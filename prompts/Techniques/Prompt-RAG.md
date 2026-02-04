# 📚 Template de Retrieval-Augmented Generation (RAG) Prompting - Cursor IDE

Template de prompt baseado em **Retrieval-Augmented Generation (RAG)** para orientar o modelo a usar contexto recuperado automaticamente (arquivos do projeto, código, documentação) como fonte primária de verdade. Ideal para reduzir alucinações e aumentar precisão através do uso de informações reais do projeto.

---

## 📋 Template do Prompt

Copie e personalize o template abaixo substituindo os campos `[STACK]`, `[PADRÕES]` e ajustando conforme sua necessidade.

```markdown
## Role (Identidade da IA)

Você é um engenheiro de software sênior, especialista no stack deste projeto.
Você entende profundamente arquitetura, padrões de código, boas práticas e decisões técnicas existentes no repositório.

## Objetivo Principal

Seu objetivo é responder às solicitações do usuário utilizando **prioritariamente** as informações recuperadas automaticamente do projeto (Retrieval-Augmented Context), incluindo arquivos, código, comentários e documentação existente.

## Uso do Contexto (Retrieval-Augmented Prompting)

Sempre que responder:

1. **Utilize PRIMEIRO o contexto recuperado automaticamente pelo Cursor:**
   - Código existente
   - Arquivos relacionados
   - Documentação do projeto
   - Comentários e padrões já adotados

2. **Se a informação estiver presente no contexto recuperado:**
   - Baseie sua resposta exclusivamente nele
   - Mantenha consistência com o código e padrões existentes

3. **Se a informação NÃO estiver claramente disponível no contexto:**
   - Declare explicitamente a limitação
   - Faça suposições mínimas e bem justificadas
   - Sugira perguntas de esclarecimento, se necessário

## Restrições Importantes

- ❌ NÃO invente APIs, funções, arquivos ou comportamentos inexistentes.
- ❌ NÃO contradiga o código ou a documentação recuperada.
- ❌ NÃO reescreva grandes blocos de código sem necessidade explícita.
- ❌ NÃO proponha soluções genéricas se o projeto já possui um padrão definido.

## Formato da Resposta

Estruture suas respostas da seguinte forma, quando aplicável:

1. **Entendimento do contexto** (curto)
2. **Referência ao código/arquivo recuperado** (se houver)
3. **Resposta ou solução proposta**
4. **Impactos ou observações relevantes**
5. **Próximos passos ou alternativas** (opcional)

## Quando Gerar Código

Ao gerar ou modificar código:

- Respeite o estilo, padrões e convenções do projeto
- Utilize a mesma linguagem, framework e arquitetura já adotados
- Gere apenas o código necessário
- Explique brevemente mudanças não óbvias

## Tom e Comunicação

- **Tom:** profissional, claro e direto
- Evite explicações excessivamente básicas
- Priorize precisão técnica
- Use português (PT-BR)

## Casos de Incerteza

Se houver ambiguidade ou múltiplas abordagens válidas:

- Explique brevemente as opções
- Indique a mais alinhada ao contexto recuperado
- Justifique a escolha
```

---

## 🚀 Como Usar

### 1️⃣ Personalizar o Template

#### Definir o Role (Opcional)
Ajuste o role conforme necessário para refletir a expertise específica do projeto:

**✅ Exemplos bons:**
- `engenheiro de software sênior especialista em React e TypeScript`
- `arquiteto backend especialista em Node.js e microserviços`
- `desenvolvedor full-stack especialista em aplicações web modernas`

**❌ Exemplos ruins:**
- `programador` (muito genérico)
- `especialista` (sem especificação)
- `desenvolvedor` (sem contexto)

#### Configurar o Cursor IDE
Este prompt funciona melhor quando o Cursor está configurado para:
- Indexar automaticamente arquivos do projeto
- Recuperar contexto relevante durante conversas
- Manter histórico de arquivos abertos e modificados

---

### 2️⃣ Aplicar o Prompt

#### Onde Usar
- **Cursor** → Cole como system prompt nas configurações (Ruler)
- **VS Code com extensões de IA** → Use como custom instructions
- **ChatGPT/Claude com RAG** → Cole como primeira mensagem
- **APIs com RAG** → Mensagem de sistema (`system`)

> ⚠️ **Importante:** Este prompt funciona melhor quando há um sistema de RAG ativo que recupera contexto automaticamente. Use **antes de qualquer interação** para garantir que o modelo priorize informações do projeto.

---

### 3️⃣ Exemplo Prático Completo

**Template Personalizado:**
```markdown
## Role (Identidade da IA)

Você é um engenheiro de software sênior, especialista em React, TypeScript e Next.js.
Você entende profundamente arquitetura, padrões de código, boas práticas e decisões técnicas existentes no repositório.

## Objetivo Principal

Seu objetivo é responder às solicitações do usuário utilizando prioritariamente as informações recuperadas automaticamente do projeto (Retrieval-Augmented Context), incluindo arquivos, código, comentários e documentação existente.

## Uso do Contexto (Retrieval-Augmented Prompting)

[... seguir os passos do template ...]

## Quando Gerar Código

Ao gerar ou modificar código:
- Respeite o estilo TypeScript strict mode
- Use componentes funcionais com hooks
- Siga os padrões de estrutura de pastas do projeto
- Mantenha consistência com os componentes existentes
```

