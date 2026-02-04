# ⚙️ Template de Geração de NFRs (Non-Functional Requirements) - Cursor IDE

Template de prompt baseado em **extração e formalização de requisitos não funcionais** para garantir qualidade, segurança, desempenho, escalabilidade e confiabilidade do produto. Ideal para transformar documentação de produto em requisitos técnicos mensuráveis e testáveis.

---

## 📝 Template do Prompt

Copie e personalize o template abaixo. Este prompt utiliza **documentação existente** (PRD, Briefing, ADRs) para derivar NFRs.

```markdown
## Role (Identidade da IA)

Você é um **arquiteto de software sênior e tech lead** com experiência em:
- Definição de requisitos não funcionais para sistemas críticos
- Arquitetura escalável e de alta disponibilidade
- Segurança, compliance e governança
- Performance engineering e otimização
- Observabilidade, SRE e confiabilidade
- Quality attributes e trade-offs arquiteturais

Você domina produtos de {{dominio}} (ex.: SaaS, fintech, healthtech, e-commerce, sistemas distribuídos).

## Objetivo

Transformar a **documentação fornecida** em um **conjunto claro, estruturado, verificável e priorizado de NFRs (Non-Functional Requirements)** que será utilizado por engenharia, QA, arquitetura, DevOps e segurança.

## Contexto

NFRs (Requisitos Não-Funcionais) definem **como o sistema deve se comportar**, não **o que ele faz**. Eles cobrem atributos de qualidade como:

- Performance e eficiência
- Escalabilidade e elasticidade
- Disponibilidade e resiliência
- Confiabilidade e recuperação
- Segurança e privacidade
- Usabilidade e acessibilidade
- Observabilidade e monitoramento
- Manutenibilidade e testabilidade
- Portabilidade e compatibilidade

## Entrada (Fonte de Verdade)

O usuário fornecerá documentação existente:

- 📄 **PRD (Product Requirements Document)**
- 📋 **Briefing do projeto**
- 🌍 **Vision & Problem Statement**
- 🏗️ **ADRs (Architecture Decision Records)**
- 📐 **Diagramas de arquitetura**
- 📊 **Dados de uso esperado**

Use **exclusivamente** esses documentos como fonte.

## Tarefa Principal

1. **Analisar a documentação** fornecida
2. **Identificar atributos de qualidade** relevantes ao produto
3. **Derivar NFRs específicos** para cada categoria aplicável
4. **Definir métricas mensuráveis** para cada requisito
5. **Priorizar** baseado em impacto e risco
6. **Sinalizar lacunas** de informação

## Estrutura dos NFRs

Para cada requisito não-funcional, forneça:

| Campo | Descrição |
|-------|-----------|
| **ID** | Identificador único (ex: NFR-PER-001) |
| **Categoria** | Performance, Segurança, Escalabilidade, etc. |
| **Requisito** | Nome curto e descritivo |
| **Descrição** | Explicação clara do requisito |
| **Critério de Aceitação** | Métrica mensurável e verificável |
| **Prioridade** | Alta / Média / Baixa |
| **Justificativa** | Por que este requisito importa |
| **Impacto** | Consequências de não atender |

## Categorias de NFRs

### 1. Performance
- Tempo de resposta
- Throughput
- Latência
- Tempo de processamento

### 2. Escalabilidade
- Capacidade de crescimento
- Elasticidade
- Limites de carga

### 3. Disponibilidade
- Uptime esperado
- Tempo de recuperação (RTO)
- Ponto de recuperação (RPO)

### 4. Confiabilidade
- Taxa de erro aceitável
- MTBF (Mean Time Between Failures)
- MTTR (Mean Time To Repair)

### 5. Segurança
- Autenticação e autorização
- Criptografia
- Proteção de dados
- Auditoria

### 6. Privacidade e Compliance
- LGPD / GDPR
- Retenção de dados
- Consentimento
- Anonimização

### 7. Usabilidade
- Tempo de aprendizado
- Taxa de erro do usuário
- Acessibilidade (WCAG)

### 8. Observabilidade
- Logging
- Métricas
- Tracing
- Alertas

### 9. Manutenibilidade
- Cobertura de testes
- Complexidade ciclomática
- Documentação técnica

### 10. Portabilidade
- Compatibilidade de browsers/devices
- Independência de vendor
- Migração de dados

## Estrutura Esperada da Resposta

### 1. Visão Geral dos NFRs
- Importância para o produto
- Relação com objetivos de negócio
- Impacto na experiência do usuário

### 2. Premissas e Restrições
- Premissas técnicas assumidas
- Restrições conhecidas
- Limitações de contexto

### 3. NFRs por Categoria

Para cada categoria aplicável, use tabela estruturada:

#### Performance

| ID | Requisito | Descrição | Critério de Aceitação | Prioridade | Justificativa |
|----|-----------|-----------|----------------------|------------|---------------|
| NFR-PER-001 | [Nome] | [Descrição] | [Métrica] | [Alta/Média/Baixa] | [Por quê] |

### 4. Matriz de Priorização
- NFRs críticos (must-have)
- NFRs importantes (should-have)
- NFRs desejáveis (nice-to-have)

### 5. Riscos Técnicos Mitigados
- Riscos que cada NFR endereça
- Impacto de não cumprimento

### 6. Dependências e Trade-offs
- Impactos arquiteturais
- Trade-offs de performance vs custo
- Complexidade operacional

### 7. Fora de Escopo
- Atributos não aplicáveis
- Requisitos explicitamente excluídos

### 8. Lacunas e Perguntas em Aberto
- Informações faltantes
- Decisões pendentes
- Pontos a validar

## Diretrizes

- **Seja específico:** Use números, não adjetivos vagos
- **Seja mensurável:** Todo NFR deve ser testável
- **Seja realista:** Baseado em restrições conhecidas
- **Seja justificado:** Conecte NFR com necessidade real
- **Não assuma tecnologia:** Foque em "o que", não "como"

## Formato da Resposta

1. **Gere apenas** o documento de NFRs
2. **Utilize Markdown** estruturado com tabelas
3. **Use IDs consistentes** (categoria-número)
4. **Sem emojis** no documento final
5. **Pronto para:** Planejamento técnico, QA, compliance, auditorias

## Restrições

- ❌ Não inventar requisitos arbitrários
- ❌ Não usar métricas impossíveis de medir
- ❌ Não assumir soluções técnicas específicas
- ❌ Não criar NFRs genéricos ("deve ser rápido")
- ✅ Derivar exclusivamente da documentação fornecida
- ✅ Usar métricas quantitativas quando possível
- ✅ Priorizar baseado em impacto real
```

