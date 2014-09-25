Git Cheat Sheet Chinese
========================


###Index
* [创建](#创建)
* [本地修改](#本地修改)
* [Commit History](#commit-history)
* [Branches & Tags](#branches--tags)
* [Update & Publish](#update--publish)
* [Merge & Rebase](#merge--rebase)
* [Undo](#undo)

---

###创建

复制一个以创建的仓库:
```
$ git clone ssh://user@domain.com/repo.git
```

创建一个新的本地仓库:
```
$ git init
```

---
###本地修改

显示工作路径下已修改的文件：
```
$ git status
```

显示与上次提交版本文件的不同：
```
$ git diff
```

把当天所有修改添加到下次提交中：
```
$ git add .
```

把对某个文件的修改添加到下次提交中：
```
$ git add -p <file>
```

提交本地的所有修改：
```
$ git commit -a
```

提交之前已标记的变化：
```
$ git commit
```

附加消息提交：
```
$ git commit -m 'message here'
```

修改上次提交<br/>
<em><sub>Don't amend published commits!</sub></em>
```
$ git commit --amend
```

---
###提交历史

从最新提交开始，显示所有的提交记录（显示hash， 作者信息，提交的标题和时间）：
```
$ git log
```

显示所有提交（仅显示提交的hash和message）：
```
$ git log --oneline
```

显示某个用户的所有提交：
```
$ git log --author="username"
```

显示某个文件的所有修改：
```
$ git log -p <file>
```

谁，在什么时间，修改了文件的什么内容：
```
$ git blame <file>
```

---
###分支和标签

列出所有的分支：
```
$ git branch
```

切换分支：
```
$ git checkout <branch>
```

基于当前分支创建新分支：
```
$ git branch <new-branch>
```

基于远程分支创建新的可追溯的分支：
```
$ git branch --track <new-branch> <remote-branch>
```

删除本地分支:
```
$ git branch -d <branch>
```

给当前版本打标签：
```
$ git tag <tag-name>
```

---
###更新和发布

列出对当前远程端的操作：
```
$ git remote -v
```

显示远程端的信息：
```
$ git remote show <remote>
```

添加新的远程端：
```
$ git remote add <remote> <url>
```

下载远程端版本，但不合并到HEAD中：
```
$ git fetch <remote>
```

下载远程端版本，并自动与HEAD版本合并：
```
$ git remote pull <remote> <url>
```

将远程端版本合并到本地版本中：
```
$ git pull origin master
```

将本地版本发布到远程端：
```
$ git push remote <remote> <branch>
```

删除远程端分支：
```
$ git push <remote> :<branch> (since Git v1.5.0)
or
git push <remote> --delete <branch> (since Git v1.7.0)
```

发布标签:
```
$ git push --tags
```

---
###Merge & Rebase

Merge <branch> into your current HEAD:
```
$ git merge <branch>
```

Rebase your current HEAD onto &lt;branch&gt;:<br>
<em><sub>Don't rebase published commit!</sub></em>
```
$ git rebase <branch>
```

Abort a rebase:
```
$ git rebase --abort
```

Continue a rebase after resolving conflicts:
```
$ git rebase --continue
```

Use your configured merge tool to solve conflicts:
```
$ git mergetool
```

Use your editor to manully solve conflicts and (after resolving) mark file as resolved:
```
$ git add <resolved-file>
```
```
$ git rm <resolved-file>
```

---
###Undo

Discard all local changes in your working directory:
```
$ git reset --hard HEAD
```

Get all the files out of the staging area (i.e. undo the last `git add`)
```
$ git reset HEAD
```

Discard local changes in a specific file:
```
$ git checkout HEAD <file>
```

Revert a commit (by producing a new commit with contrary changes):
```
$ git revert <commit>
```

Reset your HEAD pointer to a previous commit and discard all changes since then:
```
$ git reset --hard <commit>
```

Reset your HEAD pointer to a previous commit and preserve all changes as unstaged changes:
```
$ git reset <commit>
```

Reset your HEAD pointer to a previous commit and preserve uncommitted local changes:
```
$ git reset --keep <commit>
```

---
