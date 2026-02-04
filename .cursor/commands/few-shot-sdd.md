# Few-Shot: Spec-Driven Development (SDD)

Aplique a tecnica de **Few-Shot Prompting** para trabalhar com **Spec-Driven Development (SDD)**.

## Referencia

- Template: @prompts/Techniques/Prompt-FewShot.md
- Workflow: @docs/workflows/spec-driven-development.md

## Input

**Contexto/Tarefa**: `$ARGUMENTS`

## Processo

1. **Carregar Template e Workflow**:
   - Leia o arquivo `prompts/Techniques/Prompt-FewShot.md` para obter o template completo
   - Leia o arquivo `docs/workflows/spec-driven-development.md` para entender SDD
   - Entenda a estrutura: Role, Contexto, Regras, Exemplos, Instrucao Final

2. **Analisar Requisitos**:
   - Identifique o que precisa ser especificado (feature, API, componente, etc.)
   - Identifique o tipo de projeto/tarefa
   - Identifique padroes especificos necessarios

3. **Criar Exemplos Relevantes de Specs**:
   - Gere 2-5 exemplos de specs baseados no contexto fornecido
   - Exemplos devem demonstrar o padrao de especificacao desejado
   - Mantenha consistencia entre todos os exemplos
   - Inclua exemplos de diferentes tipos (features, APIs, componentes, etc.)

4. **Montar Prompt Personalizado**:
   - Preencha o template com as informacoes do projeto
   - Substitua todos os placeholders `[CAMPO]`
   - Ajuste regras conforme necessidade
   - Enfatize a importancia de escrever spec antes do codigo

## Output

Retorne o prompt personalizado seguindo a estrutura do template Few-Shot, pronto para ser usado como system prompt ou instrucoes customizadas, focado em Spec-Driven Development.

## Exemplo de Uso

```
/few-shot-sdd API REST com Node.js e TypeScript para sistema de pedidos
```

```
/few-shot-sdd Componentes React com TypeScript seguindo atomic design
```

```
/few-shot-sdd Feature de autenticacao com JWT e refresh tokens
```

## Dicas

- Enfatize a importancia de especificar "o que" antes de "como"
- Inclua exemplos de diferentes tipos de specs (features, APIs, componentes)
- Mencione ferramentas como ADRs, OpenAPI, Markdown specs
- Quanto mais especifico o contexto, melhores os exemplos gerados
