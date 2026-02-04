# 🎭 Behavior-Driven Development (BDD)

> **"Um primo mais 'humano' do TDD."**

## 🎯 Conceito

**Behavior-Driven Development (BDD)** é uma abordagem onde a spec é escrita em **linguagem quase natural**, focando no comportamento do sistema do ponto de vista do usuário.

## 🔄 Fluxo de Trabalho

```
1. Escrever Cenário em Linguagem Natural (Gherkin)
   ↓
2. Gerar Testes Automatizados
   ↓
3. Implementar Código para Passar nos Testes
   ↓
4. Validar Comportamento Esperado
```

## 📝 Sintaxe Gherkin

BDD usa **Gherkin**, uma linguagem estruturada em português (ou inglês):

```gherkin
Funcionalidade: Login de usuário
  Como um usuário
  Eu quero fazer login no sistema
  Para acessar minhas informações

  Cenário: Login bem-sucedido
    Dado que estou na página de login
    Quando eu preencho "user@example.com" no campo email
    E preencho "senha123" no campo senha
    E clico no botão "Entrar"
    Então eu devo ser redirecionado para a página inicial
    E devo ver a mensagem "Bem-vindo, User!"

  Cenário: Login com credenciais inválidas
    Dado que estou na página de login
    Quando eu preencho "wrong@example.com" no campo email
    E preencho "wrongpass" no campo senha
    E clico no botão "Entrar"
    Então eu devo ver a mensagem "Credenciais inválidas"
    E devo permanecer na página de login
```

## 🎨 Estrutura de um Cenário

### Palavras-Chave

- **Funcionalidade**: Descreve o que está sendo testado
- **Cenário**: Um caso de teste específico
- **Dado**: Pré-condições (estado inicial)
- **Quando**: Ação do usuário
- **Então**: Resultado esperado
- **E**: Conectivo para múltiplas condições/ações

### Exemplo Completo

```gherkin
Funcionalidade: Processamento de pedidos

  Cenário: Criar pedido com sucesso
    Dado que sou um cliente autenticado
    E tenho produtos no carrinho
    Quando eu confirmo o pedido
    E o pagamento é aprovado
    Então o pedido deve ser criado
    E o status deve ser "confirmado"
    E um email de confirmação deve ser enviado
```

## ✅ Quando Usar

- ✅ Times multidisciplinares (dev, QA, produto)
- ✅ Produtos com regras claras de negócio
- ✅ Quando produto precisa entender o código
- ✅ Aplicações com muitos fluxos de usuário
- ✅ Quando comunicação é crítica

## ❌ Quando NÃO Usar

- ❌ Código muito técnico/baixo nível
- ❌ Quando velocidade é mais importante que clareza
- ❌ Projetos muito pequenos
- ❌ Quando time não está familiarizado com BDD

## 🛠️ Ferramentas Comuns

### JavaScript/TypeScript
- **Cucumber.js** - Framework BDD
- **Jest-Cucumber** - Integração com Jest

### Python
- **Behave** - Framework BDD
- **Pytest-BDD** - Plugin para pytest

### Java
- **Cucumber** - Framework BDD
- **JBehave** - Alternativa ao Cucumber

### .NET
- **SpecFlow** - Framework BDD para .NET

## 📝 Exemplo Prático Completo

### 1. Arquivo de Feature (.feature)

```gherkin
# features/login.feature
Funcionalidade: Autenticação de usuário

  Cenário: Login bem-sucedido
    Dado que o usuário "admin@example.com" existe com senha "admin123"
    Quando eu faço login com "admin@example.com" e "admin123"
    Então eu devo estar autenticado
    E devo ver a mensagem "Bem-vindo!"
```

### 2. Step Definitions (Implementação)

