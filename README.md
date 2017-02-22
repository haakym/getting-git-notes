# Getting Git Notes

[Making Changes - Part 1](#making-changes---part-1)

## Making Changes - Part 1

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