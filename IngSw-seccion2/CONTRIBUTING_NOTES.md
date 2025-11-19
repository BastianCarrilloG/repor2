# Resolución de conflictos y trabajo en `main`

Este proyecto no usa ramas adicionales en el remoto. Sigue estos pasos para
mantenerte en `main` y resolver conflictos cuando GitHub muestre el aviso
"This branch has conflicts that must be resolved":

1. **Actualizar la rama local `main`:**
   ```bash
   git checkout main
   git fetch origin
   git reset --hard origin/main
   ```
   Esto asegura que tu copia local coincida con la versión más reciente del
   repositorio remoto.

2. **Aplicar tus cambios sobre `main`:**
   Trabaja normalmente (edita archivos, ejecuta pruebas, etc.). Cuando estés
   listo para guardar el progreso:
   ```bash
   git add <archivos>
   git commit -m "<mensaje descriptivo>"
   ```

3. **Sincronizar con el remoto:**
   Si otra persona subió commits mientras trabajabas, Git puede indicar
   conflictos al intentar hacer `push`. Para resolverlos:
   ```bash
   git pull --rebase origin main
   # Edita los archivos marcados con <<<<<<<, =======, >>>>>>> y conserva la versión correcta.
   git add <archivos resueltos>
   git rebase --continue
   ```

4. **Subir el commit ya resuelto:**
   ```bash
   git push origin main
   ```

Seguir esta rutina evita que GitHub cree ramas adicionales y garantiza que todo
el trabajo quede en `main`. Si aparece nuevamente el aviso de conflictos en el
pull request, repite el proceso anterior para que el historial quede limpio.
