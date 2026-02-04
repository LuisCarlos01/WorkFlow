# 📁 .claude - Centro de Configuracao e Contexto para Claude Agents

Esta pasta atua como o **nucleo de configuracao e contexto** para Claude Code e agentes Claude dentro do projeto. Aqui ficam o manifesto contextual (`CLAUDE.md`), comandos customizados e agentes especializados organizados para melhor leitura, manutencao e escalabilidade.

---

## 🎯 Visao Geral

O arquivo `CLAUDE.md` e a pasta `.claude/` existem como pontos centrais de configuracao e contexto para agentes Claude.

**Claude Code** e a ferramenta agentic da Anthropic que permite que Claude:

- Entenda o codigo-fonte do projeto
- Execute comandos no terminal
- Leia arquivos e realize tarefas de desenvolvimento programaticamente

### Componentes Principais

| Componente   | Finalidade                                                     |
|--------------|----------------------------------------------------------------|
| `CLAUDE.md`  | Manifesto contextual lido automaticamente no inicio da sessao  |
| `.claude/`   | Pasta de configuracao com comandos, agentes e settings         |

---

## 🗂️ Estrutura

```text
/.claude
├── CLAUDE.md              # Manifesto contextual (pode estar na raiz)
├── settings.json          # (Opcional) Configuracoes avancadas
├── commands/              # Comandos customizados acionados pelo agente
│   └── <command-name>.md
├── agents/                # Agentes especializados do projeto
│   ├── <agent-name>.md
│   └── <agent-name>/
│       ├── agent.md
│       └── config.json
└── README.md              # Este arquivo
```

---

## 📜 CLAUDE.md - O Manifesto Contextual

### Objetivo

O `CLAUDE.md` fornece contexto persistente e regras amplas que Claude le no inicio de cada sessao para:

- Saber o proposito do projeto
- Entender convencoes e padroes
- Ter comandos e referencias uteis
- Guiar o comportamento dos agentes e comandos automaticos

> **Importante:** Este arquivo nao e um script nem um schema JSON; e um manifesto textual legivel pelo modelo.

### Publico-Alvo

| Publico                  | Utilizacao                                                      |
|--------------------------|-----------------------------------------------------------------|
| Claude Code / Agents     | Contexto lido automaticamente no inicio de cada sessao          |
| Desenvolvedores          | Compartilha convencoes do projeto com humanos e agentes         |
| Colaboradores            | Referencia de expectativas de comportamento do agente           |

### Secoes Recomendadas

```markdown
# 🚀 Contexto do Projeto
Breve descricao do que o projeto faz e seus objetivos principais.

# 🤖 User Prompt / Persona
Definicao da persona do assistente e stack tecnologica.

# 🧠 Convencoes de Codigo
Principais padroes de estilo, nomeacao e estrutura de pastas.

# 🛠️ Comandos Frequentes
Exemplos de comandos uteis que Claude pode sugerir/usar.

# 📐 Regras de Arquitetura
Decisoes arquiteturais importantes que o agente deve respeitar.

# 🧪 Testes e Qualidade
Como rodar testes e padroes de qualidade esperados.

# ⚠️ Restricoes/Safeguards
Regras que o agente deve sempre observar.

# 📚 Referencias
Links para documentacao e recursos do projeto.
```

### Boas Praticas de Escrita

- ✅ Escopo util e conciso (Claude le tudo no inicio; instrucoes irrelevantes geram ruido)
- ✅ Tom natural, objetivo e formatado em Markdown
- ✅ Exemplos e padroes claros com listas ou blocos de codigo
- ✅ Atualizacao constante (evolutivo com mudancas do projeto)
- ❌ Evitar detalhes especificos de uma task (foco em contextos amplos e reutilizaveis)

---

## 📌 commands/

**Assunto:** Comandos customizados que Claude executa sob demanda  
**Formato:** Arquivos `*.md` escritos em linguagem natural

### Objetivo dos Commands

Prover scripts de slash commands em Markdown para tarefas repetitivas ou acoes padronizadas do dia-a-dia de desenvolvimento.

### Conteudo Atual dos Commands

