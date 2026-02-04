# 🤖 AI-First / Prompt-Driven Workflow

> **"IA como colaborador, não como mágica."**

## 🎯 Conceito

**AI-First / Prompt-Driven Workflow** é uma abordagem moderna onde a IA é integrada como **colaborador ativo** no processo de desenvolvimento, desde a especificação até a implementação.

**Ideia central**: Especificação clara → Contexto + Regras → IA gera rascunho → Humano revisa, testa, refatora

## 🔄 Fluxo de Trabalho

```
1. Escrever Especificação Clara
   ↓
2. Preparar Contexto e Regras
   ↓
3. IA Gera Rascunho de Código
   ↓
4. Humano Revisa e Testa
   ↓
5. Refatora e Melhora
   ↓
6. Aprende e Melhora Prompts
```

## 🛠️ Ferramentas e Componentes

### 1. Rules (Regras do Projeto)

Arquivos de regras que definem padrões do projeto:

```markdown
# .cursor/rules/backend.md

## Padrões de Backend
- Sempre usar TypeScript strict mode
- Validação com Zod
- Tratamento de erros com try/catch
- Testes unitários obrigatórios
```

### 2. Context (Contexto)

Informações sobre o projeto:

- Estrutura de pastas
- Bibliotecas usadas
- Padrões arquiteturais
- Decisões técnicas

### 3. Tech Specs

Especificações técnicas detalhadas:

```markdown
# tech-specs/authentication.md

## Autenticação
- JWT tokens
- Refresh tokens em Redis
- Expiração: 15 minutos
- Refresh: 7 dias
```

### 4. Sub-Agents / Specialized Prompts

Prompts especializados para tarefas específicas:

- `/few-shot` - Para padrões específicos
- `/test` - Para gerar testes
- `/refactor` - Para refatoração
- `/docs` - Para documentação

## ✅ Quando Usar

- ✅ Hoje. Literalmente hoje.
- ✅ Projetos com IA integrada (Cursor, GitHub Copilot, etc.)
- ✅ Quando velocidade e qualidade precisam coexistir
- ✅ Desenvolvimento solo ou pequenos times
- ✅ Prototipagem rápida
- ✅ Geração de boilerplate

## ❌ Quando NÃO Usar

- ❌ Código crítico sem revisão humana
- ❌ Quando não há tempo para revisar código gerado
- ❌ Projetos com padrões muito específicos não documentados
- ❌ Quando confiança cega em IA é perigosa

## 🎨 Padrões e Boas Práticas

### 1. Especificação Clara e Detalhada

```markdown
# ❌ Ruim: Vago
"Crie um endpoint de login"

# ✅ Bom: Específico
"Crie um endpoint POST /auth/login que:
- Recebe email e senha
- Valida com Zod
- Retorna JWT token
- Trata erros adequadamente
- Segue padrões do projeto"
```

### 2. Contexto Rico

Forneça contexto suficiente:

```markdown
## Contexto
- Projeto: E-commerce API
- Stack: Node.js + TypeScript + Express
- Banco: PostgreSQL + Prisma
- Autenticação: JWT
- Padrões: Clean Code, SOLID
```

### 3. Regras Explícitas

Defina regras claras:

```markdown
## Regras
- ✅ Sempre validar entrada com Zod
- ✅ Usar async/await, nunca callbacks
- ✅ Tratar erros com try/catch
- ✅ Retornar status HTTP apropriados
- ❌ Não usar `any` em TypeScript
```

### 4. Revisão Humana Sempre

```markdown
# Fluxo
1. IA gera código
2. Humano revisa
3. Humano testa
4. Humano ajusta se necessário
5. Commit
```

### 5. Iteração e Aprendizado

Melhore prompts baseado em resultados:

```markdown
# Prompt v1 (não funcionou bem)
"Crie um endpoint"

# Prompt v2 (melhorado após feedback)
"Crie um endpoint POST /api/users seguindo:
- Padrão do projeto (ver rules/backend.md)
- Validação com Zod schema
- Tratamento de erros
- Testes unitários"
```

## 📝 Exemplo Prático Completo

### 1. Preparar Especificação

```markdown
# Feature: Endpoint de Login

## Requisitos
- POST /auth/login
- Recebe: { email: string, password: string }
- Valida com Zod
- Retorna: { token: string, user: object }
- Status: 200 (sucesso), 401 (credenciais inválidas)

## Padrões
- Ver .cursor/rules/backend.md
- Usar Prisma para banco
- JWT para tokens
```

