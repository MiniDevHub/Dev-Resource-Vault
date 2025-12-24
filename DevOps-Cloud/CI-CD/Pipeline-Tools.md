<div align="center">

# ⚙️ CI/CD Pipeline Tools

### _Because manually deploying code is like manually compiling your CSS - technically possible, but why?_ 🚀

![CI/CD](https://img.shields.io/badge/CI%2FCD-Automated-blue?style=for-the-badge)
![Tools](https://img.shields.io/badge/Tools-25+-green?style=for-the-badge)
![Efficiency](https://img.shields.io/badge/Delivery-10x_Faster-gold?style=for-the-badge)
![Cloud Native](https://img.shields.io/badge/Cloud-Native-success?style=for-the-badge)

</div>

---

## 📚 Table of Contents

- [🎯 Understanding CI/CD Pipelines](#-understanding-cicd-pipelines)
- [🏆 Tool Comparison Matrix](#-tool-comparison-matrix)
- [🐙 GitHub Actions](#-github-actions)
- [🦊 GitLab CI/CD](#-gitlab-cicd)
- [🔵 Azure DevOps](#-azure-devops)
- [⚫ CircleCI](#-circleci)
- [🟢 Jenkins](#-jenkins)
- [🚀 Modern Cloud-Native Tools](#-modern-cloud-native-tools)
- [🎯 Specialized Tools](#-specialized-tools)
- [💰 Cost Comparison](#-cost-comparison)
- [🤖 AI-Powered CI/CD](#-ai-powered-cicd)
- [🔐 Security in CI/CD](#-security-in-cicd)
- [⚡ Performance Optimization](#-performance-optimization)
- [🎯 Choosing the Right Tool](#-choosing-the-right-tool)
- [💡 Best Practices](#-best-practices)
- [🐛 Common Issues & Solutions](#-common-issues--solutions)

---

<div align="center">

## 🎯 Understanding CI/CD Pipelines

_The foundation before the tools_ 📖

</div>

### The CI/CD Pipeline Flow

```
┌─────────────────────────────────────────────────────────────────────┐
│                    COMPLETE CI/CD PIPELINE FLOW                      │
└─────────────────────────────────────────────────────────────────────┘

1. 💻 CODE → Developer commits code
   ├── Git commit & push to branch
   ├── Trigger: Webhook/Poll/PR
   └── ✅ Pipeline starts automatically

2. 🔍 LINT & FORMAT → Code quality checks
   ├── ESLint, Prettier, Black, etc.
   ├── Type checking (TypeScript, mypy)
   ├── Code style enforcement
   └── ✅ Clean code verified

3. 🏗️ BUILD → Compile/bundle code
   ├── Install dependencies
   ├── Compile (if needed)
   ├── Bundle assets (Webpack, Vite)
   ├── Generate source maps
   └── ✅ Build artifacts created

4. 🧪 TEST → Automated testing
   ├── Unit tests (Jest, pytest)
   ├── Integration tests
   ├── E2E tests (Playwright, Cypress)
   ├── Coverage reports
   └── ✅ All tests passing

5. 🔒 SECURITY → Security scanning
   ├── Dependency scanning (Snyk, Dependabot)
   ├── SAST (Static Analysis)
   ├── Secret scanning
   ├── License compliance
   └── ✅ No vulnerabilities found

6. 📦 PACKAGE → Create deployable artifact
   ├── Docker image build
   ├── Tag with version
   ├── Push to registry (GHCR, ECR, Docker Hub)
   ├── Sign image (Cosign)
   └── ✅ Artifact ready

7. 🚀 DEPLOY → Release to environment
   ├── Deploy to staging (automatic)
   ├── Run smoke tests
   ├── Deploy to production (manual/auto)
   ├── Blue-green/canary deployment
   └── ✅ Live in production

8. 📊 MONITOR → Watch for issues
   ├── Error tracking (Sentry)
   ├── Performance metrics (Datadog)
   ├── User analytics
   ├── Alert on anomalies
   └── ✅ System healthy

9. 🔄 FEEDBACK → Continuous improvement
   ├── Deployment metrics
   ├── DORA metrics tracking
   ├── Post-deployment review
   └── ✅ Learn and improve
```

---

### CI vs CD vs CD (Expanded)

<div align="center">

| Concept | Full Name              | What It Does                 | When It Runs     | Human Involvement | Risk Level | Best For             |
| :------ | :--------------------- | :--------------------------- | :--------------- | :---------------- | :--------- | :------------------- |
| **CI**  | Continuous Integration | Merge & test code frequently | Every commit     | None (automated)  | 🟢 Low     | All projects         |
| **CD**  | Continuous Delivery    | Always ready to deploy       | After CI passes  | Deploy button     | 🟡 Medium  | Most production apps |
| **CD**  | Continuous Deployment  | Auto-deploy every change     | After tests pass | None (full auto)  | 🔴 High    | Mature teams only    |

</div>

---

<div align="center">

## 🏆 Tool Comparison Matrix

_The ultimate comparison for 2025_ 📊

</div>

### Complete CI/CD Tool Comparison

<div align="center">

| Tool                    | Type              | Pricing           | Learning Curve | Best For          | GitHub Integration | Kubernetes Support | Self-Hosted | Market Share |
| :---------------------- | :---------------- | :---------------- | :------------- | :---------------- | :----------------- | :----------------- | :---------- | :----------- |
| **GitHub Actions**      | Cloud/Hybrid      | Free tier + usage | ⭐⭐           | GitHub projects   | ⭐⭐⭐⭐⭐         | ⭐⭐⭐⭐           | Yes         | 🔥 Very High |
| **GitLab CI/CD**        | Cloud/Self-hosted | Free tier + paid  | ⭐⭐⭐         | Full DevOps       | ⭐⭐⭐⭐           | ⭐⭐⭐⭐⭐         | Yes         | High         |
| **Jenkins**             | Self-hosted       | Free (OSS)        | ⭐⭐⭐⭐⭐     | Complex pipelines | ⭐⭐⭐⭐           | ⭐⭐⭐⭐           | Yes         | High         |
| **CircleCI**            | Cloud/Self-hosted | Free tier + usage | ⭐⭐           | Speed & scale     | ⭐⭐⭐⭐⭐         | ⭐⭐⭐⭐           | Yes         | Medium       |
| **Azure DevOps**        | Cloud/Self-hosted | Free tier + paid  | ⭐⭐⭐         | Microsoft stack   | ⭐⭐⭐⭐           | ⭐⭐⭐⭐           | Yes         | Medium       |
| **TeamCity**            | Cloud/Self-hosted | Free tier + paid  | ⭐⭐⭐⭐       | JetBrains users   | ⭐⭐⭐⭐           | ⭐⭐⭐⭐           | Yes         | Medium       |
| **Bitbucket Pipelines** | Cloud             | Free tier + paid  | ⭐⭐           | Atlassian stack   | ⭐⭐⭐             | ⭐⭐⭐             | No          | Medium       |
| **Harness**             | Cloud             | Commercial        | ⭐⭐⭐         | AI-driven CD      | ⭐⭐⭐⭐           | ⭐⭐⭐⭐⭐         | Yes         | Growing      |
| **Argo CD**             | Cloud-native      | Free (OSS)        | ⭐⭐⭐⭐       | GitOps K8s        | ⭐⭐⭐⭐⭐         | ⭐⭐⭐⭐⭐         | Yes         | Growing      |
| **Tekton**              | Cloud-native      | Free (OSS)        | ⭐⭐⭐⭐⭐     | Kubernetes-native | ⭐⭐⭐⭐           | ⭐⭐⭐⭐⭐         | Yes         | Niche        |

</div>

---

### Decision Tree - Which Tool Should You Use?

```
🎯 Which CI/CD Tool is Right for You?

Are you using GitHub?
├─ Yes
│  ├─ Simple workflows?
│  │  └─ ✅ GitHub Actions (native, easy, powerful)
│  └─ Need extreme performance?
│     └─ ✅ CircleCI (fast, scalable)
└─ No
   ├─ Using GitLab?
   │  └─ ✅ GitLab CI/CD (integrated, full DevOps)
   ├─ Using Bitbucket?
   │  └─ ✅ Bitbucket Pipelines (Atlassian ecosystem)
   ├─ Using Azure repos?
   │  └─ ✅ Azure DevOps (Microsoft integration)
   ├─ Need maximum flexibility?
   │  └─ ✅ Jenkins (plugins galore, self-hosted)
   ├─ Kubernetes-first?
   │  └─ ✅ Argo CD or Tekton (cloud-native)
   └─ AI-powered deployments?
      └─ ✅ Harness (ML-driven CD)

Still unsure?
└─ Start with GitHub Actions
   Most modern, easiest to learn, free tier is generous
```

---

<div align="center">

## 🐙 GitHub Actions

_The modern standard for CI/CD_ 🌟

</div>

### Why GitHub Actions?

```
✅ PROS:
• Native GitHub integration (zero setup)
• Free for public repos
• 2,000 free minutes/month for private repos
• Huge marketplace of actions
• Runs on GitHub's infrastructure
• Matrix builds (test across OS/versions)
• Self-hosted runners supported
• Great documentation
• Active community

❌ CONS:
• Can get expensive for heavy private repo usage
• Less flexible than Jenkins for complex needs
• Tied to GitHub ecosystem

🎯 USE WHEN:
✓ Your code is on GitHub
✓ Want minimal setup
✓ Need quick CI/CD
✓ Building modern apps
✓ Want marketplace actions
```

---

### GitHub Actions - Complete Setup

```yaml
# ═══════════════════════════════════════════════════════════
# GITHUB ACTIONS - PRODUCTION-READY CI/CD
# .github/workflows/ci-cd.yml
# ═══════════════════════════════════════════════════════════

name: CI/CD Pipeline

on:
  # Trigger on push to main or PR
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]
  # Manual trigger
  workflow_dispatch:

# Cancel in-progress runs for same workflow
concurrency:
  group: ${{ github.workflow }}-${{ github.ref }}
  cancel-in-progress: true

env:
  NODE_VERSION: "20.x"
  REGISTRY: ghcr.io
  IMAGE_NAME: ${{ github.repository }}

jobs:
  # ═══════════════════════════════════════════════════════════
  # JOB 1: CODE QUALITY & LINTING
  # ═══════════════════════════════════════════════════════════
  lint:
    name: 🔍 Lint & Format Check
    runs-on: ubuntu-latest

    steps:
      - name: 📥 Checkout code
        uses: actions/checkout@v4

      - name: 🟢 Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: ${{ env.NODE_VERSION }}
          cache: "npm"

      - name: 📦 Install dependencies
        run: npm ci

      - name: 🎨 Check code formatting
        run: npm run format:check

      - name: 🔍 Run ESLint
        run: npm run lint

      - name: 📝 TypeScript check
        run: npm run type-check

  # ═══════════════════════════════════════════════════════════
  # JOB 2: BUILD & TEST
  # ═══════════════════════════════════════════════════════════
  test:
    name: 🧪 Test (Node ${{ matrix.node-version }} on ${{ matrix.os }})
    runs-on: ${{ matrix.os }}
    needs: lint

    strategy:
      matrix:
        os: [ubuntu-latest, windows-latest, macos-latest]
        node-version: ["18.x", "20.x"]
        # Don't fail all jobs if one fails
        fail-fast: false

    steps:
      - name: 📥 Checkout code
        uses: actions/checkout@v4

      - name: 🟢 Setup Node.js ${{ matrix.node-version }}
        uses: actions/setup-node@v4
        with:
          node-version: ${{ matrix.node-version }}
          cache: "npm"

      - name: 📦 Install dependencies
        run: npm ci

      - name: 🏗️ Build
        run: npm run build

      - name: 🧪 Run unit tests
        run: npm run test:unit -- --coverage

      - name: 🔗 Run integration tests
        run: npm run test:integration

      - name: 📊 Upload coverage to Codecov
        uses: codecov/codecov-action@v3
        with:
          files: ./coverage/coverage-final.json
          flags: ${{ matrix.os }}-${{ matrix.node-version }}

  # ═══════════════════════════════════════════════════════════
  # JOB 3: E2E TESTS
  # ═══════════════════════════════════════════════════════════
  e2e:
    name: 🎭 E2E Tests
    runs-on: ubuntu-latest
    needs: lint

    steps:
      - name: 📥 Checkout code
        uses: actions/checkout@v4

      - name: 🟢 Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: ${{ env.NODE_VERSION }}
          cache: "npm"

      - name: 📦 Install dependencies
        run: npm ci

      - name: 📦 Install Playwright
        run: npx playwright install --with-deps

      - name: 🏗️ Build application
        run: npm run build

      - name: 🚀 Start test server
        run: npm run preview &
        env:
          PORT: 3000

      - name: ⏳ Wait for server
        run: npx wait-on http://localhost:3000

      - name: 🎭 Run Playwright tests
        run: npm run test:e2e

      - name: 📸 Upload test screenshots
        if: failure()
        uses: actions/upload-artifact@v3
        with:
          name: playwright-screenshots
          path: test-results/

  # ═══════════════════════════════════════════════════════════
  # JOB 4: SECURITY SCANNING
  # ═══════════════════════════════════════════════════════════
  security:
    name: 🔒 Security Scan
    runs-on: ubuntu-latest
    needs: lint

    steps:
      - name: 📥 Checkout code
        uses: actions/checkout@v4

      - name: 🔍 Run Trivy vulnerability scanner
        uses: aquasecurity/trivy-action@master
        with:
          scan-type: "fs"
          scan-ref: "."
          format: "sarif"
          output: "trivy-results.sarif"

      - name: 📤 Upload Trivy results to GitHub Security
        uses: github/codeql-action/upload-sarif@v2
        with:
          sarif_file: "trivy-results.sarif"

      - name: 🔐 Check for secrets
        uses: trufflesecurity/trufflehog@main
        with:
          path: ./
          base: ${{ github.event.repository.default_branch }}
          head: HEAD

  # ═══════════════════════════════════════════════════════════
  # JOB 5: BUILD & PUSH DOCKER IMAGE
  # ═══════════════════════════════════════════════════════════
  docker:
    name: 🐳 Build & Push Docker Image
    runs-on: ubuntu-latest
    needs: [test, e2e, security]
    if: github.ref == 'refs/heads/main'

    permissions:
      contents: read
      packages: write

    steps:
      - name: 📥 Checkout code
        uses: actions/checkout@v4

      - name: 🔐 Login to GitHub Container Registry
        uses: docker/login-action@v3
        with:
          registry: ${{ env.REGISTRY }}
          username: ${{ github.actor }}
          password: ${{ secrets.GITHUB_TOKEN }}

      - name: 📝 Extract metadata
        id: meta
        uses: docker/metadata-action@v5
        with:
          images: ${{ env.REGISTRY }}/${{ env.IMAGE_NAME }}
          tags: |
            type=ref,event=branch
            type=ref,event=pr
            type=semver,pattern={{version}}
            type=semver,pattern={{major}}.{{minor}}
            type=sha,prefix={{branch}}-

      - name: 🏗️ Set up Docker Buildx
        uses: docker/setup-buildx-action@v3

      - name: 🐳 Build and push Docker image
        uses: docker/build-push-action@v5
        with:
          context: .
          push: true
          tags: ${{ steps.meta.outputs.tags }}
          labels: ${{ steps.meta.outputs.labels }}
          cache-from: type=gha
          cache-to: type=gha,mode=max
          platforms: linux/amd64,linux/arm64

  # ═══════════════════════════════════════════════════════════
  # JOB 6: DEPLOY TO PRODUCTION
  # ═══════════════════════════════════════════════════════════
  deploy:
    name: 🚀 Deploy to Production
    runs-on: ubuntu-latest
    needs: docker
    if: github.ref == 'refs/heads/main'
    environment:
      name: production
      url: https://myapp.com

    steps:
      - name: 📥 Checkout code
        uses: actions/checkout@v4

      - name: 🔧 Configure kubectl
        uses: azure/k8s-set-context@v3
        with:
          method: kubeconfig
          kubeconfig: ${{ secrets.KUBE_CONFIG }}

      - name: 🚀 Deploy to Kubernetes
        run: |
          kubectl set image deployment/myapp \
            myapp=${{ env.REGISTRY }}/${{ env.IMAGE_NAME }}:main \
            --record

          kubectl rollout status deployment/myapp

      - name: 🎯 Run smoke tests
        run: |
          curl -f https://myapp.com/health || exit 1

      - name: 📢 Notify Slack
        if: success()
        uses: slackapi/slack-github-action@v1
        with:
          webhook-url: ${{ secrets.SLACK_WEBHOOK }}
          payload: |
            {
              "text": "✅ Deployment successful: ${{ github.repository }}@${{ github.sha }}"
            }

      - name: 🚨 Notify on failure
        if: failure()
        uses: slackapi/slack-github-action@v1
        with:
          webhook-url: ${{ secrets.SLACK_WEBHOOK }}
          payload: |
            {
              "text": "❌ Deployment failed: ${{ github.repository }}@${{ github.sha }}"
            }
```

---

### GitHub Actions - Advanced Features

```yaml
# ═══════════════════════════════════════════════════════════
# REUSABLE WORKFLOWS
# .github/workflows/reusable-build.yml
# ═══════════════════════════════════════════════════════════

name: Reusable Build Workflow

on:
  workflow_call:
    inputs:
      node-version:
        required: true
        type: string
      environment:
        required: true
        type: string
    outputs:
      artifact-url:
        description: "URL of built artifact"
        value: ${{ jobs.build.outputs.url }}
    secrets:
      deploy-token:
        required: true

jobs:
  build:
    runs-on: ubuntu-latest
    outputs:
      url: ${{ steps.upload.outputs.artifact-url }}

    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: ${{ inputs.node-version }}

      - run: npm ci
      - run: npm run build

      - id: upload
        uses: actions/upload-artifact@v3
        with:
          name: build-${{ inputs.environment }}
          path: dist/
```

**Use the reusable workflow:**

```yaml
# .github/workflows/main.yml
name: Use Reusable Workflow

on: [push]

jobs:
  build-staging:
    uses: ./.github/workflows/reusable-build.yml
    with:
      node-version: "20.x"
      environment: "staging"
    secrets:
      deploy-token: ${{ secrets.STAGING_TOKEN }}
```

---

<div align="center">

## 🦊 GitLab CI/CD

_The complete DevOps platform_ 🎯

</div>

### Why GitLab CI/CD?

```
✅ PROS:
• All-in-one DevOps platform
• Built-in container registry
• Auto DevOps (zero config)
• Excellent Kubernetes integration
• Free for unlimited private repos
• Self-hosted option
• Built-in security scanning
• Merge request pipelines
• Review apps
• Environment management

❌ CONS:
• GitLab-specific (vendor lock-in)
• Can be resource-heavy
• Steeper learning curve

🎯 USE WHEN:
✓ Want complete DevOps platform
✓ Need self-hosted solution
✓ Kubernetes deployments
✓ Security is priority
✓ Want GitOps workflows
```

---

### GitLab CI/CD - Complete Pipeline

```yaml
# ═══════════════════════════════════════════════════════════
# GITLAB CI/CD - PRODUCTION-READY PIPELINE
# .gitlab-ci.yml
# ═══════════════════════════════════════════════════════════

# Global settings
image: node:20

# Variables
variables:
  DOCKER_DRIVER: overlay2
  DOCKER_TLS_CERTDIR: "/certs"
  KUBERNETES_VERSION: "1.28"
  # Cache settings
  npm_config_cache: "$CI_PROJECT_DIR/.npm"
  CYPRESS_CACHE_FOLDER: "$CI_PROJECT_DIR/.cache/Cypress"

# Stages
stages:
  - validate
  - build
  - test
  - security
  - package
  - deploy

# Cache configuration
cache:
  key:
    files:
      - package-lock.json
  paths:
    - .npm
    - node_modules
    - .cache

# ═══════════════════════════════════════════════════════════
# STAGE 1: VALIDATE
# ═══════════════════════════════════════════════════════════

lint:code:
  stage: validate
  script:
    - npm ci
    - npm run lint
    - npm run format:check
  rules:
    - if: '$CI_PIPELINE_SOURCE == "merge_request_event"'
    - if: '$CI_COMMIT_BRANCH == $CI_DEFAULT_BRANCH'

lint:docker:
  stage: validate
  image: hadolint/hadolint:latest-debian
  script:
    - hadolint Dockerfile
  allow_failure: true

# ═══════════════════════════════════════════════════════════
# STAGE 2: BUILD
# ═══════════════════════════════════════════════════════════

build:app:
  stage: build
  script:
    - npm ci
    - npm run build
  artifacts:
    paths:
      - dist/
    expire_in: 1 week
  rules:
    - if: '$CI_PIPELINE_SOURCE == "merge_request_event"'
    - if: '$CI_COMMIT_BRANCH == $CI_DEFAULT_BRANCH'

# ═══════════════════════════════════════════════════════════
# STAGE 3: TEST
# ═══════════════════════════════════════════════════════════

test:unit:
  stage: test
  coverage: '/All files[^|]*\|[^|]*\s+([\d\.]+)/'
  script:
    - npm ci
    - npm run test:unit -- --coverage
  artifacts:
    reports:
      coverage_report:
        coverage_format: cobertura
        path: coverage/cobertura-coverage.xml
      junit: junit.xml
    paths:
      - coverage/
    expire_in: 1 week

test:integration:
  stage: test
  services:
    - postgres:15
    - redis:7
  variables:
    POSTGRES_DB: testdb
    POSTGRES_USER: testuser
    POSTGRES_PASSWORD: testpass
    DATABASE_URL: "postgresql://testuser:testpass@postgres:5432/testdb"
    REDIS_URL: "redis://redis:6379"
  script:
    - npm ci
    - npm run test:integration
  artifacts:
    reports:
      junit: junit-integration.xml

test:e2e:
  stage: test
  image: cypress/browsers:latest
  script:
    - npm ci
    - npm run build
    - npm run start:test &
    - npx wait-on http://localhost:3000
    - npm run test:e2e
  artifacts:
    when: always
    paths:
      - cypress/screenshots/
      - cypress/videos/
    expire_in: 1 week

# ═══════════════════════════════════════════════════════════
# STAGE 4: SECURITY SCANNING
# ═══════════════════════════════════════════════════════════

# SAST (Static Application Security Testing)
sast:
  stage: security
include:
  - template: Security/SAST.gitlab-ci.yml

# Dependency Scanning
dependency_scanning:
  stage: security
include:
  - template: Security/Dependency-Scanning.gitlab-ci.yml

# Secret Detection
secret_detection:
  stage: security
include:
  - template: Security/Secret-Detection.gitlab-ci.yml

# Container Scanning (after Docker build)
container_scanning:
  stage: security
  dependencies:
    - build:docker
include:
  - template: Security/Container-Scanning.gitlab-ci.yml

# License Scanning
license_scanning:
  stage: security
include:
  - template: Security/License-Scanning.gitlab-ci.yml

# ═══════════════════════════════════════════════════════════
# STAGE 5: PACKAGE
# ═══════════════════════════════════════════════════════════

build:docker:
  stage: package
  image: docker:24
  services:
    - docker:24-dind
  before_script:
    - echo $CI_REGISTRY_PASSWORD | docker login -u $CI_REGISTRY_USER $CI_REGISTRY --password-stdin
  script:
    # Build for multiple platforms
    - docker buildx create --use
    - |
      docker buildx build \
        --platform linux/amd64,linux/arm64 \
        --tag $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA \
        --tag $CI_REGISTRY_IMAGE:$CI_COMMIT_REF_SLUG \
        --tag $CI_REGISTRY_IMAGE:latest \
        --push \
        --cache-from type=registry,ref=$CI_REGISTRY_IMAGE:buildcache \
        --cache-to type=registry,ref=$CI_REGISTRY_IMAGE:buildcache,mode=max \
        .
  rules:
    - if: '$CI_COMMIT_BRANCH == $CI_DEFAULT_BRANCH'

# ═══════════════════════════════════════════════════════════
# STAGE 6: DEPLOY
# ═══════════════════════════════════════════════════════════

# Review Apps (for merge requests)
deploy:review:
  stage: deploy
  image: bitnami/kubectl:latest
  script:
    - kubectl config use-context $KUBE_CONTEXT
    - |
      kubectl create namespace review-$CI_MERGE_REQUEST_IID || true
      kubectl apply -f k8s/ -n review-$CI_MERGE_REQUEST_IID
      kubectl set image deployment/myapp myapp=$CI_REGISTRY_IMAGE:$CI_COMMIT_SHA -n review-$CI_MERGE_REQUEST_IID
  environment:
    name: review/$CI_COMMIT_REF_SLUG
    url: https://review-$CI_MERGE_REQUEST_IID.myapp.com
    on_stop: stop:review
    auto_stop_in: 1 day
  rules:
    - if: '$CI_PIPELINE_SOURCE == "merge_request_event"'

stop:review:
  stage: deploy
  image: bitnami/kubectl:latest
  script:
    - kubectl config use-context $KUBE_CONTEXT
    - kubectl delete namespace review-$CI_MERGE_REQUEST_IID
  environment:
    name: review/$CI_COMMIT_REF_SLUG
    action: stop
  when: manual
  rules:
    - if: '$CI_PIPELINE_SOURCE == "merge_request_event"'

# Deploy to Staging
deploy:staging:
  stage: deploy
  image: bitnami/kubectl:latest
  script:
    - kubectl config use-context $KUBE_CONTEXT
    - kubectl apply -f k8s/ -n staging
    - kubectl set image deployment/myapp myapp=$CI_REGISTRY_IMAGE:$CI_COMMIT_SHA -n staging
    - kubectl rollout status deployment/myapp -n staging
  environment:
    name: staging
    url: https://staging.myapp.com
  rules:
    - if: '$CI_COMMIT_BRANCH == $CI_DEFAULT_BRANCH'

# Deploy to Production (manual)
deploy:production:
  stage: deploy
  image: bitnami/kubectl:latest
  script:
    - kubectl config use-context $KUBE_CONTEXT
    - kubectl apply -f k8s/ -n production
    - kubectl set image deployment/myapp myapp=$CI_REGISTRY_IMAGE:$CI_COMMIT_SHA -n production
    - kubectl rollout status deployment/myapp -n production

    # Run smoke tests
    - curl -f https://myapp.com/health || exit 1
  environment:
    name: production
    url: https://myapp.com
  when: manual
  rules:
    - if: '$CI_COMMIT_BRANCH == $CI_DEFAULT_BRANCH'
```

---

### GitLab Auto DevOps

```yaml
# ═══════════════════════════════════════════════════════════
# AUTO DEVOPS - ZERO CONFIG CI/CD
# Just enable Auto DevOps in project settings!
# ═══════════════════════════════════════════════════════════

# Auto DevOps automatically:
# ✅ Detects your language/framework
# ✅ Builds Docker images
# ✅ Runs tests
# ✅ Security scans
# ✅ Deploys to Kubernetes
# ✅ Creates review apps
# ✅ Monitors performance

# Customize if needed:
include:
  - template: Auto-DevOps.gitlab-ci.yml

variables:
  AUTO_DEVOPS_DOMAIN: myapp.com
  POSTGRES_ENABLED: "true"
  REVIEW_DISABLED: "false"
```

---

<div align="center">

## 🔵 Azure DevOps

_Enterprise-grade CI/CD from Microsoft_ 🏢

</div>

### Why Azure DevOps?

```
✅ PROS:
• Comprehensive DevOps suite
• Excellent for Microsoft stack
• Azure integration
• Free for small teams (5 users)
• Powerful work tracking (Azure Boards)
• Flexible hosting (cloud/on-prem)
• Great enterprise features
• Visual pipeline editor
• Release gates & approvals

❌ CONS:
• Complex UI
• Steeper learning curve
• Less community support than GitHub
• YAML can be verbose

🎯 USE WHEN:
✓ Using Azure cloud
✓ Microsoft/.NET stack
✓ Enterprise environment
✓ Need work tracking
✓ Want hybrid (cloud + on-prem)
```

---

### Azure Pipelines - Complete Setup

```yaml
# ═══════════════════════════════════════════════════════════
# AZURE DEVOPS - PRODUCTION PIPELINE
# azure-pipelines.yml
# ═══════════════════════════════════════════════════════════

# Trigger configuration
trigger:
  branches:
    include:
      - main
      - develop
  paths:
    exclude:
      - README.md
      - docs/*

pr:
  branches:
    include:
      - main

# Variables
variables:
  - group: production-secrets # Variable group
  - name: buildConfiguration
    value: "Release"
  - name: vmImageName
    value: "ubuntu-latest"
  - name: dockerRegistryServiceConnection
    value: "myregistry"
  - name: imageRepository
    value: "myapp"
  - name: containerRegistry
    value: "myregistry.azurecr.io"
  - name: dockerfilePath
    value: "$(Build.SourcesDirectory)/Dockerfile"
  - name: tag
    value: "$(Build.BuildId)"

# Stages
stages:
  # ═══════════════════════════════════════════════════════════
  # STAGE 1: BUILD & TEST
  # ═══════════════════════════════════════════════════════════
  - stage: Build
    displayName: "Build and Test"
    jobs:
      - job: BuildJob
        displayName: "Build Application"
        pool:
          vmImage: $(vmImageName)

        steps:
          - task: NodeTool@0
            inputs:
              versionSpec: "20.x"
            displayName: "Install Node.js"

          - script: |
              npm ci
              npm run build
            displayName: "npm install and build"

          - task: PublishBuildArtifacts@1
            inputs:
              PathtoPublish: "dist"
              ArtifactName: "drop"
            displayName: "Publish Artifact"

      - job: TestJob
        displayName: "Run Tests"
        pool:
          vmImage: $(vmImageName)

        steps:
          - task: NodeTool@0
            inputs:
              versionSpec: "20.x"

          - script: |
              npm ci
              npm run test:coverage
            displayName: "Run tests with coverage"

          - task: PublishCodeCoverageResults@1
            inputs:
              codeCoverageTool: "Cobertura"
              summaryFileLocation: "$(System.DefaultWorkingDirectory)/coverage/cobertura-coverage.xml"
            displayName: "Publish code coverage"

          - task: PublishTestResults@2
            inputs:
              testResultsFormat: "JUnit"
              testResultsFiles: "**/junit.xml"
            displayName: "Publish test results"

  # ═══════════════════════════════════════════════════════════
  # STAGE 2: SECURITY SCANNING
  # ═══════════════════════════════════════════════════════════
  - stage: Security
    displayName: "Security Scanning"
    dependsOn: Build
    jobs:
      - job: ScanJob
        displayName: "Security Scan"
        pool:
          vmImage: $(vmImageName)

        steps:
          - task: WhiteSource@21
            inputs:
              cwd: "$(System.DefaultWorkingDirectory)"
            displayName: "WhiteSource Scan"

          - task: SonarCloudPrepare@1
            inputs:
              SonarCloud: "SonarCloud"
              organization: "myorg"
              scannerMode: "CLI"
            displayName: "Prepare SonarCloud"

          - task: SonarCloudAnalyze@1
            displayName: "Run SonarCloud Analysis"

          - task: SonarCloudPublish@1
            displayName: "Publish SonarCloud Results"

  # ═══════════════════════════════════════════════════════════
  # STAGE 3: BUILD DOCKER IMAGE
  # ═══════════════════════════════════════════════════════════
  - stage: Docker
    displayName: "Build Docker Image"
    dependsOn: Security
    condition: and(succeeded(), eq(variables['Build.SourceBranch'], 'refs/heads/main'))
    jobs:
      - job: DockerJob
        displayName: "Build and Push Docker Image"
        pool:
          vmImage: $(vmImageName)

        steps:
          - task: Docker@2
            displayName: "Build and push image"
            inputs:
              command: buildAndPush
              repository: $(imageRepository)
              dockerfile: $(dockerfilePath)
              containerRegistry: $(dockerRegistryServiceConnection)
              tags: |
                $(tag)
                latest

  # ═══════════════════════════════════════════════════════════
  # STAGE 4: DEPLOY TO STAGING
  # ═══════════════════════════════════════════════════════════
  - stage: DeployStaging
    displayName: "Deploy to Staging"
    dependsOn: Docker
    jobs:
      - deployment: DeployStagingJob
        displayName: "Deploy to Staging Environment"
        pool:
          vmImage: $(vmImageName)
        environment: "staging"
        strategy:
          runOnce:
            deploy:
              steps:
                - task: KubernetesManifest@0
                  displayName: "Deploy to Kubernetes"
                  inputs:
                    action: "deploy"
                    kubernetesServiceConnection: "k8s-staging"
                    namespace: "staging"
                    manifests: |
                      $(Pipeline.Workspace)/manifests/deployment.yml
                      $(Pipeline.Workspace)/manifests/service.yml
                    containers: |
                      $(containerRegistry)/$(imageRepository):$(tag)

                - script: |
                    curl -f https://staging.myapp.com/health || exit 1
                  displayName: "Smoke Test"

  # ═══════════════════════════════════════════════════════════
  # STAGE 5: DEPLOY TO PRODUCTION
  # ═══════════════════════════════════════════════════════════
  - stage: DeployProduction
    displayName: "Deploy to Production"
    dependsOn: DeployStaging
    jobs:
      - deployment: DeployProductionJob
        displayName: "Deploy to Production Environment"
        pool:
          vmImage: $(vmImageName)
        environment: "production"
        strategy:
          runOnce:
            deploy:
              steps:
                - task: KubernetesManifest@0
                  displayName: "Deploy to Kubernetes"
                  inputs:
                    action: "deploy"
                    kubernetesServiceConnection: "k8s-production"
                    namespace: "production"
                    manifests: |
                      $(Pipeline.Workspace)/manifests/deployment.yml
                      $(Pipeline.Workspace)/manifests/service.yml
                    containers: |
                      $(containerRegistry)/$(imageRepository):$(tag)

                - task: AzureCLI@2
                  displayName: "Health Check"
                  inputs:
                    azureSubscription: "Production"
                    scriptType: "bash"
                    scriptLocation: "inlineScript"
                    inlineScript: |
                      az webapp show --name myapp --resource-group production
                      curl -f https://myapp.com/health || exit 1
```

---

<div align="center">

## ⚫ CircleCI

_Speed and performance focused_ ⚡

</div>

### Why CircleCI?

```
✅ PROS:
• Extremely fast builds
• Docker-first approach
• Excellent caching
• Orbs (reusable configs)
• Great GitHub/Bitbucket integration
• Parallelism & test splitting
• SSH into failed builds
• Cloud + self-hosted

❌ CONS:
• Can get expensive
• Complex pricing
• Learning curve for advanced features

🎯 USE WHEN:
✓ Speed is critical
✓ Docker-based workflows
✓ Need test parallelism
✓ Want cloud-hosted solution
✓ Have budget for performance
```

---

### CircleCI - Complete Configuration

```yaml
# ═══════════════════════════════════════════════════════════
# CIRCLECI - HIGH-PERFORMANCE PIPELINE
# .circleci/config.yml
# ═══════════════════════════════════════════════════════════

version: 2.1

# Orbs (reusable packages)
orbs:
  node: circleci/node@5.1
  docker: circleci/docker@2.2
  kubernetes: circleci/kubernetes@1.3
  slack: circleci/slack@4.12

# Executors (execution environments)
executors:
  node-executor:
    docker:
      - image: cimg/node:20.0
    resource_class: large
    working_directory: ~/project

  docker-executor:
    docker:
      - image: cimg/base:stable
    resource_class: xlarge

# Commands (reusable command sequences)
commands:
  restore-deps:
    description: "Restore dependencies from cache"
    steps:
      - restore_cache:
          keys:
            - v1-deps-{{ checksum "package-lock.json" }}
            - v1-deps-

  save-deps:
    description: "Save dependencies to cache"
    steps:
      - save_cache:
          key: v1-deps-{{ checksum "package-lock.json" }}
          paths:
            - node_modules
            - ~/.npm
            - ~/.cache

# Jobs
jobs:
  # ═══════════════════════════════════════════════════════════
  # JOB 1: LINT & FORMAT
  # ═══════════════════════════════════════════════════════════
  lint:
    executor: node-executor
    steps:
      - checkout
      - restore-deps
      - run:
          name: Install dependencies
          command: npm ci
      - save-deps
      - run:
          name: Run linters
          command: |
            npm run lint
            npm run format:check
            npm run type-check
      - slack/notify:
          event: fail
          template: basic_fail_1

  # ═══════════════════════════════════════════════════════════
  # JOB 2: BUILD
  # ═══════════════════════════════════════════════════════════
  build:
    executor: node-executor
    steps:
      - checkout
      - restore-deps
      - run:
          name: Install dependencies
          command: npm ci
      - run:
          name: Build application
          command: npm run build
      - persist_to_workspace:
          root: ~/project
          paths:
            - dist
            - node_modules
      - store_artifacts:
          path: dist
          destination: build-output

  # ═══════════════════════════════════════════════════════════
  # JOB 3: TEST (WITH PARALLELISM)
  # ═══════════════════════════════════════════════════════════
  test:
    executor: node-executor
    parallelism: 4 # Run tests in parallel across 4 containers
    steps:
      - checkout
      - restore-deps
      - attach_workspace:
          at: ~/project
      - run:
          name: Run tests
          command: |
            # Split tests by timing data
            TESTFILES=$(circleci tests glob "**/*.spec.ts" | \
              circleci tests split --split-by=timings)
            npm run test -- $TESTFILES --coverage
      - store_test_results:
          path: test-results
      - store_artifacts:
          path: coverage
      - run:
          name: Upload coverage to Codecov
          command: bash <(curl -s https://codecov.io/bash)

  # ═══════════════════════════════════════════════════════════
  # JOB 4: E2E TESTS
  # ═══════════════════════════════════════════════════════════
  e2e:
    docker:
      - image: cypress/browsers:latest
    resource_class: large
    steps:
      - checkout
      - restore-deps
      - attach_workspace:
          at: ~/project
      - run:
          name: Start application
          command: npm run preview
          background: true
      - run:
          name: Wait for application
          command: npx wait-on http://localhost:3000
      - run:
          name: Run E2E tests
          command: npm run test:e2e
      - store_test_results:
          path: cypress/results
      - store_artifacts:
          path: cypress/screenshots
      - store_artifacts:
          path: cypress/videos

  # ═══════════════════════════════════════════════════════════
  # JOB 5: SECURITY SCAN
  # ═══════════════════════════════════════════════════════════
  security:
    executor: node-executor
    steps:
      - checkout
      - restore-deps
      - run:
          name: Run npm audit
          command: npm audit --production
      - run:
          name: Run Snyk test
          command: |
            npm install -g snyk
            snyk test --severity-threshold=high
      - run:
          name: Scan for secrets
          command: |
            docker run --rm -v $(pwd):/src trufflesecurity/trufflehog:latest \
              filesystem /src --json

  # ═══════════════════════════════════════════════════════════
  # JOB 6: BUILD DOCKER IMAGE
  # ═══════════════════════════════════════════════════════════
  docker-build:
    executor: docker-executor
    steps:
      - checkout
      - setup_remote_docker:
          version: 20.10.24
          docker_layer_caching: true # DLC for faster builds
      - attach_workspace:
          at: ~/project
      - run:
          name: Build Docker image
          command: |
            docker build \
              --tag myapp:${CIRCLE_SHA1} \
              --tag myapp:latest \
              --cache-from myapp:latest \
              .
      - run:
          name: Scan image with Trivy
          command: |
            docker run --rm -v /var/run/docker.sock:/var/run/docker.sock \
              aquasec/trivy image myapp:${CIRCLE_SHA1}
      - run:
          name: Push to registry
          command: |
            echo "$DOCKER_PASSWORD" | docker login -u "$DOCKER_USERNAME" --password-stdin
            docker push myapp:${CIRCLE_SHA1}
            docker push myapp:latest

  # ═══════════════════════════════════════════════════════════
  # JOB 7: DEPLOY TO STAGING
  # ═══════════════════════════════════════════════════════════
  deploy-staging:
    executor: node-executor
    steps:
      - checkout
      - kubernetes/install-kubectl
      - run:
          name: Deploy to Kubernetes
          command: |
            echo "$KUBE_CONFIG_STAGING" | base64 -d > kubeconfig
            export KUBECONFIG=kubeconfig

            kubectl set image deployment/myapp \
              myapp=myapp:${CIRCLE_SHA1} \
              -n staging

            kubectl rollout status deployment/myapp -n staging
      - run:
          name: Smoke test
          command: curl -f https://staging.myapp.com/health
      - slack/notify:
          event: pass
          template: success_tagged_deploy_1

  # ═══════════════════════════════════════════════════════════
  # JOB 8: DEPLOY TO PRODUCTION
  # ═══════════════════════════════════════════════════════════
  deploy-production:
    executor: node-executor
    steps:
      - checkout
      - kubernetes/install-kubectl
      - run:
          name: Deploy to Kubernetes
          command: |
            echo "$KUBE_CONFIG_PRODUCTION" | base64 -d > kubeconfig
            export KUBECONFIG=kubeconfig

            kubectl set image deployment/myapp \
              myapp=myapp:${CIRCLE_SHA1} \
              -n production

            kubectl rollout status deployment/myapp -n production
      - run:
          name: Smoke test
          command: curl -f https://myapp.com/health
      - slack/notify:
          event: pass
          custom: |
            {
              "text": "✅ Production deployment successful!",
              "blocks": [
                {
                  "type": "section",
                  "text": {
                    "type": "mrkdwn",
                    "text": "*Deployment to Production* :rocket:\n*Commit*: ${CIRCLE_SHA1}\n*Branch*: ${CIRCLE_BRANCH}\n*Author*: ${CIRCLE_USERNAME}"
                  }
                }
              ]
            }

# Workflows
workflows:
  version: 2
  build-test-deploy:
    jobs:
      # Parallel: Lint and Build
      - lint:
          context: slack-secrets

      - build:
          context: npm-secrets

      # Wait for lint + build
      - test:
          requires:
            - lint
            - build
          context: test-secrets

      - e2e:
          requires:
            - build
          context: test-secrets

      - security:
          requires:
            - build
          context: security-secrets

      # Wait for all tests
      - docker-build:
          requires:
            - test
            - e2e
            - security
          filters:
            branches:
              only: main
          context: docker-secrets

      # Deploy staging
      - deploy-staging:
          requires:
            - docker-build
          filters:
            branches:
              only: main
          context: k8s-staging

      # Manual approval for production
      - hold-production:
          type: approval
          requires:
            - deploy-staging
          filters:
            branches:
              only: main

      - deploy-production:
          requires:
            - hold-production
          filters:
            branches:
              only: main
          context: k8s-production
```

---

<div align="center">

## 🟢 Jenkins

_The flexible powerhouse_ 🔧

</div>

### Why Jenkins?

```
✅ PROS:
• Completely free & open-source
• 1,800+ plugins
• Ultimate flexibility
• Self-hosted (full control)
• Massive community
• Pipeline as Code (Jenkinsfile)
• Distributed builds
• Works with everything

❌ CONS:
• Steep learning curve
• Requires maintenance
• UI feels dated
• Plugin compatibility issues
• Setup complexity

🎯 USE WHEN:
✓ Need maximum flexibility
✓ Complex custom workflows
✓ Self-hosted requirement
✓ Legacy system integration
✓ Have DevOps expertise
```

---

### Jenkins - Declarative Pipeline

```groovy
// ═══════════════════════════════════════════════════════════
// JENKINS - PRODUCTION DECLARATIVE PIPELINE
// Jenkinsfile
// ═══════════════════════════════════════════════════════════

pipeline {
    agent none

    options {
        buildDiscarder(logRotator(numToKeepStr: '10'))
        timestamps()
        timeout(time: 1, unit: 'HOURS')
        disableConcurrentBuilds()
    }

    environment {
        DOCKER_REGISTRY = 'myregistry.com'
        IMAGE_NAME = 'myapp'
        K8S_NAMESPACE = 'production'
        SLACK_CHANNEL = '#deployments'
    }

    stages {
        // ═══════════════════════════════════════════════════════════
        // STAGE 1: CHECKOUT
        // ═══════════════════════════════════════════════════════════
        stage('Checkout') {
            agent {
                label 'linux'
            }
            steps {
                checkout scm
                script {
                    env.GIT_COMMIT_SHORT = sh(
                        script: "git rev-parse --short HEAD",
                        returnStdout: true
                    ).trim()
                    env.IMAGE_TAG = "${env.GIT_COMMIT_SHORT}"
                }
            }
        }

        // ═══════════════════════════════════════════════════════════
        // STAGE 2: LINT & FORMAT
        // ═══════════════════════════════════════════════════════════
        stage('Lint') {
            agent {
                docker {
                    image 'node:20'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    npm ci
                    npm run lint
                    npm run format:check
                '''
            }
        }

        // ═══════════════════════════════════════════════════════════
        // STAGE 3: BUILD
        // ═══════════════════════════════════════════════════════════
        stage('Build') {
            agent {
                docker {
                    image 'node:20'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    npm ci
                    npm run build
                '''
                stash includes: 'dist/**', name: 'build-artifacts'
            }
        }

        // ═══════════════════════════════════════════════════════════
        // STAGE 4: TEST (PARALLEL)
        // ═══════════════════════════════════════════════════════════
        stage('Test') {
            parallel {
                stage('Unit Tests') {
                    agent {
                        docker {
                            image 'node:20'
                            reuseNode true
                        }
                    }
                    steps {
                        unstash 'build-artifacts'
                        sh '''
                            npm ci
                            npm run test:unit -- --coverage
                        '''
                        publishHTML([
                            reportDir: 'coverage',
                            reportFiles: 'index.html',
                            reportName: 'Coverage Report'
                        ])
                        junit 'junit.xml'
                    }
                }

                stage('Integration Tests') {
                    agent {
                        docker {
                            image 'node:20'
                            reuseNode true
                        }
                    }
                    steps {
                        unstash 'build-artifacts'
                        sh '''
                            npm ci
                            npm run test:integration
                        '''
                        junit 'junit-integration.xml'
                    }
                }

                stage('E2E Tests') {
                    agent {
                        docker {
                            image 'mcr.microsoft.com/playwright:latest'
                            reuseNode true
                        }
                    }
                    steps {
                        unstash 'build-artifacts'
                        sh '''
                            npm ci
                            npm run build
                            npm run preview &
                            npx wait-on http://localhost:3000
                            npm run test:e2e
                        '''
                        publishHTML([
                            reportDir: 'playwright-report',
                            reportFiles: 'index.html',
                            reportName: 'Playwright Report'
                        ])
                    }
                }
            }
        }

        // ═══════════════════════════════════════════════════════════
        // STAGE 5: SECURITY SCANNING
        // ═══════════════════════════════════════════════════════════
        stage('Security') {
            parallel {
                stage('Dependency Scan') {
                    agent {
                        label 'linux'
                    }
                    steps {
                        sh '''
                            npm audit --production
                        '''
                    }
                }

                stage('SAST Scan') {
                    agent {
                        label 'linux'
                    }
                    steps {
                        sh '''
                            docker run --rm -v $(pwd):/src \
                              returntocorp/semgrep semgrep --config=auto /src
                        '''
                    }
                }

                stage('Secret Scan') {
                    agent {
                        label 'linux'
                    }
                    steps {
                        sh '''
                            docker run --rm -v $(pwd):/src \
                              trufflesecurity/trufflehog:latest \
                              filesystem /src --json
                        '''
                    }
                }
            }
        }

        // ═══════════════════════════════════════════════════════════
        // STAGE 6: BUILD DOCKER IMAGE
        // ═══════════════════════════════════════════════════════════
        stage('Docker Build') {
            when {
                branch 'main'
            }
            agent {
                label 'linux'
            }
            steps {
                script {
                    docker.withRegistry("https://${DOCKER_REGISTRY}", 'docker-credentials') {
                        def customImage = docker.build(
                            "${IMAGE_NAME}:${IMAGE_TAG}",
                            "--cache-from ${IMAGE_NAME}:latest ."
                        )
                        customImage.push()
                        customImage.push('latest')
                    }
                }
            }
        }

        // ═══════════════════════════════════════════════════════════
        // STAGE 7: CONTAINER SCAN
        // ═══════════════════════════════════════════════════════════
        stage('Container Scan') {
            when {
                branch 'main'
            }
            agent {
                label 'linux'
            }
            steps {
                sh """
                    docker run --rm \
                      -v /var/run/docker.sock:/var/run/docker.sock \
                      aquasec/trivy image \
                      ${DOCKER_REGISTRY}/${IMAGE_NAME}:${IMAGE_TAG}
                """
            }
        }

        // ═══════════════════════════════════════════════════════════
        // STAGE 8: DEPLOY TO STAGING
        // ═══════════════════════════════════════════════════════════
        stage('Deploy Staging') {
            when {
                branch 'main'
            }
            agent {
                label 'linux'
            }
            steps {
                withKubeConfig([credentialsId: 'k8s-staging']) {
                    sh """
                        kubectl set image deployment/myapp \
                          myapp=${DOCKER_REGISTRY}/${IMAGE_NAME}:${IMAGE_TAG} \
                          -n staging

                        kubectl rollout status deployment/myapp -n staging
                    """
                }

                // Smoke test
                sh 'curl -f https://staging.myapp.com/health'
            }
        }

        // ═══════════════════════════════════════════════════════════
        // STAGE 9: MANUAL APPROVAL
        // ═══════════════════════════════════════════════════════════
        stage('Approve Production') {
            when {
                branch 'main'
            }
            steps {
                timeout(time: 1, unit: 'HOURS') {
                    input message: 'Deploy to Production?',
                          ok: 'Deploy',
                          submitter: 'deploy-team'
                }
            }
        }

        // ═══════════════════════════════════════════════════════════
        // STAGE 10: DEPLOY TO PRODUCTION
        // ═══════════════════════════════════════════════════════════
        stage('Deploy Production') {
            when {
                branch 'main'
            }
            agent {
                label 'linux'
            }
            steps {
                withKubeConfig([credentialsId: 'k8s-production']) {
                    sh """
                        kubectl set image deployment/myapp \
                          myapp=${DOCKER_REGISTRY}/${IMAGE_NAME}:${IMAGE_TAG} \
                          -n production

                        kubectl rollout status deployment/myapp -n production
                    """
                }

                // Smoke test
                sh 'curl -f https://myapp.com/health'
            }
        }
    }

    post {
        success {
            slackSend(
                channel: env.SLACK_CHANNEL,
                color: 'good',
                message: "✅ Deployment successful: ${env.JOB_NAME} #${env.BUILD_NUMBER}"
            )
        }
        failure {
            slackSend(
                channel: env.SLACK_CHANNEL,
                color: 'danger',
                message: "❌ Deployment failed: ${env.JOB_NAME} #${env.BUILD_NUMBER}"
            )
        }
        always {
            cleanWs()
        }
    }
}
```

---

<div align="center">

## 🚀 Modern Cloud-Native Tools

_The new generation of CI/CD_ ☁️

</div>

### Argo CD - GitOps for Kubernetes

```yaml
# ═══════════════════════════════════════════════════════════
# ARGO CD - GITOPS DEPLOYMENT
# application.yaml
# ═══════════════════════════════════════════════════════════

apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: myapp
  namespace: argocd
spec:
  project: default

  # Source repository
  source:
    repoURL: https://github.com/myorg/myapp
    targetRevision: main
    path: k8s

    # Helm values (if using Helm)
    helm:
      values: |
        image:
          repository: myregistry.com/myapp
          tag: v1.0.0
        replicas: 3

  # Destination cluster
  destination:
    server: https://kubernetes.default.svc
    namespace: production

  # Sync policy
  syncPolicy:
    automated:
      prune: true # Delete resources not in Git
      selfHeal: true # Auto-sync if drift detected
      allowEmpty: false

    syncOptions:
      - CreateNamespace=true
      - PrunePropagationPolicy=foreground
      - Replace=true

    retry:
      limit: 5
      backoff:
        duration: 5s
        factor: 2
        maxDuration: 3m

  # Health assessment
  ignoreDifferences:
    - group: apps
      kind: Deployment
      jsonPointers:
        - /spec/replicas
```

**Why Argo CD?**

```
✅ PROS:
• True GitOps (Git as source of truth)
• Kubernetes-native
• Real-time sync
• Automatic drift detection
• Beautiful UI
• Multi-cluster support
• RBAC built-in
• Rollback with Git revert

❌ CONS:
• Kubernetes-only
• Requires Git workflow
• Learning curve for GitOps

🎯 USE WHEN:
✓ Deploying to Kubernetes
✓ Want GitOps workflow
✓ Need multi-cluster management
✓ Security/audit requirements
```

---

### Tekton - Kubernetes-Native CI/CD

```yaml
# ═══════════════════════════════════════════════════════════
# TEKTON - CLOUD-NATIVE PIPELINE
# ═══════════════════════════════════════════════════════════

# Task: Build Docker Image
---
apiVersion: tekton.dev/v1beta1
kind: Task
metadata:
  name: build-docker-image
spec:
  params:
    - name: IMAGE
      description: Reference of the image to build
    - name: DOCKERFILE
      default: ./Dockerfile

  workspaces:
    - name: source

  steps:
    - name: build-and-push
      image: gcr.io/kaniko-project/executor:latest
      args:
        - --dockerfile=$(params.DOCKERFILE)
        - --context=$(workspaces.source.path)
        - --destination=$(params.IMAGE)
        - --cache=true

# Pipeline: Complete CI/CD
---
apiVersion: tekton.dev/v1beta1
kind: Pipeline
metadata:
  name: build-and-deploy
spec:
  params:
    - name: repo-url
    - name: image-reference

  workspaces:
    - name: shared-workspace

  tasks:
    # Task 1: Clone repository
    - name: fetch-repository
      taskRef:
        name: git-clone
      workspaces:
        - name: output
          workspace: shared-workspace
      params:
        - name: url
          value: $(params.repo-url)

    # Task 2: Run tests
    - name: run-tests
      taskRef:
        name: npm-test
      workspaces:
        - name: source
          workspace: shared-workspace
      runAfter:
        - fetch-repository

    # Task 3: Build image
    - name: build-image
      taskRef:
        name: build-docker-image
      workspaces:
        - name: source
          workspace: shared-workspace
      params:
        - name: IMAGE
          value: $(params.image-reference)
      runAfter:
        - run-tests

    # Task 4: Deploy
    - name: deploy
      taskRef:
        name: kubectl-deploy
      params:
        - name: image
          value: $(params.image-reference)
      runAfter:
        - build-image

# PipelineRun: Execute the pipeline
---
apiVersion: tekton.dev/v1beta1
kind: PipelineRun
metadata:
  name: build-and-deploy-run
spec:
  pipelineRef:
    name: build-and-deploy
  params:
    - name: repo-url
      value: https://github.com/myorg/myapp
    - name: image-reference
      value: myregistry.com/myapp:latest
  workspaces:
    - name: shared-workspace
      volumeClaimTemplate:
        spec:
          accessModes:
            - ReadWriteOnce
          resources:
            requests:
              storage: 1Gi
```

---

### Harness - AI-Powered CD

**Why Harness?**

```
✅ PROS:
• AI-driven deployments
• Automatic rollback on failure
• ML-based anomaly detection
• Visual pipeline builder
• Multi-cloud support
• Advanced deployment strategies
• Cost visibility
• Great UX

❌ CONS:
• Expensive
• Overkill for small teams
• Requires some learning

🎯 USE WHEN:
✓ Enterprise scale
✓ Want AI automation
✓ Need deployment verification
✓ Multi-cloud environments
✓ Have budget
```

---

<div align="center">

## 🎯 Specialized Tools

_Purpose-built for specific needs_ 🔧

</div>

### Tool Overview

| Tool               | Specialty             | Best For                  | Price      |
| :----------------- | :-------------------- | :------------------------ | :--------- |
| **Octopus Deploy** | Deployment automation | Complex release processes | Commercial |
| **Spinnaker**      | Multi-cloud CD        | Netflix-scale deployments | Free (OSS) |
| **Buddy**          | Developer-friendly    | Small teams, quick setup  | Freemium   |
| **Codefresh**      | Kubernetes + Docker   | Cloud-native apps         | Commercial |
| **Buildkite**      | Hybrid CI/CD          | Self-hosted agents        | Commercial |
| **Semaphore**      | Speed                 | Fast pipelines            | Freemium   |
| **TravisCI**       | Open source           | OSS projects              | Freemium   |
| **Drone**          | Container-native      | Docker workflows          | Free (OSS) |
| **GoCD**           | Value stream mapping  | Complex pipelines         | Free (OSS) |

---

<div align="center">

## 💰 Cost Comparison

_What will it actually cost you?_ 💵

</div>

### Pricing Breakdown (2025)

<div align="center">

| Tool                    | Free Tier            | Starter                 | Pro            | Enterprise | Notes                 |
| :---------------------- | :------------------- | :---------------------- | :------------- | :--------- | :-------------------- |
| **GitHub Actions**      | 2,000 min/month      | Pay per minute          | Pay per minute | Custom     | Free for public repos |
| **GitLab CI/CD**        | 400 min/month        | $29/user/month          | $99/user/month | Custom     | Self-hosted = free    |
| **CircleCI**            | 6,000 min/month      | $15/month               | $50/month      | Custom     | Credits system        |
| **Azure DevOps**        | 5 users free         | $6/user/month           | $6/user/month  | Custom     | Unlimited repos       |
| **Jenkins**             | Free (OSS)           | Free                    | Free           | Free       | Self-hosted costs     |
| **TeamCity**            | 3 agents, 100 builds | $45/month               | $299/month     | Custom     | Free for OSS          |
| **Bitbucket Pipelines** | 50 min/month         | Included with Bitbucket | Included       | Custom     | Atlassian bundle      |
| **Harness**             | None                 | Custom                  | Custom         | Custom     | Enterprise pricing    |
| **Argo CD**             | Free (OSS)           | Free                    | Free           | Free       | Kubernetes required   |
| **Tekton**              | Free (OSS)           | Free                    | Free           | Free       | Kubernetes required   |

</div>

---

### Cost Calculator Example

```
🧮 MONTHLY COST ESTIMATE:

Team Size: 10 developers
Commits/day: 50
Average build time: 10 minutes
---

GitHub Actions:
• 50 commits × 30 days × 10 min = 15,000 minutes
• Free tier: 2,000 minutes
• Overage: 13,000 minutes × $0.008 = $104/month
• Total: ~$104/month

GitLab CI/CD:
• Self-hosted: $0 (infrastructure costs only)
• SaaS Premium: 10 users × $29 = $290/month
• Total: $0-$290/month

CircleCI:
• 15,000 minutes = 250,000 credits
• Free tier: 30,000 credits
• Overage: 220,000 credits × $0.0006 = $132/month
• Total: ~$132/month

Jenkins:
• Software: $0
• Infrastructure: ~$200/month (servers)
• Maintenance: Engineering time
• Total: $200+/month

💡 RECOMMENDATION:
• Small team (<5): GitHub Actions or GitLab free
• Medium team (5-20): GitLab self-hosted or CircleCI
• Large team (20+): Jenkins or GitLab self-hosted
• Enterprise: Azure DevOps or Harness
```

---

<div align="center">

## 🤖 AI-Powered CI/CD

_The future is intelligent automation_ 🧠

</div>

### AI Features in Modern CI/CD (2025)

```
🤖 AI/ML CAPABILITIES:

1. PREDICTIVE FAILURE DETECTION
   • Analyze historical data
   • Predict build failures before they happen
   • Suggest fixes proactively
   Tools: Harness, CircleCI (Insights)

2. INTELLIGENT TEST SELECTION
   • Run only affected tests
   • ML-based test impact analysis
   • Reduce test time by 70%
   Tools: GitHub Actions, Harness

3. AUTOMATED ROLLBACK
   • Detect anomalies post-deployment
   • Automatic rollback decisions
   • ML-driven canary analysis
   Tools: Harness, Spinnaker

4. RESOURCE OPTIMIZATION
   • Auto-scale build agents
   • Optimize pipeline parallelism
   • Cost predictions
   Tools: CircleCI, Azure DevOps

5. CODE REVIEW AUTOMATION
   • AI-powered code suggestions
   • Security vulnerability detection
   • Best practice enforcement
   Tools: GitHub Copilot, GitLab

6. FLAKY TEST DETECTION
   • Identify unreliable tests
   • Auto-retry strategies
   • Root cause analysis
   Tools: All major platforms
```

---

### GitHub Copilot for CI/CD

```yaml
# ═══════════════════════════════════════════════════════════
# GITHUB COPILOT - AI-ASSISTED PIPELINE
# Copilot can help write, fix, and optimize your pipelines!
# ═══════════════════════════════════════════════════════════

# Example: Ask Copilot to generate a workflow
# Prompt: "Create a GitHub Actions workflow for a Node.js app with Docker"

name: AI-Assisted Pipeline

on: [push]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      # Copilot suggestion: Add caching
      - name: Cache dependencies
        uses: actions/cache@v3
        with:
          path: ~/.npm
          key: ${{ runner.os }}-node-${{ hashFiles('**/package-lock.json') }}

      # Copilot can auto-complete complex commands
      - name: Build and test
        run: |
          npm ci
          npm run build
          npm test

      # Copilot knows Docker best practices
      - name: Build Docker image
        run: |
          docker build \
            --cache-from myapp:latest \
            --tag myapp:${{ github.sha }} \
            --build-arg BUILDKIT_INLINE_CACHE=1 \
            .
```

---

<div align="center">

## 🔐 Security in CI/CD

_DevSecOps best practices_ 🛡️

</div>

### Security Scanning Pipeline

```yaml
# ═══════════════════════════════════════════════════════════
# COMPLETE SECURITY PIPELINE
# Multiple security tools integrated
# ═══════════════════════════════════════════════════════════

name: Security Pipeline

on: [push, pull_request]

jobs:
  # ═══════════════════════════════════════════════════════════
  # 1. SECRET SCANNING
  # ═══════════════════════════════════════════════════════════
  secrets:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0 # Full history for secret scan

      - name: TruffleHog Secret Scan
        uses: trufflesecurity/trufflehog@main
        with:
          path: ./
          base: ${{ github.event.repository.default_branch }}
          head: HEAD

      - name: GitLeaks
        uses: gitleaks/gitleaks-action@v2

  # ═══════════════════════════════════════════════════════════
  # 2. DEPENDENCY SCANNING
  # ═══════════════════════════════════════════════════════════
  dependencies:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Run Snyk
        uses: snyk/actions/node@master
        env:
          SNYK_TOKEN: ${{ secrets.SNYK_TOKEN }}
        with:
          args: --severity-threshold=high

      - name: OWASP Dependency Check
        uses: dependency-check/Dependency-Check_Action@main
        with:
          project: "myapp"
          path: "."
          format: "HTML"

      - name: Upload Dependency Check Report
        uses: actions/upload-artifact@v3
        with:
          name: dependency-check-report
          path: ${{github.workspace}}/reports

  # ═══════════════════════════════════════════════════════════
  # 3. SAST (STATIC APPLICATION SECURITY TESTING)
  # ═══════════════════════════════════════════════════════════
  sast:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: SonarCloud Scan
        uses: SonarSource/sonarcloud-github-action@master
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          SONAR_TOKEN: ${{ secrets.SONAR_TOKEN }}

      - name: Semgrep Scan
        uses: returntocorp/semgrep-action@v1
        with:
          config: >-
            p/security-audit
            p/secrets
            p/owasp-top-ten

      - name: CodeQL Analysis
        uses: github/codeql-action/init@v2
        with:
          languages: javascript, typescript

      - name: Perform CodeQL Analysis
        uses: github/codeql-action/analyze@v2

  # ═══════════════════════════════════════════════════════════
  # 4. CONTAINER SCANNING
  # ═══════════════════════════════════════════════════════════
  container:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Build Docker image
        run: docker build -t myapp:${{ github.sha }} .

      - name: Trivy Container Scan
        uses: aquasecurity/trivy-action@master
        with:
          image-ref: myapp:${{ github.sha }}
          format: "sarif"
          output: "trivy-results.sarif"
          severity: "CRITICAL,HIGH"

      - name: Upload Trivy Results
        uses: github/codeql-action/upload-sarif@v2
        with:
          sarif_file: "trivy-results.sarif"

      - name: Grype Scan
        uses: anchore/scan-action@v3
        with:
          image: myapp:${{ github.sha }}
          fail-build: true
          severity-cutoff: high

  # ═══════════════════════════════════════════════════════════
  # 5. LICENSE COMPLIANCE
  # ═══════════════════════════════════════════════════════════
  license:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: FOSSA Scan
        uses: fossas/fossa-action@main
        with:
          api-key: ${{ secrets.FOSSA_API_KEY }}

      - name: License Checker
        run: |
          npm install -g license-checker
          license-checker --production --onlyAllow 'MIT;Apache-2.0;BSD-2-Clause;BSD-3-Clause;ISC'

  # ═══════════════════════════════════════════════════════════
  # 6. SECURITY REPORTING
  # ═══════════════════════════════════════════════════════════
  report:
    runs-on: ubuntu-latest
    needs: [secrets, dependencies, sast, container, license]
    if: always()
    steps:
      - name: Aggregate Security Results
        run: |
          echo "Security scan complete!"
          echo "Check individual job results for details"

      - name: Notify Security Team
        if: failure()
        uses: 8398a7/action-slack@v3
        with:
          status: ${{ job.status }}
          text: "🚨 Security scan failed! Check results."
          webhook_url: ${{ secrets.SLACK_WEBHOOK_URL }}
```

---

<div align="center">

## ⚡ Performance Optimization

_Make your pipelines blazing fast_ 🏃‍♂️

</div>

### Pipeline Optimization Techniques

```yaml
# ═══════════════════════════════════════════════════════════
# OPTIMIZED PIPELINE - GITHUB ACTIONS
# Multiple performance optimization techniques
# ═══════════════════════════════════════════════════════════

name: Optimized Pipeline

on: [push]

# Cancel in-progress runs
concurrency:
  group: ${{ github.workflow }}-${{ github.ref }}
  cancel-in-progress: true

jobs:
  # ═══════════════════════════════════════════════════════════
  # TECHNIQUE 1: SMART CACHING
  # ═══════════════════════════════════════════════════════════
  build-with-cache:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      # Cache dependencies
      - name: Cache node modules
        uses: actions/cache@v3
        with:
          path: |
            ~/.npm
            node_modules
            .next/cache
          key: ${{ runner.os }}-node-${{ hashFiles('**/package-lock.json') }}
          restore-keys: |
            ${{ runner.os }}-node-

      # Cache build output
      - name: Cache build
        uses: actions/cache@v3
        with:
          path: dist
          key: ${{ runner.os }}-build-${{ github.sha }}

      - run: npm ci
      - run: npm run build

  # ═══════════════════════════════════════════════════════════
  # TECHNIQUE 2: MATRIX PARALLELIZATION
  # ═══════════════════════════════════════════════════════════
  test-parallel:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        # Split tests into chunks
        shard: [1, 2, 3, 4]
        total-shards: [4]
    steps:
      - uses: actions/checkout@v4
      - run: npm ci

      # Run only this shard's tests
      - name: Run tests (shard ${{ matrix.shard }})
        run: npm test -- --shard=${{ matrix.shard }}/${{ matrix.total-shards }}

  # ═══════════════════════════════════════════════════════════
  # TECHNIQUE 3: CONDITIONAL EXECUTION
  # ═══════════════════════════════════════════════════════════
  smart-execution:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0

      # Detect changed files
      - name: Get changed files
        id: changed-files
        uses: tj-actions/changed-files@v40
        with:
          files: |
            src/**
            tests/**

      # Only run if relevant files changed
      - name: Run tests
        if: steps.changed-files.outputs.any_changed == 'true'
        run: npm test

      # Only build Docker if Dockerfile changed
      - name: Build Docker
        if: contains(steps.changed-files.outputs.all_changed_files, 'Dockerfile')
        run: docker build -t myapp .

  # ═══════════════════════════════════════════════════════════
  # TECHNIQUE 4: REUSABLE WORKFLOWS
  # ═══════════════════════════════════════════════════════════
  use-reusable:
    uses: ./.github/workflows/reusable-build.yml
    with:
      node-version: "20.x"

  # ═══════════════════════════════════════════════════════════
  # TECHNIQUE 5: DOCKER LAYER CACHING
  # ═══════════════════════════════════════════════════════════
  docker-optimized:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v3

      - name: Build with cache
        uses: docker/build-push-action@v5
        with:
          context: .
          # GitHub Actions cache
          cache-from: type=gha
          cache-to: type=gha,mode=max
          tags: myapp:latest

  # ═══════════════════════════════════════════════════════════
  # TECHNIQUE 6: ARTIFACT REUSE
  # ═══════════════════════════════════════════════════════════
  build-once:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: npm ci
      - run: npm run build

      # Upload artifact
      - uses: actions/upload-artifact@v3
        with:
          name: build
          path: dist/

  deploy:
    needs: build-once
    runs-on: ubuntu-latest
    steps:
      # Download artifact (no rebuild needed!)
      - uses: actions/download-artifact@v3
        with:
          name: build
          path: dist/

      - name: Deploy
        run: ./deploy.sh
```

---

### Performance Comparison

```
⚡ PIPELINE SPEED OPTIMIZATION RESULTS:

BEFORE OPTIMIZATION:
├── Total time: 25 minutes
├── Tests: 15 minutes
├── Build: 8 minutes
└── Deploy: 2 minutes

AFTER OPTIMIZATION:
├── Total time: 8 minutes (68% faster!)
├── Tests: 4 minutes (parallelized)
├── Build: 3 minutes (cached)
└── Deploy: 1 minute (artifact reuse)

TECHNIQUES APPLIED:
✅ Dependency caching
✅ Build output caching
✅ Test parallelization (4 shards)
✅ Docker layer caching
✅ Conditional execution
✅ Artifact reuse
✅ Canceled duplicate runs
```

---

<div align="center">

## 🎯 Choosing the Right Tool

_The ultimate decision framework_ 🤔

</div>

### Decision Matrix

```
📊 CHOOSE BASED ON YOUR SITUATION:

┌─────────────────────────────────────────────────────────┐
│ IF YOU'RE A...                                           │
├─────────────────────────────────────────────────────────┤
│ Solo developer / Small startup                          │
│ └→ GitHub Actions (if on GitHub)                        │
│ └→ GitLab CI/CD Free (if want self-hosted)              │
│                                                          │
│ Growing startup (5-20 people)                            │
│ └→ GitHub Actions or CircleCI                           │
│ └→ GitLab CI/CD (for complete DevOps)                   │
│                                                          │
│ Enterprise (100+ people)                                 │
│ └→ Jenkins (maximum control)                            │
│ └→ GitLab Self-Hosted (complete platform)               │
│ └→ Azure DevOps (if Microsoft stack)                    │
│                                                          │
│ Kubernetes-focused team                                  │
│ └→ Argo CD + Tekton                                     │
│ └→ Flux CD                                               │
│ └→ GitLab + Argo CD combo                               │
│                                                          │
│ Need AI-powered deployments                              │
│ └→ Harness                                               │
│ └→ GitHub Actions (Copilot integration)                 │
└─────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│ IF YOUR PRIORITY IS...                                   │
├─────────────────────────────────────────────────────────┤
│ Speed & Performance                                      │
│ └→ CircleCI (caching, parallelism)                      │
│ └→ BuildKite (hybrid model)                             │
│                                                          │
│ Cost (Budget-conscious)                                  │
│ └→ Jenkins (free, but self-hosted)                      │
│ └→ GitHub Actions (free for public)                     │
│ └→ GitLab Free Tier                                     │
│                                                          │
│ Ease of Use                                              │
│ └→ GitHub Actions (if on GitHub)                        │
│ └→ GitLab CI/CD                                         │
│ └→ Buddy                                                 │
│                                                          │
│ Flexibility & Customization                              │
│ └→ Jenkins (plugins galore)                             │
│ └→ Tekton (Kubernetes-native)                           │
│                                                          │
│ Security & Compliance                                    │
│ └→ GitLab (built-in security)                           │
│ └→ Azure DevOps (enterprise features)                   │
│ └→ Harness (automated verification)                     │
└─────────────────────────────────────────────────────────┘
```

---

<div align="center">

## 💡 Best Practices

_Universal CI/CD wisdom_ 🎓

</div>

### The CI/CD Commandments

```
🏆 THE 20 COMMANDMENTS OF CI/CD:

1️⃣  Keep pipelines FAST (< 10 minutes ideal)
    • Cache dependencies
    • Parallelize tests
    • Only run necessary steps

2️⃣  Fail FAST (detect issues early)
    • Lint/format first
    • Run unit tests before integration
    • Security scans before deploy

3️⃣  Make pipelines RELIABLE
    • No flaky tests
    • Retry transient failures
    • Deterministic builds

4️⃣  Pipeline as CODE
    • Version control your CI/CD config
    • Review changes like code
    • Reusable components

5️⃣  Security EVERYWHERE
    • Secret scanning
    • Dependency scanning
    • Container scanning
    • SAST/DAST

6️⃣  Automate EVERYTHING
    • Tests
    • Deployments
    • Rollbacks
    • Monitoring

7️⃣  MONITOR pipelines
    • Track success rate
    • Monitor build times
    • Alert on failures
    • DORA metrics

8️⃣  Use CACHING wisely
    • Dependencies
    • Build outputs
    • Docker layers
    • Test results

9️⃣  Test in PRODUCTION-like environment
    • Same OS/versions
    • Same dependencies
    • Similar data

🔟 Keep secrets SECURE
    • Never commit secrets
    • Use secret management
    • Rotate regularly
    • Minimal permissions

1️⃣1️⃣  Make rollbacks EASY
    • Tag releases
    • Keep old versions
    • Automated rollback
    • Test rollback process

1️⃣2️⃣  Document EVERYTHING
    • README for setup
    • Pipeline diagrams
    • Troubleshooting guides
    • Runbooks

1️⃣3️⃣  Use ARTIFACTS properly
    • Build once, deploy many
    • Store artifacts
    • Version artifacts
    • Clean up old ones

1️⃣4️⃣  Implement GATES
    • Manual approvals for prod
    • Security gates
    • Performance gates
    • Business approval

1️⃣5️⃣  Parallelize WISELY
    • Independent jobs
    • Split tests
    • Multiple environments
    • But don't overdo it

1️⃣6️⃣  Keep feedback LOOPS tight
    • Notify on failures
    • Quick debug info
    • Actionable errors
    • Link to logs

1️⃣7️⃣  Environment PARITY
    • Dev == Staging == Prod
    • Same configs
    • Same versions
    • Infrastructure as Code

1️⃣8️⃣  Clean REGULARLY
    • Old artifacts
    • Unused branches
    • Failed builds
    • Cache cleanup

1️⃣9️⃣  Test the PIPELINE
    • Dry runs
    • Separate test pipeline
    • Canary for pipeline changes
    • Rollback plan

2️⃣0️⃣  Continuous IMPROVEMENT
    • Review metrics
    • Optimize bottlenecks
    • Update tools
    • Learn from failures
```

---

### Pipeline Health Checklist

```markdown
✅ HEALTHY PIPELINE CHECKLIST:

## Speed

- [ ] Pipeline completes in < 10 minutes
- [ ] Tests are parallelized
- [ ] Dependencies are cached
- [ ] Docker layers are cached
- [ ] Unnecessary steps skipped

## Reliability

- [ ] Success rate > 95%
- [ ] No flaky tests
- [ ] Automatic retries for transient failures
- [ ] Deterministic builds

## Security

- [ ] Secret scanning enabled
- [ ] Dependency scanning enabled
- [ ] Container scanning enabled
- [ ] SAST enabled
- [ ] No secrets in logs

## Observability

- [ ] Build notifications work
- [ ] Logs are accessible
- [ ] Metrics tracked
- [ ] Alerts configured
- [ ] Dashboard exists

## Maintenance

- [ ] Documentation up to date
- [ ] Regularly updated dependencies
- [ ] Old artifacts cleaned
- [ ] Pipeline code reviewed
- [ ] Disaster recovery plan

## Developer Experience

- [ ] Easy to debug failures
- [ ] Clear error messages
- [ ] Fast feedback
- [ ] Self-service
- [ ] Local testing possible
```

---

<div align="center">

## 🐛 Common Issues & Solutions

_Troubleshooting guide_ 🔧

</div>

### Top 10 CI/CD Problems & Solutions

```
1️⃣  PROBLEM: Pipeline is too slow (> 30 minutes)

✅ SOLUTIONS:
• Add caching for dependencies
• Parallelize tests across multiple runners
• Use Docker layer caching
• Run only affected tests
• Upgrade runner resources
• Split into multiple jobs
• Use faster runners (paid tier)

Example:
# Before: 30 minutes
jobs:
  test:
    run: npm test  # All tests sequentially

# After: 8 minutes
jobs:
  test:
    strategy:
      matrix:
        shard: [1, 2, 3, 4]
    run: npm test -- --shard=${{ matrix.shard }}/4

---

2️⃣  PROBLEM: Tests are flaky (random failures)

✅ SOLUTIONS:
• Identify flaky tests (run multiple times)
• Fix root cause (race conditions, timing issues)
• Increase timeouts
• Retry flaky tests automatically
• Quarantine flaky tests
• Use test impact analysis

Example:
# Retry flaky tests
- name: Run tests
  run: npm test
  timeout-minutes: 10
  # Retry on failure
  continue-on-error: true

- name: Retry failed tests
  if: failure()
  run: npm test -- --only-failed --retries=3

---

3️⃣  PROBLEM: Docker builds are slow

✅ SOLUTIONS:
• Use multi-stage builds
• Leverage build cache
• Use .dockerignore
• Order Dockerfile by change frequency
• Use smaller base images
• BuildKit for parallel builds

Example:
# Optimized Dockerfile
FROM node:20-alpine AS deps
WORKDIR /app
COPY package*.json ./
RUN npm ci --production

FROM node:20-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

FROM node:20-alpine
COPY --from=deps /app/node_modules ./node_modules
COPY --from=build /app/dist ./dist
CMD ["node", "dist/index.js"]

---

4️⃣  PROBLEM: Secrets leaked in logs

✅ SOLUTIONS:
• Use secret masking
• Never echo secrets
• Scan for secrets in code
• Use secret management tools
• Audit logs regularly

Example:
# ❌ BAD
- run: echo "API_KEY=${{ secrets.API_KEY }}"

# ✅ GOOD
- run: |
    if [ -z "$API_KEY" ]; then
      echo "API_KEY not set"
      exit 1
    fi
    # Use secret without echoing
  env:
    API_KEY: ${{ secrets.API_KEY }}

---

5️⃣  PROBLEM: Pipeline fails in production but works in CI

✅ SOLUTIONS:
• Ensure environment parity
• Use same Node/Python versions
• Same dependency versions
• Same environment variables
• Test with production data (safely)
• Staging environment matches prod

Example:
# Lock versions everywhere
{
  "engines": {
    "node": "20.11.0",
    "npm": "10.2.4"
  }
}

# Use exact versions in CI
- uses: actions/setup-node@v4
  with:
    node-version: '20.11.0'

---

6️⃣  PROBLEM: High costs for cloud CI/CD

✅ SOLUTIONS:
• Optimize pipeline speed (less minutes)
• Use self-hosted runners
• Cache aggressively
• Clean up old artifacts
• Only run necessary jobs
• Use spot instances
• Optimize runner size

Example:
# Use self-hosted runner for expensive jobs
jobs:
  build:
    runs-on: self-hosted  # Free!
    steps:
      - run: npm run build

  deploy:
    runs-on: ubuntu-latest  # Only for deploy
    needs: build

---

7️⃣  PROBLEM: Deployment failures are hard to debug

✅ SOLUTIONS:
• Comprehensive logging
• Save artifacts on failure
• SSH access to runners
• Screenshot on failure
• Detailed error messages
• Deployment history

Example:
- name: Deploy
  run: ./deploy.sh

- name: Save logs on failure
  if: failure()
  uses: actions/upload-artifact@v3
  with:
    name: deployment-logs
    path: |
      logs/
      /var/log/app/

---

8️⃣  PROBLEM: Can't reproduce CI failures locally

✅ SOLUTIONS:
• Use Docker for CI environment
• Provide local run script
• Document CI setup
• Use act (GitHub Actions locally)
• Match CI dependencies locally

Example:
# Run GitHub Actions locally
$ brew install act
$ act -j test  # Run test job locally

# Or use Docker
$ docker run -v $(pwd):/app node:20 npm test

---

9️⃣  PROBLEM: Pipeline credentials compromised

✅ SOLUTIONS:
• Rotate all secrets immediately
• Audit recent deployments
• Review access logs
• Implement secret scanning
• Use short-lived tokens
• Principle of least privilege

Example:
# Use OIDC instead of static secrets
- name: Configure AWS Credentials
  uses: aws-actions/configure-aws-credentials@v4
  with:
    role-to-assume: arn:aws:iam::ACCOUNT:role/GitHubActions
    aws-region: us-east-1
# No AWS_SECRET_ACCESS_KEY needed!

---

🔟 PROBLEM: Too many merge conflicts in CI config

✅ SOLUTIONS:
• Use reusable workflows
• Modularize pipeline
• Branch protection rules
• Regular config reviews
• Team communication

Example:
# Reusable workflow (no conflicts)
.github/workflows/reusable-test.yml

# Main workflow (rarely changes)
.github/workflows/main.yml:
  jobs:
    test:
      uses: ./.github/workflows/reusable-test.yml
```

---

<div align="center">

## 🎉 You're Now a CI/CD Expert!

**You've learned:**

✅ 10+ major CI/CD tools
✅ Pipeline configuration
✅ Security best practices
✅ Performance optimization
✅ Cost management
✅ Troubleshooting
✅ Modern AI-powered features
✅ Cloud-native approaches

### Remember MrDib's Golden Rules:

> **"Keep it simple, keep it fast, keep it secure."**

> **"Your pipeline should be faster than your coffee break."** ☕

> **"If you're not embarrassed by your first pipeline, you waited too long to ship."**

</div>

---

### Quick Reference Card

```
🎯 CI/CD QUICK REFERENCE:

BEST FOR BEGINNERS:
→ GitHub Actions (if on GitHub)
→ GitLab CI/CD (all-in-one)

BEST FOR SPEED:
→ CircleCI
→ BuildKite

BEST FOR FLEXIBILITY:
→ Jenkins
→ Tekton

BEST FOR KUBERNETES:
→ Argo CD
→ Flux CD

BEST FOR ENTERPRISE:
→ Azure DevOps
→ GitLab Self-Hosted
→ Harness

BEST FREE OPTIONS:
→ GitHub Actions (public repos)
→ GitLab Free Tier
→ Jenkins (self-hosted)

MOST POPULAR (2025):
1. GitHub Actions
2. GitLab CI/CD
3. Jenkins
4. CircleCI
5. Azure DevOps
```

---

<div align="center">

**Built with ⚙️ by MrDib**

_Now go build some amazing pipelines!_ 🚀

**May your builds always be green** ✅ **and your deploys always be smooth!** 🎯

</div>

---

### Additional Resources

```
📚 ESSENTIAL READING:

Books:
• "Continuous Delivery" by Jez Humble
• "The DevOps Handbook" by Gene Kim
• "Site Reliability Engineering" by Google

Official Docs:
• GitHub Actions: docs.github.com/actions
• GitLab CI/CD: docs.gitlab.com/ee/ci
• Jenkins: jenkins.io/doc
• CircleCI: circleci.com/docs

Communities:
• r/devops
• DevOps Discord servers
• CNCF Slack
• Tool-specific communities

Blogs to Follow:
• Netflix Tech Blog
• GitHub Engineering
• GitLab Blog
• CircleCI Blog
• CNCF Blog

Tools to Learn:
• Docker (containers)
• Kubernetes (orchestration)
• Terraform (infrastructure)
• Prometheus (monitoring)

Certifications:
• GitHub Actions Certification
• GitLab Certified CI/CD Professional
• Kubernetes certifications (CKA, CKAD)
• Cloud provider certifications
```
