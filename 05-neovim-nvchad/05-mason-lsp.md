# 05. Neovim y NvChad -- Mason y servidores LSP

> **Seccion original:** 6.5 Mason y servidores LSP

## Que es Mason

Gestor de paquetes para LSP servers, linters, formatters, DAPs. Interfaz: :Mason

## Estado actual

Paquetes en `~/.local/share/nvim/mason/packages/`:

| Paquete Mason | Nombre LSP | Habilitado en `lspconfig.lua` |
|---------------|------------|-------------------------------|
| html-lsp | html | ✅ |
| css-lsp | cssls | ✅ |
| vtsls | vtsls | ❌ |
| eslint-lsp | eslint | ❌ |
| tailwindcss-language-server | tailwindcss | ❌ |
| json-lsp | jsonls | ❌ |
| lua-language-server | lua_ls | ❌ (lo usa NvChad para su propia config) |
| astro-language-server | astro | ❌ |
| stylua | — (formatter) | Usado por Conform |

## ADVERTENCIA: Distincion clave

> **Tener un servidor instalado en Mason NO ES IGUAL a que Neovim lo haya configurado o iniciado.**
>
> - Mason: "instalado" = binario descargado en ~/.local/share/nvim/mason/
> - LSP client: "activo" = Neovim lo adjunta a buffers segun filetype y config
>
> Hoy solo `html` y `cssls` están en `vim.lsp.enable(...)`. vtsls, eslint, tailwindcss, jsonls y astro están instalados pero **no se adjuntan** a ningún buffer hasta añadirlos a la lista.

## Verificar en proyecto real

```bash
cd /ruta/a/tu/proyecto
nvim .
```

Dentro de Neovim, abre un archivo .ts / .tsx real:

```vim
:LspInfo
:checkhealth vim.lsp
:Mason
:messages
```

## Para monorepo Next.js

- Abre Neovim desde la RAIZ del repositorio (donde esta package.json / turbo.json / pnpm-workspace.yaml)
- Verifica que existan tsconfig.json del proyecto
- :LspInfo debe mostrar cliente adjunto al buffer

## Nombres de paquetes Mason vs nombres LSP

| Paquete Mason | Nombre config LSP (lspconfig) |
|---------------|-------------------------------|
| vtsls | vtsls |
| typescript-language-server | ts_ls (antes tsserver) |
| eslint-lsp | eslint |
| tailwindcss-language-server | tailwindcss |
| lua-language-server | lua_ls |

> **Evita repetir nombres sin verificar en :Mason**. En pruebas, nombres como eslint, tailwindcss, html, cssls, jsonls, lua_ls fueron rechazados como paquetes Mason (el nombre del paquete difiere del nombre corto LSP).

## Configurar LSP en NvChad

En NvChad v2.5 los servidores se activan en `lua/configs/lspconfig.lua` (lo carga `lua/plugins/init.lua`). Configuración actual:

```lua
require("nvchad.configs.lspconfig").defaults()

local servers = { "html", "cssls" }
vim.lsp.enable(servers)

-- read :h vim.lsp.config for changing options of lsp servers
```

Para añadir servidores, amplía la lista con los **nombres LSP** (no los de Mason):

```lua
local servers = { "html", "cssls", "lua_ls", "vtsls", "tailwindcss", "eslint", "jsonls" }
vim.lsp.enable(servers)
```

> `M.lsp = { servers = ... }` en `chadrc.lua` era la API de versiones anteriores de NvChad; en v2.5 no tiene efecto.

Luego: :LspRestart o reinicia Neovim.

---

> **Siguiente paso:** [06. Herramientas para Next.js](../05-neovim-nvchad/06-herramientas-nextjs.md)
