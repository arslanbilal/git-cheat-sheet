# Git Cheat Sheet 한국어

![Git Logo](../Img/git-logo.png)

가장 많이 사용되는 Git 명령어들의 빠른 참조 가이드, 쉬운 사용을 위해 카테고리별로 정리되었습니다.

## 📖 소개

이 Git 치트 시트는 개발자들이 가장 자주 사용하는 Git 명령어들을 빠르게 찾아볼 수 있도록 구성되었습니다. 초보자부터 숙련된 개발자까지, 모든 수준의 사용자가 Git 워크플로우를 효율적으로 관리할 수 있도록 도와줍니다.

---

## 📖 이 가이드에 대해

이 포괄적인 Git 참조 가이드는 Git 워크플로우를 개선하고자 하는 모든 사람들을 위한 완전한 리소스입니다. Git 여정을 시작하는 초보자부터 숙련된 개발자까지, 이 가이드는 개발 과정을 가속화하기 위해 체계적이고 분류된 명령어를 제공합니다.

### 주요 특징:
- **체계적인 카테고리**: 명령어들이 명확하고 논리적인 그룹으로 정리됨
- **실용적인 예제**: 실제 사용 사례와 함께 제공
- **초보자 친화적**: 명확한 설명과 팁 포함
- **빠른 참조**: 필수 명령어에 대한 빠른 접근

---

## 📑 목차

