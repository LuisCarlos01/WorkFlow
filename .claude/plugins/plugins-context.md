> **Documentation Index**
> Fetch the complete documentation index at: https://code.claude.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

---

# Criar Plugins para Claude Code

> Crie plugins personalizados para estender Claude Code com skills, agents, hooks e MCP servers.

Plugins permitem que você estenda Claude Code com funcionalidade personalizada que pode ser compartilhada entre projetos e equipes. Este guia cobre a criação de seus próprios plugins com skills, agents, hooks e MCP servers.

Procurando instalar plugins existentes? Veja Descobrir e instalar plugins. Para especificações técnicas completas, veja Referência de plugins.

---

## Quando Usar Plugins vs Configuração Independente

Claude Code suporta duas maneiras de adicionar skills, agents e hooks personalizados:

| Abordagem | Nomes de skills | Melhor para |
| :--- | :--- | :--- |
| **Independente** (diretório `.claude/`) | `/hello` | Fluxos de trabalho pessoais, personalizações específicas do projeto, experimentos rápidos |
| **Plugins** (diretórios com `.claude-plugin/plugin.json`) | `/plugin-name:hello` | Compartilhamento com colegas de equipe, distribuição para a comunidade, lançamentos versionados, reutilizável em projetos |

**Use configuração independente quando:**

- Você está personalizando Claude Code para um único projeto
- A configuração é pessoal e não precisa ser compartilhada
- Você está experimentando com skills ou hooks antes de empacotá-los
- Você quer nomes de skills curtos como `/hello` ou `/review`

**Use plugins quando:**

- Você quer compartilhar funcionalidade com sua equipe ou comunidade
- Você precisa dos mesmos skills/agents em múltiplos projetos
- Você quer controle de versão e atualizações fáceis para suas extensões
- Você está distribuindo através de um marketplace
- Você está ok com skills com namespace como `/my-plugin:hello` (namespacing previne conflitos entre plugins)

> **Dica:** Comece com configuração independente em `.claude/` para iteração rápida, depois converta para um plugin quando estiver pronto para compartilhar.

---

## Início Rápido

Este início rápido o guia através da criação de um plugin com um skill personalizado. Você criará um manifesto (o arquivo de configuração que define seu plugin), adicionará um skill e o testará localmente usando a flag `--plugin-dir`.

### Pré-requisitos

- Claude Code instalado e autenticado
- Claude Code versão 1.0.33 ou posterior (execute `claude --version` para verificar)

> **Nota:** Se você não vir o comando `/plugin`, atualize Claude Code para a versão mais recente. Veja Troubleshooting para instruções de atualização.

### Crie seu primeiro plugin

**Passo 1 — Crie o diretório do plugin:**

Cada plugin vive em seu próprio diretório contendo um manifesto e seus skills, agents ou hooks. Crie um agora:

```bash
mkdir my-first-plugin
```

**Passo 2 — Crie o manifesto do plugin:**

O arquivo de manifesto em `.claude-plugin/plugin.json` define a identidade do seu plugin: seu nome, descrição e versão. Claude Code usa esses metadados para exibir seu plugin no gerenciador de plugins.

Crie o diretório `.claude-plugin` dentro da pasta do seu plugin:

```bash
mkdir my-first-plugin/.claude-plugin
```

Depois crie `my-first-plugin/.claude-plugin/plugin.json` com este conteúdo:

```json
{
  "name": "my-first-plugin",
  "description": "A greeting plugin to learn the basics",
  "version": "1.0.0",
  "author": {
    "name": "Your Name"
  }
}
```

**Campos do manifesto:**

| Campo | Propósito |
| :--- | :--- |
| `name` | Identificador único e namespace de skill. Skills são prefixados com isso (ex: `/my-first-plugin:hello`). |
| `description` | Mostrado no gerenciador de plugins ao navegar ou instalar plugins. |
| `version` | Rastreie lançamentos usando semantic versioning. |
| `author` | Opcional. Útil para atribuição. |

