# Git Cheat Sheet Polski

![Git Logo](../Img/git-logo.png)

Szybki przewodnik referencyjny dla najczęściej używanych poleceń Git, zorganizowany w kategorie dla łatwego użycia.

## 📖 O tym przewodniku

Ten kompleksowy przewodnik referencyjny Git jest kompletnym zasobem dla każdego, kto chce usprawnić swój przepływ pracy z Git. Od początkujących, którzy rozpoczynają swoją przygodę z Git, po doświadczonych programistów, ten przewodnik zapewnia systematycznie zorganizowane polecenia kategoryzowane w celu przyspieszenia procesu rozwoju.

### Kluczowe cechy:
- **Systematyczne kategorie**: Polecenia zorganizowane w jasne, logiczne grupy
- **Praktyczne przykłady**: Zawiera rzeczywiste przypadki użycia
- **Przyjazne dla początkujących**: Jasne wyjaśnienia i wskazówki
- **Szybka referencja**: Błyskawiczny dostęp do niezbędnych poleceń

---

## 📑 Spis treści

- [📖 O tym przewodniku](#o-tym-przewodniku)
- [🔧 Konfiguracja początkowa](#konfiguracja-początkowa)
- [⚙️ Pliki konfiguracyjne](#pliki-konfiguracyjne)
- [📁 Konfiguracja repozytorium](#konfiguracja-repozytorium)
- [📊 Polecenia statusu](#polecenia-statusu)
- [📝 Zarządzanie plikami](#zarządzanie-plikami)
- [💾 Commity](#commity)
- [🌿 Gałęzie (Branches)](#gałęzie-branches)
- [🔀 Scalanie (Merge)](#scalanie-merge)
- [🌐 Zdalne repozytoria](#zdalne-repozytoria)
- [📚 Historia i logi](#historia-i-logi)
- [🔍 Wyszukiwanie](#wyszukiwanie)
- [📁 Przenoszenie/Zmiana nazwy](#przenoszeniizmiana-nazwy)
- [🏷️ Tagi](#tagi)
- [↩️ Cofanie zmian](#cofanie-zmian)
- [📦 Schowek (Stash)](#schowek-stash)
- [🌊 Git Flow](#git-flow)
- [💡 Przydatne wskazówki](#przydatne-wskazówki)
- [📚 Dodatkowe zasoby](#dodatkowe-zasoby)
- [🌍 Inne języki](#inne-języki)
- [🤝 Współpraca](#współpraca)
- [📄 Licencja](#licencja)

---

## 🔧 Konfiguracja początkowa

Skonfiguruj Git ze swoimi danymi osobowymi:

```bash
# Ustawienie nazwy użytkownika
git config --global user.name "Twoje Imię"

# Ustawienie adresu email
git config --global user.email "email@example.com"

# Wyświetlenie bieżącej konfiguracji
git config --list

# Ustawienie domyślnego edytora
git config --global core.editor "nano"

# Ustawienie narzędzia do scalania
git config --global merge.tool vimdiff
```

---

## ⚙️ Pliki konfiguracyjne

Git zarządza konfiguracją na kilku poziomach:

### Plik konfiguracji globalnej
```bash
# Ścieżka do globalnego pliku konfiguracji
~/.gitconfig

# Edycja globalnej konfiguracji
git config --global --edit
```

### Plik konfiguracji repozytorium
```bash
# Ścieżka do pliku konfiguracji repozytorium
.git/config

# Edycja konfiguracji repozytorium
git config --edit
```

### Konfiguracja systemowa
```bash
# Plik konfiguracji systemowej (wymaga uprawnień administratora)
/etc/gitconfig

# Edycja konfiguracji systemowej
git config --system --edit
```

### Przydatne ustawienia konfiguracji
```bash
# Włączenie kolorowego wyjścia
git config --global color.ui true

# Ustawienie domyślnej nazwy gałęzi
git config --global init.defaultBranch main

# Obsługa końców linii (macOS/Linux)
git config --global core.autocrlf input

# Obsługa końców linii (Windows)
git config --global core.autocrlf true
```

---

## 📁 Konfiguracja repozytorium

### Tworzenie nowego repozytorium:

```bash
# Utworzenie nowego repozytorium Git
git init

# Klonowanie istniejącego repozytorium
git clone <url-repozytorium>

# Klonowanie do określonego katalogu
git clone <url-repozytorium> <nazwa-katalogu>
```

---

## 📊 Polecenia statusu

### Sprawdzanie statusu repozytorium:

```bash
# Wyświetlenie bieżącego statusu repozytorium
git status

# Wyświetlenie statusu w krótkim formacie
git status -s

# Wyświetlenie statusu ignorując nieśledzone pliki
git status --ignored

# Wyświetlenie różnic w zmodyfikowanych plikach
git diff

# Wyświetlenie różnic w obszarze staging
git diff --staged

# Wyświetlenie różnic między gałęziami
git diff <gałąź1> <gałąź2>
```

---

## 📝 Zarządzanie plikami

### Dodawanie i usuwanie plików:

```bash
# Dodanie określonego pliku do obszaru staging
git add <plik>

# Dodanie wszystkich zmodyfikowanych plików
git add .

# Dodanie wszystkich plików określonego typu
git add *.txt

# Interaktywne dodawanie
git add -i

# Usunięcie pliku z repozytorium i katalogu roboczego
git rm <plik>

# Usunięcie pliku tylko z repozytorium (zachowanie w katalogu)
git rm --cached <plik>

# Przenoszenie/zmiana nazwy pliku
git mv <plik-źródłowy> <plik-docelowy>
```

---

## 💾 Commity

### Zapisywanie zmian w repozytorium:

```bash
# Commit z wiadomością
git commit -m "Wiadomość commita"

# Commit dodając wszystkie zmodyfikowane pliki
git commit -am "Wiadomość commita"

# Modyfikacja ostatniego commita
git commit --amend

# Pusty commit (przydatny dla wyzwalaczy CI/CD)
git commit --allow-empty -m "Wyzwalacz CI"

# Commit ze szczegółową wiadomością (otwiera edytor)
git commit
```

---

## 🌿 Gałęzie (Branches)

### Praca z gałęziami:

```bash
# Wyświetlenie wszystkich gałęzi
git branch

# Wyświetlenie zdalnych gałęzi
git branch -r

# Wyświetlenie wszystkich gałęzi (lokalnych i zdalnych)
git branch -a

# Utworzenie nowej gałęzi
git branch <nazwa-gałęzi>

# Przełączenie na gałąź
git checkout <nazwa-gałęzi>

# Utworzenie i przełączenie na nową gałąź
git checkout -b <nazwa-gałęzi>

# Utworzenie gałęzi z określonego commita
git checkout -b <nazwa-gałęzi> <hash-commita>

# Usunięcie gałęzi
git branch -d <nazwa-gałęzi>

# Wymuszone usunięcie gałęzi
git branch -D <nazwa-gałęzi>

# Zmiana nazwy bieżącej gałęzi
git branch -m <nowa-nazwa>

# Zmiana nazwy określonej gałęzi
git branch -m <stara-nazwa> <nowa-nazwa>
```

---

## 🔀 Scalanie (Merge)

### Scalanie zmian między gałęziami:

```bash
# Scalenie gałęzi z bieżącą gałęzią
git merge <nazwa-gałęzi>

# Scalenie bez fast-forward (utworzenie commita scalenia)
git merge --no-ff <nazwa-gałęzi>

# Scalenie tylko jeśli jest fast-forward
git merge --ff-only <nazwa-gałęzi>

# Anulowanie trwającego scalenia
git merge --abort

# Kontynuacja scalenia po rozwiązaniu konfliktów
git merge --continue
```

---

## 🌐 Zdalne repozytoria

### Zarządzanie zdalnymi repozytoriami:

```bash
# Wyświetlenie zdalnych repozytoriów
git remote

# Wyświetlenie zdalnych repozytoriów z URL-ami
git remote -v

# Dodanie zdalnego repozytorium
git remote add <nazwa> <url>

# Zmiana URL zdalnego repozytorium
git remote set-url <nazwa> <nowy-url>

# Usunięcie zdalnego repozytorium
git remote remove <nazwa>

# Wysłanie zmian do zdalnego repozytorium
git push <zdalne> <gałąź>

# Wysłanie gałęzi i ustawienie śledzenia
git push -u <zdalne> <gałąź>

# Wysłanie wszystkich gałęzi
git push --all

# Wysłanie tagów
git push --tags

# Pobranie zmian ze zdalnego repozytorium
git pull <zdalne> <gałąź>

# Pobranie zmian bez scalania
git fetch <zdalne>

# Pobranie wszystkich zdalnych gałęzi
git fetch --all
```

---

## 📚 Historia i logi

### Eksploracja historii commitów:

```bash
# Wyświetlenie historii commitów
git log

# Wyświetlenie historii w jednej linii na commit
git log --oneline

# Wyświetlenie historii z wykresem
git log --graph

# Wyświetlenie historii określonego pliku
git log <plik>

# Wyświetlenie statystyk commitów
git log --stat

# Wyświetlenie zmian w każdym commicie
git log -p

# Wyświetlenie ostatnich N commitów
git log -n <liczba>

# Wyświetlenie commitów między datami
git log --since="2023-01-01" --until="2023-12-31"

# Wyświetlenie commitów według autora
git log --author="Imię Autora"

# Wyszukiwanie w wiadomościach commitów
git log --grep="słowo kluczowe"
```

---

## 🔍 Wyszukiwanie

### Wyszukiwanie w zawartości i historii:

```bash
# Wyszukiwanie tekstu w plikach śledzonych
git grep "tekst do wyszukania"

# Wyszukiwanie z ignorowaniem wielkości liter
git grep -i "tekst"

# Wyszukiwanie całych słów
git grep -w "słowo"

# Wyświetlenie numerów linii
git grep -n "tekst"

# Wyświetlenie tylko nazw plików
git grep -l "tekst"

# Wyszukiwanie w określonych plikach
git grep "tekst" -- "*.js"

# Wyszukiwanie w historii commitów
git log -S "tekst" --source --all

# Wyszukiwanie dodań/usunięć w historii
git log -G "regex_pattern" --patch

# Wyszukiwanie według nazwy pliku
git log --all --full-history -- "**/nazwa_pliku.*"

# Wyszukiwanie w określonym commicie
git grep "tekst" <hash-commita>
```

---

## 🏷️ Tagi

### Zarządzanie tagami wersji:

```bash
# Wyświetlenie wszystkich tagów
git tag

# Utworzenie lekkiego tagu
git tag <nazwa-tagu>

# Utworzenie adnotowanego tagu
git tag -a <nazwa-tagu> -m "Wiadomość tagu"

# Utworzenie tagu na określonym commicie
git tag -a <nazwa-tagu> <hash-commita>

# Wyświetlenie informacji o tagu
git show <nazwa-tagu>

# Usunięcie lokalnego tagu
git tag -d <nazwa-tagu>

# Usunięcie zdalnego tagu
git push --delete <zdalne> <nazwa-tagu>

# Wysłanie określonego tagu
git push <zdalne> <nazwa-tagu>

# Wysłanie wszystkich tagów
git push <zdalne> --tags
```

---

## 📁 Przenoszenie/Zmiana nazwy

### Zarządzanie plikami i katalogami:

```bash
# Przenoszenie/zmiana nazwy pliku
git mv <stary-plik> <nowy-plik>

# Zmiana nazwy katalogu
git mv <stary-katalog> <nowy-katalog>

# Przenoszenie wielu plików do katalogu
git mv plik1.txt plik2.txt katalog/

# Zmiana wielkości liter (systemy plików wrażliwe na wielkość liter)
git mv nazwapliku.txt temp.txt
git mv temp.txt NazwaPliku.txt

# Śledzenie historii przeniesionego pliku
git log --follow <plik>

# Śledzenie przeniesionych plików
git log --stat -M

# Ustawienie progu wykrywania zmian nazwy
git log --follow -M90% <plik>
```

---

## ↩️ Cofanie zmian

### Przywracanie modyfikacji:

```bash
# Anulowanie zmian w określonym pliku
git checkout <plik>

# Anulowanie wszystkich niezacommitowanych zmian
git checkout .

# Przywrócenie pliku do określonej wersji
git checkout <hash-commita> <plik>

# Usunięcie pliku z obszaru staging
git reset <plik>

# Usunięcie wszystkich plików z obszaru staging
git reset

# Powrót do poprzedniego commita (zachowanie zmian)
git reset --soft HEAD~1

# Powrót do poprzedniego commita (anulowanie zmian)
git reset --hard HEAD~1

# Powrót do określonego commita
git reset --hard <hash-commita>

# Utworzenie commita anulującego inny commit
git revert <hash-commita>

# Anulowanie wielu commitów
git revert <hash-od>..<hash-do>
```

---

## 📦 Schowek (Stash)

### Tymczasowe zapisywanie pracy:

```bash
# Zapisanie bieżących zmian w schowku
git stash

# Zapisanie z opisową wiadomością
git stash save "Opisowa wiadomość"

# Wyświetlenie wszystkich schowków
git stash list

# Zastosowanie ostatniego schowka
git stash apply

# Zastosowanie określonego schowka
git stash apply stash@{0}

# Zastosowanie i usunięcie ostatniego schowka
git stash pop

# Usunięcie określonego schowka
git stash drop stash@{0}

# Usunięcie wszystkich schowków
git stash clear

# Wyświetlenie zmian w schowku
git stash show stash@{0}

# Utworzenie gałęzi ze schowka
git stash branch <nazwa-gałęzi> stash@{0}
```

---

## 🌊 Git Flow

Git Flow to model rozgałęziania, który definiuje ścisły przepływ pracy zaprojektowany wokół wydania projektu.

### Główne gałęzie:
- **master/main**: Kod produkcyjny
- **develop**: Główna gałąź rozwoju

### Gałęzie wsparcia:
- **feature**: Dla nowych funkcji
- **release**: Dla przygotowania nowych wersji
- **hotfix**: Dla pilnych poprawek w produkcji

### Polecenia Git Flow:

```bash
# Inicjalizacja git flow
git flow init

# Rozpoczęcie nowej funkcji
git flow feature start <nazwa-funkcji>

# Zakończenie funkcji
git flow feature finish <nazwa-funkcji>

# Publikowanie funkcji
git flow feature publish <nazwa-funkcji>

# Rozpoczęcie wydania
git flow release start <wersja>

# Zakończenie wydania
git flow release finish <wersja>

# Rozpoczęcie hotfixa
git flow hotfix start <wersja>

# Zakończenie hotfixa
git flow hotfix finish <wersja>
```

### Przepływ pracy bez Git Flow:

![Git Flow Commands](../Img/git-flow-commands-without-flow.png)

```bash
# Utworzenie gałęzi funkcji
git checkout develop
git checkout -b feature/nowa-funkcja

# Praca nad funkcją
git add .
git commit -m "Dodanie nowej funkcji"

# Scalenie funkcji z develop
git checkout develop
git merge --no-ff feature/nowa-funkcja
git branch -d feature/nowa-funkcja

# Utworzenie gałęzi wydania
git checkout develop
git checkout -b release/1.0.0

# Zakończenie wydania
git checkout master
git merge --no-ff release/1.0.0
git tag -a 1.0.0 -m "Wersja 1.0.0"
git checkout develop
git merge --no-ff release/1.0.0
git branch -d release/1.0.0
```

---

## 💡 Przydatne wskazówki

### Przydatne aliasy:

```bash
# Ustawienie przydatnych aliasów
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
git config --global alias.visual '!gitk'
```

### Pliki .gitignore:

```bash
# Utworzenie pliku .gitignore
echo "node_modules/" >> .gitignore
echo "*.log" >> .gitignore
echo ".env" >> .gitignore

# Ignorowanie już śledzonych plików
git rm --cached <plik>
echo "<plik>" >> .gitignore
git add .gitignore
git commit -m "Dodanie pliku do .gitignore"
```

---

## 📚 Dodatkowe zasoby

### Oficjalna dokumentacja i przewodniki
- [Oficjalna dokumentacja Git](https://git-scm.com/doc)
- [Książka Pro Git (darmowa)](https://git-scm.com/book)
- [Manual referencyjny Git](https://git-scm.com/docs)
- [Tutorial Git](https://git-scm.com/docs/gittutorial)

### Materiały do nauki online
- [GitHub Git Handbook](https://guides.github.com/introduction/git-handbook/)
- [Atlassian Git Tutorials](https://www.atlassian.com/git/tutorials)
- [Learn Git Branching (interaktywny)](https://learngitbranching.js.org/)
- [Git Immersion](http://gitimmersion.com/)

### Narzędzia GUI
- [GitHub Desktop](https://desktop.github.com/)
- [GitKraken](https://www.gitkraken.com/)
- [SourceTree](https://www.sourcetreeapp.com/)
- [Tower](https://www.git-tower.com/)

### Zaawansowane tematy
- [Git Hooks](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks)
- [Przepływy pracy Git](https://www.atlassian.com/git/tutorials/comparing-workflows)
- [Wewnętrzne mechanizmy Git](https://git-scm.com/book/en/v2/Git-Internals-Plumbing-and-Porcelain)

---

## 🌍 Inne języki

Ten Git Cheat Sheet jest dostępny w następujących językach:

- 🇺🇸 [English](../README.md)
- 🇸🇦 [العربية](git-cheat-sheet-ar.md)
- 🇧🇩 [বাংলা](git-cheat-sheet-bn.md)
- 🇩🇪 [Deutsch](git-cheat-sheet-de.md)
- 🇬🇷 [Ελληνικά](git-cheat-sheet-el.md)
- 🇪🇸 [Español](git-cheat-sheet-es.md)
- 🇮🇳 [हिन्दी](git-cheat-sheet-hi.md)
- 🇰🇷 [한국어](git-cheat-sheet-ko.md)
- 🇵🇱 **Polski** (bieżący)
- 🇧🇷 [Português](git-cheat-sheet-pt_BR.md)
- 🇹🇷 [Türkçe](git-cheat-sheet-tr.md)
- 🇨🇳 [中文](git-cheat-sheet-zh.md)

---

## 🤝 Współpraca

Zachęcamy do współpracy! Aby pomóc w ulepszaniu tego projektu:

1. **Zgłaszaj problemy**: Dziel się błędami lub sugestiami ulepszeń
2. **Dodawaj nowe języki**: Twórz tłumaczenia lub ulepszaj istniejące
3. **Ulepszaj treść**: Dodawaj nowe polecenia, przykłady lub wyjaśnienia
4. **Przekazuj opinie**: Dziel się swoimi doświadczeniami i sugestiami

### Jak współpracować:
- [Otwórz issue na GitHub](https://github.com/arslanbilal/git-cheat-sheet/issues)
- Wyślij pull request
- Zaproponuj ulepszenia dokumentacji

---

## 📄 Licencja

Ten projekt jest licencjonowany na licencji MIT. Zobacz plik [LICENSE](../LICENSE) po więcej szczegółów.

---

<div align="center">
  <strong>⭐ Jeśli ten cheat sheet jest pomocny, zostaw gwiazdkę!</strong><br>
  <em>Miłego kodowania z Git! 🚀</em>
</div>
