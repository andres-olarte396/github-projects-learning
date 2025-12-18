# Evaluación Fase 4 – Flujo de Desarrollo (Branching, Commits, PR, CI básico)

## Selección múltiple

1. Ventaja de rama `feature/<id>-slug`:
- [ ] A. Oculta cambios  
- [ ] B. Identificable y trazable  
- [ ] C. Bloquea merges  
- [ ] D. Reemplaza etiquetas  

2. “Draft PR” sirve para:
- [ ] A. Fusionar sin revisión  
- [ ] B. Feedback temprano y CI inicial  
- [ ] C. Comprimir historia  
- [ ] D. Forzar rebase automático  

3. Rebase interactivo objetivo:
- [ ] A. Duplicar commits  
- [ ] B. Limpiar y organizar historia local antes de publicar  
- [ ] C. Eliminar tags  
- [ ] D. Evitar pruebas  

4. `fix(scope): corrige validación` es:
- [ ] A. Un commit siguiendo Conventional Commits  
- [ ] B. Un tag Git  
- [ ] C. Un título de issue  
- [ ] D. Un mensaje de release  

5. `Closes #34` en PR:
- [ ] A. Solo referencia  
- [ ] B. Cierra issue al fusionar  
- [ ] C. Cambia base del PR  
- [ ] D. Reabre el issue  

6. Estrategia de merges que conserva historia:
- [ ] A. Squash  
- [ ] B. Rebase + merge (fast-forward si posible)  
- [ ] C. Cherry-pick  
- [ ] D. Force push a main  

7. Commit firmado (GPG) aporta:
- [ ] A. Rendimiento  
- [ ] B. Autenticidad  
- [ ] C. Más conflictos  
- [ ] D. Pierde autoría  

8. Evitar “big bang PR”:
- [ ] A. Genera deuda de revisión  
- [ ] B. Mejora confianza  
- [ ] C. Acelera merges  
- [ ] D. Reduce riesgos  

9. PR listo para revisión:
- [ ] A. Falta descripción  
- [ ] B. CI verde y criterios claros  
- [ ] C. Sin relación a issue  
- [ ] D. Con diffs irrelevantes  

10. Test mínimo en PR nuevo:
- [ ] A. Ninguno  
- [ ] B. Cubrir ruta crítica del cambio  
- [ ] C. Reescribir todos los tests  
- [ ] D. Eliminarlos  

11. Referencia parcial sin cierre:
- [ ] A. `Refs #12`  
- [ ] B. `Closes #12`  
- [ ] C. `Fixes #12`  
- [ ] D. `Resolve #12`  

12. Hook pre-commit:
- [ ] A. Ejecuta validaciones antes de crear commit  
- [ ] B. Forza merges  
- [ ] C. Cambia diff remoto  
- [ ] D. Reescribe tags  

13. Parametrizar CI ayuda a:
- [ ] A. Evitar cache  
- [ ] B. Minimizar ejecuciones redundantes  
- [ ] C. Romper pipelines  
- [ ] D. Saltar revisión  

14. Commit que agrupa refactor y fix crítico:
- [ ] A. Aumenta claridad  
- [ ] B. Mezcla propósitos y dificulta revertir  
- [ ] C. Mejora cherry-pick  
- [ ] D. Optimiza tag  

15. “Amend” correcto:
- [ ] A. Editar último commit local antes de push  
- [ ] B. Reescribir historia remota sin pull  
- [ ] C. Borrar tags  
- [ ] D. Fusionar ramas  

16. Pull con rebase:
- [ ] A. `git pull --rebase` reduce merges triviales  
- [ ] B. Elimina commits locales  
- [ ] C. Bloquea pushes  
- [ ] D. Cambia tags  

17. Plantilla PR coherente:
- [ ] A. Requiere pasos de prueba y checklist  
- [ ] B. Debe estar vacía  
- [ ] C. Solo título  
- [ ] D. Ignora impacto  

18. Sincronizar rama local:
- [ ] A. `git fetch origin main && git rebase origin/main`  
- [ ] B. `git rebase --delete`  
- [ ] C. `git force main`  
- [ ] D. `git sync remote`  

19. Revisiones rápidas efectivas:
- [ ] A. Pequeños lotes y claridad de cambios  
- [ ] B. Combinar features dispares  
- [ ] C. Saltar descripciones  
- [ ] D. Ignorar comentarios  

20. Estrategia para reducir conflictos:
- [ ] A. PRs cortos, merges frecuentes  
- [ ] B. Muchos commits masivos tardíos  
- [ ] C. Forzar pushes a main  
- [ ] D. Postergar integración  

## Práctica

21. Escribe un commit message para añadir validación de parámetros invalidando uno obsoleto (breaking).  
22. Explica cuándo usar squash vs merge commit.  
23. Proporciona 4 pasos para crear un PR de una rama local y enlazar issue #90.  