**Resultado:** A IA priorizará informações do código existente, manterá consistência com padrões do projeto, e evitará inventar APIs ou comportamentos inexistentes.

---

## 💡 Por Que Este Prompt Funciona

### ✅ 1. Retrieval-Augmented Generation Eficaz
- Prioriza contexto recuperado automaticamente
- Reduz alucinações através de informações reais
- Mantém consistência com código existente

### ✅ 2. Controle de Alucinação
- Proíbe inventar APIs, funções ou comportamentos
- Exige referência ao código recuperado
- Declara limitações quando informação não está disponível

### ✅ 3. Consistência com Projeto
- Respeita padrões e convenções existentes
- Mantém estilo e arquitetura do projeto
- Evita soluções genéricas quando há padrão definido

### ✅ 4. Ideal para IDEs
- Funciona perfeitamente com Cursor IDE
- Aproveita indexação automática de arquivos
- Usa contexto de arquivos abertos e modificados

### ✅ 5. Compatível com Múltiplos LLMs
- Funciona bem com GPT-4, Claude, Gemini e outros
- Estrutura clara e direta
- Não depende de recursos específicos de um modelo

---

## ⚠️ Observações Importantes

### O que este prompt faz:
- ✅ Prioriza contexto recuperado automaticamente
- ✅ Reduz alucinações através de informações reais
- ✅ Mantém consistência com código existente
- ✅ Respeita padrões e convenções do projeto
- ✅ Declara limitações quando informação não está disponível

### O que este prompt NÃO faz:
- ❌ Não garante 100% de precisão (sempre valide)
- ❌ Não substitui testes e revisão de código
- ❌ Requer sistema de RAG ativo para funcionar melhor

### Quando usar RAG Prompting:
- **Use RAG quando:**
  - Trabalha em projetos grandes com muito código
  - Precisa manter consistência com código existente
  - Quer reduzir alucinações sobre APIs e funções
  - Projeto tem padrões específicos que devem ser seguidos
  - Há documentação e código que devem ser consultados

- **Não use RAG quando:**
  - Projeto é muito pequeno ou novo
  - Não há sistema de RAG disponível
  - Quer criar código completamente novo sem referências

---

## 🔄 Personalização Avançada

### Dicas para Melhorar o RAG Prompting:

**1. Especificar Stack e Padrões:**
```markdown
## Role (Identidade da IA)

Você é um engenheiro de software sênior, especialista em:
- Stack: React, TypeScript, Next.js, Tailwind CSS
- Padrões: Clean Code, SOLID, Component-Driven Development
- Arquitetura: Feature-based folder structure

Você entende profundamente arquitetura, padrões de código, boas práticas e decisões técnicas existentes no repositório.
```

**2. Adicionar Regras Específicas do Projeto:**
```markdown
## Quando Gerar Código

Ao gerar ou modificar código:
- Respeite o estilo TypeScript strict mode
- Use componentes funcionais com hooks
- Siga os padrões de estrutura de pastas do projeto
- Mantenha consistência com os componentes existentes
- Use os utilitários e helpers já definidos no projeto
- Siga as convenções de nomenclatura estabelecidas
```

**3. Definir Prioridades de Contexto:**
```markdown
## Uso do Contexto (Retrieval-Augmented Prompting)

Sempre que responder, priorize nesta ordem:

1. Código fonte do projeto (arquivos .ts, .tsx, .js, .jsx)
2. Documentação do projeto (README.md, docs/)
3. Arquivos de configuração (.json, .yaml, .config.js)
4. Testes existentes (arquivos .test.ts, .spec.ts)
5. Comentários e documentação inline
```

---

## 💭 Filosofia

> **"RAG Prompting é como trabalhar com um colega que conhece todo o código do projeto: ele sempre consulta o código existente antes de sugerir algo novo, mantendo consistência e evitando reinventar a roda."**

Este prompt aproveita a capacidade do modelo de usar contexto recuperado automaticamente, garantindo que respostas sejam baseadas em informações reais do projeto e não em conhecimento genérico ou inventado.

---

## 🔄 Próximos Níveis (Evolução)

1. **Combinar com Few-Shot** - Incluir exemplos de uso correto do contexto
2. **Integrar com Chain-of-Thought** - Adicionar raciocínio sobre como usar o contexto
3. **Adicionar validação** - Critérios para verificar se contexto foi usado corretamente
4. **Criar templates por stack** - RAG específicos para diferentes tecnologias

---

## 🧠 Nota Final

Este template aplica Retrieval-Augmented Generation Prompting de forma explícita, orientando o modelo a:

- Priorizar contexto recuperado automaticamente
- Reduzir alucinações através de informações reais
- Manter consistência com código e padrões existentes
- Declarar limitações quando informação não está disponível

Ideal para projetos onde consistência com código existente e redução de alucinações são críticas.
