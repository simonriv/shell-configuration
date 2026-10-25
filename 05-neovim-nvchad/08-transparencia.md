# 05. Neovim y NvChad -- Transparencia en Neovim

> **Seccion original:** 6.8 Transparencia en Neovim

## Comando para alternar transparencia

Dentro de Neovim:

```vim
:lua require("base46").toggle_transparency()
```

## Qué hace

- Alterna el fondo transparente del tema base46 (el motor de temas de NvChad).
- **Independiente** de la transparencia de Ghostty (`background-opacity`).

## Si falla

| Error | Causa | Solución |
|-------|-------|----------|
| `module 'base46' not found` | Versión de NvChad distinta | Revisa `:help base46` o changelog |
| `attempt to call a nil value` | API cambiada | Busca en `:NvCheatsheet` o docs NvChad |
| No hace nada visual | Ghostty ya opaco / tema sin soporte | Verifica `background-opacity` en Ghostty |

## Transparencia: Terminal vs Editor

| Capa | Configuración | Efecto |
|------|---------------|--------|
| **Ghostty** | `background-opacity = 0.85` | Fondo de TODA la ventana terminal |
| **Neovim (base46)** | `toggle_transparency()` | Fondo solo del editor (buffers, UI) |

> Pueden combinarse: Ghostty semi-transparente + Neovim transparente = efecto "vidrio" total.

## Hacerlo persistente

En `lua/chadrc.lua`:

```lua
M.base46 = {
  theme = "tud tema",
  transparency = true,  -- true = transparente por defecto
}
```

Luego `:Lazy sync` y reinicia Neovim.

## Verificar tema actual

```vim
:lua print(vim.g.base46_theme)
:NvCheatsheet  -- busca seccion "Theme" o "Transparency"
```

---

> **Siguiente paso:** [01. Chequeos rápidos](../06-comprobaciones/01-chequeos-rapidos.md)
