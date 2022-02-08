Git and Git Flow Cheat Sheet [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)
===============
<hr>
<p align="center">
	<img alt="Git" src="../Img/git-logo.png" height="190" width="455">
</p>
<hr>


### Indeks
* [Konfiguracja](#konfiguracja)
* [Pliki Konfiguracyjne](#pliki-konfiguracyjne)
* [Tworzenie](#tworzenie)
* [Zmiany Lokalne](#zmiany-lokalne)
* [Wyszukiwanie](#wyszukiwanie)
* [Historia Commitów](#historia-commitów)
* [Gałęzie & Tagi](#gałęzie--tagi)
* [Uaktualnij & Opublikuj](#uaktualnij--opublikuj)
* [Połącz & Rebase](#połącz--rebase)
* [Cofnij](#cofnij)
* [Git Flow](#git-flow)


<hr>

## Konfiguracja

##### Wyświetl aktualną konfigurację:
```
$ git config --list
```
##### Wyświetl konfigurację repozytorium:
```
$ git config --local --list
```

##### Wyświetl konfigurację globalną:
```
$ git config --global --list
```

##### Wyświetl konfigurację systemową:
```
$ git config --system --list
```

##### Ustaw nazwę do rozpoznawania autorstwa, podczas przeglądu historii wersji:
```
$ git config --global user.name “[imię nazwisko]”
```

##### Ustaw adres email, który będzie przypisany do każdego znacznika historii:
```
$ git config --global user.email “[poprawny-email]”
```

##### Ustaw automatyczne kolorowanie wiersza poleceń Git, aby ułatwić przegląd:
```
$ git config --global color.ui auto
```

##### Ustaw edytor globalny dla commitów:
```
$ git config --global core.editor vi
```

<hr>

## Pliki Konfiguracyjne

##### Plik konfiguracyjny dla określonego repozytorium [--local]:
```
<repo>/.git/config
```

##### Własny plik konfiguracyjny [--global]:
```
~/.gitconfig
```

##### Globalny plik konfiguracyjny [--system]:
```
/etc/gitconfig
```

<hr>

## Tworzenie

##### Sklonuj istniejące repozytorium:

Istnieją dwa sposoby:

Przez SSH

```
$ git clone ssh://nazwa@domena.com/repo.git
```

Przez HTTP

```
$ git clone http://domena.com/nazwa/repo.git
```

##### Utwórz nowe repozytorium lokalne w bieżącej lokalizacji:
```
$ git init
```

##### Utwórz nowe repozytorium lokalne w konkretnej lokalizacji:
```
$ git init <ścieżka>
```

<hr>

## Zmiany Lokalne

##### Zmiany w katalogu roboczym:
```
$ git status
```

##### Zmiany w śledzonych plikach:
```
$ git diff
```

##### Zobacz zmiany/różnice w danym pliku:
```
$ git diff <plik>
```

##### Dodaj wszystkie bieżące zmiany do następnego commitu:
```
$ git add .
```

##### Dodaj kilka zmian w &lt;plik&gt; do następnego commitu:
```
$ git add -p <plik>
```

##### Dodaj tylko wymienione pliki do następnego commitu:
```
$ git add <nazwapliku1> <nazwapliku2>
```

##### Wykonaj commit z wszystkimi zmianami w śledzonych plikach:
```
$ git commit -a
```

##### Wykonaj commit wcześniej dodanych plików:
```
$ git commit
```

##### Wykonaj commit z wiadomością:
```
$ git commit -m 'twoja wiadomość'
```

##### Wykonaj commit omijając staging area i dodaj wiadomość:
```
$ git commit -am 'twoja wiadomość'
```

##### Wykonaj commit z wcześniejszą datą:
```
$ git commit --date="`date --date='n dzień temu'`" -am "<twoja wiadomość>"
```

##### Zmodyfikuj ostatni commit:<br>
<em><sub>Nie modyfikuj opublikowanych commitów!</sub></em>

```
$ git commit -a --amend
```

##### Zmodyfikuj ostatni commit, ale pozostaw poprzednią wiadomość: 
<em><sub>Nie modyfikuj opublikowanych commitów!</sub></em>

```shell
$ git commit --amend --no-edit
```

##### Zmień czas commitera ostatniego commitu:
```
GIT_COMMITTER_DATE="date" git commit --amend
```

##### Zmień czas autora ostatniego commitu:
```shell
$ git commit --amend --date="date"
```

##### Przenieś niecommitowane zmiany z bieżącej gałęzi do innej gałęzi:<br>
```
$ git stash
$ git checkout gałąź2
$ git stash pop
```

##### Przywróć przechowywane zmiany z powrotem do bieżącej gałęzi:
```shell
$ git stash apply
```

#### Przywróć dany stash z powrotem do bieżącej gałęzi:
- *{numer_stashu}* można uzyskać poprzez `git stash list`

```shell
$ git stash apply stash@{numer_stashu}
```

##### Usuń ostatni zestaw przechowywanych zmian:
```
$ git stash drop
```

<hr>

## Wyszukiwanie

##### Wyszukiwanie tekstu we wszystkich plikach w katalogu:
```
$ git grep "Cześć"
```

##### W dowolnej wersji wyszukiwania tekstu:
```
$ git grep "Cześć" v2.5
```

##### Wyświetl commity, które wprowadziły określone słowo kluczowe:
```
$ git log -S 'słowo kluczowe'
```

##### Wyświetl commity, które wprowadziły określone słowo kluczowe (używając wyrażenia regularnego):
```
$ git log -S 'słowo kluczowe' --pickaxe-regex
```

<hr>

## Historia Commitów

##### Wyświetl wszystkie commity, zaczynając od najnowszego (wyświetli hash, informacje o autorze, datę commitu i tytuł commitu):
```
$ git log
```

##### Wyświetl wszystkie commity (wyświetli tylko hash commitu i wiadomość commitu):
```
$ git log --oneline
```

##### Wyświetl wszystkie commity określonego użytkownika:
```
$ git log --author="użytkownik"
```

##### Wyświetl zmiany w czasie dla określonego pliku:
```
$ git log -p <plik>
```

##### Wyświetl commity które są tylko w remote/branch po prawej stronie:
```
$ git log --oneline <origin/master>..<remote/master> --left-right
```

##### Kto zmienił, co i kiedy w &lt;plik&gt;:
```
$ git blame <plik>
```

##### Wyświetl dziennik referencji:
```
$ git reflog show
```

##### Usuń dziennik referencji:
```
$ git reflog delete
```
<hr>

## Przenieś / Zmień nazwę

##### Zmień nazwę pliku:

Zmień nazwę z Index.txt na Index.html

```
$ git mv Index.txt Index.html
```

<hr>

## Gałęzie & Tagi

##### Wymień wszystkie lokalne gałęzie:
```
$ git branch
```

#### Wymień lokalne/zdalne gałęzie:
```
$ git branch -a
```

##### Wymień wszystkie zdalne gałęzie:
```
$ git branch -r
```

##### Zmień gałąź HEAD:
```
$ git checkout <gałąź>
```

##### Przełącz pojedynczy plik z innej gałęzi:
```
$ git checkout <gałąź> -- <nazwapliku>
```

##### Utwórz i zmień na nową gałąź:
```
$ git checkout -b <gałąź>
```

##### Zmień na poprzednią gałąź, bez podawania konkretnej nazwy:
```
$ git checkout -
```

##### Utwórz nową gałąź z istniejącej już gałęzi i przełącz na nową gałąź:
```
$ git checkout -b <nowa_gałąź> <istniejąca_gałąź>
```


#### Przełącz i utwórz nową galąź z istniejącego commitu:
```
$ git checkout <hash-commitu> -b <nazwa_nowej_gałęzi>
```


##### Utwórz nową gałąź na podstawie aktualnej gałęzi HEAD:
```
$ git branch <nowa-gałąź>
```

##### Utwórz nową gałąź śledzącą na podstawie gałęzi zdalnej:
```
$ git branch --track <nowa-gałąź> <gałąź-zdalna>
```

##### Usuń gałąź lokalną:
```
$ git branch -d <gałąź>
```

##### Zmień nazwę obecnej gałęzi:
```shell
$ git branch -m <nowa_nazwa_gałęzi>
```

##### Wymuś usunięcie gałęzi lokalnej:
<em><sub>Utracisz niepołączone zmiany!</sub></em>

```
$ git branch -D <branch>
```

##### Oznacz `HEAD` tagiem:
```
$ git tag <nazwa-tagu>
```

##### Oznacz `HEAD` tagiem i otwórz edytor, aby napisać wiadomość:
```
$ git tag -a <nazwa-tagu>
```

##### Oznacz `HEAD` tagiem z wiadomością:
```
$ git tag <nazwa-tagu> -am 'twoja wiadomość'
```

##### Wyświetl wszystkie tagi:
```
$ git tag
```

##### Wyświetl wszystkie tagi wraz z ich wiadomościami (wiadomość tagu lub wiadomość commitu jeśli tag nie ma wiadomości):
```
$ git tag -n
```

<hr>

## Uaktualnij & Opublikuj

##### Wyświetl wszystkie obecnie skonfigurowane repozytoria zdalne:
```
$ git remote -v
```

##### Wyświetl informacje o repozytorium:
```
$ git remote show <repozytorium>
```

##### Dodaj nowe zdalne repozytorium o nazwie &lt;repozytorium&gt;:
```
$ git remote add <repozytorium> <url>
```

##### Zmień nazwę zdalnego repozytoriumy, z &lt;repozytorium&gt; na &lt;nowe_repozytorium&gt;:
```
$ git remote rename <repozytorium> <nowe_repozytorium>
```

##### Usuń repozytorium:
```
$ git remote rm <repozytorium>
```

<em><sub>Uwaga: git remote rm nie usuwa zdalnego repozytorium z serwera. Po prostu usuwa zdalne repozytorium i jego referencje z lokalnego repozytorium.</sub></em>

##### Pobierz wszystkie zmiany z &lt;repozytorium&gt;, ale nie integruj ich z HEAD:
```
$ git fetch <repozytorium>
```

##### Pobierz zmian i bezpośrednio połącz/zintegruj z HEAD:
```
$ git remote pull <repozytorium> <url>
```

##### Pobierz wszystkie zmiany z HEAD do lokalnego repozytorium:
```
$ git pull origin master
```

##### Pobierz wszystkie zmiany z HEAD do lokalnego repozytorium bez łączenia ich:
```
$ git pull --rebase <repozytorium> <gałąź>
```

##### Opublikuj lokalne zmiany w repozytorium zdalnym:
```
$ git push remote <repozytorium> <gałąź>
```

##### Usuń gałąź w repozytorium zdalnym:
```
$ git push <repozytorium> :<gałąź> (od Git v1.5.0)
```
lub
```
$ git push <repozytorium> --delete <gałąź> (od Git v1.7.0)
```

##### Opublikuj swoje tagi:
```
$ git push --tags
```
<hr>

#### Ustaw globalne narzędzie do scalania jako Meld (edytor):
```bash
$ git config --global merge.tool meld
```

##### Uzyj narzędzia Meld, aby rozwiązywać konflikty:
```
$ git mergetool
```

## Połącz & Rebase

##### Połącz gałąź z aktualnym HEAD:
```
$ git merge <gałąź>
```

#### Wyświetl połączone gałęzie:
```
$ git branch --merged
```

##### Zrebase'uj obecny HEAD w &lt;gałąź&gt;:<br>
<em><sub>Nie rebase'uj opublikowanych commitów!</sub></em>

```
$ git rebase <gałąź>
```

##### Przerwij rebase:
```
$ git rebase --abort
```

##### Kontynuuj rebase po rozwiązaniu konfliktów:
```
$ git rebase --continue
```

##### Użyj swojego edytora do ręcznego rozwiązywania konfliktów i (po rozwiązaniu) oznacz plik jako rozwiązany:
```
$ git add <rozwiązany-plik>
```

```
$ git rm <rozwiązany-plik>
```

##### Łączenie commitów:
```
$ git rebase -i <commit-just-before-first>
```

Teraz zastąp to,

```
pick <commit_id>
pick <commit_id2>
pick <commit_id3>
```

tym,

```
pick <commit_id>
squash <commit_id2>
squash <commit_id3>
```
<hr>

## Cofnij

##### Odrzuć wszystkie lokalne zmiany w twoim katalogu roboczym:
```
$ git reset --hard HEAD
```

##### Usuń wszystkie pliki ze staging area(czyli cofnij ostatnie `git add`):
```
$ git reset HEAD
```

##### Odrzuć lokalne zmiany w określonym pliku:
```
$ git checkout HEAD <plik>
```

##### Cofnij commit (tworząc nowy commit z przeciwnymi zmianami):
```
$ git revert <commit>
```

##### Zresetuj wskaźnik HEAD do poprzedniego commitu i odrzuć wszystkie zmiany od tego czasu:
```
$ git reset --hard <commit>
```

##### Zresetuj wskaźnik HEAD do bieżącego stanu zdalnej gałęzi:
```
$ git reset --hard <repozytorium/gałąź> np., upstream/master, origin/my-feature
```

##### Zresetuj wskaźnik HEAD do poprzedniego commitu i zachowaj wszystkie zmiany jako zmiany niestage'owane:
```
$ git reset <commit>
```

##### Zresetuj wskaźnik HEAD do poprzedniego commitu i zachowaj niecommitowane zmiany lokalne:
```
$ git reset --keep <commit>
```

##### Usuń pliki, które zostały przypadkowo zcommitowane przed dodaniem ich do .gitignore:
```
$ git rm -r --cached .
$ git add .
$ git commit -m "remove xyz file"
```
<hr>

## Git-Flow
Poprawione [Git-flow](https://github.com/petervanderdoes/gitflow-avh)

### Indeks
* [Instalacja](#instalacja)
* [Pierwsze Kroki](#pierwsze-kroki)
* [Funkcjonalności](#funkcjonalności)
* [Utwórz Wydanie](#utwórz-wydanie)
* [Hotfiksy](#hotfiksy)
* [Komendy](#komendy)

<hr>

### Instalacja
###### Musisz mieć działającą instalację git jako warunek wstępny. Git flow działa na OSX, Linuxie i Windowsie.

##### OSX Homebrew:
```
$ brew install git-flow-avh
```

##### OSX Macports:
```
$ port install git-flow
```

##### Linux (oparty na Debianie):
```
$ sudo apt-get install git-flow
```

##### Windows (Cygwin):
###### Potrzebujesz wget oraz util-linux żeby zainstalować git-flow.
```bash
$ wget -q -O - --no-check-certificate https://raw.githubusercontent.com/petervanderdoes/gitflow/develop/contrib/gitflow-installer.sh install <state> | bash
```
<hr>

### Pierwsze Kroki
###### Git flow musi zostać zainicjowany, aby dostosować konfigurację projektu do własnych potrzeb. Zacznij używać git-flow inicjalizując go wewnątrz istniejącego repozytorium git:
##### Inicjalizacja:
###### Będziesz musiał odpowiedzieć na kilka pytań dotyczących konwencji nazewnictwa dla twoich gałęzi. Zaleca się używanie wartości domyślnych.
```shell
git flow init
```
lub
###### Żeby użyć ustawień domyślnych
```shell
git flow init -d
```
<hr>

### Funkcjonalności
###### Twórz nowe funkcjonalności dla nadchodzących wydań. Zazwyczaj istnieją tylko w repozytoriach deweloperów.
##### Utwórz nową funkcjonalność:
###### Ta czynnośc tworzy nową gałąź funkcjonalności wzorowaną na 'develop' i zmienia na tę gałąź.
```
git flow feature start MOJAFUNKCJA
```

##### Ukończ funkcjonalność:
###### Dokończ tworzenie funkcjonalności. Ta czynność wykonuje następujące zadania:
###### 1) Łączy MOJAFUNKCJA w 'develop'.
###### 2) Usuwa gałąź funkcjonalności.
###### 3) Zmienia z powrotem na gałąź 'develop'.
```
git flow feature finish MOJAFUNKCJA
```

##### Publikowanie funkcji:
###### Tworzysz funkcjonalność w ramach współpracy? Opublikuj funkcjonalność na zdalnym serwerze, aby mogli z niej korzystać inni użytkownicy.
```
git flow feature publish MOJAFUNKCJA
```

##### Pobieranie opublikowanej funkcji:
###### Pobierz funkcję opublikowaną przez innego użytkownika.
```
git flow feature pull origin MOJAFUNKCJA
```

##### Śledź funkcję na origin:
###### Możesz śledzić funkcję na origin używając:
```
git flow feature track MOJAFUNKCJA
```
<hr>

### Utwórz Wydanie
###### Wspiera przygotowanie nowego wydania produkcyjnego. Umożliwia poprawki drobnych błędów i przygotowanie meta-danych do wydania.

##### Rozpocznij wydanie:
###### Aby rozpocząć wydanie, użyj polecenia git flow release. Tworzy ono gałąź wydania utworzoną z gałęzi 'develop'. Opcjonalnie możesz podać hash SHA-1 commitu [BASE], od którego rozpocznie się wydanie. Commit musi znajdować się w gałęzi 'develop'.
```
git flow release start RELEASE [BASE]
```
###### Rozsądnie jest opublikować gałąź release po jej utworzeniu, aby umożliwić commitowanie wydania innym developerom. Zrób to podobnie do publikowania funkcji za pomocą polecenia:
```
git flow release publish RELEASE
```
###### (Możesz śledzić zdalne wydanie za pomocą komendy: ```git flow release track RELEASE```)

##### Kończenie wydania:
###### Kończenie wydania jest jednym z głównych kroków w rozgałęzianiu git. Wykonuje on kilka czynności:
###### 1) Łączy gałąź wydania z powrotem w gałąź 'master'
###### 2) Taguje wydanie jego nazwą
###### 3) Łączy gałąź wydania z powrotem w gałąź 'develop'
###### 4) Usuwa gałąź wydania
```
git flow release finish RELEASE
```
###### Nie zapomnij spushować swoich tagów używając ```git push --tags```

<hr>

### Hotfiksy
###### Hotfiksy powstają w wyniku konieczności natychmiastowego działania w przypadku niepożądanego stanu wersji produkcyjnej. Mogą być odgałęzione od odpowiedniego znacznika na gałęzi głównej, która oznacza wersję produkcyjną.

##### Początek Git flow hotfiksa:
###### Tak jak inne komendy git flow, hotfiks rozpoczyna się:
```
$ git flow hotfix start VERSION [BASENAME]
```
###### Argument "version" oznacza nazwę nowego wydania hotfiksa. Opcjonalnie możesz określić nazwę bazową, od której chcesz rozpocząć.

##### Kończenie hotfiksa:
###### Po ukończeniu hotfiksa zostaje on scalony z powrotem do wersji rozwojowej i głównej. Dodatkowo główne złączenie jest oznaczane wersją hotfiksa.
```
git flow hotfix finish VERSION
```
<hr>

### Komendy
<p align="center">
    <img alt="Git" src="./Img/git-flow-commands.png" height="270" width="460">
</p>
<hr>

### Schemat Git flow

<p align="center">
    <img alt="Git" src="Img/git-flow-commands-without-flow.png">
</p>
<hr>
