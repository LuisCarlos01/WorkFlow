# Guia Rapido - Comandos GitHub

Comandos para integracao direta com GitHub: criar PRs e issues de forma automatizada, tecnica e objetiva.

## Comandos Disponiveis

### 1. `/open-pr` - Pull Request Simples

**Quando usar:**
- PR direta, completa, sem necessidade de issues adicionais
- Todas as mudancas estao finalizadas
- Nao ha trabalho futuro ou debitos tecnicos identificados

**Como usar:**

```bash
# Uso basico
/open-pr

# Com contexto adicional
/open-pr relacionado ao ticket ABC-123
/open-pr implementa validacao de formularios
```

**O que acontece:**
1. Analisa automaticamente git status, diff e commits
2. Gera titulo e descricao tecnica da PR
3. Apresenta proposta para sua aprovacao
4. Cria a PR no GitHub apos confirmacao
5. Retorna a URL da PR criada

---

### 2. `/pr-with-issues` - Pull Request + Issues

**Quando usar:**
- PR grande que resolve multiplas tarefas
- Identifica debitos tecnicos ou melhorias futuras
- Necessita rastrear trabalho pendente relacionado

**Como usar:**

```bash
# Uso basico
/pr-with-issues

# Com contexto de epic ou milestone
/pr-with-issues epic AUTH-001 autenticacao OAuth2
/pr-with-issues milestone v2.0
```

**O que acontece:**
1. Analisa mudancas e identifica tarefas/debitos
2. Propoe issues a serem criadas (features, tech-debt, bugs)
3. Gera descricao da PR com referencias as issues
4. Apresenta proposta completa para aprovacao
5. Cria issues primeiro, depois a PR com referencias
6. Retorna URLs de PR e issues criadas

---

### 3. `/create-issues` - Criar Issues

**Quando usar:**
- Converter Tech Spec ou Tasks em issues rastreáveis
- Registrar debitos tecnicos identificados
- Planejar sprint com issues no GitHub
- Documentar bugs encontrados

**Como usar:**

```bash
# Modo interativo (assistido)
/create-issues

# A partir de Tech Spec
/create-issues docs/tasks/auth/techspec.md

# A partir de Tasks
/create-issues docs/tasks/dashboard/tasks.md

# Com contexto especifico
/create-issues 3 issues de performance para o dashboard
/create-issues bugs encontrados durante testes de integracao
```

**O que acontece:**
1. Identifica fonte das issues (spec, tasks, codigo, manual)
2. Analisa e propoe issues estruturadas por tipo
3. Apresenta proposta com titulos, descricoes e labels
4. Cria issues no GitHub apos confirmacao
5. Retorna lista com numeros e URLs das issues criadas

---

## Fluxo de Trabalho Recomendado

### Cenario 1: Feature Completa e Simples

```
1. Desenvolva a feature
2. Faça commits seguindo Conventional Commits
3. /open-pr
4. Revise e aprove a proposta
5. ✓ PR criada no GitHub
```

### Cenario 2: Feature Grande com Pendencias

```
1. Desenvolva a feature principal
2. Durante desenvolvimento, identifique debitos/melhorias
3. /pr-with-issues
4. Revise proposta de PR e issues
5. ✓ PR criada + Issues criadas para trabalho futuro
```

### Cenario 3: Planejamento de Sprint

```
1. Crie Tech Spec da feature
2. /create-issues docs/tasks/feature-x/techspec.md
3. Revise e aprove issues propostas
4. ✓ Issues criadas no GitHub para distribuir no time
```

### Cenario 4: Bug Tracking

```
1. Identifique bugs durante testes
2. /create-issues bugs encontrados em testes de checkout
3. Descreva os bugs
4. ✓ Issues de bug criadas para rastreamento
```

---

## Templates Automaticos

### Template de PR

