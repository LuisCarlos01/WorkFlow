# Pull Request com Issues

Crie uma Pull Request tecnica com issues relacionadas para rastreamento de tarefas especificas.

## Workflow

### Etapa 1: Analisar Contexto

Execute em paralelo:

1. `git status` — mudancas atuais
2. `git diff main...HEAD` — diff completo da branch
3. `git log main..HEAD --oneline` — commits da branch
4. `git branch --show-current` — branch atual
5. Use GitHub tools para buscar issues existentes relacionadas

### Etapa 2: Identificar Tarefas/Issues

Analise os commits e mudancas para identificar:
- **Tarefas completadas**: Funcionalidades implementadas
- **Bugs corrigidos**: Problemas resolvidos
- **Melhorias tecnicas**: Refatoracoes, otimizacoes
- **Pendencias**: Trabalho que ainda precisa ser feito
- **Debitos tecnicos**: Items identificados para futuro

### Etapa 3: Propor Issues

Gere uma lista de issues sugeridas:

```
### Issues Sugeridas:

**A serem criadas:**
1. [feat] Implementar validacao de entrada para formulario X
   - Tipo: enhancement
   - Prioridade: normal
   - Relacionado a: [arquivos/componentes]

2. [tech-debt] Refatorar componente Y para melhor performance
   - Tipo: enhancement
   - Prioridade: baixa
   - Estimativa: [pequena/media/grande]

**Issues existentes a serem referenciadas:**
- #123: Corrigir validacao de email (sera fechada por esta PR)
```

### Etapa 4: Gerar PR

Use o mesmo workflow do `/open-pr` mas adicione:

**Na descricao da PR:**

```markdown
## Issues Relacionadas

Closes #123
Closes #124

## Issues Criadas

- #125: [titulo-da-issue]
- #126: [titulo-da-issue]

## Pendencias

- [ ] Issue #127: [tarefa-futura]
- [ ] Issue #128: [debito-tecnico]
```

### Etapa 5: Confirmar com Usuario

Apresente:
- **PR proposta**: Titulo e descricao
- **Issues a criar**: Lista numerada com detalhes
- **Issues a referenciar**: Issues existentes que serao fechadas ou mencionadas

**Pergunte**: "Deseja criar a PR e as issues sugeridas? (sim/nao/ajustar)"

### Etapa 6: Criar PR e Issues

Apos confirmacao:

1. **Criar issues primeiro** (uma por vez):
   ```
   Use GitHub tool: issue_write com method: "create"
   - title: [titulo-conciso]
   - body: [descricao-detalhada]
   - labels: ["enhancement", "tech-debt", etc.]
   ```

2. **Criar PR** referenciando as issues criadas:
   ```
   Use GitHub tool: create_pull_request
   - Inclua referencias as issues na descricao (Closes #N, Relates to #N)
   ```

3. **Retornar resumo**:
   ```
   ✓ PR criada: [URL]
   ✓ Issues criadas: #125, #126, #127
   ✓ Issues referenciadas: #123, #124
   ```

## Tipos de Issues

**enhancement**: Nova funcionalidade ou melhoria
**bug**: Correcao de bug
**documentation**: Documentacao
**tech-debt**: Debito tecnico
**refactor**: Refatoracao
**performance**: Otimizacao de performance

## Template de Issue

```markdown
## Descricao

[Descricao concisa da tarefa/problema]

## Contexto

[Contexto tecnico relevante]

## Criterios de Aceitacao

- [ ] [Criterio 1]
- [ ] [Criterio 2]

## Arquivos/Componentes Relacionados

- `path/to/file.ts`
- `path/to/component.tsx`

## Relacionado a

PR #[numero-da-pr]
```

## Diretrizes

- **Issues objetivas**: Uma issue = uma tarefa clara
- **Titulos descritivos**: Devem comunicar claramente o objetivo
- **Labels apropriadas**: Use labels para categorizar
- **Referencias cruzadas**: Conecte PR com issues e vice-versa
- **Idioma**: Portugues brasileiro (pt-br) sem caracteres especiais
- **Prioridade**: Crie issues apenas se fizerem sentido (nao crie issues triviais)

## Parametros

Use `$ARGUMENTS` para contexto. Exemplo:

```
/pr-with-issues epic ABC-123 - implementacao de autenticacao
```

## Casos de Uso

### Quando usar `/open-pr`:
- PR simples, direta, sem necessidade de issues adicionais
- Todas as mudancas estao completas e nao ha trabalho futuro

### Quando usar `/pr-with-issues`:
- PR grande que resolve multiplas issues
- PR que identifica debitos tecnicos ou trabalho futuro
- Necessidade de rastrear tarefas especificas relacionadas a PR

## Seguranca

- NUNCA crie issues publicas com informacoes sensiveis
- SEMPRE revise o conteudo antes de criar issues/PR
- NUNCA referencie secrets ou credenciais
