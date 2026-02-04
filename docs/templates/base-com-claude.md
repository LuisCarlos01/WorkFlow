# Estrutura Base de Projeto para IA

Este documento descreve a arquitetura em camadas para configurar assistentes de IA (Claude, Cursor, etc.) em projetos de desenvolvimento.

---

## Resumo: O Que Cada Camada Diz

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│   ┌─────────────┐                                                           │
│   │     MCP     │  "Aqui está o que você pode ACESSAR"                      │
│   └─────────────┘  → Ferramentas externas, APIs, bancos de dados            │
│         │                                                                   │
│         ▼                                                                   │
│   ┌─────────────┐                                                           │
│   │   Skills    │  "Aqui está COMO fazer as coisas"                         │
│   └─────────────┘  → Workflows, automações, comandos especializados         │
│         │                                                                   │
│         ▼                                                                   │
│   ┌─────────────┐                                                           │
│   │    Rules    │  "Aqui está o conhecimento de DOMÍNIO"                    │
│   └─────────────┘  → Padrões, convenções, regras técnicas                   │
│         │                                                                   │
│         ▼                                                                   │
│   ┌─────────────┐                                                           │
│   │  CLAUDE.md  │  "Aqui está o que você precisa SABER"                     │
│   └─────────────┘  → Contexto do projeto, stack, estrutura                  │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Analogia: Onboarding de um Desenvolvedor

| Camada | Analogia | Pergunta que Responde |
|--------|----------|----------------------|
| **CLAUDE.md** | Manual de boas-vindas | "O que é este projeto?" |
| **Rules** | Guia de estilo e padrões | "Como devemos escrever código aqui?" |
| **Skills** | Playbooks e procedimentos | "Como executo tarefas específicas?" |
| **MCP** | Credenciais e acessos | "Quais ferramentas posso usar?" |

---

## Diagrama: Pirâmide de Configuração

```
                    ┌─────────────────────┐
                    │         MCP         │ ← Ferramentas externas
                    │  (Model Context     │   (APIs, DBs, serviços)
                    │     Protocol)       │
                    └──────────┬──────────┘
                               │
                    ┌──────────▼──────────┐
                    │       Skills        │ ← Workflows complexos
                    │   (Comandos e       │   (automações, pipelines)
                    │     Agentes)        │
                    └──────────┬──────────┘
                               │
                    ┌──────────▼──────────┐
                    │       Rules         │ ← Conhecimento de domínio
                    │  (Regras e          │   (padrões, convenções)
                    │   Diretrizes)       │
                    └──────────┬──────────┘
                               │
        ┌──────────────────────▼──────────────────────┐
        │      CLAUDE.md / AntiGravity / CursoR       │ ← Base do projeto
        │         (Configuração Fundamental)          │   (contexto, stack)
        └─────────────────────────────────────────────┘
```

---

## 1. Base do Projeto (Camada Fundamental)

### O que é

Arquivo principal de configuração que define o contexto fundamental do projeto para a IA.

### Nomenclaturas por Ferramenta

| Ferramenta | Arquivo |
|------------|---------|
| Claude Code | `CLAUDE.md` |
| Cursor | `.cursorrules` ou `.cursor/rules/` |
| AntiGravity | `antigravity.md` |
| Windsurf | `.windsurfrules` |
| Copilot | `.github/copilot-instructions.md` |

### Conteúdo Essencial

```markdown
# Projeto [NOME]

## Contexto
[Descrição breve do projeto e seu propósito]

## Stack Tecnológica
- Linguagem: [ex: TypeScript]
- Framework: [ex: Next.js]
- Banco de dados: [ex: PostgreSQL]

## Estrutura de Pastas
[Descrição da organização do código]

## Convenções
- Commits: Conventional Commits
- Código: [padrões específicos]
- Nomenclatura: [padrões de nomes]
```

### Exemplo: CLAUDE.md

```markdown
# Projeto E-commerce API

## Contexto
API REST para plataforma de e-commerce com autenticação JWT,
gerenciamento de produtos e processamento de pedidos.

## Stack
- Node.js 20 + TypeScript
- Express.js
- Prisma + PostgreSQL
- Jest para testes

## Estrutura
src/
├── controllers/   # Handlers de rotas
├── services/      # Lógica de negócio
├── repositories/  # Acesso a dados
├── middleware/    # Auth, validation
└── utils/         # Helpers

## Convenções
- Commits em pt-br, sem acentos
- Funções async/await (nunca callbacks)
- Validação com Zod em todas as entradas
```

