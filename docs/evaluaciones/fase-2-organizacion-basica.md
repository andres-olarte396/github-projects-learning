# Evaluación Fase 2 – Organización (Labels, Milestones, Asignación)

## Selección múltiple

### Pregunta 1: Objetivo principal de un milestone:

- a) Reducir el tamaño del repo
- b) Agrupar issues hacia un objetivo temporal (Correcta)
- c) Borrar ramas viejas
- d) Reemplazar etiquetas

### Pregunta 2: ¿Qué riesgo hay con demasiadas etiquetas?

- a) Mejora filtrado
- b) Aumenta confusión y disminuye adopción (Correcta)
- c) Acelera decisiones
- d) Obliga a usar bots

### Pregunta 3: Color de etiquetas:

- a) Irrelevante
- b) Puede comunicar categorías visuales coherentes (Correcta)
- c) Debe ser aleatorio
- d) Cambia el rendimiento

### Pregunta 4: Un “scope creep” en milestone indica:

- a) Falta de repos remotos
- b) Se agregan tareas fuera del objetivo original (Correcta)
- c) Milestone vacío
- d) Etiquetas duplicadas internas

### Pregunta 5: ¿Qué combinación aporta más prioridad?

- a) Sólo label `bug`
- b) `type: bug` + `priority: high` (Correcta)
- c) Label sin descripción
- d) Reabrir issues cerrados

### Pregunta 6: KPI inicial de salud de milestone:

- a) % issues cerrados vs plan (Correcta)
- b) Cantidad de forks
- c) Commits por hora
- d) Tamaño del README

### Pregunta 7: Reubicar issue cuando:

- a) Bloqueado y no se resolverá a tiempo (Correcta)
- b) Ya está cerrado
- c) No tiene comentarios
- d) Tiene PR vinculado

### Pregunta 8: Etiqueta `status: blocked` se quita:

- a) Tras agregar un label extra
- b) Al cerrar el issue sin resolver
- c) Cuando se elimina el milestone
- d) Cuando se resuelve la dependencia que bloqueaba (Correcta)

### Pregunta 9: Definir DoR para un issue sirve para:

- a) Evitar estimaciones
- b) Saber si está listo para entrar a un sprint/milestone (Correcta)
- c) Cambiar permisos
- d) Hacer merges directos

### Pregunta 10: Un milestone saturado (>130% capacidad) produce:

- a) Velocidad predecible
- b) Riesgo de arrastre y baja calidad (Correcta)
- c) Menos triage
- d) Menos dependencias

### Pregunta 11: Etiqueta sin descripción:

- a) Está bien siempre
- b) Reduce entendimiento del equipo (Correcta)
- c) Mejora onboarding
- d) Facilita automatización

### Pregunta 12: Métrica útil en groomings:

- a) Issues sin label ni milestone (Correcta)
- b) Número de forks
- c) Stars recibidos
- d) Tiempo de clonación

### Pregunta 13: Un issue no asignado y sin milestone:

- a) Prioridad máxima
- b) Candidato a triage / backlog (Correcta)
- c) Requiere deploy inmediato
- d) No puede etiquetarse

### Pregunta 14: ¿Qué campo de Projects complementa labels?

- a) Branch
- b) Custom field (Priority / Status) (Correcta)
- c) README
- d) .gitignore

### Pregunta 15: Al cerrar un milestone:

- a) Se borran issues
- b) Se congelan PRs
- c) Se reubican pendientes y se documentan notas (Correcta)
- d) Se elimina la historia de Git

### Pregunta 16: Ventaja de estandarizar prefijos label (type:, priority:):

- a) Dificulta búsquedas
- b) Permite filtros rápidos y consistentes (Correcta)
- c) Destruye filtros nativos
- d) Bloquea merges

### Pregunta 17: Para encontrar issues sin milestone:

- a) `gh issue list --search "no:milestone"` (Correcta)
- b) `git milestone list --null`
- c) `gh milestone orphan`
- d) `git issue orphan`

### Pregunta 18: Riesgo de no revisar progreso a mitad de ciclo:

- a) Exceso de visibilidad
- b) Rescate tardío de bloqueos (Correcta)
- c) Menos backlog
- d) Mejor planeación automática

### Pregunta 19: “Spillover” significa:

- a) Commits grandes
- b) Issues que se arrastran al siguiente milestone (Correcta)
- c) Repositorio duplicado
- d) PR reabierto

### Pregunta 20: Acción preventiva para evitar spillover:

- a) No medir capacidad
- b) Grooming y recorte tempranos (Correcta)
- c) Agregar tareas sin observar carga
- d) Demorar etiquetado

## Práctica

1. Proponer esquema inicial de labels (≥6) con prefijos.
2. Redactar criterios para cerrar un milestone de sprint de 2 semanas.
3. Comando gh para listar issues abiertos con `priority: high` y sin milestone.

(Rúbrica igual concepto que Fase 1 adaptada.)
