# 🌍 Template de Geração de Vision & Problem Statement - Cursor IDE

Template de prompt baseado em **síntese estratégica de informações** para definição clara de visão de produto e problema central. Ideal para alinhamento estratégico, product discovery, priorização e servir como documento-base (north star) para todo o fluxo de desenvolvimento.

---

## 📝 Template do Prompt

Copie e personalize o template abaixo. Este prompt é o **ponto de partida estratégico** — deve ser usado antes do Briefing.

```markdown
## Role (Identidade da IA)

Você é um **Product Leader e estrategista de produto** com experiência em:
- Definição de visão de produto (product vision)
- Formulação de problem statements claros e acionáveis
- Product discovery e validação de problemas
- Alinhamento estratégico entre negócio, usuário e tecnologia
- Síntese estratégica para tomada de decisão
- Frameworks como Jobs to Be Done, Opportunity Solution Tree

Você domina produtos de {{dominio}} (ex.: SaaS, fintech, edtech, healthtech, marketplaces, plataformas B2B).

## Objetivo

Transformar informações dispersas em um **Vision Statement** e um **Problem Statement** claros, concisos e acionáveis, que servirão como **base estratégica** para todo o desenvolvimento do produto.

## Contexto

Este documento é o **norte estratégico** do produto. Ele deve:
- Definir **para quem** o produto existe
- Explicitar **qual problema relevante** está sendo resolvido
- Apontar **por que isso importa**
- Descrever **qual futuro desejado** o produto busca criar
- **NÃO** definir soluções, features ou decisões técnicas

## Entrada (Fonte de Verdade)

O usuário fornecerá informações estratégicas ou documentação existente:

- 📊 **Pesquisas de mercado**
- 🗣️ **Entrevistas com usuários**
- 📋 **Discovery notes**
- 💼 **Objetivos de negócio**
- 📈 **Dados de comportamento**
- 🎯 **Insights de produto**

Use **exclusivamente** essas informações como fonte.

## Estrutura Esperada da Resposta

O documento deve seguir esta estrutura:

### 1. Vision Statement

Produza uma visão de produto clara e inspiradora que responda:
- Para quem o produto é
- Que mudança positiva ele promove
- Qual valor duradouro entrega
- Qual impacto deseja causar no longo prazo

**Formato recomendado:**
> "Nossa visão é [transformação desejada] para [público-alvo], permitindo [valor principal] de forma [diferencial chave]."

**Características:**
- Concisa (1-2 frases)
- Inspiradora mas factível
- Orientada ao usuário/cliente
- Atemporal (não muda a cada trimestre)

### 2. Problem Statement

Formule o problema central de forma clara e específica.

**Estrutura:**
- **Quem:** Público-alvo específico
- **Contexto:** Situação atual do usuário
- **Problema:** Dor principal enfrentada
- **Impacto:** Consequências de não resolver
- **Lacuna:** Por que soluções existentes falham

**Formato sugerido:**
> "[Público-alvo] enfrenta [problema principal] quando [contexto].
> Isso resulta em [impacto negativo], pois [causa raiz ou lacuna]."

### 3. Público-Alvo (Target Audience)

Detalhamento de quem enfrenta o problema:
- Segmentos principais
- Personas chave (se houver)
- Contexto de uso relevante
- Tamanho do mercado (se conhecido)

### 4. Necessidades e Dores Principais

Liste as principais necessidades e dores:
- Necessidades explícitas (o que dizem)
- Necessidades latentes (o que sentem mas não verbalizam)
- Dores recorrentes
- Frustrações relevantes
- Jobs to Be Done (se aplicável)

### 5. Resultados Desejados (Outcomes)

O que muda quando o problema é resolvido:
- Mudanças no comportamento do usuário
- Resultados de negócio esperados
- Indicadores de sucesso em alto nível
- Valor gerado para stakeholders

### 6. O que NÃO é o Problema (Anti-Problema)

Clareza sobre escopo:
- Problemas fora de escopo
- Suposições incorretas comuns
- Soluções disfarçadas de problema
- Red herrings e distrações

### 7. Premissas e Restrições

Contexto de contorno:
- Premissas conhecidas
- Restrições de negócio
- Restrições de mercado
- Limitações de recursos ou tempo

### 8. Perguntas em Aberto

O que ainda precisa ser validado:
- Hipóteses a testar
- Lacunas de informação críticas
- Riscos de entendimento
- Áreas que precisam de discovery

## Diretrizes

- Use **linguagem clara, objetiva e estratégica**
- Evite jargões desnecessários
- **Não descreva soluções ou features**
- Não faça promessas vagas
- Seja específico sobre o público e contexto
- Se algo não está claro, **declare explicitamente**

## Formato da Resposta

1. **Gere apenas** o documento Vision & Problem Statement
2. **Utilize Markdown** bem estruturado
3. Use **títulos, listas e blocos de citação**
4. **Sem emojis** no documento final
5. **Pronto para compartilhar** com stakeholders e times

## Restrições

- ❌ Não inventar dados ou insights
- ❌ Não incluir comentários sobre o processo
- ❌ Não assumir soluções
- ❌ Não usar conhecimento externo não fornecido
- ❌ Não criar métricas detalhadas (isso vem depois)
- ✅ Basear-se exclusivamente nas informações fornecidas
- ✅ Sinalizar lacunas de informação
- ✅ Focar no problema, não na solução
```