---

## 2. Rules (Conhecimento de Domínio)

### O que é

Regras específicas que definem padrões, convenções e conhecimento técnico do projeto.

### Localização

| Ferramenta | Localização |
|------------|-------------|
| Claude Code | `.claude/settings.json` ou arquivos `.md` referenciados |
| Cursor | `.cursor/rules/*.mdc` |

### Tipos de Regras

```
rules/
├── general.md        # Regras gerais do projeto
├── backend.md        # Padrões de backend
├── frontend.md       # Padrões de frontend
├── testing.md        # Convenções de testes
└── security.md       # Diretrizes de segurança
```

### Exemplo: backend.md

```markdown
# Regras de Backend

## Arquitetura
- Usar arquitetura em camadas: Controller → Service → Repository
- Controllers apenas recebem requests e retornam responses
- Services contêm toda lógica de negócio
- Repositories abstraem acesso a dados

## Tratamento de Erros
- Usar classes de erro customizadas
- Sempre logar erros com contexto
- Retornar mensagens amigáveis ao cliente

## Validação
- Validar todas as entradas com Zod
- Schemas em arquivos separados
- Reutilizar schemas entre endpoints

## Padrões de Código
✅ Funções pequenas (máx 20 linhas)
✅ Nomes descritivos em inglês
✅ Tipagem explícita sempre
❌ Nunca usar `any`
❌ Não misturar async/await com .then()
```

---

## 3. Skills (Workflows Complexos)

### O que é

Comandos e agentes especializados que executam tarefas complexas e repetitivas.

### Localização

| Ferramenta | Localização |
|------------|-------------|
| Claude Code | `.claude/commands/` |
| Cursor | Composer commands |

### Estrutura de uma Skill

```
.claude/commands/
├── create-component/
│   ├── SKILL.md           # Instruções
│   ├── scripts/
│   │   └── generate.sh    # Scripts executáveis
│   └── assets/
│       └── template.tsx   # Templates
│
├── run-tests/
│   └── SKILL.md
│
└── deploy/
    ├── SKILL.md
    └── scripts/
        └── deploy.sh
```

### Exemplo: create-component SKILL.md

```markdown
# create-component

## Descrição
Cria componentes React seguindo os padrões do projeto.
Gera arquivo do componente, estilos e testes.

**Keywords:** componente, react, criar, novo

## Quando Usar
- Criar novo componente React
- Gerar estrutura padrão com testes

## Instruções
1. Receber nome do componente
2. Criar pasta em src/components/
3. Gerar arquivos usando templates
4. Adicionar exports no index

## Regras
✅ PascalCase para nomes
✅ Sempre criar teste junto
❌ Não criar sem especificação clara
```

---

## 4. MCP (Ferramentas Externas)

### O que é

Model Context Protocol - integração com ferramentas externas, APIs e serviços.

### Localização

| Ferramenta | Configuração |
|------------|--------------|
| Claude Code | `.claude/settings.json` → `mcpServers` |
| Cursor | Settings → MCP |

### Tipos de Integrações

```
┌─────────────────────────────────────────────────────────────┐
│                     MCP Servers                             │
├─────────────────┬───────────────────────────────────────────┤
│  Documentação   │  Context7, DevDocs                        │
├─────────────────┼───────────────────────────────────────────┤
│  Código         │  Serena (semantic search), GitHub         │
├─────────────────┼───────────────────────────────────────────┤
│  Banco de Dados │  PostgreSQL MCP, MongoDB MCP              │
├─────────────────┼───────────────────────────────────────────┤
│  Cloud          │  AWS MCP, GCP MCP                         │
├─────────────────┼───────────────────────────────────────────┤
│  Outros         │  Slack, Jira, Notion                      │
└─────────────────┴───────────────────────────────────────────┘
```

### Exemplo: Configuração MCP

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

---

## Fluxo de Resolução

