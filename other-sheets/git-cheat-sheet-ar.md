# Git Cheat Sheet العربية

![Git Logo](../Img/git-logo.png)

دليل مرجعي سريع لأكثر أوامر Git استخداماً، منظم حسب الفئات لسهولة الاستخدام.

---

## 📖 حول هذا الدليل

هذا الدليل المرجعي لـ Git هو مرجع شامل لكل من يريد تحسين سير عمله مع Git. من المبتدئين الذين يبدؤون رحلتهم مع Git إلى المطورين ذوي الخبرة، يوفر هذا الدليل أوامر منظمة ومصنفة لتسريع رحلة التطوير الخاصة بك.

### الميزات الرئيسية:
- **فئات منظمة**: الأوامر مرتبة في مجموعات واضحة ومنطقية
- **أمثلة عملية**: مع حالات استخدام من العالم الحقيقي
- **مناسب للمبتدئين**: مع شروحات واضحة ونصائح
- **مرجع فوري**: وصول سريع للأوامر الأساسية

---

## 📑 جدول المحتويات

- [🔧 الإعداد الأولي](#الإعداد-الأولي)
- [⚙️ ملفات الإعداد](#ملفات-الإعداد)
- [📁 إعداد المستودع](#إعداد-المستودع)
- [📊 أوامر الحالة](#أوامر-الحالة)
- [📝 إدارة الملفات](#إدارة-الملفات)
- [💾 التثبيتات (Commits)](#التثبيتات-commits)
- [🌿 الفروع (Branches)](#الفروع-branches)
- [🔀 الدمج (Merge)](#الدمج-merge)
- [🌐 المستودعات البعيدة](#المستودعات-البعيدة)
- [📚 السجل والتاريخ](#السجل-والتاريخ)
- [🔍 البحث](#البحث)
- [📋 النقل/إعادة التسمية](#النقل-إعادة-التسمية)
- [🏷️ العلامات (Tags)](#العلامات-tags)
- [↩️ التراجع عن التغييرات](#التراجع-عن-التغييرات)
- [📦 المخزن المؤقت (Stash)](#المخزن-المؤقت-stash)
- [🌊 Git Flow](#git-flow)
- [💡 نصائح مفيدة](#نصائح-مفيدة)
- [🌍 لغات أخرى](#لغات-أخرى)
- [🤝 المساهمة](#المساهمة)
- [📄 الترخيص](#الترخيص)
- [📖 مصادر إضافية](#مصادر-إضافية)

---

## 🔧 الإعداد الأولي

إعداد Git بمعلوماتك الشخصية:

```bash
# إعداد اسم المستخدم
git config --global user.name "اسمك"

# إعداد البريد الإلكتروني
git config --global user.email "email@example.com"

# عرض الإعدادات الحالية
git config --list

# إعداد المحرر الافتراضي
git config --global core.editor "nano"

# إعداد أداة المقارنة
git config --global merge.tool vimdiff
```

---

## ⚙️ ملفات الإعداد

يتم تخزين إعدادات Git على ثلاثة مستويات:

| المستوى | موقع الملف | الأمر | الوصف |
|---------|------------|-------|--------|
| **System** | `/etc/gitconfig` | `--system` | إعدادات على مستوى النظام لجميع المستخدمين |
| **Global** | `~/.gitconfig` أو `~/.config/git/config` | `--global` | إعدادات للمستخدم الحالي |
| **Local** | `.git/config` | `--local` (افتراضي) | إعدادات للمستودع الحالي |

```bash
# عرض مستوى الإعداد
git config --show-origin user.name

# تعيين إعداد على مستوى محدد
git config --local user.name "اسم المشروع"
git config --global user.email "global@example.com"
```

---

## 📁 إعداد المستودع

### إنشاء مستودع جديد:

```bash
# إنشاء مستودع Git جديد
git init

# نسخ مستودع موجود
git clone <رابط-المستودع>

# نسخ إلى مجلد محدد
git clone <رابط-المستودع> <اسم-المجلد>
```

---

## 📊 أوامر الحالة

### فحص حالة المستودع:

```bash
# عرض الحالة الحالية للمستودع
git status

# عرض الحالة بصيغة مختصرة
git status -s

# عرض الحالة متجاهلاً الملفات غير المتتبعة
git status --ignored

# عرض الاختلافات في الملفات المعدلة
git diff

# عرض الاختلافات في منطقة التحضير
git diff --staged

# عرض الاختلافات بين الفروع
git diff <فرع1> <فرع2>
```

---

## 📝 إدارة الملفات

### إضافة وحذف الملفات:

```bash
# إضافة ملف محدد لمنطقة التحضير
git add <ملف>

# إضافة جميع الملفات المعدلة
git add .

# إضافة جميع الملفات من نوع محدد
git add *.txt

# إضافة تفاعلية
git add -i

# حذف ملف من المستودع ومجلد العمل
git rm <ملف>

# حذف ملف من المستودع فقط (الاحتفاظ به في المجلد)
git rm --cached <ملف>

# نقل/إعادة تسمية ملف
git mv <ملف-المصدر> <ملف-الوجهة>
```

---

## 💾 التثبيتات (Commits)

### حفظ التغييرات في المستودع:

```bash
# تثبيت مع رسالة
git commit -m "رسالة التثبيت"

# تثبيت مع إضافة جميع الملفات المعدلة
git commit -am "رسالة التثبيت"

# تعديل التثبيت الأخير
git commit --amend

# تثبيت فارغ (مفيد لـ CI/CD)
git commit --allow-empty -m "تشغيل CI"

# تثبيت مع رسالة مفصلة (يفتح المحرر)
git commit
```

---

## 🌿 الفروع (Branches)

### العمل مع الفروع:

```bash
# عرض جميع الفروع
git branch

# عرض الفروع البعيدة
git branch -r

# عرض جميع الفروع (محلية وبعيدة)
git branch -a

# إنشاء فرع جديد
git branch <اسم-الفرع>

# التبديل إلى فرع
git checkout <اسم-الفرع>

# إنشاء والتبديل إلى فرع جديد
git checkout -b <اسم-الفرع>

# إنشاء فرع من تثبيت محدد
git checkout -b <اسم-الفرع> <هاش-التثبيت>

# حذف فرع
git branch -d <اسم-الفرع>

# حذف فرع بالقوة
git branch -D <اسم-الفرع>

# إعادة تسمية الفرع الحالي
git branch -m <الاسم-الجديد>

# إعادة تسمية فرع محدد
git branch -m <الاسم-القديم> <الاسم-الجديد>
```

---

## 🔀 الدمج (Merge)

### دمج التغييرات بين الفروع:

```bash
# دمج فرع في الفرع الحالي
git merge <اسم-الفرع>

# دمج بدون fast-forward (إنشاء تثبيت دمج)
git merge --no-ff <اسم-الفرع>

# دمج فقط إذا كان fast-forward
git merge --ff-only <اسم-الفرع>

# إلغاء عملية الدمج الجارية
git merge --abort

# متابعة الدمج بعد حل التعارضات
git merge --continue
```

---

## 🌐 المستودعات البعيدة

### إدارة المستودعات البعيدة:

```bash
# عرض المستودعات البعيدة
git remote

# عرض المستودعات البعيدة مع الروابط
git remote -v

# إضافة مستودع بعيد
git remote add <اسم> <رابط>

# تغيير رابط المستودع البعيد
git remote set-url <اسم> <رابط-جديد>

# حذف مستودع بعيد
git remote remove <اسم>

# رفع التغييرات للمستودع البعيد
git push <بعيد> <فرع>

# رفع فرع وتعيين التتبع
git push -u <بعيد> <فرع>

# رفع جميع الفروع
git push --all

# رفع العلامات
git push --tags

# تحميل التغييرات من المستودع البعيد
git pull <بعيد> <فرع>

# تحميل التغييرات بدون دمج
git fetch <بعيد>

# تحميل جميع الفروع البعيدة
git fetch --all
```

---

## 📚 السجل والتاريخ

### استكشاف تاريخ التثبيتات:

```bash
# عرض تاريخ التثبيتات
git log

# عرض التاريخ في سطر واحد لكل تثبيت
git log --oneline

# عرض التاريخ مع رسم بياني
git log --graph

# عرض تاريخ ملف محدد
git log <ملف>

# عرض إحصائيات التثبيتات
git log --stat

# عرض التغييرات في كل تثبيت
git log -p

# عرض آخر N تثبيت
git log -n <عدد>

# عرض التثبيتات بين تواريخ
git log --since="2023-01-01" --until="2023-12-31"

# عرض التثبيتات حسب المؤلف
git log --author="اسم المؤلف"

# البحث في رسائل التثبيت
git log --grep="كلمة مفتاحية"
```

---

## 🔍 البحث

### البحث في الملفات والتثبيتات:

```bash
# البحث عن نص في الملفات
git grep "النص المطلوب"

# البحث في أنواع ملفات محددة
git grep "النمط" -- "*.js"

# البحث في رسائل التثبيت
git log --grep="الرسالة"

# البحث في تغييرات التثبيتات
git log -S "نص الكود"

# البحث عن أسماء الملفات
git ls-files | grep "النمط"

# البحث عن ملفات في الفرع
git ls-tree -r --name-only <اسم-الفرع>
```

---

## 📋 النقل/إعادة التسمية

### نقل وإعادة تسمية الملفات:

```bash
# نقل/إعادة تسمية ملف
git mv <الاسم-القديم> <الاسم-الجديد>

# نقل مجلد
git mv <المجلد-القديم> <المجلد-الجديد>

# بعد نقل الملف يدوياً
mv <الاسم-القديم> <الاسم-الجديد>
git rm <الاسم-القديم>
git add <الاسم-الجديد>

# نقل ملفات متعددة
git mv *.txt <المجلد-الجديد>/

# تتبع تاريخ مسار الملف
git log --follow <اسم-الملف>
```

---

## 🏷️ العلامات (Tags)

### إدارة علامات الإصدارات:

```bash
# عرض جميع العلامات
git tag

# إنشاء علامة خفيفة
git tag <اسم-العلامة>

# إنشاء علامة مشروحة
git tag -a <اسم-العلامة> -m "رسالة العلامة"

# إنشاء علامة على تثبيت محدد
git tag -a <اسم-العلامة> <هاش-التثبيت>

# عرض معلومات علامة
git show <اسم-العلامة>

# حذف علامة محلية
git tag -d <اسم-العلامة>

# حذف علامة بعيدة
git push --delete <بعيد> <اسم-العلامة>

# رفع علامة محددة
git push <بعيد> <اسم-العلامة>

# رفع جميع العلامات
git push <بعيد> --tags
```

---

## ↩️ التراجع عن التغييرات

### التراجع عن التعديلات:

```bash
# إلغاء التغييرات في ملف محدد
git checkout <ملف>

# إلغاء جميع التغييرات غير المثبتة
git checkout .

# إرجاع ملف لإصدار محدد
git checkout <هاش-التثبيت> <ملف>

# إزالة ملف من منطقة التحضير
git reset <ملف>

# إزالة جميع الملفات من منطقة التحضير
git reset

# التراجع للتثبيت السابق (الاحتفاظ بالتغييرات)
git reset --soft HEAD~1

# التراجع للتثبيت السابق (إلغاء التغييرات)
git reset --hard HEAD~1

# التراجع لتثبيت محدد
git reset --hard <هاش-التثبيت>

# إنشاء تثبيت يلغي تثبيت آخر
git revert <هاش-التثبيت>

# إلغاء تثبيتات متعددة
git revert <هاش-من>..<هاش-إلى>
```

---

## 📦 المخزن المؤقت (Stash)

### حفظ العمل مؤقتاً:

```bash
# حفظ التغييرات الحالية في المخزن المؤقت
git stash

# حفظ مع رسالة وصفية
git stash save "رسالة وصفية"

# عرض جميع المخازن المؤقتة
git stash list

# تطبيق آخر مخزن مؤقت
git stash apply

# تطبيق مخزن مؤقت محدد
git stash apply stash@{0}

# تطبيق وحذف آخر مخزن مؤقت
git stash pop

# حذف مخزن مؤقت محدد
git stash drop stash@{0}

# حذف جميع المخازن المؤقتة
git stash clear

# عرض التغييرات في مخزن مؤقت
git stash show stash@{0}

# إنشاء فرع من مخزن مؤقت
git stash branch <اسم-الفرع> stash@{0}
```

---

## 🌊 Git Flow

Git Flow هو نموذج تفريع يحدد سير عمل صارم مصمم حول إطلاق المشروع.

### الفروع الرئيسية:
- **master/main**: كود الإنتاج
- **develop**: فرع التطوير الرئيسي

### فروع الدعم:
- **feature**: للميزات الجديدة
- **release**: لتحضير إصدارات جديدة
- **hotfix**: للإصلاحات العاجلة في الإنتاج

### أوامر Git Flow:

```bash
# تهيئة git flow
git flow init

# بدء ميزة جديدة
git flow feature start <اسم-الميزة>

# إنهاء الميزة
git flow feature finish <اسم-الميزة>

# نشر الميزة
git flow feature publish <اسم-الميزة>

# بدء إصدار
git flow release start <إصدار>

# إنهاء الإصدار
git flow release finish <إصدار>

# بدء إصلاح عاجل
git flow hotfix start <إصدار>

# إنهاء الإصلاح العاجل
git flow hotfix finish <إصدار>
```

### سير العمل بدون Git Flow:

![Git Flow Commands](../Img/git-flow-commands-without-flow.png)

```bash
# إنشاء فرع الميزة
git checkout develop
git checkout -b feature/ميزة-جديدة

# العمل على الميزة
git add .
git commit -m "إضافة ميزة جديدة"

# دمج الميزة في develop
git checkout develop
git merge --no-ff feature/ميزة-جديدة
git branch -d feature/ميزة-جديدة

# إنشاء فرع الإصدار
git checkout develop
git checkout -b release/1.0.0

# إنهاء الإصدار
git checkout master
git merge --no-ff release/1.0.0
git tag -a 1.0.0 -m "الإصدار 1.0.0"
git checkout develop
git merge --no-ff release/1.0.0
git branch -d release/1.0.0
```

---

## 💡 نصائح مفيدة

### اختصارات مفيدة:

```bash
# إعداد اختصارات مفيدة
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
git config --global alias.visual '!gitk'
```

### ملفات .gitignore:

```bash
# إنشاء ملف .gitignore
echo "node_modules/" >> .gitignore
echo "*.log" >> .gitignore
echo ".env" >> .gitignore

# تجاهل ملفات متتبعة بالفعل
git rm --cached <ملف>
echo "<ملف>" >> .gitignore
git add .gitignore
git commit -m "إضافة ملف إلى .gitignore"
```

---

## 🌍 لغات أخرى

هذا الدليل المرجعي لـ Git متوفر باللغات التالية:

- 🇺🇸 [English](../README.md)
- 🇸🇦 **العربية** (الحالي)
- 🇧🇩 [বাংলা](git-cheat-sheet-bn.md)
- 🇩🇪 [Deutsch](git-cheat-sheet-de.md)
- 🇬🇷 [Ελληνικά](git-cheat-sheet-el.md)
- 🇪🇸 [Español](git-cheat-sheet-es.md)
- 🇮🇳 [हिन्दी](git-cheat-sheet-hi.md)
- 🇰🇷 [한국어](git-cheat-sheet-ko.md)
- 🇵🇱 [Polski](git-cheat-sheet-pl.md)
- 🇧🇷 [Português](git-cheat-sheet-pt_BR.md)
- 🇹🇷 [Türkçe](git-cheat-sheet-tr.md)
- 🇨🇳 [中文](git-cheat-sheet-zh.md)

---

## 🤝 المساهمة

نرحب بالمساهمات! للمساعدة في تحسين هذا المشروع:

1. **أبلغ عن المشاكل**: شارك الأخطاء أو اقتراحات التحسين
2. **أضف لغات جديدة**: أنشئ ترجمات أو حسّن الموجودة
3. **حسّن المحتوى**: أضف أوامر جديدة أو أمثلة أو شروحات
4. **قدم ملاحظات**: شارك تجاربك واقتراحاتك

### كيفية المساهمة:
- [افتح مشكلة على GitHub](https://github.com/arslanbilal/git-cheat-sheet/issues)
- أرسل طلب سحب (Pull Request)
- اقترح تحسينات على الوثائق

---

## 📄 الترخيص

هذا المشروع مرخص تحت رخصة MIT. راجع ملف [LICENSE](../LICENSE) لمزيد من التفاصيل.

---

## 📖 مصادر إضافية

- [الوثائق الرسمية لـ Git](https://git-scm.com/doc)
- [دروس Git من Atlassian](https://www.atlassian.com/git/tutorials)
- [ورقة مرجعية لـ Git من GitHub](https://education.github.com/git-cheat-sheet-education.pdf)
- [دروس Git التفاعلية](https://learngitbranching.js.org/)

---

<div align="center">
  <strong>⭐ إذا كان هذا الدليل مفيداً، امنحه نجمة!</strong><br>
  <em>برمجة سعيدة مع Git! 🚀</em>
</div>
