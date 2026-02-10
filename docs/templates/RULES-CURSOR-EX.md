# Exemplo de Rules para Cursor IDE

Este documento apresenta o padrao **Lean Rules + On-Demand Docs** para rules do Cursor IDE.

---

## Filosofia: Lean Rules

As rules do Cursor entram no contexto do modelo em **toda** interacao. Isso significa que:

- Rules grandes = mais tokens consumidos em CADA mensagem
- A IA ja conhece padroes comuns (React, TypeScript, REST, etc.)
- O que ela NAO conhece sao as **decisoes especificas do SEU projeto**

### Principio

```
Rule (lean)  →  O QUE fazer + ONDE buscar detalhes
Pattern Doc  →  COMO fazer com exemplos detalhados (consultado sob demanda)
```

### Beneficios

| Aspecto | Rule Tradicional | Lean Rule |
|---------|-----------------|-----------|
| Tamanho | 100-200 linhas | 30-50 linhas |
| Tokens por msg | Alto | Baixo |
| Detalhes | Inline (sempre carregado) | Sob demanda (so quando precisa) |
| Manutencao | Atualizar rule + exemplos juntos | Exemplos separados, mais facil |

---

## Estrutura do Arquivo de Rule

### Frontmatter

```yaml
---
description: Descricao curta da regra (usada para matching)
globs: 
alwaysApply: true/false
---
```

| Campo | Descricao |
|-------|-----------|
| `description` | Texto curto que descreve quando a regra se aplica. **IMPORTANTE**: inclua referencia ao doc detalhado aqui |
| `globs` | Padroes de arquivo para aplicacao automatica (ex: `**/*.ts`) |
| `alwaysApply` | Se `true`, aplica sempre; se `false`, aplica conforme globs/contexto |

---

## Anatomia de uma Lean Rule

Uma lean rule tem 5 secoes:

```markdown
---
description: Regras lean de [area]. Consulte docs/patterns/[area]-patterns.md para detalhes.
globs: [padroes]
alwaysApply: false
---

# [Area] - Regras Lean

> Rule enxuta. Para exemplos detalhados, consulte `docs/patterns/[area]-patterns.md`.

## Stack
[Declaracao da stack em 3-5 bullet points]

## Decisoes e Constraints
[Regras imperativas: SEMPRE faca X, NUNCA faca Y]

## Nomenclatura
[Convencoes de nomes especificas do projeto]

## Anti-Padroes
[O que NAO fazer, com razao]

## Consulta Sob Demanda
[Tabela: "Preciso de..." → "Consultar..."]
```

### Secao Chave: Consulta Sob Demanda

Esta e a secao que torna o padrao funcional. Ela cria um **mapa de navegacao** para a IA:

```markdown
## Consulta Sob Demanda

Quando precisar de detalhes, consulte os arquivos abaixo:

| Preciso de...                         | Consultar                                  |
|---------------------------------------|--------------------------------------------|
| Exemplos de componentes e composicao  | `docs/patterns/frontend-patterns.md#componentes` |
| Padroes de estado e data fetching     | `docs/patterns/frontend-patterns.md#estado` |
| Padroes de testes                     | `docs/patterns/frontend-patterns.md#testes` |
| Exemplos canonicos do projeto         | `src/components/` e `src/pages/`           |
```

A IA le esta tabela e sabe exatamente qual arquivo abrir quando precisar de mais contexto.

---

## Exemplo Completo: Lean Rule de Frontend

```markdown
---
description: Regras lean de frontend. Consulte docs/patterns/frontend-patterns.md para exemplos detalhados.
globs: "**/*.{tsx,jsx,ts,js}" | "**/components/**" | "**/pages/**"
alwaysApply: false
---

# Frontend - Regras Lean

> Rule enxuta. Para exemplos detalhados, consulte `docs/patterns/frontend-patterns.md`.

## Stack

