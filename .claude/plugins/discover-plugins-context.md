> **Documentation Index**
> Fetch the complete documentation index at: https://code.claude.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

---

# Descubra e Instale Plugins Pré-construídos Através de Marketplaces

> Encontre e instale plugins de marketplaces para estender Claude Code com novos comandos, agentes e capacidades.

Plugins estendem Claude Code com comandos personalizados, agentes, hooks e servidores MCP. Marketplaces de plugins são catálogos que ajudam você a descobrir e instalar essas extensões sem construí-las você mesmo.

Procurando criar e distribuir seu próprio marketplace? Veja Criar e distribuir um marketplace de plugins.

---

## Como os Marketplaces Funcionam

Um marketplace é um catálogo de plugins que alguém criou e compartilhou. Usar um marketplace é um processo de duas etapas:

**Passo 1 — Adicione o marketplace:**

Isso registra o catálogo com Claude Code para que você possa navegar pelo que está disponível. Nenhum plugin é instalado ainda.

**Passo 2 — Instale plugins individuais:**

Navegue pelo catálogo e instale os plugins que você deseja.

> **Analogia:** Pense nisso como adicionar uma loja de aplicativos: adicionar a loja oferece acesso para navegar sua coleção, mas você ainda escolhe quais aplicativos baixar individualmente.

---

## Marketplace Oficial da Anthropic

O marketplace oficial da Anthropic (`claude-plugins-official`) está automaticamente disponível quando você inicia Claude Code. Execute `/plugin` e vá para a aba **Discover** para navegar pelo que está disponível.

Para instalar um plugin do marketplace oficial:

```
/plugin install plugin-name@claude-plugins-official
```

> **Nota:** O marketplace oficial é mantido pela Anthropic. Para distribuir seus próprios plugins, crie seu próprio marketplace e compartilhe com usuários.

### Categorias de plugins do marketplace oficial

#### Inteligência de código

