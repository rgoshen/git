# Git 

A simplylearn course

## TOC

1. [Git Basics](#git-basics)
1. [Getting Started With Git](#getting-started-with-git)


## Git Basics

### Introduction to Git

- Git provides a flexible environment to work collaboratively and securely
- Has a Verison Control System (VCS) to allow multiple users:
	- to modify the same file, 
	- to record and track changes, 
	- to revert to earlier versions
	- to compare mutliple versions of a file
	- to manage conflicts and merge files
- Allows users to create and manage remote repositories (repos)
- Facilitates branching and merging of files with the main repo
- Allows each user to have a copy of the file locally thus keeping the file in the server secure

### Limitations fo Existing VCS and What is Git

- Limitations of Exisiting VCS
	- Existing VCS have a centralized architecture
	- Changes cannot be done offline
		- User retireves the file, makes changes, and commits
		- Next user can only pull the data when online
	- All changes are made in the central server
		- Connecting to the central server is necessary to make edits
		- Leaves no room for error
- What is Git?
	- A VCS - distributed revision control system aimed at:
		- speed
		- data integrity
		- security

### Git Configuration Levels

- Three levels of configuration
	- System level: `--system`
		- applicable to all users who use the system where git is installed
		- __command:__ `git config --system`
		- saves to: `/etc/gitconfig`
	- Global level: `--global`
		- applicable to user settings for all repos
		- __command:__ `git config --global`
		- saves to: `~/.gitconfig`
	- Local level: `--local`
		- applicable to the current repo only
		- __command:__ `git config --local` or `git config`
		- saves to: `.git/config`
	
> NOTE:
>
> Local overides Global and Global overrides System Level.

The following settings needs to be configured for all commits:
 
 - user.name
 - user.email
 
 [back](#toc)
 
## Getting Started with Git
 
### Creating a Git Repository
 
 Steps to Create a Git Repository
 
 1. Create an empty directory and change directory into created directory `mkdir <directory-name> && cd <directory-name>`
 1. Convert the directory into repository `git init`
 1. **ALT:** `git init <directory-name>` combines steps 1 & 2
 1. Run git status `git status`
 
 > NOTE:
 >
 > **`git init`** command creates a hidden directory that stores all the metadata required for it to function.
 
### Git Workflow

Git maintains three snapshots of a file maintained in separate directories:

1. Working Directory
	- refers to the directory where git was initialized by `git init` command
	- when a file is entered/created in this directory, it is __untracked__
	- Staging Area
		- area where files are moved to when __tracked__
		- __command:__ `git add`
1. __.git/index file__
	- storage of staged files
1. Local Repository
	- file moved to this area when it is committed
	- __command:__ `git commit`

#### Working Directory to Staging Area

- Working Directory
	1. drop a file into the directory
	2. add the file using `git add` command
- Staging Area
	- tracked
	- ready to commit

	1. commit the file to the local repo by using the `git commit` commands
- Local Repository
	- once the file is committed to the local repo, the working directory is cleaned
	- the local repo is in sync with the latest changes in the working repo

> NOTE:
>
> While committing, it is important to add a message using the __-m flag__.
> If missing, a default editor opens asking for comments.

### Managing and Viewing Changes

To modify a file in git --> Update --> Add --> Commit

To view the changes in a file:

 - __command:__ `git log`
 	- lists all the commands enacted on the file in reverse chronological order by:
 		- Commit ID
 		- Author
 		- Date
 		- Commit Message

> NOTE:
> 
> To restrict the output to one line, execute: __`git log --oneline`__,
> this will display the information is a single line.

### Tracking File Changes

Ability to identify changes between the different versions of the same file, spread across various repos

__command:__ `git diff`

- view the changes of a modified file in it's working directory and it's staged state

__command:__ `git diff --staged`

- view the changes of the staged file and it's last commit of the same file

Once in the local repo, the latest commit of a file is pointed to by a pointer called __HEAD__

 - each of the previous commits are also pointed to by a pointer called __HEADX__ where X is an incremented number beginnning with 1

> NOTE:
> 
> Command __`git diff --staged`__ is similar to __`git diff HEAD`__
> 

> If the number of commits increase beyond a certain count, use the __hascode__ command.
> 
> __command:__ `git diff <commit hashcode>`

### Reverting to Earlier Commits

Steps to Revert to Earlier Commits in Git

1. List details of the commit associated with a file __command:__ `git log`
2. Stage the file __command:__ `git checkout <version-code>` or `git checkout HEAD~1 <filename>`
3. Share the command to unstage the file __command:__ `git status`
4. Remove the file from the staging area and bring it back to the working directory __command:__ `git reset`

### Deleting Files in Git

Deleting Files from Staging Area and Working Directory

- Delete the file from staging area and working directory __command:__ `git rm <filename>`
	- To verify file has been removed from the staging area __command:__ `git ls-files --stage`
- Delete a file only from the staging area __command:__ `git rm --cached <filename>`

> NOTE:
> 
> This file will be untracked as it is removed from the staging area.

#### Restoring Deleted Files

The deleted file history is still in the repo

- __command:__ `git checkout <version> <filename>`

### Ignoring File in Git

How to ignore Files in Git

- Add the file to a __.gitignore__ file
	- stores file name
	- stores file pattern
- The file name and file pattern can be overridden using the __-f flag__

### Renaming Files in Git

Steps to Rename Files in Git

1. __command:__ `git mv <filename> <new-filename>`
2. __command:__ `git add .`
3. __command:__ `git commit -m "renamed <filename> => <new-filename>"`
4. __command:__ `git status`
