# 04. tmux — Paneles: dividir, navegar, redimensionar

> **Sección original:** 5.3 Dividir paneles, 5.4 Cambiar entre paneles, 5.5 Redimensionar paneles

## Configuración en ~/.tmux.conf

```tmux
# ──────────────────────────────────────────────
# CREAR PANELES (división automática en mosaico)
# ──────────────────────────────────────────────
# Crea un panel en el directorio actual y reorganiza todos en mosaico
bind v split-window -c "#{pane_current_path}" \; select-layout tiled

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

### Crear paneles

| Acción | Secuencia | Resultado |
|--------|-----------|-----------|
| Nuevo panel | `Ctrl+Space` → `v` | Divide el panel actual y reorganiza **todos** en mosaico (`tiled`) |
| División vertical clásica | `Ctrl+Space` → `%` | Atajo integrado de tmux (lado a lado) |
| División horizontal clásica | `Ctrl+Space` → `"` | Atajo integrado de tmux (arriba/abajo) |

- El panel nuevo abre en el **mismo directorio** que el actual (`-c "#{pane_current_path}"`).
- Con `v` no hace falta elegir orientación: tras cada panel nuevo, tmux reparte el espacio en una cuadrícula de paneles iguales.
- Para otra distribución después de crear paneles: `Ctrl+Space` → `Space` (ver [04. Layouts](04-layouts.md)).

> **Cambio respecto a la configuración anterior:** antes se usaban `|` (`split-window -h`) y `-` (`split-window -v`). Ya no están en `~/.tmux.conf`.

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
