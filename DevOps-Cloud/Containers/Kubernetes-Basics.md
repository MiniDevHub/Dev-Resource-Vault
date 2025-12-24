<div align="center">

# ⛵ Kubernetes - The Complete Guide

### _Orchestrating containers at scale_ 🚀

![Kubernetes](https://img.shields.io/badge/Kubernetes-1.29+-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![Scale](https://img.shields.io/badge/Scale-Production%20Ready-success?style=for-the-badge)
![CNCF](https://img.shields.io/badge/CNCF-Graduated-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Industry%20Standard-gold?style=for-the-badge)

</div>

---

## 📚 Table of Contents

- [🎯 Kubernetes Fundamentals](#-kubernetes-fundamentals)
- [🏗️ Architecture Deep Dive](#️-architecture-deep-dive)
- [🚀 Getting Started](#-getting-started)
- [📦 Core Resources](#-core-resources)
- [🌐 Networking](#-networking)
- [💾 Storage](#-storage)
- [⚙️ Advanced Workloads](#️-advanced-workloads)
- [🔐 Security](#-security)
- [📊 Monitoring & Logging](#-monitoring--logging)
- [🎛️ Configuration Management](#️-configuration-management)
- [📦 Package Management (Helm)](#-package-management-helm)
- [🐛 Troubleshooting](#-troubleshooting)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 🎯 Kubernetes Fundamentals

_Understanding K8s from first principles_ 🧠

</div>

### What is Kubernetes? The 5-Minute Explanation

```
🎯 THE PROBLEM KUBERNETES SOLVES:

Without Orchestration:
┌──────────────────────────────────────────────────────┐
│  You have 100 containers to manage:                  │
│                                                       │
│  Tasks:                                              │
│  ❌ Manually deploy containers to servers           │
│  ❌ Monitor health and restart if crashed           │
│  ❌ Scale up/down based on load                     │
│  ❌ Load balance traffic                            │
│  ❌ Handle updates without downtime                 │
│  ❌ Manage configuration and secrets                │
│  ❌ Schedule containers on available nodes          │
│                                                       │
│  Result: 🔥 Chaos, manual work, no sleep!           │
└──────────────────────────────────────────────────────┘

═══════════════════════════════════════════════════════════

With Kubernetes:
┌──────────────────────────────────────────────────────┐
│  You declare desired state:                          │
│  "I want 5 replicas of my app running"              │
│                                                       │
│  Kubernetes handles:                                 │
│  ✅ Automatic deployment                            │
│  ✅ Self-healing (auto-restart failures)            │
│  ✅ Auto-scaling (based on CPU/memory)              │
│  ✅ Load balancing (built-in)                       │
│  ✅ Rolling updates (zero downtime)                 │
│  ✅ Configuration management                         │
│  ✅ Intelligent scheduling                           │
│                                                       │
│  Result: 😌 Automated, scalable, reliable!          │
└──────────────────────────────────────────────────────┘

═══════════════════════════════════════════════════════════

KUBERNETES IN ONE SENTENCE:

"I tell Kubernetes what I want (desired state),
 and it makes sure that's what I get (actual state)"

Example:
  You say: "I want 3 replicas of my app"
  One crashes: Kubernetes automatically starts a new one
  You update: "I want 5 replicas now"
  Kubernetes: Starts 2 more immediately

═══════════════════════════════════════════════════════════

WHY "K8s"?

Kubernetes = K + 8 letters + s = K8s 🤓
(ubernete has 8 letters)

Also called:
• Kube
• K8s
• The Greek word for "helmsman" or "pilot" ⛵
```

---

### Key Concepts Explained

```
📦 KUBERNETES BUILDING BLOCKS:

1. POD (Smallest Unit)
   ┌────────────────────────┐
   │      Pod               │
   │  ┌──────────────────┐  │
   │  │  Container 1     │  │
   │  │  (nginx)         │  │
   │  └──────────────────┘  │
   │  ┌──────────────────┐  │
   │  │  Container 2     │  │
   │  │  (sidecar)       │  │
   │  └──────────────────┘  │
   │  Shared:               │
   │  • Network namespace   │
   │  • Storage volumes     │
   │  • IP address          │
   └────────────────────────┘

   • Smallest deployable unit
   • One or more containers
   • Share network and storage
   • Ephemeral (can die anytime)

2. REPLICASET (Ensures Replicas)
   ┌────────────────────────────────┐
   │      ReplicaSet                │
   │  Desired: 3                    │
   │  Current: 3                    │
   │                                │
   │  ┌─────┐  ┌─────┐  ┌─────┐    │
   │  │ Pod │  │ Pod │  │ Pod │    │
   │  │  1  │  │  2  │  │  3  │    │
   │  └─────┘  └─────┘  └─────┘    │
   │                                │
   │  If Pod 2 dies:                │
   │  ┌─────┐  ┌─────┐  ┌─────┐    │
   │  │ Pod │  │ New │  │ Pod │    │
   │  │  1  │  │ Pod │  │  3  │    │
   │  └─────┘  └─────┘  └─────┘    │
   └────────────────────────────────┘

   • Maintains desired number of pods
   • Creates new pods if some die
   • Usually managed by Deployment

3. DEPLOYMENT (Manages Updates)
   ┌─────────────────────────────────┐
   │      Deployment                 │
   │  ┌───────────────────────────┐  │
   │  │   ReplicaSet v1 (old)     │  │
   │  │   ┌─────┐  ┌─────┐        │  │
   │  │   │ Pod │  │ Pod │        │  │
   │  │   └─────┘  └─────┘        │  │
   │  └───────────────────────────┘  │
   │           ↓ Rolling Update       │
   │  ┌───────────────────────────┐  │
   │  │   ReplicaSet v2 (new)     │  │
   │  │   ┌─────┐  ┌─────┐        │  │
   │  │   │ Pod │  │ Pod │        │  │
   │  │   └─────┘  └─────┘        │  │
   │  └───────────────────────────┘  │
   └─────────────────────────────────┘

   • Manages ReplicaSets
   • Handles rolling updates
   • Rollback capability
   • Most common workload

4. SERVICE (Stable Network Endpoint)
   ┌─────────────────────────────────┐
   │      Service                    │
   │      (my-app-service)           │
   │      IP: 10.0.0.5               │
   │                                 │
   │      ↓ Load Balances            │
   │                                 │
   │  ┌─────┐  ┌─────┐  ┌─────┐     │
   │  │ Pod │  │ Pod │  │ Pod │     │
   │  │10.1 │  │10.2 │  │10.3 │     │
   │  └─────┘  └─────┘  └─────┘     │
   └─────────────────────────────────┘

   • Stable IP/DNS name
   • Load balances across pods
   • Service discovery
   • Types: ClusterIP, NodePort, LoadBalancer

5. INGRESS (HTTP Routing)
   ┌─────────────────────────────────────┐
   │         Ingress                     │
   │   (myapp.com, api.myapp.com)       │
   │                                     │
   │   myapp.com/     → frontend-svc    │
   │   myapp.com/api  → backend-svc     │
   └─────────────────────────────────────┘

   • HTTP/HTTPS routing
   • SSL/TLS termination
   • Name-based virtual hosting
   • Path-based routing

6. CONFIGMAP & SECRET (Configuration)
   ┌─────────────────────────────────┐
   │      ConfigMap                  │
   │  API_URL: https://api.com       │
   │  LOG_LEVEL: info                │
   └─────────────────────────────────┘
            ↓ Inject into Pod
   ┌─────────────────────────────────┐
   │      Secret                     │
   │  DB_PASSWORD: [encrypted]       │
   │  API_KEY: [encrypted]           │
   └─────────────────────────────────┘

   • ConfigMap: Non-sensitive config
   • Secret: Sensitive data (base64 encoded)
   • Injected as env vars or files

7. NAMESPACE (Virtual Clusters)
   ┌──────────────────────────────────────┐
   │           Cluster                    │
   │  ┌────────────────────────────┐      │
   │  │  Namespace: production     │      │
   │  │  • Pods, Services, etc.    │      │
   │  └────────────────────────────┘      │
   │  ┌────────────────────────────┐      │
   │  │  Namespace: staging        │      │
   │  │  • Pods, Services, etc.    │      │
   │  └────────────────────────────┘      │
   │  ┌────────────────────────────┐      │
   │  │  Namespace: development    │      │
   │  │  • Pods, Services, etc.    │      │
   │  └────────────────────────────┘      │
   └──────────────────────────────────────┘

   • Logical isolation
   • Resource quotas
   • Access control
   • Environment separation
```

---

<div align="center">

## 🏗️ Architecture Deep Dive

_How Kubernetes works under the hood_ ⚙️

</div>

### Cluster Architecture

```
🏗️ KUBERNETES CLUSTER ARCHITECTURE:

┌─────────────────────────────────────────────────────────────┐
│                    KUBERNETES CLUSTER                        │
└─────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────┐
│                  CONTROL PLANE (Master)                       │
│  ┌────────────────────────────────────────────────────┐      │
│  │              API SERVER (kube-apiserver)           │      │
│  │  • REST API (kubectl talks to this)               │      │
│  │  • Authentication & authorization                  │      │
│  │  • Validates and processes requests               │      │
│  │  • Only component that talks to etcd              │      │
│  └────────────────────────────────────────────────────┘      │
│                          ↕                                    │
│  ┌────────────────────────────────────────────────────┐      │
│  │                etcd (Key-Value Store)              │      │
│  │  • Cluster state storage                          │      │
│  │  • Configuration data                             │      │
│  │  • Source of truth for cluster                    │      │
│  └────────────────────────────────────────────────────┘      │
│                          ↕                                    │
│  ┌────────────────────────────────────────────────────┐      │
│  │              SCHEDULER (kube-scheduler)            │      │
│  │  • Watches for new pods                           │      │
│  │  • Decides which node to run pod on               │      │
│  │  • Considers resources, constraints, affinity     │      │
│  └────────────────────────────────────────────────────┘      │
│                          ↕                                    │
│  ┌────────────────────────────────────────────────────┐      │
│  │    CONTROLLER MANAGER (kube-controller-manager)    │      │
│  │  • Node Controller (monitors nodes)               │      │
│  │  • Replication Controller (maintains replicas)    │      │
│  │  • Endpoints Controller (populates endpoints)     │      │
│  │  • Service Account & Token Controllers            │      │
│  └────────────────────────────────────────────────────┘      │
│                          ↕                                    │
│  ┌────────────────────────────────────────────────────┐      │
│  │         CLOUD CONTROLLER MANAGER (optional)        │      │
│  │  • Cloud-specific control logic                   │      │
│  │  • Node, Route, Service, Volume controllers       │      │
│  └────────────────────────────────────────────────────┘      │
└──────────────────────────────────────────────────────────────┘

                              ↕
        ┌─────────────────────┴─────────────────────┐
        │                                            │
┌───────▼─────────┐  ┌──────────────┐  ┌───────────▼──────┐
│   WORKER NODE 1 │  │ WORKER NODE 2│  │  WORKER NODE 3   │
├─────────────────┤  ├──────────────┤  ├──────────────────┤
│ ┌─────────────┐ │  │┌────────────┐│  │┌─────────────┐   │
│ │   kubelet   │ │  ││  kubelet   ││  ││   kubelet   │   │
│ │ • Pod mgmt  │ │  ││ • Pod mgmt ││  ││ • Pod mgmt  │   │
│ │ • Talks to  │ │  ││ • Talks to ││  ││ • Talks to  │   │
│ │   API       │ │  ││   API      ││  ││   API       │   │
│ └─────────────┘ │  │└────────────┘│  │└─────────────┘   │
│ ┌─────────────┐ │  │┌────────────┐│  │┌─────────────┐   │
│ │ kube-proxy  │ │  ││ kube-proxy ││  ││ kube-proxy  │   │
│ │ • Networking│ │  ││ • Network  ││  ││ • Networking│   │
│ │ • Load bal. │ │  ││ • Load bal.││  ││ • Load bal. │   │
│ └─────────────┘ │  │└────────────┘│  │└─────────────┘   │
│ ┌─────────────┐ │  │┌────────────┐│  │┌─────────────┐   │
│ │  Container  │ │  ││ Container  ││  ││  Container  │   │
│ │   Runtime   │ │  ││  Runtime   ││  ││   Runtime   │   │
│ │  (Docker/   │ │  ││ (Docker/   ││  ││  (Docker/   │   │
│ │containerd)  │ │  ││containerd) ││  ││ containerd) │   │
│ └─────────────┘ │  │└────────────┘│  │└─────────────┘   │
│ ┌─────────────┐ │  │┌────────────┐│  │┌─────────────┐   │
│ │    Pods     │ │  ││   Pods     ││  ││    Pods     │   │
│ │  ┌───┐┌───┐ │ │  ││ ┌───┐┌───┐││  ││  ┌───┐┌───┐ │   │
│ │  │Pod││Pod│ │ │  ││ │Pod││Pod│││  ││  │Pod││Pod│ │   │
│ │  └───┘└───┘ │ │  ││ └───┘└───┘││  ││  └───┘└───┘ │   │
│ └─────────────┘ │  │└────────────┘│  │└─────────────┘   │
└─────────────────┘  └──────────────┘  └──────────────────┘

═══════════════════════════════════════════════════════════

HOW IT WORKS (Example: Creating a Deployment):

1. You: kubectl apply -f deployment.yaml
         ↓
2. API Server: Validates, authenticates, saves to etcd
         ↓
3. Controller Manager: "Oh, a new deployment! Need to create ReplicaSet"
         ↓
4. ReplicaSet Controller: "Need 3 pods? Let me create them"
         ↓
5. Scheduler: "Where should these pods run? Node 2 has space!"
         ↓
6. kubelet (Node 2): "Got new pods? Let me start containers"
         ↓
7. Container Runtime: Pulls image, starts containers
         ↓
8. kube-proxy: Updates networking rules
         ↓
9. Your app is running! 🎉

All this happens in seconds! ⚡
```

---

<div align="center">

## 🚀 Getting Started

_Your first Kubernetes cluster_ 🎬

</div>

### Local Development Options

```bash
# ═══════════════════════════════════════════════════════════
# OPTION 1: MINIKUBE (Most Popular)
# ═══════════════════════════════════════════════════════════

# Installation
# macOS
brew install minikube

# Linux
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube

# Windows (via Chocolatey)
choco install minikube

# Start cluster
minikube start

# Start with specific driver
minikube start --driver=docker
minikube start --driver=virtualbox

# Start with resource limits
minikube start --cpus=4 --memory=8g --disk-size=50g

# Check status
minikube status

# Access dashboard
minikube dashboard

# Stop cluster
minikube stop

# Delete cluster
minikube delete

# ═══════════════════════════════════════════════════════════
# OPTION 2: KIND (Kubernetes in Docker)
# ═══════════════════════════════════════════════════════════

# Installation
# macOS/Linux
brew install kind

# OR
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.20.0/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind

# Create cluster
kind create cluster

# Create cluster with name
kind create cluster --name my-cluster

# Create multi-node cluster
cat <<EOF | kind create cluster --config=-
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
- role: worker
- role: worker
EOF

# List clusters
kind get clusters

# Delete cluster
kind delete cluster --name my-cluster

# ═══════════════════════════════════════════════════════════
# OPTION 3: DOCKER DESKTOP (Easiest)
# ═══════════════════════════════════════════════════════════

# 1. Install Docker Desktop
# 2. Go to Settings → Kubernetes
# 3. Enable Kubernetes
# 4. Click Apply & Restart

# That's it! kubectl is ready to use

# ═══════════════════════════════════════════════════════════
# OPTION 4: K3S (Lightweight, Production-Grade)
# ═══════════════════════════════════════════════════════════

# Install (Linux)
curl -sfL https://get.k3s.io | sh -

# Check status
sudo systemctl status k3s

# Access with kubectl
sudo k3s kubectl get nodes

# OR copy kubeconfig
mkdir -p ~/.kube
sudo cp /etc/rancher/k3s/k3s.yaml ~/.kube/config
sudo chown $USER ~/.kube/config

# ═══════════════════════════════════════════════════════════
# INSTALL KUBECTL (Kubernetes CLI)
# ═══════════════════════════════════════════════════════════

# macOS
brew install kubectl

# Linux
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl

# Windows (via Chocolatey)
choco install kubernetes-cli

# Verify installation
kubectl version --client

# ═══════════════════════════════════════════════════════════
# KUBECTL COMPLETION & ALIASES
# ═══════════════════════════════════════════════════════════

# Bash completion
kubectl completion bash | sudo tee /etc/bash_completion.d/kubectl > /dev/null
echo 'source <(kubectl completion bash)' >>~/.bashrc

# Zsh completion
kubectl completion zsh > "${fpath[1]}/_kubectl"
echo 'source <(kubectl completion zsh)' >>~/.zshrc

# Useful aliases (add to ~/.bashrc or ~/.zshrc)
alias k='kubectl'
alias kgp='kubectl get pods'
alias kgs='kubectl get svc'
alias kgd='kubectl get deployments'
alias kga='kubectl get all'
alias kd='kubectl describe'
alias kdel='kubectl delete'
alias kl='kubectl logs'
alias klf='kubectl logs -f'
alias kex='kubectl exec -it'
alias ka='kubectl apply -f'
alias kgn='kubectl get nodes'

# Enable completion for alias
complete -F __start_kubectl k

# Reload shell
source ~/.bashrc  # or ~/.zshrc
```

---

### Your First Deployment

```bash
# ═══════════════════════════════════════════════════════════
# HELLO KUBERNETES - COMPLETE WALKTHROUGH
# ═══════════════════════════════════════════════════════════

# 1. Start local cluster
minikube start
# OR
kind create cluster

# 2. Verify cluster is running
kubectl cluster-info
kubectl get nodes

# 3. Create a deployment (nginx)
kubectl create deployment nginx --image=nginx:latest

# 4. Check deployment
kubectl get deployments
kubectl get pods

# 5. Expose deployment (create service)
kubectl expose deployment nginx --type=NodePort --port=80

# 6. Check service
kubectl get services

# 7. Access the service
# For minikube:
minikube service nginx --url

# OR port forward:
kubectl port-forward service/nginx 8080:80

# Open browser: http://localhost:8080

# 8. Scale deployment
kubectl scale deployment nginx --replicas=3

# 9. Check pods (should see 3 now!)
kubectl get pods

# 10. View deployment details
kubectl describe deployment nginx

# 11. View pod logs
kubectl logs <pod-name>

# 12. Execute command in pod
kubectl exec -it <pod-name> -- bash

# 13. Clean up
kubectl delete service nginx
kubectl delete deployment nginx

# ═══════════════════════════════════════════════════════════
# DECLARATIVE APPROACH (YAML Files)
# ═══════════════════════════════════════════════════════════

# Create deployment.yaml
cat <<EOF > deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.25-alpine
        ports:
        - containerPort: 80
EOF

# Apply deployment
kubectl apply -f deployment.yaml

# Create service.yaml
cat <<EOF > service.yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx
spec:
  selector:
    app: nginx
  ports:
  - protocol: TCP
    port: 80
    targetPort: 80
  type: LoadBalancer
EOF

# Apply service
kubectl apply -f service.yaml

# Check everything
kubectl get all

# Update deployment (change image)
kubectl set image deployment/nginx nginx=nginx:1.25-alpine

# Watch rollout
kubectl rollout status deployment/nginx

# View rollout history
kubectl rollout history deployment/nginx

# Rollback if needed
kubectl rollout undo deployment/nginx

# Clean up
kubectl delete -f deployment.yaml
kubectl delete -f service.yaml
```

<div align="center">

## 📦 Core Resources

_Deep dive into Kubernetes objects_ 🎯

</div>

### Pods - The Smallest Unit

```yaml
# ═══════════════════════════════════════════════════════════
# POD SPECIFICATION
# ═══════════════════════════════════════════════════════════

apiVersion: v1
kind: Pod
metadata:
  name: my-pod
  namespace: default
  labels:
    app: myapp
    environment: production
    version: v1.0.0
  annotations:
    description: "My application pod"
    owner: "devops-team"
spec:
  # ───────────────────────────────────────────────────────
  # Containers
  # ───────────────────────────────────────────────────────
  containers:
    - name: app
      image: myapp:v1.0.0
      imagePullPolicy: IfNotPresent # Always, Never, IfNotPresent

      # Ports
      ports:
        - containerPort: 3000
          name: http
          protocol: TCP

      # Environment Variables
      env:
        - name: NODE_ENV
          value: "production"
        - name: DATABASE_URL
          valueFrom:
            secretKeyRef:
              name: app-secrets
              key: database-url
        - name: CONFIG_FILE
          valueFrom:
            configMapKeyRef:
              name: app-config
              key: config.json

      # Resource Limits
      resources:
        requests:
          memory: "128Mi" # Minimum guaranteed
          cpu: "100m" # 100 millicores = 0.1 CPU
        limits:
          memory: "256Mi" # Maximum allowed
          cpu: "200m" # Will be throttled if exceeds

      # Health Checks
      livenessProbe:
        httpGet:
          path: /health
          port: 3000
        initialDelaySeconds: 30
        periodSeconds: 10
        timeoutSeconds: 5
        failureThreshold: 3

      readinessProbe:
        httpGet:
          path: /ready
          port: 3000
        initialDelaySeconds: 5
        periodSeconds: 5
        timeoutSeconds: 3
        failureThreshold: 3

      startupProbe: # For slow-starting apps
        httpGet:
          path: /startup
          port: 3000
        initialDelaySeconds: 0
        periodSeconds: 10
        failureThreshold: 30

      # Volume Mounts
      volumeMounts:
        - name: config-volume
          mountPath: /etc/config
        - name: data-volume
          mountPath: /data

      # Lifecycle Hooks
      lifecycle:
        postStart:
          exec:
            command: ["/bin/sh", "-c", "echo Container started"]
        preStop:
          exec:
            command:
              [
                "/bin/sh",
                "-c",
                "nginx -s quit; while killall -0 nginx; do sleep 1; done",
              ]

    # Sidecar Container (example)
    - name: log-shipper
      image: fluentd:latest
      volumeMounts:
        - name: logs
          mountPath: /var/log

  # ───────────────────────────────────────────────────────
  # Init Containers (run before main containers)
  # ───────────────────────────────────────────────────────
  initContainers:
    - name: init-db
      image: busybox:latest
      command:
        [
          "sh",
          "-c",
          "until nslookup db-service; do echo waiting for db; sleep 2; done",
        ]

  # ───────────────────────────────────────────────────────
  # Volumes
  # ───────────────────────────────────────────────────────
  volumes:
    - name: config-volume
      configMap:
        name: app-config
    - name: data-volume
      persistentVolumeClaim:
        claimName: app-data-pvc
    - name: logs
      emptyDir: {}

  # ───────────────────────────────────────────────────────
  # Pod Configuration
  # ───────────────────────────────────────────────────────
  restartPolicy: Always # Always, OnFailure, Never

  # Node Selection
  nodeSelector:
    disktype: ssd
    zone: us-west-1a

  # Affinity Rules
  affinity:
    nodeAffinity:
      requiredDuringSchedulingIgnoredDuringExecution:
        nodeSelectorTerms:
          - matchExpressions:
              - key: kubernetes.io/hostname
                operator: In
                values:
                  - node1
                  - node2

  # Tolerations (for taints)
  tolerations:
    - key: "app"
      operator: "Equal"
      value: "critical"
      effect: "NoSchedule"

  # Security Context
  securityContext:
    runAsNonRoot: true
    runAsUser: 1000
    fsGroup: 2000

  # Service Account
  serviceAccountName: app-service-account

  # DNS Policy
  dnsPolicy: ClusterFirst

  # Hostname
  hostname: my-pod
  subdomain: my-subdomain
```

---

### Deployments - Managing Replicas

```yaml
# ═══════════════════════════════════════════════════════════
# DEPLOYMENT SPECIFICATION
# ═══════════════════════════════════════════════════════════

apiVersion: apps/v1
kind: Deployment
metadata:
  name: web-app
  namespace: production
  labels:
    app: web-app
    tier: frontend
spec:
  # ───────────────────────────────────────────────────────
  # Replica Configuration
  # ───────────────────────────────────────────────────────
  replicas: 3

  # Selector (must match template labels)
  selector:
    matchLabels:
      app: web-app

  # ───────────────────────────────────────────────────────
  # Update Strategy
  # ───────────────────────────────────────────────────────
  strategy:
    type: RollingUpdate # RollingUpdate or Recreate
    rollingUpdate:
      maxSurge: 1 # Max pods above desired during update
      maxUnavailable: 0 # Max pods unavailable during update

  # Minimum time pod should be ready
  minReadySeconds: 10

  # How many old ReplicaSets to retain
  revisionHistoryLimit: 10

  # Progress deadline
  progressDeadlineSeconds: 600

  # ───────────────────────────────────────────────────────
  # Pod Template
  # ───────────────────────────────────────────────────────
  template:
    metadata:
      labels:
        app: web-app
        version: v1.0.0
      annotations:
        prometheus.io/scrape: "true"
        prometheus.io/port: "9090"

    spec:
      containers:
        - name: web
          image: myregistry.com/web-app:v1.0.0

          ports:
            - containerPort: 3000
              name: http

          env:
            - name: NODE_ENV
              value: "production"
            - name: PORT
              value: "3000"

          resources:
            requests:
              memory: "256Mi"
              cpu: "200m"
            limits:
              memory: "512Mi"
              cpu: "500m"

          livenessProbe:
            httpGet:
              path: /health
              port: 3000
            initialDelaySeconds: 30
            periodSeconds: 10

          readinessProbe:
            httpGet:
              path: /ready
              port: 3000
            initialDelaySeconds: 5
            periodSeconds: 5

      # Anti-affinity (spread pods across nodes)
      affinity:
        podAntiAffinity:
          preferredDuringSchedulingIgnoredDuringExecution:
            - weight: 100
              podAffinityTerm:
                labelSelector:
                  matchExpressions:
                    - key: app
                      operator: In
                      values:
                        - web-app
                topologyKey: kubernetes.io/hostname
```

```bash
# ═══════════════════════════════════════════════════════════
# DEPLOYMENT MANAGEMENT COMMANDS
# ═══════════════════════════════════════════════════════════

# Create deployment
kubectl apply -f deployment.yaml

# Get deployments
kubectl get deployments
kubectl get deploy -o wide

# Describe deployment
kubectl describe deployment web-app

# Scale deployment
kubectl scale deployment web-app --replicas=5

# Autoscale deployment
kubectl autoscale deployment web-app --min=3 --max=10 --cpu-percent=80

# Update image (triggers rollout)
kubectl set image deployment/web-app web=myregistry.com/web-app:v2.0.0

# Edit deployment
kubectl edit deployment web-app

# Watch rollout
kubectl rollout status deployment/web-app

# Pause rollout (for canary deployments)
kubectl rollout pause deployment/web-app

# Resume rollout
kubectl rollout resume deployment/web-app

# View rollout history
kubectl rollout history deployment/web-app

# Rollback to previous version
kubectl rollout undo deployment/web-app

# Rollback to specific revision
kubectl rollout undo deployment/web-app --to-revision=2

# View specific revision
kubectl rollout history deployment/web-app --revision=2

# Restart deployment (recreate all pods)
kubectl rollout restart deployment/web-app

# Delete deployment
kubectl delete deployment web-app
```

---

### Services - Networking

```yaml
# ═══════════════════════════════════════════════════════════
# SERVICE TYPES
# ═══════════════════════════════════════════════════════════

# ───────────────────────────────────────────────────────
# 1. ClusterIP (Default) - Internal only
# ───────────────────────────────────────────────────────
apiVersion: v1
kind: Service
metadata:
  name: backend-service
spec:
  type: ClusterIP
  selector:
    app: backend
  ports:
    - port: 80 # Service port
      targetPort: 3000 # Container port
      protocol: TCP
      name: http

# Access: Only from within cluster
# URL: backend-service.namespace.svc.cluster.local

---
# ───────────────────────────────────────────────────────
# 2. NodePort - Exposes on each Node's IP
# ───────────────────────────────────────────────────────
apiVersion: v1
kind: Service
metadata:
  name: web-service
spec:
  type: NodePort
  selector:
    app: web
  ports:
    - port: 80
      targetPort: 3000
      nodePort: 30080 # External port (30000-32767)
      protocol: TCP

# Access: <NodeIP>:30080 from outside cluster

---
# ───────────────────────────────────────────────────────
# 3. LoadBalancer - Cloud load balancer
# ───────────────────────────────────────────────────────
apiVersion: v1
kind: Service
metadata:
  name: public-service
  annotations:
    service.beta.kubernetes.io/aws-load-balancer-type: "nlb"
spec:
  type: LoadBalancer
  selector:
    app: web
  ports:
    - port: 80
      targetPort: 3000
      protocol: TCP
  sessionAffinity: ClientIP # Sticky sessions

# Access: Gets external IP from cloud provider

---
# ───────────────────────────────────────────────────────
# 4. Headless Service - No load balancing
# ───────────────────────────────────────────────────────
apiVersion: v1
kind: Service
metadata:
  name: database-service
spec:
  clusterIP: None # Headless!
  selector:
    app: database
  ports:
    - port: 5432
      targetPort: 5432

# Returns Pod IPs directly (for StatefulSets)

---
# ───────────────────────────────────────────────────────
# 5. ExternalName - DNS CNAME
# ───────────────────────────────────────────────────────
apiVersion: v1
kind: Service
metadata:
  name: external-api
spec:
  type: ExternalName
  externalName: api.external-service.com
# Access external service with internal name
```

---

### Ingress - HTTP Routing

```yaml
# ═══════════════════════════════════════════════════════════
# INGRESS CONFIGURATION
# ═══════════════════════════════════════════════════════════

apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: app-ingress
  namespace: production
  annotations:
    # Ingress class
    kubernetes.io/ingress.class: nginx

    # SSL/TLS
    cert-manager.io/cluster-issuer: letsencrypt-prod

    # Rewrites
    nginx.ingress.kubernetes.io/rewrite-target: /$2

    # Rate limiting
    nginx.ingress.kubernetes.io/limit-rps: "10"

    # CORS
    nginx.ingress.kubernetes.io/enable-cors: "true"
    nginx.ingress.kubernetes.io/cors-allow-methods: "GET, POST, PUT, DELETE"

    # Timeouts
    nginx.ingress.kubernetes.io/proxy-connect-timeout: "30"
    nginx.ingress.kubernetes.io/proxy-read-timeout: "30"

    # Whitelist
    nginx.ingress.kubernetes.io/whitelist-source-range: "10.0.0.0/8,172.16.0.0/12"

    # Force SSL redirect
    nginx.ingress.kubernetes.io/force-ssl-redirect: "true"

spec:
  # ───────────────────────────────────────────────────────
  # TLS Configuration
  # ───────────────────────────────────────────────────────
  tls:
    - hosts:
        - myapp.example.com
        - api.myapp.example.com
      secretName: myapp-tls-cert

  # ───────────────────────────────────────────────────────
  # Routing Rules
  # ───────────────────────────────────────────────────────
  rules:
    # Frontend
    - host: myapp.example.com
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: frontend-service
                port:
                  number: 80

    # API
    - host: api.myapp.example.com
      http:
        paths:
          - path: /v1
            pathType: Prefix
            backend:
              service:
                name: api-v1-service
                port:
                  number: 80

          - path: /v2
            pathType: Prefix
            backend:
              service:
                name: api-v2-service
                port:
                  number: 80

    # Path-based routing
    - host: myapp.example.com
      http:
        paths:
          - path: /api(/|$)(.*)
            pathType: Prefix
            backend:
              service:
                name: backend-service
                port:
                  number: 80

          - path: /admin(/|$)(.*)
            pathType: Prefix
            backend:
              service:
                name: admin-service
                port:
                  number: 80

---
# ───────────────────────────────────────────────────────
# Install Ingress Controller (Nginx)
# ───────────────────────────────────────────────────────
# kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.9.4/deploy/static/provider/cloud/deploy.yaml
```

---

<div align="center">

## 💾 Storage

_Persistent data in Kubernetes_ 💿

</div>

### Volumes and Storage

```yaml
# ═══════════════════════════════════════════════════════════
# STORAGE HIERARCHY
# ═══════════════════════════════════════════════════════════

# 1. StorageClass (Admin defines storage types)
#        ↓
# 2. PersistentVolume (Admin provisions storage)
#        ↓
# 3. PersistentVolumeClaim (User requests storage)
#        ↓
# 4. Pod (Uses PVC)

# ───────────────────────────────────────────────────────
# StorageClass (Storage Template)
# ───────────────────────────────────────────────────────
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: fast-ssd
provisioner: kubernetes.io/aws-ebs
parameters:
  type: gp3
  iops: "3000"
  throughput: "125"
  encrypted: "true"
volumeBindingMode: WaitForFirstConsumer
allowVolumeExpansion: true
reclaimPolicy: Delete

---
# ───────────────────────────────────────────────────────
# PersistentVolume (Actual Storage)
# ───────────────────────────────────────────────────────
apiVersion: v1
kind: PersistentVolume
metadata:
  name: postgres-pv
spec:
  capacity:
    storage: 10Gi
  accessModes:
    - ReadWriteOnce # RWO, ROX, RWX
  persistentVolumeReclaimPolicy: Retain # Retain, Delete, Recycle
  storageClassName: fast-ssd

  # Cloud provider examples:
  # AWS EBS
  awsElasticBlockStore:
    volumeID: vol-0123456789abcdef
    fsType: ext4

  # OR GCP Persistent Disk
  # gcePersistentDisk:
  #   pdName: my-data-disk
  #   fsType: ext4

  # OR Azure Disk
  # azureDisk:
  #   diskName: my-disk
  #   diskURI: /subscriptions/.../disks/my-disk

  # OR NFS
  # nfs:
  #   server: nfs-server.example.com
  #   path: /exports/data

  # OR Local (node-specific)
  # local:
  #   path: /mnt/disks/ssd1
  # nodeAffinity:
  #   required:
  #     nodeSelectorTerms:
  #     - matchExpressions:
  #       - key: kubernetes.io/hostname
  #         operator: In
  #         values:
  #         - node1

---
# ───────────────────────────────────────────────────────
# PersistentVolumeClaim (Request for Storage)
# ───────────────────────────────────────────────────────
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: postgres-pvc
spec:
  accessModes:
    - ReadWriteOnce
  storageClassName: fast-ssd
  resources:
    requests:
      storage: 10Gi

  # Optional: Select specific PV
  selector:
    matchLabels:
      type: database

---
# ───────────────────────────────────────────────────────
# Using PVC in Pod
# ───────────────────────────────────────────────────────
apiVersion: v1
kind: Pod
metadata:
  name: postgres
spec:
  containers:
    - name: postgres
      image: postgres:15
      volumeMounts:
        - name: postgres-storage
          mountPath: /var/lib/postgresql/data

  volumes:
    - name: postgres-storage
      persistentVolumeClaim:
        claimName: postgres-pvc

---
# ───────────────────────────────────────────────────────
# Volume Types in Pods
# ───────────────────────────────────────────────────────
apiVersion: v1
kind: Pod
metadata:
  name: volume-examples
spec:
  containers:
    - name: app
      image: nginx
      volumeMounts:
        - name: config
          mountPath: /etc/config
        - name: secrets
          mountPath: /etc/secrets
        - name: cache
          mountPath: /cache
        - name: logs
          mountPath: /var/log

  volumes:
    # ConfigMap volume
    - name: config
      configMap:
        name: app-config

    # Secret volume
    - name: secrets
      secret:
        secretName: app-secrets

    # EmptyDir (temporary, pod-lifetime)
    - name: cache
      emptyDir:
        sizeLimit: 1Gi

    # EmptyDir in memory
    - name: logs
      emptyDir:
        medium: Memory
        sizeLimit: 100Mi
```

```bash
# ═══════════════════════════════════════════════════════════
# STORAGE COMMANDS
# ═══════════════════════════════════════════════════════════

# List storage classes
kubectl get storageclass
kubectl get sc

# Describe storage class
kubectl describe sc fast-ssd

# List persistent volumes
kubectl get pv

# Describe PV
kubectl describe pv postgres-pv

# List PVCs
kubectl get pvc
kubectl get pvc -A  # All namespaces

# Describe PVC
kubectl describe pvc postgres-pvc

# Check PVC status
kubectl get pvc postgres-pvc -o jsonpath='{.status.phase}'

# Resize PVC (if allowVolumeExpansion: true)
kubectl patch pvc postgres-pvc -p '{"spec":{"resources":{"requests":{"storage":"20Gi"}}}}'

# Delete PVC
kubectl delete pvc postgres-pvc

# View volume mount in pod
kubectl describe pod postgres | grep -A 5 Volumes
```

---

<div align="center">

## ⚙️ Advanced Workloads

_Beyond Deployments_ 🎮

</div>

### StatefulSets - For Stateful Apps

```yaml
# ═══════════════════════════════════════════════════════════
# STATEFULSET (For databases, queues, etc.)
# ═══════════════════════════════════════════════════════════

apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: postgres
spec:
  serviceName: postgres # Headless service
  replicas: 3
  selector:
    matchLabels:
      app: postgres

  # Pod template
  template:
    metadata:
      labels:
        app: postgres
    spec:
      containers:
        - name: postgres
          image: postgres:15
          ports:
            - containerPort: 5432
              name: postgres
          env:
            - name: POSTGRES_PASSWORD
              valueFrom:
                secretKeyRef:
                  name: postgres-secret
                  key: password
          volumeMounts:
            - name: data
              mountPath: /var/lib/postgresql/data

  # Volume Claim Templates (creates PVC for each pod)
  volumeClaimTemplates:
    - metadata:
        name: data
      spec:
        accessModes: ["ReadWriteOnce"]
        storageClassName: fast-ssd
        resources:
          requests:
            storage: 10Gi

# StatefulSet guarantees:
# ✅ Stable, unique network identifiers
#    postgres-0, postgres-1, postgres-2
# ✅ Stable, persistent storage
#    Each pod gets its own PVC
# ✅ Ordered, graceful deployment and scaling
#    Pods created in order: 0 → 1 → 2
# ✅ Ordered, automated rolling updates
#    Updated in reverse: 2 → 1 → 0

---
# Headless Service (for StatefulSet)
apiVersion: v1
kind: Service
metadata:
  name: postgres
spec:
  clusterIP: None # Headless!
  selector:
    app: postgres
  ports:
    - port: 5432
      name: postgres
# DNS names:
# postgres-0.postgres.default.svc.cluster.local
# postgres-1.postgres.default.svc.cluster.local
# postgres-2.postgres.default.svc.cluster.local
```

---

### DaemonSets - One Pod Per Node

```yaml
# ═══════════════════════════════════════════════════════════
# DAEMONSET (Runs on every node)
# ═══════════════════════════════════════════════════════════

apiVersion: apps/v1
kind: DaemonSet
metadata:
  name: node-exporter
  namespace: monitoring
spec:
  selector:
    matchLabels:
      app: node-exporter

  template:
    metadata:
      labels:
        app: node-exporter
    spec:
      # Run on all nodes including master (optional)
      tolerations:
        - key: node-role.kubernetes.io/control-plane
          effect: NoSchedule

      hostNetwork: true # Use host network
      hostPID: true # See host processes

      containers:
        - name: node-exporter
          image: prom/node-exporter:latest
          ports:
            - containerPort: 9100
              name: metrics
          volumeMounts:
            - name: proc
              mountPath: /host/proc
              readOnly: true
            - name: sys
              mountPath: /host/sys
              readOnly: true

      volumes:
        - name: proc
          hostPath:
            path: /proc
        - name: sys
          hostPath:
            path: /sys
# Use cases:
# ✅ Monitoring agents (Prometheus node exporter)
# ✅ Log collectors (Fluentd, Filebeat)
# ✅ Storage daemons (Ceph, GlusterFS)
# ✅ Network plugins (Calico, Weave)
```

---

### Jobs and CronJobs

```yaml
# ═══════════════════════════════════════════════════════════
# JOB (Run to completion)
# ═══════════════════════════════════════════════════════════

apiVersion: batch/v1
kind: Job
metadata:
  name: database-backup
spec:
  # How many times to retry on failure
  backoffLimit: 3

  # Delete after completion
  ttlSecondsAfterFinished: 100

  # How many pods should complete successfully
  completions: 1

  # How many pods to run in parallel
  parallelism: 1

  # Active deadline
  activeDeadlineSeconds: 600

  template:
    spec:
      restartPolicy: OnFailure # Never or OnFailure

      containers:
        - name: backup
          image: postgres:15
          command:
            - /bin/bash
            - -c
            - |
              pg_dump -h postgres -U user mydb > /backups/backup-$(date +%Y%m%d).sql
          env:
            - name: PGPASSWORD
              valueFrom:
                secretKeyRef:
                  name: postgres-secret
                  key: password
          volumeMounts:
            - name: backups
              mountPath: /backups

      volumes:
        - name: backups
          persistentVolumeClaim:
            claimName: backup-pvc

---
# ═══════════════════════════════════════════════════════════
# CRONJOB (Scheduled Job)
# ═══════════════════════════════════════════════════════════

apiVersion: batch/v1
kind: CronJob
metadata:
  name: database-backup-cron
spec:
  # Schedule (cron format)
  schedule: "0 2 * * *" # Every day at 2 AM

  # How many successful jobs to keep
  successfulJobsHistoryLimit: 3

  # How many failed jobs to keep
  failedJobsHistoryLimit: 1

  # Concurrency policy
  concurrencyPolicy: Forbid # Allow, Forbid, Replace

  # Start deadline
  startingDeadlineSeconds: 300

  # Suspend (pause) cron
  suspend: false

  jobTemplate:
    spec:
      template:
        spec:
          restartPolicy: OnFailure
          containers:
            - name: backup
              image: postgres:15
              command:
                - /bin/bash
                - -c
                - |
                  pg_dump -h postgres -U user mydb > /backups/backup-$(date +%Y%m%d-%H%M%S).sql
              env:
                - name: PGPASSWORD
                  valueFrom:
                    secretKeyRef:
                      name: postgres-secret
                      key: password
# Cron schedule examples:
# "*/5 * * * *"      Every 5 minutes
# "0 * * * *"        Every hour
# "0 0 * * *"        Every day at midnight
# "0 0 * * 0"        Every Sunday at midnight
# "0 0 1 * *"        First day of every month
# "0 2 * * 1-5"      Weekdays at 2 AM
```

```bash
# ═══════════════════════════════════════════════════════════
# JOB & CRONJOB COMMANDS
# ═══════════════════════════════════════════════════════════

# Create job
kubectl create job my-job --image=busybox -- echo "Hello"

# Get jobs
kubectl get jobs

# View job details
kubectl describe job database-backup

# View job logs
kubectl logs job/database-backup

# Delete job
kubectl delete job database-backup

# Get cronjobs
kubectl get cronjobs
kubectl get cj

# Describe cronjob
kubectl describe cronjob database-backup-cron

# Manually trigger cronjob
kubectl create job --from=cronjob/database-backup-cron manual-backup

# Suspend cronjob
kubectl patch cronjob database-backup-cron -p '{"spec":{"suspend":true}}'

# Resume cronjob
kubectl patch cronjob database-backup-cron -p '{"spec":{"suspend":false}}'

# Delete cronjob
kubectl delete cronjob database-backup-cron
```

---

<div align="center">

## 🔐 Security

_Securing your Kubernetes cluster_ 🛡️

</div>

### RBAC (Role-Based Access Control)

```yaml
# ═══════════════════════════════════════════════════════════
# RBAC COMPONENTS
# ═══════════════════════════════════════════════════════════

# 1. ServiceAccount (Identity for pods)
# 2. Role/ClusterRole (Permissions)
# 3. RoleBinding/ClusterRoleBinding (Assign permissions)

# ───────────────────────────────────────────────────────
# ServiceAccount
# ───────────────────────────────────────────────────────
apiVersion: v1
kind: ServiceAccount
metadata:
  name: app-service-account
  namespace: production

---
# ───────────────────────────────────────────────────────
# Role (Namespace-scoped)
# ───────────────────────────────────────────────────────
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  name: pod-reader
  namespace: production
rules:
  - apiGroups: [""] # Core API group
    resources: ["pods"]
    verbs: ["get", "list", "watch"]

  - apiGroups: ["apps"]
    resources: ["deployments"]
    verbs: ["get", "list"]

---
# ───────────────────────────────────────────────────────
# RoleBinding (Binds Role to ServiceAccount)
# ───────────────────────────────────────────────────────
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: read-pods
  namespace: production
subjects:
  - kind: ServiceAccount
    name: app-service-account
    namespace: production
roleRef:
  kind: Role
  name: pod-reader
  apiGroup: rbac.authorization.k8s.io

---
# ───────────────────────────────────────────────────────
# ClusterRole (Cluster-wide)
# ───────────────────────────────────────────────────────
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
  name: secret-reader
rules:
  - apiGroups: [""]
    resources: ["secrets"]
    verbs: ["get", "list"]

---
# ───────────────────────────────────────────────────────
# ClusterRoleBinding
# ───────────────────────────────────────────────────────
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  name: read-secrets-global
subjects:
  - kind: ServiceAccount
    name: app-service-account
    namespace: production
roleRef:
  kind: ClusterRole
  name: secret-reader
  apiGroup: rbac.authorization.k8s.io

---
# ───────────────────────────────────────────────────────
# Using ServiceAccount in Pod
# ───────────────────────────────────────────────────────
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  serviceAccountName: app-service-account
  containers:
    - name: app
      image: myapp:latest
# Common RBAC verbs:
# get, list, watch, create, update, patch, delete, deletecollection
```

---

### Network Policies

```yaml
# ═══════════════════════════════════════════════════════════
# NETWORK POLICIES (Firewall Rules)
# ═══════════════════════════════════════════════════════════

# ───────────────────────────────────────────────────────
# Deny All Ingress (Default Deny)
# ───────────────────────────────────────────────────────
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: default-deny-ingress
  namespace: production
spec:
  podSelector: {} # Applies to all pods
  policyTypes:
    - Ingress

---
# ───────────────────────────────────────────────────────
# Allow Frontend → Backend
# ───────────────────────────────────────────────────────
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-frontend-to-backend
  namespace: production
spec:
  podSelector:
    matchLabels:
      app: backend # Apply to backend pods

  policyTypes:
    - Ingress

  ingress:
    - from:
        - podSelector:
            matchLabels:
              app: frontend # Allow from frontend pods
      ports:
        - protocol: TCP
          port: 3000

---
# ───────────────────────────────────────────────────────
# Allow Backend → Database (Different Namespace)
# ───────────────────────────────────────────────────────
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-backend-to-db
  namespace: database
spec:
  podSelector:
    matchLabels:
      app: postgres

  policyTypes:
    - Ingress

  ingress:
    - from:
        - namespaceSelector:
            matchLabels:
              name: production
          podSelector:
            matchLabels:
              app: backend
      ports:
        - protocol: TCP
          port: 5432

---
# ───────────────────────────────────────────────────────
# Allow External Traffic (Ingress Controller)
# ───────────────────────────────────────────────────────
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-ingress-controller
  namespace: production
spec:
  podSelector:
    matchLabels:
      app: frontend

  policyTypes:
    - Ingress

  ingress:
    - from:
        - namespaceSelector:
            matchLabels:
              name: ingress-nginx
      ports:
        - protocol: TCP
          port: 80

---
# ───────────────────────────────────────────────────────
# Egress Policy (Outbound Traffic)
# ───────────────────────────────────────────────────────
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-dns-egress
  namespace: production
spec:
  podSelector: {}

  policyTypes:
    - Egress

  egress:
    # Allow DNS
    - to:
        - namespaceSelector:
            matchLabels:
              name: kube-system
      ports:
        - protocol: UDP
          port: 53

    # Allow HTTPS to external
    - to:
        - podSelector: {}
      ports:
        - protocol: TCP
          port: 443
```

---

### Pod Security

```yaml
# ═══════════════════════════════════════════════════════════
# POD SECURITY STANDARDS
# ═══════════════════════════════════════════════════════════

# Namespace labels for Pod Security Admission
apiVersion: v1
kind: Namespace
metadata:
  name: production
  labels:
    pod-security.kubernetes.io/enforce: restricted
    pod-security.kubernetes.io/audit: restricted
    pod-security.kubernetes.io/warn: restricted

# Levels:
# - privileged: Unrestricted
# - baseline: Minimally restrictive
# - restricted: Heavily restricted (recommended)

---
# ───────────────────────────────────────────────────────
# Secure Pod Configuration
# ───────────────────────────────────────────────────────
apiVersion: v1
kind: Pod
metadata:
  name: secure-pod
spec:
  securityContext:
    # Pod-level security
    runAsNonRoot: true
    runAsUser: 1000
    runAsGroup: 3000
    fsGroup: 2000
    seccompProfile:
      type: RuntimeDefault

  containers:
    - name: app
      image: myapp:latest

      securityContext:
        # Container-level security
        allowPrivilegeEscalation: false
        readOnlyRootFilesystem: true
        runAsNonRoot: true
        runAsUser: 1000
        capabilities:
          drop:
            - ALL
          add:
            - NET_BIND_SERVICE

      resources:
        limits:
          memory: "256Mi"
          cpu: "500m"
        requests:
          memory: "128Mi"
          cpu: "250m"

      volumeMounts:
        - name: cache
          mountPath: /cache
        - name: tmp
          mountPath: /tmp

  volumes:
    - name: cache
      emptyDir: {}
    - name: tmp
      emptyDir: {}
```

---

```yaml
# ═══════════════════════════════════════════
# ConfigMaps & Secrets COMMANDS
# ═══════════════════════════════════════════

# Create ConfigMap from literal
kubectl create configmap app-config --from-literal=API_URL=https://api.example.com

# Create from file
kubectl create configmap app-config --from-file=config.json

# Create from directory
kubectl create configmap app-config --from-file=configs/

# Create Secret
kubectl create secret generic app-secrets --from-literal=password=secret123

# Create Secret from file
kubectl create secret generic app-secrets --from-file=ssh-privatekey=~/.ssh/id_rsa

# Create TLS Secret
kubectl create secret tls tls-secret --cert=cert.crt --key=cert.key

# View ConfigMap/Secret
kubectl get configmaps
kubectl get secrets
kubectl describe configmap app-config
kubectl describe secret app-secrets

# View Secret data (base64 encoded)
kubectl get secret app-secrets -o jsonpath='{.data.password}' | base64 --decode

# Edit ConfigMap/Secret
kubectl edit configmap app-config
kubectl edit secret app-secrets

# Delete ConfigMap/Secret
kubectl delete configmap app-config
kubectl delete secret app-secrets
```

---

<div align="center">

## 📊 Monitoring & Logging

_Observability for your Kubernetes cluster_ 👁️

</div>

### Monitoring Stack Setup

```yaml
# ═══════════════════════════════════════════
# PROMETHEUS - METRICS COLLECTION
# ═══════════════════════════════════════════

# Install Prometheus using Helm
# helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
# helm repo update
# helm install prometheus prometheus-community/kube-prometheus-stack

# ServiceMonitor (Prometheus Operator CRD)
---
apiVersion: monitoring.coreos.com/v1
kind: ServiceMonitor
metadata:
  name: my-app
  namespace: monitoring
spec:
  selector:
    matchLabels:
      app: my-app
  endpoints:
    - port: metrics
      interval: 30s
      path: /metrics

# ═══════════════════════════════════════════
# GRAFANA - VISUALIZATION
# ═══════════════════════════════════════════

# Access Grafana (after Helm install)
# kubectl port-forward -n monitoring svc/prometheus-grafana 3000:80

# Default credentials: admin / prom-operator

# ═══════════════════════════════════════════
# APPLICATION INSTRUMENTATION
# ═══════════════════════════════════════════

# Example: Node.js app with Prometheus metrics
---
apiVersion: v1
kind: Service
metadata:
  name: nodejs-app
  labels:
    app: nodejs-app
spec:
  ports:
    - name: http
      port: 3000
      targetPort: 3000
    - name: metrics
      port: 9090
      targetPort: 9090
  selector:
    app: nodejs-app

---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nodejs-app
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nodejs-app
  template:
    metadata:
      labels:
        app: nodejs-app
      annotations:
        prometheus.io/scrape: "true"
        prometheus.io/port: "9090"
        prometheus.io/path: "/metrics"
    spec:
      containers:
        - name: app
          image: myapp:latest
          ports:
            - containerPort: 3000
              name: http
            - containerPort: 9090
              name: metrics
```

### Logging Stack

```yaml
# ═══════════════════════════════════════════
# ELK STACK (Elasticsearch, Logstash, Kibana)
# ═══════════════════════════════════════════

# Using EFK (Fluentd instead of Logstash)
# helm repo add elastic https://helm.elastic.co
# helm install elasticsearch elastic/elasticsearch
# helm install kibana elastic/kibana

# Fluentd DaemonSet
---
apiVersion: apps/v1
kind: DaemonSet
metadata:
  name: fluentd
  namespace: kube-system
spec:
  selector:
    matchLabels:
      app: fluentd
  template:
    metadata:
      labels:
        app: fluentd
    spec:
      serviceAccountName: fluentd
      containers:
        - name: fluentd
          image: fluent/fluentd-kubernetes-daemonset:v1-debian-elasticsearch
          env:
            - name: FLUENT_ELASTICSEARCH_HOST
              value: "elasticsearch.default.svc.cluster.local"
            - name: FLUENT_ELASTICSEARCH_PORT
              value: "9200"
          volumeMounts:
            - name: varlog
              mountPath: /var/log
            - name: varlibdockercontainers
              mountPath: /var/lib/docker/containers
              readOnly: true
      volumes:
        - name: varlog
          hostPath:
            path: /var/log
        - name: varlibdockercontainers
          hostPath:
            path: /var/lib/docker/containers

---
# ═══════════════════════════════════════════
# LOKI - LIGHTWEIGHT LOGGING (GRAFANA STACK)
# ═══════════════════════════════════════════

# Install Loki
# helm repo add grafana https://grafana.github.io/helm-charts
# helm install loki grafana/loki-stack

# Promtail DaemonSet (installed with loki-stack)
# Automatically ships logs to Loki

# Query logs in Grafana:
# {namespace="production", app="my-app"}
# {namespace="production"} |= "error"
# rate({namespace="production"}[5m])
```

```bash
# ═══════════════════════════════════════════
# LOGGING COMMANDS
# ═══════════════════════════════════════════

# View pod logs
kubectl logs pod-name

# View logs from specific container
kubectl logs pod-name -c container-name

# Follow logs (real-time)
kubectl logs -f pod-name

# View logs from all pods with label
kubectl logs -l app=my-app

# View previous container logs (if crashed)
kubectl logs pod-name --previous

# View logs with timestamps
kubectl logs pod-name --timestamps

# View last N lines
kubectl logs pod-name --tail=100

# View logs since time
kubectl logs pod-name --since=1h
kubectl logs pod-name --since=2024-01-01T00:00:00Z

# Stream logs from multiple pods
kubectl logs -f -l app=my-app --all-containers=true

# Export logs to file
kubectl logs pod-name > pod.log

# ═══════════════════════════════════════════
# METRICS COMMANDS
# ═══════════════════════════════════════════

# View node metrics (requires metrics-server)
kubectl top nodes

# View pod metrics
kubectl top pods

# View pod metrics in all namespaces
kubectl top pods -A

# View pod metrics with containers
kubectl top pods --containers

# Sort by CPU
kubectl top pods --sort-by=cpu

# Sort by memory
kubectl top pods --sort-by=memory
```

### Popular Monitoring Tools

```yaml
# ═══════════════════════════════════════════
# METRICS SERVER (REQUIRED FOR kubectl top)
# ═══════════════════════════════════════════

# Install metrics-server
# kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml

---
# ═══════════════════════════════════════════
# PROMETHEUS NODE EXPORTER
# ═══════════════════════════════════════════

apiVersion: apps/v1
kind: DaemonSet
metadata:
  name: node-exporter
  namespace: monitoring
spec:
  selector:
    matchLabels:
      app: node-exporter
  template:
    metadata:
      labels:
        app: node-exporter
    spec:
      hostNetwork: true
      hostPID: true
      containers:
        - name: node-exporter
          image: prom/node-exporter:latest
          args:
            - --path.procfs=/host/proc
            - --path.sysfs=/host/sys
            - --collector.filesystem.mount-points-exclude=^/(sys|proc|dev|host|etc)($$|/)
          ports:
            - containerPort: 9100
              name: metrics
          volumeMounts:
            - name: proc
              mountPath: /host/proc
              readOnly: true
            - name: sys
              mountPath: /host/sys
              readOnly: true
      volumes:
        - name: proc
          hostPath:
            path: /proc
        - name: sys
          hostPath:
            path: /sys
```

---

<div align="center">

## 🎛️ Configuration Management

_Managing application configuration_ ⚙️

</div>

### ConfigMaps - Non-Sensitive Config

```yaml
# ═══════════════════════════════════════════
# CONFIGMAP PATTERNS
# ═══════════════════════════════════════════

# ───────────────────────────────────────────────────────
# Pattern 1: Simple Key-Value Pairs
# ───────────────────────────────────────────────────────
apiVersion: v1
kind: ConfigMap
metadata:
  name: app-config
data:
  API_URL: "https://api.production.com"
  LOG_LEVEL: "info"
  MAX_CONNECTIONS: "100"
  FEATURE_FLAG_NEW_UI: "true"

---
# ───────────────────────────────────────────────────────
# Pattern 2: Configuration Files
# ───────────────────────────────────────────────────────
apiVersion: v1
kind: ConfigMap
metadata:
  name: nginx-config
data:
  nginx.conf: |
    server {
      listen 80;
      server_name example.com;

      location / {
        proxy_pass http://backend:3000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
      }
    }

---
# ───────────────────────────────────────────────────────
# Pattern 3: JSON/YAML Configuration
# ───────────────────────────────────────────────────────
apiVersion: v1
kind: ConfigMap
metadata:
  name: app-settings
data:
  settings.json: |
    {
      "database": {
        "host": "postgres.default.svc.cluster.local",
        "port": 5432,
        "name": "myapp"
      },
      "cache": {
        "host": "redis.default.svc.cluster.local",
        "port": 6379
      },
      "features": {
        "newUI": true,
        "betaFeatures": false
      }
    }

---
# ───────────────────────────────────────────────────────
# Using ConfigMap in Pods
# ───────────────────────────────────────────────────────
apiVersion: v1
kind: Pod
metadata:
  name: app-pod
spec:
  containers:
    - name: app
      image: myapp:latest

      # Method 1: Inject all as environment variables
      envFrom:
        - configMapRef:
            name: app-config

      # Method 2: Inject specific keys as environment variables
      env:
        - name: API_URL
          valueFrom:
            configMapKeyRef:
              name: app-config
              key: API_URL

      # Method 3: Mount as volume (file)
      volumeMounts:
        - name: config-volume
          mountPath: /etc/config
          readOnly: true

  volumes:
    - name: config-volume
      configMap:
        name: nginx-config
```

### Secrets - Sensitive Data

```yaml
# ═══════════════════════════════════════════
# SECRET TYPES & USAGE
# ═══════════════════════════════════════════

# ───────────────────────────────────────────────────────
# Generic Secret (Default)
# ───────────────────────────────────────────────────────
apiVersion: v1
kind: Secret
metadata:
  name: app-secrets
type: Opaque
data:
  # Values must be base64 encoded
  username: YWRtaW4= # admin
  password: cGFzc3dvcmQxMjM= # password123

# Alternative: stringData (automatically base64 encoded)
stringData:
  database-url: "postgresql://user:pass@host:5432/db"
  api-key: "sk-1234567890abcdef"

---
# ───────────────────────────────────────────────────────
# Docker Registry Secret
# ───────────────────────────────────────────────────────
apiVersion: v1
kind: Secret
metadata:
  name: docker-registry-secret
type: kubernetes.io/dockerconfigjson
data:
  .dockerconfigjson: <base64-encoded-docker-config>

# Create with kubectl:
# kubectl create secret docker-registry docker-registry-secret \
#   --docker-server=https://index.docker.io/v1/ \
#   --docker-username=myuser \
#   --docker-password=mypassword \
#   --docker-email=myemail@example.com

# Use in Pod:
---
apiVersion: v1
kind: Pod
metadata:
  name: private-image-pod
spec:
  imagePullSecrets:
    - name: docker-registry-secret
  containers:
    - name: app
      image: myregistry.com/private-image:latest

---
# ───────────────────────────────────────────────────────
# TLS Secret
# ───────────────────────────────────────────────────────
apiVersion: v1
kind: Secret
metadata:
  name: tls-secret
type: kubernetes.io/tls
data:
  tls.crt: <base64-encoded-cert>
  tls.key: <base64-encoded-key>

# Create with kubectl:
# kubectl create secret tls tls-secret \
#   --cert=path/to/cert.crt \
#   --key=path/to/cert.key

# Use in Ingress:
---
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: tls-ingress
spec:
  tls:
    - hosts:
        - example.com
      secretName: tls-secret
  rules:
    - host: example.com
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: web-service
                port:
                  number: 80

---
# ───────────────────────────────────────────────────────
# SSH Auth Secret
# ───────────────────────────────────────────────────────
apiVersion: v1
kind: Secret
metadata:
  name: ssh-key-secret
type: kubernetes.io/ssh-auth
data:
  ssh-privatekey: <base64-encoded-private-key>

---
# ───────────────────────────────────────────────────────
# Using Secrets in Pods
# ───────────────────────────────────────────────────────
apiVersion: v1
kind: Pod
metadata:
  name: secret-pod
spec:
  containers:
    - name: app
      image: myapp:latest

      # Method 1: Environment variables from all secrets
      envFrom:
        - secretRef:
            name: app-secrets

      # Method 2: Specific secret keys as env vars
      env:
        - name: DB_PASSWORD
          valueFrom:
            secretKeyRef:
              name: app-secrets
              key: password

      # Method 3: Mount as volume
      volumeMounts:
        - name: secret-volume
          mountPath: /etc/secrets
          readOnly: true

  volumes:
    - name: secret-volume
      secret:
        secretName: app-secrets
        items:
          - key: username
            path: db-username
          - key: password
            path: db-password
```

### External Secrets Management

```yaml
# ═══════════════════════════════════════════
# EXTERNAL SECRETS OPERATOR
# ═══════════════════════════════════════════

# Install:
# helm repo add external-secrets https://charts.external-secrets.io
# helm install external-secrets external-secrets/external-secrets

# ───────────────────────────────────────────────────────
# AWS Secrets Manager Integration
# ───────────────────────────────────────────────────────
apiVersion: external-secrets.io/v1beta1
kind: SecretStore
metadata:
  name: aws-secrets-manager
spec:
  provider:
    aws:
      service: SecretsManager
      region: us-east-1
      auth:
        secretRef:
          accessKeyIDSecretRef:
            name: aws-credentials
            key: access-key-id
          secretAccessKeySecretRef:
            name: aws-credentials
            key: secret-access-key

---
apiVersion: external-secrets.io/v1beta1
kind: ExternalSecret
metadata:
  name: app-secrets
spec:
  refreshInterval: 1h
  secretStoreRef:
    name: aws-secrets-manager
    kind: SecretStore
  target:
    name: app-secrets
    creationPolicy: Owner
  data:
    - secretKey: password
      remoteRef:
        key: prod/database
        property: password

---
# ───────────────────────────────────────────────────────
# HashiCorp Vault Integration
# ───────────────────────────────────────────────────────
apiVersion: external-secrets.io/v1beta1
kind: SecretStore
metadata:
  name: vault-backend
spec:
  provider:
    vault:
      server: "https://vault.example.com"
      path: "secret"
      version: "v2"
      auth:
        kubernetes:
          mountPath: "kubernetes"
          role: "my-app"

---
apiVersion: external-secrets.io/v1beta1
kind: ExternalSecret
metadata:
  name: vault-secrets
spec:
  refreshInterval: 15m
  secretStoreRef:
    name: vault-backend
    kind: SecretStore
  target:
    name: vault-secrets
  data:
    - secretKey: api-key
      remoteRef:
        key: secret/data/myapp
        property: api_key
```

---

<div align="center">

## 📦 Package Management (Helm)

_The package manager for Kubernetes_ ⎈

</div>

### Helm Basics

```bash
# ═══════════════════════════════════════════
# HELM INSTALLATION
# ═══════════════════════════════════════════

# Install Helm
# macOS
brew install helm

# Linux
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash

# Verify installation
helm version

# ═══════════════════════════════════════════
# HELM REPOSITORIES
# ═══════════════════════════════════════════

# Add repository
helm repo add stable https://charts.helm.sh/stable
helm repo add bitnami https://charts.bitnami.com/bitnami

# Update repositories
helm repo update

# Search charts
helm search repo nginx
helm search repo postgres

# List repositories
helm repo list

# Remove repository
helm repo remove stable

# ═══════════════════════════════════════════
# INSTALLING CHARTS
# ═══════════════════════════════════════════

# Install chart
helm install my-release bitnami/nginx

# Install with custom release name
helm install my-nginx bitnami/nginx

# Install in specific namespace
helm install my-nginx bitnami/nginx --namespace production --create-namespace

# Install with custom values
helm install my-nginx bitnami/nginx --set service.type=LoadBalancer

# Install with values file
helm install my-nginx bitnami/nginx -f values.yaml

# Dry run (see what would be installed)
helm install my-nginx bitnami/nginx --dry-run --debug

# ═══════════════════════════════════════════
# MANAGING RELEASES
# ═══════════════════════════════════════════

# List releases
helm list
helm list -A  # All namespaces
helm list -n production

# Get release status
helm status my-nginx

# Get release values
helm get values my-nginx

# Get release manifest
helm get manifest my-nginx

# Get release notes
helm get notes my-nginx

# Upgrade release
helm upgrade my-nginx bitnami/nginx
helm upgrade my-nginx bitnami/nginx -f new-values.yaml

# Upgrade or install
helm upgrade --install my-nginx bitnami/nginx

# Rollback release
helm rollback my-nginx
helm rollback my-nginx 1  # Rollback to revision 1

# View release history
helm history my-nginx

# Uninstall release
helm uninstall my-nginx

# Uninstall and keep history
helm uninstall my-nginx --keep-history
```

### Creating Helm Charts

```bash
# ═══════════════════════════════════════════
# CREATE YOUR OWN HELM CHART
# ═══════════════════════════════════════════

# Create new chart
helm create my-app

# Chart structure:
'''
my-app/
├── Chart.yaml          # Chart metadata
├── values.yaml         # Default values
├── templates/          # Kubernetes manifests
│   ├── deployment.yaml
│   ├── service.yaml
│   ├── ingress.yaml
│   ├── _helpers.tpl   # Template helpers
│   └── NOTES.txt      # Post-install notes
└── charts/            # Dependent charts
'''

# Lint chart
helm lint my-app

# Package chart
helm package my-app

# Install local chart
helm install my-release ./my-app
```

### Example Helm Chart

```yaml
# ═══════════════════════════════════════════
# Chart.yaml
# ═══════════════════════════════════════════
apiVersion: v2
name: my-app
description: A Helm chart for my application
type: application
version: 1.0.0
appVersion: "1.0.0"

dependencies:
  - name: postgresql
    version: 12.x.x
    repository: https://charts.bitnami.com/bitnami
    condition: postgresql.enabled

---
# ═══════════════════════════════════════════
# values.yaml
# ═══════════════════════════════════════════
replicaCount: 3

image:
  repository: myapp
  pullPolicy: IfNotPresent
  tag: "1.0.0"

service:
  type: ClusterIP
  port: 80

ingress:
  enabled: true
  className: nginx
  hosts:
    - host: myapp.example.com
      paths:
        - path: /
          pathType: Prefix
  tls:
    - secretName: myapp-tls
      hosts:
        - myapp.example.com

resources:
  limits:
    cpu: 500m
    memory: 512Mi
  requests:
    cpu: 250m
    memory: 256Mi

autoscaling:
  enabled: true
  minReplicas: 3
  maxReplicas: 10
  targetCPUUtilizationPercentage: 80

postgresql:
  enabled: true
  auth:
    username: myapp
    password: password
    database: myapp

---
# ═══════════════════════════════════════════
# templates/deployment.yaml
# ═══════════════════════════════════════════
apiVersion: apps/v1
kind: Deployment
metadata:
  name: {{ include "my-app.fullname" . }}
  labels:
    {{- include "my-app.labels" . | nindent 4 }}
spec:
  {{- if not .Values.autoscaling.enabled }}
  replicas: {{ .Values.replicaCount }}
  {{- end }}
  selector:
    matchLabels:
      {{- include "my-app.selectorLabels" . | nindent 6 }}
  template:
    metadata:
      labels:
        {{- include "my-app.selectorLabels" . | nindent 8 }}
    spec:
      containers:
        - name: {{ .Chart.Name }}
          image: "{{ .Values.image.repository }}:{{ .Values.image.tag | default .Chart.AppVersion }}"
          imagePullPolicy: {{ .Values.image.pullPolicy }}
          ports:
            - name: http
              containerPort: 3000
              protocol: TCP
          env:
            - name: DATABASE_URL
              value: "postgresql://{{ .Values.postgresql.auth.username }}:{{ .Values.postgresql.auth.password }}@{{ include "my-app.fullname" . }}-postgresql:5432/{{ .Values.postgresql.auth.database }}"
          resources:
            {{- toYaml .Values.resources | nindent 12 }}
```

---

<div align="center">

## 🐛 Troubleshooting

_Debugging Kubernetes like a pro_ 🔍

</div>

### Essential Troubleshooting Commands

```bash
# ═══════════════════════════════════════════
# CLUSTER INFORMATION
# ═══════════════════════════════════════════

# Cluster info
kubectl cluster-info
kubectl cluster-info dump

# View cluster events
kubectl get events
kubectl get events --sort-by='.lastTimestamp'
kubectl get events --field-selector type=Warning

# Check component status
kubectl get componentstatuses
kubectl get cs

# ═══════════════════════════════════════════
# POD DEBUGGING
# ═══════════════════════════════════════════

# Describe pod (most important!)
kubectl describe pod pod-name

# Check pod status
kubectl get pod pod-name -o wide

# View pod YAML
kubectl get pod pod-name -o yaml

# Pod logs
kubectl logs pod-name
kubectl logs pod-name --previous  # Previous instance
kubectl logs pod-name -c container-name  # Specific container
kubectl logs -f pod-name  # Follow logs

# Execute command in pod
kubectl exec -it pod-name -- /bin/bash
kubectl exec -it pod-name -- sh
kubectl exec pod-name -- ls /app
kubectl exec pod-name -- env

# Copy files to/from pod
kubectl cp pod-name:/path/to/file ./local-file
kubectl cp ./local-file pod-name:/path/to/file

# Port forward
kubectl port-forward pod-name 8080:80

# Debug with ephemeral container (K8s 1.23+)
kubectl debug pod-name -it --image=busybox --target=container-name

# ═══════════════════════════════════════════
# NODE DEBUGGING
# ═══════════════════════════════════════════

# List nodes
kubectl get nodes -o wide

# Describe node
kubectl describe node node-name

# View node conditions
kubectl get nodes -o jsonpath='{range .items[*]}{.metadata.name}{"\t"}{.status.conditions[?(@.type=="Ready")].status}{"\n"}{end}'

# Cordon node (mark as unschedulable)
kubectl cordon node-name

# Drain node (evict all pods)
kubectl drain node-name --ignore-daemonsets --delete-emptydir-data

# Uncordon node
kubectl uncordon node-name

# SSH to node (if using SSH)
kubectl node-shell node-name

# ═══════════════════════════════════════════
# SERVICE & NETWORK DEBUGGING
# ═══════════════════════════════════════════

# Check service endpoints
kubectl get endpoints service-name
kubectl describe endpoints service-name

# Test service DNS
kubectl run -it --rm debug --image=busybox --restart=Never -- nslookup service-name

# Test service connectivity
kubectl run -it --rm debug --image=nicolaka/netshoot --restart=Never -- bash
# Inside container:
# curl service-name:port
# dig service-name
# ping service-name

# Check network policies
kubectl get networkpolicies
kubectl describe networkpolicy policy-name

# ═══════════════════════════════════════════
# RESOURCE DEBUGGING
# ═══════════════════════════════════════════

# Check resource quotas
kubectl get resourcequota
kubectl describe resourcequota quota-name

# Check limit ranges
kubectl get limitrange
kubectl describe limitrange limit-name

# Check PVC status
kubectl get pvc
kubectl describe pvc pvc-name

# Check if images can be pulled
kubectl run test --image=myimage:tag --dry-run=client -o yaml

# ═══════════════════════════════════════════
# RBAC DEBUGGING
# ═══════════════════════════════════════════

# Check if user can perform action
kubectl auth can-i create pods
kubectl auth can-i get secrets --as=user@example.com
kubectl auth can-i '*' '*' --all-namespaces

# Check service account permissions
kubectl auth can-i list pods --as=system:serviceaccount:default:my-sa

# View roles and bindings
kubectl get roles,rolebindings
kubectl get clusterroles,clusterrolebindings

# Describe role
kubectl describe role role-name
kubectl describe clusterrole cluster-role-name
```

### Common Issues & Solutions

```bash
# ═══════════════════════════════════════════
# ISSUE: Pod Stuck in Pending
# ═══════════════════════════════════════════

# Check pod events
kubectl describe pod pod-name | grep -A 10 Events

# Common causes:
# 1. Insufficient resources
kubectl top nodes
kubectl describe nodes | grep -A 5 "Allocated resources"

# 2. PVC not bound
kubectl get pvc

# 3. Node selector mismatch
kubectl get nodes --show-labels

# 4. Taints on nodes
kubectl describe nodes | grep Taints

# ═══════════════════════════════════════════
# ISSUE: Pod Stuck in CrashLoopBackOff
# ═══════════════════════════════════════════

# View logs
kubectl logs pod-name
kubectl logs pod-name --previous

# Common causes:
# 1. Application error (check logs)
# 2. Incorrect command/args
kubectl get pod pod-name -o yaml | grep -A 5 command

# 3. Missing dependencies (DB, secrets, etc.)
kubectl describe pod pod-name

# 4. Liveness probe failing too quickly
kubectl get pod pod-name -o yaml | grep -A 10 livenessProbe

# ═══════════════════════════════════════════
# ISSUE: ImagePullBackOff
# ═══════════════════════════════════════════

# Check events
kubectl describe pod pod-name | grep -A 10 Events

# Common causes:
# 1. Image doesn't exist
# 2. Wrong image name/tag
# 3. Private registry without imagePullSecret

# Test image pull manually
kubectl run test --image=problematic-image:tag --dry-run=client

# Check imagePullSecrets
kubectl get secret docker-registry-secret
kubectl describe secret docker-registry-secret

# ═══════════════════════════════════════════
# ISSUE: Service Not Reachable
# ═══════════════════════════════════════════

# Check service exists
kubectl get svc service-name

# Check endpoints
kubectl get endpoints service-name

# If endpoints empty, check:
# 1. Pods are running
kubectl get pods -l app=my-app

# 2. Labels match
kubectl get pods -l app=my-app --show-labels
kubectl get svc service-name -o yaml | grep selector

# 3. Ports are correct
kubectl get svc service-name -o yaml
kubectl get pods pod-name -o yaml | grep containerPort

# Test from another pod
kubectl run debug --image=busybox -it --rm --restart=Never -- wget -O- service-name:port

# ═══════════════════════════════════════════
# ISSUE: DNS Not Working
# ═══════════════════════════════════════════

# Check CoreDNS pods
kubectl get pods -n kube-system -l k8s-app=kube-dns

# Check CoreDNS logs
kubectl logs -n kube-system -l k8s-app=kube-dns

# Test DNS resolution
kubectl run -it --rm debug --image=busybox --restart=Never -- nslookup kubernetes.default

# Check CoreDNS ConfigMap
kubectl get configmap coredns -n kube-system -o yaml

# ═══════════════════════════════════════════
# ISSUE: Persistent Volume Issues
# ═══════════════════════════════════════════

# Check PV/PVC status
kubectl get pv,pvc

# Describe PVC
kubectl describe pvc pvc-name

# Check storage class
kubectl get storageclass

# Check if PV is bound
kubectl get pv pv-name -o yaml

# Check pod mounting the PVC
kubectl describe pod pod-name | grep -A 5 Volumes
```

### Debug Tools Pod

```yaml
# ═══════════════════════════════════════════
# DEBUG TOOLS POD
# ═══════════════════════════════════════════

apiVersion: v1
kind: Pod
metadata:
  name: debug-tools
spec:
  containers:
    - name: debug
      image: nicolaka/netshoot
      command: ["/bin/bash"]
      args: ["-c", "while true; do sleep 30; done"]
      securityContext:
        capabilities:
          add: ["NET_ADMIN"]
# Deploy and use:
# kubectl apply -f debug-pod.yaml
# kubectl exec -it debug-tools -- bash

# Tools available:
# - curl, wget
# - dig, nslookup, host
# - ping, traceroute
# - netstat, ss, ip
# - tcpdump, nmap
# - iperf3, httpie
# - jq, yq
```

---

<div align="center">

## 💡 Best Practices

_Production-ready Kubernetes_ ⭐

</div>

### Resource Management

```yaml
# ═══════════════════════════════════════════
# ALWAYS SET RESOURCE REQUESTS & LIMITS
# ═══════════════════════════════════════════

apiVersion: v1
kind: Pod
metadata:
  name: best-practices-pod
spec:
  containers:
    - name: app
      image: myapp:latest
      resources:
        # Requests: What you need (guaranteed)
        requests:
          memory: "256Mi"
          cpu: "250m" # 250 millicores = 0.25 CPU
        # Limits: Maximum allowed
        limits:
          memory: "512Mi"
          cpu: "500m"

# ✅ DO: Set requests = limits for critical apps (QoS: Guaranteed)
# ✅ DO: Set requests < limits for flexible apps (QoS: Burstable)
# ❌ DON'T: Skip resource limits (QoS: BestEffort)

# ═══════════════════════════════════════════
# USE RESOURCE QUOTAS PER NAMESPACE
# ═══════════════════════════════════════════

---
apiVersion: v1
kind: ResourceQuota
metadata:
  name: production-quota
  namespace: production
spec:
  hard:
    requests.cpu: "100"
    requests.memory: 200Gi
    limits.cpu: "200"
    limits.memory: 400Gi
    pods: "50"
    services: "20"
    persistentvolumeclaims: "10"

# ═══════════════════════════════════════════
# SET LIMIT RANGES
# ═══════════════════════════════════════════

---
apiVersion: v1
kind: LimitRange
metadata:
  name: default-limits
  namespace: production
spec:
  limits:
    - max:
        cpu: "2"
        memory: "4Gi"
      min:
        cpu: "100m"
        memory: "128Mi"
      default:
        cpu: "500m"
        memory: "512Mi"
      defaultRequest:
        cpu: "250m"
        memory: "256Mi"
      type: Container
```

### Health Checks

```yaml
# ═══════════════════════════════════════════
# ALWAYS USE HEALTH CHECKS
# ═══════════════════════════════════════════

apiVersion: apps/v1
kind: Deployment
metadata:
  name: production-app
spec:
  template:
    spec:
      containers:
        - name: app
          image: myapp:latest

          # Liveness: Is the app alive?
          # If fails → Pod restarts
          livenessProbe:
            httpGet:
              path: /health
              port: 3000
            initialDelaySeconds: 30 # Wait before first check
            periodSeconds: 10 # Check every 10s
            timeoutSeconds: 5 # Request timeout
            failureThreshold: 3 # Restart after 3 failures
            successThreshold: 1

          # Readiness: Is the app ready to serve traffic?
          # If fails → Removed from service endpoints
          readinessProbe:
            httpGet:
              path: /ready
              port: 3000
            initialDelaySeconds: 5
            periodSeconds: 5
            timeoutSeconds: 3
            failureThreshold: 3
            successThreshold: 1

          # Startup: For slow-starting apps
          # Disables liveness/readiness until success
          startupProbe:
            httpGet:
              path: /startup
              port: 3000
            initialDelaySeconds: 0
            periodSeconds: 10
            failureThreshold: 30 # 30 * 10s = 5 minutes max startup time

# ✅ DO: Use all three probes for production apps
# ✅ DO: Different endpoints for liveness vs readiness
# ✅ DO: Tune thresholds based on your app
# ❌ DON'T: Use same probe for liveness and readiness
```

### Security Best Practices

```yaml
# ═══════════════════════════════════════════
# SECURE POD CONFIGURATION
# ═══════════════════════════════════════════

apiVersion: v1
kind: Pod
metadata:
  name: secure-pod
spec:
  # ✅ Use non-root user
  securityContext:
    runAsNonRoot: true
    runAsUser: 1000
    runAsGroup: 3000
    fsGroup: 2000
    seccompProfile:
      type: RuntimeDefault

  containers:
    - name: app
      image: myapp:latest

      # ✅ Container-level security
      securityContext:
        allowPrivilegeEscalation: false
        readOnlyRootFilesystem: true
        runAsNonRoot: true
        runAsUser: 1000
        capabilities:
          drop:
            - ALL
          add:
            - NET_BIND_SERVICE # Only if needed

      # ✅ Use specific image tags (never :latest in prod!)
      image: myapp:v1.2.3

      # ✅ Resource limits
      resources:
        limits:
          memory: "512Mi"
          cpu: "500m"
        requests:
          memory: "256Mi"
          cpu: "250m"

# ═══════════════════════════════════════════
# NETWORK POLICY (DEFAULT DENY)
# ═══════════════════════════════════════════

---
# Deny all ingress by default
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: default-deny-ingress
  namespace: production
spec:
  podSelector: {}
  policyTypes:
    - Ingress

---
# Then allow specific traffic
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-frontend-to-backend
  namespace: production
spec:
  podSelector:
    matchLabels:
      app: backend
  policyTypes:
    - Ingress
  ingress:
    - from:
        - podSelector:
            matchLabels:
              app: frontend
      ports:
        - protocol: TCP
          port: 3000
```

### High Availability

```yaml
# ═══════════════════════════════════════════
# HA DEPLOYMENT CONFIGURATION
# ═══════════════════════════════════════════

apiVersion: apps/v1
kind: Deployment
metadata:
  name: ha-app
spec:
  # ✅ Multiple replicas
  replicas: 3

  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxSurge: 1 # 1 extra pod during update
      maxUnavailable: 0 # No downtime!

  selector:
    matchLabels:
      app: ha-app

  template:
    metadata:
      labels:
        app: ha-app
    spec:
      # ✅ Pod anti-affinity (spread across nodes)
      affinity:
        podAntiAffinity:
          preferredDuringSchedulingIgnoredDuringExecution:
            - weight: 100
              podAffinityTerm:
                labelSelector:
                  matchExpressions:
                    - key: app
                      operator: In
                      values:
                        - ha-app
                topologyKey: kubernetes.io/hostname

      # ✅ Pod disruption budget
      # Ensures minimum replicas during disruptions

      containers:
        - name: app
          image: myapp:latest
          resources:
            requests:
              memory: "256Mi"
              cpu: "250m"
            limits:
              memory: "512Mi"
              cpu: "500m"

---
# ═══════════════════════════════════════════
# POD DISRUPTION BUDGET
# ═══════════════════════════════════════════

apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: ha-app-pdb
spec:
  minAvailable: 2 # At least 2 pods must be available
  # OR
  # maxUnavailable: 1  # At most 1 pod can be unavailable
  selector:
    matchLabels:
      app: ha-app
```

### Configuration Management

```yaml
# ✅ DO: Separate config from code
# ✅ DO: Use ConfigMaps for non-sensitive config
# ✅ DO: Use Secrets for sensitive data
# ✅ DO: Version your configs
# ❌ DON'T: Hard-code configuration in images
# ❌ DON'T: Commit secrets to Git

# Example structure:
"'
configs/
├── base/
│   ├── deployment.yaml
│   ├── service.yaml
│   └── kustomization.yaml
├── dev/
│   ├── configmap.yaml
│   ├── kustomization.yaml
│   └── patches/
└── prod/
├── configmap.yaml
├── secrets.yaml (encrypted!)
├── kustomization.yaml
└── patches/
'"
```

### Monitoring & Observability

```yaml
# ✅ DO: Expose metrics endpoint
# ✅ DO: Use structured logging
# ✅ DO: Implement distributed tracing
# ✅ DO: Set up alerts
# ❌ DON'T: Log sensitive data
# ❌ DON'T: Ignore monitoring

# Example: Prometheus metrics
---
apiVersion: v1
kind: Service
metadata:
  name: app-metrics
  labels:
    app: myapp
  annotations:
    prometheus.io/scrape: "true"
    prometheus.io/port: "9090"
    prometheus.io/path: "/metrics"
spec:
  ports:
    - name: metrics
      port: 9090
      targetPort: 9090
  selector:
    app: myapp
```

### Deployment Checklist

```bash
# ═══════════════════════════════════════════
# PRE-DEPLOYMENT CHECKLIST
# ═══════════════════════════════════════════

# ✅ Resource limits set
# ✅ Health checks configured
# ✅ Multiple replicas (if HA needed)
# ✅ Pod disruption budget set
# ✅ Anti-affinity rules (if HA needed)
# ✅ Security context configured
# ✅ Network policies in place
# ✅ ConfigMaps/Secrets created
# ✅ Service account with minimal permissions
# ✅ Monitoring & logging configured
# ✅ Backup strategy in place
# ✅ Rollback plan documented
# ✅ Testing in staging environment
# ✅ Documentation updated

# ═══════════════════════════════════════════
# DEPLOYMENT COMMAND EXAMPLES
# ═══════════════════════════════════════════

# Dry run first
kubectl apply -f deployment.yaml --dry-run=client

# Apply with record (for rollback)
kubectl apply -f deployment.yaml --record

# Watch rollout
kubectl rollout status deployment/myapp

# Pause if issues
kubectl rollout pause deployment/myapp

# Resume after fix
kubectl rollout resume deployment/myapp

# Rollback if needed
kubectl rollout undo deployment/myapp

# Check history
kubectl rollout history deployment/myapp
```

---

<div align="center">

**🎉 Congratulations! You've completed the Kubernetes Guide!**

_Master these concepts, and you'll be orchestrating containers like a Kubernetes ninja!_ ⚡

**Remember:** Start simple, experiment in dev, test in staging, deploy to prod with confidence! 🚀

---

**Built with ⚓ by MrDib for the Kubernetes Community**

_May your pods always be Running and your clusters always be Healthy!_ 🌟

</div>
