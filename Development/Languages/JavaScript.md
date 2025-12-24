<div align="center">

# 🟨 JavaScript - The Language of the Web

### _From ES6 to ES2024 and beyond_ 🚀

![JavaScript](https://img.shields.io/badge/JavaScript-ES2024-yellow?style=for-the-badge&logo=javascript)
![Node.js](https://img.shields.io/badge/Node.js-20+-green?style=for-the-badge&logo=node.js)
![Usage](https://img.shields.io/badge/Usage-Everywhere-orange?style=for-the-badge)

</div>

---

## 📚 Table of Contents

- [🎯 JavaScript Fundamentals](#-javascript-fundamentals)
- [📊 Data Types & Structures](#-data-types--structures)
- [🔄 Control Flow](#-control-flow)
- [🔧 Functions](#-functions)
- [🏗️ Object-Oriented Programming](#️-object-oriented-programming)
- [⚡ Async JavaScript](#-async-javascript)
- [🎨 Modern ES Features](#-modern-es-features)
- [🎯 Design Patterns](#-design-patterns)
- [⚙️ Performance Optimization](#️-performance-optimization)
- [🌐 Web APIs](#-web-apis)
- [🛠️ Working with DOM](#️-working-with-dom)
- [🔒 Error Handling](#-error-handling)
- [🧪 Testing](#-testing)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 🎯 JavaScript Fundamentals

</div>

### Getting Started 🚀

```bash
# ═══════════════════════════════════════════
# Running JavaScript
# ═══════════════════════════════════════════

# Node.js REPL (Interactive mode)
node

# Run JavaScript file
node script.js

# Run with arguments
node script.js arg1 arg2

# Execute one-liner
node -e "console.log('Hello, World!')"

# Start with ES modules
node --experimental-modules script.mjs

# Enable watch mode (Node.js 18+)
node --watch script.js

# ═══════════════════════════════════════════
# Browser Console
# ═══════════════════════════════════════════

# Open Developer Console:
# Chrome/Edge: Cmd+Option+J (Mac) / Ctrl+Shift+J (Windows)
# Firefox: Cmd+Option+K (Mac) / Ctrl+Shift+K (Windows)
# Safari: Cmd+Option+C (Mac)
```

---

### Variables & Data Types 📝

```javascript
// ═══════════════════════════════════════════
// Variable Declarations
// ═══════════════════════════════════════════

// const - Cannot be reassigned (use by default)
const name = "MrDib";
const age = 25;
const PI = 3.14159;

// let - Can be reassigned (use when needed)
let counter = 0;
counter = 1; // ✅ OK

// var - Old way (avoid in modern JavaScript!)
var oldSchool = "don't use this";

// ═══════════════════════════════════════════
// Primitive Data Types
// ═══════════════════════════════════════════

// String
const firstName = "John";
const lastName = "Doe";
const template = `Hello, ${firstName}!`;

// Number (no separate int/float)
const integer = 42;
const float = 3.14;
const negative = -10;
const scientific = 1.5e6; // 1,500,000
const infinity = Infinity;
const notANumber = NaN;

// BigInt (for very large integers)
const bigNumber = 9007199254740991n;
const anotherBig = BigInt("9007199254740991");

// Boolean
const isActive = true;
const isCompleted = false;

// Undefined (declared but not assigned)
let notDefined;
console.log(notDefined); // undefined

// Null (intentional absence of value)
const empty = null;

// Symbol (unique identifier)
const id = Symbol("id");
const anotherId = Symbol("id");
console.log(id === anotherId); // false

// ═══════════════════════════════════════════
// Type Checking
// ═══════════════════════════════════════════

typeof "hello"; // "string"
typeof 42; // "number"
typeof true; // "boolean"
typeof undefined; // "undefined"
typeof null; // "object" (historical bug!)
typeof Symbol(); // "symbol"
typeof 123n; // "bigint"
typeof {}; // "object"
typeof []; // "object" (arrays are objects)
typeof function () {}; // "function"

// Better array check
Array.isArray([]); // true
Array.isArray({}); // false

// ═══════════════════════════════════════════
// Type Conversion
// ═══════════════════════════════════════════

// To String
String(123)(
  // "123"
  123
).toString(); // "123"
123 + ""; // "123"

// To Number
Number("123"); // 123
parseInt("123"); // 123
parseFloat("123.45") + // 123.45
  "123"; // 123 (unary plus)

// To Boolean
Boolean(1); // true
Boolean(0); // false
Boolean(""); // false
Boolean("text"); // true
!!"text"; // true (double negation)

// ═══════════════════════════════════════════
// Falsy Values (everything else is truthy!)
// ═══════════════════════════════════════════

false;
0 - 0;
0n;
("");
null;
undefined;
NaN;

// ═══════════════════════════════════════════
// String Operations
// ═══════════════════════════════════════════

const text = "JavaScript";

// Access characters
text[0]; // "J"
text.charAt(0); // "J"
text.at(-1); // "t" (last character, ES2022)

// String properties
text.length; // 10

// String methods
text.toUpperCase(); // "JAVASCRIPT"
text.toLowerCase(); // "javascript"
text.slice(0, 4); // "Java"
text.substring(0, 4); // "Java"
text.substr(0, 4); // "Java" (deprecated)
text.split(""); // ["J", "a", "v", "a", ...]
text.includes("Script"); // true
text.startsWith("Java"); // true
text.endsWith("Script"); // true
text.indexOf("Script"); // 4
text.lastIndexOf("a"); // 3
text.repeat(3); // "JavaScriptJavaScriptJavaScript"
text.trim(); // Remove whitespace
text.trimStart(); // Remove leading whitespace
text.trimEnd(); // Remove trailing whitespace
text.padStart(15, "*"); // "*****JavaScript"
text.padEnd(15, "*"); // "JavaScript*****"
text.replace("Java", "Type"); // "TypeScript"
text.replaceAll("a", "@"); // "J@v@Script"

// Template Literals (ES6)
const name = "MrDib";
const age = 25;
const message = `Hello, I'm ${name} and I'm ${age} years old.`;

// Multi-line strings
const multiline = `
  Line 1
  Line 2
  Line 3
`;

// Tagged templates
function highlight(strings, ...values) {
  return strings.reduce((result, str, i) => {
    return result + str + (values[i] ? `<mark>${values[i]}</mark>` : "");
  }, "");
}

const highlighted = highlight`Name: ${name}, Age: ${age}`;
// "Name: <mark>MrDib</mark>, Age: <mark>25</mark>"

// ═══════════════════════════════════════════
// Number Operations
// ═══════════════════════════════════════════

// Arithmetic
1 + 2; // 3
5 - 3; // 2
4 * 3; // 12
10 / 2; // 5
10 % 3; // 1 (remainder)
2 ** 3; // 8 (exponentiation)

// Math object
Math.round(4.7); // 5
Math.ceil(4.1); // 5
Math.floor(4.9); // 4
Math.trunc(4.9); // 4 (removes decimal)
Math.abs(-5); // 5
Math.min(1, 2, 3); // 1
Math.max(1, 2, 3); // 3
Math.random(); // Random between 0 and 1
Math.pow(2, 3); // 8
Math.sqrt(16); // 4
Math.cbrt(27); // 3 (cube root)
Math.sign(-5); // -1
Math.PI; // 3.141592653589793

// Random integer between min and max
const randomInt = (min, max) =>
  Math.floor(Math.random() * (max - min + 1)) + min;

randomInt(1, 10); // Random number 1-10

// Number methods
(123.456)
  .toFixed(2)(
    // "123.46"
    123.456
  )
  .toPrecision(4)(
    // "123.5"
    123
  )
  .toString(2); // "1111011" (binary)
Number.isInteger(123); // true
Number.isNaN(NaN); // true
Number.isFinite(123); // true
Number.parseInt("123"); // 123
Number.parseFloat("123.45"); // 123.45

// Number separators (ES2021)
const billion = 1_000_000_000;
const hex = 0xff_ff_ff;

// ═══════════════════════════════════════════
// Console Methods
// ═══════════════════════════════════════════

console.log("Normal message");
console.error("Error message");
console.warn("Warning message");
console.info("Info message");
console.debug("Debug message");
console.table([
  { name: "Alice", age: 25 },
  { name: "Bob", age: 30 },
]);
console.group("Group");
console.log("Inside group");
console.groupEnd();
console.time("timer");
// ... some code ...
console.timeEnd("timer");
console.assert(1 === 2, "This will show because assertion failed");
console.clear(); // Clear console
```

> **💡 Pro Tip:** Use `const` by default, only use `let` when you need to reassign. Never use `var` in modern JavaScript!

---

<div align="center">

## 📊 Data Types & Structures

</div>

### Arrays 📦

```javascript
// ═══════════════════════════════════════════
// Creating Arrays
// ═══════════════════════════════════════════

const fruits = ["apple", "banana", "cherry"];
const numbers = [1, 2, 3, 4, 5];
const mixed = [1, "hello", true, null, { name: "MrDib" }];
const empty = [];
const withNew = new Array(3); // [undefined, undefined, undefined]
const range = Array.from({ length: 5 }, (_, i) => i); // [0, 1, 2, 3, 4]

// Array.of vs Array constructor
Array.of(3); // [3]
Array(3); // [undefined, undefined, undefined]

// ═══════════════════════════════════════════
// Accessing Elements
// ═══════════════════════════════════════════

fruits[0]; // "apple" (first)
fruits[fruits.length - 1]; // "cherry" (last)
fruits.at(-1); // "cherry" (ES2022 - negative indexing)
fruits.at(0); // "apple"

// ═══════════════════════════════════════════
// Array Properties & Basic Methods
// ═══════════════════════════════════════════

fruits.length; // 3

// Add/remove elements
fruits.push("grape"); // Add to end, returns new length
fruits.pop(); // Remove from end, returns removed element
fruits.unshift("mango"); // Add to beginning
fruits.shift(); // Remove from beginning

// Add/remove at specific position
fruits.splice(1, 1); // Remove 1 element at index 1
fruits.splice(1, 0, "kiwi"); // Insert at index 1
fruits.splice(1, 1, "melon"); // Replace 1 element at index 1

// ═══════════════════════════════════════════
// Iterating Arrays
// ═══════════════════════════════════════════

const numbers = [1, 2, 3, 4, 5];

// for loop
for (let i = 0; i < numbers.length; i++) {
  console.log(numbers[i]);
}

// for...of (modern way)
for (const num of numbers) {
  console.log(num);
}

// forEach
numbers.forEach((num, index, array) => {
  console.log(`${index}: ${num}`);
});

// for...in (for indices, not recommended for arrays)
for (const index in numbers) {
  console.log(numbers[index]);
}

// ═══════════════════════════════════════════
// Array Methods - Map, Filter, Reduce
// ═══════════════════════════════════════════

const numbers = [1, 2, 3, 4, 5];

// map - Transform each element
const doubled = numbers.map((n) => n * 2);
// [2, 4, 6, 8, 10]

const squares = numbers.map((n) => n ** 2);
// [1, 4, 9, 16, 25]

// filter - Keep elements that match condition
const evens = numbers.filter((n) => n % 2 === 0);
// [2, 4]

const greaterThan2 = numbers.filter((n) => n > 2);
// [3, 4, 5]

// reduce - Reduce to single value
const sum = numbers.reduce((acc, n) => acc + n, 0);
// 15

const product = numbers.reduce((acc, n) => acc * n, 1);
// 120

// Chaining methods
const result = numbers
  .filter((n) => n % 2 === 0)
  .map((n) => n ** 2)
  .reduce((acc, n) => acc + n, 0);
// 20 (2² + 4² = 4 + 16)

// ═══════════════════════════════════════════
// Array Search Methods
// ═══════════════════════════════════════════

const numbers = [1, 2, 3, 4, 5, 3];

// find - First element matching condition
numbers.find((n) => n > 3); // 4
numbers.find((n) => n > 10); // undefined

// findIndex - Index of first match
numbers.findIndex((n) => n > 3); // 3
numbers.findIndex((n) => n > 10); // -1

// findLast - Last element matching (ES2023)
numbers.findLast((n) => n === 3); // 3 (last occurrence)

// findLastIndex - Index of last match (ES2023)
numbers.findLastIndex((n) => n === 3); // 5

// indexOf - First index of value
numbers.indexOf(3); // 2
numbers.indexOf(10); // -1

// lastIndexOf - Last index of value
numbers.lastIndexOf(3); // 5

// includes - Check if value exists
numbers.includes(3); // true
numbers.includes(10); // false

// some - Check if any element matches
numbers.some((n) => n > 4); // true
numbers.some((n) => n > 10); // false

// every - Check if all elements match
numbers.every((n) => n > 0); // true
numbers.every((n) => n > 2); // false

// ═══════════════════════════════════════════
// Array Transformation
// ═══════════════════════════════════════════

const fruits = ["apple", "banana", "cherry"];
const numbers = [3, 1, 4, 1, 5];

// join - Convert to string
fruits.join(); // "apple,banana,cherry"
fruits.join(" "); // "apple banana cherry"
fruits.join(" - "); // "apple - banana - cherry"

// concat - Combine arrays
const arr1 = [1, 2];
const arr2 = [3, 4];
const combined = arr1.concat(arr2); // [1, 2, 3, 4]

// Spread operator (modern way)
const combined2 = [...arr1, ...arr2]; // [1, 2, 3, 4]

// slice - Copy portion
numbers.slice(1, 3); // [1, 4]
numbers.slice(-2); // [1, 5] (last 2 elements)
numbers.slice(); // Copy entire array

// reverse - Reverse array (mutates original!)
numbers.reverse(); // [5, 1, 4, 1, 3]

// sort - Sort array (mutates original!)
numbers.sort(); // [1, 1, 3, 4, 5]
numbers.sort((a, b) => b - a); // [5, 4, 3, 1, 1] (descending)

// toSorted - Non-mutating sort (ES2023)
const sorted = numbers.toSorted(); // Returns new sorted array

// toReversed - Non-mutating reverse (ES2023)
const reversed = numbers.toReversed(); // Returns new reversed array

// flat - Flatten nested arrays
const nested = [1, [2, 3], [4, [5, 6]]];
nested.flat(); // [1, 2, 3, 4, [5, 6]]
nested.flat(2); // [1, 2, 3, 4, 5, 6]
nested.flat(Infinity); // Flatten all levels

// flatMap - Map then flatten
const arr = [1, 2, 3];
arr.flatMap((n) => [n, n * 2]); // [1, 2, 2, 4, 3, 6]

// fill - Fill with value
const arr = new Array(5).fill(0); // [0, 0, 0, 0, 0]

// copyWithin - Copy elements within array
const arr = [1, 2, 3, 4, 5];
arr.copyWithin(0, 3); // [4, 5, 3, 4, 5]

// ═══════════════════════════════════════════
// Array Destructuring
// ═══════════════════════════════════════════

const [first, second, third] = ["a", "b", "c"];
// first = "a", second = "b", third = "c"

// Skip elements
const [first, , third] = ["a", "b", "c"];
// first = "a", third = "c"

// Rest operator
const [first, ...rest] = [1, 2, 3, 4, 5];
// first = 1, rest = [2, 3, 4, 5]

// Default values
const [a = 1, b = 2] = [10];
// a = 10, b = 2

// Swapping variables
let a = 1,
  b = 2;
[a, b] = [b, a];
// a = 2, b = 1

// ═══════════════════════════════════════════
// Advanced Array Methods (ES2023+)
// ═══════════════════════════════════════════

const numbers = [1, 2, 3, 4, 5];

// with - Non-mutating element change (ES2023)
const newArr = numbers.with(2, 999); // [1, 2, 999, 4, 5]
// Original array unchanged

// toSpliced - Non-mutating splice (ES2023)
const spliced = numbers.toSpliced(1, 2, 99); // [1, 99, 4, 5]

// groupBy - Group by function (Stage 3 proposal)
const people = [
  { name: "Alice", age: 25 },
  { name: "Bob", age: 30 },
  { name: "Charlie", age: 25 },
];

// Using reduce to group
const grouped = people.reduce((acc, person) => {
  const key = person.age;
  if (!acc[key]) acc[key] = [];
  acc[key].push(person);
  return acc;
}, {});
// { 25: [{Alice}, {Charlie}], 30: [{Bob}] }
```

> **💡 Pro Tip:** Use `.map()` for transforming, `.filter()` for selecting, and `.reduce()` for calculating. Master these three and you'll write cleaner code!

---

### Objects 🎯

```javascript
// ═══════════════════════════════════════════
// Creating Objects
// ═══════════════════════════════════════════

// Object literal
const person = {
  name: "MrDib",
  age: 25,
  city: "Tokyo",
};

// Using new Object()
const person2 = new Object();
person2.name = "MrDib";

// Object.create()
const proto = {
  greet() {
    console.log("Hello");
  },
};
const obj = Object.create(proto);

// ═══════════════════════════════════════════
// Accessing Properties
// ═══════════════════════════════════════════

// Dot notation
person.name; // "MrDib"
person.age; // 25

// Bracket notation
person["name"]; // "MrDib"
person["age"]; // 25

// Dynamic property access
const prop = "name";
person[prop]; // "MrDib"

// Optional chaining (ES2020)
person?.name; // "MrDib"
person?.address?.city; // undefined (no error!)

// ═══════════════════════════════════════════
// Adding/Modifying Properties
// ═══════════════════════════════════════════

person.email = "mrdib@example.com"; // Add
person.age = 26; // Modify
person["country"] = "Japan"; // Add with bracket

// Computed property names
const key = "role";
const user = {
  name: "MrDib",
  [key]: "developer",
  ["is" + "Active"]: true,
};
// { name: "MrDib", role: "developer", isActive: true }

// ═══════════════════════════════════════════
// Deleting Properties
// ═══════════════════════════════════════════

delete person.city;
delete person["age"];

// ═══════════════════════════════════════════
// Checking Properties
// ═══════════════════════════════════════════

"name" in person; // true
"toString" in person; // true (inherited)

person.hasOwnProperty("name"); // true
person.hasOwnProperty("toString"); // false

// ═══════════════════════════════════════════
// Object Methods
// ═══════════════════════════════════════════

const user = {
  name: "MrDib",
  age: 25,
  greet() {
    console.log(`Hello, I'm ${this.name}`);
  },
  // Arrow functions don't have their own 'this'
  arrowGreet: () => {
    console.log(`Hello`);
  },
};

user.greet(); // "Hello, I'm MrDib"

// ═══════════════════════════════════════════
// Object Iteration
// ═══════════════════════════════════════════

const person = { name: "MrDib", age: 25, city: "Tokyo" };

// for...in (includes inherited properties)
for (const key in person) {
  if (person.hasOwnProperty(key)) {
    console.log(`${key}: ${person[key]}`);
  }
}

// Object.keys() - array of keys
Object.keys(person).forEach((key) => {
  console.log(`${key}: ${person[key]}`);
});

// Object.values() - array of values
Object.values(person).forEach((value) => {
  console.log(value);
});

// Object.entries() - array of [key, value] pairs
Object.entries(person).forEach(([key, value]) => {
  console.log(`${key}: ${value}`);
});

// for...of with Object.entries()
for (const [key, value] of Object.entries(person)) {
  console.log(`${key}: ${value}`);
}

// ═══════════════════════════════════════════
// Object Destructuring
// ═══════════════════════════════════════════

const person = { name: "MrDib", age: 25, city: "Tokyo" };

// Basic destructuring
const { name, age, city } = person;

// Rename variables
const { name: userName, age: userAge } = person;

// Default values
const { name, country = "Unknown" } = person;
// country = "Unknown"

// Rest operator
const { name, ...rest } = person;
// name = "MrDib", rest = { age: 25, city: "Tokyo" }

// Nested destructuring
const user = {
  name: "MrDib",
  address: {
    city: "Tokyo",
    country: "Japan",
  },
};

const {
  address: { city, country },
} = user;
// city = "Tokyo", country = "Japan"

// Function parameter destructuring
function greet({ name, age }) {
  console.log(`${name} is ${age} years old`);
}

greet(person); // "MrDib is 25 years old"

// ═══════════════════════════════════════════
// Spread Operator
// ═══════════════════════════════════════════

const obj1 = { a: 1, b: 2 };
const obj2 = { c: 3, d: 4 };

// Combine objects
const combined = { ...obj1, ...obj2 };
// { a: 1, b: 2, c: 3, d: 4 }

// Override properties
const updated = { ...obj1, b: 99, e: 5 };
// { a: 1, b: 99, e: 5 }

// Shallow copy
const copy = { ...obj1 };

// ═══════════════════════════════════════════
// Object Methods (Static)
// ═══════════════════════════════════════════

const source1 = { a: 1, b: 2 };
const source2 = { b: 3, c: 4 };

// Object.assign() - Merge objects
const merged = Object.assign({}, source1, source2);
// { a: 1, b: 3, c: 4 }

// Object.freeze() - Make immutable
const frozen = Object.freeze({ name: "MrDib" });
frozen.name = "New"; // Silently fails in strict mode
frozen.age = 25; // Cannot add properties

// Object.seal() - Prevent adding/removing properties
const sealed = Object.seal({ name: "MrDib" });
sealed.name = "New"; // ✅ Can modify
sealed.age = 25; // ❌ Cannot add

// Object.isFrozen() / Object.isSealed()
Object.isFrozen(frozen); // true
Object.isSealed(sealed); // true

// Object.fromEntries() - Convert entries to object
const entries = [
  ["name", "MrDib"],
  ["age", 25],
];
const obj = Object.fromEntries(entries);
// { name: "MrDib", age: 25 }

// Object.keys() / Object.values() / Object.entries()
Object.keys(person); // ["name", "age", "city"]
Object.values(person); // ["MrDib", 25, "Tokyo"]
Object.entries(person); // [["name", "MrDib"], ["age", 25], ...]

// Object.getOwnPropertyNames() - All own properties
Object.getOwnPropertyNames(person);

// Object.getOwnPropertyDescriptor()
Object.getOwnPropertyDescriptor(person, "name");
// { value: "MrDib", writable: true, enumerable: true, configurable: true }

// ═══════════════════════════════════════════
// Shorthand Properties & Methods (ES6)
// ═══════════════════════════════════════════

const name = "MrDib";
const age = 25;

// Property shorthand
const user = { name, age };
// Same as: { name: name, age: age }

// Method shorthand
const obj = {
  // Old way
  sayHello: function () {
    console.log("Hello");
  },
  // New way
  sayHi() {
    console.log("Hi");
  },
};

// ═══════════════════════════════════════════
// Getters & Setters
// ═══════════════════════════════════════════

const person = {
  firstName: "John",
  lastName: "Doe",

  // Getter
  get fullName() {
    return `${this.firstName} ${this.lastName}`;
  },

  // Setter
  set fullName(value) {
    const parts = value.split(" ");
    this.firstName = parts[0];
    this.lastName = parts[1];
  },
};

person.fullName; // "John Doe"
person.fullName = "Jane Smith";
person.firstName; // "Jane"

// ═══════════════════════════════════════════
// Object.defineProperty() - Advanced control
// ═══════════════════════════════════════════

const obj = {};

Object.defineProperty(obj, "name", {
  value: "MrDib",
  writable: false, // Cannot change value
  enumerable: true, // Shows in for...in
  configurable: false, // Cannot delete or reconfigure
});

obj.name = "New"; // Silently fails
delete obj.name; // Silently fails
```

> **⚠️ Note:** Object.freeze() is shallow! Nested objects are not frozen. Use a deep freeze function for complete immutability.

---

### Sets & Maps 🗺️

```javascript
// ═══════════════════════════════════════════
// Set - Unique values collection
// ═══════════════════════════════════════════

// Creating Sets
const set = new Set();
const setFromArray = new Set([1, 2, 3, 3, 3]); // [1, 2, 3]

// Adding values
set.add(1);
set.add(2);
set.add(2); // Duplicate, won't be added
set.add("hello");
set.add({ name: "MrDib" });

// Set operations
set.size; // Get size
set.has(1); // Check if value exists
set.delete(2); // Remove value
set.clear(); // Remove all values

// Iterating Sets
for (const value of set) {
  console.log(value);
}

set.forEach((value) => {
  console.log(value);
});

// Convert to array
const arr = [...set];
const arr2 = Array.from(set);

// Remove duplicates from array
const numbers = [1, 2, 2, 3, 3, 3, 4];
const unique = [...new Set(numbers)]; // [1, 2, 3, 4]

// Set operations (union, intersection, difference)
const setA = new Set([1, 2, 3]);
const setB = new Set([3, 4, 5]);

// Union
const union = new Set([...setA, ...setB]); // [1, 2, 3, 4, 5]

// Intersection
const intersection = new Set([...setA].filter((x) => setB.has(x))); // [3]

// Difference
const difference = new Set([...setA].filter((x) => !setB.has(x))); // [1, 2]

// ═══════════════════════════════════════════
// Map - Key-value pairs (better than objects!)
// ═══════════════════════════════════════════

// Creating Maps
const map = new Map();
const mapFromArray = new Map([
  ["name", "MrDib"],
  ["age", 25],
]);

// Adding entries
map.set("name", "MrDib");
map.set("age", 25);
map.set(1, "number key");
map.set(true, "boolean key");
map.set({}, "object key");

// Getting values
map.get("name"); // "MrDib"
map.get("unknown"); // undefined

// Map operations
map.size; // Get size
map.has("name"); // Check if key exists
map.delete("age"); // Remove entry
map.clear(); // Remove all entries

// Iterating Maps
for (const [key, value] of map) {
  console.log(`${key}: ${value}`);
}

map.forEach((value, key) => {
  console.log(`${key}: ${value}`);
});

// Map methods
map.keys(); // Iterator of keys
map.values(); // Iterator of values
map.entries(); // Iterator of [key, value] pairs

// Convert to array
const arr = [...map]; // Array of [key, value] pairs
const keys = [...map.keys()]; // Array of keys
const values = [...map.values()]; // Array of values

// Convert Map to Object
const obj = Object.fromEntries(map);

// Convert Object to Map
const objToMap = new Map(Object.entries(obj));

// ═══════════════════════════════════════════
// WeakSet & WeakMap (for memory efficiency)
// ═══════════════════════════════════════════

// WeakSet - Only holds objects, allows garbage collection
const weakSet = new WeakSet();
let obj = { name: "MrDib" };
weakSet.add(obj);
weakSet.has(obj); // true
obj = null; // Object can be garbage collected

// WeakMap - Keys must be objects
const weakMap = new WeakMap();
let key = { id: 1 };
weakMap.set(key, "value");
weakMap.get(key); // "value"
key = null; // Entry can be garbage collected
```

> **💡 Pro Tip:** Use **Set** for unique values, **Map** for key-value pairs with any key type. Use **WeakSet**/**WeakMap** when you want objects to be garbage collected!

---

<div align="center">

## 🔄 Control Flow

</div>

### Conditionals 🔀

```javascript
// ═══════════════════════════════════════════
// if / else if / else
// ═══════════════════════════════════════════

const age = 25;

if (age < 18) {
  console.log("Minor");
} else if (age < 65) {
  console.log("Adult");
} else {
  console.log("Senior");
}

// ═══════════════════════════════════════════
// Ternary Operator
// ═══════════════════════════════════════════

const status = age >= 18 ? "adult" : "minor";

// Nested ternary (use sparingly!)
const category = age < 18 ? "minor" : age < 65 ? "adult" : "senior";

// ═══════════════════════════════════════════
// Switch Statement
// ═══════════════════════════════════════════

const day = "Monday";

switch (day) {
  case "Monday":
    console.log("Start of week");
    break;
  case "Friday":
    console.log("Almost weekend!");
    break;
  case "Saturday":
  case "Sunday":
    console.log("Weekend!");
    break;
  default:
    console.log("Regular day");
}

// Switch without break (fall-through)
const month = 2;
let daysInMonth;

switch (month) {
  case 1:
  case 3:
  case 5:
  case 7:
  case 8:
  case 10:
  case 12:
    daysInMonth = 31;
    break;
  case 4:
  case 6:
  case 9:
  case 11:
    daysInMonth = 30;
    break;
  case 2:
    daysInMonth = 28;
    break;
  default:
    daysInMonth = 0;
}

// ═══════════════════════════════════════════
// Logical Operators
// ═══════════════════════════════════════════

// AND (&&)
if (age >= 18 && age < 65) {
  console.log("Working age");
}

// OR (||)
if (age < 18 || age > 65) {
  console.log("Not working age");
}

// NOT (!)
if (!isActive) {
  console.log("Inactive");
}

// Short-circuit evaluation
const name = username || "Guest"; // Use "Guest" if username is falsy
const admin = isAdmin && "Admin User"; // "Admin User" if isAdmin is true

// ═══════════════════════════════════════════
// Nullish Coalescing (??)  - ES2020
// ═══════════════════════════════════════════

// Only checks for null/undefined (not all falsy values!)
const count = 0;
const result1 = count || 10; // 10 (0 is falsy)
const result2 = count ?? 10; // 0 (only null/undefined are replaced)

const name = null;
const displayName = name ?? "Anonymous"; // "Anonymous"

// ═══════════════════════════════════════════
// Optional Chaining (?.)  - ES2020
// ═══════════════════════════════════════════

const user = {
  name: "MrDib",
  address: {
    city: "Tokyo",
  },
};

// Without optional chaining
const zip = user && user.address && user.address.zip;

// With optional chaining
const zip = user?.address?.zip; // undefined (no error!)

// With function calls
const result = user.greet?.(); // Only calls if greet exists

// With array access
const firstItem = user.items?.[0]; // Safe array access
```

---

### Loops 🔁

```javascript
// ═══════════════════════════════════════════
// for Loop
// ═══════════════════════════════════════════

// Traditional for loop
for (let i = 0; i < 5; i++) {
  console.log(i); // 0, 1, 2, 3, 4
}

// Counting backwards
for (let i = 5; i > 0; i--) {
  console.log(i); // 5, 4, 3, 2, 1
}

// Step by 2
for (let i = 0; i < 10; i += 2) {
  console.log(i); // 0, 2, 4, 6, 8
}

// Multiple variables
for (let i = 0, j = 10; i < 5; i++, j--) {
  console.log(i, j);
}

// ═══════════════════════════════════════════
// while Loop
// ═══════════════════════════════════════════

let count = 0;
while (count < 5) {
  console.log(count);
  count++;
}

// Infinite loop (use with caution!)
while (true) {
  const input = prompt("Continue? (y/n)");
  if (input === "n") break;
}

// ═══════════════════════════════════════════
// do...while Loop
// ═══════════════════════════════════════════

// Runs at least once
let i = 0;
do {
  console.log(i);
  i++;
} while (i < 5);

// ═══════════════════════════════════════════
// for...of Loop (for iterables)
// ═══════════════════════════════════════════

// Arrays
const fruits = ["apple", "banana", "cherry"];
for (const fruit of fruits) {
  console.log(fruit);
}

// Strings
for (const char of "Hello") {
  console.log(char);
}

// Sets
const set = new Set([1, 2, 3]);
for (const value of set) {
  console.log(value);
}

// Maps
const map = new Map([
  ["name", "MrDib"],
  ["age", 25],
]);
for (const [key, value] of map) {
  console.log(`${key}: ${value}`);
}

// With index using entries()
for (const [index, value] of fruits.entries()) {
  console.log(`${index}: ${value}`);
}

// ═══════════════════════════════════════════
// for...in Loop (for object keys)
// ═══════════════════════════════════════════

const person = { name: "MrDib", age: 25, city: "Tokyo" };

for (const key in person) {
  if (person.hasOwnProperty(key)) {
    console.log(`${key}: ${person[key]}`);
  }
}

// ⚠️ Not recommended for arrays (use for...of instead)
const arr = ["a", "b", "c"];
for (const index in arr) {
  console.log(arr[index]); // Works but not ideal
}

// ═══════════════════════════════════════════
// Loop Control: break & continue
// ═══════════════════════════════════════════

// break - Exit loop completely
for (let i = 0; i < 10; i++) {
  if (i === 5) break;
  console.log(i); // 0, 1, 2, 3, 4
}

// continue - Skip current iteration
for (let i = 0; i < 10; i++) {
  if (i % 2 === 0) continue; // Skip even numbers
  console.log(i); // 1, 3, 5, 7, 9
}

// Labeled statements (for nested loops)
outer: for (let i = 0; i < 3; i++) {
  for (let j = 0; j < 3; j++) {
    if (i === 1 && j === 1) break outer; // Break outer loop
    console.log(i, j);
  }
}

// ═══════════════════════════════════════════
// Array Methods (alternatives to loops)
// ═══════════════════════════════════════════

const numbers = [1, 2, 3, 4, 5];

// forEach - Iterate over each element
numbers.forEach((num, index) => {
  console.log(`${index}: ${num}`);
});

// map - Transform each element
const doubled = numbers.map((n) => n * 2);

// filter - Select elements
const evens = numbers.filter((n) => n % 2 === 0);

// reduce - Reduce to single value
const sum = numbers.reduce((acc, n) => acc + n, 0);

// some - Check if any match
const hasEven = numbers.some((n) => n % 2 === 0);

// every - Check if all match
const allPositive = numbers.every((n) => n > 0);

// find - Find first match
const firstEven = numbers.find((n) => n % 2 === 0);

// findIndex - Find index of first match
const index = numbers.findIndex((n) => n % 2 === 0);
```

> **💡 Pro Tip:** Use `for...of` for arrays/iterables, `for...in` for object keys, and array methods like `.forEach()`, `.map()`, `.filter()` for cleaner code!

---

<div align="center">

## 🔧 Functions

</div>

### Function Declarations & Expressions 📦

```javascript
// ═══════════════════════════════════════════
// Function Declaration (Hoisted)
// ═══════════════════════════════════════════

function greet(name) {
  return `Hello, ${name}!`;
}

greet("MrDib"); // "Hello, MrDib!"

// Can be called before declaration (hoisting)
sayHi(); // Works!

function sayHi() {
  console.log("Hi!");
}

// ═══════════════════════════════════════════
// Function Expression (Not Hoisted)
// ═══════════════════════════════════════════

const greet = function (name) {
  return `Hello, ${name}!`;
};

greet("MrDib");

// Anonymous function
const add = function (a, b) {
  return a + b;
};

// Named function expression (for recursion)
const factorial = function fact(n) {
  return n <= 1 ? 1 : n * fact(n - 1);
};

// ═══════════════════════════════════════════
// Arrow Functions (ES6)
// ═══════════════════════════════════════════

// Basic syntax
const greet = (name) => {
  return `Hello, ${name}!`;
};

// Implicit return (single expression)
const greet = (name) => `Hello, ${name}!`;

// Multiple parameters
const add = (a, b) => a + b;

// No parameters
const getRandom = () => Math.random();

// Single parameter (parentheses optional)
const double = (n) => n * 2;

// Object return (wrap in parentheses!)
const makePerson = (name, age) => ({ name, age });

// Multiline with implicit return
const sum = (a, b) => a + b;

// ═══════════════════════════════════════════
// Arrow Functions vs Regular Functions
// ═══════════════════════════════════════════

// 1. 'this' binding
const obj = {
  name: "MrDib",

  // Regular function - 'this' refers to obj
  greet: function () {
    console.log(`Hello, I'm ${this.name}`);
  },

  // Arrow function - 'this' refers to outer scope
  greetArrow: () => {
    console.log(`Hello, I'm ${this.name}`); // undefined!
  },
};

// 2. No arguments object
function regular() {
  console.log(arguments); // [1, 2, 3]
}
regular(1, 2, 3);

const arrow = () => {
  console.log(arguments); // ReferenceError!
};

// Use rest parameters instead
const arrow = (...args) => {
  console.log(args); // [1, 2, 3]
};

// 3. Cannot be used as constructors
const Person = (name) => {
  this.name = name;
};
new Person("MrDib"); // TypeError!

// ═══════════════════════════════════════════
// Default Parameters (ES6)
// ═══════════════════════════════════════════

function greet(name = "Guest", greeting = "Hello") {
  return `${greeting}, ${name}!`;
}

greet(); // "Hello, Guest!"
greet("MrDib"); // "Hello, MrDib!"
greet("MrDib", "Hi"); // "Hi, MrDib!"

// Default with expression
function createUser(name, id = Date.now()) {
  return { name, id };
}

// Default based on other parameters
function getArea(width, height = width) {
  return width * height;
}

// ═══════════════════════════════════════════
// Rest Parameters (...args)
// ═══════════════════════════════════════════

function sum(...numbers) {
  return numbers.reduce((total, n) => total + n, 0);
}

sum(1, 2, 3, 4, 5); // 15
sum(1, 2); // 3

// Combine with regular parameters
function multiply(multiplier, ...numbers) {
  return numbers.map((n) => n * multiplier);
}

multiply(2, 1, 2, 3); // [2, 4, 6]

// ═══════════════════════════════════════════
// Spread Operator (...)
// ═══════════════════════════════════════════

// Spread array into arguments
const numbers = [1, 2, 3, 4, 5];
Math.max(...numbers); // 5

// Combine arrays
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
const combined = [...arr1, ...arr2]; // [1, 2, 3, 4, 5, 6]

// Copy array
const original = [1, 2, 3];
const copy = [...original];

// Spread objects
const obj1 = { a: 1, b: 2 };
const obj2 = { c: 3, d: 4 };
const merged = { ...obj1, ...obj2 }; // { a: 1, b: 2, c: 3, d: 4 }

// ═══════════════════════════════════════════
// Destructuring Parameters
// ═══════════════════════════════════════════

// Object destructuring
function createUser({ name, age, email = "unknown" }) {
  return { name, age, email };
}

createUser({ name: "MrDib", age: 25 });
// { name: "MrDib", age: 25, email: "unknown" }

// Array destructuring
function getCoordinates([x, y, z = 0]) {
  return { x, y, z };
}

getCoordinates([10, 20]); // { x: 10, y: 20, z: 0 }

// ═══════════════════════════════════════════
// Function as Return Value (Higher-Order)
// ═══════════════════════════════════════════

function multiplier(factor) {
  return function (number) {
    return number * factor;
  };
}

const double = multiplier(2);
const triple = multiplier(3);

double(5); // 10
triple(5); // 15

// Arrow function version
const multiplier = (factor) => (number) => number * factor;

// ═══════════════════════════════════════════
// Immediately Invoked Function Expression (IIFE)
// ═══════════════════════════════════════════

// Creates isolated scope
(function () {
  const private = "I'm private";
  console.log("IIFE executed");
})();

// With parameters
(function (name) {
  console.log(`Hello, ${name}`);
})("MrDib");

// Arrow IIFE
(() => {
  console.log("Arrow IIFE");
})();

// ═══════════════════════════════════════════
// Callback Functions
// ═══════════════════════════════════════════

function fetchData(url, callback) {
  // Simulated async operation
  setTimeout(() => {
    const data = { user: "MrDib" };
    callback(data);
  }, 1000);
}

fetchData("/api/user", (data) => {
  console.log(data);
});

// Array methods with callbacks
[1, 2, 3].forEach((num) => console.log(num));
[1, 2, 3].map((num) => num * 2);
[1, 2, 3].filter((num) => num > 1);

// ═══════════════════════════════════════════
// Recursion
// ═══════════════════════════════════════════

// Factorial
function factorial(n) {
  if (n <= 1) return 1;
  return n * factorial(n - 1);
}

factorial(5); // 120

// Fibonacci
function fibonacci(n) {
  if (n <= 1) return n;
  return fibonacci(n - 1) + fibonacci(n - 2);
}

fibonacci(7); // 13

// Countdown
function countdown(n) {
  if (n < 0) return;
  console.log(n);
  countdown(n - 1);
}

countdown(5); // 5, 4, 3, 2, 1, 0

// Flatten array (recursive)
function flatten(arr) {
  return arr.reduce((flat, item) => {
    return flat.concat(Array.isArray(item) ? flatten(item) : item);
  }, []);
}

flatten([1, [2, [3, [4, 5]]]]); // [1, 2, 3, 4, 5]
```

> **💡 Pro Tip:** Use arrow functions for short callbacks and when you need to preserve `this` context. Use regular functions for methods and when you need `arguments` object!

---

<div align="center">

## 🏗️ Object-Oriented Programming

</div>

### Classes & Objects 🎯

```javascript
// ═══════════════════════════════════════════
// Class Declaration (ES6)
// ═══════════════════════════════════════════

class Person {
  // Constructor
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  // Method
  greet() {
    console.log(`Hello, I'm ${this.name}`);
  }

  // Static method (called on class, not instance)
  static create(name, age) {
    return new Person(name, age);
  }

  // Getter
  get info() {
    return `${this.name} (${this.age})`;
  }

  // Setter
  set info(value) {
    const [name, age] = value.split(",");
    this.name = name.trim();
    this.age = parseInt(age.trim());
  }
}

// Create instance
const person = new Person("MrDib", 25);
person.greet(); // "Hello, I'm MrDib"

// Static method
const person2 = Person.create("Alice", 30);

// Getter/Setter
console.log(person.info); // "MrDib (25)"
person.info = "Bob, 35";
console.log(person.name); // "Bob"

// ═══════════════════════════════════════════
// Private Fields & Methods (ES2022)
// ═══════════════════════════════════════════

class BankAccount {
  // Private field (starts with #)
  #balance = 0;
  #pin;

  constructor(initialBalance, pin) {
    this.#balance = initialBalance;
    this.#pin = pin;
  }

  // Public method
  deposit(amount) {
    this.#validateAmount(amount);
    this.#balance += amount;
    return this.#balance;
  }

  withdraw(amount, pin) {
    if (!this.#verifyPin(pin)) {
      throw new Error("Invalid PIN");
    }
    this.#validateAmount(amount);
    if (amount > this.#balance) {
      throw new Error("Insufficient funds");
    }
    this.#balance -= amount;
    return this.#balance;
  }

  // Getter for private field
  getBalance(pin) {
    if (!this.#verifyPin(pin)) {
      throw new Error("Invalid PIN");
    }
    return this.#balance;
  }

  // Private method
  #validateAmount(amount) {
    if (amount <= 0) {
      throw new Error("Amount must be positive");
    }
  }

  #verifyPin(pin) {
    return pin === this.#pin;
  }
}

const account = new BankAccount(1000, "1234");
account.deposit(500); // ✅ Works
console.log(account.#balance); // ❌ SyntaxError: Private field
console.log(account.getBalance("1234")); // ✅ 1500

// ═══════════════════════════════════════════
// Inheritance
// ═══════════════════════════════════════════

class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} makes a sound`);
  }

  move() {
    console.log(`${this.name} moves`);
  }
}

class Dog extends Animal {
  constructor(name, breed) {
    super(name); // Call parent constructor
    this.breed = breed;
  }

  // Override parent method
  speak() {
    console.log(`${this.name} barks`);
  }

  // Call parent method
  moveAndSpeak() {
    super.move();
    this.speak();
  }
}

const dog = new Dog("Buddy", "Golden Retriever");
dog.speak(); // "Buddy barks"
dog.moveAndSpeak(); // "Buddy moves" + "Buddy barks"

// Check inheritance
dog instanceof Dog; // true
dog instanceof Animal; // true

// ═══════════════════════════════════════════
// Static Properties & Methods
// ═══════════════════════════════════════════

class MathHelper {
  static PI = 3.14159;
  static #privateStaticField = "secret";

  static circleArea(radius) {
    return this.PI * radius ** 2;
  }

  static squareArea(side) {
    return side ** 2;
  }

  static #privateStaticMethod() {
    return "This is private";
  }

  static getSecret() {
    return this.#privateStaticMethod();
  }
}

// Use static members without instance
console.log(MathHelper.PI); // 3.14159
console.log(MathHelper.circleArea(5)); // 78.53975
console.log(MathHelper.getSecret()); // "This is private"

// ═══════════════════════════════════════════
// Getters & Setters
// ═══════════════════════════════════════════

class User {
  constructor(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
    this._email = "";
  }

  // Computed property with getter
  get fullName() {
    return `${this.firstName} ${this.lastName}`;
  }

  // Setter with validation
  set fullName(value) {
    const parts = value.split(" ");
    if (parts.length !== 2) {
      throw new Error("Full name must have first and last name");
    }
    this.firstName = parts[0];
    this.lastName = parts[1];
  }

  get email() {
    return this._email;
  }

  set email(value) {
    if (!value.includes("@")) {
      throw new Error("Invalid email");
    }
    this._email = value;
  }
}

const user = new User("John", "Doe");
console.log(user.fullName); // "John Doe"
user.fullName = "Jane Smith";
console.log(user.firstName); // "Jane"

user.email = "jane@example.com"; // ✅ Works
// user.email = "invalid";        // ❌ Throws error

// ═══════════════════════════════════════════
// Class Expression
// ═══════════════════════════════════════════

// Named class expression
const Person = class PersonClass {
  constructor(name) {
    this.name = name;
  }
};

// Anonymous class expression
const Animal = class {
  constructor(name) {
    this.name = name;
  }
};

// ═══════════════════════════════════════════
// Mixins (Multiple Inheritance Pattern)
// ═══════════════════════════════════════════

// Mixin functions
const CanEat = (Base) =>
  class extends Base {
    eat(food) {
      console.log(`${this.name} is eating ${food}`);
    }
  };

const CanWalk = (Base) =>
  class extends Base {
    walk() {
      console.log(`${this.name} is walking`);
    }
  };

const CanSwim = (Base) =>
  class extends Base {
    swim() {
      console.log(`${this.name} is swimming`);
    }
  };

// Base class
class Animal {
  constructor(name) {
    this.name = name;
  }
}

// Apply mixins
class Dog extends CanWalk(CanEat(Animal)) {
  bark() {
    console.log(`${this.name} barks`);
  }
}

class Fish extends CanSwim(CanEat(Animal)) {
  // Fish-specific methods
}

const dog = new Dog("Buddy");
dog.eat("bone"); // ✅ Works
dog.walk(); // ✅ Works
dog.bark(); // ✅ Works
// dog.swim();     // ❌ Not available

const fish = new Fish("Nemo");
fish.eat("plankton"); // ✅ Works
fish.swim(); // ✅ Works
// fish.walk();       // ❌ Not available

// ═══════════════════════════════════════════
// Prototypes (Pre-ES6 OOP)
// ═══════════════════════════════════════════

// Constructor function
function Person(name, age) {
  this.name = name;
  this.age = age;
}

// Add method to prototype
Person.prototype.greet = function () {
  console.log(`Hello, I'm ${this.name}`);
};

// Create instance
const person = new Person("MrDib", 25);
person.greet(); // "Hello, I'm MrDib"

// Prototype chain
console.log(person.__proto__ === Person.prototype); // true
console.log(Person.prototype.__proto__ === Object.prototype); // true

// Check prototype
Object.getPrototypeOf(person) === Person.prototype; // true

// Set prototype
const obj = Object.create(Person.prototype);

// ═══════════════════════════════════════════
// Object.create() Pattern
// ═══════════════════════════════════════════

const personPrototype = {
  greet() {
    console.log(`Hello, I'm ${this.name}`);
  },

  init(name, age) {
    this.name = name;
    this.age = age;
    return this;
  },
};

const person = Object.create(personPrototype).init("MrDib", 25);
person.greet(); // "Hello, I'm MrDib"
```

> **💡 Pro Tip:** Use classes for cleaner syntax, but understand prototypes under the hood. Private fields (#) are great for encapsulation!

---

<div align="center">

## ⚡ Async JavaScript

</div>

### Callbacks, Promises & Async/Await 🔄

```javascript
// ═══════════════════════════════════════════
// Callbacks (Old Way)
// ═══════════════════════════════════════════

function fetchUser(id, callback) {
  setTimeout(() => {
    const user = { id, name: "MrDib" };
    callback(null, user); // (error, data) convention
  }, 1000);
}

fetchUser(1, (error, user) => {
  if (error) {
    console.error(error);
    return;
  }
  console.log(user);
});

// Callback Hell (Pyramid of Doom) 😱
fetchUser(1, (err, user) => {
  if (err) return console.error(err);

  fetchPosts(user.id, (err, posts) => {
    if (err) return console.error(err);

    fetchComments(posts[0].id, (err, comments) => {
      if (err) return console.error(err);

      console.log(comments); // Finally!
    });
  });
});

// ═══════════════════════════════════════════
// Promises (Better Way)
// ═══════════════════════════════════════════

// Creating a Promise
const promise = new Promise((resolve, reject) => {
  const success = true;

  if (success) {
    resolve("Success!");
  } else {
    reject("Error occurred");
  }
});

// Consuming a Promise
promise
  .then((result) => {
    console.log(result); // "Success!"
  })
  .catch((error) => {
    console.error(error);
  })
  .finally(() => {
    console.log("Cleanup");
  });

// Promise example with setTimeout
function fetchUser(id) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      if (id > 0) {
        resolve({ id, name: "MrDib" });
      } else {
        reject("Invalid ID");
      }
    }, 1000);
  });
}

// Using the promise
fetchUser(1)
  .then((user) => {
    console.log(user);
    return user.id;
  })
  .then((id) => {
    console.log(`User ID: ${id}`);
  })
  .catch((error) => {
    console.error(error);
  });

// ═══════════════════════════════════════════
// Promise Chaining (No More Callback Hell!)
// ═══════════════════════════════════════════

fetchUser(1)
  .then((user) => fetchPosts(user.id))
  .then((posts) => fetchComments(posts[0].id))
  .then((comments) => {
    console.log(comments); // Much cleaner! 🎉
  })
  .catch((error) => {
    console.error(error); // Single error handler
  });

// ═══════════════════════════════════════════
// Async/Await (Best Way!)
// ═══════════════════════════════════════════

async function getUser() {
  try {
    const user = await fetchUser(1);
    console.log(user);
    return user;
  } catch (error) {
    console.error(error);
  }
}

// Async function always returns a Promise
getUser().then((user) => console.log(user));

// Sequential execution
async function getUserData() {
  try {
    const user = await fetchUser(1);
    const posts = await fetchPosts(user.id);
    const comments = await fetchComments(posts[0].id);

    return { user, posts, comments };
  } catch (error) {
    console.error("Error:", error);
  }
}

// ═══════════════════════════════════════════
// Promise.all() - Run in Parallel
// ═══════════════════════════════════════════

// All must succeed
const promises = [fetchUser(1), fetchUser(2), fetchUser(3)];

// Traditional way
Promise.all(promises)
  .then((users) => {
    console.log(users); // [user1, user2, user3]
  })
  .catch((error) => {
    console.error(error); // If ANY fails
  });

// With async/await
async function getAllUsers() {
  try {
    const [user1, user2, user3] = await Promise.all([
      fetchUser(1),
      fetchUser(2),
      fetchUser(3),
    ]);

    console.log(user1, user2, user3);
  } catch (error) {
    console.error(error);
  }
}

// ═══════════════════════════════════════════
// Promise.allSettled() - Wait for All (ES2020)
// ═══════════════════════════════════════════

// Returns results of all promises (fulfilled or rejected)
const promises = [
  Promise.resolve("Success 1"),
  Promise.reject("Error 1"),
  Promise.resolve("Success 2"),
];

Promise.allSettled(promises).then((results) => {
  console.log(results);
  /* [
    { status: "fulfilled", value: "Success 1" },
    { status: "rejected", reason: "Error 1" },
    { status: "fulfilled", value: "Success 2" }
  ] */
});

// Practical example
async function fetchMultipleUsers() {
  const userIds = [1, 2, 999, 3]; // 999 doesn't exist

  const results = await Promise.allSettled(userIds.map((id) => fetchUser(id)));

  const successful = results
    .filter((r) => r.status === "fulfilled")
    .map((r) => r.value);

  const failed = results
    .filter((r) => r.status === "rejected")
    .map((r) => r.reason);

  return { successful, failed };
}

// ═══════════════════════════════════════════
// Promise.race() - First to Finish
// ═══════════════════════════════════════════

// Returns first promise that settles (resolve or reject)
const fast = new Promise((resolve) => setTimeout(() => resolve("Fast"), 100));
const slow = new Promise((resolve) => setTimeout(() => resolve("Slow"), 1000));

Promise.race([fast, slow]).then((result) => {
  console.log(result); // "Fast"
});

// Timeout pattern
function timeout(ms) {
  return new Promise((_, reject) =>
    setTimeout(() => reject(new Error("Timeout")), ms)
  );
}

async function fetchWithTimeout(url, ms) {
  try {
    const result = await Promise.race([fetch(url), timeout(ms)]);
    return result;
  } catch (error) {
    console.error("Request timed out or failed:", error);
  }
}

// ═══════════════════════════════════════════
// Promise.any() - First Success (ES2021)
// ═══════════════════════════════════════════

// Returns first fulfilled promise, ignores rejections
const promises = [
  Promise.reject("Error 1"),
  Promise.reject("Error 2"),
  Promise.resolve("Success!"),
  Promise.resolve("Also success"),
];

Promise.any(promises).then((result) => {
  console.log(result); // "Success!"
});

// All rejections = AggregateError
Promise.any([Promise.reject("Error 1"), Promise.reject("Error 2")]).catch(
  (error) => {
    console.log(error.errors); // ["Error 1", "Error 2"]
  }
);

// Fallback servers example
async function fetchFromMultipleServers() {
  const servers = [
    "https://api1.example.com",
    "https://api2.example.com",
    "https://api3.example.com",
  ];

  try {
    const response = await Promise.any(servers.map((url) => fetch(url)));
    return await response.json();
  } catch (error) {
    console.error("All servers failed");
  }
}

// ═══════════════════════════════════════════
// Async Iteration
// ═══════════════════════════════════════════

// for await...of
async function* asyncGenerator() {
  yield await Promise.resolve(1);
  yield await Promise.resolve(2);
  yield await Promise.resolve(3);
}

async function processAsync() {
  for await (const num of asyncGenerator()) {
    console.log(num); // 1, 2, 3
  }
}

// Async iteration over array
const urls = ["/api/user/1", "/api/user/2", "/api/user/3"];

async function fetchSequentially() {
  for (const url of urls) {
    const response = await fetch(url);
    const data = await response.json();
    console.log(data);
  }
}

// ═══════════════════════════════════════════
// Error Handling Best Practices
// ═══════════════════════════════════════════

// Multiple try-catch blocks
async function complexOperation() {
  let user, posts;

  try {
    user = await fetchUser(1);
  } catch (error) {
    console.error("Failed to fetch user:", error);
    return null;
  }

  try {
    posts = await fetchPosts(user.id);
  } catch (error) {
    console.error("Failed to fetch posts:", error);
    posts = []; // Use default value
  }

  return { user, posts };
}

// Wrapper for try-catch
const handle = (promise) => {
  return promise.then((data) => [null, data]).catch((error) => [error, null]);
};

// Usage
async function getUser() {
  const [error, user] = await handle(fetchUser(1));

  if (error) {
    console.error(error);
    return null;
  }

  return user;
}

// ═══════════════════════════════════════════
// Fetch API (Modern HTTP Requests)
// ═══════════════════════════════════════════

// GET request
async function getUser(id) {
  try {
    const response = await fetch(`/api/users/${id}`);

    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }

    const user = await response.json();
    return user;
  } catch (error) {
    console.error("Fetch failed:", error);
  }
}

// POST request
async function createUser(userData) {
  try {
    const response = await fetch("/api/users", {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify(userData),
    });

    const user = await response.json();
    return user;
  } catch (error) {
    console.error("Create failed:", error);
  }
}

// With abort controller (timeout)
async function fetchWithTimeout(url, timeout = 5000) {
  const controller = new AbortController();
  const timeoutId = setTimeout(() => controller.abort(), timeout);

  try {
    const response = await fetch(url, {
      signal: controller.signal,
    });
    clearTimeout(timeoutId);
    return await response.json();
  } catch (error) {
    if (error.name === "AbortError") {
      console.error("Request timed out");
    } else {
      console.error("Fetch failed:", error);
    }
  }
}

// ═══════════════════════════════════════════
// Practical Async Patterns
// ═══════════════════════════════════════════

// Retry logic
async function fetchWithRetry(url, retries = 3) {
  for (let i = 0; i < retries; i++) {
    try {
      const response = await fetch(url);
      return await response.json();
    } catch (error) {
      if (i === retries - 1) throw error;
      console.log(`Retry ${i + 1}/${retries}`);
      await new Promise((resolve) => setTimeout(resolve, 1000 * (i + 1)));
    }
  }
}

// Batch processing
async function processBatch(items, batchSize = 5) {
  const results = [];

  for (let i = 0; i < items.length; i += batchSize) {
    const batch = items.slice(i, i + batchSize);
    const batchResults = await Promise.all(
      batch.map((item) => processItem(item))
    );
    results.push(...batchResults);
  }

  return results;
}

// Rate limiting
async function rateLimitedFetch(urls, requestsPerSecond = 2) {
  const delay = 1000 / requestsPerSecond;
  const results = [];

  for (const url of urls) {
    const result = await fetch(url);
    results.push(await result.json());
    await new Promise((resolve) => setTimeout(resolve, delay));
  }

  return results;
}

// Polling
async function pollUntilSuccess(fn, interval = 1000, maxAttempts = 10) {
  for (let i = 0; i < maxAttempts; i++) {
    try {
      const result = await fn();
      if (result) return result;
    } catch (error) {
      console.log(`Attempt ${i + 1} failed`);
    }
    await new Promise((resolve) => setTimeout(resolve, interval));
  }
  throw new Error("Max attempts reached");
}
```

> **💡 Pro Tip:** Use **async/await** for cleaner code, **Promise.all()** for parallel execution, and **Promise.allSettled()** when you need all results regardless of success/failure!

---

<div align="center">

## 🎨 Modern ES Features

</div>

### ES6 to ES2024+ Features 🚀

```javascript
// ═══════════════════════════════════════════
// Destructuring (ES6)
// ═══════════════════════════════════════════

// Array destructuring
const [first, second, ...rest] = [1, 2, 3, 4, 5];
// first = 1, second = 2, rest = [3, 4, 5]

// Object destructuring
const { name, age, email = "unknown" } = user;

// Nested destructuring
const {
  address: { city, country },
} = user;

// Rename while destructuring
const { name: userName, age: userAge } = user;

// Function parameter destructuring
function greet({ name, age }) {
  console.log(`${name} is ${age} years old`);
}

// ═══════════════════════════════════════════
// Optional Chaining (?.) - ES2020
// ═══════════════════════════════════════════

// Safe property access
const city = user?.address?.city;

// Safe method call
const result = user.greet?.();

// Safe array access
const firstItem = arr?.[0];

// ═══════════════════════════════════════════
// Nullish Coalescing (??) - ES2020
// ═══════════════════════════════════════════

// Only null/undefined trigger default
const count = value ?? 0; // Not "", false, or 0

// ═══════════════════════════════════════════
// Logical Assignment (ES2021)
// ═══════════════════════════════════════════

// OR assignment
let x = null;
x ||= 10; // x = x || 10

// AND assignment
let y = 5;
y &&= 10; // y = y && 10

// Nullish assignment
let z = null;
z ??= 10; // z = z ?? 10

// ═══════════════════════════════════════════
// Numeric Separators (ES2021)
// ═══════════════════════════════════════════

const billion = 1_000_000_000;
const hex = 0xff_ff_ff_ff;
const binary = 0b1010_0001_1000_0101;

// ═══════════════════════════════════════════
// String.replaceAll() - ES2021
// ═══════════════════════════════════════════

const text = "hello world hello";
text.replaceAll("hello", "hi"); // "hi world hi"

// ═══════════════════════════════════════════
// Promise.any() - ES2021
// ═══════════════════════════════════════════

const first = await Promise.any([promise1, promise2, promise3]);

// ═══════════════════════════════════════════
// WeakRefs & FinalizationRegistry - ES2021
// ═══════════════════════════════════════════

// Weak reference to object
let obj = { name: "MrDib" };
const weakRef = new WeakRef(obj);

// Get value (might be undefined if garbage collected)
const value = weakRef.deref();

// Cleanup callback when object is collected
const registry = new FinalizationRegistry((value) => {
  console.log(`${value} was garbage collected`);
});

registry.register(obj, "my object");

// ═══════════════════════════════════════════
// Top-level await - ES2022
// ═══════════════════════════════════════════

// In modules (.mjs), can await at top level
const user = await fetchUser(1);
console.log(user);

// ═══════════════════════════════════════════
// Array.at() - ES2022
// ═══════════════════════════════════════════

const arr = [1, 2, 3, 4, 5];
arr.at(0); // 1
arr.at(-1); // 5 (last element)
arr.at(-2); // 4 (second to last)

// ═══════════════════════════════════════════
// Object.hasOwn() - ES2022
// ═══════════════════════════════════════════

// Better than hasOwnProperty
Object.hasOwn(obj, "name"); // true/false

// ═══════════════════════════════════════════
// Error.cause - ES2022
// ═══════════════════════════════════════════

try {
  throw new Error("Failed");
} catch (error) {
  throw new Error("Operation failed", { cause: error });
}

// ═══════════════════════════════════════════
// Array Methods - ES2023
// ═══════════════════════════════════════════

const arr = [1, 2, 3, 4, 5];

// Non-mutating methods
arr.toSorted(); // Sort without mutating
arr.toReversed(); // Reverse without mutating
arr.toSpliced(1, 2, 99); // Splice without mutating
arr.with(2, 999); // Change element without mutating

// findLast & findLastIndex
arr.findLast((n) => n > 2); // 5
arr.findLastIndex((n) => n > 2); // 4

// ═══════════════════════════════════════════
// Array grouping - Stage 3 (Upcoming)
// ═══════════════════════════════════════════

const people = [
  { name: "Alice", age: 25 },
  { name: "Bob", age: 30 },
  { name: "Charlie", age: 25 },
];

// Group by age (when available)
// const grouped = Object.groupBy(people, person => person.age);
// { 25: [{Alice}, {Charlie}], 30: [{Bob}] }

// For now, use reduce
const grouped = people.reduce((acc, person) => {
  const key = person.age;
  if (!acc[key]) acc[key] = [];
  acc[key].push(person);
  return acc;
}, {});

// ═══════════════════════════════════════════
// Records & Tuples - Stage 2 (Future)
// ═══════════════════════════════════════════

// Immutable data structures (coming soon!)
// const record = #{ name: "MrDib", age: 25 };
// const tuple = #[1, 2, 3];

// ═══════════════════════════════════════════
// Pipeline Operator - Stage 2 (Future)
// ═══════════════════════════════════════════

// Will allow chaining operations
// const result = value |> fn1 |> fn2 |> fn3;

// Current alternative: function composition
const pipe =
  (...fns) =>
  (x) =>
    fns.reduce((v, f) => f(v), x);

const double = (x) => x * 2;
const addOne = (x) => x + 1;
const square = (x) => x ** 2;

const transform = pipe(double, addOne, square);
transform(3); // ((3 * 2) + 1)² = 49
```

> **💡 Pro Tip:** Stay updated with JavaScript proposals at [TC39 GitHub](https://github.com/tc39/proposals). Many features start as proposals before becoming standard!

---

<div align="center">

## 🎯 Design Patterns

</div>

### Common JavaScript Design Patterns 🏗️

```javascript
// ═══════════════════════════════════════════
// Module Pattern - Encapsulation
// ═══════════════════════════════════════════

const UserModule = (() => {
  // Private variables
  let users = [];
  let currentId = 1;

  // Private functions
  function validateEmail(email) {
    return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
  }

  function generateId() {
    return currentId++;
  }

  // Public API
  return {
    addUser(name, email) {
      if (!validateEmail(email)) {
        throw new Error("Invalid email");
      }

      const user = {
        id: generateId(),
        name,
        email,
        createdAt: new Date(),
      };

      users.push(user);
      return user;
    },

    getUser(id) {
      return users.find((u) => u.id === id);
    },

    getAllUsers() {
      return [...users]; // Return copy
    },

    updateUser(id, updates) {
      const user = this.getUser(id);
      if (!user) throw new Error("User not found");

      Object.assign(user, updates);
      return user;
    },

    deleteUser(id) {
      const index = users.findIndex((u) => u.id === id);
      if (index === -1) throw new Error("User not found");

      return users.splice(index, 1)[0];
    },

    getUserCount() {
      return users.length;
    },
  };
})();

// Usage
const user = UserModule.addUser("MrDib", "mrdib@example.com");
console.log(UserModule.getAllUsers());

// ═══════════════════════════════════════════
// Factory Pattern - Object Creation
// ═══════════════════════════════════════════

class User {
  constructor(name, email, role) {
    this.name = name;
    this.email = email;
    this.role = role;
  }

  getPermissions() {
    return ["read"];
  }
}

class AdminUser extends User {
  constructor(name, email) {
    super(name, email, "admin");
  }

  getPermissions() {
    return ["read", "write", "delete", "manage"];
  }
}

class ModeratorUser extends User {
  constructor(name, email) {
    super(name, email, "moderator");
  }

  getPermissions() {
    return ["read", "write", "moderate"];
  }
}

// Factory
class UserFactory {
  static createUser(type, name, email) {
    switch (type) {
      case "admin":
        return new AdminUser(name, email);
      case "moderator":
        return new ModeratorUser(name, email);
      case "user":
      default:
        return new User(name, email, "user");
    }
  }
}

// Usage
const admin = UserFactory.createUser("admin", "MrDib", "admin@example.com");
const user = UserFactory.createUser("user", "Alice", "alice@example.com");

console.log(admin.getPermissions()); // ["read", "write", "delete", "manage"]
console.log(user.getPermissions()); // ["read"]

// ═══════════════════════════════════════════
// Singleton Pattern - Single Instance
// ═══════════════════════════════════════════

class Database {
  constructor() {
    if (Database.instance) {
      return Database.instance;
    }

    this.connection = null;
    this.data = [];
    Database.instance = this;
  }

  connect() {
    if (!this.connection) {
      this.connection = "Connected to DB";
      console.log("Database connected");
    }
    return this.connection;
  }

  query(sql) {
    console.log(`Executing: ${sql}`);
    return this.data;
  }

  disconnect() {
    this.connection = null;
    console.log("Database disconnected");
  }
}

// Usage
const db1 = new Database();
const db2 = new Database();

console.log(db1 === db2); // true (same instance)

// Modern approach with ES6
class DatabaseModern {
  static #instance = null;

  constructor() {
    if (DatabaseModern.#instance) {
      return DatabaseModern.#instance;
    }
    DatabaseModern.#instance = this;
  }

  static getInstance() {
    if (!DatabaseModern.#instance) {
      DatabaseModern.#instance = new DatabaseModern();
    }
    return DatabaseModern.#instance;
  }
}

// ═══════════════════════════════════════════
// Observer Pattern - Event System
// ═══════════════════════════════════════════

class EventEmitter {
  constructor() {
    this.events = {};
  }

  // Subscribe to event
  on(event, callback) {
    if (!this.events[event]) {
      this.events[event] = [];
    }
    this.events[event].push(callback);

    // Return unsubscribe function
    return () => this.off(event, callback);
  }

  // Subscribe once
  once(event, callback) {
    const wrapper = (...args) => {
      callback(...args);
      this.off(event, wrapper);
    };
    this.on(event, wrapper);
  }

  // Unsubscribe from event
  off(event, callback) {
    if (!this.events[event]) return;

    this.events[event] = this.events[event].filter((cb) => cb !== callback);
  }

  // Emit event
  emit(event, ...args) {
    if (!this.events[event]) return;

    this.events[event].forEach((callback) => {
      callback(...args);
    });
  }

  // Remove all listeners
  clear(event) {
    if (event) {
      delete this.events[event];
    } else {
      this.events = {};
    }
  }
}

// Usage
const emitter = new EventEmitter();

// Subscribe
const unsubscribe = emitter.on("user:login", (user) => {
  console.log(`${user.name} logged in`);
});

emitter.on("user:logout", (user) => {
  console.log(`${user.name} logged out`);
});

// Emit events
emitter.emit("user:login", { name: "MrDib" });
emitter.emit("user:logout", { name: "MrDib" });

// Unsubscribe
unsubscribe();

// ═══════════════════════════════════════════
// Proxy Pattern - Intercept Operations
// ═══════════════════════════════════════════

// Validation proxy
const createValidatedUser = (user) => {
  return new Proxy(user, {
    set(target, property, value) {
      if (property === "age" && typeof value !== "number") {
        throw new TypeError("Age must be a number");
      }

      if (property === "email" && !value.includes("@")) {
        throw new Error("Invalid email");
      }

      target[property] = value;
      return true;
    },

    get(target, property) {
      if (property === "password") {
        return "********"; // Hide password
      }
      return target[property];
    },

    has(target, property) {
      if (property === "password") {
        return false; // Hide password property
      }
      return property in target;
    },
  });
};

// Usage
const user = createValidatedUser({
  name: "MrDib",
  email: "mrdib@example.com",
  age: 25,
  password: "secret123",
});

console.log(user.password); // "********"
console.log("password" in user); // false
// user.age = "twenty";        // TypeError!
// user.email = "invalid";     // Error!

// Caching proxy
function createCachedFetch(fn) {
  const cache = new Map();

  return new Proxy(fn, {
    apply(target, thisArg, args) {
      const key = JSON.stringify(args);

      if (cache.has(key)) {
        console.log("Returning cached result");
        return cache.get(key);
      }

      const result = target.apply(thisArg, args);
      cache.set(key, result);
      return result;
    },
  });
}

// Usage
const expensiveOperation = (n) => {
  console.log("Computing...");
  return n ** 2;
};

const cached = createCachedFetch(expensiveOperation);
cached(5); // "Computing..." + returns 25
cached(5); // "Returning cached result" + returns 25

// ═══════════════════════════════════════════
// Strategy Pattern - Interchangeable Algorithms
// ═══════════════════════════════════════════

// Payment strategies
class CreditCardPayment {
  pay(amount) {
    console.log(`Paid $${amount} with Credit Card`);
  }
}

class PayPalPayment {
  pay(amount) {
    console.log(`Paid $${amount} with PayPal`);
  }
}

class CryptoPayment {
  pay(amount) {
    console.log(`Paid $${amount} with Cryptocurrency`);
  }
}

// Payment processor
class PaymentProcessor {
  constructor(strategy) {
    this.strategy = strategy;
  }

  setStrategy(strategy) {
    this.strategy = strategy;
  }

  processPayment(amount) {
    this.strategy.pay(amount);
  }
}

// Usage
const processor = new PaymentProcessor(new CreditCardPayment());
processor.processPayment(100); // Credit Card

processor.setStrategy(new PayPalPayment());
processor.processPayment(50); // PayPal

processor.setStrategy(new CryptoPayment());
processor.processPayment(200); // Crypto

// ═══════════════════════════════════════════
// Decorator Pattern - Add Functionality
// ═══════════════════════════════════════════

// Base coffee
class Coffee {
  cost() {
    return 5;
  }

  description() {
    return "Coffee";
  }
}

// Decorators
class MilkDecorator {
  constructor(coffee) {
    this.coffee = coffee;
  }

  cost() {
    return this.coffee.cost() + 1;
  }

  description() {
    return this.coffee.description() + " + Milk";
  }
}

class SugarDecorator {
  constructor(coffee) {
    this.coffee = coffee;
  }

  cost() {
    return this.coffee.cost() + 0.5;
  }

  description() {
    return this.coffee.description() + " + Sugar";
  }
}

class WhipDecorator {
  constructor(coffee) {
    this.coffee = coffee;
  }

  cost() {
    return this.coffee.cost() + 2;
  }

  description() {
    return this.coffee.description() + " + Whip";
  }
}

// Usage
let coffee = new Coffee();
console.log(`${coffee.description()}: $${coffee.cost()}`);
// "Coffee: $5"

coffee = new MilkDecorator(coffee);
console.log(`${coffee.description()}: $${coffee.cost()}`);
// "Coffee + Milk: $6"

coffee = new SugarDecorator(coffee);
coffee = new WhipDecorator(coffee);
console.log(`${coffee.description()}: $${coffee.cost()}`);
// "Coffee + Milk + Sugar + Whip: $8.5"

// Function decorator
function logExecutionTime(target, propertyKey, descriptor) {
  const originalMethod = descriptor.value;

  descriptor.value = function (...args) {
    const start = performance.now();
    const result = originalMethod.apply(this, args);
    const end = performance.now();

    console.log(`${propertyKey} took ${(end - start).toFixed(2)}ms`);
    return result;
  };

  return descriptor;
}

class Calculator {
  @logExecutionTime
  fibonacci(n) {
    if (n <= 1) return n;
    return this.fibonacci(n - 1) + this.fibonacci(n - 2);
  }
}

// ═══════════════════════════════════════════
// Command Pattern - Encapsulate Actions
// ═══════════════════════════════════════════

// Receiver
class TextEditor {
  constructor() {
    this.text = "";
  }

  write(text) {
    this.text += text;
  }

  delete(length) {
    this.text = this.text.slice(0, -length);
  }

  getText() {
    return this.text;
  }
}

// Commands
class WriteCommand {
  constructor(editor, text) {
    this.editor = editor;
    this.text = text;
  }

  execute() {
    this.editor.write(this.text);
  }

  undo() {
    this.editor.delete(this.text.length);
  }
}

class DeleteCommand {
  constructor(editor, length) {
    this.editor = editor;
    this.length = length;
    this.deletedText = "";
  }

  execute() {
    const text = this.editor.getText();
    this.deletedText = text.slice(-this.length);
    this.editor.delete(this.length);
  }

  undo() {
    this.editor.write(this.deletedText);
  }
}

// Invoker
class CommandManager {
  constructor() {
    this.history = [];
    this.currentIndex = -1;
  }

  execute(command) {
    // Remove any commands after current index
    this.history = this.history.slice(0, this.currentIndex + 1);

    command.execute();
    this.history.push(command);
    this.currentIndex++;
  }

  undo() {
    if (this.currentIndex < 0) return;

    const command = this.history[this.currentIndex];
    command.undo();
    this.currentIndex--;
  }

  redo() {
    if (this.currentIndex >= this.history.length - 1) return;

    this.currentIndex++;
    const command = this.history[this.currentIndex];
    command.execute();
  }
}

// Usage
const editor = new TextEditor();
const manager = new CommandManager();

manager.execute(new WriteCommand(editor, "Hello "));
manager.execute(new WriteCommand(editor, "World"));
console.log(editor.getText()); // "Hello World"

manager.undo();
console.log(editor.getText()); // "Hello "

manager.redo();
console.log(editor.getText()); // "Hello World"

manager.execute(new DeleteCommand(editor, 5));
console.log(editor.getText()); // "Hello "
```

> **💡 Pro Tip:** Master these patterns! They're used everywhere in modern JavaScript frameworks and libraries. React Hooks = Strategy Pattern, Redux = Command Pattern + Observer!

---

<div align="center">

## ⚙️ Performance Optimization

</div>

### Making JavaScript Blazing Fast ⚡

```javascript
// ═══════════════════════════════════════════
// Debounce - Limit Function Calls
// ═══════════════════════════════════════════

function debounce(func, wait) {
  let timeoutId;

  return function debounced(...args) {
    const context = this;

    clearTimeout(timeoutId);

    timeoutId = setTimeout(() => {
      func.apply(context, args);
    }, wait);
  };
}

// Usage: Search input
const searchInput = document.getElementById("search");

const search = debounce(async (query) => {
  const results = await fetch(`/api/search?q=${query}`);
  displayResults(await results.json());
}, 300);

searchInput.addEventListener("input", (e) => {
  search(e.target.value);
});

// With immediate execution option
function debounceImmediate(func, wait, immediate = false) {
  let timeoutId;

  return function (...args) {
    const context = this;
    const callNow = immediate && !timeoutId;

    clearTimeout(timeoutId);

    timeoutId = setTimeout(() => {
      timeoutId = null;
      if (!immediate) {
        func.apply(context, args);
      }
    }, wait);

    if (callNow) {
      func.apply(context, args);
    }
  };
}

// ═══════════════════════════════════════════
// Throttle - Rate Limiting
// ═══════════════════════════════════════════

function throttle(func, limit) {
  let inThrottle;
  let lastFunc;
  let lastRan;

  return function (...args) {
    const context = this;

    if (!inThrottle) {
      func.apply(context, args);
      lastRan = Date.now();
      inThrottle = true;
    } else {
      clearTimeout(lastFunc);
      lastFunc = setTimeout(() => {
        if (Date.now() - lastRan >= limit) {
          func.apply(context, args);
          lastRan = Date.now();
        }
      }, Math.max(limit - (Date.now() - lastRan), 0));
    }
  };
}

// Usage: Scroll events
const handleScroll = throttle(() => {
  console.log("Scrolling...");
  updateScrollPosition();
}, 100);

window.addEventListener("scroll", handleScroll);

// ═══════════════════════════════════════════
// Memoization - Cache Expensive Operations
// ═══════════════════════════════════════════

function memoize(fn) {
  const cache = new Map();

  return function (...args) {
    const key = JSON.stringify(args);

    if (cache.has(key)) {
      console.log("Returning cached result");
      return cache.get(key);
    }

    const result = fn.apply(this, args);
    cache.set(key, result);
    return result;
  };
}

// Usage: Expensive calculation
const fibonacci = memoize(function fib(n) {
  if (n <= 1) return n;
  return fib(n - 1) + fib(n - 2);
});

console.time("First call");
fibonacci(40); // Takes time
console.timeEnd("First call");

console.time("Second call");
fibonacci(40); // Instant!
console.timeEnd("Second call");

// With expiration
function memoizeWithExpiry(fn, ttl = 60000) {
  const cache = new Map();

  return function (...args) {
    const key = JSON.stringify(args);
    const cached = cache.get(key);

    if (cached && Date.now() - cached.timestamp < ttl) {
      return cached.value;
    }

    const result = fn.apply(this, args);
    cache.set(key, {
      value: result,
      timestamp: Date.now(),
    });

    return result;
  };
}

// ═══════════════════════════════════════════
// Lazy Loading - Load on Demand
// ═══════════════════════════════════════════

// Dynamic imports
async function loadChart() {
  const { Chart } = await import("chart.js");
  return new Chart(ctx, config);
}

// Load only when needed
button.addEventListener("click", async () => {
  const module = await import("./heavy-module.js");
  module.initialize();
});

// Intersection Observer for images
const lazyLoadImages = () => {
  const images = document.querySelectorAll("img[data-src]");

  const imageObserver = new IntersectionObserver((entries, observer) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        const img = entry.target;
        img.src = img.dataset.src;
        img.removeAttribute("data-src");
        observer.unobserve(img);
      }
    });
  });

  images.forEach((img) => imageObserver.observe(img));
};

// Lazy load on scroll
const lazyLoadSections = () => {
  const sections = document.querySelectorAll("[data-lazy]");

  const sectionObserver = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          const section = entry.target;
          section.classList.add("loaded");
          sectionObserver.unobserve(section);
        }
      });
    },
    {
      threshold: 0.1,
      rootMargin: "50px",
    }
  );

  sections.forEach((section) => sectionObserver.observe(section));
};

