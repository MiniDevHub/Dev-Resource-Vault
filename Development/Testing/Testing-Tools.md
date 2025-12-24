<div align="center">

# 🧪 Testing Tools & Frameworks

### _Because "it works on my machine" is not a valid deployment strategy_ 🚀

![Testing](https://img.shields.io/badge/Testing-Essential-green?style=for-the-badge)
![Jest](https://img.shields.io/badge/Jest-Latest-red?style=for-the-badge&logo=jest)
![Coverage](https://img.shields.io/badge/Coverage-80%25+-blue?style=for-the-badge)

</div>

---

## 📚 Table of Contents

- [🎯 Testing Fundamentals](#-testing-fundamentals)
- [🃏 Unit Testing](#-unit-testing)
- [🧬 Testing Utilities](#-testing-utilities)
- [🎭 Integration Testing](#-integration-testing)
- [🌐 API Testing](#-api-testing)
- [📸 Visual Testing](#-visual-testing)
- [🎯 Test Organization](#-test-organization)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 🎯 Testing Fundamentals

</div>

### Understanding Testing 📖

```javascript
// ═══════════════════════════════════════════
// What is Testing?
// ═══════════════════════════════════════════

/*
Testing validates that code:
- Works as expected
- Handles errors gracefully
- Meets requirements
- Doesn't break when changed
- Is maintainable

Why test?
- Catch bugs early (cheaper to fix)
- Confidence in refactoring
- Documentation of behavior
- Better code design
- Faster development (long-term)
*/

// ═══════════════════════════════════════════
// Testing Pyramid
// ═══════════════════════════════════════════

/*
           /\
          /E2E\        ← Few (5-10%)
         /------\        Slow, expensive
        /  Int.  \     ← Some (15-20%)
       /----------\      Moderate speed
      / Unit Tests \   ← Many (70-80%)
     /--------------\    Fast, cheap
*/

// ═══════════════════════════════════════════
// Types of Testing
// ═══════════════════════════════════════════

const testingTypes = {
  // Unit Testing
  unit: {
    scope: "Single function/component",
    speed: "Very fast (ms)",
    isolation: "Complete",
    examples: "Pure functions, utils",
    coverage: "70-80% of tests",
  },

  // Integration Testing
  integration: {
    scope: "Multiple units working together",
    speed: "Fast to moderate",
    isolation: "Some mocking",
    examples: "API routes, database queries",
    coverage: "15-20% of tests",
  },

  // End-to-End Testing
  e2e: {
    scope: "Complete user flows",
    speed: "Slow (seconds)",
    isolation: "No mocking",
    examples: "Login flow, checkout",
    coverage: "5-10% of tests",
  },

  // Component Testing
  component: {
    scope: "UI components",
    speed: "Fast",
    isolation: "Props/state only",
    examples: "Button, Form, Modal",
    coverage: "All components",
  },

  // Visual Regression
  visual: {
    scope: "UI appearance",
    speed: "Moderate",
    isolation: "Snapshot comparison",
    examples: "Layout, colors, spacing",
    coverage: "Critical pages",
  },
};
```

---

<div align="center">

## 🃏 Unit Testing

</div>

### Jest - The Complete Testing Framework 🚀

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install -D jest
npm install -D @types/jest

# For React
npm install -D @testing-library/react @testing-library/jest-dom

# Initialize config
npx jest --init
```

```javascript
// ═══════════════════════════════════════════
// Jest Configuration (jest.config.js)
// ═══════════════════════════════════════════

module.exports = {
  // Test environment
  testEnvironment: 'jsdom', // or 'node'

  // Setup files
  setupFilesAfterEnv: ['<rootDir>/jest.setup.js'],

  // Coverage
  collectCoverageFrom: [
    'src/**/*.{js,jsx,ts,tsx}',
    '!src/**/*.d.ts',
    '!src/**/*.stories.{js,jsx,ts,tsx}',
    '!src/**/__tests__/**',
  ],

  coverageThresholds: {
    global: {
      branches: 80,
      functions: 80,
      lines: 80,
      statements: 80,
    },
  },

  // Module paths
  moduleNameMapper: {
    '^@/(.*)$': '<rootDir>/src/$1',
    '\\.(css|less|scss)$': 'identity-obj-proxy',
    '\\.(jpg|jpeg|png|gif|svg)$': '<rootDir>/__mocks__/fileMock.js',
  },

  // Transform files
  transform: {
    '^.+\\.(js|jsx|ts|tsx)$': ['babel-jest', { presets: ['next/babel'] }],
  },

  // Ignore patterns
  testPathIgnorePatterns: ['/node_modules/', '/.next/'],

  // Watch plugins
  watchPlugins: [
    'jest-watch-typeahead/filename',
    'jest-watch-typeahead/testname',
  ],
};

// ═══════════════════════════════════════════
// Setup File (jest.setup.js)
// ═══════════════════════════════════════════

import '@testing-library/jest-dom';

// Mock environment variables
process.env.NEXT_PUBLIC_API_URL = 'http://localhost:3000/api';

// Mock window.matchMedia
Object.defineProperty(window, 'matchMedia', {
  writable: true,
  value: jest.fn().mockImplementation(query => ({
    matches: false,
    media: query,
    onchange: null,
    addListener: jest.fn(),
    removeListener: jest.fn(),
    addEventListener: jest.fn(),
    removeEventListener: jest.fn(),
    dispatchEvent: jest.fn(),
  })),
});

// Mock IntersectionObserver
global.IntersectionObserver = class IntersectionObserver {
  constructor() {}
  disconnect() {}
  observe() {}
  takeRecords() {
    return [];
  }
  unobserve() {}
};

// ═══════════════════════════════════════════
// Basic Jest Tests
// ═══════════════════════════════════════════

// Simple function testing
function add(a, b) {
  return a + b;
}

describe('add function', () => {
  it('should add two numbers', () => {
    expect(add(2, 3)).toBe(5);
  });

  it('should handle negative numbers', () => {
    expect(add(-1, -2)).toBe(-3);
  });

  it('should handle zero', () => {
    expect(add(0, 5)).toBe(5);
  });
});

// ═══════════════════════════════════════════
// Jest Matchers
// ═══════════════════════════════════════════

test('matchers demo', () => {
  // Equality
  expect(2 + 2).toBe(4);
  expect({ name: 'MrDib' }).toEqual({ name: 'MrDib' });

  // Truthiness
  expect(true).toBeTruthy();
  expect(false).toBeFalsy();
  expect(null).toBeNull();
  expect(undefined).toBeUndefined();
  expect('value').toBeDefined();

  // Numbers
  expect(5).toBeGreaterThan(3);
  expect(5).toBeGreaterThanOrEqual(5);
  expect(5).toBeLessThan(10);
  expect(5).toBeLessThanOrEqual(5);
  expect(0.1 + 0.2).toBeCloseTo(0.3);

  // Strings
  expect('MrDib').toMatch(/Dib/);
  expect('testing').toContain('test');

  // Arrays
  expect([1, 2, 3]).toContain(2);
  expect([1, 2, 3]).toHaveLength(3);

  // Objects
  expect({ a: 1, b: 2 }).toHaveProperty('a');
  expect({ a: 1, b: 2 }).toMatchObject({ a: 1 });

  // Exceptions
  expect(() => {
    throw new Error('fail');
  }).toThrow('fail');

  // Async
  await expect(Promise.resolve('success')).resolves.toBe('success');
  await expect(Promise.reject('error')).rejects.toBe('error');
});

// ═══════════════════════════════════════════
// Mocking in Jest
// ═══════════════════════════════════════════

// Mock functions
const mockFn = jest.fn();
mockFn.mockReturnValue(42);
mockFn.mockReturnValueOnce(1).mockReturnValueOnce(2);
mockFn.mockResolvedValue('async value');
mockFn.mockRejectedValue(new Error('async error'));

expect(mockFn()).toBe(42);
expect(mockFn).toHaveBeenCalled();
expect(mockFn).toHaveBeenCalledTimes(1);
expect(mockFn).toHaveBeenCalledWith(arg1, arg2);

// Mock modules
jest.mock('./api');
import { fetchUser } from './api';

fetchUser.mockResolvedValue({ id: 1, name: 'MrDib' });

// Spy on methods
const user = {
  getName: () => 'MrDib',
};

const spy = jest.spyOn(user, 'getName');
user.getName();
expect(spy).toHaveBeenCalled();
spy.mockRestore();

// Mock timers
jest.useFakeTimers();

setTimeout(() => {
  console.log('delayed');
}, 1000);

jest.advanceTimersByTime(1000);
jest.runAllTimers();
jest.useRealTimers();

// ═══════════════════════════════════════════
// Async Testing
// ═══════════════════════════════════════════

// Callback
test('callback', (done) => {
  function callback(data) {
    expect(data).toBe('success');
    done();
  }

  fetchData(callback);
});

// Promises
test('promise', () => {
  return fetchData().then(data => {
    expect(data).toBe('success');
  });
});

// Async/Await
test('async/await', async () => {
  const data = await fetchData();
  expect(data).toBe('success');
});

// Resolves/Rejects
test('resolves', async () => {
  await expect(fetchData()).resolves.toBe('success');
});

test('rejects', async () => {
  await expect(fetchError()).rejects.toThrow('error');
});
```

**📦 Jest Resources:**

- Docs: https://jestjs.io/docs/getting-started
- Cheat Sheet: https://github.com/sapegin/jest-cheat-sheet

> **💡 Pro Tip:** Jest is zero-config for most projects. Use `--watch` mode during development for instant feedback!

---

<div align="center">

## 🧬 Testing Utilities

</div>

### React Testing Library 🎨

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install -D @testing-library/react @testing-library/jest-dom
npm install -D @testing-library/user-event
```

```javascript
// ═══════════════════════════════════════════
# Testing React Components
// ═══════════════════════════════════════════

import { render, screen, fireEvent, waitFor } from '@testing-library/react';
import userEvent from '@testing-library/user-event';
import '@testing-library/jest-dom';

// Component to test
function Button({ onClick, children }) {
  return (
    <button onClick={onClick} data-testid="button">
      {children}
    </button>
  );
}

// ═══════════════════════════════════════════
// Basic Component Testing
// ═══════════════════════════════════════════

describe('Button Component', () => {
  it('renders with text', () => {
    render(<Button>Click me</Button>);

    expect(screen.getByText('Click me')).toBeInTheDocument();
  });

  it('calls onClick when clicked', () => {
    const handleClick = jest.fn();
    render(<Button onClick={handleClick}>Click me</Button>);

    fireEvent.click(screen.getByTestId('button'));

    expect(handleClick).toHaveBeenCalledTimes(1);
  });

  it('handles user interactions', async () => {
    const user = userEvent.setup();
    const handleClick = jest.fn();

    render(<Button onClick={handleClick}>Click me</Button>);

    await user.click(screen.getByRole('button'));

    expect(handleClick).toHaveBeenCalled();
  });
});

// ═══════════════════════════════════════════
// Queries
// ═══════════════════════════════════════════

// By Role (preferred - accessibility friendly)
screen.getByRole('button', { name: 'Submit' });
screen.getByRole('textbox', { name: 'Email' });
screen.getByRole('heading', { level: 1 });

// By Label
screen.getByLabelText('Email');
screen.getByLabelText(/email/i); // Case insensitive

// By Placeholder
screen.getByPlaceholderText('Enter your email');

// By Text
screen.getByText('Hello World');
screen.getByText(/hello/i);

// By Display Value
screen.getByDisplayValue('John Doe');

// By Alt Text
screen.getByAltText('Profile picture');

// By Title
screen.getByTitle('Close');

// By Test ID (last resort)
screen.getByTestId('custom-element');

// Query variants
screen.getBy...()     // Throws if not found
screen.queryBy...()   // Returns null if not found
screen.findBy...()    // Async, waits for element
screen.getAllBy...()  // Returns array

// ═══════════════════════════════════════════
// Form Testing
// ═══════════════════════════════════════════

function LoginForm({ onSubmit }) {
  const [email, setEmail] = useState('');
  const [password, setPassword] = useState('');

  const handleSubmit = (e) => {
    e.preventDefault();
    onSubmit({ email, password });
  };

  return (
    <form onSubmit={handleSubmit}>
      <label htmlFor="email">Email</label>
      <input
        id="email"
        type="email"
        value={email}
        onChange={(e) => setEmail(e.target.value)}
      />

      <label htmlFor="password">Password</label>
      <input
        id="password"
        type="password"
        value={password}
        onChange={(e) => setPassword(e.target.value)}
      />

      <button type="submit">Login</button>
    </form>
  );
}

describe('LoginForm', () => {
  it('submits form with user input', async () => {
    const user = userEvent.setup();
    const handleSubmit = jest.fn();

    render(<LoginForm onSubmit={handleSubmit} />);

    // Fill form
    await user.type(screen.getByLabelText('Email'), 'test@example.com');
    await user.type(screen.getByLabelText('Password'), 'password123');

    // Submit
    await user.click(screen.getByRole('button', { name: 'Login' }));

    // Assert
    expect(handleSubmit).toHaveBeenCalledWith({
      email: 'test@example.com',
      password: 'password123',
    });
  });

  it('shows validation errors', async () => {
    const user = userEvent.setup();

    render(<LoginForm onSubmit={jest.fn()} />);

    await user.click(screen.getByRole('button', { name: 'Login' }));

    expect(await screen.findByText('Email is required')).toBeInTheDocument();
  });
});

// ═══════════════════════════════════════════
// Async Testing
// ═══════════════════════════════════════════

function UserProfile({ userId }) {
  const [user, setUser] = useState(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    fetchUser(userId).then(data => {
      setUser(data);
      setLoading(false);
    });
  }, [userId]);

  if (loading) return <div>Loading...</div>;

  return <div>{user.name}</div>;
}

describe('UserProfile', () => {
  it('loads and displays user', async () => {
    // Mock API
    global.fetch = jest.fn(() =>
      Promise.resolve({
        json: () => Promise.resolve({ name: 'MrDib' }),
      })
    );

    render(<UserProfile userId="123" />);

    // Wait for loading to finish
    await waitFor(() => {
      expect(screen.queryByText('Loading...')).not.toBeInTheDocument();
    });

    expect(screen.getByText('MrDib')).toBeInTheDocument();
  });
});

// ═══════════════════════════════════════════
// Custom Hooks Testing
// ═══════════════════════════════════════════

import { renderHook, act } from '@testing-library/react';

function useCounter(initialValue = 0) {
  const [count, setCount] = useState(initialValue);

  const increment = () => setCount(c => c + 1);
  const decrement = () => setCount(c => c - 1);
  const reset = () => setCount(initialValue);

  return { count, increment, decrement, reset };
}

describe('useCounter', () => {
  it('increments count', () => {
    const { result } = renderHook(() => useCounter());

    act(() => {
      result.current.increment();
    });

    expect(result.current.count).toBe(1);
  });

  it('resets to initial value', () => {
    const { result } = renderHook(() => useCounter(10));

    act(() => {
      result.current.increment();
      result.current.reset();
    });

    expect(result.current.count).toBe(10);
  });
});
```

**📦 Testing Library Resources:**

- Docs: https://testing-library.com/docs/react-testing-library/intro
- Query Cheat Sheet: https://testing-library.com/docs/queries/about

> **💡 Pro Tip:** Query by role and label for accessibility-friendly tests. Avoid `getByTestId` unless absolutely necessary!

<div align="center">

## 🎭 Integration Testing

</div>

### Testing Component Integration 🔗

````javascript
// ═══════════════════════════════════════════
// Integration Test Example
// ═══════════════════════════════════════════

import { render, screen, waitFor } from "@testing-library/react";
import userEvent from "@testing-library/user-event";
import { rest } from "msw";
import { setupServer } from "msw/node";
import App from "./App";

// ═══════════════════════════════════════════
// Mock Service Worker (MSW) Setup
// ═══════════════════════════════════════════

const server = setupServer(
  rest.get("/api/users", (req, res, ctx) => {
    return res(
      ctx.json({
        users: [
          { id: 1, name: "Alice" },
          { id: 2, name: "Bob" },
        ],
      })
    );
  }),

  rest.post("/api/users", (req, res, ctx) => {
    const { name, email } = req.body;
    return res(
      ctx.status(201),
      ctx.json({
        id: 3,
        name,
        email,
      })
    );
  })
);

beforeAll(() => server.listen());
afterEach(() => server.resetHandlers());
afterAll(() => server.close());

// ═══════════════════════════════════════════
// Integration Tests
// ═══════════════════════════════════════════

describe("User Management Integration", () => {
  it("loads and displays users", async () => {
    render(<App />);

    // Wait for users to load
    await waitFor(() => {
      expect(screen.getByText("Alice")).toBeInTheDocument();
      expect(screen.getByText("Bob")).toBeInTheDocument();
    });
  });

  it("creates new user", async () => {
    const user = userEvent.setup();
    render(<App />);

    // Open create form
    await user.click(screen.getByRole("button", { name: "Add User" }));

    // Fill form
    await user.type(screen.getByLabelText("Name"), "Charlie");
    await user.type(screen.getByLabelText("Email"), "charlie@example.com");

    // Submit
    await user.click(screen.getByRole("button", { name: "Create" }));

    // Verify new user appears
    await waitFor(() => {
      expect(screen.getByText("Charlie")).toBeInTheDocument();
    });
  });

  it("handles API errors gracefully", async () => {
    // Mock error response
    server.use(
      rest.get("/api/users", (req, res, ctx) => {
        return res(ctx.status(500), ctx.json({ error: "Server error" }));
      })
    );

    render(<App />);

    await waitFor(() => {
      expect(screen.getByText(/failed to load users/i)).toBeInTheDocument();
    });
  });
});

// ═══════════════════════════════════════════
// Testing with Context
// ═══════════════════════════════════════════

import { AuthProvider } from "./contexts/AuthContext";

function renderWithAuth(ui, { user = null, ...options } = {}) {
  return render(<AuthProvider initialUser={user}>{ui}</AuthProvider>, options);
}

describe("Protected Component", () => {
  it("shows content for authenticated users", () => {
    const user = { id: 1, name: "MrDib" };

    renderWithAuth(<Dashboard />, { user });

    expect(screen.getByText("Welcome, MrDib")).toBeInTheDocument();
  });

  it("redirects unauthenticated users", () => {
    renderWithAuth(<Dashboard />);

    expect(screen.getByText("Please log in")).toBeInTheDocument();
  });
});

// ═══════════════════════════════════════════
// Testing with Router
// ═══════════════════════════════════════════

import { BrowserRouter } from "react-router-dom";
import { createMemoryHistory } from "history";

function renderWithRouter(
  ui,
  {
    route = "/",
    history = createMemoryHistory({ initialEntries: [route] }),
  } = {}
) {
  return {
    ...render(<BrowserRouter>{ui}</BrowserRouter>),
    history,
  };
}

describe("Navigation", () => {
  it("navigates to user profile", async () => {
    const user = userEvent.setup();
    renderWithRouter(<App />, { route: "/users" });

    await user.click(screen.getByText("Alice"));

    expect(screen.getByRole("heading", { name: "Alice" })).toBeInTheDocument();
  });
});

// ═══════════════════════════════════════════
// Custom Render Function
// ═══════════════════════════════════════════

function renderWithProviders(
  ui,
  { initialState = {}, user = null, route = "/", ...options } = {}
) {
  const history = createMemoryHistory({ initialEntries: [route] });

  function Wrapper({ children }) {
    return (
      <BrowserRouter>
        <AuthProvider initialUser={user}>
          <ThemeProvider>
            <QueryClientProvider client={queryClient}>
              {children}
            </QueryClientProvider>
          </ThemeProvider>
        </AuthProvider>
      </BrowserRouter>
    );
  }

  return {
    ...render(ui, { wrapper: Wrapper, ...options }),
    history,
  };
}

// Usage
describe("Full App Integration", () => {
  it("complete user flow", async () => {
    const user = userEvent.setup();

    renderWithProviders(<App />, {
      route: "/",
      user: { id: 1, name: "MrDib" },
    });

    // Test complex interactions
  });
});


---

<div align="center">

## 🌐 API Testing

</div>

### Testing Backend APIs 🚀

```javascript
// ═══════════════════════════════════════════
// Supertest for Express APIs
// ═══════════════════════════════════════════

import request from "supertest";
import app from "../app";
import { setupTestDB, teardownTestDB } from "./helpers/db";

describe("API Integration Tests", () => {
  beforeAll(async () => {
    await setupTestDB();
  });

  afterAll(async () => {
    await teardownTestDB();
  });

  describe("GET /api/users", () => {
    it("returns list of users", async () => {
      const response = await request(app)
        .get("/api/users")
        .expect("Content-Type", /json/)
        .expect(200);

      expect(response.body).toHaveProperty("users");
      expect(Array.isArray(response.body.users)).toBe(true);
    });

    it("filters users by query", async () => {
      const response = await request(app)
        .get("/api/users?role=admin")
        .expect(200);

      expect(response.body.users.every((u) => u.role === "admin")).toBe(true);
    });
  });

  describe("POST /api/users", () => {
    it("creates new user", async () => {
      const newUser = {
        name: "MrDib",
        email: "mrdib@example.com",
      };

      const response = await request(app)
        .post("/api/users")
        .send(newUser)
        .expect("Content-Type", /json/)
        .expect(201);

      expect(response.body).toMatchObject(newUser);
      expect(response.body).toHaveProperty("id");
    });

    it("validates required fields", async () => {
      const response = await request(app)
        .post("/api/users")
        .send({ name: "Test" })
        .expect(400);

      expect(response.body.error).toContain("email");
    });
  });

  describe("PUT /api/users/:id", () => {
    it("updates user", async () => {
      const updates = { name: "Updated Name" };

      const response = await request(app)
        .put("/api/users/1")
        .send(updates)
        .set("Authorization", "Bearer valid-token")
        .expect(200);

      expect(response.body.name).toBe("Updated Name");
    });

    it("requires authentication", async () => {
      await request(app).put("/api/users/1").send({ name: "Test" }).expect(401);
    });
  });

  describe("DELETE /api/users/:id", () => {
    it("deletes user", async () => {
      await request(app)
        .delete("/api/users/1")
        .set("Authorization", "Bearer valid-token")
        .expect(204);

      // Verify deletion
      await request(app).get("/api/users/1").expect(404);
    });
  });
});

// ═══════════════════════════════════════════
// Contract Testing with Pact
// ═══════════════════════════════════════════

import { Pact } from "@pact-foundation/pact";
import path from "path";

const provider = new Pact({
  consumer: "FrontendApp",
  provider: "UserAPI",
  port: 1234,
  log: path.resolve(process.cwd(), "logs", "pact.log"),
  dir: path.resolve(process.cwd(), "pacts"),
  logLevel: "warn",
});

describe("User API Contract", () => {
  beforeAll(() => provider.setup());
  afterEach(() => provider.verify());
  afterAll(() => provider.finalize());

  describe("GET /users/:id", () => {
    it("returns user when exists", async () => {
      await provider.addInteraction({
        state: "user with ID 1 exists",
        uponReceiving: "a request for user 1",
        withRequest: {
          method: "GET",
          path: "/users/1",
          headers: {
            Accept: "application/json",
          },
        },
        willRespondWith: {
          status: 200,
          headers: {
            "Content-Type": "application/json",
          },
          body: {
            id: 1,
            name: "MrDib",
            email: "mrdib@example.com",
          },
        },
      });

      const response = await fetch("http://localhost:1234/users/1");
      const user = await response.json();

      expect(user).toMatchObject({
        id: 1,
        name: "MrDib",
      });
    });
  });
});

// ═══════════════════════════════════════════
// GraphQL Testing
// ═══════════════════════════════════════════

import { ApolloServer } from "@apollo/server";
import { createTestClient } from "apollo-server-testing";

const server = new ApolloServer({
  typeDefs,
  resolvers,
  context: () => ({ user: mockUser }),
});

const { query, mutate } = createTestClient(server);

describe("GraphQL API", () => {
  it("queries user", async () => {
    const GET_USER = gql`
      query GetUser($id: ID!) {
        user(id: $id) {
          id
          name
          email
        }
      }
    `;

    const result = await query({
      query: GET_USER,
      variables: { id: "1" },
    });

    expect(result.data.user).toMatchObject({
      id: "1",
      name: "MrDib",
    });
  });

  it("creates user", async () => {
    const CREATE_USER = gql`
      mutation CreateUser($input: UserInput!) {
        createUser(input: $input) {
          id
          name
        }
      }
    `;

    const result = await mutate({
      mutation: CREATE_USER,
      variables: {
        input: {
          name: "New User",
          email: "new@example.com",
        },
      },
    });

    expect(result.data.createUser).toHaveProperty("id");
  });
});
````

---

<div align="center">

## 📸 Visual Testing

</div>

### Visual Regression Testing 👁️

```javascript
// ═══════════════════════════════════════════
// Playwright Visual Testing
// ═══════════════════════════════════════════

import { test, expect } from '@playwright/test';

test('visual regression - homepage', async ({ page }) => {
  await page.goto('http://localhost:3000');

  // Full page screenshot
  await expect(page).toHaveScreenshot('homepage.png', {
    fullPage: true,
  });
});

test('visual regression - component', async ({ page }) => {
  await page.goto('http://localhost:3000');

  // Specific element
  const header = page.locator('header');
  await expect(header).toHaveScreenshot('header.png');
});

test('visual regression - responsive', async ({ page }) => {
  // Mobile
  await page.setViewportSize({ width: 375, height: 667 });
  await page.goto('http://localhost:3000');
  await expect(page).toHaveScreenshot('homepage-mobile.png');

  // Desktop
  await page.setViewportSize({ width: 1920, height: 1080 });
  await expect(page).toHaveScreenshot('homepage-desktop.png');
});

// ═══════════════════════════════════════════
# Percy Configuration (.percy.yml)
// ═══════════════════════════════════════════

/*
version: 2
snapshot:
  widths:
    - 375
    - 768
    - 1280
  min-height: 1024
  percy-css: |
    .dynamic-content {
      display: none !important;
    }
*/

// ═══════════════════════════════════════════
// Percy with Cypress
// ═══════════════════════════════════════════

import '@percy/cypress';

describe('Visual Tests', () => {
  it('homepage looks correct', () => {
    cy.visit('/');
    cy.percySnapshot('Homepage');
  });

  it('dark mode looks correct', () => {
    cy.visit('/');
    cy.get('[data-testid="theme-toggle"]').click();
    cy.percySnapshot('Homepage - Dark Mode');
  });

  it('responsive layouts', () => {
    cy.visit('/');

    // Mobile
    cy.viewport(375, 667);
    cy.percySnapshot('Homepage - Mobile');

    // Tablet
    cy.viewport(768, 1024);
    cy.percySnapshot('Homepage - Tablet');

    // Desktop
    cy.viewport(1920, 1080);
    cy.percySnapshot('Homepage - Desktop');
  });
});

// ═══════════════════════════════════════════
// Storybook Visual Testing
// ═══════════════════════════════════════════

// Button.stories.jsx
export default {
  title: 'Components/Button',
  component: Button,
  parameters: {
    percy: {
      skip: false,
    },
  },
};

export const Primary = () => <Button variant="primary">Click me</Button>;
export const Secondary = () => <Button variant="secondary">Click me</Button>;
export const Disabled = () => <Button disabled>Click me</Button>;

// Run visual tests
// npx percy storybook http://localhost:6006
```

---

<div align="center">

## 🎯 Test Organization

</div>

### Structuring Your Tests 📁

```bash
# ═══════════════════════════════════════════
# Recommended Test Structure
# ═══════════════════════════════════════════

src/
├── components/
│   ├── Button/
│   │   ├── Button.tsx
│   │   ├── Button.test.tsx          # Component tests
│   │   └── Button.stories.tsx       # Storybook stories
│   └── Form/
│       ├── Form.tsx
│       └── Form.test.tsx
│
├── hooks/
│   ├── useAuth.ts
│   └── useAuth.test.ts              # Hook tests
│
├── utils/
│   ├── helpers.ts
│   └── helpers.test.ts              # Utility tests
│
├── services/
│   ├── api.ts
│   └── api.test.ts                  # API tests
│
└── __tests__/
    ├── integration/
    │   ├── auth.test.tsx            # Integration tests
    │   └── checkout.test.tsx
    │
    ├── e2e/
    │   ├── user-flow.spec.ts        # E2E tests
    │   └── admin-flow.spec.ts
    │
    ├── fixtures/
    │   ├── users.json               # Test data
    │   └── products.json
    │
    ├── mocks/
    │   ├── handlers.ts              # MSW handlers
    │   └── server.ts                # MSW server
    │
    └── setup/
        ├── jest.setup.ts            # Jest setup
        └── test-utils.tsx           # Test helpers
```

```javascript
// ═══════════════════════════════════════════
// Test Utilities (test-utils.tsx)
// ═══════════════════════════════════════════

import { render, RenderOptions } from '@testing-library/react';
import { QueryClient, QueryClientProvider } from '@tanstack/react-query';
import { BrowserRouter } from 'react-router-dom';
import { AuthProvider } from '../contexts/AuthContext';
import { ThemeProvider } from '../contexts/ThemeContext';

// Create custom render
function AllTheProviders({ children }) {
  const queryClient = new QueryClient({
    defaultOptions: {
      queries: { retry: false },
    },
  });

  return (
    <BrowserRouter>
      <QueryClientProvider client={queryClient}>
        <AuthProvider>
          <ThemeProvider>
            {children}
          </ThemeProvider>
        </AuthProvider>
      </QueryClientProvider>
    </BrowserRouter>
  );
}

const customRender = (
  ui: React.ReactElement,
  options?: Omit<RenderOptions, 'wrapper'>
) => render(ui, { wrapper: AllTheProviders, ...options });

// Re-export everything
export * from '@testing-library/react';
export { customRender as render };

// ═══════════════════════════════════════════
// Test Fixtures
// ═══════════════════════════════════════════

// fixtures/users.ts
export const mockUser = {
  id: 1,
  name: 'Test User',
  email: 'test@example.com',
  role: 'user',
};

export const mockAdmin = {
  id: 2,
  name: 'Admin User',
  email: 'admin@example.com',
  role: 'admin',
};

export function createMockUser(overrides = {}) {
  return {
    ...mockUser,
    ...overrides,
  };
}

// ═══════════════════════════════════════════
// Mock Handlers (mocks/handlers.ts)
// ═══════════════════════════════════════════

import { rest } from 'msw';

export const handlers = [
  rest.get('/api/users', (req, res, ctx) => {
    return res(
      ctx.status(200),
      ctx.json({
        users: [
          { id: 1, name: 'Alice' },
          { id: 2, name: 'Bob' },
        ],
      })
    );
  }),

  rest.post('/api/auth/login', (req, res, ctx) => {
    const { email, password } = req.body as any;

    if (email === 'test@example.com' && password === 'password123') {
      return res(
        ctx.status(200),
        ctx.json({
          token: 'mock-token',
          user: mockUser,
        })
      );
    }

    return res(
      ctx.status(401),
      ctx.json({ error: 'Invalid credentials' })
    );
  }),
];

// ═══════════════════════════════════════════
// Mock Server (mocks/server.ts)
// ═══════════════════════════════════════════

import { setupServer } from 'msw/node';
import { handlers } from './handlers';

export const server = setupServer(...handlers);

// jest.setup.ts
beforeAll(() => server.listen());
afterEach(() => server.resetHandlers());
afterAll(() => server.close());
```

---

<div align="center">

## 💡 Best Practices

</div>

### Testing Guidelines ⭐

```javascript
// ═══════════════════════════════════════════
// 1. Test Behavior, Not Implementation
// ═══════════════════════════════════════════

// ❌ BAD: Testing implementation details
test("state updates correctly", () => {
  const { result } = renderHook(() => useState(0));
  // Testing internal state
});

// ✅ GOOD: Testing user-facing behavior
test("counter increments when button clicked", async () => {
  const user = userEvent.setup();
  render(<Counter />);

  await user.click(screen.getByRole("button", { name: "Increment" }));

  expect(screen.getByText("Count: 1")).toBeInTheDocument();
});

// ═══════════════════════════════════════════
// 2. Use Descriptive Test Names
// ═══════════════════════════════════════════

// ❌ BAD
test("test1", () => {});

// ✅ GOOD
describe("LoginForm", () => {
  describe("when user submits valid credentials", () => {
    it("should redirect to dashboard", () => {});
    it("should display welcome message", () => {});
    it("should store auth token", () => {});
  });

  describe("when user submits invalid credentials", () => {
    it("should display error message", () => {});
    it("should not redirect", () => {});
  });
});

// ═══════════════════════════════════════════
// 3. AAA Pattern (Arrange, Act, Assert)
// ═══════════════════════════════════════════

test("user can update profile", async () => {
  // Arrange
  const user = userEvent.setup();
  const mockUpdate = jest.fn();
  render(<ProfileForm onUpdate={mockUpdate} />);

  // Act
  await user.type(screen.getByLabelText("Name"), "New Name");
  await user.click(screen.getByRole("button", { name: "Save" }));

  // Assert
  expect(mockUpdate).toHaveBeenCalledWith({ name: "New Name" });
});

// ═══════════════════════════════════════════
// 4. Test Edge Cases
// ═══════════════════════════════════════════

describe("divide function", () => {
  it("divides two positive numbers", () => {
    expect(divide(10, 2)).toBe(5);
  });

  it("handles negative numbers", () => {
    expect(divide(-10, 2)).toBe(-5);
  });

  it("handles division by zero", () => {
    expect(() => divide(10, 0)).toThrow("Division by zero");
  });

  it("handles decimal results", () => {
    expect(divide(5, 2)).toBe(2.5);
  });

  it("handles very large numbers", () => {
    expect(divide(Number.MAX_SAFE_INTEGER, 2)).toBeCloseTo(
      Number.MAX_SAFE_INTEGER / 2
    );
  });
});

// ═══════════════════════════════════════════
// 5. DRY Tests with Helper Functions
// ═══════════════════════════════════════════

function setupLoginTest() {
  const user = userEvent.setup();
  const mockLogin = jest.fn();

  render(<LoginForm onLogin={mockLogin} />);

  const emailInput = screen.getByLabelText("Email");
  const passwordInput = screen.getByLabelText("Password");
  const submitButton = screen.getByRole("button", { name: "Login" });

  return {
    user,
    mockLogin,
    emailInput,
    passwordInput,
    submitButton,
  };
}

describe("LoginForm", () => {
  it("submits with valid credentials", async () => {
    const { user, mockLogin, emailInput, passwordInput, submitButton } =
      setupLoginTest();

    await user.type(emailInput, "test@example.com");
    await user.type(passwordInput, "password123");
    await user.click(submitButton);

    expect(mockLogin).toHaveBeenCalled();
  });
});

// ═══════════════════════════════════════════
// 6. Coverage Goals
// ═══════════════════════════════════════════

const coverageTargets = {
  unit: {
    statements: 80,
    branches: 75,
    functions: 80,
    lines: 80,
  },

  integration: {
    criticalPaths: 100,
    apiEndpoints: 100,
    errorScenarios: 90,
  },

  e2e: {
    happyPaths: 100,
    criticalFlows: 100,
    crossBrowser: ["Chrome", "Firefox", "Safari"],
  },
};

// ═══════════════════════════════════════════
// 7. Keep Tests Fast
// ═══════════════════════════════════════════

// ✅ GOOD: Fast, isolated tests
test("validates email", () => {
  expect(isValidEmail("test@example.com")).toBe(true);
});

// ❌ BAD: Slow, coupled tests
test("full user flow", async () => {
  // Creates real database connections
  // Makes actual HTTP requests
  // Takes 30 seconds to run
});
```

---

<div align="center">

**Built with 🧪 by MrDib, for Test-Driven Developers**

_"Untested code is broken code you just don't know about yet!"_

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

- Jest: https://jestjs.io/docs/getting-started
- Testing Library: https://testing-library.com/
- Playwright: https://playwright.dev/
- Cypress: https://docs.cypress.io/

**🎥 Learning Resources:**

- Kent C. Dodds Testing Course
- Testing JavaScript Masterclass
- Test Automation University

**🛠️ Tools:**

- Jest VS Code Extension
- Testing Playground: https://testing-playground.com/
- Testing Library Playground

---

### License 📄

This guide is open source and available under the MIT License.

---

<div align="center">

**Stay tested. Keep shipping. Build with confidence!** 💪✨

🧪 **#Testing** 🧪 **#DevResourceVault** 🧪 **#MrDib** 🧪

### Remember

> _"Test early, test often"_

> _"A failing test is better than no test"_

> _"Tests are documentation that never lies"_

> _"If it's hard to test, it's hard to use"_

> _"Coverage is a metric, not a goal"_

</div>

---

<div align="center">

**Now go forth and test everything!** 🌟🧪

</div>
