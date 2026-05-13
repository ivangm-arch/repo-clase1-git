# 03. Trabajo con ramas

## Objetivo

Aprender a crear ramas, cambiar entre ellas y observar cómo evoluciona el historial.

Una rama en Git no es una copia completa del proyecto. Es un puntero a un commit.

---

## Conceptos clave

- `main` suele ser la rama principal.
- Una rama permite trabajar de forma aislada.
- `HEAD` indica dónde estás trabajando ahora.
- `git switch` permite cambiar de rama.
- `git switch -c` crea una rama y cambia a ella.

---

## Tarea guiada

### 1. Consulta las ramas actuales

```bash
git branch
```

Responde:

- ¿Qué rama aparece marcada con `*`?

---

### 2. Crea una rama nueva

```bash
git switch -c feature/saludo
```

---

### 3. Crea un archivo en la nueva rama

```bash
echo "Trabajo en la rama feature/saludo" > saludo-rama.txt
```

---

### 4. Crea un commit en la rama

```bash
git add saludo-rama.txt
git commit -m "Añade saludo en rama feature"
```

---

### 5. Visualiza el historial

```bash
git log --oneline --graph --all
```

Responde:

- ¿Dónde está la rama `feature/saludo`?

---

### 6. Vuelve a la rama principal

```bash
git switch main
```

Si tu rama principal se llama `master`, usa:

```bash
git switch master
```

---

### 7. Comprueba los archivos

```bash
ls
```

Responde:

- ¿Ves `saludo-rama.txt`?
- ¿Por qué?

---

### 8. Crea un commit diferente en main

```bash
echo "Cambio realizado en main" > cambio-main.txt
git add cambio-main.txt
git commit -m "Añade cambio en main"
```

---

### 9. Visualiza la divergencia

```bash
git log --oneline --graph --all
```

Responde:

- ¿Las ramas tienen el mismo último commit?
- ¿Qué significa que el historial se bifurque?

---

## Reto adicional

Crea otra rama llamada `feature/notas`, añade un archivo `notas-rama.txt`, crea un commit y vuelve a `main`.

Comprueba el resultado con:

```bash
git log --oneline --graph --all
```

---

## Comandos usados

```bash
git branch
git switch <rama>
git switch -c <rama>
git log --oneline --graph --all
git add <archivo>
git commit -m "Mensaje"
```
