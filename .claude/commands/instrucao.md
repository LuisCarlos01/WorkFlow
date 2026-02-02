# Instruções para Commands

## O que são Commands?

Commands são **prompts prontos** que você pode invocar facilmente através de um comando. Eles servem para orquestrar agentes e automatizar fluxos de trabalho.

## Por que usar Commands?

> Um comando é um prompt pronto que você consegue chamá-lo de maneira fácil.

Commands são úteis porque:
1. **Padronizam** o uso de agentes
2. **Orquestram** múltiplos agentes em sequência
3. **Simplificam** tarefas complexas em um único comando
4. **Documentam** o fluxo de trabalho

## Como criar um novo Command

1. Crie um arquivo `.md` em `.claude/commands/`
2. O nome do arquivo será o nome do comando (ex: `create-techspec.md` → `/create-techspec`)
3. Use `$ARGUMENTS` para capturar parâmetros do usuário

### Estrutura básica:

```markdown
Use o @nome-do-agente para realizar a tarefa.

## Input

**Parâmetro**: `$ARGUMENTS`

## Processo

1. Primeiro passo
2. Segundo passo
3. Terceiro passo

## Output

- Arquivo gerado: `caminho/do/arquivo.md`

## Próximos passos

Após completar, sugira o próximo comando.
```

## Commands disponíveis

| Comando | Agente usado | Propósito |
|---------|--------------|-----------|
| `/create-techspec {slug}` | `@tech-spec-writer` | Criar Tech Spec |
| `/create-task {slug}` | `@tasks-writer` | Gerar tasks |
| `/execute-task {slug} {num}` | Direto | Executar uma task |
| `/execute-feature-task {slug}` | Orquestrador | Executar todas as tasks |

## Boas práticas

- **Use agentes especializados**: Delegue para o agente correto
- **Documente inputs/outputs**: Deixe claro o que esperar
- **Sugira próximos passos**: Guie o usuário no fluxo
- **Valide pré-requisitos**: Verifique se arquivos necessários existem