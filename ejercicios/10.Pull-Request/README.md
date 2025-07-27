
# 🤝 Ejercicio 10: Pull Request en GitHub

Este ejercicio te guiará paso a paso para entender cómo funcionan las **Pull Requests (PR)** en GitHub: qué son, cómo se crean y cómo se revisan y aceptan. Es una forma esencial de colaborar en proyectos abiertos o entre equipos.

---

## 🎯 Objetivo

- Crear una rama para trabajar en una nueva funcionalidad.
- Subir los cambios a GitHub.
- Abrir una Pull Request desde esa rama.
- Revisar y hacer "merge" de la PR en la rama principal.

---

## 👣 Pasos

### 1.  Crea una nueva rama de trabajo
```bash copy
git checkout -b mejora-texto
```

### 2.  Haz cambios en el proyecto
```bash copy
echo "Este es un cambio de prueba para una Pull Request." >> README.md
```
### 3.  Haz commit del cambio
```bash copy
git add README.md
git commit -m "Añadir línea de prueba para pull request"
```
### 4.  Subir la rama al repositorio remoto
```bash copy
git push origin mejora-texto
```
### 5.  Crea una PR
-   Ve a tu repositorio en GitHub.
-   Verás un mensaje como: `Compare & pull request`. Haz clic ahí.
 -   Revisa el resumen, añade una descripción clara de los cambios.
 -   Haz clic en **Create pull request**.

### 6.  Revisa y haz merge
-   En la pestaña de la Pull Request, revisa los cambios.
-  Si todo está correcto, haz clic en **Merge pull request**.
-  Luego en **Confirm merge**

### 8.  Elimina la rama local
Después de hacer el merge, GitHub te ofrecerá eliminar la rama:
- Haz clic en **Delete branch**.
- También puedes hacerlo localmente:
```bash copy
git branch -d mejora-texto
```

## 🧠 ¿Qué es una Pull Request?

Una Pull Request (PR) es una solicitud para que los cambios de una rama sean revisados y fusionados (merged) en otra rama, normalmente la rama principal (`main` o `master`). Las PR permiten:

-   Revisar el código antes de integrarlo.
-   Discutir los cambios con comentarios.    
-   Usar herramientas de revisión automática (CI/CD, linters, etc.).



