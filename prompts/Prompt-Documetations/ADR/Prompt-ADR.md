# 🏗️ Template de Geração de ADR (Architecture Decision Records) - Cursor IDE

Template de prompt baseado em **análise evolutiva de documentação** para gerar ADRs (Architecture Decision Records) claros, rastreáveis e incrementais. Ideal para documentar decisões arquiteturais importantes usando briefing, PRD e outros artefatos como fonte de contexto viva, sem criar burocracia desnecessária.

---

## 📝 Template do Prompt

Copie e personalize o template abaixo. Este prompt utiliza **contexto evolutivo** — pode receber múltiplos documentos ao longo do tempo.

```markdown
## Role (Identidade da IA)

Você é um **Arquiteto de Software Sênior** com forte experiência em:
- Arquitetura de sistemas modernos e evolutivos
- Clean Architecture, DDD e padrões arquiteturais
- Tomada de decisão técnica orientada a trade-offs
- Documentação leve e pragmática (ADR-first approach)
- Rastreabilidade de decisões arquiteturais

## Objetivo

Gerar **Architecture Decision Records (ADRs)** claros, rastreáveis e incrementais, baseados em documentação fornecida (briefing, PRD, código, RFCs), criando novos ADRs **somente quando necessário** e mantendo consistência histórica.

## Contexto

ADRs são registros de decisões arquiteturais importantes que:
- São difíceis ou custosas de reverter
- Afetam múltiplos módulos, times ou o futuro do sistema
- Geram dúvidas recorrentes ("por que fizemos assim?")

Seu foco é **registrar decisões**, não ensinar conceitos nem criar documentação excessiva.

## Entrada (Contexto Dinâmico)

Você receberá, ao longo do tempo, um ou mais dos seguintes artefatos:

- 📄 **Briefing do projeto**
- 📘 **PRD (Product Requirements Document)**
- 🏗️ **Diagramas de arquitetura**
- 📋 **RFCs (Request for Comments)**
- 💻 **Código-fonte existente**
- 📖 **README e documentação técnica**
- 🐛 **Issues e Pull Requests**
- 📊 **Postmortems e retrospectivas**

Considere **todos os arquivos como fontes complementares de contexto**, priorizando:
1. Decisões explícitas já tomadas
2. Restrições técnicas e de negócio
3. Problemas recorrentes ou difíceis de reverter

## Tarefa Principal

1. **Analisar os documentos fornecidos**
2. **Identificar decisões arquiteturais relevantes** que:
   - Sejam difíceis de reverter
   - Afetem múltiplos módulos, times ou o futuro do sistema
   - Possam gerar dúvidas futuras
3. Para cada decisão identificada:
   - Verificar se **já existe um ADR**
   - Criar um **novo ADR apenas se necessário**
4. Manter **consistência histórica e incremental**

## Estrutura do ADR

Cada ADR deve seguir **exatamente** esta estrutura:

```
# [Título claro e objetivo da decisão]

## Status
[Proposto | Aceito | Rejeitado | Substituído | Depreciado]

## Contexto
Descreva o problema que levou à decisão:
- Restrições técnicas ou de negócio
- Pressões de prazo, custo ou escala
- Informações relevantes do briefing/PRD/outros arquivos
- Alternativas consideradas (se aplicável)

## Decisão
Descreva objetivamente o que foi decidido, sem ambiguidade.

## Consequências
Liste os impactos conhecidos:
- Benefícios esperados
- Trade-offs e custos aceitos
- Riscos técnicos ou organizacionais
- Próximos passos (se aplicável)
```

## Convenção de Arquivos

- **Nome:** `NNNN-descricao-curta-da-decisao.md`
- **Numeração:** Sequencial (0001, 0002, 0003...)
- **Diretório padrão:** `/docs/adr/` ou `/docs/architecture/decisions/`

## Diretrizes

- **Foco em decisões significativas**, não trivialidades
- Use linguagem técnica, mas acessível
- Seja conciso e factual
- Registre **POR QUE**, não apenas **O QUE**
- Mencione alternativas rejeitadas quando relevante
- Mantenha neutralidade (sem opiniões pessoais)

## Formato da Resposta

1. **Liste ADRs identificados** com título e breve justificativa
2. **Gere o conteúdo completo** de cada ADR em Markdown
3. **Indique o número sequencial** apropriado
4. **Sem emojis** nos ADRs finais

## Restrições

- ❌ Não criar ADRs para decisões triviais ou facilmente reversíveis
- ❌ Não repetir ADRs já existentes
- ❌ Não escrever textos genéricos ou acadêmicos
- ❌ Não incluir código completo (apenas snippets quando necessário)
- ✅ Ser conciso, direto e factual
- ✅ Focar em decisões que impactam o longo prazo
- ✅ Manter consistência com ADRs anteriores
```

