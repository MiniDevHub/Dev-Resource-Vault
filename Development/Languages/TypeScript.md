<div align="center">

# 🔷 TypeScript - JavaScript with Superpowers

### _Type safety meets JavaScript flexibility_ 💪

![TypeScript](https://img.shields.io/badge/TypeScript-5.3+-blue?style=for-the-badge&logo=typescript)
![Type Safety](https://img.shields.io/badge/Type%20Safety-Strong-green?style=for-the-badge)
![JavaScript](https://img.shields.io/badge/Superset-JavaScript-yellow?style=for-the-badge)

</div>

---

## 📚 Table of Contents

- [🎯 TypeScript Fundamentals](#-typescript-fundamentals)
- [📊 Types & Type System](#-types--type-system)
- [🔧 Functions & Generics](#-functions--generics)
- [🏗️ Interfaces & Classes](#️-interfaces--classes)
- [🎨 Advanced Types](#-advanced-types)
- [⚛️ React with TypeScript](#️-react-with-typescript)
- [🌐 Node.js & Express](#-nodejs--express)
- [🗄️ TypeScript with Databases](#️-typescript-with-databases)
- [🧪 Testing](#-testing)
- [🎯 Common Patterns](#-common-patterns)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 🎯 TypeScript Fundamentals

</div>

### Getting Started with TypeScript 🚀

```bash
# ═══════════════════════════════════════════
# Installation & Setup
# ═══════════════════════════════════════════

# Install TypeScript globally
npm install -g typescript

# Check version
tsc --version

# Initialize TypeScript project
tsc --init

# Install TypeScript locally (recommended)
npm install --save-dev typescript

# Install type definitions
npm install --save-dev @types/node
npm install --save-dev @types/express
npm install --save-dev @types/react

# ═══════════════════════════════════════════
# Compile TypeScript
# ═══════════════════════════════════════════

# Compile single file
tsc file.ts

# Compile with config
tsc

# Watch mode
tsc --watch

# Compile specific files
tsc file1.ts file2.ts

# ═══════════════════════════════════════════
# Using ts-node (Run TS directly)
# ═══════════════════════════════════════════

# Install ts-node
npm install --save-dev ts-node

# Run TypeScript file
npx ts-node src/index.ts

# With nodemon for development
npm install --save-dev nodemon
npx nodemon --exec ts-node src/index.ts
```

---

### Hello World & Basic Syntax 📝

```typescript
// ═══════════════════════════════════════════
// Hello World
// ═══════════════════════════════════════════

console.log("Hello from MrDib! 🔷");

// Variables
let name: string = "MrDib";
let age: number = 25;
let isActive: boolean = true;

// Type inference (TypeScript can figure out types)
let inferredString = "TypeScript is smart"; // Type: string
let inferredNumber = 42; // Type: number

// Constants
const PI: number = 3.14159;
const VERSION = "1.0.0"; // Type inferred as string

// ═══════════════════════════════════════════
// Type Annotations
// ═══════════════════════════════════════════

// Explicit types
let username: string;
let score: number;
let isValid: boolean;

username = "Alice";
score = 100;
isValid = true;

// Multiple variable declarations
let x: number, y: number, z: number;

// Array notation
let numbers: number[] = [1, 2, 3, 4, 5];
let names: string[] = ["Alice", "Bob", "Charlie"];

// Alternative array syntax
let moreNumbers: Array<number> = [6, 7, 8, 9, 10];

// ═══════════════════════════════════════════
// Comments
// ═══════════════════════════════════════════

// Single-line comment

/*
 * Multi-line comment
 * More details here
 */

/**
 * JSDoc comment (for documentation)
 * @param name - User's name
 * @returns Greeting message
 */
function greet(name: string): string {
  return `Hello, ${name}!`;
}
```

> **💡 Pro Tip:** Let TypeScript infer types when possible - it makes code cleaner! Only add explicit type annotations when needed for clarity or when inference doesn't work.

---

<div align="center">

## 📊 Types & Type System

</div>

### Primitive Types 🔢

```typescript
// ═══════════════════════════════════════════
// Basic Types
// ═══════════════════════════════════════════

// String
let message: string = "Hello, TypeScript!";
let template: string = `Value is ${message}`;

// Number (integers and floats)
let integer: number = 42;
let float: number = 3.14;
let hex: number = 0xf00d;
let binary: number = 0b1010;
let octal: number = 0o744;
let bigNum: number = 1_000_000; // Numeric separators

// Boolean
let isTrue: boolean = true;
let isFalse: boolean = false;

// Null and Undefined
let nullValue: null = null;
let undefinedValue: undefined = undefined;

// With strictNullChecks, these are separate types!
let maybeString: string | null = null;
let maybeNumber: number | undefined = undefined;

// Symbol
let sym1: symbol = Symbol("key");
let sym2: symbol = Symbol("key");
// sym1 === sym2  // false, symbols are unique

// BigInt (for very large integers)
let bigInt: bigint = 9007199254740991n;

// ═══════════════════════════════════════════
// Special Types
// ═══════════════════════════════════════════

// any - Avoid when possible!
let anything: any = "can be anything";
anything = 42;
anything = true;
anything.doWhatever(); // No type checking!

// unknown - Safer alternative to any
let unknownValue: unknown = "could be anything";
// unknownValue.toUpperCase();  // ❌ Error! Must check type first

if (typeof unknownValue === "string") {
  console.log(unknownValue.toUpperCase()); // ✅ OK after check
}

// void - No return value
function logMessage(message: string): void {
  console.log(message);
  // No return statement
}

// never - Function never returns
function throwError(message: string): never {
  throw new Error(message);
}

function infiniteLoop(): never {
  while (true) {
    // Never exits
  }
}

// ═══════════════════════════════════════════
// Arrays
// ═══════════════════════════════════════════

// Array of numbers
let numbers: number[] = [1, 2, 3, 4, 5];

// Array of strings
let fruits: string[] = ["apple", "banana", "orange"];

// Generic array syntax
let scores: Array<number> = [95, 87, 92];

// Mixed array (not recommended)
let mixed: any[] = [1, "two", true];

// Better: Use union types
let mixedTyped: (number | string | boolean)[] = [1, "two", true];

// Multi-dimensional arrays
let matrix: number[][] = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9],
];

// Readonly arrays
let readonlyNumbers: readonly number[] = [1, 2, 3];
// readonlyNumbers.push(4);  // ❌ Error! Can't modify

// ═══════════════════════════════════════════
// Tuples (Fixed-length arrays with specific types)
// ═══════════════════════════════════════════

// Basic tuple
let user: [string, number] = ["MrDib", 25];
let point: [number, number] = [10, 20];

// Accessing tuple elements
let name = user[0]; // string
let age = user[1]; // number

// Destructuring tuples
let [username, userAge] = user;

// Optional elements
let optional: [string, number?] = ["Alice"];

// Rest elements
let rest: [string, ...number[]] = ["scores", 95, 87, 92];

// Labeled tuples (TypeScript 4.0+)
let labeledTuple: [name: string, age: number] = ["Bob", 30];

// ═══════════════════════════════════════════
// Object Types
// ═══════════════════════════════════════════

// Inline object type
let person: { name: string; age: number } = {
  name: "MrDib",
  age: 25,
};

// Optional properties
let partialPerson: { name: string; age?: number } = {
  name: "Alice",
};

// Readonly properties
let immutable: { readonly id: string; name: string } = {
  id: "123",
  name: "Bob",
};
// immutable.id = "456";  // ❌ Error! Can't modify

// Index signatures
let dictionary: { [key: string]: number } = {
  apples: 5,
  oranges: 10,
  bananas: 3,
};
```

---

### Union & Intersection Types 🔀

```typescript
// ═══════════════════════════════════════════
// Union Types (OR)
// ═══════════════════════════════════════════

// Basic union
let id: string | number;
id = "abc123"; // ✅ OK
id = 123; // ✅ OK
// id = true;   // ❌ Error!

// Union with multiple types
let value: string | number | boolean;

// Function with union parameter
function formatId(id: string | number): string {
  if (typeof id === "string") {
    return id.toUpperCase();
  } else {
    return id.toString();
  }
}

// Array of union types
let mixed: (string | number)[] = [1, "two", 3, "four"];

// ═══════════════════════════════════════════
// Literal Types
// ═══════════════════════════════════════════

// String literals
let direction: "north" | "south" | "east" | "west";
direction = "north"; // ✅ OK
// direction = "up";  // ❌ Error!

// Number literals
let dice: 1 | 2 | 3 | 4 | 5 | 6;

// Boolean literals (not common)
let yes: true = true;

// Combined literals
type Status = "pending" | "approved" | "rejected";
type Priority = 1 | 2 | 3 | 4 | 5;

// ═══════════════════════════════════════════
// Type Aliases
// ═══════════════════════════════════════════

// Basic type alias
type ID = string | number;
type Status = "active" | "inactive" | "pending";

// Object type alias
type User = {
  id: ID;
  name: string;
  email: string;
  status: Status;
};

// Function type alias
type MathOperation = (a: number, b: number) => number;

const add: MathOperation = (a, b) => a + b;
const subtract: MathOperation = (a, b) => a - b;

// ═══════════════════════════════════════════
// Intersection Types (AND)
// ═══════════════════════════════════════════

// Combine multiple types
type Timestamped = {
  createdAt: Date;
  updatedAt: Date;
};

type WithAuthor = {
  authorId: string;
  authorName: string;
};

type BlogPost = {
  title: string;
  content: string;
} & Timestamped &
  WithAuthor;

const post: BlogPost = {
  title: "TypeScript Guide",
  content: "...",
  createdAt: new Date(),
  updatedAt: new Date(),
  authorId: "123",
  authorName: "MrDib",
};

// ═══════════════════════════════════════════
// Type Assertions (Type Casting)
// ═══════════════════════════════════════════

// as syntax (recommended)
let someValue: unknown = "this is a string";
let strLength: number = (someValue as string).length;

// Angle-bracket syntax (not in JSX)
let altLength: number = (<string>someValue).length;

// Asserting to more specific type
interface Cat {
  name: string;
  meow(): void;
}

interface Dog {
  name: string;
  bark(): void;
}

let pet = getRandomPet(); // Returns Cat | Dog
(pet as Cat).meow(); // Assert it's a Cat

// Non-null assertion operator
function getValue(): string | null {
  return "value";
}

let value = getValue()!; // Assert it's not null
// Use carefully! Only when you're 100% sure

// Const assertions
let tuple = [10, 20] as const; // readonly [10, 20]
let obj = { x: 10, y: 20 } as const; // All properties readonly
```

> **💡 Pro Tip:** Use union types for "one of several options" and intersection types for "all of these combined". Type assertions should be used sparingly - let TypeScript infer when possible!

---

<div align="center">

## 🔧 Functions & Generics

</div>

### Function Types 📦

```typescript
// ═══════════════════════════════════════════
// Function Declarations
// ═══════════════════════════════════════════

// Basic function
function add(a: number, b: number): number {
  return a + b;
}

// Function with no return value
function logMessage(message: string): void {
  console.log(message);
}

// Optional parameters
function greet(name: string, greeting?: string): string {
  return `${greeting || "Hello"}, ${name}!`;
}

// Default parameters
function createUser(name: string, role: string = "user"): User {
  return { name, role };
}

// Rest parameters
function sum(...numbers: number[]): number {
  return numbers.reduce((acc, num) => acc + num, 0);
}

// ═══════════════════════════════════════════
// Arrow Functions
// ═══════════════════════════════════════════

// Basic arrow function
const multiply = (a: number, b: number): number => a * b;

// With block body
const divide = (a: number, b: number): number => {
  if (b === 0) {
    throw new Error("Division by zero");
  }
  return a / b;
};

// Single parameter (no parens needed)
const double = (x: number): number => x * 2;

// No parameters
const getRandomNumber = (): number => Math.random();

// ═══════════════════════════════════════════
// Function Types
// ═══════════════════════════════════════════

// Function type annotation
let operation: (a: number, b: number) => number;

operation = (x, y) => x + y;
operation = (x, y) => x * y;

// Type alias for function
type MathOp = (a: number, b: number) => number;

const subtract: MathOp = (a, b) => a - b;

// Function as parameter
function calculate(a: number, b: number, op: MathOp): number {
  return op(a, b);
}

calculate(10, 5, add); // 15
calculate(10, 5, subtract); // 5

// ═══════════════════════════════════════════
// Overloading
// ═══════════════════════════════════════════

// Function overload signatures
function format(value: string): string;
function format(value: number): string;
function format(value: boolean): string;

// Implementation signature
function format(value: string | number | boolean): string {
  if (typeof value === "string") {
    return value.toUpperCase();
  } else if (typeof value === "number") {
    return value.toFixed(2);
  } else {
    return value ? "YES" : "NO";
  }
}

format("hello"); // "HELLO"
format(3.14159); // "3.14"
format(true); // "YES"

// ═══════════════════════════════════════════
// Callback Functions
// ═══════════════════════════════════════════

// Callback with parameters
function fetchData(
  url: string,
  callback: (error: Error | null, data: any) => void
): void {
  // Simulated async operation
  setTimeout(() => {
    callback(null, { result: "Success" });
  }, 1000);
}

// Usage
fetchData("/api/data", (error, data) => {
  if (error) {
    console.error(error);
  } else {
    console.log(data);
  }
});

// ═══════════════════════════════════════════
// Promise Return Types
// ═══════════════════════════════════════════

async function getUserData(id: string): Promise<User> {
  const response = await fetch(`/api/users/${id}`);
  return response.json();
}

// Promise with union type
async function getOptionalUser(id: string): Promise<User | null> {
  try {
    return await getUserData(id);
  } catch {
    return null;
  }
}
```

---

### Generics - Reusable Type-Safe Code 🧬

```typescript
// ═══════════════════════════════════════════
// Generic Functions
// ═══════════════════════════════════════════

// Basic generic
function identity<T>(arg: T): T {
  return arg;
}

let num = identity<number>(42);
let str = identity<string>("hello");
let inferred = identity("auto"); // T inferred as string

// Generic with array
function getFirstElement<T>(arr: T[]): T | undefined {
  return arr[0];
}

let firstNum = getFirstElement([1, 2, 3]); // number | undefined
let firstStr = getFirstElement(["a", "b", "c"]); // string | undefined

// Multiple type parameters
function pair<T, U>(first: T, second: U): [T, U] {
  return [first, second];
}

let stringNumber = pair("age", 25); // [string, number]
let boolString = pair(true, "yes"); // [boolean, string]

// ═══════════════════════════════════════════
// Generic Constraints
// ═══════════════════════════════════════════

// Constrain to types with length property
interface HasLength {
  length: number;
}

function logLength<T extends HasLength>(item: T): void {
  console.log(item.length);
}

logLength("hello"); // ✅ string has length
logLength([1, 2, 3]); // ✅ array has length
// logLength(42);          // ❌ number doesn't have length

// Constrain to object keys
function getProperty<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}

let person = { name: "MrDib", age: 25 };
let name = getProperty(person, "name"); // string
let age = getProperty(person, "age"); // number
// let invalid = getProperty(person, "invalid");  // ❌ Error!

// ═══════════════════════════════════════════
// Generic Interfaces
// ═══════════════════════════════════════════

interface Container<T> {
  value: T;
  getValue(): T;
  setValue(value: T): void;
}

class NumberContainer implements Container<number> {
  constructor(public value: number) {}

  getValue(): number {
    return this.value;
  }

  setValue(value: number): void {
    this.value = value;
  }
}

// ═══════════════════════════════════════════
// Generic Classes
// ═══════════════════════════════════════════

class Stack<T> {
  private items: T[] = [];

  push(item: T): void {
    this.items.push(item);
  }

  pop(): T | undefined {
    return this.items.pop();
  }

  peek(): T | undefined {
    return this.items[this.items.length - 1];
  }

  isEmpty(): boolean {
    return this.items.length === 0;
  }

  size(): number {
    return this.items.length;
  }
}

// Usage
const numberStack = new Stack<number>();
numberStack.push(1);
numberStack.push(2);
console.log(numberStack.pop()); // 2

const stringStack = new Stack<string>();
stringStack.push("hello");
stringStack.push("world");

// ═══════════════════════════════════════════
// Generic Type Aliases
// ═══════════════════════════════════════════

type Result<T, E = Error> =
  | { success: true; data: T }
  | { success: false; error: E };

function divide(a: number, b: number): Result<number, string> {
  if (b === 0) {
    return { success: false, error: "Division by zero" };
  }
  return { success: true, data: a / b };
}

// Response wrapper
type ApiResponse<T> = {
  data: T;
  status: number;
  message: string;
};

async function fetchUser(id: string): Promise<ApiResponse<User>> {
  const response = await fetch(`/api/users/${id}`);
  return response.json();
}

// ═══════════════════════════════════════════
// Utility Types with Generics
// ═══════════════════════════════════════════

interface User {
  id: string;
  name: string;
  email: string;
  password: string;
  role: string;
}

// Partial - All properties optional
type PartialUser = Partial<User>;

// Required - All properties required
type RequiredUser = Required<User>;

// Readonly - All properties readonly
type ReadonlyUser = Readonly<User>;

// Pick - Select specific properties
type UserCredentials = Pick<User, "email" | "password">;

// Omit - Remove specific properties
type UserWithoutPassword = Omit<User, "password">;

// Record - Create object type
type UserMap = Record<string, User>;

// Exclude - Remove from union
type Role = "admin" | "user" | "guest";
type NonGuestRole = Exclude<Role, "guest">; // "admin" | "user"

// Extract - Keep only matching types
type AdminRole = Extract<Role, "admin">; // "admin"

// ReturnType - Extract function return type
type AddReturn = ReturnType<typeof add>; // number

// Parameters - Extract function parameters
type AddParams = Parameters<typeof add>; // [number, number]
```

> **💡 Pro Tip:** Generics are TypeScript's superpower! Use them to write reusable, type-safe code. Start with simple generics and gradually add constraints as needed.

---

<div align="center">

## 🏗️ Interfaces & Classes

</div>

### Interfaces - Defining Contracts 📋

```typescript
// ═══════════════════════════════════════════
// Basic Interface
// ═══════════════════════════════════════════

interface User {
  id: string;
  name: string;
  email: string;
}

const user: User = {
  id: "123",
  name: "MrDib",
  email: "mrdib@example.com",
};

// ═══════════════════════════════════════════
// Optional & Readonly Properties
// ═══════════════════════════════════════════

interface Product {
  readonly id: string; // Can't be changed
  name: string;
  price: number;
  description?: string; // Optional
  tags?: string[]; // Optional
}

const product: Product = {
  id: "prod-1",
  name: "TypeScript Guide",
  price: 29.99,
};

// product.id = "prod-2";  // ❌ Error! id is readonly

// ═══════════════════════════════════════════
// Function Types in Interfaces
// ═══════════════════════════════════════════

interface Calculator {
  add(a: number, b: number): number;
  subtract(a: number, b: number): number;
  multiply: (a: number, b: number) => number; // Alternative syntax
}

const calc: Calculator = {
  add: (a, b) => a + b,
  subtract: (a, b) => a - b,
  multiply: (a, b) => a * b,
};

// ═══════════════════════════════════════════
// Index Signatures
// ═══════════════════════════════════════════

// String index signature
interface StringDictionary {
  [key: string]: string;
}

const colors: StringDictionary = {
  primary: "#007bff",
  secondary: "#6c757d",
  success: "#28a745",
};

// Number index signature
interface NumberArray {
  [index: number]: number;
}

// Mixed with known properties
interface Config {
  host: string;
  port: number;
  [key: string]: any; // Additional properties allowed
}

// ═══════════════════════════════════════════
// Extending Interfaces
// ═══════════════════════════════════════════

interface Timestamped {
  createdAt: Date;
  updatedAt: Date;
}

interface Entity {
  id: string;
}

interface Post extends Entity, Timestamped {
  title: string;
  content: string;
  authorId: string;
}

const post: Post = {
  id: "post-1",
  title: "TypeScript Basics",
  content: "...",
  authorId: "user-1",
  createdAt: new Date(),
  updatedAt: new Date(),
};

// ═══════════════════════════════════════════
// Interface vs Type Alias
// ═══════════════════════════════════════════

// Interface (can be extended, merged)
interface Animal {
  name: string;
}

interface Animal {
  // Declaration merging
  age: number;
}

// Type alias (can't be reopened)
type Person = {
  name: string;
};

// type Person = {  // ❌ Error! Duplicate identifier
//     age: number;
// };

// When to use what?
// - Interface: For object shapes, especially when extending
// - Type: For unions, intersections, primitives, tuples
```

---

### Classes - Object-Oriented Programming 🎯

```typescript
// ═══════════════════════════════════════════
// Basic Class
// ═══════════════════════════════════════════

class User {
  name: string;
  email: string;

  constructor(name: string, email: string) {
    this.name = name;
    this.email = email;
  }

  greet(): string {
    return `Hello, I'm ${this.name}!`;
  }
}

const user = new User("MrDib", "mrdib@example.com");
console.log(user.greet());

// ═══════════════════════════════════════════
// Access Modifiers
// ═══════════════════════════════════════════

class BankAccount {
  public accountNumber: string; // Accessible everywhere (default)
  private balance: number; // Only within class
  protected transactions: string[]; // Within class and subclasses

  constructor(accountNumber: string, initialBalance: number) {
    this.accountNumber = accountNumber;
    this.balance = initialBalance;
    this.transactions = [];
  }

  public deposit(amount: number): void {
    this.balance += amount;
    this.addTransaction(`Deposit: $${amount}`);
  }

  public withdraw(amount: number): boolean {
    if (amount <= this.balance) {
      this.balance -= amount;
      this.addTransaction(`Withdrawal: $${amount}`);
      return true;
    }
    return false;
  }

  public getBalance(): number {
    return this.balance;
  }

  private addTransaction(description: string): void {
    this.transactions.push(description);
  }
}

// ═══════════════════════════════════════════
// Shorthand Properties
// ═══════════════════════════════════════════

class Person {
  // Shorthand: declare and initialize in constructor
  constructor(public name: string, public age: number, private ssn: string) {}

  introduce(): string {
    return `I'm ${this.name}, ${this.age} years old`;
  }
}

// ═══════════════════════════════════════════
// Readonly Properties
// ═══════════════════════════════════════════

class Product {
  readonly id: string;
  name: string;

  constructor(id: string, name: string) {
    this.id = id; // Can set in constructor
    this.name = name;
  }

  updateName(newName: string): void {
    this.name = newName; // ✅ OK
    // this.id = "new-id";  // ❌ Error! id is readonly
  }
}

// ═══════════════════════════════════════════
// Getters & Setters
// ═══════════════════════════════════════════

class Temperature {
  private _celsius: number = 0;

  get celsius(): number {
    return this._celsius;
  }

  set celsius(value: number) {
    if (value < -273.15) {
      throw new Error("Temperature below absolute zero!");
    }
    this._celsius = value;
  }

  get fahrenheit(): number {
    return (this._celsius * 9) / 5 + 32;
  }

  set fahrenheit(value: number) {
    this._celsius = ((value - 32) * 5) / 9;
  }
}

const temp = new Temperature();
temp.celsius = 25;
console.log(temp.fahrenheit); // 77

// ═══════════════════════════════════════════
// Static Members
// ═══════════════════════════════════════════

class MathUtils {
  static PI = 3.14159;

  static circleArea(radius: number): number {
    return this.PI * radius * radius;
  }

  static rectangleArea(width: number, height: number): number {
    return width * height;
  }
}

console.log(MathUtils.PI);
console.log(MathUtils.circleArea(5));

// ═══════════════════════════════════════════
// Inheritance
// ═══════════════════════════════════════════

class Animal {
  constructor(public name: string) {}

  makeSound(): string {
    return "Some generic sound";
  }
}

class Dog extends Animal {
  constructor(name: string, public breed: string) {
    super(name); // Call parent constructor
  }

  makeSound(): string {
    return "Woof!";
  }

  fetch(): string {
    return `${this.name} is fetching!`;
  }
}

class Cat extends Animal {
  makeSound(): string {
    return "Meow!";
  }
}

const dog = new Dog("Buddy", "Golden Retriever");
console.log(dog.makeSound()); // "Woof!"
console.log(dog.fetch());

// ═══════════════════════════════════════════
// Abstract Classes
// ═══════════════════════════════════════════

abstract class Shape {
  constructor(public color: string) {}

  abstract getArea(): number; // Must be implemented by subclasses

  describe(): string {
    return `A ${this.color} shape with area ${this.getArea()}`;
  }
}

class Circle extends Shape {
  constructor(color: string, public radius: number) {
    super(color);
  }

  getArea(): number {
    return Math.PI * this.radius ** 2;
  }
}

class Rectangle extends Shape {
  constructor(color: string, public width: number, public height: number) {
    super(color);
  }

  getArea(): number {
    return this.width * this.height;
  }
}

// const shape = new Shape("red");  // ❌ Error! Can't instantiate abstract class
const circle = new Circle("red", 5);
const rect = new Rectangle("blue", 10, 20);

// ═══════════════════════════════════════════
// Implementing Interfaces
// ═══════════════════════════════════════════

interface Printable {
  print(): void;
}

interface Saveable {
  save(): Promise<void>;
}

class Document implements Printable, Saveable {
  constructor(public content: string) {}

  print(): void {
    console.log(this.content);
  }

  async save(): Promise<void> {
    // Save to database
    console.log("Saving document...");
  }
}

// ═══════════════════════════════════════════
// Generic Classes
// ═══════════════════════════════════════════

class DataStore<T> {
  private data: T[] = [];

  add(item: T): void {
    this.data.push(item);
  }

  remove(item: T): void {
    const index = this.data.indexOf(item);
    if (index > -1) {
      this.data.splice(index, 1);
    }
  }

  getAll(): T[] {
    return [...this.data];
  }

  find(predicate: (item: T) => boolean): T | undefined {
    return this.data.find(predicate);
  }
}

const numberStore = new DataStore<number>();
numberStore.add(1);
numberStore.add(2);

const userStore = new DataStore<User>();
userStore.add({ id: "1", name: "Alice", email: "alice@example.com" });
```

> **💡 Pro Tip:** Use classes when you need object-oriented features like inheritance and encapsulation. For simple data structures, interfaces or types are often sufficient!

---

<div align="center">

## 🎨 Advanced Types

</div>

### Powerful Type Manipulation 🔮

```typescript
// ═══════════════════════════════════════════
// Mapped Types
// ═══════════════════════════════════════════

// Make all properties optional
type Partial<T> = {
  [P in keyof T]?: T[P];
};

// Make all properties required
type Required<T> = {
  [P in keyof T]-?: T[P];
};

// Make all properties readonly
type Readonly<T> = {
  readonly [P in keyof T]: T[P];
};

// Make all properties nullable
type Nullable<T> = {
  [P in keyof T]: T[P] | null;
};

// Custom mapped type
type Getters<T> = {
  [P in keyof T as `get${Capitalize<string & P>}`]: () => T[P];
};

interface Person {
  name: string;
  age: number;
}

type PersonGetters = Getters<Person>;
// {
//   getName: () => string;
//   getAge: () => number;
// }

// ═══════════════════════════════════════════
// Conditional Types
// ═══════════════════════════════════════════

// Basic conditional type
type IsString<T> = T extends string ? true : false;

type A = IsString<string>; // true
type B = IsString<number>; // false

// Exclude null and undefined
type NonNullable<T> = T extends null | undefined ? never : T;

type C = NonNullable<string | null>; // string
type D = NonNullable<number | undefined>; // number

// Extract function return type
type ReturnType<T> = T extends (...args: any[]) => infer R ? R : never;

type E = ReturnType<() => string>; // string
type F = ReturnType<(x: number) => number>; // number

// Flatten array type
type Flatten<T> = T extends Array<infer U> ? U : T;

type G = Flatten<string[]>; // string
type H = Flatten<number>; // number

// ═══════════════════════════════════════════
// Template Literal Types
// ═══════════════════════════════════════════

// Basic template literal type
type Greeting = `Hello ${string}`;

let greeting1: Greeting = "Hello World"; // ✅
let greeting2: Greeting = "Hello TypeScript"; // ✅
// let greeting3: Greeting = "Hi World";  // ❌

// With union types
type HTTPMethod = "GET" | "POST" | "PUT" | "DELETE";
type Endpoint = "/users" | "/posts";
type APIRoute = `${HTTPMethod} ${Endpoint}`;
// "GET /users" | "GET /posts" | "POST /users" | ...

// Event handlers
type EventName = "click" | "focus" | "blur";
type EventHandler = `on${Capitalize<EventName>}`;
// "onClick" | "onFocus" | "onBlur"

// CSS properties
type CSSProperty = "color" | "backgroundColor" | "fontSize";
type CSSValue = string | number;
type CSSProperties = {
  [K in CSSProperty]?: CSSValue;
};

// ═══════════════════════════════════════════
// Utility Types in Action
// ═══════════════════════════════════════════

interface User {
  id: string;
  name: string;
  email: string;
  password: string;
  role: "admin" | "user";
  createdAt: Date;
}

// Pick specific fields
type UserPublicInfo = Pick<User, "id" | "name" | "email">;

// Omit sensitive fields
type UserWithoutPassword = Omit<User, "password">;

// Make all fields optional for updates
type UserUpdate = Partial<User>;

// Make specific fields required
type UserWithEmail = Required<Pick<User, "email">> & Partial<User>;

// Record type
type UserRole = "admin" | "user" | "guest";
type RolePermissions = Record<UserRole, string[]>;

const permissions: RolePermissions = {
  admin: ["read", "write", "delete"],
  user: ["read", "write"],
  guest: ["read"],
};

// ═══════════════════════════════════════════
// Discriminated Unions (Tagged Unions)
// ═══════════════════════════════════════════

interface SuccessResponse {
  type: "success";
  data: any;
}

interface ErrorResponse {
  type: "error";
  error: string;
  code: number;
}

interface LoadingResponse {
  type: "loading";
}

type ApiResponse = SuccessResponse | ErrorResponse | LoadingResponse;

function handleResponse(response: ApiResponse) {
  switch (response.type) {
    case "success":
      console.log(response.data); // TypeScript knows it's SuccessResponse
      break;
    case "error":
      console.error(response.error, response.code); // ErrorResponse
      break;
    case "loading":
      console.log("Loading..."); // LoadingResponse
      break;
  }
}

// ═══════════════════════════════════════════
// Type Guards
// ═══════════════════════════════════════════

// typeof type guard
function padLeft(value: string, padding: string | number) {
  if (typeof padding === "number") {
    return " ".repeat(padding) + value;
  }
  if (typeof padding === "string") {
    return padding + value;
  }
}

// instanceof type guard
class Cat {
  meow() {
    console.log("Meow!");
  }
}

class Dog {
  bark() {
    console.log("Woof!");
  }
}

function makeSound(animal: Cat | Dog) {
  if (animal instanceof Cat) {
    animal.meow();
  } else {
    animal.bark();
  }
}

// Custom type guard
interface Fish {
  swim(): void;
}

interface Bird {
  fly(): void;
}

function isFish(pet: Fish | Bird): pet is Fish {
  return (pet as Fish).swim !== undefined;
}

function move(pet: Fish | Bird) {
  if (isFish(pet)) {
    pet.swim();
  } else {
    pet.fly();
  }
}

// ═══════════════════════════════════════════
// Never Type
// ═══════════════════════════════════════════

// Exhaustive checking
type Shape = Circle | Rectangle | Triangle;

function getArea(shape: Shape): number {
  switch (shape.kind) {
    case "circle":
      return Math.PI * shape.radius ** 2;
    case "rectangle":
      return shape.width * shape.height;
    case "triangle":
      return (shape.base * shape.height) / 2;
    default:
      // If we add a new shape and forget to handle it,
      // TypeScript will error here
      const _exhaustive: never = shape;
      return _exhaustive;
  }
}
```

> **💡 Pro Tip:** Advanced types are powerful but can make code harder to read. Use them when they provide real value, not just to show off TypeScript skills!

---

<div align="center">

## ⚛️ React with TypeScript

</div>

### Type-Safe React Components 🎨

```typescript
// ═══════════════════════════════════════════
// Functional Components
// ═══════════════════════════════════════════

import React, { FC, ReactNode } from "react";

// Basic component with props
interface ButtonProps {
  label: string;
  onClick: () => void;
  disabled?: boolean;
}

const Button: FC<ButtonProps> = ({ label, onClick, disabled = false }) => {
  return (
    <button onClick={onClick} disabled={disabled}>
      {label}
    </button>
  );
};

// Component with children
interface CardProps {
  title: string;
  children: ReactNode;
  className?: string;
}

const Card: FC<CardProps> = ({ title, children, className }) => {
  return (
    <div className={className}>
      <h2>{title}</h2>
      <div>{children}</div>
    </div>
  );
};

// ═══════════════════════════════════════════
// useState Hook
// ═══════════════════════════════════════════

import { useState } from "react";

function Counter() {
  // Type inferred as number
  const [count, setCount] = useState(0);

  // Explicit type
  const [name, setName] = useState<string>("");

  // Union type
  const [status, setStatus] = useState<"idle" | "loading" | "success">("idle");

  // Object state
  interface User {
    name: string;
    email: string;
  }

  const [user, setUser] = useState<User | null>(null);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}

// ═══════════════════════════════════════════
// useEffect Hook
// ═══════════════════════════════════════════

import { useEffect } from "react";

function DataFetcher() {
  const [data, setData] = useState<User[]>([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState<Error | null>(null);

  useEffect(() => {
    async function fetchData() {
      try {
        const response = await fetch("/api/users");
        const users: User[] = await response.json();
        setData(users);
      } catch (err) {
        setError(err as Error);
      } finally {
        setLoading(false);
      }
    }

    fetchData();
  }, []); // Empty dependency array

  if (loading) return <div>Loading...</div>;
  if (error) return <div>Error: {error.message}</div>;

  return (
    <ul>
      {data.map((user) => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}

// ═══════════════════════════════════════════
// useRef Hook
// ═══════════════════════════════════════════

import { useRef } from "react";

function TextInput() {
  // Ref for DOM element
  const inputRef = useRef<HTMLInputElement>(null);

  // Ref for mutable value
  const countRef = useRef<number>(0);

  const focusInput = () => {
    inputRef.current?.focus();
  };

  return (
    <div>
      <input ref={inputRef} type="text" />
      <button onClick={focusInput}>Focus Input</button>
    </div>
  );
}

// ═══════════════════════════════════════════
// Custom Hooks
// ═══════════════════════════════════════════

// Fetch hook
function useFetch<T>(url: string) {
  const [data, setData] = useState<T | null>(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState<Error | null>(null);

  useEffect(() => {
    async function fetchData() {
      try {
        const response = await fetch(url);
        const json = await response.json();
        setData(json);
      } catch (err) {
        setError(err as Error);
      } finally {
        setLoading(false);
      }
    }

    fetchData();
  }, [url]);

  return { data, loading, error };
}

// Usage
function UserList() {
  const { data: users, loading, error } = useFetch<User[]>("/api/users");

  // ... render users
}

// Local storage hook
function useLocalStorage<T>(
  key: string,
  initialValue: T
): [T, (value: T) => void] {
  const [storedValue, setStoredValue] = useState<T>(() => {
    try {
      const item = window.localStorage.getItem(key);
      return item ? JSON.parse(item) : initialValue;
    } catch (error) {
      return initialValue;
    }
  });

  const setValue = (value: T) => {
    try {
      setStoredValue(value);
      window.localStorage.setItem(key, JSON.stringify(value));
    } catch (error) {
      console.error(error);
    }
  };

  return [storedValue, setValue];
}

// ═══════════════════════════════════════════
// Event Handlers
// ═══════════════════════════════════════════

function Form() {
  const [text, setText] = useState("");

  // Input change event
  const handleChange = (e: React.ChangeEvent<HTMLInputElement>) => {
    setText(e.target.value);
  };

  // Form submit event
  const handleSubmit = (e: React.FormEvent<HTMLFormElement>) => {
    e.preventDefault();
    console.log(text);
  };

  // Button click event
  const handleClick = (e: React.MouseEvent<HTMLButtonElement>) => {
    console.log("Clicked!");
  };

  // Keyboard event
  const handleKeyDown = (e: React.KeyboardEvent<HTMLInputElement>) => {
    if (e.key === "Enter") {
      console.log("Enter pressed");
    }
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        type="text"
        value={text}
        onChange={handleChange}
        onKeyDown={handleKeyDown}
      />
      <button onClick={handleClick}>Submit</button>
    </form>
  );
}

// ═══════════════════════════════════════════
// Context API with TypeScript
// ═══════════════════════════════════════════

import { createContext, useContext } from "react";

interface AuthContextType {
  user: User | null;
  login: (email: string, password: string) => Promise<void>;
  logout: () => void;
  isAuthenticated: boolean;
}

const AuthContext = createContext<AuthContextType | undefined>(undefined);

export function AuthProvider({ children }: { children: ReactNode }) {
  const [user, setUser] = useState<User | null>(null);

  const login = async (email: string, password: string) => {
    // Login logic
    const userData = await api.login(email, password);
    setUser(userData);
  };

  const logout = () => {
    setUser(null);
  };

  const value: AuthContextType = {
    user,
    login,
    logout,
    isAuthenticated: user !== null,
  };

  return <AuthContext.Provider value={value}>{children}</AuthContext.Provider>;
}

// Custom hook for using context
export function useAuth() {
  const context = useContext(AuthContext);
  if (context === undefined) {
    throw new Error("useAuth must be used within AuthProvider");
  }
  return context;
}

// Usage
function Profile() {
  const { user, logout } = useAuth();

  return (
    <div>
      <h1>Welcome, {user?.name}</h1>
      <button onClick={logout}>Logout</button>
    </div>
  );
}

// ═══════════════════════════════════════════
// Generic Components
// ═══════════════════════════════════════════

interface ListProps<T> {
  items: T[];
  renderItem: (item: T) => ReactNode;
  keyExtractor: (item: T) => string;
}

function List<T>({ items, renderItem, keyExtractor }: ListProps<T>) {
  return (
    <ul>
      {items.map((item) => (
        <li key={keyExtractor(item)}>{renderItem(item)}</li>
      ))}
    </ul>
  );
}

// Usage
function UsersList() {
  const users: User[] = [
    /*...*/
  ];

  return (
    <List
      items={users}
      renderItem={(user) => <span>{user.name}</span>}
      keyExtractor={(user) => user.id}
    />
  );
}
```

> **💡 Pro Tip:** React and TypeScript are a perfect match! Type your props, state, and event handlers for a much better development experience with autocomplete and error checking.

---

<div align="center">

## 🌐 Node.js & Express

</div>

### Backend TypeScript 🚀

```typescript
// ═══════════════════════════════════════════
// Express with TypeScript
// ═══════════════════════════════════════════

import express, { Request, Response, NextFunction } from "express";

const app = express();

app.use(express.json());

// Basic route
app.get("/", (req: Request, res: Response) => {
  res.json({ message: "Hello, TypeScript!" });
});

// Route with params
app.get("/users/:id", (req: Request, res: Response) => {
  const { id } = req.params;
  res.json({ userId: id });
});

// Route with query params
app.get("/search", (req: Request, res: Response) => {
  const { q, page = "1" } = req.query;
  res.json({ query: q, page: parseInt(page as string) });
});

// POST route
app.post("/users", (req: Request, res: Response) => {
  const { name, email } = req.body;
  res.status(201).json({ id: "123", name, email });
});

// ═══════════════════════════════════════════
// Type-Safe Request/Response
// ═══════════════════════════════════════════

interface CreateUserRequest {
  name: string;
  email: string;
  password: string;
}

interface UserResponse {
  id: string;
  name: string;
  email: string;
  createdAt: Date;
}

app.post(
  "/users",
  (req: Request<{}, {}, CreateUserRequest>, res: Response<UserResponse>) => {
    const { name, email, password } = req.body;

    // Create user logic
    const user: UserResponse = {
      id: "123",
      name,
      email,
      createdAt: new Date(),
    };

    res.status(201).json(user);
  }
);

// ═══════════════════════════════════════════
// Custom Request Interface
// ═══════════════════════════════════════════

interface AuthRequest extends Request {
  user?: {
    id: string;
    email: string;
    role: string;
  };
}

// Middleware
const authenticate = (
  req: AuthRequest,
  res: Response,
  next: NextFunction
): void => {
  const token = req.headers.authorization?.split(" ")[1];

  if (!token) {
    res.status(401).json({ error: "No token provided" });
    return;
  }

  try {
    const decoded = verifyToken(token);
    req.user = decoded;
    next();
  } catch (error) {
    res.status(403).json({ error: "Invalid token" });
  }
};

// Using custom request
app.get("/profile", authenticate, (req: AuthRequest, res: Response) => {
  if (!req.user) {
    res.status(401).json({ error: "Not authenticated" });
    return;
  }

  res.json({ user: req.user });
});

// ═══════════════════════════════════════════
// Error Handling
// ═══════════════════════════════════════════

class AppError extends Error {
  constructor(
    public message: string,
    public statusCode: number,
    public code: string
  ) {
    super(message);
    Error.captureStackTrace(this, this.constructor);
  }
}

// Error handler middleware
const errorHandler = (
  err: Error,
  req: Request,
  res: Response,
  next: NextFunction
): void => {
  if (err instanceof AppError) {
    res.status(err.statusCode).json({
      error: {
        message: err.message,
        code: err.code,
      },
    });
  } else {
    console.error("Unexpected error:", err);
    res.status(500).json({
      error: {
        message: "Internal server error",
        code: "INTERNAL_ERROR",
      },
    });
  }
};

app.use(errorHandler);

// ═══════════════════════════════════════════
// Async Handler Wrapper
// ═══════════════════════════════════════════

type AsyncRequestHandler = (
  req: Request,
  res: Response,
  next: NextFunction
) => Promise<void>;

const asyncHandler = (fn: AsyncRequestHandler) => {
  return (req: Request, res: Response, next: NextFunction) => {
    Promise.resolve(fn(req, res, next)).catch(next);
  };
};

// Usage
app.get(
  "/users/:id",
  asyncHandler(async (req, res) => {
    const user = await getUserById(req.params.id);
    if (!user) {
      throw new AppError("User not found", 404, "USER_NOT_FOUND");
    }
    res.json(user);
  })
);

// ═══════════════════════════════════════════
// Service Layer Pattern
// ═══════════════════════════════════════════

class UserService {
  async createUser(data: CreateUserRequest): Promise<UserResponse> {
    // Validate data
    if (!this.isValidEmail(data.email)) {
      throw new AppError("Invalid email", 400, "INVALID_EMAIL");
    }

    // Create user in database
    const user = await db.users.create(data);

    return {
      id: user.id,
      name: user.name,
      email: user.email,
      createdAt: user.createdAt,
    };
  }

  async getUserById(id: string): Promise<UserResponse | null> {
    const user = await db.users.findById(id);
    if (!user) return null;

    return {
      id: user.id,
      name: user.name,
      email: user.email,
      createdAt: user.createdAt,
    };
  }

  private isValidEmail(email: string): boolean {
    return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
  }
}

// Controller
const userService = new UserService();

app.post(
  "/users",
  asyncHandler(async (req, res) => {
    const user = await userService.createUser(req.body);
    res.status(201).json(user);
  })
);

app.get(
  "/users/:id",
  asyncHandler(async (req, res) => {
    const user = await userService.getUserById(req.params.id);
    if (!user) {
      throw new AppError("User not found", 404, "USER_NOT_FOUND");
    }
    res.json(user);
  })
);
```

> **💡 Pro Tip:** Separate your business logic into service classes and keep controllers thin. Use custom request interfaces to type authentication and other middleware-added properties!

<div align="center">

## 🗄️ TypeScript with Databases

</div>

### Type-Safe Database Operations 💾

```typescript
// ═══════════════════════════════════════════
// Prisma ORM with TypeScript
// ═══════════════════════════════════════════

// Install: npm install @prisma/client
// Dev dependency: npm install -D prisma

// Initialize: npx prisma init

// schema.prisma
/*
model User {
  id        String   @id @default(uuid())
  email     String   @unique
  name      String
  posts     Post[]
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
}

model Post {
  id        String   @id @default(uuid())
  title     String
  content   String?
  published Boolean  @default(false)
  author    User     @relation(fields: [authorId], references: [id])
  authorId  String
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
}
*/

import { PrismaClient, User, Post, Prisma } from "@prisma/client";

const prisma = new PrismaClient();

// Create user
async function createUser(data: Prisma.UserCreateInput): Promise<User> {
  return prisma.user.create({
    data,
    include: {
      posts: true,
    },
  });
}

// Get user with posts
async function getUserWithPosts(
  userId: string
): Promise<(User & { posts: Post[] }) | null> {
  return prisma.user.findUnique({
    where: { id: userId },
    include: { posts: true },
  });
}

// Update user
async function updateUser(
  userId: string,
  data: Prisma.UserUpdateInput
): Promise<User> {
  return prisma.user.update({
    where: { id: userId },
    data,
  });
}

// Delete user
async function deleteUser(userId: string): Promise<User> {
  return prisma.user.delete({
    where: { id: userId },
  });
}

// Complex query
async function getPublishedPosts() {
  return prisma.post.findMany({
    where: {
      published: true,
    },
    include: {
      author: {
        select: {
          name: true,
          email: true,
        },
      },
    },
    orderBy: {
      createdAt: "desc",
    },
    take: 10,
  });
}

// ═══════════════════════════════════════════
// TypeORM with TypeScript
// ═══════════════════════════════════════════

import {
  Entity,
  PrimaryGeneratedColumn,
  Column,
  CreateDateColumn,
  UpdateDateColumn,
  ManyToOne,
  OneToMany,
} from "typeorm";

@Entity("users")
class User {
  @PrimaryGeneratedColumn("uuid")
  id!: string;

  @Column({ unique: true })
  email!: string;

  @Column()
  name!: string;

  @Column({ select: false })
  password!: string;

  @OneToMany(() => Post, (post) => post.author)
  posts!: Post[];

  @CreateDateColumn()
  createdAt!: Date;

  @UpdateDateColumn()
  updatedAt!: Date;
}

@Entity("posts")
class Post {
  @PrimaryGeneratedColumn("uuid")
  id!: string;

  @Column()
  title!: string;

  @Column("text", { nullable: true })
  content?: string;

  @Column({ default: false })
  published!: boolean;

  @ManyToOne(() => User, (user) => user.posts)
  author!: User;

  @Column()
  authorId!: string;

  @CreateDateColumn()
  createdAt!: Date;

  @UpdateDateColumn()
  updatedAt!: Date;
}

// Repository pattern
import { getRepository, Repository } from "typeorm";

class UserRepository {
  private repository: Repository<User>;

  constructor() {
    this.repository = getRepository(User);
  }

  async findById(id: string): Promise<User | undefined> {
    return this.repository.findOne({
      where: { id },
      relations: ["posts"],
    });
  }

  async create(data: Partial<User>): Promise<User> {
    const user = this.repository.create(data);
    return this.repository.save(user);
  }

  async update(id: string, data: Partial<User>): Promise<User | undefined> {
    await this.repository.update(id, data);
    return this.findById(id);
  }

  async delete(id: string): Promise<boolean> {
    const result = await this.repository.delete(id);
    return result.affected !== 0;
  }
}

// ═══════════════════════════════════════════
// MongoDB with TypeScript (Mongoose)
// ═══════════════════════════════════════════

import mongoose, { Document, Schema, Model } from "mongoose";

// Interface for document
interface IUser extends Document {
  email: string;
  name: string;
  password: string;
  posts: mongoose.Types.ObjectId[];
  createdAt: Date;
  updatedAt: Date;
}

// Schema
const userSchema = new Schema<IUser>(
  {
    email: { type: String, required: true, unique: true },
    name: { type: String, required: true },
    password: { type: String, required: true, select: false },
    posts: [{ type: Schema.Types.ObjectId, ref: "Post" }],
  },
  {
    timestamps: true,
  }
);

// Model
const User: Model<IUser> = mongoose.model<IUser>("User", userSchema);

// CRUD operations
class UserService {
  async createUser(data: {
    email: string;
    name: string;
    password: string;
  }): Promise<IUser> {
    const user = new User(data);
    return user.save();
  }

  async getUserById(id: string): Promise<IUser | null> {
    return User.findById(id).populate("posts");
  }

  async updateUser(id: string, data: Partial<IUser>): Promise<IUser | null> {
    return User.findByIdAndUpdate(id, data, { new: true });
  }

  async deleteUser(id: string): Promise<IUser | null> {
    return User.findByIdAndDelete(id);
  }

  async findByEmail(email: string): Promise<IUser | null> {
    return User.findOne({ email }).select("+password");
  }
}

// ═══════════════════════════════════════════
// SQL Query Builder (Knex.js)
// ═══════════════════════════════════════════

import knex, { Knex } from "knex";

const db: Knex = knex({
  client: "postgresql",
  connection: {
    host: "localhost",
    port: 5432,
    user: "user",
    password: "password",
    database: "mydb",
  },
});

// Type-safe queries
interface User {
  id: string;
  email: string;
  name: string;
  created_at: Date;
}

async function getUsers(): Promise<User[]> {
  return db<User>("users").select("*");
}

async function getUserById(id: string): Promise<User | undefined> {
  return db<User>("users").where({ id }).first();
}

async function createUser(
  data: Omit<User, "id" | "created_at">
): Promise<User> {
  const [user] = await db<User>("users").insert(data).returning("*");
  return user;
}

async function updateUser(id: string, data: Partial<User>): Promise<User> {
  const [user] = await db<User>("users")
    .where({ id })
    .update(data)
    .returning("*");
  return user;
}
```

> **💡 Pro Tip:** Prisma provides the best TypeScript experience with full type safety out of the box. For existing projects, TypeORM offers decorators and Active Record pattern. Choose based on your needs!

---

<div align="center">

## 🧪 Testing

</div>

### Testing TypeScript Code 🔬

```typescript
// ═══════════════════════════════════════════
// Jest with TypeScript
// ═══════════════════════════════════════════

// Install:
// npm install -D jest ts-jest @types/jest

// jest.config.js
/*
module.exports = {
  preset: 'ts-jest',
  testEnvironment: 'node',
  roots: ['<rootDir>/src'],
  testMatch: ['**/__tests__/**/*.ts', '**/?(*.)+(spec|test).ts'],
  transform: {
    '^.+\\.ts$': 'ts-jest',
  },
  collectCoverageFrom: [
    'src/**/*.ts',
    '!src/**/*.d.ts',
  ],
};
*/

// ═══════════════════════════════════════════
// Unit Tests
// ═══════════════════════════════════════════

// math.ts
export function add(a: number, b: number): number {
    return a + b;
}

export function divide(a: number, b: number): number {
    if (b === 0) {
        throw new Error('Division by zero');
    }
    return a / b;
}

// math.test.ts
import { add, divide } from './math';

describe('Math functions', () => {
    describe('add', () => {
        it('should add two positive numbers', () => {
            expect(add(2, 3)).toBe(5);
        });

        it('should add negative numbers', () => {
            expect(add(-2, -3)).toBe(-5);
        });

        it('should handle zero', () => {
            expect(add(0, 5)).toBe(5);
        });
    });

    describe('divide', () => {
        it('should divide two numbers', () => {
            expect(divide(10, 2)).toBe(5);
        });

        it('should throw error on division by zero', () => {
            expect(() => divide(10, 0)).toThrow('Division by zero');
        });
    });
});

// ═══════════════════════════════════════════
// Testing Async Code
// ═══════════════════════════════════════════

// api.ts
export async function fetchUser(id: string): Promise<User> {
    const response = await fetch(`/api/users/${id}`);
    if (!response.ok) {
        throw new Error('User not found');
    }
    return response.json();
}

// api.test.ts
import { fetchUser } from './api';

describe('fetchUser', () => {
    beforeEach(() => {
        // Mock fetch
        global.fetch = jest.fn();
    });

    afterEach(() => {
        jest.restoreAllMocks();
    });

    it('should fetch user successfully', async () => {
        const mockUser = { id: '1', name: 'MrDib', email: 'mrdib@example.com' };

        (global.fetch as jest.Mock).mockResolvedValueOnce({
            ok: true,
            json: async () => mockUser
        });

        const user = await fetchUser('1');
        expect(user).toEqual(mockUser);
        expect(fetch).toHaveBeenCalledWith('/api/users/1');
    });

    it('should throw error if user not found', async () => {
        (global.fetch as jest.Mock).mockResolvedValueOnce({
            ok: false
        });

        await expect(fetchUser('999')).rejects.toThrow('User not found');
    });
});

// ═══════════════════════════════════════════
// Testing Classes
// ═══════════════════════════════════════════

// user.service.ts
export class UserService {
    constructor(private db: Database) {}

    async createUser(data: CreateUserDto): Promise<User> {
        const existingUser = await this.db.findUserByEmail(data.email);
        if (existingUser) {
            throw new Error('User already exists');
        }
        return this.db.createUser(data);
    }

    async getUserById(id: string): Promise<User | null> {
        return this.db.findUserById(id);
    }
}

// user.service.test.ts
import { UserService } from './user.service';

describe('UserService', () => {
    let userService: UserService;
    let mockDb: jest.Mocked<Database>;

    beforeEach(() => {
        mockDb = {
            findUserByEmail: jest.fn(),
            createUser: jest.fn(),
            findUserById: jest.fn()
        } as any;

        userService = new UserService(mockDb);
    });

    describe('createUser', () => {
        it('should create new user', async () => {
            const userData = { name: 'Test', email: 'test@example.com' };
            const createdUser = { id: '1', ...userData };

            mockDb.findUserByEmail.mockResolvedValueOnce(null);
            mockDb.createUser.mockResolvedValueOnce(createdUser);

            const result = await userService.createUser(userData);

            expect(result).toEqual(createdUser);
            expect(mockDb.findUserByEmail).toHaveBeenCalledWith(userData.email);
            expect(mockDb.createUser).toHaveBeenCalledWith(userData);
        });

        it('should throw error if user exists', async () => {
            const userData = { name: 'Test', email: 'test@example.com' };
            mockDb.findUserByEmail.mockResolvedValueOnce({ id: '1' } as User);

            await expect(userService.createUser(userData))
                .rejects.toThrow('User already exists');
        });
    });
});

// ═══════════════════════════════════════════
// React Testing Library
// ═══════════════════════════════════════════

// Install: npm install -D @testing-library/react @testing-library/jest-dom

// Button.tsx
interface ButtonProps {
    label: string;
    onClick: () => void;
    disabled?: boolean;
}

export const Button: React.FC<ButtonProps> = ({ label, onClick, disabled }) => {
    return (
        <button onClick={onClick} disabled={disabled}>
            {label}
        </button>
    );
};

// Button.test.tsx
import { render, screen, fireEvent } from '@testing-library/react';
import { Button } from './Button';

describe('Button', () => {
    it('should render with label', () => {
        render(<Button label="Click me" onClick={() => {}} />);
        expect(screen.getByText('Click me')).toBeInTheDocument();
    });

    it('should call onClick when clicked', () => {
        const handleClick = jest.fn();
        render(<Button label="Click me" onClick={handleClick} />);

        fireEvent.click(screen.getByText('Click me'));
        expect(handleClick).toHaveBeenCalledTimes(1);
    });

    it('should be disabled when disabled prop is true', () => {
        render(<Button label="Click me" onClick={() => {}} disabled />);
        expect(screen.getByText('Click me')).toBeDisabled();
    });
});

// ═══════════════════════════════════════════
// Testing Hooks
// ═══════════════════════════════════════════

import { renderHook, act } from '@testing-library/react';

// useCounter.ts
export function useCounter(initialValue = 0) {
    const [count, setCount] = useState(initialValue);

    const increment = () => setCount(c => c + 1);
    const decrement = () => setCount(c => c - 1);
    const reset = () => setCount(initialValue);

    return { count, increment, decrement, reset };
}

// useCounter.test.ts
describe('useCounter', () => {
    it('should initialize with default value', () => {
        const { result } = renderHook(() => useCounter());
        expect(result.current.count).toBe(0);
    });

    it('should increment counter', () => {
        const { result } = renderHook(() => useCounter());

        act(() => {
            result.current.increment();
        });

        expect(result.current.count).toBe(1);
    });

    it('should reset counter', () => {
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
});
```

> **💡 Pro Tip:** Write tests as you code! TypeScript catches type errors, but tests catch logic errors. Aim for high coverage on critical business logic.

---

<div align="center">

## 🎯 Common Patterns

</div>

### Production-Ready TypeScript Patterns 📐

```typescript
// ═══════════════════════════════════════════
// Repository Pattern
// ═══════════════════════════════════════════

interface Repository<T> {
  findById(id: string): Promise<T | null>;
  findAll(): Promise<T[]>;
  create(data: Omit<T, "id">): Promise<T>;
  update(id: string, data: Partial<T>): Promise<T>;
  delete(id: string): Promise<boolean>;
}

class UserRepository implements Repository<User> {
  constructor(private db: Database) {}

  async findById(id: string): Promise<User | null> {
    return this.db.users.findUnique({ where: { id } });
  }

  async findAll(): Promise<User[]> {
    return this.db.users.findMany();
  }

  async create(data: Omit<User, "id">): Promise<User> {
    return this.db.users.create({ data });
  }

  async update(id: string, data: Partial<User>): Promise<User> {
    return this.db.users.update({ where: { id }, data });
  }

  async delete(id: string): Promise<boolean> {
    await this.db.users.delete({ where: { id } });
    return true;
  }
}

// ═══════════════════════════════════════════
// Factory Pattern
// ═══════════════════════════════════════════

interface Notification {
  send(to: string, message: string): Promise<void>;
}

class EmailNotification implements Notification {
  async send(to: string, message: string): Promise<void> {
    console.log(`Sending email to ${to}: ${message}`);
  }
}

class SMSNotification implements Notification {
  async send(to: string, message: string): Promise<void> {
    console.log(`Sending SMS to ${to}: ${message}`);
  }
}

class PushNotification implements Notification {
  async send(to: string, message: string): Promise<void> {
    console.log(`Sending push to ${to}: ${message}`);
  }
}

type NotificationType = "email" | "sms" | "push";

class NotificationFactory {
  static create(type: NotificationType): Notification {
    switch (type) {
      case "email":
        return new EmailNotification();
      case "sms":
        return new SMSNotification();
      case "push":
        return new PushNotification();
    }
  }
}

// Usage
const notification = NotificationFactory.create("email");
await notification.send("user@example.com", "Hello!");

// ═══════════════════════════════════════════
// Singleton Pattern
// ═══════════════════════════════════════════

class Database {
  private static instance: Database;
  private connection: any;

  private constructor() {
    // Initialize database connection
    this.connection = null;
  }

  public static getInstance(): Database {
    if (!Database.instance) {
      Database.instance = new Database();
    }
    return Database.instance;
  }

  public getConnection() {
    return this.connection;
  }
}

// Usage
const db1 = Database.getInstance();
const db2 = Database.getInstance();
console.log(db1 === db2); // true

// ═══════════════════════════════════════════
// Observer Pattern
// ═══════════════════════════════════════════

interface Observer<T> {
  update(data: T): void;
}

class Subject<T> {
  private observers: Observer<T>[] = [];

  subscribe(observer: Observer<T>): void {
    this.observers.push(observer);
  }

  unsubscribe(observer: Observer<T>): void {
    const index = this.observers.indexOf(observer);
    if (index > -1) {
      this.observers.splice(index, 1);
    }
  }

  notify(data: T): void {
    this.observers.forEach((observer) => observer.update(data));
  }
}

// Usage
interface UserEvent {
  type: "created" | "updated" | "deleted";
  userId: string;
}

class EmailObserver implements Observer<UserEvent> {
  update(event: UserEvent): void {
    console.log(`Sending email for ${event.type} event`);
  }
}

class LogObserver implements Observer<UserEvent> {
  update(event: UserEvent): void {
    console.log(`Logging ${event.type} event for user ${event.userId}`);
  }
}

const userEvents = new Subject<UserEvent>();
userEvents.subscribe(new EmailObserver());
userEvents.subscribe(new LogObserver());

userEvents.notify({ type: "created", userId: "123" });

// ═══════════════════════════════════════════
// Builder Pattern
// ═══════════════════════════════════════════

class QueryBuilder {
  private query: string = "";
  private params: any[] = [];

  select(...columns: string[]): this {
    this.query += `SELECT ${columns.join(", ")} `;
    return this;
  }

  from(table: string): this {
    this.query += `FROM ${table} `;
    return this;
  }

  where(condition: string, ...values: any[]): this {
    this.query += `WHERE ${condition} `;
    this.params.push(...values);
    return this;
  }

  orderBy(column: string, direction: "ASC" | "DESC" = "ASC"): this {
    this.query += `ORDER BY ${column} ${direction} `;
    return this;
  }

  limit(count: number): this {
    this.query += `LIMIT ${count} `;
    return this;
  }

  build(): { query: string; params: any[] } {
    return {
      query: this.query.trim(),
      params: this.params,
    };
  }
}

// Usage
const { query, params } = new QueryBuilder()
  .select("id", "name", "email")
  .from("users")
  .where("age > ?", 18)
  .orderBy("created_at", "DESC")
  .limit(10)
  .build();

// ═══════════════════════════════════════════
// Dependency Injection
// ═══════════════════════════════════════════

interface Logger {
  log(message: string): void;
  error(message: string): void;
}

class ConsoleLogger implements Logger {
  log(message: string): void {
    console.log(message);
  }

  error(message: string): void {
    console.error(message);
  }
}

class UserService {
  constructor(private repository: UserRepository, private logger: Logger) {}

  async createUser(data: CreateUserDto): Promise<User> {
    try {
      this.logger.log(`Creating user: ${data.email}`);
      const user = await this.repository.create(data);
      this.logger.log(`User created: ${user.id}`);
      return user;
    } catch (error) {
      this.logger.error(`Failed to create user: ${error}`);
      throw error;
    }
  }
}

// Usage with DI
const logger = new ConsoleLogger();
const repository = new UserRepository(db);
const userService = new UserService(repository, logger);

// ═══════════════════════════════════════════
// Result/Either Pattern
// ═══════════════════════════════════════════

type Success<T> = { success: true; data: T };
type Failure<E> = { success: false; error: E };
type Result<T, E = Error> = Success<T> | Failure<E>;

function ok<T>(data: T): Success<T> {
  return { success: true, data };
}

function err<E>(error: E): Failure<E> {
  return { success: false, error };
}

// Usage
async function getUserByEmail(email: string): Promise<Result<User, string>> {
  try {
    const user = await db.findUserByEmail(email);
    if (!user) {
      return err("User not found");
    }
    return ok(user);
  } catch (error) {
    return err("Database error");
  }
}

// Consuming the result
const result = await getUserByEmail("user@example.com");

if (result.success) {
  console.log("User:", result.data);
} else {
  console.error("Error:", result.error);
}
```

> **💡 Pro Tip:** Design patterns solve common problems elegantly. Don't force patterns where they're not needed - use them when they genuinely improve code organization and maintainability!

---

<div align="center">

## 💡 Best Practices

</div>

### TypeScript Best Practices & Configuration ⭐

```typescript
// ═══════════════════════════════════════════
// tsconfig.json - Strict Configuration
// ═══════════════════════════════════════════

{
  "compilerOptions": {
    // Type Checking
    "strict": true,                           // Enable all strict checks
    "noImplicitAny": true,                    // Error on implied 'any'
    "strictNullChecks": true,                 // Null checking
    "strictFunctionTypes": true,              // Function type checking
    "strictBindCallApply": true,              // Strict bind/call/apply
    "strictPropertyInitialization": true,     // Property initialization
    "noImplicitThis": true,                   // Error on implied 'this'
    "alwaysStrict": true,                     // Use strict mode

    // Additional Checks
    "noUnusedLocals": true,                   // Error on unused locals
    "noUnusedParameters": true,               // Error on unused parameters
    "noImplicitReturns": true,                // Implicit returns
    "noFallthroughCasesInSwitch": true,      // Switch fallthrough
    "noUncheckedIndexedAccess": true,         // Index signature checks

    // Module Resolution
    "module": "ESNext",                       // Module system
    "moduleResolution": "bundler",            // Module resolution
    "esModuleInterop": true,                  // ES module interop
    "allowSyntheticDefaultImports": true,     // Default imports
    "resolveJsonModule": true,                // Import JSON

    // Emit
    "target": "ES2022",                       // Target version
    "lib": ["ES2022", "DOM"],                 // Libraries
    "outDir": "./dist",                       // Output directory
    "sourceMap": true,                        // Source maps
    "declaration": true,                      // Type declarations
    "removeComments": true,                   // Remove comments

    // Other
    "skipLibCheck": true,                     // Skip lib checking
    "forceConsistentCasingInFileNames": true, // Consistent casing

    // Path Mapping
    "baseUrl": ".",
    "paths": {
      "@/*": ["src/*"],
      "@components/*": ["src/components/*"],
      "@utils/*": ["src/utils/*"]
    }
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules", "dist", "**/*.test.ts"]
}

// ═══════════════════════════════════════════
// Naming Conventions
// ═══════════════════════════════════════════

// ✅ Interfaces: PascalCase
interface User {}
interface UserResponse {}

// ✅ Types: PascalCase
type Status = 'active' | 'inactive';
type UserRole = 'admin' | 'user';

// ✅ Classes: PascalCase
class UserService {}
class DatabaseConnection {}

// ✅ Functions: camelCase
function getUserById(id: string) {}
const calculateTotal = () => {};

// ✅ Variables: camelCase
const userName = "MrDib";
let isActive = true;

// ✅ Constants: SCREAMING_SNAKE_CASE
const MAX_RETRIES = 3;
const API_BASE_URL = "https://api.example.com";

// ✅ Enums: PascalCase (keys and name)
enum UserRole {
    Admin = 'ADMIN',
    User = 'USER',
    Guest = 'GUEST'
}

// ✅ Generic Type Parameters: Single letter or descriptive
function identity<T>(arg: T): T {}
function map<TInput, TOutput>(items: TInput[]): TOutput[] {}

// ═══════════════════════════════════════════
// Type vs Interface
// ═══════════════════════════════════════════

// ✅ Use Interface for object shapes
interface User {
    id: string;
    name: string;
}

// ✅ Use Type for unions, intersections, primitives
type Status = 'pending' | 'approved' | 'rejected';
type ID = string | number;
type Point = { x: number; y: number };

// ✅ Interfaces can be extended
interface Admin extends User {
    permissions: string[];
}

// ✅ Types can use unions/intersections
type UserWithTimestamps = User & Timestamps;

// ═══════════════════════════════════════════
// Avoid 'any' - Use Better Alternatives
// ═══════════════════════════════════════════

// ❌ Bad: Using any
function processData(data: any) {
    return data.value;
}

// ✅ Good: Use unknown and type guard
function processData(data: unknown) {
    if (isValidData(data)) {
        return data.value;
    }
    throw new Error('Invalid data');
}

function isValidData(data: unknown): data is { value: string } {
    return typeof data === 'object' &&
           data !== null &&
           'value' in data;
}

// ✅ Good: Use generics
function processData<T extends { value: string }>(data: T) {
    return data.value;
}

// ═══════════════════════════════════════════
// Null Safety
// ═══════════════════════════════════════════

// ✅ Use optional chaining
const userName = user?.profile?.name;

// ✅ Use nullish coalescing
const port = config.port ?? 3000;

// ✅ Non-null assertion (use carefully!)
const value = getValue()!;  // Only if 100% sure it's not null

// ✅ Type guards
if (user !== null && user !== undefined) {
    console.log(user.name);
}

// ═══════════════════════════════════════════
// Function Best Practices
// ═══════════════════════════════════════════

// ✅ Explicit return types
function getUser(id: string): Promise<User | null> {
    return db.users.findUnique({ where: { id } });
}

// ✅ Avoid overusing optional parameters
// ❌ Bad
function create(a?: string, b?: number, c?: boolean) {}

// ✅ Good: Use options object
interface CreateOptions {
    name?: string;
    age?: number;
    active?: boolean;
}
function create(options: CreateOptions) {}

// ✅ Use readonly for immutable data
interface Config {
    readonly apiKey: string;
    readonly baseUrl: string;
}

// ═══════════════════════════════════════════
// Error Handling
// ═══════════════════════════════════════════

// ✅ Custom error classes
class ValidationError extends Error {
    constructor(public field: string, message: string) {
        super(message);
        this.name = 'ValidationError';
    }
}

// ✅ Type error responses
type ErrorResponse = {
    error: {
        message: string;
        code: string;
        field?: string;
    };
};

// ✅ Use Result type for predictable errors
type Result<T, E = Error> =
    | { success: true; data: T }
    | { success: false; error: E };

// ═══════════════════════════════════════════
// Import/Export Organization
// ═══════════════════════════════════════════

// ✅ Named exports (preferred)
export function getUserById(id: string) {}
export class UserService {}
export interface User {}

// ✅ Barrel exports (index.ts)
export * from './user';
export * from './post';
export { specific } from './utils';

// ❌ Avoid default exports (makes refactoring harder)
export default function() {}  // Hard to find usages

// ═══════════════════════════════════════════
// Project Structure
// ═══════════════════════════════════════════

/*
src/
├── index.ts                 # Entry point
├── types/                   # Shared types
│   ├── index.ts
│   ├── user.types.ts
│   └── api.types.ts
├── models/                  # Database models
│   ├── user.model.ts
│   └── post.model.ts
├── services/                # Business logic
│   ├── user.service.ts
│   └── post.service.ts
├── controllers/             # HTTP handlers
│   ├── user.controller.ts
│   └── post.controller.ts
├── middlewares/             # Express middleware
│   ├── auth.middleware.ts
│   └── error.middleware.ts
├── utils/                   # Utility functions
│   ├── validation.ts
│   └── helpers.ts
├── config/                  # Configuration
│   └── database.ts
└── __tests__/               # Tests
    ├── unit/
    └── integration/
*/
```

> **💡 Pro Tip:** Enable strict mode in tsconfig.json from day one! It catches more errors and forces you to write better code. Use ESLint with TypeScript for even better code quality!

---

<div align="center">

## 🎓 TypeScript Resources & Tools

### _Level up your TypeScript game!_ 📚

</div>

### Essential Tools 🛠️

```bash
# ═══════════════════════════════════════════
# Development Tools
# ═══════════════════════════════════════════

# TypeScript compiler
npm install -D typescript

# ts-node (run TS directly)
npm install -D ts-node

# nodemon (auto-restart)
npm install -D nodemon

# ESLint for TypeScript
npm install -D eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin

# Prettier (code formatter)
npm install -D prettier

# Type checking in CI/CD
tsc --noEmit

# ═══════════════════════════════════════════
# Type Definitions
# ═══════════════════════════════════════════

# Node.js types
npm install -D @types/node

# Express types
npm install -D @types/express

# React types
npm install -D @types/react @types/react-dom

# Jest types
npm install -D @types/jest

# Search for types
npx typesync
```

---

### Learning Resources 📖

```
📘 Official Resources
   - TypeScript Handbook: https://www.typescriptlang.org/docs/
   - TypeScript Playground: https://www.typescriptlang.org/play
   - TypeScript Deep Dive: https://basarat.gitbook.io/typescript/

📗 Courses & Tutorials
   - Total TypeScript (Matt Pocock)
   - TypeScript Course (freeCodeCamp)
   - Execute Program TypeScript

📙 Books
   - "Programming TypeScript" by Boris Cherny
   - "Effective TypeScript" by Dan Vanderkam
   - "TypeScript Quickly" by Yakov Fain & Anton Moiseev

🎥 Video Resources
   - Matt Pocock (YouTube) - TypeScript wizard
   - Ben Awad (YouTube) - Real-world examples
   - Jack Herrington (YouTube) - Advanced patterns

🏋️ Practice
   - Type Challenges: https://github.com/type-challenges/type-challenges
   - Exercism TypeScript Track
   - TypeScript exercises: https://typescript-exercises.github.io/

🌐 Community
   - r/typescript (Reddit)
   - TypeScript Discord
   - TypeScript GitHub Discussions

📦 Essential Libraries
   - Zod - Schema validation
   - Prisma - Type-safe ORM
   - tRPC - End-to-end type safety
   - TypeORM - TypeScript ORM
   - class-validator - Validation decorators
```

---

<div align="center">

## 🏆 You've Mastered TypeScript!

### _From JavaScript to type-safe superhero_ 🎉

</div>

**You now know:**

- ✅ TypeScript fundamentals & syntax
- ✅ Type system & type annotations
- ✅ Functions & generics
- ✅ Interfaces & classes
- ✅ Advanced types & utility types
- ✅ React with TypeScript
- ✅ Node.js & Express with types
- ✅ Database operations
- ✅ Testing strategies
- ✅ Common design patterns
- ✅ Best practices & configuration

---

<div align="center">

### The TypeScript Philosophy 🔷

> **"JavaScript that scales"**

> **"Catch errors before runtime"**

> **"Autocomplete is a superpower"**

> **"Types are documentation that never lies"**

> **"Refactor with confidence"**

</div>

---

### Quick Reference Card 📇

```typescript
// Variables
let name: string = "value";
const age: number = 25;

// Functions
function add(a: number, b: number): number {
    return a + b;
}

// Arrow functions
const multiply = (a: number, b: number): number => a * b;

// Interfaces
interface User {
    id: string;
    name: string;
    email?: string;  // Optional
}

// Type aliases
type Status = "active" | "inactive";

// Generics
function identity<T>(arg: T): T {
    return arg;
}

// Utility types
type Partial<T>    // All properties optional
type Required<T>   // All properties required
type Readonly<T>   // All properties readonly
type Pick<T, K>    // Select properties
type Omit<T, K>    // Remove properties
type Record<K, T>  // Object type

// Union types
let value: string | number;

// Type guards
if (typeof value === "string") {
    value.toUpperCase();
}

// Async/await
async function fetchData(): Promise<Data> {
    const response = await fetch(url);
    return response.json();
}
```

---

<div align="center">

### Common Commands 📋

```bash
# Compile TypeScript
tsc

# Watch mode
tsc --watch

# Run TypeScript directly
ts-node src/index.ts

# Type check only
tsc --noEmit

# Generate declaration files
tsc --declaration

# Initialize project
tsc --init
```

</div>

---

<div align="center">

## 🚀 Next Steps

### _Continue Your TypeScript Journey_ 🌟

</div>

**Level Up:**

1. 🏗️ Build a full-stack TypeScript project
2. 📖 Master advanced types and utility types
3. 🎯 Learn tRPC for end-to-end type safety
4. 🔍 Explore Zod for runtime validation
5. 🌐 Master Prisma for database operations
6. 📱 Build a TypeScript mobile app
7. 🎮 Try TypeScript with game development
8. 🤝 Contribute to TypeScript open source
9. 📝 Write technical blog posts
10. 🎤 Share your knowledge with others

---

<div align="center">

### Project Ideas 💡

```
🌐 Web Application
   - Full-stack CRUD app with React + Express
   - Real-time chat with Socket.io
   - E-commerce platform with Next.js

🛠️ CLI Tool
   - Code generator
   - File processor
   - Development automation tool

📦 NPM Package
   - Utility library
   - React component library
   - TypeScript plugin

🎮 Game Development
   - Browser game with Phaser.js
   - Text adventure game
   - Puzzle game

🤖 API Development
   - GraphQL server
   - REST API with validation
   - Microservices architecture
```

</div>

---

<div align="center">

## 🎯 Final Tips for Success

</div>

1. **Enable strict mode** - Start strict from day one
2. **Avoid 'any'** - Use 'unknown' or proper types
3. **Use type guards** - Make TypeScript understand your code
4. **Leverage generics** - Write reusable, type-safe code
5. **Type your errors** - Don't just catch Error
6. **Document with types** - Types are living documentation
7. **Use ESLint** - Catch more issues automatically
8. **Learn utility types** - They're incredibly powerful
9. **Practice type challenges** - Sharpen your skills
10. **Share your knowledge** - Teach others what you learn

---

<div align="center">

## 🔷 Why TypeScript?

</div>

### The Developer Experience Revolution 🚀

**Before TypeScript:**

- ❌ Runtime errors
- ❌ No autocomplete
- ❌ Difficult refactoring
- ❌ Documentation gets outdated
- ❌ Harder to onboard new developers

**After TypeScript:**

- ✅ Catch errors at compile time
- ✅ Amazing autocomplete & IntelliSense
- ✅ Refactor with confidence
- ✅ Types are always up-to-date
- ✅ Easier to understand codebase

### Real-World Adoption 🌍

- **Microsoft** - Created TypeScript
- **Google** - Uses TypeScript extensively
- **Airbnb** - Switched to TypeScript
- **Slack** - Rewrote in TypeScript
- **Shopify** - TypeScript for scale
- **Meta** - Increasing TypeScript usage

---

<div align="center">

**Built with 🔷 by MrDib, for TypeScript Developers**

_"TypeScript: JavaScript with guardrails that make you go faster"_

**Happy Coding, TypeScript Developer!** 🚀

**If you found this helpful, give it a ⭐ star and share with fellow developers!**

</div>

---

### Contributing 🤝

Found a mistake? Want to add something? Contributions are welcome!

1. Fork the repository
2. Create your feature branch
3. Make your changes
4. Submit a pull request

---

### License 📄

This guide is open source and available under the MIT License.

---

<div align="center">

**Stay curious. Keep coding. Embrace the types!** ⚡

🔷 **#TypeScript** 🔷 **#DevResourceVault** 🔷 **#MrDib** 🔷

### Remember

> _"Types don't slow you down. They make you faster."_

> _"The compiler is your friend, not your enemy."_

> _"If it compiles, there's a good chance it works."_

</div>

---

<div align="center">

**Now go forth and build type-safe, scalable applications!** 🔥

</div>