---

## 🚀 Como Usar

### 1️⃣ Fluxo Recomendado (Product Discovery Pipeline)

Este prompt é o **ponto de partida** da documentação:

```
0️⃣ Research & Discovery → Coleta de insights
         ↓
1️⃣ Vision & Problem Statement (este) → Define norte estratégico
         ↓
2️⃣ Briefing → Detalha contexto e objetivos
         ↓
3️⃣ PRD → Define requisitos e funcionalidades
         ↓
4️⃣ ADRs → Documenta decisões arquiteturais
         ↓
5️⃣ Diagramas → Visualiza fluxos e arquitetura
         ↓
6️⃣ Implementação → Desenvolvimento
```

**Vantagens de Começar pela Vision:**
- Garante foco no problema certo
- Evita soluções prematuras
- Alinha expectativas de stakeholders
- Facilita priorização futura
- Serve como critério de decisão

### 2️⃣ Onde Usar

- **Cursor IDE** → Cole como system prompt + forneça research
- **VS Code com extensões de IA** → Use como custom instructions
- **ChatGPT/Claude** → Sessão de discovery estratégico
- **Miro/FigJam** → Combine com workshop de discovery
- **Notion/Confluence** → Documente como fonte única de verdade

### 3️⃣ Exemplo Prático Completo

**Entrada (Research Notes):**

```markdown
# Discovery Notes - Sistema de Gestão Financeira para PMEs

**Entrevistas (15 donos de pequenas empresas):**
- 80% usam planilhas Excel desorganizadas
- Gastam 8-12h/mês fazendo fechamento manual
- Não conseguem prever fluxo de caixa
- Medo de errar declarações fiscais
- Ferramentas existentes são caras ou complexas

**Dores principais:**
- "Nunca sei se tenho dinheiro para investir"
- "Tenho medo de esquecer uma conta"
- "Levo dias para preparar impostos"

**Contexto:**
- Brasil, 2024
- 5-20 funcionários
- Faturamento R$ 500k - R$ 5M/ano
- Sem contador interno
```

**Saída Esperada (Vision & Problem Statement):**

```markdown
# Vision & Problem Statement: FinFlow

## Vision Statement

> "Nossa visão é empoderar pequenas e médias empresas brasileiras a tomarem decisões financeiras confiantes e informadas, oferecendo clareza total sobre sua saúde financeira de forma simples e acessível."

## Problem Statement

> "Donos de pequenas e médias empresas (5-20 funcionários) enfrentam insegurança constante sobre sua situação financeira real quando gerenciam finanças manualmente em planilhas.
> 
> Isso resulta em decisões de investimento atrasadas, risco de problemas fiscais e desperdício de 8-12h/mês em fechamentos manuais, pois ferramentas existentes são muito caras (R$ 500+/mês) ou complexas demais para quem não tem conhecimento técnico contábil."

## Público-Alvo

- **Segmento primário:** Donos/sócios de PMEs (5-20 funcionários)
- **Faturamento:** R$ 500k - R$ 5M/ano
- **Localização:** Brasil
- **Contexto:** Sem contador interno, sem conhecimento contábil avançado
- **Tamanho estimado:** ~2M empresas no Brasil

[... resto do documento ...]
```

---

## 💡 Por Que Este Prompt Funciona

### ✅ 1. Clareza Estratégica
- Força foco no **problema certo**
- Evita "solution jumping" prematuro
- Alinha todos os stakeholders desde o início
- Cria critério de decisão claro

