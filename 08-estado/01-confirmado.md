# 08. Estado -- Confirmado por la conversación

> **Seccion original:** 9.1 Confirmado por la conversación

## Lo que quedó verificado en el chat/historial

### Ghostty
- [x] Se configuró desde su archivo `config.ghostty`
- [x] Ubicación: `~/Library/Application Support/com.mitchellh.ghostty/config.ghostty`
- [x] Se trabajó en transparencia (`background-opacity = 0.85`)
- [x] Se probó `macos-window-buttons = hidden`
- [x] Se identificaron opciones problemáticas: `maximize = true`, `macos-titlebar-style = tabs`

### Zsh
- [x] Starship con preset **Jetpack** configurado y funcionando
- [x] Utilidades instaladas/usadas: **zoxide**, **fzf**, **eza**
- [x] Plugins: **zsh-completions**, **zsh-autosuggestions**, **zsh-syntax-highlighting** (via Homebrew)
- [x] **Decisión explícita**: NO instalar `zsh-autocomplete`; conservar autocompletado existente

### tmux
- [x] Prefijo personalizado: **Ctrl + Space**
- [x] Divisiones: `|` (vertical), `-` (horizontal)
- [x] Navegación: flechas directas (sin Option/Alt)
- [x] Redimensionamiento: Shift + flechas (con repeat `-r`)
- [x] Layouts: `Space` para `next-layout`
- [x] Ratón habilitado: `set -g mouse on`

### Neovim / NvChad
- [x] NvChad instalado y en uso
- [x] Tecla líder: `Space`
- [x] Atajos principales: `Ctrl+N` (explorador), `Space f f` (archivos), `Space f w` (texto)
- [x] **Tree-sitter**: parsers instalados y CLI disponible
  - bash, css, html, javascript, json, lua, markdown, markdown_inline, tsx, typescript
  - CLI en `/opt/homebrew/bin/tree-sitter`
- [x] **Mason**: servidores instalados (vtsls, astro-language-server, cssls, html, lua_ls)
- [x] **Health check**: conform.nvim OK, stylua disponible

### Utilidades de terminal
- [x] **fastfetch**, **btop**, **lazygit**, **bat**, **eza**, **fzf**, **zoxide** instalados/usados
- [x] **Wattop** probado (monitor Apple Silicon / IA)

### Mantenimiento
- [x] Estrategia de respaldos con fecha documentada
- [x] Reglas de mantenimiento definidas

---

> **Siguiente:** [02. Pendiente de comprobar](../08-estado/02-pendiente.md)
