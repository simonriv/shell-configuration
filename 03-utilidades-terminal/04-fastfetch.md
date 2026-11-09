# 03. Utilidades de terminal — Fastfetch al iniciar

> **Sección original:** 4.4 Fastfetch al iniciar la shell

## Propósito

Mostrar un resumen del sistema (fastfetch) **una vez por proceso de shell interactiva**, no en cada panel de tmux ni en shells no interactivas.

## Estado actual

> **En la configuración actual `fastfetch` no se ejecuta al iniciar la shell**: `~/.zshrc` no contiene el fragmento de abajo. La configuración visual sí existe en `~/.config/fastfetch/config.jsonc` (copia en [`examples/fastfetch/config.jsonc`](../examples/fastfetch/config.jsonc)): logo pequeño, claves en azul y módulos de sistema, CPU, GPU, memoria y disco.

## Fragmento opcional para ~/.zshrc

```zsh
# Mostrar fastfetch solo en shell interactiva, una vez por proceso
if [[ -o interactive && -z "$FASTFETCH_SHOWN" ]]; then
  export FASTFETCH_SHOWN=1
  fastfetch
fi
```

## Dónde colocarlo

Después de cargar plugins y prompt, y **dentro de la lógica de tmux**: como `~/.zshrc` arranca tmux automáticamente, lo que se imprima antes de `tmux new-session` queda tapado por la pantalla de tmux.

## Cómo funciona

| Condición | Qué hace |
|-----------|----------|
| `-o interactive` | Solo en shells interactivas (no scripts, no `scp`, no `ssh` comandos) |
| `-z "$FASTFETCH_SHOWN"` | La variable no existe en el entorno heredado |
| `export FASTFETCH_SHOWN=1` | Marca que ya se mostró; los procesos hijos la heredan |
| `fastfetch` | Ejecuta el comando |

## Comportamiento en tmux

- **Cada panel o ventana de tmux es un proceso Zsh nuevo** que vuelve a leer `~/.zshrc`.
- Los paneles heredan el entorno del **servidor** de tmux, que se fija al crearlo. Si `FASTFETCH_SHOWN=1` ya estaba exportada en la shell que arrancó el servidor, ningún panel mostrará fastfetch.
- Si quieres verlo una sola vez por sesión, prueba la condición dentro de tmux y verifica el resultado abriendo varios paneles antes de dejarlo fijo.

## Personalizar fastfetch

Configuración: `~/.config/fastfetch/config.jsonc`

```bash
# Generar config por defecto
fastfetch --gen-config

# Editar
nvim ~/.config/fastfetch/config.jsonc
```

## Probar sin modificar .zshrc

```bash
# Simular shell interactiva fresca
zsh -ic 'fastfetch'
```

---

> **Siguiente paso:** [01. Instalación de tmux](../04-tmux/01-instalacion.md)
