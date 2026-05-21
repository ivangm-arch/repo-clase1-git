# Contenido Git extra

Esta sección contiene ejercicios adicionales para reforzar Git con situaciones habituales de trabajo real.

No es imprescindible para una primera toma de contacto, pero sí es muy recomendable para ganar seguridad en escenarios cotidianos:

- guardar trabajo temporalmente sin hacer commit,
- recuperar commits aparentemente perdidos,
- aplicar un commit concreto de una rama a otra.
  
---

# 01. Git stash

## Objetivo

Aprender a guardar cambios temporales sin crear un commit.

`git stash` es útil cuando estás trabajando en una rama, tienes cambios sin terminar y necesitas cambiar de contexto.

Ejemplo típico:

> Estás desarrollando una funcionalidad, pero aparece una incidencia urgente en `main`. No quieres hacer un commit incompleto, pero necesitas cambiar de rama.

---

## Concepto clave

`git stash` guarda temporalmente los cambios del directorio de trabajo y deja el repositorio limpio.

Flujo mental:

```text
Tengo cambios sin terminar -> los guardo temporalmente -> cambio de rama -> vuelvo -> recupero los cambios
```

---

## Comandos principales

```bash
git stash
git stash list
git stash apply
git stash pop
git stash drop
```

---

## Diferencia entre `apply` y `pop`

| Comando | Qué hace |
|---|---|
| `git stash apply` | Recupera los cambios, pero mantiene el stash guardado |
| `git stash pop` | Recupera los cambios y elimina el stash de la lista |

Para principiantes, es más seguro usar primero:

```bash
git stash apply
```

Cuando ya se entiende el flujo, se puede usar:

```bash
git stash pop
```

---

## Ejercicio guiado

### 1. Sitúate en `main`

```bash
git switch main
```

Comprueba el estado:

```bash
git status
```

---

### 2. Crea una rama de trabajo

```bash
git switch -c feature/stash-demo
```

---

### 3. Crea cambios sin terminar

```bash
echo "Trabajo empezado pero no terminado" > trabajo-temporal.txt
```

Comprueba el estado:

```bash
git status
```

Pregunta:

- ¿El archivo está versionado?
- ¿Hay algún commit nuevo?

---

### 4. Guarda temporalmente los cambios

```bash
git add .
git stash push -m "Trabajo temporal de la feature stash"
```

Comprueba el estado:

```bash
git status
```

Pregunta:

- ¿El directorio de trabajo está limpio?

---

### 5. Consulta la lista de stash

```bash
git stash list
```

Deberías ver una entrada similar a:

```text
stash@{0}: On feature/stash-demo: Trabajo temporal de la feature stash
```

---

### 6. Simula un cambio urgente en `main`

```bash
git switch main
echo "Corrección urgente" > hotfix.txt
git add hotfix.txt
git commit -m "Añade corrección urgente"
```

---

### 7. Vuelve a la rama de trabajo

```bash
git switch feature/stash-demo
```

---

### 8. Recupera los cambios guardados

```bash
git stash apply stash@{0}
```

Comprueba el estado:

```bash
git status
```

---

### 9. Confirma el trabajo recuperado

```bash
git add trabajo-temporal.txt
git commit -m "Añade trabajo temporal recuperado desde stash"
```

---

### 10. Elimina el stash si ya no lo necesitas

```bash
git stash drop stash@{0}
```

Comprueba la lista:

```bash
git stash list
```

---

## Ejercicio extra

Repite el ejercicio usando:

```bash
git stash pop
```

Pregunta:

- ¿Qué diferencia observas respecto a `git stash apply`?

---

## Errores habituales

### Error 1: intentar cambiar de rama con cambios pendientes

Git puede impedir el cambio si existe riesgo de sobrescribir archivos.

Soluciones posibles:

```bash
git add .
git commit -m "Guarda trabajo parcial"
```

o:

```bash
git stash
```

---

### Error 2: olvidar que existen varios stash

Antes de recuperar cambios, revisa siempre:

```bash
git stash list
```

---

# 02. Git reflog

## Objetivo

Aprender a recuperar referencias recientes del repositorio.

`git reflog` es una herramienta de seguridad muy útil cuando parece que se ha perdido un commit tras operaciones como:

- `git reset`,
- `git rebase`,
- cambios de rama,
- movimientos accidentales de `HEAD`.

---

## Concepto clave

Git registra los movimientos recientes de `HEAD`.

`git log` muestra el historial visible desde la rama actual.

`git reflog` muestra por dónde se ha movido `HEAD`, incluso si algunos commits ya no aparecen en `git log`.

---

## Comandos principales

```bash
git reflog
git reset --hard <hash>
git switch -c recuperacion <hash>
```

---

## Advertencia importante

`git reset --hard` elimina cambios no confirmados del directorio de trabajo.

Antes de usarlo en un proyecto real, ejecuta:

```bash
git status
```

Si tienes cambios sin commit que quieras conservar, usa antes:

```bash
git stash
```

---

## Ejercicio guiado: recuperar un commit perdido

### 1. Crea una rama de práctica

```bash
git switch main
git switch -c feature/reflog-demo
```

---

### 2. Crea un commit que luego vas a perder

```bash
echo "Commit importante" > importante.txt
git add importante.txt
git commit -m "Añade archivo importante"
```

Guarda el historial visible:

```bash
git log --oneline --graph --all
```

---

### 3. Simula un error con reset

```bash
git reset --hard HEAD~1
```

Ahora revisa el historial:

```bash
git log --oneline --graph --all
```

Pregunta:

- ¿Sigue apareciendo el commit `Añade archivo importante`?

---

### 4. Busca el commit con reflog

```bash
git reflog
```

Busca una línea parecida a:

```text
<hash> HEAD@{1}: commit: Añade archivo importante
```

Copia el hash del commit.

---

### 5. Recupera el commit creando una rama

Esta opción es segura porque no modifica la rama actual:

```bash
git switch -c recuperacion-importante <hash>
```

Comprueba que el archivo existe:

```bash
ls
cat importante.txt
```

---

### 6. Opción alternativa: volver directamente al commit

Solo si tienes claro que quieres mover la rama actual:

```bash
git reset --hard <hash>
```

---

## Preguntas de comprensión

- ¿Por qué `git log` no mostraba el commit perdido?
- ¿Por qué `git reflog` sí lo mostraba?
- ¿Qué opción es más segura: crear una rama desde el hash o hacer `reset --hard`?

---

## Regla práctica

Cuando parezca que has perdido commits, no sigas ejecutando comandos al azar.

Primero ejecuta:

```bash
git reflog
```

---

# 03. Git cherry-pick

## Objetivo

Aprender a aplicar un commit concreto de una rama sobre otra sin fusionar toda la rama.

`git cherry-pick` es útil cuando quieres traer solo un cambio puntual.

Ejemplo típico:

> En una rama de desarrollo hay varios commits, pero solo uno de ellos corrige un bug que también necesitas en `main`.

---

## Concepto clave

`git cherry-pick` no fusiona ramas completas.

Aplica el cambio introducido por un commit concreto sobre la rama actual.

Flujo mental:

```text
Estoy en una rama -> elijo un commit de otra rama -> Git aplica ese cambio aquí
```

---

## Comandos principales

```bash
git log --oneline --graph --all
git cherry-pick <hash>
git cherry-pick --abort
```

---

## Cuándo usar cherry-pick

Casos razonables:

- aplicar un hotfix en varias ramas,
- traer un commit concreto sin mezclar toda una rama,
- recuperar un cambio pequeño de una rama experimental.

Casos en los que conviene evitarlo:

- cuando realmente quieres integrar toda una rama,
- cuando no entiendes bien qué contiene el commit,
- cuando el commit depende de otros commits anteriores.

---

## Ejercicio guiado

### 1. Sitúate en `main`

```bash
git switch main
```

---

### 2. Crea una rama con varios cambios

```bash
git switch -c feature/cherry-pick-demo
```

Crea el primer commit:

```bash
echo "Funcionalidad experimental" > experimental.txt
git add experimental.txt
git commit -m "Añade funcionalidad experimental"
```

Crea el segundo commit:

```bash
echo "Corrección reutilizable" > bugfix.txt
git add bugfix.txt
git commit -m "Corrige bug reutilizable"
```

Crea el tercer commit:

```bash
echo "Más trabajo experimental" >> experimental.txt
git add experimental.txt
git commit -m "Amplía funcionalidad experimental"
```

---

### 3. Visualiza el historial

```bash
git log --oneline --graph --all
```

Localiza el hash del commit:

```text
Corrige bug reutilizable
```

---

### 4. Vuelve a `main`

```bash
git switch main
```

---

### 5. Aplica solo el commit del bugfix

Sustituye `<hash>` por el hash real del commit `Corrige bug reutilizable`:

```bash
git cherry-pick <hash>
```

---

### 6. Comprueba el resultado

```bash
git log --oneline --graph --all
ls
cat bugfix.txt
```

Preguntas:

- ¿Se ha traído `bugfix.txt`?
- ¿Se ha traído todo el contenido de `experimental.txt`?
- ¿Por qué?

---

## Ejercicio extra: provocar un conflicto con cherry-pick

### 1. Crea una rama con un cambio en el mismo archivo

```bash
git switch -c feature/cherry-conflict main
echo "Versión desde rama de conflicto" > conflicto-cherry.txt
git add conflicto-cherry.txt
git commit -m "Añade versión desde rama de conflicto"
```

---

### 2. Vuelve a `main` y crea otro cambio incompatible

```bash
git switch main
echo "Versión desde main" > conflicto-cherry.txt
git add conflicto-cherry.txt
git commit -m "Añade versión desde main"
```

---

### 3. Intenta aplicar el commit de la otra rama

Busca el hash del commit `Añade versión desde rama de conflicto`:

```bash
git log --oneline --graph --all
```

Después ejecuta:

```bash
git cherry-pick <hash>
```

---

### 4. Resolver o abortar

Si quieres resolver el conflicto:

```bash
git status
```

Edita el archivo, elimina las marcas de conflicto y finaliza con:

```bash
git add conflicto-cherry.txt
git cherry-pick --continue
```

Si quieres cancelar la operación:

```bash
git cherry-pick --abort
```

---

## Preguntas de comprensión

- ¿Qué diferencia hay entre `merge` y `cherry-pick`?
- ¿Por qué el nuevo commit en `main` tiene un hash distinto al commit original?
- ¿Qué riesgo existe si haces cherry-pick de un commit que depende de cambios anteriores?

---

# Cierre de la sección

## Resumen rápido

| Comando | Para qué sirve |
|---|---|
| `git stash` | Guardar cambios temporales sin commit |
| `git reflog` | Recuperar movimientos recientes de `HEAD` |
| `git cherry-pick` | Aplicar un commit concreto en otra rama |
