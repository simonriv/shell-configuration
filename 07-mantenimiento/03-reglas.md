# 07. Mantenimiento -- Reglas de mantenimiento

> **Seccion original:** 8.3 Reglas de mantenimiento

## Reglas de oro

1. **Mantener copia de configuraciones antes de editar**
   - Ver [01. Respaldos](../07-mantenimiento/01-respaldos.md)
   - Nombres con fecha, no sobrescribir.

2. **NO reemplazar todo ~/.zshrc sin preservar variables y rutas de desarrollo**
   - Tu .zshrc tiene PATHs, SDKs, aliases personales.
   - Integra cambios selectivamente (ver [04. Configuración .zshrc](../02-zsh/04-configuracion-zshrc.md)).

3. **Recargar tmux tras cambios: `tmux source-file ~/.tmux.conf`**
   - Los keybindings no aplican solos.
   - Verifica con `tmux list-keys | grep tu-atajo`.

4. **Comprobar :LspInfo en archivo de codigo REAL, no en pantalla vacia**
   - LSP se adjunta segun filetype.
   - Abre .ts/.tsx/.lua real en proyecto real.

5. **Separar problemas por capa**
   | Capa | Qué configura | Dónde buscar fallos |
   |------|---------------|---------------------|
   | Terminal | Fuente, color, transparencia, GPU | `config.ghostty` |
   | Shell | Prompt, aliases, plugins, PATH | `~/.zshrc` |
   | Multiplexor | Paneles, sesiones, keybindings | `~/.tmux.conf` |
   | Editor | LSP, plugins, tema, keymaps | `~/.config/nvim/` |

6. **Registrar en esta documentacion las futuras modificaciones confirmadas**
   - Actualiza el archivo correspondiente en `docs/`
   - Marca en [08. Estado](../08-estado/) qué quedó verificado.

## Flujo de cambio seguro

```
1. Leer doc relevante en docs/
2. Hacer respaldo con fecha
3. Editar un solo archivo / una sola cosa
4. Recargar / reiniciar capa afectada
5. Verificar que funciona
6. Documentar cambio en docs/
7. Commit si usas git para dotfiles
```

## Versionado de dotfiles (opcional pero recomendado)

```bash
# En tu repo de dotfiles
git add .
git commit -m "config: ajustar transparencia Ghostty a 0.85"
git push
```

---

> **Siguiente paso:** [01. Confirmado](../08-estado/01-confirmado.md)
