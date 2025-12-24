<div align="center">

# ⚡ Performance Testing

### _Because slow apps lose users, fast apps win hearts_ 🚀

![Performance](https://img.shields.io/badge/Performance-Testing-red?style=for-the-badge)
![k6](https://img.shields.io/badge/k6-Latest-purple?style=for-the-badge&logo=k6)
![Speed](https://img.shields.io/badge/Speed-Optimized-green?style=for-the-badge)

</div>

---

## 📚 Table of Contents

- [🎯 Performance Testing Fundamentals](#-performance-testing-fundamentals)
- [🦗 k6 Load Testing](#-k6-load-testing)
- [🎯 Artillery Testing](#-artillery-testing)
- [🌐 Frontend Performance](#-frontend-performance)
- [📊 API Performance](#-api-performance)
- [🔍 Monitoring & Metrics](#-monitoring--metrics)
- [🚀 CI/CD Integration](#-cicd-integration)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 🎯 Performance Testing Fundamentals

</div>

### Understanding Performance Testing 📖

```javascript
// ═══════════════════════════════════════════
// What is Performance Testing?
// ═══════════════════════════════════════════

/*
Performance testing validates:
- Response time under load
- System stability
- Scalability limits
- Resource utilization
- User experience quality

Why it matters:
- 1 second delay = 7% fewer conversions
- 53% of users abandon slow sites (>3s)
- Page speed affects SEO rankings
- Poor performance costs money
*/

// ═══════════════════════════════════════════
// Types of Performance Testing
// ═══════════════════════════════════════════

/*
1. Load Testing
   - Normal expected load
   - Verify performance under typical conditions
   - Establish baseline metrics
   - Example: 1000 concurrent users

2. Stress Testing
   - Beyond normal capacity
   - Find breaking points
   - Test recovery mechanisms
   - Example: Push until system fails

3. Spike Testing
   - Sudden load increases
   - Black Friday scenarios
   - Flash sale simulation
   - Example: 0 to 10,000 users in 1 minute

4. Endurance Testing (Soak)
   - Extended periods (hours/days)
   - Detect memory leaks
   - Resource degradation
   - Example: 500 users for 24 hours

5. Volume Testing
   - Large amounts of data
   - Database performance
   - Big data scenarios
   - Example: 10 million records

6. Scalability Testing
   - How system scales
   - Vertical vs horizontal
   - Bottleneck identification
   - Example: Add more servers

7. Capacity Testing
   - Maximum user load
   - Resource limits
   - Infrastructure planning
   - Example: How many users can we handle?
*/

// ═══════════════════════════════════════════
// Performance Metrics
// ═══════════════════════════════════════════

const keyMetrics = {
  // Response Time
  responseTime: {
    p50: "Median response time (50th percentile)",
    p90: "90% of requests faster than this",
    p95: "95% of requests faster than this",
    p99: "99% of requests faster than this",
  },

  // Throughput
  throughput: {
    rps: "Requests per second",
    tps: "Transactions per second",
    dataTransfer: "MB/s transferred",
  },

  // Error Rate
  errors: {
    errorRate: "Percentage of failed requests",
    errorTypes: "Types of errors (4xx, 5xx)",
    timeouts: "Requests that timed out",
  },

  // Concurrency
  concurrency: {
    activeUsers: "Concurrent virtual users",
    activeConnections: "Open connections",
    queueLength: "Requests waiting",
  },

  // Resource Utilization
  resources: {
    cpu: "CPU usage percentage",
    memory: "RAM usage",
    disk: "Disk I/O",
    network: "Network bandwidth",
  },
};

// ═══════════════════════════════════════════
// Performance Testing Tools Comparison
// ═══════════════════════════════════════════

/*
k6:
  ✅ Modern, developer-friendly
  ✅ JavaScript scripting
  ✅ Great metrics
  ✅ Cloud & open-source
  ❌ Newer ecosystem

Artillery:
  ✅ Simple YAML config
  ✅ Quick to start
  ✅ Good for APIs
  ❌ Less flexible than k6

JMeter:
  ✅ Industry standard
  ✅ Extensive plugins
  ✅ GUI & CLI
  ❌ Java-based (heavyweight)
  ❌ Outdated UX

Gatling:
  ✅ High performance
  ✅ Great reports
  ✅ Scala-based
  ❌ Steeper learning curve

Locust:
  ✅ Python-based
  ✅ Distributed testing
  ✅ Web UI
  ❌ Less polished

MrDib's Pick: k6 🏆
- Modern tooling
- Great DX
- Excellent metrics
- Active community
*/
```

---

<div align="center">

## 🦗 k6 Load Testing

</div>

### Modern Performance Testing with k6 🚀

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

# macOS
brew install k6

# Linux
sudo gpg -k
sudo gpg --no-default-keyring --keyring /usr/share/keyrings/k6-archive-keyring.gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys C5AD17C747E3415A3642D57D77C6C491D6AC1D69
echo "deb [signed-by=/usr/share/keyrings/k6-archive-keyring.gpg] https://dl.k6.io/deb stable main" | sudo tee /etc/apt/sources.list.d/k6.list
sudo apt-get update
sudo apt-get install k6

# Windows
choco install k6

# Docker
docker run -i grafana/k6 run - <script.js

# Verify installation
k6 version
```

```javascript
// ═══════════════════════════════════════════
// Basic k6 Test
// ═══════════════════════════════════════════

import http from 'k6/http';
import { check, sleep } from 'k6';

export const options = {
  vus: 10, // 10 virtual users
  duration: '30s', // Run for 30 seconds
};

export default function () {
  const res = http.get('https://test.k6.io');

  check(res, {
    'status is 200': (r) => r.status === 200,
    'response time < 500ms': (r) => r.timings.duration < 500,
  });

  sleep(1);
}

// Run: k6 run script.js

// ═══════════════════════════════════════════
// Advanced k6 Configuration
// ═══════════════════════════════════════════

import http from 'k6/http';
import { check, group, sleep } from 'k6';
import { Counter, Rate, Trend, Gauge } from 'k6/metrics';
import { htmlReport } from 'https://raw.githubusercontent.com/benc-uk/k6-reporter/main/dist/bundle.js';

// Custom metrics
const myCounter = new Counter('my_counter');
const myRate = new Rate('my_rate');
const myTrend = new Trend('my_trend');
const myGauge = new Gauge('my_gauge');

export const options = {
  // Scenarios for different test patterns
  scenarios: {
    // Constant load
    constant_load: {
      executor: 'constant-vus',
      vus: 50,
      duration: '5m',
      tags: { test_type: 'constant' },
    },

    // Ramping load
    ramping_load: {
      executor: 'ramping-vus',
      startVUs: 0,
      stages: [
        { duration: '2m', target: 10 },
        { duration: '5m', target: 50 },
        { duration: '2m', target: 100 },
        { duration: '5m', target: 100 },
        { duration: '2m', target: 0 },
      ],
      gracefulRampDown: '30s',
      tags: { test_type: 'ramping' },
    },

    // Arrival rate (requests/second)
    constant_arrival_rate: {
      executor: 'constant-arrival-rate',
      rate: 100, // 100 requests per timeUnit
      timeUnit: '1s',
      duration: '5m',
      preAllocatedVUs: 50,
      maxVUs: 200,
      tags: { test_type: 'arrival_rate' },
    },

    // Spike test
    spike: {
      executor: 'ramping-arrival-rate',
      startRate: 10,
      timeUnit: '1s',
      preAllocatedVUs: 100,
      maxVUs: 500,
      stages: [
        { duration: '30s', target: 10 },
        { duration: '10s', target: 200 }, // Spike!
        { duration: '1m', target: 200 },
        { duration: '30s', target: 10 },
      ],
      tags: { test_type: 'spike' },
    },
  },

  // Thresholds (pass/fail criteria)
  thresholds: {
    // 95% of requests must complete within 500ms
    'http_req_duration': ['p(95)<500'],

    // 99% of requests must complete within 1s
    'http_req_duration{endpoint:api}': ['p(99)<1000'],

    // Error rate must be below 1%
    'http_req_failed': ['rate<0.01'],

    // Requests per second must be above 50
    'http_reqs': ['rate>50'],

    // Custom metrics
    'my_rate': ['rate<0.1'],
    'my_trend': ['p(95)<200', 'p(99)<500'],
  },

  // External metrics
  ext: {
    loadimpact: {
      projectID: 123456,
      name: 'Performance Test',
      distribution: {
        'amazon:us:ashburn': { loadZone: 'amazon:us:ashburn', percent: 50 },
        'amazon:eu:dublin': { loadZone: 'amazon:eu:dublin', percent: 50 },
      },
    },
  },
};

// ═══════════════════════════════════════════
// Test Setup & Teardown
// ═══════════════════════════════════════════

// Setup (runs once at start)
export function setup() {
  // Initialize test data
  const res = http.get('https://api.example.com/health');

  if (res.status !== 200) {
    throw new Error('API is not healthy');
  }

  // Create test users
  const users = [];
  for (let i = 0; i < 100; i++) {
    const user = http.post('https://api.example.com/test/users', JSON.stringify({
      name: `Test User ${i}`,
      email: `test${i}@example.com`,
    })).json();

    users.push(user);
  }

  return { users, startTime: new Date() };
}

// Main test (runs for each VU)
export default function (data) {
  // Select random user
  const user = data.users[Math.floor(Math.random() * data.users.length)];

  group('User Journey', () => {
    // Login
    group('Login', () => {
      const loginRes = http.post('https://api.example.com/auth/login', JSON.stringify({
        email: user.email,
        password: 'password123',
      }), {
        headers: { 'Content-Type': 'application/json' },
        tags: { endpoint: 'login' },
      });

      check(loginRes, {
        'login successful': (r) => r.status === 200,
        'has token': (r) => r.json('token') !== '',
      });

      if (loginRes.status !== 200) {
        myRate.add(1);
        return;
      }

      myRate.add(0);
      const token = loginRes.json('token');

      // Dashboard
      group('Dashboard', () => {
        const dashRes = http.get('https://api.example.com/dashboard', {
          headers: { 'Authorization': `Bearer ${token}` },
          tags: { endpoint: 'dashboard' },
        });

        myTrend.add(dashRes.timings.duration);

        check(dashRes, {
          'dashboard loaded': (r) => r.status === 200,
          'has data': (r) => r.json('data') !== null,
        });
      });

      // Create action
      group('Create', () => {
        const createRes = http.post('https://api.example.com/posts', JSON.stringify({
          title: `Post ${Date.now()}`,
          content: 'Test content',
        }), {
          headers: {
            'Authorization': `Bearer ${token}`,
            'Content-Type': 'application/json',
          },
          tags: { endpoint: 'create' },
        });

        check(createRes, {
          'post created': (r) => r.status === 201,
        });

        myCounter.add(1);
      });

      sleep(Math.random() * 3 + 1); // Think time 1-4s
    });
  });
}

// Teardown (runs once at end)
export function teardown(data) {
  console.log(`Test completed. Duration: ${new Date() - data.startTime}ms`);

  // Cleanup test data
  http.post('https://api.example.com/test/cleanup');
}

// Generate HTML report
export function handleSummary(data) {
  return {
    'summary.html': htmlReport(data),
    'summary.json': JSON.stringify(data),
  };
}

// ═══════════════════════════════════════════
// Advanced Patterns
// ═══════════════════════════════════════════

// Load test data from file
import { SharedArray } from 'k6/data';

const users = new SharedArray('users', function () {
  return JSON.parse(open('./users.json'));
});

// Execute custom code
import { exec } from 'k6/execution';

export default function () {
  console.log(`VU: ${exec.vu.idInTest}, Iteration: ${exec.vu.iterationInScenario}`);
}

// WebSocket testing
import ws from 'k6/ws';

export default function () {
  const url = 'ws://echo.websocket.org';

  const res = ws.connect(url, function (socket) {
    socket.on('open', () => {
      console.log('connected');
      socket.send('ping');
    });

    socket.on('message', (data) => {
      console.log('Message received:', data);
      socket.close();
    });

    socket.on('close', () => {
      console.log('disconnected');
    });
  });

  check(res, {
    'status is 101': (r) => r && r.status === 101,
  });
}

// Browser testing
import { browser } from 'k6/experimental/browser';

export const options = {
  scenarios: {
    browser: {
      executor: 'shared-iterations',
      options: {
        browser: {
          type: 'chromium',
        },
      },
    },
  },
};

export default async function () {
  const page = browser.newPage();

  try {
    await page.goto('https://test.k6.io');

    page.screenshot({ path: `screenshots/${__ITER}.png` });

    const submitButton = page.locator('input[type="submit"]');
    await submitButton.click();

    page.waitForNavigation();
  } finally {
    page.close();
  }
}
```

**📦 k6 Resources:**

- Docs: https://k6.io/docs/
- Extensions: https://k6.io/docs/extensions/
- Examples: https://github.com/grafana/k6-examples

> **💡 Pro Tip:** Use k6 Cloud for distributed load testing from multiple geographic locations. Great for testing CDN performance and global latency!

<div align="center">

## 🎯 Artillery Testing

</div>

### Quick Performance Tests 🚀

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install -g artillery@latest

# Verify installation
artillery -V
```

```yaml
# ═══════════════════════════════════════════
# Artillery Configuration (artillery.yml)
# ═══════════════════════════════════════════

config:
  target: "https://api.example.com"

  # Load phases
  phases:
    - duration: 60
      arrivalRate: 10
      name: "Warm up"

    - duration: 120
      arrivalRate: 50
      name: "Sustained load"

    - duration: 60
      arrivalRate: 100
      name: "Peak load"

    - duration: 60
      arrivalRate: 10
      name: "Cool down"

  # Custom processor
  processor: "./processor.js"

  # Variables
  variables:
    baseUrl: "https://api.example.com"
    apiVersion: "v1"

  # HTTP settings
  http:
    timeout: 10
    maxSockets: 100

  # Performance expectations
  ensure:
    maxErrorRate: 1
    max:
      p95: 500
      p99: 1000

  # Plugins
  plugins:
    expect: {}
    metrics-by-endpoint: {}

# ═══════════════════════════════════════════
# Test Scenarios
# ═══════════════════════════════════════════

scenarios:
  - name: "User Registration Flow"
    weight: 20
    flow:
      # Register
      - post:
          url: "/auth/register"
          json:
            name: "{{ $randomString() }}"
            email: "test-{{ $randomString() }}@example.com"
            password: "SecurePass123!"
          capture:
            - json: "$.token"
              as: "authToken"
          expect:
            - statusCode: 201
            - contentType: json
            - hasProperty: token

      # Verify email
      - think: 2
      - get:
          url: "/auth/verify?token={{ authToken }}"
          expect:
            - statusCode: 200

  - name: "Authenticated User Journey"
    weight: 60
    flow:
      # Login
      - post:
          url: "/auth/login"
          json:
            email: "{{ email }}"
            password: "{{ password }}"
          capture:
            - json: "$.token"
              as: "token"
            - json: "$.user.id"
              as: "userId"
          expect:
            - statusCode: 200

      # Get dashboard
      - think: 1
      - get:
          url: "/dashboard"
          headers:
            Authorization: "Bearer {{ token }}"
          expect:
            - statusCode: 200
            - contentType: json

      # Create post
      - think: 3
      - post:
          url: "/posts"
          headers:
            Authorization: "Bearer {{ token }}"
          json:
            title: "Test Post {{ $timestamp }}"
            content: "This is a test post"
          capture:
            - json: "$.id"
              as: "postId"
          expect:
            - statusCode: 201

      # Get own posts
      - think: 2
      - get:
          url: "/users/{{ userId }}/posts"
          headers:
            Authorization: "Bearer {{ token }}"
          expect:
            - statusCode: 200
            - hasProperty: posts

      # Update post
      - think: 3
      - put:
          url: "/posts/{{ postId }}"
          headers:
            Authorization: "Bearer {{ token }}"
          json:
            title: "Updated Title"
          expect:
            - statusCode: 200

      # Delete post
      - think: 1
      - delete:
          url: "/posts/{{ postId }}"
          headers:
            Authorization: "Bearer {{ token }}"
          expect:
            - statusCode: 204

  - name: "API Heavy User"
    weight: 20
    flow:
      # Batch requests
      - loop:
          - get:
              url: "/api/data?page={{ $loopCount }}"
              expect:
                - statusCode: 200
          - think: 0.5
        count: 10

      # Parallel requests
      - parallel:
          - get:
              url: "/api/users"
          - get:
              url: "/api/posts"
          - get:
              url: "/api/comments"
```

```javascript
// ═══════════════════════════════════════════
// Custom Processor (processor.js)
// ═══════════════════════════════════════════

module.exports = {
  beforeRequest,
  afterResponse,
  generateTestData,
};

// Run before each request
function beforeRequest(requestParams, context, ee, next) {
  // Add custom headers
  requestParams.headers["X-Request-ID"] = generateUUID();
  requestParams.headers["X-Timestamp"] = Date.now();
  requestParams.headers["X-User-Agent"] = "Artillery/LoadTest";

  // Log request (optional)
  console.log(`Request to: ${requestParams.url}`);

  return next();
}

// Run after each response
function afterResponse(requestParams, response, context, ee, next) {
  // Log slow requests
  if (response.time > 1000) {
    console.log(
      `⚠️ Slow request: ${requestParams.url} took ${response.time}ms`
    );
  }

  // Track custom metrics
  if (response.statusCode >= 500) {
    ee.emit("counter", "errors.5xx", 1);
  }

  // Extract and store data
  if (response.body) {
    try {
      const data = JSON.parse(response.body);
      if (data.userId) {
        context.vars.userId = data.userId;
      }
    } catch (e) {
      // Not JSON
    }
  }

  return next();
}

// Generate test data
function generateTestData(context, events, done) {
  const faker = require("faker");

  context.vars.email = faker.internet.email();
  context.vars.password = "TestPass123!";
  context.vars.name = faker.name.findName();
  context.vars.phone = faker.phone.phoneNumber();

  return done();
}

function generateUUID() {
  return "xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx".replace(/[xy]/g, (c) => {
    const r = (Math.random() * 16) | 0;
    const v = c === "x" ? r : (r & 0x3) | 0x8;
    return v.toString(16);
  });
}
```

```bash
# ═══════════════════════════════════════════
# Run Artillery Tests
# ═══════════════════════════════════════════

# Basic run
artillery run artillery.yml

# Generate HTML report
artillery run --output report.json artillery.yml
artillery report report.json

# Quick test
artillery quick --duration 60 --rate 10 https://api.example.com

# Run with environment variables
artillery run -e production artillery.yml

# Distributed load testing
artillery run --target https://api.example.com \
  --count 5 \  # 5 workers
  artillery.yml
```

**📦 Artillery Resources:**

- Docs: https://artillery.io/docs/
- Examples: https://github.com/artilleryio/artillery-examples

> **💡 Pro Tip:** Artillery is perfect for quick API load tests. Use YAML for simple scenarios and JavaScript processor for complex logic!

---

<div align="center">

## 🌐 Frontend Performance

</div>

### Testing User Experience Metrics 🎨

```javascript
// ═══════════════════════════════════════════
// Lighthouse Performance Testing
// ═══════════════════════════════════════════

import lighthouse from "lighthouse";
import * as chromeLauncher from "chrome-launcher";

async function runLighthouse(url, options = {}) {
  const chrome = await chromeLauncher.launch({
    chromeFlags: ["--headless", "--no-sandbox"],
  });

  const defaultOptions = {
    logLevel: "info",
    output: "json",
    onlyCategories: ["performance"],
    port: chrome.port,
    formFactor: "desktop",
    throttling: {
      rttMs: 40,
      throughputKbps: 10 * 1024,
      cpuSlowdownMultiplier: 1,
    },
  };

  const runnerResult = await lighthouse(url, {
    ...defaultOptions,
    ...options,
  });

  await chrome.kill();

  return runnerResult.lhr;
}

// ═══════════════════════════════════════════
// Core Web Vitals Testing
// ═══════════════════════════════════════════

describe("Core Web Vitals", () => {
  const pages = [
    { name: "Homepage", url: "https://example.com" },
    { name: "Product", url: "https://example.com/products/1" },
    { name: "Checkout", url: "https://example.com/checkout" },
  ];

  pages.forEach(({ name, url }) => {
    test(`${name} meets Web Vitals thresholds`, async () => {
      const results = await runLighthouse(url);
      const metrics = results.audits.metrics.details.items[0];

      // Largest Contentful Paint (LCP) < 2.5s
      expect(metrics.largestContentfulPaint).toBeLessThan(2500);
      console.log(`LCP: ${metrics.largestContentfulPaint}ms`);

      // First Contentful Paint (FCP) < 1.8s
      expect(metrics.firstContentfulPaint).toBeLessThan(1800);
      console.log(`FCP: ${metrics.firstContentfulPaint}ms`);

      // Total Blocking Time (TBT) < 300ms
      expect(metrics.totalBlockingTime).toBeLessThan(300);
      console.log(`TBT: ${metrics.totalBlockingTime}ms`);

      // Cumulative Layout Shift (CLS) < 0.1
      expect(metrics.cumulativeLayoutShift).toBeLessThan(0.1);
      console.log(`CLS: ${metrics.cumulativeLayoutShift}`);

      // Speed Index < 3.4s
      expect(metrics.speedIndex).toBeLessThan(3400);
      console.log(`Speed Index: ${metrics.speedIndex}ms`);

      // Time to Interactive (TTI) < 3.8s
      expect(metrics.interactive).toBeLessThan(3800);
      console.log(`TTI: ${metrics.interactive}ms`);

      // Performance Score > 90
      const score = results.categories.performance.score * 100;
      expect(score).toBeGreaterThan(90);
      console.log(`Performance Score: ${score}`);
    }, 60000);
  });
});

// ═══════════════════════════════════════════
// Playwright Performance Testing
// ═══════════════════════════════════════════

import { test, expect } from "@playwright/test";

test.describe("Frontend Performance", () => {
  test("measures page load metrics", async ({ page }) => {
    await page.goto("https://example.com");

    // Get Navigation Timing
    const navigationTiming = await page.evaluate(() => {
      const nav = performance.getEntriesByType("navigation")[0];
      return {
        dns: nav.domainLookupEnd - nav.domainLookupStart,
        tcp: nav.connectEnd - nav.connectStart,
        ttfb: nav.responseStart - nav.requestStart,
        download: nav.responseEnd - nav.responseStart,
        domInteractive: nav.domInteractive - nav.fetchStart,
        domComplete: nav.domComplete - nav.fetchStart,
        loadComplete: nav.loadEventEnd - nav.fetchStart,
      };
    });

    console.log("Performance Metrics:", navigationTiming);

    // Assert metrics
    expect(navigationTiming.dns).toBeLessThan(100);
    expect(navigationTiming.tcp).toBeLessThan(100);
    expect(navigationTiming.ttfb).toBeLessThan(600);
    expect(navigationTiming.domInteractive).toBeLessThan(2000);
    expect(navigationTiming.domComplete).toBeLessThan(3000);
  });

  test("measures resource loading", async ({ page }) => {
    await page.goto("https://example.com");

    // Get resource timings
    const resources = await page.evaluate(() => {
      return performance.getEntriesByType("resource").map((r) => ({
        name: r.name,
        duration: r.duration,
        size: r.encodedBodySize,
        type: r.initiatorType,
      }));
    });

    // Check for large resources
    const largeResources = resources.filter((r) => r.size > 500000);
    console.log("Large resources (>500KB):", largeResources);
    expect(largeResources.length).toBe(0);

    // Check for slow resources
    const slowResources = resources.filter((r) => r.duration > 1000);
    console.log("Slow resources (>1s):", slowResources);
    expect(slowResources.length).toBeLessThan(3);

    // Check total size
    const totalSize = resources.reduce((sum, r) => sum + r.size, 0);
    console.log(`Total page size: ${(totalSize / 1024 / 1024).toFixed(2)}MB`);
    expect(totalSize).toBeLessThan(3 * 1024 * 1024); // < 3MB
  });

  test("measures Web Vitals", async ({ page }) => {
    await page.goto("https://example.com");

    // Wait for page to fully load
    await page.waitForLoadState("networkidle");

    // Get Web Vitals
    const webVitals = await page.evaluate(() => {
      return new Promise((resolve) => {
        const vitals = {};

        // FCP
        new PerformanceObserver((list) => {
          for (const entry of list.getEntries()) {
            if (entry.name === "first-contentful-paint") {
              vitals.FCP = entry.startTime;
            }
          }
        }).observe({ entryTypes: ["paint"] });

        // LCP
        new PerformanceObserver((list) => {
          const entries = list.getEntries();
          const lastEntry = entries[entries.length - 1];
          vitals.LCP = lastEntry.startTime;
        }).observe({ entryTypes: ["largest-contentful-paint"] });

        // CLS
        let cls = 0;
        new PerformanceObserver((list) => {
          for (const entry of list.getEntries()) {
            if (!entry.hadRecentInput) {
              cls += entry.value;
            }
          }
          vitals.CLS = cls;
        }).observe({ entryTypes: ["layout-shift"] });

        setTimeout(() => resolve(vitals), 3000);
      });
    });

    console.log("Web Vitals:", webVitals);

    expect(webVitals.FCP).toBeLessThan(1800);
    expect(webVitals.LCP).toBeLessThan(2500);
    expect(webVitals.CLS).toBeLessThan(0.1);
  });
});

// ═══════════════════════════════════════════
// Bundle Size Analysis
// ═══════════════════════════════════════════

import { test as baseTest } from "@playwright/test";
import path from "path";
import fs from "fs";

test("checks bundle sizes", async () => {
  const distPath = path.join(__dirname, "../dist");
  const files = fs.readdirSync(distPath);

  const bundles = files
    .filter((f) => f.endsWith(".js"))
    .map((f) => ({
      name: f,
      size: fs.statSync(path.join(distPath, f)).size,
    }));

  console.log("Bundle sizes:");
  bundles.forEach((b) => {
    console.log(`  ${b.name}: ${(b.size / 1024).toFixed(2)}KB`);
  });

  // Main bundle < 200KB
  const mainBundle = bundles.find((b) => b.name.includes("main"));
  expect(mainBundle.size).toBeLessThan(200 * 1024);

  // Vendor bundle < 300KB
  const vendorBundle = bundles.find((b) => b.name.includes("vendor"));
  if (vendorBundle) {
    expect(vendorBundle.size).toBeLessThan(300 * 1024);
  }
});
```

---

<div align="center">

## 📊 API Performance

</div>

### Backend Load Testing Strategies 🚀

```javascript
// ═══════════════════════════════════════════
// API Load Test with k6
// ═══════════════════════════════════════════

import http from "k6/http";
import { check, group } from "k6";
import { Rate, Trend } from "k6/metrics";

const errorRate = new Rate("errors");
const apiLatency = new Trend("api_latency");

export const options = {
  scenarios: {
    // Baseline test
    baseline: {
      executor: "constant-vus",
      vus: 10,
      duration: "1m",
      tags: { test: "baseline" },
    },

    // Load test
    load: {
      executor: "ramping-vus",
      startVUs: 0,
      stages: [
        { duration: "2m", target: 50 },
        { duration: "5m", target: 50 },
        { duration: "2m", target: 100 },
        { duration: "5m", target: 100 },
        { duration: "2m", target: 0 },
      ],
      startTime: "1m",
      tags: { test: "load" },
    },

    // Stress test
    stress: {
      executor: "ramping-vus",
      startVUs: 0,
      stages: [
        { duration: "2m", target: 200 },
        { duration: "5m", target: 200 },
        { duration: "2m", target: 400 },
        { duration: "5m", target: 400 },
        { duration: "2m", target: 0 },
      ],
      startTime: "16m",
      tags: { test: "stress" },
    },
  },

  thresholds: {
    http_req_failed: ["rate<0.01"],
    http_req_duration: ["p(95)<500", "p(99)<1000"],
    "http_req_duration{endpoint:search}": ["p(95)<300"],
    errors: ["rate<0.05"],
    api_latency: ["p(95)<200"],
  },
};

const BASE_URL = "https://api.example.com";

export default function () {
  group("API Endpoints", () => {
    // GET request
    group("GET /users", () => {
      const start = Date.now();
      const res = http.get(`${BASE_URL}/users?page=1&limit=20`, {
        tags: { endpoint: "users" },
      });

      apiLatency.add(Date.now() - start);

      const success = check(res, {
        "status is 200": (r) => r.status === 200,
        "has users array": (r) => Array.isArray(r.json("users")),
        "response time < 500ms": (r) => r.timings.duration < 500,
      });

      errorRate.add(!success);
    });

    // POST request
    group("POST /users", () => {
      const payload = JSON.stringify({
        name: `Test User ${Date.now()}`,
        email: `user${Date.now()}@example.com`,
        age: Math.floor(Math.random() * 50) + 18,
      });

      const res = http.post(`${BASE_URL}/users`, payload, {
        headers: { "Content-Type": "application/json" },
        tags: { endpoint: "create" },
      });

      check(res, {
        "created successfully": (r) => r.status === 201,
        "has id": (r) => r.json("id") !== undefined,
      });
    });

    // Search endpoint
    group("Search", () => {
      const terms = ["test", "user", "admin", "product", "service"];
      const term = terms[Math.floor(Math.random() * terms.length)];

      const res = http.get(`${BASE_URL}/search?q=${term}`, {
        tags: { endpoint: "search" },
      });

      check(res, {
        "search works": (r) => r.status === 200,
        "returns results": (r) => r.json("results") !== undefined,
      });
    });

    // Batch requests
    group("Batch Operations", () => {
      const requests = [
        ["GET", `${BASE_URL}/users`],
        ["GET", `${BASE_URL}/posts`],
        ["GET", `${BASE_URL}/comments`],
      ];

      const responses = http.batch(requests);

      responses.forEach((res, i) => {
        check(res, {
          [`batch request ${i} succeeded`]: (r) => r.status === 200,
        });
      });
    });
  });
}

// ═══════════════════════════════════════════
// Database Performance Testing
// ═══════════════════════════════════════════

export function databaseStressTest() {
  group("Database Operations", () => {
    // Test read-heavy load
    group("Read Heavy", () => {
      const reads = [];
      for (let i = 0; i < 50; i++) {
        reads.push(["GET", `${BASE_URL}/products?page=${i + 1}`]);
      }

      const responses = http.batch(reads);

      const avgResponseTime =
        responses.reduce((sum, r) => sum + r.timings.duration, 0) /
        responses.length;

      console.log(`Avg read time: ${avgResponseTime.toFixed(2)}ms`);

      check(null, {
        "avg read time < 200ms": () => avgResponseTime < 200,
      });
    });

    // Test write-heavy load
    group("Write Heavy", () => {
      const writes = [];
      for (let i = 0; i < 20; i++) {
        writes.push([
          "POST",
          `${BASE_URL}/products`,
          JSON.stringify({
            name: `Product ${Date.now()}-${i}`,
            price: Math.random() * 1000,
            stock: Math.floor(Math.random() * 100),
          }),
          { headers: { "Content-Type": "application/json" } },
        ]);
      }

      const responses = http.batch(writes);

      const successRate =
        responses.filter((r) => r.status === 201).length / responses.length;

      check(null, {
        "write success rate > 95%": () => successRate > 0.95,
      });
    });

    // Test transaction performance
    group("Transactions", () => {
      const res = http.post(
        `${BASE_URL}/orders`,
        JSON.stringify({
          userId: Math.floor(Math.random() * 1000),
          items: Array.from({ length: 5 }, (_, i) => ({
            productId: Math.floor(Math.random() * 100),
            quantity: Math.floor(Math.random() * 5) + 1,
          })),
        }),
        {
          headers: { "Content-Type": "application/json" },
        }
      );

      check(res, {
        "transaction succeeded": (r) => r.status === 201,
        "transaction time < 1s": (r) => r.timings.duration < 1000,
      });
    });
  });
}
```

---

<div align="center">

## 🔍 Monitoring & Metrics

</div>

### Performance Monitoring Setup 📊

```javascript
// ═══════════════════════════════════════════
// Real-time Performance Monitoring
// ═══════════════════════════════════════════

class PerformanceMonitor {
  constructor() {
    this.metrics = {
      requests: 0,
      errors: 0,
      totalDuration: 0,
      durations: [],
      timestamps: [],
    };

    this.startTime = Date.now();
  }

  recordRequest(duration, success = true) {
    this.metrics.requests++;
    this.metrics.totalDuration += duration;
    this.metrics.durations.push(duration);
    this.metrics.timestamps.push(Date.now());

    if (!success) {
      this.metrics.errors++;
    }
  }

  getStats() {
    const sorted = [...this.metrics.durations].sort((a, b) => a - b);
    const len = sorted.length;

    const percentile = (p) => {
      const index = Math.ceil((len * p) / 100) - 1;
      return sorted[index] || 0;
    };

    const elapsed = (Date.now() - this.startTime) / 1000;

    return {
      totalRequests: this.metrics.requests,
      totalErrors: this.metrics.errors,
      errorRate:
        ((this.metrics.errors / this.metrics.requests) * 100).toFixed(2) + "%",
      avgDuration:
        (this.metrics.totalDuration / this.metrics.requests).toFixed(2) + "ms",
      p50: percentile(50).toFixed(2) + "ms",
      p95: percentile(95).toFixed(2) + "ms",
      p99: percentile(99).toFixed(2) + "ms",
      min: Math.min(...sorted).toFixed(2) + "ms",
      max: Math.max(...sorted).toFixed(2) + "ms",
      rps: (this.metrics.requests / elapsed).toFixed(2),
      duration: elapsed.toFixed(2) + "s",
    };
  }

  printReport() {
    const stats = this.getStats();

    console.log("\n📊 Performance Report");
    console.log("═══════════════════════════════════════");
    console.log(`Total Requests: ${stats.totalRequests}`);
    console.log(`Total Errors: ${stats.totalErrors} (${stats.errorRate})`);
    console.log(`Requests/sec: ${stats.rps}`);
    console.log("\nResponse Times:");
    console.log(`  Average: ${stats.avgDuration}`);
    console.log(`  Median (p50): ${stats.p50}`);
    console.log(`  p95: ${stats.p95}`);
    console.log(`  p99: ${stats.p99}`);
    console.log(`  Min: ${stats.min}`);
    console.log(`  Max: ${stats.max}`);
    console.log(`\nTest Duration: ${stats.duration}`);
    console.log("═══════════════════════════════════════\n");
  }
}

// ═══════════════════════════════════════════
// System Metrics Collection
// ═══════════════════════════════════════════

import os from "os";
import { exec } from "child_process";
import { promisify } from "util";

const execAsync = promisify(exec);

class SystemMonitor {
  async getMetrics() {
    return {
      cpu: await this.getCPUUsage(),
      memory: this.getMemoryUsage(),
      network: await this.getNetworkStats(),
      disk: await this.getDiskUsage(),
    };
  }

  async getCPUUsage() {
    const cpus = os.cpus();
    const usage = cpus.map((cpu) => {
      const total = Object.values(cpu.times).reduce((a, b) => a + b);
      const idle = cpu.times.idle;
      return (((total - idle) / total) * 100).toFixed(2);
    });

    return {
      cores: cpus.length,
      usage: usage,
      average:
        (
          usage.reduce((a, b) => parseFloat(a) + parseFloat(b)) / usage.length
        ).toFixed(2) + "%",
    };
  }

  getMemoryUsage() {
    const total = os.totalmem();
    const free = os.freemem();
    const used = total - free;

    return {
      total: (total / 1024 / 1024 / 1024).toFixed(2) + "GB",
      used: (used / 1024 / 1024 / 1024).toFixed(2) + "GB",
      free: (free / 1024 / 1024 / 1024).toFixed(2) + "GB",
      percentage: ((used / total) * 100).toFixed(2) + "%",
    };
  }

  async getNetworkStats() {
    try {
      // Linux/Mac
      const { stdout } = await execAsync(
        "netstat -i | grep -v Kernel | grep -v Iface"
      );
      // Parse network stats
      return { available: true };
    } catch {
      return { available: false };
    }
  }

  async getDiskUsage() {
    try {
      const { stdout } = await execAsync("df -h /");
      // Parse disk usage
      return { available: true };
    } catch {
      return { available: false };
    }
  }
}

// Usage
const monitor = new SystemMonitor();
setInterval(async () => {
  const metrics = await monitor.getMetrics();
  console.log("System Metrics:", JSON.stringify(metrics, null, 2));
}, 5000);
```

---

<div align="center">

## 🚀 CI/CD Integration

</div>

### Automated Performance Testing 🤖

```yaml
# ═══════════════════════════════════════════
# GitHub Actions - Performance Testing
# ═══════════════════════════════════════════

name: Performance Tests

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]
  schedule:
    - cron: "0 0 * * *" # Daily at midnight

jobs:
  performance:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: "20"

      - name: Install k6
        run: |
          sudo gpg -k
          sudo gpg --no-default-keyring --keyring /usr/share/keyrings/k6-archive-keyring.gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys C5AD17C747E3415A3642D57D77C6C491D6AC1D69
          echo "deb [signed-by=/usr/share/keyrings/k6-archive-keyring.gpg] https://dl.k6.io/deb stable main" | sudo tee /etc/apt/sources.list.d/k6.list
          sudo apt-get update
          sudo apt-get install k6

      - name: Start application
        run: |
          npm ci
          npm run build
          npm start &
          sleep 10
        env:
          NODE_ENV: production

      - name: Run k6 load test
        run: |
          k6 run --out json=results.json tests/load-test.js

      - name: Check thresholds
        run: |
          if grep -q '"thresholds_failed":true' results.json; then
            echo "❌ Performance thresholds failed"
            exit 1
          else
            echo "✅ Performance thresholds passed"
          fi

      - name: Generate report
        if: always()
        run: |
          npm install -g k6-html-reporter
          k6-html-reporter results.json

      - name: Upload results
        if: always()
        uses: actions/upload-artifact@v4
        with:
          name: performance-results
          path: |
            results.json
            report.html

      - name: Comment PR
        if: github.event_name == 'pull_request'
        uses: actions/github-script@v7
        with:
          script: |
            const fs = require('fs');
            const results = JSON.parse(fs.readFileSync('results.json'));

            const metrics = results.metrics;
            const comment = `
            ## 📊 Performance Test Results

            | Metric | Value | Threshold | Status |
            |--------|-------|-----------|--------|
            | Avg Response Time | ${metrics.http_req_duration.avg.toFixed(2)}ms | <500ms | ${metrics.http_req_duration.avg < 500 ? '✅' : '❌'} |
            | p95 Response Time | ${metrics.http_req_duration['p(95)'].toFixed(2)}ms | <1000ms | ${metrics.http_req_duration['p(95)'] < 1000 ? '✅' : '❌'} |
            | Error Rate | ${(metrics.http_req_failed.rate * 100).toFixed(2)}% | <1% | ${metrics.http_req_failed.rate < 0.01 ? '✅' : '❌'} |
            | Requests/sec | ${metrics.http_reqs.rate.toFixed(2)} | >50 | ${metrics.http_reqs.rate > 50 ? '✅' : '❌'} |
            `;

            github.rest.issues.createComment({
              issue_number: context.issue.number,
              owner: context.repo.owner,
              repo: context.repo.repo,
              body: comment
            });

  # ═══════════════════════════════════════════
  # Lighthouse CI
  # ═══════════════════════════════════════════

  lighthouse:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: "20"

      - name: Install dependencies
        run: npm ci

      - name: Build
        run: npm run build

      - name: Run Lighthouse CI
        run: |
          npm install -g @lhci/cli
          lhci autorun
        env:
          LHCI_GITHUB_APP_TOKEN: ${{ secrets.LHCI_GITHUB_APP_TOKEN }}

      - name: Upload Lighthouse results
        uses: actions/upload-artifact@v4
        with:
          name: lighthouse-results
          path: .lighthouseci

  # ═══════════════════════════════════════════
  # Docker Performance Testing
  # ═══════════════════════════════════════════

  docker-perf:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Build Docker image
        run: docker build -t myapp:test .

      - name: Run app in container
        run: |
          docker run -d -p 3000:3000 --name myapp myapp:test
          sleep 10

      - name: Run performance tests
        run: |
          docker run --network host \
            -v $(pwd)/tests:/tests \
            grafana/k6 run /tests/load-test.js

      - name: Cleanup
        if: always()
        run: docker rm -f myapp
```

---

<div align="center">

## 💡 Best Practices

</div>

### Performance Testing Guidelines ⭐

```javascript
// ═══════════════════════════════════════════
// 1. Realistic Test Scenarios
// ═══════════════════════════════════════════

// ❌ BAD: Unrealistic load pattern
export const options = {
  vus: 1000,
  duration: "1m",
};

// ✅ GOOD: Gradual ramp-up
export const options = {
  stages: [
    { duration: "2m", target: 50 }, // Ramp up
    { duration: "5m", target: 100 }, // Increase
    { duration: "10m", target: 100 }, // Sustain
    { duration: "5m", target: 200 }, // Peak
    { duration: "10m", target: 200 }, // Sustain peak
    { duration: "5m", target: 0 }, // Ramp down
  ],
};

// ═══════════════════════════════════════════
// 2. Think Time & User Behavior
// ═══════════════════════════════════════════

// ❌ BAD: No think time
http.get("/page1");
http.get("/page2");
http.get("/page3");

// ✅ GOOD: Realistic user behavior
http.get("/page1");
sleep(randomIntBetween(2, 5)); // User reads

http.get("/page2");
sleep(randomIntBetween(1, 3)); // User thinks

http.post("/form", data);
sleep(randomIntBetween(3, 7)); // User fills form

// ═══════════════════════════════════════════
// 3. Varied Test Data
// ═══════════════════════════════════════════

// ❌ BAD: Same data every time
const user = { email: "test@example.com" };

// ✅ GOOD: Varied, realistic data
import { SharedArray } from "k6/data";

const users = new SharedArray("users", function () {
  return JSON.parse(open("./test-data.json"));
});

export default function () {
  const user = users[Math.floor(Math.random() * users.length)];
  // Use random user
}

// ═══════════════════════════════════════════
// 4. Set Performance Budgets
// ═══════════════════════════════════════════

const performanceBudgets = {
  api: {
    p50: 50, // 50ms
    p95: 200, // 200ms
    p99: 500, // 500ms
    errorRate: 0.01, // 1%
  },

  frontend: {
    FCP: 1800, // 1.8s
    LCP: 2500, // 2.5s
    TBT: 300, // 300ms
    CLS: 0.1, // 0.1
    bundleSize: 200, // 200KB
  },
};

export const options = {
  thresholds: {
    http_req_duration: [
      `p(50)<${performanceBudgets.api.p50}`,
      `p(95)<${performanceBudgets.api.p95}`,
      `p(99)<${performanceBudgets.api.p99}`,
    ],
    http_req_failed: [`rate<${performanceBudgets.api.errorRate}`],
  },
};

// ═══════════════════════════════════════════
// 5. Monitor Everything
// ═══════════════════════════════════════════

const metricsToMonitor = {
  application: [
    "Response time (p50, p95, p99)",
    "Throughput (requests/second)",
    "Error rate (%)",
    "Active connections",
  ],

  infrastructure: [
    "CPU utilization (%)",
    "Memory usage (MB)",
    "Disk I/O (MB/s)",
    "Network I/O (MB/s)",
  ],

  database: [
    "Query execution time (ms)",
    "Connection pool usage",
    "Lock waits",
    "Cache hit ratio (%)",
  ],
};

// ═══════════════════════════════════════════
// 6. Test in Production-Like Environment
// ═══════════════════════════════════════════

/*
✅ DO:
- Use production-sized database
- Same infrastructure specs
- Realistic network conditions
- Similar data volumes
- Same caching behavior

❌ DON'T:
- Test on developer laptop
- Use empty database
- Ignore network latency
- Skip load balancers
*/

// ═══════════════════════════════════════════
// 7. Baseline and Compare
// ═══════════════════════════════════════════

// Always establish baseline
const baseline = {
  p95: 200,
  errorRate: 0.001,
  rps: 100,
};

// Compare against baseline
const current = getMetrics();
const comparison = {
  p95Change: (((current.p95 - baseline.p95) / baseline.p95) * 100).toFixed(2),
  errorRateChange: (
    ((current.errorRate - baseline.errorRate) / baseline.errorRate) *
    100
  ).toFixed(2),
  rpsChange: (((current.rps - baseline.rps) / baseline.rps) * 100).toFixed(2),
};

console.log(`Performance change: ${comparison.p95Change}%`);
```

---

<div align="center">

**Built with ⚡ by MrDib, for Performance-Conscious Developers**

_"Fast software is good software!"_

**Happy Optimizing!** 🚀

**If you found this helpful, give it a ⭐ star and share with fellow developers!**

</div>

---

### Contributing 🤝

Found better performance patterns? Want to add examples? Contributions are welcome!

1. Fork the repository
2. Add your performance testing examples
3. Update best practices
4. Submit a pull request

---

### Resources 📚

**📖 Official Documentation:**

- k6: https://k6.io/docs/
- Artillery: https://artillery.io/docs/
- Lighthouse: https://developers.google.com/web/tools/lighthouse

**🎥 Learning Resources:**

- Web.dev Performance: https://web.dev/performance/
- Google Web Vitals: https://web.dev/vitals/
- k6 YouTube Channel

**🛠️ Tools:**

- WebPageTest: https://www.webpagetest.org/
- PageSpeed Insights: https://pagespeed.web.dev/
- GTmetrix: https://gtmetrix.com/

---

### License 📄

This guide is open source and available under the MIT License.

---

<div align="center">

**Stay fast. Keep testing. Build performant!** 💪✨

⚡ **#Performance** ⚡ **#DevResourceVault** ⚡ **#MrDib** ⚡

### Remember

> _"Every millisecond counts"_

> _"Users don't wait for slow apps"_

> _"Performance is a feature, not an afterthought"_

> _"Measure twice, optimize once"_

> _"Fast by default, not by accident"_

</div>

---

<div align="center">

**Now go forth and make everything blazing fast!** 🌟⚡

</div>
