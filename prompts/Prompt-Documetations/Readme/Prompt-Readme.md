# 📘 Template de Geração de README - Cursor IDE

Template de prompt baseado em **síntese técnica e comunicação efetiva** para gerar **READMEs claros, profissionais e úteis** que servem como porta de entrada do projeto para desenvolvedores, stakeholders e colaboradores. Ideal para transformar documentação técnica em guia prático de onboarding.

---

## 📝 Template do Prompt

Copie e personalize o template abaixo. Este prompt utiliza **documentação existente** (PRD, Vision, ADRs, Roadmap) para criar README.

```markdown
## Role (Identidade da IA)

Você é um **engenheiro de software sênior e technical writer** com experiência em:
- Documentação técnica clara e objetiva
- READMEs de projetos open-source de sucesso
- Onboarding eficaz de desenvolvedores
- Developer Experience (DX) e usabilidade de docs
- Comunicação técnica para diferentes audiências
- Manutenção de documentação escalável

Você domina projetos de {{dominio}} (ex.: SaaS, bibliotecas open-source, APIs, mobile apps, ferramentas CLI).

## Objetivo

Transformar a **documentação fornecida** em um **README completo, claro e bem estruturado** que será a primeira impressão e guia principal do projeto para desenvolvedores, contribuidores, novos membros do time e stakeholders técnicos.

## Contexto

Um README eficaz responde:
- **O que é isso?** - Entendimento imediato
- **Por que existe?** - Problema que resolve
- **Como uso?** - Getting started rápido
- **Como funciona?** - Arquitetura de alto nível
- **Como contribuo?** - Diretrizes de colaboração
- **O que vem depois?** - Roadmap e evolução

O README é **porta de entrada**, não documentação completa. Deve permitir que alguém entenda e comece a usar o projeto em 5-10 minutos.

## Entrada (Fonte de Verdade)

O usuário fornecerá documentação existente:

- 🌍 **Vision & Problem Statement** - Propósito estratégico
- 📋 **Briefing** - Contexto do projeto
- 📄 **PRD** - Funcionalidades e requisitos
- ⚙️ **NFRs** - Requisitos de qualidade
- 🏗️ **ADRs** - Decisões técnicas importantes
- 📐 **Diagramas** - Arquitetura visual
- 🗺️ **Roadmap** - Futuro do projeto
- 🔧 **Código existente** - Estrutura de pastas, scripts

Use **exclusivamente** esses documentos como fonte.

## Tarefa Principal

1. **Extrair essência do projeto** da documentação
2. **Identificar funcionalidades principais** (não listar tudo)
3. **Criar getting started prático** (se informações existirem)
4. **Mapear arquitetura de alto nível** (sem detalhes de implementação)
5. **Identificar pré-requisitos** (ambiente, dependências)
6. **Destacar informações críticas** (NFRs, limitações, riscos)
7. **Apontar documentação adicional** (links para docs detalhados)

## Estrutura do README

### Seções Essenciais (Sempre Incluir):

#### 1. Header
- Nome do projeto
- Tagline descritiva (1 frase)
- Badges relevantes (se aplicável: build status, coverage, version)

#### 2. Visão Geral (Overview)
- Descrição clara em 2-3 parágrafos
- Problema que resolve
- Proposta de valor única
- Público-alvo principal

#### 3. Funcionalidades Principais (Key Features)
- 3-8 features mais importantes
- Bullets objetivos
- Foco em benefícios, não implementação

#### 4. Requisitos (Requirements)
- Pré-requisitos de sistema
- Dependências principais (runtime)
- Versões mínimas (se conhecidas)

#### 5. Instalação (Installation)
- Passos claros e testáveis
- Comandos copiáveis
- Troubleshooting básico (se aplicável)

#### 6. Quick Start / Uso Básico
- Exemplo mínimo funcional
- Caso de uso mais comum
- Link para docs detalhadas

#### 7. Arquitetura (High-Level)
- Visão geral dos componentes
- Diagrama ou descrição textual
- Tecnologias principais (se explícitas)

### Seções Importantes (Incluir se Informações Disponíveis):

#### 8. Configuração (Configuration)
- Variáveis de ambiente principais
- Arquivos de config relevantes
- Opções mais usadas

#### 9. Desenvolvimento (Development)
- Como rodar localmente
- Como rodar testes
- Como fazer build
- Estrutura de pastas

#### 10. Contribuição (Contributing)
- Como contribuir
- Process de PR/review
- Padrões de código (ou link para CONTRIBUTING.md)
- Code of Conduct (se aplicável)

#### 11. Testes (Testing)
- Como rodar testes
- Cobertura esperada
- Tipos de testes (unit, integration, e2e)

#### 12. Deploy / Produção
- Como fazer deploy (se aplicável)
- Ambientes disponíveis
- CI/CD (se automatizado)

### Seções Opcionais (Incluir se Relevante):

#### 13. Roadmap
- Próximas features (high-level)
- Direção futura
- Link para roadmap detalhado

#### 14. Limitações e Problemas Conhecidos
- Limitações técnicas atuais
- Workarounds conhecidos
- Issues críticos

#### 15. Performance e NFRs
- Benchmarks (se disponíveis)
- SLAs (se aplicável)
- Limitações de escala

#### 16. Segurança
- Considerações de segurança
- Como reportar vulnerabilidades
- Compliance (se aplicável)

#### 17. FAQ
- Perguntas frequentes
- Problemas comuns
- Troubleshooting

#### 18. Documentação Relacionada
- Links para:
  - Documentação completa
  - API reference
  - Guias de uso
  - ADRs
  - Diagramas

#### 19. Licença
- Tipo de licença
- Copyright

#### 20. Contato e Suporte
- Como obter ajuda
- Canais de comunicação (Slack, Discord, Issues)
- Maintainers

## Diretrizes de Escrita

### Tom e Estilo:
- **Seja direto:** Vá ao ponto rapidamente
- **Seja prático:** Prefira exemplos a explicações longas
- **Seja honesto:** Explicite limitações e problemas conhecidos
- **Seja acessível:** Não assuma conhecimento avançado
- **Seja visual:** Use code blocks, tabelas, listas

### O que Evitar:
- ❌ Paredes de texto sem formatação
- ❌ Jargão técnico desnecessário
- ❌ Instruções vagas ("configure apropriadamente")
- ❌ Comandos que não funcionam
- ❌ Links quebrados
- ❌ Informações desatualizadas

### O que Priorizar:
- ✅ Getting started funciona em < 5 minutos
- ✅ Exemplos são copiáveis e funcionam
- ✅ Arquitetura é compreensível visualmente
- ✅ Contribuir é claro e convidativo
- ✅ Informação mais importante no topo

## Estrutura Esperada da Resposta

Gere README completo com:

1. **Header** (nome, tagline, badges)
2. **Overview** (o que é, por que existe)
3. **Features** (o que faz)
4. **Requirements** (o que precisa)
5. **Installation** (como instalar)
6. **Quick Start** (como usar rapidamente)
7. **Architecture** (como funciona)
8. **Development** (como desenvolver)
9. **Testing** (como testar)
10. **Contributing** (como colaborar)
11. **Roadmap** (o que vem)
12. **Known Issues** (problemas conhecidos)
13. **Docs** (onde saber mais)
14. **License** (licença)
15. **Contact** (como obter ajuda)

Adapte seções baseado no contexto (open-source vs interno, biblioteca vs aplicação).

## Formato da Resposta

1. **Gere apenas** o arquivo README.md
2. **Utilize Markdown** bem estruturado
3. **Use code blocks** com syntax highlighting
4. **Use tabelas** quando apropriado (comparações, configs)
5. **Sem emojis** no documento final (exceto se projeto for informal/jovem)
6. **Pronto para:** Git repo, onboarding, documentação oficial

## Restrições

- ❌ Não inventar comandos ou APIs que não existem
- ❌ Não assumir tecnologias não mencionadas
- ❌ Não criar exemplos que não funcionariam
- ❌ Não usar linguagem de marketing exagerada
- ✅ Derivar exclusivamente da documentação fornecida
- ✅ Explicitar quando informações estão faltando
- ✅ Ser tecnicamente preciso e verificável
- ✅ Priorizar utilidade sobre perfeição estética
```

