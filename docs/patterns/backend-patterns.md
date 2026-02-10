# Backend Patterns - Referencia Detalhada

> Este documento e consultado sob demanda pela IA quando precisa de exemplos detalhados, snippets e padroes aprofundados de backend. A rule lean em `.cursor/rules/backend.md` aponta para ca.

---

## Estrutura

<!-- Descreva a estrutura ESPECIFICA do seu projeto -->

```
backend/
├── src/
│   ├── controllers/        # Entrada HTTP - recebe request, retorna response
│   ├── use-cases/          # Logica de negocio pura
│   ├── services/           # Orquestracao e integracao
│   ├── repositories/       # Acesso a dados (abstrai o banco)
│   ├── entities/           # Modelos de dominio
│   ├── dtos/               # Data Transfer Objects (input/output)
│   ├── middleware/          # Auth, error handling, logging
│   ├── config/             # Configuracoes e environment
│   ├── shared/             # Utilitarios compartilhados
│   └── errors/             # Classes de erro customizadas
├── prisma/                 # Schema e migrations (se usar Prisma)
└── tests/
    ├── unit/               # Testes unitarios
    ├── integration/        # Testes de integracao
    └── e2e/                # Testes end-to-end
```

**Fluxo de uma requisicao:**
```
Request → Controller → UseCase/Service → Repository → Database
                ↓              ↓              ↓
              DTO           Entity         Query
```

---

## Services

### Padrao de Service

```typescript
// services/user.service.ts
import { UserRepository } from '@/repositories/user.repository'
import { CreateUserDto, UpdateUserDto, UserResponseDto } from '@/dtos/user.dto'
import { NotFoundError, ConflictError } from '@/errors'

export class UserService {
  constructor(private readonly userRepo: UserRepository) {}

  async create(dto: CreateUserDto): Promise<UserResponseDto> {
    const existing = await this.userRepo.findByEmail(dto.email)
    if (existing) {
      throw new ConflictError('Email ja cadastrado')
    }

    const user = await this.userRepo.create({
      name: dto.name,
      email: dto.email,
      passwordHash: await hashPassword(dto.password),
    })

    return UserResponseDto.fromEntity(user)
  }

  async findById(id: string): Promise<UserResponseDto> {
    const user = await this.userRepo.findById(id)
    if (!user) {
      throw new NotFoundError('Usuario nao encontrado')
    }
    return UserResponseDto.fromEntity(user)
  }

  async update(id: string, dto: UpdateUserDto): Promise<UserResponseDto> {
    await this.findById(id) // Garante que existe
    const updated = await this.userRepo.update(id, dto)
    return UserResponseDto.fromEntity(updated)
  }

  async delete(id: string): Promise<void> {
    await this.findById(id) // Garante que existe
    await this.userRepo.delete(id)
  }
}
```

### Padrao de Use Case (alternativa a Service)

```typescript
// use-cases/create-user.use-case.ts
import { UserRepository } from '@/repositories/user.repository'
import { CreateUserDto, UserResponseDto } from '@/dtos/user.dto'

// Um use case = uma acao de negocio
export class CreateUserUseCase {
  constructor(
    private readonly userRepo: UserRepository,
    private readonly emailService: EmailService,
  ) {}

  async execute(dto: CreateUserDto): Promise<UserResponseDto> {
    // 1. Validacao de negocio
    const existing = await this.userRepo.findByEmail(dto.email)
    if (existing) throw new ConflictError('Email ja cadastrado')

    // 2. Execucao
    const user = await this.userRepo.create(dto)

    // 3. Side effects
    await this.emailService.sendWelcome(user.email)

    // 4. Retorno
    return UserResponseDto.fromEntity(user)
  }
}
```

---

## Repositorios

### Padrao de Repository

```typescript
// repositories/user.repository.ts
import { PrismaClient, User } from '@prisma/client'

export class UserRepository {
  constructor(private readonly prisma: PrismaClient) {}

  async findById(id: string): Promise<User | null> {
    return this.prisma.user.findUnique({ where: { id } })
  }

  async findByEmail(email: string): Promise<User | null> {
    return this.prisma.user.findUnique({ where: { email } })
  }

  async findAll(params?: {
    skip?: number
    take?: number
    orderBy?: Record<string, 'asc' | 'desc'>
  }): Promise<User[]> {
    return this.prisma.user.findMany({
      skip: params?.skip,
      take: params?.take ?? 20,
      orderBy: params?.orderBy ?? { createdAt: 'desc' },
    })
  }

  async create(data: Omit<User, 'id' | 'createdAt' | 'updatedAt'>): Promise<User> {
    return this.prisma.user.create({ data })
  }

  async update(id: string, data: Partial<User>): Promise<User> {
    return this.prisma.user.update({ where: { id }, data })
  }

  async delete(id: string): Promise<void> {
    await this.prisma.user.delete({ where: { id } })
  }
}
```

### Padrao de Transaction

