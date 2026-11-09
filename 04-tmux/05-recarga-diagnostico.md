# 04. tmux — Recarga y diagnóstico

> **Sección original:** 5.7 Recargar y diagnosticar

## Recargar configuración

Después de editar `~/.tmux.conf`:

```bash
# Desde dentro de tmux
tmux source-file ~/.tmux.conf

# O con atajo (si lo configuraste):
# Ctrl+Space → :source-file ~/.tmux.conf
```

## Ver atajos cargados

```bash
# Todos los keybindings
tmux list-keys

# Filtrar los relevantes
tmux list-keys | grep -E 'split-window|resize-pane|select-pane|next-layout|prefix'
```

## Gestionar sesiones

| Acción | Comando |
|--------|---------|
| Listar sesiones | `tmux ls` |
| Nueva sesión | `tmux new -s nombre` |
| Conectar a última | `tmux attach` |
| Conectar a sesión | `tmux attach -t nombre` |
| Matar sesión | `tmux kill-session -t nombre` |
| Matar servidor (todo) | `tmux kill-server` |

## Dentro de tmux (prefijo +)

| Acción | Tecla |
|--------|-------|
| Desconectar (detach) | `d` |
| Lista sesiones (interactiva) | `s` |
| Renombrar sesión | `$` |
| Nueva ventana | `c` |
| Ventana anterior/siguiente | `p` / `n` |
| Buscar ventana | `f` |
| Ver reloj | `t` |

## Ver estructura actual

```bash
# Ventanas en sesión actual
tmux list-windows

# Paneles en ventana actual
tmux list-panes

# Info completa de sesión actual
tmux display-message -p '#S:#I.#P #{pane_current_path}'
```

## Diagnosticar problemas

| Síntoma | Qué revisar |
|---------|-------------|
| Atajos no funcionan | `tmux list-keys | grep tu-atajo` — ¿está cargado? |
| Prefijo no responde | `tmux show-options -g prefix` — ¿es `C-Space`? |
| `v` no crea panel | `tmux list-keys | grep split-window` |
| Sesiones no se restauran | `ls ~/.tmux/plugins` — ¿están `tpm`, `tmux-resurrect`, `tmux-continuum`? Si no: `prefijo + I` |
| Ratón no funciona | `tmux show-options -g mouse` — ¿está `on`? |
| Config no recarga | ¿Editaste `~/.tmux.conf`? ¿Ejecutaste `source-file`? |

## Sesión `main` automática

`~/.zshrc` ejecuta `tmux new-session -A -s main` en cada shell interactiva fuera de tmux (ver [02-zsh/04](../02-zsh/04-configuracion-zshrc.md#arranque-automático-de-tmux)). Abrir Ghostty te conecta a la sesión `main`; si no existe, la crea.

## Guardar y restaurar sesiones (tmux-resurrect + tmux-continuum)

| Acción | Secuencia |
|--------|-----------|
| Guardar sesiones manualmente | `Ctrl+Space` → `Ctrl+s` |
| Restaurar manualmente | `Ctrl+Space` → `Ctrl+r` |
| Guardado automático | Cada 15 min (`@continuum-save-interval '15'`) |
| Restauración automática | Al arrancar el servidor de tmux (`@continuum-restore 'on'`) |

`@resurrect-capture-pane-contents 'on'` guarda también el contenido visible de cada panel.

### Plugins (TPM)

```bash
# Instalar TPM una sola vez
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```

| Acción | Secuencia |
|--------|-----------|
| Instalar plugins declarados | `Ctrl+Space` → `I` |
| Actualizar plugins | `Ctrl+Space` → `U` |
| Desinstalar los no declarados | `Ctrl+Space` → `Alt+u` |

## Ratón (habilitado en config)

```tmux
set -g mouse on
```

Permite: click para cambiar panel, rueda para scroll, arrastrar bordes para redimensionar.

---

> **Siguiente paso:** [06. Configuración consolidada](../04-tmux/06-configuracion-consolidada.md)
