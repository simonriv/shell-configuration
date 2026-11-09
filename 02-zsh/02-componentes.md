# 02. Zsh — Componentes del entorno

> **Sección original:** 3.1 Componentes del entorno

## Lista de componentes trabajados

| Componente | Propósito | Estado |
|------------|-----------|--------|
| **Starship** | Prompt rápido y configurable | ✅ Usado (Jetpack + iconos Nerd Font) |
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
│                    Zsh (.zshrc)                     │
├─────────────────────────────────────────────────────┤
│  1. zsh-completions (fpath) + compinit              │
│  2. zoxide init                                     │
│  3. fzf --zsh  + Tab nativo (expand-or-complete)    │
│  4. ~/.zsh_secrets y PATH de desarrollo             │
│  5. zsh-autosuggestions                             │
│  6. alias                                           │
│  7. starship init (prompt)                          │
│  8. zsh-syntax-highlighting (¡AL FINAL!)            │
│  9. exports finales (KB_ROOT)                       │
│ 10. arranque automático de tmux (último)            │
└─────────────────────────────────────────────────────┘
```

Detalle completo en [04. Configuración de .zshrc](04-configuracion-zshrc.md).

> **Orden crítico:** `zsh-syntax-highlighting` **debe cargarse al final** para funcionar correctamente.

## Notas sobre cada componente

### Starship
- Prompt escrito en Rust, configurable con TOML.
- Preset **Jetpack** como base, con iconos Nerd Font ([05. Starship](05-starship.md)).
- Config: `~/.config/starship.toml`

### zoxide
- Aprende tus directorios frecuentes.
- Uso: `z nombre` → salta al directorio más probable.
- Integración: `eval "$(zoxide init zsh)"`

### fzf
- Fuzzy finder para archivos, historial, procesos.
- Atajos útiles: `Ctrl+R` (historial), `Ctrl+T` (archivos), `Alt+C` (directorios).
- `Tab` se devuelve al completado nativo de Zsh, así que `**<Tab>` no abre fzf.

### eza
- Reemplazo moderno de `ls`.
- Alias en uso: `ls`, `ll`, `la`, `lt` (árbol) y `llt`, todos con `--icons --group-directories-first`.

### Plugins Zsh (Homebrew)
- Se instalan en `/opt/homebrew/share/` (Apple Silicon).
- Se cargan con `source /ruta/al/plugin.zsh`.

---

> **Siguiente paso:** [03. Verificación de instalación](../02-zsh/03-verificacion-instalacion.md)
