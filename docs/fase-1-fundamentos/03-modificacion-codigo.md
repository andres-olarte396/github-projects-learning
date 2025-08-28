# Cambio pequeño en el código

Para realizar un cambio pequeño en el código, sigue estos pasos:

1. **Clona el repositorio** en tu máquina local si aún no lo has hecho:

   ```bash
   git clone https://github.com/tu-usuario/nombre-repositorio.git
   ```

2. **Navega al directorio del repositorio**:

   ```powershell
   cd nombre-repositorio
   ```

3. **Crea una nueva rama** para tu cambio:

   ```powershell
   git checkout -b nombre-de-la-rama
   ```

4. **Realiza el cambio** en el archivo que deseas modificar. Por ejemplo, si quieres cambiar un mensaje en un archivo `app.js`:

   ```javascript
   console.log("Hola, mundo!");
   ```

5. **Guarda los cambios** y asegúrate de que todo funcione correctamente.

6. **Agrega los cambios** al área de preparación:

   ```powershell
   git add app.js
   ```

7. **Realiza el commit** de tus cambios:

   ```powershell
   git commit -m "Descripción del cambio realizado"
   ```

8. **Sube la rama** a tu repositorio en GitHub:

   ```powershell
   git push origin nombre-de-la-rama
   ```

Ahora has realizado un cambio pequeño en el código y lo has preparado para ser revisado.

## Formato recomendado

- Ramas de feature: `feat/<area>-<descripcion-corta>`.
- Commits: usa Conventional Commits (`feat:`, `fix:`, `docs:`…).
- PR: título claro y referencia a issue si aplica.

## Mejores prácticas

- Cambios pequeños y atómicos; un propósito por PR.
- Ejecuta linters/pruebas locales antes de subir.
- Describe el contexto del cambio y riesgos.
- Incluye screenshots si hay UI.

## Comandos PowerShell (Git y gh)

```powershell
# Crear rama, commit y subir
git checkout -b feat/demo-cambio
git add .
git commit -m "feat: demo de cambio pequeño"
git push -u origin HEAD

# Abrir PR desde terminal (requiere GitHub CLI)
gh pr create --title "feat: demo de cambio pequeño" --body "Descripción y contexto" --base main
```
