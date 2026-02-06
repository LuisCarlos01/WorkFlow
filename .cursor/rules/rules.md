---
description: Regras globais que se aplicam a todo o projeto. Foca em padrões específicos do projeto e ferramentas MCP.
globs: "**/*"
alwaysApply: true
---

# Regras Gerais do Projeto

> **📝 Nota**: Este arquivo contém regras globais. Para regras específicas, consulte:
> - [Regras de Backend](mdc:backend.md) - Padrões específicos de backend  
> - [Regras de Frontend](mdc:frontend.md) - Padrões específicos de frontend

## MCP (Model Context Protocol)

**SEMPRE** use as seguintes ferramentas MCP ao trabalhar com assistentes de IA:

- **Context7** - **SEMPRE** use Context7 para buscar documentação atualizada de bibliotecas, frameworks e código de terceiros.
- **Serena** - **SEMPRE** use Serena para semantic retrieval e editing tools. Use para busca semântica de código e operações inteligentes de edição.

**Quando usar:**
- Buscar documentação de bibliotecas/frameworks → Context7
- Buscar padrões de código semanticamente → Serena
- Realizar edições inteligentes de código → Serena
- Recuperar contexto de codebases → Serena

## Convenções Git

### Commits

Siga **Conventional Commits**: `<type>(<scope>): <subject>`

**Escopos comuns**: `api`, `web`, `ui`, `backend`, `frontend`

**Exemplo**: `feat(api): adiciona autenticacao OAuth2`

> Para detalhes completos, consulte: [Conventional Commits](https://www.conventionalcommits.org/pt-br/v1.0.0-beta.4/)

### ⚠️ Importante: Caracteres Especiais

**NÃO use** caracteres especiais em mensagens de commit (acentos, ç, til, etc.):

❌ **Errado**: `feat: adiciona configuração`  
✅ **Correto**: `feat: adiciona configuracao`

**Motivo**: O GitHub pode exibir caracteres corrompidos (ex: "configuraĂÂ£es" ao invés de "configurações").

**Caracteres a evitar**: `á é í ó ú ã õ â ê ô ç ñ à`

### 🌐 Idioma dos Commits

**SEMPRE escreva commits em português brasileiro (pt-br)**:

✅ **Correto**: `feat: adiciona autenticacao de usuarios`  
❌ **Errado**: `feat: add user authentication`

**Motivo**: Este é um repositório de estudo em pt-br. Manter consistência no idioma facilita a leitura e compreensão do histórico.

## Estrutura do Projeto

```
project-root/
├── backend/            # Ver backend.md
├── frontend/           # Ver frontend.md
├── shared/             # Código/tipos compartilhados
└── docs/               # Documentação
```

## Padrões Específicos do Projeto

<!-- Adicione aqui apenas padrões específicos do SEU projeto que a IA não conheceria -->

**Exemplo:**
- Nossa estrutura de pastas segue o padrão X
- Usamos convenção Y para nomes de arquivos
- Padrão Z para organização de código

## Referências

- [README](../README.md)
- [Backend Rules](mdc:backend.md)
- [Frontend Rules](mdc:frontend.md)

---

**Última Atualização**: [Data]
