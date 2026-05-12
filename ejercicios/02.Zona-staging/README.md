# 02. Área de staging

## Objetivo

Comprender cómo Git separa los cambios en tres zonas:

```text
Directorio de trabajo -> Área de staging -> Historial de commits
```

Este ejercicio es importante porque permite ver que un mismo archivo puede tener:

- cambios preparados para commit,
- cambios todavía sin preparar,
- y una versión anterior guardada en el último commit.

---

## Conceptos clave

- `git diff` muestra cambios en el directorio de trabajo que todavía no están en staging.
- `git diff --staged` muestra cambios que ya están preparados para el próximo commit.
- `git restore <archivo>` descarta cambios no preparados.
- `git restore --staged <archivo>` saca cambios del staging sin borrar el contenido del archivo.


---

## Diferencia entre `git add .` y `git add *`

Ambos comandos sirven para añadir cambios al área de staging, pero no son equivalentes.

### `git add .`

Añade al staging los cambios dentro del directorio actual y sus subdirectorios. Incluye:

- archivos nuevos,
- archivos modificados,
- archivos eliminados,
- archivos ocultos si están dentro del directorio actual, por ejemplo `.gitignore`.

Ejemplo recomendado:

```bash
git add .
```

### `git add *`

El asterisco `*` lo interpreta normalmente la shell antes de que Git reciba el comando. Por eso su comportamiento puede variar según el terminal. En general:

- añade archivos y carpetas visibles del directorio actual,
- no añade archivos ocultos como `.gitignore`,
- puede no detectar eliminaciones de archivos que ya no existen en el directorio,
- es menos predecible para principiantes.

Ejemplo:

```bash
git add *
```

### Recomendación para el curso

Usa preferentemente:

```bash
git add .
```

Y, si quieres añadir absolutamente todos los cambios del repositorio desde cualquier subdirectorio, usa:

```bash
git add -A
```

Resumen:

| Comando | Qué añade | Recomendación |
|---|---|---|
| `git add .` | Cambios desde el directorio actual hacia abajo | Recomendado para clase |
| `git add *` | Lo que expande la shell con `*` | Evitar en principiantes |
| `git add -A` | Todos los cambios del repositorio | Útil para proyectos reales |

---

## Tarea guiada

### 1. Prepara un archivo de trabajo

Este ejercicio necesita un archivo ya versionado por Git. Créalo con un primer commit:

```bash
echo "Línea 1" > staging-demo.txt
git add staging-demo.txt
git commit -m "Prepara archivo para practicar staging"
```

---

### 2. Revisa el archivo inicial

```bash
cat staging-demo.txt
```

Si estás en Windows PowerShell:

```powershell
Get-Content staging-demo.txt
```

---

### 3. Sobrescribe el archivo

```bash
echo "Línea 2" > staging-demo.txt
```

---

### 4. Comprueba diferencias sin preparar

```bash
git diff
```

Responde:

- ¿Qué cambio detecta Git?

---

### 5. Comprueba diferencias preparadas

```bash
git diff --staged
```

Responde:

- ¿Por qué no aparece nada?

---

### 6. Añade el archivo al staging

```bash
git add staging-demo.txt
```

---

### 7. Compara de nuevo

```bash
git diff
git diff --staged
```

Responde:

- ¿Dónde aparece ahora el cambio?

---

### 8. Modifica otra vez el mismo archivo

```bash
echo "Línea 3" >> staging-demo.txt
```

---

### 9. Comprueba los dos tipos de diferencias

```bash
git diff
git diff --staged
```

Responde:

- ¿Por qué hay cambios en ambos comandos?
- ¿Qué parte está preparada para commit?
- ¿Qué parte sigue solo en el directorio de trabajo?

---

### 10. Saca el archivo del staging

```bash
git restore --staged staging-demo.txt
```

Comprueba:

```bash
git status
git diff
git diff --staged
```

---

### 11. Descarta los cambios no confirmados

```bash
git restore staging-demo.txt
```

Comprueba:

```bash
git status
cat staging-demo.txt
```

---

## Reto adicional

Haz un cambio en `staging-demo.txt`, añádelo al staging, modifica otra vez el mismo archivo y crea un commit solo con la primera modificación.

Pista:

```bash
git add staging-demo.txt
git commit -m "Guarda primera modificación"
```

Después comprueba si queda algún cambio pendiente:

```bash
git status
```

---

## Comandos usados

```bash
git status
git diff
git diff --staged
git add <archivo>
git restore <archivo>
git restore --staged <archivo>
git commit -m "Mensaje"
```
