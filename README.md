# Git Guide

## Table of Contents

1. [Introduction to Git](#introduction-to-git)
2. [Basic Git Commands](#basic-git-commands)
3. [Intermediate Git Commands](#intermediate-git-commands)
4. [Advanced Git Commands](#advanced-git-commands)
5. [Common Git Issues and Solutions](#common-git-issues-and-solutions)
6. [Additional Resources](#additional-resources)

---

## Introduction to Git

Git is a **distributed version control system** designed to track changes in source code during software development. It enables collaboration, history tracking, and efficient management of project versions. Key features include:

- **Distributed Workflow**: Every developer has a full copy of the repository.
- **Branching and Merging**: Easily manage parallel lines of development.
- **Data Integrity**: Uses SHA-1 hashes to ensure file and commit integrity.

---

## Basic Git Commands

### Initialization and Configuration

- **Initialize a new repository**:
```
git init
```

- **Configure global username/email** (required for commits):
```
git config --global user.name "Your Name"
```
```
git config --global user.email "your.email@example.com"
```

### Working with Repositories

- **Clone an existing repository**:
```
git clone https://github.com/user/repo.git
```

- **Stage changes for commit**:
```
git add file.txt # Stage a specific file
```
```
git add . # Stage all changes
```

- **Commit staged changes**:
```
git commit -m "Descriptive commit message"
```

- **Check repository status**:
```
git status
```

- **Push commits to a remote repository**:
```
git push origin main
```

---

## Intermediate Git Commands

### Branching and Merging

- **Create a new branch**:
```
git branch feature-branch
```

- **Switch to a branch**:
```
git checkout feature-branch
```

- **Merge a branch into the current branch**:
```
git checkout main
```
```
git merge feature-branch
```

### Remote Management

- **Add a remote repository**:
```
git remote add origin https://github.com/user/repo.git
```

- **Fetch updates from a remote** (without merging):
```
git fetch origin
```

- **Pull updates from a remote** (fetch + merge):
```
git pull origin main
```

### Stashing Changes

- **Save uncommitted changes temporarily**:
```
git stash
```

- **Restore stashed changes**:
```
git stash pop
```

---

## Advanced Git Commands

### Rebasing

- **Reapply commits on top of another branch** (rewrites history):
```
git checkout feature-branch
```
```
git rebase main
```

### Resetting Changes

- **Unstage a file** (keeps changes):
```
git reset file.txt
```

- **Reset to a previous commit** (use with caution):
```
git reset --hard HEAD~1 # Discard last commit and changes
```

### Advanced Tools

- **Cherry-pick a commit**:
```
git cherry-pick abc1234 # Apply commit abc1234 to current branch
```

- **View commit history with reflog** (for recovery):
```
git reflog
```

- **Manage submodules**:
```
git submodule add https://github.com/user/submodule.git
```

---

## Common Git Issues and Solutions

### 1. Merge Conflicts

**Problem**: Conflicting changes between branches during a merge or pull.  
**Solution**:
1. Open the conflicted files and resolve the marked sections (`<<<<<<<`, `=======`, `>>>>>>>`).
2. Stage the resolved files:
 ```
git add file.txt
```
3. Complete the merge:
 ```
git commit -m "Resolved merge conflict"
```

### 2. Detached HEAD State

**Problem**: Accidentally checking out a commit instead of a branch.  
**Solution**:
- Create a new branch to retain changes:
```
git checkout -b new-branch-name
```

### 3. Accidental Commit to Wrong Branch

**Problem**: Committed changes to `main` instead of a feature branch.  
**Solution**:
1. Switch to the correct branch:
 ```
git checkout feature-branch
```
2. Cherry-pick the commit:
 ```
git cherry-pick abc1234
```
3. Reset the original branch:
 ```
git checkout main
```
 ```
git reset --hard HEAD~1
```

### 4. Accidentally Deleting a Branch

**Problem**: Lost work after deleting a branch.  
**Solution**:
1. Find the commit hash using 
```
git reflog
```
2. Recreate the branch:
 ```
git branch recovered-branch abc1234
```

### 5. Large Files in History

**Problem**: Repository size is bloated due to large files.  
**Solution**:
1. Use `git filter-branch` or tools like `git-filter-repo` to purge history.
2. Update the remote repository:
 ```
git push origin --force --all
```

---

## Additional Resources
- **[Official Git Documentation](https://git-scm.com/doc)**: Comprehensive reference for all commands.
- **[Pro Git Book](https://git-scm.com/book/en/v2)**: Free online book covering Git in depth.
- **[GitHub Training](https://docs.github.com/en/get-started)**: Guides for Git and GitHub workflows.
- **[Atlassian Git Tutorials](https://www.atlassian.com/git/tutorials)**: Beginner-friendly tutorials.

Feel free to explore these resources for more in-depth learning and troubleshooting.
