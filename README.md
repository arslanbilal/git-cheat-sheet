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