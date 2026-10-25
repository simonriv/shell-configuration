# 03. Utilidades de terminal — Instalación con Homebrew

> **Sección original:** 4.2 Instalación por Homebrew

## Comandos de instalación habituales

### Instalar todo el conjunto (recomendado inicial)

```bash
brew install btop lazygit bat eza fzf zoxide fastfetch
```

### Instalar individualmente

```bash
brew install btop        # Monitor de recursos
brew install lazygit     # Git TUI
brew install bat         # cat con syntax highlighting
brew install eza         # ls mejorado
brew install fzf         # Fuzzy finder
brew install zoxide      # Navegación inteligente
brew install fastfetch   # System info
```

## Post-instalación de fzf (importante)

Si instalas `fzf` con Homebrew, **ejecuta el script de integración** para keybindings y completion en Zsh:

```bash
# Opción 1: Script interactivo (recomendado)
/opt/homebrew/opt/fzf/install

# Opción 2: Solo keybindings y completion para Zsh (no interactivo)
/opt/homebrew/opt/fzf/install --key-bindings --completion --no-update-rc
```

> **Alternativa moderna (fzf >= 0.48):** Usa `eval "$(fzf --zsh)"` en tu `.zshrc` (ver [04. Configuración de .zshrc](../02-zsh/04-configuracion-zshrc.md)).

## Verificar instalación

```bash
# Cada comando debe mostrar versión sin error
btop --version
lazygit --version
bat --version
eza --version
fzf --version
zoxide --version
fastfetch --version
```

## Notas importantes

- **Homebrew no reinstala** si ya está presente; dice "already installed".
- **No hace falta** reinstalar todo el conjunto si solo falta uno.
- **Wattop** no se incluye aquí porque su método de instalación no quedó confirmado (ver [03. Wattop](../03-utilidades-terminal/03-wattop.md)).
- **Nerd Fonts** para iconos en eza/lazygit/Starship:
  ```bash
  brew install --cask font-jetbrains-mono-nerd-font
  # O tu favorita: font-hack-nerd-font, font-fira-code-nerd-font, etc.
  ```

## Actualizar herramientas

```bash
brew upgrade btop lazygit bat eza fzf zoxide fastfetch
```

---

> **Siguiente paso:** [03. Wattop](../03-utilidades-terminal/03-wattop.md)
