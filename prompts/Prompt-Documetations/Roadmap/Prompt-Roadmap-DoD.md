# 🗺️ Template de Geração de Roadmap + Definition of Done (DoD) - Cursor IDE

Template de prompt baseado em **planejamento estratégico e operacional** para transformar documentação de produto em **roadmap acionável** e **critérios claros de conclusão**. Ideal para garantir alinhamento entre produto, engenharia, QA e stakeholders sobre o que será entregue e quando algo está realmente pronto.

---

## 📝 Template do Prompt

Copie e personalize o template abaixo. Este prompt utiliza **documentação existente** (Vision, PRD, NFRs) para criar roadmap e DoD.

```markdown
## Role (Identidade da IA)

Você é um **Product Manager sênior e Delivery Manager** com experiência em:
- Planejamento estratégico e roadmaps orientados a valor
- Priorização baseada em impacto (RICE, Value vs Effort)
- Coordenação cross-funcional (produto, engenharia, design, QA)
- Definição de critérios de conclusão (Definition of Done)
- Gestão de dependências e riscos
- Frameworks de entrega (Scrum, Kanban, Shape Up)

Você domina produtos de {{dominio}} (ex.: SaaS, fintech, e-commerce, mobile, plataformas internas).

## Objetivo

Transformar a **documentação fornecida** em dois artefatos complementares:

1. **Roadmap de Produto** - Visão estratégica de entregas priorizadas ao longo do tempo
2. **Definition of Done (DoD)** - Critérios objetivos e verificáveis de conclusão

Esses artefatos serão utilizados por produto, engenharia, QA, design e stakeholders para alinhamento e execução.

## Contexto

**Roadmap** responde:
- O que vamos construir?
- Em que ordem?
- Por que isso importa?
- Quando aproximadamente?

**Definition of Done** responde:
- Como sabemos que algo está realmente pronto?
- Quais critérios de qualidade devem ser atendidos?
- Quem precisa aprovar?
- O que não pode ser esquecido?

## Entrada (Fonte de Verdade)

O usuário fornecerá documentação existente:

- 🌍 **Vision & Problem Statement** - Estratégia e direção
- 📋 **Briefing** - Contexto e restrições
- 📄 **PRD** - Requisitos funcionais detalhados
- ⚙️ **NFRs** - Requisitos de qualidade
- 🏗️ **ADRs** - Decisões arquiteturais (se existirem)
- 📐 **Diagramas** - Visão técnica (se existirem)

Use **exclusivamente** esses documentos como fonte.

## Tarefa Principal

### Parte 1: Roadmap de Produto

1. **Analisar a documentação** para identificar iniciativas e features
2. **Agrupar por fases** (Now/Next/Later, trimestral, ou por objetivo)
3. **Priorizar** baseado em valor, impacto e dependências
4. **Mapear dependências** entre iniciativas
5. **Identificar riscos** de cada fase
6. **Definir outcomes esperados** (não apenas outputs)

### Parte 2: Definition of Done (DoD)

1. **Criar DoD Global** aplicável a todas as entregas
2. **Criar DoDs específicos** por tipo (feature, bug, débito técnico)
3. **Definir critérios mensuráveis** e verificáveis
4. **Mapear responsáveis** por validação
5. **Incluir checkpoints de qualidade**
6. **Conectar com NFRs** quando relevante

## Estrutura do Roadmap

### Opções de Formato (escolha a mais adequada):

#### Opção 1: Now / Next / Later (Recomendado para MVPs e startups)
- **Now** - Próximos 0-3 meses (alta confiança)
- **Next** - 3-6 meses (média confiança, pode mudar)
- **Later** - 6-12 meses (ideias, baixa confiança)

#### Opção 2: Trimestral (Recomendado para empresas estabelecidas)
- **Q1 2026** - Janeiro a Março
- **Q2 2026** - Abril a Junho
- **Q3 2026** - Julho a Setembro
- **Q4 2026** - Outubro a Dezembro

#### Opção 3: Por Objetivos Estratégicos (Recomendado para transformações)
- **Fundação** - Viabilidade técnica
- **Crescimento** - Adoção e escala
- **Otimização** - Eficiência e rentabilidade

#### Opção 4: Por Fase do Produto (Recomendado para novos produtos)
- **Discovery & MVP** - Validação
- **Product-Market Fit** - Iteração
- **Scale** - Crescimento
- **Optimize** - Eficiência

### Para Cada Fase/Período, Forneça:

| Campo | Descrição |
|-------|-----------|
| **Iniciativa/Feature** | Nome descritivo |
| **Descrição** | O que será construído (breve) |
| **Objetivo/Valor** | Por que isso importa, outcome esperado |
| **Dependências** | O que precisa existir antes |
| **Riscos** | O que pode dar errado |
| **Status** | Planejado / Em progresso / Concluído |

### Critérios de Priorização

Use framework explícito (escolha um):

**RICE Score:**
- Reach (alcance)
- Impact (impacto)
- Confidence (confiança)
- Effort (esforço)

**Value vs Effort:**
- Quick wins (alto valor, baixo esforço)
- Major projects (alto valor, alto esforço)
- Fill-ins (baixo valor, baixo esforço)
- Time sinks (baixo valor, alto esforço)

**MoSCoW:**
- Must-have (crítico para lançamento)
- Should-have (importante mas não bloqueante)
- Could-have (nice-to-have)
- Won't-have (explicitamente fora de escopo)

## Estrutura da Definition of Done

### DoD Global (Aplicável a Todas as Entregas)

Checklist mínimo:

**Requisitos e Qualidade:**
- [ ] Requisitos funcionais do PRD atendidos
- [ ] NFRs aplicáveis atendidos
- [ ] Critérios de aceitação validados
- [ ] Edge cases considerados

**Testes:**
- [ ] Testes unitários escritos e passando
- [ ] Testes de integração relevantes
- [ ] Testes manuais executados
- [ ] Smoke test em ambiente de staging

**Código:**
- [ ] Code review aprovado
- [ ] Sem dívida técnica crítica introduzida
- [ ] Sem vulnerabilidades de segurança conhecidas
- [ ] Performance aceitável (conforme NFRs)

**Documentação:**
- [ ] README/docs técnicos atualizados
- [ ] Documentação de API (se aplicável)
- [ ] Changelog atualizado
- [ ] Comentários em código complexo

**Deploy e Operação:**
- [ ] CI/CD pipeline passando
- [ ] Deploy em staging bem-sucedido
- [ ] Rollback plan documentado
- [ ] Monitoring/alertas configurados

**Aprovações:**
- [ ] Product Owner aprovou
- [ ] QA aprovou
- [ ] Design aprovou (se UI)
- [ ] Tech lead aprovou

### DoDs Específicos por Tipo

Personalize por contexto.

## Estrutura Esperada da Resposta

# PARTE 1: ROADMAP DE PRODUTO

### 1. Visão Geral do Roadmap
- Objetivo e horizonte temporal
- Premissas principais
- Critério de priorização usado

### 2. Roadmap Detalhado

#### [Fase/Período 1]

| Iniciativa | Descrição | Objetivo/Valor | Dependências | Riscos | Status |
|------------|-----------|----------------|--------------|--------|--------|
| [Nome] | [O que] | [Por que] | [Antes disso] | [O que pode dar errado] | [Estado] |

### 3. Dependências Críticas
- Mapeamento visual ou lista

### 4. Riscos e Mitigações
- Principais riscos do roadmap
- Estratégias de mitigação

### 5. Fora de Escopo
- O que explicitamente não está no roadmap

---

# PARTE 2: DEFINITION OF DONE (DoD)

### 6. Objetivo da DoD
- Por que existe
- Como será usada

### 7. DoD Global
- Checklist aplicável a tudo

### 8. DoDs Específicos
- Por tipo de entrega (feature, bug, tech debt)

### 9. Responsáveis por Validação
- Quem aprova o quê

### 10. Métricas de Qualidade
- Indicadores de sucesso
- Sinais de alerta

### 11. Exceções e Casos Especiais
- Quando DoD pode ser relaxada
- Processo de exceção

---

### 12. Lacunas e Perguntas em Aberto
- Informações faltantes
- Decisões pendentes

## Diretrizes

- **Seja realista:** Não prometa o impossível
- **Seja específico:** Evite termos vagos ("melhorar", "otimizar")
- **Seja orientado a valor:** Conecte features com outcomes
- **Seja transparente:** Explicite riscos e incertezas
- **Seja verificável:** DoD deve ser testável/auditável
- **Não assuma datas:** Use períodos amplos (trimestre, fase)

## Formato da Resposta

1. **Gere apenas** Roadmap + DoD
2. **Utilize Markdown** estruturado com tabelas e checklists
3. **Use diagramas simples** quando útil (ASCII ou Mermaid)
4. **Sem emojis** no documento final
5. **Pronto para:** Planejamento, alinhamento de stakeholders, execução, tracking

## Restrições

- ❌ Não inventar features ou iniciativas não mencionadas
- ❌ Não assumir tecnologias específicas (a menos que seja ADR)
- ❌ Não prometer datas exatas sem base sólida
- ❌ Não criar DoD impossível de cumprir
- ✅ Derivar exclusivamente da documentação fornecida
- ✅ Priorizar baseado em valor e impacto explícitos
- ✅ Ser honesto sobre incertezas e riscos
- ✅ Conectar roadmap com objetivos estratégicos (Vision)
```

