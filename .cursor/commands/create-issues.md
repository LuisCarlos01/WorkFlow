# Criar Issues no GitHub

Crie issues tecnicas e bem estruturadas no GitHub baseadas no contexto atual do projeto.

## Workflow

### Etapa 1: Entender o Contexto

Pergunte ao usuario OU analise o contexto:
- **De onde vem as issues?**: 
  - Tech Spec existente? (`docs/tasks/[slug]/techspec.md`)
  - Tasks existentes? (`docs/tasks/[slug]/tasks.md`)
  - Analise de codigo atual?
  - Ideias manuais do usuario?

### Etapa 2: Analisar e Propor Issues

Se baseado em Tech Spec/Tasks:
1. Leia o arquivo de tasks ou tech spec
2. Identifique as tarefas que devem virar issues
3. Agrupe por tipo (feature, bug, tech-debt, docs)

Se baseado em codigo:
1. Use `git status` e `git diff` para ver mudancas
2. Identifique debitos tecnicos, melhorias, TODOs
3. Sugira issues para trabalho futuro

### Etapa 3: Gerar Proposta de Issues

Apresente ao usuario:

```
### Issues Propostas:

1. **[feat] Implementar autenticacao OAuth2**
   - Tipo: enhancement
   - Prioridade: alta
   - Labels: ["enhancement", "auth"]
   - Descricao: Adicionar suporte a autenticacao OAuth2...
   
2. **[tech-debt] Refatorar modulo de validacao**
   - Tipo: tech-debt
   - Prioridade: media
   - Labels: ["tech-debt", "refactor"]
   - Descricao: Melhorar estrutura do modulo de validacao...
```

**Pergunte**: "Deseja criar estas issues? (sim/nao/ajustar/selecionar)"

### Etapa 4: Criar Issues

Para cada issue aprovada:

1. Use `issue_write` do GitHub com `method: "create"`:
   ```
   {
     "owner": "[owner]",
     "repo": "[repo]",
     "title": "[titulo-conciso]",
     "body": "[descricao-formatada]",
     "labels": ["label1", "label2"]
   }
   ```

2. Registre o numero da issue criada

3. Continue para a proxima

### Etapa 5: Resumo Final

Apresente um resumo:

```
✓ Issues criadas com sucesso:

- #125: [feat] Implementar autenticacao OAuth2
  URL: https://github.com/[owner]/[repo]/issues/125
  
- #126: [tech-debt] Refatorar modulo de validacao
  URL: https://github.com/[owner]/[repo]/issues/126

Total: 2 issues criadas
```

## Template de Issue

### Para Features (feat)

```markdown
## Objetivo

[Descricao concisa da funcionalidade]

## Requisitos

- [ ] [Requisito 1]
- [ ] [Requisito 2]

## Criterios de Aceitacao

- [ ] [Criterio 1]
- [ ] [Criterio 2]

## Arquivos Relacionados

- `path/to/file.ts`

## Notas Tecnicas

[Contexto tecnico relevante, decisoes de design, etc.]
```

### Para Bugs (fix)

```markdown
## Descricao do Bug

[O que esta acontecendo de errado]

## Comportamento Esperado

[Como deveria funcionar]

## Comportamento Atual

[Como esta funcionando]

## Passos para Reproduzir

1. [Passo 1]
2. [Passo 2]

## Ambiente

- Branch: [branch]
- Versao: [versao]

## Arquivos Relacionados

- `path/to/file.ts`
```

### Para Tech Debt

```markdown
## Problema

[Descricao do debito tecnico]

## Impacto

[Como isso afeta o codigo/performance/manutencao]

## Proposta

[Como resolver/melhorar]

## Prioridade

[alta/media/baixa] - [justificativa]

## Arquivos Relacionados

- `path/to/file.ts`
```

## Tipos de Issues

- **enhancement**: Nova funcionalidade ou melhoria
- **bug**: Correcao de bug
- **documentation**: Documentacao
- **tech-debt**: Debito tecnico ou refatoracao
- **performance**: Otimizacao de performance
- **testing**: Adicionar/melhorar testes
- **chore**: Tarefas de manutencao

## Labels Comuns

**Por tipo:**
- `enhancement`, `bug`, `documentation`, `tech-debt`, `performance`, `testing`, `chore`

**Por prioridade:**
- `priority: high`, `priority: medium`, `priority: low`

**Por area:**
- `api`, `web`, `ui`, `backend`, `frontend`, `infra`, `docs`

## Diretrizes

- **Titulos claros**: Use prefixo de tipo `[feat]`, `[bug]`, `[tech-debt]` seguido de descricao concisa
- **Descricoes objetivas**: Seja tecnico e direto ao ponto
- **Uma issue, uma tarefa**: Nao crie issues muito grandes ou vagas
- **Criterios de aceitacao**: Sempre que possivel, liste criterios claros
- **Referencias cruzadas**: Mencione PRs, outras issues, commits relacionados
- **Idioma**: Portugues brasileiro (pt-br) sem caracteres especiais

## Integracao com Workflow

### A partir de Tech Spec

```
/create-issues docs/tasks/autenticacao/techspec.md
```

Analisa a tech spec e cria issues para cada secao principal.

### A partir de Tasks

```
/create-issues docs/tasks/autenticacao/tasks.md
```

Converte tasks em issues rastreáveis no GitHub.

### Manual

```
/create-issues
```

Modo interativo - o usuario descreve as issues desejadas.

## Parametros

Use `$ARGUMENTS` para especificar:
- Caminho para arquivo (tech spec ou tasks)
- Contexto adicional
- Labels ou milestone especificos

Exemplos:

```
/create-issues docs/tasks/auth/techspec.md
/create-issues milestone:v2.0 label:high-priority
/create-issues 3 issues para melhorar performance do dashboard
```

## Casos de Uso

### 1. Planejamento de Sprint
Crie issues a partir da tech spec para distribuir trabalho entre o time.

### 2. Bug Tracking
Registre bugs encontrados durante testes ou producao.

### 3. Tech Debt Registry
Documente debitos tecnicos identificados durante code review.

### 4. Feature Breakdown
Quebre uma feature grande em issues menores e rastreáveis.

## Seguranca

- NUNCA inclua secrets, API keys ou credenciais nas issues
- NUNCA exponha informacoes sensiveis em repositorios publicos
- SEMPRE revise o conteudo antes de criar issues publicas
