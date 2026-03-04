# Hoja de Referencia de Git y Git Flow 
[![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

<p align="center">
    <img alt="Git" src="../Img/git-logo.png" height="190" width="455">
</p>

---

## 📖 Acerca de

Esta completa hoja de referencia de Git te ayuda a dominar los comandos de Git sin memorizar todo. Ya seas principiante o un desarrollador experimentado, esta guía proporciona una referencia rápida a las operaciones esenciales de Git.

**¡Contribuciones bienvenidas!** Puedes:
- Corregir errores gramaticales
- Agregar nuevos comandos
- Traducir a tu idioma
- Mejorar las explicaciones

---
## 📋 Tabla de Contenidos

- [🔧 Configuración](#-configuración)
- [⚙️ Archivos de Configuración](#️-archivos-de-configuración)
- [🆕 Crear Repositorio](#-crear-repositorio)
- [📝 Cambios Locales](#-cambios-locales)
- [🔍 Búsqueda](#-búsqueda)
- [📖 Historial de Commits](#-historial-de-commits)
- [📁 Mover / Renombrar](#-mover--renombrar)
- [🌿 Ramas y Etiquetas](#-ramas-y-etiquetas)
- [🔄 Actualizar y Publicar](#-actualizar-y-publicar)
- [🔀 Fusionar y Rebase](#-fusionar-y-rebase)
- [↩️ Deshacer](#️-deshacer)
- [🌊 Git Flow](#-git-flow)
- [🌍 Otros Idiomas](#-otros-idiomas)

---

## 🔧 Configuración

### Ver Configuración

**Mostrar la configuración actual:**
```bash
git config --list
```

**Mostrar la configuración del repositorio:**
```bash
git config --local --list
```

**Mostrar la configuración global:**
```bash
git config --global --list
```

**Mostrar la configuración del sistema:**
```bash
git config --system --list
```

### Configuración de Usuario

**Establecer tu nombre para el historial de versiones:**
```bash
git config --global user.name "[firstname lastname]"
```

**Establecer tu dirección de correo electrónico:**
```bash
git config --global user.email "[valid-email]"
```

### Configuración de Pantalla y Editor

**Habilitar el coloreado automático en la línea de comandos:**
```bash
git config --global color.ui auto
```

**Establecer el editor global para commits:**
```bash
git config --global core.editor vi
```

---

## ⚙️ Archivos de Configuración

| Alcance | Ubicación | Flag de Comando |
|---------|-----------|-----------------|
| **Repositorio** | `<repo>/.git/config` | `--local` |
| **Usuario** | `~/.gitconfig` | `--global` |
| **Sistema** | `/etc/gitconfig` | `--system` |

---

## 🆕 Crear Repositorio

### Clonar Repositorio Existente

**Vía SSH:**
```bash
git clone ssh://user@domain.com/repo.git
```

**Vía HTTPS:**
```bash
git clone https://domain.com/user/repo.git
```

### Inicializar Nuevo Repositorio

**Crear repositorio en el directorio actual:**
```bash
git init
```

**Crear repositorio en un directorio específico:**
```bash
git init <directory>
```

---

## 📝 Cambios Locales

### Verificar Estado y Diferencias

**Ver el estado del directorio de trabajo:**
```bash
git status
```

**Mostrar cambios en archivos rastreados:**
```bash
git diff
```

**Mostrar cambios en un archivo específico:**
```bash
git diff <file>
```

### Preparar Cambios (Staging)

**Agregar todos los cambios actuales:**
```bash
git add .
```

**Agregar archivos específicos:**
```bash
git add <filename1> <filename2>
```

**Agregar partes de un archivo de forma interactiva:**
```bash
git add -p <file>
```

### Confirmar Cambios (Commits)

**Confirmar todos los cambios en archivos rastreados:**
```bash
git commit -a
```

**Confirmar los cambios preparados:**
```bash
git commit
```

**Confirmar con un mensaje:**
```bash
git commit -m 'message here'
```

**Saltar el staging y confirmar con un mensaje:**
```bash
git commit -am 'message here'
```

**Confirmar con una fecha específica:**
```bash
git commit --date="`date --date='n day ago'`" -am "<Commit Message Here>"
```

### Modificar Último Commit

> ⚠️ **Advertencia:** ¡No modifiques commits ya publicados!

**Modificar el último commit:**
```bash
git commit -a --amend
```

**Modificar sin cambiar el mensaje del commit:**
```bash
git commit --amend --no-edit
```

**Cambiar la fecha del committer:**
```bash
GIT_COMMITTER_DATE="date" git commit --amend
```

**Cambiar la fecha del autor:**
```bash
git commit --amend --date="date"
```

### Guardar Cambios Temporalmente (Stash)

**Guardar los cambios actuales temporalmente:**
```bash
git stash
```

**Aplicar los últimos cambios guardados:**
```bash
git stash apply
```

**Aplicar un stash específico:**
```bash
git stash apply stash@{stash_number}
```
> Usa `git stash list` para ver los stashes disponibles

**Eliminar el último stash:**
```bash
git stash drop
```

**Mover cambios no confirmados a otra rama:**
```bash
git stash
git checkout branch2
git stash pop
```

---

## 🔍 Búsqueda

### Búsqueda de Texto

**Buscar texto en todos los archivos:**
```bash
git grep "Hello"
```

**Buscar en una versión específica:**
```bash
git grep "Hello" v2.5
```

### Búsqueda en Commits

**Encontrar commits que introdujeron una palabra clave específica:**
```bash
git log -S 'keyword'
```

**Buscar con expresión regular:**
```bash
git log -S 'keyword' --pickaxe-regex
```

---

## 📖 Historial de Commits

### Historial Básico

**Mostrar todos los commits (detallado):**
```bash
git log
```

**Mostrar commits (una línea cada uno):**
```bash
git log --oneline
```

**Mostrar commits de un autor específico:**
```bash
git log --author="username"
```

**Mostrar cambios de un archivo específico:**
```bash
git log -p <file>
```

### Historial Avanzado

**Comparar ramas:**
```bash
git log --oneline <origin/master>..<remote/master> --left-right
```

**Mostrar quién cambió qué y cuándo:**
```bash
git blame <file>
```

### Logs de Referencia

**Mostrar el log de referencia:**
```bash
git reflog show
```

**Eliminar el log de referencia:**
```bash
git reflog delete
```

---

## 📁 Mover / Renombrar

**Renombrar un archivo:**
```bash
git mv Index.txt Index.html
```

---

## 🌿 Ramas y Etiquetas

### Listar Ramas

**Listar ramas locales:**
```bash
git branch
```

**Listar todas las ramas (locales + remotas):**
```bash
git branch -a
```

**Listar ramas remotas:**
```bash
git branch -r
```

**Listar ramas fusionadas:**
```bash
git branch --merged
```

### Cambiar y Crear Ramas

**Cambiar a una rama existente:**
```bash
git checkout <branch>
```

**Crear y cambiar a una nueva rama:**
```bash
git checkout -b <branch>
```

**Cambiar a la rama anterior:**
```bash
git checkout -
```

**Crear una rama a partir de una rama existente:**
```bash
git checkout -b <new_branch> <existing_branch>
```

**Crear una rama a partir de un commit específico:**
```bash
git checkout <commit-hash> -b <new_branch_name>
```

**Crear una rama sin cambiar a ella:**
```bash
git branch <new-branch>
```

**Crear una rama de seguimiento (tracking):**
```bash
git branch --track <new-branch> <remote-branch>
```

### Operaciones con Ramas

**Obtener un archivo individual de otra rama:**
```bash
git checkout <branch> -- <filename>
```

**Aplicar un commit específico de otra rama:**
```bash
git cherry-pick <commit hash>
```

**Renombrar la rama actual:**
```bash
git branch -m <new_branch_name>
```

**Eliminar una rama local:**
```bash
git branch -d <branch>
```

**Forzar la eliminación de una rama local:**
```bash
git branch -D <branch>
```
> ⚠️ **Advertencia:** ¡Perderás los cambios no fusionados!

### Etiquetas

**Crear una etiqueta en HEAD:**
```bash
git tag <tag-name>
```

**Crear una etiqueta anotada:**
```bash
git tag -a <tag-name>
```

**Crear una etiqueta con mensaje:**
```bash
git tag <tag-name> -am 'message here'
```

**Listar todas las etiquetas:**
```bash
git tag
```

**Listar etiquetas con sus mensajes:**
```bash
git tag -n
```

---

## 🔄 Actualizar y Publicar

### Gestión de Remotos

**Listar los remotos configurados:**
```bash
git remote -v
```

**Mostrar información de un remoto:**
```bash
git remote show <remote>
```

**Agregar un nuevo remoto:**
```bash
git remote add <remote> <url>
```

**Renombrar un remoto:**
```bash
git remote rename <remote> <new_remote>
```

**Eliminar un remoto:**
```bash
git remote rm <remote>
```
> ℹ️ **Nota:** Esto solo elimina la referencia remota localmente, no el repositorio remoto en sí.

### Fetch y Pull

**Descargar cambios sin fusionar:**
```bash
git fetch <remote>
```

**Descargar y fusionar cambios:**
```bash
git pull <remote> <branch>
```

**Obtener cambios de la rama principal:**
```bash
git pull origin master
```

**Pull con rebase:**
```bash
git pull --rebase <remote> <branch>
```

### Push y Publicar

**Publicar cambios locales:**
```bash
git push <remote> <branch>
```

**Eliminar una rama remota:**
```bash
# Git v1.7.0+
git push <remote> --delete <branch>

# Git v1.5.0+
git push <remote> :<branch>
```

**Publicar etiquetas:**
```bash
git push --tags
```

---

## 🔀 Fusionar y Rebase

### Operaciones de Fusión

**Fusionar una rama en el HEAD actual:**
```bash
git merge <branch>
```

**Configurar herramienta de fusión globalmente:**
```bash
git config --global merge.tool meld
```

**Usar la herramienta de fusión configurada:**
```bash
git mergetool
```

### Operaciones de Rebase

> ⚠️ **Advertencia:** ¡No hagas rebase de commits ya publicados!

**Hacer rebase del HEAD actual sobre una rama:**
```bash
git rebase <branch>
```

**Abortar el rebase:**
```bash
git rebase --abort
```

**Continuar el rebase después de resolver conflictos:**
```bash
git rebase --continue
```

### Resolución de Conflictos

**Marcar archivo como resuelto:**
```bash
git add <resolved-file>
```

**Eliminar archivo resuelto:**
```bash
git rm <resolved-file>
```

### Comprimir Commits (Squash)

**Rebase interactivo para comprimir:**
```bash
git rebase -i <commit-just-before-first>
```

**Ejemplo de configuración de squash:**
```
# Antes
pick <commit_id>
pick <commit_id2>
pick <commit_id3>

# Después (comprimir commit_id2 y commit_id3 en commit_id)
pick <commit_id>
squash <commit_id2>
squash <commit_id3>
```

---

## ↩️ Deshacer

### Descartar Cambios

**Descartar todos los cambios locales:**
```bash
git reset --hard HEAD
```

**Quitar todos los archivos del staging:**
```bash
git reset HEAD
```

**Descartar cambios en un archivo específico:**
```bash
git checkout HEAD <file>
```

### Operaciones de Reset

**Resetear a un commit anterior (descartar todos los cambios):**
```bash
git reset --hard <commit>
```

**Resetear al estado de la rama remota:**
```bash
git reset --hard <remote/branch>
# Ejemplo: git reset --hard upstream/master
```

**Resetear preservando cambios como no preparados:**
```bash
git reset <commit>
```

**Resetear preservando cambios locales no confirmados:**
```bash
git reset --keep <commit>
```

### Revertir Commits

**Revertir un commit (crear un nuevo commit con cambios opuestos):**
```bash
git revert <commit>
```

### Limpiar Archivos Ignorados

**Eliminar archivos confirmados accidentalmente que deberían ser ignorados:**
```bash
git rm -r --cached .
git add .
git commit -m "remove ignored files"
```

---

## 🌊 Git Flow

**Git-flow mejorado:** [git-flow-avh](https://github.com/petervanderdoes/gitflow-avh)

### 📋 Tabla de Contenidos
- [🔧 Instalación](#instalación)
- [🚀 Primeros Pasos](#primeros-pasos)
- [✨ Funcionalidades](#funcionalidades)
- [🎁 Crear un Release](#crear-un-release)
- [🔥 Hotfixes](#hotfixes)
- [📊 Resumen de Comandos](#resumen-de-comandos)

---

### 🔧 Instalación {#instalación}

> **Prerrequisito:** Se requiere una instalación funcional de Git. Git-flow funciona en macOS, Linux y Windows.

**macOS (Homebrew):**
```bash
brew install git-flow-avh
```

**macOS (MacPorts):**
```bash
port install git-flow
```

**Linux (basado en Debian):**
```bash
sudo apt-get install git-flow
```

**Windows (Cygwin):**
> Requiere wget y util-linux
```bash
wget -q -O - --no-check-certificate https://raw.githubusercontent.com/petervanderdoes/gitflow/develop/contrib/gitflow-installer.sh install <state> | bash
```

---

### 🚀 Primeros Pasos

Git-flow necesita inicialización para personalizar la configuración de tu proyecto.

**Inicializar (interactivo):**
```bash
git flow init
```
> Responderás preguntas sobre las convenciones de nombres de ramas. Se recomiendan los valores predeterminados.

**Inicializar (usar valores predeterminados):**
```bash
git flow init -d
```

---

### ✨ Funcionalidades

Las funcionalidades son para desarrollar nueva funcionalidad para próximos lanzamientos. Normalmente solo existen en los repositorios de los desarrolladores.

**Iniciar nueva funcionalidad:**
```bash
git flow feature start MYFEATURE
```
> Crea una rama de funcionalidad basada en 'develop' y cambia a ella

**Finalizar funcionalidad:**
```bash
git flow feature finish MYFEATURE
```
> Esto hará lo siguiente:
> 1. Fusionar MYFEATURE en 'develop'
> 2. Eliminar la rama de funcionalidad
> 3. Cambiar de vuelta a 'develop'

**Publicar funcionalidad (para colaboración):**
```bash
git flow feature publish MYFEATURE
```

**Obtener funcionalidad publicada:**
```bash
git flow feature pull origin MYFEATURE
```

**Rastrear funcionalidad en origin:**
```bash
git flow feature track MYFEATURE
```

---

### 🎁 Crear un Release

Los releases permiten preparar nuevos lanzamientos de producción, permitiendo correcciones menores de errores y preparación de metadatos.

**Iniciar release:**
```bash
git flow release start RELEASE [BASE]
```
> Crea una rama de release desde 'develop'. Opcionalmente especifica el SHA-1 del commit [BASE].

**Publicar release:**
```bash
git flow release publish RELEASE
```

**Rastrear release remoto:**
```bash
git flow release track RELEASE
```

**Finalizar release:**
```bash
git flow release finish RELEASE
```
> Esto hará lo siguiente:
> 1. Fusionar la rama de release en 'master'
> 2. Etiquetar el release
> 3. Re-fusionar el release en 'develop'
> 4. Eliminar la rama de release

> 💡 **No olvides:** Sube tus etiquetas con `git push --tags`

---

### 🔥 Hotfixes

Los hotfixes abordan problemas críticos en versiones de producción en vivo. Se ramifican desde la etiqueta correspondiente en master.

**Iniciar hotfix:**
```bash
git flow hotfix start VERSION [BASENAME]
```

**Finalizar hotfix:**
```bash
git flow hotfix finish VERSION
```
> Fusiona de vuelta tanto en 'develop' como en 'master', y etiqueta la fusión en master

---

### 📊 Resumen de Comandos

<p align="center">
    <img alt="Comandos de Git Flow" src="../Img/git-flow-commands.png" height="270" width="460">
</p>

### 🌊 Esquema de Git Flow

<p align="center">
    <img alt="Esquema de Git Flow" src="../Img/git-flow-commands-without-flow.png">
</p>

---


## 🌍 Otros Idiomas

Esta hoja de referencia está disponible en múltiples idiomas:

| Idioma | Enlace |
|--------|--------|
| 🇸🇦 Árabe | [git-cheat-sheet-ar.md](git-cheat-sheet-ar.md) |
| 🇧🇩 Bengalí | [git-cheat-sheet-bn.md](git-cheat-sheet-bn.md) |
| 🇧🇷 Portugués Brasileño | [git-cheat-sheet-pt_BR.md](git-cheat-sheet-pt_BR.md) |
| 🇨🇳 Chino | [git-cheat-sheet-zh.md](git-cheat-sheet-zh.md) |
| 🇩🇪 Alemán | [git-cheat-sheet-de.md](git-cheat-sheet-de.md) |
| 🇬🇷 Griego | [git-cheat-sheet-el.md](git-cheat-sheet-el.md) |
| 🇮🇳 Hindi | [git-cheat-sheet-hi.md](git-cheat-sheet-hi.md) |
| 🇰🇷 Coreano | [git-cheat-sheet-ko.md](git-cheat-sheet-ko.md) |
| 🇵🇱 Polaco | [git-cheat-sheet-pl.md](git-cheat-sheet-pl.md) |
| 🇪🇸 **Español** (actual) | |
| 🇹🇷 Turco | [git-cheat-sheet-tr.md](git-cheat-sheet-tr.md) |

---

## 🤝 Contribuir

¡Damos la bienvenida a las contribuciones! Puedes:

- 🐛 Reportar errores o erratas
- ✨ Agregar nuevos comandos de Git
- 🌍 Traducir a nuevos idiomas
- 💡 Mejorar las explicaciones
- 📝 Mejorar el formato

**Cómo contribuir:**
1. Haz un fork de este repositorio
2. Crea tu rama de funcionalidad (`git checkout -b feature/FuncionalidadIncreible`)
3. Confirma tus cambios (`git commit -m 'Agregar FuncionalidadIncreible'`)
4. Sube la rama (`git push origin feature/FuncionalidadIncreible`)
5. Abre un Pull Request

---

## 📄 Licencia

Este proyecto es de código abierto y está disponible bajo la [Licencia MIT](../LICENSE).

---

<p align="center">
    <b>⭐ ¡Dale una estrella a este repositorio si te resultó útil!</b>
</p>
