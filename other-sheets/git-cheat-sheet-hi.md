# Git और Git Flow चीट शीट
[![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

<p align="center">
    <img alt="Git" src="../Img/git-logo.png" height="190" width="455">
</p>

---

## 📖 परिचय

यह व्यापक Git चीट शीट आपको बिना सब कुछ याद किए Git कमांड में महारत हासिल करने में मदद करती है। चाहे आप शुरुआती हों या अनुभवी डेवलपर, यह गाइड आवश्यक Git ऑपरेशन के लिए त्वरित संदर्भ प्रदान करती है।

**योगदान का स्वागत है!** आप कर सकते हैं:
- व्याकरण की गलतियाँ ठीक करें
- नए कमांड जोड़ें
- अपनी भाषा में अनुवाद करें
- व्याख्याओं को बेहतर बनाएं

---
## 📋 विषय सूची

- [🔧 सेटअप](#-सेटअप)
- [⚙️ कॉन्फ़िगरेशन फ़ाइलें](#️-कॉन्फ़िगरेशन-फ़ाइलें)
- [🆕 रिपॉजिटरी बनाएं](#-रिपॉजिटरी-बनाएं)
- [📝 स्थानीय परिवर्तन](#-स्थानीय-परिवर्तन)
- [🔍 खोज](#-खोज)
- [📖 कमिट इतिहास](#-कमिट-इतिहास)
- [📁 स्थानांतरित / नाम बदलें](#-स्थानांतरित--नाम-बदलें)
- [🌿 ब्रांच और टैग](#-ब्रांच-और-टैग)
- [🔄 अपडेट और प्रकाशित करें](#-अपडेट-और-प्रकाशित-करें)
- [🔀 मर्ज और रीबेस](#-मर्ज-और-रीबेस)
- [↩️ पूर्ववत करें](#️-पूर्ववत-करें)
- [🌊 Git Flow](#-git-flow)
- [🌍 अन्य भाषाएं](#-अन्य-भाषाएं)

---

## 🔧 सेटअप

### कॉन्फ़िगरेशन देखें

**वर्तमान कॉन्फ़िगरेशन दिखाएं:**
```bash
git config --list
```

**रिपॉजिटरी कॉन्फ़िगरेशन दिखाएं:**
```bash
git config --local --list
```

**ग्लोबल कॉन्फ़िगरेशन दिखाएं:**
```bash
git config --global --list
```

**सिस्टम कॉन्फ़िगरेशन दिखाएं:**
```bash
git config --system --list
```

### उपयोगकर्ता कॉन्फ़िगरेशन

**संस्करण इतिहास के लिए अपना नाम सेट करें:**
```bash
git config --global user.name "[firstname lastname]"
```

**अपना ईमेल पता सेट करें:**
```bash
git config --global user.email "[valid-email]"
```

### प्रदर्शन और एडिटर सेटिंग्स

**स्वचालित कमांड लाइन रंग सक्षम करें:**
```bash
git config --global color.ui auto
```

**कमिट के लिए ग्लोबल एडिटर सेट करें:**
```bash
git config --global core.editor vi
```

---

## ⚙️ कॉन्फ़िगरेशन फ़ाइलें

| स्कोप | स्थान | कमांड फ्लैग |
|-------|--------|-------------|
| **रिपॉजिटरी** | `<repo>/.git/config` | `--local` |
| **उपयोगकर्ता** | `~/.gitconfig` | `--global` |
| **सिस्टम** | `/etc/gitconfig` | `--system` |

---

## 🆕 रिपॉजिटरी बनाएं

### मौजूदा रिपॉजिटरी क्लोन करें

**SSH के माध्यम से:**
```bash
git clone ssh://user@domain.com/repo.git
```

**HTTPS के माध्यम से:**
```bash
git clone https://domain.com/user/repo.git
```

### नई रिपॉजिटरी बनाएं

**वर्तमान डायरेक्टरी में रिपॉजिटरी बनाएं:**
```bash
git init
```

**विशिष्ट डायरेक्टरी में रिपॉजिटरी बनाएं:**
```bash
git init <directory>
```

---

## 📝 स्थानीय परिवर्तन

### स्थिति और अंतर जांचें

**वर्किंग डायरेक्टरी की स्थिति देखें:**
```bash
git status
```

**ट्रैक की गई फ़ाइलों में परिवर्तन दिखाएं:**
```bash
git diff
```

**विशिष्ट फ़ाइल में परिवर्तन दिखाएं:**
```bash
git diff <file>
```

### परिवर्तन स्टेज करें

**सभी वर्तमान परिवर्तन जोड़ें:**
```bash
git add .
```

**विशिष्ट फ़ाइलें जोड़ें:**
```bash
git add <filename1> <filename2>
```

**फ़ाइल के कुछ हिस्सों को इंटरैक्टिव रूप से जोड़ें:**
```bash
git add -p <file>
```

### परिवर्तन कमिट करें

**सभी ट्रैक की गई फ़ाइल परिवर्तन कमिट करें:**
```bash
git commit -a
```

**स्टेज किए गए परिवर्तन कमिट करें:**
```bash
git commit
```

**संदेश के साथ कमिट करें:**
```bash
git commit -m 'message here'
```

**स्टेजिंग छोड़कर संदेश के साथ कमिट करें:**
```bash
git commit -am 'message here'
```

**विशिष्ट तारीख के साथ कमिट करें:**
```bash
git commit --date="`date --date='n day ago'`" -am "<Commit Message Here>"
```

### अंतिम कमिट संशोधित करें

> ⚠️ **चेतावनी:** प्रकाशित कमिट को संशोधित न करें!

**अंतिम कमिट संशोधित करें:**
```bash
git commit -a --amend
```

**कमिट संदेश बदले बिना संशोधित करें:**
```bash
git commit --amend --no-edit
```

**कमिटर की तारीख बदलें:**
```bash
GIT_COMMITTER_DATE="date" git commit --amend
```

**लेखक की तारीख बदलें:**
```bash
git commit --amend --date="date"
```

### परिवर्तन स्टैश करें

**वर्तमान परिवर्तन अस्थायी रूप से सहेजें:**
```bash
git stash
```

**अंतिम स्टैश किए गए परिवर्तन लागू करें:**
```bash
git stash apply
```

**विशिष्ट स्टैश लागू करें:**
```bash
git stash apply stash@{stash_number}
```
> उपलब्ध स्टैश देखने के लिए `git stash list` का उपयोग करें

**अंतिम स्टैश हटाएं:**
```bash
git stash drop
```

**अन-कमिटेड परिवर्तनों को दूसरी ब्रांच में ले जाएं:**
```bash
git stash
git checkout branch2
git stash pop
```

---

## 🔍 खोज

### टेक्स्ट खोज

**सभी फ़ाइलों में टेक्स्ट खोजें:**
```bash
git grep "Hello"
```

**विशिष्ट संस्करण में खोजें:**
```bash
git grep "Hello" v2.5
```

### कमिट खोज

**विशिष्ट कीवर्ड जोड़ने वाले कमिट खोजें:**
```bash
git log -S 'keyword'
```

**रेगुलर एक्सप्रेशन के साथ खोजें:**
```bash
git log -S 'keyword' --pickaxe-regex
```

---

## 📖 कमिट इतिहास

### बुनियादी इतिहास

**सभी कमिट दिखाएं (विस्तृत):**
```bash
git log
```

**कमिट दिखाएं (प्रति कमिट एक लाइन):**
```bash
git log --oneline
```

**विशिष्ट लेखक के कमिट दिखाएं:**
```bash
git log --author="username"
```

**विशिष्ट फ़ाइल के परिवर्तन दिखाएं:**
```bash
git log -p <file>
```

### उन्नत इतिहास

**ब्रांच की तुलना करें:**
```bash
git log --oneline <origin/master>..<remote/master> --left-right
```

**किसने क्या और कब बदला दिखाएं:**
```bash
git blame <file>
```

### संदर्भ लॉग

**संदर्भ लॉग दिखाएं:**
```bash
git reflog show
```

**संदर्भ लॉग हटाएं:**
```bash
git reflog delete
```

---

## 📁 स्थानांतरित / नाम बदलें

**फ़ाइल का नाम बदलें:**
```bash
git mv Index.txt Index.html
```

---

## 🌿 ब्रांच और टैग

### ब्रांच सूची

**स्थानीय ब्रांच दिखाएं:**
```bash
git branch
```

**सभी ब्रांच दिखाएं (स्थानीय + रिमोट):**
```bash
git branch -a
```

**रिमोट ब्रांच दिखाएं:**
```bash
git branch -r
```

**मर्ज की गई ब्रांच दिखाएं:**
```bash
git branch --merged
```

### ब्रांच स्विच और बनाएं

**मौजूदा ब्रांच पर स्विच करें:**
```bash
git checkout <branch>
```

**नई ब्रांच बनाएं और स्विच करें:**
```bash
git checkout -b <branch>
```

**पिछली ब्रांच पर स्विच करें:**
```bash
git checkout -
```

**मौजूदा ब्रांच से नई ब्रांच बनाएं:**
```bash
git checkout -b <new_branch> <existing_branch>
```

**विशिष्ट कमिट से ब्रांच बनाएं:**
```bash
git checkout <commit-hash> -b <new_branch_name>
```

**बिना स्विच किए ब्रांच बनाएं:**
```bash
git branch <new-branch>
```

**ट्रैकिंग ब्रांच बनाएं:**
```bash
git branch --track <new-branch> <remote-branch>
```

### ब्रांच ऑपरेशन

**दूसरी ब्रांच से एक फ़ाइल चेकआउट करें:**
```bash
git checkout <branch> -- <filename>
```

**दूसरी ब्रांच से विशिष्ट कमिट लागू करें:**
```bash
git cherry-pick <commit hash>
```

**वर्तमान ब्रांच का नाम बदलें:**
```bash
git branch -m <new_branch_name>
```

**स्थानीय ब्रांच हटाएं:**
```bash
git branch -d <branch>
```

**जबरदस्ती स्थानीय ब्रांच हटाएं:**
```bash
git branch -D <branch>
```
> ⚠️ **चेतावनी:** आप अन-मर्ज किए गए परिवर्तन खो देंगे!

### टैग

**HEAD पर टैग बनाएं:**
```bash
git tag <tag-name>
```

**एनोटेटेड टैग बनाएं:**
```bash
git tag -a <tag-name>
```

**संदेश के साथ टैग बनाएं:**
```bash
git tag <tag-name> -am 'message here'
```

**सभी टैग दिखाएं:**
```bash
git tag
```

**संदेश के साथ टैग दिखाएं:**
```bash
git tag -n
```

---

## 🔄 अपडेट और प्रकाशित करें

### रिमोट प्रबंधन

**कॉन्फ़िगर किए गए रिमोट दिखाएं:**
```bash
git remote -v
```

**रिमोट की जानकारी दिखाएं:**
```bash
git remote show <remote>
```

**नया रिमोट जोड़ें:**
```bash
git remote add <remote> <url>
```

**रिमोट का नाम बदलें:**
```bash
git remote rename <remote> <new_remote>
```

**रिमोट हटाएं:**
```bash
git remote rm <remote>
```
> ℹ️ **नोट:** यह केवल स्थानीय रूप से रिमोट संदर्भ हटाता है, रिमोट रिपॉजिटरी स्वयं नहीं।

### फ़ेच और पुल

**बिना मर्ज किए परिवर्तन डाउनलोड करें:**
```bash
git fetch <remote>
```

**परिवर्तन डाउनलोड और मर्ज करें:**
```bash
git pull <remote> <branch>
```

**मुख्य ब्रांच से परिवर्तन प्राप्त करें:**
```bash
git pull origin master
```

**रीबेस के साथ पुल करें:**
```bash
git pull --rebase <remote> <branch>
```

### पुश और प्रकाशित करें

**स्थानीय परिवर्तन प्रकाशित करें:**
```bash
git push <remote> <branch>
```

**रिमोट ब्रांच हटाएं:**
```bash
# Git v1.7.0+
git push <remote> --delete <branch>

# Git v1.5.0+
git push <remote> :<branch>
```

**टैग प्रकाशित करें:**
```bash
git push --tags
```

---

## 🔀 मर्ज और रीबेस

### मर्ज ऑपरेशन

**ब्रांच को वर्तमान HEAD में मर्ज करें:**
```bash
git merge <branch>
```

**ग्लोबल मर्ज टूल कॉन्फ़िगर करें:**
```bash
git config --global merge.tool meld
```

**कॉन्फ़िगर किया गया मर्ज टूल उपयोग करें:**
```bash
git mergetool
```

### रीबेस ऑपरेशन

> ⚠️ **चेतावनी:** प्रकाशित कमिट को रीबेस न करें!

**वर्तमान HEAD को ब्रांच पर रीबेस करें:**
```bash
git rebase <branch>
```

**रीबेस रद्द करें:**
```bash
git rebase --abort
```

**कॉन्फ्लिक्ट हल करने के बाद रीबेस जारी रखें:**
```bash
git rebase --continue
```

### कॉन्फ्लिक्ट समाधान

**फ़ाइल को हल के रूप में चिह्नित करें:**
```bash
git add <resolved-file>
```

**हल की गई फ़ाइल हटाएं:**
```bash
git rm <resolved-file>
```

### कमिट स्क्वॉश करें

**स्क्वॉश के लिए इंटरैक्टिव रीबेस:**
```bash
git rebase -i <commit-just-before-first>
```

**स्क्वॉश कॉन्फ़िगरेशन का उदाहरण:**
```
# पहले
pick <commit_id>
pick <commit_id2>
pick <commit_id3>

# बाद में (commit_id2 और commit_id3 को commit_id में स्क्वॉश करें)
pick <commit_id>
squash <commit_id2>
squash <commit_id3>
```

---

## ↩️ पूर्ववत करें

### परिवर्तन रद्द करें

**सभी स्थानीय परिवर्तन रद्द करें:**
```bash
git reset --hard HEAD
```

**सभी फ़ाइलें अनस्टेज करें:**
```bash
git reset HEAD
```

**विशिष्ट फ़ाइल में परिवर्तन रद्द करें:**
```bash
git checkout HEAD <file>
```

### रीसेट ऑपरेशन

**पिछले कमिट पर रीसेट करें (सभी परिवर्तन रद्द करें):**
```bash
git reset --hard <commit>
```

**रिमोट ब्रांच स्थिति पर रीसेट करें:**
```bash
git reset --hard <remote/branch>
# उदाहरण: git reset --hard upstream/master
```

**परिवर्तनों को अनस्टेज्ड रखते हुए रीसेट करें:**
```bash
git reset <commit>
```

**अन-कमिटेड स्थानीय परिवर्तनों को सुरक्षित रखते हुए रीसेट करें:**
```bash
git reset --keep <commit>
```

### कमिट रिवर्ट करें

**कमिट रिवर्ट करें (विपरीत परिवर्तनों के साथ नया कमिट बनाएं):**
```bash
git revert <commit>
```

### अनदेखी फ़ाइलें साफ़ करें

**गलती से कमिट की गई फ़ाइलें हटाएं जिन्हें अनदेखा किया जाना चाहिए:**
```bash
git rm -r --cached .
git add .
git commit -m "remove ignored files"
```

---

## 🌊 Git Flow

**बेहतर Git-flow:** [git-flow-avh](https://github.com/petervanderdoes/gitflow-avh)

### 📋 विषय सूची
- [🔧 सेटअप](#setup-1)
- [🚀 शुरुआत करें](#getting-started)
- [✨ फीचर](#features)
- [🎁 रिलीज बनाएं](#make-a-release)
- [🔥 हॉटफिक्स](#hotfixes)
- [📊 कमांड अवलोकन](#commands-overview)

---

### 🔧 सेटअप {#setup-1}

> **पूर्वापेक्षा:** कार्यशील Git इंस्टॉलेशन आवश्यक है। Git-flow macOS, Linux और Windows पर काम करता है।

**macOS (Homebrew):**
```bash
brew install git-flow-avh
```

**macOS (MacPorts):**
```bash
port install git-flow
```

**Linux (Debian-आधारित):**
```bash
sudo apt-get install git-flow
```

**Windows (Cygwin):**
> wget और util-linux आवश्यक है
```bash
wget -q -O - --no-check-certificate https://raw.githubusercontent.com/petervanderdoes/gitflow/develop/contrib/gitflow-installer.sh install <state> | bash
```

---

### 🚀 शुरुआत करें

Git-flow को आपकी प्रोजेक्ट सेटअप को अनुकूलित करने के लिए इनिशियलाइज़ेशन की आवश्यकता है।

**इनिशियलाइज़ करें (इंटरैक्टिव):**
```bash
git flow init
```
> आपसे ब्रांच नामकरण परंपराओं के बारे में प्रश्न पूछे जाएंगे। डिफ़ॉल्ट मान अनुशंसित हैं।

**इनिशियलाइज़ करें (डिफ़ॉल्ट उपयोग करें):**
```bash
git flow init -d
```

---

### ✨ फीचर

फीचर आगामी रिलीज़ के लिए नई कार्यक्षमता विकसित करने के लिए हैं। वे आमतौर पर केवल डेवलपर रिपॉजिटरी में मौजूद होते हैं।

**नया फीचर शुरू करें:**
```bash
git flow feature start MYFEATURE
```
> 'develop' के आधार पर फीचर ब्रांच बनाता है और उस पर स्विच करता है

**फीचर समाप्त करें:**
```bash
git flow feature finish MYFEATURE
```
> यह करेगा:
> 1. MYFEATURE को 'develop' में मर्ज करेगा
> 2. फीचर ब्रांच हटाएगा
> 3. 'develop' पर वापस स्विच करेगा

**फीचर प्रकाशित करें (सहयोग के लिए):**
```bash
git flow feature publish MYFEATURE
```

**प्रकाशित फीचर प्राप्त करें:**
```bash
git flow feature pull origin MYFEATURE
```

**ऑरिजिन फीचर ट्रैक करें:**
```bash
git flow feature track MYFEATURE
```

---

### 🎁 रिलीज बनाएं

रिलीज़ नए प्रोडक्शन रिलीज़ की तैयारी का समर्थन करती हैं, जिसमें छोटे बग फिक्स और मेटा-डेटा की तैयारी शामिल है।

**रिलीज शुरू करें:**
```bash
git flow release start RELEASE [BASE]
```
> 'develop' से रिलीज ब्रांच बनाता है। वैकल्पिक रूप से [BASE] कमिट SHA-1 निर्दिष्ट करें।

**रिलीज प्रकाशित करें:**
```bash
git flow release publish RELEASE
```

**रिमोट रिलीज ट्रैक करें:**
```bash
git flow release track RELEASE
```

**रिलीज समाप्त करें:**
```bash
git flow release finish RELEASE
```
> यह करेगा:
> 1. रिलीज ब्रांच को 'master' में मर्ज करेगा
> 2. रिलीज को टैग करेगा
> 3. रिलीज को 'develop' में बैक-मर्ज करेगा
> 4. रिलीज ब्रांच हटाएगा

> 💡 **न भूलें:** अपने टैग `git push --tags` से पुश करें

---

### 🔥 हॉटफिक्स

हॉटफिक्स लाइव प्रोडक्शन संस्करणों में गंभीर समस्याओं को संबोधित करते हैं। वे master पर संबंधित टैग से ब्रांच बनाते हैं।

**हॉटफिक्स शुरू करें:**
```bash
git flow hotfix start VERSION [BASENAME]
```

**हॉटफिक्स समाप्त करें:**
```bash
git flow hotfix finish VERSION
```
> 'develop' और 'master' दोनों में वापस मर्ज करता है, और master मर्ज को टैग करता है

---

### 📊 कमांड अवलोकन

<p align="center">
    <img alt="Git Flow Commands" src="../Img/git-flow-commands.png" height="270" width="460">
</p>

### �� Git Flow स्कीमा

<p align="center">
    <img alt="Git Flow Schema" src="../Img/git-flow-commands-without-flow.png">
</p>

---


## 🌍 अन्य भाषाएं

यह चीट शीट कई भाषाओं में उपलब्ध है:

| भाषा | लिंक |
|------|------|
| 🇸🇦 अरबी | [git-cheat-sheet-ar.md](git-cheat-sheet-ar.md) |
| 🇧🇩 बंगाली | [git-cheat-sheet-bn.md](git-cheat-sheet-bn.md) |
| 🇧🇷 ब्राज़ीलियाई पुर्तगाली | [git-cheat-sheet-pt_BR.md](git-cheat-sheet-pt_BR.md) |
| 🇨🇳 चीनी | [git-cheat-sheet-zh.md](git-cheat-sheet-zh.md) |
| 🇩🇪 जर्मन | [git-cheat-sheet-de.md](git-cheat-sheet-de.md) |
| 🇬🇷 ग्रीक | [git-cheat-sheet-el.md](git-cheat-sheet-el.md) |
| 🇮🇳 **हिन्दी** | **(वर्तमान)** |
| 🇰🇷 कोरियाई | [git-cheat-sheet-ko.md](git-cheat-sheet-ko.md) |
| 🇵🇱 पोलिश | [git-cheat-sheet-pl.md](git-cheat-sheet-pl.md) |
| 🇪🇸 स्पेनिश | [git-cheat-sheet-es.md](git-cheat-sheet-es.md) |
| 🇹🇷 तुर्की | [git-cheat-sheet-tr.md](git-cheat-sheet-tr.md) |

---

## 🤝 योगदान

हम योगदान का स्वागत करते हैं! आप कर सकते हैं:

- 🐛 बग या टाइपो रिपोर्ट करें
- ✨ नए Git कमांड जोड़ें
- 🌍 नई भाषाओं में अनुवाद करें
- 💡 व्याख्याओं को बेहतर बनाएं
- 📝 फ़ॉर्मेटिंग में सुधार करें

**योगदान कैसे करें:**
1. इस रिपॉजिटरी को फ़ॉर्क करें
2. अपनी फीचर ब्रांच बनाएं (`git checkout -b feature/AmazingFeature`)
3. अपने परिवर्तन कमिट करें (`git commit -m 'Add some AmazingFeature'`)
4. ब्रांच पर पुश करें (`git push origin feature/AmazingFeature`)
5. Pull Request खोलें

---

## 📄 लाइसेंस

यह प्रोजेक्ट ओपन सोर्स है और [MIT लाइसेंस](../LICENSE) के तहत उपलब्ध है।

---

<p align="center">
    <b>⭐ अगर आपको यह रिपॉजिटरी उपयोगी लगी तो इसे स्टार करें!</b>
</p>
