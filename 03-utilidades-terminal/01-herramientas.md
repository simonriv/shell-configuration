# 03. Utilidades de terminal — Herramientas del entorno

> **Sección original:** 4.1 Herramientas mencionadas en el entorno

## Tabla de referencia

| Herramienta | Uso principal | Comando de verificación |
|-------------|---------------|------------------------|
| `fastfetch` | Resumen del sistema al iniciar terminal | `fastfetch` |
| `btop` | Monitor interactivo de procesos y recursos | `btop` |
| `lazygit` | Interfaz Git en terminal (TUI) | `lazygit` |
| `bat` | `cat` con resaltado de sintaxis | `bat --version` |
| `eza` | Listado de archivos moderno (reemplaza `ls`) | `eza --version` |
| `fzf` | Búsqueda difusa (archivos, historial, etc.) | `fzf --version` |
| `zoxide` | Navegación inteligente entre directorios | `zoxide --version` |
| `wattop` | Monitor para cargas IA / Apple Silicon | `wattop --version` |
| `ncdu` | Uso de disco interactivo (alias `cleanup`) | `ncdu --version` |

## Descripción rápida de cada una

### fastfetch
- Alternativa rápida a `neofetch` (escrita en C).
- Muestra: OS, kernel, shell, CPU, memoria, GPU, paquetes, uptime.
- Se usa para mostrar info al abrir terminal (ver [04. Fastfetch al iniciar](../03-utilidades-terminal/04-fastfetch.md)).

### btop
- Monitor de recursos estilo `htop` pero moderno (C++).
- CPU, memoria, disco, red, procesos, GPU (si soportado).
- Atajos: `q` salir, `h` ayuda, `f` filtrar, `k` matar proceso.

### lazygit
- TUI para Git: commit, push, pull, branch, stash, diff, log.
- Atajos: `c` commit, `P` push, `p` pull, `b` branch, `s` status.
- Abre en la raíz del repo Git.

### bat
- `cat` con resaltado de sintaxis, numeración de líneas, paging.
- `bat archivo.txt` → salida coloreada.
- `bat --list-themes` → temas disponibles.

### eza
- `ls` mejorado: colores, iconos (con Nerd Font), git status, árbol.
- Alias en uso (`~/.zshrc`):
  ```zsh
  alias ls="eza --icons --group-directories-first"
  alias ll="eza -l --icons --group-directories-first"
  alias la="eza -la --icons --group-directories-first"
  alias lt="eza --tree --icons --group-directories-first"
  alias llt="eza -l --tree --icons --group-directories-first"
  ```

### fzf
- Fuzzy finder universal.
- Integración Zsh: `Ctrl+R` (historial), `Ctrl+T` (archivos), `Alt+C` (directorios).
- `Tab` queda con el completado nativo de Zsh (ver [02-zsh/04](../02-zsh/04-configuracion-zshrc.md#tab-completado-nativo-en-lugar-de-fzf)).
- Usable en scripts: `find . -type f | fzf`

### zoxide
- `cd` inteligente que aprende tus directorios.
- `z foo` → salta al directorio que más visitas con "foo" en el nombre.
- `zi` → selección interactiva con fzf.

### wattop
- Monitor especializado para Apple Silicon.
- Muestra: CPU, GPU, Neural Engine, memoria, consumo energético.
- Instalado como cask: `brew install --cask wattop`.
- **Nota:** En pruebas no mostraba todas las sesiones de terminal ni detectaba Pi como sesión identificable. Ver [03. Wattop](../03-utilidades-terminal/03-wattop.md).

### ncdu
- Analizador de uso de disco con interfaz de texto.
- Alias `cleanup` → `cd ~ && ncdu`.

## Verificar cuáles están instaladas

```bash
for cmd in fastfetch btop lazygit bat eza fzf zoxide wattop ncdu; do
  if command -v "$cmd" >/dev/null 2>&1; then
    printf '✅ %-12s %s\n' "$cmd" "$(command -v "$cmd")"
  else
    printf '❌ %-12s\n' "$cmd"
  fi
done
```

---

> **Siguiente paso:** [02. Instalación con Homebrew](../03-utilidades-terminal/02-instalacion-homebrew.md)
