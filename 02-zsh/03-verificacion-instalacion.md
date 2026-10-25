# 02. Zsh — Verificación de instalación

> **Sección original:** 3.2 Comprobar qué está instalado

## Verificar paquetes Homebrew

```bash
# Fórmulas (binarios/librerías)
brew list --formula

# Casks (aplicaciones GUI)
brew list --cask
```

## Verificar binarios clave en PATH

```bash
command -v starship
command -v zoxide
command -v fzf
command -v eza
```

## Verificar plugins de Zsh (Homebrew)

```bash
brew list --formula | grep -E 'zsh-completions|zsh-autosuggestions|zsh-syntax-highlighting'
```

> **Nota:** Un resultado vacío no garantiza que el plugin no exista; puede estar instalado manualmente o en otra ruta.

## Comprobar rutas reales de plugins (Apple Silicon)

```bash
ls /opt/homebrew/share/zsh-completions
ls /opt/homebrew/share/zsh-autosuggestions
ls /opt/homebrew/share/zsh-syntax-highlighting
```

Si existen, verás archivos como:
- `zsh-completions/` → varios archivos `_*`
- `zsh-autosuggestions/` → `zsh-autosuggestions.zsh`
- `zsh-syntax-highlighting/` → `zsh-syntax-highlighting.zsh`

## Script de verificación rápida

```bash
for cmd in starship zoxide fzf eza; do
  if command -v "$cmd" >/dev/null 2>&1; then
    echo "✅ $cmd: $(command -v $cmd)"
  else
    echo "❌ $cmd: NO ENCONTRADO"
  fi
done

echo "--- Plugins Zsh (Homebrew) ---"
brew list --formula | grep -E 'zsh-completions|zsh-autosuggestions|zsh-syntax-highlighting' || echo "Ninguno encontrado vía brew"
```

## Qué hacer si falta algo

Ver [02. Instalación con Homebrew](../03-utilidades-terminal/02-instalacion-homebrew.md) para comandos de instalación.

---

> **Siguiente paso:** [04. Configuración de .zshrc](../02-zsh/04-configuracion-zshrc.md)
