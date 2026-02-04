# 🧠 Template de Chain-of-Thought (CoT) Prompting - Cursor IDE

Template de prompt baseado em **Chain-of-Thought (CoT) Prompting** para orientar o modelo a raciocinar passo a passo antes de fornecer a resposta final. Ideal para problemas complexos que requerem análise estruturada e validação de suposições.

---

## 📋 Template do Prompt

Copie e personalize o template abaixo substituindo os campos `[CONTEXTO]` e `[PROBLEMA]` e ajustando conforme sua necessidade.

```markdown
## Role (Identidade da IA)

Você é um assistente especialista em engenharia de software e arquitetura de código.

## Objetivo

Ajudar na resolução do problema descrito abaixo, fornecendo uma resposta correta, clara e bem fundamentada.

## Contexto

{DESCREVA AQUI O CONTEXTO DO PROJETO, STACK, FRAMEWORK, LINGUAGEM OU RESTRIÇÕES}

## Abordagem (Chain of Thought)

Ao resolver o problema, siga esta abordagem estruturada:

1. **Analise o problema passo a passo** antes de chegar à resposta final
2. **Quebre o raciocínio em etapas lógicas e verificáveis**
3. **Considere possíveis alternativas e trade-offs**
4. **Valide suposições técnicas** antes de concluir

## Instruções Importantes

- Use o raciocínio interno apenas para chegar à melhor solução
- Na resposta final, apresente:
  - ✅ A solução final clara e objetiva
  - 📝 Um **resumo do raciocínio** (não exponha pensamentos internos detalhados)
  - 📌 Observações relevantes ou riscos, se houver

## Formato da Resposta

Sempre responda utilizando o seguinte formato:

1. **Solução Final**
2. **Resumo do Raciocínio**
3. **Pontos de Atenção / Boas Práticas** (opcional)
4. **Próximos Passos** (opcional)

## Problema a ser resolvido

{DESCREVA AQUI O PROBLEMA OU TAREFA}
```

> 💡 **Observação importante:** O template solicita **raciocínio estruturado**, mas permite que o modelo entregue **um resumo do raciocínio** quando necessário (boa prática para compatibilidade e segurança).

---

## 🚀 Como Usar

### 1️⃣ Personalizar o Template

#### Definir o Contexto (Obrigatório)
Substitua `{DESCREVA AQUI O CONTEXTO...}` por informações específicas do projeto.

**✅ Exemplos bons:**
- `Projeto React com TypeScript, usando hooks customizados e Context API`
- `API REST em Node.js com Express, seguindo padrões RESTful e validação com Zod`
- `Sistema de autenticação JWT com refresh tokens e rate limiting`

**❌ Exemplos ruins:**
- `Projeto web` (muito genérico)
- `Aplicação` (sem especificação)
- `Código` (sem contexto)

#### Definir o Problema
Descreva claramente o problema ou tarefa que precisa ser resolvida:
- `Como implementar autenticação segura com JWT?`
- `Refatorar componente React para melhorar performance`
- `Criar endpoint REST seguindo padrões do projeto`

#### Ajustar Abordagem (Opcional)
Personalize as etapas do Chain-of-Thought conforme necessário:
- Adicione validações específicas
- Inclua considerações de performance, segurança, etc.
- Especifique trade-offs importantes para o projeto

---

### 2️⃣ Aplicar o Prompt

#### Onde Usar
- **Cursor** → Cole como system prompt nas configurações (Ruler)
- **VS Code com extensões de IA** → Use como custom instructions
- **ChatGPT/Claude** → Cole como primeira mensagem
- **APIs** → Mensagem de sistema (`system`)

> ⚠️ **Importante:** Use este prompt **antes de qualquer interação**. Ele orienta o modelo a raciocinar de forma estruturada antes de responder.

---

### 3️⃣ Exemplo Prático Completo

**Template Personalizado:**
```markdown
## Role (Identidade da IA)

Você é um assistente especialista em engenharia de software e arquitetura de código.

## Objetivo

Ajudar na resolução do problema descrito abaixo, fornecendo uma resposta correta, clara e bem fundamentada.

## Contexto

Projeto React com TypeScript, usando hooks customizados, Context API e React Query para gerenciamento de estado. Seguimos padrões de Clean Code e Component-Driven Development.

## Abordagem (Chain of Thought)

1. Analise o problema passo a passo antes de chegar à resposta final
2. Quebre o raciocínio em etapas lógicas e verificáveis
3. Considere possíveis alternativas e trade-offs
4. Valide suposições técnicas antes de concluir
5. Considere performance e re-renderizações no React

## Problema a ser resolvido

Como implementar um hook customizado para buscar dados de uma API com cache e tratamento de erros?
```

