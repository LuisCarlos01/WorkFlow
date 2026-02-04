# 🔁 Template de Self-Consistency Prompting - Cursor IDE

Template de prompt baseado em **Self-Consistency** para orientar o modelo a gerar múltiplas abordagens independentes e então selecionar a melhor solução através de análise comparativa. Ideal para problemas complexos onde múltiplas soluções são possíveis e você precisa da mais robusta.

---

## 📋 Template do Prompt

Copie e personalize o template abaixo substituindo os campos `[PAPEL]`, `[DOMÍNIO]`, `[TAREFA]` e ajustando conforme sua necessidade.

```markdown
## Role (Identidade da IA)

Você é um modelo de linguagem atuando como **[PAPEL / ESPECIALISTA]**, com foco em **[DOMÍNIO OU CONTEXTO]**.

## Objetivo

Seu objetivo é resolver a seguinte tarefa de forma **confiável e consistente**, utilizando a técnica de **Self-Consistency**.

## Tarefa Principal

[DESCREVA A TAREFA OU PROBLEMA A SER RESOLVIDO]

## Estratégia: Self-Consistency

Siga rigorosamente os passos abaixo:

1. **Gere múltiplas abordagens independentes** (mínimo de 3) para resolver a tarefa.
   - Cada abordagem deve ser desenvolvida de forma separada, sem reaproveitar raciocínios anteriores.
   - Utilize diferentes perspectivas, estratégias ou caminhos lógicos sempre que possível.

2. **Para cada abordagem:**
   - Explique o raciocínio passo a passo.
   - Aponte suposições feitas.
   - Destaque possíveis pontos fortes e limitações.

3. **Compare criticamente todas as abordagens geradas:**
   - Identifique padrões, convergências e divergências.
   - Avalie qual abordagem é mais robusta, correta e alinhada ao objetivo.

4. **Escolha a melhor solução final**, justificando claramente o motivo da escolha com base na análise comparativa.

## Formato da Resposta

Use exatamente a seguinte estrutura:

### Abordagem 1
- **Raciocínio:**
- **Solução proposta:**

### Abordagem 2
- **Raciocínio:**
- **Solução proposta:**

### Abordagem 3
- **Raciocínio:**
- **Solução proposta:**

### Comparação e Análise
- **Pontos em comum:**
- **Diferenças relevantes:**
- **Avaliação crítica:**

### ✅ Solução Final Escolhida
- **Solução:**
- **Justificativa:**

## Restrições e Ajustes

- **Linguagem:** [ex: técnica, simples, didática]
- **Nível de detalhe:** [baixo / médio / alto]
- **Público-alvo:** [ex: iniciantes, desenvolvedores sênior, gestores]
- Evite respostas vagas ou genéricas.
- Priorize precisão, clareza e rastreabilidade do raciocínio.

Caso alguma informação esteja ausente ou ambígua, explicite as suposições feitas antes de prosseguir.
```

---

## 🚀 Como Usar

### 1️⃣ Personalizar o Template

#### Definir o Role (Obrigatório)
Substitua `[PAPEL / ESPECIALISTA]` e `[DOMÍNIO OU CONTEXTO]` por valores específicos.

**✅ Exemplos bons:**
- `arquiteto de software` + `sistemas distribuídos`
- `engenheiro de dados` + `pipelines de ETL`
- `desenvolvedor full-stack` + `aplicações web modernas`

**❌ Exemplos ruins:**
- `especialista` (muito genérico)
- `programador` (sem especificação)
- `desenvolvedor` (sem contexto)

#### Definir a Tarefa Principal
Descreva claramente o problema ou tarefa que precisa ser resolvida:
- `Como implementar autenticação segura com múltiplas estratégias?`
- `Qual a melhor arquitetura para um sistema de cache distribuído?`
- `Como otimizar queries complexas em um banco de dados relacional?`

#### Ajustar Restrições (Opcional)
Personalize conforme necessário:
- **Linguagem:** `técnica` / `simples` / `didática`
- **Nível de detalhe:** `baixo` / `médio` / `alto`
- **Público-alvo:** `iniciantes` / `desenvolvedores sênior` / `gestores`

---

### 2️⃣ Aplicar o Prompt

#### Onde Usar
- **Cursor** → Cole como system prompt nas configurações (Ruler)
- **VS Code com extensões de IA** → Use como custom instructions
- **ChatGPT/Claude** → Cole como primeira mensagem
- **APIs** → Mensagem de sistema (`system`)

> ⚠️ **Importante:** Use este prompt **antes de qualquer interação**. Ele orienta o modelo a gerar múltiplas abordagens e selecionar a melhor através de análise comparativa.

---

### 3️⃣ Exemplo Prático Completo

