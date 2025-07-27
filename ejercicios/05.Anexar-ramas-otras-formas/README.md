
# 05. Mergear ramas otras formas

## La tarea

Nuevamente estas en tu propia rama, esta vez haremos un poco de malabarismo con las ramas para mostrar cuán livianas son las ramas en git.

1. Crear una rama de nombre `greeting` y pasate a ella
2. Edita `greeting.txt` para indicar tu saludo favorito
3. Agrega `greeting.txt` al area de staging
4. Realiza el commit
5. Vuelve a la rama `main`
6. Crea un fichero `README.md` con información sobre el repositorio. Un par de lineas
7. Agrega el fichero `README.md` al area de staging y realiza el commit
8. Cual es la salida del comando `git log --oneline --graph --all`?
9. Haz la diferencia entre ambas ramas
10. Anexa la rama `greeting` en la rama `main`
11. Cual es la salida del comando `git log --oneline --graph --all` ahora? Observa la diferencia, ahora existe un **commit extra** con el nombre "Merge branch 'greeting'"

## Comandos útiles

- `git branch`
- `git branch <branch-name>`
- `git branch -d <branch-name>`
- `git switch <branch-name>`
- `git switch -c <branch-name>`
- `git branch -v`
- `git add`
- `git commit`
- `git commit -m`
- `git merge <branchA> <branchB>`
- `git diff <branchA> <branchB>`
- `git log --oneline --graph --all`
