# 🎯 Template de Few-Shot Prompting - Cursor IDE

Template de prompt baseado em **Few-Shot Prompting** para orientar o modelo através de exemplos concretos. Ideal quando você precisa de respostas consistentes, previsíveis e alinhadas a padrões específicos do projeto.

---

## 📋 Template do Prompt

Copie e personalize o template abaixo substituindo os campos `[PAPEL]`, `[DOMÍNIO]`, `[EXEMPLOS]` e ajustando conforme sua necessidade.

```markdown
## Role (Identidade da IA)

Você é um(a) **[PAPEL_DO_MODELO]**, especialista em **[DOMÍNIO_TÉCNICO]**.
Seu objetivo é ajudar no desenvolvimento do projeto descrito abaixo, seguindo rigorosamente as regras, padrões e exemplos fornecidos.

## Contexto do Projeto

- **Tipo de projeto:** [TIPO_DE_PROJETO]
- **Linguagem(s):** [LINGUAGENS]
- **Frameworks/Bibliotecas:** [FRAMEWORKS]
- **Estilo de código:** [PADRÃO_DE_CÓDIGO]
- **Público-alvo:** [PUBLICO_ALVO]

## Regras Gerais

- ✅ Sempre siga o padrão demonstrado nos exemplos
- ✅ Seja consistente com nomenclaturas, estrutura e estilo
- ❌ Não introduza bibliotecas ou abordagens fora do escopo definido
- ✅ Prefira soluções simples, legíveis e manuteníveis
- ✅ Caso algo esteja ambíguo, faça a suposição mais conservadora possível

## Formato das Respostas

- Retorne apenas o código solicitado, salvo quando explicitamente pedido explicação
- Use comentários apenas quando necessário para clareza
- Mantenha o idioma do código e comentários em [IDIOMA_DO_CÓDIGO]

---

## Exemplos (Few-Shot Prompting)

### Exemplo 1

**Entrada do usuário:**
```
[DESCRIÇÃO_DO_PROBLEMA_1]
```

**Resposta esperada:**
```[LINGUAGEM]
[CÓDIGO_EXEMPLO_1]
```

---

### Exemplo 2

**Entrada do usuário:**
```
[DESCRIÇÃO_DO_PROBLEMA_2]
```

**Resposta esperada:**
```[LINGUAGEM]
[CÓDIGO_EXEMPLO_2]
```

---

### Exemplo 3 (Opcional)

**Entrada do usuário:**
```
[DESCRIÇÃO_DO_PROBLEMA_3]
```

**Resposta esperada:**
```[LINGUAGEM]
[CÓDIGO_EXEMPLO_3]
```

---

## Instrução Final

Com base nos exemplos acima, gere respostas que sigam **exatamente o mesmo padrão**, estrutura e nível de qualidade demonstrados.
Nunca quebre as regras estabelecidas neste documento.
```

---

## 🚀 Como Usar

### 1️⃣ Personalizar o Template

#### Definir o Role (Obrigatório)
Substitua `[PAPEL_DO_MODELO]` e `[DOMÍNIO_TÉCNICO]` por valores específicos.

**✅ Exemplos bons:**
- `engenheiro de software sênior` + `APIs REST com Node.js`
- `arquiteto backend` + `sistemas distribuídos`
- `desenvolvedor front-end` + `React e TypeScript`

**❌ Exemplos ruins:**
- `programador` (muito genérico)
- `especialista` (sem especificação)
- `desenvolvedor` (sem contexto)

#### Definir o Contexto do Projeto
Especifique claramente:
- Tipo de projeto (web app, API, mobile, etc.)
- Linguagens e frameworks utilizados
- Padrão de código seguido (Clean Code, DDD, Airbnb Style Guide, etc.)
- Público-alvo

#### Criar Exemplos Relevantes (Essencial)
Os exemplos são o coração do Few-Shot Prompting. Eles devem:

- **Ser representativos** - Cobrir casos de uso comuns do projeto
- **Seguir o padrão desejado** - Demonstrar exatamente como você quer que o código seja gerado
- **Ser consistentes** - Todos os exemplos devem seguir o mesmo estilo e estrutura
- **Ser realistas** - Baseados em problemas reais do seu projeto

**Quantidade recomendada:** 2-5 exemplos (mais exemplos = mais consistência, mas também mais tokens)

---

### 2️⃣ Aplicar o Prompt

#### Onde Usar
- **Cursor** → Cole como system prompt nas configurações (Ruler)
- **VS Code com extensões de IA** → Use como custom instructions
- **ChatGPT/Claude** → Cole como primeira mensagem
- **APIs** → Mensagem de sistema (`system`)

> ⚠️ **Importante:** Use este prompt **antes de qualquer interação**. Os exemplos definem o padrão que será seguido em todas as respostas.

---

### 3️⃣ Exemplo Prático Completo