### ✅ 2. Separação Problema vs Solução
- Base sólida para product discovery
- Reduz retrabalho por desalinhamento
- Facilita validação de hipóteses
- Permite explorar múltiplas soluções

### ✅ 3. Estrutura Testada em Produto
- Inspirada em Product Discovery (Teresa Torres)
- Compatível com Lean Startup e Design Thinking
- Facilita evolução para OKRs e roadmap
- Formato reconhecido por PMs

### ✅ 4. Documento Vivo
- Serve como north star permanente
- Pode ser revisitado e refinado
- Base para alignment checks
- Referência para priorização

### ✅ 5. Escalável
Funciona para:
- Produtos greenfield (do zero)
- Evolução de produtos existentes
- Novos mercados ou segmentos
- Pivots estratégicos

---

## ⚠️ Observações Importantes

### O que este prompt faz:
- ✅ Define visão estratégica clara
- ✅ Articula problema de forma acionável
- ✅ Identifica público-alvo específico
- ✅ Mapeia necessidades e dores
- ✅ Estabelece outcomes desejados
- ✅ Sinaliza lacunas e riscos

### O que este prompt NÃO faz:
- ❌ Não define soluções ou features
- ❌ Não cria roadmap ou backlog
- ❌ Não especifica requisitos técnicos
- ❌ Não substitui research com usuários
- ❌ Não garante product-market fit
- ❌ Não define arquitetura ou tecnologia

### Quando usar este prompt:
- **Use quando:**
  - Iniciando novo produto ou feature grande
  - Pivotando estratégia de produto
  - Desalinhamento entre stakeholders
  - Antes de investir em desenvolvimento
  - Preparando discovery ou pesquisa

- **Não use quando:**
  - Problema já está muito bem documentado
  - Foco é apenas execução técnica
  - Solução já foi validada e aprovada
  - Mudança é pequena e incremental

---

## 🔄 Personalização Avançada

### Para Diferentes Contextos:

**Produto Novo (Greenfield):**
```markdown
## Foco Adicional

Inclua:
- Análise de mercado e concorrentes
- Assumptions críticas a validar
- Riscos de mercado e timing
- Estratégia de entrada no mercado
```

**Evolução de Produto Existente:**
```markdown
## Foco Adicional

Inclua:
- Limitações da versão atual
- Feedback de usuários existentes
- Métricas atuais de uso/satisfação
- Oportunidades identificadas nos dados
```

**Produto B2B Enterprise:**
```markdown
## Foco Adicional

Inclua:
- Buyers vs end-users
- Processo de compra e aprovação
- Critérios de ROI e business case
- Restrições de compliance e segurança
```

**Produto B2C / Consumer:**
```markdown
## Foco Adicional

Inclua:
- Momentos de uso e contexto
- Aspectos emocionais e comportamentais
- Hábitos e rituais do usuário
- Triggers e motivações
```

---

## 💭 Filosofia

> **"Uma visão clara não diz apenas para onde ir — ela diz o que ignorar."**

Este prompt garante que produto e times:
- **Comecem pelo problema certo**
- **Mantenham alinhamento estratégico**
- **Tomem decisões com critério claro**
- **Evitem desperdício de desenvolvimento**

---

## 🔄 Próximos Níveis (Evolução)

1. **Vision por horizonte** - Now/Next/Later roadmap
2. **Problem statement por segmento** - Multi-persona products
3. **Opportunity Solution Tree** - Framework de Teresa Torres
4. **Continuous Discovery Habits** - Discovery contínuo
5. **Vision to OKRs** - Tradução automática em objetivos
6. **Problem validation framework** - Checklist de validação

---

## 🧠 Extensões Possíveis

### Variações do Template:

- **Vision Deck** - Apresentação visual para stakeholders
- **One-page Vision** - Versão executiva resumida
- **Vision Canvas** - Formato workshop/canvas
- **Problem Tree** - Desdobramento de problemas

### Integrações:

- **Miro/FigJam** - Workshop colaborativo
- **ProductBoard** - Feedback de usuários
- **Amplitude/Mixpanel** - Dados comportamentais
- **Notion/Confluence** - Single source of truth

### Frameworks Complementares:

```
Vision & Problem Statement
    ↓
Opportunity Solution Tree (Teresa Torres)
    ↓
Jobs to Be Done (Clayton Christensen)
    ↓
Value Proposition Canvas (Strategyzer)
    ↓
Lean Canvas (Ash Maurya)
```

---

## 💡 Dicas Práticas

