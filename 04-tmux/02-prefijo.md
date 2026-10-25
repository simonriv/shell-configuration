# 04. tmux — Prefijo personalizado

> **Sección original:** 5.2 Prefijo

## Prefijo configurado: Ctrl + Space

```tmux
# En ~/.tmux.conf
unbind C-b           # Liberar prefijo por defecto (Ctrl+b)
set -g prefix C-Space # Establecer Ctrl+Space
bind C-Space send-prefix # Permitir enviar Ctrl+Space a apps anidadas
```

## Cómo usar

1. Pulsa **`Ctrl + Space`** (mantén Ctrl, pulsa Space, suelta ambas)
2. Suelta las teclas
3. Pulsa la **tecla de acción** (ej: `|`, `-`, flecha, `d`, `c`, etc.)

## Ejemplos

| Acción | Secuencia |
|--------|-----------|
| Dividir vertical | `Ctrl+Space` → soltar → `|` |
| Dividir horizontal | `Ctrl+Space` → soltar → `-` |
| Panel izquierda | `Ctrl+Space` → soltar → `←` |
| Panel derecha | `Ctrl+Space` → soltar → `→` |
| Desconectar sesión | `Ctrl+Space` → soltar → `d` |
| Nueva ventana | `Ctrl+Space` → soltar → `c` |
| Enviar Ctrl+Space literal | `Ctrl+Space` → soltar → `Ctrl+Space` |

## Por qué Ctrl+Space

- **Ergonómico:** Accesible con una mano (pulgar en Space, meñique/índice en Ctrl)
- **No choca** con atajos comunes de editors (Vim usa Ctrl+Space para autocompletar en algunos plugins, pero tmux lo intercepta primero)
- **Estándar creciente** en configuraciones modernas

## Verificar que está activo

Dentro de tmux:

```bash
tmux show-options -g prefix
# Debe mostrar: prefix C-Space
```

---

> **Siguiente paso:** [03. Paneles](../04-tmux/03-paneles.md)
