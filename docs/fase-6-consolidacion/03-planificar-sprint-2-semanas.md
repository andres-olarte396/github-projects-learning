# Planificar un sprint de 2 semanas con milestones + Project

Planificaremos un sprint corto integrando milestones e issues dentro de un Project (Kanban).

## Pasos

1. Crea un milestone `Sprint N` con fecha fin en 2 semanas.
2. Revisa el backlog y selecciona issues realistas para el sprint.
3. Asigna esos issues al milestone `Sprint N`.
4. Abre/actualiza un Project (Kanban) del sprint.
5. Añade las tarjetas (issues) al tablero y ordénalas por prioridad.
6. Define la meta del sprint y criterios de éxito.

---

> Consejo: Limita el WIP (trabajo en progreso) por columna para evitar cuellos de botella.

## Formato recomendado

- Milestone: `Sprint N` con fecha fin (2 semanas desde inicio).
- Definición de Meta del Sprint: 1-2 frases.
- Criterios de éxito medibles.
- Lista de issues priorizados con tamaño estimado.

## Mejores prácticas

- Selecciona menos y termina más: respeta capacidad y vacaciones.
- Incluye buffer para imprevistos (10-20%).
- Define límites WIP explícitos en el tablero.
- Revisa dependencias y bloqueadores antes de iniciar.

## Comandos PowerShell (gh)

```powershell
$REPO = "owner/repo"
$SPRINT = "Sprint N"

# 1) Crear milestone del sprint
gh api repos/$REPO/milestones -X POST -f title=$SPRINT -f due_on=$(Get-Date).AddDays(14).ToString('o')

# 2) Listar issues candidatos (por label/área)
gh issue list --repo $REPO --label feature --state open --json number,title,labels --jq '.[] | {number,title,labels: [.labels[].name]}'

# 3) Asignar issues seleccionados al milestone
$ISSUES = @(1,2,3) # números de ejemplo
foreach ($i in $ISSUES) { gh issue edit $i --repo $REPO --milestone $SPRINT }

# 4) Agregar issues al Project del sprint (si usas Projects v2)
$P_NUM = 1 # número del project
foreach ($i in $ISSUES) { gh project item-add --owner @me --project $P_NUM --url "https://github.com/$REPO/issues/$i" }
```
