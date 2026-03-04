# الدليل المرجعي لـ Git و Git Flow
[![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

<p align="center">
    <img alt="Git" src="../Img/git-logo.png" height="190" width="455">
</p>

---

## 📖 حول هذا الدليل

هذا الدليل المرجعي الشامل لـ Git يساعدك على إتقان أوامر Git دون الحاجة لحفظ كل شيء. سواء كنت مبتدئاً أو مطوراً ذا خبرة، يوفر هذا الدليل مرجعاً سريعاً لعمليات Git الأساسية.

**نرحب بالمساهمات!** لا تتردد في:
- إصلاح الأخطاء الإملائية
- إضافة أوامر جديدة
- الترجمة إلى لغتك
- تحسين الشروحات

---
## 📋 جدول المحتويات

- [🔧 الإعداد](#-الإعداد)
- [⚙️ ملفات الإعداد](#️-ملفات-الإعداد)
- [🆕 إنشاء مستودع](#-إنشاء-مستودع)
- [📝 التغييرات المحلية](#-التغييرات-المحلية)
- [🔍 البحث](#-البحث)
- [📖 سجل الإيداعات](#-سجل-الإيداعات)
- [📁 النقل / إعادة التسمية](#-النقل--إعادة-التسمية)
- [🌿 الفروع والعلامات](#-الفروع-والعلامات)
- [🔄 التحديث والنشر](#-التحديث-والنشر)
- [🔀 الدمج وإعادة التأسيس](#-الدمج-وإعادة-التأسيس)
- [↩️ التراجع](#️-التراجع)
- [🌊 Git Flow](#-git-flow)
- [�� لغات أخرى](#-لغات-أخرى)

---

## 🔧 الإعداد

### عرض الإعدادات

**عرض الإعدادات الحالية:**
```bash
git config --list
```

**عرض إعدادات المستودع:**
```bash
git config --local --list
```

**عرض الإعدادات العامة:**
```bash
git config --global --list
```

**عرض إعدادات النظام:**
```bash
git config --system --list
```

### إعداد المستخدم

**تعيين اسمك لسجل الإصدارات:**
```bash
git config --global user.name "[firstname lastname]"
```

**تعيين بريدك الإلكتروني:**
```bash
git config --global user.email "[valid-email]"
```

### إعدادات العرض والمحرر

**تفعيل التلوين التلقائي لسطر الأوامر:**
```bash
git config --global color.ui auto
```

**تعيين المحرر العام للإيداعات:**
```bash
git config --global core.editor vi
```

---

## ⚙️ ملفات الإعداد

| النطاق | الموقع | خيار الأمر |
|--------|--------|------------|
| **المستودع** | `<repo>/.git/config` | `--local` |
| **المستخدم** | `~/.gitconfig` | `--global` |
| **النظام** | `/etc/gitconfig` | `--system` |

---

## 🆕 إنشاء مستودع

### استنساخ مستودع موجود

**عبر SSH:**
```bash
git clone ssh://user@domain.com/repo.git
```

**عبر HTTPS:**
```bash
git clone https://domain.com/user/repo.git
```

### تهيئة مستودع جديد

**إنشاء مستودع في المجلد الحالي:**
```bash
git init
```

**إنشاء مستودع في مجلد محدد:**
```bash
git init <directory>
```

---

## 📝 التغييرات المحلية

### فحص الحالة والاختلافات

**عرض حالة مجلد العمل:**
```bash
git status
```

**عرض التغييرات في الملفات المتتبعة:**
```bash
git diff
```

**عرض التغييرات في ملف محدد:**
```bash
git diff <file>
```

### تحضير التغييرات

**إضافة جميع التغييرات الحالية:**
```bash
git add .
```

**إضافة ملفات محددة:**
```bash
git add <filename1> <filename2>
```

**إضافة أجزاء من ملف بشكل تفاعلي:**
```bash
git add -p <file>
```

### إيداع التغييرات

**إيداع جميع تغييرات الملفات المتتبعة:**
```bash
git commit -a
```

**إيداع التغييرات المحضّرة:**
```bash
git commit
```

**إيداع مع رسالة:**
```bash
git commit -m 'message here'
```

**تخطي التحضير والإيداع مع رسالة:**
```bash
git commit -am 'message here'
```

**إيداع بتاريخ محدد:**
```bash
git commit --date="`date --date='n day ago'`" -am "<Commit Message Here>"
```

### تعديل آخر إيداع

> ⚠️ **تحذير:** لا تعدّل الإيداعات المنشورة!

**تعديل آخر إيداع:**
```bash
git commit -a --amend
```

**تعديل بدون تغيير رسالة الإيداع:**
```bash
git commit --amend --no-edit
```

**تغيير تاريخ المودع:**
```bash
GIT_COMMITTER_DATE="date" git commit --amend
```

**تغيير تاريخ المؤلف:**
```bash
git commit --amend --date="date"
```

### تخزين التغييرات مؤقتاً

**حفظ التغييرات الحالية مؤقتاً:**
```bash
git stash
```

**تطبيق آخر تغييرات مخزنة:**
```bash
git stash apply
```

**تطبيق تخزين محدد:**
```bash
git stash apply stash@{stash_number}
```
> استخدم `git stash list` لعرض التخزينات المتاحة

**حذف آخر تخزين:**
```bash
git stash drop
```

**نقل التغييرات غير المودعة إلى فرع آخر:**
```bash
git stash
git checkout branch2
git stash pop
```

---

## 🔍 البحث

### البحث في النصوص

**البحث عن نص في جميع الملفات:**
```bash
git grep "Hello"
```

**البحث في إصدار محدد:**
```bash
git grep "Hello" v2.5
```

### البحث في الإيداعات

**البحث عن إيداعات أضافت كلمة مفتاحية محددة:**
```bash
git log -S 'keyword'
```

**البحث بتعبير نمطي:**
```bash
git log -S 'keyword' --pickaxe-regex
```

---

## 📖 سجل الإيداعات

### السجل الأساسي

**عرض جميع الإيداعات (مفصل):**
```bash
git log
```

**عرض الإيداعات (سطر واحد لكل إيداع):**
```bash
git log --oneline
```

**عرض إيداعات مؤلف محدد:**
```bash
git log --author="username"
```

**عرض التغييرات لملف محدد:**
```bash
git log -p <file>
```

### السجل المتقدم

**مقارنة الفروع:**
```bash
git log --oneline <origin/master>..<remote/master> --left-right
```

**عرض من غيّر ماذا ومتى:**
```bash
git blame <file>
```

### سجلات المراجع

**عرض سجل المراجع:**
```bash
git reflog show
```

**حذف سجل المراجع:**
```bash
git reflog delete
```

---

## 📁 النقل / إعادة التسمية

**إعادة تسمية ملف:**
```bash
git mv Index.txt Index.html
```

---

## 🌿 الفروع والعلامات

### عرض الفروع

**عرض الفروع المحلية:**
```bash
git branch
```

**عرض جميع الفروع (محلية + بعيدة):**
```bash
git branch -a
```

**عرض الفروع البعيدة:**
```bash
git branch -r
```

**عرض الفروع المدمجة:**
```bash
git branch --merged
```

### التبديل وإنشاء الفروع

**التبديل إلى فرع موجود:**
```bash
git checkout <branch>
```

**إنشاء والتبديل إلى فرع جديد:**
```bash
git checkout -b <branch>
```

**التبديل إلى الفرع السابق:**
```bash
git checkout -
```

**إنشاء فرع من فرع موجود:**
```bash
git checkout -b <new_branch> <existing_branch>
```

**إنشاء فرع من إيداع محدد:**
```bash
git checkout <commit-hash> -b <new_branch_name>
```

**إنشاء فرع بدون التبديل إليه:**
```bash
git branch <new-branch>
```

**إنشاء فرع تتبع:**
```bash
git branch --track <new-branch> <remote-branch>
```

### عمليات الفروع

**استخراج ملف واحد من فرع آخر:**
```bash
git checkout <branch> -- <filename>
```

**تطبيق إيداع محدد من فرع آخر:**
```bash
git cherry-pick <commit hash>
```

**إعادة تسمية الفرع الحالي:**
```bash
git branch -m <new_branch_name>
```

**حذف فرع محلي:**
```bash
git branch -d <branch>
```

**حذف فرع محلي بالقوة:**
```bash
git branch -D <branch>
```
> ⚠️ **تحذير:** ستفقد التغييرات غير المدمجة!

### العلامات

**إنشاء علامة عند HEAD:**
```bash
git tag <tag-name>
```

**إنشاء علامة مشروحة:**
```bash
git tag -a <tag-name>
```

**إنشاء علامة مع رسالة:**
```bash
git tag <tag-name> -am 'message here'
```

**عرض جميع العلامات:**
```bash
git tag
```

**عرض العلامات مع الرسائل:**
```bash
git tag -n
```

---

## 🔄 التحديث والنشر

### إدارة المستودعات البعيدة

**عرض المستودعات البعيدة المُعدّة:**
```bash
git remote -v
```

**عرض معلومات المستودع البعيد:**
```bash
git remote show <remote>
```

**إضافة مستودع بعيد جديد:**
```bash
git remote add <remote> <url>
```

**إعادة تسمية مستودع بعيد:**
```bash
git remote rename <remote> <new_remote>
```

**حذف مستودع بعيد:**
```bash
git remote rm <remote>
```
> ℹ️ **ملاحظة:** هذا يحذف المرجع البعيد محلياً فقط، وليس المستودع البعيد نفسه.

### الجلب والسحب

**تنزيل التغييرات بدون دمج:**
```bash
git fetch <remote>
```

**تنزيل ودمج التغييرات:**
```bash
git pull <remote> <branch>
```

**الحصول على التغييرات من الفرع الرئيسي:**
```bash
git pull origin master
```

**السحب مع إعادة التأسيس:**
```bash
git pull --rebase <remote> <branch>
```

### الدفع والنشر

**نشر التغييرات المحلية:**
```bash
git push <remote> <branch>
```

**حذف فرع بعيد:**
```bash
# Git v1.7.0+
git push <remote> --delete <branch>

# Git v1.5.0+
git push <remote> :<branch>
```

**نشر العلامات:**
```bash
git push --tags
```

---

## 🔀 الدمج وإعادة التأسيس

### عمليات الدمج

**دمج فرع في HEAD الحالي:**
```bash
git merge <branch>
```

**إعداد أداة الدمج عامة:**
```bash
git config --global merge.tool meld
```

**استخدام أداة الدمج المُعدّة:**
```bash
git mergetool
```

### عمليات إعادة التأسيس

> ⚠️ **تحذير:** لا تعد تأسيس الإيداعات المنشورة!

**إعادة تأسيس HEAD الحالي على فرع:**
```bash
git rebase <branch>
```

**إلغاء إعادة التأسيس:**
```bash
git rebase --abort
```

**متابعة إعادة التأسيس بعد حل التعارضات:**
```bash
git rebase --continue
```

### حل التعارضات

**وضع علامة على ملف كمحلول:**
```bash
git add <resolved-file>
```

**حذف ملف محلول:**
```bash
git rm <resolved-file>
```

### ضغط الإيداعات

**إعادة تأسيس تفاعلية لضغط الإيداعات:**
```bash
git rebase -i <commit-just-before-first>
```

**مثال على إعداد الضغط:**
```
# قبل
pick <commit_id>
pick <commit_id2>
pick <commit_id3>

# بعد (ضغط commit_id2 و commit_id3 في commit_id)
pick <commit_id>
squash <commit_id2>
squash <commit_id3>
```

---

## ↩️ التراجع

### تجاهل التغييرات

**تجاهل جميع التغييرات المحلية:**
```bash
git reset --hard HEAD
```

**إلغاء تحضير جميع الملفات:**
```bash
git reset HEAD
```

**تجاهل التغييرات في ملف محدد:**
```bash
git checkout HEAD <file>
```

### عمليات إعادة التعيين

**إعادة التعيين إلى إيداع سابق (تجاهل جميع التغييرات):**
```bash
git reset --hard <commit>
```

**إعادة التعيين إلى حالة الفرع البعيد:**
```bash
git reset --hard <remote/branch>
# مثال: git reset --hard upstream/master
```

**إعادة التعيين مع الاحتفاظ بالتغييرات كغير محضّرة:**
```bash
git reset <commit>
```

**إعادة التعيين مع الاحتفاظ بالتغييرات المحلية غير المودعة:**
```bash
git reset --keep <commit>
```

### التراجع عن الإيداعات

**التراجع عن إيداع (إنشاء إيداع جديد بتغييرات معاكسة):**
```bash
git revert <commit>
```

### تنظيف الملفات المتجاهلة

**حذف الملفات التي أُودعت بالخطأ والتي يجب تجاهلها:**
```bash
git rm -r --cached .
git add .
git commit -m "remove ignored files"
```

---

## 🌊 Git Flow

**Git-flow المحسّن:** [git-flow-avh](https://github.com/petervanderdoes/gitflow-avh)

### 📋 جدول المحتويات
- [🔧 الإعداد](#setup-1)
- [🚀 البدء](#getting-started)
- [✨ الميزات](#features)
- [🎁 إنشاء إصدار](#make-a-release)
- [🔥 الإصلاحات العاجلة](#hotfixes)
- [📊 نظرة عامة على الأوامر](#commands-overview)

---

### 🔧 الإعداد {#setup-1}

> **متطلب أساسي:** يجب أن يكون Git مثبتاً ويعمل. Git-flow يعمل على macOS و Linux و Windows.

**macOS (Homebrew):**
```bash
brew install git-flow-avh
```

**macOS (MacPorts):**
```bash
port install git-flow
```

**Linux (توزيعات Debian):**
```bash
sudo apt-get install git-flow
```

**Windows (Cygwin):**
> يتطلب wget و util-linux
```bash
wget -q -O - --no-check-certificate https://raw.githubusercontent.com/petervanderdoes/gitflow/develop/contrib/gitflow-installer.sh install <state> | bash
```

---

### 🚀 البدء

يحتاج Git-flow إلى التهيئة لتخصيص إعدادات مشروعك.

**التهيئة (تفاعلية):**
```bash
git flow init
```
> ستجيب على أسئلة حول اتفاقيات تسمية الفروع. يُنصح باستخدام القيم الافتراضية.

**التهيئة (استخدام الافتراضيات):**
```bash
git flow init -d
```

---

### ✨ الميزات

الميزات مخصصة لتطوير وظائف جديدة للإصدارات القادمة. عادةً ما توجد فقط في مستودعات المطورين.

**بدء ميزة جديدة:**
```bash
git flow feature start MYFEATURE
```
> ينشئ فرع ميزة بناءً على 'develop' وينتقل إليه

**إنهاء ميزة:**
```bash
git flow feature finish MYFEATURE
```
> سيقوم بـ:
> 1. دمج MYFEATURE في 'develop'
> 2. حذف فرع الميزة
> 3. العودة إلى 'develop'

**نشر ميزة (للتعاون):**
```bash
git flow feature publish MYFEATURE
```

**الحصول على ميزة منشورة:**
```bash
git flow feature pull origin MYFEATURE
```

**تتبع ميزة من المصدر:**
```bash
git flow feature track MYFEATURE
```

---

### 🎁 إنشاء إصدار

الإصدارات تدعم تحضير إصدارات الإنتاج الجديدة، وتسمح بإصلاحات الأخطاء الطفيفة وتحضير البيانات الوصفية.

**بدء إصدار:**
```bash
git flow release start RELEASE [BASE]
```
> ينشئ فرع إصدار من 'develop'. اختيارياً حدد [BASE] وهو SHA-1 للإيداع.

**نشر الإصدار:**
```bash
git flow release publish RELEASE
```

**تتبع إصدار بعيد:**
```bash
git flow release track RELEASE
```

**إنهاء الإصدار:**
```bash
git flow release finish RELEASE
```
> سيقوم بـ:
> 1. دمج فرع الإصدار في 'master'
> 2. وضع علامة على الإصدار
> 3. إعادة دمج الإصدار في 'develop'
> 4. حذف فرع الإصدار

> 💡 **لا تنسَ:** ادفع العلامات باستخدام `git push --tags`

---

### 🔥 الإصلاحات العاجلة

الإصلاحات العاجلة تعالج المشاكل الحرجة في إصدارات الإنتاج الحية. تتفرع من العلامة المقابلة على master.

**بدء إصلاح عاجل:**
```bash
git flow hotfix start VERSION [BASENAME]
```

**إنهاء إصلاح عاجل:**
```bash
git flow hotfix finish VERSION
```
> يُدمج مرة أخرى في كل من 'develop' و 'master'، ويضع علامة على دمج master

---

### 📊 نظرة عامة على الأوامر

<p align="center">
    <img alt="أوامر Git Flow" src="../Img/git-flow-commands.png" height="270" width="460">
</p>

### 🌊 مخطط Git Flow

<p align="center">
    <img alt="مخطط Git Flow" src="../Img/git-flow-commands-without-flow.png">
</p>

---


## 🌍 لغات أخرى

هذا الدليل المرجعي متوفر بعدة لغات:

| اللغة | الرابط |
|-------|--------|
| 🇸🇦 العربية | **الحالي** |
| 🇧🇩 البنغالية | [git-cheat-sheet-bn.md](git-cheat-sheet-bn.md) |
| 🇧🇷 البرتغالية البرازيلية | [git-cheat-sheet-pt_BR.md](git-cheat-sheet-pt_BR.md) |
| 🇨🇳 الصينية | [git-cheat-sheet-zh.md](git-cheat-sheet-zh.md) |
| 🇩🇪 الألمانية | [git-cheat-sheet-de.md](git-cheat-sheet-de.md) |
| 🇬🇷 اليونانية | [git-cheat-sheet-el.md](git-cheat-sheet-el.md) |
| 🇮🇳 الهندية | [git-cheat-sheet-hi.md](git-cheat-sheet-hi.md) |
| 🇰🇷 الكورية | [git-cheat-sheet-ko.md](git-cheat-sheet-ko.md) |
| 🇵🇱 البولندية | [git-cheat-sheet-pl.md](git-cheat-sheet-pl.md) |
| 🇪🇸 الإسبانية | [git-cheat-sheet-es.md](git-cheat-sheet-es.md) |
| 🇹🇷 التركية | [git-cheat-sheet-tr.md](git-cheat-sheet-tr.md) |
| 🇺🇸 الإنجليزية | [README.md](../README.md) |

---

## 🤝 المساهمة

نرحب بالمساهمات! يمكنك:

- 🐛 الإبلاغ عن الأخطاء
- ✨ إضافة أوامر Git جديدة
- 🌍 الترجمة إلى لغات جديدة
- 💡 تحسين الشروحات
- 📝 تحسين التنسيق

**كيفية المساهمة:**
1. انسخ (Fork) هذا المستودع
2. أنشئ فرع الميزة (`git checkout -b feature/AmazingFeature`)
3. أودع تغييراتك (`git commit -m 'Add some AmazingFeature'`)
4. ادفع إلى الفرع (`git push origin feature/AmazingFeature`)
5. افتح طلب سحب (Pull Request)

---

## 📄 الترخيص

هذا المشروع مفتوح المصدر ومتاح تحت [رخصة MIT](../LICENSE).

---

<p align="center">
    <b>⭐ امنح هذا المستودع نجمة إذا وجدته مفيداً!</b>
</p>
