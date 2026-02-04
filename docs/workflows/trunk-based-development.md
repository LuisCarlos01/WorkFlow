# 🌳 Trunk-Based Development

> **"Workflow de branching, não de escrita."**

## 🎯 Conceito

**Trunk-Based Development** é uma estratégia de branching onde o foco está em manter o código principal (`main`/`trunk`) sempre estável e deployável, com commits pequenos e frequentes.

**Ideia central**: Poucas branches, commits pequenos, integração contínua real.

## 🔄 Fluxo de Trabalho

```
1. Criar branch curta (opcional, < 1 dia)
   ↓
2. Fazer commits pequenos e frequentes
   ↓
3. Integrar com main rapidamente
   ↓
4. Deploy contínuo
```

## 🌿 Estrutura de Branches

### Modelo Simplificado

```
main (trunk)
  ├── feature/login (curta, < 1 dia)
  ├── feature/checkout (curta, < 1 dia)
  └── hotfix/critical-bug (curta, < 1 dia)
```

### Regras de Ouro

- ✅ Branches devem viver **menos de 1 dia**
- ✅ Commits pequenos e frequentes
- ✅ `main` sempre estável e deployável
- ✅ Feature flags para features incompletas

## ✅ Quando Usar

- ✅ Times maduros e experientes
- ✅ Deploy contínuo (CI/CD)
- ✅ Produtos vivos e em produção
- ✅ Quando velocidade de integração é crítica
- ✅ Times pequenos/médios (< 10 devs)

## ❌ Quando NÃO Usar

- ❌ Times muito grandes sem feature flags
- ❌ Quando releases são raras
- ❌ Projetos com muitos desenvolvedores iniciantes
- ❌ Quando estabilidade é mais importante que velocidade

## 🎨 Padrões e Boas Práticas

### 1. Commits Pequenos e Frequentes

```bash
# ❌ Ruim: Commit gigante
git commit -m "feat: adiciona sistema completo de autenticacao"

# ✅ Bom: Commits pequenos
git commit -m "feat: adiciona validacao de email"
git commit -m "feat: adiciona hash de senha"
git commit -m "feat: adiciona endpoint de login"
```

### 2. Branches Curta Vida

```bash
# Criar branch pela manhã
git checkout -b feature/user-profile

# Trabalhar algumas horas
# Fazer commits pequenos
git commit -m "feat: adiciona campo nome"
git commit -m "feat: adiciona campo email"

# Integrar antes do fim do dia
git checkout main
git merge feature/user-profile
```

### 3. Feature Flags para Features Incompletas

```typescript
// Usar feature flags para features em desenvolvimento
if (featureFlags.isEnabled('new-checkout')) {
  return <NewCheckout />;
}
return <OldCheckout />;
```

### 4. CI/CD Contínuo

- Testes automáticos em cada commit
- Deploy automático quando testes passam
- Rollback automático se algo falhar

## 🛠️ Estratégias de Implementação

### Estratégia 1: Commits Diretos no Main

Para times muito pequenos e maduros:

```bash
# Trabalhar diretamente no main
git checkout main
git pull
# Fazer mudanças
git commit -m "feat: adiciona validacao"
git push
```

**Vantagens**: Máxima simplicidade  
**Desvantagens**: Requer disciplina absoluta

### Estratégia 2: Branches Curta Vida

Para a maioria dos times:

```bash
# Criar branch curta
git checkout -b feature/quick-fix
# Trabalhar
git commit -m "fix: corrige bug de validacao"
# Integrar rapidamente
git checkout main
git merge feature/quick-fix
git branch -d feature/quick-fix
```

**Vantagens**: Balance entre segurança e velocidade  
**Desvantagens**: Ainda há merge overhead

### Estratégia 3: Feature Flags + Main

Para features maiores:

```bash
# Trabalhar no main com feature flag desabilitada
git checkout main
# Implementar feature completa
git commit -m "feat: adiciona novo checkout (feature flag)"
# Habilitar gradualmente
featureFlags.enable('new-checkout', percentage: 10);
```

**Vantagens**: Features grandes sem branches longas  
**Desvantagens**: Requer infraestrutura de feature flags

## 📊 Comparação com GitFlow

### GitFlow (Tradicional)

```
main
  └── develop
      ├── feature/login (longa, semanas)
      ├── feature/checkout (longa, semanas)
      └── release/v1.0 (longa, semanas)
```

**Problemas**:
- Branches longas
- Muitos merges complexos
- Deploy raro

### Trunk-Based

```
main
  ├── feature/login (curta, horas)
  └── feature/checkout (curta, horas)
```

**Vantagens**:
- Branches curtas
- Merges simples
- Deploy frequente

## 🎯 Feature Flags

Feature flags são essenciais para Trunk-Based Development:

```typescript
// Exemplo de feature flag
const featureFlags = {
  newCheckout: process.env.ENABLE_NEW_CHECKOUT === 'true',
  darkMode: process.env.ENABLE_DARK_MODE === 'true',
};

// Uso no código
if (featureFlags.newCheckout) {
  return <NewCheckoutFlow />;
}
return <OldCheckoutFlow />;
```

### Benefícios

- ✅ Deploy código incompleto com segurança
- ✅ Rollback instantâneo
- ✅ Teste A/B
- ✅ Release gradual

## 🔄 CI/CD Pipeline

### Pipeline Ideal

```
1. Commit no main
   ↓
2. Testes automáticos (unitários, integração)
   ↓
3. Build da aplicação
   ↓
4. Deploy automático em staging
   ↓
5. Testes E2E em staging
   ↓
6. Deploy automático em produção (se tudo OK)
   ↓
7. Monitoramento e alertas
```

### Exemplo GitHub Actions

```yaml
name: CI/CD Pipeline

on:
  push:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - run: npm test
      - run: npm run lint

  deploy:
    needs: test
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - run: npm run build
      - run: npm run deploy
```

## ⚠️ Armadilhas Comuns

### 1. Branches Longas

```bash
# ❌ Ruim: Branch vive por semanas
git checkout -b feature/mega-feature
# ... semanas depois ...
git merge feature/mega-feature

# ✅ Bom: Dividir em branches menores
git checkout -b feature/part-1
# ... horas depois ...
git merge feature/part-1
```

### 2. Commits Gigantes

```bash
# ❌ Ruim: Um commit com tudo
git commit -m "feat: sistema completo"

# ✅ Bom: Commits pequenos e focados
git commit -m "feat: adiciona validacao"
git commit -m "feat: adiciona endpoint"
git commit -m "test: adiciona testes"
```

### 3. Main Instável

```bash
# ❌ Ruim: Commitar código quebrado
git commit -m "WIP: ainda quebrado"
git push

# ✅ Bom: Só commitar código funcional
# Usar feature flags se necessário
git commit -m "feat: adiciona feature (flag desabilitada)"
```

## 🔗 Integração com Outros Workflows

### Trunk-Based + TDD
- Testes garantem que main sempre funciona
- TDD facilita commits pequenos

### Trunk-Based + CI/CD
- Deploy contínuo requer main estável
- Trunk-Based facilita deploy contínuo

## 📚 Recursos Relacionados

- [GitFlow vs Trunk-Based](https://trunkbaseddevelopment.com/)
- [Feature Flags Guide](https://featureflags.io/)

## 🚀 Próximos Passos

1. Configure CI/CD pipeline
2. Implemente feature flags
3. Treine time em commits pequenos
4. Reduza tempo de vida das branches
5. Monitore estabilidade do main

---

**Comando Few-Shot**: Use `/few-shot-trunk` para aplicar este workflow