// ═══════════════════════════════════════════
// Web Workers - Offload Heavy Computation
// ═══════════════════════════════════════════

// worker.js
self.addEventListener("message", (e) => {
  const { data, operation } = e.data;

  let result;

  switch (operation) {
    case "fibonacci":
      result = fibonacci(data);
      break;
    case "primeNumbers":
      result = calculatePrimes(data);
      break;
  }

  self.postMessage({ result });
});

// main.js
const worker = new Worker("worker.js");

worker.addEventListener("message", (e) => {
  console.log("Result from worker:", e.data.result);
});

worker.addEventListener("error", (error) => {
  console.error("Worker error:", error);
});

// Send work to worker
worker.postMessage({
  operation: "fibonacci",
  data: 40,
});

// Terminate when done
// worker.terminate();

// ═══════════════════════════════════════════
// Virtual Scrolling - Handle Large Lists
// ═══════════════════════════════════════════

class VirtualScroller {
  constructor(container, items, itemHeight) {
    this.container = container;
    this.items = items;
    this.itemHeight = itemHeight;
    this.visibleItems = Math.ceil(container.clientHeight / itemHeight);
    this.totalHeight = items.length * itemHeight;

    this.init();
  }

  init() {
    // Create scrollable container
    this.container.style.height = `${this.totalHeight}px`;
    this.container.style.position = "relative";

    // Create viewport
    this.viewport = document.createElement("div");
    this.viewport.style.position = "absolute";
    this.viewport.style.top = "0";
    this.container.appendChild(this.viewport);

    // Render initial items
    this.render(0);

    // Handle scroll
    this.container.addEventListener("scroll", () => {
      const scrollTop = this.container.scrollTop;
      const startIndex = Math.floor(scrollTop / this.itemHeight);
      this.render(startIndex);
    });
  }

