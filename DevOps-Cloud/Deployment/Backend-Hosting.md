<div align="center">

# ☁️ Backend & Full-Stack Hosting - Complete Guide

### _Deploy your APIs and applications to production with confidence_ 🚀

![Backend](https://img.shields.io/badge/Backend-Production%20Ready-green?style=for-the-badge)
![PaaS](https://img.shields.io/badge/PaaS-Battle%20Tested-blue?style=for-the-badge)
![Serverless](https://img.shields.io/badge/Serverless-Scalable-orange?style=for-the-badge)
![Status](https://img.shields.io/badge/Guide-Complete-gold?style=for-the-badge)

</div>

---

## 📚 Table of Contents

- [🎯 Choosing the Right Platform](#-choosing-the-right-platform)
- [🚂 Platform-as-a-Service (PaaS)](#-platform-as-a-service-paas)
  - [Railway](#-railway)
  - [Fly.io](#️-flyio)
  - [Render](#-render)
  - [Heroku](#️-heroku)
  - [Cyclic](#-cyclic)
  - [Platform Comparison](#-platform-comparison)
- [⚡ Serverless Platforms](#-serverless-platforms)
  - [AWS Lambda](#-aws-lambda)
  - [Vercel Functions](#-vercel-functions)
  - [Netlify Functions](#-netlify-functions)
  - [Cloudflare Workers](#️-cloudflare-workers)
- [🗄️ Database Hosting](#️-database-hosting)
- [🚀 Deployment Strategies](#-deployment-strategies)
- [🔐 Security Best Practices](#-security-best-practices)
- [📊 Monitoring & Logging](#-monitoring--logging)
- [💰 Cost Optimization](#-cost-optimization)
- [🐛 Troubleshooting](#-troubleshooting)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 🎯 Choosing the Right Platform

_The decision tree for backend deployment_ 🌲

</div>

### Understanding Your Needs

```
┌─────────────────────────────────────────────────────────────┐
│           BACKEND HOSTING DECISION TREE                      │
└─────────────────────────────────────────────────────────────┘

START: What are you deploying?
   │
   ├─❓ Simple API or microservice?
   │  │
   │  ├─✅ Stateless functions → SERVERLESS (Lambda, Workers)
   │  │                          • Cold starts acceptable
   │  │                          • Unpredictable traffic
   │  │                          • Pay-per-use preferred
   │  │
   │  └─✅ Long-running process → PaaS (Railway, Fly.io, Render)
   │                              • WebSocket connections
   │                              • Background jobs
   │                              • Consistent performance
   │
   ├─❓ Need database included?
   │  │
   │  ├─✅ YES → Railway, Render, Fly.io
   │  │          • Managed PostgreSQL, MySQL, Redis
   │  │          • Automatic backups
   │  │          • Easy connection strings
   │  │
   │  └─❌ NO → Any platform works
   │             Consider separate DB hosting
   │
   ├─❓ Global edge deployment needed?
   │  │
   │  ├─✅ YES → Cloudflare Workers, Fly.io
   │  │          • CDN-like speed
   │  │          • Low latency worldwide
   │  │
   │  └─❌ NO → Regional deployment fine
   │             Railway, Render, Heroku
   │
   ├─❓ Budget constraints?
   │  │
   │  ├─💵 Free tier needed → Cyclic, Deta, Render (free tier)
   │  │                       Railway ($5 credit/month)
   │  │
   │  ├─💰 Pay-as-you-go → Serverless platforms
   │  │                    • AWS Lambda
   │  │                    • Cloudflare Workers
   │  │
   │  └─💎 Fixed monthly → PaaS platforms
   │                       • Predictable costs
   │                       • Easier budgeting
   │
   └─❓ Technical expertise?
      │
      ├─🔰 Beginner → Railway, Render, Cyclic
      │               • GitHub integration
      │               • Auto-deploy
      │               • Simple UI
      │
      ├─🧑‍💻 Intermediate → Fly.io, Vercel, Netlify
      │                   • CLI-first
      │                   • More control
      │                   • Docker support
      │
      └─🚀 Expert → AWS Lambda, Kubernetes, Self-hosted
                    • Full control
                    • Complex architectures
                    • Custom solutions

═══════════════════════════════════════════════════════════════

QUICK RECOMMENDATIONS:

🎯 Personal Projects / MVPs:
   → Railway, Render (Free tier)
   → GitHub integration, auto-deploy
   → Start free, scale later

🚀 Startups / Growing Apps:
   → Fly.io, Railway (Paid plans)
   → Flexible scaling
   → Good performance/cost ratio

🏢 Enterprise / Production:
   → AWS, Google Cloud, Azure
   → Custom infrastructure
   → Kubernetes, managed services

⚡ Serverless / APIs:
   → Cloudflare Workers (edge)
   → AWS Lambda (mature ecosystem)
   → Vercel/Netlify Functions (simple)

🌍 Global Apps:
   → Cloudflare Workers (global edge)
   → Fly.io (multi-region)
   → AWS CloudFront + Lambda@Edge
```

---

<div align="center">

## 🚂 Platform-as-a-Service (PaaS)

_Deploy from Git, focus on code, not infrastructure_ 🛠️

</div>

### 🚂 Railway

**The developer-first infrastructure platform**

```
🌐 Website → https://railway.app
🎯 Best For → Full-stack apps, APIs, databases
💰 Pricing  → $5 free credit/month, then pay-as-you-go
⚡ Speed    → Deploy in 30 seconds
🔧 Tech     → Node.js, Python, Go, Rust, Java, Ruby, .NET, Docker
```

#### 📥 Railway Setup & Deployment

```bash
# ═══════════════════════════════════════════
# INSTALLATION
# ═══════════════════════════════════════════

# Install Railway CLI
npm install -g @railway/cli

# Or via Homebrew
brew install railway

# Or via script
curl -fsSL https://railway.app/install.sh | sh

# Login
railway login

# Link existing project
railway link

# Or create new project
railway init

# ═══════════════════════════════════════════
# PROJECT STRUCTURE
# ═══════════════════════════════════════════

your-project/
├── src/
│   ├── server.js
│   └── routes/
├── package.json
├── .env.example
├── .gitignore
└── Dockerfile (optional)

# ═══════════════════════════════════════════
# ENVIRONMENT VARIABLES
# ═══════════════════════════════════════════

# Set variables via CLI
railway variables set NODE_ENV=production
railway variables set DATABASE_URL=postgres://...
railway variables set API_KEY=your-secret-key

# Or via Railway UI
# Project → Variables → Add Variable

# View variables
railway variables

# ═══════════════════════════════════════════
# DEPLOYMENT
# ═══════════════════════════════════════════

# Deploy current directory
railway up

# Deploy with custom start command
railway up --start "npm run start:prod"

# Watch logs
railway logs

# Open in browser
railway open

# Connect to production environment
railway run node

# Run commands in production context
railway run npm run migrate

# ═══════════════════════════════════════════
# DATABASE PROVISIONING
# ═══════════════════════════════════════════

# Add PostgreSQL
railway add postgresql

# Add MySQL
railway add mysql

# Add MongoDB
railway add mongodb

# Add Redis
railway add redis

# Connection string automatically available as:
# DATABASE_URL (PostgreSQL)
# MYSQLURL (MySQL)
# MONGOURL (MongoDB)
# REDISURL (Redis)
```

#### 📝 Railway Configuration

```json
// package.json
{
  "name": "my-api",
  "version": "1.0.0",
  "scripts": {
    "start": "node src/server.js",
    "dev": "nodemon src/server.js",
    "build": "tsc",
    "migrate": "node scripts/migrate.js"
  },
  "engines": {
    "node": "18.x"
  }
}
```

```toml
# railway.toml (optional - for advanced config)
[build]
builder = "NIXPACKS"
buildCommand = "npm install && npm run build"

[deploy]
startCommand = "npm start"
restartPolicyType = "ON_FAILURE"
restartPolicyMaxRetries = 10

[[deploy.healthcheckPath]]
path = "/health"

[deploy.healthcheckTimeout]
value = 100

[environments]
production = {}
staging = {}
```

#### 🎯 Railway Example: Node.js API

```javascript
// ═══════════════════════════════════════════
// src/server.js
// ═══════════════════════════════════════════

const express = require("express");
const cors = require("cors");
const helmet = require("helmet");

const app = express();

// Railway provides PORT automatically
const PORT = process.env.PORT || 3000;

// Middleware
app.use(helmet());
app.use(cors());
app.use(express.json());

// Health check endpoint (Railway uses this)
app.get("/health", (req, res) => {
  res.status(200).json({
    status: "healthy",
    timestamp: new Date().toISOString(),
    uptime: process.uptime(),
  });
});

// API routes
app.get("/api/users", async (req, res) => {
  try {
    // DATABASE_URL is automatically provided by Railway
    const users = await db.query("SELECT * FROM users");
    res.json(users);
  } catch (error) {
    console.error("Database error:", error);
    res.status(500).json({ error: "Internal server error" });
  }
});

// Start server
app.listen(PORT, "0.0.0.0", () => {
  console.log(`🚂 Railway server running on port ${PORT}`);
  console.log(`Environment: ${process.env.NODE_ENV}`);
});

// Graceful shutdown
process.on("SIGTERM", () => {
  console.log("SIGTERM received, shutting down gracefully");
  server.close(() => {
    console.log("Process terminated");
  });
});
```

```javascript
// ═══════════════════════════════════════════
// Database Connection (PostgreSQL)
// ═══════════════════════════════════════════

const { Pool } = require("pg");

// Railway automatically provides DATABASE_URL
const pool = new Pool({
  connectionString: process.env.DATABASE_URL,
  ssl:
    process.env.NODE_ENV === "production"
      ? { rejectUnauthorized: false }
      : false,
});

// Test connection
pool.query("SELECT NOW()", (err, res) => {
  if (err) {
    console.error("❌ Database connection failed:", err);
  } else {
    console.log("✅ Database connected:", res.rows[0].now);
  }
});

module.exports = pool;
```

#### 🔧 Railway Advanced Features

```bash
# ═══════════════════════════════════════════
# PRIVATE NETWORKING
# ═══════════════════════════════════════════

# Services can communicate via private network
# Example: Backend → Database
# Use: ${{SERVICE_NAME.RAILWAY_PRIVATE_DOMAIN}}

# In your environment variables:
DATABASE_URL=${{Postgres.DATABASE_URL}}
REDIS_URL=${{Redis.REDIS_URL}}

# ═══════════════════════════════════════════
# CRON JOBS
# ═══════════════════════════════════════════

# Create a separate service for cron jobs
# In railway.toml:
[deploy]
startCommand = "node scripts/cron.js"

# Or use node-cron in your app
const cron = require('node-cron');

// Run every day at midnight
cron.schedule('0 0 * * *', () => {
  console.log('Running daily cleanup job');
  // Your job logic
});

# ═══════════════════════════════════════════
# MULTIPLE ENVIRONMENTS
# ═══════════════════════════════════════════

# Create staging environment
railway environment create staging

# Switch between environments
railway environment use production
railway environment use staging

# Deploy to specific environment
railway up --environment staging

# ═══════════════════════════════════════════
# VOLUMES (PERSISTENT STORAGE)
# ═══════════════════════════════════════════

# Add volume via UI: Service → Settings → Volumes
# Mount path: /data
# Size: 1GB - 100GB

# Access in code:
const fs = require('fs');
const uploadPath = '/data/uploads';

if (!fs.existsSync(uploadPath)) {
  fs.mkdirSync(uploadPath, { recursive: true });
}

# ═══════════════════════════════════════════
# WEBHOOKS
# ═══════════════════════════════════════════

# Trigger deployments via webhook
curl -X POST https://backboard.railway.app/webhooks/v1/deploy/$PROJECT_ID/$ENVIRONMENT_ID \
  -H "Authorization: Bearer $RAILWAY_TOKEN"

# ═══════════════════════════════════════════
# CI/CD INTEGRATION
# ═══════════════════════════════════════════

# GitHub Actions example
# .github/workflows/deploy.yml
name: Deploy to Railway

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2

      - name: Install Railway
        run: npm install -g @railway/cli

      - name: Deploy
        run: railway up
        env:
          RAILWAY_TOKEN: ${{ secrets.RAILWAY_TOKEN }}
```

#### 💡 Railway Pro Tips

```bash
# ═══════════════════════════════════════════
# TIPS & BEST PRACTICES
# ═══════════════════════════════════════════

# 1. Use health checks
# Railway will restart your service if health check fails
app.get('/health', (req, res) => res.status(200).json({ status: 'ok' }));

# 2. Optimize cold starts
# Keep your Docker images small
# Use multi-stage builds

# 3. Monitor usage
railway logs --tail 100
railway status

# 4. Database backups
# Railway auto-backups PostgreSQL
# Download backup: Project → Database → Backups

# 5. Scaling
# Railway auto-scales based on:
# - CPU usage
# - Memory usage
# - Request rate

# 6. Cost optimization
# View usage: railway usage
# Set up alerts in UI

# 7. Local development
railway run npm run dev
# Runs with production environment variables

# 8. Quick debugging
railway shell
# SSH into your running container

# 9. Zero-downtime deployments
# Railway automatically handles rolling updates

# 10. Custom domains
# Project → Settings → Domains
# Add CNAME: subdomain.yourdomain.com → your-project.railway.app
```

---

### ✈️ Fly.io

**Deploy app servers close to your users**

```
🌐 Website → https://fly.io
🎯 Best For → Docker apps, global deployment, edge computing
💰 Pricing  → Free: 3 VMs, 160GB bandwidth, 3GB volume
⚡ Speed    → Deploy globally in seconds
🔧 Tech     → Any language (Docker-based), or use Dockerfile
```

#### 📥 Fly.io Setup & Deployment

```bash
# ═══════════════════════════════════════════
# INSTALLATION
# ═══════════════════════════════════════════

# macOS/Linux
curl -L https://fly.io/install.sh | sh

# Windows
powershell -Command "iwr https://fly.io/install.ps1 -useb | iex"

# Homebrew
brew install flyctl

# Verify installation
flyctl version

# Login
flyctl auth login

# Or signup
flyctl auth signup

# ═══════════════════════════════════════════
# CREATE & LAUNCH APP
# ═══════════════════════════════════════════

# Initialize Fly app (creates fly.toml)
flyctl launch

# This will:
# 1. Detect your app type
# 2. Generate Dockerfile (if needed)
# 3. Create fly.toml config
# 4. Ask about PostgreSQL database
# 5. Deploy your app

# Launch with custom config
flyctl launch --name my-app --region iad --org personal

# Available regions:
flyctl platform regions

# ═══════════════════════════════════════════
# DEPLOYMENT
# ═══════════════════════════════════════════

# Deploy app
flyctl deploy

# Deploy with custom Dockerfile
flyctl deploy --dockerfile Dockerfile.prod

# Deploy to specific region
flyctl deploy --region iad

# Force rebuild
flyctl deploy --build-only

# Deploy without building (use existing image)
flyctl deploy --image your-registry.com/image:tag

# Watch deployment logs
flyctl logs

# Stream logs in real-time
flyctl logs -f

# ═══════════════════════════════════════════
# APP MANAGEMENT
# ═══════════════════════════════════════════

# List apps
flyctl apps list

# Show app info
flyctl info

# Open app in browser
flyctl open

# SSH into running instance
flyctl ssh console

# Run command in instance
flyctl ssh console -C "node -v"

# Check app status
flyctl status

# Show app history
flyctl releases

# Rollback to previous version
flyctl releases rollback

# ═══════════════════════════════════════════
# SCALING
# ═══════════════════════════════════════════

# Scale instances (count)
flyctl scale count 3

# Scale to specific regions
flyctl scale count 2 --region iad
flyctl scale count 1 --region lhr

# Scale VM resources
flyctl scale vm shared-cpu-1x  # 256MB RAM
flyctl scale vm shared-cpu-2x  # 512MB RAM
flyctl scale vm shared-cpu-4x  # 1GB RAM
flyctl scale vm shared-cpu-8x  # 2GB RAM

# View available VM sizes
flyctl platform vm-sizes

# Auto-scaling (enterprise)
flyctl autoscale set min=2 max=10

# ═══════════════════════════════════════════
# SECRETS & ENVIRONMENT VARIABLES
# ═══════════════════════════════════════════

# Set secrets (encrypted)
flyctl secrets set DATABASE_URL=postgres://...
flyctl secrets set API_KEY=your-secret-key
flyctl secrets set NODE_ENV=production

# Set multiple secrets from file
flyctl secrets import < .env.production

# List secrets (names only, not values)
flyctl secrets list

# Unset secret
flyctl secrets unset API_KEY

# ═══════════════════════════════════════════
# VOLUMES (PERSISTENT STORAGE)
# ═══════════════════════════════════════════

# Create volume
flyctl volumes create data --region iad --size 10

# List volumes
flyctl volumes list

# Extend volume size
flyctl volumes extend vol_xyz123 --size 20

# Snapshot volume
flyctl volumes snapshots create vol_xyz123

# Delete volume
flyctl volumes delete vol_xyz123
```

#### 📝 Fly.io Configuration

```toml
# ═══════════════════════════════════════════
# fly.toml - Main Configuration
# ═══════════════════════════════════════════

app = "my-app"
primary_region = "iad"

# Build configuration
[build]
  dockerfile = "Dockerfile"
  # Or use buildpacks
  # builder = "paketobuildpacks/builder:base"

# Environment variables (non-secret)
[env]
  NODE_ENV = "production"
  PORT = "8080"

# HTTP service
[[services]]
  internal_port = 8080
  protocol = "tcp"
  auto_stop_machines = true
  auto_start_machines = true
  min_machines_running = 0

  # HTTP checks
  [[services.ports]]
    port = 80
    handlers = ["http"]
    force_https = true

  [[services.ports]]
    port = 443
    handlers = ["http", "tls"]

  # Health check
  [services.http_checks]
    interval = "10s"
    timeout = "2s"
    grace_period = "5s"
    method = "GET"
    path = "/health"
    protocol = "http"
    restart_limit = 0

  # Concurrency limits
  [services.concurrency]
    type = "connections"
    hard_limit = 25
    soft_limit = 20

# Volumes
[[mounts]]
  source = "data"
  destination = "/data"

# Metrics
[metrics]
  port = 9091
  path = "/metrics"
```

```dockerfile
# ═══════════════════════════════════════════
# Dockerfile for Fly.io
# ═══════════════════════════════════════════

# Multi-stage build for Node.js
FROM node:18-alpine AS builder

WORKDIR /app

# Copy package files
COPY package*.json ./

# Install dependencies
RUN npm ci --only=production

# Copy source code
COPY . .

# Build (if needed)
RUN npm run build

# Production stage
FROM node:18-alpine

WORKDIR /app

# Copy from builder
COPY --from=builder /app/node_modules ./node_modules
COPY --from=builder /app/dist ./dist
COPY --from=builder /app/package*.json ./

# Set environment
ENV NODE_ENV=production

# Expose port
EXPOSE 8080

# Health check
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
  CMD node -e "require('http').get('http://localhost:8080/health', (r) => { process.exit(r.statusCode === 200 ? 0 : 1); })"

# Start app
CMD ["node", "dist/server.js"]
```

#### 🎯 Fly.io Example: Node.js API

```javascript
// ═══════════════════════════════════════════
// server.js
// ═══════════════════════════════════════════

const express = require("express");
const app = express();

// Fly.io provides PORT (default 8080)
const PORT = process.env.PORT || 8080;

app.use(express.json());

// Health check (Fly.io uses this)
app.get("/health", (req, res) => {
  res.status(200).json({
    status: "healthy",
    region: process.env.FLY_REGION,
    instance: process.env.FLY_ALLOC_ID,
  });
});

// Get user's closest region
app.get("/api/region", (req, res) => {
  res.json({
    region: process.env.FLY_REGION,
    instance: process.env.FLY_ALLOC_ID,
    clientRegion: req.headers["fly-client-ip"],
  });
});

// Start server
app.listen(PORT, "0.0.0.0", () => {
  console.log(`✈️  Fly.io server running on port ${PORT}`);
  console.log(`Region: ${process.env.FLY_REGION}`);
});
```

#### 🌍 Fly.io Multi-Region Deployment

```bash
# ═══════════════════════════════════════════
# GLOBAL DEPLOYMENT
# ═══════════════════════════════════════════

# Deploy to multiple regions
flyctl regions add iad  # US East (Virginia)
flyctl regions add lhr  # Europe (London)
flyctl regions add sin  # Asia (Singapore)
flyctl regions add syd  # Australia (Sydney)

# List regions
flyctl regions list

# Scale instances per region
flyctl scale count 2 --region iad
flyctl scale count 2 --region lhr
flyctl scale count 1 --region sin
flyctl scale count 1 --region syd

# Remove region
flyctl regions remove sin

# Check instance locations
flyctl status

# ═══════════════════════════════════════════
# POSTGRES (MULTI-REGION)
# ═══════════════════════════════════════════

# Create Postgres cluster
flyctl postgres create

# Attach to app
flyctl postgres attach my-postgres-db

# Add read replicas in other regions
flyctl postgres create --region lhr --name my-postgres-replica

# Check Postgres status
flyctl postgres list
flyctl postgres db list

# Connect to Postgres
flyctl postgres connect -a my-postgres-db

# ═══════════════════════════════════════════
# REDIS (IN-APP)
# ═══════════════════════════════════════════

# Use Upstash Redis (integrated with Fly.io)
flyctl redis create

# Or self-host Redis as separate app
# Create redis-app with Redis Docker image
```

#### 💡 Fly.io Pro Tips

```bash
# ═══════════════════════════════════════════
# TIPS & BEST PRACTICES
# ═══════════════════════════════════════════

# 1. Use machines API for cost optimization
# auto_stop_machines = true in fly.toml
# Machines stop when idle, start on request

# 2. Monitor your app
flyctl dashboard
flyctl logs -f
flyctl status

# 3. Use Fly Proxy for internal services
# Services communicate via .internal DNS
# postgres-db.internal:5432

# 4. Custom domains
flyctl certs create yourdomain.com
# Add DNS: yourdomain.com CNAME your-app.fly.dev

# 5. Zero-downtime deployments
# Fly.io does rolling updates automatically
# Configure in fly.toml:
[deploy]
  strategy = "rolling"

# 6. Use Fly Replay for multi-region writes
# X-Fly-Region header for region routing

# 7. Debugging
flyctl ssh console
flyctl ssh sftp shell
flyctl doctor  # Check for issues

# 8. Monitoring & Metrics
flyctl dashboard metrics
flyctl monitoring dashboard

# 9. Cost optimization
# Use shared-cpu-1x for low-traffic apps
# Enable auto-stop for development apps
# Use fly.io-j for even cheaper instances

# 10. Backup strategy
# Snapshot volumes regularly
flyctl volumes snapshots create vol_xyz
```

---

### 🎨 Render

**Modern cloud platform with zero DevOps**

```
🌐 Website → https://render.com
🎯 Best For → Web services, static sites, cron jobs, databases
💰 Pricing  → Free tier available, then $7/month+
⚡ Speed    → Deploy from Git in minutes
🔧 Tech     → Node.js, Python, Go, Rust, Ruby, Docker
```

#### 📥 Render Setup & Deployment

```bash
# ═══════════════════════════════════════════
# NO CLI REQUIRED - UI-BASED DEPLOYMENT
# ═══════════════════════════════════════════

# 1. Connect GitHub/GitLab repo via UI
# 2. Render auto-detects app type
# 3. Configure build & start commands
# 4. Deploy!

# But if you want CLI:
# Install Render CLI (beta)
npm install -g @render/cli
render login

# Deploy
render services create
```

#### 📝 Render Configuration

```yaml
# ═══════════════════════════════════════════
# render.yaml - Infrastructure as Code
# ═══════════════════════════════════════════

services:
  # Web Service
  - type: web
    name: my-api
    env: node
    region: oregon
    plan: starter
    buildCommand: npm install && npm run build
    startCommand: npm start
    healthCheckPath: /health
    autoDeploy: true

    # Environment variables
    envVars:
      - key: NODE_ENV
        value: production
      - key: PORT
        value: 10000
      - key: DATABASE_URL
        fromDatabase:
          name: mydb
          property: connectionString
      - key: REDIS_URL
        fromService:
          type: redis
          name: myredis
          property: connectionString
      - key: API_KEY
        sync: false # Secret - set via UI

    # Scaling
    numInstances: 2

    # Custom domains
    domains:
      - api.example.com

  # Background Worker
  - type: worker
    name: my-worker
    env: node
    buildCommand: npm install
    startCommand: npm run worker
    envVars:
      - key: NODE_ENV
        value: production

  # Cron Job
  - type: cron
    name: daily-cleanup
    env: node
    schedule: "0 0 * * *" # Every day at midnight
    buildCommand: npm install
    startCommand: npm run cleanup

# Databases
databases:
  - name: mydb
    databaseName: myapp
    user: myapp_user
    plan: starter # Free tier
    region: oregon

  # Redis
  - name: myredis
    type: redis
    plan: starter
    maxmemoryPolicy: allkeys-lru
```

#### 🎯 Render Example: Environment-Specific Config

```javascript
// ═══════════════════════════════════════════
// server.js - Render Configuration
// ═══════════════════════════════════════════

const express = require("express");
const app = express();

// Render provides PORT (usually 10000)
const PORT = process.env.PORT || 3000;

// Render provides IS_PULL_REQUEST env var
const isPreview = process.env.IS_PULL_REQUEST === "true";

app.use(express.json());

// Health check endpoint
app.get("/health", (req, res) => {
  res.status(200).json({
    status: "healthy",
    environment: process.env.RENDER_SERVICE_NAME,
    region: process.env.RENDER_REGION,
    isPreview,
  });
});

// Database connection (Render provides DATABASE_URL)
const { Pool } = require("pg");
const pool = new Pool({
  connectionString: process.env.DATABASE_URL,
  ssl: { rejectUnauthorized: false },
});

// Start server
app.listen(PORT, "0.0.0.0", () => {
  console.log(`🎨 Render server running on port ${PORT}`);
  console.log(`Environment: ${process.env.NODE_ENV}`);
  console.log(`Service: ${process.env.RENDER_SERVICE_NAME}`);
});
```

#### 💡 Render Features

```bash
# ═══════════════════════════════════════════
# KEY FEATURES
# ═══════════════════════════════════════════

# 1. PREVIEW ENVIRONMENTS
# Automatic preview environment for each PR
# URL: https://my-app-pr-123.onrender.com

# 2. ZERO-DOWNTIME DEPLOYS
# Health checks before routing traffic
# Automatic rollback on failure

# 3. MANAGED DATABASES
# PostgreSQL with automatic backups
# Point-in-time recovery
# Auto-scaling storage

# 4. BACKGROUND WORKERS
# Long-running processes
# Separate scaling from web services

# 5. CRON JOBS
# Scheduled tasks
# Automatic retries
# Monitoring & alerts

# 6. STATIC SITES
# CDN-backed
# Automatic SSL
# Custom headers

# 7. PRIVATE SERVICES
# Internal-only services
# Not exposed to internet
# Inter-service communication

# 8. NOTIFICATIONS
# Deploy notifications
# Slack, Discord, email
# Webhook integration

# 9. IAC (Infrastructure as Code)
# render.yaml in repo
# GitOps workflow
# Review changes via PR

# 10. DDoS PROTECTION
# Automatic protection
# No configuration needed
```

---

### ⚙️ Heroku

**The original PaaS platform**

```
🌐 Website → https://heroku.com
🎯 Best For → Ruby, Node.js, Python, Java, mature apps
💰 Pricing  → Paid plans from $5/month (no free tier since 2022)
⚡ Speed    → Battle-tested, reliable
🔧 Tech     → Buildpacks for many languages
```

#### 📥 Heroku Setup & Deployment

```bash
# ═══════════════════════════════════════════
# INSTALLATION
# ═══════════════════════════════════════════

# Install Heroku CLI
# macOS
brew tap heroku/brew && brew install heroku

# Ubuntu
curl https://cli-assets.heroku.com/install-ubuntu.sh | sh

# Windows (via installer)
# Download from: https://devcenter.heroku.com/articles/heroku-cli

# Login
heroku login

# Or login with API key
heroku login -i

# ═══════════════════════════════════════════
# CREATE & DEPLOY APP
# ═══════════════════════════════════════════

# Create app
heroku create my-app

# Or in specific region
heroku create my-app --region eu

# Deploy
git push heroku main

# Or deploy specific branch
git push heroku develop:main

# ═══════════════════════════════════════════
# APP MANAGEMENT
# ═══════════════════════════════════════════

# List apps
heroku apps

# App info
heroku info

# Open app in browser
heroku open

# View logs
heroku logs --tail

# Restart app
heroku restart

# Run bash
heroku run bash

# Run one-off command
heroku run node scripts/migrate.js

# ═══════════════════════════════════════════
# SCALING
# ═══════════════════════════════════════════

# Scale dynos (instances)
heroku ps:scale web=2
heroku ps:scale worker=1

# Change dyno type
heroku ps:type web=standard-1x

# List dyno types
heroku ps

# ═══════════════════════════════════════════
# ENVIRONMENT VARIABLES (CONFIG VARS)
# ═══════════════════════════════════════════

# Set config var
heroku config:set NODE_ENV=production
heroku config:set DATABASE_URL=postgres://...

# List config vars
heroku config

# Get specific var
heroku config:get DATABASE_URL

# Unset var
heroku config:unset API_KEY

# ═══════════════════════════════════════════
# ADD-ONS (DATABASES, REDIS, ETC.)
# ═══════════════════════════════════════════

# Add PostgreSQL
heroku addons:create heroku-postgresql:mini

# Add Redis
heroku addons:create heroku-redis:mini

# Add Scheduler (cron jobs)
heroku addons:create scheduler:standard

# List add-ons
heroku addons

# Open add-on dashboard
heroku addons:open heroku-postgresql

# ═══════════════════════════════════════════
# DATABASES
# ═══════════════════════════════════════════

# Connect to database
heroku pg:psql

# Database info
heroku pg:info

# Run database backup
heroku pg:backups:capture

# Download backup
heroku pg:backups:download

# Restore from backup
heroku pg:backups:restore

# Reset database
heroku pg:reset DATABASE_URL
```

#### 📝 Heroku Configuration

```json
// ═══════════════════════════════════════════
// Procfile - Define process types
// ═══════════════════════════════════════════

// Procfile (no extension)
web: npm start
worker: npm run worker
release: npm run migrate
```

```json
// app.json - App manifest
{
  "name": "my-app",
  "description": "My awesome app",
  "repository": "https://github.com/user/repo",
  "keywords": ["node", "express", "api"],
  "image": "heroku/nodejs",
  "buildpacks": [
    {
      "url": "heroku/nodejs"
    }
  ],
  "env": {
    "NODE_ENV": {
      "description": "Node environment",
      "value": "production"
    },
    "NPM_CONFIG_PRODUCTION": {
      "value": "true"
    },
    "SECRET_KEY": {
      "description": "Secret key for sessions",
      "generator": "secret"
    }
  },
  "formation": {
    "web": {
      "quantity": 1,
      "size": "eco"
    }
  },
  "addons": [
    {
      "plan": "heroku-postgresql:mini"
    },
    {
      "plan": "heroku-redis:mini"
    }
  ],
  "scripts": {
    "postdeploy": "npm run migrate"
  }
}
```

#### 🎯 Heroku Example: Complete Setup

```javascript
// ═══════════════════════════════════════════
// server.js
// ═══════════════════════════════════════════

const express = require("express");
const app = express();

// Heroku provides PORT
const PORT = process.env.PORT || 3000;

app.use(express.json());

// Health check
app.get("/", (req, res) => {
  res.json({
    status: "ok",
    dyno: process.env.DYNO,
    release: process.env.HEROKU_RELEASE_VERSION,
  });
});

app.listen(PORT, () => {
  console.log(`⚙️ Heroku server running on port ${PORT}`);
});
```

```bash
# ═══════════════════════════════════════════
# .buildpacks (for multi-buildpack)
# ═══════════════════════════════════════════

heroku/nodejs
heroku/python  # If you need multiple languages
```

---

### 🔄 Cyclic

**Serverless deployment for Node.js**

```
🌐 Website → https://cyclic.sh
🎯 Best For → Node.js serverless apps
💰 Pricing  → Generous free tier, $1/month+
⚡ Speed    → Deploy from GitHub in seconds
🔧 Tech     → Node.js only (AWS Lambda + DynamoDB + S3)
```

#### 📥 Cyclic Features

```bash
# ═══════════════════════════════════════════
# KEY FEATURES
# ═══════════════════════════════════════════

# ✅ Serverless (AWS Lambda)
# ✅ Built-in DynamoDB
# ✅ Built-in S3 storage
# ✅ Custom domains
# ✅ Environment variables
# ✅ Automatic HTTPS
# ✅ GitHub integration
# ✅ No credit card needed for free tier

# Deployment:
# 1. Connect GitHub repo
# 2. Cyclic detects Node.js
# 3. Auto-deploys on push
# 4. That's it!

# Access via: https://your-app.cyclic.app
```

---

### 📊 Platform Comparison

```
═══════════════════════════════════════════════════════════════
PAAS PLATFORM COMPARISON
═══════════════════════════════════════════════════════════════

┌──────────┬───────────┬──────────────┬─────────┬──────────────┐
│ Platform │ Free Tier │ Best For     │ Pricing │ Complexity   │
├──────────┼───────────┼──────────────┼─────────┼──────────────┤
│ Railway  │ $5 credit │ Full-stack   │ Pay-go  │ ⭐⭐ Easy    │
│          │ /month    │ Quick deploy │ ~$10/mo │              │
├──────────┼───────────┼──────────────┼─────────┼──────────────┤
│ Fly.io   │ 3 VMs     │ Docker apps  │ Pay-go  │ ⭐⭐⭐ Med   │
│          │ 160GB BW  │ Global edge  │ ~$5/mo  │              │
├──────────┼───────────┼──────────────┼─────────┼──────────────┤
│ Render   │ 750hrs/mo │ Web services │ $7/mo   │ ⭐⭐ Easy    │
│          │ Static    │ Databases    │         │              │
├──────────┼───────────┼──────────────┼─────────┼──────────────┤
│ Heroku   │ None      │ Mature apps  │ $5/mo   │ ⭐⭐⭐ Med   │
│          │           │ Add-ons      │         │              │
├──────────┼───────────┼──────────────┼─────────┼──────────────┤
│ Cyclic   │ Generous  │ Node.js only │ $1/mo   │ ⭐ Very Easy │
│          │           │ Serverless   │         │              │
└──────────┴───────────┴──────────────┴─────────┴──────────────┘

RECOMMENDATION BY USE CASE:

🎯 Personal Projects / Learning
   → Cyclic, Railway (Free tier)

🚀 Startup / MVP
   → Railway, Fly.io, Render

🌍 Global App
   → Fly.io (multi-region), Cloudflare Workers

💼 Enterprise
   → Heroku, AWS, Google Cloud

🐳 Docker Apps
   → Fly.io, Railway

💰 Budget-Conscious
   → Cyclic, Deta, Render (free tier)

⚡ Serverless
   → Cyclic, Vercel, AWS Lambda

🗄️ Need Database
   → Railway, Render, Heroku
```

---

<div align="center">

## ⚡ Serverless Platforms

_Pay only for what you use, scale automatically_ 🤖

</div>

### Understanding Serverless

```
╔═══════════════════════════════════════════════════════════╗
║                  SERVERLESS EXPLAINED                      ║
╚═══════════════════════════════════════════════════════════╝

Traditional Server:
┌────────────────────────────────────────┐
│         Server Running 24/7            │
│  ┌──────────────────────────────────┐  │
│  │  Your App (Always Running)       │  │
│  │  • Paying for idle time          │  │
│  │  • Fixed capacity                │  │
│  │  • Manual scaling                │  │
│  └──────────────────────────────────┘  │
│  💰 Cost: $20-$50/month (always)      │
└────────────────────────────────────────┘

Serverless:
┌────────────────────────────────────────┐
│       Functions (Event-Driven)         │
│                                        │
│  Request 1 → 🔥 Function runs → Done  │
│  Request 2 → 🔥 Function runs → Done  │
│  No requests → 💤 Nothing running     │
│                                        │
│  • Pay per execution                  │
│  • Auto-scaling                       │
│  • Zero idle cost                     │
│  💰 Cost: $0-$5/month (usage-based)   │
└────────────────────────────────────────┘

PROS:
✅ No server management
✅ Auto-scaling (0 to ∞)
✅ Pay-per-use (cost-effective for variable traffic)
✅ High availability built-in
✅ Fast deployment

CONS:
❌ Cold starts (initial delay)
❌ Execution time limits (typically 5-15 minutes)
❌ Stateless (no persistent memory)
❌ Vendor lock-in (platform-specific)
❌ Can be expensive at high scale

BEST FOR:
• APIs with variable traffic
• Webhooks
• Scheduled tasks (cron jobs)
• Event processing
• Microservices
• Background jobs

NOT IDEAL FOR:
• WebSocket connections
• Long-running processes
• Stateful applications
• High-frequency, predictable traffic (cheaper with traditional)
```

---

### 🔶 AWS Lambda

**The OG serverless platform**

```
🌐 Website → https://aws.amazon.com/lambda
🎯 Best For → Event-driven apps, AWS ecosystem
💰 Pricing  → 1M requests + 400,000 GB-seconds free/month
⚡ Speed    → Millisecond billing, auto-scales
🔧 Tech     → Node.js, Python, Ruby, Java, Go, .NET, Rust
```

#### 📥 AWS Lambda Setup

```bash
# ═══════════════════════════════════════════
# USING AWS SAM (Serverless Application Model)
# ═══════════════════════════════════════════

# Install AWS SAM CLI
brew install aws-sam-cli

# Configure AWS credentials
aws configure

# Create new Lambda project
sam init

# Choose:
# 1. AWS Quick Start Templates
# 2. Hello World Example
# 3. Runtime: nodejs18.x
# 4. Name: my-lambda-api

# Project structure:
my-lambda-api/
├── hello-world/
│   ├── app.js           # Lambda function
│   ├── package.json
│   └── tests/
├── template.yaml        # SAM template
└── samconfig.toml

# ═══════════════════════════════════════════
# BUILD & DEPLOY
# ═══════════════════════════════════════════

# Build
sam build

# Test locally
sam local invoke HelloWorldFunction

# Start local API
sam local start-api

# Deploy to AWS
sam deploy --guided

# Watch logs
sam logs -n HelloWorldFunction --tail
```

#### 📝 AWS Lambda Function Example

```javascript
// ═══════════════════════════════════════════
// app.js - Lambda Handler
// ═══════════════════════════════════════════

exports.lambdaHandler = async (event, context) => {
  console.log("Event:", JSON.stringify(event, null, 2));

  // Parse request
  const { httpMethod, path, queryStringParameters, body } = event;

  try {
    // Handle different routes
    if (httpMethod === "GET" && path === "/api/users") {
      // Get users
      const users = await getUsers();

      return {
        statusCode: 200,
        headers: {
          "Content-Type": "application/json",
          "Access-Control-Allow-Origin": "*",
        },
        body: JSON.stringify(users),
      };
    }

    if (httpMethod === "POST" && path === "/api/users") {
      // Create user
      const userData = JSON.parse(body);
      const newUser = await createUser(userData);

      return {
        statusCode: 201,
        headers: {
          "Content-Type": "application/json",
          "Access-Control-Allow-Origin": "*",
        },
        body: JSON.stringify(newUser),
      };
    }

    // Route not found
    return {
      statusCode: 404,
      body: JSON.stringify({ error: "Not found" }),
    };
  } catch (error) {
    console.error("Error:", error);

    return {
      statusCode: 500,
      body: JSON.stringify({ error: "Internal server error" }),
    };
  }
};

// Database operations
const AWS = require("aws-sdk");
const dynamodb = new AWS.DynamoDB.DocumentClient();

async function getUsers() {
  const params = {
    TableName: process.env.USERS_TABLE,
  };

  const result = await dynamodb.scan(params).promise();
  return result.Items;
}

async function createUser(userData) {
  const params = {
    TableName: process.env.USERS_TABLE,
    Item: {
      id: Date.now().toString(),
      ...userData,
      createdAt: new Date().toISOString(),
    },
  };

  await dynamodb.put(params).promise();
  return params.Item;
}
```

```yaml
# ═══════════════════════════════════════════
# template.yaml - SAM Template
# ═══════════════════════════════════════════

AWSTemplateFormatVersion: "2010-09-09"
Transform: AWS::Serverless-2016-10-31
Description: My Lambda API

Globals:
  Function:
    Timeout: 10
    Runtime: nodejs18.x
    Environment:
      Variables:
        USERS_TABLE: !Ref UsersTable

Resources:
  # Lambda Function
  ApiFunction:
    Type: AWS::Serverless::Function
    Properties:
      CodeUri: hello-world/
      Handler: app.lambdaHandler
      Events:
        # GET /api/users
        GetUsers:
          Type: Api
          Properties:
            Path: /api/users
            Method: get
        # POST /api/users
        CreateUser:
          Type: Api
          Properties:
            Path: /api/users
            Method: post
      Policies:
        - DynamoDBCrudPolicy:
            TableName: !Ref UsersTable

  # DynamoDB Table
  UsersTable:
    Type: AWS::DynamoDB::Table
    Properties:
      TableName: Users
      AttributeDefinitions:
        - AttributeName: id
          AttributeType: S
      KeySchema:
        - AttributeName: id
          KeyType: HASH
      BillingMode: PAY_PER_REQUEST

Outputs:
  ApiUrl:
    Description: "API Gateway endpoint URL"
    Value: !Sub "https://${ServerlessRestApi}.execute-api.${AWS::Region}.amazonaws.com/Prod/"
```

#### 💡 AWS Lambda Best Practices

```javascript
// ═══════════════════════════════════════════
// OPTIMIZE COLD STARTS
// ═══════════════════════════════════════════

// 1. Keep dependencies minimal
// Only import what you need
const { DynamoDB } = require("@aws-sdk/client-dynamodb"); // ✅ Good
// const AWS = require('aws-sdk'); // ❌ Imports everything

// 2. Initialize outside handler (reused across invocations)
const dynamodb = new DynamoDB.DocumentClient();

exports.handler = async (event) => {
  // Handler code
};

// 3. Use Lambda layers for common dependencies
// SAM template:
/*
Layers:
  - arn:aws:lambda:us-east-1:123456789:layer:my-common-layer:1
*/

// 4. Increase memory (also increases CPU)
// More memory = faster execution = lower cost sometimes!
// Test different memory sizes: 128MB, 256MB, 512MB, 1024MB

// ═══════════════════════════════════════════
// ERROR HANDLING
// ═══════════════════════════════════════════

exports.handler = async (event) => {
  try {
    // Your logic
    return {
      statusCode: 200,
      body: JSON.stringify({ message: "Success" }),
    };
  } catch (error) {
    console.error("Error:", error);

    // Return proper error response
    return {
      statusCode: 500,
      body: JSON.stringify({ error: error.message }),
    };
  }
};

// ═══════════════════════════════════════════
// ENVIRONMENT VARIABLES
// ═══════════════════════════════════════════

// Access via process.env
const tableName = process.env.USERS_TABLE;
const apiKey = process.env.API_KEY;

// ═══════════════════════════════════════════
// ASYNC/AWAIT
// ═══════════════════════════════════════════

// Always use async/await (not callbacks)
exports.handler = async (event) => {
  const result = await someAsyncFunction();
  return result;
};

// ❌ Don't use callbacks (old style)
exports.handler = (event, context, callback) => {
  callback(null, response);
};
```

---

### ▲ Vercel Functions

**Serverless functions for the frontend-first platform**

```
🌐 Website → https://vercel.com/docs/functions
🎯 Best For → Next.js, frontend apps, API routes
💰 Pricing  → 100GB-hours free/month, unlimited invocations
⚡ Speed    → Edge functions available
🔧 Tech     → Node.js, Go, Python, Ruby
```

#### 📥 Vercel Functions Setup

```bash
# ═══════════════════════════════════════════
# INSTALLATION
# ═══════════════════════════════════════════

# Install Vercel CLI
npm i -g vercel

# Login
vercel login

# ═══════════════════════════════════════════
# PROJECT STRUCTURE
# ═══════════════════════════════════════════

your-project/
├── api/                    # Serverless functions
│   ├── hello.js           # → /api/hello
│   ├── users.js           # → /api/users
│   └── posts/
│       └── [id].js        # → /api/posts/[id] (dynamic route)
├── public/
├── package.json
└── vercel.json            # Optional config

# ═══════════════════════════════════════════
# DEPLOYMENT
# ═══════════════════════════════════════════

# Deploy to production
vercel --prod

# Deploy preview
vercel

# Deploy with environment variables
vercel --prod -e DATABASE_URL=postgres://...

# ═══════════════════════════════════════════
# ENVIRONMENT VARIABLES
# ═══════════════════════════════════════════

# Add via CLI
vercel env add DATABASE_URL production

# Or via UI: Project → Settings → Environment Variables

# Pull environment variables locally
vercel env pull

# Local development with env vars
vercel dev
```

#### 📝 Vercel Function Examples

```javascript
// ═══════════════════════════════════════════
// api/hello.js - Basic Function
// ═══════════════════════════════════════════

export default function handler(req, res) {
  res.status(200).json({
    message: 'Hello from Vercel!',
    timestamp: new Date().toISOString()
  });
}

// ═══════════════════════════════════════════
// api/users.js - REST API Endpoint
// ═══════════════════════════════════════════

import { Pool } from 'pg';

const pool = new Pool({
  connectionString: process.env.DATABASE_URL,
  ssl: { rejectUnauthorized: false }
});

export default async function handler(req, res) {
  // Handle different HTTP methods
  switch (req.method) {
    case 'GET':
      return getUsers(req, res);
    case 'POST':
      return createUser(req, res);
    case 'PUT':
      return updateUser(req, res);
    case 'DELETE':
      return deleteUser(req, res);
    default:
      res.setHeader('Allow', ['GET', 'POST', 'PUT', 'DELETE']);
      return res.status(405).json({ error: `Method ${req.method} Not Allowed` });
  }
}

async function getUsers(req, res) {
  try {
    const { rows } = await pool.query('SELECT * FROM users');
    res.status(200).json(rows);
  } catch (error) {
    console.error('Database error:', error);
    res.status(500).json({ error: 'Internal server error' });
  }
}

async function createUser(req, res) {
  try {
    const { name, email } = req.body;

    const { rows } = await pool.query(
      'INSERT INTO users (name, email) VALUES ($1, $2) RETURNING *',
      [name, email]
    );

    res.status(201).json(rows[0]);
  } catch (error) {
    console.error('Database error:', error);
    res.status(500).json({ error: 'Internal server error' });
  }
}

// ═══════════════════════════════════════════
// api/posts/[id].js - Dynamic Route
// ═══════════════════════════════════════════

export default async function handler(req, res) {
  const { id } = req.query;

  if (req.method === 'GET') {
    try {
      const { rows } = await pool.query(
        'SELECT * FROM posts WHERE id = $1',
        [id]
      );

      if (rows.length === 0) {
        return res.status(404).json({ error: 'Post not found' });
      }

      res.status(200).json(rows[0]);
    } catch (error) {
      res.status(500).json({ error: 'Internal server error' });
    }
  } else {
    res.setHeader('Allow', ['GET']);
    res.status(405).json({ error: `Method ${req.method} Not Allowed` });
  }
}

// ═══════════════════════════════════════════
// api/auth/[...auth].js - Catch-all Route
// ═══════════════════════════════════════════

export default function handler(req, res) {
  const { auth } = req.query;
  // auth is an array: /api/auth/login/oauth → ['login', 'oauth']

  console.log('Auth route:', auth);
  res.status(200).json({ route: auth });
}
```

#### ⚡ Vercel Edge Functions

```javascript
// ═══════════════════════════════════════════
// Edge Functions (Run on Vercel's Edge Network)
// ═══════════════════════════════════════════

// api/edge.js
export const config = {
  runtime: "edge",
};

export default async function handler(req) {
  const geo = req.geo; // Geolocation data
  const ip = req.ip; // User's IP

  return new Response(
    JSON.stringify({
      message: "Hello from the edge!",
      location: geo.city,
      country: geo.country,
      ip: ip,
      timestamp: new Date().toISOString(),
    }),
    {
      status: 200,
      headers: {
        "content-type": "application/json",
      },
    }
  );
}

// ═══════════════════════════════════════════
// Edge Middleware (Runs before requests)
// ═══════════════════════════════════════════

// middleware.js (in project root)
import { NextResponse } from "next/server";

export function middleware(request) {
  // Add custom header
  const response = NextResponse.next();
  response.headers.set("x-custom-header", "my-value");

  // Redirect based on geolocation
  if (request.geo?.country === "US") {
    return NextResponse.redirect(new URL("/us", request.url));
  }

  // A/B testing
  const variant = Math.random() < 0.5 ? "A" : "B";
  response.cookies.set("variant", variant);

  return response;
}

// Run middleware on specific paths
export const config = {
  matcher: "/api/:path*",
};
```

#### 📝 Vercel Configuration

```json
// ═══════════════════════════════════════════
// vercel.json - Project Configuration
// ═══════════════════════════════════════════

{
  "functions": {
    "api/**/*.js": {
      "memory": 1024,
      "maxDuration": 10
    }
  },
  "env": {
    "NODE_ENV": "production"
  },
  "regions": ["iad1", "sfo1"],
  "rewrites": [
    {
      "source": "/api/v1/:path*",
      "destination": "/api/:path*"
    }
  ],
  "headers": [
    {
      "source": "/api/(.*)",
      "headers": [
        {
          "key": "Access-Control-Allow-Origin",
          "value": "*"
        },
        {
          "key": "Access-Control-Allow-Methods",
          "value": "GET, POST, PUT, DELETE, OPTIONS"
        }
      ]
    }
  ],
  "redirects": [
    {
      "source": "/old-api/:path*",
      "destination": "/api/:path*",
      "permanent": true
    }
  ]
}
```

---

### 🌐 Netlify Functions

**Serverless functions for the Jamstack**

```
🌐 Website → https://www.netlify.com/products/functions
🎯 Best For → Static sites, Jamstack apps
💰 Pricing  → 125k requests + 100 hours free/month
⚡ Speed    → Built on AWS Lambda
🔧 Tech     → JavaScript, TypeScript, Go
```

#### 📥 Netlify Functions Setup

```bash
# ═══════════════════════════════════════════
# INSTALLATION
# ═══════════════════════════════════════════

# Install Netlify CLI
npm install -g netlify-cli

# Login
netlify login

# Initialize project
netlify init

# ═══════════════════════════════════════════
# PROJECT STRUCTURE
# ═══════════════════════════════════════════

your-project/
├── netlify/
│   └── functions/         # Serverless functions
│       ├── hello.js       # → /.netlify/functions/hello
│       ├── users.js
│       └── scheduled.js   # Scheduled function
├── public/
├── netlify.toml           # Configuration
└── package.json

# ═══════════════════════════════════════════
# LOCAL DEVELOPMENT
# ═══════════════════════════════════════════

# Run dev server (with functions)
netlify dev

# Test specific function
netlify functions:invoke hello --payload '{"name":"MrDib"}'

# ═══════════════════════════════════════════
# DEPLOYMENT
# ═══════════════════════════════════════════

# Deploy to production
netlify deploy --prod

# Deploy preview
netlify deploy
```

#### 📝 Netlify Function Examples

```javascript
// ═══════════════════════════════════════════
// netlify/functions/hello.js - Basic Function
// ═══════════════════════════════════════════

exports.handler = async (event, context) => {
  return {
    statusCode: 200,
    body: JSON.stringify({
      message: "Hello from Netlify!",
      method: event.httpMethod,
      path: event.path,
    }),
  };
};

// ═══════════════════════════════════════════
// netlify/functions/users.js - REST API
// ═══════════════════════════════════════════

const { Client } = require("pg");

exports.handler = async (event, context) => {
  // Parse request
  const { httpMethod, body } = event;

  // Database connection
  const client = new Client({
    connectionString: process.env.DATABASE_URL,
    ssl: { rejectUnauthorized: false },
  });

  await client.connect();

  try {
    if (httpMethod === "GET") {
      // Get all users
      const result = await client.query("SELECT * FROM users");

      return {
        statusCode: 200,
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(result.rows),
      };
    }

    if (httpMethod === "POST") {
      // Create user
      const { name, email } = JSON.parse(body);

      const result = await client.query(
        "INSERT INTO users (name, email) VALUES ($1, $2) RETURNING *",
        [name, email]
      );

      return {
        statusCode: 201,
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(result.rows[0]),
      };
    }

    return {
      statusCode: 405,
      body: JSON.stringify({ error: "Method not allowed" }),
    };
  } catch (error) {
    console.error("Error:", error);

    return {
      statusCode: 500,
      body: JSON.stringify({ error: error.message }),
    };
  } finally {
    await client.end();
  }
};

// ═══════════════════════════════════════════
// netlify/functions/scheduled.js - Scheduled Function
// ═══════════════════════════════════════════

const { schedule } = require("@netlify/functions");

// Runs every day at midnight
const handler = async (event, context) => {
  console.log("Running scheduled job");

  // Your scheduled task
  await performDailyCleanup();

  return {
    statusCode: 200,
    body: JSON.stringify({ message: "Cleanup completed" }),
  };
};

exports.handler = schedule("@daily", handler);

// More schedule examples:
// '@hourly'   - Every hour
// '@daily'    - Every day at midnight
// '@weekly'   - Every week
// '@monthly'  - Every month
// '0 9 * * *' - Every day at 9 AM (cron syntax)

// ═══════════════════════════════════════════
// netlify/functions/background.js - Background Function
// ═══════════════════════════════════════════

// Background functions run up to 15 minutes
exports.handler = async (event, context) => {
  // Long-running task
  await processLargeDataset();

  return {
    statusCode: 200,
    body: JSON.stringify({ message: "Processing started" }),
  };
};

// Name convention: filename-background.js
// Access at: /.netlify/functions/background
```

#### 📝 Netlify Configuration

```toml
# ═══════════════════════════════════════════
# netlify.toml - Configuration
# ═══════════════════════════════════════════

[build]
  command = "npm run build"
  publish = "dist"
  functions = "netlify/functions"

[build.environment]
  NODE_VERSION = "18"

# Function settings
[functions]
  directory = "netlify/functions"
  node_bundler = "esbuild"

# Redirects & rewrites
[[redirects]]
  from = "/api/*"
  to = "/.netlify/functions/:splat"
  status = 200

# Headers
[[headers]]
  for = "/.netlify/functions/*"
  [headers.values]
    Access-Control-Allow-Origin = "*"
    Access-Control-Allow-Methods = "GET, POST, PUT, DELETE, OPTIONS"

# Environment variables (per deploy context)
[context.production.environment]
  NODE_ENV = "production"

[context.deploy-preview.environment]
  NODE_ENV = "development"
```

---

### ☁️ Cloudflare Workers

**Serverless on the edge network**

```
🌐 Website → https://workers.cloudflare.com
🎯 Best For → Edge computing, global APIs, low latency
💰 Pricing  → 100k requests/day free, $5/10M requests
⚡ Speed    → <50ms cold start, runs in 200+ cities
🔧 Tech     → JavaScript, TypeScript, Rust (WebAssembly)
```

#### 📥 Cloudflare Workers Setup

```bash
# ═══════════════════════════════════════════
# INSTALLATION
# ═══════════════════════════════════════════

# Install Wrangler CLI
npm install -g wrangler

# Login
wrangler login

# ═══════════════════════════════════════════
# CREATE PROJECT
# ═══════════════════════════════════════════

# Create new worker
wrangler init my-worker

# Project structure:
my-worker/
├── src/
│   └── index.js       # Worker code
├── wrangler.toml      # Configuration
└── package.json

# ═══════════════════════════════════════════
# DEVELOPMENT
# ═══════════════════════════════════════════

# Run locally
wrangler dev

# Run with remote resources
wrangler dev --remote

# ═══════════════════════════════════════════
# DEPLOYMENT
# ═══════════════════════════════════════════

# Deploy to production
wrangler publish

# Deploy to specific environment
wrangler publish --env production
```

#### 📝 Cloudflare Workers Examples

```javascript
// ═══════════════════════════════════════════
// src/index.js - Basic Worker
// ═══════════════════════════════════════════

export default {
  async fetch(request, env, ctx) {
    return new Response('Hello from Cloudflare Workers!', {
      headers: {
        'Content-Type': 'text/plain',
      },
    });
  },
};

// ═══════════════════════════════════════════
// REST API Worker
// ═══════════════════════════════════════════

export default {
  async fetch(request, env, ctx) {
    const url = new URL(request.url);
    const path = url.pathname;
    const method = request.method;

    // Route handling
    if (path === '/api/users' && method === 'GET') {
      return getUsers(env);
    }

    if (path === '/api/users' && method === 'POST') {
      return createUser(request, env);
    }

    if (path.startsWith('/api/users/') && method === 'GET') {
      const id = path.split('/').pop();
      return getUser(id, env);
    }

    return new Response('Not Found', { status: 404 });
  },
};

async function getUsers(env) {
  // Access Cloudflare KV (Key-Value storage)
  const users = await env.USERS_KV.get('users', { type: 'json' });

  return new Response(JSON.stringify(users || []), {
    headers: { 'Content-Type': 'application/json' },
  });
}

async function createUser(request, env) {
  const userData = await request.json();

  // Get existing users
  const users = await env.USERS_KV.get('users', { type: 'json' }) || [];

  // Add new user
  const newUser = {
    id: Date.now().toString(),
    ...userData,
    createdAt: new Date().toISOString(),
  };

  users.push(newUser);

  // Save back to KV
  await env.USERS_KV.put('users', JSON.stringify(users));

  return new Response(JSON.stringify(newUser), {
    status: 201,
    headers: { 'Content-Type': 'application/json' },
  });
}

// ═══════════════════════════════════════════
// Worker with D1 Database (SQLite on edge)
// ═══════════════════════════════════════════

export default {
  async fetch(request, env, ctx) {
    const { pathname } = new URL(request.url);

    if (pathname === '/api/users' && request.method === 'GET') {
      // Query D1 database
      const { results } = await env.DB.prepare(
        'SELECT * FROM users'
      ).all();

      return Response.json(results);
    }

    if (pathname === '/api/users' && request.method === 'POST') {
      const { name, email } = await request.json();

      // Insert into D1
      const result = await env.DB.prepare(
        'INSERT INTO users (name, email) VALUES (?, ?) RETURNING *'
      ).bind(name, email).first();

      return Response.json(result, { status: 201 });
    }

    return new Response('Not Found', { status: 404 });
  },
};

// ═══════════════════════════════════════════
// Worker with Caching
// ═══════════════════════════════════════════

export default {
  async fetch(request, env, ctx) {
    const cache = caches.default;

    // Try to get from cache
    let response = await cache.match(request);

    if (!response) {
      // Not in cache, fetch from origin
      response = await fetch(request);

      // Cache for 1 hour
      const cacheResponse = response.clone();
      ctx.waitUntil(cache.put(request, cacheResponse));
    }

    return response;
  },
};

// ═══════════════════════════════════════════
// Worker with Rate Limiting
// ═══════════════════════════════════════════

export default {
  async fetch(request, env, ctx) {
    const ip = request.headers.get('CF-Connecting-IP');
    const key = `rate_limit:${ip}`;

    // Get current count
    const count = await env.RATE_LIMIT_KV.get(key);
    const currentCount = count ? parseInt(count) : 0;

    // Check limit (100 requests per minute)
    if (currentCount >= 100) {
      return new Response('Rate limit exceeded', {
        status: 429,
        headers: {
          'Retry-After': '60',
        },
      });
    }

    // Increment count
    await env.RATE_LIMIT_KV.put(key, (currentCount + 1).toString(), {
      expirationTtl: 60, // Expire after 60 seconds
    });

    // Process request
    return new Response('Success');
  },
};
```

#### 📝 Cloudflare Workers Configuration

```toml
# ═══════════════════════════════════════════
# wrangler.toml - Worker Configuration
# ═══════════════════════════════════════════

name = "my-worker"
main = "src/index.js"
compatibility_date = "2024-01-01"

# KV Namespaces
[[kv_namespaces]]
binding = "USERS_KV"
id = "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"

[[kv_namespaces]]
binding = "RATE_LIMIT_KV"
id = "yyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyy"

# D1 Database
[[d1_databases]]
binding = "DB"
database_name = "my-database"
database_id = "zzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzz"

# Environment variables
[vars]
ENVIRONMENT = "production"

# Secrets (set via: wrangler secret put SECRET_NAME)
# ACCESS_TOKEN
# API_KEY

# Routes
routes = [
  { pattern = "api.example.com/*", zone_name = "example.com" }
]

# Environments
[env.staging]
name = "my-worker-staging"
routes = [
  { pattern = "staging-api.example.com/*", zone_name = "example.com" }
]
```

#### 💡 Cloudflare Workers Pro Tips

```javascript
// ═══════════════════════════════════════════
// BEST PRACTICES
// ═══════════════════════════════════════════

// 1. Use Response.json() shorthand
return Response.json({ message: "Hello" });

// 2. Handle CORS properly
function corsHeaders() {
  return {
    "Access-Control-Allow-Origin": "*",
    "Access-Control-Allow-Methods": "GET, POST, PUT, DELETE, OPTIONS",
    "Access-Control-Allow-Headers": "Content-Type",
  };
}

// 3. Use waitUntil for background tasks
ctx.waitUntil(logToAnalytics(request));

// 4. Leverage edge caching
const cache = caches.default;
const cacheKey = new Request(url.toString(), request);

// 5. Use Durable Objects for stateful applications
// Requires separate configuration

// 6. Monitor with Workers Analytics
// Available in Cloudflare Dashboard

// 7. Use TypeScript for better DX
// Rename index.js to index.ts
// Add tsconfig.json

// 8. Test thoroughly
// wrangler dev --local
// wrangler dev --remote

// 9. Version your workers
// Use wrangler versions

// 10. Set up CI/CD
// GitHub Actions, GitLab CI, etc.
```

---

<div align="center">

## 🗄️ Database Hosting

_Managed databases for your backend_ 💾

</div>

### Database-as-a-Service Options

```
═══════════════════════════════════════════════════════════════
DATABASE HOSTING COMPARISON
═══════════════════════════════════════════════════════════════

RELATIONAL DATABASES (PostgreSQL, MySQL):

┌────────────────┬──────────────┬────────────────┬────────────┐
│ Provider       │ Free Tier    │ Best For       │ Pricing    │
├────────────────┼──────────────┼────────────────┼────────────┤
│ Neon           │ 0.5GB        │ PostgreSQL     │ $19/mo+    │
│ postgres.new   │ Serverless   │ Modern apps    │            │
├────────────────┼──────────────┼────────────────┼────────────┤
│ Supabase       │ 500MB        │ PostgreSQL +   │ $25/mo+    │
│                │ 2 projects   │ Auth, Storage  │            │
├────────────────┼──────────────┼────────────────┼────────────┤
│ PlanetScale    │ 5GB          │ MySQL          │ $29/mo+    │
│                │ 1 billion    │ Serverless     │            │
│                │ row reads/mo │                │            │
├────────────────┼──────────────┼────────────────┼────────────┤
│ Railway        │ Included     │ All-in-one     │ Usage-based│
│                │ with project │ Platform       │            │
├────────────────┼──────────────┼────────────────┼────────────┤
│ Render         │ None (paid)  │ Managed        │ $7/mo+     │
│                │              │ PostgreSQL     │            │
├────────────────┼──────────────┼────────────────┼────────────┤
│ AWS RDS        │ 750hrs/mo    │ Enterprise     │ $15/mo+    │
│                │ (1st year)   │ Production     │            │
└────────────────┴──────────────┴────────────────┴────────────┘

NoSQL DATABASES:

┌────────────────┬──────────────┬────────────────┬────────────┐
│ Provider       │ Free Tier    │ Best For       │ Pricing    │
├────────────────┼──────────────┼────────────────┼────────────┤
│ MongoDB Atlas  │ 512MB        │ Document DB    │ $9/mo+     │
│                │ Shared       │ Flexible schema│            │
├────────────────┼──────────────┼────────────────┼────────────┤
│ Firebase       │ 1GB storage  │ Real-time apps │ Pay-as-go  │
│ Firestore      │ 50k reads/day│ Mobile apps    │            │
├────────────────┼──────────────┼────────────────┼────────────┤
│ FaunaDB        │ 100k reads   │ Serverless     │ $23/mo+    │
│                │ 50k writes   │ GraphQL        │            │
├────────────────┼──────────────┼────────────────┼────────────┤
│ DynamoDB       │ 25GB         │ AWS ecosystem  │ Pay-as-go  │
│                │ 200M requests│ High scale     │            │
└────────────────┴──────────────┴────────────────┴────────────┘

REDIS (Caching):

┌────────────────┬──────────────┬────────────────┬────────────┐
│ Provider       │ Free Tier    │ Best For       │ Pricing    │
├────────────────┼──────────────┼────────────────┼────────────┤
│ Upstash        │ 10k commands │ Serverless     │ $0.2/100k  │
│                │ /day         │ Pay-per-use    │ requests   │
├────────────────┼──────────────┼────────────────┼────────────┤
│ Redis Cloud    │ 30MB         │ Managed Redis  │ $5/mo+     │
│                │              │                │            │
├────────────────┼──────────────┼────────────────┼────────────┤
│ Railway        │ Included     │ Integrated     │ Usage-based│
│                │              │                │            │
└────────────────┴──────────────┴────────────────┴────────────┘

RECOMMENDATIONS:

🆓 Free Projects:
   → Neon (PostgreSQL), Supabase, MongoDB Atlas

🚀 Startups/MVPs:
   → PlanetScale (MySQL), Supabase (PostgreSQL)
   → Railway (all-in-one)

💰 Cost-Effective:
   → Neon (serverless pricing)
   → PlanetScale (generous free tier)

🏢 Production/Enterprise:
   → AWS RDS, Google Cloud SQL
   → MongoDB Atlas (dedicated clusters)

⚡ Serverless Apps:
   → Neon, PlanetScale
   → DynamoDB, FaunaDB
```

### Quick Setup Examples

```bash
# ═══════════════════════════════════════════
# NEON (PostgreSQL)
# ═══════════════════════════════════════════

# 1. Sign up at https://neon.tech
# 2. Create project
# 3. Get connection string

# Connection string format:
# postgres://user:password@ep-xxx.region.aws.neon.tech/dbname?sslmode=require

# Use in Node.js:
const { Pool } = require('pg');
const pool = new Pool({
  connectionString: process.env.DATABASE_URL,
  ssl: { rejectUnauthorized: false }
});

# ═══════════════════════════════════════════
# SUPABASE (PostgreSQL + More)
# ═══════════════════════════════════════════

# 1. Sign up at https://supabase.com
# 2. Create project
# 3. Get connection string or use Supabase client

npm install @supabase/supabase-js

const { createClient } = require('@supabase/supabase-js');
const supabase = createClient(
  process.env.SUPABASE_URL,
  process.env.SUPABASE_KEY
);

# Query data:
const { data, error } = await supabase
  .from('users')
  .select('*');

# ═══════════════════════════════════════════
# PLANETSCALE (MySQL)
# ═══════════════════════════════════════════

# 1. Sign up at https://planetscale.com
# 2. Create database
# 3. Get connection string

# Connection string includes SSL certificates
# mysql://user:pass@host/db?ssl={"rejectUnauthorized":true}

# Use with Prisma:
npx prisma init
# Update schema.prisma with PlanetScale datasource

# ═══════════════════════════════════════════
# MONGODB ATLAS
# ═══════════════════════════════════════════

# 1. Sign up at https://mongodb.com/cloud/atlas
# 2. Create cluster
# 3. Get connection string

npm install mongodb

const { MongoClient } = require('mongodb');
const client = new MongoClient(process.env.MONGODB_URI);

await client.connect();
const db = client.db('myapp');
const users = db.collection('users');

# ═══════════════════════════════════════════
# UPSTASH REDIS
# ═══════════════════════════════════════════

# 1. Sign up at https://upstash.com
# 2. Create database
# 3. Get REST URL

npm install @upstash/redis

const { Redis } = require('@upstash/redis');
const redis = new Redis({
  url: process.env.UPSTASH_REDIS_REST_URL,
  token: process.env.UPSTASH_REDIS_REST_TOKEN
});

await redis.set('key', 'value');
const value = await redis.get('key');
```

---

<div align="center">

## 🚀 Deployment Strategies

_Deploy with confidence, rollback with ease_ 🎯

</div>

### Deployment Patterns

```
═══════════════════════════════════════════════════════════════
DEPLOYMENT STRATEGIES
═══════════════════════════════════════════════════════════════

1. BASIC DEPLOYMENT (Replace)
┌────────────────────────────────────────────┐
│  Old Version (v1)                          │
│  ┌─────┐ ┌─────┐ ┌─────┐                  │
│  │ v1  │ │ v1  │ │ v1  │                  │
│  └─────┘ └─────┘ └─────┘                  │
└────────────────────────────────────────────┘
              ↓ DEPLOY NEW VERSION
┌────────────────────────────────────────────┐
│  New Version (v2)                          │
│  ┌─────┐ ┌─────┐ ┌─────┐                  │
│  │ v2  │ │ v2  │ │ v2  │                  │
│  └─────┘ └─────┘ └─────┘                  │
└────────────────────────────────────────────┘

❌ Downtime: YES (brief)
✅ Rollback: Redeploy old version
💰 Cost: Low
🎯 Use: Development, non-critical apps

─────────────────────────────────────────────────────────────

2. ROLLING DEPLOYMENT (Gradual Replace)
┌────────────────────────────────────────────┐
│  Mixed Versions                            │
│  ┌─────┐ ┌─────┐ ┌─────┐                  │
│  │ v1  │ │ v1  │ │ v2  │ ← Deploy one     │
│  └─────┘ └─────┘ └─────┘                  │
└────────────────────────────────────────────┘
              ↓
┌────────────────────────────────────────────┐
│  ┌─────┐ ┌─────┐ ┌─────┐                  │
│  │ v1  │ │ v2  │ │ v2  │ ← Deploy another │
│  └─────┘ └─────┘ └─────┘                  │
└────────────────────────────────────────────┘
              ↓
┌────────────────────────────────────────────┐
│  All New                                   │
│  ┌─────┐ ┌─────┐ ┌─────┐                  │
│  │ v2  │ │ v2  │ │ v2  │ ← All deployed   │
│  └─────┘ └─────┘ └─────┘                  │
└────────────────────────────────────────────┘

✅ Downtime: NONE
✅ Rollback: Stop and reverse
⚠️  Risk: Two versions running
💰 Cost: Low
🎯 Use: Production apps

─────────────────────────────────────────────────────────────

3. BLUE-GREEN DEPLOYMENT (Switch)
┌────────────────────────────────────────────┐
│  BLUE (Current - v1)    │  GREEN (New - v2)│
│  ┌─────┐ ┌─────┐        │  ┌─────┐ ┌─────┐│
│  │ v1  │ │ v1  │  ←100% │  │ v2  │ │ v2  ││
│  └─────┘ └─────┘   Traffic └─────┘ └─────┘│
│                         │  (Waiting)        │
└────────────────────────────────────────────┘
              ↓ SWITCH TRAFFIC
┌────────────────────────────────────────────┐
│  BLUE (Old)             │  GREEN (Current) │
│  ┌─────┐ ┌─────┐        │  ┌─────┐ ┌─────┐│
│  │ v1  │ │ v1  │        │  │ v2  │ │ v2  ││
│  └─────┘ └─────┘        │  └─────┘ └─────┘│
│  (Standby)              │  ←100% Traffic   │
└────────────────────────────────────────────┘

✅ Downtime: NONE
✅ Rollback: Instant (switch back)
❌ Cost: 2x infrastructure
🎯 Use: Critical production apps

─────────────────────────────────────────────────────────────

4. CANARY DEPLOYMENT (Gradual Traffic Shift)
┌────────────────────────────────────────────┐
│  v1 (95%)              │  v2 (5%)          │
│  ┌─────┐ ┌─────┐       │  ┌─────┐         │
│  │ v1  │ │ v1  │  ←95% │  │ v2  │  ←5%    │
│  └─────┘ └─────┘       │  └─────┘         │
└────────────────────────────────────────────┘
              ↓ IF OK, INCREASE
┌────────────────────────────────────────────┐
│  v1 (50%)              │  v2 (50%)         │
│  ┌─────┐ ┌─────┐       │  ┌─────┐ ┌─────┐ │
│  │ v1  │ │ v1  │  ←50% │  │ v2  │ │ v2  │ │
│  └─────┘ └─────┘       │  └─────┘ └─────┘ │
│                         │  ←50%             │
└────────────────────────────────────────────┘
              ↓ CONTINUE
┌────────────────────────────────────────────┐
│  All v2                                    │
│  ┌─────┐ ┌─────┐ ┌─────┐ ┌─────┐          │
│  │ v2  │ │ v2  │ │ v2  │ │ v2  │  ←100%   │
│  └─────┘ └─────┘ └─────┘ └─────┘          │
└────────────────────────────────────────────┘

✅ Downtime: NONE
✅ Rollback: Stop and rollback
✅ Risk: Minimal (test with small %)
💰 Cost: Medium
🎯 Use: Risk-averse production deployments

─────────────────────────────────────────────────────────────

5. A/B TESTING DEPLOYMENT
┌────────────────────────────────────────────┐
│  Version A (50%)       │  Version B (50%)  │
│  ┌─────┐ ┌─────┐       │  ┌─────┐ ┌─────┐ │
│  │  A  │ │  A  │  ←50% │  │  B  │ │  B  │ │
│  └─────┘ └─────┘       │  └─────┘ └─────┘ │
│                         │  ←50%             │
│  • Users split by:                         │
│    - User ID                               │
│    - Location                              │
│    - Cookie                                │
│  • Measure metrics                         │
│  • Keep winner                             │
└────────────────────────────────────────────┘

✅ Downtime: NONE
🎯 Use: Feature testing, UX experiments
```

### Git Workflow Best Practices

```bash
# ═══════════════════════════════════════════
# GITFLOW BRANCHING STRATEGY
# ═══════════════════════════════════════════

main (production)
  ↑
  └─ develop (staging)
       ↑
       ├─ feature/new-api
       ├─ feature/user-auth
       ├─ bugfix/login-issue
       └─ hotfix/critical-bug

# ═══════════════════════════════════════════
# WORKFLOW
# ═══════════════════════════════════════════

# 1. Create feature branch
git checkout -b feature/new-api develop

# 2. Work on feature
git add .
git commit -m "feat: add new API endpoint"

# 3. Push to remote
git push origin feature/new-api

# 4. Create Pull Request (GitHub/GitLab)
# Review → Approve → Merge to develop

# 5. Deploy to staging (automatic)
# develop branch → staging environment

# 6. Test in staging
# QA, integration tests

# 7. Merge to main (production)
git checkout main
git merge develop
git push origin main

# 8. Deploy to production (automatic)
# main branch → production environment

# 9. Tag release
git tag -a v1.2.0 -m "Release v1.2.0"
git push origin v1.2.0

# ═══════════════════════════════════════════
# CONVENTIONAL COMMITS
# ═══════════════════════════════════════════

# Format: <type>(<scope>): <subject>

feat: add user authentication
fix: resolve login redirect issue
docs: update API documentation
style: format code with prettier
refactor: simplify database queries
test: add unit tests for auth
chore: update dependencies
perf: optimize image loading
ci: add GitHub Actions workflow

# Breaking changes:
feat!: change API response format

BREAKING CHANGE: API now returns data in different structure
```

---

<div align="center">

## 🔐 Security Best Practices

_Keep your backend secure_ 🛡️

</div>

### Security Checklist

```bash
# ═══════════════════════════════════════════
# ENVIRONMENT VARIABLES & SECRETS
# ═══════════════════════════════════════════

# ✅ DO: Use environment variables
DATABASE_URL=postgres://...
API_KEY=your-secret-key
JWT_SECRET=random-string-here

# ✅ DO: Use secret management services
# - Railway Secrets
# - Vercel Environment Variables
# - AWS Secrets Manager
# - HashiCorp Vault

# ❌ DON'T: Commit secrets to Git
# Add to .gitignore:
.env
.env.local
.env.production
.env.*.local

# ❌ DON'T: Log secrets
console.log('API Key:', apiKey); // ❌ NEVER!

# ✅ DO: Use .env.example for documentation
DATABASE_URL=
API_KEY=
JWT_SECRET=

# ═══════════════════════════════════════════
# HTTPS & SSL/TLS
# ═══════════════════════════════════════════

# ✅ Always use HTTPS in production
# Most platforms provide free SSL (Let's Encrypt)

# ✅ Force HTTPS redirect
if (req.headers['x-forwarded-proto'] !== 'https') {
  return res.redirect('https://' + req.headers.host + req.url);
}

# ✅ Set secure headers
app.use(helmet()); // Express.js security middleware

# ═══════════════════════════════════════════
# CORS (Cross-Origin Resource Sharing)
# ═══════════════════════════════════════════

const cors = require('cors');

# ❌ DON'T: Allow all origins in production
app.use(cors()); // Allows ALL origins

# ✅ DO: Specify allowed origins
app.use(cors({
  origin: ['https://yourdomain.com', 'https://app.yourdomain.com'],
  credentials: true,
  optionsSuccessStatus: 200
}));

# ✅ DO: Validate origin dynamically
app.use(cors({
  origin: function(origin, callback) {
    const allowedOrigins = process.env.ALLOWED_ORIGINS.split(',');
    if (!origin || allowedOrigins.includes(origin)) {
      callback(null, true);
    } else {
      callback(new Error('Not allowed by CORS'));
    }
  }
}));

# ═══════════════════════════════════════════
# AUTHENTICATION & AUTHORIZATION
# ═══════════════════════════════════════════

# ✅ Use JWT for stateless auth
const jwt = require('jsonwebtoken');

function generateToken(user) {
  return jwt.sign(
    { id: user.id, email: user.email },
    process.env.JWT_SECRET,
    { expiresIn: '7d' }
  );
}

function verifyToken(req, res, next) {
  const token = req.headers.authorization?.split(' ')[1];

  if (!token) {
    return res.status(401).json({ error: 'No token provided' });
  }

  try {
    const decoded = jwt.verify(token, process.env.JWT_SECRET);
    req.user = decoded;
    next();
  } catch (error) {
    return res.status(401).json({ error: 'Invalid token' });
  }
}

# ✅ Hash passwords properly
const bcrypt = require('bcrypt');

async function hashPassword(password) {
  return await bcrypt.hash(password, 10);
}

async function comparePassword(password, hash) {
  return await bcrypt.compare(password, hash);
}

# ═══════════════════════════════════════════
# RATE LIMITING
# ═══════════════════════════════════════════

const rateLimit = require('express-rate-limit');

const limiter = rateLimit({
  windowMs: 15 * 60 * 1000, // 15 minutes
  max: 100, // Limit each IP to 100 requests per window
  message: 'Too many requests from this IP'
});

app.use('/api/', limiter);

# Stricter limit for auth endpoints
const authLimiter = rateLimit({
  windowMs: 15 * 60 * 1000,
  max: 5, // 5 attempts per 15 minutes
  message: 'Too many login attempts'
});

app.post('/api/login', authLimiter, loginHandler);

# ═══════════════════════════════════════════
# INPUT VALIDATION & SANITIZATION
# ═══════════════════════════════════════════

# ✅ Validate all inputs
const { body, validationResult } = require('express-validator');

app.post('/api/users',
  body('email').isEmail().normalizeEmail(),
  body('name').trim().isLength({ min: 2, max: 50 }),
  body('age').optional().isInt({ min: 18, max: 120 }),
  async (req, res) => {
    const errors = validationResult(req);
    if (!errors.isEmpty()) {
      return res.status(400).json({ errors: errors.array() });
    }

    // Process validated data
  }
);

# ✅ Sanitize HTML to prevent XSS
const sanitizeHtml = require('sanitize-html');

const clean = sanitizeHtml(userInput, {
  allowedTags: ['b', 'i', 'em', 'strong'],
  allowedAttributes: {}
});

# ═══════════════════════════════════════════
# SQL INJECTION PREVENTION
# ═══════════════════════════════════════════

# ❌ DON'T: Use string concatenation
const query = `SELECT * FROM users WHERE email = '${email}'`; // VULNERABLE!

# ✅ DO: Use parameterized queries
const { rows } = await pool.query(
  'SELECT * FROM users WHERE email = $1',
  [email]
);

# ✅ DO: Use ORM with built-in protection
// Prisma
const user = await prisma.user.findUnique({
  where: { email: email }
});

# ═══════════════════════════════════════════
# SECURITY HEADERS
# ═══════════════════════════════════════════

const helmet = require('helmet');

app.use(helmet());

# Or manually:
app.use((req, res, next) => {
  res.setHeader('X-Content-Type-Options', 'nosniff');
  res.setHeader('X-Frame-Options', 'DENY');
  res.setHeader('X-XSS-Protection', '1; mode=block');
  res.setHeader('Strict-Transport-Security', 'max-age=31536000; includeSubDomains');
  res.setHeader('Content-Security-Policy', "default-src 'self'");
  next();
});

# ═══════════════════════════════════════════
# DEPENDENCY SECURITY
# ═══════════════════════════════════════════

# Check for vulnerabilities
npm audit
npm audit fix

# Use Snyk for continuous monitoring
npm install -g snyk
snyk test
snyk monitor

# Keep dependencies updated
npm outdated
npm update

# ═══════════════════════════════════════════
# ERROR HANDLING (Don't Leak Info)
# ═══════════════════════════════════════════

# ❌ DON'T: Expose stack traces in production
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send(err.stack); // VULNERABLE!
});

# ✅ DO: Generic error messages
app.use((err, req, res, next) => {
  console.error(err);

  if (process.env.NODE_ENV === 'production') {
    res.status(500).json({ error: 'Internal server error' });
  } else {
    res.status(500).json({ error: err.message, stack: err.stack });
  }
});
```

---

<div align="center">

## 📊 Monitoring & Logging

_Know what's happening in production_ 👁️

</div>

### Essential Monitoring Setup

```javascript
// ═══════════════════════════════════════════
// STRUCTURED LOGGING
// ═══════════════════════════════════════════

// Use Winston or Pino for production logging
const winston = require("winston");

const logger = winston.createLogger({
  level: process.env.LOG_LEVEL || "info",
  format: winston.format.combine(
    winston.format.timestamp(),
    winston.format.errors({ stack: true }),
    winston.format.json()
  ),
  defaultMeta: {
    service: "my-api",
    environment: process.env.NODE_ENV,
  },
  transports: [
    // Write all logs to console (captured by platform)
    new winston.transports.Console({
      format: winston.format.combine(
        winston.format.colorize(),
        winston.format.simple()
      ),
    }),
    // Write errors to file (if using persistent storage)
    new winston.transports.File({
      filename: "error.log",
      level: "error",
    }),
    // Write all logs to combined file
    new winston.transports.File({
      filename: "combined.log",
    }),
  ],
});

// Usage
logger.info("User logged in", { userId: 123, ip: req.ip });
logger.error("Database connection failed", { error: err.message });
logger.warn("High memory usage", { usage: process.memoryUsage() });

// ═══════════════════════════════════════════
// REQUEST LOGGING MIDDLEWARE
// ═══════════════════════════════════════════

const morgan = require("morgan");

// JSON format for structured logs
morgan.token("body", (req) => JSON.stringify(req.body));

app.use(
  morgan(":method :url :status :response-time ms - :body", {
    stream: {
      write: (message) => logger.info(message.trim()),
    },
  })
);

// Or custom middleware
app.use((req, res, next) => {
  const start = Date.now();

  res.on("finish", () => {
    const duration = Date.now() - start;

    logger.info("HTTP Request", {
      method: req.method,
      url: req.url,
      status: res.statusCode,
      duration,
      userAgent: req.get("user-agent"),
      ip: req.ip,
      userId: req.user?.id,
    });
  });

  next();
});

// ═══════════════════════════════════════════
// ERROR TRACKING (Sentry)
// ═══════════════════════════════════════════

const Sentry = require("@sentry/node");

Sentry.init({
  dsn: process.env.SENTRY_DSN,
  environment: process.env.NODE_ENV,
  tracesSampleRate: 1.0,
  // Only send errors in production
  beforeSend(event) {
    if (process.env.NODE_ENV === "development") {
      return null;
    }
    return event;
  },
});

// Request handler (must be first)
app.use(Sentry.Handlers.requestHandler());

// Your routes
app.use("/api", routes);

// Error handler (must be before other error middleware)
app.use(Sentry.Handlers.errorHandler());

// Optional: Add user context
Sentry.setUser({
  id: user.id,
  email: user.email,
});

// Capture exception manually
try {
  riskyOperation();
} catch (error) {
  Sentry.captureException(error);
  logger.error("Operation failed", { error: error.message });
}

// ═══════════════════════════════════════════
// APPLICATION PERFORMANCE MONITORING (APM)
// ═══════════════════════════════════════════

// New Relic
require("newrelic");

// Datadog
const tracer = require("dd-trace").init({
  service: "my-api",
  env: process.env.NODE_ENV,
});

// ═══════════════════════════════════════════
// HEALTH CHECK ENDPOINTS
// ═══════════════════════════════════════════

app.get("/health", (req, res) => {
  res.status(200).json({
    status: "healthy",
    uptime: process.uptime(),
    timestamp: new Date().toISOString(),
  });
});

app.get("/health/ready", async (req, res) => {
  // Check dependencies
  const checks = {
    database: false,
    redis: false,
    external_api: false,
  };

  try {
    // Check database
    await pool.query("SELECT 1");
    checks.database = true;

    // Check Redis
    await redis.ping();
    checks.redis = true;

    // Check external API
    const response = await fetch(process.env.EXTERNAL_API_URL);
    checks.external_api = response.ok;

    const allHealthy = Object.values(checks).every((check) => check);

    res.status(allHealthy ? 200 : 503).json({
      status: allHealthy ? "ready" : "not ready",
      checks,
    });
  } catch (error) {
    res.status(503).json({
      status: "not ready",
      checks,
      error: error.message,
    });
  }
});

// ═══════════════════════════════════════════
// METRICS ENDPOINT (Prometheus format)
// ═══════════════════════════════════════════

const promClient = require("prom-client");
const register = new promClient.Registry();

// Default metrics (CPU, memory, etc.)
promClient.collectDefaultMetrics({ register });

// Custom metrics
const httpRequestDuration = new promClient.Histogram({
  name: "http_request_duration_seconds",
  help: "Duration of HTTP requests in seconds",
  labelNames: ["method", "route", "status_code"],
  registers: [register],
});

// Track request duration
app.use((req, res, next) => {
  const start = Date.now();

  res.on("finish", () => {
    const duration = (Date.now() - start) / 1000;
    httpRequestDuration
      .labels(req.method, req.route?.path || req.path, res.statusCode)
      .observe(duration);
  });

  next();
});

// Expose metrics endpoint
app.get("/metrics", async (req, res) => {
  res.set("Content-Type", register.contentType);
  res.end(await register.metrics());
});

// ═══════════════════════════════════════════
// PERFORMANCE MONITORING
// ═══════════════════════════════════════════

// Monitor event loop lag
const eventLoopLag = new promClient.Gauge({
  name: "nodejs_eventloop_lag_seconds",
  help: "Event loop lag in seconds",
  registers: [register],
});

setInterval(() => {
  const start = Date.now();
  setImmediate(() => {
    const lag = (Date.now() - start) / 1000;
    eventLoopLag.set(lag);

    if (lag > 0.1) {
      logger.warn("High event loop lag detected", { lag });
    }
  });
}, 5000);

// Monitor memory usage
setInterval(() => {
  const usage = process.memoryUsage();
  const heapUsedPercent = (usage.heapUsed / usage.heapTotal) * 100;

  logger.info("Memory usage", {
    heapUsed: Math.round(usage.heapUsed / 1024 / 1024) + "MB",
    heapTotal: Math.round(usage.heapTotal / 1024 / 1024) + "MB",
    heapUsedPercent: heapUsedPercent.toFixed(2) + "%",
  });

  if (heapUsedPercent > 90) {
    logger.error("Critical: High memory usage", { usage });
  }
}, 60000);
```

### Monitoring Services Integration

```bash
# ═══════════════════════════════════════════
# MONITORING SERVICES
# ═══════════════════════════════════════════

# ─────────────────────────────────────────
# SENTRY (Error Tracking)
# ─────────────────────────────────────────
# → https://sentry.io
# • 5k errors/month free
# • Source maps support
# • Release tracking
# • Performance monitoring

npm install @sentry/node

# Setup in app:
const Sentry = require('@sentry/node');
Sentry.init({ dsn: process.env.SENTRY_DSN });

# ─────────────────────────────────────────
# BETTER STACK (Formerly Logtail)
# ─────────────────────────────────────────
# → https://betterstack.com
# • Structured logging
# • Log aggregation
# • Alerting

npm install @logtail/node

const { Logtail } = require('@logtail/node');
const logtail = new Logtail(process.env.LOGTAIL_TOKEN);

logtail.info('User logged in', { userId: 123 });

# ─────────────────────────────────────────
# UPTIME MONITORING
# ─────────────────────────────────────────

# UptimeRobot → https://uptimerobot.com
# • 50 monitors free
# • 5-minute checks
# • Email/SMS/Slack alerts

# Pingdom → https://pingdom.com
# • 30-day free trial
# • Real user monitoring
# • Transaction monitoring

# Better Uptime → https://betterstack.com/uptime
# • Modern UI
# • Status pages
# • On-call scheduling

# ─────────────────────────────────────────
# APPLICATION PERFORMANCE (APM)
# ─────────────────────────────────────────

# New Relic → https://newrelic.com
npm install newrelic

# Datadog → https://datadoghq.com
npm install dd-trace

# AppSignal → https://appsignal.com
npm install @appsignal/nodejs

# ─────────────────────────────────────────
# REAL USER MONITORING (RUM)
# ─────────────────────────────────────────

# Google Analytics
# Mixpanel
# Amplitude
# PostHog (open-source)
```

### Log Aggregation & Analysis

```bash
# ═══════════════════════════════════════════
# LOG MANAGEMENT PLATFORMS
# ═══════════════════════════════════════════

# Better Stack Logs
# → https://betterstack.com/logs
# • 1GB retention free
# • SQL-like query language
# • Live tailing

# Papertrail
# → https://papertrailapp.com
# • 50MB/day free
# • 7-day retention
# • Quick search

# Loggly
# → https://loggly.com
# • 200MB/day free
# • 7-day retention
# • JSON parsing

# Elasticsearch + Kibana
# Self-hosted or:
# • Elastic Cloud
# • AWS Elasticsearch

# ═══════════════════════════════════════════
# QUERY EXAMPLES
# ═══════════════════════════════════════════

# Find errors in last hour
level:error AND timestamp:[now-1h TO now]

# Find slow requests (>1s)
duration:>1000 AND path:/api/*

# Find specific user activity
userId:123 AND action:login

# Find database errors
message:"database connection" AND level:error
```

---

<div align="center">

## 💰 Cost Optimization

_Deploy smartly, spend wisely_ 💸

</div>

### Cost Comparison & Tips

```
═══════════════════════════════════════════════════════════════
MONTHLY COST ESTIMATES (Small API - ~100k requests/month)
═══════════════════════════════════════════════════════════════

┌─────────────────┬──────────────┬──────────────┬─────────────┐
│ Platform        │ Free Tier    │ Paid (Small) │ Paid (Med)  │
├─────────────────┼──────────────┼──────────────┼─────────────┤
│ Cyclic          │ ✅ FREE      │ $1/mo        │ $5-10/mo    │
│                 │ Generous     │              │             │
├─────────────────┼──────────────┼──────────────┼─────────────┤
│ Railway         │ $5 credit    │ $5-10/mo     │ $20-50/mo   │
│                 │ (usage-based)│              │             │
├─────────────────┼──────────────┼──────────────┼─────────────┤
│ Fly.io          │ 3 VMs free   │ $5-15/mo     │ $30-80/mo   │
│                 │ 160GB BW     │              │             │
├─────────────────┼──────────────┼──────────────┼─────────────┤
│ Render          │ 750hrs free  │ $7/mo        │ $25-50/mo   │
│                 │ (spins down) │ (always on)  │             │
├─────────────────┼──────────────┼──────────────┼─────────────┤
│ Heroku          │ None         │ $7/mo        │ $25-50/mo   │
│                 │              │ (eco dyno)   │             │
├─────────────────┼──────────────┼──────────────┼─────────────┤
│ AWS Lambda      │ 1M req free  │ $0-5/mo      │ $10-30/mo   │
│                 │              │ (pay-per-use)│             │
├─────────────────┼──────────────┼──────────────┼─────────────┤
│ Cloudflare      │ 100k req/day │ $5/10M req   │ $20-50/mo   │
│ Workers         │              │              │             │
└─────────────────┴──────────────┴──────────────┴─────────────┘

DATABASE COSTS:

┌─────────────────┬──────────────┬──────────────┬─────────────┐
│ Service         │ Free Tier    │ Small App    │ Medium App  │
├─────────────────┼──────────────┼──────────────┼─────────────┤
│ Neon            │ 0.5GB        │ $19/mo       │ $69/mo      │
│ (PostgreSQL)    │ 3GB storage  │              │             │
├─────────────────┼──────────────┼──────────────┼─────────────┤
│ Supabase        │ 500MB        │ $25/mo       │ $99/mo      │
│ (PostgreSQL+)   │ 2 projects   │              │             │
├─────────────────┼──────────────┼──────────────┼─────────────┤
│ PlanetScale     │ 5GB          │ $29/mo       │ $99/mo      │
│ (MySQL)         │ 1B reads     │              │             │
├─────────────────┼──────────────┼──────────────┼─────────────┤
│ MongoDB Atlas   │ 512MB        │ $9/mo        │ $57/mo      │
│                 │ Shared       │              │             │
├─────────────────┼──────────────┼──────────────┼─────────────┤
│ Railway DB      │ Included     │ ~$5/mo       │ ~$20/mo     │
│                 │ with project │              │             │
└─────────────────┴──────────────┴──────────────┴─────────────┘

TOTAL COST ESTIMATES:

🎯 Personal Project (Low Traffic):
   → Cyclic + Supabase Free = $0/month
   → Railway + Neon Free = $0-5/month

🚀 Startup/MVP (Moderate Traffic):
   → Railway + Supabase = $30-35/month
   → Fly.io + PlanetScale = $35-45/month

💼 Growing Business (High Traffic):
   → Fly.io + Supabase Pro = $90-120/month
   → AWS Lambda + RDS = $80-150/month
   → Railway (scaled) + Neon = $100-150/month
```

### Cost Optimization Strategies

```javascript
// ═══════════════════════════════════════════
// CACHING STRATEGIES
// ═══════════════════════════════════════════

// 1. In-Memory Caching (Node-Cache)
const NodeCache = require("node-cache");
const cache = new NodeCache({ stdTTL: 600 }); // 10 minutes

app.get("/api/users", async (req, res) => {
  // Check cache first
  const cacheKey = "all_users";
  const cached = cache.get(cacheKey);

  if (cached) {
    return res.json(cached);
  }

  // Fetch from database
  const users = await db.query("SELECT * FROM users");

  // Store in cache
  cache.set(cacheKey, users);

  res.json(users);
});

// 2. Redis Caching (Production)
const Redis = require("ioredis");
const redis = new Redis(process.env.REDIS_URL);

async function getCachedData(key, fetchFunction, ttl = 600) {
  // Try to get from cache
  const cached = await redis.get(key);

  if (cached) {
    return JSON.parse(cached);
  }

  // Fetch data
  const data = await fetchFunction();

  // Cache it
  await redis.setex(key, ttl, JSON.stringify(data));

  return data;
}

// Usage
app.get("/api/posts", async (req, res) => {
  const posts = await getCachedData(
    "posts:all",
    () => db.query("SELECT * FROM posts"),
    300 // 5 minutes
  );

  res.json(posts);
});

// 3. HTTP Caching Headers
app.get("/api/public-data", (req, res) => {
  res.set({
    "Cache-Control": "public, max-age=300", // Cache for 5 minutes
    ETag: generateETag(data),
    "Last-Modified": data.updatedAt,
  });

  res.json(data);
});

// ═══════════════════════════════════════════
// DATABASE QUERY OPTIMIZATION
// ═══════════════════════════════════════════

// ❌ Bad: N+1 query problem
async function getBadPosts() {
  const posts = await db.query("SELECT * FROM posts");

  for (const post of posts) {
    // Separate query for each post!
    post.author = await db.query("SELECT * FROM users WHERE id = $1", [
      post.author_id,
    ]);
  }

  return posts;
}

// ✅ Good: Join query
async function getGoodPosts() {
  const { rows } = await db.query(`
    SELECT
      posts.*,
      users.name as author_name,
      users.email as author_email
    FROM posts
    JOIN users ON posts.author_id = users.id
  `);

  return rows;
}

// ✅ Good: Batch query
async function getBatchPosts() {
  const posts = await db.query("SELECT * FROM posts");
  const authorIds = posts.map((p) => p.author_id);

  const authors = await db.query("SELECT * FROM users WHERE id = ANY($1)", [
    authorIds,
  ]);

  // Map authors to posts
  const authorMap = new Map(authors.map((a) => [a.id, a]));
  posts.forEach((post) => {
    post.author = authorMap.get(post.author_id);
  });

  return posts;
}

// ═══════════════════════════════════════════
// SERVERLESS OPTIMIZATION (Reduce Cold Starts)
// ═══════════════════════════════════════════

// 1. Keep package size small
// - Use webpack/esbuild to bundle
// - Remove unused dependencies
// - Use layers for common deps

// 2. Initialize connections outside handler
const db = new Pool(connectionConfig); // ✅ Outside

exports.handler = async (event) => {
  // ❌ Don't initialize here
  // const db = new Pool(connectionConfig);

  // Use existing connection
  const result = await db.query("...");
  return result;
};

// 3. Implement connection pooling
const pool = new Pool({
  connectionString: process.env.DATABASE_URL,
  max: 1, // Serverless: use 1 connection per instance
  idleTimeoutMillis: 30000,
});

// 4. Use HTTP keep-alive for external APIs
const https = require("https");
const agent = new https.Agent({
  keepAlive: true,
  maxSockets: 50,
});

const axios = require("axios");
const api = axios.create({
  httpsAgent: agent,
});

// ═══════════════════════════════════════════
// COMPRESSION
// ═══════════════════════════════════════════

const compression = require("compression");

app.use(
  compression({
    filter: (req, res) => {
      if (req.headers["x-no-compression"]) {
        return false;
      }
      return compression.filter(req, res);
    },
    level: 6, // Balance between speed and compression
  })
);

// ═══════════════════════════════════════════
// RATE LIMITING (Prevent Abuse)
// ═══════════════════════════════════════════

const rateLimit = require("express-rate-limit");

// Prevent excessive requests
const limiter = rateLimit({
  windowMs: 15 * 60 * 1000, // 15 minutes
  max: 100,
  standardHeaders: true,
  legacyHeaders: false,
});

app.use("/api/", limiter);

// ═══════════════════════════════════════════
// LAZY LOADING & PAGINATION
// ═══════════════════════════════════════════

// ❌ Bad: Load all data
app.get("/api/posts", async (req, res) => {
  const posts = await db.query("SELECT * FROM posts");
  res.json(posts); // Could be thousands of records!
});

// ✅ Good: Pagination
app.get("/api/posts", async (req, res) => {
  const page = parseInt(req.query.page) || 1;
  const limit = parseInt(req.query.limit) || 20;
  const offset = (page - 1) * limit;

  const { rows } = await db.query(
    "SELECT * FROM posts ORDER BY created_at DESC LIMIT $1 OFFSET $2",
    [limit, offset]
  );

  const {
    rows: [{ count }],
  } = await db.query("SELECT COUNT(*) FROM posts");

  res.json({
    data: rows,
    pagination: {
      page,
      limit,
      total: parseInt(count),
      totalPages: Math.ceil(count / limit),
    },
  });
});

// ✅ Good: Cursor-based pagination (better performance)
app.get("/api/posts", async (req, res) => {
  const cursor = req.query.cursor;
  const limit = parseInt(req.query.limit) || 20;

  const query = cursor
    ? "SELECT * FROM posts WHERE id < $1 ORDER BY id DESC LIMIT $2"
    : "SELECT * FROM posts ORDER BY id DESC LIMIT $1";

  const params = cursor ? [cursor, limit] : [limit];
  const { rows } = await db.query(query, params);

  const nextCursor = rows.length > 0 ? rows[rows.length - 1].id : null;

  res.json({
    data: rows,
    nextCursor,
  });
});
```

### Platform-Specific Cost Tips

```bash
# ═══════════════════════════════════════════
# RAILWAY COST OPTIMIZATION
# ═══════════════════════════════════════════

# ✅ Set resource limits
# Railway → Service → Settings → Resources
# CPU: 0.5 vCPU (instead of default 1)
# Memory: 512MB (instead of default 1GB)

# ✅ Use sleep mode for dev environments
# Automatically shuts down after inactivity

# ✅ Monitor usage
railway usage

# ═══════════════════════════════════════════
# FLY.IO COST OPTIMIZATION
# ═══════════════════════════════════════════

# ✅ Use shared-cpu-1x for low-traffic apps
flyctl scale vm shared-cpu-1x

# ✅ Enable auto-stop/start
[deploy]
  strategy = "rolling"
auto_stop_machines = true
auto_start_machines = true
min_machines_running = 0

# ✅ Use Fly.io free tier wisely
# 3 shared-cpu-1x VMs (256MB RAM each) = FREE
# 160GB bandwidth = FREE
# 3GB volume storage = FREE

# ═══════════════════════════════════════════
# VERCEL/NETLIFY COST OPTIMIZATION
# ═══════════════════════════════════════════

# ✅ Optimize function execution time
# - Reduce cold starts
# - Cache responses
# - Use edge functions when possible

# ✅ Set function memory limits
# vercel.json
{
  "functions": {
    "api/**/*.js": {
      "memory": 512  // Lower = cheaper
    }
  }
}

# ═══════════════════════════════════════════
# AWS LAMBDA COST OPTIMIZATION
# ═══════════════════════════════════════════

# ✅ Right-size memory allocation
# Test different memory sizes (128MB - 3008MB)
# More memory = faster execution = sometimes cheaper!

# ✅ Use Provisioned Concurrency only when needed
# Eliminates cold starts but costs more

# ✅ Set reasonable timeout
# Don't set 15 minutes if you only need 10 seconds

# ✅ Use Lambda Layers for common dependencies
# Reduces deployment package size

# ═══════════════════════════════════════════
# DATABASE COST OPTIMIZATION
# ═══════════════════════════════════════════

# ✅ Use connection pooling
# Reduce database connections = lower costs

# ✅ Implement query caching
# Reduce database reads

# ✅ Archive old data
# Move old records to cheaper storage (S3, etc.)

# ✅ Use read replicas (only if needed)
# Don't over-provision

# ✅ Monitor slow queries
# Optimize expensive queries

# ═══════════════════════════════════════════
# GENERAL TIPS
# ═══════════════════════════════════════════

# ✅ Use CDN for static assets
# Cloudflare (free), AWS CloudFront

# ✅ Implement caching at every level
# - Browser cache (HTTP headers)
# - CDN cache
# - API cache (Redis)
# - Database query cache

# ✅ Compress responses
# gzip/brotli compression

# ✅ Monitor and alert
# Set up budget alerts
# Track usage metrics

# ✅ Scale down dev/staging environments
# Use smaller instances
# Shut down when not needed

# ✅ Review usage monthly
# Identify optimization opportunities
# Remove unused resources
```

---

<div align="center">

## 🐛 Troubleshooting

_Common issues and how to fix them_ 🔧

</div>

### Common Deployment Issues

```bash
# ═══════════════════════════════════════════
# ISSUE: Build Fails
# ═══════════════════════════════════════════

# ❌ Error: "MODULE_NOT_FOUND"
# Cause: Missing dependencies

# Solution 1: Install missing package
npm install missing-package

# Solution 2: Clear cache and reinstall
rm -rf node_modules package-lock.json
npm install

# Solution 3: Check package.json
# Ensure all dependencies are listed
npm install --save missing-package

# ═══════════════════════════════════════════
# ISSUE: Environment Variables Not Working
# ═══════════════════════════════════════════

# ❌ Error: "Cannot read property of undefined"
# Cause: Environment variables not set or not loaded

# Solution 1: Check if variables are set
# Railway: railway variables
# Vercel: vercel env ls
# Fly.io: flyctl secrets list

# Solution 2: Load .env in development
require('dotenv').config();

# Solution 3: Check variable names (case-sensitive!)
# DATABASE_URL ≠ database_url

# Solution 4: Restart app after setting variables
railway up
vercel --prod
flyctl deploy

# ═══════════════════════════════════════════
# ISSUE: Port Binding Error
# ═══════════════════════════════════════════

# ❌ Error: "EADDRINUSE: address already in use"
# Cause: App not listening on correct port

# Solution: Use platform-provided PORT
const PORT = process.env.PORT || 3000;
app.listen(PORT, '0.0.0.0', () => {
  console.log(`Server running on port ${PORT}`);
});

# Important: Listen on 0.0.0.0, not localhost/127.0.0.1

# ═══════════════════════════════════════════
# ISSUE: Database Connection Fails
# ═══════════════════════════════════════════

# ❌ Error: "Connection refused" or "Timeout"

# Solution 1: Check connection string
console.log('DB URL:', process.env.DATABASE_URL);

# Solution 2: Enable SSL for production databases
const pool = new Pool({
  connectionString: process.env.DATABASE_URL,
  ssl: process.env.NODE_ENV === 'production'
    ? { rejectUnauthorized: false }
    : false
});

# Solution 3: Check firewall/network rules
# Allow inbound connections from platform IPs

# Solution 4: Use connection pooling
# Limit concurrent connections

# ═══════════════════════════════════════════
# ISSUE: App Crashes After Deployment
# ═══════════════════════════════════════════

# Check logs:
# Railway: railway logs
# Vercel: vercel logs
# Fly.io: flyctl logs
# Heroku: heroku logs --tail

# Common causes:

# 1. Missing start script in package.json
{
  "scripts": {
    "start": "node server.js"
  }
}

# 2. Uncaught exceptions
process.on('uncaughtException', (err) => {
  console.error('Uncaught Exception:', err);
  process.exit(1);
});

process.on('unhandledRejection', (reason, promise) => {
  console.error('Unhandled Rejection:', reason);
  process.exit(1);
});

# 3. Memory issues
# Increase memory limit or optimize code

# ═══════════════════════════════════════════
# ISSUE: Slow Response Times
# ═══════════════════════════════════════════

# Debug steps:

# 1. Add timing logs
const start = Date.now();
const result = await slowOperation();
console.log(`Operation took ${Date.now() - start}ms`);

# 2. Profile database queries
# Use EXPLAIN ANALYZE in PostgreSQL

# 3. Check external API latency
# Implement timeouts

# 4. Monitor event loop lag
# Use clinic.js or similar tools

# Solutions:
# - Add caching
# - Optimize database queries
# - Use CDN for static assets
# - Implement pagination
# - Add database indexes

# ═══════════════════════════════════════════
# ISSUE: CORS Errors
# ═══════════════════════════════════════════

# ❌ Error: "Access-Control-Allow-Origin"

# Solution: Configure CORS properly
const cors = require('cors');

# Allow specific origins
app.use(cors({
  origin: ['https://yourdomain.com', 'http://localhost:3000'],
  credentials: true
}));

# Handle preflight requests
app.options('*', cors());

# ═══════════════════════════════════════════
# ISSUE: Serverless Function Timeout
# ═══════════════════════════════════════════

# Causes:
# - Function takes too long
# - Cold start + execution > timeout limit

# Solutions:

# 1. Increase timeout (if possible)
# Vercel: max 10s (Hobby), 60s (Pro)
# Netlify: 10s (free), 26s (paid)
# AWS Lambda: up to 15 minutes

# 2. Optimize function
# - Reduce dependencies
# - Use connection pooling
# - Implement caching

# 3. Use background functions (if available)
# Netlify: name-background.js (15 minutes)

# 4. Split into smaller functions
# Break monolithic function into multiple

# ═══════════════════════════════════════════
# ISSUE: High Memory Usage
# ═══════════════════════════════════════════

# Monitor memory:
setInterval(() => {
  const usage = process.memoryUsage();
  console.log({
    rss: `${Math.round(usage.rss / 1024 / 1024)}MB`,
    heapTotal: `${Math.round(usage.heapTotal / 1024 / 1024)}MB`,
    heapUsed: `${Math.round(usage.heapUsed / 1024 / 1024)}MB`
  });
}, 60000);

# Common causes:
# - Memory leaks
# - Large data processing
# - Not closing database connections
# - Event listener leaks

# Solutions:
# - Use streaming for large data
# - Implement pagination
# - Close connections properly
# - Use --max-old-space-size flag if needed

# ═══════════════════════════════════════════
# DEBUGGING TIPS
# ═══════════════════════════════════════════

# 1. Enable detailed logging
process.env.DEBUG = '*';

# 2. Test locally with production environment
# Railway: railway run npm start
# Vercel: vercel dev
# Fly.io: flyctl proxy

# 3. Use health check endpoints
# Monitor /health endpoint regularly

# 4. Set up error tracking (Sentry)
# Get notified when errors occur

# 5. Test with production data (anonymized)
# Reproduce issues locally

# 6. Use Docker locally
# Match production environment exactly

# 7. Check platform status pages
# Railway: status.railway.app
# Vercel: vercel-status.com
# Fly.io: status.flyio.net
```

---

<div align="center">

## 💡 Best Practices

_Production-ready deployment checklist_ ✅

</div>

### Pre-Deployment Checklist

```bash
# ═══════════════════════════════════════════
# CODE QUALITY
# ═══════════════════════════════════════════

✅ Code linted (ESLint, Prettier)
✅ Tests passing (unit, integration)
✅ No console.log in production code
✅ Error handling implemented
✅ Input validation on all endpoints
✅ Database queries optimized
✅ Dependencies up to date (npm audit)
✅ TypeScript types correct (if using TS)

# ═══════════════════════════════════════════
# SECURITY
# ═══════════════════════════════════════════

✅ Environment variables set (not hardcoded)
✅ Secrets not committed to Git
✅ HTTPS enabled
✅ CORS configured properly
✅ Rate limiting implemented
✅ Authentication/authorization working
✅ SQL injection prevention (parameterized queries)
✅ XSS prevention (input sanitization)
✅ Security headers set (helmet.js)
✅ Dependencies scanned for vulnerabilities

# ═══════════════════════════════════════════
# PERFORMANCE
# ═══════════════════════════════════════════

✅ Response compression enabled (gzip/brotli)
✅ Caching strategy implemented
✅ Database indexes created
✅ N+1 queries eliminated
✅ Pagination implemented
✅ Connection pooling configured
✅ CDN set up for static assets
✅ Image optimization

# ═══════════════════════════════════════════
# MONITORING & LOGGING
# ═══════════════════════════════════════════

✅ Structured logging implemented
✅ Error tracking set up (Sentry, etc.)
✅ Health check endpoint added
✅ Metrics endpoint added (optional)
✅ Uptime monitoring configured
✅ Log retention policy set
✅ Alerting configured
✅ Performance monitoring enabled

# ═══════════════════════════════════════════
# INFRASTRUCTURE
# ═══════════════════════════════════════════

✅ Environment variables documented (.env.example)
✅ README updated with setup instructions
✅ Database migrations working
✅ Database backups configured
✅ Rollback strategy defined
✅ Scaling strategy planned
✅ CI/CD pipeline set up
✅ Staging environment available

# ═══════════════════════════════════════════
# DOCUMENTATION
# ═══════════════════════════════════════════

✅ API documentation (Swagger/OpenAPI)
✅ Setup instructions clear
✅ Environment variables documented
✅ Deployment process documented
✅ Troubleshooting guide available
✅ Architecture diagrams updated
✅ Changelog maintained

# ═══════════════════════════════════════════
# TESTING
# ═══════════════════════════════════════════

✅ Unit tests written
✅ Integration tests passing
✅ End-to-end tests working
✅ Load testing completed
✅ Security testing done
✅ Browser testing (if frontend)
✅ Mobile testing (if applicable)
```

### Production Deployment Workflow

```bash
# ═══════════════════════════════════════════
# STEP-BY-STEP DEPLOYMENT PROCESS
# ═══════════════════════════════════════════

# 1. LOCAL TESTING
npm test                    # Run all tests
npm run lint                # Check code quality
npm audit                   # Check vulnerabilities
npm run build               # Build for production

# 2. CREATE RELEASE BRANCH (Git Flow)
git checkout -b release/v1.2.0

# 3. UPDATE VERSION
npm version minor           # Updates package.json version
# Or manually update version

# 4. UPDATE CHANGELOG
# Document changes in CHANGELOG.md
- Added: New features
- Changed: Updates to existing features
- Fixed: Bug fixes
- Removed: Deprecated features

# 5. COMMIT CHANGES
git add .
git commit -m "chore: release v1.2.0"

# 6. MERGE TO MAIN
git checkout main
git merge release/v1.2.0

# 7. CREATE GIT TAG
git tag -a v1.2.0 -m "Release v1.2.0"
git push origin main --tags

# 8. DEPLOY TO STAGING (Automatic via CI/CD)
# Test in staging environment

# 9. RUN SMOKE TESTS
curl https://staging-api.yourdomain.com/health
curl https://staging-api.yourdomain.com/api/users

# 10. DEPLOY TO PRODUCTION
# Manual trigger or automatic from main branch

# 11. VERIFY DEPLOYMENT
curl https://api.yourdomain.com/health
# Check error monitoring dashboard
# Check application metrics

# 12. MONITOR
# Watch logs for first 10-15 minutes
# Check error rates
# Monitor response times

# 13. ANNOUNCE DEPLOYMENT
# Notify team
# Update status page (if applicable)
# Announce to users (if major release)

# 14. DOCUMENT
# Update internal wiki
# Add to deployment log
# Note any issues encountered
```

### Code Organization Best Practices

```javascript
// ═══════════════════════════════════════════
// RECOMMENDED PROJECT STRUCTURE
// ═══════════════════════════════════════════

project-root/
├── src/
│   ├── config/              # Configuration files
│   │   ├── database.js
│   │   ├── redis.js
│   │   └── app.js
│   ├── controllers/         # Route controllers
│   │   ├── userController.js
│   │   └── postController.js
│   ├── models/              # Data models
│   │   ├── User.js
│   │   └── Post.js
│   ├── routes/              # API routes
│   │   ├── userRoutes.js
│   │   └── postRoutes.js
│   ├── middleware/          # Custom middleware
│   │   ├── auth.js
│   │   ├── validation.js
│   │   └── errorHandler.js
│   ├── services/            # Business logic
│   │   ├── userService.js
│   │   └── emailService.js
│   ├── utils/               # Utility functions
│   │   ├── logger.js
│   │   └── helpers.js
│   ├── validators/          # Input validators
│   │   └── userValidator.js
│   └── app.js               # Express app setup
├── tests/                   # Test files
│   ├── unit/
│   └── integration/
├── scripts/                 # Utility scripts
│   ├── migrate.js
│   └── seed.js
├── .env.example             # Environment template
├── .gitignore
├── package.json
└── README.md

// ═══════════════════════════════════════════
// EXAMPLE: Clean Code Structure
// ═══════════════════════════════════════════

// src/controllers/userController.js
const userService = require('../services/userService');
const { validationResult } = require('express-validator');

exports.getUsers = async (req, res, next) => {
  try {
    const users = await userService.getAllUsers();
    res.json(users);
  } catch (error) {
    next(error);
  }
};

exports.createUser = async (req, res, next) => {
  try {
    // Validate input
    const errors = validationResult(req);
    if (!errors.isEmpty()) {
      return res.status(400).json({ errors: errors.array() });
    }

    // Create user via service
    const user = await userService.createUser(req.body);

    res.status(201).json(user);
  } catch (error) {
    next(error);
  }
};

// src/services/userService.js
const User = require('../models/User');
const bcrypt = require('bcrypt');

exports.getAllUsers = async () => {
  return await User.findAll();
};

exports.createUser = async (userData) => {
  // Business logic
  const hashedPassword = await bcrypt.hash(userData.password, 10);

  return await User.create({
    ...userData,
    password: hashedPassword
  });
};

// src/routes/userRoutes.js
const express = require('express');
const router = express.Router();
const userController = require('../controllers/userController');
const { validateUser } = require('../validators/userValidator');
const { authenticate } = require('../middleware/auth');

router.get('/', authenticate, userController.getUsers);
router.post('/', validateUser, userController.createUser);

module.exports = router;

// src/app.js
const express = require('express');
const helmet = require('helmet');
const cors = require('cors');
const userRoutes = require('./routes/userRoutes');
const errorHandler = require('./middleware/errorHandler');

const app = express();

// Middleware
app.use(helmet());
app.use(cors());
app.use(express.json());

// Routes
app.use('/api/users', userRoutes);

// Error handling
app.use(errorHandler);

module.exports = app;

// server.js (entry point)
const app = require('./src/app');
const { initDatabase } = require('./src/config/database');

const PORT = process.env.PORT || 3000;

async function start() {
  await initDatabase();

  app.listen(PORT, '0.0.0.0', () => {
    console.log(`Server running on port ${PORT}`);
  });
}

start().catch(err => {
  console.error('Failed to start server:', err);
  process.exit(1);
});
```

---

<div align="center">

## 🎯 Quick Start Guides

_Get deployed in minutes_ ⚡

</div>

### Quick Deploy: Railway

```bash
# ═══════════════════════════════════════════
# DEPLOY TO RAILWAY IN 5 MINUTES
# ═══════════════════════════════════════════

# 1. Install CLI
npm install -g @railway/cli

# 2. Login
railway login

# 3. Initialize project
railway init

# 4. Add PostgreSQL (optional)
railway add postgresql

# 5. Set environment variables
railway variables set NODE_ENV=production
railway variables set API_KEY=your-secret-key

# 6. Deploy
railway up

# 7. Open in browser
railway open

# Done! Your app is live 🎉
```

### Quick Deploy: Fly.io

```bash
# ═══════════════════════════════════════════
# DEPLOY TO FLY.IO IN 5 MINUTES
# ═══════════════════════════════════════════

# 1. Install flyctl
curl -L https://fly.io/install.sh | sh

# 2. Login
flyctl auth login

# 3. Launch app (creates fly.toml)
flyctl launch

# 4. Deploy
flyctl deploy

# 5. Open in browser
flyctl open

# Done! Your app is live globally 🌍
```

### Quick Deploy: Vercel

```bash
# ═══════════════════════════════════════════
# DEPLOY TO VERCEL IN 3 MINUTES
# ═══════════════════════════════════════════

# 1. Install CLI
npm i -g vercel

# 2. Deploy (in project directory)
vercel

# 3. Deploy to production
vercel --prod

# Or just use GitHub integration (even easier!)
# 1. Push to GitHub
# 2. Import in Vercel dashboard
# 3. Auto-deploys on every push

# Done! Your API is live ⚡
```

---

<div align="center">

## 🎓 Learning Resources

_Master backend deployment_ 📚

</div>

### Official Documentation

```
🚂 Railway
   → https://docs.railway.app

✈️ Fly.io
   → https://fly.io/docs

🎨 Render
   → https://render.com/docs

▲ Vercel
   → https://vercel.com/docs

🌐 Netlify
   → https://docs.netlify.com

☁️ Cloudflare Workers
   → https://developers.cloudflare.com/workers

🔶 AWS Lambda
   → https://docs.aws.amazon.com/lambda
```

### YouTube Channels

```
🎥 Fireship
   → Quick tech overviews

🎥 Traversy Media
   → Full tutorials

🎥 Web Dev Simplified
   → Beginner-friendly

🎥 Theo - t3.gg
   → Modern best practices
```

### Community & Support

```
💬 Railway Discord
   → https://discord.gg/railway

💬 Fly.io Community
   → https://community.fly.io

💬 Render Community
   → https://community.render.com

💬 Dev.to
   → https://dev.to

💬 Reddit /r/webdev
   → https://reddit.com/r/webdev
```

---

<div align="center">

## 🎉 Conclusion

</div>

**Congratulations!** You now have a complete guide to backend hosting! 🚀

### Remember:

✅ **Start Simple**: Use PaaS platforms for quick deployment
✅ **Iterate Fast**: Deploy often, learn from production
✅ **Monitor Everything**: Know what's happening in your app
✅ **Optimize Gradually**: Don't over-engineer early
✅ **Security First**: Never compromise on security
✅ **Document Well**: Future you will thank present you

### Recommended Path:

```
🎯 Learning:
   1. Deploy to Railway (easiest)
   2. Add database
   3. Set up monitoring
   4. Implement caching
   5. Add CI/CD

🚀 Production:
   1. Choose right platform for scale
   2. Implement all security practices
   3. Set up comprehensive monitoring
   4. Plan scaling strategy
   5. Document everything
```

---

<div align="center">

**Built with ☁️ by MrDib for Backend Developers**

_May your APIs always return 200 OK and your deployments always succeed!_ ⚡

**Now go build something amazing!** 🎉

---

**Found this helpful? Star the repo ⭐ and share with fellow developers!**

_Happy Deploying!_ 🚀

</div>
