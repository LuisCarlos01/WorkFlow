# WorkFlow visão superior

## Pense no fluxo assim:

- RULES → SKILLS → SUBAGENTS → COMMANDS → SEMANTIC SEARCH

## Não é hierarquia rígida, é um ciclo operacional.

**RULES**: leis do universo. Sempre verdadeiras, raramente chamadas explicitamente.

**SKILLS**: capacidades reutilizáveis. “Como fazer”.

**SUBAGENTS**: especialistas. “Quem faz”.

**COMMANDS**: ações acionáveis. “Quando fazer”.

**SEMANTIC SEARCH**: memória inteligente. “Onde buscar contexto”.

**HOOKS**: 

O erro comum é misturar tudo num prompt só. O acerto é delegar responsabilidade.

---

## Fluxo prático automatizado (exemplo real)

Vamos usar um cenário concreto:

“Quero refatorar um componente React, garantir testes e manter padrões do projeto.”

O que acontece por baixo dos panos:

RULES já estão carregadas
→ estilo, arquitetura, restrições, padrões de teste.

COMMAND é acionado
→ /refactor-component

O COMMAND delega para um SUBAGENT especializado
→ refactor-assistant

O SUBAGENT usa SKILLS
→ analyze-code, safe-refactor, test-awareness

Antes de agir, o agente consulta a SEMANTIC SEARCH
→ encontra padrões existentes, componentes similares, decisões anteriores.

Só então o código é modificado.

Isso reduz tokens, aumenta consistência e evita “alucinação arquitetural”.

---

## Estrutura-base de workflow (template)

.cursor/
├── rules/
│   ├── base.mdc
│   ├── frontend.mdc
│   └── testing.mdc
├── skills/
│   ├── analyze-code.md
│   ├── refactor-safely.md
│   └── write-tests.md
├── subagents/
│   ├── refactor-assistant.md
│   ├── test-engineer.md
│   └── code-reviewer.md
├── commands/
│   ├── refactor-component.md
│   ├── generate-tests.md
│   └── review-pr.md
├── semantic/
│   ├── index-config.json
│   └── semantic-guide.md
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
.cursor/skills/refactor-safely.md
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

## SUBAGENTS — especialistas cognitivos
.cursor/subagents/refactor-assistant.md
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


Commands são o botão que o humano aperta. Nada de lógica aqui — só orquestração.

## SEMANTIC SEARCH — memória contextual
.cursor/semantic/index-config.json (exemplo conceitual)
{
  "include": ["src/**"],
  "exclude": ["node_modules", "dist"],
  "priority": [
    "src/components",
    "src/hooks",
    "src/services"
  ]
}

.cursor/semantic/semantic-guide.md
# Semantic Search Usage

## Purpose
Retrieve code by meaning, not filename.

## Recommended Queries
- "components similar to X"
- "existing patterns for API calls"
- "how tests are structured in this project"

## Best Practices
- Always search before creating something new
- Prefer existing abstractions

## Fluxo resumido (visão de engenharia)
User Intent
   ↓
COMMAND
   ↓
SUBAGENT
   ↓
SKILLS
   ↓
SEMANTIC SEARCH (context)
   ↓
RULES (constraints)
   ↓
Action (code / docs / tests)


Isso é prompt engineering de verdade:
menos texto, mais estrutura; menos improviso, mais sistema.

## Como reutilizar em qualquer projeto

Quando iniciar um novo projeto:

Copie a estrutura .cursor

Ajuste apenas:

rules/ (tecnologia e padrões)

semantic/index-config.json

Reaproveite:

skills

subagents

commands

Você constrói um arsenal cognitivo que evolui com você.

---

Encerrando com a ideia central

A .cursor não é configuração.É arquitetura de pensamento aplicada a LLMs.

Quando bem feita, a IA deixa de ser “geradora de código” e vira um sistema operacional de decisão técnica.