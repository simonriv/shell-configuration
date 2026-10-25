# 00. Prerrequisitos — Verificación inicial

> **Sección original:** 0. Antes de empezar

## Entorno esperado

- **Sistema:** macOS en Apple Silicon (arm64)
- **Shell:** Zsh
- **Terminal:** Ghostty
- **Multiplexor:** tmux
- **Editor:** Neovim con NvChad
- **Gestor de paquetes:** Homebrew
- **Enfoque:** Configuración minimalista, atajos de teclado y herramientas de terminal

## Comprobaciones básicas

Ejecuta estos comandos para confirmar el estado actual:

```bash
# Arquitectura del procesador
uname -m
# En Apple Silicon debe devolver: arm64

# Versión de macOS
sw_vers

# Homebrew
command -v brew
brew --version

# Shell actual
echo "$SHELL"
zsh --version
```

## Qué verificar

| Comando | Resultado esperado |
|---------|-------------------|
| `uname -m` | `arm64` |
| `command -v brew` | Ruta a brew (ej. `/opt/homebrew/bin/brew`) |
| `echo "$SHELL"` | `/bin/zsh` o `/opt/homebrew/bin/zsh` |
| `zsh --version` | Versión 5.9 o superior |

## Notas

- Si `uname -m` devuelve `x86_64` en un Mac Apple Silicon, estás ejecutando la terminal bajo Rosetta 2.
- Homebrew en Apple Silicon se instala en `/opt/homebrew` (no en `/usr/local`).
- Zsh es el shell por defecto en macOS desde Catalina (10.15).

---

> **Siguiente paso:** [01. Instalación de Ghostty](../01-ghostty/01-instalacion.md)
