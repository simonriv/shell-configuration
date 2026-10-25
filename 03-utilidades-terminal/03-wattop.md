# 03. Utilidades de terminal — Wattop

> **Sección original:** 4.3 Wattop

## Qué es

Wattop es un monitor de terminal orientado a **cargas de IA y hardware Apple Silicon**. Muestra métricas de:
- CPU (performance + efficiency cores)
- GPU
- Neural Engine (ANE)
- Memoria unificada
- Consumo energético (watts)

## Verificar si está instalado

```bash
command -v wattop
wattop --help
```

## ⚠️ Estado de instalación

> **El comando exacto de instalación de Wattop no quedó confirmado en el historial disponible.**

Posibles métodos (verificar cuál se usó):

| Método | Comando (verificar) |
|--------|---------------------|
| Homebrew (si existe fórmula) | `brew install wattop` |
| Homebrew (cask) | `brew install --cask wattop` |
| Cargo (Rust) | `cargo install wattop` |
| Go | `go install github.com/...` |
| Binario directo | Descarga de GitHub Releases |
| Compilación manual | `git clone && make/cargo build` |

## Comportamiento observado

- **No mostraba todas las sesiones** de aplicaciones/terminales abiertas.
- **No detectaba Pi** (el agente de coding) como sesión identificable.
- Esto **no necesariamente indica un fallo**; depende de qué procesos y métricas exponga la herramienta.

## Qué hacer

1. **Verifica cómo lo instalaste** (revisa tu historial de shell: `history | grep wattop`).
2. **Consulta la documentación del proyecto** (GitHub README) para confirmar uso y limitaciones.
3. **Si no lo necesitas**, no es obligatorio para el entorno base.

## Alternativas de monitoreo

- `btop` — Monitor general de procesos (sí confirmado instalado)
- `htop` — Clásico, `brew install htop`
- `istats` — Sensores de temp/ventilador/batería (`gem install iStats` o `brew install istats`)
- `powermetrics` — Herramienta nativa macOS (requiere sudo): `sudo powermetrics --samplers smc`

---

> **Siguiente paso:** [04. Fastfetch al iniciar](../03-utilidades-terminal/04-fastfetch.md)
