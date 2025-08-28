# Crear un issue: "Implementar interpolador lineal"

En este paso crearás un issue que describe la tarea de implementar un interpolador lineal.

## Pasos

1. Ve a la pestaña **Issues** en tu repositorio de GitHub.
2. Haz clic en **New issue**.
3. Título: `Implementar interpolador lineal`.
4. Descripción sugerida:
   - Objetivo: Implementar una función de interpolación lineal `lerp(a, b, t)`.
   - Criterio de aceptación:
     - `lerp(a, b, 0) = a`
     - `lerp(a, b, 1) = b`
     - `lerp(a, b, 0.5) = (a + b) / 2`
   - Pruebas: incluir ejemplos con números enteros y flotantes.
5. Asigna Labels (por ejemplo, `feature`, `high priority`) y un Milestone si aplica.
6. Haz clic en **Submit new issue**.

---

> Consejo: Añade el texto `Planned in Sprint 1` o similar para el contexto del tablero y milestones.

## Formato recomendado para crear el issue

- Título
  - `[Core] Implementar interpolador lineal (lerp)`
- Descripción
  - Objetivo: Implementar `lerp(a, b, t)` que retorna `a + (b - a) * t`.
  - Criterios de aceptación:
    - `lerp(a, b, 0) = a`
    - `lerp(a, b, 1) = b`
    - `lerp(a, b, 0.5) = (a + b) / 2`
    - Maneja `t < 0` o `t > 1` sin excepciones (comportamiento definido).
  - Pruebas: casos con enteros, flotantes y valores límite.
  - Referencias: enlace a documentación matemática o implementación previa si existe.
- Etiquetas
  - `type: feature`, `priority: medium`, `area: core`
- Milestone
  - `Sprint 1` o la versión objetivo.
- Asignación
  - Asignatario propuesto o dejar en backlog.

## Mejores prácticas

- Usa una plantilla de issue o Issue Forms para capturar criterios y pruebas.
- Mantén los criterios de aceptación verificables y breves.
- Agrega ejemplos numéricos concretos y menciona rangos de entrada esperados.
- Vincula este issue con otros relacionados (por ejemplo, validación o documentación).

## Comandos PowerShell (GitHub CLI `gh`)

```powershell
# Variables
$owner = "<owner>"                   # ejemplo: andres-olarte396
$repo  = "<repo>"                    # ejemplo: github-projects-learning
$ms    = "Sprint 1"

$body = @"
Objetivo: Implementar lerp(a, b, t) que retorna a + (b - a) * t.

Criterios de aceptación:
- lerp(a, b, 0) = a
- lerp(a, b, 1) = b
- lerp(a, b, 0.5) = (a + b) / 2
- Comportamiento definido para t fuera de [0,1]

Pruebas:
- Enteros: a=0, b=10, t=0/0.5/1
- Flotantes: a=1.2, b=3.4, t=0.25/0.75
- Límite: t=-0.1, t=1.1
"@

# Crear issue con labels y milestone
$issue = gh issue create `
  --repo "$owner/$repo" `
  --title "[Core] Implementar interpolador lineal (lerp)" `
  --body  $body `
  --label "type: feature" `
  --label "priority: medium" `
  --label "area: core" `
  --milestone $ms `
  --json number,url | ConvertFrom-Json

"Creado issue #$($issue.number): $($issue.url)"

# (Opcional) Añadir al Project del Sprint
$projOwner = $owner
$projNum   = <numero_del_project>
gh project item-add --owner $projOwner --project-number $projNum --url $issue.url
```

> Nota: Adapta etiquetas y milestone a tu taxonomía real. Si usas Projects v2, configura reglas para mover el item según su estado.
