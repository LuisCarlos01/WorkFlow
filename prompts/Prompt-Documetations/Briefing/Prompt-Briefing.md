# 📋 Template de Geração de Briefing Profissional - Cursor IDE

Template de prompt baseado em **coleta estruturada de informações** para gerar briefings completos e profissionais. Ideal para transformar ideias em documentos executáveis para equipes de marketing, design, tecnologia, audiovisual e produto digital.

---

## 📝 Template do Prompt

Copie e personalize o template abaixo substituindo os campos `{{variável}}` conforme sua necessidade.

```markdown
## Role (Identidade da IA)

Você é um **especialista em criação de briefings profissionais**, com experiência em {{área_principal_do_projeto}} (ex.: marketing, design, tecnologia, audiovisual, produto digital).

## Objetivo

Transformar informações fornecidas pelo usuário em um **briefing claro, estruturado, acionável e pronto para execução** para {{tipo_de_projeto}} que será utilizado por {{publico_que_vai_executar}}.

## Contexto

{{DESCREVA AQUI O CONTEXTO DO PROJETO OU RESTRIÇÕES ESPECÍFICAS}}

## Informações do Projeto

O usuário fornecerá as seguintes informações. Caso algo esteja ausente, **sinalize explicitamente**:

- **Nome do projeto:** {{nome_do_projeto}}
- **Descrição resumida:** {{descricao_do_projeto}}
- **Problema ou necessidade a ser resolvida:** {{problema_principal}}
- **Objetivo principal:** {{objetivo_principal}}
- **Objetivos secundários (se houver):** {{objetivos_secundarios}}
- **Público-alvo:** {{publico_alvo}}
- **Tom e estilo desejado:** {{tom_e_estilo}}
- **Mensagem-chave:** {{mensagem_principal}}
- **Diferenciais ou referências:** {{referencias_ou_benchmarks}}
- **Restrições (prazo, orçamento, tecnologia, regras):** {{restricoes}}
- **Prazo final:** {{prazo}}
- **Critérios de sucesso:** {{criterios_de_sucesso}}

## Estrutura Esperada do Briefing

O briefing deve seguir esta estrutura:

1. **Visão Geral do Projeto** - Descrição resumida e objetivo estratégico
2. **Contexto e Problema** - Situação atual e necessidade identificada
3. **Objetivos** - Principal e secundários
4. **Público-Alvo** - Perfil detalhado do público
5. **Mensagem e Tom de Comunicação** - Como se comunicar
6. **Escopo do Projeto** - O que será entregue
7. **Referências e Inspirações** - Benchmarks e inspirações
8. **Restrições e Premissas** - Limitações e condições
9. **Cronograma** - Prazos e marcos importantes
10. **Critérios de Sucesso** - Como medir o resultado

## Diretrizes

- Use linguagem clara e objetiva
- Não invente informações que não tenham sido fornecidas
- Sinalize lacunas de informação de forma explícita
- Adapte o nível de detalhe para {{nivel_de_detalhamento}} (ex.: executivo, técnico, criativo)

## Formato da Resposta

1. **Gere apenas** o conteúdo do briefing completo
2. **Utilize Markdown** bem estruturado (títulos, listas, blocos)
3. **Sem emojis** no briefing final
4. **Pronto para compartilhar** com equipes profissionais

## Restrições

- ❌ Não invente dados não fornecidos
- ❌ Não inclua comentários meta sobre sua análise
- ❌ Não assuma informações não confirmadas
- ✅ Baseie-se exclusivamente nas informações fornecidas
```

---

## 🚀 Como Usar

### 1️⃣ Personalizar o Template

#### Definir Contexto e Área (Obrigatório)

Substitua as variáveis `{{}}` por informações específicas do projeto.

**✅ Exemplos bons:**
- **Área:** `marketing digital e campanhas de performance`
- **Tipo de projeto:** `campanha de lançamento de produto SaaS`
- **Público executor:** `agência de publicidade e time interno de growth`

**❌ Exemplos ruins:**
- **Área:** `marketing` (muito genérico)
- **Tipo de projeto:** `projeto` (sem especificação)
- **Público executor:** `equipe` (sem contexto)

#### Ajustar Nível de Detalhamento (Opcional)

Personalize o nível de detalhe conforme o público:
- **Executivo:** Foco em resultados e ROI
- **Técnico:** Detalhes de implementação e especificações
- **Criativo:** Elementos visuais e narrativa

---

### 2️⃣ Aplicar o Prompt

#### Onde Usar

- **Cursor** → Cole como system prompt e forneça informações do projeto
- **VS Code com extensões de IA** → Use como custom instructions
- **ChatGPT/Claude** → Cole como primeira mensagem
- **APIs** → Mensagem de sistema (`system`) + dados do projeto

> ⚠️ **Importante:** Quanto mais informações fornecidas, mais completo e preciso será o briefing gerado.

---

### 3️⃣ Exemplo Prático Completo

**Template Personalizado:**

