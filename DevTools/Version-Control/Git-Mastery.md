<div align="center">

# 🎯 Git Mastery - Complete Guide

<img src="https://img.shields.io/badge/Git-Mastery-orange?style=for-the-badge&logo=git" alt="Git">
<img src="https://img.shields.io/badge/Version-Control-blue?style=for-the-badge" alt="Version Control">
<img src="https://img.shields.io/badge/Level-Beginner_to_Advanced-green?style=for-the-badge" alt="All Levels">

### _Master Git from basics to advanced techniques_ 🚀

**Because version control is not optional** 💪

</div>

---

## 📚 Table of Contents

- [🎯 Git Basics](#-git-basics)
- [⚙️ Configuration](#️-configuration)
- [📝 Daily Workflow](#-daily-workflow)
- [🌿 Branching & Merging](#-branching--merging)
- [🌐 Remote Operations](#-remote-operations)
- [🔍 Viewing History](#-viewing-history)
- [↩️ Undoing Changes](#️-undoing-changes)
- [🔧 Advanced Techniques](#-advanced-techniques)
- [🚨 Troubleshooting](#-troubleshooting)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 🎯 Git Basics

</div>

### What is Git? 📖

```bash
# ═══════════════════════════════════════════
# Git Fundamentals
# ═══════════════════════════════════════════

# Git is a distributed version control system
# Key concepts:
# - Repository (repo): Collection of files and their history
# - Commit: Snapshot of your files at a point in time
# - Branch: Independent line of development
# - Remote: Version of your repo hosted elsewhere (GitHub, GitLab)

# ═══════════════════════════════════════════
# The Three States
# ═══════════════════════════════════════════

# Working Directory → Staging Area → Repository

# 1. Modified: Changes made but not staged
# 2. Staged: Changes marked to go into next commit
# 3. Committed: Changes safely stored in repository

# ═══════════════════════════════════════════
# Installing Git
# ═══════════════════════════════════════════

# macOS
brew install git

# Linux (Debian/Ubuntu)
sudo apt-get install git

# Linux (Fedora)
sudo dnf install git

# Windows
# Download from: https://git-scm.com/download/win

# Verify installation
git --version
```

---

### First Time Setup 🛠️

```bash
# ═══════════════════════════════════════════
# Configure Your Identity
# ═══════════════════════════════════════════

# Set your name (required)
git config --global user.name "MrDib"

# Set your email (required)
git config --global user.email "mrdib@example.com"

# View your configuration
git config --list

# View specific config
git config user.name
git config user.email

# ═══════════════════════════════════════════
# Configuration Levels
# ═══════════════════════════════════════════

# System level (all users)
git config --system user.name "Name"

# Global level (your user)
git config --global user.name "Name"

# Local level (current repository)
git config --local user.name "Name"

# Priority: local > global > system

# ═══════════════════════════════════════════
# View Configuration Location
# ═══════════════════════════════════════════

# System config
/etc/gitconfig

# Global config
~/.gitconfig

# Local config
.git/config

# Edit config file directly
git config --global --edit
```

---

<div align="center">

## ⚙️ Configuration

</div>

### Essential Configuration 🔧

```bash
# ═══════════════════════════════════════════
# Editor Configuration
# ═══════════════════════════════════════════

# Set default editor
git config --global core.editor "code --wait"  # VS Code
git config --global core.editor "vim"          # Vim
git config --global core.editor "nano"         # Nano

# ═══════════════════════════════════════════
# Default Branch Name
# ═══════════════════════════════════════════

# Set default branch name to 'main'
git config --global init.defaultBranch main

# ═══════════════════════════════════════════
# Line Endings
# ═══════════════════════════════════════════

# macOS/Linux
git config --global core.autocrlf input

# Windows
git config --global core.autocrlf true

# ═══════════════════════════════════════════
# Color Output
# ═══════════════════════════════════════════

git config --global color.ui auto

# ═══════════════════════════════════════════
# Aliases (Shortcuts)
# ═══════════════════════════════════════════

# Status
git config --global alias.st status

# Checkout
git config --global alias.co checkout

# Branch
git config --global alias.br branch

# Commit
git config --global alias.cm commit

# Last commit
git config --global alias.last 'log -1 HEAD'

# Pretty log
git config --global alias.lg "log --graph --oneline --all --decorate"

# Undo last commit (keep changes)
git config --global alias.undo 'reset --soft HEAD~1'

# Show all aliases
git config --global alias.aliases "config --get-regexp ^alias\."

# ═══════════════════════════════════════════
# Diff & Merge Tools
# ═══════════════════════════════════════════

# VS Code as diff tool
git config --global diff.tool vscode
git config --global difftool.vscode.cmd 'code --wait --diff $LOCAL $REMOTE'

# VS Code as merge tool
git config --global merge.tool vscode
git config --global mergetool.vscode.cmd 'code --wait $MERGED'

# ═══════════════════════════════════════════
# Ignore File Permissions
# ═══════════════════════════════════════════

git config --global core.fileMode false

# ═══════════════════════════════════════════
# Cache Credentials
# ═══════════════════════════════════════════

# Cache for 1 hour (3600 seconds)
git config --global credential.helper 'cache --timeout=3600'

# Store permanently (macOS)
git config --global credential.helper osxkeychain

# Store permanently (Linux)
git config --global credential.helper store

# Store permanently (Windows)
git config --global credential.helper wincred
```

---

<div align="center">

## 📝 Daily Workflow

</div>

### Creating & Cloning Repositories 📂

```bash
# ═══════════════════════════════════════════
# Initialize New Repository
# ═══════════════════════════════════════════

# Create new directory and initialize
mkdir my-project
cd my-project
git init

# Or initialize in current directory
git init

# Initialize with specific branch name
git init -b main

# ═══════════════════════════════════════════
# Clone Existing Repository
# ═══════════════════════════════════════════

# Clone via HTTPS
git clone https://github.com/username/repo.git

# Clone via SSH
git clone git@github.com:username/repo.git

# Clone into specific directory
git clone https://github.com/username/repo.git my-folder

# Clone specific branch
git clone -b develop https://github.com/username/repo.git

# Shallow clone (faster, only recent history)
git clone --depth 1 https://github.com/username/repo.git
```

---

### Making Changes 📝

```bash
# ═══════════════════════════════════════════
# Check Status
# ═══════════════════════════════════════════

git status              # Full status
git status -s           # Short status
git status -sb          # Short with branch info

# ═══════════════════════════════════════════
# Add Files to Staging
# ═══════════════════════════════════════════

# Add specific file
git add filename.txt

# Add multiple files
git add file1.txt file2.txt

# Add all changes in current directory
git add .

# Add all changes in repository
git add -A
git add --all

# Add only modified files (not new files)
git add -u
git add --update

# Interactive staging
git add -i

# Add part of a file (patch mode)
git add -p filename.txt

# ═══════════════════════════════════════════
# Unstage Files
# ═══════════════════════════════════════════

# Unstage specific file
git reset filename.txt
git restore --staged filename.txt

# Unstage all files
git reset
git restore --staged .

# ═══════════════════════════════════════════
# Discard Changes
# ═══════════════════════════════════════════

# Discard changes in working directory
git checkout -- filename.txt
git restore filename.txt

# Discard all changes
git checkout -- .
git restore .

# ═══════════════════════════════════════════
# Commit Changes
# ═══════════════════════════════════════════

# Commit with message
git commit -m "Add user authentication"

# Commit with detailed message
git commit -m "Add user authentication" -m "- Implement login/logout
- Add session management
- Add password hashing"

# Commit all modified files (skip staging)
git commit -am "Quick fix"

# Amend last commit
git commit --amend

# Amend without changing message
git commit --amend --no-edit

# Empty commit (useful for triggering CI)
git commit --allow-empty -m "Trigger CI build"

# ═══════════════════════════════════════════
# Remove Files
# ═══════════════════════════════════════════

# Remove file from working directory and staging
git rm filename.txt

# Remove file from staging only (keep in working directory)
git rm --cached filename.txt

# Remove directory
git rm -r directory/

# Force remove
git rm -f filename.txt

# ═══════════════════════════════════════════
# Move/Rename Files
# ═══════════════════════════════════════════

# Rename file
git mv oldname.txt newname.txt

# Move file
git mv file.txt directory/

# Equivalent to:
mv oldname.txt newname.txt
git rm oldname.txt
git add newname.txt
```

---

### Ignoring Files 🙈

```bash
# ═══════════════════════════════════════════
# .gitignore File
# ═══════════════════════════════════════════

# Create .gitignore file
cat > .gitignore << EOF
# Dependencies
node_modules/
vendor/

# Build output
dist/
build/
*.min.js
*.min.css

# Environment variables
.env
.env.local
.env.*.local

# IDE
.vscode/
.idea/
*.swp
*.swo

# OS
.DS_Store
Thumbs.db

# Logs
*.log
logs/

# Temporary files
tmp/
temp/
*.tmp

# Test coverage
coverage/

# Package lock files (optional)
# package-lock.json
# yarn.lock
EOF

# ═══════════════════════════════════════════
# Ignore Already Tracked Files
# ═══════════════════════════════════════════

# Remove from Git but keep locally
git rm --cached filename.txt
git rm -r --cached directory/

# Then add to .gitignore and commit
echo "filename.txt" >> .gitignore
git add .gitignore
git commit -m "Stop tracking filename.txt"

# ═══════════════════════════════════════════
# Global Gitignore
# ═══════════════════════════════════════════

# Create global ignore file
git config --global core.excludesfile ~/.gitignore_global

# Add common OS/IDE files
cat > ~/.gitignore_global << EOF
# macOS
.DS_Store
.AppleDouble
.LSOverride

# Windows
Thumbs.db
ehthumbs.db
Desktop.ini

# Linux
*~

# IDE
.vscode/
.idea/
*.swp
EOF

# ═══════════════════════════════════════════
# Check if File is Ignored
# ═══════════════════════════════════════════

git check-ignore -v filename.txt

# List all ignored files
git status --ignored
```

---

<div align="center">

## 🌿 Branching & Merging

</div>

### Branch Management 🌳

```bash
# ═══════════════════════════════════════════
# List Branches
# ═══════════════════════════════════════════

# List local branches
git branch

# List all branches (local + remote)
git branch -a

# List remote branches
git branch -r

# List with last commit info
git branch -v
git branch -vv              # With tracking info

# List merged branches
git branch --merged

# List unmerged branches
git branch --no-merged

# ═══════════════════════════════════════════
# Create Branches
# ═══════════════════════════════════════════

# Create new branch
git branch feature-branch

# Create and switch to new branch
git checkout -b feature-branch
git switch -c feature-branch       # Modern way

# Create branch from specific commit
git branch feature-branch abc1234

# Create branch from remote branch
git checkout -b feature origin/feature

# ═══════════════════════════════════════════
# Switch Branches
# ═══════════════════════════════════════════

# Switch to existing branch
git checkout feature-branch
git switch feature-branch          # Modern way

# Switch to previous branch
git checkout -
git switch -

# ═══════════════════════════════════════════
# Rename Branches
# ═══════════════════════════════════════════

# Rename current branch
git branch -m new-name

# Rename other branch
git branch -m old-name new-name

# Rename remote branch
git push origin :old-name new-name
git push origin -u new-name

# ═══════════════════════════════════════════
# Delete Branches
# ═══════════════════════════════════════════

# Delete local branch (safe)
git branch -d feature-branch

# Force delete local branch
git branch -D feature-branch

# Delete remote branch
git push origin --delete feature-branch
git push origin :feature-branch    # Alternative syntax

# Delete all merged local branches
git branch --merged | grep -v "\*\|main\|develop" | xargs git branch -d

# ═══════════════════════════════════════════
# Track Remote Branches
# ═══════════════════════════════════════════

# Set upstream for current branch
git push -u origin feature-branch
git branch --set-upstream-to=origin/feature-branch

# View tracking relationships
git branch -vv
```

---

### Merging 🔀

```bash
# ═══════════════════════════════════════════
# Merge Branches
# ═══════════════════════════════════════════

# Merge feature-branch into current branch
git merge feature-branch

# Merge with commit even if fast-forward
git merge --no-ff feature-branch

# Fast-forward only (fail if not possible)
git merge --ff-only feature-branch

# Squash all commits into one
git merge --squash feature-branch
git commit -m "Merge feature-branch"

# ═══════════════════════════════════════════
# Merge Conflicts
# ═══════════════════════════════════════════

# When merge conflict occurs:
git merge feature-branch
# CONFLICT (content): Merge conflict in file.txt

# View conflicts
git status

# Mark as resolved
git add file.txt

# Continue merge
git commit

# Or abort merge
git merge --abort

# ═══════════════════════════════════════════
# Merge Tools
# ═══════════════════════════════════════════

# Use configured merge tool
git mergetool

# View merged file
git show :1:file.txt  # Common ancestor
git show :2:file.txt  # Your version (HEAD)
git show :3:file.txt  # Their version (merging branch)

# ═══════════════════════════════════════════
# Merge Strategies
# ═══════════════════════════════════════════

# Recursive (default)
git merge -s recursive feature-branch

# Ours (keep our version on conflict)
git merge -X ours feature-branch

# Theirs (keep their version on conflict)
git merge -X theirs feature-branch
```

---

### Rebasing 📐

```bash
# ═══════════════════════════════════════════
# Basic Rebase
# ═══════════════════════════════════════════

# Rebase current branch onto main
git rebase main

# Equivalent to:
# 1. Move to common ancestor
# 2. Apply main's commits
# 3. Apply your commits on top

# ═══════════════════════════════════════════
# Interactive Rebase
# ═══════════════════════════════════════════

# Rebase last 5 commits
git rebase -i HEAD~5

# Rebase onto main
git rebase -i main

# Interactive options:
# pick   = use commit
# reword = use commit, edit message
# edit   = use commit, stop for amending
# squash = use commit, combine with previous
# fixup  = like squash, discard message
# drop   = remove commit

# ═══════════════════════════════════════════
# Rebase Conflicts
# ═══════════════════════════════════════════

git rebase main
# CONFLICT!

# Resolve conflicts
git add conflicted-file.txt

# Continue rebase
git rebase --continue

# Skip current commit
git rebase --skip

# Abort rebase
git rebase --abort

# ═══════════════════════════════════════════
# Rebase vs Merge
# ═══════════════════════════════════════════

# Merge: Preserves history
git merge feature-branch

# Rebase: Clean, linear history
git rebase main

# Golden Rule: Never rebase public branches!

# ⚠️ DON'T: Rebase shared branches
git checkout main
git rebase feature  # ❌ Bad!

# ✅ DO: Rebase your feature branch
git checkout feature
git rebase main     # ✅ Good!
```

---

<div align="center">

## 🌐 Remote Operations

</div>

### Working with Remotes 🔗

```bash
# ═══════════════════════════════════════════
# List Remotes
# ═══════════════════════════════════════════

# List remote names
git remote

# List with URLs
git remote -v

# Show detailed info
git remote show origin

# ═══════════════════════════════════════════
# Add Remotes
# ═══════════════════════════════════════════

# Add remote
git remote add origin https://github.com/username/repo.git

# Add with SSH
git remote add origin git@github.com:username/repo.git

# Add upstream (for forks)
git remote add upstream https://github.com/original/repo.git

# ═══════════════════════════════════════════
# Modify Remotes
# ═══════════════════════════════════════════

# Change remote URL
git remote set-url origin https://github.com/username/new-repo.git

# Change to SSH
git remote set-url origin git@github.com:username/repo.git

# Rename remote
git remote rename origin upstream

# Remove remote
git remote remove origin
git remote rm origin

# ═══════════════════════════════════════════
# Fetch from Remote
# ═══════════════════════════════════════════

# Fetch all remotes
git fetch --all

# Fetch specific remote
git fetch origin

# Fetch specific branch
git fetch origin main

# Fetch and prune deleted branches
git fetch --prune
git fetch -p

# ═══════════════════════════════════════════
# Pull from Remote
# ═══════════════════════════════════════════

# Pull current branch
git pull

# Pull specific branch
git pull origin main

# Pull with rebase
git pull --rebase

# Pull from upstream (for forks)
git pull upstream main

# Pull all submodules
git pull --recurse-submodules

# ═══════════════════════════════════════════
# Push to Remote
# ═══════════════════════════════════════════

# Push current branch
git push

# Push and set upstream
git push -u origin feature-branch

# Push specific branch
git push origin main

# Push all branches
git push --all

# Push tags
git push --tags

# Push specific tag
git push origin v1.0.0

# Force push (⚠️ dangerous!)
git push --force

# Safe force push
git push --force-with-lease

# Delete remote branch
git push origin --delete feature-branch

# ═══════════════════════════════════════════
# Track Remote Branches
# ═══════════════════════════════════════════

# Create local branch tracking remote
git checkout -b feature origin/feature
git switch -c feature origin/feature

# Set tracking for existing branch
git branch -u origin/feature
git branch --set-upstream-to=origin/feature

# View tracking branches
git branch -vv
```

---

<div align="center">

## 🔍 Viewing History

</div>

### Git Log 📜

```bash
# ═══════════════════════════════════════════
# Basic Log
# ═══════════════════════════════════════════

# Full log
git log

# One line per commit
git log --oneline

# Last 5 commits
git log -5
git log -n 5

# Graph view
git log --graph --oneline --all --decorate

# ═══════════════════════════════════════════
# Formatted Log
# ═══════════════════════════════════════════

# Custom format
git log --pretty=format:"%h - %an, %ar : %s"

# Beautiful log (add to aliases)
git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit

# With statistics
git log --stat

# With diffs
git log -p
git log --patch

# ═══════════════════════════════════════════
# Filter Log
# ═══════════════════════════════════════════

# By author
git log --author="MrDib"

# By date
git log --since="2 weeks ago"
git log --after="2024-01-01"
git log --before="2024-12-31"

# By commit message
git log --grep="fix"

# By file
git log -- filename.txt

# By content (find when text was added/removed)
git log -S "function_name"

# Commits between dates
git log --since="2024-01-01" --until="2024-12-31"

# Commits not in other branch
git log main..feature

# ═══════════════════════════════════════════
# Show Specific Commit
# ═══════════════════════════════════════════

# Show commit details
git show abc1234

# Show file at specific commit
git show abc1234:path/to/file.txt

# Show changes introduced by commit
git show abc1234

# ═══════════════════════════════════════════
# Shortlog
# ═══════════════════════════════════════════

# Summary by author
git shortlog

# Count commits per author
git shortlog -sn

# All authors
git shortlog -sn --all
```

---

### Git Diff 📊

```bash
# ═══════════════════════════════════════════
# View Changes
# ═══════════════════════════════════════════

# Changes in working directory
git diff

# Changes in staging area
git diff --staged
git diff --cached

# Changes between branches
git diff main..feature

# Changes between commits
git diff abc1234 def5678

# Changes in specific file
git diff filename.txt

# ═══════════════════════════════════════════
# Formatted Diff
# ═══════════════════════════════════════════

# Word diff
git diff --word-diff

# Stat summary
git diff --stat

# Name only
git diff --name-only

# Name and status
git diff --name-status

# ═══════════════════════════════════════════
# Compare with Remote
# ═══════════════════════════════════════════

# Compare with remote branch
git diff origin/main

# Compare local with remote current branch
git diff @{upstream}

# ═══════════════════════════════════════════
# Difftool
# ═══════════════════════════════════════════

# Open configured diff tool
git difftool

# Diff specific commits in tool
git difftool abc1234 def5678
```

---

### Git Blame 👀

```bash
# ═══════════════════════════════════════════
# See Who Changed What
# ═══════════════════════════════════════════

# Show who modified each line
git blame filename.txt

# Show with email
git blame -e filename.txt

# Show specific lines
git blame -L 10,20 filename.txt

# Show with commit details
git blame -c filename.txt

# ═══════════════════════════════════════════
# Interactive Blame (in VS Code)
# ═══════════════════════════════════════════

# GitLens extension shows inline blame
# Hover over any line to see:
# - Author
# - Date
# - Commit message
```

---

<div align="center">

## ↩️ Undoing Changes

</div>

### Reset & Restore ⏮️

```bash
# ═══════════════════════════════════════════
# Reset Modes
# ═══════════════════════════════════════════

# Soft reset (keep changes staged)
git reset --soft HEAD~1

# Mixed reset (keep changes unstaged) - DEFAULT
git reset HEAD~1
git reset --mixed HEAD~1

# Hard reset (discard all changes) ⚠️
git reset --hard HEAD~1

# Reset to specific commit
git reset --hard abc1234

# Reset specific file
git reset HEAD filename.txt

# ═══════════════════════════════════════════
# Restore Files
# ═══════════════════════════════════════════

# Restore file from staging
git restore --staged filename.txt

# Restore file in working directory
git restore filename.txt

# Restore from specific commit
git restore --source=abc1234 filename.txt

# Restore all files
git restore .

# ═══════════════════════════════════════════
# Revert Commits
# ═══════════════════════════════════════════

# Revert specific commit (creates new commit)
git revert abc1234

# Revert without committing
git revert --no-commit abc1234

# Revert multiple commits
git revert abc1234..def5678

# Revert merge commit
git revert -m 1 abc1234

# ═══════════════════════════════════════════
# Clean Untracked Files
# ═══════════════════════════════════════════

# Show what would be removed (dry run)
git clean -n

# Remove untracked files
git clean -f

# Remove untracked files and directories
git clean -fd

# Remove ignored files too
git clean -fdx

# Interactive clean
git clean -i
```

---

### Recovering Lost Work 🔄

```bash
# ═══════════════════════════════════════════
# Reflog - Your Safety Net
# ═══════════════════════════════════════════

# View all operations
git reflog

# Reflog for specific branch
git reflog show main

# Find lost commit
git reflog | grep "commit message"

# Recover commit
git checkout abc1234
git branch recovered-branch

# Reset to previous state
git reset --hard HEAD@{2}

# ═══════════════════════════════════════════
# Recover Deleted Branch
# ═══════════════════════════════════════════

# Find commit hash
git reflog | grep branch-name

# Recreate branch
git checkout -b branch-name abc1234

# ═══════════════════════════════════════════
# Fsck - Find Dangling Objects
# ═══════════════════════════════════════════

# Find lost commits
git fsck --lost-found

# Show dangling commits
git fsck --unreachable --no-reflogs

# View dangling commit
git show abc1234
```

---

<div align="center">

## 🔧 Advanced Techniques

</div>

### Git Tags 🏷️

```bash
# ═══════════════════════════════════════════
# List Tags
# ═══════════════════════════════════════════

# List all tags
git tag

# List with pattern
git tag -l "v1.*"

# List with annotations
git tag -n

# ═══════════════════════════════════════════
# Create Tags
# ═══════════════════════════════════════════

# Lightweight tag (pointer to commit)
git tag v1.0.0

# Annotated tag (recommended - full object)
git tag -a v1.0.0 -m "Release version 1.0.0"

# Tag specific commit
git tag -a v1.0.0 abc1234 -m "Release 1.0.0"

# Tag with detailed message
git tag -a v1.0.0 -m "Release 1.0.0

Features:
- User authentication
- Dashboard
- Settings page

Bug fixes:
- Fixed login issue
- Resolved memory leak"

# ═══════════════════════════════════════════
# Push Tags
# ═══════════════════════════════════════════

# Push specific tag
git push origin v1.0.0

# Push all tags
git push --tags
git push origin --tags

# ═══════════════════════════════════════════
# Checkout Tags
# ═══════════════════════════════════════════

# Checkout tag (detached HEAD)
git checkout v1.0.0

# Create branch from tag
git checkout -b version-1.0 v1.0.0

# ═══════════════════════════════════════════
# Delete Tags
# ═══════════════════════════════════════════

# Delete local tag
git tag -d v1.0.0

# Delete remote tag
git push origin --delete v1.0.0
git push origin :refs/tags/v1.0.0

# ═══════════════════════════════════════════
# Show Tag Info
# ═══════════════════════════════════════════

# Show tag details
git show v1.0.0

# List tags with commit info
git show-ref --tags
```

---

### Submodules 📦

```bash
# ═══════════════════════════════════════════
# Add Submodule
# ═══════════════════════════════════════════

# Add submodule
git submodule add https://github.com/user/repo.git path/to/submodule

# Add with specific branch
git submodule add -b main https://github.com/user/repo.git path/to/submodule

# ═══════════════════════════════════════════
# Clone with Submodules
# ═══════════════════════════════════════════

# Clone and initialize submodules
git clone --recurse-submodules https://github.com/user/repo.git

# Or after cloning
git clone https://github.com/user/repo.git
git submodule init
git submodule update

# ═══════════════════════════════════════════
# Update Submodules
# ═══════════════════════════════════════════

# Update all submodules
git submodule update --remote

# Update specific submodule
git submodule update --remote path/to/submodule

# Update and merge changes
git submodule update --remote --merge

# Update and rebase
git submodule update --remote --rebase

# ═══════════════════════════════════════════
# Submodule Status
# ═══════════════════════════════════════════

# Show submodule status
git submodule status

# Show submodule details
git submodule

# ═══════════════════════════════════════════
# Remove Submodule
# ═══════════════════════════════════════════

# 1. Remove from .gitmodules
git config -f .gitmodules --remove-section submodule.path/to/submodule

# 2. Remove from .git/config
git config -f .git/config --remove-section submodule.path/to/submodule

# 3. Remove files
git rm --cached path/to/submodule
rm -rf path/to/submodule

# 4. Remove from .git/modules
rm -rf .git/modules/path/to/submodule

# 5. Commit changes
git commit -m "Remove submodule"
```

---

### Git Worktree 🌲

```bash
# ═══════════════════════════════════════════
# Multiple Working Trees
# ═══════════════════════════════════════════

# List worktrees
git worktree list

# Add new worktree
git worktree add ../project-feature feature-branch

# Add worktree with new branch
git worktree add -b new-feature ../project-new-feature

# Add worktree for existing branch
git worktree add ../project-hotfix hotfix/security-patch

# ═══════════════════════════════════════════
# Use Cases
# ═══════════════════════════════════════════

# Work on multiple branches simultaneously
# project/           - main codebase on main
# project-feature/   - same repo on feature branch
# project-hotfix/    - same repo on hotfix branch

# ═══════════════════════════════════════════
# Remove Worktree
# ═══════════════════════════════════════════

# Remove worktree
git worktree remove ../project-feature

# Prune deleted worktrees
git worktree prune

# ═══════════════════════════════════════════
# Move Worktree
# ═══════════════════════════════════════════

git worktree move ../project-feature ../new-location
```

---

### Git Archive 📦

```bash
# ═══════════════════════════════════════════
# Create Archive
# ═══════════════════════════════════════════

# Create zip archive
git archive --format=zip --output=project.zip HEAD

# Create tar.gz archive
git archive --format=tar.gz --output=project.tar.gz HEAD

# Archive specific branch
git archive --format=zip --output=release.zip main

# Archive specific commit
git archive --format=zip --output=snapshot.zip abc1234

# Archive with prefix
git archive --format=zip --prefix=project/ --output=project.zip HEAD

# Archive specific directory
git archive --format=zip --output=docs.zip HEAD:docs/

# ═══════════════════════════════════════════
# Archive for Release
# ═══════════════════════════════════════════

# Create release archive with version
git archive --format=tar.gz --prefix=myapp-1.0.0/ --output=myapp-1.0.0.tar.gz v1.0.0
```

---

### Git Hooks 🪝

```bash
# ═══════════════════════════════════════════
# Hook Locations
# ═══════════════════════════════════════════

# Hooks directory
.git/hooks/

# Sample hooks (remove .sample to activate)
.git/hooks/pre-commit.sample
.git/hooks/commit-msg.sample
.git/hooks/pre-push.sample

# ═══════════════════════════════════════════
# Client-Side Hooks
# ═══════════════════════════════════════════

# pre-commit - Before commit
# commit-msg - Validate commit message
# post-commit - After commit
# pre-rebase - Before rebase
# post-merge - After merge
# pre-push - Before push

# ═══════════════════════════════════════════
# Example: Pre-commit Hook
# ═══════════════════════════════════════════

# .git/hooks/pre-commit
#!/bin/sh

echo "Running pre-commit checks..."

# Run tests
npm test
if [ $? -ne 0 ]; then
    echo "Tests failed! Commit aborted."
    exit 1
fi

# Run linter
npm run lint
if [ $? -ne 0 ]; then
    echo "Linting failed! Commit aborted."
    exit 1
fi

echo "All checks passed!"
exit 0

# Make executable
chmod +x .git/hooks/pre-commit

# ═══════════════════════════════════════════
# Example: Commit Message Hook
# ═══════════════════════════════════════════

# .git/hooks/commit-msg
#!/bin/sh

commit_msg_file=$1
commit_msg=$(cat "$commit_msg_file")

# Check for conventional commit format
if ! echo "$commit_msg" | grep -qE "^(feat|fix|docs|style|refactor|test|chore)(\(.+\))?: .+"; then
    echo "Error: Commit message must follow conventional commits format"
    echo "Example: feat(auth): add login functionality"
    exit 1
fi

exit 0

# Make executable
chmod +x .git/hooks/commit-msg

# ═══════════════════════════════════════════
# Using Husky (Recommended)
# ═══════════════════════════════════════════

# Install Husky
npm install --save-dev husky

# Initialize
npx husky install

# Add pre-commit hook
npx husky add .husky/pre-commit "npm test"

# Add commit-msg hook
npx husky add .husky/commit-msg 'npx --no -- commitlint --edit "$1"'

# Hooks are now version controlled!
```

---

### Git Attributes 📝

```bash
# ═══════════════════════════════════════════
# .gitattributes File
# ═══════════════════════════════════════════

# Line ending handling
* text=auto
*.txt text
*.jpg binary
*.png binary

# Language-specific
*.js text eol=lf
*.css text eol=lf
*.html text eol=lf
*.sh text eol=lf
*.bat text eol=crlf

# Diff drivers
*.json diff=json
*.md diff=markdown

# Merge drivers
package-lock.json merge=ours
yarn.lock merge=ours

# Export ignore (for git archive)
.gitattributes export-ignore
.gitignore export-ignore
.github export-ignore
tests/ export-ignore

# ═══════════════════════════════════════════
# Custom Diff Drivers
# ═══════════════════════════════════════════

# .gitattributes
*.json diff=json

# .git/config
[diff "json"]
    textconv = python -m json.tool
```

---

<div align="center">

## 🚨 Troubleshooting

</div>

### Common Issues & Solutions 🔧

```bash
# ═══════════════════════════════════════════
# Issue: Merge Conflicts
# ═══════════════════════════════════════════

# Check conflicted files
git status

# View conflict
git diff

# Abort merge
git merge --abort

# Use theirs for all conflicts
git checkout --theirs .

# Use ours for all conflicts
git checkout --ours .

# ═══════════════════════════════════════════
# Issue: Accidentally Committed to Wrong Branch
# ═══════════════════════════════════════════

# Move commits to new branch
git branch new-branch
git reset --hard HEAD~3
git checkout new-branch

# ═══════════════════════════════════════════
# Issue: Need to Undo Last Commit
# ═══════════════════════════════════════════

# Undo commit, keep changes
git reset --soft HEAD~1

# Undo commit, discard changes
git reset --hard HEAD~1

# Undo pushed commit (creates new commit)
git revert HEAD
git push

# ═══════════════════════════════════════════
# Issue: Accidentally Deleted Branch
# ═══════════════════════════════════════════

# Find deleted branch commit
git reflog

# Restore branch
git checkout -b recovered-branch abc1234

# ═══════════════════════════════════════════
# Issue: Committed Sensitive Data
# ═══════════════════════════════════════════

# Remove from last commit
git rm --cached sensitive-file.txt
echo "sensitive-file.txt" >> .gitignore
git commit --amend --no-edit

# Remove from all history
brew install bfg
bfg --delete-files sensitive-file.txt
git reflog expire --expire=now --all
git gc --prune=now --aggressive

# Force push (⚠️ coordinate with team!)
git push --force

# ═══════════════════════════════════════════
# Issue: Large Files in History
# ═══════════════════════════════════════════

# Find large files
git rev-list --objects --all | \
  git cat-file --batch-check='%(objecttype) %(objectname) %(objectsize) %(rest)' | \
  sed -n 's/^blob //p' | \
  sort --numeric-sort --key=2 | \
  tail -10

# Remove with BFG
bfg --strip-blobs-bigger-than 10M
git reflog expire --expire=now --all
git gc --prune=now --aggressive

# ═══════════════════════════════════════════
# Issue: Detached HEAD State
# ═══════════════════════════════════════════

# Save changes by creating branch
git checkout -b temp-branch

# Or discard and return to branch
git checkout main

# ═══════════════════════════════════════════
# Issue: Can't Push (Behind Remote)
# ═══════════════════════════════════════════

# Pull with rebase
git pull --rebase

# Or fetch and rebase manually
git fetch origin
git rebase origin/main

# ═══════════════════════════════════════════
# Issue: Authentication Failed
# ═══════════════════════════════════════════

# Update credentials (macOS)
git credential-osxkeychain erase
# Then push again to re-authenticate

# Switch to SSH
git remote set-url origin git@github.com:username/repo.git

# Generate SSH key
ssh-keygen -t ed25519 -C "your_email@example.com"
# Add to GitHub: Settings → SSH Keys

# ═══════════════════════════════════════════
# Issue: Repository Too Large
# ═══════════════════════════════════════════

# Find large objects
git gc
git count-objects -vH

# Clean up
git gc --aggressive --prune=now

# Reduce clone size
git clone --depth 1 https://github.com/user/repo.git

# ═══════════════════════════════════════════
# Issue: Corrupt Repository
# ═══════════════════════════════════════════

# Check for issues
git fsck --full

# Try to recover
git gc --aggressive

# Last resort: re-clone
mv .git .git-backup
git clone https://github.com/user/repo.git temp
mv temp/.git .
rm -rf temp
```

---

### Git Performance Tips ⚡

```bash
# ═══════════════════════════════════════════
# Speed Up Git Operations
# ═══════════════════════════════════════════

# Enable file system monitor
git config core.fsmonitor true

# Enable parallel operations
git config submodule.fetchJobs 8

# Enable commit graph
git config core.commitGraph true
git commit-graph write --reachable

# Use sparse checkout
git sparse-checkout init
git sparse-checkout set path/to/important/dir

# Shallow clone
git clone --depth 1 https://github.com/user/repo.git

# Partial clone (Git 2.22+)
git clone --filter=blob:none https://github.com/user/repo.git

# ═══════════════════════════════════════════
# Maintenance
# ═══════════════════════════════════════════

# Run maintenance
git maintenance run

# Enable background maintenance
git maintenance start

# Aggressive cleanup
git gc --aggressive --prune=now

# Verify repository
git fsck
```

---

<div align="center">

## 💡 Best Practices

</div>

### Commit Best Practices ✅

```bash
# ═══════════════════════════════════════════
# Good Commit Messages
# ═══════════════════════════════════════════

# ✅ DO: Write clear, descriptive messages
git commit -m "feat: add user authentication with JWT"

# ❌ DON'T: Vague messages
git commit -m "update stuff"

# ✅ DO: Use conventional commits
feat: add new feature
fix: fix bug
docs: update documentation
style: format code
refactor: refactor code
test: add tests
chore: update dependencies

# ✅ DO: Use imperative mood
"Add feature" not "Added feature"
"Fix bug" not "Fixed bug"

# ✅ DO: Limit first line to 50 characters
# ✅ DO: Separate subject from body
# ✅ DO: Explain what and why, not how

git commit -m "feat: add password reset functionality

Users can now reset their password via email.
Implements security best practices with:
- Token expiration (1 hour)
- One-time use tokens
- Secure random token generation

Closes #123"

# ═══════════════════════════════════════════
# Commit Frequency
# ═══════════════════════════════════════════

# ✅ DO: Commit often (small, logical changes)
git commit -m "feat: add login form"
git commit -m "feat: add login validation"
git commit -m "feat: add login API integration"

# ❌ DON'T: Large, monolithic commits
git commit -m "add entire authentication system"

# ✅ DO: Each commit should be atomic
# One logical change per commit

# ═══════════════════════════════════════════
# What to Commit
# ═══════════════════════════════════════════

# ✅ DO: Commit source code
# ✅ DO: Commit configuration files
# ✅ DO: Commit documentation

# ❌ DON'T: Commit build artifacts
# ❌ DON'T: Commit dependencies (node_modules)
# ❌ DON'T: Commit sensitive data (.env files)
# ❌ DON'T: Commit IDE settings
# ❌ DON'T: Commit OS files (.DS_Store)

# Use .gitignore!
```

---

### Branch Best Practices 🌿

```bash
# ═══════════════════════════════════════════
# Branch Naming
# ═══════════════════════════════════════════

# ✅ DO: Use descriptive names
feature/user-authentication
bugfix/login-redirect-issue
hotfix/security-vulnerability
refactor/database-optimization

# ❌ DON'T: Generic names
feature/stuff
bugfix/fix
update

# ✅ DO: Use prefixes
feature/    - New features
bugfix/     - Bug fixes
hotfix/     - Urgent production fixes
release/    - Release preparation
docs/       - Documentation
test/       - Testing
refactor/   - Code refactoring

# ═══════════════════════════════════════════
# Branch Management
# ═══════════════════════════════════════════

# ✅ DO: Keep branches short-lived
# Merge within 1-2 days

# ✅ DO: Delete merged branches
git branch -d feature/completed-feature

# ✅ DO: Keep main/develop clean
# Only merge reviewed code

# ✅ DO: Protect important branches
# Enable branch protection rules on GitHub

# ✅ DO: Sync with main regularly
git checkout feature-branch
git rebase main

# ❌ DON'T: Rebase public branches
# ❌ DON'T: Force push to shared branches
```

---

### Collaboration Best Practices 🤝

```bash
# ═══════════════════════════════════════════
# Working with Team
# ═══════════════════════════════════════════

# ✅ DO: Pull before starting work
git pull origin main

# ✅ DO: Create feature branches
git checkout -b feature/my-feature

# ✅ DO: Push regularly
git push -u origin feature/my-feature

# ✅ DO: Open pull requests early
# Get feedback early

# ✅ DO: Review code thoroughly
# Check functionality, style, tests

# ✅ DO: Respond to review comments
# Address feedback promptly

# ✅ DO: Keep PRs small
# Easier to review, faster to merge

# ✅ DO: Write tests
# Ensure code quality

# ✅ DO: Update documentation
# Keep README current

# ═══════════════════════════════════════════
# Communication
# ═══════════════════════════════════════════

# ✅ DO: Link issues in commits
git commit -m "fix: resolve login issue

Fixes #123"

# ✅ DO: Use PR templates
# Consistent information

# ✅ DO: Add meaningful PR descriptions
# Context helps reviewers

# ✅ DO: Use draft PRs for work in progress
# Show progress, get early feedback
```

---

### Security Best Practices 🔒

```bash
# ═══════════════════════════════════════════
# Protecting Sensitive Data
# ═══════════════════════════════════════════

# ✅ DO: Use .gitignore
echo ".env" >> .gitignore
echo "*.key" >> .gitignore
echo "secrets.yaml" >> .gitignore

# ✅ DO: Use environment variables
# Not hardcoded secrets

# ✅ DO: Scan for secrets
# Use tools like git-secrets, truffleHog

# Install git-secrets
brew install git-secrets

# Scan repository
git secrets --scan

# ✅ DO: Use .env.example
# Show required variables without values

# .env.example
DATABASE_URL=your_database_url_here
API_KEY=your_api_key_here

# ❌ DON'T: Commit credentials
# ❌ DON'T: Commit API keys
# ❌ DON'T: Commit private keys
# ❌ DON'T: Commit passwords

# ═══════════════════════════════════════════
# Signing Commits
# ═══════════════════════════════════════════

# Generate GPG key
gpg --gen-key

# List keys
gpg --list-secret-keys --keyid-format=long

# Configure Git
git config --global user.signingkey YOUR_KEY_ID
git config --global commit.gpgsign true

# Sign commits
git commit -S -m "Signed commit"

# Verify signature
git log --show-signature
```

---

<div align="center">

## 🎓 Resources & Learning

</div>

### Essential Resources 📚

```
📘 Official Documentation
   Git Documentation: https://git-scm.com/doc
   Pro Git Book (free): https://git-scm.com/book
   Git Reference: https://git-scm.com/docs

📗 Interactive Learning
   Learn Git Branching: https://learngitbranching.js.org/
   Git Immersion: http://gitimmersion.com/
   GitHub Learning Lab: https://lab.github.com/
   Visualizing Git: https://git-school.github.io/visualizing-git/

📙 Cheat Sheets
   GitHub Git Cheat Sheet: https://education.github.com/git-cheat-sheet-education.pdf
   Atlassian Git Cheat Sheet: https://www.atlassian.com/git/tutorials/atlassian-git-cheatsheet
   GitLab Git Cheat Sheet: https://about.gitlab.com/images/press/git-cheat-sheet.pdf

🎥 Video Tutorials
   Git & GitHub for Beginners (freeCodeCamp)
   Advanced Git Tutorial (The Net Ninja)
   Git Tutorial for Beginners (Programming with Mosh)

📚 Books
   "Pro Git" by Scott Chacon & Ben Straub (free online)
   "Git for Teams" by Emma Jane Hogbin Westby
   "Version Control with Git" by Jon Loeliger

🛠️ Tools
   GitKraken: https://www.gitkraken.com/
   Sourcetree: https://www.sourcetreeapp.com/
   GitHub Desktop: https://desktop.github.com/
   Fork: https://git-fork.com/
   Tower: https://www.git-tower.com/

🌐 Communities
   Stack Overflow: https://stackoverflow.com/questions/tagged/git
   Reddit r/git: https://www.reddit.com/r/git/
   Git Discord: https://discord.gg/git

🧪 Practice
   Git Katas: https://github.com/eficode-academy/git-katas
   Oh Shit, Git!: https://ohshitgit.com/
   Explain Git with D3: https://onlywei.github.io/explain-git-with-d3/
```

---

### Git Command Quick Reference 📋

```bash
# ═══════════════════════════════════════════
# Setup & Config
# ═══════════════════════════════════════════
git config --global user.name "Your Name"
git config --global user.email "email@example.com"
git config --list

# ═══════════════════════════════════════════
# Create & Clone
# ═══════════════════════════════════════════
git init
git clone <url>

# ═══════════════════════════════════════════
# Basic Commands
# ═══════════════════════════════════════════
git status
git add <file>
git add .
git commit -m "message"
git commit -am "message"
git push
git pull

# ═══════════════════════════════════════════
# Branching
# ═══════════════════════════════════════════
git branch
git branch <name>
git checkout <branch>
git checkout -b <branch>
git switch <branch>
git switch -c <branch>
git merge <branch>
git branch -d <branch>

# ═══════════════════════════════════════════
# Remote
# ═══════════════════════════════════════════
git remote -v
git remote add origin <url>
git fetch
git pull
git push
git push -u origin <branch>

# ═══════════════════════════════════════════
# History
# ═══════════════════════════════════════════
git log
git log --oneline
git log --graph
git diff
git show <commit>

# ═══════════════════════════════════════════
# Undo
# ═══════════════════════════════════════════
git reset HEAD <file>
git reset --soft HEAD~1
git reset --hard HEAD~1
git revert <commit>
git restore <file>
git restore --staged <file>

# ═══════════════════════════════════════════
# Stash
# ═══════════════════════════════════════════
git stash
git stash save "message"
git stash list
git stash pop
git stash apply
git stash drop

# ═══════════════════════════════════════════
# Tags
# ═══════════════════════════════════════════
git tag
git tag -a v1.0 -m "message"
git push --tags
git tag -d <tag>
```

---

### Useful Git Aliases 🔗

```bash
# ═══════════════════════════════════════════
# Add to ~/.gitconfig
# ═══════════════════════════════════════════

[alias]
    # Status
    st = status -sb

    # Add
    a = add
    aa = add .

    # Commit
    cm = commit -m
    cam = commit -am
    amend = commit --amend --no-edit

    # Checkout
    co = checkout
    cob = checkout -b
    com = checkout main

    # Branch
    br = branch
    brd = branch -d

    # Log
    lg = log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
    ll = log --oneline
    last = log -1 HEAD

    # Diff
    df = diff
    dfs = diff --staged

    # Remote
    pu = push
    puf = push --force-with-lease
    pl = pull

    # Undo
    undo = reset --soft HEAD~1
    unstage = reset HEAD

    # Cleanup
    cleanup = !git branch --merged | grep -v '\\*\\|main\\|develop' | xargs -n 1 git branch -d

    # Aliases
    aliases = config --get-regexp ^alias\\.
```

---

<div align="center">

**Built with 🎯 by MrDib, for developers**

_May your commits be clean and your merges be smooth!_ 🚀

**Happy Git-ing!** ✨

</div>
