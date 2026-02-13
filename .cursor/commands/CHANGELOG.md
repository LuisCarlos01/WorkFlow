# Changelog - Comandos GitHub

Historico de mudancas nos comandos de integracao GitHub.

## [2026-02-12] - Comandos GitHub Criados

### Adicionado

#### Comandos Novos

1. **`/open-pr`** - Criar Pull Request
   - Analisa automaticamente mudancas e commits
   - Gera titulo e descricao tecnica
   - Integra diretamente com GitHub API
   - Cria PR apos confirmacao do usuario

2. **`/pr-with-issues`** - Pull Request com Issues
   - Analisa mudancas e identifica trabalho pendente
   - Propoe issues para features, bugs e tech-debt
   - Cria issues primeiro, depois PR com referencias
   - Mantem rastreabilidade entre PR e issues

3. **`/create-issues`** - Criar Issues no GitHub
   - Suporta multiplas fontes (Tech Spec, Tasks, codigo, manual)
   - Templates automaticos por tipo (feature, bug, tech-debt)
   - Labels e prioridades configuraveis
   - Modo interativo para criacao assistida

#### Documentacao

- `README.md` - Visao geral dos comandos
- `github-commands-guide.md` - Guia detalhado de uso
- `EXAMPLE.md` - Exemplos praticos de uso
- `CHANGELOG.md` - Este arquivo

#### Atualizacoes em Arquivos Existentes

- `commands-context.md` - Adicionada secao com novos comandos
- `CLAUDE.md` (raiz) - Atualizada lista de comandos disponiveis

### Caracteristicas

#### Integracao GitHub

- Uso direto da GitHub API via MCP
- Criacao automatizada de PRs e issues
- Validacao antes de executar acoes
- Suporte a labels, milestones e revisores
- Referencias cruzadas automaticas

#### Templates

- Template de PR tecnica e objetiva
- Template de issue para features
- Template de issue para bugs
- Template de issue para tech-debt

#### Fluxo de Trabalho

- Analise automatica de git (status, diff, log)
- Proposta interativa antes de executar
- Confirmacao do usuario obrigatoria
- Relatorios detalhados apos execucao

#### Seguranca

- Validacao de permissoes
- Nunca expor secrets ou credenciais
- Verificacao de branch antes de push
- Confirmacao para acoes destrutivas

### Convencoes

#### Nomenclatura

- Comandos em kebab-case (`open-pr`, `create-issues`)
- Arquivos Markdown (`.md`)
- Parametros via `$ARGUMENTS`

#### Idioma

- Comandos em portugues brasileiro (pt-br)
- Sem caracteres especiais em commits/PRs
- Documentacao em pt-br

#### Padroes

- Conventional Commits para titulos de PR
- Labels padronizadas (enhancement, bug, tech-debt, etc.)
- Structured templates para issues

### Integracao com Workflow Existente

Os novos comandos complementam o workflow Spec-Driven Development:

```
1. Ideia → PRD → Tech Spec → Tasks (workflow existente)
2. Codigo → Implementacao (workflow existente)
3. GitHub → /open-pr ou /pr-with-issues (NOVO)
4. Issues → /create-issues (NOVO)
```

### Casos de Uso

1. **PR Simples**: Feature completa → `/open-pr`
2. **PR Complexa**: Feature com pendencias → `/pr-with-issues`
3. **Planejamento**: Tech Spec → `/create-issues` → distribuir trabalho
4. **Bug Tracking**: Bugs encontrados → `/create-issues` → rastrear

### Proximos Passos

Melhorias futuras sugeridas:

- [ ] Comando `/update-pr` para atualizar PRs existentes
- [ ] Comando `/link-pr-issues` para vincular PR a issues existentes
- [ ] Comando `/close-issues` para fechar multiplas issues
- [ ] Integracao com milestones do GitHub
- [ ] Suporte a draft PRs
- [ ] Auto-assign de revisores baseado em CODEOWNERS
- [ ] Templates customizaveis por repositorio
- [ ] Integracao com GitHub Projects

### Referencias

- **GitHub MCP**: Integracao via Model Context Protocol
- **Conventional Commits**: https://www.conventionalcommits.org/
- **Cursor Commands**: https://docs.cursor.com/
