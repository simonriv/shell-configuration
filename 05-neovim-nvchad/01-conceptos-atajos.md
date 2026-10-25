# 05. Neovim y NvChad — Conceptos y atajos

> **Secci\u00f3n original:** 6.1 Conceptos b\u00e1sicos y atajos

## Tecla l\u00edder (Leader)

En NvChad: **`Space`** (barra espaciadora)

> Todas las combinaciones `Space + ...` usan la tecla líder.

## Atajos principales

| Acci\u00f3n | Atajo / Comando |
|-----------|-----------------|
| Abrir Neovim en directorio actual | `nvim .` |
| Explorador de archivos (nvim-tree) | `Ctrl + N` |
| Buscar archivos (Telescope) | `Space` → `f` → `f` |
| Buscar texto en archivos (Telescope) | `Space` → `f` → `w` |
| Elegir tema (base46) | `Space` → `t` → `h` |
| Ver hoja de atajos (NvCheatsheet) | `:NvCheatsheet` |
| Abrir gestor de plugins (Lazy) | `:Lazy` |
| Sincronizar plugins | `:Lazy sync` |
| Ver mensajes recientes | `:messages` |
| Comprobar salud de Neovim | `:checkhealth` |

## Secuencias de Telescope (buscar)

```
Space f f  → find files (archivos)
Space f w  → live grep (texto en archivos)
Space f b  → buffers abiertos
Space f h  → help tags
Space f o  → old files (recientes)
Space f g  → git files
```

## Gestión de plugins (Lazy.nvim)

| Comando | Qué hace |
|---------|----------|
| `:Lazy` | Abre interfaz visual |
| `:Lazy sync` | Instala/actualiza/limpia plugins |
| `:Lazy update` | Actualiza plugins |
| `:Lazy clean` | Elimina plugins no declarados |
| `:Lazy profile` | Perfila tiempo de carga |

## Salud y diagn\u00f3stico

```vim
:checkhealth           " Chequeo general
:checkhealth nvim-treesitter   " Treesitter espec\u00edfico
:checkhealth vim.lsp   " LSP espec\u00edfico
:messages              " Log de errores/avisos recientes
```

## Archivos de configuraci\u00f3n clave

| Archivo | Prop\u00f3sito |
|---------|----------|
| `~/.config/nvim/lua/plugins/*.lua` | Plugins personalizados |
| `~/.config/nvim/lua/chadrc.lua` | Config principal NvChad (tema, UI) |
| `~/.config/nvim/init.lua` | Entry point (no tocar habitualmente) |

---

> **Siguiente paso:** [02. Estructura de configuraci\u00f3n](../05-neovim-nvchad/02-estructura-configuracion.md)
