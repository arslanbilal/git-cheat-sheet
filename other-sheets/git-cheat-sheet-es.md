Git Cheat Sheet Spanish (Hoja de trucos de Git en Español) [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)
===============
<hr>
###Índice
* [Configuración](#configuracion)
* [Crear](#crear)
* [Cambios locales](#cambios-locales)
* [Busquedas](#busqueda)
* [Historial de commits](#historial-commits)
* [Ramas y etiquetas](#ramas--etiquetas)
* [Modificación y publicación](#modificacion--publicacion)
* [Fusionar & Reorganizar](#fusion--reorganizar)
* [Deshacer](#deshacer)
* [Git Flow](#git-flow)


<hr>
##Configuración
#####Mostrar la configuración actual:
```
$ git config --list
```
#####Mostrar la configuración local:
```
$ git config --local --list
```

#####Mostrar la configuración global:
```
$ git config --global --list
```

#####Mostrar la configuración del sistema:
```
$ git config --system --list
```

#####Asignar un nombre identificable para cuando se hagan revisiones:
```
$ git config --global user.name “[firstname lastname]”
```

#####Asignar la dirección de correo que será asosiada al usuario:
```
$ git config --global user.email “[valid-email]”
```

#####Asignar comando para facilitar la revisión en Git:
```
$ git config --global color.ui auto
```
<hr>
##Crear
#####Clonar un repositorio existente:

Hay dos maneras de hacerlo:

Via SSH

```
$ git clone ssh://user@domain.com/repo.git
```

Via HTTP

```
$ git clone http://domain.com/user/repo.git
```

#####Crear un nuevo repositorio local:
```
$ git init
```
<hr>
##Cambios locales

#####Cambios en el directorio de trabajo:
```
$ git status
```

#####Cambios en los archivos rastreados:
```
$ git diff
```

#####Agregar todos los cambios actuales en la próxima confirmación (commit):
```
$ git add .
```

#####Agregar algunos cambios en &lt;file&gt; a la próxima confirmación (commit):
```
$ git add -p <file>
```

#####Confirmar (Hacer commit) todos los cambios locales en los archivos rastreados:
```
$ git commit -a
```

#####Confirmar (Hacer commit) los cambios previamente en el área de ensayo (staged):
```
$ git commit
```

#####Confirmar (Hacer commit) con mensaje:
```
$ git commit -m 'message here'
```

#####Confirmar (Hacer commit) saltandose el area de ensayo y añadiendo un mensaje:
```
$ git commit -am 'message here'
```

#####Confirmar (Hacer commit) a alguna fecha anterior:
```
git commit --date="`date --date='n day ago'`" -am "Commit Message"
```

#####Cambiar la última confirmación (commit):<br>
<em><sub>No Modificar Confirmaciones (commits) publicados!</sub></em>

```
$ git commit -a --amend
```

#####Mover cambios sin confirmar desde la rama actual hasta alguna otra rama:<br>
```
git stash
git checkout branch2
git stash pop
```
#####Restaurar cambios escondido de nuevo a la rama actual
```
git stash apply
```
<hr>
##Busquedas

#####Un texto en todos los archivos en el directorio:
```
$ git grep "Hello"
```

#####En cualquier versión de una búsqueda de texto:
```
$ git grep "Hello" v2.5
```

<hr>
###Historial de commits

#####Muestra todas las confirmaciones (commits), iniciando con la mas reciente (mostrará el hash, información del autor, fecha de la confirmación y título ó mensaje de la confirmación):
```
$ git log
```

#####Muestra todas las confirmaciones (commits) (solo mostrará el hash de la configuración y el mensaje):
```
$ git log --oneline
```

#####Muestra todas las confirmaciones (commits) de un usuario en específico:
```
$ git log --author="username"
```

#####Mostrar cambios en el tiempo para un archivo específico:
```
$ git log -p <file>
```

#####Quien cambió, qué y cuándo en &lt;file&gt;:
```
$ git blame <file>
```
<hr>
##Ramas y etiquetas

#####Listar todas las ramas locales:
```
$ git branch
```

#####Listar todas las ramas remotas:
```
$ git branch -r
```

#####Cambiar de rama el HEAD:
```
$ git checkout <branch>
```

#####Crear y cambiar a una nueva rama:
```
$ git checkout -b <branch>
```

#####Crear una nueva rama basada en el HEAD actual:
```
$ git branch <new-branch>
```

#####Crear una nueva rama de rastreo basada en una rama remota:
```
$ git branch --track <new-branch> <remote-branch>
```

#####Eliminar una rama local:
```
$ git branch -d <branch>
```

#####Forzar la eliminación de una rama local:
<em><sub>Perderas los cambios sin confirmar</sub></em>

```
$ git branch -D <branch>
```

#####Marcar la confirmación actual con una etiqueta:
```
$ git tag <tag-name>
```

#####Marcar la confirmación actual con una etiqueta que incluye un mensaje:
```
$ git tag -a <tag-name>
```
<hr>
##Modificación y publicación

#####Listar todos remotos configurados actualmente:
```
$ git remote -v
```

#####Mostrar información acerca de un remoto:
```
$ git remote show <remote>
```

#####Agregar un nuevo repositorio remoto, nombrarlo &lt;remote&gt;:
```
$ git remote add <remote> <url>
```

#####Bajar todos los cambios desde &lt;remote&gt;, pero sin integrarlos en HEAD:
```
$ git fetch <remote>
```

#####Bajar los cambios y fusionar/integrar directamente en HEAD:
```
$ git remote pull <remote> <url>
```

#####Obtener todos los cambios desde HEAD hacia el repositorio local:
```
$ git pull origin master
```

#####Obtener todos los cambios desde HEAD hacia el repositorio local sin fusionar:
```
git pull --rebase <remote> <branch>
```

#####Publicar los cambios locales en un remoto:
```
$ git push remote <remote> <branch>
```

#####Eliminar una rama en el remoto:
```
$ git push <remote> :<branch> (since Git v1.5.0)
or
git push <remote> --delete <branch> (since Git v1.7.0)
```

#####Publicar tus etiquetas:
```
$ git push --tags
```
<hr>
##Fusionar & Reorganizar

#####Fusionar <branch> con el HEAD actual:
```
$ git merge <branch>
```

#####Reorganizar el HEAD actual sobre &lt;branch&gt;:<br>
<em><sub>No reorganices confirmaciones (commits) publicadas!</sub></em>

```
$ git rebase <branch>
```

#####Abortar una reorganización:
```
$ git rebase --abort
```

#####Continuar una reorganización desde resolver conflictos:
```
$ git rebase --continue
```

#####Utilizar tu herramienta configurada de fusiones para resolver conflictos:
```
$ git mergetool
```

#####Utilizar tu editor para manualmente resolver conflictos y (despues de resolverlos) marcar el archivo como resuelto:
```
$ git add <resolved-file>
```

```
$ git rm <resolved-file>
```

#####Aplastando confirmaciones (squashing commits):
```
$ git rebase -i <commit-just-before-first>
```

Ahora reemplaza esto,

```
pick <commit_id>
pick <commit_id2>
pick <commit_id3>
```

con esto,

```
pick <commit_id>
squash <commit_id2>
squash <commit_id3>
```
<hr>
##Deshacer

#####Descartar todos los cambios locales en tu directorio de trabajo:
```
$ git reset --hard HEAD
```

#####Obtener todos los archivos fuera del área de ensayo (e.j. deshace el ultimo `git add`):
```
$ git reset HEAD
```

#####Descartar los cambios locales en un archivo específico:
```
$ git checkout HEAD <file>
```

#####Revertir una confirmación (commit) (produciendo una nueva confirmación con los cambios contrarios):
```
$ git revert <commit>
```

#####Reiniciar tu puntero HEAD a una confirmación (commit) anterior y descartar todos los cambios desde entonces:
```
$ git reset --hard <commit>
```

#####Reinicar tu puntero HEAD al estado actual de una rama remota:
```
git reset --hard <remote/branch> e.g., upstream/master, origin/my-feature
```

#####Reiniciar tu puntero HEAD a una confirmación (commit) anterior y conservar todos los cambios como cambios fuera del área de ensayo:
```
$ git reset <commit>
```

#####Reiniciar tu puntero HEAD a una confirmación (commit) anterior y conservar los cambios locales en el área de ensayo:
```
$ git reset --keep <commit>
```

#####Eliminar archivos que fueron accidentalmente confirmados antes de ser añadidos al .gitignore (ignorados):
```
$ git rm -r --cached .
$ git add .
$ git commit -m "remove xyz file"
```
<hr>

##Git-Flow

###Índice
* [Configuración](#configuracion)
* [Iniciando](#iniciando)
* [Características](#caracteristicas)
* [Hacer un lanzamiento](#hacer-un-lanzamiento)
* [Soluciones calientes](#hotfixes)
* [Comandos](#comandos)
<hr>


###Configuración
######Necesitas una instalación de Git como prerequisito. Git flow trabaja en OSX, Linux and Windows.

#####OSX Homebrew:
```
$ brew install git-flow
```

#####OSX Macports:
```
$ port install git-flow
```

#####Linux (Debian-based):
```
$ apt-get install git-flow
```

#####Windows (Cygwin):
######Necesitas wget y util-linux para instalar git-glow.
```
$ wget -q -O - --no-check-certificate https://github.com/nvie/gitflow/raw/develop/contrib/gitflow-installer.sh | bash
```
<hr>


###Iniciando
######Git flow necesita ser inicializado con el fin de personalizar la configuración de su proyecto. Inicia usando git-flow inicializandolo dentro de un repositorio git existente:
#####Inicilizar:
######Tendras que responder algunas preguntas acerca de las convenciones de nombre para tus ramas. Es recomendado utilizar los valores por defecto.
```
git flow init
```
<hr>


###Características
######Desarrolla nuevas características para los próximos lanzamientos. Normalmente, existen solo en los repositorios de desarrolladores.
#####Inicia una nueva característica:
######Esta acción crea una nueva rama de característica basada en 'desarrollo' (ó 'develop') y cambia a la misma.
```
git flow feature start MYFEATURE
```

#####Términa una característica:
######Finaliza el desarrollo de una característica. Esta acción ejecuta lo siguiente:
######1)Fusiona MYFEATURE en 'desarrollo'.
######2)Elimina la rama de la característica.
######3)Cambia de regreso a la rama 'desarrollo'.
```
git flow feature finish MYFEATURE
```

#####Publica una característica:
######¿Estas desarrollando una característica en colaboración? Publica una característica al servidor remoto, de esa manera puede ser utilizada por los demas usuarios.
```
git flow feature publish MYFEATURE
```

#####Obtener una característica publicada:
######Obtener una característica publicada por otro usuario.
```
git flow feature pull origin MYFEATURE
```

#####Rastrear una característica de origen (origin):
######Puedes rastrear una característica en origin utilizando
```
git flow feature track MYFEATURE
```
<hr>


###Hacer un lanzamiento
######Apoya la preparación de un nuevo lanzamiento a producción. Permite correcciones de errores menores y la preparación de los metadatos de un lanzamiento

#####Iniciar un lanzamiento:
######Para iniciar un lanzamiento, utiliza el comando de lanzamiento de git flow. Este crea una rama de lanzamiento creada desde la rama 'desarrollo'. Opcionalmente, puedes suministrar el codigo hash sha-1 de una confirmación (commit) [BASE], para iniciar el lanzamiento desde ahi. La confirmación debe estar en la rama 'desarrollo'.
```
git flow release start RELEASE [BASE]
```
######Es aconsejable publicar la rama de lanzamiento despues de crearla para permitir las confirmaciones (commits) del lanzamiento a los otros desarrolladores. Hazlo similiar a la publicación de la característica con el comando:
```
git flow release publish RELEASE
```
######(Puedes rastrear un lanzamiento remoto con el comando: ```git flow release track RELEASE```)

#####Terminando un lanzamiento:
######Terminar un lanzamiento es uno de los pasos mas grandes en la ramificacion de git. Se lleva a cabo varias acciones:
######1)Fusionar la rama de lanzamiento en 'master'
######2)Etiquetar el lanzamiento con su nombre
######3)Volver a fusionar la rama de lanzamiento en 'desarrollo' (ó 'develop')
######4)Eliminar la rama de lanzamiento
```
git flow release finish RELEASE
```
######No olvides publicar tus etiquetas con ```git push --tags```
<hr>


###Soluciones calientes (Hotfixes)
######Las soluciones calientes se deben a la necesidad de actuar inmediatamente despues de un estado no deseado de una version en producción en vivo. Puede ser ramificada fuera de la etiqueta correspondiente en la rama principal que marca la versión de producción.

#####Las soluciones calientes (hotfix) en Git flow, se inician de la siguiente manera:
######Al igual que los demas comando de git flow, una solución caliente (hotfix) se inicia con
```
$ git flow hotfix start VERSION [BASENAME]
```
######El argumento de la versión presente, marca el nuevo nombre de versión de la revisión (solución). Opcionalmente, se puede especificar un nombre base para empezar.

#####Terminando una solucion caliente (hotfix):
######Al terminar una solución caliente (hotfix) se fusiona en las ramas desarrollo y en master. Además, la fusión en master se etiqueta con la versión de la solución (hotfix)
```
git flow hotfix finish VERSION
```
<hr>


###Comandos
<p align="center">
	<img alt="Git" src="./Img/git-flow-commands.png" height="270" width="460">
</p>
<hr>
