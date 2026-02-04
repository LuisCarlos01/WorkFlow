# 🔗 Template de Prompt Chaining - Cursor IDE

Template de prompt baseado em **Prompt Chaining** para orientar o modelo a dividir o raciocínio em etapas claras, sequenciais e dependentes. Ideal para tarefas complexas que requerem processamento em múltiplas etapas bem definidas, garantindo que cada etapa seja concluída antes de avançar.

---

## 📋 Template do Prompt

Copie e personalize o template abaixo substituindo os campos `{{ROLE}}`, `{{OBJETIVO}}`, `{{PROJETO}}` e ajustando conforme sua necessidade.

```markdown
## Role (Identidade da IA)

Você é um(a) **{{ROLE_DO_MODELO}}**, especialista em **{{AREA_DE_CONHECIMENTO}}**.

## Objetivo Principal

Seu objetivo principal é **{{OBJETIVO_FINAL_DO_PROMPT}}**.

Você deve executar essa tarefa utilizando **PROMPT CHAINING**, dividindo o raciocínio em etapas claras, sequenciais e dependentes, conforme definido abaixo.

## Contexto Geral

- **Projeto:** {{NOME_DO_PROJETO}}
- **Público-alvo:** {{PUBLICO_ALVO}}
- **Nível técnico esperado:** {{NIVEL_TECNICO}}
- **Linguagem:** Português do Brasil
- **Ambiente:** {{EX: Cursor IDE, Backend, Frontend, Data, etc}}

## Etapa 1 – Análise

**Objetivo:**
- Compreender completamente o problema e o contexto.

**Instruções:**
- Analise os requisitos fornecidos.
- Identifique premissas, restrições e dependências.
- Liste possíveis riscos ou ambiguidades.

**Saída esperada:**
- Resumo estruturado do problema
- Lista de premissas e restrições
- Perguntas ou alertas (se houver)

> ⚠️ **Não avance para a próxima etapa sem concluir esta.**

## Etapa 2 – Planejamento

**Objetivo:**
- Definir a melhor estratégia para resolver o problema.

**Instruções:**
- Quebre a solução em subtarefas lógicas.
- Escolha abordagens, padrões ou técnicas adequadas.
- Justifique decisões importantes.

**Saída esperada:**
- Plano passo a passo
- Estrutura lógica da solução
- Tecnologias, padrões ou conceitos envolvidos

> ⚠️ **Não implemente nada nesta etapa.**

## Etapa 3 – Execução

**Objetivo:**
- Implementar a solução conforme o planejamento aprovado.

**Instruções:**
- Execute exatamente o plano definido na etapa anterior.
- Seja claro, objetivo e tecnicamente correto.
- Use boas práticas da área **{{AREA_DE_CONHECIMENTO}}**.

**Saída esperada:**
- {{EX: Código, texto, prompt, arquitetura, resposta técnica}}

## Etapa 4 – Revisão e Otimização

**Objetivo:**
- Garantir qualidade, clareza e aderência ao objetivo final.

**Instruções:**
- Revise a saída gerada.
- Aponte melhorias, otimizações ou ajustes possíveis.
- Verifique alinhamento com o objetivo inicial.

**Saída esperada:**
- Versão final otimizada
- Lista de melhorias aplicadas (se houver)

## Restrições Gerais

- ❌ Não invente informações.
- ❌ Não pule etapas.
- ❌ Não misture as saídas entre as etapas.
- ✅ Seja consistente e objetivo.
- ✅ Priorize clareza sobre criatividade, exceto se solicitado.

## Critério de Sucesso

A resposta será considerada correta se:
- ✅ Resolver **{{OBJETIVO_FINAL_DO_PROMPT}}**
- ✅ Seguir rigorosamente o encadeamento de etapas
- ✅ Produzir uma saída clara, reutilizável e tecnicamente correta
```

---

## 🚀 Como Usar

### 1️⃣ Personalizar o Template

#### Definir o Role (Obrigatório)
Substitua `{{ROLE_DO_MODELO}}` e `{{AREA_DE_CONHECIMENTO}}` por valores específicos.

**✅ Exemplos bons:**
- `Engenheiro de Software Sênior` + `desenvolvimento web com React e TypeScript`
- `Arquiteto Backend` + `sistemas distribuídos e microserviços`
- `Desenvolvedor Full-Stack` + `aplicações web modernas`

**❌ Exemplos ruins:**
- `programador` (muito genérico)
- `especialista` (sem especificação)
- `desenvolvedor` (sem contexto)

#### Definir o Objetivo Principal
Especifique claramente o objetivo final:
- `criar uma API REST completa seguindo padrões do projeto`
- `refatorar componente React para melhorar performance`
- `implementar sistema de autenticação seguro`

#### Configurar o Contexto
Defina informações do projeto:
- Nome do projeto
- Público-alvo (iniciantes, desenvolvedores sênior, etc.)
- Nível técnico esperado
- Ambiente de trabalho

---

### 2️⃣ Aplicar o Prompt

#### Onde Usar
- **Cursor** → Cole como system prompt nas configurações (Ruler)
- **VS Code com extensões de IA** → Use como custom instructions
- **ChatGPT/Claude** → Cole como primeira mensagem
- **APIs** → Mensagem de sistema (`system`)

> ⚠️ **Importante:** Use este prompt **antes de qualquer interação**. Ele orienta o modelo a seguir um processo sequencial e estruturado, garantindo que cada etapa seja concluída antes de avançar.

---

### 3️⃣ Exemplo Prático Completo

