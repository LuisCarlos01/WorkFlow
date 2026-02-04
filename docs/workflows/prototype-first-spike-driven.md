# 🔬 Prototype-First / Spike-Driven Development

> **"Não se comprometa com o código."**

## 🎯 Conceito

**Prototype-First / Spike-Driven Development** é uma abordagem onde você explora tecnologias, APIs, performance e viabilidade técnica **antes** de se comprometer com uma solução.

**Ideia central**: Exploração → Aprendizado → Decisão → Implementação (ou descarte)

## 🔄 Fluxo de Trabalho

```
1. Identificar Risco/Incerteza Técnica
   ↓
2. Criar Protótipo/Spike Rápido
   ↓
3. Explorar e Aprender
   ↓
4. Decidir: Prosseguir ou Descarte
   ↓
5. Implementar Solução ou Tentar Alternativa
```

## 🎨 Tipos de Spikes

### 1. Technical Spike

Explorar viabilidade técnica de uma solução.

**Exemplo**: "Será que conseguimos integrar com essa API em tempo hábil?"

```typescript
// spike/api-integration.ts
// Protótipo rápido para testar integração
async function testAPIIntegration() {
  try {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    console.log('API funciona!', data);
    return { success: true, latency: Date.now() - start };
  } catch (error) {
    return { success: false, error: error.message };
  }
}
```

### 2. Performance Spike

Testar performance de uma abordagem.

**Exemplo**: "Essa biblioteca consegue processar 1M de registros?"

```typescript
// spike/performance-test.ts
const start = Date.now();
for (let i = 0; i < 1000000; i++) {
  processRecord(data[i]);
}
const duration = Date.now() - start;
console.log(`Processou 1M em ${duration}ms`);
```

### 3. Architecture Spike

Validar decisão arquitetural.

**Exemplo**: "Microserviços ou monólito para este caso?"

```typescript
// spike/microservices-vs-monolith.ts
// Protótipo de ambos para comparar
```

### 4. Technology Spike

Avaliar nova tecnologia.

**Exemplo**: "Vale a pena migrar para essa nova biblioteca?"

## ✅ Quando Usar

- ✅ Tecnologia nova ou desconhecida
- ✅ Alto risco técnico
- ✅ Decisões arquiteturais importantes
- ✅ Validação de conceito (POC)
- ✅ Quando há múltiplas opções viáveis
- ✅ Antes de comprometer com solução cara

## ❌ Quando NÃO Usar

- ❌ Quando já conhecemos bem a tecnologia
- ❌ Quando risco é baixo
- ❌ Quando tempo é crítico e não há alternativas
- ❌ Para features simples e diretas

## 🎨 Padrões e Boas Práticas

### 1. Timebox Spikes

Defina tempo limite para exploração:

```markdown
Spike: Integração com API X
Tempo: 4 horas
Objetivo: Validar se API funciona e se integração é viável
```

### 2. Documentar Aprendizados

Sempre documente o que aprendeu:

```markdown
# Spike: Integração com API X

## Objetivo
Validar viabilidade de integração

## O que testamos
- Autenticação OAuth2
- Rate limits
- Formato de dados

## Resultados
- ✅ Autenticação funciona
- ⚠️ Rate limit muito restritivo (100 req/hora)
- ✅ Formato de dados compatível

## Decisão
Prosseguir, mas implementar cache agressivo devido ao rate limit
```

### 3. Código Descartável

Spikes devem ser **descartáveis**:

```typescript
// spike/exploration.ts
// ⚠️ CÓDIGO DESCARTÁVEL - NÃO USAR EM PRODUÇÃO
// Este é apenas um teste rápido

// Código sujo, sem tratamento de erro, sem testes
// Objetivo: Aprender rápido, não código perfeito
```

### 4. Focar no Essencial

Teste apenas o que precisa validar:

```typescript
// ❌ Ruim: Implementar tudo
function fullImplementation() {
  // Autenticação completa
  // Validação completa
  // Tratamento de erro completo
  // Logging completo
  // ...
}

// ✅ Bom: Focar no essencial
function spike() {
  // Apenas testar se API responde
  const response = await fetch(apiUrl);
  return response.ok;
}
```

