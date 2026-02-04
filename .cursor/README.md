# 📁 .cursor - Centro de Configuracao e Extensao da IA

Esta pasta atua como o **centro de configuracao e extensao da IA** dentro do projeto. Aqui ficam regras, comandos, skills e agentes organizados em subpastas para melhor leitura, manutencao e escalabilidade.

---

## 🗂️ Estrutura

```
/.cursor
├── commands/           # Comandos reutilizaveis (acionados com /)
│   └── *.md
├── rules/              # Instrucoes de comportamento do agente
│   └── *.md
├── skills/             # Skills de dominio
│   └── <skill>.md
├── agents/             # Subagents especializados
│   └── <agent>.md      # Ex: verifier.md, debugger.md
├── global/             # (Opcional) Configuracoes compartilhadas
│   └── *.md
└── README.md           # Este arquivo
```

---

## 📌 commands/

**Assunto:** Prompt-driven workflows rapidos e reutilizaveis  
**Acionamento:** `/comando` no chat da IDE

### Objetivo

Prover scripts de meta-prompt prontos para tarefas repetitivas (ex: criacao de PR, refatoracao padrao, geracao de testes).

### Conteudo Atual

| Comando | Descricao |
|---------|-----------|
| `few-shot.md` | Template base de Few-Shot Prompting |
| `few-shot-sdd.md` | Few-Shot para Spec-Driven Development |
| `few-shot-tdd.md` | Few-Shot para Test-Driven Development |
| `few-shot-bdd.md` | Few-Shot para Behavior-Driven Development |
| `few-shot-ai-first.md` | Few-Shot para AI-First Development |
| `few-shot-iterative.md` | Few-Shot para Iterative Development |
| `few-shot-pragmatic.md` | Few-Shot para Pragmatic Development |
| `few-shot-spike.md` | Few-Shot para Spike/Prototype-First |
| `few-shot-trunk.md` | Few-Shot para Trunk-Based Development |

### Estrutura Recomendada

```markdown
# /comando

## Descricao
Executa [descricao da tarefa].

## Uso
- Invocar: `/comando`
- Campos de entrada: [parametros]
- Requisitos: [pre-requisitos]

## Processo
1. [Passo 1]
2. [Passo 2]
3. [Passo 3]

## Output
[Formato esperado do resultado]
```

### Boas Praticas

- ✅ Nome de arquivo claro e consistente
- ✅ Um comando por trabalho especifico
- ✅ Documentar inputs esperados e contexto de uso
- ❌ Evitar comandos muito grandes ou genericos

---

## 📌 rules/

**Assunto:** Regras que o agente deve sempre ou inteligentemente aplicar  
**Formato:** Arquivos `*.md` ou `*.mdc` com frontmatter

### Objetivo

Fornecer instrucoes de sistema persistentes que moldam como o agente age, escreve codigo e usa contexto do projeto.

### Conteudo Atual

| Regra | Descricao | Escopo |
|-------|-----------|--------|
| `rules.mdc` | Regras globais do projeto | `**/*` |
| `backend.md` | Padroes especificos de backend | Backend |
| `frontend.md` | Padroes especificos de frontend | Frontend |

### Estrutura Recomendada

```markdown
---
title: Nome da Regra
description: "Descricao curta da regra"
glob: "*.ts"           # Tipos de arquivo (opcional)
alwaysApply: true      # Sempre anexar ao contexto
---

# Titulo da Regra

## Convencoes
1. [Regra 1]
2. [Regra 2]

## O que fazer
- ✅ [Pratica recomendada]

## O que evitar
- ❌ [Anti-pattern]
```

### Tipos de Regra

| Tipo | Quando Usar | Exemplo |
|------|-------------|---------|
| **Global** | Sempre aplicar | Convencoes Git, MCP |
| **Contextual** | Por tipo de arquivo | Backend, Frontend |
| **Condicional** | Sob demanda | Seguranca, Performance |

