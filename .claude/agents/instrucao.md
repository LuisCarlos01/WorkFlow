# Instruções para Agentes

## O que são Agentes?

Agentes (sub-agents) são assistentes de IA especializados com **janela de contexto separada** da conversa principal. Cada agente é projetado para uma tarefa específica.

## Regras Importantes

### 1. Não encadeie agentes diretamente

> **Não é correto usar um sub-agent para chamar outro sub-agent diretamente.**
> Por isso usamos **commands** para orquestrar o fluxo entre agentes.

### 2. Cada agente tem um propósito específico

| Agente | Propósito |
|--------|-----------|
| `tech-spec-writer` | Criar especificações técnicas |
| `tasks-writer` | Gerar lista de tarefas |
| `code-quality-reviewer` | Revisar e corrigir código |
| `conventional-commit-writer` | Criar commits padronizados |

### 3. Economia de contexto

Usar agentes separados ajuda a:
- Economizar tokens na janela principal
- Manter cada agente focado em sua especialidade
- Evitar confusão de contexto

## Como criar um novo agente

1. Crie um arquivo `.md` em `.claude/agents/`
2. Use o frontmatter YAML:

```yaml
---
name: nome-do-agente
description: Descrição curta do propósito
model: sonnet
color: blue
---
```

3. Defina claramente:
   - Responsabilidades
   - Inputs esperados
   - Outputs produzidos
   - Processo passo a passo

## Boas práticas

- **Seja específico**: Defina exatamente o que o agente deve fazer
- **Documente inputs/outputs**: Deixe claro o que entra e o que sai
- **Use templates**: Referencie templates existentes quando aplicável
- **Mantenha focado**: Um agente = uma responsabilidade
