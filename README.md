# Clase 1 Git - Ejercicios y ejemplos

Repositorio de apoyo para una primera clase práctica de Git y GitHub.

El objetivo no es memorizar comandos, sino entender el flujo de trabajo básico de Git y practicarlo con ejercicios guiados.

---

## Git vs GitHub

- **Git** es una herramienta de control de versiones que funciona en local.
- **GitHub** es una plataforma para alojar repositorios Git, colaborar, revisar cambios y trabajar con Pull Requests.

Una idea clave para la clase:

> Git es la herramienta. GitHub es una plataforma que usa Git.

---

## Objetivos de la clase

Al finalizar estos ejercicios deberías poder:

- Clonar un repositorio.
- Consultar el estado del repositorio.
- Preparar cambios en el área de staging.
- Crear commits con mensajes claros.
- Crear y cambiar de ramas.
- Fusionar ramas con `merge`.
- Resolver conflictos sencillos.
- Entender cuándo usar `revert`, `reset` y `rebase`.
- Crear una Pull Request en GitHub.
- Usar `stash`, `reflog` y `cherry-pick` en escenarios reales.

---

## Modelo mental básico

Git trabaja principalmente con tres zonas:

```text
Directorio de trabajo -> Área de staging -> Historial de commits
```

- **Directorio de trabajo**: archivos que estás editando.
- **Área de staging**: cambios preparados para el próximo commit.
- **Historial de commits**: versiones confirmadas del proyecto.

---

## Orden recomendado de ejercicios

- [00. Documentación: chuleta Git](./docs/github-git-cheat-sheet.pdf)
- [01. Commits](./ejercicios/01.Commit/README.md)
- [02. Área de staging](./ejercicios/02.Zona-staging/README.md)
- [03. Trabajo con ramas](./ejercicios/03.Trabajo-con-ramas/README.md)
- [04. Merge Fast-Forward](./ejercicios/04.Mergear-ramas/README.MD)
- [05. Merge con commit de fusión](./ejercicios/05.Anexar-ramas-otras-formas/README.md)
- [06. Resolver conflictos](./ejercicios/06.Anexar-conflictos/README.md)
- [07. Rebase de ramas](./ejercicios/07.Rebase-rama/README.md)
- [08. Revertir cambios](./ejercicios/08.Revertir-cambios/README.md)
- [09. Deshacer cambios con reset](./ejercicios/09.Reset/README.md)
- [10. Pull Request](./ejercicios/10.Pull-Request/README.md)
- [Contenido Git extra: stash, reflog y cherry-pick](./contenido-git-extra/README.md)

---

## Flujo básico diario

```bash
git status
git add <archivo>
git commit -m "Mensaje descriptivo"
git push
```

Antes de cada comando importante, usa:

```bash
git status
```

Para entender el historial, usa:

```bash
git log --oneline --graph --all
```

---

## Configuración inicial recomendada

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu@email.com"
git config --global init.defaultBranch main
```

Opcionalmente, configura un editor:

```bash
git config --global core.editor "code --wait"
```

En Windows, con Notepad:

```bash
git config --global core.editor notepad
```

---

## Chuleta de comandos

### Inicializar y clonar repositorios

```bash
git init
git clone https://github.com/ivangm-arch/repo-clase1-git.git
```

### Ver estado y diferencias

```bash
git status
git diff
git diff --staged
```

### Preparar y confirmar cambios

```bash
git add archivo.txt
git add .
git commit -m "Añade archivo de ejemplo"
git commit --amend
```

> Usa `git commit --amend` solo si el commit todavía no se ha compartido con otras personas.

### Restaurar cambios

```bash
git restore archivo.txt
git restore --staged archivo.txt
```

### Revisar historial

```bash
git log
git log --oneline
git log --oneline --graph --all
git log --follow archivo.txt
```

### Trabajar con ramas

```bash
git branch
git switch main
git switch -c mi-rama
git branch -d mi-rama
git branch -D mi-rama
```

### Fusionar y reorganizar historial

```bash
git merge mi-rama
git rebase main
```

### Remotos

```bash
git remote -v
git push
git push -u origin mi-rama
git pull
```

### Mover o eliminar ficheros versionados

```bash
git rm archivo.txt
git mv origen.txt destino.txt
```

### Stash

```bash
git stash
git stash list
git stash apply stash@{0}
git stash pop
```

### Recuperación y commits concretos

```bash
git reflog
git switch -c recuperacion <hash>
git cherry-pick <hash>
git cherry-pick --abort
```

### Alias útiles

```bash
git config --global alias.sw switch
git config --global alias.lol "log --graph --oneline --all"
```

Uso:

```bash
git sw main
git lol
```

---

## Buenas prácticas

### Mensajes de commit poco útiles

```text
fix
cambios
update
asd
```

### Mensajes de commit recomendados

```text
Añade archivo de saludo
Corrige conflicto en frutas.txt
Actualiza instrucciones del ejercicio de ramas
```

---

## Recomendación para clase

Después de cada bloque, pide a los alumnos que ejecuten:

```bash
git status
git log --oneline --graph --all
```

Eso refuerza el modelo mental de Git y evita que ejecuten comandos sin entender el estado del repositorio.
