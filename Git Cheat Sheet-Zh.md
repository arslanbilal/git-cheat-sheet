Git Cheat Sheet Chinese
========================


###索引
* [创建](#创建)
* [本地修改](#本地修改)
* [搜索](#搜索)
* [提交历史](#提交历史)
* [分支与标签](#分支与标签)
* [更新与发布](#更新与发布)
* [合并与重置](#合并与重置)
* [撤销](#撤销)
* [Git Flow](#git-flow)

---

###创建

复制一个已创建的仓库:
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

把当前所有修改添加到下次提交中：
```
$ git add 
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

提交，并将提交时间设置为之前的某个日期:
```
git commit --date="`date --date='n day ago'`" -am "Commit Message"
```

修改上次提交<br/>
<em><sub>请勿修改已发布的提交记录!</sub></em>
```
$ git commit --amend
```

把当前分支中未提交的修改移动到其他分支
```
git stash
git checkout branch2
git stash pop
```

---
###搜索

从当前目录的所有文件中查找文本内容：
```
$ git grep "Hello"
```

在某一版本中搜索文本：
```
$ git grep "Hello" v2.5
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
###分支与标签

列出所有的分支：
```
$ git branch
```

切换分支：
```
$ git checkout <branch>
```

创建并切换到新分支:
```
$ git checkout -b <branch>
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
###更新与发布

列出当前配置的远程端：
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
###合并与重置

将分支合并到当前HEAD中：
```
$ git merge <branch>
```

将当前HEAD版本重置到分支中:<br>
<em><sub>请勿重置已发布的提交!</sub></em>
```
$ git rebase <branch>
```

退出重置:
```
$ git rebase --abort
```

解决冲突后继续重置：
```
$ git rebase --continue
```

使用配置好的merge tool 解决冲突：
```
$ git mergetool
```

在编辑器中手动解决冲突后，标记文件为`已解决冲突`
```
$ git add <resolved-file>
```
```
$ git rm <resolved-file>
```

---
###撤销

放弃工作目录下的所有修改：
```
$ git reset --hard HEAD
```

移除缓存区的所有文件（i.e. 撤销上次`git add`）:
```
$ git reset HEAD
```

放弃某个文件的所有本地修改：
```
$ git checkout HEAD <file>
```

重置一个提交（通过创建一个截然不同的新提交）
```
$ git revert <commit>
```

将HEAD重置到指定的版本，并抛弃该版本之后的所有修改：
```
$ git reset --hard <commit>
```

将HEAD重置到上一次提交的版本，并将之后的修改标记为未添加到缓存区的修改：
```
$ git reset <commit>
```

将HEAD重置到上一次提交的版本，并保留未提交的本地修改：
```
$ git reset --keep <commit>
```

---

##Git-Flow

###索引
* [Setup](#setup)
* [Getting Started](#getting-started)
* [Features](#features)
* [Make a Release](#make-a-release)
* [Hotfixes](#hotfixes)
* [Commands](#commands)
<hr>

###Setup
######You need a working git installation as prerequisite. Git flow works on OSX, Linux and Windows.

#####OSX Homebrew:
```
$ git clone ssh://user@domain.com/repo.git
```

#####OSX Macports:
```
$ port install git-flow
```

#####Linux:
```
$ apt-get install git-flow
```

#####Windows (Cygwin):
######You need wget and util-linux to install git-flow.
```
$ wget -q -O - --no-check-certificate https://github.com/nvie/gitflow/raw/develop/contrib/gitflow-installer.sh | bash
```
<hr>


###Getting Started
######Git flow needs to be initialized in order to customize your project setup. Start using git-flow by initializing it inside an existing git repository:
#####Initialize:
######You'll have to answer a few questions regarding the naming conventions for your branches. It's recommended to use the default values.
```
git flow init
```
<hr>


###Features
######Develop new features for upcoming releases. Typically exist in developers repos only.
#####Start a new feature:
######This action creates a new feature branch based on 'develop' and switches to it.
```
git flow feature start MYFEATURE
```

#####Finish up a feature:
######Finish the development of a feature. This action performs the following:
######1)Merged MYFEATURE into 'develop'.
######2)Removes the feature branch.
######3)Switches back to 'develop' branch
```
git flow feature finish MYFEATURE
```

#####Publish a feature:
######Are you developing a feature in collaboration? Publish a feature to the remote server so it can be used by other users.
```
git flow feature publish MYFEATURE
```

#####Getting a published feature:
######Get a feature published by another user.
```
git flow feature pull origin MYFEATURE
```

#####Tracking a origin feature:
######You can track a feature on origin by using
```
git flow feature track MYFEATURE
```
<hr>


###Make a Release
######Support preparation of a new production release. Allow for minor bug fixes and preparing meta-data for a release

#####Start a release:
######To start a release, use the git flow release command. It creates a release branch created from the 'develop' branch. You can optionally supply a [BASE] commit sha-1 hash to start the release from. The commit must be on the 'develop' branch.
```
git flow release start RELEASE [BASE]
```
######It's wise to publish the release branch after creating it to allow release commits by other developers. Do it similar to feature publishing with the command:
```
git flow release publish RELEASE
```
######(You can track a remote release with the: ```git flow release track RELEASE``` command)

#####Finish up a release:
######Finishing a release is one of the big steps in git branching. It performs several actions:
######1)Merges the release branch back into 'master'
######2)Tags the release with its name
######3)Back-merges the release into 'develop'
######4)Removes the release branch
```
git flow release finish RELEASE
```
######Don't forget to push your tags with ```git push --tags```
<hr>


###Hotfixes
######Hotfixes arise from the necessity to act immediately upon an undesired state of a live production version. May be branched off from the corresponding tag on the master branch that marks the production version.

#####Git flow hotfix start:
######Like the other git flow commands, a hotfix is started with
```
$ git flow hotfix start VERSION [BASENAME]
```
######The version argument hereby marks the new hotfix release name. Optionally you can specify a basename to start from.

#####Finish a hotfix:
######By finishing a hotfix it gets merged back into develop and master. Additionally the master merge is tagged with the hotfix version
```
git flow hotfix finish VERSION
```
<hr>


###Commands
<p align="center">
    <img alt="Git" src="./Img/git-flow-commands.png" height="270" width="460">
</p>
<hr>