```
┌─────────────────────────────────────────────────────────────────────┐
│                        Requisição do Usuário                        │
└───────────────────────────────┬─────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────────┐
│  1. BASE DO PROJETO                                                 │
│     Carrega contexto fundamental (CLAUDE.md)                        │
│     → Entende stack, estrutura, convenções básicas                  │
└───────────────────────────────┬─────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────────┐
│  2. RULES                                                           │
│     Aplica regras de domínio relevantes                             │
│     → Padrões de código, arquitetura, segurança                     │
└───────────────────────────────┬─────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────────┐
│  3. SKILLS                                                          │
│     Executa workflows se aplicável                                  │
│     → Comandos especializados, agentes                              │
└───────────────────────────────┬─────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────────┐
│  4. MCP                                                             │
│     Consulta ferramentas externas se necessário                     │
│     → Documentação, APIs, bancos de dados                           │
└───────────────────────────────┬─────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────────┐
│                           Resposta                                  │
└─────────────────────────────────────────────────────────────────────┘
```

---

## Exemplos Completos (Few-Shot)

### Exemplo 1: Projeto Node.js API

```
projeto-api/
│
├── CLAUDE.md                    # Base do projeto
│
├── .claude/
│   ├── settings.json            # Config MCP
│   └── commands/
│       ├── create-endpoint/     # Skill
│       └── run-tests/           # Skill
│
└── .cursor/
    └── rules/
        ├── general.mdc          # Rules gerais
        └── backend.mdc          # Rules backend
```

**CLAUDE.md:**
```markdown
# API de Pedidos

## Stack
- Node.js 20 + TypeScript
- Express + Prisma + PostgreSQL
- Jest + Supertest

## Convenções
- Conventional Commits em pt-br
- Clean Architecture
- Validação com Zod
```

---

### Exemplo 2: Projeto React Frontend

```
projeto-web/
│
├── CLAUDE.md                    # Base do projeto
│
├── .claude/
│   └── commands/
│       ├── create-component/    # Skill
│       ├── create-page/         # Skill
│       └── create-hook/         # Skill
│
└── .cursor/
    └── rules/
        ├── general.mdc          # Rules gerais
        ├── frontend.mdc         # Rules frontend
        └── testing.mdc          # Rules testes
```

**CLAUDE.md:**
```markdown
# E-commerce Frontend

## Stack
- React 18 + TypeScript
- Next.js 14 (App Router)
- Tailwind CSS + Shadcn/ui
- Zustand para estado
- Vitest + Testing Library

## Estrutura
src/
├── app/           # Rotas (Next.js)
├── components/    # Componentes reutilizáveis
├── hooks/         # Custom hooks
├── stores/        # Estado global
└── lib/           # Utilitários
```

---

### Exemplo 3: Projeto Full-Stack Monorepo

```
projeto-fullstack/
│
├── CLAUDE.md                    # Base do projeto
│
├── .claude/
│   ├── settings.json            # Config MCP
│   └── commands/
│       ├── create-feature/      # Skill full-stack
│       ├── sync-types/          # Skill compartilhar tipos
│       └── deploy/              # Skill deploy
│
├── .cursor/
│   └── rules/
│       ├── general.mdc
│       ├── backend.mdc
│       ├── frontend.mdc
│       └── monorepo.mdc
│
├── apps/
│   ├── api/                     # Backend
│   └── web/                     # Frontend
│
└── packages/
    ├── shared/                  # Código compartilhado
    └── config/                  # Configurações
```

---

## Checklist de Configuração

### Base do Projeto
- [ ] Criar arquivo principal (CLAUDE.md / .cursorrules)
- [ ] Definir contexto e propósito do projeto
- [ ] Listar stack tecnológica completa
- [ ] Documentar estrutura de pastas
- [ ] Estabelecer convenções básicas

### Rules
- [ ] Criar regras gerais do projeto
- [ ] Criar regras específicas por domínio (backend, frontend, etc.)
- [ ] Definir padrões de código
- [ ] Documentar convenções de nomenclatura
- [ ] Estabelecer diretrizes de segurança

### Skills
- [ ] Identificar tarefas repetitivas
- [ ] Criar skills para workflows comuns
- [ ] Documentar instruções claras
- [ ] Incluir exemplos de uso
- [ ] Adicionar scripts auxiliares se necessário

### MCP
- [ ] Identificar ferramentas externas necessárias
- [ ] Configurar servidores MCP
- [ ] Testar integrações
- [ ] Documentar uso de cada ferramenta

---

## Referências

- [Claude Code Documentation](https://docs.anthropic.com/claude-code)
- [Cursor Rules](https://cursor.sh/docs/rules)
- [MCP Specification](https://modelcontextprotocol.io)
