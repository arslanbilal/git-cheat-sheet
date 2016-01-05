Git Cheat Sheet Spanish (Español) [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)
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
#####Restore stashed changes back to current branch
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

#####Show changes over time for a specific file:
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

#####Create a new tracking branch based on a remote branch:
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

#####Mark the current commit with a tag:
```
$ git tag <tag-name>
```

#####Mark the current commit with a tag that includes a message:
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

#####Squashing commits:
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
######You'll have to answer a few questions regarding the naming conventions for your branches. It's recommended to use the default values.
```
git flow init
```
<hr>


###Características
######Develop new features for upcoming releases. Typically exist in developers repos only.
#####Start a new feature:
######This action creates a new feature branch based on 'develop' and switches to it.
```
git flow feature start MYFEATURE
```

#####Finish up a feature:
######Finish the development of a feature. This action performs the following:
######1)Merged MYFEATURE into 'develop'.
######2)Removes the feature branch.
######3)Switches back to 'develop' branch
```
git flow feature finish MYFEATURE
```

#####Publish a feature:
######Are you developing a feature in collaboration? Publish a feature to the remote server so it can be used by other users.
```
git flow feature publish MYFEATURE
```

#####Getting a published feature:
######Get a feature published by another user.
```
git flow feature pull origin MYFEATURE
```

#####Tracking a origin feature:
######You can track a feature on origin by using
```
git flow feature track MYFEATURE
```
<hr>


###Hacer un lanzamiento
######Support preparation of a new production release. Allow for minor bug fixes and preparing meta-data for a release

#####Start a release:
######To start a release, use the git flow release command. It creates a release branch created from the 'develop' branch. You can optionally supply a [BASE] commit sha-1 hash to start the release from. The commit must be on the 'develop' branch.
```
git flow release start RELEASE [BASE]
```
######It's wise to publish the release branch after creating it to allow release commits by other developers. Do it similar to feature publishing with the command:
```
git flow release publish RELEASE
```
######(You can track a remote release with the: ```git flow release track RELEASE``` command)

#####Finish up a release:
######Finishing a release is one of the big steps in git branching. It performs several actions:
######1)Merges the release branch back into 'master'
######2)Tags the release with its name
######3)Back-merges the release into 'develop'
######4)Removes the release branch
```
git flow release finish RELEASE
```
######Don't forget to push your tags with ```git push --tags```
<hr>


###Soluciones calientes
######Hotfixes arise from the necessity to act immediately upon an undesired state of a live production version. May be branched off from the corresponding tag on the master branch that marks the production version.

#####Git flow hotfix start:
######Like the other git flow commands, a hotfix is started with
```
$ git flow hotfix start VERSION [BASENAME]
```
######The version argument hereby marks the new hotfix release name. Optionally you can specify a basename to start from.

#####Finish a hotfix:
######By finishing a hotfix it gets merged back into develop and master. Additionally the master merge is tagged with the hotfix version
```
git flow hotfix finish VERSION
```
<hr>


###Comandos
<p align="center">
	<img alt="Git" src="./Img/git-flow-commands.png" height="270" width="460">
</p>
<hr>
