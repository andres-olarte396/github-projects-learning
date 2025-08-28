# Configurar una GitHub Action simple

Crearemos un workflow que verifique el formato Markdown (ejemplo con `markdownlint-cli2`) en cada push y PR.

## Pasos

1. Crea la carpeta `.github/workflows/` si no existe.
2. Crea un archivo `markdown-lint.yml` con el siguiente contenido:

```yaml
name: Markdown Lint

on:
  push:
    branches: [ main ]
  pull_request:

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'

      - name: Install markdownlint-cli2
        run: npm install -g markdownlint-cli2

      - name: Run markdownlint
        run: markdownlint-cli2 "**/*.md"
```

1. Commit y push del workflow.

---

> Consejo: Ajusta reglas con un archivo `.markdownlint.jsonc` si necesitas excepciones.

## Formato recomendado

- Nombre del workflow: claro y accionable (ej.: "CI - Lint & Test").
- Disparadores:
  - `push` a ramas protegidas.
  - `pull_request` para validar contribuciones.
  - Opcional: `workflow_dispatch` para ejecuciones manuales.
- Jobs pequeños y composables: lint, build, test, release.
- Caching de dependencias para acelerar.

## Mejores prácticas

- Usa versiones fijas o ranges controlados en `uses:` (ej.: `@v4`).
- Mantén los secretos en GitHub Secrets y nunca los escribas en logs.
- Evita matrices gigantes sin necesidad; divide por responsabilidad.
- Falla rápido: linters y formatters primero.
- Usa artifacts para conservar reportes y resultados.
- Evita hacer release en PR; solo en `main` con tags.

## Comandos PowerShell (gh)

Acciones útiles desde PowerShell con `gh`.

```powershell
# Variables
$REPO = "owner/repo"   # ej.: andres-olarte396/github-projects-learning

# 1) Listar workflows y sus estados
gh workflow list --repo $REPO

# 2) Ver los runs recientes
gh run list --repo $REPO --limit 10

# 3) Abrir el último run en el navegador
gh run view --repo $REPO --web

# 4) Disparar manualmente un workflow (si define workflow_dispatch)
# Reemplaza NAME por el nombre exacto del workflow
gh workflow run "Markdown Lint" --repo $REPO

# 5) Ver logs de un run en consola
# Obtén primero el ID con 'gh run list'
$RUN_ID = (gh run list --repo $REPO --limit 1 --json databaseId | ConvertFrom-Json)[0].databaseId
gh run view $RUN_ID --repo $REPO --log
```
