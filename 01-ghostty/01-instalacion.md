# 01. Ghostty — Instalación

> **Sección original:** 1.1 Instalar

## Requisitos previos

- Homebrew instalado y funcionando (ver [Verificación inicial](../00-prerrequisitos/01-verificacion-inicial.md))

## Instalar Ghostty

```bash
brew install --cask ghostty
```

## Abrir Ghostty

Desde la terminal:

```bash
open -a Ghostty
```

O desde el Launchpad / carpeta Aplicaciones.

## Verificar instalación

```bash
# Verificar que el binario está en PATH
command -v ghostty

# Ver versión
ghostty --version
```

## Notas

- Ghostty es una terminal GPU-accelerada escrita en Zig.
- La instalación por `--cask` coloca la app en `/Applications/Ghostty.app`.
- La configuración **no** se gestiona por Homebrew; cada usuario tiene su archivo en `~/Library/Application Support/com.mitchellh.ghostty/`.

---

> **Siguiente paso:** [02. Configuración](../01-ghostty/02-configuracion.md)
