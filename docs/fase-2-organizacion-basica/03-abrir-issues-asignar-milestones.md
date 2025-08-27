# Abrir issues y asignarlos a milestones

Los issues representan tareas, errores o mejoras. Asignarlos a milestones ayuda a organizar el trabajo y medir el progreso.

## Pasos para abrir un issue y asignarlo a un milestone

1. Ve a la pestaña **Issues** y haz clic en **New issue**.
2. Escribe un título y una descripción clara del problema o tarea.
3. En la barra lateral derecha, busca la sección **Milestone**.
4. Selecciona el milestone al que quieres asignar el issue.
5. Haz clic en **Submit new issue**.
6. Repite el proceso para crear al menos 3 issues, cada uno asignado a un milestone.

### Ejemplo visual

![Asignar milestone a un issue](https://docs.github.com/assets/images/help/issues/issue-milestone.png)

---

> **Consejo:** Asigna los issues a milestones según su prioridad o fecha de entrega esperada.

## Formato recomendado para asignar issues a milestones

Estandariza cómo decides qué entra a cada milestone (sprint o release).

1. Selección del milestone
	- Tipo: `Sprint N` (tiempo fijo) o `vX.Y` (alcance fijo)
	- Fechas: due date clara y conocida por el equipo
	- Capacidad: número máximo de issues o puntos estimados

2. Criterios del issue (Definition of Ready)
	- Título y descripción claros con objetivo
	- Criterios de aceptación definidos
	- Labels de `type:` y `priority:` aplicados
	- Dependencias identificadas (`status: blocked` si aplica)

3. Al asignar, completa
	- Milestone: `Sprint N` o `vX.Y`
	- Labels: tipo, prioridad, estado
	- Asignado(s): responsable del trabajo
	- Estimación (si usas sizing): `size: S/M/L` o puntos en la descripción

## Mejores prácticas

- No metas issues sin criterios de aceptación.
- Limita el WIP del milestone (capacidad realista del equipo).
- Evita sobrecargar con urgencias de última hora; replanifica si es necesario.
- Revisa a mitad del ciclo y ajusta (mover fuera lo que no llegará).
- Marca dependencias con `status: blocked` y ordénalas por prioridad.
- Cierra o mueve issues que cambian de alcance para mantener foco.

## Consultas útiles (listar por estado y milestone)

```powershell
# Repositorio
$repo = "<owner>/<repo>"  # ej. andres-olarte396/github-projects-learning

# Issues sin milestone
gh issue list --repo $repo --search "no:milestone" --state open --json number,title,labels

# Issues por milestone
gh issue list --repo $repo --milestone "Sprint 1" --state all --json number,title,state

# Issues abiertos con prioridad alta y sin milestone
gh issue list --repo $repo --search "no:milestone label:\"priority: high\" state:open" --json number,title,labels
```

## Comandos PowerShell (GitHub CLI `gh`) para asignar en lote

Ejemplos para asignar uno o varios issues a un milestone.

```powershell
$repo = "<owner>/<repo>"
$milestoneTitle = "Sprint 1"

# Obtener el número del milestone por título
$ms = gh api "repos/$repo/milestones?state=open" | ConvertFrom-Json | Where-Object { $_.title -eq $milestoneTitle }
if (-not $ms) { throw "Milestone '$milestoneTitle' no encontrado" }
$msNumber = $ms.number

# Asignar un issue específico
gh issue edit 123 --repo $repo --milestone $milestoneTitle

# Asignar en lote: todos los issues abiertos con una etiqueta
$issues = gh issue list --repo $repo --label "type: feature" --state open --json number | ConvertFrom-Json
foreach ($i in $issues) {
  gh issue edit $($i.number) --repo $repo --milestone $milestoneTitle
}

# Ver progreso del milestone (abiertos vs cerrados)
gh api "repos/$repo/milestones/$msNumber" | ConvertFrom-Json | Select-Object title,open_issues,closed_issues,due_on
```