## 📝 Exemplo Prático Completo

### Cenário: Escolher Biblioteca de Gráficos

#### 1. Identificar Incerteza

```
Precisamos de gráficos interativos.
Opções: Chart.js, D3.js, Recharts, Victory
Qual escolher?
```

#### 2. Criar Spikes

```typescript
// spike/chart-libraries.ts

// Spike 1: Chart.js
async function testChartJS() {
  const chart = new Chart(ctx, {
    type: 'line',
    data: { /* ... */ },
  });
  // Testar performance, customização, etc.
}

// Spike 2: D3.js
async function testD3() {
  const svg = d3.select('svg');
  // Testar flexibilidade, curva de aprendizado, etc.
}

// Spike 3: Recharts
async function testRecharts() {
  <LineChart data={data}>
    <Line dataKey="value" />
  </LineChart>
  // Testar facilidade, React integration, etc.
}
```

#### 3. Documentar Resultados

```markdown
# Spike: Biblioteca de Gráficos

## Testes Realizados

### Chart.js
- ✅ Fácil de usar
- ✅ Boa performance
- ❌ Customização limitada

### D3.js
- ✅ Máxima flexibilidade
- ❌ Curva de aprendizado alta
- ❌ Mais código necessário

### Recharts
- ✅ Integração perfeita com React
- ✅ API declarativa
- ✅ Boa performance
- ✅ Customização suficiente

## Decisão
Usar Recharts - melhor balance entre facilidade e flexibilidade
```

#### 4. Implementar Solução Escolhida

```typescript
// Agora implementar com Recharts, sabendo que funciona
import { LineChart, Line } from 'recharts';

export function SalesChart({ data }) {
  return (
    <LineChart data={data}>
      <Line dataKey="sales" />
    </LineChart>
  );
}
```

## 🎯 Estrutura de Pastas para Spikes

```
spikes/
├── api-integration/
│   ├── README.md (documentação do spike)
│   ├── test-api.ts
│   └── results.md
├── performance-test/
│   ├── README.md
│   ├── benchmark.ts
│   └── results.md
└── architecture-poc/
    ├── README.md
    ├── microservices-poc/
    └── monolith-poc/
```

## ⚠️ Armadilhas Comuns

### 1. Spike Vira Implementação

```typescript
// ❌ Ruim: Usar código de spike em produção
// spike/quick-test.ts
export function productionCode() {
  // Código sujo do spike
}

// ✅ Bom: Reimplementar após spike
// src/production-code.ts
export function productionCode() {
  // Código limpo baseado no aprendizado do spike
}
```

### 2. Spikes Muito Longos

```markdown
# ❌ Ruim: Spike de 2 semanas
Spike: Explorar framework X
Tempo: 2 semanas

# ✅ Bom: Spike timeboxed
Spike: Explorar framework X
Tempo: 4 horas
```

### 3. Não Documentar Resultados

```markdown
# ❌ Ruim: Fazer spike mas não documentar
# Time esquece o que foi aprendido

# ✅ Bom: Documentar sempre
# README.md com objetivo, resultados, decisão
```

## 🔗 Integração com Outros Workflows

### Spike + SDD
- Spike valida decisões técnicas
- SDD documenta decisões arquiteturais

### Spike + TDD
- Spike explora viabilidade
- TDD garante qualidade na implementação

### Spike + Iterative
- Spike em cada iteração para novas tecnologias
- Aprendizado contínuo

## 📚 Recursos Relacionados

- [Spike Definition (Scrum)](https://www.scrum.org/resources/what-is-a-spike)
- [Technical Debt](https://martinfowler.com/bliki/TechnicalDebt.html)

## 🚀 Próximos Passos

1. Identifique incerteza técnica
2. Defina objetivo e timebox do spike
3. Crie protótipo rápido
4. Documente aprendizados
5. Tome decisão baseada em resultados

---

**Comando Few-Shot**: Use `/few-shot-spike` para aplicar este workflow
