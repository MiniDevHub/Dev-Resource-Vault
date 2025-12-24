<div align="center">

# 🔀 Git Workflows - Complete Professional Guide

![Git Workflows](https://img.shields.io/badge/Git-Workflows-orange?style=for-the-badge&logo=git)
![Team Collaboration](https://img.shields.io/badge/Team-Collaboration-blue?style=for-the-badge)
![Level](https://img.shields.io/badge/Level-All_Levels-green?style=for-the-badge)

### _Master every Git workflow from solo dev to enterprise teams_ 🚀

**Because messy Git history is a developer's worst nightmare** 😱

</div>

---

## 📚 Table of Contents

- [🌊 Workflow Overview](#-workflow-overview)
- [🎯 Feature Branch Workflow](#-feature-branch-workflow)
- [🔄 Git Flow](#-git-flow)
- [🚀 GitHub Flow](#-github-flow)
- [🦊 GitLab Flow](#-gitlab-flow)
- [⚡ Trunk-Based Development](#-trunk-based-development)
- [🎋 Forking Workflow](#-forking-workflow)
- [📦 Monorepo Workflows](#-monorepo-workflows)
- [🔧 Advanced Techniques](#-advanced-techniques)
- [🏷️ Commit Conventions](#️-commit-conventions)
- [🤝 Code Review](#-code-review)
- [🚀 CI/CD Integration](#-cicd-integration)
- [📋 Release Management](#-release-management)
- [🎯 Real-World Scenarios](#-real-world-scenarios)
- [💡 Pro Tips](#-pro-tips)

---

<div align="center">

## 🌊 Workflow Overview

</div>

### Workflow Comparison Matrix 📊

```bash
# ═══════════════════════════════════════════
# CHOOSING THE RIGHT WORKFLOW
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WORKFLOW COMPARISON                      ║
╚════════════════════════════════════════════════════════════╝
```

<div align="center">

| Workflow           | Team Size | Release Cycle | Complexity     | Environment          | Best For                           |
| ------------------ | --------- | ------------- | -------------- | -------------------- | ---------------------------------- |
| **Feature Branch** | 1-10      | Any           | ⭐ Simple      | Any                  | Most projects, startups            |
| **Git Flow**       | 10-50+    | Scheduled     | ⭐⭐⭐ Complex | Multiple             | Enterprise, versioned releases     |
| **GitHub Flow**    | 1-100+    | Continuous    | ⭐⭐ Moderate  | Production only      | Web apps, SaaS, CD                 |
| **GitLab Flow**    | 5-100+    | Continuous    | ⭐⭐ Moderate  | Multiple             | Staged deployments                 |
| **Trunk-Based**    | 5-1000+   | Continuous    | ⭐⭐ Moderate  | Production + staging | High-velocity teams, microservices |
| **Forking**        | Any       | Any           | ⭐⭐ Moderate  | Any                  | Open source, external contributors |

</div>

```bash
# ═══════════════════════════════════════════
# WORKFLOW SELECTION GUIDE
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WHEN TO USE WHAT                         ║
╚════════════════════════════════════════════════════════════╝

Choose Feature Branch Workflow if:
─────────────────────────────────────────────────────────────
✓ Small to medium team (1-10 developers)
✓ Simple project structure
✓ Flexible release schedule
✓ Want to keep things simple
✓ Team is new to Git workflows

Choose Git Flow if:
─────────────────────────────────────────────────────────────
✓ Scheduled releases (weekly, monthly, quarterly)
✓ Multiple versions in production
✓ Need hotfix capability
✓ Large team with clear roles
✓ Traditional software releases
✓ Desktop/mobile apps with versions

Choose GitHub Flow if:
─────────────────────────────────────────────────────────────
✓ Continuous deployment
✓ Single production environment
✓ Fast-paced development
✓ Web applications
✓ Strong CI/CD pipeline
✓ Can deploy multiple times per day

Choose GitLab Flow if:
─────────────────────────────────────────────────────────────
✓ Multiple deployment environments
✓ Environment-based workflow
✓ Need staging/production separation
✓ Continuous delivery (not deployment)
✓ Complex infrastructure

Choose Trunk-Based Development if:
─────────────────────────────────────────────────────────────
✓ High-velocity team
✓ Strong automated testing
✓ Excellent CI/CD infrastructure
✓ Can integrate daily
✓ Feature flags available
✓ Mature DevOps practices

Choose Forking Workflow if:
─────────────────────────────────────────────────────────────
✓ Open source project
✓ External contributors
✓ Need contribution control
✓ Large community
✓ Security-sensitive projects

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🎯 Feature Branch Workflow

</div>

### Overview 📋

```bash
# ═══════════════════════════════════════════
# FEATURE BRANCH WORKFLOW
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WORKFLOW STRUCTURE                       ║
╚════════════════════════════════════════════════════════════╝

                    main (production)
                      │
                      │  ← feature/login
                      │     │
                      │     │ (work)
                      │     │
                      │  ←──┘ (merge)
                      │
                      │  ← feature/dashboard
                      │     │
                      │     │ (work)
                      │     │
                      │  ←──┘ (merge)
                      │
                      ↓

Key Principles:
─────────────────────────────────────────────────────────────
• main branch is always deployable
• Each feature = separate branch
• Branch from main, merge back to main
• Use pull requests for code review
• Delete branches after merge

Pros:
─────────────────────────────────────────────────────────────
✅ Simple to understand and implement
✅ Flexible - works for any release cycle
✅ Clean separation of features
✅ Easy to review and test features
✅ Safe experimentation

Cons:
─────────────────────────────────────────────────────────────
⚠️ Can become messy without discipline
⚠️ No formal release process
⚠️ Requires good communication
⚠️ Potential for merge conflicts

═══════════════════════════════════════════════════════════
```

---

### Complete Workflow 🔄

```bash
# ═══════════════════════════════════════════
# STEP-BY-STEP FEATURE BRANCH WORKFLOW
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   STEP 1: START FRESH                      ║
╚════════════════════════════════════════════════════════════╝

# Always start from updated main
git checkout main
git pull origin main

# Verify you're on main
git branch --show-current

# Check for uncommitted changes
git status

╔════════════════════════════════════════════════════════════╗
║                   STEP 2: CREATE FEATURE BRANCH            ║
╚════════════════════════════════════════════════════════════╝

# Create and switch to feature branch
git checkout -b feature/user-authentication

# Modern Git syntax (Git 2.23+)
git switch -c feature/user-authentication

# Branch naming conventions:
─────────────────────────────────────────────────────────────
feature/add-user-login              ✅ Good
feature/user-authentication         ✅ Good
bugfix/fix-login-redirect          ✅ Good
hotfix/security-patch              ✅ Good
refactor/optimize-db-queries       ✅ Good
docs/update-api-documentation      ✅ Good
test/add-integration-tests         ✅ Good

my-feature                          ❌ Too vague
fix                                ❌ No context
temp                               ❌ Meaningless
john-branch                        ❌ Based on person

# Include ticket number if using issue tracker:
feature/JIRA-123-add-login         ✅ Perfect
bugfix/GH-456-fix-redirect         ✅ Perfect

╔════════════════════════════════════════════════════════════╗
║                   STEP 3: WORK ON FEATURE                  ║
╚════════════════════════════════════════════════════════════╝

# Make changes to files
# Edit, create, delete files as needed

# Check what changed
git status
git diff

# Stage specific files
git add src/auth/login.js
git add src/auth/login.test.js

# Or stage all changes
git add .

# Commit with descriptive message
git commit -m "feat: add login form component"

# Continue working
git add src/auth/validation.js
git commit -m "feat: add form validation"

git add src/auth/api.js
git commit -m "feat: integrate login API"

git add tests/auth.test.js
git commit -m "test: add authentication tests"

# Commit often! Small, logical commits are better
# Each commit should be a complete thought

╔════════════════════════════════════════════════════════════╗
║                   STEP 4: KEEP BRANCH UPDATED              ║
╚════════════════════════════════════════════════════════════╝

# Fetch latest changes from remote
git fetch origin

# Check if main has new commits
git log HEAD..origin/main --oneline

# Option A: Rebase (recommended for cleaner history)
─────────────────────────────────────────────────────────────
git rebase origin/main

# If conflicts occur:
# 1. Fix conflicts in files
# 2. Stage resolved files
git add .
# 3. Continue rebase
git rebase --continue

# Or abort if needed
git rebase --abort

# Option B: Merge (preserves history)
─────────────────────────────────────────────────────────────
git merge origin/main

# If conflicts occur:
# 1. Fix conflicts in files
# 2. Stage resolved files
git add .
# 3. Complete merge
git commit

# Why keep branch updated?
─────────────────────────────────────────────────────────────
✓ Reduces merge conflicts later
✓ Ensures compatibility with latest changes
✓ Makes final merge easier
✓ Catches integration issues early

# How often to sync?
─────────────────────────────────────────────────────────────
• Daily for active projects
• Before pushing
• After team members merge to main

╔════════════════════════════════════════════════════════════╗
║                   STEP 5: PUSH TO REMOTE                   ║
╚════════════════════════════════════════════════════════════╝

# First push - set upstream
git push -u origin feature/user-authentication

# Subsequent pushes
git push

# After rebase, may need force push
git push --force-with-lease

# ⚠️ NEVER use --force on shared branches!
# ⚠️ Use --force-with-lease instead (safer)

# What's the difference?
─────────────────────────────────────────────────────────────
--force          # Overwrites remote (dangerous!)
--force-with-lease  # Only if remote hasn't changed (safe)

╔════════════════════════════════════════════════════════════╗
║                   STEP 6: CREATE PULL REQUEST              ║
╚════════════════════════════════════════════════════════════╝

# Using GitHub CLI
gh pr create --title "Add user authentication" \
             --body "Implements login functionality with validation"

# Or via web UI:
# 1. Go to GitHub repository
# 2. Click "Compare & pull request" button
# 3. Fill in PR template
# 4. Select reviewers
# 5. Add labels
# 6. Link related issues

# PR Best Practices:
─────────────────────────────────────────────────────────────
✓ Write clear title and description
✓ Link to related issues (Fixes #123)
✓ Add screenshots for UI changes
✓ List testing steps
✓ Keep PRs small (<400 lines ideal)
✓ Request specific reviewers
✓ Add appropriate labels

╔════════════════════════════════════════════════════════════╗
║                   STEP 7: CODE REVIEW                      ║
╚════════════════════════════════════════════════════════════╝

# Address review feedback
git add .
git commit -m "refactor: address PR feedback"
git push

# Multiple review iterations are normal!

# If major changes needed:
git add .
git commit -m "refactor: restructure authentication flow"
git push

# Respond to comments on GitHub
# Mark conversations as resolved when addressed

╔════════════════════════════════════════════════════════════╗
║                   STEP 8: MERGE TO MAIN                    ║
╚════════════════════════════════════════════════════════════╝

# Merge strategies:
─────────────────────────────────────────────────────────────

# 1. Merge Commit (preserves all history)
   GitHub UI: "Create a merge commit"

   Result:
   * Merge pull request #123
   |\
   | * feat: add validation
   | * feat: add login form
   |/
   * Previous commit

# 2. Squash and Merge (clean history)
   GitHub UI: "Squash and merge"

   Result:
   * feat: add user authentication (#123)
   * Previous commit

   ✓ All commits combined into one
   ✓ Cleaner history
   ✓ Easier to revert

# 3. Rebase and Merge (linear history)
   GitHub UI: "Rebase and merge"

   Result:
   * test: add auth tests
   * feat: add validation
   * feat: add login form
   * Previous commit

   ✓ No merge commit
   ✓ Linear history
   ✓ Preserves individual commits

# Recommended: Squash and merge for most projects

╔════════════════════════════════════════════════════════════╗
║                   STEP 9: CLEANUP                          ║
╚════════════════════════════════════════════════════════════╝

# Update local main
git checkout main
git pull origin main

# Delete local feature branch
git branch -d feature/user-authentication

# Delete remote branch (if not auto-deleted)
git push origin --delete feature/user-authentication

# Cleanup stale remote branches
git fetch --prune
git remote prune origin

# Delete all merged local branches
git branch --merged main | grep -v "main" | xargs git branch -d

# Or use alias (add to ~/.gitconfig):
[alias]
    cleanup = "!git branch --merged | grep -v '\\*\\|main\\|develop' | xargs -n 1 git branch -d"

# Usage:
git cleanup

═══════════════════════════════════════════════════════════
```

---

### Advanced Feature Branch Techniques 🎓

```bash
# ═══════════════════════════════════════════
# STACKING FEATURE BRANCHES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   DEPENDENT FEATURES                       ║
╚════════════════════════════════════════════════════════════╝

# Scenario: Feature B depends on Feature A

# Create Feature A
git checkout main
git checkout -b feature/authentication
# ... work on auth ...
git push -u origin feature/authentication
# Open PR for review

# Create Feature B from Feature A
git checkout feature/authentication
git checkout -b feature/user-dashboard
# ... work on dashboard ...
git push -u origin feature/user-dashboard
# Open PR (base: feature/authentication)

# When Feature A is merged:
git checkout feature/user-dashboard
git rebase main
# Update PR base to main
git push --force-with-lease

# ═══════════════════════════════════════════
# LONG-RUNNING FEATURE BRANCHES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   LARGE FEATURES                           ║
╚════════════════════════════════════════════════════════════╝

# For features taking >1 week:

# Create main feature branch
git checkout -b feature/redesign-dashboard

# Create sub-feature branches
git checkout -b feature/redesign-dashboard-header
# ... work ...
git push -u origin feature/redesign-dashboard-header
# PR: merge into feature/redesign-dashboard

git checkout feature/redesign-dashboard
git checkout -b feature/redesign-dashboard-sidebar
# ... work ...
git push -u origin feature/redesign-dashboard-sidebar
# PR: merge into feature/redesign-dashboard

# Keep main feature branch updated
git checkout feature/redesign-dashboard
git rebase main

# Finally merge to main when complete

# ═══════════════════════════════════════════
# FEATURE FLAGS FOR INCOMPLETE FEATURES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   MERGE INCOMPLETE WORK                    ║
╚════════════════════════════════════════════════════════════╝

// config/features.js
export const features = {
  newDashboard: process.env.FEATURE_NEW_DASHBOARD === 'true',
  betaFeatures: process.env.FEATURE_BETA === 'true'
};

// components/Dashboard.js
import { features } from '../config/features';

export function Dashboard() {
  if (features.newDashboard) {
    return <NewDashboard />;
  }
  return <OldDashboard />;
}

# Benefits:
✓ Merge to main frequently
✓ Reduce merge conflicts
✓ Test in production safely
✓ Easy rollback
✓ Gradual rollout

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🔄 Git Flow

</div>

### Overview 📋

```bash
# ═══════════════════════════════════════════
# GIT FLOW WORKFLOW
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   BRANCH STRUCTURE                         ║
╚════════════════════════════════════════════════════════════╝

                main (production)
                  │
                  │  ← release/1.0
                  │     │
            ┌─────┴─────┴───── develop (integration)
            │     │     │         │
            │     │     │         │  ← feature/login
            │     │     │         │     │
            │     │     │         │  ←──┘
            │     │     │         │
            │     │     │         │  ← feature/dashboard
            │     │     │         │     │
            │     │     │         │  ←──┘
            │     │     │      ───┘
            │     │  ←──┘ (release)
            │  ←──┘ (merge)
            │
            │  ← hotfix/1.0.1
            │     │
            └─────┴─────────────→ develop

Branches:
─────────────────────────────────────────────────────────────
main          Production-ready code, tagged releases
develop       Integration branch for next release
feature/*     Individual features (from develop)
release/*     Release preparation (from develop)
hotfix/*      Emergency production fixes (from main)

Workflow Created by:
─────────────────────────────────────────────────────────────
Vincent Driessen (2010)
https://nvie.com/posts/a-successful-git-branching-model/

Best For:
─────────────────────────────────────────────────────────────
✓ Scheduled releases (weekly, monthly, quarterly)
✓ Multiple production versions
✓ Large teams (10-50+ developers)
✓ Traditional software releases
✓ Desktop/mobile applications
✓ Projects with staging environments

Not Ideal For:
─────────────────────────────────────────────────────────────
✗ Continuous deployment
✗ Small teams (<5 developers)
✗ Web apps with daily deploys
✗ Simple projects

═══════════════════════════════════════════════════════════
```

---

### Git Flow Setup & Commands 🔧

```bash
# ═══════════════════════════════════════════
# INSTALL GIT FLOW EXTENSION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   INSTALLATION                             ║
╚════════════════════════════════════════════════════════════╝

# macOS
brew install git-flow-avh

# Linux (Debian/Ubuntu)
sudo apt-get install git-flow

# Linux (Fedora)
sudo dnf install gitflow

# Windows
# Download from: https://github.com/petervanderdoes/gitflow-avh
# Or use Git for Windows (includes git-flow)

# Verify installation
git flow version

# ═══════════════════════════════════════════
# INITIALIZE GIT FLOW
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   FIRST-TIME SETUP                         ║
╚════════════════════════════════════════════════════════════╝

# In your repository
git flow init

# Interactive setup:
─────────────────────────────────────────────────────────────
Which branch should be used for bringing forth production releases?
   - main
Branch name for production releases: [main]

Which branch should be used for integration of the "next release"?
   - develop
Branch name for "next release" development: [develop]

How to name your supporting branch prefixes?
Feature branches? [feature/]
Bugfix branches? [bugfix/]
Release branches? [release/]
Hotfix branches? [hotfix/]
Support branches? [support/]
Version tag prefix? [v]

# Recommended: Accept all defaults by pressing Enter

# What git flow init does:
─────────────────────────────────────────────────────────────
✓ Creates 'develop' branch if it doesn't exist
✓ Switches to 'develop' branch
✓ Configures branch prefixes in .git/config

# ═══════════════════════════════════════════
# GIT FLOW vs MANUAL COMMANDS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   COMMAND COMPARISON                       ║
╚════════════════════════════════════════════════════════════╝

Feature Development:
─────────────────────────────────────────────────────────────
Git Flow:
    git flow feature start my-feature
    git flow feature finish my-feature

Manual:
    git checkout develop
    git checkout -b feature/my-feature
    # ... work ...
    git checkout develop
    git merge --no-ff feature/my-feature
    git branch -d feature/my-feature

Release Preparation:
─────────────────────────────────────────────────────────────
Git Flow:
    git flow release start 1.0.0
    git flow release finish 1.0.0

Manual:
    git checkout develop
    git checkout -b release/1.0.0
    # ... prepare ...
    git checkout main
    git merge --no-ff release/1.0.0
    git tag -a v1.0.0
    git checkout develop
    git merge --no-ff release/1.0.0
    git branch -d release/1.0.0

Hotfix:
─────────────────────────────────────────────────────────────
Git Flow:
    git flow hotfix start 1.0.1
    git flow hotfix finish 1.0.1

Manual:
    git checkout main
    git checkout -b hotfix/1.0.1
    # ... fix ...
    git checkout main
    git merge --no-ff hotfix/1.0.1
    git tag -a v1.0.1
    git checkout develop
    git merge --no-ff hotfix/1.0.1
    git branch -d hotfix/1.0.1

═══════════════════════════════════════════════════════════
```

---

### Complete Git Flow Cycle 🔄

```bash
# ═══════════════════════════════════════════
# STEP-BY-STEP GIT FLOW WORKFLOW
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   PHASE 1: FEATURE DEVELOPMENT             ║
╚════════════════════════════════════════════════════════════╝

# Start new feature
git flow feature start user-authentication

# What happens:
✓ Creates branch: feature/user-authentication
✓ Based on: develop
✓ Switches to: feature/user-authentication

# Work on feature
git add src/auth/login.js
git commit -m "feat: add login component"

git add src/auth/validation.js
git commit -m "feat: add form validation"

git add tests/auth.test.js
git commit -m "test: add authentication tests"

# Push feature branch (for collaboration)
git push -u origin feature/user-authentication

# Collaborate with team members
git pull origin feature/user-authentication
git push origin feature/user-authentication

# Finish feature
git flow feature finish user-authentication

# What happens:
✓ Merges feature/user-authentication into develop
✓ Deletes feature/user-authentication branch locally
✓ Switches to develop branch

# Push develop
git push origin develop

# Delete remote feature branch
git push origin --delete feature/user-authentication

# Alternative: Publish and pull features
─────────────────────────────────────────────────────────────
# Publish feature (push to remote)
git flow feature publish user-authentication

# Pull feature (get from remote)
git flow feature pull origin user-authentication

# Track feature (track remote feature)
git flow feature track user-authentication

╔════════════════════════════════════════════════════════════╗
║                   PHASE 2: MULTIPLE FEATURES               ║
╚════════════════════════════════════════════════════════════╝

# Develop features in parallel
git flow feature start payment-integration
# ... work ...
git flow feature finish payment-integration

git flow feature start user-dashboard
# ... work ...
git flow feature finish user-dashboard

git flow feature start notification-system
# ... work ...
git flow feature finish notification-system

# All features now in develop branch

╔════════════════════════════════════════════════════════════╗
║                   PHASE 3: RELEASE PREPARATION             ║
╚════════════════════════════════════════════════════════════╝

# Start release
git flow release start 2.0.0

# What happens:
✓ Creates branch: release/2.0.0
✓ Based on: develop
✓ Switches to: release/2.0.0

# Prepare release
─────────────────────────────────────────────────────────────
# Update version numbers
echo "2.0.0" > version.txt
git add version.txt
git commit -m "chore: bump version to 2.0.0"

# Update CHANGELOG
cat << 'EOF' > CHANGELOG.md
# Changelog

## [2.0.0] - 2024-01-15

### Added
- User authentication system
- Payment integration
- User dashboard
- Notification system

### Changed
- Improved performance
- Updated dependencies

### Fixed
- Fixed login redirect issue
- Resolved payment timeout
EOF

git add CHANGELOG.md
git commit -m "docs: update changelog for 2.0.0"

# Update documentation
git add docs/
git commit -m "docs: update API documentation"

# Bug fixes allowed during release!
git add src/
git commit -m "fix: resolve last-minute bug"

# Push release branch
git push -u origin release/2.0.0

# Testing phase
─────────────────────────────────────────────────────────────
# QA team tests release/2.0.0 branch
# Fix any bugs found
git add .
git commit -m "fix: critical bug found in testing"
git push

# Finish release
git flow release finish 2.0.0

# What happens:
✓ Merges release/2.0.0 into main
✓ Tags release: v2.0.0
✓ Merges release/2.0.0 into develop
✓ Deletes release/2.0.0 branch locally
✓ Switches to develop

# Enter tag message in editor
v2.0.0

Release 2.0.0
- User authentication
- Payment integration
- User dashboard
- Notification system

# Push everything
git push origin main develop --tags

# Delete remote release branch
git push origin --delete release/2.0.0

╔════════════════════════════════════════════════════════════╗
║                   PHASE 4: HOTFIX (EMERGENCY)              ║
╚════════════════════════════════════════════════════════════╝

# Production bug discovered!
# Start hotfix
git flow hotfix start 2.0.1

# What happens:
✓ Creates branch: hotfix/2.0.1
✓ Based on: main (production code)
✓ Switches to: hotfix/2.0.1

# Fix the critical bug
git add src/payment/gateway.js
git commit -m "fix: critical payment processing bug"

# Update version
echo "2.0.1" > version.txt
git add version.txt
git commit -m "chore: bump version to 2.0.1"

# Update CHANGELOG
cat << 'EOF' >> CHANGELOG.md

## [2.0.1] - 2024-01-16

### Fixed
- Critical payment processing bug

EOF

git add CHANGELOG.md
git commit -m "docs: update changelog for 2.0.1"

# Finish hotfix
git flow hotfix finish 2.0.1

# What happens:
✓ Merges hotfix/2.0.1 into main
✓ Tags release: v2.0.1
✓ Merges hotfix/2.0.1 into develop
✓ Deletes hotfix/2.0.1 branch locally
✓ Switches to develop

# Push everything
git push origin main develop --tags

# Deploy immediately!

╔════════════════════════════════════════════════════════════╗
║                   COMPLETE RELEASE CYCLE                   ║
╚════════════════════════════════════════════════════════════╝

# Week 1-2: Feature Development
git flow feature start feature-a
# ... work ...
git flow feature finish feature-a

git flow feature start feature-b
# ... work ...
git flow feature finish feature-b

# Week 3: Release Preparation
git flow release start 3.0.0
# ... testing & bug fixes ...
git flow release finish 3.0.0

# Production Deployment
git push origin main develop --tags

# Emergency: Hotfix if needed
git flow hotfix start 3.0.1
# ... fix ...
git flow hotfix finish 3.0.1
git push origin main develop --tags

# Continue with new features
git flow feature start feature-c
# ...

═══════════════════════════════════════════════════════════
```

---

### Git Flow Best Practices 💡

```bash
# ═══════════════════════════════════════════
# GIT FLOW BEST PRACTICES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   BRANCH MANAGEMENT                        ║
╚════════════════════════════════════════════════════════════╝

✅ DO:
─────────────────────────────────────────────────────────────
• Keep feature branches short-lived (< 1 week)
• Merge features to develop frequently
• Use pull requests for feature → develop merges
• Test thoroughly on release branches
• Keep main and develop in sync
• Use semantic versioning for tags
• Document all releases in CHANGELOG
• Protect main and develop branches

❌ DON'T:
─────────────────────────────────────────────────────────────
• Never commit directly to main
• Never commit directly to develop (except emergencies)
• Don't create features from main
• Don't leave features unfinished for weeks
• Don't skip release branches
• Don't forget to push tags

╔════════════════════════════════════════════════════════════╗
║                   RELEASE MANAGEMENT                       ║
╚════════════════════════════════════════════════════════════╝

Release Branch Checklist:
─────────────────────────────────────────────────────────────
□ Update version numbers in all files
□ Update CHANGELOG.md
□ Update documentation
□ Run full test suite
□ Perform QA testing
□ Fix any bugs found
□ Update README if needed
□ Build and test artifacts
□ Prepare release notes

Before Finishing Release:
─────────────────────────────────────────────────────────────
□ All tests passing
□ QA sign-off received
□ Documentation updated
□ Release notes prepared
□ Deployment plan ready
□ Rollback plan ready

╔════════════════════════════════════════════════════════════╗
║                   HOTFIX GUIDELINES                        ║
╚════════════════════════════════════════════════════════════╝

When to use hotfix:
─────────────────────────────────────────────────────────────
✓ Critical production bug
✓ Security vulnerability
✓ Data corruption issue
✓ Service outage
✓ Major functionality broken

When NOT to use hotfix:
─────────────────────────────────────────────────────────────
✗ Minor bugs
✗ UI tweaks
✗ Performance improvements
✗ New features
→ Use regular feature/bugfix branches instead

Hotfix Process:
─────────────────────────────────────────────────────────────
1. Identify critical issue in production
2. Start hotfix branch from main
3. Fix issue with minimal changes
4. Test thoroughly
5. Update version (patch number)
6. Finish hotfix (merges to main and develop)
7. Deploy immediately
8. Monitor production

╔════════════════════════════════════════════════════════════╗
║                   VERSIONING STRATEGY                      ║
╚════════════════════════════════════════════════════════════╝

Semantic Versioning: MAJOR.MINOR.PATCH
─────────────────────────────────────────────────────────────
MAJOR version: Breaking changes (2.0.0 → 3.0.0)
  • API changes
  • Remove features
  • Incompatible updates

MINOR version: New features (2.0.0 → 2.1.0)
  • New functionality
  • Backward compatible
  • Feature additions

PATCH version: Bug fixes (2.0.0 → 2.0.1)
  • Bug fixes
  • Security patches
  • Minor improvements

Examples:
─────────────────────────────────────────────────────────────
v1.0.0  → Initial release
v1.1.0  → Add payment feature
v1.1.1  → Fix payment bug
v1.2.0  → Add dashboard
v1.2.1  → Fix dashboard bug
v2.0.0  → Major redesign (breaking changes)

Pre-release versions:
─────────────────────────────────────────────────────────────
v2.0.0-alpha.1
v2.0.0-beta.1
v2.0.0-rc.1
v2.0.0

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🚀 GitHub Flow

</div>

### Overview 📋

```bash
# ═══════════════════════════════════════════
# GITHUB FLOW WORKFLOW
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WORKFLOW STRUCTURE                       ║
╚════════════════════════════════════════════════════════════╝

                main (always deployable)
                  │
                  │  ← feature/add-search
                  │     │ (work)
                  │     │ (deploy to staging)
                  │     │ (test)
                  │  ←──┘ (merge & deploy)
                  │
                  │  ← feature/fix-bug
                  │     │ (work)
                  │     │ (deploy to staging)
                  │     │ (test)
                  │  ←──┘ (merge & deploy)
                  │
                  ↓ (continuous deployment)

Key Principles:
─────────────────────────────────────────────────────────────
1. main branch is ALWAYS deployable
2. Create descriptive feature branches
3. Commit to branch often
4. Open pull request early
5. Deploy branch for testing
6. Merge after review
7. Deploy immediately after merge

Created by: GitHub (for their own workflow)
Used by: GitHub, many tech startups, SaaS companies

Best For:
─────────────────────────────────────────────────────────────
✓ Continuous deployment
✓ Web applications
✓ Single production environment
✓ Fast-paced development
✓ Teams of any size
✓ Simple release process

Not Ideal For:
─────────────────────────────────────────────────────────────
✗ Multiple production versions
✗ Scheduled releases
✗ Complex deployment processes
✗ Multiple environments (staging, production, etc.)

═══════════════════════════════════════════════════════════
```

---

### GitHub Flow Complete Workflow 🔄

```bash
# ═══════════════════════════════════════════
# STEP-BY-STEP GITHUB FLOW
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   STEP 1: CREATE BRANCH                    ║
╚════════════════════════════════════════════════════════════╝

# Always from main
git checkout main
git pull origin main

# Create feature branch with descriptive name
git checkout -b feature/add-search-functionality

# Branch naming - be descriptive!
─────────────────────────────────────────────────────────────
✅ Good:
feature/add-search-functionality
bugfix/fix-login-redirect-loop
improvement/optimize-image-loading
docs/update-api-documentation

❌ Bad:
search
fix
temp
my-branch

╔════════════════════════════════════════════════════════════╗
║                   STEP 2: ADD COMMITS                      ║
╚════════════════════════════════════════════════════════════╝

# Make changes and commit often
git add search-component.js
git commit -m "feat: add search input component"

git add search-api.js
git commit -m "feat: integrate search API"

git add search.test.js
git commit -m "test: add search tests"

# Commit early, commit often!
─────────────────────────────────────────────────────────────
✓ Small, focused commits
✓ Clear commit messages
✓ Each commit builds on previous
✓ Commit working code (tests pass)

╔════════════════════════════════════════════════════════════╗
║                   STEP 3: OPEN PULL REQUEST EARLY          ║
╚════════════════════════════════════════════════════════════╝

# Push branch
git push -u origin feature/add-search-functionality

# Open PR immediately (even if not ready!)
gh pr create --draft \
             --title "[WIP] Add search functionality" \
             --body "Work in progress. Will add tests and docs."

# Why open PR early?
─────────────────────────────────────────────────────────────
✓ Shows you're working on it
✓ Gets early feedback
✓ Starts discussion
✓ CI/CD runs on every push
✓ Others can see progress
✓ Prevents duplicate work

# PR Description Template:
─────────────────────────────────────────────────────────────
## What does this PR do?
Adds search functionality to the main dashboard

## Why?
Users requested ability to search products

## How to test?
1. Run `npm start`
2. Go to /dashboard
3. Enter search term
4. Verify results

## Screenshots
[Add before/after screenshots]

## Checklist
- [x] Tests added
- [x] Documentation updated
- [ ] Ready for review
- [ ] Tested in staging

╔════════════════════════════════════════════════════════════╗
║                   STEP 4: DISCUSS AND REVIEW               ║
╚════════════════════════════════════════════════════════════╝

# Continue working, push updates
git add .
git commit -m "refactor: improve search algorithm"
git push

# Respond to feedback
git add .
git commit -m "fix: address code review comments"
git push

# When ready, mark as ready for review
gh pr ready  # Convert from draft

# Request specific reviewers
gh pr edit --add-reviewer @teammate1,@teammate2

# Add labels
gh pr edit --add-label "enhancement"

╔════════════════════════════════════════════════════════════╗
║                   STEP 5: DEPLOY FOR TESTING               ║
╚════════════════════════════════════════════════════════════╝

# Deploy branch to staging/preview environment
# This is the KEY difference from other workflows!

# Option 1: Manual deployment
git checkout feature/add-search-functionality
./deploy-to-staging.sh

# Option 2: Automatic PR previews
# Many platforms provide this:
# - Vercel: Automatic PR previews
# - Netlify: Deploy previews
# - Heroku Review Apps
# - AWS Amplify PR previews

# Example Netlify:
─────────────────────────────────────────────────────────────
# netlify.toml
[build]
  command = "npm run build"
  publish = "dist"

[context.deploy-preview]
  command = "npm run build"

# Every PR gets unique URL:
# https://deploy-preview-123--myapp.netlify.app

# Example Vercel:
─────────────────────────────────────────────────────────────
# Automatic preview for every PR
# URL: myapp-git-feature-search-username.vercel.app

# Test thoroughly in preview environment!
─────────────────────────────────────────────────────────────
□ Functionality works
□ No console errors
□ UI looks correct
□ Performance acceptable
□ Mobile responsive
□ Cross-browser tested

╔════════════════════════════════════════════════════════════╗
║                   STEP 6: MERGE TO MAIN                    ║
╚════════════════════════════════════════════════════════════╝

# After approval and tests pass
# Merge via GitHub UI

# Merge strategies:
─────────────────────────────────────────────────────────────

# 1. Squash and merge (RECOMMENDED)
gh pr merge --squash --delete-branch

Result:
* feat: add search functionality (#123)

  - Add search input component
  - Integrate search API
  - Add search tests

✓ Clean history
✓ One commit per feature
✓ Easy to understand
✓ Easy to revert

# 2. Merge commit
gh pr merge --merge --delete-branch

Result:
* Merge pull request #123 from user/feature/search
|\
| * test: add search tests
| * feat: integrate search API
| * feat: add search input component
|/

✓ Preserves all commits
✓ Shows feature development
✓ More detailed history

# 3. Rebase and merge
gh pr merge --rebase --delete-branch

Result:
* test: add search tests
* feat: integrate search API
* feat: add search input component

✓ Linear history
✓ No merge commits
✓ Clean timeline

# Most teams use: Squash and merge

╔════════════════════════════════════════════════════════════╗
║                   STEP 7: DEPLOY TO PRODUCTION             ║
╚════════════════════════════════════════════════════════════╝

# Immediately after merge!
# This is automatic with CD pipeline

# Example GitHub Actions:
─────────────────────────────────────────────────────────────
# .github/workflows/deploy.yml
name: Deploy to Production

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Deploy to production
        run: ./deploy.sh
      - name: Notify team
        run: |
          curl -X POST $SLACK_WEBHOOK \
            -d "{'text':'🚀 Deployed to production!'}"

# Deploy happens automatically within minutes!

╔════════════════════════════════════════════════════════════╗
║                   STEP 8: MONITOR & ROLLBACK IF NEEDED     ║
╚════════════════════════════════════════════════════════════╝

# Monitor deployment
# Check logs, metrics, error tracking

# If issues found, rollback:

# Option 1: Revert commit
git revert HEAD
git push origin main
# Triggers automatic deployment of reverted code

# Option 2: Redeploy previous version
git checkout main
git reset --hard HEAD~1
git push --force origin main
# ⚠️ Use with caution!

# Option 3: Deploy previous release
./deploy.sh --version=previous

═══════════════════════════════════════════════════════════
```

---

### GitHub Flow with CI/CD 🤖

```yaml
# ═══════════════════════════════════════════
# GITHUB ACTIONS WORKFLOW
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   CI/CD PIPELINE                           ║
╚════════════════════════════════════════════════════════════╝

# .github/workflows/ci-cd.yml

name: CI/CD Pipeline

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  # ═══════════════════════════════════════════
  # TEST JOB - Runs on every PR
  # ═══════════════════════════════════════════
  test:
    runs-on: ubuntu-latest

    strategy:
      matrix:
        node-version: [16.x, 18.x, 20.x]

    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Setup Node.js ${{ matrix.node-version }}
        uses: actions/setup-node@v3
        with:
          node-version: ${{ matrix.node-version }}
          cache: 'npm'

      - name: Install dependencies
        run: npm ci

      - name: Run linter
        run: npm run lint

      - name: Run tests
        run: npm test -- --coverage

      - name: Upload coverage
        uses: codecov/codecov-action@v3
        with:
          files: ./coverage/coverage-final.json

  # ═══════════════════════════════════════════
  # BUILD JOB - Verify build works
  # ═══════════════════════════════════════════
  build:
    needs: test
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: 18.x

      - name: Install dependencies
        run: npm ci

      - name: Build application
        run: npm run build

      - name: Upload build artifacts
        uses: actions/upload-artifact@v3
        with:
          name: build-files
          path: dist/

  # ═══════════════════════════════════════════
  # DEPLOY PREVIEW - For PRs
  # ═══════════════════════════════════════════
  deploy-preview:
    needs: [test, build]
    if: github.event_name == 'pull_request'
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v3

      - name: Deploy to Vercel Preview
        uses: amondnet/vercel-action@v25
        with:
          vercel-token: ${{ secrets.VERCEL_TOKEN }}
          vercel-org-id: ${{ secrets.VERCEL_ORG_ID }}
          vercel-project-id: ${{ secrets.VERCEL_PROJECT_ID }}

      - name: Comment PR with preview URL
        uses: actions/github-script@v6
        with:
          script: |
            github.rest.issues.createComment({
              issue_number: context.issue.number,
              owner: context.repo.owner,
              repo: context.repo.repo,
              body: '🚀 Preview deployed! Check it out: [Preview URL]'
            })

  # ═══════════════════════════════════════════
  # DEPLOY PRODUCTION - When merged to main
  # ═══════════════════════════════════════════
  deploy-production:
    needs: [test, build]
    if: github.ref == 'refs/heads/main' && github.event_name == 'push'
    runs-on: ubuntu-latest

    environment:
      name: production
      url: https://myapp.com

    steps:
      - uses: actions/checkout@v3

      - name: Download build artifacts
        uses: actions/download-artifact@v3
        with:
          name: build-files
          path: dist/

      - name: Deploy to production
        run: |
          echo "Deploying to production..."
          ./deploy-production.sh
        env:
          DEPLOY_KEY: ${{ secrets.DEPLOY_KEY }}

      - name: Smoke tests
        run: |
          curl -f https://myapp.com/health || exit 1

      - name: Notify team
        uses: 8398a7/action-slack@v3
        with:
          status: ${{ job.status }}
          text: '🚀 Deployed to production!'
          webhook_url: ${{ secrets.SLACK_WEBHOOK }}

  # ═══════════════════════════════════════════
  # ROLLBACK - If deployment fails
  # ═══════════════════════════════════════════
  rollback:
    needs: deploy-production
    if: failure()
    runs-on: ubuntu-latest

    steps:
      - name: Rollback deployment
        run: ./rollback.sh

      - name: Notify team of rollback
        uses: 8398a7/action-slack@v3
        with:
          status: 'failure'
          text: '⚠️ Deployment failed. Rolling back...'
          webhook_url: ${{ secrets.SLACK_WEBHOOK }}

# ═══════════════════════════════════════════
# BRANCH PROTECTION RULES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   GITHUB BRANCH PROTECTION                 ║
╚════════════════════════════════════════════════════════════╝

# Settings → Branches → Branch protection rules → main

Required settings:
─────────────────────────────────────────────────────────────
✓ Require pull request reviews before merging
  - Required approvals: 1-2
  - Dismiss stale reviews on new commits

✓ Require status checks to pass
  - test
  - build
  - deploy-preview

✓ Require branches to be up to date

✓ Include administrators

✓ Require linear history (optional)

✓ Do not allow bypassing the above settings

Optional but recommended:
─────────────────────────────────────────────────────────────
✓ Require signed commits
✓ Require deployments to succeed
✓ Lock branch (for release freezes)
```

---

<div align="center">

## 🦊 GitLab Flow

</div>

### Overview 📋

```bash
# ═══════════════════════════════════════════
# GITLAB FLOW WORKFLOW
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   ENVIRONMENT-BASED BRANCHES               ║
╚════════════════════════════════════════════════════════════╝

           main (always stable)
             │
             │  ← feature/login
             │     │
             │  ←──┘
             │
             ↓ (merge to environment branches)
             │
        ┌────┴────┬────────┐
        │         │        │
    staging   pre-prod  production
        │         │        │
        ↓         ↓        ↓
     (test)   (validate) (deploy)

Created by: GitLab
Combines best of: Git Flow + GitHub Flow

Key Concepts:
─────────────────────────────────────────────────────────────
• main is always deployable
• Environment branches (staging, production)
• Feature branches from main
• Merge to main, then to environment branches
• Upstream first (always merge to main first)

Three Variations:
─────────────────────────────────────────────────────────────
1. Production branch (most common)
2. Environment branches (staging → production)
3. Release branches (for versions)

Best For:
─────────────────────────────────────────────────────────────
✓ Multiple deployment environments
✓ Staged releases
✓ Continuous delivery (not deployment)
✓ Teams needing testing stages
✓ Complex infrastructure

═══════════════════════════════════════════════════════════
```

---

### GitLab Flow Variants 🔀

```bash
# ═══════════════════════════════════════════
# VARIANT 1: PRODUCTION BRANCH
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WITH PRODUCTION BRANCH                   ║
╚════════════════════════════════════════════════════════════╝

           main (development)
             │
             │  ← feature/search
             │     │
             │  ←──┘
             │
             ↓ (when ready for production)
             │
        production
             │
             ↓ (deployed)

Workflow:
─────────────────────────────────────────────────────────────
# 1. Create feature from main
git checkout main
git pull origin main
git checkout -b feature/add-search

# 2. Work and commit
git add .
git commit -m "feat: add search functionality"
git push -u origin feature/add-search

# 3. Merge request to main
# Review and merge via GitLab UI

# 4. When ready for production
git checkout main
git pull origin main
git checkout production
git merge main
git push origin production

# 5. Production deployment happens automatically

When to use:
─────────────────────────────────────────────────────────────
✓ Simple two-stage deployment (dev → prod)
✓ Want to control production releases
✓ main = development environment
✓ production = production environment

# ═══════════════════════════════════════════
# VARIANT 2: ENVIRONMENT BRANCHES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   MULTIPLE ENVIRONMENTS                    ║
╚════════════════════════════════════════════════════════════╝

              main
                │
                ↓
             staging
                │
                ↓
           pre-production
                │
                ↓
            production

Workflow:
─────────────────────────────────────────────────────────────
# 1. Create feature from main
git checkout main
git checkout -b feature/payment-gateway

# 2. Work and merge to main
# ... work ...
# Merge via MR

# 3. Deploy to staging
git checkout staging
git merge main
git push origin staging
# Auto-deploy to staging environment

# 4. Test in staging
# Run QA tests, manual testing

# 5. Deploy to pre-production
git checkout pre-production
git merge staging
git push origin pre-production
# Auto-deploy to pre-prod environment

# 6. Final validation in pre-production
# Load testing, final checks

# 7. Deploy to production
git checkout production
git merge pre-production
git push origin production
# Auto-deploy to production

# Rollback if needed
git checkout production
git revert HEAD
git push origin production

Benefits:
─────────────────────────────────────────────────────────────
✓ Test in multiple environments
✓ Catch issues before production
✓ Staged rollout
✓ Easy rollback per environment

# ═══════════════════════════════════════════
# VARIANT 3: RELEASE BRANCHES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   VERSION-BASED RELEASES                   ║
╚════════════════════════════════════════════════════════════╝

              main
                │
                ├──→ 2-3-stable (release branch)
                │       │
                │       ↓ (cherry-pick fixes)
                │
                ├──→ 2-4-stable (current release)
                │       │
                │       ↓ (cherry-pick fixes)
                │
                ↓
           (continue development)

Workflow:
─────────────────────────────────────────────────────────────
# 1. Create release branch from main
git checkout main
git checkout -b 2-4-stable

# 2. Continue development on main
git checkout main
git checkout -b feature/new-feature
# ... work ...
# Merge to main

# 3. Bug fix needed in release 2.4
# Option A: Fix in main, cherry-pick to release
git checkout main
git checkout -b bugfix/critical-bug
# ... fix ...
# Merge to main

git checkout 2-4-stable
git cherry-pick <commit-hash>
git push origin 2-4-stable

# Option B: Fix directly in release branch
git checkout 2-4-stable
git checkout -b bugfix/release-bug
# ... fix ...
# Merge to 2-4-stable

# Then merge back to main
git checkout main
git merge 2-4-stable

When to use:
─────────────────────────────────────────────────────────────
✓ Support multiple versions
✓ Long-term support releases
✓ Different versions for different customers
✓ Mobile apps, desktop software

═══════════════════════════════════════════════════════════
```

---

### GitLab Flow Complete Example 🎯

```bash
# ═══════════════════════════════════════════
# REAL-WORLD GITLAB FLOW
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WEEK 1: FEATURE DEVELOPMENT              ║
╚════════════════════════════════════════════════════════════╝

# Monday: Start feature
git checkout main
git pull origin main
git checkout -b feature/user-dashboard

# Work throughout the week
git commit -am "feat: add dashboard layout"
git commit -am "feat: add user widgets"
git commit -am "test: add dashboard tests"

# Friday: Create merge request
git push -u origin feature/user-dashboard

# GitLab MR (via UI):
─────────────────────────────────────────────────────────────
Title: Add user dashboard
Description:
  - New dashboard page
  - User widgets
  - Responsive design

Target: main
Assignee: @reviewer
Labels: feature, frontend

╔════════════════════════════════════════════════════════════╗
║                   WEEK 2: REVIEW & STAGING                 ║
╚════════════════════════════════════════════════════════════╝

# Monday: Address review feedback
git commit -am "refactor: improve dashboard performance"
git push

# Tuesday: MR approved and merged to main

# Deploy to staging
git checkout staging
git pull origin staging
git merge main
git push origin staging

# GitLab CI/CD automatically:
─────────────────────────────────────────────────────────────
✓ Runs tests
✓ Builds application
✓ Deploys to staging environment
✓ Runs smoke tests

# Staging URL: https://staging.myapp.com

# Wednesday-Thursday: QA testing in staging
─────────────────────────────────────────────────────────────
□ Functional testing
□ UI/UX review
□ Performance testing
□ Security scan
□ Cross-browser testing

╔════════════════════════════════════════════════════════════╗
║                   WEEK 3: PRE-PRODUCTION                   ║
╚════════════════════════════════════════════════════════════╝

# Monday: Tests passed, deploy to pre-production
git checkout pre-production
git pull origin pre-production
git merge staging
git push origin pre-production

# Pre-production URL: https://pre-prod.myapp.com

# Tuesday-Wednesday: Final validation
─────────────────────────────────────────────────────────────
□ Load testing
□ Integration testing with production-like data
□ Final stakeholder review
□ Deployment runbook prepared

╔════════════════════════════════════════════════════════════╗
║                   WEEK 3: PRODUCTION DEPLOYMENT            ║
╚════════════════════════════════════════════════════════════╝

# Thursday: Deploy to production
git checkout production
git pull origin production
git merge pre-production
git push origin production

# GitLab CI/CD:
─────────────────────────────────────────────────────────────
✓ Final tests
✓ Backup database
✓ Deploy application
✓ Run migrations
✓ Smoke tests
✓ Notify team

# Production URL: https://myapp.com

# Monitor for 24 hours
─────────────────────────────────────────────────────────────
□ Error rates
□ Performance metrics
□ User feedback
□ Server resources

╔════════════════════════════════════════════════════════════╗
║                   HOTFIX SCENARIO                          ║
╚════════════════════════════════════════════════════════════╝

# Critical bug found in production!

# 1. Fix in main first
git checkout main
git checkout -b hotfix/critical-payment-bug
# ... fix ...
git commit -am "fix: resolve payment processing issue"
git push -u origin hotfix/critical-payment-bug

# 2. Create MR to main (expedited review)
# Merge immediately after review

# 3. Fast-track through environments
git checkout staging
git merge main
git push origin staging
# Wait for staging tests

git checkout pre-production
git merge staging
git push origin pre-production
# Quick validation

git checkout production
git merge pre-production
git push origin production
# Deploy immediately

# Total time: 30-60 minutes (instead of 3 weeks)

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## ⚡ Trunk-Based Development

</div>

### Overview 📋

```bash
# ═══════════════════════════════════════════
# TRUNK-BASED DEVELOPMENT
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   CONTINUOUS INTEGRATION                   ║
╚════════════════════════════════════════════════════════════╝

           main/trunk (always green)
              │
              │  ← small change (< 1 day)
              │     │
              │  ←──┘
              │
              │  ← small change
              │     │
              │  ←──┘
              │
              ↓ (deploy continuously)

Key Principles:
─────────────────────────────────────────────────────────────
• All developers work on single branch (trunk/main)
• Very short-lived feature branches (< 1 day)
• Or commit directly to trunk
• Frequent integration (multiple times per day)
• Feature flags for incomplete work
• Comprehensive automated testing
• Continuous deployment

Used by: Google, Facebook, Netflix, Amazon

Requirements:
─────────────────────────────────────────────────────────────
✓ Excellent CI/CD pipeline
✓ Fast test suite (< 10 minutes)
✓ Feature flags system
✓ Automated deployments
✓ Monitoring and rollback
✓ Team discipline

Best For:
─────────────────────────────────────────────────────────────
✓ High-velocity teams
✓ Mature DevOps practices
✓ Microservices architecture
✓ Continuous deployment
✓ Teams with strong testing culture

Not Ideal For:
─────────────────────────────────────────────────────────────
✗ Junior teams
✗ Weak CI/CD infrastructure
✗ Slow tests
✗ Scheduled releases
✗ Multiple versions

═══════════════════════════════════════════════════════════
```

---

### Trunk-Based Development Workflow 🚀

```bash
# ═══════════════════════════════════════════
# TWO APPROACHES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   APPROACH 1: DIRECT TO TRUNK              ║
╚════════════════════════════════════════════════════════════╝

# For very small changes (< 2 hours)
git checkout main
git pull origin main

# Make small change
git add .
git commit -m "fix: update button color"

# Push directly to main
git push origin main

# CI/CD automatically:
─────────────────────────────────────────────────────────────
✓ Runs tests
✓ Deploys if tests pass
✓ Monitors deployment

# When to use direct commits:
─────────────────────────────────────────────────────────────
✓ Bug fixes
✓ Small refactorings
✓ Documentation updates
✓ Configuration changes
✓ Dependency updates

╔════════════════════════════════════════════════════════════╗
║                   APPROACH 2: SHORT-LIVED BRANCHES         ║
╚════════════════════════════════════════════════════════════╝

# For slightly larger changes (< 1 day)
git checkout main
git pull origin main
git checkout -b quick-improvement

# Work for a few hours
git commit -am "feat: improve search performance"

# Push and create PR
git push -u origin quick-improvement
gh pr create --fill

# Get quick review (< 1 hour)
# Merge immediately
gh pr merge --squash --delete-branch

# Maximum branch lifetime: 24 hours!

╔════════════════════════════════════════════════════════════╗
║                   FEATURE FLAGS FOR LARGE FEATURES         ║
╚════════════════════════════════════════════════════════════╝

# Scenario: Building new dashboard (1 week of work)

# Day 1: Add basic structure (hidden behind flag)
git checkout main
git checkout -b dashboard-structure

# Add feature flag
// config/features.js
export const features = {
  newDashboard: {
    enabled: process.env.FEATURE_NEW_DASHBOARD === 'true',
    rollout: 0 // 0% of users
  }
};

// Use flag
if (features.newDashboard.enabled) {
  return <NewDashboard />;
}
return <OldDashboard />;

git commit -am "feat: add dashboard structure (behind flag)"
git push
# Merge to main within hours

# Day 2: Add dashboard components
git checkout main
git pull
git checkout -b dashboard-components

git commit -am "feat: add dashboard widgets (behind flag)"
git push
# Merge to main

# Day 3: Add dashboard data
git checkout main
git pull
git checkout -b dashboard-data

git commit -am "feat: integrate dashboard API (behind flag)"
git push
# Merge to main

# Day 4-5: Testing and refinement
# All work merged daily to main
# Feature still hidden from users

# Day 6: Enable for beta testers
// Update feature flag
rollout: 10 // 10% of users

git commit -am "feat: enable dashboard for 10% of users"
git push

# Day 7: Full rollout
rollout: 100 // All users

git commit -am "feat: enable dashboard for all users"
git push

# Benefits:
─────────────────────────────────────────────────────────────
✓ Code integrated daily
✓ No merge conflicts
✓ Test in production safely
✓ Easy rollback
✓ Gradual rollout
✓ A/B testing possible

═══════════════════════════════════════════════════════════
```

---

### Trunk-Based Development Best Practices 💡

```bash
# ═══════════════════════════════════════════
# ESSENTIAL PRACTICES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   1. INTEGRATE FREQUENTLY                  ║
╚════════════════════════════════════════════════════════════╝

# Pull from main multiple times per day
git checkout main
git pull origin main

# Minimum: 2x per day (morning & afternoon)
# Ideal: Every hour

# Before lunch:
git checkout main
git pull origin main

# After lunch:
git checkout main
git pull origin main

# Before going home:
git checkout main
git pull origin main

╔════════════════════════════════════════════════════════════╗
║                   2. KEEP CHANGES SMALL                    ║
╚════════════════════════════════════════════════════════════╝

# Size Guidelines:
─────────────────────────────────────────────────────────────
✓ < 200 lines: Perfect
✓ 200-400 lines: Acceptable
✓ > 400 lines: Too large, split it!

# Break large features into small pieces:
─────────────────────────────────────────────────────────────
❌ Don't: One giant "Add user system" PR (2000 lines)

✅ Do: Multiple small PRs
  1. Add user model (50 lines)
  2. Add user API endpoints (100 lines)
  3. Add user UI components (150 lines)
  4. Add user tests (200 lines)
  5. Wire everything together (50 lines)

╔════════════════════════════════════════════════════════════╗
║                   3. MAINTAIN FAST TESTS                   ║
╚════════════════════════════════════════════════════════════╝

# Test suite must be FAST
─────────────────────────────────────────────────────────────
Target: < 10 minutes for full suite
Ideal: < 5 minutes

# Strategies:
─────────────────────────────────────────────────────────────
✓ Run tests in parallel
✓ Use test doubles (mocks, stubs)
✓ Optimize slow tests
✓ Split into fast & slow suites

# Example: Parallel tests
npm test -- --maxWorkers=8

# Run fast tests on every commit
# Run slow tests nightly

╔════════════════════════════════════════════════════════════╗
║                   4. USE FEATURE FLAGS                     ║
╚════════════════════════════════════════════════════════════╝

# Simple feature flag implementation
// featureFlags.js
export function isFeatureEnabled(flagName, user = null) {
  const flags = {
    newDashboard: {
      enabled: true,
      rolloutPercentage: 50,
      enabledUsers: ['beta@example.com'],
      enabledCompanies: ['company-123']
    },
    betaFeatures: {
      enabled: process.env.NODE_ENV === 'development',
      rolloutPercentage: 0
    }
  };

  const flag = flags[flagName];
  if (!flag) return false;
  if (!flag.enabled) return false;

  // Check user whitelist
  if (user && flag.enabledUsers?.includes(user.email)) {
    return true;
  }

  // Check company whitelist
  if (user && flag.enabledCompanies?.includes(user.companyId)) {
    return true;
  }

  // Rollout percentage
  if (flag.rolloutPercentage === 100) return true;
  if (flag.rolloutPercentage === 0) return false;

  // Hash user ID for consistent experience
  const hash = simpleHash(user?.id || 'anonymous');
  return (hash % 100) < flag.rolloutPercentage;
}

// Usage
if (isFeatureEnabled('newDashboard', currentUser)) {
  return <NewDashboard />;
}
return <OldDashboard />;

╔════════════════════════════════════════════════════════════╗
║                   5. MONITOR EVERYTHING                    ║
╚════════════════════════════════════════════════════════════╝

# Essential monitoring:
─────────────────────────────────────────────────────────────
✓ Error rates
✓ Response times
✓ Server resources
✓ User metrics
✓ Business metrics

# Set up alerts:
─────────────────────────────────────────────────────────────
✓ Error rate > 1%
✓ Response time > 1 second
✓ Memory usage > 80%
✓ Disk space < 20%

# Quick rollback if issues detected

╔════════════════════════════════════════════════════════════╗
║                   6. PAIR PROGRAMMING                      ║
╚════════════════════════════════════════════════════════════╝

# For trunk-based development:
─────────────────────────────────────────────────────────────
✓ Pair on complex changes
✓ Built-in code review
✓ Knowledge sharing
✓ Higher quality code
✓ Faster development

# When to pair:
─────────────────────────────────────────────────────────────
✓ Critical features
✓ Complex refactorings
✓ New team members
✓ Unfamiliar code areas

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🎋 Forking Workflow

</div>

### Overview 📋

```bash
# ═══════════════════════════════════════════
# FORKING WORKFLOW
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   DISTRIBUTED COLLABORATION                ║
╚════════════════════════════════════════════════════════════╝

    Official Repository (upstream)
              │
              │ fork
              ↓
    Developer's Fork (origin)
              │
              │ clone
              ↓
    Local Repository
              │
              │ work & commit
              ↓
    Push to Fork
              │
              │ pull request
              ↓
    Official Repository

Key Principles:
─────────────────────────────────────────────────────────────
• Each developer has own fork (copy)
• Fork = server-side clone
• Pull requests from fork to upstream
• No direct push to upstream
• Maintainer reviews and merges
• Keep fork synced with upstream

Best For:
─────────────────────────────────────────────────────────────
✓ Open source projects
✓ Public repositories
✓ External contributors
✓ Projects with many contributors
✓ Security-sensitive projects
✓ Projects needing contribution control

Famous Projects Using This:
─────────────────────────────────────────────────────────────
• Linux Kernel
• React
• TensorFlow
• VS Code
• Most GitHub open source projects

═══════════════════════════════════════════════════════════
```

---

### Complete Forking Workflow 🔄

```bash
# ═══════════════════════════════════════════
# STEP-BY-STEP FORKING WORKFLOW
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   STEP 1: FORK REPOSITORY                  ║
╚════════════════════════════════════════════════════════════╝

# Via GitHub UI:
─────────────────────────────────────────────────────────────
1. Go to repository (e.g., https://github.com/original-owner/repo)
2. Click "Fork" button (top right)
3. Select your account
4. Wait for fork to complete

# Via GitHub CLI:
gh repo fork original-owner/repo --clone

# Now you have:
─────────────────────────────────────────────────────────────
Upstream: https://github.com/original-owner/repo (official)
Origin:   https://github.com/your-username/repo (your fork)

╔════════════════════════════════════════════════════════════╗
║                   STEP 2: CLONE YOUR FORK                  ║
╚════════════════════════════════════════════════════════════╝

# Clone your fork
git clone https://github.com/your-username/repo.git
cd repo

# Check remotes
git remote -v
# origin  https://github.com/your-username/repo.git (fetch)
# origin  https://github.com/your-username/repo.git (push)

╔════════════════════════════════════════════════════════════╗
║                   STEP 3: ADD UPSTREAM REMOTE              ║
╚════════════════════════════════════════════════════════════╝

# Add upstream remote (original repository)
git remote add upstream https://github.com/original-owner/repo.git

# Verify remotes
git remote -v
# origin    https://github.com/your-username/repo.git (fetch)
# origin    https://github.com/your-username/repo.git (push)
# upstream  https://github.com/original-owner/repo.git (fetch)
# upstream  https://github.com/original-owner/repo.git (push)

# Disable push to upstream (safety)
git remote set-url --push upstream DISABLE

# Verify (push URL should be DISABLE)
git remote -v

╔════════════════════════════════════════════════════════════╗
║                   STEP 4: SYNC WITH UPSTREAM               ║
╚════════════════════════════════════════════════════════════╝

# Fetch upstream changes
git fetch upstream

# Check out main branch
git checkout main

# Merge upstream changes
git merge upstream/main

# Or rebase
git rebase upstream/main

# Push to your fork
git push origin main

# Do this regularly!
# Before starting new feature
# Before creating pull request

╔════════════════════════════════════════════════════════════╗
║                   STEP 5: CREATE FEATURE BRANCH            ║
╚════════════════════════════════════════════════════════════╝

# Always start from updated main
git checkout main
git pull upstream main

# Create feature branch
git checkout -b feature/add-dark-mode

# Work on feature
git add .
git commit -m "feat: implement dark mode toggle"

git add .
git commit -m "feat: add dark mode styles"

git add .
git commit -m "test: add dark mode tests"

╔════════════════════════════════════════════════════════════╗
║                   STEP 6: PUSH TO YOUR FORK                ║
╚════════════════════════════════════════════════════════════╝

# Push feature branch to your fork
git push origin feature/add-dark-mode

# Or set upstream tracking
git push -u origin feature/add-dark-mode

╔════════════════════════════════════════════════════════════╗
║                   STEP 7: CREATE PULL REQUEST              ║
╚════════════════════════════════════════════════════════════╝

# Via GitHub UI:
─────────────────────────────────────────────────────────────
1. Go to your fork on GitHub
2. Click "Compare & pull request" button
3. Ensure base repository is upstream/main
4. Ensure compare is your-fork/feature-branch
5. Fill in PR template:
   - Clear title
   - Detailed description
   - Related issues
   - Testing steps
   - Screenshots if UI changes
6. Click "Create pull request"

# Via GitHub CLI:
gh pr create --repo original-owner/repo \
             --title "Add dark mode" \
             --body "Implements dark mode with toggle button"

# PR Template Example:
─────────────────────────────────────────────────────────────
## Description
Adds dark mode functionality with a toggle button in the header.

## Related Issues
Fixes #123

## Changes Made
- Added dark mode toggle component
- Implemented dark mode styles
- Added persistence with localStorage
- Added tests for dark mode functionality

## Screenshots
[Before/After images]

## Testing Steps
1. Run `npm start`
2. Click toggle button in header
3. Verify dark mode applies
4. Refresh page
5. Verify dark mode persists

## Checklist
- [x] Code follows project style guidelines
- [x] Tests added/updated
- [x] Documentation updated
- [x] No breaking changes
- [x] Tested locally

╔════════════════════════════════════════════════════════════╗
║                   STEP 8: ADDRESS REVIEW FEEDBACK          ║
╚════════════════════════════════════════════════════════════╝

# Make requested changes
git add .
git commit -m "refactor: address PR feedback"

# Keep branch updated with upstream
git fetch upstream
git rebase upstream/main

# Force push (your fork, safe to do)
git push --force-with-lease origin feature/add-dark-mode

# Respond to comments on GitHub
# Be respectful and constructive

╔════════════════════════════════════════════════════════════╗
║                   STEP 9: PR MERGED                        ║
╚════════════════════════════════════════════════════════════╝

# After PR is merged:

# Update your local main
git checkout main
git pull upstream main

# Delete feature branch locally
git branch -d feature/add-dark-mode

# Delete feature branch on your fork
git push origin --delete feature/add-dark-mode

# Update your fork's main
git push origin main

# Start new feature!

═══════════════════════════════════════════════════════════
```

---

### Forking Workflow Best Practices 💡

```bash
# ═══════════════════════════════════════════
# BEST PRACTICES FOR CONTRIBUTORS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   BEFORE CONTRIBUTING                      ║
╚════════════════════════════════════════════════════════════╝

□ Read CONTRIBUTING.md
□ Read CODE_OF_CONDUCT.md
□ Check existing issues/PRs
□ Discuss major changes first
□ Follow project conventions
□ Set up development environment
□ Run tests locally

╔════════════════════════════════════════════════════════════╗
║                   KEEPING FORK SYNCED                      ║
╚════════════════════════════════════════════════════════════╝

# Create alias for syncing
git config --global alias.sync '!git fetch upstream && git checkout main && git rebase upstream/main && git push origin main'

# Usage:
git sync

# Automated sync script (sync.sh):
─────────────────────────────────────────────────────────────
#!/bin/bash

echo "Syncing with upstream..."

# Fetch upstream
git fetch upstream

# Save current branch
CURRENT_BRANCH=$(git branch --show-current)

# Switch to main
git checkout main

# Rebase with upstream
if git rebase upstream/main; then
    echo "✓ Synced with upstream"

    # Push to fork
    git push origin main
    echo "✓ Updated fork"

    # Switch back to feature branch
    git checkout "$CURRENT_BRANCH"

    # Rebase feature branch
    if [ "$CURRENT_BRANCH" != "main" ]; then
        git rebase main
        echo "✓ Updated feature branch"
    fi
else
    echo "✗ Sync failed - resolve conflicts"
    git rebase --abort
fi

# Make executable:
chmod +x sync.sh

# Usage:
./sync.sh

╔════════════════════════════════════════════════════════════╗
║                   GITHUB ACTIONS AUTO-SYNC                 ║
╚════════════════════════════════════════════════════════════╝

# .github/workflows/sync-fork.yml
name: Sync Fork

on:
  schedule:
    - cron: '0 0 * * *'  # Daily at midnight
  workflow_dispatch:      # Manual trigger

jobs:
  sync:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
        with:
          token: ${{ secrets.GITHUB_TOKEN }}

      - name: Sync fork
        run: |
          git config user.name github-actions
          git config user.email github-actions@github.com
          git remote add upstream https://github.com/original-owner/repo.git
          git fetch upstream
          git checkout main
          git rebase upstream/main
          git push origin main

╔════════════════════════════════════════════════════════════╗
║                   HANDLING CONFLICTS                       ║
╚════════════════════════════════════════════════════════════╝

# When rebasing on upstream/main causes conflicts:

# 1. View conflicts
git status

# 2. Open conflicting files, fix conflicts
# Remove <<<<<<, ======, >>>>>> markers

# 3. Stage resolved files
git add .

# 4. Continue rebase
git rebase --continue

# 5. If multiple conflicts, repeat steps 2-4

# 6. Force push to your fork
git push --force-with-lease origin feature-branch

# Or abort and start over:
git rebase --abort

╔════════════════════════════════════════════════════════════╗
║                   GOOD CONTRIBUTOR PRACTICES               ║
╚════════════════════════════════════════════════════════════╝

✅ DO:
─────────────────────────────────────────────────────────────
• Keep PRs small and focused
• Write clear commit messages
• Add tests for new features
• Update documentation
• Follow project style guide
• Be responsive to feedback
• Sync fork before starting work
• Squash commits if requested
• Be patient with reviews
• Be respectful and professional

❌ DON'T:
─────────────────────────────────────────────────────────────
• Don't submit huge PRs
• Don't push unrelated changes
• Don't ignore CI failures
• Don't take feedback personally
• Don't force push to main
• Don't commit generated files
• Don't commit secrets/credentials
• Don't bypass required checks

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 📦 Monorepo Workflows

</div>

### Overview 📋

```bash
# ═══════════════════════════════════════════
# MONOREPO WORKFLOW
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   MONOREPO STRUCTURE                       ║
╚════════════════════════════════════════════════════════════╝

my-monorepo/
├── packages/
│   ├── frontend/       # React app
│   ├── backend/        # Node.js API
│   ├── mobile/         # React Native app
│   └── shared/         # Shared utilities
├── apps/
│   ├── web/
│   └── admin/
├── libs/
│   ├── ui-components/
│   ├── utils/
│   └── types/
└── tools/

What is a Monorepo?
─────────────────────────────────────────────────────────────
• Single repository
• Multiple projects/packages
• Shared dependencies
• Unified versioning
• Atomic commits across projects

Benefits:
─────────────────────────────────────────────────────────────
✓ Code sharing
✓ Atomic changes
✓ Single source of truth
✓ Easier refactoring
✓ Consistent tooling
✓ Simplified dependency management

Challenges:
─────────────────────────────────────────────────────────────
⚠ Larger repository
⚠ Longer CI times
⚠ Requires tooling
⚠ Access control complexity

Used By:
─────────────────────────────────────────────────────────────
• Google (Bazel)
• Facebook (Mercurial)
• Microsoft
• Uber
• Twitter

═══════════════════════════════════════════════════════════
```

---

### Monorepo Git Strategies 🎯

```bash
# ═══════════════════════════════════════════
# STRATEGY 1: TRUNK-BASED IN MONOREPO
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SINGLE MAIN BRANCH                       ║
╚════════════════════════════════════════════════════════════╝

# All teams commit to main
# Short-lived feature branches
# Path-based CI/CD

# Example workflow:
git checkout main
git pull origin main
git checkout -b feature/frontend-login

# Work only in packages/frontend/
git add packages/frontend/
git commit -m "feat(frontend): add login component"
git push origin feature/frontend-login

# CI only runs tests for affected packages

# ═══════════════════════════════════════════
# STRATEGY 2: PACKAGE-BASED BRANCHES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   MULTIPLE MAIN BRANCHES                   ║
╚════════════════════════════════════════════════════════════╝

# Branch per major component
main                    # Integration branch
packages/frontend/main  # Frontend development
packages/backend/main   # Backend development
packages/mobile/main    # Mobile development

# Feature branches from component branch
git checkout packages/frontend/main
git checkout -b feature/new-ui

# Merge to component branch
git checkout packages/frontend/main
git merge feature/new-ui

# Periodically merge to main
git checkout main
git merge packages/frontend/main

# ═══════════════════════════════════════════
# STRATEGY 3: SEMANTIC COMMIT SCOPES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   CONVENTIONAL COMMITS                     ║
╚════════════════════════════════════════════════════════════╝

# Format: type(scope): description

# Examples:
git commit -m "feat(frontend): add user authentication"
git commit -m "fix(backend): resolve database connection issue"
git commit -m "chore(mobile): update dependencies"
git commit -m "docs(shared): update API documentation"

# Multiple packages:
git commit -m "feat(frontend,backend): implement real-time chat"

# Breaking change:
git commit -m "feat(api)!: change authentication endpoint"

# ═══════════════════════════════════════════
# PATH-BASED CI/CD
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   GITHUB ACTIONS EXAMPLE                   ║
╚════════════════════════════════════════════════════════════╝

# .github/workflows/ci.yml
name: CI

on:
  push:
    branches: [main]
  pull_request:

jobs:
  # Detect changed packages
  changes:
    runs-on: ubuntu-latest
    outputs:
      frontend: ${{ steps.filter.outputs.frontend }}
      backend: ${{ steps.filter.outputs.backend }}
      mobile: ${{ steps.filter.outputs.mobile }}
    steps:
      - uses: actions/checkout@v3
      - uses: dorny/paths-filter@v2
        id: filter
        with:
          filters: |
            frontend:
              - 'packages/frontend/**'
            backend:
              - 'packages/backend/**'
            mobile:
              - 'packages/mobile/**'

  # Test frontend only if changed
  test-frontend:
    needs: changes
    if: needs.changes.outputs.frontend == 'true'
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Test Frontend
        run: |
          cd packages/frontend
          npm ci
          npm test

  # Test backend only if changed
  test-backend:
    needs: changes
    if: needs.changes.outputs.backend == 'true'
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Test Backend
        run: |
          cd packages/backend
          npm ci
          npm test

  # Test mobile only if changed
  test-mobile:
    needs: changes
    if: needs.changes.outputs.mobile == 'true'
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Test Mobile
        run: |
          cd packages/mobile
          npm ci
          npm test

═══════════════════════════════════════════════════════════
```

---

### Monorepo Tools 🛠️

```bash
# ═══════════════════════════════════════════
# POPULAR MONOREPO TOOLS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   LERNA (JavaScript)                       ║
╚════════════════════════════════════════════════════════════╝

# Install
npm install -g lerna

# Initialize
lerna init

# Bootstrap (install dependencies)
lerna bootstrap

# Run command in all packages
lerna run test

# Run command in specific package
lerna run test --scope=frontend

# Version & publish
lerna version
lerna publish

╔════════════════════════════════════════════════════════════╗
║                   NX (Modern Monorepo Tool)                ║
╚════════════════════════════════════════════════════════════╝

# Create workspace
npx create-nx-workspace@latest myorg

# Generate app
nx generate @nrwl/react:app frontend

# Generate library
nx generate @nrwl/react:lib ui-components

# Run app
nx serve frontend

# Build
nx build frontend

# Test
nx test frontend

# Run affected (only changed)
nx affected:test
nx affected:build

# Dependency graph
nx dep-graph

╔════════════════════════════════════════════════════════════╗
║                   TURBOREPO (Fast Builds)                  ║
╚════════════════════════════════════════════════════════════╝

# Install
npm install turbo --global

# turbo.json
{
  "pipeline": {
    "build": {
      "dependsOn": ["^build"],
      "outputs": ["dist/**"]
    },
    "test": {
      "dependsOn": ["build"],
      "outputs": []
    },
    "lint": {
      "outputs": []
    }
  }
}

# Run commands
turbo run build
turbo run test
turbo run lint

# Run in parallel
turbo run build --parallel

# Remote caching
turbo run build --team=myteam --token=abc123

╔════════════════════════════════════════════════════════════╗
║                   YARN WORKSPACES                          ║
╚════════════════════════════════════════════════════════════╝

# package.json (root)
{
  "private": true,
  "workspaces": [
    "packages/*",
    "apps/*"
  ]
}

# Install all dependencies
yarn install

# Add dependency to specific package
yarn workspace frontend add react

# Run command in workspace
yarn workspace frontend start

# Run command in all workspaces
yarn workspaces run test

╔════════════════════════════════════════════════════════════╗
║                   PNPM WORKSPACES                          ║
╚════════════════════════════════════════════════════════════╝

# pnpm-workspace.yaml
packages:
  - 'packages/*'
  - 'apps/*'

# Install
pnpm install

# Add dependency
pnpm add react --filter frontend

# Run script
pnpm --filter frontend start

# Run in all packages
pnpm -r test

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🔧 Advanced Techniques

</div>

### Git Rebase Mastery 🎯

```bash
# ═══════════════════════════════════════════
# INTERACTIVE REBASE
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   CLEANING UP HISTORY                      ║
╚════════════════════════════════════════════════════════════╝

# Interactive rebase last 5 commits
git rebase -i HEAD~5

# Opens editor:
─────────────────────────────────────────────────────────────
pick a1b2c3d feat: add login
pick e4f5g6h fix: typo
pick i7j8k9l feat: add validation
pick m1n2o3p fix: another typo
pick q4r5s6t docs: update readme

# Commands:
p, pick   = use commit
r, reword = use commit, but edit message
e, edit   = use commit, but stop for amending
s, squash = use commit, but meld into previous
f, fixup  = like squash, but discard message
d, drop   = remove commit

# ═══════════════════════════════════════════
# COMMON REBASE SCENARIOS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SQUASH COMMITS                           ║
╚════════════════════════════════════════════════════════════╝

# Before:
# * e4f5g6h fix: typo
# * a1b2c3d feat: add login

# Change to:
pick a1b2c3d feat: add login
fixup e4f5g6h fix: typo

# After:
# * a1b2c3d feat: add login (includes typo fix)

╔════════════════════════════════════════════════════════════╗
║                   REORDER COMMITS                          ║
╚════════════════════════════════════════════════════════════╝

# Just reorder the lines:
pick i7j8k9l feat: add validation
pick a1b2c3d feat: add login
pick q4r5s6t docs: update readme

╔════════════════════════════════════════════════════════════╗
║                   EDIT COMMIT MESSAGE                      ║
╚════════════════════════════════════════════════════════════╝

# Change pick to reword:
reword a1b2c3d feat: add login

# After saving, editor opens to change message

╔════════════════════════════════════════════════════════════╗
║                   SPLIT COMMIT                             ║
╚════════════════════════════════════════════════════════════╝

# Mark commit for editing:
edit a1b2c3d feat: add login and validation

# Rebase pauses, reset commit:
git reset HEAD^

# Stage and commit separately:
git add login.js
git commit -m "feat: add login"

git add validation.js
git commit -m "feat: add validation"

# Continue rebase:
git rebase --continue

# ═══════════════════════════════════════════
# REBASE ONTO
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   MOVE BRANCH BASE                         ║
╚════════════════════════════════════════════════════════════╝

# Scenario: Created feature from wrong branch
# Created from: develop
# Should be from: main

# Move branch base
git rebase --onto main develop feature-branch

# Before:
main
  └─ commit A
develop
  └─ commit B
    └─ commit C (feature-branch)

# After:
main
  └─ commit A
    └─ commit C (feature-branch)
develop
  └─ commit B

# ═══════════════════════════════════════════
# AUTO-SQUASH
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   FIXUP COMMITS                            ║
╚════════════════════════════════════════════════════════════╝

# Create main commit
git commit -m "feat: add user profile"

# Later, found a bug in that commit
git add fix.js
git commit --fixup HEAD  # or specific commit hash

# Commits:
# * fixup! feat: add user profile
# * feat: add user profile

# Auto-squash
git rebase -i --autosquash HEAD~2

# Automatically arranges fixup commits!

# Set as default:
git config --global rebase.autosquash true

═══════════════════════════════════════════════════════════
```

---

### Cherry-Picking & Reverting 🍒

```bash
# ═══════════════════════════════════════════
# CHERRY-PICK
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   APPLY SPECIFIC COMMITS                   ║
╚════════════════════════════════════════════════════════════╝

# Apply single commit
git cherry-pick a1b2c3d

# Apply multiple commits
git cherry-pick a1b2c3d e4f5g6h

# Apply range of commits
git cherry-pick a1b2c3d..e4f5g6h

# Cherry-pick without committing
git cherry-pick --no-commit a1b2c3d

# If conflicts occur:
# 1. Fix conflicts
git add .
# 2. Continue
git cherry-pick --continue

# Or abort
git cherry-pick --abort

# ═══════════════════════════════════════════
# REVERT
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   UNDO COMMITS SAFELY                      ║
╚════════════════════════════════════════════════════════════╝

# Revert single commit
git revert a1b2c3d

# Creates new commit that undoes changes

# Revert multiple commits
git revert a1b2c3d e4f5g6h

# Revert without committing
git revert --no-commit a1b2c3d

# Revert merge commit
git revert -m 1 merge-commit-hash
# -m 1 keeps first parent (main branch)

# ═══════════════════════════════════════════
# RESET vs REVERT
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WHEN TO USE WHAT                         ║
╚════════════════════════════════════════════════════════════╝

Use REVERT when:
─────────────────────────────────────────────────────────────
✓ Commits already pushed
✓ Others have pulled your changes
✓ Want to preserve history
✓ Public/shared branches

# Example:
git revert HEAD  # Undo last commit safely

Use RESET when:
─────────────────────────────────────────────────────────────
✓ Commits not yet pushed
✓ Working on local branch
✓ Want to rewrite history
✓ Private branches

# Example:
git reset --hard HEAD~1  # Remove last commit

# Reset modes:
─────────────────────────────────────────────────────────────
--soft    # Keep changes staged
--mixed   # Keep changes unstaged (default)
--hard    # Discard changes completely

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🏷️ Commit Conventions

</div>

### Conventional Commits 📝

```bash
# ═══════════════════════════════════════════
# CONVENTIONAL COMMITS SPECIFICATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   FORMAT                                   ║
╚════════════════════════════════════════════════════════════╝

<type>(<scope>): <subject>

<body>

<footer>

# ═══════════════════════════════════════════
# TYPES
# ═══════════════════════════════════════════

feat:      New feature
fix:       Bug fix
docs:      Documentation changes
style:     Code style (formatting, semicolons, etc)
refactor:  Code refactoring
perf:      Performance improvements
test:      Adding/updating tests
build:     Build system changes
ci:        CI configuration changes
chore:     Maintenance tasks
revert:    Revert previous commit

# ═══════════════════════════════════════════
# EXAMPLES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   BASIC COMMITS                            ║
╚════════════════════════════════════════════════════════════╝

feat: add user authentication

fix: resolve login redirect issue

docs: update API documentation

style: format code with prettier

refactor: extract validation logic

perf: optimize database queries

test: add unit tests for auth module

build: upgrade webpack to v5

ci: add GitHub Actions workflow

chore: update dependencies

╔════════════════════════════════════════════════════════════╗
║                   WITH SCOPE                               ║
╚════════════════════════════════════════════════════════════╝

feat(auth): implement JWT authentication

fix(api): handle null response

docs(readme): add installation instructions

refactor(database): optimize connection pool

test(auth): add integration tests

╔════════════════════════════════════════════════════════════╗
║                   WITH BODY                                ║
╚════════════════════════════════════════════════════════════╝

feat(auth): add password reset functionality

Implemented password reset flow:
- Email verification
- Reset token generation
- New password validation

Closes #123

╔════════════════════════════════════════════════════════════╗
║                   BREAKING CHANGES                         ║
╚════════════════════════════════════════════════════════════╝

feat(api)!: change authentication endpoint

BREAKING CHANGE: Authentication endpoint moved from /auth to /api/v2/auth

Migration guide:
- Update API calls from /auth to /api/v2/auth
- New JWT format required

# ═══════════════════════════════════════════
# COMMIT MESSAGE TEMPLATE
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   GIT COMMIT TEMPLATE                      ║
╚════════════════════════════════════════════════════════════╝

# .gitmessage (commit template)
# <type>(<scope>): <subject>
#
# <body>
#
# <footer>
#
# Type: feat, fix, docs, style, refactor, perf, test, build, ci, chore, revert
# Scope: Component or module affected
# Subject: Imperative mood, no period at end
# Body: Explain what and why (not how)
# Footer: Breaking changes, issues closed

# Set template:
git config --global commit.template ~/.gitmessage

# ═══════════════════════════════════════════
# COMMITLINT
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   ENFORCE COMMIT CONVENTIONS               ║
╚════════════════════════════════════════════════════════════╝

# Install
npm install --save-dev @commitlint/cli @commitlint/config-conventional

# commitlint.config.js
module.exports = {
  extends: ['@commitlint/config-conventional'],
  rules: {
    'type-enum': [
      2,
      'always',
      [
        'feat',
        'fix',
        'docs',
        'style',
        'refactor',
        'perf',
        'test',
        'build',
        'ci',
        'chore',
        'revert'
      ]
    ],
    'subject-case': [2, 'always', 'sentence-case'],
    'header-max-length': [2, 'always', 100]
  }
};

# Integrate with Husky
npm install --save-dev husky

# .husky/commit-msg
#!/bin/sh
. "$(dirname "$0")/_/husky.sh"

npx --no-install commitlint --edit "$1"

# Now commits are validated!

═══════════════════════════════════════════════════════════
```

---

### Semantic Versioning 🔢

```bash
# ═══════════════════════════════════════════
# SEMANTIC VERSIONING
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   VERSION FORMAT                           ║
╚════════════════════════════════════════════════════════════╝

MAJOR.MINOR.PATCH

Example: 2.3.1

MAJOR: Breaking changes (2.0.0)
MINOR: New features, backward compatible (2.1.0)
PATCH: Bug fixes, backward compatible (2.0.1)

# ═══════════════════════════════════════════
# VERSION BUMPING RULES
# ═══════════════════════════════════════════

Commit Type    → Version Bump
────────────────────────────────────
fix:           → PATCH (1.0.0 → 1.0.1)
feat:          → MINOR (1.0.0 → 1.1.0)
BREAKING:      → MAJOR (1.0.0 → 2.0.0)

# ═══════════════════════════════════════════
# SEMANTIC-RELEASE
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   AUTOMATED VERSIONING                     ║
╚════════════════════════════════════════════════════════════╝

# Install
npm install --save-dev semantic-release

# .releaserc.json
{
  "branches": ["main"],
  "plugins": [
    "@semantic-release/commit-analyzer",
    "@semantic-release/release-notes-generator",
    "@semantic-release/changelog",
    "@semantic-release/npm",
    "@semantic-release/github",
    "@semantic-release/git"
  ]
}

# GitHub Actions workflow
# .github/workflows/release.yml
name: Release

on:
  push:
    branches: [main]

jobs:
  release:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
      - run: npm ci
      - run: npx semantic-release
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          NPM_TOKEN: ${{ secrets.NPM_TOKEN }}

# Automatically:
# ✓ Analyzes commits
# ✓ Determines version
# ✓ Generates changelog
# ✓ Creates Git tag
# ✓ Creates GitHub release
# ✓ Publishes to npm

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🤝 Code Review

</div>

### Code Review Best Practices 👀

```bash
# ═══════════════════════════════════════════
# CREATING REVIEWABLE PULL REQUESTS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   PR SIZE GUIDELINES                       ║
╚════════════════════════════════════════════════════════════╝

Ideal PR Size:
─────────────────────────────────────────────────────────────
Lines Changed    Status       Review Time
< 50            ⭐ Tiny       5 minutes
50-100          ✅ Small      10 minutes
100-300         👍 Medium     20-30 minutes
300-500         ⚠️ Large      1 hour
500-1000        ❌ Huge       2+ hours
> 1000          💀 Too Large  Impossible

# Break large PRs into smaller ones!

╔════════════════════════════════════════════════════════════╗
║                   PR DESCRIPTION TEMPLATE                  ║
╚════════════════════════════════════════════════════════════╝

# .github/PULL_REQUEST_TEMPLATE.md

## Description
<!-- Brief description of changes -->

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Breaking change
- [ ] Documentation update
- [ ] Performance improvement
- [ ] Code refactoring

## Related Issues
<!-- Link related issues: Fixes #123, Closes #456 -->

## Changes Made
<!-- List key changes -->
-
-
-

## Testing
<!-- How to test these changes -->
1.
2.
3.

## Screenshots
<!-- If UI changes, add before/after screenshots -->

## Checklist
- [ ] Code follows style guidelines
- [ ] Self-review performed
- [ ] Comments added for complex code
- [ ] Documentation updated
- [ ] Tests added/updated
- [ ] All tests passing
- [ ] No breaking changes (or documented)
- [ ] Changelog updated

╔════════════════════════════════════════════════════════════╗
║                   FOR REVIEWERS                            ║
╚════════════════════════════════════════════════════════════╝

What to Review:
─────────────────────────────────────────────────────────────
□ Code correctness
□ Code style consistency
□ Test coverage
□ Documentation
□ Performance implications
□ Security considerations
□ Edge cases handled
□ Error handling
□ Breaking changes
□ Dependencies updated

Review Checklist:
─────────────────────────────────────────────────────────────
□ Understand the context
□ Check if PR description is clear
□ Review changes line by line
□ Run code locally
□ Check tests pass
□ Verify documentation
□ Look for potential bugs
□ Check for code duplication
□ Ensure best practices followed
□ Provide constructive feedback

╔════════════════════════════════════════════════════════════╗
║                   FEEDBACK GUIDELINES                      ║
╚════════════════════════════════════════════════════════════╝

Good Feedback:
─────────────────────────────────────────────────────────────
✅ "Consider extracting this into a separate function for better readability."
✅ "This could cause a race condition. What if the API call fails?"
✅ "Great approach! Minor suggestion: we could use Array.map() here."
✅ "This works, but have you considered using the existing utility function?"

Bad Feedback:
─────────────────────────────────────────────────────────────
❌ "This is wrong."
❌ "Why did you do it this way?"
❌ "Just use X instead."
❌ "This code is terrible."

Feedback Categories:
─────────────────────────────────────────────────────────────
🔴 Blocker:     Must be fixed before merge
🟡 Suggestion:  Nice to have, not required
🟢 Nitpick:     Minor style preference
💡 Question:    Seeking clarification
👍 Praise:      Positive feedback

# Use labels in comments:
# 🔴 Blocker: This will cause a security vulnerability
# 🟡 Suggestion: Consider adding input validation here
# 💡 Question: How does this handle null values?
# 👍 Praise: Great use of async/await!

═══════════════════════════════════════════════════════════
```

---

### GitHub Review Features 🔍

```bash
# ═══════════════════════════════════════════
# GITHUB PR REVIEW TOOLS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   REVIEW STATES                            ║
╚════════════════════════════════════════════════════════════╝

Comment:         General feedback
Approve:         Ready to merge
Request Changes: Changes needed before merge

# CLI Review
gh pr review 123 --approve
gh pr review 123 --request-changes
gh pr review 123 --comment -b "Looks good!"

╔════════════════════════════════════════════════════════════╗
║                   INLINE COMMENTS                          ║
╚════════════════════════════════════════════════════════════╝

# Add comments to specific lines
# Click line number in PR diff
# Add comment
# Submit as single comment or start review

# Suggestions (GitHub auto-applies code)

const result = data.map(item => item.value);


╔════════════════════════════════════════════════════════════╗
║ CODE OWNERS ║
╚════════════════════════════════════════════════════════════╝

# .github/CODEOWNERS

# Global owners

- @team-leads

# Frontend

/frontend/\*\* @frontend-team

# Backend

/backend/\*\* @backend-team

# Infrastructure

/infrastructure/** @devops-team
/.github/workflows/** @devops-team

# Documentation

/docs/\*\* @tech-writers

# Specific files

package.json @tech-leads
/.gitignore @everyone

# Automatically requests review from code owners!

╔════════════════════════════════════════════════════════════╗
║ BRANCH PROTECTION RULES ║
╚════════════════════════════════════════════════════════════╝

# Settings → Branches → Branch protection rules

Required Rules:
─────────────────────────────────────────────────────────────
✓ Require pull request reviews (1-2 approvals)
✓ Dismiss stale reviews on new commits
✓ Require review from Code Owners
✓ Require status checks to pass
✓ Require branches to be up to date
✓ Require conversation resolution
✓ Require signed commits
✓ Include administrators
✓ Restrict who can push

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🚀 CI/CD Integration

</div>

### Continuous Integration Pipeline 🤖

```yaml
# ═══════════════════════════════════════════
# COMPREHENSIVE CI/CD WORKFLOW
# ═══════════════════════════════════════════

# .github/workflows/ci-cd.yml

name: CI/CD Pipeline

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main, develop]
  release:
    types: [created]

env:
  NODE_VERSION: "18.x"

jobs:
  # ═══════════════════════════════════════════
  # LINT
  # ═══════════════════════════════════════════
  lint:
    name: Lint Code
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: ${{ env.NODE_VERSION }}
          cache: "npm"

      - name: Install dependencies
        run: npm ci

      - name: Run ESLint
        run: npm run lint

      - name: Run Prettier
        run: npm run format:check

  # ═══════════════════════════════════════════
  # TEST
  # ═══════════════════════════════════════════
  test:
    name: Run Tests
    runs-on: ubuntu-latest

    strategy:
      matrix:
        node-version: [16.x, 18.x, 20.x]

    steps:
      - uses: actions/checkout@v3

      - name: Setup Node.js ${{ matrix.node-version }}
        uses: actions/setup-node@v3
        with:
          node-version: ${{ matrix.node-version }}
          cache: "npm"

      - name: Install dependencies
        run: npm ci

      - name: Run unit tests
        run: npm run test:unit

      - name: Run integration tests
        run: npm run test:integration

      - name: Generate coverage
        run: npm run test:coverage

      - name: Upload coverage to Codecov
        uses: codecov/codecov-action@v3
        with:
          files: ./coverage/coverage-final.json
          flags: unittests
          name: codecov-${{ matrix.node-version }}

  # ═══════════════════════════════════════════
  # BUILD
  # ═══════════════════════════════════════════
  build:
    name: Build Application
    runs-on: ubuntu-latest
    needs: [lint, test]

    steps:
      - uses: actions/checkout@v3

      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: ${{ env.NODE_VERSION }}
          cache: "npm"

      - name: Install dependencies
        run: npm ci

      - name: Build application
        run: npm run build
        env:
          NODE_ENV: production

      - name: Upload build artifacts
        uses: actions/upload-artifact@v3
        with:
          name: build-files
          path: dist/
          retention-days: 7

  # ═══════════════════════════════════════════
  # SECURITY SCAN
  # ═══════════════════════════════════════════
  security:
    name: Security Scan
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v3

      - name: Run npm audit
        run: npm audit --audit-level=high

      - name: Run Snyk security scan
        uses: snyk/actions/node@master
        env:
          SNYK_TOKEN: ${{ secrets.SNYK_TOKEN }}

      - name: Run Trivy vulnerability scanner
        uses: aquasecurity/trivy-action@master
        with:
          scan-type: "fs"
          scan-ref: "."
          format: "sarif"
          output: "trivy-results.sarif"

      - name: Upload Trivy results to GitHub Security
        uses: github/codeql-action/upload-sarif@v2
        with:
          sarif_file: "trivy-results.sarif"

  # ═══════════════════════════════════════════
  # DEPLOY TO STAGING
  # ═══════════════════════════════════════════
  deploy-staging:
    name: Deploy to Staging
    runs-on: ubuntu-latest
    needs: [build, security]
    if: github.ref == 'refs/heads/develop'

    environment:
      name: staging
      url: https://staging.myapp.com

    steps:
      - uses: actions/checkout@v3

      - name: Download build artifacts
        uses: actions/download-artifact@v3
        with:
          name: build-files
          path: dist/

      - name: Deploy to Vercel Staging
        uses: amondnet/vercel-action@v25
        with:
          vercel-token: ${{ secrets.VERCEL_TOKEN }}
          vercel-org-id: ${{ secrets.VERCEL_ORG_ID }}
          vercel-project-id: ${{ secrets.VERCEL_PROJECT_ID }}
          vercel-args: "--prod"

      - name: Run smoke tests
        run: |
          curl -f https://staging.myapp.com/health || exit 1

      - name: Notify team
        uses: 8398a7/action-slack@v3
        with:
          status: ${{ job.status }}
          text: "✅ Deployed to staging"
          webhook_url: ${{ secrets.SLACK_WEBHOOK }}

  # ═══════════════════════════════════════════
  # DEPLOY TO PRODUCTION
  # ═══════════════════════════════════════════
  deploy-production:
    name: Deploy to Production
    runs-on: ubuntu-latest
    needs: [build, security]
    if: github.ref == 'refs/heads/main'

    environment:
      name: production
      url: https://myapp.com

    steps:
      - uses: actions/checkout@v3

      - name: Download build artifacts
        uses: actions/download-artifact@v3
        with:
          name: build-files
          path: dist/

      - name: Deploy to production
        run: |
          # Your deployment script
          ./deploy-production.sh
        env:
          DEPLOY_KEY: ${{ secrets.DEPLOY_KEY }}

      - name: Run smoke tests
        run: |
          curl -f https://myapp.com/health || exit 1

      - name: Create Sentry release
        uses: getsentry/action-release@v1
        env:
          SENTRY_AUTH_TOKEN: ${{ secrets.SENTRY_AUTH_TOKEN }}
          SENTRY_ORG: myorg
          SENTRY_PROJECT: myproject
        with:
          environment: production

      - name: Notify team
        uses: 8398a7/action-slack@v3
        with:
          status: ${{ job.status }}
          text: "🚀 Deployed to production"
          webhook_url: ${{ secrets.SLACK_WEBHOOK }}

  # ═══════════════════════════════════════════
  # ROLLBACK (if deployment fails)
  # ═══════════════════════════════════════════
  rollback:
    name: Rollback Production
    runs-on: ubuntu-latest
    needs: deploy-production
    if: failure()

    steps:
      - name: Rollback deployment
        run: ./rollback.sh
        env:
          DEPLOY_KEY: ${{ secrets.DEPLOY_KEY }}

      - name: Notify team of rollback
        uses: 8398a7/action-slack@v3
        with:
          status: "failure"
          text: "⚠️ Production deployment failed. Rolling back..."
          webhook_url: ${{ secrets.SLACK_WEBHOOK }}
```

---

### Pre-commit Hooks with Husky 🐶

```bash
# ═══════════════════════════════════════════
# HUSKY + LINT-STAGED
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SETUP                                    ║
╚════════════════════════════════════════════════════════════╝

# Install
npm install --save-dev husky lint-staged

# Initialize Husky
npx husky-init

# Install hooks
npx husky install

╔════════════════════════════════════════════════════════════╗
║                   PRE-COMMIT HOOK                          ║
╚════════════════════════════════════════════════════════════╝

# .husky/pre-commit
#!/bin/sh
. "$(dirname "$0")/_/husky.sh"

echo "Running pre-commit checks..."

# Run lint-staged
npx lint-staged

# Run tests
npm run test:staged

echo "✓ Pre-commit checks passed!"

# Make executable
chmod +x .husky/pre-commit

╔════════════════════════════════════════════════════════════╗
║                   LINT-STAGED CONFIG                       ║
╚════════════════════════════════════════════════════════════╝

# package.json
{
  "lint-staged": {
    "*.{js,jsx,ts,tsx}": [
      "eslint --fix",
      "prettier --write",
      "git add"
    ],
    "*.{json,md,yml,yaml}": [
      "prettier --write",
      "git add"
    ],
    "*.{css,scss}": [
      "stylelint --fix",
      "prettier --write",
      "git add"
    ]
  }
}

╔════════════════════════════════════════════════════════════╗
║                   COMMIT-MSG HOOK                          ║
╚════════════════════════════════════════════════════════════╝

# .husky/commit-msg
#!/bin/sh
. "$(dirname "$0")/_/husky.sh"

# Validate commit message
npx --no-install commitlint --edit "$1"

# Make executable
chmod +x .husky/commit-msg

╔════════════════════════════════════════════════════════════╗
║                   PRE-PUSH HOOK                            ║
╚════════════════════════════════════════════════════════════╝

# .husky/pre-push
#!/bin/sh
. "$(dirname "$0")/_/husky.sh"

echo "Running pre-push checks..."

# Run all tests
npm run test

# Run build
npm run build

echo "✓ Pre-push checks passed!"

# Make executable
chmod +x .husky/pre-push

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 📋 Release Management

</div>

### Release Strategies 🎯

```bash
# ═══════════════════════════════════════════
# RELEASE STRATEGIES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   STRATEGY COMPARISON                      ║
╚════════════════════════════════════════════════════════════╝

```

<div align="center">

| Strategy              | Release Frequency | Risk    | Rollback | Best For              |
| --------------------- | ----------------- | ------- | -------- | --------------------- |
| **Manual Release**    | Weeks/Months      | ⬇️ Low  | Easy     | Traditional software  |
| **Scheduled Release** | Weekly/Bi-weekly  | ⬇️ Low  | Easy     | Enterprise apps       |
| **Continuous Deploy** | Multiple/day      | ⬆️ High | Complex  | Web apps, SaaS        |
| **Feature Flags**     | Continuous        | ⬇️ Low  | Instant  | Modern web apps       |
| **Canary Release**    | Continuous        | ⬇️ Low  | Easy     | High-traffic services |
| **Blue-Green**        | Any               | ⬇️ Low  | Instant  | Critical systems      |

</div>

```bash
# ═══════════════════════════════════════════
# RELEASE PROCESS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   STEP-BY-STEP RELEASE                     ║
╚════════════════════════════════════════════════════════════╝

# ─── STEP 1: Prepare Release Branch ───

git checkout develop
git pull origin develop
git checkout -b release/v2.0.0

# ─── STEP 2: Update Version ───

# package.json
npm version 2.0.0

# Or manually:
# Update version in:
# - package.json
# - package-lock.json
# - version.txt
# - README.md
# - Other version files

git commit -am "chore: bump version to 2.0.0"

# ─── STEP 3: Generate Changelog ───

# Auto-generate from commits
npx auto-changelog --output CHANGELOG.md

# Or manually write CHANGELOG.md:
cat << 'EOF' > CHANGELOG.md
# Changelog

## [2.0.0] - 2024-01-20

### Added
- User authentication system
- Dark mode
- Export functionality

### Changed
- Improved performance by 50%
- Updated UI components

### Fixed
- Login redirect issue
- Memory leak in data processor

### Breaking Changes
- API endpoint changed from /auth to /api/v2/auth
- Removed deprecated methods

### Migration Guide
\`\`\`bash
# Update API calls
- fetch('/auth')
+ fetch('/api/v2/auth')
\`\`\`

EOF

git add CHANGELOG.md
git commit -m "docs: update changelog for v2.0.0"

# ─── STEP 4: Update Documentation ───

# Update:
# - README.md
# - API documentation
# - User guides
# - Migration guides

git add docs/
git commit -m "docs: update documentation for v2.0.0"

# ─── STEP 5: Run Final Tests ───

npm run test:all
npm run test:e2e
npm run build

# ─── STEP 6: Push Release Branch ───

git push origin release/v2.0.0

# ─── STEP 7: Create Pull Requests ───

# PR to main (production)
gh pr create --base main --head release/v2.0.0 \
             --title "Release v2.0.0" \
             --body "Release v2.0.0"

# PR to develop (merge back)
# (Created after main merge)

# ─── STEP 8: Merge to Main ───

# After approval, merge PR to main
gh pr merge --squash

# ─── STEP 9: Tag Release ───

git checkout main
git pull origin main

# Create annotated tag
git tag -a v2.0.0 -m "Release v2.0.0

- User authentication
- Dark mode
- Export functionality

See CHANGELOG.md for full details"

# Push tag
git push origin v2.0.0

# ─── STEP 10: Create GitHub Release ───

# Via GitHub CLI
gh release create v2.0.0 \
  --title "v2.0.0" \
  --notes "$(cat CHANGELOG.md)" \
  dist/app.zip

# Or via UI:
# Releases → Draft a new release
# - Tag: v2.0.0
# - Title: v2.0.0
# - Description: Copy from CHANGELOG
# - Attach binaries if needed

# ─── STEP 11: Deploy ───

# Automatic deployment via CI/CD
# Or manual:
./deploy-production.sh v2.0.0

# ─── STEP 12: Merge Back to Develop ───

git checkout develop
git merge main
git push origin develop

# ─── STEP 13: Delete Release Branch ───

git branch -d release/v2.0.0
git push origin --delete release/v2.0.0

# ─── STEP 14: Monitor ───

# Monitor for 24-48 hours:
# - Error rates
# - Performance metrics
# - User feedback
# - Server resources

# ─── STEP 15: Announce Release ───

# - Blog post
# - Social media
# - Email newsletter
# - Documentation site

═══════════════════════════════════════════════════════════
```

---

### Hotfix Process 🚨

```bash
# ═══════════════════════════════════════════
# EMERGENCY HOTFIX WORKFLOW
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   HOTFIX PROCESS                           ║
╚════════════════════════════════════════════════════════════╝

# Critical bug in production (v2.0.0)!

# ─── STEP 1: Create Hotfix Branch from Main ───

git checkout main
git pull origin main
git checkout -b hotfix/v2.0.1

# ─── STEP 2: Fix the Bug ───

# Make minimal changes
git add src/payment/processor.js
git commit -m "fix: critical payment processing bug"

# ─── STEP 3: Update Version ───

npm version patch  # 2.0.0 → 2.0.1

git commit -am "chore: bump version to 2.0.1"

# ─── STEP 4: Update Changelog ───

cat << 'EOF' >> CHANGELOG.md

## [2.0.1] - 2024-01-21

### Fixed
- Critical payment processing bug causing transaction failures

EOF

git add CHANGELOG.md
git commit -m "docs: update changelog for v2.0.1"

# ─── STEP 5: Test ───

npm run test
npm run build

# ─── STEP 6: Create PR to Main ───

git push origin hotfix/v2.0.1

gh pr create --base main --head hotfix/v2.0.1 \
             --title "Hotfix v2.0.1: Critical payment bug" \
             --body "**URGENT**

Critical payment processing bug.

**Changes:**
- Fixed payment processor logic

**Testing:**
- Unit tests added
- Tested with production-like data" \
             --label "hotfix" \
             --label "urgent"

# ─── STEP 7: Expedited Review ───

# Get urgent review
# Merge immediately after approval

# ─── STEP 8: Tag & Release ───

git checkout main
git pull origin main

git tag -a v2.0.1 -m "Hotfix v2.0.1

Critical payment processing bug fix"

git push origin v2.0.1

gh release create v2.0.1 \
  --title "v2.0.1 (Hotfix)" \
  --notes "**Critical Hotfix**

Fixed payment processing bug causing transaction failures.

All users should update immediately."

# ─── STEP 9: Deploy Immediately ───

./deploy-production.sh v2.0.1

# ─── STEP 10: Merge to Develop ───

git checkout develop
git merge main
git push origin develop

# ─── STEP 11: Delete Hotfix Branch ───

git branch -d hotfix/v2.0.1
git push origin --delete hotfix/v2.0.1

# ─── STEP 12: Notify ───

# - Team notification
# - Customer notification (if needed)
# - Post-mortem document

# Total time: 30-60 minutes (vs 3 weeks for regular release)

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🎯 Real-World Scenarios

</div>

### Common Situations & Solutions 💡

```bash
# ═══════════════════════════════════════════
# REAL-WORLD GIT SCENARIOS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║       SCENARIO 1: ACCIDENTALLY COMMITTED TO WRONG BRANCH   ║
╚════════════════════════════════════════════════════════════╝

# Committed to main instead of feature branch

# Option A: Move commits to new branch
git branch feature/my-feature  # Create branch with current commits
git reset --hard origin/main   # Reset main to remote
git checkout feature/my-feature

# Option B: Cherry-pick to correct branch
git checkout main
git log  # Note commit hashes

git checkout -b feature/my-feature origin/main
git cherry-pick <commit-hash>

git checkout main
git reset --hard origin/main

╔════════════════════════════════════════════════════════════╗
║       SCENARIO 2: NEED TO UNDO LAST COMMIT                 ║
╚════════════════════════════════════════════════════════════╝

# Not yet pushed:
git reset --soft HEAD~1  # Keep changes staged
# Or
git reset HEAD~1         # Keep changes unstaged
# Or
git reset --hard HEAD~1  # Discard changes

# Already pushed:
git revert HEAD          # Create new commit that undoes

╔════════════════════════════════════════════════════════════╗
║       SCENARIO 3: MERGE CONFLICT                           ║
╚════════════════════════════════════════════════════════════╝

# During merge:
git merge feature-branch
# CONFLICT in file.txt

# View conflicts:
git status

# Open file.txt:
const value = 'feature branch';

# Fix conflict (choose one or combine):
const value = 'combined value';

# Stage and commit:
git add file.txt
git commit -m "fix: resolve merge conflict"

# Or abort:
git merge --abort

╔════════════════════════════════════════════════════════════╗
║       SCENARIO 4: ACCIDENTALLY DELETED COMMITS             ║
╚════════════════════════════════════════════════════════════╝

# Find lost commits:
git reflog

# Output:
# a1b2c3d HEAD@{0}: reset: moving to HEAD~1
# e4f5g6h HEAD@{1}: commit: my important commit
# ...

# Recover commit:
git cherry-pick e4f5g6h

# Or reset to that point:
git reset --hard e4f5g6h

╔════════════════════════════════════════════════════════════╗
║       SCENARIO 5: NEED TO EDIT COMMIT MESSAGE              ║
╚════════════════════════════════════════════════════════════╝

# Last commit (not pushed):
git commit --amend -m "new message"

# Last commit (already pushed):
git commit --amend -m "new message"
git push --force-with-lease

# Older commit:
git rebase -i HEAD~3  # Interactive rebase last 3 commits
# Change 'pick' to 'reword' for commits to edit
# Save and edit messages

╔════════════════════════════════════════════════════════════╗
║       SCENARIO 6: NEED TO REMOVE FILE FROM HISTORY         ║
╚════════════════════════════════════════════════════════════╝

# Accidentally committed secrets.txt

# Option A: filter-branch (old way)
git filter-branch --tree-filter 'rm -f secrets.txt' HEAD

# Option B: BFG Repo-Cleaner (recommended)
# Download BFG from: https://rtyley.github.io/bfg-repo-cleaner/
java -jar bfg.jar --delete-files secrets.txt

# Option C: git-filter-repo (modern way)
pip install git-filter-repo
git filter-repo --path secrets.txt --invert-paths

# Force push
git push --force --all

╔════════════════════════════════════════════════════════════╗
║       SCENARIO 7: SYNCHRONIZE FORK WITH UPSTREAM           ║
╚════════════════════════════════════════════════════════════╝

# Fork is behind upstream

git fetch upstream
git checkout main
git rebase upstream/main
git push origin main --force-with-lease

# If feature branch exists:
git checkout feature-branch
git rebase main
git push origin feature-branch --force-with-lease

╔════════════════════════════════════════════════════════════╗
║       SCENARIO 8: SPLIT COMMIT INTO MULTIPLE               ║
╚════════════════════════════════════════════════════════════╝

# Commit too large, need to split

git rebase -i HEAD~1
# Change 'pick' to 'edit'

git reset HEAD^

# Stage and commit separately:
git add file1.js
git commit -m "feat: add feature A"

git add file2.js
git commit -m "feat: add feature B"

git rebase --continue

╔════════════════════════════════════════════════════════════╗
║       SCENARIO 9: RECOVER DELETED BRANCH                   ║
╚════════════════════════════════════════════════════════════╝

# Accidentally deleted branch

# Find last commit:
git reflog
# Find: e4f5g6h HEAD@{3}: commit: last commit on deleted branch

# Recreate branch:
git checkout -b recovered-branch e4f5g6h

╔════════════════════════════════════════════════════════════╗
║       SCENARIO 10: CLEAN UP LOCAL BRANCHES                 ║
╚════════════════════════════════════════════════════════════╝

# Delete all merged branches:
git branch --merged main | grep -v "main" | xargs git branch -d

# Delete all local branches not on remote:
git fetch --prune
git branch -vv | grep ': gone]' | awk '{print $1}' | xargs git branch -D

# Or create alias:
git config --global alias.cleanup "!git branch --merged | grep -v '\\*\\|main\\|develop' | xargs -n 1 git branch -d"

# Usage:
git cleanup

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 💡 Pro Tips

</div>

### Git Productivity Hacks ⚡

```bash
# ═══════════════════════════════════════════
# ESSENTIAL GIT ALIASES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   POWERFUL ALIASES                         ║
╚════════════════════════════════════════════════════════════╝

# Add to ~/.gitconfig

[alias]
  # Status & Info
  s = status -sb
  st = status
  branches = branch -a
  tags = tag -l
  remotes = remote -v

  # Staging
  a = add
  aa = add --all
  unstage = reset HEAD --

  # Committing
  c = commit
  cm = commit -m
  ca = commit --amend
  cane = commit --amend --no-edit

  # Logs
  l = log --oneline --decorate --graph --all
  ll = log --oneline --decorate --graph --all -20
  lg = log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
  last = log -1 HEAD --stat

  # Diff
  d = diff
  ds = diff --staged
  dt = difftool

  # Branches
  co = checkout
  cob = checkout -b
  br = branch
  brd = branch -d
  brD = branch -D

  # Merge & Rebase
  m = merge
  mn = merge --no-ff
  rb = rebase
  rbi = rebase -i
  rbc = rebase --continue
  rba = rebase --abort

  # Pull & Push
  p = pull
  pom = pull origin main
  pod = pull origin develop
  ps = push
  pso = push origin
  psf = push --force-with-lease

  # Stash
  ss = stash
  sl = stash list
  sp = stash pop
  sa = stash apply
  sd = stash drop

  # Reset
  undo = reset --soft HEAD~1
  unstage = reset HEAD --
  discard = checkout --

  # Utilities
  sync = !git fetch upstream && git rebase upstream/main
  cleanup = !git branch --merged | grep -v '\\*\\|main\\|develop' | xargs -n 1 git branch -d
  overview = !git log --all --since='2 weeks' --oneline --no-merges

  # Find
  find = !git branch -a | grep -i

╔════════════════════════════════════════════════════════════╗
║                   USAGE EXAMPLES                           ║
╚════════════════════════════════════════════════════════════╝

# Quick commit:
git aa && git cm "feat: add feature"

# Beautiful log:
git lg

# Sync with upstream:
git sync

# Cleanup branches:
git cleanup

# Quick branch switch:
git co main

# Force push safely:
git psf

# ═══════════════════════════════════════════
# GIT CONFIGURATIONS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   ESSENTIAL CONFIG                         ║
╚════════════════════════════════════════════════════════════╝

# User info
git config --global user.name "Your Name"
git config --global user.email "you@example.com"

# Default editor
git config --global core.editor "code --wait"  # VS Code
git config --global core.editor "vim"          # Vim

# Default branch name
git config --global init.defaultBranch main

# Auto-correct typos
git config --global help.autocorrect 20

# Colors
git config --global color.ui auto

# Better diff
git config --global diff.algorithm histogram

# Reuse recorded conflict resolutions
git config --global rerere.enabled true

# Auto-squash
git config --global rebase.autosquash true

# Auto-stash before rebase
git config --global rebase.autoStash true

# Push current branch
git config --global push.default current

# Pull with rebase by default
git config --global pull.rebase true

# Prune on fetch
git config --global fetch.prune true

# Show branch in prompt
git config --global core.pager 'less -RFX'

╔════════════════════════════════════════════════════════════╗
║                   GIT IGNORE GLOBAL                        ║
╚════════════════════════════════════════════════════════════╝

# Create global gitignore
cat << 'EOF' > ~/.gitignore_global
# OS
.DS_Store
Thumbs.db
*.swp
*.swo
*~

# IDEs
.vscode/
.idea/
*.sublime-project
*.sublime-workspace

# Logs
*.log
npm-debug.log*

# Environment
.env
.env.local
.env.*.local

# Dependencies
node_modules/
vendor/

# Build
dist/
build/
*.min.js
*.min.css
EOF

git config --global core.excludesfile ~/.gitignore_global

# ═══════════════════════════════════════════
# PRODUCTIVITY SCRIPTS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   QUICK COMMIT SCRIPT                      ║
╚════════════════════════════════════════════════════════════╝

# ~/bin/gac (Git Add Commit)
#!/bin/bash

if [ -z "$1" ]; then
  echo "Usage: gac \"commit message\""
  exit 1
fi

git add --all
git commit -m "$1"

echo "✓ Changes committed"
echo "Run 'git push' to push changes"

# Make executable:
chmod +x ~/bin/gac

# Usage:
gac "feat: add new feature"

╔════════════════════════════════════════════════════════════╗
║                   BRANCH CLEANUP SCRIPT                    ║
╚════════════════════════════════════════════════════════════╝

# ~/bin/git-cleanup-branches
#!/bin/bash

echo "🧹 Cleaning up Git branches..."

# Fetch and prune
echo "Fetching and pruning..."
git fetch --prune

# Delete local branches that are gone on remote
echo "Deleting local branches that are gone on remote..."
git branch -vv | grep ': gone]' | awk '{print $1}' | xargs -r git branch -D

# Delete merged branches
echo "Deleting merged branches..."
git branch --merged main | grep -v "main\|develop" | xargs -r git branch -d

echo "✓ Cleanup complete!"
echo ""
echo "Remaining branches:"
git branch

# Make executable:
chmod +x ~/bin/git-cleanup-branches

╔════════════════════════════════════════════════════════════╗
║                   WORK IN PROGRESS SCRIPT                  ║
╚════════════════════════════════════════════════════════════╝

# ~/bin/wip
#!/bin/bash

# Save work in progress

git add --all
git commit -m "WIP: $(date +'%Y-%m-%d %H:%M')" --no-verify

echo "✓ Work in progress saved"

# Resume work:
# git reset HEAD~1

# Make executable:
chmod +x ~/bin/wip

═══════════════════════════════════════════════════════════
```

---

### Git Performance Tips 🚀

```bash
# ═══════════════════════════════════════════
# OPTIMIZE GIT PERFORMANCE
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SPEED UP GIT                             ║
╚════════════════════════════════════════════════════════════╝

# Garbage collection
git gc --aggressive --prune=now

# Optimize repository
git repack -Ad
git prune

# Configure for large repos
git config --global core.preloadindex true
git config --global core.fscache true
git config --global gc.auto 256

# Shallow clone (faster)
git clone --depth 1 https://github.com/user/repo.git

# Partial clone (sparse checkout)
git clone --filter=blob:none https://github.com/user/repo.git

# Single-branch clone
git clone --single-branch --branch main https://github.com/user/repo.git

╔════════════════════════════════════════════════════════════╗
║                   SPARSE CHECKOUT                          ║
╚════════════════════════════════════════════════════════════╝

# Clone only specific directories (monorepo)

git clone --filter=blob:none --sparse https://github.com/user/monorepo.git
cd monorepo

# Add specific paths
git sparse-checkout init --cone
git sparse-checkout set packages/frontend packages/shared

# Now only selected paths are checked out!

╔════════════════════════════════════════════════════════════╗
║                   GIT LFS (LARGE FILES)                    ║
╚════════════════════════════════════════════════════════════╝

# Install Git LFS
git lfs install

# Track large files
git lfs track "*.psd"
git lfs track "*.zip"
git lfs track "assets/**"

# Verify tracking
git lfs ls-files

# Clone with LFS
git lfs clone https://github.com/user/repo.git

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🎓 Quick Reference Card

</div>

```bash
# ═══════════════════════════════════════════
# GIT WORKFLOWS CHEAT SHEET
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   DAILY COMMANDS                           ║
╚════════════════════════════════════════════════════════════╝

# Start day
git pull origin main

# Create feature
git checkout -b feature/my-feature

# Work
git add .
git commit -m "feat: add feature"

# Sync with remote
git fetch origin
git rebase origin/main

# Push
git push origin feature/my-feature

# Create PR
gh pr create --fill

# After merge, cleanup
git checkout main
git pull origin main
git branch -d feature/my-feature

╔════════════════════════════════════════════════════════════╗
║                   WORKFLOW DECISION TREE                   ║
╚════════════════════════════════════════════════════════════╝

Team Size < 10?
  ├─ Yes → Feature Branch Workflow
  └─ No  → Continue...

Scheduled Releases?
  ├─ Yes → Git Flow
  └─ No  → Continue...

Continuous Deployment?
  ├─ Yes → GitHub Flow or Trunk-Based
  └─ No  → GitLab Flow

Multiple Environments?
  ├─ Yes → GitLab Flow
  └─ No  → GitHub Flow

Open Source?
  └─ Yes → Forking Workflow

╔════════════════════════════════════════════════════════════╗
║                   EMERGENCY COMMANDS                       ║
╚════════════════════════════════════════════════════════════╝

# Undo last commit (keep changes)
git reset --soft HEAD~1

# Discard all local changes
git reset --hard HEAD
git clean -fd

# Recover deleted branch
git reflog
git checkout -b recovered-branch <commit-hash>

# Abort merge/rebase
git merge --abort
git rebase --abort

# Force pull (lose local changes)
git fetch origin
git reset --hard origin/main

═══════════════════════════════════════════════════════════
```

---

<div align="center">

**🎉 You've mastered Git Workflows! 🎉**

**Remember:** _The best workflow is the one your team actually follows_ ✨

**Built with 🔀 by MrDib, for efficient developers**

**Happy Collaborating!** 🚀

---

### 🔗 Additional Resources

- [Git Official Documentation](https://git-scm.com/doc)
- [GitHub Flow](https://githubflow.github.io/)
- [GitLab Flow](https://docs.gitlab.com/ee/topics/gitlab_flow.html)
- [Atlassian Git Tutorials](https://www.atlassian.com/git/tutorials)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [Semantic Versioning](https://semver.org/)

</div>
