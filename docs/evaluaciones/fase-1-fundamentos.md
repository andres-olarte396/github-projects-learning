# Evaluación Fase 1 – Fundamentos (Issues, Commits, PR básicos)

Instrucciones
Marca una opción (A–D) por pregunt- [ ] A. Las preguntas 21–23 son prácticas.

## Objetivos evaluados

- Creación y uso de issues
- Flujo básico de commits y ramas mínimas
- Pull Requests y cierre automático
- Etiquetado inicial y trazabilidad básica

## Parte I – Selección múltiple

1. ¿Cuál es el beneficio principal de vincular un PR con `Closes #12`?
- [ ] A. Acelera el pipeline de CI  
- [ ] B. Cierra el issue al fusionar el PR  
- [ ] C. Evita conflictos de merge  
- [ ] D. Cambia la base del PR  

2. Un buen título de issue debe:
- [ ] A. Ser genérico para reutilizarse  
- [ ] B. Incluir múltiples problemas para ahorrar tiempo  
- [ ] C. Enfocarse en un único problema claro  
- [ ] D. Omitir el contexto para ser breve  

3. ¿Cuál **comando** crea un repositorio local y conecta el remoto?
- [ ] A. `git init && git remote add origin <url>`  
- [ ] B. `git start <url>`  
- [ ] C. `git repo create <url>`  
- [ ] D. `git connect origin <url>`  

4. Un commit “atómico” significa:
- [ ] A. Muy grande con muchos cambios  
- [ ] B. Incluye código y binarios mezclados  
- [ ] C. Agrupa exactamente un propósito lógico  
- [ ] D. Solo cambia documentación  

5. ¿Cuál convención de mensaje sigue Conventional Commits?
- [ ] A. `build(scope): ...`  
- [ ] B. `scope:build ...`  
- [ ] C. `[build scope]`  
- [ ] D. `build=>scope`  

6. Un PR en estado “Draft” sirve para:
- [ ] A. Bloquear revisiones  
- [ ] B. Ejecutar CI y permitir feedback temprano  
- [ ] C. Fusionarse automáticamente  
- [ ] D. Crear etiquetas de forma automática  

7. ¿Qué NO debe hacerse en un commit?
- [ ] A. Incluir pruebas  
- [ ] B. Cambiar 1 feature a la vez  
- [ ] C. Mezclar refactors y hotfix críticos sin separar  
- [ ] D. Referenciar un issue  

8. ¿Cuándo usar etiquetas?
- [ ] A. Sólo al final del sprint  
- [ ] B. Cuando se necesita filtrar, priorizar y agrupar issues  
- [ ] C. Nunca en proyectos pequeños  
- [ ] D. Solo en PRs, no issues  

9. Ventaja de usar ramas feature/*:
- [ ] A. Reducen la historia de Git  
- [ ] B. Evitan que main cambie  
- [ ] C. Aíslan cambios y facilitan PRs pequeños  
- [ ] D. Obligan a reescribir main  

10. ¿Cuál es mejor práctica antes de abrir un PR?
- [ ] A. Forzar push sin revisar  
- [ ] B. Asegurar que la rama esté actualizada con main  
- [ ] C. Reescribir el historial público sin coordinación  
- [ ] D. Ignorar conflictos menores  

11. ¿Cuál documento orienta primero a nuevos colaboradores?
- [ ] A. LICENSE  
- [ ] B. README  
- [ ] C. CHANGELOG  
- [ ] D. .gitignore  

12. ¿Para qué sirve un ISSUE_TEMPLATE?
- [ ] A. Restringe crear issues  
- [ ] B. Estandariza la información mínima para triage  
- [ ] C. Impide cerrar issues rápido  
- [ ] D. Obliga a usar forks  

13. ¿Qué palabra clave cierra un issue al fusionar PR?
- [ ] A. Related  
- [ ] B. Fixes  
- [ ] C. Refs  
- [ ] D. Mirrors  

14. ¿Qué se revisa en un PR básico?
- [ ] A. Estrategia financiera  
- [ ] B. Cambios de infraestructura ajenos  
- [ ] C. Coherencia, alcance, evidencia de pruebas  
- [ ] D. Velocidad de CPU  

15. ¿Qué evita un commit enorme?
- [ ] A. Revisiones ágiles  
- [ ] B. Reversión controlada  
- [ ] C. Comprensión de diffs  
- [ ] D. Todas las anteriores  

16. ¿Qué NO va en un buen mensaje de commit?
- [ ] A. Contexto breve  
- [ ] B. Qué y por qué  
- [ ] C. Referencia al issue  
- [ ] D. Argumentos personales irrelevantes  

17. ¿Qué archivo debe existir para licencias abiertas?
- [ ] A. LICENSE  
- [ ] B. CONTRIBUTE  
- [ ] C. PATTERNS  
- [ ] D. AUTHORS.yml  

18. ¿Cuándo conviene squash merge?
- [ ] A. Cuando se desean múltiples commits sueltos  
- [ ] B. Para condensar commits de trabajo ruidosos  
- [ ] C. Para eliminar el historial de main  
- [ ] D. Cuando se quiere duplicar el diff  

19. ¿Qué acción produce más trazabilidad?
- [ ] A. Commits sin descripción  
- [ ] B. Referenciar issues y usar keywords en PR  
- [ ] C. Revertir cada cambio siempre  
- [ ] D. Fusionar directo en main sin PR  

20. Beneficio de un PR pequeño:
- [ ] A. Aumenta riesgo de bugs  
- [ ] B. Acelera revisión y reduce conflictos  
- [ ] C. Dificulta revertir  
- [ ] D. Rompe la integración continua  

## Parte II – Práctica (respuesta abierta)

21. Escribe un título y cuerpo de issue para reportar un error en la función de interpolación (incluye criterios de aceptación).  
22. Proporciona un ejemplo de mensaje de commit siguiendo Conventional Commits que arregle un bug referenciando el issue 45.  
23. Describe en 4–5 pasos cómo crear un PR que cierre el issue #72 usando “Fixes”.  

## Parte III – (Opcional) Rúbrica de corrección práctica

- Claridad (0–2)
- Criterios medibles (0–2)
- Referencias (0–1)
- Formato consistente (0–1)
