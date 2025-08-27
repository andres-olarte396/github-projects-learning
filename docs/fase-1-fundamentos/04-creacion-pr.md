# Cómo crear un Pull Request (PR) en GitHub

Crear un Pull Request (PR) en GitHub es un paso importante para contribuir a un proyecto. A continuación, se describen los pasos necesarios para crear un PR correctamente.

## Pasos para crear un PR

1. **Realiza cambios en tu rama**: Asegúrate de que has realizado los cambios necesarios en tu rama local. 

2. **Sube tus cambios a GitHub**: Utiliza el comando `git push origin <nombre-de-tu-rama>` para subir tus cambios a tu repositorio en GitHub.

3. **Navega a tu repositorio en GitHub**: Abre tu navegador y dirígete a la página de tu repositorio en GitHub.

4. **Selecciona la rama**: En la parte superior de la página, verás un botón que muestra la rama actual. Haz clic en él y selecciona la rama que contiene tus cambios.

5. **Inicia el Pull Request**: Una vez que estés en la rama correcta, verás un botón que dice "Compare & pull request". Haz clic en este botón.

6. **Agrega una descripción**: En la página del Pull Request, agrega un título y una descripción que explique los cambios que has realizado. Esto ayudará a los revisores a entender tu contribución.

7. **Vincula el PR a un issue (opcional)**: Si tu PR soluciona un issue, puedes vincularlo utilizando `Fixes #<número-del-issue>` en la descripción. Esto cerrará automáticamente el issue cuando se acepte el PR.

8. **Crea el Pull Request**: Haz clic en el botón "Create pull request" para enviar tu PR.

9. **Espera la revisión**: Una vez creado el PR, otros colaboradores del proyecto podrán revisarlo y dejar comentarios. 

10. **Realiza cambios si es necesario**: Si se solicitan cambios, realiza las modificaciones en tu rama y vuelve a subir los cambios. El PR se actualizará automáticamente.

Siguiendo estos pasos, podrás crear un Pull Request en GitHub de manera efectiva.

## Formato recomendado para Pull Requests

Usa esta estructura para que tus PRs sean claros, revisables y fáciles de aprobar.

1. Título
	- Usa estilo Conventional Commits: `feat:`, `fix:`, `docs:`, `refactor:`, `test:`, `chore:`, `build:`, `ci:`.
	- Sé breve y específico. Ej.: `feat: interpolador lineal (lerp)`.

2. Descripción (Resumen y contexto)
	- ¿Qué cambia y por qué? ¿Cuál es el objetivo?
	- Enlaces relevantes (issues, discusiones, docs).

3. Relación con issues
	- Cierre automático: `Fixes #<n>` / `Closes #<n>` / `Resolves #<n>`.
	- Relacionados: `Refs #<n>` o `Related to #<n>`.

4. Cambios incluidos
	- Lista breve de cambios clave (archivos/funciones afectadas).

5. Cómo probar (pasos de verificación)
	- Pasos numerados para reproducir y validar.

6. Evidencia
	- Capturas de pantalla, logs o resultados de tests (antes/después si aplica).

7. Checklist
	- [ ] CI verde (lint/test/build)
	- [ ] Sin cambios colaterales no relacionados
	- [ ] Docs/README/Changelog actualizados (si aplica)
	- [ ] Tests incluidos/actualizados (si aplica)
	- [ ] Sin secretos ni datos sensibles

8. Riesgos y mitigación
	- Riesgos conocidos, feature flags, plan de rollback.

9. Tipo de cambio
	- `bugfix` | `feature` | `docs` | `refactor` | `perf` | `test` | `build/ci` | `chore`.

### Plantilla sugerida (`.github/PULL_REQUEST_TEMPLATE.md`)

```markdown
## Descripción
Resumen del cambio y motivación.

## Relación con issues
Fixes #<n> | Closes #<n> | Resolves #<n>

## Cambios incluidos
- …
- …

## Cómo probar
1. …
2. …
3. …

## Evidencia
- Capturas / logs / resultados de tests.

## Checklist
- [ ] CI (lint/test/build) pasa
- [ ] Docs actualizadas (si aplica)
- [ ] Tests añadidos/actualizados (si aplica)
- [ ] Sin secretos/credenciales

## Riesgos y mitigación
- Riesgos: …
- Mitigación: …

## Tipo de cambio
feature | bugfix | docs | refactor | perf | test | build/ci | chore
```

## Mejores prácticas para PRs

- Un PR debe enfocarse en un único objetivo; divide en varios PRs si es grande.
- Mantén los PRs pequeños para revisiones rápidas; evita reformatos masivos no relacionados.
- Sube como Draft PR si aún trabajas, y márcalo Ready for review al finalizar.
- Asegura CI verde antes de pedir revisión; describe pasos de prueba manual.
- Usa `Fixes #<n>` para cerrar el issue automáticamente al fusionar.
- Pide revisión a las personas adecuadas y responde feedback puntualmente.
- Documenta breaking changes y actualiza ejemplos/README cuando aplique.

## Comandos PowerShell (GitHub CLI `gh`)

Crea y gestiona PRs desde la terminal de PowerShell.

```powershell
# Variables de ejemplo
$base = "main"
$branch = "feature/interpolador-lineal"
$title = "feat: interpolador lineal (lerp)"
$body = @"
## Descripción
Implementa la función lerp(a, b, t) con casos base y pruebas.

## Relación con issues
Fixes #123

## Cómo probar
1. Ejecutar tests de utilidades
2. Validar casos t=0, t=1, t=0.5
"@

# Crear PR (en repo actual)
gh pr create --base $base --head $branch --title $title --body $body

# Crear PR como borrador
gh pr create --base $base --head $branch --title $title --body $body --draft

# Añadir reviewers y labels
gh pr edit --add-reviewer usuario1 --add-reviewer usuario2
gh pr edit --add-label feature --add-label "high priority"

# Ver estado y abrir en el navegador
gh pr status
gh pr view --web

# Marcar PR listo para revisión (quitar draft)
gh pr ready

# Fusionar con squash y borrar rama
gh pr merge --squash --delete-branch
```
