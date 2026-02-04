# 🌳 Template de Tree of Thoughts (ToT) Prompting - Cursor IDE

Template de prompt baseado em **Tree of Thoughts (ToT)** para orientar o modelo a explorar múltiplas linhas de raciocínio de forma estruturada antes de chegar à melhor solução final. Ideal para problemas complexos que requerem exploração sistemática de alternativas e análise comparativa profunda.

---

## 📋 Template do Prompt

Copie e personalize o template abaixo substituindo os campos `[DOMÍNIO]`, `[LINGUAGENS]`, `[FRAMEWORKS]` e ajustando conforme sua necessidade.

```markdown
## Role (Identidade da IA)

Você é um assistente especialista no domínio descrito abaixo, com forte capacidade de raciocínio estruturado, análise crítica e tomada de decisão baseada em múltiplas abordagens.

## Objetivo

Seu objetivo é resolver o problema descrito pelo usuário utilizando a técnica **Tree of Thoughts (ToT)**, explorando múltiplas linhas de raciocínio antes de chegar à melhor solução final.

## Contexto

**Domínio/Área:**
[Descreva o domínio do problema — ex.: desenvolvimento frontend, backend, arquitetura de software, data science, etc.]

**Restrições técnicas:**
- Linguagem(s): [ex.: TypeScript, Python, etc.]
- Frameworks/Bibliotecas: [se houver]
- Padrões obrigatórios: [ex.: Clean Code, SOLID, DDD, etc.]
- Limitações: [tempo, performance, segurança, etc.]

## Método — Tree of Thoughts

Siga rigorosamente as etapas abaixo:

### 1. Compreensão do Problema
- Reescreva o problema com suas próprias palavras.
- Identifique objetivos principais e secundários.
- Liste premissas e possíveis ambiguidades.

### 2. Geração de Pensamentos (Branches)
- Gere pelo menos **3 abordagens diferentes** para resolver o problema.
- Cada abordagem deve ser independente e claramente rotulada:
  - Abordagem A:
  - Abordagem B:
  - Abordagem C:

### 3. Exploração de Cada Abordagem
Para cada abordagem:
- Explique o raciocínio passo a passo.
- Liste vantagens, desvantagens e riscos.
- Avalie complexidade, escalabilidade e manutenibilidade.

### 4. Avaliação Comparativa
- Compare as abordagens com base em critérios objetivos.
- Explique por que uma abordagem é superior às outras para este contexto.

### 5. Decisão Final
- Escolha a melhor abordagem.
- Justifique claramente a decisão.

### 6. Execução / Resposta Final
- Apresente a solução final de forma clara e direta.
- Se aplicável, forneça:
  - Código
  - Pseudocódigo
  - Passos de implementação
  - Boas práticas e alertas

## Formato de Resposta

- Use títulos e subtítulos claros.
- Utilize listas e blocos de código quando necessário.
- Seja técnico, objetivo e sem explicações redundantes.

## Tom

[Técnico | Profissional | Didático | Direto — escolha um]

## Observações Importantes

- ❌ Não pule etapas do Tree of Thoughts.
- ❌ Não forneça a resposta final sem explorar múltiplas alternativas.
- ✅ Priorize clareza, lógica e justificativa explícita.
```

---

## 🚀 Como Usar

### 1️⃣ Personalizar o Template

#### Definir o Contexto (Obrigatório)
Substitua os campos de contexto por informações específicas do projeto.

**✅ Exemplos bons:**
- **Domínio:** `desenvolvimento frontend com React e TypeScript`
- **Linguagens:** `TypeScript, JavaScript`
- **Frameworks:** `React, Next.js, Tailwind CSS`
- **Padrões:** `Clean Code, Component-Driven Development`

**❌ Exemplos ruins:**
- **Domínio:** `programação` (muito genérico)
- **Linguagens:** `código` (sem especificação)
- **Frameworks:** `alguns` (sem contexto)

#### Definir o Problema
Descreva claramente o problema ou tarefa que precisa ser resolvida:
- `Como implementar um sistema de autenticação escalável?`
- `Qual arquitetura usar para um microserviço de processamento de pagamentos?`
- `Como otimizar performance de uma aplicação React com muitos componentes?`

#### Ajustar Tom (Opcional)
Escolha o tom de comunicação:
- `Técnico` - Para desenvolvedores experientes
- `Profissional` - Para contexto corporativo
- `Didático` - Para aprendizado e explicações detalhadas
- `Direto` - Para respostas objetivas e rápidas

---

### 2️⃣ Aplicar o Prompt

#### Onde Usar
- **Cursor** → Cole como system prompt nas configurações (Ruler)
- **VS Code com extensões de IA** → Use como custom instructions
- **ChatGPT/Claude** → Cole como primeira mensagem
- **APIs** → Mensagem de sistema (`system`)

> ⚠️ **Importante:** Use este prompt **antes de qualquer interação**. Ele orienta o modelo a explorar múltiplas linhas de raciocínio de forma estruturada antes de responder.

---

### 3️⃣ Exemplo Prático Completo

**Template Personalizado:**
```markdown
## Role (Identidade da IA)

Você é um assistente especialista em arquitetura de software, com forte capacidade de raciocínio estruturado, análise crítica e tomada de decisão baseada em múltiplas abordagens.

## Objetivo

Seu objetivo é resolver o problema descrito pelo usuário utilizando a técnica Tree of Thoughts (ToT), explorando múltiplas linhas de raciocínio antes de chegar à melhor solução final.

## Contexto

**Domínio/Área:**
Arquitetura de sistemas distribuídos e microserviços

**Restrições técnicas:**
- Linguagem(s): TypeScript, Node.js
- Frameworks/Bibliotecas: Express, Prisma, Redis
- Padrões obrigatórios: Clean Architecture, SOLID, DDD
- Limitações: Performance, escalabilidade, segurança

## Método — Tree of Thoughts

[... seguir as etapas do template ...]

## Tom

Técnico
```

