# Explicação sobre One-Shot

**One-shot prompting** ocorre quando você fornece **um único exemplo** (entrada → saída) para a LLM demonstrar como realizar a tarefa. O modelo infere o padrão a partir desse exemplo e replica o formato, estilo ou comportamento em novas entradas. É o meio-termo entre Zero-Shot (sem exemplos) e Few-Shot (vários exemplos).

## 🎯 Template de One-Shot Prompting - Cursor IDE

Template de prompt baseado em **One-Shot Prompting** para orientar o modelo usando um exemplo representativo. Ideal quando uma demonstração clara supera descrições longas e reduz ambiguidade sobre formato e estilo esperados.

---

## 📋 Template do Prompt

Copie e personalize o template abaixo substituindo os campos `[INSTRUÇÃO]`, `[EXEMPLO]` e `[TAREFA NOVA]`.

```markdown
## Objetivo

[DESCREVA CLARAMENTE O QUE O MODELO DEVE FAZER]

## Exemplo (One-Shot)

Siga o padrão do exemplo abaixo:

**Entrada:**
[EXEMPLO DE ENTRADA - código, texto, dados, etc.]

**Saída esperada:**
[EXEMPLO DE SAÍDA - mostre exatamente o formato desejado]

## Sua Tarefa

Agora aplique o mesmo padrão a:

**Entrada:**
[SUA TAREFA / CÓDIGO / TEXTO NOVO]

## Regras

- ✅ Mantenha o mesmo formato do exemplo
- ✅ Aplique a mesma lógica/estrutura
- ❌ NÃO desvie do padrão estabelecido
```

---

## 🚀 Como Usar

### 1️⃣ Escolher um Exemplo Representativo

O exemplo único deve:
- Ser **claro** e **completo**
- Cobrir os **casos típicos** da tarefa
- Mostrar o **formato exato** de saída esperada
- Evitar edge cases que possam confundir o modelo

**✅ Exemplo bom (refatoração de código):**
```
Entrada: function add(a,b){return a+b}
Saída: function add(a: number, b: number): number {
  return a + b;
}
```

**❌ Exemplo ruim:**
- Muito curto ou incompleto
- Com múltiplos padrões misturados
- Ambíguo sobre o que deve ser replicado

---

### 2️⃣ Estruturar o Prompt

#### Ordem recomendada:
1. **Instrução** — O que fazer (1-2 frases)
2. **Exemplo** — Entrada + Saída (o coração do One-Shot)
3. **Tarefa** — O que processar agora
4. **Regras opcionais** — Restrições adicionais

#### Quando o exemplo deve vir antes ou depois?
- **Antes da tarefa** (recomendado): O modelo "carrega" o padrão e aplica à nova entrada
- **Depois da tarefa**: Menos comum; use quando a tarefa precisar de contexto extenso primeiro

---

### 3️⃣ Aplicar o Prompt

#### Onde Usar
- **Cursor** → Cole no chat ou como parte do contexto
- **VS Code com extensões de IA** → Inclua no prompt do comando
- **ChatGPT/Claude** → Cole diretamente na conversa
- **APIs** → Monte como mensagem de usuário com exemplo embutido

> ⚠️ **Importante:** O exemplo deve estar **no mesmo prompt** da tarefa. Se enviar em mensagens separadas, o modelo pode não manter o contexto.

---

### 4️⃣ Exemplo Prático Completo

**Cenário:** Converter comentários JSDoc para TypeScript

```markdown
## Objetivo

Converta comentários JSDoc em tipos TypeScript explícitos.

## Exemplo (One-Shot)

Siga o padrão do exemplo abaixo:

**Entrada:**
```javascript
/**
 * Soma dois números
 * @param {number} a
 * @param {number} b
 * @returns {number}
 */
function add(a, b) {
  return a + b;
}
```

**Saída esperada:**
```typescript
function add(a: number, b: number): number {
  return a + b;
}
```

## Sua Tarefa

Aplique o mesmo padrão a:

**Entrada:**
```javascript
/**
 * Busca usuário por ID
 * @param {string} id
 * @returns {Promise<User>}
 */
async function getUser(id) {
  return db.users.findById(id);
}
```

## Regras

- Remova o JSDoc e use apenas tipos TypeScript
- Mantenha a estrutura da função
- Preserve async/await quando existir
```

