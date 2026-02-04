# 📄 Template de Geração de PRD (Product Requirements Document) - Cursor IDE

Template de prompt baseado em **transformação estruturada de briefing em PRD** para gerar documentos de requisitos de produto completos e profissionais. Ideal para traduzir problemas de negócio em especificações técnicas acionáveis para equipes de engenharia e design.

---

## 📝 Template do Prompt

Copie e personalize o template abaixo. Este prompt utiliza **Prompt Chaining** — deve receber um briefing como entrada.

```markdown
## Role (Identidade da IA)

Você é um **Product Manager sênior** com experiência em:
- Tradução de briefings em PRDs estruturados
- Definição de requisitos funcionais e não-funcionais
- Comunicação entre negócio, design e engenharia
- Produtos digitais (SaaS, apps mobile, plataformas web)

## Objetivo

Transformar o **briefing fornecido** em um **PRD (Product Requirements Document)** completo, claro e acionável para equipes de desenvolvimento e design.

## Contexto

Um briefing foi previamente criado e aprovado. Agora, você deve **traduzir** esse briefing em especificações técnicas e funcionais, sem alterar o escopo ou inventar novos requisitos.

## Entrada (Input)

O usuário fornecerá um **briefing completo**. Use-o como **fonte única de verdade**.

## Estrutura Esperada do PRD

O PRD deve seguir esta estrutura:

### 1. Visão Geral do Produto
- Nome do produto
- Objetivo estratégico
- Problema que resolve
- Proposta de valor

### 2. Contexto e Justificativa
- Por que estamos construindo isso?
- Qual o impacto esperado?
- Como se alinha com a estratégia da empresa?

### 3. Público-Alvo e Personas
- Quem são os usuários?
- Quais suas necessidades e dores?
- Comportamentos e contextos de uso

### 4. Requisitos Funcionais
Lista objetiva de funcionalidades:
- **RF001:** [Descrição clara do requisito]
- **RF002:** [Descrição clara do requisito]
- Priorização (Must-have / Should-have / Nice-to-have)

### 5. Requisitos Não-Funcionais
- Performance (tempo de resposta, carga)
- Segurança (autenticação, autorização, dados sensíveis)
- Escalabilidade
- Acessibilidade
- Compatibilidade (browsers, dispositivos)

### 6. Fluxos de Usuário (User Flows)
Descreva os principais fluxos:
- Onboarding
- Feature principal
- Casos de erro/exceção

### 7. Critérios de Aceitação
Para cada requisito principal:
- Dado [contexto]
- Quando [ação]
- Então [resultado esperado]

### 8. Fora de Escopo (Out of Scope)
Liste explicitamente o que **NÃO** será construído nesta versão.

### 9. Dependências e Integrações
- APIs externas
- Sistemas legados
- Serviços de terceiros

### 10. Riscos e Mitigações
- Riscos técnicos
- Riscos de produto
- Planos de mitigação

### 11. Métricas de Sucesso
- KPIs a serem monitorados
- Metas quantitativas
- Como medir o impacto

### 12. Cronograma e Fases (se aplicável)
- MVP / Fase 1
- Iterações futuras
- Marcos importantes

## Diretrizes

- **Baseie-se EXCLUSIVAMENTE no briefing fornecido**
- Não invente funcionalidades ou requisitos
- Use linguagem clara, objetiva e técnica
- Evite ambiguidades
- Priorize requisitos quando possível
- Seja específico em critérios de aceitação

## Formato da Resposta

1. **Gere apenas** o conteúdo do PRD completo
2. **Utilize Markdown** bem estruturado
3. **Sem emojis** no PRD final
4. **Pronto para compartilhar** com equipes de engenharia e design

## Restrições

- ❌ Não adicione requisitos não mencionados no briefing
- ❌ Não proponha soluções técnicas específicas (isso é papel da engenharia)
- ❌ Não assuma decisões estratégicas não definidas no briefing
- ✅ Foque em **O QUE** construir, não **COMO** construir
```

---

## 🚀 Como Usar

### 1️⃣ Fluxo Recomendado (Prompt Chaining)