  render(startIndex) {
    const endIndex = Math.min(
      startIndex + this.visibleItems + 1,
      this.items.length
    );

    const visibleItems = this.items.slice(startIndex, endIndex);

    this.viewport.style.transform = `translateY(${
      startIndex * this.itemHeight
    }px)`;

    this.viewport.innerHTML = visibleItems
      .map((item) => `<div style="height: ${this.itemHeight}px">${item}</div>`)
      .join("");
  }
}

// Usage
const items = Array.from({ length: 10000 }, (_, i) => `Item ${i + 1}`);
const scroller = new VirtualScroller(
  document.getElementById("container"),
  items,
  50
);

// ═══════════════════════════════════════════
// Request Animation Frame - Smooth Animations
// ═══════════════════════════════════════════

// Bad: Using setInterval
function animateBad() {
  let position = 0;
  setInterval(() => {
    position += 1;
    element.style.left = position + "px";
  }, 16); // ~60fps
}

// Good: Using requestAnimationFrame
function animateGood() {
  let position = 0;

  function step() {
    position += 1;
    element.style.left = position + "px";

    if (position < 500) {
      requestAnimationFrame(step);
    }
  }

  requestAnimationFrame(step);
}

// With timing control
function animate(duration, draw) {
  const start = performance.now();

  requestAnimationFrame(function step(currentTime) {
    const elapsed = currentTime - start;
    const progress = Math.min(elapsed / duration, 1);

    draw(progress);

    if (progress < 1) {
      requestAnimationFrame(step);
    }
  });
}