```markdown
## Resumo
[Objetivo principal das mudancas]

## Mudancas Principais
- [Lista objetiva de mudancas]
- [Arquivos/componentes afetados]

## Tipo de Mudanca
- [x] Nova funcionalidade (feat)
- [ ] Correcao de bug (fix)
- [ ] Refatoracao (refactor)

## Checklist
- [ ] Codigo segue padroes do projeto
- [ ] Testes atualizados
- [ ] Documentacao atualizada
```

### Template de Issue - Feature

```markdown
## Objetivo
[Descricao da funcionalidade]

## Requisitos
- [ ] Requisito 1
- [ ] Requisito 2

## Criterios de Aceitacao
- [ ] Criterio 1
- [ ] Criterio 2

## Arquivos Relacionados
- `path/to/file.ts`
```

### Template de Issue - Bug

```markdown
## Descricao do Bug
[O que esta errado]

## Comportamento Esperado
[Como deveria funcionar]

## Comportamento Atual
[Como esta funcionando]

## Passos para Reproduzir
1. Passo 1
2. Passo 2
```

### Template de Issue - Tech Debt

```markdown
## Problema
[Descricao do debito tecnico]

## Impacto
[Como afeta manutencao/performance]

## Proposta
[Como resolver]

## Prioridade
[alta/media/baixa] - [justificativa]
```

---

## Tipos e Labels

### Tipos de Mudanca (PR/Issues)

| Tipo | Quando usar | Label |
|------|-------------|-------|
| `feat` | Nova funcionalidade | `enhancement` |
| `fix` | Correcao de bug | `bug` |
| `refactor` | Refatoracao de codigo | `tech-debt` |
| `docs` | Documentacao | `documentation` |
| `perf` | Otimizacao | `performance` |
| `test` | Testes | `testing` |
| `chore` | Manutencao | `chore` |

### Labels por Area

- `api`, `web`, `ui`, `backend`, `frontend`, `infra`, `docs`

### Labels de Prioridade

- `priority: high`, `priority: medium`, `priority: low`

---

## Dicas e Boas Praticas

### Para PRs

✅ **Faça:**
- PRs pequenas e focadas (1 objetivo principal)
- Titulos seguindo Conventional Commits
- Descricoes tecnicas e objetivas
- Liste arquivos/componentes chave afetados
- Adicione checklist relevante

❌ **Evite:**
- PRs gigantes com multiplos objetivos
- Titulos vagos ("fix stuff", "updates")
- Descricoes longas e subjetivas
- Expor informacoes sensiveis

### Para Issues

✅ **Faça:**
- Uma issue = uma tarefa clara
- Titulos descritivos e objetivos
- Criterios de aceitacao quando possivel
- Referencias cruzadas (PRs, outras issues)
- Labels apropriadas

❌ **Evite:**
- Issues vagas ou muito grandes
- Titulos genericos
- Falta de contexto tecnico
- Expor secrets ou credenciais

---

## Troubleshooting

### PR nao foi criada

**Problema:** Erro ao criar PR no GitHub

**Solucoes:**
1. Verifique se a branch foi pushed: `git push -u origin HEAD`
2. Verifique permissoes no repositorio GitHub
3. Confirme que nao existe PR aberta para a branch
4. Verifique autenticacao do GitHub MCP

### Issues nao foram criadas

**Problema:** Erro ao criar issues no GitHub

**Solucoes:**
1. Verifique permissoes no repositorio
2. Confirme que os labels existem no repositorio
3. Verifique se o milestone existe (se especificado)
4. Valide autenticacao do GitHub MCP

### Commits nao aparecem na PR

**Problema:** PR criada mas sem commits

**Solucoes:**
1. Certifique-se que a branch foi pushed
2. Verifique se a branch base esta correta
3. Confirme que ha commits entre base e head

---

## Referencias

- **Conventional Commits**: https://www.conventionalcommits.org/pt-br/
- **GitHub CLI**: https://cli.github.com/
- **GitHub API**: https://docs.github.com/rest

## Suporte

Para issues ou melhorias nestes comandos:
1. Abra uma issue no repositorio WorkFlow
2. Use a label `commands` ou `github-integration`
3. Descreva o problema ou sugestao
