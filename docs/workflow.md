# 🎯 Como Escolher o Workflow Certo

> **"Nao existe workflow perfeito. Existe workflow certo para o contexto."**

Este guia te ajuda a escolher o workflow ideal para cada tarefa usando um **fluxo cognitivo de decisao**.

---

## Arvore de Decisao

Responda as perguntas abaixo para encontrar seu workflow:

```mermaid
flowchart TD
    START((🎯 Nova Tarefa)) --> P1

    subgraph PERGUNTAS["❓ Perguntas-Chave"]
        P1{1. Qual o OBJETIVO<br/>principal?}
        P2{2. Qual a COMPLEXIDADE<br/>da tarefa?}
        P3{3. Qual o RISCO<br/>envolvido?}
        P4{4. Precisa de<br/>FEEDBACK rapido?}
        P5{5. Time precisa<br/>ENTENDER o codigo?}
    end

    P1 -->|Velocidade maxima| P2
    P1 -->|Qualidade/Confianca| P3
    P1 -->|Clareza/Documentacao| SDD
    P1 -->|Aprendizado/Exploracao| SPIKE
    
    P2 -->|Simples| AIFIRST
    P2 -->|Media| P4
    P2 -->|Complexa| SDD_AI
    
    P3 -->|Alto - codigo critico| TDD
    P3 -->|Medio - regras de negocio| P5
    P3 -->|Baixo| PRAGMATIC
    
    P4 -->|Sim - MVP/Startup| ITERATIVE
    P4 -->|Nao - pode planejar| SDD
    
    P5 -->|Sim - time multidisciplinar| BDD
    P5 -->|Nao - so devs| TDD
    
    subgraph WORKFLOWS["📋 Workflows Recomendados"]
        SDD[📋 SDD<br/>Spec-Driven]
        TDD[🧪 TDD<br/>Test-Driven]
        BDD[🎭 BDD<br/>Behavior-Driven]
        AIFIRST[🤖 AI-First<br/>Prompt-Driven]
        SPIKE[🔬 Prototype-First<br/>Spike-Driven]
        ITERATIVE[🔄 Iterative<br/>Incremental]
        PRAGMATIC[🎯 Pragmatic<br/>Opportunistic]
        SDD_AI[📋+🤖 SDD + AI-First<br/>Combinado]
    end

    style START fill:#e8f5e9,stroke:#2e7d32,stroke-width:3px
    style SDD fill:#c8e6c9,stroke:#388e3c
    style TDD fill:#bbdefb,stroke:#1976d2
    style BDD fill:#e1bee7,stroke:#7b1fa2
    style AIFIRST fill:#ffccbc,stroke:#e64a19
    style SPIKE fill:#fff9c4,stroke:#fbc02d
    style ITERATIVE fill:#b2dfdb,stroke:#00897b
    style PRAGMATIC fill:#ffecb3,stroke:#ff8f00
    style SDD_AI fill:#f3e5f5,stroke:#6a1b9a
```

---

## Matriz de Decisao Rapida

### Por Objetivo

| Se voce quer... | Use este workflow |
|-----------------|-------------------|
| 🚀 **Desenvolver rapido** | [AI-First](workflows/ai-first-prompt-driven.md) |
| 📋 **Alinhar com time** | [SDD](workflows/spec-driven-development.md) |
| 🧪 **Codigo sem bugs** | [TDD](workflows/test-driven-development.md) |
| 💬 **Time entender codigo** | [BDD](workflows/behavior-driven-development.md) |
| 🔬 **Explorar tecnologia nova** | [Prototype-First](workflows/prototype-first-spike-driven.md) |
| 🔄 **Validar com usuarios** | [Iterative](workflows/iterative-incremental-development.md) |
| 🌳 **Deploy frequente** | [Trunk-Based](workflows/trunk-based-development.md) |
| 🎯 **Flexibilidade total** | [Pragmatic](workflows/pragmatic-opportunistic.md) |

### Por Tipo de Projeto

