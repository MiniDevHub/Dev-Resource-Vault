<div align="center">

# 🏗️ System Design - Build Scalable Systems! 🏗️

![System Design](https://img.shields.io/badge/System_Design-Architecture-blue?style=for-the-badge)
![Scalability](https://img.shields.io/badge/Scalability-High_Scale-green?style=for-the-badge)
![Distributed](https://img.shields.io/badge/Distributed_Systems-Cloud-orange?style=for-the-badge)

### _Design systems that scale to millions_ 🚀

**From small apps to global platforms!** ✨

</div>

---

## 📚 Table of Contents

- [🎯 What is System Design](#-what-is-system-design)
- [📊 Key Concepts](#-key-concepts)
- [⚖️ Scalability](#️-scalability)
- [🔄 Load Balancing](#-load-balancing)
- [⚡ Caching](#-caching)
- [💾 Database Design](#-database-design)
- [🌐 Content Delivery Networks](#-content-delivery-networks)
- [📬 Message Queues](#-message-queues)
- [🔧 Microservices Architecture](#-microservices-architecture)
- [🎯 System Design Process](#-system-design-process)
- [📱 Real-World Examples](#-real-world-examples)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 🎯 What is System Design

</div>

### Understanding System Design 🌟

```

# ═══════════════════════════════════════════

# SYSTEM DESIGN EXPLAINED

# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║ WHAT IS SYSTEM DESIGN?                                     ║
╚════════════════════════════════════════════════════════════╝

System Design:
─────────────────────────────────────────────────────────────
The process of defining the architecture, components,
modules, interfaces, and data for a system to satisfy
specified requirements.

Key Aspects:
─────────────────────────────────────────────────────────────
✅ Architecture planning
✅ Component design
✅ Data flow
✅ Scalability
✅ Reliability
✅ Performance
✅ Security
✅ Cost optimization

Why Important:
─────────────────────────────────────────────────────────────
• Handle millions of users
• Ensure high availability
• Scale efficiently
• Minimize costs
• Fast response times
• Handle failures gracefully
• Support future growth

╔════════════════════════════════════════════════════════════╗
║ SMALL vs LARGE SCALE                                       ║
╚════════════════════════════════════════════════════════════╝

Small Scale (< 1,000 users):
─────────────────────────────────────────────────────────────

```

```

┌──────────────┐
│ Client │
└──────┬───────┘
│
▼
┌──────────────┐ ┌──────────────┐
│ Web Server │─────▶│ Database │
└──────────────┘ └──────────────┘

Simple Architecture:
• Single server
• Single database
• No caching
• Direct connections

```

```

Medium Scale (1K - 100K users):
─────────────────────────────────────────────────────────────

```

```

┌──────────────┐
│ Client │
└──────┬───────┘
│
▼
┌──────────────┐ ┌──────────────┐
│Load Balancer │ │ Cache │
└──────┬───────┘ └──────┬───────┘
│ │
┌───┴────┬────────────────┘
▼ ▼
┌──────┐ ┌──────┐ ┌──────────────┐
│Server│ │Server│───▶│ Database │
└──────┘ └──────┘ └──────────────┘

Improvements:
• Multiple servers
• Load balancer
• Caching layer
• Database replication

```

```

Large Scale (100K+ users):
─────────────────────────────────────────────────────────────

```

```

              ┌──────────────┐
              │     CDN      │
              └──────┬───────┘
                     │

┌──────────────┐ │
│ Client │─────┘
└──────┬───────┘
│
▼
┌──────────────┐ ┌──────────────┐
│ DNS │ │ CDN │
└──────┬───────┘ └──────────────┘
│
▼
┌──────────────┐ ┌──────────────┐
│Load Balancer │ │ Cache │
└──────┬───────┘ │ (Redis) │
│ └──────┬───────┘
┌───┴────┬────────────────┘
▼ ▼
┌──────┐ ┌──────┐ ┌──────────────┐
│Server│ │Server│ │ Message Queue│
└──┬───┘ └──┬───┘ └──────┬───────┘
│ │ │
└────────┴───────────────┘
│
▼
┌───────────────┐
│ Databases │
│ (Sharded) │
└───────────────┘

Enterprise Features:
• Multiple data centers
• Auto-scaling
• Message queues
• Microservices
• Database sharding
• CDN
• Caching layers
• Monitoring
• Logging

```

```

╔════════════════════════════════════════════════════════════╗
║ SYSTEM DESIGN GOALS                                        ║
╚════════════════════════════════════════════════════════════╝

The Four Pillars:
─────────────────────────────────────────────────────────────

1. Scalability
   Can system handle growth?
   • More users
   • More data
   • More requests

2. Reliability
   System works correctly even with failures
   • Fault tolerance
   • Error handling
   • Data integrity

3. Availability
   System is accessible when needed
   • Uptime (99.9%, 99.99%, 99.999%)
   • No single point of failure
   • Redundancy

4. Performance
   System responds quickly
   • Low latency
   • High throughput
   • Efficient processing

Trade-offs:
─────────────────────────────────────────────────────────────
Can't have everything! Must balance:

Consistency vs Availability (CAP Theorem)
Cost vs Performance
Complexity vs Simplicity
Flexibility vs Efficiency

"Good system design is about making the right trade-offs
for your specific requirements."

```

---

<div align="center">

## 📊 Key Concepts

</div>

### Fundamental Concepts 🎓

```

# ═══════════════════════════════════════════

# KEY SYSTEM DESIGN CONCEPTS

# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║ CAP THEOREM                                                ║
╚════════════════════════════════════════════════════════════╝

The CAP Theorem (Brewer's Theorem):
─────────────────────────────────────────────────────────────
A distributed system can only guarantee 2 out of 3:

C - Consistency
All nodes see the same data at the same time

A - Availability
Every request receives a response (success or failure)

P - Partition Tolerance
System continues to work despite network failures

Can only pick 2:
─────────────────────────────────────────────────────────────

CP (Consistency + Partition Tolerance):
• Sacrifice availability
• Example: Banking systems
• Better to be unavailable than show wrong balance

AP (Availability + Partition Tolerance):
• Sacrifice consistency
• Example: Social media feeds
• OK to see slightly old data, but must be available

CA (Consistency + Availability):
• Sacrifice partition tolerance
• Only works in single-node systems
• Not practical for distributed systems

Real-World Examples:
─────────────────────────────────────────────────────────────
MongoDB (CP): Consistency first
Cassandra (AP): Availability first
PostgreSQL (CA): Single server, both C and A

╔════════════════════════════════════════════════════════════╗
║ LATENCY vs THROUGHPUT                                      ║
╚════════════════════════════════════════════════════════════╝

Latency:
─────────────────────────────────────────────────────────────
Time to complete a single request
"How fast?"

Example: API response in 50ms

Throughput:
─────────────────────────────────────────────────────────────
Number of requests processed per unit time
"How many?"

Example: 1000 requests per second

Trade-off:
─────────────────────────────────────────────────────────────
Low latency ≠ High throughput

Fast car (low latency) vs Bus (high throughput)
• Car: Gets you there fast (low latency)
• Bus: Moves more people total (high throughput)

Optimize based on needs:
• Real-time gaming: Low latency critical
• Batch processing: High throughput critical
• Web APIs: Balance both

╔════════════════════════════════════════════════════════════╗
║ AVAILABILITY NUMBERS                                       ║
╚════════════════════════════════════════════════════════════╝

Uptime Percentages:
─────────────────────────────────────────────────────────────

```

| Availability      | Downtime/Year | Downtime/Month | Downtime/Week |
| ----------------- | ------------- | -------------- | ------------- |
| 90%               | 36.5 days     | 72 hours       | 16.8 hours    |
| 95%               | 18.25 days    | 36 hours       | 8.4 hours     |
| 99%               | 3.65 days     | 7.2 hours      | 1.68 hours    |
| 99.9% (3 nines)   | 8.76 hours    | 43.2 minutes   | 10.1 minutes  |
| 99.99% (4 nines)  | 52.56 minutes | 4.32 minutes   | 1.01 minutes  |
| 99.999% (5 nines) | 5.26 minutes  | 25.9 seconds   | 6.05 seconds  |

```

Industry Standards:
─────────────────────────────────────────────────────────────
• Most services: 99.9% (Three nines)
• Critical services: 99.99% (Four nines)
• Mission critical: 99.999% (Five nines)

Cost increases exponentially with each nine!

╔════════════════════════════════════════════════════════════╗
║ BACK-OF-THE-ENVELOPE CALCULATIONS                          ║
╚════════════════════════════════════════════════════════════╝

Quick Estimates:
─────────────────────────────────────────────────────────────

Time Scales:
• 1 second = 1,000 milliseconds (ms)
• 1 ms = 1,000 microseconds (μs)
• 1 μs = 1,000 nanoseconds (ns)

Latency Numbers:
• L1 cache: 0.5 ns
• L2 cache: 7 ns
• RAM: 100 ns
• SSD: 150 μs (0.15 ms)
• Network within datacenter: 0.5 ms
• HDD: 10 ms
• Network cross-country: 50-100 ms
• Network cross-ocean: 150+ ms

Storage:
• 1 KB = 1,000 bytes
• 1 MB = 1,000 KB
• 1 GB = 1,000 MB
• 1 TB = 1,000 GB
• 1 PB = 1,000 TB

Traffic Estimates:
─────────────────────────────────────────────────────────────
Example: Twitter-like service

Given:
• 300 million daily active users
• Each user posts 2 tweets per day
• 10% of tweets contain media (images/videos)

Calculations:
─────────────────────────────────────────────────────────────
Tweets per day:
300M users × 2 tweets = 600M tweets/day

Tweets per second:
600M tweets / 86,400 seconds ≈ 7,000 tweets/second

Read/Write Ratio (typical: 100:1):
• Writes: 7,000 tweets/sec
• Reads: 700,000 tweets/sec

Storage:
• Text: 140 chars × 2 bytes = 280 bytes
• Media: 200 KB average
• Daily storage: 600M × 280 bytes + (60M × 200 KB)
= 168 GB text + 12 TB media = ~12.2 TB/day

Network Bandwidth:
• Reads: 700K req/sec × 280 bytes = 196 MB/sec
• With media: Add ~20 GB/sec

Servers Needed (rough estimate):
• 1 server handles 10,000 req/sec
• Need 70 servers minimum
• With redundancy: 150-200 servers

```

---

<div align="center">

## ⚖️ Scalability

</div>

### Scale Your System 📈

```

# ═══════════════════════════════════════════

# SCALABILITY STRATEGIES

# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║ VERTICAL vs HORIZONTAL                                     ║
╚════════════════════════════════════════════════════════════╝

Vertical Scaling (Scale Up):
─────────────────────────────────────────────────────────────
Add more power to existing machine

```

```

Before: After:
┌────────┐ ┌────────┐
│ 4 CPU │ │ 16 CPU │
│ 8 GB │ → │ 64 GB │
│ 100GB │ │ 1 TB │
└────────┘ └────────┘

Pros:
✅ Simple (no code changes)
✅ No data consistency issues
✅ Lower latency (single machine)

Cons:
❌ Hardware limits (can't scale infinitely)
❌ Single point of failure
❌ Expensive at scale
❌ Downtime during upgrade

```

```

Horizontal Scaling (Scale Out):
─────────────────────────────────────────────────────────────
Add more machines

```

```

Before: After:
┌────────┐   ┌────────┐ ┌────────┐ ┌────────┐
│Server 1│   │Server 1│ │Server 2│ │Server 3│
└────────┘ → └────────┘ └────────┘ └────────┘

Pros:
✅ Unlimited scaling potential
✅ No single point of failure
✅ Cheaper (commodity hardware)
✅ No downtime (add/remove servers)

Cons:
❌ Complex (code must support)
❌ Data consistency challenges
❌ Network latency between machines
❌ More management overhead

```

```

Which to Choose:
─────────────────────────────────────────────────────────────
Start: Vertical (simple)
Growth: Horizontal (only way to scale infinitely)

Most systems: Both!
• Vertical: Delay complexity
• Horizontal: When vertical maxes out

╔════════════════════════════════════════════════════════════╗
║ STATELESS vs STATEFUL                                      ║
╚════════════════════════════════════════════════════════════╝

Stateless Servers:
─────────────────────────────────────────────────────────────
Server doesn't store session data

```

```

Request 1 → Server A → Response
Request 2 → Server B → Response (any server works!)

Pros:
✅ Easy to scale
✅ Any server can handle any request
✅ Server failure doesn't lose data
✅ Simple load balancing

Implementation:
• Store sessions in database/cache
• Use JWT tokens
• Pass all needed data in request

```

```

Stateful Servers:
─────────────────────────────────────────────────────────────
Server stores session data

```

```

User → Server A (has session data)
User → Server A (MUST go to same server)

Cons:
❌ Hard to scale
❌ Sticky sessions needed
❌ Server failure loses data
❌ Uneven load distribution

When Needed:
• WebSocket connections
• Long-running operations
• Gaming servers

Best Practice: Make servers stateless whenever possible!

```

```

╔════════════════════════════════════════════════════════════╗
║ AUTO-SCALING                                               ║
╚════════════════════════════════════════════════════════════╝

Dynamic Scaling:
─────────────────────────────────────────────────────────────
Automatically add/remove servers based on load

```

```

Low Traffic: High Traffic:
┌────────┐ ┌────────┐ ┌────────┐
│Server 1│ │Server 1│ │Server 2│
└────────┘ ├────────┤ ├────────┤
│Server 3│ │Server 4│
└────────┘ └────────┘

```

```

Metrics to Monitor:
─────────────────────────────────────────────────────────────
• CPU usage (> 70% → scale up)
• Memory usage
• Request queue length
• Response time
• Network throughput

Scaling Policies:
─────────────────────────────────────────────────────────────
Scale Up When:
• CPU > 70% for 5 minutes
• Response time > 200ms
• Queue length > 100

Scale Down When:
• CPU < 30% for 15 minutes
• Low traffic period

Implementation:
─────────────────────────────────────────────────────────────
• AWS Auto Scaling Groups
• Kubernetes Horizontal Pod Autoscaler
• Google Cloud Autoscaler
• Azure VM Scale Sets

```

---

<div align="center">

## 🔄 Load Balancing

</div>

### Distribute Traffic Efficiently ⚖️

```

# ═══════════════════════════════════════════

# LOAD BALANCING

# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║ WHAT IS LOAD BALANCING?                                    ║
╚════════════════════════════════════════════════════════════╝

Load Balancer:
─────────────────────────────────────────────────────────────
Distributes incoming traffic across multiple servers

```

```

                ┌──────────────┐
                │    Clients   │
                └──────┬───────┘
                       │
                       ▼
                ┌──────────────┐
                │Load Balancer │
                └──────┬───────┘
                       │
        ┌──────────────┼──────────────┐
        ▼              ▼              ▼
        ┌────────┐ ┌────────┐ ┌────────┐
        │Server 1│ │Server 2│ │Server 3│
        └────────┘ └────────┘ └────────┘

```

```

Benefits:
─────────────────────────────────────────────────────────────
✅ Distribute traffic evenly
✅ No single point of failure
✅ Better resource utilization
✅ Scale horizontally
✅ Health checks (remove failed servers)
✅ SSL termination
✅ Session persistence

╔════════════════════════════════════════════════════════════╗
║ LOAD BALANCING ALGORITHMS                                  ║
╚════════════════════════════════════════════════════════════╝

1. Round Robin:
   ─────────────────────────────────────────────────────────────
   Distribute requests sequentially

Request 1 → Server A
Request 2 → Server B
Request 3 → Server C
Request 4 → Server A (loop back)

Pros: Simple, fair
Cons: Doesn't consider server load

2. Least Connections:
   ─────────────────────────────────────────────────────────────
   Send to server with fewest active connections

Server A: 10 connections
Server B: 5 connections ← Next request goes here
Server C: 8 connections

Pros: Better load distribution
Cons: More complex

3. Least Response Time:
   ─────────────────────────────────────────────────────────────
   Send to fastest responding server

Server A: 100ms avg
Server B: 50ms avg ← Next request goes here
Server C: 80ms avg

Pros: Best user experience
Cons: Most complex

4. IP Hash:
   ─────────────────────────────────────────────────────────────
   Route based on client IP (sticky sessions)

hash(client_IP) % num_servers = server

Client 1.2.3.4 → Always Server A
Client 5.6.7.8 → Always Server B

Pros: Session persistence
Cons: Uneven distribution

5. Weighted Round Robin:
   ─────────────────────────────────────────────────────────────
   Assign weights to servers

Server A (weight 3): Gets 3 requests
Server B (weight 2): Gets 2 requests
Server C (weight 1): Gets 1 request

Use when servers have different capacities

╔════════════════════════════════════════════════════════════╗
║ LAYER 4 vs LAYER 7 LB                                      ║
╚════════════════════════════════════════════════════════════╝

Layer 4 (Transport Layer):
─────────────────────────────────────────────────────────────
Routes based on IP and port

Pros:
✅ Fast (no content inspection)
✅ Lower latency
✅ Higher throughput

Cons:
❌ No content-based routing
❌ No SSL termination

Use for: High-performance, simple routing

Layer 7 (Application Layer):
─────────────────────────────────────────────────────────────
Routes based on content (URL, headers, cookies)

Examples:
/api/users → API servers
/static/_ → Static file servers
/admin/_ → Admin servers

Pros:
✅ Smart routing
✅ SSL termination
✅ Content caching
✅ Request modification

Cons:
❌ Slower (content inspection)
❌ More CPU intensive

Use for: Complex routing, microservices

╔════════════════════════════════════════════════════════════╗
║ POPULAR LOAD BALANCERS                                     ║
╚════════════════════════════════════════════════════════════╝

Software:
─────────────────────────────────────────────────────────────
• Nginx (most popular)
• HAProxy
• Apache HTTP Server
• Traefik (modern, container-friendly)

Cloud:
─────────────────────────────────────────────────────────────
• AWS Elastic Load Balancer (ELB)
• Google Cloud Load Balancing
• Azure Load Balancer
• Cloudflare Load Balancing

Hardware:
─────────────────────────────────────────────────────────────
• F5 BIG-IP
• Citrix ADC
• A10 Networks

Most Common: Nginx or Cloud LB

```

---

<div align="center">

## ⚡ Caching

</div>

### Speed Up Your System 🚀

```
# ═══════════════════════════════════════════
# CACHING STRATEGIES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WHAT IS CACHING?                         ║
╚════════════════════════════════════════════════════════════╝

Caching:
─────────────────────────────────────────────────────────────
Store frequently accessed data in fast storage (memory)
to avoid expensive operations (database queries, API calls)

```

```
Without Cache:                With Cache:
┌──────┐                      ┌──────┐
│Client│                      │Client│
└───┬──┘                      └───┬──┘
    │                             │
    ▼                             ▼
┌──────────┐                  ┌───────┐
│  Server  │                  │ Cache │ ← Fast (1ms)
└───┬──────┘                  └───┬───┘
    │                             │ (miss)
    ▼                             ▼
┌──────────┐                  ┌──────────┐
│ Database │ ← Slow (100ms)   │ Database │ ← Only on miss
└──────────┘                  └──────────┘

Speed: 100x faster with cache hit!
```

```
Benefits:
─────────────────────────────────────────────────────────────
✅ Reduce latency (faster response)
✅ Reduce database load
✅ Save money (fewer DB queries)
✅ Handle traffic spikes
✅ Improve user experience

╔════════════════════════════════════════════════════════════╗
║                   CACHING STRATEGIES                       ║
╚════════════════════════════════════════════════════════════╝

1. Cache-Aside (Lazy Loading):
─────────────────────────────────────────────────────────────
Application checks cache first

```

```
Read:
1. Check cache
2. If miss → read from DB
3. Store in cache
4. Return data

Write:
1. Write to DB
2. Invalidate cache

Pros:
✅ Only cache what's needed
✅ Resilient (cache failure = slower, not broken)

Cons:
❌ First request slow (cache miss)
❌ Data can be stale

Use: Most common pattern
```

```
2. Write-Through:
─────────────────────────────────────────────────────────────
Write to cache and DB simultaneously

```

```
Write:
1. Write to cache
2. Write to DB (synchronous)
3. Return success

Read:
1. Check cache (always fresh!)
2. Return data

Pros:
✅ Data always fresh
✅ Consistent

Cons:
❌ Slower writes (both operations)
❌ Cache unnecessary data

Use: When consistency critical
```

```
3. Write-Behind (Write-Back):
─────────────────────────────────────────────────────────────
Write to cache, DB later (async)

```

```
Write:
1. Write to cache
2. Return success (fast!)
3. Async write to DB (later)

Pros:
✅ Fast writes
✅ Batch DB writes

Cons:
❌ Data loss risk (if cache fails before DB write)
❌ Complex

Use: High-write workloads, can tolerate some data loss
```

```
4. Refresh-Ahead:
─────────────────────────────────────────────────────────────
Predict and refresh cache before expiry

```

```
• Refresh popular items before expiry
• Based on access patterns
• Proactive approach

Pros:
✅ No cache misses for popular data
✅ Always fast

Cons:
❌ Complex prediction
❌ Waste resources on wrong predictions

Use: Predictable access patterns
```

```
╔════════════════════════════════════════════════════════════╗
║                   CACHE EVICTION POLICIES                  ║
╚════════════════════════════════════════════════════════════╝

When cache is full, what to remove?

1. LRU (Least Recently Used):
─────────────────────────────────────────────────────────────
Remove least recently accessed item

Timeline: A(5min) → B(2min) → C(1min) → D(now)
Remove: A (accessed 5 minutes ago)

Most common policy

2. LFU (Least Frequently Used):
─────────────────────────────────────────────────────────────
Remove least frequently accessed item

Access count: A(100) B(50) C(10) D(5)
Remove: D (only accessed 5 times)

3. FIFO (First In, First Out):
─────────────────────────────────────────────────────────────
Remove oldest item

Order: A → B → C → D
Remove: A (first added)

4. TTL (Time To Live):
─────────────────────────────────────────────────────────────
Remove after expiration time

Item A: expires in 5 minutes
Item B: expires in 10 minutes

╔════════════════════════════════════════════════════════════╗
║                   CACHE LEVELS                             ║
╚════════════════════════════════════════════════════════════╝

Multi-Level Caching:
─────────────────────────────────────────────────────────────
```

```
┌──────────┐
│ Client   │
└────┬─────┘
     │
     ▼
┌──────────┐  ← Browser Cache (fastest, smallest)
│ Browser  │
└────┬─────┘
     │
     ▼
┌──────────┐  ← CDN Cache (fast, global)
│   CDN    │
└────┬─────┘
     │
     ▼
┌──────────┐  ← Application Cache (Redis/Memcached)
│  Server  │
└────┬─────┘
     │
     ▼
┌──────────┐  ← Database Cache (query cache)
│ Database │
└──────────┘
```

```
1. Client-Side:
   • Browser cache
   • LocalStorage
   • Service Workers
   Speed: Instant

2. CDN:
   • Static assets
   • Edge locations
   Speed: 10-50ms

3. Application:
   • Redis, Memcached
   • In-memory
   Speed: 1-5ms

4. Database:
   • Query cache
   • Index cache
   Speed: 10-50ms

╔════════════════════════════════════════════════════════════╗
║                   POPULAR CACHING SOLUTIONS                ║
╚════════════════════════════════════════════════════════════╝

Redis:
─────────────────────────────────────────────────────────────
⭐⭐⭐⭐⭐ Most Popular

Pros:
✅ Fast (in-memory)
✅ Rich data structures (strings, lists, sets, hashes)
✅ Persistence options
✅ Pub/Sub messaging
✅ Atomic operations
✅ Clustering support

Use: General-purpose caching, sessions, real-time

Memcached:
─────────────────────────────────────────────────────────────
⭐⭐⭐⭐ Simple & Fast

Pros:
✅ Very fast
✅ Simple (key-value only)
✅ Multi-threaded
✅ Lower memory footprint

Cons:
❌ Only key-value
❌ No persistence
❌ No advanced features

Use: Simple caching needs

Comparison:
─────────────────────────────────────────────────────────────
Redis: Feature-rich, versatile
Memcached: Simple, slightly faster for basic ops

Most choose: Redis (more features, similar speed)

╔════════════════════════════════════════════════════════════╗
║                   CACHE PROBLEMS                           ║
╚════════════════════════════════════════════════════════════╝

1. Cache Stampede:
─────────────────────────────────────────────────────────────
Problem: Popular item expires, many requests hit DB

```

```
Cache expires → 1000 requests → All hit DB!
          ↓
     DB overload!

Solution:
• Lock on cache miss (only 1 request fetches)
• Probabilistic early expiration
• Background refresh
```

```
2. Cache Penetration:
─────────────────────────────────────────────────────────────
Problem: Requests for non-existent data (bypass cache)

```

```
Request for user_id=9999 (doesn't exist)
→ Cache miss
→ DB query returns null
→ Doesn't cache null
→ Next request repeats!

Solution:
• Cache null results (short TTL)
• Bloom filter (check existence before query)
```

```
3. Cache Avalanche:
─────────────────────────────────────────────────────────────
Problem: Many items expire at once

```

```
All cached items expire at midnight
→ All requests hit DB
→ DB overload!

Solution:
• Randomize expiration times
• Don't set same TTL for everything
```

```
Best Practices:
─────────────────────────────────────────────────────────────
✅ Set appropriate TTL (not too short, not too long)
✅ Monitor cache hit rate (> 80% is good)
✅ Use consistent hashing for distributed cache
✅ Handle cache failures gracefully
✅ Don't cache everything (cost vs benefit)
✅ Cache immutable data longer
✅ Use compression for large values
```

---

<div align="center">

## 💾 Database Design

</div>

### Store and Query Data Efficiently 📊

```
# ═══════════════════════════════════════════
# DATABASE STRATEGIES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SQL vs NoSQL                             ║
╚════════════════════════════════════════════════════════════╝

SQL (Relational):
─────────────────────────────────────────────────────────────
Structured data, relationships, ACID transactions

Examples: PostgreSQL, MySQL, Oracle

```

```
Users Table:
┌────┬──────┬─────────────────┐
│ ID │ Name │ Email           │
├────┼──────┼─────────────────┤
│ 1  │ John │ john@email.com  │
│ 2  │ Jane │ jane@email.com  │
└────┴──────┴─────────────────┘

Orders Table:
┌────┬─────────┬────────┐
│ ID │ User_ID │ Amount │
├────┼─────────┼────────┤
│ 1  │ 1       │ 100    │
│ 2  │ 1       │ 200    │
└────┴─────────┴────────┘

Related by foreign keys
```

```
Pros:
✅ ACID transactions (reliable)
✅ Complex queries (JOINs)
✅ Data integrity
✅ Mature tooling

Cons:
❌ Hard to scale horizontally
❌ Schema changes difficult
❌ Less flexible

Use When:
• Need transactions
• Complex relationships
• Data integrity critical
• Predictable queries

NoSQL (Non-Relational):
─────────────────────────────────────────────────────────────
Flexible schema, horizontal scaling, eventual consistency

Types:

1. Document (MongoDB, CouchDB):
```

```
{
  "id": 1,
  "name": "John",
  "email": "john@email.com",
  "orders": [
    { "id": 1, "amount": 100 },
    { "id": 2, "amount": 200 }
  ]
}

All data in one document
```

```
2. Key-Value (Redis, DynamoDB):
```

```
user:1 → { name: "John", email: "..." }
user:2 → { name: "Jane", email: "..." }

Simple lookups
```

```
3. Column-Family (Cassandra, HBase):
```

```
Row: user:1
  name: John
  email: john@email.com
  city: NYC

Wide columns, good for analytics
```

```
4. Graph (Neo4j, ArangoDB):
```

```
(John)-[:FRIENDS_WITH]->(Jane)
(John)-[:LIKES]->(Pizza)

Relationships as first-class citizens
```

```
Pros:
✅ Horizontal scaling
✅ Flexible schema
✅ High performance
✅ Handle massive data

Cons:
❌ No ACID (usually)
❌ Limited query capabilities
❌ Eventual consistency

Use When:
• Need to scale massively
• Flexible schema
• Simple queries
• High write throughput

Decision Matrix:
─────────────────────────────────────────────────────────────
```

| Requirement        | SQL | NoSQL |
| ------------------ | --- | ----- |
| Complex queries    | ✅  | ❌    |
| Transactions       | ✅  | ❌    |
| Horizontal scaling | ❌  | ✅    |
| Flexible schema    | ❌  | ✅    |
| High writes        | ❌  | ✅    |
| Data integrity     | ✅  | ❌    |

```
╔════════════════════════════════════════════════════════════╗
║                   DATABASE SCALING                         ║
╚════════════════════════════════════════════════════════════╝

1. Replication:
─────────────────────────────────────────────────────────────
Copy data to multiple databases

Master-Slave:
```

```
       ┌────────┐
       │ Master │ ← All writes
       └───┬────┘
           │
    ┌──────┴──────┐
    ▼             ▼
┌───────┐     ┌───────┐
│Slave 1│     │Slave 2│ ← All reads
└───────┘     └───────┘

Pros:
✅ Read scalability
✅ Backup/redundancy
✅ No downtime for reads

Cons:
❌ Replication lag
❌ Write bottleneck (single master)
```

```
Master-Master:
```

```
┌────────┐ ←→ ┌────────┐
│Master 1│    │Master 2│
└────────┘    └────────┘
Both can read/write

Pros:
✅ Write scalability
✅ High availability

Cons:
❌ Conflict resolution
❌ Complex
```

```
2. Sharding (Horizontal Partitioning):
─────────────────────────────────────────────────────────────
Split data across multiple databases

```

```
        ┌─────────────┐
        │  App Server │
        └──────┬──────┘
               │
     ┌─────────┼─────────┐
     ▼         ▼         ▼
┌─────────┐┌─────────┐┌─────────┐
│Shard 1  ││Shard 2  ││Shard 3  │
│Users    ││Users    ││Users    │
│1-1000   ││1001-2000││2001-3000│
└─────────┘└─────────┘└─────────┘
```

```
Sharding Strategies:

a) Range-Based:
   User 1-1000 → Shard 1
   User 1001-2000 → Shard 2

   Simple but uneven distribution

b) Hash-Based:
   hash(user_id) % num_shards = shard

   Even distribution but hard to add shards

c) Geographic:
   US users → US shard
   EU users → EU shard

   Low latency but uneven

d) Directory-Based:
   Lookup table: user_id → shard

   Flexible but single point of failure

Pros:
✅ Horizontal scaling
✅ High throughput
✅ Large datasets

Cons:
❌ Complex queries (cross-shard JOINs)
❌ Rebalancing difficult
❌ Transactions across shards hard

3. Partitioning:
─────────────────────────────────────────────────────────────
Split table into smaller parts (same database)

Vertical:
┌────────────┐    ┌────────────┐
│ Users      │    │ User_Prefs │
│ - id       │    │ - user_id  │
│ - name     │    │ - settings │
│ - email    │    │ - theme    │
└────────────┘    └────────────┘

Horizontal:
Users_2023 (recent)
Users_2022 (archive)
Users_2021 (archive)

╔════════════════════════════════════════════════════════════╗
║                   DATABASE INDEXING                        ║
╚════════════════════════════════════════════════════════════╝

Index:
─────────────────────────────────────────────────────────────
Data structure for fast lookups

Without Index:
SELECT * FROM users WHERE email = 'john@email.com';
→ Scan all rows (slow for millions)

With Index:
CREATE INDEX idx_email ON users(email);
→ Jump directly to row (fast!)

Types:

1. B-Tree Index (most common):
   • Sorted tree structure
   • Good for range queries
   • Default in most databases

2. Hash Index:
   • Fast equality lookups
   • No range queries

3. Full-Text Index:
   • Search text content
   • Used for search features

Trade-offs:
─────────────────────────────────────────────────────────────
Pros:
✅ Fast reads (100x faster!)
✅ Better query performance

Cons:
❌ Slower writes (update index too)
❌ Extra storage
❌ Maintenance overhead

Best Practices:
─────────────────────────────────────────────────────────────
✅ Index foreign keys
✅ Index frequently queried columns
✅ Composite indexes for multiple columns
❌ Don't index everything (slow writes)
❌ Don't index low-cardinality columns (gender, boolean)
```

---

<div align="center">

## 🌐 Content Delivery Networks

</div>

### Serve Content Globally Fast 🌍

```
# ═══════════════════════════════════════════
# CDN (CONTENT DELIVERY NETWORK)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WHAT IS A CDN?                           ║
╚════════════════════════════════════════════════════════════╝

CDN:
─────────────────────────────────────────────────────────────
Network of servers globally that cache and serve content
from locations closest to users

```

```
Without CDN:                  With CDN:
┌─────────┐                   ┌─────────┐
│User (US)│                   │User (US)│
└────┬────┘                   └────┬────┘
     │ 200ms                       │ 10ms
     ▼                             ▼
┌──────────┐                  ┌─────────┐
│Server    │                  │CDN (US) │
│(Asia)    │                  └─────────┘
└──────────┘

20x faster with CDN!
```

```
Benefits:
─────────────────────────────────────────────────────────────
✅ Faster content delivery (lower latency)
✅ Reduce server load (CDN serves)
✅ Handle traffic spikes
✅ Global reach
✅ DDoS protection
✅ Save bandwidth costs

What to Cache on CDN:
─────────────────────────────────────────────────────────────
✅ Images, videos
✅ CSS, JavaScript
✅ HTML (static pages)
✅ Downloads (PDFs, files)
✅ API responses (cacheable)

❌ User-specific data
❌ Sensitive information
❌ Real-time data
❌ Frequently changing content

Popular CDNs:
─────────────────────────────────────────────────────────────
• Cloudflare (most popular)
• AWS CloudFront
• Fastly
• Akamai
• Google Cloud CDN

How It Works:
─────────────────────────────────────────────────────────────
1. User requests image.jpg
2. DNS routes to nearest CDN edge server
3. If cached → serve immediately (hit)
4. If not → fetch from origin, cache, serve (miss)
5. Next request → served from cache
```

---

<div align="center">

## 📬 Message Queues

</div>

### Asynchronous Communication 📨

```
# ═══════════════════════════════════════════
# MESSAGE QUEUES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WHAT IS A MESSAGE QUEUE?                 ║
╚════════════════════════════════════════════════════════════╝

Message Queue:
─────────────────────────────────────────────────────────────
Asynchronous communication between services

```

```
Without Queue:                With Queue:
┌────────┐                    ┌────────┐
│Request │                    │Request │
└───┬────┘                    └───┬────┘
    │                             │
    ▼                             ▼
┌──────────┐                  ┌──────────┐
│  Server  │                  │  Server  │
└───┬──────┘                  └───┬──────┘
    │ Wait...                     │ Return immediately!
    ▼                             ▼
┌──────────┐                  ┌─────────┐
│Send Email│                  │  Queue  │
└──────────┘                  └────┬────┘
(Blocks!)                          │ Async
                                   ▼
                              ┌──────────┐
                              │  Worker  │
                              └────┬─────┘
                                   ▼
                              ┌──────────┐
                              │Send Email│
                              └──────────┘
```

```
Benefits:
─────────────────────────────────────────────────────────────
✅ Async processing (don't wait)
✅ Decouple services
✅ Handle traffic spikes (queue buffers)
✅ Retry failed operations
✅ Scale independently
✅ Fault tolerance

Use Cases:
─────────────────────────────────────────────────────────────
• Email sending
• Image processing
• Video encoding
• Report generation
• Notifications
• Background tasks
• Data processing

Popular Message Queues:
─────────────────────────────────────────────────────────────
• RabbitMQ (most popular)
• Apache Kafka (high-throughput)
• AWS SQS
• Redis (Pub/Sub)
• Google Cloud Pub/Sub

Patterns:
─────────────────────────────────────────────────────────────

1. Queue (Point-to-Point):
```

```
Producer → [Queue] → Consumer

One message → One consumer
```

```
2. Pub/Sub (Publish/Subscribe):
```

```
                    ┌→ Subscriber 1
Publisher → [Topic] ├→ Subscriber 2
                    └→ Subscriber 3

One message → All subscribers
```

---

<div align="center">

## 🔧 Microservices Architecture

</div>

### Break Down Monoliths 🏗️

```
# ═══════════════════════════════════════════
# MICROSERVICES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   MONOLITH vs MICROSERVICES                ║
╚════════════════════════════════════════════════════════════╝

Monolith:
─────────────────────────────────────────────────────────────
All code in one application

```

```
┌────────────────────────────┐
│      Monolithic App        │
│  ┌──────────────────────┐  │
│  │ User Management      │  │
│  ├──────────────────────┤  │
│  │ Product Catalog      │  │
│  ├──────────────────────┤  │
│  │ Order Processing     │  │
│  ├──────────────────────┤  │
│  │ Payment              │  │
│  └──────────────────────┘  │
└──────────┬─────────────────┘
           ▼
      ┌─────────┐
      │Database │
      └─────────┘

Pros:
✅ Simple to develop
✅ Easy to test
✅ Easy to deploy (one unit)
✅ No network overhead

Cons:
❌ Hard to scale
❌ Long deployment times
❌ One bug can crash everything
❌ Technology lock-in
❌ Hard to understand (as it grows)
```

```
Microservices:
─────────────────────────────────────────────────────────────
Split into independent services

```

```
┌──────────┐  ┌──────────┐  ┌──────────┐  ┌─────────┐
│  User    │  │ Product  │  │  Order   │  │ Payment │
│ Service  │  │ Service  │  │ Service  │  │ Service │
└────┬─────┘  └────┬─────┘  └────┬─────┘  └────┬────┘
     │             │             │             │
     ▼             ▼             ▼             ▼
 ┌────────┐   ┌────────┐   ┌────────┐   ┌────────┐
 │  DB 1  │   │  DB 2  │   │  DB 3  │   │  DB 4  │
 └────────┘   └────────┘   └────────┘   └────────┘

Each service: Own database, own deployment

Pros:
✅ Scale independently
✅ Deploy independently
✅ Technology flexibility
✅ Team autonomy
✅ Fault isolation

Cons:
❌ Complex (distributed system)
❌ Network latency
❌ Data consistency challenges
❌ More operational overhead
❌ Harder to test

When to Use Microservices:
─────────────────────────────────────────────────────────────
✅ Large team (50+ developers)
✅ Need independent scaling
✅ Different technologies per service
✅ Mature DevOps
✅ Can handle complexity

Start with Monolith:
❌ Small team
❌ New product (uncertain requirements)
❌ Simple domain
❌ Limited resources

"You must be this tall to use microservices"
- Martin Fowler

╔════════════════════════════════════════════════════════════╗
║                   API GATEWAY                              ║
╚════════════════════════════════════════════════════════════╝

API Gateway:
─────────────────────────────────────────────────────────────
Single entry point for all clients

```

```
┌─────────┐
│ Clients │
└────┬────┘
     │
     ▼
┌──────────────┐  ← Single Entry Point
│ API Gateway  │
└──────┬───────┘
       │
   ┌───┴───┬───────┬──────┐
   ▼       ▼       ▼      ▼
┌─────┐ ┌─────┐ ┌─────┐ ┌─────┐
│User │ │Order│ │Pay  │ │Notif│
└─────┘ └─────┘ └─────┘ └─────┘

Benefits:
✅ Single entry point
✅ Authentication/Authorization
✅ Rate limiting
✅ Request routing
✅ Load balancing
✅ Caching
✅ Logging/Monitoring
✅ Protocol translation

Popular:
• Kong
• AWS API Gateway
• Azure API Management
• Google Cloud Endpoints
```

---

<div align="center">

## 🎯 System Design Process

</div>

### How to Approach Design Problems 📝

```
# ═══════════════════════════════════════════
# SYSTEM DESIGN INTERVIEW PROCESS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   STEP-BY-STEP PROCESS                     ║
╚════════════════════════════════════════════════════════════╝

Step 1: Understand Requirements (5 min)
─────────────────────────────────────────────────────────────

Functional Requirements:
• What features does system need?
• What should users be able to do?

Example: Design Twitter
✅ Post tweets (140 chars)
✅ Follow users
✅ View timeline (tweets from followed users)
✅ Like tweets
❌ DMs (out of scope for interview)
❌ Trending topics (out of scope)

Non-Functional Requirements:
• Scale (users, data)
• Performance
• Availability
• Consistency

Example:
• 100M daily active users
• 200M tweets per day
• Read-heavy (100:1 read/write ratio)
• Low latency (< 200ms)
• High availability (99.99%)
• Eventual consistency OK

Ask Clarifying Questions:
─────────────────────────────────────────────────────────────
❓ How many users?
❓ Read-heavy or write-heavy?
❓ What's the traffic pattern?
❓ Data retention?
❓ Real-time or can be delayed?
❓ Global or regional?
❓ Mobile, web, or both?

Step 2: Back-of-the-Envelope Estimation (5 min)
─────────────────────────────────────────────────────────────

Calculate:
• QPS (Queries Per Second)
• Storage
• Bandwidth

Example: Twitter-like service

Given:
• 100M DAU
• Each user posts 2 tweets/day
• Each user views 100 tweets/day
• 10% tweets have media (image)

Write QPS:
100M users × 2 tweets = 200M tweets/day
200M / 86,400 seconds ≈ 2,300 tweets/sec

Read QPS:
100M users × 100 views = 10B views/day
10B / 86,400 ≈ 115,000 views/sec

Storage (per day):
Text: 200M × 280 bytes ≈ 56 GB
Media: 20M × 200 KB ≈ 4 TB
Total: ~4 TB/day

Over 5 years:
4 TB × 365 × 5 = 7.3 PB

Bandwidth:
Peak QPS × Average response size
115K × 1 KB = 115 MB/sec

Step 3: High-Level Design (10 min)
─────────────────────────────────────────────────────────────

Draw basic architecture:

```

```
┌──────────┐
│  Client  │
└─────┬────┘
      │
      ▼
┌──────────┐     ┌────────┐
│   CDN    │────▶│ Static │
└─────┬────┘     └────────┘
      │
      ▼
┌──────────┐
│   DNS    │
└─────┬────┘
      │
      ▼
┌──────────┐     ┌────────┐
│   Load   │────▶│ Cache  │
│ Balancer │     │(Redis) │
└─────┬────┘     └────────┘
      │
  ┌───┴───┐
  ▼       ▼
┌─────┐ ┌─────┐
│Web  │ │Web  │
│Srvr1│ │Srvr2│
└──┬──┘ └──┬──┘
   │       │
   └───┬───┘
       ▼
┌──────────┐     ┌────────┐
│   App    │────▶│Message │
│ Servers  │     │ Queue  │
└─────┬────┘     └────────┘
      │
      ▼
┌──────────┐
│ Database │
│(Sharded) │
└──────────┘
```

```
Components:
• Load Balancer
• Web Servers
• Application Servers
• Cache
• Database
• Message Queue

Step 4: Deep Dive (15-20 min)
─────────────────────────────────────────────────────────────

Interviewer will ask about specific components:

1. How to handle writes at scale?
   → Sharding, message queues

2. How to handle reads at scale?
   → Caching, replication, CDN

3. How to ensure availability?
   → Redundancy, failover, health checks

4. How to handle real-time updates?
   → WebSockets, Server-Sent Events, Long polling

5. How to store data efficiently?
   → Database choice, indexing, partitioning

Example Deep Dive: Timeline Generation

Problem: How to show user's timeline (tweets from followed users)?

Approach 1: Fan-out on Read
```

```
User requests timeline
→ Get list of followed users
→ Query tweets from each
→ Merge and sort
→ Return

Pros: ✅ Fast writes
Cons: ❌ Slow reads (if following many users)
```

```
Approach 2: Fan-out on Write
```

```
User posts tweet
→ Find all followers
→ Insert tweet into each follower's timeline cache
→ Done

User requests timeline
→ Read from pre-computed cache
→ Fast!

Pros: ✅ Fast reads
Cons: ❌ Slow writes (celebrities with millions)
```

```
Hybrid Approach (Best):
```

```
Regular users: Fan-out on write
Celebrities: Fan-out on read
```

```
Step 5: Identify Bottlenecks (5 min)
─────────────────────────────────────────────────────────────

Discuss:
• Single points of failure
• Scalability limits
• Performance bottlenecks

Solutions:
• Add redundancy (multiple instances)
• Add caching
• Add load balancing
• Shard database
• Use CDN
• Add monitoring

╔════════════════════════════════════════════════════════════╗
║                   COMMON INTERVIEW SYSTEMS                 ║
╚════════════════════════════════════════════════════════════╝

Popular Interview Questions:
─────────────────────────────────────────────────────────────
• Design Twitter
• Design Instagram
• Design Netflix
• Design Uber
• Design WhatsApp
• Design URL Shortener
• Design Rate Limiter
• Design Web Crawler
• Design YouTube
• Design Dropbox

Key Concepts to Know:
─────────────────────────────────────────────────────────────
✅ Load balancing
✅ Caching
✅ Database sharding
✅ Replication
✅ CAP theorem
✅ Consistent hashing
✅ Message queues
✅ CDN
✅ API Gateway
✅ Microservices

Do's and Don'ts:
─────────────────────────────────────────────────────────────

DO:
✅ Ask clarifying questions
✅ Define requirements clearly
✅ Start with high-level design
✅ Discuss trade-offs
✅ Think out loud
✅ Use diagrams
✅ Consider scalability
✅ Acknowledge limitations

DON'T:
❌ Jump into implementation details
❌ Assume requirements
❌ Design for perfection (overengineering)
❌ Stay silent
❌ Ignore interviewer feedback
❌ Use buzzwords without understanding
```

---

<div align="center">

## 📱 Real-World Examples

</div>

### Learn from Industry Giants 🏢

```
# ═══════════════════════════════════════════
# REAL-WORLD SYSTEM DESIGNS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   DESIGN: URL SHORTENER                    ║
╚════════════════════════════════════════════════════════════╝

Example: bit.ly, tinyurl.com

Requirements:
─────────────────────────────────────────────────────────────
Functional:
• Shorten URL (long → short)
• Redirect (short → long)
• Custom aliases (optional)
• Analytics (click count)

Non-Functional:
• 100M URLs created per month
• 10B redirects per month
• Low latency (< 100ms)
• High availability

Calculations:
─────────────────────────────────────────────────────────────
Write QPS: 100M / (30 × 86,400) ≈ 40 URLs/sec
Read QPS: 10B / (30 × 86,400) ≈ 3,850 redirects/sec
Read/Write ratio: 100:1 (read-heavy!)

Storage:
• URL: 500 bytes average
• 100M × 500 bytes = 50 GB/month
• Over 10 years: 6 TB

URL Encoding:
─────────────────────────────────────────────────────────────
Short URL length: 7 characters
Character set: [a-z, A-Z, 0-9] = 62 characters
Possible URLs: 62^7 = 3.5 trillion (enough!)

Example: https://short.url/abc123d

Algorithm:
─────────────────────────────────────────────────────────────

Option 1: Hash
```

```
MD5(long_url) → take first 7 chars
Problem: Collisions!
Solution: Add counter if collision
```

```
Option 2: Base62 Encoding
```

```
Auto-increment ID → Convert to base62
ID: 12345 → base62: "3D7"

Pros: No collisions, predictable
Cons: Sequential (can guess next)
```

```
Option 3: Random + Check
```

```
Generate random 7-char string
Check if exists in DB
If yes → retry
If no → use it

Pros: Random, secure
Cons: Slight chance of retry
```

```
Architecture:
─────────────────────────────────────────────────────────────
```

```
┌────────┐
│ Client │
└───┬────┘
    │
    ▼
┌─────────────┐
│Load Balancer│
└───┬─────────┘
    │
┌───┴───┐
│       │
▼       ▼
┌────┐ ┌────┐
│API │ │API │
│Srvr│ │Srvr│
└─┬──┘ └─┬──┘
  │      │
  └──┬───┘
     │
     ▼
┌─────────┐  ← Cache (Redis) for hot URLs
│  Cache  │
└────┬────┘
     │ (miss)
     ▼
┌─────────┐
│Database │  ← Store URL mappings
│(NoSQL)  │     short_url → long_url
└─────────┘
```

```
Database Schema:
─────────────────────────────────────────────────────────────
```

| Field      | Type          | Description   |
| ---------- | ------------- | ------------- |
| short_url  | VARCHAR(7)    | Primary key   |
| long_url   | VARCHAR(2048) | Original URL  |
| created_at | TIMESTAMP     | Creation time |
| clicks     | INT           | Click count   |

```
Optimization:
─────────────────────────────────────────────────────────────
• Cache popular URLs (80/20 rule)
• Use CDN for static assets
• Database sharding by URL hash
• Bloom filter to check existence
• Analytics via message queue (async)

╔════════════════════════════════════════════════════════════╗
║                   DESIGN: INSTAGRAM (SIMPLIFIED)           ║
╚════════════════════════════════════════════════════════════╝

Requirements:
─────────────────────────────────────────────────────────────
Functional:
• Upload photos
• Follow users
• View feed (photos from followed users)
• Like photos

Non-Functional:
• 500M daily active users
• 50M photos uploaded per day
• Read-heavy (100:1)
• High availability

Key Challenges:
─────────────────────────────────────────────────────────────
1. Store massive photos (PB scale)
2. Generate feed efficiently
3. Handle celebrity accounts

Architecture:
─────────────────────────────────────────────────────────────
```

```
┌────────┐
│ Client │
└───┬────┘
    │
    ▼
┌─────────┐
│   CDN   │  ← Serve photos (global, fast)
└────┬────┘
     │
     ▼
┌──────────┐
│   Load   │
│ Balancer │
└─────┬────┘
      │
  ┌───┴───┐
  ▼       ▼
┌─────┐ ┌─────┐
│ API │ │ API │
└──┬──┘ └──┬──┘
   │       │
   └───┬───┘
       │
   ┌───┴────┬────────┐
   ▼        ▼        ▼
┌──────┐ ┌──────┐ ┌──────┐
│Cache │ │Queue │ │Object│
│Redis │ │Kafka │ │Store │  ← Photos (S3)
└──┬───┘ └──┬───┘ └──────┘
   │        │
   └────┬───┘
        ▼
   ┌─────────┐
   │Database │  ← User data, metadata
   │(Sharded)│
   └─────────┘
```

```
Database Tables:
─────────────────────────────────────────────────────────────

Users:
• user_id (PK)
• username
• email
• created_at

Photos:
• photo_id (PK)
• user_id (FK)
• s3_url
• caption
• created_at

Follows:
• follower_id (FK)
• followee_id (FK)
• created_at

Likes:
• user_id (FK)
• photo_id (FK)
• created_at

Feed Generation:
─────────────────────────────────────────────────────────────
```

```
User opens app
→ Check Redis cache for pre-computed feed
→ If hit: Return immediately
→ If miss: Generate feed
    1. Get followed users
    2. Get recent photos from followed users
    3. Sort by time
    4. Cache result (expire in 10 min)
    5. Return

Background job:
• Pre-compute feeds for active users
• Update every 5-10 minutes
• Use fan-out on write for regular users
• Use fan-out on read for celebrities
```

```
Photo Storage:
─────────────────────────────────────────────────────────────
1. Client uploads photo
2. API server generates pre-signed URL
3. Client uploads directly to S3
4. API server saves metadata to DB
5. Async: Generate thumbnails (multiple sizes)
6. CDN pulls from S3
7. Future requests served from CDN

Scalability:
─────────────────────────────────────────────────────────────
• Object storage (S3): Unlimited photos
• Database sharding: By user_id
• Cache: Hot photos and feeds
• CDN: Global photo delivery
• Message queue: Async processing

╔════════════════════════════════════════════════════════════╗
║                   DESIGN: RATE LIMITER                     ║
╚════════════════════════════════════════════════════════════╝

Purpose:
─────────────────────────────────────────────────────────────
Limit number of requests per user/IP to prevent abuse

Requirements:
─────────────────────────────────────────────────────────────
• Limit: 100 requests per minute per user
• Return error if exceeded
• Low latency (< 10ms)
• Distributed (multiple servers)

Algorithms:
─────────────────────────────────────────────────────────────

1. Token Bucket (Most Common):
```

```
Bucket capacity: 100 tokens
Refill rate: 100 tokens/minute

Request comes in:
→ Check bucket
→ If tokens available: Remove 1 token, allow
→ If empty: Reject (429 Too Many Requests)

Pros: ✅ Smooth rate limiting
      ✅ Handles bursts
```

```
2. Fixed Window:
```

```
Window: 1 minute
Count: Requests in current minute

00:00-00:59 → Count up to 100
01:00-01:59 → Reset counter, count again

Pros: ✅ Simple
Cons: ❌ Burst at window edge (99 at 00:59, 100 at 01:00)
```

```
3. Sliding Window Log:
```

```
Keep timestamp of each request
On new request:
→ Remove old requests (> 1 min ago)
→ Count remaining
→ If < 100: Allow
→ If >= 100: Reject

Pros: ✅ Accurate
Cons: ❌ Memory intensive (store all timestamps)
```

```
Implementation with Redis:
─────────────────────────────────────────────────────────────
```

```python
import redis
import time

redis_client = redis.Redis()

def is_allowed(user_id, limit=100, window=60):
    key = f"rate_limit:{user_id}"
    current = int(time.time())

    # Token bucket implementation
    pipe = redis_client.pipeline()

    # Get last refill time and tokens
    last_refill = redis_client.get(f"{key}:last_refill") or current
    tokens = redis_client.get(f"{key}:tokens") or limit

    # Refill tokens
    time_passed = current - int(last_refill)
    tokens_to_add = (time_passed / window) * limit
    tokens = min(limit, int(tokens) + tokens_to_add)

    # Check if request allowed
    if tokens >= 1:
        tokens -= 1
        redis_client.set(f"{key}:tokens", tokens)
        redis_client.set(f"{key}:last_refill", current)
        return True

    return False

# Usage
if is_allowed(user_id):
    # Process request
    pass
else:
    # Return 429 Too Many Requests
    pass
```

```
Distributed Rate Limiting:
─────────────────────────────────────────────────────────────
```

```
Challenge: Multiple servers, shared counter

Solution: Centralized Redis

┌────────┐  ┌────────┐  ┌────────┐
│Server 1│  │Server 2│  │Server 3│
└───┬────┘  └───┬────┘  └───┬────┘
    │           │           │
    └───────────┼───────────┘
                ▼
          ┌──────────┐
          │  Redis   │  ← Shared counter
          │(Cluster) │
          └──────────┘

All servers check same Redis counter
Atomic operations ensure accuracy
```

---

<div align="center">

## 💡 Best Practices

</div>

### System Design Wisdom 🎓

```
# ═══════════════════════════════════════════
# SYSTEM DESIGN BEST PRACTICES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   DESIGN PRINCIPLES                        ║
╚════════════════════════════════════════════════════════════╝

1. KISS (Keep It Simple, Stupid):
─────────────────────────────────────────────────────────────
✅ Start simple
✅ Add complexity only when needed
❌ Don't over-engineer

Example:
• Start: Single server + database
• Growing: Add caching
• Scale: Add load balancer, replicas
• Large scale: Sharding, microservices

2. YAGNI (You Aren't Gonna Need It):
─────────────────────────────────────────────────────────────
✅ Build what you need now
✅ Don't build for "what if"
❌ Premature optimization

3. Fail Fast:
─────────────────────────────────────────────────────────────
✅ Validate inputs early
✅ Return errors quickly
✅ Don't waste resources on bad requests

4. Design for Failure:
─────────────────────────────────────────────────────────────
✅ Assume everything can fail
✅ Add redundancy
✅ Graceful degradation
✅ Circuit breakers

5. Separate Concerns:
─────────────────────────────────────────────────────────────
✅ Each component does one thing
✅ Loose coupling
✅ Easy to maintain and scale

╔════════════════════════════════════════════════════════════╗
║                   SCALABILITY CHECKLIST                    ║
╚════════════════════════════════════════════════════════════╝

Before Launch:
─────────────────────────────────────────────────────────────
☐ Stateless servers
☐ Load balancer configured
☐ Database indexed properly
☐ Caching strategy
☐ CDN for static assets
☐ Monitoring and logging
☐ Auto-scaling rules
☐ Backup strategy

Growing (1K-100K users):
─────────────────────────────────────────────────────────────
☐ Database replication
☐ Cache layer (Redis)
☐ Asynchronous processing
☐ Message queues
☐ Rate limiting
☐ API versioning

Large Scale (100K+ users):
─────────────────────────────────────────────────────────────
☐ Database sharding
☐ Microservices (if needed)
☐ Multiple data centers
☐ Geographic distribution
☐ Advanced monitoring
☐ Chaos engineering
☐ Cost optimization

╔════════════════════════════════════════════════════════════╗
║                   COMMON MISTAKES                          ║
╚════════════════════════════════════════════════════════════╝

1. Premature Optimization:
─────────────────────────────────────────────────────────────
❌ Sharding from day one
❌ Microservices for 3 developers
❌ Complex caching strategies for 10 users

Start simple, scale when needed!

2. Single Point of Failure:
─────────────────────────────────────────────────────────────
❌ Single database (no replication)
❌ Single load balancer
❌ No fallback

Add redundancy for critical components!

3. Not Monitoring:
─────────────────────────────────────────────────────────────
❌ No metrics
❌ No alerts
❌ No logging

"You can't improve what you don't measure"

4. Ignoring Security:
─────────────────────────────────────────────────────────────
❌ No rate limiting
❌ No authentication
❌ No encryption

Security from the start!

5. Not Planning for Failure:
─────────────────────────────────────────────────────────────
❌ No retry logic
❌ No circuit breakers
❌ No graceful degradation

Everything fails eventually!

╔════════════════════════════════════════════════════════════╗
║                   TRADE-OFFS TO CONSIDER                   ║
╚════════════════════════════════════════════════════════════╝

Consistency vs Availability:
─────────────────────────────────────────────────────────────
Consistency: All nodes see same data
Availability: Always responds

Choose based on use case:
• Banking: Consistency (can't show wrong balance)
• Social media: Availability (OK to see old post)

Latency vs Throughput:
─────────────────────────────────────────────────────────────
Latency: How fast (single request)
Throughput: How many (total requests)

Balance:
• Real-time: Low latency priority
• Batch: High throughput priority

Cost vs Performance:
─────────────────────────────────────────────────────────────
Better performance = More money

Optimize:
• Cache to reduce DB queries (save cost)
• CDN for static assets (faster + cheaper)
• Auto-scaling (pay for what you use)

Complexity vs Features:
─────────────────────────────────────────────────────────────
More features = More complexity

Keep it simple:
• MVP first
• Add features gradually
• Measure impact

╔════════════════════════════════════════════════════════════╗
║                   LEARNING RESOURCES                       ║
╚════════════════════════════════════════════════════════════╝

Books:
─────────────────────────────────────────────────────────────
📚 "Designing Data-Intensive Applications" - Martin Kleppmann
📚 "System Design Interview" - Alex Xu (Volumes 1 & 2)
📚 "Building Microservices" - Sam Newman
📚 "Site Reliability Engineering" - Google

Websites:
─────────────────────────────────────────────────────────────
🔗 highscalability.com (Real-world architectures)
🔗 github.com/donnemartin/system-design-primer
🔗 systemdesign.one
🔗 bytebytego.com

Practice:
─────────────────────────────────────────────────────────────
💪 Design systems you use daily
💪 Mock interviews (Pramp, Exponent)
💪 Read tech blogs (Netflix, Uber, Airbnb)
💪 Build and deploy projects
💪 Learn from failures

╔════════════════════════════════════════════════════════════╗
║                   FINAL WISDOM                             ║
╚════════════════════════════════════════════════════════════╝

Key Takeaways:
─────────────────────────────────────────────────────────────
✅ Start simple, scale gradually
✅ Understand requirements first
✅ Make trade-offs consciously
✅ Design for failure
✅ Measure everything
✅ Learn from real systems
✅ Practice, practice, practice

Remember:
─────────────────────────────────────────────────────────────
"Premature optimization is the root of all evil."
- Donald Knuth

"Make it work, make it right, make it fast."
- Kent Beck

"The best system design is one that solves
the actual problem, not an imaginary one."

"You don't need microservices for 100 users.
You don't need sharding for 10,000 users.
You don't need multiple data centers for 100,000 users.

Start small. Scale when needed.
Complexity is your enemy."

Now go design amazing systems! 🚀
```

---

<div align="center">

## 📊 Quick Reference

</div>

### System Design Cheat Sheet 📝

| Component                | Purpose                       | When to Use         | Examples                |
| ------------------------ | ----------------------------- | ------------------- | ----------------------- |
| **Load Balancer**        | Distribute traffic            | Multiple servers    | Nginx, HAProxy, ELB     |
| **Cache**                | Speed up reads                | Frequent queries    | Redis, Memcached        |
| **CDN**                  | Serve static content globally | Images, videos, CSS | Cloudflare, CloudFront  |
| **Message Queue**        | Async processing              | Background tasks    | RabbitMQ, Kafka, SQS    |
| **Database Replication** | Read scaling                  | Read-heavy          | Master-Slave setup      |
| **Database Sharding**    | Write scaling                 | Huge data           | Horizontal partitioning |
| **Microservices**        | Independent scaling           | Large teams         | Service-oriented        |
| **API Gateway**          | Single entry point            | Microservices       | Kong, AWS API Gateway   |

### Scalability Numbers

| Metric                 | Value                       | Context    |
| ---------------------- | --------------------------- | ---------- |
| 99.9% uptime           | 8.76 hours downtime/year    | Standard   |
| 99.99% uptime          | 52.56 minutes downtime/year | Critical   |
| RAM access             | 100 ns                      | Very fast  |
| SSD access             | 150 μs                      | Fast       |
| Network in datacenter  | 0.5 ms                      | Acceptable |
| HDD access             | 10 ms                       | Slow       |
| Network across regions | 50-100 ms                   | Noticeable |

---

<div align="center">

**Built with 🏗️ by MrDib, for system architects**

_Remember: "Start simple, scale smart!"_ ✨

**Happy Designing!** 🚀

</div>

---

## 🔗 Related Guides

- [Design Patterns](./Design-Patterns.md)
- [Microservices](./Microservices.md)
- [Best Practices](./Best-Practices.md)
- [Database Design](../Backend/Databases.md)

---

## 📖 Interview Prep

### Top 10 Systems to Practice:

1. ✅ **URL Shortener** (Easy - Start here!)
2. ✅ **Rate Limiter** (Easy/Medium)
3. ✅ **Twitter/X** (Medium)
4. ✅ **Instagram** (Medium)
5. ✅ **YouTube** (Medium/Hard)
6. ✅ **Uber** (Hard)
7. ✅ **WhatsApp** (Hard)
8. ✅ **Netflix** (Hard)
9. ✅ **Web Crawler** (Medium)
10. ✅ **Notification System** (Medium)

### Study Plan (4 weeks):

- **Week 1**: Fundamentals (caching, load balancing, databases)
- **Week 2**: Practice 3 easy systems
- **Week 3**: Practice 3 medium systems
- **Week 4**: Practice 2 hard systems + mock interviews

---
