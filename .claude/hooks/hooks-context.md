> **Documentation Index**
> Fetch the complete documentation index at: https://code.claude.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

---

# Comece com os Hooks do Claude Code

> Aprenda como personalizar e estender o comportamento do Claude Code registrando comandos shell.

Os hooks do Claude Code são comandos shell definidos pelo usuário que executam em vários pontos do ciclo de vida do Claude Code. Os hooks fornecem controle determinístico sobre o comportamento do Claude Code, garantindo que certas ações sempre aconteçam em vez de depender do LLM para escolher executá-las.

> **Dica:** Para documentação de referência sobre hooks, consulte Referência de Hooks.

**Casos de uso de exemplo para hooks:**

- **Notificações** — Personalize como você é notificado quando o Claude Code está aguardando sua entrada ou permissão para executar algo.
- **Formatação automática** — Execute `prettier` em arquivos .ts, `gofmt` em arquivos .go, etc. após cada edição de arquivo.
- **Logging** — Rastreie e conte todos os comandos executados para conformidade ou depuração.
- **Feedback** — Forneça feedback automatizado quando o Claude Code produz código que não segue as convenções da sua base de código.
- **Permissões personalizadas** — Bloqueie modificações em arquivos de produção ou diretórios sensíveis.

Ao codificar essas regras como hooks em vez de instruções de prompt, você transforma sugestões em código de nível de aplicativo que executa toda vez que se espera que seja executado.

> **Aviso:** Você deve considerar as implicações de segurança dos hooks conforme os adiciona, porque os hooks são executados automaticamente durante o loop do agente com as credenciais do ambiente atual. Por exemplo, código de hooks malicioso pode exfiltrar seus dados. Sempre revise sua implementação de hooks antes de registrá-los. Para as melhores práticas de segurança completas, consulte Considerações de Segurança na documentação de referência de hooks.

---

## Visão Geral dos Eventos de Hook

O Claude Code fornece vários eventos de hook que são executados em diferentes pontos do fluxo de trabalho:

| Evento | Quando executa | Pode |
| :--- | :--- | :--- |
| **PreToolUse** | Antes de chamadas de ferramenta | Bloquear chamadas |
| **PermissionRequest** | Quando um diálogo de permissão é mostrado | Permitir ou negar |
| **PostToolUse** | Após as chamadas de ferramenta serem concluídas | — |
| **UserPromptSubmit** | Quando o usuário envia um prompt, antes do Claude processá-lo | — |
| **Notification** | Quando o Claude Code envia notificações | — |
| **Stop** | Quando o Claude Code termina de responder | — |
| **SubagentStop** | Quando as tarefas do subagente são concluídas | — |
| **PreCompact** | Antes do Claude Code estar prestes a executar uma operação compacta | — |
| **SessionStart** | Quando o Claude Code inicia uma nova sessão ou retoma uma sessão existente | — |
| **SessionEnd** | Quando a sessão do Claude Code termina | — |

Cada evento recebe dados diferentes e pode controlar o comportamento do Claude de diferentes maneiras.

---

## Início Rápido

Neste início rápido, você adicionará um hook que registra os comandos shell que o Claude Code executa.

### Pré-requisitos

Instale `jq` para processamento JSON na linha de comando.

### Etapa 1: Abra a configuração de hooks

Execute o comando de barra `/hooks` e selecione o evento de hook `PreToolUse`.

Os hooks `PreToolUse` são executados antes de chamadas de ferramenta e podem bloqueá-las enquanto fornecem feedback do Claude sobre o que fazer de forma diferente.

### Etapa 2: Adicione um matcher

Selecione `+ Add new matcher…` para executar seu hook apenas em chamadas de ferramenta Bash.

Digite `Bash` para o matcher.

> **Nota:** Você pode usar `*` para corresponder a todas as ferramentas.

### Etapa 3: Adicione o hook

Selecione `+ Add new hook…` e digite este comando:

```bash
jq -r '"\(.tool_input.command) - \(.tool_input.description // "No description")"' >> ~/.claude/bash-command-log.txt
```

### Etapa 4: Salve sua configuração

Para o local de armazenamento, selecione `User settings` já que você está registrando em seu diretório inicial. Este hook será aplicado a todos os projetos, não apenas ao seu projeto atual.

Em seguida, pressione `Esc` até retornar ao REPL. Seu hook agora está registrado.

### Etapa 5: Verifique seu hook

Execute `/hooks` novamente ou verifique `~/.claude/settings.json` para ver sua configuração:

```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Bash",
        "hooks": [
          {
            "type": "command",
            "command": "jq -r '\"\\(.tool_input.command) - \\(.tool_input.description // \"No description\")\"' >> ~/.claude/bash-command-log.txt"
          }
        ]
      }
    ]
  }
}
```

### Etapa 6: Teste seu hook

Peça ao Claude para executar um comando simples como `ls` e verifique seu arquivo de log:

```bash
cat ~/.claude/bash-command-log.txt
```

Você deve ver entradas como:

```
ls - Lists files and directories
```

---

## Mais Exemplos

