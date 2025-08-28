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

## Formato recomendado de nombres de ramas

- Prefijos
	- `feature/` nuevas funcionalidades
	- `fix/` correcciones de bugs
	- `chore/` tareas de mantenimiento
	- `docs/` documentación
- Estructura
	- `<prefijo>/<id-o-issue>-<slug-descriptivo>`
	- Ejemplos: `feature/123-interpolador-lineal`, `fix/456-null-pointer`

## Mejores prácticas

- Crea la rama desde `main` (o `develop`) actualizado para minimizar conflictos.
- Mantén el nombre corto, descriptivo y en minúsculas con guiones.
- Trabaja con commits pequeños y mensajes claros; referencia el issue (`#123`).
- Publica la rama al remoto y abre el PR temprano como draft para feedback.
- Sincroniza frecuentemente con `main` (rebase o merge) para evitar drift.

## Comandos PowerShell (git y GitHub CLI `gh`)

```powershell
# Variables
$owner = "<owner>"                  # ejemplo: andres-olarte396
$repo  = "<repo>"                   # ejemplo: github-projects-learning
$issue = 123                         # número de issue (si aplica)
$branch = "feature/$issue-interpolador-lineal"

# 1) Actualizar main y crear la rama
git checkout main
git pull origin main
git checkout -b $branch

# 2) Asociar la rama con el issue en GitHub (comentario de contexto)
if ($issue) {
	gh issue comment $issue --repo "$owner/$repo" --body "Trabajando en rama `$branch`"
}

# 3) Publicar la rama al remoto
git push -u origin $branch

# 4) (Opcional) Crear PR en draft referenciando el issue
if ($issue) {
	gh pr create --repo "$owner/$repo" --base main --head $branch `
		--title "feat: interpolador lineal (#$issue)" `
		--body "Implementa lerp(a,b,t). Closes #$issue" `
		--draft
} else {
	gh pr create --repo "$owner/$repo" --base main --head $branch `
		--title "feat: interpolador lineal" `
		--body "Implementa lerp(a,b,t)."
}
```

> Nota: Ajusta el branch de base si usas `develop`. Mantén consistencia con tu convención de mensajes de commit (Convencional Commits, por ejemplo).
