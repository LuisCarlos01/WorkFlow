# Few-Shot: AI-First / Prompt-Driven Workflow

Aplique a tecnica de **Few-Shot Prompting** para trabalhar com **AI-First / Prompt-Driven Workflow**.

## Referencia

- Template: @prompts/Techniques/Prompt-FewShot.md
- Workflow: @docs/workflows/ai-first-prompt-driven.md

## Input

**Contexto/Tarefa**: `$ARGUMENTS`

## Processo

1. **Carregar Template e Workflow**:
   - Leia o arquivo `prompts/Techniques/Prompt-FewShot.md` para obter o template completo
   - Leia o arquivo `docs/workflows/ai-first-prompt-driven.md` para entender AI-First
   - Entenda a estrutura: Role, Contexto, Regras, Exemplos, Instrucao Final

2. **Analisar Requisitos**:
   - Identifique o que precisa ser implementado
   - Identifique regras e padroes do projeto disponiveis
   - Identifique contexto necessario para IA

3. **Criar Exemplos Relevantes**:
   - Gere 2-5 exemplos de prompts eficazes para IA
   - Exemplos devem demonstrar: especificacao clara → contexto → codigo gerado → revisao
   - Mantenha consistencia entre todos os exemplos
   - Inclua exemplos de diferentes tipos de tarefas (features, refatoracao, testes, docs)

4. **Montar Prompt Personalizado**:
   - Preencha o template com as informacoes do projeto
   - Substitua todos os placeholders `[CAMPO]`
   - Ajuste regras conforme necessidade
   - Enfatize a importancia de especificacao clara, contexto rico e revisao humana

## Output

Retorne o prompt personalizado seguindo a estrutura do template Few-Shot, pronto para ser usado como system prompt ou instrucoes customizadas, focado em AI-First / Prompt-Driven Workflow.

## Exemplo de Uso

```
/few-shot-ai-first API REST com Node.js e regras do projeto
```

```
/few-shot-ai-first Componentes React seguindo atomic design
```

```
/few-shot-ai-first Refatoracao de codigo legado com TypeScript
```

## Dicas

- Enfatize especificacao clara e detalhada
- Mencione importancia de contexto rico (regras, padroes, exemplos)
- Inclua exemplos de revisao humana sempre
- Quanto mais especifico o contexto, melhores os resultados
- Mencione ferramentas como Rules, Tech Specs, Context
