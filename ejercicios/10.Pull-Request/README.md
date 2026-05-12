# 10. Pull Request en GitHub

## Objetivo

Crear una Pull Request en GitHub para entender el flujo básico de colaboración.

Una Pull Request no es un comando de Git. Es una funcionalidad de GitHub para revisar y fusionar cambios entre ramas.

---

## Conceptos clave

Una Pull Request permite:

- revisar cambios antes de integrarlos,
- dejar comentarios,
- pedir modificaciones,
- ejecutar validaciones automáticas,
- fusionar una rama en otra.

Flujo habitual:

```text
crear rama -> hacer commits -> push -> abrir Pull Request -> revisar -> merge
```

---

## Tarea guiada

### 1. Actualiza tu rama principal

```bash
git switch main
git pull
```

Si tu rama principal se llama `master`, usa:

```bash
git switch master
git pull
```

---

### 2. Crea una rama de trabajo

```bash
git switch -c mejora-texto
```

---

### 3. Haz un cambio pequeño

Puedes modificar `dir1/README.md`:

```bash
echo "Cambio propuesto desde una Pull Request." >> dir1/README.md
```

---

### 4. Revisa el cambio

```bash
git status
git diff
```

---

### 5. Crea un commit

```bash
git add dir1/README.md
git commit -m "Actualiza texto de ejemplo para Pull Request"
```

---

### 6. Sube la rama a GitHub

```bash
git push -u origin mejora-texto
```

---

### 7. Crea la Pull Request en GitHub

1. Abre el repositorio en GitHub.
2. Pulsa **Compare & pull request**.
3. Revisa la rama origen y la rama destino.
4. Añade un título descriptivo.
5. Añade una descripción breve.
6. Pulsa **Create pull request**.

Título recomendado:

```text
Actualiza texto de ejemplo para Pull Request
```

Descripción recomendada:

```text
## Cambios

- Actualiza el fichero dir1/README.md con una línea de prueba.

## Motivo

- Practicar el flujo de Pull Request en GitHub.
```

---

### 8. Revisa la Pull Request

En la PR, revisa:

- pestaña **Files changed**,
- comentarios,
- estado de validaciones,
- conversación de la PR.

Si estás trabajando con compañeros, pide que alguien revise la PR antes de fusionarla.

---

### 9. Fusiona la Pull Request

Cuando todo esté correcto:

1. Pulsa **Merge pull request**.
2. Pulsa **Confirm merge**.
3. Opcionalmente, elimina la rama remota desde GitHub con **Delete branch**.

---

### 10. Actualiza tu repositorio local

```bash
git switch main
git pull
```

Si usas `master`:

```bash
git switch master
git pull
```

---

### 11. Elimina la rama local

```bash
git branch -d mejora-texto
```

---

## Reto adicional

Abre una Pull Request con un compañero:

1. Una persona crea una rama y sube un cambio.
2. La otra persona revisa la PR y deja un comentario.
3. La primera persona aplica la mejora solicitada.
4. Se fusiona la PR después de la revisión.

---

## Comandos usados

```bash
git switch main
git pull
git switch -c mejora-texto
git status
git diff
git add dir1/README.md
git commit -m "Actualiza texto de ejemplo para Pull Request"
git push -u origin mejora-texto
git branch -d mejora-texto
```
