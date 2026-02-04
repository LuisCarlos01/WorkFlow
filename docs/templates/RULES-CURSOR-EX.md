# Exemplo de Rules para Cursor IDE

Este documento apresenta um exemplo completo de arquivo de regras (`.mdc`) para o Cursor IDE.

---

## Estrutura de uma Rule

As rules do Cursor são definidas em arquivos `.mdc` localizados em `.cursor/rules/`.

### Frontmatter

```yaml
---
description: Descricao curta da regra (usada para matching)
globs: 
alwaysApply: true/false
---
```

| Campo | Descrição |
|-------|-----------|
| `description` | Texto curto que descreve quando a regra se aplica |
| `globs` | Padrões de arquivo para aplicação automática (ex: `**/*.ts`) |
| `alwaysApply` | Se `true`, aplica sempre; se `false`, aplica conforme globs/contexto |

---

## Exemplo Completo: Regras Globais

```markdown
---
description: Regras globais do projeto que devem ser sempre aplicadas
globs: 
alwaysApply: true
---

# Regras Gerais do Projeto

## MCP (Model Context Protocol)

**SEMPRE** use as seguintes ferramentas MCP:

- **Context7** - Para buscar documentação atualizada de bibliotecas
- **Serena** - Para semantic retrieval e editing tools

## Convenções Git

### Commits

Siga **Conventional Commits**: `<type>(<scope>): <subject>`

**Tipos:**
- `feat`: Nova funcionalidade
- `fix`: Correção de bug
- `docs`: Documentação
- `chore`: Tarefas de manutenção
- `refactor`: Refatoração

**Escopos comuns:** `api`, `web`, `ui`, `backend`, `frontend`

### Importante: Caracteres Especiais

**NÃO use** caracteres especiais em mensagens de commit:

❌ **Errado:** `feat: adiciona configuração`  
✅ **Correto:** `feat: adiciona configuracao`

### Idioma dos Commits

**SEMPRE escreva commits em português brasileiro (pt-br)**:

✅ **Correto:** `feat: adiciona autenticacao de usuarios`  
❌ **Errado:** `feat: add user authentication`

## Estrutura do Projeto

```text
project-root/
├── backend/            # Código do servidor
├── frontend/           # Código do cliente
├── shared/             # Código compartilhado
└── docs/               # Documentação
```
```

---

## Exemplo: Regras de Backend

```markdown
---
description: Regras especificas para desenvolvimento backend
globs: backend/**/*
alwaysApply: false
---

# Regras de Backend

## Stack Tecnológica

- **Runtime:** Node.js 20+
- **Linguagem:** TypeScript 5.x (strict mode)
- **Framework:** Fastify 4.x
- **ORM:** Prisma 5.x
- **Banco:** PostgreSQL 16

## Arquitetura

Seguir Clean Architecture com camadas:

```text
src/
├── controllers/    # Entrada HTTP
├── use-cases/      # Lógica de negócio
├── repositories/   # Acesso a dados
├── entities/       # Modelos de domínio
└── shared/         # Utilitários
```

## Padrões de Código

### Nomenclatura

- Arquivos: kebab-case (ex: `user-service.ts`)
- Classes: PascalCase (ex: `UserService`)
- Funções: camelCase (ex: `getUserById`)
- Constantes: UPPER_SNAKE_CASE (ex: `API_BASE_URL`)

### Validação

- SEMPRE use Zod para validar inputs
- Nunca confie em dados externos
- Sanitize antes de usar

### Tratamento de Erros

- Use classes de erro customizadas
- Sempre log erros com contexto
- Retorne respostas HTTP apropriadas
```

---

## Exemplo: Regras de Frontend

```markdown
---
description: Regras especificas para desenvolvimento frontend
globs: frontend/**/*
alwaysApply: false
---

# Regras de Frontend

## Stack Tecnológica

- **Framework:** React 18
- **Linguagem:** TypeScript 5.x
- **Estilização:** Tailwind CSS 3.x + shadcn/ui
- **Estado:** Zustand 4.x
- **Build:** Vite 5.x

## Estrutura de Componentes

```text
src/
├── components/     # Componentes reutilizáveis
├── features/       # Features organizadas
├── hooks/          # Hooks customizados
├── lib/            # Utilitários
└── stores/         # Estado global
```

## Padrões de Código

### Nomenclatura

- Componentes: PascalCase (ex: `UserProfile.tsx`)
- Hooks: camelCase com prefixo `use` (ex: `useAuth.ts`)
- Utilitários: kebab-case (ex: `format-date.ts`)

### Componentes

- SEMPRE funcionais com hooks
- Props tipadas com TypeScript
- Composição sobre herança
- Máximo 150 linhas por componente

### Estilização

- Tailwind para estilos utilitários
- shadcn/ui para componentes base
- CSS Modules apenas quando necessário
```

---

## Checklist de Criação de Rules

- [ ] Frontmatter com `description` descritiva
- [ ] `globs` configurado se não for `alwaysApply`
- [ ] `alwaysApply: true` apenas para regras globais
- [ ] Conteúdo claro e objetivo
- [ ] Exemplos quando apropriado
- [ ] Nomenclatura consistente
- [ ] Regras de "fazer" e "não fazer"

---

## Referências

- [Documentação do Cursor](https://docs.cursor.com)
- [Regras Globais](../../.cursor/rules/rules.mdc)
- [Regras de Backend](../../.cursor/rules/backend.md)
- [Regras de Frontend](../../.cursor/rules/frontend.md)
