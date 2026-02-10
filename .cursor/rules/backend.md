---
description: Regras lean de backend. Consulte docs/patterns/backend-patterns.md para exemplos detalhados e padroes aprofundados.
globs: "**/*.{ts,js,py,go,rs,java,php,rb}" | "**/api/**" | "**/server/**" | "**/backend/**"
alwaysApply: false
---

# Backend - Regras Lean

> Rule enxuta. Para exemplos detalhados, padroes e snippets, consulte `docs/patterns/backend-patterns.md`.

## Stack

- **Runtime**: [ex.: Node.js 20+, Python 3.12]
- **Framework**: [ex.: Fastify, NestJS, FastAPI]
- **Banco de Dados**: [ex.: PostgreSQL 16]
- **ORM**: [ex.: Prisma, Drizzle, SQLAlchemy]
- **Arquitetura**: [ex.: Clean Architecture, Hexagonal]

## Decisoes e Constraints

- SEMPRE validar inputs com [ex.: Zod, class-validator]
- SEMPRE usar classes de erro customizadas
- SEMPRE logar erros com contexto
- NUNCA confiar em dados externos sem sanitizacao
- NUNCA expor stack traces em producao
- [Adicione suas decisoes especificas]

## Nomenclatura

- Arquivos: `kebab-case.ts`
- Classes: `PascalCase` (ex.: `UserService`)
- Funcoes: `camelCase` (ex.: `getUserById`)
- Constantes: `UPPER_SNAKE_CASE` (ex.: `API_BASE_URL`)
- DTOs: `PascalCase` + sufixo `Dto` (ex.: `CreateUserDto`)

## Design de API

- Versionamento: [ex.: `/api/v1/...`]
- Formato padrao de resposta: ver `docs/patterns/backend-patterns.md#respostas`
- Autenticacao: [ex.: JWT, OAuth2]

## Anti-Padroes

- NAO faca queries direto no controller - use repository/service
- NAO retorne entidades do banco direto na API - use DTOs
- NAO ignore tratamento de erros em operacoes async
- [Adicione anti-padroes especificos do projeto]

## Consulta Sob Demanda

Quando precisar de detalhes, consulte os arquivos abaixo:

| Preciso de...                          | Consultar                                   |
|----------------------------------------|---------------------------------------------|
| Exemplos de services e use-cases       | `docs/patterns/backend-patterns.md#services` |
| Padroes de repositorio e queries       | `docs/patterns/backend-patterns.md#repositorios` |
| Formato de respostas e erros           | `docs/patterns/backend-patterns.md#respostas` |
| Padroes de validacao e DTOs            | `docs/patterns/backend-patterns.md#validacao` |
| Estrutura de pastas e organizacao      | `docs/patterns/backend-patterns.md#estrutura` |
| Padroes de autenticacao e autorizacao  | `docs/patterns/backend-patterns.md#auth` |
| Padroes de testes                      | `docs/patterns/backend-patterns.md#testes` |
| Exemplos canonicos do projeto          | `src/services/` e `src/controllers/`        |