---

## 🚀 Como Usar

### 1️⃣ Fluxo Recomendado (Evolutivo)

Este prompt funciona melhor em um **workflow evolutivo**:

```
Fase 1: Briefing + PRD → Gera ADRs iniciais (decisões arquiteturais de alto nível)
           ↓
Fase 2: RFCs técnicos → Gera ADRs de implementação
           ↓
Fase 3: Código + Issues → Gera ADRs de refinamento
           ↓
Fase 4: Postmortems → Gera ADRs de ajuste/substituição
```

**Vantagens da Abordagem Evolutiva:**
- ADRs crescem organicamente com o projeto
- Não gera documentação prematura
- Mantém rastreabilidade temporal
- Facilita onboarding de novos membros

### 2️⃣ Onde Usar

- **Cursor IDE** → Cole como system prompt + forneça documentos
- **VS Code com extensões de IA** → Use como custom instructions
- **ChatGPT/Claude** → Cole prompt + documentação na conversa
- **APIs** → System message + documentos como contexto
- **CI/CD** → Gerar ADRs automaticamente em pipelines

### 3️⃣ Exemplo Prático Completo

**Entrada (PRD Resumido):**

```markdown
# PRD - Sistema de Pagamentos

**Requisitos:**
- Processamento de pagamentos em tempo real
- Suporte a múltiplos gateways (Stripe, PayPal, PagSeguro)
- Retry automático em falhas
- Auditoria completa de transações
- Webhook para notificações assíncronas
```

**Saída Esperada (ADRs):**

```
ADRs Identificados:
1. 0001-escolha-de-gateway-de-pagamento-abstrato.md
2. 0002-estrategia-de-retry-exponencial.md
3. 0003-armazenamento-de-eventos-para-auditoria.md
```

A IA gerará cada ADR completo documentando as decisões arquiteturais.

---

## 💡 Por Que Este Prompt Funciona

### ✅ 1. Contexto Evolutivo e Incremental
- Não exige toda documentação de uma vez
- Permite adicionar contexto gradualmente
- Mantém histórico de decisões
- Facilita rastreamento de mudanças

### ✅ 2. Foco em Decisões Significativas
- Evita ADRs triviais ("usaremos Git")
- Prioriza decisões difíceis de reverter
- Documenta trade-offs importantes
- Registra alternativas consideradas

### ✅ 3. Estrutura Leve e Prática
- Template simples (4 seções principais)
- Fácil de escrever e manter
- Sem burocracia desnecessária
- Formato reconhecido pela indústria

### ✅ 4. Rastreabilidade e Governança
- Numeração sequencial facilita referências
- Status claro de cada decisão
- Histórico imutável (não altera ADRs antigos)
- Facilita compliance e auditorias

### ✅ 5. Integração com Workflow Existente
Funciona com documentos já criados:
- Briefing → Decisões estratégicas
- PRD → Decisões de produto/arquitetura
- RFCs → Decisões técnicas detalhadas
- Código → Decisões de implementação

---

## ⚠️ Observações Importantes

### O que este prompt faz:
- ✅ Identifica decisões arquiteturais em documentos
- ✅ Gera ADRs estruturados e consistentes
- ✅ Mantém histórico incremental de decisões
- ✅ Documenta contexto, decisão e consequências
- ✅ Prioriza decisões significativas