Para campos adicionais como `homepage`, `repository` e `license`, veja o esquema de manifesto completo na Referência de plugins.

**Passo 3 — Adicione um skill:**

Skills vivem no diretório `skills/`. Cada skill é uma pasta contendo um arquivo `SKILL.md`. O nome da pasta se torna o nome do skill, prefixado com o namespace do plugin (`hello/` em um plugin nomeado `my-first-plugin` cria `/my-first-plugin:hello`).

Crie um diretório de skill na pasta do seu plugin:

```bash
mkdir -p my-first-plugin/skills/hello
```

Depois crie `my-first-plugin/skills/hello/SKILL.md` com este conteúdo:

```markdown
---
description: Greet the user with a friendly message
disable-model-invocation: true
---

Greet the user warmly and ask how you can help them today.
```

**Passo 4 — Teste seu plugin:**

Execute Claude Code com a flag `--plugin-dir` para carregar seu plugin:

```bash
claude --plugin-dir ./my-first-plugin
```

Uma vez que Claude Code inicia, tente seu novo comando:

```
/my-first-plugin:hello
```

Você verá Claude responder com uma saudação. Execute `/help` para ver seu comando listado sob o namespace do plugin.

> **Nota:** Skills de plugin sempre têm namespace (como `/greet:hello`) para prevenir conflitos quando múltiplos plugins têm skills com o mesmo nome. Para mudar o prefixo de namespace, atualize o campo `name` em `plugin.json`.

**Passo 5 — Adicione argumentos de skill:**

Torne seu skill dinâmico aceitando entrada do usuário. O placeholder `$ARGUMENTS` captura qualquer texto que o usuário fornece após o nome do skill.

Atualize seu arquivo `hello.md`:

```markdown
---
description: Greet the user with a personalized message
---

# Hello Command

Greet the user named "$ARGUMENTS" warmly and ask how you can help them today. Make the greeting personal and encouraging.
```

Reinicie Claude Code para pegar as mudanças, depois tente o comando com seu nome:

```
/my-first-plugin:hello Alex
```

Claude o saudará pelo nome. Para mais sobre passar argumentos para skills, veja a documentação de Skills.

---

**Resumo do que foi criado:**

- **Manifesto do plugin** (`.claude-plugin/plugin.json`) — descreve os metadados do seu plugin
- **Diretório de comandos** (`commands/`) — contém seus skills personalizados
- **Argumentos de skill** (`$ARGUMENTS`) — captura entrada do usuário para comportamento dinâmico

> **Dica:** A flag `--plugin-dir` é útil para desenvolvimento e testes. Quando estiver pronto para compartilhar seu plugin com outros, veja Criar e distribuir um marketplace de plugins.

---

## Visão Geral da Estrutura do Plugin

Você criou um plugin com um skill, mas plugins podem incluir muito mais: agents personalizados, hooks, MCP servers e LSP servers.

> **Aviso — Erro comum:** Não coloque `commands/`, `agents/`, `skills/` ou `hooks/` dentro do diretório `.claude-plugin/`. Apenas `plugin.json` vai dentro de `.claude-plugin/`. Todos os outros diretórios devem estar no nível raiz do plugin.

| Diretório | Localização | Propósito |
| :--- | :--- | :--- |
| `.claude-plugin/` | Raiz do plugin | Contém manifesto `plugin.json` (opcional se componentes usam localizações padrão) |
| `commands/` | Raiz do plugin | Skills como arquivos Markdown |
| `agents/` | Raiz do plugin | Definições de agent personalizadas |
| `skills/` | Raiz do plugin | Agent Skills com arquivos `SKILL.md` |
| `hooks/` | Raiz do plugin | Manipuladores de eventos em `hooks.json` |
| `.mcp.json` | Raiz do plugin | Configurações de MCP server |
| `.lsp.json` | Raiz do plugin | Configurações de LSP server para inteligência de código |

