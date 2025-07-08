# Git Cheat Sheet Deutsch

![Git Logo](../Img/git-logo.png)

Dieses umfassende Git-Cheat-Sheet hilft Ihnen dabei, Git-Befehle zu beherrschen, ohne alles auswendig zu lernen. Egal, ob Sie Anfänger oder erfahrener Entwickler sind, dieser Leitfaden bietet eine schnelle Referenz für wichtige Git-Operationen.

---

## 📖 Über

Dieses umfassende Git-Cheat-Sheet hilft Ihnen dabei, Git-Befehle zu beherrschen, ohne alles auswendig zu lernen. Egal, ob Sie Anfänger oder erfahrener Entwickler sind, dieser Leitfaden bietet eine schnelle Referenz für wichtige Git-Operationen.

**Beiträge willkommen!** Fühlen Sie sich frei:
- Grammatikfehler zu korrigieren
- Neue Befehle hinzuzufügen
- In Ihre Sprache zu übersetzen
- Erklärungen zu verbessern

---

## 📋 Inhaltsverzeichnis

- [📖 Über](#-Über)
- [🔧 Setup](#-setup)
- [⚙️ Konfigurationsdateien](#️-konfigurationsdateien)
- [🆕 Repository erstellen](#-repository-erstellen)
- [📝 Lokale Änderungen](#-lokale-änderungen)
- [🔍 Suchen](#-suchen)
- [📖 Commit-Historie](#-commit-historie)
- [📁 Verschieben / Umbenennen](#-verschieben--umbenennen)
- [🌿 Branches & Tags](#-branches--tags)
- [🔄 Aktualisieren & Veröffentlichen](#-aktualisieren--veröffentlichen)
- [🔀 Merge & Rebase](#-merge--rebase)
- [↩️ Rückgängig machen](#️-rückgängig-machen)
- [📦 Zwischenspeichern (Stash)](#-zwischenspeichern-stash)
- [🌊 Git Flow](#-git-flow)
- [💡 Nützliche Tipps](#-nützliche-tipps)
- [🌍 Andere Sprachen](#-andere-sprachen)
- [🤝 Beitragen](#-beitragen)
- [📄 Lizenz](#-lizenz)
- [📖 Zusätzliche Ressourcen](#-zusätzliche-ressourcen)

---

## 🔧 Setup

### Konfiguration anzeigen

**Aktuelle Konfiguration anzeigen:**
```bash
git config --list
```

**Repository-Konfiguration anzeigen:**
```bash
git config --local --list
```

**Globale Konfiguration anzeigen:**
```bash
git config --global --list
```

**System-Konfiguration anzeigen:**
```bash
git config --system --list
```

### Benutzer-Konfiguration

**Namen für Versionsverlauf festlegen:**
```bash
git config --global user.name "[Vorname Nachname]"
```

**E-Mail-Adresse festlegen:**
```bash
git config --global user.email "[gültige-email]"
```

### Anzeige- & Editor-Einstellungen

**Automatische Befehlszeilen-Farbgebung aktivieren:**
```bash
git config --global color.ui auto
```

**Globalen Editor für Commits festlegen:**
```bash
git config --global core.editor vi
```

---

## ⚙️ Konfigurationsdateien

| Bereich | Ort | Befehlsflag |
|---------|-----|-------------|
| **Repository** | `<repo>/.git/config` | `--local` |
| **Benutzer** | `~/.gitconfig` | `--global` |
| **System** | `/etc/gitconfig` | `--system` |

---

## 🆕 Repository erstellen

### Existierendes Repository klonen

**Über SSH:**
```bash
git clone ssh://benutzer@domain.com/repo.git
```

**Über HTTPS:**
```bash
git clone https://domain.com/benutzer/repo.git
```

### Neues Repository initialisieren

**Repository im aktuellen Verzeichnis erstellen:**
```bash
git init
```

**Repository in spezifischem Verzeichnis erstellen:**
```bash
git init <verzeichnis>
```

---

## 📝 Lokale Änderungen

### Status & Unterschiede prüfen

**Arbeitsverzeichnis-Status anzeigen:**
```bash
git status
```

**Änderungen in verfolgten Dateien anzeigen:**
```bash
git diff
```

**Änderungen in spezifischer Datei anzeigen:**
```bash
git diff <datei>
```

### Änderungen bereitstellen

**Alle aktuellen Änderungen hinzufügen:**
```bash
git add .
```

**Spezifische Dateien hinzufügen:**
```bash
git add <datei1> <datei2>
```

**Interaktiv Teile einer Datei hinzufügen:**
```bash
git add -p <datei>
```

### Änderungen committen

**Alle verfolgten Dateiänderungen committen:**
```bash
git commit -a
```

**Bereitgestellte Änderungen committen:**
```bash
git commit
```

**Mit Nachricht committen:**
```bash
git commit -m 'Nachricht hier'
```

**Bereitstellung überspringen und mit Nachricht committen:**
```bash
git commit -am 'Nachricht hier'
```

**Mit spezifischem Datum committen:**
```bash
git commit --date="`date --date='n day ago'`" -am "<Commit-Nachricht hier>"
```

### Letzten Commit ändern

> ⚠️ **Warnung:** Veröffentlichte Commits nicht ändern!

**Letzten Commit ergänzen:**
```bash
git commit -a --amend
```

**Ergänzen ohne Commit-Nachricht zu ändern:**
```bash
git commit --amend --no-edit
```

**Committer-Datum ändern:**
```bash
GIT_COMMITTER_DATE="datum" git commit --amend
```

**Autor-Datum ändern:**
```bash
git commit --amend --date="datum"
```

### Änderungen zwischenspeichern

**Aktuelle Änderungen temporär speichern:**
```bash
git stash
```

**Letzte gespeicherte Änderungen anwenden:**
```bash
git stash apply
```

**Spezifischen Stash anwenden:**
```bash
git stash apply stash@{stash_nummer}
```
> Verwenden Sie `git stash list`, um verfügbare Stashes zu sehen

**Letzten Stash entfernen:**
```bash
git stash drop
```

**Nicht committete Änderungen zu anderem Branch verschieben:**
```bash
git stash
git checkout branch2
git stash pop
```

---

## 🔍 Suchen

### Text-Suche

**Text in allen Dateien suchen:**
```bash
git grep "Hallo"
```

**In spezifischer Version suchen:**
```bash
git grep "Hallo" v2.5
```

### Commit-Suche

**Commits finden, die spezifisches Schlüsselwort eingeführt haben:**
```bash
git log -S 'schlüsselwort'
```

**Mit regulärem Ausdruck suchen:**
```bash
git log -S 'schlüsselwort' --pickaxe-regex
```

---

## 📖 Commit-Historie

### Basis-Historie

**Alle Commits anzeigen (detailliert):**
```bash
git log
```

**Commits anzeigen (eine Zeile je Commit):**
```bash
git log --oneline
```

**Commits von spezifischem Autor anzeigen:**
```bash
git log --author="benutzername"
```

**Änderungen für spezifische Datei anzeigen:**
```bash
git log -p <datei>
```

### Erweiterte Historie

**Branches vergleichen:**
```bash
git log --oneline <origin/master>..<remote/master> --left-right
```

**Anzeigen, wer was wann geändert hat:**
```bash
git blame <datei>
```

### Referenz-Logs

**Referenz-Log anzeigen:**
```bash
git reflog show
```

**Referenz-Log löschen:**
```bash
git reflog delete
```

---

## 📁 Verschieben / Umbenennen

**Datei umbenennen:**
```bash
git mv Index.txt Index.html
```

---

## 🌿 Branches & Tags

### Branches auflisten

**Lokale Branches auflisten:**
```bash
git branch
```

**Alle Branches auflisten (lokal + remote):**
```bash
git branch -a
```

**Remote Branches auflisten:**
```bash
git branch -r
```

**Zusammengeführte Branches auflisten:**
```bash
git branch --merged
```

### Branches wechseln & erstellen

**Zu existierendem Branch wechseln:**
```bash
git checkout <branch>
```

**Neuen Branch erstellen und dorthin wechseln:**
```bash
git checkout -b <branch>
```

**Zum vorherigen Branch wechseln:**
```bash
git checkout -
```

**Branch von existierendem Branch erstellen:**
```bash
git checkout -b <neuer_branch> <existierender_branch>
```

**Branch von spezifischem Commit erstellen:**
```bash
git checkout <commit-hash> -b <neuer_branch_name>
```

**Branch ohne Wechsel erstellen:**
```bash
git branch <neuer-branch>
```

**Tracking-Branch erstellen:**
```bash
git branch --track <neuer-branch> <remote-branch>
```

### Branch-Operationen

**Einzelne Datei von anderem Branch abrufen:**
```bash
git checkout <branch> -- <dateiname>
```

**Spezifischen Commit von anderem Branch anwenden:**
```bash
git cherry-pick <commit hash>
```

**Aktuellen Branch umbenennen:**
```bash
git branch -m <neuer_branch_name>
```

**Lokalen Branch löschen:**
```bash
git branch -d <branch>
```

**Lokalen Branch erzwungen löschen:**
```bash
git branch -D <branch>
```
> ⚠️ **Warnung:** Sie verlieren nicht zusammengeführte Änderungen!

### Tags

**Tag am HEAD erstellen:**
```bash
git tag <tag-name>
```

**Annotierten Tag erstellen:**
```bash
git tag -a <tag-name>
```

**Tag mit Nachricht erstellen:**
```bash
git tag <tag-name> -am 'Nachricht hier'
```

**Alle Tags auflisten:**
```bash
git tag
```

**Tags mit Nachrichten auflisten:**
```bash
git tag -n
```

---

## 🔄 Aktualisieren & Veröffentlichen

### Remote-Verwaltung

**Konfigurierte Remotes auflisten:**
```bash
git remote -v
```

**Remote-Informationen anzeigen:**
```bash
git remote show <remote>
```

**Neuen Remote hinzufügen:**
```bash
git remote add <remote> <url>
```

**Remote umbenennen:**
```bash
git remote rename <remote> <neuer_remote>
```

**Remote entfernen:**
```bash
git remote rm <remote>
```
> ℹ️ **Hinweis:** Dies entfernt nur die Remote-Referenz lokal, nicht das Remote-Repository selbst.

### Fetch & Pull

**Änderungen ohne Merge herunterladen:**
```bash
git fetch <remote>
```

**Änderungen herunterladen und mergen:**
```bash
git pull <remote> <branch>
```

**Änderungen vom Haupt-Branch abrufen:**
```bash
git pull origin master
```

**Mit Rebase pullen:**
```bash
git pull --rebase <remote> <branch>
```

### Push & Veröffentlichen

**Lokale Änderungen veröffentlichen:**
```bash
git push <remote> <branch>
```

**Remote Branch löschen:**
```bash
# Git v1.7.0+
git push <remote> --delete <branch>

# Git v1.5.0+
git push <remote> :<branch>
```

**Tags veröffentlichen:**
```bash
git push --tags
```

---

## 🔀 Merge & Rebase

### Merge-Operationen

**Branch in aktuellen HEAD mergen:**
```bash
git merge <branch>
```

**Merge-Tool global konfigurieren:**
```bash
git config --global merge.tool meld
```

**Konfiguriertes Merge-Tool verwenden:**
```bash
git mergetool
```

### Rebase-Operationen

> ⚠️ **Warnung:** Veröffentlichte Commits nicht rebasen!

**Aktuellen HEAD auf Branch rebasen:**
```bash
git rebase <branch>
```

**Rebase abbrechen:**
```bash
git rebase --abort
```

**Rebase nach Konfliktlösung fortsetzen:**
```bash
git rebase --continue
```

### Konfliktlösung

**Datei als gelöst markieren:**
```bash
git add <gelöste-datei>
```

**Gelöste Datei entfernen:**
```bash
git rm <gelöste-datei>
```

### Commits zusammenfassen

**Interaktives Rebase zum Zusammenfassen:**
```bash
git rebase -i <commit-direkt-vor-dem-ersten>
```

**Beispiel-Konfiguration zum Zusammenfassen:**
```
# Vorher
pick <commit_id>
pick <commit_id2>
pick <commit_id3>

# Nachher (commit_id2 und commit_id3 in commit_id zusammenfassen)
pick <commit_id>
squash <commit_id2>
squash <commit_id3>
```

---

## ↩️ Rückgängig machen

### Änderungen verwerfen

**Alle lokalen Änderungen verwerfen:**
```bash
git reset --hard HEAD
```

**Alle Dateien aus der Staging-Area entfernen:**
```bash
git reset HEAD
```

**Änderungen in spezifischer Datei verwerfen:**
```bash
git checkout HEAD <datei>
```

### Reset-Operationen

**Zu vorherigem Commit zurücksetzen (alle Änderungen verwerfen):**
```bash
git reset --hard <commit>
```

**Zu Remote Branch-Zustand zurücksetzen:**
```bash
git reset --hard <remote/branch>
# Beispiel: git reset --hard upstream/master
```

**Reset mit Änderungen als unstaged beibehalten:**
```bash
git reset <commit>
```

**Reset mit lokalen uncommitted Änderungen beibehalten:**
```bash
git reset --keep <commit>
```

### Commits rückgängig machen

**Commit rückgängig machen (neuen Commit mit gegenteiligen Änderungen erstellen):**
```bash
git revert <commit>
```

### Ignorierte Dateien bereinigen

**Versehentlich committete Dateien entfernen, die ignoriert werden sollten:**
```bash
git rm -r --cached .
git add .
git commit -m "ignorierte Dateien entfernen"
```

---

## 📦 Zwischenspeichern (Stash)

### Änderungen temporär speichern

**Aktuelle Änderungen zwischenspeichern:**
```bash
git stash
```

**Mit beschreibender Nachricht zwischenspeichern:**
```bash
git stash save "Beschreibende Nachricht"
```

**Alle Stashes anzeigen:**
```bash
git stash list
```

**Letzten Stash anwenden:**
```bash
git stash apply
```

**Spezifischen Stash anwenden:**
```bash
git stash apply stash@{0}
```

**Letzten Stash anwenden und entfernen:**
```bash
git stash pop
```

**Spezifischen Stash entfernen:**
```bash
git stash drop stash@{0}
```

**Alle Stashes entfernen:**
```bash
git stash clear
```

**Änderungen in einem Stash anzeigen:**
```bash
git stash show stash@{0}
```

**Branch aus Stash erstellen:**
```bash
git stash branch <branch-name> stash@{0}
```

---

## 🌊 Git Flow

**Verbesserter Git-flow:** [git-flow-avh](https://github.com/petervanderdoes/gitflow-avh)

### 📋 Inhaltsverzeichnis
- [🔧 Setup](#setup-1)
- [🚀 Erste Schritte](#erste-schritte)
- [✨ Features](#features)
- [🎁 Release erstellen](#release-erstellen)
- [🔥 Hotfixes](#hotfixes)
- [📊 Befehls-Übersicht](#befehls-übersicht)

---

### 🔧 Setup {#setup-1}

> **Voraussetzung:** Funktionierende Git-Installation erforderlich. Git-flow funktioniert auf macOS, Linux und Windows.

**macOS (Homebrew):**
```bash
brew install git-flow-avh
```

**macOS (MacPorts):**
```bash
port install git-flow
```

**Linux (Debian-basiert):**
```bash
sudo apt-get install git-flow
```

**Windows (Cygwin):**
> Benötigt wget und util-linux
```bash
wget -q -O - --no-check-certificate https://raw.githubusercontent.com/petervanderdoes/gitflow/develop/contrib/gitflow-installer.sh install <state> | bash
```

---

### 🚀 Erste Schritte

Git-flow benötigt Initialisierung, um Ihre Projekt-Konfiguration anzupassen.

**Initialisieren (interaktiv):**
```bash
git flow init
```
> Sie beantworten Fragen zu Branch-Namenskonventionen. Standardwerte werden empfohlen.

**Initialisieren (Standardwerte verwenden):**
```bash
git flow init -d
```

---

### ✨ Features

Features sind für die Entwicklung neuer Funktionalität für kommende Releases. Sie existieren typischerweise nur in Entwickler-Repositories.

**Neues Feature starten:**
```bash
git flow feature start MEINFEATURE
```
> Erstellt Feature-Branch basierend auf 'develop' und wechselt dorthin

**Feature beenden:**
```bash
git flow feature finish MEINFEATURE
```
> Dies wird:
> 1. MEINFEATURE in 'develop' mergen
> 2. Den Feature-Branch entfernen
> 3. Zurück zu 'develop' wechseln

**Feature veröffentlichen (für Zusammenarbeit):**
```bash
git flow feature publish MEINFEATURE
```

**Veröffentlichtes Feature abrufen:**
```bash
git flow feature pull origin MEINFEATURE
```

**Origin Feature verfolgen:**
```bash
git flow feature track MEINFEATURE
```

---

### 🎁 Release erstellen

Releases unterstützen die Vorbereitung neuer Produktions-Releases, erlauben kleinere Bugfixes und bereiten Meta-Daten vor.

**Release starten:**
```bash
git flow release start RELEASE [BASE]
```
> Erstellt Release-Branch von 'develop'. Optional [BASE] Commit SHA-1 angeben.

**Release veröffentlichen:**
```bash
git flow release publish RELEASE
```

**Remote Release verfolgen:**
```bash
git flow release track RELEASE
```

**Release beenden:**
```bash
git flow release finish RELEASE
```
> Dies wird:
> 1. Release-Branch in 'master' mergen
> 2. Das Release taggen
> 3. Release zurück in 'develop' mergen
> 4. Release-Branch entfernen

> 💡 **Nicht vergessen:** Tags mit `git push --tags` pushen

---

### 🔥 Hotfixes

Hotfixes addressieren kritische Probleme in Live-Produktionsversionen. Sie zweigen vom entsprechenden Tag auf master ab.

**Hotfix starten:**
```bash
git flow hotfix start VERSION [BASENAME]
```

**Hotfix beenden:**
```bash
git flow hotfix finish VERSION
```
> Mergt zurück in 'develop' und 'master', und taggt den Master-Merge

---

### 📊 Befehls-Übersicht

<p align="center">
    <img alt="Git Flow Befehle" src="../Img/git-flow-commands.png" height="270" width="460">
</p>

### 🌊 Git Flow Schema

<p align="center">
    <img alt="Git Flow Schema" src="../Img/git-flow-commands-without-flow.png">
</p>

---

## 💡 Nützliche Tipps

### Nützliche Aliases

**Nützliche Aliases konfigurieren:**
```bash
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
git config --global alias.visual '!gitk'
```

### .gitignore Dateien

**.gitignore Datei erstellen:**
```bash
echo "node_modules/" >> .gitignore
echo "*.log" >> .gitignore
echo ".env" >> .gitignore

# Bereits verfolgte Dateien ignorieren
git rm --cached <datei>
echo "<datei>" >> .gitignore
git add .gitignore
git commit -m "Datei zu .gitignore hinzufügen"
```

### Git Hooks

**Lokale Hooks konfigurieren:**
```bash
# Pre-commit Hook (Beispiel)
cat > .git/hooks/pre-commit << 'EOF'
#!/bin/sh
# Tests vor jedem Commit ausführen
npm test
EOF

chmod +x .git/hooks/pre-commit
```

---

## 🌍 Andere Sprachen

Dieses Cheat-Sheet ist in mehreren Sprachen verfügbar:

| Sprache | Link |
|---------|------|
| 🇺🇸 Englisch | [README.md](../README.md) |
| 🇸🇦 Arabisch | [git-cheat-sheet-ar.md](./git-cheat-sheet-ar.md) |
| 🇧🇩 Bengali | [git-cheat-sheet-bn.md](./git-cheat-sheet-bn.md) |
| 🇧🇷 Brasilianisches Portugiesisch | [git-cheat-sheet-pt_BR.md](./git-cheat-sheet-pt_BR.md) |
| 🇨🇳 Chinesisch | [git-cheat-sheet-zh.md](./git-cheat-sheet-zh.md) |
| 🇪🇸 Spanisch | [git-cheat-sheet-es.md](./git-cheat-sheet-es.md) |
| 🇬🇷 Griechisch | [git-cheat-sheet-el.md](./git-cheat-sheet-el.md) |
| 🇮🇳 Hindi | [git-cheat-sheet-hi.md](./git-cheat-sheet-hi.md) |
| 🇰🇷 Koreanisch | [git-cheat-sheet-ko.md](./git-cheat-sheet-ko.md) |
| 🇵🇱 Polnisch | [git-cheat-sheet-pl.md](./git-cheat-sheet-pl.md) |
| 🇹🇷 Türkisch | [git-cheat-sheet-tr.md](./git-cheat-sheet-tr.md) |

---

## 🤝 Beitragen

Wir begrüßen Beiträge! Sie können:

- 🐛 Fehler oder Tippfehler melden
- ✨ Neue Git-Befehle hinzufügen
- 🌍 In neue Sprachen übersetzen
- 💡 Erklärungen verbessern
- 📝 Formatierung verbessern

**Wie Sie beitragen:**
1. Forken Sie dieses Repository
2. Erstellen Sie Ihren Feature-Branch (`git checkout -b feature/FantastischesFeature`)
3. Committen Sie Ihre Änderungen (`git commit -m 'Fantastisches Feature hinzufügen'`)
4. Pushen Sie zum Branch (`git push origin feature/FantastischesFeature`)
5. Öffnen Sie einen Pull Request

---

## 📄 Lizenz

Dieses Projekt ist Open Source und unter der [MIT-Lizenz](LICENSE) verfügbar.

---

## 📖 Zusätzliche Ressourcen

- [Offizielle Git-Dokumentation](https://git-scm.com/doc)
- [Atlassian Git-Tutorials](https://www.atlassian.com/git/tutorials)
- [GitHub Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
- [Interaktives Git-Tutorial](https://learngitbranching.js.org/)
- [Pro Git Buch (kostenlos)](https://git-scm.com/book/de/v2)
- [Git Workflows](https://www.atlassian.com/git/tutorials/comparing-workflows)

---

<p align="center">
    <b>⭐ Geben Sie diesem Repository einen Stern, wenn es hilfreich war!</b>
</p>
