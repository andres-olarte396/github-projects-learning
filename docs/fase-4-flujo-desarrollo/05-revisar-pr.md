# Revisar el Pull Request antes de aprobar

La revisión asegura calidad y mantiene estándares del proyecto.

## Checklist de revisión

- Verificar que el PR compila/pasa tests.
- Confirmar que el alcance corresponde al issue.
- Revisar nombres de funciones, claridad y comentarios.
- Chequear efectos colaterales y cambios de API.
- Confirmar que el PR enlaza al issue con `Fixes #<n>`.

## Pasos

1. Abre el PR y revisa los archivos cambiados (tab **Files changed**).
2. Comenta líneas específicas si es necesario.
3. Si está todo correcto, haz clic en **Approve**.
4. Si falta algo, solicita cambios (**Request changes**).

## Formato recomendado para la revisión

- Alcance y trazabilidad
	- El PR resuelve exactamente lo descrito en el issue y lo referencia (`Closes #N`).
- Diseño y legibilidad
	- Nombres claros, funciones pequeñas, documentación mínima necesaria.
- Pruebas y verificación
	- Tests agregados/actualizados y CI en verde.
- Seguridad y rendimiento
	- Sin filtración de secretos; inputs validados; cambios de rendimiento entendidos.
- Compatibilidad
	- Sin breaking changes no declarados; migraciones/notes si aplica.

## Mejores prácticas

- Comenta con empatía y especificidad; sugiere acciones concretas.
- Prefiere sugerencias con diff inline para cambios menores.
- Pide pruebas cuando el comportamiento cambia; valida casos borde.
- Mantén ciclos de revisión cortos; evita bloqueos innecesarios.
- Usa “Approve” solo cuando esté listo para merge.

## Comandos PowerShell (GitHub CLI `gh`)

```powershell
# Variables
$owner = "<owner>"                 # ejemplo: andres-olarte396
$repo  = "<repo>"                  # ejemplo: github-projects-learning
$pr    = <numero_pr>

# 1) Ver archivos cambiados del PR en terminal
gh pr diff $pr --repo "$owner/$repo"

# 2) Comentar en el PR (comentario general)
gh pr comment $pr --repo "$owner/$repo" --body "Buen trabajo. Verifica casos borde para t fuera de [0,1]."

# 3) Aprobar o solicitar cambios
gh pr review $pr --repo "$owner/$repo" --approve --body "Listo para merge."
# gh pr review $pr --repo "$owner/$repo" --request-changes --body "Faltan tests para t=0.5."

# 4) Añadir etiquetas de estado del PR
gh pr edit $pr --repo "$owner/$repo" --add-label "status: needs changes"

# 5) Abrir el PR en el navegador
gh pr view $pr --repo "$owner/$repo" --web
```

> Nota: Si tu proceso requiere checklist de seguridad/privacidad, añade una sección específica en la plantilla del PR y verifica cumplimiento durante la revisión.
