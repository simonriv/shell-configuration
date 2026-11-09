# 08. Estado — Pendiente

> **Sección original:** 9.2 Pendiente de comprobar en el Mac
>
> Lo que se podía verificar leyendo archivos ya está en [01. Confirmado](01-confirmado.md). Aquí queda lo que requiere probarlo a mano o decidir.

## Requiere prueba manual

- [ ] **LSP en un proyecto Next.js real**: abrir un `.tsx`, ejecutar `:LspInfo` y confirmar qué clientes se adjuntan (hoy solo están habilitados `html` y `cssls`)
- [ ] **Prettier con Conform**: no está configurado; decidir si se añade (ver [05-neovim-nvchad/07](../05-neovim-nvchad/07-conform-formateo.md))
- [ ] **Transparencia de Neovim**: comprobar `toggle_transparency()` con el tema `ayu_dark` y Ghostty a 0.86
- [ ] **Restauración de tmux**: cerrar el servidor (`tmux kill-server`) y comprobar que `tmux-continuum` restaura la sesión `main`
- [ ] **Wattop**: comprobar si ya detecta todas las sesiones de terminal

## Decisiones abiertas

- [ ] Habilitar `vtsls`, `eslint`, `tailwindcss` y `jsonls` en `lua/configs/lspconfig.lua` (ya están instalados en Mason)
- [ ] Mostrar o no `fastfetch` al iniciar (con el arranque automático de tmux hay que colocarlo con cuidado; ver [03-utilidades-terminal/04](../03-utilidades-terminal/04-fastfetch.md))
- [ ] Mostrar el icono de rama en Starship (`[git_branch]` no incluye `$symbol` en su `format`)
- [ ] Mover `export KB_ROOT` encima del bloque de arranque de tmux en `.zshrc`

## Respaldos

- [ ] No hay respaldos fechados de `.tmux.conf`, `nvim`, Ghostty ni `~/.config/backups/zsh/`. Crear uno antes del próximo cambio (ver [07-mantenimiento/01](../07-mantenimiento/01-respaldos.md))

## Cómo volver a verificar

```bash
# Comparar la máquina con las copias del repo
cd examples
diff -u ghostty/config.ghostty "$HOME/Library/Application Support/com.mitchellh.ghostty/config.ghostty"
diff -u zsh/zshrc ~/.zshrc            # difiere a propósito en config-term ($HOME)
diff -u tmux/tmux.conf ~/.tmux.conf
diff -u starship/starship.toml ~/.config/starship.toml
diff -u fastfetch/config.jsonc ~/.config/fastfetch/config.jsonc
diff -ru -x .git -x LICENSE -x README.md -x .DS_Store nvim ~/.config/nvim
```

Si aparece alguna diferencia, actualiza la copia en `examples/` y el documento del tema correspondiente.

---

> **Fin de la documentación.**
