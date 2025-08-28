# Crear un Release (v0.1-schema)

Los Releases agrupan binarios/notas para una versión del proyecto.

## Pasos

1. Ve a la pestaña **Releases** > **Draft a new release**.
2. Tag: `v0.1-schema` (o crea el tag en el draft).
3. Target: selecciona la rama o commit (normalmente `main`).
4. Título: `v0.1-schema`.
5. Notas: resume cambios y lista issues/PRs relevantes.
6. Marca **Set as the latest release** (opcional).
7. Publica el release con **Publish release**.

---

> Consejo: Puedes adjuntar artefactos (zip, binarios) si tu proyecto los genera.

## Formato recomendado

- Versionado de tags: `vMAJOR.MINOR.PATCH` (ej.: `v0.1.0`) o pre-release `-rc.1`, `-beta.1`.
- Título: igual al tag (ej.: `v0.1.0`).
- Cuerpo (release notes):
	- Highlights.
	- Cambios destacados (por área o tipo).
	- Breaking changes (si aplica) y pasos de migración.
	- Issues cerrados y PRs incluidos (auto-generados o listados manualmente).
	- Artefactos y checks (builds, linters, pruebas).

Consulta también: [Plantillas en GitHub: Issues, PRs, Discussions, Releases y Milestones](./00-plantillas-objetos-github.md) para estandarizar notas y plantillas.

Sugerencia de plantilla de notas:

```markdown
## Highlights

- …

## Cambios

- …

## Breaking changes

- …

## Issues y PRs

- Cerrados: #12, #18
- PRs: #21, #22
```

## Mejores prácticas

- Alinea el release con un milestone cerrado (mismo alcance y fecha): facilita trazabilidad.
- Usa `--generate-notes` o herramientas como Release Drafter para consistencia.
- Firma y protege tags (Git: annotated tags) si el proyecto lo requiere.
- Mantén un CHANGELOG.md y referencia al release.
- Adjunta artefactos reproducibles (checksums, SBOM si procede).
- Automatiza la creación de releases desde CI cuando sea estable.

## Comandos PowerShell (gh)

Ejemplos usando GitHub CLI desde PowerShell. Ajusta `$REPO`, `$TAG` y rama objetivo.

```powershell
# Variables básicas
$REPO = "owner/repo"   # ej.: andres-olarte396/github-projects-learning
$TAG  = "v0.1.0"

# 1) Crear un tag anotado y empujarlo
git tag -a $TAG -m "Release $TAG"
git push origin $TAG

# 2) Crear un release con notas generadas automáticamente
gh release create $TAG --repo $REPO --generate-notes --latest --title $TAG

# 3) Subir artefactos (si tienes archivos de build)
# gh release upload $TAG "path/to/artifact.zip" --repo $REPO

# 4) Ver detalles del release
gh release view $TAG --repo $REPO --web

# 5) Listar releases y tags
gh release list --repo $REPO
git tag --list | sort

# 6) Editar título o marcar como latest (si cambió)
gh release edit $TAG --repo $REPO --title $TAG --latest

# 7) Crear un draft primero y publicarlo luego
gh release create $TAG --repo $REPO --draft --title $TAG
# ...edita el draft en la web y luego publica:
gh release edit $TAG --repo $REPO --draft=false

# 8) Generar notas entre el tag anterior y HEAD para revisarlas localmente
$prev = git describe --tags --abbrev=0 ($TAG + "^") 2>$null
git log $prev..$TAG --pretty=format:"* %s (%h)" | Out-File -Encoding utf8 .\RELEASE_NOTES_$TAG.md
```