// Usage
animate(1000, (progress) => {
  element.style.left = progress * 500 + "px";
});

// ═══════════════════════════════════════════
// Object Pooling - Reuse Objects
// ═══════════════════════════════════════════

class ObjectPool {
  constructor(factory, reset, initialSize = 10) {
    this.factory = factory;
    this.reset = reset;
    this.pool = [];
    this.active = new Set();

    // Pre-create objects
    for (let i = 0; i < initialSize; i++) {
      this.pool.push(this.factory());
    }
  }

  acquire() {
    let obj;

    if (this.pool.length > 0) {
      obj = this.pool.pop();
    } else {
      obj = this.factory();
    }

    this.active.add(obj);
    return obj;
  }

  release(obj) {
    if (!this.active.has(obj)) return;

    this.active.delete(obj);
    this.reset(obj);
    this.pool.push(obj);
  }

  clear() {
    this.pool = [];
    this.active.clear();
  }

  get size() {
    return this.pool.length + this.active.size;
  }
}

// Usage: Particle system
class Particle {
  constructor() {
    this.x = 0;
    this.y = 0;
    this.vx = 0;
    this.vy = 0;
  }

  update() {
    this.x += this.vx;
    this.y += this.vy;
  }
}

const particlePool = new ObjectPool(
  () => new Particle(),
  (particle) => {
    particle.x = 0;
    particle.y = 0;
    particle.vx = 0;
    particle.vy = 0;
  },
  100
);