> **Nota:** Para uma implementação de exemplo completa, consulte o exemplo de validador de comando bash no repositório público da Anthropic.

### Hook de Formatação de Código

Formate automaticamente arquivos TypeScript após editar:

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Edit|Write",
        "hooks": [
          {
            "type": "command",
            "command": "jq -r '.tool_input.file_path' | { read file_path; if echo \"$file_path\" | grep -q '\\.ts$'; then npx prettier --write \"$file_path\"; fi; }"
          }
        ]
      }
    ]
  }
}
```

### Hook de Formatação de Markdown

Corrija automaticamente tags de idioma ausentes e problemas de formatação em arquivos markdown:

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Edit|Write",
        "hooks": [
          {
            "type": "command",
            "command": "\"$CLAUDE_PROJECT_DIR\"/.claude/hooks/markdown_formatter.py"
          }
        ]
      }
    ]
  }
}
```

Crie `.claude/hooks/markdown_formatter.py` com este conteúdo:

```python
#!/usr/bin/env python3
"""
Markdown formatter for Claude Code output.
Fixes missing language tags and spacing issues while preserving code content.
"""
import json
import sys
import re
import os

def detect_language(code):
    """Best-effort language detection from code content."""
    s = code.strip()

    # JSON detection
    if re.search(r'^\s*[{\[]', s):
        try:
            json.loads(s)
            return 'json'
        except:
            pass

    # Python detection
    if re.search(r'^\s*def\s+\w+\s*\(', s, re.M) or \
       re.search(r'^\s*(import|from)\s+\w+', s, re.M):
        return 'python'

    # JavaScript detection
    if re.search(r'\b(function\s+\w+\s*\(|const\s+\w+\s*=)', s) or \
       re.search(r'=>|console\.(log|error)', s):
        return 'javascript'

    # Bash detection
    if re.search(r'^#!.*\b(bash|sh)\b', s, re.M) or \
       re.search(r'\b(if|then|fi|for|in|do|done)\b', s):
        return 'bash'

    # SQL detection
    if re.search(r'\b(SELECT|INSERT|UPDATE|DELETE|CREATE)\s+', s, re.I):
        return 'sql'

    return 'text'

def format_markdown(content):
    """Format markdown content with language detection."""
    # Fix unlabeled code fences
    def add_lang_to_fence(match):
        indent, info, body, closing = match.groups()
        if not info.strip():
            lang = detect_language(body)
            return f"{indent}```{lang}\n{body}{closing}\n"
        return match.group(0)

    fence_pattern = r'(?ms)^([ \t]{0,3})```([^\n]*)\n(.*?)(\n\1```)\s*$'
    content = re.sub(fence_pattern, add_lang_to_fence, content)

    # Fix excessive blank lines (only outside code fences)
    content = re.sub(r'\n{3,}', '\n\n', content)

    return content.rstrip() + '\n'

# Main execution
try:
    input_data = json.load(sys.stdin)
    file_path = input_data.get('tool_input', {}).get('file_path', '')

    if not file_path.endswith(('.md', '.mdx')):
        sys.exit(0)  # Not a markdown file

    if os.path.exists(file_path):
        with open(file_path, 'r', encoding='utf-8') as f:
            content = f.read()

        formatted = format_markdown(content)

        if formatted != content:
            with open(file_path, 'w', encoding='utf-8') as f:
                f.write(formatted)
            print(f"✓ Fixed markdown formatting in {file_path}")

except Exception as e:
    print(f"Error formatting markdown: {e}", file=sys.stderr)
    sys.exit(1)
```

Torne o script executável:

```bash
chmod +x .claude/hooks/markdown_formatter.py
```

Este hook automaticamente:

- Detecta linguagens de programação em blocos de código sem rótulo
- Adiciona tags de idioma apropriadas para destaque de sintaxe
- Corrige linhas em branco excessivas enquanto preserva o conteúdo do código
- Processa apenas arquivos markdown (`.md`, `.mdx`)

### Hook de Notificação Personalizada

Obtenha notificações de desktop quando Claude precisar de entrada:

```json
{
  "hooks": {
    "Notification": [
      {
        "matcher": "",
        "hooks": [
          {
            "type": "command",
            "command": "notify-send 'Claude Code' 'Awaiting your input'"
          }
        ]
      }
    ]
  }
}
```

### Hook de Proteção de Arquivo

Bloqueie edições em arquivos sensíveis:

```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Edit|Write",
        "hooks": [
          {
            "type": "command",
            "command": "python3 -c \"import json, sys; data=json.load(sys.stdin); path=data.get('tool_input',{}).get('file_path',''); sys.exit(2 if any(p in path for p in ['.env', 'package-lock.json', '.git/']) else 0)\""
          }
        ]
      }
    ]
  }
}
```

---

## Saiba Mais

- **Referência de Hooks** — Documentação de referência completa sobre hooks
- **Considerações de Segurança** — Práticas de segurança abrangentes e diretrizes
- **Depuração** — Etapas de solução de problemas e técnicas de depuração na documentação de referência de hooks
