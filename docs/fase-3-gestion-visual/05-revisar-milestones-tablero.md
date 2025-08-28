# Revisar milestones reflejados en el tablero

Puedes ver cómo los issues asociados a milestones avanzan en el tablero Kanban.

## Pasos para revisar milestones en el tablero

1. Abre tu Project (Kanban) en GitHub.
2. Observa los issues en cada columna; si están vinculados a un milestone, verás la referencia en la tarjeta del issue.
3. Haz clic en el issue para ver detalles del milestone asociado.
4. Puedes filtrar o agrupar issues por milestone desde el tablero.

### Ejemplo visual

![Milestones en el tablero](https://docs.github.com/assets/images/help/projects/milestone-in-project-card.png)

---

> **Consejo:** Usa los milestones junto con el tablero para planificar y dar seguimiento a entregas parciales o sprints.

## Formato recomendado para revisar milestones en el tablero

- Vistas sugeridas (Projects v2)
	- Board: filtro por `milestone:"<Sprint o Release>"` y columnas por `Status`.
	- Table: columnas `Title`, `Assignees`, `Labels`, `Milestone`, `Status`, `Priority` y orden por `Priority`.
	- Saved views: una por Sprint actual y otra por Release.
- Campos clave
	- `Status` (Todo, In Progress, Blocked, Done)
	- `Priority` (High, Medium, Low)
	- `Milestone`
- Definición del milestone (resumen)
	- Título y fecha objetivo, objetivo del Sprint/Release y DoD asociado.
	- Para detalles de creación de milestones, ver `docs/fase-2-organizacion-basica/02-crear-milestones.md`.

## Mejores prácticas

- Mantén una vista filtrada por el milestone activo para standups y revisión.
- Controla bloqueos: revisa `Blocked` y asigna acciones de desbloqueo.
- Congela alcance después del 60% del Sprint salvo urgencias justificadas.
- Cierra el milestone al final y reubica pendientes al siguiente milestone con comentario.
- Usa etiquetas de `priority:` para ordenar el trabajo dentro del milestone.

## Comandos PowerShell (GitHub CLI `gh`)

```powershell
# Variables
$owner = "<owner>"                 # ejemplo: andres-olarte396
$repo  = "<repo>"                  # ejemplo: github-projects-learning
$ms    = "Sprint 1"                # nombre del milestone

# 1) Resumen de progreso del milestone
$issues = gh issue list --repo "$owner/$repo" --milestone $ms --json state,number,title,labels,url | ConvertFrom-Json
$open   = ($issues | Where-Object { $_.state -eq "OPEN" }).Count
$closed = ($issues | Where-Object { $_.state -eq "CLOSED" }).Count
$total  = $open + $closed
if ($total -gt 0) { $pct = [math]::Round(($closed / $total) * 100, 2) } else { $pct = 0 }
Write-Host "Milestone '$ms': $closed/$total cerrados ($pct%). Abiertos: $open"

# 2) Issues bloqueados dentro del milestone
$blocked = $issues | Where-Object { $_.labels -and ($_.labels.name -contains "status: blocked") }
$blocked | Select-Object number, title

# 3) Exportar a CSV para reporte
$san = ($ms -replace '[^A-Za-z0-9_-]','_')
$issues | Select-Object number, title, state, @{n="labels";e={ ($_.labels.name -join ";") }} |
	Export-Csv "./milestone-$san.csv" -NoTypeInformation -Encoding UTF8

# 4) Limpiar etiquetas de estado en issues cerrados (si aplica)
$closedInProgress = gh issue list --repo "$owner/$repo" --milestone $ms --state closed --label "status: in progress" --json number | ConvertFrom-Json
foreach ($i in $closedInProgress) { gh issue edit $($i.number) --repo "$owner/$repo" --remove-label "status: in progress" }

# 5) Triage: issues abiertos sin milestone
gh issue list --repo "$owner/$repo" --search "no:milestone state:open" --json number,title
```

> Nota: Para reflejar automáticamente el avance en Projects v2, configura reglas que actualicen `Status` y muevan tarjetas entre columnas cuando un issue cambie de estado o sea cerrado.
