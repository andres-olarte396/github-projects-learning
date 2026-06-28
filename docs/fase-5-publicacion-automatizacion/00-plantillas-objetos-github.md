# Plantillas en GitHub: Issues, PRs, Discussions, Releases y Milestones

Centraliza aquí cómo definir e incluir plantillas para los objetos más usados del flujo.

## Issues (Markdown o Issue Forms YAML)

Ubicación: `.github/ISSUE_TEMPLATE/`

- Markdown clásicos: `bug_report.md`, `feature_request.md`.
- Issue Forms (recomendado): `bug.yml`, `feature.yml` con estructura guiada.
- Configuración: `.github/ISSUE_TEMPLATE/config.yml`.

Ejemplo de Issue Form (bug):

```yaml
name: Bug report
description: Reporta un problema
labels: [bug]
body:
  - type: textarea
    id: description
    attributes:
      label: Descripción
      description: ¿Qué pasa?
      placeholder: Describe el bug
    validations:
      required: true
  - type: input
    id: repro
    attributes:
      label: Pasos de reproducción
      placeholder: 1) … 2) … 3) …
  - type: dropdown
    id: severity
    attributes:
      label: Severidad
      options: [low, medium, high]
```

Archivo de configuración (ocultar template libre y ordenar):

```yaml
blank_issues_enabled: false
contact_links:
  - name: Q&A
    url: https://github.com/OWNER/REPO/discussions/categories/q-a
    about: Usa Discussions para preguntas
```

## Pull Requests (PR)

- Plantilla por defecto: `.github/pull_request_template.md`.
- Múltiples plantillas: `.github/PULL_REQUEST_TEMPLATE/feature.md`, `.github/PULL_REQUEST_TEMPLATE/bugfix.md`.
  - En la UI podrás seleccionar, o usar `?template=feature.md` al crear el PR.

Ejemplo de `pull_request_template.md`:

```markdown
## Resumen

- …

## Checklist

- [ ] Pruebas locales OK
- [ ] Linter OK
- [ ] Referencia a issue (Fixes #N)
```

## Discussions

- Plantillas opcionales: `.github/DISCUSSION_TEMPLATE/idea.md`, `.github/DISCUSSION_TEMPLATE/q-a.md`.

Ejemplo `idea.md`:

```markdown
## Contexto

## Objetivo

## Alternativas

## Criterios de aceptación
```

## Releases (notas generadas)

- Archivo para notas auto-generadas: `.github/release.yml`.
- Alternativa manual: mantener `RELEASE_TEMPLATE.md` y usar `gh release create --notes-file`.

Ejemplo `.github/release.yml` (categorías por labels):

```yaml
author: github-actions
changelog:
  exclude:
    labels: [chore, skip-changelog]
  categories:
    - title: 🚀 Features
      labels: [feature, feat]
    - title: 🐛 Fixes
      labels: [bug, fix]
    - title: 🧰 Maintenance
      labels: [chore, refactor, docs]
```

## Milestones (no hay plantillas nativas)

- Define convención de nombre, descripción base y criterios de cierre.
- Automatiza la creación con un script que inyecta una descripción estándar.

Ejemplo PowerShell (gh api):

```powershell
$REPO = "owner/repo"
$TITLE = "Sprint N"
$DESC  = @"
Objetivo: …
Criterios de Done: …
Alcance: …
"@

# Crear milestone con descripción
$payload = @{ title = $TITLE; description = $DESC; due_on = (Get-Date).AddDays(14).ToString('o') } | ConvertTo-Json
gh api repos/$REPO/milestones -X POST -H "Content-Type: application/json" -f body="$payload"
```

## Recomendaciones

- Versiona estos archivos bajo `.github/` y revísalos en PRs.
- Mantén consistencia entre templates y guías del proyecto (este repo de docs).
- Itera los templates tras cada sprint/retrospectiva.
