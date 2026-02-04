# Estrutura Base de Projeto para Cursor

Este documento descreve a arquitetura em camadas para configurar o **Cursor IDE** em projetos de desenvolvimento.

> **Fonte oficial**: [docs.cursor.com](https://docs.cursor.com) | **Forum**: [forum.cursor.com](https://forum.cursor.com)

---

## Resumo: O Que Cada Camada Diz

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│   ┌─────────────────┐                                                       │
│   │       MCP       │  "Aqui estao as FERRAMENTAS externas"                 │
│   │ (Model Context  │  → APIs, bancos de dados, documentacao externa        │
│   │    Protocol)    │                                                       │
│   └─────────────────┘                                                       │
│           │                                                                 │
│           ▼                                                                 │
│   ┌─────────────────┐                                                       │
│   │     Skills      │  "Aqui esta COMO fazer as coisas"                     │
│   │ (.cursor/skills)│  → Workflows especializados, conhecimento de dominio  │
│   └─────────────────┘                                                       │
│           │                                                                 │
│           ▼                                                                 │
│   ┌─────────────────┐                                                       │
│   │    Commands     │  "Aqui estao os ATALHOS acionaveis"                   │
│   │(.cursor/commands│  → Prompts reutilizaveis invocados com /              │
│   └─────────────────┘                                                       │
│           │                                                                 │
│           ▼                                                                 │
│   ┌─────────────────┐                                                       │
│   │      Rules      │  "Aqui estao as REGRAS de comportamento"              │
│   │ (.cursor/rules) │  → Padroes, convencoes, diretrizes tecnicas           │
│   └─────────────────┘                                                       │
│           │                                                                 │
│           ▼                                                                 │
│   ┌─────────────────┐                                                       │
│   │   .cursorrules  │  "Aqui esta o contexto FUNDAMENTAL"                   │
│   │  (ou rules.mdc) │  → Contexto global do projeto                         │
│   └─────────────────┘                                                       │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Analogia: Onboarding de um Desenvolvedor

| Camada | Analogia | Pergunta que Responde |
|--------|----------|----------------------|
| **Rules** | Guia de estilo e padroes | "Como devemos escrever codigo aqui?" |
| **Commands** | Scripts e atalhos | "Como executo tarefas rapidamente?" |
| **Skills** | Playbooks especializados | "Como resolvo problemas especificos?" |
| **MCP** | Credenciais e acessos | "Quais ferramentas posso usar?" |

---

## Diagrama: Piramide de Configuracao

```
                         ┌─────────────────────┐
                         │         MCP         │ ← Ferramentas externas
                         │    (Settings/MCP)   │   (Context7, Serena, etc.)
                         └──────────┬──────────┘
                                    │
                         ┌──────────▼──────────┐
                         │       Skills        │ ← Conhecimento especializado
                         │   (.cursor/skills)  │   (dominio, workflows)
                         └──────────┬──────────┘
                                    │
                         ┌──────────▼──────────┐
                         │      Commands       │ ← Prompts reutilizaveis
                         │  (.cursor/commands) │   (atalhos com /)
                         └──────────┬──────────┘
                                    │
                         ┌──────────▼──────────┐
                         │        Rules        │ ← Regras contextuais
                         │   (.cursor/rules)   │   (por tipo de arquivo)
                         └──────────┬──────────┘
                                    │
         ┌──────────────────────────▼──────────────────────┐
         │        .cursorrules ou rules.mdc (global)       │ ← Base do projeto
         │            (Configuracao Fundamental)            │   (sempre aplicado)
         └──────────────────────────────────────────────────┘
```

---

## 1. Rules (Regras de Comportamento)

### O que sao

Regras que definem como o agente Cursor deve se comportar, quais padroes seguir e como escrever codigo no projeto.

### Localizacao

| Tipo | Arquivo | Descricao |
|------|---------|-----------|
| **Global (legado)** | `.cursorrules` | Arquivo unico na raiz (ainda suportado) |
| **Global (novo)** | `.cursor/rules/rules.mdc` | Regra com `alwaysApply: true` |
| **Contextual** | `.cursor/rules/*.md` | Regras por dominio/tipo de arquivo |

### Estrutura de um Arquivo de Regra

```markdown
---
title: Nome da Regra
description: "Descricao curta com keywords. Keywords: backend, api, typescript."
glob: "**/*.ts"           # Tipos de arquivo (opcional)
alwaysApply: true         # Sempre anexar ao contexto (default: false)
---

# Titulo da Regra

## Convencoes
1. [Regra 1]
2. [Regra 2]

## O que fazer
- ✅ [Pratica recomendada]

## O que evitar
- ❌ [Anti-pattern]
```

### Tipos de Regras

| Tipo | Quando Carregar | Exemplo |
|------|-----------------|---------|
| **Global** | Sempre (`alwaysApply: true`) | Convencoes Git, MCP |
| **Contextual** | Por tipo de arquivo (`glob`) | Backend, Frontend |
| **Sob demanda** | Por busca semantica (`description`) | Seguranca, Performance |

### Exemplo: rules.mdc (Global)

```markdown
---
title: Regras Gerais do Projeto
description: Regras globais. Keywords: git, commits, estrutura.
glob: "**/*"
alwaysApply: true
---

# Regras Gerais

## MCP (Model Context Protocol)
**SEMPRE** use:
- **Context7** - para documentacao de bibliotecas
- **Serena** - para busca semantica de codigo

## Convencoes Git
- Conventional Commits em pt-br
- Sem caracteres especiais em commits
```

### Exemplo: backend.md (Contextual)

```markdown
---
title: Regras de Backend
description: Padroes para APIs e servicos. Keywords: api, backend, node, typescript.
glob: "backend/**/*"
alwaysApply: false
---

# Regras de Backend

## Arquitetura
- Usar camadas: Controller → Service → Repository
- Validar entradas com Zod

## Padroes
✅ Funcoes pequenas (max 20 linhas)
✅ Tipagem explicita sempre
❌ Nunca usar `any`
```

---

## 2. Commands (Comandos Reutilizaveis)

### O que sao

Prompts pre-configurados que podem ser invocados rapidamente com `/comando` no chat do Cursor.

### Localizacao

```
.cursor/commands/
├── few-shot.md           # Template de Few-Shot Prompting
├── create-component.md   # Criar componente padrao
├── run-tests.md          # Executar suite de testes
└── refactor.md           # Refatorar codigo selecionado
```

### Estrutura de um Command

```markdown
# /nome-do-comando

## Descricao
Executa [descricao da tarefa].

## Referencia
@caminho/para/arquivo-template.md

## Input
**Contexto/Tarefa**: `$ARGUMENTS`

## Processo
1. [Passo 1]
2. [Passo 2]
3. [Passo 3]

## Output
[Formato esperado do resultado]

## Exemplo de Uso
\`\`\`
/nome-do-comando contexto especifico aqui
\`\`\`
```

### Exemplo: few-shot.md

```markdown
# /few-shot

## Descricao
Aplica tecnica de Few-Shot Prompting usando template padrao.

## Referencia
@prompts/Techniques/Prompt-FewShot.md

## Input
**Contexto/Tarefa**: `$ARGUMENTS`

## Processo
1. Carregar template de referencia
2. Analisar requisitos do usuario
3. Criar exemplos relevantes
4. Montar prompt personalizado

## Exemplo de Uso
\`\`\`
/few-shot API REST com Node.js e TypeScript
\`\`\`
```

---

## 3. Skills (Conhecimento Especializado)

### O que sao

Arquivos que capacitam o agente com conhecimento de dominio especifico. O Cursor decide automaticamente quando aplicar baseado na descricao e keywords.

### Localizacao

```
.cursor/skills/
├── frontend-design.md     # Design de interfaces
├── testing.md             # Estrategias de teste
├── security.md            # Praticas de seguranca
└── performance.md         # Otimizacao de performance
```

### Estrutura de uma Skill

```markdown
---
name: nome-da-skill
description: Descricao detalhada com keywords para busca semantica. Keywords: keyword1, keyword2, keyword3.
---

# Nome da Skill

## Quando Usar Esta Skill
- [Situacao 1]
- [Situacao 2]

## Instrucoes

### 1. [Topico Principal]
[Detalhes e diretrizes]

### 2. [Outro Topico]
[Mais detalhes]

## Regras
✅ [O que fazer]
❌ [O que evitar]

## Exemplos (Few-Shot)

### Exemplo 1: [Cenario]
**Entrada:** [Input do usuario]
**Resposta:** [Output esperado]

\`\`\`tsx
// Codigo de exemplo
\`\`\`
```

### Exemplo: frontend-design.md

```markdown
---
name: frontend-design
description: Skill para criacao de interfaces frontend modernas. Keywords: frontend, design, landing page, dashboard, UI, UX, tailwind, react.
---

# Frontend Design Skill

## Quando Usar
- Criar landing pages
- Desenvolver componentes React
- Implementar design systems

## Instrucoes

### 1. Design System
- Paleta de cores (max 5)
- Tipografia (max 2 fontes)
- Espacamento consistente

### 2. Evitar Cliches de IA
❌ Gradientes genericos
❌ Bordas arredondadas excessivas
✅ Cores com proposito
✅ Hierarquia visual clara

## Exemplos

### Exemplo: Hero Section
**Entrada:** "Crie hero section moderna para SaaS"
**Resposta:** [Componente completo com explicacao]
```

---

## 4. MCP (Model Context Protocol)

### O que e

Protocolo que permite integrar ferramentas externas ao Cursor: APIs, bancos de dados, documentacao, e servicos de terceiros.

### Configuracao

Via **Cursor Settings > MCP** ou arquivo de configuracao:

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@anthropic/context7-mcp"]
    },
    "serena": {
      "command": "npx",
      "args": ["-y", "serena-mcp"]
    },
    "postgres": {
      "command": "npx",
      "args": ["-y", "@anthropic/postgres-mcp"],
      "env": {
        "DATABASE_URL": "${DATABASE_URL}"
      }
    }
  }
}
```

### Tipos de Integracoes MCP

```
┌─────────────────────────────────────────────────────────────┐
│                      MCP Servers                            │
├─────────────────┬───────────────────────────────────────────┤
│  Documentacao   │  Context7, DevDocs                        │
├─────────────────┼───────────────────────────────────────────┤
│  Codigo         │  Serena (semantic search), GitHub         │
├─────────────────┼───────────────────────────────────────────┤
│  Banco de Dados │  PostgreSQL MCP, MongoDB MCP              │
├─────────────────┼───────────────────────────────────────────┤
│  Cloud          │  AWS MCP, GCP MCP                         │
├─────────────────┼───────────────────────────────────────────┤
│  Outros         │  Slack, Jira, Notion, Linear              │
└─────────────────┴───────────────────────────────────────────┘
```

### Uso no Cursor

Apos configurar, use via simbolos `@`:
- `@Docs` - Documentacao publica indexada
- `@Web` - Busca na web
- `@MCP` - Ferramentas MCP configuradas

---

## 5. Contexto via Simbolos @

### O que sao

O Cursor usa simbolos `@` para referenciar contexto de forma explicita e eficiente.

### Simbolos Disponiveis

| Simbolo | Descricao | Exemplo |
|---------|-----------|---------|
| `@file` | Arquivo especifico | `@src/components/Button.tsx` |
| `@folder` | Pasta inteira | `@src/utils` |
| `@Codebase` | Busca semantica no codigo | `@Codebase como funciona auth?` |
| `@Docs` | Documentacao publica | `@Docs React hooks` |
| `@Web` | Busca na internet | `@Web latest Next.js 15 features` |
| `@Git` | Historico Git | `@Git ultimos commits` |

### Boas Praticas

```markdown
✅ Seja especifico: @src/auth/middleware.ts
✅ Use @Codebase para descoberta
✅ Combine simbolos: @Docs React + @file App.tsx

