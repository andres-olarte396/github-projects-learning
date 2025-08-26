# Cierre automático del issue al fusionar el PR

GitHub cierra automáticamente un issue cuando el PR que contiene `Fixes #<n>` se fusiona en la rama base.

## Pasos

1. Asegúrate de que el PR incluya `Fixes #<numero_del_issue>` en la descripción.
2. Tras aprobar, haz clic en **Merge pull request** -> **Confirm merge**.
3. Verifica que el issue aparece como **Closed** automáticamente.

## Nota

- También funcionan palabras clave como `Closes #<n>`, `Resolves #<n>`.
