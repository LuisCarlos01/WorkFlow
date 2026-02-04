# Few-Shot: Pragmatic / Opportunistic Workflow

Aplique a tecnica de **Few-Shot Prompting** para trabalhar com **Pragmatic / Opportunistic Workflow**.

## Referencia

- Template: @prompts/Techniques/Prompt-FewShot.md
- Workflow: @docs/workflows/pragmatic-opportunistic.md

## Input

**Contexto/Tarefa**: `$ARGUMENTS`

## Processo

1. **Carregar Template e Workflow**:
   - Leia o arquivo `prompts/Techniques/Prompt-FewShot.md` para obter o template completo
   - Leia o arquivo `docs/workflows/pragmatic-opportunistic.md` para entender Pragmatic Workflow
   - Entenda a estrutura: Role, Contexto, Regras, Exemplos, Instrucao Final

2. **Analisar Requisitos**:
   - Identifique a situacao atual (criticidade, complexidade, urgencia, risco)
   - Identifique tecnicas disponiveis (SDD, TDD, BDD, AI-First, etc.)
   - Identifique o contexto do projeto

3. **Criar Exemplos Relevantes**:
   - Gere 2-5 exemplos de escolha de tecnica baseada em situacao
   - Exemplos devem demonstrar: situacao → tecnica apropriada → execucao
   - Mantenha consistencia entre todos os exemplos
   - Inclua exemplos de diferentes situacoes (bug critico, feature nova, refatoracao, etc.)

4. **Montar Prompt Personalizado**:
   - Preencha o template com as informacoes do projeto
   - Substitua todos os placeholders `[CAMPO]`
   - Ajuste regras conforme necessidade
   - Enfatize consciencia situacional e alternancia inteligente entre tecnicas

## Output

Retorne o prompt personalizado seguindo a estrutura do template Few-Shot, pronto para ser usado como system prompt ou instrucoes customizadas, focado em Pragmatic / Opportunistic Workflow.

## Exemplo de Uso

```
/few-shot-pragmatic Desenvolvedor solo em startup rapida
```

```
/few-shot-pragmatic Projeto pequeno com contexto variado
```

```
/few-shot-pragmatic Alternancia entre tecnicas conforme necessidade
```

## Dicas

- Enfatize consciencia situacional (criticidade, complexidade, urgencia, risco)
- Mencione importancia de ter "menu" de tecnicas disponiveis
- Inclua exemplos de matriz de decisao (quando usar cada tecnica)
- Quanto mais especifico o contexto, melhores os exemplos gerados
- Mencione que pragmatismo nao e bagunca, e escolha consciente
