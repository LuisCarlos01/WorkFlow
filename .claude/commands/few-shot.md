# Few-Shot Prompting

Aplique a tecnica de **Few-Shot Prompting** usando o template de referencia.

## Referencia

@prompts/Techniques/Prompt-FewShot.md

## Input

**Contexto/Tarefa**: `$ARGUMENTS`

## Processo

1. **Carregar Template**:
   - Leia o arquivo `prompts/Techniques/Prompt-FewShot.md` para obter o template completo
   - Entenda a estrutura: Role, Contexto, Regras, Exemplos, Instrucao Final

2. **Analisar Requisitos**:
   - Identifique o dominio tecnico do usuario
   - Identifique o tipo de projeto/tarefa
   - Identifique padroes especificos necessarios

3. **Criar Exemplos Relevantes**:
   - Gere 2-5 exemplos baseados no contexto fornecido
   - Exemplos devem demonstrar o padrao desejado
   - Mantenha consistencia entre todos os exemplos

4. **Montar Prompt Personalizado**:
   - Preencha o template com as informacoes do projeto
   - Substitua todos os placeholders `[CAMPO]`
   - Ajuste regras conforme necessidade

## Output

Retorne o prompt personalizado seguindo a estrutura do template Few-Shot, pronto para ser usado como system prompt ou instrucoes customizadas.

## Exemplo de Uso

```
/few-shot API REST com Node.js e TypeScript para sistema de pedidos
```

```
/few-shot Componentes React com Tailwind CSS seguindo atomic design
```

```
/few-shot Scripts Python para processamento de dados com Pandas
```

## Dicas

- Quanto mais especifico o contexto, melhores os exemplos gerados
- Inclua linguagens, frameworks e padroes desejados
- Mencione restricoes ou requisitos especiais do projeto
