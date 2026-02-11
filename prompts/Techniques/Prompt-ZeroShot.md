# Explicação sobre Zero-Shot

**Zero-shot prompting** ocorre quando você não fornece nenhum exemplo para a LLM — ou seja, pede para o modelo fazer algo sem demonstrar a tarefa antes. O modelo responde com base apenas em seu conhecimento pré-treinado, sem exemplos adicionais no contexto.

## 🎯 Template de Zero-Shot Prompting - Cursor IDE


Template de prompt baseado em **Zero-Shot Prompting** para orientar o comportamento do modelo sem exemplos prévios. Foca em previsibilidade, clareza e qualidade de resposta através de regras claras e determinísticas.

---

## 📋 Template do Prompt

Copie e personalize o template abaixo substituindo os campos `[PAPEL]`, `[DOMÍNIO]`, `[STACK]` e ajustando conforme sua necessidade.

```markdown
## Role (Identidade da IA)

Você é um(a) **[PAPEL / FUNÇÃO ESPECIALIZADA]** com experiência avançada em **[DOMÍNIO PRINCIPAL]**.
Seu objetivo é atuar de forma precisa, consistente e alinhada às melhores práticas do domínio.

## Contexto

Este projeto envolve:
- **Tecnologia(s):** [STACK / LINGUAGENS / FRAMEWORKS]
- **Ambiente:** [EX: frontend, backend, mobile, data, infra]
- **Público-alvo:** [EX: desenvolvedores seniores, iniciantes, clientes finais]
- **Restrições importantes:** [EX: performance, segurança, legibilidade, padrões internos]

## Objetivo Principal

Sua tarefa é:
**[DESCREVER CLARAMENTE O QUE O MODELO DEVE FAZER]**

Você deve focar em:
- Correção técnica
- Clareza e objetividade
- Soluções práticas e aplicáveis

## Instruções de Comportamento (Zero-Shot)

- ❌ NÃO forneça exemplos a menos que seja explicitamente solicitado
- ❌ NÃO invente requisitos ou contexto ausente
- ✅ Se houver ambiguidade, faça suposições razoáveis e explícitas
- ✅ Priorize soluções simples antes de complexas
- ✅ Evite respostas genéricas ou vagas

## Formato de Resposta

Sempre responda utilizando o seguinte formato:

1. **Resumo da solução**
2. **Explicação técnica**
3. **Implementação (se aplicável)**
4. **Boas práticas ou observações finais**

## Padrões e Boas Práticas

- Siga convenções oficiais das tecnologias utilizadas
- Escreva código limpo, legível e comentado quando necessário
- Evite overengineering
- Utilize terminologia técnica correta

## Tom e Estilo

- **Tom:** [EX: profissional, técnico, direto]
- **Linguagem:** clara e objetiva
- Evite emojis, jargões desnecessários ou informalidade excessiva

## Limitações

- Não forneça informações desatualizadas
- Não assuma dependências não mencionadas
- Não gere código inseguro ou antipadrões conhecidos
```

---

## 🚀 Como Usar

### 1️⃣ Personalizar o Template

#### Definir o Role (Obrigatório)
Substitua `[PAPEL / FUNÇÃO ESPECIALIZADA]` e `[DOMÍNIO PRINCIPAL]` por valores específicos.

**✅ Exemplos bons:**
- `desenvolvedor full-stack` + `aplicações web modernas`
- `arquiteto de software` + `sistemas distribuídos`
- `engenheiro de dados` + `pipelines de ETL`

**❌ Exemplos ruins:**
- `programador` (muito genérico)
- `especialista` (sem especificação)
- `desenvolvedor` (sem contexto)

#### Definir o Contexto
Especifique claramente:
- Stack tecnológico utilizado
- Ambiente de desenvolvimento
- Público-alvo das soluções
- Restrições importantes do projeto

#### Definir o Objetivo Principal
Descreva claramente o que a IA deve fazer:
- `analisar código e sugerir melhorias`
- `escrever código seguindo padrões específicos`
- `explicar conceitos técnicos de forma clara`

---

### 2️⃣ Aplicar o Prompt

#### Onde Usar
- **Cursor** → Cole como system prompt nas configurações (Ruler)
- **VS Code com extensões de IA** → Use como custom instructions
- **ChatGPT/Claude** → Cole como primeira mensagem
- **APIs** → Mensagem de sistema (`system`)

> ⚠️ **Importante:** Use este prompt **antes de qualquer interação**. Ele funciona como um **contrato de funcionamento** que orienta o comportamento sem necessidade de exemplos.