---

## 🚀 Como Usar

### 1️⃣ Fluxo Recomendado (Documentation Pipeline)

O README é tipicamente criado após documentação estrutural:

```
1️⃣ Vision & Problem Statement → Propósito estratégico
         ↓
2️⃣ Briefing → Contexto e stakeholders
         ↓
3️⃣ PRD → Funcionalidades detalhadas
         ↓
4️⃣ NFRs → Requisitos de qualidade
         ↓
5️⃣ Diagramas → Arquitetura visual
         ↓
6️⃣ ADRs → Decisões técnicas
         ↓
7️⃣ Roadmap → Planejamento futuro
         ↓
8️⃣ README (este) → Síntese e porta de entrada
         ↓
9️⃣ Código → Implementação
```

**Vantagens de Criar README Cedo:**
- Força clareza sobre propósito do projeto
- Facilita onboarding contínuo
- Documenta decisões enquanto são tomadas
- Serve como "fonte da verdade" evolutiva

**Quando Atualizar README:**
- Novas features importantes
- Mudanças de arquitetura
- Novos requisitos ou dependências
- Mudanças no processo de contribuição
- Mínimo: trimestralmente

### 2️⃣ Onde Usar

- **GitHub/GitLab** → README.md na raiz do repo
- **Notion/Confluence** → Página de overview do projeto
- **Wiki interna** → Guia de onboarding
- **Documentação pública** → Landing page técnica
- **Apresentações** → Base para slides de overview

### 3️⃣ Exemplo Prático Completo

**Entrada (Documentação Base):**

```markdown
# PRD - TaskFlow (Sistema de Gerenciamento de Tarefas)

**Vision:** Simplificar gestão de tarefas para times remotos.

**Features:**
- Criação e atribuição de tarefas
- Boards Kanban customizáveis
- Integrações (Slack, GitHub)
- Time tracking
- Relatórios de produtividade

**Tech Stack:**
- Frontend: React + TypeScript
- Backend: Node.js + Express
- Database: PostgreSQL
- Infra: AWS (ECS, RDS, S3)

**NFRs:**
- Performance: Resposta < 200ms
- Disponibilidade: 99.5% uptime
- Escalabilidade: 10k usuários simultâneos
```

**Saída Esperada:**

A IA gerará README completo com todas as seções, exemplos de uso, comandos de instalação, arquitetura, etc.

---

