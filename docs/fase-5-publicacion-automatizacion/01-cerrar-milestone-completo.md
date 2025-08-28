# Cerrar un milestone completo

Cuando todos los issues de un milestone están cerrados, puedes cerrar el milestone para marcar la entrega como completada.

## Pasos

1. Ve a **Issues** > **Milestones** en tu repositorio.
2. Abre el milestone que quieres cerrar.
3. Verifica que todos los issues estén **Closed**.
4. Haz clic en **Close milestone**.
5. Registra notas de cierre si aplica (opcional).

---

> Consejo: Si quedan issues abiertos, muévelos a otro milestone antes de cerrar.

## Formato recomendado para el cierre de milestones

- Nombre
	- Sprint: `Sprint <N> - <YYYY-MM-DD> → <YYYY-MM-DD>`
	- Release: `v<MAJOR>.<MINOR>.<PATCH>`
- Criterios de cierre (DoD)
	- 100% de issues cerrados o reubicados justificadamente.
	- PRs fusionados y CI en verde.
	- Notas de cierre redactadas (cambios, riesgos, pendientes).
	- Documentación/CHANGELOG actualizado si aplica.
- Notas de cierre
	- Resumen de entregables, métricas (issues cerrados/pendientes), próximos pasos.

## Mejores prácticas

- Reubica issues abiertos al siguiente milestone con un comentario de contexto.
- Verifica dependencias/PRs pendientes antes de cerrar.
- Genera notas de versión básicas a partir de issues cerrados.
- Si usas Projects v2, valida que las tarjetas del milestone quedaron en `Done`.
- Mantén consistencia en la nomenclatura y fechas.

## Comandos PowerShell (GitHub CLI `gh`)

```powershell
# Variables
$owner   = "<owner>"                  # ejemplo: andres-olarte396
$repo    = "<repo>"                   # ejemplo: github-projects-learning
$msTitle = "Sprint 1"                 # título exacto del milestone a cerrar
$nextMs  = "Sprint 2"                 # siguiente milestone (opcional)

# 1) Ver milestones abiertos y obtener el número del milestone objetivo
$openMs = gh api repos/$owner/$repo/milestones -f state=open | ConvertFrom-Json
$msObj  = $openMs | Where-Object { $_.title -eq $msTitle } | Select-Object -First 1
if (-not $msObj) { Write-Error "Milestone '$msTitle' no encontrado entre abiertos."; return }
"Milestone '$($msObj.title)' (#$($msObj.number)) - Abiertos: $($msObj.open_issues) Cerrados: $($msObj.closed_issues)"

# 2) Revisar issues abiertos del milestone
$openIssues = gh issue list --repo "$owner/$repo" --milestone $msTitle --state open --json number,title | ConvertFrom-Json
if ($openIssues.Count -gt 0) {
	"Issues abiertos: $($openIssues.Count)"
	$openIssues | Format-Table number, title

	# 2a) (Opcional) Mover issues abiertos al siguiente milestone
	if ($nextMs) {
		foreach ($i in $openIssues) {
			gh issue edit $($i.number) --repo "$owner/$repo" --milestone $nextMs
		}
		"Movidos $($openIssues.Count) issues a '$nextMs'"
	}
}

# 3) Cerrar el milestone vía API de GitHub
gh api repos/$owner/$repo/milestones/$($msObj.number) -X PATCH -f state=closed | Out-Null
"Cerrado milestone '$msTitle' (#$($msObj.number))"

# 4) Exportar notas de cierre (issues cerrados del milestone)
$closedIssues = gh issue list --repo "$owner/$repo" --milestone $msTitle --state closed --json number,title | ConvertFrom-Json
$san = ($msTitle -replace '[^A-Za-z0-9_-]','_')
$lines = @("# Notas de cierre - $msTitle", "") + ($closedIssues | ForEach-Object { "- #$($_.number) $($_.title)" })
$path = "./notas-cierre-$san.md"
$lines | Out-File $path -Encoding utf8
"Notas de cierre generadas en $path"
```

> Nota: Necesitas permisos para editar milestones. En repos con flujos de release, considera automatizar la generación de notas con GitHub Releases y cerrar el milestone como parte del checklist de publicación.
