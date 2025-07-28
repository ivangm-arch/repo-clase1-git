
# 02. Trabajo con el área de staging

Este ejercicio examinará el área de preparación de git.

En git estamos trabajando con tres áreas diferentes:

1. El directorio de trabajo donde está realizando sus cambios.
2. El área de preparación donde permanecerán todos los cambios que haya agregado a través de `git add`
3. El repositorio donde termina cada confirmación, haciendo tu historial. Para poner sus cambios preparados aquí, emita el comando `git commit`.

Un archivo puede tener cambios tanto en el directorio de trabajo como en el área de preparación al mismo tiempo.
Estos cambios no tienen por qué ser los mismos.

También trabajaremos con `git restore` para restaurar los cambios preparados de un archivo y `git checkout` para devolver un archivo a un estado anterior.

## La tarea

Vives en tu propio repositorio. Hay un archivo llamado `file.txt`.

1. ¿Cuál es el contenido de `file.txt`?
2. Sobrescriba el contenido en `file.txt`: `echo 2 > file.txt` para cambiar el estado de su archivo en el directorio de trabajo
3. ¿Qué te dice "git diff"?
4. ¿Qué te dice `git diff --staged`? ¿Por qué está esto en blanco?
5. Ejecute `git add file.txt` para preparar sus cambios desde el directorio de trabajo.
6. ¿Qué te dice `git diff`?
7. ¿Qué te dice `git diff --staged`?
8. Sobrescriba el contenido en `file.txt`: `echo 3 > file.txt` para cambiar el estado de su archivo en el directorio de trabajo.
9. ¿Qué te dice `git diff`?
10. ¿Qué te dice `git diff --staged`?
11. Explica lo que está pasando
12. Ejecute `git status` y observe que `file.txt` está presente dos veces en la salida.
13. Ejecute `git restore --staged file.txt` para cancelar el cambio
14. ¿Qué te dice ahora "git status"?
15. Materializa el cambio haciendo un commit.
16. ¿Cómo se ve el registro?
17. Sobrescriba el contenido en `file.txt`: `echo 4 > file.txt` 
18. ¿Cuál es el contenido de `file.txt`?
19. ¿Qué nos dice "git status"?
20. Ejecute `git restore file.txt`
21. ¿Cuál es el contenido de `file.txt`?
22. ¿Qué nos dice "git status"?

## Comandos útiles

- `git add`
- `git commit`
- `git commit -m "Mi mensaje de confirmación breve y perezoso"`
- `git log`
- `git log -n 5`
- `git log --oneline`
- `git log --oneline --graph`
- `git restore --staged`

## Alias

Puede configurar alias, que pueden ser útiles para ahorrar tiempo al escribir comandos largos.
`git config --global alias.lol 'log --oneline --graph --all'`
