# 05. Neovim y NvChad -- Mason y servidores LSP

> **Seccion original:** 6.5 Mason y servidores LSP

## Que es Mason

Gestor de paquetes para LSP servers, linters, formatters, DAPs. Interfaz: :Mason

## Estado observado

| Servidor | En Mason | Cliente LSP activo |
|----------|----------|-------------------|
| vtsls | Instalado | No confirmado |
| astro-language-server | Instalado | No confirmado |
| cssls | Instalado | Habilitado |
| html | Instalado | Habilitado |
| lua_ls | Instalado | Habilitado |

## ADVERTENCIA: Distincion clave

> **Tener un servidor instalado en Mason NO ES IGUAL a que Neovim lo haya configurado o iniciado.**
>
> - Mason: "instalado" = binario descargado en ~/.local/share/mason/
> - LSP client: "activo" = Neovim lo adjunta a buffers segun filetype y config
>
> En :checkhealth vim.lsp solo aparecian cssls, html, lua_ls como configuraciones habilitadas. vtsls y astro no tenian clientes activos.

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

En lua/chadrc.lua (seccion lsp):

```lua
M.lsp = {
  servers = { "cssls", "html", "lua_ls", "vtsls", "tailwindcss", "eslint" },
  -- configuracion extra por servidor:
  -- config = {
  --   vtsls = { settings = { ... } },
  -- }
}
```

Luego: :LspRestart o reinicia Neovim.

---

> **Siguiente paso:** [06. Herramientas para Next.js](../05-neovim-nvchad/06-herramientas-nextjs.md)
