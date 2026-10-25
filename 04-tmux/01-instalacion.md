# 04. tmux — Instalación

> **Sección original:** 5.1 Instalar y comprobar

## Instalar

```bash
brew install tmux
```

## Verificar

```bash
tmux -V
# Debe mostrar versión 3.x (ej. tmux 3.5a)

command -v tmux
# Debe mostrar /opt/homebrew/bin/tmux (Apple Silicon)
```

## Archivo de configuración

Ubicación: `~/.tmux.conf`

```bash
# Editar
nvim ~/.tmux.conf

# Ver si existe
ls -la ~/.tmux.conf
```

## Primera ejecución

```bash
# Crear sesión inicial
tmux new -s trabajo

# Dentro de tmux: prefijo (Ctrl+Space) luego 'd' para desconectar
# Volver a conectar:
tmux attach -t trabajo
```

## Ver sesiones/ventanas/paneles

```bash
tmux ls              # Listar sesiones
tmux list-windows    # Ventanas en sesión actual
tmux list-panes      # Paneles en ventana actual
```

---

> **Siguiente paso:** [02. Prefijo personalizado](../04-tmux/02-prefijo.md)