| Tipo de Projeto | Workflow Principal | Complementos |
|-----------------|-------------------|--------------|
| **MVP/Startup** | Iterative | + AI-First + Pragmatic |
| **Backend Critico** | TDD | + SDD + Trunk-Based |
| **Frontend Rapido** | AI-First | + Iterative |
| **API Publica** | SDD | + TDD + BDD |
| **Tecnologia Nova** | Prototype-First | + SDD |
| **Time Grande** | SDD | + Trunk-Based + BDD |
| **Solo Dev** | Pragmatic | + AI-First |

### Por Situacao

| Situacao | Melhor Abordagem |
|----------|-----------------|
| Bug critico em producao | Fix rapido + teste manual → Pragmatic |
| Feature nova simples | Codigo direto + testes depois → AI-First |
| Feature nova complexa | Spec + codigo + testes → SDD + TDD |
| Tecnologia desconhecida | Spike primeiro → Prototype-First |
| Logica de negocio | Teste antes → TDD |
| Time precisa alinhar | Spec primeiro → SDD |
| Validar ideia rapido | MVP + feedback → Iterative |
| Deploy continuo | Branches curtas → Trunk-Based |

---

## Fluxo Cognitivo Detalhado

### Pergunta 1: Qual o objetivo principal?

```mermaid
flowchart LR
    Q[Objetivo?] --> V[🚀 Velocidade]
    Q --> C[🧪 Confianca]
    Q --> A[📋 Alinhamento]
    Q --> E[🔬 Exploracao]
    
    V --> |AI ajuda| AIFIRST[AI-First]
    C --> |Testes garantem| TDD[TDD]
    A --> |Spec documenta| SDD[SDD]
    E --> |Spike valida| SPIKE[Prototype-First]
```

**Pergunte-se:**
- Preciso entregar rapido? → **Velocidade**
- O codigo nao pode ter bugs? → **Confianca**
- O time precisa entender? → **Alinhamento**
- Nao sei se vai funcionar? → **Exploracao**

---

### Pergunta 2: Qual a complexidade?

```mermaid
flowchart LR
    C[Complexidade?] --> S[📗 Simples<br/>1-2 horas]
    C --> M[📙 Media<br/>1-2 dias]
    C --> H[📕 Complexa<br/>1+ semanas]
    
    S --> DIRECT[Codigo direto<br/>ou AI-First]
    M --> SPEC[Spec leve<br/>ou TDD]
    H --> FULL[SDD completo<br/>+ TDD + Review]
```

**Indicadores de complexidade:**
- **Simples**: Uma funcao, um componente, bugfix
- **Media**: Uma feature, integracao, refatoracao
- **Complexa**: Sistema novo, arquitetura, multiplos servicos

---

### Pergunta 3: Qual o risco?

```mermaid
flowchart LR
    R[Risco?] --> H[🔴 Alto<br/>Critico]
    R --> M[🟡 Medio<br/>Importante]
    R --> L[🟢 Baixo<br/>Normal]
    
    H --> TDD[TDD obrigatorio<br/>+ Code Review]
    M --> TEST[Testes onde importa<br/>+ Spec]
    L --> FAST[Codigo rapido<br/>+ Teste manual]
```

**Codigo de alto risco:**
- Pagamentos, autenticacao, dados sensiveis
- Calculos financeiros, regras de negocio criticas
- Integracoes externas, APIs publicas

---

### Pergunta 4: Preciso de feedback rapido?

```mermaid
flowchart LR
    F[Feedback?] --> Y[✅ Sim<br/>Validacao]
    F --> N[❌ Nao<br/>Requisitos claros]
    
    Y --> ITER[Iterative<br/>MVP + Feedback + Ajuste]
    N --> SDD[SDD<br/>Spec + Implementacao]
```

**Quando feedback e critico:**
- Produto novo, startup, MVP
- Requisitos incertos
- Usuario final e desconhecido

---

### Pergunta 5: Time precisa entender o codigo?

