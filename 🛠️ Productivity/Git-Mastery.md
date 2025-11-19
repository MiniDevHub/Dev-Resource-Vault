<div align="center">

# 🔥 Git Mastery - Level Up Your Version Control

### _Because `git push --force` on main branch is how villains are born_ 😈

![Git](https://img.shields.io/badge/Git-Master-orange?style=for-the-badge&logo=git)
![Level](https://img.shields.io/badge/Level-Expert-purple?style=for-the-badge)

</div>

---

<div align="center">

## 🎯 Git Fundamentals Refresher

</div>

### Essential Commands (The Daily Drivers) 🚗

```bash
# Initialize & Clone
git init                          # Start new repo
git clone <url>                   # Clone existing repo
git clone --depth=1 <url>         # Shallow clone (faster!)

# Basic Operations
git add .                         # Stage all changes
git add -p                        # Interactive staging
git commit -m "message"           # Commit with message
git commit -am "message"          # Add + commit (tracked files only)
git commit --amend                # Modify last commit
git commit --amend --no-edit      # Amend without changing message

# Branching
git branch                        # List branches
git branch <name>                 # Create branch
git checkout <branch>             # Switch branch
git checkout -b <branch>          # Create + switch
git switch <branch>               # Modern way to switch
git switch -c <branch>            # Modern create + switch

# Remote Operations
git remote -v                     # List remotes
git fetch                         # Download changes
git pull                          # Fetch + merge
git push                          # Upload changes
git push -u origin <branch>       # Set upstream + push
```

---

<div align="center">

## 🚀 Advanced Git Techniques

</div>

### Interactive Rebase (Time Travel) ⏰

```bash
# Interactive rebase last 3 commits
git rebase -i HEAD~3

# Commands in interactive mode:
# p, pick = use commit
# r, reword = edit commit message
# e, edit = stop for amending
# s, squash = meld into previous
# f, fixup = like squash but discard message
# x, exec = run command
# d, drop = remove commit

# Example: Squash last 3 commits
git rebase -i HEAD~3
# Change 'pick' to 'squash' for commits 2 & 3
# Save and write new commit message

# Abort rebase if things go wrong
git rebase --abort

# Continue after resolving conflicts
git rebase --continue
```

### Cherry-Picking (Surgical Commits) 🍒

```bash
# Pick specific commit to current branch
git cherry-pick <commit-hash>

# Pick multiple commits
git cherry-pick <hash1> <hash2> <hash3>

# Pick range of commits
git cherry-pick <older-hash>..<newer-hash>

# Cherry-pick without committing
git cherry-pick -n <commit-hash>

# Cherry-pick with edit
git cherry-pick -e <commit-hash>
```

### Stashing (Your Safety Net) 🥅

```bash
# Basic stash
git stash                        # Save changes
git stash pop                    # Apply and remove
git stash apply                  # Apply but keep

# Advanced stash
git stash save "WIP: feature X"  # Named stash
git stash list                   # Show all stashes
git stash show -p stash@{1}      # Show specific stash diff
git stash branch <name>          # Create branch from stash

# Partial stash
git stash -p                     # Interactive stash
git stash -- file1.js file2.js   # Stash specific files

# Include untracked files
git stash -u                     # Include untracked
git stash -a                     # Include ignored files too

# Clear stashes
git stash drop stash@{1}         # Drop specific
git stash clear                  # Drop all (careful!)
```

---

<div align="center">

## 🔍 Git Investigation Tools

</div>

### Git Blame & History (Detective Mode) 🕵️

```bash
# Who wrote this line?
git blame <file>                 # Show line-by-line authorship
git blame -L 10,20 <file>        # Blame specific lines
git blame -w <file>              # Ignore whitespace changes
git blame -C <file>              # Detect moved/copied lines

# Better blame with GUI
git gui blame <file>             # Visual blame

# History exploration
git log --oneline --graph --all  # Visual branch history
git log --follow <file>          # File history (including renames)
git log -p <file>                # File history with diffs
git log --grep="bugfix"          # Search commit messages
git log --author="MrDib"         # Commits by author
git log --since="2 weeks ago"    # Recent commits
git log --stat                   # Show file changes summary

# Find deleted file
git log --all --full-history -- <path/to/file>

# Search code history
git log -S "function_name"       # Find when code was added/removed
git log -G "regex"               # Search with regex
```

### Git Bisect (Binary Search for Bugs) 🐛

```bash
# Start bisect
git bisect start
git bisect bad                   # Current commit is bad
git bisect good <commit>         # Known good commit

# Git will checkout commits for you to test
# After testing each:
git bisect good                  # If commit is good
git bisect bad                   # If commit is bad

# Git will find the first bad commit!

# End bisect
git bisect reset

# Automated bisect with script
git bisect start
git bisect bad HEAD
git bisect good <commit>
git bisect run npm test          # Auto-run tests
```

---

<div align="center">

## 🏗️ Git Workflows

</div>

### GitFlow Workflow 🌊

```bash
# Main branches:
# - main/master: production code
# - develop: integration branch

# Feature development
git checkout develop
git checkout -b feature/awesome-feature
# ... make changes ...
git checkout develop
git merge --no-ff feature/awesome-feature
git branch -d feature/awesome-feature

# Release
git checkout -b release/1.2.0 develop
# ... final fixes ...
git checkout main
git merge --no-ff release/1.2.0
git tag -a v1.2.0 -m "Version 1.2.0"
git checkout develop
git merge --no-ff release/1.2.0

# Hotfix
git checkout -b hotfix/fix-critical main
# ... fix bug ...
git checkout main
git merge --no-ff hotfix/fix-critical
git tag -a v1.2.1 -m "Hotfix version 1.2.1"
git checkout develop
git merge --no-ff hotfix/fix-critical
```

### GitHub Flow (Simpler Alternative) 🌟

```bash
# 1. Create feature branch from main
git checkout -b feature/new-feature main

# 2. Make changes and commit
git add .
git commit -m "Add new feature"

# 3. Push branch
git push -u origin feature/new-feature

# 4. Create Pull Request on GitHub

# 5. After review, merge to main
git checkout main
git pull origin main
git merge --no-ff feature/new-feature
git push origin main
```

---

<div align="center">

## 🛠️ Git Configuration & Aliases

</div>

### Powerful Git Aliases 🚀

```bash
# Add to ~/.gitconfig or run git config commands

# Status & Information
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
git config --global alias.visual '!gitk'

# Pretty logs
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"

git config --global alias.ll "log --pretty=format:'%C(yellow)%h%Cred%d %Creset%s%Cblue [%an]' --decorate --numstat"

git config --global alias.tree "log --graph --oneline --all --decorate"

# Useful shortcuts
git config --global alias.amend 'commit --amend --no-edit'
git config --global alias.undo 'reset --soft HEAD~1'
git config --global alias.wip 'add -A && commit -m "WIP"'
git config --global alias.cleanup 'branch --merged | grep -v main | xargs -n 1 git branch -d'

# Advanced aliases
git config --global alias.pushf 'push --force-with-lease'
git config --global alias.conflicts 'diff --name-only --diff-filter=U'
git config --global alias.incoming '!git fetch && git log HEAD..origin/$(git branch --show-current)'
git config --global alias.outgoing '!git log origin/$(git branch --show-current)..HEAD'
```

### Git Configuration Best Practices ⚙️

```bash
# User configuration
git config --global user.name "MrDib"
git config --global user.email "mrdib@example.com"

# Editor configuration
git config --global core.editor "code --wait"  # VSCode
git config --global merge.tool "code"

# Better diffs
git config --global diff.algorithm histogram
git config --global diff.colorMoved zebra

# Useful settings
git config --global pull.rebase true           # Rebase on pull
git config --global rerere.enabled true        # Remember conflict resolutions
git config --global help.autocorrect 1         # Auto-correct typos
git config --global init.defaultBranch main    # Default branch name

# Performance
git config --global core.preloadindex true     # Faster git status
git config --global core.fscache true          # File system cache
git config --global gc.auto 256                # More frequent garbage collection

# Pretty formats
git config --global pretty.changelog "format:* %s (%h)"
git config --global pretty.detailed "format:%C(yellow)%h %Cblue%ad %Cgreen%an%Cred%d %Creset%s"
```

---

<div align="center">

## 🔧 Git Hooks

</div>

### Client-Side Hooks 🎣

```bash
# Location: .git/hooks/

# pre-commit hook example
#!/bin/sh
# .git/hooks/pre-commit

# Run tests before commit
npm test
if [ $? -ne 0 ]; then
  echo "Tests failed! Commit aborted."
  exit 1
fi

# Check for console.log
if git diff --cached | grep -q "console.log"; then
  echo "Warning: console.log found in commit"
  read -p "Continue? (y/n) " -n 1 -r
  echo
  if [[ ! $REPLY =~ ^[Yy]$ ]]; then
    exit 1
  fi
fi

# Run linter
npm run lint
exit $?
```

### Husky (Modern Git Hooks) 🐕

```json
// package.json
{
  "scripts": {
    "prepare": "husky install"
  },
  "devDependencies": {
    "husky": "^8.0.0",
    "lint-staged": "^13.0.0"
  },
  "lint-staged": {
    "*.{js,jsx,ts,tsx}": ["eslint --fix", "prettier --write"],
    "*.{json,md}": ["prettier --write"]
  }
}
```

```bash
# Install husky
npm install --save-dev husky lint-staged
npx husky install

# Add hooks
npx husky add .husky/pre-commit "npx lint-staged"
npx husky add .husky/commit-msg 'npx --no -- commitlint --edit "$1"'
npx husky add .husky/pre-push "npm test"
```

---

<div align="center">

## 🚑 Git Emergency Commands

</div>

### When Things Go Wrong 🔥

```bash
# "Oh no, I committed to the wrong branch!"
git checkout correct-branch
git cherry-pick <commit-hash>
git checkout wrong-branch
git reset --hard HEAD~1

# "I need to undo my last commit but keep changes"
git reset --soft HEAD~1

# "I messed up, take me back to last commit!"
git reset --hard HEAD

# "I accidentally deleted a file"
git checkout HEAD -- <file>

# "I want to completely start over"
git fetch origin
git reset --hard origin/main

# "I committed sensitive data"
# Use BFG Repo Cleaner
brew install bfg
bfg --delete-files secrets.txt
git reflog expire --expire=now --all
git gc --prune=now --aggressive

# "I need to change commit author"
git commit --amend --author="MrDib <mrdib@example.com>"

# "I want to remove a file from all history"
git filter-branch --tree-filter 'rm -rf path/to/file' HEAD

# "I need to recover deleted branch"
git reflog
git checkout -b recovered-branch <commit-hash>

# "Fix detached HEAD state"
git checkout -b temp-branch    # Create branch from current state
git checkout main              # Or switch to existing branch
git merge temp-branch          # If you want to keep changes
```

---

<div align="center">

## 📊 Git Best Practices

</div>

### Commit Message Convention 📝

```bash
# Format: <type>(<scope>): <subject>
#
# <type>:
#   feat: New feature
#   fix: Bug fix
#   docs: Documentation
#   style: Code style (formatting, semicolons, etc)
#   refactor: Code refactoring
#   perf: Performance improvements
#   test: Adding tests
#   chore: Maintenance tasks
#   build: Build system changes
#   ci: CI/CD changes

# Examples:
git commit -m "feat(auth): add Google OAuth login"
git commit -m "fix(api): resolve CORS issue with production URL"
git commit -m "docs(readme): update installation instructions"
git commit -m "style(button): fix hover state colors"
git commit -m "perf(images): implement lazy loading"
git commit -m "test(user): add integration tests for user service"
git commit -m "chore(deps): update dependencies to latest versions"

# With body and footer:
git commit -m "feat(payment): integrate Stripe payment gateway

- Add payment form component
- Implement payment processing service
- Add webhook handlers for payment events

Closes #123
Breaking Change: Payment API endpoint changed from /pay to /payments"
```

### Branch Naming Convention 🌿

```bash
# Feature branches
feature/user-authentication
feature/shopping-cart
feature/JIRA-123-payment-integration

# Bug fixes
bugfix/login-redirect
bugfix/JIRA-456-cart-total

# Hotfixes
hotfix/security-patch
hotfix/payment-processing-error

# Release branches
release/v1.2.0
release/2023-11-sprint

# Other
chore/update-dependencies
docs/api-documentation
test/integration-tests
```

---

<div align="center">

## 🎯 Git Tips & Tricks

</div>

### Productivity Boosters 🚀

```bash
# Quick commit with diff review
git commit -v

# Show word-level diff
git diff --word-diff

# Diff with syntax highlighting
git diff --color-words

# List files changed between branches
git diff --name-only main..feature

# Show commits in branch not in main
git log main..feature

# Find common ancestor
git merge-base branch1 branch2

# Clean up local branches
git branch --merged | grep -v main | xargs -n 1 git branch -d

# Prune remote branches
git remote prune origin

# Archive project
git archive --format=zip --output=project.zip HEAD

# Export patch
git format-patch -1 <commit>

# Apply patch
git apply <patch-file>

# Count commits
git rev-list --count HEAD

# Show file at specific commit
git show <commit>:<file>

# List git aliases
git config --get-regexp alias

# Optimize repository
git gc --aggressive --prune=now
```

---

<div align="center">

## 📚 Git Resources

</div>

### Learning Resources 📖

```
📘 Pro Git Book       → https://git-scm.com/book
   - Official book
   - Free online
   - Comprehensive

🎮 Learn Git Branching → https://learngitbranching.js.org
   - Interactive tutorial
   - Visual learning
   - Practice branching

🎯 Oh My Git!         → https://ohmygit.org
   - Game-based learning
   - Fun approach
   - Visual puzzles

📺 Git Documentation  → https://git-scm.com/docs
   - Official docs
   - Complete reference
   - Man pages
```

### Git GUIs 🖼️

```
🌲 GitKraken         → https://gitkraken.com
   - Beautiful UI
   - Cross-platform
   - Free for public repos

🔷 Sourcetree        → https://sourcetreeapp.com
   - Free GUI
   - By Atlassian
   - Windows/Mac

🦊 GitLens (VSCode)  → VSCode Extension
   - In-editor git
   - Blame annotations
   - History explorer

📊 GitHub Desktop    → https://desktop.github.com
   - Official GitHub app
   - Simple interface
   - Free
```

---

<div align="center">

_Remember: With great git power comes great responsibility. Always think twice before force pushing! 🚀_

</div>
