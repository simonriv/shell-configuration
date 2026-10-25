# 01. Ghostty — Apariencia

> **Sección original:** 1.3 Transparencia, 1.4 Barra de título y botones de ventana

## Transparencia del fondo

Para hacer translúcido el fondo de Ghostty:

```ini
background-opacity = 0.85
```

| Valor | Efecto |
|-------|--------|
| `1.0` | Totalmente opaco (por defecto) |
| `0.85` | Semi-transparente (recomendado inicial) |
| `0.7` - `0.9` | Rango usual de uso |
| `< 0.5` | Muy transparente, puede dificultar lectura |

> **Nota:** La apariencia final también depende del fondo de escritorio de macOS y de la configuración de "Reducir transparencia" en Accesibilidad.

## Barra de título y botones de ventana

### Ocultar solo los botones (cerrar, minimizar, maximizar)

```ini
macos-window-buttons = hidden
```

### Ocultar toda la barra de título

```ini
macos-titlebar-style = hidden
```

## ⚠️ Advertencias importantes

Las siguientes opciones **causaron problemas en pruebas anteriores** y **no deben añadirse** sin una razón concreta y verificada:

| Opción | Problema |
|--------|----------|
| `maximize = true` | Causó comportamiento inesperado al iniciar |
| `macos-titlebar-style = tabs` | Interfirió con la gestión de pestañas/ventanas |

> **Regla:** Si no estás seguro de una opción, no la añadas. Prueba una a una y verifica.

## Combinación recomendada (inicial)

```ini
# Transparencia sutil
background-opacity = 0.85

# Ocultar botones de ventana, mantener barra de título para arrastrar
macos-window-buttons = hidden
```

## Probar cambios

1. Guarda el archivo `config.ghostty`
2. Abre una nueva ventana: `Cmd + N`
3. Verifica el efecto visual
4. Si no se ve el cambio, reinicia Ghostty completamente (`Cmd + Q` → abrir de nuevo)

---

> **Siguiente paso:** [04. Validación y respaldo](../01-ghostty/04-validacion-respaldo.md)