```typescript
// features/step_definitions/login.steps.ts
import { Given, When, Then } from '@cucumber/cucumber';
import { expect } from 'chai';
import { login, isAuthenticated } from '../support/auth';

Given('que o usuário {string} existe com senha {string}', 
  async (email: string, password: string) => {
    // Criar usuário no banco de dados de teste
    await createUser({ email, password });
  }
);

When('eu faço login com {string} e {string}', 
  async (email: string, password: string) => {
    await login(email, password);
  }
);

Then('eu devo estar autenticado', async () => {
  expect(isAuthenticated()).to.be.true;
});

Then('devo ver a mensagem {string}', async (message: string) => {
  const actualMessage = getWelcomeMessage();
  expect(actualMessage).to.equal(message);
});
```

## 🎨 Padrões e Boas Práticas

### 1. Escreva em Linguagem de Negócio

```gherkin
# ❌ Ruim: Muito técnico
Dado que o endpoint POST /api/users retorna 201

# ✅ Bom: Linguagem de negócio
Dado que um novo usuário foi cadastrado
```

### 2. Seja Específico, mas Não Detalhado

```gherkin
# ❌ Ruim: Muito detalhado
Quando eu clico no botão com id "submit-btn" que está na div com class "form-container"

# ✅ Bom: Foco no comportamento
Quando eu confirmo o formulário
```

### 3. Um Cenário, Um Comportamento

```gherkin
# ❌ Ruim: Múltiplos comportamentos
Cenário: Login completo
  Dado que faço login
  E crio um pedido
  E faço checkout
  E vejo o histórico

# ✅ Bom: Um comportamento por cenário
Cenário: Login bem-sucedido
  Dado que faço login
  Então devo estar autenticado

Cenário: Criar pedido
  Dado que estou autenticado
  Quando crio um pedido
  Então o pedido deve ser criado
```

### 4. Use Background para Pré-condições Comuns

```gherkin
Funcionalidade: Gerenciamento de pedidos

  Background:
    Dado que estou autenticado como "admin@example.com"
    E tenho produtos disponíveis

  Cenário: Criar pedido
    Quando eu crio um pedido
    Então o pedido deve ser criado

  Cenário: Listar pedidos
    Quando eu acesso a lista de pedidos
    Então devo ver meus pedidos
```

## 🔗 Integração com Outros Workflows

### BDD + TDD
- **BDD**: Testes de comportamento do sistema
- **TDD**: Testes unitários de código
- Ambos se complementam

### BDD + SDD
- **BDD**: Especifica comportamento em linguagem natural
- **SDD**: Documenta arquitetura e decisões técnicas
- BDD pode ser parte da spec

## 📊 Estrutura de Pastas Recomendada

```
features/
├── login/
│   ├── login.feature
│   └── step_definitions/
│       └── login.steps.ts
├── checkout/
│   ├── checkout.feature
│   └── step_definitions/
│       └── checkout.steps.ts
└── support/
    ├── auth.ts
    └── database.ts
```

## ⚠️ Armadilhas Comuns

### 1. Cenários Muito Longos

```gherkin
# ❌ Ruim: Cenário muito longo
Cenário: Fluxo completo de compra
  Dado que faço login
  E adiciono produtos ao carrinho
  E preencho endereço
  E escolho método de pagamento
  E confirmo pedido
  E recebo confirmação
  E acompanho entrega
  E recebo produto
  E avalio produto

# ✅ Bom: Dividir em cenários menores
Cenário: Adicionar produto ao carrinho
  Dado que estou autenticado
  Quando adiciono um produto ao carrinho
  Então o produto deve estar no carrinho
```

### 2. Step Definitions Muito Genéricos

```typescript
// ❌ Ruim: Muito genérico, difícil de entender
When('eu faço algo', async () => {
  // código vago
});

// ✅ Bom: Específico e claro
When('eu faço login com {string} e {string}', async (email, password) => {
  await login(email, password);
});
```

## 📚 Recursos Relacionados

- [TDD Workflow](./test-driven-development.md)
- [SDD Workflow](./spec-driven-development.md)

## 🚀 Próximos Passos

1. Identifique um comportamento do sistema
2. Escreva o cenário em Gherkin
3. Implemente os step definitions
4. Execute os testes
5. Implemente o código para passar

---

**Comando Few-Shot**: Use `/few-shot-bdd` para aplicar este workflow
