# Exemplo Pratico - Comandos GitHub

Exemplo de uso completo dos comandos de integracao GitHub em um cenario real.

## Cenario: Implementando Feature de Autenticacao OAuth2

### Contexto

Voce implementou uma nova feature de autenticacao OAuth2 no projeto. A feature inclui:
- Backend: Endpoints de autenticacao
- Frontend: Componentes de login
- Documentacao atualizada
- Testes unitarios

### Commits Realizados

```bash
$ git log --oneline main..HEAD

a1b2c3d feat(auth): adiciona endpoints OAuth2
b4e5f6g feat(ui): adiciona componente de login OAuth2  
c7d8e9h docs(auth): atualiza documentacao de autenticacao
i0j1k2l test(auth): adiciona testes para OAuth2
```

---

## Caso 1: PR Simples e Direta

**Situacao:** Feature completa, sem trabalho pendente identificado.

### Passo 1: Executar o Comando

```
/open-pr implementa autenticacao OAuth2 conforme especificado em AUTH-001
```

### Passo 2: Revisar Proposta

O assistente analisa e retorna:

```
### Analise das Mudancas

Branch: feature/oauth2-auth
Base: main
Commits: 4

Mudancas encontradas:
- src/backend/auth/oauth2.controller.ts (novo)
- src/backend/auth/oauth2.service.ts (novo)
- src/frontend/components/LoginOAuth2.tsx (novo)
- docs/authentication.md (modificado)
- tests/auth/oauth2.test.ts (novo)

### Proposta de PR

**Titulo:** feat(auth): adiciona autenticacao OAuth2

**Descricao:**

## Resumo

Implementa sistema de autenticacao OAuth2 com suporte a Google e GitHub providers.

## Mudancas Principais

- Adiciona endpoints de autenticacao OAuth2 (`/auth/oauth2/login`, `/auth/oauth2/callback`)
- Implementa servico de autenticacao com estrategias para Google e GitHub
- Cria componente de UI para login OAuth2 com botoes para providers
- Atualiza documentacao com fluxo de autenticacao OAuth2
- Adiciona suite de testes unitarios para endpoints e servico

## Tipo de Mudanca

- [x] Nova funcionalidade (feat)
- [ ] Correcao de bug (fix)
- [ ] Refatoracao (refactor)

## Checklist

- [x] Codigo segue padroes do projeto
- [x] Testes adicionados/atualizados
- [x] Documentacao atualizada
- [x] Sem conflitos com a branch base

Deseja criar a PR com estas informacoes? (sim/nao/ajustar)
```

### Passo 3: Confirmar

```
sim
```

### Passo 4: Resultado

```
✓ PR criada com sucesso!

URL: https://github.com/LuisCarlos01/WorkFlow/pull/42
Branch: feature/oauth2-auth -> main
Titulo: feat(auth): adiciona autenticacao OAuth2

Deseja adicionar revisores ou labels? (sim/nao)
```

---

## Caso 2: PR com Issues para Trabalho Futuro

**Situacao:** Feature implementada, mas voce identificou melhorias e debitos tecnicos durante o desenvolvimento.

### Passo 1: Executar o Comando

```
/pr-with-issues implementa OAuth2 - identificadas melhorias para v2
```

### Passo 2: Revisar Proposta

```
### Analise das Mudancas
[mesma analise do Caso 1]

### Issues Identificadas

Durante a implementacao, foram identificadas oportunidades de melhoria:

**Issues Sugeridas a serem criadas:**

1. [enhancement] Adicionar suporte a mais OAuth2 providers
   - Tipo: enhancement
   - Prioridade: media
   - Labels: ["enhancement", "auth"]
   - Descricao: Expandir suporte OAuth2 para incluir Facebook, Microsoft e Apple
   
2. [tech-debt] Refatorar estrategias OAuth2 para pattern Strategy
   - Tipo: tech-debt
   - Prioridade: baixa
   - Labels: ["tech-debt", "refactor", "auth"]
   - Descricao: Melhorar arquitetura usando pattern Strategy para strategies de providers

3. [enhancement] Adicionar refresh token automatico
   - Tipo: enhancement
   - Prioridade: alta
   - Labels: ["enhancement", "auth", "security"]
   - Descricao: Implementar renovacao automatica de tokens antes da expiracao

### Proposta de PR

**Titulo:** feat(auth): adiciona autenticacao OAuth2

**Descricao:**

## Resumo

Implementa sistema de autenticacao OAuth2 com suporte inicial a Google e GitHub.

## Mudancas Principais

- Adiciona endpoints de autenticacao OAuth2
- Implementa servico com estrategias Google e GitHub
- Cria componente UI para login OAuth2
- Atualiza documentacao de autenticacao
- Adiciona testes unitarios completos

## Issues Relacionadas

Issues criadas para melhorias futuras:
- #43: [enhancement] Adicionar suporte a mais OAuth2 providers
- #44: [tech-debt] Refatorar estrategias OAuth2 para pattern Strategy  
- #45: [enhancement] Adicionar refresh token automatico

## Tipo de Mudanca

- [x] Nova funcionalidade (feat)

## Checklist

- [x] Codigo segue padroes do projeto
- [x] Testes adicionados/atualizados
- [x] Documentacao atualizada
- [x] Issues criadas para trabalho futuro

Deseja criar a PR e as issues sugeridas? (sim/nao/ajustar)
```

