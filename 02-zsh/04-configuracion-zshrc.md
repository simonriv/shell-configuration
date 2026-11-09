# 02. Zsh — Configuración de .zshrc

> **Sección original:** 3.3 Orden de carga recomendado

## Principio fundamental: orden de carga

El orden en `~/.zshrc` **importa**. Cargar en el orden incorrecto rompe completados, sugerencias o resaltado.

### Orden en uso

```
 1. fpath (zsh-completions) ANTES de compinit
 2. autoload -Uz compinit && compinit        ← UNA SOLA VEZ
 3. Historial (HISTSIZE, SAVEHIST, opciones)
 4. zoxide: eval "$(zoxide init zsh)"
 5. fzf: source <(fzf --zsh) + Tab nativo de Zsh
 6. Secretos: source ~/.zsh_secrets
 7. PATH de desarrollo (Bun, PostgreSQL, ~/.local/bin, Google Cloud SDK)
 8. zsh-autosuggestions
 9. Alias
10. Starship: eval "$(starship init zsh)"
11. zsh-syntax-highlighting                  ← AL FINAL de los plugins
12. Arranque automático de tmux
13. Variables de la base de conocimiento (KB_ROOT)
```

## Archivo actual

Copia completa (sin credenciales) en [`examples/zsh/zshrc`](../examples/zsh/zshrc).

```zsh
# Completado de Zsh
fpath=("$(brew --prefix)/share/zsh-completions" $fpath)
autoload -Uz compinit
compinit

# Historial
HISTSIZE=50000
SAVEHIST=50000
setopt HIST_IGNORE_DUPS
setopt SHARE_HISTORY

# Navegación inteligente
eval "$(zoxide init zsh)"

# Búsqueda interactiva
source <(fzf --zsh)
bindkey '^I' expand-or-complete

# Secretos (API keys, tokens): viven en ~/.zsh_secrets (chmod 600)
[ -f "$HOME/.zsh_secrets" ] && source "$HOME/.zsh_secrets"
# Bun
export BUN_INSTALL="$HOME/.bun"
export PATH="$BUN_INSTALL/bin:$PATH"
[ -s "$BUN_INSTALL/_bun" ] && source "$BUN_INSTALL/_bun"

# Rutas de desarrollo
export PATH="/opt/homebrew/opt/postgresql@18/bin:$PATH"
export PATH="$HOME/.local/bin:$PATH"
export PATH="/opt/homebrew/share/google-cloud-sdk/bin:$PATH"

# Sugerencias de comandos
source "$(brew --prefix)/share/zsh-autosuggestions/zsh-autosuggestions.zsh"

# Aliases (eza)
alias ls="eza --icons --group-directories-first"
alias ll="eza -l --icons --group-directories-first"
alias la="eza -la --icons --group-directories-first"
alias lt="eza --tree --icons --group-directories-first"
alias llt="eza -l --tree --icons --group-directories-first"

# Navegación y utilidades
alias ..="cd .."
alias ...="cd ../.."
alias ~="cd ~"
alias cls="clear"

alias reload="source ~/.zshrc"
alias config-zsh="nvim ~/.zshrc"
alias config-term="nvim $HOME/Library/Application\ Support/com.mitchellh.ghostty/config.ghostty"

alias projects="cd ~/Projects"
alias cleanup="cd ~ && ncdu"
# Prompt minimalista
eval "$(starship init zsh)"

# Syntax highlighting: siempre al final
source "$(brew --prefix)/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh"

# Iniciar tmux automáticamente en terminales interactivas
if [[ -o interactive && -z "$TMUX" && -z "$SSH_CONNECTION" ]]; then
  tmux new-session -A -s main
fi

# Knowledge system vault
export KB_ROOT="$HOME/kb"
```

## Detalles de cada bloque

### Tab: completado nativo en lugar de fzf

`source <(fzf --zsh)` asigna `Tab` a `fzf-completion`. La línea siguiente lo devuelve al completado nativo de Zsh:

```zsh
bindkey '^I' expand-or-complete
```

