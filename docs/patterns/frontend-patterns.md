# Frontend Patterns - Referencia Detalhada

> Este documento e consultado sob demanda pela IA quando precisa de exemplos detalhados, snippets e padroes aprofundados de frontend. A rule lean em `.cursor/rules/frontend.md` aponta para ca.

---

## Estrutura

<!-- Descreva a estrutura ESPECIFICA do seu projeto -->

```
frontend/
├── src/
│   ├── app/                # Rotas e layouts (App Router / Pages)
│   ├── components/
│   │   ├── ui/             # Componentes base (botoes, inputs, modals)
│   │   ├── layout/         # Header, Footer, Sidebar
│   │   └── features/       # Componentes de dominio (UserCard, OrderList)
│   ├── hooks/              # Hooks customizados
│   ├── lib/                # Utilitarios e helpers
│   ├── services/           # Camada de comunicacao com API
│   ├── stores/             # Estado global (Zustand, Context)
│   ├── types/              # Tipos e interfaces compartilhados
│   └── styles/             # Estilos globais e temas
├── public/                 # Assets estaticos
└── tests/                  # Testes
```

**Regras de organizacao:**
- Componentes reutilizaveis vao em `components/ui/`
- Componentes de dominio/feature vao em `components/features/`
- Cada feature complexa pode ter sua propria pasta com `index.ts`, `types.ts`, `hooks.ts`

---

## Componentes

### Padrao de Componente

```typescript
// Ordem interna de um componente:
// 1. Imports
// 2. Types/Interfaces (Props)
// 3. Componente
// 4. Sub-componentes (se necessario)

import { useState } from 'react'
import { Button } from '@/components/ui/button'

interface UserCardProps {
  name: string
  email: string
  onEdit?: () => void
}

export function UserCard({ name, email, onEdit }: UserCardProps) {
  const [isHovered, setIsHovered] = useState(false)

  return (
    <div
      className="rounded-lg border p-4"
      onMouseEnter={() => setIsHovered(true)}
      onMouseLeave={() => setIsHovered(false)}
    >
      <h3 className="font-semibold">{name}</h3>
      <p className="text-muted-foreground">{email}</p>
      {onEdit && <Button onClick={onEdit}>Editar</Button>}
    </div>
  )
}
```

### Padrao de Composicao

```typescript
// Prefira composicao sobre props condicionais complexas

// BOM - Composicao
<Card>
  <Card.Header>
    <Card.Title>Titulo</Card.Title>
  </Card.Header>
  <Card.Content>Conteudo</Card.Content>
  <Card.Footer>
    <Button>Acao</Button>
  </Card.Footer>
</Card>

// EVITAR - Props demais
<Card
  title="Titulo"
  content="Conteudo"
  footerAction="Acao"
  showHeader={true}
  showFooter={true}
/>
```

---

## Estado

### Estado Local vs Global

```typescript
// ESTADO LOCAL - Use para dados que pertencem a um unico componente
function SearchInput() {
  const [query, setQuery] = useState('')
  // ...
}

// ESTADO GLOBAL (Zustand) - Use para dados compartilhados entre componentes
// stores/use-auth-store.ts
import { create } from 'zustand'

interface AuthState {
  user: User | null
  isAuthenticated: boolean
  login: (credentials: Credentials) => Promise<void>
  logout: () => void
}

export const useAuthStore = create<AuthState>((set) => ({
  user: null,
  isAuthenticated: false,
  login: async (credentials) => {
    const user = await authService.login(credentials)
    set({ user, isAuthenticated: true })
  },
  logout: () => set({ user: null, isAuthenticated: false }),
}))
```

### Data Fetching

```typescript
// Padrao com React Query / TanStack Query
import { useQuery, useMutation, useQueryClient } from '@tanstack/react-query'

// Hook de leitura
export function useUsers() {
  return useQuery({
    queryKey: ['users'],
    queryFn: () => userService.getAll(),
    staleTime: 5 * 60 * 1000, // 5 minutos
  })
}

// Hook de mutacao
export function useCreateUser() {
  const queryClient = useQueryClient()

  return useMutation({
    mutationFn: (data: CreateUserDto) => userService.create(data),
    onSuccess: () => {
      queryClient.invalidateQueries({ queryKey: ['users'] })
    },
  })
}

// Uso no componente
function UserList() {
  const { data: users, isLoading, error } = useUsers()
  const createUser = useCreateUser()

  if (isLoading) return <Skeleton />
  if (error) return <ErrorMessage error={error} />

  return (
    <div>
      {users?.map((user) => (
        <UserCard key={user.id} {...user} />
      ))}
    </div>
  )
}
```

---

## Estilizacao

### Tailwind - Padroes

```typescript
// Use cn() para merge condicional de classes
import { cn } from '@/lib/utils'

interface ButtonProps {
  variant?: 'primary' | 'secondary' | 'danger'
  size?: 'sm' | 'md' | 'lg'
  className?: string
}

export function Button({ variant = 'primary', size = 'md', className }: ButtonProps) {
  return (
    <button
      className={cn(
        // Base
        'inline-flex items-center justify-center rounded-md font-medium transition-colors',
        // Variantes
        variant === 'primary' && 'bg-primary text-primary-foreground hover:bg-primary/90',
        variant === 'secondary' && 'bg-secondary text-secondary-foreground hover:bg-secondary/80',
        variant === 'danger' && 'bg-destructive text-destructive-foreground hover:bg-destructive/90',
        // Tamanhos
        size === 'sm' && 'h-8 px-3 text-sm',
        size === 'md' && 'h-10 px-4',
        size === 'lg' && 'h-12 px-6 text-lg',
        // Classes externas
        className,
      )}
    />
  )
}
```