### O que este prompt NÃO faz:
- ❌ Não toma decisões arquiteturais pelo time
- ❌ Não documenta implementação detalhada
- ❌ Não substitui RFCs ou design docs
- ❌ Não gera ADRs para decisões triviais
- ❌ Não altera ADRs históricos (cria novos)

### Quando usar este prompt:
- **Use quando:**
  - Precisa documentar decisões arquiteturais importantes
  - Quer rastreabilidade de escolhas técnicas
  - Facilitar onboarding de novos membros
  - Atender requisitos de governança/compliance
  - Registrar trade-offs e alternativas

- **Não use quando:**
  - Decisão é trivial ou padrão da indústria
  - Mudança é facilmente reversível
  - Não há impacto significativo no sistema
  - Documentação detalhada já existe em outro formato

---

## 🔄 Personalização Avançada

### Para Diferentes Contextos:

**Startup / MVP:**
```markdown
## Critérios para ADR

Priorize decisões sobre:
- Escolha de stack tecnológica principal
- Arquitetura de deployment (monolito vs microserviços)
- Estratégias de escalabilidade
- Escolhas que impactam time-to-market
```

**Enterprise / Sistema Legado:**
```markdown
## Critérios para ADR

Priorize decisões sobre:
- Estratégias de migração gradual
- Integração com sistemas legados
- Compliance e segurança
- Governança de dados
```

**Microserviços / Distribuído:**
```markdown
## Critérios para ADR

Priorize decisões sobre:
- Escolha de padrões de comunicação (REST, gRPC, eventos)
- Estratégias de consistência eventual
- Service mesh e observabilidade
- Contratos entre serviços
```

**Produto com IA/ML:**
```markdown
## Critérios para ADR

Priorize decisões sobre:
- Escolha de modelos e frameworks
- Pipeline de treinamento e deployment
- Versionamento de modelos
- Monitoramento de drift
```

---

## 💭 Filosofia

> **"ADRs não são burocracia — são memória organizacional que previne retrabalho e acelera decisões futuras."**

Este prompt garante:
- **Transparência** nas decisões arquiteturais
- **Rastreabilidade** de trade-offs ao longo do tempo
- **Conhecimento** preservado mesmo com rotatividade de time
- **Velocidade** em decisões similares futuras

---

## 🔄 Próximos Níveis (Evolução)

1. **ADR com impacto estimado** - Custo, tempo e risco de cada decisão
2. **Geração de diagramas** - Visualizações automáticas de decisões
3. **ADR templates por domínio** - Frontend, Backend, Infra, Data
4. **Validação automática** - Checklist de completude
5. **Relacionamento entre ADRs** - Grafo de dependências
6. **ADR review automation** - Sugestões de review em PRs

---

## 🧠 Extensões Possíveis

### Variações do Template:

- **ADR Curto** - Formato reduzido para decisões menores
- **ADR Técnico** - Mais detalhes de implementação
- **ADR de Segurança** - Foco em threat model
- **ADR de Performance** - Benchmarks e métricas

### Integrações:

- **GitHub** - ADRs como parte de PRs
- **Confluence/Notion** - Sincronização de documentação
- **Miro/Lucidchart** - Diagramas arquiteturais linkados
- **Jira** - Rastreamento de implementação de ADRs

### Automações:

```yaml
# Exemplo de workflow CI/CD
name: Generate ADRs
on:
  push:
    paths:
      - 'docs/prd/**'
      - 'docs/rfcs/**'
  workflow_dispatch:

jobs:
  generate-adrs:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Analyze docs and generate ADRs
        run: |
          # LLM analisa novos docs e sugere ADRs
          # Cria PR com ADRs propostos
          # Time revisa e aprova
```

---

## 💡 Dicas Práticas

### Para Melhor Qualidade dos ADRs:

1. **Documente no momento certo** - Quando decisão é tomada, não depois
2. **Seja específico** - "Usamos PostgreSQL" é melhor que "usamos SQL"
3. **Explique alternativas** - Mostre o que foi considerado e rejeitado
4. **Quantifique trade-offs** - "3x mais lento, mas 10x mais simples"
5. **Inclua data** - Contexto temporal é importante

### Checklist de Qualidade do ADR:

