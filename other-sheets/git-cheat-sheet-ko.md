# Git과 Git Flow 치트 시트
[![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

<p align="center">
    <img alt="Git" src="../Img/git-logo.png" height="190" width="455">
</p>

---

## 📖 소개

이 포괄적인 Git 치트 시트는 모든 Git 명령어를 외우지 않고도 Git을 마스터할 수 있도록 도와줍니다. 초보자든 숙련된 개발자든, 이 가이드는 필수적인 Git 작업에 대한 빠른 참조를 제공합니다.

**기여를 환영합니다!** 자유롭게:
- 문법 오류 수정
- 새로운 명령어 추가
- 다른 언어로 번역
- 설명 개선

---
## 📋 목차

- [🔧 설정](#-설정)
- [⚙️ 설정 파일](#️-설정-파일)
- [🆕 저장소 생성](#-저장소-생성)
- [📝 로컬 변경사항](#-로컬-변경사항)
- [🔍 검색](#-검색)
- [📖 커밋 히스토리](#-커밋-히스토리)
- [📁 이동 / 이름 변경](#-이동--이름-변경)
- [🌿 브랜치와 태그](#-브랜치와-태그)
- [🔄 업데이트와 발행](#-업데이트와-발행)
- [🔀 머지와 리베이스](#-머지와-리베이스)
- [↩️ 되돌리기](#️-되돌리기)
- [🌊 Git Flow](#-git-flow)
- [🌍 다른 언어](#-다른-언어)

---

## 🔧 설정

### 설정 확인

**현재 설정 보기:**
```bash
git config --list
```

**저장소 설정 보기:**
```bash
git config --local --list
```

**전역 설정 보기:**
```bash
git config --global --list
```

**시스템 설정 보기:**
```bash
git config --system --list
```

### 사용자 설정

**버전 기록에 사용할 이름 설정:**
```bash
git config --global user.name "[firstname lastname]"
```

**이메일 주소 설정:**
```bash
git config --global user.email "[valid-email]"
```

### 표시 및 에디터 설정

**자동 명령줄 색상 표시 활성화:**
```bash
git config --global color.ui auto
```

**커밋용 전역 에디터 설정:**
```bash
git config --global core.editor vi
```

---

## ⚙️ 설정 파일

| 범위 | 위치 | 명령어 플래그 |
|------|------|--------------|
| **저장소** | `<repo>/.git/config` | `--local` |
| **사용자** | `~/.gitconfig` | `--global` |
| **시스템** | `/etc/gitconfig` | `--system` |

---

## 🆕 저장소 생성

### 기존 저장소 복제

**SSH를 통해:**
```bash
git clone ssh://user@domain.com/repo.git
```

**HTTPS를 통해:**
```bash
git clone https://domain.com/user/repo.git
```

### 새 저장소 초기화

**현재 디렉토리에 저장소 생성:**
```bash
git init
```

**특정 디렉토리에 저장소 생성:**
```bash
git init <directory>
```

---

## 📝 로컬 변경사항

### 상태 및 차이점 확인

**작업 디렉토리 상태 보기:**
```bash
git status
```

**추적 파일의 변경사항 보기:**
```bash
git diff
```

**특정 파일의 변경사항 보기:**
```bash
git diff <file>
```

### 변경사항 스테이징

**모든 현재 변경사항 추가:**
```bash
git add .
```

**특정 파일 추가:**
```bash
git add <filename1> <filename2>
```

**파일의 일부를 대화형으로 추가:**
```bash
git add -p <file>
```

### 변경사항 커밋

**추적된 모든 파일의 변경사항 커밋:**
```bash
git commit -a
```

**스테이징된 변경사항 커밋:**
```bash
git commit
```

**메시지와 함께 커밋:**
```bash
git commit -m 'message here'
```

**스테이징 건너뛰고 메시지와 함께 커밋:**
```bash
git commit -am 'message here'
```

**특정 날짜로 커밋:**
```bash
git commit --date="`date --date='n day ago'`" -am "<Commit Message Here>"
```

### 마지막 커밋 수정

> ⚠️ **경고:** 발행된 커밋은 수정하지 마세요!

**마지막 커밋 수정:**
```bash
git commit -a --amend
```

**커밋 메시지를 변경하지 않고 수정:**
```bash
git commit --amend --no-edit
```

**커미터 날짜 변경:**
```bash
GIT_COMMITTER_DATE="date" git commit --amend
```

**작성자 날짜 변경:**
```bash
git commit --amend --date="date"
```

### 변경사항 스태시

**현재 변경사항 임시 저장:**
```bash
git stash
```

**마지막으로 스태시한 변경사항 적용:**
```bash
git stash apply
```

**특정 스태시 적용:**
```bash
git stash apply stash@{stash_number}
```
> `git stash list`를 사용하여 사용 가능한 스태시 확인

**마지막 스태시 제거:**
```bash
git stash drop
```

**커밋되지 않은 변경사항을 다른 브랜치로 이동:**
```bash
git stash
git checkout branch2
git stash pop
```

---

## 🔍 검색

### 텍스트 검색

**모든 파일에서 텍스트 검색:**
```bash
git grep "Hello"
```

**특정 버전에서 검색:**
```bash
git grep "Hello" v2.5
```

### 커밋 검색

**특정 키워드를 도입한 커밋 찾기:**
```bash
git log -S 'keyword'
```

**정규표현식으로 검색:**
```bash
git log -S 'keyword' --pickaxe-regex
```

---

## 📖 커밋 히스토리

### 기본 히스토리

**모든 커밋 보기 (상세):**
```bash
git log
```

**커밋 보기 (한 줄씩):**
```bash
git log --oneline
```

**특정 작성자의 커밋 보기:**
```bash
git log --author="username"
```

**특정 파일의 변경사항 보기:**
```bash
git log -p <file>
```

### 고급 히스토리

**브랜치 비교:**
```bash
git log --oneline <origin/master>..<remote/master> --left-right
```

**누가 언제 무엇을 변경했는지 보기:**
```bash
git blame <file>
```

### 참조 로그

**참조 로그 보기:**
```bash
git reflog show
```

**참조 로그 삭제:**
```bash
git reflog delete
```

---

## 📁 이동 / 이름 변경

**파일 이름 변경:**
```bash
git mv Index.txt Index.html
```

---

## 🌿 브랜치와 태그

### 브랜치 목록

**로컬 브랜치 목록:**
```bash
git branch
```

**모든 브랜치 목록 (로컬 + 원격):**
```bash
git branch -a
```

**원격 브랜치 목록:**
```bash
git branch -r
```

**머지된 브랜치 목록:**
```bash
git branch --merged
```

### 브랜치 전환 및 생성

**기존 브랜치로 전환:**
```bash
git checkout <branch>
```

**새 브랜치를 생성하고 전환:**
```bash
git checkout -b <branch>
```

**이전 브랜치로 전환:**
```bash
git checkout -
```

**기존 브랜치에서 새 브랜치 생성:**
```bash
git checkout -b <new_branch> <existing_branch>
```

**특정 커밋에서 브랜치 생성:**
```bash
git checkout <commit-hash> -b <new_branch_name>
```

**전환 없이 브랜치 생성:**
```bash
git branch <new-branch>
```

**추적 브랜치 생성:**
```bash
git branch --track <new-branch> <remote-branch>
```

### 브랜치 작업

**다른 브랜치에서 단일 파일 체크아웃:**
```bash
git checkout <branch> -- <filename>
```

**다른 브랜치의 특정 커밋 적용:**
```bash
git cherry-pick <commit hash>
```

**현재 브랜치 이름 변경:**
```bash
git branch -m <new_branch_name>
```

**로컬 브랜치 삭제:**
```bash
git branch -d <branch>
```

**로컬 브랜치 강제 삭제:**
```bash
git branch -D <branch>
```
> ⚠️ **경고:** 머지되지 않은 변경사항이 손실됩니다!

### 태그

**HEAD에 태그 생성:**
```bash
git tag <tag-name>
```

**주석이 달린 태그 생성:**
```bash
git tag -a <tag-name>
```

**메시지와 함께 태그 생성:**
```bash
git tag <tag-name> -am 'message here'
```

**모든 태그 목록:**
```bash
git tag
```

**메시지와 함께 태그 목록:**
```bash
git tag -n
```

---

## 🔄 업데이트와 발행

### 원격 저장소 관리

**설정된 원격 저장소 목록:**
```bash
git remote -v
```

**원격 저장소 정보 보기:**
```bash
git remote show <remote>
```

**새 원격 저장소 추가:**
```bash
git remote add <remote> <url>
```

**원격 저장소 이름 변경:**
```bash
git remote rename <remote> <new_remote>
```

**원격 저장소 제거:**
```bash
git remote rm <remote>
```
> ℹ️ **참고:** 이 명령어는 로컬의 원격 참조만 제거하며, 원격 저장소 자체는 삭제하지 않습니다.

### 가져오기와 풀

**머지 없이 변경사항 다운로드:**
```bash
git fetch <remote>
```

**변경사항 다운로드 및 머지:**
```bash
git pull <remote> <branch>
```

**메인 브랜치의 변경사항 가져오기:**
```bash
git pull origin master
```

**리베이스와 함께 풀:**
```bash
git pull --rebase <remote> <branch>
```

### 푸시 및 발행

**로컬 변경사항 발행:**
```bash
git push <remote> <branch>
```

**원격 브랜치 삭제:**
```bash
# Git v1.7.0+
git push <remote> --delete <branch>

# Git v1.5.0+
git push <remote> :<branch>
```

**태그 발행:**
```bash
git push --tags
```

---

## 🔀 머지와 리베이스

### 머지 작업

**현재 HEAD에 브랜치 머지:**
```bash
git merge <branch>
```

**전역 머지 도구 설정:**
```bash
git config --global merge.tool meld
```

**설정된 머지 도구 사용:**
```bash
git mergetool
```

### 리베이스 작업

> ⚠️ **경고:** 발행된 커밋은 리베이스하지 마세요!

**현재 HEAD를 브랜치에 리베이스:**
```bash
git rebase <branch>
```

**리베이스 중단:**
```bash
git rebase --abort
```

**충돌 해결 후 리베이스 계속:**
```bash
git rebase --continue
```

### 충돌 해결

**파일을 해결됨으로 표시:**
```bash
git add <resolved-file>
```

**해결된 파일 제거:**
```bash
git rm <resolved-file>
```

### 커밋 스쿼시

**스쿼시를 위한 대화형 리베이스:**
```bash
git rebase -i <commit-just-before-first>
```

**스쿼시 설정 예시:**
```
# 이전
pick <commit_id>
pick <commit_id2>
pick <commit_id3>

# 이후 (commit_id2와 commit_id3를 commit_id에 스쿼시)
pick <commit_id>
squash <commit_id2>
squash <commit_id3>
```

---

## ↩️ 되돌리기

### 변경사항 폐기

**모든 로컬 변경사항 폐기:**
```bash
git reset --hard HEAD
```

**모든 파일 언스테이지:**
```bash
git reset HEAD
```

**특정 파일의 변경사항 폐기:**
```bash
git checkout HEAD <file>
```

### 리셋 작업

**이전 커밋으로 리셋 (모든 변경사항 폐기):**
```bash
git reset --hard <commit>
```

**원격 브랜치 상태로 리셋:**
```bash
git reset --hard <remote/branch>
# 예시: git reset --hard upstream/master
```

**변경사항을 언스테이지 상태로 보존하며 리셋:**
```bash
git reset <commit>
```

**커밋되지 않은 로컬 변경사항을 보존하며 리셋:**
```bash
git reset --keep <commit>
```

### 커밋 되돌리기

**커밋 되돌리기 (반대 변경사항으로 새 커밋 생성):**
```bash
git revert <commit>
```

### 무시된 파일 정리

**무시되어야 할 실수로 커밋된 파일 제거:**
```bash
git rm -r --cached .
git add .
git commit -m "remove ignored files"
```

---

## 🌊 Git Flow

**개선된 Git-flow:** [git-flow-avh](https://github.com/petervanderdoes/gitflow-avh)

### 📋 목차
- [🔧 설정](#setup-1)
- [🚀 시작하기](#getting-started)
- [✨ 기능](#features)
- [🎁 릴리스 만들기](#make-a-release)
- [🔥 핫픽스](#hotfixes)
- [📊 명령어 개요](#commands-overview)

---

### 🔧 설정 {#setup-1}

> **전제 조건:** 작동하는 Git 설치가 필요합니다. Git-flow는 macOS, Linux, Windows에서 작동합니다.

**macOS (Homebrew):**
```bash
brew install git-flow-avh
```

**macOS (MacPorts):**
```bash
port install git-flow
```

**Linux (Debian 기반):**
```bash
sudo apt-get install git-flow
```

**Windows (Cygwin):**
> wget과 util-linux가 필요합니다
```bash
wget -q -O - --no-check-certificate https://raw.githubusercontent.com/petervanderdoes/gitflow/develop/contrib/gitflow-installer.sh install <state> | bash
```

---

### 🚀 시작하기

Git-flow는 프로젝트 설정을 커스터마이즈하기 위해 초기화가 필요합니다.

**초기화 (대화형):**
```bash
git flow init
```
> 브랜치 명명 규칙에 대한 질문에 답하게 됩니다. 기본값을 권장합니다.

**초기화 (기본값 사용):**
```bash
git flow init -d
```

---

### ✨ 기능

기능은 향후 릴리스를 위한 새로운 기능을 개발하기 위한 것입니다. 일반적으로 개발자 저장소에만 존재합니다.

**새 기능 시작:**
```bash
git flow feature start MYFEATURE
```
> 'develop'을 기반으로 기능 브랜치를 생성하고 해당 브랜치로 전환합니다

**기능 완료:**
```bash
git flow feature finish MYFEATURE
```
> 이 명령어는:
> 1. MYFEATURE를 'develop'에 머지
> 2. 기능 브랜치 제거
> 3. 'develop'으로 다시 전환

**기능 발행 (협업용):**
```bash
git flow feature publish MYFEATURE
```

**발행된 기능 가져오기:**
```bash
git flow feature pull origin MYFEATURE
```

**원격 기능 추적:**
```bash
git flow feature track MYFEATURE
```

---

### 🎁 릴리스 만들기

릴리스는 새 프로덕션 릴리스 준비를 지원하며, 사소한 버그 수정과 메타데이터 준비를 허용합니다.

**릴리스 시작:**
```bash
git flow release start RELEASE [BASE]
```
> 'develop'에서 릴리스 브랜치를 생성합니다. 선택적으로 [BASE] 커밋 SHA-1을 지정할 수 있습니다.

**릴리스 발행:**
```bash
git flow release publish RELEASE
```

**원격 릴리스 추적:**
```bash
git flow release track RELEASE
```

**릴리스 완료:**
```bash
git flow release finish RELEASE
```
> 이 명령어는:
> 1. 릴리스 브랜치를 'master'에 머지
> 2. 릴리스에 태그 지정
> 3. 릴리스를 'develop'에 역머지
> 4. 릴리스 브랜치 제거

> 💡 **잊지 마세요:** `git push --tags`로 태그를 푸시하세요

---

### 🔥 핫픽스

핫픽스는 라이브 프로덕션 버전의 심각한 문제를 해결합니다. master의 해당 태그에서 브랜치됩니다.

**핫픽스 시작:**
```bash
git flow hotfix start VERSION [BASENAME]
```

**핫픽스 완료:**
```bash
git flow hotfix finish VERSION
```
> 'develop'과 'master' 모두에 역머지되고, master 머지에 태그가 지정됩니다

---

### 📊 명령어 개요

<p align="center">
    <img alt="Git Flow Commands" src="../Img/git-flow-commands.png" height="270" width="460">
</p>

### 🌊 Git Flow 스키마

<p align="center">
    <img alt="Git Flow Schema" src="../Img/git-flow-commands-without-flow.png">
</p>

---


## 🌍 다른 언어

이 치트 시트는 여러 언어로 제공됩니다:

| 언어 | 링크 |
|------|------|
| 🇸🇦 아랍어 | [git-cheat-sheet-ar.md](git-cheat-sheet-ar.md) |
| 🇧🇩 벵골어 | [git-cheat-sheet-bn.md](git-cheat-sheet-bn.md) |
| 🇧🇷 브라질 포르투갈어 | [git-cheat-sheet-pt_BR.md](git-cheat-sheet-pt_BR.md) |
| 🇨🇳 중국어 | [git-cheat-sheet-zh.md](git-cheat-sheet-zh.md) |
| 🇩🇪 독일어 | [git-cheat-sheet-de.md](git-cheat-sheet-de.md) |
| 🇬🇷 그리스어 | [git-cheat-sheet-el.md](git-cheat-sheet-el.md) |
| 🇮🇳 힌디어 | [git-cheat-sheet-hi.md](git-cheat-sheet-hi.md) |
| 🇰🇷 **한국어** (현재) | |
| 🇵🇱 폴란드어 | [git-cheat-sheet-pl.md](git-cheat-sheet-pl.md) |
| 🇪🇸 스페인어 | [git-cheat-sheet-es.md](git-cheat-sheet-es.md) |
| 🇹🇷 터키어 | [git-cheat-sheet-tr.md](git-cheat-sheet-tr.md) |

---

## 🤝 기여하기

기여를 환영합니다! 다음과 같이 할 수 있습니다:

- 🐛 버그나 오타 보고
- ✨ 새 Git 명령어 추가
- 🌍 새로운 언어로 번역
- 💡 설명 개선
- 📝 포맷 개선

**기여하는 방법:**
1. 이 저장소를 포크하세요
2. 기능 브랜치를 생성하세요 (`git checkout -b feature/AmazingFeature`)
3. 변경사항을 커밋하세요 (`git commit -m 'Add some AmazingFeature'`)
4. 브랜치에 푸시하세요 (`git push origin feature/AmazingFeature`)
5. Pull Request를 여세요

---

## 📄 라이센스

이 프로젝트는 오픈 소스이며 [MIT 라이센스](../LICENSE) 하에 제공됩니다.

---

<p align="center">
    <b>⭐ 이 저장소가 도움이 되었다면 별표를 눌러주세요!</b>
</p>