❌ Nao sobrecarregue com contexto demais
❌ Evite referencias muito amplas: @src (pasta muito grande)
```

---

## Fluxo de Resolucao de Contexto

```
┌─────────────────────────────────────────────────────────────────────┐
│                        Requisicao do Usuario                        │
└───────────────────────────────┬─────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────────┐
│  1. RULES GLOBAIS                                                   │
│     Carrega regras com alwaysApply: true                            │
│     → Entende convencoes basicas, MCP disponivel                    │
└───────────────────────────────┬─────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────────┐
│  2. RULES CONTEXTUAIS                                               │
│     Carrega regras que match com glob do arquivo atual              │
│     → Padroes de backend, frontend, etc.                            │
└───────────────────────────────┬─────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────────┐
│  3. SKILLS                                                          │
│     Busca semantica por skills relevantes (via description)         │
│     → Conhecimento especializado de dominio                         │
└───────────────────────────────┬─────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────────┐
│  4. COMMANDS                                                        │
│     Se usuario invocou /comando, carrega instrucoes                 │
│     → Workflows pre-configurados                                    │
└───────────────────────────────┬─────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────────┐
│  5. MCP & SIMBOLOS @                                                │
│     Consulta ferramentas externas e referencias explicitas          │
│     → Documentacao, codigo, web, etc.                               │
└───────────────────────────────┬─────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────────┐
│                              Resposta                               │
└─────────────────────────────────────────────────────────────────────┘
```

---

## Exemplos Completos

### Exemplo 1: Projeto Node.js API

```
projeto-api/
│
├── .cursor/
│   ├── rules/
│   │   ├── rules.mdc        # Global: Git, MCP, estrutura
│   │   ├── backend.md       # Backend: arquitetura, padroes
│   │   └── testing.md       # Testes: convencoes Jest
│   ├── commands/
│   │   ├── create-endpoint.md
│   │   └── run-tests.md
│   └── skills/
│       └── api-design.md
│
├── src/
│   ├── controllers/
│   ├── services/
│   └── repositories/
│
└── package.json
```

**rules.mdc:**
```markdown
---
title: Regras Gerais
alwaysApply: true
---

