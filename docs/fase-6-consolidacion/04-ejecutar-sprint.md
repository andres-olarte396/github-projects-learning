# Ejecutar el sprint con issues, PRs y milestones

Durante el sprint, actualiza estados, crea PRs y da seguimiento al milestone.

## Pasos

1. Toma un issue de `To Do` y muévelo a `In Progress`.
2. Crea una rama de trabajo, realiza commits y abre PRs vinculados al issue.
3. Revisa y fusiona PRs; cierra issues con `Fixes #<n>`.
4. Monitorea el avance del milestone y el tablero.
5. Realiza dailies breves y ajusta prioridades si es necesario.

---

> Consejo: Usa filtros por `assignee`, `label` y `milestone` para mantener foco y visibilidad.

## Formato recomendado

- Daily breve: ayer/hoy/bloqueos.
- Actualizaciones en tablero: mover tarjetas y actualizar estado/labels.
- PRs vinculados a issues con mensajes claros.
- Revisión de avance del milestone en mid-sprint.

## Mejores prácticas

- Enfócate en terminar antes de empezar nuevas tareas.
- Limita WIP y pide ayuda para desbloquear cuellos de botella.
- Escribe PRs pequeños y revisables; preferir squash merge.
- Documenta decisiones clave y enlaza al issue.

## Comandos PowerShell (gh)

```powershell
$REPO = "owner/repo"
$SPRINT = "Sprint N"

# 1) Ver issues del sprint por responsable
gh issue list --repo $REPO --milestone $SPRINT --assignee @me --json number,title,state --jq '.[]'

# 2) Crear PR rápido desde rama actual referenciando issue #X
$ISSUE = 1
gh pr create --repo $REPO --title "feat: avance #$ISSUE" --body "Refs #$ISSUE" --base main

# 3) Listar PRs listos para merge
gh pr list --repo $REPO --search "label:ready-to-merge state:open" --json number,title,headRefName --jq '.[]'

# 4) Ver avance del milestone
gh api repos/$REPO/milestones --jq '.[] | select(.title=="'$SPRINT'") | {title, open_issues, closed_issues}'
```
