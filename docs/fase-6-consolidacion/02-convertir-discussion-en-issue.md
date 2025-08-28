# Convertir una Discussion en un issue

Cuando haya consenso, convierte la discusión en un issue accionable.

## Pasos

1. Abre la Discussion acordada.
2. Haz clic en **Convert to issue** (en la barra lateral o menú de la discusión).
3. Selecciona el repositorio/plantilla de issue si aplica.
4. Ajusta título y descripción para que sean accionables.
5. Añade Labels y Milestone.
6. Crea el issue.

---

> Consejo: Enlaza la discusión original en el issue para conservar el contexto.

## Formato recomendado

- Al convertir a issue, usa una plantilla de issue (bug/feature) con:
	- Contexto y objetivo resumido desde la Discussion.
	- Criterios de aceptación claros.
	- Definición de Done (DoD) y riesgos conocidos.
	- Labels y Milestone del sprint en curso.

## Mejores prácticas

- No borres el enlace de referencia a la Discussion; ayuda a futuros lectores.
- Si la Discussion contiene decisiones, copia el resumen como "Decisión tomada" en el issue.
- Asigna responsable y tamaño (story points) si tu flujo lo usa.
- Si hay sub-tareas, desglósalas en checklist o issues vinculados.

## Comandos PowerShell (gh)

La conversión directa se hace mejor en la UI. Con `gh api` puedes crear el issue y enlazar referencias.

```powershell
$REPO = "owner/repo"
$DISCUSSION_NUMBER = 1  # ajusta

# 1) Recuperar el título y parte del body de la Discussion
$DISC = gh api repos/$REPO/discussions/$DISCUSSION_NUMBER --jq '{title: .title, body: .body}' | ConvertFrom-Json

# 2) Crear issue referenciando la Discussion
$TITLE = "[Feature] $($DISC.title)"
$BODY  = "Contexto (de la discussion #$DISCUSSION_NUMBER):`n`n$($DISC.body.Substring(0,[Math]::Min(1000,$DISC.body.Length)))`n`nCriterios de aceptación:`n- …"

gh issue create --repo $REPO --title $TITLE --body $BODY --label feature --milestone "Sprint N"

# 3) Abrir el issue creado
gh issue list --repo $REPO --state open --search $TITLE --limit 1 --json number,url --jq '.[0]'
```