---

## 🚀 Como Usar

### 1️⃣ Fluxo Recomendado (Product Development Pipeline)

Este prompt é usado após definição estratégica e requisitos:

```
1️⃣ Vision & Problem Statement → Direção estratégica
         ↓
2️⃣ Briefing → Contexto e restrições
         ↓
3️⃣ PRD → Requisitos funcionais
         ↓
4️⃣ NFRs → Requisitos de qualidade
         ↓
5️⃣ Diagramas → Visão técnica
         ↓
6️⃣ Roadmap + DoD (este) → Planejamento e critérios de qualidade
         ↓
7️⃣ Backlog → Stories e tasks
         ↓
8️⃣ Sprints → Execução
         ↓
9️⃣ Release → Deploy para produção
```

**Vantagens de Criar Roadmap + DoD Cedo:**
- Alinha expectativas de stakeholders
- Facilita estimativas e planejamento de recursos
- Garante qualidade consistente
- Reduz ambiguidade sobre "quando" e "o que é pronto"
- Permite tracking de progresso

### 2️⃣ Onde Usar

- **Cursor IDE** → Cole como system prompt + forneça PRD/Vision
- **Notion/Confluence** → Documentação de planejamento
- **Jira/Linear** → Criação de roadmap visual
- **Miro/FigJam** → Workshops de planejamento
- **Google Docs** → Documentação para stakeholders
- **GitHub Projects** → Roadmap público

### 3️⃣ Exemplo Prático Completo

**Entrada (PRD Resumido + NFRs):**

```markdown
# PRD - Plataforma de Agendamento Online

**Vision:** Simplificar agendamento de serviços locais.

**Features Principais:**
1. Cadastro de prestadores (salões, clínicas, etc.)
2. Busca e descoberta por localização
3. Sistema de agendamento com calendário
4. Pagamento integrado
5. Sistema de avaliações
6. Notificações (email, SMS, push)
7. Dashboard para prestadores

**NFRs Críticos:**
- Performance: Busca < 500ms
- Disponibilidade: 99.5% uptime
- Segurança: PCI-DSS para pagamentos
- Escalabilidade: 10k agendamentos/dia

**Contexto:**
- Time: 5 engenheiros, 1 PM, 1 designer
- Prazo: Lançamento em 6 meses
- Budget: Limitado (startup seed stage)
```

