# 01. Commits: primeros pasos

## Objetivo

Practicar el flujo básico de Git:

```text
Directorio de trabajo -> Área de staging -> Commit
```

Al terminar este ejercicio deberías entender:

- qué detecta `git status`,
- qué hace `git add`,
- qué guarda `git commit`,
- cómo consultar el historial con `git log`.

---

## Preparación

Comprueba tu configuración de Git:

```bash
git config --global user.name
git config --global user.email
```

Si no aparece tu nombre o tu email, configúralos:

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu@email.com"
```

---

## Tarea guiada

### 1. Consulta el estado del repositorio

```bash
git status
```

Responde:

- ¿En qué rama estás?
- ¿Hay cambios pendientes?

---

### 2. Consulta el historial

```bash
git log --oneline --graph --all
```

Responde:

- ¿Cuántos commits ves?
- ¿Cuál es el commit más reciente?

---

### 3. Crea un archivo nuevo

```bash
echo "Hola Git" > saludo.txt
```

En Windows PowerShell también puedes usar:

```powershell
"Hola Git" > saludo.txt
```

---

### 4. Comprueba el estado

```bash
git status
```

Responde:

- ¿Git detecta el archivo?
- ¿Está preparado para commit?

---

### 5. Añade el archivo al área de staging

```bash
git add saludo.txt
```

---

### 6. Comprueba el estado de nuevo

```bash
git status
```

Responde:

- ¿Qué ha cambiado respecto al paso anterior?

---

### 7. Crea el primer commit

```bash
git commit -m "Añade archivo de saludo"
```

---

### 8. Revisa el historial

```bash
git log --oneline --graph --all
```

Responde:

- ¿Aparece tu nuevo commit?
- ¿Qué mensaje tiene?

---

### 9. Modifica el archivo

```bash
echo "Estoy aprendiendo Git" >> saludo.txt
```

---

### 10. Repite el flujo completo

```bash
git status
git add saludo.txt
git commit -m "Actualiza saludo"
git log --oneline --graph --all
```

---

## Reto adicional

Crea un segundo archivo llamado `notas.txt`, añade dos líneas de contenido y crea un commit con un mensaje descriptivo.

Ejemplo:

```bash
echo "Nota 1" > notas.txt
echo "Nota 2" >> notas.txt
git add notas.txt
git commit -m "Añade notas del curso"
```

---

## Comandos usados

```bash
git status
git add <archivo>
git commit -m "Mensaje"
git log --oneline --graph --all
```