---

### 3️⃣ Exemplo Prático Completo

**Template Personalizado:**
```markdown
## Role (Identidade da IA)

Você é um desenvolvedor full-stack com experiência avançada em aplicações web modernas.
Seu objetivo é atuar de forma precisa, consistente e alinhada às melhores práticas do domínio.

## Contexto

Este projeto envolve:
- Tecnologia(s): React, TypeScript, Node.js, PostgreSQL
- Ambiente: frontend e backend web
- Público-alvo: desenvolvedores intermediários
- Restrições importantes: performance, segurança, legibilidade

## Objetivo Principal

Sua tarefa é:
Analisar código, sugerir melhorias e escrever código limpo seguindo padrões modernos.

[... resto do template ...]
```

**Resultado:** A IA responderá de forma técnica e objetiva, sem fornecer exemplos desnecessários, focando em soluções práticas e aplicáveis.

---

## 💡 Por Que Este Prompt Funciona

### ✅ 1. Zero-Shot Prompting Eficaz
- Não requer exemplos prévios para funcionar
- Usa conhecimento pré-treinado do modelo de forma eficiente
- Reduz tokens e custos comparado a Few-Shot

### ✅ 2. Regras Claras e Determinísticas
- Instruções explícitas sobre o que fazer e não fazer
- Formato de resposta obrigatório garante consistência
- Limitações claras previnem comportamentos indesejados

### ✅ 3. Foco em Previsibilidade
- Estrutura consistente facilita parsing e validação
- Tom e estilo definidos garantem uniformidade
- Padrões e boas práticas orientam a qualidade

### ✅ 4. Ideal para IDEs
- Foco técnico e objetivo
- Adaptável a diferentes contextos de projeto
- Não depende de exemplos que podem ficar desatualizados

### ✅ 5. Eficiente e Escalável
- Menor consumo de tokens que Few-Shot
- Fácil de personalizar para diferentes domínios
- Funciona bem com modelos modernos (GPT-4, Claude, etc.)

---

## ⚠️ Observações Importantes

### O que este prompt faz:
- ✅ Orienta comportamento sem exemplos
- ✅ Garante formato consistente de resposta
- ✅ Previne respostas genéricas ou vagas
- ✅ Foca em soluções práticas e aplicáveis
- ✅ Reduz consumo de tokens

### O que este prompt NÃO faz:
- ❌ Não fornece exemplos de saída esperada
- ❌ Não garante 100% de precisão (sempre valide)
- ❌ Não é adequado quando exemplos são essenciais

### Quando usar Zero-Shot vs Few-Shot:
- **Use Zero-Shot quando:** O modelo tem conhecimento suficiente sobre o domínio
- **Use Few-Shot quando:** Precisa de exemplos muito específicos ou formatos complexos

---

## 🔄 Personalização Avançada

### Para Diferentes Contextos:

**Desenvolvimento Frontend:**
```markdown
Tecnologia(s): React, TypeScript, Tailwind CSS
Ambiente: frontend web
Restrições: performance, acessibilidade, SEO
```

**Desenvolvimento Backend:**
```markdown
Tecnologia(s): Node.js, Express, PostgreSQL
Ambiente: backend API REST
Restrições: segurança, escalabilidade, performance
```

**Análise de Dados:**
```markdown
Tecnologia(s): Python, Pandas, NumPy
Ambiente: data science
Restrições: precisão, performance, visualização clara
```

---

## 💭 Filosofia

> **"Zero-Shot Prompting é como dar instruções claras a um especialista experiente: você confia no conhecimento pré-existente e orienta o comportamento através de regras precisas."**

Este prompt aproveita o conhecimento pré-treinado do modelo, orientando-o com regras claras sem necessidade de exemplos. É eficiente, escalável e ideal para tarefas onde o modelo já possui conhecimento suficiente.

---

## 🔄 Próximos Níveis (Evolução)

1. **Combinar com Few-Shot** - Adicionar exemplos quando necessário para casos específicos
2. **Integrar com Chain-of-Thought** - Adicionar raciocínio passo a passo quando apropriado
3. **Adicionar validação** - Critérios de qualidade para as respostas
4. **Criar versões por domínio** - Templates específicos para cada área técnica

---

## 🧠 Nota Final

Este template aplica Zero-Shot Prompting de forma explícita, reduzindo dependência de exemplos e focando em:

- Regras claras e determinísticas
- Formato de resposta consistente
- Comportamento previsível e eficiente

Ideal para uso contínuo em IDEs onde eficiência e consistência são prioritárias.
