<div align="center">

# 🎭 End-to-End Testing

### _Test your app like a real user would_ 🚀

![E2E](https://img.shields.io/badge/E2E-Testing-purple?style=for-the-badge)
![Playwright](https://img.shields.io/badge/Playwright-Latest-green?style=for-the-badge&logo=playwright)
![Cypress](https://img.shields.io/badge/Cypress-Latest-blue?style=for-the-badge&logo=cypress)

</div>

---

## 📚 Table of Contents

- [🎯 E2E Testing Fundamentals](#-e2e-testing-fundamentals)
- [🎭 Playwright](#-playwright)
- [🌲 Cypress](#-cypress)
- [🎨 Testing Patterns](#-testing-patterns)
- [🔐 Authentication Testing](#-authentication-testing)
- [🧪 Advanced Techniques](#-advanced-techniques)
- [🚀 CI/CD Integration](#-cicd-integration)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 🎯 E2E Testing Fundamentals

</div>

### Understanding E2E Testing 📖

```javascript
// ═══════════════════════════════════════════
// What is E2E Testing?
// ═══════════════════════════════════════════

/*
End-to-End testing validates complete user flows:
- Tests from user's perspective
- Covers full application stack
- Interacts with real browser
- Validates UI, API, database together

Unit vs Integration vs E2E:

Unit Testing:
  ✅ Fast
  ✅ Isolated
  ❌ Doesn't test integration

Integration Testing:
  ✅ Tests module interaction
  ✅ Faster than E2E
  ❌ Doesn't test UI

E2E Testing:
  ✅ Tests complete flows
  ✅ High confidence
  ❌ Slower
  ❌ More brittle
*/

// ═══════════════════════════════════════════
// Testing Pyramid
// ═══════════════════════════════════════════

/*
       /\
      /E2E\      ← Few (10-20%)
     /------\
    /Integration\   ← Some (20-30%)
   /----------\
  /   Unit    \ ← Many (50-70%)
 /--------------\
*/

// ═══════════════════════════════════════════
// Modern E2E Tools Comparison
// ═══════════════════════════════════════════

/*
Playwright:
  ✅ Multi-browser (Chromium, Firefox, WebKit)
  ✅ Auto-wait built-in
  ✅ Network interception
  ✅ Multiple tabs/contexts
  ✅ Great debugging tools
  ❌ Newer (smaller community)

Cypress:
  ✅ Great DX
  ✅ Time-travel debugging
  ✅ Real-time reload
  ✅ Large community
  ❌ Chrome/Edge only (no Firefox/Safari)
  ❌ No multi-tab support

Puppeteer:
  ✅ Lightweight
  ✅ Google-maintained
  ✅ Great for scraping
  ❌ Chrome/Chromium only
  ❌ No test runner

Selenium:
  ✅ Industry standard
  ✅ Multi-language
  ✅ Widest browser support
  ❌ Slower
  ❌ More complex setup

MrDib's Pick: Playwright 🏆
- Modern API
- Multi-browser
- Great debugging
- Active development
*/
```

---

<div align="center">

## 🎭 Playwright

</div>

### Complete Playwright Guide 🚀

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

# New project
npm init playwright@latest

# Existing project
npm install -D @playwright/test

# Install browsers
npx playwright install

# Install specific browser
npx playwright install chromium
```

```javascript
// ═══════════════════════════════════════════
// Playwright Configuration
// ═══════════════════════════════════════════

// playwright.config.ts
import { defineConfig, devices } from "@playwright/test";

export default defineConfig({
  // Test directory
  testDir: "./e2e",

  // Timeout for each test
  timeout: 30 * 1000,

  // Expect timeout
  expect: {
    timeout: 5000,
  },

  // Run tests in parallel
  fullyParallel: true,

  // Fail build on CI if you accidentally left test.only
  forbidOnly: !!process.env.CI,

  // Retry on CI
  retries: process.env.CI ? 2 : 0,

  // Workers
  workers: process.env.CI ? 1 : undefined,

  // Reporter
  reporter: [
    ["html"],
    ["json", { outputFile: "test-results.json" }],
    ["junit", { outputFile: "test-results.xml" }],
    ["list"],
  ],

  // Shared settings
  use: {
    // Base URL
    baseURL: process.env.BASE_URL || "http://localhost:3000",

    // Collect trace on failure
    trace: "on-first-retry",

    // Screenshot on failure
    screenshot: "only-on-failure",

    // Video on failure
    video: "retain-on-failure",

    // Browser options
    headless: !!process.env.CI,
    viewport: { width: 1280, height: 720 },

    // Ignore HTTPS errors
    ignoreHTTPSErrors: true,

    // Default timeout for actions
    actionTimeout: 10000,

    // Default timeout for navigation
    navigationTimeout: 30000,
  },

  // Test projects for different browsers
  projects: [
    {
      name: "chromium",
      use: { ...devices["Desktop Chrome"] },
    },
    {
      name: "firefox",
      use: { ...devices["Desktop Firefox"] },
    },
    {
      name: "webkit",
      use: { ...devices["Desktop Safari"] },
    },
    // Mobile browsers
    {
      name: "Mobile Chrome",
      use: { ...devices["Pixel 5"] },
    },
    {
      name: "Mobile Safari",
      use: { ...devices["iPhone 13"] },
    },
    // Branded browsers
    {
      name: "Microsoft Edge",
      use: {
        ...devices["Desktop Edge"],
        channel: "msedge",
      },
    },
    {
      name: "Google Chrome",
      use: {
        ...devices["Desktop Chrome"],
        channel: "chrome",
      },
    },
  ],

  // Web server
  webServer: {
    command: "npm run dev",
    url: "http://localhost:3000",
    reuseExistingServer: !process.env.CI,
    timeout: 120 * 1000,
  },
});

// ═══════════════════════════════════════════
// Basic Test Structure
// ═══════════════════════════════════════════

import { test, expect } from "@playwright/test";

test.describe("Feature Name", () => {
  // Runs before each test
  test.beforeEach(async ({ page }) => {
    await page.goto("/");
  });

  // Runs after each test
  test.afterEach(async ({ page }) => {
    await page.close();
  });

  test("should do something", async ({ page }) => {
    // Your test code
  });
});

// ═══════════════════════════════════════════
// Locators (Finding Elements)
// ═══════════════════════════════════════════

// By role (recommended - accessibility friendly)
await page.getByRole("button", { name: "Submit" }).click();
await page.getByRole("textbox", { name: "Email" }).fill("test@example.com");
await page.getByRole("link", { name: "Sign up" }).click();

// By label
await page.getByLabel("Email").fill("test@example.com");
await page.getByLabel("Password").fill("password123");

// By placeholder
await page.getByPlaceholder("Enter your email").fill("test@example.com");

// By text
await page.getByText("Welcome back!").click();
await page.getByText(/welcome/i).click(); // Regex

// By test ID
await page.getByTestId("submit-button").click();

// By CSS selector
await page.locator(".submit-button").click();
await page.locator("#email-input").fill("test@example.com");

// By XPath (not recommended)
await page.locator('xpath=//button[@type="submit"]').click();

// Chaining locators
await page
  .locator(".card")
  .filter({ hasText: "Product" })
  .getByRole("button", { name: "Buy" })
  .click();

// nth element
await page.locator(".item").nth(0).click(); // First
await page.locator(".item").nth(-1).click(); // Last

// ═══════════════════════════════════════════
// Actions
// ═══════════════════════════════════════════

// Click
await page.getByRole("button").click();
await page.getByRole("button").click({ button: "right" }); // Right click
await page.getByRole("button").dblclick(); // Double click

// Type
await page.getByLabel("Email").fill("test@example.com");
await page.getByLabel("Email").type("test@example.com"); // Character by character
await page.getByLabel("Email").press("Enter");
await page.getByLabel("Email").press("Control+A"); // Keyboard shortcuts

// Select
await page.getByLabel("Country").selectOption("USA");
await page.getByLabel("Country").selectOption({ label: "United States" });
await page.getByLabel("Country").selectOption({ value: "us" });

// Check/Uncheck
await page.getByLabel("Accept terms").check();
await page.getByLabel("Subscribe").uncheck();

// Upload files
await page.getByLabel("Upload").setInputFiles("path/to/file.pdf");
await page.getByLabel("Upload").setInputFiles(["file1.pdf", "file2.pdf"]);

// Hover
await page.getByRole("button").hover();

// Drag and drop
await page.locator("#source").dragTo(page.locator("#target"));

// Focus
await page.getByLabel("Email").focus();

// Scroll
await page.locator("#bottom").scrollIntoViewIfNeeded();

// ═══════════════════════════════════════════
// Assertions
// ═══════════════════════════════════════════

// Visibility
await expect(page.getByText("Success")).toBeVisible();
await expect(page.getByText("Loading")).not.toBeVisible();
await expect(page.getByText("Hidden")).toBeHidden();

// Text content
await expect(page.getByRole("heading")).toContainText("Welcome");
await expect(page.getByRole("heading")).toHaveText("Welcome back!");
await expect(page.getByRole("heading")).toHaveText(/welcome/i);

// Count
await expect(page.locator(".item")).toHaveCount(5);

// Attribute
await expect(page.getByRole("button")).toHaveAttribute("disabled");
await expect(page.getByRole("link")).toHaveAttribute("href", "/about");

// Class
await expect(page.locator(".button")).toHaveClass("btn btn-primary");
await expect(page.locator(".button")).toHaveClass(/btn-primary/);

// Value
await expect(page.getByLabel("Email")).toHaveValue("test@example.com");

// URL
await expect(page).toHaveURL("http://localhost:3000/dashboard");
await expect(page).toHaveURL(/dashboard/);

// Title
await expect(page).toHaveTitle("Dashboard - My App");

// Screenshot comparison
await expect(page).toHaveScreenshot("homepage.png");

// Custom assertion
await expect(async () => {
  const response = await page.request.get("/api/status");
  expect(response.status()).toBe(200);
}).toPass();

// ═══════════════════════════════════════════
// Navigation
// ═══════════════════════════════════════════

// Navigate to URL
await page.goto("https://example.com");
await page.goto("/dashboard"); // Relative to baseURL

// Navigate with options
await page.goto("/dashboard", {
  waitUntil: "networkidle", // Wait for network to be idle
  timeout: 30000,
});

// Go back/forward
await page.goBack();
await page.goForward();

// Reload
await page.reload();

// Wait for navigation
await Promise.all([page.waitForNavigation(), page.getByRole("button").click()]);

// ═══════════════════════════════════════════
// Waiting
// ═══════════════════════════════════════════

// Wait for selector
await page.waitForSelector(".dynamic-content");

// Wait for load state
await page.waitForLoadState("networkidle");
await page.waitForLoadState("domcontentloaded");

// Wait for function
await page.waitForFunction(() => document.querySelectorAll(".item").length > 5);

// Wait for timeout (avoid if possible
await page.waitForTimeout(1000); // Use sparingly

// Wait for specific condition
await page.waitForFunction(() => {
  return window.myApp.isReady === true;
});

// ═══════════════════════════════════════════
// API Testing with Playwright
// ═══════════════════════════════════════════

test("API request", async ({ request }) => {
  // GET request
  const response = await request.get("/api/users");
  expect(response.status()).toBe(200);

  const users = await response.json();
  expect(users).toHaveLength(10);

  // POST request
  const createResponse = await request.post("/api/users", {
    data: {
      name: "MrDib",
      email: "test@example.com",
    },
  });

  expect(createResponse.status()).toBe(201);
  const user = await createResponse.json();
  expect(user).toHaveProperty("id");
});

// Intercept and modify requests
test("intercept API", async ({ page }) => {
  // Mock API response
  await page.route("**/api/users", async (route) => {
    await route.fulfill({
      status: 200,
      contentType: "application/json",
      body: JSON.stringify({
        users: [{ id: 1, name: "Mocked User" }],
      }),
    });
  });

  await page.goto("/users");
  await expect(page.getByText("Mocked User")).toBeVisible();
});

// Continue original request with modifications
await page.route("**/api/**", async (route) => {
  const headers = {
    ...route.request().headers(),
    "X-Custom-Header": "custom-value",
  };

  await route.continue({ headers });
});

// Abort requests
await page.route("**/analytics/**", (route) => route.abort());

// ═══════════════════════════════════════════
// Multi-Page/Multi-Tab Testing
// ═══════════════════════════════════════════

test("multiple tabs", async ({ context }) => {
  const page1 = await context.newPage();
  const page2 = await context.newPage();

  await page1.goto("/admin");
  await page2.goto("/user");

  // Interact with both pages
  await page1.getByRole("button", { name: "Update" }).click();
  await expect(page2.getByText("Updated")).toBeVisible();

  await page1.close();
  await page2.close();
});

// Listen for new pages
test("popup window", async ({ context, page }) => {
  const [popup] = await Promise.all([
    context.waitForEvent("page"),
    page.getByRole("button", { name: "Open popup" }).click(),
  ]);

  await expect(popup.getByRole("heading")).toContainText("Popup Window");
  await popup.close();
});

// ═══════════════════════════════════════════
// File Downloads
// ═══════════════════════════════════════════

test("download file", async ({ page }) => {
  const [download] = await Promise.all([
    page.waitForEvent("download"),
    page.getByRole("button", { name: "Download" }).click(),
  ]);

  // Save file
  const path = await download.path();
  console.log(path);

  // Get filename
  console.log(download.suggestedFilename());

  // Save to specific location
  await download.saveAs("/path/to/save/file.pdf");
});

// ═══════════════════════════════════════════
// Browser Context & Storage
// ═══════════════════════════════════════════

// Set cookies
await context.addCookies([
  {
    name: "session",
    value: "abc123",
    domain: "localhost",
    path: "/",
  },
]);

// Get cookies
const cookies = await context.cookies();

// Local storage
await page.evaluate(() => {
  localStorage.setItem("token", "my-token");
});

// Session storage
await page.evaluate(() => {
  sessionStorage.setItem("key", "value");
});

// Save storage state
await context.storageState({ path: "auth.json" });

// Load storage state
const context = await browser.newContext({
  storageState: "auth.json",
});
```

---

<div align="center">

## 🔐 Authentication Testing

</div>

### Handling Auth in E2E Tests 🔑

```javascript
// ═══════════════════════════════════════════
// Method 1: Login Before Each Test
// ═══════════════════════════════════════════

test.beforeEach(async ({ page }) => {
  await page.goto('/login');
  await page.getByLabel('Email').fill('test@example.com');
  await page.getByLabel('Password').fill('password123');
  await page.getByRole('button', { name: 'Login' }).click();

  await expect(page).toHaveURL('/dashboard');
});

// ═══════════════════════════════════════════
// Method 2: Global Setup (Recommended)
// ═══════════════════════════════════════════

// global-setup.ts
import { chromium, FullConfig } from '@playwright/test';

async function globalSetup(config: FullConfig) {
  const browser = await chromium.launch();
  const page = await browser.newPage();

  // Login
  await page.goto('http://localhost:3000/login');
  await page.getByLabel('Email').fill('test@example.com');
  await page.getByLabel('Password').fill('password123');
  await page.getByRole('button', { name: 'Login' }).click();

  await page.waitForURL('**/dashboard');

  // Save storage state
  await page.context().storageState({ path: 'auth.json' });

  await browser.close();
}

export default globalSetup;

// playwright.config.ts
export default defineConfig({
  globalSetup: require.resolve('./global-setup'),
  use: {
    storageState: 'auth.json',
  },
});

// ═══════════════════════════════════════════
// Method 3: API-Based Login
// ═══════════════════════════════════════════

test.beforeEach(async ({ page, request }) => {
  // Login via API
  const response = await request.post('/api/auth/login', {
    data: {
      email: 'test@example.com',
      password: 'password123',
    },
  });

  const { token } = await response.json();

  // Set token in storage
  await page.addInitScript((token) => {
    localStorage.setItem('auth-token', token);
  }, token);

  await page.goto('/dashboard');
});

// ═══════════════════════════════════════════
// Method 4: Fixture for Auth
// ═══════════════════════════════════════════

// fixtures.ts
import { test as base } from '@playwright/test';

export const test = base.extend({
  authenticatedPage: async ({ page, request }, use) => {
    // Login
    const response = await request.post('/api/auth/login', {
      data: {
        email: 'test@example.com',
        password: 'password123',
      },
    });

    const { token } = await response.json();

    await page.addInitScript((token) => {
      localStorage.setItem('auth-token', token);
    }, token);

    await use(page);
  },
});

// Usage
test('authenticated test', async ({ authenticatedPage }) => {
  await authenticatedPage.goto('/profile');
  await expect(authenticatedPage.getByText('My Profile')).toBeVisible();
});

// ═══════════════════════════════════════════
// Testing Logout
// ═══════════════════════════════════════════

test('logout', async ({ page }) => {
  await page.goto('/dashboard');

  await page.getByRole('button', { name: 'User menu' }).click();
  await page.getByRole('menuitem', { name: 'Logout' }).click();

  await expect(page).toHaveURL('/login');
  await expect(page.getByRole('button', { name: 'Login' })).toBeVisible();

  // Verify protected route redirects
  await page.goto('/dashboard');
  await expect(page).toHaveURL('/login');
});

// ═══════════════════════════════════════════
// Testing Session Expiry
// ═══════════════════════════════════════════

test('session expiry', async ({ page, context }) => {
  // Set expired token
  await context.addCookies([
    {
      name: 'session',
      value: 'expired-token',
      domain: 'localhost',
      path: '/',
      expires: Date.now() / 1000 - 3600, // 1 hour ago
    },
  ]);

  await page.goto('/dashboard');

  // Should redirect to login
  await expect(page).toHaveURL('/login');
  await expect(page.getByText('Session expired')).toBeVisible();
});
```

---

<div align="center">

## 🎨 Testing Patterns

</div>

### Page Object Model (POM) 📄

```javascript
// ═══════════════════════════════════════════
// Page Object Pattern
// ═══════════════════════════════════════════

// pages/LoginPage.ts
import { Page, Locator } from '@playwright/test';

export class LoginPage {
  readonly page: Page;
  readonly emailInput: Locator;
  readonly passwordInput: Locator;
  readonly loginButton: Locator;
  readonly errorMessage: Locator;

  constructor(page: Page) {
    this.page = page;
    this.emailInput = page.getByLabel('Email');
    this.passwordInput = page.getByLabel('Password');
    this.loginButton = page.getByRole('button', { name: 'Login' });
    this.errorMessage = page.locator('.error-message');
  }

  async goto() {
    await this.page.goto('/login');
  }

  async login(email: string, password: string) {
    await this.emailInput.fill(email);
    await this.passwordInput.fill(password);
    await this.loginButton.click();
  }

  async expectError(message: string) {
    await expect(this.errorMessage).toBeVisible();
    await expect(this.errorMessage).toContainText(message);
  }
}

// pages/DashboardPage.ts
export class DashboardPage {
  readonly page: Page;
  readonly welcomeMessage: Locator;
  readonly userMenu: Locator;

  constructor(page: Page) {
    this.page = page;
    this.welcomeMessage = page.getByRole('heading', { name: /welcome/i });
    this.userMenu = page.getByRole('button', { name: 'User menu' });
  }

  async goto() {
    await this.page.goto('/dashboard');
  }

  async logout() {
    await this.userMenu.click();
    await this.page.getByRole('menuitem', { name: 'Logout' }).click();
  }
}

// ═══════════════════════════════════════════
// Using Page Objects
// ═══════════════════════════════════════════

import { test, expect } from '@playwright/test';
import { LoginPage } from './pages/LoginPage';
import { DashboardPage } from './pages/DashboardPage';

test('login flow', async ({ page }) => {
  const loginPage = new LoginPage(page);
  const dashboardPage = new DashboardPage(page);

  await loginPage.goto();
  await loginPage.login('test@example.com', 'password123');

  await expect(page).toHaveURL('/dashboard');
  await expect(dashboardPage.welcomeMessage).toBeVisible();
});

// ═══════════════════════════════════════════
// Custom Fixtures
// ═══════════════════════════════════════════

// fixtures.ts
import { test as base } from '@playwright/test';
import { LoginPage } from './pages/LoginPage';
import { DashboardPage } from './pages/DashboardPage';

type MyFixtures = {
  loginPage: LoginPage;
  dashboardPage: DashboardPage;
};

export const test = base.extend<MyFixtures>({
  loginPage: async ({ page }, use) => {
    await use(new LoginPage(page));
  },

  dashboardPage: async ({ page }, use) => {
    await use(new DashboardPage(page));
  },
});

// Usage with fixtures
test('login with fixtures', async ({ loginPage, dashboardPage, page }) => {
  await loginPage.goto();
  await loginPage.login('test@example.com', 'password123');

  await expect(page).toHaveURL('/dashboard');
  await expect(dashboardPage.welcomeMessage).toBeVisible();
});

// ═══════════════════════════════════════════
// Test Data Fixture
// ═══════════════════════════════════════════

type TestData = {
  testUser: {
    email: string;
    password: string;
    name: string;
  };
};

export const test = base.extend<TestData>({
  testUser: async ({}, use) => {
    const user = {
      email: `test-${Date.now()}@example.com`,
      password: 'SecurePass123!',
      name: 'Test User',
    };

    // Cleanup after test
    await use(user);

    // Optional: Delete test user
  },
});

// ═══════════════════════════════════════════
// Component Testing Pattern
// ═══════════════════════════════════════════

class ButtonComponent {
  constructor(private locator: Locator) {}

  async click() {
    await this.locator.click();
  }

  async expectText(text: string) {
    await expect(this.locator).toContainText(text);
  }

  async expectDisabled() {
    await expect(this.locator).toBeDisabled();
  }
}

class FormComponent {
  constructor(private page: Page, private formSelector: string) {}

  field(name: string) {
    return this.page.locator(`${this.formSelector} [name="${name}"]`);
  }

  button(name: string) {
    return new ButtonComponent(
      this.page.locator(`${this.formSelector} button:has-text("${name}")`)
    );
  }

  async submit() {
    await this.page.locator(`${this.formSelector}`).press('Enter');
  }
}
```

---

<div align="center">

## 🌲 Cypress

</div>

### E2E with Cypress 🚀

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install -D cypress

# Open Cypress
npx cypress open

# Run headless
npx cypress run
```

```javascript
// ═══════════════════════════════════════════
// Cypress Configuration
// ═══════════════════════════════════════════

// cypress.config.ts
import { defineConfig } from 'cypress';

export default defineConfig({
  e2e: {
    baseUrl: 'http://localhost:3000',
    viewportWidth: 1280,
    viewportHeight: 720,

    // Video
    video: true,
    videoCompression: 32,

    // Screenshots
    screenshotOnRunFailure: true,

    // Timeouts
    defaultCommandTimeout: 10000,
    pageLoadTimeout: 30000,
    requestTimeout: 10000,

    // Retries
    retries: {
      runMode: 2,
      openMode: 0,
    },

    setupNodeEvents(on, config) {
      // Tasks
      on('task', {
        log(message) {
          console.log(message);
          return null;
        },

        seedDatabase() {
          // Seed database
          return null;
        },

        clearDatabase() {
          // Clear database
          return null;
        },
      });

      return config;
    },
  },
});

// ═══════════════════════════════════════════
// Cypress Tests
// ═══════════════════════════════════════════

// cypress/e2e/login.cy.ts
describe('Authentication', () => {
  beforeEach(() => {
    cy.visit('/login');
  });

  it('should login successfully', () => {
    cy.get('[data-cy="email"]').type('test@example.com');
    cy.get('[data-cy="password"]').type('password123');
    cy.get('[data-cy="submit"]').click();

    cy.url().should('include', '/dashboard');
    cy.get('h1').should('contain', 'Dashboard');
  });

  it('should show error for invalid credentials', () => {
    cy.get('[data-cy="email"]').type('wrong@example.com');
    cy.get('[data-cy="password"]').type('wrongpass');
    cy.get('[data-cy="submit"]').click();

    cy.get('[data-cy="error"]').should('be.visible');
    cy.get('[data-cy="error"]').should('contain', 'Invalid credentials');
  });
});

// ═══════════════════════════════════════════
// Custom Commands
// ═══════════════════════════════════════════

// cypress/support/commands.ts
declare global {
  namespace Cypress {
    interface Chainable {
      login(email: string, password: string): Chainable<void>;
      logout(): Chainable<void>;
      getBySel(selector: string): Chainable<JQuery<HTMLElement>>;
    }
  }
}

Cypress.Commands.add('login', (email, password) => {
  cy.session([email, password], () => {
    cy.visit('/login');
    cy.get('[data-cy="email"]').type(email);
    cy.get('[data-cy="password"]').type(password);
    cy.get('[data-cy="submit"]').click();

    cy.url().should('not.include', '/login');
  });
});

Cypress.Commands.add('logout', () => {
  cy.get('[data-cy="user-menu"]').click();
  cy.get('[data-cy="logout"]').click();
});

Cypress.Commands.add('getBySel', (selector) => {
  return cy.get(`[data-cy="${selector}"]`);
});

// Usage
cy.getBySel('submit-button').click();

// ═══════════════════════════════════════════
// API Testing with Cypress
// ═══════════════════════════════════════════

describe('API Testing', () => {
it('should fetch users', () => {
cy.request('GET', '/api/users').then((response) => {
expect(response.status).to.eq(200);
expect(response.body).to.have.length(10);
expect(response.body[0]).to.have.property('name');
});
});

it('should create user', () => {
cy.request('POST', '/api/users', {
name: 'MrDib',
email: 'test@example.com',
}).then((response) => {
expect(response.status).to.eq(201);
expect(response.body).to.have.property('id');
});
});
});

// Intercept API calls
it('should intercept API', () => {
cy.intercept('GET', '/api/users', {
statusCode: 200,
body: {
users: [{ id: 1, name: 'Mocked User' }],
},
}).as('getUsers');

cy.visit('/users');
cy.wait('@getUsers');

cy.contains('Mocked User').should('be.visible');
});

// Modify request
cy.intercept('POST', '/api/users', (req) => {
req.headers['x-custom-header'] = 'custom-value';
req.body.modified = true;
});

// ═══════════════════════════════════════════
// Cypress Real-World Example
// ═══════════════════════════════════════════

describe('Todo App', () => {
beforeEach(() => {
cy.login('test@example.com', 'password123');
cy.visit('/todos');
});

it('should manage todos', () => {
// Create todo
cy.getBySel('todo-input').type('Write tests{enter}');
cy.getBySel('todo-list').should('contain', 'Write tests');

    // Mark complete
    cy.contains('Write tests')
      .parent()
      .find('[data-cy="checkbox"]')
      .check();

    cy.contains('Write tests')
      .parent()
      .should('have.class', 'completed');

    // Edit todo
    cy.contains('Write tests').dblclick();
    cy.getBySel('edit-input')
      .clear()
      .type('Write E2E tests{enter}');

    cy.contains('Write E2E tests').should('exist');

    // Delete todo
    cy.contains('Write E2E tests')
      .parent()
      .find('[data-cy="delete"]')
      .click();

    cy.contains('Write E2E tests').should('not.exist');

});

it('should filter todos', () => {
// Create multiple todos
['Todo 1', 'Todo 2', 'Todo 3'].forEach(todo => {
cy.getBySel('todo-input').type(`${todo}{enter}`);
});

    // Complete first todo
    cy.contains('Todo 1')
      .parent()
      .find('[data-cy="checkbox"]')
      .check();

    // Filter active
    cy.getBySel('filter-active').click();
    cy.getBySel('todo-list').children().should('have.length', 2);

    // Filter completed
    cy.getBySel('filter-completed').click();
    cy.getBySel('todo-list').children().should('have.length', 1);
    cy.contains('Todo 1').should('exist');

});
});
```

---

<div align="center">

## 🧪 Advanced Techniques

</div>

### Visual Regression Testing 📸

```javascript
// ═══════════════════════════════════════════
// Playwright Visual Testing
// ═══════════════════════════════════════════

import { test, expect } from "@playwright/test";

test("visual regression", async ({ page }) => {
  await page.goto("/");

  // Full page screenshot
  await expect(page).toHaveScreenshot("homepage.png", {
    fullPage: true,
  });

  // Element screenshot
  const header = page.locator("header");
  await expect(header).toHaveScreenshot("header.png");

  // With threshold
  await expect(page).toHaveScreenshot("homepage.png", {
    maxDiffPixels: 100, // Allow 100 pixel difference
  });

  // Mask dynamic elements
  await expect(page).toHaveScreenshot("page-with-mask.png", {
    mask: [page.locator(".timestamp")],
  });
});

// ═══════════════════════════════════════════
// Percy (Visual Testing Service)
// ═══════════════════════════════════════════

// npm install -D @percy/playwright

import percySnapshot from "@percy/playwright";

test("percy snapshot", async ({ page }) => {
  await page.goto("/");
  await percySnapshot(page, "Homepage");

  // Responsive snapshots
  await percySnapshot(page, "Homepage - Desktop", {
    widths: [768, 1024, 1280],
  });
});

// ═══════════════════════════════════════════
// Accessibility Testing
// ═══════════════════════════════════════════

// npm install -D @axe-core/playwright

import { injectAxe, checkA11y } from "@axe-core/playwright";

test("accessibility", async ({ page }) => {
  await page.goto("/");

  // Inject axe
  await injectAxe(page);

  // Check accessibility
  await checkA11y(page, null, {
    detailedReport: true,
  });

  // Check specific element
  await checkA11y(page, ".navigation", {
    rules: {
      "color-contrast": { enabled: true },
    },
  });
});

// ═══════════════════════════════════════════
// Performance Testing
// ═══════════════════════════════════════════

test("performance metrics", async ({ page }) => {
  await page.goto("/");

  // Get performance metrics
  const metrics = await page.evaluate(() => {
    const navigation = performance.getEntriesByType("navigation")[0];
    const paint = performance.getEntriesByType("paint");

    return {
      domContentLoaded:
        navigation.domContentLoadedEventEnd -
        navigation.domContentLoadedEventStart,
      loadComplete: navigation.loadEventEnd - navigation.loadEventStart,
      firstPaint: paint.find((p) => p.name === "first-paint")?.startTime,
      firstContentfulPaint: paint.find(
        (p) => p.name === "first-contentful-paint"
      )?.startTime,
    };
  });

  console.log(metrics);

  // Assert performance
  expect(metrics.domContentLoaded).toBeLessThan(2000);
  expect(metrics.firstContentfulPaint).toBeLessThan(1500);
});

// Web Vitals
test("web vitals", async ({ page }) => {
  await page.goto("/");

  const vitals = await page.evaluate(() => {
    return new Promise((resolve) => {
      let vitals = {};

      new PerformanceObserver((list) => {
        for (const entry of list.getEntries()) {
          if (entry.name === "first-contentful-paint") {
            vitals.FCP = entry.startTime;
          }
          if (entry.entryType === "largest-contentful-paint") {
            vitals.LCP = entry.startTime;
          }
        }
        resolve(vitals);
      }).observe({ entryTypes: ["paint", "largest-contentful-paint"] });
    });
  });

  expect(vitals.FCP).toBeLessThan(1800);
  expect(vitals.LCP).toBeLessThan(2500);
});
```

---

<div align="center">

## 🚀 CI/CD Integration

</div>

### Running Tests in CI 🤖

```yaml
# ═══════════════════════════════════════════
# GitHub Actions - Playwright
# ═══════════════════════════════════════════

# .github/workflows/e2e.yml
name: E2E Tests

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  test:
    timeout-minutes: 60
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - uses: actions/setup-node@v4
        with:
          node-version: 20

      - name: Install dependencies
        run: npm ci

      - name: Install Playwright Browsers
        run: npx playwright install --with-deps

      - name: Run E2E tests
        run: npx playwright test
        env:
          BASE_URL: ${{ secrets.BASE_URL }}

      - uses: actions/upload-artifact@v4
        if: always()
        with:
          name: playwright-report
          path: playwright-report/
          retention-days: 30

      - uses: actions/upload-artifact@v4
        if: failure()
        with:
          name: test-results
          path: test-results/
          retention-days: 7

# ═══════════════════════════════════════════
# Parallel Testing in CI
# ═══════════════════════════════════════════

jobs:
  test:
    strategy:
      fail-fast: false
      matrix:
        shardIndex: [1, 2, 3, 4]
        shardTotal: [4]

    steps:
      - name: Run E2E tests
        run: npx playwright test --shard=${{ matrix.shardIndex }}/${{ matrix.shardTotal }}

# ═══════════════════════════════════════════
# Docker for Consistent Environment
# ═══════════════════════════════════════════

# Dockerfile.e2e
FROM mcr.microsoft.com/playwright:v1.40.0-focal

WORKDIR /app

COPY package*.json ./
RUN npm ci

COPY . .

CMD ["npx", "playwright", "test"]

# docker-compose.yml
version: '3.8'

services:
  app:
    build: .
    ports:
      - "3000:3000"
    environment:
      - NODE_ENV=production

  e2e:
    build:
      context: .
      dockerfile: Dockerfile.e2e
    depends_on:
      - app
    environment:
      - BASE_URL=http://app:3000
    volumes:
      - ./test-results:/app/test-results
      - ./playwright-report:/app/playwright-report

# Run tests
# docker-compose up --abort-on-container-exit e2e

# ═══════════════════════════════════════════
# Cypress in CI
# ═══════════════════════════════════════════

name: Cypress Tests

on: [push]

jobs:
  cypress-run:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Cypress run
        uses: cypress-io/github-action@v6
        with:
          build: npm run build
          start: npm start
          wait-on: 'http://localhost:3000'
          browser: chrome
          record: true
        env:
          CYPRESS_RECORD_KEY: ${{ secrets.CYPRESS_RECORD_KEY }}

      - uses: actions/upload-artifact@v4
        if: failure()
        with:
          name: cypress-screenshots
          path: cypress/screenshots

      - uses: actions/upload-artifact@v4
        if: always()
        with:
          name: cypress-videos
          path: cypress/videos
```

---

<div align="center">

## 💡 Best Practices

</div>

### E2E Testing Guidelines ⭐

```javascript
// ═══════════════════════════════════════════
// 1. Test User Journeys, Not Implementation
// ═══════════════════════════════════════════

// ❌ BAD: Testing implementation details
test("should update state", async ({ page }) => {
  // Testing internal state
});

// ✅ GOOD: Testing user behavior
test("user can complete purchase", async ({ page }) => {
  await page.goto("/shop");
  await page.getByRole("button", { name: "Add to Cart" }).click();
  await page.getByRole("link", { name: "Checkout" }).click();
  await page.getByLabel("Card Number").fill("4242424242424242");
  await page.getByRole("button", { name: "Pay" }).click();

  await expect(page).toHaveURL("/order-confirmation");
  await expect(page.getByText("Order confirmed")).toBeVisible();
});

// ═══════════════════════════════════════════
// 2. Use Stable Selectors
// ═══════════════════════════════════════════

// ❌ BAD: Brittle selectors
await page.click(".btn.submit"); // Classes can change
await page.click("button:nth-child(3)"); // Position can change

// ✅ GOOD: Stable selectors
await page.getByRole("button", { name: "Submit" });
await page.getByTestId("submit-button");
await page.getByLabel("Email");

// ═══════════════════════════════════════════
// 3. Keep Tests Independent
// ═══════════════════════════════════════════

// ❌ BAD: Tests depend on each other
test("create user", async ({ page }) => {
  // Creates user with specific ID
});

test("update user", async ({ page }) => {
  // Assumes user from previous test exists
});

// ✅ GOOD: Independent tests
test.beforeEach(async ({ page, request }) => {
  // Create fresh test data for each test
  await request.post("/api/test/seed");
});

test("update user", async ({ page }) => {
  // Test has its own data
});

// ═══════════════════════════════════════════
// 4. Handle Async Operations
// ═══════════════════════════════════════════

// ✅ GOOD: Playwright auto-waits
await page.getByRole("button").click(); // Waits for element
await expect(page.getByText("Success")).toBeVisible(); // Waits for assertion

// Explicit waits when needed
await page.waitForLoadState("networkidle");
await page.waitForResponse((resp) => resp.url().includes("/api/users"));

// ═══════════════════════════════════════════
// 5. Test Different States
// ═══════════════════════════════════════════

test.describe("Form states", () => {
  test("empty state", async ({ page }) => {
    await page.goto("/form");
    await expect(page.getByRole("button", { name: "Submit" })).toBeDisabled();
  });

  test("loading state", async ({ page }) => {
    await page.goto("/form");
    await page.getByRole("button").click();
    await expect(page.getByText("Loading...")).toBeVisible();
  });

  test("error state", async ({ page }) => {
    await page.route("**/api/submit", (route) => route.abort());
    await page.goto("/form");
    await page.getByLabel("Name").fill("Test");
    await page.getByRole("button").click();
    await expect(page.getByText("Error occurred")).toBeVisible();
  });

  test("success state", async ({ page }) => {
    await page.goto("/form");
    await page.getByLabel("Name").fill("Test");
    await page.getByRole("button").click();
    await expect(page.getByText("Success")).toBeVisible();
  });
});

// ═══════════════════════════════════════════
// 6. Organize Tests Well
// ═══════════════════════════════════════════

// Good structure
test.describe("Authentication", () => {
  test.describe("Login", () => {
    test("successful login", async ({ page }) => {});
    test("invalid credentials", async ({ page }) => {});
    test("remember me", async ({ page }) => {});
  });

  test.describe("Signup", () => {
    test("successful signup", async ({ page }) => {});
    test("duplicate email", async ({ page }) => {});
    test("password validation", async ({ page }) => {});
  });
});

// ═══════════════════════════════════════════
// 7. Mock External Services
// ═══════════====════════════════════════════

// ✅ GOOD: Mock external APIs
test('payment with mocked gateway', async ({ page }) => {
await page.route('**/api/payment/**', async (route) => {
await route.fulfill({
status: 200,
contentType: 'application/json',
body: JSON.stringify({
success: true,
transactionId: 'mock-123',
}),
});
});

await page.goto('/checkout');
await page.getByRole('button', { name: 'Pay' }).click();
await expect(page).toHaveURL('/success');
});

// Mock third-party scripts
await page.addInitScript(() => {
window.analytics = {
track: () => {},
identify: () => {},
};
});

// ═══════════════════════════════════════════
// 8. Use Test IDs for Stability
// ═══════════════════════════════════════════

// In your components
<button data-testid="submit-button">Submit</button>

<div data-testid="user-profile">...</div>

// In tests
await page.getByTestId('submit-button').click();
await expect(page.getByTestId('user-profile')).toBeVisible();

// ═══════════════════════════════════════════
// 9. Test Responsive Design
// ═══════════════════════════════════════════

const viewports = [
{ width: 1920, height: 1080, device: 'Desktop' },
{ width: 768, height: 1024, device: 'Tablet' },
{ width: 375, height: 667, device: 'Mobile' },
];

viewports.forEach(({ width, height, device }) => {
test(`responsive on ${device}`, async ({ page }) => {
await page.setViewportSize({ width, height });
await page.goto('/');

    if (device === 'Mobile') {
      await expect(page.getByRole('button', { name: 'Menu' })).toBeVisible();
    } else {
      await expect(page.getByRole('navigation')).toBeVisible();
    }

});
});

// ═══════════════════════════════════════════
// 10. Clean Test Data
// ═══════════════════════════════════════════

test.afterEach(async ({ request }) => {
// Clean up test data
await request.delete('/api/test/cleanup');
});

// Use unique identifiers
const testId = `test-${Date.now()}`;
const email = `test-${testId}@example.com`;

// ═══════════════════════════════════════════
// 11. Performance Considerations
// ═══════════════════════════════════════════

// Run tests in parallel
test.describe.configure({ mode: 'parallel' });

// Or sequential when needed
test.describe.configure({ mode: 'serial' });

// Reuse authentication
test.use({ storageState: 'auth.json' });

// ═══════════════════════════════════════════
// 12. Debugging Tips
// ═══════════════════════════════════════════

// Run in headed mode
// npx playwright test --headed

// Debug mode
// npx playwright test --debug

// Pause execution
test('debug test', async ({ page }) => {
await page.goto('/');
await page.pause(); // Opens Playwright Inspector
await page.getByRole('button').click();
});

// Console logs
test('with logging', async ({ page }) => {
page.on('console', msg => console.log(msg.text()));
await page.goto('/');
});

// Screenshot on specific step
await page.screenshot({ path: 'debug.png' });

// Video recording
test.use({ video: 'on' });

// ═══════════════════════════════════════════
// 13. Error Handling
// ═══════════════════════════════════════════

// ✅ GOOD: Handle expected errors gracefully
test('handles network error', async ({ page }) => {
await page.route('\*\*/api/data', route => route.abort());

await page.goto('/');

await expect(page.getByText('Failed to load')).toBeVisible();
await expect(page.getByRole('button', { name: 'Retry' })).toBeVisible();
});

// Retry flaky tests
test('flaky test', async ({ page }) => {
test.setTimeout(60000);

await expect(async () => {
await page.goto('/');
await expect(page.getByText('Dynamic content')).toBeVisible();
}).toPass({
timeout: 30000,
intervals: [1000, 2000, 5000],
});
});
```

---

### Quick Reference 📋

```javascript
// ═══════════════════════════════════════════
// Playwright Cheat Sheet
// ═══════════════════════════════════════════

// Navigation
await page.goto(url);
await page.goBack();
await page.goForward();
await page.reload();

// Locators
page.getByRole("button", { name: "Submit" });
page.getByLabel("Email");
page.getByPlaceholder("Enter email");
page.getByText("Welcome");
page.getByTestId("submit");
page.locator(".class");

// Actions
await locator.click();
await locator.fill("text");
await locator.type("text");
await locator.press("Enter");
await locator.check();
await locator.uncheck();
await locator.selectOption("value");
await locator.hover();

// Assertions
await expect(locator).toBeVisible();
await expect(locator).toBeHidden();
await expect(locator).toBeEnabled();
await expect(locator).toBeDisabled();
await expect(locator).toHaveText("text");
await expect(locator).toContainText("text");
await expect(locator).toHaveValue("value");
await expect(locator).toHaveCount(5);
await expect(page).toHaveURL("url");
await expect(page).toHaveTitle("title");

// Waiting
await page.waitForSelector(".selector");
await page.waitForLoadState("networkidle");
await page.waitForFunction(() => condition);
await page.waitForResponse(url);

// API
await request.get(url);
await request.post(url, { data });
await page.route(url, (route) => route.fulfill());

// Multiple pages
await context.newPage();
await page.close();

// Storage
await context.storageState({ path: "auth.json" });
await browser.newContext({ storageState: "auth.json" });

// ═══════════════════════════════════════════
// Cypress Cheat Sheet
// ═══════════════════════════════════════════

// Navigation
cy.visit(url);
cy.go("back");
cy.go("forward");
cy.reload();

// Selectors
cy.get(".selector");
cy.contains("text");
cy.get('[data-cy="selector"]');

// Actions
cy.click();
cy.type("text");
cy.clear();
cy.check();
cy.uncheck();
cy.select("option");
cy.submit();

// Assertions
cy.should("be.visible");
cy.should("have.text", "text");
cy.should("have.value", "value");
cy.should("have.class", "class");
cy.should("have.length", 5);

// Waiting
cy.wait(1000);
cy.wait("@alias");

// API
cy.request("GET", url);
cy.intercept("GET", url).as("alias");

// Custom commands
Cypress.Commands.add("login", (email, password) => {});
```

---

### Common Pitfalls ⚠️

```javascript
// ═══════════════════════════════════════════
// Pitfall 1: Hard-coded waits
// ═══════════════════════════════════════════

// ❌ BAD
await page.waitForTimeout(5000); // Arbitrary wait

// ✅ GOOD
await page.waitForSelector(".loaded");
await expect(page.getByText("Ready")).toBeVisible();

// ═══════════════════════════════════════════
// Pitfall 2: Testing implementation details
// ═══════════════════════════════════════════

// ❌ BAD
await expect(page.locator(".internal-class")).toBeVisible();

// ✅ GOOD
await expect(page.getByRole("button", { name: "Submit" })).toBeVisible();

// ═══════════════════════════════════════════
// Pitfall 3: Brittle selectors
// ═══════════════════════════════════════════

// ❌ BAD
await page.click(".btn.btn-primary.submit"); // CSS classes change
await page.click("button:nth-child(3)"); // Position changes

// ✅ GOOD
await page.getByRole("button", { name: "Submit" }).click();
await page.getByTestId("submit-button").click();

// ═══════════════════════════════════════════
// Pitfall 4: Not cleaning up
// ═══════════════════════════════════════════

// ❌ BAD
test("create user", async () => {
  // Creates data but never cleans up
});

// ✅ GOOD
test("create user", async ({ request }) => {
  const user = await createTestUser();

  // Test code...

  await request.delete(`/api/users/${user.id}`);
});

// ═══════════════════════════════════════════
// Pitfall 5: Slow tests
// ═══════════════════════════════════════════

// ❌ BAD
test.describe.configure({ mode: "serial" }); // Unnecessarily sequential

// ✅ GOOD
test.describe.configure({ mode: "parallel" });

// ❌ BAD
await page.goto("/login");
await page.fill('input[name="email"]', "test@example.com");
await page.fill('input[name="password"]', "password123");
await page.click('button[type="submit"]');

// ✅ GOOD - Use fixtures
test("test", async ({ authenticatedPage }) => {
  // Already logged in
});
```

---

<div align="center">

**Built with 🎭 by MrDib, for Quality-Driven Developers**

_"Test like a user, think like a developer!"_

**Happy Testing!** 🚀

**If you found this helpful, give it a ⭐ star and share with fellow developers!**

</div>

---

### Contributing 🤝

Found better testing patterns? Want to add examples? Contributions are welcome!

1. Fork the repository
2. Add your testing examples
3. Update best practices
4. Submit a pull request

---

### Resources 📚

**📖 Official Documentation:**

- Playwright: https://playwright.dev/docs/intro
- Cypress: https://docs.cypress.io/
- Testing Library: https://testing-library.com/

**🎥 Learning Resources:**

- Playwright YouTube Channel
- Cypress YouTube Channel
- Test Automation University

**🛠️ Tools & Extensions:**

- Playwright VS Code Extension
- Cypress VS Code Extension
- Percy (Visual Testing)
- Axe DevTools (Accessibility)

---

### License 📄

This guide is open source and available under the MIT License.

---

<div align="center">

**Stay tested. Keep shipping. Build with confidence!** 💪✨

🎭 **#E2ETesting** 🎭 **#DevResourceVault** 🎭 **#MrDib** 🎭

### Remember

> _"A bug in production is worth a thousand tests"_

> _"Test user behavior, not implementation"_

> _"Stable selectors = stable tests"_

> _"Mock external dependencies"_

> _"Independent tests = reliable tests"_

> _"If it's hard to test, it's hard to use"_

</div>

---

<div align="center">

**Now go forth and test everything!** 🌟🎭

</div>
