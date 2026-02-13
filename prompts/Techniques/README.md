# Guia de Técnicas de Prompt Engineering

Guia prático para escolher a técnica de prompt correta para cada cenário de desenvolvimento.

---

## Visão Geral das Técnicas

| Técnica | Propósito Principal | Complexidade |
|---------|---------------------|--------------|
| [Role Prompting](#role-prompting) | Definir identidade e comportamento da IA | Baixa |
| [Zero-Shot](#zero-shot-prompting) | Orientar sem exemplos, usando regras | Baixa |
| [One-Shot](#one-shot-prompting) | Demonstrar com um único exemplo representativo | Baixa |
| [Few-Shot](#few-shot-prompting) | Ensinar através de exemplos concretos | Média |
| [Guardrails](#guardrails-prompting) | Aplicar regras e restrições rígidas | Média |
| [Controle](#controle-prompting) | Limitar a um domínio específico único | Média |
| [Chain-of-Thought](#chain-of-thought-cot) | Raciocinar passo a passo | Média |
| [Reflection](#reflection-prompting) | Autoavaliar e refinar respostas | Média |
| [RAG](#rag-prompting) | Usar contexto do projeto como fonte | Média |
| [Prompt Chaining](#prompt-chaining) | Dividir em etapas sequenciais formais | Alta |
| [Self-Consistency](#self-consistency) | Gerar múltiplas soluções e escolher a melhor | Alta |
| [Tree of Thoughts](#tree-of-thoughts-tot) | Explorar múltiplos caminhos em árvore | Alta |

---

## Fluxo de Decisão Rápido

```
Qual é sua necessidade principal?
│
├─► Definir QUEM a IA é?
│   └─► Role Prompting
│
├─► Seguir REGRAS rígidas?
│   ├─► Regras gerais + restrições técnicas → Guardrails
│   └─► Limitar a um domínio único → Controle
│
├─► Ensinar um PADRÃO específico?
│   ├─► Tenho vários exemplos → Few-Shot
│   ├─► Tenho 1 exemplo representativo → One-Shot
│   └─► Não tenho exemplos → Zero-Shot
│
├─► Usar CONTEXTO do projeto?
│   └─► RAG Prompting
│
├─► Melhorar QUALIDADE da resposta?
│   ├─► Pensar antes de responder → Chain-of-Thought
│   └─► Revisar e refinar → Reflection
│
├─► Resolver problema COMPLEXO?
│   ├─► Etapas sequenciais dependentes → Prompt Chaining
│   ├─► Múltiplas soluções independentes → Self-Consistency
│   └─► Exploração em árvore de decisão → Tree of Thoughts
│
└─► Não sabe qual usar?
    └─► Comece com Role + Guardrails (base sólida)
```

---

## Quando Usar Cada Técnica

### Role Prompting
**Arquivo:** `Prompt-Role.md`

**Use quando:**
- Precisa definir a identidade, expertise e comportamento da IA
- Quer consistência de persona em toda a conversa
- Precisa de um especialista em área específica

**Cenários típicos:**
- Iniciar qualquer projeto (base para outras técnicas)
- Análise de código por "arquiteto sênior"
- Explicações por "mentor técnico"

**Combina bem com:** Guardrails, Few-Shot, Chain-of-Thought

---

### Zero-Shot Prompting
**Arquivo:** `Prompt-ZeroShot.md`

**Use quando:**
- O modelo já conhece bem o domínio
- Não tem exemplos específicos do padrão desejado
- Quer economizar tokens
- Padrões são genéricos ou bem conhecidos

**Cenários típicos:**
- Tarefas comuns de desenvolvimento
- Explicações de conceitos padrão
- Refatoração seguindo boas práticas gerais

**Combina bem com:** Role, Guardrails

---

### One-Shot Prompting
**Arquivo:** `Prompt-OneShot.md`

**Use quando:**
- Precisa de 1 exemplo para fixar formato ou estilo
- Um exemplo representativo comunica o padrão com clareza
- Quer economia de tokens (menos que Few-Shot)
- Formato específico de saída é importante

**Cenários típicos:**
- Conversão de formatos (JSDoc → TypeScript, JSON → YAML)
- Refatoração seguindo padrão demonstrado
- Geração de texto com estrutura específica
- Extração de dados em formato definido

**Combina bem com:** Role, Guardrails

---

### Few-Shot Prompting
**Arquivo:** `Prompt-FewShot.md`

**Use quando:**
- Projeto tem padrões muito específicos
- Precisa de consistência absoluta com código existente
- Padrões são difíceis de descrever apenas com palavras
- Tem 2-5 exemplos claros do padrão desejado

**Cenários típicos:**
- Gerar código seguindo estilo específico do projeto
- Criar endpoints seguindo padrão existente
- Manter convenções de nomenclatura únicas

**Combina bem com:** Role, Guardrails, RAG

---

### Guardrails Prompting
**Arquivo:** `Prompt-Guardrails.md`

**Use quando:**
- Precisa de regras e restrições rígidas
- Quer evitar comportamento inesperado
- Restrições técnicas são críticas
- Ambiente requer controle rigoroso

**Cenários típicos:**
- Desenvolvimento em produção
- Projetos com padrões obrigatórios (ESLint, TypeScript strict)
- Evitar bibliotecas não aprovadas
- Prevenir código inseguro

**Combina bem com:** Role, Few-Shot, RAG

---

### Controle Prompting
**Arquivo:** `Prompt-Controle.md`

**Use quando:**
- Precisa limitar a IA a um domínio único e específico
- Quer rejeitar completamente perguntas fora do escopo
- Ambiente de compliance ou produção
- Máxima previsibilidade é necessária

**Cenários típicos:**
- Assistente especializado em uma tecnologia
- Bot de suporte técnico focado
- Integração com RAG e validação de fontes

**Combina bem com:** RAG

---

### Chain-of-Thought (CoT)
**Arquivo:** `Prompt-CoT.md`

**Use quando:**
- Problema é complexo e requer análise
- Há múltiplas abordagens possíveis
- Precisa considerar trade-offs
- Validação de suposições é crítica

**Cenários típicos:**
- Debugging de problemas complexos
- Decisões arquiteturais
- Análise de código com múltiplos aspectos
- Implementações que requerem raciocínio

**Combina bem com:** Role, Guardrails, Reflection

---

### Reflection Prompting
**Arquivo:** `Prompt-Reflection.md`

**Use quando:**
- Precisa de código de alta qualidade
- Quer evitar erros e refatorações futuras
- Clareza e manutenibilidade são críticas
- Soluções devem ser bem pensadas

**Cenários típicos:**
- Code review automatizado
- Refatoração de código crítico
- Implementação de features complexas
- Código que vai para produção

**Combina bem com:** Role, Chain-of-Thought, Guardrails

---

### RAG Prompting
**Arquivo:** `Prompt-RAG.md`

**Use quando:**
- Trabalha em projetos grandes com muito código
- Precisa manter consistência com código existente
- Quer reduzir alucinações sobre APIs e funções
- Projeto tem padrões específicos que devem ser seguidos

**Cenários típicos:**
- Desenvolvimento em projetos existentes
- Manutenção de código legado
- Extensão de funcionalidades existentes
- Qualquer tarefa onde contexto do projeto é importante

**Combina bem com:** Role, Guardrails, Few-Shot

---

### Prompt Chaining
**Arquivo:** `Prompt-Chaining.md`

**Use quando:**
- Tarefa é complexa e requer múltiplas etapas
- Cada etapa depende da anterior
- Quer garantir processo completo e estruturado
- Precisa de rastreabilidade do processo

**Cenários típicos:**
- Implementação de features completas
- Criação de APIs do zero
- Projetos com múltiplas fases
- Tarefas que requerem análise → planejamento → execução → revisão

**Combina bem com:** Role, Chain-of-Thought, Reflection

---

### Self-Consistency
**Arquivo:** `Prompt-SelfConsistency.md`

**Use quando:**
- Problema tem múltiplas soluções válidas
- Precisa da solução mais robusta
- Trade-offs são complexos e importantes
- Quer reduzir viés e aumentar confiabilidade

**Cenários típicos:**
- Decisões arquiteturais importantes
- Escolha entre tecnologias/abordagens
- Problemas com múltiplas soluções válidas
- Quando precisa de justificativa fundamentada

**Combina bem com:** Role, Chain-of-Thought

---

### Tree of Thoughts (ToT)
**Arquivo:** `Prompt-ToT.md`

**Use quando:**
- Problema é muito complexo e requer análise profunda
- Há múltiplas soluções arquiteturais possíveis
- Trade-offs são complexos e importantes
- Decisão tem impacto de longo prazo

**Cenários típicos:**
- Arquitetura de sistemas
- Escolha de stack tecnológico
- Refatoração de grande escala
- Problemas que requerem exploração sistemática

**Combina bem com:** Role, Self-Consistency

---

## Matriz de Decisão por Cenário

| Cenário | Técnica Primária | Técnicas Complementares |
|---------|------------------|-------------------------|
| Iniciar projeto novo | Role | Guardrails |
| Manter código existente | RAG | Role, Guardrails |
| Gerar código com padrão específico | Few-Shot | Role, Guardrails |
| Fixar formato com 1 exemplo | One-Shot | Role, Guardrails |
| Debugging complexo | Chain-of-Thought | Role, Reflection |
| Code review | Reflection | Role, Guardrails |
| Decisão arquitetural | Tree of Thoughts | Role, Self-Consistency |
| Escolha entre abordagens | Self-Consistency | Role, Chain-of-Thought |
| Implementação de feature completa | Prompt Chaining | Role, Guardrails |
| Assistente focado em tecnologia | Controle | RAG |
| Tarefa simples e direta | Zero-Shot | Role |

---

## Combinações Recomendadas

### Base Sólida (recomendado para todos)
```
Role + Guardrails
```
Define quem a IA é e estabelece regras básicas de comportamento.

### Desenvolvimento em Projeto Existente
```
Role + RAG + Guardrails
```
Usa contexto do projeto, mantém consistência, segue regras.

### Código com Padrões Específicos
```
Role + Few-Shot + Guardrails
```
Ensina padrões através de exemplos, mantém regras rígidas.

### Problemas Complexos
```
Role + Chain-of-Thought + Reflection
```
Pensa antes de responder, revisa e refina a solução.

### Decisões Arquiteturais
```
Role + Tree of Thoughts + Self-Consistency
```
Explora múltiplos caminhos, gera várias abordagens, escolhe a melhor.

### Implementação Completa
```
Role + Prompt Chaining + Guardrails
```
Segue processo formal de etapas, mantém regras durante todo o fluxo.

---

## Como Escrever Bons Prompts

### Processo Iterativo
Escrever bons prompts é iterativo e progressivo. Pratique e teste variações — a qualidade melhora com a experiência.

### Divida Tarefas Grandes
Quebre tarefas complexas em partes menores e específicas. Facilita o entendimento e melhora os resultados.

### Teste Variações
Experimente diferentes formas de escrever a mesma instrução. Pequenas mudanças podem gerar grandes melhorias.

### Instruções Claras
Use linguagem direta e precisa. Evite ambiguidades que possam confundir a LLM.

---

## Técnicas Avançadas de Prompting

### Use Comandos Diretos
Use ordens claras no prompt: **Você deve**, **Faça**, **Não faça**. Estabelece autoridade e clareza na instrução.

### Adicione Consequências
Inclua consequência clara: **se você não fizer X, sua tarefa será rejeitada**. Reforça a importância de seguir as instruções.

### Seja Específico
Inclua detalhes técnicos relevantes: ferramentas necessárias, estruturas de arquivos, padrões específicos a seguir.

### Use Markdown + XML
Estruture os prompts com markdown para formatação e XML para seções específicas. Estudos da **Anthropic** comprovam a eficácia.

---

### Formatos de Prompts

| Formato Markdown | Formato XML     |
|------------------|-----------------|
| Task             | `<Task>`        |
| Instruction      | `<Instruction>` |
| Requirements     | `<Requeriments>`|
| Context          | `<Context>`     |
| Output           | `<Output>`      |

---

### Roles

Dentro de uma conversa ou prompt, temos diferentes **roles**. Em LLMs, a conversa é estruturada com papéis para diferenciar quem está falando.

| Role       | Descrição                                                        |
|------------|------------------------------------------------------------------|
| **SYSTEM** | Define o comportamento geral e as instruções de alto nível       |
| **USER**   | Representa a mensagem do usuário (pergunta ou instrução)         |
| **ASSISTANT** | Representa a resposta gerada pelo modelo de IA                |

---

### Tecnicas Avançadas: **Pensar antes de responder**

Para encorajar o modelo a realizar um raciocínio mais aprofundado antes de gerar a resposta, você pode incluir instruções específicas que o guiam a um processo de pensamento mais deliberado.

#### Pense Antes de Responder

Instrua o modelo a **pense bem antes de responder**. Isso o incentiva a considerar diferentes perspectivas e a elaborar uma resposta mais completa e ponderada, em vez de uma reação imediata.

#### Raciocine sobre Múltiplas Soluções

Peça ao modelo para **raciocinar sobre múltiplas soluções antes de executar sua tarefa**. Esta técnica promove a exploração de alternativas e a seleção da melhor opção, o que é especialmente útil para problemas complexos.

Essas frases chave funcionam como metainstruções, guiando o processo interno do modelo e resultando em saídas mais robustas e de maior qualidade, aumentando a chance de obter a resposta ideal.

---
## Resumo de Uma Linha

| Técnica | Resumo |
|---------|--------|
| **Role** | Define QUEM a IA é |
| **Zero-Shot** | Orienta SEM exemplos |
| **One-Shot** | Demonstra com 1 EXEMPLO |
| **Few-Shot** | Ensina COM exemplos |
| **Guardrails** | Aplica REGRAS rígidas |
| **Controle** | Limita a UM domínio |
| **CoT** | PENSA antes de responder |
| **Reflection** | REVISA antes de entregar |
| **RAG** | Usa CONTEXTO do projeto |
| **Chaining** | Divide em ETAPAS formais |
| **Self-Consistency** | Gera MÚLTIPLAS soluções |
| **ToT** | Explora em ÁRVORE de decisão |

---

## Dica Final

> **Não sabe por onde começar?**
> 
> Use **Role + Guardrails** como base. Adicione outras técnicas conforme a necessidade específica do problema.

A maioria dos cenários de desenvolvimento se beneficia dessa combinação básica, e você pode evoluir adicionando técnicas complementares conforme a complexidade aumenta.