- [ ] Título é claro e auto-explicativo?
- [ ] Contexto explica o problema real?
- [ ] Decisão é objetiva e sem ambiguidade?
- [ ] Consequências incluem benefícios E custos?
- [ ] Alternativas foram mencionadas?
- [ ] Status está correto?
- [ ] Texto é conciso (evita verbosidade)?
- [ ] Referências a outros ADRs estão claras?

### Quando Criar um Novo ADR:

✅ **Crie quando:**
- Decisão afeta múltiplos times
- Reverter seria custoso (> 1 sprint)
- Gera dúvidas recorrentes
- Envolve trade-offs significativos
- Impacta arquitetura de longo prazo

❌ **Não crie para:**
- Decisões óbvias ("usaremos Git")
- Escolhas facilmente reversíveis
- Detalhes de implementação local
- Padrões já documentados
- Decisões triviais de time

---

## 🔗 Integração com Outros Templates

Este template funciona melhor em conjunto:

```
📋 Briefing → Define visão e restrições de negócio
    ↓
📄 PRD → Define requisitos funcionais e não-funcionais
    ↓
🏗️ ADR (este) → Documenta decisões arquiteturais
    ↓
🎯 RFCs → Detalha implementação técnica
    ↓
💻 Código → Implementa decisões documentadas
```

**Fluxo completo:**
1. Crie briefing e PRD (templates anteriores)
2. Identifique decisões arquiteturais significativas
3. Gere ADRs para cada decisão (este template)
4. Referencie ADRs em RFCs e código
5. Atualize/substitua ADRs quando necessário

---

## 📚 Exemplos de ADRs Reais

### Exemplo 1: Escolha de Banco de Dados

```markdown
# 0001 - Uso de PostgreSQL como Banco Principal

## Status
Aceito

## Contexto
Precisamos de um banco de dados para armazenar dados transacionais
do sistema de e-commerce. Requisitos principais:
- Transações ACID
- Suporte a JSON para dados flexíveis
- Comunidade ativa e ferramentas maduras

Alternativas consideradas:
- MySQL: Menos recursos para JSON
- MongoDB: ACID limitado em versões antigas
- DynamoDB: Vendor lock-in com AWS

## Decisão
Usaremos PostgreSQL 15+ como banco de dados principal.

## Consequências
**Positivo:**
- ACID completo garante consistência
- JSONB permite flexibilidade quando necessário
- Ferramentas maduras (pg_dump, repmgr, patroni)
- Time já tem experiência

**Negativo:**
- Escala vertical tem limites (sharding é complexo)
- Custo de infra pode ser maior que DynamoDB em alta escala
- Requer gerenciamento de alta disponibilidade

**Próximos passos:**
- Configurar replicação read-only
- Implementar pooling com PgBouncer
- Definir estratégia de backup
```

### Exemplo 2: Arquitetura de Microserviços

```markdown
# 0002 - Comunicação Assíncrona via Event Bus

## Status
Aceito

## Contexto
Sistema cresceu e acoplamento entre serviços está causando:
- Cascading failures
- Deploy bloqueado por dependências
- Timeout em chamadas síncronas

Requisitos:
- Desacoplamento entre serviços
- Auditoria de eventos
- Eventual consistency aceitável

Alternativas:
- REST síncrono: Mantém problemas atuais
- gRPC: Ainda acoplado
- Message Queue simples: Sem replay de eventos

## Decisão
Implementar event bus com Apache Kafka para comunicação
assíncrona entre serviços.

## Consequências
**Positivo:**
- Desacoplamento temporal e lógico
- Replay de eventos para debug/auditoria
- Escalabilidade horizontal
- Tolerância a falhas melhorada

**Negativo:**
- Eventual consistency requer mudança de mindset
- Complexidade operacional (Kafka cluster)
- Debugging mais difícil (tracing distribuído necessário)
- Custo de infra aumenta

**Próximos passos:**
- Implementar tracing distribuído (Jaeger)
- Definir schema registry (Avro)
- Criar runbooks para Kafka
```

---

**Criado para documentar decisões arquiteturais com clareza, rastreabilidade e praticidade.**
