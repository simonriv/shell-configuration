# 01. Ghostty — Configuración

> **Sección original:** 1.2 Archivo de configuración

## Ubicación del archivo

En macOS, Ghostty busca su configuración en:

```text
~/Library/Application Support/com.mitchellh.ghostty/config.ghostty
```

## Crear carpeta y archivo si no existen

```bash
mkdir -p "$HOME/Library/Application Support/com.mitchellh.ghostty"
touch "$HOME/Library/Application Support/com.mitchellh.ghostty/config.ghostty"
```

## Editar la configuración

Con Neovim (o tu editor preferido):

```bash
nvim "$HOME/Library/Application Support/com.mitchellh.ghostty/config.ghostty"
```

## Formato del archivo

El archivo usa formato simple `clave = valor`; las líneas con `#` son comentarios.

## Configuración actual

Copia completa en [`examples/ghostty/config.ghostty`](../examples/ghostty/config.ghostty).

```ini
#Tema y Tipografía
theme = TokyoNight Night
font-family = JetBrainsMono Nerd Font
font-size = 13

background-opacity = 0.86
window-padding-x = 10
window-padding-y = 8
window-inherit-working-directory = true
macos-window-buttons = hidden

# Restauración de ventanas, tabs y divisiones
window-save-state = always

# Divisiones nativas
keybind = cmd+d=new_split:auto
keybind = cmd+shift+d=new_split:down
keybind = cmd+shift+e=equalize_splits

# Navegación entre divisiones
keybind = cmd+alt+left=goto_split:left
keybind = cmd+alt+right=goto_split:right
keybind = cmd+alt+up=goto_split:top
keybind = cmd+alt+down=goto_split:bottom
```

| Opción | Efecto |
|--------|--------|
| `theme = TokyoNight Night` | Esquema de colores integrado en Ghostty (`ghostty +list-themes` lista los disponibles) |
| `font-family` / `font-size` | JetBrainsMono Nerd Font a 13 pt; la Nerd Font es necesaria para los iconos de Starship, eza y NvChad |
| `window-padding-x` / `-y` | Margen interior de 10 × 8 px |
| `window-inherit-working-directory` | Las ventanas, tabs y divisiones nuevas abren en el directorio actual |
| `window-save-state = always` | Al reabrir Ghostty restaura ventanas, tabs y divisiones |

### Divisiones nativas de Ghostty

Son independientes de los paneles de tmux: dividen la ventana de Ghostty, y cada división tiene su propia shell.

| Atajo | Acción |
|-------|--------|
| `Cmd + D` | Nueva división (Ghostty elige la orientación) |
| `Cmd + Shift + D` | Nueva división hacia abajo |
| `Cmd + Shift + E` | Igualar tamaños |
| `Cmd + Option + ←/→/↑/↓` | Moverse a la división en esa dirección |

> **Nota:** `~/.zshrc` arranca tmux en cada shell interactiva (`tmux new-session -A -s main`), así que cada división nueva se conecta a la misma sesión `main`. Si quieres sesiones distintas por división, ver [04. Configuración de .zshrc](../02-zsh/04-configuracion-zshrc.md#arranque-automático-de-tmux).

## Aplicar cambios

Ghostty recarga la configuración automáticamente al:
- Abrir una nueva ventana (`Cmd + N`)
- Recargar con el atajo configurado (por defecto `Cmd + Shift + ,`)
- Reiniciar la aplicación (`Cmd + Q` y volver a abrir)

## Rutas útiles

| Acción | Comando |
|--------|---------|
| Abrir carpeta de config en Finder | `open "$HOME/Library/Application Support/com.mitchellh.ghostty"` |
| Ver contenido actual | `cat "$HOME/Library/Application Support/com.mitchellh.ghostty/config.ghostty"` |
| Crear respaldo rápido | `cp "$HOME/Library/Application Support/com.mitchellh.ghostty/config.ghostty" "$HOME/Library/Application Support/com.mitchellh.ghostty/config.ghostty.bak"` |

---

> **Siguiente paso:** [03. Apariencia](../01-ghostty/03-apariencia.md)
