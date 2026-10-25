# 02. Zsh — Configuración de .zshrc

> **Sección original:** 3.3 Orden de carga recomendado

## Principio fundamental: orden de carga

El orden en `~/.zshrc` **importa**. Cargar en el orden incorrecto rompe completados, sugerencias o resaltado.

### Orden recomendado

```
1. Configurar fpath (zsh-completions) ANTES de compinit
2. autoload -Uz compinit && compinit        ← UNA SOLA VEZ
3. Inicializar zoxide: eval "$(zoxide init zsh)"
4. Inicializar fzf (keybindings + completion)
5. Inicializar Starship: eval "$(starship init zsh)"
6. Cargar zsh-autosuggestions
7. Cargar zsh-syntax-highlighting           ← ¡SIEMPRE AL FINAL!
```

## Ejemplo orientativo (NO copiar ciegamente)

```zsh
# ──────────────────────────────────────────────
# 1. COMPLETADOS ADICIONALES (antes de compinit)
# ──────────────────────────────────────────────
if [[ -d /opt/homebrew/share/zsh-completions ]]; then
  fpath=(/opt/homebrew/share/zsh-completions $fpath)
fi

# ──────────────────────────────────────────────
# 2. INICIALIZAR SISTEMA DE COMPLETADO (una vez)
# ──────────────────────────────────────────────
autoload -Uz compinit
compinit

# ──────────────────────────────────────────────
# 3. NAVEGACIÓN INTELIGENTE (zoxide)
# ──────────────────────────────────────────────
eval "$(zoxide init zsh)"

# ──────────────────────────────────────────────
# 4. FZF (keybindings + completion)
# ──────────────────────────────────────────────
# Si instalaste fzf con Homebrew, el script de integración está en:
# /opt/homebrew/opt/fzf/shell/key-bindings.zsh
# /opt/homebrew/opt/fzf/shell/completion.zsh
# O usa la función nativa de fzf >= 0.48:
eval "$(fzf --zsh)"

# ──────────────────────────────────────────────
# 5. PROMPT (Starship)
# ──────────────────────────────────────────────
eval "$(starship init zsh)"

# ──────────────────────────────────────────────
# 6. PLUGINS: AUTOSUGGESTIONS (antes de syntax highlighting)
# ──────────────────────────────────────────────
[[ -r /opt/homebrew/share/zsh-autosuggestions/zsh-autosuggestions.zsh ]] &&
  source /opt/homebrew/share/zsh-autosuggestions/zsh-autosuggestions.zsh

# ──────────────────────────────────────────────
# 7. PLUGINS: SYNTAX HIGHLIGHTING (¡AL FINAL!)
# ──────────────────────────────────────────────
[[ -r /opt/homebrew/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh ]] &&
  source /opt/homebrew/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh

# ──────────────────────────────────────────────
# 8. TUS CONFIGURACIONES PERSONALES (alias, exports, etc.)
# ──────────────────────────────────────────────
# alias ls='eza'
# alias ll='eza -l'
# export EDITOR=nvim
# ... tus variables de desarrollo (PATH, SDKs, etc.) ...
```

## ⚠️ Antes de reemplazar tu .zshrc actual

1. **Haz un respaldo** (ver [01. Respaldos y limpieza](../02-zsh/01-respaldos-limpieza.md))
2. **Compara** tu archivo actual con este ejemplo
3. **Preserva** tus variables de entorno, PATHs, SDKs, aliases personalizados
4. **Integra** solo las partes que falten

## Verificar rutas en tu máquina

```bash
# Comprueba que estas rutas existen ANTES de usarlas en .zshrc
ls /opt/homebrew/share/zsh-completions
ls /opt/homebrew/share/zsh-autosuggestions
ls /opt/homebrew/share/zsh-syntax-highlighting
ls /opt/homebrew/opt/fzf/shell/ 2>/dev/null || echo "fzf no en opt, usa 'fzf --zsh'"
```

## Errores comunes

| Error | Causa | Solución |
|-------|-------|----------|
| `compinit:503: no such file or directory` | `fpath` apunta a ruta inexistente | Verifica `/opt/homebrew/share/zsh-completions` |
| Sugerencias no aparecen | `zsh-autosuggestions` cargado antes de `compinit` | Muévelo después |
| Resaltado no funciona | `zsh-syntax-highlighting` no al final | Muévelo al final del archivo |
| Prompt raro / lento | Starship no inicializado o doble init | Un solo `eval "$(starship init zsh)"` |

---

> **Siguiente paso:** [05. Starship (preset Jetpack)](../02-zsh/05-starship.md)
