# Evaluación Fase 4 – Flujo de Desarrollo (Branching, Commits, PR, CI básico)

## Selección múltiple

### Pregunta 1: Ventaja de rama `feature/<id>-slug`:

- a) Oculta cambios
- b) Identificable y trazable (Correcta)
- c) Bloquea merges
- d) Reemplaza etiquetas

### Pregunta 2: “Draft PR” sirve para:

- a) Fusionar sin revisión
- b) Feedback temprano y CI inicial (Correcta)
- c) Comprimir historia
- d) Forzar rebase automático

### Pregunta 3: Rebase interactivo objetivo:

- a) Duplicar commits
- b) Limpiar y organizar historia local antes de publicar (Correcta)
- c) Eliminar tags
- d) Evitar pruebas

### Pregunta 4: `fix(scope): corrige validación` es:

- a) Un commit siguiendo Conventional Commits (Correcta)
- b) Un tag Git
- c) Un título de issue
- d) Un mensaje de release

### Pregunta 5: `Closes #34` en PR:

- a) Solo referencia
- b) Cierra issue al fusionar (Correcta)
- c) Cambia base del PR
- d) Reabre el issue

### Pregunta 6: Estrategia de merges que conserva historia:

- a) Squash
- b) Rebase + merge (fast-forward si posible) (Correcta)
- c) Cherry-pick
- d) Force push a main

### Pregunta 7: Commit firmado (GPG) aporta:

- a) Rendimiento
- b) Autenticidad (Correcta)
- c) Más conflictos
- d) Pierde autoría

### Pregunta 8: Evitar “big bang PR”:

- a) Genera deuda de revisión
- b) Mejora confianza
- c) Acelera merges
- d) Reduce riesgos (Correcta)

### Pregunta 9: PR listo para revisión:

- a) Falta descripción
- b) CI verde y criterios claros (Correcta)
- c) Sin relación a issue
- d) Con diffs irrelevantes

### Pregunta 10: Test mínimo en PR nuevo:

- a) Ninguno
- b) Cubrir ruta crítica del cambio (Correcta)
- c) Reescribir todos los tests
- d) Eliminarlos

### Pregunta 11: Referencia parcial sin cierre:

- a) `Refs #12` (Correcta)
- b) `Closes #12`
- c) `Fixes #12`
- d) `Resolve #12`

### Pregunta 12: Hook pre-commit:

- a) Ejecuta validaciones antes de crear commit (Correcta)
- b) Forza merges
- c) Cambia diff remoto
- d) Reescribe tags

### Pregunta 13: Parametrizar CI ayuda a:

- a) Evitar cache
- b) Minimizar ejecuciones redundantes (Correcta)
- c) Romper pipelines
- d) Saltar revisión

### Pregunta 14: Commit que agrupa refactor y fix crítico:

- a) Aumenta claridad
- b) Mezcla propósitos y dificulta revertir (Correcta)
- c) Mejora cherry-pick
- d) Optimiza tag

### Pregunta 15: “Amend” correcto:

- a) Editar último commit local antes de push (Correcta)
- b) Reescribir historia remota sin pull
- c) Borrar tags
- d) Fusionar ramas

### Pregunta 16: Pull con rebase:

- a) `git pull --rebase` reduce merges triviales (Correcta)
- b) Elimina commits locales
- c) Bloquea pushes
- d) Cambia tags

### Pregunta 17: Plantilla PR coherente:

- a) Requiere pasos de prueba y checklist (Correcta)
- b) Debe estar vacía
- c) Solo título
- d) Ignora impacto

### Pregunta 18: Sincronizar rama local:

- a) `git fetch origin main && git rebase origin/main` (Correcta)
- b) `git rebase --delete`
- c) `git force main`
- d) `git sync remote`

### Pregunta 19: Revisiones rápidas efectivas:

- a) Pequeños lotes y claridad de cambios (Correcta)
- b) Combinar features dispares
- c) Saltar descripciones
- d) Ignorar comentarios

### Pregunta 20: Estrategia para reducir conflictos:

- a) PRs cortos, merges frecuentes (Correcta)
- b) Muchos commits masivos tardíos
- c) Forzar pushes a main
- d) Postergar integración

## Práctica

1. Escribe un commit message para añadir validación de parámetros invalidando uno obsoleto (breaking).
2. Explica cuándo usar squash vs merge commit.
3. Proporciona 4 pasos para crear un PR de una rama local y enlazar issue #90.
