
# Clase 1 Git Pontia Tech - Ejercicios y ejemplos

## ¿Porqué de estos ejemplos?

En este repositorio encontrareis una serie de ejemplos y ejercicios basicos para comenzar a trabajar con Git.
Los ejercicios están diseñados para aprendizaje de Git, y para practicar el uso de Git.


## Sugerencia de ejercicios

Esta es una lista del orden recomendado para realizar los ejercicios.

- [00. Docs](./docs/github-git-cheat-sheet.pdf)
- [01. Commits](./ejercicios/01.Commit/README.md)
- [02. Zona staging](./ejercicios/02.Zona-staging/README.md)
- [03. Trabajar con ramas](./ejercicios/03.Trabajo-con-ramas/README.md)
- [04. Mergear ramas tipo Fast-Forward](./ejercicios/04.Mergear-ramas/README.MD)
- [05. Mergear ramas tipo 3-way](./ejercicios/05.Anexar-ramas-otras-formas/README.md)
- [06. Resolver conflictos](./ejercicios/06.Anexar-conflictos/README.md)
- [07. Rebase rama](./ejercicios/07.Rebase-rama/README.md)
- [08. Revertir cambios](./ejercicios/08.Revertir-cambios/README.md)
- [09. Resetear cambios](./ejercicios/09.Reset/README.md)
- [10. Pull Request](./ejercicios/10.Pull-Request/README.md)


## Chuleta de comandos

Una colección de comandos útiles para usar en todos los ejercicios y en el día a día:

```shell
# Inicializar un vacio repositorio.
git init            # Inicializa una vacio repositorio en el actual directorio.

# Clonar repositorio
git clone https://github.com/ivangm-arch/repo-clase1-git.git     # Clone el repositorio url y crea un directorio con el repo del repositorio

# Git (usuario and repositorio nivel) configuraciones
git config --local user.name "Repo-level Username"            # Establece el nombre de usuario por defecto a nivel repo git.
git config --local user.email "Repo-level.Email@Example.com"  # Establece el email de usuario por defecto a nivel repo git.
                                                              # --global -> Establece el parametro a nivel usuario <user-home>/.gitconfig for ej. ~/.gitconfig
                                                              # --local -> Establece el parametro a nivel repositorio .git/config


# Ver cambios en local
git status                  # Muestra el estado del directorio-trabajo
git diff                    # Muestra cambios en el actual directorio-trabajo (aún no staged)
git diff --cached           # Muestra cambios actualmente staged para commit

# Agregar ficheros al staging (antes de hacer commit)
git add myfile.txt          # Agregar myfile.txt al stage
git add .                   # Agregar el directorio de trabajo completo al stage

# Hacer commits
git commit                              # Hace un nuevo commit con los cambios en el area de staging. Abrirá el editor para agregar un mensaje.
git commit -m "I love documentation"    # Hace un nuevo commit con los cambios en el area de staging. Usa el mensaje dado.
git commit -a                           # Hace un nuevo commit y automaticamente agregar los cmabios para todos los ficheros conocidos por git
git commit -am "I still do!"            # Una combinación de las 2 opciones anteriores
git commit --amend                      # Rehace el commit message del previos commit (sino está subido al remoto)
                                        # Nunca cambiar la historia pública
git reset <file>                        # Unstage un fichero agregado al area de staging para dejarlo en el directorio-trabajo sin perder ningún cambio.
git reset --soft [commit_hash]          # Resetea la actual rama. No toca el staging area o el arbol de directorios en nada.
                                        # --hard modo debería descartar todos los cambios.

# Configurando un diferente editor
- `git config --global core.editor nano`

## Para Windows:
- Usando Notepad:
`git config --global core.editor notepad`

- O utilizar Notepad++:
`git config --global core.editor "'C:/Program Files/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"`


# Revisar historial
git log                     # Muestra el historial de commits
git log --oneline           # Formatear commits a una single linea (atajo para --pretty=oneline  --abbrev-commit)
git log --graph             # Mostrar un grafico de los commits y ramas
git log --pretty=fuller     # Ver la historia de los comits de forma detallada con autor y detalles del commit.
git log --follow <file>     # Lista la historia de un fichero más alla de los renombradosrenames
git log branch2..branch1    # Muestra commits alcanzables desde rama1 pero no en la rama2

# Stash
git stash                 # Guarda los cambios en un Stash en la rama actual, lo que permite cambiar a una rama diferente sin arrastrar los cambios.
git stash list            # Lista de stashs.
git stash apply <stash>   # Aplica el stash con nombre <stash>, si no incluimos el nombre aplica el ultimo de la lista.


# Trabajar con ramas (Branches)
git branch my-branch       # Crea una nueva rama my-branch
git switch my-branch       # Cambia a otra rama para trabajar en ella
git switch -c my-branch    # Crea una nueva rama llamada my-branch y cambia a esa rama nueva
git branch -d my-branch    # Elimina la rama my-branch solo si se ha mergeado con otra rama
git branch -D my-branch    # Fuarza la eliminación de la rama, aunque no se haya mergeado con otra rama

# Merging
git merge master         # Hace un merge de la rama master sobre la rama en la que estes trabajando
git rebase master        # Mueve los commits de tu rama actual para reaplicarlos sobre la punta más reciente de la rama master

# Remotes
git remote                   # Muestra tus remote actuales
git remote -v                # Muestra tus remotes actuales y sus URLs
git push                     # Envía tus commits locales de la rama actual al repositorio remoto
git push -u origin my-branch # Envía la rama local my-branch al repositorio remoto llamado origin y establece esa rama remota como la rama por defecto, para que en futuros pushs o pulls puedas usar solo git push o git pull sin especificar la rama from origin.
git pull                     # Descarga los cambios de la rama remota aplicandolos sobre tu rama local

# Mover ficheros bajo version control
git rm <path/to/the/file>                 # Elimina un fichero o directorio y tambien de la zona stage 
git mv <source/file> <destination/file>   # Mueve/renombre un fichero o directorio y lo actualiza de la zona stage

# Aliases - Existe la posibilidad de crear Alias de comandos utilizados con frecuencia

# Añadir un alias "sw" for "switch"
git config --global alias.sw "switch"
# Uso:
git sw master     # Realmente has hecho "git switch master"

## Logging
git log --graph --online --all # Muestra el historial de commits de todas las ramas en un formato compacto y visualmente gráfico
## Añadir un alias llamado "lol" (log oneline..) muestra lo anterior
git config --global alias.lol "log --graph --oneline --all"
## Usando el alias
git lol     # Realmente has hecho "git log --graph --oneline --all"
```