**Template Personalizado:**
```markdown
## Role (Identidade da IA)

Você é um engenheiro de software sênior, especialista em APIs REST com Node.js e TypeScript.
Seu objetivo é ajudar no desenvolvimento do projeto descrito abaixo, seguindo rigorosamente as regras, padrões e exemplos fornecidos.

## Contexto do Projeto

- Tipo de projeto: API REST para e-commerce
- Linguagem(s): TypeScript
- Frameworks/Bibliotecas: Express, Prisma, Zod
- Estilo de código: Clean Code, SOLID principles
- Público-alvo: desenvolvedores intermediários

## Regras Gerais

- Sempre siga o padrão demonstrado nos exemplos
- Use TypeScript strict mode
- Valide todas as entradas com Zod
- Use async/await, nunca callbacks
- Trate erros com try/catch

## Formato das Respostas

- Retorne apenas o código solicitado
- Use comentários apenas quando necessário
- Mantenha o idioma do código e comentários em português

---

## Exemplos (Few-Shot Prompting)

### Exemplo 1

**Entrada do usuário:**
```
Crie um endpoint GET /products que retorna lista de produtos paginada
```

**Resposta esperada:**
```typescript
import { Request, Response } from 'express';
import { z } from 'zod';
import { prisma } from '../lib/prisma';

const querySchema = z.object({
  page: z.string().optional().default('1'),
  limit: z.string().optional().default('10'),
});

export async function getProducts(req: Request, res: Response) {
  try {
    const { page, limit } = querySchema.parse(req.query);
    const skip = (Number(page) - 1) * Number(limit);

    const products = await prisma.product.findMany({
      skip,
      take: Number(limit),
      orderBy: { createdAt: 'desc' },
    });

    return res.json({
      data: products,
      pagination: {
        page: Number(page),
        limit: Number(limit),
      },
    });
  } catch (error) {
    return res.status(400).json({ error: 'Invalid query parameters' });
  }
}
```

[... mais exemplos ...]
```

**Resultado:** A IA gerará código seguindo exatamente o padrão demonstrado nos exemplos, com validação Zod, tratamento de erros, e estrutura consistente.

---

## 💡 Por Que Este Prompt Funciona

### ✅ 1. Few-Shot Prompting Eficaz
- Exemplos concretos mostram exatamente o padrão desejado
- Modelo aprende o estilo e estrutura através de demonstração
- Reduz ambiguidade e aumenta consistência

### ✅ 2. Aprendizado por Demonstração
- Modelo identifica padrões nos exemplos
- Aplica os mesmos padrões em novas situações
- Mais eficaz que apenas descrever o padrão em texto

### ✅ 3. Consistência de Projeto
- Garante que todo código gerado siga o mesmo estilo
- Mantém nomenclaturas e estruturas consistentes
- Preserva decisões arquiteturais do projeto

### ✅ 4. Ideal para Padrões Específicos
- Quando o projeto tem convenções únicas
- Quando precisa manter consistência com código existente
- Quando padrões são difíceis de descrever apenas com palavras

### ✅ 5. Reduz Necessidade de Revisão
- Código gerado já segue o padrão esperado
- Menos necessidade de refatoração
- Acelera desenvolvimento

---

## ⚠️ Observações Importantes

### O que este prompt faz:
- ✅ Ensina padrões através de exemplos
- ✅ Garante consistência com código existente
- ✅ Reduz necessidade de correções de estilo
- ✅ Preserva decisões arquiteturais
- ✅ Funciona melhor que Zero-Shot para padrões específicos

### O que este prompt NÃO faz:
- ❌ Não substitui documentação de código
- ❌ Não garante 100% de precisão (sempre valide)
- ❌ Consome mais tokens que Zero-Shot (devido aos exemplos)

### Quando usar Few-Shot vs Zero-Shot:
- **Use Few-Shot quando:**
  - Projeto tem padrões muito específicos
  - Precisa manter consistência absoluta
  - Padrões são difíceis de descrever apenas com palavras
  - Tem exemplos claros do padrão desejado

- **Use Zero-Shot quando:**
  - Padrões são genéricos ou bem conhecidos
  - Quer economizar tokens
  - Modelo já conhece bem o domínio

---

## 🔄 Personalização Avançada

### Dicas para Criar Bons Exemplos:

**1. Variedade de Casos:**
```markdown
Exemplo 1: Operação simples (GET)
Exemplo 2: Operação com validação (POST)
Exemplo 3: Operação com relacionamentos (GET com JOIN)
```

**2. Consistência de Estilo:**
- Todos os exemplos devem usar a mesma estrutura
- Mesma forma de tratamento de erros
- Mesma convenção de nomenclatura

**3. Casos Reais:**
- Use exemplos baseados em código real do projeto
- Inclua casos de uso comuns
- Demonstre edge cases importantes

**4. Qualidade dos Exemplos:**
- Exemplos devem ser código de produção
- Sem erros ou más práticas
- Bem formatados e comentados quando necessário

---

## 💭 Filosofia

> **"Few-Shot Prompting é como treinar um estagiário: você mostra exemplos do trabalho esperado e ele aprende o padrão através da demonstração."**

Este prompt aproveita a capacidade do modelo de aprender padrões através de exemplos, garantindo que o código gerado seja consistente com o estilo e estrutura do projeto.

---

## 🔄 Próximos Níveis (Evolução)

1. **Combinar com Zero-Shot** - Usar exemplos apenas para padrões específicos
2. **Atualizar exemplos dinamicamente** - Manter exemplos atualizados com mudanças no projeto
3. **Criar biblioteca de exemplos** - Templates de exemplos por tipo de operação
4. **Integrar com linters** - Validar que código gerado segue padrões

---

## 🧠 Nota Final

Este template aplica Few-Shot Prompting de forma explícita, usando exemplos para:

- Ensinar padrões específicos do projeto
- Garantir consistência absoluta
- Reduzir necessidade de refatoração

Ideal para projetos com padrões bem definidos onde consistência é crítica.
