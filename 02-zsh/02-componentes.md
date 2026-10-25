# 02. Zsh — Componentes del entorno

> **Sección original:** 3.1 Componentes del entorno

## Lista de componentes trabajados

| Componente | Propósito | Estado |
|------------|-----------|--------|
| **Starship** | Prompt rápido y configurable | ✅ Usado (preset Jetpack) |
| **zoxide** | Navegación inteligente (`z` en lugar de `cd`) | ✅ Instalado |
| **fzf** | Búsqueda difusa en historial/archivos | ✅ Instalado |
| **eza** | `ls` mejorado con colores, iconos, git | ✅ Instalado |
| **zsh-completions** | Completados adicionales | ✅ Instalado (Homebrew) |
| **zsh-autosuggestions** | Sugerencias grises basadas en historial | ✅ Instalado (Homebrew) |
| **zsh-syntax-highlighting** | Resaltado de sintaxis en línea de comandos | ✅ Instalado (Homebrew) |

## ❌ No instalado / No usado

| Componente | Motivo |
|------------|--------|
| `zsh-autocomplete` | **Decisión explícita:** se conservó el autocompletado existente, no se sustituyó por este paquete |

## Relación entre componentes

```
┌─────────────────────────────────────────────────────┐
│                    Zsh (.zshrc)                      │
├─────────────────────────────────────────────────────┤
│  1. compinit + zsh-completions                       │
│  2. zoxide init                                      │
│  3. fzf init (keybindings + completion)             │
│  4. starship init (prompt)                           │
│  5. zsh-autosuggestions (al final)                   │
│  6. zsh-syntax-highlighting (¡AL FINAL!)            │
└─────────────────────────────────────────────────────┘
```

> **Orden crítico:** `zsh-syntax-highlighting` **debe cargarse al final** para funcionar correctamente.

## Notas sobre cada componente

### Starship
- Prompt escrito en Rust, configurable con TOML.
- Preset **Jetpack** elegido por ser compacto e informativo.
- Config: `~/.config/starship.toml`

### zoxide
- Aprende tus directorios frecuentes.
- Uso: `z nombre` → salta al directorio más probable.
- Integración: `eval "$(zoxide init zsh)"`

### fzf
- Fuzzy finder para archivos, historial, procesos.
- Atajos útiles: `Ctrl+R` (historial), `Ctrl+T` (archivos), `Alt+C` (directorios).

### eza
- Reemplazo moderno de `ls`.
- Alias comunes: `alias ls='eza'`, `alias ll='eza -l'`, `alias la='eza -la'`.

### Plugins Zsh (Homebrew)
- Se instalan en `/opt/homebrew/share/` (Apple Silicon).
- Se cargan con `source /ruta/al/plugin.zsh`.

---

> **Siguiente paso:** [03. Verificación de instalación](../02-zsh/03-verificacion-instalacion.md)
