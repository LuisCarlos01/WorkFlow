---
description: Padrões específicos de backend do projeto. Foca em convenções de API, banco de dados e arquitetura específicas deste projeto.
globs: "**/*.{ts,js,py,go,rs,java,php,rb}" | "**/api/**" | "**/server/**" | "**/backend/**"
alwaysApply: false
---

# Regras de Desenvolvimento Backend

> **📝 Instruções**: Edite este arquivo com padrões ESPECÍFICOS do seu projeto. Remova exemplos genéricos e adicione apenas o que é único ao seu projeto.

## Stack e Arquitetura

<!-- Especifique sua stack específica -->
**Stack**: [ex.: NestJS, Express, FastAPI]
**Banco de Dados**: [ex.: PostgreSQL com Prisma]
**Arquitetura**: [ex.: Clean Architecture, Hexagonal]

> **Referência**: Para padrões gerais de TypeScript/Python, a IA já conhece. Foque apenas no que é específico do seu projeto.

## Padrões Específicos do Projeto

### Estrutura de Pastas

<!-- Descreva a estrutura ESPECÍFICA do seu projeto -->
```
backend/
├── src/
│   ├── [sua estrutura específica]
```

**Regras específicas:**
- [Adicione regras específicas da sua organização]

### Convenções de Nomenclatura

<!-- Apenas convenções que fogem do padrão -->
- **Services**: [ex.: Sufixo "Service" ou outro padrão específico]
- **Controllers**: [ex.: Sufixo "Controller" ou outro padrão específico]
- **DTOs**: [ex.: Sufixo "Dto" ou outro padrão específico]

### Design de API

<!-- Padrões específicos da sua API -->
- **Versionamento**: [ex.: `/api/v1/...` ou outro padrão]
- **Formato de Resposta**: 
  ```typescript
  // Exemplo do formato ESPECÍFICO usado no projeto
  interface ApiResponse<T> {
    // Seu formato específico
  }
  ```

**Referência**: Veja exemplos em `src/controllers/` ou `docs/api.md`

### Banco de Dados

<!-- Convenções específicas do seu projeto -->
- **ORM**: [ex.: Prisma, TypeORM]
- **Migrations**: [ex.: Como são organizadas]
- **Padrões de Query**: [ex.: Eager loading, transactions]

**Referência**: Veja exemplos em `src/repositories/` ou `docs/database.md`

### Tratamento de Erros

<!-- Padrão específico de erros do projeto -->
```typescript
// Exemplo do padrão ESPECÍFICO usado
class CustomError extends Error {
  // Seu padrão específico
}
```

**Referência**: Veja exemplos em `src/errors/` ou `src/middleware/error-handler.ts`

### Validação

<!-- Biblioteca e padrão específico -->
- **Biblioteca**: [ex.: Zod, Yup, class-validator]
- **Onde validar**: [ex.: Controller, Service, Middleware]

**Referência**: Veja exemplos em `src/dto/` ou `src/validators/`

## Padrões Arquiteturais Específicos

<!-- Apenas padrões que são específicos do seu projeto -->
- **Service Layer**: [Como você organiza services]
- **Repository Pattern**: [Como você implementa repositories]
- **Dependency Injection**: [Como você faz DI]

**Referência**: Veja exemplos canônicos em:
- `src/services/[exemplo].ts`
- `src/repositories/[exemplo].ts`

## Anti-Padrões Específicos

<!-- Apenas anti-padrões específicos do seu projeto -->
- ❌ Não faça X porque [razão específica do projeto]
- ❌ Evite Y porque [razão específica do projeto]

## Referências

- [README Backend](../README.md)
- [Documentação da API](../docs/api.md)
- [Schema do Banco](../docs/database.md)
- [Exemplos Canônicos](../src/)

---

**Última Atualização**: [Data]
