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

## Configuración actual (`lua/configs/conform.lua`)

```lua
local options = {
  formatters_by_ft = {
    lua = { "stylua" },
    -- css = { "prettier" },
    -- html = { "prettier" },
  },

  -- format_on_save = {
  --   -- These options will be passed to conform.format()
  --   timeout_ms = 500,
  --   lsp_fallback = true,
  -- },
}

return options
```

Solo formatea Lua con `stylua`; `format_on_save` está desactivado. `lua/plugins/init.lua` carga este archivo con `opts = require "configs.conform"`.

## Ampliar a proyectos JS/TS (propuesta)

Sustituye `formatters_by_ft` en `lua/configs/conform.lua`:

```lua
local options = {
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
}

return options
```

## Atajos útiles

| Acción | Comando |
|--------|---------|
| Formatear buffer actual | `Space` → `f` → `m` (mapeo de NvChad) |
| Formatear con comando | `:lua require("conform").format()` |
| Ver formatters configurados | `:ConformInfo` |

## Notas

- `format_on_save` formatea al guardar (opcional, puede ser molesto en algunos proyectos).
- `lsp_fallback = true` usa LSP formatting si no hay formatter externo.
- Prettier **debe estar en el proyecto** (`node_modules/.bin/prettier` o `npx prettier`).

---

> **Siguiente paso:** [08. Transparencia en Neovim](../05-neovim-nvchad/08-transparencia.md)