```typescript
// Quando precisar de transacoes entre multiplos repositorios
async transferFunds(fromId: string, toId: string, amount: number): Promise<void> {
  await this.prisma.$transaction(async (tx) => {
    const from = await tx.account.findUniqueOrThrow({ where: { id: fromId } })

    if (from.balance < amount) {
      throw new BusinessError('Saldo insuficiente')
    }

    await tx.account.update({
      where: { id: fromId },
      data: { balance: { decrement: amount } },
    })

    await tx.account.update({
      where: { id: toId },
      data: { balance: { increment: amount } },
    })
  })
}
```

---

## Respostas

### Formato Padrao de Resposta

```typescript
// Sucesso
interface ApiSuccessResponse<T> {
  success: true
  data: T
  meta?: {
    page?: number
    perPage?: number
    total?: number
  }
}

// Erro
interface ApiErrorResponse {
  success: false
  error: {
    code: string           // Ex: 'NOT_FOUND', 'VALIDATION_ERROR'
    message: string        // Mensagem legivel
    details?: unknown[]    // Detalhes de validacao
  }
}

// Exemplos de resposta:

// 200 OK
{
  "success": true,
  "data": { "id": "1", "name": "Joao", "email": "joao@email.com" }
}

// 200 OK (lista paginada)
{
  "success": true,
  "data": [...],
  "meta": { "page": 1, "perPage": 20, "total": 150 }
}

// 400 Bad Request
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Dados de entrada invalidos",
    "details": [
      { "field": "email", "message": "Email invalido" }
    ]
  }
}

// 404 Not Found
{
  "success": false,
  "error": {
    "code": "NOT_FOUND",
    "message": "Usuario nao encontrado"
  }
}
```

### Padrao de Error Handling

```typescript
// errors/base-error.ts
export abstract class AppError extends Error {
  abstract readonly statusCode: number
  abstract readonly code: string

  constructor(message: string) {
    super(message)
    this.name = this.constructor.name
  }
}

// errors/not-found.error.ts
export class NotFoundError extends AppError {
  readonly statusCode = 404
  readonly code = 'NOT_FOUND'
}

// errors/conflict.error.ts
export class ConflictError extends AppError {
  readonly statusCode = 409
  readonly code = 'CONFLICT'
}

// errors/validation.error.ts
export class ValidationError extends AppError {
  readonly statusCode = 400
  readonly code = 'VALIDATION_ERROR'

  constructor(
    message: string,
    readonly details: Array<{ field: string; message: string }>,
  ) {
    super(message)
  }
}

// middleware/error-handler.ts
export function errorHandler(err: Error, req: Request, res: Response, next: NextFunction) {
  if (err instanceof AppError) {
    return res.status(err.statusCode).json({
      success: false,
      error: {
        code: err.code,
        message: err.message,
        ...(err instanceof ValidationError && { details: err.details }),
      },
    })
  }

  // Erro inesperado - NAO expor detalhes em producao
  console.error('Unexpected error:', err)
  return res.status(500).json({
    success: false,
    error: {
      code: 'INTERNAL_ERROR',
      message: 'Erro interno do servidor',
    },
  })
}
```

---

## Validacao

### Padrao com Zod

```typescript
// dtos/user.dto.ts
import { z } from 'zod'

// Schema de criacao
export const createUserSchema = z.object({
  name: z.string().min(2).max(100),
  email: z.string().email(),
  password: z.string().min(8).max(128),
  role: z.enum(['admin', 'user', 'viewer']).default('user'),
})

export type CreateUserDto = z.infer<typeof createUserSchema>

// Schema de atualizacao (todos os campos opcionais)
export const updateUserSchema = createUserSchema.partial().omit({ password: true })

export type UpdateUserDto = z.infer<typeof updateUserSchema>

// Schema de query params
export const listUsersQuerySchema = z.object({
  page: z.coerce.number().int().min(1).default(1),
  perPage: z.coerce.number().int().min(1).max(100).default(20),
  search: z.string().optional(),
  role: z.enum(['admin', 'user', 'viewer']).optional(),
})

// DTO de resposta (o que a API retorna)
export class UserResponseDto {
  constructor(
    public id: string,
    public name: string,
    public email: string,
    public role: string,
    public createdAt: Date,
  ) {}

  static fromEntity(entity: User): UserResponseDto {
    return new UserResponseDto(
      entity.id,
      entity.name,
      entity.email,
      entity.role,
      entity.createdAt,
    )
  }
}
```

### Middleware de Validacao

```typescript
// middleware/validate.ts
import { ZodSchema } from 'zod'
import { ValidationError } from '@/errors'

export function validate(schema: ZodSchema, source: 'body' | 'query' | 'params' = 'body') {
  return (req: Request, _res: Response, next: NextFunction) => {
    const result = schema.safeParse(req[source])

    if (!result.success) {
      const details = result.error.issues.map((issue) => ({
        field: issue.path.join('.'),
        message: issue.message,
      }))
      throw new ValidationError('Dados de entrada invalidos', details)
    }

    req[source] = result.data
    next()
  }
}

// Uso no router
router.post('/users', validate(createUserSchema), userController.create)
router.get('/users', validate(listUsersQuerySchema, 'query'), userController.list)
```

