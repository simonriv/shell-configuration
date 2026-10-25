# 02. Zsh — Recarga y verificación

> **Sección original:** 3.5 Recargar Zsh

## Recargar configuración

```bash
source ~/.zshrc
```

O abre una nueva pestaña/ventana en Ghostty (`Cmd + T` / `Cmd + N`).

## Verificar sintaxis (sin ejecutar)

```bash
zsh -n ~/.zshrc
```

- **Salida vacía (código 0)** → sintaxis OK
- **Error mostrado** → línea y tipo de error

> Útil para detectar errores antes de hacer `source`.

## Verificar que componentes cargaron

```bash
# Starship
echo $STARSHIP_SESSION_KEY

# zoxide
zoxide query ~

# fzf keybindings
bindkey | grep fzf

# Autosuggestions
bindkey | grep autosuggest

# Syntax highlighting
typeset -f _zsh_highlight
```

## Chequeo rápido todo-en-uno

```bash
echo "=== Zsh config check ==="
zsh -n ~/.zshrc && echo "✅ Sintaxis OK" || echo "❌ Error de sintaxis"

echo "=== Componentes ==="
command -v starship >/dev/null && echo "✅ starship" || echo "❌ starship"
command -v zoxide >/dev/null && echo "✅ zoxide" || echo "❌ zoxide"
command -v fzf >/dev/null && echo "✅ fzf" || echo "❌ fzf"
command -v eza >/dev/null && echo "✅ eza" || echo "❌ eza"

echo "=== Plugins cargados ==="
[[ -n $ZSH_AUTOSUGGEST_VERSION ]] && echo "✅ zsh-autosuggestions" || echo "⚠️ zsh-autosuggestions (no detectado)"
typeset -f _zsh_highlight >/dev/null && echo "✅ zsh-syntax-highlighting" || echo "⚠️ zsh-syntax-highlighting (no detectado)"
```

## Si algo falla

1. Revisa la salida de `zsh -n ~/.zshrc`
2. Comprueba el orden de carga (ver [04. Configuración de .zshrc](../02-zsh/04-configuracion-zshrc.md))
3. Verifica que las rutas de `source` existan (`ls /ruta/al/plugin.zsh`)
4. Revisa `~/.zsh_history` o ejecuta `zsh -x ~/.zshrc 2>&1 | head -50` para debug

---

> **Siguiente paso:** [01. Herramientas del entorno](../03-utilidades-terminal/01-herramientas.md)