---

## 🚀 Como Usar

### 1️⃣ Fluxo Recomendado (Workflow Técnico)

Este prompt é usado após definição de requisitos funcionais:

```
1️⃣ Vision & Problem Statement → Define estratégia
         ↓
2️⃣ Briefing → Contextualiza projeto
         ↓
3️⃣ PRD → Define requisitos funcionais
         ↓
4️⃣ Diagramas → Visualiza arquitetura
         ↓
5️⃣ NFRs (este) → Define atributos de qualidade
         ↓
6️⃣ ADRs → Documenta decisões técnicas
         ↓
7️⃣ Implementação → Desenvolvimento
```

**Vantagens de Definir NFRs Cedo:**
- Evita refatoração cara depois
- Influencia decisões arquiteturais
- Facilita estimativas realistas
- Reduz dívida técnica
- Garante qualidade desde o início

### 2️⃣ Onde Usar

- **Cursor IDE** → Cole como system prompt + forneça PRD
- **VS Code com extensões de IA** → Use como custom instructions
- **ChatGPT/Claude** → Análise de documentação técnica
- **Confluence/Notion** → Documentação de arquitetura
- **Jira/Linear** → Criação de technical stories

### 3️⃣ Exemplo Prático Completo

**Entrada (PRD Resumido):**

```markdown
# PRD - Plataforma de Pagamentos Online

**Requisitos Funcionais:**
- Processar pagamentos via cartão de crédito
- Suportar múltiplos gateways (Stripe, Adyen)
- Webhook de confirmação
- Dashboard de transações
- Refunds parciais e totais

**Contexto:**
- E-commerce B2C
- 10k transações/dia esperadas (pico: 50k)
- Disponível 24/7
- Dados sensíveis (PCI-DSS)
- Usuários no Brasil (LGPD)
```

