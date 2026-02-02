# Instruções de Projeto - WorkFlow

Este é um repositório de estudo para desenvolvimento assistido por IA seguindo a metodologia **Spec-Driven Development (SDD)**.

## Contexto do Projeto

WorkFlow é um framework que implementa um fluxo de trabalho estruturado para desenvolvimento com IA, usando agentes especializados e comandos customizados para criar especificações técnicas, gerar tarefas e executar código com qualidade.

## MCP (Model Context Protocol)

**SEMPRE** use as seguintes ferramentas MCP ao trabalhar neste projeto:

### Context7

- Use para buscar documentação atualizada de bibliotecas, frameworks e código de terceiros
- Essencial para garantir uso correto de APIs e padrões externos

### Serena

- Use para semantic retrieval e editing tools
- Use para busca semântica de código
- Use para operações inteligentes de edição

**Quando usar cada ferramenta:**

- Buscar documentação de bibliotecas/frameworks → Context7
- Buscar padrões de código semanticamente → Serena
- Realizar edições inteligentes de código → Serena
- Recuperar contexto de codebases → Serena

## Convenções Git

### Conventional Commits

**SEMPRE** siga o padrão Conventional Commits: `<type>(<scope>): <subject>`

**Tipos comuns:**

- `feat`: Nova funcionalidade
- `fix`: Correção de bug
- `docs`: Documentação
- `chore`: Tarefas de manutenção
- `refactor`: Refatoração de código

**Escopos comuns:** `api`, `web`, `ui`, `backend`, `frontend`, `docs`, `config`, `rules`

**Exemplo:** `feat(api): adiciona autenticacao OAuth2`

Referência: [Conventional Commits](https://www.conventionalcommits.org/pt-br/v1.0.0-beta.4/)

### ⚠️ IMPORTANTE: Caracteres Especiais

**NÃO use caracteres especiais em mensagens de commit** (acentos, ç, til, etc.):

❌ **Errado:** `feat: adiciona configuração`  
✅ **Correto:** `feat: adiciona configuracao`

**Motivo:** O GitHub pode exibir caracteres corrompidos (ex: "configuraĂÂ£es" ao invés de "configurações").

**Caracteres a evitar:** `á é í ó ú ã õ â ê ô ç ñ à`

### 🌐 Idioma dos Commits

**SEMPRE escreva commits em português brasileiro (pt-br)**:

✅ **Correto:** `feat: adiciona autenticacao de usuarios`  
❌ **Errado:** `feat: add user authentication`

**Motivo:** Este é um repositório de estudo em pt-br. Manter consistência no idioma facilita a leitura e compreensão do histórico.

## Estrutura do Projeto

```text
WorkFlow/
├── .claude/
│   ├── agents/              # Agentes especializados
│   │   ├── tech-spec-writer.md
│   │   ├── tasks-writer.md
│   │   ├── code-quality-reviewer.md
│   │   └── conventional-commit-writer.md
│   └── commands/            # Comandos do workflow
│       ├── create-techspec.md
│       ├── create-task.md
│       ├── execute-task.md
│       └── execute-feature-task.md
├── .cursor/
│   └── rules/               # Regras específicas (Cursor)
│       ├── rules.mdc        # Regras gerais
│       ├── backend.md       # Regras de backend
│       └── frontend.md      # Regras de frontend
├── docs/
│   ├── templates/           # Templates reutilizáveis
│   │   ├── techspec.md
│   │   ├── tasks.md
│   │   └── task.md
│   ├── tasks/               # Features em desenvolvimento
│   ├── guiabasico.md
│   ├── workflow.md
│   └── spec-driven-development.md
├── CLAUDE.md                # Este arquivo
└── README.md
```

## Workflow de Desenvolvimento

Este projeto segue o Spec-Driven Development (SDD):

1. **Ideia** → Conceito inicial
2. **PRD** → Product Requirements Document
3. **Tech Spec** → Especificação técnica detalhada
4. **Tasks** → Lista de tarefas geradas da spec
5. **Código** → Implementação
6. **Review** → Revisão de qualidade
7. **Commit** → Commit padronizado

### Comandos Disponíveis

- `/create-techspec {slug}` - Cria uma Tech Spec para uma feature
- `/create-task {slug}` - Gera tasks a partir da Tech Spec
- `/execute-task {slug} {num}` - Executa uma task específica
- `/execute-feature-task {slug}` - Executa todas as tasks de uma feature

### Agentes Especializados

- `@tech-spec-writer` - Cria especificações técnicas detalhadas
- `@tasks-writer` - Gera lista de tarefas a partir da Tech Spec
- `@code-quality-reviewer` - Revisa código e aplica correções
- `@conventional-commit-writer` - Cria commits seguindo Conventional Commits

## Padrões de Código

### Documentação

- Use markdown para toda documentação
- Mantenha documentação atualizada junto com o código
- Use exemplos práticos e claros

### Organização

- Siga a estrutura de pastas estabelecida
- Use nomenclatura descritiva e consistente
- Mantenha separação clara entre diferentes contextos (agentes, comandos, regras, templates)

### Qualidade

- Especificações antes de código (Spec-Driven)
- Review de código antes de commit
- Commits padronizados e descritivos

## Referências

Para regras específicas de tecnologias, consulte:

- Backend: `.cursor/rules/backend.md`
- Frontend: `.cursor/rules/frontend.md`

Para documentação do workflow:

- [README](README.md) - Visão geral
- [Guia Básico](docs/guiabasico.md) - Como usar
- [Spec-Driven Development](docs/spec-driven-development.md) - Metodologia
- [Workflow](docs/workflow.md) - Diagrama do processo
