# 06. Resolver conflictos

## Objetivo

Aprender cómo se produce un conflicto y cómo resolverlo sin perder cambios.

Un conflicto ocurre cuando Git no puede decidir automáticamente qué versión de un archivo debe conservar.

---

## Conceptos clave

Cuando hay conflicto, Git inserta marcas dentro del archivo:

```text
<<<<<<< HEAD
Contenido de la rama actual
=======
Contenido de la rama que estás fusionando
>>>>>>> nombre-rama
```

- `HEAD` representa tu rama actual.
- La parte inferior representa la rama que intentas fusionar.
- Resolver el conflicto consiste en editar el archivo y dejar el contenido final correcto.

---

## Tarea guiada

### 1. Asegúrate de estar en main

```bash
git switch main
```

Si tu rama principal se llama `master`, usa:

```bash
git switch master
```

---

### 2. Crea un archivo base

```bash
echo "Fruta: manzana" > frutas.txt
git add frutas.txt
git commit -m "Añade fruta inicial"
```

---

### 3. Crea una rama nueva

```bash
git switch -c feature/pera
```

---

### 4. Cambia el mismo archivo en la rama

```bash
echo "Fruta: pera" > frutas.txt
git add frutas.txt
git commit -m "Cambia fruta a pera"
```

---

### 5. Vuelve a main

```bash
git switch main
```

---

### 6. Cambia el mismo archivo en main

```bash
echo "Fruta: plátano" > frutas.txt
git add frutas.txt
git commit -m "Cambia fruta a plátano"
```

---

### 7. Intenta fusionar

```bash
git merge feature/pera
```

Git debería informar de un conflicto.

Comprueba el estado:

```bash
git status
```

---

### 8. Abre el archivo conflictivo

```bash
cat frutas.txt
```

Verás marcas parecidas a estas:

```text
<<<<<<< HEAD
Fruta: plátano
=======
Fruta: pera
>>>>>>> feature/pera
```

---

### 9. Resuelve el conflicto

Edita `frutas.txt` y deja el contenido final deseado. Por ejemplo:

```text
Fruta: plátano
Fruta: pera
```

Elimina siempre las marcas:

```text
<<<<<<<
=======
>>>>>>>
```

---

### 10. Finaliza el merge

```bash
git add frutas.txt
git commit
```

También puedes usar un mensaje explícito:

```bash
git commit -m "Resuelve conflicto de frutas"
```

---

### 11. Comprueba el historial

```bash
git log --oneline --graph --all
```

---

## Reto adicional

Provoca otro conflicto en un archivo llamado `colores.txt` usando dos ramas diferentes y resuélvelo dejando ambas aportaciones.

---

## Comandos usados

```bash
git merge <rama>
git status
git add <archivo>
git commit
git log --oneline --graph --all
```
