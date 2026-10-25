# 06. Comprobaciones rápidas -- Chequeos de salud

> **Seccion original:** 7. Comprobaciones rápidas

## Script todo-en-uno: Herramientas

```bash
for cmd in brew ghostty zsh starship zoxide fzf eza tmux nvim fastfetch btop lazygit bat wattop tree-sitter; do
  if command -v "$cmd" >/dev/null 2>&1; then
    printf 'OK   %-14s %s\n' "$cmd" "$(command -v "$cmd")"
  else
    printf 'FALTA %-14s\n' "$cmd"
  fi
done
```

> Informa qué ejecutables están en el PATH; no verifica configuraciones.

## Zsh

```bash
# Sintaxis
zsh -n ~/.zshrc

# Recargar y probar
source ~/.zshrc
```

## tmux

```bash
# Version
tmux -V

# Recargar config
tmux source-file ~/.tmux.conf

# Ver keybindings relevantes
tmux list-keys | grep -E 'split-window|resize-pane|select-pane|next-layout'
```

## Neovim (dentro de Neovim)

```vim
:checkhealth
:Lazy
:Mason
:LspInfo
:messages
```

## Chequeo rapido combinado (terminal)

```bash
echo "=== HERRAMIENTAS ==="
for cmd in ghostty zsh starship zoxide fzf eza tmux nvim fastfetch btop lazygit bat tree-sitter; do
  command -v "$cmd" >/dev/null && echo "✅ $cmd" || echo "❌ $cmd"
done

echo -e "\n=== ZSH ==="
zsh -n ~/.zshrc && echo "✅ Sintaxis OK" || echo "❌ Error sintaxis"

echo -e "\n=== TMUX ==="
tmux -V
tmux list-keys | grep -c 'split-window\|resize-pane\|select-pane\|next-layout' | xargs -I{} echo "Keybindings panel: {}"

echo -e "\n=== NEOVIM ==="
nvim --headless -c "checkhealth" -c "qa" 2>&1 | grep -E '^(OK|WARNING|ERROR)' | head -20
```

---

> **Siguiente paso:** [01. Respaldos antes de editar](../07-mantenimiento/01-respaldos.md)