### Passo 3: Confirmar

```
sim
```

### Passo 4: Resultado

```
✓ Issues criadas com sucesso:

- #43: [enhancement] Adicionar suporte a mais OAuth2 providers
  URL: https://github.com/LuisCarlos01/WorkFlow/issues/43
  
- #44: [tech-debt] Refatorar estrategias OAuth2 para pattern Strategy
  URL: https://github.com/LuisCarlos01/WorkFlow/issues/44
  
- #45: [enhancement] Adicionar refresh token automatico
  URL: https://github.com/LuisCarlos01/WorkFlow/issues/45

✓ PR criada com sucesso!

URL: https://github.com/LuisCarlos01/WorkFlow/pull/42
Branch: feature/oauth2-auth -> main
Issues referenciadas: #43, #44, #45

Total:
- 1 PR criada
- 3 issues criadas
```

---

## Caso 3: Criando Issues a partir de Tech Spec

**Situacao:** Voce tem uma Tech Spec para dashboard de metricas e quer criar issues para distribuir o trabalho.

### Tech Spec Existente

```
docs/tasks/dashboard-metricas/techspec.md
```

### Passo 1: Executar o Comando

```
/create-issues docs/tasks/dashboard-metricas/techspec.md
```

### Passo 2: Revisar Proposta

```
### Tech Spec Analisada

Arquivo: docs/tasks/dashboard-metricas/techspec.md
Secoes identificadas:
- Componente de Graficos
- API de Metricas
- Cache de Dados
- Testes

### Issues Propostas

1. [feat] Implementar componente de graficos de metricas
   - Tipo: enhancement
   - Prioridade: alta
   - Labels: ["enhancement", "frontend", "ui"]
   - Descricao: Criar componente React para visualizacao de graficos com Chart.js
   - Arquivos: src/components/MetricsChart.tsx
   
2. [feat] Criar API de metricas
   - Tipo: enhancement
   - Prioridade: alta
   - Labels: ["enhancement", "backend", "api"]
   - Descricao: Implementar endpoints REST para consulta de metricas
   - Arquivos: src/api/metrics.controller.ts, src/api/metrics.service.ts
   
3. [enhancement] Implementar cache de metricas com Redis
   - Tipo: enhancement
   - Prioridade: media
   - Labels: ["enhancement", "backend", "performance"]
   - Descricao: Adicionar camada de cache Redis para metricas frequentes
   - Arquivos: src/cache/metrics.cache.ts
   
4. [test] Adicionar testes para dashboard de metricas
   - Tipo: testing
   - Prioridade: alta
   - Labels: ["testing", "frontend", "backend"]
   - Descricao: Suite completa de testes unitarios e integracao
   - Arquivos: tests/metrics/

Deseja criar estas issues? (sim/nao/ajustar/selecionar)
```

### Passo 3: Selecionar Issues

```
criar 1, 2 e 4 - issue 3 sera para v2
```

### Passo 4: Resultado