### 2. Preparar Contexto

```markdown
## Contexto do Projeto
- Stack: Node.js + TypeScript + Express
- ORM: Prisma
- Validação: Zod
- Autenticação: JWT
- Estrutura: src/routes, src/controllers, src/services
```

### 3. Gerar com IA

**Prompt para IA**:
```
Crie um endpoint POST /auth/login seguindo a especificação em 
docs/features/login.md e as regras em .cursor/rules/backend.md.

Inclua:
- Validação com Zod
- Lógica de autenticação
- Geração de JWT
- Tratamento de erros
- Testes unitários
```

### 4. Revisar Código Gerado

```typescript
// Código gerado pela IA
export async function login(req: Request, res: Response) {
  // Revisar:
  // ✅ Validação está correta?
  // ✅ Tratamento de erros adequado?
  // ✅ Segue padrões do projeto?
  // ✅ Testes cobrem casos importantes?
}
```

### 5. Ajustar e Melhorar

```typescript
// Ajustes feitos após revisão
export async function login(req: Request, res: Response) {
  // Melhorias:
  // - Adicionar rate limiting
  // - Melhorar mensagens de erro
  // - Adicionar logging
}
```

## 🎯 Estrutura de Arquivos

```
.cursor/
├── rules/
│   ├── backend.md
│   ├── frontend.md
│   └── general.md
├── commands/
│   ├── few-shot.md
│   ├── test.md
│   └── refactor.md
└── context/
    └── project-overview.md

docs/
├── tech-specs/
│   ├── authentication.md
│   └── database.md
└── features/
    └── login.md
```

## 🔧 Comandos Úteis

### Few-Shot Prompting

```bash
/few-shot API REST com Node.js e TypeScript
```

Gera prompt personalizado com exemplos do padrão desejado.

### Test Generation

```bash
/test create unit tests for userService
```

Gera testes baseados no código existente.

### Refactoring

```bash
/refactor improve error handling in authController
```

Refatora código seguindo padrões do projeto.

## ⚠️ Armadilhas Comuns

### 1. Confiança Cega

```typescript
// ❌ Ruim: Aceitar código sem revisar
// IA gerou, então deve estar certo

// ✅ Bom: Sempre revisar
// IA gerou, vou revisar, testar e ajustar
```

### 2. Prompts Vagos

```markdown
# ❌ Ruim: Vago
"Crie um endpoint"

# ✅ Bom: Específico
"Crie um endpoint POST /api/users que:
- Valida entrada com Zod schema UserSchema
- Cria usuário no banco com Prisma
- Retorna 201 com dados do usuário criado
- Trata erros com try/catch
- Segue padrões em .cursor/rules/backend.md"
```

### 3. Falta de Contexto

```markdown
# ❌ Ruim: Sem contexto
"Crie um componente React"

# ✅ Bom: Com contexto
"Crie um componente React seguindo:
- Padrões em .cursor/rules/frontend.md
- Usar TypeScript
- Styled Components para estilos
- Atomic Design pattern
- Exemplo similar em src/components/Button"
```

### 4. Não Aprender com Resultados

```markdown
# ❌ Ruim: Usar mesmo prompt sempre
# Mesmo que resultados sejam ruins

# ✅ Bom: Melhorar prompts iterativamente
# Prompt v1 → Revisar → Prompt v2 melhorado
```

## 🔗 Integração com Outros Workflows

### AI-First + SDD
- SDD fornece especificações claras
- IA implementa baseado nas specs
- Ciclo virtuoso: Spec → IA → Código → Validação

### AI-First + TDD
- IA gera testes baseados em specs
- TDD garante qualidade
- IA ajuda na implementação

### AI-First + Iterative
- IA acelera cada iteração
- Feedback rápido permite ajustes rápidos
- Ciclo de melhoria contínua

## 📚 Recursos Relacionados

- [Cursor IDE](https://cursor.sh/)
- [GitHub Copilot](https://github.com/features/copilot)
- [Prompt Engineering Guide](https://www.promptingguide.ai/)

## 🚀 Próximos Passos

1. Configure regras do projeto (.cursor/rules/)
2. Documente padrões e contexto
3. Crie comandos personalizados
4. Pratique escrita de prompts claros
5. Revise e melhore iterativamente

---

**Comando Few-Shot**: Use `/few-shot-ai-first` para aplicar este workflow
