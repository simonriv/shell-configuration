# 04. tmux — Paneles: dividir, navegar, redimensionar

> **Sección original:** 5.3 Dividir paneles, 5.4 Cambiar entre paneles, 5.5 Redimensionar paneles

## Configuración en ~/.tmux.conf

```tmux
# ──────────────────────────────────────────────
# DIVIDIR PANELES
# ──────────────────────────────────────────────
bind | split-window -h   # Dividir verticalmente (paneles lado a lado)
bind - split-window -v   # Dividir horizontalmente (paneles arriba/abajo)

# ──────────────────────────────────────────────
# NAVEGAR ENTRE PANELES (prefijo + flechas directas)
# ──────────────────────────────────────────────
bind Left  select-pane -L
bind Right select-pane -R
bind Up    select-pane -U
bind Down  select-pane -D

# ──────────────────────────────────────────────
# REDIMENSIONAR (prefijo + Shift + flechas)
# ──────────────────────────────────────────────
bind -r S-Left  resize-pane -L 5  # Ensanchar panel activo hacia la izquierda
bind -r S-Right resize-pane -R 5  # Ensanchar hacia la derecha
bind -r S-Up    resize-pane -U 2  # Aumentar altura
bind -r S-Down  resize-pane -D 2  # Disminuir altura
```

## Uso práctico

### Dividir paneles

| Acción | Secuencia | Resultado |
|--------|-----------|-----------|
| Vertical (lado a lado) | `Ctrl+Space` → `|` | Dos paneles, 50% cada uno |
| Horizontal (arriba/abajo) | `Ctrl+Space` → `-` | Dos paneles, 50% cada uno |

> **Nota:** `-h` = *horizontal split* = division vertical (lado a lado). `-v` = *vertical split* = división horizontal (arriba/abajo). La nomenclatura de tmux se refiere a **dónde cae la línea divisoria**.

### Navegar entre paneles

```
Ctrl+Space → soltar → ←  (izquierda)
Ctrl+Space → soltar → →  (derecha)
Ctrl+Space → soltar → ↑  (arriba)
Ctrl+Space → soltar → ↓  (abajo)
```

> Se usaron flechas directas (sin Option/Alt) porque `Option+flecha` no funcionaba correctamente en macOS.

### Redimensionar paneles

```
Ctrl+Space → soltar → Shift+←  (ensanchar izquierda, 5 celdas)
Ctrl+Space → soltar → Shift+→  (ensanchar derecha, 5 celdas)
Ctrl+Space → soltar → Shift+↑  (aumentar altura, 2 líneas)
Ctrl+Space → soltar → Shift+↓  (disminuir altura, 2 líneas)
```

- La flag `-r` permite **repetir** manteniendo la combinación (si el terminal envía repetición).
- Valores `5` y `2` son ajustables; cambia en `.tmux.conf` si prefieres otros saltos.

## Otros atajos útiles de paneles (built-in)

| Acción | Secuencia (prefijo +) |
|--------|----------------------|
| Cerrar panel actual | `x` (pide confirmación) |
| Intercambiar paneles | `{` / `}` |
| Rotar paneles | `Ctrl+o` |
| Panel a pantalla completa | `z` (toggle zoom) |
| Mostrar números de panel | `q` (luego pulsa número) |

## Verificar atajos cargados

```bash
tmux list-keys | grep -E 'split-window|select-pane|resize-pane'
```

---

> **Siguiente paso:** [04. Layouts](../04-tmux/04-layouts.md)
