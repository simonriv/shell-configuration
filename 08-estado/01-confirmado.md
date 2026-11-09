# 08. Estado — Confirmado

> **Sección original:** 9.1 Confirmado por la conversación
>
> **Última verificación contra la máquina de referencia:** 2026-11-09. Los archivos de configuración se compararon uno a uno con [`examples/`](../examples/README.md).

## Versiones

| Herramienta | Versión |
|-------------|---------|
| Ghostty | 1.4.0 |
| tmux | 3.8 |
| Neovim | 0.12.6 (NvChad v2.5) |
| Starship | 1.27.0 |
| fzf | 0.74.5 |
| zoxide | 0.10.0 |
| eza | 0.23.5 |
| bat | 0.26.1 |
| btop | 1.4.8 |
| lazygit | 0.66.2 |
| fastfetch | 2.70.0 |
| tree-sitter CLI | 0.27.1 |
| wattop | 0.3.1 (cask) |

## Ghostty

- [x] Configuración en `~/Library/Application Support/com.mitchellh.ghostty/config.ghostty`; `ghostty +validate-config` sin errores
- [x] Tema `TokyoNight Night`, `JetBrainsMono Nerd Font` 13 pt
- [x] `background-opacity = 0.86`, padding 10 × 8, `macos-window-buttons = hidden`
- [x] `window-inherit-working-directory = true` y `window-save-state = always`
- [x] Divisiones nativas: `Cmd+D`, `Cmd+Shift+D`, `Cmd+Shift+E` y navegación con `Cmd+Option+flechas`
- [x] Opciones a evitar: `maximize = true`, `macos-titlebar-style = tabs`

## Zsh

- [x] Orden de carga documentado en [02-zsh/04](../02-zsh/04-configuracion-zshrc.md), igual al archivo real
- [x] `bindkey '^I' expand-or-complete` tras `fzf --zsh`: Tab con completado nativo; `Ctrl+R`/`Ctrl+T`/`Alt+C` siguen con fzf
- [x] Secretos en `~/.zsh_secrets` (permisos 600), cargados desde `.zshrc`
- [x] Arranque automático de tmux en la sesión `main`
- [x] Alias de eza con iconos y `cleanup` → `ncdu`
- [x] Plugins: **zsh-completions**, **zsh-autosuggestions**, **zsh-syntax-highlighting** (Homebrew)
- [x] **Decisión explícita**: NO instalar `zsh-autocomplete`

## Starship

- [x] Preset **Jetpack** como base, con iconos Nerd Font en lenguajes, herramientas, batería y memoria
- [x] `starship print-config` sin errores

## tmux

- [x] Prefijo **Ctrl + Space**
- [x] `v` crea panel en el directorio actual y aplica `tiled` (ya no hay `|` ni `-`)
- [x] Navegación con flechas; redimensión con Shift + flechas (`-r`)
- [x] `Space` → `next-layout`
- [x] Ratón, historial de 50 000 líneas, numeración desde 1, `extended-keys`, RGB para Ghostty
- [x] Barra de estado propia (sesión a la izquierda, hora y fecha a la derecha)
- [x] Plugins con TPM: `tmux-resurrect` y `tmux-continuum` (guardado cada 15 min, restauración automática)

## Neovim / NvChad

- [x] NvChad starter v2.5 con tema `ayu_dark`
- [x] Atajos de `lua/mappings.lua`: `;` → `:` y `jk` → `Esc`
- [x] **Tree-sitter**: parsers bash, css, html, javascript, json, lua, markdown, markdown_inline, tsx, typescript; CLI en `/opt/homebrew/bin/tree-sitter`
- [x] **Mason**: astro-language-server, css-lsp, eslint-lsp, html-lsp, json-lsp, lua-language-server, stylua, tailwindcss-language-server, vtsls
- [x] **LSP habilitados** en `lua/configs/lspconfig.lua`: solo `html` y `cssls`
- [x] **Conform**: solo `stylua` para Lua; `format_on_save` desactivado
- [x] `vim-be-good` **no** instalado

## Utilidades de terminal

- [x] **fastfetch**, **btop**, **lazygit**, **bat**, **eza**, **fzf**, **zoxide**, **ncdu** instalados con Homebrew
- [x] **Wattop** instalado como cask (`brew install --cask wattop`)
- [x] Config de fastfetch en `~/.config/fastfetch/config.jsonc`; **no** se ejecuta al iniciar la shell

## Mantenimiento

- [x] Estrategia de respaldos con fecha documentada
- [x] Reglas de mantenimiento definidas

---

> **Siguiente:** [02. Pendiente de comprobar](../08-estado/02-pendiente.md)
