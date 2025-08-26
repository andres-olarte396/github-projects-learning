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
