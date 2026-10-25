# 05. Neovim y NvChad -- Herramientas para proyectos Next.js

> **Seccion original:** 6.6 Herramientas para proyectos Next.js

## Componentes recomendados

| Herramienta | Proposito | Paquete Mason | LSP config |
|-------------|-----------|---------------|------------|
| vtsls | LSP TypeScript/JavaScript avanzado | vtsls | vtsls |
| eslint-lsp | Diagnosticos ESLint | eslint-lsp | eslint |
| tailwindcss-language-server | Soporte Tailwind CSS | tailwindcss-language-server | tailwindcss |
| html-lsp | HTML | html-lsp | html |
| css-lsp | CSS | css-lsp | cssls |
| json-lsp | JSON | json-lsp | jsonls |
| lua-language-server | Lua (config Neovim) | lua-language-server | lua_ls |
| Prettier | Formateo (en proyecto) | -- | -- |
| LazyGit | Git TUI | -- | -- |

## Estado

> **El estado final de instalacion y configuracion de todos estos componentes NO quedo confirmado.**
>
> Instala y configura solo los que necesites, usando los nombres que muestre TU version de Mason/NvChad.

## Instalacion via Mason

1. Abre `:Mason`
2. Busca cada paquete (usa la barra de busqueda `/`)
3. Instala con `i` sobre el paquete
4. Verifica en `:Mason` que aparezca "Installed"

## Configurar en NvChad (lua/chadrc.lua)

```lua
M.lsp = {
  servers = {
    "cssls", "html", "lua_ls",
    "vtsls", "tailwindcss", "eslint",
    "jsonls"
  },
}
```

## Prettier

- **NO instales globalmente** si el proyecto ya lo declara como dependencia.
- Verifica en el proyecto:
  ```bash
  npx prettier --version
  ```
- Conform.nvim (ver siguiente seccion) puede usar Prettier del proyecto.

## LazyGit

Ya instalado como herramienta de terminal (ver [03. Utilidades](../03-utilidades-terminal/01-herramientas.md)).
Atajo en NvChad: `Space g g` (si esta configurado) o ejecuta `lazygit` en terminal.

## Flujo de trabajo sugerido

1. Abre proyecto: `cd /ruta/proyecto && nvim .`
2. Verifica LSP: `:LspInfo` en archivo .tsx
3. Formatea: `:ConformInfo` o `<leader>fm` (si mapeado)
4. Git: `:LazyGit` o terminal `lazygit`

---

> **Siguiente paso:** [07. Conform y formateo](../05-neovim-nvchad/07-conform-formateo.md)
