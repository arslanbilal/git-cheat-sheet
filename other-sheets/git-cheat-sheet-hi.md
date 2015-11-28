Git Cheat Sheet Hindi [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)
===============

###सूची
* [निर्माण](#निर्माण)
* [स्थानीय परिवर्तन](#स्थानीय-परिवर्तन)
* [खोज](#खोज)
* [कमेट इतिहास](#कमेट-इतिहास)
* [शाखाएं और टैग](#शाखाएं-और-टैग)

<hr>
##निर्माण

#####एक मौजूदा भंडार का क्लोन:
```
$ git clone ssh://user@domain.com/repo.git
```

#####एक नए स्थानीय भंडार बनाएं :
```
$ git init
```
<hr>

##स्थानीय परिवर्तन

#####कार्य फ़ोल्डर में परिवर्तन:
```
$ git status
```

#####ट्रैक फ़ाइलों में परिवर्तन:
```
$ git diff
```

#####अगले कमेट करने के लिए नई फ़ाइलों को जोड़ना:
```
$ git add
```

#####अगले कमेट करने के लिए <फ़ाइल> में कुछ बदलाव जोड़ना:
```
$ git add -p <file>
```

#####ट्रैक फ़ाइलों में सभी परिवर्तन के लिए कमेट:
```
$ git commit -a
```

#####पिछले परिवर्तन के लिए कमेट:
```
$ git commit
```

#####संदेश के साथ कमेट:
```
$ git commit -m 'message here'
```

#####पिछले कुछ तारीख के लिए कमेट:
```
git commit --date="`date --date='n day ago'`" -am "Commit Message"
```

#####पिछले कमेट बदलें:<br>
######प्रकाशित कमेट का संशोधन मत करो!
```
$ git commit --amend
```

#####शाखा में वर्तमान अन्य शाखा में ले जाएँ:
```
git stash
git checkout branch2
git stash pop
```

<hr>
##खोज

#####फ़ोल्डर में सभी फाइलों पर एक खोज:
```
$ git grep "hello"
```

#####एक खोज के किसी भी संस्करण में:
```
$ git grep "hello" v2.5
```

<hr>
##कमेट इतिहास 

#####नवीनतम के साथ शुरू, सब कमेट दिखाएँ:
```
$ git log
```

#####सब कमेट दिखाएँ (कोई लेखक जानकारी नहीं):
```
$ git log --oneline
```

#####एक विशिष्ट लेखक के सभी कमेट दिखाएँ:
```
$ git log --author="username"
```

#####एक विशिष्ट फ़ाइल के लिए समय के साथ परिवर्तन दिखाएँ:
```
$ git log -p <file>
```

#####एक फाइल में कौन क्या बदला:
```
$ git blame <file>
```

<hr>

##शाखाएं और टैग

#####सभी स्थानीय शाखाओं की सूची:
```
$ git branch
```

#####सिर शाखा बदलने:
```
$ git checkout <branch>
```

#####नई शाखा बनाएँ और उस पर जाने:
```
$ git branch <new-branch>
```

#####:
```
$ git branch --track <new-branch> <remote-branch>
```

#####Yerel branchi siler:
```
$ git branch -d <branch>
```

#####Güncel commiti etiket ile işaretler:
```
$ git tag <tag-name>
```

<hr>

