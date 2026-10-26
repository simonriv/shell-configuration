# Ejemplos de configuración

Copia real de los archivos de configuración de la máquina de referencia (macOS, Apple Silicon), tomada el 2026-10-26. Sirve para ver cómo queda cada archivo una vez aplicada la guía.

> **Sin credenciales:** las API keys se retiraron de `zshrc` y se sustituyeron por la carga de `~/.zsh_secrets` (plantilla en `zsh/zsh_secrets.example`). Las rutas con nombre de usuario se cambiaron por `$HOME`.

## Dónde va cada archivo

| Archivo del repo | Destino en tu máquina | Guía |
|---|---|---|
| `ghostty/config.ghostty` | `~/Library/Application Support/com.mitchellh.ghostty/config.ghostty` | [01-ghostty](../01-ghostty/02-configuracion.md) |
| `zsh/zshrc` | `~/.zshrc` | [02-zsh/04](../02-zsh/04-configuracion-zshrc.md) |
| `zsh/zshenv` | `~/.zshenv` | [02-zsh/01](../02-zsh/01-respaldos-limpieza.md) |
| `zsh/zprofile` | `~/.zprofile` | [02-zsh/01](../02-zsh/01-respaldos-limpieza.md) |
| `zsh/zsh_secrets.example` | `~/.zsh_secrets` (con `chmod 600`) | — |
| `starship/starship.toml` | `~/.config/starship.toml` | [02-zsh/05](../02-zsh/05-starship.md) |
| `fastfetch/config.jsonc` | `~/.config/fastfetch/config.jsonc` | [03-utilidades/04](../03-utilidades-terminal/04-fastfetch.md) |
| `tmux/tmux.conf` | `~/.tmux.conf` | [04-tmux/06](../04-tmux/06-configuracion-consolidada.md) |
| `nvim/` | `~/.config/nvim/` | [05-neovim-nvchad/02](../05-neovim-nvchad/02-estructura-configuracion.md) |

## Antes de copiar

1. **Respalda** lo que ya tengas: [07-mantenimiento/01](../07-mantenimiento/01-respaldos.md).
2. **Revisa `zshrc` línea a línea.** Incluye rutas propias de la máquina de referencia que quizá no necesites: Bun, `postgresql@18`, Google Cloud SDK, `KB_ROOT` y el arranque automático de tmux. Bórralas si no aplican.
3. `zshenv` carga `~/.cargo/env`: quítalo si no tienes Rust instalado o la shell dará error al arrancar.
4. `tmux.conf` usa TPM: instálalo con `git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm` y dentro de tmux pulsa `prefijo + I`.

## Notas sobre Neovim

- Es el [NvChad starter](https://github.com/NvChad/starter) con el tema `ayu_dark` en `lua/chadrc.lua`. Se omitieron `.git`, `LICENSE` y `README.md` del starter.
- `lazy-lock.json` fija las versiones de plugins; bórralo si prefieres las últimas.
- En esta copia **no** existe `lua/plugins/vim-be-good.lua` ni servidores LSP extra (solo `html` y `cssls`): lo descrito en [05-neovim-nvchad/03](../05-neovim-nvchad/03-plugin-vim-be-good.md) y [05](../05-neovim-nvchad/05-mason-lsp.md) es opcional y hay que añadirlo a mano.

## Copia rápida (tras respaldar)

```bash
cd examples
cp ghostty/config.ghostty "$HOME/Library/Application Support/com.mitchellh.ghostty/config.ghostty"
cp zsh/zshrc ~/.zshrc && cp zsh/zshenv ~/.zshenv && cp zsh/zprofile ~/.zprofile
cp starship/starship.toml ~/.config/starship.toml
mkdir -p ~/.config/fastfetch && cp fastfetch/config.jsonc ~/.config/fastfetch/config.jsonc
cp tmux/tmux.conf ~/.tmux.conf
cp -R nvim ~/.config/nvim
```