- **Framework**: Next.js 15 (App Router)
- **UI**: shadcn/ui + Radix
- **Estado**: Zustand + React Query
- **Estilos**: Tailwind CSS

## Decisoes e Constraints

- Componentes SEMPRE funcionais com hooks
- Props SEMPRE tipadas com TypeScript
- Maximo 150 linhas por componente
- Use `cn()` para merge de classes Tailwind

## Nomenclatura

- Componentes: `PascalCase.tsx`
- Hooks: `useCamelCase.ts`
- Utils: `kebab-case.ts`

## Anti-Padroes

- NAO use `any`
- NAO faca fetch direto em componentes
- NAO use CSS inline

## Consulta Sob Demanda

| Preciso de...                         | Consultar                                  |
|---------------------------------------|--------------------------------------------|
| Exemplos de componentes e composicao  | `docs/patterns/frontend-patterns.md#componentes` |
| Padroes de estado e data fetching     | `docs/patterns/frontend-patterns.md#estado` |
| Padroes de estilizacao e temas        | `docs/patterns/frontend-patterns.md#estilizacao` |
| Padroes de formularios e validacao    | `docs/patterns/frontend-patterns.md#formularios` |
| Padroes de testes                     | `docs/patterns/frontend-patterns.md#testes` |
```

---

## Exemplo Completo: Pattern Doc

O pattern doc (`docs/patterns/[area]-patterns.md`) e onde ficam os detalhes:

```markdown
# Frontend Patterns - Referencia Detalhada

> Consultado sob demanda pela IA quando precisa de exemplos detalhados.

## Componentes

### Padrao de Componente
[Exemplo completo com codigo]

### Padrao de Composicao
[Exemplo completo com codigo]

## Estado

### Estado Local vs Global
[Quando usar cada um, com exemplos]

### Data Fetching
[Padrao com React Query, exemplos]

## Estilizacao
[Padroes de Tailwind, responsividade, temas]

## Formularios
[React Hook Form + Zod, exemplos]

## Testes
[Padroes de teste de componente e hook]
```

---

## Estrutura de Arquivos Recomendada

```
project/
├── .cursor/rules/
│   ├── rules.md              # Regras globais (lean, alwaysApply: true)
│   ├── frontend.md           # Lean rule de frontend (~40 linhas)
│   └── backend.md            # Lean rule de backend (~40 linhas)
├── docs/
│   └── patterns/
│       ├── frontend-patterns.md  # Referencia detalhada (~200-300 linhas)
│       └── backend-patterns.md   # Referencia detalhada (~200-300 linhas)
```

**Fluxo da IA:**
1. Abre arquivo `.tsx` → Cursor carrega `frontend.md` (lean, ~40 linhas)
2. Precisa criar componente → Le a tabela "Consulta Sob Demanda"
3. Abre `docs/patterns/frontend-patterns.md#componentes` sob demanda
4. Implementa seguindo o padrao detalhado

---

## Checklist de Criacao de Lean Rules

- [ ] Frontmatter com `description` que menciona o doc detalhado
- [ ] `globs` configurado se nao for `alwaysApply`
- [ ] Rule com no maximo 50 linhas
- [ ] Stack declarada em bullet points
- [ ] Decisoes como imperativos (SEMPRE/NUNCA)
- [ ] Tabela de "Consulta Sob Demanda" preenchida
- [ ] Pattern Doc correspondente criado em `docs/patterns/`
- [ ] Pattern Doc com exemplos de codigo completos e funcionais

---

## Referencia

- [Documentacao do Cursor](https://docs.cursor.com)
- [Regras Globais](../../.cursor/rules/rules.md)
- [Regras de Backend](../../.cursor/rules/backend.md)
- [Regras de Frontend](../../.cursor/rules/frontend.md)
- [Frontend Patterns](../patterns/frontend-patterns.md)
- [Backend Patterns](../patterns/backend-patterns.md)