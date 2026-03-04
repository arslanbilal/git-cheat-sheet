# Git Cheat Sheet Português (Brasil)

![Git Logo](../Img/git-logo.png)

---

## 📖 Sobre

Esta folha de dicas abrangente do Git ajuda você a dominar comandos Git sem memorizar tudo. Seja você iniciante ou desenvolvedor experiente, este guia fornece referência rápida para operações essenciais do Git.

**Contribuições são bem-vindas!** Sinta-se livre para:
- Corrigir erros gramaticais
- Adicionar novos comandos
- Traduzir para seu idioma
- Melhorar explicações

---

## 📋 Índice

- [🔧 Configuração](#-configuração)
- [⚙️ Arquivos de Configuração](#️-arquivos-de-configuração)
- [🆕 Criar Repositório](#-criar-repositório)
- [📝 Mudanças Locais](#-mudanças-locais)
- [🔍 Buscar](#-buscar)
- [📖 Histórico de Commits](#-histórico-de-commits)
- [📁 Mover / Renomear](#-mover--renomear)
- [🌿 Branches e Tags](#-branches-e-tags)
- [🔄 Atualizar e Publicar](#-atualizar-e-publicar)
- [🔀 Merge e Rebase](#-merge-e-rebase)
- [↩️ Desfazer](#️-desfazer)
- [🌊 Git Flow](#-git-flow)
- [🌍 Outros Idiomas](#-outros-idiomas)

---

## 🔧 Configuração

### Ver Configuração

**Mostrar configuração atual:**
```bash
git config --list
```

**Mostrar configuração do repositório:**
```bash
git config --local --list
```

**Mostrar configuração global:**
```bash
git config --global --list
```

**Mostrar configuração do sistema:**
```bash
git config --system --list
```

### Configuração do Usuário

**Definir seu nome para histórico de versões:**
```bash
git config --global user.name "[nome sobrenome]"
```

**Definir seu endereço de email:**
```bash
git config --global user.email "[email-válido]"
```

### Configurações de Exibição e Editor

**Habilitar coloração automática da linha de comando:**
```bash
git config --global color.ui auto
```

**Definir editor global para commits:**
```bash
git config --global core.editor vi
```

---

## ⚙️ Arquivos de Configuração

| Escopo | Localização | Flag do Comando |
|--------|-------------|-----------------|
| **Repositório** | `<repo>/.git/config` | `--local` |
| **Usuário** | `~/.gitconfig` | `--global` |
| **Sistema** | `/etc/gitconfig` | `--system` |

---

## 🆕 Criar Repositório

### Clonar Repositório Existente

**Via SSH:**
```bash
git clone ssh://usuario@dominio.com/repo.git
```

**Via HTTPS:**
```bash
git clone https://dominio.com/usuario/repo.git
```

### Inicializar Novo Repositório

**Criar repositório no diretório atual:**
```bash
git init
```

**Criar repositório em diretório específico:**
```bash
git init <diretorio>
```

---

## 📝 Mudanças Locais

### Verificar Status e Diferenças

**Ver status do diretório de trabalho:**
```bash
git status
```

**Mostrar mudanças em arquivos rastreados:**
```bash
git diff
```

**Mostrar mudanças em arquivo específico:**
```bash
git diff <arquivo>
```

### Preparar Mudanças

**Adicionar todas as mudanças atuais:**
```bash
git add .
```

**Adicionar arquivos específicos:**
```bash
git add <arquivo1> <arquivo2>
```

**Adicionar interativamente partes de um arquivo:**
```bash
git add -p <arquivo>
```

### Fazer Commit das Mudanças

**Fazer commit de todas as mudanças de arquivos rastreados:**
```bash
git commit -a
```

**Fazer commit das mudanças preparadas:**
```bash
git commit
```

**Fazer commit com mensagem:**
```bash
git commit -m 'mensagem aqui'
```

**Pular preparação e fazer commit com mensagem:**
```bash
git commit -am 'mensagem aqui'
```

**Fazer commit com data específica:**
```bash
git commit --date="`date --date='n day ago'`" -am "<Mensagem do Commit Aqui>"
```

### Modificar Último Commit

> ⚠️ **Aviso:** Não modifique commits publicados!

**Emendar último commit:**
```bash
git commit -a --amend
```

**Emendar sem alterar mensagem do commit:**
```bash
git commit --amend --no-edit
```

**Alterar data do committer:**
```bash
GIT_COMMITTER_DATE="data" git commit --amend
```

**Alterar data do autor:**
```bash
git commit --amend --date="data"
```

### Guardar Mudanças Temporariamente

**Salvar mudanças atuais temporariamente:**
```bash
git stash
```

**Aplicar últimas mudanças salvas:**
```bash
git stash apply
```

**Aplicar stash específico:**
```bash
git stash apply stash@{numero_stash}
```
> Use `git stash list` para ver stashes disponíveis

**Remover último stash:**
```bash
git stash drop
```

**Mover mudanças não commitadas para outro branch:**
```bash
git stash
git checkout branch2
git stash pop
```

---

## 🔍 Buscar

### Busca de Texto

**Buscar texto em todos os arquivos:**
```bash
git grep "Olá"
```

**Buscar em versão específica:**
```bash
git grep "Olá" v2.5
```

### Busca de Commits

**Encontrar commits que introduziram palavra-chave específica:**
```bash
git log -S 'palavra-chave'
```

**Buscar com expressão regular:**
```bash
git log -S 'palavra-chave' --pickaxe-regex
```

---

## 📖 Histórico de Commits

### Histórico Básico

**Mostrar todos os commits (detalhado):**
```bash
git log
```

**Mostrar commits (uma linha cada):**
```bash
git log --oneline
```

**Mostrar commits por autor específico:**
```bash
git log --author="nomeusuario"
```

**Mostrar mudanças para arquivo específico:**
```bash
git log -p <arquivo>
```

### Histórico Avançado

**Comparar branches:**
```bash
git log --oneline <origin/master>..<remote/master> --left-right
```

**Mostrar quem mudou o que e quando:**
```bash
git blame <arquivo>
```

### Logs de Referência

**Mostrar log de referência:**
```bash
git reflog show
```

**Deletar log de referência:**
```bash
git reflog delete
```

---

## 📁 Mover / Renomear

**Renomear um arquivo:**
```bash
git mv Index.txt Index.html
```

---

## 🌿 Branches e Tags

### Listar Branches

**Listar branches locais:**
```bash
git branch
```

**Listar todos os branches (local + remoto):**
```bash
git branch -a
```

**Listar branches remotos:**
```bash
git branch -r
```

**Listar branches mesclados:**
```bash
git branch --merged
```

### Trocar e Criar Branches

**Trocar para branch existente:**
```bash
git checkout <branch>
```

**Criar e trocar para novo branch:**
```bash
git checkout -b <branch>
```

**Trocar para branch anterior:**
```bash
git checkout -
```

**Criar branch a partir de branch existente:**
```bash
git checkout -b <novo_branch> <branch_existente>
```

**Criar branch a partir de commit específico:**
```bash
git checkout <hash-commit> -b <nome_novo_branch>
```

**Criar branch sem trocar:**
```bash
git branch <novo-branch>
```

**Criar branch de rastreamento:**
```bash
git branch --track <novo-branch> <branch-remoto>
```

### Operações de Branch

**Obter arquivo único de branch diferente:**
```bash
git checkout <branch> -- <nomearquivo>
```

**Aplicar commit específico de outro branch:**
```bash
git cherry-pick <hash commit>
```

**Renomear branch atual:**
```bash
git branch -m <nome_novo_branch>
```

**Deletar branch local:**
```bash
git branch -d <branch>
```

**Forçar deleção de branch local:**
```bash
git branch -D <branch>
```
> ⚠️ **Aviso:** Você perderá mudanças não mescladas!

### Tags

**Criar tag no HEAD:**
```bash
git tag <nome-tag>
```

**Criar tag anotada:**
```bash
git tag -a <nome-tag>
```

**Criar tag com mensagem:**
```bash
git tag <nome-tag> -am 'mensagem aqui'
```

**Listar todas as tags:**
```bash
git tag
```

**Listar tags com mensagens:**
```bash
git tag -n
```

---

## 🔄 Atualizar e Publicar

### Gerenciamento de Remotos

**Listar remotos configurados:**
```bash
git remote -v
```

**Mostrar informações do remoto:**
```bash
git remote show <remoto>
```

**Adicionar novo remoto:**
```bash
git remote add <remoto> <url>
```

**Renomear remoto:**
```bash
git remote rename <remoto> <novo_remoto>
```

**Remover remoto:**
```bash
git remote rm <remoto>
```
> ℹ️ **Nota:** Isso apenas remove a referência remota localmente, não o repositório remoto em si.

### Fetch e Pull

**Baixar mudanças sem mesclar:**
```bash
git fetch <remoto>
```

**Baixar e mesclar mudanças:**
```bash
git pull <remoto> <branch>
```

**Obter mudanças do branch principal:**
```bash
git pull origin master
```

**Pull com rebase:**
```bash
git pull --rebase <remoto> <branch>
```

### Push e Publicar

**Publicar mudanças locais:**
```bash
git push <remoto> <branch>
```

**Deletar branch remoto:**
```bash
# Git v1.7.0+
git push <remoto> --delete <branch>

# Git v1.5.0+
git push <remoto> :<branch>
```

**Publicar tags:**
```bash
git push --tags
```

---

## 🔀 Merge e Rebase

### Operações de Merge

**Mesclar branch no HEAD atual:**
```bash
git merge <branch>
```

**Configurar ferramenta de merge globalmente:**
```bash
git config --global merge.tool meld
```

**Usar ferramenta de merge configurada:**
```bash
git mergetool
```

### Operações de Rebase

> ⚠️ **Aviso:** Não faça rebase de commits publicados!

**Fazer rebase do HEAD atual sobre branch:**
```bash
git rebase <branch>
```

**Abortar rebase:**
```bash
git rebase --abort
```

**Continuar rebase após resolver conflitos:**
```bash
git rebase --continue
```

### Resolução de Conflitos

**Marcar arquivo como resolvido:**
```bash
git add <arquivo-resolvido>
```

**Remover arquivo resolvido:**
```bash
git rm <arquivo-resolvido>
```

### Squashing Commits

**Rebase interativo para squashing:**
```bash
git rebase -i <commit-logo-antes-do-primeiro>
```

**Exemplo de configuração para squash:**
```
# Antes
pick <commit_id>
pick <commit_id2>
pick <commit_id3>

# Depois (squash commit_id2 e commit_id3 em commit_id)
pick <commit_id>
squash <commit_id2>
squash <commit_id3>
```

---

## ↩️ Desfazer

### Descartar Mudanças

**Descartar todas as mudanças locais:**
```bash
git reset --hard HEAD
```

**Tirar todos os arquivos da área de staging:**
```bash
git reset HEAD
```

**Descartar mudanças em arquivo específico:**
```bash
git checkout HEAD <arquivo>
```

### Operações de Reset

**Reset para commit anterior (descartar todas as mudanças):**
```bash
git reset --hard <commit>
```

**Reset para estado do branch remoto:**
```bash
git reset --hard <remoto/branch>
# Exemplo: git reset --hard upstream/master
```

**Reset preservando mudanças como não preparadas:**
```bash
git reset <commit>
```

**Reset preservando mudanças locais não commitadas:**
```bash
git reset --keep <commit>
```

### Reverter Commits

**Reverter commit (criar novo commit com mudanças opostas):**
```bash
git revert <commit>
```

### Limpar Arquivos Ignorados

**Remover arquivos acidentalmente commitados que deveriam ser ignorados:**
```bash
git rm -r --cached .
git add .
git commit -m "remover arquivos ignorados"
```

---

## 🌊 Git Flow

**Git-flow melhorado:** [git-flow-avh](https://github.com/petervanderdoes/gitflow-avh)

### 📋 Índice
- [🔧 Configuração](#configuração-1)
- [🚀 Começando](#começando)
- [✨ Features](#features)
- [🎁 Fazer um Release](#fazer-um-release)
- [🔥 Hotfixes](#hotfixes)
- [📊 Resumo de Comandos](#resumo-de-comandos)

---

### 🔧 Configuração {#configuração-1}

> **Pré-requisito:** Instalação do Git funcionando é necessária. Git-flow funciona no macOS, Linux e Windows.

**macOS (Homebrew):**
```bash
brew install git-flow-avh
```

**macOS (MacPorts):**
```bash
port install git-flow
```

**Linux (baseado em Debian):**
```bash
sudo apt-get install git-flow
```

**Windows (Cygwin):**
> Requer wget e util-linux
```bash
wget -q -O - --no-check-certificate https://raw.githubusercontent.com/petervanderdoes/gitflow/develop/contrib/gitflow-installer.sh install <state> | bash
```

---

### 🚀 Começando

Git-flow precisa de inicialização para personalizar a configuração do seu projeto.

**Inicializar (interativo):**
```bash
git flow init
```
> Você responderá perguntas sobre convenções de nomenclatura de branches. Valores padrão são recomendados.

**Inicializar (usar padrões):**
```bash
git flow init -d
```

---

### ✨ Features

Features são para desenvolver nova funcionalidade para próximos releases. Tipicamente existem apenas em repositórios de desenvolvedores.

**Iniciar novo feature:**
```bash
git flow feature start MEUFEATURE
```
> Cria branch de feature baseado em 'develop' e troca para ele

**Finalizar feature:**
```bash
git flow feature finish MEUFEATURE
```
> Isso fará:
> 1. Mesclar MEUFEATURE em 'develop'
> 2. Remover o branch de feature
> 3. Trocar de volta para 'develop'

**Publicar feature (para colaboração):**
```bash
git flow feature publish MEUFEATURE
```

**Obter feature publicado:**
```bash
git flow feature pull origin MEUFEATURE
```

**Rastrear feature de origem:**
```bash
git flow feature track MEUFEATURE
```

---

### 🎁 Fazer um Release

Releases suportam preparação de novos releases de produção, permitindo correções menores de bugs e preparando meta-dados.

**Iniciar release:**
```bash
git flow release start RELEASE [BASE]
```
> Cria branch de release a partir de 'develop'. Opcionalmente especifique commit SHA-1 [BASE].

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
> Isso fará:
> 1. Mesclar branch de release em 'master'
> 2. Taggar o release
> 3. Mesclar release de volta em 'develop'
> 4. Remover branch de release

> 💡 **Não esqueça:** Envie suas tags com `git push --tags`

---

### 🔥 Hotfixes

Hotfixes abordam problemas críticos em versões de produção ao vivo. Eles se ramificam da tag correspondente no master.

**Iniciar hotfix:**
```bash
git flow hotfix start VERSAO [NOMEBASE]
```

**Finalizar hotfix:**
```bash
git flow hotfix finish VERSAO
```
> Mescla de volta em 'develop' e 'master', e tagga o merge do master

---

### 📊 Resumo de Comandos

<p align="center">
    <img alt="Comandos Git Flow" src="../Img/git-flow-commands.png" height="270" width="460">
</p>

### 🌊 Esquema do Git Flow

<p align="center">
    <img alt="Esquema Git Flow" src="../Img/git-flow-commands-without-flow.png">
</p>

---


## 🌍 Outros Idiomas

Esta folha de dicas está disponível em múltiplos idiomas:

| Idioma | Link |
|--------|------|
| 🇺🇸 Inglês | [README.md](../README.md) |
| 🇸🇦 Árabe | [git-cheat-sheet-ar.md](./git-cheat-sheet-ar.md) |
| 🇧🇩 Bengali | [git-cheat-sheet-bn.md](./git-cheat-sheet-bn.md) |
| 🇨🇳 Chinês | [git-cheat-sheet-zh.md](./git-cheat-sheet-zh.md) |
| 🇩🇪 Alemão | [git-cheat-sheet-de.md](./git-cheat-sheet-de.md) |
| 🇪🇸 Espanhol | [git-cheat-sheet-es.md](./git-cheat-sheet-es.md) |
| 🇬🇷 Grego | [git-cheat-sheet-el.md](./git-cheat-sheet-el.md) |
| 🇮🇳 Hindi | [git-cheat-sheet-hi.md](./git-cheat-sheet-hi.md) |
| 🇰🇷 Coreano | [git-cheat-sheet-ko.md](./git-cheat-sheet-ko.md) |
| 🇧🇷 **Português (Brasil)** | **atual** |
| 🇵🇱 Polonês | [git-cheat-sheet-pl.md](./git-cheat-sheet-pl.md) |
| 🇹🇷 Turco | [git-cheat-sheet-tr.md](./git-cheat-sheet-tr.md) |

---

## 🤝 Contribuir

Damos as boas-vindas a contribuições! Você pode:

- 🐛 Reportar bugs ou erros de digitação
- ✨ Adicionar novos comandos Git
- 🌍 Traduzir para novos idiomas
- 💡 Melhorar explicações
- 📝 Aprimorar formatação

**Como contribuir:**
1. Faça fork deste repositório
2. Crie seu branch de feature (`git checkout -b feature/FeatureIncrivel`)
3. Faça commit das suas mudanças (`git commit -m 'Adicionar alguma FeatureIncrivel'`)
4. Faça push para o branch (`git push origin feature/FeatureIncrivel`)
5. Abra um Pull Request

---

## 📄 Licença

Este projeto é código aberto e está disponível sob a [Licença MIT](LICENSE).

---

<p align="center">
    <b>⭐ Dê uma estrela neste repositório se foi útil!</b>
</p>
