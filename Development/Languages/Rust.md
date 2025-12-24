<div align="center">

# 🦀 Rust - Safe, Fast, Concurrent

### _Fearless concurrency and memory safety without garbage collection_ ⚡

![Rust](https://img.shields.io/badge/Rust-1.75+-orange?style=for-the-badge&logo=rust)
![Performance](https://img.shields.io/badge/Performance-Blazing%20Fast-green?style=for-the-badge)
![Memory Safety](https://img.shields.io/badge/Memory-Safe-red?style=for-the-badge)

</div>

---

## 📚 Table of Contents

- [🎯 Rust Fundamentals](#-rust-fundamentals)
- [📊 Data Types & Ownership](#-data-types--ownership)
- [🔄 Control Flow](#-control-flow)
- [🔧 Functions & Closures](#-functions--closures)
- [🏗️ Structs & Enums](#️-structs--enums)
- [🎨 Traits & Generics](#-traits--generics)
- [⚠️ Error Handling](#️-error-handling)
- [📦 Collections & Iterators](#-collections--iterators)
- [🧵 Concurrency & Async](#-concurrency--async)
- [🌐 Web Development](#-web-development)
- [🗄️ Database Operations](#️-database-operations)
- [📂 File I/O](#-file-io)
- [🧪 Testing](#-testing)
- [🎯 Common Patterns](#-common-patterns)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 🎯 Rust Fundamentals

</div>

### Getting Started with Rust 🚀

```bash
# ═══════════════════════════════════════════
# Installation & Setup
# ═══════════════════════════════════════════

# Install Rust (rustup)
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

# Update Rust
rustup update

# Check version
rustc --version
cargo --version

# Install nightly (for experimental features)
rustup install nightly
rustup default nightly

# Format code
rustfmt --version
cargo fmt

# Lint code
cargo clippy

# ═══════════════════════════════════════════
# Cargo Commands (Package Manager)
# ═══════════════════════════════════════════

# Create new project
cargo new myproject        # Binary
cargo new mylib --lib      # Library

# Build
cargo build               # Debug mode
cargo build --release     # Optimized

# Run
cargo run
cargo run --release

# Check (faster than build)
cargo check

# Test
cargo test
cargo test --release

# Clean build artifacts
cargo clean

# Update dependencies
cargo update

# Generate documentation
cargo doc --open
```

---

### Hello World & Basic Syntax 📝

```rust
// ═══════════════════════════════════════════
// Hello World
// ═══════════════════════════════════════════

fn main() {
    println!("Hello from MrDib! 🦀");

    // Variables (immutable by default)
    let name = "MrDib";
    let age = 25;

    // Mutable variables
    let mut score = 100;
    score += 50;
    println!("Score: {}", score);

    // Constants (must have type annotation)
    const MAX_POINTS: u32 = 100_000;
    const VERSION: &str = "1.0.0";

    // Type annotations
    let x: i32 = 42;
    let pi: f64 = 3.14159;
    let is_active: bool = true;

    // Shadowing (redeclaring variable)
    let x = 5;
    let x = x + 1;  // x is now 6
    let x = x * 2;  // x is now 12

    // String formatting
    println!("Name: {}, Age: {}", name, age);
    println!("Value: {:?}", some_variable);  // Debug format
    println!("Pretty: {:#?}", some_struct);  // Pretty debug
}

// ═══════════════════════════════════════════
// Comments
// ═══════════════════════════════════════════

// Single-line comment

/*
 * Multi-line comment
 * More details here
 */

/// Documentation comment for the following item
/// Supports Markdown!
fn documented_function() {}

//! Module-level documentation
//! This documents the enclosing module

// ═══════════════════════════════════════════
// Macros (End with !)
// ═══════════════════════════════════════════

println!("Hello");      // Print with newline
print!("No newline");   // Print without newline
eprintln!("Error");     // Print to stderr
format!("String");      // Create formatted string
vec![1, 2, 3];         // Create vector
panic!("Oh no!");       // Crash program
assert_eq!(a, b);      // Assert equality
```

> **💡 Pro Tip:** Variables are immutable by default in Rust - this prevents bugs! Use `mut` only when you need to change a variable.

---

<div align="center">

## 📊 Data Types & Ownership

</div>

### Primitive Data Types 🔢

```rust
// ═══════════════════════════════════════════
// Scalar Types
// ═══════════════════════════════════════════

fn scalar_types() {
    // Integers (signed)
    let i8_val: i8 = -128;           // -128 to 127
    let i16_val: i16 = -32_768;      // -32,768 to 32,767
    let i32_val: i32 = 42;           // Default integer type
    let i64_val: i64 = 1_000_000;
    let i128_val: i128 = 999_999_999_999;
    let isize_val: isize = 100;      // Pointer-sized (32/64-bit)

    // Integers (unsigned)
    let u8_val: u8 = 255;            // 0 to 255
    let u16_val: u16 = 65_535;
    let u32_val: u32 = 4_294_967_295;
    let u64_val: u64 = 18_446_744_073_709_551_615;
    let u128_val: u128 = 340_282_366_920_938_463_463_374_607_431_768_211_455;
    let usize_val: usize = 100;      // Pointer-sized (32/64-bit)

    // Floating point
    let f32_val: f32 = 3.14;
    let f64_val: f64 = 2.718281828;  // Default float type

    // Boolean
    let is_true: bool = true;
    let is_false: bool = false;

    // Character (4 bytes, Unicode)
    let letter: char = 'A';
    let emoji: char = '😀';
    let chinese: char = '中';

    // Number literals
    let decimal = 98_222;            // Underscore for readability
    let hex = 0xff;                  // Hexadecimal
    let octal = 0o77;                // Octal
    let binary = 0b1111_0000;        // Binary
    let byte = b'A';                 // Byte (u8 only)
}

// ═══════════════════════════════════════════
// Compound Types
// ═══════════════════════════════════════════

fn compound_types() {
    // Tuple (fixed size, different types)
    let tuple: (i32, f64, &str) = (42, 3.14, "hello");

    // Destructuring
    let (x, y, z) = tuple;

    // Access by index
    let first = tuple.0;
    let second = tuple.1;

    // Unit type (empty tuple)
    let unit: () = ();

    // Array (fixed size, same type)
    let array: [i32; 5] = [1, 2, 3, 4, 5];
    let first = array[0];
    let length = array.len();

    // Array with same value
    let zeros = [0; 10];  // [0, 0, 0, 0, 0, 0, 0, 0, 0, 0]

    // Slice (view into array/vector)
    let slice: &[i32] = &array[1..3];  // [2, 3]
}

// ═══════════════════════════════════════════
// String Types (The Tricky Part!)
// ═══════════════════════════════════════════

fn string_types() {
    // String slice (&str) - immutable, fixed size
    let string_slice: &str = "hello";  // Stored in binary

    // String (String) - growable, heap-allocated
    let string: String = String::from("world");

    // Conversion between types
    let from_str: String = "hello".to_string();
    let from_string: &str = &string;

    // String operations
    let mut s = String::from("hello");
    s.push_str(", world");       // Append string slice
    s.push('!');                 // Append single char

    // Concatenation
    let s1 = String::from("Hello, ");
    let s2 = String::from("world!");
    let s3 = s1 + &s2;           // s1 moved, s2 still valid

    // Format macro (doesn't take ownership)
    let s1 = String::from("Hello");
    let s2 = String::from("World");
    let s3 = format!("{} {}!", s1, s2);  // s1, s2 still valid

    // Indexing not allowed (UTF-8 encoded!)
    // let h = s[0];  // ❌ Error!

    // Slicing (be careful with multi-byte chars)
    let hello = "Здравствуйте";
    let s = &hello[0..4];  // First 4 bytes, not characters!

    // Iterating over characters
    for c in "नमस्ते".chars() {
        println!("{}", c);
    }

    // Iterating over bytes
    for b in "नमस्ते".bytes() {
        println!("{}", b);
    }
}
```

---

### Ownership - Rust's Superpower! 🦸

```rust
// ═══════════════════════════════════════════
// The Three Rules of Ownership
// ═══════════════════════════════════════════

/*
1. Each value in Rust has a single owner
2. There can only be one owner at a time
3. When the owner goes out of scope, the value is dropped
*/

// ═══════════════════════════════════════════
// Ownership in Action
// ═══════════════════════════════════════════

fn ownership_basics() {
    // Stack vs Heap
    let x = 5;  // Stack (Copy type)
    let y = x;  // Copy happens
    println!("{}, {}", x, y);  // ✅ Both valid

    // Heap-allocated data
    let s1 = String::from("hello");
    let s2 = s1;  // Move happens (not copy!)
    // println!("{}", s1);  // ❌ Error! s1 no longer valid
    println!("{}", s2);     // ✅ s2 is valid

    // Clone (deep copy)
    let s3 = String::from("world");
    let s4 = s3.clone();
    println!("{}, {}", s3, s4);  // ✅ Both valid

    // Ownership and functions
    let s = String::from("hello");
    takes_ownership(s);
    // println!("{}", s);  // ❌ Error! s moved into function

    let x = 5;
    makes_copy(x);
    println!("{}", x);  // ✅ x still valid (copied)
}

fn takes_ownership(some_string: String) {
    println!("{}", some_string);
}  // some_string dropped here

fn makes_copy(some_integer: i32) {
    println!("{}", some_integer);
}  // some_integer dropped, but it's just a copy

// ═══════════════════════════════════════════
// References & Borrowing
// ═══════════════════════════════════════════

fn borrowing_basics() {
    let s1 = String::from("hello");

    // Immutable reference (borrowing)
    let len = calculate_length(&s1);
    println!("Length of '{}' is {}", s1, len);  // s1 still valid!

    // Multiple immutable references OK
    let r1 = &s1;
    let r2 = &s1;
    println!("{}, {}", r1, r2);  // ✅ Multiple readers OK

    // Mutable reference
    let mut s = String::from("hello");
    change(&mut s);
    println!("{}", s);  // "hello, world"

    // Only ONE mutable reference at a time
    let r1 = &mut s;
    // let r2 = &mut s;  // ❌ Error! Can't have two mutable refs

    // Can't mix mutable and immutable references
    let r1 = &s;      // ✅ OK
    let r2 = &s;      // ✅ OK
    // let r3 = &mut s;  // ❌ Error! Can't mix
}

fn calculate_length(s: &String) -> usize {
    s.len()
}  // s goes out of scope, but doesn't own data, so nothing happens

fn change(s: &mut String) {
    s.push_str(", world");
}

// ═══════════════════════════════════════════
// Slices (References to Parts of Collections)
// ═══════════════════════════════════════════

fn slice_examples() {
    let s = String::from("hello world");

    // String slices
    let hello = &s[0..5];   // "hello"
    let world = &s[6..11];  // "world"
    let hello = &s[..5];    // Same as [0..5]
    let world = &s[6..];    // Same as [6..len]
    let whole = &s[..];     // Entire string

    // Array slices
    let arr = [1, 2, 3, 4, 5];
    let slice = &arr[1..3];  // [2, 3]

    // First word function
    fn first_word(s: &str) -> &str {
        let bytes = s.as_bytes();

        for (i, &item) in bytes.iter().enumerate() {
            if item == b' ' {
                return &s[0..i];
            }
        }

        &s[..]
    }

    let my_string = String::from("hello world");
    let word = first_word(&my_string);
    println!("First word: {}", word);
}

// ═══════════════════════════════════════════
// Lifetimes (Ensuring References are Valid)
// ═══════════════════════════════════════════

// Lifetime annotations
fn longest<'a>(x: &'a str, y: &'a str) -> &'a str {
    if x.len() > y.len() {
        x
    } else {
        y
    }
}

// Lifetime in structs
struct ImportantExcerpt<'a> {
    part: &'a str,
}

impl<'a> ImportantExcerpt<'a> {
    fn announce_and_return_part(&self, announcement: &str) -> &str {
        println!("Attention: {}", announcement);
        self.part
    }
}

// Static lifetime (lives for entire program)
let s: &'static str = "I have a static lifetime.";
```

> **💡 Pro Tip:** Ownership is Rust's killer feature! It eliminates entire classes of bugs at compile time. The borrow checker is strict, but it's there to help you write safe code!

---

<div align="center">

## 🔄 Control Flow

</div>

### Conditionals & Loops 🔀

```rust
// ═══════════════════════════════════════════
// If/Else Expressions
// ═══════════════════════════════════════════

fn conditionals() {
    let number = 85;

    // Basic if/else
    if number >= 90 {
        println!("Grade: A");
    } else if number >= 80 {
        println!("Grade: B");
    } else if number >= 70 {
        println!("Grade: C");
    } else {
        println!("Grade: F");
    }

    // if is an expression (returns value)
    let grade = if number >= 90 {
        "A"
    } else if number >= 80 {
        "B"
    } else {
        "F"
    };

    // No parentheses needed (but condition must be bool)
    let condition = true;
    if condition {
        println!("Condition was true");
    }
}

// ═══════════════════════════════════════════
// Loops
// ═══════════════════════════════════════════

fn loops() {
    // Infinite loop
    let mut counter = 0;
    let result = loop {
        counter += 1;
        if counter == 10 {
            break counter * 2;  // Loop can return value!
        }
    };
    println!("Result: {}", result);  // 20

    // Loop labels (for nested loops)
    'outer: loop {
        println!("Entered outer loop");

        'inner: loop {
            println!("Entered inner loop");
            break 'outer;  // Break outer loop
        }

        println!("This won't print");
    }

    // While loop
    let mut number = 3;
    while number != 0 {
        println!("{}!", number);
        number -= 1;
    }
    println!("LIFTOFF!!!");

    // For loop (most common)
    let arr = [10, 20, 30, 40, 50];

    for element in arr {
        println!("Value: {}", element);
    }

    // Range
    for number in 1..=5 {  // 1 to 5 (inclusive)
        println!("{}", number);
    }

    for number in (1..5).rev() {  // Reverse: 4, 3, 2, 1
        println!("{}", number);
    }

    // Enumerate (index + value)
    for (index, value) in arr.iter().enumerate() {
        println!("Index {}: Value {}", index, value);
    }
}

// ═══════════════════════════════════════════
// Match Expression (Pattern Matching)
// ═══════════════════════════════════════════

fn match_examples() {
    let number = 7;

    // Basic match
    match number {
        1 => println!("One"),
        2 | 3 | 5 | 7 | 11 => println!("Prime"),
        13..=19 => println!("Teen"),
        _ => println!("Other"),  // Default case
    }

    // Match returns value
    let description = match number {
        1 => "one",
        2..=10 => "small",
        _ => "large",
    };

    // Destructuring tuples
    let point = (0, 5);
    match point {
        (0, y) => println!("On y-axis at {}", y),
        (x, 0) => println!("On x-axis at {}", x),
        (x, y) => println!("On neither axis: ({}, {})", x, y),
    }

    // Match with Option
    let some_value = Some(5);
    match some_value {
        Some(i) => println!("Got value: {}", i),
        None => println!("No value"),
    }

    // Match with Result
    let result: Result<i32, &str> = Ok(42);
    match result {
        Ok(value) => println!("Success: {}", value),
        Err(e) => println!("Error: {}", e),
    }

    // Match guards
    let num = Some(4);
    match num {
        Some(x) if x % 2 == 0 => println!("Even number: {}", x),
        Some(x) => println!("Odd number: {}", x),
        None => (),
    }

    // @ bindings
    match number {
        n @ 1..=5 => println!("Small number: {}", n),
        n @ 6..=10 => println!("Medium number: {}", n),
        _ => println!("Large number"),
    }
}

// ═══════════════════════════════════════════
// if let & while let (Syntactic Sugar)
// ═══════════════════════════════════════════

fn if_let_examples() {
    let some_value = Some(5);

    // Instead of match with one pattern
    if let Some(i) = some_value {
        println!("Got value: {}", i);
    } else {
        println!("No value");
    }

    // while let (loop until pattern doesn't match)
    let mut stack = vec![1, 2, 3];

    while let Some(top) = stack.pop() {
        println!("{}", top);
    }
}
```

> **💡 Pro Tip:** Match is exhaustive - the compiler ensures you handle all cases! Use `_` for catch-all patterns. Unlike switch in other languages, match doesn't fall through!

---

<div align="center">

## 🔧 Functions & Closures

</div>

### Function Declarations 📦

```rust
// ═══════════════════════════════════════════
// Basic Functions
// ═══════════════════════════════════════════

// Simple function
fn greet(name: &str) {
    println!("Hello, {}!", name);
}

// Function with return value (no semicolon!)
fn add(a: i32, b: i32) -> i32 {
    a + b  // Last expression is return value
}

// Explicit return
fn subtract(a: i32, b: i32) -> i32 {
    return a - b;  // Early return
}

// Multiple parameters
fn calculate(a: i32, b: i32, c: i32) -> i32 {
    a * b + c
}

// Multiple return values (using tuple)
fn swap(a: i32, b: i32) -> (i32, i32) {
    (b, a)
}

// Unit return type (no return value)
fn no_return() -> () {
    println!("I return nothing");
}

// Equivalent (unit type implicit)
fn no_return_implicit() {
    println!("Same as above");
}

// ═══════════════════════════════════════════
// Advanced Function Features
// ═══════════════════════════════════════════

// References as parameters
fn calculate_length(s: &String) -> usize {
    s.len()
}

// Mutable references
fn change(s: &mut String) {
    s.push_str(", world");
}

// Taking ownership
fn consume(s: String) {
    println!("{}", s);
}  // s dropped here

// Returning ownership
fn create_string() -> String {
    String::from("hello")
}

// Generic functions
fn largest<T: PartialOrd>(list: &[T]) -> &T {
    let mut largest = &list[0];
    for item in list {
        if item > largest {
            largest = item;
        }
    }
    largest
}

// Diverging functions (never return)
fn loop_forever() -> ! {
    loop {
        println!("Forever!");
    }
}

// ═══════════════════════════════════════════
// Closures (Anonymous Functions)
// ═══════════════════════════════════════════

fn closure_basics() {
    // Basic closure
    let add_one = |x: i32| -> i32 { x + 1 };
    println!("{}", add_one(5));  // 6

    // Type inference (most common)
    let add_two = |x| x + 2;
    println!("{}", add_two(5));  // 7

    // Multiple parameters
    let multiply = |x, y| x * y;
    println!("{}", multiply(3, 4));  // 12

    // Multi-line closure
    let complex = |x| {
        let doubled = x * 2;
        let tripled = doubled + x;
        tripled
    };

    // Capturing environment (borrowing)
    let x = 4;
    let equal_to_x = |z| z == x;  // Borrows x
    println!("{}", equal_to_x(4));  // true

    // Mutable borrow
    let mut list = vec![1, 2, 3];
    let mut add_to_list = || list.push(4);
    add_to_list();
    println!("{:?}", list);  // [1, 2, 3, 4]

    // Moving ownership into closure
    let list = vec![1, 2, 3];
    let consume = move || println!("{:?}", list);
    consume();
    // println!("{:?}", list);  // ❌ Error! list moved
}

// ═══════════════════════════════════════════
// Closures with Iterators
// ═══════════════════════════════════════════

fn closure_with_iterators() {
    let numbers = vec![1, 2, 3, 4, 5];

    // map
    let doubled: Vec<i32> = numbers.iter().map(|x| x * 2).collect();
    println!("{:?}", doubled);  // [2, 4, 6, 8, 10]

    // filter
    let evens: Vec<&i32> = numbers.iter().filter(|x| *x % 2 == 0).collect();
    println!("{:?}", evens);  // [2, 4]

    // find
    let first_even = numbers.iter().find(|&&x| x % 2 == 0);
    println!("{:?}", first_even);  // Some(2)

    // any & all
    let has_even = numbers.iter().any(|&x| x % 2 == 0);
    let all_positive = numbers.iter().all(|&x| x > 0);

    // fold (reduce)
    let sum: i32 = numbers.iter().fold(0, |acc, x| acc + x);
    println!("Sum: {}", sum);  // 15
}

// ═══════════════════════════════════════════
// Function Pointers
// ═══════════════════════════════════════════

fn add_one(x: i32) -> i32 {
    x + 1
}

fn apply_function(f: fn(i32) -> i32, value: i32) -> i32 {
    f(value)
}

fn function_pointers() {
    let result = apply_function(add_one, 5);
    println!("{}", result);  // 6

    // Pass closure as function pointer
    let result = apply_function(|x| x * 2, 5);
    println!("{}", result);  // 10
}

// ═══════════════════════════════════════════
// Returning Closures
// ═══════════════════════════════════════════

fn returns_closure() -> Box<dyn Fn(i32) -> i32> {
    Box::new(|x| x + 1)
}

fn closure_factory(factor: i32) -> Box<dyn Fn(i32) -> i32> {
    Box::new(move |x| x * factor)
}

fn using_returned_closures() {
    let add_one = returns_closure();
    println!("{}", add_one(5));  // 6

    let double = closure_factory(2);
    let triple = closure_factory(3);
    println!("{}", double(5));  // 10
    println!("{}", triple(5));  // 15
}
```

> **💡 Pro Tip:** Closures are incredibly powerful in Rust! They can capture their environment in three ways: by reference (&T), by mutable reference (&mut T), or by value (T). Use `move` to force taking ownership!

---

<div align="center">

## 🏗️ Structs & Enums

</div>

### Defining Structs 📦

```rust
// ═══════════════════════════════════════════
// Classic Struct
// ═══════════════════════════════════════════

struct User {
    username: String,
    email: String,
    age: u8,
    is_active: bool,
}

// Create instance
fn struct_basics() {
    let user1 = User {
        username: String::from("mrdib"),
        email: String::from("mrdib@example.com"),
        age: 25,
        is_active: true,
    };

    // Access fields
    println!("Username: {}", user1.username);

    // Mutable struct
    let mut user2 = User {
        username: String::from("alice"),
        email: String::from("alice@example.com"),
        age: 30,
        is_active: true,
    };

    user2.age = 31;  // Can modify

    // Struct update syntax
    let user3 = User {
        username: String::from("bob"),
        email: String::from("bob@example.com"),
        ..user1  // Use remaining fields from user1
    };
}

// Constructor pattern
impl User {
    fn new(username: String, email: String, age: u8) -> Self {
        Self {
            username,
            email,
            age,
            is_active: true,
        }
    }
}

// ═══════════════════════════════════════════
// Tuple Structs (Named Tuples)
// ═══════════════════════════════════════════

struct Color(u8, u8, u8);
struct Point(i32, i32, i32);

fn tuple_structs() {
    let black = Color(0, 0, 0);
    let origin = Point(0, 0, 0);

    // Access by index
    println!("Red: {}", black.0);
    println!("X: {}", origin.0);

    // Different types even with same structure
    // let color: Point = black;  // ❌ Error! Different types
}

// ═══════════════════════════════════════════
// Unit Structs (No Fields)
// ═══════════════════════════════════════════

struct AlwaysEqual;

fn unit_structs() {
    let subject = AlwaysEqual;
    // Useful for traits without data
}

// ═══════════════════════════════════════════
// Methods & Associated Functions
// ═══════════════════════════════════════════

struct Rectangle {
    width: u32,
    height: u32,
}

impl Rectangle {
    // Associated function (constructor)
    fn new(width: u32, height: u32) -> Self {
        Self { width, height }
    }

    // Method (takes &self)
    fn area(&self) -> u32 {
        self.width * self.height
    }

    // Method with parameters
    fn can_hold(&self, other: &Rectangle) -> bool {
        self.width > other.width && self.height > other.height
    }

    // Method with mutable self
    fn scale(&mut self, factor: u32) {
        self.width *= factor;
        self.height *= factor;
    }

    // Method that takes ownership
    fn into_square(self) -> Rectangle {
        let size = self.width.min(self.height);
        Rectangle {
            width: size,
            height: size,
        }
    }

    // Associated function (no self)
    fn square(size: u32) -> Self {
        Self {
            width: size,
            height: size,
        }
    }
}

// Multiple impl blocks (allowed)
impl Rectangle {
    fn perimeter(&self) -> u32 {
        2 * (self.width + self.height)
    }
}

fn using_methods() {
    let mut rect = Rectangle::new(30, 50);
    println!("Area: {}", rect.area());
    println!("Perimeter: {}", rect.perimeter());

    rect.scale(2);

    let square = Rectangle::square(20);
}

// ═══════════════════════════════════════════
// Enums (Sum Types)
// ═══════════════════════════════════════════

// Basic enum
enum IpAddrKind {
    V4,
    V6,
}

// Enum with data
enum IpAddr {
    V4(u8, u8, u8, u8),
    V6(String),
}

// Enum with different types
enum Message {
    Quit,                       // No data
    Move { x: i32, y: i32 },   // Named fields
    Write(String),              // Single value
    ChangeColor(u8, u8, u8),   // Tuple
}

// Methods on enums
impl Message {
    fn call(&self) {
        match self {
            Message::Quit => println!("Quit"),
            Message::Move { x, y } => println!("Move to ({}, {})", x, y),
            Message::Write(text) => println!("Write: {}", text),
            Message::ChangeColor(r, g, b) => {
                println!("Change color to ({}, {}, {})", r, g, b)
            }
        }
    }
}

fn enum_examples() {
    let home = IpAddr::V4(127, 0, 0, 1);
    let loopback = IpAddr::V6(String::from("::1"));

    let msg = Message::Write(String::from("Hello"));
    msg.call();
}

// ═══════════════════════════════════════════
// Option<T> - Rust's Way of Handling Null
// ═══════════════════════════════════════════

// enum Option<T> {
//     Some(T),
//     None,
// }

fn option_examples() {
    let some_number = Some(5);
    let some_string = Some("hello");
    let absent_number: Option<i32> = None;

    // Match on Option
    match some_number {
        Some(i) => println!("Got number: {}", i),
        None => println!("No number"),
    }

    // if let (syntactic sugar)
    if let Some(i) = some_number {
        println!("Number is {}", i);
    }

    // unwrap_or (default value)
    let value = absent_number.unwrap_or(0);

    // map
    let doubled = some_number.map(|x| x * 2);  // Some(10)

    // and_then (flatMap)
    let result = some_number.and_then(|x| {
        if x % 2 == 0 {
            Some(x / 2)
        } else {
            None
        }
    });

    // ok_or (convert to Result)
    let result: Result<i32, &str> = some_number.ok_or("No value");
}

// ═══════════════════════════════════════════
// Result<T, E> - Error Handling
// ═══════════════════════════════════════════

// enum Result<T, E> {
//     Ok(T),
//     Err(E),
// }

fn divide(a: f64, b: f64) -> Result<f64, String> {
    if b == 0.0 {
        Err(String::from("Division by zero"))
    } else {
        Ok(a / b)
    }
}

fn result_examples() {
    match divide(10.0, 2.0) {
        Ok(result) => println!("Result: {}", result),
        Err(e) => println!("Error: {}", e),
    }

    // unwrap (panics on error - use carefully!)
    let result = divide(10.0, 2.0).unwrap();

    // expect (panics with custom message)
    let result = divide(10.0, 2.0).expect("Division failed");

    // unwrap_or
    let result = divide(10.0, 0.0).unwrap_or(0.0);

    // map and map_err
    let result = divide(10.0, 2.0)
        .map(|x| x * 2)
        .map_err(|e| format!("Failed: {}", e));
}
```

> **💡 Pro Tip:** Rust doesn't have null! Use `Option<T>` instead. This forces you to handle the "no value" case explicitly, eliminating null pointer errors at compile time!

---

<div align="center">

## 🎨 Traits & Generics

</div>

### Traits - Defining Shared Behavior 🔀

```rust
// ═══════════════════════════════════════════
// Basic Trait Definition
// ═══════════════════════════════════════════

trait Summary {
    fn summarize(&self) -> String;

    // Default implementation
    fn author(&self) -> String {
        String::from("Unknown")
    }

    // Method using other trait methods
    fn full_summary(&self) -> String {
        format!("{} by {}", self.summarize(), self.author())
    }
}

struct Article {
    title: String,
    content: String,
    author: String,
}

struct Tweet {
    username: String,
    content: String,
    retweets: u32,
}

// Implement trait for Article
impl Summary for Article {
    fn summarize(&self) -> String {
        format!("{} by {}", self.title, self.author)
    }

    fn author(&self) -> String {
        self.author.clone()
    }
}

// Implement trait for Tweet
impl Summary for Tweet {
    fn summarize(&self) -> String {
        format!("@{}: {}", self.username, self.content)
    }
}

// ═══════════════════════════════════════════
// Trait Bounds
// ═══════════════════════════════════════════

// Function parameter with trait bound
fn notify(item: &impl Summary) {
    println!("Breaking news! {}", item.summarize());
}

// Generic with trait bound (equivalent)
fn notify_generic<T: Summary>(item: &T) {
    println!("Breaking news! {}", item.summarize());
}

// Multiple trait bounds
use std::fmt::Display;

fn notify_display<T: Summary + Display>(item: &T) {
    println!("{}", item);
}

// Where clause (cleaner for complex bounds)
fn some_function<T, U>(t: &T, u: &U) -> i32
where
    T: Display + Clone,
    U: Clone + std::fmt::Debug,
{
    0
}

// Return type with trait
fn returns_summarizable() -> impl Summary {
    Tweet {
        username: String::from("mrdib"),
        content: String::from("Hello, Rust!"),
        retweets: 0,
    }
}

// ═══════════════════════════════════════════
// Trait Objects (Dynamic Dispatch)
// ═══════════════════════════════════════════

fn trait_objects() {
    let article = Article {
        title: String::from("Rust is Awesome"),
        content: String::from("..."),
        author: String::from("MrDib"),
    };

    let tweet = Tweet {
        username: String::from("rustlang"),
        content: String::from("Announcing Rust 1.75!"),
        retweets: 1000,
    };

    // Vector of trait objects
    let items: Vec<Box<dyn Summary>> = vec![
        Box::new(article),
        Box::new(tweet),
    ];

    for item in items {
        println!("{}", item.summarize());
    }
}

// ═══════════════════════════════════════════
// Commonly Used Traits
// ═══════════════════════════════════════════

// Clone trait
#[derive(Clone)]
struct MyStruct {
    data: Vec<i32>,
}

// Copy trait (only for types fully on stack)
#[derive(Copy, Clone)]
struct Point {
    x: i32,
    y: i32,
}

// Debug trait
#[derive(Debug)]
struct Rectangle {
    width: u32,
    height: u32,
}

// Display trait (custom formatting)
use std::fmt;

impl fmt::Display for Rectangle {
    fn fmt(&self, f: &mut fmt::Formatter) -> fmt::Result {
        write!(f, "Rectangle {}x{}", self.width, self.height)
    }
}

// PartialEq and Eq
#[derive(PartialEq, Eq)]
struct User {
    id: u32,
    name: String,
}

// PartialOrd and Ord
#[derive(PartialOrd, Ord, PartialEq, Eq)]
struct Priority {
    level: u8,
}

// From and Into
struct Number {
    value: i32,
}

impl From<i32> for Number {
    fn from(value: i32) -> Self {
        Number { value }
    }
}

// Into is automatically implemented!
fn using_from_into() {
    let num = Number::from(5);
    let num: Number = 5.into();  // Same thing
}

// ═══════════════════════════════════════════
// Generics
// ═══════════════════════════════════════════

// Generic struct
struct Point<T> {
    x: T,
    y: T,
}

impl<T> Point<T> {
    fn x(&self) -> &T {
        &self.x
    }
}

// Specific implementation for one type
impl Point<f64> {
    fn distance_from_origin(&self) -> f64 {
        (self.x.powi(2) + self.y.powi(2)).sqrt()
    }
}

// Multiple generic types
struct Pair<T, U> {
    first: T,
    second: U,
}

// Generic enum
enum Result<T, E> {
    Ok(T),
    Err(E),
}

enum Option<T> {
    Some(T),
    None,
}

// Generic function
fn largest<T: PartialOrd>(list: &[T]) -> &T {
    let mut largest = &list[0];

    for item in list {
        if item > largest {
            largest = item;
        }
    }

    largest
}

// Using generics
fn generic_examples() {
    let integer_point = Point { x: 5, y: 10 };
    let float_point = Point { x: 1.0, y: 4.0 };

    let pair = Pair {
        first: 5,
        second: "hello",
    };

    let numbers = vec![34, 50, 25, 100, 65];
    let result = largest(&numbers);
    println!("Largest: {}", result);
}

// ═══════════════════════════════════════════
// Associated Types
// ═══════════════════════════════════════════

trait Iterator {
    type Item;  // Associated type

    fn next(&mut self) -> Option<Self::Item>;
}

struct Counter {
    count: u32,
}

impl Iterator for Counter {
    type Item = u32;  // Specify concrete type

    fn next(&mut self) -> Option<Self::Item> {
        if self.count < 5 {
            self.count += 1;
            Some(self.count)
        } else {
            None
        }
    }
}

// ═══════════════════════════════════════════
// Operator Overloading
// ═══════════════════════════════════════════

use std::ops::Add;

#[derive(Debug, PartialEq)]
struct Point2D {
    x: i32,
    y: i32,
}

impl Add for Point2D {
    type Output = Point2D;

    fn add(self, other: Point2D) -> Point2D {
        Point2D {
            x: self.x + other.x,
            y: self.y + other.y,
        }
    }
}

fn operator_overloading() {
    let p1 = Point2D { x: 1, y: 2 };
    let p2 = Point2D { x: 3, y: 4 };
    let p3 = p1 + p2;  // Uses our Add implementation

    assert_eq!(p3, Point2D { x: 4, y: 6 });
}
```

> **💡 Pro Tip:** Traits are Rust's answer to interfaces and abstract classes. They enable polymorphism without inheritance! Use trait bounds to write generic, reusable code.

---

<div align="center">

## ⚠️ Error Handling

</div>

### The Rust Way of Handling Errors 🛡️

```rust
// ═══════════════════════════════════════════
// Unrecoverable Errors (panic!)
// ═══════════════════════════════════════════

fn panic_examples() {
    // Explicit panic
    // panic!("Crash and burn!");

    // Panic with formatted message
    let x = 5;
    // panic!("x should be 10, but was {}", x);

    // Out of bounds access panics
    let v = vec![1, 2, 3];
    // let element = v[99];  // Panics!

    // Use .get() for safe access
    let element = v.get(99);  // Returns None
    match element {
        Some(e) => println!("Element: {}", e),
        None => println!("No element at index"),
    }
}

// ═══════════════════════════════════════════
// Recoverable Errors (Result<T, E>)
// ═══════════════════════════════════════════

use std::fs::File;
use std::io::{self, Read, ErrorKind};

// Basic Result handling
fn read_file_basic() {
    let file_result = File::open("hello.txt");

    let file = match file_result {
        Ok(file) => file,
        Err(error) => {
            panic!("Problem opening file: {:?}", error);
        }
    };
}

// Match on error kind
fn read_file_match_error() {
    let file_result = File::open("hello.txt");

    let file = match file_result {
        Ok(file) => file,
        Err(error) => match error.kind() {
            ErrorKind::NotFound => match File::create("hello.txt") {
                Ok(fc) => fc,
                Err(e) => panic!("Problem creating file: {:?}", e),
            },
            other_error => {
                panic!("Problem opening file: {:?}", other_error);
            }
        },
    };
}

// Using unwrap_or_else (cleaner)
fn read_file_unwrap_or_else() {
    let file = File::open("hello.txt").unwrap_or_else(|error| {
        if error.kind() == ErrorKind::NotFound {
            File::create("hello.txt").unwrap_or_else(|error| {
                panic!("Problem creating file: {:?}", error);
            })
        } else {
            panic!("Problem opening file: {:?}", error);
        }
    });
}

// ═══════════════════════════════════════════
// Shortcuts: unwrap and expect
// ═══════════════════════════════════════════

fn unwrap_examples() {
    // unwrap: returns value or panics
    let file = File::open("hello.txt").unwrap();

    // expect: panics with custom message
    let file = File::open("hello.txt")
        .expect("Failed to open hello.txt");
}

// ═══════════════════════════════════════════
// The ? Operator (Error Propagation)
// ═══════════════════════════════════════════

fn read_username_from_file() -> Result<String, io::Error> {
    let mut file = File::open("hello.txt")?;  // Returns error if fails
    let mut username = String::new();
    file.read_to_string(&mut username)?;      // Returns error if fails
    Ok(username)                               // Return success
}

// Even shorter with method chaining
fn read_username_short() -> Result<String, io::Error> {
    let mut username = String::new();
    File::open("hello.txt")?.read_to_string(&mut username)?;
    Ok(username)
}

// Shortest using fs::read_to_string
fn read_username_shortest() -> Result<String, io::Error> {
    std::fs::read_to_string("hello.txt")
}

// ? with Option
fn last_char_of_first_line(text: &str) -> Option<char> {
    text.lines().next()?.chars().last()
}

// ═══════════════════════════════════════════
// Custom Error Types
// ═══════════════════════════════════════════

use std::fmt;

#[derive(Debug)]
enum AppError {
    IoError(io::Error),
    ParseError(String),
    NotFound,
    ValidationError(String),
}

impl fmt::Display for AppError {
    fn fmt(&self, f: &mut fmt::Formatter) -> fmt::Result {
        match self {
            AppError::IoError(e) => write!(f, "IO Error: {}", e),
            AppError::ParseError(msg) => write!(f, "Parse Error: {}", msg),
            AppError::NotFound => write!(f, "Resource not found"),
            AppError::ValidationError(msg) => write!(f, "Validation Error: {}", msg),
        }
    }
}

impl std::error::Error for AppError {}

// Convert from io::Error
impl From<io::Error> for AppError {
    fn from(error: io::Error) -> Self {
        AppError::IoError(error)
    }
}

// Using custom error type
fn process_file(filename: &str) -> Result<String, AppError> {
    let mut file = File::open(filename)?;  // Auto-converts io::Error
    let mut contents = String::new();
    file.read_to_string(&mut contents)?;

    if contents.is_empty() {
        return Err(AppError::NotFound);
    }

    if !contents.contains("valid") {
        return Err(AppError::ValidationError(
            String::from("Content is invalid")
        ));
    }

    Ok(contents)
}

// ═══════════════════════════════════════════
// Using anyhow for Error Handling
// ═══════════════════════════════════════════

// Add to Cargo.toml: anyhow = "1.0"

use anyhow::{Context, Result};

fn read_config() -> Result<String> {
    let config = std::fs::read_to_string("config.toml")
        .context("Failed to read config file")?;

    // Add context to errors
    let parsed = parse_config(&config)
        .context("Failed to parse config")?;

    Ok(parsed)
}

// ═══════════════════════════════════════════
// Using thiserror for Custom Errors
// ═══════════════════════════════════════════

// Add to Cargo.toml: thiserror = "1.0"

use thiserror::Error;

#[derive(Error, Debug)]
enum DataStoreError {
    #[error("Connection failed: {0}")]
    ConnectionError(String),

    #[error("Query failed: {query}")]
    QueryError { query: String },

    #[error("Data not found")]
    NotFound,

    #[error(transparent)]
    IOError(#[from] std::io::Error),
}

fn query_database(id: u32) -> Result<String, DataStoreError> {
    if id == 0 {
        return Err(DataStoreError::NotFound);
    }

    // Simulate database query
    Ok(format!("Data for id {}", id))
}

// ═══════════════════════════════════════════
// Error Handling Best Practices
// ═══════════════════════════════════════════

// ✅ DO: Use Result for recoverable errors
fn divide(a: f64, b: f64) -> Result<f64, String> {
    if b == 0.0 {
        Err(String::from("Division by zero"))
    } else {
        Ok(a / b)
    }
}

// ✅ DO: Use ? operator for propagation
fn read_and_parse() -> Result<i32, Box<dyn std::error::Error>> {
    let content = std::fs::read_to_string("number.txt")?;
    let number = content.trim().parse()?;
    Ok(number)
}

// ✅ DO: Provide context to errors
fn load_config() -> Result<String> {
    std::fs::read_to_string("config.toml")
        .context("Failed to load configuration file")
}

// ❌ DON'T: Use unwrap in production code
fn bad_example() {
    let file = File::open("important.txt").unwrap();  // Could panic!
}

// ✅ DO: Handle errors gracefully
fn good_example() {
    match File::open("important.txt") {
        Ok(file) => { /* use file */ },
        Err(e) => {
            eprintln!("Failed to open file: {}", e);
            // Handle error appropriately
        }
    }
}
```

> **💡 Pro Tip:** Use `Result` for recoverable errors and `panic!` only for unrecoverable errors. The `?` operator makes error propagation incredibly clean. For applications, use `anyhow`. For libraries, use `thiserror`!

---

<div align="center">

## 📦 Collections & Iterators

</div>

### Essential Data Structures 📦

```rust
// ═══════════════════════════════════════════
// Vectors (Dynamic Arrays)
// ═══════════════════════════════════════════

fn vector_examples() {
    // Create vector
    let v: Vec<i32> = Vec::new();

    // Using macro
    let v = vec![1, 2, 3, 4, 5];

    // Push elements
    let mut v = Vec::new();
    v.push(1);
    v.push(2);
    v.push(3);

    // Access elements
    let third = &v[2];              // Panics if out of bounds
    let third = v.get(2);           // Returns Option<&T>

    match v.get(2) {
        Some(value) => println!("Third element: {}", value),
        None => println!("No third element"),
    }

    // Iterate
    for i in &v {
        println!("{}", i);
    }

    // Iterate and modify
    for i in &mut v {
        *i += 50;
    }

    // Pop element
    while let Some(top) = v.pop() {
        println!("{}", top);
    }

    // Vector methods
    v.len();              // Length
    v.is_empty();         // Check if empty
    v.clear();            // Remove all elements
    v.insert(2, 100);     // Insert at index
    v.remove(1);          // Remove at index
    v.swap(0, 1);         // Swap elements
    v.reverse();          // Reverse in place
    v.sort();             // Sort in place
    v.dedup();            // Remove consecutive duplicates

    // Capacity management
    let mut v = Vec::with_capacity(10);  // Pre-allocate
    v.capacity();         // Current capacity
    v.shrink_to_fit();    // Reduce capacity to length
}

// ═══════════════════════════════════════════
// HashMap (Key-Value Pairs)
// ═══════════════════════════════════════════

use std::collections::HashMap;

fn hashmap_examples() {
    // Create HashMap
    let mut scores = HashMap::new();
    scores.insert(String::from("Blue"), 10);
    scores.insert(String::from("Yellow"), 50);

    // From vectors
    let teams = vec![String::from("Blue"), String::from("Yellow")];
    let initial_scores = vec![10, 50];
    let scores: HashMap<_, _> = teams.iter().zip(initial_scores.iter()).collect();

    // Access values
    let team_name = String::from("Blue");
    let score = scores.get(&team_name);  // Returns Option<&V>

    match score {
        Some(s) => println!("Score: {}", s),
        None => println!("Team not found"),
    }

    // Iterate
    for (key, value) in &scores {
        println!("{}: {}", key, value);
    }

    // Update
    scores.insert(String::from("Blue"), 25);  // Overwrite

    // Only insert if key doesn't exist
    scores.entry(String::from("Green")).or_insert(50);

    // Update based on old value
    let text = "hello world wonderful world";
    let mut map = HashMap::new();

    for word in text.split_whitespace() {
        let count = map.entry(word).or_insert(0);
        *count += 1;
    }

    println!("{:?}", map);  // {"hello": 1, "world": 2, "wonderful": 1}

    // Remove
    scores.remove(&String::from("Blue"));

    // Check if key exists
    if scores.contains_key(&String::from("Blue")) {
        println!("Found Blue team");
    }
}

// ═══════════════════════════════════════════
// HashSet (Unique Values)
// ═══════════════════════════════════════════

use std::collections::HashSet;

fn hashset_examples() {
    let mut set = HashSet::new();

    // Insert
    set.insert(1);
    set.insert(2);
    set.insert(2);  // Duplicate ignored

    // Check membership
    if set.contains(&1) {
        println!("Found 1");
    }

    // Remove
    set.remove(&1);

    // Set operations
    let a: HashSet<_> = [1, 2, 3, 4].iter().collect();
    let b: HashSet<_> = [3, 4, 5, 6].iter().collect();

    // Union
    let union: HashSet<_> = a.union(&b).collect();
    println!("{:?}", union);  // {1, 2, 3, 4, 5, 6}

    // Intersection
    let intersection: HashSet<_> = a.intersection(&b).collect();
    println!("{:?}", intersection);  // {3, 4}

    // Difference
    let difference: HashSet<_> = a.difference(&b).collect();
    println!("{:?}", difference);  // {1, 2}

    // Symmetric difference
    let sym_diff: HashSet<_> = a.symmetric_difference(&b).collect();
    println!("{:?}", sym_diff);  // {1, 2, 5, 6}
}

// ═══════════════════════════════════════════
// VecDeque (Double-Ended Queue)
// ═══════════════════════════════════════════

use std::collections::VecDeque;

fn vecdeque_examples() {
    let mut deque = VecDeque::new();

    // Push/pop from front and back
    deque.push_back(1);
    deque.push_back(2);
    deque.push_front(0);

    println!("{:?}", deque);  // [0, 1, 2]

    deque.pop_front();  // Some(0)
    deque.pop_back();   // Some(2)
}

// ═══════════════════════════════════════════
// BTreeMap & BTreeSet (Sorted Collections)
// ═══════════════════════════════════════════

use std::collections::{BTreeMap, BTreeSet};

fn btree_examples() {
    // BTreeMap (sorted by key)
    let mut map = BTreeMap::new();
    map.insert(3, "c");
    map.insert(1, "a");
    map.insert(2, "b");

    for (k, v) in &map {
        println!("{}: {}", k, v);  // Prints in order: 1, 2, 3
    }

    // BTreeSet (sorted set)
    let mut set = BTreeSet::new();
    set.insert(3);
    set.insert(1);
    set.insert(2);

    println!("{:?}", set);  // {1, 2, 3}
}
```

---

### Iterators - Rust's Secret Weapon! 🚀

```rust
// ═══════════════════════════════════════════
// Iterator Basics
// ═══════════════════════════════════════════

fn iterator_basics() {
    let v = vec![1, 2, 3, 4, 5];

    // Create iterator
    let iter = v.iter();

    // For loop (consumes iterator)
    for val in &v {
        println!("{}", val);
    }

    // Manual iteration
    let mut iter = v.iter();
    assert_eq!(iter.next(), Some(&1));
    assert_eq!(iter.next(), Some(&2));

    // iter() - borrows
    let iter = v.iter();         // Iterator of &T

    // iter_mut() - mutable borrows
    let mut v = vec![1, 2, 3];
    let iter = v.iter_mut();     // Iterator of &mut T

    // into_iter() - takes ownership
    let iter = v.into_iter();    // Iterator of T (v consumed)
}

// ═══════════════════════════════════════════
// Iterator Adapters (Transformations)
// ═══════════════════════════════════════════

fn iterator_adapters() {
    let v = vec![1, 2, 3, 4, 5];

    // map - transform each element
    let doubled: Vec<i32> = v.iter().map(|x| x * 2).collect();
    println!("{:?}", doubled);  // [2, 4, 6, 8, 10]

    // filter - keep elements matching condition
    let evens: Vec<&i32> = v.iter().filter(|x| *x % 2 == 0).collect();
    println!("{:?}", evens);  // [2, 4]

    // filter_map - filter and map in one step
    let doubled_evens: Vec<i32> = v.iter()
        .filter_map(|x| {
            if x % 2 == 0 {
                Some(x * 2)
            } else {
                None
            }
        })
        .collect();

    // take - take first n elements
    let first_three: Vec<&i32> = v.iter().take(3).collect();
    println!("{:?}", first_three);  // [1, 2, 3]

    // skip - skip first n elements
    let skip_two: Vec<&i32> = v.iter().skip(2).collect();
    println!("{:?}", skip_two);  // [3, 4, 5]

    // chain - concatenate iterators
    let v2 = vec![6, 7, 8];
    let combined: Vec<&i32> = v.iter().chain(v2.iter()).collect();
    println!("{:?}", combined);  // [1, 2, 3, 4, 5, 6, 7, 8]

    // zip - combine two iterators
    let names = vec!["Alice", "Bob", "Charlie"];
    let ages = vec![25, 30, 35];
    let people: Vec<_> = names.iter().zip(ages.iter()).collect();
    println!("{:?}", people);  // [("Alice", 25), ("Bob", 30), ("Charlie", 35)]

    // enumerate - get index and value
    for (i, val) in v.iter().enumerate() {
        println!("Index {}: Value {}", i, val);
    }

    // rev - reverse iterator
    let reversed: Vec<&i32> = v.iter().rev().collect();
    println!("{:?}", reversed);  // [5, 4, 3, 2, 1]

    // cycle - repeat forever (use with take!)
    let repeated: Vec<&i32> = v.iter().cycle().take(10).collect();

    // flat_map - map and flatten
    let nested = vec![vec![1, 2], vec![3, 4], vec![5, 6]];
    let flattened: Vec<i32> = nested.iter()
        .flat_map(|inner| inner.iter().copied())
        .collect();
    println!("{:?}", flattened);  // [1, 2, 3, 4, 5, 6]

    // flatten - flatten nested structures
    let flattened: Vec<i32> = nested.iter()
        .flatten()
        .copied()
        .collect();
}

// ═══════════════════════════════════════════
// Iterator Consumers (Terminal Operations)
// ═══════════════════════════════════════════

fn iterator_consumers() {
    let v = vec![1, 2, 3, 4, 5];

    // collect - consume into collection
    let doubled: Vec<i32> = v.iter().map(|x| x * 2).collect();

    // sum - sum all elements
    let sum: i32 = v.iter().sum();
    println!("Sum: {}", sum);  // 15

    // product - multiply all elements
    let product: i32 = v.iter().product();
    println!("Product: {}", product);  // 120

    // min & max
    let min = v.iter().min();
    let max = v.iter().max();
    println!("Min: {:?}, Max: {:?}", min, max);  // Some(1), Some(5)

    // count - count elements
    let count = v.iter().filter(|x| *x % 2 == 0).count();
    println!("Even count: {}", count);  // 2

    // fold - accumulate (reduce)
    let sum = v.iter().fold(0, |acc, x| acc + x);
    println!("Sum: {}", sum);  // 15

    // reduce - similar to fold but returns Option
    let sum = v.iter().copied().reduce(|acc, x| acc + x);
    println!("Sum: {:?}", sum);  // Some(15)

    // find - find first matching element
    let first_even = v.iter().find(|&&x| x % 2 == 0);
    println!("First even: {:?}", first_even);  // Some(2)

    // position - find index of first match
    let pos = v.iter().position(|&x| x == 3);
    println!("Position of 3: {:?}", pos);  // Some(2)

    // any - check if any element matches
    let has_even = v.iter().any(|&x| x % 2 == 0);
    println!("Has even: {}", has_even);  // true

    // all - check if all elements match
    let all_positive = v.iter().all(|&x| x > 0);
    println!("All positive: {}", all_positive);  // true

    // partition - split into two collections
    let (evens, odds): (Vec<_>, Vec<_>) = v.iter()
        .partition(|&&x| x % 2 == 0);
    println!("Evens: {:?}, Odds: {:?}", evens, odds);

    // for_each - perform action on each element
    v.iter().for_each(|x| println!("{}", x));
}

// ═══════════════════════════════════════════
// Creating Custom Iterators
// ═══════════════════════════════════════════

struct Counter {
    count: u32,
}

impl Counter {
    fn new() -> Counter {
        Counter { count: 0 }
    }
}

impl Iterator for Counter {
    type Item = u32;

    fn next(&mut self) -> Option<Self::Item> {
        if self.count < 5 {
            self.count += 1;
            Some(self.count)
        } else {
            None
        }
    }
}

fn custom_iterator() {
    let counter = Counter::new();

    for num in counter {
        println!("{}", num);  // Prints 1, 2, 3, 4, 5
    }

    // Can use all iterator methods!
    let sum: u32 = Counter::new().sum();
    println!("Sum: {}", sum);  // 15
}
```

> **💡 Pro Tip:** Iterators in Rust are zero-cost abstractions - they compile down to the same machine code as hand-written loops! Chain iterator methods to write expressive, functional-style code.

<div align="center">

## 🧵 Concurrency & Async

</div>

### Fearless Concurrency 💪

```rust
// ═══════════════════════════════════════════
// Threads
// ═══════════════════════════════════════════

use std::thread;
use std::time::Duration;

fn thread_basics() {
    // Spawn a thread
    let handle = thread::spawn(|| {
        for i in 1..10 {
            println!("Thread: {}", i);
            thread::sleep(Duration::from_millis(1));
        }
    });

    // Main thread work
    for i in 1..5 {
        println!("Main: {}", i);
        thread::sleep(Duration::from_millis(1));
    }

    // Wait for thread to finish
    handle.join().unwrap();
}

// Thread with move closure
fn thread_with_move() {
    let v = vec![1, 2, 3];

    let handle = thread::spawn(move || {
        println!("Vector: {:?}", v);
    });

    // println!("{:?}", v);  // ❌ Error! v moved into thread

    handle.join().unwrap();
}

// Multiple threads
fn multiple_threads() {
    let mut handles = vec![];

    for i in 0..10 {
        let handle = thread::spawn(move || {
            println!("Thread {}", i);
        });
        handles.push(handle);
    }

    for handle in handles {
        handle.join().unwrap();
    }
}

// ═══════════════════════════════════════════
// Message Passing (Channels)
// ═══════════════════════════════════════════

use std::sync::mpsc;

fn channel_basics() {
    let (tx, rx) = mpsc::channel();

    thread::spawn(move || {
        let val = String::from("Hello from thread");
        tx.send(val).unwrap();
        // println!("{}", val);  // ❌ Error! val moved
    });

    let received = rx.recv().unwrap();
    println!("Received: {}", received);
}

// Multiple messages
fn multiple_messages() {
    let (tx, rx) = mpsc::channel();

    thread::spawn(move || {
        let vals = vec![
            String::from("hi"),
            String::from("from"),
            String::from("the"),
            String::from("thread"),
        ];

        for val in vals {
            tx.send(val).unwrap();
            thread::sleep(Duration::from_secs(1));
        }
    });

    // Receive messages as they come
    for received in rx {
        println!("Got: {}", received);
    }
}

// Multiple producers
fn multiple_producers() {
    let (tx, rx) = mpsc::channel();

    let tx1 = tx.clone();
    thread::spawn(move || {
        tx1.send(String::from("Message from thread 1")).unwrap();
    });

    thread::spawn(move || {
        tx.send(String::from("Message from thread 2")).unwrap();
    });

    for received in rx {
        println!("Got: {}", received);
    }
}

// ═══════════════════════════════════════════
// Shared State (Mutex)
// ═══════════════════════════════════════════

use std::sync::{Arc, Mutex};

fn mutex_basics() {
    let m = Mutex::new(5);

    {
        let mut num = m.lock().unwrap();
        *num = 6;
    }  // Lock released here

    println!("m = {:?}", m);
}

// Shared state across threads
fn shared_state() {
    let counter = Arc::new(Mutex::new(0));
    let mut handles = vec![];

    for _ in 0..10 {
        let counter = Arc::clone(&counter);
        let handle = thread::spawn(move || {
            let mut num = counter.lock().unwrap();
            *num += 1;
        });
        handles.push(handle);
    }

    for handle in handles {
        handle.join().unwrap();
    }

    println!("Result: {}", *counter.lock().unwrap());  // 10
}

// ═══════════════════════════════════════════
// RwLock (Multiple Readers, Single Writer)
// ═══════════════════════════════════════════

use std::sync::RwLock;

fn rwlock_example() {
    let lock = RwLock::new(5);

    // Multiple readers
    {
        let r1 = lock.read().unwrap();
        let r2 = lock.read().unwrap();
        println!("{}, {}", *r1, *r2);
    }  // Read locks released

    // Single writer
    {
        let mut w = lock.write().unwrap();
        *w += 1;
    }  // Write lock released
}

// ═══════════════════════════════════════════
// Atomic Types (Lock-Free Concurrency)
// ═══════════════════════════════════════════

use std::sync::atomic::{AtomicUsize, Ordering};

fn atomic_example() {
    let counter = Arc::new(AtomicUsize::new(0));
    let mut handles = vec![];

    for _ in 0..10 {
        let counter = Arc::clone(&counter);
        let handle = thread::spawn(move || {
            counter.fetch_add(1, Ordering::SeqCst);
        });
        handles.push(handle);
    }

    for handle in handles {
        handle.join().unwrap();
    }

    println!("Result: {}", counter.load(Ordering::SeqCst));  // 10
}

// ═══════════════════════════════════════════
// Async/Await with Tokio
// ═══════════════════════════════════════════

// Add to Cargo.toml:
// [dependencies]
// tokio = { version = "1", features = ["full"] }

use tokio;

#[tokio::main]
async fn main() {
    let result = fetch_data().await;
    println!("Result: {}", result);
}

async fn fetch_data() -> String {
    // Simulate async operation
    tokio::time::sleep(Duration::from_secs(1)).await;
    String::from("Data fetched!")
}

// Multiple async operations
async fn multiple_async() {
    // Sequential (slow)
    let data1 = fetch_data().await;
    let data2 = fetch_data().await;

    // Concurrent (fast!)
    let (data1, data2) = tokio::join!(
        fetch_data(),
        fetch_data()
    );

    // Select first to complete
    tokio::select! {
        result1 = fetch_data() => println!("First: {}", result1),
        result2 = fetch_data() => println!("Second: {}", result2),
    }
}

// Spawning async tasks
async fn spawn_tasks() {
    let handle1 = tokio::spawn(async {
        fetch_data().await
    });

    let handle2 = tokio::spawn(async {
        fetch_data().await
    });

    let result1 = handle1.await.unwrap();
    let result2 = handle2.await.unwrap();

    println!("{}, {}", result1, result2);
}

// Async HTTP request
async fn http_request() -> Result<String, reqwest::Error> {
    let body = reqwest::get("https://api.github.com/repos/rust-lang/rust")
        .await?
        .text()
        .await?;

    Ok(body)
}

// Stream processing
use tokio_stream::StreamExt;

async fn stream_example() {
    let mut stream = tokio_stream::iter(vec![1, 2, 3, 4, 5]);

    while let Some(value) = stream.next().await {
        println!("Got: {}", value);
    }
}
```

> **💡 Pro Tip:** Rust's ownership system makes thread safety guaranteed at compile time! No data races, no segfaults. For async programming, Tokio is the de-facto standard runtime. Use `Arc<Mutex<T>>` for shared mutable state across threads.

---

<div align="center">

## 🌐 Web Development

</div>

### Building Web Services 🚀

```rust
// ═══════════════════════════════════════════
// Actix-Web - High Performance Web Framework
// ═══════════════════════════════════════════

// Add to Cargo.toml:
// [dependencies]
// actix-web = "4"
// serde = { version = "1.0", features = ["derive"] }
// serde_json = "1.0"

use actix_web::{web, App, HttpServer, HttpResponse, Result};
use serde::{Deserialize, Serialize};

#[derive(Serialize, Deserialize)]
struct User {
    id: u32,
    name: String,
    email: String,
}

// Route handlers
async fn index() -> Result<HttpResponse> {
    Ok(HttpResponse::Ok().body("Hello, Rust Web! 🦀"))
}

async fn get_user(path: web::Path<u32>) -> Result<HttpResponse> {
    let user_id = path.into_inner();
    let user = User {
        id: user_id,
        name: String::from("MrDib"),
        email: String::from("mrdib@example.com"),
    };
    Ok(HttpResponse::Ok().json(user))
}

async fn create_user(user: web::Json<User>) -> Result<HttpResponse> {
    Ok(HttpResponse::Created().json(user.into_inner()))
}

// Query parameters
#[derive(Deserialize)]
struct SearchParams {
    q: String,
    page: Option<u32>,
}

async fn search(query: web::Query<SearchParams>) -> Result<HttpResponse> {
    let page = query.page.unwrap_or(1);
    Ok(HttpResponse::Ok().json(format!("Search: {}, Page: {}", query.q, page)))
}

// Complete Actix server
#[actix_web::main]
async fn main() -> std::io::Result<()> {
    println!("🚀 Server starting on http://localhost:8080");

    HttpServer::new(|| {
        App::new()
            .route("/", web::get().to(index))
            .route("/users/{id}", web::get().to(get_user))
            .route("/users", web::post().to(create_user))
            .route("/search", web::get().to(search))
    })
    .bind(("127.0.0.1", 8080))?
    .run()
    .await
}

// ═══════════════════════════════════════════
// Axum - Ergonomic Web Framework
// ═══════════════════════════════════════════

// Add to Cargo.toml:
// [dependencies]
// axum = "0.7"
// tokio = { version = "1", features = ["full"] }
// serde = { version = "1.0", features = ["derive"] }

use axum::{
    routing::{get, post},
    Router,
    Json,
    extract::{Path, Query},
};

// Handlers
async fn root() -> &'static str {
    "Hello, Axum! 🦀"
}

async fn get_user_axum(Path(id): Path<u32>) -> Json<User> {
    Json(User {
        id,
        name: String::from("MrDib"),
        email: String::from("mrdib@example.com"),
    })
}

async fn create_user_axum(Json(payload): Json<User>) -> Json<User> {
    Json(payload)
}

#[tokio::main]
async fn main() {
    let app = Router::new()
        .route("/", get(root))
        .route("/users/:id", get(get_user_axum))
        .route("/users", post(create_user_axum));

    let listener = tokio::net::TcpListener::bind("127.0.0.1:8080")
        .await
        .unwrap();

    println!("🚀 Server running on http://localhost:8080");

    axum::serve(listener, app).await.unwrap();
}

// ═══════════════════════════════════════════
// Middleware Example
// ═══════════════════════════════════════════

use axum::middleware::{self, Next};
use axum::http::Request;
use axum::response::Response;

async fn auth_middleware<B>(
    req: Request<B>,
    next: Next<B>,
) -> Result<Response, StatusCode> {
    let auth_header = req.headers()
        .get("Authorization")
        .and_then(|h| h.to_str().ok());

    if let Some(token) = auth_header {
        if validate_token(token) {
            return Ok(next.run(req).await);
        }
    }

    Err(StatusCode::UNAUTHORIZED)
}

fn validate_token(token: &str) -> bool {
    // Token validation logic
    !token.is_empty()
}

// Apply middleware
let app = Router::new()
    .route("/protected", get(protected_handler))
    .layer(middleware::from_fn(auth_middleware));

// ═══════════════════════════════════════════
// HTTP Client with Reqwest
// ═══════════════════════════════════════════

// Add to Cargo.toml:
// [dependencies]
// reqwest = { version = "0.11", features = ["json"] }

use reqwest;

async fn http_client_examples() -> Result<(), Box<dyn std::error::Error>> {
    // GET request
    let response = reqwest::get("https://api.github.com/repos/rust-lang/rust")
        .await?
        .json::<serde_json::Value>()
        .await?;

    println!("{:#?}", response);

    // POST request
    let client = reqwest::Client::new();
    let user = User {
        id: 0,
        name: String::from("MrDib"),
        email: String::from("mrdib@example.com"),
    };

    let res = client
        .post("https://api.example.com/users")
        .json(&user)
        .send()
        .await?;

    println!("Status: {}", res.status());

    // With headers
    let res = client
        .get("https://api.example.com/data")
        .header("Authorization", "Bearer token")
        .header("Content-Type", "application/json")
        .send()
        .await?;

    // Query parameters
    let res = client
        .get("https://api.example.com/search")
        .query(&[("q", "rust"), ("limit", "10")])
        .send()
        .await?;

    Ok(())
}
```

> **💡 Pro Tip:** Actix-Web is one of the fastest web frameworks in any language! Axum provides excellent ergonomics and integrates seamlessly with the Tokio ecosystem. Both are production-ready choices.

---

<div align="center">

## 🗄️ Database Operations

</div>

### Working with Databases 💾

```rust
// ═══════════════════════════════════════════
// SQLx - Async SQL Toolkit
// ═══════════════════════════════════════════

// Add to Cargo.toml:
// [dependencies]
// sqlx = { version = "0.7", features = ["runtime-tokio", "postgres"] }
// tokio = { version = "1", features = ["full"] }

use sqlx::{PgPool, FromRow};
use sqlx::postgres::PgPoolOptions;

#[derive(Debug, FromRow)]
struct User {
    id: i32,
    username: String,
    email: String,
}

// Connect to database
async fn connect_db() -> Result<PgPool, sqlx::Error> {
    let pool = PgPoolOptions::new()
        .max_connections(5)
        .connect("postgres://user:password@localhost/dbname")
        .await?;

    Ok(pool)
}

// CREATE table
async fn create_table(pool: &PgPool) -> Result<(), sqlx::Error> {
    sqlx::query(
        r#"
        CREATE TABLE IF NOT EXISTS users (
            id SERIAL PRIMARY KEY,
            username VARCHAR(50) UNIQUE NOT NULL,
            email VARCHAR(100) UNIQUE NOT NULL,
            created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
        )
        "#
    )
    .execute(pool)
    .await?;

    Ok(())
}

// INSERT
async fn create_user(pool: &PgPool, username: &str, email: &str) -> Result<User, sqlx::Error> {
    let user = sqlx::query_as::<_, User>(
        "INSERT INTO users (username, email) VALUES ($1, $2) RETURNING id, username, email"
    )
    .bind(username)
    .bind(email)
    .fetch_one(pool)
    .await?;

    Ok(user)
}

// SELECT one
async fn get_user_by_id(pool: &PgPool, id: i32) -> Result<Option<User>, sqlx::Error> {
    let user = sqlx::query_as::<_, User>(
        "SELECT id, username, email FROM users WHERE id = $1"
    )
    .bind(id)
    .fetch_optional(pool)
    .await?;

    Ok(user)
}

// SELECT multiple
async fn get_all_users(pool: &PgPool) -> Result<Vec<User>, sqlx::Error> {
    let users = sqlx::query_as::<_, User>(
        "SELECT id, username, email FROM users ORDER BY id"
    )
    .fetch_all(pool)
    .await?;

    Ok(users)
}

// UPDATE
async fn update_user(pool: &PgPool, id: i32, email: &str) -> Result<(), sqlx::Error> {
    sqlx::query("UPDATE users SET email = $1 WHERE id = $2")
        .bind(email)
        .bind(id)
        .execute(pool)
        .await?;

    Ok(())
}

// DELETE
async fn delete_user(pool: &PgPool, id: i32) -> Result<(), sqlx::Error> {
    sqlx::query("DELETE FROM users WHERE id = $1")
        .bind(id)
        .execute(pool)
        .await?;

    Ok(())
}

// Transaction
async fn transaction_example(pool: &PgPool) -> Result<(), sqlx::Error> {
    let mut tx = pool.begin().await?;

    sqlx::query("INSERT INTO users (username, email) VALUES ($1, $2)")
        .bind("user1")
        .bind("user1@example.com")
        .execute(&mut *tx)
        .await?;

    sqlx::query("INSERT INTO users (username, email) VALUES ($1, $2)")
        .bind("user2")
        .bind("user2@example.com")
        .execute(&mut *tx)
        .await?;

    tx.commit().await?;  // Or tx.rollback() on error

    Ok(())
}

// ═══════════════════════════════════════════
// Diesel - ORM for Rust
// ═══════════════════════════════════════════

// Add to Cargo.toml:
// [dependencies]
// diesel = { version = "2.1", features = ["postgres"] }
// dotenvy = "0.15"

// Install diesel CLI: cargo install diesel_cli --no-default-features --features postgres

use diesel::prelude::*;
use diesel::pg::PgConnection;

// Define schema (auto-generated by diesel)
diesel::table! {
    users (id) {
        id -> Int4,
        username -> Varchar,
        email -> Varchar,
    }
}

// Model
#[derive(Queryable, Selectable)]
#[diesel(table_name = users)]
struct User {
    id: i32,
    username: String,
    email: String,
}

// Insertable model
#[derive(Insertable)]
#[diesel(table_name = users)]
struct NewUser<'a> {
    username: &'a str,
    email: &'a str,
}

// Connect
fn establish_connection() -> PgConnection {
    let database_url = std::env::var("DATABASE_URL")
        .expect("DATABASE_URL must be set");
    PgConnection::establish(&database_url)
        .unwrap_or_else(|_| panic!("Error connecting to {}", database_url))
}

// CRUD operations
fn diesel_examples() {
    use self::users::dsl::*;

    let connection = &mut establish_connection();

    // CREATE
    let new_user = NewUser {
        username: "mrdib",
        email: "mrdib@example.com",
    };

    diesel::insert_into(users)
        .values(&new_user)
        .execute(connection)
        .expect("Error saving new user");

    // READ
    let results = users
        .filter(username.eq("mrdib"))
        .load::<User>(connection)
        .expect("Error loading users");

    // UPDATE
    diesel::update(users.find(1))
        .set(email.eq("newemail@example.com"))
        .execute(connection)
        .expect("Error updating user");

    // DELETE
    diesel::delete(users.find(1))
        .execute(connection)
        .expect("Error deleting user");
}
```

> **💡 Pro Tip:** SQLx provides compile-time checked queries - typos in SQL are caught at compile time! Diesel is a full-featured ORM with a query builder DSL. Choose SQLx for raw SQL with safety, Diesel for ORM features.

---

<div align="center">

## 📂 File I/O

</div>

### Reading & Writing Files 📄

```rust
// ═══════════════════════════════════════════
// Reading Files
// ═══════════════════════════════════════════

use std::fs;
use std::io::{self, Read, Write, BufRead, BufReader};

// Read entire file to string
fn read_to_string() -> io::Result<String> {
    let contents = fs::read_to_string("hello.txt")?;
    Ok(contents)
}

// Read file to bytes
fn read_to_bytes() -> io::Result<Vec<u8>> {
    let contents = fs::read("hello.txt")?;
    Ok(contents)
}

// Read file line by line
fn read_lines() -> io::Result<()> {
    let file = fs::File::open("hello.txt")?;
    let reader = BufReader::new(file);

    for line in reader.lines() {
        let line = line?;
        println!("{}", line);
    }

    Ok(())
}

// Read with manual buffer
fn read_with_buffer() -> io::Result<()> {
    let mut file = fs::File::open("hello.txt")?;
    let mut buffer = [0; 1024];

    loop {
        let n = file.read(&mut buffer)?;
        if n == 0 { break; }

        // Process buffer[..n]
        println!("Read {} bytes", n);
    }

    Ok(())
}

// ═══════════════════════════════════════════
// Writing Files
// ═══════════════════════════════════════════

// Write entire string to file
fn write_to_file() -> io::Result<()> {
    fs::write("output.txt", "Hello, Rust!")?;
    Ok(())
}

// Write bytes to file
fn write_bytes() -> io::Result<()> {
    let data = vec![72, 101, 108, 108, 111];  // "Hello"
    fs::write("output.bin", data)?;
    Ok(())
}

// Append to file
fn append_to_file() -> io::Result<()> {
    use std::fs::OpenOptions;

    let mut file = OpenOptions::new()
        .append(true)
        .create(true)
        .open("log.txt")?;

    writeln!(file, "New log entry")?;
    Ok(())
}

// Buffered writing
fn buffered_write() -> io::Result<()> {
    use std::io::BufWriter;

    let file = fs::File::create("output.txt")?;
    let mut writer = BufWriter::new(file);

    for i in 0..1000 {
        writeln!(writer, "Line {}", i)?;
    }

    writer.flush()?;  // Important!
    Ok(())
}

// ═══════════════════════════════════════════
// File Operations
// ═══════════════════════════════════════════

// Check if file exists
fn file_exists() -> bool {
    std::path::Path::new("hello.txt").exists()
}

// Get file metadata
fn file_metadata() -> io::Result<()> {
    let metadata = fs::metadata("hello.txt")?;

    println!("Size: {} bytes", metadata.len());
    println!("Is file: {}", metadata.is_file());
    println!("Is directory: {}", metadata.is_dir());
    println!("Modified: {:?}", metadata.modified()?);

    Ok(())
}

// Copy file
fn copy_file() -> io::Result<()> {
    fs::copy("source.txt", "destination.txt")?;
    Ok(())
}

// Rename/move file
fn rename_file() -> io::Result<()> {
    fs::rename("old_name.txt", "new_name.txt")?;
    Ok(())
}

// Delete file
fn delete_file() -> io::Result<()> {
    fs::remove_file("unwanted.txt")?;
    Ok(())
}

// ═══════════════════════════════════════════
// Directory Operations
// ═══════════════════════════════════════════

// Create directory
fn create_dir() -> io::Result<()> {
    fs::create_dir("my_folder")?;
    Ok(())
}

// Create nested directories
fn create_dirs() -> io::Result<()> {
    fs::create_dir_all("path/to/nested/folder")?;
    Ok(())
}

// Read directory contents
fn read_dir() -> io::Result<()> {
    for entry in fs::read_dir(".")? {
        let entry = entry?;
        println!("{:?}", entry.path());
    }
    Ok(())
}

// Remove directory
fn remove_dir() -> io::Result<()> {
    fs::remove_dir("empty_folder")?;  // Must be empty
    Ok(())
}

// Remove directory and contents
fn remove_dir_all() -> io::Result<()> {
    fs::remove_dir_all("folder_with_contents")?;
    Ok(())
}

// Walk directory tree
fn walk_dir() -> io::Result<()> {
    use walkdir::WalkDir;  // cargo add walkdir

    for entry in WalkDir::new(".") {
        let entry = entry?;
        println!("{}", entry.path().display());
    }
    Ok(())
}

// ═══════════════════════════════════════════
// Working with Paths
// ═══════════════════════════════════════════

use std::path::{Path, PathBuf};

fn path_operations() {
    let path = Path::new("folder/file.txt");

    // Path components
    println!("File name: {:?}", path.file_name());
    println!("Extension: {:?}", path.extension());
    println!("Parent: {:?}", path.parent());

    // Build paths
    let mut path_buf = PathBuf::from("folder");
    path_buf.push("subfolder");
    path_buf.push("file.txt");
    println!("{:?}", path_buf);  // "folder/subfolder/file.txt"

    // Join paths
    let path = Path::new("folder").join("file.txt");

    // Check path type
    if path.is_file() {
        println!("It's a file");
    }
    if path.is_dir() {
        println!("It's a directory");
    }
}

// ═══════════════════════════════════════════
// JSON File Operations
// ═══════════════════════════════════════════

use serde::{Deserialize, Serialize};
use serde_json;

#[derive(Serialize, Deserialize)]
struct Config {
    host: String,
    port: u16,
    database: String,
}

// Read JSON file
fn read_json() -> Result<Config, Box<dyn std::error::Error>> {
    let contents = fs::read_to_string("config.json")?;
    let config: Config = serde_json::from_str(&contents)?;
    Ok(config)
}

// Write JSON file
fn write_json(config: &Config) -> Result<(), Box<dyn std::error::Error>> {
    let json = serde_json::to_string_pretty(config)?;
    fs::write("config.json", json)?;
    Ok(())
}

// ═══════════════════════════════════════════
// TOML File Operations
// ═══════════════════════════════════════════

use toml;  // cargo add toml

// Read TOML file
fn read_toml() -> Result<Config, Box<dyn std::error::Error>> {
    let contents = fs::read_to_string("config.toml")?;
    let config: Config = toml::from_str(&contents)?;
    Ok(config)
}

// Write TOML file
fn write_toml(config: &Config) -> Result<(), Box<dyn std::error::Error>> {
    let toml = toml::to_string(config)?;
    fs::write("config.toml", toml)?;
    Ok(())
}
```

> **💡 Pro Tip:** Always use `?` for error propagation in I/O operations. Use `BufReader` and `BufWriter` for better performance with large files. The `Path` and `PathBuf` types handle cross-platform path differences!

---

<div align="center">

## 🧪 Testing

</div>

### Test-Driven Development 🎯

````rust
// ═══════════════════════════════════════════
// Unit Tests
// ═══════════════════════════════════════════

// Function to test
pub fn add(a: i32, b: i32) -> i32 {
    a + b
}

// Tests module
#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    fn test_add() {
        assert_eq!(add(2, 2), 4);
        assert_eq!(add(-1, 1), 0);
    }

    #[test]
    fn test_add_negative() {
        assert_eq!(add(-2, -3), -5);
    }

    #[test]
    #[should_panic]
    fn test_panic() {
        panic!("This should panic");
    }

    #[test]
    #[should_panic(expected = "divide by zero")]
    fn test_specific_panic() {
        divide_by_zero();
    }

    #[test]
    fn test_with_result() -> Result<(), String> {
        if 2 + 2 == 4 {
            Ok(())
        } else {
            Err(String::from("Math is broken"))
        }
    }

    #[test]
    #[ignore]
    fn expensive_test() {
        // This test is ignored by default
        // Run with: cargo test -- --ignored
    }
}

// ═══════════════════════════════════════════
// Assertion Macros
// ═══════════════════════════════════════════

#[test]
fn assertion_examples() {
    // assert!
    assert!(true);
    assert!(2 + 2 == 4);

    // assert_eq!
    assert_eq!(2 + 2, 4);
    assert_eq!("hello".to_string(), String::from("hello"));

    // assert_ne!
    assert_ne!(2 + 2, 5);

    // Custom message
    assert!(
        2 + 2 == 4,
        "Math is broken: {} + {} should equal {}",
        2, 2, 4
    );
}

// ═══════════════════════════════════════════
// Testing Private Functions
// ═══════════════════════════════════════════

fn private_function(x: i32) -> i32 {
    x * 2
}

#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    fn test_private() {
        assert_eq!(private_function(5), 10);
    }
}

// ═══════════════════════════════════════════
// Integration Tests (tests/ directory)
// ═══════════════════════════════════════════

// tests/integration_test.rs
use my_crate;

#[test]
fn test_public_api() {
    assert_eq!(my_crate::add(2, 2), 4);
}

// ═══════════════════════════════════════════
// Test Organization
// ═══════════════════════════════════════════

#[cfg(test)]
mod tests {
    use super::*;

    mod addition {
        use super::*;

        #[test]
        fn positive_numbers() {
            assert_eq!(add(2, 3), 5);
        }

        #[test]
        fn negative_numbers() {
            assert_eq!(add(-2, -3), -5);
        }
    }

    mod subtraction {
        use super::*;

        #[test]
        fn basic() {
            assert_eq!(subtract(5, 3), 2);
        }
    }
}

// ═══════════════════════════════════════════
// Documentation Tests
// ═══════════════════════════════════════════

/// Adds two numbers together.
///
/// # Examples
///
/// ```
/// let result = my_crate::add(2, 2);
/// assert_eq!(result, 4);
/// ```
///
/// ```
/// # use my_crate::add;
/// let result = add(-1, 1);
/// assert_eq!(result, 0);
/// ```
pub fn add(a: i32, b: i32) -> i32 {
    a + b
}

// ═══════════════════════════════════════════
// Benchmarking with Criterion
// ═══════════════════════════════════════════

// Add to Cargo.toml:
// [dev-dependencies]
// criterion = "0.5"

// benches/benchmark.rs
use criterion::{black_box, criterion_group, criterion_main, Criterion};

fn fibonacci(n: u64) -> u64 {
    match n {
        0 => 1,
        1 => 1,
        n => fibonacci(n - 1) + fibonacci(n - 2),
    }
}

fn criterion_benchmark(c: &mut Criterion) {
    c.bench_function("fib 20", |b| b.iter(|| fibonacci(black_box(20))));
}

criterion_group!(benches, criterion_benchmark);
criterion_main!(benches);

// Run with: cargo bench

// ═══════════════════════════════════════════
// Test Utilities
// ═══════════════════════════════════════════

// Test helper functions
#[cfg(test)]
mod test_helpers {
    pub fn create_test_user() -> User {
        User {
            id: 1,
            name: String::from("testuser"),
            email: String::from("test@example.com"),
        }
    }
}

#[test]
fn test_with_helper() {
    let user = test_helpers::create_test_user();
    assert_eq!(user.name, "testuser");
}
````

### Running Tests 🏃

```bash
# ═══════════════════════════════════════════
# Test Commands
# ═══════════════════════════════════════════

# Run all tests
cargo test

# Run tests with output
cargo test -- --nocapture

# Run specific test
cargo test test_add

# Run tests matching pattern
cargo test addition

# Run ignored tests
cargo test -- --ignored

# Run tests in single thread
cargo test -- --test-threads=1

# Run doc tests only
cargo test --doc

# Run integration tests only
cargo test --test integration_test

# ═══════════════════════════════════════════
# Coverage
# ═══════════════════════════════════════════

# Install tarpaulin
cargo install cargo-tarpaulin

# Generate coverage
cargo tarpaulin --out Html

# ═══════════════════════════════════════════
# Benchmarks
# ═══════════════════════════════════════════

# Run benchmarks
cargo bench

# Run specific benchmark
cargo bench fib

# Compare benchmarks
cargo bench -- --save-baseline baseline
# Make changes
cargo bench -- --baseline baseline
```

> **💡 Pro Tip:** Write tests as you code! Rust's testing framework is built-in and fast. Use `cargo test` frequently during development. Documentation tests ensure your examples actually work!

---

<div align="center">

## 🎯 Common Patterns

</div>

### Idiomatic Rust Patterns 📐

```rust
// ═══════════════════════════════════════════
// Builder Pattern
// ═══════════════════════════════════════════

struct User {
    name: String,
    email: String,
    age: Option<u8>,
    is_active: bool,
}

struct UserBuilder {
    name: String,
    email: String,
    age: Option<u8>,
    is_active: bool,
}

impl UserBuilder {
    fn new(name: String, email: String) -> Self {
        Self {
            name,
            email,
            age: None,
            is_active: true,
        }
    }

    fn age(mut self, age: u8) -> Self {
        self.age = Some(age);
        self
    }

    fn inactive(mut self) -> Self {
        self.is_active = false;
        self
    }

    fn build(self) -> User {
        User {
            name: self.name,
            email: self.email,
            age: self.age,
            is_active: self.is_active,
        }
    }
}

// Usage
fn builder_example() {
    let user = UserBuilder::new(
        String::from("MrDib"),
        String::from("mrdib@example.com")
    )
    .age(25)
    .build();
}

// ═══════════════════════════════════════════
// Newtype Pattern (Type Safety)
// ═══════════════════════════════════════════

struct UserId(u32);
struct ProductId(u32);

// Can't accidentally mix them up!
fn get_user(id: UserId) -> User {
    // implementation
}

// fn get_user(id: ProductId) -> User {  // ❌ Compile error!

// Deriving traits for newtypes
#[derive(Debug, Clone, Copy, PartialEq, Eq, Hash)]
struct Meters(f64);

#[derive(Debug, Clone, Copy, PartialEq, Eq, Hash)]
struct Kilometers(f64);

impl From<Kilometers> for Meters {
    fn from(km: Kilometers) -> Self {
        Meters(km.0 * 1000.0)
    }
}

// ═══════════════════════════════════════════
// State Pattern
// ═══════════════════════════════════════════

struct Draft {
    content: String,
}

struct PendingReview {
    content: String,
}

struct Published {
    content: String,
}

struct Post {
    state: PostState,
}

enum PostState {
    Draft(Draft),
    PendingReview(PendingReview),
    Published(Published),
}

impl Post {
    fn new() -> Post {
        Post {
            state: PostState::Draft(Draft {
                content: String::new(),
            }),
        }
    }

    fn add_text(&mut self, text: &str) {
        match &mut self.state {
            PostState::Draft(draft) => {
                draft.content.push_str(text);
            }
            _ => {}  // Can only add text in draft state
        }
    }

    fn request_review(self) -> Post {
        match self.state {
            PostState::Draft(draft) => Post {
                state: PostState::PendingReview(PendingReview {
                    content: draft.content,
                }),
            },
            _ => self,
        }
    }

    fn approve(self) -> Post {
        match self.state {
            PostState::PendingReview(pending) => Post {
                state: PostState::Published(Published {
                    content: pending.content,
                }),
            },
            _ => self,
        }
    }

    fn content(&self) -> &str {
        match &self.state {
            PostState::Published(published) => &published.content,
            _ => "",
        }
    }
}

// ═══════════════════════════════════════════
// Command Pattern
// ═══════════════════════════════════════════

trait Command {
    fn execute(&self);
    fn undo(&self);
}

struct MoveCommand {
    x: i32,
    y: i32,
}

impl Command for MoveCommand {
    fn execute(&self) {
        println!("Moving to ({}, {})", self.x, self.y);
    }

    fn undo(&self) {
        println!("Moving back from ({}, {})", self.x, self.y);
    }
}

struct CommandHistory {
    commands: Vec<Box<dyn Command>>,
}

impl CommandHistory {
    fn new() -> Self {
        Self {
            commands: Vec::new(),
        }
    }

    fn execute(&mut self, command: Box<dyn Command>) {
        command.execute();
        self.commands.push(command);
    }

    fn undo(&mut self) {
        if let Some(command) = self.commands.pop() {
            command.undo();
        }
    }
}

// ═══════════════════════════════════════════
// Visitor Pattern
// ═══════════════════════════════════════════

trait Visitor {
    fn visit_file(&self, file: &File);
    fn visit_directory(&self, directory: &Directory);
}

trait Element {
    fn accept(&self, visitor: &dyn Visitor);
}

struct File {
    name: String,
    size: u64,
}

struct Directory {
    name: String,
    children: Vec<Box<dyn Element>>,
}

impl Element for File {
    fn accept(&self, visitor: &dyn Visitor) {
        visitor.visit_file(self);
    }
}

impl Element for Directory {
    fn accept(&self, visitor: &dyn Visitor) {
        visitor.visit_directory(self);
        for child in &self.children {
            child.accept(visitor);
        }
    }
}

struct SizeCalculator {
    total_size: std::cell::RefCell<u64>,
}

impl Visitor for SizeCalculator {
    fn visit_file(&self, file: &File) {
        *self.total_size.borrow_mut() += file.size;
    }

    fn visit_directory(&self, _directory: &Directory) {
        // Just traverse
    }
}

// ═══════════════════════════════════════════
// RAII Pattern (Resource Acquisition Is Initialization)
// ═══════════════════════════════════════════

struct DatabaseConnection {
    // connection details
}

impl DatabaseConnection {
    fn new() -> Self {
        println!("Opening database connection");
        DatabaseConnection {}
    }
}

impl Drop for DatabaseConnection {
    fn drop(&mut self) {
        println!("Closing database connection");
    }
}

fn raii_example() {
    let _conn = DatabaseConnection::new();
    // Connection automatically closed when _conn goes out of scope
}

// ═══════════════════════════════════════════
// Interior Mutability Pattern
// ═══════════════════════════════════════════

use std::cell::{RefCell, Cell};
use std::rc::Rc;

struct SharedState {
    data: RefCell<Vec<String>>,
    counter: Cell<u32>,
}

impl SharedState {
    fn new() -> Self {
        Self {
            data: RefCell::new(Vec::new()),
            counter: Cell::new(0),
        }
    }

    fn add(&self, item: String) {
        self.data.borrow_mut().push(item);
        self.counter.set(self.counter.get() + 1);
    }
}

// ═══════════════════════════════════════════
// Type State Pattern
// ═══════════════════════════════════════════

struct Locked;
struct Unlocked;

struct Door<State> {
    state: std::marker::PhantomData<State>,
}

impl Door<Locked> {
    fn new() -> Self {
        Door {
            state: std::marker::PhantomData,
        }
    }

    fn unlock(self) -> Door<Unlocked> {
        println!("Unlocking door");
        Door {
            state: std::marker::PhantomData,
        }
    }
}

impl Door<Unlocked> {
    fn open(&self) {
        println!("Opening door");
    }

    fn lock(self) -> Door<Locked> {
        println!("Locking door");
        Door {
            state: std::marker::PhantomData,
        }
    }
}

fn type_state_example() {
    let door = Door::<Locked>::new();
    // door.open();  // ❌ Compile error! Can't open locked door

    let door = door.unlock();
    door.open();  // ✅ OK!

    let door = door.lock();
}

// ═══════════════════════════════════════════
// Extension Trait Pattern
// ═══════════════════════════════════════════

trait StringExtensions {
    fn is_palindrome(&self) -> bool;
    fn word_count(&self) -> usize;
}

impl StringExtensions for str {
    fn is_palindrome(&self) -> bool {
        let chars: Vec<char> = self.chars().collect();
        chars.iter().eq(chars.iter().rev())
    }

    fn word_count(&self) -> usize {
        self.split_whitespace().count()
    }
}

fn extension_trait_example() {
    let text = "hello world";
    println!("Word count: {}", text.word_count());
    println!("Is palindrome: {}", text.is_palindrome());
}
```

> **💡 Pro Tip:** Rust's type system enables powerful compile-time guarantees. Use the type state pattern to make invalid states unrepresentable! The newtype pattern provides zero-cost abstraction.

---

<div align="center">

## 💡 Best Practices

</div>

### Rust Best Practices & Style Guide ⭐

````rust
// ═══════════════════════════════════════════
// Naming Conventions
// ═══════════════════════════════════════════

// ✅ Variables & functions: snake_case
let user_count = 42;
fn calculate_total() {}

// ✅ Types & traits: PascalCase
struct UserAccount {}
trait Drawable {}

// ✅ Constants: SCREAMING_SNAKE_CASE
const MAX_CONNECTIONS: u32 = 100;

// ✅ Lifetimes: short, lowercase
fn longest<'a>(x: &'a str, y: &'a str) -> &'a str {}

// ✅ Type parameters: Single uppercase letter or PascalCase
fn generic<T>(item: T) {}
fn process<TItem>(item: TItem) {}

// ═══════════════════════════════════════════
// Error Handling
// ═══════════════════════════════════════════

// ✅ DO: Use Result for recoverable errors
fn divide(a: f64, b: f64) -> Result<f64, String> {
    if b == 0.0 {
        Err(String::from("Division by zero"))
    } else {
        Ok(a / b)
    }
}

// ✅ DO: Use ? operator
fn read_config() -> Result<String, std::io::Error> {
    let contents = std::fs::read_to_string("config.toml")?;
    Ok(contents)
}

// ❌ DON'T: Use unwrap in production code
fn bad_example() {
    let file = std::fs::File::open("config.toml").unwrap();  // Could panic!
}

// ✅ DO: Use expect with descriptive messages (better than unwrap)
fn better_example() {
    let file = std::fs::File::open("config.toml")
        .expect("Failed to open config.toml");
}

// ═══════════════════════════════════════════
// Ownership & Borrowing
// ═══════════════════════════════════════════

// ✅ DO: Use references when you don't need ownership
fn process_data(data: &[u8]) {
    // Just reading data
}

// ❌ DON'T: Take ownership unnecessarily
fn bad_process_data(data: Vec<u8>) {
    // Takes ownership, caller loses data
}

// ✅ DO: Use &str for string parameters
fn print_message(msg: &str) {
    println!("{}", msg);
}

// ❌ DON'T: Use String unnecessarily
fn bad_print_message(msg: String) {
    // Forces caller to convert or give up ownership
}

// ✅ DO: Return owned types
fn create_message() -> String {
    String::from("Hello")
}

// ❌ DON'T: Return references without good reason
fn bad_create_message() -> &'static str {
    // Limited to static strings
    "Hello"
}

// ═══════════════════════════════════════════
// Collections & Iterators
// ═══════════════════════════════════════════

// ✅ DO: Use iterator methods
let numbers = vec![1, 2, 3, 4, 5];
let sum: i32 = numbers.iter().sum();
let doubled: Vec<i32> = numbers.iter().map(|x| x * 2).collect();

// ❌ DON'T: Use explicit loops unnecessarily
let mut sum = 0;
for num in &numbers {
    sum += num;
}

// ✅ DO: Pre-allocate when size is known
let mut vec = Vec::with_capacity(100);

// ✅ DO: Use iterators instead of indexing
for item in &items {
    println!("{}", item);
}

// ❌ DON'T: Index into collections
for i in 0..items.len() {
    println!("{}", items[i]);  // Could panic, less idiomatic
}

// ═══════════════════════════════════════════
// Option & Result
// ═══════════════════════════════════════════

// ✅ DO: Use combinators
let result = some_option
    .map(|x| x * 2)
    .filter(|x| x > &10)
    .unwrap_or(0);

// ❌ DON'T: Use match for simple cases
let result = match some_option {
    Some(x) => x * 2,
    None => 0,
};

// ✅ DO: Use if let for single pattern
if let Some(value) = some_option {
    println!("{}", value);
}

// ❌ DON'T: Use match for single pattern
match some_option {
    Some(value) => println!("{}", value),
    None => {}
}

// ═══════════════════════════════════════════
// Struct & Enum Design
// ═══════════════════════════════════════════

// ✅ DO: Use descriptive field names
struct User {
    username: String,
    email: String,
    created_at: DateTime<Utc>,
}

// ❌ DON'T: Use abbreviated names
struct User {
    usr: String,
    em: String,
    ct: DateTime<Utc>,
}

// ✅ DO: Derive common traits
#[derive(Debug, Clone, PartialEq)]
struct Point {
    x: i32,
    y: i32,
}

// ✅ DO: Use enums for variants
enum Status {
    Active,
    Inactive,
    Pending,
}

// ❌ DON'T: Use multiple booleans
struct Account {
    is_active: bool,
    is_pending: bool,
    is_suspended: bool,  // Complex logic!
}

// ═══════════════════════════════════════════
// Performance Tips
// ═══════════════════════════════════════════

// ✅ DO: Use string slices when possible
fn count_words(text: &str) -> usize {
    text.split_whitespace().count()
}

// ✅ DO: Avoid unnecessary clones
let data = expensive_operation();
process_data(&data);  // Borrow instead of clone

// ✅ DO: Use Cow for conditional cloning
use std::borrow::Cow;

fn process_text(text: Cow<str>) -> Cow<str> {
    if text.contains("replace") {
        Cow::Owned(text.replace("replace", "new"))
    } else {
        text  // No allocation if no change needed
    }
}

// ✅ DO: Use inline for small, hot functions
#[inline]
fn add(a: i32, b: i32) -> i32 {
    a + b
}

// ═══════════════════════════════════════════
// Code Organization
// ═══════════════════════════════════════════

// ✅ DO: Use modules to organize code
mod models {
    pub struct User {
        pub id: u32,
        pub name: String,
    }
}

mod handlers {
    use super::models::User;

    pub fn get_user(id: u32) -> User {
        // implementation
    }
}

// ✅ DO: Re-export commonly used types
pub use self::models::{User, Product};

// ✅ DO: Use descriptive module names
mod database;
mod authentication;
mod user_management;

// ❌ DON'T: Use generic names
mod utils;  // Too vague
mod helpers;  // What kind of helpers?

// ═══════════════════════════════════════════
// Documentation
// ═══════════════════════════════════════════

// ✅ DO: Document public APIs
/// Calculates the area of a circle.
///
/// # Arguments
///
/// * `radius` - The radius of the circle
///
/// # Examples
///
/// ```
/// let area = calculate_area(5.0);
/// assert_eq!(area, 78.53981633974483);
/// ```
///
/// # Panics
///
/// Panics if radius is negative.
pub fn calculate_area(radius: f64) -> f64 {
    assert!(radius >= 0.0, "Radius cannot be negative");
    std::f64::consts::PI * radius * radius
}

// ✅ DO: Use //! for module-level docs
//! This module handles user authentication.
//!
//! It provides functions for login, logout, and session management.

// ═══════════════════════════════════════════
// Testing
// ═══════════════════════════════════════════

// ✅ DO: Write tests for public APIs
#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    fn test_add() {
        assert_eq!(add(2, 2), 4);
    }

    #[test]
    fn test_divide_by_zero() {
        assert!(divide(10.0, 0.0).is_err());
    }
}

// ✅ DO: Use descriptive test names
#[test]
fn user_creation_with_valid_email_succeeds() {
    // test implementation
}

// ❌ DON'T: Use generic test names
#[test]
fn test1() {
    // What does this test?
}

// ═══════════════════════════════════════════
// Cargo.toml Best Practices
// ═══════════════════════════════════════════

/*
[package]
name = "my_project"
version = "0.1.0"
edition = "2021"
authors = ["MrDib <mrdib@example.com>"]
license = "MIT OR Apache-2.0"
description = "A brief description"
repository = "https://github.com/mrdib/my_project"
keywords = ["cli", "tool"]
categories = ["command-line-utilities"]

[dependencies]
# Pin major versions
serde = "1.0"
tokio = { version = "1", features = ["full"] }

[dev-dependencies]
criterion = "0.5"

[profile.release]
opt-level = 3
lto = true
codegen-units = 1
strip = true  # Remove debug symbols
*/
````

> **💡 Pro Tip:** Run `cargo clippy` regularly - it catches common mistakes and suggests idiomatic improvements. Use `cargo fmt` to maintain consistent style. Read the Rust API Guidelines for comprehensive best practices!

---

<div align="center">

## 🎓 Rust Resources & Tools

### _Level up your Rust game!_ 📚

</div>

### Essential Tools 🛠️

```bash
# ═══════════════════════════════════════════
# Code Quality Tools
# ═══════════════════════════════════════════

# rustfmt - Code formatter
cargo fmt
rustfmt --check src/main.rs

# Clippy - Linter
cargo clippy
cargo clippy -- -D warnings  # Deny warnings

# cargo-audit - Security vulnerabilities
cargo install cargo-audit
cargo audit

# cargo-outdated - Check outdated dependencies
cargo install cargo-outdated
cargo outdated

# cargo-tree - Dependency tree
cargo tree

# cargo-expand - Expand macros
cargo install cargo-expand
cargo expand

# ═══════════════════════════════════════════
# Development Tools
# ═══════════════════════════════════════════

# rust-analyzer - LSP server for IDEs
rustup component add rust-analyzer

# cargo-watch - Auto-rebuild on changes
cargo install cargo-watch
cargo watch -x run
cargo watch -x test

# cargo-edit - Manage dependencies from CLI
cargo install cargo-edit
cargo add serde
cargo rm tokio
cargo upgrade

# ═══════════════════════════════════════════
# Testing & Benchmarking
# ═══════════════════════════════════════════

# cargo-tarpaulin - Code coverage
cargo install cargo-tarpaulin
cargo tarpaulin --out Html

# cargo-nextest - Faster test runner
cargo install cargo-nextest
cargo nextest run

# cargo-criterion - Benchmarking
# (Add criterion to dev-dependencies)
cargo bench

# ═══════════════════════════════════════════
# Documentation
# ═══════════════════════════════════════════

# Generate documentation
cargo doc --open

# Check documentation
cargo doc --no-deps

# ═══════════════════════════════════════════
# Build & Release
# ═══════════════════════════════════════════

# Build for different targets
rustup target add x86_64-pc-windows-gnu
cargo build --target x86_64-pc-windows-gnu

# Release build with optimizations
cargo build --release

# cargo-bloat - Find large dependencies
cargo install cargo-bloat
cargo bloat --release
```

---

### Learning Resources 📖

```
📘 Official Resources
   - The Rust Book: https://doc.rust-lang.org/book/
   - Rust by Example: https://doc.rust-lang.org/rust-by-example/
   - The Cargo Book: https://doc.rust-lang.org/cargo/
   - Rustlings (Exercises): https://github.com/rust-lang/rustlings
   - Rust Playground: https://play.rust-lang.org/

📗 Advanced Learning
   - The Rustonomicon: https://doc.rust-lang.org/nomicon/
   - Async Book: https://rust-lang.github.io/async-book/
   - Rust API Guidelines: https://rust-lang.github.io/api-guidelines/
   - Rust Design Patterns: https://rust-unofficial.github.io/patterns/
   - Rust Performance Book: https://nnethercote.github.io/perf-book/

📙 Books
   - "Programming Rust" by Jim Blandy & Jason Orendorff
   - "Rust in Action" by Tim McNamara
   - "Zero to Production in Rust" by Luca Palmieri
   - "Rust for Rustaceans" by Jon Gjengset

🎥 Video Resources
   - Jon Gjengset (YouTube) - Advanced Rust concepts
   - Ryan Levick (YouTube) - Rust for beginners
   - No Boilerplate (YouTube) - Quick Rust videos
   - Let's Get Rusty (YouTube) - Tutorials & news

🏋️ Practice
   - Exercism.io Rust Track
   - LeetCode (Rust problems)
   - Advent of Code (in Rust)
   - Codewars Rust challenges

🌐 Community
   - r/rust (Reddit)
   - Rust Users Forum: https://users.rust-lang.org/
   - Rust Discord: https://discord.gg/rust-lang
   - This Week in Rust: https://this-week-in-rust.org/

📦 Essential Crates
   - serde: Serialization/deserialization
   - tokio: Async runtime
   - reqwest: HTTP client
   - actix-web / axum: Web frameworks
   - clap: CLI argument parsing
   - anyhow / thiserror: Error handling
   - tracing: Logging & instrumentation
   - sqlx / diesel: Database access
```

---

<div align="center">

## 🏆 You've Mastered Rust!

### _From zero to Rustacean_ 🎉

</div>

**You now know:**

- ✅ Rust fundamentals & syntax
- ✅ Ownership, borrowing & lifetimes
- ✅ Data types & collections
- ✅ Structs, enums & pattern matching
- ✅ Traits & generics
- ✅ Error handling the Rust way
- ✅ Iterators & functional programming
- ✅ Concurrency & async programming
- ✅ Web development with Rust
- ✅ Database operations
- ✅ File I/O operations
- ✅ Testing & benchmarking
- ✅ Common design patterns
- ✅ Best practices & optimization

---

<div align="center">

### The Rust Philosophy 🦀

> **"Fearless concurrency"**

> **"Zero-cost abstractions"**

> **"Move fast and don't break things"**

> **"If it compiles, it usually works"**

> **"Fight the borrow checker until you understand it, then it becomes your friend"**

</div>

---

### Quick Reference Card 📇

```rust
// Variables
let x = 5;              // Immutable
let mut y = 10;         // Mutable
const MAX: u32 = 100;   // Constant

// Functions
fn add(a: i32, b: i32) -> i32 {
    a + b  // No semicolon = return
}

// Structs
struct Point { x: i32, y: i32 }

// Enums
enum Option<T> {
    Some(T),
    None,
}

// Pattern matching
match value {
    Some(x) => println!("{}", x),
    None => println!("Nothing"),
}

// Error handling
let result = function()?;  // Propagate error

// Ownership
let s1 = String::from("hello");
let s2 = s1;  // s1 moved to s2

// Borrowing
let s = String::from("hello");
let len = calculate(&s);  // Borrow

// Iterators
let doubled: Vec<i32> = vec.iter()
    .map(|x| x * 2)
    .collect();

// Traits
trait Summary {
    fn summarize(&self) -> String;
}

// Generics
fn largest<T: PartialOrd>(list: &[T]) -> &T {
    // implementation
}

// Async
async fn fetch() -> Result<String, Error> {
    let data = api_call().await?;
    Ok(data)
}
```

---

<div align="center">

### Useful Cargo Commands 📋

```bash
# Project
cargo new myproject
cargo init

# Build & Run
cargo build
cargo build --release
cargo run
cargo check

# Testing
cargo test
cargo bench

# Dependencies
cargo add serde
cargo update

# Tools
cargo fmt
cargo clippy
cargo doc --open

# Publishing
cargo publish
```

</div>

---

<div align="center">

## 🚀 Next Steps

### _Continue Your Rust Journey_ 🌟

</div>

**Level Up:**

1. 🏗️ Build a real project (CLI tool, web API, game)
2. 📖 Read "Rust for Rustaceans" for advanced patterns
3. 🎯 Contribute to open-source Rust projects
4. 🔍 Learn about unsafe Rust and FFI
5. 🌐 Master async programming with Tokio
6. 🐳 Deploy Rust apps with Docker
7. ☸️ Explore WebAssembly with Rust
8. 🎮 Build a game with Bevy engine
9. 📝 Write technical blog posts about Rust
10. 🤝 Join the Rust community events

---

<div align="center">

### Project Ideas 💡

```
🌐 Web Application
   - REST API with Actix/Axum
   - GraphQL server
   - Real-time chat with WebSockets

🛠️ CLI Tool
   - File processor
   - System monitor
   - Build automation tool

🎮 Game Development
   - 2D game with Bevy
   - Roguelike with bracket-lib
   - Game engine component

🔌 System Programming
   - Custom shell
   - File system utility
   - Network tool

📊 Data Processing
   - Log analyzer
   - Data pipeline
   - ETL tool

🤖 Embedded Systems
   - IoT device firmware
   - Raspberry Pi project
   - Microcontroller programming
```

</div>

---

<div align="center">

## 🎯 Final Tips for Success

</div>

1. **Fight the borrow checker** - It's teaching you memory safety
2. **Read compiler errors carefully** - They're incredibly helpful
3. **Start with `cargo new`** - Don't fight the tooling
4. **Use `clippy` religiously** - It'll teach you idiomatic Rust
5. **Embrace immutability** - Use `mut` only when needed
6. **Think in ownership** - Who owns this data?
7. **Use `Result` and `Option`** - No null, no exceptions
8. **Leverage the type system** - Make invalid states unrepresentable
9. **Read The Book** - Multiple times
10. **Have patience** - Rust has a learning curve, but it's worth it

---

<div align="center">

## 🦀 Why Rust?

</div>

### The Triple Crown ⭐⭐⭐

1. **🛡️ Safety** - Memory safety without garbage collection
2. **⚡ Speed** - Zero-cost abstractions, C-level performance
3. **🔒 Concurrency** - Fearless concurrent programming

### Real-World Impact 🌍

- **Mozilla Firefox** - Parts written in Rust
- **Discord** - Switched to Rust for performance
- **Cloudflare** - Uses Rust for edge computing
- **Microsoft** - Uses Rust for Windows components
- **Amazon** - Uses Rust for AWS services
- **Google** - Uses Rust in Android

### The Rust Guarantee 💪

> **If it compiles, it probably works.** > **No null pointers. No data races. No segfaults.** > **Write it once, write it right.**

---

<div align="center">

**Built with 🦀 by MrDib, for Rustaceans**

_"Rust: Empowering everyone to build reliable and efficient software."_ - Rust Team

**Happy Coding, Rustacean!** 🚀

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

**Stay curious. Keep coding. Embrace the borrow checker!** ⚡

🦀 **#RustLang** 🦀 **#DevResourceVault** 🦀 **#MrDib** 🦀

### Remember

> _"Rust is not about writing less code. It's about writing better code."_

> _"The compiler is not your enemy. It's your pair programmer."_

> _"Every error message is a teaching moment."_

</div>

---

<div align="center">

**Now go forth and build blazing fast, memory-safe, concurrent systems!** 🔥

</div>
