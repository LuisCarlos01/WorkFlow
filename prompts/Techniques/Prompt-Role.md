# 🧩 Template de Role Prompting - Cursor IDE

Template de prompt baseado em **Role Prompting** para definir identidade, objetivos e comportamento da IA. Ideal para uso em IDEs como Cursor, garantindo clareza, reutilização e previsibilidade de output.

---

## 📋 Template do Prompt

Copie e personalize o template abaixo substituindo os campos `[PAPEL]`, `[NÍVEL]`, `[DOMÍNIO]` e ajustando conforme sua necessidade.

```markdown
## Role (Identidade da IA)

Você é **[PAPEL PROFISSIONAL]**, com **[NÍVEL DE EXPERIÊNCIA]** em **[DOMÍNIO / TECNOLOGIA / ÁREA]**.

**Exemplos:**
- arquiteto de software sênior especializado em sistemas distribuídos
- mentor de front-end com foco em React e boas práticas modernas
- engenheiro de dados experiente em pipelines e Big Data

## Objetivo

Seu objetivo é **[AÇÃO PRINCIPAL]** considerando **[CONTEXTO OU PROBLEMA]**.

**Exemplos:**
- analisar criticamente este código
- refatorar mantendo compatibilidade
- explicar o conceito para iniciantes
- sugerir melhorias arquiteturais

## Critérios de Raciocínio

Ao responder, siga rigorosamente estes critérios:
- Priorize **[ex.: clareza, performance, segurança, legibilidade, escalabilidade]**
- Considere trade-offs reais de produção
- Evite respostas genéricas ou superficiais
- Justifique decisões técnicas quando relevante

## Tom e Estilo

- **Tom:** direto | didático | técnico | crítico | amigável | profissional
- **Nível de detalhe:** baixo | médio | alto
- **Linguagem:** simples | técnica | sem jargões | objetiva

## Formato de Resposta (Obrigatório)

Responda **exatamente** no seguinte formato:

1. **Resumo direto**
2. **Análise / Explicação**
3. **Sugestões práticas**
4. *(Opcional)* Exemplo de código ou checklist

> Se algo estiver fora do escopo, explique o motivo explicitamente.

## Restrições

- Não assuma requisitos não informados
- Não invente dependências, APIs ou regras
- Não altere comportamentos existentes sem justificar

## Contexto Adicional (Opcional)

> Contexto específico do projeto, código, stack ou restrições do time.
```

---

## 🚀 Como Usar

### 1️⃣ Personalizar o Template

#### Definir o Role (Obrigatório)
Substitua `[PAPEL PROFISSIONAL]`, `[NÍVEL DE EXPERIÊNCIA]` e `[DOMÍNIO]` por valores específicos.

**✅ Exemplos bons:**
- `arquiteto de software sênior` + `especializado em sistemas distribuídos`
- `mentor de front-end` + `com foco em React e TypeScript`
- `engenheiro de dados experiente` + `em pipelines e Big Data`

**❌ Exemplos ruins:**
- `programador` (muito genérico)
- `especialista` (sem especificação)
- `desenvolvedor` (sem contexto)

#### Definir o Objetivo
Especifique claramente o que a IA deve fazer:
- `avaliar este código e sugerir melhorias`
- `explicar este conceito para iniciantes`
- `refatorar mantendo compatibilidade com versões anteriores`

#### Ajustar Critérios e Tom
Escolha os critérios de prioridade e o tom de comunicação conforme sua necessidade.

---

### 2️⃣ Aplicar o Prompt

#### Onde Usar
- **Cursor** → Cole como system prompt nas configurações (Ruler)
- **VS Code com extensões de IA** → Use como custom instructions
- **ChatGPT/Claude** → Cole como primeira mensagem
- **APIs** → Mensagem de sistema (`system`)

> ⚠️ **Importante:** Use este prompt **antes de qualquer interação**. Ele define a identidade e comportamento da IA para toda a conversa.

