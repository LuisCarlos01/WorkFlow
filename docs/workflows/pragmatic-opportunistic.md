# 🎯 Pragmatic / Opportunistic Workflow

> **"O 'dev pragmático' em estado puro."**

## 🎯 Conceito

**Pragmatic / Opportunistic Workflow** é uma abordagem onde você alterna entre diferentes técnicas e workflows conforme a situação demanda, sem seguir um processo rígido.

**Ideia central**: Não é bagunça — é **consciência situacional**.

## 🔄 Fluxo de Trabalho

```
Situação → Escolher Ferramenta Apropriada → Executar → Avaliar → Próxima Situação
```

Não há um fluxo fixo. O fluxo se adapta à situação.

## 🎨 Princípios

### 1. Consciência Situacional

Entender o contexto antes de escolher a abordagem:

```markdown
Situação: Bug crítico em produção
→ Escolha: Fix rápido + teste manual
→ Não: TDD completo + refatoração

Situação: Nova feature complexa
→ Escolha: Spec primeiro, depois código
→ Não: Código direto sem pensar

Situação: Protótipo rápido
→ Escolha: Código rápido, testar depois
→ Não: Spec completa + TDD
```

### 2. Alternância Inteligente

Alternar entre técnicas conforme necessário:

```typescript
// Feature nova → Spec primeiro
// Escrever spec em markdown

// Implementação → Código rápido primeiro
// Fazer funcionar

// Lógica crítica → TDD
// Escrever teste antes

// Refatoração → Código direto
// Melhorar sem quebrar
```

### 3. Pragmatismo sobre Dogma

```markdown
❌ Dogma: "Sempre TDD, sempre"
✅ Pragmatismo: "TDD quando faz sentido"

❌ Dogma: "Sempre spec primeiro"
✅ Pragmatismo: "Spec quando ajuda, código quando velocidade importa"

❌ Dogma: "Sempre seguir processo X"
✅ Pragmatismo: "Processo certo para situação certa"
```

## ✅ Quando Usar

- ✅ Projetos pequenos
- ✅ Solo dev
- ✅ Protótipos rápidos
- ✅ Quando contexto muda rápido
- ✅ Desenvolvedores experientes
- ✅ Quando flexibilidade é mais importante que processo

## ❌ Quando NÃO Usar

- ❌ Times grandes (precisa de alinhamento)
- ❌ Projetos críticos sem processos
- ❌ Quando consistência é essencial
- ❌ Desenvolvedores iniciantes (precisam de estrutura)

## 🎨 Padrões e Boas Práticas

### 1. Mapa Mental de Técnicas

Ter um "menu" de técnicas disponíveis:

```markdown
## Menu de Técnicas

### Para Alinhamento
- SDD (Spec-Driven Development)
- ADRs (Architecture Decision Records)

### Para Confiança
- TDD (Test-Driven Development)
- BDD (Behavior-Driven Development)

### Para Velocidade
- AI-First (Prompt-Driven)
- Prototype-First (Spike)

### Para Flexibilidade
- Iterative Development
- Pragmatic Workflow
```

### 2. Decisão Baseada em Contexto

```markdown
## Matriz de Decisão

| Situação | Técnica Recomendada |
|----------|-------------------|
| Bug crítico | Fix rápido + teste manual |
| Feature nova simples | Código direto + teste depois |
| Feature nova complexa | Spec + código + testes |
| Refatoração | Código direto (já tem testes) |
| Tecnologia nova | Spike + aprendizado |
| Lógica crítica | TDD obrigatório |
| UI/UX | Protótipo + feedback |
```

### 3. Documentar Decisões

Mesmo sendo pragmático, documente decisões importantes:

```markdown
# Decisão: Não usar TDD aqui

## Contexto
Bug crítico em produção, precisa de fix rápido.

## Decisão
Fix direto + teste manual, adicionar testes depois.

## Justificativa
Velocidade > Processo neste caso específico.
```

### 4. Balance entre Velocidade e Qualidade

