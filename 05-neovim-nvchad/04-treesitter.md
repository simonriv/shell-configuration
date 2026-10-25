# 05. Neovim y NvChad \u2014 Tree-sitter

> **Secci\u00f3n original:** 6.4 Tree-sitter

## Qu\u00e9 es

Tree-sitter es el motor de parsing incremental que usa Neovim para resaltado de sintaxis, indentaci\u00f3n, navegaci\u00f3n de c\u00f3digo, etc.

## CLI tree-sitter

```bash
# Verificar instalaci\u00f3n
tree-sitter --version
command -v tree-sitter

# Ubicaci\u00f3n habitual (Apple Silicon + Homebrew)
/opt/homebrew/bin/tree-sitter
```

## Parsers instalados (confirmados en health check)

| Parser | Estado |
|--------|--------|
| bash | \u2705 |
| css | \u2705 |
| html | \u2705 |
| javascript | \u2705 |
| json | \u2705 |
| lua | \u2705 |
| markdown | \u2705 |
| markdown_inline | \u2705 |
| tsx | \u2705 |
| typescript | \u2705 |

## Health check en Neovim

```vim
:checkhealth nvim-treesitter
```

### Salida esperada (resumen)

- **OK**: Parsers instalados y funcionando
- **WARN**: `jsonc` parser no soportado en esa configuraci\u00f3n (no es un fallo general)
- **ERROR previo**: `ENOENT` no encontraba ejecutable `tree-sitter` \u2192 resuelto tras instalar CLI

## Instalar / actualizar parsers

Dentro de Neovim:

```vim
:TSInstall bash css html javascript json lua markdown markdown_inline tsx typescript
:TSUpdate
:TSInstallInfo
```

## Notas importantes

- La **CLI `tree-sitter`** es distinta del **módulo `nvim-treesitter`** de Neovim. Ambas son necesarias para funcionamiento completo.
- Si `:checkhealth nvim-treesitter` da error `ENOENT: tree-sitter`, instala la CLI: `brew install tree-sitter`.
- `jsonc` (JSON con comentarios) no tiene parser oficial en todas las versiones; no es bloqueante.
- Los parsers se compilan localmente; requieren `gcc`/`clang` (Xcode Command Line Tools en macOS).

## Verificar parsers activos

```vim
:TSModuleInfo
```

---

> **Siguiente paso:** [05. Mason y servidores LSP](../05-neovim-nvchad/05-mason-lsp.md)
