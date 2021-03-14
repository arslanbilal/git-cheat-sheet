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

## 병합 & 리베이스

##### 현재 HEAD로 브랜치 병합:
```
$ git merge <branch>
```

##### 현재 HEAD에 &lt;branch&gt;로 리베이스:<br>
<em><sub>Don't rebase published commit!</sub></em>

```
$ git rebase <branch>
```

##### 리베이스 중단:
```
$ git rebase --abort
```

##### 충돌 해결 후 리베이스 재개:
```
$ git rebase --continue
```

##### 편집기를 사용하여 수동으로 충돌을 해결하고 해당 파일에 표시:
```
$ git add <resolved-file>
```

```
$ git rm <resolved-file>
```

##### 커밋들을 압축:
```
$ git rebase -i <commit-just-before-first>
```

이제 이걸

```
pick <commit_id>
pick <commit_id2>
pick <commit_id3>
```

이렇게 바꿉니다,

```
pick <commit_id>
squash <commit_id2>
squash <commit_id3>
```
<hr>

## 실행 취소

##### 작업 디렉터리의 모든 로컬 변경사항 취소:
```
$ git reset --hard HEAD
```

##### Staging 영역에서 모든 파일 빼내기 (즉 마지막 `git add`를 실행 취소):
```
$ git reset HEAD
```

##### 특정 파일의 로컬 변경사항 취소:
```
$ git checkout HEAD <file>
```

##### 커밋 되돌리기 (되돌리기 위한 변경사항을 포함하는 새 커밋을 생성함):
```
$ git revert <commit>
```

##### HEAD 포인터를 이전 커밋으로 재설정하고 그 이후의 모든 변경 사항을 삭제:
```
$ git reset --hard <commit>
```

##### HEAD 포인터를 원격 브랜치의 현재 상태로 재설정:
```
$ git reset --hard <remote/branch> e.g., upstream/master, origin/my-feature
```

##### HEAD 포인터를 이전 커밋으로 재설정하고 모든 변경사항을 Unstaging 상태로 유지:
```
$ git reset <commit>
```

##### HEAD 포인터를 이전 커밋으로 재설정하고 커밋되지 않은 로컬 변경사항 유지:
```
$ git reset --keep <commit>
```

##### .gitignore에 추가되기 전에 실수로 커밋된 파일 제거:
```
$ git rm -r --cached .
$ git add .
$ git commit -m "remove xyz file"
```
<hr>

