# 02. Zsh — Starship (preset Jetpack)

> **Sección original:** 3.4 Starship Jetpack

## Verificar instalación

```bash
starship --version
starship preset --list
```

## Preset Jetpack

El preset **Jetpack** fue elegido por su aspecto compacto y minimalista.

### Aplicar el preset

```bash
# Opción 1: Configurar vía archivo (recomendado)
# Editar ~/.config/starship.toml

# Opción 2: Aplicar preset directamente (sobrescribe config)
starship preset jetpack -o ~/.config/starship.toml
```

## Archivo de configuración

Ubicación: `~/.config/starship.toml`

### Ver configuración actual

```bash
cat ~/.config/starship.toml
```

### Ejemplo de configuración Jetpack

```toml
# ~/.config/starship.toml
# Preset Jetpack aplicado

format = """
$username\
$hostname\
$directory\
$git_branch\
$git_status\
$cmd_duration\
$line_break\
$character"""

# Módulos deshabilitados para minimalismo
[username]
show_always = false

[hostname]
ssh_only = true

[directory]
truncation_length = 3
truncate_to_repo = true

[git_branch]
symbol = "🌱 "

[character]
success_symbol = "❯ "
error_symbol = "❯ "
vicmd_symbol = "❮ "
```

> **Nota:** El preset Jetpack puede cambiar entre versiones. Usa `starship preset jetpack -o ~/.config/starship.toml` para obtener la versión exacta actual.

## Respaldar antes de cambiar

```bash
cp ~/.config/starship.toml ~/.config/starship.toml.bak.$(date +%Y%m%d-%H%M%S)
```

## Probar cambios sin recargar shell

```bash
# Renderiza el prompt actual en stdout
starship prompt
```

## Solución de problemas

| Problema | Causa probable | Solución |
|----------|----------------|----------|
| Prompt no cambia | Config no recargada | `source ~/.zshrc` o nueva terminal |
| Error al iniciar | Sintaxis TOML inválida | `starship print-config` para validar |
| Iconos rotos | Falta Nerd Font | Instala `font-jetbrains-mono-nerd-font` (brew cask) |

---

> **Siguiente paso:** [06. Recarga y verificación](../02-zsh/06-recarga-verificacion.md)
