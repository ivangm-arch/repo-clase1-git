# 07. Rebase de ramas

## Objetivos

En este ejercicio aprenderás a:

- Crear ramas.
- Realizar commits en diferentes ramas.
- Utilizar `git rebase`.
- Resolver conflictos durante un rebase.
- Usar `rebase interactivo`.
- Mantener un historial limpio.

---

# Ejercicio 1 — Rebase básico

## 1. Crear rama principal

```bash
git checkout -b main
```

---

## 2. Crear commit inicial

```bash
echo "Proyecto Git" > README.md

git add .
git commit -m "Commit inicial"
```

---

## 3. Crear rama feature

```bash
git checkout -b feature/login
```

---

## 4. Crear cambios en la rama feature

```bash
echo "Formulario login" > login.txt

git add .
git commit -m "Añadir formulario login"
```

```bash
echo "Validación usuario" >> login.txt

git add .
git commit -m "Añadir validación login"
```

---

## 5. Volver a `main` y añadir cambios

```bash
git checkout main
```

```bash
echo "Configuración global" > config.txt

git add .
git commit -m "Añadir configuración global"
```

---

## 6. Hacer rebase de la rama feature sobre `main`

Cambiar a la rama feature:

```bash
git checkout feature/login
```

Ejecutar el rebase:

```bash
git rebase main
```

---

## 7. Ver el historial

```bash
git log --oneline --graph --all
```

---

# Ejercicio 2 — Rebase con conflictos

## 1. Crear nueva rama

```bash
git checkout main
git checkout -b feature/conflicto
```

---

## 2. Modificar fichero

```bash
echo "Color azul" > estilos.txt

git add .
git commit -m "Color azul"
```

---

## 3. Volver a `main` y modificar la misma línea

```bash
git checkout main
```

```bash
echo "Color rojo" > estilos.txt

git add .
git commit -m "Color rojo"
```

---

## 4. Volver a la rama feature y lanzar rebase

```bash
git checkout feature/conflicto
```

```bash
git rebase main
```

---

## 5. Resolver conflicto

Git mostrará algo parecido a esto:

```text
<<<<<<< HEAD
Color rojo
=======
Color azul
>>>>>>> commit
```

Editar el fichero dejando el contenido correcto:

```text
Color azul y rojo
```

---

## 6. Continuar el rebase

```bash
git add estilos.txt
git rebase --continue
```

---

## 7. Cancelar un rebase (opcional)

```bash
git rebase --abort
```

---

# Ejercicio 3 — Rebase interactivo

## 1. Crear rama

```bash
git checkout main
git checkout -b feature/interactivo
```

---

## 2. Crear varios commits

```bash
echo "Linea 1" > fichero.txt

git add .
git commit -m "Commit 1"
```

```bash
echo "Linea 2" >> fichero.txt

git add .
git commit -m "Commit 2"
```

```bash
echo "Linea 3" >> fichero.txt

git add .
git commit -m "Commit 3"
```

---

## 3. Lanzar rebase interactivo

```bash
git rebase -i HEAD~3
```

---

## 4. Editor interactivo

Git abrirá algo parecido a:

```text
pick abc123 Commit 1
pick def456 Commit 2
pick ghi789 Commit 3
```

---

# Opciones del rebase interactivo

## Combinar commits (`squash`)

```text
pick abc123 Commit 1
squash def456 Commit 2
squash ghi789 Commit 3
```

Resultado:

- Los commits se combinarán en uno solo.

---

## Cambiar mensaje (`reword`)

```text
reword abc123 Commit 1
pick def456 Commit 2
pick ghi789 Commit 3
```

Resultado:

- Git permitirá modificar el mensaje del commit.

---

## Eliminar commit (`drop`)

```text
pick abc123 Commit 1
drop def456 Commit 2
pick ghi789 Commit 3
```

Resultado:

- El commit eliminado desaparecerá del historial.

---

## Reordenar commits

Simplemente cambiar el orden:

```text
pick ghi789 Commit 3
pick abc123 Commit 1
pick def456 Commit 2
```

---

# Ver historial final

```bash
git log --oneline --graph --all
```

---

# Buenas prácticas

## Actualizar cambios remotos antes de rebase

```bash
git fetch
```

---

## Rebase correcto sobre la rama principal

```bash
git checkout feature/login
git rebase main
```

---

## Evitar merges innecesarios

Usar:

```bash
git pull --rebase
```

En lugar de:

```bash
git pull
```

---

# Conceptos importantes

## `merge`

- Mantiene el historial original.
- Genera commits de merge.

---

## `rebase`

- Reescribe el historial.
- Mantiene una línea temporal más limpia.
- Reaplica commits encima de otra rama.

---

# Cuándo usar rebase

- Mantener historial limpio.
- Preparar Pull Requests.
- Combinar commits pequeños.
- Actualizar ramas feature con cambios de `main`.

---

# Cuándo NO usar rebase

No hacer rebase sobre ramas públicas compartidas por otros desarrolladores, ya que reescribe el historial.
