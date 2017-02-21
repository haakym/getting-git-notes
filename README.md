# Getting Git Notes

## Making Changes - Part 1

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
 - Creates a .git directory: > Initialized empty Git repository in /dir/.git/
 - .git directory serves as a database to store info about current state of repo and its history
 - Deleting the .git directory will remove git repository

### init: git add

- Changes are not automatically tracked by Git, important difference to other version control systems
- Git add allows selection of what files should be tracked
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

`git commit --amend` launches text editor to edit previous commit message

`git commit -a --amend --no-edit` add additional changes to the previous commit and don't change the message

- `-a` add all changes to all tracked files
- `--amend` add to previous commit
- `--no-edit` use original commit message

### init: git rm

After deleting a file (via UI or `rm file.txt`) this change can be tracked using `git add file.txt` - this requires 2 steps

`git rm file.txt` removes file and stages change in one command

### Master: git rm



### init: git reset

### Master: git reset

### init: git revert

### Master: git revert

### Summary