### Boas Praticas

- ✅ Regra separada por assunto curto e coeso
- ✅ Usar `alwaysApply: true` apenas quando necessario
- ✅ Definir `glob` para tipos de arquivo especificos
- ❌ Evitar regras muito longas (500+ linhas)
- ❌ Nao duplicar regras entre arquivos

---

## 📌 skills/

**Assunto:** Skills de dominio e workflows acionaveis pelo agente  
**Formato:** Arquivos `*.md` com frontmatter `name` e `description`

### Objetivo

Capacitar o agente com conhecimentos especializados ou processos que ele decide aplicar com base no contexto.

### Conteudo Atual

| Skill | Descricao |
|-------|-----------|
| `frontend-design-exemplo.md` | Criacao de interfaces frontend modernas |

### Estrutura Recomendada

```markdown
---
name: nome-da-skill
description: Descricao curta com keywords relevantes. Keywords: keyword1, keyword2.
---

# Nome da Skill

## Quando Usar Esta Skill
- [Situacao 1]
- [Situacao 2]

## Instrucoes
### 1. [Topico]
[Detalhes]

## Regras
✅ [O que fazer]
❌ [O que evitar]

## Exemplos (Few-Shot)
### Exemplo 1
**Entrada:** [Input]
**Resposta:** [Output esperado]
```

### Boas Praticas

- ✅ Nome da skill explicito (testing, security, performance)
- ✅ Description com keywords para busca semantica
- ✅ Incluir exemplos Few-Shot para consistencia
- ✅ Facilitar invocacao automatica pelo agente
- ❌ Nao criar skills muito genericas ou sobrepostas

---

## 📌 agents/

**Assunto:** Subagents especializados que o Agent pode delegar tarefas  
**Formato:** Arquivos `*.md` com frontmatter YAML

> ⚠️ **Nota:** Esta pasta contem **subagents** (ver secao detalhada abaixo). A estrutura segue o padrao oficial do Cursor.

### Estrutura

```
agents/
├── verifier.md         # Valida trabalho completado
├── debugger.md         # Especialista em debugging
├── security-auditor.md # Revisao de seguranca
└── test-runner.md      # Automacao de testes
```

### Casos de Uso

- **Verifier**: Valida que implementacoes estao funcionais
- **Debugger**: Analisa erros e falhas de teste
- **Security Auditor**: Revisao focada em seguranca
- **Test Runner**: Executa testes e corrige falhas

