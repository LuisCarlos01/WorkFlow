# 📝 Template de Geração de Guidelines - Cursor IDE

Template de prompt baseado em **Análise de Projeto** para gerar arquivos `guideline.md` com diretrizes claras e práticas para contribuir, manter e evoluir projetos. Ideal para documentação técnica automatizada e padronização de contribuições.

---

## 📋 Template do Prompt

Copie e personalize o template abaixo substituindo os campos `[PROJETO]`, `[CONTEXTO]` e ajustando conforme sua necessidade.

```markdown
## Role (Identidade da IA)

Você é um **arquiteto de software sênior** e **especialista em documentação técnica**.

## Objetivo

Analisar o projeto fornecido (estrutura de pastas, código, README e demais arquivos relevantes) e gerar um arquivo chamado `guideline.md` com diretrizes claras e práticas para contribuir, manter e evoluir o projeto.

## Contexto

{DESCREVA AQUI O CONTEXTO DO PROJETO, REPOSITÓRIO OU RESTRIÇÕES ESPECÍFICAS}

## Instruções de Análise

Antes de escrever, analise cuidadosamente:

1. **Estrutura do projeto** - Organização de pastas e arquivos
2. **Linguagem(ns) e frameworks** - Stack técnica utilizada
3. **Padrões de código existentes** - Convenções já estabelecidas
4. **Convenções de nomenclatura** - Nomes de arquivos, variáveis, funções
5. **Scripts, configurações e ferramentas** - Linters, testes, CI/CD

## Conteúdo do Guideline

O arquivo `guideline.md` deve conter, quando aplicável:

- Visão geral do projeto
- Padrões de código e boas práticas adotadas
- Convenções de nomenclatura (arquivos, pastas, variáveis, funções)
- Organização da estrutura de pastas
- Boas práticas para commits e versionamento
- Diretrizes para criação de novas features
- Diretrizes para correção de bugs
- Padrões de testes (se existirem)
- Regras de formatação e linting
- Boas práticas de documentação
- O que evitar no projeto (anti-patterns observados ou riscos comuns)

## Formato da Resposta

1. **Gere apenas** o conteúdo do arquivo `guideline.md`
2. **Utilize Markdown** bem estruturado (títulos, listas, blocos de código)
3. **Seja conciso**, mas completo
4. **Não inclua** explicações fora do arquivo

## Restrições

- ❌ Não invente regras que não possam ser inferidas do projeto
- ❌ Não inclua comentários meta sobre sua análise
- ❌ Não assuma requisitos não informados
- ✅ Baseie todas as diretrizes **exclusivamente no que for observado**
```

---

## 🚀 Como Usar

### 1️⃣ Personalizar o Template

#### Definir o Contexto (Obrigatório)
Substitua `{DESCREVA AQUI O CONTEXTO...}` por informações específicas do projeto.

**✅ Exemplos bons:**
- `Repositório monorepo com múltiplos pacotes npm`
- `API REST em Python com FastAPI, usando Docker e PostgreSQL`
- `Aplicação React Native com Expo, seguindo Atomic Design`

**❌ Exemplos ruins:**
- `Projeto web` (muito genérico)
- `Aplicação` (sem especificação)
- `Código` (sem contexto)

#### Ajustar Conteúdo do Guideline (Opcional)
Personalize as seções do guideline conforme as necessidades do projeto:
- Remova seções que não se aplicam
- Adicione seções específicas (ex.: "Padrões de acessibilidade", "Internacionalização")
- Especifique prioridades para o time

---

### 2️⃣ Aplicar o Prompt

#### Onde Usar
- **Cursor** → Cole como system prompt e forneça o código do projeto
- **VS Code com extensões de IA** → Use como custom instructions
- **ChatGPT/Claude** → Cole como primeira mensagem junto com estrutura do projeto
- **APIs** → Mensagem de sistema (`system`) + contexto do projeto

> ⚠️ **Importante:** Forneça **acesso ao código** ou **estrutura do projeto** para que a análise seja precisa. Quanto mais contexto, melhor o guideline gerado.

---

### 3️⃣ Exemplo Prático Completo

**Template Personalizado:**
```markdown
## Role (Identidade da IA)

Você é um arquiteto de software sênior e especialista em documentação técnica.

## Objetivo

Analisar este projeto Node.js e gerar um arquivo `guideline.md` com diretrizes para contribuição.

## Contexto

API REST em Node.js com Express, TypeScript, Prisma ORM e Jest para testes. O projeto segue Clean Architecture e está em fase de crescimento do time.

## Conteúdo do Guideline

Foque especialmente em:
- Padrões de commits (Conventional Commits)
- Estrutura de pastas (Clean Architecture)
- Padrões de testes unitários e integração
- Code review guidelines
- Processo de criação de PRs

## Formato da Resposta

Gere apenas o conteúdo do arquivo `guideline.md` em Markdown estruturado.
```