**Saída Esperada:**

A IA gerará roadmap completo (Now/Next/Later ou trimestral) + DoD detalhada.

---

## 💡 Por Que Este Prompt Funciona

### ✅ 1. Alinhamento Estratégico + Operacional
- Roadmap conecta entregas com objetivos estratégicos (Vision)
- DoD garante que "pronto" significa a mesma coisa para todos
- Reduz desalinhamento entre produto, engenharia e stakeholders
- Facilita comunicação com executivos e investidores

### ✅ 2. Priorização Baseada em Valor
- Foca em outcomes (resultados), não apenas outputs (features)
- Explicita critérios de priorização (RICE, Value vs Effort, MoSCoW)
- Identifica quick wins e projetos de longo prazo
- Evita feature factory (construir sem propósito)

### ✅ 3. Gestão de Dependências e Riscos
- Mapeia dependências entre iniciativas
- Identifica riscos cedo (technical debt, integrações, terceiros)
- Permite planejamento de mitigações
- Reduz surpresas durante execução

### ✅ 4. Qualidade Consistente via DoD
- Estabelece padrão mínimo de qualidade
- Previne shortcuts que geram dívida técnica
- Facilita onboarding de novos membros
- Reduz retrabalho e bugs em produção

### ✅ 5. Transparência e Flexibilidade
- Now/Next/Later permite adaptação sem quebrar compromissos
- Explicita incertezas e lacunas
- Facilita repriorização baseada em learnings
- Suporta metodologias ágeis (iteração)

### ✅ 6. Escalável e Adaptável
Funciona para:
- MVPs (roadmap enxuto, DoD essencial)
- Scale-ups (roadmap detalhado, DoD rigorosa)
- Enterprises (roadmaps multi-times, DoDs por squad)
- Diferentes domínios (SaaS, mobile, fintech, etc.)

---

## ⚠️ Observações Importantes

### O que este prompt faz:
- ✅ Cria roadmap orientado a valor e impacto
- ✅ Define critérios claros de "pronto"
- ✅ Mapeia dependências e riscos
- ✅ Prioriza baseado em frameworks explícitos
- ✅ Conecta entregas com objetivos estratégicos
- ✅ Fornece estrutura para tracking e comunicação
- ✅ Identifica lacunas na documentação

### O que este prompt NÃO faz:
- ❌ Não cria plano de sprint detalhado (use após)
- ❌ Não estima em story points ou horas
- ❌ Não define arquitetura técnica (use ADRs)
- ❌ Não cria user stories detalhadas (use após)
- ❌ Não substitui discovery contínuo
- ❌ Não garante sucesso do produto (execution matters)

### Quando usar este prompt:
- **Use quando:**
  - PRD está completo ou quase completo
  - Vision está clara
  - Precisa alinhar expectativas de stakeholders
  - Vai iniciar planejamento de sprints
  - Quer estabelecer padrão de qualidade
  - Time cresce e precisa de alinhamento
  - Stakeholders perguntam "quando vem X?"

- **Não use quando:**
  - Produto ainda está em discovery puro (use Vision/Briefing primeiro)
  - PRD está muito incompleto ou vago
  - É um protótipo/throwaway descartável
  - Roadmap já está rigidamente definido
  - Time é muito pequeno (1-2 pessoas, comunicação informal funciona)

---

## 🔄 Personalização Avançada

### Para Diferentes Contextos:

**Startup Seed/Pre-Seed (MVP Focus):**
```markdown
## Ajustes de Contexto

**Roadmap:**
- Use Now/Next/Later (não trimestres)
- Now = Próximas 4-6 semanas apenas
- Foco em validação, não escala
- Priorize por learning value

**DoD:**
- DoD minimalista (essencial apenas)
- Aceite alguma dívida técnica
- Foco em funcionalidade core
- Menos rigor em documentação
- Mais rigor em métricas de produto
```

**Startup Series A/B (Product-Market Fit → Scale):**
```markdown
## Ajustes de Contexto

**Roadmap:**
- Use trimestral (Q1, Q2, Q3, Q4)
- Balance entre growth e tech debt
- Inclua iniciativas de infra/plataforma
- Priorize por impacto em métricas north star

**DoD:**
- DoD completa mas pragmática
- Inclua performance e monitoramento
- Exija code review e testes
- Documentação obrigatória
- Security review para features críticas
```

**Enterprise/Corporate:**
```markdown
## Ajustes de Contexto

**Roadmap:**
- Use anual (com revisões trimestrais)
- Inclua iniciativas de compliance
- Considere múltiplos times/squads
- Alinhe com OKRs corporativos

**DoD:**
- DoD rigorosa e detalhada
- Inclua security, compliance, accessibility
- Exija documentação completa
- Múltiplos níveis de aprovação
- Testes de carga obrigatórios
- Rollback plan documentado
```

**Mobile App (iOS/Android):**
```markdown
## Ajustes de Contexto

**Roadmap:**
- Considere review time (App Store: 1-3 dias)
- Planeje releases maiores (não pode patchar rápido)
- Inclua suporte a versões antigas de OS
- Sincronize lançamentos iOS/Android

**DoD:**
- Testes em múltiplos devices/OS versions
- Performance em devices low-end
- App Store guidelines compliance
- Screenshots e marketing assets prontos
- Testes de conectividade offline
```