**Resultado:** O modelo produzirá a versão TypeScript seguindo o padrão do exemplo, com `id: string` e retorno `Promise<User>`.

---

## 💡 Por Que Este Prompt Funciona

### ✅ 1. Demonstração Concreta
- Um exemplo vale mais que parágrafos de instrução
- Elimina ambiguidade sobre formato e estilo
- O modelo "vê" exatamente o que você quer

### ✅ 2. Equilíbrio Tokens vs. Precisão
- Menos tokens que Few-Shot (1 exemplo vs. 3-5)
- Mais preciso que Zero-Shot em tarefas com formato específico
- Ideal quando um exemplo bem escolhido é suficiente

### ✅ 3. Formato e Padrão
- Excelente para: formatação, refatoração, conversão de código
- Estabelece convenções (nomenclatura, estrutura, estilo)
- Reduz variação indesejada na saída

### ✅ 4. Tarefas com Padrão Claro
- Quando a tarefa segue uma "receita" reconhecível
- Quando o exemplo cobre bem o caso de uso
- Quando Few-Shot seria overkill

### ✅ 5. Custo-Benefício
- Um exemplo bem feito evita iterações de "tente de novo"
- Acelera desenvolvimento em tarefas repetitivas
- Fácil de atualizar (troque apenas o exemplo)

---

## ⚠️ Observações Importantes

### O que este prompt faz:
- ✅ Estabelece formato específico de saída
- ✅ Demonstra padrões de código, texto ou dados
- ✅ Reduz ambiguidade com custo moderado de tokens
- ✅ Funciona bem para tarefas com padrão consistente

### O que este prompt NÃO faz:
- ❌ Não funciona bem para tarefas com muitos edge cases (use Few-Shot)
- ❌ Não é adequado quando o modelo já é excelente sem exemplo (Zero-Shot basta)
- ❌ Não substitui Few-Shot em formatos muito complexos ou hierárquicos

### Quando usar cada abordagem:

| Abordagem    | Use quando...                                      |
|-------------|----------------------------------------------------|
| **Zero-Shot** | Conhecimento do modelo é suficiente; tarefa genérica |
| **One-Shot**  | Precisa de 1 exemplo para fixar formato/estilo      |
| **Few-Shot**  | Tarefa complexa; vários exemplos reduzem erros      |

---

## 🔄 Personalização Avançada

### Para Diferentes Contextos:

**Refatoração de Código:**
```markdown
Exemplo: Código legado → Código moderno (React, TypeScript)
Foco: Estrutura, tipos, hooks
```

**Conversão de Formatos:**
```markdown
Exemplo: JSON → YAML, Markdown → HTML, etc.
Foco: Sintaxe e estrutura exata
```

**Geração de Texto:**
```markdown
Exemplo: Um commit message, um comentário, uma descrição
Foco: Tom, tamanho, estrutura
```

**Extração de Dados:**
```markdown
Exemplo: Texto livre → Objeto estruturado
Foco: Campos, tipos, aninhamento
```

---

## 💭 Filosofia

> **"One-Shot Prompting é como mostrar uma única vez a um aprendiz: 'Faça assim.' Um exemplo bem escolhido pode substituir páginas de especificação."**

One-Shot aproveita a capacidade do modelo de aprender padrões por demonstração. Um exemplo claro e representativo ancorou a expectativa e reduz a necessidade de instruções verbosas ou múltiplos exemplos.

---

## 🔄 Próximos Níveis (Evolução)

1. **Evoluir para Few-Shot** — Adicione 2-3 exemplos quando um não bastar
2. **Combinar com Zero-Shot** — Use One-Shot só em tarefas que precisam de formato
3. **Exemplos dinâmicos** — Gere o exemplo conforme o contexto do projeto
4. **Template por tipo de tarefa** — Versões específicas: refatoração, testes, docs

---

## 🧠 Nota Final

One-Shot Prompting é a ponte entre Zero-Shot e Few-Shot:

- **Zero-Shot:** Instruções apenas
- **One-Shot:** Instruções + 1 exemplo
- **Few-Shot:** Instruções + vários exemplos

Escolha One-Shot quando um exemplo representativo conseguir comunicar o padrão desejado com clareza e economia de tokens.
