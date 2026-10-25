# 07. Mantenimiento -- Actualizaciones

> **Seccion original:** 8.2 Actualizar Homebrew

## Actualizar Homebrew y ver que hay nuevo

```bash
# Actualizar indice de formulas
brew update

# Ver paquetes desactualizados
brew outdated

# Ver todo (formulas + casks)
brew outdated --formula --cask
```

## Actualizar selectivamente (recomendado)

```bash
# Solo una herramienta
brew upgrade nvim
brew upgrade tmux
brew upgrade ghostty

# Varias a la vez
brew upgrade neovim tmux ghostty starship zoxide fzf eza bat lazygit btop fastfetch
```

## Actualizar todo (con precaucion)

```bash
# Actualiza TODAS las formulas y casks
brew upgrade

# Limpia versiones antiguas y cache
brew cleanup
```

## Neovim / NvChad / Plugins

```bash
# Dentro de Neovim
:Lazy sync          # Actualiza plugins declarados
:Mason              # Ver/actualizar LSP servers, linters, etc.
:checkhealth        # Verificar tras actualizaciones
```

## Starship

```bash
# Actualizar starship (si instalado via brew)
brew upgrade starship

# Ver version
starship --version
```

## Ghostty

```bash
# Actualizar (cask)
brew upgrade --cask ghostty

# Ver version
ghostty --version
```

## Reglas de actualizacion

1. **Lee los changelogs** antes de actualizar herramientas criticas (nvim, tmux, zsh).
2. **Actualiza selectivamente**, no todo a la vez.
3. **Haz respaldo ANTES** (ver [01. Respaldos](../07-mantenimiento/01-respaldos.md)).
4. **Prueba despues de cada grupo**: `source ~/.zshrc`, `tmux source-file ~/.tmux.conf`, `:checkhealth`.
5. **Si algo rompe**, restaura el respaldo y espera a entender el cambio.

---

> **Siguiente paso:** [03. Reglas de mantenimiento](../07-mantenimiento/03-reglas.md)