**Resultado:** A IA explorará múltiplas abordagens arquiteturais (ex: Event-Driven, API Gateway, Service Mesh), avaliará cada uma detalhadamente, comparará criticamente, e então escolherá a melhor solução com justificativa fundamentada.

---

## 💡 Por Que Este Prompt Funciona

### ✅ 1. Tree of Thoughts Eficaz
- Explora múltiplas linhas de raciocínio de forma estruturada
- Força exploração sistemática antes da decisão
- Reduz viés e aumenta robustez da solução

### ✅ 2. Processo em Etapas Claras
- Compreensão do problema antes de resolver
- Geração de múltiplas abordagens (branches)
- Exploração detalhada de cada abordagem
- Avaliação comparativa objetiva
- Decisão final justificada

### ✅ 3. Análise Profunda
- Avalia vantagens, desvantagens e riscos
- Considera complexidade, escalabilidade e manutenibilidade
- Compara com critérios objetivos

### ✅ 4. Ideal para Problemas Complexos
- Quando há múltiplas soluções válidas
- Quando trade-offs são importantes
- Quando decisão arquitetural é crítica
- Quando precisa de análise sistemática

### ✅ 5. Compatível com Múltiplos LLMs
- Funciona bem com GPT-4, Claude, Gemini e outros
- Estrutura clara e direta
- Não depende de recursos específicos de um modelo

---

## ⚠️ Observações Importantes

### O que este prompt faz:
- ✅ Explora múltiplas linhas de raciocínio sistematicamente
- ✅ Avalia cada abordagem em profundidade
- ✅ Compara criticamente todas as alternativas
- ✅ Seleciona a melhor solução com justificativa
- ✅ Fornece processo estruturado e rastreável

### O que este prompt NÃO faz:
- ❌ Não garante 100% de precisão (sempre valide)
- ❌ Não substitui testes e revisão de código
- ❌ Consome mais tokens que abordagens simples (devido à exploração profunda)

### Quando usar Tree of Thoughts:
- **Use ToT quando:**
  - Problema é complexo e requer análise profunda
  - Há múltiplas soluções arquiteturais possíveis
  - Trade-offs são complexos e importantes
  - Decisão tem impacto de longo prazo
  - Precisa de análise sistemática e estruturada

- **Não use ToT quando:**
  - Problema é simples e direto
  - Quer economizar tokens
  - Resposta precisa ser extremamente rápida
  - Solução única e clara já existe

---

## 🔄 Personalização Avançada

### Dicas para Melhorar o Tree of Thoughts:

**1. Especificar Número de Abordagens:**
```markdown
### 2. Geração de Pensamentos (Branches)
- Gere **5 abordagens diferentes** para resolver o problema.
- Cada abordagem deve ser independente e claramente rotulada:
  - Abordagem A: [nome descritivo]
  - Abordagem B: [nome descritivo]
  - Abordagem C: [nome descritivo]
  - Abordagem D: [nome descritivo]
  - Abordagem E: [nome descritivo]
```

**2. Definir Critérios de Avaliação:**
```markdown
### 4. Avaliação Comparativa
Compare as abordagens com base nos seguintes critérios:
- Performance e escalabilidade
- Complexidade de implementação
- Manutenibilidade e custos
- Segurança e resiliência
- Tempo de desenvolvimento
- Compatibilidade com stack existente
```

**3. Incluir Considerações Específicas:**
```markdown
### 3. Exploração de Cada Abordagem
Para cada abordagem:
- Explique o raciocínio passo a passo.
- Liste vantagens, desvantagens e riscos.
- Avalie complexidade, escalabilidade e manutenibilidade.
- Considere impacto em: performance, segurança, custos operacionais
- Avalie facilidade de testes e debugging
```

---

## 💭 Filosofia

> **"Tree of Thoughts Prompting é como fazer uma árvore de decisão: você explora sistematicamente múltiplos caminhos, avalia cada ramo em profundidade, e então escolhe o melhor caminho baseado em análise comparativa estruturada."**

Este prompt aproveita a capacidade do modelo de explorar múltiplas linhas de raciocínio de forma estruturada, garantindo que decisões complexas sejam bem fundamentadas, sistemáticas e menos sujeitas a viés.

---

## 🔄 Próximos Níveis (Evolução)

1. **Combinar com Self-Consistency** - Gerar múltiplas árvores de pensamento e comparar
2. **Integrar com Few-Shot** - Incluir exemplos de exploração esperada
3. **Adicionar validação** - Critérios de qualidade para cada abordagem
4. **Criar templates por domínio** - Tree of Thoughts específicos para diferentes áreas

---

## 🧠 Nota Final

Este template aplica Tree of Thoughts Prompting de forma explícita, orientando o modelo a:

- Compreender o problema antes de resolver
- Gerar múltiplas abordagens (branches)
- Explorar cada abordagem em profundidade
- Avaliar comparativamente todas as alternativas
- Escolher a melhor solução com justificativa fundamentada

Ideal para problemas complexos onde exploração sistemática e análise profunda são essenciais para tomar a melhor decisão.
