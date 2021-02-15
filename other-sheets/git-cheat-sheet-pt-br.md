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

##### Deleta uma branch na remota:
```
$ git push <remote> :<branch> (desde Git v1.5.0)
```
OR
```
$ git push <remote> --delete <branch> (desde Git v1.7.0)
```

##### Publicar suas tags:
```
$ git push --tags
```
<hr>

#### Configurar a ferramenta de merge globalmente para fundir o código
```bash
$ git config --global merge.tool meld
```

##### Use sua própria ferramenta/editor para resolver conflitos:
```
$ git mergetool
```

## Merge & Rebase (fundir e rebasear)

##### Fazer merge da branch na pilha (HEAD) atual:
```
$ git merge <branch>
```

##### Rebasear a pilha (HEAD) em &lt;branch&gt;:<br>
<em><sub>Só faça rebase de commit publicado!</sub></em>

```
$ git rebase <branch>
```

##### Aborte o rebase:
```
$ git rebase --abort
```

##### Continue um rebase depois de resolver os conflitos:
```
$ git rebase --continue
```

##### Use seu editor para resolver conflitos manualmente e (depois de resolvidos) marcar arquivo como resolvido:
```
$ git add <arquivo_resolvido>
```

```
$ git rm <arquivo_resolvido>
```

##### Squashing commits (tradução literal seria "esmagar commits"):
```
$ git rebase -i <commit-logo-antes-do-primeiro>
```

Agora, substitua...

```
pick <commit_id>
pick <commit_id2>
pick <commit_id3>
```

para isso,

```
pick <commit_id>
squash <commit_id2>
squash <commit_id3>
```
<hr>

## Desfazer

##### Descartar todas as alterações locais no seu atual diretório:
```
$ git reset --hard HEAD
```

##### Tira todos os arquivos da área temporária (staging) (ou seja, desfaz o último `git add`):
```
$ git reset HEAD
```

##### Descarta as alterações locais em um arquivo específico:
```
$ git checkout HEAD <arquivo>
```

##### Reverte um commit (produzindo um novo commit com mudanças contrárias ou diferentes):
```
$ git revert <commit>
```

##### Reseta o ponteiro da HEAD para um commit anterior e descarta todas as mudanças desde aquele ponto:
```
$ git reset --hard <commit>
```

##### Reseta o ponteiro da HEAD pointer para o estado atual de uma branch remota.
```
$ git reset --hard <remote/branch> e.g., upstream/master, origin/my-feature
```

##### Reseta o ponteiro da HEAD para um commit anterior e mantém todas as mudanças na staged:
```
$ git reset <commit>
```

##### Reseta o ponteiro da HEAD para um commit anterior e preserva mudanças locais sem commit:
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

### Index
* [Instalação](#instalação)
* [Iniciando](#iniciando)
* [Características](#características)
* [Fazer um release](#fazer-um-release)
* [Hotfixes](#hotfixes)
* [Comandos](#comandos)

<hr>

### Instalação
###### Você precisa de uma instalação do Git como pré-requisito. Git flow funciona em OSX, Linux e Windows.

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
###### Você vai precisar do wget e util-linux para instalar o git-flow.
```bash
$ wget -q -O - --no-check-certificate https://raw.githubusercontent.com/petervanderdoes/gitflow/develop/contrib/gitflow-installer.sh install <state> | bash
```
<hr>

### Iniciando
###### Git flow precisa inicializar para personalizar um projeto. O uso do git-flow começa ao inicializar dentro de um repositório git existente:
##### Inicializar:
###### Você vai precisar responder algumas questões para personalizar a configuração do projeto. Recomenda-se usar as configurações padrão.
```shell
git flow init
```
OU
###### Para usar o padrão (default)
```shell
git flow init -d
```
<hr>

### Características
###### Desenvolva novas características para versões posteriores. Tipicamente existe em repos de desenvolvedores apenas.
##### Iniciar uma nova feature (característica):
###### Esta ação cria uma branch de nova feature baseada no 'develop' e alterna para ela.
```
git flow feature start MYFEATURE
```

##### Terminar uma feature:
###### Finaliza o desenvolvimento da feature. Esta ação realiza o seguinte:
###### 1) Faz o merged da MYFEATURE na 'develop'.
###### 2) Remove a branch 'feature'.
###### 3) Volta para a branch 'develop'
```
git flow feature finish MYFEATURE
```

##### Publicar uma feature:
###### Você desenvolve uma feature em equipe? Publique uma feature para o servidor remoto para que os outros possam usá-la.
```
git flow feature publish MYFEATURE
```

##### Baixar uma feature publicada:
###### Baixar uma feature publicada por outro usuário.
```
git flow feature pull origin MYFEATURE
```

##### Rastreando a feature na origin:
###### Você consegue rastrear a feature na origin usando:
```
git flow feature track MYFEATURE
```
<hr>

### Fazer um release
###### Ajustes na preparação de um novo release de produção. Permitir para correção de bugs menores e preparando os metadados para um release.

##### Iniciar um release:
###### Use o comando git flow, que cria uma branch de release a partir da 'develop'. Opcionalmente você pode fornecer um hash sha-1 de um commit [BASE] para iniciar a release a partir deste. O commit deve estar no branch 'develop'.
```
git flow release start RELEASE [BASE]
```
###### É aconselhável publicar a release branch depois de criá-la, para permitir outros commits de desenvolvedores. Faça de maneira similar a publicar uma feature com o comando:
```
git flow release publish RELEASE
```
###### (É possível rastrear uma release remota com: ```git flow release track RELEASE```)

##### Finalizando a release:
###### Finalizar a release é um dos grandes pontos em branching no git. Isto executa várias ações:
###### 1) Merge da release branch de volta na 'master'
###### 2) Faz as tags da release com seu nome
###### 3) Volta a fundir a release branch na branch 'develop'
###### 4) Apaga a release branch
```
git flow release finish RELEASE
```
###### Não esqueça de publicar as tags com ```git push --tags```

<hr>

### Hotfixes
###### Hotfixes surgiram da necessidade de agir imediatamente sobre um determinado estado de uma versão em produção. Pode ser criado um branch correspondente a partir da tag na master branch que marca a versão em produção.

##### Iniciar um hotfix:
###### Assim como o comando git flow, um hotfix inicia com:
```
$ git flow hotfix start VERSION [BASENAME]
```
###### O argumento 'version' marca o novo nome da release. Opcionalmente pode-se especificar um basename.

##### Terminando um hotfix:
###### Ao terminar um hotfix, este é fundido de volta na develop e na master. Adicionalmente é feita uma tag na master com a versão do hotfix.
```
git flow hotfix finish VERSION
```
<hr>

### Comandos
<p align="center">
    <img alt="Git" src="./Img/git-flow-commands.png" height="270" width="460">
</p>
<hr>

### Esquema do Git flow

<p align="center">
    <img alt="Git" src="Img/git-flow-commands-without-flow.png">
</p>
<hr>