| Comando    | Descricao                     |
|------------|-------------------------------|
| *(vazio)*  | Nenhum comando definido ainda |

### Estrutura Recomendada para Commands

```markdown
# /nome-do-comando

## Descricao
Executa [descricao da tarefa].

## Uso
- Invocar: `/nome-do-comando`
- Campos de entrada: [parametros]
- Requisitos: [pre-requisitos]

## Processo
1. [Passo 1]
2. [Passo 2]
3. [Passo 3]

## Output
[Formato esperado do resultado]
```

### Convencoes de Nomenclatura para Commands

- **Formato:** `<action>.<scope>.md` ou `<action>-<scope>.md`
- **Exemplos:** `generate-docs.md`, `fix-tests.md`, `create-techspec.md`

### Boas Praticas para Commands

- ✅ Nome de arquivo claro e consistente
- ✅ Um comando por trabalho especifico
- ✅ Documentar inputs esperados e contexto de uso
- ✅ Usar placeholders com sintaxe clara (ex: `$ARGUMENTS`, `{slug}`)
- ❌ Evitar comandos muito grandes ou genericos

---

## 📌 agents/

**Assunto:** Agentes especializados com comportamentos modulares  
**Formato:** Arquivos `*.md` ou subpastas com `agent.md` e `config.json`

### Objetivo dos Agents

Definir agentes com comportamentos especializados, isolando responsabilidades e permitindo modularizacao de contexto.

### Conteudo Atual dos Agents

| Agente                          | Descricao                                      |
|---------------------------------|------------------------------------------------|
| `tech-spec-writer.md`           | Cria especificacoes tecnicas detalhadas        |
| `task-writer.md`                | Gera lista de tarefas a partir da Tech Spec    |
| `code-quality-reviewer.md`      | Revisa codigo e aplica correcoes               |
| `conventional-commit-writer.md` | Cria commits seguindo Conventional Commits     |
| `instrucao.md`                  | Instrucoes gerais para agentes                 |

### Estrutura Simples para Agents (Arquivo Unico)

```markdown
# Nome do Agente

## Identity
name: [Nome do Agente]
description: [Descricao do proposito]

## Context
[Instrucoes especificas para este agente]

## Rules
- [Regra 1]
- [Regra 2]

## Examples (Few-Shot)
### Exemplo 1
**Input:** [Entrada]
**Output:** [Saida esperada]
```

### Estrutura Avancada para Agents (Subpasta)

```text
agents/
└── <agent-name>/
    ├── agent.md        # Instrucoes de comportamento
    └── config.json     # Configuracoes especificas (model, habilidades, limites)
```

### Convencoes de Nomenclatura para Agents

- **Formato:** `kebab-case` para nomes de agentes
- **Exemplos:** `tech-spec-writer`, `code-quality-reviewer`, `ci-agent`

### Boas Praticas para Agents

- ✅ Nome explicito que indica a funcao do agente
- ✅ Incluir exemplos Few-Shot para consistencia
- ✅ Separar agentes por dominio/responsabilidade
- ✅ Documentar regras e restricoes especificas
- ❌ Nao criar agentes com responsabilidades sobrepostas

---

## ⚙️ settings.json (Opcional)

**Assunto:** Configuracoes avancadas do projeto  
**Formato:** Arquivo JSON

### Objetivo do Settings

Definir permissoes, modelo padrao, hooks e outras configuracoes avancadas para o agente.

### Estrutura Exemplo do Settings

```json
{
  "model": "claude-3.5-sonnet",
  "permissions": {
    "terminal": true,
    "fileSystem": true,
    "web": false
  },
  "hooks": {
    "onSessionStart": "read CLAUDE.md",
    "beforeCommit": "run lint"
  },
  "safeguards": {
    "requireConfirmation": ["delete", "overwrite"],
    "blacklist": ["*.env", "secrets/*"]
  }
}
```

> **Nota:** Esta estrutura e inferida de praticas da comunidade e pode nao refletir implementacao oficial.

---

## 🔗 Relacao entre Componentes

