---
description: Padrões específicos de frontend do projeto. Foca em convenções de componentes, estado e UI específicas deste projeto.
globs: "**/*.{tsx,jsx,ts,js}" | "**/components/**" | "**/pages/**" | "**/app/**" | "**/src/**"
alwaysApply: false
---

# Regras de Desenvolvimento Frontend

> **📝 Instruções**: Edite este arquivo com padrões ESPECÍFICOS do seu projeto. Remova exemplos genéricos e adicione apenas o que é único ao seu projeto.

## Stack e Ferramentas

<!-- Especifique sua stack específica -->
**Framework**: [ex.: Next.js 15, React 19]
**UI Library**: [ex.: shadcn/ui, Material-UI]
**State Management**: [ex.: Zustand, React Query]
**Styling**: [ex.: Tailwind CSS, CSS Modules]

> **Referência**: Para padrões gerais de React/TypeScript, a IA já conhece. Foque apenas no que é específico do seu projeto.

## Padrões Específicos do Projeto

### Estrutura de Pastas

<!-- Descreva a estrutura ESPECÍFICA do seu projeto -->
```
frontend/
├── src/
│   ├── [sua estrutura específica]
```

**Regras específicas:**
- [Adicione regras específicas da sua organização]

### Convenções de Nomenclatura

<!-- Apenas convenções que fogem do padrão -->
- **Componentes**: [ex.: PascalCase, localização específica]
- **Hooks**: [ex.: Prefixo "use", organização]
- **Utils**: [ex.: Onde ficam, como são organizados]

### Estrutura de Componentes

<!-- Padrão específico usado no projeto -->
```typescript
// Exemplo do padrão ESPECÍFICO usado
export function ComponentName() {
  // Ordem específica: imports, types, hooks, handlers, render
}
```

**Referência**: Veja exemplos canônicos em `src/components/[exemplo].tsx`

### Gerenciamento de Estado

<!-- Padrão específico do projeto -->
- **Estado Local**: [ex.: Quando usar useState vs useReducer]
- **Estado Global**: [ex.: Context vs Zustand vs Redux - quando usar cada]
- **Estado do Servidor**: [ex.: React Query configurado como]

**Referência**: Veja exemplos em `src/store/` ou `src/hooks/`

### Estilização

<!-- Padrão específico -->
- **Abordagem**: [ex.: Tailwind, CSS Modules, Styled Components]
- **Temas**: [ex.: Como temas são organizados]
- **Responsividade**: [ex.: Breakpoints específicos]

**Referência**: Veja exemplos em `src/styles/` ou componentes em `src/components/ui/`

### Busca de Dados

<!-- Padrão específico de data fetching -->
```typescript
// Exemplo do padrão ESPECÍFICO usado
export function useCustomHook() {
  // Seu padrão específico
}
```

**Referência**: Veja exemplos em `src/hooks/` ou `src/services/`

### Componentes UI

<!-- Biblioteca e padrões específicos -->
- **Biblioteca Base**: [ex.: shadcn/ui, Material-UI]
- **Customização**: [ex.: Onde componentes customizados ficam]
- **Composição**: [ex.: Padrão de composição usado]

**Referência**: Veja exemplos canônicos em `src/components/ui/`

## Padrões Específicos

<!-- Apenas padrões que são específicos do seu projeto -->
- **Roteamento**: [ex.: File-based routing, rotas protegidas]
- **Formulários**: [ex.: React Hook Form + Zod configurado como]
- **Validação**: [ex.: Padrão específico de validação]

**Referência**: Veja exemplos canônicos em:
- `src/pages/[exemplo].tsx`
- `src/components/forms/[exemplo].tsx`

## Anti-Padrões Específicos

<!-- Apenas anti-padrões específicos do seu projeto -->
- ❌ Não faça X porque [razão específica do projeto]
- ❌ Evite Y porque [razão específica do projeto]

## Referências

- [README Frontend](../README.md)
- [Biblioteca de Componentes](../docs/components.md)
- [Design System](../docs/design-system.md)
- [Exemplos Canônicos](../src/)

---

**Última Atualização**: [Data]
