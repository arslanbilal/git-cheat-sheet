Git and Git Flow Cheat Sheet [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)
===============
<hr>
<p align="center">
	<img alt="Git" src="../Img/git-logo.png" height="190" width="455">
</p>
<hr>

### Índice

* [Configuração](#configuração)
* [Arquivos de Configuração](#arquivos-de-configuração)
* [Criar](#criar)
* [Mudanças Locais](#mudanças-locais)
* [Pesquisa](#pesquisa)
* [Histórico de Commits](#histórico-de-commits)
* [Ramos e Tags](#ramos-e-tags)
* [Atualizar e Publicar](#atualizar-e-publicar)
* [Mesclar e Reconstruir](#mesclar-e-reconstruir)
* [Desfazer](#desfazer)
* [Git Flow](#git-flow)

<hr>

## Configuração

##### Mostrar a configuração atual:

```
$ git config --list
```

##### Mostrar a configuração do repositório:

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

##### Definir um nome que seja identificável para crédito ao revisar o histórico de versão:

```
$ git config --global user.name “[nome sobrenome]”
```

##### Definir um endereço de e-mail que será associado a cada marcador de histórico:

```
$ git config --global user.email “[email-válido]”
```

##### Definir a coloração automática da linha de comandos do Git para facilitar a revisão:

```
$ git config --global color.ui auto
```

##### Definir o editor global para *commits*

```
$ git config --global core.editor vi
```

<hr>

## Arquivos de Configuração

##### Arquivo de configuração específico do repositório [--local]:

```
<repo>/.git/config
```

##### Arquivo de configuração específico do usuário [--global]:

```
~/.gitconfig
```

##### Arquivo de configuração de todo o sistema [--system]:

```
/etc/gitconfig
```

<hr>

## Criar

##### Clonar um repositório existente:

Existem duas maneiras:

Via SSH

```
$ git clone ssh://usuario@dominio.com/repo.git
```

Via HTTP

```
$ git clone http://dominio.com/usuario/repo.git
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

## Mudanças Locais

##### Mudanças no diretório de trabalho:

```
$ git status
```

##### Mudanças nos arquivos monitorados:

```
$ git diff
```

##### Ver as mudanças/diferenças de um arquivo específico:

```
$ git diff <arquivo>
```

##### Adicionar todas as mudanças atuais ao próximo *commit*:

```
$ git add .
```

##### Adicionar algumas mudanças no &lt;arquivo&gt; para o próximo *commit*:

```
$ git add -p <arquivo>
```

##### Adicionar apenas os arquivos mencionados ao próximo *commit*:

```
$ git add <nome-do-arquivo-1> <nome-do-arquivo-2>
```

##### Realizar um *commit* de todas as mudanças locais nos arquivos monitorados:

```
$ git commit -a
```

##### Realizar um *commit* das mudanças anteriormente preparadas (*staged*):

```
$ git commit
```

##### Realizar um *commit* com mensagem:

```
$ git commit -m 'mensagem aqui'
```

##### Realizar um *commit* pulando a área de preparação (*staging area*) e adicionando uma mensagem:

```
$ git commit -am 'mensagem aqui'
```

##### Realizar um *commit* com alguma data anterior:

```
$ git commit --date="`date --date='n day ago'`" -am "<Mensagem do commit aqui>"
```

##### Emendar o último *commit*:<br>
<em><sub>Não emenda os *commits* publicados!</sub></em>

```
$ git commit -a --amend
```

##### Emendar com o último *commit*, mas usar a mensagem de log do *commit* anterior:
<em><sub>Não emenda os *commits* publicados!</sub></em>

```shell
$ git commit --amend --no-edit
```

##### Alterar data do *commit* do último *commit*:

```
GIT_COMMITTER_DATE="data" git commit --amend
```

##### Alterar data do Autor do último *commit*:

```shell
$ git commit --amend --date="data"
```

##### Mover as alterações não confirmadas (*uncommitted changes*) do ramo atual para algum outro ramo:<br>

```
$ git stash
$ git checkout ramo2
$ git stash pop
```

##### Restaurar as alterações acumuladas (*stashed changes*) de volta para o ramo atual:

```shell
$ git stash apply
```

##### Restaurar um *stash* particular de volta para o ramo atual:

- O *{numero-do-stash}* pode ser obtido de `git stash list`

```shell
$ git stash apply stash@{numero-do-stash}
```

##### Remover o último conjunto de alterações acumuladas:

```
$ git stash drop
```

<hr>

## Pesquisa

##### Uma pesquisa de texto em todos os arquivos do diretório:

```
$ git grep "Olá"
```

##### Um texto em qualquer versão:

```
$ git grep "Olá" v2.5
```

##### Mostrar *commits* que introduziram uma palavra-chave específica:

```
$ git log -S'palavra-chave'
```

##### Mostrar *commits* que introduziram uma palavra-chave específica (usando uma expressão regular):

```
$ git log -S'palavra-chave' --pickaxe-regex
```

<hr>

## Histórico de Commits

##### Mostrar todos os *commits*, começando pelo mais novo (mostrará o hash, informações do autor, data do *commit* e título do *commit*):

```
$ git log
```

##### Mostrar todos os *commits* (mostrará apenas o hash do *commit* e a mensagem do *commit*)

```
$ git log --oneline
```

##### Mostrar todos os *commits* de um usuário específico:

```
$ git log --author="nome-do-usuario"
```

##### Mostrar alterações ao longo do tempo para um arquivo específico:

```
$ git log -p <arquivo>
```

##### Exibir *commits* que estão presentes apenas no remoto/ramo no lado direito

```
$ git log --oneline <origin/master>..<remoto/master> --left-right
```

##### Quem mudou, o quê e quando no &lt;arquivo&gt;:

```
$ git blame <arquivo>
```

##### Mostrar log de referência:

```
$ git reflog show
```

##### Deletar log de referência:

```
$ git reflog delete
```

<hr>

## Mover / Renomear

##### Renomear um arquivo:

Renomear Index.txt para Index.html

```
$ git mv Index.txt Index.html
```

<hr>

## Ramos e Tags

##### Listar todos os ramos locais:

```
$ git branch
```

##### Listar ramos locais/remotos:

```
$ git branch -a
```

##### Liste todos os ramos remotos:

```
$ git branch -r
```

##### Mudar ramo `HEAD`:

```
$ git checkout <ramo>
```

##### Atualizar um único arquivo de outro ramo:

```
$ git checkout <ramo> -- <arquivo>
```

##### Criar e mudar para um novo ramo:

```
$ git checkout -b <ramo>
```


##### Criar um novo ramo a partir de um ramo existente e mudar para o novo ramo:

```
$ git checkout -b <ramo_novo> <ramo_existente>
```


##### Criar um novo ramo a partir de um *commit* existente e mudar para o novo ramo:

```
$ git checkout <hash-do-commit> -b <novo_nome_do_ramo>
```


##### Criar um novo ramo com base em seu `HEAD` atual:

```
$ git branch <novo-ramo>
```

##### Criar um novo ramo de monitoramento com base em um ramo remoto:

```
$ git branch --track <ramo-novo> <ramo-remoto>
```

##### Deletar um ramo local:

```
$ git branch -d <ramo>
```

##### Renomear o ramo atual para um novo nome de ramo

```shell
$ git branch -m <nome_do_novo_ramo>
```

##### Forçar a exclusão de um ramo local:
<em><sub>Você perderá as alterações não mescladas!</sub></em>

```
$ git branch -D <ramo>
```

##### Marcar `HEAD` com uma *tag*:

```
$ git tag <nome-da-tag>
```

##### Marcar `HEAD` com uma *tag* e abrir o editor para incluir uma mensagem:

```
$ git tag -a <nome-da-tag>
```

##### Marcar `HEAD` com uma *tag* que inclui uma mensagem:

```
$ git tag <nome-da-tag> -am 'mensagem aqui'
```

##### Listar todas as *tags*:

```
$ git tag
```

##### Listar todas as *tags* com suas mensagens (mensagem de *tag* ou mensagem de *commit* se a *tag* não tiver mensagem):

```
$ git tag -n
```

<hr>

## Atualizar e Publicar

##### Listar todos os remotos configurados atualmente:

```
$ git remote -v
```

##### Mostrar informações sobre um remoto:

```
$ git remote show <remoto>
```

##### Adicionar um novo repositório removo chamado &lt;remoto&gt;:

```
$ git remote add <remoto> <url>
```

##### Renomear um repositório remoto de &lt;remoto&gt; para &lt;novo_remoto&gt;:

```
$ git remote rename <remoto> <novo_remoto>
```

##### Remover um remoto:

```
$ git remote rm <remoto>
```

<em><sub>Nota: `git remote rm` não exclui o repositório remoto do servidor. Ele simplesmente remove o remoto e suas referências de seu repositório local.</sub></em>

##### Baixar todas as alterações de &lt;remoto&gt;, mas não integrar no `HEAD`:

```
$ git fetch <remoto>
```

##### Baixar as alterações e mesclar/integrar diretamente no `HEAD`:

```
$ git remote pull <remoto> <url>
```

##### Obter todas as alterações do `HEAD` para o repositório local:

```
$ git pull origin master
```

##### Obter todas as alterações do `HEAD` para o repositório local sem mesclagem:

```
$ git pull --rebase <remoto> <ramo>
```

##### Publicar as alterações locais remotamente:

```
$ git push remote <remoto> <ramo>
```

##### Excluir um ramo no remoto:

```
$ git push <remoto> :<ramo> (desde o Git v1.5.0)
```

OU

```
$ git push <remoto> --delete <ramo> (desde o Git v1.7.0)
```

##### Publicar suas *tags*:

```
$ git push --tags
```

##### Configurar a ferramenta de mesclagem globalmente para o meld (editor)

```bash
$ git config --global merge.tool meld
```

##### Usar sua ferramenta de mesclagem configurada para resolver conflitos:

```
$ git mergetool
```

<hr>

## Mesclar e Reconstruir

##### Mesclar ramo em seu `HEAD` atual:

```
$ git merge <ramo>
```

##### Reconstruir (rebase) seu `HEAD` atual no &lt;ramo&gt;:<br>
<em><sub>Não faz reconstrução de *commit* publicado!</sub></em>

```
$ git rebase <ramo>
```

##### Abortar uma reconstrução:

```
$ git rebase --abort
```

##### Continuar uma reconstrução após resolver os conflitos:

```
$ git rebase --continue
```

##### Usar seu editor para resolver manualmente os conflitos e (depois de resolver) marcar o arquivo como resolvido:

```
$ git add <arquivo-resolvido>
```

```
$ git rm <arquivo-resolvido>
```

##### Juntando *commits* (*squashing commits*):

```
$ git rebase -i <commit-just-before-first>
```

Agora substitua isso:

```
pick <commit_id>
pick <commit_id2>
pick <commit_id3>
```

para isso:

```
pick <commit_id>
squash <commit_id2>
squash <commit_id3>
```

<hr>

## Desfazer

##### Descartar todas as mudanças locais em seu diretório de trabalho:

```
$ git reset --hard HEAD
```

##### Tirar todos os arquivos da área de preparação (ou seja, desfazer o último `git add`):

```
$ git reset HEAD
```

##### Descartar as alterações locais em um arquivo específico:

```
$ git checkout HEAD <arquivo>
```

##### Reverter um *commit* (produzindo um novo *commit* com alterações contrárias):

```
$ git revert <commit>
```

##### Redefinir o ponteiro `HEAD` para um *commit* anterior e descartar todas as alterações desde então:

```
$ git reset --hard <commit>
```

##### Redefinir o ponteiro `HEAD` para um estado atual de um ramo remoto:

```
$ git reset --hard <remoto/ramo> e.g., upstream/master, origin/minha-recurso
```

##### Redefinir o ponteiro `HEAD` para um *commit* anterior e preservar todas as alterações como alterações não preparadas (*unstaged changes*):

```
$ git reset <commit>
```

##### Redefinir o ponteiro `HEAD` para um *commit* anterior e preservar as alterações locais não confirmadas (*committed*):

```
$ git reset --keep <commit>
```

##### Remover arquivos que foram acidentalmente confirmados antes de serem adicionados a .gitignore:

```
$ git rm -r --cached .
$ git add .
$ git commit -m "remove arquivo xyz"
```

<hr>

## Git-Flow
Improved [Git-flow](https://github.com/petervanderdoes/gitflow-avh)

### Índice

* [Configuração](#configuração)
* [Começar](#começar)
* [Recursos](#features)
* [Fazer um Lançamento](#fazer-um-lançamento)
* [Correções Rápidas](#correções-rápidas)
* [Comandos](#comandos)

<hr>

### Configuração

###### Você precisa de uma instalação git funcional como pré-requisito. O Git flow funciona em OSX, Linux e Windows.

##### OSX Homebrew:

```
$ brew install git-flow-avh
```

##### OSX Macports:

```
$ port install git-flow
```

##### Linux (baseado em Debian):

```
$ sudo apt-get install git-flow
```

##### Windows (Cygwin):

###### Você precisa do wget e do util-linux para instalar o git-flow.

```bash
$ wget -q -O - --no-check-certificate https://raw.githubusercontent.com/petervanderdoes/gitflow/develop/contrib/gitflow-installer.sh install <state> | bash
```

<hr>

### Começar

###### O Git flow precisa ser inicializado para personalizar a configuração do projeto. Comece a usar o git-flow inicializando-o dentro de um repositório git existente:

##### Inicializar:

###### Você terá que responder a algumas perguntas sobre as convenções de nomenclatura de seus ramos. É recomendável usar os valores padrão.

```shell
git flow init
```

OU

###### Para usar o padrão

```shell
git flow init -d
```

<hr>

### Recursos

###### Desenvolver novos recursos para os próximos lançamentos. Normalmente existe apenas em repositórios de desenvolvedores.

##### Começar um novo recurso:

###### Esta ação cria um novo ramo de recurso baseado em 'desenvolver' e muda para ele.

```
git flow feature start MEURECURSO
```

##### Concluir um recurso:

###### Concluir o desenvolvimento de um recurso. Esta ação realiza o seguinte:

###### 1) Mescla MEURECURSO para 'desenvolver'.

###### 2) Remove o ramo do recurso.

###### 3) Volta para o ramo 'desenvolver'

```
git flow feature finish MEURECURSO
```

##### Publicar um recurso:

###### Você está desenvolvendo um recurso em colaboração? Publique um recurso no servidor remoto para que possa ser usado por outros usuários.

```
git flow feature publish MEURECURSO
```

##### Obter um recurso publicado:

###### Obter um recurso publicado por outro usuário.

```
git flow feature pull origin MEURECURSO
```

##### Monitorar um recurso de origin:

###### Você pode monitorar um recurso em origin usando

```
git flow feature track MEURECURSO
```

<hr>

### Fazer um Lançamento

###### Apoio na preparação de um novo lançamento de produção. Permitir pequenas correções de bugs e preparar metadados para um lançamento

##### Começar um lançamento:

###### Para iniciar uma versão, use o comando `git flow release`. Ele cria um ramo de lançamento criado a partir do ramo 'desenvolver'. Opcionalmente, você pode fornecer um hash sha-1 de *commit* [BASE] para iniciar o lançamento. O *commit* deve estar no ramo 'desenvolver'.

```
git flow release start LANÇAMENTO [BASE]
```

###### É aconselhável publicar o ramo de lançamento depois de criá-lo para permitir *commits* de lançamento por outros desenvolvedores. Faça de forma semelhante à publicação de recursos com o comando:

```
git flow release publish LANÇAMENTO
```

###### (Você pode monitorar uma versão remota com o comando: `git flow release track LANÇAMENTO`)

##### Concluir um lançamento:

###### Concluir um lançamento é um dos grandes passos na ramificação git. Ele executa várias ações:

###### 1) Mescla o ramo de lançamento de volta em 'master'

###### 2) Marca o lançamento com seu nome

###### 3) Mescla de volta o lançamento em 'desenvolver'

###### 4) Remove o ramo de lançamento

```
git flow release finish LANÇAMENTO
```

###### Não se esqueça de enviar suas *tags* com ```git push --tags```

<hr>

### Correções rápidas

###### As correções rápidas (*hotfixes*) surgem da necessidade de agir imediatamente em um estado indesejado de uma versão de produção ao vivo. Pode ser ramificado a partir da *tag* correspondente no ramo *master* que marca a versão de produção.

##### Início da correção rápida do Git flow:

###### Como os outros comandos do git flow, uma correção rápida é iniciada com

```
$ git flow hotfix start VERSÃO [NOMEDABASE]
```

###### O argumento da versão marca o novo nome de lançamento da correção rápida. Opcionalmente, você pode especificar um nome de base para começar.

##### Concluir uma correção rápida:

###### Ao terminar uma correção rápida, ele é mesclado de volta ao desenvolver e ao *master*. Além disso, a mesclagem do *master* é marcada com a versão da correção rápida

```
git flow hotfix finish VERSÃO
```

<hr>

### Comandos
<p align="center">
    <img alt="Git" src="../Img/git-flow-commands.png" height="270" width="460">
</p>
<hr>

### Esquema git flow

<p align="center">
    <img alt="Git" src="../Img/git-flow-commands-without-flow.png">
</p>
<hr>
