# Documentación del entorno de terminal en macOS
>
> **Propósito:** Guía completa de instalación y configuración de Ghostty, Zsh, Starship, tmux, Neovim/NvChad y utilidades de terminal en macOS (Apple Silicon).
>
> **Origen:** Basado en el manual original `manual-terminal-macos-ghostty-zsh-tmux-nvchad.md`, reorganizado por temas para facilitar la navegación y el mantenimiento.

---

## Índice de contenidos

### 00. Prerrequisitos
- [01. Verificación inicial](00-prerrequisitos/01-verificacion-inicial.md) — Comprobar arquitectura, macOS, Homebrew, shell y versiones.

### 01. Ghostty (Terminal)
- [01. Instalación](01-ghostty/01-instalacion.md) — Instalar con Homebrew.
- [02. Configuración](01-ghostty/02-configuracion.md) — Ubicación y edición del archivo `config.ghostty`.
- [03. Apariencia](01-ghostty/03-apariencia.md) — Transparencia, barra de título y botones de ventana.
- [04. Validación y respaldo](01-ghostty/04-validacion-respaldo.md) — Respaldos fechados y verificación de opciones activas.

### 02. Zsh (Shell)
- [01. Respaldos y limpieza](02-zsh/01-respaldos-limpieza.md) — Backup de archivos de configuración existentes.
- [02. Componentes del entorno](02-zsh/02-componentes.md) — Starship, zoxide, fzf, eza, plugins de Zsh.
- [03. Verificación de instalación](02-zsh/03-verificacion-instalacion.md) — Comandos para comprobar qué está instalado.
- [04. Configuración de .zshrc](02-zsh/04-configuracion-zshrc.md) — Orden de carga recomendado y ejemplo orientativo.
- [05. Starship (preset Jetpack)](02-zsh/05-starship.md) — Configuración y verificación del prompt.
- [06. Recarga y verificación](02-zsh/06-recarga-verificacion.md) — `source ~/.zshrc` y comprobación de sintaxis.

### 03. Utilidades de terminal
- [01. Herramientas del entorno](03-utilidades-terminal/01-herramientas.md) — Tabla de referencia: fastfetch, btop, lazygit, bat, eza, fzf, zoxide, wattop.
- [02. Instalación con Homebrew](03-utilidades-terminal/02-instalacion-homebrew.md) — Comandos de instalación habituales.
- [03. Wattop](03-utilidades-terminal/03-wattop.md) — Monitor para Apple Silicon, notas de verificación.
- [04. Fastfetch al iniciar](03-utilidades-terminal/04-fastfetch.md) — Mostrar resumen del sistema en shells interactivas.

### 04. tmux (Multiplexor)
- [01. Instalación](04-tmux/01-instalacion.md) — Instalar y comprobar versión.
- [02. Prefijo personalizado](04-tmux/02-prefijo.md) — Ctrl + Space como prefijo.
- [03. Paneles](04-tmux/03-paneles.md) — Dividir, navegar y redimensionar paneles.
- [04. Layouts](04-tmux/04-layouts.md) — Recorrer distribuciones con prefijo + Space.
- [05. Recarga y diagnóstico](04-tmux/05-recarga-diagnostico.md) — Recargar config, listar atajos, gestionar sesiones.
- [06. Configuración consolidada](04-tmux/06-configuracion-consolidada.md) — Bloque completo de `~/.tmux.conf` conocido.

### 05. Neovim y NvChad
- [01. Conceptos y atajos](05-neovim-nvchad/01-conceptos-atajos.md) — Tecla líder, atajos principales, comandos útiles.
- [02. Estructura de configuración](05-neovim-nvchad/02-estructura-configuracion.md) — Carpeta `~/.config/nvim/` y cómo inspeccionarla.
- [03. Plugin vim-be-good](05-neovim-nvchad/03-plugin-vim-be-good.md) — Juego para practicar movimientos de Vim.
- [04. Tree-sitter](05-neovim-nvchad/04-treesitter.md) — Parsers instalados, CLI, health check.
- [05. Mason y servidores LSP](05-neovim-nvchad/05-mason-lsp.md) — Estado de vtsls, astro, cssls, html, lua_ls.
- [06. Herramientas para Next.js](05-neovim-nvchad/06-herramientas-nextjs.md) — vtsls, eslint, tailwind, prettier, lazygit.
- [07. Conform y formateo](05-neovim-nvchad/07-conform-formateo.md) — Formateo con conform.nvim, stylua, prettier.
- [08. Transparencia en Neovim](05-neovim-nvchad/08-transparencia.md) — Toggle de transparencia independiente de Ghostty.

### 06. Comprobaciones rápidas
- [01. Chequeos de salud](06-comprobaciones/01-chequeos-rapidos.md) — Scripts para verificar herramientas, Zsh, tmux y Neovim.

### 07. Mantenimiento
- [01. Respaldos antes de editar](07-mantenimiento/01-respaldos.md) — Backup de archivos críticos.
- [02. Actualizaciones](07-mantenimiento/02-actualizaciones.md) — Homebrew update/outdated, actualizaciones selectivas.
- [03. Reglas de mantenimiento](07-mantenimiento/03-reglas.md) — Buenas prácticas para cambios futuros.

### 08. Estado de confirmación
- [01. Confirmado](08-estado/01-confirmado.md) — Qué quedó verificado en la conversación.
- [02. Pendiente](08-estado/02-pendiente.md) — Qué requiere verificación en la máquina local.

---

## Cómo usar esta documentación

1. **Empieza por** `00-prerrequisitos/01-verificacion-inicial.md` para confirmar tu entorno base.
2. **Sigue el orden numérico** de las carpetas (01 → 08) para una instalación completa.
3. **Cada archivo es independiente** — puedes consultar solo lo que necesites.
4. **Antes de editar cualquier configuración**, lee `07-mantenimiento/01-respaldos.md`.
4. **Consulta `08-estado/02-pendiente.md`** para saber qué verificar en tu máquina actual.

---

## Convenciones

- **Rutas**: `~/` = `$HOME`. Las rutas de macOS usan comillas cuando contienen espacios.
- **Comandos**: Bloques de código con `$` indican comandos de terminal.
- **Archivos de config**: Se muestra la ruta típica; verifica en tu sistema.
- **⚠️ Advertencia**: Indica opciones que causaron problemas o requieren verificación.
- **📝 Nota**: Información orientativa, no copia exacta del estado final.

---

## Licencia / Uso

Documentación personal para referencia y reconstrucción del entorno. Libre uso y modificación.
