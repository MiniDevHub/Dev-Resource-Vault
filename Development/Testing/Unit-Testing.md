<div align="center">

# 🧪 Unit Testing

### _Write tests that give you confidence_ 🎯

![Testing](https://img.shields.io/badge/Testing-Unit-green?style=for-the-badge)
![Jest](https://img.shields.io/badge/Jest-Latest-red?style=for-the-badge&logo=jest)
![Coverage](https://img.shields.io/badge/Coverage-80%25+-brightgreen?style=for-the-badge)

</div>

---

## 📚 Table of Contents

- [🎯 Unit Testing Fundamentals](#-unit-testing-fundamentals)
- [🃏 Jest Framework](#-jest-framework)
- [⚛️ React Testing](#-react-testing)
- [🟢 Node.js Testing](#-nodejs-testing)
- [🔷 TypeScript Testing](#-typescript-testing)
- [🎭 Mocking Strategies](#-mocking-strategies)
- [📊 Code Coverage](#-code-coverage)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 🎯 Unit Testing Fundamentals

</div>

### Understanding Unit Testing 📖

```javascript
// ═══════════════════════════════════════════
// What is Unit Testing?
// ═══════════════════════════════════════════

/*
Unit testing validates individual units of code:
- Single functions
- Single components
- Single modules
- In complete isolation

Unit vs Integration vs E2E:

Unit Testing:
  ✅ Very fast (milliseconds)
  ✅ Easy to debug
  ✅ High coverage
  ❌ Doesn't test integration

Integration Testing:
  ✅ Tests interaction
  ✅ Higher confidence
  ❌ Slower
  ❌ Harder to debug

E2E Testing:
  ✅ Tests complete flows
  ✅ Highest confidence
  ❌ Very slow
  ❌ Brittle
*/

// ═══════════════════════════════════════════
// FIRST Principles of Unit Testing
// ═══════════════════════════════════════════

const FIRSTprinciples = {
  Fast: {
    description: "Tests run in milliseconds",
    why: "Developers run them frequently",
    how: "Mock external dependencies, use in-memory databases",
  },

  Isolated: {
    description: "Tests are independent",
    why: "No cascading failures, run in parallel",
    how: "No shared state, clean up after each test",
  },

  Repeatable: {
    description: "Same result every time",
    why: "Reliable CI/CD, trust the results",
    how: "No random data, mock time/network",
  },

  SelfValidating: {
    description: "Pass/fail without manual check",
    why: "Automated validation",
    how: "Use assertions, clear expectations",
  },

  Timely: {
    description: "Written with or before code (TDD)",
    why: "Better design, complete coverage",
    how: "Write test first, then implementation",
  },
};

// ═══════════════════════════════════════════
// Test Structure - AAA Pattern
// ═══════════════════════════════════════════

test("calculates order total with discount", () => {
  // Arrange - Set up test data
  const items = [
    { name: "Item 1", price: 100, quantity: 2 },
    { name: "Item 2", price: 50, quantity: 1 },
  ];
  const discount = 0.1; // 10% discount

  // Act - Execute the function
  const total = calculateOrderTotal(items, discount);

  // Assert - Verify the result
  expect(total).toBe(225); // (200 + 50) * 0.9
});
```

---

<div align="center">

## 🃏 Jest Framework

</div>

### Complete Jest Guide 🚀

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install -D jest
npm install -D @types/jest

# For TypeScript
npm install -D ts-jest @types/jest

# For React
npm install -D @testing-library/react @testing-library/jest-dom

# Initialize configuration
npx jest --init
```

```javascript
// ═══════════════════════════════════════════
// Jest Configuration (jest.config.js)
// ═══════════════════════════════════════════

module.exports = {
  // Test environment
  testEnvironment: "jsdom", // or 'node'

  // Setup files
  setupFilesAfterEnv: ["<rootDir>/jest.setup.js"],

  // Module paths
  moduleNameMapper: {
    "^@/(.*)$": "<rootDir>/src/$1",
    "\\.(css|less|scss)$": "identity-obj-proxy",
    "\\.(jpg|jpeg|png|gif|svg)$": "<rootDir>/__mocks__/fileMock.js",
  },

  // Transform
  transform: {
    "^.+\\.(ts|tsx)$": "ts-jest",
    "^.+\\.(js|jsx)$": "babel-jest",
  },

  // Coverage
  collectCoverageFrom: [
    "src/**/*.{js,jsx,ts,tsx}",
    "!src/**/*.d.ts",
    "!src/**/*.stories.{js,jsx,ts,tsx}",
  ],

  coverageThresholds: {
    global: {
      branches: 80,
      functions: 80,
      lines: 80,
      statements: 80,
    },
  },

  // Ignore patterns
  testPathIgnorePatterns: ["/node_modules/", "/build/", "/dist/"],

  // Test match patterns
  testMatch: ["**/__tests__/**/*.[jt]s?(x)", "**/?(*.)+(spec|test).[jt]s?(x)"],
};

// ═══════════════════════════════════════════
// Setup File (jest.setup.js)
// ═══════════════════════════════════════════

// Extend matchers
import "@testing-library/jest-dom";

// Mock environment variables
process.env.API_URL = "http://localhost:3000";

// Mock window.matchMedia
Object.defineProperty(window, "matchMedia", {
  writable: true,
  value: jest.fn().mockImplementation((query) => ({
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

// Global test utilities
global.flushPromises = () => new Promise((resolve) => setImmediate(resolve));

// ═══════════════════════════════════════════
// Basic Jest Tests
// ═══════════════════════════════════════════

// Simple function
function add(a, b) {
  return a + b;
}

describe("add function", () => {
  it("adds two positive numbers", () => {
    expect(add(2, 3)).toBe(5);
  });

  it("adds negative numbers", () => {
    expect(add(-1, -2)).toBe(-3);
  });

  it("handles zero", () => {
    expect(add(0, 5)).toBe(5);
  });
});

// ═══════════════════════════════════════════
// Jest Matchers
// ═══════════════════════════════════════════

describe("Jest Matchers", () => {
  // Equality
  test("equality matchers", () => {
    expect(2 + 2).toBe(4);
    expect({ name: "MrDib" }).toEqual({ name: "MrDib" });
    expect([1, 2, 3]).toStrictEqual([1, 2, 3]);
  });

  // Truthiness
  test("truthiness matchers", () => {
    expect(true).toBeTruthy();
    expect(false).toBeFalsy();
    expect(null).toBeNull();
    expect(undefined).toBeUndefined();
    expect("value").toBeDefined();
  });

  // Numbers
  test("number matchers", () => {
    expect(5).toBeGreaterThan(3);
    expect(5).toBeGreaterThanOrEqual(5);
    expect(5).toBeLessThan(10);
    expect(5).toBeLessThanOrEqual(5);
    expect(0.1 + 0.2).toBeCloseTo(0.3, 5);
  });

  // Strings
  test("string matchers", () => {
    expect("MrDib").toMatch(/Dib/);
    expect("testing").toContain("test");
    expect("hello").toHaveLength(5);
  });

  // Arrays & Iterables
  test("array matchers", () => {
    const arr = [1, 2, 3];
    expect(arr).toContain(2);
    expect(arr).toHaveLength(3);
    expect(arr).toEqual(expect.arrayContaining([1, 2]));
  });

  // Objects
  test("object matchers", () => {
    const obj = { a: 1, b: 2, c: 3 };
    expect(obj).toHaveProperty("a");
    expect(obj).toHaveProperty("a", 1);
    expect(obj).toMatchObject({ a: 1, b: 2 });
    expect(obj).toEqual(expect.objectContaining({ a: 1 }));
  });

  // Exceptions
  test("exception matchers", () => {
    function throwError() {
      throw new Error("Oops!");
    }

    expect(throwError).toThrow();
    expect(throwError).toThrow("Oops!");
    expect(throwError).toThrow(/Oops/);
    expect(throwError).toThrow(Error);
  });

  // Promises
  test("promise matchers", async () => {
    await expect(Promise.resolve("success")).resolves.toBe("success");
    await expect(Promise.reject("error")).rejects.toBe("error");
  });

  // Custom matchers
  expect.extend({
    toBeWithinRange(received, floor, ceiling) {
      const pass = received >= floor && received <= ceiling;
      return {
        pass,
        message: () =>
          `expected ${received} to be within range ${floor} - ${ceiling}`,
      };
    },
  });

  expect(10).toBeWithinRange(5, 15);
});

// ═══════════════════════════════════════════
// Async Testing
// ═══════════════════════════════════════════

// Callbacks
test("callback", (done) => {
  function fetchData(callback) {
    setTimeout(() => callback("data"), 100);
  }

  fetchData((data) => {
    expect(data).toBe("data");
    done();
  });
});

// Promises
test("promise", () => {
  return fetchData().then((data) => {
    expect(data).toBe("success");
  });
});

// Async/Await
test("async/await", async () => {
  const data = await fetchData();
  expect(data).toBe("success");
});

// Resolves/Rejects
test("resolves", async () => {
  await expect(fetchData()).resolves.toBe("success");
});

test("rejects", async () => {
  await expect(fetchError()).rejects.toThrow("error");
});

// ═══════════════════════════════════════════
// Test Lifecycle Hooks
// ═══════════════════════════════════════════

describe("Lifecycle Hooks", () => {
  beforeAll(() => {
    // Runs once before all tests
    console.log("Setup before all tests");
  });

  afterAll(() => {
    // Runs once after all tests
    console.log("Cleanup after all tests");
  });

  beforeEach(() => {
    // Runs before each test
    console.log("Setup before each test");
  });

  afterEach(() => {
    // Runs after each test
    console.log("Cleanup after each test");
  });

  test("test 1", () => {});
  test("test 2", () => {});
});

// ═══════════════════════════════════════════
// Test Organization
// ═══════════════════════════════════════════

describe("Calculator", () => {
  describe("add", () => {
    it("adds positive numbers", () => {});
    it("adds negative numbers", () => {});
  });

  describe("subtract", () => {
    it("subtracts positive numbers", () => {});
    it("subtracts negative numbers", () => {});
  });
});

// Test only/skip
test.only("runs only this test", () => {});
test.skip("skips this test", () => {});

describe.only("only this suite", () => {});
describe.skip("skip this suite", () => {});

// Conditional tests
const testIf = (condition) => (condition ? test : test.skip);

testIf(process.platform === "darwin")("macOS only", () => {});
```

**📦 Jest Resources:**

- Docs: https://jestjs.io/docs/getting-started
- API: https://jestjs.io/docs/api
- Cheat Sheet: https://github.com/sapegin/jest-cheat-sheet

> **💡 Pro Tip:** Use `test.each` for data-driven tests to reduce repetition and improve readability!

<div align="center">

## ⚛️ React Testing

</div>

### Testing React Components 🎨

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install -D @testing-library/react
npm install -D @testing-library/jest-dom
npm install -D @testing-library/user-event
npm install -D @testing-library/react-hooks
```

```javascript
// ═══════════════════════════════════════════
// Basic Component Testing
// ═══════════════════════════════════════════

import { render, screen, waitFor } from "@testing-library/react";
import userEvent from "@testing-library/user-event";
import "@testing-library/jest-dom";

// Component
function Button({ onClick, disabled, children }) {
  return (
    <button onClick={onClick} disabled={disabled}>
      {children}
    </button>
  );
}

describe("Button Component", () => {
  it("renders with text", () => {
    render(<Button>Click me</Button>);

    expect(
      screen.getByRole("button", { name: "Click me" })
    ).toBeInTheDocument();
  });

  it("calls onClick when clicked", async () => {
    const user = userEvent.setup();
    const handleClick = jest.fn();

    render(<Button onClick={handleClick}>Click me</Button>);

    await user.click(screen.getByRole("button"));

    expect(handleClick).toHaveBeenCalledTimes(1);
  });

  it("is disabled when disabled prop is true", () => {
    render(<Button disabled>Click me</Button>);

    expect(screen.getByRole("button")).toBeDisabled();
  });
});

// ═══════════════════════════════════════════
// Form Testing
// ═══════════════════════════════════════════

function LoginForm({ onSubmit }) {
  const [email, setEmail] = useState("");
  const [password, setPassword] = useState("");
  const [errors, setErrors] = useState({});

  const handleSubmit = (e) => {
    e.preventDefault();

    const newErrors = {};
    if (!email) newErrors.email = "Email required";
    if (!password) newErrors.password = "Password required";

    if (Object.keys(newErrors).length > 0) {
      setErrors(newErrors);
      return;
    }

    onSubmit({ email, password });
  };

  return (
    <form onSubmit={handleSubmit}>
      <div>
        <label htmlFor="email">Email</label>
        <input
          id="email"
          type="email"
          value={email}
          onChange={(e) => setEmail(e.target.value)}
        />
        {errors.email && <span role="alert">{errors.email}</span>}
      </div>

      <div>
        <label htmlFor="password">Password</label>
        <input
          id="password"
          type="password"
          value={password}
          onChange={(e) => setPassword(e.target.value)}
        />
        {errors.password && <span role="alert">{errors.password}</span>}
      </div>

      <button type="submit">Login</button>
    </form>
  );
}

describe("LoginForm", () => {
  it("submits form with valid data", async () => {
    const user = userEvent.setup();
    const handleSubmit = jest.fn();

    render(<LoginForm onSubmit={handleSubmit} />);

    // Fill form
    await user.type(screen.getByLabelText("Email"), "test@example.com");
    await user.type(screen.getByLabelText("Password"), "password123");

    // Submit
    await user.click(screen.getByRole("button", { name: "Login" }));

    // Assert
    expect(handleSubmit).toHaveBeenCalledWith({
      email: "test@example.com",
      password: "password123",
    });
  });

  it("shows validation errors", async () => {
    const user = userEvent.setup();
    const handleSubmit = jest.fn();

    render(<LoginForm onSubmit={handleSubmit} />);

    // Submit without filling
    await user.click(screen.getByRole("button", { name: "Login" }));

    // Assert errors
    expect(screen.getByText("Email required")).toBeInTheDocument();
    expect(screen.getByText("Password required")).toBeInTheDocument();
    expect(handleSubmit).not.toHaveBeenCalled();
  });
});

// ═══════════════════════════════════════════
// Testing with State & Effects
// ═══════════════════════════════════════════

function UserProfile({ userId }) {
  const [user, setUser] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    fetchUser(userId)
      .then((data) => {
        setUser(data);
        setLoading(false);
      })
      .catch((err) => {
        setError(err.message);
        setLoading(false);
      });
  }, [userId]);

  if (loading) return <div>Loading...</div>;
  if (error) return <div>Error: {error}</div>;
  if (!user) return <div>User not found</div>;

  return (
    <div>
      <h1>{user.name}</h1>
      <p>{user.email}</p>
    </div>
  );
}

describe("UserProfile", () => {
  it("loads and displays user", async () => {
    // Mock API
    global.fetch = jest.fn(() =>
      Promise.resolve({
        ok: true,
        json: () =>
          Promise.resolve({
            name: "MrDib",
            email: "mrdib@example.com",
          }),
      })
    );

    render(<UserProfile userId="123" />);

    // Check loading state
    expect(screen.getByText("Loading...")).toBeInTheDocument();

    // Wait for user to load
    await waitFor(() => {
      expect(screen.getByText("MrDib")).toBeInTheDocument();
    });

    expect(screen.getByText("mrdib@example.com")).toBeInTheDocument();
  });

  it("handles error", async () => {
    // Mock failed API
    global.fetch = jest.fn(() => Promise.reject(new Error("Network error")));

    render(<UserProfile userId="123" />);

    await waitFor(() => {
      expect(screen.getByText("Error: Network error")).toBeInTheDocument();
    });
  });
});

// ═══════════════════════════════════════════
// Custom Hooks Testing
// ═══════════════════════════════════════════

import { renderHook, act } from "@testing-library/react";

function useCounter(initialValue = 0) {
  const [count, setCount] = useState(initialValue);

  const increment = useCallback(() => setCount((c) => c + 1), []);
  const decrement = useCallback(() => setCount((c) => c - 1), []);
  const reset = useCallback(() => setCount(initialValue), [initialValue]);

  return { count, increment, decrement, reset };
}

describe("useCounter", () => {
  it("initializes with default value", () => {
    const { result } = renderHook(() => useCounter());

    expect(result.current.count).toBe(0);
  });

  it("initializes with custom value", () => {
    const { result } = renderHook(() => useCounter(10));

    expect(result.current.count).toBe(10);
  });

  it("increments count", () => {
    const { result } = renderHook(() => useCounter());

    act(() => {
      result.current.increment();
    });

    expect(result.current.count).toBe(1);
  });

  it("decrements count", () => {
    const { result } = renderHook(() => useCounter(5));

    act(() => {
      result.current.decrement();
    });

    expect(result.current.count).toBe(4);
  });

  it("resets to initial value", () => {
    const { result } = renderHook(() => useCounter(10));

    act(() => {
      result.current.increment();
      result.current.increment();
    });

    expect(result.current.count).toBe(12);

    act(() => {
      result.current.reset();
    });

    expect(result.current.count).toBe(10);
  });

  it("updates when initial value changes", () => {
    const { result, rerender } = renderHook(
      ({ initialValue }) => useCounter(initialValue),
      { initialProps: { initialValue: 0 } }
    );

    expect(result.current.count).toBe(0);

    act(() => {
      result.current.increment();
    });

    rerender({ initialValue: 10 });

    act(() => {
      result.current.reset();
    });

    expect(result.current.count).toBe(10);
  });
});

// ═══════════════════════════════════════════
// Testing with Context
// ═══════════════════════════════════════════

const AuthContext = createContext();

function AuthProvider({ children, initialUser = null }) {
  const [user, setUser] = useState(initialUser);

  const login = (userData) => setUser(userData);
  const logout = () => setUser(null);

  return (
    <AuthContext.Provider value={{ user, login, logout }}>
      {children}
    </AuthContext.Provider>
  );
}

function useAuth() {
  const context = useContext(AuthContext);
  if (!context) throw new Error("useAuth must be used within AuthProvider");
  return context;
}

// Test helper
function renderWithAuth(ui, { user = null, ...options } = {}) {
  return render(<AuthProvider initialUser={user}>{ui}</AuthProvider>, options);
}

function Dashboard() {
  const { user, logout } = useAuth();

  if (!user) return <div>Please log in</div>;

  return (
    <div>
      <h1>Welcome, {user.name}</h1>
      <button onClick={logout}>Logout</button>
    </div>
  );
}

describe("Dashboard", () => {
  it("shows login prompt when not authenticated", () => {
    renderWithAuth(<Dashboard />);

    expect(screen.getByText("Please log in")).toBeInTheDocument();
  });

  it("displays user info when authenticated", () => {
    const user = { id: "123", name: "MrDib" };

    renderWithAuth(<Dashboard />, { user });

    expect(screen.getByText("Welcome, MrDib")).toBeInTheDocument();
  });

  it("logs out user", async () => {
    const user = { id: "123", name: "MrDib" };
    const userEvent = require("@testing-library/user-event").default;

    renderWithAuth(<Dashboard />, { user });

    await userEvent.click(screen.getByRole("button", { name: "Logout" }));

    expect(screen.getByText("Please log in")).toBeInTheDocument();
  });
});

// ═══════════════════════════════════════════
// Testing with React Query
// ═══════════════════════════════════════════

import { QueryClient, QueryClientProvider } from "@tanstack/react-query";

function createTestQueryClient() {
  return new QueryClient({
    defaultOptions: {
      queries: { retry: false },
      mutations: { retry: false },
    },
  });
}

function renderWithQueryClient(ui, client = createTestQueryClient()) {
  return render(
    <QueryClientProvider client={client}>{ui}</QueryClientProvider>
  );
}

function useUser(userId) {
  return useQuery({
    queryKey: ["user", userId],
    queryFn: () => fetchUser(userId),
  });
}

describe("useUser", () => {
  it("fetches user successfully", async () => {
    global.fetch = jest.fn(() =>
      Promise.resolve({
        ok: true,
        json: () => Promise.resolve({ id: "1", name: "MrDib" }),
      })
    );

    const { result } = renderHook(() => useUser("1"), {
      wrapper: ({ children }) => {
        const client = createTestQueryClient();
        return (
          <QueryClientProvider client={client}>{children}</QueryClientProvider>
        );
      },
    });

    await waitFor(() => expect(result.current.isSuccess).toBe(true));

    expect(result.current.data).toEqual({ id: "1", name: "MrDib" });
  });
});
```

---

<div align="center">

## 🟢 Node.js Testing

</div>

### Testing Express APIs 🚀

```javascript
// ═══════════════════════════════════════════
# Express API Testing with Supertest
// ═══════════════════════════════════════════

import request from 'supertest';
import app from '../app';
import { User } from '../models';

// Mock database
jest.mock('../models');

describe('User API', () => {
  beforeEach(() => {
    jest.clearAllMocks();
  });

  describe('GET /api/users', () => {
    it('returns list of users', async () => {
      const mockUsers = [
        { id: '1', name: 'Alice', email: 'alice@example.com' },
        { id: '2', name: 'Bob', email: 'bob@example.com' },
      ];

      User.findAll.mockResolvedValue(mockUsers);

      const response = await request(app)
        .get('/api/users')
        .expect('Content-Type', /json/)
        .expect(200);

      expect(response.body).toEqual({
        success: true,
        data: mockUsers,
      });

      expect(User.findAll).toHaveBeenCalled();
    });

    it('handles database errors', async () => {
      User.findAll.mockRejectedValue(new Error('Database error'));

      const response = await request(app)
        .get('/api/users')
        .expect(500);

      expect(response.body).toMatchObject({
        success: false,
        error: expect.any(String),
      });
    });
  });

  describe('POST /api/users', () => {
    it('creates user with valid data', async () => {
      const newUser = {
        name: 'MrDib',
        email: 'mrdib@example.com',
        password: 'SecurePass123!',
      };

      const createdUser = {
        id: '123',
        name: newUser.name,
        email: newUser.email,
      };

      User.create.mockResolvedValue(createdUser);

      const response = await request(app)
        .post('/api/users')
        .send(newUser)
        .expect(201);

      expect(response.body.data).toMatchObject({
        id: '123',
        name: 'MrDib',
        email: 'mrdib@example.com',
      });

      // Password should not be returned
      expect(response.body.data.password).toBeUndefined();
    });

    it('validates required fields', async () => {
      const response = await request(app)
        .post('/api/users')
        .send({ name: 'Test' }) // Missing email
        .expect(400);

      expect(response.body.error).toMatch(/email/i);
    });

    it('validates email format', async () => {
      const response = await request(app)
        .post('/api/users')
        .send({
          name: 'Test',
          email: 'invalid-email',
          password: 'password123',
        })
        .expect(400);

      expect(response.body.error).toMatch(/valid email/i);
    });
  });

  describe('PUT /api/users/:id', () => {
    it('updates user', async () => {
      const updates = { name: 'Updated Name' };
      const updatedUser = { id: '1', name: 'Updated Name', email: 'test@example.com' };

      User.findByPk.mockResolvedValue({
        update: jest.fn().mockResolvedValue(updatedUser),
      });

      const response = await request(app)
        .put('/api/users/1')
        .set('Authorization', 'Bearer valid-token')
        .send(updates)
        .expect(200);

      expect(response.body.data.name).toBe('Updated Name');
    });

    it('requires authentication', async () => {
      await request(app)
        .put('/api/users/1')
        .send({ name: 'Test' })
        .expect(401);
    });

    it('prevents updating other users', async () => {
      const token = generateToken({ id: '1', role: 'user' });

      await request(app)
        .put('/api/users/2') // Different user ID
        .set('Authorization', `Bearer ${token}`)
        .send({ name: 'Test' })
        .expect(403);
    });
  });

  describe('DELETE /api/users/:id', () => {
    it('deletes user', async () => {
      const mockUser = {
        id: '1',
        destroy: jest.fn().mockResolvedValue(true),
      };

      User.findByPk.mockResolvedValue(mockUser);

      await request(app)
        .delete('/api/users/1')
        .set('Authorization', 'Bearer admin-token')
        .expect(204);

      expect(mockUser.destroy).toHaveBeenCalled();
    });
  });
});

// ═══════════════════════════════════════════
// Service Layer Testing
// ═══════════════════════════════════════════

class UserService {
  constructor(userRepository, emailService) {
    this.userRepository = userRepository;
    this.emailService = emailService;
  }

  async createUser(userData) {
    // Hash password
    const hashedPassword = await bcrypt.hash(userData.password, 10);

    // Create user
    const user = await this.userRepository.create({
      ...userData,
      password: hashedPassword,
    });

    // Send welcome email
    try {
      await this.emailService.sendWelcomeEmail(user.email, user.name);
    } catch (error) {
      console.error('Failed to send welcome email:', error);
    }

    // Return user without password
    const { password, ...userWithoutPassword } = user;
    return userWithoutPassword;
  }
}

describe('UserService', () => {
  let userService;
  let mockUserRepository;
  let mockEmailService;

  beforeEach(() => {
    mockUserRepository = {
      create: jest.fn(),
      findById: jest.fn(),
      update: jest.fn(),
      delete: jest.fn(),
    };

    mockEmailService = {
      sendWelcomeEmail: jest.fn(),
    };

    userService = new UserService(mockUserRepository, mockEmailService);
  });

  describe('createUser', () => {
    it('creates user and sends welcome email', async () => {
      const userData = {
        name: 'MrDib',
        email: 'mrdib@example.com',
        password: 'password123',
      };

      const createdUser = {
        id: '123',
        ...userData,
        password: 'hashed_password',
      };

      mockUserRepository.create.mockResolvedValue(createdUser);
      mockEmailService.sendWelcomeEmail.mockResolvedValue(true);

      const result = await userService.createUser(userData);

      // Verify password was hashed
      expect(mockUserRepository.create).toHaveBeenCalledWith({
        ...userData,
        password: expect.not.stringMatching('password123'),
      });

      // Verify email was sent
      expect(mockEmailService.sendWelcomeEmail).toHaveBeenCalledWith(
        userData.email,
        userData.name
      );

      // Verify password not returned
      expect(result).not.toHaveProperty('password');
      expect(result).toMatchObject({
        id: '123',
        name: 'MrDib',
        email: 'mrdib@example.com',
      });
    });

    it('handles email service failure gracefully', async () => {
      const userData = {
        name: 'MrDib',
        email: 'mrdib@example.com',
        password: 'password123',
      };

      mockUserRepository.create.mockResolvedValue({ id: '123', ...userData });
      mockEmailService.sendWelcomeEmail.mockRejectedValue(
        new Error('Email service down')
      );

      // Should not throw
      const result = await userService.createUser(userData);

      expect(result).toHaveProperty('id');
    });
  });
});
```

---

<div align="center">

## 🎭 Mocking Strategies

</div>

### Effective Mocking Techniques 🎯

```javascript
// ═══════════════════════════════════════════
// Mock Functions
// ═══════════════════════════════════════════

// Basic mock
const mockFn = jest.fn();

// Mock return value
mockFn.mockReturnValue(42);
mockFn.mockReturnValueOnce(1).mockReturnValueOnce(2);

// Mock resolved/rejected promises
mockFn.mockResolvedValue("success");
mockFn.mockRejectedValue(new Error("failed"));

// Mock implementation
mockFn.mockImplementation((a, b) => a + b);

// Check calls
expect(mockFn).toHaveBeenCalled();
expect(mockFn).toHaveBeenCalledTimes(2);
expect(mockFn).toHaveBeenCalledWith(arg1, arg2);
expect(mockFn).toHaveBeenLastCalledWith(arg1);

// Access calls
const calls = mockFn.mock.calls;
const results = mockFn.mock.results;

// Reset
mockFn.mockClear(); // Clear call history
mockFn.mockReset(); // Clear + remove implementation
mockFn.mockRestore(); // Restore original (for spies)

// ═══════════════════════════════════════════
// Mock Modules
// ═══════════════════════════════════════════

// Auto-mock entire module
jest.mock("./api");

// Manual mock
jest.mock("./api", () => ({
  fetchUser: jest.fn(),
  createUser: jest.fn(),
}));

// Partial mock
jest.mock("./api", () => ({
  ...jest.requireActual("./api"),
  fetchUser: jest.fn(),
}));

// Mock default export
jest.mock("./config", () => ({
  __esModule: true,
  default: {
    apiUrl: "http://localhost:3000",
  },
}));

// ═══════════════════════════════════════════
// Spy on Methods
// ═══════════════════════════════════════════

const user = {
  getName: () => "MrDib",
};

const spy = jest.spyOn(user, "getName");

user.getName();

expect(spy).toHaveBeenCalled();

// Restore original
spy.mockRestore();

// Spy and mock return value
jest.spyOn(user, "getName").mockReturnValue("Mocked Name");

// ═══════════════════════════════════════════
// Mock Timers
// ═══════════════════════════════════════════

beforeEach(() => {
  jest.useFakeTimers();
});

afterEach(() => {
  jest.useRealTimers();
});

test("delays execution", () => {
  const callback = jest.fn();

  setTimeout(callback, 1000);

  // Fast-forward time
  jest.advanceTimersByTime(1000);

  expect(callback).toHaveBeenCalled();
});

// Run all timers
jest.runAllTimers();

// Run only pending timers
jest.runOnlyPendingTimers();

// ═══════════════════════════════════════════
// Mock Dates
// ═══════════════════════════════════════════

beforeEach(() => {
  jest.useFakeTimers();
  jest.setSystemTime(new Date("2024-01-01"));
});

afterEach(() => {
  jest.useRealTimers();
});

test("uses mocked date", () => {
  expect(new Date().toISOString()).toBe("2024-01-01T00:00:00.000Z");
});

// ═══════════════════════════════════════════
// Mock Service Worker (MSW)
// ═══════════════════════════════════════════

import { rest } from "msw";
import { setupServer } from "msw/node";

const server = setupServer(
  rest.get("/api/users", (req, res, ctx) => {
    return res(
      ctx.status(200),
      ctx.json({
        users: [{ id: "1", name: "MrDib" }],
      })
    );
  })
);

beforeAll(() => server.listen());
afterEach(() => server.resetHandlers());
afterAll(() => server.close());

test("fetches users", async () => {
  const users = await fetchUsers();
  expect(users).toHaveLength(1);
});

// Override handler for specific test
test("handles error", async () => {
  server.use(
    rest.get("/api/users", (req, res, ctx) => {
      return res(ctx.status(500));
    })
  );

  await expect(fetchUsers()).rejects.toThrow();
});
```

---

<div align="center">

## 💡 Best Practices

</div>

### Unit Testing Guidelines ⭐

```javascript
// ═══════════════════════════════════════════
// 1. Test Behavior, Not Implementation
// ═══════════════════════════════════════════

// ❌ BAD: Testing internal state
test("sets loading to true", () => {
  // Testing implementation detail
});

// ✅ GOOD: Testing user-facing behavior
test("shows loading spinner while fetching", async () => {
  render(<UserList />);

  expect(screen.getByText("Loading...")).toBeInTheDocument();

  await waitFor(() => {
    expect(screen.queryByText("Loading...")).not.toBeInTheDocument();
  });
});

// ═══════════════════════════════════════════
// 2. Use Descriptive Test Names
// ═══════════════════════════════════════════

// ❌ BAD
test("user test", () => {});
test("works", () => {});

// ✅ GOOD
describe("User Registration", () => {
  describe("when email is valid", () => {
    it("creates user account", () => {});
    it("sends welcome email", () => {});
    it("redirects to dashboard", () => {});
  });

  describe("when email is invalid", () => {
    it("shows validation error", () => {});
    it("does not create account", () => {});
  });
});

// ═══════════════════════════════════════════
// 3. Keep Tests Independent
// ═══════════════════════════════════════════

// ❌ BAD: Tests depend on each other
let userId;

test("creates user", () => {
  userId = createUser();
});

test("updates user", () => {
  updateUser(userId); // Depends on previous test
});

// ✅ GOOD: Independent tests
test("updates user", () => {
  const userId = createTestUser();
  updateUser(userId);
});

// ═══════════════════════════════════════════
// 4. Use Test Data Factories
// ═══════════════════════════════════════════

function createUser(overrides = {}) {
  return {
    id: faker.datatype.uuid(),
    name: faker.name.fullName(),
    email: faker.internet.email(),
    createdAt: new Date(),
    ...overrides,
  };
}

test("updates user email", () => {
  const user = createUser({ email: "old@example.com" });

  const updated = updateEmail(user, "new@example.com");

  expect(updated.email).toBe("new@example.com");
});

// ═══════════════════════════════════════════
// 5. Test Edge Cases
// ═══════════════════════════════════════════

describe("divide", () => {
  it("divides positive numbers", () => {
    expect(divide(10, 2)).toBe(5);
  });

  it("divides negative numbers", () => {
    expect(divide(-10, 2)).toBe(-5);
  });

  it("throws on division by zero", () => {
    expect(() => divide(10, 0)).toThrow("Division by zero");
  });

  it("handles decimal division", () => {
    expect(divide(10, 3)).toBeCloseTo(3.333);
  });

  it("handles very large numbers", () => {
    expect(divide(Number.MAX_SAFE_INTEGER, 2)).toBeCloseTo(
      Number.MAX_SAFE_INTEGER / 2
    );
  });
});

// ═══════════════════════════════════════════
// 6. Coverage Goals
// ═══════════════════════════════════════════

const coverageTargets = {
  statements: 80,
  branches: 75,
  functions: 80,
  lines: 80,
};

// Focus on:
// - Critical business logic: 100%
// - Utility functions: 90%+
// - UI components: 80%+
// - Configuration files: Not required
```

---

<div align="center">

**Built with 🧪 by MrDib, for Test-Driven Developers**

_"Tests are the safety net that lets you refactor with confidence!"_

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
- Testing Library: https://testing-library.com/docs/react-testing-library/intro
- React Testing: https://reactjs.org/docs/testing.html

**🎥 Learning Resources:**

- Kent C. Dodds Testing Course
- Testing JavaScript Masterclass
- Jest Crash Course

**🛠️ Tools:**

- Jest VS Code Extension
- Testing Playground: https://testing-playground.com/
- Wallaby.js (Test Runner)

---

### License 📄

This guide is open source and available under the MIT License.

---

<div align="center">

**Stay tested. Keep shipping. Build with confidence!** 💪✨

🧪 **#UnitTesting** 🧪 **#DevResourceVault** 🧪 **#MrDib** 🧪

### Remember

> _"Write tests. Not too many. Mostly integration."_ - Kent C. Dodds

> _"Test behavior, not implementation"_

> _"A test is worth a thousand debugs"_

> _"If you can't test it, you can't maintain it"_

> _"Good tests are a love letter to your future self"_

</div>

---

<div align="center">

**Now go forth and test everything!** 🌟🧪

</div>
