# Getting Git Notes

## Making Changes

### Overview

### init: git init

### Master: git init

### init: git add

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
