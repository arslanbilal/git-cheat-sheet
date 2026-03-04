# Git এবং Git Flow চিট শিট 
[![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

<p align="center">
    <img alt="Git" src="../Img/git-logo.png" height="190" width="455">
</p>

---

## 📖 সম্পর্কে

এই বিস্তৃত Git চিট শিটটি আপনাকে সবকিছু মুখস্ত না করেই Git কমান্ডগুলো আয়ত্ত করতে সাহায্য করবে। আপনি শিক্ষানবিস হোন বা অভিজ্ঞ ডেভেলপার, এই গাইডটি প্রয়োজনীয় Git অপারেশনগুলোর দ্রুত রেফারেন্স প্রদান করে।

**অবদান স্বাগত!** আপনি যা করতে পারেন:
- ব্যাকরণ ত্রুটি ঠিক করুন
- নতুন কমান্ড যোগ করুন
- আপনার ভাষায় অনুবাদ করুন
- ব্যাখ্যা উন্নত করুন

---
## 📋 সূচিপত্র

- [🔧 সেটআপ](#-সেটআপ)
- [⚙️ কনফিগারেশন ফাইল](#️-কনফিগারেশন-ফাইল)
- [🆕 রিপোজিটরি তৈরি](#-রিপোজিটরি-তৈরি)
- [📝 লোকাল পরিবর্তন](#-লোকাল-পরিবর্তন)
- [🔍 অনুসন্ধান](#-অনুসন্ধান)
- [📖 কমিট ইতিহাস](#-কমিট-ইতিহাস)
- [📁 সরানো / নাম পরিবর্তন](#-সরানো--নাম-পরিবর্তন)
- [🌿 ব্রাঞ্চ ও ট্যাগ](#-ব্রাঞ্চ-ও-ট্যাগ)
- [🔄 আপডেট ও প্রকাশ](#-আপডেট-ও-প্রকাশ)
- [🔀 মার্জ ও রিবেস](#-মার্জ-ও-রিবেস)
- [↩️ পূর্বাবস্থায় ফেরানো](#️-পূর্বাবস্থায়-ফেরানো)
- [🌊 Git Flow](#-git-flow)
- [🌍 অন্যান্য ভাষা](#-অন্যান্য-ভাষা)

---

## 🔧 সেটআপ

### কনফিগারেশন দেখুন

**বর্তমান কনফিগারেশন দেখুন:**
```bash
git config --list
```

**রিপোজিটরি কনফিগারেশন দেখুন:**
```bash
git config --local --list
```

**গ্লোবাল কনফিগারেশন দেখুন:**
```bash
git config --global --list
```

**সিস্টেম কনফিগারেশন দেখুন:**
```bash
git config --system --list
```

### ব্যবহারকারী কনফিগারেশন

**ভার্সন ইতিহাসের জন্য আপনার নাম সেট করুন:**
```bash
git config --global user.name "[firstname lastname]"
```

**আপনার ইমেইল ঠিকানা সেট করুন:**
```bash
git config --global user.email "[valid-email]"
```

### ডিসপ্লে ও এডিটর সেটিংস

**স্বয়ংক্রিয় কমান্ড লাইন রঙ সক্রিয় করুন:**
```bash
git config --global color.ui auto
```

**কমিটের জন্য গ্লোবাল এডিটর সেট করুন:**
```bash
git config --global core.editor vi
```

---

## ⚙️ কনফিগারেশন ফাইল

| পরিসর | অবস্থান | কমান্ড ফ্ল্যাগ |
|-------|----------|--------------|
| **রিপোজিটরি** | `<repo>/.git/config` | `--local` |
| **ব্যবহারকারী** | `~/.gitconfig` | `--global` |
| **সিস্টেম** | `/etc/gitconfig` | `--system` |

---

## 🆕 রিপোজিটরি তৈরি

### বিদ্যমান রিপোজিটরি ক্লোন করুন

**SSH এর মাধ্যমে:**
```bash
git clone ssh://user@domain.com/repo.git
```

**HTTPS এর মাধ্যমে:**
```bash
git clone https://domain.com/user/repo.git
```

### নতুন রিপোজিটরি শুরু করুন

**বর্তমান ডিরেক্টরিতে রিপোজিটরি তৈরি করুন:**
```bash
git init
```

**নির্দিষ্ট ডিরেক্টরিতে রিপোজিটরি তৈরি করুন:**
```bash
git init <directory>
```

---

## 📝 লোকাল পরিবর্তন

### স্ট্যাটাস ও পার্থক্য পরীক্ষা করুন

**ওয়ার্কিং ডিরেক্টরির স্ট্যাটাস দেখুন:**
```bash
git status
```

**ট্র্যাক করা ফাইলের পরিবর্তন দেখুন:**
```bash
git diff
```

**নির্দিষ্ট ফাইলের পরিবর্তন দেখুন:**
```bash
git diff <file>
```

### পরিবর্তন স্টেজিং

**সব বর্তমান পরিবর্তন যোগ করুন:**
```bash
git add .
```

**নির্দিষ্ট ফাইল যোগ করুন:**
```bash
git add <filename1> <filename2>
```

**ইন্টারঅ্যাক্টিভভাবে ফাইলের অংশ যোগ করুন:**
```bash
git add -p <file>
```

### পরিবর্তন কমিট করুন

**সব ট্র্যাক করা ফাইলের পরিবর্তন কমিট করুন:**
```bash
git commit -a
```

**স্টেজ করা পরিবর্তন কমিট করুন:**
```bash
git commit
```

**বার্তা সহ কমিট করুন:**
```bash
git commit -m 'message here'
```

**স্টেজিং এড়িয়ে বার্তা সহ কমিট করুন:**
```bash
git commit -am 'message here'
```

**নির্দিষ্ট তারিখে কমিট করুন:**
```bash
git commit --date="`date --date='n day ago'`" -am "<Commit Message Here>"
```

### শেষ কমিট সংশোধন করুন

> ⚠️ **সতর্কতা:** প্রকাশিত কমিট সংশোধন করবেন না!

**শেষ কমিট সংশোধন করুন:**
```bash
git commit -a --amend
```

**কমিট বার্তা পরিবর্তন না করে সংশোধন করুন:**
```bash
git commit --amend --no-edit
```

**কমিটারের তারিখ পরিবর্তন করুন:**
```bash
GIT_COMMITTER_DATE="date" git commit --amend
```

**লেখকের তারিখ পরিবর্তন করুন:**
```bash
git commit --amend --date="date"
```

### পরিবর্তন স্ট্যাশ করা

**বর্তমান পরিবর্তন অস্থায়ীভাবে সংরক্ষণ করুন:**
```bash
git stash
```

**শেষ স্ট্যাশ করা পরিবর্তন প্রয়োগ করুন:**
```bash
git stash apply
```

**নির্দিষ্ট স্ট্যাশ প্রয়োগ করুন:**
```bash
git stash apply stash@{stash_number}
```
> উপলব্ধ স্ট্যাশ দেখতে `git stash list` ব্যবহার করুন

**শেষ স্ট্যাশ মুছুন:**
```bash
git stash drop
```

**অকমিটেড পরিবর্তন অন্য ব্রাঞ্চে স্থানান্তর করুন:**
```bash
git stash
git checkout branch2
git stash pop
```

---

## 🔍 অনুসন্ধান

### টেক্সট অনুসন্ধান

**সব ফাইলে টেক্সট অনুসন্ধান করুন:**
```bash
git grep "Hello"
```

**নির্দিষ্ট ভার্সনে অনুসন্ধান করুন:**
```bash
git grep "Hello" v2.5
```

### কমিট অনুসন্ধান

**নির্দিষ্ট কীওয়ার্ড যোগ করা কমিট খুঁজুন:**
```bash
git log -S 'keyword'
```

**রেগুলার এক্সপ্রেশন দিয়ে অনুসন্ধান করুন:**
```bash
git log -S 'keyword' --pickaxe-regex
```

---

## 📖 কমিট ইতিহাস

### মৌলিক ইতিহাস

**সব কমিট দেখুন (বিস্তারিত):**
```bash
git log
```

**কমিট দেখুন (প্রতিটি এক লাইনে):**
```bash
git log --oneline
```

**নির্দিষ্ট লেখকের কমিট দেখুন:**
```bash
git log --author="username"
```

**নির্দিষ্ট ফাইলের পরিবর্তন দেখুন:**
```bash
git log -p <file>
```

### উন্নত ইতিহাস

**ব্রাঞ্চ তুলনা করুন:**
```bash
git log --oneline <origin/master>..<remote/master> --left-right
```

**কে কখন কী পরিবর্তন করেছে দেখুন:**
```bash
git blame <file>
```

### রেফারেন্স লগ

**রেফারেন্স লগ দেখুন:**
```bash
git reflog show
```

**রেফারেন্স লগ মুছুন:**
```bash
git reflog delete
```

---

## 📁 সরানো / নাম পরিবর্তন

**একটি ফাইলের নাম পরিবর্তন করুন:**
```bash
git mv Index.txt Index.html
```

---

## 🌿 ব্রাঞ্চ ও ট্যাগ

### ব্রাঞ্চ তালিকা

**লোকাল ব্রাঞ্চ তালিকা দেখুন:**
```bash
git branch
```

**সব ব্রাঞ্চ তালিকা দেখুন (লোকাল + রিমোট):**
```bash
git branch -a
```

**রিমোট ব্রাঞ্চ তালিকা দেখুন:**
```bash
git branch -r
```

**মার্জ হওয়া ব্রাঞ্চ তালিকা দেখুন:**
```bash
git branch --merged
```

### ব্রাঞ্চ পরিবর্তন ও তৈরি

**বিদ্যমান ব্রাঞ্চে সুইচ করুন:**
```bash
git checkout <branch>
```

**নতুন ব্রাঞ্চ তৈরি করে সুইচ করুন:**
```bash
git checkout -b <branch>
```

**আগের ব্রাঞ্চে সুইচ করুন:**
```bash
git checkout -
```

**বিদ্যমান ব্রাঞ্চ থেকে ব্রাঞ্চ তৈরি করুন:**
```bash
git checkout -b <new_branch> <existing_branch>
```

**নির্দিষ্ট কমিট থেকে ব্রাঞ্চ তৈরি করুন:**
```bash
git checkout <commit-hash> -b <new_branch_name>
```

**সুইচ না করে ব্রাঞ্চ তৈরি করুন:**
```bash
git branch <new-branch>
```

**ট্র্যাকিং ব্রাঞ্চ তৈরি করুন:**
```bash
git branch --track <new-branch> <remote-branch>
```

### ব্রাঞ্চ অপারেশন

**ভিন্ন ব্রাঞ্চ থেকে একটি ফাইল চেকআউট করুন:**
```bash
git checkout <branch> -- <filename>
```

**অন্য ব্রাঞ্চ থেকে নির্দিষ্ট কমিট প্রয়োগ করুন:**
```bash
git cherry-pick <commit hash>
```

**বর্তমান ব্রাঞ্চের নাম পরিবর্তন করুন:**
```bash
git branch -m <new_branch_name>
```

**লোকাল ব্রাঞ্চ মুছুন:**
```bash
git branch -d <branch>
```

**জোর করে লোকাল ব্রাঞ্চ মুছুন:**
```bash
git branch -D <branch>
```
> ⚠️ **সতর্কতা:** আপনি মার্জ না হওয়া পরিবর্তন হারাবেন!

### ট্যাগ

**HEAD-এ ট্যাগ তৈরি করুন:**
```bash
git tag <tag-name>
```

**টীকাযুক্ত ট্যাগ তৈরি করুন:**
```bash
git tag -a <tag-name>
```

**বার্তা সহ ট্যাগ তৈরি করুন:**
```bash
git tag <tag-name> -am 'message here'
```

**সব ট্যাগ তালিকা দেখুন:**
```bash
git tag
```

**বার্তা সহ ট্যাগ তালিকা দেখুন:**
```bash
git tag -n
```

---

## 🔄 আপডেট ও প্রকাশ

### রিমোট ব্যবস্থাপনা

**কনফিগার করা রিমোট তালিকা দেখুন:**
```bash
git remote -v
```

**রিমোটের তথ্য দেখুন:**
```bash
git remote show <remote>
```

**নতুন রিমোট যোগ করুন:**
```bash
git remote add <remote> <url>
```

**রিমোটের নাম পরিবর্তন করুন:**
```bash
git remote rename <remote> <new_remote>
```

**রিমোট মুছুন:**
```bash
git remote rm <remote>
```
> ℹ️ **নোট:** এটি শুধুমাত্র লোকালভাবে রিমোট রেফারেন্স মুছে দেয়, রিমোট রিপোজিটরি নিজে নয়।

### ফেচ ও পুল

**মার্জ না করে পরিবর্তন ডাউনলোড করুন:**
```bash
git fetch <remote>
```

**পরিবর্তন ডাউনলোড ও মার্জ করুন:**
```bash
git pull <remote> <branch>
```

**মেইন ব্রাঞ্চ থেকে পরিবর্তন আনুন:**
```bash
git pull origin master
```

**রিবেস সহ পুল করুন:**
```bash
git pull --rebase <remote> <branch>
```

### পুশ ও প্রকাশ

**লোকাল পরিবর্তন প্রকাশ করুন:**
```bash
git push <remote> <branch>
```

**রিমোট ব্রাঞ্চ মুছুন:**
```bash
# Git v1.7.0+
git push <remote> --delete <branch>

# Git v1.5.0+
git push <remote> :<branch>
```

**ট্যাগ প্রকাশ করুন:**
```bash
git push --tags
```

---

## 🔀 মার্জ ও রিবেস

### মার্জ অপারেশন

**বর্তমান HEAD-এ ব্রাঞ্চ মার্জ করুন:**
```bash
git merge <branch>
```

**গ্লোবালভাবে মার্জ টুল কনফিগার করুন:**
```bash
git config --global merge.tool meld
```

**কনফিগার করা মার্জ টুল ব্যবহার করুন:**
```bash
git mergetool
```

### রিবেস অপারেশন

> ⚠️ **সতর্কতা:** প্রকাশিত কমিট রিবেস করবেন না!

**বর্তমান HEAD ব্রাঞ্চে রিবেস করুন:**
```bash
git rebase <branch>
```

**রিবেস বাতিল করুন:**
```bash
git rebase --abort
```

**কনফ্লিক্ট সমাধানের পর রিবেস চালিয়ে যান:**
```bash
git rebase --continue
```

### কনফ্লিক্ট সমাধান

**ফাইলকে সমাধানকৃত হিসেবে চিহ্নিত করুন:**
```bash
git add <resolved-file>
```

**সমাধানকৃত ফাইল মুছুন:**
```bash
git rm <resolved-file>
```

### কমিট স্কোয়াশ করা

**স্কোয়াশ করার জন্য ইন্টারঅ্যাক্টিভ রিবেস:**
```bash
git rebase -i <commit-just-before-first>
```

**স্কোয়াশ কনফিগারেশনের উদাহরণ:**
```
# আগে
pick <commit_id>
pick <commit_id2>
pick <commit_id3>

# পরে (commit_id2 এবং commit_id3 কে commit_id তে স্কোয়াশ করুন)
pick <commit_id>
squash <commit_id2>
squash <commit_id3>
```

---

## ↩️ পূর্বাবস্থায় ফেরানো

### পরিবর্তন বাতিল করুন

**সব লোকাল পরিবর্তন বাতিল করুন:**
```bash
git reset --hard HEAD
```

**সব ফাইল আনস্টেজ করুন:**
```bash
git reset HEAD
```

**নির্দিষ্ট ফাইলের পরিবর্তন বাতিল করুন:**
```bash
git checkout HEAD <file>
```

### রিসেট অপারেশন

**আগের কমিটে রিসেট করুন (সব পরিবর্তন বাতিল করুন):**
```bash
git reset --hard <commit>
```

**রিমোট ব্রাঞ্চের অবস্থায় রিসেট করুন:**
```bash
git reset --hard <remote/branch>
# উদাহরণ: git reset --hard upstream/master
```

**পরিবর্তন আনস্টেজড হিসেবে রেখে রিসেট করুন:**
```bash
git reset <commit>
```

**অকমিটেড লোকাল পরিবর্তন রেখে রিসেট করুন:**
```bash
git reset --keep <commit>
```

### কমিট রিভার্ট

**কমিট রিভার্ট করুন (বিপরীত পরিবর্তন সহ নতুন কমিট তৈরি করুন):**
```bash
git revert <commit>
```

### উপেক্ষিত ফাইল পরিষ্কার করুন

**ভুলবশত কমিট হওয়া উপেক্ষিত ফাইল মুছুন:**
```bash
git rm -r --cached .
git add .
git commit -m "remove ignored files"
```

---

## 🌊 Git Flow

**উন্নত Git-flow:** [git-flow-avh](https://github.com/petervanderdoes/gitflow-avh)

### �� সূচিপত্র
- [🔧 সেটআপ](#setup-1)
- [🚀 শুরু করা](#getting-started)
- [✨ ফিচার](#features)
- [🎁 রিলিজ তৈরি](#make-a-release)
- [🔥 হটফিক্স](#hotfixes)
- [📊 কমান্ড ওভারভিউ](#commands-overview)

---

### 🔧 সেটআপ {#setup-1}

> **পূর্বশর্ত:** কার্যকরী Git ইনস্টলেশন প্রয়োজন। Git-flow macOS, Linux এবং Windows-এ কাজ করে।

**macOS (Homebrew):**
```bash
brew install git-flow-avh
```

**macOS (MacPorts):**
```bash
port install git-flow
```

**Linux (Debian-ভিত্তিক):**
```bash
sudo apt-get install git-flow
```

**Windows (Cygwin):**
> wget এবং util-linux প্রয়োজন
```bash
wget -q -O - --no-check-certificate https://raw.githubusercontent.com/petervanderdoes/gitflow/develop/contrib/gitflow-installer.sh install <state> | bash
```

---

### 🚀 শুরু করা

আপনার প্রজেক্ট সেটআপ কাস্টমাইজ করতে Git-flow-এর ইনিশিয়ালাইজেশন প্রয়োজন।

**ইনিশিয়ালাইজ করুন (ইন্টারঅ্যাক্টিভ):**
```bash
git flow init
```
> আপনাকে ব্রাঞ্চ নামকরণ নিয়ম সম্পর্কে প্রশ্নের উত্তর দিতে হবে। ডিফল্ট মান সুপারিশ করা হয়।

**ইনিশিয়ালাইজ করুন (ডিফল্ট ব্যবহার করুন):**
```bash
git flow init -d
```

---

### ✨ ফিচার

ফিচারগুলো আসন্ন রিলিজের জন্য নতুন কার্যকারিতা ডেভেলপ করতে ব্যবহৃত হয়। এগুলো সাধারণত শুধুমাত্র ডেভেলপার রিপোজিটরিতে থাকে।

**নতুন ফিচার শুরু করুন:**
```bash
git flow feature start MYFEATURE
```
> 'develop' ভিত্তিক ফিচার ব্রাঞ্চ তৈরি করে এবং সেখানে সুইচ করে

**ফিচার শেষ করুন:**
```bash
git flow feature finish MYFEATURE
```
> এটি করবে:
> 1. MYFEATURE কে 'develop'-এ মার্জ করবে
> 2. ফিচার ব্রাঞ্চ মুছে দেবে
> 3. 'develop'-এ ফিরে যাবে

**ফিচার প্রকাশ করুন (সহযোগিতার জন্য):**
```bash
git flow feature publish MYFEATURE
```

**প্রকাশিত ফিচার আনুন:**
```bash
git flow feature pull origin MYFEATURE
```

**অরিজিন ফিচার ট্র্যাক করুন:**
```bash
git flow feature track MYFEATURE
```

---

### 🎁 রিলিজ তৈরি

রিলিজ নতুন প্রোডাকশন রিলিজের প্রস্তুতি সমর্থন করে, ছোট বাগ ফিক্স এবং মেটা-ডেটা প্রস্তুত করার অনুমতি দেয়।

**রিলিজ শুরু করুন:**
```bash
git flow release start RELEASE [BASE]
```
> 'develop' থেকে রিলিজ ব্রাঞ্চ তৈরি করে। ঐচ্ছিকভাবে [BASE] কমিট SHA-1 উল্লেখ করুন।

**রিলিজ প্রকাশ করুন:**
```bash
git flow release publish RELEASE
```

**রিমোট রিলিজ ট্র্যাক করুন:**
```bash
git flow release track RELEASE
```

**রিলিজ শেষ করুন:**
```bash
git flow release finish RELEASE
```
> এটি করবে:
> 1. রিলিজ ব্রাঞ্চকে 'master'-এ মার্জ করবে
> 2. রিলিজ ট্যাগ করবে
> 3. 'develop'-এ রিলিজ ব্যাক-মার্জ করবে
> 4. রিলিজ ব্রাঞ্চ মুছে দেবে

> 💡 **ভুলবেন না:** `git push --tags` দিয়ে আপনার ট্যাগ পুশ করুন

---

### 🔥 হটফিক্স

হটফিক্স লাইভ প্রোডাকশন ভার্সনের গুরুতর সমস্যা সমাধান করে। এগুলো master-এর সংশ্লিষ্ট ট্যাগ থেকে ব্রাঞ্চ করে।

**হটফিক্স শুরু করুন:**
```bash
git flow hotfix start VERSION [BASENAME]
```

**হটফিক্স শেষ করুন:**
```bash
git flow hotfix finish VERSION
```
> 'develop' এবং 'master' উভয়েই ব্যাক-মার্জ করে এবং master মার্জ ট্যাগ করে

---

### 📊 কমান্ড ওভারভিউ

<p align="center">
    <img alt="Git Flow Commands" src="../Img/git-flow-commands.png" height="270" width="460">
</p>

### 🌊 Git Flow স্কিমা

<p align="center">
    <img alt="Git Flow Schema" src="../Img/git-flow-commands-without-flow.png">
</p>

---


## 🌍 অন্যান্য ভাষা

এই চিট শিটটি একাধিক ভাষায় উপলব্ধ:

| ভাষা | লিংক |
|----------|------|
| 🇸🇦 আরবি | [git-cheat-sheet-ar.md](git-cheat-sheet-ar.md) |
| 🇧🇩 **বাংলা** | **(বর্তমান)** |
| 🇧🇷 ব্রাজিলিয়ান পর্তুগিজ | [git-cheat-sheet-pt_BR.md](git-cheat-sheet-pt_BR.md) |
| 🇨🇳 চীনা | [git-cheat-sheet-zh.md](git-cheat-sheet-zh.md) |
| 🇩🇪 জার্মান | [git-cheat-sheet-de.md](git-cheat-sheet-de.md) |
| 🇬🇷 গ্রিক | [git-cheat-sheet-el.md](git-cheat-sheet-el.md) |
| 🇮🇳 হিন্দি | [git-cheat-sheet-hi.md](git-cheat-sheet-hi.md) |
| 🇰🇷 কোরিয়ান | [git-cheat-sheet-ko.md](git-cheat-sheet-ko.md) |
| 🇵🇱 পোলিশ | [git-cheat-sheet-pl.md](git-cheat-sheet-pl.md) |
| 🇪🇸 স্প্যানিশ | [git-cheat-sheet-es.md](git-cheat-sheet-es.md) |
| 🇹🇷 তুর্কি | [git-cheat-sheet-tr.md](git-cheat-sheet-tr.md) |
| 🇺🇸 ইংরেজি | [README.md](../README.md) |

---

## 🤝 অবদান

আমরা অবদানকে স্বাগত জানাই! আপনি যা করতে পারেন:

- 🐛 বাগ বা টাইপো রিপোর্ট করুন
- ✨ নতুন Git কমান্ড যোগ করুন
- 🌍 নতুন ভাষায় অনুবাদ করুন
- 💡 ব্যাখ্যা উন্নত করুন
- 📝 ফরম্যাটিং উন্নত করুন

**কিভাবে অবদান রাখবেন:**
1. এই রিপোজিটরি ফর্ক করুন
2. আপনার ফিচার ব্রাঞ্চ তৈরি করুন (`git checkout -b feature/AmazingFeature`)
3. আপনার পরিবর্তন কমিট করুন (`git commit -m 'Add some AmazingFeature'`)
4. ব্রাঞ্চে পুশ করুন (`git push origin feature/AmazingFeature`)
5. একটি Pull Request খুলুন

---

## 📄 লাইসেন্স

এই প্রকল্পটি ওপেন সোর্স এবং [MIT লাইসেন্স](../LICENSE)-এর অধীনে উপলব্ধ।

---

<p align="center">
    <b>⭐ এই রিপোজিটরি সহায়ক হলে স্টার দিন!</b>
</p>
