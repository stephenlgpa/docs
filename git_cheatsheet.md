# Git Cheat Sheet

## Installation

```
sudo apt install git [or] sudo apt-get git
git config --global user.name "Stephen Grabner"
git config --global user.email "gen@pronkingantelope.net"
git config --global --list
```

## Cloning a remote (e.g. GitHub) repository

- `git clone url` : clones a remote repository
- `git push origin master` : origin=remote name; master=branch to push 

## Starting with a fresh project

```
git init <projectname>  //creates new folder <projectname>
git add <filename>
git commit [or] git commit -m "message"
git status
```

## Add Git to current project

```
git init  //in existing folder
git add *   //adds all files in folder recursively
git commit -m "message"  //commit files
git status
```

## Basic commands

- `git status` :status of git
- `git add <file>` :git tracks the file, stages it.
- `git add .` :adds all recursively
- `git add *` :adds all files in folder (not recursively)
- `git commit -m "commit message"` :commits staged files to the repository
- `git commit` :opens editor to add a comment. Save.
- `git commit -am "message"` :stages modified files, then commits with message
- `git ls-files` :lists all files git is tracking
- `git push` :pushes local repository to remote repository (eg to GitHub)
- `git pull` :downloads latest changes from a remote repository to the local repository
- `git --version` :shows git version number

## Adding files

- `git add <fileOrDir>` :adds file to staging area. If a directory, recursively adds all files to the staging area
- `git add .` :
- `git add *` :add all files in directory

## Ignoring files

```
touch .gitignore
vim .gitignore
//add filenames/directories to this file, one to a line. Can use wildcards
```

## Renaming and Deleting files from Git

- `git rm --cached <filename>` :removes file from staging area


## Branches

- `git branch 'branchName'` :create a new branch called 'branchName'
- `git checkout 'branchName'` :switch to the branch 'branchName'
- `git commit -m "comment"` :changes are committed as normal to the new branch
- `git merge 'branchName'` :merge the branch back into the master branch





