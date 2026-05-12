# 07. Rebase de ramas

## Objetivo

Comprender cómo funciona `git rebase` y en qué se diferencia de `git merge`.

`git rebase` reaplica los commits de una rama sobre otra base, creando una historia más lineal.

---

## Advertencia importante

`git rebase` reescribe historial.

Regla práctica:

> No hagas rebase de ramas compartidas con otras personas salvo que el equipo lo haya acordado.

Es adecuado para limpiar una rama local antes de abrir una Pull Request.

---

## Merge vs Rebase

| Característica | `git merge` | `git rebase` |
|---|---|---|
| Conserva la historia real | Sí | No exactamente |
| Crea commit de merge | A veces | No |
| Reescribe commits | No | Sí |
| Historial lineal | No siempre | Sí |
| Riesgo en ramas compartidas | Bajo | Alto |

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
git switch -c feature/rebase-demo
```

---

### 3. Crea dos commits en la rama

```bash
echo "Línea feature 1" > rebase-demo.txt
git add rebase-demo.txt
git commit -m "Añade primera línea en feature"

echo "Línea feature 2" >> rebase-demo.txt
git add rebase-demo.txt
git commit -m "Añade segunda línea en feature"
```

---

### 4. Vuelve a main

```bash
git switch main
```

---

### 5. Crea un commit nuevo en main

```bash
echo "Cambio nuevo en main" > main-rebase.txt
git add main-rebase.txt
git commit -m "Añade cambio nuevo en main"
```

---

### 6. Observa la divergencia

```bash
git log --oneline --graph --all
```

---

### 7. Vuelve a la rama feature

```bash
git switch feature/rebase-demo
```

---

### 8. Reaplica la rama sobre main

```bash
git rebase main
```

Si aparecen conflictos:

1. Edita los archivos afectados.
2. Añade los archivos resueltos.
3. Continúa el rebase.

```bash
git add <archivo>
git rebase --continue
```

Para cancelar el rebase:

```bash
git rebase --abort
```

---

### 9. Visualiza el historial final

```bash
git log --oneline --graph --all
```

Responde:

- ¿La historia parece más lineal?
- ¿Los commits de la rama tienen nuevos hashes?

---

### 10. Fusiona en main con Fast-Forward

```bash
git switch main
git merge feature/rebase-demo
```

---

## Reto adicional

Repite este ejercicio usando `git merge` en vez de `git rebase` y compara los historiales.

---

## Comandos usados

```bash
git rebase main
git rebase --continue
git rebase --abort
git merge <rama>
git log --oneline --graph --all
```
