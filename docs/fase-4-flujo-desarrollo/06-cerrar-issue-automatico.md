# Cierre automático del issue al fusionar el PR

GitHub cierra automáticamente un issue cuando el PR que contiene `Fixes #<n>` se fusiona en la rama base.

## Pasos

1. Asegúrate de que el PR incluya `Fixes #<numero_del_issue>` en la descripción.
2. Tras aprobar, haz clic en **Merge pull request** -> **Confirm merge**.
3. Verifica que el issue aparece como **Closed** automáticamente.

## Nota

- También funcionan palabras clave como `Closes #<n>`, `Resolves #<n>`.

## Formato recomendado para el cierre automático

- En la descripción del PR
	- Incluir una línea con palabra clave de cierre y número: `Closes #123`.
	- Si hay varios issues: una línea por cada uno (`Closes #123`, `Fixes #124`).
- Antes de fusionar
	- CI en verde, revisiones aprobadas, cambios alineados al issue.
- Después de fusionar
	- Verificar que el issue aparece como cerrado y que el Project movió la tarjeta a `Done` (si hay reglas).

Notas importantes

- El cierre automático funciona al fusionar hacia la rama por defecto del repositorio (típicamente `main`) o cuando GitHub lo soporta para la rama base configurada.
- En forks o entre repos distintos, el comportamiento puede variar; preferir cerrar manualmente si no aplica.

## Mejores prácticas

- Usa palabras clave en el cuerpo del PR, no solo en commits, para mayor confiabilidad.
- Prefiere `squash` o `merge` estándar según tu política; evita `rebase` si pierdes el mensaje con la palabra clave.
- Añade evidencia de la resolución (tests en verde, screenshot, enlace a despliegue).
- Limpia etiquetas de estado en el issue cerrado (`status: in progress` → quitar).
- Cierra por milestone para mantener orden del Sprint/Release.

## Comandos PowerShell (GitHub CLI `gh`)

```powershell
# Variables
$owner = "<owner>"                 # ejemplo: andres-olarte396
$repo  = "<repo>"                  # ejemplo: github-projects-learning
$pr    = <numero_pr>
$issue = <numero_issue>

# 1) Habilitar auto-merge (opcional) y fusionar el PR
gh pr merge $pr --repo "$owner/$repo" --squash --auto --delete-branch

# 2) Verificar estado del issue (debería cerrarse automáticamente)
gh issue view $issue --repo "$owner/$repo" --json state,closedAt,url

# 3) Limpiar etiquetas de estado obsoletas en el issue cerrado
gh issue edit $issue --repo "$owner/$repo" --remove-label "status: in progress" --remove-label "status: blocked"

# 4) Listar issues cerrados recientemente (últimos 10) para revisión rápida
gh issue list --repo "$owner/$repo" --state closed --limit 10 --json number,title,closedAt
```

> Nota: Para mover automáticamente la tarjeta a `Done` en Projects v2, configura reglas en el Project (por ejemplo, al cerrar el issue o al establecer una etiqueta de estado específica).