```markdown
## Role (Identidade da IA)

Você é um especialista em criação de briefings profissionais, com experiência em marketing digital e produto SaaS.

## Objetivo

Transformar informações fornecidas em um briefing completo para campanha de lançamento de produto SaaS que será utilizado por agência de marketing e time interno.

## Contexto

Startup em fase de lançamento do primeiro produto no mercado. Time pequeno, orçamento limitado, foco em crescimento rápido e validação de produto-mercado.

## Informações do Projeto

- **Nome do projeto:** Launch Campaign - TaskFlow Pro
- **Descrição:** Campanha de lançamento de ferramenta de gestão de tarefas para times remotos
- **Problema:** Times remotos perdem produtividade por falta de visibilidade e comunicação
- **Objetivo principal:** Alcançar 1000 usuários pagos nos primeiros 3 meses
- **Público-alvo:** Tech leads e product managers de startups e scale-ups
- **Tom:** Profissional, direto, orientado a resultados
- **Mensagem-chave:** "Gerencie projetos remotos com clareza total"
- **Restrições:** Orçamento de R$ 50k, prazo de 2 meses
- **Critérios de sucesso:** 1000 sign-ups, 200 conversões trial-to-paid, CAC < R$ 100
```

**Resultado:** A IA gerará um briefing completo e estruturado, pronto para ser usado pela equipe de execução.

---

## 💡 Por Que Este Prompt Funciona

### ✅ 1. Role Explícito
- Define claramente a identidade da IA
- Aumenta consistência e qualidade da resposta
- Contextualiza a expertise necessária

### ✅ 2. Separação Clara de Contexto, Dados e Instruções
- Reduz ambiguidade
- Melhora interpretação por diferentes LLMs
- Facilita debugging e ajustes

### ✅ 3. Template com Campos Injetáveis (`{{}}`)
- Permite reutilização
- Facilita automação
- Integração com formulários e sistemas

### ✅ 4. Estrutura de Saída Bem Definida
- Garante previsibilidade
- Padroniza documentação
- Facilita leitura e execução

### ✅ 5. Controle de Escopo e Alucinação
- Instrui a não inventar dados
- Sinaliza lacunas explicitamente
- Mantém fidelidade às informações

### ✅ 6. Escalável e Adaptável
- Funciona para múltiplos tipos de projetos
- Ajustável por domínio e público
- Flexível em nível de detalhamento

---

## ⚠️ Observações Importantes

### O que este prompt faz:
- ✅ Estrutura informações dispersas em briefing profissional
- ✅ Identifica e sinaliza lacunas de informação
- ✅ Padroniza formato e linguagem
- ✅ Adapta tom ao público executor
- ✅ Gera documento pronto para execução

### O que este prompt NÃO faz:
- ❌ Não inventa informações não fornecidas
- ❌ Não substitui planejamento estratégico
- ❌ Não garante viabilidade do projeto
- ❌ Não substitui validação de mercado

### Quando usar este prompt:
- **Use quando:**
  - Precisa formalizar ideia em documento estruturado
  - Vai contratar agência ou freelancer
  - Precisa alinhar expectativas com time
  - Quer padronizar briefings da empresa

- **Não use quando:**
  - Projeto é muito vago ou inicial (fazer discovery primeiro)
  - Falta informações críticas sobre o problema
  - Precisa de pesquisa de mercado antes

---

## 🔄 Personalização Avançada

### Para Diferentes Domínios:

**Marketing e Publicidade:**
```markdown
## Estrutura Esperada

Foque em:
- Posicionamento e diferenciação
- Canais de distribuição
- Métricas de performance (CTR, CPA, ROI)
- Guidelines de marca
```

**Design e UX:**
```markdown
## Estrutura Esperada

Foque em:
- User personas detalhadas
- Jornada do usuário
- Requisitos de acessibilidade
- Sistema de design existente
```

**Tecnologia e Produto:**
```markdown
## Estrutura Esperada

Foque em:
- Requisitos funcionais e não-funcionais
- Stack tecnológica
- Integrações necessárias
- Critérios de aceitação técnicos
```

**Audiovisual e Conteúdo:**
```markdown
## Estrutura Esperada

Foque em:
- Conceito criativo
- Formato e duração
- Locações e recursos necessários
- Roteiro e storyboard
```

---

## 💭 Filosofia

> **"Um bom briefing transforma ideias em ação, alinha expectativas e reduz retrabalho."**

Este prompt transforma informações dispersas em documentação estruturada, garantindo que todos os stakeholders tenham clareza sobre o que será executado.

---

## 🔄 Próximos Níveis (Evolução)

1. **Briefing iterativo** - Incluir perguntas de refinamento automáticas
2. **Integração com ferramentas** - Conectar com Notion, Google Docs, Jira
3. **Templates por vertical** - Versões especializadas por indústria
4. **Validação automática** - Checklist de completude do briefing

---

## 🧠 Extensões Possíveis

### Variações do Template:

- **One-page briefing** - Versão executiva resumida
- **Briefing técnico** - Foco em especificações e implementação
- **Briefing criativo** - Ênfase em conceito e narrativa
- **Briefing de pitch** - Para apresentações e vendas

### Integrações:

- **Formulários web** - Coletar informações automaticamente
- **Automações** - Gerar briefing via API
- **Workflows** - Integrar com processo de aprovação
- **Versionamento** - Rastrear mudanças no briefing

---

## 💡 Dica Extra

Para projetos complexos, use o prompt em **modo iterativo**:

1. **Primeira rodada:** Gere briefing inicial com informações disponíveis
2. **Revisão:** Identifique lacunas e perguntas
3. **Segunda rodada:** Refine briefing com informações adicionais
4. **Validação:** Compartilhe com stakeholders para feedback final

Isso garante briefings mais completos e alinhados com expectativas de todos os envolvidos.

---

**Criado para transformar ideias em execução com clareza e profissionalismo.**
