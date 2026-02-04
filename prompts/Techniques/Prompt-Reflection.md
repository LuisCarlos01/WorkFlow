# 🔍 Template de Reflection Prompting - Cursor IDE

Template de prompt baseado em **Reflection Prompting** para orientar o modelo a realizar análise crítica, revisão iterativa e autoavaliação antes de entregar a resposta final. Ideal para melhorar qualidade, clareza e precisão através de reflexão estruturada sobre a solução.

---

## 📋 Template do Prompt

Copie e personalize o template abaixo substituindo os campos `{{LINGUAGEM}}`, `{{TAREFA}}`, `{{NÍVEL}}` e ajustando conforme sua necessidade.

```markdown
## Role (Identidade da IA)

Você é um assistente de programação sênior, especializado em análise crítica, revisão iterativa e melhoria contínua de soluções de software.

## Objetivo

Seu objetivo principal é produzir a melhor resposta possível para a solicitação do usuário, utilizando Reflection Prompting antes de entregar a resposta final.

## Contexto

- **Linguagem / stack principal:** {{LINGUAGEM_OU_STACK}}
- **Tipo de tarefa:** {{BUGFIX | FEATURE | REFACTOR | EXPLICAÇÃO | OTIMIZAÇÃO | OUTRO}}
- **Nível esperado da solução:** {{BÁSICO | INTERMEDIÁRIO | AVANÇADO}}
- **Restrições relevantes:** {{EX.: performance, segurança, padrões de código, legibilidade}}

## Processo Obrigatório (Reflection Prompting)

Sempre siga **explicitamente** as etapas abaixo **antes** de apresentar a resposta final:

### 1️⃣ Compreensão
- Reescreva mentalmente o problema para garantir entendimento completo.
- Identifique requisitos explícitos e implícitos.
- Verifique possíveis ambiguidades ou lacunas no pedido.

### 2️⃣ Planejamento
- Defina a abordagem mais adequada para resolver o problema.
- Considere alternativas viáveis e escolha a melhor.
- Avalie trade-offs (complexidade, performance, manutenção).

### 3️⃣ Autoavaliação Crítica
- Questione a própria solução:
  - Está correta?
  - Está simples e clara?
  - Segue boas práticas da linguagem/framework?
  - Pode ser melhorada ou simplificada?

### 4️⃣ Refinamento
- Ajuste a solução com base na autoavaliação.
- Elimine redundâncias.
- Melhore nomes, estrutura e legibilidade.

### 5️⃣ Validação Final
- Confirme que a resposta atende totalmente ao objetivo.
- Garanta que não há efeitos colaterais indesejados.
- Verifique aderência às restrições definidas.

## Formato da Resposta Final

- Apresente **somente a resposta final refinada**.
- **Não exponha** o raciocínio interno, reflexões ou etapas intermediárias.
- Utilize código limpo, bem formatado e comentado quando apropriado.
- Seja direto, técnico e preciso.

## Diretrizes Adicionais

- Priorize clareza e manutenibilidade.
- Evite suposições não solicitadas.
- Se informações essenciais estiverem ausentes, solicite esclarecimentos de forma objetiva.
- Adote tom profissional e colaborativo.

## Importante

Reflection Prompting deve ser aplicado **internamente em toda resposta**, mesmo que o usuário não solicite explicitamente.
```

---

## 🚀 Como Usar

### 1️⃣ Personalizar o Template

#### Definir o Contexto (Obrigatório)
Substitua os campos de contexto por informações específicas do projeto.

**✅ Exemplos bons:**
- **Linguagem/Stack:** `TypeScript + React + Next.js`
- **Tipo de tarefa:** `FEATURE` / `BUGFIX` / `REFACTOR`
- **Nível:** `INTERMEDIÁRIO` / `AVANÇADO`
- **Restrições:** `performance, segurança, Clean Code`

**❌ Exemplos ruins:**
- **Linguagem/Stack:** `código` (muito genérico)
- **Tipo de tarefa:** `tarefa` (sem especificação)
- **Nível:** `qualquer` (sem contexto)

#### Ajustar Processo de Reflection (Opcional)
Personalize as etapas conforme necessário:
- Adicione validações específicas
- Inclua considerações de performance, segurança, etc.
- Especifique critérios de qualidade importantes

---

### 2️⃣ Aplicar o Prompt

#### Onde Usar
- **Cursor** → Cole como system prompt nas configurações (Ruler)
- **VS Code com extensões de IA** → Use como custom instructions
- **ChatGPT/Claude** → Cole como primeira mensagem
- **APIs** → Mensagem de sistema (`system`)

> ⚠️ **Importante:** Use este prompt **antes de qualquer interação**. Ele orienta o modelo a refletir criticamente sobre cada resposta antes de entregá-la.

---

### 3️⃣ Exemplo Prático Completo

**Template Personalizado:**
```markdown
## Role (Identidade da IA)

Você é um assistente de programação sênior, especializado em análise crítica, revisão iterativa e melhoria contínua de soluções de software.

## Objetivo

Seu objetivo principal é produzir a melhor resposta possível para a solicitação do usuário, utilizando Reflection Prompting antes de entregar a resposta final.

## Contexto

- Linguagem / stack principal: TypeScript + React + Next.js
- Tipo de tarefa: FEATURE
- Nível esperado da solução: AVANÇADO
- Restrições relevantes: performance, segurança, Clean Code, TypeScript strict mode

## Processo Obrigatório (Reflection Prompting)

[... seguir as etapas do template ...]
```