**Template Personalizado:**
```markdown
## Role (Identidade da IA)

Você é um Engenheiro de Software Sênior, especialista em desenvolvimento web com React e TypeScript.

## Objetivo Principal

Seu objetivo principal é criar uma API REST completa seguindo padrões do projeto.

Você deve executar essa tarefa utilizando PROMPT CHAINING, dividindo o raciocínio em etapas claras, sequenciais e dependentes.

## Contexto Geral

- Projeto: E-commerce API
- Público-alvo: desenvolvedores intermediários
- Nível técnico esperado: intermediário
- Linguagem: Português do Brasil
- Ambiente: Cursor IDE, Backend

## Etapa 1 – Análise

[... seguir as etapas do template ...]
```

**Resultado:** A IA seguirá um processo sequencial: primeiro analisará o problema, depois planejará, executará e finalmente revisará, garantindo que cada etapa seja concluída antes de avançar.

---

## 💡 Por Que Este Prompt Funciona

### ✅ 1. Prompt Chaining Eficaz
- Divide tarefas complexas em etapas claras e sequenciais
- Garante que cada etapa seja concluída antes de avançar
- Cria dependências explícitas entre etapas

### ✅ 2. Processo Estruturado
- Análise antes de planejar
- Planejamento antes de executar
- Execução seguindo o plano
- Revisão e otimização final

### ✅ 3. Controle de Fluxo
- Proíbe pular etapas
- Evita misturar saídas entre etapas
- Garante sequência lógica

### ✅ 4. Ideal para Tarefas Complexas
- Quando tarefa requer múltiplas etapas
- Quando cada etapa depende da anterior
- Quando quer garantir processo completo
- Quando precisa de rastreabilidade

### ✅ 5. Compatível com Múltiplos LLMs
- Funciona bem com GPT-4, Claude, Gemini e outros
- Estrutura clara e direta
- Não depende de recursos específicos de um modelo

---

## ⚠️ Observações Importantes

### O que este prompt faz:
- ✅ Divide tarefas complexas em etapas sequenciais
- ✅ Garante que cada etapa seja concluída antes de avançar
- ✅ Cria dependências explícitas entre etapas
- ✅ Fornece processo estruturado e rastreável
- ✅ Evita pular etapas ou misturar saídas

### O que este prompt NÃO faz:
- ❌ Não garante 100% de precisão (sempre valide)
- ❌ Não substitui testes e revisão de código
- ❌ Pode ser mais lento que abordagens diretas

### Quando usar Prompt Chaining:
- **Use Prompt Chaining quando:**
  - Tarefa é complexa e requer múltiplas etapas
  - Cada etapa depende da anterior
  - Quer garantir processo completo e estruturado
  - Precisa de rastreabilidade do processo
  - Quer evitar pular etapas importantes

- **Não use Prompt Chaining quando:**
  - Tarefa é simples e direta
  - Quer resposta extremamente rápida
  - Etapas são independentes entre si
  - Quer economizar tokens

---

## 🔄 Personalização Avançada

### Dicas para Melhorar o Prompt Chaining:

**1. Adicionar Mais Etapas:**
```markdown
## Etapa 2.5 – Validação do Planejamento

**Objetivo:**
- Validar que o plano está completo e viável.

**Instruções:**
- Revise o plano da Etapa 2.
- Identifique possíveis problemas ou lacunas.
- Ajuste o plano se necessário.

**Saída esperada:**
- Plano validado e ajustado
- Lista de ajustes realizados
```

**2. Especificar Saídas por Etapa:**
```markdown
## Etapa 3 – Execução

**Saída esperada:**
- Código TypeScript completo
- Arquivos organizados por estrutura de pastas
- Comentários explicativos onde necessário
- Testes unitários básicos
```

**3. Adicionar Critérios de Validação:**
```markdown
## Critério de Sucesso

A resposta será considerada correta se:

**Etapa 1:**
- ✅ Problema foi completamente compreendido
- ✅ Todas as premissas foram identificadas

**Etapa 2:**
- ✅ Plano está completo e viável
- ✅ Decisões técnicas foram justificadas

**Etapa 3:**
- ✅ Código segue o plano definido
- ✅ Boas práticas foram aplicadas

**Etapa 4:**
- ✅ Solução está otimizada
- ✅ Objetivo final foi alcançado
```

---

## 💭 Filosofia

> **"Prompt Chaining é como seguir uma receita: você precisa completar cada passo antes de passar para o próximo, garantindo que o resultado final seja construído sobre uma base sólida e bem estruturada."**

Este prompt aproveita a capacidade do modelo de seguir processos sequenciais, garantindo que tarefas complexas sejam divididas em etapas gerenciáveis e que cada etapa seja concluída antes de avançar.

---

## 🔄 Próximos Níveis (Evolução)

1. **Combinar com Chain-of-Thought** - Adicionar raciocínio passo a passo dentro de cada etapa
2. **Integrar com Reflection** - Adicionar autoavaliação em cada etapa
3. **Adicionar validação automática** - Critérios para verificar conclusão de cada etapa
4. **Criar templates por tipo de tarefa** - Chaining específicos para diferentes tipos de problemas

---

## 🧠 Nota Final

Este template aplica Prompt Chaining de forma explícita, orientando o modelo a:

- Dividir tarefas complexas em etapas sequenciais
- Garantir que cada etapa seja concluída antes de avançar
- Criar dependências explícitas entre etapas
- Seguir processo estruturado e rastreável
- Produzir saída final completa e tecnicamente correta

Ideal para tarefas complexas onde processo estruturado, rastreabilidade e garantia de conclusão de etapas são essenciais.