Este prompt funciona melhor em um **workflow encadeado**:

```
1️⃣ Prompt Briefing → Gera briefing completo
         ↓
2️⃣ Prompt PRD (este) → Transforma briefing em PRD
         ↓
3️⃣ Prompt Técnico → Quebra PRD em tarefas/épicos (opcional)
```

**Vantagens do Chaining:**
- Reduz alucinação (cada prompt tem fonte clara)
- Mantém coerência entre documentos
- Facilita iteração e refinamento
- Cria pipeline documental completo

### 2️⃣ Onde Usar

- **Cursor IDE** → Cole como system prompt + forneça briefing
- **VS Code com extensões de IA** → Use como custom instructions
- **ChatGPT/Claude** → Cole prompt + briefing na conversa
- **APIs** → System message + briefing como user message
- **Workflows automatizados** → Integre com ferramentas de gestão

### 3️⃣ Exemplo Prático Completo

**Entrada (Briefing Resumido):**

```markdown
# Briefing - TaskFlow Pro

**Problema:** Times remotos perdem produtividade por falta de visibilidade
**Objetivo:** Ferramenta de gestão de tarefas para times remotos
**Público:** Tech leads e product managers de startups
**Features principais:**
- Kanban boards
- Time tracking
- Notificações em tempo real
- Integrações Slack/GitHub
```

**Saída Esperada (PRD):**

A IA gerará um PRD completo com:
- Requisitos funcionais detalhados para cada feature
- Requisitos não-funcionais (performance, segurança)
- Fluxos de usuário
- Critérios de aceitação
- Métricas de sucesso

---

## 💡 Por Que Este Prompt Funciona

### ✅ 1. Prompt Chaining Controlado
- Usa o briefing como **fonte única de verdade**
- Reduz ruído e alucinação
- Mantém coerência entre documentos
- Facilita rastreabilidade

### ✅ 2. Escopo Bem Definido
- **PRD ≠ Solução técnica** (isso é papel da engenharia)
- **PRD ≠ Planejamento de sprint** (isso vem depois)
- **PRD = Tradução de problema → requisitos**
- Foca no **O QUE**, não no **COMO**

### ✅ 3. Estrutura Profissional de PRD
- Alinhada com práticas reais de Product Management
- Facilita handoff para engenharia e design
- Reduz retrabalho e interpretação ambígua
- Formato reconhecido pela indústria

### ✅ 4. Escalável e Adaptável
Funciona para diversos tipos de produtos:
- SaaS (web apps)
- Apps mobile (iOS/Android)
- Plataformas internas (ferramentas enterprise)
- Produtos B2B e B2C
- MVPs e produtos maduros

### ✅ 5. Reduz Ambiguidade
- Critérios de aceitação claros (Given/When/Then)
- Requisitos priorizados (Must/Should/Nice-to-have)
- Escopo negativo explícito (Out of Scope)
- Dependências mapeadas

---

## ⚠️ Observações Importantes

### O que este prompt faz:
- ✅ Traduz briefing em especificações técnicas
- ✅ Define requisitos funcionais e não-funcionais
- ✅ Estabelece critérios de aceitação claros
- ✅ Prioriza funcionalidades
- ✅ Identifica riscos e dependências

### O que este prompt NÃO faz:
- ❌ Não decide arquitetura técnica
- ❌ Não escolhe tecnologias ou frameworks
- ❌ Não cria planejamento de sprint
- ❌ Não substitui discovery ou validação de produto
- ❌ Não inventa requisitos não mencionados no briefing

### Quando usar este prompt:
- **Use quando:**
  - Briefing está completo e validado
  - Precisa documentar requisitos para engenharia
  - Vai iniciar desenvolvimento
  - Quer alinhar expectativas técnicas
  - Precisa de base para estimativas

- **Não use quando:**
  - Briefing está incompleto ou mal definido
  - Projeto ainda está em fase de discovery
  - Decisões estratégicas ainda não foram tomadas
  - Produto precisa de validação de mercado primeiro

---

## 🔄 Personalização Avançada

### Para Diferentes Tipos de Produto:

**SaaS / Web App:**
```markdown
## Requisitos Adicionais

Foque em:
- Autenticação e autorização (SSO, RBAC)
- Multi-tenancy e isolamento de dados
- APIs RESTful ou GraphQL
- Webhooks para integrações
- Dashboard de analytics
```

**App Mobile:**
```markdown
## Requisitos Adicionais

Foque em:
- Suporte offline (sync)
- Push notifications
- Geolocalização
- Permissões de dispositivo
- Compatibilidade iOS/Android
```

**Plataforma Interna (Enterprise):**
```markdown
## Requisitos Adicionais

Foque em:
- Integração com Active Directory
- Compliance e auditoria
- Logs detalhados de ações
- Backups e disaster recovery
- SLA e uptime
```

**Produto com IA/ML:**
```markdown
## Requisitos Adicionais

Foque em:
- Qualidade e viés dos dados
- Transparência do modelo (explainability)
- Fallbacks quando modelo falha
- Performance de inferência
- Retreinamento e versionamento
```

---

## 💭 Filosofia

> **"Um bom PRD não descreve apenas o que construir — ele evita construir a coisa errada."**

Este prompt garante:
- **Alinhamento** entre negócio, design e engenharia
- **Clareza** sobre o que será construído
- **Eficiência** na execução (menos retrabalho)
- **Rastreabilidade** das decisões de produto

---

## 🔄 Próximos Níveis (Evolução)

1. **PRD técnico por stack** - Templates específicos (React, Node, Python)
2. **Geração automática de épicos** - Transformar PRD em user stories
3. **Conversão PRD → Jira/Linear** - Integração com ferramentas de gestão
4. **Checklist de validação** - Verificar completude do PRD
5. **PRD iterativo** - Perguntas automáticas para refinar requisitos
6. **Estimativas automatizadas** - Story points baseados no PRD

---

## 🧠 Extensões Possíveis

### Variações do Template:

- **PRD Lean** - Versão resumida para MVPs rápidos
- **PRD Técnico** - Mais detalhes de implementação
- **PRD de Feature** - Para funcionalidades isoladas
- **PRD de Plataforma** - Para sistemas complexos

### Integrações:

- **Figma** - Link com mockups e protótipos
- **Jira/Linear** - Criação automática de tickets
- **Confluence/Notion** - Documentação centralizada
- **GitHub** - Issues e milestones sincronizados

### Automações:

```yaml
# Exemplo de workflow
1. Briefing aprovado → Trigger automático
2. LLM gera PRD via API
3. PRD publicado no Notion
4. Notificação enviada para equipe
5. Review assíncrono com comentários
6. PRD aprovado → Criação de épicos no Jira
```

---

## 💡 Dicas Práticas

### Para Melhor Qualidade do PRD:

1. **Briefing detalhado** - Quanto melhor o input, melhor o output
2. **Revisar sempre** - PRD gerado é ponto de partida, não final
3. **Envolver engenharia** - Validar viabilidade técnica cedo
4. **Iterar** - Use feedback para refinar o prompt
5. **Documentar decisões** - Adicione seção de "Decisões de Design"

### Checklist de Qualidade do PRD:

- [ ] Todos os requisitos do briefing foram traduzidos?
- [ ] Há critérios de aceitação claros?
- [ ] Requisitos estão priorizados?
- [ ] Out of Scope está explícito?
- [ ] Riscos foram identificados?
- [ ] Métricas de sucesso estão definidas?
- [ ] Dependências técnicas estão mapeadas?
- [ ] Fluxos de usuário estão descritos?

---

## 🔗 Integração com Outros Templates

Este template funciona melhor em conjunto:

```
📋 Briefing Template
    ↓
📄 PRD Template (este)
    ↓
🎯 Technical Breakdown Template
    ↓
✅ Testing Strategy Template
```

**Fluxo completo:**
1. Gere briefing com template de Briefing
2. Transforme em PRD (este template)
3. Quebre em tarefas técnicas
4. Defina estratégia de testes
5. Execute desenvolvimento

---

**Criado para transformar visão de produto em especificações executáveis com clareza e precisão.**