```text
┌─────────────────────────────────────────────────────────┐
│                      CLAUDE.md                          │
│         (Instrucoes gerais para todos os agentes)       │
└─────────────────────────┬───────────────────────────────┘
                          │
          ┌───────────────┼───────────────┐
          ▼               ▼               ▼
    ┌──────────┐    ┌──────────┐    ┌──────────┐
    │ commands/│    │ agents/  │    │ settings │
    │          │    │          │    │ .json    │
    │ Comandos │    │ Agentes  │    │ Config   │
    │ sob      │    │ especial │    │ avancada │
    │ demanda  │    │ izados   │    │          │
    └──────────┘    └──────────┘    └──────────┘
```

### Hierarquia de Responsabilidades

| Nivel | Componente      | Escopo                                            |
|-------|-----------------|---------------------------------------------------|
| 1     | `CLAUDE.md`     | Contexto universal para todos os agentes/comandos |
| 2     | `agents/*.md`   | Comportamentos especializados e modularizados     |
| 3     | `commands/*.md` | Comandos reutilizaveis executados sob demanda     |
| 4     | `settings.json` | Permissoes e configuracoes tecnicas               |

---

## 🧠 Boas Praticas de Prompt Engineering

Esta estrutura aplica boas praticas reconhecidas de prompt/agent engineering:

| Pratica                              | Como e Aplicada                                          |
|--------------------------------------|----------------------------------------------------------|
| **Clareza de contexto**              | CLAUDE.md fornece contexto universal, evitando repeticao |
| **Delimitacao de responsabilidades** | Comandos e agentes tem papeis isolados                   |
| **Separacao global vs especifico**   | Regras gerais no manifesto; detalhes nos agentes         |
| **Escalabilidade**                   | Adicionar agentes especializados sem inflar CLAUDE.md    |
| **Manutenibilidade**                 | Cada comando/agent isolado facilita revisoes e testes    |

---

## 📦 Carregamento de Contexto Sob Demanda

### A Premissa

Assistentes de IA possuem uma **janela de contexto limitada** (tokens). Carregar toda a documentacao do projeto em cada interacao gera:

- ❌ **Desperdicio de tokens** (custo e lentidao)
- ❌ **Ruido** (informacao irrelevante confunde a IA)
- ❌ **Perda de foco** (contexto diluido)

**A solucao:** Estruturar a documentacao de forma que a LLM possa **buscar apenas o necessario, quando necessario**.

### Os Tres Pilares

