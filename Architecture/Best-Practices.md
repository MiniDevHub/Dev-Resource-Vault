<div align="center">

# ⭐ Best Practices - Write Better Code! ⭐

![Best Practices](https://img.shields.io/badge/Best_Practices-Software_Engineering-blue?style=for-the-badge)
![Clean Code](https://img.shields.io/badge/Clean_Code-Quality-green?style=for-the-badge)
![Standards](https://img.shields.io/badge/Standards-Professional-orange?style=for-the-badge)

### _Professional software engineering practices_ 🎯

**Write code that others (and future you) will love!** ✨

</div>

---

## 📚 Table of Contents

- [🎯 What are Best Practices](#-what-are-best-practices)
- [✨ Clean Code Principles](#-clean-code-principles)
- [📝 Naming Conventions](#-naming-conventions)
- [📖 Comments & Documentation](#-comments--documentation)
- [⚠️ Error Handling](#️-error-handling)
- [🧪 Testing Best Practices](#-testing-best-practices)
- [🔀 Git Best Practices](#-git-best-practices)
- [👀 Code Reviews](#-code-reviews)
- [🔒 Security Best Practices](#-security-best-practices)
- [⚡ Performance Optimization](#-performance-optimization)
- [🗄️ Database Best Practices](#️-database-best-practices)
- [🌐 API Design](#-api-design)
- [🚀 Deployment Practices](#-deployment-practices)
- [💡 General Wisdom](#-general-wisdom)

---

<div align="center">

## 🎯 What are Best Practices

</div>

### Understanding Software Best Practices 🌟

```

# ═══════════════════════════════════════════

# BEST PRACTICES EXPLAINED

# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║ WHAT ARE BEST PRACTICES? ║
╚════════════════════════════════════════════════════════════╝

Best Practices:
─────────────────────────────────────────────────────────────
Proven methods and techniques that lead to better software
development outcomes. Industry-standard approaches that have
been tested and refined over time.

Why Important:
─────────────────────────────────────────────────────────────
✅ Write maintainable code
✅ Reduce bugs
✅ Improve collaboration
✅ Faster development (long-term)
✅ Better code quality
✅ Easier onboarding
✅ Professional standards
✅ Career advancement

Key Principles:
─────────────────────────────────────────────────────────────
• Code is read more than written
• Simple is better than complex
• Consistency matters
• Automate repetitive tasks
• Test your code
• Document your decisions
• Security first
• Performance matters
• Think about maintenance

╔════════════════════════════════════════════════════════════╗
║ THE MINDSET ║
╚════════════════════════════════════════════════════════════╝

Professional Developer Mindset:
─────────────────────────────────────────────────────────────

❌ Amateur Mindset:
"Just make it work"
"I'll fix it later"
"Only I will maintain this"
"Comments are waste of time"
"Tests slow me down"

✅ Professional Mindset:
"Make it work, make it right, make it fast"
"Fix it now, technical debt accumulates"
"Write code for others to read"
"Code explains how, comments explain why"
"Tests save time in long run"

The Goal:
─────────────────────────────────────────────────────────────
Write code that:
• Works correctly
• Is easy to understand
• Is easy to change
• Is easy to test
• Is secure
• Performs well

Remember:
"Any fool can write code that a computer can understand.
Good programmers write code that humans can understand."

- Martin Fowler

╔════════════════════════════════════════════════════════════╗
║ CODE QUALITY PYRAMID ║
╚════════════════════════════════════════════════════════════╝

Hierarchy of Code Quality:
─────────────────────────────────────────────────────────────

```

```

        ┌───────────────┐
        │   Elegant     │  ← Bonus (nice to have)
        ├───────────────┤
        │   Efficient   │  ← Optimize when needed
        ├───────────────┤
        │  Maintainable │  ← Critical!
        ├───────────────┤
        │   Readable    │  ← Most important!
        ├───────────────┤
        │   Correct     │  ← Foundation (must have!)
        └───────────────┘

Priority Order:

1. Correct (works as intended)
2. Readable (easy to understand)
3. Maintainable (easy to change)
4. Efficient (performs well)
5. Elegant (beautiful code)

Don't skip levels!
Elegant but unreadable code is useless.

```

---

<div align="center">

## ✨ Clean Code Principles

</div>

### Write Code That Speaks for Itself 📖

```

# ═══════════════════════════════════════════

# CLEAN CODE PRINCIPLES

# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║ FUNCTIONS/METHODS ║
╚════════════════════════════════════════════════════════════╝

Principle: Do One Thing
─────────────────────────────────────────────────────────────

❌ BAD - Does too much:

```

```javascript
function processUser(userData) {
  // Validate
  if (!userData.email || !userData.email.includes("@")) {
    throw new Error("Invalid email");
  }

  // Hash password
  const hashedPassword = bcrypt.hashSync(userData.password, 10);

  // Save to database
  const user = db.insert({
    name: userData.name,
    email: userData.email,
    password: hashedPassword,
  });

  // Send email
  emailService.sendWelcome(user.email);

  // Log
  logger.info("User created:", user.id);

  return user;
}
```

```
✅ GOOD - Separated responsibilities:
```

```javascript
function createUser(userData) {
  validateUserData(userData);
  const hashedPassword = hashPassword(userData.password);
  const user = saveUser(userData, hashedPassword);
  sendWelcomeEmail(user.email);
  logUserCreation(user.id);
  return user;
}

function validateUserData(userData) {
  if (!userData.email || !userData.email.includes("@")) {
    throw new Error("Invalid email");
  }
}

function hashPassword(password) {
  return bcrypt.hashSync(password, 10);
}

function saveUser(userData, hashedPassword) {
  return db.insert({
    name: userData.name,
    email: userData.email,
    password: hashedPassword,
  });
}

function sendWelcomeEmail(email) {
  emailService.sendWelcome(email);
}

function logUserCreation(userId) {
  logger.info("User created:", userId);
}
```

```
Benefits:
✅ Each function is simple
✅ Easy to test
✅ Easy to reuse
✅ Easy to understand
✅ Easy to modify

Function Guidelines:
─────────────────────────────────────────────────────────────
✅ Small (< 20 lines ideally)
✅ Do one thing
✅ One level of abstraction
✅ Descriptive names
✅ Few parameters (< 3 ideally)
✅ No side effects (when possible)
✅ Return early

╔════════════════════════════════════════════════════════════╗
║                   DRY (DON'T REPEAT YOURSELF)              ║
╚════════════════════════════════════════════════════════════╝

Principle: Don't Duplicate Code
─────────────────────────────────────────────────────────────

❌ BAD - Repetition:
```

```javascript
// Calculating discounts in multiple places
function getProductPrice(product) {
  let price = product.basePrice;
  if (product.category === "electronics") {
    price = price * 0.9; // 10% discount
  }
  return price;
}

function getCartTotal(cart) {
  let total = 0;
  for (const item of cart.items) {
    let price = item.basePrice;
    if (item.category === "electronics") {
      price = price * 0.9; // 10% discount - DUPLICATED!
    }
    total += price * item.quantity;
  }
  return total;
}
```

```
✅ GOOD - Single source of truth:
```

```javascript
function applyDiscount(basePrice, category) {
  const discounts = {
    electronics: 0.9,
    clothing: 0.8,
    food: 1.0,
  };
  return basePrice * (discounts[category] || 1.0);
}

function getProductPrice(product) {
  return applyDiscount(product.basePrice, product.category);
}

function getCartTotal(cart) {
  return cart.items.reduce((total, item) => {
    const price = applyDiscount(item.basePrice, item.category);
    return total + price * item.quantity;
  }, 0);
}
```

```
Benefits:
✅ Single place to update
✅ No inconsistencies
✅ Easier to maintain
✅ Less code

When to DRY:
✅ Same logic in multiple places
✅ Copy-paste code smell
✅ Similar patterns

When NOT to DRY:
❌ Coincidental similarity (may diverge)
❌ Premature abstraction
❌ Makes code harder to understand

"Duplication is far cheaper than wrong abstraction"
- Sandi Metz

╔════════════════════════════════════════════════════════════╗
║                   KISS (KEEP IT SIMPLE)                    ║
╚════════════════════════════════════════════════════════════╝

Principle: Simplicity Over Cleverness
─────────────────────────────────────────────────────────────

❌ BAD - Too clever:
```

```javascript
// Overly complex one-liner
const result = arr.reduce((a, b) => ({ ...a, [b.id]: b }), {});

// What does this do? Need to think...
const x = (a, b) => a.map((v, i) => v + b[i]);
```

```
✅ GOOD - Simple and clear:
```

```javascript
// Convert array to object by id
const result = {};
for (const item of arr) {
  result[item.id] = item;
}

// Add two arrays element-wise
function addArrays(arr1, arr2) {
  return arr1.map((value, index) => value + arr2[index]);
}
```

```
Guidelines:
─────────────────────────────────────────────────────────────
✅ Explicit over implicit
✅ Readable over clever
✅ Simple over complex
✅ Clear over compact

"Debugging is twice as hard as writing the code.
So if you write the code as cleverly as possible,
you are, by definition, not smart enough to debug it."
- Brian Kernighan

╔════════════════════════════════════════════════════════════╗
║                   YAGNI (YOU AIN'T GONNA NEED IT)          ║
╚════════════════════════════════════════════════════════════╝

Principle: Don't Build What You Don't Need Now
─────────────────────────────────────────────────────────────

❌ BAD - Premature features:
```

```javascript
class User {
  constructor(name, email) {
    this.name = name;
    this.email = email;
    this.address = null; // Might need later?
    this.phoneNumber = null; // Just in case?
    this.preferences = {}; // Could be useful?
    this.metadata = {}; // Future-proof!
    this.tags = []; // Why not?
  }

  // Methods we might need someday...
  updatePreferences() {}
  addTag() {}
  removeTag() {}
  exportToJSON() {}
  exportToXML() {}
  exportToCSV() {}
}
```

```
✅ GOOD - Build what you need:
```

```javascript
class User {
  constructor(name, email) {
    this.name = name;
    this.email = email;
  }
}

// Add features when actually needed!
```

```
Benefits:
✅ Less code to maintain
✅ Faster development
✅ No wasted effort
✅ Simpler codebase

When to Add Features:
✅ When actually needed
✅ When requirements are clear
✅ When you have real use case

Avoid:
❌ "We might need this"
❌ "This could be useful"
❌ "Future-proofing"

Build for today, refactor for tomorrow.

╔════════════════════════════════════════════════════════════╗
║                   CODE STRUCTURE                           ║
╚════════════════════════════════════════════════════════════╝

File Organization:
─────────────────────────────────────────────────────────────

❌ BAD - Everything in one file:
```

```
app.js (5000 lines)
├─ Database config
├─ Models
├─ Controllers
├─ Routes
├─ Middleware
├─ Utils
└─ Everything else
```

```
✅ GOOD - Organized structure:
```

```
src/
├── config/
│   ├── database.js
│   └── app.js
├── models/
│   ├── User.js
│   ├── Order.js
│   └── Product.js
├── controllers/
│   ├── UserController.js
│   ├── OrderController.js
│   └── ProductController.js
├── routes/
│   ├── userRoutes.js
│   ├── orderRoutes.js
│   └── productRoutes.js
├── middleware/
│   ├── auth.js
│   └── validation.js
├── services/
│   ├── EmailService.js
│   └── PaymentService.js
├── utils/
│   ├── validators.js
│   └── helpers.js
└── app.js
```

```
Benefits:
✅ Easy to find files
✅ Clear responsibilities
✅ Team-friendly
✅ Scalable

Guidelines:
─────────────────────────────────────────────────────────────
✅ One class/component per file
✅ Group by feature or type
✅ Consistent structure
✅ Clear naming
✅ Reasonable file size (< 300 lines)
```

---

<div align="center">

## 📝 Naming Conventions

</div>

### Names That Reveal Intent 💡

```
# ═══════════════════════════════════════════
# NAMING CONVENTIONS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   GOOD NAMING                              ║
╚════════════════════════════════════════════════════════════╝

Principle: Names Should Reveal Intent
─────────────────────────────────────────────────────────────

❌ BAD - Unclear names:
```

```javascript
const d = 86400000; // milliseconds in a day
const u = getU();
const arr = [];
let temp = 0;
let data = fetchData();

function calc(x, y) {
  return x * y * 0.2;
}

function process(input) {
  // What does this process?
}
```

```
✅ GOOD - Clear names:
```

```javascript
const MILLISECONDS_PER_DAY = 86400000;
const currentUser = getCurrentUser();
const activeUsers = [];
let totalAmount = 0;
let customerOrders = fetchCustomerOrders();

function calculateShippingCost(weight, distance) {
  const COST_PER_KG_PER_KM = 0.2;
  return weight * distance * COST_PER_KG_PER_KM;
}

function validateEmail(email) {
  // Clear what this does
}
```

```
Naming Rules:
─────────────────────────────────────────────────────────────

Variables:
✅ Descriptive nouns
✅ camelCase (most languages)
✅ Meaningful context
✅ Avoid abbreviations

Examples:
• user, currentUser, loggedInUser
• orderList, activeOrders, pendingOrders
• totalPrice, discountedPrice

Functions:
✅ Verb + Noun
✅ Action-oriented
✅ Clear purpose

Examples:
• getUser(), fetchUserData()
• createOrder(), processPayment()
• validateEmail(), isValidPassword()
• calculateTotal(), computeDiscount()

Classes:
✅ PascalCase
✅ Nouns
✅ Singular

Examples:
• User, Order, Product
• EmailService, PaymentProcessor
• UserController, OrderManager

Constants:
✅ UPPER_SNAKE_CASE
✅ Descriptive

Examples:
• MAX_RETRY_COUNT = 3
• API_TIMEOUT_MS = 5000
• DEFAULT_PAGE_SIZE = 20

Booleans:
✅ is/has/can prefix
✅ Question form

Examples:
• isActive, isLoggedIn, isValid
• hasPermission, hasOrders
• canEdit, canDelete

╔════════════════════════════════════════════════════════════╗
║                   AVOID THESE NAMES                        ║
╚════════════════════════════════════════════════════════════╝

Bad Name Patterns:
─────────────────────────────────────────────────────────────

❌ Single Letters (except loop counters):
```

```javascript
const d = new Date(); // What is d?
let x = 10; // What is x?
const u = getUser(); // User? URL? Unknown?

// Only OK in short loops
for (let i = 0; i < 10; i++) {} // OK
```

```
❌ Abbreviations:
```

```javascript
const usr = getUser(); // user
const ord = getOrder(); // order
const msg = getMessage(); // message
const btn = document.querySelector(); // button

// Just spell it out!
const user = getUser();
const order = getOrder();
const message = getMessage();
const button = document.querySelector();
```

```
❌ Generic Names:
```

```javascript
let data = fetchData(); // What data?
let info = getInfo(); // What info?
let temp = calculate(); // Temporary what?
let result = process(); // Result of what?

// Be specific
let userProfile = fetchUserProfile();
let orderDetails = getOrderDetails();
let calculatedTotal = calculateOrderTotal();
let validationResult = validateInput();
```

```
❌ Misleading Names:
```

```javascript
// Says one thing, does another
function getUsers() {
  // Actually creates AND returns users - misleading!
  const users = createUsers();
  return users;
}

// Function name implies no side effects but has them
function calculateTotal(cart) {
  saveToDatabase(cart); // Side effect!
  return cart.total;
}

// Better
function createAndGetUsers() {}
function calculateAndSaveTotal(cart) {}
```

```
❌ Hungarian Notation (outdated):
```

```javascript
// Old style - type in name
let strName = "John";
let intAge = 30;
let arrUsers = [];
let bIsActive = true;

// Modern - let types speak for themselves
let name = "John";
let age = 30;
let users = [];
let isActive = true;
```

```
╔════════════════════════════════════════════════════════════╗
║                   LANGUAGE-SPECIFIC CONVENTIONS            ║
╚════════════════════════════════════════════════════════════╝

JavaScript/TypeScript:
─────────────────────────────────────────────────────────────
• Variables/Functions: camelCase
• Classes: PascalCase
• Constants: UPPER_SNAKE_CASE
• Private: _prefix or #prefix (modern)

const userName = 'John';
function getUserData() {}
class UserService {}
const MAX_RETRIES = 3;

Python:
─────────────────────────────────────────────────────────────
• Variables/Functions: snake_case
• Classes: PascalCase
• Constants: UPPER_SNAKE_CASE
• Private: _prefix

user_name = 'John'
def get_user_data():
class UserService:
MAX_RETRIES = 3

Java:
─────────────────────────────────────────────────────────────
• Variables/Methods: camelCase
• Classes: PascalCase
• Constants: UPPER_SNAKE_CASE
• Packages: lowercase

String userName = "John";
public void getUserData() {}
public class UserService {}
public static final int MAX_RETRIES = 3;

C#:
─────────────────────────────────────────────────────────────
• Local Variables: camelCase
• Public Properties/Methods: PascalCase
• Classes: PascalCase
• Constants: PascalCase

string userName = "John";
public void GetUserData() {}
public class UserService {}
public const int MaxRetries = 3;

Follow your language's conventions!
```

---

<div align="center">

## 📖 Comments & Documentation

</div>

### When and How to Comment 💬

```
# ═══════════════════════════════════════════
# COMMENTS & DOCUMENTATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WHEN TO COMMENT                          ║
╚════════════════════════════════════════════════════════════╝

The Golden Rule:
─────────────────────────────────────────────────────────────
"Code tells you HOW, comments tell you WHY"

Good Comments:
─────────────────────────────────────────────────────────────

✅ Explain WHY (not what):
```

```javascript
// ✅ GOOD - Explains reasoning
// Using setTimeout instead of setInterval because
// we want to wait for the previous request to complete
// before making the next one
setTimeout(fetchData, 5000);

// Using Map for O(1) lookups instead of Array.find() O(n)
const userMap = new Map();

// Workaround for bug in Safari < 14
// https://bugs.webkit.org/show_bug.cgi?id=12345
const result = polyfill();
```

```
✅ Warning about consequences:
```

```javascript
// WARNING: Changing this value affects all users
// Make sure to clear cache after modification
const CACHE_KEY = "user_preferences";

// IMPORTANT: Must be called before init()
// or it will throw an error
function configure() {}

// TODO: Optimize this loop - currently O(n²)
// See issue #123 for discussion
for (let i = 0; i < items.length; i++) {
  for (let j = 0; j < items.length; j++) {
    // ...
  }
}
```

```
✅ Complex business logic:
```

```javascript
// Calculate pro-rated refund based on:
// 1. Days remaining in subscription
// 2. Original purchase price
// 3. Any applicable discounts
// Formula: (daysRemaining / totalDays) * originalPrice * (1 - discount)
function calculateRefund(subscription) {
  const daysRemaining = getDaysRemaining(subscription);
  const totalDays = getTotalDays(subscription);
  const originalPrice = subscription.price;
  const discount = subscription.discount || 0;

  return (daysRemaining / totalDays) * originalPrice * (1 - discount);
}
```

```
✅ Legal/compliance requirements:
```

```javascript
// GDPR Compliance: User data must be encrypted at rest
// and deleted within 30 days of account closure
function storeUserData(data) {
  const encrypted = encrypt(data);
  db.insert(encrypted);
}
```

```
Bad Comments:
─────────────────────────────────────────────────────────────

❌ Stating the obvious:
```

```javascript
// Increment i by 1
i++;

// Get the user
const user = getUser();

// Return true if user is active
function isActive(user) {
  return user.active === true;
}
```

```
❌ Commented out code:
```

```javascript
// Don't do this!
function process() {
  doSomething();
  // doSomethingElse(); // old code
  // anotherThing();    // commented out
  doFinalThing();
}

// Use version control instead!
// Delete commented code.
```

```
❌ Redundant comments:
```

```javascript
// User class
class User {
  // Constructor
  constructor(name) {
    // Set name
    this.name = name;
  }

  // Get name method
  getName() {
    // Return name
    return this.name;
  }
}

// Code is already clear!
```

```
❌ Outdated comments:
```

```javascript
// Returns user from database
function getUser(id) {
  // But now it returns from cache!
  return cache.get(id);
}

// Worse than no comment - misleading!
```

```
╔════════════════════════════════════════════════════════════╗
║                   DOCUMENTATION                            ║
╚════════════════════════════════════════════════════════════╝

Function Documentation:
─────────────────────────────────────────────────────────────

JSDoc (JavaScript):
```

```javascript
/**
 * Calculates the total price including tax and shipping
 *
 * @param {number} basePrice - The base price before tax
 * @param {number} taxRate - Tax rate as decimal (0.1 for 10%)
 * @param {number} shippingCost - Flat shipping cost
 * @returns {number} The total price
 * @throws {Error} If basePrice is negative
 *
 * @example
 * const total = calculateTotal(100, 0.1, 10);
 * // Returns 120 (100 + 10 tax + 10 shipping)
 */
function calculateTotal(basePrice, taxRate, shippingCost) {
  if (basePrice < 0) {
    throw new Error("Base price cannot be negative");
  }

  const tax = basePrice * taxRate;
  return basePrice + tax + shippingCost;
}
```

```
Python Docstrings:
```

```python
def calculate_total(base_price, tax_rate, shipping_cost):
    """
    Calculates the total price including tax and shipping.

    Args:
        base_price (float): The base price before tax
        tax_rate (float): Tax rate as decimal (0.1 for 10%)
        shipping_cost (float): Flat shipping cost

    Returns:
        float: The total price

    Raises:
        ValueError: If base_price is negative

    Example:
        >>> calculate_total(100, 0.1, 10)
        120.0
    """
    if base_price < 0:
        raise ValueError('Base price cannot be negative')

    tax = base_price * tax_rate
    return base_price + tax + shipping_cost
```

```
README.md:
─────────────────────────────────────────────────────────────

Essential sections:
```

````markdown
# Project Name

Brief description of what it does.

## Features

- Feature 1
- Feature 2
- Feature 3

## Installation

```bash
npm install my-package
```
````

## Usage

```javascript
const myPackage = require("my-package");
myPackage.doSomething();
```

## API Reference

### `functionName(param1, param2)`

Description of what it does.

**Parameters:**

- `param1` (string): Description
- `param2` (number): Description

**Returns:** Description of return value

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md)

## License

MIT

```

Best Practices:
─────────────────────────────────────────────────────────────
✅ Keep documentation close to code
✅ Update docs when code changes
✅ Include examples
✅ Document public APIs thoroughly
✅ Private code needs less docs (good names help)
✅ Use diagrams for complex systems
✅ Keep it current (stale docs are worse than none)

```

---

<div align="center">

## ⚠️ Error Handling

</div>

### Handle Errors Gracefully 🛡️

```

# ═══════════════════════════════════════════

# ERROR HANDLING BEST PRACTICES

# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║ TRY-CATCH PROPERLY ║
╚════════════════════════════════════════════════════════════╝

❌ BAD - Silent failures:

```

```javascript
try {
  riskyOperation();
} catch (error) {
  // Silent failure - error disappears!
}

try {
  const data = JSON.parse(input);
} catch (e) {
  console.log("Error"); // Too generic
}
```

```
✅ GOOD - Proper error handling:
```

```javascript
try {
  const data = await fetchData();
  return processData(data);
} catch (error) {
  // Log with context
  logger.error("Failed to fetch and process data", {
    error: error.message,
    stack: error.stack,
    context: { userId: user.id },
  });

  // Re-throw or handle appropriately
  throw new Error("Data processing failed");
}

// Specific error handling
try {
  const data = JSON.parse(input);
  return data;
} catch (error) {
  if (error instanceof SyntaxError) {
    throw new Error(`Invalid JSON format: ${error.message}`);
  }
  throw error;
}
```

```
╔════════════════════════════════════════════════════════════╗
║                   CUSTOM ERRORS                            ║
╚════════════════════════════════════════════════════════════╝

Create Meaningful Errors:
```

```javascript
// Custom error classes
class ValidationError extends Error {
  constructor(message, field) {
    super(message);
    this.name = "ValidationError";
    this.field = field;
    this.statusCode = 400;
  }
}

class NotFoundError extends Error {
  constructor(resource, id) {
    super(`${resource} with id ${id} not found`);
    this.name = "NotFoundError";
    this.statusCode = 404;
  }
}

class AuthenticationError extends Error {
  constructor(message = "Authentication failed") {
    super(message);
    this.name = "AuthenticationError";
    this.statusCode = 401;
  }
}

// Usage
function validateUser(user) {
  if (!user.email) {
    throw new ValidationError("Email is required", "email");
  }
  if (!user.email.includes("@")) {
    throw new ValidationError("Invalid email format", "email");
  }
}

async function getUser(id) {
  const user = await db.findUser(id);
  if (!user) {
    throw new NotFoundError("User", id);
  }
  return user;
}

// Handle in middleware
app.use((error, req, res, next) => {
  logger.error(error);

  if (error instanceof ValidationError) {
    return res.status(400).json({
      error: error.message,
      field: error.field,
    });
  }

  if (error instanceof NotFoundError) {
    return res.status(404).json({ error: error.message });
  }

  // Default error
  res.status(500).json({ error: "Internal server error" });
});
```

```
╔════════════════════════════════════════════════════════════╗
║                   ERROR MESSAGES                           ║
╚════════════════════════════════════════════════════════════╝

Good Error Messages:
─────────────────────────────────────────────────────────────

❌ BAD:
```

```javascript
throw new Error("Error");
throw new Error("Invalid input");
throw new Error("Failed");
```

```
✅ GOOD:
```

```javascript
throw new Error("Email must contain @ symbol");
throw new Error("Password must be at least 8 characters");
throw new Error("User with email john@example.com already exists");
throw new Error("Failed to connect to database: connection timeout");
```

```
Guidelines:
─────────────────────────────────────────────────────────────
✅ Be specific
✅ Include context
✅ Suggest solution when possible
✅ User-friendly for user-facing errors
✅ Technical for developer errors
✅ Don't expose sensitive info (passwords, tokens)

╔════════════════════════════════════════════════════════════╗
║                   ASYNC ERROR HANDLING                     ║
╚════════════════════════════════════════════════════════════╝

Promises:
```

```javascript
// ❌ Unhandled rejection
async function fetchData() {
  const response = await fetch(url); // Could fail!
  return response.json();
}

// ✅ Proper handling
async function fetchData() {
  try {
    const response = await fetch(url);
    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }
    return await response.json();
  } catch (error) {
    logger.error("Failed to fetch data", { error });
    throw error;
  }
}

// ✅ Or use .catch()
fetchData()
  .then((data) => processData(data))
  .catch((error) => handleError(error));
```

```
Error Wrapper Pattern:
```

```javascript
// Utility function to wrap async route handlers
function asyncHandler(fn) {
  return (req, res, next) => {
    Promise.resolve(fn(req, res, next)).catch(next);
  };
}

// Usage
app.get(
  "/users/:id",
  asyncHandler(async (req, res) => {
    const user = await getUser(req.params.id);
    res.json(user);
  })
);

// Errors automatically caught and passed to error middleware
```

```
Global Error Handlers:
```

```javascript
// Node.js - Unhandled rejections
process.on("unhandledRejection", (reason, promise) => {
  logger.error("Unhandled Rejection at:", promise, "reason:", reason);
  // Application-specific logging, throwing an error, or other logic
  process.exit(1);
});

// Node.js - Uncaught exceptions
process.on("uncaughtException", (error) => {
  logger.error("Uncaught Exception:", error);
  process.exit(1);
});
```

---

<div align="center">

## 🧪 Testing Best Practices

</div>

### Write Tests That Matter 🎯

```
# ═══════════════════════════════════════════
# TESTING BEST PRACTICES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   TESTING PYRAMID                          ║
╚════════════════════════════════════════════════════════════╝

The Testing Pyramid:
─────────────────────────────────────────────────────────────
```

```
        ┌─────────────────┐
        │   E2E Tests     │  ← Few (slow, expensive)
        │     (5%)        │
        ├─────────────────┤
        │Integration Tests│  ← Some (medium speed)
        │     (15%)       │
        ├─────────────────┤
        │   Unit Tests    │  ← Many (fast, cheap)
        │     (80%)       │
        └─────────────────┘

Unit Tests:
• Test individual functions/methods
• Fast (milliseconds)
• Many tests
• Mock dependencies

Integration Tests:
• Test multiple components together
• Medium speed (seconds)
• Fewer tests
• Test real integrations

E2E Tests:
• Test entire user flows
• Slow (minutes)
• Few critical paths
• Test like real user
```

```
╔════════════════════════════════════════════════════════════╗
║                   UNIT TEST BEST PRACTICES                 ║
╚════════════════════════════════════════════════════════════╝

Good Unit Tests:
─────────────────────────────────────────────────────────────

✅ AAA Pattern (Arrange-Act-Assert):
```

```javascript
describe("calculateTotal", () => {
  it("should calculate total with tax and shipping", () => {
    // Arrange
    const basePrice = 100;
    const taxRate = 0.1;
    const shippingCost = 10;

    // Act
    const result = calculateTotal(basePrice, taxRate, shippingCost);

    // Assert
    expect(result).toBe(120);
  });

  it("should throw error for negative price", () => {
    // Arrange
    const basePrice = -10;

    // Act & Assert
    expect(() => calculateTotal(basePrice, 0.1, 10)).toThrow(
      "Base price cannot be negative"
    );
  });
});
```

```
Test Naming:
─────────────────────────────────────────────────────────────

❌ BAD:
```

```javascript
it("test1", () => {});
it("works", () => {});
it("calculateTotal", () => {});
```

```
✅ GOOD:
```

```javascript
it("should calculate total with tax and shipping", () => {});
it("should throw error when price is negative", () => {});
it("should return 0 for empty cart", () => {});
it("should apply discount code correctly", () => {});
```

```
Pattern: "should [expected behavior] when [condition]"

Test One Thing:
─────────────────────────────────────────────────────────────

❌ BAD - Testing multiple things:
```

```javascript
it("should validate user", () => {
  expect(validateEmail("test@example.com")).toBe(true);
  expect(validatePassword("12345678")).toBe(true);
  expect(validateAge(25)).toBe(true);
});
```

```
✅ GOOD - One assertion per test:
```

```javascript
describe("validateEmail", () => {
  it("should return true for valid email", () => {
    expect(validateEmail("test@example.com")).toBe(true);
  });

  it("should return false for email without @", () => {
    expect(validateEmail("testexample.com")).toBe(false);
  });

  it("should return false for empty email", () => {
    expect(validateEmail("")).toBe(false);
  });
});
```

```
Mocking:
─────────────────────────────────────────────────────────────
```

```javascript
// Mock external dependencies
const emailService = {
  sendEmail: jest.fn(),
};

describe("createUser", () => {
  it("should send welcome email after user creation", async () => {
    // Arrange
    const userData = { name: "John", email: "john@example.com" };

    // Act
    await createUser(userData, emailService);

    // Assert
    expect(emailService.sendEmail).toHaveBeenCalledWith(
      "john@example.com",
      "Welcome!"
    );
  });
});
```

```
Test Coverage:
─────────────────────────────────────────────────────────────
Aim for:
• 80%+ code coverage (good baseline)
• 100% for critical paths
• Don't obsess over 100% everywhere

Quality > Quantity

╔════════════════════════════════════════════════════════════╗
║                   INTEGRATION TESTS                        ║
╚════════════════════════════════════════════════════════════╝

Test Real Integrations:
```

```javascript
describe("User API Integration", () => {
  let app;
  let db;

  beforeAll(async () => {
    // Set up test database
    db = await createTestDatabase();
    app = createApp(db);
  });

  afterAll(async () => {
    await db.close();
  });

  beforeEach(async () => {
    // Clean database before each test
    await db.clear();
  });

  it("should create and retrieve user", async () => {
    // Create user
    const response = await request(app)
      .post("/api/users")
      .send({ name: "John", email: "john@example.com" })
      .expect(201);

    const userId = response.body.id;

    // Retrieve user
    const getResponse = await request(app)
      .get(`/api/users/${userId}`)
      .expect(200);

    expect(getResponse.body.name).toBe("John");
    expect(getResponse.body.email).toBe("john@example.com");
  });
});
```

```
╔════════════════════════════════════════════════════════════╗
║                   TEST BEST PRACTICES                      ║
╚════════════════════════════════════════════════════════════╝

Guidelines:
─────────────────────────────────────────────────────────────
✅ Tests should be fast
✅ Tests should be independent
✅ Tests should be repeatable
✅ Tests should be self-validating
✅ Tests should be timely (write soon after code)

FIRST Principles:
─────────────────────────────────────────────────────────────
• Fast: Run quickly
• Independent: Don't depend on other tests
• Repeatable: Same result every time
• Self-validating: Pass or fail clearly
• Timely: Write tests with code

What to Test:
✅ Happy path
✅ Edge cases
✅ Error conditions
✅ Boundary values

What NOT to Test:
❌ Third-party libraries
❌ Framework code
❌ Trivial getters/setters
```

---

<div align="center">

## 🔀 Git Best Practices

</div>

### Version Control Like a Pro 📦

```
# ═══════════════════════════════════════════
# GIT BEST PRACTICES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   COMMIT MESSAGES                          ║
╚════════════════════════════════════════════════════════════╝

Good Commit Messages:
─────────────────────────────────────────────────────────────

❌ BAD:
```

```bash
git commit -m "fix"
git commit -m "update"
git commit -m "changes"
git commit -m "asdfasdf"
git commit -m "final version"
git commit -m "final version 2"
```

```
✅ GOOD:
```

```bash
git commit -m "fix: resolve null pointer in user login"
git commit -m "feat: add email validation to signup form"
git commit -m "refactor: extract payment logic into service"
git commit -m "docs: update README with installation steps"
git commit -m "test: add unit tests for user service"
```

```
Conventional Commits Format:
─────────────────────────────────────────────────────────────
```

```
<type>(<scope>): <subject>

<body>

<footer>
```

```
Types:
• feat: New feature
• fix: Bug fix
• docs: Documentation
• style: Formatting (no code change)
• refactor: Code restructuring
• test: Adding tests
• chore: Maintenance

Examples:
```

```bash
feat(auth): add OAuth2 login support

Implemented Google and GitHub OAuth2 providers.
Users can now sign in using their social accounts.

Closes #123

---

fix(api): handle timeout errors in payment service

Added retry logic with exponential backoff for
payment gateway timeouts.

Fixes #456

---

refactor(database): migrate from MongoDB to PostgreSQL

Breaking Change: Database schema has changed.
Run migrations before deploying.
```

```
Guidelines:
─────────────────────────────────────────────────────────────
✅ Use imperative mood ("add" not "added")
✅ First line < 50 characters
✅ Body < 72 characters per line
✅ Explain WHY, not WHAT
✅ Reference issues/tickets

╔════════════════════════════════════════════════════════════╗
║                   BRANCHING STRATEGY                       ║
╚════════════════════════════════════════════════════════════╝

Git Flow (Common Strategy):
─────────────────────────────────────────────────────────────
```

```
main (production)
  ↓
develop (integration)
  ↓
feature/user-auth ────┐
feature/payment   ────┤→ develop → main
hotfix/critical-bug ──┘
```

```
Branch Naming:
```

```bash
# Features
feature/user-authentication
feature/payment-integration
feature/dark-mode

# Bug fixes
fix/login-error
fix/null-pointer-exception

# Hotfixes
hotfix/security-vulnerability
hotfix/payment-crash

# Releases
release/v1.2.0
```

```
Guidelines:
─────────────────────────────────────────────────────────────
✅ One feature per branch
✅ Keep branches short-lived
✅ Merge frequently
✅ Delete merged branches
✅ Rebase vs merge (team decision)

╔════════════════════════════════════════════════════════════╗
║                   WHAT TO COMMIT                           ║
╚════════════════════════════════════════════════════════════╝

DO Commit:
─────────────────────────────────────────────────────────────
✅ Source code
✅ Configuration files
✅ Documentation
✅ Tests
✅ Build scripts

DON'T Commit:
─────────────────────────────────────────────────────────────
❌ Dependencies (node_modules, vendor)
❌ Build artifacts (dist, build)
❌ Environment variables (.env)
❌ IDE files (.vscode, .idea)
❌ OS files (.DS_Store, Thumbs.db)
❌ Sensitive data (API keys, passwords)
❌ Large binary files (use Git LFS)

.gitignore:
```

```bash
# Dependencies
node_modules/
vendor/

# Build
dist/
build/
*.log

# Environment
.env
.env.local

# IDE
.vscode/
.idea/
*.swp

# OS
.DS_Store
Thumbs.db
```

```
╔════════════════════════════════════════════════════════════╗
║                   USEFUL GIT COMMANDS                      ║
╚════════════════════════════════════════════════════════════╝

Essential Commands:
```

```bash
# Stage changes
git add <file>
git add .

# Commit
git commit -m "message"
git commit --amend  # Fix last commit

# Branches
git checkout -b feature/new-feature
git branch -d feature/old-feature
git branch -a  # List all branches

# Push/Pull
git push origin feature/branch
git pull origin main

# Stash (save work temporarily)
git stash
git stash pop
git stash list

# Undo changes
git checkout -- <file>  # Discard local changes
git reset HEAD <file>   # Unstage
git reset --hard HEAD~1 # Undo last commit (careful!)

# History
git log --oneline --graph
git log --author="John"
git blame <file>  # See who changed what

# Rebase
git rebase main  # Update feature branch
git rebase -i HEAD~3  # Interactive rebase

# Cherry-pick
git cherry-pick <commit-hash>  # Apply specific commit
```

```
Best Practices:
─────────────────────────────────────────────────────────────
✅ Commit often
✅ Pull before you push
✅ Review changes before committing
✅ Write meaningful commit messages
✅ Don't commit directly to main
✅ Use pull requests
✅ Keep commits atomic (one logical change)
```

---

<div align="center">

## 👀 Code Reviews

</div>

### Review Code Effectively 🔍

```
# ═══════════════════════════════════════════
# CODE REVIEW BEST PRACTICES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WHY CODE REVIEWS                         ║
╚════════════════════════════════════════════════════════════╝

Benefits:
─────────────────────────────────────────────────────────────
✅ Catch bugs early
✅ Share knowledge
✅ Maintain code quality
✅ Enforce standards
✅ Mentoring opportunity
✅ Better design decisions
✅ Reduce technical debt

Statistics:
─────────────────────────────────────────────────────────────
• 60% of bugs found in code reviews
• Reviews improve code quality by 40%
• Team knowledge sharing
• Faster onboarding

╔════════════════════════════════════════════════════════════╗
║                   FOR AUTHORS                              ║
╚════════════════════════════════════════════════════════════╝

Before Submitting PR:
─────────────────────────────────────────────────────────────
☐ Code works and is tested
☐ All tests pass
☐ No console.logs or debugger statements
☐ Code follows style guide
☐ No commented-out code
☐ PR is small (< 400 lines)
☐ Clear description
☐ Linked to issue/ticket

PR Description Template:
```

```markdown
## What

Brief description of changes

## Why

Reason for this change

## How

Technical approach

## Testing

How to test these changes

## Screenshots (if UI)

[Include screenshots]

## Checklist

- [ ] Tests added
- [ ] Documentation updated
- [ ] No breaking changes
```

```
PR Best Practices:
─────────────────────────────────────────────────────────────
✅ Keep PRs small (< 400 lines)
✅ One feature per PR
✅ Clear title and description
✅ Link to issue
✅ Self-review first
✅ Add comments for complex logic
✅ Respond to feedback promptly
✅ Be open to suggestions

╔════════════════════════════════════════════════════════════╗
║                   FOR REVIEWERS                            ║
╚════════════════════════════════════════════════════════════╝

What to Look For:
─────────────────────────────────────────────────────────────

1. Functionality:
☐ Does it work as intended?
☐ Are edge cases handled?
☐ Any bugs?

2. Code Quality:
☐ Is it readable?
☐ Are names clear?
☐ Is it maintainable?
☐ Any code smells?

3. Tests:
☐ Are there tests?
☐ Do tests cover edge cases?
☐ Do all tests pass?

4. Performance:
☐ Any performance issues?
☐ Unnecessary loops?
☐ Memory leaks?

5. Security:
☐ SQL injection risk?
☐ XSS vulnerabilities?
☐ Authentication/authorization?
☐ Sensitive data exposure?

6. Standards:
☐ Follows style guide?
☐ Consistent with codebase?
☐ Uses team conventions?

How to Give Feedback:
─────────────────────────────────────────────────────────────

❌ BAD:
```

```
"This is wrong"
"Bad code"
"Why did you do this?"
"This is stupid"
```

```
✅ GOOD:
```

```
"Consider using map() instead of for loop for better readability"
"This could cause a memory leak if..."
"What do you think about extracting this into a separate function?"
"Nice solution! One suggestion: we could use..."
```

```
Feedback Guidelines:
─────────────────────────────────────────────────────────────
✅ Be kind and respectful
✅ Explain WHY (not just what)
✅ Suggest alternatives
✅ Ask questions
✅ Praise good code
✅ Focus on code, not person
✅ Use "we" not "you"

Comment Prefixes:
─────────────────────────────────────────────────────────────
• [nit]: Minor suggestion (not blocking)
• [question]: Need clarification
• [suggestion]: Optional improvement
• [issue]: Must fix before merge
• [praise]: Good code!

Examples:
```

```
[nit]: Consider renaming `data` to `userData` for clarity

[question]: How does this handle null values?

[suggestion]: We could use Promise.all() here for better performance

[issue]: This will fail if user is undefined

[praise]: Great use of error handling here!
```

```
Review Timing:
─────────────────────────────────────────────────────────────
✅ Review within 24 hours
✅ Prioritize small PRs
✅ Block time for reviews
✅ Don't review when rushed
```

---

<div align="center">

## 🔒 Security Best Practices

</div>

### Write Secure Code 🛡️

```
# ═══════════════════════════════════════════
# SECURITY BEST PRACTICES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   COMMON VULNERABILITIES                   ║
╚════════════════════════════════════════════════════════════╝

OWASP Top 10 (2021):
─────────────────────────────────────────────────────────────
1. Broken Access Control
2. Cryptographic Failures
3. Injection
4. Insecure Design
5. Security Misconfiguration
6. Vulnerable Components
7. Authentication Failures
8. Data Integrity Failures
9. Logging Failures
10. Server-Side Request Forgery

╔════════════════════════════════════════════════════════════╗
║                   INPUT VALIDATION                         ║
╚════════════════════════════════════════════════════════════╝

Never Trust User Input:
─────────────────────────────────────────────────────────────

❌ BAD - SQL Injection:
```

```javascript
// NEVER do this!
const query = `SELECT * FROM users WHERE email = '${email}'`;
db.query(query);

// Attacker can input: ' OR '1'='1
// Query becomes: SELECT * FROM users WHERE email = '' OR '1'='1'
// Returns all users!
```

```
✅ GOOD - Use parameterized queries:
```

```javascript
// Parameterized query (safe)
const query = "SELECT * FROM users WHERE email = ?";
db.query(query, [email]);

// ORM (safe)
const user = await User.findOne({ where: { email } });
```

```
❌ BAD - XSS (Cross-Site Scripting):
```

```javascript
// Directly inserting user input
element.innerHTML = userInput;

// Attacker input: <script>alert('XSS')</script>
// Script executes!
```

```
✅ GOOD - Sanitize and escape:
```

```javascript
// Use textContent (no HTML)
element.textContent = userInput;

// Or sanitize HTML
import DOMPurify from "dompurify";
const clean = DOMPurify.sanitize(userInput);
element.innerHTML = clean;
```

```
Validation Rules:
─────────────────────────────────────────────────────────────
✅ Validate on server (not just client)
✅ Whitelist (allow known good) > Blacklist
✅ Sanitize all input
✅ Validate data types
✅ Check length limits
✅ Validate format (email, phone, etc.)

╔════════════════════════════════════════════════════════════╗
║                   AUTHENTICATION & AUTHORIZATION           ║
╚════════════════════════════════════════════════════════════╝

Password Security:
```

```javascript
// ❌ NEVER store plain text passwords!
const user = { password: "password123" };

// ❌ NEVER use weak hashing (MD5, SHA1)
const hash = md5(password);

// ✅ Use bcrypt or argon2
const bcrypt = require("bcrypt");
const saltRounds = 10;
const hashedPassword = await bcrypt.hash(password, saltRounds);

// Verify
const isValid = await bcrypt.compare(inputPassword, hashedPassword);
```

```
JWT Best Practices:
```

```javascript
// ✅ Use strong secret
const secret = process.env.JWT_SECRET; // 32+ random characters

// ✅ Set expiration
const token = jwt.sign({ userId }, secret, { expiresIn: "1h" });

// ✅ Validate token
try {
  const decoded = jwt.verify(token, secret);
} catch (error) {
  // Invalid or expired token
}

// ✅ Store securely (httpOnly cookie)
res.cookie("token", token, {
  httpOnly: true, // Prevent JavaScript access
  secure: true, // HTTPS only
  sameSite: "strict",
});
```

```
Authorization:
```

```javascript
// Check permissions before actions
function deleteUser(requestingUser, targetUserId) {
  if (!requestingUser.isAdmin) {
    throw new Error("Unauthorized");
  }

  // Delete user
}

// Never trust client-side permissions
// Always check on server
```

```
╔════════════════════════════════════════════════════════════╗
║                   SENSITIVE DATA                           ║
╚════════════════════════════════════════════════════════════╝

Environment Variables:
```

```javascript
// ❌ NEVER commit secrets
const apiKey = 'sk_live_abc123';  // NEVER!

// ✅ Use environment variables
const apiKey = process.env.API_KEY;

// .env file
API_KEY=sk_live_abc123
DATABASE_URL=postgresql://...

// .gitignore
.env
.env.local
```

```
Data Encryption:
```

```javascript
// Encrypt sensitive data at rest
const crypto = require("crypto");

function encrypt(text, key) {
  const iv = crypto.randomBytes(16);
  const cipher = crypto.createCipheriv("aes-256-cbc", Buffer.from(key), iv);
  let encrypted = cipher.update(text);
  encrypted = Buffer.concat([encrypted, cipher.final()]);
  return iv.toString("hex") + ":" + encrypted.toString("hex");
}

function decrypt(text, key) {
  const parts = text.split(":");
  const iv = Buffer.from(parts.shift(), "hex");
  const encrypted = Buffer.from(parts.join(":"), "hex");
  const decipher = crypto.createDecipheriv("aes-256-cbc", Buffer.from(key), iv);
  let decrypted = decipher.update(encrypted);
  decrypted = Buffer.concat([decrypted, decipher.final()]);
  return decrypted.toString();
}
```

```
Best Practices:
─────────────────────────────────────────────────────────────
✅ Never log passwords or tokens
✅ Encrypt sensitive data at rest
✅ Use HTTPS everywhere
✅ Implement rate limiting
✅ Use security headers
✅ Keep dependencies updated
✅ Regular security audits
✅ Principle of least privilege
```

---

## 💡 Quick Reference

### Best Practices Checklist ✅

```
╔════════════════════════════════════════════════════════════╗
║                   DAILY CHECKLIST                          ║
╚════════════════════════════════════════════════════════════╝

Before Committing:
─────────────────────────────────────────────────────────────
☐ Code works
☐ Tests pass
☐ No console.logs
☐ No commented code
☐ Clear commit message
☐ Small, focused commit

Before Creating PR:
─────────────────────────────────────────────────────────────
☐ Self-review
☐ All tests pass
☐ Clear description
☐ Link to issue
☐ Screenshots (if UI)
☐ No secrets committed

Code Quality:
─────────────────────────────────────────────────────────────
☐ Clear names
☐ Functions do one thing
☐ No duplication
☐ Proper error handling
☐ Comments for WHY
☐ Tests included

Remember:
"Clean code is not written by following a set of rules.
You don't become a software craftsman by learning a list of what to do.
Professionalism and craftsmanship come from discipline and practice."
- Robert C. Martin
```

---

<div align="center">

**Built with ⭐ by MrDib, for professional developers**

_Remember: "Any fool can write code that a computer can understand. Good programmers write code that humans can understand."_ ✨

**Happy Coding!** 🚀

</div>

---

## 🔗 Related Guides

- [Design Patterns](./Design-Patterns.md)
- [System Design](./System-Design.md)
- [Microservices](./Microservices.md)
- [Clean Code](../Development/Clean-Code.md)

---
