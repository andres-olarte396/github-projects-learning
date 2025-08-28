# Mover el issue en el tablero `In Progress` → `Done`

Al cerrar el PR y el issue, refleja el estado final en el tablero Kanban.

## Pasos

1. Abre el Project (Kanban) correspondiente.
2. Localiza la tarjeta del issue en `In Progress`.
3. Arrastra la tarjeta a la columna `Done`.
4. Confirma que el issue está cerrado y el PR fusionado.

> Consejo: Si usas Projects (Beta), puedes automatizar este movimiento con reglas basadas en el estado del pull request o issue.

## Formato recomendado para reflejar `Done`

- Condiciones previas
	- PR fusionado, CI en verde, issue cerrado (o por cerrar con auto-cierre).
	- Etiquetas de estado actualizadas (evitar `status: in progress` en issues cerrados).
- Movimiento en Project
	- Campo `Status` en `Done` o regla que mueva la tarjeta al cerrar el issue.
	- Archivar tarjetas antiguas para mantener el tablero ligero.

## Mejores prácticas

- Revisa diariamente la columna `In Progress` y mueve a `Done` tras el merge.
- Usa filtros por milestone para confirmar el avance del Sprint.
- Registra notas de cierre si el cambio requiere seguimiento posterior.
- Evita “work in progress” perpetuo; define criterios objetivos de Done.

## Comandos PowerShell (GitHub CLI `gh`)

```powershell
# Variables
$owner = "<owner>"
$repo  = "<repo>"
$ms    = "Sprint 1"

# 1) Listar issues cerrados del milestone (candidatos a Done)
gh issue list --repo "$owner/$repo" --state closed --milestone $ms --json number,title,closedAt

# 2) Quitar etiquetas de estado obsoletas
$closed = gh issue list --repo "$owner/$repo" --state closed --label "status: in progress" --json number | ConvertFrom-Json
foreach ($i in $closed) { gh issue edit $($i.number) --repo "$owner/$repo" --remove-label "status: in progress" }

# 3) (Opcional) Añadir una etiqueta de confirmación de Done
# gh issue edit <n> --repo "$owner/$repo" --add-label "status: done"
```

> Nota: El cambio del campo `Status` en Projects v2 puede automatizarse mediante reglas; si no existen, realiza el movimiento desde la UI del tablero.
