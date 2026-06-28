# Evaluación Fase 5 – Publicación y Automatización (Milestones finales, Releases, Actions)

## Selección múltiple

### Pregunta 1: Objetivo de un release semántico:

- a) Nombrar arbitrariamente
- b) Comunicar cambios (fix, feat, breaking) predecibles (Correcta)
- c) Reducir issues
- d) Forzar tags ocultos

### Pregunta 2: `v0.1.0` implica:

- a) Versión estable mayor
- b) Iteración temprana (pre 1.0) (Correcta)
- c) Parche crítico de seguridad
- d) Retroceso de versión

### Pregunta 3: Archivo para notas automáticas:

- a) `.github/release.yml` (Correcta)
- b) `release-config.json`
- c) `release.txt`
- d) `notes.yml`

### Pregunta 4: GitHub Actions se activan con:

- a) Hooks locales
- b) Eventos (push, pull_request, workflow_dispatch) (Correcta)
- c) Tags manuales directos
- d) Ramas protegidas exclusivamente

### Pregunta 5: Buen nombre de workflow:

- a) Build
- b) “CI – Build & Test” descriptivo (Correcta)
- c) `wf1`
- d) `test` genérico

### Pregunta 6: Secreto almacenado en:

- a) README
- b) GitHub Secrets (Correcta)
- c) Código fuente
- d) Issue privado

### Pregunta 7: Minimizar tiempo de pipeline:

- a) Cache dependencias (Correcta)
- b) Instalar todo cada vez
- c) Evitar matrices
- d) Repetir steps innecesariamente

### Pregunta 8: “Least privilege” en token:

- a) Acceso mínimo necesario (Correcta)
- b) Acceso total siempre
- c) Solo lectura impide releases
- d) Desactiva auditorías

### Pregunta 9: Un release “draft”:

- a) Ya visible para todos
- b) Permite revisión antes de publicar (Correcta)
- c) Borra tags
- d) Forza CI

### Pregunta 10: Al cerrar milestone antes de release:

- a) No relevante
- b) Garantiza que el alcance planificado terminó (Correcta)
- c) Rompe pipeline
- d) Elimina issues

### Pregunta 11: Action reusable:

- a) Es un composite para steps comunes (Correcta)
- b) Reemplaza el repo
- c) Deshabilita YAML
- d) No admite inputs

### Pregunta 12: Matriz de jobs:

- a) Ejecuta combinaciones (ej. versiones de Node) (Correcta)
- b) Duplica logs sin propósito
- c) Bloquea cache
- d) Requiere self-hosted obligado

### Pregunta 13: Paso “checkout” hace:

- a) Generar release
- b) Clonar el repo en runner (Correcta)
- c) Instalar dependencias automáticamente
- d) Subir artefactos

### Pregunta 14: Artefactos:

- a) Sólo logs
- b) Ficheros empaquetados para descarga posterior (Correcta)
- c) Siempre secretos
- d) Variables de env

### Pregunta 15: Tag ligero vs anotado:

- a) Igual
- b) Anotado incluye mensaje y metadata (Correcta)
- c) Ligero tiene firma GPG
- d) Ligero genera release automático

### Pregunta 16: PR fusionado sin tag:

- a) No dispara release basado en tag (Correcta)
- b) Crea release automáticamente
- c) Rompe milestones
- d) Borra acciones previas

### Pregunta 17: `on: pull_request` ejecuta en:

- a) Creación y actualizaciones del PR (Correcta)
- b) Sólo merges
- c) Sólo tags
- d) Rebase local

### Pregunta 18: Recomendación al fallar workflow:

- a) Ignorarlo si es menor
- b) Corregir y reejecutar con `gh workflow run` o re-push (Correcta)
- c) Forzar merge
- d) Borrar historial

### Pregunta 19: Archivar notas release:

- a) En issues
- b) En tag annotation y CHANGELOG (Correcta)
- c) En README siempre
- d) No se guarda

### Pregunta 20: Riesgo de credenciales en repositorio:

- a) Aumenta seguridad
- b) Exposición y revocación necesaria (Correcta)
- c) Mejora CI
- d) Obliga a más tests

## Práctica

1. Pasos para generar un release candidato a partir de milestone cerrado.
2. YAML mínimo para workflow que instale dependencias y ejecute pruebas.
3. Explica cuándo crearías un hotfix `v0.1.1` tras `v0.1.0`.
