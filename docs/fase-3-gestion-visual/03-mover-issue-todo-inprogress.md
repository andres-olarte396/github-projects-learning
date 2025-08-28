# Mover un issue de `To Do` a `In Progress`

Mover issues entre columnas refleja el estado actual de cada tarea.

## Pasos para mover un issue

1. Abre tu Project (Kanban) en GitHub.
2. Localiza el issue en la columna `To Do`.
3. Haz clic y arrastra el issue a la columna `In Progress`.
4. El cambio se guarda automáticamente y todos los miembros del proyecto pueden verlo.

### Ejemplo visual

![Mover issue entre columnas](https://docs.github.com/assets/images/help/projects/move-card-between-columns.png)

---

> **Consejo:** Actualiza el estado de los issues frecuentemente para mantener el tablero al día.

## Formato recomendado al iniciar trabajo (In Progress)

Antes de mover un issue a `In Progress`, verifica que cumpla:

- DoR (Definition of Ready) cumplida: objetivo claro y criterios de aceptación.
- Dependencias identificadas; si existe bloqueo, marca `status: blocked`.
- Etiquetas mínimas: `type: ...`, `priority: ...` y opcional `area: ...`.
- Asignatario definido (quién lo trabajará).
- Milestone del Sprint (si aplica).

Acciones sugeridas al mover a `In Progress`

- Asignarte el issue y cambiar etiqueta de estado a `status: in progress`.
- Crear rama de trabajo y referenciar el issue en commits/PR.
- Añadir notas o checklist técnico si ayuda al seguimiento.

Nota: El formato para crear/añadir issues al tablero está detallado en `02-anadir-issues-tablero.md`.

## Mejores prácticas

- Usa reglas del Project para que al añadir la etiqueta `status: in progress` se mueva a la columna correspondiente.
- Limita WIP: no tomes nuevos issues sin terminar los actuales.
- Si el issue queda bloqueado, actualiza a `status: blocked` y registra causa/acción.
- Crea el PR temprano en modo draft y vincúlalo al issue para visibilidad.

## Comandos PowerShell (GitHub CLI `gh`)

```powershell
# Variables
$owner = "<owner>"                   # ejemplo: andres-olarte396
$repo  = "<repo>"                    # ejemplo: github-projects-learning
$num   = <numero_del_issue>           # ejemplo: 123

# 1) Asignarte el issue y marcarlo In Progress mediante etiquetas
gh issue edit $num --repo "$owner/$repo" --add-assignee @me `
	--add-label "status: in progress" --remove-label "status: needs triage"

# 2) Añadir o ajustar prioridad/tipo si faltan
gh issue edit $num --repo "$owner/$repo" --add-label "type: feature" --add-label "priority: high"

# 3) Agregar un comentario de inicio de trabajo
gh issue comment $num --repo "$owner/$repo" --body "Iniciando trabajo. Plan: ..."

# 4) (Opcional) Crear una rama local para este issue
# Requiere git instalado y un clon del repo local.
git checkout -b issue-$num-in-progress

# 5) (Opcional) Si usas reglas de Project por etiquetas, el item se moverá automáticamente.
# Si no, realiza el movimiento en la UI del Project.
```

> Nota: El soporte CLI para cambiar el campo `Status` de Projects v2 directamente es limitado; se recomienda usar reglas del Project basadas en etiquetas o realizar el cambio desde la UI.