// Create particle
const particle = particlePool.acquire();
particle.x = 100;
particle.y = 200;

// Return to pool when done
particlePool.release(particle);

// ═══════════════════════════════════════════
// Performance Monitoring
// ═══════════════════════════════════════════

// Measure execution time
console.time("operation");
// ... code ...
console.timeEnd("operation");

// Performance API
const start = performance.now();
// ... code ...
const end = performance.now();
console.log(`Took ${end - start}ms`);

// Mark and measure
performance.mark("start-fetch");
await fetch("/api/data");
performance.mark("end-fetch");

performance.measure("fetch-duration", "start-fetch", "end-fetch");

const measures = performance.getEntriesByName("fetch-duration");
console.log(`Fetch took ${measures[0].duration}ms`);

// Memory usage (Chrome only)
if (performance.memory) {
  console.log({
    usedJSHeapSize: performance.memory.usedJSHeapSize,
    totalJSHeapSize: performance.memory.totalJSHeapSize,
    jsHeapSizeLimit: performance.memory.jsHeapSizeLimit,
  });
}

// Performance Observer
const observer = new PerformanceObserver((list) => {
  for (const entry of list.getEntries()) {
    console.log(`${entry.name}: ${entry.duration}ms`);
  }
});

observer.observe({ entryTypes: ["measure"] });
```

> **💡 Pro Tip:** Use Chrome DevTools Performance tab to identify bottlenecks. Profile before optimizing - "Premature optimization is the root of all evil!"

---

<div align="center">

## 🌐 Web APIs

</div>

### Browser APIs You Should Know 🔥

```javascript
// ═══════════════════════════════════════════
// Fetch API - HTTP Requests
// ═══════════════════════════════════════════

// GET request
async function getUser(id) {
  try {
    const response = await fetch(`/api/users/${id}`);

    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }

    const user = await response.json();
    return user;
  } catch (error) {
    console.error("Fetch error:", error);
  }
}

// POST request
async function createUser(userData) {
  try {
    const response = await fetch("/api/users", {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
        Authorization: "Bearer token123",
      },
      body: JSON.stringify(userData),
    });

    return await response.json();
  } catch (error) {
    console.error("Create error:", error);
  }
}

// Upload file
async function uploadFile(file) {
  const formData = new FormData();
  formData.append("file", file);

  const response = await fetch("/api/upload", {
    method: "POST",
    body: formData,
  });

  return await response.json();
}

// Abort request
const controller = new AbortController();

fetch("/api/data", {
  signal: controller.signal,
}).catch((error) => {
  if (error.name === "AbortError") {
    console.log("Request aborted");
  }
});

// Cancel after 5 seconds
setTimeout(() => controller.abort(), 5000);

// ═══════════════════════════════════════════
// Local Storage & Session Storage
// ═══════════════════════════════════════════

// Local Storage (persists)
localStorage.setItem("user", JSON.stringify({ name: "MrDib" }));
const user = JSON.parse(localStorage.getItem("user"));
localStorage.removeItem("user");
localStorage.clear();

// Session Storage (tab-scoped)
sessionStorage.setItem("token", "abc123");
const token = sessionStorage.getItem("token");
sessionStorage.removeItem("token");

// Storage event (listen for changes)
window.addEventListener("storage", (e) => {
  console.log(`${e.key} changed from ${e.oldValue} to ${e.newValue}`);
});

// Storage wrapper with expiry
class Storage {
  static set(key, value, ttl = null) {
    const item = {
      value,
      expiry: ttl ? Date.now() + ttl : null,
    };
    localStorage.setItem(key, JSON.stringify(item));
  }

  static get(key) {
    const itemStr = localStorage.getItem(key);
    if (!itemStr) return null;

    const item = JSON.parse(itemStr);

    if (item.expiry && Date.now() > item.expiry) {
      localStorage.removeItem(key);
      return null;
    }

    return item.value;
  }

  static remove(key) {
    localStorage.removeItem(key);
  }

  static clear() {
    localStorage.clear();
  }
}

// Usage
Storage.set("user", { name: "MrDib" }, 60000); // 1 minute TTL

// ═══════════════════════════════════════════
// IndexedDB - Client-side Database
// ═══════════════════════════════════════════

class Database {
  constructor(dbName, version = 1) {
    this.dbName = dbName;
    this.version = version;
    this.db = null;
  }

  async open() {
    return new Promise((resolve, reject) => {
      const request = indexedDB.open(this.dbName, this.version);

      request.onerror = () => reject(request.error);
      request.onsuccess = () => {
        this.db = request.result;
        resolve(this.db);
      };

      request.onupgradeneeded = (event) => {
        const db = event.target.result;

        if (!db.objectStoreNames.contains("users")) {
          const store = db.createObjectStore("users", {
            keyPath: "id",
            autoIncrement: true,
          });
          store.createIndex("email", "email", { unique: true });
        }
      };
    });
  }

  async add(storeName, data) {
    const transaction = this.db.transaction([storeName], "readwrite");
    const store = transaction.objectStore(storeName);

    return new Promise((resolve, reject) => {
      const request = store.add(data);
      request.onsuccess = () => resolve(request.result);
      request.onerror = () => reject(request.error);
    });
  }

  async get(storeName, key) {
    const transaction = this.db.transaction([storeName], "readonly");
    const store = transaction.objectStore(storeName);

    return new Promise((resolve, reject) => {
      const request = store.get(key);
      request.onsuccess = () => resolve(request.result);
      request.onerror = () => reject(request.error);
    });
  }

  async getAll(storeName) {
    const transaction = this.db.transaction([storeName], "readonly");
    const store = transaction.objectStore(storeName);

    return new Promise((resolve, reject) => {
      const request = store.getAll();
      request.onsuccess = () => resolve(request.result);
      request.onerror = () => reject(request.error);
    });
  }

  async delete(storeName, key) {
    const transaction = this.db.transaction([storeName], "readwrite");
    const store = transaction.objectStore(storeName);

    return new Promise((resolve, reject) => {
      const request = store.delete(key);
      request.onsuccess = () => resolve();
      request.onerror = () => reject(request.error);
    });
  }
}

// Usage
const db = new Database("myDatabase");
await db.open();

await db.add("users", { name: "MrDib", email: "mrdib@example.com" });
const users = await db.getAll("users");

// ═══════════════════════════════════════════
// Geolocation API
// ═══════════════════════════════════════════

// Get current position
if ("geolocation" in navigator) {
  navigator.geolocation.getCurrentPosition(
    (position) => {
      const { latitude, longitude } = position.coords;
      console.log(`Lat: ${latitude}, Lon: ${longitude}`);
    },
    (error) => {
      console.error("Geolocation error:", error.message);
    },
    {
      enableHighAccuracy: true,
      timeout: 5000,
      maximumAge: 0,
    }
  );
}

// Watch position (continuous tracking)
const watchId = navigator.geolocation.watchPosition(
  (position) => {
    updateMap(position.coords);
  },
  (error) => console.error(error)
);

// Stop watching
navigator.geolocation.clearWatch(watchId);

// ═══════════════════════════════════════════
// Notification API
// ═══════════════════════════════════════════

// Request permission
async function requestNotificationPermission() {
  if (!("Notification" in window)) {
    console.log("Notifications not supported");
    return false;
  }

  const permission = await Notification.requestPermission();
  return permission === "granted";
}

// Show notification
async function showNotification(title, options = {}) {
  if (await requestNotificationPermission()) {
    new Notification(title, {
      body: options.body || "",
      icon: options.icon || "/icon.png",
      badge: options.badge || "/badge.png",
      tag: options.tag || "default",
      requireInteraction: options.requireInteraction || false,
      ...options,
    });
  }
}

// Usage
showNotification("New Message", {
  body: "You have a new message from MrDib",
  icon: "/avatar.png",
  tag: "message",
});

// ═══════════════════════════════════════════
// Clipboard API
// ═══════════════════════════════════════════

// Copy to clipboard
async function copyToClipboard(text) {
  try {
    await navigator.clipboard.writeText(text);
    console.log("Copied to clipboard");
  } catch (error) {
    console.error("Copy failed:", error);
  }
}

// Read from clipboard
async function readFromClipboard() {
  try {
    const text = await navigator.clipboard.readText();
    return text;
  } catch (error) {
    console.error("Read failed:", error);
  }
}

// Copy button
button.addEventListener("click", () => {
  copyToClipboard("Hello, World!");
});

// ═══════════════════════════════════════════
// Intersection Observer - Lazy Loading
// ═══════════════════════════════════════════

const observer = new IntersectionObserver(
  (entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        entry.target.classList.add("visible");
        observer.unobserve(entry.target);
      }
    });
  },
  {
    threshold: 0.1,
    rootMargin: "50px",
  }
);

// Observe elements
document.querySelectorAll(".lazy").forEach((el) => {
  observer.observe(el);
});

// ═══════════════════════════════════════════
// Resize Observer - Responsive Components
// ═══════════════════════════════════════════

const resizeObserver = new ResizeObserver((entries) => {
  entries.forEach((entry) => {
    const { width, height } = entry.contentRect;
    console.log(`Element resized to ${width}x${height}`);
  });
});

resizeObserver.observe(document.getElementById("container"));

// ═══════════════════════════════════════════
// Mutation Observer - DOM Changes
// ═══════════════════════════════════════════

const mutationObserver = new MutationObserver((mutations) => {
  mutations.forEach((mutation) => {
    console.log("DOM changed:", mutation.type);
  });
});

mutationObserver.observe(document.body, {
  childList: true,
  subtree: true,
  attributes: true,
  characterData: true,
});

// ═══════════════════════════════════════════
// Web Speech API
// ═══════════════════════════════════════════

// Text to Speech
function speak(text) {
  const utterance = new SpeechSynthesisUtterance(text);
  utterance.lang = "en-US";
  utterance.rate = 1;
  utterance.pitch = 1;

  speechSynthesis.speak(utterance);
}

speak("Hello, I am a robot");

// Speech to Text
const recognition = new (window.SpeechRecognition ||
  window.webkitSpeechRecognition)();
recognition.lang = "en-US";
recognition.continuous = false;

recognition.onresult = (event) => {
  const transcript = event.results[0][0].transcript;
  console.log("You said:", transcript);
};

recognition.start();

// ═══════════════════════════════════════════
// Page Visibility API
// ═══════════════════════════════════════════

document.addEventListener("visibilitychange", () => {
  if (document.hidden) {
    console.log("Page is hidden");
    pauseVideo();
  } else {
    console.log("Page is visible");
    playVideo();
  }
});

// ═══════════════════════════════════════════
// Network Information API
// ═══════════════════════════════════════════

if ("connection" in navigator) {
  const connection = navigator.connection;

  console.log("Connection type:", connection.effectiveType);
  console.log("Downlink:", connection.downlink);
  console.log("RTT:", connection.rtt);

  connection.addEventListener("change", () => {
    console.log("Connection changed to:", connection.effectiveType);
  });
}

// ═══════════════════════════════════════════
// Battery Status API
// ═══════════════════════════════════════════

if ("getBattery" in navigator) {
  navigator.getBattery().then((battery) => {
    console.log("Battery level:", battery.level * 100 + "%");
    console.log("Charging:", battery.charging);

    battery.addEventListener("levelchange", () => {
      console.log("Battery level changed to:", battery.level * 100 + "%");
    });
  });
}
```

> **💡 Pro Tip:** Always check browser compatibility with `if ("feature" in window)` before using modern APIs. Use [Can I Use](https://caniuse.com/) for browser support info!

Let me know when you're ready for the next sections! 🚀

````markdown
---

<div align="center">

## 🎯 Design Patterns

</div>

### Common JavaScript Design Patterns 🏗️

```javascript
// ═══════════════════════════════════════════
// Module Pattern - Encapsulation
// ═══════════════════════════════════════════

const UserModule = (() => {
  // Private variables
  let users = [];
  let currentId = 1;

  // Private functions
  function validateEmail(email) {
    return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
  }

  function generateId() {
    return currentId++;
  }

  // Public API
  return {
    addUser(name, email) {
      if (!validateEmail(email)) {
        throw new Error("Invalid email");
      }

      const user = {
        id: generateId(),
        name,
        email,
        createdAt: new Date(),
      };

      users.push(user);
      return user;
    },

    getUser(id) {
      return users.find((u) => u.id === id);
    },

    getAllUsers() {
      return [...users]; // Return copy
    },

    updateUser(id, updates) {
      const user = this.getUser(id);
      if (!user) throw new Error("User not found");

      Object.assign(user, updates);
      return user;
    },

    deleteUser(id) {
      const index = users.findIndex((u) => u.id === id);
      if (index === -1) throw new Error("User not found");

      return users.splice(index, 1)[0];
    },

    getUserCount() {
      return users.length;
    },
  };
})();

// Usage
const user = UserModule.addUser("MrDib", "mrdib@example.com");
console.log(UserModule.getAllUsers());

// ═══════════════════════════════════════════
// Factory Pattern - Object Creation
// ═══════════════════════════════════════════

class User {
  constructor(name, email, role) {
    this.name = name;
    this.email = email;
    this.role = role;
  }

  getPermissions() {
    return ["read"];
  }
}

class AdminUser extends User {
  constructor(name, email) {
    super(name, email, "admin");
  }

  getPermissions() {
    return ["read", "write", "delete", "manage"];
  }
}

class ModeratorUser extends User {
  constructor(name, email) {
    super(name, email, "moderator");
  }

  getPermissions() {
    return ["read", "write", "moderate"];
  }
}

// Factory
class UserFactory {
  static createUser(type, name, email) {
    switch (type) {
      case "admin":
        return new AdminUser(name, email);
      case "moderator":
        return new ModeratorUser(name, email);
      case "user":
      default:
        return new User(name, email, "user");
    }
  }
}

// Usage
const admin = UserFactory.createUser("admin", "MrDib", "admin@example.com");
const user = UserFactory.createUser("user", "Alice", "alice@example.com");

console.log(admin.getPermissions()); // ["read", "write", "delete", "manage"]
console.log(user.getPermissions()); // ["read"]

// ═══════════════════════════════════════════
// Singleton Pattern - Single Instance
// ═══════════════════════════════════════════

class Database {
  constructor() {
    if (Database.instance) {
      return Database.instance;
    }

    this.connection = null;
    this.data = [];
    Database.instance = this;
  }

  connect() {
    if (!this.connection) {
      this.connection = "Connected to DB";
      console.log("Database connected");
    }
    return this.connection;
  }

  query(sql) {
    console.log(`Executing: ${sql}`);
    return this.data;
  }

  disconnect() {
    this.connection = null;
    console.log("Database disconnected");
  }
}

// Usage
const db1 = new Database();
const db2 = new Database();

console.log(db1 === db2); // true (same instance)

// Modern approach with ES6
class DatabaseModern {
  static #instance = null;

  constructor() {
    if (DatabaseModern.#instance) {
      return DatabaseModern.#instance;
    }
    DatabaseModern.#instance = this;
  }

  static getInstance() {
    if (!DatabaseModern.#instance) {
      DatabaseModern.#instance = new DatabaseModern();
    }
    return DatabaseModern.#instance;
  }
}

// ═══════════════════════════════════════════
// Observer Pattern - Event System
// ═══════════════════════════════════════════

class EventEmitter {
  constructor() {
    this.events = {};
  }

  // Subscribe to event
  on(event, callback) {
    if (!this.events[event]) {
      this.events[event] = [];
    }
    this.events[event].push(callback);

    // Return unsubscribe function
    return () => this.off(event, callback);
  }

  // Subscribe once
  once(event, callback) {
    const wrapper = (...args) => {
      callback(...args);
      this.off(event, wrapper);
    };
    this.on(event, wrapper);
  }

  // Unsubscribe from event
  off(event, callback) {
    if (!this.events[event]) return;

    this.events[event] = this.events[event].filter((cb) => cb !== callback);
  }

  // Emit event
  emit(event, ...args) {
    if (!this.events[event]) return;

    this.events[event].forEach((callback) => {
      callback(...args);
    });
  }

  // Remove all listeners
  clear(event) {
    if (event) {
      delete this.events[event];
    } else {
      this.events = {};
    }
  }
}

// Usage
const emitter = new EventEmitter();

// Subscribe
const unsubscribe = emitter.on("user:login", (user) => {
  console.log(`${user.name} logged in`);
});

emitter.on("user:logout", (user) => {
  console.log(`${user.name} logged out`);
});

// Emit events
emitter.emit("user:login", { name: "MrDib" });
emitter.emit("user:logout", { name: "MrDib" });

// Unsubscribe
unsubscribe();

// ═══════════════════════════════════════════
// Proxy Pattern - Intercept Operations
// ═══════════════════════════════════════════

// Validation proxy
const createValidatedUser = (user) => {
  return new Proxy(user, {
    set(target, property, value) {
      if (property === "age" && typeof value !== "number") {
        throw new TypeError("Age must be a number");
      }

      if (property === "email" && !value.includes("@")) {
        throw new Error("Invalid email");
      }

      target[property] = value;
      return true;
    },

    get(target, property) {
      if (property === "password") {
        return "********"; // Hide password
      }
      return target[property];
    },

    has(target, property) {
      if (property === "password") {
        return false; // Hide password property
      }
      return property in target;
    },
  });
};

// Usage
const user = createValidatedUser({
  name: "MrDib",
  email: "mrdib@example.com",
  age: 25,
  password: "secret123",
});

console.log(user.password); // "********"
console.log("password" in user); // false
// user.age = "twenty";        // TypeError!
// user.email = "invalid";     // Error!

// Caching proxy
function createCachedFetch(fn) {
  const cache = new Map();

  return new Proxy(fn, {
    apply(target, thisArg, args) {
      const key = JSON.stringify(args);

      if (cache.has(key)) {
        console.log("Returning cached result");
        return cache.get(key);
      }

      const result = target.apply(thisArg, args);
      cache.set(key, result);
      return result;
    },
  });
}

// Usage
const expensiveOperation = (n) => {
  console.log("Computing...");
  return n ** 2;
};

const cached = createCachedFetch(expensiveOperation);
cached(5); // "Computing..." + returns 25
cached(5); // "Returning cached result" + returns 25

// ═══════════════════════════════════════════
// Strategy Pattern - Interchangeable Algorithms
// ═══════════════════════════════════════════

// Payment strategies
class CreditCardPayment {
  pay(amount) {
    console.log(`Paid $${amount} with Credit Card`);
  }
}

class PayPalPayment {
  pay(amount) {
    console.log(`Paid $${amount} with PayPal`);
  }
}

class CryptoPayment {
  pay(amount) {
    console.log(`Paid $${amount} with Cryptocurrency`);
  }
}

// Payment processor
class PaymentProcessor {
  constructor(strategy) {
    this.strategy = strategy;
  }

  setStrategy(strategy) {
    this.strategy = strategy;
  }

  processPayment(amount) {
    this.strategy.pay(amount);
  }
}

// Usage
const processor = new PaymentProcessor(new CreditCardPayment());
processor.processPayment(100); // Credit Card

processor.setStrategy(new PayPalPayment());
processor.processPayment(50); // PayPal

processor.setStrategy(new CryptoPayment());
processor.processPayment(200); // Crypto

// ═══════════════════════════════════════════
// Decorator Pattern - Add Functionality
// ═══════════════════════════════════════════

// Base coffee
class Coffee {
  cost() {
    return 5;
  }

  description() {
    return "Coffee";
  }
}

// Decorators
class MilkDecorator {
  constructor(coffee) {
    this.coffee = coffee;
  }

  cost() {
    return this.coffee.cost() + 1;
  }

  description() {
    return this.coffee.description() + " + Milk";
  }
}

