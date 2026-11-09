# 05. Neovim y NvChad — Tree-sitter

> **Sección original:** 6.4 Tree-sitter

## Qué es

Tree-sitter es el motor de parsing incremental que usa Neovim para resaltado de sintaxis, indentación, navegación de código, etc.

## CLI tree-sitter

```bash
# Verificar instalación
tree-sitter --version
command -v tree-sitter

# Ubicación habitual (Apple Silicon + Homebrew)
/opt/homebrew/bin/tree-sitter
```

## Parsers instalados (confirmados en health check)

| Parser | Estado |
|--------|--------|
| bash | ✅ |
| css | ✅ |
| html | ✅ |
| javascript | ✅ |
| json | ✅ |
| lua | ✅ |
| markdown | ✅ |
| markdown_inline | ✅ |
| tsx | ✅ |
| typescript | ✅ |

## Health check en Neovim

```vim
:checkhealth nvim-treesitter
```

### Salida esperada (resumen)

- **OK**: Parsers instalados y funcionando
- **WARN**: `jsonc` parser no soportado en esa configuración (no es un fallo general)
- **ERROR previo**: `ENOENT` no encontraba ejecutable `tree-sitter` → resuelto tras instalar CLI

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
