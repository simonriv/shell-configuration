# 05. Neovim y NvChad — Estructura de configuración

> **Sección original:** 6.2 Archivos de configuración

## Carpeta raíz

```text
~/.config/nvim/
```

## Inspeccionar estructura

```bash
# Ver árbol (hasta 3 niveles, solo archivos)
find ~/.config/nvim -maxdepth 3 -type f

# Ver todo con tree (si está instalado)
tree ~/.config/nvim -L 3
```

## Estructura actual (NvChad starter v2.5)

Copia completa en [`examples/nvim/`](../examples/nvim/).

```text
~/.config/nvim/
├── init.lua                 # Entry point: lazy.nvim + NvChad v2.5 + lua/plugins
├── lazy-lock.json           # Versiones fijadas de los plugins
├── .stylua.toml             # Estilo de formateo de Lua (stylua)
└── lua/
    ├── chadrc.lua           # CONFIG PRINCIPAL: tema base46 (ayu_dark), UI
    ├── options.lua          # Opciones de Vim (carga nvchad.options)
    ├── mappings.lua         # Atajos propios (`;` → `:`, `jk` → Esc)
    ├── autocmds.lua         # Autocomandos (carga nvchad.autocmds)
    ├── configs/
    │   ├── conform.lua      # Formatters por tipo de archivo
    │   ├── lazy.lua         # Opciones de lazy.nvim
    │   └── lspconfig.lua    # Servidores LSP activos (html, cssls)
    └── plugins/
        └── init.lua         # Plugins extra: conform.nvim, nvim-lspconfig
```

> Es el [NvChad starter](https://github.com/NvChad/starter) casi sin cambios: el único ajuste propio es el tema `ayu_dark` (el starter trae `onedark`). **No existe** `lua/plugins/vim-be-good.lua` (ver [03. Plugin vim-be-good](03-plugin-vim-be-good.md)).

## Atajos añadidos (`lua/mappings.lua`, vienen del starter)

| Modo | Atajo | Acción |
|------|-------|--------|
| Normal | `;` | Entra en modo comando (igual que `:`) |
| Inserción | `jk` | Sale a modo normal (igual que `Esc`) |

## Archivos que SÍ se editan habitualmente

| Archivo | Qué configurar |
|---------|----------------|
| `lua/chadrc.lua` | Tema base46, statusline, nvdash, UI |
| `lua/configs/lspconfig.lua` | Servidores LSP activos |
| `lua/configs/conform.lua` | Formatters por tipo de archivo |
| `lua/mappings.lua` / `lua/options.lua` | Atajos y opciones propias |
| `lua/plugins/*.lua` | Añadir/quitar plugins (un archivo o una entrada por plugin) |

## Archivos que NO se tocan (gestión NvChad)

- `init.lua` — Punto de entrada, gestiona carga de lazy.nvim + NvChad
- El núcleo de NvChad vive como plugin en `~/.local/share/nvim/lazy/NvChad` (se actualiza con `:Lazy sync`); no se edita

## ⚠️ Antes de editar

1. **Respaldar:**
   ```bash
   cp -R ~/.config/nvim ~/.config/nvim.bak.$(date +%Y%m%d-%H%M%S)
   ```

2. **No asumas** que cada archivo propuesto en chats quedó creado. Verifica con `find` o `ls`.

3. **Edita `chadrc.lua`** para cambios de UI/tema y `configs/lspconfig.lua` para LSP.

4. **Crea archivos en `lua/plugins/`** para plugins extra (un archivo por plugin).

## Verificar que NvChad carga bien

```bash
nvim --headless -c "checkhealth" -c "qa" 2>&1 | head -50
```

O dentro de Neovim:

```vim
:checkhealth
:Lazy
```

---

> **Siguiente paso:** [03. Plugin vim-be-good](../05-neovim-nvchad/03-plugin-vim-be-good.md)
