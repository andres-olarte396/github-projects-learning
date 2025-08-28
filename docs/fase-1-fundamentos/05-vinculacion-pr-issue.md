# Vincular un PR a un Issue

Vincular un Pull Request (PR) a un issue es una práctica esencial en el desarrollo colaborativo. Esto no solo ayuda a mantener un registro claro de los cambios realizados, sino que también facilita el seguimiento del progreso de los problemas planteados.

## Importancia de Vincular PR a Issues

1. **Seguimiento Eficiente**: Al vincular un PR a un issue, se puede ver fácilmente qué cambios están relacionados con qué problemas.
2. **Cierre Automático**: Usar `Fixes #<número>` en la descripción del PR permite que el issue se cierre automáticamente una vez que el PR es fusionado.
3. **Mejora de la Colaboración**: Facilita la comunicación entre los miembros del equipo, ya que todos pueden ver el estado de los problemas y los cambios propuestos.

## Cómo Vincular un PR a un Issue

1. **Crear un Pull Request**: Después de realizar cambios en tu código, crea un PR en GitHub.
2. **Agregar la Referencia al Issue**: En la descripción del PR, incluye la línea `Fixes #<número>`, donde `<número>` es el número del issue que deseas vincular.
3. **Fusionar el PR**: Una vez que el PR sea revisado y aprobado, fusiónalo. El issue se cerrará automáticamente.

Siguiendo estos pasos, podrás mantener un flujo de trabajo organizado y eficiente en tus proyectos de GitHub.

## Formato recomendado para vincular PRs e Issues

Cuando crees el PR, incluye una sección específica para la relación con issues.

1. Resumen del cambio

   - Breve descripción del qué y por qué.

2. Relación con issues

   - Cierre automático: `Fixes #<n>` / `Closes #<n>` / `Resolves #<n>`.
   - Referencias sin cerrar: `Refs #<n>` o `Related to #<n>`.
   - Múltiples issues: `Fixes #12, Fixes #34`.

3. Cómo probar/validar

   - Pasos breves para verificar el resultado.

4. Checklist

    - [ ] CI verde
    - [ ] Tests/Docs actualizados (si aplica)

### Ejemplo de bloque en la descripción del PR

```markdown
## Relación con issues
Fixes #123
Refs #98
```

## Palabras clave de vinculación (y reglas)

- Palabras soportadas para cierre automático: `Fixes`, `Closes`, `Resolves` (y sus variantes en minúscula).
- El cierre automático ocurre cuando el PR se fusiona en la rama por defecto (por ejemplo, `main`) del mismo repositorio.
- Si el issue está en otro repositorio, no se cerrará automáticamente; deberás cerrarlo manualmente o con automatización.
- También funciona si la palabra clave está en el mensaje de commit que llega a la rama por defecto.

## Mejores prácticas

- Usa `Fixes #<n>` solo si el PR realmente cierra el issue; si no, usa `Refs #<n>`.
- Un PR por issue cuando sea posible; si cubre varios, indica cada uno claramente.
- Añade contexto en el PR y referencia discusiones/decisiones previas.
- Mantén la consistencia: usa siempre el mismo keyword para cierres automáticos.
- Verifica después del merge que el issue quedó cerrado y enlazado al PR.

## Ejemplos

### Mensaje de commit con referencia (sin cerrar)

```text
feat: agregar validación de entrada (refs #123)
```

### Mensaje de commit o PR que cierra el issue

```text
fix: corregir error en cálculo de totales

Closes #456
```

## Comandos PowerShell con GitHub CLI (gh)

Ejemplos para crear/editar PRs incluyendo vinculación con issues.

```powershell
# Variables de ejemplo
$base = "main"
$branch = "feature/lerp"
$title = "feat: interpolador lineal (lerp)"
$issue = 123
$body = @"
## Descripción
Implementa lerp(a, b, t) con casos base y prueba.

## Relación con issues
Fixes #$issue
"@

# Crear PR con cierre automático del issue
gh pr create --base $base --head $branch --title $title --body $body

# Si el PR ya existe, añadir la línea Fixes al cuerpo
$current = gh pr view --json body --jq ".body"
$newBody = $current + "`n`nFixes #$issue"
gh pr edit --body $newBody

# Referenciar sin cerrar (comentario en PR)
gh pr comment --body "Refs #$issue"

# Verificar relación en la web
gh pr view --web
```