class SugarDecorator {
  constructor(coffee) {
    this.coffee = coffee;
  }

  cost() {
    return this.coffee.cost() + 0.5;
  }

  description() {
    return this.coffee.description() + " + Sugar";
  }
}

class WhipDecorator {
  constructor(coffee) {
    this.coffee = coffee;
  }

  cost() {
    return this.coffee.cost() + 2;
  }

  description() {
    return this.coffee.description() + " + Whip";
  }
}

// Usage
let coffee = new Coffee();
console.log(`${coffee.description()}: $${coffee.cost()}`);
// "Coffee: $5"

coffee = new MilkDecorator(coffee);
console.log(`${coffee.description()}: $${coffee.cost()}`);
// "Coffee + Milk: $6"

coffee = new SugarDecorator(coffee);
coffee = new WhipDecorator(coffee);
console.log(`${coffee.description()}: $${coffee.cost()}`);
// "Coffee + Milk + Sugar + Whip: $8.5"

// Function decorator
function logExecutionTime(target, propertyKey, descriptor) {
  const originalMethod = descriptor.value;

  descriptor.value = function (...args) {
    const start = performance.now();
    const result = originalMethod.apply(this, args);
    const end = performance.now();

    console.log(`${propertyKey} took ${(end - start).toFixed(2)}ms`);
    return result;
  };

  return descriptor;
}

class Calculator {
  @logExecutionTime
  fibonacci(n) {
    if (n <= 1) return n;
    return this.fibonacci(n - 1) + this.fibonacci(n - 2);
  }
}

// ═══════════════════════════════════════════
// Command Pattern - Encapsulate Actions
// ═══════════════════════════════════════════

// Receiver
class TextEditor {
  constructor() {
    this.text = "";
  }

  write(text) {
    this.text += text;
  }

  delete(length) {
    this.text = this.text.slice(0, -length);
  }

  getText() {
    return this.text;
  }
}

// Commands
class WriteCommand {
  constructor(editor, text) {
    this.editor = editor;
    this.text = text;
  }

  execute() {
    this.editor.write(this.text);
  }

  undo() {
    this.editor.delete(this.text.length);
  }
}

class DeleteCommand {
  constructor(editor, length) {
    this.editor = editor;
    this.length = length;
    this.deletedText = "";
  }

  execute() {
    const text = this.editor.getText();
    this.deletedText = text.slice(-this.length);
    this.editor.delete(this.length);
  }

  undo() {
    this.editor.write(this.deletedText);
  }
}

// Invoker
class CommandManager {
  constructor() {
    this.history = [];
    this.currentIndex = -1;
  }

  execute(command) {
    // Remove any commands after current index
    this.history = this.history.slice(0, this.currentIndex + 1);

    command.execute();
    this.history.push(command);
    this.currentIndex++;
  }

  undo() {
    if (this.currentIndex < 0) return;

    const command = this.history[this.currentIndex];
    command.undo();
    this.currentIndex--;
  }

  redo() {
    if (this.currentIndex >= this.history.length - 1) return;

    this.currentIndex++;
    const command = this.history[this.currentIndex];
    command.execute();
  }
}

// Usage
const editor = new TextEditor();
const manager = new CommandManager();

manager.execute(new WriteCommand(editor, "Hello "));
manager.execute(new WriteCommand(editor, "World"));
console.log(editor.getText()); // "Hello World"

manager.undo();
console.log(editor.getText()); // "Hello "

manager.redo();
console.log(editor.getText()); // "Hello World"

manager.execute(new DeleteCommand(editor, 5));
console.log(editor.getText()); // "Hello "
```
````

> **💡 Pro Tip:** Master these patterns! They're used everywhere in modern JavaScript frameworks and libraries. React Hooks = Strategy Pattern, Redux = Command Pattern + Observer!

---

<div align="center">

## ⚙️ Performance Optimization

</div>

### Making JavaScript Blazing Fast ⚡

```javascript
// ═══════════════════════════════════════════
// Debounce - Limit Function Calls
// ═══════════════════════════════════════════

function debounce(func, wait) {
  let timeoutId;

  return function debounced(...args) {
    const context = this;

    clearTimeout(timeoutId);

    timeoutId = setTimeout(() => {
      func.apply(context, args);
    }, wait);
  };
}

// Usage: Search input
const searchInput = document.getElementById("search");

const search = debounce(async (query) => {
  const results = await fetch(`/api/search?q=${query}`);
  displayResults(await results.json());
}, 300);

searchInput.addEventListener("input", (e) => {
  search(e.target.value);
});

// With immediate execution option
function debounceImmediate(func, wait, immediate = false) {
  let timeoutId;

  return function (...args) {
    const context = this;
    const callNow = immediate && !timeoutId;

    clearTimeout(timeoutId);

    timeoutId = setTimeout(() => {
      timeoutId = null;
      if (!immediate) {
        func.apply(context, args);
      }
    }, wait);

    if (callNow) {
      func.apply(context, args);
    }
  };
}

// ═══════════════════════════════════════════
// Throttle - Rate Limiting
// ═══════════════════════════════════════════

function throttle(func, limit) {
  let inThrottle;
  let lastFunc;
  let lastRan;

  return function (...args) {
    const context = this;

    if (!inThrottle) {
      func.apply(context, args);
      lastRan = Date.now();
      inThrottle = true;
    } else {
      clearTimeout(lastFunc);
      lastFunc = setTimeout(() => {
        if (Date.now() - lastRan >= limit) {
          func.apply(context, args);
          lastRan = Date.now();
        }
      }, Math.max(limit - (Date.now() - lastRan), 0));
    }
  };
}

// Usage: Scroll events
const handleScroll = throttle(() => {
  console.log("Scrolling...");
  updateScrollPosition();
}, 100);

window.addEventListener("scroll", handleScroll);

// ═══════════════════════════════════════════
// Memoization - Cache Expensive Operations
// ═══════════════════════════════════════════

function memoize(fn) {
  const cache = new Map();

  return function (...args) {
    const key = JSON.stringify(args);

    if (cache.has(key)) {
      console.log("Returning cached result");
      return cache.get(key);
    }

    const result = fn.apply(this, args);
    cache.set(key, result);
    return result;
  };
}

// Usage: Expensive calculation
const fibonacci = memoize(function fib(n) {
  if (n <= 1) return n;
  return fib(n - 1) + fib(n - 2);
});

console.time("First call");
fibonacci(40); // Takes time
console.timeEnd("First call");

console.time("Second call");
fibonacci(40); // Instant!
console.timeEnd("Second call");

// With expiration
function memoizeWithExpiry(fn, ttl = 60000) {
  const cache = new Map();

  return function (...args) {
    const key = JSON.stringify(args);
    const cached = cache.get(key);

    if (cached && Date.now() - cached.timestamp < ttl) {
      return cached.value;
    }

    const result = fn.apply(this, args);
    cache.set(key, {
      value: result,
      timestamp: Date.now(),
    });

    return result;
  };
}

// ═══════════════════════════════════════════
// Lazy Loading - Load on Demand
// ═══════════════════════════════════════════

// Dynamic imports
async function loadChart() {
  const { Chart } = await import("chart.js");
  return new Chart(ctx, config);
}

// Load only when needed
button.addEventListener("click", async () => {
  const module = await import("./heavy-module.js");
  module.initialize();
});

// Intersection Observer for images
const lazyLoadImages = () => {
  const images = document.querySelectorAll("img[data-src]");

  const imageObserver = new IntersectionObserver((entries, observer) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        const img = entry.target;
        img.src = img.dataset.src;
        img.removeAttribute("data-src");
        observer.unobserve(img);
      }
    });
  });

  images.forEach((img) => imageObserver.observe(img));
};

// Lazy load on scroll
const lazyLoadSections = () => {
  const sections = document.querySelectorAll("[data-lazy]");

  const sectionObserver = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          const section = entry.target;
          section.classList.add("loaded");
          sectionObserver.unobserve(section);
        }
      });
    },
    {
      threshold: 0.1,
      rootMargin: "50px",
    }
  );

  sections.forEach((section) => sectionObserver.observe(section));
};

// ═══════════════════════════════════════════
// Web Workers - Offload Heavy Computation
// ═══════════════════════════════════════════

// worker.js
self.addEventListener("message", (e) => {
  const { data, operation } = e.data;

  let result;

  switch (operation) {
    case "fibonacci":
      result = fibonacci(data);
      break;
    case "primeNumbers":
      result = calculatePrimes(data);
      break;
  }

  self.postMessage({ result });
});

// main.js
const worker = new Worker("worker.js");

worker.addEventListener("message", (e) => {
  console.log("Result from worker:", e.data.result);
});

worker.addEventListener("error", (error) => {
  console.error("Worker error:", error);
});

// Send work to worker
worker.postMessage({
  operation: "fibonacci",
  data: 40,
});

// Terminate when done
// worker.terminate();

// ═══════════════════════════════════════════
// Virtual Scrolling - Handle Large Lists
// ═══════════════════════════════════════════

class VirtualScroller {
  constructor(container, items, itemHeight) {
    this.container = container;
    this.items = items;
    this.itemHeight = itemHeight;
    this.visibleItems = Math.ceil(container.clientHeight / itemHeight);
    this.totalHeight = items.length * itemHeight;

    this.init();
  }

  init() {
    // Create scrollable container
    this.container.style.height = `${this.totalHeight}px`;
    this.container.style.position = "relative";

    // Create viewport
    this.viewport = document.createElement("div");
    this.viewport.style.position = "absolute";
    this.viewport.style.top = "0";
    this.container.appendChild(this.viewport);

    // Render initial items
    this.render(0);

    // Handle scroll
    this.container.addEventListener("scroll", () => {
      const scrollTop = this.container.scrollTop;
      const startIndex = Math.floor(scrollTop / this.itemHeight);
      this.render(startIndex);
    });
  }

  render(startIndex) {
    const endIndex = Math.min(
      startIndex + this.visibleItems + 1,
      this.items.length
    );

    const visibleItems = this.items.slice(startIndex, endIndex);

    this.viewport.style.transform = `translateY(${
      startIndex * this.itemHeight
    }px)`;

    this.viewport.innerHTML = visibleItems
      .map((item) => `<div style="height: ${this.itemHeight}px">${item}</div>`)
      .join("");
  }
}

// Usage
const items = Array.from({ length: 10000 }, (_, i) => `Item ${i + 1}`);
const scroller = new VirtualScroller(
  document.getElementById("container"),
  items,
  50
);

// ═══════════════════════════════════════════
// Request Animation Frame - Smooth Animations
// ═══════════════════════════════════════════

// Bad: Using setInterval
function animateBad() {
  let position = 0;
  setInterval(() => {
    position += 1;
    element.style.left = position + "px";
  }, 16); // ~60fps
}

// Good: Using requestAnimationFrame
function animateGood() {
  let position = 0;

  function step() {
    position += 1;
    element.style.left = position + "px";

    if (position < 500) {
      requestAnimationFrame(step);
    }
  }

  requestAnimationFrame(step);
}

// With timing control
function animate(duration, draw) {
  const start = performance.now();

  requestAnimationFrame(function step(currentTime) {
    const elapsed = currentTime - start;
    const progress = Math.min(elapsed / duration, 1);

    draw(progress);

    if (progress < 1) {
      requestAnimationFrame(step);
    }
  });
}

// Usage
animate(1000, (progress) => {
  element.style.left = progress * 500 + "px";
});

// ═══════════════════════════════════════════
// Object Pooling - Reuse Objects
// ═══════════════════════════════════════════

class ObjectPool {
  constructor(factory, reset, initialSize = 10) {
    this.factory = factory;
    this.reset = reset;
    this.pool = [];
    this.active = new Set();

    // Pre-create objects
    for (let i = 0; i < initialSize; i++) {
      this.pool.push(this.factory());
    }
  }

  acquire() {
    let obj;

    if (this.pool.length > 0) {
      obj = this.pool.pop();
    } else {
      obj = this.factory();
    }

    this.active.add(obj);
    return obj;
  }

  release(obj) {
    if (!this.active.has(obj)) return;

    this.active.delete(obj);
    this.reset(obj);
    this.pool.push(obj);
  }

  clear() {
    this.pool = [];
    this.active.clear();
  }

  get size() {
    return this.pool.length + this.active.size;
  }
}

// Usage: Particle system
class Particle {
  constructor() {
    this.x = 0;
    this.y = 0;
    this.vx = 0;
    this.vy = 0;
  }

  update() {
    this.x += this.vx;
    this.y += this.vy;
  }
}

const particlePool = new ObjectPool(
  () => new Particle(),
  (particle) => {
    particle.x = 0;
    particle.y = 0;
    particle.vx = 0;
    particle.vy = 0;
  },
  100
);

// Create particle
const particle = particlePool.acquire();
particle.x = 100;
particle.y = 200;

// Return to pool when done
particlePool.release(particle);

// ═══════════════════════════════════════════
// Performance Monitoring
// ═══════════════════════════════════════════

// Measure execution time
console.time("operation");
// ... code ...
console.timeEnd("operation");

// Performance API
const start = performance.now();
// ... code ...
const end = performance.now();
console.log(`Took ${end - start}ms`);

// Mark and measure
performance.mark("start-fetch");
await fetch("/api/data");
performance.mark("end-fetch");

performance.measure("fetch-duration", "start-fetch", "end-fetch");

const measures = performance.getEntriesByName("fetch-duration");
console.log(`Fetch took ${measures[0].duration}ms`);

// Memory usage (Chrome only)
if (performance.memory) {
  console.log({
    usedJSHeapSize: performance.memory.usedJSHeapSize,
    totalJSHeapSize: performance.memory.totalJSHeapSize,
    jsHeapSizeLimit: performance.memory.jsHeapSizeLimit,
  });
}

// Performance Observer
const observer = new PerformanceObserver((list) => {
  for (const entry of list.getEntries()) {
    console.log(`${entry.name}: ${entry.duration}ms`);
  }
});

observer.observe({ entryTypes: ["measure"] });
```

> **💡 Pro Tip:** Use Chrome DevTools Performance tab to identify bottlenecks. Profile before optimizing - "Premature optimization is the root of all evil!"

---

<div align="center">

## 🌐 Web APIs

</div>

### Browser APIs You Should Know 🔥

```javascript
// ═══════════════════════════════════════════
// Fetch API - HTTP Requests
// ═══════════════════════════════════════════

// GET request
async function getUser(id) {
  try {
    const response = await fetch(`/api/users/${id}`);

    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }

    const user = await response.json();
    return user;
  } catch (error) {
    console.error("Fetch error:", error);
  }
}

// POST request
async function createUser(userData) {
  try {
    const response = await fetch("/api/users", {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
        Authorization: "Bearer token123",
      },
      body: JSON.stringify(userData),
    });

    return await response.json();
  } catch (error) {
    console.error("Create error:", error);
  }
}

// Upload file
async function uploadFile(file) {
  const formData = new FormData();
  formData.append("file", file);

  const response = await fetch("/api/upload", {
    method: "POST",
    body: formData,
  });

  return await response.json();
}

// Abort request
const controller = new AbortController();

fetch("/api/data", {
  signal: controller.signal,
}).catch((error) => {
  if (error.name === "AbortError") {
    console.log("Request aborted");
  }
});

// Cancel after 5 seconds
setTimeout(() => controller.abort(), 5000);

// ═══════════════════════════════════════════
// Local Storage & Session Storage
// ═══════════════════════════════════════════

// Local Storage (persists)
localStorage.setItem("user", JSON.stringify({ name: "MrDib" }));
const user = JSON.parse(localStorage.getItem("user"));
localStorage.removeItem("user");
localStorage.clear();

// Session Storage (tab-scoped)
sessionStorage.setItem("token", "abc123");
const token = sessionStorage.getItem("token");
sessionStorage.removeItem("token");

// Storage event (listen for changes)
window.addEventListener("storage", (e) => {
  console.log(`${e.key} changed from ${e.oldValue} to ${e.newValue}`);
});

// Storage wrapper with expiry
class Storage {
  static set(key, value, ttl = null) {
    const item = {
      value,
      expiry: ttl ? Date.now() + ttl : null,
    };
    localStorage.setItem(key, JSON.stringify(item));
  }

  static get(key) {
    const itemStr = localStorage.getItem(key);
    if (!itemStr) return null;

    const item = JSON.parse(itemStr);

    if (item.expiry && Date.now() > item.expiry) {
      localStorage.removeItem(key);
      return null;
    }

    return item.value;
  }

  static remove(key) {
    localStorage.removeItem(key);
  }

  static clear() {
    localStorage.clear();
  }
}

// Usage
Storage.set("user", { name: "MrDib" }, 60000); // 1 minute TTL

// ═══════════════════════════════════════════
// IndexedDB - Client-side Database
// ═══════════════════════════════════════════

class Database {
  constructor(dbName, version = 1) {
    this.dbName = dbName;
    this.version = version;
    this.db = null;
  }

  async open() {
    return new Promise((resolve, reject) => {
      const request = indexedDB.open(this.dbName, this.version);

      request.onerror = () => reject(request.error);
      request.onsuccess = () => {
        this.db = request.result;
        resolve(this.db);
      };

      request.onupgradeneeded = (event) => {
        const db = event.target.result;

        if (!db.objectStoreNames.contains("users")) {
          const store = db.createObjectStore("users", {
            keyPath: "id",
            autoIncrement: true,
          });
          store.createIndex("email", "email", { unique: true });
        }
      };
    });
  }

  async add(storeName, data) {
    const transaction = this.db.transaction([storeName], "readwrite");
    const store = transaction.objectStore(storeName);

    return new Promise((resolve, reject) => {
      const request = store.add(data);
      request.onsuccess = () => resolve(request.result);
      request.onerror = () => reject(request.error);
    });
  }

  async get(storeName, key) {
    const transaction = this.db.transaction([storeName], "readonly");
    const store = transaction.objectStore(storeName);

    return new Promise((resolve, reject) => {
      const request = store.get(key);
      request.onsuccess = () => resolve(request.result);
      request.onerror = () => reject(request.error);
    });
  }

  async getAll(storeName) {
    const transaction = this.db.transaction([storeName], "readonly");
    const store = transaction.objectStore(storeName);

    return new Promise((resolve, reject) => {
      const request = store.getAll();
      request.onsuccess = () => resolve(request.result);
      request.onerror = () => reject(request.error);
    });
  }

  async delete(storeName, key) {
    const transaction = this.db.transaction([storeName], "readwrite");
    const store = transaction.objectStore(storeName);

    return new Promise((resolve, reject) => {
      const request = store.delete(key);
      request.onsuccess = () => resolve();
      request.onerror = () => reject(request.error);
    });
  }
}

// Usage
const db = new Database("myDatabase");
await db.open();

await db.add("users", { name: "MrDib", email: "mrdib@example.com" });
const users = await db.getAll("users");

// ═══════════════════════════════════════════
// Geolocation API
// ═══════════════════════════════════════════

// Get current position
if ("geolocation" in navigator) {
  navigator.geolocation.getCurrentPosition(
    (position) => {
      const { latitude, longitude } = position.coords;
      console.log(`Lat: ${latitude}, Lon: ${longitude}`);
    },
    (error) => {
      console.error("Geolocation error:", error.message);
    },
    {
      enableHighAccuracy: true,
      timeout: 5000,
      maximumAge: 0,
    }
  );
}

// Watch position (continuous tracking)
const watchId = navigator.geolocation.watchPosition(
  (position) => {
    updateMap(position.coords);
  },
  (error) => console.error(error)
);

// Stop watching
navigator.geolocation.clearWatch(watchId);

// ═══════════════════════════════════════════
// Notification API
// ═══════════════════════════════════════════

// Request permission
async function requestNotificationPermission() {
  if (!("Notification" in window)) {
    console.log("Notifications not supported");
    return false;
  }

  const permission = await Notification.requestPermission();
  return permission === "granted";
}

// Show notification
async function showNotification(title, options = {}) {
  if (await requestNotificationPermission()) {
    new Notification(title, {
      body: options.body || "",
      icon: options.icon || "/icon.png",
      badge: options.badge || "/badge.png",
      tag: options.tag || "default",
      requireInteraction: options.requireInteraction || false,
      ...options,
    });
  }
}

// Usage
showNotification("New Message", {
  body: "You have a new message from MrDib",
  icon: "/avatar.png",
  tag: "message",
});

// ═══════════════════════════════════════════
// Clipboard API
// ═══════════════════════════════════════════

// Copy to clipboard
async function copyToClipboard(text) {
  try {
    await navigator.clipboard.writeText(text);
    console.log("Copied to clipboard");
  } catch (error) {
    console.error("Copy failed:", error);
  }
}

