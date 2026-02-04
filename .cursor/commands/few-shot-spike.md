# Few-Shot: Prototype-First / Spike-Driven Development

Aplique a tecnica de **Few-Shot Prompting** para trabalhar com **Prototype-First / Spike-Driven Development**.

## Referencia

- Template: @prompts/Techniques/Prompt-FewShot.md
- Workflow: @docs/workflows/prototype-first-spike-driven.md

## Input

**Contexto/Tarefa**: `$ARGUMENTS`

## Processo

1. **Carregar Template e Workflow**:
   - Leia o arquivo `prompts/Techniques/Prompt-FewShot.md` para obter o template completo
   - Leia o arquivo `docs/workflows/prototype-first-spike-driven.md` para entender Spike-Driven
   - Entenda a estrutura: Role, Contexto, Regras, Exemplos, Instrucao Final

2. **Analisar Requisitos**:
   - Identifique a incerteza tecnica ou risco a ser explorado
   - Identifique o tipo de spike (technical, performance, architecture, technology)
   - Identifique tempo disponivel (timebox)

3. **Criar Exemplos Relevantes**:
   - Gere 2-5 exemplos de spikes/prototipos rapidos
   - Exemplos devem demonstrar: exploracao → aprendizado → decisao
   - Mantenha consistencia entre todos os exemplos
   - Inclua exemplos de diferentes tipos de spikes

4. **Montar Prompt Personalizado**:
   - Preencha o template com as informacoes do projeto
   - Substitua todos os placeholders `[CAMPO]`
   - Ajuste regras conforme necessidade
   - Enfatize a importancia de codigo descartavel e documentacao de aprendizados

## Output

Retorne o prompt personalizado seguindo a estrutura do template Few-Shot, pronto para ser usado como system prompt ou instrucoes customizadas, focado em Prototype-First / Spike-Driven Development.

## Exemplo de Uso

```
/few-shot-spike Explorar integracao com API externa
```

```
/few-shot-spike Validar performance de biblioteca de graficos
```

```
/few-shot-spike Decidir entre microservicos ou monolito
```

## Dicas

- Enfatize codigo descartavel e rapido
- Mencione importancia de timebox (limite de tempo)
- Inclua exemplos de documentacao de resultados
- Quanto mais especifico o contexto, melhores os exemplos gerados
- Mencione que spikes sao para aprender, nao para produzir
