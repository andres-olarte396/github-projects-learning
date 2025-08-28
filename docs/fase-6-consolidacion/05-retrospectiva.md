# Retrospectiva al final del sprint

Analiza qué salió bien, qué se puede mejorar y acciones para el próximo sprint.

## Pasos

1. Abre una **Discussion** o issue de tipo retrospectiva.
2. Propón una plantilla con secciones: `Start / Stop / Continue`.
3. Recoge feedback del equipo (anónimo si es posible).
4. Prioriza 1-3 acciones concretas de mejora.
5. Cierra la retrospectiva dejando dueños y fechas para las acciones.

---

> Consejo: Mantén la retrospectiva breve, honesta y enfocada en aprendizaje continuo.

## Formato recomendado

Plantilla sugerida (Issue/Discussion):

```markdown
## Qué salió bien

- …

## Qué no salió bien

- …

## Acciones concretas (propietario y fecha)

- …
```

## Mejores prácticas

- Enfoca en procesos, no en personas; evita culpas.
- 1-3 acciones, específicas y medibles; revísalas en el sprint siguiente.
- Usa datos (lead time, PR throughput, defectos) para objetividad.
- Alterna formatos (4Ls, Start/Stop/Continue) para mantener frescura.

## Comandos PowerShell (gh)

```powershell
$REPO = "owner/repo"
$SPRINT = "Sprint N"

# 1) Extraer issues cerrados del sprint para preparar datos
gh issue list --repo $REPO --milestone $SPRINT --state closed --json number,title,closedAt --jq '.[]'

# 2) Crear una Discussion de retrospectiva enlazando el sprint
$TITLE = "Retrospectiva $SPRINT"
$BODY  = "Resumen de resultados y acciones. Milestone: $SPRINT"
gh api repos/$REPO/discussions -X POST -f title=$TITLE -f body=$BODY -f category_id=$(gh api repos/$REPO/discussions/categories --jq '.[] | select(.slug=="general") | .id')

# 3) Abrir tablero del sprint
Start-Process "https://github.com/$REPO/projects"
```
