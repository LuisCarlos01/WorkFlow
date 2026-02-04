# Few-Shot: Trunk-Based Development

Aplique a tecnica de **Few-Shot Prompting** para trabalhar com **Trunk-Based Development**.

## Referencia

- Template: @prompts/Techniques/Prompt-FewShot.md
- Workflow: @docs/workflows/trunk-based-development.md

## Input

**Contexto/Tarefa**: `$ARGUMENTS`

## Processo

1. **Carregar Template e Workflow**:
   - Leia o arquivo `prompts/Techniques/Prompt-FewShot.md` para obter o template completo
   - Leia o arquivo `docs/workflows/trunk-based-development.md` para entender Trunk-Based
   - Entenda a estrutura: Role, Contexto, Regras, Exemplos, Instrucao Final

2. **Analisar Requisitos**:
   - Identifique o tipo de projeto/tarefa
   - Identifique estrategia de branching atual
   - Identifique ferramentas de CI/CD disponiveis

3. **Criar Exemplos Relevantes**:
   - Gere 2-5 exemplos de commits pequenos e frequentes
   - Exemplos devem demonstrar: branch curta → commits pequenos → merge rapido
   - Mantenha consistencia entre todos os exemplos
   - Inclua exemplos de feature flags quando necessario

4. **Montar Prompt Personalizado**:
   - Preencha o template com as informacoes do projeto
   - Substitua todos os placeholders `[CAMPO]`
   - Ajuste regras conforme necessidade
   - Enfatize a importancia de commits pequenos e branches curtas

## Output

Retorne o prompt personalizado seguindo a estrutura do template Few-Shot, pronto para ser usado como system prompt ou instrucoes customizadas, focado em Trunk-Based Development.

## Exemplo de Uso

```
/few-shot-trunk Projeto Node.js com deploy continuo
```

```
/few-shot-trunk Time pequeno trabalhando em main
```

```
/few-shot-trunk Feature flags para features incompletas
```

## Dicas

- Enfatize commits pequenos e frequentes
- Mencione importancia de branches curtas (< 1 dia)
- Inclua exemplos de feature flags
- Quanto mais especifico o contexto, melhores os exemplos gerados
- Mencione CI/CD e testes automaticos
