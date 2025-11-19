<div align="center">

# 🧪 Testing Tools & Frameworks 🧪

### _Because "it works on my machine" is not a valid deployment strategy_ 🤷‍♂️

![Testing](https://img.shields.io/badge/Testing-Essential-green?style=for-the-badge)
![Coverage](https://img.shields.io/badge/Coverage-100%25_Goal-blue?style=for-the-badge)

</div>

---

<div align="center">

## 🎯 Unit Testing Frameworks

</div>

### JavaScript Testing 📦

```

🃏 Jest → https://jestjs.io

- Facebook's framework
- Zero config
- Snapshot testing
- Code coverage
- npm install --save-dev jest

⚡ Vitest → https://vitest.dev

- Vite native
- Jest compatible
- Super fast
- ESM first
- npm install -D vitest

🧪 Mocha → https://mochajs.org

- Flexible framework
- Async support
- Browser support
- Mature ecosystem
- npm install --save-dev mocha

📊 Jasmine → https://jasmine.github.io

- Behavior-driven
- No dependencies
- Spy framework
- Browser ready

🎯 AVA → https://github.com/avajs/ava

- Concurrent tests
- Minimal & fast
- Promise support
- Good errors
- npm install --save-dev ava

```

### Testing Utilities 🛠️

```javascript
// 🔨 Testing Library
import { render, screen, fireEvent } from "@testing-library/react";
import userEvent from "@testing-library/user-event";

test("button click", async () => {
  render(<Button />);
  const button = screen.getByRole("button");

  await userEvent.click(button);
  expect(screen.getByText("Clicked!")).toBeInTheDocument();
});

// 🧬 Enzyme (Legacy)
import { shallow, mount } from "enzyme";

const wrapper = shallow(<Component />);
expect(wrapper.find(".class-name")).toHaveLength(1);

// 📸 Snapshot Testing
test("component snapshot", () => {
  const tree = renderer.create(<Component />).toJSON();
  expect(tree).toMatchSnapshot();
});

// 🎭 Mock Functions
const mockFn = jest.fn();
mockFn.mockReturnValue(42);
mockFn.mockResolvedValue("async value");

// 🔄 Testing Hooks
import { renderHook, act } from "@testing-library/react-hooks";

const { result } = renderHook(() => useCounter());
act(() => {
  result.current.increment();
});
expect(result.current.count).toBe(1);
```

---

<div align="center">

## 🌐 End-to-End Testing

</div>

### E2E Testing Frameworks 🎬

```
🎭 Playwright        → https://playwright.dev
   - Microsoft's tool
   - Multi-browser
   - Fast execution
   - Great DX
   - npm install -D @playwright/test

🌲 Cypress           → https://cypress.io
   - Developer friendly
   - Real browser
   - Time travel
   - Great debugging
   - npm install -D cypress

🤖 Puppeteer         → https://pptr.dev
   - Chrome automation
   - Headless testing
   - PDF generation
   - Screenshots
   - npm install puppeteer

🌙 Nightwatch        → https://nightwatchjs.org
   - Selenium based
   - BDD syntax
   - Cloud testing
   - Page objects
   - npm install -D nightwatch

🔧 WebdriverIO       → https://webdriver.io
   - W3C compliant
   - Multi-browser
   - Mobile testing
   - Extensive API
   - npm install -D webdriverio
```

### E2E Testing Examples 🎯

```javascript
// 🎭 Playwright Example
import { test, expect } from "@playwright/test";

test("user login flow", async ({ page }) => {
  await page.goto("https://example.com/login");

  await page.fill('input[name="email"]', "user@example.com");
  await page.fill('input[name="password"]', "password123");
  await page.click('button[type="submit"]');

  await expect(page).toHaveURL("https://example.com/dashboard");
  await expect(page.locator("h1")).toContainText("Welcome");
});

// 🌲 Cypress Example
describe("User Flow", () => {
  it("should log in successfully", () => {
    cy.visit("/login");

    cy.get("[data-cy=email]").type("user@example.com");
    cy.get("[data-cy=password]").type("password123");
    cy.get("[data-cy=submit]").click();

    cy.url().should("include", "/dashboard");
    cy.contains("h1", "Welcome").should("be.visible");
  });
});

// 🤖 Puppeteer Example
const puppeteer = require("puppeteer")(async () => {
  const browser = await puppeteer.launch();
  const page = await browser.newPage();

  await page.goto("https://example.com");
  await page.screenshot({ path: "example.png" });

  await page.type("#search", "puppeteer");
  await page.click("#submit");
  await page.waitForNavigation();

  await browser.close();
})();
```

---

<div align="center">

## 🎨 Visual Testing

</div>

### Visual Regression Tools 👁️

```
📸 Percy            → https://percy.io
   - Visual testing
   - CI integration
   - Responsive testing
   - Team collaboration
   - From $399/month

🎯 Chromatic        → https://chromatic.com
   - By Storybook team
   - UI testing
   - Visual regression
   - Free tier available

👁️ Applitools       → https://applitools.com
   - AI-powered
   - Cross-browser
   - Smart comparison
   - Enterprise ready

🖼️ BackstopJS       → https://github.com/garris/BackstopJS
   - Open source
   - Headless Chrome
   - CLI & GUI
   - npm install -D backstopjs

📷 Lost Pixel       → https://lost-pixel.com
   - Open source
   - Storybook support
   - GitHub integration
   - Modern approach
```

### Visual Testing Setup 📸

```javascript
// 📸 Percy with Cypress
import "@percy/cypress";

it("visual regression test", () => {
  cy.visit("/home");
  cy.percySnapshot("Homepage");

  cy.get("[data-cy=menu]").click();
  cy.percySnapshot("Homepage - Menu Open");
});

// 🖼️ BackstopJS Config
module.exports = {
  id: "my_project",
  viewports: [
    { label: "phone", width: 320, height: 480 },
    { label: "tablet", width: 1024, height: 768 },
    { label: "desktop", width: 1920, height: 1080 },
  ],
  scenarios: [
    {
      label: "Homepage",
      url: "http://localhost:3000",
      selectors: ["body"],
      delay: 500,
    },
  ],
  paths: {
    bitmaps_reference: "backstop_data/bitmaps_reference",
    bitmaps_test: "backstop_data/bitmaps_test",
  },
};
```

---

<div align="center">

## 📊 Performance Testing

</div>

### Performance Testing Tools 🚀

```
🔥 Lighthouse        → Built into Chrome DevTools
   - Performance audit
   - Accessibility
   - SEO checks
   - PWA audit
   - CLI available

⚡ WebPageTest       → https://webpagetest.org
   - Real browsers
   - Global locations
   - Detailed metrics
   - Video capture

📊 GTmetrix          → https://gtmetrix.com
   - Page speed
   - Recommendations
   - Historical data
   - Monitoring

🎯 K6               → https://k6.io
   - Load testing
   - JavaScript API
   - Cloud & local
   - CI/CD ready
   - brew install k6

🔨 JMeter           → https://jmeter.apache.org
   - Load testing
   - Protocol support
   - GUI & CLI
   - Distributed testing
```

### Performance Testing Examples 🏃

```javascript
// ⚡ K6 Load Test
import http from "k6/http";
import { check, sleep } from "k6";

export const options = {
  stages: [
    { duration: "30s", target: 20 }, // Ramp up
    { duration: "1m", target: 20 }, // Stay at 20 users
    { duration: "30s", target: 0 }, // Ramp down
  ],
  thresholds: {
    http_req_duration: ["p(95)<500"], // 95% of requests under 500ms
  },
};

export default function () {
  const res = http.get("https://api.example.com/users");

  check(res, {
    "status is 200": (r) => r.status === 200,
    "response time < 500ms": (r) => r.timings.duration < 500,
  });

  sleep(1);
}

// 🔥 Lighthouse CI
module.exports = {
  ci: {
    collect: {
      url: ["http://localhost:3000"],
      numberOfRuns: 3,
    },
    assert: {
      assertions: {
        "categories:performance": ["error", { minScore: 0.9 }],
        "categories:accessibility": ["warn", { minScore: 0.9 }],
      },
    },
    upload: {
      target: "temporary-public-storage",
    },
  },
};
```

---

<div align="center">

## 🔒 Security Testing

</div>

### Security Testing Tools 🛡️

```
🔍 OWASP ZAP        → https://owasp.org/www-project-zap
   - Security scanner
   - Penetration testing
   - API scanning
   - Free & open source

🎯 Burp Suite       → https://portswigger.net/burp
   - Web security
   - Professional tool
   - Proxy & scanner
   - Community edition

🛡️ Snyk             → https://snyk.io
   - Vulnerability scanning
   - Dependency check
   - Container scanning
   - IDE integration
   - npm install -g snyk

🔒 npm audit        → Built into npm
   - Dependency scanner
   - Security advisories
   - Auto fix
   - npm audit fix

⚡ ESLint Security   → https://github.com/nodesecurity/eslint-plugin-security
   - Code analysis
   - Security patterns
   - npm install -D eslint-plugin-security
```

---

<div align="center">

## 🎯 API Testing

</div>

### API Testing Tools 🌐

```javascript
// 🧪 Supertest for API Testing
const request = require("supertest");
const app = require("../app");

describe("API Tests", () => {
  test("GET /api/users", async () => {
    const response = await request(app)
      .get("/api/users")
      .set("Authorization", "Bearer token123")
      .expect("Content-Type", /json/)
      .expect(200);

    expect(response.body).toHaveProperty("users");
    expect(response.body.users).toHaveLength(10);
  });

  test("POST /api/users", async () => {
    const newUser = {
      name: "MrDib",
      email: "mrdib@test.com",
    };

    const response = await request(app)
      .post("/api/users")
      .send(newUser)
      .expect(201);

    expect(response.body.user).toMatchObject(newUser);
  });
});

// 🎭 Pact for Contract Testing
const { Pact } = require("@pact-foundation/pact");

const provider = new Pact({
  consumer: "Frontend",
  provider: "UserAPI",
  port: 1234,
});

describe("API Contract", () => {
  beforeAll(() => provider.setup());
  afterAll(() => provider.finalize());

  test("get user", async () => {
    await provider.addInteraction({
      state: "user exists",
      uponReceiving: "a request for user",
      withRequest: {
        method: "GET",
        path: "/users/1",
      },
      willRespondWith: {
        status: 200,
        body: {
          id: 1,
          name: "John Doe",
        },
      },
    });

    // Test implementation
  });
});
```

---

<div align="center">

## 🎨 Test Organization

</div>

### Test Structure Best Practices 📁

```
tests/
├── unit/
│   ├── components/
│   │   ├── Button.test.js
│   │   └── Form.test.js
│   ├── utils/
│   │   └── helpers.test.js
│   └── hooks/
│       └── useAuth.test.js
├── integration/
│   ├── auth.test.js
│   └── api.test.js
├── e2e/
│   ├── user-flow.spec.js
│   └── checkout.spec.js
├── fixtures/
│   └── users.json
├── mocks/
│   └── handlers.js
└── setup/
    └── jest.setup.js
```

### Testing Pyramid 🔺

```
           /\
          /  \
         /    \
        / E2E  \       ← Few tests (slow, expensive)
       /--------\
      /    UI    \     ← Some tests (moderate)
     /------------\
    /  Integration \   ← More tests
   /----------------\
  /    Unit Tests    \ ← Many tests (fast, cheap)
 /--------------------\
```

---

<div align="center">

## 💡 MrDib's Testing Tips

</div>

### Do's ✅

```
✓ Write tests first (TDD)
✓ Test behavior, not implementation
✓ Keep tests simple and focused
✓ Use descriptive test names
✓ Mock external dependencies
✓ Run tests in CI/CD
✓ Aim for 80%+ coverage
✓ Test edge cases
```

### Don'ts ❌

```
✗ Test implementation details
✗ Write brittle tests
✗ Ignore flaky tests
✗ Skip error scenarios
✗ Over-mock everything
✗ Test framework code
✗ Forget cleanup
✗ Test private methods
```

### Test Writing Patterns

```javascript
// ✅ GOOD: Descriptive test names
describe("UserAuthentication", () => {
  it("should return 401 when credentials are invalid", () => {});
  it("should return user data when login is successful", () => {});
  it("should refresh token when it expires", () => {});
});

// ✅ GOOD: AAA Pattern
test("user can update profile", () => {
  // Arrange
  const user = createUser({ name: "MrDib" });
  const newName = "MrDib Updated";

  // Act
  const result = updateUserProfile(user.id, { name: newName });

  // Assert
  expect(result.name).toBe(newName);
});

// ✅ GOOD: Test data builders
const createUser = (overrides = {}) => ({
  id: 1,
  name: "Test User",
  email: "test@example.com",
  role: "user",
  ...overrides,
});
```

---

<div align="center">

## 📊 Testing Metrics

</div>

### Coverage Goals 🎯

```
📊 Unit Tests
   - Statements: 80%+
   - Branches: 75%+
   - Functions: 80%+
   - Lines: 80%+

🎯 Integration Tests
   - API endpoints: 100%
   - Critical paths: 100%
   - Error scenarios: 90%+

🌐 E2E Tests
   - Happy paths: 100%
   - Critical user flows: 100%
   - Cross-browser: Major browsers
```

---

<div align="center">

_Remember: Untested code is broken code that you just don't know about yet! 🐛_

</div>
