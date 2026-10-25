# 08. Estado -- Pendiente de comprobar en el Mac

> **Seccion original:** 9.2 Pendiente de comprobar en el Mac

## Archivos de configuración (contenido exacto actual)

- [ ] `~/.zshrc` — contenido completo actual
- [ ] `~/.tmux.conf` — contenido completo actual
- [ ] `~/Library/Application Support/com.mitchellh.ghostty/config.ghostty` — contenido completo actual
- [ ] `~/.config/starship.toml` — preset aplicado y personalizaciones
- [ ] `~/.config/nvim/lua/chadrc.lua` — configuración NvChad actual
- [ ] `~/.config/nvim/lua/plugins/` — plugins personalizados actuales

## Respaldos existentes

- [ ] Nombres exactos de respaldos en `~/.config/backups/zsh/`
- [ ] Respaldos de `.tmux.conf`, `nvim`, `ghostty` con fechas reales

## Wattop

- [ ] Método y comando exacto de instalación usado
- [ ] Versión instalada y fuente (brew, cargo, binario, etc.)
- [ ] Verificar si cumple expectativas de monitoreo

## Utilidades instaladas actualmente

- [ ] `fastfetch` — versión y config
- [ ] `btop` — versión
- [ ] `lazygit` — versión
- [ ] `bat` — versión
- [ ] `eza` — versión
- [ ] `fzf` — versión y keybindings en Zsh
- [ ] `zoxide` — versión y base de datos
- [ ] `wattop` — versión
- [ ] `tree-sitter` CLI — versión

## Neovim / NvChad

- [ ] Archivo `vim-be-good.lua` — ¿existe? ¿plugin instalado en Lazy?
- [ ] **LSP activos reales** en proyecto TypeScript/Next.js:
  - [ ] `vtsls` — cliente adjunto?
  - [ ] `tailwindcss` — cliente adjunto?
  - [ ] `eslint` — cliente adjunto?
  - [ ] `html` / `cssls` / `jsonls` — clientes adjuntos?
- [ ] `:LspInfo` en archivo `.tsx` real — output completo
- [ ] `:checkhealth vim.lsp` — estado actual
- [ ] `:Mason` — lista completa de paquetes instalados
- [ ] `conform.nvim` — formatters configurados por filetype
- [ ] Prettier — ¿en proyecto? ¿global? ¿funciona con Conform?

## Atajos y opciones propuestos

- [ ] Ghostty: ¿`background-opacity = 0.85` activo? ¿`macos-window-buttons = hidden` activo?
- [ ] Zsh: ¿orden de carga correcto en `.zshrc`? ¿plugins cargados?
- [ ] Starship: ¿preset Jetpack activo? ¿config personalizada?
- [ ] tmux: ¿todos los keybindings del bloque consolidado presentes?
- [ ] Neovim: ¿transparencia base46 funcional?

## Cómo verificar eficientemente

```bash
# 1. Herramientas
for cmd in fastfetch btop lazygit bat eza fzf zoxide wattop tree-sitter starship ghostty tmux nvim; do
  command -v "$cmd" && echo "✅ $cmd" || echo "❌ $cmd"
done

# 2. Configs clave
echo "=== .zshrc ==="; head -80 ~/.zshrc
echo "=== .tmux.conf ==="; cat ~/.tmux.conf
echo "=== Ghostty ==="; cat "$HOME/Library/Application Support/com.mitchellh.ghostty/config.ghostty"
echo "=== Starship ==="; cat ~/.config/starship.toml

# 3. Neovim health
nvim --headless -c "checkhealth" -c "qa" 2>&1 | head -60

# 4. Plugins NvChad
ls ~/.config/nvim/lua/plugins/

# 5. Mason
nvim --headless -c "Mason" -c "qa" 2>&1 | head -30
```

---

> **Fin de la documentacion.** Para convertir esto en copia exacta de la maquina, compara cada seccion "Pendiente" con los archivos reales y actualiza la documentacion accordingly.