| Pilar | Descricao | Aplicacao no Claude Code |
|-------|-----------|--------------------------|
| **Separacao** | Global vs Contextual | CLAUDE.md (global) vs agents/*.md (especifico) |
| **Referencia** | Apontar para docs ao inves de inline | `(Full details: docs/GUIDE.md)` |
| **Modularizacao** | Agentes especializados por dominio | `@tech-spec-writer`, `@code-quality-reviewer` |

### Como Funciona no Claude Code

Diferente do Cursor (que usa frontmatter com `alwaysApply` e `glob`), o Claude Code opera com:

```text
┌─────────────────────────────────────────────────────────────┐
│                      CLAUDE.md                              │
│              (Lido automaticamente - SEMPRE)                │
│                                                             │
│  • Contexto do projeto                                      │
│  • Convencoes globais                                       │
│  • Referencias para docs detalhadas                         │
└─────────────────────────┬───────────────────────────────────┘
                          │
                          ▼ Sob Demanda (mencao @agent ou contexto)
          ┌───────────────┼───────────────┐
          ▼               ▼               ▼
    ┌──────────┐    ┌──────────┐    ┌──────────┐
    │ @tech-   │    │ @code-   │    │ @commit- │
    │ spec-    │    │ quality- │    │ writer   │
    │ writer   │    │ reviewer │    │          │
    └──────────┘    └──────────┘    └──────────┘
```

### Exemplo Pratico: Cenarios de Carregamento

```text
Tarefa do Usuario              │  O que Claude Carrega
───────────────────────────────┼──────────────────────────────────────
"Crie uma especificacao"       │  CLAUDE.md + @tech-spec-writer
"Revise a qualidade do codigo" │  CLAUDE.md + @code-quality-reviewer
"Faca o commit"                │  CLAUDE.md + @conventional-commit-writer
"Gere as tasks"                │  CLAUDE.md + @task-writer
```

### Padrao de Referencia Externa

Quando o CLAUDE.md precisa mencionar documentacao extensa, **referencie ao inves de incluir inline**:

**❌ Anti-pattern (Pesado):**

```markdown
# Regras de Arquitetura

## Camada de Dominio
A camada de dominio e responsavel por encapsular toda a logica de negocios...
[500 linhas de documentacao completa]
```

**✅ Pattern (Leve):**

```markdown
# Regras de Arquitetura (Full details: docs/ARCHITECTURE.md)

**Estrutura:**
- Apps = Bootstraps (orquestracao apenas)
- Packages = Logica de negocios
- Modules = Dominios independentes e composiveis
```

### Agentes como "Documentacao Sob Demanda"

No Claude Code, os **agents** funcionam como documentacao especializada carregada sob demanda:

| Agente | Quando e Carregado | Conteudo Especializado |
|--------|-------------------|------------------------|
| `@tech-spec-writer` | Ao criar especificacoes | Templates, padroes de spec |
| `@task-writer` | Ao gerar tasks | Formato de tasks, criterios |
| `@code-quality-reviewer` | Ao revisar codigo | Checklists, boas praticas |
| `@conventional-commit-writer` | Ao commitar | Padroes de commit, escopos |

### Estrategias de Otimizacao

| Estrategia | Descricao |
|------------|-----------|
| **CLAUDE.md enxuto** | Manter apenas contexto universal, sem detalhes de tasks |
| **Agentes modulares** | Um agente por responsabilidade/dominio |
| **Referencias externas** | Apontar para docs detalhadas ao inves de inline |
| **Invocacao explicita** | Usar `@agent` para carregar contexto especifico |

---

## 🔄 Hierarquia de Carregamento

```text
1. CLAUDE.md (lido automaticamente no inicio da sessao)
   ↓
2. settings.json (configuracoes e permissoes)
   ↓
3. agents/*.md (invocados por mencao @agent ou contexto)
   ↓
4. commands/*.md (invocados explicitamente com /)
```

---

## 📐 Boas Praticas Gerais

### Clareza e Organizacao

- ✅ Titulos e descricoes claras em cada arquivo
- ✅ Documentar no README como usar cada categoria
- ✅ Manter consistencia de nomenclatura (kebab-case)

### Escopo e Reutilizacao

- ✅ CLAUDE.md com escopo amplo e reutilizavel
- ✅ Commands focados em um unico objetivo
- ✅ Agents com proposito claro e especializado

### Manutencao em Times

- ✅ Version control completo (Git)
- ✅ Convencoes internas documentadas
- ✅ Versionar comandos e agentes junto ao codigo

### Seguranca e Safeguards

- ✅ Manter permissoes/seguranca em settings.json
- ✅ Definir safeguards para evitar acoes destrutivas
- ✅ Blacklist de arquivos sensiveis

---

## 🔗 Referencias

- [CLAUDE.md Principal](../CLAUDE.md) - Manifesto do projeto
- [Documentacao do Workflow](../docs/workflow.md) - Fluxo de trabalho
- [README Principal](../README.md) - Visao geral do projeto
- [Templates](../docs/templates/) - Templates reutilizaveis

---

## 📊 Comparativo: .claude/ vs .cursor/

| Aspecto         | .claude/                     | .cursor/                       |
|-----------------|------------------------------|--------------------------------|
| **Ferramenta**  | Claude Code (Anthropic)      | Cursor AI (Cursor)             |
| **Manifesto**   | CLAUDE.md                    | rules/*.mdc                    |
| **Carregamento**| Automatico no inicio         | Por glob/alwaysApply           |
| **Comandos**    | commands/*.md                | commands/*.md                  |
| **Agentes**     | agents/*.md                  | agents/*.md                    |
| **Skills**      | (via agents)                 | skills/*.md                    |
| **Rules**       | (via CLAUDE.md)              | rules/*.md                     |

---

**Ultima Atualizacao**: Fevereiro 2026