### Para Melhor Qualidade da Vision:

1. **Seja específico no público** - "PMEs brasileiras" > "empresas"
2. **Evite buzzwords vazios** - "empoderar" deve ter significado real
3. **Teste com stakeholders** - Todos entendem igual?
4. **Vision ≠ Mission** - Vision é sobre o futuro, mission é sobre propósito
5. **Mantenha atemporal** - Não mencione features específicas

### Checklist de Qualidade do Problem Statement:

- [ ] Descreve um público-alvo específico?
- [ ] Articula o problema, não a solução?
- [ ] Explica o impacto/consequência do problema?
- [ ] Menciona o contexto em que ocorre?
- [ ] Clarifica por que soluções atuais falham?
- [ ] É verificável com pesquisa/dados?
- [ ] É grande o suficiente para importar?
- [ ] É específico o suficiente para ser acionável?

### Red Flags (Sinais de Alerta):

❌ **Vision muito genérica:**
- "Ser líder de mercado"
- "Revolucionar a indústria"
- "Melhor experiência do usuário"

✅ **Vision específica:**
- "Permitir que todo dono de PME brasileira tome decisões financeiras com confiança em menos de 5 minutos por dia"

❌ **Problem disfarçado de solução:**
- "Falta de um app mobile"
- "Ausência de integrações"

✅ **Problem real:**
- "Donos de PME gastam 8-12h/mês em fechamentos manuais e ainda têm medo de errar impostos"

---

## 🔗 Integração com Outros Templates

Este template é o **ponto de partida** da cadeia:

```
🌍 Vision & Problem Statement (este)
    ↓
    Define: Para quem? Qual problema? Por quê?
    ↓
📋 Briefing
    ↓
    Detalha: Contexto, objetivos, restrições
    ↓
📄 PRD
    ↓
    Especifica: Requisitos, funcionalidades, critérios
    ↓
🏗️ ADR
    ↓
    Documenta: Decisões arquiteturais
    ↓
📐 Diagramas
    ↓
    Visualiza: Fluxos, arquitetura, jornadas
    ↓
💻 Implementação
```

**Fluxo completo de uso:**
1. **Faça research/discovery** com usuários e mercado
2. **Gere Vision & Problem Statement** (este template)
3. **Valide com stakeholders** e refine se necessário
4. **Use como input** para Briefing (próximo template)
5. **Referencie constantemente** durante desenvolvimento
6. **Revise periodicamente** (quarterly reviews)

---

## 📚 Exemplos Reais Completos

### Exemplo 1: Produto SaaS B2B

```markdown
# Vision & Problem Statement: TeamSync

## Vision Statement

> "Nossa visão é transformar times remotos em equipes altamente produtivas e conectadas, oferecendo visibilidade em tempo real do trabalho assíncrono sem sacrificar a autonomia individual."

## Problem Statement

> "Tech leads de times distribuídos (5-30 pessoas) enfrentam ansiedade constante sobre o progresso real do trabalho quando dependem de daily standups síncronos em múltiplos fusos horários.
> 
> Isso resulta em reuniões excessivas (10-15h/semana), burnout de liderança, e atrasos na identificação de bloqueios, pois ferramentas atuais (Jira, Linear) mostram apenas status de tickets, não o contexto real do trabalho e energia do time."

## Público-Alvo

- **Segmento primário:** Tech Leads, Engineering Managers
- **Tamanho do time:** 5-30 pessoas
- **Contexto:** Times distribuídos (2+ fusos horários)
- **Tipo de empresa:** Startups/Scale-ups tech
- **Mercado:** Global, foco inicial EUA/Europa

## Necessidades Principais

1. **Visibilidade assíncrona:** Ver progresso sem interromper o time
2. **Contexto rico:** Entender além do status (energia, bloqueios, colaboração)
3. **Antecipação de problemas:** Identificar riscos antes de virarem crises
4. **Respeito ao deep work:** Não adicionar overhead ao time
5. **Síntese automática:** Transformar sinais em insights

## Dores Principais

- Ansiedade de não saber se time está bem
- Reuniões em excesso por falta de visibilidade
- Descobrir bloqueios tarde demais
- Burnout de micromanagement
- Time se sentindo vigiado por ferramentas de tracking

## Resultados Desejados

**Para Tech Leads:**
- Reduzir reuniões de status em 50%
- Identificar bloqueios 2-3 dias mais cedo
- Reduzir ansiedade sobre progresso do time
- Mais tempo para mentoria e estratégia

**Para o Time:**
- Menos interrupções síncronas
- Sentir-se apoiado, não vigiado
- Autonomia mantida
- Reconhecimento de esforço invisível

**Para a Empresa:**
- Velocity mais previsível
- Menos projetos atrasados por surpresa
- Retenção de talentos melhorada
- Cultura de confiança

## O que NÃO é o Problema

- ❌ Falta de ferramentas de tracking (existem várias)
- ❌ Time não trabalha o suficiente (premissa falsa)
- ❌ Necessidade de monitorar horário de trabalho
- ❌ Substituir comunicação humana por dashboards

## Premissas

- Times já usam ferramentas como Jira/Linear/GitHub
- Líderes confiam no time (não querem surveillance)
- Trabalho é majoritariamente assíncrono
- Cultura de escrita e documentação existe

## Restrições

- Não pode adicionar overhead significativo ao time
- Deve respeitar privacidade individual
- Não pode ser usado como ferramenta punitiva
- Precisa funcionar com ferramentas existentes

## Perguntas em Aberto

- Qual é o threshold de "informação suficiente"?
- Como diferenciar de ferramentas de surveillance?
- Qual frequência de atualização não vira ruído?
- Como garantir que não cria pressão por "sempre online"?
```

