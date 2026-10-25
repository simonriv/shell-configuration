# 01. Ghostty — Validación y respaldo

> **Sección original:** 1.5 Validar y respaldar

## Crear respaldo fechado (recomendado)

Antes de cualquier cambio en la configuración:

```bash
cp "$HOME/Library/Application Support/com.mitchellh.ghostty/config.ghostty" \
   "$HOME/Library/Application Support/com.mitchellh.ghostty/config.ghostty.bak.$(date +%Y%m%d-%H%M%S)"
```

Esto crea un archivo como `config.ghostty.bak.20250115-143022`.

## Ver opciones activas actuales

```bash
cat "$HOME/Library/Application Support/com.mitchellh.ghostty/config.ghostty"
```

## Verificar sintaxis / recargar

1. **Nueva ventana:** `Cmd + N` (aplica config al instante)
2. **Recarga manual:** `Cmd + Shift + ,` (atajo por defecto)
3. **Reinicio completo:** `Cmd + Q` → abrir Ghostty de nuevo

## Lista de opciones conocidas usadas en este entorno

| Opción | Valor ejemplo | Descripción |
|--------|---------------|-------------|
| `background-opacity` | `0.85` | Transparencia del fondo |
| `macos-window-buttons` | `hidden` | Oculta botones de ventana |
| `macos-titlebar-style` | `hidden` | Oculta barra de título completa |
| `font-family` | `"JetBrainsMono Nerd Font"` | Fuente (requiere Nerd Font instalada) |
| `font-size` | `14` | Tamaño de fuente en puntos |

## Buenas prácticas

1. **Un cambio a la vez** — modifica una opción, verifica, continúa.
2. **Respaldos con fecha** — nunca sobrescribas el `.bak` anterior.
3. **Documenta tus cambios** — añade comentarios en el archivo (`# Mi cambio: ...`).
4. **Si algo falla** — restaura el respaldo más reciente y vuelve a empezar.

```bash
# Restaurar respaldo más reciente (ejemplo)
cp "$HOME/Library/Application Support/com.mitchellh.ghostty/config.ghostty.bak.20250115-143022" \
   "$HOME/Library/Application Support/com.mitchellh.ghostty/config.ghostty"
```

---

> **Siguiente paso:** [01. Respaldos y limpieza de Zsh](../02-zsh/01-respaldos-limpieza.md)
