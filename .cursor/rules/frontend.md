---
description: Regras lean de frontend. Consulte docs/patterns/frontend-patterns.md para exemplos detalhados e padroes aprofundados.
globs: "**/*.{tsx,jsx,ts,js}" | "**/components/**" | "**/pages/**" | "**/app/**" | "**/src/**"
alwaysApply: false
---

# Frontend - Regras Lean

> Rule enxuta. Para exemplos detalhados, padroes e snippets, consulte `docs/patterns/frontend-patterns.md`.

## Stack

- **Framework**: [ex.: Next.js 15, React 19]
- **UI**: [ex.: shadcn/ui, Radix UI]
- **Estado**: [ex.: Zustand, React Query]
- **Estilos**: [ex.: Tailwind CSS]

## Decisoes e Constraints

- Componentes SEMPRE funcionais com hooks
- Props SEMPRE tipadas com TypeScript
- Composicao sobre heranca
- Maximo [N] linhas por componente
- [Adicione suas decisoes especificas]

## Nomenclatura

- Componentes: `PascalCase.tsx`
- Hooks: `useCamelCase.ts`
- Utils: `kebab-case.ts`
- Tipos/Interfaces: `PascalCase` (sem prefixo `I`)

## Anti-Padroes

- NAO use `any` - sempre tipar explicitamente
- NAO faca fetch direto em componentes - use hooks/services
- NAO use CSS inline - use Tailwind ou CSS Modules
- [Adicione anti-padroes especificos do projeto]

## Consulta Sob Demanda

Quando precisar de detalhes, consulte os arquivos abaixo:

| Preciso de...                         | Consultar                                  |
|---------------------------------------|--------------------------------------------|
| Exemplos de componentes e composicao  | `docs/patterns/frontend-patterns.md#componentes` |
| Padroes de estado e data fetching     | `docs/patterns/frontend-patterns.md#estado` |
| Estrutura de pastas e organizacao     | `docs/patterns/frontend-patterns.md#estrutura` |
| Padroes de estilizacao e temas        | `docs/patterns/frontend-patterns.md#estilizacao` |
| Padroes de formularios e validacao    | `docs/patterns/frontend-patterns.md#formularios` |
| Padroes de roteamento                 | `docs/patterns/frontend-patterns.md#roteamento` |
| Padroes de testes                     | `docs/patterns/frontend-patterns.md#testes` |
| Exemplos canonicos do projeto         | `src/components/` e `src/pages/`           |
