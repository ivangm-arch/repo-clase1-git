# 09. Deshacer cambios con git reset

## Objetivo

Comprender cómo funciona `git reset` en sus tres modos más comunes:

- `--soft`
- `--mixed`
- `--hard`

Este ejercicio muestra cómo afectan al historial, al área de staging y al directorio de trabajo.

---

## Advertencia importante

`git reset` puede reescribir historial.

Especialmente:

```bash
git reset --hard
```

Este comando puede eliminar cambios del directorio de trabajo. Úsalo con cuidado.

Regla práctica:

> No uses `git reset` sobre commits que ya has compartido con otras personas salvo que sepas exactamente lo que estás haciendo.

---

## Tabla resumen

| Modo | Historial | Staging | Directorio de trabajo | Riesgo |
|---|---|---|---|---|
| `--soft` | Mueve HEAD | Conserva cambios | Conserva cambios | Bajo |
| `--mixed` | Mueve HEAD | Saca cambios del staging | Conserva cambios | Medio |
| `--hard` | Mueve HEAD | Borra staging | Borra cambios | Alto |

---

## Tarea guiada

### 1. Crea un archivo y el primer commit

```bash
echo "Línea 1" > archivo-reset.txt
git add archivo-reset.txt
git commit -m "Commit 1: añade línea 1"
```

---

### 2. Crea un segundo commit

```bash
echo "Línea 2" >> archivo-reset.txt
git add archivo-reset.txt
git commit -m "Commit 2: añade línea 2"
```

---

### 3. Crea un tercer commit

```bash
echo "Línea 3" >> archivo-reset.txt
git add archivo-reset.txt
git commit -m "Commit 3: añade línea 3"
```

---

### 4. Revisa el historial

```bash
git log --oneline
```

---

## Parte A: reset --soft

### 5. Ejecuta reset suave

```bash
git reset --soft HEAD~1
```

---

### 6. Comprueba el estado

```bash
git status
git diff --staged
cat archivo-reset.txt
```

Responde:

- ¿El último commit ha desaparecido del historial?
- ¿El cambio sigue preparado en staging?
- ¿El contenido del archivo se conserva?

---

### 7. Recupera el commit para continuar

```bash
git commit -m "Commit 3: añade línea 3"
```

---

## Parte B: reset --mixed

### 8. Ejecuta reset mixto

```bash
git reset --mixed HEAD~1
```

`--mixed` es el modo por defecto. Este comando equivale a:

```bash
git reset HEAD~1
```

---

### 9. Comprueba el estado

```bash
git status
git diff
cat archivo-reset.txt
```

Responde:

- ¿El cambio sigue en el archivo?
- ¿Está preparado en staging?

---

### 10. Recupera el commit para continuar

```bash
git add archivo-reset.txt
git commit -m "Commit 3: añade línea 3"
```

---

## Parte C: reset --hard

### 11. Ejecuta reset duro

```bash
git reset --hard HEAD~1
```

---

### 12. Comprueba el resultado

```bash
git status
git log --oneline
cat archivo-reset.txt
```

Responde:

- ¿El último commit ha desaparecido?
- ¿La línea 3 sigue en el archivo?
- ¿Por qué este modo es peligroso?

---

## Reto adicional

Haz un cambio en `archivo-reset.txt` sin crear commit y ejecuta:

```bash
git reset --hard
```

Comprueba qué ocurre con el cambio no confirmado.

---

## Comandos usados

```bash
git reset --soft HEAD~1
git reset --mixed HEAD~1
git reset --hard HEAD~1
git status
git diff
git diff --staged
git log --oneline
```
