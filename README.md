# Getting Git Notes

 1. [Making Changes](#making-changes)
 2. [Viewing History](#viewing-history)
 3. [Managing Workflow](#managing-workflow)
 4. [Sharing Work](#sharing-work)
 5. [Everyday Git](#everyday-git)

## Making Changes

- [Overview](#overview)
- [init: git init](#init-git-init)
- [Master: git init](#master-git-init)
- [init: git add](#init-git-add)
- [Master: git add](#master-git-add)
- [init: git commit](#init-git-commit)
- [Master: git commit](#master-git-commit)
- [init: git rm](#init-git-rm)
- [Master: git rm](#master-git-rm)
- [init: git reset](#init-git-reset)
- [Master: git reset](#master-git-reset)
- [init: git revert](#init-git-revert)
- [Master: git revert](#master-git-revert)
- [Summary](#summary)

### Overview

### init: git init

`git init`

- Turns a directory into a git repository
- Track files under the directory

`git status`

- Current state of repository

### Master: git init

`git init`

- Unlikey to use the options for `git init`
- What does `git init` do?
 - Creates a **.git** directory: "Initialized empty Git repository in /dir/.git/"
 - The **.git** directory serves as a database to store info about current state of repo and its history
 - Deleting the **.git** directory will remove git repository

### init: git add

- Changes are not automatically tracked by Git. This is an important difference to other version control systems.
- `git add` allows selection of what files should be tracked
- `git add file1.txt` adds a single file
- `git add .` adds multiple files
- `git add dir` adds all files in a directory
- `git add *.c` adds all matching files
- `git add -p` interactively add files
- `git add --help` for more commands

### Master: git add

`git add .`

- Only adds files under the current directory
- Adds tracked and untracked files
 
 `git add -A`
 
- Adds all files within the git repo regardless of current directory
  
`git add -u`

- Only adds tracked files
 
 `git add -p`
 
- The `p` stands for patch
- Gathers all changes in tracked files and allows you to review them *interactively*
 - Some options for interactive review
  - `y` add the change and continue
  - `n` not add the change
  - `s` split the change into smaller changes
  - `q` quit

`git help add` for more details

### init: git commit

`git add` tells Git what changes we want to track aka *staging* our changes

`git commit` takes all *staged* changes and records them together as a version

`git commit` will open your text editor so you can provide a commit message

After using `git commit`:

1. Git took all of our staged changes and recorded them as a version, assigning it a unique ID (Hash or HSA)
2. Staged changes are no longer seen by Git as modified

In review, Git gives you a two part process to give you full control over your changes

1. You tell Git what changes you want to be in the version 
2. You record those changes to create the version

`git commit -m 'Commit message'` adds commit message from terminal

### Master: git commit

`git commit -a -m 'Commit message'` add & commit in one command
`git commit -am 'Commit message'` combine options

`git commit --amend` launches text editor to edit previous commit message

`git commit -a --amend --no-edit` add additional changes to the previous commit and don't change the message

- `-a` add all changes to all tracked files
- `--amend` add to previous commit
- `--no-edit` use original commit message

### init: git rm

After deleting a file (via UI or `rm file.txt`) this change can be tracked using `git add file.txt` - this requires 2 steps

`git rm file.txt` removes file and stages change in one command

### Master: git rm

`git rm --cached file.txt`

- Remove from repository but keep local copy
- Opposite to `git add`

### init: git reset

`git reset`

- Unstages changes
- Command is shown when running `git status`:
 - (use "git reset HEAD <file>..." to unstage change)
 - `HEAD` can be dropped as this is the default

`git reset file.txt`

- Removes staged file
- Effectively undid the `git add file.txt` command

`git reset` removes all staged changes

`git reset` undoes commands such as `git add` and `git rm`

### Master: git reset

Resetting commits with `git reset`

`git reset SHA^`

- Using the Hash/SHA from a commit `git reset` can be used to undo a commit 
- note: `^` after SHA
- In other words, it resets the repo back to the state before the commit

`git reset --hard SHA^`

- Resets the repo back to the *clean* state before the commit

`git reset --hard`

- Resets repo back to *clean* state
- For example, remove staged files

`git reset --hard` is a *destructive* command so be careful when using it!

### init: git revert

Automatically create a new commit containing changes that undo the original commit

`git revert SHA`

- Opens text editor for comment
- Automatically creates a message "Revert 'my commit'"
- Adds the commit SHA in the commit message body e.g. "This reverts SHA" and the files that were changed in the commit comments

### Master: git revert

`git revert -n SHA`

- `-n` no commit
- Command will put repo into state of *REVERTING*
- `git add` or `git rm` to add more changes or to stage the changes we want to undo

`git revert --continue`

- Complete the revert
- Recommended: modify the commit message to highlight the changes made to the commit

`git revert --abort`

- Abandon any changes made during the *REVERTING* process
- Revert current state back to the previous clean state

### Summary

![Image of commands summary](https://github.com/haakym/getting-git-notes/blob/master/images/part-1/summary.png)

## Viewing History - Part 2

### Overview

- `git status`
- `git log`
- `git show`
- `git diff`

### init: git status

`git status` on an empty repository will show

```
On branch master

Initial commit

nothing to commit (create/copy files and use "git add" to track)
```

- Shows current branch
- The current state of the repository
- Note, following words can be subsituted in Git:
	- working - current/local
	- tree - branch/repository

`git status` on a repo with some unstaged files will show

```
On branch master

Initial commit

	file-1.txt
	file-2.txt

nothing added to commit but untracked files present (use "git add" to track)
```

- Details about new files
- Git is very helpful. It recommends what command to use next, see final line recommends "git add" to stage files

`git status` on repo with a staged and unstaged file

```
On branch master

Initial commit

Changes to be committed:
	(use "git rm --cached <file>..." to unstage)

		new file:	file-1.txt

Untracked files:
	(use "git add <file>..." to include what will be committed)

		file-2.txt

```

### Master: git status

The states of `git status`

- Untracked files: not under version control so any changes to these files will not be tracked
- Changes to be committed: tracked files that have been staged
- Clean state: no untracked files and all tracked files are unmodified
- Modified: tracked files that have been changed since the previous commit

Life cycle:
- New file
 - untracked -> staged -> unmodified
- Tracked file
 - modified -> staged -> unmodified

`git reset` can be used to reverse aforementioned cycle

### init: git log

`git log` shows history of commits

- Commit SHA
- Author
- Date
- Full commit message
- Navigate up and down via arrow keys
- q to quit

`git log -n 2` or `git log -2` will limit the number of commits shown

`git log --online`

- Commit SHA
- Commit message

`git log filename` show only the commit history for a single file

`git log --oneline filename` combining above commands

### Master: git log

`git log --graph` visualises a git repo as a tree/graph

`git log --graph --decorate` will show HEAD

#### HEAD

- A pointer to the tip of your current branch
- More simply, a reference to the most recent commit

`git log --oneline -3` to illustrate example uses of HEAD

```
* 733f7e4 (HEAD -> master) contents and titles
* 99474b1 show image in summary
* 1ca93bc summary image
```

- HEAD can be used to relatively reference other commits with ^ and ~
 - HEAD - most recent commit
 - HEAD~1 or HEAD^ - 1 commit before HEAD
 - HEAD~2 or HEAD^^ - 2 commits before HEAD
 - HEAD~3 or HEAD^^^ - 3 commits before HEAD
- Commit SHAs can also be used
 - HEAD or 733f7e4 - most recent commit
 - 99474b1 or 733f7e4~1 or 733f7e4^ - 1 commit before HEAD
 - 1ca93bc or 733f7e4~2 or 733f7e4^^ - 2 commits before HEAD

### init: git show

`git show`

- Similar to git log with its options being almost identical
- By default only shows the most recent commit
- Shows the changes in the commit

`git show SHA` for a specific commit

### Master: git show

`git show --name--status`

- Show each file changed and how it was changed
 - M - modified
 - A - added
 - D - deleted

 Use `git show` to show information on a single commit, for everything else use `git log`

### init: git diff

`git diff` on tracked files with modifications

- Additions in green with a +
- Deletions in red with a -
- Scroll through changes with keys, q to quit
- Only displays changes to tracked modified files, does not display changes to untracked or staged files

`git diff --staged` to see staged changes

`git diff filename` to only show changes in a file

### Master: git diff

`git diff -w` ignore whitespace changes

Example log:

```
* 733f7e4 contents and titles
* 99474b1 show image in summary
* 1ca93bc summary image
```

`git diff 733f7e4..99474b1`

- Show changes between a range of SHAs
- Will ignore recent changes (HEAD) as outside of range specified
- Note: more recent commit is first, counter intuitive as will show diff as deletions (-)

`git diff 99474b1..733f7e4`

- Note: more recent commit is second, easier to reason with as will show diff as additions (+)

### Summary

With the exception of `git status` other commands may be seldom used

`git log --oneline` to get an overview of an unfamiliar repository

`git log --oneline --name-status -10` to see recent commits

`git diff 1ca93bc..HEAD`

- Older SHA first 

## Managing Workflow - Part 3

### Overview

### init: git branch

### Master: git branch

### init: git checkout

### Master: git checkout

### init: git merge

### Master: git merge

### init: git rebase

### Master: git rebase

### init: git cherry-pick

### Master: git cherry-pick

### Summary



## Sharing Work - Part 4

### Overview

### init: git clone

### Master: git clone

### init: git remote

### Master: git remote

### init: git push

### Master: git push

### init: git fetch

### Master: git fetch

### init: git pull

### Master: git pull

### Summary

