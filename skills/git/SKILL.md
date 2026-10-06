---
name: git
description: Convenciones git y formato de mensajes de commit. Se activa cuando se generan mensajes de commit, se trabaja con historial git, o se usa /git:commit. Aplica Conventional Commits v1.0.0 de forma estricta en mensajes auto-generados.
---

# Git Conventions

Referencia de convenciones git para este usuario. El formato de mensajes de commit sigue estrictamente la especificacion Conventional Commits v1.0.0.

## Conventional Commits

Al generar un mensaje de commit, lee y sigue estrictamente `references/conventional-commits-v1.0.0.md`.

### Formato

```
<type>[(scope)][!]: <description>

[optional body]

[optional footer(s)]
```

### Tipos validos

| Tipo | Usar cuando... |
|------|----------------|
| `feat` | Se anade funcionalidad nueva (MINOR en SemVer) |
| `fix` | Se corrige un bug (PATCH en SemVer) |
| `docs` | Solo cambia documentacion |
| `style` | Formato, sin cambio de logica (whitespace, semicolons, etc.) |
| `refactor` | Cambio de codigo que no es fix ni feat |
| `perf` | Mejora de rendimiento |
| `test` | Anadir o corregir tests |
| `build` | Sistema de build o dependencias externas |
| `ci` | Configuracion de CI/CD |
| `chore` | Mantenimiento que no toca src ni test |
| `revert` | Revierte un commit anterior |

### Reglas para mensajes auto-generados

1. **Elegir type**: Analiza los cambios y elige el type que mejor describe la naturaleza del trabajo. Consulta la tabla de tipos y las reglas 2, 3 y 14 de la spec.

2. **Inferir scope**: Analiza los directorios y modulos afectados por los cambios.
   - Si los cambios se concentran en un directorio/modulo claro, usalo como scope: `feat(auth):`, `fix(parser):`
   - Si los cambios afectan multiples areas sin un modulo predominante, omite el scope: `refactor:`
   - El scope debe ser un sustantivo corto que describa la seccion del codebase (regla 4 de la spec)

3. **Escribir description**: Resumen corto e imperativo del cambio.
   - Minusculas (no capitalizar la primera letra)
   - Sin punto final
   - Maximo 50 caracteres en la primera linea
   - Imperativo: "add feature" no "added feature" ni "adds feature"

4. **Body** (opcional): Si los cambios son complejos o necesitan contexto adicional.
   - Separado por una linea en blanco despues de la description (regla 6)
   - Formato libre, puede tener multiples parrafos (regla 7)
   - Explica el "por que" del cambio, no solo el "que"

5. **Breaking changes**: Si el cambio rompe compatibilidad hacia atras.
   - Usar `!` antes de `:` en el type/scope: `feat(api)!: remove deprecated endpoint`
   - Y/o footer `BREAKING CHANGE: descripcion del cambio que rompe` (regla 11-13)

6. **Footers** (opcional): Para metadata adicional.
   - Formato: `Token: valor` o `Token #valor` (regla 8)
   - Tokens usan `-` en vez de espacios: `Reviewed-by`, `Refs` (regla 9)

### Mensajes proporcionados por el usuario

Cuando el usuario proporciona un mensaje con `-m`, **respetarlo tal cual sin modificar ni validar**. El formato Conventional Commits solo se aplica a mensajes auto-generados.
