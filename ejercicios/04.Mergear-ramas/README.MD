# 04. Merge Fast-Forward

## Objetivo

Comprender cómo funciona un merge Fast-Forward.

Un merge Fast-Forward ocurre cuando la rama destino no tiene commits nuevos desde que se creó la rama que vamos a fusionar.

En este caso Git no necesita crear un commit de merge. Solo mueve el puntero de la rama destino hacia adelante.

---

## Situación inicial

Queremos hacer un cambio en una rama y fusionarlo después en `main`.

```text
main
  \
   feature/mayusculas
```

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

### 2. Crea una rama de trabajo

```bash
git switch -c feature/mayusculas
```

---

### 3. Crea o modifica un archivo

```bash
echo "hola mundo" > hello_world.txt
```

---

### 4. Crea un commit en la rama

```bash
git add hello_world.txt
git commit -m "Añade saludo en minúsculas"
```

---

### 5. Cambia el texto a mayúsculas

```bash
echo "HOLA MUNDO" > hello_world.txt
git add hello_world.txt
git commit -m "Convierte saludo a mayúsculas"
```

---

### 6. Visualiza el historial

```bash
git log --oneline --graph --all
```

---

### 7. Vuelve a main

```bash
git switch main
```

---

### 8. Fusiona la rama

```bash
git merge feature/mayusculas
```

---

### 9. Comprueba el resultado

```bash
git log --oneline --graph --all
cat hello_world.txt
```

Responde:

- ¿Se ha creado un commit de merge?
- ¿Por qué Git pudo hacer Fast-Forward?

---

## Reto adicional

Elimina la rama ya fusionada:

```bash
git branch -d feature/mayusculas
```

Comprueba el historial:

```bash
git log --oneline --graph --all
```

---

## Comandos usados

```bash
git switch -c <rama>
git switch <rama>
git merge <rama>
git branch -d <rama>
git log --oneline --graph --all
```
