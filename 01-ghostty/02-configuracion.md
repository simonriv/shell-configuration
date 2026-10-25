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

El archivo usa formato INI simple: `clave = valor`. Ejemplo:

```ini
# Comentario
background-opacity = 0.85
macos-window-buttons = hidden
font-family = "JetBrainsMono Nerd Font"
font-size = 14
```

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
