# Specify - GitHub Spec Kit

## O que é?

**Specify** é um toolkit de desenvolvimento orientado a especificações (Spec-Driven Development) criado pelo GitHub. É uma ferramenta CLI que ajuda a configurar e gerenciar projetos que seguem a metodologia de desenvolvimento baseada em especificações.

## Comandos Principais

### `specify init`
Inicializa um novo projeto Specify a partir do template mais recente.

### `specify check`
Verifica se todas as ferramentas necessárias estão instaladas no sistema.

### `specify version`
Exibe informações sobre a versão e o sistema.

## Para que serve?

O Specify facilita o **Spec-Driven Development**, uma abordagem onde você:
1. Define especificações claras do que precisa construir
2. Usa essas especificações como guia para o desenvolvimento
3. Mantém a documentação e o código sincronizados

## Como usar?

```bash
# Ver ajuda
specify --help

# Iniciar um novo projeto
specify init

# Verificar dependências
specify check

# Ver versão instalada
specify version
```

## Instalação

```bash
uv tool install specify-cli --from git+https://github.com/github/spec-kit.git
```

## Mais informações

- Repositório: https://github.com/github/spec-kit
- Versão instalada: 0.0.22
