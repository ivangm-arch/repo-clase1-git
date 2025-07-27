
# 🧪 Ejercicio 09: Deshacer cambios con `git reset`

Este ejercicio práctico te ayudará a entender cómo funciona `git reset` en sus tres modos más comunes: `--soft`, `--mixed` y `--hard`. Verás cómo afectan al staging area (index) y al directorio de trabajo.

---

## 🎯 Objetivo

- Comprender las diferencias entre `git reset --soft`, `--mixed` y `--hard`.
- Aprender a deshacer commits de manera segura o destructiva según la situación.
- Ver en qué casos se conserva o se borra el trabajo hecho.

---

## 🔟 Pasos

---
### 1.  Crear primer commit
```bash copy
echo "Línea 1" > archivo.txt
git add archivo.txt
git commit -m "Commit 1: Añadir línea 1"
```

### 2.  Añadir más contenido y hacer segundo commit
```bash copy
echo "Línea 2" >> archivo.txt
git add archivo.txt
git commit -m "Commit 2: Añadir línea 2"
```
### 3.  Añadir otra línea y hacer tercer commit
```bash copy
echo "Línea 3" >> archivo.txt
git add archivo.txt
git commit -m "Commit 3: Añadir línea 3"
```
### 4.  Añadir ultima linea y hacer commit
```bash copy
echo "Ultima linea" >> archivo.txt
git add archivo.txt
git commit -m "Commit 4: Ultima linea"
```
### 5.  Añadir ultima linea y hacer commit
```bash copy
git log --oneline
```
Debería verse algo así
```
c3 Commit 4: Ultima linea
c3 Commit 3: Añadir línea 3
c2 Commit 2: Añadir línea 2
c1 Commit 1: Añadir línea 1
```
### 6.  Reset suave (`--soft`)
Esto **deshace el commit**, pero mantiene los cambios en el staging area (preparados para volver a commitear).
```bash copy
git reset --soft HEAD~1
```
verifica el estado
```bash copy
git status
```
### 7.  Reset mixto (`--mixed`, por defecto)
Esto **deshace el commit y saca los cambios del staging**, pero **no borra los cambios del archivo**.
```bash copy
git reset --mixed HEAD~1
```
verifica el estado
```bash copy
git status
```
### 8.  Reset duro (`--hard`)
Esto **borra el commit y borra los cambios del archivo**. Es destructivo.
```bash copy
git reset --hard HEAD~1
```
### 9.  Verifica el estado 
Verifica el estado 
```bash copy
git status
```
### 10.  verifica el fichero
Verifica el estado 
```bash copy
cat archivo.txt
```
# 📌 Resumen de modos de `git reset`

| Modo       | Comando                        | Cambios en el historial | Cambios en el staging (`git add`) | Cambios en el working directory | ¿Peligroso? |
|------------|--------------------------------|--------------------------|------------------------------------|-------------------------------|-------------|
| `--soft`   | `git reset --soft HEAD~1`      | ✅ Se eliminan los commits | ✅ Se conservan                   | ✅ Se conservan               | ❌ No        |
| `--mixed`  | `git reset --mixed HEAD~1`     | ✅ Se eliminan los commits | ❌ Se eliminan del staging        | ✅ Se conservan               | ❌ No        |
| `--hard`   | `git reset --hard HEAD~1`      | ✅ Se eliminan los commits | ❌ Se eliminan                    | ❌ Se eliminan                | ✅ Sí        |