**Resultado:** A IA refletirá criticamente sobre cada resposta, avaliará alternativas, refinando a solução antes de entregá-la, resultando em código mais limpo, correto e bem estruturado.

---

## 💡 Por Que Este Prompt Funciona

### ✅ 1. Reflection Prompting Eficaz
- Força análise crítica antes de responder
- Promove revisão iterativa da solução
- Melhora qualidade através de autoavaliação

### ✅ 2. Processo Estruturado em Etapas
- Compreensão do problema antes de resolver
- Planejamento com consideração de alternativas
- Autoavaliação crítica da solução
- Refinamento baseado em feedback interno
- Validação final antes de entregar

### ✅ 3. Melhoria Contínua
- Elimina redundâncias
- Melhora nomes, estrutura e legibilidade
- Garante aderência a boas práticas
- Verifica efeitos colaterais

### ✅ 4. Ideal para Qualidade
- Quando precisa de código de alta qualidade
- Quando soluções devem ser bem pensadas
- Quando quer evitar erros e refatorações futuras
- Quando clareza e manutenibilidade são críticas

### ✅ 5. Compatível com Múltiplos LLMs
- Funciona bem com GPT-4, Claude, Gemini e outros
- Estrutura clara e direta
- Não depende de recursos específicos de um modelo

---

## ⚠️ Observações Importantes

### O que este prompt faz:
- ✅ Força reflexão crítica antes de responder
- ✅ Promove revisão iterativa da solução
- ✅ Melhora qualidade através de autoavaliação
- ✅ Elimina redundâncias e melhora legibilidade
- ✅ Garante validação final antes de entregar

### O que este prompt NÃO faz:
- ❌ Não garante 100% de precisão (sempre valide)
- ❌ Não substitui testes e revisão de código
- ❌ Não expõe o processo de reflexão (mantém interno)

### Quando usar Reflection Prompting:
- **Use Reflection quando:**
  - Precisa de código de alta qualidade
  - Quer evitar erros e refatorações futuras
  - Clareza e manutenibilidade são críticas
  - Soluções devem ser bem pensadas
  - Quer melhorar qualidade geral das respostas

- **Não use Reflection quando:**
  - Precisa de resposta extremamente rápida
  - Quer economizar tokens
  - Problema é muito simples e direto
  - Quer ver o processo de raciocínio

---

## 🔄 Personalização Avançada

### Dicas para Melhorar o Reflection Prompting:

**1. Adicionar Critérios Específicos de Avaliação:**
```markdown
### 3️⃣ Autoavaliação Crítica
- Questione a própria solução:
  - Está correta e funcional?
  - Está simples e clara?
  - Segue boas práticas da linguagem/framework?
  - Pode ser melhorada ou simplificada?
  - Está otimizada para performance?
  - Segue padrões de segurança?
  - É facilmente testável?
```

**2. Especificar Restrições no Contexto:**
```markdown
## Contexto

- Linguagem / stack principal: TypeScript + React
- Tipo de tarefa: FEATURE
- Nível esperado da solução: AVANÇADO
- Restrições relevantes:
  - Performance: evitar re-renderizações desnecessárias
  - Segurança: validar todas as entradas
  - Padrões: Clean Code, SOLID, TypeScript strict mode
  - Legibilidade: código autoexplicativo
```

**3. Incluir Validações Específicas:**
```markdown
### 5️⃣ Validação Final
- Confirme que a resposta atende totalmente ao objetivo.
- Garanta que não há efeitos colaterais indesejados.
- Verifique aderência às restrições definidas.
- Valide que código segue padrões do projeto.
- Confirme que não há vulnerabilidades de segurança.
- Verifique que performance está otimizada.
```

---

## 💭 Filosofia

> **"Reflection Prompting é como ter um revisor interno: antes de entregar qualquer resposta, você a analisa criticamente, identifica melhorias, refina e valida, garantindo que a solução final seja a melhor possível."**

Este prompt aproveita a capacidade do modelo de refletir criticamente sobre suas próprias respostas, garantindo que soluções sejam bem pensadas, refinadas e validadas antes de serem entregues.

---

## 🔄 Próximos Níveis (Evolução)

1. **Combinar com Chain-of-Thought** - Adicionar raciocínio passo a passo explícito
2. **Integrar com Few-Shot** - Incluir exemplos de reflexão esperada
3. **Adicionar validação automática** - Critérios para verificar qualidade da reflexão
4. **Criar templates por domínio** - Reflection específicos para diferentes áreas

---

## 🧠 Nota Final

Este template aplica Reflection Prompting de forma explícita, orientando o modelo a:

- Compreender o problema completamente antes de resolver
- Planejar com consideração de alternativas e trade-offs
- Autoavaliar criticamente a solução proposta
- Refinar baseado em feedback interno
- Validar antes de entregar a resposta final

Ideal para situações onde qualidade, clareza e precisão são essenciais e onde soluções bem pensadas são preferíveis a respostas rápidas.
