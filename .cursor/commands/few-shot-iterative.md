# Few-Shot: Iterative / Incremental Development

Aplique a tecnica de **Few-Shot Prompting** para trabalhar com **Iterative / Incremental Development**.

## Referencia

- Template: @prompts/Techniques/Prompt-FewShot.md
- Workflow: @docs/workflows/iterative-incremental-development.md

## Input

**Contexto/Tarefa**: `$ARGUMENTS`

## Processo

1. **Carregar Template e Workflow**:
   - Leia o arquivo `prompts/Techniques/Prompt-FewShot.md` para obter o template completo
   - Leia o arquivo `docs/workflows/iterative-incremental-development.md` para entender Iterative Development
   - Entenda a estrutura: Role, Contexto, Regras, Exemplos, Instrucao Final

2. **Analisar Requisitos**:
   - Identifique o tipo de produto/projeto
   - Identifique objetivos da iteracao atual
   - Identifique como coletar feedback

3. **Criar Exemplos Relevantes**:
   - Gere 2-5 exemplos de iteracoes incrementais
   - Exemplos devem demonstrar: MVP → Feedback → Ajuste → Proxima Iteracao
   - Mantenha consistencia entre todos os exemplos
   - Inclua exemplos de diferentes tipos de iteracoes (features, melhorias, correcoes)

4. **Montar Prompt Personalizado**:
   - Preencha o template com as informacoes do projeto
   - Substitua todos os placeholders `[CAMPO]`
   - Ajuste regras conforme necessidade
   - Enfatize a importancia de fatias verticais e feedback rapido

## Output

Retorne o prompt personalizado seguindo a estrutura do template Few-Shot, pronto para ser usado como system prompt ou instrucoes customizadas, focado em Iterative / Incremental Development.

## Exemplo de Uso

```
/few-shot-iterative MVP de e-commerce com feedback de usuarios
```

```
/few-shot-iterative Feature de autenticacao em iteracoes incrementais
```

```
/few-shot-iterative Startup validando produto com usuarios
```

## Dicas

- Enfatize fatias verticais (feature completa), nao horizontais (camadas)
- Mencione importancia de MVP em cada iteracao
- Inclua exemplos de como coletar e usar feedback
- Quanto mais especifico o contexto, melhores os exemplos gerados
- Mencione user stories e criterios de aceitacao
