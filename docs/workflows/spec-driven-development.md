# 📋 Spec-Driven Development (SDD)

> **"Especificação primeiro, código depois."**

## 🎯 Conceito

**Spec-Driven Development (SDD)** é uma abordagem onde você escreve **o que o sistema deve fazer** antes de escrever **como ele faz**.

A ideia é simples e poderosa: documentar o comportamento esperado, a arquitetura e as decisões antes de implementar o código.

## 🔄 Fluxo de Trabalho

```
1. Escrever Spec (Markdown/ADR)
   ↓
2. Revisar e Alinhar com Time
   ↓
3. Implementar Código seguindo Spec
   ↓
4. Validar que Código atende Spec
   ↓
5. Atualizar Spec se necessário
```

## 🛠️ Ferramentas Comuns

- **Markdown specs** - Documentação técnica em Markdown
- **ADRs (Architecture Decision Records)** - Registro de decisões arquiteturais
- **SpecKit no GitHub** - Ferramentas para specs no GitHub
- **OpenAPI/Swagger** - Para APIs REST
- **PlantUML/Mermaid** - Para diagramas

## ✅ Quando Usar

- ✅ Projetos médios/grandes
- ✅ Integração com IA (especs servem como contexto)
- ✅ Software que vai crescer
- ✅ Times que precisam de alinhamento
- ✅ Quando documentação é crítica
- ✅ Projetos com múltiplos desenvolvedores

## ❌ Quando NÃO Usar

- ❌ Protótipos muito rápidos
- ❌ Projetos que mudam constantemente
- ❌ Quando velocidade é mais importante que clareza
- ❌ Projetos solo muito pequenos

## 📝 Estrutura de uma Spec

### Exemplo Básico

```markdown
# Feature: Autenticação de Usuário

## Objetivo
Permitir que usuários façam login no sistema.

## Requisitos Funcionais
- RF1: Usuário deve poder fazer login com email e senha
- RF2: Sistema deve validar credenciais
- RF3: Sistema deve retornar token JWT válido

## Requisitos Não-Funcionais
- RNF1: Resposta deve ser < 200ms
- RNF2: Senha deve ser criptografada (bcrypt)

## Endpoints

### POST /auth/login
**Request:**
```json
{
  "email": "user@example.com",
  "password": "senha123"
}
```

**Response (200):**
```json
{
  "token": "eyJhbGc...",
  "user": {
    "id": 1,
    "email": "user@example.com"
  }
}
```

**Response (401):**
```json
{
  "error": "Invalid credentials"
}
```

## Decisões Arquiteturais
- Usar JWT para tokens
- Usar bcrypt para hash de senhas
- Armazenar tokens em Redis para revogação
```

## 🎨 Padrões e Boas Práticas

### 1. Escreva Specs Executáveis

Quando possível, use specs que podem ser validadas automaticamente:

- OpenAPI para APIs
- Testes de contrato
- Validação de schemas

### 2. Mantenha Specs Atualizadas

- Atualize specs quando código muda
- Use specs como fonte da verdade
- Revise specs regularmente

### 3. Seja Específico, mas Não Rigido

- Especifique comportamento, não implementação
- Deixe espaço para decisões técnicas
- Foque no "o quê", não no "como"

### 4. Use ADRs para Decisões Importantes

```markdown
# ADR-001: Escolha de Banco de Dados

## Status
Aceito

## Contexto
Precisamos escolher um banco de dados para o projeto.

## Decisão
Usaremos PostgreSQL.

## Consequências
- ✅ Suporte robusto a relacionamentos
- ✅ ACID completo
- ⚠️ Requer mais configuração que SQLite
```

## 🔗 Integração com IA

SDD é especialmente poderoso com IA porque:

1. **Specs servem como contexto** - IA entende o que precisa fazer
2. **Geração de código alinhada** - Código segue a spec
3. **Validação automática** - IA pode validar código contra spec
4. **Documentação sempre atualizada** - IA pode atualizar specs

## 📚 Recursos Relacionados

- [Spec-Driven Development Guide](../spec-driven-development.md)
- [ADR Template](../../prompts/Prompt-Documetations/ADR/Prompt-ADR.md)
- [PRD Template](../../prompts/Prompt-Documetations/PRD/Prompt-PRD.md)

## 🚀 Próximos Passos

1. Escolha uma feature para especificar
2. Use o template de spec apropriado
3. Revise com o time
4. Implemente seguindo a spec
5. Valide que código atende spec

---

**Comando Few-Shot**: Use `/few-shot-sdd` para aplicar este workflow