> 📚 **Ver secao completa:** [subagents/](#-subagents) para formato, configuracao e exemplos detalhados.

---

## 📌 subagents/

**Assunto:** Agentes especializados que o Agent principal pode delegar tarefas  
**Formato:** Arquivos `*.md` com frontmatter YAML em `.cursor/agents/`

> 📚 **Referencia oficial:** [Cursor Subagents Documentation](https://cursor.com/docs/context/subagents)

### O que sao Subagents

Subagents sao assistentes de IA especializados que o Agent do Cursor pode **delegar tarefas**. Cada subagent opera em sua propria janela de contexto, executa trabalho especifico e retorna o resultado ao agente principal.

### Beneficios

| Beneficio | Descricao |
|-----------|-----------|
| **Isolamento de contexto** | Cada subagent tem sua propria janela. Tarefas longas nao consomem espaco na conversa principal. |
| **Execucao paralela** | Lance multiplos subagents simultaneamente para trabalhar em partes diferentes do codigo. |
| **Expertise especializada** | Configure subagents com prompts customizados, acesso a ferramentas e modelos para tarefas especificas. |
| **Reutilizacao** | Defina subagents customizados e use em varios projetos. |

### Subagents Built-in

O Cursor inclui tres subagents nativos que lidam com operacoes pesadas automaticamente:

| Subagent | Proposito | Por que e um subagent |
|----------|-----------|----------------------|
| **Explore** | Busca e analisa codebases | Exploracao gera muito output intermediario. Usa modelo mais rapido para buscas paralelas. |
| **Bash** | Executa series de comandos shell | Output de comandos e verboso. Isolar mantem o foco do agente principal. |
| **Browser** | Controla browser via MCP | Interacoes de browser produzem snapshots DOM ruidosos. O subagent filtra resultados relevantes. |

### Modos de Execucao

| Modo | Comportamento | Melhor para |
|------|---------------|-------------|
| **Foreground** | Bloqueia ate completar. Retorna resultado imediatamente. | Tarefas sequenciais onde voce precisa do output. |
| **Background** | Retorna imediatamente. Subagent trabalha independentemente. | Tarefas longas ou workstreams paralelos. |

### Localizacoes de Arquivos

| Tipo | Localizacao | Escopo |
|------|-------------|--------|
| **Projeto** | `.cursor/agents/` | Apenas projeto atual |
| **Projeto** | `.claude/agents/` | Projeto atual (compatibilidade Claude) |
| **Usuario** | `~/.cursor/agents/` | Todos os projetos do usuario |
| **Usuario** | `~/.claude/agents/` | Todos os projetos (compatibilidade Claude) |

### Formato do Arquivo

```markdown
---
name: security-auditor
description: Especialista em seguranca. Use ao implementar auth, pagamentos ou dados sensiveis.
model: inherit
---

Voce e um especialista em seguranca auditando codigo para vulnerabilidades.

Quando invocado:
1. Identifique caminhos de codigo sensiveis a seguranca
2. Verifique vulnerabilidades comuns (injection, XSS, auth bypass)
3. Confirme que secrets nao estao hardcoded
4. Revise validacao e sanitizacao de input

Reporte achados por severidade:
- Critico (corrigir antes do deploy)
- Alto (corrigir em breve)
- Medio (resolver quando possivel)
```

### Campos de Configuracao

| Campo | Obrigatorio | Descricao |
|-------|-------------|-----------|
| `name` | Nao | Identificador unico. Use letras minusculas e hifens. Default: nome do arquivo. |
| `description` | Nao | Quando usar este subagent. Agent le isso para decidir delegacao. |
| `model` | Nao | Modelo a usar: `fast`, `inherit`, ou ID especifico. Default: `inherit`. |
| `readonly` | Nao | Se `true`, subagent roda com permissoes de escrita restritas. |
| `is_background` | Nao | Se `true`, subagent roda em background sem esperar conclusao. |

### Usando Subagents

**Delegacao automatica:** Agent delega automaticamente baseado na complexidade da tarefa e descricoes dos subagents.

**Invocacao explicita:** Use sintaxe `/nome` no prompt:

```text
> /verifier confirm the auth flow is complete
> /debugger investigate this error
> /security-auditor review the payment module
```

**Execucao paralela:** Lance multiplos subagents para maximo throughput:

```text
> Review the API changes and update the documentation in parallel
```

### Subagents vs Skills

| Use subagents quando... | Use skills quando... |
|-------------------------|---------------------|
| Precisa isolamento de contexto para pesquisa longa | Tarefa e single-purpose (gerar changelog, formatar) |
| Rodando multiplos workstreams em paralelo | Quer uma acao rapida e repetivel |
| Tarefa requer expertise especializada em muitos passos | Tarefa completa em um shot |
| Quer verificacao independente do trabalho | Nao precisa de janela de contexto separada |

### Exemplos de Subagents

#### Verificador

```markdown
---
name: verifier
description: Valida trabalho completado. Use apos tarefas marcadas como prontas para confirmar que implementacoes funcionam.
model: fast
---

Voce e um validador cetico. Seu trabalho e verificar que o trabalho alegado como completo realmente funciona.

Quando invocado:
1. Identifique o que foi alegado como completado
2. Verifique que a implementacao existe e e funcional
3. Execute testes relevantes ou passos de verificacao
4. Procure por edge cases que podem ter sido perdidos

Reporte:
- O que foi verificado e passou
- O que foi alegado mas esta incompleto ou quebrado
- Problemas especificos que precisam ser resolvidos
```

#### Debugger

```markdown
---
name: debugger
description: Especialista em debugging para erros e falhas de teste. Use ao encontrar problemas.
---

Voce e um debugger especialista em analise de causa raiz.

Quando invocado:
1. Capture mensagem de erro e stack trace
2. Identifique passos de reproducao
3. Isole a localizacao da falha
4. Implemente correcao minima
5. Verifique que a solucao funciona

Para cada problema, forneca:
- Explicacao da causa raiz
- Evidencia suportando o diagnostico
- Correcao especifica de codigo
- Abordagem de teste
```

### Boas Praticas

- ✅ **Subagents focados** - Cada um deve ter responsabilidade unica e clara
- ✅ **Invista em descriptions** - O campo `description` determina quando Agent delega
- ✅ **Prompts concisos** - Prompts longos diluem o foco
- ✅ **Versione subagents** - Commit `.cursor/agents/` no repositorio
- ✅ **Comece com Agent** - Deixe Agent ajudar a criar o subagent inicial

### Anti-patterns

- ❌ **Descricoes vagas** - "Use for general tasks" nao da sinal sobre quando delegar
- ❌ **Prompts muito longos** - 2000 palavras nao torna o subagent mais inteligente
- ❌ **Duplicar slash commands** - Se e single-purpose, use skill/command
- ❌ **Muitos subagents** - Comece com 2-3 focados, adicione conforme necessidade

---

## 🧠 Carregamento de Contexto Sob Demanda

### A Premissa

Assistentes de IA possuem uma **janela de contexto limitada** (tokens). Carregar toda a documentacao do projeto em cada interacao gera:

- ❌ **Desperdicio de tokens** (custo e lentidao)
- ❌ **Ruido** (informacao irrelevante confunde a IA)
- ❌ **Perda de foco** (contexto diluido)

**A solucao:** Estruturar a documentacao de forma que a LLM possa **buscar apenas o necessario, quando necessario**.

```text
┌─────────────────────────────────────────────────────────────┐
│                    JANELA DE CONTEXTO                       │
│                                                             │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐         │
│  │   Regras    │  │   Codigo    │  │  Resposta   │         │
│  │  Globais    │  │  do User    │  │   da IA     │         │
│  │  (sempre)   │  │             │  │             │         │
│  └─────────────┘  └─────────────┘  └─────────────┘         │
│        +                                                    │
│  ┌─────────────┐                                           │
│  │   Regras    │  ← Carregadas SOB DEMANDA                 │
│  │ Contextuais │    (quando relevantes)                    │
│  └─────────────┘                                           │
└─────────────────────────────────────────────────────────────┘
```

### Os Tres Pilares

| Pilar | Descricao | Como Aplicar |
|-------|-----------|--------------|
| **Separacao** | Global vs Contextual | `alwaysApply: true` vs `alwaysApply: false` |
| **Referencia** | Apontar para docs ao inves de inline | `(Full details: docs/GUIDE.md)` |
| **Metadados** | Permitir busca semantica | `description` com keywords relevantes |

### Estrategias de Otimizacao

| Estrategia | Descricao |
|------------|-----------|
| **Referencia** | Referenciar regras por ID ao inves de texto completo |
| **Separacao** | Global vs contextual (so carregar o necessario) |
| **Lazy Loading** | Incluir apenas blocos relacionados a tarefa |
| **Indexacao** | Mapear regras por topicos para busca semantica |

### Exemplo Pratico: Cenarios de Carregamento

```text
Tarefa do Usuario          │  O que a LLM Carrega
───────────────────────────┼──────────────────────────────────────
"Crie um componente"       │  rules.mdc + git-conventions.md
"Refatore este codigo"     │  rules.mdc + git-conventions.md + refactoring.md
"Adicione testes"          │  rules.mdc + git-conventions.md + testing.md
"Revise a seguranca"       │  rules.mdc + git-conventions.md + security.md
```

### Padrao de Referencia Externa

Quando uma regra precisa de documentacao extensa, **referencie ao inves de incluir inline**:

**❌ Anti-pattern (Pesado):**

```markdown
# Regras de Arquitetura

## Camada de Dominio
A camada de dominio e responsavel por encapsular toda a logica de negocios...
[500 linhas de documentacao completa]
```

**✅ Pattern (Leve):**

```markdown
---
description: "arquitetura, clean architecture, camadas, domain"
alwaysApply: false
---

# Regras de Arquitetura (Full details: docs/ARCHITECTURE.md)

**Estrutura:**
- Apps = Bootstraps (orquestracao apenas)
- Packages = Logica de negocios
- Modules = Dominios independentes e composiveis
```

### Como Funciona na Pratica

```text
1. IDE detecta: "Arquivo *.ts em backend/"
                    │
                    ▼
2. Busca regras com glob match:
   ┌──────────────────────────────────────┐
   │ rules.mdc        → alwaysApply: true │ ✅ Carrega
   │ backend.md       → glob: "backend/*" │ ✅ Carrega
   │ frontend.md      → glob: "frontend/*"│ ❌ Ignora
   │ security.md      → alwaysApply: false│ ❌ Ignora (por enquanto)
   └──────────────────────────────────────┘
                    │
                    ▼
3. Usuario menciona "autenticacao JWT"
                    │
                    ▼
4. Busca semantica na description:
   security.md → description: "autenticacao, JWT, OAuth"
                    │
                    ▼
5. Carrega security.md sob demanda ✅
```

### Exemplo de Referencia por Identifier

```markdown
# .cursor/rules/architecture.md
identifier: architecture-standard
```

O agente busca conteudo sob demanda quando a query pedir por arquitetura.

---

## 📐 Boas Praticas Gerais

### Clareza

- ✅ Titulos e descricoes claras em cada arquivo
- ✅ Documentar no README como usar cada categoria
- ✅ Manter consistencia de nomenclatura

### Escopo e Reutilizacao

- ✅ Regra unica por arquivo com escopo bem definido
- ✅ Commands focados em um unico objetivo
- ✅ Skills com proposito claro e keywords de ativacao

### Manutencao em Times

- ✅ Version control completo (Git)
- ✅ Convencoes internas documentadas
- ✅ Linters quando aplicavel

---

## 🔗 Referencias

- [Template Few-Shot](../prompts/Techniques/Prompt-FewShot.md)
- [Workflows Disponiveis](../docs/workflows/)
- [README Principal](../README.md)

### Documentacao Oficial Cursor

- [Subagents](https://cursor.com/docs/context/subagents) - Agentes especializados para delegacao
- [Rules](https://cursor.com/docs/context/rules) - Regras de comportamento
- [Skills](https://cursor.com/docs/context/skills) - Skills de dominio
- [Commands](https://cursor.com/docs/context/commands) - Comandos customizados

---

## 🔄 Hierarquia de Carregamento

```
1. rules/*.md (alwaysApply: true)
   ↓
2. rules/*.md (glob match)
   ↓
3. skills/*.md (keyword match no contexto)
   ↓
4. agents/*.md (delegacao automatica ou /nome)
   ↓
5. commands/*.md (invocacao explicita com /)
```

### Fluxo de Delegacao de Subagents

```
Agent Principal
    │
    ├──► Subagent (Foreground) ──► Resultado ──► Continua
    │
    └──► Subagent (Background) ──► [Trabalha independente]
              │
              └──► Output em ~/.cursor/subagents/
```

---

**Ultima Atualizacao**: Fevereiro 2026