
# 07. Rebase una rama

Este ejercicio muestra cómo funciona `git rebase`, comparado con `merge`, y cómo mantener un historial de commits más lineal. También incluye un conflicto simple durante el rebase.


- Usar `git rebase` para aplicar commits de una rama sobre otra.
- Comparar `git rebase` con `git merge`.
- Resolver un conflicto durante el rebase.


## La tarea
1. Crear commit base en main
```bash copy
echo "Línea 1" > archivo.txt
git add archivo.txt
git commit -m "Commit 1: Línea inicial"
```
2. Crear rama `feature` y hacer dos commits
```bash copy
git checkout -b feature

echo "Línea 2 (feature)" >> archivo.txt
git commit -am "Commit 2: Línea 2 desde feature"

echo "Línea 3 (feature)" >> archivo.txt
git commit -am "Commit 3: Línea 3 desde feature"
```
3. Volver a `main` y hacer un cambio
```bash copy
git checkout main

echo "Línea 2 (main)" >> archivo.txt
git commit -am "Commit 4: Línea 2 desde main"
```
4. Mostrar historial antes del rebase
```bash copy
git log --oneline --graph --all
```
Deberías ver algo como esto
```
* 76e9ae0 (HEAD -> main) Commit 4: Línea 2 desde main
| * e0db584 (feature) Commit 3: Línea 3 desde feature
| * 0665459 Commit 2: Línea 2 desde feature
|/
* 3d4de1f Commit 1: Línea inicial
* bfa5844 (origin/main, origin/HEAD) Update README.md
*   5791047 Merge branch 'main' of https://github.com/ivangm-arch/repo-base-clase1
```
5. Hacer `rebase` de la rama `feature` sobre `main`
```bash copy
git checkout feature
git rebase main
```
Si hay conflictos Git lo mostrará
```bash
CONFLICT (content): Merge conflict in archivo.txt
```

6. Abre `archivo.txt` y resuelve el conflicto (por ejemplo, uniendo ambos cambios).
```text copy
Línea 1
Línea 2 (main)
Línea 2 (feature)
Línea 3 (feature)
```
7. Después de resolver, confirma los cambios
```bash copy
git add archivo.txt
git rebase --continue
```
8. Revisa el log
```bash copy
git log --oneline --graph --all
```
Ahora el historial será más lineal, como si los commits de `feature` se hubieran creado después del último commit de `main`



## Comandos útiles
- `git branch`
- `git rebase`
- `git checkout -b`
- `git merge`
- `git status`
- `git mergetool --tool=emerge`
- `git mergetool --tool=vimdiff`
- `git add`
- `git commit`

## 📊 Comparación: Merge vs Rebase

| Característica                     | `git merge`                                          | `git rebase`                                          |
|-----------------------------------|------------------------------------------------------|-------------------------------------------------------|
| Historial                         | Crea un commit de merge y mantiene ramas separadas  | Reescribe el historial para que parezca lineal       |
| Commits nuevos                    | No cambia los commits existentes                     | Reaplica los commits sobre la nueva base              |
| Claridad del historial            | Puede volverse complejo con muchas ramas             | Más limpio y fácil de seguir                         |
| Conflictos                        | Puede haber conflictos al fusionar                   | También puede haber conflictos en cada commit reaplicado |
| Uso recomendado                   | En proyectos colaborativos donde importa conservar la historia real | Para limpieza de historial antes de subir una feature branch |
| Riesgo de sobrescribir historia   | Bajo                                                  | Alto si se hace en ramas compartidas                 |
| Commit extra                      | Sí, crea un commit de merge                          | No, solo reescribe los commits existentes             |

