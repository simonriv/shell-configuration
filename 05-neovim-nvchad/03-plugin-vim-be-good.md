# 05. Neovim y NvChad \u2014 Plugin vim-be-good

> **Secci\u00f3n original:** 6.3 Plugin `vim-be-good`

## Qu\u00e9 es

Un **juego interactivo** dentro de Neovim para practicar movimientos de Vim (h, j, k, l, w, b, e, gg, G, etc.).

## Instalaci\u00f3n (propuesta)

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

2. Esperar a que termine la instalaci\u00f3n (aparece en la interfaz Lazy).

## Jugar

```vim
:VimBeGood
```

Se abre una ventana con niveles progresivos. Completa cada reto para avanzar.

## Estado

> **Esta instalaci\u00f3n se present\u00f3 como una propuesta.**
>
> Verifica:
> - \u00bfExiste el archivo `~/.config/nvim/lua/plugins/vim-be-good.lua`?
> - \u00bfAparece en `:Lazy` como instalado?
> - \u00bfFunciona `:VimBeGood`?

## Notas

- `cmd = "VimBeGood"` = carga perezosa (lazy-load): el plugin solo se carga al ejecutar el comando.
- No afecta el tiempo de inicio de Neovim.
- Ideal para calentar manos antes de programar.

---

> **Siguiente paso:** [04. Tree-sitter](../05-neovim-nvchad/04-treesitter.md)