```markdown
## Escala de Pragmatismo

Máxima Velocidade (Pragmático)
  ↓
  - Código direto
  - Teste manual
  - Refatorar depois
  ↓
Balance Ideal
  ↓
  - Spec quando ajuda
  - Teste quando importa
  - Refatorar quando necessário
  ↓
Máxima Qualidade (Processo)
  ↓
  - Spec sempre
  - TDD sempre
  - Refatoração contínua
```

## 📝 Exemplo Prático

### Cenário: Desenvolvedor Solo em Startup

#### Situação 1: MVP Rápido

```typescript
// Objetivo: Validar ideia rápido
// Abordagem: Código direto, sem testes, sem spec

// Implementar feature básica
function quickFeature() {
  // Código funcional, não perfeito
  // Testar manualmente
  // Iterar baseado em feedback
}
```

#### Situação 2: Feature Crítica

```typescript
// Objetivo: Pagamento - precisa funcionar
// Abordagem: Spec + TDD + revisão

// 1. Escrever spec
// 2. Escrever testes
// 3. Implementar
// 4. Revisar cuidadosamente
```

#### Situação 3: Integração Nova

```typescript
// Objetivo: Integrar com API externa
// Abordagem: Spike primeiro

// 1. Criar spike rápido
// 2. Testar integração
// 3. Decidir se prossegue
// 4. Implementar se viável
```

#### Situação 4: Refatoração

```typescript
// Objetivo: Melhorar código existente
// Abordagem: Refatoração incremental

// 1. Identificar problema
// 2. Refatorar pequena parte
// 3. Testar que ainda funciona
// 4. Repetir
```

## 🎯 Princípios de Decisão

### 1. Criticidade

```
Crítico → Processo rigoroso
Normal → Processo balanceado
Baixo → Processo rápido
```

### 2. Complexidade

```
Complexo → Spec + TDD
Médio → Spec ou TDD
Simples → Código direto
```

### 3. Urgência

```
Urgente → Fix rápido
Normal → Processo normal
Baixa → Processo completo
```

### 4. Risco

```
Alto Risco → Spike + Spec + TDD
Médio Risco → Spec ou TDD
Baixo Risco → Código direto
```

## ⚠️ Armadilhas Comuns

### 1. Pragmatismo = Bagunça

```typescript
// ❌ Ruim: Sem critério, tudo bagunçado
// Código sem padrão, sem testes, sem documentação

// ✅ Bom: Pragmático mas consciente
// Escolher técnica apropriada para cada situação
```

### 2. Nunca Usar Processos

```markdown
# ❌ Ruim: Nunca usar TDD, nunca escrever specs
# "Sou pragmático, não preciso de processos"

# ✅ Bom: Usar processos quando faz sentido
# "TDD para lógica crítica, código direto para protótipos"
```

### 3. Falta de Consistência

```typescript
// ❌ Ruim: Cada arquivo com padrão diferente
// Alguns com testes, outros sem
// Alguns com validação, outros sem

// ✅ Bom: Consistência dentro do contexto
// Features críticas: sempre testes
// Protótipos: testes opcionais
```

## 🔗 Integração com Outros Workflows

O Pragmatic Workflow **integra** todos os outros:

```
Pragmatic Workflow
  ├── Usa SDD quando precisa alinhar
  ├── Usa TDD quando precisa confiança
  ├── Usa BDD quando precisa comunicação
  ├── Usa AI-First quando precisa velocidade
  ├── Usa Spike quando precisa explorar
  └── Usa Iterative quando precisa feedback
```

## 📚 Recursos Relacionados

- [Pragmatic Programmer](https://pragprog.com/titles/tpp20/the-pragmatic-programmer-20th-anniversary-edition/)
- [All Workflows](./work-flows.md)

## 🚀 Próximos Passos

1. Desenvolva consciência situacional
2. Crie seu "menu" de técnicas
3. Pratique alternância inteligente
4. Documente decisões importantes
5. Ajuste baseado em resultados

---

**Comando Few-Shot**: Use `/few-shot-pragmatic` para aplicar este workflow