**B2B SaaS:**
```markdown
## Ajustes de Contexto

**Roadmap:**
- Balance feedback de clientes vs visão de produto
- Inclua iniciativas de enterprise features
- Considere migration/upgrade paths
- Alinhe com ciclos de vendas

**DoD:**
- Multi-tenancy testado
- Backward compatibility garantida
- Migration scripts testados
- Customer comms preparada
- CS/Support treinado
```

**Plataforma/API:**
```markdown
## Ajustes de Contexto

**Roadmap:**
- Considere breaking changes (versioning)
- Planeje deprecation de APIs antigas
- Inclua SDKs/docs para desenvolvedores
- Beta releases para early adopters

**DoD:**
- API docs completas (OpenAPI/Swagger)
- SDKs atualizados (se aplicável)
- Testes de carga passando
- Exemplos de código prontos
- Changelog detalhado
- Deprecation notices (se aplicável)
```

---

## 💭 Filosofia

> **"Um roadmap sem DoD é uma promessa sem garantia. Uma DoD sem roadmap é qualidade sem direção."**

Este prompt garante que:
- **Planejamento não é wishful thinking**, mas baseado em realidade
- **Qualidade não é negociável**, mas adaptável ao contexto
- **Priorização é transparente**, não política ou aleatória
- **Progresso é mensurável**, não subjetivo

**Princípios Fundamentais:**

1. **Outcomes > Outputs** - Foque em impacto, não em features
2. **Qualidade Consistente** - DoD previne atalhos perigosos
3. **Transparência** - Explicite riscos, dependências e incertezas
4. **Flexibilidade** - Roadmap evolui com learnings
5. **Alinhamento** - Um roadmap para governar todos os times

---

## 🔄 Próximos Níveis (Evolução)

1. **Roadmap → OKRs** - Conectar iniciativas com objetivos e key results
2. **Roadmap → Resource Planning** - Estimar esforço e alocar pessoas
3. **DoD → Automated Checks** - Gates automáticos em CI/CD
4. **DoD → Quality Metrics Dashboard** - Visualizar compliance real-time
5. **Roadmap → Public Roadmap** - Versão para clientes/usuários
6. **Roadmap → Release Notes** - Auto-geração de changelogs
7. **DoD → Production Readiness Checklist** - Expansão para go-live

---

## 🧠 Extensões Possíveis

### Variações do Template:

- **Roadmap Lean Canvas** - Versão visual em uma página
- **Roadmap por Persona** - Priorizando por segmento de usuário
- **Roadmap Orientado a Métricas** - Features associadas a KPIs
- **DoD por Squad** - Permitir personalização por time
- **DoD para Diferentes Ambientes** - Dev, Staging, Production

### Integrações com Ferramentas:

```
Roadmap + DoD
    ↓
Jira/Linear → Criação automática de epics e DoD nos tickets
    ↓
GitHub → Checklist em PRs baseada em DoD
    ↓
Notion → Dashboard de roadmap visual
    ↓
Slack → Notificações de conclusão baseadas em DoD
    ↓
CI/CD → Automated quality gates
```

### Frameworks Complementares:

- **RICE Scoring** - Priorização quantitativa
- **OKRs** - Conectar roadmap com objetivos
- **Shape Up** - Ciclos de 6 semanas com cooldown
- **Dual-Track Agile** - Discovery + Delivery em paralelo
- **Continuous Discovery** - Integrar learnings no roadmap

---

## 💡 Dicas Práticas

### Para Roadmaps Melhores:

1. **Comunique incerteza** - Use confidence intervals (alta/média/baixa)
2. **Evite feature creep** - Diga "não" com dados
3. **Reserve buffer** - 20-30% para imprevistos e tech debt
4. **Revise regularmente** - Trimestral mínimo, mensal ideal
5. **Mostre progresso** - Status visual (Planejado/Em Progresso/Concluído)
6. **Conecte com métricas** - "Feature X aumentará retenção em Y%"
7. **Use temas** - Agrupe features por objetivo estratégico

### Para DoDs Melhores:

1. **Seja específico** - "Testes passando" > "Testado"
2. **Seja verificável** - Alguém pode checar objetivamente?
3. **Seja realista** - DoD impossível será ignorada
4. **Evolua com maturidade** - MVP tem DoD diferente de Scale
5. **Automatize quando possível** - CI/CD checks são melhores que checklist manual
6. **Revise após incidentes** - Adicione checks que teriam prevenido bugs
7. **Inclua exceções** - Processo para hotfixes que relaxam DoD

### Checklist de Qualidade do Roadmap:

- [ ] Cada iniciativa tem objetivo/valor claro?
- [ ] Priorização está justificada (framework usado)?
- [ ] Dependências estão mapeadas?
- [ ] Riscos principais estão identificados?
- [ ] Horizonte temporal é realista (não overpromising)?
- [ ] Conecta com Vision e objetivos estratégicos?
- [ ] Fora de escopo está explícito?
- [ ] Stakeholders revisaram e alinharam?

### Checklist de Qualidade da DoD:

- [ ] Todos os itens são verificáveis objetivamente?
- [ ] Responsáveis por aprovação estão claros?
- [ ] Cobre requisitos, testes, código, docs, deploy?
- [ ] É realista para o contexto (não impossível)?
- [ ] Está alinhada com NFRs?
- [ ] Processo de exceção está documentado?
- [ ] Time inteiro conhece e concorda com a DoD?
- [ ] Pode ser parcialmente automatizada?

### Padrões Anti-Pattern (Evite!):

❌ **Roadmap com datas fixas** - "Feature X dia 15/março/2026"
✅ **Roadmap com períodos** - "Feature X no Q1 2026"

❌ **Roadmap só de features** - Lista de funcionalidades
✅ **Roadmap orientado a outcomes** - "Reduzir churn em 20% via..."

