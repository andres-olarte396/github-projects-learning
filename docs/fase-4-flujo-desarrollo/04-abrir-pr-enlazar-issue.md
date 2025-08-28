# Abrir un Pull Request (PR) y enlazarlo al issue

Crear un PR permite revisar cambios antes de fusionarlos a `main`.

## Pasos

1. En GitHub, ve a la pestaña **Pull requests** y haz clic en **New pull request**.
2. Elige como base `main` y como compare `feature/interpolador-lineal`.
3. Título sugerido: `feat: interpolador lineal (lerp)`.
4. Descripción: resume los cambios y añade el enlace al issue usando cierre automático:
   - Escribe `Fixes #<numero_del_issue>` (ejemplo: `Fixes #12`).
5. Asigna revisores y etiquetas si corresponde.
6. Haz clic en **Create pull request**.

---

> Consejo: Incluye pasos de prueba manual y/o resultados de tests en la descripción del PR.

## Formato recomendado del PR

- Título
   - Convencional: `feat(scope): resumen breve` o `fix(scope): ...`
   - Opcional: referencia al issue en el título: `... (#123)`
- Descripción
   - Contexto y objetivo
   - Cambios principales (bullets)
   - Cómo probar (pasos + resultados esperados)
   - Impacto y compatibilidad (migraciones, breaking changes)
   - Enlace al issue con cierre automático: `Closes #123`
- Metadatos
   - Base: `main` (o `develop`), Head: tu rama de trabajo
   - Etiquetas: `type: ...`, `area: ...`, `status: needs review`
   - Revisores y milestone si aplica

Palabras clave de cierre admitidas: close/closes/closed, fix/fixes/fixed, resolve/resolves/resolved.

## Mejores prácticas

- PRs pequeños y enfocados; evita mezclar refactor masivo con nuevas features.
- Agrega evidencia: screenshots, logs, métricas, enlaces a despliegues.
- Mantén la rama actualizada con `main`; evita conflictos tardíos.
- Usa Draft hasta estar listo; solicita revisión a las personas adecuadas.
- Pasa CI localmente cuando sea posible antes de abrir el PR.

## Comandos PowerShell (GitHub CLI `gh`)

```powershell
# Variables
$owner  = "<owner>"                 # ejemplo: andres-olarte396
$repo   = "<repo>"                  # ejemplo: github-projects-learning
$base   = "main"
$branch = "feature/123-interpolador-lineal"
$issue  = 123

$body = @"
Contexto: Implementa lerp(a,b,t).

Cambios principales:
- Función y casos base
- Pruebas unitarias

Cómo probar:
1. Ejecutar tests
2. Validar resultados para t=0,0.5,1

Closes #$issue
"@

# 1) Crear PR (draft) con enlace al issue (cierre automático)
gh pr create --repo "$owner/$repo" `
   --base $base `
   --head $branch `
   --title "feat(core): interpolador lineal (#$issue)" `
   --body  $body `
   --draft

# 2) Añadir etiquetas, reviewers y milestone
gh pr edit --repo "$owner/$repo" --add-label "type: feature" --add-label "status: needs review"
gh pr edit --repo "$owner/$repo" --add-reviewer "<usuario1>" --add-reviewer "<usuario2>"
gh pr edit --repo "$owner/$repo" --milestone "Sprint 1"

# 3) Ver PR en el navegador
gh pr view --repo "$owner/$repo" --web

# 4) Marcar como listo para revisión cuando corresponda
gh pr ready --repo "$owner/$repo"
```

> Nota: Ajusta el branch base si usas `develop`. Mantén consistencia con tu plantilla de PR y usa palabras clave de cierre para auto-cerrar el issue al fusionar.
