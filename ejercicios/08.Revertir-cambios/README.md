
# 🧪 Ejercicio 08: Revertir cambios con `git revert`

Este ejercicio te guía paso a paso para aprender a usar el comando `git revert`, el cual permite **deshacer un commit** creando uno nuevo que revierte los cambios, **sin modificar el historial existente**.

---

## 🎯 Objetivo

- Practicar cómo revertir uno o varios commits.
- Ver el efecto de `git revert` en el historial.
- Comparar con `git reset` (pero sin alterar historial).

---

## 🔟 Pasos

### 1.  Crear primer commit
```bash copy
echo "Línea 1" > archivo.txt
git add archivo.txt
git commit -m "Commit 1: Añadir línea 1"
```

### 2.  Añadir segundo commit
```bash copy
echo "Línea 2" >> archivo.txt
git commit -am "Commit 2: Añadir línea 2"
```
### 3.  Añadir tercer commit
```bash copy
echo "Línea 3" >> archivo.txt
git commit -am "Commit 3: Añadir línea 3"
```
### 4. Ver historial de commits
```bash copy
git log --oneline
```
Deberías ver algo así
```
c3 Commit 3: Añadir línea 3
c2 Commit 2: Añadir línea 2
c1 Commit 1: Añadir línea 1
```
### 5.  Ver contenido actual del archivo
```bash copy
cat archivo.txt
```
Resultado esperado
```
Línea 1
Línea 2
Línea 3
```
### 6.  Revertir el último commit (`HEAD`)
```bash copy
git revert HEAD
```
### 7.  Ver historial después del revert
```bash copy
git log --oneline
```
Deberías ver algo así
``` 
c4 Revert "Commit 3: Añadir línea 3"
c3 Commit 3: Añadir línea 3
c2 Commit 2: Añadir línea 2
c1 Commit 1: Añadir línea 1
```
### 8.  Ver contenido del archivo después del revert
```bash copy
cat archivo.txt
```
Resultado esperado
```
Línea 1
Línea 2
```
### 9.  Revertir múltiples commits
```bash copy
echo "Línea 4" >> archivo.txt
git commit -am "Commit 4: Añadir línea 4"

echo "Línea 5" >> archivo.txt
git commit -am "Commit 5: Añadir línea 5"
```
Revertir los 2 últimos commits
```bash copy
git revert HEAD~2..HEAD
```

### 10.  Ver contenido del archivo después del revert múltiple
```bash copy
cat archivo.txt
```

# 📌 Resumen de comandos

| Acción                        | Comando                           | Descripción                                                                 |
|------------------------------|------------------------------------|------------------------------------------------------------------------------|
| Revertir el último commit    | `git revert HEAD`                 | Crea un nuevo commit que revierte los cambios del último commit             |
| Revertir un commit por hash  | `git revert <hash>`               | Reviertes un commit específico (puedes obtener el hash con `git log`)       |
| Revertir varios commits      | `git revert A..B`                 | Reviertes varios commits en orden inverso (de B hacia A, sin incluir A)     |
| Ver historial simple         | `git log --oneline`               | Muestra los commits de forma resumida en una línea                          |
| Ver historial con gráfico    | `git log --graph --oneline --all` | Muestra el historial visualmente, útil para ver ramas y merges              |
| Ver contenido de un archivo  | `cat archivo.txt`                 | Muestra el contenido actual del archivo desde la línea de comandos          |




