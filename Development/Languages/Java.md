<div align="center">

# ☕ Java - Write Once, Run Anywhere

### _Enterprise-grade, object-oriented powerhouse_ 💪

![Java](https://img.shields.io/badge/Java-21+-orange?style=for-the-badge&logo=openjdk)
![Platform](https://img.shields.io/badge/Platform-Cross--Platform-green?style=for-the-badge)
![Type](https://img.shields.io/badge/Type-Strongly%20Typed-blue?style=for-the-badge)

</div>

---

## 📚 Table of Contents

- [🎯 Java Fundamentals](#-java-fundamentals)
- [📊 Data Types & Variables](#-data-types--variables)
- [🔄 Control Flow](#-control-flow)
- [🔧 Methods & Functions](#-methods--functions)
- [🏗️ Object-Oriented Programming](#️-object-oriented-programming)
- [📦 Collections Framework](#-collections-framework)
- [🌊 Streams & Lambda Expressions](#-streams--lambda-expressions)
- [🧬 Generics](#-generics)
- [📝 Annotations](#-annotations)
- [📂 File I/O](#-file-io)
- [⚠️ Exception Handling](#️-exception-handling)
- [🧵 Concurrency & Multithreading](#-concurrency--multithreading)
- [🧪 Testing](#-testing)
- [🎁 Modern Java Features](#-modern-java-features)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 🎯 Java Fundamentals

</div>

### Getting Started with Java 🚀

```bash
# ═══════════════════════════════════════════
# Installation & Setup
# ═══════════════════════════════════════════

# Check Java version
java -version
javac -version

# macOS (using Homebrew)
brew install openjdk@21

# Linux (Ubuntu/Debian)
sudo apt update
sudo apt install openjdk-21-jdk

# Windows
# Download from: https://adoptium.net/

# Set JAVA_HOME
export JAVA_HOME=$(/usr/libexec/java_home -v 21)  # macOS
export PATH=$JAVA_HOME/bin:$PATH

# ═══════════════════════════════════════════
# Compile & Run Java Programs
# ═══════════════════════════════════════════

# Compile
javac HelloWorld.java

# Run
java HelloWorld

# Compile and run in one step (Java 11+)
java HelloWorld.java

# Run with classpath
java -cp /path/to/classes HelloWorld

# Create JAR file
jar cvf myapp.jar *.class

# Run JAR file
java -jar myapp.jar
```

---

### Hello World & Basic Syntax 📝

```java
// ═══════════════════════════════════════════
// Hello World
// ═══════════════════════════════════════════

public class HelloWorld {
    // Main method - entry point of program
    public static void main(String[] args) {
        System.out.println("Hello from MrDib! 🚀");

        // Print without newline
        System.out.print("Hello ");
        System.out.print("World");

        // Formatted output
        System.out.printf("Name: %s, Age: %d%n", "MrDib", 25);

        // Command-line arguments
        if (args.length > 0) {
            System.out.println("First argument: " + args[0]);
        }
    }
}

// ═══════════════════════════════════════════
// Comments
// ═══════════════════════════════════════════

// Single-line comment

/*
 * Multi-line comment
 * More details here
 */

/**
 * JavaDoc comment (documentation)
 * @author MrDib
 * @version 1.0
 * @since 2024
 */

// ═══════════════════════════════════════════
// Package & Import
// ═══════════════════════════════════════════

package com.mrdib.project;

import java.util.ArrayList;
import java.util.List;
import java.util.*;              // Import all from package
import static java.lang.Math.*;  // Import static members

public class MyClass {
    // Class content
}
```

> **💡 Pro Tip:** Always use meaningful package names (reverse domain notation). Keep one public class per file matching the filename!

---

<div align="center">

## 📊 Data Types & Variables

</div>

### Primitive & Reference Types 🔢

```java
// ═══════════════════════════════════════════
// Primitive Data Types
// ═══════════════════════════════════════════

public class DataTypes {
    public static void main(String[] args) {
        // Integers
        byte byteVal = 127;              // -128 to 127 (8 bits)
        short shortVal = 32_767;         // -32,768 to 32,767 (16 bits)
        int intVal = 2_147_483_647;      // -2^31 to 2^31-1 (32 bits)
        long longVal = 9_223_372_036_854_775_807L;  // 64 bits

        // Floating point
        float floatVal = 3.14f;          // 32 bits (7 decimal digits)
        double doubleVal = 2.718281828;  // 64 bits (15 decimal digits)

        // Character (Unicode)
        char charVal = 'A';              // 16 bits
        char unicodeChar = '\u0041';     // 'A' in Unicode
        char emoji = '😀';

        // Boolean
        boolean isTrue = true;
        boolean isFalse = false;

        // Number formatting with underscores (Java 7+)
        int million = 1_000_000;
        long creditCard = 1234_5678_9012_3456L;
        int binary = 0b1010_0001_1000_0101;

        // Different number bases
        int decimal = 26;
        int binary = 0b11010;    // Binary
        int octal = 032;         // Octal
        int hex = 0x1A;          // Hexadecimal

        // Type casting
        int i = 100;
        long l = i;              // Implicit (widening)
        int i2 = (int) l;        // Explicit (narrowing)

        // Overflow behavior
        int max = Integer.MAX_VALUE;
        int overflow = max + 1;  // Wraps to Integer.MIN_VALUE
    }
}

// ═══════════════════════════════════════════
// Wrapper Classes (Boxing & Unboxing)
// ═══════════════════════════════════════════

public class WrapperClasses {
    public static void main(String[] args) {
        // Wrapper classes for primitives
        Byte b = Byte.valueOf((byte) 1);
        Short s = Short.valueOf((short) 2);
        Integer i = Integer.valueOf(3);
        Long l = Long.valueOf(4L);
        Float f = Float.valueOf(5.0f);
        Double d = Double.valueOf(6.0);
        Character c = Character.valueOf('A');
        Boolean bool = Boolean.valueOf(true);

        // Auto-boxing (automatic conversion)
        Integer autoBoxed = 42;              // int → Integer

        // Auto-unboxing
        int primitiveInt = autoBoxed;        // Integer → int

        // Useful constants
        System.out.println("Max int: " + Integer.MAX_VALUE);
        System.out.println("Min int: " + Integer.MIN_VALUE);
        System.out.println("Max double: " + Double.MAX_VALUE);
        System.out.println("Min double: " + Double.MIN_VALUE);
        System.out.println("NaN: " + Double.NaN);
        System.out.println("Infinity: " + Double.POSITIVE_INFINITY);

        // Parsing strings
        int parsed = Integer.parseInt("123");
        double parsedDouble = Double.parseDouble("3.14");
        boolean parsedBool = Boolean.parseBoolean("true");

        // Converting to string
        String str = Integer.toString(42);
        String binary = Integer.toBinaryString(42);
        String hex = Integer.toHexString(42);
    }
}

// ═══════════════════════════════════════════
// Variables & Constants
// ═══════════════════════════════════════════

public class Variables {
    // Instance variables (non-static fields)
    private String name;
    private int age;

    // Class variables (static fields)
    private static int count = 0;

    // Constants (final static)
    public static final double PI = 3.14159;
    public static final String VERSION = "1.0.0";

    public void method() {
        // Local variables
        int localVar = 10;

        // Type inference (Java 10+)
        var message = "Hello";    // String inferred
        var number = 42;          // int inferred
        var list = new ArrayList<String>();  // ArrayList<String> inferred

        // Final variables (cannot be reassigned)
        final int MAX_SIZE = 100;
        // MAX_SIZE = 200;  // ❌ Compilation error

        // Blank final (must be initialized before use)
        final int value;
        if (condition) {
            value = 10;
        } else {
            value = 20;
        }
    }
}

// ═══════════════════════════════════════════
// String Operations
// ═══════════════════════════════════════════

public class StringOperations {
    public static void main(String[] args) {
        String str = "Hello, World!";

        // Length
        int length = str.length();              // 13

        // Character access
        char firstChar = str.charAt(0);         // 'H'

        // Substring
        String sub = str.substring(0, 5);       // "Hello"
        String sub2 = str.substring(7);         // "World!"

        // Concatenation
        String greeting = "Hello" + ", " + "World!";
        String combined = str.concat(" Java!");

        // Case conversion
        String upper = str.toUpperCase();       // "HELLO, WORLD!"
        String lower = str.toLowerCase();       // "hello, world!"

        // Trimming
        String padded = "  Hello  ";
        String trimmed = padded.trim();         // "Hello"
        String stripped = padded.strip();       // "Hello" (Java 11+, Unicode-aware)
        String stripLeading = padded.stripLeading();
        String stripTrailing = padded.stripTrailing();

        // Checking
        boolean startsWith = str.startsWith("Hello");  // true
        boolean endsWith = str.endsWith("!");         // true
        boolean contains = str.contains("World");     // true
        boolean isEmpty = str.isEmpty();              // false
        boolean isBlank = "   ".isBlank();           // true (Java 11+)

        // Searching
        int index = str.indexOf("World");             // 7
        int lastIndex = str.lastIndexOf("o");         // 8

        // Replacing
        String replaced = str.replace("World", "Java");
        String replacedFirst = str.replaceFirst("o", "0");
        String replacedAll = str.replaceAll("[aeiou]", "*");

        // Splitting
        String[] parts = str.split(", ");             // ["Hello", "World!"]
        String[] chars = str.split("");               // Each character

        // Joining (Java 8+)
        String joined = String.join("-", "a", "b", "c");  // "a-b-c"

        // Formatting
        String formatted = String.format("Name: %s, Age: %d", "Alice", 25);

        // Comparison
        boolean equals = str.equals("Hello, World!");
        boolean equalsIgnoreCase = str.equalsIgnoreCase("hello, world!");
        int comparison = str.compareTo("Hello");

        // Repeat (Java 11+)
        String repeated = "Ha".repeat(3);  // "HaHaHa"

        // Lines (Java 11+)
        String multiLine = "Line1\nLine2\nLine3";
        multiLine.lines().forEach(System.out::println);

        // Text Blocks (Java 15+)
        String json = """
            {
                "name": "MrDib",
                "age": 25,
                "city": "Tokyo"
            }
            """;

        // StringBuilder (mutable, not thread-safe)
        StringBuilder sb = new StringBuilder("Hello");
        sb.append(", World!");
        sb.insert(5, " Java");
        sb.delete(0, 6);
        sb.reverse();
        String result = sb.toString();

        // StringBuffer (mutable, thread-safe)
        StringBuffer buffer = new StringBuffer("Hello");
        buffer.append(", World!");
    }
}

// ═══════════════════════════════════════════
// Arrays
// ═══════════════════════════════════════════

public class ArrayExamples {
    public static void main(String[] args) {
        // Array declaration & initialization
        int[] numbers = {1, 2, 3, 4, 5};
        String[] names = new String[3];

        // Initialize with values
        names[0] = "Alice";
        names[1] = "Bob";
        names[2] = "Charlie";

        // Access elements
        int first = numbers[0];
        int last = numbers[numbers.length - 1];

        // Length
        int length = numbers.length;

        // Multi-dimensional arrays
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };

        int[][] matrix2 = new int[3][3];

        // Jagged arrays
        int[][] jagged = new int[3][];
        jagged[0] = new int[2];
        jagged[1] = new int[4];
        jagged[2] = new int[3];

        // Iterate over array
        for (int i = 0; i < numbers.length; i++) {
            System.out.println(numbers[i]);
        }

        // Enhanced for loop
        for (int num : numbers) {
            System.out.println(num);
        }

        // Arrays utility class
        import java.util.Arrays;

        // Sort
        Arrays.sort(numbers);

        // Binary search (must be sorted first)
        int index = Arrays.binarySearch(numbers, 3);

        // Fill
        Arrays.fill(numbers, 0);

        // Copy
        int[] copy = Arrays.copyOf(numbers, numbers.length);
        int[] partial = Arrays.copyOfRange(numbers, 0, 3);

        // Equals
        boolean equal = Arrays.equals(numbers, copy);

        // Convert to string
        String str = Arrays.toString(numbers);

        // Convert to list
        List<Integer> list = Arrays.asList(1, 2, 3, 4, 5);

        // Stream operations
        int sum = Arrays.stream(numbers).sum();
        double average = Arrays.stream(numbers).average().orElse(0);
        int max = Arrays.stream(numbers).max().orElse(0);
    }
}
```

> **💡 Pro Tip:** Use `StringBuilder` for string concatenation in loops. Strings are immutable in Java - every concatenation creates a new object!

---

<div align="center">

## 🔄 Control Flow

</div>

### Conditionals & Loops 🔀

```java
// ═══════════════════════════════════════════
// If-Else Statements
// ═══════════════════════════════════════════

public class Conditionals {
    public static void main(String[] args) {
        int score = 85;

        // Basic if-else
        if (score >= 90) {
            System.out.println("Grade: A");
        } else if (score >= 80) {
            System.out.println("Grade: B");
        } else if (score >= 70) {
            System.out.println("Grade: C");
        } else if (score >= 60) {
            System.out.println("Grade: D");
        } else {
            System.out.println("Grade: F");
        }

        // Ternary operator
        String result = (score >= 60) ? "Pass" : "Fail";

        // Nested ternary (use sparingly!)
        String grade = score >= 90 ? "A" :
                      score >= 80 ? "B" :
                      score >= 70 ? "C" : "F";

        // Logical operators
        if (score >= 60 && score < 90) {
            System.out.println("Good performance");
        }

        if (score < 60 || score > 100) {
            System.out.println("Invalid or failing score");
        }

        if (!(score < 0)) {
            System.out.println("Valid score");
        }
    }
}

// ═══════════════════════════════════════════
// Switch Statements
// ═══════════════════════════════════════════

public class SwitchExamples {
    public static void main(String[] args) {
        // Traditional switch
        int day = 3;
        String dayName;

        switch (day) {
            case 1:
                dayName = "Monday";
                break;
            case 2:
                dayName = "Tuesday";
                break;
            case 3:
                dayName = "Wednesday";
                break;
            case 4:
                dayName = "Thursday";
                break;
            case 5:
                dayName = "Friday";
                break;
            case 6:
            case 7:
                dayName = "Weekend";
                break;
            default:
                dayName = "Invalid day";
        }

        // Switch expressions (Java 14+)
        String dayName2 = switch (day) {
            case 1 -> "Monday";
            case 2 -> "Tuesday";
            case 3 -> "Wednesday";
            case 4 -> "Thursday";
            case 5 -> "Friday";
            case 6, 7 -> "Weekend";
            default -> "Invalid day";
        };

        // Switch with yield (Java 14+)
        String message = switch (score / 10) {
            case 10, 9 -> "Excellent!";
            case 8 -> "Good!";
            case 7 -> "Average";
            case 6 -> "Below Average";
            default -> {
                String msg = "Needs Improvement";
                System.out.println("Score: " + score);
                yield msg;  // Return value from block
            }
        };

        // Switch on strings
        String command = "start";
        switch (command) {
            case "start" -> System.out.println("Starting...");
            case "stop" -> System.out.println("Stopping...");
            case "pause" -> System.out.println("Pausing...");
            default -> System.out.println("Unknown command");
        }

        // Pattern matching in switch (Java 17+ Preview, 21+ Standard)
        Object obj = "Hello";
        String result = switch (obj) {
            case Integer i -> "Integer: " + i;
            case String s -> "String: " + s.toUpperCase();
            case Double d -> "Double: " + d;
            case null -> "Null value";
            default -> "Unknown type";
        };
    }
}

// ═══════════════════════════════════════════
// Loops
// ═══════════════════════════════════════════

public class Loops {
    public static void main(String[] args) {
        // for loop
        for (int i = 0; i < 5; i++) {
            System.out.println("Iteration: " + i);
        }

        // Count backwards
        for (int i = 5; i > 0; i--) {
            System.out.println(i);
        }

        // Step by 2
        for (int i = 0; i < 10; i += 2) {
            System.out.println(i);
        }

        // Multiple variables
        for (int i = 0, j = 10; i < 5; i++, j--) {
            System.out.println(i + ", " + j);
        }

        // Enhanced for loop (for-each)
        int[] numbers = {1, 2, 3, 4, 5};
        for (int num : numbers) {
            System.out.println(num);
        }

        String[] names = {"Alice", "Bob", "Charlie"};
        for (String name : names) {
            System.out.println(name);
        }

        // while loop
        int count = 0;
        while (count < 5) {
            System.out.println("Count: " + count);
            count++;
        }

        // do-while loop (executes at least once)
        int i = 0;
        do {
            System.out.println("i: " + i);
            i++;
        } while (i < 5);

        // break statement
        for (int j = 0; j < 10; j++) {
            if (j == 5) {
                break;  // Exit loop
            }
            System.out.println(j);
        }

        // continue statement
        for (int k = 0; k < 10; k++) {
            if (k % 2 == 0) {
                continue;  // Skip even numbers
            }
            System.out.println(k);
        }

        // Labeled break (break out of nested loops)
        outer: for (int x = 0; x < 3; x++) {
            for (int y = 0; y < 3; y++) {
                if (x == 1 && y == 1) {
                    break outer;  // Break out of both loops
                }
                System.out.println(x + ", " + y);
            }
        }

        // Labeled continue
        outer: for (int x = 0; x < 3; x++) {
            for (int y = 0; y < 3; y++) {
                if (y == 1) {
                    continue outer;  // Continue outer loop
                }
                System.out.println(x + ", " + y);
            }
        }
    }
}
```

> **💡 Pro Tip:** Use enhanced for loop when you don't need the index. Use labeled break/continue only when absolutely necessary - it can make code harder to read!

---

<div align="center">

## 🔧 Methods & Functions

</div>

### Method Declarations & Overloading 📦

```java
// ═══════════════════════════════════════════
// Method Basics
// ═══════════════════════════════════════════

public class Methods {
    // Basic method
    public void greet() {
        System.out.println("Hello!");
    }

    // Method with parameters
    public void greet(String name) {
        System.out.println("Hello, " + name + "!");
    }

    // Method with return value
    public int add(int a, int b) {
        return a + b;
    }

    // Multiple return values (using array)
    public int[] getMinMax(int[] numbers) {
        int min = Arrays.stream(numbers).min().orElse(0);
        int max = Arrays.stream(numbers).max().orElse(0);
        return new int[]{min, max};
    }

    // Multiple return values (using custom class/record)
    public Result calculate(int a, int b) {
        return new Result(a + b, a - b, a * b);
    }

    record Result(int sum, int diff, int product) {}

    // Varargs (variable arguments)
    public int sum(int... numbers) {
        int total = 0;
        for (int num : numbers) {
            total += num;
        }
        return total;
    }

    // Usage
    public void demo() {
        greet();
        greet("MrDib");
        int result = add(5, 3);
        int total = sum(1, 2, 3, 4, 5);
    }
}

// ═══════════════════════════════════════════
// Method Overloading (Compile-time Polymorphism)
// ═══════════════════════════════════════════

public class Calculator {
    // Same method name, different parameters

    // Two integers
    public int add(int a, int b) {
        return a + b;
    }

    // Three integers
    public int add(int a, int b, int c) {
        return a + b + c;
    }

    // Two doubles
    public double add(double a, double b) {
        return a + b;
    }

    // Array
    public int add(int[] numbers) {
        return Arrays.stream(numbers).sum();
    }

    // Usage
    public void demo() {
        Calculator calc = new Calculator();
        System.out.println(calc.add(2, 3));           // 5
        System.out.println(calc.add(2, 3, 4));        // 9
        System.out.println(calc.add(2.5, 3.5));       // 6.0
        System.out.println(calc.add(new int[]{1, 2, 3})); // 6
    }
}

// ═══════════════════════════════════════════
// Access Modifiers
// ═══════════════════════════════════════════

public class AccessModifiers {
    // public - accessible everywhere
    public void publicMethod() {}

    // protected - accessible in same package and subclasses
    protected void protectedMethod() {}

    // default (package-private) - accessible in same package
    void defaultMethod() {}

    // private - accessible only within class
    private void privateMethod() {}
}

// ═══════════════════════════════════════════
// Static vs Instance Methods
// ═══════════════════════════════════════════

public class MathUtils {
    // Static method (belongs to class)
    public static int square(int n) {
        return n * n;
    }

    // Static method can't access instance variables
    public static void staticMethod() {
        // Can't use 'this' or instance variables
        square(5);  // Can call other static methods
    }

    // Instance method (belongs to object)
    private int value;

    public void setValue(int value) {
        this.value = value;  // Can use 'this'
    }

    public int getValue() {
        return value;
    }

    // Usage
    public static void main(String[] args) {
        // Static method - called on class
        int result = MathUtils.square(5);

        // Instance method - called on object
        MathUtils utils = new MathUtils();
        utils.setValue(10);
        int value = utils.getValue();
    }
}

// ═══════════════════════════════════════════
// Recursion
// ═══════════════════════════════════════════

public class RecursionExamples {
    // Factorial
    public static int factorial(int n) {
        if (n <= 1) return 1;
        return n * factorial(n - 1);
    }

    // Fibonacci
    public static int fibonacci(int n) {
        if (n <= 1) return n;
        return fibonacci(n - 1) + fibonacci(n - 2);
    }

    // Sum of digits
    public static int sumDigits(int n) {
        if (n == 0) return 0;
        return n % 10 + sumDigits(n / 10);
    }

    // Binary search (recursive)
    public static int binarySearch(int[] arr, int target, int left, int right) {
        if (left > right) return -1;

        int mid = left + (right - left) / 2;

        if (arr[mid] == target) return mid;
        if (arr[mid] > target) return binarySearch(arr, target, left, mid - 1);
        return binarySearch(arr, target, mid + 1, right);
    }
}
```

> **💡 Pro Tip:** Use recursion for naturally recursive problems (trees, graphs), but watch out for stack overflow! For simple iterations, loops are often more efficient.

---

<div align="center">

## 🏗️ Object-Oriented Programming

</div>

### Classes, Objects & Inheritance 🎯

```java
// ═══════════════════════════════════════════
// Classes & Objects
// ═══════════════════════════════════════════

public class Person {
    // Instance variables (fields)
    private String name;
    private int age;
    private String email;

    // Static variable (shared across all instances)
    private static int personCount = 0;

    // Constant
    public static final String SPECIES = "Homo Sapiens";

    // Default constructor
    public Person() {
        this("Unknown", 0, "unknown@email.com");
    }

    // Parameterized constructor
    public Person(String name, int age, String email) {
        this.name = name;
        this.age = age;
        this.email = email;
        personCount++;
    }

    // Getters
    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }

    public String getEmail() {
        return email;
    }

    // Setters
    public void setName(String name) {
        this.name = name;
    }

    public void setAge(int age) {
        if (age >= 0 && age <= 150) {
            this.age = age;
        } else {
            throw new IllegalArgumentException("Invalid age");
        }
    }

    public void setEmail(String email) {
        if (email.contains("@")) {
            this.email = email;
        } else {
            throw new IllegalArgumentException("Invalid email");
        }
    }

    // Instance method
    public void displayInfo() {
        System.out.printf("Name: %s, Age: %d, Email: %s%n", name, age, email);
    }

    // Static method
    public static int getPersonCount() {
        return personCount;
    }

    // toString override
    @Override
    public String toString() {
        return String.format("Person{name='%s', age=%d, email='%s'}",
                           name, age, email);
    }

    // equals override
    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;
        if (obj == null || getClass() != obj.getClass()) return false;
        Person person = (Person) obj;
        return age == person.age &&
               name.equals(person.name) &&
               email.equals(person.email);
    }

    // hashCode override
    @Override
    public int hashCode() {
        return Objects.hash(name, age, email);
    }
}

// ═══════════════════════════════════════════
// Inheritance
// ═══════════════════════════════════════════

// Base class (Parent/Superclass)
public class Animal {
    protected String name;
    protected int age;

    public Animal(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public void eat() {
        System.out.println(name + " is eating");
    }

    public void sleep() {
        System.out.println(name + " is sleeping");
    }

    public void makeSound() {
        System.out.println(name + " makes a sound");
    }
}

// Derived class (Child/Subclass)
public class Dog extends Animal {
    private String breed;

    public Dog(String name, int age, String breed) {
        super(name, age);  // Call parent constructor
        this.breed = breed;
    }

    // Method overriding
    @Override
    public void eat() {
        System.out.println(name + " is eating dog food");
    }

    @Override
    public void makeSound() {
        System.out.println(name + " says: Woof!");
    }

    // Additional method
    public void bark() {
        System.out.println(name + " is barking!");
    }

    // Call parent method
    public void parentEat() {
        super.eat();  // Call Animal's eat method
    }
}

public class Cat extends Animal {
    private boolean isIndoor;

    public Cat(String name, int age, boolean isIndoor) {
        super(name, age);
        this.isIndoor = isIndoor;
    }

    @Override
    public void makeSound() {
        System.out.println(name + " says: Meow!");
    }

    public void scratch() {
        System.out.println(name + " is scratching");
    }
}

// ═══════════════════════════════════════════
// Polymorphism
// ═══════════════════════════════════════════

public class PolymorphismDemo {
    public static void main(String[] args) {
        // Runtime polymorphism (Method Overriding)
        Animal animal1 = new Dog("Buddy", 3, "Golden Retriever");
        Animal animal2 = new Cat("Whiskers", 2, true);
        Animal animal3 = new Animal("Generic", 5);

        // Polymorphic behavior
        animal1.makeSound();  // "Buddy says: Woof!"
        animal2.makeSound();  // "Whiskers says: Meow!"
        animal3.makeSound();  // "Generic makes a sound"

        // Array of polymorphic objects
        Animal[] animals = {
            new Dog("Rex", 4, "German Shepherd"),
            new Cat("Felix", 3, true),
            new Dog("Max", 2, "Bulldog")
        };

        for (Animal animal : animals) {
            animal.makeSound();
        }

        // instanceof check
        if (animal1 instanceof Dog) {
            Dog dog = (Dog) animal1;
            dog.bark();
        }

        // Pattern matching instanceof (Java 16+)
        if (animal1 instanceof Dog dog) {
            dog.bark();  // No explicit cast needed
        }
    }
}

// ═══════════════════════════════════════════
// Abstract Classes
// ═══════════════════════════════════════════

public abstract class Shape {
    protected String color;

    public Shape(String color) {
        this.color = color;
    }

    // Abstract method (must be implemented by subclasses)
    public abstract double calculateArea();
    public abstract double calculatePerimeter();

    // Concrete method
    public void displayColor() {
        System.out.println("Color: " + color);
    }

    // Can have constructor
    // Can have instance variables
    // Can have concrete methods
}

public class Circle extends Shape {
    private double radius;

    public Circle(String color, double radius) {
        super(color);
        this.radius = radius;
    }

    @Override
    public double calculateArea() {
        return Math.PI * radius * radius;
    }

    @Override
    public double calculatePerimeter() {
        return 2 * Math.PI * radius;
    }
}

public class Rectangle extends Shape {
    private double width;
    private double height;

    public Rectangle(String color, double width, double height) {
        super(color);
        this.width = width;
        this.height = height;
    }

    @Override
    public double calculateArea() {
        return width * height;
    }

    @Override
    public double calculatePerimeter() {
        return 2 * (width + height);
    }
}

// ═══════════════════════════════════════════
// Interfaces
// ═══════════════════════════════════════════

public interface Drawable {
    // Abstract method (implicitly public abstract)
    void draw();

    // Default method (Java 8+)
    default void display() {
        System.out.println("Displaying...");
    }

    // Static method (Java 8+)
    static void info() {
        System.out.println("This is a Drawable interface");
    }

    // Private method (Java 9+)
    private void helper() {
        System.out.println("Helper method");
    }

    // Constants (implicitly public static final)
    String TYPE = "Drawable";
}

public interface Resizable {
    void resize(double factor);

    default void doubleSize() {
        resize(2.0);
    }
}

// Multiple interface implementation
public class Image implements Drawable, Resizable {
    private int width;
    private int height;

    public Image(int width, int height) {
        this.width = width;
        this.height = height;
    }

    @Override
    public void draw() {
        System.out.println("Drawing image " + width + "x" + height);
    }

    @Override
    public void resize(double factor) {
        width *= factor;
        height *= factor;
        System.out.println("Resized to " + width + "x" + height);
    }
}

// Functional Interface (single abstract method)
@FunctionalInterface
public interface Calculator {
    int calculate(int a, int b);

    // Can have default and static methods
    default void log() {
        System.out.println("Calculating...");
    }

    static Calculator add() {
        return (a, b) -> a + b;
    }
}

// ═══════════════════════════════════════════
// Enums
// ═══════════════════════════════════════════

// Simple enum
public enum Day {
    MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY
}

// Enum with properties and methods
public enum Planet {
    MERCURY(3.303e+23, 2.4397e6),
    VENUS(4.869e+24, 6.0518e6),
    EARTH(5.976e+24, 6.37814e6),
    MARS(6.421e+23, 3.3972e6),
    JUPITER(1.9e+27, 7.1492e7),
    SATURN(5.688e+26, 6.0268e7),
    URANUS(8.686e+25, 2.5559e7),
    NEPTUNE(1.024e+26, 2.4746e7);

    private final double mass;   // in kilograms
    private final double radius; // in meters

    Planet(double mass, double radius) {
        this.mass = mass;
        this.radius = radius;
    }

    public double getMass() {
        return mass;
    }

    public double getRadius() {
        return radius;
    }

    public double surfaceGravity() {
        final double G = 6.67300E-11;
        return G * mass / (radius * radius);
    }

    public double surfaceWeight(double otherMass) {
        return otherMass * surfaceGravity();
    }
}

// Usage
public class EnumDemo {
    public static void main(String[] args) {
        Day today = Day.MONDAY;

        // Switch with enum
        switch (today) {
            case MONDAY -> System.out.println("Start of week");
            case FRIDAY -> System.out.println("TGIF!");
            case SATURDAY, SUNDAY -> System.out.println("Weekend!");
            default -> System.out.println("Midweek");
        }

        // Iterate over enum values
        for (Day day : Day.values()) {
            System.out.println(day);
        }

        // Get enum by name
        Day day = Day.valueOf("MONDAY");

        // Ordinal (position)
        int position = Day.MONDAY.ordinal();  // 0

        // Planet calculations
        double earthWeight = 75.0;
        double mass = earthWeight / Planet.EARTH.surfaceGravity();

        for (Planet planet : Planet.values()) {
            double weight = planet.surfaceWeight(mass);
            System.out.printf("Weight on %s: %.2f kg%n", planet, weight);
        }
    }
}

// ═══════════════════════════════════════════
// Records (Java 14+ Preview, 16+ Standard)
// ═══════════════════════════════════════════

// Immutable data carrier
public record User(String name, int age, String email) {
    // Compact constructor (validation)
    public User {
        if (age < 0) {
            throw new IllegalArgumentException("Age cannot be negative");
        }
        if (!email.contains("@")) {
            throw new IllegalArgumentException("Invalid email");
        }
    }

    // Canonical constructor (explicit)
    public User(String name, int age, String email) {
        this.name = name;
        this.age = age;
        this.email = email;
    }

    // Additional constructor
    public User(String name) {
        this(name, 0, "unknown@email.com");
    }

    // Additional methods
    public boolean isAdult() {
        return age >= 18;
    }

    public String getDisplayName() {
        return name + " <" + email + ">";
    }
}

// Usage
public class RecordDemo {
    public static void main(String[] args) {
        User user = new User("Alice", 25, "alice@email.com");

        // Automatic getters (no "get" prefix)
        System.out.println(user.name());   // Alice
        System.out.println(user.age());    // 25
        System.out.println(user.email());  // alice@email.com

        // Automatic toString
        System.out.println(user);
        // User[name=Alice, age=25, email=alice@email.com]

        // Automatic equals and hashCode
        User user2 = new User("Alice", 25, "alice@email.com");
        System.out.println(user.equals(user2));  // true

        // Records are immutable (no setters)
        // user.name = "Bob";  // ❌ Compilation error

        // Create modified copy with record pattern
        User updatedUser = new User("Bob", user.age(), user.email());
    }
}

// ═══════════════════════════════════════════
// Sealed Classes (Java 17+)
// ═══════════════════════════════════════════

// Restrict which classes can extend/implement
public sealed class Shape
    permits Circle, Rectangle, Triangle {
    // Only Circle, Rectangle, Triangle can extend Shape
}

public final class Circle extends Shape {
    // Must be final, sealed, or non-sealed
}

public final class Rectangle extends Shape {
}

public non-sealed class Triangle extends Shape {
    // non-sealed allows further extension
}
```

> **💡 Pro Tip:** Use composition over inheritance when possible. Prefer interfaces for contracts, abstract classes for shared code. Records are perfect for DTOs and value objects!

---

<div align="center">

## 📦 Collections Framework

</div>

### Lists, Sets, Maps & More 🗂️

```java
import java.util.*;

// ═══════════════════════════════════════════
// List Interface (Ordered, allows duplicates)
// ═══════════════════════════════════════════

public class ListExamples {
    public static void main(String[] args) {
        // ArrayList (dynamic array, fast random access)
        List<String> arrayList = new ArrayList<>();
        arrayList.add("Apple");
        arrayList.add("Banana");
        arrayList.add("Cherry");
        arrayList.add("Apple");  // Duplicates allowed

        // Access elements
        String first = arrayList.get(0);
        arrayList.set(1, "Blueberry");  // Update

        // Remove elements
        arrayList.remove(0);              // By index
        arrayList.remove("Cherry");       // By value

        // Check
        boolean contains = arrayList.contains("Apple");
        int size = arrayList.size();
        boolean isEmpty = arrayList.isEmpty();
        int index = arrayList.indexOf("Apple");

        // Iterate
        for (String fruit : arrayList) {
            System.out.println(fruit);
        }

        // Using iterator
        Iterator<String> iterator = arrayList.iterator();
        while (iterator.hasNext()) {
            String fruit = iterator.next();
            System.out.println(fruit);
        }

        // LinkedList (doubly-linked list, fast insertion/deletion)
        List<String> linkedList = new LinkedList<>();
        linkedList.add("First");
        linkedList.add("Second");
        linkedList.add("Third");

        // LinkedList specific operations
        LinkedList<String> ll = new LinkedList<>();
        ll.addFirst("Start");
        ll.addLast("End");
        String first = ll.getFirst();
        String last = ll.getLast();
        ll.removeFirst();
        ll.removeLast();

        // List operations
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
        Collections.reverse(numbers);
        Collections.sort(numbers);
        Collections.shuffle(numbers);

        // Sublist
        List<Integer> subList = numbers.subList(0, 3);

        // Copy
        List<Integer> copy = new ArrayList<>(numbers);

        // Clear
        numbers.clear();
    }
}

// ═══════════════════════════════════════════
// Set Interface (No duplicates)
// ═══════════════════════════════════════════

public class SetExamples {
    public static void main(String[] args) {
        // HashSet (unordered, fastest)
        Set<String> hashSet = new HashSet<>();
        hashSet.add("Apple");
        hashSet.add("Banana");
        hashSet.add("Cherry");
        hashSet.add("Apple");  // Duplicate ignored

        System.out.println(hashSet);  // Order not guaranteed

        // Check
        boolean contains = hashSet.contains("Apple");
        int size = hashSet.size();

        // Remove
        hashSet.remove("Banana");

        // LinkedHashSet (maintains insertion order)
        Set<String> linkedHashSet = new LinkedHashSet<>();
        linkedHashSet.add("Apple");
        linkedHashSet.add("Banana");
        linkedHashSet.add("Cherry");

        System.out.println(linkedHashSet);  // [Apple, Banana, Cherry]

        // TreeSet (sorted, natural ordering)
        Set<Integer> treeSet = new TreeSet<>();
        treeSet.add(5);
        treeSet.add(2);
        treeSet.add(8);
        treeSet.add(1);

        System.out.println(treeSet);  // [1, 2, 5, 8]

        // TreeSet with custom comparator
        Set<String> customTreeSet = new TreeSet<>(Comparator.reverseOrder());
        customTreeSet.add("Apple");
        customTreeSet.add("Banana");
        customTreeSet.add("Cherry");

        System.out.println(customTreeSet);  // [Cherry, Banana, Apple]

        // Set operations
        Set<Integer> set1 = new HashSet<>(Arrays.asList(1, 2, 3, 4));
        Set<Integer> set2 = new HashSet<>(Arrays.asList(3, 4, 5, 6));

        // Union
        Set<Integer> union = new HashSet<>(set1);
        union.addAll(set2);  // [1, 2, 3, 4, 5, 6]

        // Intersection
        Set<Integer> intersection = new HashSet<>(set1);
        intersection.retainAll(set2);  // [3, 4]

        // Difference
        Set<Integer> difference = new HashSet<>(set1);
        difference.removeAll(set2);  // [1, 2]

        // Symmetric difference
        Set<Integer> symmetricDiff = new HashSet<>(union);
        symmetricDiff.removeAll(intersection);  // [1, 2, 5, 6]
    }
}

// ═══════════════════════════════════════════
// Map Interface (Key-Value pairs)
// ═══════════════════════════════════════════

public class MapExamples {
    public static void main(String[] args) {
        // HashMap (unordered, fastest)
        Map<String, Integer> hashMap = new HashMap<>();
        hashMap.put("Alice", 25);
        hashMap.put("Bob", 30);
        hashMap.put("Charlie", 35);
        hashMap.put("Alice", 26);  // Overwrites previous value

        // Access
        int age = hashMap.get("Alice");
        int defaultValue = hashMap.getOrDefault("David", 0);

        // Check
        boolean hasKey = hashMap.containsKey("Bob");
        boolean hasValue = hashMap.containsValue(30);

        // Remove
        hashMap.remove("Charlie");
        hashMap.remove("Bob", 30);  // Remove only if value matches

        // Iterate
        for (Map.Entry<String, Integer> entry : hashMap.entrySet()) {
            System.out.println(entry.getKey() + ": " + entry.getValue());
        }

        // Keys and values
        Set<String> keys = hashMap.keySet();
        Collection<Integer> values = hashMap.values();

        // LinkedHashMap (maintains insertion order)
        Map<String, Integer> linkedHashMap = new LinkedHashMap<>();
        linkedHashMap.put("First", 1);
        linkedHashMap.put("Second", 2);
        linkedHashMap.put("Third", 3);

        // TreeMap (sorted by keys)
        Map<String, Integer> treeMap = new TreeMap<>();
        treeMap.put("Charlie", 35);
        treeMap.put("Alice", 25);
        treeMap.put("Bob", 30);

        System.out.println(treeMap);  // {Alice=25, Bob=30, Charlie=35}

        // Compute operations (Java 8+)
        Map<String, Integer> scores = new HashMap<>();
        scores.put("Alice", 100);

        // Compute if absent
        scores.computeIfAbsent("Bob", k -> 0);

        // Compute if present
        scores.computeIfPresent("Alice", (k, v) -> v + 10);

        // Compute
        scores.compute("Charlie", (k, v) -> v == null ? 1 : v + 1);

        // Merge
        scores.merge("Alice", 5, Integer::sum);  // Add 5 to existing value

        // Replace
        scores.replace("Bob", 50);
        scores.replace("Alice", 110, 115);  // Only if current value is 110

        // putIfAbsent
        scores.putIfAbsent("David", 80);
    }
}

// ═══════════════════════════════════════════
// Queue Interface (FIFO)
// ═══════════════════════════════════════════

public class QueueExamples {
    public static void main(String[] args) {
        // LinkedList as Queue
        Queue<String> queue = new LinkedList<>();
        queue.offer("First");   // Add (returns false if fails)
        queue.offer("Second");
        queue.offer("Third");

        String head = queue.peek();   // View head (null if empty)
        String removed = queue.poll(); // Remove head (null if empty)

        // PriorityQueue (natural ordering or comparator)
        Queue<Integer> priorityQueue = new PriorityQueue<>();
        priorityQueue.offer(5);
        priorityQueue.offer(2);
        priorityQueue.offer(8);
        priorityQueue.offer(1);

        while (!priorityQueue.isEmpty()) {
            System.out.println(priorityQueue.poll());  // 1, 2, 5, 8
        }

        // Custom comparator
        Queue<String> customQueue = new PriorityQueue<>(Comparator.reverseOrder());
        customQueue.offer("Apple");
        customQueue.offer("Banana");
        customQueue.offer("Cherry");

        // Deque (Double-ended queue)
        Deque<String> deque = new ArrayDeque<>();
        deque.offerFirst("First");
        deque.offerLast("Last");
        deque.pollFirst();
        deque.pollLast();

        // Stack operations (use Deque instead of Stack class)
        Deque<Integer> stack = new ArrayDeque<>();
        stack.push(1);
        stack.push(2);
        stack.push(3);
        int top = stack.pop();  // 3
        int peek = stack.peek(); // 2
    }
}

// ═══════════════════════════════════════════
// Collections Utility Class
// ═══════════════════════════════════════════

public class CollectionsUtility {
    public static void main(String[] args) {
        List<Integer> numbers = new ArrayList<>(Arrays.asList(5, 2, 8, 1, 9));

        // Sort
        Collections.sort(numbers);  // [1, 2, 5, 8, 9]
        Collections.sort(numbers, Comparator.reverseOrder());  // [9, 8, 5, 2, 1]

        // Reverse
        Collections.reverse(numbers);

        // Shuffle
        Collections.shuffle(numbers);

        // Binary search (must be sorted)
        Collections.sort(numbers);
        int index = Collections.binarySearch(numbers, 5);

        // Min and Max
        int min = Collections.min(numbers);
        int max = Collections.max(numbers);

        // Frequency
        int count = Collections.frequency(numbers, 5);

        // Fill
        Collections.fill(numbers, 0);

        // Copy
        List<Integer> dest = new ArrayList<>(numbers.size());
        for (int i = 0; i < numbers.size(); i++) dest.add(0);
        Collections.copy(dest, numbers);

        // Rotate
        Collections.rotate(numbers, 2);

        // Swap
        Collections.swap(numbers, 0, 1);

        // Replace all
        Collections.replaceAll(numbers, 5, 10);

        // Unmodifiable collections
        List<Integer> unmodifiable = Collections.unmodifiableList(numbers);

        // Synchronized collections
        List<Integer> synchronized = Collections.synchronizedList(numbers);

        // Singleton collections
        Set<String> singleton = Collections.singleton("only");

        // Empty collections
        List<String> emptyList = Collections.emptyList();
        Set<String> emptySet = Collections.emptySet();
        Map<String, Integer> emptyMap = Collections.emptyMap();

        // Checked collections (type-safe at runtime)
        List<String> checked = Collections.checkedList(
            new ArrayList<>(), String.class
        );
    }
}
```

> **💡 Pro Tip:** Use **ArrayList** for most cases, **LinkedList** for frequent insertions/deletions, **HashSet** for unique values, **HashMap** for key-value pairs. Always specify generic types!

---

<div align="center">

## 🌊 Streams & Lambda Expressions

</div>

### Functional Programming in Java 💫

```java
import java.util.*;
import java.util.stream.*;
import java.util.function.*;

// ═══════════════════════════════════════════
// Lambda Expressions (Java 8+)
// ═══════════════════════════════════════════

public class LambdaExamples {
    public static void main(String[] args) {
        // Traditional way (anonymous class)
        Runnable runnable1 = new Runnable() {
            @Override
            public void run() {
                System.out.println("Running...");
            }
        };

        // Lambda way
        Runnable runnable2 = () -> System.out.println("Running...");

        // Comparator
        List<String> names = Arrays.asList("Charlie", "Alice", "Bob");

        // Traditional
        Collections.sort(names, new Comparator<String>() {
            @Override
            public int compare(String s1, String s2) {
                return s1.compareTo(s2);
            }
        });

        // Lambda
        Collections.sort(names, (s1, s2) -> s1.compareTo(s2));

        // Method reference
        Collections.sort(names, String::compareTo);
        names.sort(Comparator.naturalOrder());

        // Lambda with multiple statements
        Runnable complex = () -> {
            System.out.println("Line 1");
            System.out.println("Line 2");
            System.out.println("Line 3");
        };

        // Lambda with parameters
        BinaryOperator<Integer> add = (a, b) -> a + b;
        BinaryOperator<Integer> multiply = (a, b) -> a * b;

        System.out.println(add.apply(5, 3));       // 8
        System.out.println(multiply.apply(5, 3));  // 15
    }
}

// ═══════════════════════════════════════════
// Built-in Functional Interfaces
// ═══════════════════════════════════════════

public class FunctionalInterfaceExamples {
    public static void main(String[] args) {
        // Predicate<T> - takes T, returns boolean
        Predicate<Integer> isEven = n -> n % 2 == 0;
        Predicate<String> isEmpty = String::isEmpty;
        System.out.println(isEven.test(4));  // true

        // Function<T, R> - takes T, returns R
        Function<String, Integer> stringLength = String::length;
        Function<Integer, String> toString = String::valueOf;
        System.out.println(stringLength.apply("Hello"));  // 5

        // Consumer<T> - takes T, returns void
        Consumer<String> printer = System.out::println;
        Consumer<String> upperPrinter = s -> System.out.println(s.toUpperCase());
        printer.accept("Hello, World!");

        // Supplier<T> - takes nothing, returns T
        Supplier<Double> randomSupplier = Math::random;
        Supplier<String> stringSupplier = () -> "Hello";
        System.out.println(randomSupplier.get());

        // BiFunction<T, U, R> - takes T and U, returns R
        BiFunction<Integer, Integer, Integer> adder = (a, b) -> a + b;
        BiFunction<String, String, String> concat = (a, b) -> a + b;
        System.out.println(adder.apply(5, 3));  // 8

        // UnaryOperator<T> - takes T, returns T
        UnaryOperator<Integer> square = n -> n * n;
        UnaryOperator<String> toUpper = String::toUpperCase;
        System.out.println(square.apply(5));  // 25

        // BinaryOperator<T> - takes two T, returns T
        BinaryOperator<Integer> multiplier = (a, b) -> a * b;
        BinaryOperator<String> combiner = (a, b) -> a + " " + b;
        System.out.println(multiplier.apply(5, 3));  // 15

        // BiPredicate<T, U> - takes T and U, returns boolean
        BiPredicate<String, Integer> lengthCheck = (s, len) -> s.length() == len;
        System.out.println(lengthCheck.test("Hello", 5));  // true

        // BiConsumer<T, U> - takes T and U, returns void
        BiConsumer<String, Integer> printer2 = (s, n) ->
            System.out.println(s + ": " + n);
        printer2.accept("Count", 42);
    }
}

// ═══════════════════════════════════════════
// Stream API - Creation & Operations
// ═══════════════════════════════════════════

public class StreamBasics {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

        // Filter - select elements
        List<Integer> evens = numbers.stream()
            .filter(n -> n % 2 == 0)
            .collect(Collectors.toList());
        // [2, 4, 6, 8, 10]

        // Map - transform elements
        List<Integer> squared = numbers.stream()
            .map(n -> n * n)
            .collect(Collectors.toList());
        // [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

        // Map with method reference
        List<String> strings = Arrays.asList("a", "b", "c");
        List<String> upper = strings.stream()
            .map(String::toUpperCase)
            .collect(Collectors.toList());

        // FlatMap - flatten nested structures
        List<List<Integer>> nested = Arrays.asList(
            Arrays.asList(1, 2, 3),
            Arrays.asList(4, 5, 6),
            Arrays.asList(7, 8, 9)
        );

        List<Integer> flattened = nested.stream()
            .flatMap(List::stream)
            .collect(Collectors.toList());
        // [1, 2, 3, 4, 5, 6, 7, 8, 9]

        // Distinct - remove duplicates
        List<Integer> duplicates = Arrays.asList(1, 2, 2, 3, 3, 3, 4, 5);
        List<Integer> unique = duplicates.stream()
            .distinct()
            .collect(Collectors.toList());
        // [1, 2, 3, 4, 5]

        // Sorted
        List<String> names = Arrays.asList("Charlie", "Alice", "Bob");
        List<String> sorted = names.stream()
            .sorted()
            .collect(Collectors.toList());
        // [Alice, Bob, Charlie]

        // Sorted with comparator
        List<String> reversed = names.stream()
            .sorted(Comparator.reverseOrder())
            .collect(Collectors.toList());

        // Limit & Skip
        List<Integer> limited = numbers.stream()
            .limit(5)
            .collect(Collectors.toList());
        // [1, 2, 3, 4, 5]

        List<Integer> skipped = numbers.stream()
            .skip(5)
            .collect(Collectors.toList());
        // [6, 7, 8, 9, 10]

        // Peek - perform action without modifying stream
        numbers.stream()
            .filter(n -> n % 2 == 0)
            .peek(n -> System.out.println("Filtered: " + n))
            .map(n -> n * n)
            .peek(n -> System.out.println("Mapped: " + n))
            .collect(Collectors.toList());
    }
}

// ═══════════════════════════════════════════
// Stream Terminal Operations
// ═══════════════════════════════════════════

public class StreamTerminalOps {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

        // forEach - perform action on each element
        numbers.stream()
            .filter(n -> n % 2 == 0)
            .forEach(System.out::println);

        // count - count elements
        long count = numbers.stream()
            .filter(n -> n > 5)
            .count();
        // 5

        // collect - gather elements
        List<Integer> list = numbers.stream()
            .filter(n -> n % 2 == 0)
            .collect(Collectors.toList());

        Set<Integer> set = numbers.stream()
            .collect(Collectors.toSet());

        // reduce - reduce to single value
        int sum = numbers.stream()
            .reduce(0, (a, b) -> a + b);
        // 55

        // reduce with method reference
        int sum2 = numbers.stream()
            .reduce(0, Integer::sum);

        Optional<Integer> sum3 = numbers.stream()
            .reduce(Integer::sum);

        int product = numbers.stream()
            .reduce(1, (a, b) -> a * b);

        // min & max
        Optional<Integer> min = numbers.stream()
            .min(Integer::compareTo);

        Optional<Integer> max = numbers.stream()
            .max(Integer::compareTo);

        // anyMatch, allMatch, noneMatch
        boolean hasEven = numbers.stream()
            .anyMatch(n -> n % 2 == 0);   // true

        boolean allPositive = numbers.stream()
            .allMatch(n -> n > 0);        // true

        boolean noNegative = numbers.stream()
            .noneMatch(n -> n < 0);       // true

        // findFirst, findAny
        Optional<Integer> first = numbers.stream()
            .filter(n -> n > 5)
            .findFirst();
        // Optional[6]

        Optional<Integer> any = numbers.stream()
            .filter(n -> n > 5)
            .findAny();

        // toArray
        Integer[] array = numbers.stream()
            .toArray(Integer[]::new);
    }
}

// ═══════════════════════════════════════════
// Collectors - Advanced Collection Operations
// ═══════════════════════════════════════════

public class CollectorExamples {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("Alice", "Bob", "Charlie", "David");
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

        // toList, toSet
        List<String> list = names.stream()
            .collect(Collectors.toList());

        Set<String> set = names.stream()
            .collect(Collectors.toSet());

        // toMap
        Map<String, Integer> map = names.stream()
            .collect(Collectors.toMap(
                name -> name,
                String::length
            ));
        // {Alice=5, Bob=3, Charlie=7, David=5}

        // joining - concatenate strings
        String joined = names.stream()
            .collect(Collectors.joining());
        // "AliceBobCharlieDavid"

        String withDelimiter = names.stream()
            .collect(Collectors.joining(", "));
        // "Alice, Bob, Charlie, David"

        String withPrefixSuffix = names.stream()
            .collect(Collectors.joining(", ", "[", "]"));
        // "[Alice, Bob, Charlie, David]"

        // groupingBy - group elements
        Map<Integer, List<String>> byLength = names.stream()
            .collect(Collectors.groupingBy(String::length));
        // {3=[Bob], 5=[Alice, David], 7=[Charlie]}

        Map<Boolean, List<Integer>> evenOdd = numbers.stream()
            .collect(Collectors.groupingBy(n -> n % 2 == 0));
        // {false=[1,3,5,7,9], true=[2,4,6,8,10]}

        // partitioningBy - split into two groups
        Map<Boolean, List<Integer>> partitioned = numbers.stream()
            .collect(Collectors.partitioningBy(n -> n > 5));
        // {false=[1,2,3,4,5], true=[6,7,8,9,10]}

        // counting
        long count = numbers.stream()
            .collect(Collectors.counting());

        // summingInt, summingLong, summingDouble
        int total = numbers.stream()
            .collect(Collectors.summingInt(Integer::intValue));

        // averagingInt, averagingLong, averagingDouble
        double average = numbers.stream()
            .collect(Collectors.averagingInt(Integer::intValue));

        // summarizingInt - get statistics
        IntSummaryStatistics stats = numbers.stream()
            .collect(Collectors.summarizingInt(Integer::intValue));

        System.out.println("Count: " + stats.getCount());
        System.out.println("Sum: " + stats.getSum());
        System.out.println("Min: " + stats.getMin());
        System.out.println("Max: " + stats.getMax());
        System.out.println("Average: " + stats.getAverage());

        // maxBy, minBy
        Optional<String> longest = names.stream()
            .collect(Collectors.maxBy(Comparator.comparing(String::length)));

        // mapping - transform then collect
        List<Integer> lengths = names.stream()
            .collect(Collectors.mapping(
                String::length,
                Collectors.toList()
            ));

        // filtering - filter then collect
        List<String> longNames = names.stream()
            .collect(Collectors.filtering(
                s -> s.length() > 4,
                Collectors.toList()
            ));
    }
}

// ═══════════════════════════════════════════
// Stream Creation Methods
// ═══════════════════════════════════════════

public class StreamCreation {
    public static void main(String[] args) {
        // From collection
        List<Integer> list = Arrays.asList(1, 2, 3, 4, 5);
        Stream<Integer> stream1 = list.stream();

        // From array
        String[] array = {"a", "b", "c"};
        Stream<String> stream2 = Arrays.stream(array);

        // Of elements
        Stream<String> stream3 = Stream.of("a", "b", "c");

        // Empty stream
        Stream<String> empty = Stream.empty();

        // Generate - infinite stream
        Stream<Double> randoms = Stream.generate(Math::random);
        randoms.limit(5).forEach(System.out::println);

        // Iterate - infinite stream
        Stream<Integer> numbers = Stream.iterate(0, n -> n + 2);
        numbers.limit(10).forEach(System.out::println);
        // 0, 2, 4, 6, 8, 10, 12, 14, 16, 18

        // Iterate with predicate (Java 9+)
        Stream<Integer> numbers2 = Stream.iterate(0, n -> n < 20, n -> n + 2);
        numbers2.forEach(System.out::println);

        // IntStream, LongStream, DoubleStream
        IntStream intStream = IntStream.range(1, 10);  // 1 to 9
        IntStream intStream2 = IntStream.rangeClosed(1, 10);  // 1 to 10

        // Primitive stream operations
        int sum = IntStream.range(1, 11).sum();
        double average = IntStream.range(1, 11).average().orElse(0);
        int max = IntStream.range(1, 11).max().orElse(0);

        // Box to wrapper types
        List<Integer> boxed = IntStream.range(1, 11)
            .boxed()
            .collect(Collectors.toList());

        // From strings
        IntStream chars = "Hello".chars();
        Stream<String> lines = "Line1\nLine2\nLine3".lines();

        // From file
        try (Stream<String> fileLines = Files.lines(Paths.get("file.txt"))) {
            fileLines.forEach(System.out::println);
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}

// ═══════════════════════════════════════════
// Parallel Streams
// ═══════════════════════════════════════════

public class ParallelStreams {
    public static void main(String[] args) {
        List<Integer> numbers = IntStream.rangeClosed(1, 1_000_000)
            .boxed()
            .collect(Collectors.toList());

        // Sequential stream
        long start = System.currentTimeMillis();
        long sum = numbers.stream()
            .mapToLong(Integer::longValue)
            .sum();
        long end = System.currentTimeMillis();
        System.out.println("Sequential: " + (end - start) + "ms");

        // Parallel stream
        start = System.currentTimeMillis();
        sum = numbers.parallelStream()
            .mapToLong(Integer::longValue)
            .sum();
        end = System.currentTimeMillis();
        System.out.println("Parallel: " + (end - start) + "ms");

        // Convert to parallel
        numbers.stream()
            .parallel()
            .forEach(System.out::println);

        // Convert to sequential
        numbers.parallelStream()
            .sequential()
            .forEach(System.out::println);
    }
}
```

> **💡 Pro Tip:** Use streams for data processing pipelines. Parallel streams can be faster for large datasets but have overhead. Not all operations benefit from parallelization!

---

<div align="center">

## 🧬 Generics

</div>

### Type-Safe Generic Programming 🔒

```java
// ═══════════════════════════════════════════
// Generic Classes
// ═══════════════════════════════════════════

// Generic class with single type parameter
public class Box<T> {
    private T content;

    public void set(T content) {
        this.content = content;
    }

    public T get() {
        return content;
    }
}

// Usage
Box<String> stringBox = new Box<>();
stringBox.set("Hello");
String content = stringBox.get();

Box<Integer> intBox = new Box<>();
intBox.set(42);
int number = intBox.get();

// Generic class with multiple type parameters
public class Pair<K, V> {
    private K key;
    private V value;

    public Pair(K key, V value) {
        this.key = key;
        this.value = value;
    }

    public K getKey() {
        return key;
    }

    public V getValue() {
        return value;
    }
}

// Usage
Pair<String, Integer> pair = new Pair<>("Age", 25);
String key = pair.getKey();
Integer value = pair.getValue();

// ═══════════════════════════════════════════
// Generic Methods
// ═══════════════════════════════════════════

public class GenericMethods {
    // Generic method
    public static <T> void printArray(T[] array) {
        for (T element : array) {
            System.out.println(element);
        }
    }

    // Generic method with return type
    public static <T> T getFirst(T[] array) {
        if (array.length > 0) {
            return array[0];
        }
        return null;
    }

    // Multiple type parameters
    public static <K, V> void printPair(K key, V value) {
        System.out.println(key + ": " + value);
    }

    // Usage
    public static void main(String[] args) {
        Integer[] intArray = {1, 2, 3, 4, 5};
        String[] stringArray = {"a", "b", "c"};

        printArray(intArray);
        printArray(stringArray);

        Integer first = getFirst(intArray);
        String firstStr = getFirst(stringArray);

        printPair("Name", "MrDib");
        printPair("Age", 25);
    }
}

// ═══════════════════════════════════════════
// Bounded Type Parameters
// ═══════════════════════════════════════════

// Upper bound (extends)
public class NumberBox<T extends Number> {
    private T number;

    public void set(T number) {
        this.number = number;
    }

    public double doubleValue() {
        return number.doubleValue();  // Can call Number methods
    }
}

// Usage
NumberBox<Integer> intBox = new NumberBox<>();
NumberBox<Double> doubleBox = new NumberBox<>();
// NumberBox<String> stringBox = new NumberBox<>();  // ❌ Error!

// Multiple bounds
public class MultiBox<T extends Number & Comparable<T>> {
    private T value;

    public boolean isGreaterThan(T other) {
        return value.compareTo(other) > 0;
    }
}

// Generic method with bounds
public static <T extends Comparable<T>> T max(T a, T b) {
    return a.compareTo(b) > 0 ? a : b;
}

// ═══════════════════════════════════════════
// Wildcards
// ═══════════════════════════════════════════

public class WildcardExamples {
    // Unbounded wildcard (?)
    public static void printList(List<?> list) {
        for (Object element : list) {
            System.out.println(element);
        }
    }

    // Upper bounded wildcard (? extends Type)
    public static double sumOfList(List<? extends Number> list) {
        double sum = 0.0;
        for (Number number : list) {
            sum += number.doubleValue();
        }
        return sum;
    }

    // Lower bounded wildcard (? super Type)
    public static void addIntegers(List<? super Integer> list) {
        list.add(1);
        list.add(2);
        list.add(3);
    }

    // Usage
    public static void main(String[] args) {
        List<Integer> intList = Arrays.asList(1, 2, 3);
        List<Double> doubleList = Arrays.asList(1.1, 2.2, 3.3);
        List<String> stringList = Arrays.asList("a", "b", "c");

        printList(intList);
        printList(doubleList);
        printList(stringList);

        double sum1 = sumOfList(intList);
        double sum2 = sumOfList(doubleList);

        List<Number> numbers = new ArrayList<>();
        addIntegers(numbers);
    }
}

// ═══════════════════════════════════════════
// Type Erasure & Limitations
// ═══════════════════════════════════════════

public class TypeErasure {
    // ❌ Cannot create instance of type parameter
    // public <T> void create() {
    //     T instance = new T();  // Error!
    // }

    // ❌ Cannot create array of parameterized type
    // public <T> void createArray() {
    //     T[] array = new T[10];  // Error!
    // }

    // ✅ Workaround for array creation
    @SuppressWarnings("unchecked")
    public <T> T[] createArray(Class<T> clazz, int size) {
        return (T[]) Array.newInstance(clazz, size);
    }

    // ❌ Cannot use primitives as type arguments
    // List<int> list = new ArrayList<>();  // Error!

    // ✅ Use wrapper classes
    List<Integer> list = new ArrayList<>();

    // ❌ Cannot catch generic exceptions
    // catch (T e) { }  // Error!

    // Type erasure means generic type info is lost at runtime
    public void demo() {
        List<String> strings = new ArrayList<>();
        List<Integer> integers = new ArrayList<>();

        // Both are just List at runtime
        System.out.println(strings.getClass() == integers.getClass());  // true
    }
}

// ═══════════════════════════════════════════
// Practical Generic Examples
// ═══════════════════════════════════════════

// Generic Stack
public class Stack<T> {
    private List<T> elements = new ArrayList<>();

    public void push(T element) {
        elements.add(element);
    }

    public T pop() {
        if (isEmpty()) {
            throw new EmptyStackException();
        }
        return elements.remove(elements.size() - 1);
    }

    public T peek() {
        if (isEmpty()) {
            throw new EmptyStackException();
        }
        return elements.get(elements.size() - 1);
    }

    public boolean isEmpty() {
        return elements.isEmpty();
    }

    public int size() {
        return elements.size();
    }
}

// Generic Tuple
public class Tuple<A, B, C> {
    private final A first;
    private final B second;
    private final C third;

    public Tuple(A first, B second, C third) {
        this.first = first;
        this.second = second;
        this.third = third;
    }

    public A getFirst() { return first; }
    public B getSecond() { return second; }
    public C getThird() { return third; }
}

// Generic Builder Pattern
public class Builder<T> {
    private T instance;

    public Builder(Supplier<T> supplier) {
        instance = supplier.get();
    }

    public <V> Builder<T> with(BiConsumer<T, V> setter, V value) {
        setter.accept(instance, value);
        return this;
    }

    public T build() {
        return instance;
    }
}

// Usage
Person person = new Builder<>(Person::new)
    .with(Person::setName, "MrDib")
    .with(Person::setAge, 25)
    .with(Person::setEmail, "mrdib@example.com")
    .build();
```

> **💡 Pro Tip:** Use generics to write type-safe, reusable code. Bounded wildcards (`? extends` and `? super`) follow the PECS principle: Producer Extends, Consumer Super!

---

<div align="center">

## 📝 Annotations

</div>

### Metadata & Code Documentation 🏷️

```java
// ═══════════════════════════════════════════
// Built-in Annotations
// ═══════════════════════════════════════════

public class BuiltInAnnotations {
    // @Override - marks method as overriding parent method
    @Override
    public String toString() {
        return "BuiltInAnnotations";
    }

    // @Deprecated - marks code as deprecated
    @Deprecated
    public void oldMethod() {
        System.out.println("This method is deprecated");
    }

    @Deprecated(since = "2.0", forRemoval = true)
    public void veryOldMethod() {
        System.out.println("This will be removed soon");
    }

    // @SuppressWarnings - suppress compiler warnings
    @SuppressWarnings("unchecked")
    public void uncheckedOperation() {
        List list = new ArrayList();
        list.add("String");
    }

    @SuppressWarnings({"unchecked", "deprecation"})
    public void multipleSuppressions() {
        // Code with multiple warnings
    }

    // @FunctionalInterface - marks interface as functional
    @FunctionalInterface
    interface Calculator {
        int calculate(int a, int b);
    }

    // @SafeVarargs - suppress varargs warnings
    @SafeVarargs
    public final <T> void printAll(T... items) {
        for (T item : items) {
            System.out.println(item);
        }
    }
}

// ═══════════════════════════════════════════
// Custom Annotations
// ═══════════════════════════════════════════

// Simple marker annotation
@interface MyAnnotation {
}

// Annotation with single element
@interface Author {
    String value();
}

// Annotation with multiple elements
@interface Version {
    int major();
    int minor();
    String description() default "";
}

// Annotation with array elements
@interface Authors {
    String[] value();
}

// Meta-annotations
@Retention(RetentionPolicy.RUNTIME)  // Available at runtime
@Target(ElementType.METHOD)          // Can be applied to methods only
@Documented                          // Include in JavaDoc
@Inherited                           // Inherited by subclasses
@interface MyMethodAnnotation {
    String value();
}

// Target types
@Target({
    ElementType.TYPE,           // Class, interface, enum
    ElementType.FIELD,          // Field
    ElementType.METHOD,         // Method
    ElementType.PARAMETER,      // Method parameter
    ElementType.CONSTRUCTOR,    // Constructor
    ElementType.LOCAL_VARIABLE, // Local variable
    ElementType.ANNOTATION_TYPE,// Annotation
    ElementType.PACKAGE         // Package
})
@interface MultiTargetAnnotation {
}

// Retention policies
@Retention(RetentionPolicy.SOURCE)   // Discarded by compiler
@interface SourceAnnotation {}

@Retention(RetentionPolicy.CLASS)    // In .class file, not at runtime
@interface ClassAnnotation {}

@Retention(RetentionPolicy.RUNTIME)  // Available at runtime via reflection
@interface RuntimeAnnotation {}

// ═══════════════════════════════════════════
// Using Custom Annotations
// ═══════════════════════════════════════════

@Author("MrDib")
@Version(major = 1, minor = 0, description = "Initial release")
public class AnnotatedClass {

    @MyMethodAnnotation("Important method")
    public void annotatedMethod() {
        System.out.println("Method with annotation");
    }

    @Authors({"Alice", "Bob", "Charlie"})
    public void multipleAuthors() {
        System.out.println("Method with multiple authors");
    }
}

// ═══════════════════════════════════════════
// Processing Annotations at Runtime
// ═══════════════════════════════════════════

public class AnnotationProcessor {
    public static void main(String[] args) {
        Class<AnnotatedClass> clazz = AnnotatedClass.class;

        // Check if annotation is present
        if (clazz.isAnnotationPresent(Author.class)) {
            Author author = clazz.getAnnotation(Author.class);
            System.out.println("Author: " + author.value());
        }

        if (clazz.isAnnotationPresent(Version.class)) {
            Version version = clazz.getAnnotation(Version.class);
            System.out.printf("Version: %d.%d - %s%n",
                version.major(),
                version.minor(),
                version.description()
            );
        }

        // Get all annotations
        Annotation[] annotations = clazz.getAnnotations();
        for (Annotation annotation : annotations) {
            System.out.println(annotation);
        }

        // Process method annotations
        for (Method method : clazz.getDeclaredMethods()) {
            if (method.isAnnotationPresent(MyMethodAnnotation.class)) {
                MyMethodAnnotation annotation =
                    method.getAnnotation(MyMethodAnnotation.class);
                System.out.println("Method: " + method.getName());
                System.out.println("Annotation: " + annotation.value());
            }
        }
    }
}

// ═══════════════════════════════════════════
// Practical Annotation Examples
// ═══════════════════════════════════════════

// Test annotation (like JUnit)
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.METHOD)
@interface Test {
    long timeout() default 0L;
    Class<? extends Throwable> expected() default None.class;

    class None extends Throwable {
        private static final long serialVersionUID = 1L;
    }
}

// Validation annotations
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.FIELD)
@interface NotNull {
    String message() default "Field cannot be null";
}

@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.FIELD)
@interface Min {
    int value();
    String message() default "Value must be at least {value}";
}

@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.FIELD)
@interface Email {
    String message() default "Invalid email format";
}

// Usage
public class User {
    @NotNull(message = "Name is required")
    private String name;

    @Min(value = 0, message = "Age must be positive")
    private int age;

    @Email
    private String email;

    // Constructor, getters, setters...
}

// Simple validator
public class Validator {
    public static void validate(Object obj) throws Exception {
        Class<?> clazz = obj.getClass();

        for (Field field : clazz.getDeclaredFields()) {
            field.setAccessible(true);

            if (field.isAnnotationPresent(NotNull.class)) {
                if (field.get(obj) == null) {
                    NotNull annotation = field.getAnnotation(NotNull.class);
                    throw new Exception(annotation.message());
                }
            }

            if (field.isAnnotationPresent(Min.class)) {
                Min annotation = field.getAnnotation(Min.class);
                int value = (int) field.get(obj);
                if (value < annotation.value()) {
                    String message = annotation.message()
                        .replace("{value}", String.valueOf(annotation.value()));
                    throw new Exception(message);
                }
            }
        }
    }
}
```

> **💡 Pro Tip:** Use annotations for metadata, not business logic. Runtime annotations require reflection (slow). Compile-time annotation processing is faster and type-safe!

---

<div align="center">

## 📂 File I/O

</div>

### Reading & Writing Files 📄

```java
import java.io.*;
import java.nio.file.*;
import java.nio.charset.StandardCharsets;
import java.util.List;
import java.util.stream.Stream;

// ═══════════════════════════════════════════
// Traditional I/O (java.io)
// ═══════════════════════════════════════════

public class TraditionalIO {
    // Read file line by line
    public static void readFile(String filename) throws IOException {
        try (BufferedReader reader = new BufferedReader(new FileReader(filename))) {
            String line;
            while ((line = reader.readLine()) != null) {
                System.out.println(line);
            }
        }
    }

    // Write to file
    public static void writeFile(String filename, String content) throws IOException {
        try (BufferedWriter writer = new BufferedWriter(new FileWriter(filename))) {
            writer.write(content);
        }
    }

    // Append to file
    public static void appendToFile(String filename, String content) throws IOException {
        try (BufferedWriter writer = new BufferedWriter(
                new FileWriter(filename, true))) {
            writer.write(content);
            writer.newLine();
        }
    }

    // Read entire file as string
    public static String readEntireFile(String filename) throws IOException {
        StringBuilder content = new StringBuilder();
        try (BufferedReader reader = new BufferedReader(new FileReader(filename))) {
            String line;
            while ((line = reader.readLine()) != null) {
                content.append(line).append("\n");
            }
        }
        return content.toString();
    }

    // Copy file
    public static void copyFile(String source, String destination) throws IOException {
        try (FileInputStream in = new FileInputStream(source);
             FileOutputStream out = new FileOutputStream(destination)) {

            byte[] buffer = new byte[1024];
            int bytesRead;
            while ((bytesRead = in.read(buffer)) != -1) {
                out.write(buffer, 0, bytesRead);
            }
        }
    }
}

// ═══════════════════════════════════════════
// Modern NIO.2 (java.nio.file)
// ═══════════════════════════════════════════

public class ModernFileIO {
    // Read file as string (Java 11+)
    public static String readFile(String filename) throws IOException {
        return Files.readString(Path.of(filename));
    }

    // Read file as string with encoding
    public static String readFileWithEncoding(String filename) throws IOException {
        return Files.readString(Path.of(filename), StandardCharsets.UTF_8);
    }

    // Read all lines
    public static List<String> readAllLines(String filename) throws IOException {
        return Files.readAllLines(Path.of(filename));
    }

    // Write string to file (Java 11+)
    public static void writeFile(String filename, String content) throws IOException {
        Files.writeString(Path.of(filename), content);
    }

    // Write lines to file
    public static void writeLines(String filename, List<String> lines) throws IOException {
        Files.write(Path.of(filename), lines);
    }

    // Append to file
    public static void appendToFile(String filename, String content) throws IOException {
        Files.writeString(
            Path.of(filename),
            content,
            StandardOpenOption.APPEND,
            StandardOpenOption.CREATE
        );
    }

    // Read file as stream (memory efficient for large files)
    public static void readFileAsStream(String filename) throws IOException {
        try (Stream<String> lines = Files.lines(Path.of(filename))) {
            lines.forEach(System.out::println);
        }
    }

    // Process large file efficiently
    public static long countLongLines(String filename) throws IOException {
        try (Stream<String> lines = Files.lines(Path.of(filename))) {
            return lines.filter(line -> line.length() > 100).count();
        }
    }

    // Copy file
    public static void copyFile(String source, String destination) throws IOException {
        Files.copy(
            Path.of(source),
            Path.of(destination),
            StandardCopyOption.REPLACE_EXISTING
        );
    }

    // Move/rename file
    public static void moveFile(String source, String destination) throws IOException {
        Files.move(
            Path.of(source),
            Path.of(destination),
            StandardCopyOption.REPLACE_EXISTING
        );
    }

    // Delete file
    public static void deleteFile(String filename) throws IOException {
        Files.delete(Path.of(filename));
    }

    // Delete if exists
    public static boolean deleteIfExists(String filename) throws IOException {
        return Files.deleteIfExists(Path.of(filename));
    }
}

// ═══════════════════════════════════════════
// File & Directory Operations
// ═══════════════════════════════════════════

public class FileOperations {
    public static void main(String[] args) throws IOException {
        Path path = Path.of("myfile.txt");

        // Check existence
        boolean exists = Files.exists(path);
        boolean notExists = Files.notExists(path);

        // Check file properties
        boolean isRegularFile = Files.isRegularFile(path);
        boolean isDirectory = Files.isDirectory(path);
        boolean isSymbolicLink = Files.isSymbolicLink(path);
        boolean isReadable = Files.isReadable(path);
        boolean isWritable = Files.isWritable(path);
        boolean isExecutable = Files.isExecutable(path);

        // Get file attributes
        long size = Files.size(path);
        FileTime lastModified = Files.getLastModifiedTime(path);

        // Create directory
        Path dir = Path.of("mydir");
        Files.createDirectory(dir);

        // Create directories (including parents)
        Path nestedDir = Path.of("parent/child/grandchild");
        Files.createDirectories(nestedDir);

        // Create temp file
        Path tempFile = Files.createTempFile("prefix", ".txt");

        // Create temp directory
        Path tempDir = Files.createTempDirectory("prefix");

        // List files in directory
        try (Stream<Path> paths = Files.list(Path.of("."))) {
            paths.forEach(System.out::println);
        }

        // Walk directory tree
        try (Stream<Path> paths = Files.walk(Path.of("."))) {
            paths.filter(Files::isRegularFile)
                 .forEach(System.out::println);
        }

        // Walk with depth limit
        try (Stream<Path> paths = Files.walk(Path.of("."), 2)) {
            paths.forEach(System.out::println);
        }

        // Find files
        try (Stream<Path> paths = Files.find(
                Path.of("."),
                Integer.MAX_VALUE,
                (path, attrs) -> path.toString().endsWith(".java")
        )) {
            paths.forEach(System.out::println);
        }

        // Delete directory recursively
        Files.walk(Path.of("mydir"))
             .sorted(Comparator.reverseOrder())
             .forEach(p -> {
                 try {
                     Files.delete(p);
                 } catch (IOException e) {
                     e.printStackTrace();
                 }
             });
    }
}

// ═══════════════════════════════════════════
// Binary File Operations
// ═══════════════════════════════════════════

public class BinaryFileIO {
    // Read binary file
    public static byte[] readBinaryFile(String filename) throws IOException {
        return Files.readAllBytes(Path.of(filename));
    }

    // Write binary file
    public static void writeBinaryFile(String filename, byte[] data) throws IOException {
        Files.write(Path.of(filename), data);
    }

    // Read with InputStream
    public static void readWithInputStream(String filename) throws IOException {
        try (InputStream in = Files.newInputStream(Path.of(filename))) {
            byte[] buffer = new byte[1024];
            int bytesRead;
            while ((bytesRead = in.read(buffer)) != -1) {
                // Process bytes
            }
        }
    }

    // Write with OutputStream
    public static void writeWithOutputStream(String filename, byte[] data) throws IOException {
        try (OutputStream out = Files.newOutputStream(Path.of(filename))) {
            out.write(data);
        }
    }
}

// ═══════════════════════════════════════════
// Serialization
// ═══════════════════════════════════════════

// Serializable class
class Person implements Serializable {
    private static final long serialVersionUID = 1L;

    private String name;
    private int age;
    private transient String password;  // Not serialized

    public Person(String name, int age, String password) {
        this.name = name;
        this.age = age;
        this.password = password;
    }

    // Getters and setters...
}

public class SerializationExample {
    // Serialize object to file
    public static void serialize(Person person, String filename) throws IOException {
        try (ObjectOutputStream out = new ObjectOutputStream(
                new FileOutputStream(filename))) {
            out.writeObject(person);
        }
    }

    // Deserialize object from file
    public static Person deserialize(String filename)
            throws IOException, ClassNotFoundException {
        try (ObjectInputStream in = new ObjectInputStream(
                new FileInputStream(filename))) {
            return (Person) in.readObject();
        }
    }

    public static void main(String[] args) throws Exception {
        Person person = new Person("MrDib", 25, "secret");

        // Serialize
        serialize(person, "person.ser");

        // Deserialize
        Person loaded = deserialize("person.ser");
        System.out.println(loaded.getName());  // "MrDib"
        System.out.println(loaded.getPassword());  // null (transient)
    }
}

// ═══════════════════════════════════════════
// File Watching (Monitor file changes)
// ═══════════════════════════════════════════

public class FileWatcher {
    public static void watchDirectory(String dirPath) throws IOException, InterruptedException {
        WatchService watchService = FileSystems.getDefault().newWatchService();
        Path path = Path.of(dirPath);

        path.register(
            watchService,
            StandardWatchEventKinds.ENTRY_CREATE,
            StandardWatchEventKinds.ENTRY_DELETE,
            StandardWatchEventKinds.ENTRY_MODIFY
        );

        System.out.println("Watching directory: " + dirPath);

        while (true) {
            WatchKey key = watchService.take();

            for (WatchEvent<?> event : key.pollEvents()) {
                WatchEvent.Kind<?> kind = event.kind();
                Path filename = (Path) event.context();

                System.out.println(kind + ": " + filename);
            }

            boolean valid = key.reset();
            if (!valid) {
                break;
            }
        }
    }
}
```

> **💡 Pro Tip:** Use NIO.2 (java.nio.file) for modern file operations - it's simpler and more powerful! Always use try-with-resources to ensure files are closed properly.

---

<div align="center">

## ⚠️ Exception Handling

</div>

### Robust Error Management 🛡️

```java
// ═══════════════════════════════════════════
// Exception Hierarchy
// ═══════════════════════════════════════════

/*
Throwable
├── Error (Serious problems, don't catch)
│   ├── OutOfMemoryError
│   ├── StackOverflowError
│   └── VirtualMachineError
│
└── Exception
    ├── Checked Exceptions (Must be handled)
    │   ├── IOException
    │   ├── SQLException
    │   ├── ClassNotFoundException
    │   └── FileNotFoundException
    │
    └── RuntimeException (Unchecked)
        ├── NullPointerException
        ├── ArrayIndexOutOfBoundsException
        ├── ArithmeticException
        ├── IllegalArgumentException
        ├── NumberFormatException
        └── ClassCastException
*/

// ═══════════════════════════════════════════
// Try-Catch-Finally
// ═══════════════════════════════════════════

public class ExceptionHandling {
    public static void main(String[] args) {
        // Basic try-catch
        try {
            int result = 10 / 0;
        } catch (ArithmeticException e) {
            System.out.println("Cannot divide by zero!");
        }

        // Multiple catch blocks (specific to general)
        try {
            int[] arr = {1, 2, 3};
            System.out.println(arr[5]);
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Array index out of bounds!");
        } catch (Exception e) {
            System.out.println("General exception");
        }

        // Multi-catch (Java 7+)
        try {
            // Some code
        } catch (IOException | SQLException e) {
            System.out.println("IO or SQL exception");
            e.printStackTrace();
        }

        // Finally block (always executes)
        try {
            int result = 10 / 2;
        } catch (Exception e) {
            System.out.println("Error occurred");
        } finally {
            System.out.println("Cleanup code");
        }

        // Try-with-resources (Java 7+)
        try (FileReader reader = new FileReader("file.txt");
             BufferedReader br = new BufferedReader(reader)) {
            String line = br.readLine();
            System.out.println(line);
        } catch (IOException e) {
            e.printStackTrace();
        }
        // Resources automatically closed

        // Multiple resources
        try (FileInputStream in = new FileInputStream("input.txt");
             FileOutputStream out = new FileOutputStream("output.txt")) {
            // Copy file
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}

// ═══════════════════════════════════════════
// Custom Exceptions
// ═══════════════════════════════════════════

// Custom checked exception
public class InvalidAgeException extends Exception {
    public InvalidAgeException(String message) {
        super(message);
    }

    public InvalidAgeException(String message, Throwable cause) {
        super(message, cause);
    }
}

// Custom unchecked exception
public class InvalidEmailException extends RuntimeException {
    public InvalidEmailException(String message) {
        super(message);
    }
}

// Custom exception with additional data
public class ValidationException extends Exception {
    private final String field;
    private final Object value;

    public ValidationException(String message, String field, Object value) {
        super(message);
        this.field = field;
        this.value = value;
    }

    public String getField() {
        return field;
    }

    public Object getValue() {
        return value;
    }
}

// Usage
public class User {
    private String name;
    private int age;
    private String email;

    public void setAge(int age) throws InvalidAgeException {
        if (age < 0 || age > 150) {
            throw new InvalidAgeException(
                "Age must be between 0 and 150, got: " + age
            );
        }
        this.age = age;
    }

    public void setEmail(String email) {
        if (!email.contains("@")) {
            throw new InvalidEmailException("Invalid email format: " + email);
        }
        this.email = email;
    }
}

// ═══════════════════════════════════════════
// Best Practices
// ═══════════════════════════════════════════

public class ExceptionBestPractices {
    // ✅ Good - specific exception
    public void readFile(String filename) throws FileNotFoundException {
        FileReader reader = new FileReader(filename);
    }

    // ❌ Bad - generic exception
    public void readFile2(String filename) throws Exception {
        FileReader reader = new FileReader(filename);
    }

    // ✅ Good - preserve stack trace when wrapping
    public void wrapper() throws CustomException {
        try {
            dangerousMethod();
        } catch (IOException e) {
            throw new CustomException("Failed to process", e);  // Preserve cause
        }
    }

    // ❌ Bad - swallow exception
    public void bad() {
        try {
            riskyOperation();
        } catch (Exception e) {
            // Silently ignoring - DON'T DO THIS!
        }
    }

    // ✅ Good - at least log it
    public void better() {
        try {
            riskyOperation();
        } catch (Exception e) {
            logger.error("Operation failed", e);
            throw new RuntimeException("Wrapped exception", e);
        }
    }

    // ✅ Good - validate parameters
    public void divide(int a, int b) {
        if (b == 0) {
            throw new IllegalArgumentException("Divisor cannot be zero");
        }
        return a / b;
    }

    // ✅ Good - document exceptions
    /**
     * Processes user registration.
     *
     * @param user the user to register
     * @throws InvalidAgeException if age is invalid
     * @throws InvalidEmailException if email format is wrong
     * @throws DuplicateUserException if user already exists
     */
    public void registerUser(User user)
            throws InvalidAgeException, DuplicateUserException {
        // Implementation
    }

    // ✅ Good - fail fast
    public void processUser(User user) {
        Objects.requireNonNull(user, "User cannot be null");

        if (user.getAge() < 0) {
            throw new IllegalArgumentException("Age cannot be negative");
        }

        // Process user...
    }
}

// ═══════════════════════════════════════════
// Exception Handling Patterns
// ═══════════════════════════════════════════

// Result pattern (alternative to exceptions)
public class Result<T> {
    private final T value;
    private final Exception error;

    private Result(T value, Exception error) {
        this.value = value;
        this.error = error;
    }

    public static <T> Result<T> success(T value) {
        return new Result<>(value, null);
    }

    public static <T> Result<T> failure(Exception error) {
        return new Result<>(null, error);
    }

    public boolean isSuccess() {
        return error == null;
    }

    public T getValue() {
        if (!isSuccess()) {
            throw new IllegalStateException("Cannot get value from failed result");
        }
        return value;
    }

    public Exception getError() {
        return error;
    }
}

// Usage
public Result<User> findUser(int id) {
    try {
        User user = database.findUser(id);
        return Result.success(user);
    } catch (Exception e) {
        return Result.failure(e);
    }
}

Result<User> result = findUser(123);
if (result.isSuccess()) {
    User user = result.getValue();
} else {
    Exception error = result.getError();
}

// Try pattern (Java 8+ style)
public class Try<T> {
    private final T value;
    private final Exception exception;

    private Try(T value, Exception exception) {
        this.value = value;
        this.exception = exception;
    }

    public static <T> Try<T> of(Supplier<T> supplier) {
        try {
            return new Try<>(supplier.get(), null);
        } catch (Exception e) {
            return new Try<>(null, e);
        }
    }

    public boolean isSuccess() {
        return exception == null;
    }

    public T get() {
        if (!isSuccess()) {
            throw new RuntimeException(exception);
        }
        return value;
    }

    public T getOrElse(T defaultValue) {
        return isSuccess() ? value : defaultValue;
    }

    public <U> Try<U> map(Function<T, U> mapper) {
        if (!isSuccess()) {
            return new Try<>(null, exception);
        }
        return Try.of(() -> mapper.apply(value));
    }
}

// Usage
Try<String> content = Try.of(() -> Files.readString(Path.of("file.txt")));
String text = content.getOrElse("Default content");
```

> **💡 Pro Tip:** Use checked exceptions for recoverable conditions, unchecked for programming errors. Always preserve the original exception when wrapping. Never catch Throwable or Error!

---

<div align="center">

## 🧵 Concurrency & Multithreading

</div>

### Concurrent Programming 💪

```java
import java.util.concurrent.*;
import java.util.concurrent.atomic.*;
import java.util.concurrent.locks.*;

// ═══════════════════════════════════════════
// Creating Threads
// ═══════════════════════════════════════════

// Method 1: Extend Thread class
class MyThread extends Thread {
    @Override
    public void run() {
        System.out.println("Thread running: " + Thread.currentThread().getName());
    }
}

// Method 2: Implement Runnable
class MyRunnable implements Runnable {
    @Override
    public void run() {
        System.out.println("Runnable running: " + Thread.currentThread().getName());
    }
}

// Method 3: Lambda (Java 8+)
public class ThreadCreation {
    public static void main(String[] args) {
        // Using Thread class
        MyThread thread1 = new MyThread();
        thread1.start();

        // Using Runnable
        Thread thread2 = new Thread(new MyRunnable());
        thread2.start();

        // Using lambda
        Thread thread3 = new Thread(() -> {
            System.out.println("Lambda thread running");
        });
        thread3.start();

        // Thread with name
        Thread thread4 = new Thread(() -> {
            System.out.println("Named thread");
        }, "MyThread");
        thread4.start();

        // Thread methods
        try {
            Thread.sleep(1000);  // Sleep for 1 second
            thread1.join();      // Wait for thread1 to complete
            thread2.join(2000);  // Wait max 2 seconds
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        // Thread info
        Thread current = Thread.currentThread();
        System.out.println("Name: " + current.getName());
        System.out.println("Priority: " + current.getPriority());
        System.out.println("State: " + current.getState());
        System.out.println("Is alive: " + current.isAlive());
    }
}

// ═══════════════════════════════════════════
// Synchronization
// ═══════════════════════════════════════════

public class Counter {
    private int count = 0;

    // Synchronized method
    public synchronized void increment() {
        count++;
    }

    // Synchronized block
    public void incrementBlock() {
        synchronized(this) {
            count++;
        }
    }

    // Synchronized static method
    public static synchronized void staticMethod() {
        // Synchronized on class object
    }

    public int getCount() {
        return count;
    }
}

// Race condition demo
public class RaceConditionDemo {
    public static void main(String[] args) throws InterruptedException {
        Counter counter = new Counter();

        Runnable task = () -> {
            for (int i = 0; i < 1000; i++) {
                counter.increment();
            }
        };

        Thread t1 = new Thread(task);
        Thread t2 = new Thread(task);

        t1.start();
        t2.start();
        t1.join();
        t2.join();

        System.out.println("Count: " + counter.getCount());  // Should be 2000
    }
}

// ═══════════════════════════════════════════
// ExecutorService
// ═══════════════════════════════════════════

public class ExecutorExample {
    public static void main(String[] args) {
        // Fixed thread pool
        ExecutorService executor = Executors.newFixedThreadPool(5);

        for (int i = 0; i < 10; i++) {
            int taskId = i;
            executor.submit(() -> {
                System.out.println("Task " + taskId + " on " +
                                 Thread.currentThread().getName());
                try {
                    Thread.sleep(1000);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            });
        }

        executor.shutdown();  // Don't accept new tasks

        try {
            if (!executor.awaitTermination(1, TimeUnit.MINUTES)) {
                executor.shutdownNow();  // Force shutdown
            }
        } catch (InterruptedException e) {
            executor.shutdownNow();
        }

        // Different executor types
        ExecutorService single = Executors.newSingleThreadExecutor();
        ExecutorService cached = Executors.newCachedThreadPool();
        ScheduledExecutorService scheduled = Executors.newScheduledThreadPool(2);

        // Scheduled execution
        scheduled.schedule(() -> {
            System.out.println("Task executed after delay");
        }, 5, TimeUnit.SECONDS);

        // Fixed rate execution
        scheduled.scheduleAtFixedRate(() -> {
            System.out.println("Periodic task");
        }, 0, 1, TimeUnit.SECONDS);

        scheduled.shutdown();
    }
}

// ═══════════════════════════════════════════
// Callable & Future
// ═══════════════════════════════════════════

public class CallableFutureExample {
    public static void main(String[] args) throws Exception {
        ExecutorService executor = Executors.newSingleThreadExecutor();

        // Callable returns a value
        Callable<Integer> task = () -> {
            Thread.sleep(1000);
            return 42;
        };

        Future<Integer> future = executor.submit(task);

        // Do other work while task is running
        System.out.println("Doing other work...");

        // Check if done
        if (future.isDone()) {
            System.out.println("Task completed");
        }

        // Cancel task
        // future.cancel(true);

        // Get result (blocks until complete)
        Integer result = future.get();
        System.out.println("Result: " + result);

        // Get with timeout
        try {
            Integer result2 = future.get(2, TimeUnit.SECONDS);
        } catch (TimeoutException e) {
            System.out.println("Task timed out");
        }

        executor.shutdown();
    }
}

// ═══════════════════════════════════════════
// CompletableFuture (Java 8+)
// ═══════════════════════════════════════════

public class CompletableFutureExample {
    public static void main(String[] args) {
        // Async execution
        CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            return "Hello";
        });

        // Chain operations
        future.thenApply(s -> s + ", World!")
              .thenAccept(System.out::println)
              .thenRun(() -> System.out.println("Done"));

        // Combine multiple futures
        CompletableFuture<String> future1 =
            CompletableFuture.supplyAsync(() -> "Hello");
        CompletableFuture<String> future2 =
            CompletableFuture.supplyAsync(() -> "World");

        CompletableFuture<String> combined = future1.thenCombine(
            future2,
            (s1, s2) -> s1 + " " + s2
        );

        combined.thenAccept(System.out::println);

        // Handle exceptions
        CompletableFuture<String> futureWithError =
            CompletableFuture.supplyAsync(() -> {
                if (true) throw new RuntimeException("Error!");
                return "Success";
            }).exceptionally(ex -> {
                System.out.println("Exception: " + ex.getMessage());
                return "Recovered";
            });

        // All of (wait for all)
        CompletableFuture<Void> allOf = CompletableFuture.allOf(
            future1, future2, combined
        );

        // Any of (wait for first)
        CompletableFuture<Object> anyOf = CompletableFuture.anyOf(
            future1, future2
        );
    }
}

// ═══════════════════════════════════════════
// Concurrent Collections
// ═══════════════════════════════════════════

public class ConcurrentCollectionsExample {
    public static void main(String[] args) {
        // ConcurrentHashMap
        ConcurrentHashMap<String, Integer> map = new ConcurrentHashMap<>();
        map.put("Alice", 25);
        map.put("Bob", 30);

        // Atomic operations
        map.putIfAbsent("Charlie", 35);
        map.computeIfAbsent("David", k -> 40);
        map.computeIfPresent("Alice", (k, v) -> v + 1);
        map.merge("Bob", 5, Integer::sum);

        // CopyOnWriteArrayList (for read-heavy scenarios)
        CopyOnWriteArrayList<String> list = new CopyOnWriteArrayList<>();
        list.add("A");
        list.add("B");

        // ConcurrentLinkedQueue
        ConcurrentLinkedQueue<String> queue = new ConcurrentLinkedQueue<>();
        queue.offer("First");
        queue.offer("Second");
        String head = queue.poll();

        // BlockingQueue
        BlockingQueue<String> blockingQueue = new LinkedBlockingQueue<>();

        // Producer
        new Thread(() -> {
            try {
                for (int i = 0; i < 10; i++) {
                    blockingQueue.put("Item " + i);
                    Thread.sleep(100);
                }
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }).start();

        // Consumer
        new Thread(() -> {
            try {
                while (true) {
                    String item = blockingQueue.take();
                    System.out.println("Consumed: " + item);
                }
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }).start();
    }
}

// ═══════════════════════════════════════════
// Atomic Variables
// ═══════════════════════════════════════════

public class AtomicExample {
    private AtomicInteger counter = new AtomicInteger(0);
    private AtomicLong longCounter = new AtomicLong(0);
    private AtomicBoolean flag = new AtomicBoolean(false);

    public void increment() {
        counter.incrementAndGet();
        counter.addAndGet(5);
        counter.compareAndSet(10, 20);  // CAS operation
    }

    public int getCount() {
        return counter.get();
    }

    // AtomicReference for objects
    private AtomicReference<String> message = new AtomicReference<>("Initial");

    public void updateMessage(String newMessage) {
        message.set(newMessage);
        message.compareAndSet("Initial", "Updated");
    }
}

// ═══════════════════════════════════════════
// Locks
// ═══════════════════════════════════════════

public class LockExample {
    private final Lock lock = new ReentrantLock();
    private final ReadWriteLock rwLock = new ReentrantReadWriteLock();
    private int count = 0;

    public void increment() {
        lock.lock();
        try {
            count++;
        } finally {
            lock.unlock();
        }
    }

    // Try lock with timeout
    public void incrementWithTimeout() {
        try {
            if (lock.tryLock(1, TimeUnit.SECONDS)) {
                try {
                    count++;
                } finally {
                    lock.unlock();
                }
            } else {
                System.out.println("Could not acquire lock");
            }
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }

    // ReadWriteLock
    private String data = "";

    public void write(String value) {
        rwLock.writeLock().lock();
        try {
            data = value;
        } finally {
            rwLock.writeLock().unlock();
        }
    }

    public String read() {
        rwLock.readLock().lock();
        try {
            return data;
        } finally {
            rwLock.readLock().unlock();
        }
    }
}
```

> **💡 Pro Tip:** Always prefer **ExecutorService** over manually creating threads. Use **CompletableFuture** for async programming. Use concurrent collections for thread-safe operations without manual locking!

---

<div align="center">

## 🧪 Testing

</div>

### JUnit & Testing Best Practices 🎯

```java
import org.junit.jupiter.api.*;
import static org.junit.jupiter.api.Assertions.*;
import org.mockito.*;
import static org.mockito.Mockito.*;

// ═══════════════════════════════════════════
// JUnit 5 Basics
// ═══════════════════════════════════════════

public class CalculatorTest {
    private Calculator calculator;

    @BeforeAll
    static void setupAll() {
        // Runs once before all tests
        System.out.println("Starting tests...");
    }

    @BeforeEach
    void setup() {
        // Runs before each test
        calculator = new Calculator();
    }

    @Test
    void testAddition() {
        assertEquals(5, calculator.add(2, 3));
        assertEquals(0, calculator.add(-1, 1));
        assertEquals(-5, calculator.add(-2, -3));
    }

    @Test
    @DisplayName("Subtraction should work correctly")
    void testSubtraction() {
        assertEquals(1, calculator.subtract(3, 2));
        assertEquals(-2, calculator.subtract(-1, 1));
    }

    @Test
    void testMultiplication() {
        assertEquals(6, calculator.multiply(2, 3));
        assertEquals(0, calculator.multiply(0, 5));
    }

    @Test
    void testDivision() {
        assertEquals(2.0, calculator.divide(6, 3), 0.001);
        assertEquals(2.5, calculator.divide(5, 2), 0.001);
    }

    @Test
    void testDivisionByZero() {
        assertThrows(ArithmeticException.class, () -> {
            calculator.divide(10, 0);
        });
    }

    @Test
    @Disabled("Not implemented yet")
    void testSquareRoot() {
        // Test disabled
    }

    @Test
    @Timeout(value = 1, unit = TimeUnit.SECONDS)
    void testTimeout() {
        // Must complete within 1 second
        calculator.add(2, 3);
    }

    @AfterEach
    void tearDown() {
        // Runs after each test
        calculator = null;
    }

    @AfterAll
    static void tearDownAll() {
        // Runs once after all tests
        System.out.println("All tests completed");
    }
}

// ═══════════════════════════════════════════
// Assertions
// ═══════════════════════════════════════════

public class AssertionExamples {
    @Test
    void testAssertions() {
        // Equality
        assertEquals(expected, actual);
        assertEquals(expected, actual, "Custom failure message");
        assertNotEquals(unexpected, actual);

        // Boolean
        assertTrue(condition);
        assertFalse(condition);

        // Null
        assertNull(object);
        assertNotNull(object);

        // Same/Not same (reference equality)
        assertSame(expected, actual);
        assertNotSame(unexpected, actual);

        // Arrays
        assertArrayEquals(expectedArray, actualArray);

        // Iterables
        assertIterableEquals(expectedList, actualList);

        // Lines (for multi-line strings)
        assertLinesMatch(expectedLines, actualLines);

        // Exceptions
        Exception exception = assertThrows(Exception.class, () -> {
            // Code that throws exception
        });
        assertEquals("Expected message", exception.getMessage());

        // Timeout
        assertTimeout(Duration.ofSeconds(1), () -> {
            // Code that should complete within timeout
        });

        // Timeout preemptively (aborts if timeout exceeded)
        assertTimeoutPreemptively(Duration.ofSeconds(1), () -> {
            // Code that should complete within timeout
        });

        // All assertions (all checked even if one fails)
        assertAll(
            () -> assertEquals(5, calculator.add(2, 3)),
            () -> assertEquals(1, calculator.subtract(3, 2)),
            () -> assertEquals(6, calculator.multiply(2, 3)),
            () -> assertEquals(2, calculator.divide(6, 3))
        );

        // Grouped assertions
        assertAll("Person properties",
            () -> assertEquals("John", person.getName()),
            () -> assertEquals(25, person.getAge()),
            () -> assertEquals("john@example.com", person.getEmail())
        );
    }
}

// ═══════════════════════════════════════════
// Parameterized Tests
// ═══════════════════════════════════════════

import org.junit.jupiter.params.ParameterizedTest;
import org.junit.jupiter.params.provider.*;

public class ParameterizedTests {
    @ParameterizedTest
    @ValueSource(ints = {2, 4, 6, 8, 10})
    void testEvenNumbers(int number) {
        assertTrue(number % 2 == 0);
    }

    @ParameterizedTest
    @ValueSource(strings = {"hello", "world", "java"})
    void testStrings(String str) {
        assertNotNull(str);
        assertTrue(str.length() > 0);
    }

    @ParameterizedTest
    @CsvSource({
        "1, 2, 3",
        "10, 20, 30",
        "100, 200, 300"
    })
    void testAddition(int a, int b, int expected) {
        assertEquals(expected, calculator.add(a, b));
    }

    @ParameterizedTest
    @CsvFileSource(resources = "/test-data.csv", numLinesToSkip = 1)
    void testFromCsvFile(int a, int b, int expected) {
        assertEquals(expected, calculator.add(a, b));
    }

    @ParameterizedTest
    @MethodSource("provideTestData")
    void testWithMethodSource(String input, int expected) {
        assertEquals(expected, input.length());
    }

    static Stream<Arguments> provideTestData() {
        return Stream.of(
            Arguments.of("hello", 5),
            Arguments.of("world", 5),
            Arguments.of("java", 4)
        );
    }

    @ParameterizedTest
    @EnumSource(Day.class)
    void testEnumSource(Day day) {
        assertNotNull(day);
    }

    @ParameterizedTest
    @EnumSource(value = Day.class, names = {"MONDAY", "FRIDAY"})
    void testSpecificEnumValues(Day day) {
        assertTrue(day == Day.MONDAY || day == Day.FRIDAY);
    }
}

// ═══════════════════════════════════════════
// Test Lifecycle & Nested Tests
// ═══════════════════════════════════════════

@TestInstance(TestInstance.Lifecycle.PER_CLASS)  // One instance for all tests
public class LifecycleTest {
    private int counter = 0;

    @BeforeAll
    void setupAll() {
        // Non-static with PER_CLASS
        counter = 0;
    }

    @Nested
    @DisplayName("Tests for positive numbers")
    class PositiveNumbers {
        @Test
        void testPositive() {
            assertTrue(10 > 0);
        }
    }

    @Nested
    @DisplayName("Tests for negative numbers")
    class NegativeNumbers {
        @Test
        void testNegative() {
            assertTrue(-10 < 0);
        }
    }
}

// ═══════════════════════════════════════════
// Conditional Test Execution
// ═══════════════════════════════════════════

public class ConditionalTests {
    @Test
    @EnabledOnOs(OS.MAC)
    void onlyOnMac() {
        // Runs only on macOS
    }

    @Test
    @EnabledOnOs({OS.LINUX, OS.MAC})
    void onLinuxOrMac() {
        // Runs on Linux or Mac
    }

    @Test
    @DisabledOnOs(OS.WINDOWS)
    void notOnWindows() {
        // Doesn't run on Windows
    }

    @Test
    @EnabledOnJre(JRE.JAVA_17)
    void onlyOnJava17() {
        // Runs only on Java 17
    }

    @Test
    @EnabledForJreRange(min = JRE.JAVA_11, max = JRE.JAVA_17)
    void fromJava11To17() {
        // Runs on Java 11-17
    }

    @Test
    @EnabledIfSystemProperty(named = "os.arch", matches = ".*64.*")
    void only64Bit() {
        // Runs only on 64-bit systems
    }

    @Test
    @EnabledIfEnvironmentVariable(named = "ENV", matches = "prod")
    void onlyInProduction() {
        // Runs only if ENV=prod
    }

    @Test
    @EnabledIf("customCondition")
    void conditionalTest() {
        // Runs if customCondition returns true
    }

    boolean customCondition() {
        return true;
    }
}

// ═══════════════════════════════════════════
// Mockito - Mocking Framework
// ═══════════════════════════════════════════

public class MockitoExamples {
    @Mock
    private UserRepository userRepository;

    @Mock
    private EmailService emailService;

    @InjectMocks
    private UserService userService;

    @BeforeEach
    void setup() {
        MockitoAnnotations.openMocks(this);
    }

    @Test
    void testGetUser() {
        // Arrange
        User mockUser = new User("Alice", 25, "alice@example.com");
        when(userRepository.findById("123")).thenReturn(mockUser);

        // Act
        User result = userService.getUser("123");

        // Assert
        assertEquals("Alice", result.getName());
        verify(userRepository, times(1)).findById("123");
    }

    @Test
    void testSaveUser() {
        User user = new User("Bob", 30, "bob@example.com");

        // Act
        userService.saveUser(user);

        // Assert
        verify(userRepository).save(user);
        verify(emailService).sendWelcomeEmail("bob@example.com");
    }

    @Test
    void testException() {
        // Arrange
        when(userRepository.findById("invalid"))
            .thenThrow(new UserNotFoundException("User not found"));

        // Act & Assert
        assertThrows(UserNotFoundException.class, () -> {
            userService.getUser("invalid");
        });
    }

    @Test
    void testMultipleReturns() {
        // First call returns Alice, second returns Bob
        when(userRepository.findById("123"))
            .thenReturn(new User("Alice", 25, "alice@example.com"))
            .thenReturn(new User("Bob", 30, "bob@example.com"));

        User first = userService.getUser("123");
        User second = userService.getUser("123");

        assertEquals("Alice", first.getName());
        assertEquals("Bob", second.getName());
    }

    @Test
    void testArgumentMatchers() {
        // Any string
        when(userRepository.findById(anyString()))
            .thenReturn(new User("Default", 0, "default@example.com"));

        // Specific value
        when(userRepository.findById(eq("123")))
            .thenReturn(new User("Alice", 25, "alice@example.com"));

        // Custom matcher
        when(userRepository.findById(argThat(id -> id.startsWith("admin"))))
            .thenReturn(new User("Admin", 0, "admin@example.com"));
    }

    @Test
    void testVerification() {
        User user = new User("Charlie", 35, "charlie@example.com");

        userService.saveUser(user);

        // Verify method was called
        verify(userRepository).save(user);

        // Verify with times
        verify(userRepository, times(1)).save(user);
        verify(userRepository, atLeastOnce()).save(user);
        verify(userRepository, atMost(5)).save(user);
        verify(userRepository, never()).delete(user);

        // Verify no more interactions
        verifyNoMoreInteractions(userRepository);

        // Verify no interactions at all
        verifyNoInteractions(emailService);
    }

    @Test
    void testSpying() {
        // Spy on real object
        List<String> list = new ArrayList<>();
        List<String> spyList = spy(list);

        // Use real method
        spyList.add("one");
        assertEquals(1, spyList.size());

        // Stub specific method
        when(spyList.size()).thenReturn(100);
        assertEquals(100, spyList.size());

        // Verify
        verify(spyList).add("one");
    }
}

// ═══════════════════════════════════════════
// Test Coverage
// ═══════════════════════════════════════════

/*
Add to pom.xml (Maven):

<plugin>
    <groupId>org.jacoco</groupId>
    <artifactId>jacoco-maven-plugin</artifactId>
    <version>0.8.10</version>
    <executions>
        <execution>
            <goals>
                <goal>prepare-agent</goal>
            </goals>
        </execution>
        <execution>
            <id>report</id>
            <phase>test</phase>
            <goals>
                <goal>report</goal>
            </goals>
        </execution>
    </executions>
</plugin>

Run: mvn clean test
View: target/site/jacoco/index.html
*/
```

> **💡 Pro Tip:** Write tests as you code (TDD). Aim for 80%+ coverage. Use mocks for external dependencies. Test behavior, not implementation!

---

<div align="center">

## 🎁 Modern Java Features

</div>

### Java 8 to Java 21+ 🚀

```java
// ═══════════════════════════════════════════
// Java 8 Features
// ═══════════════════════════════════════════

// Lambda expressions
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
names.forEach(name -> System.out.println(name));

// Stream API
long count = names.stream()
    .filter(name -> name.length() > 4)
    .count();

// Method references
names.forEach(System.out::println);

// Optional
Optional<String> optional = Optional.of("Hello");
optional.ifPresent(System.out::println);
String value = optional.orElse("Default");

// Default methods in interfaces
interface MyInterface {
    default void defaultMethod() {
        System.out.println("Default implementation");
    }
}

// Date/Time API
LocalDate date = LocalDate.now();
LocalTime time = LocalTime.now();
LocalDateTime dateTime = LocalDateTime.now();
ZonedDateTime zonedDateTime = ZonedDateTime.now();

// ═══════════════════════════════════════════
// Java 9 Features
// ═══════════════════════════════════════════

// Module system (module-info.java)
/*
module com.example.myapp {
    requires java.sql;
    exports com.example.myapp;
}
*/

// Collection factory methods
List<String> list = List.of("a", "b", "c");
Set<String> set = Set.of("x", "y", "z");
Map<String, Integer> map = Map.of("a", 1, "b", 2);

// Stream improvements
Stream.iterate(0, i -> i < 10, i -> i + 1)
    .forEach(System.out::println);

Stream.ofNullable(null);  // Empty stream if null

// Private methods in interfaces
interface MyInterface {
    default void publicMethod() {
        privateHelper();
    }

    private void privateHelper() {
        System.out.println("Private method");
    }
}

// ═══════════════════════════════════════════
// Java 10 Features
// ═══════════════════════════════════════════

// Local variable type inference (var)
var message = "Hello";           // String
var number = 42;                 // int
var list = new ArrayList<String>();  // ArrayList<String>

// var with diamond operator
var map = new HashMap<String, Integer>();

// var in loops
for (var item : list) {
    System.out.println(item);
}

// ═══════════════════════════════════════════
// Java 11 Features
// ═══════════════════════════════════════════

// String methods
String str = "  Hello  ";
str.isBlank();                  // true for whitespace-only
str.strip();                    // Unicode-aware trim
str.stripLeading();
str.stripTrailing();
str.repeat(3);                  // "  Hello    Hello    Hello  "
str.lines().forEach(System.out::println);

// File methods
String content = Files.readString(Path.of("file.txt"));
Files.writeString(Path.of("file.txt"), "content");

// Collection to array
List<String> list = List.of("a", "b", "c");
String[] array = list.toArray(String[]::new);

// Predicate.not()
list.stream()
    .filter(Predicate.not(String::isBlank))
    .forEach(System.out::println);

// ═══════════════════════════════════════════
// Java 12-13 Features
// ═══════════════════════════════════════════

// Switch expressions (Java 12 preview, 14 standard)
String result = switch (day) {
    case MONDAY, FRIDAY, SUNDAY -> "6";
    case TUESDAY -> "7";
    default -> "0";
};

// Switch with yield
int numLetters = switch (day) {
    case MONDAY, FRIDAY, SUNDAY -> {
        System.out.println("6 letters");
        yield 6;
    }
    case TUESDAY -> {
        System.out.println("7 letters");
        yield 7;
    }
    default -> 0;
};

// Text blocks (Java 13 preview, 15 standard)
String json = """
    {
        "name": "MrDib",
        "age": 25,
        "city": "Tokyo"
    }
    """;

String html = """
    <html>
        <body>
            <h1>Hello, World!</h1>
        </body>
    </html>
    """;

// ═══════════════════════════════════════════
// Java 14-15 Features
// ═══════════════════════════════════════════

// Records (Java 14 preview, 16 standard)
record Point(int x, int y) {}

Point p = new Point(10, 20);
int x = p.x();
int y = p.y();
System.out.println(p);  // Point[x=10, y=20]

// Pattern matching for instanceof (Java 14 preview, 16 standard)
if (obj instanceof String s) {
    System.out.println(s.toUpperCase());
}

// Traditional way
if (obj instanceof String) {
    String s = (String) obj;
    System.out.println(s.toUpperCase());
}

// Helpful NullPointerExceptions
// Shows which variable was null in the stack trace

// ═══════════════════════════════════════════
// Java 17 Features (LTS)
// ═══════════════════════════════════════════

// Sealed classes
public sealed class Shape
    permits Circle, Rectangle, Triangle {}

public final class Circle extends Shape {}
public final class Rectangle extends Shape {}
public non-sealed class Triangle extends Shape {}

// Pattern matching for switch (preview)
String formatted = switch (obj) {
    case Integer i -> String.format("int %d", i);
    case Long l -> String.format("long %d", l);
    case Double d -> String.format("double %f", d);
    case String s -> String.format("String %s", s);
    default -> obj.toString();
};

// ═══════════════════════════════════════════
// Java 21 Features (LTS)
// ═══════════════════════════════════════════

// Pattern matching for switch (standard)
static String formatterPatternSwitch(Object obj) {
    return switch (obj) {
        case Integer i -> "int: " + i;
        case String s when s.length() > 5 -> "long string: " + s;
        case String s -> "short string: " + s;
        case null -> "null value";
        default -> obj.toString();
    };
}

// Record patterns
record Point(int x, int y) {}

static void printPoint(Object obj) {
    if (obj instanceof Point(int x, int y)) {
        System.out.println("x = " + x + ", y = " + y);
    }
}

// Virtual Threads (Project Loom)
try (var executor = Executors.newVirtualThreadPerTaskExecutor()) {
    for (int i = 0; i < 10_000; i++) {
        executor.submit(() -> {
            Thread.sleep(Duration.ofSeconds(1));
            return i;
        });
    }
}

// Virtual thread creation
Thread.startVirtualThread(() -> {
    System.out.println("Virtual thread");
});

Thread vThread = Thread.ofVirtual().start(() -> {
    System.out.println("Virtual thread");
});

// Structured Concurrency (preview)
try (var scope = new StructuredTaskScope.ShutdownOnFailure()) {
    Future<String> user = scope.fork(() -> fetchUser());
    Future<Integer> order = scope.fork(() -> fetchOrder());

    scope.join();
    scope.throwIfFailed();

    // Use results
    String userResult = user.resultNow();
    Integer orderResult = order.resultNow();
}

// Sequenced Collections
// New interfaces: SequencedCollection, SequencedSet, SequencedMap

List<String> list = new ArrayList<>();
list.addFirst("first");
list.addLast("last");
String first = list.getFirst();
String last = list.getLast();
List<String> reversed = list.reversed();

// String templates (preview)
String name = "MrDib";
int age = 25;
String message = STR."Hello, \{name}! You are \{age} years old.";
```

> **💡 Pro Tip:** Java 17 and 21 are LTS (Long-Term Support) versions. Virtual threads in Java 21 are game-changers for concurrent programming! Records and sealed classes improve data modeling.

---

<div align="center">

## 💡 Best Practices

</div>

### Java Best Practices & Guidelines 📋

```java
// ═══════════════════════════════════════════
// 1. Naming Conventions
// ═══════════════════════════════════════════

// Classes: PascalCase
public class UserAccount { }
public class PaymentProcessor { }

// Interfaces: PascalCase (no I prefix)
public interface Drawable { }
public interface Serializable { }

// Methods & variables: camelCase
public void calculateTotalPrice() { }
private int totalAmount;
private String userName;

// Constants: UPPER_SNAKE_CASE
public static final int MAX_USERS = 100;
public static final String API_KEY = "secret_key";
private static final double PI = 3.14159;

// Packages: lowercase, no underscores
package com.mrdib.project.service;
package com.example.app.model;

// Enums: PascalCase for enum, UPPER_CASE for values
public enum Day {
    MONDAY, TUESDAY, WEDNESDAY
}

// ═══════════════════════════════════════════
// 2. Code Organization
// ═══════════════════════════════════════════

/*
my-project/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/mrdib/project/
│   │   │       ├── model/           # Domain entities
│   │   │       ├── repository/      # Data access
│   │   │       ├── service/         # Business logic
│   │   │       ├── controller/      # API endpoints
│   │   │       ├── dto/             # Data transfer objects
│   │   │       ├── config/          # Configuration
│   │   │       ├── exception/       # Custom exceptions
│   │   │       ├── util/            # Utility classes
│   │   │       └── Application.java # Main class
│   │   └── resources/
│   │       ├── application.properties
│   │       ├── application-dev.properties
│   │       ├── application-prod.properties
│   │       ├── static/
│   │       └── templates/
│   └── test/
│       └── java/
│           └── com/mrdib/project/
│               ├── service/
│               │   └── UserServiceTest.java
│               └── repository/
│                   └── UserRepositoryTest.java
├── pom.xml or build.gradle
├── README.md
├── .gitignore
└── docker-compose.yml
*/

// ═══════════════════════════════════════════
// 3. Best Practices
// ═══════════════════════════════════════════

// ✅ Use meaningful names
List<User> activeUsers = findActiveUsers();
int userCount = users.size();

// ❌ Avoid
List<User> list = getList();
int n = users.size();

// ✅ Keep methods small (one responsibility)
public void processOrder(Order order) {
    validateOrder(order);
    calculateTotal(order);
    saveOrder(order);
    sendConfirmation(order);
}

// ❌ Avoid long methods
public void processOrder(Order order) {
    // 200 lines of code...
}

// ✅ Use Optional instead of null
public Optional<User> findUser(String id) {
    User user = database.findUser(id);
    return Optional.ofNullable(user);
}

// ❌ Returning null
public User findUser(String id) {
    return null;  // NullPointerException waiting to happen
}

// ✅ Use try-with-resources
try (BufferedReader reader = new BufferedReader(new FileReader("file.txt"))) {
    String line = reader.readLine();
}

// ❌ Manual resource management
BufferedReader reader = new BufferedReader(new FileReader("file.txt"));
try {
    String line = reader.readLine();
} finally {
    reader.close();
}

// ✅ Use StringBuilder for concatenation in loops
StringBuilder sb = new StringBuilder();
for (int i = 0; i < 1000; i++) {
    sb.append(i);
}
String result = sb.toString();

// ❌ String concatenation in loop
String result = "";
for (int i = 0; i < 1000; i++) {
    result += i;  // Creates new String object each time
}

// ✅ Use Collections factory methods (immutable)
List<String> list = List.of("a", "b", "c");
Set<Integer> set = Set.of(1, 2, 3);
Map<String, Integer> map = Map.of("a", 1, "b", 2);

// ✅ Prefer composition over inheritance
public class Car {
    private Engine engine;  // Composition

    public void start() {
        engine.start();
    }
}

// ❌ Avoid deep inheritance hierarchies
public class SportsCar extends Car extends Vehicle extends Machine { }

// ✅ Use interfaces for contracts
public interface PaymentProcessor {
    void processPayment(Payment payment);
}

// ✅ Follow SOLID principles
// S - Single Responsibility
// O - Open/Closed
// L - Liskov Substitution
// I - Interface Segregation
// D - Dependency Inversion

// ✅ Use Streams for collection operations
List<String> result = users.stream()
    .filter(user -> user.isActive())
    .map(User::getName)
    .sorted()
    .collect(Collectors.toList());

// ✅ Handle exceptions appropriately
public void processFile(String filename) throws FileNotFoundException {
    // Specific exception
}

// ❌ Catching generic exceptions
try {
    riskyOperation();
} catch (Exception e) {
    // Too broad
}

// ✅ Close resources properly
try (Connection conn = getConnection()) {
    // Use connection
}

// ✅ Use @Override annotation
@Override
public String toString() {
    return "MyClass";
}

// ✅ Validate method parameters
public void setAge(int age) {
    if (age < 0 || age > 150) {
        throw new IllegalArgumentException("Invalid age: " + age);
    }
    this.age = age;
}

// ✅ Use Objects utility class
Objects.requireNonNull(user, "User cannot be null");
Objects.equals(obj1, obj2);
Objects.hash(field1, field2, field3);

// ═══════════════════════════════════════════
// 4. Performance Tips
// ═══════════════════════════════════════════

// ✅ Use ArrayList for most cases
List<String> list = new ArrayList<>();

// ✅ Initialize with capacity if size known
List<String> list = new ArrayList<>(1000);

// ✅ Use HashMap for key-value pairs
Map<String, Integer> map = new HashMap<>();

// ✅ Use EnumSet for enum collections
EnumSet<Day> weekend = EnumSet.of(Day.SATURDAY, Day.SUNDAY);

// ✅ Use primitive streams for better performance
int sum = IntStream.range(1, 1000000).sum();

// ✅ Use parallel streams for large datasets (carefully!)
long count = largeList.parallelStream()
    .filter(predicate)
    .count();

// ✅ Cache expensive computations
private final Map<String, Result> cache = new ConcurrentHashMap<>();

public Result getResult(String key) {
    return cache.computeIfAbsent(key, this::expensiveComputation);
}

// ═══════════════════════════════════════════
// 5. Documentation
// ═══════════════════════════════════════════

/**
 * Calculates the total price including tax.
 *
 * @param price the base price
 * @param taxRate the tax rate (0.0 to 1.0)
 * @return the total price with tax applied
 * @throws IllegalArgumentException if price is negative or taxRate is invalid
 */
public double calculateTotal(double price, double taxRate) {
    if (price < 0) {
        throw new IllegalArgumentException("Price cannot be negative");
    }
    if (taxRate < 0 || taxRate > 1) {
        throw new IllegalArgumentException("Tax rate must be between 0 and 1");
    }
    return price * (1 + taxRate);
}

// ═══════════════════════════════════════════
// 6. Maven Commands
// ═══════════════════════════════════════════

/*
# Clean & compile
mvn clean compile

# Run tests
mvn test

# Package (create JAR/WAR)
mvn package

# Install to local repository
mvn install

# Skip tests
mvn package -DskipTests

# Run Spring Boot app
mvn spring-boot:run

# Dependency tree
mvn dependency:tree

# Update dependencies
mvn versions:update-properties

# Clean install
mvn clean install
*/

// ═══════════════════════════════════════════
// 7. Gradle Commands
// ═══════════════════════════════════════════

/*
# Build project
./gradlew build

# Run tests
./gradlew test

# Run application
./gradlew run

# Clean build
./gradlew clean build

# Skip tests
./gradlew build -x test

# List dependencies
./gradlew dependencies

# Spring Boot run
./gradlew bootRun

# Generate sources
./gradlew generateSources
*/
```

> **💡 Pro Tip:** Follow the Java Code Conventions. Use static analysis tools like SonarQube, Checkstyle, and SpotBugs. Write clean, readable code - you'll thank yourself later!

---

<div align="center">

## 🎉 Conclusion

_You've Mastered Java!_ 🏆

</div>

### What's Next? 🚀

You now have comprehensive knowledge of:

- ✅ **Fundamentals** - Syntax, data types, control flow
- ✅ **OOP** - Classes, inheritance, polymorphism, interfaces
- ✅ **Collections** - Lists, Sets, Maps, Queues
- ✅ **Streams** - Functional programming with lambdas
- ✅ **Generics** - Type-safe programming
- ✅ **I/O** - File operations, serialization
- ✅ **Exceptions** - Robust error handling
- ✅ **Concurrency** - Multithreading, ExecutorService, CompletableFuture
- ✅ **Testing** - JUnit, Mockito, test best practices
- ✅ **Modern Features** - Java 8-21 features

### Continue Your Journey 📚

```java
public class JavaMastery {
    public static void main(String[] args) {
        List<String> nextSteps = List.of(
            "Spring Boot",
            "Spring Data JPA",
            "Spring Security",
            "Microservices",
            "Docker & Kubernetes",
            "Apache Kafka",
            "RESTful APIs",
            "GraphQL",
            "Reactive Programming",
            "Cloud Deployment (AWS/Azure/GCP)"
        );

        nextSteps.forEach(step -> {
            System.out.println("✨ Learn: " + step);
        });

        System.out.println("\n🚀 Keep coding, keep learning!");
    }
}
```

### Essential Resources 🔗

**📘 Official Documentation**

- [Java Documentation](https://docs.oracle.com/en/java/)
- [Java Tutorials](https://docs.oracle.com/javase/tutorial/)
- [OpenJDK](https://openjdk.org/)
- [Java Language Specification](https://docs.oracle.com/javase/specs/)

**📗 Learning Platforms**

- [Java Visualizer](https://pythontutor.com/java.html)
- [Baeldung](https://www.baeldung.com/)
- [JournalDev](https://www.journaldev.com/)
- [Jenkov Tutorials](https://jenkov.com/tutorials/java/index.html)

**📙 Books**

- "Effective Java" by Joshua Bloch
- "Head First Java" by Kathy Sierra
- "Java Concurrency in Practice" by Brian Goetz
- "Clean Code" by Robert C. Martin

**🛠️ Essential Frameworks & Libraries**

- **Spring Boot** - Web applications
- **Spring Data JPA** - Database access
- **Spring Security** - Authentication/Authorization
- **Hibernate** - ORM
- **JUnit 5** - Testing
- **Mockito** - Mocking
- **Lombok** - Reduce boilerplate
- **Jackson** - JSON processing
- **Apache Commons** - Utilities
- **SLF4J + Logback** - Logging

**🎥 Video Resources**

- Java Brains (YouTube)
- Amigoscode (YouTube)
- Spring Boot Tutorial (YouTube)
- Java T Point

**💬 Community**

- [Stack Overflow](https://stackoverflow.com/questions/tagged/java)
- [r/java](https://reddit.com/r/java)
- [Java Discord](https://discord.gg/java)

---

<div align="center">

**Built with ☕ by MrDib, for Java developers**

_"Write once, run anywhere"_ ✨

**Now go build something amazing!** 🚀

**If you found this helpful, give it a ⭐ star!**

</div>