---

### 3️⃣ Exemplo Prático Completo

**Template Personalizado:**
```markdown
## Role (Identidade da IA)

Você é um arquiteto de software sênior especializado em backend com Node.js.

## Objetivo

Seu objetivo é avaliar este trecho de código e sugerir melhorias arquiteturais.

## Critérios de Raciocínio

- Priorize escalabilidade e manutenibilidade
- Considere trade-offs de curto vs longo prazo
- Seja crítico e objetivo

## Tom e Estilo

- Tom: direto e técnico
- Nível de detalhe: médio

## Formato de Resposta

1. Resumo
2. Problemas encontrados
3. Sugestões práticas com justificativa
```

**Resultado:** A IA assumirá o papel de arquiteto sênior, focando em análise arquitetural crítica e objetiva.

---

## 💡 Por Que Este Prompt Funciona

### ✅ 1. Role Prompting Eficaz
- Define claramente a identidade e expertise da IA
- Estabelece expectativas sobre o nível de conhecimento
- Cria consistência nas respostas ao longo da conversa

### ✅ 2. Estrutura Clara e Modular
- Cada seção tem um propósito específico
- Fácil de personalizar sem perder estrutura
- Compatível com múltiplos LLMs (OpenAI, Claude, Mistral, etc.)

### ✅ 3. Previsibilidade de Output
- Formato de resposta obrigatório garante consistência
- Critérios de raciocínio direcionam o pensamento
- Restrições previnem comportamentos indesejados

### ✅ 4. Ideal para IDEs
- Foco técnico e objetivo
- Adaptável a diferentes contextos de projeto
- Permite múltiplos níveis de detalhamento

### ✅ 5. Reutilizável e Escalável
- Template base que pode ser adaptado para qualquer domínio
- Funciona para análise, explicação, refatoração, etc.
- Pode ser combinado com outros padrões de prompt

---

## ⚠️ Observações Importantes

### O que este prompt faz:
- ✅ Define identidade clara da IA
- ✅ Estabelece objetivos específicos
- ✅ Garante formato consistente de resposta
- ✅ Previne respostas genéricas
- ✅ Permite personalização por contexto

### O que este prompt NÃO faz:
- ❌ Não substitui conhecimento técnico do usuário
- ❌ Não garante 100% de precisão (sempre valide)
- ❌ Não é adequado para tarefas muito abertas ou criativas

---

## 🔄 Personalização Avançada

### Para Diferentes Contextos:

**Análise de Código:**
```markdown
Critérios: Priorize segurança, performance e manutenibilidade
Formato: 1. Resumo | 2. Problemas | 3. Sugestões
```

**Explicação Didática:**
```markdown
Tom: didático e amigável
Nível de detalhe: alto
Linguagem: simples, sem jargões
```

**Refatoração:**
```markdown
Critérios: Mantenha compatibilidade, melhore legibilidade
Formato: 1. Análise | 2. Mudanças propostas | 3. Código refatorado
```

---

## 💭 Filosofia

> **"Role Prompting é como contratar um especialista: você define quem ele é, o que ele deve fazer e como ele deve pensar."**

Este prompt transforma a IA de um assistente genérico em um **especialista focado** com comportamento previsível e consistente.

---

## 🔄 Próximos Níveis (Evolução)

1. **Combinar com Chain-of-Thought** - Adicionar raciocínio passo a passo
2. **Integrar com Few-Shot** - Incluir exemplos de respostas esperadas
3. **Adicionar validação** - Critérios de qualidade para as respostas
4. **Criar biblioteca de roles** - Templates pré-configurados por área

---

## 🧠 Nota Final

Este template aplica Role Prompting de forma explícita, reduz ambiguidade e força o modelo a:

- Assumir uma identidade clara
- Adotar critérios profissionais
- Gerar respostas previsíveis e reutilizáveis

Ideal para uso contínuo no fluxo de desenvolvimento.