**Estrutura visual de exemplo:**

```
my-plugin/
├── .claude-plugin/
│   └── plugin.json          # Manifesto (obrigatório)
├── commands/                 # Skills como Markdown
│   └── hello.md
├── agents/                   # Definições de agents
│   └── reviewer.md
├── skills/                   # Agent Skills
│   └── code-review/
│       └── SKILL.md
├── hooks/                    # Manipuladores de eventos
│   └── hooks.json
├── .mcp.json                 # Config MCP servers
└── .lsp.json                 # Config LSP servers
```

---

## Desenvolver Plugins Mais Complexos

Uma vez que você está confortável com plugins básicos, você pode criar extensões mais sofisticadas.

### Adicione Skills ao seu plugin

Plugins podem incluir Agent Skills para estender as capacidades do Claude. Skills são invocados por modelo: Claude os usa automaticamente baseado no contexto da tarefa.

Adicione um diretório `skills/` na raiz do seu plugin com pastas de Skill contendo arquivos `SKILL.md`:

```
my-plugin/
├── .claude-plugin/
│   └── plugin.json
└── skills/
    └── code-review/
        └── SKILL.md
```

Cada `SKILL.md` precisa de frontmatter com campos `name` e `description`, seguido por instruções:

```yaml
---
name: code-review
description: Reviews code for best practices and potential issues. Use when reviewing code, checking PRs, or analyzing code quality.
---

When reviewing code, check for:
1. Code organization and structure
2. Error handling
3. Security concerns
4. Test coverage
```

Após instalar o plugin, reinicie Claude Code para carregar os Skills. Para orientação completa de autoria de Skill incluindo divulgação progressiva e restrições de ferramentas, veja a documentação de Agent Skills.

### Adicione LSP servers ao seu plugin

> **Dica:** Para linguagens comuns como TypeScript, Python e Rust, instale os plugins LSP pré-construídos do marketplace oficial. Crie plugins LSP personalizados apenas quando você precisar de suporte para linguagens que ainda não estão cobertas.

Plugins LSP (Language Server Protocol) dão ao Claude inteligência de código em tempo real. Se você precisar suportar uma linguagem que não tem um plugin LSP oficial, você pode criar o seu próprio adicionando um arquivo `.lsp.json` ao seu plugin:

```json
{
  "go": {
    "command": "gopls",
    "args": ["serve"],
    "extensionToLanguage": {
      ".go": "go"
    }
  }
}
```

Usuários instalando seu plugin devem ter o binário do language server instalado em sua máquina.

Para opções de configuração LSP completas, veja LSP servers na Referência de plugins.

### Organize plugins complexos

Para plugins com muitos componentes, organize sua estrutura de diretório por funcionalidade. Para layouts de diretório completos e padrões de organização, veja Estrutura de diretório do plugin na Referência de plugins.

### Teste seus plugins localmente

Use a flag `--plugin-dir` para testar plugins durante o desenvolvimento. Isso carrega seu plugin diretamente sem exigir instalação.

```bash
claude --plugin-dir ./my-plugin
```

Conforme você faz mudanças no seu plugin, reinicie Claude Code para pegar as atualizações. Teste seus componentes de plugin:

- Tente seus comandos com `/command-name`
- Verifique que agents aparecem em `/agents`
- Verifique que hooks funcionam como esperado

> **Dica:** Você pode carregar múltiplos plugins de uma vez especificando a flag múltiplas vezes:
>
> ```bash
> claude --plugin-dir ./plugin-one --plugin-dir ./plugin-two
> ```

### Depure problemas de plugin

Se seu plugin não está funcionando como esperado:

1. **Verifique a estrutura** — Certifique-se de que seus diretórios estão na raiz do plugin, não dentro de `.claude-plugin/`
2. **Teste componentes individualmente** — Verifique cada comando, agent e hook separadamente
3. **Use ferramentas de validação e depuração** — Veja Ferramentas de depuração e desenvolvimento na Referência de plugins para comandos CLI e técnicas de troubleshooting

