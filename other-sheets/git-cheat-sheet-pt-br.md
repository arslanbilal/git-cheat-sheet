Git Cheat Sheet Brazilian portuguese (pt-br)
===============
### Índice
* [Configuração](#configuração)
* [Arquivos de configuração](#arquivos-de-configuração)
* [Criar](#criar)
* [Alterações locais](#alterações locais)
* [Pesquisa](#pesquisa)
* [Histórico de "commit"](#histórico-de-commit)
* [Ramificações & Etiquetas](#ramificações--etiquetas)
* [Atualizar & Publicar](#atualizar--publicar)
* [Fundir & Reembasar](#fundir--reembasar)
* [Desfazer](#desfazer)
* [Git Flow](#git-flow)

<hr>

## Configuração

##### Mostrar a configuração atual:
```
$ git config --list
```
##### Mostrar a configuração local:
```
$ git config --local --list
```

##### Mostrar a configuração global:
```
$ git config --global --list
```

##### Mostrar a configuração do sistema:
```
$ git config --system --list
```

##### Definir um nome que seja identificável para crédito (de autoria) quando houver histórico de revisão:
```
$ git config --global user.name “[nome apelido escolha]”
```

##### Definir um endereço de email que será associado a cada marcador no histórico:
```
$ git config --global user.email “[email-válido]”
```

##### Definir uso de cores na linha de comando, para facilitar a revisão de código usando o Git por linha de comando:
```
$ git config --global color.ui auto
```

##### Definir qual o editor global de código:
```
$ git config --global core.editor vi
```

<hr>

## Arquivos de configuração

##### Arquivos de configuração específicos do repositório [--local]:
```
<repo>/.git/config
```

##### Arquivos de configuração específicos do usuário [--global]:
```
~/.gitconfig
```

##### Arquivos de configuração do sistema [--system]:
```
/etc/gitconfig
```

<hr>

## Criar

##### Clonar um repositório existente:

Há dois modos:

Usando SSH

```
$ git clone ssh://usuario@dominio.com/repo.git
```

Usando HTTP

```
$ git clone http://dominio.com/usario/repo.git
```

##### Criar um novo repositório local no diretório atual:
```
$ git init
```

##### Criar um novo repositório local em um diretório específico:
```
$ git init <diretorio>
```

<hr>

## Alterações locais

##### Alterações no diretório de trabalho:
```
$ git status
```

##### Alterações em arquivos rastreados:
```
$ git diff
```

##### Ver alterações/modificações em um arquivo específico:
```
$ git diff <arquivo>
```

##### Adicionar todas as alterações para o próximo commit:
```
$ git add .
```

##### Adicionar algumas alterações no &lt;arquivo&gt; para o próximo commit:
```
$ git add -p <arquivo>
```

##### Adicionar apenas os arquivos especificados para o próximo commit:
```
$ git add <arquivo1> <arquivo2>
```

##### Fazer commit de todas as mudanças locais (de arquivos rastreados):
```
$ git commit -a
```

##### Fazer commit de todas as mudanças na área temporária (staged):
```
$ git commit
```

##### Inserir um comentário ou mensagem no commit:
```
$ git commit -m 'este espaço pode ser seu, anuncie aqui'
```

##### Fazer o commit pulando a área temporária (staged) e deixando comentário:
```
$ git commit -am 'este espaço pode ser seu, anuncie aqui'
```

##### Fazendo um commit para uma data anterior:
```
$ git commit --date="`date --date='n day ago'`" -am "<Commit este espaço pode ser seu, anuncie aqui>"
```

##### Modificando o último commit:<br>
<em><sub>Não modifique os commits já publicados!</sub></em>

```
$ git commit -a --amend
```

##### Corrigir com o último commit, mas usar a mensagem de log do commit anterior
<em><sub>Não modifique os commits já publicados!</sub></em>

```shell
$ git commit --amend --no-edit
```

##### Alterar a data do "commitador" do último commit:
```
GIT_COMMITTER_DATE="date" git commit --amend
```

##### Alterar a data do autor do último commit:
```shell
$ git commit --amend --date="date"
```

##### Mover as alterações não confirmadas do branch atual para outro branch:<br>
```
$ git stash
$ git checkout branch2
$ git stash pop
```

##### Restaurar mudanças temporárias (staged) para o branch atual:
```shell
$ git stash apply
```

#### Restaura um "stash" específico de volta para o branch atual:
- *{numero_stash}* pode ser obtido usando `git stash list`

```shell
$ git stash apply stash@{numero_stash}
```

##### Remover o último conjunto de mudanças temporárias:
```
$ git stash drop
```

<hr>

## Pesquisa

##### Pesquisar por um texto em todos os arquivos no diretório:
```
$ git grep "Eae mundo"
```

##### Um texto em qualquer versão:
```
$ git grep "Eae mundo" v2.5
```

##### Mostrar commits que iniciem com uma palavra chave específica:
```
$ git log -S'palavra'
```

##### Mostrar commits que iniciem com uma palavra chave específica (usando regex --expressões regulares):
```
$ git log -S'palavra' --pickaxe-regex
```

<hr>

## Histórico de Commit

##### Mostra todos os commits, começando pelos mais novos (vai mostrar o hash, informações do autor, data do commit e título do commit):
```
$ git log
```

##### Mostra todos os commits (mas apenas o hash do commit e a mensagem em uma linha só):
```
$ git log --oneline
```

##### Mostra todos os commits de um usuário específico:
```
$ git log --author="mané"
```

##### Mostra histórico das mudanças de um arquivo específico:
```
$ git log -p <arquivo>
```

##### Mostra commits que estão presentes apenas numa branch remota no lado direito:
```
$ git log --oneline <origin/master>..<remote/master> --left-right
```

##### Quem mudou ("dedo-duro"), o que e quando no &lt;arquivo&gt;:
```
$ git blame <arquivo>
```

##### Mostra o log de referência:
```
$ git reflog show
```

##### Apaga o log de referência:
```
$ git reflog delete
```
<hr>

## Mover / Renomear

##### Renomear um arquivo:

Renomeando Index.txt para Index.html

```
$ git mv Index.txt Index.html
```

<hr>

## Branches & Tags (Ramificações e etiquetas)

##### Lista todas as branches locais:
```
$ git branch
```

#### Lista todas as branches (locais e remotas)
```
$ git branch -a
```

##### Lista todas as branches remotas:
```
$ git branch -r
```

##### Muda a branch:
```
$ git checkout <branch>
```

##### Faz o checkout de um arquivo de outra branch:
```
$ git checkout <branch> -- <nome_arquivo>
```

##### Cria e alterna para uma nova branch:
```
$ git checkout -b <branch>
```


##### Cria uma nova branch de uma existente e alterna para esta nova branch:
```
$ git checkout -b <nova_branch> <branch_existente>
```


#### Faz o checkout e cria uma nova branch de um commit anterior (pelo hash)
```
$ git checkout <commit-hash> -b <nova_branch>
```


##### Cria uma nova branch baseada na pilha (HEAD) atual:
```
$ git branch <nova_branch>
```

##### Cria uma nova branch de rastreamento com base numa branch remota:
```
$ git branch --track <nova_branch> <branch_remota>
```

##### Deleta uma branch local:
```
$ git branch -d <branch>
```

##### Renomeia a branch atual
```shell
$ git branch -m <novo_nome_branch>
```

##### Força a exclusão de uma branch local:
<em><sub>Abre o olho que vai perder tudo que foi alterado!</sub></em>

```
$ git branch -D <branch>
```

##### Marcar a `pilha` com uma tag:
```
$ git tag <tag-name>
```

##### Marcar a `pilha` com uma tag e abrir o editor para incluir uma mensagem:
```
$ git tag -a <tag-name>
```

##### Marcar a `pilha` com uma tag e incluindo uma mensagem:
```
$ git tag <tag-name> -am 'este espaço pode ser seu, anuncie aqui'
```

##### Listar todas as tags:
```
$ git tag
```

##### Lista todas as tags com suas mensagens (mensagem da tag ou do commit, se não conter mensagem):
```
$ git tag -n
```

<hr>

## Atualizar & Publicar

##### Listar todas as remotas configuradas atualmente:
```
$ git remote -v
```

##### Mostra informação de uma remota:
```
$ git remote show <remota>
```

##### Adiciona um novo repositório remoto, com o nome de &lt;remoto&gt;:
```
$ git remote add <remoto> <url>
```

##### Renomeia um repositório remoto, de &lt;remoto&gt; para &lt;novo_remoto&gt;:
```
$ git remote rename <remoto> <novo_remoto>
```

##### Remove um remoto específico:
```
$ git remote rm <remoto>
```

<em><sub>Nota: git remote rm não exclui o repositório remoto do servidor. Ele simplesmente remove o remoto e suas referências de seu repositório local.</sub></em>

##### Download de todas as mudanças todas as mudanças de &lt;remoto&gt;, mas não integra na pilha (HEAD):
```
$ git fetch <remoto>
```

##### Download das mudanças e integra (merge) tudo direto na pilha (HEAD):
```
$ git remote pull <remoto> <url>
```

##### Baixa todas as mudanças da pilha (HEAD) para o repositório local:
```
$ git pull origin master
```

##### Baixa todas as mudanças da pilha (HEAD) para o repositório local sem merge:
```
$ git pull --rebase <remote> <branch>
```

##### Publica mudanças locais na remota:
```
$ git push remote <remote> <branch>
```

##### Delete a branch on the remote:
```
$ git push <remote> :<branch> (since Git v1.5.0)
```
OR
```
$ git push <remote> --delete <branch> (since Git v1.7.0)
```

##### Publish your tags:
```
$ git push --tags
```
<hr>

#### Configure the merge tool globally to meld (editor)
```bash
$ git config --global merge.tool meld
```

##### Use your configured merge tool to solve conflicts:
```
$ git mergetool
```

## Merge & Rebase

##### Merge branch into your current HEAD:
```
$ git merge <branch>
```

##### Rebase your current HEAD onto &lt;branch&gt;:<br>
<em><sub>Don't rebase published commit!</sub></em>

```
$ git rebase <branch>
```

##### Abort a rebase:
```
$ git rebase --abort
```

##### Continue a rebase after resolving conflicts:
```
$ git rebase --continue
```

##### Use your editor to manually solve conflicts and (after resolving) mark arquivo as resolved:
```
$ git add <resolved-arquivo>
```

```
$ git rm <resolved-arquivo>
```

##### Squashing commits:
```
$ git rebase -i <commit-just-before-first>
```

Now replace this,

```
pick <commit_id>
pick <commit_id2>
pick <commit_id3>
```

to this,

```
pick <commit_id>
squash <commit_id2>
squash <commit_id3>
```
<hr>

## Undo

##### Discard all local changes in your working diretório:
```
$ git reset --hard HEAD
```

##### Get all the arquivos out of the staging area(i.e. undo the last `git add`):
```
$ git reset HEAD
```

##### Discard local changes in a specific arquivo:
```
$ git checkout HEAD <arquivo>
```

##### Revert a commit (by producing a new commit with contrary changes):
```
$ git revert <commit>
```

##### Reset your HEAD pointer to a previous commit and discard all changes since then:
```
$ git reset --hard <commit>
```

##### Reset your HEAD pointer to a remote branch current state.
```
$ git reset --hard <remote/branch> e.g., upstream/master, origin/my-feature
```

##### Reset your HEAD pointer to a previous commit and preserve all changes as unstaged changes:
```
$ git reset <commit>
```

##### Reset your HEAD pointer to a previous commit and preserve uncommitted local changes:
```
$ git reset --keep <commit>
```

##### Remove arquivos that were accidentally committed before they were added to .gitignore
```
$ git rm -r --cached .
$ git add .
$ git commit -m "remove xyz arquivo"
```
<hr>

## Git-Flow
Improved [Git-flow](https://github.com/petervanderdoes/gitflow-avh)

### Index
* [Setup](#setup)
* [Getting Started](#getting-started)
* [Features](#features)
* [Make a Release](#make-a-release)
* [Hotfixes](#hotfixes)
* [Commands](#commands)

<hr>

### Setup
###### You need a working git installation as prerequisite. Git flow works on OSX, Linux and Windows.

##### OSX Homebrew:
```
$ brew install git-flow-avh
```

##### OSX Macports:
```
$ port install git-flow
```

##### Linux (Debian-based):
```
$ sudo apt-get install git-flow
```

##### Windows (Cygwin):
###### You need wget and util-linux to install git-flow.
```bash
$ wget -q -O - --no-check-certificate https://raw.githubusercontent.com/petervanderdoes/gitflow/develop/contrib/gitflow-installer.sh install <state> | bash
```
<hr>

### Getting Started
###### Git flow needs to be initialized in order to customize your project setup. Start using git-flow by initializing it inside an existing git repository:
##### Initialize:
###### You'll have to answer a few questions regarding the naming conventions for your branches. It's recommended to use the default values.
```shell
git flow init
```
OR
###### To use default
```shell
git flow init -d
```
<hr>

### Features
###### Develop new features for upcoming releases. Typically exist in developers repos only.
##### Start a new feature:
###### This action creates a new feature branch based on 'develop' and switches to it.
```
git flow feature start MYFEATURE
```

##### Finish up a feature:
###### Finish the development of a feature. This action performs the following:
###### 1) Merged MYFEATURE into 'develop'.
###### 2) Removes the feature branch.
###### 3) Switches back to 'develop' branch
```
git flow feature finish MYFEATURE
```

##### Publish a feature:
###### Are you developing a feature in collaboration? Publish a feature to the remote server so it can be used by other users.
```
git flow feature publish MYFEATURE
```

##### Getting a published feature:
###### Get a feature published by another user.
```
git flow feature pull origin MYFEATURE
```

##### Tracking a origin feature:
###### You can track a feature on origin by using
```
git flow feature track MYFEATURE
```
<hr>

### Make a Release
###### Support preparation of a new production release. Allow for minor bug fixes and preparing meta-data for a release

##### Start a release:
###### To start a release, use the git flow release command. It creates a release branch created from the 'develop' branch. You can optionally supply a [BASE] commit sha-1 hash to start the release from. The commit must be on the 'develop' branch.
```
git flow release start RELEASE [BASE]
```
###### It's wise to publish the release branch after creating it to allow release commits by other developers. Do it similar to feature publishing with the command:
```
git flow release publish RELEASE
```
###### (You can track a remote release with the: ```git flow release track RELEASE``` command)

##### Finish up a release:
###### Finishing a release is one of the big steps in git branching. It performs several actions:
###### 1) Merges the release branch back into 'master'
###### 2) Tags the release with its name
###### 3) Back-merges the release into 'develop'
###### 4) Removes the release branch
```
git flow release finish RELEASE
```
###### Don't forget to push your tags with ```git push --tags```

<hr>

### Hotfixes
###### Hotfixes arise from the necessity to act immediately upon an undesired state of a live production version. May be branched off from the corresponding tag on the master branch that marks the production version.

##### Git flow hotfix start:
###### Like the other git flow commands, a hotfix is started with
```
$ git flow hotfix start VERSION [BASENAME]
```
###### The version argument hereby marks the new hotfix release name. Optionally you can specify a basename to start from.

##### Finish a hotfix:
###### By finishing a hotfix it gets merged back into develop and master. Additionally the master merge is tagged with the hotfix version
```
git flow hotfix finish VERSION
```
<hr>

### Commands
<p align="center">
    <img alt="Git" src="./Img/git-flow-commands.png" height="270" width="460">
</p>
<hr>

### Git flow schema

<p align="center">
    <img alt="Git" src="Img/git-flow-commands-without-flow.png">
</p>
<hr>