| Atajo | Con esta línea |
|-------|----------------|
| `Tab` | Completado nativo de Zsh (menús de `compinit` + `zsh-completions`) |
| `**` + `Tab` | **Deja de abrir fzf** (el disparador de fzf queda desactivado) |
| `Ctrl + R` / `Ctrl + T` / `Alt + C` | Siguen abriendo fzf (historial, archivos, directorios) |

> El `bindkey` tiene que ir **después** de `source <(fzf --zsh)`; si va antes, fzf lo sobrescribe.

Comprobar qué hay asignado a Tab:

```bash
bindkey '^I'
# Debe mostrar: "^I" expand-or-complete
```

### Secretos fuera de `.zshrc`

Las API keys y tokens viven en `~/.zsh_secrets`, nunca en `.zshrc`:

```bash
cp examples/zsh/zsh_secrets.example ~/.zsh_secrets
chmod 600 ~/.zsh_secrets
nvim ~/.zsh_secrets   # pon tus valores reales
```

`.gitignore` del repo excluye `.zsh_secrets` por si se copia aquí por error.

### Arranque automático de tmux

```zsh
if [[ -o interactive && -z "$TMUX" && -z "$SSH_CONNECTION" ]]; then
  tmux new-session -A -s main
fi
```

| Condición | Motivo |
|-----------|--------|
| `-o interactive` | No se ejecuta en scripts ni en `zsh -c` |
| `-z "$TMUX"` | Evita abrir tmux dentro de tmux |
| `-z "$SSH_CONNECTION"` | No se activa en sesiones SSH |
| `new-session -A -s main` | Se conecta a la sesión `main` si existe; si no, la crea |

Consecuencia: todas las ventanas, tabs y divisiones de Ghostty comparten la sesión `main`. Para una sesión aparte: `tmux new -s otra`.

> ⚠️ **El código que va después de este bloque** (como `export KB_ROOT=...`) solo se ejecuta en la shell externa **cuando sales de tmux**. Dentro de tmux sí se carga, porque cada panel vuelve a leer `.zshrc`. Si un `export` tiene que estar disponible también en el servidor de tmux (por ejemplo, para `run-shell`), muévelo encima del bloque.

### PATH y herramientas propias de esta máquina

Bun, `postgresql@18`, `~/.local/bin`, Google Cloud SDK y `KB_ROOT` son del entorno de desarrollo de referencia. Bórralos si no los usas: un `source` de un archivo inexistente da error al arrancar.

## ⚠️ Antes de reemplazar tu .zshrc actual

1. **Haz un respaldo** (ver [01. Respaldos y limpieza](../02-zsh/01-respaldos-limpieza.md))
2. **Compara** tu archivo actual con este ejemplo
3. **Preserva** tus variables de entorno, PATHs, SDKs, aliases personalizados
4. **Integra** solo las partes que falten

## Verificar rutas en tu máquina

```bash
# Comprueba que estas rutas existen ANTES de usarlas en .zshrc
ls "$(brew --prefix)/share/zsh-completions"
ls "$(brew --prefix)/share/zsh-autosuggestions"
ls "$(brew --prefix)/share/zsh-syntax-highlighting"
fzf --zsh >/dev/null && echo "fzf --zsh disponible (fzf >= 0.48)"
```

## Errores comunes

| Error | Causa | Solución |
|-------|-------|----------|
| `compinit:503: no such file or directory` | `fpath` apunta a ruta inexistente | Verifica `$(brew --prefix)/share/zsh-completions` |
| Sugerencias no aparecen | `zsh-autosuggestions` cargado antes de `compinit` | Muévelo después |
| Resaltado no funciona | `zsh-syntax-highlighting` no al final | Muévelo al final de los plugins |
| Prompt raro / lento | Starship no inicializado o doble init | Un solo `eval "$(starship init zsh)"` |
| `**<Tab>` no abre fzf | `bindkey '^I' expand-or-complete` activo | Es lo esperado; quita la línea si quieres el disparador de fzf |
| tmux dentro de tmux | Falta la condición `-z "$TMUX"` | Usa el bloque de arranque tal cual |

---

> **Siguiente paso:** [05. Starship (preset Jetpack)](../02-zsh/05-starship.md)
