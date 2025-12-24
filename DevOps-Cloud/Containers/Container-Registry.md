<div align="center">

# 📦 Container Registries - The Complete Guide

### _Store, secure, and distribute your container images like a pro_ 🏭

![Registry](https://img.shields.io/badge/Registry-Secure%20Storage-purple?style=for-the-badge)
![Distribution](https://img.shields.io/badge/Distribution-Global-blue?style=for-the-badge)
![Security](https://img.shields.io/badge/Security-Hardened-red?style=for-the-badge)
![DevOps](https://img.shields.io/badge/DevOps-Essential-gold?style=for-the-badge)

</div>

---

## 📚 Table of Contents

- [🎯 Understanding Container Registries](#-understanding-container-registries)
- [🌐 Public Container Registries](#-public-container-registries)
- [☁️ Cloud Provider Registries](#️-cloud-provider-registries)
- [🏢 Self-Hosted Registries](#-self-hosted-registries)
- [🔐 Registry Security](#-registry-security)
- [🖊️ Image Signing & Verification](#️-image-signing--verification)
- [🔍 Vulnerability Scanning](#-vulnerability-scanning)
- [⚡ Registry Optimization](#-registry-optimization)
- [🔄 CI/CD Integration](#-cicd-integration)
- [💰 Cost Comparison](#-cost-comparison)
- [🚚 Migration Strategies](#-migration-strategies)
- [💡 Best Practices](#-best-practices)
- [🐛 Troubleshooting](#-troubleshooting)

---

<div align="center">

## 🎯 Understanding Container Registries

_What are they and why do you need one?_ 🤔

</div>

### What is a Container Registry?

```
📦 CONTAINER REGISTRY = IMAGE WAREHOUSE

┌──────────────────────────────────────────────────────────┐
│                    CONTAINER REGISTRY                    │
│                                                          │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐                │
│  │  Image   │  │  Image   │  │  Image   │                │
│  │ myapp:v1 │  │ myapp:v2 │  │ myapp:v3 │  ...           │
│  └──────────┘  └──────────┘  └──────────┘                │
│                                                          │
│  • Storage                                               │
│  • Versioning (tags)                                     │
│  • Distribution                                          │
│  • Access control                                        │
│  • Security scanning                                     │
└──────────────────────────────────────────────────────────┘

Think of it as:
• GitHub for container images
• npm registry for Docker images
• App Store for containers

Purpose:
✅ Store container images
✅ Version management (tags)
✅ Distribute to deployments
✅ Control access (RBAC)
✅ Scan for vulnerabilities
✅ Ensure consistency across environments
```

---

### Registry vs Repository vs Image

```
📊 HIERARCHY EXPLAINED:

Registry (Docker Hub, GHCR, ECR)
  └── Repository (myusername/myapp)
        └── Image + Tag (myapp:v1.0.0, myapp:latest)
              └── Layers (actual data)

Example:
┌────────────────────────────────────────────────┐
│ docker.io/library/nginx:1.25-alpine           │
│    │        │       │     │                    │
│    │        │       │     └── Tag              │
│    │        │       └── Image name             │
│    │        └── Repository (namespace)         │
│    └── Registry                                │
└────────────────────────────────────────────────┘

Real-world example:
• Registry: ghcr.io
• Repository: ghcr.io/mrdib/awesome-app
• Image: ghcr.io/mrdib/awesome-app:v2.1.0
```

---

### Registry Types Comparison

<div align="center">

| Type            | Examples         | Pros                          | Cons                      | Best For                     |
| :-------------- | :--------------- | :---------------------------- | :------------------------ | :--------------------------- |
| **Public**      | Docker Hub, GHCR | Free, easy, no maintenance    | Rate limits, less control | Open source, public projects |
| **Cloud**       | ECR, GCR, ACR    | Managed, integrated, scalable | Vendor lock-in, costs     | Production apps on cloud     |
| **Self-Hosted** | Harbor, Portus   | Full control, private         | Maintenance burden        | On-prem, compliance needs    |
| **Hybrid**      | Harbor + S3      | Best of both worlds           | Complex setup             | Large enterprises            |

</div>

---

<div align="center">

## 🌐 Public Container Registries

_Free and accessible to all_ 🆓

</div>

### Docker Hub

```yaml
# ═══════════════════════════════════════════════════════════
# DOCKER HUB - THE ORIGINAL REGISTRY
# https://hub.docker.com
# ═══════════════════════════════════════════════════════════

Overview:
  Provider: Docker, Inc.
  Launch: 2013
  Default: Yes (docker pull defaults to Docker Hub)
  Market Share: 80%+ of public images

Pricing (2025):
  Personal (Free): • Unlimited public repositories
    • 1 private repository
    • 200 container pulls per 6 hours (unauthenticated)
    • 5,000 container pulls per day (authenticated)
    • No parallel builds

  Pro ($5/month): • Unlimited private repositories
    • Unlimited pulls
    • 5 parallel builds
    • Advanced image management

  Team ($7/user/month): • All Pro features
    • Team collaboration
    • Audit logs
    • Organization management

  Business ($25/user/month): • All Team features
    • SSO (SAML)
    • Image access management
    • SLA support

Features: ✅ Official Images (verified by Docker)
  ✅ Automated builds (GitHub/Bitbucket)
  ✅ Webhooks
  ✅ Organizations & teams
  ✅ README & description
  ✅ Image vulnerability scanning (Pro+)
  ✅ Web UI for management
  ✅ REST API

Pros: ✅ Most popular (everyone knows it)
  ✅ Huge selection of public images
  ✅ Easy to use
  ✅ Good documentation
  ✅ Integrated with Docker CLI
  ✅ Official images are vetted

Cons: ❌ Rate limits (can be annoying)
  ❌ Only 1 private repo (free)
  ❌ Not free for teams
  ❌ No built-in CI/CD
  ❌ Slower than some alternatives
  ❌ Past security incidents (2019 breach)

Use Cases: ✓ Public open-source projects
  ✓ Learning & experimentation
  ✓ Pulling official images
  ✓ Personal projects (1 private repo)

Don't Use For: ✗ Production secrets (use private registry)
  ✗ Multiple private projects (free tier)
  ✗ High-frequency pulls (rate limits)
  ✗ Enterprise compliance
```

**Docker Hub Usage:**

```bash
# ═══════════════════════════════════════════════════════════
# DOCKER HUB COMMANDS
# ═══════════════════════════════════════════════════════════

# Login
docker login
# OR with credentials
docker login -u myusername -p mypassword
# OR with token (more secure!)
echo $DOCKER_TOKEN | docker login -u myusername --password-stdin

# Tag image for Docker Hub
docker tag myapp:latest myusername/myapp:latest
docker tag myapp:latest myusername/myapp:v1.0.0
docker tag myapp:latest myusername/myapp:stable

# Push to Docker Hub
docker push myusername/myapp:latest
docker push myusername/myapp:v1.0.0
docker push myusername/myapp:stable

# Pull from Docker Hub
docker pull myusername/myapp:latest
docker pull nginx:1.25-alpine  # Official image

# Search Docker Hub
docker search nginx
docker search --filter stars=100 nginx

# Logout
docker logout

# ═══════════════════════════════════════════════════════════
# BEST PRACTICES
# ═══════════════════════════════════════════════════════════

# 1. Use access tokens (not password!)
# Generate token: https://hub.docker.com/settings/security

# 2. Always tag with version
docker push myusername/myapp:v1.2.3  # ✅ Good
docker push myusername/myapp:latest  # ⚠️ Also push latest

# 3. Add description & README
# Do this in Docker Hub web UI

# 4. Use .dockerignore
echo "node_modules" >> .dockerignore
echo ".git" >> .dockerignore
echo "*.log" >> .dockerignore

# 5. Authenticate to avoid rate limits
docker login  # Gets you 5,000 pulls/day vs 200 pulls/6hr
```

---

### GitHub Container Registry (GHCR)

```yaml
# ═══════════════════════════════════════════════════════════
# GITHUB CONTAINER REGISTRY (GHCR)
# https://ghcr.io
# ═══════════════════════════════════════════════════════════

Overview:
  Provider: GitHub (Microsoft)
  Launch: 2020
  URL Format: ghcr.io/username/package
  Integration: Native GitHub integration

Pricing (2025):
  Public Packages: • FREE (unlimited storage, unlimited bandwidth)

  Private Packages:
    • FREE: 500 MB storage, 1 GB bandwidth/month
    • Pro ($4/month): 2 GB storage, 10 GB bandwidth
    • Team ($4/user/month): 2 GB storage, 10 GB bandwidth
    • Enterprise: Unlimited

Features: ✅ GitHub integration (link to repo)
  ✅ GitHub Actions native support
  ✅ Fine-grained permissions (per package)
  ✅ Package versioning
  ✅ Automatic README from repo
  ✅ No rate limits (for public)
  ✅ Fast (GitHub CDN)
  ✅ Anonymous pulls (public packages)
  ✅ OCI-compliant

Pros: ✅ Free for public (no rate limits!)
  ✅ Integrated with GitHub ecosystem
  ✅ Great GitHub Actions integration
  ✅ Simple authentication (GitHub token)
  ✅ Fast & reliable (Microsoft infrastructure)
  ✅ Per-package permissions
  ✅ Anonymous pulls for public

Cons: ❌ Requires GitHub account
  ❌ Less discovery (not as popular as Docker Hub)
  ❌ No vulnerability scanning (yet)
  ❌ GitHub ecosystem only
  ❌ Newer (less mature)

Use Cases: ✓ GitHub-hosted projects
  ✓ GitHub Actions CI/CD
  ✓ Open source projects
  ✓ Want to avoid Docker Hub rate limits
  ✓ Free private images (small projects)

Winner: Best for GitHub users! 🏆
```

**GHCR Usage:**

```bash
# ═══════════════════════════════════════════════════════════
# GITHUB CONTAINER REGISTRY COMMANDS
# ═══════════════════════════════════════════════════════════

# Generate token: https://github.com/settings/tokens
# Scopes needed: write:packages, read:packages, delete:packages

# Login to GHCR
export CR_PAT=YOUR_TOKEN
echo $CR_PAT | docker login ghcr.io -u USERNAME --password-stdin

# Tag for GHCR
docker tag myapp:latest ghcr.io/username/myapp:latest
docker tag myapp:latest ghcr.io/username/myapp:v1.0.0

# Push to GHCR
docker push ghcr.io/username/myapp:latest
docker push ghcr.io/username/myapp:v1.0.0

# Pull from GHCR (public packages = no auth needed!)
docker pull ghcr.io/username/myapp:latest

# Pull private package
docker login ghcr.io
docker pull ghcr.io/username/private-app:latest

# Logout
docker logout ghcr.io
```

**GitHub Actions Integration:**

```yaml
# ═══════════════════════════════════════════════════════════
# GITHUB ACTIONS - BUILD & PUSH TO GHCR
# .github/workflows/docker.yml
# ═══════════════════════════════════════════════════════════

name: Build & Push to GHCR

on:
  push:
    branches: [main]
    tags: ["v*"]
  pull_request:
    branches: [main]

env:
  REGISTRY: ghcr.io
  IMAGE_NAME: ${{ github.repository }}

jobs:
  build-and-push:
    runs-on: ubuntu-latest
    permissions:
      contents: read
      packages: write # Important! For GHCR push

    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v3

      - name: Log in to GHCR
        uses: docker/login-action@v3
        with:
          registry: ${{ env.REGISTRY }}
          username: ${{ github.actor }}
          password: ${{ secrets.GITHUB_TOKEN }} # Automatic!

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
            type=sha

      - name: Build and push
        uses: docker/build-push-action@v5
        with:
          context: .
          push: ${{ github.event_name != 'pull_request' }}
          tags: ${{ steps.meta.outputs.tags }}
          labels: ${{ steps.meta.outputs.labels }}
          cache-from: type=gha
          cache-to: type=gha,mode=max
```

---

### Quay.io

```yaml
# ═══════════════════════════════════════════════════════════
# QUAY.IO - RED HAT'S REGISTRY
# https://quay.io
# ═══════════════════════════════════════════════════════════

Overview:
  Provider: Red Hat (IBM)
  Launch: 2013
  Focus: Security & enterprise features
  Open Source: Yes (quay.io code is open)

Pricing (2025):
  Free: • Unlimited public repositories
    • 10 private repositories (wow!)
    • Vulnerability scanning
    • Robot accounts
    • Build triggers

  Paid Plans:
    • $12.50/month: 50 private repos
    • $125/month: Unlimited private repos
    • Enterprise: Custom pricing

Features: ✅ Clair vulnerability scanning (built-in!)
  ✅ Robot accounts (for CI/CD)
  ✅ Time machine (rollback images)
  ✅ Geo-replication
  ✅ Build triggers (GitHub, Bitbucket, GitLab)
  ✅ Dockerfile analysis
  ✅ Audit logs
  ✅ Application repositories (group images)
  ✅ Fine-grained permissions

Pros: ✅ Generous free tier (10 private repos!)
  ✅ Built-in security scanning
  ✅ Robot accounts (great for CI/CD)
  ✅ Open source (can self-host)
  ✅ Enterprise-grade features
  ✅ No rate limits
  ✅ Time machine feature

Cons: ❌ Less popular than Docker Hub
  ❌ Smaller image selection
  ❌ UI feels dated
  ❌ Slower builds than competitors
  ❌ Red Hat ecosystem

Use Cases: ✓ Need 10+ private repos (free!)
  ✓ Security is priority (vulnerability scanning)
  ✓ Red Hat/OpenShift users
  ✓ Want robot accounts for automation
  ✓ Enterprise features on budget

Hidden Gem: 10 free private repos! 💎
```

---

### GitLab Container Registry

```yaml
# ═══════════════════════════════════════════════════════════
# GITLAB CONTAINER REGISTRY
# https://gitlab.com
# ═══════════════════════════════════════════════════════════

Overview:
  Provider: GitLab
  Launch: 2016
  Integration: Native GitLab CI/CD
  Format: registry.gitlab.com/username/project

Pricing (2025):
  Free: • 5 GB storage
    • 10 GB bandwidth/month
    • Unlimited private repositories
    • GitLab CI/CD included

  Premium ($29/user/month): • 250 GB storage
    • 500 GB bandwidth
    • Advanced CI/CD
    • Dependency scanning

  Ultimate ($99/user/month): • 500 GB storage
    • 1 TB bandwidth
    • Container scanning
    • License compliance

Features: ✅ GitLab CI/CD integration (native)
  ✅ Project-level registries
  ✅ Cleanup policies
  ✅ Dependency proxy (cache Docker Hub!)
  ✅ Container scanning (Ultimate tier)
  ✅ Deploy tokens
  ✅ Group-level sharing
  ✅ Protected tags

Pros: ✅ Free private repos (unlimited!)
  ✅ Native GitLab CI/CD integration
  ✅ Dependency proxy (avoid rate limits!)
  ✅ Part of complete DevOps platform
  ✅ Self-hosted option (GitLab CE)
  ✅ Per-project registries

Cons: ❌ Requires GitLab
  ❌ Storage limits (free tier)
  ❌ Container scanning requires Ultimate
  ❌ GitLab ecosystem only
  ❌ Less popular than GitHub

Use Cases: ✓ GitLab-hosted projects
  ✓ GitLab CI/CD pipelines
  ✓ Need dependency proxy
  ✓ All-in-one DevOps platform
  ✓ Self-hosted GitLab

Unique Feature: Dependency proxy (cache Docker Hub)! 🎯
```

---

<div align="center">

## ☁️ Cloud Provider Registries

_Managed registries from big cloud providers_ ☁️

</div>

### AWS ECR (Elastic Container Registry)

```yaml
# ═══════════════════════════════════════════════════════════
# AWS ECR - AMAZON'S CONTAINER REGISTRY
# ═══════════════════════════════════════════════════════════

Overview:
  Provider: Amazon Web Services
  Launch: 2015
  Types: ECR Public (public.ecr.aws), ECR Private
  Integration: ECS, EKS, Lambda

Pricing (2025):
  Public ECR:
    • FREE: 50 GB storage/month
    • FREE: 500 GB bandwidth/month (to internet)
    • FREE: Unlimited bandwidth (within AWS)

  Private ECR:
    • Storage: $0.10/GB/month
    • Data Transfer:
      - In: FREE
      - Out to internet: $0.09/GB
      - Within AWS: FREE

Features:
  ✅ Image scanning (ECR Enhanced Scanning)
  ✅ Lifecycle policies (auto-cleanup)
  ✅ Encryption at rest (KMS)
  ✅ IAM integration
  ✅ Cross-region replication
  ✅ Pull through cache (Docker Hub, etc.)
  ✅ OCI support
  ✅ Resource tagging
  ✅ CloudWatch metrics
  ✅ VPC endpoints (private access)

Pros:
  ✅ Deep AWS integration (ECS, EKS, Lambda)
  ✅ IAM for fine-grained access
  ✅ Enhanced scanning (OS + language packages)
  ✅ High availability (AWS SLA)
  ✅ Fast (within AWS)
  ✅ Pull through cache (avoid Docker Hub limits)
  ✅ Cross-region replication
  ✅ Immutable tags

Cons:
  ❌ AWS-specific
  ❌ More expensive than competitors
  ❌ Complex IAM permissions
  ❌ No built-in CI/CD (use CodeBuild)
  ❌ Not beginner-friendly

Use Cases:
  ✓ AWS ECS/EKS deployments
  ✓ Lambda container images
  ✓ Need AWS IAM integration
  ✓ High-security requirements
  ✓ Already on AWS

Pricing Example:
  • 100 GB storage: $10/month
  • 100 GB transfer (out): $9/month
  • Total: ~$19/month
```

**ECR Usage:**

```bash
# ═══════════════════════════════════════════════════════════
# AWS ECR COMMANDS
# ═══════════════════════════════════════════════════════════

# Create repository
aws ecr create-repository --repository-name myapp

# Get login token & login
aws ecr get-login-password --region us-east-1 | \
  docker login --username AWS --password-stdin \
  123456789012.dkr.ecr.us-east-1.amazonaws.com

# Tag image for ECR
docker tag myapp:latest \
  123456789012.dkr.ecr.us-east-1.amazonaws.com/myapp:latest

# Push to ECR
docker push \
  123456789012.dkr.ecr.us-east-1.amazonaws.com/myapp:latest

# Pull from ECR
docker pull \
  123456789012.dkr.ecr.us-east-1.amazonaws.com/myapp:latest

# Set lifecycle policy (auto-delete old images)
cat > lifecycle-policy.json <<EOF
{
  "rules": [{
    "rulePriority": 1,
    "description": "Keep last 10 images",
    "selection": {
      "tagStatus": "any",
      "countType": "imageCountMoreThan",
      "countNumber": 10
    },
    "action": {
      "type": "expire"
    }
  }]
}
EOF

aws ecr put-lifecycle-policy \
  --repository-name myapp \
  --lifecycle-policy-text file://lifecycle-policy.json

# Enable image scanning
aws ecr put-image-scanning-configuration \
  --repository-name myapp \
  --image-scanning-configuration scanOnPush=true

# Enable cross-region replication
aws ecr put-replication-configuration \
  --replication-configuration file://replication-config.json
```

---

### GCP Artifact Registry

```yaml
# ═══════════════════════════════════════════════════════════
# GCP ARTIFACT REGISTRY (Replaces GCR)
# ═══════════════════════════════════════════════════════════

Overview:
  Provider: Google Cloud Platform
  Launch: 2021 (GA)
  Legacy: GCR (gcr.io) being deprecated
  URL: REGION-docker.pkg.dev/PROJECT/REPO/IMAGE
  Format: Regional, multi-regional

Pricing (2025):
  Storage:
    • First 0.5 GB: FREE
    • $0.10/GB/month (Standard)
    • $0.020/GB/month (Archive - coming soon)

  Network:
    • Egress within same region: FREE
    • Egress to other GCP regions: $0.01/GB
    • Egress to internet: $0.12/GB

Features:
  ✅ Multi-format (Docker, Maven, npm, Python, etc.)
  ✅ Vulnerability scanning (built-in)
  ✅ IAM integration
  ✅ Artifact Analysis
  ✅ Regional & multi-regional
  ✅ Immutable tags
  ✅ Cleanup policies
  ✅ VPC Service Controls
  ✅ Customer-managed encryption keys (CMEK)
  ✅ Remote repositories (proxy)

Pros:
  ✅ Multi-format (not just Docker!)
  ✅ Better than legacy GCR
  ✅ GCP IAM integration
  ✅ Vulnerability scanning included
  ✅ Regional control (latency & compliance)
  ✅ Good pricing
  ✅ Remote repositories (cache Docker Hub)

Cons:
  ❌ GCP-specific
  ❌ Migration from GCR required
  ❌ More complex URL structure
  ❌ Newer (less mature than ECR)
  ❌ No free tier (but 0.5GB free)

Use Cases:
  ✓ GKE deployments
  ✓ Cloud Run applications
  ✓ Need multi-format registry
  ✓ Already on GCP
  ✓ Want proxy/cache features

Unique: Multi-format support! (Docker + npm + Maven + Python)
```

**Artifact Registry Usage:**

```bash
# ═══════════════════════════════════════════════════════════
# GCP ARTIFACT REGISTRY COMMANDS
# ═══════════════════════════════════════════════════════════

# Create repository
gcloud artifacts repositories create myapp \
  --repository-format=docker \
  --location=us-central1 \
  --description="My application images"

# Configure Docker authentication
gcloud auth configure-docker us-central1-docker.pkg.dev

# Tag image for Artifact Registry
docker tag myapp:latest \
  us-central1-docker.pkg.dev/my-project/myapp/myapp:latest

# Push to Artifact Registry
docker push \
  us-central1-docker.pkg.dev/my-project/myapp/myapp:latest

# Pull from Artifact Registry
docker pull \
  us-central1-docker.pkg.dev/my-project/myapp/myapp:latest

# Enable vulnerability scanning
gcloud artifacts repositories update myapp \
  --location=us-central1 \
  --enable-scanning

# Set up cleanup policy
gcloud artifacts repositories set-cleanup-policies myapp \
  --location=us-central1 \
  --policy=policy.json

# Migrate from GCR to Artifact Registry
gcloud container images list --repository=gcr.io/my-project
# Then re-tag and push to Artifact Registry
```

---

### Azure Container Registry (ACR)

```yaml
# ═══════════════════════════════════════════════════════════
# AZURE CONTAINER REGISTRY (ACR)
# ═══════════════════════════════════════════════════════════

Overview:
  Provider: Microsoft Azure
  Launch: 2017
  URL: REGISTRY.azurecr.io/IMAGE:TAG
  Tiers: Basic, Standard, Premium

Pricing (2025):
  Basic: • $5/month (per registry)
    • 10 GB storage included
    • 100 GB bandwidth/day
    • 2 webhooks

  Standard: • $20/month
    • 100 GB storage included
    • 200 GB bandwidth/day
    • 10 webhooks

  Premium: • $50/month
    • 500 GB storage included
    • Unlimited bandwidth/day
    • 500 webhooks
    • Geo-replication
    • Content Trust
    • Private Link

Features: ✅ Geo-replication (Premium)
  ✅ Content Trust (image signing)
  ✅ Webhook support
  ✅ ACR Tasks (build images in cloud)
  ✅ Azure Active Directory integration
  ✅ VNet & Private Link
  ✅ Customer-managed keys
  ✅ Vulnerability scanning (Defender for Cloud)
  ✅ Artifact caching
  ✅ Helm charts support

Pros: ✅ Azure ecosystem integration (AKS, App Service)
  ✅ Geo-replication (Premium) - amazing!
  ✅ ACR Tasks (cloud builds)
  ✅ Content Trust for signing
  ✅ Private Link support
  ✅ Good enterprise features
  ✅ Azure AD integration

Cons: ❌ Azure-specific
  ❌ Premium needed for best features
  ❌ More expensive than competitors
  ❌ Complex pricing tiers
  ❌ UI less intuitive

Use Cases: ✓ Azure AKS deployments
  ✓ Azure App Service containers
  ✓ Need geo-replication
  ✓ Already on Azure
  ✓ Enterprise compliance

Best Feature: Geo-replication! (deploy close to users globally)
```

**ACR Usage:**

```bash
# ═══════════════════════════════════════════════════════════
# AZURE CONTAINER REGISTRY COMMANDS
# ═══════════════════════════════════════════════════════════

# Create registry
az acr create \
  --name myregistry \
  --resource-group mygroup \
  --sku Premium \
  --location eastus

# Login to ACR
az acr login --name myregistry

# Tag image for ACR
docker tag myapp:latest myregistry.azurecr.io/myapp:latest

# Push to ACR
docker push myregistry.azurecr.io/myapp:latest

# Pull from ACR
docker pull myregistry.azurecr.io/myapp:latest

# Enable geo-replication (Premium only)
az acr replication create \
  --registry myregistry \
  --location westus

# Set up ACR Tasks (cloud build)
az acr task create \
  --registry myregistry \
  --name buildtask \
  --context https://github.com/user/repo.git \
  --file Dockerfile \
  --git-access-token $GITHUB_TOKEN

# Enable Content Trust (signing)
export DOCKER_CONTENT_TRUST=1
export DOCKER_CONTENT_TRUST_SERVER=https://myregistry.azurecr.io

# Enable vulnerability scanning
az security atp storage update \
  --resource-group mygroup \
  --is-enabled true
```

---

### Cloud Registry Comparison

<div align="center">

| Feature                    | AWS ECR          | GCP Artifact Registry | Azure ACR         | Winner     |
| :------------------------- | :--------------- | :-------------------- | :---------------- | :--------- |
| **Pricing (100GB)**        | $10/mo storage   | $10/mo storage        | $20/mo (Standard) | 🏆 AWS/GCP |
| **Free Tier**              | None             | 0.5 GB free           | None              | 🏆 GCP     |
| **Vulnerability Scanning** | ✅ Enhanced      | ✅ Built-in           | ✅ Defender       | 🤝 Tie     |
| **Multi-format**           | ❌ Docker only   | ✅ Docker+Maven+npm   | ❌ Docker+Helm    | 🏆 GCP     |
| **Geo-Replication**        | ✅ Yes           | ✅ Multi-regional     | ✅ Premium only   | 🏆 AWS/GCP |
| **Pull Through Cache**     | ✅ Yes           | ✅ Yes                | ✅ Yes            | 🤝 Tie     |
| **CI/CD Integration**      | CodeBuild        | Cloud Build           | ACR Tasks         | 🤝 Tie     |
| **Private Network**        | ✅ VPC Endpoints | ✅ VPC SC             | ✅ Private Link   | 🤝 Tie     |

</div>

**Recommendation:**

- **AWS users:** ECR (no-brainer)
- **GCP users:** Artifact Registry (modern, multi-format)
- **Azure users:** ACR Premium (geo-replication!)
- **Multi-cloud:** GHCR or Harbor

---

<div align="center">

## 🏢 Self-Hosted Registries

_Run your own registry_ 🏠

</div>

### Harbor

```yaml
# ═══════════════════════════════════════════════════════════
# HARBOR - OPEN SOURCE ENTERPRISE REGISTRY
# https://goharbor.io
# ═══════════════════════════════════════════════════════════

Overview:
  Provider: CNCF (Cloud Native Computing Foundation)
  License: Apache 2.0 (Open Source)
  Launch: 2016 (VMware, now CNCF)
  Status: CNCF Graduated Project

Features:
  ✅ Multi-tenancy (projects)
  ✅ RBAC (role-based access control)
  ✅ Image replication (push/pull)
  ✅ Vulnerability scanning (Trivy, Clair)
  ✅ Content Trust (Notary)
  ✅ Image retention policies
  ✅ Webhooks
  ✅ Helm charts support
  ✅ LDAP/AD integration
  ✅ Audit logging
  ✅ Quota management
  ✅ Tag immutability
  ✅ Proxy cache (Docker Hub, etc.)
  ✅ Robot accounts
  ✅ API & Web UI

Pros:
  ✅ Enterprise-grade features
  ✅ Free & open source
  ✅ Self-hosted (full control)
  ✅ No vendor lock-in
  ✅ Active development (CNCF)
  ✅ Great UI
  ✅ Multi-scanner support
  ✅ Replication (multi-site)

Cons:
  ❌ Requires infrastructure
  ❌ You maintain it (upgrades, backups)
  ❌ Complex initial setup
  ❌ Need storage backend (S3, etc.)
  ❌ Security responsibility on you

Use Cases:
  ✓ On-premises deployment
  ✓ Air-gapped environments
  ✓ Compliance requirements
  ✓ Want full control
  ✓ Multi-tenancy needed
  ✓ Large organizations

Installation (Docker Compose):
  # Download installer
  wget https://github.com/goharbor/harbor/releases/download/v2.10.0/harbor-offline-installer-v2.10.0.tgz
  tar xvf harbor-offline-installer-v2.10.0.tgz
  cd harbor

  # Configure
  cp harbor.yml.tmpl harbor.yml
  # Edit harbor.yml (hostname, admin password, etc.)

  # Install
  ./install.sh --with-trivy --with-chartmuseum

  # Access: https://your-harbor-domain

Installation (Kubernetes with Helm):
  helm repo add harbor https://helm.goharbor.io
  helm install harbor harbor/harbor
```

**Harbor Configuration:**

```yaml
# ═══════════════════════════════════════════════════════════
# HARBOR CONFIGURATION - harbor.yml
# ═══════════════════════════════════════════════════════════

hostname: registry.mycompany.com

https:
  port: 443
  certificate: /path/to/cert.crt
  private_key: /path/to/cert.key

harbor_admin_password: Harbor12345 # Change this!

database:
  password: root123
  max_idle_conns: 100
  max_open_conns: 900

data_volume: /data

trivy:
  ignore_unfixed: false
  skip_update: false
  insecure: false

jobservice:
  max_job_workers: 10

notification:
  webhook_job_max_retry: 3

chart:
  absolute_url: disabled

log:
  level: info
  local:
    rotate_count: 50
    rotate_size: 200M
    location: /var/log/harbor

_version: "2.10.0"

proxy:
  http_proxy:
  https_proxy:
  no_proxy:
  components:
    - core
    - jobservice
    - trivy

upload_purging:
  enabled: true
  age: 168h
  interval: 24h
  dryrun: false
```

---

### Docker Registry (Official)

```yaml
# ═══════════════════════════════════════════════════════════
# DOCKER REGISTRY - OFFICIAL OPEN SOURCE
# https://github.com/distribution/distribution
# ═══════════════════════════════════════════════════════════

Overview:
  Provider: Docker, Inc.
  License: Apache 2.0
  Type: Minimalist registry server
  Image: registry:2

Features:
  ✅ Simple HTTP API
  ✅ Storage backends (filesystem, S3, Azure, GCS)
  ✅ TLS support
  ✅ Basic auth
  ✅ Webhooks
  ✅ Token-based authentication
  ✅ Lightweight

Pros:
  ✅ Very simple
  ✅ Official Docker project
  ✅ Minimal resource usage
  ✅ Multiple storage backends
  ✅ Fast

Cons:
  ❌ No UI (command-line only)
  ❌ No vulnerability scanning
  ❌ Basic auth only
  ❌ No RBAC
  ❌ No replication
  ❌ Bare-bones features

Use Cases:
  ✓ Small teams
  ✓ Internal use only
  ✓ Simple needs
  ✓ Want minimal setup
  ✓ Embedded in CI/CD

Deployment:
  docker run -d \
    -p 5000:5000 \
    --name registry \
    --restart=always \
    -v /mnt/registry:/var/lib/registry \
    registry:2

Usage:
  # Tag for local registry
  docker tag myapp:latest localhost:5000/myapp:latest

  # Push
  docker push localhost:5000/myapp:latest

  # Pull
  docker pull localhost:5000/myapp:latest
```

---

### Self-Hosted Comparison

<div align="center">

| Feature         | Harbor    | Docker Registry | Portus | Best              |
| :-------------- | :-------- | :-------------- | :----- | :---------------- |
| **Complexity**  | High      | Low             | Medium | Registry (simple) |
| **UI**          | Excellent | None            | Good   | Harbor            |
| **RBAC**        | ✅ Yes    | ❌ No           | ✅ Yes | Harbor            |
| **Scanning**    | ✅ Yes    | ❌ No           | ✅ Yes | Harbor            |
| **Replication** | ✅ Yes    | ❌ No           | ❌ No  | Harbor            |
| **Resources**   | High      | Low             | Medium | Registry (light)  |
| **Maintenance** | High      | Low             | Medium | Registry (easy)   |

</div>

**Recommendation:**

- **Enterprise:** Harbor (full features)
- **Simple needs:** Docker Registry (minimal)
- **SUSE users:** Portus (integrated)

---

<div align="center">

## 🔐 Registry Security

_Lock down your container images_ 🛡️

</div>

### Authentication & Access Control

```yaml
# ═══════════════════════════════════════════════════════════
# REGISTRY AUTHENTICATION STRATEGIES
# ═══════════════════════════════════════════════════════════

Basic Authentication (Username/Password):
  Pros: ✅ Simple to set up
    ✅ Widely supported
    ✅ Good for development
  Cons: ❌ Credentials can leak
    ❌ No fine-grained permissions
    ❌ Manual rotation

  Best For: Development, small teams
  Security Rating: ⭐⭐☆☆☆

Token-Based Authentication:
  Pros: ✅ Revocable
    ✅ Scoped permissions
    ✅ Time-limited
    ✅ Auditable
  Cons: ❌ Requires token management
    ❌ Complexity for teams

  Best For: Production, CI/CD
  Security Rating: ⭐⭐⭐⭐☆

Service Accounts / Robot Accounts:
  Pros: ✅ Non-human identities
    ✅ Automated workflows
    ✅ Fine-grained permissions
    ✅ Auditable
    ✅ No password rotation
  Cons: ❌ Initial setup complexity

  Best For: CI/CD pipelines, automation
  Security Rating: ⭐⭐⭐⭐⭐ (Best!)

Identity-Based (IAM):
  Pros: ✅ No credentials to manage
    ✅ Cloud-native
    ✅ Centralized access control
    ✅ Automatic rotation
  Cons: ❌ Cloud-specific
    ❌ Vendor lock-in

  Best For: Cloud deployments (ECR, GCR, ACR)
  Security Rating: ⭐⭐⭐⭐⭐
```

**Authentication Examples:**

```bash
# ═══════════════════════════════════════════════════════════
# DOCKER HUB - TOKEN AUTHENTICATION (RECOMMENDED)
# ═══════════════════════════════════════════════════════════

# 1. Generate token: https://hub.docker.com/settings/security
# 2. Save token securely
export DOCKER_TOKEN="dckr_pat_xxxxxxxxxxxxx"

# 3. Login with token (NOT password!)
echo $DOCKER_TOKEN | docker login -u your-username --password-stdin

# ✅ Best Practice: Use tokens, not passwords!

# ═══════════════════════════════════════════════════════════
# GITHUB CONTAINER REGISTRY (GHCR) - GITHUB TOKEN
# ═══════════════════════════════════════════════════════════

# 1. Create Personal Access Token (PAT)
# Go to: https://github.com/settings/tokens
# Scopes: write:packages, read:packages, delete:packages

# 2. Login to GHCR
export CR_PAT="ghp_xxxxxxxxxxxxx"
echo $CR_PAT | docker login ghcr.io -u your-github-username --password-stdin

# 3. In GitHub Actions (automatic!)
- name: Login to GHCR
  uses: docker/login-action@v3
  with:
    registry: ghcr.io
    username: ${{ github.actor }}
    password: ${{ secrets.GITHUB_TOKEN }}  # Automatic!

# ═══════════════════════════════════════════════════════════
# AWS ECR - IAM AUTHENTICATION (NO PERMANENT CREDENTIALS!)
# ═══════════════════════════════════════════════════════════

# Method 1: AWS CLI (temporary token)
aws ecr get-login-password --region us-east-1 | \
  docker login --username AWS --password-stdin \
  123456789012.dkr.ecr.us-east-1.amazonaws.com

# Token expires in 12 hours (secure!)

# Method 2: ECR Credential Helper (automatic!)
# Install: https://github.com/awslabs/amazon-ecr-credential-helper

# Add to ~/.docker/config.json
{
  "credHelpers": {
    "123456789012.dkr.ecr.us-east-1.amazonaws.com": "ecr-login",
    "public.ecr.aws": "ecr-login"
  }
}

# Now docker commands work automatically!
docker push 123456789012.dkr.ecr.us-east-1.amazonaws.com/myapp:latest

# ✅ No manual login needed!

# ═══════════════════════════════════════════════════════════
# GCP ARTIFACT REGISTRY - gcloud AUTHENTICATION
# ═══════════════════════════════════════════════════════════

# Method 1: gcloud (for interactive use)
gcloud auth configure-docker us-central1-docker.pkg.dev

# Method 2: Service Account (for CI/CD)
# 1. Create service account with Artifact Registry Writer role
# 2. Generate JSON key
# 3. Use in CI/CD

# GitHub Actions example:
- name: Authenticate to GCP
  uses: google-github-actions/auth@v1
  with:
    credentials_json: ${{ secrets.GCP_SA_KEY }}

- name: Configure Docker
  run: gcloud auth configure-docker us-central1-docker.pkg.dev

# ═══════════════════════════════════════════════════════════
# AZURE ACR - az CLI AUTHENTICATION
# ═══════════════════════════════════════════════════════════

# Method 1: az CLI (interactive)
az acr login --name myregistry

# Method 2: Service Principal (CI/CD)
az acr login --name myregistry \
  --username $SP_APP_ID \
  --password $SP_PASSWORD

# Method 3: Admin Account (NOT RECOMMENDED FOR PRODUCTION!)
# Enable in portal, use admin credentials
# ⚠️ Use service principals instead!

# ═══════════════════════════════════════════════════════════
# HARBOR - ROBOT ACCOUNTS (RECOMMENDED FOR CI/CD)
# ═══════════════════════════════════════════════════════════

# 1. Create robot account in Harbor UI
#    Project → Robot Accounts → New Robot Account
#    Name: ci-deployer
#    Permissions: Push, Pull

# 2. Save token (shown once!)
export HARBOR_ROBOT_TOKEN="xxxxxx"

# 3. Login
docker login harbor.mycompany.com \
  -u "robot\$ci-deployer" \
  -p "$HARBOR_ROBOT_TOKEN"

# ✅ Robot accounts can't login to UI (more secure!)
```

---

### Network Security

```yaml
# ═══════════════════════════════════════════════════════════
# NETWORK SECURITY CONFIGURATIONS
# ═══════════════════════════════════════════════════════════

Public Registry (Internet Access):
  ├─ Pros: Easy to use, accessible anywhere
  ├─ Cons: Exposed to internet threats
  ├─ Mitigations:
  │  • Strong authentication
  │  • Rate limiting
  │  • DDoS protection
  │  • IP whitelisting (if possible)
  └─ Use For: Public open-source projects

Private Registry (VPC/VNet Only):
  ├─ Pros: Not exposed to internet
  ├─ Cons: Requires VPN/bastion for access
  ├─ Setup:
  │  • VPC endpoints (AWS)
  │  • Private Service Connect (GCP)
  │  • Private Link (Azure)
  └─ Use For: Production workloads

  Example (AWS ECR VPC Endpoint):
    # Create VPC endpoint for ECR
    aws ec2 create-vpc-endpoint \
      --vpc-id vpc-xxxxx \
      --service-name com.amazonaws.us-east-1.ecr.dkr \
      --route-table-ids rtb-xxxxx

    # Now ECR traffic stays in VPC (no internet!)

Hybrid (Private with Public Access):
  ├─ Pros: Flexibility
  ├─ Setup:
  │  • Private registry in VPC
  │  • API Gateway/proxy for external access
  │  • VPN for team access
  └─ Use For: Enterprise with remote teams

# ═══════════════════════════════════════════════════════════
# IP WHITELISTING EXAMPLES
# ═══════════════════════════════════════════════════════════

Docker Hub (Paid plans):
  # Configure in Docker Hub settings
  # IP Access Management → Add allowed IPs

  Allowed IPs:
    - 203.0.113.0/24  # Office network
    - 198.51.100.0/24 # CI/CD servers

Harbor:
  # Use Nginx/reverse proxy for IP filtering
  # nginx.conf
  location / {
    # Allow office IP
    allow 203.0.113.0/24;
    # Allow CI/CD
    allow 198.51.100.0/24;
    # Deny all others
    deny all;

    proxy_pass http://harbor:80;
  }

AWS ECR (VPC Endpoint Policy):
  {
    "Statement": [
      {
        "Sid": "AllowPullFromSpecificIPs",
        "Effect": "Allow",
        "Principal": "*",
        "Action": [
          "ecr:GetDownloadUrlForLayer",
          "ecr:BatchGetImage"
        ],
        "Condition": {
          "IpAddress": {
            "aws:SourceIp": [
              "203.0.113.0/24",
              "198.51.100.0/24"
            ]
          }
        }
      }
    ]
  }
```

---

### Registry Policies & Governance

```yaml
# ═══════════════════════════════════════════════════════════
# REGISTRY POLICIES
# ═══════════════════════════════════════════════════════════

Image Retention Policies:

  Why: Save storage costs, reduce attack surface

  Common Strategies:
    • Keep last N images (e.g., last 10)
    • Keep images from last X days (e.g., 90 days)
    • Keep all prod tags (e.g., stable, latest, v*)
    • Delete untagged images (manifests without tags)

  AWS ECR Lifecycle Policy:
    {
      "rules": [
        {
          "rulePriority": 1,
          "description": "Keep last 10 tagged images",
          "selection": {
            "tagStatus": "tagged",
            "tagPrefixList": ["v"],
            "countType": "imageCountMoreThan",
            "countNumber": 10
          },
          "action": {
            "type": "expire"
          }
        },
        {
          "rulePriority": 2,
          "description": "Delete untagged after 7 days",
          "selection": {
            "tagStatus": "untagged",
            "countType": "sinceImagePushed",
            "countUnit": "days",
            "countNumber": 7
          },
          "action": {
            "type": "expire"
          }
        }
      ]
    }

  GCP Artifact Registry (Tag Filters):
    # Keep images with semantic version tags
    gcloud artifacts repositories update myrepo \
      --location=us-central1 \
      --cleanup-policy-delete-after-days=90 \
      --cleanup-policy-keep-tag-prefixes=v,prod,stable

  Harbor (Retention Rules):
    # UI: Project → Policy → Retention
    Rule 1: Keep last 10 images (tag pattern: v*)
    Rule 2: Keep images from last 90 days
    Rule 3: Delete untagged immediately

    Schedule: Daily at 2 AM UTC

Tag Immutability:

  Why: Prevent tag reuse (security + reproducibility)

  Scenario: Someone pushes myapp:v1.0.0, production deploys it.
            Later, someone pushes myapp:v1.0.0 again (different image!).
            Production redeploys and gets different code! 💥

  Solution: Make tags immutable (can't be overwritten)

  AWS ECR (Enable Immutability):
    aws ecr put-image-tag-mutability \
      --repository-name myapp \
      --image-tag-mutability IMMUTABLE

    # Now pushing to existing tag fails!

  Harbor (Tag Immutability):
    # UI: Project → Configuration
    # Enable "Prevent vulnerable images from running"
    # Enable "Automatically scan images on push"
    # Enable "Prevent images with unresolved vulnerabilities"

  Best Practice:
    ✅ Make version tags immutable (v1.0.0, v1.0.1)
    ⚠️ Allow latest/dev tags to be mutable (for development)

Content Trust / Image Signing:

  Why: Verify image authenticity (not tampered with)

  Technologies:
    • Docker Content Trust (DCT) - Notary v1
    • Cosign (Sigstore) - Modern, recommended
    • GPG signing

  See "Image Signing & Verification" section below!

# ═══════════════════════════════════════════════════════════
# ROLE-BASED ACCESS CONTROL (RBAC)
# ═══════════════════════════════════════════════════════════

Common Roles:

  Developer:
    • Pull: ✅ Yes
    • Push: ✅ Yes (dev/feature tags only)
    • Delete: ❌ No
    • Admin: ❌ No

  CI/CD Service:
    • Pull: ✅ Yes
    • Push: ✅ Yes
    • Delete: ❌ No (use retention policies)
    • Admin: ❌ No

  Production Cluster:
    • Pull: ✅ Yes
    • Push: ❌ No
    • Delete: ❌ No
    • Admin: ❌ No

  Admin:
    • Pull: ✅ Yes
    • Push: ✅ Yes
    • Delete: ✅ Yes
    • Admin: ✅ Yes

Harbor RBAC Example:

  Project: myapp

  Members:
    • dev-team (Developers): Developer role
    • ci-robot (Robot): Master role (push/pull)
    • prod-cluster (Robot): Guest role (pull only)
    • john@company.com: Project Admin

  Permissions Matrix:
    ┌─────────────────┬──────┬──────┬────────┬───────┐
    │ Role            │ Pull │ Push │ Delete │ Admin │
    ├─────────────────┼──────┼──────┼────────┼───────┤
    │ Project Admin   │  ✅  │  ✅  │   ✅   │  ✅   │
    │ Master          │  ✅  │  ✅  │   ✅   │  ❌   │
    │ Developer       │  ✅  │  ✅  │   ❌   │  ❌   │
    │ Guest           │  ✅  │  ❌  │   ❌   │  ❌   │
    │ Limited Guest   │  ✅* │  ❌  │   ❌   │  ❌   │
    └─────────────────┴──────┴──────┴────────┴───────┘
    * Limited Guest: Pull only specific images
```

---

<div align="center">

## 🖊️ Image Signing & Verification

_Trust, but verify_ ✍️

</div>

### Why Sign Container Images?

```
🎯 THE PROBLEM:

Container Registry
     ↓
Your image: myapp:v1.0.0
     ↓
BUT... is it REALLY your image?

Threats:
❌ Man-in-the-middle attack (image swapped in transit)
❌ Compromised registry (attacker replaces image)
❌ Supply chain attack (malicious image with same tag)
❌ Insider threat (unauthorized push)

THE SOLUTION: Cryptographic Signing

✅ Verify image came from trusted source (authenticity)
✅ Verify image wasn't tampered with (integrity)
✅ Non-repudiation (can't deny you signed it)
✅ Policy enforcement (only allow signed images)
```

---

### Cosign (Sigstore) - Modern Approach

```yaml
# ═══════════════════════════════════════════════════════════
# COSIGN - THE MODERN WAY TO SIGN CONTAINER IMAGES
# https://github.com/sigstore/cosign
# ═══════════════════════════════════════════════════════════

What is Cosign?
  Provider: Sigstore (Linux Foundation)
  Launch: 2021
  Status: Production-ready, widely adopted

  Features:
    ✅ Simple CLI
    ✅ Keyless signing (no key management!)
    ✅ Store signatures in registry (no separate infra!)
    ✅ Kubernetes integration
    ✅ Policy enforcement
    ✅ SBOM attestation support
    ✅ Open source

Why Cosign > Docker Content Trust?
  ✅ Simpler (no Notary server needed)
  ✅ Keyless signing option
  ✅ Better Kubernetes integration
  ✅ Modern, actively developed
  ✅ Supports SBOM & attestations

Installation:
  # macOS
  brew install cosign

  # Linux
  wget https://github.com/sigstore/cosign/releases/download/v2.2.0/cosign-linux-amd64
  chmod +x cosign-linux-amd64
  sudo mv cosign-linux-amd64 /usr/local/bin/cosign

  # Verify installation
  cosign version
```

**Cosign Usage:**

```bash
# ═══════════════════════════════════════════════════════════
# METHOD 1: KEY-BASED SIGNING (Traditional)
# ═══════════════════════════════════════════════════════════

# 1. Generate key pair (one-time)
cosign generate-key-pair

# Creates:
# - cosign.key (private key - KEEP SECRET!)
# - cosign.pub (public key - share this)

# 2. Sign an image
cosign sign --key cosign.key ghcr.io/mrdib/myapp:v1.0.0

# Enter password for private key
# Signature stored in registry alongside image!

# 3. Verify signature
cosign verify --key cosign.pub ghcr.io/mrdib/myapp:v1.0.0

# Output:
# Verification for ghcr.io/mrdib/myapp:v1.0.0 --
# The following checks were performed on each of these signatures:
#   - The cosign claims were validated
#   - The signatures were verified against the specified public key
# ✅ VERIFIED!

# ═══════════════════════════════════════════════════════════
# METHOD 2: KEYLESS SIGNING (RECOMMENDED!)
# ═══════════════════════════════════════════════════════════

# No key management needed!
# Uses OpenID Connect (OIDC) for identity

# 1. Sign image (keyless)
cosign sign ghcr.io/mrdib/myapp:v1.0.0

# Opens browser for OIDC authentication (GitHub, Google, Microsoft)
# Identity stored in transparency log (Rekor)

# 2. Verify (keyless)
cosign verify \
  --certificate-identity=your-email@example.com \
  --certificate-oidc-issuer=https://github.com/login/oauth \
  ghcr.io/mrdib/myapp:v1.0.0

# ✅ Verified using transparency log!

# ═══════════════════════════════════════════════════════════
# SIGNING IN CI/CD (GITHUB ACTIONS)
# ═══════════════════════════════════════════════════════════

name: Build, Sign, and Push

on:
  push:
    tags: ['v*']

permissions:
  contents: read
  packages: write
  id-token: write  # Required for keyless signing!

jobs:
  build-sign-push:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Install Cosign
        uses: sigstore/cosign-installer@v3

      - name: Login to GHCR
        uses: docker/login-action@v3
        with:
          registry: ghcr.io
          username: ${{ github.actor }}
          password: ${{ secrets.GITHUB_TOKEN }}

      - name: Build and push
        uses: docker/build-push-action@v5
        id: build
        with:
          context: .
          push: true
          tags: ghcr.io/${{ github.repository }}:${{ github.ref_name }}

      - name: Sign image (keyless!)
        env:
          COSIGN_EXPERIMENTAL: 1
        run: |
          cosign sign --yes ghcr.io/${{ github.repository }}:${{ github.ref_name }}

      - name: Verify signature
        env:
          COSIGN_EXPERIMENTAL: 1
        run: |
          cosign verify \
            --certificate-identity-regexp="https://github.com/${{ github.repository }}/*" \
            --certificate-oidc-issuer=https://token.actions.githubusercontent.com \
            ghcr.io/${{ github.repository }}:${{ github.ref_name }}

# ═══════════════════════════════════════════════════════════
# KUBERNETES POLICY ENFORCEMENT (Kyverno + Cosign)
# ═══════════════════════════════════════════════════════════

# Install Kyverno
kubectl create -f https://github.com/kyverno/kyverno/releases/download/v1.11.0/install.yaml

# Create policy: Only allow signed images
apiVersion: kyverno.io/v1
kind: ClusterPolicy
metadata:
  name: require-signed-images
spec:
  validationFailureAction: Enforce
  rules:
    - name: verify-signature
      match:
        any:
        - resources:
            kinds:
              - Pod
      verifyImages:
      - imageReferences:
        - "ghcr.io/mrdib/*"
        attestors:
        - entries:
          - keyless:
              subject: "https://github.com/mrdib/*"
              issuer: "https://token.actions.githubusercontent.com"
              rekor:
                url: https://rekor.sigstore.dev

# Now unsigned pods are rejected!
# Try deploying unsigned image:
kubectl run test --image=ghcr.io/mrdib/unsigned:latest

# ❌ Error: image verification failed

# ═══════════════════════════════════════════════════════════
# SIGNING WITH SBOM (SOFTWARE BILL OF MATERIALS)
# ═══════════════════════════════════════════════════════════

# 1. Generate SBOM with Syft
syft ghcr.io/mrdib/myapp:v1.0.0 -o spdx-json > sbom.json

# 2. Attach SBOM to image
cosign attach sbom --sbom sbom.json ghcr.io/mrdib/myapp:v1.0.0

# 3. Sign SBOM
cosign sign --key cosign.key ghcr.io/mrdib/myapp:v1.0.0

# 4. Verify SBOM
cosign verify-attestation \
  --key cosign.pub \
  --type spdxjson \
  ghcr.io/mrdib/myapp:v1.0.0

# ═══════════════════════════════════════════════════════════
# BEST PRACTICES
# ═══════════════════════════════════════════════════════════

✅ Use keyless signing (no key management!)
✅ Sign in CI/CD (automated)
✅ Enforce signatures in Kubernetes (policy)
✅ Sign SBOMs (supply chain visibility)
✅ Use unique tags (not latest!)
✅ Store public keys in version control
✅ Rotate keys regularly (if using key-based)
✅ Test signature verification before enforcing

❌ Don't commit private keys to Git!
❌ Don't use same key for everything
❌ Don't skip verification in production
❌ Don't sign latest tag (changes!)
```

---

### Docker Content Trust (Legacy)

```yaml
# ═══════════════════════════════════════════════════════════
# DOCKER CONTENT TRUST (DCT) - LEGACY APPROACH
# Based on Notary v1 (being replaced by Notary v2)
# ═══════════════════════════════════════════════════════════

Status: ⚠️ Still works, but Cosign is recommended

Why Use DCT?
  ✅ Built into Docker
  ✅ Works with Docker Hub
  ✅ No external tools

Why NOT Use DCT?
  ❌ Complex setup (Notary server required for self-hosted)
  ❌ Being replaced (Notary v2 / Notation)
  ❌ Less flexible than Cosign
  ❌ Harder to use with Kubernetes

Enable DCT:
  # Enable for all operations
  export DOCKER_CONTENT_TRUST=1

  # Now all pushes/pulls require signatures!
  docker push myregistry.com/myapp:v1.0.0
  # Automatically signs on push

  docker pull myregistry.com/myapp:v1.0.0
  # Fails if not signed or signature invalid

Manual Signing:
  # Sign specific tag
  docker trust sign myregistry.com/myapp:v1.0.0

  # View signatures
  docker trust inspect --pretty myregistry.com/myapp:v1.0.0

⚠️ Recommendation: Use Cosign instead for new projects!
```

---

<div align="center">

## 🔍 Vulnerability Scanning

_Find bugs before attackers do_ 🐛

</div>

### Why Scan Container Images?

```
🎯 THE REALITY:

Average container image contains:
• 500+ packages/libraries
• 50+ known vulnerabilities (CVEs)
• 5-10 HIGH or CRITICAL vulnerabilities

Threats:
❌ Known CVEs in base image (Ubuntu, Alpine)
❌ Vulnerable application dependencies (Log4Shell 💥)
❌ Outdated system packages
❌ Embedded secrets/credentials
❌ Malware

THE SOLUTION: Automated Vulnerability Scanning

✅ Scan on build (CI/CD)
✅ Scan on push (registry)
✅ Scan running images (continuous monitoring)
✅ Block vulnerable images from deploying
```

---

### Scanner Comparison

<div align="center">

| Scanner      | Type            | Cost             | Accuracy   | Speed    | Best For                       |
| :----------- | :-------------- | :--------------- | :--------- | :------- | :----------------------------- |
| **Trivy**    | Open Source     | FREE             | ⭐⭐⭐⭐⭐ | Fast     | 🏆 Best all-around             |
| **Grype**    | Open Source     | FREE             | ⭐⭐⭐⭐⭐ | Fast     | Modern alternative to Trivy    |
| **Clair**    | Open Source     | FREE             | ⭐⭐⭐⭐☆  | Moderate | Harbor integration             |
| **Snyk**     | Commercial/Free | Free tier + Paid | ⭐⭐⭐⭐⭐ | Fast     | Developer-friendly, great UX   |
| **Aqua**     | Commercial      | Enterprise       | ⭐⭐⭐⭐⭐ | Fast     | Enterprise, runtime protection |
| **ECR Scan** | Cloud (AWS)     | Included         | ⭐⭐⭐⭐☆  | Fast     | AWS users                      |
| **GCR Scan** | Cloud (GCP)     | Included         | ⭐⭐⭐⭐☆  | Fast     | GCP users                      |
| **ACR Scan** | Cloud (Azure)   | Paid add-on      | ⭐⭐⭐⭐☆  | Fast     | Azure users                    |

</div>

**Winner:** 🏆 **Trivy** (best free option, widely adopted)

---

### Trivy - The Best Free Scanner

```bash
# ═══════════════════════════════════════════════════════════
# TRIVY - COMPREHENSIVE VULNERABILITY SCANNER
# https://github.com/aquasecurity/trivy
# ═══════════════════════════════════════════════════════════

Installation:
  # macOS
  brew install trivy

  # Linux
  wget https://github.com/aquasecurity/trivy/releases/download/v0.48.0/trivy_0.48.0_Linux-64bit.tar.gz
  tar zxvf trivy_*.tar.gz
  sudo mv trivy /usr/local/bin/

  # Docker
  docker run aquasec/trivy --version

What Trivy Scans:
  ✅ OS packages (apt, yum, apk)
  ✅ Application dependencies (npm, pip, maven, go.mod, Gemfile, etc.)
  ✅ Kubernetes manifests (misconfigurations)
  ✅ Infrastructure as Code (Terraform, CloudFormation)
  ✅ Secrets (API keys, passwords)
  ✅ Licenses (GPL, MIT, etc.)

# ═══════════════════════════════════════════════════════════
# BASIC USAGE
# ═══════════════════════════════════════════════════════════

# Scan local image
trivy image nginx:latest

# Scan image from registry
trivy image ghcr.io/mrdib/myapp:v1.0.0

# Scan Dockerfile
trivy config Dockerfile

# Scan filesystem
trivy fs .

# Scan Git repository
trivy repo https://github.com/mrdib/myapp

# ═══════════════════════════════════════════════════════════
# OUTPUT FORMATS
# ═══════════════════════════════════════════════════════════

# Table (default)
trivy image nginx:latest

# JSON (for automation)
trivy image --format json nginx:latest > scan-results.json

# SARIF (for GitHub Code Scanning)
trivy image --format sarif nginx:latest > results.sarif

# Template (custom format)
trivy image --format template --template "@contrib/html.tpl" \
  -o report.html nginx:latest

# ═══════════════════════════════════════════════════════════
# SEVERITY FILTERING
# ═══════════════════════════════════════════════════════════

# Only show HIGH and CRITICAL
trivy image --severity HIGH,CRITICAL nginx:latest

# Exit with error if HIGH or CRITICAL found (CI/CD!)
trivy image --exit-code 1 --severity HIGH,CRITICAL nginx:latest

# ═══════════════════════════════════════════════════════════
# IGNORING FALSE POSITIVES
# ═══════════════════════════════════════════════════════════

# Create .trivyignore file
cat > .trivyignore <<EOF
# Ignore specific CVE (with reason!)
CVE-2023-12345  # False positive, doesn't affect our use case

# Ignore all CVEs for specific package
pkg:apk/alpine-baselayout@*

# Ignore by expiration date
CVE-2023-54321 exp:2024-12-31  # Will be fixed in next release
EOF

# Trivy will skip ignored CVEs
trivy image --ignorefile .trivyignore nginx:latest

# ═══════════════════════════════════════════════════════════
# SCANNING IN CI/CD
# ═══════════════════════════════════════════════════════════

# GitHub Actions
name: Trivy Scan

on:
  push:
    branches: [main]
  pull_request:

jobs:
  scan:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Build image
        run: docker build -t myapp:${{ github.sha }} .

      - name: Run Trivy
        uses: aquasecurity/trivy-action@master
        with:
          image-ref: myapp:${{ github.sha }}
          format: 'sarif'
          output: 'trivy-results.sarif'
          severity: 'CRITICAL,HIGH'
          exit-code: '1'  # Fail build if vulnerabilities found

      - name: Upload to GitHub Security
        uses: github/codeql-action/upload-sarif@v2
        if: always()
        with:
          sarif_file: 'trivy-results.sarif'

# ═══════════════════════════════════════════════════════════
# SCANNING RUNNING CONTAINERS
# ═══════════════════════════════════════════════════════════

# Scan running container by name
trivy image $(docker inspect --format='{{.Config.Image}}' mycontainer)

# Scan all running containers
for container in $(docker ps --format '{{.Names}}'); do
  echo "Scanning $container..."
  trivy image $(docker inspect --format='{{.Config.Image}}' $container)
done

# Scan Kubernetes cluster
trivy k8s --report summary cluster

# Scan specific namespace
trivy k8s --report summary namespace/default

# ═══════════════════════════════════════════════════════════
# SECRET DETECTION
# ═══════════════════════════════════════════════════════════

# Scan for exposed secrets
trivy image --scanners secret nginx:latest

# Common secrets detected:
# • AWS Access Keys
# • GitHub tokens
# • API keys
# • Private keys
# • Passwords in env vars

# ═══════════════════════════════════════════════════════════
# BEST PRACTICES
# ═══════════════════════════════════════════════════════════

✅ Scan in CI/CD (every build)
✅ Fail builds on HIGH/CRITICAL
✅ Scan base images regularly
✅ Use .trivyignore for false positives (with reasons!)
✅ Update Trivy database regularly (trivy image --download-db-only)
✅ Scan running containers periodically
✅ Integrate with GitHub Security / GitLab Security
✅ Generate reports for audits

❌ Don't ignore all vulnerabilities
❌ Don't skip scanning in production
❌ Don't use outdated base images
❌ Don't commit secrets to images
```

---

### Registry-Integrated Scanning

```yaml
# ═══════════════════════════════════════════════════════════
# AWS ECR IMAGE SCANNING
# ═══════════════════════════════════════════════════════════

Types:
  Basic Scanning:
    • Uses Clair
    • Scans for CVEs
    • Free (included)

  Enhanced Scanning:
    • Uses Amazon Inspector
    • Continuous scanning
    • OS + language packages
    • SBOM generation
    • Cost: $0.09 per image scan (first scan)
           $0.01 per rescan

Enable Basic Scanning:
  aws ecr put-image-scanning-configuration \
    --repository-name myapp \
    --image-scanning-configuration scanOnPush=true

  # Scan on every push!

Enable Enhanced Scanning:
  # Enable at registry level
  aws ecr put-registry-scanning-configuration \
    --scan-type ENHANCED \
    --rules '[{
      "repositoryFilters": [{"filter":"*","filterType":"WILDCARD"}],
      "scanFrequency":"CONTINUOUS_SCAN"
    }]'

View Scan Results:
  aws ecr describe-image-scan-findings \
    --repository-name myapp \
    --image-id imageTag=v1.0.0

  # Output: CVEs, severity, package info

# ═══════════════════════════════════════════════════════════
# GCP ARTIFACT REGISTRY / CONTAINER ANALYSIS
# ═══════════════════════════════════════════════════════════

Enable Scanning:
  # Automatic scanning on push (enabled by default!)

  # Check scanning status
  gcloud artifacts docker images list us-central1-docker.pkg.dev/my-project/myrepo \
    --include-tags

View Vulnerabilities:
  # Using gcloud
  gcloud artifacts docker images describe \
    us-central1-docker.pkg.dev/my-project/myrepo/myapp:v1.0.0 \
    --show-all-metadata

  # Using Container Analysis API
  gcloud container images describe gcr.io/my-project/myapp:v1.0.0 \
    --show-package-vulnerability

Cost:
  • First 1,000 scans/month: FREE
  • Additional: $0.26 per image

# ═══════════════════════════════════════════════════════════
# AZURE CONTAINER REGISTRY - MICROSOFT DEFENDER
# ═══════════════════════════════════════════════════════════

Enable Defender for Containers:
  # Azure Portal: Security Center → Defender Plans → Containers → Enable

  # Or via CLI
  az security pricing create \
    --name Containers \
    --tier Standard

  # Cost: ~$7 per vCore/month

View Scan Results:
  # Azure Portal: ACR → Repositories → Select image → Security

Features:
  • Vulnerability assessment (Qualys)
  • Continuous scanning
  • Recommendations
  • Compliance dashboard
  • Integration with Defender for Cloud

# ═══════════════════════════════════════════════════════════
# HARBOR - INTEGRATED TRIVY/CLAIR SCANNING
# ═══════════════════════════════════════════════════════════

Enable Scanning:
  # Harbor UI: Administration → Interrogation Services
  # Set default scanner: Trivy (recommended) or Clair

  # Enable scan on push
  # Project → Configuration → Enable "Automatically scan images on push"

Configure Policies:
  # Project → Policy → Add Rule

  Policy Example:
    Rule: Prevent vulnerable images
    Severity: HIGH, CRITICAL
    Action: Block pull/deployment

  # Now images with HIGH/CRITICAL can't be pulled!

Scan Manually:
  # UI: Repositories → Select image → Scan

  # API
  curl -X POST "https://harbor.example.com/api/v2.0/projects/myproject/repositories/myapp/artifacts/v1.0.0/scan" \
    -H "authorization: Basic $TOKEN"

View Results:
  # UI shows CVE count badges
  # Click for detailed report

# ═══════════════════════════════════════════════════════════
# COMPARISON
# ═══════════════════════════════════════════════════════════

Feature Comparison:

┌──────────────────┬─────────────┬─────────────┬─────────────┬─────────┐
│ Feature          │ ECR         │ GCP         │ ACR         │ Harbor  │
├──────────────────┼─────────────┼─────────────┼─────────────┼─────────┤
│ Scan on Push     │ ✅ Yes      │ ✅ Yes      │ ✅ Yes      │ ✅ Yes  │
│ Continuous Scan  │ ✅ Enhanced │ ✅ Yes      │ ✅ Defender │ ❌ No   │
│ Block Vulnerable │ ⚠️ Via IAM  │ ⚠️ Via IAM  │ ❌ No       │ ✅ Yes  │
│ SBOM             │ ✅ Enhanced │ ❌ No       │ ❌ No       │ ❌ No   │
│ Cost             │ Free/Paid   │ Free tier   │ Paid        │ FREE    │
│ Scanner          │ Inspector   │ GCP         │ Qualys      │ Choose  │
└──────────────────┴─────────────┴─────────────┴─────────────┴─────────┘

Recommendation:
  • AWS users: Enhanced scanning (worth the cost)
  • GCP users: Built-in (free tier sufficient)
  • Azure users: Defender (if budget allows)
  • Self-hosted: Harbor + Trivy (best free combo)
```

---

<div align="center">

## ⚡ Registry Optimization

_Faster builds, smaller images, lower costs_ 🚀

</div>

### Image Layer Caching

```
🎯 UNDERSTANDING IMAGE LAYERS:

Docker images are built in layers:

Dockerfile:
  FROM ubuntu:22.04          ← Layer 1 (base)
  RUN apt-get update         ← Layer 2
  COPY package.json .        ← Layer 3
  RUN npm install            ← Layer 4 (largest!)
  COPY . .                   ← Layer 5 (changes often)

Problem: Changing Layer 5 rebuilds ONLY Layer 5
         But changing Layer 3 rebuilds Layers 3, 4, 5!

Solution: Order matters! Put least-changing layers first.

═══════════════════════════════════════════════════════════

❌ BAD DOCKERFILE (Inefficient):

FROM node:20-alpine
WORKDIR /app
COPY . .                    # Copies everything (changes often!)
RUN npm install             # Rebuilds deps every time!
CMD ["node", "server.js"]

Build time: 5 minutes (every change!)

═══════════════════════════════════════════════════════════

✅ GOOD DOCKERFILE (Optimized):

FROM node:20-alpine
WORKDIR /app

# Copy only dependency files first (rarely change)
COPY package.json package-lock.json ./
RUN npm ci --only=production  # Cached unless package.json changes!

# Copy application code last (changes often)
COPY . .

CMD ["node", "server.js"]

Build time: 10 seconds (for code changes!)
            5 minutes (only when dependencies change)

Time saved: 98%! 🎉
```

---

### Multi-Stage Builds

```dockerfile
# ═══════════════════════════════════════════════════════════
# MULTI-STAGE BUILDS - REDUCE IMAGE SIZE BY 90%!
# ═══════════════════════════════════════════════════════════

# ❌ SINGLE-STAGE BUILD (Inefficient):

FROM node:20
WORKDIR /app
COPY package*.json ./
RUN npm install  # Includes dev dependencies!
COPY . .
RUN npm run build
CMD ["node", "dist/server.js"]

# Result: 1.2 GB image (includes Node.js, npm, build tools, source code!)

# ═══════════════════════════════════════════════════════════

# ✅ MULTI-STAGE BUILD (Optimized):

# Stage 1: Build (large, but discarded)
FROM node:20 AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

# Stage 2: Production (small, final image)
FROM node:20-alpine  # Smaller base (alpine!)
WORKDIR /app
COPY --from=builder /app/dist ./dist
COPY --from=builder /app/node_modules ./node_modules
COPY package*.json ./
CMD ["node", "dist/server.js"]

# Result: 150 MB image (90% smaller!)

# What's excluded:
# ❌ Source TypeScript files
# ❌ Build tools
# ❌ Dev dependencies
# ❌ test files
# ✅ Only production runtime + compiled code

# ═══════════════════════════════════════════════════════════
# REAL-WORLD EXAMPLES BY LANGUAGE
# ═══════════════════════════════════════════════════════════

# Go (Single Binary)
FROM golang:1.21 AS builder
WORKDIR /app
COPY go.mod go.sum ./
RUN go mod download
COPY . .
RUN CGO_ENABLED=0 GOOS=linux go build -o server

# Final stage: Minimal image!
FROM scratch  # Empty image (smallest possible!)
COPY --from=builder /app/server /server
EXPOSE 8080
CMD ["/server"]

# Result: 10 MB image (just the binary!)

# ═══════════════════════════════════════════════════════════

# Python (Flask/FastAPI)
FROM python:3.12 AS builder
WORKDIR /app
COPY requirements.txt .
RUN pip install --user --no-cache-dir -r requirements.txt

FROM python:3.12-slim
WORKDIR /app
COPY --from=builder /root/.local /root/.local
COPY . .
ENV PATH=/root/.local/bin:$PATH
CMD ["uvicorn", "main:app", "--host", "0.0.0.0"]

# Result: 200 MB (vs 1 GB with full Python image)

# ═══════════════════════════════════════════════════════════

# Java (Spring Boot)
FROM maven:3.9-eclipse-temurin-21 AS builder
WORKDIR /app
COPY pom.xml .
RUN mvn dependency:go-offline
COPY src ./src
RUN mvn package -DskipTests

FROM eclipse-temurin:21-jre-alpine
WORKDIR /app
COPY --from=builder /app/target/*.jar app.jar
EXPOSE 8080
CMD ["java", "-jar", "app.jar"]

# Result: 300 MB (vs 1.5 GB with full Maven + JDK)

# ═══════════════════════════════════════════════════════════

# React (Frontend)
FROM node:20 AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

FROM nginx:alpine
COPY --from=builder /app/build /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

# Result: 25 MB (vs 1.2 GB with Node.js)

# ═══════════════════════════════════════════════════════════
# SIZE COMPARISON
# ═══════════════════════════════════════════════════════════

Language/Framework   Single-Stage   Multi-Stage   Savings
─────────────────────────────────────────────────────────
Node.js (Express)    1.2 GB         150 MB        87%
Go (API)             800 MB         10 MB         99%
Python (FastAPI)     1.0 GB         200 MB        80%
Java (Spring Boot)   1.5 GB         300 MB        80%
React (SPA)          1.2 GB         25 MB         98%

Average savings: 89%!

Benefits:
✅ Faster image pulls (10x faster!)
✅ Lower storage costs (90% less)
✅ Reduced attack surface (fewer packages)
✅ Faster deployments
✅ Lower bandwidth costs
```

---

### Image Optimization Techniques

```dockerfile
# ═══════════════════════════════════════════════════════════
# IMAGE OPTIMIZATION BEST PRACTICES
# ═══════════════════════════════════════════════════════════

# ✅ TECHNIQUE 1: Use Alpine Linux (Smallest Base)
# ────────────────────────────────────────────────────────────

# Regular base images:
FROM ubuntu:22.04        # 77 MB
FROM debian:12           # 124 MB
FROM node:20             # 1.1 GB

# Alpine alternatives:
FROM alpine:3.19         # 7 MB (11x smaller than Ubuntu!)
FROM node:20-alpine      # 135 MB (8x smaller!)
FROM python:3.12-alpine  # 51 MB

# ⚠️ Caveat: Alpine uses musl libc (not glibc)
#    Some binaries may not work. Test thoroughly!

# ═══════════════════════════════════════════════════════════

# ✅ TECHNIQUE 2: Combine RUN Commands (Reduce Layers)
# ────────────────────────────────────────────────────────────

# ❌ BAD: Multiple layers
RUN apt-get update
RUN apt-get install -y curl
RUN apt-get install -y git
RUN apt-get clean
# Result: 4 layers

# ✅ GOOD: Single layer
RUN apt-get update && \
    apt-get install -y curl git && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
# Result: 1 layer (smaller!)

# ═══════════════════════════════════════════════════════════

# ✅ TECHNIQUE 3: Use .dockerignore (Exclude Unnecessary Files)
# ────────────────────────────────────────────────────────────

# .dockerignore file:
node_modules
npm-debug.log
.git
.gitignore
.env
.env.local
*.md
.vscode
.idea
dist
build
coverage
.DS_Store
Dockerfile
docker-compose.yml

# Prevents copying unnecessary files (faster builds + smaller images!)

# ═══════════════════════════════════════════════════════════

# ✅ TECHNIQUE 4: Clean Up in Same RUN Command
# ────────────────────────────────────────────────────────────

# ❌ BAD: Cache remains in layer
RUN apt-get update && apt-get install -y build-essential
RUN rm -rf /var/lib/apt/lists/*  # Too late! Already in previous layer

# ✅ GOOD: Clean up in same command
RUN apt-get update && \
    apt-get install -y build-essential && \
    rm -rf /var/lib/apt/lists/*  # Cleaned before layer finalized

# ═══════════════════════════════════════════════════════════

# ✅ TECHNIQUE 5: Use Specific Package Versions (Reproducibility)
# ────────────────────────────────────────────────────────────

# ❌ BAD: Unpredictable
FROM node:20
RUN npm install express  # Version changes over time!

# ✅ GOOD: Pinned versions
FROM node:20.10.0-alpine3.19
COPY package-lock.json .  # Locks exact versions
RUN npm ci  # Uses lock file (reproducible!)

# ═══════════════════════════════════════════════════════════

# ✅ TECHNIQUE 6: Remove Build Dependencies After Use
# ────────────────────────────────────────────────────────────

# Python example:
FROM python:3.12-alpine
WORKDIR /app

# Install build deps, build, then remove deps (all in one layer!)
RUN apk add --no-cache --virtual .build-deps \
    gcc musl-dev libffi-dev && \
    pip install --no-cache-dir cryptography && \
    apk del .build-deps

# Result: Runtime without build tools (smaller!)

# ═══════════════════════════════════════════════════════════

# ✅ TECHNIQUE 7: Use BuildKit Features (Cache Mounts)
# ────────────────────────────────────────────────────────────

# Enable BuildKit
# export DOCKER_BUILDKIT=1

FROM node:20-alpine
WORKDIR /app
COPY package*.json ./

# Cache npm packages between builds!
RUN --mount=type=cache,target=/root/.npm \
    npm ci --only=production

COPY . .
CMD ["node", "server.js"]

# npm cache persists across builds (faster!)

# ═══════════════════════════════════════════════════════════

# ✅ TECHNIQUE 8: Distroless Images (No Shell, Minimal Attack Surface)
# ────────────────────────────────────────────────────────────

# Multi-stage with distroless
FROM golang:1.21 AS builder
WORKDIR /app
COPY . .
RUN CGO_ENABLED=0 go build -o server

# Distroless base (no shell, no package manager!)
FROM gcr.io/distroless/static-debian12
COPY --from=builder /app/server /
CMD ["/server"]

# Result:
# ✅ Tiny image (base is ~2 MB)
# ✅ No shell (can't be exploited!)
# ✅ Minimal CVEs
# ⚠️ Hard to debug (no shell!)

# ═══════════════════════════════════════════════════════════

# ✅ TECHNIQUE 9: Optimize Layer Order
# ────────────────────────────────────────────────────────────

# Principle: Put rarely-changing layers first

FROM node:20-alpine
WORKDIR /app

# Layer 1: Base image (never changes)
# Layer 2: Package dependencies (changes occasionally)
COPY package*.json ./
RUN npm ci

# Layer 3: Application code (changes frequently)
COPY . .

# Last layer is smallest and rebuilt most often!

# ═══════════════════════════════════════════════════════════
# SIZE OPTIMIZATION CHECKLIST
# ═══════════════════════════════════════════════════════════

Before Optimization: 1.2 GB Node.js app
After applying techniques:

✅ Alpine base:           -900 MB → 300 MB
✅ Multi-stage build:     -150 MB → 150 MB
✅ .dockerignore:          -20 MB → 130 MB
✅ Combine RUN commands:   -10 MB → 120 MB
✅ Clean cache:            -20 MB → 100 MB

Final: 100 MB (92% reduction!)

╔════════════════════════════════════════════════════════╗
║  💡 OPTIMIZATION PRO TIPS:                              ║
╠════════════════════════════════════════════════════════╣
║  • Analyze with: docker history <image>               ║
║  • Find large layers: dive <image>                     ║
║  • Use BuildKit for better caching                     ║
║  • Alpine when possible (but test!)                    ║
║  • Multi-stage for all production images              ║
║  • Never include secrets in layers                     ║
║  • Pin versions for reproducibility                    ║
║  • Test image: docker run --rm -it <image> sh         ║
╚════════════════════════════════════════════════════════╝
```

---

### Registry-Specific Optimizations

```yaml
# ═══════════════════════════════════════════════════════════
# DOCKER HUB OPTIMIZATIONS
# ═══════════════════════════════════════════════════════════

Rate Limit Avoidance:
  Problem: 100 pulls/6hrs (anonymous), 200 pulls/6hrs (free account)

  Solutions:
    ✅ Authenticate (5,000 pulls/day!)
    ✅ Use pull-through cache (Harbor, etc.)
    ✅ Mirror images to your registry
    ✅ Upgrade to Pro ($5/month = unlimited)

Automated Builds:
  # Link GitHub repo for automatic builds
  # Webhook triggers build on push
  # Free for public repos

  Optimization:
    ✅ Use .dockerignore (faster uploads)
    ✅ Small images (faster builds)
    ✅ Cache layers (faster rebuilds)

# ═══════════════════════════════════════════════════════════
# GITHUB CONTAINER REGISTRY (GHCR) OPTIMIZATIONS
# ═══════════════════════════════════════════════════════════

GitHub Actions Caching:
  # Use actions/cache for Docker layers
  - name: Cache Docker layers
    uses: actions/cache@v3
    with:
      path: /tmp/.buildx-cache
      key: ${{ runner.os }}-buildx-${{ github.sha }}
      restore-keys: |
        ${{ runner.os }}-buildx-

  - name: Build and push
    uses: docker/build-push-action@v5
    with:
      cache-from: type=local,src=/tmp/.buildx-cache
      cache-to: type=local,dest=/tmp/.buildx-cache-new,mode=max

  # Result: 10x faster builds!

# ═══════════════════════════════════════════════════════════
# AWS ECR OPTIMIZATIONS
# ═══════════════════════════════════════════════════════════

Lifecycle Policies (Auto-cleanup):
  {
    "rules": [
      {
        "rulePriority": 1,
        "description": "Keep last 10 images",
        "selection": {
          "tagStatus": "tagged",
          "countType": "imageCountMoreThan",
          "countNumber": 10
        },
        "action": {"type": "expire"}
      },
      {
        "rulePriority": 2,
        "description": "Delete untagged after 1 day",
        "selection": {
          "tagStatus": "untagged",
          "countType": "sinceImagePushed",
          "countUnit": "days",
          "countNumber": 1
        },
        "action": {"type": "expire"}
      }
    ]
  }

  Savings: ~80% storage costs!

Image Replication (Multi-region):
  # Replicate to other regions automatically
  aws ecr put-replication-configuration \
    --replication-configuration file://replication.json

  {
    "rules": [
      {
        "destinations": [
          {"region": "us-west-2", "registryId": "123456789012"},
          {"region": "eu-west-1", "registryId": "123456789012"}
        ]
      }
    ]
  }

  # Images available in 3 regions (faster pulls!)

# ═══════════════════════════════════════════════════════════
# GCP ARTIFACT REGISTRY OPTIMIZATIONS
# ═══════════════════════════════════════════════════════════

Remote Repositories (Cache Docker Hub):
  # Create remote repository (caches Docker Hub)
  gcloud artifacts repositories create dockerhub-cache \
    --location=us-central1 \
    --repository-format=docker \
    --mode=remote-repository \
    --remote-repo-config-desc="Docker Hub cache" \
    --remote-docker-repo=DOCKER-HUB

  # Pull through cache
  docker pull us-central1-docker.pkg.dev/my-project/dockerhub-cache/nginx:latest

  # Subsequent pulls are INSTANT (cached!) + no rate limits!

Cleanup Policies:
  gcloud artifacts repositories set-cleanup-policies myrepo \
    --location=us-central1 \
    --policy=policy.json

  # policy.json
  {
    "name": "keep-10-versions",
    "action": "DELETE",
    "condition": {
      "tagState": "TAGGED",
      "olderThan": "2592000s"  # 30 days
    }
  }

# ═══════════════════════════════════════════════════════════
# HARBOR OPTIMIZATIONS
# ═══════════════════════════════════════════════════════════

Replication (Multi-Harbor):
  # UI: Administration → Replications → New Replication Rule

  Source: Harbor A (us-east)
  Destination: Harbor B (eu-west)
  Trigger: Event based (on push)
  Filters: v*, prod*

  # Images auto-replicate to EU harbor!

Proxy Cache (Docker Hub/GHCR):
  # UI: Administration → Registries → New Registry

  Provider: Docker Hub
  Name: dockerhub
  Endpoint: https://hub.docker.com

  # Create proxy cache project
  # Pull through: harbor.mycompany.com/dockerhub/nginx:latest

  # Result: Cached locally, no rate limits!

Quota Management:
  # UI: Projects → myproject → Configuration → Resource Quota

  Storage: 100 GB

  # Prevents runaway storage costs!

# ═══════════════════════════════════════════════════════════
# COST OPTIMIZATION COMPARISON
# ═══════════════════════════════════════════════════════════

Scenario: 100 repos, 1,000 images, 500 GB total

Without Optimization:
  Storage: 500 GB × $0.10/GB = $50/month
  Transfer: 2 TB × $0.09/GB = $180/month
  Total: $230/month

With Optimization:
  ✅ Multi-stage builds (90% smaller): 50 GB storage = $5/month
  ✅ Lifecycle policies (80% reduction): 10 GB storage = $1/month
  ✅ Pull-through cache (70% less transfer): 600 GB = $54/month
  Total: $60/month

Savings: $170/month (74%!) 💰
```

---

<div align="center">

## 🔄 CI/CD Integration

_Automate everything_ 🤖

</div>

### GitHub Actions Integration

```yaml
# ═══════════════════════════════════════════════════════════
# GITHUB ACTIONS - COMPLETE CI/CD PIPELINE
# .github/workflows/docker.yml
# ═══════════════════════════════════════════════════════════

name: Build, Test, Scan, Sign & Deploy

on:
  push:
    branches: [main, develop]
    tags: ['v*']
  pull_request:
    branches: [main]

env:
  REGISTRY: ghcr.io
  IMAGE_NAME: ${{ github.repository }}

jobs:
  # ─────────────────────────────────────────────────────────
  # JOB 1: BUILD & PUSH
  # ─────────────────────────────────────────────────────────
  build:
    runs-on: ubuntu-latest
    permissions:
      contents: read
      packages: write
      id-token: write  # For signing

    outputs:
      image-tag: ${{ steps.meta.outputs.tags }}
      image-digest: ${{ steps.build.outputs.digest }}

    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v3

      - name: Log in to GHCR
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
            type=sha,prefix={{branch}}-
            type=raw,value=latest,enable={{is_default_branch}}

      - name: Build and push
        id: build
        uses: docker/build-push-action@v5
        with:
          context: .
          platforms: linux/amd64,linux/arm64  # Multi-arch!
          push: ${{ github.event_name != 'pull_request' }}
          tags: ${{ steps.meta.outputs.tags }}
          labels: ${{ steps.meta.outputs.labels }}
          cache-from: type=gha
          cache-to: type=gha,mode=max
          provenance: true
          sbom: true  # Generate SBOM automatically!

  # ─────────────────────────────────────────────────────────
  # JOB 2: SECURITY SCAN
  # ─────────────────────────────────────────────────────────
  scan:
    needs: build
    runs-on: ubuntu-latest
    permissions:
      security-events: write

    steps:
      - name: Run Trivy scanner
        uses: aquasecurity/trivy-action@master
        with:
          image-ref: ${{ needs.build.outputs.image-tag }}
          format: 'sarif'
          output: 'trivy-results.sarif'
          severity: 'CRITICAL,HIGH'
          exit-code: '1'  # Fail on vulnerabilities!

      - name: Upload Trivy results to GitHub Security
        uses: github/codeql-action/upload-sarif@v2
        if: always()
        with:
          sarif_file: 'trivy-results.sarif'

  # ─────────────────────────────────────────────────────────
  # JOB 3: SIGN IMAGE
  # ─────────────────────────────────────────────────────────
  sign:
    needs: [build, scan]
    runs-on: ubuntu-latest
    permissions:
      packages: write
      id-token: write

    steps:
      - name: Install Cosign
        uses: sigstore/cosign-installer@v3

      - name: Log in to GHCR
        uses: docker/login-action@v3
        with:
          registry: ${{ env.REGISTRY }}
          username: ${{ github.actor }}
          password: ${{ secrets.GITHUB_TOKEN }}

      - name: Sign image (keyless)
        env:
          COSIGN_EXPERIMENTAL: 1
        run: |
          cosign sign --yes \
            ${{ needs.build.outputs.image-tag }}@${{ needs.build.outputs.image-digest }}

  # ─────────────────────────────────────────────────────────
  # JOB 4: DEPLOY TO PRODUCTION
  # ─────────────────────────────────────────────────────────
  deploy:
    needs: [build, scan, sign]
    runs-on: ubuntu-latest
    if: github.ref == 'refs/heads/main'
    environment: production

    steps:
      - name: Deploy to Kubernetes
        uses: azure/k8s-deploy@v4
        with:
          manifests: |
            k8s/deployment.yml
          images: |
            ${{ needs.build.outputs.image-tag }}@${{ needs.build.outputs.image-digest }}
          imagepullsecrets: |
            ghcr-secret

# ═══════════════════════════════════════════════════════════
# ADVANCED: MATRIX BUILDS (MULTIPLE VERSIONS)
# ═══════════════════════════════════════════════════════════

name: Multi-Version Build

on:
  push:
    branches: [main]

jobs:
  build-matrix:
    strategy:
      matrix:
        node-version: [18, 20, 21]
        arch: [amd64, arm64]

    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Build Node ${{ matrix.node-version }} - ${{ matrix.arch }}
        uses: docker/build-push-action@v5
        with:
          context: .
          build-args: |
            NODE_VERSION=${{ matrix.node-version }}
          platforms: linux/${{ matrix.arch }}
          push: true
          tags: ghcr.io/${{ github.repository }}:node${{ matrix.node-version }}-${{ matrix.arch }}

# ═══════════════════════════════════════════════════════════
# ADVANCED: CONDITIONAL DEPLOYMENTS
# ═══════════════════════════════════════════════════════════

deploy:
  steps:
    - name: Deploy to Dev
      if: github.ref == 'refs/heads/develop'
      run: |
        kubectl set image deployment/myapp \
          myapp=${{ env.IMAGE }} \
          --namespace=dev

    - name: Deploy to Staging
      if: startsWith(github.ref, 'refs/tags/v') && !contains(github.ref, 'rc')
      run: |
        kubectl set image deployment/myapp \
          myapp=${{ env.IMAGE }} \
          --namespace=staging

    - name: Deploy to Production
      if: startsWith(github.ref, 'refs/tags/v') && !contains(github.ref, 'rc') && !contains(github.ref, 'beta')
      run: |
        kubectl set image deployment/myapp \
          myapp=${{ env.IMAGE }} \
          --namespace=production
```

---

### GitLab CI/CD Integration

```yaml
# ═══════════════════════════════════════════════════════════
# GITLAB CI/CD - COMPLETE PIPELINE
# .gitlab-ci.yml
# ═══════════════════════════════════════════════════════════

stages:
  - build
  - test
  - security
  - deploy

variables:
  DOCKER_HOST: tcp://docker:2376
  DOCKER_TLS_CERTDIR: "/certs"
  DOCKER_TLS_VERIFY: 1
  DOCKER_CERT_PATH: "$DOCKER_TLS_CERTDIR/client"
  IMAGE_TAG: $CI_REGISTRY_IMAGE:$CI_COMMIT_REF_SLUG
  LATEST_TAG: $CI_REGISTRY_IMAGE:latest

# ─────────────────────────────────────────────────────────
# BUILD STAGE
# ─────────────────────────────────────────────────────────
build:
  stage: build
  image: docker:24-dind
  services:
    - docker:24-dind
  before_script:
    - echo $CI_REGISTRY_PASSWORD | docker login -u $CI_REGISTRY_USER --password-stdin $CI_REGISTRY
  script:
    # Build
    - docker build -t $IMAGE_TAG -t $LATEST_TAG .

    # Push
    - docker push $IMAGE_TAG
    - docker push $LATEST_TAG
  only:
    - branches
    - tags

# ─────────────────────────────────────────────────────────
# TEST STAGE
# ─────────────────────────────────────────────────────────
test:
  stage: test
  image: $IMAGE_TAG
  script:
    - npm test
  coverage: '/Coverage: \d+\.\d+%/'

# ─────────────────────────────────────────────────────────
# SECURITY SCAN STAGE
# ─────────────────────────────────────────────────────────
container_scanning:
  stage: security
  image: aquasec/trivy:latest
  script:
    - trivy image --exit-code 1 --severity HIGH,CRITICAL $IMAGE_TAG
  allow_failure: false
  only:
    - main
    - tags

# GitLab built-in container scanning (Ultimate tier)
include:
  - template: Security/Container-Scanning.gitlab-ci.yml

# ─────────────────────────────────────────────────────────
# DEPLOY STAGE
# ─────────────────────────────────────────────────────────
deploy_dev:
  stage: deploy
  image: bitnami/kubectl:latest
  script:
    - kubectl config use-context $KUBE_CONTEXT
    - kubectl set image deployment/myapp myapp=$IMAGE_TAG -n dev
    - kubectl rollout status deployment/myapp -n dev
  environment:
    name: development
    url: https://dev.myapp.com
  only:
    - develop

deploy_production:
  stage: deploy
  image: bitnami/kubectl:latest
  script:
    - kubectl config use-context $KUBE_CONTEXT
    - kubectl set image deployment/myapp myapp=$IMAGE_TAG -n production
    - kubectl rollout status deployment/myapp -n production
  environment:
    name: production
    url: https://myapp.com
  when: manual # Require manual approval!
  only:
    - tags
    - main

# ═══════════════════════════════════════════════════════════
# MULTI-STAGE WITH BUILDKIT
# ═══════════════════════════════════════════════════════════

build_optimized:
  stage: build
  image: docker:24-dind
  services:
    - docker:24-dind
  variables:
    DOCKER_BUILDKIT: 1
  before_script:
    - echo $CI_REGISTRY_PASSWORD | docker login -u $CI_REGISTRY_USER --password-stdin $CI_REGISTRY
  script:
    - |
      docker build \
        --cache-from $IMAGE_TAG \
        --build-arg BUILDKIT_INLINE_CACHE=1 \
        -t $IMAGE_TAG \
        .
    - docker push $IMAGE_TAG
```

---

### Jenkins Pipeline

```groovy
// ═══════════════════════════════════════════════════════════
// JENKINS DECLARATIVE PIPELINE
// Jenkinsfile
// ═══════════════════════════════════════════════════════════

pipeline {
    agent any

    environment {
        REGISTRY = 'ghcr.io'
        IMAGE_NAME = "${REGISTRY}/${env.GIT_URL.replaceFirst(/^.*\/([^\/]+?).git$/, '$1')}"
        IMAGE_TAG = "${IMAGE_NAME}:${env.GIT_COMMIT.take(7)}"
        LATEST_TAG = "${IMAGE_NAME}:latest"
        DOCKER_CREDS = credentials('github-token')
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    docker.build("${IMAGE_TAG}")
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    docker.image("${IMAGE_TAG}").inside {
                        sh 'npm test'
                    }
                }
            }
        }

        stage('Security Scan') {
            steps {
                script {
                    sh """
                        docker run --rm \
                          -v /var/run/docker.sock:/var/run/docker.sock \
                          aquasec/trivy image \
                          --exit-code 1 \
                          --severity HIGH,CRITICAL \
                          ${IMAGE_TAG}
                    """
                }
            }
        }

        stage('Push') {
            when {
                branch 'main'
            }
            steps {
                script {
                    docker.withRegistry("https://${REGISTRY}", 'github-token') {
                        docker.image("${IMAGE_TAG}").push()
                        docker.image("${IMAGE_TAG}").push('latest')
                    }
                }
            }
        }

        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                script {
                    sh """
                        kubectl set image deployment/myapp \
                          myapp=${IMAGE_TAG} \
                          --namespace=production
                    """
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
```

---

<div align="center">

## 💰 Cost Comparison

_The real cost of hosting container images_ 💸

</div>

### Detailed Cost Breakdown (2025 Pricing)

```yaml
# ═══════════════════════════════════════════════════════════
# REALISTIC SCENARIO: MEDIUM-SIZED COMPANY
# ═══════════════════════════════════════════════════════════

Company Profile:
  Team Size: 50 developers
  Repositories: 100 (mix of microservices)
  Images: 1,000 total (10 per repo)
  Total Storage: 200 GB (optimized images)
  Monthly Pulls: 50,000 (CI/CD + deployments)
  Monthly Pushes: 5,000 (daily builds)

# ═══════════════════════════════════════════════════════════
# DOCKER HUB
# ═══════════════════════════════════════════════════════════

Docker Hub Pro ($5/user/month):
  Subscription: $5 × 50 users = $250/month
  Storage: Unlimited (included)
  Pulls: Unlimited (included)
  Pushes: Unlimited (included)
  Private Repos: Unlimited (included)
  Parallel Builds: 5 (included)

  Total: $250/month

  Pros:
    ✅ Simple pricing
    ✅ Predictable costs
    ✅ No usage charges

  Cons:
    ❌ Per-user pricing (expensive for large teams)
    ❌ Less features than alternatives

Docker Hub Team ($7/user/month):
  Subscription: $7 × 50 users = $350/month
  + Audit logs
  + Advanced image management

  Total: $350/month

# ═══════════════════════════════════════════════════════════
# GITHUB CONTAINER REGISTRY (GHCR)
# ═══════════════════════════════════════════════════════════

GHCR (with GitHub Team):
  GitHub Team: $4/user/month × 50 = $200/month

  Storage: 50 GB free, then $0.008/GB/month
    200 GB - 50 GB free = 150 GB
    150 GB × $0.008 = $1.20/month

  Bandwidth: 100 GB free, then $0.50/GB
    Estimate: 500 GB/month
    (500 GB - 100 GB) × $0.50 = $200/month

  Total: $200 + $1.20 + $200 = $401.20/month

  ⚠️ Bandwidth can be expensive for heavy usage!

GHCR (Public Repos - FREE!):
  If all images are public:
    Storage: FREE (unlimited!)
    Bandwidth: FREE (unlimited!)
    Total: $0/month 🎉

  Winner for open source!

# ═══════════════════════════════════════════════════════════
# AWS ECR
# ═══════════════════════════════════════════════════════════

AWS ECR Private:
  Storage: $0.10/GB/month
    200 GB × $0.10 = $20/month

  Data Transfer IN: FREE
  Data Transfer OUT (to internet): $0.09/GB
    Estimate: 500 GB/month × $0.09 = $45/month
  Data Transfer OUT (within AWS): FREE

  Enhanced Scanning (optional):
    First scan: $0.09/image
    Continuous scan: $0.01/image/month
    1,000 images × $0.01 = $10/month

  Total: $20 + $45 + $10 = $75/month

  Total (if mostly internal AWS traffic):
    $20 + $10 = $30/month

  Pros:
    ✅ Very cheap for AWS-internal usage!
    ✅ Pay only for what you use

  Cons:
    ❌ Expensive egress for external pulls

AWS ECR Public:
  Storage: FREE (up to 50 GB, then $0.10/GB)
  Data Transfer IN: FREE
  Data Transfer OUT: $0.09/GB (after 50 GB free)

  Total: ~$0-20/month (public images)

# ═══════════════════════════════════════════════════════════
# GCP ARTIFACT REGISTRY
# ═══════════════════════════════════════════════════════════

GCP Artifact Registry:
  Storage: $0.10/GB/month
    200 GB × $0.10 = $20/month

  Network Egress (within same region): FREE
  Network Egress (to internet): $0.12/GB
    Estimate: 500 GB/month × $0.12 = $60/month
  Network Egress (GCP internal, different region): $0.01/GB

  Vulnerability Scanning:
    First 1,000 scans/month: FREE
    Additional: $0.26/scan
    Our usage: 1,000 images = FREE!

  Total: $20 + $60 = $80/month

  Total (mostly internal GCP): $20/month

# ═══════════════════════════════════════════════════════════
# AZURE CONTAINER REGISTRY (ACR)
# ═══════════════════════════════════════════════════════════

Azure ACR (Standard):
  Registry: $20/month (per registry)
  Storage: $0.10/GB/month (after 100 GB included)
    200 GB - 100 GB = 100 GB
    100 GB × $0.10 = $10/month

  Data Transfer OUT (to internet): $0.087/GB
    500 GB × $0.087 = $43.50/month
  Data Transfer (within Azure): FREE

  Webhooks: 10 included

  Microsoft Defender (optional): ~$7/vCore/month
    Estimate: ~$50/month

  Total: $20 + $10 + $43.50 = $73.50/month
  Total (with Defender): $123.50/month

  Total (mostly internal Azure): $30/month

Azure ACR (Premium):
  Registry: $50/month
  Storage: $0.10/GB/month (after 500 GB)
  + Geo-replication (3 regions):
    Additional 2 regions × $50 = $100/month

  Total (geo-replicated): $150/month

# ═══════════════════════════════════════════════════════════
# HARBOR (SELF-HOSTED)
# ═══════════════════════════════════════════════════════════

Harbor on AWS EC2:
  EC2 Instance (t3.large): $60/month (2 vCPU, 8 GB)
  EBS Storage (200 GB): $20/month
  Data Transfer OUT: $0.09/GB × 500 GB = $45/month

  Total: $125/month

  + Maintenance time: ~5 hours/month × $50/hr = $250
  True Cost: $375/month

Harbor on DigitalOcean:
  Droplet (4 GB): $24/month
  Block Storage (200 GB): $20/month
  Bandwidth: 5 TB included (FREE!)

  Total: $44/month

  + Maintenance: $250
  True Cost: $294/month

Harbor on Kubernetes (EKS):
  EKS Cluster: $73/month (control plane)
  Worker Nodes (2× t3.large): $120/month
  EBS Storage: $20/month
  Load Balancer: $16/month

  Total: $229/month
  + Maintenance: $250
  True Cost: $479/month

# ═══════════════════════════════════════════════════════════
# QUAY.IO
# ═══════════════════════════════════════════════════════════

Quay.io Free:
  Cost: FREE
  Private Repos: 10 (generous!)
  Public Repos: Unlimited
  Storage: Unlimited (for free!)

  Limitation: Only 10 private repos

  Total: $0/month 🎉

Quay.io Paid:
  50 private repos: $12.50/month
  Unlimited private repos: $125/month

  Vulnerability scanning: Included!
  Robot accounts: Included!

# ═══════════════════════════════════════════════════════════
# GITLAB CONTAINER REGISTRY
# ═══════════════════════════════════════════════════════════

GitLab Free:
  Storage: 5 GB (FREE)
  Bandwidth: 10 GB/month

  Not sufficient for our scenario

GitLab Premium ($29/user/month):
  Subscription: $29 × 50 = $1,450/month
  Storage: 250 GB (included)
  Bandwidth: 500 GB/month (included)

  Total: $1,450/month

  ⚠️ Very expensive! (But includes full GitLab platform)

Self-Hosted GitLab:
  Free (CE) or $99/user/year (EE)

  Infrastructure: Similar to Harbor (~$300/month)

# ═══════════════════════════════════════════════════════════
# COST COMPARISON SUMMARY (Monthly)
# ═══════════════════════════════════════════════════════════

Scenario: 50 devs, 200 GB, 500 GB egress/month

┌──────────────────────────┬──────────────┬────────────────┐
│ Registry                 │ Cost/Month   │ Best For       │
├──────────────────────────┼──────────────┼────────────────┤
│ GHCR (public)            │ $0           │ 🏆 Open source │
│ Quay.io (free, 10 repos) │ $0           │ 🏆 Small teams │
│ ECR (internal AWS)       │ $30          │ 🏆 AWS users   │
│ GCP AR (internal GCP)    │ $20          │ 🏆 GCP users   │
│ Azure ACR (internal)     │ $30          │ 🏆 Azure users │
│ Harbor (DigitalOcean)    │ $44 + labor  │ Control        │
│ ECR (external traffic)   │ $75          │ AWS users      │
│ Azure ACR (external)     │ $74          │ Azure users    │
│ GCP AR (external)        │ $80          │ GCP users      │
│ Harbor (AWS)             │ $125 + labor │ Control        │
│ Docker Hub Pro           │ $250         │ Simplicity     │
│ Docker Hub Team          │ $350         │ Collaboration  │
│ GHCR (private)           │ $401         │ GitHub users   │
│ GitLab Premium           │ $1,450       │ Full platform  │
└──────────────────────────┴──────────────┴────────────────┘

# ═══════════════════════════════════════════════════════════
# WINNER BY SCENARIO
# ═══════════════════════════════════════════════════════════

Open Source Project:
  🏆 Winner: GHCR or Quay.io (FREE!)

Startup (10 devs, AWS):
  🏆 Winner: AWS ECR ($10/month)
  Runner-up: GHCR public ($0)

Scale-up (50 devs, Multi-cloud):
  🏆 Winner: GHCR ($50-100/month)
  Runner-up: Quay.io paid ($125)

Enterprise (AWS):
  🏆 Winner: AWS ECR ($30-100/month)

Enterprise (GCP):
  🏆 Winner: GCP Artifact Registry ($20-50/month)

Enterprise (Azure):
  🏆 Winner: Azure ACR ($30-150/month)

Enterprise (On-prem required):
  🏆 Winner: Harbor self-hosted ($300-500/month all-in)

# ═══════════════════════════════════════════════════════════
# COST OPTIMIZATION TIPS
# ═══════════════════════════════════════════════════════════

✅ Use cloud registry if already on that cloud (cheapest!)
✅ Keep pulls within same cloud (free egress!)
✅ Use lifecycle policies (delete old images = save 50-80%)
✅ Optimize image sizes (90% smaller = 90% less storage)
✅ Use public repos when possible (often free!)
✅ Consider pull-through cache (avoid rate limits + egress)
✅ Multi-region? Use geo-replication vs separate registries
✅ Small team? Quay.io free tier (10 private repos!)

❌ Don't pay per-user if you have large team (Docker Hub)
❌ Don't use expensive registry if simple needs (over-engineering)
❌ Don't ignore egress costs (can surprise you!)
❌ Don't forget maintenance costs for self-hosted

╔════════════════════════════════════════════════════════╗
║  💡 COST OPTIMIZATION EXAMPLE:                          ║
╠════════════════════════════════════════════════════════╣
║  Before: Docker Hub Team ($350/month)                  ║
║  After: ECR + lifecycle policies                       ║
║    Storage: $20/month (was unlimited but only used 200)║
║    Egress: $0 (within AWS)                             ║
║    Total: $20/month                                    ║
║                                                         ║
║  Savings: $330/month = $3,960/year! 💰                 ║
╚════════════════════════════════════════════════════════╝
```

---

<div align="center">

## 🚚 Migration Strategies

_Moving images between registries like a pro_ 📦

</div>

### Migration Planning

```
🎯 MIGRATION PHASES:

Phase 1: Assessment (Week 1)
  ☐ Inventory all images
  ☐ Identify dependencies
  ☐ Document current workflows
  ☐ Calculate costs (current vs target)
  ☐ Identify breaking changes

Phase 2: Setup Target Registry (Week 1-2)
  ☐ Create accounts/infrastructure
  ☐ Configure authentication
  ☐ Set up automation/CI/CD
  ☐ Test with sample images
  ☐ Configure policies (retention, security)

Phase 3: Pilot Migration (Week 2-3)
  ☐ Migrate 1-2 non-critical apps
  ☐ Update CI/CD pipelines
  ☐ Test deployment workflows
  ☐ Gather team feedback
  ☐ Document lessons learned

Phase 4: Bulk Migration (Week 3-6)
  ☐ Migrate in batches
  ☐ Parallel run (both registries)
  ☐ Update all references
  ☐ Monitor for issues

Phase 5: Cutover (Week 6-7)
  ☐ Final sync
  ☐ Switch all traffic to new registry
  ☐ Monitor closely (24-48 hours)
  ☐ Archive old registry (keep for 30 days)

Phase 6: Decommission (Week 8)
  ☐ Verify no traffic to old registry
  ☐ Export final backup
  ☐ Delete old registry
  ☐ Update documentation

═══════════════════════════════════════════════════════════

MIGRATION RISK ASSESSMENT:

Low Risk:
✅ Dev/test environments
✅ Internal tools
✅ Small team (<10 people)
✅ Few images (<50)

Medium Risk:
⚠️ Staging environments
⚠️ Medium team (10-50 people)
⚠️ Moderate image count (50-500)
⚠️ Some CI/CD automation

High Risk:
❌ Production environments
❌ Large team (50+ people)
❌ Many images (500+)
❌ Complex CI/CD pipelines
❌ Multiple regions/clusters
❌ External customers pulling images

Mitigation:
✅ Pilot with low-risk apps first
✅ Parallel run (both registries active)
✅ Gradual rollout
✅ Rollback plan ready
✅ Communication plan
```

---

### Migration Tools & Scripts

```bash
# ═══════════════════════════════════════════════════════════
# CRANE - GOOGLE'S CONTAINER IMAGE TOOL
# https://github.com/google/go-containerregistry/tree/main/cmd/crane
# ═══════════════════════════════════════════════════════════

# Installation
brew install crane

# OR
go install github.com/google/go-containerregistry/cmd/crane@latest

# Copy single image
crane copy \
  docker.io/myuser/myapp:v1.0.0 \
  ghcr.io/myuser/myapp:v1.0.0

# Copy all tags
crane copy \
  docker.io/myuser/myapp \
  ghcr.io/myuser/myapp \
  --all-tags

# Copy preserving digests (important!)
crane copy \
  docker.io/myuser/myapp:v1.0.0 \
  ghcr.io/myuser/myapp:v1.0.0 \
  --platform all  # Copy all architectures!

# ✅ Pros:
#   • Fast (no local pull/push)
#   • Preserves layers (efficient)
#   • Cross-registry copy
#   • Multi-arch support

# ═══════════════════════════════════════════════════════════
# SKOPEO - RED HAT'S IMAGE COPYING TOOL
# https://github.com/containers/skopeo
# ═══════════════════════════════════════════════════════════

# Installation
# macOS
brew install skopeo

# Linux (Ubuntu/Debian)
sudo apt-get install skopeo

# Copy image
skopeo copy \
  docker://docker.io/myuser/myapp:v1.0.0 \
  docker://ghcr.io/myuser/myapp:v1.0.0

# Copy with credentials
skopeo copy \
  --src-creds=user:pass \
  --dest-creds=user:token \
  docker://docker.io/myuser/myapp:v1.0.0 \
  docker://ghcr.io/myuser/myapp:v1.0.0

# Inspect image without pulling
skopeo inspect docker://docker.io/library/nginx:latest

# List tags
skopeo list-tags docker://docker.io/library/nginx

# ✅ Pros:
#   • No Docker daemon required!
#   • Works on any system
#   • Supports many registries
#   • Can inspect without pulling

# ═══════════════════════════════════════════════════════════
# REGCTL - REGCLIENT CLI TOOL
# https://github.com/regclient/regclient
# ═══════════════════════════════════════════════════════════

# Installation
curl -L https://github.com/regclient/regclient/releases/latest/download/regctl-linux-amd64 \
  -o regctl
chmod +x regctl
sudo mv regctl /usr/local/bin/

# Copy image
regctl image copy \
  docker.io/myuser/myapp:v1.0.0 \
  ghcr.io/myuser/myapp:v1.0.0

# Copy with all tags
regctl image copy \
  docker.io/myuser/myapp \
  ghcr.io/myuser/myapp \
  --digest-tags

# ═══════════════════════════════════════════════════════════
# MIGRATION SCRIPT - BATCH MIGRATION
# ═══════════════════════════════════════════════════════════

#!/bin/bash
# migrate-registry.sh

set -e

SOURCE_REGISTRY="docker.io/myuser"
TARGET_REGISTRY="ghcr.io/myuser"

# List of images to migrate
IMAGES=(
  "api-gateway"
  "auth-service"
  "user-service"
  "notification-service"
  "payment-service"
)

# Authenticate to registries
echo "Logging in to registries..."
echo $SOURCE_TOKEN | docker login docker.io -u $SOURCE_USER --password-stdin
echo $TARGET_TOKEN | docker login ghcr.io -u $TARGET_USER --password-stdin

# Migrate each image
for image in "${IMAGES[@]}"; do
  echo "=================================="
  echo "Migrating: $image"
  echo "=================================="

  # Get all tags for this image
  tags=$(crane ls ${SOURCE_REGISTRY}/${image})

  for tag in $tags; do
    echo "  Copying tag: $tag"

    # Copy image with crane (fast!)
    crane copy \
      ${SOURCE_REGISTRY}/${image}:${tag} \
      ${TARGET_REGISTRY}/${image}:${tag} \
      --platform all

    echo "  ✅ Copied: $tag"
  done

  echo "✅ Migrated: $image"
done

echo ""
echo "🎉 Migration complete!"
echo ""
echo "Next steps:"
echo "1. Verify images in target registry"
echo "2. Update CI/CD pipelines"
echo "3. Update Kubernetes manifests"
echo "4. Test deployments"

# ═══════════════════════════════════════════════════════════
# ADVANCED: PARALLEL MIGRATION WITH RETRIES
# ═══════════════════════════════════════════════════════════

#!/bin/bash
# parallel-migrate.sh

SOURCE="docker.io/myuser"
TARGET="ghcr.io/myuser"
MAX_RETRIES=3
PARALLEL_JOBS=5

# Function to migrate single image
migrate_image() {
  local image=$1
  local tag=$2
  local attempt=1

  while [ $attempt -le $MAX_RETRIES ]; do
    echo "Attempt $attempt: $image:$tag"

    if crane copy \
      ${SOURCE}/${image}:${tag} \
      ${TARGET}/${image}:${tag} \
      --platform all 2>&1 | tee /tmp/migrate-$$.log; then
      echo "✅ Success: $image:$tag"
      return 0
    fi

    echo "⚠️ Failed attempt $attempt for $image:$tag"
    attempt=$((attempt + 1))
    sleep 5
  done

  echo "❌ Failed after $MAX_RETRIES attempts: $image:$tag"
  return 1
}

export -f migrate_image
export SOURCE TARGET MAX_RETRIES

# Get all images and tags
echo "Discovering images..."
images=$(crane catalog $SOURCE)

# Migrate in parallel
echo "$images" | parallel -j $PARALLEL_JOBS migrate_image {} || true

echo "Migration complete! Check logs for failures."

# ═══════════════════════════════════════════════════════════
# DOCKER-BASED MIGRATION (Traditional)
# ═══════════════════════════════════════════════════════════

#!/bin/bash
# docker-migrate.sh
# Slower but works everywhere

SOURCE="docker.io/myuser/myapp"
TARGET="ghcr.io/myuser/myapp"

# Get all tags
tags=$(curl -s "https://registry.hub.docker.com/v2/repositories/myuser/myapp/tags?page_size=100" \
  | jq -r '.results[].name')

for tag in $tags; do
  echo "Migrating: $tag"

  # Pull from source
  docker pull ${SOURCE}:${tag}

  # Tag for target
  docker tag ${SOURCE}:${tag} ${TARGET}:${tag}

  # Push to target
  docker push ${TARGET}:${tag}

  # Clean up local image
  docker rmi ${SOURCE}:${tag} ${TARGET}:${tag}

  echo "✅ Migrated: $tag"
done

# ⚠️ Warning: This pulls images locally (slow + uses disk space!)
# Use crane/skopeo for production migrations

# ═══════════════════════════════════════════════════════════
# VERIFICATION SCRIPT
# ═══════════════════════════════════════════════════════════

#!/bin/bash
# verify-migration.sh

SOURCE="docker.io/myuser"
TARGET="ghcr.io/myuser"
IMAGES=("api-gateway" "auth-service" "user-service")

echo "Verifying migration..."
echo ""

for image in "${IMAGES[@]}"; do
  echo "Image: $image"

  # Get tags from source
  source_tags=$(crane ls ${SOURCE}/${image} | sort)

  # Get tags from target
  target_tags=$(crane ls ${TARGET}/${image} | sort)

  # Compare
  if [ "$source_tags" == "$target_tags" ]; then
    echo "  ✅ All tags present"
  else
    echo "  ❌ Tags mismatch!"
    echo "  Missing tags:"
    comm -23 <(echo "$source_tags") <(echo "$target_tags")
  fi

  # Compare digests
  for tag in $source_tags; do
    source_digest=$(crane digest ${SOURCE}/${image}:${tag})
    target_digest=$(crane digest ${TARGET}/${image}:${tag})

    if [ "$source_digest" == "$target_digest" ]; then
      echo "  ✅ $tag: digests match"
    else
      echo "  ❌ $tag: digest mismatch!"
      echo "    Source: $source_digest"
      echo "    Target: $target_digest"
    fi
  done

  echo ""
done

echo "Verification complete!"
```

---

### Registry-Specific Migration Guides

```yaml
# ═══════════════════════════════════════════════════════════
# DOCKER HUB → GITHUB CONTAINER REGISTRY (GHCR)
# ═══════════════════════════════════════════════════════════

Step 1: Setup GHCR
  # Generate GitHub Personal Access Token
  # https://github.com/settings/tokens
  # Scopes: write:packages, read:packages, delete:packages

  export GITHUB_TOKEN="ghp_xxxxx"
  echo $GITHUB_TOKEN | docker login ghcr.io -u your-username --password-stdin

Step 2: Migrate Images
  # Using crane (recommended)
  for tag in v1.0.0 v1.1.0 latest; do
    crane copy \
      docker.io/your-username/myapp:$tag \
      ghcr.io/your-username/myapp:$tag
  done

Step 3: Update GitHub Actions
  # Before:
  - name: Push to Docker Hub
    uses: docker/login-action@v3
    with:
      username: ${{ secrets.DOCKERHUB_USERNAME }}
      password: ${{ secrets.DOCKERHUB_TOKEN }}

  # After:
  - name: Push to GHCR
    uses: docker/login-action@v3
    with:
      registry: ghcr.io
      username: ${{ github.actor }}
      password: ${{ secrets.GITHUB_TOKEN }}  # Automatic!

Step 4: Update Kubernetes
  # Before:
  image: docker.io/your-username/myapp:v1.0.0

  # After:
  image: ghcr.io/your-username/myapp:v1.0.0

Step 5: Update Pull Secrets
  kubectl create secret docker-registry ghcr-secret \
    --docker-server=ghcr.io \
    --docker-username=your-username \
    --docker-password=$GITHUB_TOKEN

Benefits:
  ✅ FREE for public images (unlimited!)
  ✅ No rate limits
  ✅ Native GitHub integration
  ✅ Simpler CI/CD

# ═══════════════════════════════════════════════════════════
# DOCKER HUB → AWS ECR
# ═══════════════════════════════════════════════════════════

Step 1: Create ECR Repositories
  for repo in api-gateway auth-service user-service; do
    aws ecr create-repository --repository-name $repo
  done

Step 2: Authenticate
  aws ecr get-login-password --region us-east-1 | \
    docker login --username AWS --password-stdin \
    123456789012.dkr.ecr.us-east-1.amazonaws.com

Step 3: Migrate
  crane copy \
    docker.io/myuser/myapp:v1.0.0 \
    123456789012.dkr.ecr.us-east-1.amazonaws.com/myapp:v1.0.0

Step 4: Configure Lifecycle Policies
  aws ecr put-lifecycle-policy \
    --repository-name myapp \
    --lifecycle-policy-text file://lifecycle-policy.json

Step 5: Enable Scanning
  aws ecr put-image-scanning-configuration \
    --repository-name myapp \
    --image-scanning-configuration scanOnPush=true

Benefits:
  ✅ Native AWS integration
  ✅ IAM authentication
  ✅ No egress costs within AWS
  ✅ Enhanced scanning

# ═══════════════════════════════════════════════════════════
# GCR → ARTIFACT REGISTRY (GCP UPGRADE)
# ═══════════════════════════════════════════════════════════

Why Migrate?
  • GCR (gcr.io) is legacy
  • Artifact Registry is the future (better features)
  • GCR will be deprecated

Step 1: Create Artifact Registry Repository
  gcloud artifacts repositories create myrepo \
    --repository-format=docker \
    --location=us-central1

Step 2: Migrate Images
  # List GCR images
  gcloud container images list --repository=gcr.io/my-project

  # Copy to Artifact Registry
  for image in $(gcloud container images list --repository=gcr.io/my-project --format="value(name)"); do
    for tag in $(gcloud container images list-tags $image --format="value(tags)"); do
      crane copy \
        $image:$tag \
        us-central1-docker.pkg.dev/my-project/myrepo/$(basename $image):$tag
    done
  done

Step 3: Update GKE Clusters
  # Before:
  image: gcr.io/my-project/myapp:v1.0.0

  # After:
  image: us-central1-docker.pkg.dev/my-project/myrepo/myapp:v1.0.0

Step 4: Update CI/CD
  # Cloud Build
  images:
    - 'us-central1-docker.pkg.dev/my-project/myrepo/myapp:$COMMIT_SHA'

# ═══════════════════════════════════════════════════════════
# SELF-HOSTED HARBOR → CLOUD REGISTRY
# ═══════════════════════════════════════════════════════════

Scenario: Moving from on-prem Harbor to cloud

Step 1: Export Harbor Projects
  # Get list of all repositories
  curl -u admin:password \
    https://harbor.mycompany.com/api/v2.0/projects | jq

Step 2: Migrate with Harbor Replication
  # UI: Administration → Replications → New Replication Rule

  Source: Local Harbor
  Destination: Target Registry (ECR/GHCR/GCR)
  Trigger: Manual / Scheduled

  # Or API:
  curl -X POST \
    -H "Content-Type: application/json" \
    -u admin:password \
    https://harbor.mycompany.com/api/v2.0/replication/executions \
    -d '{
      "policy_id": 1
    }'

Step 3: Verify Migration
  # Compare image counts
  harbor_count=$(curl -s https://harbor.mycompany.com/api/v2.0/repositories | jq 'length')
  target_count=$(crane catalog ghcr.io/myuser | wc -l)

  echo "Harbor: $harbor_count repositories"
  echo "Target: $target_count repositories"

Step 4: Update All References
  # Find all Kubernetes manifests
  find . -name "*.yaml" -type f -exec \
    sed -i 's|harbor.mycompany.com|ghcr.io/myuser|g' {} \;

Step 5: Parallel Run
  # Keep Harbor running for 30 days
  # Monitor usage
  # Decommission when zero pulls for 7 days

# ═══════════════════════════════════════════════════════════
# MIGRATION TIMELINE EXAMPLES
# ═══════════════════════════════════════════════════════════

Small Team (10 devs, 50 images):
  Week 1: Planning + Setup
  Week 2: Migration + Testing
  Week 3: Cutover
  Total: 3 weeks

Medium Team (50 devs, 500 images):
  Week 1-2: Planning + Setup
  Week 3-4: Pilot Migration
  Week 5-7: Bulk Migration
  Week 8: Cutover + Monitoring
  Total: 8 weeks

Large Enterprise (500+ devs, 5000+ images):
  Month 1: Planning + Setup
  Month 2-3: Pilot Migration
  Month 4-6: Phased Migration
  Month 7: Cutover
  Month 8: Decommission
  Total: 8 months

╔════════════════════════════════════════════════════════╗
║  💡 MIGRATION PRO TIPS:                                 ║
╠════════════════════════════════════════════════════════╣
║  • Use crane/skopeo (10x faster than docker pull/push)║
║  • Verify digests after migration                      ║
║  • Keep old registry running during transition         ║
║  • Update CI/CD pipelines first (dev env)              ║
║  • Test thoroughly before production cutover           ║
║  • Document all changes (wiki, runbook)                ║
║  • Communicate early and often                         ║
║  • Have rollback plan ready                            ║
║  • Monitor both registries during transition           ║
║  • Archive old registry (don't delete immediately!)    ║
╚════════════════════════════════════════════════════════╝
```

---

<div align="center">

## 💡 Best Practices

_Learn from the pros_ 🎓

</div>

### Tagging Strategy

```yaml
# ═══════════════════════════════════════════════════════════
# IMAGE TAGGING BEST PRACTICES
# ═══════════════════════════════════════════════════════════

❌ BAD TAGGING PRACTICES:

  # Using only 'latest'
  docker push myapp:latest

  Problems:
    • Can't rollback (which version was latest?)
    • Not reproducible
    • Breaks in production randomly
    • No audit trail

  # Using date-based tags
  docker push myapp:2025-01-15

  Problems:
    • Not semantic
    • Hard to know what changed
    • Can't tell breaking changes

  # Using random strings
  docker push myapp:abc123xyz

  Problems:
    • No meaning
    • Hard to identify versions

═══════════════════════════════════════════════════════════

✅ GOOD TAGGING STRATEGIES:

Strategy 1: Semantic Versioning (BEST for releases)
  Format: vMAJOR.MINOR.PATCH

  Examples:
    • v1.0.0 (initial release)
    • v1.0.1 (bug fix)
    • v1.1.0 (new feature, backward compatible)
    • v2.0.0 (breaking changes)

  Usage:
    # Tag with version
    docker tag myapp:latest myapp:v1.2.3
    docker push myapp:v1.2.3

    # Also tag major/minor (mutable)
    docker tag myapp:v1.2.3 myapp:v1.2
    docker tag myapp:v1.2.3 myapp:v1
    docker push myapp:v1.2
    docker push myapp:v1

  Kubernetes:
    # Production (immutable tag!)
    image: myapp:v1.2.3

    # Staging (gets latest v1.2.x)
    image: myapp:v1.2

    # Dev (gets latest v1.x.x)
    image: myapp:v1

Strategy 2: Git Commit SHA (BEST for CI/CD)
  Format: SHA or branch-SHA

  Examples:
    • abc1234 (short SHA)
    • main-abc1234 (branch + SHA)
    • pr-42-abc1234 (PR + SHA)

  GitHub Actions:
    - name: Build and push
      uses: docker/build-push-action@v5
      with:
        tags: |
          myapp:${{ github.sha }}
          myapp:${{ github.ref_name }}-${{ github.sha }}

  Benefits:
    ✅ Exact code version
    ✅ Traceable to commit
    ✅ Unique (no collisions)
    ✅ Immutable

Strategy 3: Hybrid Approach (RECOMMENDED!)
  Combine semantic version + SHA + environment

  Examples:
    Production:
      • myapp:v1.2.3
      • myapp:v1.2.3-abc1234
      • myapp:prod-v1.2.3

    Staging:
      • myapp:staging-v1.2.3
      • myapp:staging-latest

    Development:
      • myapp:dev-abc1234
      • myapp:dev-latest
      • myapp:feature-auth-abc1234

  CI/CD Tagging:
    # .github/workflows/docker.yml
    - name: Docker metadata
      id: meta
      uses: docker/metadata-action@v5
      with:
        images: ghcr.io/${{ github.repository }}
        tags: |
          # Semantic version tags
          type=semver,pattern={{version}}
          type=semver,pattern={{major}}.{{minor}}
          type=semver,pattern={{major}}

          # Branch name
          type=ref,event=branch

          # PR number
          type=ref,event=pr

          # Git SHA
          type=sha,prefix={{branch}}-

          # Latest (only on main)
          type=raw,value=latest,enable={{is_default_branch}}

Strategy 4: Metadata Labels (Additional context)
  Use LABEL in Dockerfile:

  FROM node:20-alpine

  LABEL org.opencontainers.image.title="My App"
  LABEL org.opencontainers.image.description="API service"
  LABEL org.opencontainers.image.version="1.2.3"
  LABEL org.opencontainers.image.source="https://github.com/user/repo"
  LABEL org.opencontainers.image.revision="abc1234"
  LABEL org.opencontainers.image.created="2025-01-15T10:30:00Z"
  LABEL org.opencontainers.image.authors="team@company.com"

  # Query labels
  docker inspect myapp:v1.2.3 | jq '.[0].Config.Labels'

═══════════════════════════════════════════════════════════

TAG NAMING CONVENTIONS:

Format: registry/namespace/repository:tag

Examples:
  # Public Docker Hub
  docker.io/library/nginx:1.25-alpine

  # User on Docker Hub
  docker.io/mrdib/myapp:v1.2.3

  # GHCR
  ghcr.io/mrdib/myapp:v1.2.3

  # ECR
  123456789012.dkr.ecr.us-east-1.amazonaws.com/myapp:v1.2.3

  # Harbor
  harbor.mycompany.com/production/myapp:v1.2.3

Tag Patterns:
  Releases:
    ✅ v1.2.3
    ✅ 1.2.3
    ✅ v1.2.3-alpine
    ✅ v1.2.3-slim

  Environments:
    ✅ prod-v1.2.3
    ✅ staging-abc1234
    ✅ dev-latest

  Branches:
    ✅ main-abc1234
    ✅ develop-xyz5678
    ✅ feature-auth-abc1234

  Pull Requests:
    ✅ pr-42
    ✅ pr-42-abc1234

═══════════════════════════════════════════════════════════

TAG IMMUTABILITY:

Immutable Tags (NEVER change):
  ✅ v1.2.3 (semantic versions)
  ✅ abc1234 (git SHAs)
  ✅ v1.2.3-abc1234 (version + SHA)

  Enforced by:
    • AWS ECR: Image tag mutability setting
    • Harbor: Tag immutability rules
    • Registry policies

Mutable Tags (CAN change):
  ⚠️ latest
  ⚠️ dev
  ⚠️ staging
  ⚠️ v1 (major version only)
  ⚠️ v1.2 (major.minor only)

  Use for:
    • Development/testing
    • Rolling updates
    • Feature branches

Production Rule:
  🎯 ALWAYS use immutable tags in production!

  # ❌ BAD
  image: myapp:latest

  # ✅ GOOD
  image: myapp:v1.2.3

  # ✅ EVEN BETTER
  image: myapp:v1.2.3@sha256:abc123...  # Digest pinning!

╔════════════════════════════════════════════════════════╗
║  💡 TAGGING STRATEGY CHECKLIST:                         ║
╠════════════════════════════════════════════════════════╣
║  ☐ Use semantic versioning for releases               ║
║  ☐ Include Git SHA for traceability                   ║
║  ☐ Tag with multiple aliases (v1, v1.2, v1.2.3)       ║
║  ☐ Use immutable tags in production                   ║
║  ☐ Add metadata labels to images                      ║
║  ☐ Include environment in tag (prod-, staging-)       ║
║  ☐ Document tagging strategy in README                ║
║  ☐ Automate tagging in CI/CD                          ║
║  ☐ Never reuse tags (especially versions!)            ║
║  ☐ Keep 'latest' but don't rely on it                 ║
╚════════════════════════════════════════════════════════╝
```

---

### Security Best Practices

```yaml
# ═══════════════════════════════════════════════════════════
# SECURITY BEST PRACTICES
# ═══════════════════════════════════════════════════════════

1. Never Store Secrets in Images

   ❌ WRONG:
   Dockerfile:
     ENV DATABASE_PASSWORD="supersecret"
     ENV API_KEY="sk-1234567890"

   ✅ RIGHT:
   Dockerfile:
     # No secrets!

   Kubernetes:
     env:
       - name: DATABASE_PASSWORD
         valueFrom:
           secretKeyRef:
             name: db-secret
             key: password

2. Scan Images for Vulnerabilities

   ✅ In CI/CD:
     # GitHub Actions
     - name: Run Trivy
       uses: aquasecurity/trivy-action@master
       with:
         image-ref: ${{ env.IMAGE }}
         exit-code: '1'  # Fail on HIGH/CRITICAL

   ✅ In Registry:
     • Enable ECR scanning
     • Harbor with Trivy
     • GCR vulnerability scanning

   ✅ In Kubernetes:
     • Admission controllers (OPA, Kyverno)
     • Only allow signed images
     • Block images with vulnerabilities

3. Use Minimal Base Images

   Size Matters (for security too!):

   FROM ubuntu:22.04        # 77 MB, 100+ packages
   FROM alpine:3.19         # 7 MB, 15 packages
   FROM distroless/static   # 2 MB, 0 packages!

   Fewer packages = fewer vulnerabilities!

   ✅ Recommendations:
     • Alpine for most apps
     • Distroless for Go/Java
     • Scratch for static binaries

4. Run as Non-Root User

   ❌ WRONG:
   FROM node:20-alpine
   COPY . /app
   CMD ["node", "server.js"]
   # Runs as root! (uid 0)

   ✅ RIGHT:
   FROM node:20-alpine

   # Create non-root user
   RUN addgroup -g 1001 -S nodejs && \
       adduser -S nodejs -u 1001

   WORKDIR /app
   COPY --chown=nodejs:nodejs . .

   # Switch to non-root
   USER nodejs

   CMD ["node", "server.js"]
   # Now runs as nodejs (uid 1001)

   Kubernetes:
     securityContext:
       runAsNonRoot: true
       runAsUser: 1001
       readOnlyRootFilesystem: true

5. Sign Images

   ✅ Use Cosign:
     # Sign in CI/CD
     cosign sign --yes $IMAGE_TAG

   ✅ Verify in Kubernetes:
     # Kyverno policy
     apiVersion: kyverno.io/v1
     kind: ClusterPolicy
     metadata:
       name: verify-images
     spec:
       validationFailureAction: Enforce
       rules:
         - name: verify-signature
           match:
             any:
             - resources:
                 kinds:
                   - Pod
           verifyImages:
           - imageReferences:
             - "ghcr.io/mrdib/*"
             attestors:
             - entries:
               - keyless:
                   subject: "https://github.com/mrdib/*"

6. Use Private Registries for Internal Apps

   ✅ Keep internal apps private!
   ✅ Use authentication
   ✅ Network isolation (VPC endpoints)
   ✅ IP whitelisting if possible

7. Implement Least Privilege Access

   Team Access:
   ├─ Developers: Pull + Push (dev tags only)
   ├─ CI/CD: Pull + Push (all tags)
   ├─ Production Cluster: Pull only
   └─ Admins: Full access

   AWS ECR IAM Policy (Production Pull Only):
     {
       "Version": "2012-10-17",
       "Statement": [
         {
           "Effect": "Allow",
           "Action": [
             "ecr:GetDownloadUrlForLayer",
             "ecr:BatchGetImage",
             "ecr:BatchCheckLayerAvailability"
           ],
           "Resource": "arn:aws:ecr:us-east-1:123456789012:repository/*",
           "Condition": {
             "StringLike": {
               "ecr:ResourceTag/environment": "production"
             }
           }
         }
       ]
     }

8. Enable Registry Audit Logs

   ✅ Track all operations:
     • Who pulled which image?
     • Who pushed what?
     • Authentication attempts
     • Permission changes

   AWS ECR:
     # CloudTrail automatically logs ECR API calls

   Harbor:
     # UI: Administration → Audit Log

   GHCR:
     # GitHub audit log (Enterprise only)

9. Implement Image Retention Policies

   ✅ Delete old images:
     • Reduce attack surface
     • Save costs
     • Compliance

   Example Policy:
     • Keep all images < 30 days
     • Keep last 10 versions
     • Keep all prod tags
     • Delete untagged after 7 days

10. Use Content Trust / Notary

    ✅ Docker Content Trust:
      export DOCKER_CONTENT_TRUST=1
      docker push myapp:v1.0.0  # Signed automatically

    ✅ Cosign (recommended):
      cosign sign myapp:v1.0.0

═══════════════════════════════════════════════════════════

SECURITY CHECKLIST:

Build Time:
  ☐ Scan Dockerfile with hadolint
  ☐ Use minimal base images
  ☐ Don't include secrets in image
  ☐ Run as non-root user
  ☐ Use multi-stage builds
  ☐ Pin package versions
  ☐ Add security labels

Push Time:
  ☐ Scan with Trivy/Snyk
  ☐ Sign with Cosign
  ☐ Tag properly (semantic versioning)
  ☐ Generate SBOM
  ☐ Push to private registry

Deploy Time:
  ☐ Verify signatures
  ☐ Pull from trusted registry
  ☐ Use image digests
  ☐ Apply security context
  ☐ Enable network policies
  ☐ Use secrets management

Runtime:
  ☐ Monitor for vulnerabilities
  ☐ Scan running containers
  ☐ Rotate images regularly
  ☐ Review audit logs
  ☐ Update base images
```

---

### Performance Best Practices

```yaml
# ═══════════════════════════════════════════════════════════
# PERFORMANCE OPTIMIZATION
# ═══════════════════════════════════════════════════════════

1. Use Image Layer Caching

   ✅ Order Dockerfile for maximum cache hits:

   FROM node:20-alpine
   WORKDIR /app

   # 1. Dependencies first (change rarely)
   COPY package*.json ./
   RUN npm ci  # Cached unless package.json changes!

   # 2. Code last (changes often)
   COPY . .

   Result: 5-minute builds become 10 seconds!

2. Use BuildKit Cache Mounts

   # Enable BuildKit
   export DOCKER_BUILDKIT=1

   # Use cache mounts
   RUN --mount=type=cache,target=/root/.npm \
       npm ci

   # npm cache persists between builds!

3. Multi-Stage Builds

   Reduce image size by 90%:

   # Build stage (discarded)
   FROM node:20 AS builder
   WORKDIR /app
   COPY . .
   RUN npm run build

   # Final stage (small!)
   FROM node:20-alpine
   COPY --from=builder /app/dist ./dist
   CMD ["node", "dist/server.js"]

4. Use .dockerignore

   # .dockerignore
   node_modules
   .git
   .env
   *.md
   tests

   Faster builds + smaller context!

5. Parallel Builds in CI/CD

   # GitHub Actions - Build multiple platforms
   - uses: docker/build-push-action@v5
     with:
       platforms: linux/amd64,linux/arm64
       # Builds in parallel!

6. Use Registry Caching

   # Pull through cache (Harbor, Artifact Registry)
   docker pull harbor.mycompany.com/dockerhub/nginx:latest

   # First pull: slow (from Docker Hub)
   # Next pulls: INSTANT (from cache!)

7. Compress Layers

   # Combine commands to reduce layers
   RUN apt-get update && \
       apt-get install -y curl && \
       apt-get clean && \
       rm -rf /var/lib/apt/lists/*

   # Single layer instead of 4!

8. Use Multi-Arch Images

   docker buildx build \
     --platform linux/amd64,linux/arm64 \
     -t myapp:latest \
     --push .

   # Works on Intel AND ARM (M1/M2 Macs, AWS Graviton)

9. Optimize Image Pulls

   # Use digests for immutability & caching
   image: myapp@sha256:abc123...

   # Kubernetes caches by digest
   # Same digest = no pull needed!

10. Load Balance Registry Traffic

    # Use geo-replicated registries
    AWS ECR Replication:
      us-east-1 (primary)
      us-west-2 (replica)
      eu-west-1 (replica)

    # Kubernetes pulls from nearest region (faster!)

╔════════════════════════════════════════════════════════╗
║  💡 PERFORMANCE TIPS:                                   ║
╠════════════════════════════════════════════════════════╣
║  • Layer caching = 10x faster builds                   ║
║  • Multi-stage = 90% smaller images                    ║
║  • .dockerignore = faster builds                       ║
║  • BuildKit cache mounts = persistent caching          ║
║  • Pull-through cache = instant pulls                  ║
║  • Multi-arch = works everywhere                       ║
║  • Digest pinning = better caching in K8s              ║
║  • Geo-replication = lower latency                     ║
╚════════════════════════════════════════════════════════╝
```

---

<div align="center">

## 🐛 Troubleshooting

_Common issues and solutions_ 🔧

</div>

### Common Problems & Solutions

```yaml
# ═══════════════════════════════════════════════════════════
# AUTHENTICATION ISSUES
# ═══════════════════════════════════════════════════════════

Problem: "unauthorized: authentication required"

Solutions:
  1. Login to registry:
     docker login ghcr.io -u username

  2. Check credentials:
     cat ~/.docker/config.json

  3. Use correct token (not password!):
     echo $TOKEN | docker login ghcr.io -u username --password-stdin

  4. Check token permissions:
     # GitHub: write:packages, read:packages
     # Docker Hub: Read & Write

  5. Token expired?
     # AWS ECR tokens expire in 12 hours
     # Re-authenticate:
     aws ecr get-login-password | docker login ...

# ═══════════════════════════════════════════════════════════
# RATE LIMITING
# ═══════════════════════════════════════════════════════════

Problem: "You have reached your pull rate limit"

Docker Hub Rate Limits:
  • Anonymous: 100 pulls / 6 hours
  • Free account: 200 pulls / 6 hours
  • Pro: 5,000 pulls / day
  • Team: 5,000 pulls / day (per user)

Solutions:
  1. Authenticate (5,000 pulls/day):
     docker login

  2. Use pull-through cache:
     # Harbor proxy cache
     docker pull harbor.mycompany.com/dockerhub/nginx:latest

  3. Mirror images to your registry:
     crane copy docker.io/nginx:latest ghcr.io/myuser/nginx:latest

  4. Upgrade to Docker Hub Pro ($5/month):
     Unlimited pulls!

  5. Use alternative registries:
     • GHCR (no rate limits for public!)
     • Quay.io (no rate limits!)

# ═══════════════════════════════════════════════════════════
# PUSH/PULL ERRORS
# ═══════════════════════════════════════════════════════════

Problem: "denied: requested access to the resource is denied"

Causes & Solutions:
  1. Not logged in:
     docker login registry.example.com

  2. Wrong registry URL:
     # ❌ Wrong
     docker push myapp:latest

     # ✅ Correct
     docker push ghcr.io/username/myapp:latest

  3. No permission:
     # Check IAM policies (AWS ECR)
     # Check robot account permissions (Harbor)
     # Check token scopes (GHCR)

  4. Repository doesn't exist:
     # Create repository first
     aws ecr create-repository --repository-name myapp

Problem: "manifest unknown: manifest unknown"

Causes:
  • Image doesn't exist
  • Wrong tag
  • Typo in image name

Solution:
  # List available tags
  crane ls ghcr.io/username/myapp

Problem: "Error response from daemon: Get https://registry.example.com: x509: certificate signed by unknown authority"

Solutions:
  1. Add registry to insecure registries (NOT RECOMMENDED!):
     # /etc/docker/daemon.json
     {
       "insecure-registries": ["registry.example.com:5000"]
     }

  2. Add CA certificate (RECOMMENDED):
     sudo cp ca.crt /etc/docker/certs.d/registry.example.com/ca.crt

  3. Use valid TLS certificate:
     # Let's Encrypt, etc.

# ═══════════════════════════════════════════════════════════
# STORAGE ISSUES
# ═══════════════════════════════════════════════════════════

Problem: "no space left on device"

Solutions:
  1. Clean up Docker:
     # Remove unused images
     docker image prune -a

     # Remove unused volumes
     docker volume prune

     # Remove everything unused
     docker system prune -a --volumes

  2. Check disk usage:
     docker system df

  3. Increase disk size:
     # Docker Desktop: Settings → Resources → Disk

     # Linux: Expand volume
     sudo lvextend -L +50G /dev/mapper/docker-vg

  4. Use registry lifecycle policies:
     # Delete old images automatically

Problem: "failed to register layer: ApplyLayer exit status 1"

Solutions:
  1. Increase Docker daemon storage:
     # /etc/docker/daemon.json
     {
       "storage-driver": "overlay2",
       "storage-opts": [
         "overlay2.size=50G"
       ]
     }

  2. Clean up:
     docker system prune -a

# ═══════════════════════════════════════════════════════════
# NETWORK ISSUES
# ═══════════════════════════════════════════════════════════

Problem: "dial tcp: lookup registry.example.com: no such host"

Solutions:
  1. Check DNS:
     nslookup registry.example.com
     dig registry.example.com

  2. Check /etc/hosts:
     # Add entry if needed
     192.168.1.100 registry.example.com

  3. Check firewall:
     # Allow port 443
     sudo ufw allow 443/tcp

Problem: "i/o timeout" or "connection timeout"

Solutions:
  1. Check network:
     ping registry.example.com
     telnet registry.example.com 443

  2. Increase timeout:
     # /etc/docker/daemon.json
     {
       "max-concurrent-downloads": 3,
       "max-concurrent-uploads": 3
     }

  3. Check proxy settings:
     export HTTP_PROXY=http://proxy.example.com:8080
     export HTTPS_PROXY=http://proxy.example.com:8080

# ═══════════════════════════════════════════════════════════
# CI/CD ISSUES
# ═══════════════════════════════════════════════════════════

Problem: GitHub Actions - "buildx failed with: ERROR: failed to solve"

Solutions:
  1. Check Dockerfile syntax:
     docker build --no-cache .

  2. Check context:
     # Add .dockerignore
     node_modules
     .git

  3. Enable BuildKit:
     - name: Build
       env:
         DOCKER_BUILDKIT: 1
       run: docker build .

Problem: "Error: Cannot perform an interactive login from a non TTY device"

Solution:
  # Use --password-stdin
  echo $TOKEN | docker login --username user --password-stdin

# ═══════════════════════════════════════════════════════════
# IMAGE CORRUPTION
# ═══════════════════════════════════════════════════════════

Problem: "image is corrupted" or "invalid tar header"

Solutions:
  1. Re-pull image:
     docker rmi myapp:latest
     docker pull myapp:latest

  2. Verify digest:
     crane digest myapp:latest

  3. Check registry health:
     # Harbor: Administration → Health Check
     # ECR: AWS Console → Health

  4. Re-push image:
     docker push myapp:latest

# ═══════════════════════════════════════════════════════════
# HARBOR-SPECIFIC ISSUES
# ═══════════════════════════════════════════════════════════

Problem: Harbor - "Project quota exceeded"

Solution:
  # UI: Projects → Configuration → Resource Quota
  # Increase or remove quota

Problem: Harbor - Scanning fails

Solutions:
  1. Check scanner health:
     # Administration → Interrogation Services

  2. Restart Trivy:
     docker restart harbor-trivy

  3. Update scanner:
     docker-compose pull trivy
     docker-compose up -d

# ═══════════════════════════════════════════════════════════
# DEBUGGING COMMANDS
# ═══════════════════════════════════════════════════════════

# Check Docker daemon
sudo systemctl status docker
docker info

# Check registry connectivity
curl -v https://registry.example.com/v2/

# Check authentication
curl -u user:token https://registry.example.com/v2/_catalog

# List images
crane catalog registry.example.com

# Inspect image without pulling
skopeo inspect docker://registry.example.com/myapp:latest

# View image manifest
crane manifest registry.example.com/myapp:latest

# Check image digest
crane digest registry.example.com/myapp:latest

# Test push
docker tag hello-world registry.example.com/test:latest
docker push registry.example.com/test:latest

# Check logs
docker logs <container-id>
journalctl -u docker

╔════════════════════════════════════════════════════════╗
║  💡 TROUBLESHOOTING TIPS:                               ║
╠════════════════════════════════════════════════════════╣
║  • Check authentication first (most common issue!)     ║
║  • Use 'docker info' to see registry config            ║
║  • Test with curl before Docker                        ║
║  • Check logs (docker logs, journalctl)                ║
║  • Verify network connectivity (ping, telnet)          ║
║  • Clean up regularly (docker system prune)            ║
║  • Use crane/skopeo for debugging                      ║
║  • Check rate limits (Docker Hub!)                     ║
║  • Verify image digests for integrity                  ║
║  • Enable debug logging when needed                    ║
╚════════════════════════════════════════════════════════╝
```

---

<div align="center">

## 🎉 Conclusion

_You're now a Container Registry expert!_ 🏆

</div>

### Quick Reference

```yaml
# ═══════════════════════════════════════════════════════════
# CHEAT SHEET
# ═══════════════════════════════════════════════════════════

Essential Commands:
  # Login
  docker login ghcr.io -u username
  echo $TOKEN | docker login --username user --password-stdin

  # Tag
  docker tag myapp:latest ghcr.io/user/myapp:v1.0.0

  # Push
  docker push ghcr.io/user/myapp:v1.0.0

  # Pull
  docker pull ghcr.io/user/myapp:v1.0.0

  # Scan
  trivy image ghcr.io/user/myapp:v1.0.0

  # Sign
  cosign sign --yes ghcr.io/user/myapp:v1.0.0

  # Copy
  crane copy source/image:tag target/image:tag

  # List tags
  crane ls ghcr.io/user/myapp

  # Inspect
  crane manifest ghcr.io/user/myapp:v1.0.0

Crane (recommended for registry operations):
  crane copy         # Copy images
  crane ls           # List tags
  crane manifest     # View manifest
  crane digest       # Get digest
  crane delete       # Delete image
  crane catalog      # List repositories

Cosign (image signing):
  cosign generate-key-pair  # Generate keys
  cosign sign              # Sign image
  cosign verify            # Verify signature
  cosign sign --yes        # Keyless signing

Trivy (vulnerability scanning):
  trivy image              # Scan image
  trivy fs                 # Scan filesystem
  trivy config             # Scan IaC
  trivy k8s                # Scan Kubernetes

═══════════════════════════════════════════════════════════

Registry Selection Guide:

Open Source Project:
  🏆 GHCR (free, no rate limits)

Startup (AWS):
  🏆 ECR (cheap, native integration)

Startup (GCP):
  🏆 Artifact Registry (good value)

Startup (Multi-cloud):
  🏆 GHCR (free/cheap, portable)

Enterprise (AWS):
  🏆 ECR (native, secure)

Enterprise (GCP):
  🏆 Artifact Registry (modern)

Enterprise (Azure):
  🏆 ACR (native, hybrid)

Enterprise (On-prem):
  🏆 Harbor (full-featured, free)

Small Team (<10):
  🏆 Quay.io free (10 private repos!)

═══════════════════════════════════════════════════════════

Key Takeaways:

✅ Use semantic versioning (v1.2.3)
✅ Scan images for vulnerabilities
✅ Sign images with Cosign
✅ Multi-stage builds (90% smaller!)
✅ Use .dockerignore
✅ Run as non-root user
✅ Never commit secrets
✅ Implement lifecycle policies
✅ Use immutable tags in production
✅ Authenticate to avoid rate limits

❌ Don't use 'latest' in production
❌ Don't store secrets in images
❌ Don't run as root
❌ Don't ignore vulnerabilities
❌ Don't skip image signing
❌ Don't use huge base images
❌ Don't forget .dockerignore
❌ Don't reuse version tags
❌ Don't skip lifecycle policies
❌ Don't ignore costs
```

---

### Resources & Links

```yaml
# ═══════════════════════════════════════════════════════════
# OFFICIAL DOCUMENTATION
# ═══════════════════════════════════════════════════════════

Docker Hub:
  • https://hub.docker.com
  • Docs: https://docs.docker.com/docker-hub/

GitHub Container Registry:
  • https://ghcr.io
  • Docs: https://docs.github.com/packages

AWS ECR:
  • https://aws.amazon.com/ecr/
  • Docs: https://docs.aws.amazon.com/ecr/

GCP Artifact Registry:
  • https://cloud.google.com/artifact-registry
  • Docs: https://cloud.google.com/artifact-registry/docs

Azure ACR:
  • https://azure.microsoft.com/en-us/services/container-registry/
  • Docs: https://docs.microsoft.com/azure/container-registry/

Harbor:
  • https://goharbor.io
  • Docs: https://goharbor.io/docs/
  • GitHub: https://github.com/goharbor/harbor

Quay.io:
  • https://quay.io
  • Docs: https://docs.quay.io

# ═══════════════════════════════════════════════════════════
# TOOLS
# ═══════════════════════════════════════════════════════════

Crane:
  • https://github.com/google/go-containerregistry/tree/main/cmd/crane

Skopeo:
  • https://github.com/containers/skopeo

Cosign:
  • https://github.com/sigstore/cosign
  • Docs: https://docs.sigstore.dev/cosign/

Trivy:
  • https://github.com/aquasecurity/trivy
  • Docs: https://aquasecurity.github.io/trivy/

Syft (SBOM):
  • https://github.com/anchore/syft

Grype (Scanner):
  • https://github.com/anchore/grype

Dive (Analyze layers):
  • https://github.com/wagoodman/dive

# ═══════════════════════════════════════════════════════════
# LEARNING RESOURCES
# ═══════════════════════════════════════════════════════════

Official:
  • Docker Docs: https://docs.docker.com
  • OCI Spec: https://github.com/opencontainers/image-spec
  • CNCF Projects: https://www.cncf.io/projects/

Courses:
  • Docker Mastery (Udemy - Bret Fisher)
  • Kubernetes for Developers (Linux Foundation)
  • Cloud Provider Certifications

Communities:
  • Docker Community: https://www.docker.com/community
  • CNCF Slack: https://slack.cncf.io
  • Reddit: r/docker, r/kubernetes

Blogs:
  • Docker Blog: https://www.docker.com/blog/
  • CNCF Blog: https://www.cncf.io/blog/
  • Cloud Provider Blogs

# ═══════════════════════════════════════════════════════════
# STANDARDS & SPECIFICATIONS
# ═══════════════════════════════════════════════════════════

OCI (Open Container Initiative):
  • Image Spec: https://github.com/opencontainers/image-spec
  • Distribution Spec: https://github.com/opencontainers/distribution-spec
  • Runtime Spec: https://github.com/opencontainers/runtime-spec

Container Image Format:
  • https://github.com/opencontainers/image-spec/blob/main/spec.md

Registry API:
  • Docker Registry HTTP API V2
  • https://docs.docker.com/registry/spec/api/

Sigstore:
  • https://www.sigstore.dev
  • Cosign, Rekor, Fulcio

SBOM Standards:
  • SPDX: https://spdx.dev
  • CycloneDX: https://cyclonedx.org
```

---

<div align="center">

**Built with 🐳 by MrDib**

_Now you know everything about Container Registries!_ ✨

**Go build something amazing!** 🚀

</div>

---

### Final Words

```
╔═════════════════════════════════════════════════════════╗
║                                                         ║
║  🎯 YOU'VE MASTERED CONTAINER REGISTRIES!               ║
║                                                         ║
║  You now know:                                          ║
║  ✅ All major container registries                      ║
║  ✅ Security best practices                             ║
║  ✅ Image signing & verification                        ║
║  ✅ Vulnerability scanning                              ║
║  ✅ Cost optimization                                   ║
║  ✅ CI/CD integration                                   ║
║  ✅ Migration strategies                                ║
║  ✅ Troubleshooting                                     ║
║                                                         ║
║  Remember:                                              ║
║  • Security first (scan, sign, verify!)                 ║
║  • Optimize images (multi-stage builds!)                ║
║  • Tag properly (semantic versioning!)                  ║
║  • Monitor costs (lifecycle policies!)                  ║
║  • Automate everything (CI/CD!)                         ║
║                                                         ║
║  Now stop reading and start building! 🎉                ║
║                                                         ║
╚═════════════════════════════════════════════════════════╝

"A container registry is not just storage—
it's the foundation of your deployment pipeline."
                                        - MrDib, 2025

P.S. Don't forget to:
☐ Star this repo ⭐
☐ Share with your team 👥
☐ Implement these practices 🛠️
☐ Build something awesome 🚀
```
