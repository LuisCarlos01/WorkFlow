# Few-Shot: Behavior-Driven Development (BDD)

Aplique a tecnica de **Few-Shot Prompting** para trabalhar com **Behavior-Driven Development (BDD)**.

## Referencia

- Template: @prompts/Techniques/Prompt-FewShot.md
- Workflow: @docs/workflows/behavior-driven-development.md

## Input

**Contexto/Tarefa**: `$ARGUMENTS`

## Processo

1. **Carregar Template e Workflow**:
   - Leia o arquivo `prompts/Techniques/Prompt-FewShot.md` para obter o template completo
   - Leia o arquivo `docs/workflows/behavior-driven-development.md` para entender BDD
   - Entenda a estrutura: Role, Contexto, Regras, Exemplos, Instrucao Final

2. **Analisar Requisitos**:
   - Identifique o comportamento do sistema que precisa ser especificado
   - Identifique o tipo de projeto/tarefa
   - Identifique framework BDD (Cucumber, Behave, SpecFlow, etc.)

3. **Criar Exemplos Relevantes de BDD**:
   - Gere 2-5 exemplos de cenarios em Gherkin
   - Exemplos devem demonstrar a sintaxe: Dado-Quando-Entao
   - Mantenha consistencia entre todos os exemplos
   - Inclua exemplos de diferentes tipos de comportamentos (login, checkout, etc.)

4. **Montar Prompt Personalizado**:
   - Preencha o template com as informacoes do projeto
   - Substitua todos os placeholders `[CAMPO]`
   - Ajuste regras conforme necessidade
   - Enfatize a importancia de linguagem de negocio, nao tecnica

## Output

Retorne o prompt personalizado seguindo a estrutura do template Few-Shot, pronto para ser usado como system prompt ou instrucoes customizadas, focado em Behavior-Driven Development.

## Exemplo de Uso

```
/few-shot-bdd Fluxos de usuario em aplicacao web com Cucumber.js
```

```
/few-shot-bdd Regras de negocio em Python com Behave
```

```
/few-shot-bdd Cenarios de teste E2E com Gherkin
```

## Dicas

- Enfatize a sintaxe Gherkin (Dado-Quando-Entao)
- Use linguagem de negocio, nao tecnica
- Inclua exemplos de step definitions
- Mencione a importancia de cenarios claros e especificos
- Quanto mais especifico o contexto, melhores os exemplos gerados