```
✓ Issues criadas com sucesso:

- #46: [feat] Implementar componente de graficos de metricas
  URL: https://github.com/LuisCarlos01/WorkFlow/issues/46
  Labels: enhancement, frontend, ui
  
- #47: [feat] Criar API de metricas
  URL: https://github.com/LuisCarlos01/WorkFlow/issues/47
  Labels: enhancement, backend, api
  
- #48: [test] Adicionar testes para dashboard de metricas
  URL: https://github.com/LuisCarlos01/WorkFlow/issues/48
  Labels: testing, frontend, backend

Total: 3 issues criadas

Issue #3 (cache Redis) nao foi criada - planejada para v2.
Deseja criar uma issue de planejamento para rastrear isso? (sim/nao)
```

---

## Caso 4: Bug Tracking Rapido

**Situacao:** Voce encontrou bugs durante testes e precisa registra-los rapidamente.

### Passo 1: Executar o Comando

```
/create-issues 2 bugs criticos encontrados em testes de producao
```

### Passo 2: Descrever Bugs

```
Descreva os bugs encontrados:
```

Resposta:

```
1. Formulario de login nao valida email corretamente - aceita emails invalidos
2. API de metricas retorna 500 quando usuario nao tem permissao
```

### Passo 3: Revisar Proposta

```
### Issues Propostas

1. [bug] Validacao de email incorreta no formulario de login
   - Tipo: bug
   - Prioridade: alta
   - Labels: ["bug", "frontend", "ui", "priority: high"]
   - Descricao:
   
## Descricao do Bug

Formulario de login aceita emails invalidos durante validacao.

## Comportamento Esperado

Formulario deve validar formato de email usando regex padrao RFC 5322.

## Comportamento Atual

Emails como "user@" ou "@domain.com" sao aceitos.

## Passos para Reproduzir

1. Acessar pagina de login
2. Digitar email invalido (ex: "teste@")
3. Formulario aceita e tenta fazer login

## Ambiente

- Componente: LoginForm.tsx
- Versao: v1.2.0

2. [bug] API de metricas retorna 500 para usuarios sem permissao
   - Tipo: bug
   - Prioridade: alta
   - Labels: ["bug", "backend", "api", "priority: high"]
   - Descricao:
   
## Descricao do Bug

Endpoint /api/metrics retorna status 500 quando usuario nao tem permissao.

## Comportamento Esperado

Deve retornar status 403 Forbidden com mensagem apropriada.

## Comportamento Atual

Retorna status 500 Internal Server Error.

## Passos para Reproduzir

1. Fazer login como usuario sem role "admin"
2. Fazer GET request para /api/metrics
3. Receber 500 ao inves de 403

## Ambiente

- Endpoint: /api/metrics
- Controller: metrics.controller.ts

Deseja criar estas issues? (sim/nao/ajustar)
```

### Passo 4: Confirmar e Criar

```
sim
```

### Passo 5: Resultado

```
✓ Issues criadas com sucesso:

- #49: [bug] Validacao de email incorreta no formulario de login
  URL: https://github.com/LuisCarlos01/WorkFlow/issues/49
  Labels: bug, frontend, ui, priority: high
  
- #50: [bug] API de metricas retorna 500 para usuarios sem permissao
  URL: https://github.com/LuisCarlos01/WorkFlow/issues/50
  Labels: bug, backend, api, priority: high

Total: 2 bugs registrados

Deseja criar uma PR para corrigir estes bugs? (sim/nao)
```

---

## Dicas de Uso

### Combine Comandos

```bash
# 1. Crie issues do planejamento
/create-issues docs/tasks/feature-x/techspec.md

# 2. Implemente a feature
# [desenvolver codigo]

# 3. Crie PR referenciando as issues
/pr-with-issues implementa feature-x conforme issues 46, 47, 48
```

### Use Contexto Adicional

Sempre que possivel, forneça contexto nos comandos:

```bash
# Bom
/open-pr

# Melhor
/open-pr relacionado ao ticket PROJ-123

# Ainda melhor
/open-pr implementa autenticacao OAuth2 conforme spec PROJ-123
```

### Revise Antes de Confirmar

Os comandos sempre apresentam uma proposta antes de executar. Aproveite para:
- Revisar titulos e descricoes
- Ajustar labels
- Adicionar/remover issues
- Refinar o conteudo

---

## Conclusao

Estes comandos automatizam tarefas repetitivas de integracao com GitHub, permitindo que voce foque no desenvolvimento enquanto mantem rastreabilidade e documentacao de qualidade.

**Proximos passos:**
- Experimente os comandos no seu workflow
- Ajuste templates conforme necessidade do projeto
- Compartilhe feedback para melhorias