---

## Auth

### Padrao JWT

```typescript
// middleware/auth.ts
import jwt from 'jsonwebtoken'
import { UnauthorizedError, ForbiddenError } from '@/errors'

export function authenticate(req: Request, _res: Response, next: NextFunction) {
  const token = req.headers.authorization?.replace('Bearer ', '')

  if (!token) {
    throw new UnauthorizedError('Token nao fornecido')
  }

  try {
    const payload = jwt.verify(token, process.env.JWT_SECRET!) as TokenPayload
    req.user = payload
    next()
  } catch {
    throw new UnauthorizedError('Token invalido ou expirado')
  }
}

export function authorize(...roles: string[]) {
  return (req: Request, _res: Response, next: NextFunction) => {
    if (!roles.includes(req.user.role)) {
      throw new ForbiddenError('Sem permissao para esta acao')
    }
    next()
  }
}

// Uso no router
router.get('/admin/users', authenticate, authorize('admin'), userController.list)
router.get('/profile', authenticate, userController.getProfile)
```

---

## Testes

### Padrao de Teste Unitario (Service)

```typescript
import { describe, it, expect, vi, beforeEach } from 'vitest'
import { UserService } from './user.service'
import { UserRepository } from '@/repositories/user.repository'
import { NotFoundError, ConflictError } from '@/errors'

describe('UserService', () => {
  let service: UserService
  let mockRepo: jest.Mocked<UserRepository>

  beforeEach(() => {
    mockRepo = {
      findById: vi.fn(),
      findByEmail: vi.fn(),
      create: vi.fn(),
      update: vi.fn(),
      delete: vi.fn(),
    } as any

    service = new UserService(mockRepo)
  })

  describe('create', () => {
    it('cria usuario quando email nao existe', async () => {
      mockRepo.findByEmail.mockResolvedValue(null)
      mockRepo.create.mockResolvedValue({ id: '1', name: 'Joao', email: 'joao@email.com' })

      const result = await service.create({
        name: 'Joao',
        email: 'joao@email.com',
        password: '12345678',
      })

      expect(result.name).toBe('Joao')
      expect(mockRepo.create).toHaveBeenCalledOnce()
    })

    it('lanca ConflictError quando email ja existe', async () => {
      mockRepo.findByEmail.mockResolvedValue({ id: '1', email: 'joao@email.com' })

      await expect(
        service.create({ name: 'Joao', email: 'joao@email.com', password: '12345678' }),
      ).rejects.toThrow(ConflictError)
    })
  })

  describe('findById', () => {
    it('retorna usuario quando encontrado', async () => {
      mockRepo.findById.mockResolvedValue({ id: '1', name: 'Joao' })

      const result = await service.findById('1')

      expect(result.name).toBe('Joao')
    })

    it('lanca NotFoundError quando nao encontrado', async () => {
      mockRepo.findById.mockResolvedValue(null)

      await expect(service.findById('999')).rejects.toThrow(NotFoundError)
    })
  })
})
```

### Padrao de Teste de Integracao (API)

```typescript
import { describe, it, expect, beforeAll, afterAll } from 'vitest'
import request from 'supertest'
import { app } from '@/app'
import { prisma } from '@/lib/prisma'

describe('POST /api/v1/users', () => {
  beforeAll(async () => {
    await prisma.user.deleteMany()
  })

  afterAll(async () => {
    await prisma.$disconnect()
  })

  it('201 - cria usuario com dados validos', async () => {
    const res = await request(app)
      .post('/api/v1/users')
      .send({ name: 'Joao', email: 'joao@email.com', password: '12345678' })

    expect(res.status).toBe(201)
    expect(res.body.success).toBe(true)
    expect(res.body.data.email).toBe('joao@email.com')
  })

  it('400 - rejeita email invalido', async () => {
    const res = await request(app)
      .post('/api/v1/users')
      .send({ name: 'Joao', email: 'invalido', password: '12345678' })

    expect(res.status).toBe(400)
    expect(res.body.success).toBe(false)
    expect(res.body.error.code).toBe('VALIDATION_ERROR')
  })

  it('409 - rejeita email duplicado', async () => {
    // Primeiro cria
    await request(app)
      .post('/api/v1/users')
      .send({ name: 'Maria', email: 'maria@email.com', password: '12345678' })

    // Tenta duplicar
    const res = await request(app)
      .post('/api/v1/users')
      .send({ name: 'Maria 2', email: 'maria@email.com', password: '12345678' })

    expect(res.status).toBe(409)
  })
})
```

---

## Checklist Rapido

- [ ] Input validado com Zod/schema
- [ ] Erros tratados com classes customizadas
- [ ] Resposta no formato padrao (success/error)
- [ ] Autenticacao/autorizacao aplicada
- [ ] Logs com contexto em operacoes criticas
- [ ] Testes unitarios para services/use-cases
- [ ] Testes de integracao para endpoints
- [ ] Sem secrets hardcoded
