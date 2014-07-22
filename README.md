Git Cheat Sheet
===============

<hr>

<h4>Create</h4>

Clone an existing repository:
```
$ git clone ssh://user@domain.com/repo.git
```

Create a new local repository:
```
$ git init
```

<hr>

<h4>Local Changes</h4>

Changed files in your working directory:
```
$ git status
```

Changes to tracked files:
```
$ git diff
```

Add all current changes to the next commit:
```
$ git add
```

Add some changes in <file> to the next commit:
```
$ git add -p <file>
```

Commit all local changes in tracked files:
```
$ git commit -a
```

Commit previously staged changes:
```
$ it commit
```

Commit with message
```
$ git commit -m 'message here'
```

Change last commit:<br>
<em><sub>Don't amend published commits!</sub></em>
```
$ git commit --amend
```

<hr>

<h4>Commit History</h4>

Show all commits, starting with newest:
```
$ git log
```

Show changes over time for a specific file:
```
$ git log -p <file>
```

Who changed, what and when in <file>:
```
$ git blame <file>
```

<hr>

<h4>Branches & Tags</h4>

List all existing branches:
```
$ git branch
```

Switch HEAD branch:
```
$ git checkout <branch>
```

Create a new branch based on your current HEAD:
```
$ git branch <new-branch>
```

Create a new tracking branch based on a remote branch:
```
$ git branch --track <new-branch> <remote-branch>
```

Delete a local branch:
```
$ git branch -d <branch>
```

Mark the current commit with a tag:
```
$ git tag <tag-name>
```

<hr>

<h4>Update & Publish</h4>

List all current configured remotes:
```
$ git remote -v
```

Show information about a remote:
```
$ git remote show <remote>
```

Add new remote repository, named <remote>:
```
$ git remote add <remote> <url>
```

Download all changes from <remote>, but don't integrate into HEAD:
```
$ git fetch <remote>
```

Download changes and directly merge/integrate into HEAD:
```
$ git remote pull <remote> <url>
```

Publish local changes on a remote:
```
$ git push remote <remote> <branch>
```

Delete a branch on the remote:
```
$ git push <remote> :<branch>
```

Publish your tags:
```
$ git push --tags
```

<hr>

<h4>Merge & Rebase</h4>

Merge <branch> into your current HEAD:
```
$ git merge <branch>
```

Rebase your current HEAD onto <branch>:<br>
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

<hr>