<div align="center">

# 🔧 Microservices - Build Distributed Systems! 🔧

![Microservices](https://img.shields.io/badge/Microservices-Architecture-blue?style=for-the-badge)
![Distributed](https://img.shields.io/badge/Distributed-Systems-green?style=for-the-badge)
![Scalable](https://img.shields.io/badge/Scalable-Independent-orange?style=for-the-badge)

### _Break down monoliths into independent services_ 🚀

**Scale, deploy, and evolve services independently!** ✨

</div>

---

## 📚 Table of Contents

- [🎯 What are Microservices](#-what-are-microservices)
- [🏛️ Monolith vs Microservices](#️-monolith-vs-microservices)
- [📐 Microservices Patterns](#-microservices-patterns)
- [🔄 Service Communication](#-service-communication)
- [🗺️ Service Discovery](#️-service-discovery)
- [🚪 API Gateway](#-api-gateway)
- [💾 Data Management](#-data-management)
- [📨 Event-Driven Architecture](#-event-driven-architecture)
- [🚀 Deployment & DevOps](#-deployment--devops)
- [📊 Monitoring & Observability](#-monitoring--observability)
- [🔒 Security](#-security)
- [🔄 Migration Strategies](#-migration-strategies)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 🎯 What are Microservices

</div>

### Understanding Microservices Architecture 🌟

```

# ═══════════════════════════════════════════

# MICROSERVICES EXPLAINED

# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║ WHAT ARE MICROSERVICES?                                    ║
╚════════════════════════════════════════════════════════════╝

Microservices:
─────────────────────────────────────────────────────────────
An architectural style that structures an application as a
collection of small, autonomous services, each running in
its own process and communicating via lightweight mechanisms.

Key Characteristics:
─────────────────────────────────────────────────────────────
✅ Small, focused services
✅ Independent deployment
✅ Own database per service
✅ Decentralized governance
✅ Technology diversity
✅ Fault isolation
✅ Scalable independently
✅ Organized around business capabilities

Example:
─────────────────────────────────────────────────────────────
E-commerce Application:

```

```

┌──────────────┐ ┌──────────────┐ ┌──────────────┐
│ User         │ │   Product    │ │    Order     │
│ Service      │ │   Service    │ │   Service    │
└──────┬───────┘ └──────┬───────┘ └──────┬───────┘
       │                │                │
       ▼                ▼                ▼
    ┌────────┐      ┌────────┐       ┌────────┐
    │User DB │      │Prod DB │       │Order DB│
    └────────┘      └────────┘       └────────┘

┌──────────────┐ ┌──────────────┐ ┌──────────────┐
│ Payment      │ │  Shipping    │ │ Notification │
│ Service      │ │   Service    │ │   Service    │
└──────┬───────┘ └──────┬───────┘ └──────┬───────┘
       │                │                │
       ▼                ▼                ▼
   ┌────────┐      ┌────────┐       ┌────────┐
   │Pay DB  │      │Ship DB │       │Notif DB│
   └────────┘      └────────┘       └────────┘

Each service:
• Independent codebase
• Own database
• Own team
• Deploy independently
• Scale independently

```

```

╔════════════════════════════════════════════════════════════╗
║ MICROSERVICES PRINCIPLES                                   ║
╚════════════════════════════════════════════════════════════╝

1. Single Responsibility:
   ─────────────────────────────────────────────────────────────
   Each service does ONE thing well

Example:
✅ User Service: User management only
✅ Order Service: Orders only
❌ UserOrderPaymentService: Too much!

2. Loose Coupling:
   ─────────────────────────────────────────────────────────────
   Services are independent, minimal dependencies

Changes in Service A don't affect Service B

3. High Cohesion:
   ─────────────────────────────────────────────────────────────
   Related functionality stays together

All user-related operations in User Service

4. Autonomous:
   ─────────────────────────────────────────────────────────────
   Services can be deployed independently

No need to deploy all services for one change

5. Resilient:
   ─────────────────────────────────────────────────────────────
   Failure in one service doesn't crash entire system

Circuit breakers, fallbacks, retries

6. Observable:
   ─────────────────────────────────────────────────────────────
   Comprehensive monitoring and logging

Distributed tracing across services

╔════════════════════════════════════════════════════════════╗
║ BENEFITS OF MICROSERVICES                                  ║
╚════════════════════════════════════════════════════════════╝

Advantages:
─────────────────────────────────────────────────────────────
✅ Independent Deployment
• Deploy one service without touching others
• Faster release cycles
• Reduced risk

✅ Technology Freedom
• Use best tool for each service
• Service A: Node.js
• Service B: Python
• Service C: Go

✅ Team Autonomy
• Teams own their services
• Make decisions independently
• Faster development

✅ Scalability
• Scale services independently
• Scale only what needs scaling
• Optimize resource usage

✅ Fault Isolation
• Service failure doesn't crash system
• Other services continue working
• Better reliability

✅ Easier to Understand
• Small codebase per service
• Focused domain
• Onboarding easier

Challenges:
─────────────────────────────────────────────────────────────
❌ Complexity
• Distributed system challenges
• Network calls can fail
• More moving parts

❌ Data Consistency
• No transactions across services
• Eventual consistency
• Complex to manage

❌ Operational Overhead
• Many services to deploy
• More monitoring needed
• DevOps complexity

❌ Testing Complexity
• Integration testing harder
• End-to-end tests complex
• Mock dependencies

❌ Network Latency
• Service-to-service calls
• Slower than in-process
• Need optimization

╔════════════════════════════════════════════════════════════╗
║ WHEN TO USE MICROSERVICES                                  ║
╚════════════════════════════════════════════════════════════╝

Use Microservices When:
─────────────────────────────────────────────────────────────
✅ Large team (50+ developers)
✅ Complex domain (many bounded contexts)
✅ Need independent scaling
✅ Different technologies per domain
✅ Mature DevOps practices
✅ Can handle distributed system complexity
✅ Need frequent deployments
✅ Product is mature and stable

DON'T Use Microservices When:
─────────────────────────────────────────────────────────────
❌ Small team (< 10 developers)
❌ Simple application
❌ Startup/MVP (uncertain requirements)
❌ No DevOps expertise
❌ Can't handle complexity
❌ Limited resources
❌ Monolith works fine

The Rule:
─────────────────────────────────────────────────────────────
"You must be this tall to use microservices"

- Martin Fowler

Start with Monolith:
• Build fast
• Learn domain
• Identify boundaries
• Migrate to microservices when needed

Microservices are NOT for everyone!

```

---

<div align="center">

## 🏛️ Monolith vs Microservices

</div>

### Understanding the Trade-offs ⚖️

```

# ═══════════════════════════════════════════

# MONOLITH vs MICROSERVICES

# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║ MONOLITHIC ARCHITECTURE                                    ║
╚════════════════════════════════════════════════════════════╝

Monolith:
─────────────────────────────────────────────────────────────
Single codebase, deployed as one unit

```

```

┌────────────────────────────────────────────┐
│ Monolithic Application                     │
│ ┌──────────────────────────────────────┐   │
│ │ UI Layer                             │   │
│ ├──────────────────────────────────────┤   │
│ │ Business Logic                       │   │
│ │ ┌────────────┬───────────────────┐   │   │
│ │ │User Module │ Order Module      │   │   │
│ │ ├────────────┼───────────────────┤   │   │
│ │ │Payment Mod │ Shipping Module   │   │   │
│ │ └────────────┴───────────────────┘   │   │
│ ├──────────────────────────────────────┤   │
│ │ Data Access Layer                    │   │
│ └──────────────────────────────────────┘   │
└─────────────────┬──────────────────────────┘
                  │
                  ▼
           ┌───────────────┐
           │ Database      │
           │ (Single DB)   │
           └───────────────┘

```

```

Monolith Pros:
─────────────────────────────────────────────────────────────
✅ Simple to develop
• One codebase
• Familiar architecture
• Easy to understand

✅ Easy to test
• End-to-end tests simple
• No network calls to mock
• Single deployment

✅ Easy to deploy
• One deployment unit
• Simple CI/CD
• Single version

✅ Better performance
• No network overhead
• In-process calls
• Shared memory

✅ Easier debugging
• Single log file
• Simple stack traces
• Easy to trace execution

✅ ACID transactions
• Database transactions work
• Data consistency easy
• No distributed transactions

Monolith Cons:
─────────────────────────────────────────────────────────────
❌ Hard to scale
• Must scale entire app
• Can't scale components independently
• Inefficient resource usage

❌ Slow deployments
• Deploy everything for small change
• Long build times
• High risk deployments

❌ Technology lock-in
• Stuck with one stack
• Hard to adopt new tech
• Legacy code builds up

❌ Single point of failure
• One bug can crash everything
• No fault isolation
• High blast radius

❌ Large codebase
• Hard to understand (as it grows)
• Slow to onboard
• Merge conflicts

╔════════════════════════════════════════════════════════════╗
║ MICROSERVICES ARCHITECTURE ║
╚════════════════════════════════════════════════════════════╝

Microservices:
─────────────────────────────────────────────────────────────
Multiple independent services

```

```

┌───────────┐ ┌───────────┐ ┌───────────┐
│  User     │ │   Order   │ │  Payment  │
│ Service   │ │  Service  │ │  Service  │
│           │ │           │ │           │
│  Node.js  │ │  Python   │ │    Go     │
└─────┬─────┘ └─────┬─────┘ └─────┬─────┘
      │             │             │
      ▼             ▼             ▼
  ┌────────┐    ┌────────┐    ┌────────┐
  │User DB │    │Order DB│    │ Pay DB │
  │MongoDB │    │Postgres│    │ MySQL   │
  └────────┘    └────────┘    └────────┘

┌───────────┐ ┌───────────┐ ┌───────────┐
│  Shipping │ │ Inventory │ │   Email   │
│  Service  │ │  Service  │ │  Service  │
│           │ │           │ │           │
│    Java   │ │   Rust    │ │  Node.js  │
└─────┬─────┘ └─────┬─────┘ └─────┬─────┘
      │             │             │
      ▼             ▼             ▼
  ┌────────┐    ┌────────┐    ┌────────┐
  │Ship DB │    │Invnt DB│    │Email Q │
  └────────┘    └────────┘    └────────┘

```

```

Microservices Pros:
─────────────────────────────────────────────────────────────
✅ Independent scaling
• Scale what needs scaling
• Optimize resources
• Cost-effective

✅ Technology diversity
• Best tool for each job
• Experiment with new tech
• No lock-in

✅ Team autonomy
• Teams own services
• Independent decisions
• Parallel development

✅ Fast deployment
• Deploy one service
• Reduced risk
• Faster iterations

✅ Fault isolation
• Service failure contained
• System stays up
• Better resilience

✅ Small codebase
• Easy to understand
• Fast to build
• Easy to replace

Microservices Cons:
─────────────────────────────────────────────────────────────
❌ Distributed complexity
• Network failures
• Latency issues
• Debugging harder

❌ Data consistency
• No ACID transactions
• Eventual consistency
• Complex to manage

❌ Testing complexity
• Integration tests hard
• Need service mocks
• E2E tests complex

❌ Operational overhead
• Many deployments
• More monitoring
• DevOps heavy

❌ Network overhead
• Service calls slower
• Latency accumulates
• Need optimization

╔════════════════════════════════════════════════════════════╗
║ COMPARISON TABLE ║
╚════════════════════════════════════════════════════════════╝

```

| Aspect                          | Monolith          | Microservices        |
| ------------------------------- | ----------------- | -------------------- |
| **Complexity**                  | ⭐ Simple         | ⭐⭐⭐⭐⭐ Complex   |
| **Development Speed (Initial)** | ⭐⭐⭐⭐⭐ Fast   | ⭐⭐ Slow            |
| **Development Speed (Mature)**  | ⭐⭐ Slow         | ⭐⭐⭐⭐ Fast        |
| **Deployment**                  | ⭐⭐⭐⭐⭐ Simple | ⭐⭐ Complex         |
| **Scalability**                 | ⭐⭐ Limited      | ⭐⭐⭐⭐⭐ Excellent |
| **Team Size**                   | < 10 devs         | 50+ devs             |
| **Technology Freedom**          | ❌ No             | ✅ Yes               |
| **Performance**                 | ⭐⭐⭐⭐⭐ Fast   | ⭐⭐⭐ Good          |
| **Testing**                     | ⭐⭐⭐⭐⭐ Easy   | ⭐⭐ Hard            |
| **Debugging**                   | ⭐⭐⭐⭐⭐ Easy   | ⭐⭐ Hard            |
| **Data Consistency**            | ⭐⭐⭐⭐⭐ Easy   | ⭐⭐ Hard            |
| **Fault Isolation**             | ⭐ Poor           | ⭐⭐⭐⭐ Fast        |
| **DevOps Requirements**         | ⭐⭐ Low          | ⭐⭐⭐⭐⭐ High      |
| **Cost (Small Scale)**          | ⭐⭐⭐⭐⭐ Low    | ⭐⭐ High            |
| **Cost (Large Scale)**          | ⭐⭐ High         | ⭐⭐⭐⭐ Optimized   |

```

╔════════════════════════════════════════════════════════════╗
║ EVOLUTION PATH ║
╚════════════════════════════════════════════════════════════╝

The Journey:
─────────────────────────────────────────────────────────────

Phase 1: Startup (0-10 users)
┌──────────────┐
│ Monolith │ ← Start here!
└──────────────┘
Simple, fast to build

Phase 2: Growing (100-10K users)
┌──────────────┐
│ Modular │ ← Better monolith
│ Monolith │ Clear boundaries
└──────────────┘

Phase 3: Scaling (10K-100K users)
┌────────┬────────┬────────┐
│Service │Service │Service │ ← Selective extraction
│ A │ B │Monolith│ Critical services out
└────────┴────────┴────────┘

Phase 4: Large Scale (100K+ users)
┌────┬────┬────┬────┬────┐
│Svc │Svc │Svc │Svc │Svc │ ← Full microservices
│ A │ B │ C │ D │ E │
└────┴────┴────┴────┴────┘

Don't skip phases!

```

---

<div align="center">

## 📐 Microservices Patterns

</div>

### Common Design Patterns 🎨

```

# ═══════════════════════════════════════════

# MICROSERVICES PATTERNS

# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║ DATABASE PER SERVICE ║
╚════════════════════════════════════════════════════════════╝

Pattern:
─────────────────────────────────────────────────────────────
Each service owns its data, no sharing

```

```

✅ Correct:
┌──────────┐ ┌──────────┐ ┌──────────┐
│ User │ │ Order │ │ Payment │
│ Service │ │ Service │ │ Service │
└────┬─────┘ └────┬─────┘ └────┬─────┘
│ │ │
▼ ▼ ▼
┌────────┐ ┌────────┐ ┌────────┐
│User DB │ │Order DB│ │ Pay DB │
└────────┘ └────────┘ └────────┘

Each service has its own database

❌ Incorrect:
┌──────────┐ ┌──────────┐ ┌──────────┐
│ User │ │ Order │ │ Payment │
│ Service │ │ Service │ │ Service │
└────┬─────┘ └────┬─────┘ └────┬─────┘
│ │ │
└─────────────────┼─────────────────┘
▼
┌────────────┐
│ Shared DB │ ← DON'T DO THIS!
└────────────┘

```

```

Benefits:
✅ Service autonomy
✅ Independent scaling
✅ Technology choice per service
✅ Loose coupling

Challenges:
❌ Data duplication
❌ No joins across services
❌ Consistency challenges

╔════════════════════════════════════════════════════════════╗
║ SAGA PATTERN ║
╚════════════════════════════════════════════════════════════╝

Pattern:
─────────────────────────────────────────────────────────────
Distributed transactions across services

Problem:
User places order → Need to:

1. Create order
2. Charge payment
3. Update inventory
4. Send notification

All must succeed or all must rollback!

Solution: Saga (sequence of local transactions)

```

```

Choreography-Based Saga:
─────────────────────────────────────────────────────────────

┌──────┐ Order ┌──────┐ Payment ┌──────┐
│Order │─Created──→ │Payment│──Success─→│Invent│
│ │ │ │ │ │
│ │←─Failed── │ │←─Failed─ │ │
└──────┘ └──────┘ └──────┘

Each service emits events
Other services react

Pros: ✅ Loose coupling
Cons: ❌ Hard to understand flow

Orchestration-Based Saga:
─────────────────────────────────────────────────────────────

        ┌──────────────┐
        │ Saga Manager │  ← Central orchestrator
        └───────┬──────┘
                │
    ┌───────────┼───────────┐
    ▼           ▼           ▼

┌──────┐ ┌──────┐ ┌──────┐
│Order │ │Payment│ │Invent│
└──────┘ └──────┘ └──────┘

Saga Manager coordinates all steps

Pros: ✅ Clear flow, easier to understand
Cons: ❌ Central point of control

Compensation (Rollback):
─────────────────────────────────────────────────────────────
If step fails, undo previous steps

1. Create Order ✅
2. Charge Payment ✅
3. Update Inventory ❌ Failed!
4. Refund Payment (compensation)
5. Cancel Order (compensation)

```

```

╔════════════════════════════════════════════════════════════╗
║ CQRS PATTERN ║
╚════════════════════════════════════════════════════════════╝

Pattern:
─────────────────────────────────────────────────────────────
Command Query Responsibility Segregation
Separate read and write models

```

```

┌────────────────────────────────────────────┐
│ Application │
└────────┬──────────────────────┬────────────┘
│ │
Commands Queries
(Write) (Read)
│ │
▼ ▼
┌─────────────────┐ ┌─────────────────┐
│ Write Model │ │ Read Model │
│ (Normalized) │───▶│ (Denormalized) │
│ │ │ (Views) │
└────────┬────────┘ └─────────────────┘
│
▼
┌─────────┐
│Write DB │
└─────────┘

Sync via events → Read DB

Benefits:
✅ Optimize reads and writes separately
✅ Scale independently
✅ Different models for different needs

Use When:
• Complex business logic
• High read/write ratio difference
• Need different data models

```

```

╔════════════════════════════════════════════════════════════╗
║ STRANGLER FIG PATTERN ║
╚════════════════════════════════════════════════════════════╝

Pattern:
─────────────────────────────────────────────────────────────
Gradually migrate from monolith to microservices

```

```

Phase 1: Start
┌─────────────────────────┐
│ Monolith │
│ - Users │
│ - Orders │
│ - Products │
│ - Payments │
└─────────────────────────┘

Phase 2: Extract One Service
┌────────────┐ ┌─────────────────┐
│ User │ │ Monolith │
│ Service │ │ - Orders │
└────────────┘ │ - Products │
│ - Payments │
└─────────────────┘

Phase 3: Extract More
┌────────┐ ┌────────┐ ┌─────────────┐
│ User │ │ Order │ │ Monolith │
│Service │ │Service │ │ - Products │
└────────┘ └────────┘ │ - Payments │
└─────────────┘

Phase 4: Complete
┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐
│ User │ │ Order │ │Product │ │Payment │
│Service │ │Service │ │Service │ │Service │
└────────┘ └────────┘ └────────┘ └────────┘

Gradually replace functionality
Like strangler fig plant!

```

```

╔════════════════════════════════════════════════════════════╗
║ CIRCUIT BREAKER PATTERN                                    ║
╚════════════════════════════════════════════════════════════╝

Pattern:
─────────────────────────────────────────────────────────────
Prevent cascading failures

```

```

States:
┌────────┐
│ Closed │ ← Normal operation
└───┬────┘
│ Failures exceed threshold
▼
┌────────┐
│ Open │ ← Stop calling, return error immediately
└───┬────┘
│ After timeout
▼
┌────────┐
│Half- │ ← Try one request
│ Open │
└───┬────┘
│ Success → Closed
│ Failure → Open

Example:
Service A calls Service B
Service B is down
Circuit breaker opens
Service A gets immediate failure (no waiting)
Prevents resource exhaustion

```

```

Implementation:

```

```javascript
class CircuitBreaker {
  constructor(threshold = 5, timeout = 60000) {
    this.failureThreshold = threshold;
    this.timeout = timeout;
    this.failures = 0;
    this.state = "CLOSED";
    this.nextAttempt = Date.now();
  }

  async call(fn) {
    if (this.state === "OPEN") {
      if (Date.now() < this.nextAttempt) {
        throw new Error("Circuit breaker is OPEN");
      }
      this.state = "HALF_OPEN";
    }

    try {
      const result = await fn();
      this.onSuccess();
      return result;
    } catch (error) {
      this.onFailure();
      throw error;
    }
  }

  onSuccess() {
    this.failures = 0;
    this.state = "CLOSED";
  }

  onFailure() {
    this.failures++;
    if (this.failures >= this.failureThreshold) {
      this.state = "OPEN";
      this.nextAttempt = Date.now() + this.timeout;
    }
  }
}

// Usage
const breaker = new CircuitBreaker();

async function callService() {
  return breaker.call(async () => {
    return await fetch("http://service-b/api");
  });
}
```

---

<div align="center">

## 🔄 Service Communication

</div>

### How Services Talk to Each Other 💬

```
# ═══════════════════════════════════════════
# SERVICE COMMUNICATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SYNCHRONOUS vs ASYNCHRONOUS              ║
╚════════════════════════════════════════════════════════════╝

Synchronous (Request-Response):
─────────────────────────────────────────────────────────────
Caller waits for response

```

```
Service A ──Request──▶ Service B
          ◀─Response──

Service A is blocked until response

Examples: REST, gRPC

Pros:
✅ Simple to understand
✅ Immediate response
✅ Easy to debug

Cons:
❌ Tight coupling
❌ Service B must be available
❌ Cascading failures
❌ Latency accumulates

Asynchronous (Event-Driven):
─────────────────────────────────────────────────────────────
Fire and forget

```

```
Service A ──Event──▶ Message Queue ──▶ Service B
          (returns immediately)

Service A doesn't wait

Examples: Message Queues, Event Bus

Pros:
✅ Loose coupling
✅ No waiting
✅ Better fault tolerance
✅ Can handle bursts

Cons:
❌ Complex to debug
❌ Eventual consistency
❌ More infrastructure needed
```

```
╔════════════════════════════════════════════════════════════╗
║                   REST API                                 ║
╚════════════════════════════════════════════════════════════╝

Most Common:
─────────────────────────────────────────────────────────────
HTTP-based communication

```

```
Service A                    Service B
    │                            │
    │   GET /users/123           │
    ├───────────────────────────▶│
    │                            │
    │   200 OK                   │
    │   {user data}              │
    │◀───────────────────────────┤
```

```
Example:
```

```javascript
// Service A calls Service B
async function getUser(userId) {
  const response = await fetch(`http://user-service/api/users/${userId}`);
  const user = await response.json();
  return user;
}

// Service B endpoint
app.get("/api/users/:id", async (req, res) => {
  const user = await db.findUser(req.params.id);
  res.json(user);
});
```

```
Best Practices:
─────────────────────────────────────────────────────────────
✅ Use versioning (/api/v1/users)
✅ Consistent naming
✅ Proper HTTP methods (GET, POST, PUT, DELETE)
✅ Meaningful status codes
✅ Pagination for lists
✅ Error handling
✅ Rate limiting
✅ Authentication

Pros:
✅ Simple, well-understood
✅ Human-readable
✅ Easy to debug (browser, Postman)
✅ Language-agnostic

Cons:
❌ Text-based (larger payload)
❌ Slower than binary protocols
❌ No contract enforcement

╔════════════════════════════════════════════════════════════╗
║                   gRPC                                     ║
╚════════════════════════════════════════════════════════════╝

Modern Alternative:
─────────────────────────────────────────────────────────────
Binary protocol, high performance

```

```
Service A                    Service B
    │                            │
    │   GetUser(id: 123)         │
    ├───────────────────────────▶│
    │   (binary protobuf)        │
    │                            │
    │   User{...}                │
    │◀───────────────────────────┤
    │   (binary)                 │
```

```
Define Contract (Protocol Buffers):
```

```protobuf
syntax = "proto3";

service UserService {
  rpc GetUser (UserId) returns (User);
  rpc CreateUser (UserRequest) returns (User);
}

message UserId {
  int32 id = 1;
}

message User {
  int32 id = 1;
  string name = 2;
  string email = 3;
}
```

```
Implementation:
```

```javascript
// Service B (Server)
const grpc = require("@grpc/grpc-js");
const protoLoader = require("@grpc/proto-loader");

const packageDefinition = protoLoader.loadSync("user.proto");
const proto = grpc.loadPackageDefinition(packageDefinition);

function getUser(call, callback) {
  const userId = call.request.id;
  const user = db.findUser(userId);
  callback(null, user);
}

const server = new grpc.Server();
server.addService(proto.UserService.service, { getUser });
server.bindAsync("0.0.0.0:50051", grpc.ServerCredentials.createInsecure());

// Service A (Client)
const client = new proto.UserService(
  "user-service:50051",
  grpc.credentials.createInsecure()
);

client.getUser({ id: 123 }, (error, user) => {
  console.log(user);
});
```

```
Pros:
✅ Fast (binary, smaller payload)
✅ Strong typing (contract)
✅ Code generation
✅ Streaming support
✅ Better for service-to-service

Cons:
❌ Not human-readable
❌ Harder to debug
❌ Need code generation
❌ Limited browser support

When to Use:
─────────────────────────────────────────────────────────────
REST: Client-facing APIs, public APIs
gRPC: Internal service-to-service communication

╔════════════════════════════════════════════════════════════╗
║                   MESSAGE QUEUES                           ║
╚════════════════════════════════════════════════════════════╝

Asynchronous Communication:
─────────────────────────────────────────────────────────────

```

```
Service A ──▶ [Queue] ──▶ Service B
(Producer)              (Consumer)

Service A sends message and continues
Service B processes when ready
```

```
Example (RabbitMQ):
```

```javascript
// Service A (Producer)
const amqp = require("amqplib");

async function sendOrder(order) {
  const connection = await amqp.connect("amqp://rabbitmq");
  const channel = await connection.createChannel();
  const queue = "orders";

  await channel.assertQueue(queue);
  channel.sendToQueue(queue, Buffer.from(JSON.stringify(order)));

  console.log("Order sent");
  await channel.close();
  await connection.close();
}

// Service B (Consumer)
async function processOrders() {
  const connection = await amqp.connect("amqp://rabbitmq");
  const channel = await connection.createChannel();
  const queue = "orders";

  await channel.assertQueue(queue);

  channel.consume(queue, (msg) => {
    const order = JSON.parse(msg.content.toString());
    console.log("Processing order:", order);

    // Process order...

    channel.ack(msg);
  });
}
```

```
Benefits:
─────────────────────────────────────────────────────────────
✅ Loose coupling
✅ Async processing
✅ Load balancing (multiple consumers)
✅ Retry mechanism
✅ Order guarantee
✅ Buffering (handle spikes)

Patterns:
─────────────────────────────────────────────────────────────

1. Work Queue:
   One message → One consumer

2. Pub/Sub:
   One message → All subscribers

3. Topic Exchange:
   Route by topic pattern

Popular Tools:
─────────────────────────────────────────────────────────────
• RabbitMQ (most popular)
• Apache Kafka (high-throughput)
• AWS SQS
• Google Cloud Pub/Sub
• Redis (simple)
```

---

<div align="center">

## 🗺️ Service Discovery

</div>

### Find Services Dynamically 🔍

```
# ═══════════════════════════════════════════
# SERVICE DISCOVERY
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   THE PROBLEM                              ║
╚════════════════════════════════════════════════════════════╝

Challenge:
─────────────────────────────────────────────────────────────
How does Service A know where Service B is?

```

```
❌ Hard-coded addresses:
const userServiceUrl = 'http://192.168.1.10:3000';

Problems:
• IP changes when service restarts
• Multiple instances? Which one to call?
• Manual configuration
• No health checking
```

```
Solution: Service Discovery
─────────────────────────────────────────────────────────────

```

```
┌──────────┐
│Service A │
└────┬─────┘
     │ "Where is User Service?"
     ▼
┌─────────────────┐
│Service Registry │  ← Central directory
└────┬────────────┘
     │ "User Service at 10.0.1.5:3000"
     ▼
┌──────────┐
│Service A │ ──calls──▶ User Service (10.0.1.5:3000)
└──────────┘
```

```
╔════════════════════════════════════════════════════════════╗
║                   CLIENT-SIDE DISCOVERY                    ║
╚════════════════════════════════════════════════════════════╝

Pattern:
─────────────────────────────────────────────────────────────
Client queries registry and picks instance

```

```
┌──────────┐
│Service A │
└────┬─────┘
     │ 1. Query registry
     ▼
┌─────────────────┐
│Service Registry │
└────┬────────────┘
     │ 2. Returns list of instances
     ▼
┌──────────┐    3. Pick one    ┌──────────┐
│Service A │──────────────────▶│Service B │
└──────────┘                   │Instance 1│
                               └──────────┘

Pros: ✅ Client controls load balancing
Cons: ❌ Client more complex

Tools: Eureka, Consul
```

```
╔════════════════════════════════════════════════════════════╗
║                   SERVER-SIDE DISCOVERY                    ║
╚════════════════════════════════════════════════════════════╝

Pattern:
─────────────────────────────────────────────────────────────
Load balancer queries registry

```

```
┌──────────┐
│Service A │
└────┬─────┘
     │ 1. Call via load balancer
     ▼
┌──────────────┐    2. Query    ┌─────────────────┐
│Load Balancer │───────────────▶│Service Registry │
└──────┬───────┘                └─────────────────┘
       │ 3. Route to instance
       ▼
   ┌──────────┐
   │Service B │
   │Instance 1│
   └──────────┘

Pros: ✅ Client simple
Cons: ❌ Another moving part

Tools: Kubernetes, AWS ELB
```

```
╔════════════════════════════════════════════════════════════╗
║                   IMPLEMENTATION EXAMPLE                   ║
╚════════════════════════════════════════════════════════════╝

Using Consul:
```

```javascript
const Consul = require("consul");
const consul = new Consul();

// Service Registration
async function registerService() {
  await consul.agent.service.register({
    name: "user-service",
    address: "10.0.1.5",
    port: 3000,
    check: {
      http: "http://10.0.1.5:3000/health",
      interval: "10s",
    },
  });
}

// Service Discovery
async function callUserService() {
  // 1. Discover service
  const result = await consul.health.service("user-service");
  const instances = result[0];

  // 2. Pick healthy instance (load balance)
  const instance = instances[Math.floor(Math.random() * instances.length)];
  const url = `http://${instance.Service.Address}:${instance.Service.Port}`;

  // 3. Call service
  const response = await fetch(`${url}/api/users/123`);
  return response.json();
}
```

```
Health Checking:
─────────────────────────────────────────────────────────────
Registry pings services periodically

```

```
┌──────────┐    Ping     ┌──────────┐
│ Registry │────────────▶│Service A │
└──────────┘◀────────────└──────────┘
           Healthy/Unhealthy

Unhealthy services removed from registry
```

```
Popular Tools:
─────────────────────────────────────────────────────────────
• Consul (HashiCorp) - Full-featured
• Eureka (Netflix) - Java ecosystem
• etcd (CoreOS) - Simple key-value
• ZooKeeper (Apache) - Mature
• Kubernetes DNS - Built-in for K8s
```

---

<div align="center">

## 🚪 API Gateway

</div>

### Single Entry Point 🚀

```
# ═══════════════════════════════════════════
# API GATEWAY PATTERN
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WHAT IS API GATEWAY?                     ║
╚════════════════════════════════════════════════════════════╝

API Gateway:
─────────────────────────────────────────────────────────────
Single entry point for all client requests

```

```
Without Gateway:                 With Gateway:
┌────────┐                       ┌────────┐
│ Client │                       │ Client │
└───┬────┘                       └───┬────┘
    │                                │
    ├──▶ User Service               ▼
    ├──▶ Order Service          ┌──────────────┐
    ├──▶ Payment Service        │ API Gateway  │
    └──▶ Product Service        └──────┬───────┘
                                       │
    Problems:                      ┌───┴───┬───────┬──────┐
    • Multiple endpoints           ▼       ▼       ▼      ▼
    • Auth in each service     ┌─────┐ ┌─────┐ ┌─────┐ ┌─────┐
    • CORS issues              │User │ │Order│ │Pay  │ │Prod │
    • Different protocols      └─────┘ └─────┘ └─────┘ └─────┘
```

```
╔════════════════════════════════════════════════════════════╗
║                   API GATEWAY RESPONSIBILITIES             ║
╚════════════════════════════════════════════════════════════╝

Responsibilities:
─────────────────────────────────────────────────────────────

1. Request Routing:
   Route to appropriate service

2. Authentication & Authorization:
   Verify JWT, API keys

3. Rate Limiting:
   Prevent abuse

4. Load Balancing:
   Distribute requests

5. Caching:
   Cache responses

6. Request/Response Transformation:
   Modify requests, aggregate responses

7. Protocol Translation:
   HTTP → gRPC, WebSocket → HTTP

8. Logging & Monitoring:
   Centralized logging

9. Circuit Breaking:
   Prevent cascading failures

10. API Versioning:
    Handle multiple API versions

╔════════════════════════════════════════════════════════════╗
║                   PATTERNS                                 ║
╚════════════════════════════════════════════════════════════╝

1. Simple Routing:
─────────────────────────────────────────────────────────────
```

```
GET /users/*     → User Service
GET /orders/*    → Order Service
GET /products/*  → Product Service
```

```
2. Aggregation (BFF - Backend for Frontend):
─────────────────────────────────────────────────────────────
```

```
Mobile Client:
GET /mobile/home
  → Gateway calls:
     • User Service (get user)
     • Order Service (recent orders)
     • Product Service (recommendations)
  → Gateway aggregates
  → Returns single response

Saves multiple round trips!
```

```
3. Protocol Translation:
─────────────────────────────────────────────────────────────
```

```
Client (HTTP/REST) → Gateway → Service (gRPC)
```

```
Implementation Example:
```

```javascript
// Express-based API Gateway
const express = require("express");
const { createProxyMiddleware } = require("http-proxy-middleware");
const jwt = require("jsonwebtoken");

const app = express();

// Authentication Middleware
function authenticate(req, res, next) {
  const token = req.headers.authorization?.split(" ")[1];

  try {
    const decoded = jwt.verify(token, process.env.JWT_SECRET);
    req.user = decoded;
    next();
  } catch (error) {
    res.status(401).json({ error: "Unauthorized" });
  }
}

// Rate Limiting
const rateLimit = require("express-rate-limit");
const limiter = rateLimit({
  windowMs: 15 * 60 * 1000, // 15 minutes
  max: 100, // limit each IP to 100 requests per windowMs
});

app.use(limiter);

// Routing
app.use(
  "/api/users",
  authenticate,
  createProxyMiddleware({
    target: "http://user-service:3000",
    changeOrigin: true,
    pathRewrite: { "^/api/users": "/users" },
  })
);

app.use(
  "/api/orders",
  authenticate,
  createProxyMiddleware({
    target: "http://order-service:3001",
    changeOrigin: true,
    pathRewrite: { "^/api/orders": "/orders" },
  })
);

app.use(
  "/api/products",
  createProxyMiddleware({
    target: "http://product-service:3002",
    changeOrigin: true,
  })
);

// Aggregation endpoint
app.get("/api/dashboard", authenticate, async (req, res) => {
  try {
    const [user, orders, recommendations] = await Promise.all([
      fetch(`http://user-service:3000/users/${req.user.id}`),
      fetch(`http://order-service:3001/orders/recent?userId=${req.user.id}`),
      fetch(
        `http://product-service:3002/recommendations?userId=${req.user.id}`
      ),
    ]);

    res.json({
      user: await user.json(),
      recentOrders: await orders.json(),
      recommendations: await recommendations.json(),
    });
  } catch (error) {
    res.status(500).json({ error: "Failed to fetch dashboard" });
  }
});

app.listen(8000);
```

```
Popular API Gateways:
─────────────────────────────────────────────────────────────
• Kong (most popular, open-source)
• AWS API Gateway
• Azure API Management
• Google Cloud Endpoints
• Nginx
• Traefik
• Envoy
• Apache APISIX

Best Practices:
─────────────────────────────────────────────────────────────
✅ Keep gateway thin (routing, auth, rate limiting)
✅ Don't put business logic in gateway
✅ Cache at gateway level
✅ Monitor gateway performance
✅ Make gateway redundant (multiple instances)
❌ Don't make gateway a bottleneck
```

---

<div align="center">

## 💾 Data Management

</div>

### Handle Data in Distributed Systems 🗄️

```
# ═══════════════════════════════════════════
# DATA MANAGEMENT IN MICROSERVICES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   DATABASE PER SERVICE                     ║
╚════════════════════════════════════════════════════════════╝

Core Principle:
─────────────────────────────────────────────────────────────
Each service owns its data

```

```
┌──────────┐      ┌──────────┐      ┌──────────┐
│  User    │      │  Order   │      │ Product  │
│ Service  │      │ Service  │      │ Service  │
└────┬─────┘      └────┬─────┘      └────┬─────┘
     │                 │                 │
     ▼                 ▼                 ▼
┌─────────┐       ┌─────────┐       ┌─────────┐
│User DB  │       │Order DB │       │Product  │
│(MongoDB)│       │(Postgres│       │DB (MySQL│
└─────────┘       └─────────┘       └─────────┘

Different databases OK!
Choose best tool for each service.
```

```
Benefits:
─────────────────────────────────────────────────────────────
✅ Service autonomy
✅ Independent scaling
✅ Technology choice
✅ Loose coupling
✅ Fault isolation

Challenges:
─────────────────────────────────────────────────────────────
❌ No joins across services
❌ Data duplication
❌ Distributed transactions
❌ Data consistency

╔════════════════════════════════════════════════════════════╗
║                   DATA PATTERNS                            ║
╚════════════════════════════════════════════════════════════╝

1. Data Duplication (Denormalization):
─────────────────────────────────────────────────────────────
Copy data between services

Example:
Order Service stores user info (name, email)
Even though User Service owns users

```

```
User Service:                Order Service:
┌─────────────┐             ┌──────────────────┐
│ Users       │             │ Orders           │
├─────────────┤             ├──────────────────┤
│ id          │             │ id               │
│ name        │             │ user_id          │
│ email       │──duplicated─│ user_name        │
│ password    │      →      │ user_email       │
└─────────────┘             │ items            │
                            │ total            │
                            └──────────────────┘
```

```
When to Duplicate:
✅ Read-heavy data
✅ Rarely changes
✅ Need fast access
✅ Avoid service calls

Sync Mechanism:
• Events (when user updates → publish event)
• Order Service subscribes and updates copy

2. API Composition:
─────────────────────────────────────────────────────────────
Fetch from multiple services and combine

```

```
GET /orders/123/details

API Gateway:
1. Call Order Service → Get order
2. Call User Service → Get user info
3. Call Product Service → Get product details
4. Combine all data
5. Return to client

Pros: ✅ No duplication
Cons: ❌ Multiple network calls, slower
```

```
3. Event Sourcing:
─────────────────────────────────────────────────────────────
Store events, not state

```

```
Traditional:
┌─────────────┐
│ User Table  │
├─────────────┤
│ id: 1       │
│ name: John  │
│ email: j@e  │
└─────────────┘

Event Sourcing:
┌──────────────────────────────┐
│ Events                       │
├──────────────────────────────┤
│ UserCreated(id=1, name=John) │
│ EmailUpdated(id=1, email=j@) │
│ NameChanged(id=1, name=John) │
└──────────────────────────────┘

Current state = replay all events
```

```
Benefits:
✅ Complete history (audit log)
✅ Time travel (rebuild state at any point)
✅ Easy to add new views
✅ Event-driven naturally

Use Cases:
• Banking (transaction history)
• E-commerce (order lifecycle)
• Audit requirements

╔════════════════════════════════════════════════════════════╗
║                   HANDLING QUERIES ACROSS SERVICES         ║
╚════════════════════════════════════════════════════════════╝

Problem:
"Get all orders with user name and product details"

In Monolith:
```

```sql
SELECT orders.*, users.name, products.name
FROM orders
JOIN users ON orders.user_id = users.id
JOIN products ON orders.product_id = products.id;
```

```
In Microservices:
No joins across services!

Solutions:
─────────────────────────────────────────────────────────────

Option 1: API Composition (Runtime Join)
```

```javascript
async function getOrderDetails(orderId) {
  // 1. Get order
  const order = await orderService.getOrder(orderId);

  // 2. Get user
  const user = await userService.getUser(order.userId);

  // 3. Get products
  const products = await Promise.all(
    order.items.map((item) => productService.getProduct(item.productId))
  );

  // 4. Combine
  return {
    ...order,
    userName: user.name,
    items: order.items.map((item, i) => ({
      ...item,
      productName: products[i].name,
    })),
  };
}
```

```
Pros: ✅ Always up-to-date
Cons: ❌ Multiple network calls, slower

Option 2: CQRS (Separate Read Model)
```

```
Write:
Order created → Event → Multiple DBs update

Read:
Materialized view with all data pre-joined

┌──────────────────────────────┐
│ Order Read Model (View)      │
├──────────────────────────────┤
│ order_id                     │
│ user_name (denormalized)     │
│ product_name (denormalized)  │
│ total                        │
└──────────────────────────────┘

Query this view directly (fast!)
```

```
Pros: ✅ Fast reads
Cons: ❌ Eventually consistent

Option 3: Data Duplication
Store necessary data in Order Service

Pros: ✅ Fast, no network calls
Cons: ❌ Data duplication, sync needed

Choose Based on:
─────────────────────────────────────────────────────────────
• Consistency requirements (strong vs eventual)
• Performance needs
• Query complexity
• Data update frequency

Common Pattern: Mix approaches!
```

---

<div align="center">

## 📨 Event-Driven Architecture

</div>

### Decouple Services with Events 🔄

```
# ═══════════════════════════════════════════
# EVENT-DRIVEN MICROSERVICES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WHAT IS EVENT-DRIVEN?                    ║
╚════════════════════════════════════════════════════════════╝

Event-Driven:
─────────────────────────────────────────────────────────────
Services communicate by publishing and subscribing to events

```

```
┌──────────┐  UserCreated   ┌───────────────┐
│  User    │──────Event────▶│  Event Bus    │
│ Service  │                └───────┬───────┘
└──────────┘                        │
                            ┌───────┼───────┐
                            ▼       ▼       ▼
                        ┌─────┐ ┌─────┐ ┌─────┐
                        │Email│ │Notif│ │Audit│
                        └─────┘ └─────┘ └─────┘

All subscribers receive event
Loose coupling!
```

```
Event Structure:
```

```json
{
  "eventId": "uuid-123",
  "eventType": "UserCreated",
  "timestamp": "2024-01-15T10:30:00Z",
  "source": "user-service",
  "data": {
    "userId": 123,
    "name": "John Doe",
    "email": "john@example.com"
  }
}
```

```
╔════════════════════════════════════════════════════════════╗
║                   BENEFITS                                 ║
╚════════════════════════════════════════════════════════════╝

Benefits:
─────────────────────────────────────────────────────────────
✅ Loose Coupling
   Services don't know about each other

✅ Scalability
   Add new subscribers without changing publisher

✅ Async Processing
   Don't wait for subscribers

✅ Audit Trail
   All events logged

✅ Temporal Decoupling
   Services can be offline

Challenges:
─────────────────────────────────────────────────────────────
❌ Debugging Complex
   Hard to trace event flow

❌ Eventual Consistency
   Not immediate

❌ Event Ordering
   Events can arrive out of order

❌ Duplicate Events
   Need idempotent handlers

╔════════════════════════════════════════════════════════════╗
║                   IMPLEMENTATION                           ║
╚════════════════════════════════════════════════════════════╝

Using RabbitMQ:
```

```javascript
// Publisher (User Service)
const amqp = require("amqplib");

async function publishEvent(eventType, data) {
  const connection = await amqp.connect("amqp://rabbitmq");
  const channel = await connection.createChannel();
  const exchange = "events";

  await channel.assertExchange(exchange, "fanout", { durable: true });

  const event = {
    eventId: generateUUID(),
    eventType,
    timestamp: new Date().toISOString(),
    source: "user-service",
    data,
  };

  channel.publish(exchange, "", Buffer.from(JSON.stringify(event)));

  console.log("Event published:", eventType);
  await channel.close();
  await connection.close();
}

// When user created
async function createUser(userData) {
  const user = await db.insertUser(userData);

  await publishEvent("UserCreated", {
    userId: user.id,
    name: user.name,
    email: user.email,
  });

  return user;
}

// Subscriber (Email Service)
async function subscribeToEvents() {
  const connection = await amqp.connect("amqp://rabbitmq");
  const channel = await connection.createChannel();
  const exchange = "events";
  const queue = "email-service-queue";

  await channel.assertExchange(exchange, "fanout", { durable: true });
  await channel.assertQueue(queue, { durable: true });
  await channel.bindQueue(queue, exchange, "");

  channel.consume(queue, async (msg) => {
    const event = JSON.parse(msg.content.toString());

    if (event.eventType === "UserCreated") {
      await sendWelcomeEmail(event.data.email);
      console.log("Welcome email sent to", event.data.email);
    }

    channel.ack(msg);
  });
}

subscribeToEvents();
```

```
Using Kafka:
```

```javascript
const { Kafka } = require("kafkajs");

const kafka = new Kafka({
  clientId: "user-service",
  brokers: ["kafka:9092"],
});

// Producer
const producer = kafka.producer();

async function publishEvent(topic, event) {
  await producer.connect();
  await producer.send({
    topic,
    messages: [{ value: JSON.stringify(event) }],
  });
  await producer.disconnect();
}

// Consumer
const consumer = kafka.consumer({ groupId: "email-service" });

async function subscribeToEvents() {
  await consumer.connect();
  await consumer.subscribe({ topic: "user-events" });

  await consumer.run({
    eachMessage: async ({ topic, partition, message }) => {
      const event = JSON.parse(message.value.toString());

      if (event.eventType === "UserCreated") {
        await sendWelcomeEmail(event.data.email);
      }
    },
  });
}
```

```
╔════════════════════════════════════════════════════════════╗
║                   EVENT PATTERNS                           ║
╚════════════════════════════════════════════════════════════╝

1. Event Notification:
─────────────────────────────────────────────────────────────
Minimal info, subscribers fetch more if needed

Event: { eventType: "OrderCreated", orderId: 123 }
Subscriber: Fetch order details from Order Service

2. Event-Carried State Transfer:
─────────────────────────────────────────────────────────────
All necessary data in event

Event: {
  eventType: "OrderCreated",
  order: { id: 123, total: 99.99, items: [...] }
}
Subscriber: Has all data, no need to call Order Service

3. Event Sourcing:
─────────────────────────────────────────────────────────────
Events are source of truth

Store all events, rebuild state by replaying

Best Practices:
─────────────────────────────────────────────────────────────
✅ Idempotent event handlers (handle duplicates)
✅ Version events (schema evolution)
✅ Include correlation ID (tracing)
✅ Set event retention policy
✅ Dead letter queue for failed events
✅ Monitor event lag
```

---

<div align="center">

## 🚀 Deployment & DevOps

</div>

### Deploy and Manage Microservices 🛠️

```
# ═══════════════════════════════════════════
# DEPLOYMENT STRATEGIES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   CONTAINERIZATION                         ║
╚════════════════════════════════════════════════════════════╝

Docker:
─────────────────────────────────────────────────────────────
Each service in its own container

Dockerfile:
```

```dockerfile
FROM node:18-alpine

WORKDIR /app

COPY package*.json ./
RUN npm ci --only=production

COPY . .

EXPOSE 3000

CMD ["node", "server.js"]
```

```
Build and Run:
```

```bash
# Build image
docker build -t user-service:1.0 .

# Run container
docker run -d -p 3000:3000 --name user-service user-service:1.0

# Docker Compose (multiple services)
docker-compose up
```

```
docker-compose.yml:
```

```yaml
version: "3.8"

services:
  user-service:
    build: ./user-service
    ports:
      - "3000:3000"
    environment:
      - DB_HOST=postgres
      - REDIS_HOST=redis
    depends_on:
      - postgres
      - redis

  order-service:
    build: ./order-service
    ports:
      - "3001:3000"
    depends_on:
      - postgres

  postgres:
    image: postgres:15
    environment:
      - POSTGRES_PASSWORD=secret
    volumes:
      - postgres-data:/var/lib/postgresql/data

  redis:
    image: redis:7-alpine

volumes:
  postgres-data:
```

```
╔════════════════════════════════════════════════════════════╗
║                   KUBERNETES                               ║
╚════════════════════════════════════════════════════════════╝

Kubernetes:
─────────────────────────────────────────────────────────────
Orchestrate containers at scale

```

```
┌─────────────────────────────────────────┐
│         Kubernetes Cluster              │
│  ┌───────────────────────────────────┐  │
│  │         Namespace: prod           │  │
│  │  ┌──────────┐    ┌──────────┐     │  │
│  │  │  Pod     │    │  Pod     │     │  │
│  │  │ User Svc │    │Order Svc │     │  │
│  │  └──────────┘    └──────────┘     │  │
│  │  ┌──────────┐    ┌──────────┐     │  │
│  │  │ Service  │    │ Service  │     │  │
│  │  │(ClusterIP│    │(ClusterIP│     │  │
│  │  └──────────┘    └──────────┘     │  │
│  │  ┌──────────────────────────┐     │  │
│  │  │  Ingress (Load Balancer) │     │  │
│  │  └──────────────────────────┘     │  │
│  └───────────────────────────────────┘  │
└─────────────────────────────────────────┘
```

```
Deployment YAML:
```

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: user-service
spec:
  replicas: 3
  selector:
    matchLabels:
      app: user-service
  template:
    metadata:
      labels:
        app: user-service
    spec:
      containers:
        - name: user-service
          image: user-service:1.0
          ports:
            - containerPort: 3000
          env:
            - name: DB_HOST
              value: postgres
          resources:
            requests:
              memory: "128Mi"
              cpu: "250m"
            limits:
              memory: "256Mi"
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
---
apiVersion: v1
kind: Service
metadata:
  name: user-service
spec:
  selector:
    app: user-service
  ports:
    - port: 80
      targetPort: 3000
  type: ClusterIP
```

```
Key Concepts:
─────────────────────────────────────────────────────────────
• Pod: Smallest unit (1+ containers)
• Deployment: Manages pods
• Service: Exposes pods (load balancing)
• Ingress: External access
• ConfigMap: Configuration
• Secret: Sensitive data
• Namespace: Isolation

Commands:
```

```bash
# Deploy
kubectl apply -f deployment.yaml

# Scale
kubectl scale deployment user-service --replicas=5

# Update (rolling update)
kubectl set image deployment/user-service user-service=user-service:2.0

# View
kubectl get pods
kubectl get services
kubectl logs user-service-abc123

# Rollback
kubectl rollout undo deployment/user-service
```

```
╔════════════════════════════════════════════════════════════╗
║                   DEPLOYMENT STRATEGIES                    ║
╚════════════════════════════════════════════════════════════╝

1. Blue-Green Deployment:
─────────────────────────────────────────────────────────────
Two identical environments

```

```
Step 1: Blue (current) handles traffic
┌──────┐    ┌──────────────┐
│Users │───▶│ Blue (v1.0)  │ ← Live
└──────┘    └──────────────┘
            ┌──────────────┐
            │ Green (v2.0) │ ← Staging
            └──────────────┘

Step 2: Test Green

Step 3: Switch traffic to Green
┌──────┐    ┌──────────────┐
│Users │    │ Blue (v1.0)  │ ← Standby
└──────┘    └──────────────┘
      │     ┌──────────────┐
      └────▶│ Green (v2.0) │ ← Live
            └──────────────┘

Rollback: Switch back to Blue

Pros: ✅ Zero downtime, easy rollback
Cons: ❌ Double resources
```

```
2. Canary Deployment:
─────────────────────────────────────────────────────────────
Gradual rollout

```

```
Step 1: 90% v1.0, 10% v2.0
┌──────┐    ┌──────────────┐
│Users │───▶│ v1.0 (90%)   │
└──────┘    └──────────────┘
      │     ┌──────────────┐
      └────▶│ v2.0 (10%)   │ ← Canary
            └──────────────┘

Step 2: Monitor canary

Step 3: 50% v1.0, 50% v2.0

Step 4: 100% v2.0

Rollback: Stop routing to v2.0

Pros: ✅ Gradual, low risk
Cons: ❌ Complex monitoring
```

```
3. Rolling Deployment:
─────────────────────────────────────────────────────────────
Update instances one at a time

```

```
3 instances: v1.0, v1.0, v1.0

Step 1: v2.0, v1.0, v1.0
Step 2: v2.0, v2.0, v1.0
Step 3: v2.0, v2.0, v2.0

Always some instances available

Pros: ✅ No extra resources
Cons: ❌ Both versions running simultaneously
```

---

<div align="center">

## 📊 Monitoring & Observability

</div>

### Know What's Happening 👀

```
# ═══════════════════════════════════════════
# MONITORING & OBSERVABILITY
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   THREE PILLARS                            ║
╚════════════════════════════════════════════════════════════╝

1. Metrics:
─────────────────────────────────────────────────────────────
Numbers over time

Examples:
• CPU usage
• Memory usage
• Request count
• Response time
• Error rate

Tools: Prometheus, Grafana

2. Logs:
─────────────────────────────────────────────────────────────
Event records

Examples:
• Application logs
• Error logs
• Access logs

Tools: ELK Stack (Elasticsearch, Logstash, Kibana)

3. Traces:
─────────────────────────────────────────────────────────────
Request journey across services

```

```
User Request
  ↓
API Gateway (50ms)
  ↓
User Service (20ms)
  ↓
Order Service (100ms)
  ├─→ Payment Service (80ms)
  └─→ Inventory Service (30ms)

Total: 280ms

Tools: Jaeger, Zipkin

╔════════════════════════════════════════════════════════════╗
║                   DISTRIBUTED TRACING                      ║
╚════════════════════════════════════════════════════════════╝

Problem:
Request touches 5 services, slow response
Which service is the bottleneck?

Solution: Distributed Tracing
```

```
┌───────────────────────────────────────────────────┐
│  Trace ID: abc-123                                │
├───────────────────────────────────────────────────┤
│  API Gateway      [████] 50ms                     │
│  └─ User Service  [██] 20ms                       │
│     └─ Order Service [████████████] 100ms         │
│        ├─ Payment Service [███████] 80ms  ← Slow! │
│        └─ Inventory Service [███] 30ms            │
└───────────────────────────────────────────────────┘

Payment Service is the bottleneck!
```

```
Implementation (Jaeger):
```

```javascript
const opentracing = require("opentracing");
const initJaegerTracer = require("jaeger-client").initTracer;

// Initialize tracer
const config = {
  serviceName: "user-service",
  sampler: { type: "const", param: 1 },
  reporter: { logSpans: true },
};

const tracer = initJaegerTracer(config);

// Instrument code
app.get("/users/:id", async (req, res) => {
  const span = tracer.startSpan("get_user");
  span.setTag("user.id", req.params.id);

  try {
    const user = await db.findUser(req.params.id);
    res.json(user);
  } catch (error) {
    span.setTag("error", true);
    span.log({ event: "error", message: error.message });
    res.status(500).json({ error: "Failed" });
  } finally {
    span.finish();
  }
});
```

```
Correlation ID:
─────────────────────────────────────────────────────────────
Track request across services

```

```
Request ID: req-xyz-789

API Gateway    [req-xyz-789] Request started
User Service   [req-xyz-789] Fetching user
Order Service  [req-xyz-789] Creating order
Payment Service[req-xyz-789] Charging card

All logs have same ID!
Easy to trace full request path
```

```
Best Practices:
─────────────────────────────────────────────────────────────
✅ Structured logging (JSON)
✅ Centralized logging
✅ Include correlation IDs
✅ Set up alerts
✅ Monitor key metrics (SLIs)
✅ Define SLOs (Service Level Objectives)
✅ Dashboard for each service
✅ On-call rotation
```

---

## 💡 Best Practices

### Microservices Wisdom 🎓

```
# ═══════════════════════════════════════════
# MICROSERVICES BEST PRACTICES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   DO'S AND DON'TS                          ║
╚════════════════════════════════════════════════════════════╝

DO's:
─────────────────────────────────────────────────────────────
✅ Start with monolith
✅ Define clear boundaries
✅ Design for failure
✅ Automate everything
✅ Monitor everything
✅ One database per service
✅ API versioning
✅ Async communication when possible
✅ CI/CD pipeline for each service
✅ Document your APIs
✅ Health check endpoints
✅ Graceful shutdown
✅ Correlation IDs
✅ Circuit breakers
✅ Rate limiting

DON'Ts:
─────────────────────────────────────────────────────────────
❌ Shared database
❌ Distributed transactions (avoid if possible)
❌ Tight coupling
❌ Chatty services (too many calls)
❌ Microservices for small projects
❌ Premature optimization
❌ Ignore security
❌ Manual deployments
❌ Synchronous calls everywhere
❌ Too fine-grained services
❌ Ignore monitoring

╔════════════════════════════════════════════════════════════╗
║                   SERVICE SIZE                             ║
╚════════════════════════════════════════════════════════════╝

How Big/Small?
─────────────────────────────────────────────────────────────

Too Small (Nanoservices):
❌ UserService, UserEmailService, UserPasswordService
❌ Too many network calls
❌ Overhead > benefit

Too Big:
❌ One service does everything
❌ Defeats purpose

Just Right:
✅ Focused on one business capability
✅ Can be built by one team
✅ 2-week sprints
✅ Fits in your head

Rules of Thumb:
─────────────────────────────────────────────────────────────
• Small enough: One team can own it
• Large enough: Provides business value
• Independent: Can deploy without touching others
• Cohesive: Related functionality together

"Microservices should be as small as possible,
but no smaller." - Sam Newman

╔════════════════════════════════════════════════════════════╗
║                   MIGRATION CHECKLIST                      ║
╚════════════════════════════════════════════════════════════╝

Before Migrating to Microservices:
─────────────────────────────────────────────────────────────
☐ Team size > 20 developers?
☐ Monolith has clear domain boundaries?
☐ Need independent scaling?
☐ Have DevOps expertise?
☐ CI/CD pipeline in place?
☐ Monitoring and logging ready?
☐ Team understands distributed systems?
☐ Leadership buy-in?
☐ Budget for infrastructure?
☐ Can handle increased complexity?

If < 7 checked: Stay with monolith!

╔════════════════════════════════════════════════════════════╗
║                   LEARNING RESOURCES                       ║
╚════════════════════════════════════════════════════════════╝

Books:
─────────────────────────────────────────────────────────────
📚 "Building Microservices" - Sam Newman
📚 "Microservices Patterns" - Chris Richardson
📚 "Release It!" - Michael Nygard
📚 "Domain-Driven Design" - Eric Evans

Websites:
─────────────────────────────────────────────────────────────
🔗 microservices.io (patterns)
🔗 martinfowler.com (articles)
🔗 12factor.net (methodology)

Practice:
─────────────────────────────────────────────────────────────
💪 Build small microservices project
💪 Contribute to open-source microservices
💪 Read architecture blogs (Netflix, Uber, Airbnb)

╔════════════════════════════════════════════════════════════╗
║                   FINAL WISDOM                             ║
╚════════════════════════════════════════════════════════════╝

Remember:
─────────────────────────────────────────────────────────────
"Microservices are not a goal.
They're a means to achieve:
• Independent deployment
• Team autonomy
• Technology diversity
• Scalability

If you don't need these, don't use microservices.

Start with monolith.
Break apart when needed.
Not before.

Complexity is your enemy.
Add it only when benefits outweigh costs."

Key Principles:
─────────────────────────────────────────────────────────────
✅ Start simple
✅ Design for failure
✅ Automate everything
✅ Monitor relentlessly
✅ Document thoroughly
✅ Test extensively
✅ Deploy independently
✅ Scale intelligently

Microservices are powerful,
but with great power comes great complexity.

Choose wisely! 🚀
```

---

<div align="center">

## 📊 Quick Reference

</div>

### Microservices Cheat Sheet 📝

| Aspect          | Monolith          | Microservices        |
| --------------- | ----------------- | -------------------- |
| **Team Size**   | < 10 developers   | 50+ developers       |
| **Deployment**  | Single unit       | Multiple services    |
| **Scaling**     | Scale everything  | Scale independently  |
| **Technology**  | Single stack      | Multiple stacks      |
| **Data**        | Shared database   | Database per service |
| **Complexity**  | Low               | High                 |
| **Testing**     | Easy              | Complex              |
| **Performance** | Fast (in-process) | Network overhead     |
| **Failure**     | All or nothing    | Isolated             |
| **Best For**    | Startups, MVPs    | Large enterprises    |

### Common Patterns

| Pattern               | Purpose                    | When to Use              |
| --------------------- | -------------------------- | ------------------------ |
| **API Gateway**       | Single entry point         | Always in microservices  |
| **Service Discovery** | Find services dynamically  | Dynamic environments     |
| **Circuit Breaker**   | Prevent cascading failures | Resilience needed        |
| **Saga**              | Distributed transactions   | Multi-service workflows  |
| **CQRS**              | Separate read/write        | Complex queries          |
| **Event Sourcing**    | Store events               | Audit trail needed       |
| **Strangler Fig**     | Gradual migration          | Monolith → Microservices |

---

<div align="center">

**Built with 🔧 by MrDib, for microservices architects**

_Remember: "Start with monolith, migrate when needed!"_ ✨

**Happy Building!** 🚀

</div>

---

## 🔗 Related Guides

- [System Design](./System-Design.md)
- [Design Patterns](./Design-Patterns.md)
- [Best Practices](./Best-Practices.md)
- [DevOps](../DevOps-Cloud/CI-CD.md)

---