❌ **DoD genérica** - "Feito conforme especificado"
✅ **DoD específica** - "Testes unitários > 80%, code review aprovado"

❌ **DoD inflexível** - Mesma DoD para MVP e Scale
✅ **DoD contextual** - Adapta ao estágio do produto

---

## 🔗 Integração com Outros Templates

Este template funciona melhor em conjunto:

```
🌍 Vision & Problem Statement → Direção estratégica
    ↓
📋 Briefing → Contexto e stakeholders
    ↓
📄 PRD → Requisitos funcionais detalhados
    ↓
⚙️ NFRs → Atributos de qualidade
    ↓
📐 Diagramas → Visão técnica
    ↓
🗺️ Roadmap + DoD (este) → O que e quando + Como sabemos que está pronto
    ↓
🏗️ ADRs → Decisões técnicas durante implementação
    ↓
📋 Backlog → Stories e tasks detalhadas
    ↓
🔄 Sprints → Execução iterativa
    ↓
✅ Release → Deploy guiado pela DoD
    ↓
📊 Retrospective → Melhoria contínua (atualiza Roadmap e DoD)
```

**Fluxo completo de uso:**
1. Crie Vision (direção) e PRD (requisitos)
2. Gere Roadmap baseado no PRD (este template - parte 1)
3. Gere DoD baseado nos NFRs (este template - parte 2)
4. Use Roadmap para comunicar com stakeholders
5. Use DoD como critério de aceitação em todas as entregas
6. Revise Roadmap trimestralmente baseado em progresso
7. Evolua DoD baseado em incidentes e maturidade do time

---

## 📚 Exemplos Reais Completos

### Exemplo 1: Plataforma de Agendamento Online (Startup MVP)

```markdown
# Roadmap + DoD - BookEasy (Plataforma de Agendamento)

## PARTE 1: ROADMAP DE PRODUTO

### 1. Visão Geral do Roadmap

**Objetivo:** Lançar MVP em 4 meses e alcançar 50 prestadores e 500 agendamentos/mês em 6 meses.

**Horizonte Temporal:** Now/Next/Later (revisão mensal)

**Premissas:**
- Time: 4 engenheiros full-stack, 1 PM, 1 designer
- Stack: Next.js + Supabase + Vercel (low infra overhead)
- Budget: $5k/mês infra + $50k para 6 meses de pessoal
- Foco: Salões de beleza inicialmente (vertical específica)

**Critério de Priorização:** Value vs Effort (priorizamos Quick Wins e Must-Haves)

---

### 2. Roadmap Detalhado

#### 🟢 NOW (Próximos 2 meses - Fevereiro a Março 2026)

**Tema:** MVP Core - Viabilidade Técnica e Funcional

| Iniciativa | Descrição | Objetivo/Valor | Dependências | Riscos | Status |
|------------|-----------|----------------|--------------|--------|--------|
| **Auth e Onboarding** | Login/cadastro para prestadores e clientes (OAuth + email) | Permitir que usuários criem contas | - | Integração OAuth pode levar +1 semana | ⏳ Em Progresso |
| **Perfil de Prestador** | Cadastro de salão (nome, endereço, fotos, horário funcionamento) | Prestadores conseguem se listar na plataforma | Auth | Validação de endereço complexa | 📋 Planejado |
| **Calendário de Disponibilidade** | Prestadores definem horários disponíveis (grid semanal) | Base para sistema de agendamento | Perfil Prestador | UX complexa, pode precisar 2 iterações | 📋 Planejado |
| **Busca Básica** | Busca por nome ou CEP (sem filtros avançados) | Clientes encontram prestadores | Perfil Prestador | - | 📋 Planejado |
| **Agendamento (V1)** | Cliente escolhe horário disponível e confirma | Core do produto, first booking | Calendário + Busca | Conflitos de horário se não bloquear corretamente | 📋 Planejado |
| **Notificações Email** | Email de confirmação e lembrete 24h antes | Reduzir no-shows | Agendamento V1 | Deliverability (pode ser bloqueado como spam) | 📋 Planejado |

**Outcome Esperado:** MVP funcional que permite primeiro agendamento end-to-end.

---

#### 🟡 NEXT (3-4 meses - Abril a Maio 2026)

**Tema:** Product-Market Fit - Retenção e Qualidade

| Iniciativa | Descrição | Objetivo/Valor | Dependências | Riscos | Status |
|------------|-----------|----------------|--------------|--------|--------|
| **Sistema de Avaliações** | Clientes avaliam prestadores (1-5 estrelas + comentário) | Trust e descoberta (social proof) | Agendamento concluído | Avaliações falsas/manipuladas | 📋 Planejado |
| **Dashboard Prestador** | Visualizar agendamentos, histórico, avaliações | Prestadores gerenciam negócio pela plataforma | Agendamento + Avaliações | - | 📋 Planejado |
| **Pagamento Online (Stripe)** | Pagamento via cartão na plataforma | Reduzir no-shows, revenue para BookEasy (% comissão) | Agendamento V1 | PCI compliance, integração Stripe complexa | 📋 Planejado |
| **Cancelamento e Reagendamento** | Clientes podem cancelar/reagendar com X horas de antecedência | Flexibilidade, reduzir atrito | Agendamento V1 | Política de cancelamento controversa | 📋 Planejado |
| **Notificações SMS** | SMS além de email (maior engajamento) | Reduzir no-shows de ~30% para ~10% | Notificações Email | Custo por SMS (~$0.01/SMS) | 📋 Planejado |
| **Mobile Responsivo** | PWA otimizado para mobile | 70% dos acessos são mobile | - | Design responsivo em calendário complexo | 📋 Planejado |

**Outcome Esperado:** 50 prestadores ativos, 500 agendamentos/mês, <15% no-show rate.

---

#### 🔵 LATER (5-6 meses - Junho a Julho 2026)

**Tema:** Scale - Crescimento e Eficiência

| Iniciativa | Descrição | Objetivo/Valor | Dependências | Riscos | Status |
|------------|-----------|----------------|--------------|--------|--------|
| **Busca Avançada** | Filtros (preço, avaliação, distância, disponibilidade) | Melhorar descoberta, conversão | Busca Básica + Avaliações | Performance com muitos prestadores | 💡 Ideia |
| **Múltiplos Serviços** | Prestadores oferecem menu (corte, barba, hidratação) | Aumentar ticket médio | Calendário | Complexidade de duração variável | 💡 Ideia |
| **App Mobile Nativo (iOS/Android)** | App nativo com push notifications | Retenção, notificações mais confiáveis | PWA funcionando bem | Custo de desenvolvimento alto | 💡 Ideia |
| **Programa de Fidelidade** | Cliente ganha pontos a cada agendamento | Retenção de clientes | Pagamento Online | Complexidade de gamification | 💡 Ideia |
| **Expansão para Clínicas** | Vertical adicional além de salões | Diversificar receita | MVP validado | Requer customizações (ex: agendamento por procedimento) | 💡 Ideia |
| **Admin Dashboard** | Ferramentas internas para CS, fraude, analytics | Escalar operação | Dashboard Prestador | - | 💡 Ideia |

**Outcome Esperado:** 200 prestadores, 2k agendamentos/mês, $10k MRR.

---

### 3. Dependências Críticas

```
Auth/Onboarding
    ↓
