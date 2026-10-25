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

## Estructura típica NvChad

```text
~/.config/nvim/
├── init.lua                 # Entry point (carga chadrc + lazy)
├── lua/
│   ├── chadrc.lua           # CONFIG PRINCIPAL: tema, UI, plugins base
│   ├── plugins/             # Plugins personalizados (un archivo por plugin)
│   │   ├── init.lua         # Lista de specs de plugins extra
│   │   ├── vim-be-good.lua  # Ejemplo: plugin de práctica
│   │   └── ...
│   └── config/              # Configs específicas (opcional)
└── ...
```

## Archivos que SÍ se editan habitualmente

| Archivo | Qué configurar |
|---------|----------------|
| `lua/chadrc.lua` | Tema base46, statusline, nvim-tree, mason, LSP servers, UI |
| `lua/plugins/*.lua` | Añadir/quitar/plugins custom (ej: vim-be-good, LSP extra) |

## Archivos que NO se tocan (gestión NvChad)

- `init.lua` — Punto de entrada, gestiona carga de chadrc + lazy
- `lua/core/` — Núcleo de NvChad (actualizaciones lo sobrescriben)
- `lua/plugins/` — Plugins base de NvChad (se actualizan con `:Lazy sync`)

## ⚠️ Antes de editar

1. **Respaldar:**
   ```bash
   cp -R ~/.config/nvim ~/.config/nvim.bak.$(date +%Y%m%d-%H%M%S)
   ```

2. **No asumas** que cada archivo propuesto en chats quedó creado. Verifica con `find` o `ls`.

3. **Edita `chadrc.lua`** para cambios de UI/tema/LSP base.

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
