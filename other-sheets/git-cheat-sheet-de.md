Git and Git Flow Cheat Sheet [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)
===============
<hr>
<p align="center">
    <img alt="Git" src="./Img/git-logo.png" height="190" width="455">
</p>
<hr>

# Verfügbare Sprachen:

1. [Arabisches Git Cheat Sheet](https://github.com/arslanbilal/git-cheat-sheet/blob/master/other-sheets/git-cheat-sheet-ar.md)
2. [Chinesisches Git Cheat Sheet](https://github.com/arslanbilal/git-cheat-sheet/blob/master/other-sheets/git-cheat-sheet-zh.md)
3. [Hindi Git Cheat Sheet](https://github.com/arslanbilal/git-cheat-sheet/blob/master/other-sheets/git-cheat-sheet-hi.md)
4. [Türkisches Git Cheat Sheet](https://github.com/arslanbilal/git-cheat-sheet/blob/master/other-sheets/git-cheat-sheet-tr.md)
5. [Spanisches Git Cheat Sheet](https://github.com/arslanbilal/git-cheat-sheet/blob/master/other-sheets/git-cheat-sheet-es.md)
6. [Griechisches Git Cheat Sheet](https://github.com/arslanbilal/git-cheat-sheet/blob/master/other-sheets/git-cheat-sheet-el.md)
7. [Brasilianisch Portugisisches Git Cheat Sheet](https://github.com/arslanbilal/git-cheat-sheet/blob/master/other-sheets/git-cheat-sheet-pt_BR.md)
8. [Koreanisches Git Cheat Sheet](https://github.com/arslanbilal/git-cheat-sheet/blob/master/other-sheets/git-cheat-sheet-ko.md)
9. [Polnisches Git Cheat Sheet](https://github.com/arslanbilal/git-cheat-sheet/blob/master/other-sheets/git-cheat-sheet-pl.md)

Git Cheat Sheet erspart Ihnen das Auswendiglernen aller Befehle.

Fühlen Sie sich frei, einen Beitrag zu leisten, aktualisieren Sie Grammatikfehler. Sie können auch Ihre eigene Sprachdatei hinzufügen.

<hr>

Git Cheat Sheet Deutsch
===============
### Index
* [Installation](#setup)
* [Konfigurationsdateien](#configuration-files)
* [Erstellen](#create)
* [Lokale Änderungen](#local-changes)
* [Suche](#search)
* [Commit Historie](#commit-history)
* [Zweige & Tags](#branches--tags)
* [Aktualisieren & Veröffentlichen](#update--publish)
* [Zusammenführen & Zurücksetzen](#merge--rebase)
* [Rückgängig machen](#undo)
* [Git Flow](#git-flow)


<hr>

## Installation

##### Zeige die aktuelle Konfiguration:
```
$ git config --list
```
##### Zeige die Repository Konfiguration:
```
$ git config --local --list
```

##### Zeige die globale Konfiguration:
```
$ git config --global --list
```

##### Zeige die System Konfiguration:
```
$ git config --system --list
```

##### Lege einen Namen fest, mit dem Sie beim Überprüfen des Versionsverlaufs identifiziert werden können:
```
$ git config --global user.name "[Vorname Nachname]"
```

##### Lege eine E-Mail-Adresse fest, die jeder Verlaufsmarkierung zugeordnet wird:
```
$ git config --global user.email "[gültige-email]"
```

##### Stelle die automatische Farbgebung der Befehlszeile für Git ein
```
$ git config --global color.ui auto
```

##### Globalen Editor für Commits festlegen
```
$ git config --global core.editor vi
```

<hr>

## Konfigurationsdateien

##### Repository spezifische Konfigurationsdateien [--local]:
```
<repo>/.git/config
```

##### Benutzer spezifische Konfigurationsdatei [--global]:
```
~/.gitconfig
```

##### Systemweite Konfigurationsdatei [--system]:
```
/etc/gitconfig
```

<hr>

## Erstellen

##### Ein existierendes Repository clonen:

Es gibt 2 Wege:

Via SSH

```
$ git clone ssh://benutzer@domain.com/repo.git
```

Via HTTP

```
$ git clone http://domain.com/benutzer/repo.git
```

##### Erstelle ein neues lokales Repository im aktuellen Verzeichnis:
```
$ git init
```

##### Erstelle ein neues lokales Repository in einem bestimmten Verzeichnis:
```
$ git init <Verzeichnis>
```

<hr>

## Lokale Änderungen

##### Änderungen im Arbeitsverzeichnis:
```
$ git status
```

##### Zeige Änderungen an nachverfolgten Dateien:
```
$ git diff
```

##### Zeige Änderungen/Unterschiede einer bestimmten Datei:
```
$ git diff <Datei>
```

##### Füge alle aktuellen Änderungen zum nächsten Commit hinzu:
```
$ git add .
```

##### Füge Änderungen an &lt;Datei&gt; zum nächsten Commit hinzu:
```
$ git add -p <Datei>
```

##### Füge dem nächsten Commit nur die genannten Dateien hinzu:
```
$ git add <Dateiname1> <Dateiname2>
```

##### Commit aller lokalen Änderungen in nachverfolgten Dateien:
```
$ git commit -a
```

##### Commit von zuvor bereitgestellte Änderungen:
```
$ git commit
```

##### Commit mit Nachricht:
```
$ git commit -m 'Nachricht hier'
```

##### Commit mit überspringen des Staging-Bereichs und hinzufügen einer Nachricht:
```
$ git commit -am 'Nachricht hier'
```

##### Commit zu einem früheren Datum:
```
$ git commit --date="`date --date='n day ago'`" -am "<Commit Nachricht hier>"
```

##### Ändere letzten Commit:<br>
<em><sub>Ändere keine veröffentlichten Commits!</sub></em>

```
$ git commit -a --amend
```

##### Mit letztem Commit ergänzen, aber vorherige Commit-Protokollmeldung verwenden
<em><sub>Ändere keine veröffentlichten Commits!</sub></em>

```shell
$ git commit --amend --no-edit
```

##### Commit-Datum des letzten Commit ändern:
```
GIT_COMMITTER_DATE="date" git commit --amend
```

##### Ändere das Datum des letzten Commit:
```shell
$ git commit --amend --date="date"
```

##### Nicht committete Änderungen aus dem aktuellen Zweig in einen anderen Zweig verschieben:<br>
```
$ git stash
$ git checkout Zweig2
$ git stash pop
```

##### Stelle im Stash gespeicherte Änderungen auf dem aktuellen Zweig wieder her:
```shell
$ git stash apply
```

#### Stelle einen bestimmten Stash auf dem aktuellen Zweig wieder her:
- *{stash_nummer}* kann bezogen werden von `git stash list`

```shell
$ git stash apply stash@{stash_nummer}
```

##### Entferne den letzten Satz gespeicherter Änderungen:
```
$ git stash drop
```

<hr>

## Suche

##### Eine Textsuche in allen Dateien im Verzeichnis:
```
$ git grep "Hallo"
```

##### Textsuche in jeder Version:
```
$ git grep "Hello" v2.5
```

##### Commits anzeigen, die ein bestimmtes Schlüsselwort eingeführt haben
```
$ git log -S 'Schlüsselwort'
```

##### Commits anzeigen, die ein bestimmtes Schlüsselwort eingeführt haben (mit Hilfe eines regulären Ausdrucks)
```
$ git log -S 'Schlüsselwort' --pickaxe-regex
```

<hr>

## Commit Historie

##### Alle Commits anzeigen, beginnend mit dem neuesten (es werden Hash, Autoreninformationen, Datum des Commit und Titel des Commits angezeigt):
```
$ git log
```

##### Alle Commits anzeigen (es werden nur der Commit-Hash und die Commit-Nachricht angezeigt):
```
$ git log --oneline
```

##### Alle Commits eines bestimmten Benutzers anzeigen:
```
$ git log --author="Benutzername"
```

##### Zeige Änderungen im Laufe der Zeit für eine bestimmte Datei an:
```
$ git log -p <Datei>
```

##### Zeigt Commits an, die nur in remote/branch auf der rechten Seite vorhanden sind
```
$ git log --oneline <origin/master>..<remote/master> --left-right
```

##### Wer hat wann, was in &lt;Datei&gt;  geändert:
```
$ git blame <Datei>
```

##### Referenzprotokoll anzeigen:
```
$ git reflog show
```

##### Referenzprotokoll löschen:
```
$ git reflog delete
```
<hr>

## Verschieben / Umbenennen

##### Eine Datei umbenennen:

Index.txt umbenennen zu Index.html

```
$ git mv Index.txt Index.html
```

<hr>

## Zweige & Tags

##### Zeige alle lokalen Zweige:
```
$ git branch
```

#### Zeige alle lokalen und entfernten Zweige
```
$ git branch -a
```

##### Zeige alle entfernten Zweige:
```
$ git branch -r
```

##### HEAD-Zweig wechseln:
```
$ git checkout <Zweig>
```

##### Einzelne Datei aus einem anderen Zweig auschecken
```
$ git checkout <Zweig> -- <Datei>
```

##### Neuen Zweig erstellen und auschecken:
```
$ git checkout -b <Zweig>
```

##### In den vorherigen Zweig wechseln, ohne den Namen explizit anzugeben:
```
$ git checkout -
```

##### Erstelle einen neuen Zweig aus einem bestehenden Zweig und wechsle zum neuen Zweig:
```
$ git checkout -b <Neuer_Zweig> <Existierender_Zweig>
```


#### Auschecken und einen neuen Zweig aus einem bestehenden Commit erstellen
```
$ git checkout <commit-hash> -b <Neuer_Zweig_Name>
```


##### Erstelle einen neuen Zweig basierend auf dem aktuellen HEAD
```
$ git branch <Neuer_Zweig>
```

##### Erstelle einen neuen nachverfolgenden Zweig basierend auf einem entfernten Zweig:
```
$ git branch --track <Neuer_Zweig> <Entfernter_Zweig>
```

##### Einen lokalen Zweig löschen:
```
$ git branch -d <Zweig>
```

##### Benenne den aktuellen Zweig in einen neuen Namen um
```shell
$ git branch -m <Neuer_Zweig_Name>
```

##### Erzwinge löschen eines lokalen Zweigs:
<em><sub>Nicht zusammengeführte Änderungen gehen verloren!</sub></em>

```
$ git branch -D <Zweig>
```

##### Markiere `HEAD` mit einem Tag:
```
$ git tag <Tag-Name>
```

##### Markiere `HEAD` mit einem Tag und öffne den Editor, um eine Nachricht einzufügen:
```
$ git tag -a <Tag-Name>
```

##### Markiere `HEAD` mit einem Tag, das eine Nachricht enthält:
```
$ git tag <Tag-Name> -am 'Nachricht hier'
```

##### Liste alle Tags auf:
```
$ git tag
```

##### Alle Tags mit ihren Nachrichten auflisten (Tag-Nachricht oder Commit-Nachricht, wenn Tag keine Nachricht hat):
```
$ git tag -n
```

<hr>

## Aktualisieren & Veröffentlichen

##### Alle aktuell konfigurierten entfernten Repositories auflisten:
```
$ git remote -v
```

##### Zeige Informationen über ein entferntes Repository:
```
$ git remote show <remote-Repository>
```

##### Füge ein neues remote Repository mit dem Namen &lt;remote-Repository&gt; hinzu:
```
$ git remote add <remote-Repository> <url>
```

##### Benenne ein entferntes Repository um, von &lt;remote-Repository&gt; zu &lt;neues-remote-Repository&gt;:
```
$ git remote rename <remote-Repository> <neues-remote-Repository>
```

##### Ein entferntes Repository löschen:
```
$ git remote rm <remote-Repository>
```

<em><sub>Hinweis: git remote rm löscht das entfernte Repository nicht vom Server. Es entfernt einfach das Repository und dessen Referenzen aus Ihrem lokalen Repository.</sub></em>

##### Alle Änderungen von &lt;remote-Repository&gt; herunterladen, aber nicht in HEAD integrieren:
```
$ git fetch <remote-Repository>
```

##### Änderungen herunterladen und direkt in HEAD zusammenführen/integrieren:
```
$ git remote pull <remote-Repository> <url>
```

##### Alle Änderungen von HEAD in das lokale Repository übertragen:
```
$ git pull origin master
```

##### Hole alle Änderungen von HEAD in das lokale Repository ohne Zusammenführung
```
$ git pull --rebase <remote-Repository> <Zweig>
```

##### Lokale Änderungen auf einem entfernten Repository veröffentlichen:
```
$ git push <remote-Repository> <Zweig>
```

##### Einen Zweig auf dem entfernten Repository löschen:
```
$ git push <remote-Repository> :<Zweig> (since Git v1.5.0)
```
ODER
```
$ git push <remote-Repository> --delete <Zweig> (since Git v1.7.0)
```

##### Tags veröffentlichen:
```
$ git push --tags
```
<hr>

#### Das Zusammenführungstool global auf meld (editor) setzen
```bash
$ git config --global merge.tool meld
```

##### Nutze konfiguriertes Zusammenführungstool, um Konflikte zu lösen:
```
$ git mergetool
```

## Zusammenführen & Zurücksetzen

##### Zweig mit aktuellem HEAD zusammenführen:
```
$ git merge <Zweig>
```

#### Liste zusammengeführte Zweige auf
```
$ git branch --merged
```

##### Setze akzuellen HEAD auf &lt;Zweig&gt; zurück:<br>
<em><sub>Setze keine veröffentlichten Zweige zurück!</sub></em>

```
$ git rebase <Zweig>
```

##### Ein Zurücksetzen abbrechen:
```
$ git rebase --abort
```

##### Ein Zurücksetzen fortführen nachdem Konflikte gelöst wurden:
```
$ git rebase --continue
```

##### Verwende einen Editor, um Konflikte manuell zu lösen und (nach der Lösung) die Datei als gelöst zu markieren:
```
$ git add <gelöste-Datei>
```

```
$ git rm <gelöste-Datei>
```

##### Commits squashen:
```
$ git rebase -i <commit-direkt-vor-dem-ersten>
```

Ändere,

```
pick <commit_id>
pick <commit_id2>
pick <commit_id3>
```

zu,

```
pick <commit_id>
squash <commit_id2>
squash <commit_id3>
```
<hr>

## Rückgängig machen

##### Alle lokalen Änderungen im Arbeitsverzeichnis verwerfen:
```
$ git reset --hard HEAD
```

##### Holen Dateien aus dem Staging-Bereich (d.h. mache das letzte `git add` rückgängig):
```
$ git reset HEAD
```

##### Lokale Änderungen in einer bestimmten Datei verwerfen:
```
$ git checkout HEAD <Datei>
```

##### Einen Commit rückgängig machen (indem ein neuer Commit mit gegensätzlichen Änderungen erstellt wird):
```
$ git revert <commit>
```

##### Setze HEAD-Zeiger auf einen früheren Commit zurück und verwirf alle Änderungen seitdem:
```
$ git reset --hard <commit>
```

##### Setze HEAD-Zeiger auf den aktuellen Zustand eines entfernten Zweigs zurück.
```
$ git reset --hard <remote-Repository/Zweig> z.B., upstream/master, origin/my-feature
```

##### Setze HEAD-Zeiger auf einen früheren Commit zurück und behalte alle Änderungen als nicht bereitgestellte Änderungen bei:
```
$ git reset <commit>
```

##### Setze HEAD-Zeiger auf einen früheren Commit zurück und behalte nicht committete lokale Änderungen bei:
```
$ git reset --keep <commit>
```

##### Entferne Dateien, die versehentlich commitet wurden, bevor sie zu .gitignore hinzugefügt wurden
```
$ git rm -r --cached .
$ git add .
$ git commit -m "Entferne Datei xyz"
```
<hr>

## Git-Flow
Verbessert [Git-flow](https://github.com/petervanderdoes/gitflow-avh)

### Index
* [Installation](#setup)
* [Einstieg](#getting-started)
* [Funktionen](#features)
* [Ein Release erstellen](#make-a-release)
* [Hotfixes](#hotfixes)
* [Kommandos](#commands)

<hr>

### Installation
###### Voraussetzung ist eine funktionierende Git-Installation. Git-Flow funktioniert unter OSX, Linux und Windows.

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
###### Sie benötigen wget und util-linux, um git-flow zu installieren.
```bash
$ wget -q -O - --no-check-certificate https://raw.githubusercontent.com/petervanderdoes/gitflow/develop/contrib/gitflow-installer.sh install <state> | bash
```
<hr>

### Einstieg
###### Git-Flow muss initialisiert werden, um Ihr Projekt-Setup anzupassen. Beginnen Sie mit der Verwendung von Git-Flow, indem Sie es in einem vorhandenen Git-Repository initialisieren:
##### Initialisierung:
###### Sie müssen einige Fragen zu den Namenskonventionen für Ihre Zweige beantworten. Es wird empfohlen, die Standardwerte zu verwenden.
```shell
git flow init
```
ODER
###### Um Standardwerte zu benutzen
```shell
git flow init -d
```
<hr>

### Funktionen
###### Entwickeln Sie neue Funktionen für kommende Versionen. Existieren normalerweise nur in Entwickler-Repositorys.
##### Eine neue Funktion starten:
###### Diese Aktion erstellt einen neuen Funktions-Zweig basierend auf „develop“ und wechselt zu diesem.
```
git flow feature start MEINEFUNKTION
```

##### Eine Funktion fertigstellen:
###### Beenden Sie die Entwicklung einer Funktion. Diese Aktion führt Folgendes aus:
###### 1) MEINEFUNKTION mit 'develop' zusammenführen.
###### 2) Entfernt den Funktions-Zweig.
###### 3) Wechselt zurück zum 'develop' Zweig
```
git flow feature finish MEINEFUNKTION
```

##### Eine Funktion veröffentlichen:
###### Entwickeln Sie eine Funktion in Zusammenarbeit? Veröffentlichen Sie eine Funktion auf dem Remote-Server, damit sie von anderen Benutzern verwendet werden kann.
```
git flow feature publish MEINEFUNKTION
```

##### Abrufen einer veröffentlichten Funktion:
###### Abrufen einer von einem anderen Benutzer veröffentlichten Funktion.
```
git flow feature pull origin MEINEFUNKTION
```

##### Verfolgen eines einer Funktion:
###### Sie können ein Feature auf origin verfolgen, indem Sie:
```
git flow feature track MEINEFUNKTION
```
<hr>

### Ein Release erstellen
###### Unterstützen Sie die Vorbereitung einer neuen Produktionsversion. Lassen Sie kleinere Fehlerkorrekturen zu und bereiten Sie Metadaten für eine Veröffentlichung vor.

##### Ein Release beginnen:
###### Um ein Release zu starten, verwenden Sie den Befehl git flow release. Er erstellt einen Release-Zweig, der aus dem 'develop'-Zweig erstellt wird. Sie können optional einen [BASE] Commit sha-1 Hash angeben, von dem aus die Veröffentlichung gestartet werden soll. Der Commit muss sich im Zweig „develop“ befinden.
```
git flow release start RELEASE [BASE]
```
###### Es ist ratsam, den Release-Zweig nach seiner Erstellung zu veröffentlichen, um Release-Commits durch andere Entwickler zu ermöglichen. Machen Sie es ähnlich wie beim Veröffentlichen von Funktionen mit dem Befehl:
```
git flow release publish RELEASE
```
###### (Sie können eine Remote-Freigabe verfolgen mit dem: ```git flow release track RELEASE``` Befehl)

##### Ein Release abschließen:
###### Das Fertigstellen eines Release ist einer der großen Schritte beim Git-Branching. Er führt mehrere Aktionen aus:
###### 1) Führt den Release-Zweig zurück in den 'master' Zweig
###### 2) Tagged das Release mit dessen Namen
###### 3) Führt das Release zurück in den 'develop' Zweig
###### 4) Entfernt den Release-Zweig
```
git flow release finish RELEASE
```
###### Vergessen Sie nicht, Ihre Tags mit ```git push --tags``` zu veröffentlichen

<hr>

### Hotfixes
###### Hotfixes entstehen aus der Notwendigkeit, sofort auf einen unerwünschten Zustand einer Live-Produktionsversion zu reagieren. Kann von dem entsprechenden Tag auf dem Master-Zweig abgezweigt werden, der die Produktionsversion markiert.

##### Git flow hotfix Start:
###### Wie die anderen Git-Flow-Befehle wird ein Hotfix gestartet mit
```
$ git flow hotfix start VERSION [BASENAME]
```
###### Das Versionsargument markiert dabei den neuen Hotfix-Release-Namen. Optional können Sie einen Basisnamen angeben, von dem aus gestartet werden soll.

##### Einen Hotfix abschließen:
###### Durch das Fertigstellen eines Hotfixes wird er wieder in Develop und Master zusammengeführt. Zusätzlich ist der Master-Merge mit der Hotfix-Version gekennzeichnet
```
git flow hotfix finish VERSION
```
<hr>

### Kommandos
<p align="center">
    <img alt="Git" src="./Img/git-flow-commands.png" height="270" width="460">
</p>
<hr>

### Git flow Schema

<p align="center">
    <img alt="Git" src="Img/git-flow-commands-without-flow.png">
</p>
<hr>

