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

## Instalación

Instalado como **cask de Homebrew**:

```bash
brew install --cask wattop
wattop --version
# wattop v0.3.1-…
```

## Comportamiento observado

- **No mostraba todas las sesiones** de aplicaciones/terminales abiertas.
- **No detectaba Pi** (el agente de coding) como sesión identificable.
- Esto **no necesariamente indica un fallo**; depende de qué procesos y métricas exponga la herramienta.

## Qué hacer

1. **Consulta la documentación del proyecto** (GitHub README) para confirmar uso y limitaciones.
2. **Si no lo necesitas**, no es obligatorio para el entorno base.

## Alternativas de monitoreo

- `btop` — Monitor general de procesos (sí confirmado instalado)
- `htop` — Clásico, `brew install htop`
- `istats` — Sensores de temp/ventilador/batería (`gem install iStats` o `brew install istats`)
- `powermetrics` — Herramienta nativa macOS (requiere sudo): `sudo powermetrics --samplers smc`

---

> **Siguiente paso:** [04. Fastfetch al iniciar](../03-utilidades-terminal/04-fastfetch.md)