### Compartilhe seus plugins

Quando seu plugin estiver pronto para compartilhar:

1. **Adicione documentação** — Inclua um `README.md` com instruções de instalação e uso
2. **Versione seu plugin** — Use semantic versioning em seu `plugin.json`
3. **Crie ou use um marketplace** — Distribua através de marketplaces de plugins para instalação
4. **Teste com outros** — Tenha membros da equipe testarem o plugin antes de distribuição mais ampla

Uma vez que seu plugin está em um marketplace, outros podem instalá-lo usando as instruções em Descobrir e instalar plugins.

---

## Converter Configurações Existentes em Plugins

Se você já tem skills ou hooks em seu diretório `.claude/`, você pode convertê-los em um plugin para compartilhamento e distribuição mais fáceis.

### Passos de migração

**Passo 1 — Crie a estrutura do plugin:**

Crie um novo diretório de plugin:

```bash
mkdir -p my-plugin/.claude-plugin
```

Crie o arquivo de manifesto em `my-plugin/.claude-plugin/plugin.json`:

```json
{
  "name": "my-plugin",
  "description": "Migrated from standalone configuration",
  "version": "1.0.0"
}
```

**Passo 2 — Copie seus arquivos existentes:**

Copie suas configurações existentes para o diretório do plugin:

```bash
# Copy commands
cp -r .claude/commands my-plugin/

# Copy agents (if any)
cp -r .claude/agents my-plugin/

# Copy skills (if any)
cp -r .claude/skills my-plugin/
```

**Passo 3 — Migre hooks:**

Se você tem hooks em suas configurações, crie um diretório de hooks:

```bash
mkdir my-plugin/hooks
```

Crie `my-plugin/hooks/hooks.json` com sua configuração de hooks. Copie o objeto `hooks` de seu `.claude/settings.json` ou `settings.local.json`, já que o formato é o mesmo. O comando recebe entrada de hook como JSON em stdin, então use `jq` para extrair o caminho do arquivo:

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write|Edit",
        "hooks": [
          {
            "type": "command",
            "command": "jq -r '.tool_input.file_path' | xargs npm run lint:fix"
          }
        ]
      }
    ]
  }
}
```

**Passo 4 — Teste seu plugin migrado:**

Carregue seu plugin para verificar que tudo funciona:

```bash
claude --plugin-dir ./my-plugin
```

Teste cada componente: execute seus comandos, verifique que agents aparecem em `/agents` e verifique que hooks disparam corretamente.

### O que muda ao migrar

| Independente (`.claude/`) | Plugin |
| :--- | :--- |
| Disponível apenas em um projeto | Pode ser compartilhado via marketplaces |
| Arquivos em `.claude/commands/` | Arquivos em `plugin-name/commands/` |
| Hooks em `settings.json` | Hooks em `hooks/hooks.json` |
| Deve copiar manualmente para compartilhar | Instale com `/plugin install` |

> **Nota:** Após migrar, você pode remover os arquivos originais de `.claude/` para evitar duplicatas. A versão do plugin terá precedência quando carregada.

---

## Próximos Passos

Agora que você entende o sistema de plugins do Claude Code, aqui estão caminhos sugeridos para diferentes objetivos:

### Para usuários de plugins

- **Descobrir e instalar plugins** — navegue em marketplaces e instale plugins
- **Configurar marketplaces de equipe** — configure plugins em nível de repositório para sua equipe

### Para desenvolvedores de plugins

- **Criar e distribuir um marketplace** — empacote e compartilhe seus plugins
- **Referência de plugins** — especificações técnicas completas
- **Mergulhe mais fundo em componentes específicos de plugin:**
  - **Skills** — detalhes de desenvolvimento de skill
  - **Subagents** — configuração e capacidades de agent
  - **Hooks** — manipulação de eventos e automação
  - **MCP** — integração de ferramentas externas
