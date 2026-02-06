# WorkFlow visão superior

## Pense no fluxo assim:

- RULES → SKILLS → SUBAGENTS → COMMANDS → SEMANTIC SEARCH → HOOKS

## Não é hierarquia rígida, é um ciclo operacional.

**RULES**: leis do universo. Sempre verdadeiras, raramente chamadas explicitamente.

**SKILLS**: capacidades reutilizáveis. “Como fazer”.

**SUBAGENTS**: especialistas. “Quem faz”.

**COMMANDS**: ações acionáveis. “Quando fazer”.

**SEMANTIC SEARCH**: memória inteligente. “Onde buscar contexto”.

**HOOKS**: automacoes do agente. "O que executar antes/depois de acoes".

O erro comum é misturar tudo num prompt só. O acerto é delegar responsabilidade.

---

## Fluxo prático automatizado (exemplo real)

Vamos usar um cenário concreto:

“Quero refatorar um componente React, garantir testes e manter padrões do projeto.”

O que acontece por baixo dos panos:

RULES já estão carregadas
→ estilo, arquitetura, restrições, padrões de teste.

COMMAND é acionado pelo usuário
→ /refactor-component (um arquivo Markdown com instruções)

O AGENT interpreta o command e, com base na complexidade da tarefa e nas descrições dos subagents disponíveis, decide delegar para um SUBAGENT especializado
→ refactor-assistant

O SUBAGENT usa SKILLS
→ analyze-code, safe-refactor, test-awareness

Antes de agir, o agente consulta a SEMANTIC SEARCH
→ encontra padrões existentes, componentes similares, decisões anteriores.

Só então o código é modificado.

> **Nota:** Commands não têm lógica de delegação embutida. São arquivos Markdown simples com instruções. Quem decide se e quando delegar para subagents é o Agent, autonomamente.

Isso reduz tokens, aumenta consistência e evita “alucinação arquitetural”.

---

## Estrutura-base de workflow (template)

.cursor/
├── rules/
│   ├── base.mdc
│   ├── frontend.mdc
│   └── testing.mdc
├── skills/
│   ├── analyze-code/
│   │   └── SKILL.md
│   ├── refactor-safely/
│   │   └── SKILL.md
│   └── write-tests/
│       └── SKILL.md
├── agents/
│   ├── refactor-assistant.md
│   ├── test-engineer.md
│   └── code-reviewer.md
├── commands/
│   ├── refactor-component.md
│   ├── generate-tests.md
│   └── review-pr.md
├── search-semantic/
│   └── search-semantic-context.md  # Documentacao (indexacao e gerenciada pelo Cursor)
└── utils/
    └── context-policy.md

Agora vamos aos templates reais.

---

## RULES — leis do sistema (template .mdc)
.cursor/rules/frontend.mdc
---
description: "Frontend architecture and style rules"
globs: ["src/**/*.tsx", "src/**/*.ts"]
alwaysApply: true
---

# Architecture
- Components must be small and composable
- Business logic must not live inside UI components

# Styling
- Tailwind CSS only
- No inline styles

# Refactoring Rules
- Never change behavior without explicit instruction
- Prefer incremental refactors

# Tests
- New or refactored components must include tests


Boas práticas aplicadas aqui

Regras curtas

Sem explicar “por quê”

Sem exemplos longos

Sempre verdadeiras

## SKILLS — capacidades reutilizáveis
.cursor/skills/refactor-safely/SKILL.md
---
name: refactor-safely
description: Apply refactors without altering observable behavior.
---

# Skill: Safe Refactoring

## Purpose
Apply refactors without altering observable behavior.

## Steps
1. Identify responsibilities of the current code
2. Detect code smells (duplication, long functions, tight coupling)
3. Apply small, reversible changes
4. Preserve public APIs
5. Ensure tests pass or are added

## Constraints
- No breaking changes
- No stylistic refactors unless necessary

## Output
- Cleaner structure
- Same external behavior


Mentalidade: skill é como fazer, não quando nem quem.

> **Importante:** Cada skill deve ser uma **pasta** contendo um arquivo `SKILL.md`, nao um arquivo `.md` solto.

## SUBAGENTS — especialistas cognitivos
.cursor/agents/refactor-assistant.md
# Subagent: Refactor Assistant

## Role
Specialist in structural code improvements without behavior changes.

## When to Use
- Refactoring requests
- Code smells detected
- Large or complex components

## Skills Used
- analyze-code
- refactor-safely
- write-tests

## Context Scope
- Target file
- Related components (via semantic search)
- Applicable rules

## Instructions
- Always inspect existing patterns via semantic search
- Prefer minimal diffs
- Flag risky refactors instead of executing blindly


Aqui nasce a inteligência real do sistema: foco + limites claros.

## COMMANDS — gatilhos explícitos
.cursor/commands/refactor-component.md
# Command: Refactor Component

## Trigger
User requests refactoring of a component or file.

## Flow
1. Load applicable rules
2. Invoke Refactor Assistant subagent
3. Perform semantic search for similar components
4. Apply safe refactor
5. Suggest or generate tests

## Output
- Refactored code
- Summary of changes
- Test recommendations


Commands são o botão que o humano aperta. Nada de lógica aqui — são instruções em Markdown que o Agent lê, interpreta e executa. O Agent é quem decide se delega para subagents ou não, com base na complexidade da tarefa.

## SEMANTIC SEARCH — memória contextual (gerenciada pelo Cursor)

> A busca semantica e **totalmente gerenciada pelo Cursor**. Nao existe arquivo de configuracao como `index-config.json`. O Cursor indexa automaticamente todos os arquivos do workspace, exceto os listados em `.gitignore` e `.cursorignore`.

Para controlar o que e indexado, use `.cursorignore`:

```
# .cursorignore - Excluir da indexacao semantica
node_modules/
dist/
*.test.ts
```

### Consultas recomendadas

- "components similar to X"
- "existing patterns for API calls"
- "how tests are structured in this project"

### Boas praticas

- Sempre buscar antes de criar algo novo
- Preferir abstracoes existentes
- Manter `.cursorignore` atualizado

## Fluxo resumido (visão de engenharia)
User Intent
   ↓
COMMAND (instrução em Markdown — acionado pelo usuário)
   ↓
AGENT (interpreta o command e decide como executar)
   ↓
SUBAGENT (se a tarefa for complexa — decisão do Agent)
   ↓
SKILLS (capacidades reutilizáveis)
   ↓
SEMANTIC SEARCH (contexto)
   ↓
RULES (restrições — sempre ativas)
   ↓
Action (code / docs / tests)

> O Agent é o orquestrador central. Commands descrevem "o que fazer", mas é o Agent que decide "como fazer" — incluindo se usa subagents ou não.


Isso é prompt engineering de verdade:
menos texto, mais estrutura; menos improviso, mais sistema.

## Como reutilizar em qualquer projeto

Quando iniciar um novo projeto:

Copie a estrutura .cursor

Ajuste apenas:

rules/ (tecnologia e padroes)

.cursorignore (quais arquivos excluir da indexacao)

Reaproveite:

skills

subagents

commands

Você constrói um arsenal cognitivo que evolui com você.

---

Encerrando com a ideia central

A .cursor não é configuração.É arquitetura de pensamento aplicada a LLMs.

Quando bem feita, a IA deixa de ser “geradora de código” e vira um sistema operacional de decisão técnica.