**Resultado:** A IA raciocinará passo a passo sobre a implementação, considerando hooks, cache, tratamento de erros, e então fornecerá uma solução fundamentada com resumo do raciocínio.

---

## 💡 Por Que Este Prompt Funciona

### ✅ 1. Chain-of-Thought Eficaz
- Força o modelo a pensar antes de responder
- Quebra problemas complexos em etapas menores
- Reduz erros de lógica e suposições incorretas

### ✅ 2. Raciocínio Estruturado
- Etapas lógicas e verificáveis
- Considera alternativas e trade-offs
- Valida suposições antes de concluir

### ✅ 3. Resumo do Raciocínio
- Não expõe pensamentos internos detalhados (economiza tokens)
- Mantém resposta focada e objetiva
- Facilita revisão e validação

### ✅ 4. Ideal para Problemas Complexos
- Quando há múltiplas abordagens possíveis
- Quando precisa considerar trade-offs
- Quando validação de suposições é crítica

### ✅ 5. Compatível com Múltiplos LLMs
- Funciona bem com GPT-4, Claude, Gemini e outros
- Estrutura clara e direta
- Não depende de recursos específicos de um modelo

---

## ⚠️ Observações Importantes

### O que este prompt faz:
- ✅ Força raciocínio passo a passo
- ✅ Reduz erros de lógica
- ✅ Considera alternativas e trade-offs
- ✅ Valida suposições antes de responder
- ✅ Fornece resumo do raciocínio (não pensamentos internos detalhados)

### O que este prompt NÃO faz:
- ❌ Não garante 100% de precisão (sempre valide)
- ❌ Não substitui testes e revisão de código
- ❌ Não é adequado para problemas muito simples

### Quando usar Chain-of-Thought:
- **Use CoT quando:**
  - Problema é complexo e requer análise
  - Há múltiplas abordagens possíveis
  - Precisa considerar trade-offs importantes
  - Validação de suposições é crítica

- **Não use CoT quando:**
  - Problema é muito simples e direto
  - Quer economizar tokens
  - Resposta precisa ser extremamente concisa

---

## 🔄 Personalização Avançada

### Dicas para Melhorar o Chain-of-Thought:

**1. Adicionar Validações Específicas:**
```markdown
## Abordagem (Chain of Thought)

1. Analise o problema passo a passo
2. Valide requisitos de segurança
3. Considere impacto em performance
4. Verifique compatibilidade com versões
5. Avalie trade-offs de cada abordagem
```

**2. Incluir Considerações do Domínio:**
```markdown
## Abordagem (Chain of Thought)

1. Analise o problema passo a passo
2. Considere padrões React (hooks, context, etc.)
3. Avalie impacto em re-renderizações
4. Verifique compatibilidade com TypeScript
5. Considere testes e manutenibilidade
```

**3. Especificar Trade-offs Importantes:**
```markdown
## Abordagem (Chain of Thought)

1. Analise o problema passo a passo
2. Considere trade-offs: performance vs legibilidade
3. Avalie complexidade vs manutenibilidade
4. Verifique segurança vs facilidade de uso
```

---

## 💭 Filosofia

> **"Chain-of-Thought Prompting é como pedir para alguém mostrar o trabalho: você vê o processo de pensamento e pode validar cada etapa antes de chegar à conclusão."**

Este prompt aproveita a capacidade do modelo de raciocinar de forma estruturada, garantindo que respostas complexas sejam bem fundamentadas e verificáveis.

---

## 🔄 Próximos Níveis (Evolução)

1. **Combinar com Few-Shot** - Adicionar exemplos de raciocínio esperado
2. **Integrar com Role Prompting** - Especificar expertise necessária
3. **Adicionar validação** - Critérios de qualidade para o raciocínio
4. **Criar templates por domínio** - Chain-of-Thought específicos para diferentes áreas

---

## 🧠 Nota Final

Este template aplica Chain-of-Thought Prompting de forma explícita, orientando o modelo a:

- Raciocinar passo a passo antes de responder
- Considerar alternativas e trade-offs
- Validar suposições técnicas
- Fornecer resumo do raciocínio (não pensamentos internos detalhados)

Ideal para problemas complexos onde análise estruturada é essencial.

---

## 💡 Dica Extra (Opcional)

Se quiser **forçar ainda mais qualidade**, você pode adicionar no Cursor Rules:

```markdown
Sempre priorize soluções simples, seguras e alinhadas às boas práticas da linguagem utilizada.
Evite overengineering.
```