**Saída Esperada (NFRs):**

A IA gerará documento completo com NFRs estruturados por categoria, métricas claras, justificativas e priorizações.

---

## 💡 Por Que Este Prompt Funciona

### ✅ 1. NFRs Mensuráveis e Testáveis
- Evita requisitos vagos ("deve ser rápido")
- Fornece critérios objetivos de aceitação
- Facilita validação em QA
- Permite monitoramento em produção

### ✅ 2. Alinhamento Técnico-Estratégico
- Conecta qualidade com objetivos de negócio
- Justifica investimento técnico
- Prioriza baseado em impacto real
- Reduz over-engineering

### ✅ 3. Cobertura Abrangente
- 10 categorias principais de qualidade
- Considera compliance e governança
- Inclui observabilidade e operações
- Não esquece usabilidade

### ✅ 4. Documentação Acionável
- Formato tabular fácil de consumir
- IDs rastreáveis
- Conectável com testes e métricas
- Usável em planejamento e estimativas

### ✅ 5. Escalável por Contexto
Funciona para:
- MVPs (NFRs essenciais)
- Produtos maduros (NFRs avançados)
- Sistemas críticos (NFRs rigorosos)
- Diferentes domínios (fintech, saúde, etc.)

---

## ⚠️ Observações Importantes

### O que este prompt faz:
- ✅ Extrai NFRs implícitos em documentação
- ✅ Formaliza requisitos de qualidade
- ✅ Define métricas mensuráveis
- ✅ Prioriza baseado em impacto
- ✅ Identifica riscos técnicos
- ✅ Sinaliza trade-offs e lacunas

### O que este prompt NÃO faz:
- ❌ Não define arquitetura técnica
- ❌ Não escolhe tecnologias específicas
- ❌ Não cria planos de teste detalhados
- ❌ Não substitui engenharia de performance
- ❌ Não gera código ou implementação
- ❌ Não garante compliance automaticamente

### Quando usar este prompt:
- **Use quando:**
  - PRD está completo ou quase completo
  - Vai iniciar planejamento técnico
  - Precisa estimar esforço realisticamente
  - Quer evitar dívida técnica
  - Compliance é crítico (fintech, saúde)
  - Sistema terá alta carga ou criticidade

- **Não use quando:**
  - Projeto ainda está em discovery
  - PRD está incompleto ou muito vago
  - É um protótipo descartável
  - NFRs já estão rigidamente definidos
  - Foco é apenas proof of concept

---

## 🔄 Personalização Avançada

### Para Diferentes Domínios:

**Fintech / Pagamentos:**
```markdown
## Categorias Prioritárias

Foque especialmente em:
- Segurança (PCI-DSS, criptografia)
- Disponibilidade (99.99% uptime)
- Confiabilidade (transações ACID)
- Auditoria (logs imutáveis)
- Performance (processamento < 2s)
- Compliance (regulamentações financeiras)
```

**Healthcare / Saúde:**
```markdown
## Categorias Prioritárias

Foque especialmente em:
- Privacidade (HIPAA, LGPD)
- Segurança (dados sensíveis de saúde)
- Disponibilidade (sistemas críticos)
- Auditoria (rastreabilidade completa)
- Interoperabilidade (HL7, FHIR)
- Integridade de dados
```

**E-commerce / Varejo:**
```markdown
## Categorias Prioritárias

Foque especialmente em:
- Performance (conversão)
- Escalabilidade (black friday)
- Disponibilidade (sem downtime)
- Usabilidade (checkout friction)
- Observabilidade (funil de vendas)
- Compatibilidade (devices, browsers)
```

**SaaS B2B:**
```markdown
## Categorias Prioritárias

Foque especialmente em:
- Disponibilidade (SLA contratual)
- Segurança (multi-tenancy)
- Escalabilidade (por tenant)
- Observabilidade (por cliente)
- Manutenibilidade (deploys frequentes)
- Integração (APIs confiáveis)
```

---

## 💭 Filosofia

> **"Requisitos não funcionais não dizem o que o sistema faz — dizem se ele merece existir em produção."**

