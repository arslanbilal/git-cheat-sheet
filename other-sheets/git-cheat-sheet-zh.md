Git and Git Flow Cheat Sheet [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)
===============
<hr>
<p align="center">
	<img alt="Git" src="../Img/git-logo.png" height="190" width="455">
</p>

Git cheat sheet 让你不用再去记所有的 git 命令。

欢迎贡献内容、更新语法错误，也欢迎添加你母语版本的 Git cheat sheet。

---------------------

Git Cheat Sheet 中文版
===============
### 索引
* [配置](#配置)
* [配置文件](#配置文件)
* [创建](#创建)
* [本地修改](#本地修改)
* [搜索](#搜索)
* [提交历史](#提交历史)
* [移动/重命名](#移动--重命名)
* [分支与标签](#分支与标签)
* [更新与发布](#更新与发布)
* [合并与重置](#合并与重置)
* [撤销](#撤销)
* [Git Flow](#git-flow)

---

### 配置

##### 列出当前配置：
```
$ git config --list
```

##### 列出 repository 配置：
```
$ git config --local --list
```

##### 列出全局配置：
```
$ git config --global --list
```

##### 列出系统配置：
```
$ git config --system --list
```

##### 设置用户名：
```
$ git config --global user.name "[firstname lastname]"
```

##### 设置用户邮箱：
```
$ git config --global user.email "[valid-email]"
```

##### 设置 git 命令行输出为彩色：
```
$ git config --global color.ui auto
```

##### 设置 git 使用的文本编辑器：
```
$ git config --global core.editor vi
```

---

### 配置文件

##### Repository 配置对应的配置文件路径 [--local]：
```
<repo>/.git/config
```

##### 用户全局配置对应的配置文件路径 [--global]：
```
~/.gitconfig
```

##### 系统配置对应的配置文件路径 [--system]：
```
/etc/gitconfig
```

----------

### 创建

##### 复制一个已创建的仓库：
```bash
# 通过 SSH
$ git clone ssh://user@domain.com/repo.git

# 通过 HTTP
$ git clone http://domain.com/user/repo.git
```

##### 在当前目录创建一个新的本地仓库：
```
$ git init
```

##### 在指定目录创建一个新的本地仓库：
```
$ git init <directory>
```

---

### 本地修改

##### 显示工作路径下已修改的文件：
```
$ git status
```

##### 显示提交文件的变化：
```
$ git diff
```

##### 显示指定文件的变化：
```
$ git diff <file>
```

##### 把当前所有修改添加到下次提交中：
```
$ git add .
```

##### 把对某个文件的修改添加到下次提交中：
```
$ git add -p <file>
```

##### 把指定文件的修改添加到下次提交中：
```
$ git add <filename1> <filename2>
```

##### 提交本地的所有修改：
```
$ git commit -a
```

##### 提交之前已标记的变化：
```
$ git commit
```

##### 附加消息提交：
```
$ git commit -m 'message here'
```

##### 提交，并将提交时间设置为之前的某个日期：
```
$ git commit --date="`date --date='n day ago'`" -am "Commit Message"
```

##### 修改上次提交
<em><sub>请勿修改已发布的提交记录！</sub></em>

```
$ git commit --amend
```

##### 修改上次提交的 committer date：
```
GIT_COMMITTER_DATE="date" git commit --amend
```

##### 修改上次提交的 author date：
```
$ git commit --amend --date="date"
```

##### 把当前分支中未提交的修改移动到其他分支：
```
$ git stash
$ git checkout branch2
$ git stash pop
```

##### 将缓存的变化应用到当前分支：
```
$ git stash apply
```

##### 删除缓存的变化：
```
$ git stash drop
```

---

### 搜索

##### 从当前目录的所有文件中查找文本内容：
```
$ git grep "Hello"
```

##### 在某一版本中搜索文本：
```
$ git grep "Hello" v2.5
```

##### 显示引入了特定关键字的提交：
```
$ git log -S 'keyword'
```

##### 显示引入了特定关键字的提交（使用正则表达式）：
```
$ git log -S 'keyword' --pickaxe-regex
```

---

### 提交历史

##### 从最新提交开始，显示所有的提交记录（显示 hash，作者信息，提交的标题和时间）：
```
$ git log
```

##### 显示所有提交（仅显示提交的 hash 和 message）：
```
$ git log --oneline
```

##### 显示某个用户的所有提交：
```
$ git log --author="username"
```

##### 显示某个文件的所有修改：
```
$ git log -p <file>
```

##### 显示远程 <remote/master> 分支与远程 <origin/master> 分支提交记录的差集：
```
$ git log --oneline <origin/master>..<remote/master> --left-right
```

##### 谁，在什么时间，修改了文件的什么内容：
```
$ git blame <file>
```

##### 显示 reflog：
```
$ git reflog show 
```

##### 删除 reflog：
```
$ git reflog delete
```

---

### 移动 / 重命名

##### 重命名文件：

将 Index.txt 重命名为 Index.html

```
$ git mv Index.txt Index.html
```

---

### 分支与标签

##### 列出所有的本地分支：
```
$ git branch
```

##### 列出所有的本地/远程分支：
```
$ git branch -a
```

##### 列出所有的远程分支：
```
$ git branch -r
```

##### 切换分支：
```
$ git checkout <branch>
```

##### 从不同的分支单个文件：
```
$ git checkout <branch> -- <filename>
```

##### 创建并切换到新分支：
```
$ git checkout -b <branch>
```

##### 切换到之前的分支：
```
$ git checkout -
```

##### 从现有的分支创建一个新的分支，并切换到新的分支：
```
$ git checkout -b <new_branch> <existing_branch>
```

##### 从现有的提交创建一个新的分支，并切换到新的分支：
```
$ git checkout <commit-hash> -b <new_branch_name>
```

##### 基于当前分支创建新分支：
```
$ git branch <new-branch>
```

##### 基于远程分支创建新的可追溯的分支：
```
$ git branch --track <new-branch> <remote-branch>
```

##### 删除本地分支：
```
$ git branch -d <branch>
```

##### 强制删除一个本地分支：
<em><sub>将会丢失未合并的修改！</sub></em>

```
$ git branch -D <branch>
```

##### 给当前分支打标签：
```
$ git tag <tag-name>
```

##### 给当前分支打标签并打开编辑器附加消息：
```
$ git tag -a <tag-name>
```

##### 给当前分支打标签并附加消息：
```
$ git tag <tag-name> -am 'message here'
```

##### 列出所有标签：
```
$ git tag
```

##### 列出所有标签及其附加信息（标签信息或提交信息）：
```
$ git tag -n
```

---

### 更新与发布

##### 列出当前配置的远程仓库：
```
$ git remote -v
```

##### 显示远程仓库的信息：
```
$ git remote show <remote>
```

##### 添加新的远程仓库，命名为 <remote>：
```
$ git remote add <remote> <url>
```

##### 重命名远程仓库，<remote> 修改为 <new_remote>：
```
$ git remote rename <remote> <new_remote>
```

##### 删除远程：
```
$ git remote rm <remote>
```

<em><sub>注意：git remote rm 不会从服务器上删除远程仓库。它只是从本地仓库中删除远程文件及其引用。</sub></em>

##### 从远程仓库下载所有修改，但不合并到 HEAD 中：
```
$ git fetch <remote>
```

##### 从远程仓库下载所有修改，并自动与 HEAD 合并：
```
$ git remote pull <remote> <url>
```

##### 将合并到本地仓库中：
```
$ git pull origin master
```

##### 以 rebase 方式将远程分支与本地合并：
```
git pull --rebase <remote> <branch>
```

##### 将本地修改发布到远程仓库：
```
$ git push remote <remote> <branch>
```

##### 删除远程分支：
```
$ git push <remote> :<branch> (since Git v1.5.0)
```
或
```
$ git push <remote> --delete <branch> (since Git v1.7.0)
```

##### 发布标签：
```
$ git push --tags
```

---

### 合并与重置

##### 将分支合并到当前 HEAD 中：
```
$ git merge <branch>
```

##### 列出合并的分支：
```
$ git branch --merged
```

##### 将当前 HEAD 版本重置到分支中：
<em><sub>请勿重置已发布的提交！</sub></em>
```
$ git rebase <branch>
```

##### 终止重置：
```
$ git rebase --abort
```

##### 解决冲突后继续重置：
```
$ git rebase --continue
```

##### 将合并工具全局配置为 meld（编辑器）：
```bash
$ git config --global merge.tool meld
```

##### 使用配置好的 merge tool 解决冲突：
```
$ git mergetool
```

##### 在编辑器中手动解决冲突后，将文件标记为已解决冲突：
```
$ git add <resolved-file>
```

```
$ git rm <resolved-file>
```

##### 合并提交：
```
$ git rebase -i <commit-just-before-first>
```

把下面的内容：

```
pick <commit_id>
pick <commit_id2>
pick <commit_id3>
```

替换为：
```
pick <commit_id>
squash <commit_id2>
squash <commit_id3>
```

---

### 撤销

##### 放弃工作目录下的所有修改：
```
$ git reset --hard HEAD
```

##### 移除缓存区的所有文件（即，撤销上次 `git add`）：
```
$ git reset HEAD
```

##### 放弃某个文件的所有本地修改：
```
$ git checkout HEAD <file>
```

##### 重置一个提交（通过创建一个截然不同的新提交）：
```
$ git revert <commit>
```

##### 将 HEAD 重置到指定的版本，并放弃该版本之后的所有修改：
```
$ git reset --hard <commit>
```

##### 用远程分支强制覆盖本地分支：
```
git reset --hard <remote/branch> e.g., upstream/master, origin/my-feature
```

##### 将 HEAD 重置到上一次提交的版本，并将之后的修改标记为未添加到缓存区：
```
$ git reset <commit>
```

##### 将 HEAD 重置到上一次提交的版本，并保留未提交的本地修改：
```
$ git reset --keep <commit>
```

##### 删除添加 `.gitignore` 文件前错误提交的文件：
```
$ git rm -r --cached .
$ git add .
$ git commit -m "remove xyz file"
```

---

## Git-Flow

### 索引
* [安装](#安装)
* [开始](#开始)
* [特性](#特性)
* [制作 release 版本](#制作-release-版本)
* [热修复](#热修复)
* [命令](#命令)

---

### 安装

- 你需要有一个可以工作的 git 作为前提。
- Git flow 可以工作在 OSX，Linux 和 Windows 之下。

##### OSX Homebrew

```
$ brew install git-flow
```

##### OSX Macports

```
$ port install git-flow
```

##### Linux

```
$ apt-get install git-flow
```

##### Windows (Cygwin)

安装 git-flow，你需要 wget 和 util-linux。

```
$ wget -q -O - --no-check-certificate https://github.com/nvie/gitflow/raw/develop/contrib/gitflow-installer.sh | bash
```

----

### 开始

- 为了自定义你的项目，Git flow 需要初始化。
- 使用 git-flow，从初始化一个现有的 git 库内开始。
- 初始化，你必须回答几个关于分支的命名约定的问题。建议使用默认值。

```
git flow init
```

---

### 特性

- 为即将发布的版本开发新功能特性。
- 这通常只存在于开发者的仓库中。

##### 创建一个新特性

下面操作创建了一个基于 'develop' 的新特性分支，并切换到该分支。

```
git flow feature start MYFEATURE
```

##### 完成新特性的开发

完成开发新特性。这个动作执行以下操作：
1. 将 MYFEATURE 分支合并到 'develop'
2. 删除这个新特性分支
3. 切换回 'develop' 分支

```
git flow feature finish MYFEATURE
```

##### 发布新特性

- 你是否合作开发一项新特性？
- 发布新特性分支到远程服务器，以便其它用户使用该分支。

```
git flow feature publish MYFEATURE
```

##### 获取发布的新特性分支

获取由其它用户发布的新特性分支。

```
git flow feature pull origin MYFEATURE
```

##### 追溯远程上的特性

通过下面的命令追溯远程上的特性

```
git flow feature track MYFEATURE
```

---

### 制作 release 版本

- 支持一个新的用于生产环境的发布版本。
- 允许修复小问题，并为发布版本准备元数据。

##### 开始创建 release 版本

- 使用 git flow release 命令创建 release 版本。 
- 'release' 分支基于 'develop' 分支创建。 
- 你可以选择提供一个 [BASE] 参数，即提交记录的 sha-1 hash 值，来开启 release 分支。
- 这个提交记录的 sha-1 hash 值必须是 'develop' 分支下的。 

```
git flow release start RELEASE [BASE]
```

明智的做法是在创建 release 分支之后立即发布，允许其它用户向这个 release 分支提交内容。使用类似发布新特性的命令：

```
git flow release publish RELEASE
```

(你可以通过 `git flow release track RELEASE` 命令追溯远程的 release 版本)

##### 完成 release 版本

完成 release 版本是一个 git 分支的重要操作之一。它执行以下几个动作：
1. 归并 release 分支到 'master' 分支
2. 用 release 分支名打标签
3. 归并 release 分支到 'develop' 分支
4. 移除 release 分支

```
git flow release finish RELEASE
```

不要忘记使用 `git push --tags` 将标签推送到远程。

---

### 热修复

热修复来自这样的需求：生产环境的版本处于非预期状态时需要立即采取行动。有可能是需要修复 master 分支上某个标记的生产版本。

##### 开始 git flow 热修复

像其它 git flow 命令一样，热修复分支开始自：

```
$ git flow hotfix start VERSION [BASENAME]
```

VERSION 参数标记新的热修复发布名称。你还可以指定从哪个 `[BASENAME]` 开始，`[BASENAME]` 是完成 release 版本时填写的版本号。

##### 完成热修复

当完成热修复，分支代码将被合并到 develop 和 master 分支。相应地，master 分支打上热修复版本的标签。

```
git flow hotfix finish VERSION
```

---

### 命令
<p align="center">
    <img alt="Git" src="../Img/git-flow-commands.png" height="270" width="460">
</p>
<hr>

### Git flow schema

<p align="center">
    <img alt="Git" src="../Img/git-flow-commands-without-flow.png">
</p>
<hr>

