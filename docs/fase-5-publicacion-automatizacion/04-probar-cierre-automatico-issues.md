# Probar el cierre automático de issues con `Fixes #<n>`

Verificaremos que al fusionar un PR que contiene `Fixes #<n>` el issue se cierre automáticamente.

## Pasos

1. Abre o identifica un issue abierto (por ejemplo, `#15`).
2. Crea/actualiza un PR y en la descripción incluye `Fixes #15`.
3. Aprueba y fusiona el PR hacia `main`.
4. Verifica que el issue `#15` ahora está **Closed** y referenciado por el PR.

---

> Consejo: También funcionan `Closes #<n>` y `Resolves #<n>`.
