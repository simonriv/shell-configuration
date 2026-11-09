# 02. Zsh — Starship (preset Jetpack personalizado)

> **Sección original:** 3.4 Starship Jetpack

## Verificar instalación

```bash
starship --version
starship preset --list
```

## Punto de partida: preset Jetpack

La configuración parte del preset **Jetpack** (compacto, prompt a la izquierda e información a la derecha):

```bash
# Sobrescribe ~/.config/starship.toml con el preset original
starship preset jetpack -o ~/.config/starship.toml
```

Sobre esa base se hicieron las personalizaciones de la sección siguiente. La copia completa está en [`examples/starship/starship.toml`](../examples/starship/starship.toml).

## Personalizaciones sobre Jetpack

| Cambio | Detalle |
|--------|---------|
| **Iconos Nerd Font** | Los símbolos geométricos del preset (`◫`, `⊃`, `∩`…) se sustituyeron por iconos Nerd Font en lenguajes (node, bun, deno, lua, python, ruby, rust, swift, go, java…), herramientas (docker, aws, conda…), batería, memoria y `nix_shell` |
| **Formato de lenguajes** | `" [$symbol](italic)[$version]($style)"`: icono + versión, sin la etiqueta de texto (`node`, `py`, `rs`…) del preset |
| **Directorio** | `truncation_symbol = "…/"` y candado Nerd Font en `read_only` |
| **`right_format`** | Empieza con `\` para que no haya salto de línea al principio del bloque derecho |

> **Requisito:** una Nerd Font en la terminal. En Ghostty está `font-family = JetBrainsMono Nerd Font` (cask `font-jetbrains-mono-nerd-font`). Sin ella los iconos se ven como cuadros.

> **Nota:** `[git_branch]` define `symbol`, pero su `format` no incluye `$symbol`, así que el icono de rama **no se muestra**. Para verlo, cambia el formato a `" [$symbol$branch(:$remote_branch)]($style)"`.

## Estructura del prompt

```toml
format = """($nix_shell$container$fill$git_metrics\n)$cmd_duration\
$hostname\
$localip\
$shlvl\
$shell\
$env_var\
$jobs\
$sudo\
$username\
$character"""

right_format = """\
$singularity\
$kubernetes\
$directory\
$vcsh\
$fossil_branch\
$git_branch\
$git_commit\
$git_state\
$git_status\
$hg_branch\
$pijul_channel\
$docker_context\
$package\
$c\
$cpp\
$cmake\
$cobol\
$daml\
$dart\
$deno\
$dotnet\
$elixir\
$elm\
$erlang\
$fennel\
$fortran\
$golang\
$guix_shell\
$haskell\
$haxe\
$helm\
$java\
$julia\
$kotlin\
$gradle\
$lua\
$maven\
$nim\
$nodejs\
$bun\
$ocaml\
$opa\
$perl\
$php\
$pulumi\
$purescript\
$python\
$raku\
$rlang\
$red\
$ruby\
$rust\
$scala\
$solidity\
$swift\
$terraform\
$vlang\
$vagrant\
$xmake\
$zig\
$buf\
$conda\
$pixi\
$meson\
$spack\
$memory_usage\
$aws\
$gcloud\
$openstack\
$azure\
$crystal\
$custom\
$status\
$os\
$battery\
$time"""
```

- **Izquierda (`format`):** línea opcional con `nix_shell`, `container` y métricas de git; después duración del último comando, host, usuario y el carácter del prompt (`◎` si va bien, `○` si el comando falló).
- **Derecha (`right_format`):** directorio, rama y estado de git, versiones de lenguajes y hora.

## Extractos de la configuración

```toml
[directory]
home_symbol = "⌂"
truncation_length = 2
truncation_symbol = "…/"
read_only = " 󰌾"
use_os_path_sep = true
style = "italic blue"
format = '[$path]($style)[$read_only]($read_only_style)'
repo_root_style = 'bold blue'
repo_root_format = '[$before_root_path]($before_repo_root_style)[$repo_root]($repo_root_style)[$path]($style)[$read_only]($read_only_style) [△](bold bright-blue)'

[git_branch]
format = " [$branch(:$remote_branch)]($style)"
symbol = " "
style = "italic bright-blue"
truncation_symbol = "⋯"
truncation_length = 11
ignore_branches = ["main", "master"]
only_attached = true

[nodejs]
format = " [$symbol](italic)[$version](bold bright-green)"
version_format = "${raw}"
symbol = " "
detect_files = ["package-lock.json", "yarn.lock"]
detect_folders = ["node_modules"]
detect_extensions = []

[battery]
format = "[ $percentage $symbol]($style)"
full_symbol = "󰁹 "
charging_symbol = "󰂄 "
discharging_symbol = "󰂃 "
unknown_symbol = "󰂑 "
empty_symbol = "󰂎 "
```

## Respaldar antes de cambiar

```bash
cp ~/.config/starship.toml ~/.config/starship.toml.bak.$(date +%Y%m%d-%H%M%S)
```

## Probar cambios sin recargar shell

```bash
# Renderiza el prompt actual en stdout
starship prompt

# Muestra la configuración efectiva (falla si el TOML es inválido)
starship print-config >/dev/null && echo "TOML OK"
```

## Solución de problemas

| Problema | Causa probable | Solución |
|----------|----------------|----------|
| Prompt no cambia | Config no recargada | `source ~/.zshrc` o nueva terminal |
| Error al iniciar | Sintaxis TOML inválida | `starship print-config` para validar |
| Iconos rotos (cuadros) | Falta Nerd Font | Instala `font-jetbrains-mono-nerd-font` (brew cask) y selecciónala en Ghostty |
| Prompt lento en repos grandes | `git_metrics` / `git_status` | `starship timings` para ver qué módulo tarda |

---

> **Siguiente paso:** [06. Recarga y verificación](../02-zsh/06-recarga-verificacion.md)
