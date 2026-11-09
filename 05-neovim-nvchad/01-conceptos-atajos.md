# 05. Neovim y NvChad — Conceptos y atajos

> **Sección original:** 6.1 Conceptos básicos y atajos

## Tecla líder (Leader)

En NvChad: **`Space`** (barra espaciadora)

> Todas las combinaciones `Space + ...` usan la tecla líder.

## Atajos principales

| Acción | Atajo / Comando |
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
| Modo comando (`mappings.lua`) | `;` (equivale a `:`) |
| Salir de inserción (`mappings.lua`) | `jk` (equivale a `Esc`) |
| Formatear archivo (Conform) | `Space` → `f` → `m` |

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

## Salud y diagnóstico

```vim
:checkhealth           " Chequeo general
:checkhealth nvim-treesitter   " Treesitter específico
:checkhealth vim.lsp   " LSP específico
:messages              " Log de errores/avisos recientes
```

## Archivos de configuración clave

| Archivo | Propósito |
|---------|----------|
| `~/.config/nvim/lua/plugins/*.lua` | Plugins personalizados |
| `~/.config/nvim/lua/chadrc.lua` | Config principal NvChad (tema, UI) |
| `~/.config/nvim/init.lua` | Entry point (no tocar habitualmente) |

---

> **Siguiente paso:** [02. Estructura de configuración](../05-neovim-nvchad/02-estructura-configuracion.md)
