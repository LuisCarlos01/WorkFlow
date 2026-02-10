> **Documentation Index**
> Fetch the complete documentation index at: https://code.claude.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

---

# Parte 1: Criar Subagentes Personalizados

> Crie e use subagentes de IA especializados no Claude Code para fluxos de trabalho específicos de tarefas e gerenciamento de contexto aprimorado.

Subagentes são assistentes de IA especializados que lidam com tipos específicos de tarefas. Cada subagente é executado em sua própria janela de contexto com um prompt de sistema personalizado, acesso a ferramentas específicas e permissões independentes. Quando Claude encontra uma tarefa que corresponde à descrição de um subagente, ele delega para esse subagente, que funciona independentemente e retorna resultados.

> **Nota:** Se você precisar de múltiplos agentes trabalhando em paralelo e se comunicando entre si, consulte [Parte 2: Equipes de Agentes](#parte-2-orquestre-equipes-de-sessões-claude-code) em vez disso. Subagentes funcionam dentro de uma única sessão; equipes de agentes coordenam entre sessões separadas.

**Subagentes ajudam você a:**

- **Preservar contexto** — mantendo exploração e implementação fora de sua conversa principal
- **Aplicar restrições** — limitando quais ferramentas um subagente pode usar
- **Reutilizar configurações** — entre projetos com subagentes de nível de usuário
- **Especializar comportamento** — com prompts de sistema focados para domínios específicos
- **Controlar custos** — roteando tarefas para modelos mais rápidos e baratos como Haiku

Claude usa a descrição de cada subagente para decidir quando delegar tarefas. Quando você cria um subagente, escreva uma descrição clara para que Claude saiba quando usá-lo.

Claude Code inclui vários subagentes integrados como **Explore**, **Plan** e **general-purpose**. Você também pode criar subagentes personalizados para lidar com tarefas específicas. Esta página cobre os [subagentes integrados](#subagentes-integrados), [como criar o seu próprio](#início-rápido-crie-seu-primeiro-subagente), [opções de configuração completas](#configurar-subagentes), [padrões para trabalhar com subagentes](#trabalhe-com-subagentes) e [subagentes de exemplo](#subagentes-de-exemplo).

---

## Subagentes Integrados

Claude Code inclui subagentes integrados que Claude usa automaticamente quando apropriado. Cada um herda as permissões da conversa pai com restrições de ferramentas adicionais.

### Explore

Um agente rápido e somente leitura otimizado para pesquisar e analisar bases de código.

- **Modelo:** Haiku (rápido, baixa latência)
- **Ferramentas:** Ferramentas somente leitura (acesso negado a ferramentas Write e Edit)
- **Propósito:** Descoberta de arquivos, pesquisa de código, exploração de base de código

Claude delega para Explore quando precisa pesquisar ou entender uma base de código sem fazer alterações. Isso mantém os resultados da exploração fora do contexto da sua conversa principal.

Ao invocar Explore, Claude especifica um nível de minuciosidade: **quick** para buscas direcionadas, **medium** para exploração equilibrada, ou **very thorough** para análise abrangente.

### Plan

Um agente de pesquisa usado durante plan mode para reunir contexto antes de apresentar um plano.

- **Modelo:** Herda da conversa principal
- **Ferramentas:** Ferramentas somente leitura (acesso negado a ferramentas Write e Edit)
- **Propósito:** Pesquisa de base de código para planejamento

Quando você está em plan mode e Claude precisa entender sua base de código, ele delega a pesquisa para o subagente Plan. Isso evita aninhamento infinito (subagentes não podem gerar outros subagentes) enquanto ainda reúne o contexto necessário.

### General-purpose

Um agente capaz para tarefas complexas e multi-etapas que requerem exploração e ação.

- **Modelo:** Herda da conversa principal
- **Ferramentas:** Todas as ferramentas
- **Propósito:** Pesquisa complexa, operações multi-etapas, modificações de código

Claude delega para general-purpose quando a tarefa requer exploração e modificação, raciocínio complexo para interpretar resultados, ou múltiplas etapas dependentes.

### Outros Agentes Auxiliares

Claude Code inclui agentes auxiliares adicionais para tarefas específicas. Estes são normalmente invocados automaticamente, então você não precisa usá-los diretamente.

| Agente | Modelo | Quando Claude o usa |
| :--- | :--- | :--- |
| Bash | Herda | Executando comandos de terminal em um contexto separado |
| statusline-setup | Sonnet | Quando você executa `/statusline` para configurar sua linha de status |
| Claude Code Guide | Haiku | Quando você faz perguntas sobre recursos do Claude Code |

Além desses subagentes integrados, você pode criar os seus próprios com prompts personalizados, restrições de ferramentas, modos de permissão, hooks e skills. As seções a seguir mostram como começar e personalizar subagentes.

---

## Início Rápido: Crie Seu Primeiro Subagente

Subagentes são definidos em arquivos Markdown com frontmatter YAML. Você pode criá-los manualmente ou usar o comando `/agents`.

Este passo a passo o guia através da criação de um subagente de nível de usuário com o comando `/agent`. O subagente revisa código e sugere melhorias para a base de código.

**Passo 1 — Abra a interface de subagentes:**

No Claude Code, execute:

```
/agents
```

**Passo 2 — Crie um novo agente de nível de usuário:**

Selecione **Create new agent**, depois escolha **User-level**. Isso salva o subagente em `~/.claude/agents/` para que esteja disponível em todos os seus projetos.

**Passo 3 — Gere com Claude:**

Selecione **Generate with Claude**. Quando solicitado, descreva o subagente:

```
A code improvement agent that scans files and suggests improvements
for readability, performance, and best practices. It should explain
each issue, show the current code, and provide an improved version.
```

Claude gera o prompt de sistema e a configuração. Pressione `e` para abri-lo em seu editor se quiser personalizá-lo.

**Passo 4 — Selecione ferramentas:**

Para um revisor somente leitura, desselecione tudo exceto **Read-only tools**. Se você manter todas as ferramentas selecionadas, o subagente herda todas as ferramentas disponíveis para a conversa principal.

**Passo 5 — Selecione modelo:**

Escolha qual modelo o subagente usa. Para este agente de exemplo, selecione **Sonnet**, que equilibra capacidade e velocidade para analisar padrões de código.

**Passo 6 — Escolha uma cor:**

Escolha uma cor de fundo para o subagente. Isso ajuda você a identificar qual subagente está sendo executado na interface.

**Passo 7 — Salve e teste:**

Salve o subagente. Ele está disponível imediatamente (sem necessidade de reiniciar). Teste-o:

```
Use the code-improver agent to suggest improvements in this project
```

Claude delega para seu novo subagente, que verifica a base de código e retorna sugestões de melhoria.

Agora você tem um subagente que pode usar em qualquer projeto em sua máquina para analisar bases de código e sugerir melhorias.

Você também pode criar subagentes manualmente como arquivos Markdown, defini-los via flags CLI, ou distribuí-los através de plugins. As seções a seguir cobrem todas as opções de configuração.

---

## Configurar Subagentes

### Use o comando /agents

O comando `/agents` fornece uma interface interativa para gerenciar subagentes. Execute `/agents` para:

- Visualizar todos os subagentes disponíveis (integrados, usuário, projeto e plugin)
- Criar novos subagentes com configuração guiada ou geração por Claude
- Editar configuração de subagente existente e acesso a ferramentas
- Deletar subagentes personalizados
- Ver quais subagentes estão ativos quando duplicatas existem

Esta é a forma recomendada de criar e gerenciar subagentes. Para criação manual ou automação, você também pode adicionar arquivos de subagente diretamente.

### Escolha o escopo do subagente

Subagentes são arquivos Markdown com frontmatter YAML. Armazene-os em locais diferentes dependendo do escopo. Quando múltiplos subagentes compartilham o mesmo nome, o local de prioridade mais alta vence.

| Local | Escopo | Prioridade | Como criar |
| :--- | :--- | :--- | :--- |
| Flag CLI `--agents` | Sessão atual | 1 (mais alta) | Passe JSON ao iniciar Claude Code |
| `.claude/agents/` | Projeto atual | 2 | Interativo ou manual |
| `~/.claude/agents/` | Todos os seus projetos | 3 | Interativo ou manual |
| Diretório `agents/` do Plugin | Onde o plugin está habilitado | 4 (mais baixa) | Instalado com plugins |

**Subagentes de projeto** (`.claude/agents/`) são ideais para subagentes específicos de uma base de código. Verifique-os no controle de versão para que sua equipe possa usá-los e melhorá-los colaborativamente.

**Subagentes de usuário** (`~/.claude/agents/`) são subagentes pessoais disponíveis em todos os seus projetos.

**Subagentes definidos por CLI** são passados como JSON ao iniciar Claude Code. Eles existem apenas para essa sessão e não são salvos em disco, tornando-os úteis para testes rápidos ou scripts de automação:

```bash
claude --agents '{
  "code-reviewer": {
    "description": "Expert code reviewer. Use proactively after code changes.",
    "prompt": "You are a senior code reviewer. Focus on code quality, security, and best practices.",
    "tools": ["Read", "Grep", "Glob", "Bash"],
    "model": "sonnet"
  }
}'
```

A flag `--agents` aceita JSON com os mesmos campos que frontmatter. Use `prompt` para o prompt de sistema (equivalente ao corpo markdown em subagentes baseados em arquivo). Consulte a referência CLI para o formato JSON completo.

**Subagentes de plugin** vêm de plugins que você instalou. Eles aparecem em `/agents` junto com seus subagentes personalizados. Consulte a referência de componentes de plugin para detalhes sobre como criar subagentes de plugin.

### Escreva arquivos de subagente

Arquivos de subagente usam frontmatter YAML para configuração, seguido pelo prompt de sistema em Markdown:

> **Nota:** Subagentes são carregados no início da sessão. Se você criar um subagente adicionando manualmente um arquivo, reinicie sua sessão ou use `/agents` para carregá-lo imediatamente.

```markdown
---
name: code-reviewer
description: Reviews code for quality and best practices
tools: Read, Glob, Grep
model: sonnet
---

You are a code reviewer. When invoked, analyze the code and provide
specific, actionable feedback on quality, security, and best practices.
```

O frontmatter define os metadados e configuração do subagente. O corpo se torna o prompt de sistema que guia o comportamento do subagente. Subagentes recebem apenas este prompt de sistema (mais detalhes básicos de ambiente como diretório de trabalho), não o prompt de sistema completo do Claude Code.

#### Campos de frontmatter suportados

Os seguintes campos podem ser usados no frontmatter YAML. Apenas `name` e `description` são obrigatórios.

| Campo | Obrigatório | Descrição |
| :--- | :--- | :--- |
| `name` | Sim | Identificador único usando letras minúsculas e hífens |
| `description` | Sim | Quando Claude deve delegar para este subagente |
| `tools` | Não | Ferramentas que o subagente pode usar. Herda todas as ferramentas se omitido |
| `disallowedTools` | Não | Ferramentas a negar, removidas da lista herdada ou especificada |
| `model` | Não | Modelo a usar: `sonnet`, `opus`, `haiku`, ou `inherit`. Padrão é `inherit` |
| `permissionMode` | Não | Modo de permissão: `default`, `acceptEdits`, `dontAsk`, `bypassPermissions`, ou `plan` |
| `skills` | Não | Skills a carregar no contexto do subagente na inicialização. O conteúdo completo da skill é injetado, não apenas disponibilizado para invocação. Subagentes não herdam skills da conversa pai |
| `hooks` | Não | Hooks de ciclo de vida escopo para este subagente |
| `memory` | Não | Escopo de memória persistente: `user`, `project`, ou `local`. Habilita aprendizado entre sessões |

### Escolha um modelo

O campo `model` controla qual modelo de IA o subagente usa:

- **Alias de modelo:** Use um dos aliases disponíveis: `sonnet`, `opus`, ou `haiku`
- **inherit:** Use o mesmo modelo que a conversa principal
- **Omitido:** Se não especificado, padrão é `inherit` (usa o mesmo modelo que a conversa principal)

### Controle as capacidades do subagente

Você pode controlar o que os subagentes podem fazer através de acesso a ferramentas, modos de permissão e regras condicionais.

#### Ferramentas disponíveis

Subagentes podem usar qualquer uma das ferramentas internas do Claude Code. Por padrão, subagentes herdam todas as ferramentas da conversa principal, incluindo ferramentas MCP.

Para restringir ferramentas, use o campo `tools` (lista de permissões) ou campo `disallowedTools` (lista de negação):

```yaml
---
name: safe-researcher
description: Research agent with restricted capabilities
tools: Read, Grep, Glob, Bash
disallowedTools: Write, Edit
---
```

#### Modos de permissão

O campo `permissionMode` controla como o subagente lida com prompts de permissão. Subagentes herdam o contexto de permissão da conversa principal, mas podem sobrescrever o modo.

| Modo | Comportamento |
| :--- | :--- |
| `default` | Verificação de permissão padrão com prompts |
| `acceptEdits` | Auto-aceitar edições de arquivo |
| `dontAsk` | Auto-negar prompts de permissão (ferramentas explicitamente permitidas ainda funcionam) |
| `bypassPermissions` | Pular todas as verificações de permissão |
| `plan` | Plan mode (exploração somente leitura) |

> **Aviso:** Use `bypassPermissions` com cuidado. Ele pula todas as verificações de permissão, permitindo que o subagente execute qualquer operação sem aprovação.

Se o pai usar `bypassPermissions`, isso tem precedência e não pode ser sobrescrito.

#### Pré-carregue skills em subagentes

Use o campo `skills` para injetar conteúdo de skill no contexto de um subagente na inicialização. Isso dá ao subagente conhecimento de domínio sem exigir que ele descubra e carregue skills durante a execução.

```yaml
---
name: api-developer
description: Implement API endpoints following team conventions
skills:
  - api-conventions
  - error-handling-patterns
---

Implement API endpoints. Follow the conventions and patterns from the preloaded skills.
```

O conteúdo completo de cada skill é injetado no contexto do subagente, não apenas disponibilizado para invocação. Subagentes não herdam skills da conversa pai; você deve listá-las explicitamente.

> **Nota:** Isso é o inverso de executar uma skill em um subagente. Com `skills` em um subagente, o subagente controla o prompt de sistema e carrega conteúdo de skill. Com `context: fork` em uma skill, o conteúdo de skill é injetado no agente que você especificar. Ambos usam o mesmo sistema subjacente.

#### Habilite memória persistente

O campo `memory` dá ao subagente um diretório persistente que sobrevive entre conversas. O subagente usa este diretório para construir conhecimento ao longo do tempo, como padrões de base de código, insights de depuração e decisões arquiteturais.

```yaml
---
name: code-reviewer
description: Reviews code for quality and best practices
memory: user
---

You are a code reviewer. As you review code, update your agent memory with
patterns, conventions, and recurring issues you discover.
```

Escolha um escopo baseado em quão amplamente a memória deve se aplicar:

| Escopo | Local | Use quando |
| :--- | :--- | :--- |
| `user` | `~/.claude/agent-memory/<name-of-agent>/` | O subagente deve lembrar aprendizados entre todos os projetos |
| `project` | `.claude/agent-memory/<name-of-agent>/` | O conhecimento do subagente é específico do projeto e compartilhável via controle de versão |
| `local` | `.claude/agent-memory-local/<name-of-agent>/` | O conhecimento do subagente é específico do projeto, mas não deve ser verificado no controle de versão |

**Quando a memória está habilitada:**

- O prompt de sistema do subagente inclui instruções para ler e escrever no diretório de memória.
- O prompt de sistema do subagente também inclui as primeiras 200 linhas de `MEMORY.md` no diretório de memória, com instruções para curar `MEMORY.md` se exceder 200 linhas.
- Ferramentas Read, Write e Edit são automaticamente habilitadas para que o subagente possa gerenciar seus arquivos de memória.

**Dicas de memória persistente:**

- `user` é o escopo padrão recomendado. Use `project` ou `local` quando o conhecimento do subagente é apenas relevante para uma base de código específica.
- Peça ao subagente para consultar sua memória antes de começar o trabalho: "Review this PR, and check your memory for patterns you've seen before."
- Peça ao subagente para atualizar sua memória após completar uma tarefa: "Now that you're done, save what you learned to your memory." Com o tempo, isso constrói uma base de conhecimento que torna o subagente mais eficaz.
- Inclua instruções de memória diretamente no arquivo markdown do subagente para que ele mantenha proativamente sua própria base de conhecimento:

```markdown
Update your agent memory as you discover codepaths, patterns, library
locations, and key architectural decisions. This builds up institutional
knowledge across conversations. Write concise notes about what you found
and where.
```

#### Regras condicionais com hooks

Para controle mais dinâmico sobre o uso de ferramentas, use hooks `PreToolUse` para validar operações antes de serem executadas. Isso é útil quando você precisa permitir algumas operações de uma ferramenta enquanto bloqueia outras.

Este exemplo cria um subagente que permite apenas consultas de banco de dados somente leitura. O hook `PreToolUse` executa o script especificado em `command` antes de cada comando Bash ser executado:

```yaml
---
name: db-reader
description: Execute read-only database queries
tools: Bash
hooks:
  PreToolUse:
    - matcher: "Bash"
      hooks:
        - type: command
          command: "./scripts/validate-readonly-query.sh"
---
```

Claude Code passa entrada de hook como JSON via stdin para comandos de hook. O script de validação lê este JSON, extrai o comando Bash e sai com código 2 para bloquear operações de escrita:

```bash
#!/bin/bash
# ./scripts/validate-readonly-query.sh

INPUT=$(cat)
COMMAND=$(echo "$INPUT" | jq -r '.tool_input.command // empty')

# Block SQL write operations (case-insensitive)
if echo "$COMMAND" | grep -iE '\b(INSERT|UPDATE|DELETE|DROP|CREATE|ALTER|TRUNCATE)\b' > /dev/null; then
  echo "Blocked: Only SELECT queries are allowed" >&2
  exit 2
fi

exit 0
```

Consulte Entrada de Hook para o esquema de entrada completo e códigos de saída para como códigos de saída afetam o comportamento.

#### Desabilite subagentes específicos

Você pode impedir que Claude use subagentes específicos adicionando-os ao array `deny` em suas configurações. Use o formato `Task(subagent-name)` onde `subagent-name` corresponde ao campo name do subagente.

```json
{
  "permissions": {
    "deny": ["Task(Explore)", "Task(my-custom-agent)"]
  }
}
```

Isso funciona para subagentes integrados e personalizados. Você também pode usar a flag CLI `--disallowedTools`:

```bash
claude --disallowedTools "Task(Explore)"
```

Consulte Documentação de Permissões para mais detalhes sobre regras de permissão.

### Defina hooks para subagentes

Subagentes podem definir hooks que são executados durante o ciclo de vida do subagente. Existem duas formas de configurar hooks:

1. **No frontmatter do subagente:** Defina hooks que são executados apenas enquanto esse subagente específico está ativo
2. **Em `settings.json`:** Defina hooks que são executados na sessão principal quando subagentes iniciam ou param

#### Hooks no frontmatter do subagente

Defina hooks diretamente no arquivo markdown do subagente. Esses hooks são executados apenas enquanto esse subagente específico está ativo e são limpos quando ele termina.

Todos os eventos de hook são suportados. Os eventos mais comuns para subagentes são:

| Evento | Entrada do Matcher | Quando é acionado |
| :--- | :--- | :--- |
| `PreToolUse` | Nome da ferramenta | Antes do subagente usar uma ferramenta |
| `PostToolUse` | Nome da ferramenta | Depois do subagente usar uma ferramenta |
| `Stop` | (nenhum) | Quando o subagente termina (convertido para `SubagentStop` em tempo de execução) |

Este exemplo valida comandos Bash com o hook `PreToolUse` e executa um linter após edições de arquivo com `PostToolUse`:

```yaml
---
name: code-reviewer
description: Review code changes with automatic linting
hooks:
  PreToolUse:
    - matcher: "Bash"
      hooks:
        - type: command
          command: "./scripts/validate-command.sh $TOOL_INPUT"
  PostToolUse:
    - matcher: "Edit|Write"
      hooks:
        - type: command
          command: "./scripts/run-linter.sh"
---
```

Hooks `Stop` no frontmatter são automaticamente convertidos para eventos `SubagentStop`.

#### Hooks de nível de projeto para eventos de subagente

Configure hooks em `settings.json` que respondem a eventos de ciclo de vida de subagente na sessão principal.

| Evento | Entrada do Matcher | Quando é acionado |
| :--- | :--- | :--- |
| `SubagentStart` | Nome do tipo de agente | Quando um subagente começa a execução |
| `SubagentStop` | (nenhum) | Quando qualquer subagente é concluído |

`SubagentStart` suporta matchers para direcionar tipos de agente específicos por nome. `SubagentStop` é acionado para todas as conclusões de subagente independentemente dos valores do matcher. Este exemplo executa um script de configuração apenas quando o subagente `db-agent` inicia, e um script de limpeza quando qualquer subagente para:

```json
{
  "hooks": {
    "SubagentStart": [
      {
        "matcher": "db-agent",
        "hooks": [
          { "type": "command", "command": "./scripts/setup-db-connection.sh" }
        ]
      }
    ],
    "SubagentStop": [
      {
        "hooks": [
          { "type": "command", "command": "./scripts/cleanup-db-connection.sh" }
        ]
      }
    ]
  }
}
```

Consulte Hooks para o formato de configuração de hook completo.

---

## Trabalhe com Subagentes

### Entenda a delegação automática

Claude delega tarefas automaticamente baseado na descrição da tarefa em sua solicitação, no campo `description` nas configurações de subagente e no contexto atual. Para encorajar delegação proativa, inclua frases como "use proactively" no campo description do seu subagente.

Você também pode solicitar um subagente específico explicitamente:

```
Use the test-runner subagent to fix failing tests
Have the code-reviewer subagent look at my recent changes
```

### Execute subagentes em primeiro plano ou segundo plano

Subagentes podem ser executados em primeiro plano (bloqueante) ou segundo plano (concorrente):

- **Subagentes em primeiro plano** — bloqueiam a conversa principal até serem concluídos. Prompts de permissão e perguntas de esclarecimento (como `AskUserQuestion`) são passados para você.
- **Subagentes em segundo plano** — são executados concorrentemente enquanto você continua trabalhando. Antes de iniciar, Claude Code solicita quaisquer permissões de ferramenta que o subagente precisará, garantindo que ele tenha as aprovações necessárias antecipadamente. Uma vez em execução, o subagente herda essas permissões e auto-nega qualquer coisa não pré-aprovada. Se um subagente em segundo plano precisar fazer perguntas de esclarecimento, essa chamada de ferramenta falha, mas o subagente continua. Ferramentas MCP não estão disponíveis em subagentes em segundo plano.

Se um subagente em segundo plano falhar devido a permissões ausentes, você pode retomá-lo em primeiro plano para tentar novamente com prompts interativos.

Claude decide se deve executar subagentes em primeiro plano ou segundo plano baseado na tarefa. Você também pode:

- Pedir a Claude para "run this in the background"
- Pressionar **Ctrl+B** para colocar uma tarefa em execução em segundo plano

Para desabilitar toda a funcionalidade de tarefa em segundo plano, defina a variável de ambiente `CLAUDE_CODE_DISABLE_BACKGROUND_TASKS` para `1`.

### Padrões comuns

#### Isole operações de alto volume

Um dos usos mais eficazes para subagentes é isolar operações que produzem grandes quantidades de saída. Executar testes, buscar documentação ou processar arquivos de log pode consumir contexto significativo. Ao delegar esses para um subagente, a saída verbosa fica no contexto do subagente enquanto apenas o resumo relevante retorna para sua conversa principal.

```
Use a subagent to run the test suite and report only the failing tests with their error messages
```

#### Execute pesquisa em paralelo

Para investigações independentes, lance múltiplos subagentes para trabalhar simultaneamente:

```
Research the authentication, database, and API modules in parallel using separate subagents
```

Cada subagente explora sua área independentemente, depois Claude sintetiza os achados. Isso funciona melhor quando os caminhos de pesquisa não dependem um do outro.

> **Aviso:** Quando subagentes são concluídos, seus resultados retornam para sua conversa principal. Executar muitos subagentes que cada um retorna resultados detalhados pode consumir contexto significativo.

Para tarefas que precisam de paralelismo sustentado ou excedem sua janela de contexto, [equipes de agentes](#parte-2-orquestre-equipes-de-sessões-claude-code) dão a cada trabalhador seu próprio contexto independente.

#### Encadeie subagentes

Para fluxos de trabalho multi-etapas, peça a Claude para usar subagentes em sequência. Cada subagente completa sua tarefa e retorna resultados para Claude, que então passa contexto relevante para o próximo subagente.

```
Use the code-reviewer subagent to find performance issues, then use the optimizer subagent to fix them
```

### Escolha entre subagentes e conversa principal

**Use a conversa principal quando:**

- A tarefa precisa de frequente ida e volta ou refinamento iterativo
- Múltiplas fases compartilham contexto significativo (planejamento → implementação → testes)
- Você está fazendo uma mudança rápida e direcionada
- Latência importa — subagentes começam do zero e podem precisar de tempo para reunir contexto

**Use subagentes quando:**

- A tarefa produz saída verbosa que você não precisa em seu contexto principal
- Você quer aplicar restrições de ferramentas específicas ou permissões
- O trabalho é auto-contido e pode retornar um resumo

Considere Skills em vez disso quando você quer prompts reutilizáveis ou fluxos de trabalho que são executados no contexto da conversa principal em vez de contexto de subagente isolado.

> **Nota:** Subagentes não podem gerar outros subagentes. Se seu fluxo de trabalho requer delegação aninhada, use Skills ou encadeie subagentes da conversa principal.

### Gerencie o contexto do subagente

#### Retome subagentes

Cada invocação de subagente cria uma nova instância com contexto fresco. Para continuar o trabalho de um subagente existente em vez de começar do zero, peça a Claude para retomá-lo.

Subagentes retomados retêm seu histórico de conversa completo, incluindo todas as chamadas de ferramenta anteriores, resultados e raciocínio. O subagente continua exatamente de onde parou em vez de começar do zero.

Quando um subagente é concluído, Claude recebe seu ID de agente. Para retomar um subagente, peça a Claude para continuar o trabalho anterior:

```
Use the code-reviewer subagent to review the authentication module
[Agent completes]

Continue that code review and now analyze the authorization logic
[Claude resumes the subagent with full context from previous conversation]
```

Você também pode pedir a Claude pelo ID do agente se quiser referenciá-lo explicitamente, ou encontrar IDs nos arquivos de transcrição em `~/.claude/projects/{project}/{sessionId}/subagents/`. Cada transcrição é armazenada como `agent-{agentId}.jsonl`.

**Persistência de transcrições de subagente:**

- **Compactação da conversa principal:** Quando a conversa principal se compacta, transcrições de subagente não são afetadas. Elas são armazenadas em arquivos separados.
- **Persistência de sessão:** Transcrições de subagente persistem dentro de sua sessão. Você pode retomar um subagente após reiniciar Claude Code retomando a mesma sessão.
- **Limpeza automática:** Transcrições são limpas baseado na configuração `cleanupPeriodDays` (padrão: 30 dias).

#### Auto-compactação

Subagentes suportam compactação automática usando a mesma lógica que a conversa principal. Por padrão, auto-compactação é acionada em aproximadamente 95% de capacidade. Para acionar compactação mais cedo, defina `CLAUDE_AUTOCOMPACT_PCT_OVERRIDE` para uma porcentagem mais baixa (por exemplo, `50`).

Eventos de compactação são registrados em arquivos de transcrição de subagente:

```json
{
  "type": "system",
  "subtype": "compact_boundary",
  "compactMetadata": {
    "trigger": "auto",
    "preTokens": 167189
  }
}
```

O valor `preTokens` mostra quantos tokens foram usados antes da compactação ocorrer.

---

## Subagentes de Exemplo

Estes exemplos demonstram padrões eficazes para construir subagentes. Use-os como pontos de partida, ou gere uma versão personalizada com Claude.

> **Melhores práticas:**
>
> - **Projete subagentes focados:** cada subagente deve se destacar em uma tarefa específica
> - **Escreva descrições detalhadas:** Claude usa a descrição para decidir quando delegar
> - **Limite o acesso a ferramentas:** conceda apenas permissões necessárias para segurança e foco
> - **Verifique no controle de versão:** compartilhe subagentes de projeto com sua equipe

### Revisor de código

Um subagente somente leitura que revisa código sem modificá-lo. Este exemplo mostra como projetar um subagente focado com acesso limitado a ferramentas (sem Edit ou Write) e um prompt detalhado que especifica exatamente o que procurar e como formatar a saída.

```markdown
---
name: code-reviewer
description: Expert code review specialist. Proactively reviews code for quality, security, and maintainability. Use immediately after writing or modifying code.
tools: Read, Grep, Glob, Bash
model: inherit
---

You are a senior code reviewer ensuring high standards of code quality and security.

When invoked:
1. Run git diff to see recent changes
2. Focus on modified files
3. Begin review immediately

Review checklist:
- Code is clear and readable
- Functions and variables are well-named
- No duplicated code
- Proper error handling
- No exposed secrets or API keys
- Input validation implemented
- Good test coverage
- Performance considerations addressed

Provide feedback organized by priority:
- Critical issues (must fix)
- Warnings (should fix)
- Suggestions (consider improving)

Include specific examples of how to fix issues.
```

### Depurador

Um subagente que pode analisar e corrigir problemas. Diferentemente do revisor de código, este inclui Edit porque corrigir bugs requer modificar código. O prompt fornece um fluxo de trabalho claro de diagnóstico para verificação.

```markdown
---
name: debugger
description: Debugging specialist for errors, test failures, and unexpected behavior. Use proactively when encountering any issues.
tools: Read, Edit, Bash, Grep, Glob
---

You are an expert debugger specializing in root cause analysis.

When invoked:
1. Capture error message and stack trace
2. Identify reproduction steps
3. Isolate the failure location
4. Implement minimal fix
5. Verify solution works

Debugging process:
- Analyze error messages and logs
- Check recent code changes
- Form and test hypotheses
- Add strategic debug logging
- Inspect variable states

For each issue, provide:
- Root cause explanation
- Evidence supporting the diagnosis
- Specific code fix
- Testing approach
- Prevention recommendations

Focus on fixing the underlying issue, not the symptoms.
```

### Cientista de dados

Um subagente específico de domínio para trabalho de análise de dados. Este exemplo mostra como criar subagentes para fluxos de trabalho especializados fora de tarefas de codificação típicas. Ele explicitamente define `model: sonnet` para análise mais capaz.

```markdown
---
name: data-scientist
description: Data analysis expert for SQL queries, BigQuery operations, and data insights. Use proactively for data analysis tasks and queries.
tools: Bash, Read, Write
model: sonnet
---

You are a data scientist specializing in SQL and BigQuery analysis.

When invoked:
1. Understand the data analysis requirement
2. Write efficient SQL queries
3. Use BigQuery command line tools (bq) when appropriate
4. Analyze and summarize results
5. Present findings clearly

Key practices:
- Write optimized SQL queries with proper filters
- Use appropriate aggregations and joins
- Include comments explaining complex logic
- Format results for readability
- Provide data-driven recommendations

For each analysis:
- Explain the query approach
- Document any assumptions
- Highlight key findings
- Suggest next steps based on data

Always ensure queries are efficient and cost-effective.
```

### Validador de consulta de banco de dados

Um subagente que permite acesso Bash, mas valida comandos para permitir apenas consultas SQL somente leitura. Este exemplo mostra como usar hooks `PreToolUse` para validação condicional quando você precisa de controle mais fino do que o campo `tools` fornece.

```markdown
---
name: db-reader
description: Execute read-only database queries. Use when analyzing data or generating reports.
tools: Bash
hooks:
  PreToolUse:
    - matcher: "Bash"
      hooks:
        - type: command
          command: "./scripts/validate-readonly-query.sh"
---

You are a database analyst with read-only access. Execute SELECT queries to answer questions about the data.

When asked to analyze data:
1. Identify which tables contain the relevant data
2. Write efficient SELECT queries with appropriate filters
3. Present results clearly with context

You cannot modify data. If asked to INSERT, UPDATE, DELETE, or modify schema, explain that you only have read access.
```

Claude Code passa entrada de hook como JSON via stdin para comandos de hook. O script de validação lê este JSON, extrai o comando sendo executado e o verifica contra uma lista de operações de escrita SQL. Se uma operação de escrita for detectada, o script sai com código 2 para bloquear a execução e retorna uma mensagem de erro para Claude via stderr.

Crie o script de validação em qualquer lugar em seu projeto. O caminho deve corresponder ao campo `command` em sua configuração de hook:

```bash
#!/bin/bash
# Blocks SQL write operations, allows SELECT queries

# Read JSON input from stdin
INPUT=$(cat)

# Extract the command field from tool_input using jq
COMMAND=$(echo "$INPUT" | jq -r '.tool_input.command // empty')

if [ -z "$COMMAND" ]; then
  exit 0
fi

# Block write operations (case-insensitive)
if echo "$COMMAND" | grep -iE '\b(INSERT|UPDATE|DELETE|DROP|CREATE|ALTER|TRUNCATE|REPLACE|MERGE)\b' > /dev/null; then
  echo "Blocked: Write operations not allowed. Use SELECT queries only." >&2
  exit 2
fi

exit 0
```

Torne o script executável:

```bash
chmod +x ./scripts/validate-readonly-query.sh
```

O hook recebe JSON via stdin com o comando Bash em `tool_input.command`. Código de saída 2 bloqueia a operação e alimenta a mensagem de erro de volta para Claude. Consulte Hooks para detalhes sobre códigos de saída e Entrada de Hook para o esquema de entrada completo.

---

## Próximos Passos (Subagentes)

Agora que você entende subagentes, explore esses recursos relacionados:

- Distribua subagentes com plugins para compartilhar subagentes entre equipes ou projetos
- Execute Claude Code programaticamente com o Agent SDK para CI/CD e automação
- Use MCP servers para dar aos subagentes acesso a ferramentas externas e dados

---
---

# Parte 2: Orquestre Equipes de Sessões Claude Code

> Coordene múltiplas instâncias Claude Code trabalhando juntas como uma equipe, com tarefas compartilhadas, mensagens entre agentes e gerenciamento centralizado.

> **Experimental:** Equipes de agentes são experimentais e desabilitadas por padrão. Ative-as adicionando `CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS` ao seu `settings.json` ou ambiente. Equipes de agentes têm limitações conhecidas em torno da retomada de sessão, coordenação de tarefas e comportamento de encerramento.

Equipes de agentes permitem que você coordene múltiplas instâncias Claude Code trabalhando juntas. Uma sessão atua como o **líder da equipe**, coordenando o trabalho, atribuindo tarefas e sintetizando resultados. Os companheiros de equipe trabalham independentemente, cada um em sua própria janela de contexto, e se comunicam diretamente uns com os outros.

Diferentemente de subagentes, que são executados dentro de uma única sessão e podem apenas relatar de volta ao agente principal, você também pode interagir com companheiros de equipe individuais diretamente sem passar pelo líder.

**Esta seção cobre:**

- Quando usar equipes de agentes, incluindo os melhores casos de uso e como elas se comparam com subagentes
- Iniciando uma equipe
- Controlando companheiros de equipe, incluindo modos de exibição, atribuição de tarefas e delegação
- Melhores práticas para trabalho paralelo

---

## Quando Usar Equipes de Agentes

Equipes de agentes são mais eficazes para tarefas onde a exploração paralela adiciona valor real. Os casos de uso mais fortes são:

- **Pesquisa e revisão:** múltiplos companheiros de equipe podem investigar diferentes aspectos de um problema simultaneamente, depois compartilhar e desafiar as descobertas uns dos outros
- **Novos módulos ou recursos:** companheiros de equipe podem possuir cada um uma peça separada sem se atrapalharem
- **Depuração com hipóteses concorrentes:** companheiros de equipe testam diferentes teorias em paralelo e convergem para a resposta mais rapidamente
- **Coordenação entre camadas:** mudanças que abrangem frontend, backend e testes, cada uma de propriedade de um companheiro de equipe diferente

Equipes de agentes adicionam sobrecarga de coordenação e usam significativamente mais tokens do que uma única sessão. Elas funcionam melhor quando os companheiros de equipe podem operar independentemente. Para tarefas sequenciais, edições do mesmo arquivo ou trabalho com muitas dependências, uma única sessão ou subagentes são mais eficazes.

### Comparar com subagentes

Tanto equipes de agentes quanto subagentes permitem paralelizar o trabalho, mas operam de forma diferente. Escolha com base em se seus trabalhadores precisam se comunicar uns com os outros:

| Aspecto | Subagentes | Equipes de Agentes |
| :--- | :--- | :--- |
| **Contexto** | Janela de contexto própria; resultados retornam ao chamador | Janela de contexto própria; totalmente independente |
| **Comunicação** | Relatar resultados de volta ao agente principal apenas | Companheiros de equipe se mensageiam diretamente |
| **Coordenação** | Agente principal gerencia todo o trabalho | Lista de tarefas compartilhada com auto-coordenação |
| **Melhor para** | Tarefas focadas onde apenas o resultado importa | Trabalho complexo que requer discussão e colaboração |
| **Custo de token** | Menor: resultados resumidos de volta ao contexto principal | Maior: cada companheiro de equipe é uma instância Claude separada |

**Regra geral:** Use subagentes quando você precisa de trabalhadores rápidos e focados que relatem de volta. Use equipes de agentes quando os companheiros de equipe precisam compartilhar descobertas, desafiar uns aos outros e se coordenar por conta própria.

---

## Ativar Equipes de Agentes

Equipes de agentes são desabilitadas por padrão. Ative-as definindo a variável de ambiente `CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS` como `1`, seja no seu ambiente de shell ou através de `settings.json`:

```json
{
  "env": {
    "CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS": "1"
  }
}
```

---

## Inicie Sua Primeira Equipe de Agentes

Após ativar equipes de agentes, diga ao Claude para criar uma equipe de agentes e descreva a tarefa e a estrutura da equipe que você deseja em linguagem natural. Claude cria a equipe, gera companheiros de equipe e coordena o trabalho com base no seu prompt.

Este exemplo funciona bem porque os três papéis são independentes e podem explorar o problema sem esperar um pelo outro:

```
I'm designing a CLI tool that helps developers track TODO comments across
their codebase. Create an agent team to explore this from different angles: one
teammate on UX, one on technical architecture, one playing devil's advocate.
```

A partir daí, Claude cria uma equipe com uma lista de tarefas compartilhada, gera companheiros de equipe para cada perspectiva, faz com que explorem o problema, sintetiza descobertas e tenta limpar a equipe quando terminar.

O terminal do líder lista todos os companheiros de equipe e no que estão trabalhando. Use **Shift+Up/Down** para selecionar um companheiro de equipe e enviar uma mensagem diretamente.

---

## Controle Sua Equipe de Agentes

Diga ao líder o que você quer em linguagem natural. Ele lida com coordenação de equipe, atribuição de tarefas e delegação com base em suas instruções.

### Escolha um modo de exibição

Equipes de agentes suportam dois modos de exibição:

- **In-process:** todos os companheiros de equipe são executados dentro do seu terminal principal. Use Shift+Up/Down para selecionar um companheiro de equipe e digite para enviar uma mensagem diretamente. Funciona em qualquer terminal, nenhuma configuração extra necessária.
- **Split panes:** cada companheiro de equipe recebe seu próprio painel. Você pode ver a saída de todos de uma vez e clicar em um painel para interagir diretamente. Requer tmux ou iTerm2.

> **Nota:** `tmux` tem limitações conhecidas em certos sistemas operacionais e tradicionalmente funciona melhor no macOS. Usar `tmux -CC` no iTerm2 é o ponto de entrada sugerido para `tmux`.

O padrão é `"auto"`, que usa split panes se você já estiver executando dentro de uma sessão tmux, e in-process caso contrário. A configuração `"tmux"` ativa o modo split-pane e detecta automaticamente se deve usar tmux ou iTerm2 com base no seu terminal.

Para substituir, defina `teammateMode` no seu `settings.json`:

```json
{
  "teammateMode": "in-process"
}
```

Para forçar o modo in-process para uma única sessão, passe como um sinalizador:

```bash
claude --teammate-mode in-process
```

**Instalação do modo split-pane:**

- **tmux:** instale através do gerenciador de pacotes do seu sistema. Veja o [tmux wiki](https://github.com/tmux/tmux/wiki/Installing) para instruções específicas da plataforma.
- **iTerm2:** instale o [it2 CLI](https://github.com/mkusaka/it2), depois ative a API Python em iTerm2 → Settings → General → Magic → Enable Python API.

### Especifique companheiros de equipe e modelos

Claude decide o número de companheiros de equipe a gerar com base em sua tarefa, ou você pode especificar exatamente o que deseja:

```
Create a team with 4 teammates to refactor these modules in parallel.
Use Sonnet for each teammate.
```

### Exigir aprovação de plano para companheiros de equipe

Para tarefas complexas ou arriscadas, você pode exigir que os companheiros de equipe planejem antes de implementar. O companheiro de equipe trabalha em modo de plano somente leitura até que o líder aprove sua abordagem:

```
Spawn an architect teammate to refactor the authentication module.
Require plan approval before they make any changes.
```

Quando um companheiro de equipe termina o planejamento, ele envia uma solicitação de aprovação de plano ao líder. O líder revisa o plano e o aprova ou o rejeita com feedback. Se rejeitado, o companheiro de equipe permanece em modo de plano, revisa com base no feedback e resubmete. Uma vez aprovado, o companheiro de equipe sai do modo de plano e começa a implementação.

O líder toma decisões de aprovação autonomamente. Para influenciar o julgamento do líder, dê a ele critérios no seu prompt, como "apenas aprove planos que incluam cobertura de teste" ou "rejeite planos que modifiquem o esquema do banco de dados".

### Use modo delegado

Sem modo delegado, o líder às vezes começa a implementar tarefas por conta própria em vez de esperar pelos companheiros de equipe. O modo delegado evita isso restringindo o líder a ferramentas apenas de coordenação: geração, mensagens, encerramento de companheiros de equipe e gerenciamento de tarefas.

Isso é útil quando você quer que o líder se concentre inteiramente em orquestração, como dividir o trabalho, atribuir tarefas e sintetizar resultados, sem tocar no código diretamente.

Para ativar, inicie uma equipe primeiro, depois pressione **Shift+Tab** para alternar para o modo delegado.

### Converse com companheiros de equipe diretamente

Cada companheiro de equipe é uma sessão Claude Code completa e independente. Você pode enviar uma mensagem para qualquer companheiro de equipe diretamente para dar instruções adicionais, fazer perguntas de acompanhamento ou redirecionar sua abordagem.

- **Modo in-process:** use Shift+Up/Down para selecionar um companheiro de equipe, depois digite para enviar uma mensagem. Pressione Enter para visualizar a sessão de um companheiro de equipe, depois Escape para interromper seu turno atual. Pressione Ctrl+T para alternar a lista de tarefas.
- **Modo split-pane:** clique no painel de um companheiro de equipe para interagir com sua sessão diretamente. Cada companheiro de equipe tem uma visualização completa de seu próprio terminal.

### Atribuir e reivindicar tarefas

A lista de tarefas compartilhada coordena o trabalho em toda a equipe. O líder cria tarefas e os companheiros de equipe trabalham através delas. As tarefas têm três estados: **pendente**, **em progresso** e **concluída**. As tarefas também podem depender de outras tarefas: uma tarefa pendente com dependências não resolvidas não pode ser reivindicada até que essas dependências sejam concluídas.

O líder pode atribuir tarefas explicitamente ou os companheiros de equipe podem auto-reivindicar:

- **Líder atribui:** diga ao líder qual tarefa dar a qual companheiro de equipe
- **Auto-reivindicar:** após terminar uma tarefa, um companheiro de equipe pega a próxima tarefa não atribuída e desbloqueada por conta própria

A reivindicação de tarefas usa bloqueio de arquivo para evitar condições de corrida quando múltiplos companheiros de equipe tentam reivindicar a mesma tarefa simultaneamente.

### Encerre companheiros de equipe

Para encerrar graciosamente a sessão de um companheiro de equipe:

```
Ask the researcher teammate to shut down
```

O líder envia uma solicitação de encerramento. O companheiro de equipe pode aprovar, saindo graciosamente, ou rejeitar com uma explicação.

### Limpe a equipe

Quando terminar, peça ao líder para limpar:

```
Clean up the team
```

Isso remove os recursos compartilhados da equipe. Quando o líder executa a limpeza, ele verifica se há companheiros de equipe ativos e falha se algum ainda estiver em execução, então encerre-os primeiro.

> **Importante:** Sempre use o líder para limpar. Os companheiros de equipe não devem executar limpeza porque seu contexto de equipe pode não ser resolvido corretamente, deixando potencialmente recursos em um estado inconsistente.

### Enforce quality gates com hooks

Use hooks para aplicar regras quando companheiros de equipe terminam trabalho ou tarefas são concluídas:

- **`TeammateIdle`:** executa quando um companheiro de equipe está prestes a ficar inativo. Saia com código 2 para enviar feedback e manter o companheiro de equipe trabalhando.
- **`TaskCompleted`:** executa quando uma tarefa está sendo marcada como completa. Saia com código 2 para impedir a conclusão e enviar feedback.

---

## Como Funcionam as Equipes de Agentes

Esta seção cobre a arquitetura e a mecânica por trás das equipes de agentes.

### Como Claude inicia equipes de agentes

Existem duas maneiras pelas quais as equipes de agentes começam:

1. **Você solicita uma equipe:** dê ao Claude uma tarefa que se beneficie do trabalho paralelo e solicite explicitamente uma equipe de agentes. Claude cria uma com base em suas instruções.
2. **Claude propõe uma equipe:** se Claude determinar que sua tarefa se beneficiaria do trabalho paralelo, ele pode sugerir criar uma equipe. Você confirma antes que ele proceda.

Em ambos os casos, você permanece no controle. Claude não criará uma equipe sem sua aprovação.

### Arquitetura

Uma equipe de agentes consiste em:

| Componente | Papel |
| :--- | :--- |
| **Líder da equipe** | A sessão Claude Code principal que cria a equipe, gera companheiros de equipe e coordena o trabalho |
| **Companheiros de equipe** | Instâncias Claude Code separadas que cada uma trabalha em tarefas atribuídas |
| **Lista de tarefas** | Lista compartilhada de itens de trabalho que os companheiros de equipe reivindicam e completam |
| **Caixa de correio** | Sistema de mensagens para comunicação entre agentes |

O sistema gerencia dependências de tarefas automaticamente. Quando um companheiro de equipe completa uma tarefa da qual outras tarefas dependem, as tarefas bloqueadas são desbloqueadas sem intervenção manual.

**Armazenamento local:**

- Configuração da equipe: `~/.claude/teams/{team-name}/config.json`
- Lista de tarefas: `~/.claude/tasks/{team-name}/`

A configuração da equipe contém um array `members` com o nome de cada companheiro de equipe, ID do agente e tipo de agente. Os companheiros de equipe podem ler este arquivo para descobrir outros membros da equipe.

### Permissões

Os companheiros de equipe começam com as configurações de permissão do líder. Se o líder for executado com `--dangerously-skip-permissions`, todos os companheiros de equipe também serão. Após a geração, você pode alterar modos de companheiros de equipe individuais, mas não pode definir modos por companheiro de equipe no momento da geração.

### Contexto e comunicação

Cada companheiro de equipe tem sua própria janela de contexto. Quando gerado, um companheiro de equipe carrega o mesmo contexto de projeto que uma sessão regular: CLAUDE.md, servidores MCP e skills. Ele também recebe o prompt de geração do líder. O histórico de conversa do líder **não** é transferido.

**Como os companheiros de equipe compartilham informações:**

- **Entrega automática de mensagens:** quando os companheiros de equipe enviam mensagens, elas são entregues automaticamente aos destinatários. O líder não precisa pesquisar atualizações.
- **Notificações de inatividade:** quando um companheiro de equipe termina e para, ele notifica automaticamente o líder.
- **Lista de tarefas compartilhada:** todos os agentes podem ver o status da tarefa e reivindicar trabalho disponível.

**Tipos de mensagens entre companheiros de equipe:**

- **message:** enviar uma mensagem para um companheiro de equipe específico
- **broadcast:** enviar para todos os companheiros de equipe simultaneamente. Use com moderação, pois os custos aumentam com o tamanho da equipe.

### Uso de tokens

Equipes de agentes usam significativamente mais tokens do que uma única sessão. Cada companheiro de equipe tem sua própria janela de contexto, e o uso de tokens aumenta com o número de companheiros de equipe ativos. Para pesquisa, revisão e trabalho de novos recursos, os tokens extras geralmente valem a pena. Para tarefas rotineiras, uma única sessão é mais econômica.

---

## Exemplos de Casos de Uso

Estes exemplos mostram como as equipes de agentes lidam com tarefas onde a exploração paralela adiciona valor.

### Execute uma revisão de código paralela

Um único revisor tende a gravitar em torno de um tipo de problema por vez. Dividir critérios de revisão em domínios independentes significa que segurança, desempenho e cobertura de teste recebem atenção completa simultaneamente. O prompt atribui a cada companheiro de equipe uma lente distinta para que não se sobreponham:

```
Create an agent team to review PR #142. Spawn three reviewers:
- One focused on security implications
- One checking performance impact
- One validating test coverage
Have them each review and report findings.
```

Cada revisor trabalha a partir do mesmo PR, mas aplica um filtro diferente. O líder sintetiza descobertas em todos os três após terminarem.

### Investigue com hipóteses concorrentes

Quando a causa raiz é incerta, um único agente tende a encontrar uma explicação plausível e parar de procurar. O prompt combate isso tornando os companheiros de equipe explicitamente adversários: o trabalho de cada um não é apenas investigar sua própria teoria, mas desafiar as dos outros.

```
Users report the app exits after one message instead of staying connected.
Spawn 5 agent teammates to investigate different hypotheses. Have them talk to
each other to try to disprove each other's theories, like a scientific
debate. Update the findings doc with whatever consensus emerges.
```

A estrutura de debate é o mecanismo-chave aqui. A investigação sequencial sofre de ancoragem: uma vez que uma teoria é explorada, a investigação subsequente é tendenciosa em relação a ela. Com múltiplos investigadores independentes tentando ativamente desprovar uns aos outros, a teoria que sobrevive é muito mais provável de ser a causa raiz real.

---

## Melhores Práticas

### Dê aos companheiros de equipe contexto suficiente

Os companheiros de equipe carregam contexto de projeto automaticamente, incluindo CLAUDE.md, servidores MCP e skills, mas não herdam o histórico de conversa do líder. Inclua detalhes específicos da tarefa no prompt de geração:

```
Spawn a security reviewer teammate with the prompt: "Review the authentication module
at src/auth/ for security vulnerabilities. Focus on token handling, session
management, and input validation. The app uses JWT tokens stored in
httpOnly cookies. Report any issues with severity ratings."
```

### Dimensione tarefas apropriadamente

- **Muito pequeno:** sobrecarga de coordenação excede o benefício
- **Muito grande:** companheiros de equipe trabalham muito tempo sem check-ins, aumentando o risco de esforço desperdiçado
- **Bem dimensionado:** unidades auto-contidas que produzem um entregável claro, como uma função, um arquivo de teste ou uma revisão

O líder divide o trabalho em tarefas e as atribui aos companheiros de equipe automaticamente. Se não estiver criando tarefas suficientes, peça para dividir o trabalho em pedaços menores. Ter 5-6 tarefas por companheiro de equipe mantém todos produtivos e permite que o líder reatribua trabalho se alguém ficar preso.

### Espere os companheiros de equipe terminarem

Às vezes, o líder começa a implementar tarefas por conta própria em vez de esperar pelos companheiros de equipe. Se você notar isso:

```
Wait for your teammates to complete their tasks before proceeding
```

### Comece com pesquisa e revisão

Se você é novo em equipes de agentes, comece com tarefas que têm limites claros e não requerem escrever código: revisar um PR, pesquisar uma biblioteca ou investigar um bug. Essas tarefas mostram o valor da exploração paralela sem os desafios de coordenação que vêm com a implementação paralela.

### Evite conflitos de arquivo

Dois companheiros de equipe editando o mesmo arquivo leva a sobrescrita. Divida o trabalho para que cada companheiro de equipe possua um conjunto diferente de arquivos.

### Monitore e direcione

Verifique o progresso dos companheiros de equipe, redirecione abordagens que não estão funcionando e sintetize descobertas conforme chegam. Deixar uma equipe sem supervisão por muito tempo aumenta o risco de esforço desperdiçado.

---

## Solução de Problemas

### Companheiros de equipe não aparecem

Se os companheiros de equipe não aparecerem depois que você pedir ao Claude para criar uma equipe:

- No modo in-process, os companheiros de equipe podem já estar em execução, mas não visíveis. Pressione **Shift+Down** para alternar entre companheiros de equipe ativos.
- Verifique se a tarefa que você deu ao Claude era complexa o suficiente para justificar uma equipe. Claude decide se deve gerar companheiros de equipe com base na tarefa.
- Se você solicitou explicitamente split panes, certifique-se de que tmux está instalado e disponível no seu PATH:

```bash
which tmux
```

- Para iTerm2, verifique se o `it2` CLI está instalado e a API Python está ativada nas preferências do iTerm2.

### Muitos prompts de permissão

Solicitações de permissão de companheiros de equipe surgem para o líder, o que pode criar atrito. Pré-aprove operações comuns nas suas configurações de permissão antes de gerar companheiros de equipe para reduzir interrupções.

### Companheiros de equipe parando em erros

Os companheiros de equipe podem parar após encontrar erros em vez de se recuperar. Verifique sua saída usando Shift+Up/Down no modo in-process ou clicando no painel no modo split, depois:

- Dê a eles instruções adicionais diretamente
- Gere um companheiro de equipe de substituição para continuar o trabalho

### Líder encerra antes do trabalho estar pronto

O líder pode decidir que a equipe terminou antes de todas as tarefas estarem realmente completas. Se isso acontecer, diga a ele para continuar. Você também pode dizer ao líder para esperar os companheiros de equipe terminarem antes de prosseguir se ele começar a fazer trabalho em vez de delegar.

### Sessões tmux órfãs

Se uma sessão tmux persistir após o término da equipe, ela pode não ter sido totalmente limpa. Liste as sessões e mate a criada pela equipe:

```bash
tmux ls
tmux kill-session -t <session-name>
```

---

## Limitações

Equipes de agentes são experimentais. Limitações atuais a serem observadas:

- **Sem retomada de sessão com companheiros de equipe in-process:** `/resume` e `/rewind` não restauram companheiros de equipe in-process. Após retomar uma sessão, o líder pode tentar enviar mensagens para companheiros de equipe que não existem mais. Se isso acontecer, diga ao líder para gerar novos companheiros de equipe.
- **Status da tarefa pode atrasar:** os companheiros de equipe às vezes falham em marcar tarefas como concluídas, o que bloqueia tarefas dependentes. Se uma tarefa parecer presa, verifique se o trabalho está realmente pronto e atualize o status da tarefa manualmente ou diga ao líder para pressionar o companheiro de equipe.
- **Encerramento pode ser lento:** os companheiros de equipe terminam sua solicitação atual ou chamada de ferramenta antes de encerrar, o que pode levar tempo.
- **Uma equipe por sessão:** um líder pode gerenciar apenas uma equipe por vez. Limpe a equipe atual antes de iniciar uma nova.
- **Sem equipes aninhadas:** os companheiros de equipe não podem gerar suas próprias equipes ou companheiros de equipe. Apenas o líder pode gerenciar a equipe.
- **Líder é fixo:** a sessão que cria a equipe é o líder por sua vida útil. Você não pode promover um companheiro de equipe a líder ou transferir liderança.
- **Permissões definidas na geração:** todos os companheiros de equipe começam com o modo de permissão do líder. Você pode alterar modos de companheiros de equipe individuais após a geração, mas não pode definir modos por companheiro de equipe no momento da geração.
- **Split panes requerem tmux ou iTerm2:** o modo in-process padrão funciona em qualquer terminal. O modo split-pane não é suportado no terminal integrado do VS Code, Windows Terminal ou Ghostty.

> **Nota:** `CLAUDE.md` funciona normalmente: os companheiros de equipe leem arquivos `CLAUDE.md` de seu diretório de trabalho. Use isso para fornecer orientação específica do projeto a todos os companheiros de equipe.

---

## Próximos Passos (Equipes de Agentes)

Explore abordagens relacionadas para trabalho paralelo e delegação:

- **Delegação leve:** subagentes geram agentes auxiliares para pesquisa ou verificação dentro de sua sessão, melhor para tarefas que não precisam de coordenação entre agentes
- **Sessões paralelas manuais:** Git worktrees permitem que você execute múltiplas sessões Claude Code por conta própria sem coordenação de equipe automatizada
- **Comparar abordagens:** veja a comparação subagent vs agent team para um detalhamento lado a lado
