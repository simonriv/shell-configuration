# 02. Zsh — Respaldos y limpieza

> **Sección original:** 2. Respaldos y limpieza de Zsh

## Archivos de configuración de Zsh

| Archivo | Propósito | Prioridad |
|---------|-----------|-----------|
| `~/.zshrc` | Configuración principal (interactiva) | **Esencial** |
| `~/.zprofile` | Login shell (similar a `.bash_profile`) | Opcional |
| `~/.zshenv` | Siempre se carga (variables de entorno) | Opcional |
| `~/.zlogin` | Al iniciar sesión (login shell) | Raro |

> No todos tienen que existir. `~/.zshrc` es el que casi siempre se edita.

## Ver qué archivos existen

```bash
ls -la ~/.zsh*
```

## Crear respaldo antes de editar

```bash
# Crear carpeta de respaldos
mkdir -p ~/.config/backups/zsh

# Respaldar archivos existentes (con fecha/hora)
cp -p ~/.zshrc ~/.config/backups/zsh/zshrc.$(date +%Y%m%d-%H%M%S).bak 2>/dev/null
cp -p ~/.zprofile ~/.config/backups/zsh/zprofile.$(date +%Y%m%d-%H%M%S).bak 2>/dev/null
cp -p ~/.zshenv ~/.config/backups/zsh/zshenv.$(date +%Y%m%d-%H%M%S).bak 2>/dev/null
cp -p ~/.zlogin ~/.config/backups/zsh/zlogin.$(date +%Y%m%d-%H%M%S).bak 2>/dev/null
```

> `2>/dev/null` evita errores si el archivo no existe. `-p` preserva timestamps y permisos.

## Ver respaldos creados

```bash
ls -la ~/.config/backups/zsh/
```

## Revisar diferencias con un respaldo

```bash
# Reemplaza ARCHIVO_DE_RESPALDO por el nombre real
diff -u ~/.config/backups/zsh/ARCHIVO_DE_RESPALDO ~/.zshrc
```

## ⚠️ Importante

- **No borres respaldos antiguos** hasta confirmar que la nueva configuración funciona.
- Los nombres de respaldo históricos pueden variar; usa `ls` para ver los reales.
- Esta sección documenta **cómo** hacer respaldos, no los nombres exactos de respaldos previos.

---

> **Siguiente paso:** [02. Componentes del entorno](../02-zsh/02-componentes.md)
