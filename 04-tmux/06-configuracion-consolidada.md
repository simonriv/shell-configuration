# 04. tmux \u2014 Configuraci\u00f3n consolidada (~/.tmux.conf)

> **Secci\u00f3n original:** 5.8 Ejemplo consolidado de `~/.tmux.conf`

## Bloque completo conocido

Este es el conjunto de ajustes **confirmados en la conversaci\u00f3n**. Tu archivo real puede tener m\u00e1s l\u00edneas; **compara antes de reemplazar**.

```tmux
# \u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500
# PREFIJO PERSONALIZADO
# \u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500
unbind C-b
set -g prefix C-Space
bind C-Space send-prefix

# \u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500
# DIVIDIR PANELES
# \u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500
bind | split-window -h
bind - split-window -v

# \u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500
# NAVEGAR ENTRE PANELES (prefijo + flechas)
# \u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500
bind Left  select-pane -L
bind Right select-pane -R
bind Up    select-pane -U
bind Down  select-pane -D

# \u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500
# REDIMENSIONAR (prefijo + Shift + flechas)
# \u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500
bind -r S-Left  resize-pane -L 5
bind -r S-Right resize-pane -R 5
bind -r S-Up    resize-pane -U 2
bind -r S-Down  resize-pane -D 2

# \u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500
# LAYOUTS
# \u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500
bind Space next-layout

# \u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500
# RAT\u00d3N
# \u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2502\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500
set -g mouse on

# \u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500
# OPCIONES ADICIONALES RECOMENDADAS
# \u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500
# Historial de scroll m\u00e1s grande
set -g history-limit 10000

# Numeraci\u00f3n de ventanas/paneles desde 1 (no 0)
set -g base-index 1
setw -g pane-base-index 1

# Renumerar ventanas al cerrar una
set -g renumber-windows on

# Tiempo de espera para secuencias de escape (ms)
set -g escape-time 10

# Modo vi en copy-mode
setw -g mode-keys vi

# T\u00edtulos de terminal
set -g set-titles on
set -g set-titles-string '#S:#I #W'
```

## C\u00f3mo aplicar

1. **Respaldar tu config actual:**
   ```bash
   cp ~/.tmux.conf ~/.tmux.conf.bak.$(date +%Y%m%d-%H%M%S)
   ```

2. **Comparar** (diff) con tu archivo actual:
   ```bash
   diff -u ~/.tmux.conf <(cat <<'EOF'
   # Pega aqu\u00ed el bloque de arriba
   EOF
   )
   ```

3. **Integrar** solo lo que falte, preservando tus personalizaciones.

4. **Recargar:**
   ```bash
   tmux source-file ~/.tmux.conf
   ```

5. **Verificar:**
   ```bash
   tmux list-keys | grep -E 'split-window|resize-pane|select-pane|next-layout|prefix'
   ```

## \u26a0\ufe0f Nota importante

> **Este es un bloque consolidado de los ajustes conocidos, no una copia verificada de todo el archivo existente.**
>
> Tu `~/.tmux.conf` real puede contener:
> - Plugins (tpm, catppuccin, etc.)
> - Temas de colores / statusline personalizada
> - Keybindings adicionales
> - Configuraciones de copy-mode espec\u00edficas
> - Variables de entorno
>
> **No reemplaces ciegamente.** Integra selectivamente.

---

> **Siguiente paso:** [01. Conceptos y atajos de Neovim/NvChad](../05-neovim-nvchad/01-conceptos-atajos.md)
