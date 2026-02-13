# Abrir Pull Request

Crie uma Pull Request tecnica, objetiva e concisa para as mudancas atuais no repositorio.

## Workflow

### Etapa 1: Analisar Contexto

Execute em paralelo para entender o estado atual:

1. `git status` — para ver todas as mudancas
2. `git diff main...HEAD` — para ver o diff completo da branch
3. `git log main..HEAD --oneline` — para ver os commits da branch
4. `git branch --show-current` — para identificar a branch atual
5. Use GitHub tools para verificar se ja existe PR para esta branch

### Etapa 2: Analisar Commits e Mudancas

Agrupe os commits por tipo (feat, fix, docs, etc.) e identifique:
- **Funcionalidades adicionadas**
- **Bugs corrigidos** 
- **Refatoracoes realizadas**
- **Documentacao atualizada**
- **Testes adicionados/atualizados**

### Etapa 3: Gerar Titulo e Descricao da PR

**Titulo**: Use o formato Conventional Commits baseado no commit principal:
- `feat: adiciona [funcionalidade]`
- `fix: corrige [problema]`
- `refactor: refatora [componente]`

**Descricao**: Seja tecnico, objetivo e conciso. Use este template:

```markdown
## Resumo

[1-2 frases explicando o objetivo principal das mudancas]

## Mudancas Principais

- [Lista objetiva das mudancas mais importantes]
- [Mencione arquivos/componentes chave afetados]

## Tipo de Mudanca

- [ ] Nova funcionalidade (feat)
- [ ] Correcao de bug (fix)
- [ ] Refatoracao (refactor)
- [ ] Documentacao (docs)
- [ ] Outro: [especificar]

## Checklist

- [ ] Codigo segue os padroes do projeto
- [ ] Testes adicionados/atualizados (se aplicavel)
- [ ] Documentacao atualizada (se aplicavel)
- [ ] Sem conflitos com a branch base
```

### Etapa 4: Apresentar Proposta ao Usuario

Mostre ao usuario:
- **Branch**: [nome-da-branch]
- **Base**: [branch-destino] (geralmente `main` ou `master`)
- **Titulo**: [titulo-proposto]
- **Descricao**: [descricao-gerada]

**Pergunte**: "Deseja criar a PR com estas informacoes? (sim/nao/ajustar)"

### Etapa 5: Criar a PR

Apos confirmacao:

1. Verifique se a branch esta atualizada: `git push -u origin HEAD` (se necessario)
2. Use a ferramenta GitHub `create_pull_request` com:
   - `owner`: dono do repositorio (obtido do remote)
   - `repo`: nome do repositorio (obtido do remote)
   - `title`: titulo aprovado
   - `body`: descricao aprovada
   - `head`: branch atual
   - `base`: branch destino (padrao: `main`)
3. Retorne a URL da PR criada

### Etapa 6: Opcoes Adicionais

Pergunte ao usuario se deseja:
- Adicionar labels (feat, fix, docs, etc.)
- Adicionar revisores
- Marcar como draft
- Criar issues relacionadas (use `/pr-with-issues` para workflow completo)

## Diretrizes

- **Seja conciso**: PRs devem ser diretas ao ponto
- **Seja tecnico**: Foque em "o que" mudou, nao em detalhes triviais
- **Seja objetivo**: Use listas e bullets, evite paragrrafos longos
- **Idioma**: Titulo e descricao em portugues brasileiro (pt-br)
- **Sem caracteres especiais**: Evite acentos se houver problemas de encoding

## Seguranca

- NUNCA exponha secrets ou API keys na descricao da PR
- NUNCA force push sem confirmacao explicita
- SEMPRE verifique se a branch esta sincronizada antes de criar a PR

## Parametros

Use `$ARGUMENTS` para contexto adicional opcional. Exemplo:

```
/open-pr relacionado ao ticket ABC-123
```

Isso sera incluido na descricao da PR automaticamente.
