# Git
Git is a version control system and it is a tool that helps to track changes in the code.
# Git HUb
It is a website that allows developers to share and manage the code using git.
## Setting up Git
```
git --version
```
### Configuring Git
```
git config --global user.name "My name"
git config --global user.email "name@gmail.com"
git config --list
```
### Clone and Status
**Clone** - Cloning a repository on our local machine.
```
git clone link
```
**Status** - Display the state of the code.
```
git status
```
Types of status - Untracked, Modified, Staged, Unmodified.
## Add and Commit
**Add** - Adds new changed files in your working directory to the git staging area.
```
git add filename
```
**Commit** - It is the record of chnages.
```
git commit -m "Some message"
```
## Initialisation 
**init** - Used to create a new git repo.
```
git init
git remote add origin link
```
To verify remote
```
git remote -v
```
## Push Command
**Push** - Upload local repo content to remote repo.
```
git push origin main
```
### Work Flow 
Local Git -> GitHub Repo -> Clone -> Changes -> Add -> Commit -> Push
## Git Branches
A Git branch is a separate, independent version of your project's history.
### Branch Commands
To check branch
```
git branch
```
To rename branch
```
git branch -M main
```
To change branch 
```
git checkout branch_name
```
To create new branch
```
git checkout -b new_branch
```
To delete branch
```
git branch -d branch_name
```
To check history 
```
git log
```
## Merge Code
### Way1
To compare commits, branches, files and more.
```
git diff branch_name
```
To merge two branches.
```
git merge branch_name
```
### Way2
Create a pull request on github.
## Pull request
It is used to fetch and download content from a remote repo and immediately update the local repo to match that content.
### Pull command
```
git pull origin main
```
## Resolving merge conflicts
It is an event that takes place when git is unable to automatically resolve difference in code between two commits.
### Undoing changes
**Case1** - Staged changes
```
git reset file_name
git reset
```
**Case2** - Committed changes (for one commit)
```
git reset HEAD~1
```
**Case3** - Committed changes (for many commits)
```
git reset commit_hash
git reset --hard commit_hash
```
1. Committed the wrong message?
```
git commit --amend
```
2. Skipped file in the last commit ?
```
git commit —amend —no-edit
```
3. Accidentally committed on master?
```
git reset HEAD~ —hard
```
4. Accidentally committed to the wrong branch?
```
git reset HEAD~ —soft
```
5. Want to undo the last 5 commits?
```
git revert [Saved hash]
```
6. Want to undo changes to a file?
```
git checkout [saved hash] --file_path
```
## Fork 
A fork is a new repository that shares code and visibility settings with the original upstream repository (rough copy).
