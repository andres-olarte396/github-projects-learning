# Hacer commits en la rama de la funcionalidad

Los commits deben ser pequeños, descriptivos y referenciar el issue cuando sea posible.

## Pasos

1. Realiza cambios en los archivos de tu proyecto (por ejemplo, agrega `lerp` en un archivo de utilidades o ejemplo).
2. Añade los cambios al staging:

```powershell
git add .
```

1. Crea un commit con mensaje significativo y referencia al issue (ejemplo issue #12):

```powershell
git commit -m "feat: implementar lerp(a, b, t); casos base y tests (refs #12)"
```

1. Repite para más cambios. Sube tu rama al remoto:

```powershell
git push -u origin feature/interpolador-lineal
```

---

> Consejo: Prefiere mensajes de commit con prefijos convencionales (feat, fix, docs, refactor).

## Formato recomendado de mensajes de commit (Conventional Commits)

Estructura

- `tipo(scope): resumen breve`
- Cuerpo (opcional): detalles, motivación, impacto
- Footer (opcional): `Closes #123`, `Refs #456`, `BREAKING CHANGE: ...`

Tipos comunes

- `feat` nueva funcionalidad
- `fix` corrección de bug
- `docs` documentación
- `refactor` cambio interno sin alterar comportamiento
- `test` pruebas, `chore` tareas varias, `ci` pipelines, `build` dependencias, `perf` rendimiento, `style` formato

Ejemplos

- `feat(core): implementar lerp(a,b,t) con casos base`
- `fix(math): manejar t fuera de [0,1] sin excepciones (refs #12)`
- `docs(api): agregar ejemplos de uso de lerp`

## Mejores prácticas

- Un commit por intención; pequeño y atómico.
- Mensaje en modo imperativo y resumen ≤ 72 caracteres si es posible.
- Referencia issues con `Refs #N` o cierre automático con `Closes #N`.
- Ejecuta pruebas y linters antes de commitear.
- Usa `Co-authored-by:` en el footer para trabajo colaborativo.

## Comandos PowerShell (git)

```powershell
# Ver cambios y preparar staging
git status
git diff
git add -p    # staging interactivo (opcional)
git add .     # o añade todo si ya revisaste

# Commit con body y referencias (múltiples -m para varias líneas)
git commit -m "feat(core): implementar lerp(a,b,t)" `
		   -m "Casos base: t=0, t=1, t=0.5" `
		   -m "Closes #12"

# Enmendar el último commit (ajustar archivos o mensaje)
git add .
git commit --amend -m "feat(core): implementar lerp(a,b,t) y pruebas (Closes #12)"

# Publicar la rama actual (ajusta $branch si no está configurado upstream)
$branch = git branch --show-current
git push -u origin $branch

# Opcional: firmar commits con sign-off
git commit -s -m "feat(core): validar rangos de t (Refs #12)"

# Opcional: squash de commits recientes (edición interactiva)
# git rebase -i HEAD~3
```

> Nota: Usa `git restore --staged <archivo>` o `git reset -p` para deshacer staging selectivo. Prefiere `--force-with-lease` si necesitas actualizar el historial remoto tras un amend.