// Read from clipboard
async function readFromClipboard() {
  try {
    const text = await navigator.clipboard.readText();
    return text;
  } catch (error) {
    console.error("Read failed:", error);
  }
}

// Copy button
button.addEventListener("click", () => {
  copyToClipboard("Hello, World!");
});

// ═══════════════════════════════════════════
// Intersection Observer - Lazy Loading
// ═══════════════════════════════════════════

const observer = new IntersectionObserver(
  (entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        entry.target.classList.add("visible");
        observer.unobserve(entry.target);
      }
    });
  },
  {
    threshold: 0.1,
    rootMargin: "50px",
  }
);

// Observe elements
document.querySelectorAll(".lazy").forEach((el) => {
  observer.observe(el);
});

// ═══════════════════════════════════════════
// Resize Observer - Responsive Components
// ═══════════════════════════════════════════

const resizeObserver = new ResizeObserver((entries) => {
  entries.forEach((entry) => {
    const { width, height } = entry.contentRect;
    console.log(`Element resized to ${width}x${height}`);
  });
});

resizeObserver.observe(document.getElementById("container"));

// ═══════════════════════════════════════════
// Mutation Observer - DOM Changes
// ═══════════════════════════════════════════

const mutationObserver = new MutationObserver((mutations) => {
  mutations.forEach((mutation) => {
    console.log("DOM changed:", mutation.type);
  });
});

mutationObserver.observe(document.body, {
  childList: true,
  subtree: true,
  attributes: true,
  characterData: true,
});

// ═══════════════════════════════════════════
// Web Speech API
// ═══════════════════════════════════════════

// Text to Speech
function speak(text) {
  const utterance = new SpeechSynthesisUtterance(text);
  utterance.lang = "en-US";
  utterance.rate = 1;
  utterance.pitch = 1;

  speechSynthesis.speak(utterance);
}

speak("Hello, I am a robot");

// Speech to Text
const recognition = new (window.SpeechRecognition ||
  window.webkitSpeechRecognition)();
recognition.lang = "en-US";
recognition.continuous = false;

recognition.onresult = (event) => {
  const transcript = event.results[0][0].transcript;
  console.log("You said:", transcript);
};

recognition.start();

// ═══════════════════════════════════════════
// Page Visibility API
// ═══════════════════════════════════════════

document.addEventListener("visibilitychange", () => {
  if (document.hidden) {
    console.log("Page is hidden");
    pauseVideo();
  } else {
    console.log("Page is visible");
    playVideo();
  }
});

// ═══════════════════════════════════════════
// Network Information API
// ═══════════════════════════════════════════

if ("connection" in navigator) {
  const connection = navigator.connection;

  console.log("Connection type:", connection.effectiveType);
  console.log("Downlink:", connection.downlink);
  console.log("RTT:", connection.rtt);

  connection.addEventListener("change", () => {
    console.log("Connection changed to:", connection.effectiveType);
  });
}

// ═══════════════════════════════════════════
// Battery Status API
// ═══════════════════════════════════════════

if ("getBattery" in navigator) {
  navigator.getBattery().then((battery) => {
    console.log("Battery level:", battery.level * 100 + "%");
    console.log("Charging:", battery.charging);

    battery.addEventListener("levelchange", () => {
      console.log("Battery level changed to:", battery.level * 100 + "%");
    });
  });
}
```

> **💡 Pro Tip:** Always check browser compatibility with `if ("feature" in window)` before using modern APIs. Use [Can I Use](https://caniuse.com/) for browser support info!

---

<div align="center">

## 🛠️ Working with DOM

</div>

### DOM Manipulation Mastery 🎨

```javascript
// ═══════════════════════════════════════════
// Selecting Elements
// ═══════════════════════════════════════════

// Single element
const element = document.getElementById("myId");
const element = document.querySelector(".my-class");
const element = document.querySelector("[data-id='123']");

// Multiple elements
const elements = document.getElementsByClassName("my-class");
const elements = document.getElementsByTagName("div");
const elements = document.querySelectorAll(".my-class");

// Modern approach (NodeList has forEach)
document.querySelectorAll(".item").forEach((item) => {
  console.log(item);
});

// Parent, children, siblings
const parent = element.parentElement;
const children = element.children;
const firstChild = element.firstElementChild;
const lastChild = element.lastElementChild;
const nextSibling = element.nextElementSibling;
const previousSibling = element.previousElementSibling;

// Closest parent matching selector
const card = element.closest(".card");

// Check if element matches selector
if (element.matches(".active")) {
  console.log("Element is active");
}

// ═══════════════════════════════════════════
// Creating & Modifying Elements
// ═══════════════════════════════════════════

// Create element
const div = document.createElement("div");
const text = document.createTextNode("Hello");
const fragment = document.createDocumentFragment();

// Set attributes
div.id = "myDiv";
div.className = "card active";
div.setAttribute("data-id", "123");
div.setAttribute("aria-label", "My card");

// Get attributes
const id = div.id;
const dataId = div.getAttribute("data-id");
const hasAttr = div.hasAttribute("data-id");

// Remove attributes
div.removeAttribute("data-id");

// Dataset API (data-* attributes)
div.dataset.userId = "123"; // Sets data-user-id="123"
div.dataset.userName = "MrDib"; // Sets data-user-name="MrDib"
console.log(div.dataset.userId); // "123"

// Content manipulation
div.textContent = "Plain text"; // No HTML parsing
div.innerHTML = "<strong>HTML</strong>"; // Parses HTML
div.innerText = "Visible text"; // Respects CSS visibility

// Modern alternative (safer than innerHTML)
div.insertAdjacentHTML("beforeend", "<span>Safe HTML</span>");

// ═══════════════════════════════════════════
// Adding/Removing Elements
// ═══════════════════════════════════════════

// Append child
parent.appendChild(child);

// Modern methods
parent.append(child); // Can append text too
parent.prepend(child); // Add at start
parent.before(child); // Add before element
parent.after(child); // Add after element

// Multiple elements
parent.append(child1, child2, "text", child3);

// Insert at specific position
parent.insertBefore(newChild, referenceChild);
parent.insertAdjacentElement("beforebegin", element);
parent.insertAdjacentElement("afterbegin", element);
parent.insertAdjacentElement("beforeend", element);
parent.insertAdjacentElement("afterend", element);

// Remove element
element.remove(); // Modern way
parent.removeChild(element); // Old way

// Replace element
parent.replaceChild(newChild, oldChild);
oldElement.replaceWith(newElement); // Modern way

// Clone element
const clone = element.cloneNode(true); // true = deep clone

// ═══════════════════════════════════════════
// CSS Class Manipulation
// ═══════════════════════════════════════════

// Add class
element.classList.add("active");
element.classList.add("active", "selected", "highlighted");

// Remove class
element.classList.remove("active");

// Toggle class
element.classList.toggle("active");
element.classList.toggle("active", true); // Force add
element.classList.toggle("active", false); // Force remove

// Replace class
element.classList.replace("old-class", "new-class");

// Check if has class
if (element.classList.contains("active")) {
  console.log("Element is active");
}

// Get all classes
const classes = [...element.classList];

// ═══════════════════════════════════════════
// Style Manipulation
// ═══════════════════════════════════════════

// Inline styles
element.style.color = "red";
element.style.backgroundColor = "blue";
element.style.fontSize = "16px";

// Multiple styles
Object.assign(element.style, {
  color: "red",
  backgroundColor: "blue",
  fontSize: "16px",
});

// CSS text
element.style.cssText = "color: red; background: blue; font-size: 16px;";

// Get computed style
const styles = window.getComputedStyle(element);
const color = styles.color;
const fontSize = styles.fontSize;

// Check if element is visible
function isVisible(element) {
  const styles = window.getComputedStyle(element);
  return (
    styles.display !== "none" &&
    styles.visibility !== "hidden" &&
    styles.opacity !== "0"
  );
}

// ═══════════════════════════════════════════
// Event Handling
// ═══════════════════════════════════════════

// Add event listener
button.addEventListener("click", handleClick);

// Event listener with options
button.addEventListener("click", handleClick, {
  once: true, // Remove after first call
  passive: true, // Won't call preventDefault()
  capture: false, // Bubble phase (default)
});

// Remove event listener
button.removeEventListener("click", handleClick);

// Event handler function
function handleClick(event) {
  event.preventDefault(); // Prevent default action
  event.stopPropagation(); // Stop bubbling
  event.stopImmediatePropagation(); // Stop other listeners

  console.log("Event type:", event.type);
  console.log("Target:", event.target);
  console.log("Current target:", event.currentTarget);
}

// Multiple events
["click", "touchstart"].forEach((eventType) => {
  button.addEventListener(eventType, handleClick);
});

// Event delegation (efficient for many elements)
document.addEventListener("click", (event) => {
  if (event.target.matches(".delete-button")) {
    deleteItem(event.target);
  }
});

// Custom events
const customEvent = new CustomEvent("userLogin", {
  detail: { userId: 123, name: "MrDib" },
  bubbles: true,
  cancelable: true,
});

element.dispatchEvent(customEvent);

// Listen for custom event
element.addEventListener("userLogin", (event) => {
  console.log("User logged in:", event.detail);
});

// ═══════════════════════════════════════════
// Form Handling
// ═══════════════════════════════════════════

const form = document.getElementById("myForm");

// Form submission
form.addEventListener("submit", (event) => {
  event.preventDefault();

  // Get form data
  const formData = new FormData(form);

  // Iterate form data
  for (const [key, value] of formData.entries()) {
    console.log(`${key}: ${value}`);
  }

  // Convert to object
  const data = Object.fromEntries(formData);

  // Send data
  fetch("/api/submit", {
    method: "POST",
    body: formData,
  });
});

// Get/Set form values
const input = document.getElementById("username");
const value = input.value;
input.value = "New value";

// Checkbox/Radio
const checkbox = document.getElementById("agree");
const isChecked = checkbox.checked;
checkbox.checked = true;

// Select dropdown
const select = document.getElementById("country");
const selectedValue = select.value;
const selectedText = select.options[select.selectedIndex].text;

// Set select value
select.value = "USA";

// Multiple select
const selectedOptions = [...select.selectedOptions].map((opt) => opt.value);

// Form validation
input.addEventListener("input", (event) => {
  if (input.validity.valid) {
    input.classList.remove("invalid");
  } else {
    input.classList.add("invalid");
  }
});

// Check validity
if (form.checkValidity()) {
  console.log("Form is valid");
} else {
  console.log("Form has errors");
}

// Custom validation
input.setCustomValidity("This field is required");
input.reportValidity(); // Show error message

// Clear custom validation
input.setCustomValidity("");

// ═══════════════════════════════════════════
// Measurements & Positions
// ═══════════════════════════════════════════

// Element dimensions
const width = element.offsetWidth; // Including padding & border
const height = element.offsetHeight;
const clientWidth = element.clientWidth; // Excluding border
const clientHeight = element.clientHeight;
const scrollWidth = element.scrollWidth; // Total scrollable width
const scrollHeight = element.scrollHeight;

// Element position
const rect = element.getBoundingClientRect();
console.log({
  top: rect.top,
  right: rect.right,
  bottom: rect.bottom,
  left: rect.left,
  width: rect.width,
  height: rect.height,
  x: rect.x,
  y: rect.y,
});

// Offset from parent
const offsetTop = element.offsetTop;
const offsetLeft = element.offsetLeft;

// Scroll position
const scrollTop = element.scrollTop;
const scrollLeft = element.scrollLeft;

// Scroll to position
element.scrollTo(0, 100);
element.scrollTo({ top: 100, behavior: "smooth" });

// Scroll into view
element.scrollIntoView();
element.scrollIntoView({ behavior: "smooth", block: "center" });

// Window dimensions
const windowWidth = window.innerWidth;
const windowHeight = window.innerHeight;
const documentHeight = document.documentElement.scrollHeight;

// ═══════════════════════════════════════════
// Practical DOM Utilities
// ═══════════════════════════════════════════

// Check if element is in viewport
function isInViewport(element) {
  const rect = element.getBoundingClientRect();
  return (
    rect.top >= 0 &&
    rect.left >= 0 &&
    rect.bottom <= window.innerHeight &&
    rect.right <= window.innerWidth
  );
}

// Wait for element to exist
function waitForElement(selector) {
  return new Promise((resolve) => {
    if (document.querySelector(selector)) {
      return resolve(document.querySelector(selector));
    }

    const observer = new MutationObserver(() => {
      if (document.querySelector(selector)) {
        resolve(document.querySelector(selector));
        observer.disconnect();
      }
    });

    observer.observe(document.body, {
      childList: true,
      subtree: true,
    });
  });
}

// Usage
const element = await waitForElement(".dynamic-element");

// Smooth scroll to element
function smoothScrollTo(element) {
  element.scrollIntoView({
    behavior: "smooth",
    block: "start",
  });
}

// Get all parents until root
function getParents(element) {
  const parents = [];
  while (element.parentElement) {
    parents.push(element.parentElement);
    element = element.parentElement;
  }
  return parents;
}

// Delegate event handling
function delegate(element, eventType, selector, handler) {
  element.addEventListener(eventType, (event) => {
    if (event.target.matches(selector)) {
      handler.call(event.target, event);
    }
  });
}

// Usage
delegate(document, "click", ".button", function (event) {
  console.log("Button clicked:", this);
});

// Create element with properties
function createElement(tag, props = {}, children = []) {
  const element = document.createElement(tag);

  Object.entries(props).forEach(([key, value]) => {
    if (key === "className") {
      element.className = value;
    } else if (key === "style") {
      Object.assign(element.style, value);
    } else if (key.startsWith("data")) {
      const dataKey = key.slice(4).toLowerCase();
      element.dataset[dataKey] = value;
    } else {
      element[key] = value;
    }
  });

  children.forEach((child) => {
    if (typeof child === "string") {
      element.appendChild(document.createTextNode(child));
    } else {
      element.appendChild(child);
    }
  });

  return element;
}

// Usage
const card = createElement(
  "div",
  {
    className: "card",
    dataId: "123",
    style: { padding: "20px" },
  },
  [createElement("h2", {}, ["Title"]), createElement("p", {}, ["Description"])]
);

// Batch DOM updates (performance)
function batchDOMUpdates(callback) {
  const fragment = document.createDocumentFragment();
  callback(fragment);
  document.body.appendChild(fragment);
}

// Usage
batchDOMUpdates((fragment) => {
  for (let i = 0; i < 1000; i++) {
    const div = document.createElement("div");
    div.textContent = `Item ${i}`;
    fragment.appendChild(div);
  }
});
```

> **💡 Pro Tip:** Use `querySelector` and `querySelectorAll` for flexibility. Use `DocumentFragment` for batch DOM operations to improve performance!

---

<div align="center">

## 🔒 Error Handling

</div>

### Robust Error Management 🛡️

```javascript
// ═══════════════════════════════════════════
// Try/Catch/Finally
// ═══════════════════════════════════════════

try {
  // Code that might throw error
  const result = riskyOperation();
} catch (error) {
  // Handle error
  console.error("Error occurred:", error.message);
} finally {
  // Always runs (cleanup)
  cleanup();
}

// Multiple error types
try {
  const data = JSON.parse(invalidJson);
} catch (error) {
  if (error instanceof SyntaxError) {
    console.error("Invalid JSON");
  } else if (error instanceof TypeError) {
    console.error("Type error");
  } else {
    console.error("Unknown error:", error);
  }
}

// ═══════════════════════════════════════════
// Throwing Errors
// ═══════════════════════════════════════════

// Throw Error
throw new Error("Something went wrong");

// Throw specific error types
throw new TypeError("Invalid type");
throw new ReferenceError("Variable not found");
throw new RangeError("Out of range");
throw new SyntaxError("Invalid syntax");

// Throw custom value
throw "Custom error message";
throw { code: 404, message: "Not found" };

// ═══════════════════════════════════════════
// Custom Error Classes
// ═══════════════════════════════════════════

class ValidationError extends Error {
  constructor(message, field) {
    super(message);
    this.name = "ValidationError";
    this.field = field;
  }
}

class NetworkError extends Error {
  constructor(message, statusCode) {
    super(message);
    this.name = "NetworkError";
    this.statusCode = statusCode;
  }
}

class AuthenticationError extends Error {
  constructor(message) {
    super(message);
    this.name = "AuthenticationError";
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

try {
  validateUser({ name: "MrDib" });
} catch (error) {
  if (error instanceof ValidationError) {
    console.error(`Validation error in ${error.field}: ${error.message}`);
  } else {
    console.error("Unknown error:", error);
  }
}

// ═══════════════════════════════════════════
// Async Error Handling
// ═══════════════════════════════════════════

// With async/await
async function fetchData() {
  try {
    const response = await fetch("/api/data");

    if (!response.ok) {
      throw new NetworkError("Failed to fetch data", response.status);
    }

    const data = await response.json();
    return data;
  } catch (error) {
    if (error instanceof NetworkError) {
      console.error(`Network error (${error.statusCode}): ${error.message}`);
    } else if (error instanceof SyntaxError) {
      console.error("Invalid JSON response");
    } else {
      console.error("Fetch failed:", error);
    }

    throw error; // Re-throw for caller to handle
  }
}

// Promise error handling
fetchData()
  .then((data) => console.log(data))
  .catch((error) => console.error("Error:", error))
  .finally(() => console.log("Cleanup"));

// ═══════════════════════════════════════════
// Error Handling Utilities
// ═══════════════════════════════════════════

// Wrapper for try-catch
async function handle(promise) {
  try {
    const data = await promise;
    return [null, data];
  } catch (error) {
    return [error, null];
  }
}

// Usage
async function getUser(id) {
  const [error, user] = await handle(fetchUser(id));

  if (error) {
    console.error("Failed to get user:", error);
    return null;
  }

  return user;
}

// Retry mechanism
async function retry(fn, retries = 3, delay = 1000) {
  for (let i = 0; i < retries; i++) {
    try {
      return await fn();
    } catch (error) {
      if (i === retries - 1) throw error;

      console.log(`Attempt ${i + 1} failed, retrying in ${delay}ms...`);
      await new Promise((resolve) => setTimeout(resolve, delay));
      delay *= 2; // Exponential backoff
    }
  }
}

// Usage
const data = await retry(() => fetch("/api/data"), 3, 1000);

// Timeout wrapper
async function timeout(promise, ms) {
  const timeoutPromise = new Promise((_, reject) => {
    setTimeout(() => reject(new Error("Operation timed out")), ms);
  });

  return Promise.race([promise, timeoutPromise]);
}

// Usage
try {
  const data = await timeout(fetchData(), 5000);
} catch (error) {
  console.error("Request timed out or failed:", error);
}

// ═══════════════════════════════════════════
// Global Error Handling
// ═══════════════════════════════════════════

// Catch uncaught errors
window.addEventListener("error", (event) => {
  console.error("Global error:", event.error);

  // Log to error tracking service
  logErrorToService({
    message: event.error.message,
    stack: event.error.stack,
    url: event.filename,
    line: event.lineno,
    column: event.colno,
  });

  // Prevent default error handling
  event.preventDefault();
});

// Catch unhandled promise rejections
window.addEventListener("unhandledrejection", (event) => {
  console.error("Unhandled promise rejection:", event.reason);

  // Log to error tracking service
  logErrorToService({
    type: "unhandledRejection",
    reason: event.reason,
    promise: event.promise,
  });

  event.preventDefault();
});

// ═══════════════════════════════════════════
// Error Logging & Monitoring
// ═══════════════════════════════════════════

class ErrorLogger {
  static logs = [];

  static log(error, context = {}) {
    const errorLog = {
      message: error.message,
      stack: error.stack,
      name: error.name,
      timestamp: new Date().toISOString(),
      userAgent: navigator.userAgent,
      url: window.location.href,
      context,
    };

    this.logs.push(errorLog);

    // Send to server
    this.sendToServer(errorLog);

    // Log to console in development
    if (process.env.NODE_ENV === "development") {
      console.error("Error logged:", errorLog);
    }
  }

  static async sendToServer(errorLog) {
    try {
      await fetch("/api/errors", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(errorLog),
      });
    } catch (error) {
      console.error("Failed to send error log:", error);
    }
  }

  static getLogs() {
    return [...this.logs];
  }

  static clear() {
    this.logs = [];
  }
}

// Usage
try {
  riskyOperation();
} catch (error) {
  ErrorLogger.log(error, {
    userId: currentUser.id,
    action: "riskyOperation",
  });
}

// ═══════════════════════════════════════════
// Defensive Programming
// ═══════════════════════════════════════════

// Input validation
function divide(a, b) {
  // Type checking
  if (typeof a !== "number" || typeof b !== "number") {
    throw new TypeError("Arguments must be numbers");
  }

  // Value validation
  if (b === 0) {
    throw new RangeError("Cannot divide by zero");
  }

  return a / b;
}

// Null checks
function processUser(user) {
  if (!user) {
    throw new Error("User is required");
  }

  if (!user.email) {
    throw new ValidationError("Email is required", "email");
  }

  // Safe navigation
  const city = user?.address?.city ?? "Unknown";

  return { ...user, city };
}

// Assertions
function assert(condition, message) {
  if (!condition) {
    throw new Error(message || "Assertion failed");
  }
}

// Usage
function calculateDiscount(price, percentage) {
  assert(price > 0, "Price must be positive");
  assert(percentage >= 0 && percentage <= 100, "Invalid percentage");

  return price * (percentage / 100);
}

// ═══════════════════════════════════════════
// Error Boundaries (React-style pattern)
// ═══════════════════════════════════════════

class SafeExecutor {
  static execute(fn, fallback, onError) {
    try {
      return fn();
    } catch (error) {
      if (onError) {
        onError(error);
      }
      return fallback;
    }
  }

