<div align="center">

# 🐳 Docker - The Complete Guide

### _Build once, run anywhere_ 📦

![Docker](https://img.shields.io/badge/Docker-24.0+-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Compose](https://img.shields.io/badge/Compose-v2-2496ED?style=for-the-badge)
![Platform](https://img.shields.io/badge/Platform-Cross%20Platform-green?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Production%20Ready-success?style=for-the-badge)

</div>

---

## 📚 Table of Contents

- [🎯 Docker Fundamentals](#-docker-fundamentals)
- [🚀 Installation & Setup](#-installation--setup)
- [📦 Images Deep Dive](#-images-deep-dive)
- [🐳 Containers Explained](#-containers-explained)
- [📝 Dockerfile Mastery](#-dockerfile-mastery)
- [🔗 Docker Compose](#-docker-compose)
- [🌐 Networking](#-networking)
- [💾 Volumes & Storage](#-volumes--storage)
- [🔐 Security Best Practices](#-security-best-practices)
- [⚡ Performance Optimization](#-performance-optimization)
- [🛠️ Development Workflows](#️-development-workflows)
- [🚢 Production Deployment](#-production-deployment)
- [📊 Monitoring & Logging](#-monitoring--logging)
- [🐛 Troubleshooting](#-troubleshooting)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 🎯 Docker Fundamentals

_Understanding containers from first principles_ 🧠

</div>

### What is Docker? The 5-Minute Explanation

```
🎯 THE PROBLEM DOCKER SOLVES:

Traditional Development:
┌──────────────────────────────────────────────────────┐
│  Developer Machine        Production Server          │
│  ├─ Python 3.9            ├─ Python 3.7  ❌          │
│  ├─ Node.js 20            ├─ Node.js 18  ❌          │
│  ├─ Ubuntu 22.04          ├─ CentOS 7    ❌          │
│  └─ Works on my machine!  └─ Doesn't work! 💥        │
└──────────────────────────────────────────────────────┘

THE CLASSIC: "But it works on my machine!" 😅

═══════════════════════════════════════════════════════════

THE DOCKER SOLUTION:

Package Everything Together:
┌──────────────────────────────────────────────────────┐
│                    Docker Container                  │
│  ┌────────────────────────────────────────────────┐  │
│  │  Your Application                              │  │
│  │  ├─ App Code                                   │  │
│  │  ├─ Dependencies (package.json, requirements)  │  │
│  │  ├─ Runtime (Node.js, Python, etc.)            │  │
│  │  ├─ System Libraries                           │  │
│  │  └─ Configuration                              │  │
│  └────────────────────────────────────────────────┘  │
│                                                      │
│  Runs on:                                            │
│  ✅ Your laptop                                      │
│  ✅ Coworker's laptop                                │
│  ✅ CI/CD server                                     │
│  ✅ Production server                                │
│  ✅ Cloud (AWS, GCP, Azure)                          │
└──────────────────────────────────────────────────────┘

Result: "If it works on your machine, it works everywhere!" 🎉

═══════════════════════════════════════════════════════════

DOCKER vs VIRTUAL MACHINES:

Virtual Machines (Heavy):
┌────────────────────────────────────────┐
│         Physical Hardware              │
│  ┌──────────────────────────────────┐  │
│  │      Host Operating System       │  │
│  │  ┌────────────┐  ┌────────────┐  │  │
│  │  │ Hypervisor │  │ Hypervisor │  │  │
│  │  ├────────────┤  ├────────────┤  │  │
│  │  │  Guest OS  │  │  Guest OS  │  │  │ Each VM = Full OS!
│  │  │  (2-4 GB)  │  │  (2-4 GB)  │  │  │ Boot time: Minutes
│  │  ├────────────┤  ├────────────┤  │  │ Resource: Heavy
│  │  │    App     │  │    App     │  │  │
│  │  └────────────┘  └────────────┘  │  │
│  └──────────────────────────────────┘  │
└────────────────────────────────────────┘

Docker Containers (Lightweight):
┌────────────────────────────────────────┐
│         Physical Hardware              │
│  ┌──────────────────────────────────┐  │
│  │      Host Operating System       │  │
│  │  ┌──────────────────────────┐    │  │
│  │  │     Docker Engine        │    │  │
│  │  ├──────────┬───────────────┤    │  │
│  │  │Container │   Container   │    │  │ Share OS kernel!
│  │  │  (50 MB) │   (50 MB)     │    │  │ Boot time: Seconds
│  │  ├──────────┼───────────────┤    │  │ Resource: Light
│  │  │   App    │      App      │    │  │
│  │  └──────────┴───────────────┘    │  │
│  └──────────────────────────────────┘  │
└────────────────────────────────────────┘

Containers:
  ✅ 10x faster startup
  ✅ 10x less resource usage
  ✅ 10x more density (more containers per server)
  ✅ Share host OS kernel (Linux)

VMs:
  ✅ Stronger isolation
  ✅ Can run different OS kernels
  ✅ Better for running Windows on Linux (or vice versa)
```

---

### Core Concepts Visualized

```
📦 DOCKER ARCHITECTURE:

┌─────────────────────────────────────────────────────────┐
│                    YOUR COMPUTER                         │
│                                                          │
│  ┌────────────────────────────────────────────────┐     │
│  │              Docker Client (CLI)               │     │
│  │  $ docker run nginx                            │     │
│  │  $ docker build -t myapp .                     │     │
│  └────────────────┬───────────────────────────────┘     │
│                   │ REST API                             │
│  ┌────────────────▼───────────────────────────────┐     │
│  │            Docker Daemon (dockerd)             │     │
│  │  • Manages containers                          │     │
│  │  • Manages images                              │     │
│  │  • Manages networks                            │     │
│  │  • Manages volumes                             │     │
│  └────────────────┬───────────────────────────────┘     │
│                   │                                      │
│  ┌────────────────▼───────────────────────────────┐     │
│  │         Containers (Running)                   │     │
│  │  ┌──────────┐  ┌──────────┐  ┌──────────┐     │     │
│  │  │ nginx    │  │ postgres │  │  myapp   │     │     │
│  │  │ (Port 80)│  │(Port 5432)│ │(Port 3000)│     │     │
│  │  └──────────┘  └──────────┘  └──────────┘     │     │
│  └────────────────────────────────────────────────┘     │
│                                                          │
│  ┌────────────────────────────────────────────────┐     │
│  │         Images (Stored Locally)                │     │
│  │  📦 nginx:latest                               │     │
│  │  📦 postgres:15                                │     │
│  │  📦 myapp:v1.0.0                               │     │
│  └────────────────────────────────────────────────┘     │
└─────────────────────────────────────────────────────────┘
                   ▲
                   │ docker pull/push
                   │
┌──────────────────▼──────────────────────────────────────┐
│              Docker Registry (Remote)                    │
│  • Docker Hub (hub.docker.com)                          │
│  • GitHub Container Registry (ghcr.io)                  │
│  • Private Registry                                     │
│                                                          │
│  📦 nginx:latest        📦 node:20                       │
│  📦 postgres:15         📦 python:3.12                   │
│  📦 redis:7             📦 mysql:8                       │
└──────────────────────────────────────────────────────────┘

═══════════════════════════════════════════════════════════

KEY CONCEPTS:

1. Image (Template):
   • Read-only template
   • Contains OS, code, dependencies
   • Built from Dockerfile
   • Stored in registry
   • Example: nginx:latest, node:20-alpine

2. Container (Running Instance):
   • Running instance of an image
   • Isolated process
   • Has its own filesystem
   • Can be started/stopped/deleted
   • Example: my-nginx-container

3. Dockerfile (Blueprint):
   • Text file with instructions
   • Defines how to build an image
   • Like a recipe
   • Example: FROM, COPY, RUN, CMD

4. Volume (Persistent Storage):
   • Persistent data storage
   • Survives container deletion
   • Shared between containers
   • Example: /var/lib/postgresql/data

5. Network (Communication):
   • Connects containers
   • Isolates traffic
   • Built-in DNS
   • Example: bridge, host, overlay

6. Registry (Image Store):
   • Stores and distributes images
   • Public or private
   • Like GitHub for Docker images
   • Example: Docker Hub, GHCR

═══════════════════════════════════════════════════════════

IMAGE → CONTAINER RELATIONSHIP:

Image (Class):                Container (Instance):
┌─────────────┐              ┌─────────────┐
│  nginx:     │    run →     │ container1  │
│  latest     │              │ (running)   │
│             │    run →     ├─────────────┤
│ (template)  │              │ container2  │
│             │    run →     │ (running)   │
│ One image   │              ├─────────────┤
│ stored once │              │ container3  │
└─────────────┘              │ (stopped)   │
                             └─────────────┘
                             Many containers
                             from one image

Think of it like:
• Image = Class definition (OOP)
• Container = Object instance
• Image = Recipe
• Container = Cooked meal
• Image = .exe file
• Container = Running program
```

---

<div align="center">

## 🚀 Installation & Setup

_Get Docker running on your system_ ⚙️

</div>

### Installation by Platform

```bash
# ═══════════════════════════════════════════════════════════
# DOCKER DESKTOP (macOS & Windows) - RECOMMENDED
# ═══════════════════════════════════════════════════════════

macOS:
  # Download Docker Desktop
  https://www.docker.com/products/docker-desktop/

  # OR via Homebrew
  brew install --cask docker

  # Start Docker Desktop app
  # Icon appears in menu bar

Windows:
  # Requirements:
  • Windows 10/11 64-bit (Pro, Enterprise, or Education)
  • Enable Hyper-V and Containers features
  • OR use WSL 2 (recommended!)

  # Download Docker Desktop
  https://www.docker.com/products/docker-desktop/

  # WSL 2 Setup (recommended):
  wsl --install
  wsl --set-default-version 2

  # Install Docker Desktop with WSL 2 backend

# ═══════════════════════════════════════════════════════════
# LINUX (Ubuntu/Debian)
# ═══════════════════════════════════════════════════════════

# Remove old versions
sudo apt-get remove docker docker-engine docker.io containerd runc

# Update package index
sudo apt-get update

# Install prerequisites
sudo apt-get install -y \
  ca-certificates \
  curl \
  gnupg \
  lsb-release

# Add Docker's official GPG key
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | \
  sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

# Set up repository
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \
  https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Install Docker Engine
sudo apt-get update
sudo apt-get install -y docker-ce docker-ce-cli containerd.io \
  docker-buildx-plugin docker-compose-plugin

# Start Docker
sudo systemctl start docker
sudo systemctl enable docker

# Add user to docker group (no more sudo!)
sudo usermod -aG docker $USER
newgrp docker  # Activate changes

# Test installation
docker run hello-world

# ═══════════════════════════════════════════════════════════
# LINUX (CentOS/RHEL/Fedora)
# ═══════════════════════════════════════════════════════════

# Remove old versions
sudo yum remove docker docker-client docker-client-latest \
  docker-common docker-latest docker-latest-logrotate \
  docker-logrotate docker-engine

# Install prerequisites
sudo yum install -y yum-utils

# Add Docker repository
sudo yum-config-manager --add-repo \
  https://download.docker.com/linux/centos/docker-ce.repo

# Install Docker Engine
sudo yum install -y docker-ce docker-ce-cli containerd.io \
  docker-buildx-plugin docker-compose-plugin

# Start Docker
sudo systemctl start docker
sudo systemctl enable docker

# Add user to docker group
sudo usermod -aG docker $USER
newgrp docker

# ═══════════════════════════════════════════════════════════
# VERIFICATION
# ═══════════════════════════════════════════════════════════

# Check Docker version
docker --version
# Output: Docker version 24.0.7, build afdd53b

# Check Docker Compose
docker compose version
# Output: Docker Compose version v2.23.3

# Detailed info
docker info

# Test with hello-world
docker run hello-world

# Expected output:
# Hello from Docker!
# This message shows that your installation appears to be working correctly.

# ═══════════════════════════════════════════════════════════
# POST-INSTALLATION CONFIGURATION
# ═══════════════════════════════════════════════════════════

# Configure Docker daemon
sudo mkdir -p /etc/docker
sudo tee /etc/docker/daemon.json <<EOF
{
  "log-driver": "json-file",
  "log-opts": {
    "max-size": "10m",
    "max-file": "3"
  },
  "default-address-pools": [
    {
      "base": "172.17.0.0/16",
      "size": 24
    }
  ],
  "storage-driver": "overlay2"
}
EOF

# Restart Docker
sudo systemctl restart docker

# Enable BuildKit (faster builds!)
echo 'export DOCKER_BUILDKIT=1' >> ~/.bashrc
echo 'export COMPOSE_DOCKER_CLI_BUILD=1' >> ~/.bashrc
source ~/.bashrc

# ═══════════════════════════════════════════════════════════
# DOCKER DESKTOP SETTINGS (macOS/Windows)
# ═══════════════════════════════════════════════════════════

Recommended Settings:
  Resources:
    • CPUs: 4 (or half your cores)
    • Memory: 8 GB (or half your RAM)
    • Disk: 100 GB+

  Features:
    ✅ Use Docker Compose V2
    ✅ Enable Kubernetes (optional)
    ✅ Use gRPC FUSE for file sharing (macOS)
    ✅ Use WSL 2 backend (Windows)

  Advanced:
    ✅ Enable resource limits
    ✅ Enable experimental features
    ✅ Configure log rotation

# ═══════════════════════════════════════════════════════════
# USEFUL ALIASES
# ═══════════════════════════════════════════════════════════

# Add to ~/.bashrc or ~/.zshrc
alias d='docker'
alias dc='docker compose'
alias dps='docker ps'
alias dpsa='docker ps -a'
alias di='docker images'
alias dex='docker exec -it'
alias dlog='docker logs -f'
alias dclean='docker system prune -af --volumes'
alias dstop='docker stop $(docker ps -q)'
alias drm='docker rm $(docker ps -aq)'
alias drmi='docker rmi $(docker images -q)'

# Docker Compose shortcuts
alias dcup='docker compose up -d'
alias dcdown='docker compose down'
alias dcrestart='docker compose restart'
alias dclogs='docker compose logs -f'

# Reload shell
source ~/.bashrc  # or ~/.zshrc
```

---

<div align="center">

## 📦 Images Deep Dive

_Understanding Docker images_ 🖼️

</div>

### Image Architecture

```
🏗️ IMAGE LAYERS EXPLAINED:

Docker Image = Stack of Read-Only Layers

Example: Node.js Application
┌─────────────────────────────────────┐
│     Container (Writable Layer)      │ ← Your changes
├─────────────────────────────────────┤
│  Layer 5: CMD ["node", "app.js"]    │ ← 0 MB
├─────────────────────────────────────┤
│  Layer 4: COPY . .                  │ ← 10 MB (your code)
├─────────────────────────────────────┤
│  Layer 3: RUN npm install           │ ← 150 MB (node_modules)
├─────────────────────────────────────┤
│  Layer 2: COPY package*.json ./     │ ← 0.01 MB
├─────────────────────────────────────┤
│  Layer 1: FROM node:20-alpine       │ ← 135 MB (base OS + Node)
└─────────────────────────────────────┘
Total: ~295 MB

Key Concepts:
• Each Dockerfile instruction = new layer
• Layers are cached (reusable!)
• Layers are immutable (read-only)
• Containers add writable layer on top
• Multiple containers share base layers

═══════════════════════════════════════════════════════════

LAYER CACHING (The Secret Sauce):

First Build:
  Layer 1: FROM node:20-alpine      ⏱️  2 minutes (download)
  Layer 2: COPY package.json        ⏱️  0.1 seconds
  Layer 3: RUN npm install          ⏱️  3 minutes
  Layer 4: COPY . .                 ⏱️  1 second
  Total: 5 minutes

Second Build (no changes):
  Layer 1: CACHED ✅                 ⏱️  0 seconds
  Layer 2: CACHED ✅                 ⏱️  0 seconds
  Layer 3: CACHED ✅                 ⏱️  0 seconds
  Layer 4: CACHED ✅                 ⏱️  0 seconds
  Total: 1 second! 🚀

Third Build (code changed):
  Layer 1: CACHED ✅                 ⏱️  0 seconds
  Layer 2: CACHED ✅                 ⏱️  0 seconds
  Layer 3: CACHED ✅                 ⏱️  0 seconds
  Layer 4: REBUILD                  ⏱️  1 second
  Total: 1 second! 🎉

Fourth Build (dependencies changed):
  Layer 1: CACHED ✅                 ⏱️  0 seconds
  Layer 2: REBUILD                  ⏱️  0.1 seconds
  Layer 3: REBUILD                  ⏱️  3 minutes (npm install again!)
  Layer 4: REBUILD                  ⏱️  1 second
  Total: 3 minutes

💡 Lesson: Order matters! Put changing files LAST!
```

---

### Image Management Commands

```bash
# ═══════════════════════════════════════════════════════════
# WORKING WITH IMAGES
# ═══════════════════════════════════════════════════════════

# Pull image from registry
docker pull nginx:latest
docker pull node:20-alpine
docker pull postgres:15

# Pull specific platform (M1/M2 Macs, ARM servers)
docker pull --platform linux/amd64 mysql:8
docker pull --platform linux/arm64 nginx:latest

# List images
docker images
docker image ls

# Detailed format
docker images --format "table {{.Repository}}\t{{.Tag}}\t{{.Size}}"

# Filter images
docker images nginx
docker images "node:*alpine*"

# Show image history (layers)
docker history nginx:latest
docker history --no-trunc myapp:latest  # Full commands

# Inspect image (detailed info)
docker inspect nginx:latest
docker inspect nginx:latest | jq '.[0].Config'  # With jq

# ═══════════════════════════════════════════════════════════
# BUILDING IMAGES
# ═══════════════════════════════════════════════════════════

# Build from Dockerfile
docker build -t myapp:latest .

# Build with custom Dockerfile name
docker build -f Dockerfile.prod -t myapp:prod .

# Build with no cache (force rebuild)
docker build --no-cache -t myapp:latest .

# Build with build arguments
docker build --build-arg NODE_VERSION=20 -t myapp:latest .

# Build with target stage (multi-stage)
docker build --target production -t myapp:prod .

# Build for multiple platforms (BuildX)
docker buildx build \
  --platform linux/amd64,linux/arm64 \
  -t myapp:latest \
  --push .  # Push to registry

# Build with progress (pretty output)
docker build --progress=plain -t myapp:latest .

# ═══════════════════════════════════════════════════════════
# TAGGING IMAGES
# ═══════════════════════════════════════════════════════════

# Tag existing image
docker tag myapp:latest myapp:v1.0.0
docker tag myapp:latest ghcr.io/username/myapp:latest

# Tag for registry
docker tag nginx:latest registry.company.com/nginx:latest

# Multiple tags
docker tag myapp:latest myapp:v1
docker tag myapp:latest myapp:v1.0
docker tag myapp:latest myapp:v1.0.0

# ═══════════════════════════════════════════════════════════
# PUSHING/PULLING TO REGISTRY
# ═══════════════════════════════════════════════════════════

# Push to Docker Hub
docker push username/myapp:latest

# Push to GHCR
docker push ghcr.io/username/myapp:latest

# Push all tags
docker push --all-tags username/myapp

# Pull from private registry
docker pull registry.company.com/myapp:latest

# ═══════════════════════════════════════════════════════════
# REMOVING IMAGES
# ═══════════════════════════════════════════════════════════

# Remove single image
docker rmi nginx:latest
docker rmi image-id

# Remove multiple images
docker rmi image1 image2 image3

# Force remove (even if containers using it)
docker rmi -f nginx:latest

# Remove unused images
docker image prune
docker image prune -a  # Remove all unused images

# Remove images by pattern
docker images -q nginx:* | xargs docker rmi

# ═══════════════════════════════════════════════════════════
# SAVING/LOADING IMAGES (Offline Transfer)
# ═══════════════════════════════════════════════════════════

# Save image to tar file
docker save -o nginx.tar nginx:latest
docker save nginx:latest | gzip > nginx.tar.gz  # Compressed

# Save multiple images
docker save -o images.tar nginx:latest postgres:15 redis:7

# Load image from tar file
docker load -i nginx.tar
docker load < nginx.tar.gz

# Export/Import (flatten layers, no history!)
docker export container-name > container.tar
docker import container.tar myapp:imported

# ═══════════════════════════════════════════════════════════
# IMAGE ANALYSIS & OPTIMIZATION
# ═══════════════════════════════════════════════════════════

# Analyze image size
docker images --format "{{.Repository}}:{{.Tag}}\t{{.Size}}"

# Show what's taking up space
docker history --no-trunc myapp:latest

# Use dive to explore layers (external tool)
# Install: brew install dive
dive myapp:latest

# Scan for vulnerabilities
docker scan myapp:latest  # Docker Desktop feature

# Or use Trivy
trivy image myapp:latest

# ═══════════════════════════════════════════════════════════
# IMAGE CLEANUP
# ═══════════════════════════════════════════════════════════

# Remove dangling images (untagged)
docker image prune

# Remove all unused images
docker image prune -a

# Remove images older than 24 hours
docker image prune -a --filter "until=24h"

# Clean up everything (images, containers, networks, volumes)
docker system prune -a --volumes

# Show disk usage
docker system df
docker system df -v  # Verbose

# ═══════════════════════════════════════════════════════════
# ADVANCED: MULTI-PLATFORM BUILDS
# ═══════════════════════════════════════════════════════════

# Create builder instance
docker buildx create --name mybuilder --use
docker buildx inspect --bootstrap

# Build for multiple platforms
docker buildx build \
  --platform linux/amd64,linux/arm64,linux/arm/v7 \
  -t username/myapp:latest \
  --push .

# Build and load locally (single platform only)
docker buildx build \
  --platform linux/amd64 \
  -t myapp:latest \
  --load .
```

---

### Image Best Practices

```yaml
# ═══════════════════════════════════════════════════════════
# IMAGE SIZE OPTIMIZATION
# ═══════════════════════════════════════════════════════════

Choose Minimal Base Images:
  ❌ FROM ubuntu:22.04           # 77 MB
  ❌ FROM node:20                # 1.1 GB
  ✅ FROM alpine:3.19            # 7 MB
  ✅ FROM node:20-alpine         # 135 MB
  ✅ FROM gcr.io/distroless/base # 20 MB (no shell!)

Multi-Stage Builds:
  # Before: 1.2 GB
  FROM node:20
  WORKDIR /app
  COPY . .
  RUN npm install
  RUN npm run build
  CMD ["node", "dist/server.js"]

  # After: 150 MB (90% smaller!)
  FROM node:20 AS builder
  WORKDIR /app
  COPY package*.json ./
  RUN npm ci
  COPY . .
  RUN npm run build

  FROM node:20-alpine
  WORKDIR /app
  COPY --from=builder /app/dist ./dist
  COPY --from=builder /app/node_modules ./node_modules
  CMD ["node", "dist/server.js"]

Combine RUN Commands:
  # ❌ BAD: 4 layers
  RUN apt-get update
  RUN apt-get install -y curl
  RUN apt-get install -y git
  RUN apt-get clean

  # ✅ GOOD: 1 layer
  RUN apt-get update && \
      apt-get install -y curl git && \
      apt-get clean && \
      rm -rf /var/lib/apt/lists/*

Remove Build Dependencies:
  RUN apk add --no-cache --virtual .build-deps \
      gcc musl-dev && \
      pip install cryptography && \
      apk del .build-deps  # Remove after use!

# ═══════════════════════════════════════════════════════════
# LAYER CACHING OPTIMIZATION
# ═══════════════════════════════════════════════════════════

Order Dockerfile Instructions:
  FROM node:20-alpine
  WORKDIR /app

  # 1. Copy dependencies first (change rarely)
  COPY package*.json ./
  RUN npm ci --only=production

  # 2. Copy code last (changes often)
  COPY . .

  CMD ["node", "server.js"]

  # Result: Code changes don't rebuild dependencies! 🚀

Use .dockerignore:
  # .dockerignore
  node_modules
  npm-debug.log
  .git
  .env
  .env.local
  .DS_Store
  *.md
  coverage
  .vscode
  .idea

  # Smaller context = faster builds!

# ═══════════════════════════════════════════════════════════
# SECURITY BEST PRACTICES
# ═══════════════════════════════════════════════════════════

Use Official Images:
  ✅ FROM node:20-alpine        # Official, maintained
  ❌ FROM random-user/node       # Unknown, risky

Specify Exact Versions:
  ✅ FROM node:20.10.0-alpine3.19
  ❌ FROM node:latest            # Unpredictable!

Run as Non-Root User:
  # Create user
  RUN addgroup -g 1001 -S nodejs && \
      adduser -S nodejs -u 1001

  # Change ownership
  COPY --chown=nodejs:nodejs . .

  # Switch to user
  USER nodejs

Scan for Vulnerabilities:
  # Trivy
  trivy image myapp:latest

  # Docker Scout (built-in)
  docker scout cves myapp:latest

  # Snyk
  snyk container test myapp:latest

Don't Include Secrets:
  ❌ ENV API_KEY="secret123"
  ❌ COPY .env .
  ✅ Use runtime secrets (env vars, secrets management)
```

<div align="center">

## 🐳 Containers Explained

_Running and managing containers_ 🏃

</div>

### Container Lifecycle

```
🔄 CONTAINER STATES:

┌─────────────────────────────────────────────────────────┐
│                   Container Lifecycle                    │
└─────────────────────────────────────────────────────────┘

    docker create
         ↓
    ┌─────────┐
    │ CREATED │  (Exists but not running)
    └────┬────┘
         │ docker start
         ↓
    ┌─────────┐
    │ RUNNING │  (Active, processes executing)
    └────┬────┘
         │
    ┌────┴────┬─────────┬─────────┐
    │         │         │         │
    pause   stop     kill      restart
    │         │         │         │
    ▼         ▼         ▼         │
┌─────────┐ ┌─────────┐ ┌─────────┐ │
│ PAUSED  │ │ STOPPED │ │  DEAD   │ │
└────┬────┘ └────┬────┘ └─────────┘ │
     │           │                   │
  unpause      start                 │
     │           │                   │
     └───────────┴───────────────────┘
                 │
                 ▼
         ┌─────────────┐
         │   REMOVED   │
         └─────────────┘
              (Gone forever)

Commands:
• docker create    → Create but don't start
• docker start     → Start existing container
• docker run       → Create + Start in one command
• docker pause     → Pause all processes
• docker unpause   → Resume paused container
• docker stop      → Graceful shutdown (SIGTERM)
• docker kill      → Force shutdown (SIGKILL)
• docker restart   → Stop + Start
• docker rm        → Remove container
```

---

### Essential Container Commands

```bash
# ═══════════════════════════════════════════════════════════
# RUNNING CONTAINERS
# ═══════════════════════════════════════════════════════════

# Run container (create + start)
docker run nginx

# Run in background (detached mode)
docker run -d nginx

# Run with name
docker run -d --name my-nginx nginx

# Run with port mapping
docker run -d -p 8080:80 nginx
# Host:Container
# Access at http://localhost:8080

# Run with environment variables
docker run -d \
  -e POSTGRES_PASSWORD=secret \
  -e POSTGRES_USER=admin \
  postgres:15

# Run with volume mount
docker run -d \
  -v /host/path:/container/path \
  nginx

# Run with automatic removal (cleanup)
docker run --rm -it ubuntu bash
# Deleted when you exit!

# Run with resource limits
docker run -d \
  --memory="512m" \
  --cpus="1.5" \
  nginx

# Run with restart policy
docker run -d \
  --restart=unless-stopped \
  nginx
# Policies: no, on-failure, always, unless-stopped

# Run interactive with terminal (for debugging)
docker run -it ubuntu bash
docker run -it node:20-alpine sh
docker run -it python:3.12 python

# Run with custom network
docker run -d \
  --network my-network \
  --name api \
  myapi:latest

# Run with all options combined
docker run -d \
  --name my-app \
  --hostname app-server \
  --restart=always \
  -p 3000:3000 \
  -e NODE_ENV=production \
  -e DATABASE_URL=postgres://... \
  -v app-data:/app/data \
  --network app-network \
  --memory="1g" \
  --cpus="2" \
  --health-cmd="curl -f http://localhost:3000/health || exit 1" \
  --health-interval=30s \
  --health-timeout=3s \
  --health-retries=3 \
  myapp:latest

# ═══════════════════════════════════════════════════════════
# MANAGING RUNNING CONTAINERS
# ═══════════════════════════════════════════════════════════

# List running containers
docker ps

# List all containers (including stopped)
docker ps -a

# List with custom format
docker ps --format "table {{.Names}}\t{{.Status}}\t{{.Ports}}"

# List container IDs only
docker ps -q

# Filter containers
docker ps --filter "name=nginx"
docker ps --filter "status=running"
docker ps --filter "ancestor=nginx:latest"

# Start stopped container
docker start container-name

# Stop running container
docker stop container-name
docker stop $(docker ps -q)  # Stop all running

# Restart container
docker restart container-name

# Pause/Unpause (freeze processes)
docker pause container-name
docker unpause container-name

# Kill container (force stop)
docker kill container-name

# Remove container
docker rm container-name
docker rm -f container-name  # Force remove (even if running)

# Remove all stopped containers
docker container prune
docker rm $(docker ps -aq)  # Alternative

# ═══════════════════════════════════════════════════════════
# INSPECTING CONTAINERS
# ═══════════════════════════════════════════════════════════

# View logs
docker logs container-name
docker logs -f container-name  # Follow (real-time)
docker logs --tail 100 container-name  # Last 100 lines
docker logs --since 1h container-name  # Last hour
docker logs --timestamps container-name  # With timestamps

# View real-time stats
docker stats
docker stats container-name

# View processes
docker top container-name

# Inspect container details
docker inspect container-name
docker inspect container-name | jq '.[0].NetworkSettings.IPAddress'

# View port mappings
docker port container-name

# View changes to filesystem
docker diff container-name

# ═══════════════════════════════════════════════════════════
# INTERACTING WITH CONTAINERS
# ═══════════════════════════════════════════════════════════

# Execute command in running container
docker exec container-name ls -la

# Interactive shell
docker exec -it container-name bash
docker exec -it container-name sh  # Alpine uses sh
docker exec -it container-name /bin/sh

# Execute as specific user
docker exec -u root -it container-name bash

# Run one-off command
docker exec container-name npm test
docker exec container-name python manage.py migrate

# Attach to running container (view output)
docker attach container-name
# Detach: Ctrl+P, Ctrl+Q (don't stop container)

# ═══════════════════════════════════════════════════════════
# COPYING FILES
# ═══════════════════════════════════════════════════════════

# Copy from container to host
docker cp container-name:/path/in/container /path/on/host

# Copy from host to container
docker cp /path/on/host container-name:/path/in/container

# Examples:
docker cp my-nginx:/etc/nginx/nginx.conf ./nginx.conf
docker cp ./app.js my-app:/app/app.js

# ═══════════════════════════════════════════════════════════
# CONTAINER RESOURCE MANAGEMENT
# ═══════════════════════════════════════════════════════════

# Update resource limits (running container)
docker update --memory="1g" --cpus="2" container-name

# Limit CPU shares (relative weight)
docker run -d --cpu-shares=512 nginx

# Set CPU quota (microseconds per 100ms)
docker run -d --cpu-quota=50000 nginx  # 50% of 1 CPU

# Set memory with swap
docker run -d \
  --memory="512m" \
  --memory-swap="1g" \
  nginx

# Block IO weight (relative to other containers)
docker run -d --blkio-weight=500 nginx

# ═══════════════════════════════════════════════════════════
# CONTAINER EXPORT/IMPORT (Not recommended, use images!)
# ═══════════════════════════════════════════════════════════

# Export container to tar
docker export container-name > container.tar

# Import tar as image
docker import container.tar myimage:tag

# Better: Commit container to image
docker commit container-name myimage:tag

# ═══════════════════════════════════════════════════════════
# HEALTH CHECKS
# ═══════════════════════════════════════════════════════════

# View health status
docker ps  # Shows health status
docker inspect container-name | jq '.[0].State.Health'

# Manual health check
docker exec container-name curl -f http://localhost/health

# ═══════════════════════════════════════════════════════════
# USEFUL ONE-LINERS
# ═══════════════════════════════════════════════════════════

# Stop all running containers
docker stop $(docker ps -q)

# Remove all containers
docker rm $(docker ps -aq)

# Remove all stopped containers
docker container prune -f

# Follow logs for multiple containers
docker logs -f $(docker ps -q --filter "name=api")

# Get IP address of container
docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' container-name

# Get environment variables
docker inspect -f '{{.Config.Env}}' container-name

# Restart unhealthy containers
docker ps --filter "health=unhealthy" -q | xargs docker restart

# Show size of containers
docker ps -s
```

---

### Container Networking Basics

```bash
# ═══════════════════════════════════════════════════════════
# CONTAINER NETWORKING QUICK START
# ═══════════════════════════════════════════════════════════

# Port Mapping (Host:Container)
docker run -d -p 8080:80 nginx
# Host port 8080 → Container port 80
# Access: http://localhost:8080

# Publish all exposed ports (random host ports)
docker run -d -P nginx

# Multiple port mappings
docker run -d \
  -p 3000:3000 \
  -p 3001:3001 \
  myapp

# Bind to specific host interface
docker run -d -p 127.0.0.1:8080:80 nginx
# Only accessible from localhost

# UDP ports
docker run -d -p 53:53/udp dns-server

# Container-to-Container Communication
# Create custom network
docker network create mynetwork

# Run containers on same network
docker run -d --name db --network mynetwork postgres
docker run -d --name api --network mynetwork myapi

# Inside api container, connect to: db:5432
# Docker's built-in DNS resolves container names!

# Check container's IP
docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' container-name
```

---

<div align="center">

## 📝 Dockerfile Mastery

_Writing production-grade Dockerfiles_ 📜

</div>

### Dockerfile Instructions Reference

```dockerfile
# ═══════════════════════════════════════════════════════════
# DOCKERFILE INSTRUCTION REFERENCE
# ═══════════════════════════════════════════════════════════

# FROM - Base image (required, first instruction)
FROM node:20-alpine
FROM node:20-alpine AS builder  # Named stage
FROM scratch  # Empty image (for static binaries)

# LABEL - Metadata
LABEL maintainer="mrdib@example.com"
LABEL version="1.0.0"
LABEL description="My awesome app"
LABEL org.opencontainers.image.source="https://github.com/user/repo"

# ARG - Build-time variables
ARG NODE_VERSION=20
ARG BUILD_DATE
FROM node:${NODE_VERSION}-alpine

# Usage:
# docker build --build-arg NODE_VERSION=18 -t myapp .

# ENV - Environment variables (runtime)
ENV NODE_ENV=production
ENV PORT=3000
ENV DATABASE_URL="postgres://localhost/mydb"

# Multiple env vars
ENV NODE_ENV=production \
    PORT=3000 \
    LOG_LEVEL=info

# WORKDIR - Set working directory
WORKDIR /app
# Creates directory if doesn't exist
# All subsequent commands run from here

# COPY - Copy files from host to image
COPY package.json .
COPY package*.json ./
COPY src/ ./src/
COPY --chown=node:node . .  # With ownership

# ADD - Like COPY but with extras (avoid unless needed!)
ADD https://example.com/file.tar.gz /tmp/  # Download URL
ADD archive.tar.gz /app/  # Auto-extract tar/zip
# ⚠️ Use COPY for simple file copying!

# RUN - Execute commands during build
RUN npm install
RUN apt-get update && apt-get install -y curl

# Multiple commands (single layer)
RUN apt-get update && \
    apt-get install -y curl git && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Use build cache mount (BuildKit)
RUN --mount=type=cache,target=/root/.npm \
    npm ci

# USER - Switch user (security!)
USER node
USER 1001  # By UID

# EXPOSE - Document ports (doesn't publish!)
EXPOSE 3000
EXPOSE 80 443
EXPOSE 8080/tcp 8080/udp

# VOLUME - Create mount point
VOLUME /data
VOLUME ["/var/log", "/var/db"]

# CMD - Default command (can be overridden)
CMD ["node", "server.js"]
CMD ["npm", "start"]

# Only last CMD is used:
CMD echo "Hello"  # Ignored
CMD echo "World"  # This runs

# ENTRYPOINT - Main command (harder to override)
ENTRYPOINT ["node", "server.js"]

# ENTRYPOINT + CMD (best practice!)
ENTRYPOINT ["node"]
CMD ["server.js"]
# docker run myapp           → node server.js
# docker run myapp app.js    → node app.js

# HEALTHCHECK - Container health monitoring
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
  CMD curl -f http://localhost:3000/health || exit 1

# Disable health check
HEALTHCHECK NONE

# STOPSIGNAL - Signal to stop container
STOPSIGNAL SIGTERM  # Default
STOPSIGNAL SIGINT

# SHELL - Default shell for RUN commands
SHELL ["/bin/bash", "-c"]

# ONBUILD - Instructions for derived images
ONBUILD COPY . /app
ONBUILD RUN npm install
# Runs when this image is used as base

# ═══════════════════════════════════════════════════════════
# MULTI-STAGE BUILD TEMPLATE
# ═══════════════════════════════════════════════════════════

# Stage 1: Dependencies
FROM node:20-alpine AS deps
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production

# Stage 2: Build
FROM node:20 AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

# Stage 3: Production
FROM node:20-alpine AS production
WORKDIR /app

# Copy from previous stages
COPY --from=deps /app/node_modules ./node_modules
COPY --from=builder /app/dist ./dist
COPY package*.json ./

USER node
EXPOSE 3000
CMD ["node", "dist/server.js"]

# Build specific stage:
# docker build --target production -t myapp:prod .
```

---

### Real-World Dockerfile Examples

```dockerfile
# ═══════════════════════════════════════════════════════════
# NODE.JS APPLICATION (Express/NestJS/Next.js)
# ═══════════════════════════════════════════════════════════

FROM node:20-alpine AS base

# Install dependencies only when needed
FROM base AS deps
WORKDIR /app

# Copy package files
COPY package.json package-lock.json ./

# Install dependencies
RUN npm ci

# Rebuild source code only when needed
FROM base AS builder
WORKDIR /app
COPY --from=deps /app/node_modules ./node_modules
COPY . .

# Build application
RUN npm run build

# Production image
FROM base AS runner
WORKDIR /app

# Don't run as root
RUN addgroup --system --gid 1001 nodejs && \
    adduser --system --uid 1001 nodejs

# Copy built application
COPY --from=builder --chown=nodejs:nodejs /app/dist ./dist
COPY --from=builder --chown=nodejs:nodejs /app/node_modules ./node_modules
COPY --from=builder --chown=nodejs:nodejs /app/package.json ./

USER nodejs

EXPOSE 3000

ENV NODE_ENV=production
ENV PORT=3000

HEALTHCHECK --interval=30s --timeout=3s --start-period=5s \
  CMD node healthcheck.js || exit 1

CMD ["node", "dist/main.js"]

# ═══════════════════════════════════════════════════════════
# PYTHON APPLICATION (Flask/FastAPI/Django)
# ═══════════════════════════════════════════════════════════

FROM python:3.12-slim AS base

# Set environment variables
ENV PYTHONUNBUFFERED=1 \
    PYTHONDONTWRITEBYTECODE=1 \
    PIP_NO_CACHE_DIR=1 \
    PIP_DISABLE_PIP_VERSION_CHECK=1

WORKDIR /app

# Install system dependencies
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    gcc \
    postgresql-client && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Install Python dependencies
FROM base AS deps
COPY requirements.txt .
RUN pip install --user --no-cache-dir -r requirements.txt

# Final stage
FROM python:3.12-slim
ENV PYTHONUNBUFFERED=1 \
    PATH=/root/.local/bin:$PATH

WORKDIR /app

# Copy Python dependencies
COPY --from=deps /root/.local /root/.local

# Copy application
COPY . .

# Create non-root user
RUN useradd -m -u 1001 appuser && \
    chown -R appuser:appuser /app

USER appuser

EXPOSE 8000

HEALTHCHECK --interval=30s --timeout=3s \
  CMD python -c "import requests; requests.get('http://localhost:8000/health')"

CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]

# ═══════════════════════════════════════════════════════════
# GO APPLICATION (Static Binary)
# ═══════════════════════════════════════════════════════════

# Build stage
FROM golang:1.21-alpine AS builder

WORKDIR /app

# Copy go mod files
COPY go.mod go.sum ./
RUN go mod download

# Copy source code
COPY . .

# Build binary
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o main .

# Final stage (minimal!)
FROM scratch

# Copy CA certificates (for HTTPS)
COPY --from=builder /etc/ssl/certs/ca-certificates.crt /etc/ssl/certs/

# Copy binary
COPY --from=builder /app/main /main

EXPOSE 8080

ENTRYPOINT ["/main"]

# Result: ~10 MB image! 🎉

# ═══════════════════════════════════════════════════════════
# REACT/FRONTEND APPLICATION
# ═══════════════════════════════════════════════════════════

# Build stage
FROM node:20-alpine AS builder

WORKDIR /app

COPY package*.json ./
RUN npm ci

COPY . .
RUN npm run build

# Production stage (Nginx)
FROM nginx:alpine

# Copy built files
COPY --from=builder /app/build /usr/share/nginx/html

# Copy custom nginx config (optional)
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]

# Result: ~25 MB image!

# ═══════════════════════════════════════════════════════════
# JAVA APPLICATION (Spring Boot)
# ═══════════════════════════════════════════════════════════

FROM maven:3.9-eclipse-temurin-21 AS builder

WORKDIR /app

# Copy pom.xml and download dependencies
COPY pom.xml .
RUN mvn dependency:go-offline

# Copy source and build
COPY src ./src
RUN mvn package -DskipTests

# Runtime stage
FROM eclipse-temurin:21-jre-alpine

WORKDIR /app

# Copy jar from builder
COPY --from=builder /app/target/*.jar app.jar

# Create non-root user
RUN addgroup -g 1001 spring && \
    adduser -u 1001 -G spring -s /bin/sh -D spring

USER spring

EXPOSE 8080

HEALTHCHECK --interval=30s --timeout=3s \
  CMD wget --quiet --tries=1 --spider http://localhost:8080/actuator/health || exit 1

ENTRYPOINT ["java", "-jar", "/app/app.jar"]

# ═══════════════════════════════════════════════════════════
# RUST APPLICATION
# ═══════════════════════════════════════════════════════════

FROM rust:1.75 AS builder

WORKDIR /app

# Copy manifest files
COPY Cargo.toml Cargo.lock ./

# Build dependencies only (cached layer!)
RUN mkdir src && \
    echo "fn main() {}" > src/main.rs && \
    cargo build --release && \
    rm -rf src

# Copy actual source
COPY src ./src

# Build application
RUN touch src/main.rs && \
    cargo build --release

# Runtime stage
FROM debian:bookworm-slim

RUN apt-get update && \
    apt-get install -y --no-install-recommends ca-certificates && \
    rm -rf /var/lib/apt/lists/*

COPY --from=builder /app/target/release/myapp /usr/local/bin/myapp

EXPOSE 8080

CMD ["myapp"]

# ═══════════════════════════════════════════════════════════
# .NET APPLICATION
# ═══════════════════════════════════════════════════════════

FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build

WORKDIR /src

COPY ["MyApp.csproj", "./"]
RUN dotnet restore

COPY . .
RUN dotnet publish -c Release -o /app/publish

FROM mcr.microsoft.com/dotnet/aspnet:8.0

WORKDIR /app

COPY --from=build /app/publish .

EXPOSE 80

ENTRYPOINT ["dotnet", "MyApp.dll"]
```

---

### Dockerfile Optimization Checklist

```yaml
# ═══════════════════════════════════════════════════════════
# DOCKERFILE OPTIMIZATION CHECKLIST
# ═══════════════════════════════════════════════════════════

Size Optimization:
  ✅ Use alpine or slim base images
  ✅ Multi-stage builds
  ✅ Combine RUN commands
  ✅ Remove cache in same layer
  ✅ Use .dockerignore
  ✅ Don't install unnecessary packages
  ✅ Clean package manager cache

  Example Size Reduction:
    Before: 1.2 GB (node:20 + all files)
    After: 150 MB (node:20-alpine + multi-stage)
    Savings: 87%! 🎉

Build Speed:
  ✅ Order layers by change frequency
  ✅ Copy dependencies before code
  ✅ Use BuildKit cache mounts
  ✅ Leverage layer caching
  ✅ Parallel multi-stage builds

  Example Time Reduction:
    Before: 5 minutes (every build)
    After: 10 seconds (with cache)
    Savings: 97%! ⚡

Security:
  ✅ Use official base images
  ✅ Pin specific versions (not latest)
  ✅ Run as non-root user
  ✅ Don't include secrets
  ✅ Scan for vulnerabilities
  ✅ Minimal base (distroless, scratch)
  ✅ Update base images regularly

Reliability:
  ✅ Add health checks
  ✅ Handle signals properly
  ✅ One process per container
  ✅ Log to stdout/stderr
  ✅ Graceful shutdown support
  ✅ Use ENTRYPOINT + CMD

Maintainability:
  ✅ Add metadata labels
  ✅ Document exposed ports
  ✅ Comment complex instructions
  ✅ Use consistent naming
  ✅ Version control Dockerfiles
  ✅ Use ARG for build-time config
```

---

<div align="center">

## 🔗 Docker Compose

_Multi-container orchestration made easy_ 🎼

</div>

### Docker Compose Fundamentals

```yaml
# ═══════════════════════════════════════════════════════════
# DOCKER COMPOSE FILE STRUCTURE
# docker-compose.yml
# ═══════════════════════════════════════════════════════════

version: "3.8" # Compose file version (optional in v2)

# Define services (containers)
services:
  # Service name (becomes hostname in network)
  web:
    # Build from Dockerfile
    build:
      context: .
      dockerfile: Dockerfile
      args:
        NODE_VERSION: 20
      target: production

    # OR use pre-built image
    image: nginx:alpine

    # Container name (optional)
    container_name: my-web-app

    # Port mapping (HOST:CONTAINER)
    ports:
      - "3000:3000"
      - "3001:3001"

    # Environment variables
    environment:
      NODE_ENV: production
      DATABASE_URL: postgres://user:pass@db:5432/mydb
      # Or from .env file
    env_file:
      - .env
      - .env.production

    # Volumes (data persistence)
    volumes:
      - ./src:/app/src # Bind mount (dev)
      - node_modules:/app/node_modules # Named volume
      - /app/data # Anonymous volume

    # Networks
    networks:
      - frontend
      - backend

    # Dependencies (start order)
    depends_on:
      - db
      - redis

    # Healthcheck
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:3000/health"]
      interval: 30s
      timeout: 10s
      retries: 3
      start_period: 40s

    # Restart policy
    restart: unless-stopped
    # Options: no, always, on-failure, unless-stopped

    # Resource limits
    deploy:
      resources:
        limits:
          cpus: "2"
          memory: 1G
        reservations:
          cpus: "1"
          memory: 512M

    # Command override
    command: npm run dev

    # Logging
    logging:
      driver: "json-file"
      options:
        max-size: "10m"
        max-file: "3"

# Define volumes
volumes:
  node_modules:
  postgres-data:
  redis-data:

# Define networks
networks:
  frontend:
  backend:
    driver: bridge
```

---

### Complete Full-Stack Example

```yaml
# ═══════════════════════════════════════════════════════════
# FULL-STACK APPLICATION
# docker-compose.yml
# ═══════════════════════════════════════════════════════════

version: "3.8"

services:
  # ───────────────────────────────────────────────────────
  # Frontend (React/Next.js)
  # ───────────────────────────────────────────────────────
  frontend:
    build:
      context: ./frontend
      dockerfile: Dockerfile
      target: development
    container_name: frontend
    ports:
      - "3000:3000"
    environment:
      - NEXT_PUBLIC_API_URL=http://localhost:4000
      - NEXT_PUBLIC_WS_URL=ws://localhost:4000
    volumes:
      - ./frontend/src:/app/src
      - ./frontend/public:/app/public
      - frontend_node_modules:/app/node_modules
    depends_on:
      - backend
    networks:
      - app-network
    command: npm run dev
    restart: unless-stopped

  # ───────────────────────────────────────────────────────
  # Backend API (Node.js/Express/NestJS)
  # ───────────────────────────────────────────────────────
  backend:
    build:
      context: ./backend
      dockerfile: Dockerfile
    container_name: backend
    ports:
      - "4000:4000"
    environment:
      NODE_ENV: development
      PORT: 4000
      DATABASE_URL: postgres://postgres:password@db:5432/myapp
      REDIS_URL: redis://redis:6379
      JWT_SECRET: ${JWT_SECRET}
    volumes:
      - ./backend/src:/app/src
      - backend_node_modules:/app/node_modules
      - ./backend/uploads:/app/uploads
    depends_on:
      db:
        condition: service_healthy
      redis:
        condition: service_started
    networks:
      - app-network
    command: npm run dev
    restart: unless-stopped
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:4000/health"]
      interval: 10s
      timeout: 5s
      retries: 5

  # ───────────────────────────────────────────────────────
  # PostgreSQL Database
  # ───────────────────────────────────────────────────────
  db:
    image: postgres:15-alpine
    container_name: postgres
    ports:
      - "5432:5432"
    environment:
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: password
      POSTGRES_DB: myapp
      POSTGRES_INITDB_ARGS: "-E UTF8 --locale=en_US.UTF-8"
    volumes:
      - postgres_data:/var/lib/postgresql/data
      - ./database/init.sql:/docker-entrypoint-initdb.d/init.sql
    networks:
      - app-network
    restart: unless-stopped
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U postgres"]
      interval: 5s
      timeout: 5s
      retries: 5

  # ───────────────────────────────────────────────────────
  # Redis Cache
  # ───────────────────────────────────────────────────────
  redis:
    image: redis:7-alpine
    container_name: redis
    ports:
      - "6379:6379"
    command: redis-server --appendonly yes --requirepass ${REDIS_PASSWORD}
    volumes:
      - redis_data:/data
    networks:
      - app-network
    restart: unless-stopped
    healthcheck:
      test: ["CMD", "redis-cli", "ping"]
      interval: 5s
      timeout: 3s
      retries: 5

  # ───────────────────────────────────────────────────────
  # Nginx Reverse Proxy
  # ───────────────────────────────────────────────────────
  nginx:
    image: nginx:alpine
    container_name: nginx
    ports:
      - "80:80"
      - "443:443"
    volumes:
      - ./nginx/nginx.conf:/etc/nginx/nginx.conf:ro
      - ./nginx/ssl:/etc/nginx/ssl:ro
    depends_on:
      - frontend
      - backend
    networks:
      - app-network
    restart: unless-stopped

  # ───────────────────────────────────────────────────────
  # Worker (Background Jobs)
  # ───────────────────────────────────────────────────────
  worker:
    build:
      context: ./backend
      dockerfile: Dockerfile
    container_name: worker
    environment:
      NODE_ENV: development
      DATABASE_URL: postgres://postgres:password@db:5432/myapp
      REDIS_URL: redis://redis:6379
    volumes:
      - ./backend/src:/app/src
      - backend_node_modules:/app/node_modules
    depends_on:
      - db
      - redis
    networks:
      - app-network
    command: npm run worker
    restart: unless-stopped

  # ───────────────────────────────────────────────────────
  # Adminer (Database UI) - Development Only
  # ───────────────────────────────────────────────────────
  adminer:
    image: adminer:latest
    container_name: adminer
    ports:
      - "8080:8080"
    environment:
      ADMINER_DEFAULT_SERVER: db
    depends_on:
      - db
    networks:
      - app-network
    profiles:
      - dev # Only start with --profile dev

  # ───────────────────────────────────────────────────────
  # Mailhog (Email Testing) - Development Only
  # ───────────────────────────────────────────────────────
  mailhog:
    image: mailhog/mailhog:latest
    container_name: mailhog
    ports:
      - "1025:1025" # SMTP
      - "8025:8025" # Web UI
    networks:
      - app-network
    profiles:
      - dev

volumes:
  postgres_data:
    driver: local
  redis_data:
    driver: local
  frontend_node_modules:
  backend_node_modules:

networks:
  app-network:
    driver: bridge
    ipam:
      config:
        - subnet: 172.20.0.0/16
```

---

### Docker Compose Commands

```bash
# ═══════════════════════════════════════════════════════════
# DOCKER COMPOSE V2 COMMANDS
# ═══════════════════════════════════════════════════════════

# Start all services
docker compose up
docker compose up -d  # Detached (background)

# Start specific services
docker compose up web db
docker compose up -d frontend backend

# Build and start
docker compose up --build
docker compose up -d --build --force-recreate

# Start with profile
docker compose --profile dev up -d

# View logs
docker compose logs
docker compose logs -f  # Follow
docker compose logs -f web  # Specific service
docker compose logs --tail=100 web

# List running services
docker compose ps
docker compose ps -a  # All (including stopped)

# Execute command in service
docker compose exec web bash
docker compose exec -u root db psql -U postgres
docker compose exec backend npm test

# Run one-off command
docker compose run --rm web npm install
docker compose run --rm backend python manage.py migrate

# Stop services
docker compose stop
docker compose stop web  # Specific service

# Start stopped services
docker compose start
docker compose start web

# Restart services
docker compose restart
docker compose restart web db

# Pause services (freeze)
docker compose pause
docker compose unpause

# Stop and remove
docker compose down
docker compose down -v  # Also remove volumes
docker compose down --rmi all  # Also remove images

# View service config
docker compose config
docker compose config --services  # List services

# Scale services
docker compose up -d --scale web=3
docker compose up -d --scale worker=5

# Pull images
docker compose pull
docker compose pull web db

# Build images
docker compose build
docker compose build --no-cache web
docker compose build --parallel

# View resource usage
docker compose top
docker compose top web

# View port mappings
docker compose port web 3000

# Validate compose file
docker compose config -q  # Returns 0 if valid

# Create and start in one command
docker compose up -d --remove-orphans

# ═══════════════════════════════════════════════════════════
# ENVIRONMENT-SPECIFIC COMPOSE FILES
# ═══════════════════════════════════════════════════════════

# Base file
docker-compose.yml

# Override for development
docker-compose.override.yml  # Loaded automatically

# Production override
docker compose -f docker-compose.yml -f docker-compose.prod.yml up -d

# Testing override
docker compose -f docker-compose.yml -f docker-compose.test.yml up

# Example structure:
# docker-compose.yml          - Base configuration
# docker-compose.override.yml - Development (auto-loaded)
# docker-compose.prod.yml     - Production overrides
# docker-compose.test.yml     - Testing overrides

# ═══════════════════════════════════════════════════════════
# USEFUL ONE-LINERS
# ═══════════════════════════════════════════════════════════

# Rebuild and restart specific service
docker compose up -d --build --force-recreate web

# View logs from all services with timestamps
docker compose logs -f -t

# Execute psql in database
docker compose exec db psql -U postgres -d myapp

# Backup database
docker compose exec -T db pg_dump -U postgres myapp > backup.sql

# Restore database
docker compose exec -T db psql -U postgres myapp < backup.sql

# Clean up everything
docker compose down -v --rmi all --remove-orphans

# Check service health
docker compose ps --format json | jq '.[] | {name: .Name, health: .Health}'
```

<div align="center">

## 🌐 Networking

_Connecting containers like a pro_ 🔌

</div>

### Docker Network Types

```
🌐 DOCKER NETWORK DRIVERS:

┌─────────────────────────────────────────────────────────┐
│                    NETWORK TYPES                         │
└─────────────────────────────────────────────────────────┘

1. BRIDGE (Default)
   ┌──────────────────────────────────────────┐
   │         Host Machine                     │
   │  ┌────────────────────────────────┐      │
   │  │    Docker Bridge Network       │      │
   │  │    (172.17.0.0/16)            │      │
   │  │  ┌──────────┐  ┌──────────┐   │      │
   │  │  │Container1│  │Container2│   │      │
   │  │  │172.17.0.2│  │172.17.0.3│   │      │
   │  │  └──────────┘  └──────────┘   │      │
   │  └────────────────────────────────┘      │
   │           ↕                               │
   │    Host Network Interface                │
   └──────────────────────────────────────────┘

   • Isolated from host
   • Containers can talk to each other
   • Need port mapping (-p) for external access
   • Best for: Single-host deployments

2. HOST (No Isolation)
   ┌──────────────────────────────────────────┐
   │         Host Machine                     │
   │  ┌──────────┐                            │
   │  │Container │  Uses host's network!     │
   │  │localhost │  No port mapping needed   │
   │  └──────────┘                            │
   │                                          │
   │  Host Network Interface                 │
   └──────────────────────────────────────────┘

   • Container shares host's network stack
   • No port mapping needed
   • Better performance (no NAT)
   • Best for: Performance-critical apps

3. NONE (No Network)
   ┌──────────────────────────────────────────┐
   │         Host Machine                     │
   │  ┌──────────┐                            │
   │  │Container │  Completely isolated!     │
   │  │ (no net) │  No network access        │
   │  └──────────┘                            │
   └──────────────────────────────────────────┘

   • No network connectivity
   • Maximum isolation
   • Best for: Security-sensitive tasks

4. OVERLAY (Multi-Host)
   ┌──────────────────────┐  ┌──────────────────────┐
   │    Host 1            │  │    Host 2            │
   │  ┌──────────┐        │  │  ┌──────────┐        │
   │  │Container1│────────┼──┼──│Container2│        │
   │  └──────────┘        │  │  └──────────┘        │
   └──────────────────────┘  └──────────────────────┘
           Encrypted tunnel (VXLAN)

   • Spans multiple Docker hosts
   • Requires Docker Swarm or Kubernetes
   • Encrypted by default
   • Best for: Multi-host orchestration

5. MACVLAN (Direct NIC Access)
   ┌──────────────────────────────────────────┐
   │         Host Machine                     │
   │  ┌──────────┐  ┌──────────┐             │
   │  │Container1│  │Container2│             │
   │  │10.0.0.10 │  │10.0.0.11 │             │
   │  └──────────┘  └──────────┘             │
   │           ↕          ↕                    │
   │    Physical Network (10.0.0.0/24)       │
   └──────────────────────────────────────────┘

   • Containers get MAC addresses
   • Appear as physical devices on network
   • No port mapping needed
   • Best for: Legacy app migration
```

---

### Network Management Commands

```bash
# ═══════════════════════════════════════════════════════════
# NETWORK OPERATIONS
# ═══════════════════════════════════════════════════════════

# List networks
docker network ls

# Inspect network
docker network inspect bridge
docker network inspect mynetwork -f '{{json .Containers}}'

# Create custom bridge network
docker network create mynetwork
docker network create --driver bridge --subnet 192.168.1.0/24 mynetwork

# Create network with options
docker network create \
  --driver=bridge \
  --subnet=172.28.0.0/16 \
  --ip-range=172.28.5.0/24 \
  --gateway=172.28.5.254 \
  mynetwork

# Connect container to network
docker network connect mynetwork container-name

# Connect with specific IP
docker network connect --ip 172.28.5.10 mynetwork container-name

# Disconnect container from network
docker network disconnect mynetwork container-name

# Remove network
docker network rm mynetwork

# Remove unused networks
docker network prune

# ═══════════════════════════════════════════════════════════
# RUNNING CONTAINERS WITH NETWORKS
# ═══════════════════════════════════════════════════════════

# Run with custom network
docker run -d --name web --network mynetwork nginx

# Run with multiple networks
docker run -d --name app \
  --network frontend \
  --network backend \
  myapp

# Run with host network
docker run -d --network host nginx
# Access at host's ports directly!

# Run with no network
docker run -d --network none alpine

# Run with specific IP
docker run -d --name web \
  --network mynetwork \
  --ip 172.28.5.100 \
  nginx

# Run with hostname
docker run -d --name web \
  --network mynetwork \
  --hostname webserver \
  nginx

# Run with DNS settings
docker run -d --name web \
  --network mynetwork \
  --dns 8.8.8.8 \
  --dns 8.8.4.4 \
  nginx

# ═══════════════════════════════════════════════════════════
# PORT MAPPING (Bridge Network)
# ═══════════════════════════════════════════════════════════

# Map single port (HOST:CONTAINER)
docker run -d -p 8080:80 nginx
# Access: http://localhost:8080

# Map multiple ports
docker run -d \
  -p 8080:80 \
  -p 8443:443 \
  nginx

# Map to specific interface
docker run -d -p 127.0.0.1:8080:80 nginx
# Only accessible from localhost

# Map random host port
docker run -d -P nginx
# Docker assigns random port

# UDP port
docker run -d -p 53:53/udp dns-server

# Map range of ports
docker run -d -p 8000-8010:8000-8010 myapp

# ═══════════════════════════════════════════════════════════
# CONTAINER DNS & SERVICE DISCOVERY
# ═══════════════════════════════════════════════════════════

# Create network
docker network create mynetwork

# Run database
docker run -d --name db --network mynetwork postgres

# Run API (can connect to "db" hostname!)
docker run -d --name api --network mynetwork \
  -e DATABASE_URL=postgres://user:pass@db:5432/mydb \
  myapi

# Inside api container:
# ping db          → Works!
# curl http://db:5432  → Works!

# Docker's built-in DNS resolves container names! 🎉

# Add network alias
docker run -d --name api \
  --network mynetwork \
  --network-alias api-server \
  myapi

# Now accessible as both "api" and "api-server"

# ═══════════════════════════════════════════════════════════
# INSPECT CONTAINER NETWORKING
# ═══════════════════════════════════════════════════════════

# Get container's IP address
docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' container-name

# Get all network info
docker inspect container-name | jq '.[0].NetworkSettings'

# View port mappings
docker port container-name

# Test connectivity
docker exec container1 ping container2
docker exec web curl http://api:3000/health
```

---

### Network Examples

```yaml
# ═══════════════════════════════════════════════════════════
# DOCKER COMPOSE NETWORKING EXAMPLES
# ═══════════════════════════════════════════════════════════

# Example 1: Simple Network (Default)
version: "3.8"

services:
  web:
    image: nginx
    ports:
      - "80:80"

  api:
    image: myapi
    # Accessible as "api" from web container

# Both on default network automatically!

# ─────────────────────────────────────────────────────────

# Example 2: Multiple Networks (Isolation)
version: "3.8"

services:
  frontend:
    image: react-app
    networks:
      - frontend-net

  backend:
    image: api
    networks:
      - frontend-net  # Can talk to frontend
      - backend-net   # Can talk to database

  database:
    image: postgres
    networks:
      - backend-net  # ONLY accessible from backend
    # frontend CANNOT access database directly!

networks:
  frontend-net:
  backend-net:

# ─────────────────────────────────────────────────────────

# Example 3: Custom Network Config
version: "3.8"

services:
  web:
    image: nginx
    networks:
      app-net:
        ipv4_address: 172.20.0.10
        aliases:
          - web-server
          - nginx-server

networks:
  app-net:
    driver: bridge
    ipam:
      config:
        - subnet: 172.20.0.0/16
          gateway: 172.20.0.1

# ─────────────────────────────────────────────────────────

# Example 4: External Network (Pre-existing)
version: "3.8"

services:
  app:
    image: myapp
    networks:
      - existing-network

networks:
  existing-network:
    external: true
    name: my-existing-network

# ─────────────────────────────────────────────────────────

# Example 5: Host Network (Performance)
version: "3.8"

services:
  app:
    image: myapp
    network_mode: host
    # Uses host's network stack
    # No port mapping needed!
```

---

<div align="center">

## 💾 Volumes & Storage

_Persistent data management_ 📂

</div>

### Volume Types Explained

```
💾 DOCKER STORAGE OPTIONS:

┌─────────────────────────────────────────────────────────┐
│                    VOLUME TYPES                          │
└─────────────────────────────────────────────────────────┘

1. NAMED VOLUMES (Recommended for Production)
   ┌──────────────────────────────────────────┐
   │         Host Machine                     │
   │  ┌────────────────────────────────┐      │
   │  │ /var/lib/docker/volumes/       │      │
   │  │   mydata/_data/                │      │
   │  │   ├─ file1.txt                 │      │
   │  │   └─ file2.txt                 │      │
   │  └────────────────────────────────┘      │
   │           ↕                               │
   │  ┌──────────────────────┐                │
   │  │ Container            │                │
   │  │ /app/data            │                │
   │  │ ├─ file1.txt         │                │
   │  │ └─ file2.txt         │                │
   │  └──────────────────────┘                │
   └──────────────────────────────────────────┘

   • Managed by Docker
   • Persists after container deletion
   • Can be shared between containers
   • Backup-friendly
   • Best for: Databases, uploads, logs

2. BIND MOUNTS (Dev & Config)
   ┌──────────────────────────────────────────┐
   │         Host Machine                     │
   │  ┌────────────────────────────────┐      │
   │  │ /home/user/project/src/        │      │
   │  │   ├─ app.js                    │      │
   │  │   └─ index.js                  │      │
   │  └────────────────────────────────┘      │
   │           ↕ (Direct mapping!)            │
   │  ┌──────────────────────┐                │
   │  │ Container            │                │
   │  │ /app/src             │                │
   │  │ ├─ app.js            │ ← Same files! │
   │  │ └─ index.js          │                │
   │  └──────────────────────┘                │
   └──────────────────────────────────────────┘

   • Direct mapping to host path
   • Changes reflect immediately
   • Host filesystem exposed
   • Best for: Development, config files

3. TMPFS MOUNTS (In-Memory)
   ┌──────────────────────────────────────────┐
   │         Host Machine                     │
   │  ┌────────────────────────────────┐      │
   │  │ RAM Memory                     │      │
   │  │ (temporary, fast!)             │      │
   │  └────────────────────────────────┘      │
   │           ↕                               │
   │  ┌──────────────────────┐                │
   │  │ Container            │                │
   │  │ /tmp/cache           │                │
   │  │ (in memory!)         │                │
   │  └──────────────────────┘                │
   └──────────────────────────────────────────┘

   • Stored in memory (RAM)
   • Not persisted to disk
   • Very fast
   • Gone on restart
   • Best for: Sensitive data, temp files

Comparison:

Feature          Named Volume    Bind Mount      tmpfs
────────────────────────────────────────────────────────
Performance      Good            Good            Excellent
Persistence      Yes             Yes             No
Portability      Excellent       Poor            N/A
Security         Good            Poor            Excellent
Docker Managed   Yes             No              Yes
Use in Prod      ✅ Yes          ❌ No           ✅ Limited
```

---

### Volume Management

```bash
# ═══════════════════════════════════════════════════════════
# VOLUME COMMANDS
# ═══════════════════════════════════════════════════════════

# Create volume
docker volume create mydata

# Create with driver options
docker volume create \
  --driver local \
  --opt type=nfs \
  --opt o=addr=192.168.1.100,rw \
  --opt device=:/path/to/dir \
  nfs-volume

# List volumes
docker volume ls

# Inspect volume
docker volume inspect mydata
docker volume inspect mydata -f '{{.Mountpoint}}'

# Remove volume
docker volume rm mydata

# Remove unused volumes
docker volume prune
docker volume prune -f  # Force, no confirmation

# ═══════════════════════════════════════════════════════════
# USING VOLUMES WITH CONTAINERS
# ═══════════════════════════════════════════════════════════

# Named volume
docker run -d \
  --name db \
  -v postgres-data:/var/lib/postgresql/data \
  postgres:15

# Bind mount (absolute path required!)
docker run -d \
  --name web \
  -v /home/user/app:/app \
  nginx

# Bind mount (current directory)
docker run -d \
  --name web \
  -v $(pwd):/app \
  nginx

# Read-only mount
docker run -d \
  -v mydata:/data:ro \
  nginx

# Tmpfs mount (in-memory)
docker run -d \
  --tmpfs /tmp:rw,noexec,nosuid,size=100m \
  nginx

# Multiple volumes
docker run -d \
  -v postgres-data:/var/lib/postgresql/data \
  -v /host/backups:/backups \
  -v /host/config:/etc/postgresql \
  postgres:15

# ═══════════════════════════════════════════════════════════
# VOLUME BACKUP & RESTORE
# ═══════════════════════════════════════════════════════════

# Backup volume to tar file
docker run --rm \
  -v mydata:/data \
  -v $(pwd):/backup \
  alpine \
  tar czf /backup/mydata-backup.tar.gz -C /data .

# Restore volume from backup
docker run --rm \
  -v mydata:/data \
  -v $(pwd):/backup \
  alpine \
  tar xzf /backup/mydata-backup.tar.gz -C /data

# Copy files from volume
docker run --rm \
  -v mydata:/data \
  -v $(pwd):/backup \
  alpine \
  cp -r /data/* /backup/

# ═══════════════════════════════════════════════════════════
# DOCKER COMPOSE VOLUMES
# ═══════════════════════════════════════════════════════════

version: "3.8"

services:
  db:
    image: postgres:15
    volumes:
      # Named volume
      - postgres-data:/var/lib/postgresql/data

      # Bind mount (config)
      - ./postgresql.conf:/etc/postgresql/postgresql.conf

      # Bind mount (init script)
      - ./init.sql:/docker-entrypoint-initdb.d/init.sql

  web:
    image: nginx
    volumes:
      # Bind mount for development
      - ./src:/usr/share/nginx/html

      # Named volume for logs
      - nginx-logs:/var/log/nginx

volumes:
  postgres-data:
    driver: local
  nginx-logs:
    driver: local

# ═══════════════════════════════════════════════════════════
# ADVANCED VOLUME OPTIONS
# ═══════════════════════════════════════════════════════════

# Volume with driver options
volumes:
  mydata:
    driver: local
    driver_opts:
      type: nfs
      o: addr=192.168.1.100,nolock,soft,rw
      device: ":/path/to/dir"

# External volume (pre-existing)
volumes:
  existing-data:
    external: true
    name: my-existing-volume

# Volume with labels
volumes:
  mydata:
    driver: local
    labels:
      environment: production
      backup: daily

# ═══════════════════════════════════════════════════════════
# VOLUME INSPECTION & DEBUGGING
# ═══════════════════════════════════════════════════════════

# Find volume location on host
docker volume inspect mydata -f '{{.Mountpoint}}'
# Output: /var/lib/docker/volumes/mydata/_data

# Access volume data (careful!)
sudo ls -la /var/lib/docker/volumes/mydata/_data

# Check volume size
docker system df -v

# List containers using volume
docker ps -a --filter volume=mydata

# ═══════════════════════════════════════════════════════════
# VOLUME BEST PRACTICES
# ═══════════════════════════════════════════════════════════

# ✅ DO: Use named volumes for data persistence
docker run -d -v postgres-data:/var/lib/postgresql/data postgres

# ✅ DO: Use bind mounts for development
docker run -d -v $(pwd)/src:/app/src node

# ✅ DO: Backup volumes regularly
docker run --rm -v mydata:/data -v $(pwd):/backup alpine tar czf /backup/backup.tar.gz /data

# ❌ DON'T: Use bind mounts in production
# ❌ DON'T: Store data in container filesystem
# ❌ DON'T: Forget to backup volumes
```

---

<div align="center">

## 🔐 Security Best Practices

_Hardening your containers_ 🛡️

</div>

### Security Checklist

```yaml
# ═══════════════════════════════════════════════════════════
# DOCKER SECURITY BEST PRACTICES
# ═══════════════════════════════════════════════════════════

1. Image Security:
   ✅ Use official base images only
   ✅ Specify exact image versions (not 'latest')
   ✅ Scan images for vulnerabilities
   ✅ Use minimal base images (alpine, distroless)
   ✅ Multi-stage builds (don't include build tools)
   ✅ Keep base images updated

   # Example: Secure base image
   FROM node:20.10.0-alpine3.19  # ✅ Specific version
   # NOT: FROM node:latest        # ❌ Unpredictable

   # Scan for vulnerabilities
   docker scan myapp:latest
   trivy image myapp:latest

2. Run as Non-Root:
   ✅ Create and use non-root user
   ✅ Never run as root (UID 0)
   ✅ Use numeric UIDs (not just usernames)

   # Dockerfile
   FROM node:20-alpine

   # Create non-root user
   RUN addgroup -g 1001 -S nodejs && \
       adduser -S nodejs -u 1001

   # Change ownership
   COPY --chown=nodejs:nodejs . /app

   # Switch to non-root
   USER nodejs

   # Verify in running container
   docker exec container-name id
   # uid=1001(nodejs) gid=1001(nodejs)

3. Secrets Management:
   ❌ NEVER: Store secrets in Dockerfile
   ❌ NEVER: Pass secrets as ENV in Dockerfile
   ❌ NEVER: Commit secrets to images

   ✅ DO: Use Docker secrets (Swarm)
   ✅ DO: Use environment variables at runtime
   ✅ DO: Use secret management tools (Vault, AWS Secrets Manager)

   # ❌ BAD:
   ENV DATABASE_PASSWORD="supersecret"
   ENV API_KEY="sk-1234567890"

   # ✅ GOOD:
   # Pass at runtime:
   docker run -e DATABASE_PASSWORD="$DB_PASS" myapp

   # Or use secrets:
   docker secret create db_password db_password.txt
   docker service create --secret db_password myapp

4. Limit Container Resources:
   ✅ Set memory limits
   ✅ Set CPU limits
   ✅ Prevent resource exhaustion

   docker run -d \
     --memory="512m" \
     --memory-swap="1g" \
     --cpus="1.5" \
     --pids-limit=100 \
     myapp

5. Read-Only Filesystem:
   ✅ Mount root filesystem as read-only
   ✅ Only allow writes to specific directories

   docker run -d \
     --read-only \
     --tmpfs /tmp:rw,noexec,nosuid,size=100m \
     myapp

6. Drop Capabilities:
   ✅ Drop all capabilities by default
   ✅ Only add what's needed

   docker run -d \
     --cap-drop=ALL \
     --cap-add=NET_BIND_SERVICE \
     myapp

7. Use Security Profiles:
   ✅ Enable AppArmor/SELinux
   ✅ Use seccomp profiles

   docker run -d \
     --security-opt=no-new-privileges \
     --security-opt=seccomp=seccomp-profile.json \
     myapp

8. Network Security:
   ✅ Use custom networks (not default bridge)
   ✅ Isolate containers by network
   ✅ Don't expose unnecessary ports

   # Create isolated networks
   docker network create frontend
   docker network create backend

   # Frontend can't access database
   docker run -d --network frontend web
   docker run -d --network backend db

9. Logging & Monitoring:
   ✅ Enable logging
   ✅ Monitor container behavior
   ✅ Set up alerts for suspicious activity

   docker run -d \
     --log-driver=json-file \
     --log-opt max-size=10m \
     --log-opt max-file=3 \
     myapp

10. Content Trust:
    ✅ Enable Docker Content Trust
    ✅ Only pull signed images

    export DOCKER_CONTENT_TRUST=1
    docker pull nginx:latest  # Verifies signature
```

---

### Security Scanning

```bash
# ═══════════════════════════════════════════════════════════
# VULNERABILITY SCANNING
# ═══════════════════════════════════════════════════════════

# Docker Scout (built-in Docker Desktop)
docker scout cves myapp:latest
docker scout recommendations myapp:latest

# Trivy (comprehensive scanner)
trivy image myapp:latest
trivy image --severity HIGH,CRITICAL myapp:latest
trivy image --format json myapp:latest > scan-results.json

# Snyk
snyk container test myapp:latest
snyk container monitor myapp:latest

# Grype
grype myapp:latest

# ═══════════════════════════════════════════════════════════
# DOCKERFILE LINTING
# ═══════════════════════════════════════════════════════════

# Hadolint (Dockerfile linter)
hadolint Dockerfile

# Example output:
# DL3008: Pin versions in apt-get install
# DL3009: Delete apt-get lists after installing
# DL3059: Multiple consecutive RUN instructions

# Fix issues:
# Before:
RUN apt-get update && apt-get install -y curl

# After:
RUN apt-get update && \
    apt-get install -y curl=7.68.0-1ubuntu2 && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# ═══════════════════════════════════════════════════════════
# RUNTIME SECURITY
# ═══════════════════════════════════════════════════════════

# Run with security options
docker run -d \
  --read-only \
  --tmpfs /tmp:rw,noexec,nosuid,size=100m \
  --cap-drop=ALL \
  --cap-add=NET_BIND_SERVICE \
  --security-opt=no-new-privileges \
  --pids-limit=100 \
  --memory="512m" \
  --cpus="1" \
  myapp

# Docker Compose security
version: "3.8"

services:
  app:
    image: myapp:latest
    read_only: true
    tmpfs:
      - /tmp:rw,noexec,nosuid,size=100m
    cap_drop:
      - ALL
    cap_add:
      - NET_BIND_SERVICE
    security_opt:
      - no-new-privileges:true
    deploy:
      resources:
        limits:
          cpus: '1'
          memory: 512M
    user: "1001:1001"  # Non-root!
```

---

<div align="center">

## ⚡ Performance Optimization

_Making Docker blazing fast_ 🚀

</div>

### Build Performance

```bash
# ═══════════════════════════════════════════════════════════
# FASTER DOCKER BUILDS
# ═══════════════════════════════════════════════════════════

# 1. Enable BuildKit (NEW Docker builder)
export DOCKER_BUILDKIT=1
export COMPOSE_DOCKER_CLI_BUILD=1

# Add to ~/.bashrc or ~/.zshrc to make permanent
echo 'export DOCKER_BUILDKIT=1' >> ~/.bashrc

# 2. Use BuildKit cache mounts
FROM node:20-alpine

WORKDIR /app

COPY package*.json ./

# Cache npm dependencies between builds!
RUN --mount=type=cache,target=/root/.npm \
    npm ci --only=production

COPY . .

CMD ["node", "server.js"]

# Result: npm install only runs when package.json changes!

# 3. Layer caching optimization
# Order Dockerfile by change frequency:

FROM node:20-alpine
WORKDIR /app

# 1. Base dependencies (rarely change)
RUN apk add --no-cache python3 g++ make

# 2. Package dependencies (change occasionally)
COPY package*.json ./
RUN npm ci

# 3. Application code (changes frequently)
COPY . .

# Build
RUN npm run build

CMD ["node", "dist/server.js"]

# 4. Use .dockerignore
# Create .dockerignore file:
node_modules
npm-debug.log
.git
.gitignore
.env
.env.local
README.md
.vscode
.idea
coverage
.nyc_output
*.log
.DS_Store
Dockerfile
docker-compose.yml

# Result: Smaller context = faster uploads to Docker daemon

# 5. Multi-stage builds
# Build stage includes everything
# Final stage only has runtime needs

FROM node:20 AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

FROM node:20-alpine
WORKDIR /app
COPY --from=builder /app/dist ./dist
COPY --from=builder /app/node_modules ./node_modules
CMD ["node", "dist/server.js"]

# Result: 1.2 GB → 150 MB (90% smaller!)

# ═══════════════════════════════════════════════════════════
# BUILD PERFORMANCE COMPARISON
# ═══════════════════════════════════════════════════════════

Without optimization:
  Build time: 5 minutes
  Image size: 1.2 GB
  Upload time: 2 minutes

With optimization:
  Build time: 10 seconds (with cache)
  Image size: 150 MB
  Upload time: 15 seconds

Savings: 95% faster, 90% smaller! 🎉
```

---

### Runtime Performance

```bash
# ═══════════════════════════════════════════════════════════
# CONTAINER RUNTIME OPTIMIZATION
# ═══════════════════════════════════════════════════════════

# 1. Resource limits (prevent resource hogging)
docker run -d \
  --memory="1g" \
  --memory-reservation="750m" \
  --cpus="2" \
  --cpu-shares=1024 \
  myapp

# 2. Storage driver optimization
# Check current driver
docker info | grep "Storage Driver"

# Best drivers:
# - overlay2 (default, recommended)
# - btrfs (on Btrfs filesystem)
# - zfs (on ZFS filesystem)

# Configure in /etc/docker/daemon.json
{
  "storage-driver": "overlay2"
}

# 3. Logging optimization
docker run -d \
  --log-driver=json-file \
  --log-opt max-size=10m \
  --log-opt max-file=3 \
  myapp

# 4. Network performance
# Use host network for maximum performance
docker run -d --network host myapp

# Or optimize bridge network
docker network create \
  --opt com.docker.network.driver.mtu=9000 \
  mynetwork

# 5. Volume performance
# Named volumes are faster than bind mounts
docker run -d -v mydata:/data myapp  # ✅ Fast
docker run -d -v /host/path:/data myapp  # ❌ Slower

# For Mac/Windows: Use Docker volumes, not bind mounts!
# Bind mounts on Mac/Windows use osxfs/CIFS (slow)
# Volumes use VM's native filesystem (fast)

# ═══════════════════════════════════════════════════════════
# DOCKER DAEMON TUNING
# ═══════════════════════════════════════════════════════════

# Edit /etc/docker/daemon.json
{
  "log-driver": "json-file",
  "log-opts": {
    "max-size": "10m",
    "max-file": "3"
  },
  "storage-driver": "overlay2",
  "live-restore": true,
  "userland-proxy": false,
  "default-ulimits": {
    "nofile": {
      "Name": "nofile",
      "Hard": 64000,
      "Soft": 64000
    }
  }
}

# Restart Docker
sudo systemctl restart docker
```

<div align="center">

## 🛠️ Development Workflows

_Docker for local development_ 💻

</div>

### Hot Reload Development Setup

```yaml
# ═══════════════════════════════════════════════════════════
# DOCKER COMPOSE FOR DEVELOPMENT
# docker-compose.yml
# ═══════════════════════════════════════════════════════════

version: "3.8"

services:
  # ───────────────────────────────────────────────────────
  # Node.js with Hot Reload
  # ───────────────────────────────────────────────────────
  api:
    build:
      context: ./backend
      dockerfile: Dockerfile.dev # Development Dockerfile
    volumes:
      # Source code (hot reload!)
      - ./backend/src:/app/src

      # Don't overwrite node_modules
      - /app/node_modules

      # Persist uploads
      - uploads:/app/uploads

    environment:
      - NODE_ENV=development
      - PORT=3000
      - DATABASE_URL=postgres://postgres:password@db:5432/myapp
      - REDIS_URL=redis://redis:6379

    ports:
      - "3000:3000"
      - "9229:9229" # Node.js debugger

    command: npm run dev # nodemon or ts-node-dev

    depends_on:
      - db
      - redis

    # Enable debugging
    stdin_open: true
    tty: true

  # ───────────────────────────────────────────────────────
  # React with Fast Refresh
  # ───────────────────────────────────────────────────────
  frontend:
    build:
      context: ./frontend
      dockerfile: Dockerfile.dev
    volumes:
      - ./frontend/src:/app/src
      - ./frontend/public:/app/public
      - /app/node_modules

    environment:
      - CHOKIDAR_USEPOLLING=true # Fix hot reload on Windows/Mac
      - REACT_APP_API_URL=http://localhost:3000

    ports:
      - "3001:3000"

    command: npm start

    stdin_open: true

  # ───────────────────────────────────────────────────────
  # Database with Persistent Data
  # ───────────────────────────────────────────────────────
  db:
    image: postgres:15-alpine
    environment:
      POSTGRES_DB: myapp
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: password
    volumes:
      - postgres_data:/var/lib/postgresql/data
      - ./database/init.sql:/docker-entrypoint-initdb.d/init.sql
    ports:
      - "5432:5432"

  # ───────────────────────────────────────────────────────
  # Redis
  # ───────────────────────────────────────────────────────
  redis:
    image: redis:7-alpine
    ports:
      - "6379:6379"

volumes:
  postgres_data:
  uploads:
```

---

### Development Dockerfile

```dockerfile
# ═══════════════════════════════════════════════════════════
# DEVELOPMENT DOCKERFILE
# Dockerfile.dev
# ═══════════════════════════════════════════════════════════

FROM node:20-alpine

# Install development tools
RUN apk add --no-cache \
    python3 \
    g++ \
    make \
    git

WORKDIR /app

# Copy package files
COPY package*.json ./

# Install ALL dependencies (including dev)
RUN npm install

# Copy source (will be overridden by volume in dev)
COPY . .

# Expose app port
EXPOSE 3000

# Expose debugger port
EXPOSE 9229

# Development command with debugging enabled
CMD ["npm", "run", "dev"]

# For debugging:
# CMD ["node", "--inspect=0.0.0.0:9229", "src/index.js"]
```

---

### Development Commands

```bash
# ═══════════════════════════════════════════════════════════
# DEVELOPMENT WORKFLOW
# ═══════════════════════════════════════════════════════════

# Start development environment
docker compose up

# Start in background
docker compose up -d

# View logs
docker compose logs -f

# Rebuild and start (after Dockerfile changes)
docker compose up --build

# Run commands in containers
docker compose exec api npm test
docker compose exec api npm run migrate
docker compose exec api npm install new-package

# Shell access
docker compose exec api sh
docker compose exec db psql -U postgres myapp

# Restart specific service
docker compose restart api

# Stop everything
docker compose down

# Stop and remove volumes (fresh start)
docker compose down -v

# ═══════════════════════════════════════════════════════════
# DEBUGGING IN DOCKER
# ═══════════════════════════════════════════════════════════

# Node.js debugging (VS Code)
# 1. Expose debugger port in docker-compose.yml:
ports:
  - "9229:9229"

# 2. Start with inspect flag:
command: node --inspect=0.0.0.0:9229 src/index.js

# 3. VS Code launch.json:
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "node",
      "request": "attach",
      "name": "Docker: Attach to Node",
      "address": "localhost",
      "port": 9229,
      "localRoot": "${workspaceFolder}/backend/src",
      "remoteRoot": "/app/src",
      "restart": true
    }
  ]
}

# ═══════════════════════════════════════════════════════════
# DATABASE MIGRATIONS & SEEDING
# ═══════════════════════════════════════════════════════════

# Run migrations
docker compose exec api npm run migrate

# Seed database
docker compose exec api npm run seed

# Reset database (fresh start)
docker compose down -v
docker compose up -d db
sleep 5  # Wait for DB to be ready
docker compose exec api npm run migrate
docker compose exec api npm run seed

# Backup database
docker compose exec -T db pg_dump -U postgres myapp > backup.sql

# Restore database
docker compose exec -T db psql -U postgres myapp < backup.sql

# ═══════════════════════════════════════════════════════════
# USEFUL DEV ALIASES
# ═══════════════════════════════════════════════════════════

# Add to ~/.bashrc or ~/.zshrc
alias dc='docker compose'
alias dcu='docker compose up -d'
alias dcd='docker compose down'
alias dcr='docker compose restart'
alias dcl='docker compose logs -f'
alias dce='docker compose exec'
alias dcb='docker compose up --build -d'

# Usage:
# dcu          # Start services
# dcl api      # View API logs
# dce api sh   # Shell into API container
```

---

### Testing in Docker

```yaml
# ═══════════════════════════════════════════════════════════
# TESTING WITH DOCKER COMPOSE
# docker-compose.test.yml
# ═══════════════════════════════════════════════════════════

version: "3.8"

services:
  # ───────────────────────────────────────────────────────
  # Test Runner
  # ───────────────────────────────────────────────────────
  test:
    build:
      context: .
      dockerfile: Dockerfile.test
    environment:
      NODE_ENV: test
      DATABASE_URL: postgres://postgres:password@test-db:5432/test_db
      REDIS_URL: redis://test-redis:6379
    depends_on:
      test-db:
        condition: service_healthy
      test-redis:
        condition: service_started
    volumes:
      - ./src:/app/src
      - ./tests:/app/tests
    command: npm test

  # ───────────────────────────────────────────────────────
  # Test Database (Isolated)
  # ───────────────────────────────────────────────────────
  test-db:
    image: postgres:15-alpine
    environment:
      POSTGRES_DB: test_db
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: password
    tmpfs:
      - /var/lib/postgresql/data # In-memory (fast!)
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U postgres"]
      interval: 5s
      timeout: 5s
      retries: 5

  # ───────────────────────────────────────────────────────
  # Test Redis
  # ───────────────────────────────────────────────────────
  test-redis:
    image: redis:7-alpine
    tmpfs:
      - /data
# Run tests:
# docker compose -f docker-compose.test.yml up --abort-on-container-exit
```

```bash
# ═══════════════════════════════════════════════════════════
# TESTING COMMANDS
# ═══════════════════════════════════════════════════════════

# Run tests
docker compose -f docker-compose.test.yml up --abort-on-container-exit

# Run tests with cleanup
docker compose -f docker-compose.test.yml up --abort-on-container-exit
docker compose -f docker-compose.test.yml down -v

# Run specific test
docker compose -f docker-compose.test.yml run --rm test npm test -- user.test.js

# Run with coverage
docker compose -f docker-compose.test.yml run --rm test npm run test:coverage

# Integration tests in CI/CD
#!/bin/bash
set -e

# Start services
docker compose -f docker-compose.test.yml up -d test-db test-redis

# Wait for services to be ready
sleep 5

# Run tests
docker compose -f docker-compose.test.yml run --rm test npm test

# Cleanup
docker compose -f docker-compose.test.yml down -v
```

---

<div align="center">

## 🚢 Production Deployment

_Taking containers to production_ 🌐

</div>

### Production Docker Compose

```yaml
# ═══════════════════════════════════════════════════════════
# PRODUCTION DOCKER COMPOSE
# docker-compose.prod.yml
# ═══════════════════════════════════════════════════════════

version: "3.8"

services:
  # ───────────────────────────────────────────────────────
  # API (Production Build)
  # ───────────────────────────────────────────────────────
  api:
    image: myregistry.com/api:${VERSION:-latest}
    restart: always

    environment:
      NODE_ENV: production
      PORT: 3000
      DATABASE_URL: ${DATABASE_URL}
      REDIS_URL: ${REDIS_URL}
      JWT_SECRET: ${JWT_SECRET}

    ports:
      - "3000:3000"

    deploy:
      replicas: 3 # Multiple instances for HA
      resources:
        limits:
          cpus: "2"
          memory: 1G
        reservations:
          cpus: "1"
          memory: 512M
      restart_policy:
        condition: on-failure
        delay: 5s
        max_attempts: 3

    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:3000/health"]
      interval: 30s
      timeout: 10s
      retries: 3
      start_period: 40s

    logging:
      driver: "json-file"
      options:
        max-size: "10m"
        max-file: "3"

    networks:
      - backend

    # Security
    read_only: true
    tmpfs:
      - /tmp:rw,noexec,nosuid,size=100m
    cap_drop:
      - ALL
    cap_add:
      - NET_BIND_SERVICE
    security_opt:
      - no-new-privileges:true
    user: "1001:1001"

  # ───────────────────────────────────────────────────────
  # Nginx (Reverse Proxy + SSL)
  # ───────────────────────────────────────────────────────
  nginx:
    image: nginx:alpine
    restart: always

    ports:
      - "80:80"
      - "443:443"

    volumes:
      - ./nginx/nginx.conf:/etc/nginx/nginx.conf:ro
      - ./nginx/ssl:/etc/nginx/ssl:ro
      - nginx_cache:/var/cache/nginx

    depends_on:
      - api

    healthcheck:
      test: ["CMD", "wget", "-q", "--spider", "http://localhost/health"]
      interval: 30s
      timeout: 10s
      retries: 3

    networks:
      - backend
      - frontend

    logging:
      driver: "json-file"
      options:
        max-size: "10m"
        max-file: "3"

  # ───────────────────────────────────────────────────────
  # Database (External in Production)
  # ───────────────────────────────────────────────────────
  # Use managed database (RDS, Cloud SQL, etc.) in production!
  # This is just for reference

  db:
    image: postgres:15-alpine
    restart: always

    environment:
      POSTGRES_DB: ${DB_NAME}
      POSTGRES_USER: ${DB_USER}
      POSTGRES_PASSWORD: ${DB_PASSWORD}

    volumes:
      - postgres_data:/var/lib/postgresql/data

    # Don't expose port publicly!
    # ports:
    #   - "5432:5432"

    networks:
      - backend

    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U ${DB_USER}"]
      interval: 10s
      timeout: 5s
      retries: 5

    deploy:
      resources:
        limits:
          cpus: "2"
          memory: 2G

volumes:
  postgres_data:
    driver: local
  nginx_cache:

networks:
  frontend:
    driver: bridge
  backend:
    driver: bridge
    internal: true # No external access!
```

---

### Production Dockerfile

```dockerfile
# ═══════════════════════════════════════════════════════════
# PRODUCTION DOCKERFILE
# Dockerfile
# ═══════════════════════════════════════════════════════════

# ───────────────────────────────────────────────────────
# Stage 1: Dependencies
# ───────────────────────────────────────────────────────
FROM node:20-alpine AS deps

WORKDIR /app

# Copy package files
COPY package*.json ./

# Install production dependencies only
RUN npm ci --only=production && \
    npm cache clean --force

# ───────────────────────────────────────────────────────
# Stage 2: Build
# ───────────────────────────────────────────────────────
FROM node:20-alpine AS builder

WORKDIR /app

# Copy package files
COPY package*.json ./

# Install all dependencies (including dev)
RUN npm ci

# Copy source code
COPY . .

# Build application
RUN npm run build && \
    npm prune --production

# ───────────────────────────────────────────────────────
# Stage 3: Production
# ───────────────────────────────────────────────────────
FROM node:20-alpine AS production

# Install dumb-init (proper signal handling)
RUN apk add --no-cache dumb-init

# Create non-root user
RUN addgroup -g 1001 -S nodejs && \
    adduser -S nodejs -u 1001

WORKDIR /app

# Copy production dependencies
COPY --from=deps --chown=nodejs:nodejs /app/node_modules ./node_modules

# Copy built application
COPY --from=builder --chown=nodejs:nodejs /app/dist ./dist
COPY --from=builder --chown=nodejs:nodejs /app/package*.json ./

# Switch to non-root user
USER nodejs

# Expose port
EXPOSE 3000

# Health check
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
  CMD node healthcheck.js || exit 1

# Use dumb-init for proper signal handling
ENTRYPOINT ["dumb-init", "--"]

# Start application
CMD ["node", "dist/server.js"]
```

---

### Deployment Scripts

```bash
# ═══════════════════════════════════════════════════════════
# DEPLOYMENT SCRIPT
# deploy.sh
# ═══════════════════════════════════════════════════════════

#!/bin/bash
set -e

# Configuration
REGISTRY="myregistry.com"
IMAGE_NAME="api"
VERSION=${1:-latest}
COMPOSE_FILE="docker-compose.prod.yml"

echo "🚀 Deploying version: $VERSION"

# 1. Build image
echo "📦 Building Docker image..."
docker build -t $REGISTRY/$IMAGE_NAME:$VERSION .
docker tag $REGISTRY/$IMAGE_NAME:$VERSION $REGISTRY/$IMAGE_NAME:latest

# 2. Push to registry
echo "⬆️  Pushing to registry..."
docker push $REGISTRY/$IMAGE_NAME:$VERSION
docker push $REGISTRY/$IMAGE_NAME:latest

# 3. Pull on production server
echo "⬇️  Pulling on production..."
ssh production "docker pull $REGISTRY/$IMAGE_NAME:$VERSION"

# 4. Update and restart services
echo "🔄 Restarting services..."
ssh production "cd /app && \
  export VERSION=$VERSION && \
  docker compose -f $COMPOSE_FILE pull && \
  docker compose -f $COMPOSE_FILE up -d --no-deps api && \
  docker compose -f $COMPOSE_FILE exec api npm run migrate"

# 5. Health check
echo "🏥 Running health check..."
sleep 10
ssh production "curl -f http://localhost:3000/health || exit 1"

echo "✅ Deployment complete!"

# ═══════════════════════════════════════════════════════════
# BLUE-GREEN DEPLOYMENT
# ═══════════════════════════════════════════════════════════

#!/bin/bash
set -e

VERSION=$1
CURRENT_ENV=$(cat current_env.txt)  # "blue" or "green"
NEW_ENV=$([ "$CURRENT_ENV" == "blue" ] && echo "green" || echo "blue")

echo "🔵🟢 Deploying to $NEW_ENV environment..."

# 1. Deploy to inactive environment
docker compose -f docker-compose.$NEW_ENV.yml pull
docker compose -f docker-compose.$NEW_ENV.yml up -d

# 2. Health check
echo "🏥 Health checking $NEW_ENV..."
sleep 10
curl -f http://localhost:8001/health || exit 1  # Green on 8001

# 3. Switch traffic (update nginx/load balancer)
echo "🔄 Switching traffic to $NEW_ENV..."
./switch-traffic.sh $NEW_ENV

# 4. Monitor for issues
echo "👀 Monitoring for 60 seconds..."
sleep 60

# 5. If all good, stop old environment
echo "🛑 Stopping $CURRENT_ENV environment..."
docker compose -f docker-compose.$CURRENT_ENV.yml down

# 6. Update current environment file
echo $NEW_ENV > current_env.txt

echo "✅ Blue-Green deployment complete!"

# ═══════════════════════════════════════════════════════════
# ROLLBACK SCRIPT
# ═══════════════════════════════════════════════════════════

#!/bin/bash
set -e

PREVIOUS_VERSION=${1:-$(git describe --tags --abbrev=0 HEAD^)}

echo "⏪ Rolling back to version: $PREVIOUS_VERSION"

# 1. Pull previous version
docker pull $REGISTRY/$IMAGE_NAME:$PREVIOUS_VERSION

# 2. Update and restart
export VERSION=$PREVIOUS_VERSION
docker compose -f docker-compose.prod.yml up -d --no-deps api

# 3. Health check
sleep 10
curl -f http://localhost:3000/health || exit 1

echo "✅ Rollback complete!"
```

---

<div align="center">

## 📊 Monitoring & Logging

_Observability for containers_ 👀

</div>

### Logging Best Practices

```yaml
# ═══════════════════════════════════════════════════════════
# LOGGING CONFIGURATION
# ═══════════════════════════════════════════════════════════

services:
  app:
    image: myapp

    # Logging configuration
    logging:
      driver: "json-file"
      options:
        max-size: "10m"
        max-file: "3"
        labels: "production,api"
        env: "NODE_ENV,VERSION"

    # OR use syslog
    logging:
      driver: "syslog"
      options:
        syslog-address: "tcp://logs.mycompany.com:514"
        tag: "{{.Name}}/{{.ID}}"

    # OR use fluentd
    logging:
      driver: "fluentd"
      options:
        fluentd-address: "localhost:24224"
        tag: "docker.{{.Name}}"
```

```bash
# ═══════════════════════════════════════════════════════════
# VIEWING LOGS
# ═══════════════════════════════════════════════════════════

# View logs
docker logs container-name

# Follow logs (real-time)
docker logs -f container-name

# Last 100 lines
docker logs --tail 100 container-name

# Since timestamp
docker logs --since 2024-01-01T00:00:00 container-name

# Last hour
docker logs --since 1h container-name

# With timestamps
docker logs -t container-name

# Docker Compose logs
docker compose logs -f
docker compose logs -f api db
docker compose logs --tail=100 api
```

---

### Monitoring Stack

```yaml
# ═══════════════════════════════════════════════════════════
# MONITORING WITH PROMETHEUS + GRAFANA
# docker-compose.monitoring.yml
# ═══════════════════════════════════════════════════════════

version: "3.8"

services:
  # ───────────────────────────────────────────────────────
  # Prometheus (Metrics Collection)
  # ───────────────────────────────────────────────────────
  prometheus:
    image: prom/prometheus:latest
    container_name: prometheus

    volumes:
      - ./prometheus/prometheus.yml:/etc/prometheus/prometheus.yml
      - prometheus_data:/prometheus

    command:
      - "--config.file=/etc/prometheus/prometheus.yml"
      - "--storage.tsdb.path=/prometheus"
      - "--web.console.libraries=/usr/share/prometheus/console_libraries"
      - "--web.console.templates=/usr/share/prometheus/consoles"

    ports:
      - "9090:9090"

    restart: unless-stopped

  # ───────────────────────────────────────────────────────
  # Grafana (Visualization)
  # ───────────────────────────────────────────────────────
  grafana:
    image: grafana/grafana:latest
    container_name: grafana

    environment:
      - GF_SECURITY_ADMIN_USER=admin
      - GF_SECURITY_ADMIN_PASSWORD=admin
      - GF_USERS_ALLOW_SIGN_UP=false

    volumes:
      - grafana_data:/var/lib/grafana
      - ./grafana/provisioning:/etc/grafana/provisioning

    ports:
      - "3001:3000"

    depends_on:
      - prometheus

    restart: unless-stopped

  # ───────────────────────────────────────────────────────
  # cAdvisor (Container Metrics)
  # ───────────────────────────────────────────────────────
  cadvisor:
    image: gcr.io/cadvisor/cadvisor:latest
    container_name: cadvisor

    volumes:
      - /:/rootfs:ro
      - /var/run:/var/run:ro
      - /sys:/sys:ro
      - /var/lib/docker/:/var/lib/docker:ro
      - /dev/disk/:/dev/disk:ro

    ports:
      - "8080:8080"

    privileged: true
    restart: unless-stopped

  # ───────────────────────────────────────────────────────
  # Node Exporter (Host Metrics)
  # ───────────────────────────────────────────────────────
  node-exporter:
    image: prom/node-exporter:latest
    container_name: node-exporter

    volumes:
      - /proc:/host/proc:ro
      - /sys:/host/sys:ro
      - /:/rootfs:ro

    command:
      - "--path.procfs=/host/proc"
      - "--path.sysfs=/host/sys"
      - "--collector.filesystem.mount-points-exclude=^/(sys|proc|dev|host|etc)($$|/)"

    ports:
      - "9100:9100"

    restart: unless-stopped

  # ───────────────────────────────────────────────────────
  # Loki (Log Aggregation)
  # ───────────────────────────────────────────────────────
  loki:
    image: grafana/loki:latest
    container_name: loki

    volumes:
      - ./loki/loki-config.yml:/etc/loki/loki-config.yml
      - loki_data:/loki

    command: -config.file=/etc/loki/loki-config.yml

    ports:
      - "3100:3100"

    restart: unless-stopped

  # ───────────────────────────────────────────────────────
  # Promtail (Log Shipper)
  # ───────────────────────────────────────────────────────
  promtail:
    image: grafana/promtail:latest
    container_name: promtail

    volumes:
      - ./promtail/promtail-config.yml:/etc/promtail/promtail-config.yml
      - /var/lib/docker/containers:/var/lib/docker/containers:ro
      - /var/run/docker.sock:/var/run/docker.sock

    command: -config.file=/etc/promtail/promtail-config.yml

    depends_on:
      - loki

    restart: unless-stopped

volumes:
  prometheus_data:
  grafana_data:
  loki_data:
```

---

<div align="center">

## 🐛 Troubleshooting

_Solving common Docker issues_ 🔧

</div>

### Common Problems & Solutions

```bash
# ═══════════════════════════════════════════════════════════
# PROBLEM: Container won't start
# ═══════════════════════════════════════════════════════════

# 1. Check logs
docker logs container-name
docker logs --tail 100 container-name

# 2. Inspect container
docker inspect container-name
docker inspect container-name | jq '.[0].State'

# 3. Try running interactively
docker run -it myapp sh
# OR
docker run --entrypoint sh -it myapp

# 4. Check health status
docker inspect --format='{{json .State.Health}}' container-name | jq

# ═══════════════════════════════════════════════════════════
# PROBLEM: Port already in use
# ═══════════════════════════════════════════════════════════

# Find what's using the port
lsof -i :8080
# OR
sudo netstat -tulpn | grep :8080

# Kill process
kill -9 <PID>

# OR use different port
docker run -p 8081:80 nginx

# ═══════════════════════════════════════════════════════════
# PROBLEM: Permission denied
# ═══════════════════════════════════════════════════════════

# Check file ownership
ls -la

# Fix permissions
sudo chown -R $USER:$USER .

# Run as root (temporary fix, not recommended!)
docker run --user root myapp

# Better: Fix Dockerfile to use correct user
RUN chown -R nodejs:nodejs /app
USER nodejs

# ═══════════════════════════════════════════════════════════
# PROBLEM: Out of disk space
# ═══════════════════════════════════════════════════════════

# Check disk usage
docker system df
docker system df -v

# Clean up
docker system prune -a --volumes
docker volume prune
docker image prune -a
docker container prune

# Remove specific resources
docker rm $(docker ps -aq)  # All containers
docker rmi $(docker images -q)  # All images
docker volume rm $(docker volume ls -q)  # All volumes

# ═══════════════════════════════════════════════════════════
# PROBLEM: Container networking issues
# ═══════════════════════════════════════════════════════════

# Check if container can reach other container
docker exec container1 ping container2

# Check DNS resolution
docker exec container1 nslookup container2

# Check network configuration
docker network inspect bridge

# Test connectivity
docker exec container1 curl http://container2:3000

# Check if port is exposed
docker port container-name

# ═══════════════════════════════════════════════════════════
# PROBLEM: Build cache not working
# ═══════════════════════════════════════════════════════════

# Build without cache
docker build --no-cache -t myapp .

# Enable BuildKit for better caching
export DOCKER_BUILDKIT=1
docker build -t myapp .

# Check build history
docker history myapp

# ═══════════════════════════════════════════════════════════
# PROBLEM: Container is slow
# ═══════════════════════════════════════════════════════════

# Check resource usage
docker stats container-name

# Check host resources
docker info

# Set resource limits
docker run -d \
  --memory="1g" \
  --cpus="2" \
  myapp

# Check for disk I/O issues
docker run --rm -it alpine sh -c "dd if=/dev/zero of=/tmp/test bs=1M count=100"

# ═══════════════════════════════════════════════════════════
# PROBLEM: Can't connect to Docker daemon
# ═══════════════════════════════════════════════════════════

# Check if Docker is running
sudo systemctl status docker

# Start Docker
sudo systemctl start docker

# Add user to docker group
sudo usermod -aG docker $USER
newgrp docker

# Check Docker socket permissions
ls -la /var/run/docker.sock
sudo chmod 666 /var/run/docker.sock

# ═══════════════════════════════════════════════════════════
# PROBLEM: Container keeps restarting
# ═══════════════════════════════════════════════════════════

# Check why it's restarting
docker logs container-name
docker inspect container-name | jq '.[0].State'

# View restart count
docker inspect -f '{{.RestartCount}}' container-name

# Stop auto-restart temporarily
docker update --restart=no container-name

# Run without restart policy
docker run -d --restart=no myapp

# ═══════════════════════════════════════════════════════════
# DEBUGGING COMMANDS
# ═══════════════════════════════════════════════════════════

# Get container IP
docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' container-name

# Get all container info
docker inspect container-name

# View real-time events
docker events

# Check Docker daemon logs
journalctl -u docker

# Export container filesystem
docker export container-name > filesystem.tar

# Save image layers
docker save myapp -o myapp.tar

# Check image vulnerabilities
docker scan myapp
trivy image myapp
```

---

<div align="center">

## 💡 Best Practices

_The ultimate Docker checklist_ ✅

</div>

### Comprehensive Best Practices

```yaml
# ═══════════════════════════════════════════════════════════
# DOCKER BEST PRACTICES CHECKLIST
# ═══════════════════════════════════════════════════════════

Dockerfile: ✅ Use official base images
  ✅ Specify exact image versions (not 'latest')
  ✅ Use multi-stage builds
  ✅ Order layers by change frequency
  ✅ Combine RUN commands to reduce layers
  ✅ Use .dockerignore
  ✅ Don't install unnecessary packages
  ✅ Clean up in same layer
  ✅ Use COPY instead of ADD
  ✅ Minimize number of layers
  ✅ Add metadata labels
  ✅ Set WORKDIR
  ✅ Use ENTRYPOINT + CMD
  ✅ Add health checks
  ✅ Run as non-root user
  ✅ Pin package versions

Security: ✅ Never run as root
  ✅ Don't store secrets in images
  ✅ Scan images for vulnerabilities
  ✅ Use minimal base images
  ✅ Keep base images updated
  ✅ Enable Docker Content Trust
  ✅ Use read-only filesystem when possible
  ✅ Drop unnecessary capabilities
  ✅ Set resource limits
  ✅ Use secrets management
  ✅ Enable security profiles (AppArmor/SELinux)
  ✅ Limit container privileges
  ✅ Use private registries
  ✅ Sign and verify images

Performance: ✅ Use layer caching effectively
  ✅ Enable BuildKit
  ✅ Use cache mounts for package managers
  ✅ Optimize image size
  ✅ Use appropriate storage driver
  ✅ Set proper resource limits
  ✅ Use volumes for persistent data
  ✅ Enable log rotation
  ✅ Use host network when appropriate
  ✅ Minimize layers
  ✅ Parallel builds in CI/CD

Networking: ✅ Use custom networks (not default bridge)
  ✅ Isolate containers by network
  ✅ Don't expose unnecessary ports
  ✅ Use DNS for service discovery
  ✅ Implement network policies
  ✅ Use TLS for inter-container communication

Storage: ✅ Use named volumes for data persistence
  ✅ Use bind mounts only for development
  ✅ Don't store data in containers
  ✅ Backup volumes regularly
  ✅ Use tmpfs for sensitive temporary data
  ✅ Set volume permissions correctly

Logging & Monitoring: ✅ Log to stdout/stderr
  ✅ Configure log rotation
  ✅ Use structured logging
  ✅ Implement health checks
  ✅ Monitor resource usage
  ✅ Set up alerts
  ✅ Use centralized logging
  ✅ Track container metrics

Development: ✅ Use Docker Compose for local development
  ✅ Separate dev and prod Dockerfiles
  ✅ Enable hot reload in development
  ✅ Use environment-specific compose files
  ✅ Document setup process
  ✅ Use consistent naming conventions
  ✅ Version control everything
  ✅ Test containers before deploying

Production: ✅ Use orchestration (Kubernetes, Swarm)
  ✅ Implement rolling updates
  ✅ Have rollback strategy
  ✅ Use managed services when possible
  ✅ Implement CI/CD pipeline
  ✅ Use image registries
  ✅ Tag images properly (semantic versioning)
  ✅ Run multiple replicas
  ✅ Implement auto-scaling
  ✅ Monitor and alert
  ✅ Regular backups
  ✅ Disaster recovery plan

Maintenance: ✅ Regular security updates
  ✅ Clean up unused resources
  ✅ Monitor disk usage
  ✅ Review and update dependencies
  ✅ Audit container configurations
  ✅ Document changes
  ✅ Keep Docker updated
```

---

### Final Recommendations

```
╔════════════════════════════════════════════════════════╗
║  🐳 MRDIB'S DOCKER WISDOM                               ║
╠════════════════════════════════════════════════════════╣
║                                                         ║
║  "Docker is not just about containers.                 ║
║   It's about standardizing how we build,               ║
║   ship, and run applications."                         ║
║                                                         ║
║  Key Takeaways:                                        ║
║                                                         ║
║  1. Start Simple                                       ║
║     • Begin with basic Dockerfile                      ║
║     • Use Docker Compose for local dev                 ║
║     • Master basics before advanced features           ║
║                                                         ║
║  2. Security First                                     ║
║     • Never run as root                                ║
║     • Scan images regularly                            ║
║     • Keep secrets out of images                       ║
║                                                         ║
║  3. Optimize Everything                                ║
║     • Multi-stage builds (90% smaller!)                ║
║     • Layer caching (95% faster!)                      ║
║     • Use .dockerignore                                ║
║                                                         ║
║  4. Think Production                                   ║
║     • Health checks are mandatory                      ║
║     • Resource limits prevent disasters                ║
║     • Logging is your friend                           ║
║                                                         ║
║  5. Automate Everything                                ║
║     • CI/CD for builds                                 ║
║     • Automated testing                                ║
║     • Infrastructure as Code                           ║
║                                                         ║
║  Remember:                                             ║
║  • Containers should be ephemeral                      ║
║  • One process per container                           ║
║  • Immutable infrastructure                            ║
║  • Declarative over imperative                         ║
║                                                         ║
║  The Docker journey:                                   ║
║  Beginner → docker run                                 ║
║  Intermediate → Dockerfile + Compose                   ║
║  Advanced → Multi-stage + Optimization                 ║
║  Expert → Production + Orchestration                   ║
║                                                         ║
║  Now go containerize all the things! 🚀                ║
║                                                         ║
╚════════════════════════════════════════════════════════╝

Quick Start Recap:

1. Install Docker
   brew install --cask docker  # macOS

2. Run your first container
   docker run -d -p 80:80 nginx

3. Create Dockerfile
   FROM node:20-alpine
   WORKDIR /app
   COPY package*.json ./
   RUN npm ci
   COPY . .
   CMD ["node", "server.js"]

4. Build and run
   docker build -t myapp .
   docker run -d -p 3000:3000 myapp

5. Use Docker Compose
   docker compose up -d

6. Learn, iterate, optimize! 🎯

Resources:
• Official Docs: https://docs.docker.com
• Docker Hub: https://hub.docker.com
• Play with Docker: https://labs.play-with-docker.com
• Best Practices: https://docs.docker.com/develop/dev-best-practices/

Happy Containerizing! 🐳
```

---

<div align="center">

**Built with 🐳 by MrDib**

_Now you're a Docker expert! Go build something amazing!_ ✨

**THE END** 🎉

</div>
