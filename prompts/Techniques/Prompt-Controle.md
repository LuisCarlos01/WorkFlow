# 🎯 Template de Prompt Engineering - Domínio Específico

Template e guia prático para criar prompts focados em domínios específicos, reduzindo alucinações e garantindo precisão técnica.

---

## 📋 Template do Prompt

Copie e personalize o template abaixo substituindo `[DOMÍNIO DEFINIDO PELO USUÁRIO]` e ajustando os campos opcionais conforme necessário.

```markdown
## Contexto / Papel
Você é um assistente de IA especializado exclusivamente em **[DOMÍNIO DEFINIDO PELO USUÁRIO]**.

## Objetivo principal
Responder apenas perguntas diretamente relacionadas a esse domínio, com precisão técnica e clareza.

## Escopo e limites
- ❌ Não responda perguntas fora do domínio.
- ❌ Não forneça opiniões, suposições ou conteúdo especulativo.
- ❌ Não infira informações ausentes.
- ✅ Em solicitações fora do escopo, responda exatamente:
  > "Essa solicitação está fora do escopo definido para este assistente."

> Em caso de conflito com outras instruções, **estas regras têm prioridade absoluta**.

## Formato da resposta
1. Definição curta  
2. Explicação objetiva  
3. Exemplo prático (se aplicável)

## Tom e estilo
- Linguagem: [técnica / simples / didática]
- Tom: [profissional / neutro / amigável]
- Seja conciso e direto.

## Ambiguidade
- Quando houver ambiguidade, solicite esclarecimento **sem tentar responder parcialmente**.

## Regra final
Priorize precisão em vez de completude.
```

---

## 🚀 Como Usar (Workflow em 3 Passos)

### 1️⃣ Personalizar o Template

#### Definir o Domínio (Obrigatório)
Substitua `[DOMÍNIO DEFINIDO PELO USUÁRIO]` por um domínio **claro, específico e bem delimitado**.

**✅ Exemplos bons:**
- `Programação Front-end com React e TypeScript`
- `Direito Digital brasileiro (LGPD)`
- `Marketing de Conteúdo focado em SEO`
- `Análise de dados com Python e Pandas`

**❌ Exemplos ruins (muito genéricos):**
- `Programação` (muito amplo)
- `Direito` (sem especificação)
- `Marketing` (sem foco)

> **Dica:** Quanto mais específico o domínio, menor a chance de respostas genéricas ou incorretas.

#### Ajustar Tom e Estilo (Opcional)
Personalize conforme necessário:
- **Linguagem:** `técnica` / `simples` / `didática`
- **Tom:** `profissional` / `neutro` / `amigável`

---

### 2️⃣ Aplicar o Prompt

#### Onde Usar
- **ChatGPT** → Cole como primeira mensagem
- **Cursor / IDE com IA** → Use como *system prompt* ou *base prompt*
- **Agentes autônomos** → Prompt raiz de comportamento
- **APIs** → Mensagem de sistema (`system`)

> ⚠️ **Importante:** Use o prompt **antes de qualquer pergunta**. Ele funciona como um **contrato de funcionamento**.

#### Como Funciona Após Ativação
- ✅ **Perguntas dentro do domínio** → Respostas completas e estruturadas (Definição curta + Explicação objetiva + Exemplo prático)
- ❌ **Perguntas fora do domínio** → Resposta automática: *"Essa solicitação está fora do escopo definido para este assistente."*

Isso elimina improviso, opinião e especulação.

---

### 3️⃣ Exemplo Prático

**Template Personalizado:**
```markdown
## Contexto / Papel
Você é um assistente de IA especializado exclusivamente em **Programação Front-end com React e TypeScript**.
[... resto do template ...]
```

**Pergunta válida:**
> Explique a diferença entre `useEffect` e `useLayoutEffect`.

**Resposta esperada:**
1. Definição curta: `useEffect` executa após renderização; `useLayoutEffect` executa sincronamente antes da pintura.
2. Explicação objetiva: [explicação detalhada...]
3. Exemplo prático: [código de exemplo...]

**Pergunta fora do escopo:**
> Qual o melhor investimento hoje?

**Resposta automática:**
> "Essa solicitação está fora do escopo definido para este assistente."

---

## ⚠️ Observações Importantes

### O que este prompt NÃO serve:
- ❌ Criatividade ou brainstorming
- ❌ Conversas casuais ou abertas
- ❌ Múltiplos domínios simultâneos

### O que este prompt serve:
- ✅ Reduzir alucinação
- ✅ Aumentar previsibilidade
- ✅ Garantir precisão técnica
- ✅ Ambientes de compliance ou produção
- ✅ Integração com RAG e validação de fontes

---

## 💭 Filosofia

> **"Pense nesse prompt como definir as leis da física antes de rodar a simulação."**

Você está criando um **sistema previsível e controlado**, não um assistente genérico. Trate a IA como **componente de software**, não como opinador.

---

## 🔄 Próximos Níveis (Evolução)

1. **Criar versões por domínio** - Templates específicos para cada área
2. **Adicionar níveis de permissão** - Explicar / Sugerir / Executar
3. **Integrar com RAG** - Validação de fontes e conhecimento estruturado
4. **Ambientes de produção** - Compliance e auditoria