## 💡 Por Que Este Prompt Funciona

### ✅ 1. README como Primeira Impressão
- Desenvolvedores decidem em 30s se vão usar/contribuir
- README claro = mais adoção, menos fricção
- README confuso = abandono imediato
- "Show, don't tell" - exemplos > explicações

### ✅ 2. Onboarding Acelerado
- Novos desenvolvedores produtivos em horas, não dias
- Reduz interrupções ("como eu faço X?")
- Self-service documentation
- Menos dependência de tribal knowledge

### ✅ 3. Documentação Viva
- Sincroniza com código e decisões técnicas
- Evolui com o projeto (não fica obsoleto)
- Baseado em documentação estruturada (PRD, ADRs)
- Single source of truth atualizado

### ✅ 4. Multi-Audiência
- **Desenvolvedores:** Getting started, arquitetura, contribuição
- **Stakeholders:** Overview, features, roadmap
- **Usuários finais:** (se produto) Como usar
- **Contribuidores externos:** Como colaborar

### ✅ 5. Reduz Dívida de Documentação
- README força clareza desde o início
- Previne "código sem contexto"
- Facilita manutenção (estrutura padrão)
- Escala para múltiplos projetos

### ✅ 6. Melhora Developer Experience (DX)
- Quick start funciona de verdade
- Exemplos são copiáveis
- Troubleshooting antecipa problemas
- Links levam a docs úteis

---

## ⚠️ Observações Importantes

### O que este prompt faz:
- ✅ Cria README estruturado e completo
- ✅ Extrai informações de múltiplas fontes (PRD, ADRs, Roadmap)
- ✅ Organiza conteúdo por relevância
- ✅ Fornece getting started prático
- ✅ Mapeia arquitetura de alto nível
- ✅ Identifica gaps de documentação
- ✅ Adapta tom para audiência

### O que este prompt NÃO faz:
- ❌ Não cria documentação técnica profunda (use docs separadas)
- ❌ Não gera código ou exemplos funcionais (use o que existe)
- ❌ Não substitui API reference (use tools como Swagger)
- ❌ Não cria tutoriais detalhados (README aponta para eles)
- ❌ Não documenta todos os detalhes de implementação
- ❌ Não mantém README atualizado automaticamente

### Quando usar este prompt:
- **Use quando:**
  - Iniciando novo projeto (README como design doc inicial)
  - Projeto existe mas README está vago/desatualizado
  - Onboarding está lento (muitas perguntas repetidas)
  - Preparando projeto para open-source
  - Novo time assumindo projeto legado
  - Documentação está espalhada (centralizar no README)

- **Não use quando:**
  - Projeto ainda é apenas ideia (use Vision primeiro)
  - Não há documentação base mínima
  - Organização tem template de README rígido e completo
  - README já está excelente (não quebre o que funciona)

---

## 🔄 Personalização Avançada

### Para Diferentes Tipos de Projeto:

**Open-Source (Biblioteca/Framework):**
```markdown
## Ajustes de Foco

**Seções Essenciais:**
1. **Installation via package managers** (npm, pip, cargo)
2. **Quick example** (< 10 linhas de código)
3. **API Reference** (ou link para ela)
4. **Contributing guidelines** (detalhado)
5. **License** (muito importante)
6. **Badges** (build status, coverage, downloads)
7. **Comparison table** (vs alternativas)

**Tom:**
- Convidativo para contribuidores
- Assumir zero contexto prévio
- Exemplos progressivos (básico → avançado)
- Highlight community (Discord, forum)

**Exemplo de Header:**
```

# LibraryName

Fast, type-safe [problema] for [linguagem/plataforma].

![Build Status](badge) ![Coverage](badge) ![npm version](badge)