Este prompt garante que:
- **Qualidade não é acidental**, mas intencional
- **Performance é medida**, não esperada
- **Segurança é design**, não add-on
- **Confiabilidade é garantida**, não prometida

---

## 🔄 Próximos Níveis (Evolução)

1. **NFRs → Test Strategy** - Conversão automática em plano de testes
2. **NFRs → SLOs/SLIs** - Tradução em service level objectives
3. **NFRs → Architecture Decision** - Influência em escolhas técnicas
4. **NFRs → Monitoring** - Geração de dashboards e alertas
5. **NFRs → Cost Model** - Estimativa de custos de infra
6. **NFRs → Production Readiness** - Checklist de go-live

---

## 🧠 Extensões Possíveis

### Variações do Template:

- **NFRs Lean** - Versão mínima para MVPs
- **NFRs Enterprise** - Versão completa para sistemas críticos
- **NFRs por Feature** - Requisitos específicos por funcionalidade
- **NFRs por Layer** - Frontend, Backend, Infra separados

### Integrações:

- **Datadog/New Relic** - Monitoramento de NFRs
- **PagerDuty** - Alertas de violação
- **Jira/Linear** - Technical stories
- **SonarQube** - Quality gates
- **k6/JMeter** - Performance testing

### Frameworks Relacionados:

```
NFRs
  ↓
ISO 25010 (Quality Model)
  ↓
SRE Principles (Google)
  ↓
12 Factor App
  ↓
Cloud Native Patterns
```

---

## 💡 Dicas Práticas

### Para Melhor Qualidade dos NFRs:

1. **Use números específicos** - "API responde em < 200ms p95" > "API deve ser rápida"
2. **Defina condições** - "Sob carga de 1000 req/s"
3. **Seja realista** - Baseado em benchmarks da indústria
4. **Priorize ruthlessly** - Nem tudo pode ser prioridade 1
5. **Conecte com negócio** - "200ms = +15% conversão"

### Checklist de Qualidade do NFR:

- [ ] Tem métrica quantitativa ou qualitativa clara?
- [ ] É testável automaticamente ou manualmente?
- [ ] Está conectado a uma necessidade real?
- [ ] Tem prioridade justificada?
- [ ] Considera trade-offs (custo, complexidade)?
- [ ] Inclui condições de contorno (carga, horário)?
- [ ] É independente de tecnologia específica?
- [ ] Tem ID rastreável único?

### Métricas por Categoria:

| Categoria | Exemplos de Métricas Boas |
|-----------|---------------------------|
| **Performance** | p50 < 100ms, p95 < 500ms, p99 < 1s |
| **Escalabilidade** | Suporta 10k usuários concurrent, 100k req/min |
| **Disponibilidade** | 99.9% uptime (43min downtime/mês) |
| **Confiabilidade** | Taxa de erro < 0.1%, MTTR < 15min |
| **Segurança** | 0 vulnerabilidades critical/high, MFA obrigatório |
| **Usabilidade** | Task completion rate > 95%, SUS score > 80 |

---

## 🔗 Integração com Outros Templates

Este template funciona melhor em conjunto:

```
🌍 Vision & Problem Statement → Define estratégia
    ↓
📋 Briefing → Contextualiza projeto
    ↓
📄 PRD → Define requisitos funcionais
    ↓
📐 Diagramas → Visualiza arquitetura
    ↓
⚙️ NFRs (este) → Define atributos de qualidade
    ↓
🏗️ ADRs → Documenta decisões técnicas
    ↓
🧪 Test Strategy → Valida NFRs
    ↓
💻 Implementação → Código + Infra
    ↓
📊 Monitoring → Valida NFRs em produção
```

**Fluxo completo de uso:**
1. Crie PRD com requisitos funcionais (template anterior)
2. Gere NFRs baseados no PRD (este template)
3. Use NFRs para informar decisões arquiteturais (ADRs)
4. Crie diagramas considerando NFRs
5. Implemente validação dos NFRs (testes, monitoring)
6. Monitore compliance em produção

---

## 📚 Exemplos Reais Completos

### Exemplo 1: Plataforma de Streaming de Vídeo

