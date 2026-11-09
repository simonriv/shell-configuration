# 05. Neovim y NvChad — Plugin vim-be-good

> **Sección original:** 6.3 Plugin `vim-be-good`

## Qué es

Un **juego interactivo** dentro de Neovim para practicar movimientos de Vim (h, j, k, l, w, b, e, gg, G, etc.).

## Instalación (propuesta)

Crear archivo:

```text
~/.config/nvim/lua/plugins/vim-be-good.lua
```

Contenido:

```lua
return {
  {
    "ThePrimeagen/vim-be-good",
    cmd = "VimBeGood",
  },
}
```

## Activar

1. Dentro de Neovim:
   ```vim
   :Lazy sync
   ```

2. Esperar a que termine la instalación (aparece en la interfaz Lazy).

## Jugar

```vim
:VimBeGood
```

Se abre una ventana con niveles progresivos. Completa cada reto para avanzar.

## Estado

> **No instalado.** En la configuración actual no existe `~/.config/nvim/lua/plugins/vim-be-good.lua` ni el plugin aparece en `~/.local/share/nvim/lazy/`. Es opcional: sigue los pasos de arriba si lo quieres.

## Notas

- `cmd = "VimBeGood"` = carga perezosa (lazy-load): el plugin solo se carga al ejecutar el comando.
- No afecta el tiempo de inicio de Neovim.
- Ideal para calentar manos antes de programar.

---

> **Siguiente paso:** [04. Tree-sitter](../05-neovim-nvchad/04-treesitter.md)
