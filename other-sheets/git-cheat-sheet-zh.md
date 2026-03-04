# Git Cheat Sheet 中文

![Git Logo](../Img/git-logo.png)

---

## 📖 关于

这个全面的Git速查表帮助您掌握Git命令而无需记住所有内容。无论您是初学者还是经验丰富的开发者，本指南都为基本的Git操作提供快速参考。

**欢迎贡献！** 请随意：
- 修正语法错误
- 添加新命令
- 翻译成您的语言
- 改进说明

---

## 📋 目录

- [🔧 设置](#-设置)
- [⚙️ 配置文件](#️-配置文件)
- [🆕 创建仓库](#-创建仓库)
- [📝 本地更改](#-本地更改)
- [🔍 搜索](#-搜索)
- [📖 提交历史](#-提交历史)
- [📁 移动 / 重命名](#-移动--重命名)
- [🌿 分支和标签](#-分支和标签)
- [🔄 更新和发布](#-更新和发布)
- [🔀 合并和变基](#-合并和变基)
- [↩️ 撤销](#️-撤销)
- [🌊 Git Flow](#-git-flow)
- [🌍 其他语言](#-其他语言)

---

## 🔧 设置

### 查看配置

**显示当前配置：**
```bash
git config --list
```

**显示仓库配置：**
```bash
git config --local --list
```

**显示全局配置：**
```bash
git config --global --list
```

**显示系统配置：**
```bash
git config --system --list
```

### 用户配置

**设置版本历史的姓名：**
```bash
git config --global user.name "[姓名]"
```

**设置电子邮件地址：**
```bash
git config --global user.email "[有效邮箱]"
```

### 显示和编辑器设置

**启用自动命令行着色：**
```bash
git config --global color.ui auto
```

**设置全局提交编辑器：**
```bash
git config --global core.editor vi
```

---

## ⚙️ 配置文件

| 范围 | 位置 | 命令标志 |
|------|------|----------|
| **仓库** | `<repo>/.git/config` | `--local` |
| **用户** | `~/.gitconfig` | `--global` |
| **系统** | `/etc/gitconfig` | `--system` |

---

## 🆕 创建仓库

### 克隆现有仓库

**通过SSH：**
```bash
git clone ssh://用户@域名.com/repo.git
```

**通过HTTPS：**
```bash
git clone https://域名.com/用户/repo.git
```

### 初始化新仓库

**在当前目录创建仓库：**
```bash
git init
```

**在指定目录创建仓库：**
```bash
git init <目录>
```

---

## 📝 本地更改

### 检查状态和差异

**查看工作目录状态：**
```bash
git status
```

**显示跟踪文件的更改：**
```bash
git diff
```

**显示特定文件的更改：**
```bash
git diff <文件>
```

### 暂存更改

**添加所有当前更改：**
```bash
git add .
```

**添加特定文件：**
```bash
git add <文件1> <文件2>
```

**交互式添加文件的部分内容：**
```bash
git add -p <文件>
```

### 提交更改

**提交所有跟踪文件的更改：**
```bash
git commit -a
```

**提交暂存的更改：**
```bash
git commit
```

**带消息提交：**
```bash
git commit -m '这里是消息'
```

**跳过暂存并带消息提交：**
```bash
git commit -am '这里是消息'
```

**以特定日期提交：**
```bash
git commit --date="`date --date='n day ago'`" -am "<提交消息>"
```

### 修改最后一次提交

> ⚠️ **警告：** 不要修改已发布的提交！

**修正最后一次提交：**
```bash
git commit -a --amend
```

**修正而不更改提交消息：**
```bash
git commit --amend --no-edit
```

**更改提交者日期：**
```bash
GIT_COMMITTER_DATE="日期" git commit --amend
```

**更改作者日期：**
```bash
git commit --amend --date="日期"
```

### 暂存更改

**临时保存当前更改：**
```bash
git stash
```

**应用最后保存的更改：**
```bash
git stash apply
```

**应用特定的暂存：**
```bash
git stash apply stash@{暂存号}
```
> 使用 `git stash list` 查看可用的暂存

**删除最后一个暂存：**
```bash
git stash drop
```

**将未提交的更改移动到另一个分支：**
```bash
git stash
git checkout 分支2
git stash pop
```

---

## 🔍 搜索

### 文本搜索

**在所有文件中搜索文本：**
```bash
git grep "你好"
```

**在特定版本中搜索：**
```bash
git grep "你好" v2.5
```

### 提交搜索

**查找引入特定关键字的提交：**
```bash
git log -S '关键字'
```

**使用正则表达式搜索：**
```bash
git log -S '关键字' --pickaxe-regex
```

---

## 📖 提交历史

### 基本历史

**显示所有提交（详细）：**
```bash
git log
```

**显示提交（每行一个）：**
```bash
git log --oneline
```

**显示特定作者的提交：**
```bash
git log --author="用户名"
```

**显示特定文件的更改：**
```bash
git log -p <文件>
```

### 高级历史

**比较分支：**
```bash
git log --oneline <origin/master>..<remote/master> --left-right
```

**显示谁何时更改了什么：**
```bash
git blame <文件>
```

### 引用日志

**显示引用日志：**
```bash
git reflog show
```

**删除引用日志：**
```bash
git reflog delete
```

---

## 📁 移动 / 重命名

**重命名文件：**
```bash
git mv Index.txt Index.html
```

---

## 🌿 分支和标签

### 列出分支

**列出本地分支：**
```bash
git branch
```

**列出所有分支（本地+远程）：**
```bash
git branch -a
```

**列出远程分支：**
```bash
git branch -r
```

**列出已合并的分支：**
```bash
git branch --merged
```

### 切换和创建分支

**切换到现有分支：**
```bash
git checkout <分支>
```

**创建并切换到新分支：**
```bash
git checkout -b <分支>
```

**切换到上一个分支：**
```bash
git checkout -
```

**从现有分支创建分支：**
```bash
git checkout -b <新分支> <现有分支>
```

**从特定提交创建分支：**
```bash
git checkout <提交哈希> -b <新分支名>
```

**创建分支但不切换：**
```bash
git branch <新分支>
```

**创建跟踪分支：**
```bash
git branch --track <新分支> <远程分支>
```

### 分支操作

**从不同分支检出单个文件：**
```bash
git checkout <分支> -- <文件名>
```

**应用另一个分支的特定提交：**
```bash
git cherry-pick <提交哈希>
```

**重命名当前分支：**
```bash
git branch -m <新分支名>
```

**删除本地分支：**
```bash
git branch -d <分支>
```

**强制删除本地分支：**
```bash
git branch -D <分支>
```
> ⚠️ **警告：** 您将丢失未合并的更改！

### 标签

**在HEAD创建标签：**
```bash
git tag <标签名>
```

**创建注释标签：**
```bash
git tag -a <标签名>
```

**创建带消息的标签：**
```bash
git tag <标签名> -am '这里是消息'
```

**列出所有标签：**
```bash
git tag
```

**列出带消息的标签：**
```bash
git tag -n
```

---

## 🔄 更新和发布

### 远程管理

**列出配置的远程：**
```bash
git remote -v
```

**显示远程信息：**
```bash
git remote show <远程>
```

**添加新远程：**
```bash
git remote add <远程> <网址>
```

**重命名远程：**
```bash
git remote rename <远程> <新远程>
```

**删除远程：**
```bash
git remote rm <远程>
```
> ℹ️ **注意：** 这只是在本地删除远程引用，不是远程仓库本身。

### 获取和拉取

**下载更改而不合并：**
```bash
git fetch <远程>
```

**下载并合并更改：**
```bash
git pull <远程> <分支>
```

**从主分支获取更改：**
```bash
git pull origin master
```

**使用变基拉取：**
```bash
git pull --rebase <远程> <分支>
```

### 推送和发布

**发布本地更改：**
```bash
git push <远程> <分支>
```

**删除远程分支：**
```bash
# Git v1.7.0+
git push <远程> --delete <分支>

# Git v1.5.0+
git push <远程> :<分支>
```

**发布标签：**
```bash
git push --tags
```

---

## 🔀 合并和变基

### 合并操作

**将分支合并到当前HEAD：**
```bash
git merge <分支>
```

**全局配置合并工具：**
```bash
git config --global merge.tool meld
```

**使用配置的合并工具：**
```bash
git mergetool
```

### 变基操作

> ⚠️ **警告：** 不要变基已发布的提交！

**将当前HEAD变基到分支：**
```bash
git rebase <分支>
```

**中止变基：**
```bash
git rebase --abort
```

**解决冲突后继续变基：**
```bash
git rebase --continue
```

### 冲突解决

**标记文件为已解决：**
```bash
git add <已解决文件>
```

**删除已解决文件：**
```bash
git rm <已解决文件>
```

### 压缩提交

**交互式变基进行压缩：**
```bash
git rebase -i <第一个提交之前的提交>
```

**压缩配置示例：**
```
# 之前
pick <提交id>
pick <提交id2>
pick <提交id3>

# 之后（将提交id2和提交id3压缩到提交id）
pick <提交id>
squash <提交id2>
squash <提交id3>
```

---

## ↩️ 撤销

### 丢弃更改

**丢弃所有本地更改：**
```bash
git reset --hard HEAD
```

**从暂存区移除所有文件：**
```bash
git reset HEAD
```

**丢弃特定文件的更改：**
```bash
git checkout HEAD <文件>
```

### 重置操作

**重置到上一个提交（丢弃所有更改）：**
```bash
git reset --hard <提交>
```

**重置到远程分支状态：**
```bash
git reset --hard <远程/分支>
# 示例：git reset --hard upstream/master
```

**重置保持更改为未暂存：**
```bash
git reset <提交>
```

**重置保持本地未提交更改：**
```bash
git reset --keep <提交>
```

### 还原提交

**还原提交（创建具有相反更改的新提交）：**
```bash
git revert <提交>
```

### 清理忽略的文件

**删除意外提交的应该被忽略的文件：**
```bash
git rm -r --cached .
git add .
git commit -m "删除忽略的文件"
```

---

## 🌊 Git Flow

**改进的Git-flow：** [git-flow-avh](https://github.com/petervanderdoes/gitflow-avh)

### 📋 目录
- [🔧 设置](#设置-1)
- [🚀 开始](#开始)
- [✨ 功能](#功能)
- [🎁 制作发布](#制作发布)
- [🔥 热修复](#热修复)
- [📊 命令概览](#命令概览)

---

### 🔧 设置 {#设置-1}

> **先决条件：** 需要可工作的Git安装。Git-flow可在macOS、Linux和Windows上运行。

**macOS (Homebrew)：**
```bash
brew install git-flow-avh
```

**macOS (MacPorts)：**
```bash
port install git-flow
```

**Linux (基于Debian)：**
```bash
sudo apt-get install git-flow
```

**Windows (Cygwin)：**
> 需要wget和util-linux
```bash
wget -q -O - --no-check-certificate https://raw.githubusercontent.com/petervanderdoes/gitflow/develop/contrib/gitflow-installer.sh install <state> | bash
```

---

### 🚀 开始

Git-flow需要初始化以自定义您的项目设置。

**初始化（交互式）：**
```bash
git flow init
```
> 您将回答关于分支命名约定的问题。建议使用默认值。

**初始化（使用默认值）：**
```bash
git flow init -d
```

---

### ✨ 功能

功能用于开发即将发布的新功能。它们通常只存在于开发者仓库中。

**开始新功能：**
```bash
git flow feature start 我的功能
```
> 基于'develop'创建功能分支并切换到它

**完成功能：**
```bash
git flow feature finish 我的功能
```
> 这将：
> 1. 将我的功能合并到'develop'
> 2. 删除功能分支
> 3. 切换回'develop'

**发布功能（用于协作）：**
```bash
git flow feature publish 我的功能
```

**获取已发布的功能：**
```bash
git flow feature pull origin 我的功能
```

**跟踪源功能：**
```bash
git flow feature track 我的功能
```

---

### 🎁 制作发布

发布支持新生产版本的准备，允许小的错误修复和准备元数据。

**开始发布：**
```bash
git flow release start 发布 [基础]
```
> 从'develop'创建发布分支。可选择指定[基础]提交SHA-1。

**发布版本：**
```bash
git flow release publish 发布
```

**跟踪远程发布：**
```bash
git flow release track 发布
```

**完成发布：**
```bash
git flow release finish 发布
```
> 这将：
> 1. 将发布分支合并到'master'
> 2. 标记发布
> 3. 将发布合并回'develop'
> 4. 删除发布分支

> 💡 **别忘了：** 使用 `git push --tags` 推送您的标签

---

### 🔥 热修复

热修复解决在线生产版本中的关键问题。它们从master上的相应标签分支。

**开始热修复：**
```bash
git flow hotfix start 版本 [基础名称]
```

**完成热修复：**
```bash
git flow hotfix finish 版本
```
> 合并回'develop'和'master'，并标记master合并

---

### 📊 命令概览

<p align="center">
    <img alt="Git Flow命令" src="../Img/git-flow-commands.png" height="270" width="460">
</p>

### 🌊 Git Flow模式

<p align="center">
    <img alt="Git Flow模式" src="../Img/git-flow-commands-without-flow.png">
</p>

---

## 🌍 其他语言

此速查表提供多种语言版本：

| 语言 | 链接 |
|------|------|
| 🇺🇸 英语 | [README.md](../README.md) |
| 🇸🇦 阿拉伯语 | [git-cheat-sheet-ar.md](./git-cheat-sheet-ar.md) |
| 🇧🇩 孟加拉语 | [git-cheat-sheet-bn.md](./git-cheat-sheet-bn.md) |
| 🇧🇷 巴西葡萄牙语 | [git-cheat-sheet-pt_BR.md](./git-cheat-sheet-pt_BR.md) |
| 🇩🇪 德语 | [git-cheat-sheet-de.md](./git-cheat-sheet-de.md) |
| 🇪🇸 西班牙语 | [git-cheat-sheet-es.md](./git-cheat-sheet-es.md) |
| 🇬🇷 希腊语 | [git-cheat-sheet-el.md](./git-cheat-sheet-el.md) |
| 🇮🇳 印地语 | [git-cheat-sheet-hi.md](./git-cheat-sheet-hi.md) |
| 🇰🇷 韩语 | [git-cheat-sheet-ko.md](./git-cheat-sheet-ko.md) |
| 🇵🇱 波兰语 | [git-cheat-sheet-pl.md](./git-cheat-sheet-pl.md) |
| 🇹🇷 土耳其语 | [git-cheat-sheet-tr.md](./git-cheat-sheet-tr.md) |
| 🇨🇳 **中文** | **当前** |

---

## 🤝 贡献

我们欢迎贡献！您可以：

- 🐛 报告错误或拼写错误
- ✨ 添加新的Git命令
- 🌍 翻译成新语言
- 💡 改进说明
- 📝 增强格式

**如何贡献：**
1. Fork这个仓库
2. 创建您的功能分支 (`git checkout -b feature/神奇功能`)
3. 提交您的更改 (`git commit -m '添加一些神奇功能'`)
4. 推送到分支 (`git push origin feature/神奇功能`)
5. 打开Pull Request

---

## 📄 许可证

此项目是开源的，在[MIT许可证](LICENSE)下可用。

---

<p align="center">
    <b>⭐ 如果这个仓库对您有帮助，请给它加星！</b>
</p>