Perfil Prestador
    ↓
Calendário de Disponibilidade
    ↓                           ↓
Busca Básica              Agendamento (V1)
    ↓                           ↓
Busca Avançada          Notificações → Pagamento → Avaliações
                              ↓              ↓
                         Cancelamento   Dashboard Prestador
```

**Bloqueadores Críticos:**
- Agendamento V1 bloqueia quase tudo (núcleo do produto)
- Pagamento Online bloqueia programa de fidelidade
- Avaliações necessárias antes de busca avançada ser útil

---

### 4. Riscos e Mitigações

| Risco | Probabilidade | Impacto | Mitigação |
|-------|---------------|---------|-----------|
| **Integração Stripe mais complexa que esperado** | Média | Alto | Começar integração cedo (sprint 1 de Next), usar Stripe Checkout (não custom) |
| **No-shows altos (>30%) matam prestadores** | Alta | Crítico | Implementar SMS + email + política de cancelamento + futuramente depósito |
| **Prestadores não adotam (manual funciona)** | Média | Crítico | Onboarding manual, suporte 1:1, incentivos early adopter |
| **Performance ruim com muitos prestadores** | Baixa | Médio | Pagination, indexação DB, cache (só otimizar se for problema real) |
| **Clientes não confiam (novo)** | Média | Alto | Social proof (avaliações), design profissional, SEO |
| **Churn de prestadores (comissão alta)** | Média | Alto | Começar com comissão baixa (5-10%), aumentar valor antes de aumentar % |

---

### 5. Fora de Escopo (Roadmap)

Explicitamente **não faremos** nos próximos 6 meses:

- ❌ App nativo (PWA é suficiente para MVP)
- ❌ Múltiplas verticais (foco em salões apenas)
- ❌ Internacionalização
- ❌ White-label para empresas
- ❌ Integração com Google/Apple Calendar
- ❌ Sistema de chat in-app
- ❌ Marketplace de produtos (apenas serviços)
- ❌ Programa de afiliados

---

---

## PARTE 2: DEFINITION OF DONE (DoD)

### 6. Objetivo da DoD

**Por que existe:**
- Garantir qualidade mínima em entregas (MVP não significa buggy)
- Evitar dívida técnica que trava crescimento
- Alinhar expectativas entre PM, Eng e QA
- Reduzir retrabalho e hotfixes

**Como será usada:**
- Checklist em cada PR antes de merge
- Critério de aceitação em cada task/story
- Gate para mover card para "Done" no board
- Base para retrospectivas (se violamos DoD, por quê?)

---

### 7. DoD Global (Aplicável a Todas as Entregas)

**Requisitos e Funcionalidade:**
- [ ] Requisitos do PRD/story atendidos
- [ ] Critérios de aceitação validados (manual ou auto)
- [ ] Happy path funciona end-to-end
- [ ] Edge cases principais cobertos (ex: campos vazios, dados inválidos)

**Código:**
- [ ] Code review aprovado por pelo menos 1 engenheiro
- [ ] Sem `console.log` ou código de debug
- [ ] Sem `TODO` críticos (marcar como tech debt se não for agora)
- [ ] Naming claro (funções, variáveis, componentes)

**Testes:**
- [ ] Testes unitários para lógica crítica (ex: validações, cálculos)
- [ ] Pelo menos 1 teste de integração para fluxo principal
- [ ] Testado manualmente em dev e staging
- [ ] Smoke test: feature não quebra fluxos existentes

**UI/UX (se aplicável):**
- [ ] Design aprovado por designer (Figma vs implementado)
- [ ] Responsivo (mobile e desktop)
- [ ] Estados de loading, erro e vazio implementados
- [ ] Acessibilidade básica (navegação por teclado, alt text em imagens)

**Performance:**
- [ ] Página carrega em < 3s (4G)
- [ ] Sem loops infinitos ou memory leaks óbvios
- [ ] Imagens otimizadas (WebP, lazy loading)

**Segurança:**
- [ ] Inputs são validados e sanitizados
- [ ] Sem secrets commitados no código
- [ ] Autenticação/autorização nos endpoints aplicáveis

**Deploy e Infra:**
- [ ] CI passa (lint, type-check, tests)
- [ ] Deploy em staging bem-sucedido
- [ ] Testado em staging antes de prod
- [ ] Rollback plan conhecido (Vercel permite rollback em 1-click)

**Documentação:**
- [ ] README atualizado se houver nova env var ou setup
- [ ] Comentários em código complexo (ex: regex, algoritmos)
- [ ] PR description explica o "porquê" (não apenas o "o que")

**Aprovações:**
- [ ] PM aprovou (testou em staging)
- [ ] QA spot-check (se feature crítica)
- [ ] Designer aprovou (se houver UI)

---

### 8. DoDs Específicos por Tipo de Entrega

#### 📌 Feature de Produto (Nova Funcionalidade)

Além da DoD Global:

- [ ] Onboarding/empty state implementado (se for primeira vez do usuário)
- [ ] Analytics/tracking instrumentado (eventos de uso)
- [ ] Feature flag criada (se lançamento gradual for necessário)
- [ ] Documentação de usuário atualizada (se houver help center)

**Exemplo:** Feature "Agendamento V1"
- [ ] Cliente consegue agendar sem erros
- [ ] Prestador recebe notificação
- [ ] Agendamento aparece no dashboard
- [ ] Evento `booking_created` logado no Mixpanel
- [ ] Testado com múltiplos horários e prestadores

---

#### 📌 Bug / Correção

Além da DoD Global:

- [ ] Causa raiz identificada e documentada (no PR ou ticket)
- [ ] Teste de regressão adicionado (para prevenir bug voltar)
- [ ] Verificado que fix não quebrou nada adjacente
- [ ] Se bug atingiu produção: post-mortem leve (o que falhou na DoD?)

**Exemplo:** Bug "Horários duplicados no calendário"
- [ ] Root cause: race condition no update de disponibilidade
- [ ] Fix: adicionar lock otimista (version field)
- [ ] Teste: simular updates concorrentes
- [ ] Validado que horários não duplicam mais

---

#### 📌 Débito Técnico / Refactoring

Além da DoD Global:

- [ ] Justificativa clara (por que fazer agora?)
- [ ] Métricas "antes vs depois" (se aplicável: performance, bundle size)
- [ ] Sem regressão funcional (todos testes passam)
- [ ] Se mudança grande: feito em etapas pequenas (evitar mega-PR)

**Exemplo:** Refactoring "Migrar de Context API para Zustand (state management)"
- [ ] Testes passam antes e depois
- [ ] Componentes principais migrados
- [ ] Bundle size não aumentou significativamente
- [ ] Documentação de padrão atualizada

---

#### 📌 Spike / Pesquisa Técnica

Critérios diferentes (não há código):

- [ ] Documento de findings escrito (Notion/Google Docs)
- [ ] Recomendação clara (fazer X, não fazer Y)
- [ ] Pros/cons de alternativas avaliadas
- [ ] Esforço estimado se formos implementar
- [ ] Apresentado para o time (async ou sync)

**Exemplo:** Spike "Avaliar Stripe vs Mercado Pago para pagamentos"
- [ ] Comparação de fees, API, documentação
- [ ] Teste de integração (sandboxes de ambos)
- [ ] Recomendação: Stripe (melhor API, docs)
- [ ] Estimativa: 2 semanas para integração

---

### 9. Responsáveis por Validação

| Critério | Quem Valida | Quando |
|----------|-------------|--------|
| **Código funciona** | Engenheiro (PR reviewer) | Antes de merge |
| **Requisitos atendidos** | PM | Em staging, antes de prod |
| **Design implementado** | Designer | Em staging (spot check) |
| **Qualidade técnica** | Tech Lead | Code review |
| **Sem bugs óbvios** | QA (ou PM) | Smoke test em staging |
| **Performance aceitável** | Engenheiro | Lighthouse CI em PR |
| **Acessibilidade básica** | Designer ou Eng | Checklist em PR |

**Fluxo de Aprovação:**
1. Engenheiro abre PR → CI roda
2. Code review (outro engenheiro) → aprova ou pede mudanças
3. Merge para `main` → auto-deploy para staging
4. PM testa em staging → aprova ou rejeita
5. Merge para `production` → deploy para prod
6. Smoke test em prod → alertas se algo quebrou

---

### 10. Métricas de Qualidade (Como Medir se DoD Funciona)

**Indicadores de Sucesso:**
- **Deploy frequency:** 3-5x por semana (idealmente diário)
- **Lead time:** < 3 dias (de PR aberto até produção)
- **Change fail rate:** < 15% (deploys que precisam rollback ou hotfix)
- **MTTR (Mean Time to Repair):** < 2 horas (tempo para corrigir bug em prod)
- **Code review time:** < 4 horas (para não bloquear)
- **Test coverage:** > 70% (crítico > 90%)

**Sinais de Alerta (DoD sendo ignorada):**
- ⚠️ Hotfixes frequentes (>1 por semana) → DoD de testes falhou
- ⚠️ Bugs recorrentes → DoD de testes de regressão falhou
- ⚠️ PRs enormes (>500 linhas) → DoD de small batches falhou
- ⚠️ Tech debt crescente → DoD de refactoring falhou
- ⚠️ Surpresas em prod → DoD de staging testing falhou

**Ação Corretiva:**
- Se métricas pioram, revisitar DoD em retrospectiva
- Adicionar checks faltantes
- Automatizar quando possível (CI/CD)

---

### 11. Exceções e Casos Especiais

**Quando DoD pode ser relaxada (com aprovação explícita):**

1. **Hotfix Crítico (Produção Quebrada):**
   - Pode pular: testes completos, staging prolongado
   - Não pode pular: code review, rollback plan
   - Compensação: criar tech debt ticket, adicionar teste depois

2. **Prova de Conceito (Demo para Investidor):**
   - Pode pular: testes, performance, edge cases
   - Não pode pular: funcionalidade principal
   - Compensação: reescrever antes de produção real

3. **Feature Flag (Lançamento Gradual):**
   - Pode pular: documentação de usuário (ainda não é público)
   - Não pode pular: testes, code review
   - Compensação: completar antes de feature flag para 100%

**Processo de Exceção:**
1. PM ou Tech Lead decide que exceção é necessária
2. Documenta no PR: "Exceção DoD: [motivo]"
3. Cria ticket de follow-up (se houver dívida técnica)
4. Discute em retrospectiva: foi necessário? Como evitar?

---

### 12. Lacunas e Perguntas em Aberto

**Decisões Pendentes sobre DoD:**

- ⚠️ **Cobertura de testes exata:** Qual % mínimo? (proposta: 70% global, 90% crítico)
- ⚠️ **Responsável por QA:** PM faz ou contratamos QA? (início: PM, depois: contratar)
- ⚠️ **Testes E2E:** Quando adicionar Playwright? (Later, quando houver budget)
- ⚠️ **Acessibilidade rigorosa:** WCAG AA obrigatório desde MVP? (início: básico, depois: AA)
- ⚠️ **Performance budgets:** Lighthouse score mínimo? (proposta: >80)
- ⚠️ **Security review:** Quando obrigatório? (proposta: antes de pagamentos)

**Decisões Pendentes sobre Roadmap:**

- ⚠️ **Comissão exata:** 5%? 10%? 15%? (testar com early adopters)
- ⚠️ **Política de cancelamento:** Até quando cliente pode cancelar grátis? (proposta: 24h antes)
- ⚠️ **Suporte a múltiplos idiomas:** PT-BR apenas ou EN também? (início: PT-BR, depois: EN)
- ⚠️ **Multi-tenancy:** Prestador pode ter múltiplas localizações? (Later)
- ⚠️ **Pico de carga:** Quantos agendamentos simultâneos? (validar em Later com load testing)

---

**Próxima Revisão:** 1 mês (final de fevereiro 2026) - ajustar Roadmap e DoD baseado em progresso real.
```

