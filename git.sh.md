Git is a **distributed [[version control system (VCS)]]** used for tracking changes in code, collaborating with others, and managing software development efficiently.
- **Version Control** allows multiple people to work on a project while keeping track of changes.
- **Git** is a **distributed** VCS, meaning every developer has a full copy of the repository.
---
# **Installation**
```sh
	sudo pacman -S git    # Arch
	sudo apt install git  # Debian/Ubuntu  
    sudo yum install git  # RHEL/CentOS  
    brew install git      # MacOS Homebrew
```
- **Windows**: Download from [git-scm.com](https://git-scm.com/)
---
# **Usage**
```sh
git init              # Create a new repository
git clone <repo_url>  # Or clone a pre-existing repo

# Checking Repository Status
git status

# Adding Files to Staging Area
git add <file>      # Add a single file  
git add .           # Add all changes  

# Committing Changes
git commit -m "Commit message"

# Viewing Commit History
git log
```
---
# **Working with Remote Repositories**
```sh
# Adding a Remote Repository
git remote add origin <repo_url>

#Pushing Changes to Remote
git push origin <branch_name>

#Pulling Changes from Remote
git pull origin <branch_name>

#Fetching Remote Changes
git fetch  # Downloads changes without merging them.
```
---
# **Undoing Changes**
**Undo Last Commit (Keep Changes in Staging)**
```sh
git reset --soft HEAD~1
```
**Undo Last Commit (Remove Changes Completely)**
```sh
git reset --hard HEAD~1
```
**Revert a Commit (Create a New Commit that Undoes a Previous One)**
```sh
git revert <commit_hash>
```
---
# Branches
### **1. What is a Branch in Git?**
A **branch** is a pointer to a commit in Git. When you create a new branch, it simply **points to the same commit** as your current branch until you make changes.
- The **main branch** (default) is usually called `main` or `master`.
- **Feature branches** are used for developing new features.
- **Bug fix branches** help isolate fixes.
---
### **2. Listing Branches**
```sh
	git branch     # List local branches (on your machine)
    git branch -r  # List remote branches (from the remote repository)
    git branch -a  # List all branches (local + remote)
    git branch --show-current
```
### **3. Creating and Switching Branches**
```sh
git branch <branch_name>   # creates but doesn't switch 

git checkout <branch_name> # switch to a branch
git switch <branch_name>   # switch to a branch (recommended in new git versions)

git checkout -b <branch_name> # Create and switch
git switch -c <branch_name>   # Create and switch (-c,--create)
```
---
### **4. Renaming a Branch**
```sh
git branch -m <new_branch_name> # Rename Current Branch (-m, --move)
git branch -m <old_name> <new_name> # Rename Another branch (-m, --move)
```
---
### **5. Merging Branches**
When you're done working on a feature, you need to merge it back into `main` or another branch.
1. Switch to `main` branch:
    ```sh
    git checkout main
    ```
2. Merge the feature branch:
    ```sh
    git merge <branch_name>
    ```
If there are **merge conflicts**, Git will prompt you to resolve them manually before completing the merge.

---
### **6. Deleting Branches**
### **Delete a Local Branch**
```sh
git branch -d <branch_name>
```
If the branch contains unmerged changes, use:

```sh
git branch -D <branch_name>
```
### **Delete a Remote Branch**

```sh
git push origin --delete <branch_name>
```
---
## **7. Working with Remote Branches**
### **Fetch Remote Branches**
```sh
git fetch
```
### **Track a Remote Branch Locally**
```sh
git checkout -b <local_branch> origin/<remote_branch>
```

### **Push a New Branch to Remote**

```sh
git push -u origin <branch_name>
```

The `-u` option sets the upstream branch for easy future pushes.

---

## **8. Rebasing Instead of Merging**

Instead of merging, you can **rebase** a branch to keep a linear commit history.

```sh
git checkout feature-branch
git rebase main
```

This applies the commits from `feature-branch` **on top of** the latest `main`.

---
### **Best Practices for Git Branching**

✅ Use **descriptive names** (e.g., `feature-login`, `fix-bug-123`)  
✅ Keep feature branches **short-lived** and regularly merge them  
✅ Regularly **pull updates** to avoid conflicts  
✅ Delete **stale branches** after merging
# Configuration
1. **System-wide (`--system`)** – Applies to all users on the computer.
2. **User-wide (`--global`)** – Applies to your user account.
3. **Repository-specific (`--local`)** – Applies only to a single project.
```sh
git config --list           # List all configs applied now
git config user.name        # List a specific config

# Git needs your name and email to track who makes changes.
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# By default, Git names the first branch **master**, but many projects now use main. Set the default to main:
git config --global init.defaultBranch main

# When writing commit messages, Git uses a text editor. Change it to your preferred editor:
git config --global core.editor "code --wait"  # For VS Code
git config --global core.editor "nano"        # For Nano
git config --global core.editor "vim"         # For Vim

# Enabling Color Output for Better Readability
git config --global color.ui auto

# Create Aliases
git config --global alias.st status  # 'git st' instead of 'git status'
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.cm "commit -m"
```
---
# Etymology
**The name "git" doesn’t stand for anything. but was given by Linus Torvalds when he wrote the very first version**. He described the tool as "the stupid content tracker" and the name as : random three-letter combination that is pronounceable, and not actually used by any common UNIX command.

---
# Resources
- [Online Interactive Visual Git Course](https://learngitbranching.js.org/)
- [Visual Git Game](https://ohmygit.org/)



 HEAD is the symbolic name for the currently checked out commit -- it's essentially what commit you're working on top of.
 HEAD always points to the most recent commit which is reflected in the working tree. Most git commands which make changes to the working tree will start by changing HEAD.
Normally HEAD points to a branch name (like bugFix). When you commit, the status of bugFix is altered and this change is visible through HEAD.

Detaching HEAD just means attaching it to a commit instead of a branch.


Git is smart about hashes. It only requires you to specify enough characters of the hash until it uniquely identifies the commit. So I can type `fed2` instead of the long string above. (full hash is fed2da64c0efc5293610bdd892f82a58e8cbc5d8)

Relative commits are powerful, but we will introduce two simple ones here:
- Moving upwards one commit at a time with `^`
- Moving upwards a number of times with `~<num>`
So saying `main^` is equivalent to "the first parent of `main`".
`main^^` is the grandparent (second-generation ancestor) of `main`

You can directly reassign a branch to a commit with the `-f` option. So something like:
`git branch -f main HEAD~3`
_Note: In a real git environment `git branch -f command` is not allowed for your current branch._


here are two primary ways to undo changes in Git -- one is using `git reset` and the other is using `git revert`
 `git reset` will move a branch backwards as if the commit had never been made in the first place.