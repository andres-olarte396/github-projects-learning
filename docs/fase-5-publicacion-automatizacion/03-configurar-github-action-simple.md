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