**Resultado:** A IA analisará o projeto e gerará um guideline completo, documentando padrões existentes e estabelecendo diretrizes claras para o time.

---

## 💡 Por Que Este Prompt Funciona

### ✅ 1. Análise Baseada em Evidências
- Força a IA a analisar o projeto antes de escrever
- Evita suposições e diretrizes genéricas
- Documenta o que realmente existe no código

### ✅ 2. Estrutura Abrangente
- Cobre todos os aspectos relevantes de um guideline
- Flexível para diferentes tipos de projetos
- Fácil de personalizar por seção

### ✅ 3. Formato Padronizado
- Gera documentação consistente
- Markdown bem estruturado
- Pronto para uso imediato no repositório

### ✅ 4. Ideal para Onboarding
- Facilita entrada de novos desenvolvedores
- Documenta conhecimento implícito do time
- Reduz tempo de ramp-up

### ✅ 5. Manutenção Simplificada
- Pode ser regenerado quando o projeto evolui
- Identifica inconsistências e anti-patterns
- Promove padronização contínua

---

## ⚠️ Observações Importantes

### O que este prompt faz:
- ✅ Analisa estrutura e padrões existentes no projeto
- ✅ Gera documentação baseada em evidências
- ✅ Identifica convenções já adotadas pelo time
- ✅ Documenta boas práticas e anti-patterns
- ✅ Cria guideline pronto para uso no repositório

### O que este prompt NÃO faz:
- ❌ Não inventa padrões não observados no código
- ❌ Não substitui decisões arquiteturais do time
- ❌ Não garante 100% de cobertura (revisar sempre)

### Quando usar este prompt:
- **Use quando:**
  - Projeto precisa de documentação de contribuição
  - Time está crescendo e precisa de padronização
  - Quer automatizar geração de guidelines
  - Precisa documentar conhecimento implícito

- **Não use quando:**
  - Projeto é muito pequeno ou trivial
  - Não há código suficiente para análise
  - Quer criar padrões do zero (sem base existente)

---

## 🔄 Personalização Avançada

### Para Diferentes Tipos de Projeto:

**Frontend (React/Vue/Angular):**
```markdown
## Conteúdo do Guideline

Foque em:
- Estrutura de componentes
- Padrões de state management
- Convenções de CSS/styling
- Testes de componentes
- Acessibilidade
```

**Backend (API REST):**
```markdown
## Conteúdo do Guideline

Foque em:
- Estrutura de endpoints
- Padrões de validação
- Tratamento de erros
- Autenticação/autorização
- Documentação de API
```

**Monorepo:**
```markdown
## Conteúdo do Guideline

Foque em:
- Organização de pacotes
- Dependências compartilhadas
- Convenções de versionamento
- Scripts de build/deploy
- Integração entre pacotes
```

---

## 💭 Filosofia

> **"Um bom guideline documenta o que o time já faz bem e estabelece diretrizes para manter a qualidade conforme o projeto cresce."**

Este prompt transforma conhecimento implícito em documentação explícita, garantindo que padrões e convenções sejam preservados e compartilhados.

---

## 🔄 Próximos Níveis (Evolução)

1. **Combinar com análise de PRs** - Incluir padrões de code review
2. **Integrar com linters** - Gerar configurações baseadas no guideline
3. **Versionar guidelines** - Manter histórico de evolução
4. **Automatizar validação** - CI/CD que valida aderência ao guideline

---

## 🧠 Nota Final

Este template aplica análise de projeto de forma explícita, orientando a IA a:

- Observar antes de documentar
- Basear-se em evidências do código
- Gerar documentação prática e acionável
- Evitar suposições e generalizações

Ideal para times que precisam documentar padrões existentes e estabelecer diretrizes de contribuição.

---

## 💡 Dica Extra (Opcional)

Para garantir que o guideline seja **atualizado regularmente**, adicione no seu CI/CD:

```yaml
# .github/workflows/update-guideline.yml
name: Update Guidelines
on:
  schedule:
    - cron: '0 0 1 * *' # Primeiro dia de cada mês
  workflow_dispatch:

jobs:
  update:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Regenerate guideline
        run: |
          # Integração com API de IA para regenerar guideline
          echo "Regenerate guideline.md based on current codebase"
```
