# Evaluación Fase 5 – Publicación y Automatización (Milestones finales, Releases, Actions)

## Selección múltiple

1. Objetivo de un release semántico:
- [ ] A. Nombrar arbitrariamente  
- [ ] B. Comunicar cambios (fix, feat, breaking) predecibles  
- [ ] C. Reducir issues  
- [ ] D. Forzar tags ocultos  

2. `v0.1.0` implica:
- [ ] A. Versión estable mayor  
- [ ] B. Iteración temprana (pre 1.0)  
- [ ] C. Parche crítico de seguridad  
- [ ] D. Retroceso de versión  

3. Archivo para notas automáticas:
- [ ] A. `.github/release.yml`  
- [ ] B. `release-config.json`  
- [ ] C. `release.txt`  
- [ ] D. `notes.yml`  

4. GitHub Actions se activan con:
- [ ] A. Hooks locales  
- [ ] B. Eventos (push, pull_request, workflow_dispatch)  
- [ ] C. Tags manuales directos  
- [ ] D. Ramas protegidas exclusivamente  

5. Buen nombre de workflow:
- [ ] A. Build  
- [ ] B. “CI – Build & Test” descriptivo  
- [ ] C. `wf1`  
- [ ] D. `test` genérico  

6. Secreto almacenado en:
- [ ] A. README  
- [ ] B. GitHub Secrets  
- [ ] C. Código fuente  
- [ ] D. Issue privado  

7. Minimizar tiempo de pipeline:
- [ ] A. Cache dependencias  
- [ ] B. Instalar todo cada vez  
- [ ] C. Evitar matrices  
- [ ] D. Repetir steps innecesariamente  

8. “Least privilege” en token:
- [ ] A. Acceso mínimo necesario  
- [ ] B. Acceso total siempre  
- [ ] C. Solo lectura impide releases  
- [ ] D. Desactiva auditorías  

9. Un release “draft”:
- [ ] A. Ya visible para todos  
- [ ] B. Permite revisión antes de publicar  
- [ ] C. Borra tags  
- [ ] D. Forza CI  

10. Al cerrar milestone antes de release:
- [ ] A. No relevante  
- [ ] B. Garantiza que el alcance planificado terminó  
- [ ] C. Rompe pipeline  
- [ ] D. Elimina issues  

11. Action reusable:
- [ ] A. Es un composite para steps comunes  
- [ ] B. Reemplaza el repo  
- [ ] C. Deshabilita YAML  
- [ ] D. No admite inputs  

12. Matriz de jobs:
- [ ] A. Ejecuta combinaciones (ej. versiones de Node)  
- [ ] B. Duplica logs sin propósito  
- [ ] C. Bloquea cache  
- [ ] D. Requiere self-hosted obligado  

13. Paso “checkout” hace:
- [ ] A. Generar release  
- [ ] B. Clonar el repo en runner  
- [ ] C. Instalar dependencias automáticamente  
- [ ] D. Subir artefactos  

14. Artefactos:
- [ ] A. Sólo logs  
- [ ] B. Ficheros empaquetados para descarga posterior  
- [ ] C. Siempre secretos  
- [ ] D. Variables de env  

15. Tag ligero vs anotado:
- [ ] A. Igual  
- [ ] B. Anotado incluye mensaje y metadata  
- [ ] C. Ligero tiene firma GPG  
- [ ] D. Ligero genera release automático  

16. PR fusionado sin tag:
- [ ] A. No dispara release basado en tag  
- [ ] B. Crea release automáticamente  
- [ ] C. Rompe milestones  
- [ ] D. Borra acciones previas  

17. `on: pull_request` ejecuta en:
- [ ] A. Creación y actualizaciones del PR  
- [ ] B. Sólo merges  
- [ ] C. Sólo tags  
- [ ] D. Rebase local  

18. Recomendación al fallar workflow:
- [ ] A. Ignorarlo si es menor  
- [ ] B. Corregir y reejecutar con `gh workflow run` o re-push  
- [ ] C. Forzar merge  
- [ ] D. Borrar historial  

19. Archivar notas release:
- [ ] A. En issues  
- [ ] B. En tag annotation y CHANGELOG  
- [ ] C. En README siempre  
- [ ] D. No se guarda  

20. Riesgo de credenciales en repositorio:
- [ ] A. Aumenta seguridad  
- [ ] B. Exposición y revocación necesaria  
- [ ] C. Mejora CI  
- [ ] D. Obliga a más tests  

## Práctica

21. Pasos para generar un release candidato a partir de milestone cerrado.  
22. YAML mínimo para workflow que instale dependencias y ejecute pruebas.  
23. Explica cuándo crearías un hotfix `v0.1.1` tras `v0.1.0`.  