---

### Exemplo 2: Sistema de E-learning Corporativo (Enterprise B2B)

```markdown
# Roadmap + DoD - LearnHub Enterprise

## PARTE 1: ROADMAP DE PRODUTO

### 1. Visão Geral

**Objetivo:** Modernizar plataforma de treinamento corporativo para 500 empresas e 50k usuários finais.

**Horizonte Temporal:** Anual (2026) com revisões trimestrais.

**Premissas:**
- Time: 15 engenheiros (3 squads), 2 PMs, 3 designers, 2 QAs
- Migração de plataforma legada (rails monolith → microservices)
- Contratos existentes: renovação depende de novas features
- Compliance: SOC2, GDPR, WCAG AA

**Critério de Priorização:** MoSCoW + Impacto em Churn

---

### 2. Roadmap Detalhado

#### Q1 2026 (Janeiro - Março): Fundação

**Must-Have:**
- Migração de autenticação para SSO (SAML/OIDC)
- API pública v1 (para integrações de clientes)
- Dashboard de admin renovado
- Sistema de relatórios básicos

**Should-Have:**
- Mobile app (iOS/Android) MVP

**Won't-Have:**
- Gamificação, AI-powered recommendations

---

#### Q2 2026 (Abril - Junho): Escala

**Must-Have:**
- Multi-tenancy completo (isolamento de dados)
- Suporte a 100k usuários simultâneos (load testing)
- Advanced analytics (completion rates, time spent)

**Should-Have:**
- Integração com Slack/Teams
- White-labeling (custom branding por cliente)

---

#### Q3 2026 (Julho - Setembro): Diferenciação

**Must-Have:**
- AI-powered content recommendations
- Acessibilidade WCAG 2.1 AA completa

**Should-Have:**
- Live streaming de aulas
- Certificações e badges

---

#### Q4 2026 (Outubro - Dezembro): Otimização

**Should-Have:**
- Advanced reporting (custom dashboards)
- Mobile offline mode
- Marketplace de conteúdo

---

### 3. Riscos

- **Migração legacy:** Pode atrasar Q1 em 4-6 semanas
- **SOC2 audit:** Precisa passar em Q2 (senão perdemos contratos)
- **Load de 100k users:** Requer rewrite de partes críticas

---

## PARTE 2: DEFINITION OF DONE

### DoD Global (Enterprise)

**Segurança e Compliance:**
- [ ] Security review aprovado
- [ ] Sem vulnerabilidades critical/high (Snyk scan)
- [ ] GDPR compliant (data export, deletion)
- [ ] Audit log para dados sensíveis

**Qualidade:**
- [ ] Cobertura de testes > 85%
- [ ] Testes E2E para fluxos críticos (Playwright)
- [ ] Load tested (se aplicável)
- [ ] No breaking changes em API pública

**Documentação:**
- [ ] API docs atualizadas (OpenAPI)
- [ ] Internal docs (ADRs para decisões grandes)
- [ ] Customer-facing docs (help center)
- [ ] Migration guide (se breaking change)

**Operação:**
- [ ] Monitoring/alertas configurados
- [ ] Runbook para incidentes
- [ ] Rollback testado
- [ ] Feature flag (se lançamento gradual)

**Aprovações:**
- [ ] PM, Tech Lead, QA, Security, Design (conforme aplicável)
- [ ] Beta test com 3 clientes piloto (features grandes)

---

**Roadmap revisado:** Trimestralmente.  
**DoD revisada:** Semestralmente ou após incidentes.
```

---

**Criado para garantir que planejamento seja orientado a valor e entregas tenham qualidade consistente.**
