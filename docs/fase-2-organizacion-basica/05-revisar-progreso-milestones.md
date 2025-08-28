# Revisar el progreso de milestones

GitHub permite visualizar el avance de cada milestone, mostrando cuántos issues han sido completados y cuántos están pendientes.

## Pasos para revisar el progreso

1. Ve a la pestaña **Issues** y haz clic en **Milestones**.
2. Selecciona el milestone que deseas revisar.
3. Observa la barra de progreso y la lista de issues asociados.
4. Puedes ver cuántos issues están abiertos y cuántos cerrados.

### Ejemplo visual

![Progreso de un milestone](../../assets/milestone/milestone-progress-bar.png)

---

> **Consejo:** Usa los milestones para hacer seguimiento a entregas parciales y motivar al equipo mostrando el avance.

## Formato recomendado para la revisión

- Antes de la revisión:
	- Verifica el alcance del milestone y su fecha límite.
	- Asegura que issues y PRs estén correctamente vinculados y etiquetados.
- Durante la revisión:
	- Revisa barra de avance: abiertos vs. cerrados.
	- Identifica bloqueadores y dependencias.
	- Decide si se replanifica o se extiende, si aplica.
- Al finalizar:
	- Documenta conclusiones y acciones.
	- Ajusta el siguiente milestone o backlog.

## Mejores prácticas

- Mantén los milestones pequeños y con objetivos claros.
- No cierres un milestone con issues abiertos sin plan de migración.
- Usa labels de tipo `status:` para resaltar bloqueos.
- Vincula el milestone a un release cuando aplique.

## Comandos PowerShell (gh)

```powershell
$REPO = "owner/repo"   # ej.: andres-olarte396/github-projects-learning
$MILESTONE = "Sprint N"

# 1) Ver progreso (abiertos vs. cerrados)
gh api repos/$REPO/milestones --jq '.[] | select(.title=="'$MILESTONE'") | {title, open_issues, closed_issues, due_on}'

# 2) Listar issues abiertos del milestone
gh issue list --repo $REPO --milestone $MILESTONE --state open --json number,title,assignees --jq '.[]'

# 3) Abrir la vista del milestone en el navegador
$MS = gh api repos/$REPO/milestones --jq '.[] | select(.title=="'$MILESTONE'") | .number'
Start-Process "https://github.com/$REPO/milestone/$MS"

# 4) Mover rápidamente issues bloqueados al siguiente milestone
$NEXT = "Sprint N+1"
gh api repos/$REPO/milestones -X POST -f title=$NEXT 2>$null | Out-Null
gh issue list --repo $REPO --milestone $MILESTONE --label status:blocked --state open --json number --jq '.[].number' |
	ForEach-Object { gh issue edit $_ --repo $REPO --milestone $NEXT }
```
