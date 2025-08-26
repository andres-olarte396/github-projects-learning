# Crear un branch `feature/interpolador-lineal`

Trabajar en una rama (branch) separada permite desarrollar sin afectar la rama principal.

## Pasos (línea de comandos)

1. Asegúrate de estar en `main` actualizado.
2. Crea y cambia a la rama:

```powershell
# PowerShell
git checkout main
git pull origin main
git checkout -b feature/interpolador-lineal
```

1. Verifica la rama actual:

```powershell
git branch --show-current
```

---

> Consejo: Usa un prefijo `feature/` para ramas de nuevas funcionalidades.
