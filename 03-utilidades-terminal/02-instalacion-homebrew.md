# 03. Utilidades de terminal — Instalación con Homebrew

> **Sección original:** 4.2 Instalación por Homebrew

## Comandos de instalación habituales

### Instalar todo el conjunto (recomendado inicial)

```bash
brew install btop lazygit bat eza fzf zoxide fastfetch ncdu
brew install --cask wattop
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
brew install ncdu        # Uso de disco (alias cleanup)
brew install --cask wattop  # Monitor Apple Silicon
```

## Post-instalación de fzf (importante)

**En uso:** `source <(fzf --zsh)` en `.zshrc` (fzf >= 0.48), sin script de instalación. Ver [04. Configuración de .zshrc](../02-zsh/04-configuracion-zshrc.md).

Alternativa para versiones antiguas de fzf, con el script de integración:

```bash
# Opción 1: Script interactivo (recomendado)
/opt/homebrew/opt/fzf/install

# Opción 2: Solo keybindings y completion para Zsh (no interactivo)
/opt/homebrew/opt/fzf/install --key-bindings --completion --no-update-rc
```


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
ncdu --version
wattop --version
```

## Notas importantes

- **Homebrew no reinstala** si ya está presente; dice "already installed".
- **No hace falta** reinstalar todo el conjunto si solo falta uno.
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