[Quick Start](#quick-start) | [Docs](link) | [Examples](link) | [Contributing](#contributing)
```
```

---

**Startup/Produto SaaS:**
```markdown
## Ajustes de Foco

**Seções Essenciais:**
1. **Problem statement** (dor que resolve)
2. **Demo link ou screenshots**
3. **Features** (user-facing, não técnicas)
4. **Tech stack** (para engenheiros)
5. **Development setup** (onboarding de time)
6. **Deployment** (staging, produção)
7. **Architecture diagram** (high-level)

**Tom:**
- Product-first, tech depois
- Contexto de negócio importante
- Link para PRD e roadmap
- Metrics e KPIs (se públicos)

**Estrutura Sugerida:**
```

# ProductName - [Tagline]

## What We're Building
[Vision statement - 2 parágrafos]

## Key Features
- Feature 1 (benefit)
- Feature 2 (benefit)

## Tech Stack
Frontend: React, TypeScript
Backend: Node.js, PostgreSQL
Infra: AWS, Vercel

## Development
[Getting started para novos engenheiros]

## Documentation
- [PRD](link) - Product requirements
- [Roadmap](link) - What's next
- [ADRs](link) - Technical decisions
```
```

---

**Enterprise/Sistema Interno:**
```markdown
## Ajustes de Foco

**Seções Essenciais:**
1. **Business context** (por que existe)
2. **System dependencies** (outros sistemas internos)
3. **Access/permissions** (como obter acesso)
4. **Runbooks** (operações comuns)
5. **SLAs e NFRs** (expectativas de qualidade)
6. **Contacts** (owners, on-call)
7. **Compliance** (SOC2, GDPR, etc)

**Tom:**
- Enterprise-friendly
- Compliance-aware
- Operations-focused
- Clear ownership

**Exemplo de Seção:**
```

## System Overview

Internal billing system that processes [X] transactions/day.

**Owners:** Payments Team (@payments-team)
**On-Call:** PagerDuty rotation
**SLA:** 99.9% uptime, < 500ms p95

## Dependencies
- Auth Service (SSO)
- Data Warehouse (analytics)
- Stripe API (payments)

## Access
Request access via [ServiceNow ticket].
```
```

---

**API/Microservice:**
```markdown
## Ajustes de Foco

**Seções Essenciais:**
1. **API overview** (o que a API faz)
2. **Authentication** (como autenticar)
3. **Endpoints principais** (lista ou link para OpenAPI)
4. **Rate limits** (throttling)
5. **Examples** (curl, SDK examples)
6. **Error codes** (documentação de erros)
7. **Versioning** (estratégia de versões)
8. **Monitoring** (dashboards, logs)

**Tom:**
- API-first documentation
- Runnable examples
- Clear contracts (input/output)

**Estrutura Sugerida:**
```

# API Name

REST API for [purpose].

Base URL: `https://api.example.com/v1`

## Authentication

```bash
curl -H "Authorization: Bearer YOUR_TOKEN" \
  https://api.example.com/v1/resource
```

## Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /users | List users |
| POST | /users | Create user |

Full API Reference: [OpenAPI Spec](link)

## Rate Limits
- 100 requests/minute (authenticated)
- 10 requests/minute (unauthenticated)

## SDKs
- [JavaScript SDK](link)
- [Python SDK](link)
```
```

---

**Mobile App (iOS/Android):**
```markdown
## Ajustes de Foco

**Seções Essenciais:**
1. **App overview** (o que o app faz)
2. **Supported platforms** (iOS 14+, Android 10+)
3. **Development setup** (Xcode, Android Studio)
4. **Running locally** (simulators, devices)
5. **Build/release process** (CI/CD, app stores)
6. **Testing** (unit, UI, manual)
7. **Assets** (design files, marketing materials)

**Tom:**
- Mobile-specific concerns
- Platform differences (iOS vs Android)
- Design system reference

**Exemplo:**
```

# AppName

[Description] - Available on iOS and Android.

## Supported Platforms
- iOS 14.0+
- Android 10.0+ (API 29+)

## Development Setup

### iOS
```bash
cd ios && pod install
open AppName.xcworkspace
```

### Android
```bash
cd android && ./gradlew assembleDebug
```

## Design
- Figma: [link]
- Design System: [link]

## Release
- iOS: Fastlane → TestFlight → App Store
- Android: Fastlane → Internal Testing → Production
```
```

---

**CLI Tool:**
```markdown
## Ajustes de Foco

**Seções Essenciais:**
1. **Installation** (brew, npm, cargo, binary)
2. **Usage** (principais comandos com exemplos)
3. **Configuration** (config files, env vars)
4. **Examples** (casos de uso comuns)
5. **Troubleshooting** (problemas comuns)
6. **Shell completion** (se disponível)

**Tom:**
- Command-line focused
- Copy-paste ready
- Clear command syntax

**Exemplo:**
```

# tool-name

Fast [task] from the command line.

## Installation

```bash
# macOS
brew install tool-name

# npm
npm install -g tool-name

# Binary
curl -L https://releases.../tool-name | tar xz
```

## Usage

```bash
# Basic usage
tool-name command [options]

# Examples
tool-name init                    # Initialize project
tool-name build --watch           # Build with watch mode
tool-name deploy --env production # Deploy to production
```

## Configuration

Create `.toolrc.json`:

```json
{
  "option1": "value1",
  "option2": "value2"
}
```

## Commands

Run `tool-name --help` for full command reference.
```
```

---

## 💭 Filosofia

> **"Um bom README não explica tudo — ele explica o suficiente para começar e aponta para onde aprender mais."**

Este prompt garante que:
- **Clareza > Completude** - Melhor ser claro e incompleto que completo e confuso
- **Prático > Teórico** - Exemplos funcionais > explicações abstratas
- **Atualizado > Perfeito** - README vivo e 80% correto > README perfeito mas obsoleto
- **Acessível > Impressionante** - Qualquer dev entende > só experts entendem

**Princípios Fundamentais:**

1. **5-Minute Rule** - Alguém deve conseguir entender e começar em 5 minutos
2. **Copy-Paste Works** - Todos os exemplos de código devem funcionar
3. **Progressive Disclosure** - Info mais importante primeiro, detalhes depois
4. **Honest Documentation** - Explicite limitações, não esconda problemas
5. **Living Document** - Evolui com código, não é "write once"

---

## 🔄 Próximos Níveis (Evolução)

1. **README → Docs Site** - Expandir para documentação multi-página
2. **README → API Reference** - Auto-gerar docs de código (JSDoc, Swagger)
3. **README + CI/CD** - Validar exemplos automaticamente (readme-check)
4. **README Multilíngue** - i18n para audiência global
5. **README + Analytics** - Track quais seções são mais lidas
6. **README Templates** - Biblioteca de templates por tipo de projeto
7. **Interactive README** - Runnable examples in-browser (RunKit, CodeSandbox)

---

## 🧠 Extensões Possíveis

### Variações do Template:

- **README Minimal** - Versão ultra-enxuta (< 100 linhas)
- **README Comprehensive** - Versão detalhada (> 500 linhas)
- **README for Docs** - README que é gateway para docs extensas
- **README Marketing** - Mais product-focused (menos técnico)
- **README Technical** - 100% engenharia (zero marketing)

### Ferramentas Complementares:

```
README.md
    ↓
Markdown Linters → Vale, markdownlint
    ↓
Link Checkers → markdown-link-check
    ↓
Spell Check → cspell
    ↓
Screenshots → Playwright screenshots automáticos
    ↓
Badges → shields.io automáticos
    ↓
Docs Generator → MkDocs, Docusaurus, Nextra
```

### Automações:

- **Auto-update version badges** - CI/CD atualiza badges
- **Auto-generate table of contents** - markdown-toc
- **Auto-validate examples** - CI testa código do README
- **Auto-screenshot** - Captura screenshots de UI automaticamente
- **Auto-translate** - Tradução automática (com revisão humana)

---

## 💡 Dicas Práticas

### Para READMEs Melhores:

1. **Use Table of Contents** - Para READMEs > 200 linhas
2. **Screenshots/GIFs são ouro** - Mostre, não só conte
3. **Badge com propósito** - Só badges úteis (build, coverage, version)
4. **Links funcionam** - Teste todos os links regularmente
5. **Exemplos testados** - Execute todo código do README
6. **Versão no README** - Explicite para qual versão é o README
7. **Changelog link** - Aponte para changelog/releases
8. **ASCII art com moderação** - Se usar, use com bom gosto

### Estrutura de Seções (Ordem Sugerida):

```markdown
1. **Header** (nome + tagline + badges) ← 10s para entender
2. **Quick Start** (exemplo funcional) ← 2min para rodar
3. **Overview** (o que é, por que) ← 1min para contexto
4. **Features** (o que faz) ← 30s para avaliar
5. **Installation** (como instalar) ← 5min para setup
6. **Usage** (como usar) ← 10min para explorar
7. **Architecture** (como funciona) ← Entendimento profundo
8. **Development** (como desenvolver) ← Onboarding de devs
9. **Contributing** (como colaborar) ← Guia de contribuição
10. **Everything Else** (roadmap, FAQ, license, etc) ← Referência
```

### Checklist de Qualidade do README:

- [ ] Alguém sem contexto entende em < 2 minutos?
- [ ] Quick start funciona sem ajuda externa?
- [ ] Todos os comandos são copiáveis e funcionam?
- [ ] Todos os links estão funcionando?
- [ ] Badges são úteis e atualizados?
- [ ] Screenshots/diagramas são claros?
- [ ] Limitações conhecidas estão explícitas?
- [ ] Há caminho claro para docs detalhadas?
- [ ] Última atualização foi < 6 meses atrás?
- [ ] Contribuir é claro e convidativo?

### O que Incluir vs Linkar:

**Incluir no README:**
- ✅ Quick start (< 10 linhas de código)
- ✅ Comandos principais (install, run, test)
- ✅ Arquitetura high-level (1 parágrafo ou diagrama)
- ✅ Features principais (top 5-8)
- ✅ Requisitos mínimos

**Linkar para Docs Externas:**
- 🔗 API reference completa
- 🔗 Tutoriais detalhados
- 🔗 Guias de uso avançado
- 🔗 ADRs técnicos
- 🔗 Changelog detalhado
- 🔗 Contribution guide completo (se > 100 linhas)

### Anti-Patterns (Evite!):

❌ **README gigante** (> 1000 linhas) - Quebre em docs separadas
✅ **README conciso** (< 500 linhas) com links para docs

❌ **"Coming soon"** - Não prometa, entregue
✅ **Roadmap link** - Transparência sobre o que vem

❌ **Comandos sem contexto** - `npm install && npm start` (mas onde?)
✅ **Comandos com output esperado** - Mostre o que deve acontecer

❌ **Jargão excessivo** - "Leverages synergistic paradigms..."
✅ **Linguagem clara** - "Simplifies X by doing Y"

❌ **Screenshots desatualizados** - UI antiga
✅ **Screenshots atualizados** - Automatize se possível

---

## 🔗 Integração com Outros Templates

Este template funciona melhor em conjunto:

```
🌍 Vision & Problem Statement → Por que o projeto existe
    ↓
📋 Briefing → Contexto de criação
    ↓
📄 PRD → O que ele faz (features detalhadas)
    ↓
⚙️ NFRs → Como deve funcionar (qualidade)
    ↓
📐 Diagramas → Como está arquitetado
    ↓
🏗️ ADRs → Por que certas decisões técnicas
    ↓
🗺️ Roadmap + DoD → O que vem depois + O que é "pronto"
    ↓
📘 README (este) → Síntese de tudo + Porta de entrada
    ↓
📚 Docs Detalhadas → Aprofundamento (API, guias, etc)
    ↓
💻 Código → Implementação real
```

**Fluxo completo de uso:**
1. Crie Vision e PRD (defina o que construir)
2. Crie ADRs e Diagramas (defina como construir)
3. Crie README baseado nesses docs (síntese)
4. Mantenha README atualizado conforme código evolui
5. README aponta para docs detalhadas quando necessário
6. Use README como onboarding doc para novos devs
7. Revise README trimestralmente

---

## 📚 Exemplos Reais Completos

### Exemplo 1: Biblioteca Open-Source (JavaScript)

```markdown
# fast-cache

Lightning-fast, zero-dependency in-memory cache for Node.js.

![Build Status](https://img.shields.io/github/workflow/status/user/fast-cache/CI)
![Coverage](https://img.shields.io/codecov/c/github/user/fast-cache)
![npm version](https://img.shields.io/npm/v/fast-cache)
![License](https://img.shields.io/npm/l/fast-cache)

[Quick Start](#quick-start) | [API Docs](https://docs.fast-cache.dev) | [Examples](./examples) | [Contributing](#contributing)

---

## Overview

`fast-cache` is a high-performance, type-safe in-memory caching library for Node.js applications. It provides:

- **Fast:** Sub-millisecond operations with LRU eviction
- **Simple:** Minimal API surface, easy to learn
- **Type-safe:** First-class TypeScript support
- **Zero dependencies:** No bloat, small bundle size
- **Flexible:** TTL, max size, custom eviction policies

Perfect for caching API responses, computed results, or any frequently accessed data.

---

## Why fast-cache?

| Feature | fast-cache | node-cache | lru-cache |
|---------|-----------|------------|-----------|
| TypeScript | ✅ | ⚠️ | ✅ |
| Zero deps | ✅ | ❌ | ✅ |
| TTL support | ✅ | ✅ | ⚠️ |
| Performance | 🚀 | ⚡ | ⚡ |
| Bundle size | 2kb | 12kb | 8kb |

---

## Quick Start

### Installation

```bash
npm install fast-cache
# or
yarn add fast-cache
# or
pnpm add fast-cache
```

### Basic Usage

```typescript
import { Cache } from 'fast-cache';

// Create cache with max 1000 items
const cache = new Cache<string, User>({ maxSize: 1000 });

// Set with optional TTL (milliseconds)
cache.set('user:123', { id: '123', name: 'Alice' }, { ttl: 60000 });

// Get
const user = cache.get('user:123');
console.log(user); // { id: '123', name: 'Alice' }

// Delete
cache.delete('user:123');

// Clear all
cache.clear();
```

---

## Features

- **LRU Eviction:** Automatically removes least recently used items when full
- **TTL Support:** Per-key time-to-live with automatic expiration
- **Type Safety:** Full TypeScript support with generics
- **Statistics:** Built-in cache hit/miss tracking
- **Events:** Subscribe to cache events (set, get, evict, expire)
- **Serialization:** Optional persistence to disk

---

## API Reference

### Constructor

```typescript
new Cache<K, V>(options?: CacheOptions)
```

**Options:**
- `maxSize?: number` - Maximum number of items (default: 1000)
- `ttl?: number` - Default TTL in milliseconds (default: none)
- `onEvict?: (key: K, value: V) => void` - Eviction callback

### Methods

- `set(key: K, value: V, options?: { ttl?: number }): void`
- `get(key: K): V | undefined`
- `has(key: K): boolean`
- `delete(key: K): boolean`
- `clear(): void`
- `size(): number`
- `stats(): CacheStats`

Full API documentation: [docs.fast-cache.dev](https://docs.fast-cache.dev)

---

## Examples

### API Response Caching

```typescript
import { Cache } from 'fast-cache';

const apiCache = new Cache<string, Response>({ maxSize: 500, ttl: 300000 });

async function fetchUser(id: string) {
  const cached = apiCache.get(id);
  if (cached) return cached;

  const response = await fetch(`/api/users/${id}`);
  const user = await response.json();
  
  apiCache.set(id, user);
  return user;
}
```

### Computed Results Cache

```typescript
const computeCache = new Cache<string, number>({ maxSize: 100 });

function fibonacci(n: number): number {
  const key = `fib:${n}`;
  const cached = computeCache.get(key);
  if (cached !== undefined) return cached;

  const result = n <= 1 ? n : fibonacci(n - 1) + fibonacci(n - 2);
  computeCache.set(key, result);
  return result;
}
```

More examples: [./examples](./examples)

---

## Performance

Benchmarks on MacBook Pro M1 (Node.js 20):

```
Cache.set x 10,000,000 ops/sec ±0.5%
Cache.get x 15,000,000 ops/sec ±0.3%
Cache.has x 20,000,000 ops/sec ±0.2%
```

Run benchmarks: `npm run bench`

---

## Development

### Setup

```bash
git clone https://github.com/user/fast-cache.git
cd fast-cache
npm install
```

### Running Tests

```bash
npm test              # Run all tests
npm run test:watch    # Watch mode
npm run test:coverage # With coverage
```

### Building

```bash
npm run build         # Build for production
npm run dev           # Watch mode
```

### Project Structure

```
fast-cache/
├── src/
│   ├── cache.ts      # Core cache implementation
│   ├── types.ts      # TypeScript types
│   └── utils.ts      # Helper functions
├── tests/
│   ├── cache.test.ts
│   └── performance.bench.ts
├── examples/
│   ├── basic.ts
│   └── advanced.ts
└── docs/
    └── api.md
```

---

## Contributing

We welcome contributions! Please see [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines.

**Quick start:**
1. Fork the repo
2. Create a branch (`git checkout -b feature/amazing`)
3. Make changes and add tests
4. Ensure tests pass (`npm test`)
5. Commit (`git commit -m 'feat: add amazing feature'`)
6. Push and open a PR

**Code of Conduct:** [CODE_OF_CONDUCT.md](./CODE_OF_CONDUCT.md)

---

## Roadmap

- [ ] Persistence layer (save/load from disk)
- [ ] Cluster mode (shared cache across processes)
- [ ] Advanced eviction policies (LFU, ARC)
- [ ] Compression support
- [ ] Metrics export (Prometheus)

See full roadmap: [GitHub Projects](https://github.com/user/fast-cache/projects/1)

---

## Known Issues

- TTL precision is ~100ms due to internal sweep interval
- Not suitable for massive datasets (>10M items) - consider Redis
- No built-in distributed caching (single-process only)

See all issues: [GitHub Issues](https://github.com/user/fast-cache/issues)

---

## Documentation

- [API Reference](https://docs.fast-cache.dev)
- [Migration Guide](./docs/migration.md) (from node-cache)
- [Best Practices](./docs/best-practices.md)
- [FAQ](./docs/faq.md)

---

## License

MIT License - see [LICENSE](./LICENSE) file for details.

---

## Support

- **Issues:** [GitHub Issues](https://github.com/user/fast-cache/issues)
- **Discussions:** [GitHub Discussions](https://github.com/user/fast-cache/discussions)
- **Twitter:** [@fast_cache](https://twitter.com/fast_cache)

---

**Made with ❤️ by the fast-cache team**
```

---

### Exemplo 2: Produto SaaS (Startup)

```markdown
# TaskFlow - Smart Task Management for Remote Teams

Modern task management built for distributed teams who need clarity, not complexity.

[Try Demo](https://demo.taskflow.app) | [Documentation](https://docs.taskflow.app) | [Roadmap](#roadmap)

---

## What We're Building

TaskFlow is a task management platform designed for remote-first teams. Unlike traditional project management tools that overwhelm users with features, TaskFlow focuses on three core principles:

1. **Clarity:** See what matters, hide what doesn't
2. **Speed:** Create and assign tasks in seconds, not minutes
3. **Collaboration:** Real-time updates, contextual conversations

**Problem We Solve:**
Remote teams waste 2-3 hours/week in status meetings and Slack threads trying to figure out who's doing what. TaskFlow gives everyone a shared source of truth without the overhead.

**Who It's For:**
- Remote/hybrid teams (5-50 people)
- Product, engineering, and design teams
- Teams tired of Jira but need more than Trello

---

## Key Features

### Core Functionality
- **Smart Boards:** Kanban boards that auto-organize by priority and deadline
- **Quick Capture:** Create tasks via Slack, email, or browser extension
- **Time Tracking:** Built-in time tracking with productivity insights
- **Integrations:** GitHub, Slack, Figma, Linear, and more

### What Makes Us Different
- **AI-Powered Summaries:** Daily digest of what happened across all boards
- **Focus Mode:** Hides noise, shows only your tasks for the day
- **Async-First:** Designed for teams across timezones (no real-time required)
- **Mobile-Native:** Full-featured iOS and Android apps

---

## Tech Stack

**Frontend:**
- React 18 + TypeScript
- Next.js 14 (App Router)
- Tailwind CSS + Radix UI
- TanStack Query (data fetching)
- Zustand (state management)

**Backend:**
- Node.js 20 + Express
- PostgreSQL 16 (primary DB)
- Redis (caching, queues)
- Prisma (ORM)

**Infrastructure:**
- Hosting: Vercel (frontend), AWS ECS (backend)
- Database: AWS RDS PostgreSQL
- Storage: AWS S3
- Monitoring: Datadog
- CI/CD: GitHub Actions

**External Services:**
- Auth: Clerk
- Payments: Stripe
- Email: Resend
- Analytics: PostHog

---

## Development Setup

### Prerequisites

- Node.js 20+
- PostgreSQL 16+
- Redis 7+
- pnpm 8+

### Installation

```bash
# Clone repo
git clone https://github.com/taskflow/taskflow.git
cd taskflow

# Install dependencies
pnpm install

# Setup environment
cp .env.example .env.local
# Edit .env.local with your API keys

# Setup database
pnpm db:migrate
pnpm db:seed

# Start dev servers
pnpm dev
```

This starts:
- Frontend: http://localhost:3000
- Backend API: http://localhost:4000
- Storybook: http://localhost:6006

### Project Structure

```
taskflow/
├── apps/
│   ├── web/              # Next.js frontend
│   ├── api/              # Express backend
│   └── mobile/           # React Native app
├── packages/
│   ├── ui/               # Shared UI components
│   ├── database/         # Prisma schema
│   ├── auth/             # Auth utilities
│   └── integrations/     # Third-party integrations
├── docs/                 # Documentation
└── scripts/              # Automation scripts
```

---

## Development Workflow

### Running Tests

```bash
pnpm test                # All tests
pnpm test:unit           # Unit tests
pnpm test:integration    # Integration tests
pnpm test:e2e            # E2E tests (Playwright)
```

### Code Quality

```bash
pnpm lint                # ESLint
pnpm type-check          # TypeScript
pnpm format              # Prettier
```

### Database

```bash
pnpm db:migrate          # Run migrations
pnpm db:seed             # Seed test data
pnpm db:studio           # Prisma Studio (DB GUI)
pnpm db:reset            # Reset DB (destructive!)
```

---

## Deployment

### Staging

Automatic deployment on push to `main` branch:
- Frontend: https://staging.taskflow.app
- API: https://api-staging.taskflow.app

### Production

Manual deployment via GitHub Actions:

```bash
# Tag release
git tag -a v1.2.3 -m "Release v1.2.3"
git push origin v1.2.3

# Triggers production deploy
```

Production URLs:
- Frontend: https://taskflow.app
- API: https://api.taskflow.app

---

## Architecture

### High-Level Overview

```
┌─────────────┐
│   Browser   │
│  (Next.js)  │
└──────┬──────┘
       │ API calls
       ↓
┌─────────────┐      ┌──────────────┐
│   Vercel    │────→ │   AWS ECS    │
│  (Frontend) │      │  (Backend)   │
└─────────────┘      └───────┬──────┘
                             │
                    ┌────────┴────────┐
                    ↓                 ↓
              ┌──────────┐      ┌─────────┐
              │PostgreSQL│      │  Redis  │
              │  (RDS)   │      │(Cache)  │
              └──────────┘      └─────────┘
```

### Key Architectural Decisions

- **ADR-001:** [Why Next.js App Router](./docs/adr/001-nextjs-app-router.md)
- **ADR-002:** [Why PostgreSQL over MongoDB](./docs/adr/002-postgresql.md)
- **ADR-003:** [Why Clerk for Auth](./docs/adr/003-clerk-auth.md)
- **ADR-004:** [Multi-Tenancy Strategy](./docs/adr/004-multi-tenancy.md)

Full ADRs: [./docs/adr](./docs/adr)

---

## Quality Standards

### Definition of Done

Every feature must meet:
- [ ] Functional requirements from PRD met
- [ ] Unit tests (> 80% coverage)
- [ ] Integration tests for critical paths
- [ ] E2E test for happy path
- [ ] Code review approved
- [ ] Design approved (if UI)
- [ ] Performance acceptable (Lighthouse > 90)
- [ ] Accessibility checked (WCAG AA)
- [ ] Deployed to staging and tested
- [ ] PM approved

Full DoD: [docs/dod.md](./docs/dod.md)

### Non-Functional Requirements

- **Performance:** API responds < 200ms (p95)
- **Availability:** 99.5% uptime
- **Scalability:** 10k simultaneous users
- **Security:** HTTPS only, JWT auth, rate limiting
- **Compliance:** GDPR, LGPD compliant

Full NFRs: [docs/nfrs.md](./docs/nfrs.md)

---

## Roadmap

### Q1 2026 (Now)
- ✅ Core task management (boards, tasks, assignments)
- ✅ Slack integration
- 🔄 GitHub integration (in progress)
- 🔄 Time tracking

### Q2 2026 (Next)
- Recurring tasks
- Custom fields
- Advanced search
- Mobile apps (iOS, Android)

### Q3 2026 (Later)
- Reporting and analytics
- Automation rules
- AI task suggestions
- API v2 with webhooks

Full roadmap: [docs/roadmap.md](./docs/roadmap.md)

---

## Contributing

We're not open-source yet, but accepting contributions from team members and partners.

**For Team Members:**
1. Pick issue from [Project Board](https://github.com/orgs/taskflow/projects/1)
2. Create feature branch: `feature/issue-123-description`
3. Follow DoD checklist
4. Open PR and request review
5. Address feedback
6. Merge when approved

**Code Style:**
- TypeScript strict mode
- Functional components (React)
- Test coverage > 80%
- ESLint + Prettier enforced

**Commit Convention:**
- `feat:` new feature
- `fix:` bug fix
- `docs:` documentation
- `refactor:` code restructure
- `test:` add tests

---

## Known Issues and Limitations

### Current Limitations
- Mobile apps in beta (some features missing)
- Webhooks not available yet (coming Q2)
- No offline mode (web app requires connection)
- Search limited to exact matches (no fuzzy search yet)

### Known Bugs
- [ ] Drag-and-drop flaky on Safari < 17 ([#234](https://github.com/taskflow/taskflow/issues/234))
- [ ] Time tracking stops on browser sleep ([#289](https://github.com/taskflow/taskflow/issues/289))

See all: [GitHub Issues](https://github.com/taskflow/taskflow/issues)

---

## Documentation

- **Product:** [docs/prd.md](./docs/prd.md) - Product requirements
- **Architecture:** [docs/architecture.md](./docs/architecture.md) - System design
- **ADRs:** [docs/adr/](./docs/adr/) - Technical decisions
- **API:** [docs/api.md](./docs/api.md) - API reference
- **Runbooks:** [docs/runbooks/](./docs/runbooks/) - Operational guides

---

## Team and Contact

**Product:** @alice (PM)
**Engineering:** @bob (Tech Lead), @charlie, @diana
**Design:** @eve (Lead Designer)

**Channels:**
- Slack: #taskflow-dev
- Email: dev@taskflow.app
- Issues: GitHub Issues
- Meetings: Mondays 10am PT (engineering sync)

---

## License

Proprietary - Copyright (c) 2026 TaskFlow, Inc.

---

**Built with ❤️ by a distributed team across 5 timezones**
```

---

**Criado para transformar documentação técnica em READMEs claros, úteis e que realmente ajudam desenvolvedores a começar rapidamente.**