```mermaid
flowchart LR
    T[Time?] --> DEV[👨‍💻 So Devs]
    T --> MULTI[👥 Multidisciplinar<br/>Dev + QA + Produto]
    
    DEV --> TDD[TDD<br/>Testes tecnicos]
    MULTI --> BDD[BDD<br/>Linguagem natural]
```

**BDD e ideal quando:**
- QA/Produto precisa validar specs
- Regras de negocio complexas
- Documentacao viva necessaria

---

## Como Usar IA de Forma Correta

```mermaid
flowchart TD
    A((Como usar IA<br/>corretamente?)) --> B[1. Dar contexto]
    
    B --> C[Padroes do projeto<br/>que IA deve seguir]
    B --> D[Ferramentas e libs<br/>que IA deve usar]
    
    C --> E[IA gera codigo<br/>no padrao desejado]
    D --> F[React, Zod, pnpm,<br/>Next.js, PostgreSQL...]
    
    F --> G[Quanto mais<br/>especificar, melhor!]
    G --> H[Crie as **Rules**<br/>e **SKILL.md**]
    
    H --> I{Qual workflow<br/>escolher?}
    I --> J[Use a arvore<br/>de decisao acima ☝️]

    style A fill:#e3f2fd,stroke:#1565c0,stroke-width:2px
    style H fill:#fff3e0,stroke:#e65100
    style I fill:#fce4ec,stroke:#c2185b
```

### Checklist para IA Eficiente

- [ ] **Contexto claro** - IA sabe o que o projeto faz
- [ ] **Padroes definidos** - Rules/.cursor/rules/
- [ ] **Stack especificada** - Libs, frameworks, versoes
- [ ] **Exemplos disponiveis** - Few-shot patterns
- [ ] **Workflow escolhido** - Sabe o processo a seguir

---

## Combinando Workflows

### Principio Fundamental

> **Nenhum time usa um workflow puro. A arte esta em combinar.**

### Formula do Workflow Moderno

```
┌─────────────────────────────────────────────────────────────┐
│                   WORKFLOW MODERNO EFICAZ                    │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│   📋 SDD          →  Alinhamento (o que fazer)               │
│   🧪 TDD          →  Confianca (funciona certo)              │
│   🔄 Iterative    →  Feedback (usuarios validam)             │
│   🤖 AI-First     →  Velocidade (IA acelera)                 │
│   🌳 Trunk-Based  →  Deploy (entrega continua)               │
│                                                              │
│   =  🚀 Desenvolvimento Eficiente                            │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

### Exemplos de Combinacao

#### MVP Rapido
```
Iterative (validacao) + AI-First (velocidade) + Pragmatic (flexibilidade)
```

#### Backend Critico
```
SDD (clareza) + TDD (confianca) + Trunk-Based (deploy)
```

#### Time Grande
```
SDD (alinhamento) + BDD (comunicacao) + Trunk-Based (integracao)
```

---

## Proximos Passos

1. **Identifique sua tarefa** - O que voce precisa fazer?
2. **Responda as perguntas** - Use a arvore de decisao
3. **Escolha o workflow** - Principal + complementos
4. **Leia a documentacao** - Do workflow escolhido
5. **Configure o ambiente** - Rules, prompts, templates
6. **Execute** - Aplique o workflow na pratica

---

## Links Uteis

- 📚 [Mapa Completo de Workflows](workflows/work-flows.md)
- 📋 [SDD - Spec-Driven](workflows/spec-driven-development.md)
- 🧪 [TDD - Test-Driven](workflows/test-driven-development.md)
- 🎭 [BDD - Behavior-Driven](workflows/behavior-driven-development.md)
- 🤖 [AI-First](workflows/ai-first-prompt-driven.md)
- 🔬 [Prototype-First](workflows/prototype-first-spike-driven.md)
- 🔄 [Iterative](workflows/iterative-incremental-development.md)
- 🌳 [Trunk-Based](workflows/trunk-based-development.md)
- 🎯 [Pragmatic](workflows/pragmatic-opportunistic.md)

---

**Ultima Atualizacao**: 2024
