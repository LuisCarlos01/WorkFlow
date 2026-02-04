# 🧪 Test-Driven Development (TDD)

> **"O código nasce quebrando."**

## 🎯 Conceito

**Test-Driven Development (TDD)** é uma abordagem onde você escreve o teste **antes** de escrever o código.

O teste é a spec executável.

## 🔄 Fluxo de Trabalho (Red-Green-Refactor)

```
1. 🔴 RED: Escrever teste que falha
   ↓
2. 🟢 GREEN: Escrever código mínimo para passar
   ↓
3. 🔵 REFACTOR: Melhorar código mantendo testes passando
   ↓
4. Repetir para próxima funcionalidade
```

## 📝 Exemplo Prático

### Passo 1: Escrever Teste (RED)

```typescript
// user.test.ts
import { validateEmail } from './user';

describe('validateEmail', () => {
  it('should return true for valid email', () => {
    expect(validateEmail('user@example.com')).toBe(true);
  });

  it('should return false for invalid email', () => {
    expect(validateEmail('invalid-email')).toBe(false);
  });
});
```

**Resultado**: Teste falha (função não existe)

### Passo 2: Escrever Código Mínimo (GREEN)

```typescript
// user.ts
export function validateEmail(email: string): boolean {
  return email.includes('@');
}
```

**Resultado**: Testes passam (mas código é simples)

### Passo 3: Refatorar (REFACTOR)

```typescript
// user.ts
export function validateEmail(email: string): boolean {
  const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  return emailRegex.test(email);
}
```

**Resultado**: Código melhorado, testes ainda passam

## ✅ Quando Usar

- ✅ Backends e APIs
- ✅ Regras de negócio complexas
- ✅ Bibliotecas e utilitários
- ✅ Código crítico (segurança, financeiro)
- ✅ Quando confiança é essencial
- ✅ Refatoração de código legado

## ❌ Quando NÃO Usar

- ❌ Protótipos muito rápidos
- ❌ UI/UX (testes são mais difíceis)
- ❌ Quando velocidade inicial é crítica
- ❌ Código que muda constantemente

## 🎨 Padrões e Boas Práticas

### 1. Teste Primeiro, Sempre

- Escreva o teste antes do código
- Veja o teste falhar (importante!)
- Escreva código mínimo para passar

### 2. Mantenha Testes Simples

- Um teste, uma coisa
- Testes devem ser legíveis
- Use nomes descritivos

### 3. Use AAA Pattern

```typescript
it('should calculate total price correctly', () => {
  // Arrange (Preparar)
  const items = [
    { price: 10, quantity: 2 },
    { price: 5, quantity: 3 },
  ];

  // Act (Agir)
  const total = calculateTotal(items);

  // Assert (Afirmar)
  expect(total).toBe(35);
});
```

### 4. Teste Comportamento, Não Implementação

```typescript
// ❌ Ruim: Testa implementação
expect(calculator.add).toHaveBeenCalled();

// ✅ Bom: Testa comportamento
expect(result).toBe(5);
```

### 5. Mantenha Testes Rápidos

- Testes unitários devem ser rápidos
- Evite I/O em testes unitários
- Use mocks para dependências externas

## 🛠️ Ferramentas Comuns

### JavaScript/TypeScript
- Jest
- Vitest
- Mocha + Chai

### Python
- pytest
- unittest

### Java
- JUnit
- TestNG

### C#
- xUnit
- NUnit

## 📊 Tipos de Testes

### Testes Unitários
Testam unidades isoladas de código.

```typescript
describe('calculateTotal', () => {
  it('should sum all items', () => {
    expect(calculateTotal([1, 2, 3])).toBe(6);
  });
});
```

### Testes de Integração
Testam interação entre componentes.

```typescript
describe('UserService', () => {
  it('should create user and send welcome email', async () => {
    const user = await userService.create({ email: 'test@example.com' });
    expect(emailService.send).toHaveBeenCalled();
  });
});
```

### Testes End-to-End
Testam fluxo completo do sistema.

```typescript
describe('User Registration Flow', () => {
  it('should register new user', async () => {
    await page.goto('/register');
    await page.fill('#email', 'test@example.com');
    await page.click('button[type="submit"]');
    await expect(page.locator('.success')).toBeVisible();
  });
});
```

## 🎯 Pirâmide de Testes

```
        /\
       /E2E\        Poucos, lentos, caros
      /------\
     /Integração\   Alguns, médios
    /------------\
   /  Unitários   \  Muitos, rápidos, baratos
  /----------------\
```

**Regra**: Muitos testes unitários, alguns de integração, poucos E2E.

## ⚠️ Armadilhas Comuns

### 1. Testes de Implementação

```typescript
// ❌ Ruim: Testa como faz, não o que faz
expect(service.privateMethod).toHaveBeenCalled();

// ✅ Bom: Testa resultado
expect(result).toBe(expectedValue);
```

### 2. Testes Frágeis

```typescript
// ❌ Ruim: Depende de ordem ou estado global
let counter = 0;
function test() {
  counter++;
  expect(counter).toBe(1);
}

// ✅ Bom: Isolado e independente
function test() {
  const result = calculate();
  expect(result).toBe(expected);
}
```

### 3. Cobertura ≠ Qualidade

- 100% de cobertura não garante qualidade
- Foque em testes significativos
- Teste casos de erro também

## 🔗 Integração com Outros Workflows

### TDD + SDD
1. Escreva spec (SDD)
2. Escreva testes baseados na spec (TDD)
3. Implemente código

### TDD + BDD
- TDD para código
- BDD para comportamento do sistema
- Ambos se complementam

## 📚 Recursos Relacionados

- [BDD Workflow](./behavior-driven-development.md)
- [SDD Workflow](./spec-driven-development.md)

## 🚀 Próximos Passos

1. Escolha uma função para implementar
2. Escreva o teste primeiro
3. Veja o teste falhar
4. Escreva código mínimo
5. Refatore

---

**Comando Few-Shot**: Use `/few-shot-tdd` para aplicar este workflow
