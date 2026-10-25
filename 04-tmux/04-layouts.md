# 04. tmux — Layouts (distribuciones de paneles)

> **Sección original:** 5.6 Cambiar distribución

## Recorrer layouts predefinidos

```tmux
# En ~/.tmux.conf
bind Space next-layout
```

## Uso

```
Ctrl+Space → soltar → Space
```

Cada pulsación alterna entre los **5 layouts integrados** de tmux:

1. **even-horizontal** — Paneles apilados horizontalmente (igual altura)
2. **even-vertical** — Paneles lado a lado (igual ancho)
3. **main-horizontal** — Panel principal arriba (grande), resto abajo (pequeños)
4. **main-vertical** — Panel principal a la izquierda (grande), resto a la derecha
5. **tiled** — Mosaico: todos los paneles mismo tamaño, en grid

## Configurar tamaños de "main"

```tmux
# Tamaño del panel principal (en celdas/porcentaje)
set -g main-pane-width 120    # Para main-vertical
set -g main-pane-height 30    # Para main-horizontal
```

## Verificar que el binding existe

```bash
tmux list-keys | grep 'next-layout'
# Debe mostrar: bind-key Space next-layout
```

## Layouts personalizados (avanzado)

Puedes guardar/restaurar layouts con `tmux list-windows -F '#{window_layout}'` y `select-layout`, pero los 5 built-in cubren la mayoría de casos.

---

> **Siguiente paso:** [05. Recarga y diagnóstico](../04-tmux/05-recarga-diagnostico.md)
