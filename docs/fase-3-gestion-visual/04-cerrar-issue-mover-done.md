# Cerrar un issue y moverlo a `Done`

Cuando una tarea está completada, debes cerrar el issue y moverlo a la columna `Done`.

## Pasos para cerrar y mover un issue

1. Abre el issue y haz clic en **Close issue** para marcarlo como resuelto.
2. Vuelve al Project (Kanban) y localiza el issue cerrado.
3. Arrastra el issue a la columna `Done`.
4. El tablero reflejará que la tarea está finalizada.

### Ejemplo visual

![Cerrar y mover issue a Done](https://docs.github.com/assets/images/help/projects/close-issue-move-done.png)

---

> **Consejo:** Solo mueve a `Done` los issues que realmente estén resueltos y cerrados.

## Formato recomendado para cerrar y mover a Done

Checklist de cierre (DoD)

- Criterios de aceptación cumplidos y revisados.
- PR relacionado fusionado a la rama objetivo (main/dev) y CI en verde.
- Documentación/CHANGELOG actualizados si aplica.
- Sin TODOs pendientes o issues dependientes sin resolver.
- Labels coherentes; evita dejar `status: in progress` en issues cerrados.

Movimiento en Project

- Usa el campo `Status` del Project en `Done` o una regla que mueva a `Done` cuando el issue esté cerrado.
- Evita columnas “cementerio”; archiva tarjetas antiguas si el tablero crece demasiado.

## Mejores prácticas

- Prefiere auto-cierre desde Pull Requests usando palabras clave: "Closes #123" en la descripción.
- Comenta el cierre con evidencia (screenshots, enlaces a despliegue, pruebas).
- Si el PR no se fusiona (revert/cancel), explica y referencia el issue sucesor.
- Cierra por milestone para mantener higiene del Sprint/Release.
- Revisa que no queden etiquetas de estado desalineadas al cerrar.

## Comandos PowerShell (GitHub CLI `gh`)

```powershell
# Variables
$owner = "<owner>"                 # ejemplo: andres-olarte396
$repo  = "<repo>"                  # ejemplo: github-projects-learning
$num   = <numero_del_issue>         # ejemplo: 123

# 1) Comentar y cerrar un issue
gh issue comment $num --repo "$owner/$repo" --body "Completado según criterios de aceptación. Cerrando."
gh issue close   $num --repo "$owner/$repo"

# 2) Quitar etiquetas de estado obsoletas (si las usas)
gh issue edit $num --repo "$owner/$repo" --remove-label "status: in progress" --remove-label "status: blocked"

# 3) Auto-cierre por Pull Request (al fusionar)
# Incluye en el PR: "Closes #$num" y al hacer merge se cerrará automáticamente.
# Ejemplo de merge (ajusta flags a tu flujo):
# gh pr merge <numero_pr> --merge --delete-branch --repo "$owner/$repo"

# 4) Listar issues abiertos por milestone para evaluar cierre
$ms = "Sprint 1"
gh issue list --repo "$owner/$repo" --state open --milestone $ms --json number,title,labels
```

> Nota: El movimiento de la tarjeta a `Done` en Projects v2 puede automatizarse con reglas del Project (por ejemplo, al cerrar el issue o al cambiar el campo `Status`). Si no hay regla, realiza el movimiento desde la UI del tablero.
