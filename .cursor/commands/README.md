# Comandos Cursor - WorkFlow

Comandos personalizados para automatizar fluxos de trabalho no desenvolvimento com IA.

## Como Usar

No Cursor, digite `/` no campo de chat para ver todos os comandos disponiveis. Os comandos sao automaticamente detectados desta pasta.

## Comandos Disponiveis

### Integracao GitHub

| Comando | Descricao | Uso |
|---------|-----------|-----|
| `/open-pr` | Cria PR tecnica e objetiva | `/open-pr [contexto]` |
| `/pr-with-issues` | Cria PR com issues relacionadas | `/pr-with-issues [contexto]` |
| `/create-issues` | Cria issues no GitHub | `/create-issues [fonte]` |

**Documentacao detalhada:** [github-commands-guide.md](./github-commands-guide.md)

---

## Estrutura de um Comando

Comandos sao arquivos Markdown (`.md`) com:

1. **Nome do arquivo**: Define o nome do comando (ex: `open-pr.md` → `/open-pr`)
2. **Conteudo**: Instrucoes em Markdown descrevendo o que o comando deve fazer
3. **Parametros**: Use `$ARGUMENTS` para capturar parametros adicionais

### Exemplo Basico

```markdown
# Meu Comando

Descricao breve do que o comando faz.

## Workflow

1. Passo 1
2. Passo 2
3. Passo 3

## Parametros

Use `$ARGUMENTS` para contexto adicional.
```

---

## Boas Praticas

### Nomenclatura

- Use nomes descritivos e em kebab-case
- Evite nomes muito longos
- Exemplos: `open-pr`, `create-issues`, `run-tests`

### Conteudo

- **Seja claro**: Descreva exatamente o que o comando deve fazer
- **Seja estruturado**: Use secoes e listas
- **Seja completo**: Inclua validacoes e tratamento de erros
- **Seja seguro**: Sempre valide antes de executar acoes destrutivas

### Parametros

- Use `$ARGUMENTS` para capturar tudo apos o nome do comando
- Documente claramente como usar parametros
- Forneca exemplos de uso

---

## Criando Novos Comandos

### Passo 1: Criar Arquivo

```bash
# Na raiz do projeto
touch .cursor/commands/meu-comando.md
```

### Passo 2: Definir Estrutura

```markdown
# Meu Comando

## Visao Geral
[Descricao do comando]

## Workflow

### Etapa 1: [Nome]
[Descricao]

### Etapa 2: [Nome]
[Descricao]

## Parametros

$ARGUMENTS - [Explicacao]

## Exemplos

```bash
/meu-comando
/meu-comando parametro1 parametro2
```

## Diretrizes

- [Regra 1]
- [Regra 2]
```

### Passo 3: Testar

1. Reinicie o Cursor (ou recarregue a janela)
2. Digite `/` no chat
3. Seu comando deve aparecer na lista
4. Teste com diferentes parametros

---

## Comandos por Categoria

### GitHub Integration
- `open-pr.md` - Criar Pull Requests
- `pr-with-issues.md` - PR com issues relacionadas
- `create-issues.md` - Criar issues estruturadas

### (Adicione mais categorias conforme necessario)

---

## Documentacao de Referencia

- **Comandos Context**: [commands-context.md](./commands-context.md)
- **Guia GitHub**: [github-commands-guide.md](./github-commands-guide.md)

---

## Atualizacoes

Para melhorar ou corrigir comandos existentes:

1. Edite o arquivo `.md` correspondente
2. Teste as mudancas
3. Documente alteracoes significativas
4. Considere criar uma issue ou PR se for uma mudanca importante

---

## Suporte

Para duvidas ou problemas:

1. Consulte a [documentacao oficial do Cursor](https://docs.cursor.com/)
2. Veja exemplos em [commands-context.md](./commands-context.md)
3. Abra uma issue no repositorio WorkFlow