# API de Pedidos

## Stack
- Node.js 20 + TypeScript
- Express + Prisma + PostgreSQL
- Jest + Supertest

## MCP
- Context7 para docs de libs
- Serena para busca de codigo
```

---

### Exemplo 2: Projeto React Frontend

```
projeto-web/
│
├── .cursor/
│   ├── rules/
│   │   ├── rules.mdc        # Global
│   │   ├── frontend.md      # React patterns
│   │   └── styling.md       # Tailwind conventions
│   ├── commands/
│   │   ├── create-component.md
│   │   ├── create-page.md
│   │   └── create-hook.md
│   └── skills/
│       └── frontend-design.md
│
├── src/
│   ├── app/
│   ├── components/
│   └── hooks/
│
└── package.json
```

---

### Exemplo 3: Monorepo Full-Stack

```
projeto-fullstack/
│
├── .cursor/
│   ├── rules/
│   │   ├── rules.mdc          # Global
│   │   ├── backend.md         # API patterns
│   │   ├── frontend.md        # React patterns
│   │   └── monorepo.md        # Workspace conventions
│   ├── commands/
│   │   ├── create-feature.md  # Feature full-stack
│   │   ├── sync-types.md      # Sincronizar tipos
│   │   └── deploy.md          # Pipeline de deploy
│   └── skills/
│       ├── api-design.md
│       └── frontend-design.md
│
├── apps/
│   ├── api/
│   └── web/
│
└── packages/
    ├── shared/
    └── config/
