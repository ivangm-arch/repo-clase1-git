# 07. Rebase de ramas

## Objetivo

Aprender a:

- Reaplicar commits sobre otra rama usando `git rebase`
- Entender la diferencia entre `merge` y `rebase`
- Resolver conflictos durante un rebase
- Mantener un historial lineal y limpio

---

# ¿Qué hace `git rebase`?

`git rebase` toma los commits de una rama y los vuelve a aplicar sobre otra base.

Ejemplo:

```text
Antes:

A---B develop
     \
      C---D feature/rebase-demo
```

Después de:

```bash
git rebase develop
```

queda:

```text
A---B---C'---D' feature/rebase-demo
```

Git crea commits nuevos (`C'` y `D'`) con hashes distintos.

---

# Diferencia entre merge y rebase

| Merge | Rebase |
|---|---|
| Une historias creando un merge commit | Reescribe commits sobre otra base |
| Mantiene la historia original | Crea commits nuevos |
| Historial más ramificado | Historial lineal |
| Más seguro para ramas compartidas | Más limpio para ramas locales |

---

# Escenario del ejercicio

Vamos a:

1. Crear una rama feature
2. Hacer cambios
3. Avanzar `develop`
4. Provocar un conflicto
5. Resolverlo con `rebase`

---

# 1. Crear la rama de trabajo

```bash
git switch develop
git switch -c feature/rebase-demo
```

---

# 2. Crear archivo y primer commit

```bash
echo "Linea inicial" > rebase-demo.txt
git add rebase-demo.txt
git commit -m "feat: crear archivo rebase-demo"
```

---

# 3. Segundo commit en la feature

```bash
echo "Cambio desde feature" >> rebase-demo.txt
git add rebase-demo.txt
git commit -m "feat: cambios desde feature"
```

---

# 4. Volver a develop y generar conflicto

```bash
git switch develop
```

Modificar el MISMO archivo para provocar conflicto:

```bash
echo "Cambio desde develop" > rebase-demo.txt
git add rebase-demo.txt
git commit -m "feat: cambios desde develop"
```

---

# Estado del historial

```text
A---B develop
     \
      C---D feature/rebase-demo
```

---

# 5. Volver a la feature y ejecutar rebase

```bash
git switch feature/rebase-demo
git rebase develop
```

Git detectará un conflicto.

---

# 6. Ver conflicto

```bash
git status
```

Verás algo parecido a:

```text
CONFLICT (content): Merge conflict in rebase-demo.txt
```

---

# 7. Resolver conflicto manualmente

Abrir `rebase-demo.txt`.

Verás algo parecido a:

```text
<<<<<<< HEAD
Cambio desde develop
=======
Linea inicial
Cambio desde feature
>>>>>>> feat: cambios desde feature
```

Resolver el conflicto dejando el contenido final así:

```text
Cambio desde develop
Cambio desde feature
```

---

# 8. Marcar conflicto resuelto

```bash
git add rebase-demo.txt
git rebase --continue
```

Si aparecen más conflictos, repetir el proceso.

---

# 9. Verificar historial

```bash
git log --oneline --graph --all
```

Deberías ver una historia lineal:

```text
A---B---C'---D'
```

Sin merge commits.

---

# 10. Integrar la rama en develop

```bash
git switch develop
git merge --ff-only feature/rebase-demo
```

Como la historia quedó lineal, Git hará un fast-forward merge.

---

# Resultado final

```text
A---B---C'---D' develop
```

---

# Comandos útiles durante un rebase

## Continuar después de resolver conflictos

```bash
git rebase --continue
```

## Cancelar el rebase

```bash
git rebase --abort
```

## Saltar un commit conflictivo

```bash
git rebase --skip
```

---

# Importante

Después de un rebase:

- los commits tienen hashes nuevos
- la historia fue reescrita

Si la rama ya existía en remoto, normalmente necesitarás:

```bash
git push --force-with-lease
```

---

# Ejercicio final

1. Crear una nueva rama `feature/rebase-extra`
2. Hacer 3 commits
3. Modificar el mismo archivo desde `develop`
4. Ejecutar:

```bash
git rebase develop
```

5. Resolver conflictos
6. Verificar el historial final con:

```bash
git log --oneline --graph --all
```

---

# Preguntas de reflexión

1. ¿Qué diferencia visual hay entre `merge` y `rebase` en el historial?
2. ¿Por qué los commits cambian de hash después del rebase?
3. ¿Qué ventaja tiene una historia lineal?
4. ¿Cuándo NO deberías hacer rebase sobre ramas compartidas?
5. ¿Qué hace `git push --force-with-lease`?
