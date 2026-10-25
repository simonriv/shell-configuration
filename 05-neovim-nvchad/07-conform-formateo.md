# 05. Neovim y NvChad -- Conform y formateo

> **Seccion original:** 6.7 Conform y formateo

## Qué es Conform.nvim

Formateador asíncrono para Neovim. Se integra con LSP y herramientas externas (prettier, stylua, etc.).

## Estado confirmado (health check)

- `conform.nvim`: **Saludable** (OK)
- `stylua`: **Disponible** para formatear Lua

> **NO confirma** que Prettier esté instalado o conectado a archivos Next.js.

## Verificar Prettier en proyecto

```bash
npx prettier --version
```

## Configurar Conform (en lua/chadrc.lua o lua/plugins/conform.lua)

```lua
return {
  "stevearc/conform.nvim",
  opts = {
    formatters_by_ft = {
      lua = { "stylua" },
      javascript = { "prettier" },
      typescript = { "prettier" },
      javascriptreact = { "prettier" },
      typescriptreact = { "prettier" },
      json = { "prettier" },
      css = { "prettier" },
      html = { "prettier" },
      markdown = { "prettier" },
    },
    format_on_save = {
      timeout_ms = 500,
      lsp_fallback = true,
    },
  },
}
```

## Atajos útiles

| Acción | Comando |
|--------|---------|
| Formatear buffer actual | `:ConformInfo` |
| Formatear rango visual | `:ConformInfo` (en modo visual) |
| Ver formatters configurados | `:ConformInfo` |

## Notas

- `format_on_save` formatea al guardar (opcional, puede ser molesto en algunos proyectos).
- `lsp_fallback = true` usa LSP formatting si no hay formatter externo.
- Prettier **debe estar en el proyecto** (`node_modules/.bin/prettier` o `npx prettier`).

---

> **Siguiente paso:** [08. Transparencia en Neovim](../05-neovim-nvchad/08-transparencia.md)
