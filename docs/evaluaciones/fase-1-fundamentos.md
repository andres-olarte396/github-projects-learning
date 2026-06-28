# Evaluación Fase 1 – Fundamentos (Issues, Commits, PR básicos)

Instrucciones
Marca una opción (A–D) por pregunt

- A. Las preguntas 21–23 son prácticas.

## Objetivos evaluados

- Creación y uso de issues
- Flujo básico de commits y ramas mínimas
- Pull Requests y cierre automático
- Etiquetado inicial y trazabilidad básica

## Parte I – Selección múltiple

### Pregunta 1: ¿Cuál es el beneficio principal de vincular un PR con `Closes #12`?

- a) Acelera el pipeline de CI
- b) Cierra el issue al fusionar el PR (Correcta)
- c) Evita conflictos de merge
- d) Cambia la base del PR

### Pregunta 2: Un buen título de issue debe:

- a) Ser genérico para reutilizarse
- b) Incluir múltiples problemas para ahorrar tiempo
- c) Enfocarse en un único problema claro (Correcta)
- d) Omitir el contexto para ser breve

### Pregunta 3: ¿Cuál **comando** crea un repositorio local y conecta el remoto?

- a) `git init && git remote add origin <url>` (Correcta)
- b) `git start <url>`
- c) `git repo create <url>`
- d) `git connect origin <url>`

### Pregunta 4: Un commit “atómico” significa:

- a) Muy grande con muchos cambios
- b) Incluye código y binarios mezclados
- c) Agrupa exactamente un propósito lógico (Correcta)
- d) Solo cambia documentación

### Pregunta 5: ¿Cuál convención de mensaje sigue Conventional Commits?

- a) `build(scope): ...` (Correcta)
- b) `scope:build ...`
- c) `[build scope]`
- d) `build=>scope`

### Pregunta 6: Un PR en estado “Draft” sirve para:

- a) Bloquear revisiones
- b) Ejecutar CI y permitir feedback temprano (Correcta)
- c) Fusionarse automáticamente
- d) Crear etiquetas de forma automática

### Pregunta 7: ¿Qué NO debe hacerse en un commit?

- a) Incluir pruebas
- b) Cambiar 1 feature a la vez
- c) Mezclar refactors y hotfix críticos sin separar (Correcta)
- d) Referenciar un issue

### Pregunta 8: ¿Cuándo usar etiquetas?

- a) Sólo al final del sprint
- b) Cuando se necesita filtrar, priorizar y agrupar issues (Correcta)
- c) Nunca en proyectos pequeños
- d) Solo en PRs, no issues

### Pregunta 9: Ventaja de usar ramas feature/\*:

- a) Reducen la historia de Git
- b) Evitan que main cambie
- c) Aíslan cambios y facilitan PRs pequeños (Correcta)
- d) Obligan a reescribir main

### Pregunta 10: ¿Cuál es mejor práctica antes de abrir un PR?

- a) Forzar push sin revisar
- b) Asegurar que la rama esté actualizada con main (Correcta)
- c) Reescribir el historial público sin coordinación
- d) Ignorar conflictos menores

### Pregunta 11: ¿Cuál documento orienta primero a nuevos colaboradores?

- a) LICENSE
- b) README (Correcta)
- c) CHANGELOG
- d) .gitignore

### Pregunta 12: ¿Para qué sirve un ISSUE_TEMPLATE?

- a) Restringe crear issues
- b) Estandariza la información mínima para triage (Correcta)
- c) Impide cerrar issues rápido
- d) Obliga a usar forks

### Pregunta 13: ¿Qué palabra clave cierra un issue al fusionar PR?

- a) Related
- b) Fixes (Correcta)
- c) Refs
- d) Mirrors

### Pregunta 14: ¿Qué se revisa en un PR básico?

- a) Estrategia financiera
- b) Cambios de infraestructura ajenos
- c) Coherencia, alcance, evidencia de pruebas (Correcta)
- d) Velocidad de CPU

### Pregunta 15: ¿Qué evita un commit enorme?

- a) Revisiones ágiles
- b) Reversión controlada
- c) Comprensión de diffs
- d) Todas las anteriores (Correcta)

### Pregunta 16: ¿Qué NO va en un buen mensaje de commit?

- a) Contexto breve
- b) Qué y por qué
- c) Referencia al issue
- d) Argumentos personales irrelevantes (Correcta)

### Pregunta 17: ¿Qué archivo debe existir para licencias abiertas?

- a) LICENSE (Correcta)
- b) CONTRIBUTE
- c) PATTERNS
- d) AUTHORS.yml

### Pregunta 18: ¿Cuándo conviene squash merge?

- a) Cuando se desean múltiples commits sueltos
- b) Para condensar commits de trabajo ruidosos (Correcta)
- c) Para eliminar el historial de main
- d) Cuando se quiere duplicar el diff

### Pregunta 19: ¿Qué acción produce más trazabilidad?

- a) Commits sin descripción
- b) Referenciar issues y usar keywords en PR (Correcta)
- c) Revertir cada cambio siempre
- d) Fusionar directo en main sin PR

### Pregunta 20: Beneficio de un PR pequeño:

- a) Aumenta riesgo de bugs
- b) Acelera revisión y reduce conflictos (Correcta)
- c) Dificulta revertir
- d) Rompe la integración continua

## Parte II – Práctica (respuesta abierta)

1. Escribe un título y cuerpo de issue para reportar un error en la función de interpolación (incluye criterios de aceptación).
2. Proporciona un ejemplo de mensaje de commit siguiendo Conventional Commits que arregle un bug referenciando el issue 45.
3. Describe en 4–5 pasos cómo crear un PR que cierre el issue #72 usando “Fixes”.

## Parte III – (Opcional) Rúbrica de corrección práctica

- Claridad (0–2)
- Criterios medibles (0–2)
- Referencias (0–1)
- Formato consistente (0–1)