- [📖 이 가이드에 대해](#이-가이드에-대해)
- [🔧 초기 설정](#초기-설정)
- [⚙️ 설정 파일](#설정-파일)
- [📁 저장소 설정](#저장소-설정)
- [📊 상태 명령어](#상태-명령어)
- [📝 파일 관리](#파일-관리)
- [💾 커밋](#커밋)
- [🌿 브랜치](#브랜치)
- [🔀 머지](#머지)
- [🌐 원격 저장소](#원격-저장소)
- [📚 히스토리와 로그](#히스토리와-로그)
- [🔍 검색](#검색)
- [📁 이동/이름 변경](#이동이름-변경)
- [🏷️ 태그](#태그)
- [↩️ 변경사항 되돌리기](#변경사항-되돌리기)
- [📦 스태시](#스태시)
- [🌊 Git Flow](#git-flow)
- [💡 유용한 팁](#유용한-팁)
- [🌍 다른 언어](#다른-언어)
- [🤝 기여하기](#기여하기)
- [📄 라이센스](#라이센스)
- [📖 추가 리소스](#추가-리소스)

---

## 🔧 초기 설정

개인 정보로 Git을 설정하세요:

```bash
# 사용자 이름 설정
git config --global user.name "당신의 이름"

# 이메일 설정
git config --global user.email "email@example.com"

# 현재 설정 보기
git config --list

# 기본 에디터 설정
git config --global core.editor "nano"

# 머지 도구 설정
git config --global merge.tool vimdiff
```

---

## ⚙️ 설정 파일

Git은 여러 레벨에서 설정을 관리할 수 있습니다:

### 전역 설정 파일
```bash
# 전역 설정 파일 경로
~/.gitconfig

# 전역 설정 편집
git config --global --edit
```

### 저장소별 설정 파일
```bash
# 저장소별 설정 파일 경로
.git/config

# 저장소별 설정 편집
git config --edit
```

### 시스템 전체 설정
```bash
# 시스템 설정 파일 (관리자 권한 필요)
/etc/gitconfig

# 시스템 설정 편집
git config --system --edit
```

### 유용한 설정들
```bash
# 컬러 출력 활성화
git config --global color.ui true

# 기본 브랜치명 설정
git config --global init.defaultBranch main

# 줄 바꿈 처리 (macOS/Linux)
git config --global core.autocrlf input

# 줄 바꿈 처리 (Windows)
git config --global core.autocrlf true
```

---

## 📁 저장소 설정

### 새 저장소 만들기:

```bash
# 새 Git 저장소 생성
git init

# 기존 저장소 클론
git clone <저장소-url>

# 특정 디렉토리에 클론
git clone <저장소-url> <디렉토리-이름>
```

---

## 📊 상태 명령어

### 저장소 상태 확인:

```bash
# 저장소의 현재 상태 보기
git status

# 짧은 형식으로 상태 보기
git status -s

# 추적되지 않는 파일을 무시하고 상태 보기
git status --ignored

# 수정된 파일의 차이점 보기
git diff

# 스테이징 영역의 차이점 보기
git diff --staged

# 브랜치 간 차이점 보기
git diff <브랜치1> <브랜치2>
```

---

## 📝 파일 관리

### 파일 추가 및 제거:

```bash
# 특정 파일을 스테이징 영역에 추가
git add <파일>

# 모든 수정된 파일 추가
git add .

# 특정 타입의 모든 파일 추가
git add *.txt

# 대화형으로 추가
git add -i

# 저장소와 작업 디렉토리에서 파일 제거
git rm <파일>

# 저장소에서만 파일 제거 (디렉토리에는 유지)
git rm --cached <파일>

# 파일 이동/이름 변경
git mv <소스-파일> <대상-파일>
```

---

## 💾 커밋

### 저장소에 변경사항 저장:

```bash
# 메시지와 함께 커밋
git commit -m "커밋 메시지"

# 모든 수정된 파일을 추가하고 커밋
git commit -am "커밋 메시지"

# 마지막 커밋 수정
git commit --amend

# 빈 커밋 (CI/CD 트리거에 유용)
git commit --allow-empty -m "CI 트리거"

# 상세한 메시지로 커밋 (에디터 열림)
git commit
```

---

## 🌿 브랜치

### 브랜치 작업:

```bash
# 모든 브랜치 보기
git branch

# 원격 브랜치 보기
git branch -r

# 모든 브랜치 보기 (로컬과 원격)
git branch -a

# 새 브랜치 생성
git branch <브랜치-이름>

# 브랜치로 전환
git checkout <브랜치-이름>

# 새 브랜치 생성하고 전환
git checkout -b <브랜치-이름>

# 특정 커밋에서 브랜치 생성
git checkout -b <브랜치-이름> <커밋-해시>

# 브랜치 삭제
git branch -d <브랜치-이름>

# 강제로 브랜치 삭제
git branch -D <브랜치-이름>

# 현재 브랜치 이름 변경
git branch -m <새-이름>

# 특정 브랜치 이름 변경
git branch -m <옛-이름> <새-이름>
```

---

## 🔀 머지

### 브랜치 간 변경사항 머지:

```bash
# 현재 브랜치에 다른 브랜치 머지
git merge <브랜치-이름>

# 패스트-포워드 없이 머지 (머지 커밋 생성)
git merge --no-ff <브랜치-이름>

# 패스트-포워드일 때만 머지
git merge --ff-only <브랜치-이름>

# 진행 중인 머지 취소
git merge --abort

# 충돌 해결 후 머지 계속
git merge --continue
```

---

## 🌐 원격 저장소

### 원격 저장소 관리:

```bash
# 원격 저장소 보기
git remote

# URL과 함께 원격 저장소 보기
git remote -v

# 원격 저장소 추가
git remote add <이름> <url>

# 원격 저장소 URL 변경
git remote set-url <이름> <새-url>

# 원격 저장소 제거
git remote remove <이름>

# 원격 저장소에 변경사항 푸시
git push <원격> <브랜치>

# 브랜치 푸시하고 추적 설정
git push -u <원격> <브랜치>

# 모든 브랜치 푸시
git push --all

# 태그 푸시
git push --tags

# 원격 저장소에서 변경사항 다운로드
git pull <원격> <브랜치>

# 머지 없이 변경사항 다운로드
git fetch <원격>

# 모든 원격 브랜치 다운로드
git fetch --all
```

---

## 📚 히스토리와 로그

### 커밋 히스토리 탐색:

```bash
# 커밋 히스토리 보기
git log

# 커밋당 한 줄로 히스토리 보기
git log --oneline

# 그래프와 함께 히스토리 보기
git log --graph

# 특정 파일의 히스토리 보기
git log <파일>

# 커밋 통계 보기
git log --stat

# 각 커밋의 변경사항 보기
git log -p

# 마지막 N개 커밋 보기
git log -n <숫자>

# 날짜 범위 내 커밋 보기
git log --since="2023-01-01" --until="2023-12-31"

# 작성자별 커밋 보기
git log --author="작성자 이름"

# 커밋 메시지에서 검색
git log --grep="키워드"
```

---

## 🔍 검색

### 파일과 내용 검색:

```bash
# 파일 내용에서 텍스트 검색
git grep "검색어"

# 특정 커밋에서 검색
git grep "검색어" HEAD~3

# 대소문자 구분 없이 검색
git grep -i "검색어"

# 정확한 단어만 검색
git grep -w "검색어"

# 줄 번호와 함께 검색
git grep -n "검색어"

# 매칭된 파일 이름만 표시
git grep -l "검색어"

# 로그에서 특정 텍스트 변경사항 검색
git log -S "검색어"

# 정규표현식으로 로그 검색
git log --grep="패턴" --perl-regexp

# 파일명 검색
git ls-files | grep "패턴"
```

---

## 🏷️ 태그

### 버전 태그 관리:

```bash
# 모든 태그 보기
git tag

# 가벼운 태그 생성
git tag <태그-이름>

# 주석이 달린 태그 생성
git tag -a <태그-이름> -m "태그 메시지"

# 특정 커밋에 태그 생성
git tag -a <태그-이름> <커밋-해시>

# 태그 정보 보기
git show <태그-이름>

# 로컬 태그 삭제
git tag -d <태그-이름>

# 원격 태그 삭제
git push --delete <원격> <태그-이름>

# 특정 태그 푸시
git push <원격> <태그-이름>

# 모든 태그 푸시
git push <원격> --tags
```

---

## 📁 이동/이름 변경

### 파일과 디렉토리 관리:

```bash
# 파일 이동/이름 변경
git mv <기존-파일> <새-파일>

# 디렉토리 이름 변경
git mv <기존-디렉토리> <새-디렉토리>

# 여러 파일을 디렉토리로 이동
git mv file1.txt file2.txt directory/

# 대소문자만 변경 (대소문자 구분 파일시스템)
git mv filename.txt temp.txt
git mv temp.txt FileName.txt

# 파일 이동 후 히스토리 확인
git log --follow <파일>

# 이동된 파일 추적
git log --stat -M

# 이름 변경 감지 임계값 설정
git log --follow -M90% <파일>
```

---

## ↩️ 변경사항 되돌리기

### 수정사항 되돌리기:

```bash
# 특정 파일의 변경사항 취소
git checkout <파일>

# 모든 커밋되지 않은 변경사항 취소
git checkout .

# 특정 버전으로 파일 되돌리기
git checkout <커밋-해시> <파일>

# 스테이징 영역에서 파일 제거
git reset <파일>

# 스테이징 영역에서 모든 파일 제거
git reset

# 이전 커밋으로 돌아가기 (변경사항 유지)
git reset --soft HEAD~1

# 이전 커밋으로 돌아가기 (변경사항 취소)
git reset --hard HEAD~1

# 특정 커밋으로 돌아가기
git reset --hard <커밋-해시>

# 다른 커밋을 취소하는 새 커밋 생성
git revert <커밋-해시>

# 여러 커밋 되돌리기
git revert <해시-시작>..<해시-끝>
```

---

## 📦 스태시

### 임시로 작업 저장:

```bash
# 현재 변경사항을 스태시에 저장
git stash

# 설명적 메시지와 함께 저장
git stash save "설명적 메시지"

# 모든 스태시 보기
git stash list

# 마지막 스태시 적용
git stash apply

# 특정 스태시 적용
git stash apply stash@{0}

# 마지막 스태시 적용하고 삭제
git stash pop

# 특정 스태시 삭제
git stash drop stash@{0}

# 모든 스태시 삭제
git stash clear

# 스태시의 변경사항 보기
git stash show stash@{0}

# 스태시에서 브랜치 생성
git stash branch <브랜치-이름> stash@{0}
```

---

## 🌊 Git Flow

Git Flow는 프로젝트 릴리스를 중심으로 설계된 엄격한 워크플로우를 정의하는 브랜칭 모델입니다.

### 주요 브랜치:
- **master/main**: 프로덕션 코드
- **develop**: 주요 개발 브랜치

### 지원 브랜치:
- **feature**: 새로운 기능을 위한
- **release**: 새 버전 준비를 위한
- **hotfix**: 프로덕션 긴급 수정을 위한

### Git Flow 명령어:

```bash
# git flow 초기화
git flow init

# 새 기능 시작
git flow feature start <기능-이름>

# 기능 완료
git flow feature finish <기능-이름>

# 기능 발행
git flow feature publish <기능-이름>

# 릴리스 시작
git flow release start <버전>

# 릴리스 완료
git flow release finish <버전>

# 핫픽스 시작
git flow hotfix start <버전>

# 핫픽스 완료
git flow hotfix finish <버전>
```

### Git Flow 없는 워크플로우:

![Git Flow Commands](../Img/git-flow-commands-without-flow.png)

```bash
# 기능 브랜치 생성
git checkout develop
git checkout -b feature/새-기능

# 기능 작업
git add .
git commit -m "새 기능 추가"

# develop에 기능 머지
git checkout develop
git merge --no-ff feature/새-기능
git branch -d feature/새-기능

# 릴리스 브랜치 생성
git checkout develop
git checkout -b release/1.0.0

# 릴리스 완료
git checkout master
git merge --no-ff release/1.0.0
git tag -a 1.0.0 -m "버전 1.0.0"
git checkout develop
git merge --no-ff release/1.0.0
git branch -d release/1.0.0
```

---

## 💡 유용한 팁

### 유용한 별칭:

```bash
# 유용한 별칭 설정
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
git config --global alias.visual '!gitk'
```

### .gitignore 파일:

```bash
# .gitignore 파일 생성
echo "node_modules/" >> .gitignore
echo "*.log" >> .gitignore
echo ".env" >> .gitignore

# 이미 추적된 파일 무시하기
git rm --cached <파일>
echo "<파일>" >> .gitignore
git add .gitignore
git commit -m ".gitignore에 파일 추가"
```

---

## 📖 추가 리소스

### 공식 문서 및 가이드
- [Git 공식 문서](https://git-scm.com/doc)
- [Pro Git 책 (무료)](https://git-scm.com/book)
- [Git 참조 매뉴얼](https://git-scm.com/docs)
- [Git 튜토리얼](https://git-scm.com/docs/gittutorial)

### 온라인 학습 자료
- [GitHub Git 핸드북](https://guides.github.com/introduction/git-handbook/)
- [Atlassian Git 튜토리얼](https://www.atlassian.com/git/tutorials)
- [Learn Git Branching (대화형)](https://learngitbranching.js.org/)
- [Git Immersion](http://gitimmersion.com/)

### GUI 도구
- [GitHub Desktop](https://desktop.github.com/)
- [GitKraken](https://www.gitkraken.com/)
- [SourceTree](https://www.sourcetreeapp.com/)
- [Tower](https://www.git-tower.com/)

### 고급 주제
- [Git Hooks](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks)
- [Git Workflows](https://www.atlassian.com/git/tutorials/comparing-workflows)
- [Git 내부 구조](https://git-scm.com/book/en/v2/Git-Internals-Plumbing-and-Porcelain)

---

## 🌍 다른 언어

이 Git Cheat Sheet는 다음 언어로 제공됩니다:

- 🇺🇸 [English](../README.md)
- 🇸🇦 [العربية](git-cheat-sheet-ar.md)
- 🇧🇩 [বাংলা](git-cheat-sheet-bn.md)
- 🇩🇪 [Deutsch](git-cheat-sheet-de.md)
- 🇬🇷 [Ελληνικά](git-cheat-sheet-el.md)
- 🇪🇸 [Español](git-cheat-sheet-es.md)
- 🇮🇳 [हिन्दी](git-cheat-sheet-hi.md)
- 🇰🇷 **한국어** (현재)
- 🇵🇱 [Polski](git-cheat-sheet-pl.md)
- 🇧🇷 [Português](git-cheat-sheet-pt_BR.md)
- 🇹🇷 [Türkçe](git-cheat-sheet-tr.md)
- 🇨🇳 [中文](git-cheat-sheet-zh.md)

---

## 🤝 기여하기

기여를 환영합니다! 이 프로젝트를 개선하는 데 도움을 주세요:

1. **문제 보고**: 오류나 개선 제안을 공유하세요
2. **새 언어 추가**: 번역을 만들거나 기존 것을 개선하세요
3. **내용 개선**: 새로운 명령어, 예제 또는 설명을 추가하세요
4. **피드백 제공**: 경험과 제안을 공유하세요

### 기여 방법:
- [GitHub에서 이슈 열기](https://github.com/arslanbilal/git-cheat-sheet/issues)
- Pull request 제출
- 문서 개선 제안

---

## 📄 라이센스

이 프로젝트는 MIT 라이센스 하에 라이센스가 부여됩니다. 자세한 내용은 [LICENSE](../LICENSE) 파일을 참조하세요.

---

<div align="center">
  <strong>⭐ 이 치트 시트가 유용하다면 별표를 주세요!</strong><br>
  <em>Git과 함께 즐거운 코딩 하세요! 🚀</em>
</div>