```markdown
# NFRs - StreamFlix (Plataforma de Streaming)

## 1. Visão Geral

StreamFlix é uma plataforma de streaming de vídeo on-demand para 100k+ usuários simultâneos. Qualidade de experiência e disponibilidade são críticas para retenção.

## 2. Premissas e Restrições

**Premissas:**
- CDN global disponível (Cloudflare/Akamai)
- Usuários com internet mínima de 5 Mbps
- Suporte a browsers modernos (últimas 2 versões)

**Restrições:**
- Budget de infra: $50k/mês inicial
- Lançamento em 4 meses
- Compliance: LGPD (Brasil)

## 3. NFRs por Categoria

### 3.1 Performance

| ID | Requisito | Descrição | Critério de Aceitação | Prioridade | Justificativa |
|----|-----------|-----------|----------------------|------------|---------------|
| NFR-PER-001 | Video Start Time | Tempo até primeiro frame do vídeo | < 2s (p95) sob rede 5Mbps | Alta | Cada 1s adicional = -6% conversão |
| NFR-PER-002 | Rebuffering Ratio | Taxa de pausa para buffering | < 0.5% do tempo de visualização | Alta | Rebuffering = churn primário |
| NFR-PER-003 | Search Latency | Tempo de resposta da busca | < 300ms (p95) | Média | Impacta descoberta de conteúdo |
| NFR-PER-004 | API Response Time | Endpoints críticos (catalog, auth) | < 200ms (p95) | Alta | Base para todas interações |

### 3.2 Escalabilidade

| ID | Requisito | Descrição | Critério de Aceitação | Prioridade | Justificativa |
|----|-----------|-----------|----------------------|------------|---------------|
| NFR-ESC-001 | Concurrent Users | Usuários simultâneos streaming | 100k usuários sem degradação | Alta | Meta de lançamento |
| NFR-ESC-002 | Peak Load Handling | Picos de acesso (releases) | 3x carga normal (300k) por 2h | Média | Lançamentos de conteúdo |
| NFR-ESC-003 | Horizontal Scaling | Capacidade de escalar | Auto-scaling em < 5min | Alta | Resposta a demanda |
| NFR-ESC-004 | Storage Growth | Crescimento de catálogo | Suporta 10k vídeos, +500/mês | Média | Roadmap de conteúdo |

### 3.3 Disponibilidade

| ID | Requisito | Descrição | Critério de Aceitação | Prioridade | Justificativa |
|----|-----------|-----------|----------------------|------------|---------------|
| NFR-DIS-001 | Uptime | Disponibilidade do serviço | 99.9% (43min downtime/mês) | Alta | SLA implícito com usuários |
| NFR-DIS-002 | Regional Failover | Redundância geográfica | Failover automático < 30s | Média | Desastres regionais |
| NFR-DIS-003 | Degradação Graciosa | Comportamento em falha parcial | Features não críticas degradam, core funciona | Alta | Experiência > nada |
| NFR-DIS-004 | CDN Availability | Distribuição de conteúdo | 99.99% (4min downtime/mês) | Alta | Core do negócio |

### 3.4 Confiabilidade

| ID | Requisito | Descrição | Critério de Aceitação | Prioridade | Justificativa |
|----|-----------|-----------|----------------------|------------|---------------|
| NFR-REL-001 | Error Rate | Taxa de erro em requests | < 0.1% (1 erro/1000 requests) | Alta | Experiência sem fricção |
| NFR-REL-002 | Data Consistency | Consistência de metadados | Eventual consistency < 5s | Média | Catálogo atualizado |
| NFR-REL-003 | Payment Processing | Confiabilidade de pagamentos | 99.95% success rate | Alta | Revenue crítico |
| NFR-REL-004 | MTTR | Tempo médio de recuperação | < 15 minutos | Alta | Minimizar impacto |

### 3.5 Segurança

| ID | Requisito | Descrição | Critério de Aceitação | Prioridade | Justificativa |
|----|-----------|-----------|----------------------|------------|---------------|
| NFR-SEG-001 | Content Protection | DRM para conteúdo premium | Widevine L3 mínimo | Alta | Contratos com produtoras |
| NFR-SEG-002 | Authentication | Autenticação de usuários | MFA opcional, OAuth2 | Alta | Proteção de contas |
| NFR-SEG-003 | API Security | Proteção de APIs | Rate limiting, JWT tokens | Alta | Prevenir abuse |
| NFR-SEG-004 | Data Encryption | Criptografia de dados | TLS 1.3 em trânsito, AES-256 em repouso | Alta | LGPD compliance |
| NFR-SEG-005 | Vulnerability Scanning | Scan de segurança | 0 vulns critical/high em produção | Alta | Postura de segurança |

### 3.6 Privacidade e Compliance

| ID | Requisito | Descrição | Critério de Aceitação | Prioridade | Justificativa |
|----|-----------|-----------|----------------------|------------|---------------|
| NFR-PRI-001 | LGPD Compliance | Conformidade com LGPD | Consentimento explícito, direito ao esquecimento | Alta | Obrigatório legal (Brasil) |
| NFR-PRI-002 | Data Retention | Retenção de dados pessoais | Máximo 2 anos após cancelamento | Alta | LGPD |
| NFR-PRI-003 | Audit Logging | Logs de acesso a dados sensíveis | 100% de acessos logados, retenção 1 ano | Alta | Auditoria e compliance |
| NFR-PRI-004 | Data Export | Portabilidade de dados do usuário | Export completo em < 24h | Média | Direito LGPD |

### 3.7 Usabilidade

| ID | Requisito | Descrição | Critério de Aceitação | Prioridade | Justificativa |
|----|-----------|-----------|----------------------|------------|---------------|
| NFR-USA-001 | Adaptive Bitrate | Ajuste automático de qualidade | Transição suave baseada em bandwidth | Alta | Experiência sem buffering |
| NFR-USA-002 | Resume Playback | Continuar de onde parou | Sincroniza posição em < 5s cross-device | Alta | Feature esperada |
| NFR-USA-003 | Accessibility | Acessibilidade WCAG | WCAG 2.1 Level AA | Média | Inclusão |
| NFR-USA-004 | Subtitles | Legendas e closed captions | Suporta múltiplos idiomas, sincronização < 100ms | Alta | Mercado internacional |

### 3.8 Observabilidade

| ID | Requisito | Descrição | Critério de Aceitação | Prioridade | Justificativa |
|----|-----------|-----------|----------------------|------------|---------------|
| NFR-OBS-001 | Metrics Collection | Coleta de métricas técnicas | 100% de serviços com métricas RED | Alta | Visibilidade operacional |
| NFR-OBS-002 | Distributed Tracing | Rastreamento de requests | 100% de APIs instrumentadas | Alta | Debug de performance |
| NFR-OBS-003 | Log Aggregation | Centralização de logs | Logs estruturados, busca em < 2s | Alta | Troubleshooting rápido |
| NFR-OBS-004 | Quality of Experience | Métricas de UX | Rebuffering, start time, error rate | Alta | North star metrics |
| NFR-OBS-005 | Alerting | Alertas de incidentes | Alert em < 1min para violações críticas | Alta | Resposta rápida |

### 3.9 Manutenibilidade

| ID | Requisito | Descrição | Critério de Aceitação | Prioridade | Justificativa |
|----|-----------|-----------|----------------------|------------|---------------|
| NFR-MAN-001 | Test Coverage | Cobertura de testes | > 80% code coverage, 100% paths críticos | Alta | Confiança em deploys |
| NFR-MAN-002 | Deployment Frequency | Frequência de deploy | Deploy to prod 3x/semana sem downtime | Média | Velocidade de entrega |
| NFR-MAN-003 | Rollback Time | Tempo de rollback | < 5 minutos | Alta | Recuperação de deploy ruim |
| NFR-MAN-004 | Documentation | Documentação técnica | README + ADRs + APIs documentadas | Média | Onboarding de devs |

### 3.10 Portabilidade

| ID | Requisito | Descrição | Critério de Aceitação | Prioridade | Justificativa |
|----|-----------|-----------|----------------------|------------|---------------|
| NFR-POR-001 | Browser Support | Compatibilidade de browsers | Chrome, Firefox, Safari, Edge (últimas 2 versões) | Alta | Cobertura de 95% usuários |
| NFR-POR-002 | Device Support | Dispositivos suportados | Web, iOS, Android, Smart TVs | Alta | Multi-platform |
| NFR-POR-003 | Cloud Portability | Independência de cloud | Arquitetura permite migração de AWS | Baixa | Mitigar vendor lock-in |

## 4. Matriz de Priorização

### Críticos (Must-Have) - P0
- Performance: NFR-PER-001, NFR-PER-002, NFR-PER-004
- Escalabilidade: NFR-ESC-001, NFR-ESC-003
- Disponibilidade: NFR-DIS-001, NFR-DIS-003, NFR-DIS-004
- Confiabilidade: NFR-REL-001, NFR-REL-003, NFR-REL-004
- Segurança: Todos (NFR-SEG-001 a 005)
- Privacidade: NFR-PRI-001, NFR-PRI-002, NFR-PRI-003
- Usabilidade: NFR-USA-001, NFR-USA-002, NFR-USA-004
- Observabilidade: NFR-OBS-001, NFR-OBS-003, NFR-OBS-004, NFR-OBS-005
- Manutenibilidade: NFR-MAN-001, NFR-MAN-003
- Portabilidade: NFR-POR-001, NFR-POR-002

### Importantes (Should-Have) - P1
- Performance: NFR-PER-003
- Escalabilidade: NFR-ESC-002, NFR-ESC-004
- Disponibilidade: NFR-DIS-002
- Confiabilidade: NFR-REL-002
- Privacidade: NFR-PRI-004
- Usabilidade: NFR-USA-003
- Observabilidade: NFR-OBS-002
- Manutenibilidade: NFR-MAN-002, NFR-MAN-004

### Desejáveis (Nice-to-Have) - P2
- Portabilidade: NFR-POR-003

## 5. Riscos Técnicos Mitigados

| Risco | NFRs que Mitigam | Impacto de Não Cumprimento |
|-------|------------------|---------------------------|
| Churn por má experiência | NFR-PER-001, NFR-PER-002 | -30% retenção |
| Downtime em lançamentos | NFR-ESC-001, NFR-ESC-002 | Perda de revenue, má imprensa |
| Breach de segurança | NFR-SEG-001 a 005 | Multas LGPD, perda de confiança |
| Incidentes não detectados | NFR-OBS-001 a 005 | MTTR alto, má experiência |
| Problemas em produção | NFR-MAN-001, NFR-MAN-003 | Rollbacks lentos, bugs |

## 6. Dependências e Impactos

### Impacto em Arquitetura:
- **Escalabilidade:** Requer arquitetura stateless, uso de CDN
- **Observabilidade:** Necessita APM (Datadog/New Relic)
- **Disponibilidade:** Multi-region deployment, cache agressivo

### Impacto em Custos:
- **CDN:** ~$15k/mês (100k users, 2h/dia viewing)
- **Infra (AWS):** ~$25k/mês (compute, storage, DB)
- **APM/Observability:** ~$5k/mês
- **DRM/Security:** ~$3k/mês
- **Total:** ~$48k/mês inicial

### Impacto em Prazos:
- NFRs de segurança e compliance: +3 semanas
- Observabilidade completa: +2 semanas
- Testes de carga e validação: +2 semanas

### Complexidade Operacional:
- Multi-region: Alta complexidade
- CDN management: Média complexidade
- Monitoring/alerting: Média complexidade

## 7. Fora de Escopo

- ❌ Live streaming (apenas VOD nesta fase)
- ❌ Social features (comentários, reviews)
- ❌ Offline downloads (mobile)
- ❌ 4K streaming (máximo 1080p inicialmente)
- ❌ GDPR full compliance (foco LGPD apenas)

## 8. Lacunas e Perguntas em Aberto

- ⚠️ **Qual encoding profile exato?** (H.264 vs H.265?)
- ⚠️ **CDN vendor definido?** (Cloudflare vs Akamai vs AWS CloudFront?)
- ⚠️ **Estratégia de cache?** (TTLs, invalidation strategy)
- ⚠️ **DRM keyserver?** (Build vs buy?)
- ⚠️ **Metrics backend?** (Prometheus vs Datadog vs custom?)
- ⚠️ **Peak load real?** (Depende de marketing, releases)
```

---

**Criado para garantir que qualidade, segurança e confiabilidade sejam intencionais, mensuráveis e acionáveis desde o início.**