```

---

## Carregamento de Contexto Sob Demanda

### A Premissa

Assistentes de IA possuem **janela de contexto limitada**. Carregar toda documentacao em cada interacao gera:

- ❌ **Desperdicio de tokens** (custo e lentidao)
- ❌ **Ruido** (informacao irrelevante)
- ❌ **Perda de foco** (contexto diluido)

**Solucao:** Estruturar documentacao para que o Cursor carregue **apenas o necessario, quando necessario**.

### Estrategias

| Estrategia | Como Aplicar |
|------------|--------------|
| **Separacao** | `alwaysApply: true` vs `false` |
| **Glob Matching** | `glob: "backend/**/*"` |
| **Busca Semantica** | `description` com keywords |
| **Referencia** | Apontar para docs ao inves de inline |

### Cenarios de Carregamento

```
Tarefa do Usuario          │  O que o Cursor Carrega
───────────────────────────┼──────────────────────────────────────
"Crie endpoint REST"       │  rules.mdc + backend.md + api-design.md
"Estilize componente"      │  rules.mdc + frontend.md + frontend-design.md
"Adicione testes"          │  rules.mdc + testing.md
"Revise seguranca"         │  rules.mdc + security.md (sob demanda)
```

---

## Comparacao: Cursor vs Claude Code

| Aspecto | Cursor | Claude Code |
|---------|--------|-------------|
| **Arquivo Base** | `.cursorrules` ou `.cursor/rules/rules.mdc` | `CLAUDE.md` |
| **Rules** | `.cursor/rules/*.md` com frontmatter | `.claude/settings.json` ou refs |
| **Commands** | `.cursor/commands/*.md` | `.claude/commands/` |
| **Skills** | `.cursor/skills/*.md` | Embutido em commands/agents |
| **MCP** | Settings > MCP | `.claude/settings.json` |
| **Simbolos** | `@file`, `@Docs`, `@Web` | Nao tem equivalente direto |

---

## Checklist de Configuracao

### Rules
- [ ] Criar `.cursor/rules/rules.mdc` com `alwaysApply: true`
- [ ] Criar regras contextuais (backend.md, frontend.md)
- [ ] Definir `description` com keywords para busca semantica
- [ ] Usar `glob` para escopo de arquivos

### Commands
- [ ] Identificar tarefas repetitivas
- [ ] Criar commands para workflows comuns
- [ ] Documentar uso e exemplos

### Skills
- [ ] Criar skills para dominios especificos
- [ ] Incluir exemplos Few-Shot
- [ ] Adicionar keywords relevantes na `description`

### MCP
- [ ] Configurar Context7 para documentacao
- [ ] Configurar Serena para busca semantica
- [ ] Testar integracoes

---

## Hierarquia de Carregamento

```
1. Rules com alwaysApply: true
   ↓
2. Rules com glob match no arquivo atual
   ↓
3. Skills com keywords match no contexto
   ↓
4. Commands invocados com /
   ↓
5. MCP e simbolos @ explicitos
```

---

## Referencias

- [Cursor Documentation](https://docs.cursor.com)
- [Cursor Forum](https://forum.cursor.com)
- [MCP Specification](https://modelcontextprotocol.io)
- [Cursor Context Guide](https://docs.cursor.com/guides/working-with-context)
- [Cursor Rules Documentation](https://docs.cursor.com/context/rules)

---

**Ultima Atualizacao**: Fevereiro 2026
