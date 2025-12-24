<div align="center">

# 🚀 Deployment Strategies

### _Ship code like a pro - safely, quickly, and without breaking production_ 💪

![Deployment](https://img.shields.io/badge/Deploy-Zero_Downtime-green?style=for-the-badge)
![Strategies](https://img.shields.io/badge/Strategies-7+-blue?style=for-the-badge)
![Reliability](https://img.shields.io/badge/Reliability-99.99%25-gold?style=for-the-badge)

</div>

---

## 📚 Table of Contents

- [🎯 Understanding Deployment Strategies](#-understanding-deployment-strategies)
- [🔄 Recreate Deployment](#-recreate-deployment)
- [🌊 Rolling Deployment](#-rolling-deployment)
- [💙💚 Blue-Green Deployment](#-blue-green-deployment)
- [🐤 Canary Deployment](#-canary-deployment)
- [🧪 A/B Testing](#-ab-testing)
- [🎭 Shadow Deployment](#-shadow-deployment)
- [🔀 Feature Flags](#-feature-flags)
- [🗄️ Database Migrations](#️-database-migrations)
- [🔙 Rollback Strategies](#-rollback-strategies)
- [📊 Monitoring & Observability](#-monitoring--observability)
- [🛠️ Tools & Platforms](#️-tools--platforms)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 🎯 Understanding Deployment Strategies

_Choose the right strategy for your use case_ 🎯

</div>

### Strategy Comparison Matrix

<div align="center">

| Strategy        | Downtime | Complexity | Rollback Speed | Resource Usage | Best For      |
| :-------------- | :------: | :--------: | :------------: | :------------: | :------------ |
| **Recreate**    |  ❌ Yes  |     ⭐     |     ⚡⚡⚡     |       💰       | Dev/Test      |
| **Rolling**     |  ✅ No   |    ⭐⭐    |      ⚡⚡      |      💰💰      | Most apps     |
| **Blue-Green**  |  ✅ No   |   ⭐⭐⭐   |   ⚡⚡⚡⚡⚡   |    💰💰💰💰    | Critical apps |
| **Canary**      |  ✅ No   |  ⭐⭐⭐⭐  |    ⚡⚡⚡⚡    |      💰💰      | Large scale   |
| **A/B Testing** |  ✅ No   | ⭐⭐⭐⭐⭐ |     ⚡⚡⚡     |      💰💰      | Features      |
| **Shadow**      |  ✅ No   | ⭐⭐⭐⭐⭐ |      N/A       |     💰💰💰     | Testing       |

</div>

---

### Decision Tree

```
🎯 Which Deployment Strategy Should You Use?

Can you afford downtime?
├─ No
│  ├─ Need instant rollback?
│  │  ├─ Yes + Have resources?
│  │  │  └─ ✅ Blue-Green (instant rollback, 2x resources)
│  │  └─ No
│  │     └─ ✅ Rolling (gradual, efficient)
│  ├─ Testing new features?
│  │  └─ ✅ Canary (gradual % of traffic)
│  ├─ Need user feedback?
│  │  └─ ✅ A/B Testing (specific user segments)
│  └─ Testing production load?
│     └─ ✅ Shadow (mirror traffic)
└─ Yes (Dev/Test only!)
   └─ ✅ Recreate (simplest, but downtime)

Still unsure?
└─ Start with Rolling
   Most balanced approach for production
```

---

<div align="center">

## 🔄 Recreate Deployment

_The simplest strategy (with downtime)_ ⏸️

</div>

### How It Works

```
Timeline:
┌──────────────┬───────────┬──────────────┐
│   Running    │ Downtime  │   Running    │
│   v1.0 ████  │           │  v2.0 ████   │
│              │  [STOP]   │              │
│              │  [START]  │              │
└──────────────┴───────────┴──────────────┘
     t=0          t=1-2min       t=3min

Process:
1. Stop all v1.0 instances
2. Deploy v2.0 code
3. Start all v2.0 instances
4. ⚠️ Users experience downtime during steps 1-3
```

---

### Kubernetes Implementation

```yaml
# ═══════════════════════════════════════════════════════════
# RECREATE DEPLOYMENT - KUBERNETES
# ═══════════════════════════════════════════════════════════

apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
  namespace: production
spec:
  replicas: 3
  strategy:
    type: Recreate # All old pods terminated before new ones start
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
        version: v2.0.0
    spec:
      containers:
        - name: app
          image: myregistry/my-app:v2.0.0
          ports:
            - containerPort: 8080
          resources:
            requests:
              memory: "256Mi"
              cpu: "250m"
            limits:
              memory: "512Mi"
              cpu: "500m"
          livenessProbe:
            httpGet:
              path: /health
              port: 8080
            initialDelaySeconds: 30
            periodSeconds: 10
          readinessProbe:
            httpGet:
              path: /ready
              port: 8080
            initialDelaySeconds: 10
            periodSeconds: 5
```

---

### Docker Compose Implementation

```yaml
# ═══════════════════════════════════════════════════════════
# RECREATE - DOCKER COMPOSE
# ═══════════════════════════════════════════════════════════

version: "3.8"

services:
  app:
    image: myapp:v2.0.0
    deploy:
      replicas: 3
      update_config:
        parallelism: 0 # Stop all instances
        delay: 0s
      restart_policy:
        condition: on-failure
    ports:
      - "8080:8080"
    environment:
      - NODE_ENV=production
```

**Deployment Command:**

```bash
# ═══════════════════════════════════════════════════════════
# RECREATE DEPLOYMENT SCRIPT
# ═══════════════════════════════════════════════════════════

#!/bin/bash
set -e

echo "🛑 Stopping current version..."
kubectl delete deployment my-app --grace-period=30

echo "⏳ Waiting for graceful shutdown..."
sleep 30

echo "🚀 Deploying new version..."
kubectl apply -f deployment-v2.yaml

echo "⏳ Waiting for deployment to be ready..."
kubectl wait --for=condition=available --timeout=300s deployment/my-app

echo "✅ Deployment complete!"

# Verify
kubectl get pods -l app=my-app
```

---

### Pros & Cons

```
✅ PROS:
• Simple to implement
• Clean state (no version mixing)
• Predictable behavior
• Easy to understand
• No extra infrastructure needed

❌ CONS:
• Downtime (usually 1-5 minutes)
• Bad user experience
• Risk if new version has issues
• Not suitable for production
• Can't test in production

🎯 USE WHEN:
✓ Development environments
✓ Testing environments
✓ Internal tools with maintenance windows
✓ Batch jobs
✓ Simplicity > availability

❌ DON'T USE FOR:
✗ Customer-facing production apps
✗ 24/7 services
✗ High-availability requirements
✗ SLA commitments
```

> **⚠️ Reality Check:** Recreate is fine for dev/test, but if you're using it in production, you're basically telling users "we don't care about your time." Don't be that company!

---

<div align="center">

## 🌊 Rolling Deployment

_Gradual replacement with zero downtime_ 🔄

</div>

### How It Works

```
Timeline (4 replicas):
┌──────────┬──────────┬──────────┬──────────┬──────────┐
│  Start   │  Step 1  │  Step 2  │  Step 3  │  Step 4  │
├──────────┼──────────┼──────────┼──────────┼──────────┤
│ v1 ████  │ v1 ███   │ v1 ██    │ v1 █     │ v2 ████  │
│          │ v2 █     │ v2 ██    │ v2 ███   │          │
└──────────┴──────────┴──────────┴──────────┴──────────┘

Process:
1. Deploy 1 instance of v2.0
2. Wait for health check ✓
3. Remove 1 instance of v1.0
4. Repeat steps 1-3 until complete
5. ✅ No downtime - always have instances serving traffic
```

---

### Kubernetes Implementation

```yaml
# ═══════════════════════════════════════════════════════════
# ROLLING DEPLOYMENT - KUBERNETES
# Production-ready configuration
# ═══════════════════════════════════════════════════════════

apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
  namespace: production
  labels:
    app: my-app
spec:
  replicas: 4
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxSurge: 1 # Max 1 pod above desired count (25%)
      maxUnavailable: 1 # Max 1 pod can be unavailable (25%)

  # How long to wait before considering deployment failed
  progressDeadlineSeconds: 600

  # Min seconds pod should be ready without crashes
  minReadySeconds: 30

  selector:
    matchLabels:
      app: my-app

  template:
    metadata:
      labels:
        app: my-app
        version: v2.0.0
    spec:
      # Graceful shutdown
      terminationGracePeriodSeconds: 60

      containers:
        - name: app
          image: myregistry/my-app:v2.0.0
          ports:
            - name: http
              containerPort: 8080
              protocol: TCP

          # Resource limits
          resources:
            requests:
              memory: "256Mi"
              cpu: "250m"
            limits:
              memory: "512Mi"
              cpu: "500m"

          # Liveness probe (restart if fails)
          livenessProbe:
            httpGet:
              path: /health
              port: 8080
              scheme: HTTP
            initialDelaySeconds: 30
            periodSeconds: 10
            timeoutSeconds: 5
            successThreshold: 1
            failureThreshold: 3

          # Readiness probe (remove from service if fails)
          readinessProbe:
            httpGet:
              path: /ready
              port: 8080
              scheme: HTTP
            initialDelaySeconds: 10
            periodSeconds: 5
            timeoutSeconds: 3
            successThreshold: 1
            failureThreshold: 3

          # Startup probe (for slow-starting apps)
          startupProbe:
            httpGet:
              path: /health
              port: 8080
            initialDelaySeconds: 0
            periodSeconds: 10
            timeoutSeconds: 3
            successThreshold: 1
            failureThreshold: 30 # 5 minutes to start

          # Environment variables
          env:
            - name: NODE_ENV
              value: "production"
            - name: LOG_LEVEL
              value: "info"

          # Graceful shutdown handler
          lifecycle:
            preStop:
              exec:
                command: ["/bin/sh", "-c", "sleep 15"] # Wait for load balancer to deregister
```

---

### Advanced Rolling Deployment Script

```bash
#!/bin/bash
# ═══════════════════════════════════════════════════════════
# ADVANCED ROLLING DEPLOYMENT SCRIPT
# With health checks, monitoring, and automatic rollback
# ═══════════════════════════════════════════════════════════

set -euo pipefail

# Configuration
APP_NAME="my-app"
NAMESPACE="production"
NEW_VERSION="v2.0.0"
MAX_WAIT_TIME=600  # 10 minutes
HEALTH_CHECK_URL="https://api.example.com/health"
ERROR_THRESHOLD=0.05  # 5% error rate threshold

# Colors for output
RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[1;33m'
NC='\033[0m' # No Color

log_info() {
    echo -e "${GREEN}[INFO]${NC} $1"
}

log_warn() {
    echo -e "${YELLOW}[WARN]${NC} $1"
}

log_error() {
    echo -e "${RED}[ERROR]${NC} $1"
}

# Function to check deployment health
check_deployment_health() {
    local deployment=$1
    local namespace=$2

    # Check if deployment is available
    if ! kubectl rollout status deployment/$deployment -n $namespace --timeout=${MAX_WAIT_TIME}s; then
        log_error "Deployment rollout failed!"
        return 1
    fi

    # Check pod health
    local ready_pods=$(kubectl get deployment $deployment -n $namespace -o jsonpath='{.status.readyReplicas}')
    local desired_pods=$(kubectl get deployment $deployment -n $namespace -o jsonpath='{.spec.replicas}')

    if [ "$ready_pods" != "$desired_pods" ]; then
        log_error "Not all pods are ready ($ready_pods/$desired_pods)"
        return 1
    fi

    log_info "All pods are healthy ($ready_pods/$desired_pods)"
    return 0
}

# Function to check application metrics
check_application_metrics() {
    log_info "Checking application metrics..."

    # Get error rate from Prometheus/monitoring system
    # This is a simplified example
    local error_rate=$(curl -s "$HEALTH_CHECK_URL/metrics" | grep error_rate | awk '{print $2}')

    if (( $(echo "$error_rate > $ERROR_THRESHOLD" | bc -l) )); then
        log_error "Error rate too high: $error_rate (threshold: $ERROR_THRESHOLD)"
        return 1
    fi

    log_info "Error rate is acceptable: $error_rate"
    return 0
}

# Function to perform rollback
perform_rollback() {
    log_error "🚨 ROLLING BACK DEPLOYMENT! 🚨"

    kubectl rollout undo deployment/$APP_NAME -n $NAMESPACE

    log_info "Waiting for rollback to complete..."
    kubectl rollout status deployment/$APP_NAME -n $NAMESPACE --timeout=300s

    log_info "✅ Rollback completed successfully"
}

# Main deployment function
main() {
    log_info "🚀 Starting rolling deployment of $APP_NAME:$NEW_VERSION"

    # 1. Update deployment
    log_info "Updating deployment manifest..."
    kubectl set image deployment/$APP_NAME $APP_NAME=myregistry/$APP_NAME:$NEW_VERSION -n $NAMESPACE

    # 2. Watch rollout
    log_info "Watching rollout progress..."
    if ! check_deployment_health "$APP_NAME" "$NAMESPACE"; then
        perform_rollback
        exit 1
    fi

    # 3. Wait for stabilization
    log_info "Waiting 60s for deployment to stabilize..."
    sleep 60

    # 4. Check application health
    if ! check_application_metrics; then
        perform_rollback
        exit 1
    fi

    # 5. Run smoke tests
    log_info "Running smoke tests..."
    if ! ./scripts/smoke-tests.sh; then
        log_error "Smoke tests failed!"
        perform_rollback
        exit 1
    fi

    # 6. Success!
    log_info "✅ Deployment completed successfully!"

    # 7. Notify team
    curl -X POST https://hooks.slack.com/services/YOUR/WEBHOOK/URL \
      -H 'Content-Type: application/json' \
      -d "{\"text\":\"✅ $APP_NAME:$NEW_VERSION deployed successfully!\"}"

    # 8. Document deployment
    kubectl annotate deployment/$APP_NAME -n $NAMESPACE \
      "deployment.kubernetes.io/deployed-by=$(whoami)" \
      "deployment.kubernetes.io/deployed-at=$(date -u +%Y-%m-%dT%H:%M:%SZ)" \
      "deployment.kubernetes.io/git-commit=$(git rev-parse HEAD)"
}

# Cleanup on exit
trap 'log_warn "Deployment interrupted!"' INT TERM

# Run main function
main "$@"
```

---

### Pros & Cons

```
✅ PROS:
• Zero downtime
• Gradual rollout reduces risk
• Easy to understand
• Built-in to most platforms
• Automatic rollback on failure
• Cost-effective (no 2x resources)

❌ CONS:
• Both versions run simultaneously
• Rollback takes time (not instant)
• Database compatibility required
• Can't easily test full new version first
• Complex if app doesn't support mixed versions

🎯 USE WHEN:
✓ Standard production deployments
✓ Stateless applications
✓ Backward-compatible changes
✓ Limited resources (can't afford 2x)
✓ Need zero downtime

⚠️ CHALLENGES:
• Database schema changes
• Breaking API changes
• Incompatible versions
• Shared state
```

---

### Health Check Examples

```javascript
// ═══════════════════════════════════════════════════════════
// HEALTH CHECK ENDPOINTS - EXPRESS.JS
// ═══════════════════════════════════════════════════════════

const express = require("express");
const app = express();

// Liveness probe - is the app running?
app.get("/health", (req, res) => {
  // Basic check - if this endpoint responds, app is alive
  res.status(200).json({ status: "ok", timestamp: Date.now() });
});

// Readiness probe - is the app ready to serve traffic?
app.get("/ready", async (req, res) => {
  try {
    // Check database connection
    await database.ping();

    // Check required services
    await cache.ping();
    await messageQueue.ping();

    // Check if migrations are complete
    const migrationsComplete = await checkMigrations();

    if (!migrationsComplete) {
      return res.status(503).json({
        status: "not_ready",
        reason: "migrations_pending",
      });
    }

    // All checks passed
    res.status(200).json({
      status: "ready",
      checks: {
        database: "ok",
        cache: "ok",
        messageQueue: "ok",
        migrations: "ok",
      },
    });
  } catch (error) {
    // Not ready
    res.status(503).json({
      status: "not_ready",
      error: error.message,
    });
  }
});

// Startup probe - is the app starting up?
// Useful for apps that take a while to initialize
app.get("/startup", (req, res) => {
  if (app.locals.startupComplete) {
    res.status(200).json({ status: "started" });
  } else {
    res.status(503).json({ status: "starting" });
  }
});

// Mark startup as complete after initialization
app.listen(8080, async () => {
  await initializeApp();
  app.locals.startupComplete = true;
  console.log("App started and ready");
});
```

---

<div align="center">

## 💙💚 Blue-Green Deployment

_Instant rollback with full environment switching_ 🎛️

</div>

### How It Works

```
Setup:
┌─────────────────────┬─────────────────────┐
│   Blue (Current)    │   Green (New)       │
│                     │                     │
│   v1.0 ████████     │   v2.0 ████████     │
│   (Production)      │   (Staging/Ready)   │
└─────────────────────┴─────────────────────┘
           ▲
           │
    Traffic Routes Here

Switch:
┌─────────────────────┬─────────────────────┐
│   Blue (Old)        │   Green (Current)   │
│                     │                     │
│   v1.0 ████████     │   v2.0 ████████     │
│   (Idle)            │   (Production)      │
└─────────────────────┴─────────────────────┘
                              ▲
                              │
                       Traffic Routes Here

Process:
1. Deploy v2.0 to Green environment
2. Test Green thoroughly
3. Switch traffic from Blue to Green (instant!)
4. Monitor for issues
5. If issues: switch back to Blue (instant!)
6. If good: Blue becomes next staging environment
```

---

### Kubernetes Implementation

```yaml
# ═══════════════════════════════════════════════════════════
# BLUE-GREEN DEPLOYMENT - KUBERNETES
# Complete setup with service switching
# ═══════════════════════════════════════════════════════════

# Blue Deployment (Current Production)
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app-blue
  namespace: production
  labels:
    app: my-app
    environment: blue
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
      version: blue
  template:
    metadata:
      labels:
        app: my-app
        version: blue
    spec:
      containers:
        - name: app
          image: myregistry/my-app:v1.0.0
          ports:
            - containerPort: 8080
          resources:
            requests:
              memory: "256Mi"
              cpu: "250m"
            limits:
              memory: "512Mi"
              cpu: "500m"
          livenessProbe:
            httpGet:
              path: /health
              port: 8080
            initialDelaySeconds: 30
            periodSeconds: 10
          readinessProbe:
            httpGet:
              path: /ready
              port: 8080
            initialDelaySeconds: 10
            periodSeconds: 5
          env:
            - name: ENVIRONMENT
              value: "blue"

# Green Deployment (New Version)
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app-green
  namespace: production
  labels:
    app: my-app
    environment: green
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
      version: green
  template:
    metadata:
      labels:
        app: my-app
        version: green
    spec:
      containers:
        - name: app
          image: myregistry/my-app:v2.0.0
          ports:
            - containerPort: 8080
          resources:
            requests:
              memory: "256Mi"
              cpu: "250m"
            limits:
              memory: "512Mi"
              cpu: "500m"
          livenessProbe:
            httpGet:
              path: /health
              port: 8080
            initialDelaySeconds: 30
            periodSeconds: 10
          readinessProbe:
            httpGet:
              path: /ready
              port: 8080
            initialDelaySeconds: 10
            periodSeconds: 5
          env:
            - name: ENVIRONMENT
              value: "green"

# Production Service (Routes to Blue or Green)
---
apiVersion: v1
kind: Service
metadata:
  name: my-app-service
  namespace: production
  labels:
    app: my-app
spec:
  type: LoadBalancer
  selector:
    app: my-app
    version: blue # Change to 'green' to switch traffic
  ports:
    - name: http
      port: 80
      targetPort: 8080
      protocol: TCP
  sessionAffinity: ClientIP # Optional: sticky sessions
  sessionAffinityConfig:
    clientIP:
      timeoutSeconds: 10800 # 3 hours

# Internal Testing Services (Always available)
---
apiVersion: v1
kind: Service
metadata:
  name: my-app-blue
  namespace: production
spec:
  selector:
    app: my-app
    version: blue
  ports:
    - port: 80
      targetPort: 8080

---
apiVersion: v1
kind: Service
metadata:
  name: my-app-green
  namespace: production
spec:
  selector:
    app: my-app
    version: green
  ports:
    - port: 80
      targetPort: 8080
```

---

### Blue-Green Deployment Script

```bash
#!/bin/bash
# ═══════════════════════════════════════════════════════════
# BLUE-GREEN DEPLOYMENT SCRIPT
# Production-grade with extensive checks
# ═══════════════════════════════════════════════════════════

set -euo pipefail

# Configuration
APP_NAME="my-app"
NAMESPACE="production"
NEW_VERSION="v2.0.0"
SERVICE_NAME="my-app-service"
MONITORING_PERIOD=300  # 5 minutes
ERROR_THRESHOLD=0.05

# Colors
GREEN='\033[0;32m'
YELLOW='\033[1;33m'
RED='\033[0;31m'
NC='\033[0m'

log_info() { echo -e "${GREEN}[INFO]${NC} $1"; }
log_warn() { echo -e "${YELLOW}[WARN]${NC} $1"; }
log_error() { echo -e "${RED}[ERROR]${NC} $1"; }

# Get current active environment
get_active_environment() {
    kubectl get service $SERVICE_NAME -n $NAMESPACE \
      -o jsonpath='{.spec.selector.version}'
}

# Deploy to inactive environment
deploy_to_inactive() {
    local active_env=$(get_active_environment)
    local target_env="green"

    if [ "$active_env" = "green" ]; then
        target_env="blue"
    fi

    log_info "Active environment: $active_env"
    log_info "Deploying $NEW_VERSION to $target_env environment..."

    # Update deployment
    kubectl set image deployment/$APP_NAME-$target_env \
      app=myregistry/$APP_NAME:$NEW_VERSION \
      -n $NAMESPACE

    # Wait for rollout
    kubectl rollout status deployment/$APP_NAME-$target_env \
      -n $NAMESPACE --timeout=600s

    log_info "✅ Deployment to $target_env complete"
    echo "$target_env"
}

# Run comprehensive tests
run_tests() {
    local env=$1
    local endpoint="http://my-app-$env.$NAMESPACE.svc.cluster.local"

    log_info "Running tests against $env environment..."

    # Health check
    log_info "1. Health check..."
    if ! curl -f "$endpoint/health" > /dev/null 2>&1; then
        log_error "Health check failed!"
        return 1
    fi

    # Smoke tests
    log_info "2. Smoke tests..."
    if ! ./scripts/smoke-tests.sh "$endpoint"; then
        log_error "Smoke tests failed!"
        return 1
    fi

    # Integration tests
    log_info "3. Integration tests..."
    if ! ./scripts/integration-tests.sh "$endpoint"; then
        log_error "Integration tests failed!"
        return 1
    fi

    # Performance tests
    log_info "4. Performance tests..."
    if ! ./scripts/performance-tests.sh "$endpoint"; then
        log_error "Performance tests failed!"
        return 1
    fi

    log_info "✅ All tests passed!"
    return 0
}

# Switch traffic
switch_traffic() {
    local target_env=$1
    local active_env=$(get_active_environment)

    log_warn "🔄 Switching traffic from $active_env to $target_env..."

    # Update service selector
    kubectl patch service $SERVICE_NAME -n $NAMESPACE -p \
      "{\"spec\":{\"selector\":{\"version\":\"$target_env\"}}}"

    log_info "✅ Traffic switched to $target_env"
    log_info "Waiting for load balancer to propagate (30s)..."
    sleep 30
}

# Monitor deployment
monitor_deployment() {
    local env=$1
    local start_time=$(date +%s)
    local end_time=$((start_time + MONITORING_PERIOD))

    log_info "📊 Monitoring $env environment for $MONITORING_PERIOD seconds..."

    while [ $(date +%s) -lt $end_time ]; do
        # Check error rate
        local error_rate=$(kubectl logs -l version=$env -n $NAMESPACE --tail=100 | \
          grep -c "ERROR" || echo "0")

        # Check pod status
        local ready_pods=$(kubectl get deployment $APP_NAME-$env -n $NAMESPACE \
          -o jsonpath='{.status.readyReplicas}')
        local desired_pods=$(kubectl get deployment $APP_NAME-$env -n $NAMESPACE \
          -o jsonpath='{.spec.replicas}')

        if [ "$ready_pods" != "$desired_pods" ]; then
            log_error "Pod count mismatch: $ready_pods/$desired_pods"
            return 1
        fi

        log_info "Status: $ready_pods/$desired_pods pods ready, error_rate: $error_rate"

        sleep 30
    done

    log_info "✅ Monitoring complete - no issues detected"
    return 0
}

# Rollback function
rollback() {
    local target_env=$1

    log_error "🚨 ROLLING BACK TO $target_env! 🚨"

    switch_traffic "$target_env"

    log_info "✅ Rollback complete"
}

# Cleanup old environment
cleanup_old_environment() {
    local old_env=$1

    log_info "🧹 Cleaning up $old_env environment..."

    # Scale down to save resources (optional)
    kubectl scale deployment/$APP_NAME-$old_env --replicas=1 -n $NAMESPACE

    log_info "✅ Cleanup complete"
}

# Main function
main() {
    log_info "🚀 Starting Blue-Green deployment of $APP_NAME:$NEW_VERSION"

    # Get current state
    local active_env=$(get_active_environment)
    log_info "Current active environment: $active_env"

    # Step 1: Deploy to inactive environment
    local target_env=$(deploy_to_inactive)

    # Step 2: Run tests
    if ! run_tests "$target_env"; then
        log_error "Tests failed on $target_env - aborting deployment"
        exit 1
    fi

    # Step 3: Manual approval (optional)
    log_warn "⚠️  About to switch traffic from $active_env to $target_env"
    read -p "Continue? (yes/no): " confirm
    if [ "$confirm" != "yes" ]; then
        log_warn "Deployment cancelled by user"
        exit 0
    fi

    # Step 4: Switch traffic
    switch_traffic "$target_env"

    # Step 5: Monitor
    if ! monitor_deployment "$target_env"; then
        rollback "$active_env"
        exit 1
    fi

    # Step 6: Success!
    log_info "✅ Deployment successful!"

    # Step 7: Cleanup
    cleanup_old_environment "$active_env"

    # Step 8: Notify
    curl -X POST https://hooks.slack.com/services/YOUR/WEBHOOK \
      -H 'Content-Type: application/json' \
      -d "{\"text\":\"✅ $APP_NAME:$NEW_VERSION deployed via Blue-Green strategy!\"}"
}

# Trap signals
trap 'log_warn "Deployment interrupted!"' INT TERM

# Run
main "$@"
```

---

### Pros & Cons

```
✅ PROS:
• Instant rollback (just switch service back)
• Full environment testing before switch
• Zero downtime
• Clean separation of versions
• Can compare versions side-by-side
• Reduced risk

❌ CONS:
• 2x infrastructure cost (during deployment)
• Database migrations complexity
• Stateful applications challenging
• Need to handle data sync between environments
• Resource intensive

🎯 USE WHEN:
✓ Critical production applications
✓ Can afford 2x resources temporarily
✓ Need instant rollback capability
✓ Want to test full environment first
✓ High-risk deployments

💰 COST CONSIDERATION:
• Need 2x compute resources during deployment
• But only temporarily (minutes to hours)
• After switch, can scale down old environment

🎯 PERFECT FOR:
• Financial systems
• Healthcare applications
• E-commerce (during peak)
• Mission-critical apps
• Compliance requirements
```

---

<div align="center">

## 🐤 Canary Deployment

_Test with real users gradually_ 📊

</div>

### How It Works

```
Traffic Distribution Over Time:

Stage 1 (10% canary):
v1.0: ████████████████████ (90%)
v2.0: ██ (10%)
      Monitor metrics...

Stage 2 (25% canary):
v1.0: ███████████████ (75%)
v2.0: █████ (25%)
      Monitor metrics...

Stage 3 (50% canary):
v1.0: ██████████ (50%)
v2.0: ██████████ (50%)
      Monitor metrics...

Stage 4 (75% canary):
v1.0: █████ (25%)
v2.0: ███████████████ (75%)
      Monitor metrics...

Stage 5 (100% canary):
v1.0: (0%)
v2.0: ████████████████████ (100%)
      Success!

Each stage: Monitor for errors, latency, business metrics
If issues detected at any stage → Rollback immediately
```

---

### Kubernetes + Flagger Implementation

```yaml
# ═══════════════════════════════════════════════════════════
# CANARY DEPLOYMENT - FLAGGER
# Automated canary with metrics-based promotion
# ═══════════════════════════════════════════════════════════

# Install Flagger first:
# kubectl apply -k github.com/fluxcd/flagger//kustomize/linkerd

apiVersion: flagger.app/v1beta1
kind: Canary
metadata:
  name: my-app
  namespace: production
spec:
  # Target deployment
  targetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: my-app

  # HPA reference (optional)
  autoscalerRef:
    apiVersion: autoscaling/v2
    kind: HorizontalPodAutoscaler
    name: my-app

  # Service configuration
  service:
    port: 80
    targetPort: 8080
    gateways:
      - istio-system/public-gateway
    hosts:
      - app.example.com
    trafficPolicy:
      tls:
        mode: DISABLE

  # Canary analysis
  analysis:
    # Schedule interval (how often to check metrics)
    interval: 1m

    # Max number of failed checks before rollback
    threshold: 5

    # Max traffic percentage routed to canary
    maxWeight: 50

    # Traffic increment per iteration
    stepWeight: 10

    # Metrics to check
    metrics:
      # Request success rate (from Prometheus)
      - name: request-success-rate
        thresholdRange:
          min: 99
        interval: 1m

      # Request duration (from Prometheus)
      - name: request-duration
        thresholdRange:
          max: 500
        interval: 1m

      # Custom metric query
      - name: error-rate
        templateRef:
          name: error-rate
          namespace: flagger
        thresholdRange:
          max: 1
        interval: 1m

    # Webhooks for testing
    webhooks:
      # Pre-rollout webhook (smoke tests)
      - name: smoke-test
        type: pre-rollout
        url: http://flagger-loadtester.test/
        timeout: 5m
        metadata:
          type: bash
          cmd: "curl -sd 'test' http://my-app-canary/token | grep token"

      # Load test during canary
      - name: load-test
        url: http://flagger-loadtester.test/
        timeout: 5s
        metadata:
          cmd: "hey -z 1m -q 10 -c 2 http://my-app-canary/"

      # Post-rollout notification
      - name: send-notification
        type: post-rollout
        url: http://notification-service/
        metadata:
          message: "Canary deployment completed"

---
# Prometheus metric template (custom metrics)
apiVersion: flagger.app/v1beta1
kind: MetricTemplate
metadata:
  name: error-rate
  namespace: flagger
spec:
  provider:
    type: prometheus
    address: http://prometheus.monitoring:9090
  query: |
    100 - sum(
      rate(
        http_requests_total{
          kubernetes_namespace="{{ namespace }}",
          kubernetes_pod_name=~"{{ target }}-[0-9a-zA-Z]+(-[0-9a-zA-Z]+)",
          status!~"5.."
        }[{{ interval }}]
      )
    )
    /
    sum(
      rate(
        http_requests_total{
          kubernetes_namespace="{{ namespace }}",
          kubernetes_pod_name=~"{{ target }}-[0-9a-zA-Z]+(-[0-9a-zA-Z]+)"
        }[{{ interval }}]
      )
    )
    * 100
```

---

### Manual Canary with Nginx

```nginx
# ═══════════════════════════════════════════════════════════
# CANARY DEPLOYMENT - NGINX
# Manual traffic splitting
# ═══════════════════════════════════════════════════════════

upstream backend {
    # Initial: 90% to v1, 10% to v2
    server app-v1:8080 weight=90 max_fails=3 fail_timeout=30s;
    server app-v2:8080 weight=10 max_fails=3 fail_timeout=30s;

    # Stage 2: 75% to v1, 25% to v2
    # server app-v1:8080 weight=75;
    # server app-v2:8080 weight=25;

    # Stage 3: 50/50
    # server app-v1:8080 weight=50;
    # server app-v2:8080 weight=50;

    # Final: 100% to v2
    # server app-v2:8080 weight=100;

    # Connection settings
    keepalive 32;
}

server {
    listen 80;
    server_name app.example.com;

    location / {
        proxy_pass http://backend;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_cache_bypass $http_upgrade;

        # Add version header for debugging
        add_header X-Backend-Version $upstream_addr;
    }
}
```

---

### Canary Deployment Script

```bash
#!/bin/bash
# ═══════════════════════════════════════════════════════════
# MANUAL CANARY DEPLOYMENT SCRIPT
# Gradual traffic increase with monitoring
# ═══════════════════════════════════════════════════════════

set -euo pipefail

# Configuration
APP_NAME="my-app"
NEW_VERSION="v2.0.0"
CANARY_STAGES=(10 25 50 75 100)
MONITORING_DURATION=300  # 5 minutes per stage
ERROR_THRESHOLD=0.05
LATENCY_THRESHOLD_MS=500

log_info() { echo "[INFO] $1"; }
log_error() { echo "[ERROR] $1" >&2; }

# Deploy canary version
deploy_canary() {
    log_info "Deploying canary version $NEW_VERSION..."

    kubectl apply -f - <<EOF
apiVersion: apps/v1
kind: Deployment
metadata:
  name: ${APP_NAME}-canary
spec:
  replicas: 1
  selector:
    matchLabels:
      app: $APP_NAME
      version: canary
  template:
    metadata:
      labels:
        app: $APP_NAME
        version: canary
    spec:
      containers:
      - name: app
        image: myregistry/$APP_NAME:$NEW_VERSION
        ports:
        - containerPort: 8080
EOF

    kubectl wait --for=condition=available deployment/${APP_NAME}-canary --timeout=300s
    log_info "✅ Canary deployed"
}

# Update traffic split
update_traffic_split() {
    local canary_percent=$1
    local stable_percent=$((100 - canary_percent))

    log_info "Setting traffic: ${stable_percent}% stable, ${canary_percent}% canary"

    # This depends on your service mesh (Istio, Linkerd, etc.)
    # Example with Istio VirtualService:
    kubectl apply -f - <<EOF
apiVersion: networking.istio.io/v1beta1
kind: VirtualService
metadata:
  name: $APP_NAME
spec:
  hosts:
  - $APP_NAME
  http:
  - route:
    - destination:
        host: $APP_NAME
        subset: stable
      weight: $stable_percent
    - destination:
        host: $APP_NAME
        subset: canary
      weight: $canary_percent
EOF
}

# Monitor metrics
monitor_canary() {
    local duration=$1
    local end_time=$(($(date +%s) + duration))

    log_info "Monitoring for ${duration}s..."

    while [ $(date +%s) -lt $end_time ]; do
        # Query Prometheus for error rate
        local error_rate=$(curl -s 'http://prometheus:9090/api/v1/query' \
          --data-urlencode 'query=rate(http_requests_total{version="canary",status=~"5.."}[5m])' | \
          jq -r '.data.result[0].value[1]')

        # Query Prometheus for latency
        local latency=$(curl -s 'http://prometheus:9090/api/v1/query' \
          --data-urlencode 'query=histogram_quantile(0.99, rate(http_request_duration_seconds_bucket{version="canary"}[5m]))' | \
          jq -r '.data.result[0].value[1]')

        local latency_ms=$(echo "$latency * 1000" | bc)

        log_info "Canary metrics: error_rate=$error_rate, p99_latency=${latency_ms}ms"

        # Check thresholds
        if (( $(echo "$error_rate > $ERROR_THRESHOLD" | bc -l) )); then
            log_error "Error rate too high: $error_rate"
            return 1
        fi

        if (( $(echo "$latency_ms > $LATENCY_THRESHOLD_MS" | bc -l) )); then
            log_error "Latency too high: ${latency_ms}ms"
            return 1
        fi

        sleep 30
    done

    log_info "✅ Monitoring passed"
    return 0
}

# Rollback
rollback() {
    log_error "🚨 ROLLING BACK CANARY! 🚨"

    # Set traffic to 100% stable
    update_traffic_split 0

    # Delete canary deployment
    kubectl delete deployment ${APP_NAME}-canary

    log_info "✅ Rollback complete"
}

# Promote canary
promote_canary() {
    log_info "🎉 Promoting canary to stable..."

    # Update stable deployment to new version
    kubectl set image deployment/$APP_NAME app=myregistry/$APP_NAME:$NEW_VERSION

    # Wait for rollout
    kubectl rollout status deployment/$APP_NAME

    # Delete canary deployment
    kubectl delete deployment ${APP_NAME}-canary

    # Reset traffic to 100% stable
    kubectl delete virtualservice $APP_NAME

    log_info "✅ Promotion complete!"
}

# Main
main() {
    log_info "🚀 Starting canary deployment: $APP_NAME:$NEW_VERSION"

    # Deploy canary
    deploy_canary

    # Gradual rollout
    for stage in "${CANARY_STAGES[@]}"; do
        log_info "📊 Stage: ${stage}% canary traffic"

        # Update traffic
        update_traffic_split "$stage"

        # Monitor
        if ! monitor_canary "$MONITORING_DURATION"; then
            rollback
            exit 1
        fi

        # Pause between stages (optional)
        if [ "$stage" -lt 100 ]; then
            log_info "Pausing 60s before next stage..."
            sleep 60
        fi
    done

    # Promote
    promote_canary

    log_info "✅ Canary deployment successful!"
}

main "$@"
```

---

### Pros & Cons

```
✅ PROS:
• Very low risk (gradual rollout)
• Real production testing
• Can detect issues early with small %
• Automatic rollback possible
• Great for large-scale apps
• Users barely notice issues

❌ CONS:
• Complex setup (need service mesh)
• Requires metrics/monitoring
• Slow rollout (hours)
• Need traffic shaping
• Stateful apps are tricky

🎯 USE WHEN:
✓ Large user base
✓ Can't afford any downtime
✓ Have good monitoring
✓ High-risk changes
✓ Want gradual validation

📊 REQUIREMENTS:
• Service mesh (Istio, Linkerd) or load balancer
• Metrics system (Prometheus)
• Monitoring/alerting
• Automated testing

🎯 PERFECT FOR:
• Netflix-scale applications
• Financial services
• Healthcare systems
• Large SaaS platforms
```

---

<div align="center">

## 🧪 A/B Testing

_Test features with specific user segments_ 🎲

</div>

### How It Works

```
User Traffic Split:

Control Group (50%):
├── See Version A (current)
├── Track conversion metrics
└── Baseline performance

Treatment Group (50%):
├── See Version B (new feature)
├── Track conversion metrics
└── Compare to baseline

Analysis:
├── Conversion rates
├── User engagement
├── Revenue impact
├── User satisfaction
└── Statistical significance

Decision:
└── Keep version with better metrics
```

---

### Application-Level A/B Testing

```javascript
// ═══════════════════════════════════════════════════════════
// A/B TESTING - APPLICATION LEVEL
// Feature flag based implementation
// ═══════════════════════════════════════════════════════════

const express = require("express");
const app = express();

// A/B testing configuration
const experiments = {
  "new-checkout-flow": {
    enabled: true,
    variants: {
      control: { weight: 50 }, // 50% see old version
      treatment: { weight: 50 }, // 50% see new version
    },
    // Specific users/segments
    overrides: {
      "vip-users": "treatment", // VIPs always see new
      "internal-team": "treatment", // Team always sees new
    },
  },
};

// Analytics tracking
const analytics = {
  track: (userId, event, properties) => {
    console.log(`[Analytics] User ${userId}: ${event}`, properties);
    // Send to analytics service (Mixpanel, Amplitude, etc.)
  },
};

// Hash function for consistent assignment
function hashUserId(userId) {
  let hash = 0;
  for (let i = 0; i < userId.length; i++) {
    const char = userId.charCodeAt(i);
    hash = (hash << 5) - hash + char;
    hash = hash & hash; // Convert to 32bit integer
  }
  return Math.abs(hash);
}

// Assign user to variant
function getVariant(userId, experimentKey) {
  const experiment = experiments[experimentKey];

  if (!experiment || !experiment.enabled) {
    return "control";
  }

  // Check for user segment override
  const userSegment = getUserSegment(userId);
  if (experiment.overrides[userSegment]) {
    return experiment.overrides[userSegment];
  }

  // Consistent hash-based assignment
  const hash = hashUserId(userId);
  const bucket = hash % 100;

  let cumulative = 0;
  for (const [variant, config] of Object.entries(experiment.variants)) {
    cumulative += config.weight;
    if (bucket < cumulative) {
      return variant;
    }
  }

  return "control";
}

// Middleware to assign experiments
app.use((req, res, next) => {
  const userId = req.session?.userId || req.cookies?.userId;

  if (!userId) {
    return next();
  }

  // Assign all active experiments
  req.experiments = {};
  for (const experimentKey in experiments) {
    const variant = getVariant(userId, experimentKey);
    req.experiments[experimentKey] = variant;

    // Track assignment
    analytics.track(userId, "Experiment Assigned", {
      experiment: experimentKey,
      variant: variant,
    });
  }

  next();
});

// Routes with A/B testing
app.get("/checkout", (req, res) => {
  const variant = req.experiments["new-checkout-flow"];

  // Track page view
  analytics.track(req.session.userId, "Checkout Page Viewed", {
    variant: variant,
  });

  if (variant === "treatment") {
    // New checkout flow
    res.render("checkout-v2", {
      variant: "treatment",
      features: {
        oneClickCheckout: true,
        expressShipping: true,
        guestCheckout: true,
      },
    });
  } else {
    // Original checkout flow
    res.render("checkout-v1", {
      variant: "control",
    });
  }
});

// Track conversion
app.post("/checkout/complete", (req, res) => {
  const variant = req.experiments["new-checkout-flow"];
  const orderValue = req.body.total;

  // Track conversion event
  analytics.track(req.session.userId, "Purchase Completed", {
    variant: variant,
    orderValue: orderValue,
    experiment: "new-checkout-flow",
  });

  res.json({ success: true });
});

// Helper: Get user segment
function getUserSegment(userId) {
  // In real app, query from database
  // For example: check if user is VIP, internal, etc.
  return "standard";
}
```

---

### Infrastructure-Level A/B Testing (Istio)

```yaml
# ═══════════════════════════════════════════════════════════
# A/B TESTING - INFRASTRUCTURE LEVEL
# Using Istio for traffic routing based on headers
# ═══════════════════════════════════════════════════════════

# Destination Rule (Define versions)
apiVersion: networking.istio.io/v1beta1
kind: DestinationRule
metadata:
  name: my-app
spec:
  host: my-app
  subsets:
    - name: version-a
      labels:
        version: v1.0.0
    - name: version-b
      labels:
        version: v2.0.0

---
# Virtual Service (Route based on user segment)
apiVersion: networking.istio.io/v1beta1
kind: VirtualService
metadata:
  name: my-app
spec:
  hosts:
    - my-app
  http:
    # VIP users always get version B
    - match:
        - headers:
            user-segment:
              exact: vip
      route:
        - destination:
            host: my-app
            subset: version-b
          weight: 100

    # Internal team always gets version B
    - match:
        - headers:
            user-segment:
              exact: internal
      route:
        - destination:
            host: my-app
            subset: version-b
          weight: 100

    # Regular users: 50/50 split
    - route:
        - destination:
            host: my-app
            subset: version-a
          weight: 50
          headers:
            response:
              set:
                x-variant: "control"
        - destination:
            host: my-app
            subset: version-b
          weight: 50
          headers:
            response:
              set:
                x-variant: "treatment"
```

---

### Using LaunchDarkly (Feature Flag Service)

```javascript
// ═══════════════════════════════════════════════════════════
// LAUNCHDARKLY - FEATURE FLAG SERVICE
// Enterprise-grade A/B testing
// ═══════════════════════════════════════════════════════════

const LaunchDarkly = require("launchdarkly-node-server-sdk");

// Initialize LaunchDarkly client
const ldClient = LaunchDarkly.init("YOUR_SDK_KEY");

// Wait for client to be ready
ldClient.once("ready", () => {
  console.log("LaunchDarkly client initialized");
});

// Middleware to add feature flags
app.use(async (req, res, next) => {
  const user = {
    key: req.session.userId,
    email: req.session.email,
    custom: {
      userSegment: req.session.userSegment,
      accountAge: req.session.accountAge,
      totalPurchases: req.session.totalPurchases,
    },
  };

  // Get all feature flags for user
  req.featureFlags = await ldClient.allFlagsState(user);

  next();
});

// Use feature flag in route
app.get("/checkout", async (req, res) => {
  const user = {
    key: req.session.userId,
    email: req.session.email,
    custom: {
      userSegment: req.session.userSegment,
    },
  };

  // Check feature flag
  const useNewCheckout = await ldClient.variation(
    "new-checkout-flow",
    user,
    false // Default value
  );

  if (useNewCheckout) {
    res.render("checkout-v2");
  } else {
    res.render("checkout-v1");
  }

  // Track that user saw this variation
  ldClient.track("checkout-page-viewed", user, {
    variant: useNewCheckout ? "new" : "old",
  });
});

// Graceful shutdown
process.on("SIGTERM", () => {
  ldClient.close();
});
```

---

### Pros & Cons

```
✅ PROS:
• Test specific features
• Measure business impact
• Target specific user segments
• Data-driven decisions
• Can run multiple experiments
• Marketing & product testing

❌ CONS:
• Complex implementation
• Need analytics integration
• Statistical significance takes time
• Can confuse users if inconsistent
• Maintenance overhead

🎯 USE WHEN:
✓ Testing new features
✓ Optimizing conversion
✓ Product experimentation
✓ Marketing campaigns
✓ Need data-driven decisions

📊 REQUIREMENTS:
• Analytics platform
• Feature flag system
• Statistical analysis
• Large user base
• Business metrics tracking

🎯 PERFECT FOR:
• E-commerce optimization
• SaaS feature testing
• Marketing experiments
• UI/UX improvements
• Pricing strategies
```

---

<div align="center">

## 🎭 Shadow Deployment

_Test with real traffic without user impact_ 👥

</div>

### How It Works

```
Traffic Flow:

User Request
     │
     ├──────────────────┬─────────────────►
     │                  │
     ▼                  ▼
Production Env     Shadow Env
(v1.0 - Live)     (v2.0 - Testing)
     │                  │
     │                  │ (Response discarded)
     ▼                  ▼
User Response      Metrics Only
     ◄──────────────────┘
(Only from production)

Purpose:
• Test v2.0 with real production traffic
• Compare metrics: latency, errors, resources
• No user impact (shadow responses discarded)
• Validate before actual deployment
```

---

### Istio Shadow Deployment

```yaml
# ═══════════════════════════════════════════════════════════
# SHADOW DEPLOYMENT - ISTIO
# Mirror traffic to shadow environment
# ═══════════════════════════════════════════════════════════

apiVersion: networking.istio.io/v1beta1
kind: VirtualService
metadata:
  name: my-app
spec:
  hosts:
    - my-app
  http:
    - route:
        # Primary route (production)
        - destination:
            host: my-app
            subset: production
          weight: 100
      # Mirror to shadow environment
      mirror:
        host: my-app
        subset: shadow
      mirrorPercentage:
        value: 100 # Mirror 100% of traffic

---
apiVersion: networking.istio.io/v1beta1
kind: DestinationRule
metadata:
  name: my-app
spec:
  host: my-app
  subsets:
    - name: production
      labels:
        version: v1.0.0
    - name: shadow
      labels:
        version: v2.0.0
```

---

### Nginx Shadow Deployment

```nginx
# ═══════════════════════════════════════════════════════════
# SHADOW DEPLOYMENT - NGINX
# Mirror traffic using mirror directive
# ═══════════════════════════════════════════════════════════

upstream production {
    server app-v1:8080;
}

upstream shadow {
    server app-v2:8080;
}

server {
    listen 80;
    server_name app.example.com;

    location / {
        # Primary request to production
        proxy_pass http://production;

        # Mirror request to shadow
        mirror /mirror;
        mirror_request_body on;

        # Standard proxy headers
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }

    # Internal location for mirror
    location = /mirror {
        internal;
        proxy_pass http://shadow$request_uri;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;

        # Don't wait for shadow response
        proxy_ignore_client_abort on;
    }
}
```

---

### Application-Level Shadow Testing

```javascript
// ═══════════════════════════════════════════════════════════
// APPLICATION-LEVEL SHADOW TESTING
// Mirror requests to shadow version
// ═══════════════════════════════════════════════════════════

const express = require("express");
const axios = require("axios");
const app = express();

// Configuration
const PRODUCTION_SERVICE = "http://app-v1:8080";
const SHADOW_SERVICE = "http://app-v2:8080";
const SHADOW_PERCENTAGE = 100; // % of traffic to shadow

// Middleware to mirror requests
app.use(async (req, res, next) => {
  // Forward to production (primary)
  try {
    const productionResponse = await axios({
      method: req.method,
      url: `${PRODUCTION_SERVICE}${req.path}`,
      data: req.body,
      headers: req.headers,
      timeout: 5000,
    });

    // Send production response to user
    res.status(productionResponse.status).json(productionResponse.data);

    // Mirror to shadow (async, don't wait)
    if (Math.random() * 100 < SHADOW_PERCENTAGE) {
      mirrorToShadow(req).catch((err) => {
        console.error("Shadow request failed:", err.message);
      });
    }
  } catch (error) {
    res.status(500).json({ error: "Service unavailable" });
  }
});

// Mirror request to shadow environment
async function mirrorToShadow(req) {
  const startTime = Date.now();

  try {
    const shadowResponse = await axios({
      method: req.method,
      url: `${SHADOW_SERVICE}${req.path}`,
      data: req.body,
      headers: {
        ...req.headers,
        "X-Shadow-Request": "true",
      },
      timeout: 5000,
    });

    const duration = Date.now() - startTime;

    // Log metrics for comparison
    logShadowMetrics({
      path: req.path,
      method: req.method,
      status: shadowResponse.status,
      duration: duration,
      success: true,
    });
  } catch (error) {
    const duration = Date.now() - startTime;

    logShadowMetrics({
      path: req.path,
      method: req.method,
      status: error.response?.status || 500,
      duration: duration,
      success: false,
      error: error.message,
    });
  }
}

// Log shadow metrics to monitoring system
function logShadowMetrics(metrics) {
  // Send to Prometheus, DataDog, CloudWatch, etc.
  console.log("[Shadow Metrics]", JSON.stringify(metrics));
}

app.listen(8080);
```

---

### Monitoring Shadow Deployment

```yaml
# ═══════════════════════════════════════════════════════════
# PROMETHEUS METRICS FOR SHADOW DEPLOYMENT
# Compare production vs shadow performance
# ═══════════════════════════════════════════════════════════

# Grafana Dashboard Query Examples:

# 1. Latency Comparison
# Production latency
histogram_quantile(0.99,
  rate(http_request_duration_seconds_bucket{
    version="production"
  }[5m])
)

# Shadow latency
histogram_quantile(0.99,
  rate(http_request_duration_seconds_bucket{
    version="shadow"
  }[5m])
)

# 2. Error Rate Comparison
# Production errors
sum(rate(http_requests_total{
  version="production",
  status=~"5.."
}[5m]))

# Shadow errors
sum(rate(http_requests_total{
  version="shadow",
  status=~"5.."
}[5m]))

# 3. Resource Usage Comparison
# Production CPU
rate(container_cpu_usage_seconds_total{
  pod=~"app-production.*"
}[5m])

# Shadow CPU
rate(container_cpu_usage_seconds_total{
  pod=~"app-shadow.*"
}[5m])

# 4. Alert if shadow performance degrades
- alert: ShadowPerformanceDegraded
  expr: |
    (
      histogram_quantile(0.99, rate(http_request_duration_seconds_bucket{version="shadow"}[5m]))
      /
      histogram_quantile(0.99, rate(http_request_duration_seconds_bucket{version="production"}[5m]))
    ) > 1.2
  for: 10m
  annotations:
    summary: "Shadow environment 20% slower than production"
```

---

### Pros & Cons

```
✅ PROS:
• Zero user impact (responses discarded)
• Test with real production traffic
• Compare performance directly
• Validate before rollout
• Find edge cases
• Load testing with real patterns

❌ CONS:
• 2x infrastructure load
• Doubles resource usage
• Can't test user-facing changes
• Database writes can be tricky
• Complex to set up

🎯 USE WHEN:
✓ Testing performance improvements
✓ Validating refactors
✓ Testing new algorithms
✓ Load testing
✓ Backend changes only

⚠️ CHALLENGES:
• Side effects (don't write to production DB!)
• Idempotency issues
• External API calls (2x cost)
• Real-time systems

💡 BEST PRACTICES:
✓ Only mirror read operations
✓ Use separate database for shadow
✓ Monitor resource usage closely
✓ Start with small percentage
✓ Set timeout limits
```

---

<div align="center">

## 🔀 Feature Flags

_Decouple deployment from release_ 🎚️

</div>

### Feature Flag Patterns

```javascript
// ═══════════════════════════════════════════════════════════
// FEATURE FLAGS - IMPLEMENTATION PATTERNS
// ═══════════════════════════════════════════════════════════

// 1. SIMPLE BOOLEAN FLAG
const features = {
  newCheckout: process.env.FEATURE_NEW_CHECKOUT === "true",
};

if (features.newCheckout) {
  // New feature
} else {
  // Old feature
}

// 2. PERCENTAGE ROLLOUT
function isFeatureEnabled(userId, featureName, percentage) {
  const hash = hashUserId(userId);
  return hash % 100 < percentage;
}

// 10% of users see new feature
if (isFeatureEnabled(userId, "newDashboard", 10)) {
  return renderNewDashboard();
}

// 3. USER SEGMENT TARGETING
const featureConfig = {
  newDashboard: {
    enabled: true,
    rules: [
      { segment: "beta-testers", enabled: true },
      { segment: "enterprise", enabled: true },
      { segment: "free-tier", enabled: false },
    ],
  },
};

function canAccessFeature(user, featureName) {
  const config = featureConfig[featureName];
  const userSegment = getUserSegment(user);

  const rule = config.rules.find((r) => r.segment === userSegment);
  return rule ? rule.enabled : false;
}

// 4. TIME-BASED ACTIVATION
const features = {
  blackFridaySale: {
    enabled: true,
    startDate: "2024-11-29T00:00:00Z",
    endDate: "2024-11-30T23:59:59Z",
  },
};

function isFeatureActive(featureName) {
  const feature = features[featureName];
  const now = new Date();
  const start = new Date(feature.startDate);
  const end = new Date(feature.endDate);

  return feature.enabled && now >= start && now <= end;
}

// 5. DEPENDENCY CHECKING
const features = {
  advancedAnalytics: {
    enabled: true,
    dependencies: ["newDashboard", "premiumPlan"],
  },
};

function canUseFeature(user, featureName) {
  const feature = features[featureName];

  // Check dependencies
  for (const dep of feature.dependencies) {
    if (!canUseFeature(user, dep)) {
      return false;
    }
  }

  return feature.enabled;
}
```

---

### Feature Flag Service (Self-Hosted)

```javascript
// ═══════════════════════════════════════════════════════════
// FEATURE FLAG SERVICE
// Simple self-hosted implementation
// ═══════════════════════════════════════════════════════════

const express = require("express");
const redis = require("redis");
const app = express();

const redisClient = redis.createClient({
  url: process.env.REDIS_URL,
});

// Feature flag configuration in Redis
// Key: feature:{name}
// Value: JSON config

// Get feature flag
app.get("/api/features/:name", async (req, res) => {
  const { name } = req.params;
  const { userId, userSegment } = req.query;

  try {
    // Get feature config from Redis
    const configStr = await redisClient.get(`feature:${name}`);

    if (!configStr) {
      return res.json({ enabled: false });
    }

    const config = JSON.parse(configStr);

    // Evaluate feature flag
    const enabled = evaluateFeatureFlag(config, {
      userId,
      userSegment,
    });

    res.json({
      name,
      enabled,
      variant: enabled ? config.variant : "control",
    });
  } catch (error) {
    res.status(500).json({ error: error.message });
  }
});

// Create/Update feature flag
app.put("/api/features/:name", async (req, res) => {
  const { name } = req.params;
  const config = req.body;

  // Validate config
  if (!config.enabled === undefined) {
    return res.status(400).json({ error: "enabled field required" });
  }

  // Save to Redis
  await redisClient.set(`feature:${name}`, JSON.stringify(config));

  // Publish update event
  await redisClient.publish(
    "feature-flag-updates",
    JSON.stringify({ name, config })
  );

  res.json({ success: true });
});

// Evaluate feature flag logic
function evaluateFeatureFlag(config, context) {
  if (!config.enabled) {
    return false;
  }

  // User segment targeting
  if (config.segments && config.segments.length > 0) {
    if (!config.segments.includes(context.userSegment)) {
      return false;
    }
  }

  // Percentage rollout
  if (config.percentage !== undefined) {
    const hash = hashUserId(context.userId);
    if (hash % 100 >= config.percentage) {
      return false;
    }
  }

  // Time window
  if (config.startDate || config.endDate) {
    const now = new Date();
    if (config.startDate && now < new Date(config.startDate)) {
      return false;
    }
    if (config.endDate && now > new Date(config.endDate)) {
      return false;
    }
  }

  return true;
}

// Client SDK
class FeatureFlagClient {
  constructor(apiUrl) {
    this.apiUrl = apiUrl;
    this.cache = new Map();
    this.cacheTimeout = 60000; // 1 minute
  }

  async isEnabled(featureName, context = {}) {
    // Check cache
    const cached = this.cache.get(featureName);
    if (cached && Date.now() - cached.timestamp < this.cacheTimeout) {
      return cached.enabled;
    }

    // Fetch from API
    const response = await fetch(
      `${this.apiUrl}/api/features/${featureName}?` +
        new URLSearchParams(context)
    );

    const data = await response.json();

    // Update cache
    this.cache.set(featureName, {
      enabled: data.enabled,
      timestamp: Date.now(),
    });

    return data.enabled;
  }

  // Real-time updates via WebSocket
  subscribeToUpdates() {
    const ws = new WebSocket(`${this.apiUrl.replace("http", "ws")}/updates`);

    ws.on("message", (data) => {
      const update = JSON.parse(data);
      // Invalidate cache for updated feature
      this.cache.delete(update.name);
    });
  }
}

// Usage in application
const featureFlags = new FeatureFlagClient("http://feature-service:3000");

app.get("/dashboard", async (req, res) => {
  const useNewDashboard = await featureFlags.isEnabled("new-dashboard", {
    userId: req.user.id,
    userSegment: req.user.segment,
  });

  if (useNewDashboard) {
    res.render("dashboard-v2");
  } else {
    res.render("dashboard-v1");
  }
});
```

---

### Feature Flag Best Practices

```

🎯 FEATURE FLAG COMMANDMENTS:

1️⃣ Keep Flags Short-Lived
• Remove after rollout completes
• Technical debt accumulates fast
• Set expiration dates

2️⃣ Name Descriptively
✅ enable-new-checkout-flow-2024
❌ flag_123 or newFeature

3️⃣ Clean Up Old Flags
• Monthly audit
• Remove code for removed flags
• Keep flag list manageable

4️⃣ Default to Safe State
• Default should be "off" or "old behavior"
• If flag system fails, use safe default

5️⃣ Monitor Flag Usage
• Track which flags are active
• Log flag evaluations
• Alert on unused flags

6️⃣ Document Purpose
• Why was this flag created?
• When can it be removed?
• Who owns it?

7️⃣ Avoid Flag Complexity
• Don't nest flags deeply
• Avoid flag dependencies
• Keep logic simple

8️⃣ Test Both States
• Test with flag ON
• Test with flag OFF
• Test flag transitions

9️⃣ Secure Flag Management
• Who can change flags?
• Audit flag changes
• Protect production flags

🔟 Use Kill Switches
• Ability to instantly disable features
• Emergency rollback without deploy

```

---

<div align="center">

## 🗄️ Database Migrations

_The deployment challenge nobody talks about_ 💀

</div>

### The Database Migration Problem

```

The Challenge:
├── New code version needs new database schema
├── Can't have downtime
├── Must support both old and new code during rollout
└── Need rollback capability

Example Scenario:
┌────────────────────────────────────────────┐
│ Old Code expects: users.name (string) │
│ New Code expects: users.first_name + │
│ users.last_name │
└────────────────────────────────────────────┘

❌ BAD: Deploy new code + migration together
→ Old pods crash when schema changes

✅ GOOD: 3-phase deployment (expand-migrate-contract)

```

---

### Expand-Migrate-Contract Pattern

```

Phase 1: EXPAND (Add new columns)
┌─────────────────────────────────────┐
│ users │
├─────────────────────────────────────┤
│ id │ integer │
│ name │ string (keep old) │
│ first_name │ string (add new) │
│ last_name │ string (add new) │
└─────────────────────────────────────┘

Deploy: Migration adds new columns
Code: Old code still uses 'name' (works)
New code uses 'first_name' + 'last_name' (works)

Phase 2: MIGRATE (Copy data)
┌─────────────────────────────────────┐
│ Background job copies data: │
│ Split 'name' → 'first_name' │
│ + 'last_name' │
└─────────────────────────────────────┘

Phase 3: CONTRACT (Remove old column)
┌─────────────────────────────────────┐
│ users │
├─────────────────────────────────────┤
│ id │ integer │
│ first_name │ string │
│ last_name │ string │
└─────────────────────────────────────┘

Deploy: Migration removes 'name' column
Code: Only new code deployed (all uses new columns)

```

---

### Migration Examples

```sql
-- ═══════════════════════════════════════════════════════════
-- DATABASE MIGRATION - EXPAND PHASE
-- Add new columns without breaking existing code
-- ═══════════════════════════════════════════════════════════

-- Migration 001: Add new columns
CREATE TABLE IF NOT EXISTS users (
    id SERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    created_at TIMESTAMP DEFAULT NOW()
);

-- Add new columns (nullable initially)
ALTER TABLE users
ADD COLUMN first_name VARCHAR(255),
ADD COLUMN last_name VARCHAR(255);

-- Create indexes for new columns
CREATE INDEX idx_users_first_name ON users(first_name);
CREATE INDEX idx_users_last_name ON users(last_name);

-- Trigger to sync old → new (during transition)
CREATE OR REPLACE FUNCTION sync_user_name()
RETURNS TRIGGER AS $$
BEGIN
    IF NEW.name IS NOT NULL AND (NEW.first_name IS NULL OR NEW.last_name IS NULL) THEN
        NEW.first_name := split_part(NEW.name, ' ', 1);
        NEW.last_name := COALESCE(split_part(NEW.name, ' ', 2), '');
    END IF;

    IF NEW.first_name IS NOT NULL AND NEW.last_name IS NOT NULL THEN
        NEW.name := NEW.first_name || ' ' || NEW.last_name;
    END IF;

    RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER user_name_sync
BEFORE INSERT OR UPDATE ON users
FOR EACH ROW
EXECUTE FUNCTION sync_user_name();

-- ═══════════════════════════════════════════════════════════
-- MIGRATE PHASE - Background job
-- ═══════════════════════════════════════════════════════════

-- Batch update existing data
DO $$
DECLARE
    batch_size INT := 1000;
    processed INT := 0;
BEGIN
    LOOP
        UPDATE users
        SET
            first_name = split_part(name, ' ', 1),
            last_name = COALESCE(split_part(name, ' ', 2), '')
        WHERE id IN (
            SELECT id
            FROM users
            WHERE first_name IS NULL
            LIMIT batch_size
        );

        GET DIAGNOSTICS processed = ROW_COUNT;
        EXIT WHEN processed = 0;

        -- Sleep between batches to avoid load
        PERFORM pg_sleep(1);
    END LOOP;
END $$;

-- ═══════════════════════════════════════════════════════════
-- CONTRACT PHASE - Remove old column
-- Only after ALL code uses new columns!
-- ═══════════════════════════════════════════════════════════

-- Drop trigger
DROP TRIGGER IF EXISTS user_name_sync ON users;
DROP FUNCTION IF EXISTS sync_user_name();

-- Make new columns NOT NULL
ALTER TABLE users
ALTER COLUMN first_name SET NOT NULL,
ALTER COLUMN last_name SET NOT NULL;

-- Remove old column
ALTER TABLE users DROP COLUMN name;
```

---

### Zero-Downtime Migration Strategy

```javascript
// ═══════════════════════════════════════════════════════════
// APPLICATION CODE - COMPATIBLE WITH BOTH SCHEMAS
// Supports old and new database schema
// ═══════════════════════════════════════════════════════════

class User {
  constructor(data) {
    this.id = data.id;
    this.email = data.email;

    // Support both old and new schema
    if (data.first_name && data.last_name) {
      // New schema
      this.firstName = data.first_name;
      this.lastName = data.last_name;
      this.name = `${data.first_name} ${data.last_name}`;
    } else if (data.name) {
      // Old schema
      this.name = data.name;
      const parts = data.name.split(" ");
      this.firstName = parts[0] || "";
      this.lastName = parts.slice(1).join(" ") || "";
    }
  }

  // Save method works with both schemas
  async save(db) {
    // Write to both old and new columns (during transition)
    return await db.query(
      `
      UPDATE users
      SET
        name = $1,
        first_name = $2,
        last_name = $3
      WHERE id = $4
    `,
      [this.name, this.firstName, this.lastName, this.id]
    );
  }

  // After migration complete, simplify:
  async saveNew(db) {
    return await db.query(
      `
      UPDATE users
      SET
        first_name = $1,
        last_name = $2
      WHERE id = $3
    `,
      [this.firstName, this.lastName, this.id]
    );
  }
}
```

---

### Migration Tools

```bash
# ═══════════════════════════════════════════════════════════
# DATABASE MIGRATION TOOLS
# ═══════════════════════════════════════════════════════════

# Flyway (Java-based)
flyway migrate -url=jdbc:postgresql://localhost/mydb -user=user -password=pass

# Liquibase (Java-based)
liquibase update --changelog-file=changelog.xml

# Alembic (Python)
alembic upgrade head

# Prisma (Node.js)
npx prisma migrate deploy

# golang-migrate
migrate -path ./migrations -database postgres://localhost/mydb up

# Atlas (Modern declarative migrations)
atlas schema apply --url "postgres://localhost/mydb"
```

---

### Migration Best Practices

```
🎯 DATABASE MIGRATION RULES:

1️⃣  Never Break Backwards Compatibility
    • Old code must work with new schema
    • Use expand-migrate-contract pattern

2️⃣  Make Changes in Small Steps
    • One change per migration
    • Deploy frequently
    • Easier to rollback

3️⃣  Test Migrations Thoroughly
    • Test on production-like data
    • Test rollback procedures
    • Load test with new schema

4️⃣  Use Transactions (When Possible)
    BEGIN;
    -- migration
    COMMIT;

5️⃣  Avoid Large Table Locks
    • Use concurrent indexes
    • Batch large updates
    • Avoid ALTER TABLE on huge tables

6️⃣  Always Have Rollback Plan
    • Write down migration
    • Write rollback migration
    • Test both!

7️⃣  Monitor During Migration
    • Database locks
    • Replication lag
    • Application errors
    • Query performance

8️⃣  Communicate Schema Changes
    • Notify team before deployment
    • Document breaking changes
    • Coordinate with app deployments

📋 SAFE OPERATIONS (No downtime):
✅ Add new table
✅ Add new column (nullable)
✅ Add new index (CONCURRENT)
✅ Create new trigger
✅ Add CHECK constraint (NOT VALID, then VALIDATE)

⚠️ RISKY OPERATIONS (Need careful planning):
⚠️ Drop column (need expand-contract)
⚠️ Rename column (need expand-contract)
⚠️ Change column type
⚠️ Add NOT NULL constraint
⚠️ Drop table

❌ NEVER DO:
❌ Drop column in same deploy as code change
❌ Rename column without backward compatibility
❌ Change column type without migration period
```

---

<div align="center">

## 🔙 Rollback Strategies

_When things go wrong (and they will)_ 🚨

</div>

### Rollback Methods Comparison

<div align="center">

| Method                 |   Speed    | Data Loss Risk | Complexity | Best For    |
| :--------------------- | :--------: | :------------: | :--------: | :---------- |
| **Service Switch**     | ⚡⚡⚡⚡⚡ |      Low       |    Low     | Blue-Green  |
| **Container Rollback** |  ⚡⚡⚡⚡  |      Low       |    Low     | Kubernetes  |
| **Git Revert**         |   ⚡⚡⚡   |     Medium     |   Medium   | Simple apps |
| **Database Restore**   |     ⚡     |      High      |    High    | Last resort |
| **Feature Flag**       | ⚡⚡⚡⚡⚡ |      None      |    Low     | Modern apps |

</div>

---

### Kubernetes Rollback

```bash
# ═══════════════════════════════════════════════════════════
# KUBERNETES ROLLBACK COMMANDS
# ═══════════════════════════════════════════════════════════

# View deployment history
kubectl rollout history deployment/my-app

# Output:
# REVISION  CHANGE-CAUSE
# 1         Initial deployment
# 2         Update to v2.0.0
# 3         Update to v2.1.0

# Check rollout status
kubectl rollout status deployment/my-app

# Undo to previous version (most common)
kubectl rollout undo deployment/my-app

# Undo to specific revision
kubectl rollout undo deployment/my-app --to-revision=2

# Pause rollout (stop mid-deployment)
kubectl rollout pause deployment/my-app

# Resume paused rollout
kubectl rollout resume deployment/my-app

# Restart deployment (useful for ConfigMap changes)
kubectl rollout restart deployment/my-app
```

---

### Automated Rollback Script

```bash
#!/bin/bash
# ═══════════════════════════════════════════════════════════
# AUTOMATED ROLLBACK SCRIPT
# Monitors deployment and rolls back if issues detected
# ═══════════════════════════════════════════════════════════

set -euo pipefail

APP_NAME="my-app"
NAMESPACE="production"
ERROR_THRESHOLD=0.05
LATENCY_THRESHOLD_MS=1000
MONITORING_DURATION=300  # 5 minutes

# Check if deployment is healthy
check_deployment_health() {
    local deployment=$1

    # Check pod status
    local ready=$(kubectl get deployment $deployment -n $NAMESPACE \
      -o jsonpath='{.status.readyReplicas}')
    local desired=$(kubectl get deployment $deployment -n $NAMESPACE \
      -o jsonpath='{.spec.replicas}')

    if [ "$ready" != "$desired" ]; then
        echo "UNHEALTHY: $ready/$desired pods ready"
        return 1
    fi

    # Check for pod crashes
    local crashes=$(kubectl get pods -n $NAMESPACE -l app=$APP_NAME \
      -o jsonpath='{range .items[*]}{.status.containerStatuses[0].restartCount}{"\n"}{end}' | \
      awk '{sum+=$1} END {print sum}')

    if [ "$crashes" -gt 5 ]; then
        echo "UNHEALTHY: Too many restarts ($crashes)"
        return 1
    fi

    return 0
}

# Check application metrics
check_application_metrics() {
    # Query Prometheus
    local error_rate=$(curl -s 'http://prometheus:9090/api/v1/query' \
      --data-urlencode "query=rate(http_requests_total{app=\"$APP_NAME\",status=~\"5..\"}[5m])" | \
      jq -r '.data.result[0].value[1] // 0')

    local latency=$(curl -s 'http://prometheus:9090/api/v1/query' \
      --data-urlencode "query=histogram_quantile(0.99, rate(http_request_duration_seconds_bucket{app=\"$APP_NAME\"}[5m])) * 1000" | \
      jq -r '.data.result[0].value[1] // 0')

    echo "Metrics: error_rate=$error_rate, p99_latency=${latency}ms"

    # Check thresholds
    if (( $(echo "$error_rate > $ERROR_THRESHOLD" | bc -l) )); then
        echo "UNHEALTHY: Error rate too high ($error_rate)"
        return 1
    fi

    if (( $(echo "$latency > $LATENCY_THRESHOLD_MS" | bc -l) )); then
        echo "UNHEALTHY: Latency too high (${latency}ms)"
        return 1
    fi

    return 0
}

# Perform rollback
perform_rollback() {
    echo "🚨 ROLLING BACK DEPLOYMENT! 🚨"

    # Get current revision
    local current_rev=$(kubectl rollout history deployment/$APP_NAME -n $NAMESPACE | \
      tail -n 1 | awk '{print $1}')

    # Rollback
    kubectl rollout undo deployment/$APP_NAME -n $NAMESPACE

    # Wait for rollback to complete
    kubectl rollout status deployment/$APP_NAME -n $NAMESPACE --timeout=300s

    # Verify health after rollback
    sleep 30
    if check_deployment_health "$APP_NAME"; then
        echo "✅ Rollback successful!"
    else
        echo "❌ Rollback completed but issues remain!"
    fi

    # Send alert
    send_alert "Deployment rolled back from revision $current_rev"
}

# Send alert to team
send_alert() {
    local message=$1

    # Slack
    curl -X POST "$SLACK_WEBHOOK_URL" \
      -H 'Content-Type: application/json' \
      -d "{\"text\":\"🚨 $message\"}"

    # PagerDuty
    # curl -X POST "https://events.pagerduty.com/v2/enqueue" ...
}

# Main monitoring loop
main() {
    echo "🔍 Monitoring deployment of $APP_NAME..."

    local start_time=$(date +%s)
    local end_time=$((start_time + MONITORING_DURATION))
    local check_interval=30
    local consecutive_failures=0
    local max_consecutive_failures=3

    while [ $(date +%s) -lt $end_time ]; do
        echo "--- Health Check ---"

        # Check deployment health
        if ! check_deployment_health "$APP_NAME"; then
            ((consecutive_failures++))
            echo "⚠️ Health check failed ($consecutive_failures/$max_consecutive_failures)"
        else
            echo "✅ Deployment healthy"
            consecutive_failures=0
        fi

        # Check application metrics
        if ! check_application_metrics; then
            ((consecutive_failures++))
            echo "⚠️ Metrics check failed ($consecutive_failures/$max_consecutive_failures)"
        else
            echo "✅ Metrics healthy"
        fi

        # Rollback if too many failures
        if [ $consecutive_failures -ge $max_consecutive_failures ]; then
            perform_rollback
            exit 1
        fi

        # Wait before next check
        sleep $check_interval
    done

    echo "✅ Monitoring complete - deployment successful!"
}

main "$@"
```

---

### Database Rollback Strategy

```sql
-- ═══════════════════════════════════════════════════════════
-- DATABASE ROLLBACK STRATEGIES
-- ═══════════════════════════════════════════════════════════

-- Strategy 1: Keep old columns during transition
-- This allows rollback without data loss

-- Forward migration (can rollback)
ALTER TABLE users ADD COLUMN new_field VARCHAR(255);
UPDATE users SET new_field = old_field;

-- Rollback: Just use old field again
-- No data loss!

-- Strategy 2: Versioned schema
-- Keep schema version in database

CREATE TABLE schema_version (
    version INT PRIMARY KEY,
    applied_at TIMESTAMP DEFAULT NOW(),
    description TEXT
);

-- Each migration records version
INSERT INTO schema_version (version, description)
VALUES (5, 'Added new_field to users table');

-- Application checks compatible version range
-- version >= 5 AND version <= 10

-- Strategy 3: Shadow tables for risky migrations
-- Keep old data in separate table during migration

-- Create shadow table
CREATE TABLE users_backup AS SELECT * FROM users;

-- Perform migration
ALTER TABLE users ADD COLUMN new_structure JSONB;
UPDATE users SET new_structure = to_jsonb(old_structure);

-- If rollback needed:
DROP TABLE users;
ALTER TABLE users_backup RENAME TO users;

-- Strategy 4: Soft deletes instead of hard deletes
-- Never actually delete data

ALTER TABLE users ADD COLUMN deleted_at TIMESTAMP;
CREATE INDEX idx_users_deleted ON users(deleted_at) WHERE deleted_at IS NULL;

-- "Delete" records
UPDATE users SET deleted_at = NOW() WHERE id = 123;

-- Rollback deletion
UPDATE users SET deleted_at = NULL WHERE id = 123;
```

---

### Rollback Checklist

```markdown
## Rollback Decision Checklist

### Trigger Rollback If:

- [ ] Error rate > 5% for 5+ minutes
- [ ] P99 latency > 2x baseline
- [ ] More than 10% of pods crashing
- [ ] Critical functionality broken
- [ ] Database connection issues
- [ ] External service failures
- [ ] Memory leaks detected
- [ ] CPU usage > 90% sustained

### Before Rolling Back:

- [ ] Confirm issue is from deployment (not infrastructure)
- [ ] Document symptoms
- [ ] Capture logs & metrics
- [ ] Notify team
- [ ] Check if hotfix is faster than rollback

### During Rollback:

- [ ] Monitor rollback progress
- [ ] Verify health checks
- [ ] Check database consistency
- [ ] Test critical flows
- [ ] Monitor for new issues

### After Rollback:

- [ ] Verify system stability
- [ ] Conduct post-mortem
- [ ] Fix root cause
- [ ] Update tests
- [ ] Plan re-deployment
```

---

<div align="center">

## 📊 Monitoring & Observability

_You can't deploy what you can't measure_ 📈

</div>

### Key Deployment Metrics

```yaml
# ═══════════════════════════════════════════════════════════
# PROMETHEUS METRICS FOR DEPLOYMENTS
# Track deployment health and performance
# ═══════════════════════════════════════════════════════════

# 1. Deployment Success Rate
deployment_success_total / deployment_attempts_total

# 2. Deployment Duration
histogram_quantile(0.99, deployment_duration_seconds_bucket)

# 3. Rollback Rate
rollback_total / deployment_attempts_total

# 4. Error Rate During Deployment
rate(http_requests_total{status=~"5.."}[5m])

# 5. Latency During Deployment
histogram_quantile(0.99, rate(http_request_duration_seconds_bucket[5m]))

# 6. Pod Restart Count
sum(kube_pod_container_status_restarts_total) by (pod)

# 7. Deployment Frequency (DORA Metric)
count_over_time(deployment_completed_total[7d])

# 8. Mean Time to Recovery (DORA Metric)
avg(time_to_recovery_seconds)

# 9. Change Failure Rate (DORA Metric)
failed_deployments_total / deployment_attempts_total
```

---

### Grafana Dashboard Example

```json
{
  "dashboard": {
    "title": "Deployment Monitoring",
    "panels": [
      {
        "title": "Deployment Status",
        "targets": [
          {
            "expr": "deployment_status{app=\"my-app\"}",
            "legendFormat": "{{version}}"
          }
        ]
      },
      {
        "title": "Error Rate",
        "targets": [
          {
            "expr": "rate(http_requests_total{status=~\"5..\"}[5m])",
            "legendFormat": "Errors/sec"
          }
        ],
        "alert": {
          "conditions": [
            {
              "evaluator": {
                "params": [0.05],
                "type": "gt"
              }
            }
          ]
        }
      },
      {
        "title": "P99 Latency",
        "targets": [
          {
            "expr": "histogram_quantile(0.99, rate(http_request_duration_seconds_bucket[5m]))",
            "legendFormat": "P99"
          }
        ]
      },
      {
        "title": "Pod Health",
        "targets": [
          {
            "expr": "kube_deployment_status_replicas_available / kube_deployment_spec_replicas",
            "legendFormat": "Available %"
          }
        ]
      }
    ]
  }
}
```

---

<div align="center">

## 🛠️ Tools & Platforms

_The deployment toolbox_ 🧰

</div>

### Deployment Tool Comparison

<div align="center">

| Tool               | Type       | Learning Curve | Best For         |    Cost     |
| :----------------- | :--------- | :------------: | :--------------- | :---------: |
| **Kubernetes**     | Platform   |   ⭐⭐⭐⭐⭐   | Everything       |    Free     |
| **ArgoCD**         | GitOps     |     ⭐⭐⭐     | K8s deployments  |    Free     |
| **Spinnaker**      | Pipeline   |    ⭐⭐⭐⭐    | Multi-cloud      |    Free     |
| **Flux**           | GitOps     |     ⭐⭐⭐     | K8s GitOps       |    Free     |
| **Jenkins**        | CI/CD      |     ⭐⭐⭐     | Traditional      |    Free     |
| **GitHub Actions** | CI/CD      |      ⭐⭐      | GitHub projects  |  Free tier  |
| **GitLab CI**      | CI/CD      |      ⭐⭐      | GitLab projects  |  Free tier  |
| **AWS CodeDeploy** | Deployment |      ⭐⭐      | AWS              | Pay-per-use |
| **Vercel**         | Platform   |       ⭐       | Frontend/Next.js |  Free tier  |
| **Railway**        | Platform   |       ⭐       | Full-stack apps  |  Free tier  |

</div>

---

<div align="center">

## 💡 Best Practices

_MrDib's deployment wisdom_ 🎓

</div>

### The Deployment Commandments

```
🏆 The 15 Commandments of Safe Deployment:

1️⃣  Always Have a Rollback Plan
    • Know how to rollback BEFORE deploying
    • Test rollback procedure
    • Document it

2️⃣  Deploy During Low Traffic
    • 2 AM deployments exist for a reason
    • Or use gradual rollouts

3️⃣  Monitor Everything
    • Error rates
    • Latency
    • Resource usage
    • Business metrics

4️⃣  Automate, Automate, Automate
    • Manual deployments = human errors
    • CI/CD pipelines are your friend

5️⃣  Test in Production-Like Environment
    • Staging should mirror production
    • Test with real data volumes

6️⃣  Use Feature Flags
    • Decouple deploy from release
    • Instant rollback without redeployment

7️⃣  Deploy Small Changes
    • Small changes = small risk
    • Deploy frequently

8️⃣  Never Skip the Smoke Tests
    • Basic functionality checks
    • Critical user flows

9️⃣  Communicate with Team
    • Notify before deployment
    • Keep team updated
    • Post-mortem after incidents

🔟 Document Everything
    • What changed?
    • Why?
    • Who deployed?
    • What time?

1️⃣1️⃣  Version Everything
    • Code (Git tags)
    • Docker images
    • Database schemas

1️⃣2️⃣  Handle Database Migrations Carefully
    • Backward compatible changes
    • Expand-migrate-contract
    • Never break old code

1️⃣3️⃣  Set Up Proper Alerts
    • Error rate spikes
    • Latency increases
    • Pod crashes

1️⃣4️⃣  Practice Chaos Engineering
    • Test failure scenarios
    • Practice rollbacks
    • Run game days

1️⃣5️⃣  Learn from Failures
    • Blameless post-mortems
    • Document lessons learned
    • Improve processes
```

---

### Common Deployment Mistakes

```
❌ TOP 10 DEPLOYMENT DISASTERS:

1. "It works on my machine"
   → Use containers, ensure parity

2. Deploying Friday afternoon
   → Never deploy before weekend

3. No rollback plan
   → Always have a way back

4. Skipping staging
   → Test in prod-like environment

5. Deploying database changes with code
   → Separate DB migrations

6. Not monitoring after deploy
   → Watch for 30+ minutes

7. Deploying during peak traffic
   → Choose low-traffic windows

8. No health checks
   → Implement proper probes

9. Ignoring warnings in logs
   → Warnings become errors

10. Not testing rollback
    → Test rollback before you need it
```

---

<div align="center">

## 🎉 You're Now a Deployment Master!

**You've learned:**

- ✅ 7 deployment strategies
- ✅ Zero-downtime techniques
- ✅ Database migration patterns
- ✅ Feature flag implementation
- ✅ Rollback strategies
- ✅ Monitoring & observability
- ✅ Production-ready scripts
- ✅ Best practices

### Remember

> **"Hope is not a strategy."** - Traditional DevOps Wisdom

And more importantly:

> **"Deploy small, deploy often, and always have a rollback plan."** - MrDib 🚀

</div>

---

### Quick Reference

<div align="center">

| Situation                               | Use This    | Why                 |
| :-------------------------------------- | :---------- | :------------------ |
| **Small app, low traffic**              | Rolling     | Simple, efficient   |
| **Critical app, need instant rollback** | Blue-Green  | Instant switch back |
| **Large scale, gradual testing**        | Canary      | Low risk validation |
| **Testing features**                    | A/B Testing | Measure impact      |
| **Testing performance**                 | Shadow      | No user impact      |
| **Dev/Test only**                       | Recreate    | Simplest            |

</div>

---

<div align="center">

**Built with 🚀 by MrDib, for engineers who ship with confidence**

_Now go deploy something amazing (safely)!_ ✨

**Remember: The best deployment is the one nobody notices!** 🎯

</div>

---

### Final Pro Tips

```
💎 MrDib's Deployment Wisdom:

1. Start simple (Rolling) → Add complexity as needed
2. Blue-Green for critical apps worth the cost
3. Canary for large-scale (> 100K users)
4. Feature flags are your insurance policy
5. Database migrations need 3-phase deployment
6. Monitor for 30min minimum after deploy
7. Rollback if in doubt
8. Document everything
9. Automate everything
10. Practice makes perfect (run drills!)

📚 Essential Reading:
• "Accelerate" by Nicole Forsgren
• "Site Reliability Engineering" by Google
• "The Phoenix Project" by Gene Kim

🔧 Must-Have Tools:
• Kubernetes (orchestration)
• ArgoCD (GitOps)
• Prometheus + Grafana (monitoring)
• LaunchDarkly or similar (feature flags)
• PagerDuty (alerting)

🎯 The Golden Rules:
• Deploy frequently (reduce risk per deploy)
• Monitor everything (you can't fix what you can't see)
• Automate (humans make mistakes)
• Test rollbacks (practice before you need it)
• Learn from failures (blameless post-mortems)

Now go ship code with confidence! 🚀
```
