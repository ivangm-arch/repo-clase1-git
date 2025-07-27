# 04. Mergear ramas tipo Fast-Forward

## La tarea

Nuevamente estas en tu propia rama, esta vez haremos un poco de malabarismo con las ramas para mostrar cuán livianas son las ramas en git.

1. Crear a (feature)branch llamada `feature/uppercase` (si, `feature/uppercase` es un nombre perfectamente válido para una rama y además es una convención común).
2. Pasate a esa nueva rama
3. Cual es la salida de `git status`?
4. Edita el fichero `hello_world.txt` para cambiar el texto a mayúsculas
5. Agrega `hello_world.txt` al staging area y realiza el commit
6. Cual es la salida de `git branch`?
7. Cual es la salida de `git log --oneline --graph --all`

   *Recuerde: desea actualizar la rama maestra para que también tenga todos los cambios actualmente en la rama de features. El comando 'git merge [nombre de rama]' toma una rama como argumento del cual toma cambios. La rama a la que apunta HEAD (rama actual) se actualiza para incluir también estos cambios.*

8. Pasa a la rama `main`
9. Usa comando `cat` para ver el contenido del fichero `hello_world.txt`
10. Muestra la diferencia entre las ramas
11. Anexa los cambios entre las ramas (recuerda estás en la rama master)
12. Usa comando `cat` para ver el contenido del fichero `hello_world.txt`
13. Borra la rama `feature/uppercase`

## Comandos útiles

- `git branch`
- `git branch <branch-name>`
- `git branch -d <branch-name>`
- `git switch`
- `git branch -v`
- `git add`
- `git commit`
- `git commit -m`
- `git merge <branch>`
- `git diff <branchA> <branchB>`
- `git log --oneline --graph --all`

=======

# 04. Mergear ramas tipo Fast-Forward

## La tarea

Nuevamente estas en tu propia rama, esta vez haremos un poco de malabarismo con las ramas para mostrar cuán livianas son las ramas en git.

1. Crear a (feature)branch llamada `feature/uppercase` (si, `feature/uppercase` es un nombre perfectamente válido para una rama y además es una convención común).
2. Pasate a esa nueva rama
3. Cual es la salida de `git status`?
4. Edita el fichero `hello_world.txt` para cambiar el texto a mayúsculas
5. Agrega `hello_world.txt` al staging area y realiza el commit
6. Cual es la salida de `git branch`?
7. Cual es la salida de `git log --oneline --graph --all`

   *Recuerde: desea actualizar la rama maestra para que también tenga todos los cambios actualmente en la rama de features. El comando 'git merge [nombre de rama]' toma una rama como argumento del cual toma cambios. La rama a la que apunta HEAD (rama actual) se actualiza para incluir también estos cambios.*

8. Pasa a la rama `main`
9. Usa comando `cat` para ver el contenido del fichero `hello_world.txt`
10. Muestra la diferencia entre las ramas
11. Anexa los cambios entre las ramas (recuerda estás en la rama master)
12. Usa comando `cat` para ver el contenido del fichero `hello_world.txt`
13. Borra la rama `feature/uppercase`

## Comandos útiles

- `git branch`
- `git branch <branch-name>`
- `git branch -d <branch-name>`
- `git switch`
- `git branch -v`
- `git add`
- `git commit`
- `git commit -m`
- `git merge <branch>`
- `git diff <branchA> <branchB>`
- `git log --oneline --graph --all`
