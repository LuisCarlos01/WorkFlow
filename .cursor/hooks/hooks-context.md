# Hooks

Hooks permitem observar, controlar e estender o loop do agente usando scripts personalizados. Hooks são processos separados que se comunicam via stdio usando JSON em ambas as direções. Eles são executados antes ou depois de estágios definidos do loop do agente e podem observar, bloquear ou modificar o comportamento.

Com hooks, você pode:

- Executar formatadores após edições
- Adicionar analytics de eventos
- Verificar PII (dados pessoais) ou segredos
- Controlar operações arriscadas (por exemplo, escritas em SQL)
- Controlar a execução de subagentes (ferramenta Task)
- Injetar contexto no início da sessão

Procurando integrações prontas para uso? Consulte [Partner Integrations](#partner-integrations) para soluções de segurança, governança e gerenciamento de segredos dos nossos parceiros do ecossistema.

O Cursor é compatível com o carregamento de hooks de ferramentas de terceiros, como o Claude Code. Consulte [Third Party Hooks](/docs/agent/third-party-hooks) para detalhes sobre compatibilidade e configuração.

## Suporte a Agent e Tab

Hooks funcionam tanto com o **Cursor Agent** (Cmd+K/Agent Chat) quanto com o **Cursor Tab** (compleções em linha), mas eles usam diferentes eventos de hooks:

**Agent (Cmd+K/Agent Chat)** usa os hooks padrão:

- `sessionStart` / `sessionEnd` - Gerenciamento do ciclo de vida da sessão
- `preToolUse` / `postToolUse` / `postToolUseFailure` - Hooks genéricos de uso de ferramenta (disparados para todas as ferramentas)
- `subagentStart` / `subagentStop` - Ciclo de vida do subagent (ferramenta Task)
- `beforeShellExecution` / `afterShellExecution` - Controlar comandos de shell
- `beforeMCPExecution` / `afterMCPExecution` - Controlar o uso de ferramentas MCP
- `beforeReadFile` / `afterFileEdit` - Controlar o acesso a arquivos e suas edições
- `beforeSubmitPrompt` - Validar prompts antes do envio
- `preCompact` - Observar a compactação da janela de contexto
- `stop` - Tratar a finalização do Agent
- `afterAgentResponse` / `afterAgentThought` - Acompanhar respostas do Agent

**Tab (compleções em linha)** usa hooks especializados:

- `beforeTabFileRead` - Controlar o acesso a arquivos para compleções do Tab
- `afterTabFileEdit` - Pós-processar edições do Tab

Esses hooks separados permitem definir políticas diferentes para operações autônomas do Tab versus operações orientadas pelo usuário no Agent.

## Início rápido

Crie um arquivo `hooks.json`. Você pode criá-lo no nível do projeto (`<project>/.cursor/hooks.json`) ou no seu diretório pessoal (`~/.cursor/hooks.json`). Hooks no nível do projeto se aplicam apenas a esse projeto específico, enquanto hooks no diretório pessoal se aplicam globalmente.

Hooks de usuário (~/.cursor/)Hooks de projeto (.cursor/)Para hooks em nível de usuário que se aplicam globalmente, crie `~/.cursor/hooks.json`:

```
{
  "version": 1,
  "hooks": {
    "afterFileEdit": [{ "command": "./hooks/format.sh" }]
  }
}
```

Crie seu script de hook em `~/.cursor/hooks/format.sh`:

```
#!/bin/bash
# Lê a entrada, faz algo, sai com 0
cat > /dev/null
exit 0
```

Deixe-o executável:

```
chmod +x ~/.cursor/hooks/format.sh
```

Reinicie o Cursor. Seu hook agora será executado após cada edição de arquivo.

## Tipos de Hook

Hooks suportam dois tipos de execução: baseada em comando (padrão) e baseada em prompt (avaliada por LLM).

### Hooks baseados em comandos

Hooks baseados em comandos executam scripts de shell que recebem entrada JSON pela stdin e retornam saída JSON pela stdout.

```
{
  "hooks": {
    "beforeShellExecution": [
      {
        "command": "./scripts/approve-network.sh",
        "timeout": 30,
        "matcher": "curl|wget|nc"
      }
    ]
  }
}
```

**Comportamento do código de saída:**

- Código de saída `0` - Hook concluído com sucesso, use a saída JSON
- Código de saída `2` - Bloqueia a ação (equivalente a retornar `permission: "deny"`)
- Outros códigos de saída - O hook falhou, a ação prossegue (fail-open por padrão)

### Hooks baseados em prompt

Hooks baseados em prompt usam um LLM para avaliar uma condição em linguagem natural. Eles são úteis para aplicar políticas sem precisar escrever scripts personalizados.

```
{
  "hooks": {
    "beforeShellExecution": [
      {
        "type": "prompt",
        "prompt": "Este comando parece seguro para executar? Permitir apenas operações de leitura.",
        "timeout": 10
      }
    ]
  }
}
```

**Funcionalidades:**

- Retorna uma resposta estruturada `{ ok: boolean, reason?: string }`
- Usa um modelo rápido para avaliação rápida
- O placeholder `$ARGUMENTS` é substituído automaticamente pelo JSON de entrada do hook
- Se `$ARGUMENTS` estiver ausente, a entrada do hook é adicionada automaticamente
- Campo opcional `model` para sobrescrever o modelo LLM padrão

## Exemplos

Os exemplos abaixo usam caminhos `./hooks/...`, que funcionam para **user hooks** (`~/.cursor/hooks.json`), nos quais os scripts são executados a partir de `~/.cursor/`. Para **project hooks** (`<project>/.cursor/hooks.json`), use caminhos `.cursor/hooks/...`, já que os scripts são executados a partir da raiz do projeto.

hooks.jsonaudit.shblock-git.sh```
{
  "version": 1,
  "hooks": {
    "sessionStart": [
      {
        "command": "./hooks/session-init.sh"
      }
    ],
    "sessionEnd": [
      {
        "command": "./hooks/audit.sh"
      }
    ],
    "beforeShellExecution": [
      {
        "command": "./hooks/audit.sh"
      },
      {
        "command": "./hooks/block-git.sh"
      }
    ],
    "beforeMCPExecution": [
      {
        "command": "./hooks/audit.sh"
      }
    ],
    "afterShellExecution": [
      {
        "command": "./hooks/audit.sh"
      }
    ],
    "afterMCPExecution": [
      {
        "command": "./hooks/audit.sh"
      }
    ],
    "afterFileEdit": [
      {
        "command": "./hooks/audit.sh"
      }
    ],
    "beforeSubmitPrompt": [
      {
        "command": "./hooks/audit.sh"
      }
    ],
    "preCompact": [
      {
        "command": "./hooks/audit.sh"
      }
    ],
    "stop": [
      {
        "command": "./hooks/audit.sh"
      }
    ],
    "beforeTabFileRead": [
      {
        "command": "./hooks/redact-secrets-tab.sh"
      }
    ],
    "afterTabFileEdit": [
      {
        "command": "./hooks/format-tab.sh"
      }
    ]
  }
}
```

### Hook de parada de automação em TypeScript

Escolha TypeScript quando você precisar de JSON tipado, I/O de arquivos persistente e chamadas HTTP no mesmo hook. Este hook `stop`, baseado em Bun, rastreia em disco as contagens de falhas por conversa, encaminha telemetria estruturada para uma API interna e pode agendar automaticamente uma nova tentativa quando o agente falha duas vezes seguidas.

hooks.json.cursor/hooks/track-stop.ts```
{
  "version": 1,
  "hooks": {
    "stop": [
      {
        "command": "bun run .cursor/hooks/track-stop.ts --stop"
      }
    ]
  }
}
```

Defina `AGENT_TELEMETRY_URL` como o endpoint interno que deve receber resumos de execução.

### Hook de proteção de manifests em Python

Python se destaca quando você precisa de bibliotecas ricas de parsing. Este hook usa `pyyaml` para inspecionar manifests do Kubernetes antes de `kubectl apply` ser executado; Bash teria dificuldade para fazer o parse com segurança de YAML com múltiplos documentos.

hooks.json.cursor/hooks/kube_guard.py```
{
  "version": 1,
  "hooks": {
    "beforeShellExecution": [
      {
        "command": "python3 .cursor/hooks/kube_guard.py"
      }
    ]
  }
}
```

Instale o PyYAML (por exemplo, `pip install pyyaml`) em qualquer lugar em que seus scripts de hook sejam executados para que a importação do parser funcione corretamente.

## Integrações com parceiros

Trabalhamos com parceiros do ecossistema que adicionaram suporte a hooks ao Cursor. Essas integrações abrangem análise de segurança, governança, gerenciamento de segredos e muito mais.

### Governança e visibilidade de MCP

PartnerDescription[MintMCP](https://www.mintmcp.com/blog/mcp-governance-cursor-hooks)Crie um inventário completo de servidores MCP, monitore padrões de uso de ferramentas e verifique respostas em busca de dados confidenciais antes que sejam enviados ao modelo de IA.[Oasis Security](https://www.oasis.security/blog/cursor-oasis-governing-agentic-access)Aplique políticas de mínimo privilégio às ações de agentes de IA e mantenha trilhas de auditoria completas em todos os sistemas corporativos.[Runlayer](https://www.runlayer.com/blog/cursor-hooks)Encapsule ferramentas MCP e integre-as ao broker MCP deles para controle centralizado e visibilidade das interações entre agentes e ferramentas.
### Segurança do código e boas práticas

ParceiroDescrição[Corridor](https://corridor.dev/blog/corridor-cursor-hooks/)Receba feedback em tempo real sobre a implementação do código e decisões de desenho de segurança enquanto o código é escrito.[Semgrep](https://semgrep.dev/blog/2025/cursor-hooks-mcp-server)Analise automaticamente código gerado por IA em busca de vulnerabilidades, com feedback em tempo real para regenerar o código até que os problemas de segurança sejam resolvidos.
### Segurança de dependências

ParceiroDescrição[Endor Labs](https://www.endorlabs.com/learn/bringing-malware-detection-into-ai-coding-workflows-with-cursor-hooks)Intercepte instalações de pacotes e analise-as em busca de dependências maliciosas, prevenindo ataques à cadeia de suprimentos de software antes que cheguem à sua base de código.
### Segurança e proteção dos agentes

ParceiroDescrição[Snyk](https://snyk.io/blog/evo-agent-guard-cursor-integration/)Monitore as ações dos agentes em tempo real com o Evo Agent Guard, detectando e prevenindo problemas como prompt injection e chamadas perigosas de ferramentas.
### Gerenciamento de segredos

ParceiroDescrição[1Password](https://marketplace.1password.com/integration/cursor-hooks)Valide que arquivos de ambiente do 1Password Environments estão devidamente montados antes da execução de comandos de shell, permitindo acesso just-in-time a segredos sem gravar credenciais em disco.
Para mais detalhes sobre nossos parceiros de hooks, consulte o post do blog [Hooks para equipes de segurança e plataforma](/blog/hooks-partners).

## Configuração

Defina hooks em um arquivo `hooks.json`. A configuração pode ser definida em vários níveis; fontes de maior prioridade substituem as de menor prioridade:

```
~/.cursor/
├── hooks.json
└── hooks/
    ├── audit.sh
    └── block-git.sh
```

- **Global** (gerenciado pela Enterprise):
- macOS: `/Library/Application Support/Cursor/hooks.json`
- Linux/WSL: `/etc/cursor/hooks.json`
- Windows: `C:\\ProgramData\\Cursor\\hooks.json`
- **Diretório do projeto** (específico do projeto):
- `<project-root>/.cursor/hooks.json`
- Hooks do projeto são executados em qualquer espaço de trabalho confiável e são versionados junto com o seu projeto
- **Diretório pessoal** (específico do usuário):
- `~/.cursor/hooks.json`

Ordem de prioridade (da mais alta para a mais baixa): Enterprise → Equipe → Projeto → Usuário

O objeto `hooks` mapeia nomes de hooks para arrays de definições de hooks. Cada definição atualmente oferece suporte a uma propriedade `command` que pode ser uma string de shell, um caminho absoluto ou um caminho relativo. O diretório de trabalho depende da origem do hook:

- **Hooks do projeto** (`.cursor/hooks.json` em um repositório): Executados a partir do **diretório raiz do projeto**
- **Hooks do usuário** (`~/.cursor/hooks.json`): Executados a partir de `~/.cursor/`
- **Hooks da Enterprise** (configuração em todo o sistema): Executados a partir do diretório de configuração da Enterprise
- **Hooks de equipe** (distribuídos pela nuvem): Executados a partir do diretório de hooks gerenciado

Para hooks de projeto, use caminhos como `.cursor/hooks/script.sh` (relativo ao diretório raiz do projeto), não `./hooks/script.sh` (que procuraria por `<project>/hooks/script.sh`).

### Arquivo de configuração

Este exemplo mostra um arquivo de hooks em nível de usuário (`~/.cursor/hooks.json`). Para hooks em nível de projeto, substitua caminhos como `./hooks/script.sh` por `.cursor/hooks/script.sh`:

```
{
  "version": 1,
  "hooks": {
    "sessionStart": [{ "command": "./session-init.sh" }],
    "sessionEnd": [{ "command": "./audit.sh" }],
    "preToolUse": [
      {
        "command": "./hooks/validate-tool.sh",
        "matcher": "Shell|Read|Write"
      }
    ],
    "postToolUse": [{ "command": "./hooks/audit-tool.sh" }],
    "subagentStart": [{ "command": "./hooks/validate-subagent.sh" }],
    "subagentStop": [{ "command": "./hooks/audit-subagent.sh" }],
    "beforeShellExecution": [{ "command": "./script.sh" }],
    "afterShellExecution": [{ "command": "./script.sh" }],
    "afterMCPExecution": [{ "command": "./script.sh" }],
    "afterFileEdit": [{ "command": "./format.sh" }],
    "preCompact": [{ "command": "./audit.sh" }],
    "stop": [{ "command": "./audit.sh", "loop_limit": 10 }],
    "beforeTabFileRead": [{ "command": "./redact-secrets-tab.sh" }],
    "afterTabFileEdit": [{ "command": "./format-tab.sh" }]
  }
}
```

Os hooks do agente (`sessionStart`, `sessionEnd`, `preToolUse`, `postToolUse`, `postToolUseFailure`, `subagentStart`, `subagentStop`, `beforeShellExecution`, `afterShellExecution`, `beforeMCPExecution`, `afterMCPExecution`, `beforeReadFile`, `afterFileEdit`, `beforeSubmitPrompt`, `preCompact`, `stop`, `afterAgentResponse`, `afterAgentThought`) aplicam-se às operações Cmd+K e Agent Chat. Os hooks do Tab (`beforeTabFileRead`, `afterTabFileEdit`) aplicam-se especificamente às completações Tab inline.

### Opções globais de configuração

OpçãoTipoPadrãoDescrição`version`number`1`Versão do esquema de configuração
### Opções de configuração por script

OpçãoTipoPadrãoDescrição`command`stringobrigatórioCaminho do script ou comando`type``"command"` | `"prompt"``"command"`Tipo de execução do hook`timeout`numberpadrão da plataformaTempo limite de execução em segundos`loop_limit`number | null`5`Limite de iterações por script para hooks `stop`/`subagentStop`. `null` significa sem limite. O padrão é `5` para hooks do Cursor e `null` para hooks do Claude Code.`matcher`object-Critérios de filtragem para quando o hook é executado
### Configuração de matchers

Os matchers permitem filtrar quando um hook é executado. O campo ao qual o matcher se aplica depende do hook:

```
{
  "hooks": {
    "preToolUse": [
      {
        "command": "./validate-shell.sh",
        "matcher": "Shell"
      }
    ],
    "subagentStart": [
      {
        "command": "./validate-explore.sh",
        "matcher": "explore|shell"
      }
    ],
    "beforeShellExecution": [
      {
        "command": "./approve-network.sh",
        "matcher": "curl|wget|nc "
      }
    ]
  }
}
```

- **subagentStart**: O matcher é aplicado ao **tipo de subagente** (por exemplo, `explore`, `shell`, `generalPurpose`). Use-o para executar hooks apenas quando um tipo específico de subagente é iniciado. O exemplo acima executa `validate-explore.sh` somente para subagentes explore ou shell.
- **beforeShellExecution**: O matcher é aplicado à string do **comando de shell**. Use-o para executar hooks apenas quando o comando corresponde a um padrão (por exemplo, chamadas de rede, exclusão de arquivos). O exemplo acima executa `approve-network.sh` somente quando o comando contém `curl`, `wget` ou `nc `.

**Matchers disponíveis por hook:**

- **preToolUse** (e outros hooks de ferramenta): Filtra por tipo de ferramenta — `Shell`, `Read`, `Write`, `Grep`, `LS`, `Delete`, `MCP`, `Task`, etc.
- **subagentStart**: Filtra por tipo de subagente — `generalPurpose`, `explore`, `shell`, etc.
- **beforeShellExecution**: Filtra pelo texto do comando de shell; o matcher é comparado com a string completa do comando.

## Distribuição na equipe

Hooks podem ser distribuídos aos membros da equipe por meio de hooks de projeto (via controle de versão), ferramentas de MDM ou pelo sistema de distribuição em nuvem do Cursor.

### Hooks de Projeto (Controle de Versão)

Hooks de projeto são a forma mais simples de compartilhar hooks com sua equipe. Coloque um arquivo `hooks.json` em `<project-root>/.cursor/hooks.json` e faça commit dele no seu repositório. Quando os membros da equipe abrirem o projeto em um espaço de trabalho confiável, o Cursor carregará e executará automaticamente os hooks do projeto.

Hooks de projeto:

- São armazenados no controle de versão junto com o código
- São carregados automaticamente para todos os membros da equipe em espaços de trabalho confiáveis
- Podem ser específicos do projeto (por exemplo, impor padrões de formatação para uma determinada base de código)
- Exigem que o espaço de trabalho seja confiável para serem executados (por segurança)

### Distribuição via MDM

Distribua hooks em toda a sua organização usando ferramentas de gerenciamento de dispositivos móveis (Mobile Device Management, MDM). Coloque o arquivo `hooks.json` e os scripts de hook nos diretórios de destino em cada máquina.

**Diretório pessoal do usuário** (distribuição por usuário):

- `~/.cursor/hooks.json`
- `~/.cursor/hooks/` (para scripts de hook)

**Diretórios globais** (distribuição em todo o sistema):

- macOS: `/Library/Application Support/Cursor/hooks.json`
- Linux/WSL: `/etc/cursor/hooks.json`
- Windows: `C:\\ProgramData\\Cursor\\hooks.json`

Observação: a distribuição baseada em MDM é totalmente gerenciada pela sua organização. O Cursor não distribui nem gerencia arquivos por meio da sua solução de MDM. Certifique-se de que sua equipe interna de TI ou de segurança cuide da configuração, distribuição e atualizações em conformidade com as políticas da sua organização.

### Distribuição em Nuvem (somente Enterprise)

Equipes Enterprise podem usar a distribuição em nuvem nativa do Cursor para sincronizar automaticamente hooks com todos os membros da equipe. Configure hooks no [painel web](https://cursor.com/dashboard?tab=team-content&section=hooks). O Cursor entrega automaticamente os hooks configurados para todas as máquinas clientes quando os membros da equipe fazem login.

A distribuição em nuvem oferece:

- Sincronização automática para todos os membros da equipe (a cada trinta minutos)
- Segmentação por sistema operacional para hooks específicos da plataforma
- Gerenciamento centralizado pelo painel

Administradores Enterprise podem criar, editar e gerenciar hooks de equipe pelo painel, sem precisar de acesso às máquinas individuais.

## Referência

### Esquema comum

#### Entrada (todos os hooks)

Todos os hooks recebem um conjunto básico de campos, além dos campos específicos de cada hook:

```
{
  "conversation_id": "string",
  "generation_id": "string",
  "model": "string",
  "hook_event_name": "string",
  "cursor_version": "string",
  "workspace_roots": ["<path>"],
  "user_email": "string | null",
  "transcript_path": "string | null"
}
```

FieldTypeDescription`conversation_id`stringID estável da conversa ao longo de vários turnos`generation_id`stringA geração atual, que muda a cada mensagem do usuário`model`stringO modelo configurado para o composer que acionou o hook`hook_event_name`stringQual hook está sendo executado`cursor_version`stringVersão do aplicativo Cursor (por exemplo, "1.7.2")`workspace_roots`string[]Lista de pastas raiz no workspace (normalmente apenas uma, mas workspaces multirraiz podem ter várias)`user_email`stringnullEndereço de e-mail do usuário autenticado, se disponível`transcript_path`stringnullCaminho para o arquivo principal de transcrição da conversa (null se as transcrições estiverem desativadas)
### Eventos de hook

#### preToolUse

Chamado antes da execução de qualquer ferramenta. Este é um hook genérico acionado para todos os tipos de ferramenta (Shell, Read, Write, MCP, Task, etc.). Use matchers para filtrar ferramentas específicas.

```
// Input
{
  "tool_name": "Shell",
  "tool_input": { "command": "npm install", "working_directory": "/project" },
  "tool_use_id": "abc123",
  "cwd": "/project",
  "model": "claude-sonnet-4-20250514",
  "agent_message": "Installing dependencies..."
}

// Output
{
  "decision": "allow" | "deny",
  "reason": "<reason shown to agent if denied>",
  "updated_input": { "command": "npm ci" }
}
```

Campo de saídaTipoDescrição`decision`string`"allow"` para prosseguir, `"deny"` para bloquear`reason`string (opcional)Explicação exibida ao agente quando a solicitação é negada`updated_input`object (opcional)Entrada de ferramenta modificada para usar em seu lugar
#### postToolUse

Chamado após a execução bem-sucedida de uma ferramenta. Útil para auditoria e análises.

```
// Input
{
  "tool_name": "Shell",
  "tool_input": { "command": "npm test" },
  "tool_output": "All tests passed",
  "tool_use_id": "abc123",
  "cwd": "/project",
  "duration": 5432,
  "model": "claude-sonnet-4-20250514"
}

// Output
{
  "updated_mcp_tool_output": { "modified": "output" }
}
```

Campo de entradaTipoDescrição`duration`numberTempo de execução em milissegundos`tool_output`stringSaída completa da ferramenta
Campo de saídaTipoDescrição`updated_mcp_tool_output`object (optional)Somente para ferramentas MCP: substitui a saída da ferramenta vista pelo modelo
#### postToolUseFailure

Chamado quando uma ferramenta falha, atinge o tempo limite ou é rejeitada. Útil para rastreamento de erros e lógica de recuperação.

```
// Input
{
  "tool_name": "Shell",
  "tool_input": { "command": "npm test" },
  "tool_use_id": "abc123",
  "cwd": "/project",
  "error_message": "Command timed out after 30s",
  "failure_type": "timeout" | "error" | "permission_denied",
  "duration": 5000,
  "is_interrupt": false
}

// Output
{
  // Nenhum campo de saída é suportado atualmente
}
```

Campo de entradaTipoDescrição`error_message`stringDescrição da falha`failure_type`stringTipo de falha: `"error"`, `"timeout"` ou `"permission_denied"``duration`numberTempo em milissegundos até a ocorrência da falha`is_interrupt`booleanIndica se a falha foi causada por uma interrupção/cancelamento do usuário
#### subagentStart

Chamado antes de criar um subagente (ferramenta Task). Pode permitir ou negar a criação do subagente.

```
// Input
{
  "subagent_type": "generalPurpose",
  "prompt": "Explore the authentication flow",
  "model": "claude-sonnet-4-20250514"
}

// Output
{
  "decision": "allow" | "deny",
  "reason": "<reason if denied>"
}
```

#### subagentStop

Chamado quando a execução de um subagente é concluída ou falha. Pode disparar ações subsequentes.

```
// Entrada
{
  "subagent_type": "generalPurpose",
  "status": "completed" | "error",
  "result": "<subagent output>",
  "duration": 45000,
  "agent_transcript_path": "/path/to/subagent/transcript.txt"
}

// Output
{
  "followup_message": "<auto-continue with this message>"
}
```

Campo de entradaTipoDescrição`subagent_type`stringTipo de subagente: `generalPurpose`, `explore`, `shell`, etc.`status`string`"completed"` ou `"error"``result`stringSaída/resultado do subagente`duration`numberTempo de execução em milissegundos`agent_transcript_path`stringnullCaminho para o próprio arquivo de transcrição do subagente (separado da conversa principal)
O campo `followup_message` permite fluxos em loop em que a conclusão do subagente dispara a próxima iteração.

#### beforeShellExecution / beforeMCPExecution

Chamado antes da execução de qualquer comando de shell ou ferramenta MCP. Retorne uma decisão de permissão.

`beforeMCPExecution` adota o comportamento **fail-closed**. Se o script do hook falhar ao ser executado (travar, expirar ou retornar JSON inválido), a chamada da ferramenta MCP será bloqueada. Isso garante que operações MCP não possam contornar os hooks configurados.

```
// beforeShellExecution input
{
  "command": "<comando completo do terminal>",
  "cwd": "<diretório de trabalho atual>",
  "timeout": 30
}

// beforeMCPExecution input
{
  "tool_name": "<nome da ferramenta>",
  "tool_input": "<parâmetros json>"
}
// Mais um dos seguintes:
{ "url": "<url do servidor>" }
// Ou:
{ "command": "<string de comando>" }

// Output
{
  "permission": "allow" | "deny" | "ask",
  "user_message": "<mensagem exibida no cliente>",
  "agent_message": "<mensagem enviada ao agente>"
}
```

#### afterShellExecution

É acionado depois que um comando de shell é executado; útil para auditoria ou para coletar métricas a partir da saída do comando.

```
// Entrada
{
  "command": "<comando completo do terminal>",
  "output": "<saída completa do terminal>",
  "duration": 1234
}
```

FieldTypeDescription`command`stringO comando completo de terminal que foi executado`output`stringSaída completa capturada no terminal`duration`numberTempo em milissegundos gasto na execução do comando de shell (não inclui o tempo de espera por aprovação)
#### afterMCPExecution

É disparado após a execução de uma ferramenta MCP; inclui os parâmetros de entrada da ferramenta e o resultado JSON completo.

```
// Entrada
{
  "tool_name": "<nome da ferramenta>",
  "tool_input": "<parâmetros json>",
  "result_json": "<json de resultado da ferramenta>",
  "duration": 1234
}
```

CampoTipoDescrição`tool_name`stringNome da ferramenta MCP que foi executada`tool_input`stringString JSON de parâmetros enviada para a ferramenta`result_json`stringString JSON com a resposta da ferramenta`duration`numberTempo, em milissegundos, gasto na execução da ferramenta MCP (não inclui o tempo de espera por aprovação)
#### afterFileEdit

É acionado depois que o Agent edita um arquivo; útil para formatadores ou para contabilizar o código escrito pelo Agent.

```
// Entrada
{
  "file_path": "<caminho absoluto>",
  "edits": [{ "old_string": "<busca>", "new_string": "<substitui>" }]
}
```

#### beforeReadFile

Chamado antes de o Agent ler um arquivo. Use para controle de acesso e para bloquear o envio de arquivos sensíveis ao modelo.

Este hook usa comportamento de **fail-closed**. Se o script do hook falhar na execução (travar, expirar ou retornar JSON inválido), a leitura do arquivo será bloqueada. Isso oferece garantias de segurança no acesso a arquivos sensíveis.

```
// Input
{
  "file_path": "<absolute path>",
  "content": "<file contents>",
  "attachments": [
    {
      "type": "file" | "rule",
      "filePath": "<absolute path>"
    }
  ]
}

// Output
{
  "permission": "allow" | "deny",
  "user_message": "<message shown when denied>"
}
```

Input FieldTypeDescription`file_path`stringCaminho absoluto para o arquivo a ser lido`content`stringConteúdo completo do arquivo`attachments`arrayAnexos de contexto associados ao prompt
Output FieldTypeDescription`permission`string`"allow"` para prosseguir, `"deny"` para bloquear`user_message`string (optional)Mensagem exibida ao usuário quando o acesso é negado
#### beforeTabFileRead

Chamado antes de o Tab (compleções inline) ler um arquivo. Habilite redação ou controle de acesso antes de o Tab acessar o conteúdo do arquivo.

**Principais diferenças em relação a `beforeReadFile`:**

- Acionado apenas pelo Tab, não pelo Agent
- Não inclui o campo `attachments` (o Tab não usa anexos de prompt)
- Útil para aplicar políticas diferentes a operações autônomas do Tab

```
// Entrada
{
  "file_path": "<caminho absoluto>",
  "content": "<conteúdo do arquivo>"
}

// Saída
{
  "permission": "allow" | "deny"
}
```

#### afterTabFileEdit

Chamado depois que o Tab (completações inline) edita um arquivo. Útil para formatadores ou para auditoria de código escrito pelo Tab.

**Principais diferenças em relação a `afterFileEdit`:**

- Acionado apenas pelo Tab, não pelo Agent
- Inclui informações detalhadas da edição: `range`, `old_line` e `new_line` para rastreamento preciso da edição
- Útil para formatação ou análise detalhada das edições do Tab

```
// Entrada
{
  "file_path": "<caminho absoluto>",
  "edits": [
    {
      "old_string": "<pesquisar>",
      "new_string": "<substituir>",
      "range": {
        "start_line_number": 10,
        "start_column": 5,
        "end_line_number": 10,
        "end_column": 20
      },
      "old_line": "<linha antes da edição>",
      "new_line": "<linha depois da edição>"
    }
  ]
}

// Saída
{
  // Nenhum campo de saída disponível no momento
}
```

#### beforeSubmitPrompt

Chamado logo depois que o usuário clica em Enviar, mas antes da requisição ao backend. Pode impedir o envio.

```
// Entrada
{
  "prompt": "<texto do prompt do usuário>",
  "attachments": [
    {
      "type": "file" | "rule",
      "filePath": "<caminho absoluto>"
    }
  ]
}

// Saída
{
  "continue": true | false,
  "user_message": "<mensagem exibida para o usuário quando bloqueado>"
}
```

Campo de saídaTipoDescrição`continue`booleanSe o envio do prompt pode prosseguir`user_message`string (optional)Mensagem exibida ao usuário quando o prompt é bloqueado
#### afterAgentResponse

Chamado após o agente concluir uma mensagem do assistente.

```
// Entrada
{
  "text": "<texto final do assistente>"
}
```

#### afterAgentThought

Chamado após o agente concluir um bloco de raciocínio. Útil para observar o processo de raciocínio do agente.

```
// Entrada
{
  "text": "<texto de raciocínio totalmente agregado>",
  "duration_ms": 5000
}

// Saída
{
  // Nenhum campo de saída disponível no momento
}
```

FieldTypeDescription`text`stringTexto de raciocínio totalmente agregado do bloco concluído`duration_ms`number (optional)Duração, em milissegundos, do bloco de raciocínio
#### stop

Chamado quando o loop do agente termina. Opcionalmente, pode enviar automaticamente uma mensagem de acompanhamento do usuário para continuar iterando.

```
// Entrada
{
  "status": "completed" | "aborted" | "error",
  "loop_count": 0
}
```

```
// Output
{
  "followup_message": "<texto da mensagem>"
}
```

- O `followup_message` opcional é uma string. Quando definido e não vazio, o Cursor o enviará automaticamente como a próxima mensagem do usuário. Isso permite fluxos em loop (por exemplo, iterar até que uma meta seja atingida).
- O campo `loop_count` indica quantas vezes o stop hook já acionou um follow-up automático para esta conversa (inicia em 0). Para evitar loops infinitos, é aplicado um máximo de 5 follow-ups automáticos.

#### sessionStart

Chamado quando uma nova conversa do Composer é criada. Use este hook para configurar variáveis de ambiente específicas da sessão, injetar contexto adicional ou bloquear a criação da sessão com base em políticas personalizadas.

```
// Input
{
  "session_id": "<unique session identifier>",
  "is_background_agent": true | false,
  "composer_mode": "agent" | "ask" | "edit"
}
```

```
// Output
{
  "env": { "<key>": "<value>" },
  "additional_context": "<contexto a adicionar à conversa>",
  "continue": true | false,
  "user_message": "<message shown if blocked>"
}
```

Input FieldTypeDescription`session_id`stringIdentificador único para esta sessão (mesmo que `conversation_id`)`is_background_agent`booleanIndica se esta é uma sessão de agente em segundo plano ou uma sessão interativa`composer_mode`string (optional)O modo em que o Composer está iniciando (por exemplo, "agent", "ask", "edit")
Output FieldTypeDescription`env`object (optional)Variáveis de ambiente a serem definidas para esta sessão. Disponíveis para todas as execuções de hooks subsequentes`additional_context`string (optional)Contexto adicional a ser incluído no contexto inicial de sistema da conversa`continue`boolean (optional)Indica se a criação da sessão deve continuar. Se false, a sessão não será criada. Padrão: true`user_message`string (optional)Mensagem a ser exibida para o usuário se `continue` for false
#### sessionEnd

Chamado quando uma conversa do composer termina. Este é um hook fire-and-forget, útil para logging, analytics ou tarefas de limpeza. A resposta é registrada, mas não é utilizada.

```
// Entrada
{
  "session_id": "<unique session identifier>",
  "reason": "completed" | "aborted" | "error" | "window_close" | "user_close",
  "duration_ms": 45000,
  "is_background_agent": true | false,
  "final_status": "<status string>",
  "error_message": "<error details if reason is 'error'>"
}
```

```
// Output
{
  // Sem campos de saída - dispara e esquece
}
```

Input FieldTypeDescription`session_id`stringIdentificador único da sessão que está terminando`reason`stringMotivo do término da sessão: "completed", "aborted", "error", "window_close" ou "user_close"`duration_ms`numberDuração total da sessão em milissegundos`is_background_agent`booleanIndica se esta foi uma sessão de agente em segundo plano`final_status`stringStatus final da sessão`error_message`string (optional)Mensagem de erro se o motivo for "error"
#### preCompact

Chamado antes da compactação/resumo da janela de contexto. Este é um hook apenas para observação, que não pode bloquear nem modificar o comportamento de compactação. Útil para registrar quando a compactação acontece ou para notificar usuários.

```
// Entrada
{
  "trigger": "auto" | "manual",
  "context_usage_percent": 85,
  "context_tokens": 120000,
  "context_window_size": 128000,
  "message_count": 45,
  "messages_to_compact": 30,
  "is_first_compaction": true | false
}
```

```
// Saída
{
  "user_message": "<message to show when compaction occurs>"
}
```

Campo de entradaTipoDescrição`trigger`stringO que acionou a compactação: "auto" ou "manual"`context_usage_percent`numberUso atual da janela de contexto, em porcentagem (0-100)`context_tokens`numberContagem atual de tokens na janela de contexto`context_window_size`numberTamanho máximo da janela de contexto em tokens`message_count`numberNúmero de mensagens na conversa`messages_to_compact`numberNúmero de mensagens que serão resumidas`is_first_compaction`booleanIndica se esta é a primeira compactação para esta conversa
Campo de saídaTipoDescrição`user_message`string (optional)Mensagem exibida ao usuário quando a compactação ocorre
## Variáveis de ambiente

Scripts de hook recebem variáveis de ambiente quando executados:

VariávelDescriçãoSempre presente`CURSOR_PROJECT_DIR`Diretório raiz do workspaceSim`CURSOR_VERSION`String de versão do CursorSim`CURSOR_USER_EMAIL`E-mail do usuário autenticadoSe estiver logado`CURSOR_CODE_REMOTE`Caminho de projeto com suporte a remotoPara workspaces remotos`CLAUDE_PROJECT_DIR`Alias para diretório do projeto (compatibilidade com Claude)Sim
Variáveis de ambiente com escopo de sessão, definidas por hooks `sessionStart`, são passadas para todas as execuções de hooks subsequentes dentro dessa sessão.

## Solução de problemas

**Como confirmar que os hooks estão ativos**

Há uma guia Hooks nas Configurações do Cursor para depurar hooks configurados e executados, além de um canal de saída de Hooks para ver erros.

**Se os hooks não estiverem funcionando**

- Reinicie o Cursor para garantir que o serviço de hooks esteja em execução.
- Verifique se os caminhos relativos estão corretos para a origem do seu hook:
- Para **hooks de projeto**, os caminhos são relativos à **raiz do projeto** (por exemplo, `.cursor/hooks/script.sh`)
- Para **hooks de usuário**, os caminhos são relativos a `~/.cursor/` (por exemplo, `./hooks/script.sh` ou `hooks/script.sh`)

**Bloqueio por código de saída**

O código de saída `2` de hooks de comando bloqueia a ação (equivalente a retornar `decision: "deny"`). Isso corresponde ao comportamento do Claude Code para compatibilidade.