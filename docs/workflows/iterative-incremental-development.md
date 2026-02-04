# 🔄 Iterative / Incremental Development

> **"Construir em fatias verticais, não tudo de uma vez."**

## 🎯 Conceito

**Iterative / Incremental Development** é uma abordagem onde você constrói o software em **fatias verticais** (iterações), cada uma entregando valor e recebendo feedback antes da próxima.

**Ideia central**: Versão mínima → Feedback → Ajuste → Repetir

## 🔄 Fluxo de Trabalho

```
1. Planejar Iteração (o que fazer agora)
   ↓
2. Implementar Versão Mínima Funcional
   ↓
3. Entregar e Coletar Feedback
   ↓
4. Ajustar Baseado no Feedback
   ↓
5. Repetir para Próxima Iteração
```

## 📊 Modelo Iterativo vs Tradicional

### Desenvolvimento Tradicional (Waterfall)

```
Análise → Design → Implementação → Teste → Deploy
  (tudo)    (tudo)      (tudo)        (tudo)    (tudo)
```

**Problema**: Feedback só no final

### Desenvolvimento Iterativo

```
Iteração 1: Login básico → Feedback → Ajuste
Iteração 2: Login + Perfil → Feedback → Ajuste
Iteração 3: Login + Perfil + Pedidos → Feedback → Ajuste
```

**Vantagem**: Feedback constante

## ✅ Quando Usar

- ✅ Produtos em validação
- ✅ MVPs (Minimum Viable Products)
- ✅ Startups
- ✅ Quando feedback rápido é crítico
- ✅ Produtos com requisitos incertos
- ✅ Quando aprendizado é importante

## ❌ Quando NÃO Usar

- ❌ Projetos com requisitos muito fixos
- ❌ Quando especificação completa é obrigatória
- ❌ Sistemas críticos que não podem mudar
- ❌ Quando "perfeito" é mais importante que "rápido"

## 🎨 Padrões e Boas Práticas

### 1. Fatias Verticais, Não Horizontais

```typescript
// ❌ Ruim: Fatia horizontal (toda camada de uma vez)
// Iteração 1: Todos os models
// Iteração 2: Todos os controllers
// Iteração 3: Todas as views

// ✅ Bom: Fatia vertical (feature completa)
// Iteração 1: Login completo (model + controller + view)
// Iteração 2: Perfil completo (model + controller + view)
// Iteração 3: Pedidos completo (model + controller + view)
```

### 2. MVP em Cada Iteração

Cada iteração deve entregar um **MVP** (Minimum Viable Product) daquela funcionalidade:

```typescript
// Iteração 1: Login MVP
// - Email + senha
// - Validação básica
// - Sem recuperação de senha (próxima iteração)

// Iteração 2: Login Melhorado
// - Adiciona recuperação de senha
// - Adiciona "lembrar-me"
// - Melhora UX
```

### 3. Feedback Loop Curto

```
Implementar (1-2 semanas)
  ↓
Entregar
  ↓
Coletar Feedback (dias)
  ↓
Ajustar (baseado no feedback)
  ↓
Próxima Iteração
```

### 4. Priorizar por Valor

Use uma matriz de priorização:

```
Alto Valor + Baixo Esforço → Fazer Primeiro
Alto Valor + Alto Esforço → Planejar
Baixo Valor + Baixo Esforço → Fazer Depois
Baixo Valor + Alto Esforço → Não Fazer
```

## 📝 Exemplo Prático

### Produto: E-commerce

#### Iteração 1: MVP de Autenticação

**Objetivo**: Usuário pode fazer login

**Entregas**:
- ✅ Página de login
- ✅ Validação básica
- ✅ Autenticação simples

**Feedback Coletado**:
- "Preciso recuperar senha"
- "Quero fazer login com Google"

#### Iteração 2: Autenticação Melhorada

**Objetivo**: Melhorar experiência de login

**Entregas**:
- ✅ Recuperação de senha
- ✅ Login com Google (OAuth)
- ✅ Melhorias de UX

**Feedback Coletado**:
- "Quero ver meu perfil"

