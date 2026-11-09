# 04. tmux — Configuración consolidada (~/.tmux.conf)

> **Sección original:** 5.8 Ejemplo consolidado de `~/.tmux.conf`

## Archivo actual

Copia exacta de `~/.tmux.conf` (también en [`examples/tmux/tmux.conf`](../examples/tmux/tmux.conf)).

```tmux
# ── Teclas principales ───────────────────────────
unbind C-b
set -g prefix C-Space
bind C-Space send-prefix

# ── Terminal y compatibilidad ────────────────────
set -g default-terminal "tmux-256color"
set -as terminal-features ",xterm-ghostty:RGB"

# Teclas modificadas: conservar compatibilidad con pegado
set -s extended-keys on
set -s extended-keys-format xterm

# ── Paneles: división automática en mosaico ──────
# Ctrl+Space, luego v: crear panel y reorganizar todos
bind v split-window -c "#{pane_current_path}" \; select-layout tiled

# Mantener el atajo para cambiar manualmente de distribución
bind Space next-layout

# ── Navegación entre paneles ─────────────────────
bind Left select-pane -L
bind Right select-pane -R
bind Up select-pane -U
bind Down select-pane -D

# ── Redimensionar paneles ────────────────────────
bind -r S-Left resize-pane -L 5
bind -r S-Right resize-pane -R 5
bind -r S-Up resize-pane -U 2
bind -r S-Down resize-pane -D 2

# ── Comportamiento ───────────────────────────────
set -g mouse on
set -g history-limit 50000
set -g renumber-windows on
set -g base-index 1
set -g pane-base-index 1
set -g focus-events on
set -sg escape-time 10

# ── Barra de estado ─────────────────────────────
set -g status-position bottom
set -g status-interval 5
set -g status-left-length 30
set -g status-right-length 45
set -g status-left '#[bold] #S '
set -g status-right '#[dim]%H:%M  %d-%m '
set -g status-style 'bg=default,fg=colour245'
set -g window-status-format ' #I:#W '
set -g window-status-current-format ' #[bold]#I:#W '

# ── Guardado y restauración de sesiones ─────────
set -g @plugin 'tmux-plugins/tmux-resurrect'
set -g @plugin 'tmux-plugins/tmux-continuum'
set -g @resurrect-capture-pane-contents 'on'
set -g @continuum-restore 'on'
set -g @continuum-save-interval '15'

# ── Gestor de plugins ───────────────────────────
run '~/.tmux/plugins/tpm/tpm'
```

## Qué hace cada bloque

| Bloque | Ajustes | Detalle |
|--------|---------|---------|
| Teclas principales | `prefix C-Space` | [02. Prefijo](02-prefijo.md) |
| Terminal | `tmux-256color`, `RGB` para `xterm-ghostty` | Color verdadero (24 bits) dentro de tmux con Ghostty |
| Teclas modificadas | `extended-keys on`, formato `xterm` | Reenvía combinaciones como `Ctrl+Shift+…` a las apps sin romper el pegado |
| Paneles | `v` → panel nuevo + `tiled` | [03. Paneles](03-paneles.md) |
| Layouts | `Space` → `next-layout` | [04. Layouts](04-layouts.md) |
| Navegación / redimensión | Flechas y `Shift` + flechas | [03. Paneles](03-paneles.md) |
| Comportamiento | Ratón, 50 000 líneas de historial, numeración desde 1, `focus-events`, `escape-time 10` | `focus-events` lo necesita Neovim para detectar cambios de archivo; `escape-time` bajo evita retraso al pulsar `Esc` |
| Barra de estado | Abajo; nombre de sesión a la izquierda; hora y fecha (`%H:%M  %d-%m`) a la derecha; fondo transparente | Se refresca cada 5 s |
| Sesiones | `tmux-resurrect` + `tmux-continuum` | Guardado cada 15 min y restauración automática ([05. Recarga y diagnóstico](05-recarga-diagnostico.md#guardar-y-restaurar-sesiones-tmux-resurrect--tmux-continuum)) |
| Plugins | `run '~/.tmux/plugins/tpm/tpm'` | **Debe ser la última línea** del archivo |

## Cómo aplicar

1. **Respaldar tu config actual:**
   ```bash
   cp ~/.tmux.conf ~/.tmux.conf.bak.$(date +%Y%m%d-%H%M%S)
   ```

2. **Comparar** con la copia del repo:
   ```bash
   diff -u ~/.tmux.conf examples/tmux/tmux.conf
   ```

3. **Instalar TPM** si no existe:
   ```bash
   git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
   ```

4. **Recargar** e instalar plugins:
   ```bash
   tmux source-file ~/.tmux.conf
   # Dentro de tmux: Ctrl+Space → I
   ```

5. **Verificar:**
   ```bash
   tmux list-keys | grep -E 'split-window|resize-pane|select-pane|next-layout'
   tmux show-options -g prefix
   ls ~/.tmux/plugins
   ```

## ⚠️ Nota importante

> `extended-keys` y `terminal-features` necesitan tmux ≥ 3.2; el entorno de referencia usa tmux 3.8. Con versiones antiguas, `tmux source-file` mostrará errores en esas líneas.

---

> **Siguiente paso:** [01. Conceptos y atajos de Neovim/NvChad](../05-neovim-nvchad/01-conceptos-atajos.md)