### Responsividade

```typescript
// Breakpoints padrao Tailwind: sm(640) md(768) lg(1024) xl(1280) 2xl(1536)
// Mobile-first: estilos base sao mobile, adicione prefixos para telas maiores

<div className="
  grid grid-cols-1        // Mobile: 1 coluna
  sm:grid-cols-2          // Tablet: 2 colunas
  lg:grid-cols-3          // Desktop: 3 colunas
  xl:grid-cols-4          // Wide: 4 colunas
  gap-4
">
```

---

## Formularios

### Padrao com React Hook Form + Zod

```typescript
import { useForm } from 'react-hook-form'
import { zodResolver } from '@hookform/resolvers/zod'
import { z } from 'zod'

// 1. Schema de validacao
const createUserSchema = z.object({
  name: z.string().min(2, 'Nome deve ter pelo menos 2 caracteres'),
  email: z.string().email('Email invalido'),
  role: z.enum(['admin', 'user', 'viewer']),
})

type CreateUserForm = z.infer<typeof createUserSchema>

// 2. Componente de formulario
export function CreateUserForm({ onSubmit }: { onSubmit: (data: CreateUserForm) => void }) {
  const form = useForm<CreateUserForm>({
    resolver: zodResolver(createUserSchema),
    defaultValues: {
      name: '',
      email: '',
      role: 'user',
    },
  })

  return (
    <form onSubmit={form.handleSubmit(onSubmit)} className="space-y-4">
      <div>
        <label htmlFor="name">Nome</label>
        <input {...form.register('name')} />
        {form.formState.errors.name && (
          <p className="text-destructive text-sm">{form.formState.errors.name.message}</p>
        )}
      </div>
      {/* ... demais campos ... */}
      <button type="submit" disabled={form.formState.isSubmitting}>
        Criar
      </button>
    </form>
  )
}
```

---

## Roteamento

### Padrao de Rotas Protegidas

```typescript
// middleware.ts (Next.js) ou wrapper de rota
import { useAuthStore } from '@/stores/use-auth-store'
import { redirect } from 'next/navigation'

// Padrao de rota protegida
export function ProtectedRoute({ children }: { children: React.ReactNode }) {
  const isAuthenticated = useAuthStore((s) => s.isAuthenticated)

  if (!isAuthenticated) {
    redirect('/login')
  }

  return <>{children}</>
}

// Padrao de layout com auth
export default function DashboardLayout({ children }: { children: React.ReactNode }) {
  return (
    <ProtectedRoute>
      <Sidebar />
      <main className="flex-1 p-6">{children}</main>
    </ProtectedRoute>
  )
}
```

---

## Testes

### Padrao de Teste de Componente

```typescript
import { render, screen, fireEvent } from '@testing-library/react'
import { UserCard } from './UserCard'

describe('UserCard', () => {
  const defaultProps = {
    name: 'Joao Silva',
    email: 'joao@email.com',
  }

  it('renderiza nome e email', () => {
    render(<UserCard {...defaultProps} />)

    expect(screen.getByText('Joao Silva')).toBeInTheDocument()
    expect(screen.getByText('joao@email.com')).toBeInTheDocument()
  })

  it('mostra botao editar quando onEdit e fornecido', () => {
    const onEdit = vi.fn()
    render(<UserCard {...defaultProps} onEdit={onEdit} />)

    fireEvent.click(screen.getByText('Editar'))
    expect(onEdit).toHaveBeenCalledOnce()
  })

  it('nao mostra botao editar quando onEdit nao e fornecido', () => {
    render(<UserCard {...defaultProps} />)

    expect(screen.queryByText('Editar')).not.toBeInTheDocument()
  })
})
```

### Padrao de Teste de Hook

```typescript
import { renderHook, waitFor } from '@testing-library/react'
import { QueryClientProvider, QueryClient } from '@tanstack/react-query'
import { useUsers } from './useUsers'

const wrapper = ({ children }) => {
  const queryClient = new QueryClient({
    defaultOptions: { queries: { retry: false } },
  })
  return <QueryClientProvider client={queryClient}>{children}</QueryClientProvider>
}

describe('useUsers', () => {
  it('retorna lista de usuarios', async () => {
    const { result } = renderHook(() => useUsers(), { wrapper })

    await waitFor(() => expect(result.current.isSuccess).toBe(true))

    expect(result.current.data).toHaveLength(3)
  })
})
```

---

## Checklist Rapido

- [ ] Componente funcional com TypeScript
- [ ] Props tipadas (sem `any`)
- [ ] Estados com nomes descritivos
- [ ] Loading e error states tratados
- [ ] Responsivo (mobile-first)
- [ ] Acessivel (labels, aria, semantica)
- [ ] Testes para logica e interacoes criticas
