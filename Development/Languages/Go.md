<div align="center">

# 🔵 Go (Golang) - Simple, Fast, Concurrent

### _Build reliable and efficient software at Google scale_ ⚡

![Go](https://img.shields.io/badge/Go-1.21+-00ADD8?style=for-the-badge&logo=go)
![Performance](https://img.shields.io/badge/Performance-Blazing%20Fast-green?style=for-the-badge)
![Concurrency](https://img.shields.io/badge/Concurrency-Built--in-orange?style=for-the-badge)

</div>

---

## 📚 Table of Contents

- [🎯 Go Fundamentals](#-go-fundamentals)
- [📊 Data Types & Structures](#-data-types--structures)
- [🔄 Control Flow](#-control-flow)
- [🔧 Functions](#-functions)
- [🏗️ Structs & Methods](#️-structs--methods)
- [🔌 Interfaces](#-interfaces)
- [⚠️ Error Handling](#️-error-handling)
- [📦 Packages & Modules](#-packages--modules)
- [🚀 Goroutines & Concurrency](#-goroutines--concurrency)
- [🌐 Web Development](#-web-development)
- [🗄️ Database Operations](#️-database-operations)
- [📂 File I/O](#-file-io)
- [🧪 Testing](#-testing)
- [🎯 Common Patterns](#-common-patterns)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 🎯 Go Fundamentals

</div>

### Getting Started with Go 🚀

```bash
# ═══════════════════════════════════════════
# Installation & Setup
# ═══════════════════════════════════════════

# Check Go version
go version

# macOS (using Homebrew)
brew install go

# Linux
wget https://go.dev/dl/go1.21.0.linux-amd64.tar.gz
sudo tar -C /usr/local -xzf go1.21.0.linux-amd64.tar.gz

# Windows
# Download from: https://go.dev/dl/

# Set up GOPATH (optional in Go 1.11+)
export GOPATH=$HOME/go
export PATH=$PATH:/usr/local/go/bin:$GOPATH/bin

# ═══════════════════════════════════════════
# Go Commands
# ═══════════════════════════════════════════

# Run Go program
go run main.go

# Build executable
go build
go build -o myapp

# Install binary to $GOPATH/bin
go install

# Format code
go fmt ./...
gofmt -w .

# Run tests
go test
go test -v ./...
go test -cover

# Get dependencies
go get github.com/pkg/errors

# Tidy modules
go mod tidy

# Initialize module
go mod init github.com/username/project

# Download dependencies
go mod download

# Verify dependencies
go mod verify

# ═══════════════════════════════════════════
# Create new project
# ═══════════════════════════════════════════

mkdir myproject
cd myproject
go mod init github.com/username/myproject

# Create main.go
touch main.go
```

---

### Hello World & Basic Syntax 📝

```go
// ═══════════════════════════════════════════
// Hello World
// ═══════════════════════════════════════════

package main

import (
    "fmt"
    "time"
)

func main() {
    fmt.Println("Hello from MrDib! 🚀")

    // Variables
    var name string = "MrDib"
    age := 25                    // Short declaration (type inferred)
    const version = "1.0.0"      // Constants (immutable)

    // Multiple declarations
    var (
        isActive bool   = true
        score    int    = 100
        pi       float64 = 3.14159
    )

    // Multiple assignment
    x, y := 10, 20
    x, y = y, x  // Swap values

    // Blank identifier (ignore values)
    result, _ := someFunction()

    fmt.Printf("Name: %s, Age: %d, Active: %v\n", name, age, isActive)
}

// ═══════════════════════════════════════════
// Comments
// ═══════════════════════════════════════════

// Single-line comment

/*
 * Multi-line comment
 * More details here
 */

// Package-level documentation comment
// Package main is the entry point of the application.
package main

// Exported function documentation
// Add returns the sum of two integers.
func Add(a, b int) int {
    return a + b
}

// ═══════════════════════════════════════════
// Visibility Rules
// ═══════════════════════════════════════════

// Exported (public) - starts with capital letter
type User struct {
    Name  string  // Exported
    email string  // Unexported (private)
}

func PublicFunction() {}   // Exported
func privateFunction() {}  // Unexported
```

> **💡 Pro Tip:** Go doesn't have public/private keywords. Instead, visibility is determined by capitalization - uppercase = exported, lowercase = unexported!

---

<div align="center">

## 📊 Data Types & Structures

</div>

### Basic Types & Collections 📦

```go
// ═══════════════════════════════════════════
// Primitive Data Types
// ═══════════════════════════════════════════

package main

import "fmt"

func dataTypes() {
    // Integers
    var i8 int8 = 127              // -128 to 127
    var i16 int16 = 32767          // -32,768 to 32,767
    var i32 int32 = 2147483647     // -2^31 to 2^31-1
    var i64 int64 = 9223372036854775807

    var u8 uint8 = 255             // 0 to 255
    var u16 uint16 = 65535
    var u32 uint32 = 4294967295
    var u64 uint64 = 18446744073709551615

    // Platform-dependent
    var i int = 42                 // int32 or int64
    var u uint = 42                // uint32 or uint64

    // Floating point
    var f32 float32 = 3.14
    var f64 float64 = 2.718281828

    // Complex numbers
    var c64 complex64 = 1 + 2i
    var c128 complex128 = 3 + 4i

    // Boolean
    var isTrue bool = true
    var isFalse bool = false

    // String (UTF-8 encoded)
    var str string = "Hello, 世界"

    // Byte (alias for uint8)
    var b byte = 'A'

    // Rune (alias for int32, represents Unicode code point)
    var r rune = '世'

    // Pointer
    var ptr *int
    x := 42
    ptr = &x
    fmt.Println(*ptr)  // Dereference: 42
}

// ═══════════════════════════════════════════
// Arrays (Fixed Size)
// ═══════════════════════════════════════════

func arrayExamples() {
    // Declare array
    var arr [5]int
    arr[0] = 1

    // Initialize array
    numbers := [5]int{1, 2, 3, 4, 5}

    // Compiler counts elements
    fruits := [...]string{"apple", "banana", "cherry"}

    // Initialize specific indices
    indexed := [5]int{0: 10, 2: 20, 4: 30}

    // Array length
    length := len(numbers)

    // Multi-dimensional arrays
    matrix := [3][3]int{
        {1, 2, 3},
        {4, 5, 6},
        {7, 8, 9},
    }

    // Iterate over array
    for i, value := range numbers {
        fmt.Printf("Index %d: %d\n", i, value)
    }

    // Iterate without index
    for _, value := range numbers {
        fmt.Println(value)
    }
}

// ═══════════════════════════════════════════
// Slices (Dynamic Arrays)
// ═══════════════════════════════════════════

func sliceExamples() {
    // Create slice
    var slice []int                    // nil slice
    slice = []int{1, 2, 3, 4, 5}      // Slice literal

    // Make slice with length and capacity
    nums := make([]int, 5)             // length: 5, capacity: 5
    nums2 := make([]int, 5, 10)        // length: 5, capacity: 10

    // Append to slice
    slice = append(slice, 6)
    slice = append(slice, 7, 8, 9)

    // Append another slice
    slice2 := []int{10, 11, 12}
    slice = append(slice, slice2...)   // Spread operator

    // Slicing
    sub := slice[1:4]                  // Elements 1-3
    sub2 := slice[:3]                  // Elements 0-2
    sub3 := slice[3:]                  // Elements 3-end
    sub4 := slice[:]                   // All elements (copy reference)

    // Length and capacity
    length := len(slice)
    capacity := cap(slice)

    // Copy slice
    dest := make([]int, len(slice))
    copy(dest, slice)

    // Delete element (no built-in delete)
    i := 2  // Index to delete
    slice = append(slice[:i], slice[i+1:]...)

    // Insert element
    i = 2  // Index to insert at
    slice = append(slice[:i], append([]int{99}, slice[i:]...)...)
}

// ═══════════════════════════════════════════
// Maps (Hash Tables)
// ═══════════════════════════════════════════

func mapExamples() {
    // Create map
    var m map[string]int               // nil map (can't add to it)
    m = make(map[string]int)           // Initialized map

    // Map literal
    scores := map[string]int{
        "Alice": 95,
        "Bob":   87,
        "Charlie": 92,
    }

    // Add/Update
    scores["David"] = 88
    scores["Alice"] = 96  // Update

    // Get value
    score := scores["Alice"]

    // Check if key exists
    if score, exists := scores["Eve"]; exists {
        fmt.Println("Eve's score:", score)
    } else {
        fmt.Println("Eve not found")
    }

    // Delete key
    delete(scores, "Bob")

    // Iterate over map (order is random!)
    for key, value := range scores {
        fmt.Printf("%s: %d\n", key, value)
    }

    // Get length
    length := len(scores)
}

// ═══════════════════════════════════════════
// Strings
// ═══════════════════════════════════════════

import (
    "strings"
    "strconv"
)

func stringExamples() {
    str := "Hello, World!"

    // Length (in bytes, not characters!)
    length := len(str)

    // Access bytes
    firstByte := str[0]  // 'H'

    // Strings are immutable
    // str[0] = 'h'  // ❌ Compilation error

    // Rune slice (for Unicode)
    runes := []rune(str)
    runes[0] = 'h'
    modified := string(runes)  // "hello, World!"

    // String operations
    upper := strings.ToUpper(str)
    lower := strings.ToLower(str)
    hasPrefix := strings.HasPrefix(str, "Hello")
    hasSuffix := strings.HasSuffix(str, "!")
    contains := strings.Contains(str, "World")

    // Replace
    replaced := strings.Replace(str, "World", "Go", 1)  // Replace 1
    replacedAll := strings.ReplaceAll(str, "o", "0")    // Replace all

    // Split and Join
    parts := strings.Split("a,b,c", ",")        // ["a", "b", "c"]
    joined := strings.Join(parts, "-")          // "a-b-c"

    // Trim
    trimmed := strings.TrimSpace("  hello  ")   // "hello"
    trimmed2 := strings.Trim("...hello...", ".") // "hello"

    // String conversion
    num := 42
    str2 := strconv.Itoa(num)                   // "42"
    num2, err := strconv.Atoi("123")            // 123, nil

    float := strconv.ParseFloat("3.14", 64)
    bool := strconv.ParseBool("true")

    // String builder (efficient concatenation)
    var builder strings.Builder
    builder.WriteString("Hello")
    builder.WriteString(", ")
    builder.WriteString("World!")
    result := builder.String()
}

// ═══════════════════════════════════════════
// Type Conversion
// ═══════════════════════════════════════════

func typeConversion() {
    // Explicit conversion required
    var i int = 42
    var f float64 = float64(i)
    var u uint = uint(i)

    // String conversion
    str := string(65)  // "A" (converts to rune)

    // Byte slice to string
    bytes := []byte{72, 101, 108, 108, 111}
    str2 := string(bytes)  // "Hello"

    // String to byte slice
    bytes2 := []byte("Hello")
}

// ═══════════════════════════════════════════
// Zero Values
// ═══════════════════════════════════════════

func zeroValues() {
    var i int           // 0
    var f float64       // 0.0
    var b bool          // false
    var s string        // ""
    var ptr *int        // nil
    var slice []int     // nil
    var m map[string]int // nil
    var ch chan int     // nil
}
```

> **💡 Pro Tip:** Use slices instead of arrays for most cases. Slices are more flexible and idiomatic in Go. Remember: maps iteration order is random!

---

<div align="center">

## 🔄 Control Flow

</div>

### Conditionals & Loops 🔀

```go
// ═══════════════════════════════════════════
// If/Else Statements
// ═══════════════════════════════════════════

func conditionals() {
    score := 85

    // Basic if-else
    if score >= 90 {
        fmt.Println("Grade: A")
    } else if score >= 80 {
        fmt.Println("Grade: B")
    } else if score >= 70 {
        fmt.Println("Grade: C")
    } else {
        fmt.Println("Grade: F")
    }

    // Short statement in if
    if err := doSomething(); err != nil {
        log.Fatal(err)
    }

    // Variable scoped to if block
    if num := compute(); num < 0 {
        fmt.Println("Negative")
    } else if num < 10 {
        fmt.Println("Small")
    } else {
        fmt.Println("Large")
    }
    // num is not accessible here
}

// ═══════════════════════════════════════════
// For Loops (Only Loop in Go!)
// ═══════════════════════════════════════════

func loops() {
    // Traditional for loop
    for i := 0; i < 5; i++ {
        fmt.Println(i)
    }

    // While-style loop
    counter := 0
    for counter < 5 {
        fmt.Println(counter)
        counter++
    }

    // Infinite loop
    for {
        // Break or return to exit
        if condition {
            break
        }
    }

    // Range over slice
    fruits := []string{"apple", "banana", "cherry"}
    for index, fruit := range fruits {
        fmt.Printf("%d: %s\n", index, fruit)
    }

    // Ignore index
    for _, fruit := range fruits {
        fmt.Println(fruit)
    }

    // Only index
    for index := range fruits {
        fmt.Println(index)
    }

    // Range over map
    scores := map[string]int{"Alice": 95, "Bob": 87}
    for name, score := range scores {
        fmt.Printf("%s: %d\n", name, score)
    }

    // Range over string (iterates over runes)
    for index, char := range "Hello, 世界" {
        fmt.Printf("%d: %c\n", index, char)
    }

    // Range over channel
    ch := make(chan int, 3)
    ch <- 1
    ch <- 2
    ch <- 3
    close(ch)

    for value := range ch {
        fmt.Println(value)
    }

    // Break and continue
    for i := 0; i < 10; i++ {
        if i == 3 {
            continue  // Skip 3
        }
        if i == 8 {
            break  // Stop at 8
        }
        fmt.Println(i)
    }

    // Labels (for breaking nested loops)
outer:
    for i := 0; i < 3; i++ {
        for j := 0; j < 3; j++ {
            if i == 1 && j == 1 {
                break outer  // Break outer loop
            }
            fmt.Printf("(%d, %d)\n", i, j)
        }
    }
}

// ═══════════════════════════════════════════
// Switch Statements
// ═══════════════════════════════════════════

func switchStatements() {
    day := time.Now().Weekday()

    // Basic switch
    switch day {
    case time.Saturday, time.Sunday:
        fmt.Println("Weekend!")
    case time.Friday:
        fmt.Println("TGIF!")
    default:
        fmt.Println("Weekday")
    }

    // Switch without condition (replaces if-else chain)
    hour := time.Now().Hour()
    switch {
    case hour < 12:
        fmt.Println("Good morning!")
    case hour < 17:
        fmt.Println("Good afternoon!")
    default:
        fmt.Println("Good evening!")
    }

    // Switch with short statement
    switch os := runtime.GOOS; os {
    case "darwin":
        fmt.Println("macOS")
    case "linux":
        fmt.Println("Linux")
    case "windows":
        fmt.Println("Windows")
    default:
        fmt.Println("Unknown OS")
    }

    // Type switch
    var i interface{} = "hello"

    switch v := i.(type) {
    case int:
        fmt.Printf("Integer: %d\n", v)
    case string:
        fmt.Printf("String: %s\n", v)
    case bool:
        fmt.Printf("Boolean: %v\n", v)
    default:
        fmt.Printf("Unknown type: %T\n", v)
    }

    // Fallthrough (rarely used)
    switch num := 2; num {
    case 1:
        fmt.Println("One")
    case 2:
        fmt.Println("Two")
        fallthrough  // Continue to next case
    case 3:
        fmt.Println("Three")
    }
}
```

> **💡 Pro Tip:** Go's `for` is the only loop - no while, no do-while. The switch statement doesn't need break (no fall-through by default)!

---

<div align="center">

## 🔧 Functions

</div>

### Function Declarations & Features 📦

```go
// ═══════════════════════════════════════════
// Basic Functions
// ═══════════════════════════════════════════

// Simple function
func greet(name string) {
    fmt.Printf("Hello, %s!\n", name)
}

// Function with return value
func add(a, b int) int {
    return a + b
}

// Multiple parameters of same type
func multiply(a, b, c int) int {
    return a * b * c
}

// Multiple return values
func divide(a, b float64) (float64, error) {
    if b == 0 {
        return 0, errors.New("division by zero")
    }
    return a / b, nil
}

// Named return values
func getCoordinates() (x, y int) {
    x = 10
    y = 20
    return  // Naked return (returns x and y)
}

// Named returns with explicit return
func compute() (result int, err error) {
    result = 42
    err = nil
    return result, err
}

// ═══════════════════════════════════════════
// Variadic Functions
// ═══════════════════════════════════════════

// Variable number of arguments
func sum(numbers ...int) int {
    total := 0
    for _, num := range numbers {
        total += num
    }
    return total
}

// Usage
total1 := sum(1, 2, 3)
total2 := sum(1, 2, 3, 4, 5)

// Spread slice into variadic
nums := []int{1, 2, 3, 4, 5}
total3 := sum(nums...)

// Mixed parameters (variadic must be last)
func printf(format string, args ...interface{}) {
    fmt.Printf(format, args...)
}

// ═══════════════════════════════════════════
// Functions as Values
// ═══════════════════════════════════════════

func functionValues() {
    // Assign function to variable
    add := func(a, b int) int {
        return a + b
    }

    result := add(3, 4)  // 7

    // Function as parameter
    apply := func(fn func(int, int) int, a, b int) int {
        return fn(a, b)
    }

    result2 := apply(add, 5, 6)  // 11

    // Function as return value
    multiplier := func(factor int) func(int) int {
        return func(x int) int {
            return x * factor
        }
    }

    double := multiplier(2)
    triple := multiplier(3)

    fmt.Println(double(5))  // 10
    fmt.Println(triple(5))  // 15
}

// ═══════════════════════════════════════════
// Closures
// ═══════════════════════════════════════════

// Function that returns a closure
func counter() func() int {
    count := 0
    return func() int {
        count++
        return count
    }
}

// Usage
func closureExample() {
    c1 := counter()
    fmt.Println(c1())  // 1
    fmt.Println(c1())  // 2
    fmt.Println(c1())  // 3

    c2 := counter()
    fmt.Println(c2())  // 1 (separate closure)
}

// Closure with state
func fibonacci() func() int {
    a, b := 0, 1
    return func() int {
        a, b = b, a+b
        return a
    }
}

// ═══════════════════════════════════════════
// Defer
// ═══════════════════════════════════════════

func deferExamples() {
    // Defer executes after function returns
    defer fmt.Println("World")
    fmt.Println("Hello")
    // Output: Hello\nWorld

    // Multiple defers (LIFO order)
    defer fmt.Println("1")
    defer fmt.Println("2")
    defer fmt.Println("3")
    // Output: 3\n2\n1

    // Common use: Cleanup
    file, err := os.Open("file.txt")
    if err != nil {
        log.Fatal(err)
    }
    defer file.Close()  // Ensures file is closed

    // Process file...
}

// Defer with closure
func deferClosure() {
    x := 1
    defer func() {
        fmt.Println(x)  // Captures x by reference
    }()
    x = 2
    // Output: 2
}

// Defer with parameters (captured immediately)
func deferParams() {
    x := 1
    defer fmt.Println(x)  // x captured immediately as 1
    x = 2
    // Output: 1
}

// ═══════════════════════════════════════════
// Panic and Recover
// ═══════════════════════════════════════════

func recoverExample() {
    defer func() {
        if r := recover(); r != nil {
            fmt.Println("Recovered from panic:", r)
        }
    }()

    fmt.Println("About to panic")
    panic("something went wrong!")
    fmt.Println("This won't execute")
}

// Practical panic/recover
func safeFunction() (err error) {
    defer func() {
        if r := recover(); r != nil {
            err = fmt.Errorf("panic: %v", r)
        }
    }()

    // Risky code that might panic
    riskyOperation()

    return nil
}

// ═══════════════════════════════════════════
// Init Function
// ═══════════════════════════════════════════

// Runs automatically before main()
func init() {
    fmt.Println("Initializing...")
    // Setup code, configurations, etc.
}

// Multiple init functions (run in order)
func init() {
    fmt.Println("Second init")
}

// ═══════════════════════════════════════════
// Methods vs Functions
// ═══════════════════════════════════════════

type Rectangle struct {
    Width, Height float64
}

// Method (has receiver)
func (r Rectangle) Area() float64 {
    return r.Width * r.Height
}

// Function (no receiver)
func CalculateArea(width, height float64) float64 {
    return width * height
}
```

> **💡 Pro Tip:** Use defer for cleanup operations (closing files, unlocking mutexes). Defer statements are executed in LIFO order. Panic/recover is for exceptional cases, not regular error handling!

---

<div align="center">

## 🏗️ Structs & Methods

</div>

### Defining Structs 📦

```go
// ═══════════════════════════════════════════
// Basic Struct Definition
// ═══════════════════════════════════════════

// Simple struct
type Person struct {
    Name string
    Age  int
}

// Creating instances
person1 := Person{Name: "MrDib", Age: 25}
person2 := Person{"Alice", 30}  // Must match field order

// Partial initialization (unspecified fields get zero values)
person3 := Person{Name: "Bob"}  // Age = 0

// Pointer to struct
person4 := &Person{Name: "Charlie", Age: 35}

// Anonymous struct (one-time use)
config := struct {
    Host string
    Port int
}{
    Host: "localhost",
    Port: 8080,
}

// ═══════════════════════════════════════════
// Nested Structs
// ═══════════════════════════════════════════

type Address struct {
    Street  string
    City    string
    ZipCode string
}

type Employee struct {
    Name    string
    Age     int
    Address Address  // Nested struct
    Salary  float64
}

// Usage
emp := Employee{
    Name: "MrDib",
    Age:  25,
    Address: Address{
        Street:  "123 Tech Street",
        City:    "Tokyo",
        ZipCode: "100-0001",
    },
    Salary: 75000,
}

// Access nested fields
fmt.Println(emp.Address.City)  // "Tokyo"

// ═══════════════════════════════════════════
// Embedded Structs (Composition)
// ═══════════════════════════════════════════

type Animal struct {
    Name   string
    Age    int
}

func (a Animal) Speak() string {
    return "Some sound"
}

// Dog embeds Animal (inheritance-like behavior)
type Dog struct {
    Animal      // Embedded (anonymous field)
    Breed string
}

// Usage
dog := Dog{
    Animal: Animal{Name: "Buddy", Age: 3},
    Breed:  "Golden Retriever",
}

// Can access embedded fields directly
fmt.Println(dog.Name)   // "Buddy" (promoted field)
fmt.Println(dog.Age)    // 3
dog.Speak()             // Inherited method

// ═══════════════════════════════════════════
// Struct Tags (Metadata)
// ═══════════════════════════════════════════

type User struct {
    ID        int    `json:"id" db:"user_id"`
    Username  string `json:"username" validate:"required,min=3,max=30"`
    Email     string `json:"email" validate:"required,email"`
    Password  string `json:"-" db:"password_hash"`  // "-" = ignore in JSON
    CreatedAt string `json:"created_at,omitempty"`  // omit if empty
}

// Tags are used by encoding/decoding libraries
import "encoding/json"

user := User{ID: 1, Username: "mrdib", Email: "mrdib@example.com"}
jsonData, _ := json.Marshal(user)
// {"id":1,"username":"mrdib","email":"mrdib@example.com"}

// ═══════════════════════════════════════════
// Comparing Structs
// ═══════════════════════════════════════════

type Point struct {
    X, Y int
}

p1 := Point{1, 2}
p2 := Point{1, 2}
p3 := Point{2, 3}

fmt.Println(p1 == p2)  // true
fmt.Println(p1 == p3)  // false

// Note: Structs containing slices, maps, or functions cannot be compared!
```

---

### Methods (Functions with Receivers) 🎯

```go
// ═══════════════════════════════════════════
// Value Receiver Methods
// ═══════════════════════════════════════════

type Rectangle struct {
    Width, Height float64
}

// Value receiver (works on a copy)
func (r Rectangle) Area() float64 {
    return r.Width * r.Height
}

func (r Rectangle) Perimeter() float64 {
    return 2 * (r.Width + r.Height)
}

// Usage
rect := Rectangle{Width: 10, Height: 5}
fmt.Println(rect.Area())       // 50
fmt.Println(rect.Perimeter())  // 30

// ═══════════════════════════════════════════
// Pointer Receiver Methods (Can Modify)
// ═══════════════════════════════════════════

type Counter struct {
    Count int
}

// Pointer receiver (can modify the original)
func (c *Counter) Increment() {
    c.Count++
}

func (c *Counter) Decrement() {
    c.Count--
}

func (c *Counter) Reset() {
    c.Count = 0
}

// Usage
counter := &Counter{Count: 0}
counter.Increment()
counter.Increment()
fmt.Println(counter.Count)  // 2

// Go automatically handles pointer/value conversion
counter2 := Counter{Count: 5}
counter2.Increment()  // Go automatically converts to (&counter2).Increment()

// ═══════════════════════════════════════════
// When to Use Pointer vs Value Receiver?
// ═══════════════════════════════════════════

/*
Use POINTER receiver when:
✅ Method needs to modify the receiver
✅ Struct is large (avoid copying)
✅ For consistency (if some methods use pointers, all should)

Use VALUE receiver when:
✅ Struct is small
✅ Method doesn't need to modify
✅ Receiver is immutable (like time.Time)
*/

// ═══════════════════════════════════════════
// Constructor Pattern (Go doesn't have constructors)
// ═══════════════════════════════════════════

type User struct {
    ID       int
    Username string
    Email    string
}

// Constructor function (convention: NewTypeName)
func NewUser(username, email string) *User {
    return &User{
        ID:       generateID(),
        Username: username,
        Email:    email,
    }
}

// Constructor with validation
func NewValidatedUser(username, email string) (*User, error) {
    if username == "" {
        return nil, errors.New("username cannot be empty")
    }
    if !isValidEmail(email) {
        return nil, errors.New("invalid email")
    }
    return &User{
        ID:       generateID(),
        Username: username,
        Email:    email,
    }, nil
}

// Usage
user1 := NewUser("mrdib", "mrdib@example.com")
user2, err := NewValidatedUser("alice", "alice@example.com")

// ═══════════════════════════════════════════
// Method Chaining
// ═══════════════════════════════════════════

type Builder struct {
    data string
}

func (b *Builder) Add(s string) *Builder {
    b.data += s
    return b  // Return self for chaining
}

func (b *Builder) AddSpace() *Builder {
    b.data += " "
    return b
}

func (b *Builder) Build() string {
    return b.data
}

// Usage (fluent interface)
result := (&Builder{}).
    Add("Hello").
    AddSpace().
    Add("World").
    Build()
// "Hello World"

// ═══════════════════════════════════════════
// Getters and Setters (Go convention)
// ═══════════════════════════════════════════

type Account struct {
    balance float64  // Unexported (private)
}

// Getter (no "Get" prefix in Go convention)
func (a *Account) Balance() float64 {
    return a.balance
}

// Setter (with validation)
func (a *Account) SetBalance(amount float64) error {
    if amount < 0 {
        return errors.New("balance cannot be negative")
    }
    a.balance = amount
    return nil
}

// Better: Use methods for operations
func (a *Account) Deposit(amount float64) error {
    if amount <= 0 {
        return errors.New("deposit amount must be positive")
    }
    a.balance += amount
    return nil
}

func (a *Account) Withdraw(amount float64) error {
    if amount <= 0 {
        return errors.New("withdrawal amount must be positive")
    }
    if amount > a.balance {
        return errors.New("insufficient funds")
    }
    a.balance -= amount
    return nil
}
```

> **💡 Pro Tip:** In Go, use pointer receivers for methods that modify the struct or when the struct is large. For small, immutable structs, value receivers are fine!

---

<div align="center">

## 🔌 Interfaces

</div>

### Understanding Interfaces 🎭

```go
// ═══════════════════════════════════════════
// Basic Interface Definition
// ═══════════════════════════════════════════

// Interface defines behavior (method signatures)
type Writer interface {
    Write([]byte) (int, error)
}

type Reader interface {
    Read([]byte) (int, error)
}

// Combining interfaces
type ReadWriter interface {
    Reader
    Writer
}

// Empty interface (accepts any type)
type Any interface{}  // Or: any (Go 1.18+)

// ═══════════════════════════════════════════
// Implementing Interfaces (Implicit)
// ═══════════════════════════════════════════

// No explicit "implements" keyword!
// A type implements an interface by implementing its methods

type Shape interface {
    Area() float64
    Perimeter() float64
}

// Rectangle implements Shape (implicitly)
type Rectangle struct {
    Width, Height float64
}

func (r Rectangle) Area() float64 {
    return r.Width * r.Height
}

func (r Rectangle) Perimeter() float64 {
    return 2 * (r.Width + r.Height)
}

// Circle implements Shape (implicitly)
type Circle struct {
    Radius float64
}

func (c Circle) Area() float64 {
    return 3.14159 * c.Radius * c.Radius
}

func (c Circle) Perimeter() float64 {
    return 2 * 3.14159 * c.Radius
}

// Function accepting interface
func PrintShapeInfo(s Shape) {
    fmt.Printf("Area: %.2f\n", s.Area())
    fmt.Printf("Perimeter: %.2f\n", s.Perimeter())
}

// Usage
rect := Rectangle{Width: 10, Height: 5}
circle := Circle{Radius: 7}

PrintShapeInfo(rect)    // Works!
PrintShapeInfo(circle)  // Works!

// ═══════════════════════════════════════════
// Common Standard Library Interfaces
// ═══════════════════════════════════════════

// io.Reader - read data
type Reader interface {
    Read(p []byte) (n int, err error)
}

// io.Writer - write data
type Writer interface {
    Write(p []byte) (n int, err error)
}

// fmt.Stringer - custom string representation
type Stringer interface {
    String() string
}

// Example: Implementing Stringer
type Person struct {
    Name string
    Age  int
}

func (p Person) String() string {
    return fmt.Sprintf("%s (%d years old)", p.Name, p.Age)
}

person := Person{Name: "MrDib", Age: 25}
fmt.Println(person)  // "MrDib (25 years old)"

// error interface
type error interface {
    Error() string
}

// sort.Interface - for sorting
type Interface interface {
    Len() int
    Less(i, j int) bool
    Swap(i, j int)
}

// ═══════════════════════════════════════════
// Type Assertion
// ═══════════════════════════════════════════

var i interface{} = "hello"

// Type assertion (unsafe - panics if wrong type)
s := i.(string)
fmt.Println(s)  // "hello"

// Safe type assertion
s, ok := i.(string)
if ok {
    fmt.Println(s)  // "hello"
} else {
    fmt.Println("Not a string")
}

// Type assertion with different type
n, ok := i.(int)
if ok {
    fmt.Println(n)
} else {
    fmt.Println("Not an int")  // This will print
}

// ═══════════════════════════════════════════
// Type Switch
// ═══════════════════════════════════════════

func describe(i interface{}) {
    switch v := i.(type) {
    case int:
        fmt.Printf("Integer: %d\n", v)
    case string:
        fmt.Printf("String: %s\n", v)
    case bool:
        fmt.Printf("Boolean: %v\n", v)
    case []int:
        fmt.Printf("Integer slice: %v\n", v)
    case Person:
        fmt.Printf("Person: %s\n", v.Name)
    default:
        fmt.Printf("Unknown type: %T\n", v)
    }
}

// Usage
describe(42)           // "Integer: 42"
describe("hello")      // "String: hello"
describe(true)         // "Boolean: true"
describe([]int{1, 2})  // "Integer slice: [1 2]"

// ═══════════════════════════════════════════
// Interface Best Practices
// ═══════════════════════════════════════════

// ✅ Keep interfaces small (1-3 methods)
type Saver interface {
    Save() error
}

type Loader interface {
    Load() error
}

// ❌ Don't create large interfaces
type DataManager interface {
    Create() error
    Read() error
    Update() error
    Delete() error
    Validate() error
    Transform() error
    Export() error
    Import() error
}  // Too many methods!

// ✅ Accept interfaces, return concrete types
func ProcessData(r io.Reader) (*Result, error) {
    // r is interface (flexible input)
    // *Result is concrete (clear output)
    return &Result{}, nil
}

// ✅ Define interfaces where they're used (consumer side)
// Don't define interfaces in the same package as the type

// ═══════════════════════════════════════════
// Real-World Example: Database Interface
// ═══════════════════════════════════════════

type Database interface {
    Connect() error
    Close() error
    Query(sql string) ([]Row, error)
    Execute(sql string) error
}

// PostgreSQL implementation
type PostgresDB struct {
    connectionString string
}

func (db *PostgresDB) Connect() error {
    // Connect to PostgreSQL
    return nil
}

func (db *PostgresDB) Close() error {
    // Close connection
    return nil
}

func (db *PostgresDB) Query(sql string) ([]Row, error) {
    // Execute query
    return nil, nil
}

func (db *PostgresDB) Execute(sql string) error {
    // Execute command
    return nil
}

// MySQL implementation
type MySQLDB struct {
    host string
    port int
}

func (db *MySQLDB) Connect() error {
    // Connect to MySQL
    return nil
}

func (db *MySQLDB) Close() error {
    // Close connection
    return nil
}

func (db *MySQLDB) Query(sql string) ([]Row, error) {
    // Execute query
    return nil, nil
}

func (db *MySQLDB) Execute(sql string) error {
    // Execute command
    return nil
}

// Service using the interface
type UserService struct {
    db Database  // Can be any database!
}

func (s *UserService) GetUsers() ([]User, error) {
    rows, err := s.db.Query("SELECT * FROM users")
    if err != nil {
        return nil, err
    }
    // Process rows...
    return nil, nil
}

// Usage
pgDB := &PostgresDB{connectionString: "postgres://..."}
userService1 := &UserService{db: pgDB}

myDB := &MySQLDB{host: "localhost", port: 3306}
userService2 := &UserService{db: myDB}
```

> **💡 Pro Tip:** "Accept interfaces, return structs" is a Go mantra. Keep interfaces small and focused. If it has more than 3 methods, consider breaking it down!

---

<div align="center">

## ⚠️ Error Handling

</div>

### Go's Error Philosophy 🛡️

```go
// ═══════════════════════════════════════════
// The error Interface
// ═══════════════════════════════════════════

type error interface {
    Error() string
}

// Creating errors
import "errors"

// Simple error
err := errors.New("something went wrong")

// Formatted error
import "fmt"
err := fmt.Errorf("failed to process user %d", userID)

// ═══════════════════════════════════════════
// Basic Error Handling Pattern
// ═══════════════════════════════════════════

func divide(a, b float64) (float64, error) {
    if b == 0 {
        return 0, errors.New("division by zero")
    }
    return a / b, nil
}

// Usage
result, err := divide(10, 2)
if err != nil {
    log.Fatal(err)
    return
}
fmt.Println(result)

// ═══════════════════════════════════════════
// Custom Error Types
// ═══════════════════════════════════════════

// Simple custom error
type ValidationError struct {
    Field   string
    Message string
}

func (e *ValidationError) Error() string {
    return fmt.Sprintf("validation error: %s - %s", e.Field, e.Message)
}

// Usage
func validateAge(age int) error {
    if age < 0 {
        return &ValidationError{
            Field:   "age",
            Message: "must be non-negative",
        }
    }
    return nil
}

// Advanced custom error with context
type DatabaseError struct {
    Query     string
    Err       error
    Timestamp time.Time
}

func (e *DatabaseError) Error() string {
    return fmt.Sprintf("database error at %s: %v (query: %s)",
        e.Timestamp.Format(time.RFC3339),
        e.Err,
        e.Query,
    )
}

func (e *DatabaseError) Unwrap() error {
    return e.Err  // For error wrapping support
}

// ═══════════════════════════════════════════
// Error Wrapping (Go 1.13+)
// ═══════════════════════════════════════════

import "fmt"

func readConfig(filename string) error {
    _, err := os.Open(filename)
    if err != nil {
        // Wrap error with context
        return fmt.Errorf("failed to read config: %w", err)
    }
    return nil
}

func initialize() error {
    err := readConfig("config.yml")
    if err != nil {
        return fmt.Errorf("initialization failed: %w", err)
    }
    return nil
}

// Check wrapped errors
err := initialize()
if err != nil {
    // Check if specific error is in chain
    if errors.Is(err, os.ErrNotExist) {
        fmt.Println("Config file not found")
    }
}

// ═══════════════════════════════════════════
// errors.Is and errors.As (Go 1.13+)
// ═══════════════════════════════════════════

// errors.Is - check error type
var ErrNotFound = errors.New("not found")

func GetUser(id int) (*User, error) {
    // ...
    return nil, fmt.Errorf("user lookup failed: %w", ErrNotFound)
}

// Usage
_, err := GetUser(123)
if errors.Is(err, ErrNotFound) {
    fmt.Println("User not found!")
}

// errors.As - extract error type
var valErr *ValidationError
if errors.As(err, &valErr) {
    fmt.Printf("Validation failed for field: %s\n", valErr.Field)
}

// ═══════════════════════════════════════════
// Sentinel Errors (Pre-defined errors)
// ═══════════════════════════════════════════

var (
    ErrNotFound     = errors.New("resource not found")
    ErrUnauthorized = errors.New("unauthorized access")
    ErrInvalidInput = errors.New("invalid input")
    ErrTimeout      = errors.New("operation timed out")
)

func GetResource(id string) (*Resource, error) {
    if id == "" {
        return nil, ErrInvalidInput
    }
    // ...
    return nil, ErrNotFound
}

// Usage
resource, err := GetResource("123")
if err == ErrNotFound {
    // Handle not found
}

// ═══════════════════════════════════════════
// Multiple Return Values Pattern
// ═══════════════════════════════════════════

// Typical pattern
func LoadUser(id int) (*User, error) {
    // Return result + error
    return &User{}, nil
}

// Boolean result + error
func UserExists(id int) (bool, error) {
    // Return boolean + error
    return true, nil
}

// Multiple values + error
func GetUserStats(id int) (posts, followers, following int, err error) {
    return 100, 50, 75, nil
}

// ═══════════════════════════════════════════
// Defer for Cleanup (Guarantee execution)
// ═══════════════════════════════════════════

func processFile(filename string) error {
    file, err := os.Open(filename)
    if err != nil {
        return fmt.Errorf("open file: %w", err)
    }
    defer file.Close()  // Always executed

    // Process file...
    // Even if error occurs, file.Close() is called

    return nil
}

// Multiple defers (LIFO order)
func multipleDefers() {
    defer fmt.Println("Third")   // Executes third
    defer fmt.Println("Second")  // Executes second
    defer fmt.Println("First")   // Executes first
}

// ═══════════════════════════════════════════
// Panic and Recover (Emergency Only!)
// ═══════════════════════════════════════════

// Panic - for unrecoverable errors
func mustConnect(url string) *Connection {
    conn, err := connect(url)
    if err != nil {
        panic(fmt.Sprintf("failed to connect: %v", err))
    }
    return conn
}

// Recover - catch panics
func safeExecute(fn func()) (err error) {
    defer func() {
        if r := recover(); r != nil {
            err = fmt.Errorf("panic occurred: %v", r)
        }
    }()

    fn()  // Execute potentially panicking function
    return nil
}

// Usage
err := safeExecute(func() {
    // Code that might panic
    panic("something went wrong!")
})

if err != nil {
    fmt.Println(err)  // "panic occurred: something went wrong!"
}

// ═══════════════════════════════════════════
// Error Handling Best Practices
// ═══════════════════════════════════════════

// ✅ DO: Handle errors immediately
result, err := someFunction()
if err != nil {
    return fmt.Errorf("context: %w", err)
}

// ❌ DON'T: Ignore errors
result, _ := someFunction()  // Bad practice!

// ✅ DO: Provide context
if err != nil {
    return fmt.Errorf("failed to load user %d: %w", userID, err)
}

// ❌ DON'T: Just return the error
if err != nil {
    return err  // No context!
}

// ✅ DO: Check specific errors
if errors.Is(err, ErrNotFound) {
    // Handle specific case
}

// ✅ DO: Log or return, not both
func BadExample() error {
    err := doSomething()
    if err != nil {
        log.Println(err)  // Logging
        return err         // AND returning (redundant!)
    }
    return nil
}

// Better: Choose one
func GoodExample() error {
    err := doSomething()
    if err != nil {
        return fmt.Errorf("do something: %w", err)  // Just return
    }
    return nil
}

// ═══════════════════════════════════════════
// Real-World Example: HTTP Handler
// ═══════════════════════════════════════════

func HandleGetUser(w http.ResponseWriter, r *http.Request) {
    userID := r.URL.Query().Get("id")

    user, err := getUserFromDB(userID)
    if err != nil {
        // Check specific error types
        if errors.Is(err, ErrNotFound) {
            http.Error(w, "User not found", http.StatusNotFound)
            return
        }

        // Generic error
        log.Printf("Error fetching user: %v", err)
        http.Error(w, "Internal server error", http.StatusInternalServerError)
        return
    }

    // Success
    json.NewEncoder(w).Encode(user)
}
```

> **💡 Pro Tip:** Go doesn't have try-catch. Embrace explicit error handling! It makes your code more reliable. Panic/recover is for truly exceptional cases only!

---

<div align="center">

## 📦 Packages & Modules

</div>

### Package Basics 📚

```go
// ═══════════════════════════════════════════
// Package Declaration
// ═══════════════════════════════════════════

// Every Go file starts with a package declaration
package main  // Executable package

package mypackage  // Library package

// Package name should match directory name (convention)

// ═══════════════════════════════════════════
// Importing Packages
// ═══════════════════════════════════════════

import "fmt"  // Single import

// Multiple imports (preferred)
import (
    "fmt"
    "math"
    "strings"
)

// Import with alias
import (
    f "fmt"
    m "math"
)

// Usage
f.Println("Hello")
m.Sqrt(16)

// Blank import (for side effects only)
import _ "github.com/lib/pq"  // Executes init() but doesn't use

// Dot import (discouraged - imports into current namespace)
import . "fmt"
Println("No prefix needed")  // Bad practice!

// ═══════════════════════════════════════════
// Package Visibility
// ═══════════════════════════════════════════

// Exported (public) - starts with UPPERCASE
type User struct {
    ID   int     // Exported
    Name string  // Exported
}

func PublicFunction() {}  // Exported

const MaxSize = 100  // Exported

// Unexported (private) - starts with lowercase
type internal struct {
    data string  // Unexported
}

func privateFunction() {}  // Unexported

const minSize = 10  // Unexported

// ═══════════════════════════════════════════
// Package Organization
// ═══════════════════════════════════════════

/*
Project Structure:

myapp/
├── go.mod
├── go.sum
├── main.go
├── models/
│   ├── user.go
│   └── product.go
├── handlers/
│   ├── user_handler.go
│   └── product_handler.go
├── database/
│   └── db.go
└── utils/
    └── helpers.go

Each directory is a package!
*/

// ═══════════════════════════════════════════
// Internal Packages (Go 1.4+)
// ═══════════════════════════════════════════

/*
Special "internal" directory restricts imports

myapp/
├── internal/          # Can only be imported by myapp
│   └── auth/
│       └── auth.go
└── utils/
    └── helpers.go

github.com/other/project CANNOT import myapp/internal/auth
*/

// ═══════════════════════════════════════════
// init() Function
// ═══════════════════════════════════════════

// Runs automatically before main()
// Can have multiple init() in same package
// Useful for initialization

package database

import "database/sql"

var DB *sql.DB

func init() {
    // Initialize database connection
    var err error
    DB, err = sql.Open("postgres", "connection_string")
    if err != nil {
        panic(err)
    }

    // Run migrations
    runMigrations()
}

// Execution order:
// 1. Import packages
// 2. Initialize package-level variables
// 3. Call init() functions
// 4. Call main() (if main package)
```

---

### Go Modules (Dependency Management) 📦

```bash
# ═══════════════════════════════════════════
# Initializing a Module
# ═══════════════════════════════════════════

# Create new module
go mod init github.com/username/project

# Creates go.mod file
# module github.com/username/project
#
# go 1.21

# ═══════════════════════════════════════════
# Managing Dependencies
# ═══════════════════════════════════════════

# Add dependency (latest version)
go get github.com/gin-gonic/gin

# Add specific version
go get github.com/gin-gonic/gin@v1.9.0

# Add specific commit
go get github.com/gin-gonic/gin@abc123

# Remove unused dependencies
go mod tidy

# Download dependencies
go mod download

# Verify dependencies
go mod verify

# Show dependency graph
go mod graph

# Explain why a package is needed
go mod why github.com/some/package

# ═══════════════════════════════════════════
# Upgrading Dependencies
# ═══════════════════════════════════════════

# Upgrade to latest minor version
go get -u github.com/gin-gonic/gin

# Upgrade to latest patch version
go get -u=patch github.com/gin-gonic/gin

# Upgrade all dependencies
go get -u ./...

# View available updates
go list -u -m all

# ═══════════════════════════════════════════
# Vendor Directory (Optional)
# ═══════════════════════════════════════════

# Copy dependencies to vendor/
go mod vendor

# Build using vendor
go build -mod=vendor

# ═══════════════════════════════════════════
# Replace Directive (Local Development)
# ═══════════════════════════════════════════

# In go.mod
replace github.com/user/package => ../local/package

# Or use local fork
replace github.com/user/package => github.com/myuser/package v1.2.3

# ═══════════════════════════════════════════
# Private Repositories
# ═══════════════════════════════════════════

# Set GOPRIVATE for private repos
export GOPRIVATE=github.com/mycompany/*

# Or in go env
go env -w GOPRIVATE=github.com/mycompany/*

# ═══════════════════════════════════════════
# Common go.mod File
# ═══════════════════════════════════════════

module github.com/mrdib/myapp

go 1.21

require (
    github.com/gin-gonic/gin v1.9.1
    github.com/lib/pq v1.10.9
    golang.org/x/crypto v0.14.0
)

require (
    // Indirect dependencies
    github.com/gin-contrib/sse v0.1.0 // indirect
    github.com/go-playground/validator/v10 v10.15.5 // indirect
)
```

---

<div align="center">

## 🚀 Goroutines & Concurrency

### _Go's superpower for concurrent programming_ ⚡

</div>

### Goroutines - Lightweight Threads 🧵

```go
// ═══════════════════════════════════════════
// Basic Goroutines
// ═══════════════════════════════════════════

import (
    "fmt"
    "time"
)

// Regular function call (blocking)
func regularCall() {
    doWork()         // Blocks until complete
    doMoreWork()     // Then runs this
}

// Goroutine (non-blocking)
func withGoroutine() {
    go doWork()      // Runs concurrently
    doMoreWork()     // Runs immediately (doesn't wait)
}

// Simple example
func sayHello() {
    fmt.Println("Hello from goroutine!")
}

func main() {
    go sayHello()  // Launch goroutine

    // Main must wait, or program exits before goroutine runs
    time.Sleep(time.Second)

    fmt.Println("Main function")
}

// ═══════════════════════════════════════════
// Anonymous Goroutines
// ═══════════════════════════════════════════

func main() {
    // Inline goroutine
    go func() {
        fmt.Println("Anonymous goroutine")
    }()

    // With parameters
    message := "Hello"
    go func(msg string) {
        fmt.Println(msg)
    }(message)

    time.Sleep(time.Second)
}

// ═══════════════════════════════════════════
// Multiple Goroutines
// ═══════════════════════════════════════════

func worker(id int) {
    fmt.Printf("Worker %d starting\n", id)
    time.Sleep(time.Second)
    fmt.Printf("Worker %d done\n", id)
}

func main() {
    // Launch 5 workers concurrently
    for i := 1; i <= 5; i++ {
        go worker(i)
    }

    // Wait for all to complete
    time.Sleep(2 * time.Second)
}

// Output (order may vary):
// Worker 1 starting
// Worker 3 starting
// Worker 2 starting
// Worker 5 starting
// Worker 4 starting
// Worker 1 done
// Worker 2 done
// Worker 3 done
// Worker 4 done
// Worker 5 done
```

---

### Channels - Communication Between Goroutines 📡

```go
// ═══════════════════════════════════════════
// Creating Channels
// ═══════════════════════════════════════════

// Unbuffered channel
ch := make(chan int)

// Buffered channel (capacity 5)
ch := make(chan int, 5)

// Channel types
var intChan chan int            // Bidirectional
var sendChan chan<- int         // Send-only
var recvChan <-chan int         // Receive-only

// ═══════════════════════════════════════════
// Sending and Receiving
// ═══════════════════════════════════════════

ch := make(chan string)

// Send to channel (blocks until receiver ready)
ch <- "Hello"

// Receive from channel (blocks until sender ready)
message := <-ch

// Receive and discard value
<-ch

// ═══════════════════════════════════════════
// Basic Channel Example
// ═══════════════════════════════════════════

func main() {
    ch := make(chan string)

    // Sender goroutine
    go func() {
        ch <- "Hello from goroutine!"
    }()

    // Receiver (main goroutine)
    msg := <-ch
    fmt.Println(msg)
}

// ═══════════════════════════════════════════
// Buffered Channels
// ═══════════════════════════════════════════

func main() {
    // Buffered channel (capacity 3)
    ch := make(chan int, 3)

    // Can send 3 values without blocking
    ch <- 1
    ch <- 2
    ch <- 3

    // 4th send would block (if no receiver)
    // ch <- 4  // Deadlock!

    // Receive values
    fmt.Println(<-ch)  // 1
    fmt.Println(<-ch)  // 2
    fmt.Println(<-ch)  // 3
}

// ═══════════════════════════════════════════
// Closing Channels
// ═══════════════════════════════════════════

ch := make(chan int)

// Close channel (sender's responsibility)
close(ch)

// Check if channel is closed
value, ok := <-ch
if ok {
    fmt.Println("Received:", value)
} else {
    fmt.Println("Channel closed")
}

// Range over channel (receives until closed)
ch := make(chan int, 5)

// Send values
go func() {
    for i := 0; i < 5; i++ {
        ch <- i
    }
    close(ch)  // Must close to end range loop
}()

// Receive all values
for value := range ch {
    fmt.Println(value)
}

// ═══════════════════════════════════════════
// Select Statement (Multiplexing)
// ═══════════════════════════════════════════

// Listen on multiple channels
ch1 := make(chan string)
ch2 := make(chan string)

go func() {
    time.Sleep(1 * time.Second)
    ch1 <- "from channel 1"
}()

go func() {
    time.Sleep(2 * time.Second)
    ch2 <- "from channel 2"
}()

// Select first available
select {
case msg1 := <-ch1:
    fmt.Println(msg1)
case msg2 := <-ch2:
    fmt.Println(msg2)
}

// Select with timeout
select {
case msg := <-ch1:
    fmt.Println(msg)
case <-time.After(3 * time.Second):
    fmt.Println("Timeout!")
}

// Select with default (non-blocking)
select {
case msg := <-ch1:
    fmt.Println(msg)
default:
    fmt.Println("No message received")
}

// ═══════════════════════════════════════════
// Worker Pool Pattern
// ═══════════════════════════════════════════

func worker(id int, jobs <-chan int, results chan<- int) {
    for job := range jobs {
        fmt.Printf("Worker %d processing job %d\n", id, job)
        time.Sleep(time.Second)
        results <- job * 2
    }
}

func main() {
    const numWorkers = 3
    const numJobs = 9

    jobs := make(chan int, numJobs)
    results := make(chan int, numJobs)

    // Start workers
    for w := 1; w <= numWorkers; w++ {
        go worker(w, jobs, results)
    }

    // Send jobs
    for j := 1; j <= numJobs; j++ {
        jobs <- j
    }
    close(jobs)

    // Collect results
    for a := 1; a <= numJobs; a++ {
        result := <-results
        fmt.Println("Result:", result)
    }
}

// ═══════════════════════════════════════════
// Fan-Out, Fan-In Pattern
// ═══════════════════════════════════════════

// Fan-out: distribute work to multiple goroutines
func producer(n int) <-chan int {
    out := make(chan int)
    go func() {
        for i := 0; i < n; i++ {
            out <- i
        }
        close(out)
    }()
    return out
}

// Multiple workers process concurrently
func worker(in <-chan int) <-chan int {
    out := make(chan int)
    go func() {
        for num := range in {
            out <- num * 2  // Process
        }
        close(out)
    }()
    return out
}

// Fan-in: combine results from multiple channels
func merge(channels ...<-chan int) <-chan int {
    out := make(chan int)

    for _, ch := range channels {
        go func(c <-chan int) {
            for val := range c {
                out <- val
            }
        }(ch)
    }

    return out
}

// ═══════════════════════════════════════════
// Pipeline Pattern
// ═══════════════════════════════════════════

// Stage 1: Generate numbers
func generate(nums ...int) <-chan int {
    out := make(chan int)
    go func() {
        for _, n := range nums {
            out <- n
        }
        close(out)
    }()
    return out
}

// Stage 2: Square numbers
func square(in <-chan int) <-chan int {
    out := make(chan int)
    go func() {
        for n := range in {
            out <- n * n
        }
        close(out)
    }()
    return out
}

// Stage 3: Sum numbers
func sum(in <-chan int) int {
    sum := 0
    for n := range in {
        sum += n
    }
    return sum
}

// Use pipeline
func main() {
    // Pipeline: generate -> square -> sum
    numbers := generate(1, 2, 3, 4, 5)
    squared := square(numbers)
    result := sum(squared)
    fmt.Println(result)  // 55
}
```

---

### Synchronization Primitives 🔒

```go
// ═══════════════════════════════════════════
// WaitGroup - Wait for Goroutines to Finish
// ═══════════════════════════════════════════

import "sync"

func worker(id int, wg *sync.WaitGroup) {
    defer wg.Done()  // Decrement counter when done

    fmt.Printf("Worker %d starting\n", id)
    time.Sleep(time.Second)
    fmt.Printf("Worker %d done\n", id)
}

func main() {
    var wg sync.WaitGroup

    for i := 1; i <= 5; i++ {
        wg.Add(1)  // Increment counter
        go worker(i, &wg)
    }

    wg.Wait()  // Block until counter is 0
    fmt.Println("All workers done")
}

// ═══════════════════════════════════════════
// Mutex - Mutual Exclusion
// ═══════════════════════════════════════════

type Counter struct {
    mu    sync.Mutex
    value int
}

func (c *Counter) Increment() {
    c.mu.Lock()
    c.value++
    c.mu.Unlock()
}

func (c *Counter) Value() int {
    c.mu.Lock()
    defer c.mu.Unlock()
    return c.value
}

// Usage
func main() {
    counter := &Counter{}
    var wg sync.WaitGroup

    // 1000 goroutines incrementing
    for i := 0; i < 1000; i++ {
        wg.Add(1)
        go func() {
            defer wg.Done()
            counter.Increment()
        }()
    }

    wg.Wait()
    fmt.Println("Final count:", counter.Value())  // 1000 (safe!)
}

// ═══════════════════════════════════════════
// RWMutex - Read/Write Mutex
// ═══════════════════════════════════════════

type SafeMap struct {
    mu   sync.RWMutex
    data map[string]int
}

func (sm *SafeMap) Read(key string) int {
    sm.mu.RLock()  // Multiple readers OK
    defer sm.mu.RUnlock()
    return sm.data[key]
}

func (sm *SafeMap) Write(key string, value int) {
    sm.mu.Lock()  // Exclusive write access
    defer sm.mu.Unlock()
    sm.data[key] = value
}

// ═══════════════════════════════════════════
// Once - Execute Only Once
// ═══════════════════════════════════════════

var (
    instance *Singleton
    once     sync.Once
)

type Singleton struct {
    data string
}

func GetInstance() *Singleton {
    once.Do(func() {
        fmt.Println("Creating singleton instance")
        instance = &Singleton{data: "singleton"}
    })
    return instance
}

// ═══════════════════════════════════════════
// Context - Cancellation and Timeouts
// ═══════════════════════════════════════════

import "context"

// With timeout
func main() {
    ctx, cancel := context.WithTimeout(context.Background(), 2*time.Second)
    defer cancel()

    go doWork(ctx)

    time.Sleep(3 * time.Second)
}

func doWork(ctx context.Context) {
    for {
        select {
        case <-ctx.Done():
            fmt.Println("Work cancelled:", ctx.Err())
            return
        default:
            fmt.Println("Working...")
            time.Sleep(500 * time.Millisecond)
        }
    }
}

// Manual cancellation
ctx, cancel := context.WithCancel(context.Background())

go func() {
    time.Sleep(2 * time.Second)
    cancel()  // Trigger cancellation
}()

// With deadline
deadline := time.Now().Add(5 * time.Second)
ctx, cancel := context.WithDeadline(context.Background(), deadline)
defer cancel()

// With values (pass request-scoped data)
ctx := context.WithValue(context.Background(), "userID", 123)

// Retrieve value
if userID, ok := ctx.Value("userID").(int); ok {
    fmt.Println("User ID:", userID)
}

// ═══════════════════════════════════════════
// Atomic Operations
// ═══════════════════════════════════════════

import "sync/atomic"

var counter int64

func increment() {
    atomic.AddInt64(&counter, 1)
}

func getCounter() int64 {
    return atomic.LoadInt64(&counter)
}

// More atomic operations
atomic.StoreInt64(&counter, 42)
atomic.CompareAndSwapInt64(&counter, 42, 100)
```

> **💡 Pro Tip:** Use channels for communication, mutexes for protecting shared state. "Don't communicate by sharing memory; share memory by communicating" is Go's mantra!

---

<div align="center">

## 🌐 Web Development

</div>

### Standard Library HTTP Server 🌍

```go
// ═══════════════════════════════════════════
// Basic HTTP Server
// ═══════════════════════════════════════════

import (
    "fmt"
    "net/http"
)

func main() {
    // Simple handler
    http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
        fmt.Fprintf(w, "Hello, World!")
    })

    // Start server
    fmt.Println("Server starting on :8080")
    http.ListenAndServe(":8080", nil)
}

// ═══════════════════════════════════════════
// Multiple Routes
// ═══════════════════════════════════════════

func homeHandler(w http.ResponseWriter, r *http.Request) {
    fmt.Fprintf(w, "Welcome to the home page!")
}

func aboutHandler(w http.ResponseWriter, r *http.Request) {
    fmt.Fprintf(w, "About page")
}

func main() {
    http.HandleFunc("/", homeHandler)
    http.HandleFunc("/about", aboutHandler)

    http.ListenAndServe(":8080", nil)
}

// ═══════════════════════════════════════════
// JSON API
// ═══════════════════════════════════════════

import "encoding/json"

type User struct {
    ID    int    `json:"id"`
    Name  string `json:"name"`
    Email string `json:"email"`
}

func getUsersHandler(w http.ResponseWriter, r *http.Request) {
    users := []User{
        {ID: 1, Name: "MrDib", Email: "mrdib@example.com"},
        {ID: 2, Name: "Alice", Email: "alice@example.com"},
    }

    w.Header().Set("Content-Type", "application/json")
    json.NewEncoder(w).Encode(users)
}

func createUserHandler(w http.ResponseWriter, r *http.Request) {
    if r.Method != http.MethodPost {
        http.Error(w, "Method not allowed", http.StatusMethodNotAllowed)
        return
    }

    var user User
    err := json.NewDecoder(r.Body).Decode(&user)
    if err != nil {
        http.Error(w, err.Error(), http.StatusBadRequest)
        return
    }

    // Process user...
    user.ID = 123  // Assign ID

    w.Header().Set("Content-Type", "application/json")
    w.WriteStatus(http.StatusCreated)
    json.NewEncoder(w).Encode(user)
}

// ═══════════════════════════════════════════
// Custom Router
// ═══════════════════════════════════════════

type Router struct {
    routes map[string]http.HandlerFunc
}

func NewRouter() *Router {
    return &Router{
        routes: make(map[string]http.HandlerFunc),
    }
}

func (rt *Router) HandleFunc(pattern string, handler http.HandlerFunc) {
    rt.routes[pattern] = handler
}

func (rt *Router) ServeHTTP(w http.ResponseWriter, r *http.Request) {
    if handler, ok := rt.routes[r.URL.Path]; ok {
        handler(w, r)
    } else {
        http.NotFound(w, r)
    }
}

// ═══════════════════════════════════════════
// Middleware Pattern
// ═══════════════════════════════════════════

// Logging middleware
func loggingMiddleware(next http.Handler) http.Handler {
    return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        fmt.Printf("%s %s\n", r.Method, r.URL.Path)
        next.ServeHTTP(w, r)
    })
}

// Auth middleware
func authMiddleware(next http.Handler) http.Handler {
    return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        token := r.Header.Get("Authorization")
        if token == "" {
            http.Error(w, "Unauthorized", http.StatusUnauthorized)
            return
        }
        next.ServeHTTP(w, r)
    })
}

// Usage
func main() {
    mux := http.NewServeMux()
    mux.HandleFunc("/", homeHandler)

    // Wrap with middleware
    handler := loggingMiddleware(authMiddleware(mux))

    http.ListenAndServe(":8080", handler)
}
```

---

### Gin Framework - Fast & Elegant 🍸

```go
// ═══════════════════════════════════════════
// Installation
// ═══════════════════════════════════════════

// go get -u github.com/gin-gonic/gin

// ═══════════════════════════════════════════
// Basic Gin Server
// ═══════════════════════════════════════════

import "github.com/gin-gonic/gin"

func main() {
    // Create router
    r := gin.Default()  // With logger & recovery middleware

    // Routes
    r.GET("/", func(c *gin.Context) {
        c.JSON(200, gin.H{
            "message": "Hello, World!",
        })
    })

    // Start server
    r.Run(":8080")
}

// ═══════════════════════════════════════════
// RESTful API
// ═══════════════════════════════════════════

type User struct {
    ID    int    `json:"id"`
    Name  string `json:"name" binding:"required"`
    Email string `json:"email" binding:"required,email"`
}

func main() {
    r := gin.Default()

    // GET all users
    r.GET("/users", func(c *gin.Context) {
        users := []User{
            {ID: 1, Name: "MrDib", Email: "mrdib@example.com"},
            {ID: 2, Name: "Alice", Email: "alice@example.com"},
        }
        c.JSON(200, users)
    })

    // GET single user
    r.GET("/users/:id", func(c *gin.Context) {
        id := c.Param("id")
        // Fetch user...
        c.JSON(200, gin.H{"id": id})
    })

    // POST create user
    r.POST("/users", func(c *gin.Context) {
        var user User
        if err := c.ShouldBindJSON(&user); err != nil {
            c.JSON(400, gin.H{"error": err.Error()})
            return
        }

        // Save user...
        user.ID = 123
        c.JSON(201, user)
    })

    // PUT update user
    r.PUT("/users/:id", func(c *gin.Context) {
        id := c.Param("id")
        var user User
        if err := c.ShouldBindJSON(&user); err != nil {
            c.JSON(400, gin.H{"error": err.Error()})
            return
        }

        // Update user...
        c.JSON(200, user)
    })

    // DELETE user
    r.DELETE("/users/:id", func(c *gin.Context) {
        id := c.Param("id")
        // Delete user...
        c.JSON(200, gin.H{"message": "User deleted", "id": id})
    })

    r.Run(":8080")
}

// ═══════════════════════════════════════════
// Query Parameters
// ═══════════════════════════════════════════

r.GET("/search", func(c *gin.Context) {
    query := c.Query("q")              // ?q=golang
    page := c.DefaultQuery("page", "1")  // Default if missing

    c.JSON(200, gin.H{
        "query": query,
        "page":  page,
    })
})

// ═══════════════════════════════════════════
// Route Groups & Middleware
// ═══════════════════════════════════════════

func main() {
    r := gin.Default()

    // Public routes
    r.GET("/", homeHandler)
    r.POST("/login", loginHandler)

    // Protected routes (with auth middleware)
    authorized := r.Group("/api")
    authorized.Use(authMiddleware())
    {
        authorized.GET("/profile", profileHandler)
        authorized.POST("/posts", createPostHandler)
        authorized.DELETE("/posts/:id", deletePostHandler)
    }

    r.Run(":8080")
}

// Auth middleware
func authMiddleware() gin.HandlerFunc {
    return func(c *gin.Context) {
        token := c.GetHeader("Authorization")
        if token == "" {
            c.JSON(401, gin.H{"error": "Unauthorized"})
            c.Abort()
            return
        }

        // Validate token...
        c.Set("userID", 123)  // Store in context
        c.Next()
    }
}

// ═══════════════════════════════════════════
// File Upload
// ═══════════════════════════════════════════

r.POST("/upload", func(c *gin.Context) {
    file, err := c.FormFile("file")
    if err != nil {
        c.JSON(400, gin.H{"error": err.Error()})
        return
    }

    // Save file
    dst := "./uploads/" + file.Filename
    if err := c.SaveUploadedFile(file, dst); err != nil {
        c.JSON(500, gin.H{"error": err.Error()})
        return
    }

    c.JSON(200, gin.H{"message": "File uploaded", "filename": file.Filename})
})

// ═══════════════════════════════════════════
// Serving Static Files
// ═══════════════════════════════════════════

r.Static("/static", "./static")
r.StaticFile("/favicon.ico", "./favicon.ico")
r.StaticFS("/assets", http.Dir("./assets"))

// ═══════════════════════════════════════════
// HTML Templates
// ═══════════════════════════════════════════

r.LoadHTMLGlob("templates/*")

r.GET("/", func(c *gin.Context) {
    c.HTML(200, "index.html", gin.H{
        "title": "Home Page",
        "user":  "MrDib",
    })
})

// ═══════════════════════════════════════════
// Graceful Shutdown
// ═══════════════════════════════════════════

import (
    "context"
    "net/http"
    "os"
    "os/signal"
    "syscall"
    "time"
)

func main() {
    r := gin.Default()

    r.GET("/", func(c *gin.Context) {
        c.String(200, "Hello!")
    })

    srv := &http.Server{
        Addr:    ":8080",
        Handler: r,
    }

    // Start server in goroutine
    go func() {
        if err := srv.ListenAndServe(); err != nil && err != http.ErrServerClosed {
            log.Fatalf("listen: %s\n", err)
        }
    }()

    // Wait for interrupt signal
    quit := make(chan os.Signal, 1)
    signal.Notify(quit, syscall.SIGINT, syscall.SIGTERM)
    <-quit

    fmt.Println("Shutting down server...")

    // Graceful shutdown with timeout
    ctx, cancel := context.WithTimeout(context.Background(), 5*time.Second)
    defer cancel()

    if err := srv.Shutdown(ctx); err != nil {
        log.Fatal("Server forced to shutdown:", err)
    }

    fmt.Println("Server exited")
}
```

> **💡 Pro Tip:** Gin is one of the fastest Go web frameworks. Perfect for building RESTful APIs! For simpler projects, the standard library `net/http` is also powerful enough!

---

<div align="center">

## 🗄️ Database Operations

</div>

### SQL Databases with database/sql 🐘

```go
// ═══════════════════════════════════════════
// PostgreSQL Setup
// ═══════════════════════════════════════════

// Install driver
// go get github.com/lib/pq

import (
    "database/sql"
    "fmt"
    "log"

    _ "github.com/lib/pq"  // Import for side effects
)

// Connection
func connectDB() (*sql.DB, error) {
    connStr := "postgres://user:password@localhost/dbname?sslmode=disable"
    db, err := sql.Open("postgres", connStr)
    if err != nil {
        return nil, err
    }

    // Test connection
    if err = db.Ping(); err != nil {
        return nil, err
    }

    // Connection pool settings
    db.SetMaxOpenConns(25)
    db.SetMaxIdleConns(5)
    db.SetConnMaxLifetime(5 * time.Minute)

    return db, nil
}

// ═══════════════════════════════════════════
// Creating Tables
// ═══════════════════════════════════════════

func createTables(db *sql.DB) error {
    query := `
    CREATE TABLE IF NOT EXISTS users (
        id SERIAL PRIMARY KEY,
        username VARCHAR(50) UNIQUE NOT NULL,
        email VARCHAR(100) UNIQUE NOT NULL,
        created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
    )`

    _, err := db.Exec(query)
    return err
}

// ═══════════════════════════════════════════
// INSERT Operations
// ═══════════════════════════════════════════

type User struct {
    ID        int
    Username  string
    Email     string
    CreatedAt time.Time
}

// Insert single user
func createUser(db *sql.DB, username, email string) (int, error) {
    query := `
        INSERT INTO users (username, email)
        VALUES ($1, $2)
        RETURNING id
    `

    var id int
    err := db.QueryRow(query, username, email).Scan(&id)
    if err != nil {
        return 0, err
    }

    return id, nil
}

// Insert with struct
func createUserStruct(db *sql.DB, user *User) error {
    query := `
        INSERT INTO users (username, email)
        VALUES ($1, $2)
        RETURNING id, created_at
    `

    err := db.QueryRow(query, user.Username, user.Email).
        Scan(&user.ID, &user.CreatedAt)

    return err
}

// ═══════════════════════════════════════════
// SELECT Operations
// ═══════════════════════════════════════════

// Get single user
func getUserByID(db *sql.DB, id int) (*User, error) {
    query := `
        SELECT id, username, email, created_at
        FROM users
        WHERE id = $1
    `

    user := &User{}
    err := db.QueryRow(query, id).Scan(
        &user.ID,
        &user.Username,
        &user.Email,
        &user.CreatedAt,
    )

    if err == sql.ErrNoRows {
        return nil, fmt.Errorf("user not found")
    }
    if err != nil {
        return nil, err
    }

    return user, nil
}

// Get multiple users
func getAllUsers(db *sql.DB) ([]User, error) {
    query := `
        SELECT id, username, email, created_at
        FROM users
        ORDER BY created_at DESC
    `

    rows, err := db.Query(query)
    if err != nil {
        return nil, err
    }
    defer rows.Close()

    var users []User
    for rows.Next() {
        var user User
        err := rows.Scan(
            &user.ID,
            &user.Username,
            &user.Email,
            &user.CreatedAt,
        )
        if err != nil {
            return nil, err
        }
        users = append(users, user)
    }

    // Check for errors during iteration
    if err = rows.Err(); err != nil {
        return nil, err
    }

    return users, nil
}

// With WHERE clause
func getUsersByEmail(db *sql.DB, emailPattern string) ([]User, error) {
    query := `
        SELECT id, username, email, created_at
        FROM users
        WHERE email LIKE $1
    `

    rows, err := db.Query(query, "%"+emailPattern+"%")
    if err != nil {
        return nil, err
    }
    defer rows.Close()

    var users []User
    for rows.Next() {
        var user User
        if err := rows.Scan(&user.ID, &user.Username, &user.Email, &user.CreatedAt); err != nil {
            return nil, err
        }
        users = append(users, user)
    }

    return users, rows.Err()
}

// ═══════════════════════════════════════════
// UPDATE Operations
// ═══════════════════════════════════════════

func updateUser(db *sql.DB, id int, username, email string) error {
    query := `
        UPDATE users
        SET username = $1, email = $2
        WHERE id = $3
    `

    result, err := db.Exec(query, username, email, id)
    if err != nil {
        return err
    }

    // Check rows affected
    rowsAffected, err := result.RowsAffected()
    if err != nil {
        return err
    }

    if rowsAffected == 0 {
        return fmt.Errorf("user not found")
    }

    return nil
}

// ═══════════════════════════════════════════
// DELETE Operations
// ═══════════════════════════════════════════

func deleteUser(db *sql.DB, id int) error {
    query := `DELETE FROM users WHERE id = $1`

    result, err := db.Exec(query, id)
    if err != nil {
        return err
    }

    rowsAffected, err := result.RowsAffected()
    if err != nil {
        return err
    }

    if rowsAffected == 0 {
        return fmt.Errorf("user not found")
    }

    return nil
}

// ═══════════════════════════════════════════
// Transactions
// ═══════════════════════════════════════════

func transferFunds(db *sql.DB, fromID, toID int, amount float64) error {
    // Begin transaction
    tx, err := db.Begin()
    if err != nil {
        return err
    }

    // Defer rollback (only executes if commit doesn't happen)
    defer tx.Rollback()

    // Deduct from sender
    _, err = tx.Exec(
        "UPDATE accounts SET balance = balance - $1 WHERE id = $2",
        amount, fromID,
    )
    if err != nil {
        return err
    }

    // Add to receiver
    _, err = tx.Exec(
        "UPDATE accounts SET balance = balance + $1 WHERE id = $2",
        amount, toID,
    )
    if err != nil {
        return err
    }

    // Commit transaction
    return tx.Commit()
}

// ═══════════════════════════════════════════
// Prepared Statements (Better Performance)
// ═══════════════════════════════════════════

func insertManyUsers(db *sql.DB, users []User) error {
    // Prepare statement
    stmt, err := db.Prepare("INSERT INTO users (username, email) VALUES ($1, $2)")
    if err != nil {
        return err
    }
    defer stmt.Close()

    // Execute multiple times
    for _, user := range users {
        _, err := stmt.Exec(user.Username, user.Email)
        if err != nil {
            return err
        }
    }

    return nil
}

// ═══════════════════════════════════════════
// NULL Values Handling
// ═══════════════════════════════════════════

import "database/sql"

type User struct {
    ID       int
    Username string
    Email    sql.NullString  // Can be NULL
    Age      sql.NullInt64   // Can be NULL
}

func getUserWithNulls(db *sql.DB, id int) (*User, error) {
    query := "SELECT id, username, email, age FROM users WHERE id = $1"

    user := &User{}
    err := db.QueryRow(query, id).Scan(
        &user.ID,
        &user.Username,
        &user.Email,
        &user.Age,
    )

    if err != nil {
        return nil, err
    }

    // Check NULL values
    if user.Email.Valid {
        fmt.Println("Email:", user.Email.String)
    } else {
        fmt.Println("Email is NULL")
    }

    return user, nil
}
```

---

### GORM - Go ORM Library 🎯

```go
// ═══════════════════════════════════════════
// Installation
// ═══════════════════════════════════════════

// go get -u gorm.io/gorm
// go get -u gorm.io/driver/postgres

// ═══════════════════════════════════════════
// GORM Setup
// ═══════════════════════════════════════════

import (
    "gorm.io/driver/postgres"
    "gorm.io/gorm"
)

func connectGORM() (*gorm.DB, error) {
    dsn := "host=localhost user=postgres password=secret dbname=mydb port=5432 sslmode=disable"

    db, err := gorm.Open(postgres.Open(dsn), &gorm.Config{})
    if err != nil {
        return nil, err
    }

    return db, nil
}

// ═══════════════════════════════════════════
// Defining Models
// ═══════════════════════════════════════════

type User struct {
    ID        uint      `gorm:"primaryKey"`
    Username  string    `gorm:"uniqueIndex;not null"`
    Email     string    `gorm:"uniqueIndex;not null"`
    Age       int       `gorm:"default:0"`
    Active    bool      `gorm:"default:true"`
    CreatedAt time.Time
    UpdatedAt time.Time
    DeletedAt gorm.DeletedAt `gorm:"index"`  // Soft delete
}

// Custom table name
func (User) TableName() string {
    return "users"
}

// ═══════════════════════════════════════════
// Auto Migration
// ═══════════════════════════════════════════

func migrate(db *gorm.DB) error {
    return db.AutoMigrate(&User{})
}

// ═══════════════════════════════════════════
// CRUD Operations
// ═══════════════════════════════════════════

// CREATE
func createUser(db *gorm.DB) {
    user := User{
        Username: "mrdib",
        Email:    "mrdib@example.com",
        Age:      25,
    }

    result := db.Create(&user)
    if result.Error != nil {
        log.Fatal(result.Error)
    }

    fmt.Println("User ID:", user.ID)  // Auto-populated
}

// READ
func getUsers(db *gorm.DB) {
    // Get all
    var users []User
    db.Find(&users)

    // Get first
    var user User
    db.First(&user)  // ORDER BY id LIMIT 1

    // Get by primary key
    db.First(&user, 10)  // WHERE id = 10

    // Get with condition
    db.First(&user, "email = ?", "mrdib@example.com")

    // Where clause
    db.Where("age > ?", 18).Find(&users)

    // Multiple conditions
    db.Where("username = ? AND age > ?", "mrdib", 18).Find(&users)
}

// UPDATE
func updateUser(db *gorm.DB) {
    // Update single field
    db.Model(&User{}).Where("id = ?", 1).Update("age", 26)

    // Update multiple fields
    db.Model(&User{}).Where("id = ?", 1).Updates(User{
        Username: "mrdib_updated",
        Age:      26,
    })

    // Update with map
    db.Model(&User{}).Where("id = ?", 1).Updates(map[string]interface{}{
        "username": "mrdib",
        "age":      25,
    })
}

// DELETE
func deleteUser(db *gorm.DB) {
    // Soft delete (sets DeletedAt)
    db.Delete(&User{}, 1)

    // Permanent delete
    db.Unscoped().Delete(&User{}, 1)

    // Delete with condition
    db.Where("age < ?", 18).Delete(&User{})
}

// ═══════════════════════════════════════════
// Advanced Queries
// ═══════════════════════════════════════════

// Select specific fields
var users []User
db.Select("username", "email").Find(&users)

// Order
db.Order("created_at DESC").Find(&users)

// Limit and Offset
db.Limit(10).Offset(20).Find(&users)

// Count
var count int64
db.Model(&User{}).Where("age > ?", 18).Count(&count)

// Group and Having
db.Model(&User{}).Select("age, count(*) as count").
    Group("age").
    Having("count > ?", 1).
    Find(&users)

// Joins
type Result struct {
    Username string
    PostTitle string
}

var results []Result
db.Model(&User{}).
    Select("users.username, posts.title as post_title").
    Joins("LEFT JOIN posts ON posts.user_id = users.id").
    Scan(&results)

// ═══════════════════════════════════════════
// Associations (Relationships)
// ═══════════════════════════════════════════

// One-to-Many
type User struct {
    gorm.Model
    Username string
    Posts    []Post  // Has many posts
}

type Post struct {
    gorm.Model
    Title  string
    UserID uint
    User   User  // Belongs to user
}

// Create with associations
user := User{
    Username: "mrdib",
    Posts: []Post{
        {Title: "First Post"},
        {Title: "Second Post"},
    },
}
db.Create(&user)

// Eager loading
var users []User
db.Preload("Posts").Find(&users)

// Many-to-Many
type User struct {
    gorm.Model
    Username string
    Roles    []Role `gorm:"many2many:user_roles;"`
}

type Role struct {
    gorm.Model
    Name  string
    Users []User `gorm:"many2many:user_roles;"`
}

// ═══════════════════════════════════════════
// Transactions
// ═══════════════════════════════════════════

func transfer(db *gorm.DB, fromID, toID uint, amount float64) error {
    return db.Transaction(func(tx *gorm.DB) error {
        // Deduct from sender
        if err := tx.Model(&Account{}).
            Where("id = ?", fromID).
            Update("balance", gorm.Expr("balance - ?", amount)).Error; err != nil {
            return err
        }

        // Add to receiver
        if err := tx.Model(&Account{}).
            Where("id = ?", toID).
            Update("balance", gorm.Expr("balance + ?", amount)).Error; err != nil {
            return err
        }

        return nil
    })
}

// ═══════════════════════════════════════════
// Hooks (Callbacks)
// ═══════════════════════════════════════════

type User struct {
    gorm.Model
    Username string
    Email    string
}

// Before create
func (u *User) BeforeCreate(tx *gorm.DB) error {
    // Validate or modify before saving
    if u.Username == "" {
        return errors.New("username is required")
    }
    return nil
}

// After create
func (u *User) AfterCreate(tx *gorm.DB) error {
    // Log, send notification, etc.
    fmt.Printf("User %s created\n", u.Username)
    return nil
}
```

> **💡 Pro Tip:** GORM is great for rapid development, but raw SQL with database/sql gives you more control and better performance for complex queries. Choose based on your needs!

---

<div align="center">

## 📂 File I/O

</div>

### Reading & Writing Files 📄

```go
// ═══════════════════════════════════════════
// Reading Files
// ═══════════════════════════════════════════

import (
    "fmt"
    "io"
    "io/ioutil"
    "os"
)

// Method 1: Read entire file (small files)
func readFile1(filename string) ([]byte, error) {
    data, err := ioutil.ReadFile(filename)
    if err != nil {
        return nil, err
    }
    return data, nil
}

// Method 2: Using os.ReadFile (Go 1.16+)
func readFile2(filename string) ([]byte, error) {
    return os.ReadFile(filename)
}

// Method 3: Read with os.Open
func readFile3(filename string) (string, error) {
    file, err := os.Open(filename)
    if err != nil {
        return "", err
    }
    defer file.Close()

    content, err := io.ReadAll(file)
    if err != nil {
        return "", err
    }

    return string(content), nil
}

// Method 4: Read line by line (large files)
import "bufio"

func readFileLineByLine(filename string) error {
    file, err := os.Open(filename)
    if err != nil {
        return err
    }
    defer file.Close()

    scanner := bufio.NewScanner(file)
    for scanner.Scan() {
        line := scanner.Text()
        fmt.Println(line)
    }

    return scanner.Err()
}

// Method 5: Read in chunks (very large files)
func readFileInChunks(filename string) error {
    file, err := os.Open(filename)
    if err != nil {
        return err
    }
    defer file.Close()

    buffer := make([]byte, 1024)  // 1KB chunks
    for {
        n, err := file.Read(buffer)
        if err == io.EOF {
            break
        }
        if err != nil {
            return err
        }

        // Process chunk
        fmt.Printf("Read %d bytes\n", n)
    }

    return nil
}

// ═══════════════════════════════════════════
// Writing Files
// ═══════════════════════════════════════════

// Method 1: Write entire file (overwrites)
func writeFile1(filename, content string) error {
    data := []byte(content)
    return ioutil.WriteFile(filename, data, 0644)
}

// Method 2: Using os.WriteFile (Go 1.16+)
func writeFile2(filename, content string) error {
    return os.WriteFile(filename, []byte(content), 0644)
}

// Method 3: Using os.Create
func writeFile3(filename, content string) error {
    file, err := os.Create(filename)
    if err != nil {
        return err
    }
    defer file.Close()

    _, err = file.WriteString(content)
    return err
}

// Method 4: Append to file
func appendToFile(filename, content string) error {
    file, err := os.OpenFile(filename, os.O_APPEND|os.O_WRONLY|os.O_CREATE, 0644)
    if err != nil {
        return err
    }
    defer file.Close()

    _, err = file.WriteString(content)
    return err
}

// Method 5: Buffered writing (better performance)
func writeFileBuffered(filename string, lines []string) error {
    file, err := os.Create(filename)
    if err != nil {
        return err
    }
    defer file.Close()

    writer := bufio.NewWriter(file)
    for _, line := range lines {
        _, err := writer.WriteString(line + "\n")
        if err != nil {
            return err
        }
    }

    return writer.Flush()  // Important!
}

// ═══════════════════════════════════════════
// File Information
// ═══════════════════════════════════════════

func getFileInfo(filename string) error {
    info, err := os.Stat(filename)
    if err != nil {
        if os.IsNotExist(err) {
            return fmt.Errorf("file does not exist")
        }
        return err
    }

    fmt.Println("Name:", info.Name())
    fmt.Println("Size:", info.Size(), "bytes")
    fmt.Println("Mode:", info.Mode())
    fmt.Println("Modified:", info.ModTime())
    fmt.Println("Is Directory:", info.IsDir())

    return nil
}

// Check if file exists
func fileExists(filename string) bool {
    _, err := os.Stat(filename)
    return !os.IsNotExist(err)
}

// ═══════════════════════════════════════════
// File Operations
// ═══════════════════════════════════════════

// Copy file
func copyFile(src, dst string) error {
    sourceFile, err := os.Open(src)
    if err != nil {
        return err
    }
    defer sourceFile.Close()

    destFile, err := os.Create(dst)
    if err != nil {
        return err
    }
    defer destFile.Close()

    _, err = io.Copy(destFile, sourceFile)
    return err
}

// Move/Rename file
func moveFile(oldPath, newPath string) error {
    return os.Rename(oldPath, newPath)
}

// Delete file
func deleteFile(filename string) error {
    return os.Remove(filename)
}

// Change permissions
func changePermissions(filename string) error {
    return os.Chmod(filename, 0755)
}

// ═══════════════════════════════════════════
// Directory Operations
// ═══════════════════════════════════════════

// Create directory
func createDir(path string) error {
    return os.Mkdir(path, 0755)
}

// Create nested directories
func createDirs(path string) error {
    return os.MkdirAll(path, 0755)
}

// List directory contents
func listDir(path string) ([]string, error) {
    entries, err := os.ReadDir(path)
    if err != nil {
        return nil, err
    }

    var names []string
    for _, entry := range entries {
        names = append(names, entry.Name())
    }

    return names, nil
}

// Remove directory (must be empty)
func removeDir(path string) error {
    return os.Remove(path)
}

// Remove directory and contents
func removeDirAll(path string) error {
    return os.RemoveAll(path)
}

// Walk directory tree
import "path/filepath"

func walkDir(root string) error {
    return filepath.Walk(root, func(path string, info os.FileInfo, err error) error {
        if err != nil {
            return err
        }

        fmt.Println(path)
        return nil
    })
}

// ═══════════════════════════════════════════
// Working with JSON Files
// ═══════════════════════════════════════════

type Config struct {
    Host     string `json:"host"`
    Port     int    `json:"port"`
    Database string `json:"database"`
}

// Read JSON file
func readJSONFile(filename string) (*Config, error) {
    data, err := os.ReadFile(filename)
    if err != nil {
        return nil, err
    }

    var config Config
    err = json.Unmarshal(data, &config)
    if err != nil {
        return nil, err
    }

    return &config, nil
}

// Write JSON file
func writeJSONFile(filename string, config *Config) error {
    data, err := json.MarshalIndent(config, "", "  ")
    if err != nil {
        return err
    }

    return os.WriteFile(filename, data, 0644)
}

// ═══════════════════════════════════════════
// Temporary Files
// ═══════════════════════════════════════════

import "io/ioutil"

// Create temp file
func createTempFile() (*os.File, error) {
    tmpFile, err := ioutil.TempFile("", "prefix-*.txt")
    if err != nil {
        return nil, err
    }

    fmt.Println("Temp file:", tmpFile.Name())
    return tmpFile, nil
}

// Create temp directory
func createTempDir() (string, error) {
    tmpDir, err := ioutil.TempDir("", "prefix-")
    if err != nil {
        return "", err
    }

    fmt.Println("Temp dir:", tmpDir)
    return tmpDir, nil
}

// ═══════════════════════════════════════════
// CSV File Operations
// ═══════════════════════════════════════════

import "encoding/csv"

// Read CSV
func readCSV(filename string) ([][]string, error) {
    file, err := os.Open(filename)
    if err != nil {
        return nil, err
    }
    defer file.Close()

    reader := csv.NewReader(file)
    records, err := reader.ReadAll()
    if err != nil {
        return nil, err
    }

    return records, nil
}

// Write CSV
func writeCSV(filename string, data [][]string) error {
    file, err := os.Create(filename)
    if err != nil {
        return err
    }
    defer file.Close()

    writer := csv.NewWriter(file)
    defer writer.Flush()

    return writer.WriteAll(data)
}
```

> **💡 Pro Tip:** Always use `defer file.Close()` after opening files. Don't forget to flush buffers when using buffered writers!

---

<div align="center">

## 🧪 Testing

</div>

### Unit Testing with testing Package 🔬

```go
// ═══════════════════════════════════════════
// File: math.go
// ═══════════════════════════════════════════

package math

func Add(a, b int) int {
    return a + b
}

func Subtract(a, b int) int {
    return a - b
}

func Multiply(a, b int) int {
    return a * b
}

func Divide(a, b int) (int, error) {
    if b == 0 {
        return 0, errors.New("division by zero")
    }
    return a / b, nil
}

// ═══════════════════════════════════════════
// File: math_test.go
// ═══════════════════════════════════════════

package math

import "testing"

// Basic test
func TestAdd(t *testing.T) {
    result := Add(2, 3)
    expected := 5

    if result != expected {
        t.Errorf("Add(2, 3) = %d; want %d", result, expected)
    }
}

// Multiple test cases
func TestSubtract(t *testing.T) {
    tests := []struct {
        name     string
        a, b     int
        expected int
    }{
        {"positive", 5, 3, 2},
        {"negative", 3, 5, -2},
        {"zero", 5, 5, 0},
    }

    for _, tt := range tests {
        t.Run(tt.name, func(t *testing.T) {
            result := Subtract(tt.a, tt.b)
            if result != tt.expected {
                t.Errorf("Subtract(%d, %d) = %d; want %d",
                    tt.a, tt.b, result, tt.expected)
            }
        })
    }
}

// Test with error
func TestDivide(t *testing.T) {
    // Normal case
    result, err := Divide(10, 2)
    if err != nil {
        t.Fatalf("Divide(10, 2) returned error: %v", err)
    }
    if result != 5 {
        t.Errorf("Divide(10, 2) = %d; want 5", result)
    }

    // Error case
    _, err = Divide(10, 0)
    if err == nil {
        t.Error("Divide(10, 0) should return error")
    }
}

// ═══════════════════════════════════════════
// Table-Driven Tests (Best Practice)
// ═══════════════════════════════════════════

func TestMultiply(t *testing.T) {
    testCases := []struct {
        name     string
        a        int
        b        int
        expected int
    }{
        {"positive * positive", 2, 3, 6},
        {"positive * negative", 2, -3, -6},
        {"negative * negative", -2, -3, 6},
        {"multiply by zero", 5, 0, 0},
        {"multiply by one", 5, 1, 5},
    }

    for _, tc := range testCases {
        t.Run(tc.name, func(t *testing.T) {
            result := Multiply(tc.a, tc.b)
            if result != tc.expected {
                t.Errorf("Multiply(%d, %d) = %d; want %d",
                    tc.a, tc.b, result, tc.expected)
            }
        })
    }
}

// ═══════════════════════════════════════════
// Setup and Teardown
// ═══════════════════════════════════════════

func TestMain(m *testing.M) {
    // Setup
    fmt.Println("Setting up tests...")

    // Run tests
    code := m.Run()

    // Teardown
    fmt.Println("Cleaning up...")

    os.Exit(code)
}

// ═══════════════════════════════════════════
// Benchmarks
// ═══════════════════════════════════════════

func BenchmarkAdd(b *testing.B) {
    for i := 0; i < b.N; i++ {
        Add(2, 3)
    }
}

func BenchmarkMultiply(b *testing.B) {
    for i := 0; i < b.N; i++ {
        Multiply(10, 20)
    }
}

// Run benchmarks:
// go test -bench=.
// go test -bench=. -benchmem  // With memory stats

// ═══════════════════════════════════════════
// Example Tests (Documentation)
// ═══════════════════════════════════════════

func ExampleAdd() {
    result := Add(2, 3)
    fmt.Println(result)
    // Output: 5
}

func ExampleSubtract() {
    result := Subtract(5, 3)
    fmt.Println(result)
    // Output: 2
}

// ═══════════════════════════════════════════
// Testing HTTP Handlers
// ═══════════════════════════════════════════

import (
    "net/http"
    "net/http/httptest"
)

func helloHandler(w http.ResponseWriter, r *http.Request) {
    w.WriteHeader(http.StatusOK)
    w.Write([]byte("Hello, World!"))
}

func TestHelloHandler(t *testing.T) {
    // Create request
    req, err := http.NewRequest("GET", "/hello", nil)
    if err != nil {
        t.Fatal(err)
    }

    // Create ResponseRecorder
    rr := httptest.NewRecorder()

    // Call handler
    handler := http.HandlerFunc(helloHandler)
    handler.ServeHTTP(rr, req)

    // Check status code
    if status := rr.Code; status != http.StatusOK {
        t.Errorf("handler returned wrong status code: got %v want %v",
            status, http.StatusOK)
    }

    // Check response body
    expected := "Hello, World!"
    if rr.Body.String() != expected {
        t.Errorf("handler returned unexpected body: got %v want %v",
            rr.Body.String(), expected)
    }
}

// ═══════════════════════════════════════════
// Mocking with Interfaces
// ═══════════════════════════════════════════

type Database interface {
    GetUser(id int) (*User, error)
}

type UserService struct {
    db Database
}

func (s *UserService) GetUserName(id int) (string, error) {
    user, err := s.db.GetUser(id)
    if err != nil {
        return "", err
    }
    return user.Name, nil
}

// Mock database for testing
type MockDatabase struct {
    users map[int]*User
}

func (m *MockDatabase) GetUser(id int) (*User, error) {
    user, ok := m.users[id]
    if !ok {
        return nil, errors.New("user not found")
    }
    return user, nil
}

// Test with mock
func TestUserService_GetUserName(t *testing.T) {
    mockDB := &MockDatabase{
        users: map[int]*User{
            1: {ID: 1, Name: "MrDib"},
            2: {ID: 2, Name: "Alice"},
        },
    }

    service := &UserService{db: mockDB}

    name, err := service.GetUserName(1)
    if err != nil {
        t.Fatalf("unexpected error: %v", err)
    }

    if name != "MrDib" {
        t.Errorf("got %s; want MrDib", name)
    }
}

// ═══════════════════════════════════════════
// Test Coverage
// ═══════════════════════════════════════════

/*
Run tests with coverage:

go test -cover
go test -coverprofile=coverage.out
go tool cover -html=coverage.out

This opens an HTML view showing which lines are covered!
*/
```

---

### Testing Commands

```bash
# ═══════════════════════════════════════════
# Running Tests
# ═══════════════════════════════════════════

# Run all tests
go test

# Run tests in all packages
go test ./...

# Verbose output
go test -v

# Run specific test
go test -run TestAdd

# Run tests matching pattern
go test -run Test.*Divide

# ═══════════════════════════════════════════
# Benchmarks
# ═══════════════════════════════════════════

# Run all benchmarks
go test -bench=.

# Run specific benchmark
go test -bench=BenchmarkAdd

# With memory allocation stats
go test -bench=. -benchmem

# Run for specific time
go test -bench=. -benchtime=10s

# ═══════════════════════════════════════════
# Coverage
# ═══════════════════════════════════════════

# Show coverage percentage
go test -cover

# Generate coverage profile
go test -coverprofile=coverage.out

# View coverage in browser
go tool cover -html=coverage.out

# Coverage for all packages
go test -cover ./...

# ═══════════════════════════════════════════
# Other Useful Flags
# ═══════════════════════════════════════════

# Run tests in parallel
go test -parallel 4

# Timeout after duration
go test -timeout 30s

# Short mode (skip long tests)
go test -short

# Show test caching behavior
go test -count=1  # Disable cache

# Run tests with race detector
go test -race

# Generate test binary
go test -c
```

> **💡 Pro Tip:** Write tests as you write code, not after! Aim for at least 80% code coverage. Use table-driven tests for better organization and coverage!

---

<div align="center">

## 🎯 Common Patterns

### _Idiomatic Go patterns every developer should know_ ✨

</div>

### Functional Options Pattern 🛠️

```go
// ═══════════════════════════════════════════
// Flexible Configuration with Functional Options
// ═══════════════════════════════════════════

type Server struct {
    host    string
    port    int
    timeout time.Duration
    maxConn int
}

// Option is a function that configures Server
type Option func(*Server)

// Constructor with options
func NewServer(options ...Option) *Server {
    // Default values
    server := &Server{
        host:    "localhost",
        port:    8080,
        timeout: 30 * time.Second,
        maxConn: 100,
    }

    // Apply options
    for _, option := range options {
        option(server)
    }

    return server
}

// Option functions
func WithHost(host string) Option {
    return func(s *Server) {
        s.host = host
    }
}

func WithPort(port int) Option {
    return func(s *Server) {
        s.port = port
    }
}

func WithTimeout(timeout time.Duration) Option {
    return func(s *Server) {
        s.timeout = timeout
    }
}

func WithMaxConnections(maxConn int) Option {
    return func(s *Server) {
        s.maxConn = maxConn
    }
}

// Usage
server := NewServer(
    WithHost("0.0.0.0"),
    WithPort(3000),
    WithTimeout(60 * time.Second),
    WithMaxConnections(200),
)

// Or with defaults
server := NewServer()  // Uses all defaults

// Or partial configuration
server := NewServer(WithPort(9000))
```

---

### Builder Pattern 🏗️

```go
// ═══════════════════════════════════════════
// Building Complex Objects Step by Step
// ═══════════════════════════════════════════

type Query struct {
    table      string
    columns    []string
    where      []string
    orderBy    string
    limit      int
    offset     int
}

type QueryBuilder struct {
    query *Query
}

func NewQueryBuilder() *QueryBuilder {
    return &QueryBuilder{
        query: &Query{},
    }
}

func (qb *QueryBuilder) Table(table string) *QueryBuilder {
    qb.query.table = table
    return qb
}

func (qb *QueryBuilder) Select(columns ...string) *QueryBuilder {
    qb.query.columns = columns
    return qb
}

func (qb *QueryBuilder) Where(condition string) *QueryBuilder {
    qb.query.where = append(qb.query.where, condition)
    return qb
}

func (qb *QueryBuilder) OrderBy(column string) *QueryBuilder {
    qb.query.orderBy = column
    return qb
}

func (qb *QueryBuilder) Limit(limit int) *QueryBuilder {
    qb.query.limit = limit
    return qb
}

func (qb *QueryBuilder) Offset(offset int) *QueryBuilder {
    qb.query.offset = offset
    return qb
}

func (qb *QueryBuilder) Build() string {
    // Build SQL query string
    sql := fmt.Sprintf("SELECT %s FROM %s",
        strings.Join(qb.query.columns, ", "),
        qb.query.table,
    )

    if len(qb.query.where) > 0 {
        sql += " WHERE " + strings.Join(qb.query.where, " AND ")
    }

    if qb.query.orderBy != "" {
        sql += " ORDER BY " + qb.query.orderBy
    }

    if qb.query.limit > 0 {
        sql += fmt.Sprintf(" LIMIT %d", qb.query.limit)
    }

    if qb.query.offset > 0 {
        sql += fmt.Sprintf(" OFFSET %d", qb.query.offset)
    }

    return sql
}

// Usage - Fluent interface
query := NewQueryBuilder().
    Table("users").
    Select("id", "name", "email").
    Where("age > 18").
    Where("active = true").
    OrderBy("created_at DESC").
    Limit(10).
    Offset(0).
    Build()

// Output: SELECT id, name, email FROM users WHERE age > 18 AND active = true ORDER BY created_at DESC LIMIT 10 OFFSET 0
```

---

### Singleton Pattern 🎯

```go
// ═══════════════════════════════════════════
// Thread-Safe Singleton
// ═══════════════════════════════════════════

import "sync"

type Database struct {
    connection string
}

var (
    instance *Database
    once     sync.Once
)

func GetInstance() *Database {
    once.Do(func() {
        fmt.Println("Creating database instance...")
        instance = &Database{
            connection: "connected",
        }
    })
    return instance
}

// Usage
db1 := GetInstance()  // Creates instance
db2 := GetInstance()  // Returns same instance
fmt.Println(db1 == db2)  // true

// ═══════════════════════════════════════════
// Alternative: Package-level initialization
// ═══════════════════════════════════════════

var db = &Database{
    connection: "connected",
}

func GetDB() *Database {
    return db
}
```

---

### Repository Pattern 📦

```go
// ═══════════════════════════════════════════
// Abstracting Data Access
// ═══════════════════════════════════════════

type User struct {
    ID    int
    Name  string
    Email string
}

// Repository interface
type UserRepository interface {
    Create(user *User) error
    GetByID(id int) (*User, error)
    GetAll() ([]*User, error)
    Update(user *User) error
    Delete(id int) error
}

// PostgreSQL implementation
type PostgresUserRepository struct {
    db *sql.DB
}

func NewPostgresUserRepository(db *sql.DB) *PostgresUserRepository {
    return &PostgresUserRepository{db: db}
}

func (r *PostgresUserRepository) Create(user *User) error {
    query := "INSERT INTO users (name, email) VALUES ($1, $2) RETURNING id"
    return r.db.QueryRow(query, user.Name, user.Email).Scan(&user.ID)
}

func (r *PostgresUserRepository) GetByID(id int) (*User, error) {
    user := &User{}
    query := "SELECT id, name, email FROM users WHERE id = $1"
    err := r.db.QueryRow(query, id).Scan(&user.ID, &user.Name, &user.Email)
    if err != nil {
        return nil, err
    }
    return user, nil
}

func (r *PostgresUserRepository) GetAll() ([]*User, error) {
    query := "SELECT id, name, email FROM users"
    rows, err := r.db.Query(query)
    if err != nil {
        return nil, err
    }
    defer rows.Close()

    var users []*User
    for rows.Next() {
        user := &User{}
        if err := rows.Scan(&user.ID, &user.Name, &user.Email); err != nil {
            return nil, err
        }
        users = append(users, user)
    }

    return users, rows.Err()
}

func (r *PostgresUserRepository) Update(user *User) error {
    query := "UPDATE users SET name = $1, email = $2 WHERE id = $3"
    _, err := r.db.Exec(query, user.Name, user.Email, user.ID)
    return err
}

func (r *PostgresUserRepository) Delete(id int) error {
    query := "DELETE FROM users WHERE id = $1"
    _, err := r.db.Exec(query, id)
    return err
}

// Service using repository
type UserService struct {
    repo UserRepository
}

func NewUserService(repo UserRepository) *UserService {
    return &UserService{repo: repo}
}

func (s *UserService) RegisterUser(name, email string) (*User, error) {
    // Business logic here
    user := &User{Name: name, Email: email}
    err := s.repo.Create(user)
    if err != nil {
        return nil, err
    }
    return user, nil
}

// Usage (easy to swap implementations!)
db, _ := sql.Open("postgres", "connection_string")
repo := NewPostgresUserRepository(db)
service := NewUserService(repo)

user, _ := service.RegisterUser("MrDib", "mrdib@example.com")
```

---

### Middleware Chain Pattern 🔗

```go
// ═══════════════════════════════════════════
// HTTP Middleware Chain
// ═══════════════════════════════════════════

type Middleware func(http.Handler) http.Handler

// Logging middleware
func LoggingMiddleware(next http.Handler) http.Handler {
    return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        start := time.Now()
        next.ServeHTTP(w, r)
        log.Printf("%s %s %v", r.Method, r.URL.Path, time.Since(start))
    })
}

// Auth middleware
func AuthMiddleware(next http.Handler) http.Handler {
    return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        token := r.Header.Get("Authorization")
        if token == "" {
            http.Error(w, "Unauthorized", http.StatusUnauthorized)
            return
        }
        // Validate token...
        next.ServeHTTP(w, r)
    })
}

// CORS middleware
func CORSMiddleware(next http.Handler) http.Handler {
    return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        w.Header().Set("Access-Control-Allow-Origin", "*")
        w.Header().Set("Access-Control-Allow-Methods", "GET, POST, PUT, DELETE, OPTIONS")
        w.Header().Set("Access-Control-Allow-Headers", "Content-Type, Authorization")

        if r.Method == "OPTIONS" {
            w.WriteHeader(http.StatusOK)
            return
        }

        next.ServeHTTP(w, r)
    })
}

// Rate limiting middleware
func RateLimitMiddleware(next http.Handler) http.Handler {
    limiter := rate.NewLimiter(10, 20)  // 10 requests per second, burst of 20

    return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        if !limiter.Allow() {
            http.Error(w, "Too many requests", http.StatusTooManyRequests)
            return
        }
        next.ServeHTTP(w, r)
    })
}

// Chain helper
func Chain(h http.Handler, middlewares ...Middleware) http.Handler {
    for i := len(middlewares) - 1; i >= 0; i-- {
        h = middlewares[i](h)
    }
    return h
}

// Usage
func main() {
    mux := http.NewServeMux()
    mux.HandleFunc("/", homeHandler)

    // Apply middleware chain
    handler := Chain(mux,
        LoggingMiddleware,
        CORSMiddleware,
        RateLimitMiddleware,
        AuthMiddleware,
    )

    http.ListenAndServe(":8080", handler)
}
```

---

### Object Pool Pattern 🏊

```go
// ═══════════════════════════════════════════
// Reusable Object Pool (Reduce GC Pressure)
// ═══════════════════════════════════════════

import "sync"

type Buffer struct {
    data []byte
}

var bufferPool = sync.Pool{
    New: func() interface{} {
        return &Buffer{
            data: make([]byte, 0, 1024),
        }
    },
}

func GetBuffer() *Buffer {
    return bufferPool.Get().(*Buffer)
}

func PutBuffer(buf *Buffer) {
    buf.data = buf.data[:0]  // Reset
    bufferPool.Put(buf)
}

// Usage
func processData(data []byte) {
    // Get buffer from pool
    buf := GetBuffer()
    defer PutBuffer(buf)  // Return to pool

    // Use buffer
    buf.data = append(buf.data, data...)
    // Process...
}

// ═══════════════════════════════════════════
// Database Connection Pool (Built-in)
// ═══════════════════════════════════════════

db, err := sql.Open("postgres", "connection_string")
db.SetMaxOpenConns(25)                 // Max open connections
db.SetMaxIdleConns(5)                  // Max idle connections
db.SetConnMaxLifetime(5 * time.Minute) // Max connection lifetime
```

---

### Circuit Breaker Pattern 🔌

```go
// ═══════════════════════════════════════════
// Prevent Cascading Failures
// ═══════════════════════════════════════════

type State int

const (
    StateClosed State = iota
    StateOpen
    StateHalfOpen
)

type CircuitBreaker struct {
    maxFailures  int
    timeout      time.Duration
    failures     int
    lastFailTime time.Time
    state        State
    mu           sync.Mutex
}

func NewCircuitBreaker(maxFailures int, timeout time.Duration) *CircuitBreaker {
    return &CircuitBreaker{
        maxFailures: maxFailures,
        timeout:     timeout,
        state:       StateClosed,
    }
}

func (cb *CircuitBreaker) Call(fn func() error) error {
    cb.mu.Lock()
    defer cb.mu.Unlock()

    // Check if circuit should close
    if cb.state == StateOpen {
        if time.Since(cb.lastFailTime) > cb.timeout {
            cb.state = StateHalfOpen
        } else {
            return fmt.Errorf("circuit breaker is open")
        }
    }

    // Try to execute
    err := fn()

    if err != nil {
        cb.failures++
        cb.lastFailTime = time.Now()

        if cb.failures >= cb.maxFailures {
            cb.state = StateOpen
        }

        return err
    }

    // Success - reset
    if cb.state == StateHalfOpen {
        cb.state = StateClosed
    }
    cb.failures = 0

    return nil
}

// Usage
cb := NewCircuitBreaker(3, 10*time.Second)

err := cb.Call(func() error {
    // Call external service
    return callExternalAPI()
})

if err != nil {
    log.Printf("Call failed: %v", err)
}
```

---

### Retry Pattern 🔄

```go
// ═══════════════════════════════════════════
// Automatic Retry with Exponential Backoff
// ═══════════════════════════════════════════

func Retry(attempts int, sleep time.Duration, fn func() error) error {
    for i := 0; i < attempts; i++ {
        err := fn()
        if err == nil {
            return nil
        }

        if i < attempts-1 {
            // Exponential backoff
            time.Sleep(sleep)
            sleep *= 2
        }
    }

    return fmt.Errorf("failed after %d attempts", attempts)
}

// Usage
err := Retry(5, time.Second, func() error {
    return callExternalAPI()
})

if err != nil {
    log.Printf("All retry attempts failed: %v", err)
}

// ═══════════════════════════════════════════
// Retry with Context (Cancellable)
// ═══════════════════════════════════════════

func RetryWithContext(ctx context.Context, attempts int, sleep time.Duration, fn func() error) error {
    for i := 0; i < attempts; i++ {
        select {
        case <-ctx.Done():
            return ctx.Err()
        default:
        }

        err := fn()
        if err == nil {
            return nil
        }

        if i < attempts-1 {
            select {
            case <-time.After(sleep):
                sleep *= 2
            case <-ctx.Done():
                return ctx.Err()
            }
        }
    }

    return fmt.Errorf("failed after %d attempts", attempts)
}

// Usage with timeout
ctx, cancel := context.WithTimeout(context.Background(), 30*time.Second)
defer cancel()

err := RetryWithContext(ctx, 5, time.Second, func() error {
    return callExternalAPI()
})
```

---

<div align="center">

## 💡 Best Practices

### _Write Go code like a pro_ ⭐

</div>

### Code Organization 📁

```go
// ═══════════════════════════════════════════
// Project Structure
// ═══════════════════════════════════════════

/*
myapp/
├── cmd/                    # Main applications
│   └── myapp/
│       └── main.go
├── internal/               # Private application code
│   ├── handlers/
│   ├── models/
│   ├── services/
│   └── repository/
├── pkg/                    # Public libraries
│   └── utils/
├── api/                    # API definitions (OpenAPI, protobuf)
├── web/                    # Web assets (templates, static files)
├── configs/                # Configuration files
├── scripts/                # Build and deployment scripts
├── test/                   # Additional test files
├── docs/                   # Documentation
├── go.mod
├── go.sum
├── README.md
├── Makefile
└── .gitignore
*/

// ═══════════════════════════════════════════
// Package Naming
// ═══════════════════════════════════════════

// ✅ Good package names
package user       // Short, lowercase, singular
package http       // No underscores
package strings    // Descriptive

// ❌ Bad package names
package user_service  // No underscores
package Users         // No capitals
package pkg          // Too generic

// ═══════════════════════════════════════════
// Variable Naming
// ═══════════════════════════════════════════

// ✅ Good names
var userCount int
var isActive bool
var HTTPServer *Server

// ❌ Bad names
var n int              // Too short, unclear
var user_count int     // Use camelCase
var httpserver *Server // Wrong capitalization

// Short names OK in small scopes
for i := 0; i < 10; i++ {  // ✅ 'i' is fine here
    // ...
}

// Longer names for wider scopes
var applicationConfiguration Config  // ✅ Clear in large scope
```

---

### Error Handling Best Practices 🛡️

```go
// ═══════════════════════════════════════════
// Error Handling Patterns
// ═══════════════════════════════════════════

// ✅ DO: Always handle errors
result, err := doSomething()
if err != nil {
    return fmt.Errorf("do something: %w", err)
}

// ❌ DON'T: Ignore errors
result, _ := doSomething()  // Bad!

// ✅ DO: Add context to errors
if err != nil {
    return fmt.Errorf("failed to load user %d: %w", userID, err)
}

// ❌ DON'T: Return bare errors
if err != nil {
    return err  // No context!
}

// ✅ DO: Check for specific errors
if errors.Is(err, sql.ErrNoRows) {
    return ErrUserNotFound
}

// ✅ DO: Extract error types
var pathErr *os.PathError
if errors.As(err, &pathErr) {
    fmt.Println("Failed path:", pathErr.Path)
}

// ❌ DON'T: Use panic for normal errors
func GetUser(id int) *User {
    user, err := db.Query(id)
    if err != nil {
        panic(err)  // Bad! Use error returns
    }
    return user
}

// ✅ DO: Panic only for unrecoverable errors
func init() {
    if critical_resource == nil {
        panic("critical resource not available")
    }
}

// ✅ DO: Return early
func process(data []byte) error {
    if len(data) == 0 {
        return errors.New("empty data")
    }

    if !isValid(data) {
        return errors.New("invalid data")
    }

    // Main logic here
    return nil
}

// ❌ DON'T: Deeply nest error checks
func badExample(data []byte) error {
    if len(data) > 0 {
        if isValid(data) {
            if canProcess(data) {
                // Deep nesting!
                return process(data)
            } else {
                return errors.New("cannot process")
            }
        } else {
            return errors.New("invalid")
        }
    } else {
        return errors.New("empty")
    }
}
```

---

### Performance Tips ⚡

```go
// ═══════════════════════════════════════════
// String Building
// ═══════════════════════════════════════════

// ❌ Slow: Concatenation in loop
var result string
for i := 0; i < 1000; i++ {
    result += "item"  // Creates new string each time!
}

// ✅ Fast: Use strings.Builder
var builder strings.Builder
for i := 0; i < 1000; i++ {
    builder.WriteString("item")
}
result := builder.String()

// ═══════════════════════════════════════════
// Slice Preallocation
// ═══════════════════════════════════════════

// ❌ Grows dynamically (multiple allocations)
var items []int
for i := 0; i < 1000; i++ {
    items = append(items, i)
}

// ✅ Preallocate if size known
items := make([]int, 0, 1000)
for i := 0; i < 1000; i++ {
    items = append(items, i)
}

// ═══════════════════════════════════════════
// Map Preallocation
// ═══════════════════════════════════════════

// ❌ Default
m := make(map[string]int)

// ✅ Preallocate if size known
m := make(map[string]int, 1000)

// ═══════════════════════════════════════════
// Avoid Unnecessary Allocations
// ═══════════════════════════════════════════

// ❌ Allocates on every call
func getConfig() Config {
    return Config{/* ... */}
}

// ✅ Return pointer (single allocation)
func getConfig() *Config {
    return &Config{/* ... */}
}

// ═══════════════════════════════════════════
// Use sync.Pool for Reusable Objects
// ═══════════════════════════════════════════

var bufferPool = sync.Pool{
    New: func() interface{} {
        return new(bytes.Buffer)
    },
}

func process() {
    buf := bufferPool.Get().(*bytes.Buffer)
    defer func() {
        buf.Reset()
        bufferPool.Put(buf)
    }()

    // Use buffer...
}

// ═══════════════════════════════════════════
// Avoid Interface Conversions in Hot Paths
// ═══════════════════════════════════════════

// ❌ Slower
func process(data interface{}) {
    value := data.(int)  // Type assertion
    // ...
}

// ✅ Faster
func process(data int) {
    // Direct use
}

// ═══════════════════════════════════════════
// Use Buffered Channels
// ═══════════════════════════════════════════

// ❌ Unbuffered (may block)
ch := make(chan int)

// ✅ Buffered (reduces blocking)
ch := make(chan int, 100)
```

---

### Concurrency Best Practices 🔄

```go
// ═══════════════════════════════════════════
// Always Use WaitGroups or Channels
// ═══════════════════════════════════════════

// ❌ DON'T: Sleep to wait
go doWork()
time.Sleep(time.Second)  // Fragile!

// ✅ DO: Use WaitGroup
var wg sync.WaitGroup
wg.Add(1)
go func() {
    defer wg.Done()
    doWork()
}()
wg.Wait()

// ✅ DO: Use channel
done := make(chan bool)
go func() {
    doWork()
    done <- true
}()
<-done

// ═══════════════════════════════════════════
// Protect Shared State
// ═══════════════════════════════════════════

// ❌ Race condition
type Counter struct {
    count int
}

func (c *Counter) Increment() {
    c.count++  // Not thread-safe!
}

// ✅ Use mutex
type Counter struct {
    mu    sync.Mutex
    count int
}

func (c *Counter) Increment() {
    c.mu.Lock()
    c.count++
    c.mu.Unlock()
}

// ✅ Or use atomic
type Counter struct {
    count int64
}

func (c *Counter) Increment() {
    atomic.AddInt64(&c.count, 1)
}

// ═══════════════════════════════════════════
// Always Close Channels (Sender's Job)
// ═══════════════════════════════════════════

// ✅ Proper channel lifecycle
func producer(ch chan<- int) {
    defer close(ch)  // Close when done sending

    for i := 0; i < 10; i++ {
        ch <- i
    }
}

func consumer(ch <-chan int) {
    for value := range ch {  // Exits when closed
        fmt.Println(value)
    }
}

// ═══════════════════════════════════════════
// Use Context for Cancellation
// ═══════════════════════════════════════════

func doWork(ctx context.Context) error {
    for {
        select {
        case <-ctx.Done():
            return ctx.Err()  // Cancelled
        default:
            // Do work
        }
    }
}

// Usage
ctx, cancel := context.WithTimeout(context.Background(), 5*time.Second)
defer cancel()

go doWork(ctx)

// ═══════════════════════════════════════════
// Avoid Goroutine Leaks
// ═══════════════════════════════════════════

// ❌ Leaks goroutines
func leakyFunc() {
    ch := make(chan int)
    go func() {
        value := <-ch  // Blocks forever if nothing sent!
        fmt.Println(value)
    }()
    // ch never receives anything!
}

// ✅ Proper cleanup
func properFunc() {
    ch := make(chan int)
    done := make(chan bool)

    go func() {
        select {
        case value := <-ch:
            fmt.Println(value)
        case <-done:
            return  // Clean exit
        }
    }()

    // Later...
    close(done)  // Clean up goroutine
}
```

---

### Code Quality Tips ✨

```go
// ═══════════════════════════════════════════
// Keep Functions Small
// ═══════════════════════════════════════════

// ❌ Too long
func processUser(id int) error {
    // 200 lines of code...
}

// ✅ Break into smaller functions
func processUser(id int) error {
    user, err := fetchUser(id)
    if err != nil {
        return err
    }

    if err := validateUser(user); err != nil {
        return err
    }

    return saveUser(user)
}

// ═══════════════════════════════════════════
// Use Meaningful Variable Names
// ═══════════════════════════════════════════

// ❌ Unclear
func calc(a, b int) int {
    return a + b
}

// ✅ Clear
func calculateTotalPrice(basePrice, tax int) int {
    return basePrice + tax
}

// ═══════════════════════════════════════════
// Comment Why, Not What
// ═══════════════════════════════════════════

// ❌ States the obvious
// Increment counter by 1
counter++

// ✅ Explains reasoning
// Use double timeout for slow networks
timeout := baseTimeout * 2

// ✅ Document exported functions
// CalculateDiscount returns the discount amount based on user loyalty tier.
// Tier 1: 10%, Tier 2: 15%, Tier 3: 20%
func CalculateDiscount(price float64, tier int) float64 {
    // ...
}

// ═══════════════════════════════════════════
// Use gofmt and golint
// ═══════════════════════════════════════════

/*
# Format code
go fmt ./...

# Lint code
golangci-lint run

# Vet for suspicious code
go vet ./...
*/

// ═══════════════════════════════════════════
// Accept Interfaces, Return Structs
// ═══════════════════════════════════════════

// ✅ Flexible input
func processData(reader io.Reader) (*Result, error) {
    // Can accept any Reader implementation
    return &Result{}, nil
}

// ❌ Too specific
func processData(file *os.File) (*Result, error) {
    // Only works with files!
    return &Result{}, nil
}
```

---

### Testing Best Practices 🧪

```go
// ═══════════════════════════════════════════
// Table-Driven Tests
// ═══════════════════════════════════════════

// ✅ Comprehensive and organized
func TestAdd(t *testing.T) {
    tests := []struct {
        name     string
        a, b     int
        expected int
    }{
        {"positive numbers", 2, 3, 5},
        {"negative numbers", -2, -3, -5},
        {"mixed signs", 2, -3, -1},
        {"zero", 0, 0, 0},
    }

    for _, tt := range tests {
        t.Run(tt.name, func(t *testing.T) {
            result := Add(tt.a, tt.b)
            if result != tt.expected {
                t.Errorf("Add(%d, %d) = %d; want %d",
                    tt.a, tt.b, result, tt.expected)
            }
        })
    }
}

// ═══════════════════════════════════════════
// Use Testify for Assertions (Optional)
// ═══════════════════════════════════════════

import "github.com/stretchr/testify/assert"

func TestSomething(t *testing.T) {
    result := doSomething()

    assert.NotNil(t, result)
    assert.Equal(t, "expected", result.Value)
    assert.True(t, result.IsValid)
}

// ═══════════════════════════════════════════
// Mock External Dependencies
// ═══════════════════════════════════════════

// Define interface
type EmailSender interface {
    Send(to, subject, body string) error
}

// Mock implementation
type MockEmailSender struct {
    sentEmails []string
}

func (m *MockEmailSender) Send(to, subject, body string) error {
    m.sentEmails = append(m.sentEmails, to)
    return nil
}

// Test with mock
func TestNotifyUser(t *testing.T) {
    mock := &MockEmailSender{}
    service := NewUserService(mock)

    service.NotifyUser("user@example.com")

    assert.Len(t, mock.sentEmails, 1)
    assert.Equal(t, "user@example.com", mock.sentEmails[0])
}
```

---

<div align="center">

## 🎓 Go Resources & Tools

### _Level up your Go game!_ 📚

</div>

### Essential Tools 🛠️

```bash
# ═══════════════════════════════════════════
# Code Quality Tools
# ═══════════════════════════════════════════

# gofmt - Format code
go fmt ./...
gofmt -w .

# goimports - Format + organize imports
go install golang.org/x/tools/cmd/goimports@latest
goimports -w .

# golangci-lint - Comprehensive linter
go install github.com/golangci/golangci-lint/cmd/golangci-lint@latest
golangci-lint run

# go vet - Static analysis
go vet ./...

# staticcheck - Advanced static analysis
go install honnef.co/go/tools/cmd/staticcheck@latest
staticcheck ./...

# ═══════════════════════════════════════════
# Documentation
# ═══════════════════════════════════════════

# View package documentation
go doc fmt
go doc fmt.Println

# Start documentation server
godoc -http=:6060

# ═══════════════════════════════════════════
# Profiling & Debugging
# ═══════════════════════════════════════════

# CPU profiling
go test -cpuprofile=cpu.prof -bench=.
go tool pprof cpu.prof

# Memory profiling
go test -memprofile=mem.prof -bench=.
go tool pprof mem.prof

# Race detector
go test -race ./...
go run -race main.go

# Delve debugger
go install github.com/go-delve/delve/cmd/dlv@latest
dlv debug main.go

# ═══════════════════════════════════════════
# Build Tools
# ═══════════════════════════════════════════

# Cross-compilation
GOOS=linux GOARCH=amd64 go build
GOOS=windows GOARCH=amd64 go build
GOOS=darwin GOARCH=arm64 go build

# Build with flags
go build -ldflags="-s -w" -o myapp  # Smaller binary

# Install to $GOPATH/bin
go install
```

---

### Learning Resources 📖

```
📚 Official Documentation
   - https://go.dev/doc/
   - https://go.dev/tour/
   - https://go.dev/doc/effective_go

📚 Books
   - "The Go Programming Language" by Donovan & Kernighan
   - "Concurrency in Go" by Katherine Cox-Buday
   - "Learning Go" by Jon Bodner

🎥 Video Courses
   - Gophercises (https://gophercises.com)
   - JustForFunc (YouTube)
   - Todd McLeod's Go Course (Udemy)

🏋️ Practice
   - Exercism.io Go Track
   - LeetCode (Go problems)
   - Go by Example (https://gobyexample.com)

🌐 Community
   - r/golang (Reddit)
   - Gophers Slack (https://invite.slack.golangbridge.org/)
   - Go Forum (https://forum.golangbridge.org/)

📰 Blogs & News
   - Go Blog (https://go.dev/blog/)
   - Dave Cheney's Blog
   - Ardan Labs Blog
   - Golang Weekly Newsletter
```

---

### Popular Go Packages 📦

```go
// ═══════════════════════════════════════════
// Web Frameworks
// ═══════════════════════════════════════════

// Gin - Fast web framework
github.com/gin-gonic/gin

// Echo - High performance framework
github.com/labstack/echo

// Fiber - Express-inspired framework
github.com/gofiber/fiber

// Chi - Lightweight router
github.com/go-chi/chi

// ═══════════════════════════════════════════
// Database
// ═══════════════════════════════════════════

// GORM - ORM library
gorm.io/gorm

// sqlx - Extensions for database/sql
github.com/jmoiron/sqlx

// pgx - PostgreSQL driver
github.com/jackc/pgx

// Redis client
github.com/go-redis/redis

// MongoDB driver
go.mongodb.org/mongo-driver

// ═══════════════════════════════════════════
// Testing
// ═══════════════════════════════════════════

// Testify - Testing toolkit
github.com/stretchr/testify

// GoMock - Mocking framework
github.com/golang/mock

// Ginkgo - BDD testing framework
github.com/onsi/ginkgo

// ═══════════════════════════════════════════
// Utilities
// ═══════════════════════════════════════════

// Viper - Configuration management
github.com/spf13/viper

// Cobra - CLI applications
github.com/spf13/cobra

// Logrus - Structured logging
github.com/sirupsen/logrus

// Zap - Fast logging
go.uber.org/zap

// UUID generation
github.com/google/uuid

// Validator
github.com/go-playground/validator

// ═══════════════════════════════════════════
// Networking
// ═══════════════════════════════════════════

// gRPC
google.golang.org/grpc

// WebSocket
github.com/gorilla/websocket

// HTTP client
github.com/go-resty/resty

// ═══════════════════════════════════════════
// Concurrency
// ═══════════════════════════════════════════

// Errgroup - Error group helpers
golang.org/x/sync/errgroup

// Rate limiting
golang.org/x/time/rate

// Worker pool
github.com/gammazero/workerpool
```

---

<div align="center">

## 🏆 You've Mastered Go!

### _From basics to advanced patterns_ 🎉

</div>

**You now know:**

- ✅ Go fundamentals & syntax
- ✅ Data structures & types
- ✅ Functions & methods
- ✅ Structs & interfaces
- ✅ Error handling patterns
- ✅ Packages & modules
- ✅ Goroutines & concurrency
- ✅ Web development
- ✅ Database operations
- ✅ File I/O
- ✅ Testing strategies
- ✅ Common design patterns
- ✅ Best practices & optimization

---

<div align="center">

### The Go Philosophy 🧘

> **"Less is exponentially more"** - Rob Pike

> **"Don't communicate by sharing memory; share memory by communicating"** - Go Proverb

> **"Clear is better than clever"** - Go Proverb

> **"Errors are values"** - Go Proverb

> **"Concurrency is not parallelism"** - Rob Pike

</div>

---

### Quick Reference Card 📇

```go
// Variables
var name string = "value"
name := "value"  // Short declaration

// Functions
func name(param type) returnType {}

// Methods
func (r Receiver) name() {}

// Goroutines
go function()

// Channels
ch := make(chan type)
ch <- value      // Send
value := <-ch    // Receive

// Error handling
if err != nil {
    return fmt.Errorf("context: %w", err)
}

// Defer
defer cleanup()

// Interfaces
type Name interface {
    Method() type
}

// Structs
type Name struct {
    Field type
}

// For loop (only loop in Go!)
for i := 0; i < 10; i++ {}
for condition {}
for {}  // Infinite
for key, value := range collection {}

// Switch
switch value {
case option1:
    // code
case option2:
    // code
default:
    // code
}
```

---

<div align="center">

### Useful Commands Cheat Sheet 📋

```bash
# Run
go run main.go

# Build
go build
go build -o appname

# Test
go test ./...
go test -v
go test -cover
go test -bench=.

# Modules
go mod init
go mod tidy
go get package
go mod download

# Format & Lint
go fmt ./...
go vet ./...
golangci-lint run

# Documentation
go doc package
godoc -http=:6060

# Cross-compile
GOOS=linux GOARCH=amd64 go build
```

</div>

---

<div align="center">

## 🚀 Next Steps

### _Continue Your Go Journey_ 🌟

</div>

**Level Up:**

1. 🏗️ Build a real project (REST API, CLI tool, microservice)
2. 📖 Read "Concurrency in Go" book
3. 🎯 Practice design patterns
4. 🔍 Learn profiling and optimization
5. 🌐 Explore gRPC and Protocol Buffers
6. 🐳 Containerize Go apps with Docker
7. ☸️ Deploy to Kubernetes
8. 🤝 Contribute to open source Go projects
9. 📝 Write technical blog posts about Go
10. 🎤 Join Go community events

---

<div align="center">

### Quick Project Ideas 💡

```
🌐 Web Application
   - REST API with Gin/Echo
   - Real-time chat with WebSockets
   - Blog platform with templates

🛠️ CLI Tool
   - Task manager
   - File organizer
   - Git wrapper

🔌 Microservices
   - User authentication service
   - Payment gateway
   - Notification system

🤖 Automation
   - Web scraper
   - Backup tool
   - Deployment automation

📊 Data Processing
   - Log analyzer
   - CSV processor
   - Data pipeline
```

</div>

---

<div align="center">

## 🎯 Final Tips for Success

</div>

1. **Write Go code daily** - Consistency beats intensity
2. **Read other people's code** - Learn from the Go standard library
3. **Don't fight the language** - Embrace Go's simplicity
4. **Benchmark before optimizing** - Measure, don't guess
5. **Test everything** - Tests are documentation
6. **Use interfaces wisely** - Keep them small and focused
7. **Handle errors explicitly** - No hidden control flow
8. **Think in goroutines** - Leverage concurrency
9. **Read Effective Go** - Over and over
10. **Have fun!** - Go is enjoyable to write

---

<div align="center">

**Built with 🔵 by MrDib, for Gophers**

_"Go is not meant to innovate programming theory. It's meant to innovate programming practice."_ - Samuel Tesla

**Happy Coding, Gopher!** 🚀

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

**Stay curious. Keep coding. Go forth and build amazing things!** ⚡

🔵 **#GoLang** 🔵 **#DevResourceVault** 🔵 **#MrDib** 🔵

</div>
