# Guia Básico - Workflow com IA

Este guia explica como usar o workflow de desenvolvimento com IA de forma eficiente.

## Conceitos Fundamentais

### 1. Sub-Agents (Agentes Especializados)

Sub-agents são agentes de IA com **janela de contexto separada**. Isso é importante porque:

1. **Propósito específico** - Crie-os para tarefas bem definidas e use-os de maneira inteligente
2. **Economia de tokens** - Cada agente mantém seu próprio contexto, evitando sobrecarregar a janela principal
3. **Parte do fluxo** - Eles são componentes de um workflow maior

#### Agentes disponíveis neste projeto:

| Agente | Propósito |
|--------|-----------|
| `@tech-spec-writer` | Cria especificações técnicas detalhadas |
| `@tasks-writer` | Gera lista de tarefas a partir da Tech Spec |
| `@code-quality-reviewer` | Revisa código e aplica correções |
| `@conventional-commit-writer` | Cria commits seguindo padrões |

### 2. Commands (Comandos)

Commands são **prompts prontos** que você pode chamar facilmente. Eles orquestram os agentes.

> **Importante**: Não é correto um sub-agent chamar outro sub-agent diretamente. Por isso usamos commands para orquestrar o fluxo.

#### Comandos disponíveis:

| Comando | O que faz |
|---------|-----------|
| `/create-techspec {slug}` | Cria uma Tech Spec para uma feature |
| `/create-task {slug}` | Gera tasks a partir da Tech Spec |
| `/execute-task {slug} {num}` | Executa uma task específica |
| `/execute-feature-task {slug}` | Executa todas as tasks de uma feature |

## Fluxo de Trabalho Completo

```mermaid
flowchart LR
    A[PRD/Ideia] --> B[/create-techspec]
    B --> C[Tech Spec]
    C --> D[/create-task]
    D --> E[Tasks]
    E --> F[/execute-task]
    F --> G[Implementação]
    G --> H[@code-quality-reviewer]
    H --> I[@conventional-commit-writer]
    I --> J[Done!]
```

### Passo a passo:

1. **Defina a feature** - Tenha claro o que você quer construir (PRD opcional)
2. **Crie a Tech Spec** - `/create-techspec minha-feature`
3. **Gere as Tasks** - `/create-task minha-feature`
4. **Execute as Tasks** - `/execute-task minha-feature 01`
5. **Revise o código** - O agente de review é chamado automaticamente
6. **Commit** - O agente de commit é chamado automaticamente

## Estrutura de Pastas

```
docs/
├── tasks/
│   └── {feature-slug}/
│       ├── prd.md          # (opcional) Requisitos do produto
│       ├── techspec.md     # Especificação técnica
│       ├── tasks.md        # Resumo das tasks
│       ├── 01_task.md      # Task individual
│       └── 02_task.md      # Task individual
├── templates/
│   ├── techspec.md         # Template da Tech Spec
│   ├── tasks.md            # Template do resumo
│   └── task.md             # Template da task
└── workflow.md             # Diagrama do fluxo
```

## Dicas Importantes

1. **Sempre dê contexto** - Quanto mais específico, melhor o resultado
2. **Use Rules** - Configure regras no `.cursor/rules/` para padrões do projeto
3. **Especifique ferramentas** - Diga quais libs e frameworks usar
4. **Siga o fluxo** - Tech Spec → Tasks → Implementação → Review → Commit
