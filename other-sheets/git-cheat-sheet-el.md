# Σύντομος Οδηγός Git και Git Flow 
[![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

<p align="center">
    <img alt="Git" src="../Img/git-logo.png" height="190" width="455">
</p>

---

## 📖 Σχετικά

Αυτός ο περιεκτικός σύντομος οδηγός Git σας βοηθά να κατακτήσετε τις εντολές Git χωρίς να χρειάζεται να τις απομνημονεύσετε όλες. Είτε είστε αρχάριος είτε έμπειρος προγραμματιστής, αυτός ο οδηγός παρέχει γρήγορη αναφορά στις βασικές λειτουργίες Git.

**Οι συνεισφορές είναι ευπρόσδεκτες!** Μπορείτε να:
- Διορθώσετε γραμματικά λάθη
- Προσθέσετε νέες εντολές
- Μεταφράσετε στη γλώσσα σας
- Βελτιώσετε τις εξηγήσεις

---
## 📋 Πίνακας Περιεχομένων

- [🔧 Ρύθμιση](#-ρύθμιση)
- [⚙️ Αρχεία Ρυθμίσεων](#️-αρχεία-ρυθμίσεων)
- [�� Δημιουργία Αποθετηρίου](#-δημιουργία-αποθετηρίου)
- [📝 Τοπικές Αλλαγές](#-τοπικές-αλλαγές)
- [🔍 Αναζήτηση](#-αναζήτηση)
- [�� Ιστορικό Υποβολών](#-ιστορικό-υποβολών)
- [📁 Μετακίνηση / Μετονομασία](#-μετακίνηση--μετονομασία)
- [🌿 Κλάδοι & Ετικέτες](#-κλάδοι--ετικέτες)
- [🔄 Ενημέρωση & Δημοσίευση](#-ενημέρωση--δημοσίευση)
- [🔀 Συγχώνευση & Rebase](#-συγχώνευση--rebase)
- [↩️ Αναίρεση](#️-αναίρεση)
- [🌊 Git Flow](#-git-flow)
- [🌍 Άλλες Γλώσσες](#-άλλες-γλώσσες)

---

## 🔧 Ρύθμιση

### Προβολή Ρυθμίσεων

**Εμφάνιση τρέχουσας ρύθμισης:**
```bash
git config --list
```

**Εμφάνιση ρυθμίσεων αποθετηρίου:**
```bash
git config --local --list
```

**Εμφάνιση καθολικών ρυθμίσεων:**
```bash
git config --global --list
```

**Εμφάνιση ρυθμίσεων συστήματος:**
```bash
git config --system --list
```

### Ρύθμιση Χρήστη

**Ορισμός ονόματος για το ιστορικό εκδόσεων:**
```bash
git config --global user.name "[firstname lastname]"
```

**Ορισμός διεύθυνσης email:**
```bash
git config --global user.email "[valid-email]"
```

### Ρυθμίσεις Εμφάνισης & Επεξεργαστή

**Ενεργοποίηση αυτόματου χρωματισμού γραμμής εντολών:**
```bash
git config --global color.ui auto
```

**Ορισμός καθολικού επεξεργαστή για υποβολές:**
```bash
git config --global core.editor vi
```

---

## ⚙️ Αρχεία Ρυθμίσεων

| Εύρος | Τοποθεσία | Σημαία Εντολής |
|-------|----------|--------------|
| **Αποθετήριο** | `<repo>/.git/config` | `--local` |
| **Χρήστης** | `~/.gitconfig` | `--global` |
| **Σύστημα** | `/etc/gitconfig` | `--system` |

---

## 🆕 Δημιουργία Αποθετηρίου

### Κλωνοποίηση Υπάρχοντος Αποθετηρίου

**Μέσω SSH:**
```bash
git clone ssh://user@domain.com/repo.git
```

**Μέσω HTTPS:**
```bash
git clone https://domain.com/user/repo.git
```

### Αρχικοποίηση Νέου Αποθετηρίου

**Δημιουργία αποθετηρίου στον τρέχοντα κατάλογο:**
```bash
git init
```

**Δημιουργία αποθετηρίου σε συγκεκριμένο κατάλογο:**
```bash
git init <directory>
```

---

## 📝 Τοπικές Αλλαγές

### Έλεγχος Κατάστασης & Διαφορών

**Προβολή κατάστασης καταλόγου εργασίας:**
```bash
git status
```

**Εμφάνιση αλλαγών σε παρακολουθούμενα αρχεία:**
```bash
git diff
```

**Εμφάνιση αλλαγών σε συγκεκριμένο αρχείο:**
```bash
git diff <file>
```

### Προσθήκη Αλλαγών στο Staging

**Προσθήκη όλων των τρεχουσών αλλαγών:**
```bash
git add .
```

**Προσθήκη συγκεκριμένων αρχείων:**
```bash
git add <filename1> <filename2>
```

**Διαδραστική προσθήκη τμημάτων αρχείου:**
```bash
git add -p <file>
```

### Υποβολή Αλλαγών

**Υποβολή όλων των αλλαγών παρακολουθούμενων αρχείων:**
```bash
git commit -a
```

**Υποβολή αλλαγών στο staging:**
```bash
git commit
```

**Υποβολή με μήνυμα:**
```bash
git commit -m 'message here'
```

**Παράλειψη staging και υποβολή με μήνυμα:**
```bash
git commit -am 'message here'
```

**Υποβολή με συγκεκριμένη ημερομηνία:**
```bash
git commit --date="`date --date='n day ago'`" -am "<Commit Message Here>"
```

### Τροποποίηση Τελευταίας Υποβολής

> ⚠️ **Προσοχή:** Μην τροποποιείτε δημοσιευμένες υποβολές!

**Τροποποίηση τελευταίας υποβολής:**
```bash
git commit -a --amend
```

**Τροποποίηση χωρίς αλλαγή μηνύματος υποβολής:**
```bash
git commit --amend --no-edit
```

**Αλλαγή ημερομηνίας committer:**
```bash
GIT_COMMITTER_DATE="date" git commit --amend
```

**Αλλαγή ημερομηνίας συγγραφέα:**
```bash
git commit --amend --date="date"
```

### Προσωρινή Αποθήκευση Αλλαγών

**Προσωρινή αποθήκευση τρεχουσών αλλαγών:**
```bash
git stash
```

**Εφαρμογή τελευταίων αποθηκευμένων αλλαγών:**
```bash
git stash apply
```

**Εφαρμογή συγκεκριμένου stash:**
```bash
git stash apply stash@{stash_number}
```
> Χρησιμοποιήστε `git stash list` για να δείτε τα διαθέσιμα stashes

**Αφαίρεση τελευταίου stash:**
```bash
git stash drop
```

**Μεταφορά μη υποβληθεισών αλλαγών σε άλλο κλάδο:**
```bash
git stash
git checkout branch2
git stash pop
```

---

## 🔍 Αναζήτηση

### Αναζήτηση Κειμένου

**Αναζήτηση κειμένου σε όλα τα αρχεία:**
```bash
git grep "Hello"
```

**Αναζήτηση σε συγκεκριμένη έκδοση:**
```bash
git grep "Hello" v2.5
```

### Αναζήτηση Υποβολών

**Εύρεση υποβολών που εισήγαγαν συγκεκριμένη λέξη-κλειδί:**
```bash
git log -S 'keyword'
```

**Αναζήτηση με κανονική έκφραση:**
```bash
git log -S 'keyword' --pickaxe-regex
```

---

## 📖 Ιστορικό Υποβολών

### Βασικό Ιστορικό

**Εμφάνιση όλων των υποβολών (αναλυτικά):**
```bash
git log
```

**Εμφάνιση υποβολών (μία γραμμή ανά υποβολή):**
```bash
git log --oneline
```

**Εμφάνιση υποβολών συγκεκριμένου συγγραφέα:**
```bash
git log --author="username"
```

**Εμφάνιση αλλαγών για συγκεκριμένο αρχείο:**
```bash
git log -p <file>
```

### Προχωρημένο Ιστορικό

**Σύγκριση κλάδων:**
```bash
git log --oneline <origin/master>..<remote/master> --left-right
```

**Εμφάνιση ποιος άλλαξε τι και πότε:**
```bash
git blame <file>
```

### Αρχεία Αναφοράς

**Εμφάνιση αρχείου αναφοράς:**
```bash
git reflog show
```

**Διαγραφή αρχείου αναφοράς:**
```bash
git reflog delete
```

---

## 📁 Μετακίνηση / Μετονομασία

**Μετονομασία αρχείου:**
```bash
git mv Index.txt Index.html
```

---

## 🌿 Κλάδοι & Ετικέτες

### Λίστα Κλάδων

**Λίστα τοπικών κλάδων:**
```bash
git branch
```

**Λίστα όλων των κλάδων (τοπικών + απομακρυσμένων):**
```bash
git branch -a
```

**Λίστα απομακρυσμένων κλάδων:**
```bash
git branch -r
```

**Λίστα συγχωνευμένων κλάδων:**
```bash
git branch --merged
```

### Εναλλαγή & Δημιουργία Κλάδων

**Εναλλαγή σε υπάρχοντα κλάδο:**
```bash
git checkout <branch>
```

**Δημιουργία και εναλλαγή σε νέο κλάδο:**
```bash
git checkout -b <branch>
```

**Εναλλαγή στον προηγούμενο κλάδο:**
```bash
git checkout -
```

**Δημιουργία κλάδου από υπάρχοντα κλάδο:**
```bash
git checkout -b <new_branch> <existing_branch>
```

**Δημιουργία κλάδου από συγκεκριμένη υποβολή:**
```bash
git checkout <commit-hash> -b <new_branch_name>
```

**Δημιουργία κλάδου χωρίς εναλλαγή:**
```bash
git branch <new-branch>
```

**Δημιουργία κλάδου παρακολούθησης:**
```bash
git branch --track <new-branch> <remote-branch>
```

### Λειτουργίες Κλάδων

**Checkout μεμονωμένου αρχείου από διαφορετικό κλάδο:**
```bash
git checkout <branch> -- <filename>
```

**Εφαρμογή συγκεκριμένης υποβολής από άλλο κλάδο:**
```bash
git cherry-pick <commit hash>
```

**Μετονομασία τρέχοντος κλάδου:**
```bash
git branch -m <new_branch_name>
```

**Διαγραφή τοπικού κλάδου:**
```bash
git branch -d <branch>
```

**Αναγκαστική διαγραφή τοπικού κλάδου:**
```bash
git branch -D <branch>
```
> ⚠️ **Προσοχή:** Θα χάσετε τις μη συγχωνευμένες αλλαγές!

### Ετικέτες

**Δημιουργία ετικέτας στο HEAD:**
```bash
git tag <tag-name>
```

**Δημιουργία σχολιασμένης ετικέτας:**
```bash
git tag -a <tag-name>
```

**Δημιουργία ετικέτας με μήνυμα:**
```bash
git tag <tag-name> -am 'message here'
```

**Λίστα όλων των ετικετών:**
```bash
git tag
```

**Λίστα ετικετών με μηνύματα:**
```bash
git tag -n
```

---

## 🔄 Ενημέρωση & Δημοσίευση

### Διαχείριση Απομακρυσμένων

**Λίστα ρυθμισμένων απομακρυσμένων:**
```bash
git remote -v
```

**Εμφάνιση πληροφοριών απομακρυσμένου:**
```bash
git remote show <remote>
```

**Προσθήκη νέου απομακρυσμένου:**
```bash
git remote add <remote> <url>
```

**Μετονομασία απομακρυσμένου:**
```bash
git remote rename <remote> <new_remote>
```

**Αφαίρεση απομακρυσμένου:**
```bash
git remote rm <remote>
```
> ℹ️ **Σημείωση:** Αυτό αφαιρεί μόνο την τοπική αναφορά στο απομακρυσμένο, όχι το ίδιο το απομακρυσμένο αποθετήριο.

### Fetch & Pull

**Λήψη αλλαγών χωρίς συγχώνευση:**
```bash
git fetch <remote>
```

**Λήψη και συγχώνευση αλλαγών:**
```bash
git pull <remote> <branch>
```

**Λήψη αλλαγών από τον κύριο κλάδο:**
```bash
git pull origin master
```

**Pull με rebase:**
```bash
git pull --rebase <remote> <branch>
```

### Push & Δημοσίευση

**Δημοσίευση τοπικών αλλαγών:**
```bash
git push <remote> <branch>
```

**Διαγραφή απομακρυσμένου κλάδου:**
```bash
# Git v1.7.0+
git push <remote> --delete <branch>

# Git v1.5.0+
git push <remote> :<branch>
```

**Δημοσίευση ετικετών:**
```bash
git push --tags
```

---

## 🔀 Συγχώνευση & Rebase

### Λειτουργίες Συγχώνευσης

**Συγχώνευση κλάδου στο τρέχον HEAD:**
```bash
git merge <branch>
```

**Ρύθμιση εργαλείου συγχώνευσης καθολικά:**
```bash
git config --global merge.tool meld
```

**Χρήση ρυθμισμένου εργαλείου συγχώνευσης:**
```bash
git mergetool
```

### Λειτουργίες Rebase

> ⚠️ **Προσοχή:** Μην κάνετε rebase σε δημοσιευμένες υποβολές!

**Rebase τρέχοντος HEAD πάνω σε κλάδο:**
```bash
git rebase <branch>
```

**Ακύρωση rebase:**
```bash
git rebase --abort
```

**Συνέχιση rebase μετά την επίλυση συγκρούσεων:**
```bash
git rebase --continue
```

### Επίλυση Συγκρούσεων

**Σήμανση αρχείου ως επιλυμένου:**
```bash
git add <resolved-file>
```

**Αφαίρεση επιλυμένου αρχείου:**
```bash
git rm <resolved-file>
```

### Συμπίεση Υποβολών

**Διαδραστικό rebase για συμπίεση:**
```bash
git rebase -i <commit-just-before-first>
```

**Παράδειγμα ρύθμισης συμπίεσης:**
```
# Πριν
pick <commit_id>
pick <commit_id2>
pick <commit_id3>

# Μετά (συμπίεση commit_id2 και commit_id3 στο commit_id)
pick <commit_id>
squash <commit_id2>
squash <commit_id3>
```

---

## ↩️ Αναίρεση

### Απόρριψη Αλλαγών

**Απόρριψη όλων των τοπικών αλλαγών:**
```bash
git reset --hard HEAD
```

**Αφαίρεση όλων των αρχείων από το staging:**
```bash
git reset HEAD
```

**Απόρριψη αλλαγών σε συγκεκριμένο αρχείο:**
```bash
git checkout HEAD <file>
```

### Λειτουργίες Επαναφοράς

**Επαναφορά σε προηγούμενη υποβολή (απόρριψη όλων των αλλαγών):**
```bash
git reset --hard <commit>
```

**Επαναφορά στην κατάσταση απομακρυσμένου κλάδου:**
```bash
git reset --hard <remote/branch>
# Παράδειγμα: git reset --hard upstream/master
```

**Επαναφορά διατηρώντας αλλαγές ως unstaged:**
```bash
git reset <commit>
```

**Επαναφορά διατηρώντας μη υποβληθείσες τοπικές αλλαγές:**
```bash
git reset --keep <commit>
```

### Αντιστροφή Υποβολών

**Αντιστροφή υποβολής (δημιουργία νέας υποβολής με αντίθετες αλλαγές):**
```bash
git revert <commit>
```

### Καθαρισμός Αγνοημένων Αρχείων

**Αφαίρεση αρχείων που υποβλήθηκαν κατά λάθος και πρέπει να αγνοηθούν:**
```bash
git rm -r --cached .
git add .
git commit -m "remove ignored files"
```

---

## 🌊 Git Flow

**Βελτιωμένο Git-flow:** [git-flow-avh](https://github.com/petervanderdoes/gitflow-avh)

### 📋 Πίνακας Περιεχομένων
- [🔧 Ρύθμιση](#setup-1)
- [🚀 Ξεκινώντας](#ξεκινώντας)
- [✨ Λειτουργίες](#λειτουργίες)
- [🎁 Δημιουργία Έκδοσης](#δημιουργία-έκδοσης)
- [🔥 Hotfixes](#hotfixes)
- [📊 Επισκόπηση Εντολών](#επισκόπηση-εντολών)

---

### 🔧 Ρύθμιση {#setup-1}

> **Προαπαιτούμενο:** Απαιτείται λειτουργική εγκατάσταση Git. Το Git-flow λειτουργεί σε macOS, Linux και Windows.

**macOS (Homebrew):**
```bash
brew install git-flow-avh
```

**macOS (MacPorts):**
```bash
port install git-flow
```

**Linux (βασισμένο σε Debian):**
```bash
sudo apt-get install git-flow
```

**Windows (Cygwin):**
> Απαιτεί wget και util-linux
```bash
wget -q -O - --no-check-certificate https://raw.githubusercontent.com/petervanderdoes/gitflow/develop/contrib/gitflow-installer.sh install <state> | bash
```

---

### 🚀 Ξεκινώντας

Το Git-flow χρειάζεται αρχικοποίηση για να προσαρμόσει τη ρύθμιση του έργου σας.

**Αρχικοποίηση (διαδραστική):**
```bash
git flow init
```
> Θα απαντήσετε σε ερωτήσεις σχετικά με τις συμβάσεις ονομασίας κλάδων. Συνιστώνται οι προεπιλεγμένες τιμές.

**Αρχικοποίηση (χρήση προεπιλογών):**
```bash
git flow init -d
```

---

### ✨ Λειτουργίες

Οι λειτουργίες χρησιμοποιούνται για την ανάπτυξη νέας λειτουργικότητας για επερχόμενες εκδόσεις. Συνήθως υπάρχουν μόνο σε αποθετήρια προγραμματιστών.

**Έναρξη νέας λειτουργίας:**
```bash
git flow feature start MYFEATURE
```
> Δημιουργεί κλάδο λειτουργίας βασισμένο στο 'develop' και μεταβαίνει σε αυτόν

**Ολοκλήρωση λειτουργίας:**
```bash
git flow feature finish MYFEATURE
```
> Αυτό θα:
> 1. Συγχωνεύσει το MYFEATURE στο 'develop'
> 2. Αφαιρέσει τον κλάδο λειτουργίας
> 3. Μεταβεί πίσω στο 'develop'

**Δημοσίευση λειτουργίας (για συνεργασία):**
```bash
git flow feature publish MYFEATURE
```

**Λήψη δημοσιευμένης λειτουργίας:**
```bash
git flow feature pull origin MYFEATURE
```

**Παρακολούθηση λειτουργίας origin:**
```bash
git flow feature track MYFEATURE
```

---

### 🎁 Δημιουργία Έκδοσης

Οι εκδόσεις υποστηρίζουν την προετοιμασία νέων εκδόσεων παραγωγής, επιτρέποντας μικρές διορθώσεις σφαλμάτων και προετοιμασία μεταδεδομένων.

**Έναρξη έκδοσης:**
```bash
git flow release start RELEASE [BASE]
```
> Δημιουργεί κλάδο έκδοσης από το 'develop'. Προαιρετικά καθορίστε [BASE] commit SHA-1.

**Δημοσίευση έκδοσης:**
```bash
git flow release publish RELEASE
```

**Παρακολούθηση απομακρυσμένης έκδοσης:**
```bash
git flow release track RELEASE
```

**Ολοκλήρωση έκδοσης:**
```bash
git flow release finish RELEASE
```
> Αυτό θα:
> 1. Συγχωνεύσει τον κλάδο έκδοσης στο 'master'
> 2. Προσθέσει ετικέτα στην έκδοση
> 3. Συγχωνεύσει ξανά την έκδοση στο 'develop'
> 4. Αφαιρέσει τον κλάδο έκδοσης

> 💡 **Μην ξεχάσετε:** Κάντε push τις ετικέτες σας με `git push --tags`

---

### 🔥 Hotfixes

Τα hotfixes αντιμετωπίζουν κρίσιμα ζητήματα σε ζωντανές εκδόσεις παραγωγής. Διακλαδίζονται από την αντίστοιχη ετικέτα στο master.

**Έναρξη hotfix:**
```bash
git flow hotfix start VERSION [BASENAME]
```

**Ολοκλήρωση hotfix:**
```bash
git flow hotfix finish VERSION
```
> Συγχωνεύεται πίσω τόσο στο 'develop' όσο και στο 'master', και προσθέτει ετικέτα στη συγχώνευση master

---

### 📊 Επισκόπηση Εντολών

<p align="center">
    <img alt="Git Flow Commands" src="../Img/git-flow-commands.png" height="270" width="460">
</p>

### 🌊 Σχήμα Git Flow

<p align="center">
    <img alt="Git Flow Schema" src="../Img/git-flow-commands-without-flow.png">
</p>

---


## 🌍 Άλλες Γλώσσες

Αυτός ο σύντομος οδηγός είναι διαθέσιμος σε πολλές γλώσσες:

| Γλώσσα | Σύνδεσμος |
|----------|------|
| 🇸🇦 Αραβικά | [git-cheat-sheet-ar.md](git-cheat-sheet-ar.md) |
| 🇧🇩 Μπενγκάλι | [git-cheat-sheet-bn.md](git-cheat-sheet-bn.md) |
| 🇧🇷 Βραζιλιάνικα Πορτογαλικά | [git-cheat-sheet-pt_BR.md](git-cheat-sheet-pt_BR.md) |
| 🇨🇳 Κινέζικα | [git-cheat-sheet-zh.md](git-cheat-sheet-zh.md) |
| 🇩🇪 Γερμανικά | [git-cheat-sheet-de.md](git-cheat-sheet-de.md) |
| 🇬🇷 **Ελληνικά** | [git-cheat-sheet-el.md](git-cheat-sheet-el.md) |
| 🇮🇳 Χίντι | [git-cheat-sheet-hi.md](git-cheat-sheet-hi.md) |
| 🇰🇷 Κορεάτικα | [git-cheat-sheet-ko.md](git-cheat-sheet-ko.md) |
| 🇵🇱 Πολωνικά | [git-cheat-sheet-pl.md](git-cheat-sheet-pl.md) |
| 🇪🇸 Ισπανικά | [git-cheat-sheet-es.md](git-cheat-sheet-es.md) |
| 🇹🇷 Τούρκικα | [git-cheat-sheet-tr.md](git-cheat-sheet-tr.md) |

---

## 🤝 Συνεισφορά

Καλωσορίζουμε τις συνεισφορές! Μπορείτε να:

- 🐛 Αναφέρετε σφάλματα ή τυπογραφικά λάθη
- ✨ Προσθέσετε νέες εντολές Git
- 🌍 Μεταφράσετε σε νέες γλώσσες
- 💡 Βελτιώσετε τις εξηγήσεις
- 📝 Βελτιώσετε τη μορφοποίηση

**Πώς να συνεισφέρετε:**
1. Κάντε Fork αυτό το αποθετήριο
2. Δημιουργήστε τον κλάδο λειτουργίας σας (`git checkout -b feature/AmazingFeature`)
3. Κάντε commit τις αλλαγές σας (`git commit -m 'Add some AmazingFeature'`)
4. Κάντε push στον κλάδο (`git push origin feature/AmazingFeature`)
5. Ανοίξτε ένα Pull Request

---

## 📄 Άδεια Χρήσης

Αυτό το έργο είναι ανοιχτού κώδικα και διαθέσιμο υπό την [Άδεια MIT](LICENSE).

---

<p align="center">
    <b>⭐ Βάλτε αστέρι σε αυτό το αποθετήριο αν το βρήκατε χρήσιμο!</b>
</p>
