# 01. Commits primeros pasos

Este kata le presentará los comandos `git add` y `git commit`.
Este es un kata muy introductorio. Si ha utilizado `git status`, `git log --oneline --graph`, `git add` y `git commit` de manera extensiva, probablemente debería omitirlo.
Puede consultar la parte inferior de este archivo si aún no ha realizado la configuración básica de git.


## Configuración:

1. Run `source setup.sh`

## The task

0. Usa `git status` revisar en cual rama estas.
1. Utilice `git status` para ver en qué rama se encuentra.
2. ¿Cómo se ve "git log"?
3. Crea un archivo
4. ¿Cómo se ve ahora el resultado de "git status"?
5. `add` el archivo al área de preparación
6. ¿Cómo se ve ahora el "estado de git"?
7. `commit` el archivo en el repositorio
8. ¿Cómo se ve ahora "git status"?
9. Cambie el contenido del archivo que creó anteriormente.
10. ¿Cómo se ve ahora el "estado de git"?
11. `add` el cambio de archivo
12. ¿Cómo se ve ahora el "estado de git"?
13. Cambia el archivo nuevamente.
14. Haz un "commit"
15. ¿Cómo es el "estado" ahora? ¿El "registro"?



## Comandos útiles
- `git add`
- `git commit`
- `git commit -m "My commit message"`
- `git log`
- `git log -n 5`
- `git log --oneline`
- `git log --oneline --graph`
- `touch filename` (para crear un fichero)


## Configuración inicial de Git
1. `git config --global user.name "username"`
2. `git config --global user.email "username@example.com`

Otras opciones de edición:
- `git config --global core.editor "code --wait"`
- `git config --global core.editor "'C:/Program Files/Notepad++/notepad++.exe' -multiInst"` (windows)
