<div align="center">

# 🚀 GitHub Actions - Complete Guide

<img src="https://img.shields.io/badge/GitHub-Actions-blue?style=for-the-badge&logo=github-actions" alt="GitHub Actions">
<img src="https://img.shields.io/badge/CI%2FCD-Automated-green?style=for-the-badge" alt="CI/CD">
<img src="https://img.shields.io/badge/Level-Beginner_to_Advanced-orange?style=for-the-badge" alt="All Levels">

### _Automate, customize, and execute your software development workflows_ ⚡

**Because manual deployments are so 2015** 🎯

</div>

---

## 📚 Table of Contents

- [🎯 GitHub Actions Basics](#-github-actions-basics)
- [🔄 Essential Workflows](#-essential-workflows)
- [🎨 Advanced Patterns](#-advanced-patterns)
- [🔌 Popular Actions](#-popular-actions)
- [🛠️ Custom Actions](#️-custom-actions)
- [🔐 Secrets & Security](#-secrets--security)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 🎯 GitHub Actions Basics

</div>

### Understanding GitHub Actions 📖

```yaml
# ═══════════════════════════════════════════
# Basic Concepts
# ═══════════════════════════════════════════

# Workflow: Automated process defined in YAML
# Event: Triggers that start workflows (push, PR, schedule, etc.)
# Job: Set of steps executed on the same runner
# Step: Individual task (action or shell command)
# Action: Reusable unit of code
# Runner: Server that runs workflows

# ═══════════════════════════════════════════
# Workflow Syntax Overview
# ═══════════════════════════════════════════

name: Workflow Name                    # Display name
on: [push, pull_request]              # Trigger events
env:                                  # Environment variables
  NODE_VERSION: '20'
jobs:                                 # Jobs to run
  job-name:
    runs-on: ubuntu-latest           # Runner type
    steps:                           # Steps to execute
      - name: Step name
        uses: actions/checkout@v4    # Use an action
      - name: Run command
        run: npm install             # Run shell command

# ═══════════════════════════════════════════
# Your First Workflow
# ═══════════════════════════════════════════
# .github/workflows/hello-world.yml

name: Hello World

on:
  push:
    branches: [main]

jobs:
  hello:
    runs-on: ubuntu-latest

    steps:
      - name: Say hello
        run: echo "Hello, GitHub Actions! 👋"

      - name: Show date
        run: date

      - name: List files
        run: ls -la
```

---

### Workflow Triggers 🎯

```yaml
# ═══════════════════════════════════════════
# Push Events
# ═══════════════════════════════════════════

on:
  push:
    branches:
      - main
      - develop
      - 'feature/*'      # Wildcard pattern
    paths:
      - 'src/**'         # Only when src/ changes
      - '**.js'          # Only when JS files change
    paths-ignore:
      - 'docs/**'        # Ignore docs changes
      - '**.md'          # Ignore markdown

# ═══════════════════════════════════════════
# Pull Request Events
# ═══════════════════════════════════════════

on:
  pull_request:
    types:
      - opened
      - synchronize      # New commits pushed
      - reopened
      - ready_for_review
    branches:
      - main
      - develop

# ═══════════════════════════════════════════
# Schedule (Cron)
# ═══════════════════════════════════════════

on:
  schedule:
    - cron: '0 0 * * *'        # Daily at midnight
    - cron: '*/15 * * * *'     # Every 15 minutes
    - cron: '0 9 * * 1-5'      # Weekdays at 9 AM

# Cron format: minute hour day month day-of-week
# * = any value
# */n = every n units
# n-m = range from n to m

# ═══════════════════════════════════════════
# Manual Trigger (workflow_dispatch)
# ═══════════════════════════════════════════

on:
  workflow_dispatch:
    inputs:
      environment:
        description: 'Environment to deploy'
        required: true
        type: choice
        options:
          - staging
          - production
      debug:
        description: 'Enable debug mode'
        required: false
        type: boolean
        default: false
      version:
        description: 'Version to deploy'
        required: true
        default: 'latest'

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Echo inputs
        run: |
          echo "Environment: ${{ inputs.environment }}"
          echo "Debug: ${{ inputs.debug }}"
          echo "Version: ${{ inputs.version }}"

# ═══════════════════════════════════════════
# Repository Events
# ═══════════════════════════════════════════

on:
  issues:
    types: [opened, labeled]
  issue_comment:
    types: [created]
  release:
    types: [published]
  fork:
  watch:
    types: [started]

# ═══════════════════════════════════════════
# Multiple Events
# ═══════════════════════════════════════════

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]
  schedule:
    - cron: '0 0 * * 0'  # Weekly
  workflow_dispatch:     # Manual trigger
```

---

<div align="center">

## 🔄 Essential Workflows

</div>

### Node.js CI/CD 🟢

```yaml
# ═══════════════════════════════════════════
# .github/workflows/node-ci-cd.yml
# Complete Node.js CI/CD Pipeline
# ═══════════════════════════════════════════

name: Node.js CI/CD

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main, develop]

env:
  NODE_VERSION: "20"

jobs:
  # ═══════════════════════════════════════════
  # Setup & Install
  # ═══════════════════════════════════════════
  setup:
    name: Setup & Install
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: ${{ env.NODE_VERSION }}
          cache: "npm"

      - name: Cache node modules
        uses: actions/cache@v3
        id: cache-npm
        with:
          path: node_modules
          key: ${{ runner.os }}-node-${{ hashFiles('**/package-lock.json') }}
          restore-keys: |
            ${{ runner.os }}-node-

      - name: Install dependencies
        if: steps.cache-npm.outputs.cache-hit != 'true'
        run: npm ci

      - name: Upload node_modules
        uses: actions/upload-artifact@v3
        with:
          name: node_modules
          path: node_modules
          retention-days: 1

  # ═══════════════════════════════════════════
  # Lint
  # ═══════════════════════════════════════════
  lint:
    name: Lint Code
    runs-on: ubuntu-latest
    needs: setup

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: ${{ env.NODE_VERSION }}

      - name: Download node_modules
        uses: actions/download-artifact@v3
        with:
          name: node_modules
          path: node_modules

      - name: Run ESLint
        run: npm run lint

      - name: Run Prettier
        run: npm run format:check

      - name: Annotate code with lint results
        uses: ataylorme/eslint-annotate-action@v2
        if: always()
        with:
          repo-token: ${{ secrets.GITHUB_TOKEN }}
          report-json: "eslint-report.json"

  # ═══════════════════════════════════════════
  # Type Check
  # ═══════════════════════════════════════════
  type-check:
    name: Type Check
    runs-on: ubuntu-latest
    needs: setup

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: ${{ env.NODE_VERSION }}

      - name: Download node_modules
        uses: actions/download-artifact@v3
        with:
          name: node_modules
          path: node_modules

      - name: Run TypeScript compiler
        run: npm run type-check

  # ═══════════════════════════════════════════
  # Test
  # ═══════════════════════════════════════════
  test:
    name: Test
    runs-on: ubuntu-latest
    needs: setup

    strategy:
      matrix:
        node-version: [18, 20]

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Setup Node.js ${{ matrix.node-version }}
        uses: actions/setup-node@v4
        with:
          node-version: ${{ matrix.node-version }}

      - name: Download node_modules
        uses: actions/download-artifact@v3
        with:
          name: node_modules
          path: node_modules

      - name: Run tests
        run: npm test -- --coverage

      - name: Upload coverage to Codecov
        uses: codecov/codecov-action@v3
        with:
          token: ${{ secrets.CODECOV_TOKEN }}
          files: ./coverage/coverage-final.json
          flags: unittests
          name: codecov-umbrella

      - name: Upload test results
        uses: actions/upload-artifact@v3
        if: always()
        with:
          name: test-results
          path: |
            coverage/
            test-results/

  # ═══════════════════════════════════════════
  # Build
  # ═══════════════════════════════════════════
  build:
    name: Build
    runs-on: ubuntu-latest
    needs: [lint, type-check, test]

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: ${{ env.NODE_VERSION }}

      - name: Download node_modules
        uses: actions/download-artifact@v3
        with:
          name: node_modules
          path: node_modules

      - name: Build application
        run: npm run build
        env:
          NODE_ENV: production

      - name: Upload build artifacts
        uses: actions/upload-artifact@v3
        with:
          name: build
          path: |
            dist/
            build/
            .next/
          retention-days: 7

  # ═══════════════════════════════════════════
  # Deploy to Staging
  # ═══════════════════════════════════════════
  deploy-staging:
    name: Deploy to Staging
    runs-on: ubuntu-latest
    needs: build
    if: github.ref == 'refs/heads/develop'
    environment:
      name: staging
      url: https://staging.example.com

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Download build artifacts
        uses: actions/download-artifact@v3
        with:
          name: build

      - name: Deploy to Vercel
        uses: amondnet/vercel-action@v25
        with:
          vercel-token: ${{ secrets.VERCEL_TOKEN }}
          vercel-org-id: ${{ secrets.VERCEL_ORG_ID }}
          vercel-project-id: ${{ secrets.VERCEL_PROJECT_ID }}
          vercel-args: "--prod"
          working-directory: ./

      - name: Comment on PR
        if: github.event_name == 'pull_request'
        uses: actions/github-script@v7
        with:
          script: |
            github.rest.issues.createComment({
              issue_number: context.issue.number,
              owner: context.repo.owner,
              repo: context.repo.repo,
              body: '✅ Deployed to staging: https://staging.example.com'
            })

  # ═══════════════════════════════════════════
  # Deploy to Production
  # ═══════════════════════════════════════════
  deploy-production:
    name: Deploy to Production
    runs-on: ubuntu-latest
    needs: build
    if: github.ref == 'refs/heads/main'
    environment:
      name: production
      url: https://example.com

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Download build artifacts
        uses: actions/download-artifact@v3
        with:
          name: build

      - name: Deploy to Vercel
        uses: amondnet/vercel-action@v25
        with:
          vercel-token: ${{ secrets.VERCEL_TOKEN }}
          vercel-org-id: ${{ secrets.VERCEL_ORG_ID }}
          vercel-project-id: ${{ secrets.VERCEL_PROJECT_ID }}
          vercel-args: "--prod"
          working-directory: ./

      - name: Create GitHub Release
        uses: actions/create-release@v1
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        with:
          tag_name: v${{ github.run_number }}
          release_name: Release v${{ github.run_number }}
          draft: false
          prerelease: false

      - name: Notify Slack
        uses: slackapi/slack-github-action@v1
        with:
          payload: |
            {
              "text": "🚀 Production deployment successful!",
              "blocks": [
                {
                  "type": "section",
                  "text": {
                    "type": "mrkdwn",
                    "text": "*Production Deployment*\n✅ Successfully deployed to production\nVersion: v${{ github.run_number }}\n<${{ github.event.repository.html_url }}/commit/${{ github.sha }}|View commit>"
                  }
                }
              ]
            }
        env:
          SLACK_WEBHOOK_URL: ${{ secrets.SLACK_WEBHOOK_URL }}
```

---

### Python CI/CD 🐍

```yaml
# ═══════════════════════════════════════════
# .github/workflows/python-ci-cd.yml
# Python Testing & Deployment
# ═══════════════════════════════════════════

name: Python CI/CD

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]

jobs:
  test:
    name: Test Python ${{ matrix.python-version }}
    runs-on: ${{ matrix.os }}

    strategy:
      fail-fast: false
      matrix:
        os: [ubuntu-latest, macos-latest, windows-latest]
        python-version: ["3.9", "3.10", "3.11", "3.12"]

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Set up Python ${{ matrix.python-version }}
        uses: actions/setup-python@v5
        with:
          python-version: ${{ matrix.python-version }}
          cache: "pip"

      - name: Install dependencies
        run: |
          python -m pip install --upgrade pip
          pip install -r requirements.txt
          pip install -r requirements-dev.txt

      - name: Lint with flake8
        run: |
          pip install flake8
          flake8 . --count --select=E9,F63,F7,F82 --show-source --statistics
          flake8 . --count --exit-zero --max-complexity=10 --max-line-length=127 --statistics

      - name: Format check with black
        run: |
          pip install black
          black --check .

      - name: Type check with mypy
        run: |
          pip install mypy
          mypy src/

      - name: Test with pytest
        run: |
          pip install pytest pytest-cov
          pytest --cov=src --cov-report=xml --cov-report=html

      - name: Upload coverage
        uses: codecov/codecov-action@v3
        with:
          files: ./coverage.xml
          flags: unittests
          name: codecov-${{ matrix.os }}-py${{ matrix.python-version }}

  build:
    name: Build package
    runs-on: ubuntu-latest
    needs: test

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Set up Python
        uses: actions/setup-python@v5
        with:
          python-version: "3.11"

      - name: Install build tools
        run: |
          python -m pip install --upgrade pip
          pip install build twine

      - name: Build package
        run: python -m build

      - name: Check package
        run: twine check dist/*

      - name: Upload artifacts
        uses: actions/upload-artifact@v3
        with:
          name: dist
          path: dist/

  publish:
    name: Publish to PyPI
    runs-on: ubuntu-latest
    needs: build
    if: github.event_name == 'push' && startsWith(github.ref, 'refs/tags')

    steps:
      - name: Download artifacts
        uses: actions/download-artifact@v3
        with:
          name: dist
          path: dist/

      - name: Publish to PyPI
        uses: pypa/gh-action-pypi-publish@release/v1
        with:
          password: ${{ secrets.PYPI_API_TOKEN }}
```

---

### Docker Build & Push 🐳

```yaml
# ═══════════════════════════════════════════
# .github/workflows/docker.yml
# Build and push Docker images
# ═══════════════════════════════════════════

name: Docker Build & Push

on:
  push:
    branches: [main, develop]
    tags:
      - "v*"
  pull_request:
    branches: [main]

env:
  REGISTRY: ghcr.io
  IMAGE_NAME: ${{ github.repository }}

jobs:
  build-and-push:
    name: Build and Push Docker Image
    runs-on: ubuntu-latest
    permissions:
      contents: read
      packages: write

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Set up QEMU
        uses: docker/setup-qemu-action@v3

      - name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v3

      - name: Log in to Container Registry
        uses: docker/login-action@v3
        with:
          registry: ${{ env.REGISTRY }}
          username: ${{ github.actor }}
          password: ${{ secrets.GITHUB_TOKEN }}

      - name: Extract metadata
        id: meta
        uses: docker/metadata-action@v5
        with:
          images: ${{ env.REGISTRY }}/${{ env.IMAGE_NAME }}
          tags: |
            type=ref,event=branch
            type=ref,event=pr
            type=semver,pattern={{version}}
            type=semver,pattern={{major}}.{{minor}}
            type=semver,pattern={{major}}
            type=sha,prefix={{branch}}-
            type=raw,value=latest,enable={{is_default_branch}}

      - name: Build and push
        uses: docker/build-push-action@v5
        with:
          context: .
          platforms: linux/amd64,linux/arm64
          push: ${{ github.event_name != 'pull_request' }}
          tags: ${{ steps.meta.outputs.tags }}
          labels: ${{ steps.meta.outputs.labels }}
          cache-from: type=gha
          cache-to: type=gha,mode=max
          build-args: |
            BUILD_DATE=${{ fromJSON(steps.meta.outputs.json).labels['org.opencontainers.image.created'] }}
            VERSION=${{ fromJSON(steps.meta.outputs.json).labels['org.opencontainers.image.version'] }}

      - name: Scan image for vulnerabilities
        uses: aquasecurity/trivy-action@master
        with:
          image-ref: ${{ env.REGISTRY }}/${{ env.IMAGE_NAME }}:${{ steps.meta.outputs.version }}
          format: "sarif"
          output: "trivy-results.sarif"

      - name: Upload scan results
        uses: github/codeql-action/upload-sarif@v2
        with:
          sarif_file: "trivy-results.sarif"
```

---

<div align="center">

## 🎨 Advanced Patterns

</div>

### Matrix Builds 🔢

```yaml
# ═══════════════════════════════════════════
# Test across multiple versions/platforms
# ═══════════════════════════════════════════

name: Matrix Build

on: [push, pull_request]

jobs:
  test:
    name: Test on ${{ matrix.os }} with Node ${{ matrix.node }}
    runs-on: ${{ matrix.os }}

    strategy:
      # Don't cancel all jobs if one fails
      fail-fast: false

      matrix:
        os: [ubuntu-latest, windows-latest, macos-latest]
        node: [18, 20]
        # Exclude specific combinations
        exclude:
          - os: macos-latest
            node: 18
        # Include additional combinations
        include:
          - os: ubuntu-latest
            node: 20
            experimental: true

    steps:
      - uses: actions/checkout@v4

      - name: Setup Node.js ${{ matrix.node }}
        uses: actions/setup-node@v4
        with:
          node-version: ${{ matrix.node }}

      - name: Install dependencies
        run: npm ci

      - name: Run tests
        run: npm test
        continue-on-error: ${{ matrix.experimental || false }}

# ═══════════════════════════════════════════
# Dynamic Matrix from JSON
# ═══════════════════════════════════════════

jobs:
  generate-matrix:
    runs-on: ubuntu-latest
    outputs:
      matrix: ${{ steps.set-matrix.outputs.matrix }}
    steps:
      - uses: actions/checkout@v4
      - id: set-matrix
        run: |
          MATRIX=$(cat .github/test-matrix.json)
          echo "matrix=$MATRIX" >> $GITHUB_OUTPUT

  test:
    needs: generate-matrix
    runs-on: ${{ matrix.os }}
    strategy:
      matrix: ${{ fromJSON(needs.generate-matrix.outputs.matrix) }}
    steps:
      - run: echo "Testing on ${{ matrix.os }}"
```

---

### Reusable Workflows 🔄

```yaml
# ═══════════════════════════════════════════
# .github/workflows/reusable-build.yml
# Reusable workflow for building
# ═══════════════════════════════════════════

name: Reusable Build Workflow

on:
  workflow_call:
    inputs:
      node-version:
        required: false
        type: string
        default: '20'
      environment:
        required: true
        type: string
    outputs:
      build-id:
        description: "Build identifier"
        value: ${{ jobs.build.outputs.build-id }}
    secrets:
      deploy-token:
        required: true

jobs:
  build:
    name: Build for ${{ inputs.environment }}
    runs-on: ubuntu-latest
    outputs:
      build-id: ${{ steps.build.outputs.id }}

    steps:
      - uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: ${{ inputs.node-version }}

      - name: Build
        id: build
        run: |
          npm ci
          npm run build
          echo "id=${{ github.run_id }}" >> $GITHUB_OUTPUT

      - name: Deploy
        env:
          DEPLOY_TOKEN: ${{ secrets.deploy-token }}
        run: |
          echo "Deploying to ${{ inputs.environment }}"

# ═══════════════════════════════════════════
# .github/workflows/caller.yml
# Workflow that calls the reusable workflow
# ═══════════════════════════════════════════

name: Build & Deploy

on:
  push:
    branches: [main, develop]

jobs:
  build-staging:
    uses: ./.github/workflows/reusable-build.yml
    with:
      node-version: '20'
      environment: 'staging'
    secrets:
      deploy-token: ${{ secrets.STAGING_DEPLOY_TOKEN }}

  build-production:
    if: github.ref == 'refs/heads/main'
    needs: build-staging
    uses: ./.github/workflows/reusable-build.yml
    with:
      node-version: '20'
      environment: 'production'
    secrets:
      deploy-token: ${{ secrets.PROD_DEPLOY_TOKEN }}
```

---

### Composite Actions 🧩

```yaml
# ═══════════════════════════════════════════
# .github/actions/setup-node-cache/action.yml
# Composite action for Node.js setup with caching
# ═══════════════════════════════════════════

name: "Setup Node.js with Cache"
description: "Setup Node.js and restore npm cache"

inputs:
  node-version:
    description: "Node.js version"
    required: false
    default: "20"
  cache-dependency-path:
    description: "Path to package-lock.json"
    required: false
    default: "**/package-lock.json"

outputs:
  cache-hit:
    description: "Whether cache was hit"
    value: ${{ steps.cache.outputs.cache-hit }}

runs:
  using: "composite"
  steps:
    - name: Setup Node.js
      uses: actions/setup-node@v4
      with:
        node-version: ${{ inputs.node-version }}

    - name: Get npm cache directory
      id: npm-cache-dir
      shell: bash
      run: echo "dir=$(npm config get cache)" >> $GITHUB_OUTPUT

    - name: Cache npm dependencies
      id: cache
      uses: actions/cache@v3
      with:
        path: ${{ steps.npm-cache-dir.outputs.dir }}
        key: ${{ runner.os }}-node-${{ hashFiles(inputs.cache-dependency-path) }}
        restore-keys: |
          ${{ runner.os }}-node-

    - name: Install dependencies
      if: steps.cache.outputs.cache-hit != 'true'
      shell: bash
      run: npm ci

# Usage in workflow:
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: ./.github/actions/setup-node-cache
        with:
          node-version: "20"
```

---

<div align="center">

## 🔌 Popular Actions

</div>

### Essential Actions Library 📚

```yaml
# ═══════════════════════════════════════════
# Code Checkout & Setup
# ═══════════════════════════════════════════

- name: Checkout code
  uses: actions/checkout@v4
  with:
    fetch-depth: 0 # Full history
    submodules: recursive # Include submodules
    token: ${{ secrets.PAT }} # Custom token

- name: Setup Node.js
  uses: actions/setup-node@v4
  with:
    node-version: "20"
    cache: "npm"
    registry-url: "https://registry.npmjs.org"

- name: Setup Python
  uses: actions/setup-python@v5
  with:
    python-version: "3.11"
    cache: "pip"

- name: Setup Go
  uses: actions/setup-go@v5
  with:
    go-version: "1.21"
    cache: true

- name: Setup Java
  uses: actions/setup-java@v4
  with:
    distribution: "temurin"
    java-version: "17"
    cache: "gradle"

# ═══════════════════════════════════════════
# Caching
# ═══════════════════════════════════════════

- name: Cache dependencies
  uses: actions/cache@v3
  with:
    path: |
      ~/.npm
      ~/.cache
      node_modules
    key: ${{ runner.os }}-deps-${{ hashFiles('**/package-lock.json') }}
    restore-keys: |
      ${{ runner.os }}-deps-

- name: Cache build
  uses: actions/cache@v3
  with:
    path: |
      dist
      .next
      build
    key: ${{ runner.os }}-build-${{ github.sha }}

# ═══════════════════════════════════════════
# Artifacts
# ═══════════════════════════════════════════

- name: Upload artifacts
  uses: actions/upload-artifact@v3
  with:
    name: build-artifacts
    path: |
      dist/
      build/
    retention-days: 7
    if-no-files-found: error

- name: Download artifacts
  uses: actions/download-artifact@v3
  with:
    name: build-artifacts
    path: ./build

# ═══════════════════════════════════════════
# Code Quality & Security
# ═══════════════════════════════════════════

- name: Run CodeQL Analysis
  uses: github/codeql-action/init@v2
  with:
    languages: javascript, python
    queries: security-and-quality

- name: ESLint Annotate
  uses: ataylorme/eslint-annotate-action@v2
  with:
    repo-token: ${{ secrets.GITHUB_TOKEN }}
    report-json: eslint-report.json

- name: SonarCloud Scan
  uses: SonarSource/sonarcloud-github-action@master
  env:
    GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
    SONAR_TOKEN: ${{ secrets.SONAR_TOKEN }}

- name: Snyk Security Scan
  uses: snyk/actions/node@master
  env:
    SNYK_TOKEN: ${{ secrets.SNYK_TOKEN }}

- name: Trivy Vulnerability Scan
  uses: aquasecurity/trivy-action@master
  with:
    scan-type: "fs"
    scan-ref: "."
    format: "sarif"
    output: "trivy-results.sarif"

# ═══════════════════════════════════════════
# Testing
# ═══════════════════════════════════════════

- name: Run Cypress tests
  uses: cypress-io/github-action@v6
  with:
    build: npm run build
    start: npm start
    wait-on: "http://localhost:3000"
    browser: chrome

- name: Playwright tests
  uses: microsoft/playwright-github-action@v1

- name: Upload coverage to Codecov
  uses: codecov/codecov-action@v3
  with:
    token: ${{ secrets.CODECOV_TOKEN }}
    files: ./coverage/coverage-final.json
    flags: unittests
    name: codecov-umbrella

# ═══════════════════════════════════════════
# Deployment
# ═══════════════════════════════════════════

- name: Deploy to Vercel
  uses: amondnet/vercel-action@v25
  with:
    vercel-token: ${{ secrets.VERCEL_TOKEN }}
    vercel-org-id: ${{ secrets.VERCEL_ORG_ID }}
    vercel-project-id: ${{ secrets.VERCEL_PROJECT_ID }}
    vercel-args: "--prod"

- name: Deploy to Netlify
  uses: netlify/actions/cli@master
  with:
    args: deploy --prod
  env:
    NETLIFY_AUTH_TOKEN: ${{ secrets.NETLIFY_AUTH_TOKEN }}
    NETLIFY_SITE_ID: ${{ secrets.NETLIFY_SITE_ID }}

- name: Deploy to Heroku
  uses: akhileshns/heroku-deploy@v3.12.14
  with:
    heroku_api_key: ${{ secrets.HEROKU_API_KEY }}
    heroku_app_name: "my-app"
    heroku_email: "email@example.com"

- name: Deploy to AWS S3
  uses: jakejarvis/s3-sync-action@master
  with:
    args: --acl public-read --follow-symlinks --delete
  env:
    AWS_S3_BUCKET: ${{ secrets.AWS_S3_BUCKET }}
    AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
    AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
    SOURCE_DIR: "dist"

# ═══════════════════════════════════════════
# Notifications
# ═══════════════════════════════════════════

- name: Slack Notification
  uses: slackapi/slack-github-action@v1
  with:
    payload: |
      {
        "text": "Build completed: ${{ job.status }}",
        "blocks": [
          {
            "type": "section",
            "text": {
              "type": "mrkdwn",
              "text": "*${{ github.workflow }}* - ${{ job.status }}\n<${{ github.event.repository.html_url }}/actions/runs/${{ github.run_id }}|View Run>"
            }
          }
        ]
      }
  env:
    SLACK_WEBHOOK_URL: ${{ secrets.SLACK_WEBHOOK_URL }}

- name: Discord Notification
  uses: sarisia/actions-status-discord@v1
  with:
    webhook: ${{ secrets.DISCORD_WEBHOOK }}
    status: ${{ job.status }}
    title: "Build Status"

- name: Microsoft Teams Notification
  uses: aliencube/microsoft-teams-actions@v0.8.0
  with:
    webhook_uri: ${{ secrets.TEAMS_WEBHOOK }}
    title: ${{ github.workflow }}
    summary: Build ${{ job.status }}

# ═══════════════════════════════════════════
# Git Operations
# ═══════════════════════════════════════════

- name: Create Release
  uses: actions/create-release@v1
  env:
    GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
  with:
    tag_name: ${{ github.ref }}
    release_name: Release ${{ github.ref }}
    draft: false
    prerelease: false

- name: Create Pull Request
  uses: peter-evans/create-pull-request@v5
  with:
    token: ${{ secrets.GITHUB_TOKEN }}
    commit-message: Update dependencies
    title: "chore: update dependencies"
    body: Auto-generated dependency updates
    branch: dependency-updates

- name: Label PRs
  uses: actions/labeler@v5
  with:
    repo-token: ${{ secrets.GITHUB_TOKEN }}

# ═══════════════════════════════════════════
# Container Operations
# ═══════════════════════════════════════════

- name: Build Docker Image
  uses: docker/build-push-action@v5
  with:
    context: .
    push: true
    tags: user/app:latest
    cache-from: type=gha
    cache-to: type=gha,mode=max

- name: Docker Compose
  uses: isbang/compose-action@v1.5.1
  with:
    compose-file: "./docker-compose.yml"
    up-flags: "--build"

# ═══════════════════════════════════════════
# Utilities
# ═══════════════════════════════════════════

- name: Read file contents
  id: read-file
  uses: andstor/file-reader-action@v1
  with:
    path: "./VERSION"

- name: String manipulation
  uses: frabert/replace-string-action@v2
  id: format
  with:
    pattern: 'v(\d+\.\d+\.\d+)'
    string: ${{ github.ref }}
    replace-with: "$1"

- name: Wait for URL
  uses: nev7n/wait_for_response@v1
  with:
    url: "https://example.com"
    responseCode: 200
    timeout: 60000
    interval: 1000
```

---

<div align="center">

## 🛠️ Custom Actions

</div>

### JavaScript Action 📜

```javascript
// ═══════════════════════════════════════════
// .github/actions/hello-world/action.yml
// ═══════════════════════════════════════════

name: 'Hello World'
description: 'Greet someone and record the time'
author: 'MrDib'

inputs:
  who-to-greet:
    description: 'Who to greet'
    required: true
    default: 'World'

outputs:
  time:
    description: 'The time we greeted you'

runs:
  using: 'node20'
  main: 'index.js'

branding:
  icon: 'message-circle'
  color: 'blue'

// ═══════════════════════════════════════════
// .github/actions/hello-world/index.js
// ═══════════════════════════════════════════

const core = require('@actions/core');
const github = require('@actions/github');

try {
  // Get inputs
  const nameToGreet = core.getInput('who-to-greet');
  console.log(`Hello ${nameToGreet}!`);

  // Get the current time
  const time = new Date().toTimeString();

  // Set outputs
  core.setOutput('time', time);

  // Get the JSON webhook payload for the event
  const payload = JSON.stringify(github.context.payload, undefined, 2);
  console.log(`The event payload: ${payload}`);

  // Set environment variable
  core.exportVariable('GREETING_TIME', time);

  // Add to PATH
  core.addPath('/custom/path');

  // Create annotations
  core.notice('This is a notice');
  core.warning('This is a warning');
  core.error('This is an error');

  // Group logs
  core.startGroup('My group');
  console.log('Inside the group');
  core.endGroup();

  // Set secret
  core.setSecret(nameToGreet);

} catch (error) {
  core.setFailed(error.message);
}

// ═══════════════════════════════════════════
// .github/actions/hello-world/package.json
// ═══════════════════════════════════════════

{
  "name": "hello-world-action",
  "version": "1.0.0",
  "main": "index.js",
  "dependencies": {
    "@actions/core": "^1.10.0",
    "@actions/github": "^6.0.0"
  }
}

// ═══════════════════════════════════════════
// Usage in workflow
// ═══════════════════════════════════════════

jobs:
  hello:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: ./.github/actions/hello-world
        id: hello
        with:
          who-to-greet: 'MrDib'
      - name: Get the output time
        run: echo "The time was ${{ steps.hello.outputs.time }}"
```

---

### Docker Action 🐳

```dockerfile
# ═══════════════════════════════════════════
# .github/actions/docker-hello/Dockerfile
# ═══════════════════════════════════════════

FROM alpine:3.18

# Install dependencies
RUN apk add --no-cache bash curl jq

# Copy entrypoint script
COPY entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh

ENTRYPOINT ["/entrypoint.sh"]
```

```yaml
# ═══════════════════════════════════════════
# .github/actions/docker-hello/action.yml
# ═══════════════════════════════════════════

name: "Docker Hello World"
description: "A Docker-based action"

inputs:
  name:
    description: "Your name"
    required: true

outputs:
  greeting:
    description: "The greeting message"

runs:
  using: "docker"
  image: "Dockerfile"
  args:
    - ${{ inputs.name }}
```

```bash
# ═══════════════════════════════════════════
# .github/actions/docker-hello/entrypoint.sh
# ═══════════════════════════════════════════

#!/bin/bash
set -e

NAME=$1

echo "Hello, $NAME!"

# Set output
echo "greeting=Hello, $NAME!" >> $GITHUB_OUTPUT

# Use GitHub Actions toolkit
echo "::notice::This is a notice from Docker action"
```

---

### Composite Action with Multiple Steps 🧩

```yaml
# ═══════════════════════════════════════════
# .github/actions/setup-and-test/action.yml
# Complete setup and test action
# ═══════════════════════════════════════════

name: "Setup and Test"
description: "Setup environment and run tests"

inputs:
  node-version:
    description: "Node.js version"
    required: false
    default: "20"
  run-e2e:
    description: "Run E2E tests"
    required: false
    default: "false"

outputs:
  coverage:
    description: "Test coverage percentage"
    value: ${{ steps.test.outputs.coverage }}

runs:
  using: "composite"
  steps:
    - name: Setup Node.js
      uses: actions/setup-node@v4
      with:
        node-version: ${{ inputs.node-version }}
        cache: "npm"

    - name: Install dependencies
      shell: bash
      run: |
        echo "Installing dependencies..."
        npm ci

    - name: Run linter
      shell: bash
      run: npm run lint

    - name: Run unit tests
      id: test
      shell: bash
      run: |
        npm run test -- --coverage
        COVERAGE=$(cat coverage/coverage-summary.json | jq '.total.lines.pct')
        echo "coverage=$COVERAGE" >> $GITHUB_OUTPUT

    - name: Run E2E tests
      if: inputs.run-e2e == 'true'
      shell: bash
      run: npm run test:e2e

    - name: Upload coverage
      uses: codecov/codecov-action@v3
      with:
        files: ./coverage/coverage-final.json

# Usage:
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: ./.github/actions/setup-and-test
        with:
          node-version: "20"
          run-e2e: "true"
```

---

<div align="center">

## 🔐 Secrets & Security

</div>

### Managing Secrets 🔑

```yaml
# ═══════════════════════════════════════════
# Using Secrets in Workflows
# ═══════════════════════════════════════════

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Deploy with secrets
        env:
          # Access secrets via ${{ secrets.NAME }}
          API_KEY: ${{ secrets.API_KEY }}
          DATABASE_URL: ${{ secrets.DATABASE_URL }}
          AWS_ACCESS_KEY: ${{ secrets.AWS_ACCESS_KEY_ID }}
          AWS_SECRET_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
        run: |
          echo "Deploying with API key..."
          # Secrets are automatically masked in logs
          echo "API_KEY: $API_KEY"  # Will show: API_KEY: ***

# ═══════════════════════════════════════════
# Environment Secrets
# ═══════════════════════════════════════════

jobs:
  deploy-staging:
    runs-on: ubuntu-latest
    environment:
      name: staging
      url: https://staging.example.com
    steps:
      - name: Deploy
        env:
          # Environment-specific secrets
          DEPLOY_TOKEN: ${{ secrets.STAGING_DEPLOY_TOKEN }}
        run: deploy.sh

  deploy-production:
    runs-on: ubuntu-latest
    environment:
      name: production
      url: https://example.com
    steps:
      - name: Deploy
        env:
          DEPLOY_TOKEN: ${{ secrets.PRODUCTION_DEPLOY_TOKEN }}
        run: deploy.sh

# ═══════════════════════════════════════════
# Passing Secrets to Reusable Workflows
# ═══════════════════════════════════════════

jobs:
  call-workflow:
    uses: ./.github/workflows/reusable.yml
    secrets:
      token: ${{ secrets.DEPLOY_TOKEN }}
    # Or pass all secrets
    secrets: inherit

# ═══════════════════════════════════════════
# Creating Secrets from Workflow
# ═══════════════════════════════════════════

- name: Create secret
  uses: actions/github-script@v7
  with:
    script: |
      const sodium = require('tweetsodium');

      // Get public key
      const { data: { key, key_id } } = await github.rest.actions.getRepoPublicKey({
        owner: context.repo.owner,
        repo: context.repo.repo
      });

      // Encrypt secret
      const messageBytes = Buffer.from('my-secret-value');
      const keyBytes = Buffer.from(key, 'base64');
      const encryptedBytes = sodium.seal(messageBytes, keyBytes);
      const encrypted = Buffer.from(encryptedBytes).toString('base64');

      // Create secret
      await github.rest.actions.createOrUpdateRepoSecret({
        owner: context.repo.owner,
        repo: context.repo.repo,
        secret_name: 'MY_SECRET',
        encrypted_value: encrypted,
        key_id: key_id
      });

# ═══════════════════════════════════════════
# Security Best Practices
# ═══════════════════════════════════════════

# ✅ DO: Pin action versions
uses: actions/checkout@8e5e7e5ab8b370d6c329ec480221332ada57f0ab  # v3.5.2

# ❌ DON'T: Use @main or @master
uses: actions/checkout@main  # Dangerous!

# ✅ DO: Use GITHUB_TOKEN with minimal permissions
permissions:
  contents: read
  pull-requests: write

# ✅ DO: Validate inputs
- name: Validate input
  run: |
    if [[ ! "${{ inputs.environment }}" =~ ^(staging|production)$ ]]; then
      echo "Invalid environment"
      exit 1
    fi

# ✅ DO: Use CODEOWNERS for workflow changes
# .github/CODEOWNERS
/.github/workflows/ @security-team

# ✅ DO: Enable branch protection
# Settings → Branches → Add rule
# - Require pull request reviews
# - Require status checks
# - Include administrators
```

---

### Security Scanning 🔍

```yaml
# ═══════════════════════════════════════════
# .github/workflows/security.yml
# Comprehensive security scanning
# ═══════════════════════════════════════════

name: Security Scan

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]
  schedule:
    - cron: "0 0 * * 0" # Weekly

jobs:
  # Dependency scanning
  dependency-scan:
    name: Dependency Scan
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Run npm audit
        run: npm audit --audit-level=moderate
        continue-on-error: true

      - name: Run Snyk
        uses: snyk/actions/node@master
        env:
          SNYK_TOKEN: ${{ secrets.SNYK_TOKEN }}
        with:
          args: --severity-threshold=high

  # Code scanning
  codeql:
    name: CodeQL Analysis
    runs-on: ubuntu-latest
    permissions:
      security-events: write
      actions: read
      contents: read

    strategy:
      matrix:
        language: ["javascript", "typescript"]

    steps:
      - uses: actions/checkout@v4

      - name: Initialize CodeQL
        uses: github/codeql-action/init@v2
        with:
          languages: ${{ matrix.language }}
          queries: security-extended,security-and-quality

      - name: Autobuild
        uses: github/codeql-action/autobuild@v2

      - name: Perform CodeQL Analysis
        uses: github/codeql-action/analyze@v2

  # Secret scanning
  secret-scan:
    name: Secret Scan
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0

      - name: TruffleHog Scan
        uses: trufflesecurity/trufflehog@main
        with:
          path: ./
          base: ${{ github.event.repository.default_branch }}
          head: HEAD

  # Container scanning
  container-scan:
    name: Container Scan
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Build image
        run: docker build -t myapp:test .

      - name: Scan with Trivy
        uses: aquasecurity/trivy-action@master
        with:
          image-ref: "myapp:test"
          format: "sarif"
          output: "trivy-results.sarif"

      - name: Upload results
        uses: github/codeql-action/upload-sarif@v2
        with:
          sarif_file: "trivy-results.sarif"

  # License compliance
  license-check:
    name: License Check
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: "20"

      - name: Install dependencies
        run: npm ci

      - name: Check licenses
        run: npx license-checker --summary --production --onlyAllow="MIT;Apache-2.0;BSD-2-Clause;BSD-3-Clause;ISC"
```

---

<div align="center">

## 💡 Best Practices

</div>

### Workflow Optimization 🚀

```yaml
# ═══════════════════════════════════════════
# 1. Use Caching Effectively
# ═══════════════════════════════════════════

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      # ✅ Cache dependencies
      - name: Cache node modules
        uses: actions/cache@v3
        with:
          path: node_modules
          key: ${{ runner.os }}-node-${{ hashFiles('**/package-lock.json') }}
          restore-keys: |
            ${{ runner.os }}-node-

      # ✅ Cache build output
      - name: Cache build
        uses: actions/cache@v3
        with:
          path: |
            .next/cache
            dist
          key: ${{ runner.os }}-build-${{ github.sha }}

# ═══════════════════════════════════════════
# 2. Parallelize Jobs
# ═══════════════════════════════════════════

jobs:
  # Run these jobs in parallel
  lint:
    runs-on: ubuntu-latest
    steps:
      - run: npm run lint

  test:
    runs-on: ubuntu-latest
    steps:
      - run: npm test

  type-check:
    runs-on: ubuntu-latest
    steps:
      - run: npm run type-check

  # This job waits for all parallel jobs
  build:
    needs: [lint, test, type-check]
    runs-on: ubuntu-latest
    steps:
      - run: npm run build

# ═══════════════════════════════════════════
# 3. Conditional Execution
# ═══════════════════════════════════════════

jobs:
  deploy:
    runs-on: ubuntu-latest
    # Only run on main branch
    if: github.ref == 'refs/heads/main'
    steps:
      - run: deploy.sh

  test-e2e:
    runs-on: ubuntu-latest
    # Skip on draft PRs
    if: github.event.pull_request.draft == false
    steps:
      - run: npm run test:e2e

# ═══════════════════════════════════════════
# 4. Timeout & Retry
# ═══════════════════════════════════════════

jobs:
  flaky-test:
    runs-on: ubuntu-latest
    timeout-minutes: 10  # Timeout after 10 minutes
    steps:
      - name: Run flaky tests with retry
        uses: nick-fields/retry-action@v2
        with:
          timeout_minutes: 5
          max_attempts: 3
          command: npm run test:flaky

# ═══════════════════════════════════════════
# 5. Cleanup & Resource Management
# ═══════════════════════════════════════════

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Build
        run: npm run build

      # Always cleanup, even on failure
      - name: Cleanup
        if: always()
        run: rm -rf node_modules dist

# ═══════════════════════════════════════════
# 6. Prevent Duplicate Runs
# ═══════════════════════════════════════════

name: CI

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

concurrency:
  group: ${{ github.workflow }}-${{ github.ref }}
  cancel-in-progress: true  # Cancel previous runs

# ═══════════════════════════════════════════
# 7. Path Filtering
# ═══════════════════════════════════════════

on:
  push:
    paths:
      - 'src/**'
      - 'package.json'
      - 'package-lock.json'
    paths-ignore:
      - '**.md'
      - 'docs/**'

# ═══════════════════════════════════════════
# 8. Job Outputs
# ═══════════════════════════════════════════

jobs:
  setup:
    runs-on: ubuntu-latest
    outputs:
      version: ${{ steps.get-version.outputs.version }}
    steps:
      - id: get-version
        run: echo "version=$(cat package.json | jq -r .version)" >> $GITHUB_OUTPUT

  deploy:
    needs: setup
    runs-on: ubuntu-latest
    steps:
      - run: echo "Deploying version ${{ needs.setup.outputs.version }}"

# ═══════════════════════════════════════════
# 9. Environment Variables
# ═══════════════════════════════════════════

env:
  # Global env vars
  NODE_VERSION: '20'
  CACHE_KEY: v1

jobs:
  build:
    runs-on: ubuntu-latest
    env:
      # Job-level env vars
      BUILD_ENV: production
    steps:
      - name: Build
        env:
          # Step-level env vars
          CUSTOM_VAR: value
        run: npm run build
```

---

### Debugging Workflows 🔍

```yaml
# ═══════════════════════════════════════════
# Enable Debug Logging
# ═══════════════════════════════════════════

# Set these secrets in your repository:
# ACTIONS_STEP_DEBUG = true
# ACTIONS_RUNNER_DEBUG = true

# ═══════════════════════════════════════════
# Debug Steps
# ═══════════════════════════════════════════

jobs:
  debug:
    runs-on: ubuntu-latest
    steps:
      - name: Dump GitHub context
        env:
          GITHUB_CONTEXT: ${{ toJson(github) }}
        run: echo "$GITHUB_CONTEXT"

      - name: Dump job context
        env:
          JOB_CONTEXT: ${{ toJson(job) }}
        run: echo "$JOB_CONTEXT"

      - name: Dump runner context
        env:
          RUNNER_CONTEXT: ${{ toJson(runner) }}
        run: echo "$RUNNER_CONTEXT"

      - name: Show environment
        run: env | sort

      - name: Show PATH
        run: echo $PATH | tr ':' '\n'

# ═══════════════════════════════════════════
# Test Workflows Locally with Act
# ═══════════════════════════════════════════

# Install act
brew install act

# Run workflow locally
act

# Run specific job
act -j test

# Run with secrets
act -s GITHUB_TOKEN=xxx

# Use specific event
act push

# Dry run
act -n
```

---

<div align="center">

## 🎓 Resources & Learning

</div>

### Essential Resources 📚

```
📘 Official Documentation
   GitHub Actions Docs: https://docs.github.com/actions
   Workflow Syntax: https://docs.github.com/actions/reference/workflow-syntax-for-github-actions
   Action Marketplace: https://github.com/marketplace?type=actions

📗 Learning Resources
   GitHub Actions Learning Path: https://docs.github.com/en/actions/learn-github-actions
   Awesome Actions: https://github.com/sdras/awesome-actions
   Act (Local testing): https://github.com/nektos/act

📙 Example Repositories
   Actions Starter Workflows: https://github.com/actions/starter-workflows
   GitHub Actions Examples: https://github.com/actions/examples

🎥 Video Tutorials
   GitHub Actions Tutorial (freeCodeCamp)
   CI/CD with GitHub Actions (Traversy Media)
   GitHub Actions Deep Dive (DevOps Journey)

🛠️ Tools
   Action Validator: https://rhysd.github.io/actionlint/
   Workflow Visualizer: https://github.com/githubocto/flat-viewer
   VS Code Extension: GitHub Actions

📊 Best Practices
   Security Hardening: https://docs.github.com/actions/security-guides
   Workflow Templates: https://github.com/actions/starter-workflows

🌐 Community
   GitHub Community Discussions
   r/github (Reddit)
   GitHub Actions Discord
```

---

<div align="center">

**Built with 🚀 by the GitHub community**

_Automate everything, deploy with confidence!_ ✨

**Happy CI/CD-ing!** 🎉

</div>
