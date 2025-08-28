# Abrir una Discussion para una nueva funcionalidad

Las Discussions sirven para idear, debatir y validar antes de crear issues.

## Pasos

1. Ve a **Discussions** en tu repositorio (actívalas en Settings si no aparecen).
2. Haz clic en **New discussion**.
3. Selecciona categoría (por ejemplo, `Ideas`).
4. Título: describe brevemente la funcionalidad.
5. Contenido: contexto, motivación, posibles soluciones.
6. Publica la discusión.

---

> Consejo: Usa etiquetas y enlaces a documentación o prototipos para enriquecer la discusión.

## Formato recomendado

- Plantilla sugerida de Discussion (categoría Ideas):

```markdown
## Contexto

Breve descripción del problema u oportunidad.

## Objetivo

Qué buscamos lograr y por qué ahora.

## Alternativas consideradas

- Opción A
- Opción B

## Criterios de aceptación (si procede)

- …

## Riesgos / Suposiciones

- …
```

## Mejores prácticas

- Selecciona la categoría adecuada (Ideas, Q&A, Announcements) para facilitar el filtrado.
- Mantén el foco y una pregunta clara para promover respuestas accionables.
- Usa etiquetas (labels) y enlaza documentación, maquetas o PoCs.
- Resume la conclusión y cierra la Discussion si ya no se necesita.

## Comandos PowerShell (gh)

Actualmente la CLI no cubre todas las operaciones de Discussions; puedes usar la API vía `gh api`.

```powershell
$REPO = "owner/repo"   # ej.: andres-olarte396/github-projects-learning

# 1) Listar categorías de Discussions
gh api repos/$REPO/discussions/categories --jq '.[] | {id,name,slug}'

# 2) Obtener el id de la categoría 'Ideas' (ajusta si tu slug es distinto)
$CAT_ID = gh api repos/$REPO/discussions/categories --jq '.[] | select(.slug=="ideas") | .id'

# 3) Crear una Discussion
$TITLE = "[Idea] Nueva funcionalidad"
$BODY  = @"
Contexto: …
Objetivo: …
Alternativas: …
"@

gh api repos/$REPO/discussions -X POST -f title=$TITLE -f body=$BODY -f category_id=$CAT_ID

# 4) Abrir la lista de Discussions en el navegador
Start-Process "https://github.com/$REPO/discussions"
```
