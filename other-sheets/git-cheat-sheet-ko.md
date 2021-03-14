Git and Git Flow Cheat Sheet [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome) [![Build Status](https://travis-ci.org/arslanbilal/git-cheat-sheet.svg?branch=master)](https://travis-ci.org/arslanbilal/git-cheat-sheet)
===============
<hr>
<p align="center">
    <img alt="Git" src="./Img/git-logo.png" height="190" width="455">
</p>
<hr>

# Other Available Languages:

1. [Arabic Git Cheat Sheet](https://github.com/arslanbilal/git-cheat-sheet/blob/master/other-sheets/git-cheat-sheet-ar.md)
2. [Chinese Git Cheat Sheet](https://github.com/arslanbilal/git-cheat-sheet/blob/master/other-sheets/git-cheat-sheet-zh.md)
3. [Hindi Git Cheat Sheet](https://github.com/arslanbilal/git-cheat-sheet/blob/master/other-sheets/git-cheat-sheet-hi.md)
4. [Turkish Git Cheat Sheet](https://github.com/arslanbilal/git-cheat-sheet/blob/master/other-sheets/git-cheat-sheet-tr.md)
5. [Spanish Git Cheat Sheet](https://github.com/arslanbilal/git-cheat-sheet/blob/master/other-sheets/git-cheat-sheet-es.md)
6. [Greek Git Cheat Sheet](https://github.com/arslanbilal/git-cheat-sheet/blob/master/other-sheets/git-cheat-sheet-el.md)
6. [Korean Git Cheat Sheet](https://github.com/arslanbilal/git-cheat-sheet/blob/master/other-sheets/git-cheat-sheet-ko.md)

깃 치트시트는 당신이 모든 명령어를 외우는 일로부터 벗어나게 해드립니다.

언제든지 기여하고 문법 실수들을 업데이트하세요. 또한 언어 파일을 자유롭게 추가할 수 있습니다.

<hr>

깃 치트시트 한국어
===============
### Index
* [설정](#setup)
* [설정 파일들](#configuration-files)
* [생성](#create)
* [로컬 수정사항](#local-changes)
* [검색](#search)
* [커밋 히스토리](#commit-history)
* [브랜치 & 태그](#branches--tags)
* [업데이트 & 배포](#update--publish)
* [머지 & 리베이스](#merge--rebase)
* [되돌리기](#undo)
* [깃 플로우](#git-flow)


<hr>

## 설정

##### 현재 설정 구성 보기:
```
$ git config --list
```
##### 현재 리포지토리 설정 구성 보기:
```
$ git config --local --list
```

##### 글로벌 설정 구성 보기:
```
$ git config --global --list
```

##### 시스템 설정 구성 보기:
```
$ git config --system --list
```

##### 버전 히스토리 검토할 때 크레딧에 식별 가능한 이름을 설정:
```
$ git config --global user.name “[firstname lastname]”
```

##### 각 히스토리 마커와 연결할 이메일 주소 설정:
```
$ git config --global user.email “[valid-email]”
```

##### 쉬운 리뷰를 위해서 깃의 자동 명령줄 색 설정:
```
$ git config --global color.ui auto
```

##### 커밋에 대한 글로벌 에디터 설정:
```
$ git config --global core.editor vi
```

<hr>

## 설정 파일

##### 특정 리포지토리 설정 파일 [--local]:
```
<repo>/.git/config
```

##### 특정 유저 설정 파일 [--global]:
```
~/.gitconfig
```

##### 시스템 전체 설정 파일 [--system]:
```
/etc/gitconfig
```

<hr>

## 생성

##### 기존 리포지토리 복제:

2가지 방법이 있습니다:

SSH를 통해

```
$ git clone ssh://user@domain.com/repo.git
```

HTTP를 통해

```
$ git clone http://domain.com/user/repo.git
```

##### 현재 디렉터리에 새로운 로컬 리포지토리 생성:
```
$ git init
```

##### 특정 디렉터리에 새로운 로컬 리포지토리 생성:
```
$ git init <directory>
```

<hr>

## 로컬 수정

##### 작업 디렉터리 변경사항:
```
$ git status
```

##### 추적된 파일들의 변경사항:
```
$ git diff
```

##### 특정 파일의 변경사항/차이 확인:
```
$ git diff <file>
```

##### 모든 현재 변경사항을 다음 커밋에 추가:
```
$ git add .
```

##### \<file>의 일부 변경사항을 다음 커밋에 추가:
```
$ git add -p <file>
```

##### 추적되는 파일들의 모든 로컬 변경사항을 커밋:
```
$ git commit -a
```

##### 이전에 stage된 변경사항을 커밋:
```
$ git commit
```

##### 메시지와 함께 커밋:
```
$ git commit -m 'message here'
```

##### Staging 영역 건너뛰기 및 메시지 추가하여 커밋:
```
$ git commit -am 'message here'
```

##### 과거 날짜에 커밋:
```
$ git commit --date="`date --date='n day ago'`" -am "<Commit Message Here>"
```

##### 마지막 커밋 수정:<br>
<em><sub>이미 배포된 커밋을 수정하지 마세요!</sub></em>

```
$ git commit -a --amend
```

##### 이전 로그 메시지를 사용하여 마지막 커밋 수정:
<em><sub>이미 배포된 커밋을 수정하지 마세요!</sub></em>

```shell
$ git commit --amend --no-edit
```

##### 마지막 커밋의 커밋 작성자 날짜 수정:
```
GIT_COMMITTER_DATE="date" git commit --amend
```

##### 마지막 커밋의 작성자 날짜 수정:
```shell
$ git commit --amend --date="date"
```

##### 현재 브랜치의 커밋되지 않은 변경사항을 다른 브랜치로 이동:<br>
```
$ git stash
$ git checkout branch2
$ git stash pop
```

##### 보관된 변경사항을 현재 브랜치로 복원:
```shell
$ git stash apply
```

#### 보관된 특정 변경사항을 현재 브랜치로 복원:
- `git stash list`를 통해 *{stash_number}* 를 얻을 수 있습니다. 

```shell
$ git stash apply stash@{stash_number}
```

##### 마지막으로 보관된 변경사항을 제거:
```
$ git stash drop
```

<hr>

## 검색

##### 디렉터리에 있는 모든 파일에서 텍스트 검색:
```
$ git grep "Hello"
```

##### 버전에서 텍스트 검색:
```
$ git grep "Hello" v2.5
```

<hr>

## 커밋 히스토리

##### 모든 커밋 표시, 가장 최신 커밋부터(커밋 해시, 작성자 정보, 커밋 날짜, 커밋 제목 포함):
```
$ git log
```

##### 모든 커밋 표시 (커밋 해시와 커밋 메시지 포함):
```
$ git log --oneline
```

##### 특정 유저의 모든 커밋 표시:
```
$ git log --author="username"
```

##### 특정 파일에 대한 시간 경과에 따른 변경사항 표시:
```
$ git log -p <file>
```

##### 현재 오른쪽 remote 브랜치에만 있는 커밋 표시:
```
$ git log --oneline <origin/master>..<remote/master> --left-right
```

##### &lt;file&gt;에 대한 변경자, 변경사항 그리고 변경일자 표시:
```
$ git blame <file>
```

##### 참조 로그 표시:
```
$ git reflog show
```

##### 참조 로그 삭제:
```
$ git reflog delete
```
<hr>

## 이동 / 이름 수정

##### 파일 이름 수정:

Index.txt에서 Index.html로 이름 바꾸기

```
$ git mv Index.txt Index.html
```

<hr>

## 브랜치 & 태그

##### 모든 로컬 브랜치 목록:
```
$ git branch
```

#### 모든 로컬/원격 브랜치 목록
```
$ git branch -a
```

##### 모든 원격 브랜치 목록:
```
$ git branch -r
```

##### HEAD 브랜치 전환:
```
$ git checkout <branch>
```

##### 다른 브랜치에서 단일 파일 Checkout:
```
$ git checkout <branch> -- <filename>
```

##### 새로운 브랜치 생성 후 HEAD 브랜치 전환:
```
$ git checkout -b <branch>
```


##### 기존 특정 브랜치에서 새로운 브랜치 생성하고 브랜치 전환:
```
$ git checkout -b <new_branch> <existing_branch>
```


#### 기존 특정 커밋에서 브랜치 생성 후 브랜치 전환:
```
$ git checkout <commit-hash> -b <new_branch_name>
```


##### 현재 HEAD 브랜치 기준으로 새 브랜치 생성:
```
$ git branch <new-branch>
```

##### 원격 브랜치를 기반으로 새로운 추적 브랜치 생성:
```
$ git branch --track <new-branch> <remote-branch>
```

##### 로컬 브랜치 삭제:
```
$ git branch -d <branch>
```

##### 현재 브랜치 이름 변경:
```shell
$ git branch -m <new_branch_name>
```

##### 로컬 브랜치 강제 삭제:
<em><sub>머지되지 않은 변경사항을 잃게 됩니다!</sub></em>

```
$ git branch -D <branch>
```

##### `HEAD`에 태그 추가:
```
$ git tag <tag-name>
```

##### `HEAD`에 태그를 추가하고 메시지를 포함할 에디터 열기:
```
$ git tag -a <tag-name>
```

##### `HEAD`에 메시지를 포함하는 태그 추가:
```
$ git tag <tag-name> -am 'message here'
```

##### 모든 태그 목록:
```
$ git tag
```

##### 메시지 (태그 메시지, 없다면 커밋 메시지)와 함께 모든 태그 목록 표시:
```
$ git tag -n
```

<hr>

## 업데이트 & 배포

##### 현재 구성된 모든 원격 목록 표시:
```
$ git remote -v
```

##### 특정 원격 정보 표시:
```
$ git remote show <remote>
```

##### 이름 &lt;remote&gt; 새로운 원격 리포지토리 추가:
```
$ git remote add <remote> <url>
```

##### &lt;remote&gt;에서 &lt;new_remote&gt;로 원격 리포지토리의 이름 수정:
```
$ git remote rename <remote> <new_remote>
```

##### 특정 원격 삭제:
```
$ git remote rm <remote>
```

<em><sub>알림: git remote rm 은 서버의 원격 리포지토리를 삭제하지 않습니다. 단순히 리모트와 참조를 로컬 리포지토리에서부터 삭제만 합니다.</sub></em>

##### &lt;remote&gt;에서 모든 변경사항 다운로드하지만 HEAD와 통합하지 않음:
```
$ git fetch <remote>
```

##### 변경사항을 다운로드하고 HEAD와 병합:
```
$ git remote pull <remote> <url>
```

##### HEAD에서 로컬 리포지토리로 모든 변경사항을 가져옴:   
```
$ git pull origin master
```

##### 병합하지 않고 HEAD에서 로컬 리포지토리로 모든 변경사항을 가져옴:
```
$ git pull --rebase <remote> <branch>
```

##### 로컬 변경사항을 리모트에 배포:
```
$ git push remote <remote> <branch>
```

##### 리모트에서 브랜치 삭제:
```
$ git push <remote> :<branch> (since Git v1.5.0)
```
혹은
```
$ git push <remote> --delete <branch> (since Git v1.7.0)
```

##### 태그 배포:
```
$ git push --tags
```
<hr>

#### 병합 툴(편집기)을 글로벌 설정
```bash
$ git config --global merge.tool meld
```

##### 구성된 병합 툴로 충돌 해결:
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

##### Use your editor to manually solve conflicts and (after resolving) mark file as resolved:
```
$ git add <resolved-file>
```

```
$ git rm <resolved-file>
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

##### Discard all local changes in your working directory:
```
$ git reset --hard HEAD
```

##### Get all the files out of the staging area(i.e. undo the last `git add`):
```
$ git reset HEAD
```

##### Discard local changes in a specific file:
```
$ git checkout HEAD <file>
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

##### Remove files that were accidentally committed before they were added to .gitignore
```
$ git rm -r --cached .
$ git add .
$ git commit -m "remove xyz file"
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