Plugins de inteligência de código ajudam Claude a entender sua base de código mais profundamente. Com esses plugins instalados, Claude pode pular para definições, encontrar referências e ver erros de tipo imediatamente após edições. Esses plugins usam o [Language Server Protocol](https://microsoft.github.io/language-server-protocol/) (LSP), a mesma tecnologia que alimenta a inteligência de código do VS Code.

Esses plugins requerem que o binário do language server esteja instalado em seu sistema. Se você já tiver um language server instalado, Claude pode solicitar que você instale o plugin correspondente quando abrir um projeto.

| Linguagem | Plugin | Binário necessário |
| :--- | :--- | :--- |
| C/C++ | `clangd-lsp` | `clangd` |
| C# | `csharp-lsp` | `csharp-ls` |
| Go | `gopls-lsp` | `gopls` |
| Java | `jdtls-lsp` | `jdtls` |
| Lua | `lua-lsp` | `lua-language-server` |
| PHP | `php-lsp` | `intelephense` |
| Python | `pyright-lsp` | `pyright-langserver` |
| Rust | `rust-analyzer-lsp` | `rust-analyzer` |
| Swift | `swift-lsp` | `sourcekit-lsp` |
| TypeScript | `typescript-lsp` | `typescript-language-server` |

Você também pode criar seu próprio plugin LSP para outras linguagens.

> **Nota:** Se você vir `Executable not found in $PATH` na aba Errors do `/plugin` após instalar um plugin, instale o binário necessário da tabela acima.

#### Integrações externas

Esses plugins agrupam servidores MCP pré-configurados para que você possa conectar Claude a serviços externos sem configuração manual:

- **Controle de versão:** `github`, `gitlab`
- **Gerenciamento de projetos:** `atlassian` (Jira/Confluence), `asana`, `linear`, `notion`
- **Design:** `figma`
- **Infraestrutura:** `vercel`, `firebase`, `supabase`
- **Comunicação:** `slack`
- **Monitoramento:** `sentry`

#### Fluxos de trabalho de desenvolvimento

Plugins que adicionam comandos e agentes para tarefas comuns de desenvolvimento:

- **commit-commands** — Fluxos de trabalho de commit do Git incluindo commit, push e criação de PR
- **pr-review-toolkit** — Agentes especializados para revisar pull requests
- **agent-sdk-dev** — Ferramentas para construir com o Claude Agent SDK
- **plugin-dev** — Toolkit para criar seus próprios plugins

#### Estilos de saída

Personalize como Claude responde:

- **explanatory-output-style** — Insights educacionais sobre escolhas de implementação
- **learning-output-style** — Modo de aprendizado interativo para desenvolvimento de habilidades

---

## Experimente: Adicione o Marketplace de Demonstração

Anthropic também mantém um marketplace de plugins de demonstração (`claude-code-plugins`) com plugins de exemplo que mostram o que é possível com o sistema de plugins. Diferentemente do marketplace oficial, você precisa adicionar este manualmente.

**Passo 1 — Adicione o marketplace:**

De dentro do Claude Code, execute o comando `plugin marketplace add` para o marketplace `anthropics/claude-code`:

```
/plugin marketplace add anthropics/claude-code
```

Isso baixa o catálogo do marketplace e torna seus plugins disponíveis para você.

**Passo 2 — Navegue pelos plugins disponíveis:**

Execute `/plugin` para abrir o gerenciador de plugins. Isso abre uma interface com abas. Use **Tab** (ou **Shift+Tab** para voltar) para navegar:

| Aba | Função |
| :--- | :--- |
| **Discover** | Navegue pelos plugins disponíveis de todos os seus marketplaces |
| **Installed** | Visualize e gerencie seus plugins instalados |
| **Marketplaces** | Adicione, remova ou atualize seus marketplaces adicionados |
| **Errors** | Visualize quaisquer erros de carregamento de plugins |

Vá para a aba **Discover** para ver plugins do marketplace que você acabou de adicionar.

**Passo 3 — Instale um plugin:**

Selecione um plugin para visualizar seus detalhes e escolha um escopo de instalação:

- **Escopo de usuário** — instale para você em todos os projetos
- **Escopo de projeto** — instale para todos os colaboradores neste repositório
- **Escopo local** — instale para você neste repositório apenas

Por exemplo, selecione **commit-commands** (um plugin que adiciona comandos de fluxo de trabalho do git) e instale-o no seu escopo de usuário.

Você também pode instalar diretamente da linha de comando:

```
/plugin install commit-commands@anthropics-claude-code
```

**Passo 4 — Use seu novo plugin:**

Após instalar, os comandos do plugin estão imediatamente disponíveis. Os comandos do plugin são nomeados com namespace pelo nome do plugin, então **commit-commands** fornece comandos como `/commit-commands:commit`.

Experimente fazendo uma alteração em um arquivo e executando:

```
/commit-commands:commit
```

Isso prepara suas alterações, gera uma mensagem de commit e cria o commit.

Cada plugin funciona de forma diferente. Verifique a descrição do plugin na aba **Discover** ou sua página inicial para aprender quais comandos e capacidades ele fornece.

---

## Adicione Marketplaces

Use o comando `/plugin marketplace add` para adicionar marketplaces de diferentes fontes.

> **Dica:** Você pode usar `/plugin market` em vez de `/plugin marketplace` e `rm` em vez de `remove`.

**Fontes suportadas:**

- **Repositórios GitHub** — formato `owner/repo` (ex: `anthropics/claude-code`)
- **URLs Git** — qualquer URL de repositório git (GitLab, Bitbucket, auto-hospedado)
- **Caminhos locais** — diretórios ou caminhos diretos para arquivos `marketplace.json`
- **URLs remotas** — URLs diretas para arquivos `marketplace.json` hospedados

### Adicione do GitHub

Adicione um repositório GitHub que contenha um arquivo `.claude-plugin/marketplace.json` usando o formato `owner/repo`:

```
/plugin marketplace add anthropics/claude-code
```

### Adicione de outros hosts Git

Adicione qualquer repositório git fornecendo a URL completa. Funciona com GitLab, Bitbucket e servidores auto-hospedados.

**Usando HTTPS:**

```
/plugin marketplace add https://gitlab.com/company/plugins.git
```

**Usando SSH:**

```
/plugin marketplace add git@gitlab.com:company/plugins.git
```

**Branch ou tag específico** — acrescente `#` seguido pela ref:

```
/plugin marketplace add https://gitlab.com/company/plugins.git#v1.0.0
```

### Adicione de caminhos locais

Adicione um diretório local que contenha um arquivo `.claude-plugin/marketplace.json`:

```
/plugin marketplace add ./my-marketplace
```

Ou adicione um caminho direto para um arquivo `marketplace.json`:

```
/plugin marketplace add ./path/to/marketplace.json
```

### Adicione de URLs remotas

Adicione um arquivo `marketplace.json` remoto via URL:

```
/plugin marketplace add https://example.com/marketplace.json
```

> **Nota:** Marketplaces baseados em URL têm algumas limitações em comparação com marketplaces baseados em Git. Se você encontrar erros "path not found" ao instalar plugins, veja Troubleshooting no guia de marketplace.

---

## Instale Plugins

Depois de adicionar marketplaces, você pode instalar plugins diretamente (instala no escopo de usuário por padrão):

```
/plugin install plugin-name@marketplace-name
```

Para escolhar um escopo de instalação diferente, use a interface interativa: execute `/plugin`, vá para a aba **Discover** e pressione **Enter** em um plugin. Você verá opções para:

- **Escopo de usuário** (padrão) — instale para você em todos os projetos
- **Escopo de projeto** — instale para todos os colaboradores neste repositório (adiciona a `.claude/settings.json`)
- **Escopo local** — instale para você neste repositório apenas (não compartilhado com colaboradores)

Plugins com escopo **managed** são instalados por administradores via managed settings e não podem ser modificados.

Execute `/plugin` e vá para a aba **Installed** para ver seus plugins agrupados por escopo.

> **Aviso:** Certifique-se de confiar em um plugin antes de instalá-lo. Anthropic não controla quais servidores MCP, arquivos ou outro software estão incluídos em plugins e não pode verificar que funcionam conforme pretendido. Verifique a página inicial de cada plugin para mais informações.

---

## Gerencie Plugins Instalados

Execute `/plugin` e vá para a aba **Installed** para visualizar, ativar, desativar ou desinstalar seus plugins.

**Comandos diretos:**

Desative um plugin sem desinstalá-lo:

```
/plugin disable plugin-name@marketplace-name
```

Reative um plugin desativado:

```
/plugin enable plugin-name@marketplace-name
```

Remova completamente um plugin:

```
/plugin uninstall plugin-name@marketplace-name
```

**Escopo específico** — use a opção `--scope`:

```
claude plugin install formatter@your-org --scope project
claude plugin uninstall formatter@your-org --scope project
```

---

## Gerencie Marketplaces

### Interface interativa

Execute `/plugin` e vá para a aba **Marketplaces** para:

- Visualize todos os seus marketplaces adicionados com suas fontes e status
- Adicione novos marketplaces
- Atualize listagens de marketplace para buscar os plugins mais recentes
- Remova marketplaces que você não precisa mais

### Comandos CLI

**Liste todos os marketplaces configurados:**

```
/plugin marketplace list
```

**Atualize listagens de plugins de um marketplace:**

```
/plugin marketplace update marketplace-name
```

**Remova um marketplace:**

```
/plugin marketplace remove marketplace-name
```

> **Aviso:** Remover um marketplace desinstalará quaisquer plugins que você instalou dele.

### Configure atualizações automáticas

Claude Code pode atualizar automaticamente marketplaces e seus plugins instalados na inicialização. Quando a atualização automática está ativada para um marketplace, Claude Code atualiza os dados do marketplace e atualiza os plugins instalados para suas versões mais recentes. Se algum plugin foi atualizado, você verá uma notificação sugerindo que reinicie Claude Code.

**Alterar atualização automática para marketplaces individuais:**

1. Execute `/plugin` para abrir o gerenciador de plugins
2. Selecione **Marketplaces**
3. Escolha um marketplace da lista
4. Selecione **Enable auto-update** ou **Disable auto-update**

**Comportamento padrão:**

- Marketplaces oficiais da Anthropic — atualização automática ativada por padrão
- Marketplaces de terceiros e de desenvolvimento local — atualização automática desativada por padrão

**Desativar todas as atualizações automáticas:**

Defina a variável de ambiente `DISABLE_AUTOUPDATER`. Veja Auto updates para detalhes.

**Manter atualizações de plugins ativas enquanto desativa atualizações do Claude Code:**

```bash
export DISABLE_AUTOUPDATER=true
export FORCE_AUTOUPDATE_PLUGINS=true
```

Isso é útil quando você quer gerenciar atualizações de Claude Code manualmente mas ainda receber atualizações automáticas de plugins.

---

## Configure Marketplaces de Equipe

Administradores de equipe podem configurar instalação automática de marketplace para projetos adicionando configuração de marketplace a `.claude/settings.json`. Quando membros da equipe confiam na pasta do repositório, Claude Code os solicita a instalar esses marketplaces e plugins.

Para opções de configuração completas incluindo `extraKnownMarketplaces` e `enabledPlugins`, veja Plugin settings.

---

## Solução de Problemas

### Comando /plugin não reconhecido

Se você vir "unknown command" ou o comando `/plugin` não aparecer:

1. **Verifique sua versão** — Execute `claude --version`. Plugins requerem versão 1.0.33 ou posterior.
2. **Atualize Claude Code:**
   - **Homebrew:** `brew upgrade claude-code`
   - **npm:** `npm update -g @anthropic-ai/claude-code`
   - **Native installer:** Execute novamente o comando de instalação de Setup
3. **Reinicie Claude Code** — Após atualizar, reinicie seu terminal e execute `claude` novamente.

### Problemas comuns

| Problema | Solução |
| :--- | :--- |
| **Marketplace não carregando** | Verifique se a URL está acessível e se `.claude-plugin/marketplace.json` existe no caminho |
| **Falhas na instalação de plugins** | Verifique se as URLs de origem do plugin estão acessíveis e se os repositórios são públicos (ou você tem acesso) |
| **Arquivos não encontrados após instalação** | Plugins são copiados para um cache; caminhos referenciando arquivos fora do diretório do plugin não funcionarão |
| **Plugin Skills não aparecendo** | Limpe o cache com `rm -rf ~/.claude/plugins/cache`, reinicie Claude Code e reinstale o plugin |

Para troubleshooting detalhado com soluções, veja Troubleshooting no guia de marketplace. Para ferramentas de debugging, veja Debugging and development tools na Referência de plugins.

---

## Próximos Passos

- **Construa seus próprios plugins** — Veja Plugins para criar comandos personalizados, agentes e hooks
- **Crie um marketplace** — Veja Create a plugin marketplace para distribuir plugins para sua equipe ou comunidade
- **Referência técnica** — Veja Plugins reference para especificações completas