**Template Personalizado:**
```markdown
## Role (Identidade da IA)

Você é um modelo de linguagem atuando como arquiteto de software, com foco em sistemas distribuídos.

## Objetivo

Seu objetivo é resolver a seguinte tarefa de forma confiável e consistente, utilizando a técnica de Self-Consistency.

## Tarefa Principal

Como implementar um sistema de cache distribuído que seja resiliente, escalável e consistente?

## Estratégia: Self-Consistency

[... seguir os passos do template ...]

## Restrições e Ajustes

- Linguagem: técnica
- Nível de detalhe: alto
- Público-alvo: desenvolvedores sênior
```

**Resultado:** A IA gerará pelo menos 3 abordagens diferentes (ex: Redis Cluster, Memcached, Couchbase), comparará criticamente cada uma, e então selecionará a melhor solução com justificativa fundamentada.

---

## 💡 Por Que Este Prompt Funciona

### ✅ 1. Self-Consistency Eficaz
- Gera múltiplas abordagens independentes
- Força o modelo a considerar diferentes perspectivas
- Reduz viés e aumenta robustez da solução

### ✅ 2. Análise Comparativa Estruturada
- Identifica padrões e convergências
- Destaca diferenças relevantes
- Avalia robustez e correção de cada abordagem

### ✅ 3. Seleção Justificada
- Escolha da melhor solução é fundamentada
- Justificativa baseada em análise comparativa
- Rastreabilidade do raciocínio

### ✅ 4. Ideal para Problemas Complexos
- Quando há múltiplas soluções válidas
- Quando precisa da solução mais robusta
- Quando trade-offs são importantes

### ✅ 5. Compatível com Múltiplos LLMs
- Funciona bem com GPT-4, Claude, Gemini e outros
- Estrutura clara e direta
- Não depende de recursos específicos de um modelo

---

## ⚠️ Observações Importantes

### O que este prompt faz:
- ✅ Gera múltiplas abordagens independentes
- ✅ Compara criticamente todas as soluções
- ✅ Seleciona a melhor solução com justificativa
- ✅ Reduz viés e aumenta robustez
- ✅ Fornece rastreabilidade do raciocínio

### O que este prompt NÃO faz:
- ❌ Não garante 100% de precisão (sempre valide)
- ❌ Não substitui testes e revisão de código
- ❌ Consome mais tokens que abordagens simples (devido às múltiplas gerações)

### Quando usar Self-Consistency:
- **Use Self-Consistency quando:**
  - Problema tem múltiplas soluções válidas
  - Precisa da solução mais robusta
  - Trade-offs são complexos e importantes
  - Quer reduzir viés e aumentar confiabilidade

- **Não use Self-Consistency quando:**
  - Problema tem solução única e clara
  - Quer economizar tokens
  - Resposta precisa ser extremamente rápida

---

## 🔄 Personalização Avançada

### Dicas para Melhorar o Self-Consistency:

**1. Especificar Número de Abordagens:**
```markdown
## Estratégia: Self-Consistency

Gere **5 abordagens independentes** para resolver a tarefa.
[... resto do template ...]
```

**2. Definir Critérios de Comparação:**
```markdown
## Estratégia: Self-Consistency

[... passos do template ...]

3. Compare criticamente todas as abordagens considerando:
   - Performance e escalabilidade
   - Complexidade de implementação
   - Manutenibilidade e custos
   - Segurança e resiliência
```

**3. Incluir Contexto Específico:**
```markdown
## Tarefa Principal

Como implementar autenticação JWT considerando:
- Escalabilidade para milhões de usuários
- Segurança contra ataques comuns
- Facilidade de revogação de tokens
- Compatibilidade com microserviços
```

---

## 💭 Filosofia

> **"Self-Consistency Prompting é como pedir múltiplas opiniões de especialistas: você obtém diferentes perspectivas, compara criticamente, e então escolhe a melhor solução fundamentada."**

Este prompt aproveita a capacidade do modelo de gerar múltiplas soluções independentes, garantindo que a escolha final seja robusta, bem fundamentada e menos sujeita a viés.

---

## 🔄 Próximos Níveis (Evolução)

1. **Combinar com Chain-of-Thought** - Adicionar raciocínio passo a passo em cada abordagem
2. **Integrar com Few-Shot** - Incluir exemplos de comparações esperadas
3. **Adicionar validação** - Critérios de qualidade para cada abordagem
4. **Criar templates por domínio** - Self-Consistency específicos para diferentes áreas

---

## 🧠 Nota Final

Este template aplica Self-Consistency Prompting de forma explícita, orientando o modelo a:

- Gerar múltiplas abordagens independentes
- Comparar criticamente todas as soluções
- Selecionar a melhor solução com justificativa fundamentada
- Reduzir viés e aumentar robustez

Ideal para problemas complexos onde múltiplas soluções são possíveis e você precisa da mais robusta e confiável.
