# Hooks de Terceiros

O Cursor oferece suporte ao carregamento de hooks de ferramentas de terceiros, garantindo compatibilidade com configurações de hooks já existentes de outros assistentes de programação com IA.

## Hooks do Claude Code

O Cursor pode carregar e executar hooks configurados para o Claude Code, permitindo que você use os mesmos scripts de hook em ambas as ferramentas.

### Requisitos

Para habilitar a compatibilidade com os hooks do Claude Code:

1. **Habilite Third-party skills** em Cursor Settings → Features → Third-party skills
2. O recurso precisa estar habilitado na sua conta

### Locais de configuração

Hooks do Claude Code são carregados nestes locais (em ordem de prioridade):

LocalCaminhoDescrição**Projeto local**`.claude/settings.local.json`Substituições específicas do projeto, ignoradas pelo Git**Projeto**`.claude/settings.json`Hooks em nível de projeto, versionados no repositório**Usuário**`~/.claude/settings.json`Hooks em nível de usuário, aplicados globalmente
### Ordem de prioridade

Quando hooks são configurados em vários locais, eles são combinados nesta ordem de prioridade (da mais alta para a mais baixa):

1. Hooks de Enterprise (implantação gerenciada)
2. Hooks de equipe (configurados no painel)
3. Hooks de projeto (`.cursor/hooks.json`)
4. Hooks de usuário (`~/.cursor/hooks.json`)
5. Projeto Claude local (`.claude/settings.local.json`)
6. Projeto Claude (`.claude/settings.json`)
7. Usuário Claude (`~/.claude/settings.json`)

Hooks com prioridade mais alta são executados primeiro, e qualquer hook pode bloquear a execução dos hooks de prioridade mais baixa.

### Formato de Hooks do Claude Code

Hooks do Claude Code usam um formato semelhante, mas levemente diferente. O Cursor associa automaticamente os nomes de hooks do Claude aos seus equivalentes no Cursor.

**Exemplo de settings.json do Claude Code:**

```
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Shell",
        "hooks": [
          {
            "type": "command",
            "command": "./hooks/validate-shell.sh"
          }
        ]
      }
    ],
    "PostToolUse": [
      {
        "matcher": ".*",
        "hooks": [
          {
            "type": "command",
            "command": "./hooks/audit.sh"
          }
        ]
      }
    ]
  }
}
```

### Mapeamento de etapas de hook

Os nomes de hooks do Claude Code são mapeados automaticamente para nomes de hooks do Cursor:

Hook do Claude CodeHook do Cursor`PreToolUse``preToolUse``PostToolUse``postToolUse``UserPromptSubmit``beforeSubmitPrompt``Stop``stop``SubagentStop``subagentStop``SessionStart``sessionStart``SessionEnd``sessionEnd``PreCompact``preCompact`
### Comportamento do código de saída

Tanto o Cursor quanto os hooks do Claude Code oferecem suporte ao código de saída `2` para bloquear uma ação. Isso garante um comportamento consistente ao compartilhar hooks entre ferramentas:

```
#!/bin/bash
# Bloqueia comandos perigosos
if [[ "$COMMAND" == *"rm -rf"* ]]; then
  echo '{"decision": "deny", "reason": "Destructive command blocked"}'
  exit 2
fi
echo '{"decision": "allow"}'
exit 0
```

- **Código de saída 0**: Hook concluído com sucesso, use a saída em JSON
- **Código de saída 2**: Bloqueia a ação (equivalente a `decision: "deny"`)
- **Outros códigos de saída**: Hook falhou, a ação prossegue (fail-open)

### Migração do Claude Code

Se você já tiver hooks do Claude Code, você pode:

1. **Continuar usando arquivos de configuração do Claude Code**: Ative as habilidades de terceiros e seus hooks existentes em `.claude/settings.json` funcionarão automaticamente
2. **Migrar para o formato do Cursor**: Copie seus hooks para `.cursor/hooks.json` usando o formato do Cursor para suporte completo a recursos

**Formato equivalente no Cursor:**

```
{
  "version": 1,
  "hooks": {
    "preToolUse": [
      {
        "command": "./hooks/validate-shell.sh",
        "matcher": "Shell"
      }
    ],
    "postToolUse": [
      {
        "command": "./hooks/audit.sh"
      }
    ]
  }
}
```

## Recursos com suporte

Ao usar hooks do Claude Code no Cursor, os seguintes recursos têm suporte:

Evento do Claude CodeMapeamento no CursorCompatível`PreToolUse``preToolUse`Sim`PostToolUse``postToolUse`Sim`Stop``stop`Sim`SubagentStop``subagentStop`Sim`SessionStart``sessionStart`Sim`SessionEnd``sessionEnd`Sim`PreCompact``preCompact`Sim`UserPromptSubmit``beforeSubmitPrompt`Sim`Notification`-Não`PermissionRequest`-Não
**Recursos adicionais com suporte:**

RecursoCompatívelHooks baseados em comando (`type: "command"`)SimHooks baseados em prompt (`type: "prompt"`)SimBloqueio com código de saída 2SimMatchers de ferramentas (padrões regex)SimConfiguração de tempo limiteSim
### Mapeamento de nomes de ferramentas

Os nomes das ferramentas do Claude Code são mapeados para os nomes das ferramentas do Cursor:

Claude Code ToolCursor ToolSuportado`Bash``Shell`Sim`Read``Read`Sim`Write``Write`Sim`Edit``Write`Sim`Grep``Grep`Sim`Task``Task`Sim`Glob`-Não`WebFetch`-Não`WebSearch`-Não
### Limitações

Alguns recursos só estão disponíveis ao usar o formato nativo do Cursor:

- Hook `subagentStart` (Claude Code só possui `SubagentStop`)
- Configuração de limite de iterações (loop) (`loop_limit`)
- Distribuição de hooks em equipes/empresas via dashboard

## Solução de problemas

**Hooks do Claude Code não carregando**

1. Verifique se "Third-party skills" está habilitado em Cursor Settings
2. Confira se seu arquivo `.claude/settings.json` é um JSON válido
3. Reinicie o Cursor depois de ativar a configuração

**Hooks sendo executados, mas não bloqueando**

1. Certifique-se de que seu script de hook saia com o código `2` para bloquear ações
2. Verifique se o formato de saída JSON corresponde ao esquema esperado
3. Consulte o canal de saída de Hooks no Cursor para ver detalhes de erros

**Comportamento diferente entre Cursor e Claude Code**

Algumas diferenças de comportamento podem existir devido a ambientes de execução diferentes. Teste seus hooks em ambas as ferramentas para garantir compatibilidade.