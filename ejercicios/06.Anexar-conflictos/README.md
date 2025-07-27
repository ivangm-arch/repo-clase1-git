
# 06. Resolver un conflicto de fusión

¡En este ejercicio te enfrentarás a tu primer conflicto de fusión! Habrá dos ramas diferentes:

* `main`
* `feature/pera`

La tarea consiste en observar el conflicto de fusión y resolverlo editando el archivo en consecuencia.
1. Crear un conflicto de merge entre dos ramas.
2. Resolverlo manualmente.
3. Confirmar el merge.


## La tarea
1. Crea un archivo `frutas.txt` y añade como contenido `Manzana`
2. Añade el cambio a la zona staging y realiza un commit
3. Crea una nueva rama `feature/pera` y cámbiate a ella
4. Crea un archivo `frutas.txt` y añade como contenido `Pera`
5. Añade el cambio a la zona staging y realiza un commit
6. Regresa a la rama `main`
7. Crea un archivo `frutas.txt` y añade como contenido `Platano`
8. Añade el cambio a la zona staging y realiza un commit
9. Visualiza las diferencias entre la rama `main` y la rama `feature/pera`
10. Anexa la rama `feature/pera` sobre la rama `main`
11. ¡Acabas de crear tu primer conflicto! Git no sabe si dejar `Platano`o `Pera` porque ambos modificaron la misma linea del mismo fichero.
12.  Visualiza el contenido del fichero `frutas.txt`
13. Edita el fichero `frutas.txt` para dejar el contenido que quieras
14. Añade el cambio a la zona staging y realiza un commit 
15. Revisa la salida del comando `git log --oneline --graph --all`



## Comandos útiles
- `git branch`
- `git checkout -b`
- `git merge`
- `git status`
- `git mergetool --tool=emerge`
- `git mergetool --tool=vimdiff`
- `git add`
- `git commit`