  static async executeAsync(fn, fallback, onError) {
    try {
      return await fn();
    } catch (error) {
      if (onError) {
        onError(error);
      }
      return fallback;
    }
  }
}

// Usage
const result = SafeExecutor.execute(
  () => JSON.parse(invalidJson),
  {},
  (error) => console.error("Parse failed:", error)
);

const data = await SafeExecutor.executeAsync(
  () => fetchData(),
  null,
  (error) => ErrorLogger.log(error)
);
```

> **💡 Pro Tip:** Create custom error classes for better error handling. Always log errors to a monitoring service in production. Use type checking in development!

---

<div align="center">

## 🧪 Testing

</div>

### Writing Bulletproof Tests 🔬

```javascript
// ═══════════════════════════════════════════
// Unit Testing with Jest
// ═══════════════════════════════════════════

// math.js
export function add(a, b) {
  return a + b;
}

export function subtract(a, b) {
  return a - b;
}

export function multiply(a, b) {
  return a * b;
}

export function divide(a, b) {
  if (b === 0) {
    throw new Error("Cannot divide by zero");
  }
  return a / b;
}

// math.test.js
import { add, subtract, multiply, divide } from "./math";

describe("Math operations", () => {
  // Basic test
  test("adds 1 + 2 to equal 3", () => {
    expect(add(1, 2)).toBe(3);
  });

  test("subtracts 5 - 3 to equal 2", () => {
    expect(subtract(5, 3)).toBe(2);
  });

  test("multiplies 3 * 4 to equal 12", () => {
    expect(multiply(3, 4)).toBe(12);
  });

  test("divides 10 / 2 to equal 5", () => {
    expect(divide(10, 2)).toBe(5);
  });

  test("throws error when dividing by zero", () => {
    expect(() => divide(10, 0)).toThrow("Cannot divide by zero");
  });
});

// ═══════════════════════════════════════════
// Jest Matchers
// ═══════════════════════════════════════════

describe("Jest matchers", () => {
  // Equality
  test("toBe for primitive values", () => {
    expect(2 + 2).toBe(4);
  });

  test("toEqual for objects/arrays", () => {
    const data = { name: "MrDib" };
    expect(data).toEqual({ name: "MrDib" });
  });

  // Truthiness
  test("toBeNull", () => {
    expect(null).toBeNull();
  });

  test("toBeDefined", () => {
    expect("value").toBeDefined();
  });

  test("toBeUndefined", () => {
    expect(undefined).toBeUndefined();
  });

  test("toBeTruthy", () => {
    expect(1).toBeTruthy();
  });

  test("toBeFalsy", () => {
    expect(0).toBeFalsy();
  });

  // Numbers
  test("toBeGreaterThan", () => {
    expect(10).toBeGreaterThan(5);
  });

  test("toBeLessThan", () => {
    expect(5).toBeLessThan(10);
  });

  test("toBeCloseTo for floats", () => {
    expect(0.1 + 0.2).toBeCloseTo(0.3);
  });

  // Strings
  test("toMatch regex", () => {
    expect("hello@example.com").toMatch(/^\S+@\S+\.\S+$/);
  });

  // Arrays
  test("toContain", () => {
    expect([1, 2, 3]).toContain(2);
  });

  test("toHaveLength", () => {
    expect([1, 2, 3]).toHaveLength(3);
  });

  // Objects
  test("toHaveProperty", () => {
    expect({ name: "MrDib" }).toHaveProperty("name");
  });

  // Exceptions
  test("toThrow", () => {
    expect(() => {
      throw new Error("Error!");
    }).toThrow("Error!");
  });
});

// ═══════════════════════════════════════════
// Async Testing
// ═══════════════════════════════════════════

// user.js
export async function fetchUser(id) {
  const response = await fetch(`/api/users/${id}`);
  if (!response.ok) {
    throw new Error("User not found");
  }
  return response.json();
}

// user.test.js
import { fetchUser } from "./user";

describe("fetchUser", () => {
  // With async/await
  test("fetches user successfully", async () => {
    const user = await fetchUser(1);
    expect(user).toHaveProperty("name");
  });

  // With .resolves
  test("fetches user with resolves", () => {
    return expect(fetchUser(1)).resolves.toHaveProperty("name");
  });

  // With .rejects
  test("throws error for invalid id", () => {
    return expect(fetchUser(999)).rejects.toThrow("User not found");
  });

  // With done callback
  test("fetches user with done", (done) => {
    fetchUser(1).then(user => {
      expect(user).toHaveProperty("name");
      done();
    });
  });
});

// ═══════════════════════════════════════════
// Mocking
// ═══════════════════════════════════════════

// Mock function
test("mock function", () => {
  const mockFn = jest.fn();

  mockFn("arg1", "arg2");
  mockFn("arg3");

  expect(mockFn).toHaveBeenCalled();
  expect(mockFn).toHaveBeenCalledTimes(2);
  expect(mockFn).toHaveBeenCalledWith("arg1", "arg2");
  expect(mockFn).toHaveBeenLastCalledWith("arg3");
});

// Mock with return value
test("mock return value", () => {
  const mockFn = jest.fn(() => "mocked value");

  expect(mockFn()).toBe("mocked value");
});

// Mock with different return values
test("mock different returns", () => {
  const mockFn = jest.fn()
    .mockReturnValueOnce("first")
    .mockReturnValueOnce("second")
    .mockReturnValue("default");

  expect(mockFn()).toBe("first");
  expect(mockFn()).toBe("second");
  expect(mockFn()).toBe("default");
});

// Mock async function
test("mock async function", async () => {
  const mockFn = jest.fn().mockResolvedValue({ name: "MrDib" });

  const result = await mockFn();
  expect(result).toEqual({ name: "MrDib" });
});

// Mock module
jest.mock("./api");

import { fetchData } from "./api";

test("mocked module", async () => {
  fetchData.mockResolvedValue({ data: "mocked" });

  const result = await fetchData();
  expect(result).toEqual({ data: "mocked" });
});

// ═══════════════════════════════════════════
// Setup & Teardown
// ═══════════════════════════════════════════

describe("Database tests", () => {
  let db;

  // Before all tests
  beforeAll(() => {
    db = new Database();
    db.connect();
  });

  // After all tests
  afterAll(() => {
    db.disconnect();
  });

  // Before each test
  beforeEach(() => {
    db.clear();
  });

  // After each test
  afterEach(() => {
    db.reset();
  });

  test("adds user to database", () => {
    db.addUser({ name: "MrDib" });
    expect(db.getUsers()).toHaveLength(1);
  });

  test("deletes user from database", () => {
    db.addUser({ name: "MrDib" });
    db.deleteUser(1);
    expect(db.getUsers()).toHaveLength(0);
  });
});

// ═══════════════════════════════════════════
// Test Coverage
// ═══════════════════════════════════════════

// Run tests with coverage
// npm test -- --coverage

// Coverage thresholds (package.json)
{
  "jest": {
    "coverageThreshold": {
      "global": {
        "branches": 80,
        "functions": 80,
        "lines": 80,
        "statements": 80
      }
    }
  }
}

// ═══════════════════════════════════════════
// Snapshot Testing
// ═══════════════════════════════════════════

test("renders component correctly", () => {
  const component = render(<UserCard name="MrDib" age={25} />);
  expect(component).toMatchSnapshot();
});

// Update snapshots
// npm test -- -u

// ═══════════════════════════════════════════
// Integration Testing
// ═══════════════════════════════════════════

describe("User API integration", () => {
  test("creates and retrieves user", async () => {
    // Create user
    const createResponse = await fetch("/api/users", {
      method: "POST",
      body: JSON.stringify({ name: "MrDib", email: "test@example.com" })
    });
    const createdUser = await createResponse.json();

    // Retrieve user
    const getResponse = await fetch(`/api/users/${createdUser.id}`);
    const retrievedUser = await getResponse.json();

    expect(retrievedUser).toEqual(createdUser);
  });
});

// ═══════════════════════════════════════════
// E2E Testing with Playwright
// ═══════════════════════════════════════════

import { test, expect } from "@playwright/test";

test("user can login", async ({ page }) => {
  // Navigate to page
  await page.goto("https://example.com/login");

  // Fill form
  await page.fill("#username", "mrdib");
  await page.fill("#password", "password123");

  // Click button
  await page.click('button[type="submit"]');

  // Wait for navigation
  await page.waitForURL("https://example.com/dashboard");

  // Assert
  await expect(page.locator("h1")).toContainText("Dashboard");
});

test("displays error for invalid credentials", async ({ page }) => {
  await page.goto("https://example.com/login");

  await page.fill("#username", "invalid");
  await page.fill("#password", "wrong");
  await page.click('button[type="submit"]');

  await expect(page.locator(".error")).toContainText("Invalid credentials");
});
```

> **💡 Pro Tip:** Write tests as you code (TDD), not after. Aim for 80%+ coverage. Mock external dependencies. Test behavior, not implementation!

---

<div align="center">

## 💡 Best Practices

</div>

### JavaScript Best Practices & Style Guide 📋

```javascript
// ═══════════════════════════════════════════
// 1. Variable Declarations
// ═══════════════════════════════════════════

// ❌ Bad
var name = "MrDib";
var age = 25;
var isActive = true;

// ✅ Good
const name = "MrDib";
const age = 25;
let isActive = true;

// Use const by default, let only when reassigning
const users = [];
users.push({ name: "Alice" }); // ✅ OK (mutating, not reassigning)

let counter = 0;
counter += 1; // ✅ OK (reassigning)

// ═══════════════════════════════════════════
// 2. Naming Conventions
// ═══════════════════════════════════════════

// ❌ Bad
const u = getUser();
const dt = new Date();
const fn = () => {};

// ✅ Good
const user = getUser();
const currentDate = new Date();
const fetchUserData = () => {};

// Constants
const MAX_RETRIES = 3;
const API_BASE_URL = "https://api.example.com";

// Classes
class UserManager {}
class PaymentProcessor {}

// Private fields
class User {
  #privateField = "secret";
}

// Boolean variables
const isActive = true;
const hasPermission = false;
const canEdit = true;

// ═══════════════════════════════════════════
// 3. Functions
// ═══════════════════════════════════════════

// ❌ Bad - Multiple responsibilities
function handleUser(user) {
  validateUser(user);
  saveToDatabase(user);
  sendEmail(user);
  updateCache(user);
}

// ✅ Good - Single responsibility
function validateUser(user) {
  if (!user.email) throw new Error("Email required");
  if (!user.name) throw new Error("Name required");
}

function saveUser(user) {
  return database.save(user);
}

function notifyUser(user) {
  return emailService.send(user.email, "Welcome!");
}

// ❌ Bad - Too many parameters
function createUser(name, email, age, address, phone, role, status) {
  // ...
}

// ✅ Good - Use object parameter
function createUser({ name, email, age, address, phone, role, status }) {
  // ...
}

// ❌ Bad - Callback hell
getData(function (a) {
  getMoreData(a, function (b) {
    getEvenMoreData(b, function (c) {
      console.log(c);
    });
  });
});

// ✅ Good - Async/await
async function getAllData() {
  const a = await getData();
  const b = await getMoreData(a);
  const c = await getEvenMoreData(b);
  return c;
}

// ═══════════════════════════════════════════
// 4. Object & Array Manipulation
// ═══════════════════════════════════════════

// ❌ Bad - Direct mutation
const user = { name: "MrDib", age: 25 };
user.age = 26;

const numbers = [1, 2, 3];
numbers.push(4);

// ✅ Good - Immutable updates
const updatedUser = { ...user, age: 26 };
const newNumbers = [...numbers, 4];

// Array operations
// ❌ Bad
const doubled = [];
for (let i = 0; i < numbers.length; i++) {
  doubled.push(numbers[i] * 2);
}

// ✅ Good
const doubled = numbers.map((n) => n * 2);
const evens = numbers.filter((n) => n % 2 === 0);
const sum = numbers.reduce((acc, n) => acc + n, 0);

// ═══════════════════════════════════════════
// 5. Conditionals
// ═══════════════════════════════════════════

// ❌ Bad - Nested if statements
if (user) {
  if (user.isActive) {
    if (user.hasPermission) {
      // Do something
    }
  }
}

// ✅ Good - Early returns
if (!user) return;
if (!user.isActive) return;
if (!user.hasPermission) return;

// Do something

// ❌ Bad - Multiple if-else
let status;
if (age < 18) {
  status = "minor";
} else if (age < 65) {
  status = "adult";
} else {
  status = "senior";
}

// ✅ Good - Ternary or function
const status = age < 18 ? "minor" : age < 65 ? "adult" : "senior";

// Or better, use a function
function getAgeStatus(age) {
  if (age < 18) return "minor";
  if (age < 65) return "adult";
  return "senior";
}

// ❌ Bad - Checking for undefined
if (typeof value !== "undefined" && value !== null) {
  // ...
}

// ✅ Good - Nullish coalescing
const result = value ?? defaultValue;
const name = user?.name ?? "Guest";

// ═══════════════════════════════════════════
// 6. Error Handling
// ═══════════════════════════════════════════

// ❌ Bad - Silent failures
function getUser(id) {
  try {
    return database.getUser(id);
  } catch (error) {
    return null; // Error swallowed!
  }
}

// ✅ Good - Proper error handling
async function getUser(id) {
  try {
    return await database.getUser(id);
  } catch (error) {
    console.error("Failed to get user:", error);
    throw new Error(`User ${id} not found`);
  }
}

// ❌ Bad - Generic error messages
throw new Error("Error");

// ✅ Good - Descriptive errors
throw new Error("User with ID 123 not found in database");

// ═══════════════════════════════════════════
// 7. Async/Await Best Practices
// ═══════════════════════════════════════════

// ❌ Bad - Sequential when could be parallel
async function getData() {
  const users = await fetchUsers();
  const posts = await fetchPosts();
  const comments = await fetchComments();
  return { users, posts, comments };
}

// ✅ Good - Parallel execution
async function getData() {
  const [users, posts, comments] = await Promise.all([
    fetchUsers(),
    fetchPosts(),
    fetchComments(),
  ]);
  return { users, posts, comments };
}

// ❌ Bad - Forgot await
async function getUser() {
  const user = fetchUser(); // Returns Promise, not user!
  console.log(user.name); // undefined!
}

// ✅ Good
async function getUser() {
  const user = await fetchUser();
  console.log(user.name);
}

// ═══════════════════════════════════════════
// 8. Code Organization
// ═══════════════════════════════════════════

// ❌ Bad - Everything in one place
const app = {
  users: [],
  addUser: function (user) {
    /* ... */
  },
  deleteUser: function (id) {
    /* ... */
  },
  validateEmail: function (email) {
    /* ... */
  },
  sendEmail: function (user) {
    /* ... */
  },
  // ...100 more methods
};

// ✅ Good - Separation of concerns
class UserRepository {
  async add(user) {
    /* ... */
  }
  async delete(id) {
    /* ... */
  }
  async findById(id) {
    /* ... */
  }
}

class UserValidator {
  static validateEmail(email) {
    /* ... */
  }
  static validateName(name) {
    /* ... */
  }
}

class EmailService {
  async send(to, subject, body) {
    /* ... */
  }
}

// ═══════════════════════════════════════════
// 9. Comments & Documentation
// ═══════════════════════════════════════════

// ❌ Bad - Obvious comments
// Increment counter
counter++;

// Add 1 to the variable i
i = i + 1;

// ✅ Good - Explain WHY, not WHAT
// Retry with exponential backoff to handle rate limiting
await retry(fetchData, 3, 1000);

// Cache for 1 hour to reduce database load
cache.set(key, value, 3600);

// JSDoc comments
/**
 * Fetches user data from the API
 * @param {number} userId - The ID of the user
 * @param {Object} options - Additional options
 * @param {boolean} options.includeDeleted - Include deleted users
 * @returns {Promise<User>} The user object
 * @throws {Error} If user not found
 */
async function fetchUser(userId, options = {}) {
  // ...
}

// ═══════════════════════════════════════════
// 10. Performance Tips
// ═══════════════════════════════════════════

// ❌ Bad - Creating functions in loops
for (let i = 0; i < 1000; i++) {
  setTimeout(function () {
    console.log(i);
  }, 1000);
}

// ✅ Good - Reuse function
const logValue = (value) => () => console.log(value);
for (let i = 0; i < 1000; i++) {
  setTimeout(logValue(i), 1000);
}

// ❌ Bad - Inefficient DOM manipulation
for (let i = 0; i < 1000; i++) {
  const div = document.createElement("div");
  div.textContent = `Item ${i}`;
  document.body.appendChild(div); // Reflow on each append!
}

// ✅ Good - Batch DOM updates
const fragment = document.createDocumentFragment();
for (let i = 0; i < 1000; i++) {
  const div = document.createElement("div");
  div.textContent = `Item ${i}`;
  fragment.appendChild(div);
}
document.body.appendChild(fragment); // Single reflow!

// ❌ Bad - Memory leaks
function attachEvent() {
  const bigData = new Array(1000000);
  element.addEventListener("click", () => {
    console.log(bigData.length); // bigData never garbage collected!
  });
}

// ✅ Good - Clean up references
function attachEvent() {
  const bigData = new Array(1000000);
  const handler = () => console.log(bigData.length);

  element.addEventListener("click", handler);

  // Clean up when done
  element.addEventListener("remove", () => {
    element.removeEventListener("click", handler);
  });
}
```

> **💡 Pro Tip:** Use ESLint + Prettier for consistent code style. Follow Airbnb or Standard JS style guide. Write self-documenting code!

---

<div align="center">

## 🎉 Conclusion

_You've Mastered JavaScript!_ 🏆

</div>

### What's Next? 🚀

You now have a comprehensive understanding of:

- ✅ **Fundamentals** - Variables, data types, functions
- ✅ **Modern Features** - ES6+ syntax, async/await, modules
- ✅ **OOP** - Classes, inheritance, encapsulation
- ✅ **Async Programming** - Promises, async/await, parallel execution
- ✅ **Design Patterns** - Singleton, Factory, Observer, and more
- ✅ **Performance** - Optimization techniques, lazy loading, memoization
- ✅ **DOM Manipulation** - Events, element creation, efficient updates
- ✅ **Error Handling** - Try/catch, custom errors, logging
- ✅ **Testing** - Unit tests, mocks, integration tests
- ✅ **Best Practices** - Clean code, naming conventions, organization

### Continue Your Journey 📚

```javascript
const nextSteps = {
  frameworks: ["React", "Vue", "Angular", "Svelte"],
  backend: ["Node.js", "Express", "NestJS", "Deno"],
  testing: ["Jest", "Vitest", "Playwright", "Cypress"],
  tools: ["TypeScript", "Webpack", "Vite", "ESBuild"],
  mobile: ["React Native", "Ionic", "Capacitor"],
  desktop: ["Electron", "Tauri"],
};

async function keepLearning() {
  while (true) {
    await learnNewThing();
    await buildSomethingAwesome();
    await shareWithCommunity();
  }
}

keepLearning();
```

### Useful Resources 🔗

- 📖 [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript) - The ultimate JS reference
- 📖 [JavaScript.info](https://javascript.info) - Modern JavaScript tutorial
- 📖 [You Don't Know JS](https://github.com/getify/You-Dont-Know-JS) - Deep dive into JS
- 📖 [Eloquent JavaScript](https://eloquentjavascript.net) - Free online book
- 🎥 [JavaScript30](https://javascript30.com) - 30 day vanilla JS challenge
- 🎥 [FreeCodeCamp](https://www.freecodecamp.org) - Free JS courses
- 💬 [JavaScript Discord](https://discord.gg/javascript) - Community help
- 🐦 [Follow JS experts on Twitter](https://twitter.com/i/lists/1234567890)

---

<div align="center">

**Built with 💛 by MrDib, for JavaScript developers**

_"JavaScript is the duct tape of the Internet."_ ✨

**Now go build something amazing!** 🚀

</div>
