Git and Git Flow Cheat Sheet [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)
===============
<hr>
<p align="center">
	<img alt="Git" src="../Img/git-logo.png" height="190" width="455">
</p>
<hr>


### सूची

* [सेटअप (व्यवस्था)](#सेटअप-(व्यवस्था))
* [कॉन्फ़िगरेशन फ़ाइलें](#कॉन्फ़िगरेशन-फ़ाइलें)
* [निर्माण](#निर्माण)
* [स्थानीय परिवर्तन](#स्थानीय-परिवर्तन)
* [खोज](#खोज)
* [कमिट इतिहास](#कमिट-इतिहास)
* [चाल और नाम बदलें](#चाल-औरऔर-नाम-बदलें)
* [शाखाएं और टैग](#शाखाएं-और-टैग)
* [अद्यतन और प्रकाशित करें](#अद्यतन-और-प्रकाशित-करें)
* [मर्ज और रिबेस](#मर्ज-और-रिबेस)
* [पूर्ववत](#पूर्ववत)

<hr>

## सेटअप (व्यवस्था)

##### वर्तमान कॉन्फ़िगरेशन दिखाएं:

```shell
git config --list
```

##### रिपॉजिटरी (भंडार गृह) कॉन्फ़िगरेशन दिखाएं:

```shell
git config --local --list
```

##### वैश्विक कॉन्फ़िगरेशन दिखाएं:

```shell
git config --global --list
```

##### सिस्टम कॉन्फ़िगरेशन दिखाएं:

```shell
git config --system --list
```

##### संस्करण इतिहास की समीक्षा करते समय एक नाम निर्धारित करें जो क्रेडिट के लिए पहचाने जाने योग्य हो:

```shell
git config --global user.name “[firstname lastname]”
```

##### एक ईमेल पता सेट करें जो प्रत्येक इतिहास मार्कर के साथ जुड़ा होगा:

```shell
git config --global user.email “[valid-email]”
```

##### आसान समीक्षा के लिए Git के लिए स्वचालित कमांड लाइन रंग सेट करें:

```shell
git config --global color.ui auto
```

##### प्रतिबद्ध के लिए वैश्विक संपादक सेट करें

```shell
git config --global core.editor vi
```

<hr>

## कॉन्फ़िगरेशन फ़ाइलें

##### रिपॉजिटरी (भंडार गृह) विशिष्ट कॉन्फ़िगरेशन फ़ाइल - [--local] (स्थानीय):

```shell
<repo>/.git/config
```

##### उपयोगकर्ता-विशिष्ट कॉन्फ़िगरेशन फ़ाइल - [--global] (वैश्विक):

```shell
~/.gitconfig
```

##### सिस्टम-वाइड कॉन्फ़िगरेशन फ़ाइल - [--system] (सिस्टम):

```shell
/etc/gitconfig
```

<hr>

## निर्माण

##### एक मौजूदा भंडार का क्लोन:

ये करने के दो तरीके है:

एस.एस.एच. के माध्यम से:

```shell
git clone ssh://user@domain.com/repo.git
```

एचटीटीपी के माध्यम से:

```shell
git clone http://domain.com/user/repo.git
```

##### एक नई स्थानीय रिपॉजिटरी (भंडार) बनाएं:

```shell
git init
```

##### एक विशिष्ट निर्देशिका में एक नया स्थानीय भंडार बनाएँ:

```shell
git init <directory>
```

<hr>

## स्थानीय परिवर्तन

##### कार्य फ़ोल्डर में परिवर्तन:

```shell
git status
```

##### ट्रैक फ़ाइलों में परिवर्तन:

```shell
git diff
```

##### अगले कमिट करने के लिए नई फ़ाइलों को जोड़ना:

```shell
git add .
```

##### अगले कमिट करने के लिए <फ़ाइल> में कुछ बदलाव जोड़ना:

```shell
git add -p <file>
```

##### ट्रैक फ़ाइलों में सभी परिवर्तन के लिए कमिट:

```shell
git commit -a
```

##### पिछले परिवर्तन के लिए कमिट:

```shell
git commit
```

##### संदेश के साथ कमिट:

```shell
git commit -m 'message here'
```

##### पिछले कुछ तारीख के लिए कमिट:

```shell
git commit --date="`date --date='n day ago'`" -am "Commit Message"
```

##### पिछली कमिट बदलें:

_प्रकाशित कमिट का संशोधन मत करें!_

```shell
git commit --amend
```

##### पिछली कमिट के साथ संशोधन करें लेकिन पिछली कमिट लॉग संदेश का उपयोग करें

_प्रकाशित कमिट का संशोधन मत करें!_

```shell
git commit --amend --no-edit
```

##### पिछली कमिट की कमेंटरी तारीख बदलें

```shell
GIT_COMMITTER_DATE="date" git commit --amend
```

##### पिछली कमिट के लेखक की तारीख बदलें

```shell
git commit --amend --date="date"
```

##### न किए गए कमिट परिवर्तन को वर्तमान शाखा से किसी अन्य शाखा में परिवर्तन करें: 

```shell
git stash
git checkout branch2
git stash pop
```

##### वर्तमान शाखा में वापस किए गए परिवर्तनों को पुनर्स्थापित करें:

```shell
git stash apply
```

#### वर्तमान शाखा में वापस विशेष रोक को पुनर्स्थापित करें:

- *{स्टैश_संख्या}* `git stash list` से प्राप्त किया जा सकता है

```shell
git stash apply stash@{stash_number}
```

##### अंतिम चरण (स्टैश) में परिवर्तनों को निकालें:

```shell
git stash drop
```

<hr>

## खोज

##### फ़ोल्डर में सभी फाइलों पर एक खोज:

```shell
git grep "hello"
```

##### एक खोज के किसी भी संस्करण में:

```shell
git grep "hello" v2.5
```

<hr>

## कमिट इतिहास 

##### नवीनतम के साथ शुरू, सब कमिट दिखाएँ:

```shell
git log
```

##### सब कमिट दिखाएँ (कोई लेखक जानकारी नहीं):

```shell
git log --oneline
```

##### एक विशिष्ट लेखक के सभी कमिट दिखाएँ:

```shell
git log --author="username"
```

##### एक विशिष्ट फ़ाइल के लिए समय के साथ परिवर्तन दिखाएँ:

```shell
git log -p <file>
```

##### एक फाइल में कौन क्या बदला:

```shell
git blame <file>
```

##### उन प्रदर्शनों को प्रदर्शित करें जो केवल दाईं ओर दूरस्थ / शाखा में मौजूद हैं:

```shell
git log --oneline <origin/master>..<remote/master> --left-right
```

##### संदर्भ लॉग दिखाएं:

```shell
git reflog show
```

##### संदर्भ लॉग हटाएं:

```shell
git reflog delete
```

<hr>

## चाल और नाम बदलें

##### फ़ाइल का नाम बदलें:

Index.txt को Index.html में बदलें

```shell
git mv Index.txt Index.html
```

<hr>

## शाखाएं और टैग

##### सभी स्थानीय शाखाओं की सूची:

```shell
git branch
```

##### सिर शाखा बदलने:

```shell
git checkout <branch>
```

##### नई शाखा बनाएँ और उस पर जाने:

```shell
git checkout -b <new-branch>
```

#### मौजूदा प्रतिबद्ध (कमिट) से एक नई शाखा की जाँच करें और बनाएँ:

```shell
git checkout <commit-hash> -b <new_branch_name>
```

##### अपने वर्तमान हेड (HEAD) के आधार पर एक नई शाखा बनाएँ:

```shell
git branch <new-branch>
```

##### एक रिमोट शाखा पर आधारित एक नए ट्रैकिंग शाखा बनाएँ:

```shell
git branch --track <new-branch> <remote-branch>
```

##### स्थानीय शाखा हटाना:

```shell
git branch -d <branch>
```

##### नई शाखा के नाम पर वर्तमान शाखा का नाम बदलें:

```shell
git branch -m <new_branch_name>
```

##### स्थानीय शाखा जबर्दस्ती हटाएं

_आप मर्ज ना किए गए बदलाव खो देंगे!_

```shell
git branch -D <branch>
```

##### एक टैग के साथ `HEAD` को चिह्नित करें:

```shell
git tag <tag-name>
```

##### एक टैग के साथ `HEAD` को चिह्नित करें और संदेश को शामिल करने के लिए संपादक खोलें:

```shell
git tag -a <tag-name>
```

##### एक टैग के साथ `HEAD` को चिह्नित करें और संदेश को शामिल करने के लिए संपादक खोलें:

```shell
git tag <tag-name> -am 'message here'
```

##### सभी टैग सूचीबद्ध करें:

```shell
git tag
```

##### सभी संदेशों को उनके संदेशों के साथ सूचीबद्ध करें:

```shell
git tag -n
```

<hr>

## अद्यतन और प्रकाशित करें

##### सभी वर्तमान कॉन्फ़िगर किए गए रिमोट को सूचीबद्ध करें:

```shell
git remote -v
```

##### रिमोट के बारे में जानकारी दिखाएं:

```shell
git remote show <remote>
```

##### नया दूरस्थ रिपॉजिटरी जोड़ें:

```shell
git remote add <remote> <url>
```

##### दूरस्थ रिपॉजिटरी का नाम बदलें:

```shell
git remote rename <remote> <new_remote>
```

##### एक रिमोट निकालें:

```shell
git remote rm <remote>
```

_नोट: `git remote rm` सर्वर से दूरस्थ रिपॉजिटरी को डिलीट नहीं करता है। यह केवल आपके स्थानीय रिपॉजिटरी से रिमोट और उसके संदर्भों को हटा देता है।_

##### रिमोट से सभी परिवर्तन डाउनलोड करें, लेकिन HEAD में एकीकृत न हों:

```shell
git fetch <remote>
```

##### परिवर्तन डाउनलोड करें और सीधे HEAD में विलय / एकीकृत करें:

```shell
git remote pull <remote> <url>
```

##### HEAD से स्थानीय रिपॉजिटरी में सभी परिवर्तन प्राप्त करें:

```shell
git pull origin master
```

##### मग के बिना HEAD से स्थानीय रिपॉजिटरी में सभी परिवर्तन प्राप्त करें:

```shell
git pull --rebase <remote> <branch>
```

##### दूरस्थ पर स्थानीय परिवर्तन प्रकाशित करें:

```shell
git push remote <remote> <branch>
```

##### रिमोट पर एक शाखा हटाएँ:

```shell
git push <remote> :<branch> (since Git v1.5.0)
```

या

```shell
git push <remote> --delete <branch> (since Git v1.7.0)
```

##### अपने टैग प्रकाशित करें:

```shell
git push --tags
```

<hr>

## मर्ज और रिबेस

##### एक शाखा मर्ज:

```shell
git merge <branch>
```

##### अपने वर्तमान HEAD को एक शाखा पर पुनः स्थापित करें

_प्रकाशित कमिट का संशोधन मत करें!_

```shell
git rebase <branch>
```

##### रिबेस छोड़ना:

```shell
git rebase --abort
```

##### संघर्ष को हल करने के बाद एक रिबेस जारी:

```shell
git rebase --continue
```

##### संघर्ष का समाधान करने के लिए अपने से कॉन्फ़िगर मर्ज उपकरण का उपयोग करें:

```shell
git mergetool
```

##### सुलझाया के रूप में मैन्युअल निशान फ़ाइल (हल करने के बाद) संघर्षों और हल करने के लिए अपने संपादक का उपयोग करें:

```shell
git add <resolved-file>
```

```shell
git rm <resolved-file>
```

##### कमिट को स्क्वाश करें:

```shell
git rebase -i <commit-just-before-first>
```

<hr>

## पूर्ववत

##### अपने कार्य निर्देशिका में सभी स्थानीय परिवर्तनों को छोड़ें:

```shell
git reset --hard HEAD
```

##### मचान क्षेत्र से बाहर सभी फ़ाइलों को प्राप्त (पिछले  ```git add``` पूर्ववत):

```shell
git reset HEAD
```

##### एक विशिष्ट फ़ाइल में स्थानीय परिवर्तनों को छोड़ें:

```shell
git checkout HEAD <file>
```

##### कमिट एक वापस लाएं:

```shell
git revert <commit>
```

##### अपने HEAD पॉइंटर को पिछली प्रतिबद्धताओं पर रीसेट करें और तब से सभी परिवर्तनों को छोड़ दें:

```shell
git reset --hard <commit>
```

##### अपने HEAD पॉइंटर को पिछली प्रतिबद्धताओं पर रीसेट करें और सभी परिवर्तनों को बिना किसी बदलाव के संरक्षित करें:

```shell
git reset <commit>
```

##### अपने HEAD पॉइंटर को पिछली कमिट में रीसेट करें और अनचाहे स्थानीय परिवर्तनों को संरक्षित करें:

```shell
git reset --keep <commit>
```

##### अपने HEAD पॉइंटर को किसी दूरस्थ शाखा वर्तमान स्थिति पर रीसेट करें:

```shell
git reset --hard <remote/branch> e.g., upstream/master, origin/my-feature
```

##### उन फ़ाइलों को हटा दें जो गलती से .gitignore मैं पहले ही जोड़ दिए गए थे:

```shell
git rm -r --cached .
git add .
git commit -m "remove xyz file"
```

<hr>