## Git-Flow
개선된 [Git-flow](https://github.com/petervanderdoes/gitflow-avh)

### 인덱스
* [설정](#setup)
* [시작하기](#getting-started)
* [기능](#features)
* [릴리즈 생성](#make-a-release)
* [핫픽스](#hotfixes)
* [명령어들](#commands)

<hr>

### 설정
###### 필수 구성 요소로 Git을 설치해야 합니다. Git 플로우는 OSX, 리눅스 및 윈도우즈에서 작동합니다.

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
###### git-flow를 설치하기 위해서는 wget과 util-linux가 필요합니다.
```bash
$ wget -q -O - --no-check-certificate https://raw.githubusercontent.com/petervanderdoes/gitflow/develop/contrib/gitflow-installer.sh install <state> | bash
```
<hr>

### 시작하기
###### 프로젝트 설정을 커스텀하려면 Git 플로우를 초기화해야합니다. 기존 git 리포지토리 내에서 초기화하여 git-flow 사용을 시작하십시오:
##### 초기화:
###### 브랜치의 이름 규칙에 관한 몇 가지 질문에 답해야합니다. 기본값을 사용하는 것이 좋습니다.
```shell
git flow init
```
혹은
###### 기본값 사용
```shell
git flow init -d
```
<hr>

### 기능
###### 릴리즈를위한 새로운 기능을 개발하십시오. 일반적으로 개발자 리포지토리에만 존재합니다.
##### 새로운 기능 시작:
###### 이 작업은 'develop'을 기반으로 새 기능 브랜치를 만들고 전환합니다.
```
git flow feature start MYFEATURE
```

##### 기능 완료:
###### 기능 개발을 완료합니다. 이 작업은 다음을 수행합니다:
###### 1) MYFEATURE를 'develop'에 병합.
###### 2) 기능 브랜치를 제거.
###### 3) 'develop' 브랜치로 재전환
```
git flow feature finish MYFEATURE
```

##### 기능 배포:
###### 공동으로 기능을 개발하고 있습니까? 다른 사용자가 사용할 수 있도록 기능을 원격 서버에 배포합니다.
```
git flow feature publish MYFEATURE
```

##### 배포된 기능 가져오기:
###### 다른 사용자에 의해 배포된 기능을 가져오기.
```
git flow feature pull origin MYFEATURE
```

##### 오리진 기능 추적:
###### 다음을 통해서 오리진의 기능을 추적할 수 있습니다.
```
git flow feature track MYFEATURE
```
<hr>

### 릴리즈 생성
###### 새로운 프로덕션 릴리즈 준비를 지원하고 사소한 버그 수정 및 릴리즈를위한 메타 데이터 준비를 허용합니다.

##### 릴리즈 시작:
###### 릴리스를 시작하려면 git flow release 명령을 사용하십시오. 'develop'브랜치에서 생성 된 릴리즈 브랜치를 생성합니다. 릴리즈를 시작할 [BASE] 커밋 sha-1 해시를 선택적으로 제공 할 수 있습니다. 커밋은 'develop'브랜치에 있어야합니다. 
```
git flow release start RELEASE [BASE]
```
###### 다른 개발자의 릴리즈 커밋을 허용하도록 릴리스 브랜치를 만든 후 배포하는 것이 좋습니다. 다음 명령을 사용하여 기능 배포와 유사하게 수행하십시오. 
```
git flow release publish RELEASE
```
###### (이 명령어를 통해 리모트 릴리즈를 추적할 수 있습니다: ```git flow release track RELEASE```)

##### 릴리즈 완료:
###### 릴리즈를 완료하는 것은 깃 브랜치의 중요한 단계 중 하나입니다. 이것은 몇 가지 작업을 수행합니다:
###### 1) 릴리즈 브랜치를 'master'브랜치로 다시 병합합니다
###### 2) 릴리즈에 이름으로 태그 지정
###### 3) 릴리즈를 'develop'로 역으로 병합
###### 4) 릴리즈 브랜치 삭제
```
git flow release finish RELEASE
```
###### ```git push --tags```로 태그를 푸시하는 것을 잊지마세요 

<hr>

### 핫픽스
###### 핫픽스는 라이브 프로덕션 버전의 원치 않는 상태에 즉시 대응해야 하는 필요성 때문에 발생합니다. 프로덕션 버전을 표시하는 마스터 브랜치의 해당 태그에서 분기될 수 있습니다. 

##### 깃 플로우 핫픽스 시작:
###### 다른 깃 플로우 명령어처럼 핫픽스는 다음으로 시작됩니다
```
$ git flow hotfix start VERSION [BASENAME]
```
###### 위 명령어의 버전 인수를 통해 새로운 릴리즈 이름을 표시합니다. 선택적으로 시작할 기본 이름을 설정할 수 있습니다.

##### 핫픽스 완료:
###### 핫픽스를 완료하면 다시 develop/master 브랜치로 병합됩니다. 또한 마스터 병합에는 핫픽스 버전 태그가 지정됩니다.
```
git flow hotfix finish VERSION
```
<hr>

### 명령어
<p align="center">
    <img alt="Git" src="./Img/git-flow-commands.png" height="270" width="460">
</p>
<hr>

### 깃 플로우 스키마

<p align="center">
    <img alt="Git" src="Img/git-flow-commands-without-flow.png">
</p>
<hr>