#### Iteração 3: Perfil de Usuário

**Objetivo**: Usuário pode gerenciar perfil

**Entregas**:
- ✅ Visualizar perfil
- ✅ Editar informações
- ✅ Upload de foto

**E assim por diante...**

## 🎯 Técnicas de Planejamento

### 1. User Stories

```
Como [tipo de usuário]
Eu quero [ação]
Para [benefício]

Critérios de Aceitação:
- [ ] Critério 1
- [ ] Critério 2
```

**Exemplo**:
```
Como cliente
Eu quero fazer login
Para acessar minha conta

Critérios de Aceitação:
- [ ] Posso fazer login com email e senha
- [ ] Vejo mensagem de erro se credenciais inválidas
- [ ] Sou redirecionado após login bem-sucedido
```

### 2. Sprints (Scrum)

- **Duração**: 1-4 semanas
- **Objetivo**: Entregar incremento de valor
- **Cerimônias**: Planning, Daily, Review, Retrospective

### 3. Kanban

- **Foco**: Fluxo contínuo
- **Limite**: WIP (Work In Progress)
- **Objetivo**: Reduzir tempo de ciclo

## 🔄 Ciclo de Iteração

### Fase 1: Planejamento

- Definir objetivo da iteração
- Priorizar features
- Estimar esforço
- Definir critérios de sucesso

### Fase 2: Implementação

- Desenvolver features
- Testar continuamente
- Integrar frequentemente
- Documentar mudanças

### Fase 3: Entrega

- Deploy em ambiente de teste/staging
- Demo para stakeholders
- Coletar feedback
- Documentar aprendizados

### Fase 4: Ajuste

- Analisar feedback
- Decidir o que ajustar
- Priorizar próxima iteração
- Repetir ciclo

## 📊 Métricas Importantes

### 1. Velocidade de Entrega

- Tempo entre início e entrega de feature
- Objetivo: Reduzir continuamente

### 2. Taxa de Feedback

- Quantidade de feedback coletado
- Objetivo: Maximizar feedback útil

### 3. Taxa de Ajuste

- Quantas vezes ajustamos baseado em feedback
- Objetivo: Ajustar rapidamente

### 4. Valor Entregue

- Valor de negócio entregue por iteração
- Objetivo: Maximizar valor

## ⚠️ Armadilhas Comuns

### 1. Iterações Muito Longas

```
# ❌ Ruim: Iteração de 3 meses
Iteração 1: Sistema completo (3 meses)

# ✅ Bom: Iterações curtas
Iteração 1: Login (1 semana)
Iteração 2: Perfil (1 semana)
Iteração 3: Pedidos (1 semana)
```

### 2. Ignorar Feedback

```
# ❌ Ruim: Coletar feedback mas não usar
Feedback: "Preciso de recuperação de senha"
Ação: Ignorar e seguir para próxima feature

# ✅ Bom: Usar feedback para priorizar
Feedback: "Preciso de recuperação de senha"
Ação: Adicionar à próxima iteração
```

### 3. Fatias Horizontais

```
# ❌ Ruim: Fazer toda camada de uma vez
Iteração 1: Todos os models
Iteração 2: Todos os controllers

# ✅ Bom: Fazer feature completa
Iteração 1: Login (model + controller + view)
```

## 🔗 Integração com Outros Workflows

### Iterative + SDD
- Escrever spec para cada iteração
- Especs evoluem com feedback

### Iterative + TDD
- Testes garantem qualidade em cada iteração
- Refatoração contínua

### Iterative + AI-First
- IA acelera implementação de cada iteração
- Feedback rápido permite ajustes rápidos

## 📚 Recursos Relacionados

- [Agile Manifesto](https://agilemanifesto.org/)
- [Scrum Guide](https://scrumguides.org/)
- [Lean Startup](https://theleanstartup.com/)

## 🚀 Próximos Passos

1. Defina objetivo da primeira iteração
2. Priorize features por valor
3. Implemente MVP
4. Colete feedback
5. Ajuste e repita

---

**Comando Few-Shot**: Use `/few-shot-iterative` para aplicar este workflow
