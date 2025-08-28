# Crear un repositorio de prueba en GitHub

## Introducción

Este manual te guiará a través del proceso de creación de un repositorio de prueba en GitHub. 

## Pasos para crear un repositorio

1. **Iniciar sesión en GitHub**
   - Ve a [github.com](https://github.com) e inicia sesión con tu cuenta.

2. **Crear un nuevo repositorio**
   - Haz clic en el botón "New" o "Nuevo" en la esquina superior derecha de la página de inicio de tu perfil.

3. **Configurar el repositorio**
   - **Nombre del repositorio**: Escribe un nombre para tu repositorio (por ejemplo, `repositorio-prueba`).
   - **Descripción**: Opcionalmente, agrega una descripción para tu repositorio.
   - **Visibilidad**: Selecciona si deseas que tu repositorio sea público o privado.
   - **Inicializar este repositorio con**: Puedes seleccionar la opción de agregar un archivo README si lo deseas.

4. **Crear el repositorio**
   - Haz clic en el botón "Create repository" o "Crear repositorio".

5. **Captura de pantalla**
   - (Aquí puedes incluir una captura de pantalla del formulario de creación del repositorio).

## Formato recomendado para nuevos repositorios

Usa este formato como plantilla mínima al crear un nuevo repositorio. Te ayudará a mantener consistencia y buenas prácticas desde el inicio.

1. Nombre del repositorio
   - Formato recomendado: `kebab-case` (ej.: `mi-proyecto-api`).
   - Prefijos/sufijos útiles: `app`, `api`, `web`, `docs`, `infra`.
   - Evita espacios, acentos y caracteres especiales.

2. Descripción y topics
   - Descripción en 1–2 líneas con propósito y alcance.
   - Añade 3–6 topics (tags) relevantes: lenguaje, framework, dominio.

3. Visibilidad y permisos
   - Público para proyectos de aprendizaje/OSS; privado si contiene información sensible.
   - Configura colaboradores con mínimos privilegios necesarios.

4. Archivos iniciales
   - `README.md`: propósito, instalación, uso rápido, contribución.
   - `.gitignore`: basado en el lenguaje (usa la plantilla de GitHub).
   - `LICENSE`: elige una (MIT para OSS simple, o la de tu preferencia).
   - `CODE_OF_CONDUCT.md` (opcional) y `CONTRIBUTING.md` (recomendado).

5. Convenciones
   - Rama por defecto: `main`.
   - Estilo de mensajes de commit: Conventional Commits (`feat:`, `fix:`, `docs:`...).
   - Versionado: SemVer (ej.: `v0.1.0`).

6. Automatización y plantillas (carpeta `.github/`)
   - `ISSUE_TEMPLATE/bug_report.md` y `feature_request.md`.
   - `PULL_REQUEST_TEMPLATE.md`.
   - `CODEOWNERS` (responsables por ruta/directorio).
   - `workflows/` para CI simple (lint/test).

7. Seguridad y calidad
   - `SECURITY.md` (cómo reportar vulnerabilidades).
   - Dependabot (`.github/dependabot.yml`) para actualizar dependencias.
   - Reglas de protección de rama (`main`) y revisión obligatoria de PRs.

## Mejores prácticas y recomendaciones

- Mantén el `README.md` actualizado: propósito, cómo ejecutar, cómo contribuir, estado de CI.
- Usa etiquetas estándar: `bug`, `feature`, `documentation`, `high priority`.
- Planifica con milestones y Projects (Kanban) desde el inicio de cada etapa.
- Prefiere PRs pequeños, enfocados y con checklist de revisión.
- Evita subir secretos; usa GitHub Secrets para CI/CD.
- Habilita branch protection: mínimo 1 revisor, status checks requeridos, no permitir pushes directos a `main`.
- Define una estrategia de ramas simple: trunk-based o GitHub Flow (`feature/*` → PR → `main`).
- Versiona releases con tags firmados si es posible (`vX.Y.Z`).

## Ejemplo de estructura inicial

```text
.
├─ README.md
├─ .gitignore
├─ LICENSE
├─ .github/
│  ├─ ISSUE_TEMPLATE/
│  │  ├─ bug_report.md
│  │  └─ feature_request.md
│  ├─ PULL_REQUEST_TEMPLATE.md
│  ├─ CODEOWNERS
│  ├─ dependabot.yml
│  └─ workflows/
│     └─ ci.yml
└─ src/ (o carpeta principal de tu lenguaje)
```

## Checklist poscreación (rápido)

1. [ ] Completar descripción y topics del repositorio.
2. [ ] Añadir `.gitignore`, `LICENSE`, `README.md` inicial.
3. [ ] Crear plantillas de issue y PR en `.github/`.
4. [ ] Configurar CI mínimo (lint/test) con GitHub Actions.
5. [ ] Habilitar protección de rama en `main`.
6. [ ] Crear labels base y, si aplica, milestones iniciales.

## Opcional: crear y preparar desde la terminal (PowerShell)

```powershell
# Requiere Git y GitHub CLI (gh)
gh repo create <owner>/<repo-name> --public --source . --remote origin --push

# Iniciales recomendados (si aún no existen)
ni README.md -Force | Out-Null
ni .gitignore -Force | Out-Null
ni LICENSE -Force | Out-Null
mkdir .github\ISSUE_TEMPLATE -Force | Out-Null
mkdir .github\workflows -Force | Out-Null

git add .
git commit -m "chore: bootstrap repo with README, gitignore, license and GitHub templates"
git push -u origin main
```

## Conclusión

Ahora has creado un repositorio de prueba en GitHub. Puedes comenzar a agregar archivos y realizar cambios en él.
