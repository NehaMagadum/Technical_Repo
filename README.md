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
**Clone** - Cloning a repository on our local machine
```
git clone link
```
**Status** - Display the state of the code.
```
git status
```
Types of status - Untracked, Modified, Staged, Unmodified.
## Add and Commit
**Add** - adds new changed files in your working directory to the git staging area.
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
### Branch Command
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
To merge two branches
```
git merge branch_name
```
### Way2
Create a pull request on github.
## Pull request
It is used to fetch and download content from a remote repo and immediately update the local repo to natch that content.
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
## Fork 
A fork is a new repository that shares code and visibility settings with the original upstream repository.




