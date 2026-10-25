# 07. Mantenimiento -- Respaldos antes de editar

> **Seccion original:** 8. Restauración y mantenimiento / Antes de editar cualquier configuracion

## Archivos criticos a respaldar

```bash
# Zsh
cp ~/.zshrc ~/.zshrc.bak.$(date +%Y%m%d-%H%M%S)

# tmux
cp ~/.tmux.conf ~/.tmux.conf.bak.$(date +%Y%m%d-%H%M%S)

# Neovim (carpeta completa)
cp -R ~/.config/nvim ~/.config/nvim.bak.$(date +%Y%m%d-%H%M%S)

# Ghostty
cp "$HOME/Library/Application Support/com.mitchellh.ghostty/config.ghostty" \
   "$HOME/Library/Application Support/com.mitchellh.ghostty/config.ghostty.bak.$(date +%Y%m%d-%H%M%S)"
```

> Estos comandos pueden fallar si un archivo no existe; comprueba primero con `ls`.

## Verificar antes de respaldar

```bash
ls -la ~/.zshrc ~/.tmux.conf ~/.config/nvim "$HOME/Library/Application Support/com.mitchellh.ghostty/config.ghostty"
```

## Buenas practicas

1. **Nombres con fecha** (`YYYYMMDD-HHMMSS`) para evitar sobrescribir respaldos previos.
2. **Verifica el respaldo** inmediatamente: `cat archivo.bak.20250115-143022 | head -20`
3. **Mantén al menos 3 respaldos** recientes antes de purgar antiguos.
4. **Documenta qué cambiaste** en un comentario al inicio del archivo modificado.

## Restaurar un respaldo

```bash
# Ejemplo Zsh
cp ~/.zshrc.bak.20250115-143022 ~/.zshrc
source ~/.zshrc

# Ejemplo tmux
cp ~/.tmux.conf.bak.20250115-143022 ~/.tmux.conf
tmux source-file ~/.tmux.conf

# Ejemplo Neovim
rm -rf ~/.config/nvim
cp -R ~/.config/nvim.bak.20250115-143022 ~/.config/nvim

# Ejemplo Ghostty
cp "$HOME/Library/Application Support/com.mitchellh.ghostty/config.ghostty.bak.20250115-143022" \
   "$HOME/Library/Application Support/com.mitchellh.ghostty/config.ghostty"
```

---

> **Siguiente paso:** [02. Actualizaciones](../07-mantenimiento/02-actualizaciones.md)
