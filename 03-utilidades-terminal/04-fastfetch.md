# 03. Utilidades de terminal — Fastfetch al iniciar

> **Sección original:** 4.4 Fastfetch al iniciar la shell

## Propósito

Mostrar un resumen del sistema (fastfetch) **una vez por proceso de shell interactiva**, no en cada panel de tmux ni en shells no interactivas.

## Fragmento propuesto para ~/.zshrc

```zsh
# Mostrar fastfetch solo en shell interactiva, una vez por proceso
if [[ -o interactive && -z "$FASTFETCH_SHOWN" ]]; then
  export FASTFETCH_SHOWN=1
  fastfetch
fi
```

## Dónde colocarlo

Al **final** de `~/.zshrc`, después de cargar todos los plugins y configuraciones.

## Cómo funciona

| Condición | Qué hace |
|-----------|----------|
| `-o interactive` | Solo en shells interactivas (no scripts, no `scp`, no `ssh` comandos) |
| `-z "$FASTFETCH_SHOWN"` | Variable no existe (primera vez en este proceso) |
| `export FASTFETCH_SHOWN=1` | Marca que ya se mostró en este proceso |
| `fastfetch` | Ejecuta el comando |

## Comportamiento en tmux

- **Nueva sesión tmux** → nuevo proceso Zsh → **se muestra fastfetch** ✅
- **Nuevo panel/ventana en tmux existente** → mismo proceso Zsh (si `default-command` no recrea shell) → **no se muestra** ✅
- **Si se muestra en cada panel** → tu tmux crea shells de login por panel → ajusta `default-command` en `.tmux.conf`:
  ```tmux
  set -g default-command "${SHELL}"
  # En lugar de: set -g default-command "${SHELL} -l"
  ```

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
