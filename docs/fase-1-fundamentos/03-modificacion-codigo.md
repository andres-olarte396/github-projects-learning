# Cambio pequeño en el código

Para realizar un cambio pequeño en el código, sigue estos pasos:

1. **Clona el repositorio** en tu máquina local si aún no lo has hecho:
   ```
   git clone https://github.com/tu-usuario/nombre-repositorio.git
   ```

2. **Navega al directorio del repositorio**:
   ```
   cd nombre-repositorio
   ```

3. **Crea una nueva rama** para tu cambio:
   ```
   git checkout -b nombre-de-la-rama
   ```

4. **Realiza el cambio** en el archivo que deseas modificar. Por ejemplo, si quieres cambiar un mensaje en un archivo `app.js`:
   ```javascript
   console.log("Hola, mundo!");
   ```

5. **Guarda los cambios** y asegúrate de que todo funcione correctamente.

6. **Agrega los cambios** al área de preparación:
   ```
   git add app.js
   ```

7. **Realiza el commit** de tus cambios:
   ```
   git commit -m "Descripción del cambio realizado"
   ```

8. **Sube la rama** a tu repositorio en GitHub:
   ```
   git push origin nombre-de-la-rama
   ```

Ahora has realizado un cambio pequeño en el código y lo has preparado para ser revisado.