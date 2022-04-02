
গিট এবং গিট ফ্লো চিট শীট [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)
===============
<hr>
<p align="center">
    <img alt="Git" src="../Img/git-logo.png" height="190" width="455">
</p>


<hr>

### সূচিপত্র
* [সেট আপ](#সেট-আপ)
* [কনফিগারেশন ফাইল](#কনফিগারেশন-ফাইল)
* [তৈরী করা](#তৈরী-করা)
* [লোকালি পরিবর্তন করা](#লোকালি-পরিবর্তন-করা)
* [অনুসন্ধান](#অনুসন্ধান)
* [কমিট ইতিহাস](#কমিট-ইতিহাস)
* [সড়ানো বা নাম পরিবর্তন](#সড়ানো-বা-নাম-পরিবর্তন)
* [ব্রাঞ্চ এবং ট্যাগ](#ব্রাঞ্চ-এবং-ট্যাগ)
* [আপডেট এবং প্রকাশ](#আপডেট-এবং-প্রকাশ)
* [মার্জ এবং রিবেস](#মার্জ-এবং-রিবেস)
* [আনডো](#আনডো)
* [গিট ফ্লো](#গিট-ফ্লো)


<hr>

## সেট আপ

##### বর্তমান কনফিগারেশন দেখা:
```
$ git config --list
```
##### রিপোজিটরি কনফিগারেশন দেখা:
```
$ git config --local --list
```

##### গ্লোবাল কনফিগারেশন দেখা:
```
$ git config --global --list
```

##### সিস্টেম কনফিগারেশন দেখা:
```
$ git config --system --list
```

##### সংস্করণকৃত ইতিহাস পর্যালোচনা করার সময় এবং কৃতিত্বের জন্য সনাক্তযোগ্য একটি নাম সেট করুন:
```
$ git config --global user.name "[firstname lastname]"
```

##### একটি ইমেল ঠিকানা সেট করুন যা প্রতিটি ইতিহাস চিহ্নিতকারীর সাথে যুক্ত হবে:
```
$ git config --global user.email "[valid-email]"
```

##### সহজে পর্যালোচনার জন্য গিটের মধ্যে স্বয়ংক্রিয় কমান্ড লাইনের রঙ সেট করুন:
```
$ git config --global color.ui auto
```

##### কমিটের জন্য গ্লোবাল এডিটর সেট করুন:
```
$ git config --global core.editor vi
```

<hr>

## কনফিগারেশন ফাইল

##### রিপোজিটরি স্পেসিফিক কনফিগারেশন ফাইল [--local]:
```
<repo>/.git/config
```

##### ইউজার স্পেসিফিক কনফিগারেশন ফাইল [--global]:
```
~/.gitconfig
```

##### সিস্টেম-ওয়াইজ কনফিগারেশন ফাইল [--system]:
```
/etc/gitconfig
```

<hr>

## তৈরী করা

##### একটি বিদ্যমান রিপোজিটরি ক্লোন করুন:

দুটি উপায় আছে:

SSH এর মাধ্যমে

```
$ git clone ssh://user@domain.com/repo.git
```

HTTP এর মাধ্যমে

```
$ git clone http://domain.com/user/repo.git
```

##### বর্তমান ডিরেক্টরিতে একটি নতুন লোকাল রিপোজিটরি তৈরি করুন:
```
$ git init
```

##### একটি নির্দিষ্ট ডিরেক্টরিতে একটি নতুন লোকাল রিপোজিটরি তৈরি করুন:
```
$ git init <directory>
```

<hr>

## লোকালি পরিবর্তন করা

##### কাজের ডিরেক্টরিতে পরিবর্তন দেখুন:
```
$ git status
```

##### ট্র্যাক করা ফাইলে পরিবর্তন দেখুন:
```
$ git diff
```

##### একটি নির্দিষ্ট ফাইলের পরিবর্তন বা পার্থক্য দেখুন:
```
$ git diff <file>
```

##### পরবর্তী কমিটে সমস্ত পরিবর্তনগুলো যোগ করুন:
```
$ git add .
```

##### &lt;file&gt; এর পরিবর্তনগুলো পরবর্তী কমিটে যোগ করুন:
```
$ git add -p <file>
```

##### পরবর্তী কমিটে শুধুমাত্র উল্লিখিত ফাইলগুলো যোগ করুন:
```
$ git add <filename1> <filename2>
```

##### ট্র্যাক করা ফাইলগুলিতে সমস্ত লোকাল পরিবর্তনগুলি কমিট করুন:
```
$ git commit -a
```

##### পূর্বে স্টেজ পরিবর্তনগুলো কমিট করুন:
```
$ git commit
```

##### মেসেজ দিয়ে কমিট করুন:
```
$ git commit -m 'message here'
```

##### স্টেজিং এরিয়া এড়িয়ে যাওয়া এবং মেসেজ যোগ করার কমিট করুন:
```
$ git commit -am 'message here'
```

##### কিছু পূর্ববর্তী তারিখ কমিট করুন:
```
$ git commit --date="`date --date='n day ago'`" -am "<Commit Message Here>"
```

##### শেষ কমিট পরিবর্তন করুন:<br>
<em><sub>প্রকাশিত কমিটটি সংশোধন করবেন না!</sub></em>

```
$ git commit -a --amend
```

##### শেষ কমিট দিয়ে সংশোধন করুন কিন্তু আগের কমিট লগ মেসেজটি ব্যবহার করুন
<em><sub>প্রকাশিত কমিটটি সংশোধন করবেন না!</sub></em>

```shell
$ git commit --amend --no-edit
```

##### শেষ কমিটের তারিখ পরিবর্তন করুন:
```
GIT_COMMITTER_DATE="date" git commit --amend
```

##### শেষ কমিটের অথর ডেট পরিবর্তন করুন:
```shell
$ git commit --amend --date="date"
```

##### বর্তমান শাখা থেকে অন্য কোন শাখায় অপ্রত্যাশিত পরিবর্তনগুলি সড়ান:<br>
```
$ git stash
$ git checkout branch2
$ git stash pop
```

##### লুকিয়ে রাখা বা স্ট্যাশ করা পরিবর্তনগুলিকে বর্তমান শাখায় ফিরিয়ে আনুন:
```shell
$ git stash apply
```

#### বর্তমান শাখায় নির্দিষ্ট স্ট্যাশ পুনরুদ্ধার করুন বা ফিরিয়ে আনুন:
- `git stash list` থেকে *{stash_number}* পাওয়া যাবে

```shell
$ git stash apply stash@{stash_number}
```

##### স্ট্যাশে রাখা পরিবর্তনের শেষ সেটটি সড়ান:
```
$ git stash drop
```

<hr>

## অনুসন্ধান

##### A text search on all files in the directory:
```
$ git grep "Hello"
```

##### In any version of a text search:
```
$ git grep "Hello" v2.5
```

##### Show commits that introduced a specific keyword
```
$ git log -S 'keyword'
```

##### Show commits that introduced a specific keyword (using a regular expression)
```
$ git log -S 'keyword' --pickaxe-regex
```

<hr>

## কমিট ইতিহাস

##### Show all commits, starting with newest (it'll show the hash, author information, date of commit and title of the commit):
```
$ git log
```

##### Show all the commits(it'll show just the commit hash and the commit message):
```
$ git log --oneline
```

##### Show all commits of a specific user:
```
$ git log --author="username"
```

##### Show changes over time for a specific file:
```
$ git log -p <file>
```

##### Display commits that are present only in remote/branch in right side
```
$ git log --oneline <origin/master>..<remote/master> --left-right
```

##### Who changed, what and when in &lt;file&gt;:
```
$ git blame <file>
```

##### Show Reference log:
```
$ git reflog show
```

##### Delete Reference log:
```
$ git reflog delete
```
<hr>

## সড়ানো বা নাম পরিবর্তন

##### Rename a file:

Rename Index.txt to Index.html

```
$ git mv Index.txt Index.html
```

<hr>

## ব্রাঞ্চ এবং ট্যাগ

##### List all local branches:
```
$ git branch
```

#### List local/remote branches
```
$ git branch -a
```

##### List all remote branches:
```
$ git branch -r
```

##### Switch HEAD branch:
```
$ git checkout <branch>
```

##### Checkout single file from different branch
```
$ git checkout <branch> -- <filename>
```

##### Create and switch new branch:
```
$ git checkout -b <branch>
```

##### Switch to the previous branch, without saying the name explicitly:
```
$ git checkout -
```

##### Create a new branch from an exiting branch and switch to new branch:
```
$ git checkout -b <new_branch> <existing_branch>
```


#### Checkout and create a new branch from existing commit
```
$ git checkout <commit-hash> -b <new_branch_name>
```


##### Create a new branch based on your current HEAD:
```
$ git branch <new-branch>
```

##### Create a new tracking branch based on a remote branch:
```
$ git branch --track <new-branch> <remote-branch>
```

##### Delete a local branch:
```
$ git branch -d <branch>
```

##### Rename current branch to new branch name
```shell
$ git branch -m <new_branch_name>
```

##### Force delete a local branch:
<em><sub>You will lose unmerged changes!</sub></em>

```
$ git branch -D <branch>
```

##### Mark `HEAD` with a tag:
```
$ git tag <tag-name>
```

##### Mark `HEAD` with a tag and open the editor to include a message:
```
$ git tag -a <tag-name>
```

##### Mark `HEAD` with a tag that includes a message:
```
$ git tag <tag-name> -am 'message here'
```

##### List all tags:
```
$ git tag
```

##### List all tags with their messages (tag message or commit message if tag has no message):
```
$ git tag -n
```

<hr>

## আপডেট এবং প্রকাশ

##### List all current configured remotes:
```
$ git remote -v
```

##### Show information about a remote:
```
$ git remote show <remote>
```

##### Add new remote repository, named &lt;remote&gt;:
```
$ git remote add <remote> <url>
```

##### Rename a remote repository, from &lt;remote&gt; to &lt;new_remote&gt;:
```
$ git remote rename <remote> <new_remote>
```

##### Remove a remote:
```
$ git remote rm <remote>
```

<em><sub>Note: git remote rm does not delete the remote repository from the server. It simply removes the remote and its references from your local repository.</sub></em>

##### Download all changes from &lt;remote&gt;, but don't integrate into HEAD:
```
$ git fetch <remote>
```

##### Download changes and directly merge/integrate into HEAD:
```
$ git remote pull <remote> <url>
```

##### Get all changes from HEAD to local repository:
```
$ git pull origin master
```

##### Get all changes from HEAD to local repository without a merge:
```
$ git pull --rebase <remote> <branch>
```

##### Publish local changes on a remote:
```
$ git push <remote> <branch>
```

##### Delete a branch on the remote:
```
$ git push <remote> :<branch> (since Git v1.5.0)
```
OR
```
$ git push <remote> --delete <branch> (since Git v1.7.0)
```

##### Publish your tags:
```
$ git push --tags
```
<hr>

#### Configure the merge tool globally to meld (editor)
```bash
$ git config --global merge.tool meld
```

##### Use your configured merge tool to solve conflicts:
```
$ git mergetool
```

## মার্জ এবং রিবেস

##### Merge branch into your current HEAD:
```
$ git merge <branch>
```

#### List merged branches
```
$ git branch --merged
```

##### Rebase your current HEAD onto &lt;branch&gt;:<br>
<em><sub>Don't rebase published commit!</sub></em>

```
$ git rebase <branch>
```

##### Abort a rebase:
```
$ git rebase --abort
```

##### Continue a rebase after resolving conflicts:
```
$ git rebase --continue
```

##### Use your editor to manually solve conflicts and (after resolving) mark file as resolved:
```
$ git add <resolved-file>
```

```
$ git rm <resolved-file>
```

##### Squashing commits:
```
$ git rebase -i <commit-just-before-first>
```

Now replace this,

```
pick <commit_id>
pick <commit_id2>
pick <commit_id3>
```

to this,

```
pick <commit_id>
squash <commit_id2>
squash <commit_id3>
```
<hr>

## আনডো

##### Discard all local changes in your working directory:
```
$ git reset --hard HEAD
```

##### Get all the files out of the staging area(i.e. undo the last `git add`):
```
$ git reset HEAD
```

##### Discard local changes in a specific file:
```
$ git checkout HEAD <file>
```

##### Revert a commit (by producing a new commit with contrary changes):
```
$ git revert <commit>
```

##### Reset your HEAD pointer to a previous commit and discard all changes since then:
```
$ git reset --hard <commit>
```

##### Reset your HEAD pointer to a remote branch current state.
```
$ git reset --hard <remote/branch> e.g., upstream/master, origin/my-feature
```

##### Reset your HEAD pointer to a previous commit and preserve all changes as unstaged changes:
```
$ git reset <commit>
```

##### Reset your HEAD pointer to a previous commit and preserve uncommitted local changes:
```
$ git reset --keep <commit>
```

##### Remove files that were accidentally committed before they were added to .gitignore
```
$ git rm -r --cached .
$ git add .
$ git commit -m "remove xyz file"
```
<hr>

## গিট ফ্লো
Improved [Git-flow](https://github.com/petervanderdoes/gitflow-avh)

### Index
* [Setup](#setup)
* [Getting Started](#getting-started)
* [Features](#features)
* [Make a Release](#make-a-release)
* [Hotfixes](#hotfixes)
* [Commands](#commands)

<hr>

### Setup
###### You need a working git installation as prerequisite. Git flow works on OSX, Linux and Windows.

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
###### You need wget and util-linux to install git-flow.
```bash
$ wget -q -O - --no-check-certificate https://raw.githubusercontent.com/petervanderdoes/gitflow/develop/contrib/gitflow-installer.sh install <state> | bash
```
<hr>

### Getting Started
###### Git flow needs to be initialized in order to customize your project setup. Start using git-flow by initializing it inside an existing git repository:
##### Initialize:
###### You'll have to answer a few questions regarding the naming conventions for your branches. It's recommended to use the default values.
```shell
git flow init
```
OR
###### To use default
```shell
git flow init -d
```
<hr>

### Features
###### Develop new features for upcoming releases. Typically exist in developers repos only.
##### Start a new feature:
###### This action creates a new feature branch based on 'develop' and switches to it.
```
git flow feature start MYFEATURE
```

##### Finish up a feature:
###### Finish the development of a feature. This action performs the following:
###### 1) Merged MYFEATURE into 'develop'.
###### 2) Removes the feature branch.
###### 3) Switches back to 'develop' branch
```
git flow feature finish MYFEATURE
```

##### Publish a feature:
###### Are you developing a feature in collaboration? Publish a feature to the remote server so it can be used by other users.
```
git flow feature publish MYFEATURE
```

##### Getting a published feature:
###### Get a feature published by another user.
```
git flow feature pull origin MYFEATURE
```

##### Tracking a origin feature:
###### You can track a feature on origin by using
```
git flow feature track MYFEATURE
```
<hr>

### Make a Release
###### Support preparation of a new production release. Allow for minor bug fixes and preparing meta-data for a release

##### Start a release:
###### To start a release, use the git flow release command. It creates a release branch created from the 'develop' branch. You can optionally supply a [BASE] commit sha-1 hash to start the release from. The commit must be on the 'develop' branch.
```
git flow release start RELEASE [BASE]
```
###### It's wise to publish the release branch after creating it to allow release commits by other developers. Do it similar to feature publishing with the command:
```
git flow release publish RELEASE
```
###### (You can track a remote release with the: ```git flow release track RELEASE``` command)

##### Finish up a release:
###### Finishing a release is one of the big steps in git branching. It performs several actions:
###### 1) Merges the release branch back into 'master'
###### 2) Tags the release with its name
###### 3) Back-merges the release into 'develop'
###### 4) Removes the release branch
```
git flow release finish RELEASE
```
###### Don't forget to push your tags with ```git push --tags```

<hr>

### Hotfixes
###### Hotfixes arise from the necessity to act immediately upon an undesired state of a live production version. May be branched off from the corresponding tag on the master branch that marks the production version.

##### Git flow hotfix start:
###### Like the other git flow commands, a hotfix is started with
```
$ git flow hotfix start VERSION [BASENAME]
```
###### The version argument hereby marks the new hotfix release name. Optionally you can specify a basename to start from.

##### Finish a hotfix:
###### By finishing a hotfix it gets merged back into develop and master. Additionally the master merge is tagged with the hotfix version
```
git flow hotfix finish VERSION
```
<hr>

### Commands
<p align="center">
    <img alt="Git" src="./Img/git-flow-commands.png" height="270" width="460">
</p>
<hr>

### Git flow schema

<p align="center">
    <img alt="Git" src="Img/git-flow-commands-without-flow.png">
</p>
<hr>

