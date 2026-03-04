# Git Cheat Sheet Español

![Git Logo](../Img/git-logo.png)

Una guía de referencia rápida para los comandos de Git más utilizados, organizados por categorías para facilitar su consulta.

---

## 📖 Acerca de esta Guía

Esta guía completa de referencia de Git es un recurso integral para cualquiera que busque mejorar su flujo de trabajo con Git. Desde principiantes que comienzan su viaje con Git hasta desarrolladores experimentados, esta guía proporciona comandos organizados y categorizados para acelerar tu proceso de desarrollo.

### Características Principales:
- **Categorías organizadas**: Los comandos están organizados en grupos claros y lógicos
- **Ejemplos prácticos**: Con casos de uso del mundo real
- **Amigable para principiantes**: Con explicaciones claras y consejos
- **Referencia rápida**: Acceso rápido a comandos esenciales

---

## 📑 Tabla de Contenidos

- [📖 Acerca de esta Guía](#acerca-de-esta-guía)
- [🔧 Configuración Inicial](#configuración-inicial)
- [📁 Configuración de Repositorio](#configuración-de-repositorio)
- [📊 Comandos de Estado](#comandos-de-estado)
- [📝 Gestión de Archivos](#gestión-de-archivos)
- [💾 Commits](#commits)
- [🌿 Ramas (Branches)](#ramas-branches)
- [🔀 Fusión (Merge)](#fusión-merge)
- [🌐 Remotos](#remotos)
- [📚 Historial y Logs](#historial-y-logs)
- [🏷️ Etiquetas (Tags)](#etiquetas-tags)
- [↩️ Deshacer Cambios](#deshacer-cambios)
- [📦 Stash](#stash)
- [🌊 Git Flow](#git-flow)
- [⚙️ Archivos de Configuración](#archivos-de-configuración)
- [🔍 Búsqueda](#búsqueda)
- [📁 Mover/Renombrar](#moverrenombrar)
- [💡 Consejos Útiles](#consejos-útiles)
- [🌍 Otros Idiomas](#otros-idiomas)
- [🤝 Contribuir](#contribuir)
- [📄 Licencia](#licencia)
- [📖 Recursos Adicionales](#recursos-adicionales)

---

## 🔧 Configuración Inicial

Configurar Git con tu información personal:

```bash
# Configurar nombre de usuario
git config --global user.name "Tu Nombre"

# Configurar email
git config --global user.email "tuemail@ejemplo.com"

# Ver configuración actual
git config --list

# Configurar editor por defecto
git config --global core.editor "nano"

# Configurar herramienta de diff
git config --global merge.tool vimdiff
```

---

## 📁 Configuración de Repositorio

### Inicializar un nuevo repositorio:

```bash
# Crear un nuevo repositorio Git
git init

# Clonar un repositorio existente
git clone <url-del-repositorio>

# Clonar a un directorio específico
git clone <url-del-repositorio> <nombre-directorio>
```

---

## 📊 Comandos de Estado

### Verificar el estado de tu repositorio:

```bash
# Mostrar estado actual del repositorio
git status

# Mostrar estado en formato corto
git status -s

# Mostrar estado ignorando archivos no rastreados
git status --ignored

# Mostrar diferencias en archivos modificados
git diff

# Mostrar diferencias en el área de preparación
git diff --staged

# Mostrar diferencias entre ramas
git diff <rama1> <rama2>
```

---

## 📝 Gestión de Archivos

### Agregar y remover archivos:

```bash
# Agregar archivo específico al área de preparación
git add <archivo>

# Agregar todos los archivos modificados
git add .

# Agregar todos los archivos de un tipo específico
git add *.txt

# Agregar interactivamente
git add -i

# Remover archivo del repositorio y del directorio de trabajo
git rm <archivo>

# Remover archivo solo del repositorio (mantener en directorio)
git rm --cached <archivo>

# Mover/renombrar archivo
git mv <archivo-origen> <archivo-destino>
```

---

## 💾 Commits

### Guardar cambios en el repositorio:

```bash
# Hacer commit con mensaje
git commit -m "Mensaje del commit"

# Hacer commit agregando todos los archivos modificados
git commit -am "Mensaje del commit"

# Modificar el último commit
git commit --amend

# Hacer commit vacío (útil para triggers de CI/CD)
git commit --allow-empty -m "Trigger CI"

# Hacer commit con mensaje detallado (abre editor)
git commit
```

---

## 🌿 Ramas (Branches)

### Trabajar con ramas:

```bash
# Listar todas las ramas
git branch

# Listar ramas remotas
git branch -r

# Listar todas las ramas (locales y remotas)
git branch -a

# Crear nueva rama
git branch <nombre-rama>

# Cambiar a una rama
git checkout <nombre-rama>

# Crear y cambiar a nueva rama
git checkout -b <nombre-rama>

# Crear rama desde un commit específico
git checkout -b <nombre-rama> <hash-commit>

# Eliminar rama
git branch -d <nombre-rama>

# Eliminar rama forzadamente
git branch -D <nombre-rama>

# Renombrar rama actual
git branch -m <nuevo-nombre>

# Renombrar rama específica
git branch -m <nombre-antiguo> <nombre-nuevo>
```

---

## 🔀 Fusión (Merge)

### Fusionar cambios entre ramas:

```bash
# Fusionar rama en la rama actual
git merge <nombre-rama>

# Fusionar sin fast-forward (crear commit de merge)
git merge --no-ff <nombre-rama>

# Fusionar solo si es fast-forward
git merge --ff-only <nombre-rama>

# Abortar fusión en curso
git merge --abort

# Continuar fusión después de resolver conflictos
git merge --continue
```

---

## 🌐 Remotos

### Gestionar repositorios remotos:

```bash
# Listar repositorios remotos
git remote

# Listar repositorios remotos con URLs
git remote -v

# Agregar repositorio remoto
git remote add <nombre> <url>

# Cambiar URL de repositorio remoto
git remote set-url <nombre> <nueva-url>

# Eliminar repositorio remoto
git remote remove <nombre>

# Subir cambios al repositorio remoto
git push <remoto> <rama>

# Subir rama y establecer tracking
git push -u <remoto> <rama>

# Subir todas las ramas
git push --all

# Subir etiquetas
git push --tags

# Descargar cambios del repositorio remoto
git pull <remoto> <rama>

# Descargar cambios sin fusionar
git fetch <remoto>

# Descargar todas las ramas remotas
git fetch --all
```

---

## 📚 Historial y Logs

### Explorar el historial de commits:

```bash
# Mostrar historial de commits
git log

# Mostrar historial en una línea por commit
git log --oneline

# Mostrar historial con gráfico
git log --graph

# Mostrar historial de un archivo específico
git log <archivo>

# Mostrar estadísticas de commits
git log --stat

# Mostrar cambios en cada commit
git log -p

# Mostrar últimos N commits
git log -n <número>

# Mostrar commits entre fechas
git log --since="2023-01-01" --until="2023-12-31"

# Mostrar commits por autor
git log --author="Nombre del Autor"

# Buscar en mensajes de commit
git log --grep="palabra clave"
```

---

## 🏷️ Etiquetas (Tags)

### Gestionar etiquetas de versión:

```bash
# Listar todas las etiquetas
git tag

# Crear etiqueta ligera
git tag <nombre-etiqueta>

# Crear etiqueta anotada
git tag -a <nombre-etiqueta> -m "Mensaje de la etiqueta"

# Crear etiqueta en commit específico
git tag -a <nombre-etiqueta> <hash-commit>

# Mostrar información de una etiqueta
git show <nombre-etiqueta>

# Eliminar etiqueta local
git tag -d <nombre-etiqueta>

# Eliminar etiqueta remota
git push --delete <remoto> <nombre-etiqueta>

# Subir etiqueta específica
git push <remoto> <nombre-etiqueta>

# Subir todas las etiquetas
git push <remoto> --tags
```

---

## ↩️ Deshacer Cambios

### Revertir modificaciones:

```bash
# Descartar cambios en archivo específico
git checkout <archivo>

# Descartar todos los cambios no confirmados
git checkout .

# Revertir archivo a versión específica
git checkout <hash-commit> <archivo>

# Quitar archivo del área de preparación
git reset <archivo>

# Quitar todos los archivos del área de preparación
git reset

# Revertir al commit anterior (mantener cambios)
git reset --soft HEAD~1

# Revertir al commit anterior (descartar cambios)
git reset --hard HEAD~1

# Revertir a commit específico
git reset --hard <hash-commit>

# Crear commit que revierte otro commit
git revert <hash-commit>

# Revertir múltiples commits
git revert <hash-desde>..<hash-hasta>
```

---

## 📦 Stash

### Guardar trabajo temporalmente:

```bash
# Guardar cambios actuales en stash
git stash

# Guardar con mensaje descriptivo
git stash save "Mensaje descriptivo"

# Listar todos los stashes
git stash list

# Aplicar el último stash
git stash apply

# Aplicar stash específico
git stash apply stash@{0}

# Aplicar y eliminar el último stash
git stash pop

# Eliminar stash específico
git stash drop stash@{0}

# Eliminar todos los stashes
git stash clear

# Mostrar cambios en un stash
git stash show stash@{0}

# Crear rama desde un stash
git stash branch <nombre-rama> stash@{0}
```

---

## 🌊 Git Flow

Git Flow es un modelo de ramificación que define un flujo de trabajo estricto diseñado alrededor del lanzamiento del proyecto.

### Ramas principales:
- **master/main**: Código de producción
- **develop**: Rama de desarrollo principal

### Ramas de soporte:
- **feature**: Para nuevas características
- **release**: Para preparar nuevas versiones
- **hotfix**: Para correcciones urgentes en producción

### Comandos Git Flow:

```bash
# Inicializar git flow
git flow init

# Iniciar nueva característica
git flow feature start <nombre-caracteristica>

# Finalizar característica
git flow feature finish <nombre-caracteristica>

# Publicar característica
git flow feature publish <nombre-caracteristica>

# Iniciar release
git flow release start <version>

# Finalizar release
git flow release finish <version>

# Iniciar hotfix
git flow hotfix start <version>

# Finalizar hotfix
git flow hotfix finish <version>
```

### Flujo de trabajo sin Git Flow:

![Git Flow Commands](../Img/git-flow-commands-without-flow.png)

```bash
# Crear rama de característica
git checkout develop
git checkout -b feature/nueva-caracteristica

# Trabajar en la característica
git add .
git commit -m "Agregar nueva característica"

# Fusionar característica en develop
git checkout develop
git merge --no-ff feature/nueva-caracteristica
git branch -d feature/nueva-caracteristica

# Crear rama de release
git checkout develop
git checkout -b release/1.0.0

# Finalizar release
git checkout master
git merge --no-ff release/1.0.0
git tag -a 1.0.0 -m "Versión 1.0.0"
git checkout develop
git merge --no-ff release/1.0.0
git branch -d release/1.0.0
```

---

## ⚙️ Archivos de Configuración

Git utiliza archivos de configuración para almacenar preferencias de usuario y repositorio:

### Niveles de configuración:

```bash
# Sistema (todos los usuarios)
git config --system

# Usuario (usuario actual)
git config --global

# Repositorio (proyecto específico)
git config --local
```

### Configuraciones comunes:

```bash
# Identidad del usuario
git config --global user.name "Tu Nombre"
git config --global user.email "email@ejemplo.com"

# Editor de texto
git config --global core.editor nano

# Herramienta de merge
git config --global merge.tool vimdiff

# Colores en la salida
git config --global color.ui auto

# Ver configuraciones
git config --list
```

---

## 🔍 Búsqueda

### Buscar en el historial y contenido:

```bash
# Buscar en mensajes de commit
git log --grep="palabra-clave"

# Buscar cambios en el código
git log -S "fragmento de código"

# Buscar en archivos de trabajo
git grep "patrón"

# Buscar en commit específico
git grep "patrón" <hash-commit>

# Buscar ignorando mayúsculas/minúsculas
git grep -i "patrón"

# Buscar palabras completas
git grep -w "palabra"

# Mostrar números de línea
git grep -n "patrón"
```

---

## 📁 Mover/Renombrar

### Mover y renombrar archivos:

```bash
# Renombrar archivo
git mv archivo_viejo.txt archivo_nuevo.txt

# Mover archivo a carpeta
git mv archivo.txt carpeta/

# Renombrar carpeta
git mv carpeta_vieja carpeta_nueva

# Proceso de renombrado sin git mv
mv archivo_viejo.txt archivo_nuevo.txt
git add archivo_nuevo.txt
git rm archivo_viejo.txt

# Rastrear renombrados en el log
git log --follow archivo.txt

# Detectar movimientos
git log --stat -M
```

---

## 💡 Consejos Útiles

### Alias útiles:

```bash
# Configurar alias útiles
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
git config --global alias.visual '!gitk'
```

### Archivos .gitignore:

```bash
# Crear archivo .gitignore
echo "node_modules/" >> .gitignore
echo "*.log" >> .gitignore
echo ".env" >> .gitignore

# Ignorar archivos ya rastreados
git rm --cached <archivo>
echo "<archivo>" >> .gitignore
git add .gitignore
git commit -m "Agregar archivo a .gitignore"
```

---

## 🌍 Otros Idiomas

Esta hoja de referencia está disponible en los siguientes idiomas:

- 🇺🇸 [English](../README.md)
- 🇸🇦 [العربية](git-cheat-sheet-ar.md)
- 🇧🇩 [বাংলা](git-cheat-sheet-bn.md)
- 🇩🇪 [Deutsch](git-cheat-sheet-de.md)
- 🇬🇷 [Ελληνικά](git-cheat-sheet-el.md)
- 🇪🇸 **Español** (actual)
- 🇮🇳 [हिन्दी](git-cheat-sheet-hi.md)
- 🇰🇷 [한국어](git-cheat-sheet-ko.md)
- 🇵🇱 [Polski](git-cheat-sheet-pl.md)
- 🇧🇷 [Português](git-cheat-sheet-pt_BR.md)
- 🇹🇷 [Türkçe](git-cheat-sheet-tr.md)
- 🇨🇳 [中文](git-cheat-sheet-zh.md)

---

## 🤝 Contribuir

¡Las contribuciones son bienvenidas! Para ayudar a mejorar este proyecto:

1. **Reportar problemas**: Comparte errores o sugerencias de mejora
2. **Agregar nuevos idiomas**: Crea traducciones o mejora las existentes
3. **Mejorar contenido**: Agrega nuevos comandos, ejemplos o explicaciones
4. **Dar retroalimentación**: Comparte tus experiencias y sugerencias

### Cómo contribuir:
- [Abrir un issue en GitHub](https://github.com/arslanbilal/git-cheat-sheet/issues)
- Enviar un pull request
- Sugerir mejoras de documentación

---

## 📄 Licencia

Este proyecto está licenciado bajo la Licencia MIT. Consulta el archivo [LICENSE](../LICENSE) para más detalles.

---

## 📖 Recursos Adicionales

- [Documentación Oficial de Git](https://git-scm.com/doc)
- [Tutoriales de Git de Atlassian](https://www.atlassian.com/git/tutorials)
- [Hoja de Referencia de Git de GitHub](https://education.github.com/git-cheat-sheet-education.pdf)
- [Tutorial Interactivo de Git](https://learngitbranching.js.org/)
- [Libro Pro Git (gratuito)](https://git-scm.com/book/es/v2)
- [Flujos de Trabajo con Git](https://www.atlassian.com/git/tutorials/comparing-workflows)

---

<div align="center">
  <strong>⭐ ¡Si esta hoja de referencia es útil, dale una estrella!</strong><br>
  <em>¡Feliz codificación con Git! 🚀</em>
</div>
