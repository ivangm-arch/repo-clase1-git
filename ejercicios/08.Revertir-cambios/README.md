# 08. Revertir cambios con git revert

## Objetivo

Aprender a deshacer cambios con `git revert`.

`git revert` no borra historial. Crea un commit nuevo que deshace los cambios introducidos por otro commit.

Esto lo hace más seguro que `git reset` para commits que ya han sido compartidos con otras personas.

---

## Conceptos clave

- `git revert HEAD` revierte el último commit.
- `git revert <hash>` revierte un commit concreto.
- `git revert --no-edit <hash>` crea el commit de reversión sin abrir el editor.
- `git revert` es seguro para ramas compartidas porque no reescribe historial.

---

## Tarea guiada

### 1. Crea un primer commit

```bash
echo "Línea 1" > archivo-revert.txt
git add archivo-revert.txt
git commit -m "Commit 1: añade línea 1"
```

---

### 2. Añade un segundo commit

```bash
echo "Línea 2" >> archivo-revert.txt
git add archivo-revert.txt
git commit -m "Commit 2: añade línea 2"
```

---

### 3. Añade un tercer commit

```bash
echo "Línea 3" >> archivo-revert.txt
git add archivo-revert.txt
git commit -m "Commit 3: añade línea 3"
```

---

### 4. Revisa el historial

```bash
git log --oneline
```

Deberías ver algo parecido a:

```text
abc1234 Commit 3: añade línea 3
def5678 Commit 2: añade línea 2
ghi9012 Commit 1: añade línea 1
```

---

### 5. Revisa el contenido actual

```bash
cat archivo-revert.txt
```

Resultado esperado:

```text
Línea 1
Línea 2
Línea 3
```

---

### 6. Revierte el último commit

```bash
git revert --no-edit HEAD
```

---

### 7. Revisa el historial después del revert

```bash
git log --oneline
```

Ahora deberías ver un commit nuevo de tipo `Revert`.

---

### 8. Revisa el contenido del archivo

```bash
cat archivo-revert.txt
```

Resultado esperado:

```text
Línea 1
Línea 2
```

---

### 9. Crea dos commits más

```bash
echo "Línea 4" >> archivo-revert.txt
git add archivo-revert.txt
git commit -m "Commit 4: añade línea 4"

echo "Línea 5" >> archivo-revert.txt
git add archivo-revert.txt
git commit -m "Commit 5: añade línea 5"
```

---

### 10. Revierte los dos últimos commits

```bash
git revert --no-edit HEAD~2..HEAD
```

---

### 11. Comprueba el resultado

```bash
git log --oneline
cat archivo-revert.txt
```

---

## Reto adicional

Usa `git log --oneline` para copiar el hash de un commit concreto y reviértelo con:

```bash
git revert --no-edit <hash>
```

---

## Resumen

| Acción | Comando |
|---|---|
| Revertir último commit | `git revert HEAD` |
| Revertir sin abrir editor | `git revert --no-edit HEAD` |
| Revertir commit concreto | `git revert <hash>` |
| Revertir rango de commits | `git revert A..B` |
| Ver historial | `git log --oneline` |
