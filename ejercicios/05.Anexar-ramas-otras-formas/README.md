# 05. Merge con commit de fusión

## Objetivo

Entender qué ocurre cuando dos ramas han avanzado de forma independiente y Git no puede hacer Fast-Forward.

En ese caso, Git crea un commit de merge para unir ambas líneas de trabajo.

---

## Conceptos clave

- **Fast-Forward**: Git solo mueve el puntero de la rama.
- **Merge commit**: Git crea un nuevo commit que une dos historiales.
- **Historia divergente**: dos ramas tienen commits diferentes desde un punto común.

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

### 2. Crea una rama nueva

```bash
git switch -c feature/greeting
```

---

### 3. Crea un commit en la rama

```bash
echo "Hola desde feature/greeting" > greeting.txt
git add greeting.txt
git commit -m "Añade saludo desde rama feature"
```

---

### 4. Vuelve a main

```bash
git switch main
```

---

### 5. Crea un commit diferente en main

```bash
echo "Cambio independiente en main" > main-change.txt
git add main-change.txt
git commit -m "Añade cambio independiente en main"
```

---

### 6. Visualiza la divergencia

```bash
git log --oneline --graph --all
```

Responde:

- ¿Ves dos líneas de historial?
- ¿Qué commit tienen en común ambas ramas?

---

### 7. Fusiona la rama feature

```bash
git merge feature/greeting
```

Si Git abre un editor para el mensaje del merge, guarda y cierra el editor.

---

### 8. Comprueba el historial

```bash
git log --oneline --graph --all
```

Responde:

- ¿Aparece un commit de merge?
- ¿En qué se diferencia de un Fast-Forward?

---

## Reto adicional

Repite el ejercicio con otra rama, pero fuerza que Git cree un commit de merge incluso cuando podría hacer Fast-Forward:

```bash
git merge --no-ff nombre-de-la-rama
```

---

## Comandos usados

```bash
git switch -c <rama>
git switch <rama>
git merge <rama>
git merge --no-ff <rama>
git log --oneline --graph --all
```