### Exemplo 2: Produto B2C Mobile

```markdown
# Vision & Problem Statement: MealPlan

## Vision Statement

> "Nossa visão é tornar alimentação saudável acessível e sem fricção para famílias brasileiras, permitindo que qualquer pessoa planeje refeições nutritivas em minutos, não horas, independente de conhecimento culinário."

## Problem Statement

> "Pais e mães (25-45 anos) sentem culpa e estresse diários ao decidir o que cozinhar quando chegam cansados do trabalho às 19h sem ter planejado refeições.
> 
> Isso resulta em dependência de delivery não saudável (3-5x/semana), gastos 40% maiores com comida, e sentimento de fracasso como pais, pois apps de receitas exigem tempo que não têm, e meal kits são caros demais (R$ 150+/pessoa/semana) para a realidade brasileira."

## Público-Alvo

- **Segmento primário:** Pais/mães trabalhadores, 25-45 anos
- **Composição familiar:** 2-4 pessoas (com crianças)
- **Renda:** Classe B/C (R$ 5k-15k familiar)
- **Localização:** Brasil, grandes cidades
- **Contexto:** Ambos trabalham fora, chegam cansados

## Necessidades Principais

1. **Rapidez:** Decisão em < 5 minutos
2. **Simplicidade:** Receitas com < 30min preparo
3. **Ingredientes acessíveis:** Disponíveis no supermercado local
4. **Variedade:** Não repetir toda semana
5. **Nutrição:** Equilibrado sem ser chato

## Dores Principais

- "Não sei o que fazer para jantar HOJE"
- "Sempre acabo pedindo delivery e me sinto mal"
- "Receitas online são muito complexas"
- "Tenho ingredientes mas não sei combinar"
- "Meal kit é caro e nem sempre vem tudo"

## Resultados Desejados

**Para Usuários:**
- Reduzir delivery não planejado em 60%
- Economizar R$ 400-600/mês
- Refeições caseiras 5x/semana (vs 2x atual)
- Menos culpa e estresse sobre alimentação

**Comportamentais:**
- Abrir app às 18h, decidir em 5min
- Compra no mercado mais assertiva
- Menos desperdício de alimentos
- Crianças comendo melhor

## O que NÃO é o Problema

- ❌ Falta de receitas disponíveis online
- ❌ Pessoas não sabem cozinhar nada
- ❌ Querem virar chefs gourmet
- ❌ Precisam de refeições instagram-worthy

## Premissas

- Usuários sabem cozinhar básico
- Têm acesso a supermercado
- Possuem smartphone
- Querem comer em casa (não são contra)

## Restrições

- Precisa funcionar offline (receitas salvas)
- Lista de compras fácil de usar no mercado
- Adequado à realidade de ingredientes do Brasil
- Preço acessível (< R$ 30/mês)

## Perguntas em Aberto

- Qual é a unidade de planejamento ideal? (semana? dia?)
- Como lidar com restrições alimentares variadas?
- Como adaptar receitas ao que já têm na geladeira?
- Como motivar mudança de hábito de delivery?
```

---

**Criado para garantir que produtos comecem pelo problema certo, com clareza estratégica e alinhamento total.**
