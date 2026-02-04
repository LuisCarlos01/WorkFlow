# Few-Shot: Test-Driven Development (TDD)

Aplique a tecnica de **Few-Shot Prompting** para trabalhar com **Test-Driven Development (TDD)**.

## Referencia

- Template: @prompts/Techniques/Prompt-FewShot.md
- Workflow: @docs/workflows/test-driven-development.md

## Input

**Contexto/Tarefa**: `$ARGUMENTS`

## Processo

1. **Carregar Template e Workflow**:
   - Leia o arquivo `prompts/Techniques/Prompt-FewShot.md` para obter o template completo
   - Leia o arquivo `docs/workflows/test-driven-development.md` para entender TDD
   - Entenda a estrutura: Role, Contexto, Regras, Exemplos, Instrucao Final

2. **Analisar Requisitos**:
   - Identifique o que precisa ser testado (funcao, classe, componente, etc.)
   - Identifique o tipo de projeto/tarefa
   - Identifique framework de testes (Jest, Vitest, pytest, etc.)

3. **Criar Exemplos Relevantes de TDD**:
   - Gere 2-5 exemplos demonstrando o ciclo Red-Green-Refactor
   - Exemplos devem mostrar: teste que falha → codigo minimo → refatoracao
   - Mantenha consistencia entre todos os exemplos
   - Inclua exemplos de diferentes tipos de testes (unitarios, integracao)

4. **Montar Prompt Personalizado**:
   - Preencha o template com as informacoes do projeto
   - Substitua todos os placeholders `[CAMPO]`
   - Ajuste regras conforme necessidade
   - Enfatize a importancia de escrever teste antes do codigo

## Output

Retorne o prompt personalizado seguindo a estrutura do template Few-Shot, pronto para ser usado como system prompt ou instrucoes customizadas, focado em Test-Driven Development.

## Exemplo de Uso

```
/few-shot-tdd Funcoes utilitarias em TypeScript com Jest
```

```
/few-shot-tdd Servicos backend em Python com pytest
```

```
/few-shot-tdd Componentes React com Vitest e Testing Library
```

## Dicas

- Enfatize o ciclo Red-Green-Refactor
- Inclua exemplos de diferentes tipos de testes
- Mencione padroes como AAA (Arrange-Act-Assert)
- Quanto mais especifico o contexto, melhores os exemplos gerados
- Inclua exemplos de testes de casos de erro tambem
