# Abrir un Issue en GitHub

Abrir un issue en GitHub es una forma efectiva de comunicar problemas, errores o solicitudes de características en un proyecto. A continuación, se detalla el proceso para abrir un issue simple.

## Pasos para abrir un issue

1. **Navegar al repositorio**: Ve al repositorio de GitHub donde deseas abrir el issue.

2. **Ir a la pestaña de "Issues"**: Haz clic en la pestaña "Issues" en la parte superior del repositorio.

3. **Crear un nuevo issue**: Haz clic en el botón "New issue".

4. **Escribir un título claro**: En el campo de título, escribe un resumen breve y claro del problema o solicitud.

5. **Describir el problema o solicitud**: En el campo de descripción, proporciona detalles sobre el problema o la solicitud. Incluye información relevante como:
   - Pasos para reproducir el problema.
   - Comportamiento esperado.
   - Comportamiento actual.
   - Capturas de pantalla o ejemplos de código si es necesario.

6. **Etiquetas y asignaciones**: Si es necesario, agrega etiquetas o asigna el issue a un colaborador.

7. **Enviar el issue**: Haz clic en el botón "Submit new issue" para crear el issue.

## Ejemplo de un issue

**Título**: Error al cargar la página principal

**Descripción**:
Al intentar acceder a la página principal del sitio, se muestra un error 404. Esto ocurre al hacer clic en el enlace de inicio desde cualquier otra página del sitio.

**Pasos para reproducir**:

1. Ir a la página de contacto.
2. Hacer clic en el enlace "Inicio".
3. Observar el error 404.

**Comportamiento esperado**: La página principal debería cargarse correctamente.

**Comportamiento actual**: Se muestra un error 404.

Este formato ayuda a los colaboradores a entender rápidamente el problema y a tomar medidas para resolverlo.

## Formato recomendado para crear issues

Usa esta estructura para mantener claridad y facilitar el seguimiento.

1. Título
    - Breve y específico. Ejemplos:
       - `feat: exportar reporte a CSV`
       - `bug: error 500 al guardar usuario`

2. Contexto / Descripción
    - ¿Qué se necesita y por qué? Incluye enlaces y referencias.

3. Pasos para reproducir (si aplica)
    - Lista numerada con pasos mínimos y datos de ejemplo.

4. Comportamiento esperado vs actual
    - Esperado: …
    - Actual: …

5. Criterios de aceptación / Definition of Done
    - [ ] Condición verificable 1
    - [ ] Condición verificable 2

6. Evidencia
    - Capturas, logs o snippet de código breve.

7. Metadatos
    - Labels: `bug` | `feature` | `documentation` | prioridad
    - Milestone: versión o sprint
    - Asignado(s): responsable(s)

### Plantilla sugerida (Markdown)

```markdown
## Descripción
Breve resumen del problema/solicitud y objetivo.

## Contexto
¿Por qué es necesario? Enlaces y referencias.

## Pasos para reproducir (si aplica)
1. …
2. …
3. …

## Comportamiento esperado
…

## Comportamiento actual
…

## Criterios de aceptación
- [ ] …
- [ ] …

## Evidencia
Capturas, logs, snippets.

## Metadatos
Labels: … | Milestone: … | Asignado a: …
```

### Opcional: Issue Forms (YAML) en `.github/ISSUE_TEMPLATE/`

```yaml
name: Bug report
description: Reporta un problema
title: "bug: <resumen>"
labels: [bug]
body:
   - type: textarea
      id: description
      attributes:
         label: Descripción
         description: ¿Qué ocurre y por qué importa?
      validations:
         required: true
   - type: textarea
      id: steps
      attributes:
         label: Pasos para reproducir
         placeholder: |
            1. …
            2. …
            3. …
   - type: textarea
      id: expected
      attributes:
         label: Comportamiento esperado
   - type: textarea
      id: actual
      attributes:
         label: Comportamiento actual
   - type: checkboxes
      id: acceptance
      attributes:
         label: Criterios de aceptación
         options:
            - label: Criterio 1
            - label: Criterio 2
```

## Mejores prácticas y recomendaciones

- Un tema por issue; si hay varios, divídelos en issues más pequeños.
- Titula con prefijos útiles: `bug:`, `feat:`, `docs:`, `chore:`.
- Agrega labels y milestone al crearlo; evita que queden sin clasificar.
- Incluye criterios de aceptación claros y medibles.
- Referencia contexto y decisiones previas; enlaza PRs o issues relacionados.
- Para bugs, siempre incluye pasos de reproducción y evidencia.
- No compartas secretos/credenciales en capturas o logs.
- Usa `Fixes #<n>` en el PR para cerrar el issue automáticamente al fusionar.

## Comandos PowerShell (GitHub CLI `gh`)

Ejemplos para crear y gestionar issues desde la terminal de PowerShell.

```powershell
# Variables opcionales
$repo = "<owner>/<repo>"          # ej. andres-olarte396/github-projects-learning
$title = "feat: exportar reporte a CSV"
$body = @"
## Descripción
Exportar reporte a CSV desde la vista de resultados.

## Criterios de aceptación
- [ ] Botón "Exportar CSV" visible
- [ ] Archivo descargado con separador ","
"@

# Crear issue (en el repo actual si estás dentro de la carpeta git)
gh issue create --title $title --body $body

# Crear issue con metadatos (repo, labels, assignee y milestone)
gh issue create --repo $repo --title $title --body $body --label feature,high\ priority --assignee <usuario> --milestone "Sprint 1"

# Listar issues abiertos con un label
gh issue list --repo $repo --label feature --state open

# Añadir etiquetas a un issue existente
gh issue edit 123 --add-label bug --repo $repo

# Asignar responsable(s)
gh issue edit 123 --add-assignee <usuario> --repo $repo

# Comentar en un issue
gh issue comment 123 --body "Gracias, lo reviso"

# Cerrar / reabrir un issue
gh issue close 123 --repo $repo
gh issue reopen 123 --repo $repo
```
