# Probar el cierre automático de issues con `Fixes #<n>`

Verificaremos que al fusionar un PR que contiene `Fixes #<n>` el issue se cierre automáticamente.

## Pasos

1. Abre o identifica un issue abierto (por ejemplo, `#15`).
2. Crea/actualiza un PR y en la descripción incluye `Fixes #15`.
3. Aprueba y fusiona el PR hacia `main`.
4. Verifica que el issue `#15` ahora está **Closed** y referenciado por el PR.

---

> Consejo: También funcionan `Closes #<n>` y `Resolves #<n>`.

## Formato recomendado

- Mensaje en PR/commit: incluye una referencia de cierre por cada issue.
	- Ejemplos: `Fixes #15`, `Closes #20`, `Resolves #33`.
- Asegúrate de que el PR se fusione a la rama por defecto (normalmente `main`).
- Si hay varios issues, separa por espacios: `Fixes #1 Fixes #2`.

## Mejores prácticas

- Prefiere referenciar en la descripción del PR; más visible para los revisores.
- Evita cerrar issues en PRs de experimentación; usa `Refs #n` para referencia sin cierre.
- Si el repo es monorepo o con múltiples proyectos, describe el contexto al referenciar.
- Verifica permisos: solo se cierra automáticamente al merge a la rama por defecto.

## Comandos PowerShell (gh)

Verificación y utilidades con GitHub CLI.

```powershell
$REPO = "owner/repo"   # ej.: andres-olarte396/github-projects-learning

# 1) Crear un issue de prueba y obtener su número
$ISSUE_JSON = gh issue create --repo $REPO --title "Prueba autocierre" --body "Se cerrará al fusionar PR." --json number --jq .
$ISSUE = [int]$ISSUE_JSON
Write-Host "Issue creado: #$ISSUE"

# 2) Crear rama y commit que lo referencia
git checkout -b feat/autocierre-test
"demo" | Out-File -Encoding utf8 .\demo.txt
git add .
git commit -m "feat: demo autocierre (Fixes #$ISSUE)"
git push -u origin HEAD

# 3) Abrir PR que será fusionado a main
gh pr create --repo $REPO --title "Autocierre demo" --body "Fixes #$ISSUE" --base main --head feat/autocierre-test

# 4) Fusionar el PR con squash
gh pr merge --repo $REPO --squash --auto --delete-branch

# 5) Validar que el issue se cerró
Start-Sleep -Seconds 5
gh issue view $ISSUE --repo $REPO --json state,url --jq "{state: .state, url: .url}"
```
