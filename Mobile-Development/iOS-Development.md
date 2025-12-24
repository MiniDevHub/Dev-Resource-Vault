<div align="center">

# 🍎 iOS Development - Build for Apple! 🍎

![iOS](https://img.shields.io/badge/iOS-000000?style=for-the-badge&logo=ios&logoColor=white)
![Swift](https://img.shields.io/badge/Swift-FA7343?style=for-the-badge&logo=swift&logoColor=white)
![Xcode](https://img.shields.io/badge/Xcode-007ACC?style=for-the-badge&logo=xcode&logoColor=white)

### _Build beautiful apps for iPhone and iPad_ 📱

**Native performance, stunning UI, Apple ecosystem!** ✨

</div>

---

## 📚 Table of Contents

- [🎯 What is iOS Development](#-what-is-ios-development)
- [🚀 Getting Started](#-getting-started)
- [📝 Swift Language Basics](#-swift-language-basics)
- [🎨 SwiftUI Fundamentals](#-swiftui-fundamentals)
- [🏗️ UIKit Basics](#️-uikit-basics)
- [🧭 Navigation & Routing](#-navigation--routing)
- [💾 Data Persistence](#-data-persistence)
- [📡 Networking](#-networking)
- [🔧 Core Frameworks](#-core-frameworks)
- [🎬 Animations](#-animations)
- [🧪 Testing](#-testing)
- [⚡ Performance](#-performance)
- [📲 App Store Submission](#-app-store-submission)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 🎯 What is iOS Development

</div>

### Understanding iOS Development 🌟

```

# ═══════════════════════════════════════════

# iOS DEVELOPMENT EXPLAINED

# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║ WHAT IS iOS DEVELOPMENT?                                   ║
╚════════════════════════════════════════════════════════════╝

iOS Development:
─────────────────────────────────────────────────────────────
Building native applications for Apple's mobile devices
(iPhone, iPad, iPod Touch) using Swift or Objective-C.

Key Points:
─────────────────────────────────────────────────────────────
✅ Apple's mobile platform
✅ Swift programming language (modern)
✅ Xcode IDE (official)
✅ SwiftUI (declarative UI)
✅ UIKit (imperative UI)
✅ App Store distribution
✅ High-quality ecosystem

Platforms:
─────────────────────────────────────────────────────────────
• iOS - iPhone
• iPadOS - iPad
• watchOS - Apple Watch
• tvOS - Apple TV
• macOS - Mac (with Catalyst)

╔════════════════════════════════════════════════════════════╗
║ SWIFTUI vs UIKIT                                           ║
╚════════════════════════════════════════════════════════════╝

SwiftUI (New - 2019):
─────────────────────────────────────────────────────────────
✅ Declarative syntax
✅ Less code
✅ Live preview
✅ Cross-platform (iOS, macOS, watchOS, tvOS)
✅ Modern and future-proof
✅ Automatic animations
❌ iOS 13+ only
❌ Some features missing
❌ Less community resources

UIKit (Legacy - 2008):
─────────────────────────────────────────────────────────────
✅ Mature and stable
✅ Works on older iOS versions
✅ Complete feature set
✅ Huge community
✅ More Stack Overflow answers
❌ More boilerplate code
❌ Storyboards can be messy
❌ Being phased out slowly

Recommendation:
─────────────────────────────────────────────────────────────
New Projects: SwiftUI (iOS 15+)
Legacy Support: UIKit or Hybrid
Enterprise: Hybrid approach

╔════════════════════════════════════════════════════════════╗
║ WHY iOS DEVELOPMENT?                                       ║
╚════════════════════════════════════════════════════════════╝

Advantages:
─────────────────────────────────────────────────────────────
✅ High-quality users
✅ Better monetization
✅ Less fragmentation (vs Android)
✅ Powerful ecosystem
✅ Apple design guidelines
✅ Quality hardware
✅ Privacy-focused
✅ Regular updates

Challenges:
─────────────────────────────────────────────────────────────
❌ Need Mac for development
❌ $99/year developer program
❌ Strict App Store review
❌ Apple-only ecosystem
❌ Limited device testing (expensive)

Requirements:
─────────────────────────────────────────────────────────────
• Mac computer (Xcode requirement)
• Apple Developer Account ($99/year for App Store)
• iPhone/iPad for testing (optional but recommended)
• Xcode (free)

╔════════════════════════════════════════════════════════════╗
║ iOS MARKET                                                 ║
╚════════════════════════════════════════════════════════════╝

Statistics:
─────────────────────────────────────────────────────────────
• 1.8 billion active iOS devices
• 27% global smartphone market share
• Higher revenue than Android
• Premium user base
• Strong in US, Europe, Japan

App Store:
─────────────────────────────────────────────────────────────
• 2+ million apps
• Strict quality control
• 30% commission (15% for small businesses)
• Global distribution
• Built-in payment processing

Career Opportunities:
─────────────────────────────────────────────────────────────
✅ High demand
✅ Good salaries
✅ Remote work opportunities
✅ Freelance projects
✅ Startup opportunities

```

---

<div align="center">

## 🚀 Getting Started

</div>

### Setup Your Environment 🛠️

```

# ═══════════════════════════════════════════

# SETUP & INSTALLATION

# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║ REQUIREMENTS                                               ║
╚════════════════════════════════════════════════════════════╝

Hardware:
─────────────────────────────────────────────────────────────
• Mac computer (MacBook, iMac, Mac mini, Mac Studio)

- Apple Silicon (M1/M2/M3) - Recommended
- Intel Mac - Works but slower
  • At least 8GB RAM (16GB recommended)
  • 50GB+ free disk space

Software:
─────────────────────────────────────────────────────────────
• macOS Ventura or later (for latest Xcode)
• Xcode (free from App Store)
• Apple Developer Account (free for testing, $99/year for App Store)

╔════════════════════════════════════════════════════════════╗
║ INSTALL XCODE                                              ║
╚════════════════════════════════════════════════════════════╝

Installation:
─────────────────────────────────────────────────────────────

1. Open App Store
2. Search "Xcode"
3. Click "Get" (8+ GB download)
4. Wait for installation
5. Open Xcode
6. Install additional components when prompted

Or via command line:
─────────────────────────────────────────────────────────────

```

Install Xcode Command Line Tools:

```bash
# Install command line tools
xcode-select --install

# Verify installation
xcode-select -p
# Should print: /Applications/Xcode.app/Contents/Developer

# Accept license
sudo xcodebuild -license accept

# Install iOS Simulator
xcrun simctl list devices
```

```
╔════════════════════════════════════════════════════════════╗
║                   CREATE YOUR FIRST APP                    ║
╚════════════════════════════════════════════════════════════╝

Steps:
─────────────────────────────────────────────────────────────
1. Open Xcode
2. Click "Create New Project"
3. Choose "iOS" → "App"
4. Enter details:
   - Product Name: MyFirstApp
   - Team: None (for now)
   - Organization Identifier: com.yourname
   - Interface: SwiftUI
   - Language: Swift
5. Choose save location
6. Click "Create"

Project Structure:
─────────────────────────────────────────────────────────────
```

```
MyFirstApp/
├── MyFirstApp.xcodeproj    # Xcode project file
├── MyFirstApp/
│   ├── MyFirstAppApp.swift # App entry point
│   ├── ContentView.swift   # Main view
│   ├── Assets.xcassets     # Images, colors
│   ├── Preview Content/    # Preview assets
│   └── Info.plist          # App configuration (if needed)
└── MyFirstAppTests/        # Test files
```

```
╔════════════════════════════════════════════════════════════╗
║                   RUN YOUR FIRST APP                       ║
╚════════════════════════════════════════════════════════════╝

Running in Simulator:
─────────────────────────────────────────────────────────────
1. Select simulator from device menu (top toolbar)
   - iPhone 15 Pro, iPad Pro, etc.
2. Click "Run" button (▶︎) or Cmd+R
3. Wait for build and simulator launch
4. App opens automatically

Running on Physical Device:
─────────────────────────────────────────────────────────────
1. Connect iPhone/iPad via USB
2. Trust computer on device
3. Select your device from device menu
4. First time: Fix code signing
   - Click project name in navigator
   - Select target
   - "Signing & Capabilities" tab
   - Select "Automatically manage signing"
   - Choose your team/Apple ID
5. Click Run (Cmd+R)

Troubleshooting:
─────────────────────────────────────────────────────────────
• "No developer account": Add Apple ID in Xcode Preferences
• "Device not trusted": Trust computer on device
• "Code signing error": Check team selection

╔════════════════════════════════════════════════════════════╗
║                   YOUR FIRST SWIFTUI APP                   ║
╚════════════════════════════════════════════════════════════╝
```

Hello World App:

```swift
// MyFirstAppApp.swift - App Entry Point
import SwiftUI

@main
struct MyFirstAppApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}

// ContentView.swift - Main View
import SwiftUI

struct ContentView: View {
    @State private var counter = 0

    var body: some View {
        VStack(spacing: 20) {
            Text("Hello, iOS!")
                .font(.largeTitle)
                .fontWeight(.bold)

            Text("You tapped \(counter) times")
                .font(.title2)

            Button(action: {
                counter += 1
            }) {
                Text("Tap Me!")
                    .font(.title3)
                    .foregroundColor(.white)
                    .padding()
                    .background(Color.blue)
                    .cornerRadius(10)
            }

            Button(action: {
                counter = 0
            }) {
                Text("Reset")
                    .foregroundColor(.red)
            }
        }
        .padding()
    }
}

// Preview
#Preview {
    ContentView()
}
```

---

<div align="center">

## 📝 Swift Language Basics

</div>

### Learn Swift Essentials 💎

```
# ═══════════════════════════════════════════
# SWIFT LANGUAGE BASICS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SWIFT FUNDAMENTALS                       ║
╚════════════════════════════════════════════════════════════╝

Variables & Constants:
─────────────────────────────────────────────────────────────
```

Swift basics:

```swift
// Variables (can change)
var name = "John"
var age = 30
var height = 5.9
var isActive = true

// Constants (cannot change)
let pi = 3.14159
let appName = "MyApp"

// Type annotations
var message: String = "Hello"
var count: Int = 10
var price: Double = 19.99
var isEnabled: Bool = true

// Type inference (Swift figures it out)
var greeting = "Hello" // String
var number = 42        // Int

// Optionals (can be nil)
var optionalName: String? = "John"
var optionalAge: Int? = nil

// Optional binding
if let name = optionalName {
    print("Name is \(name)")
} else {
    print("Name is nil")
}

// Guard let
func greet(name: String?) {
    guard let name = name else {
        print("No name provided")
        return
    }
    print("Hello, \(name)")
}

// Nil coalescing
let displayName = optionalName ?? "Guest"

// Force unwrapping (dangerous!)
let unwrapped = optionalName! // Crashes if nil

// Collections
let fruits = ["Apple", "Banana", "Orange"]
var numbers = [1, 2, 3, 4, 5]

// Dictionary
var scores = ["John": 90, "Jane": 95, "Bob": 85]

// Set
var colors: Set = ["Red", "Green", "Blue"]

// String interpolation
let firstName = "John"
let lastName = "Doe"
print("Full name: \(firstName) \(lastName)")
print("Age next year: \(age + 1)")

// Functions
func add(a: Int, b: Int) -> Int {
    return a + b
}

// Function with label
func greet(person name: String) -> String {
    return "Hello, \(name)!"
}

// Usage
greet(person: "John")

// Default parameters
func welcome(name: String = "Guest") {
    print("Welcome, \(name)")
}

// Closures (anonymous functions)
let multiply = { (a: Int, b: Int) -> Int in
    return a * b
}

// Shorthand
let numbers2 = [1, 2, 3, 4, 5]
let doubled = numbers2.map { $0 * 2 }
print(doubled) // [2, 4, 6, 8, 10]

// Control flow
if age >= 18 {
    print("Adult")
} else {
    print("Minor")
}

// Switch
let grade = "A"
switch grade {
case "A":
    print("Excellent")
case "B":
    print("Good")
case "C":
    print("Average")
default:
    print("Needs improvement")
}

// For loop
for fruit in fruits {
    print(fruit)
}

for i in 1...5 {
    print(i)
}

for i in 0..<5 {
    print(i) // 0 to 4
}

// While loop
var count = 0
while count < 5 {
    print(count)
    count += 1
}
```

```
Classes & Structs:
─────────────────────────────────────────────────────────────
```

Classes and Structs:

```swift
// Struct (value type - copied)
struct Person {
    var name: String
    var age: Int

    func introduce() {
        print("Hi, I'm \(name), age \(age)")
    }

    mutating func haveBirthday() {
        age += 1
    }
}

var person = Person(name: "John", age: 30)
person.introduce()

// Class (reference type - shared)
class Animal {
    var name: String
    var species: String

    init(name: String, species: String) {
        self.name = name
        self.species = species
    }

    func makeSound() {
        print("Some sound")
    }
}

// Inheritance
class Dog: Animal {
    var breed: String

    init(name: String, breed: String) {
        self.breed = breed
        super.init(name: name, species: "Dog")
    }

    override func makeSound() {
        print("Woof!")
    }
}

let dog = Dog(name: "Buddy", breed: "Golden Retriever")
dog.makeSound()

// Properties
class Counter {
    var count = 0

    // Computed property
    var doubleCount: Int {
        return count * 2
    }

    // Property observer
    var total: Int = 0 {
        didSet {
            print("Total changed from \(oldValue) to \(total)")
        }
        willSet {
            print("About to set total to \(newValue)")
        }
    }
}

// Enums
enum Direction {
    case north, south, east, west
}

enum Result {
    case success(String)
    case failure(Error)
}

// Protocols (like interfaces)
protocol Drawable {
    func draw()
}

class Circle: Drawable {
    func draw() {
        print("Drawing circle")
    }
}

// Extensions
extension String {
    func greet() -> String {
        return "Hello, \(self)!"
    }
}

let name = "World"
print(name.greet()) // "Hello, World!"

// Generics
func swap<T>(_ a: inout T, _ b: inout T) {
    let temp = a
    a = b
    b = temp
}

// Error handling
enum NetworkError: Error {
    case badURL
    case noInternet
    case serverError
}

func fetchData() throws -> String {
    throw NetworkError.noInternet
}

// Try-catch
do {
    let data = try fetchData()
    print(data)
} catch NetworkError.noInternet {
    print("No internet connection")
} catch {
    print("Unknown error: \(error)")
}

// Try?
let data = try? fetchData() // Returns nil if error

// Async/await (modern)
func fetchUser() async throws -> User {
    let url = URL(string: "https://api.example.com/user")!
    let (data, _) = try await URLSession.shared.data(from: url)
    return try JSONDecoder().decode(User.self, from: data)
}

// Usage
Task {
    do {
        let user = try await fetchUser()
        print(user.name)
    } catch {
        print("Error: \(error)")
    }
}
```

---

<div align="center">

## 🎨 SwiftUI Fundamentals

</div>

### Build Modern iOS Apps 🎯

```
# ═══════════════════════════════════════════
# SWIFTUI FUNDAMENTALS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   BASIC VIEWS                              ║
╚════════════════════════════════════════════════════════════╝

Common Views:
─────────────────────────────────────────────────────────────
```

SwiftUI views:

```swift
import SwiftUI

struct ContentView: View {
    var body: some View {
        VStack(spacing: 20) {
            // Text
            Text("Hello, SwiftUI!")
                .font(.title)
                .fontWeight(.bold)
                .foregroundColor(.blue)

            // Image
            Image(systemName: "star.fill")
                .font(.system(size: 50))
                .foregroundColor(.yellow)

            // Custom image
            Image("logo")
                .resizable()
                .scaledToFit()
                .frame(width: 100, height: 100)

            // Button
            Button("Tap Me") {
                print("Button tapped")
            }
            .buttonStyle(.borderedProminent)

            // Custom button
            Button(action: {
                print("Custom button tapped")
            }) {
                HStack {
                    Image(systemName: "heart.fill")
                    Text("Like")
                }
                .padding()
                .background(Color.red)
                .foregroundColor(.white)
                .cornerRadius(10)
            }

            // TextField
            TextField("Enter name", text: .constant(""))
                .textFieldStyle(.roundedBorder)
                .padding(.horizontal)

            // SecureField (password)
            SecureField("Password", text: .constant(""))
                .textFieldStyle(.roundedBorder)
                .padding(.horizontal)

            // Toggle
            Toggle("Enable notifications", isOn: .constant(true))
                .padding(.horizontal)

            // Slider
            Slider(value: .constant(50), in: 0...100)
                .padding(.horizontal)

            // Picker
            Picker("Select", selection: .constant(0)) {
                Text("Option 1").tag(0)
                Text("Option 2").tag(1)
                Text("Option 3").tag(2)
            }
            .pickerStyle(.segmented)
            .padding(.horizontal)
        }
    }
}
```

```
╔════════════════════════════════════════════════════════════╗
║                   STATE MANAGEMENT                         ║
╚════════════════════════════════════════════════════════════╝

@State - Local State:
─────────────────────────────────────────────────────────────
```

State management:

```swift
struct CounterView: View {
    @State private var count = 0
    @State private var name = ""
    @State private var isEnabled = false

    var body: some View {
        VStack(spacing: 20) {
            Text("Count: \(count)")
                .font(.largeTitle)

            Button("Increment") {
                count += 1
            }

            Button("Decrement") {
                count -= 1
            }

            TextField("Name", text: $name)
                .textFieldStyle(.roundedBorder)
                .padding()

            Text("Hello, \(name)")

            Toggle("Enable", isOn: $isEnabled)
                .padding()
        }
    }
}

// @Binding - Pass state to child
struct ChildView: View {
    @Binding var count: Int

    var body: some View {
        Button("Increment from child") {
            count += 1
        }
    }
}

struct ParentView: View {
    @State private var count = 0

    var body: some View {
        VStack {
            Text("Count: \(count)")
            ChildView(count: $count)
        }
    }
}

// @ObservedObject - For external objects
class UserData: ObservableObject {
    @Published var username = ""
    @Published var age = 0
    @Published var isLoggedIn = false
}

struct ProfileView: View {
    @ObservedObject var userData = UserData()

    var body: some View {
        VStack {
            TextField("Username", text: $userData.username)
            Text("Username: \(userData.username)")
        }
    }
}

// @StateObject - Own and manage object
struct AppView: View {
    @StateObject private var userData = UserData()

    var body: some View {
        ProfileView(userData: userData)
    }
}

// @EnvironmentObject - Share across app
@main
struct MyApp: App {
    @StateObject private var userData = UserData()

    var body: some Scene {
        WindowGroup {
            ContentView()
                .environmentObject(userData)
        }
    }
}

struct ContentView: View {
    @EnvironmentObject var userData: UserData

    var body: some View {
        Text("Hello, \(userData.username)")
    }
}
```

```
╔════════════════════════════════════════════════════════════╗
║                   LAYOUTS                                  ║
╚════════════════════════════════════════════════════════════╝
```

Layout containers:

```swift
// VStack - Vertical
VStack(alignment: .leading, spacing: 10) {
    Text("Item 1")
    Text("Item 2")
    Text("Item 3")
}

// HStack - Horizontal
HStack(alignment: .center, spacing: 15) {
    Image(systemName: "star.fill")
    Text("Rating")
    Text("5.0")
}

// ZStack - Overlay
ZStack {
    Color.blue
        .ignoresSafeArea()

    Text("Overlay Text")
        .foregroundColor(.white)
}

// Spacer
HStack {
    Text("Left")
    Spacer()
    Text("Right")
}

// Divider
VStack {
    Text("Above")
    Divider()
    Text("Below")
}

// Grid (iOS 16+)
Grid {
    GridRow {
        Text("1")
        Text("2")
        Text("3")
    }
    GridRow {
        Text("4")
        Text("5")
        Text("6")
    }
}

// LazyVStack (for lists)
ScrollView {
    LazyVStack {
        ForEach(0..<1000) { index in
            Text("Row \(index)")
        }
    }
}

// List
List {
    Text("Item 1")
    Text("Item 2")
    Text("Item 3")
}

// List with data
struct Item: Identifiable {
    let id = UUID()
    let title: String
}

struct ListView: View {
    let items = [
        Item(title: "Item 1"),
        Item(title: "Item 2"),
        Item(title: "Item 3")
    ]

    var body: some View {
        List(items) { item in
            Text(item.title)
        }
    }
}

// ScrollView
ScrollView {
    VStack(spacing: 20) {
        ForEach(0..<50) { index in
            Text("Row \(index)")
                .frame(maxWidth: .infinity)
                .padding()
                .background(Color.gray.opacity(0.2))
                .cornerRadius(8)
        }
    }
    .padding()
}

// Horizontal ScrollView
ScrollView(.horizontal, showsIndicators: false) {
    HStack(spacing: 20) {
        ForEach(0..<10) { index in
            RoundedRectangle(cornerRadius: 10)
                .fill(Color.blue)
                .frame(width: 150, height: 100)
        }
    }
    .padding()
}
```

```
╔════════════════════════════════════════════════════════════╗
║                   MODIFIERS                                ║
╚════════════════════════════════════════════════════════════╝
```

Common modifiers:

```swift
Text("Hello")
    // Font
    .font(.title)
    .font(.system(size: 20))
    .fontWeight(.bold)

    // Color
    .foregroundColor(.blue)
    .background(Color.yellow)

    // Padding
    .padding()
    .padding(.horizontal, 20)
    .padding(.vertical, 10)

    // Frame
    .frame(width: 200, height: 50)
    .frame(maxWidth: .infinity) // Full width

    // Corner radius
    .cornerRadius(10)

    // Shadow
    .shadow(color: .gray, radius: 5, x: 0, y: 2)

    // Border
    .border(Color.red, width: 2)
    .overlay(
        RoundedRectangle(cornerRadius: 10)
            .stroke(Color.blue, lineWidth: 2)
    )

    // Opacity
    .opacity(0.5)

    // Rotation
    .rotationEffect(.degrees(45))

    // Scale
    .scaleEffect(1.5)

    // Offset
    .offset(x: 10, y: 20)
```

---

<div align="center">

## 🏗️ UIKit Basics

</div>

### Legacy UI Framework 📱

```
# ═══════════════════════════════════════════
# UIKIT BASICS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   UIKIT VIEWCONTROLLER                     ║
╚════════════════════════════════════════════════════════════╝

Basic ViewController:
─────────────────────────────────────────────────────────────
```

UIKit example:

```swift
import UIKit

class ViewController: UIViewController {

    // UI Elements
    let titleLabel: UILabel = {
        let label = UILabel()
        label.text = "Hello, UIKit!"
        label.font = UIFont.systemFont(ofSize: 24, weight: .bold)
        label.textAlignment = .center
        label.translatesAutoresizingMaskIntoConstraints = false
        return label
    }()

    let counterLabel: UILabel = {
        let label = UILabel()
        label.text = "0"
        label.font = UIFont.systemFont(ofSize: 48)
        label.textAlignment = .center
        label.translatesAutoresizingMaskIntoConstraints = false
        return label
    }()

    let incrementButton: UIButton = {
        let button = UIButton(type: .system)
        button.setTitle("Increment", for: .normal)
        button.titleLabel?.font = UIFont.systemFont(ofSize: 18)
        button.translatesAutoresizingMaskIntoConstraints = false
        return button
    }()

    var counter = 0

    // Lifecycle
    override func viewDidLoad() {
        super.viewDidLoad()
        setupUI()
    }

    func setupUI() {
        view.backgroundColor = .white

        // Add subviews
        view.addSubview(titleLabel)
        view.addSubview(counterLabel)
        view.addSubview(incrementButton)

        // Add button action
        incrementButton.addTarget(self, action: #selector(incrementTapped), for: .touchUpInside)

        // Layout constraints
        NSLayoutConstraint.activate([
            // Title label
            titleLabel.topAnchor.constraint(equalTo: view.safeAreaLayoutGuide.topAnchor, constant: 50),
            titleLabel.leadingAnchor.constraint(equalTo: view.leadingAnchor, constant: 20),
            titleLabel.trailingAnchor.constraint(equalTo: view.trailingAnchor, constant: -20),

            // Counter label
            counterLabel.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            counterLabel.centerYAnchor.constraint(equalTo: view.centerYAnchor),

            // Button
            incrementButton.topAnchor.constraint(equalTo: counterLabel.bottomAnchor, constant: 30),
            incrementButton.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            incrementButton.widthAnchor.constraint(equalToConstant: 120),
            incrementButton.heightAnchor.constraint(equalToConstant: 44)
        ])
    }

    @objc func incrementTapped() {
        counter += 1
        counterLabel.text = "\(counter)"
    }
}

// TableView example
class TableViewController: UITableViewController {

    let items = ["Item 1", "Item 2", "Item 3", "Item 4", "Item 5"]

    override func viewDidLoad() {
        super.viewDidLoad()
        tableView.register(UITableViewCell.self, forCellReuseIdentifier: "cell")
    }

    override func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return items.count
    }

    override func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "cell", for: indexPath)
        cell.textLabel?.text = items[indexPath.row]
        return cell
    }

    override func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
        print("Selected: \(items[indexPath.row])")
        tableView.deselectRow(at: indexPath, animated: true)
    }
}
```

---

<div align="center">

## 🧭 Navigation & Routing

</div>

### Navigate Between Screens 🗺️

```
# ═══════════════════════════════════════════
# NAVIGATION IN SWIFTUI
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   NAVIGATIONSTACK (iOS 16+)                ║
╚════════════════════════════════════════════════════════════╝
```

SwiftUI navigation:

```swift
import SwiftUI

// Modern NavigationStack (iOS 16+)
struct ContentView: View {
    var body: some View {
        NavigationStack {
            List {
                NavigationLink("Go to Detail") {
                    DetailView(item: "Item 1")
                }

                NavigationLink("Go to Settings") {
                    SettingsView()
                }
            }
            .navigationTitle("Home")
        }
    }
}

struct DetailView: View {
    let item: String

    var body: some View {
        VStack {
            Text("Detail: \(item)")

            NavigationLink("Go Deeper") {
                ThirdView()
            }
        }
        .navigationTitle("Detail")
    }
}

// Programmatic navigation
struct NavigationExample: View {
    @State private var path = NavigationPath()

    var body: some View {
        NavigationStack(path: $path) {
            VStack {
                Button("Go to Detail") {
                    path.append("detail")
                }

                Button("Go to Settings") {
                    path.append("settings")
                }

                Button("Pop to Root") {
                    path = NavigationPath()
                }
            }
            .navigationDestination(for: String.self) { value in
                if value == "detail" {
                    DetailView(item: "Item")
                } else if value == "settings" {
                    SettingsView()
                }
            }
            .navigationTitle("Home")
        }
    }
}

// TabView
struct TabViewExample: View {
    var body: some View {
        TabView {
            HomeView()
                .tabItem {
                    Label("Home", systemImage: "house")
                }

            SearchView()
                .tabItem {
                    Label("Search", systemImage: "magnifyingglass")
                }

            ProfileView()
                .tabItem {
                    Label("Profile", systemImage: "person")
                }
        }
    }
}

// Sheet (modal)
struct SheetExample: View {
    @State private var showSheet = false

    var body: some View {
        Button("Show Sheet") {
            showSheet = true
        }
        .sheet(isPresented: $showSheet) {
            SheetContent()
        }
    }
}

struct SheetContent: View {
    @Environment(\.dismiss) var dismiss

    var body: some View {
        NavigationStack {
            Text("Sheet Content")
                .navigationTitle("Modal")
                .toolbar {
                    ToolbarItem(placement: .cancellationAction) {
                        Button("Close") {
                            dismiss()
                        }
                    }
                }
        }
    }
}

// FullScreenCover
.fullScreenCover(isPresented: $showFullScreen) {
    FullScreenView()
}

// Alert
struct AlertExample: View {
    @State private var showAlert = false

    var body: some View {
        Button("Show Alert") {
            showAlert = true
        }
        .alert("Important", isPresented: $showAlert) {
            Button("OK", role: .cancel) { }
            Button("Delete", role: .destructive) {
                print("Deleted")
            }
        } message: {
            Text("Are you sure you want to delete?")
        }
    }
}

// ActionSheet
.confirmationDialog("Choose an option", isPresented: $showActionSheet) {
    Button("Option 1") { }
    Button("Option 2") { }
    Button("Cancel", role: .cancel) { }
}
```

---

<div align="center">

## 💾 Data Persistence

</div>

### Save Data Locally 📂

```
# ═══════════════════════════════════════════
# DATA PERSISTENCE
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   USERDEFAULTS                             ║
╚════════════════════════════════════════════════════════════╝

Simple Key-Value Storage:
─────────────────────────────────────────────────────────────
```

UserDefaults:

```swift
// Save
UserDefaults.standard.set("John", forKey: "username")
UserDefaults.standard.set(25, forKey: "age")
UserDefaults.standard.set(true, forKey: "isLoggedIn")

// Read
let username = UserDefaults.standard.string(forKey: "username")
let age = UserDefaults.standard.integer(forKey: "age")
let isLoggedIn = UserDefaults.standard.bool(forKey: "isLoggedIn")

// Save object
struct User: Codable {
    let name: String
    let age: Int
}

let user = User(name: "John", age: 25)
if let encoded = try? JSONEncoder().encode(user) {
    UserDefaults.standard.set(encoded, forKey: "user")
}

// Read object
if let data = UserDefaults.standard.data(forKey: "user"),
   let user = try? JSONDecoder().decode(User.self, from: data) {
    print(user.name)
}

// Remove
UserDefaults.standard.removeObject(forKey: "username")

// Property wrapper
@AppStorage("username") var username: String = ""
@AppStorage("isDarkMode") var isDarkMode: Bool = false

struct SettingsView: View {
    @AppStorage("username") var username: String = ""

    var body: some View {
        TextField("Username", text: $username)
    }
}
```

```
╔════════════════════════════════════════════════════════════╗
║                   SWIFTDATA (iOS 17+)                      ║
╚════════════════════════════════════════════════════════════╝
```

SwiftData (modern):

```swift
import SwiftData

// Define model
@Model
class Todo {
    var title: String
    var isCompleted: Bool
    var createdAt: Date

    init(title: String, isCompleted: Bool = false) {
        self.title = title
        self.isCompleted = isCompleted
        self.createdAt = Date()
    }
}

// App setup
@main
struct MyApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
        .modelContainer(for: Todo.self)
    }
}

// Use in views
struct ContentView: View {
    @Environment(\.modelContext) private var context
    @Query private var todos: [Todo]

    var body: some View {
        NavigationStack {
            List {
                ForEach(todos) { todo in
                    HStack {
                        Text(todo.title)
                        Spacer()
                        if todo.isCompleted {
                            Image(systemName: "checkmark")
                        }
                    }
                    .onTapGesture {
                        todo.isCompleted.toggle()
                    }
                }
                .onDelete(perform: deleteTodos)
            }
            .navigationTitle("Todos")
            .toolbar {
                Button("Add") {
                    addTodo()
                }
            }
        }
    }

    func addTodo() {
        let todo = Todo(title: "New Todo")
        context.insert(todo)
    }

    func deleteTodos(at offsets: IndexSet) {
        for index in offsets {
            context.delete(todos[index])
        }
    }
}
```

```
╔════════════════════════════════════════════════════════════╗
║                   CORE DATA (LEGACY)                       ║
╚════════════════════════════════════════════════════════════╝
```

Core Data:

```swift
import CoreData

// Create entity in .xcdatamodeld file first

// Fetch
let fetchRequest: NSFetchRequest<Item> = Item.fetchRequest()
let items = try? context.fetch(fetchRequest)

// Create
let newItem = Item(context: context)
newItem.name = "My Item"
newItem.timestamp = Date()

// Save
try? context.save()

// Delete
context.delete(item)
try? context.save()

// SwiftUI + Core Data
struct ContentView: View {
    @Environment(\.managedObjectContext) private var viewContext

    @FetchRequest(
        sortDescriptors: [NSSortDescriptor(keyPath: \Item.timestamp, ascending: true)],
        animation: .default)
    private var items: FetchedResults<Item>

    var body: some View {
        List {
            ForEach(items) { item in
                Text(item.name ?? "")
            }
            .onDelete(perform: deleteItems)
        }
    }

    func deleteItems(offsets: IndexSet) {
        offsets.map { items[$0] }.forEach(viewContext.delete)
        try? viewContext.save()
    }
}
```

---

<div align="center">

## 📡 Networking

</div>

### Fetch Data from APIs 🌐

```
# ═══════════════════════════════════════════
# NETWORKING IN iOS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   URLSESSION                               ║
╚════════════════════════════════════════════════════════════╝
```

URLSession examples:

```swift
import Foundation

// Model
struct User: Codable, Identifiable {
    let id: Int
    let name: String
    let email: String
}

// API Service
class APIService {
    static let shared = APIService()

    // GET request
    func fetchUsers() async throws -> [User] {
        let url = URL(string: "https://api.example.com/users")!

        let (data, response) = try await URLSession.shared.data(from: url)

        guard let httpResponse = response as? HTTPURLResponse,
              httpResponse.statusCode == 200 else {
            throw URLError(.badServerResponse)
        }

        let users = try JSONDecoder().decode([User].self, from: data)
        return users
    }

    // POST request
    func createUser(name: String, email: String) async throws -> User {
        let url = URL(string: "https://api.example.com/users")!
        var request = URLRequest(url: url)
        request.httpMethod = "POST"
        request.setValue("application/json", forHTTPHeaderField: "Content-Type")

        let body: [String: Any] = ["name": name, "email": email]
        request.httpBody = try JSONSerialization.data(withJSONObject: body)

        let (data, _) = try await URLSession.shared.data(for: request)
        let user = try JSONDecoder().decode(User.self, from: data)
        return user
    }

    // With authentication
    func fetchProtectedData(token: String) async throws -> Data {
        let url = URL(string: "https://api.example.com/protected")!
        var request = URLRequest(url: url)
        request.setValue("Bearer \(token)", forHTTPHeaderField: "Authorization")

        let (data, _) = try await URLSession.shared.data(for: request)
        return data
    }
}

// Usage in SwiftUI
struct UsersView: View {
    @State private var users: [User] = []
    @State private var isLoading = false
    @State private var error: String?

    var body: some View {
        NavigationStack {
            Group {
                if isLoading {
                    ProgressView()
                } else if let error = error {
                    Text("Error: \(error)")
                } else {
                    List(users) { user in
                        VStack(alignment: .leading) {
                            Text(user.name)
                                .font(.headline)
                            Text(user.email)
                                .font(.subheadline)
                                .foregroundColor(.gray)
                        }
                    }
                }
            }
            .navigationTitle("Users")
            .task {
                await loadUsers()
            }
        }
    }

    func loadUsers() async {
        isLoading = true
        error = nil

        do {
            users = try await APIService.shared.fetchUsers()
        } catch {
            self.error = error.localizedDescription
        }

        isLoading = false
    }
}

// Download image
func downloadImage(from urlString: String) async throws -> UIImage? {
    let url = URL(string: urlString)!
    let (data, _) = try await URLSession.shared.data(from: url)
    return UIImage(data: data)
}

// Cached image loading
class ImageCache {
    static let shared = ImageCache()
    private var cache = NSCache<NSString, UIImage>()

    func get(forKey key: String) -> UIImage? {
        return cache.object(forKey: key as NSString)
    }

    func set(_ image: UIImage, forKey key: String) {
        cache.setObject(image, forKey: key as NSString)
    }
}

struct AsyncImageView: View {
    let url: String
    @State private var image: UIImage?

    var body: some View {
        Group {
            if let image = image {
                Image(uiImage: image)
                    .resizable()
                    .scaledToFit()
            } else {
                ProgressView()
            }
        }
        .task {
            await loadImage()
        }
    }

    func loadImage() async {
        // Check cache
        if let cached = ImageCache.shared.get(forKey: url) {
            image = cached
            return
        }

        // Download
        if let downloaded = try? await downloadImage(from: url) {
            ImageCache.shared.set(downloaded, forKey: url)
            image = downloaded
        }
    }
}

// Or use built-in AsyncImage
AsyncImage(url: URL(string: "https://example.com/image.jpg")) { image in
    image
        .resizable()
        .scaledToFit()
} placeholder: {
    ProgressView()
}
.frame(width: 200, height: 200)
```

---

<div align="center">

## 🔧 Core Frameworks

</div>

### iOS System Frameworks 🛠️

```
# ═══════════════════════════════════════════
# CORE iOS FRAMEWORKS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   CORE LOCATION                            ║
╚════════════════════════════════════════════════════════════╝
```

Core Location:

```swift
import CoreLocation

class LocationManager: NSObject, ObservableObject, CLLocationManagerDelegate {
    private let manager = CLLocationManager()
    @Published var location: CLLocation?
    @Published var authorizationStatus: CLAuthorizationStatus?

    override init() {
        super.init()
        manager.delegate = self
    }

    func requestLocation() {
        manager.requestWhenInUseAuthorization()
        manager.startUpdatingLocation()
    }

    func locationManager(_ manager: CLLocationManager, didUpdateLocations locations: [CLLocation]) {
        location = locations.first
    }

    func locationManagerDidChangeAuthorization(_ manager: CLLocationManager) {
        authorizationStatus = manager.authorizationStatus
    }
}

// Usage
struct LocationView: View {
    @StateObject private var locationManager = LocationManager()

    var body: some View {
        VStack {
            if let location = locationManager.location {
                Text("Lat: \(location.coordinate.latitude)")
                Text("Lng: \(location.coordinate.longitude)")
            } else {
                Text("Location unknown")
            }

            Button("Get Location") {
                locationManager.requestLocation()
            }
        }
    }
}

// Info.plist keys needed:
// NSLocationWhenInUseUsageDescription
// NSLocationAlwaysAndWhenInUseUsageDescription
```

```
╔════════════════════════════════════════════════════════════╗
║                   PHOTOKIT (CAMERA/PHOTOS)                 ║
╚════════════════════════════════════════════════════════════╝
```

PhotoPicker:

```swift
import PhotosUI
import SwiftUI

struct PhotoPickerView: View {
    @State private var selectedItem: PhotosPickerItem?
    @State private var selectedImage: Image?

    var body: some View {
        VStack {
            PhotosPicker("Select Photo", selection: $selectedItem, matching: .images)

            if let selectedImage {
                selectedImage
                    .resizable()
                    .scaledToFit()
                    .frame(width: 300, height: 300)
            }
        }
        .onChange(of: selectedItem) { _, newItem in
            Task {
                if let data = try? await newItem?.loadTransferable(type: Data.self),
                   let uiImage = UIImage(data: data) {
                    selectedImage = Image(uiImage: uiImage)
                }
            }
        }
    }
}
```

---

## 🎯 Summary

```
╔════════════════════════════════════════════════════════════╗
║                   QUICK START CHECKLIST                    ║
╚════════════════════════════════════════════════════════════╝

Getting Started:
─────────────────────────────────────────────────────────────
☐ Buy/have a Mac
☐ Install Xcode
☐ Learn Swift basics
☐ Create first app
☐ Run on simulator
☐ Learn SwiftUI
☐ Build real app
☐ Test on device
☐ Submit to App Store

Essential Concepts:
─────────────────────────────────────────────────────────────
✅ Swift language
✅ SwiftUI views
✅ State management (@State, @ObservedObject)
✅ Navigation
✅ Data persistence
✅ Networking
✅ Core frameworks

Recommended Stack:
─────────────────────────────────────────────────────────────
✅ SwiftUI (UI)
✅ SwiftData or Core Data (database)
✅ URLSession (networking)
✅ Combine (reactive)
✅ Firebase (backend)

Remember:
─────────────────────────────────────────────────────────────
"Learn Swift first.
Master SwiftUI.
Follow Apple's HIG.
Test on real devices.
App Store review takes time!"

Now go build amazing iOS apps! 🍎
```

---

<div align="center">

**Built with 🍎 by MrDib, for iOS developers**

_Remember: "Think different!"_ ✨

**Happy iOS Development!** 🚀

</div>

---

## 🔗 Related Guides

- [Swift Programming](../Development/Languages/Swift.md)
- [Mobile Development](./React-Native.md)
- [App Design](../Design-Resources/Design-Galleries.md)
- [Backend Services](../APIs-Services/Backend-Services.md)

---

## 📊 Quick Reference Card

### **Essential Commands:**

```bash
# Build
Cmd + B

# Run
Cmd + R

# Stop
Cmd + .

# Clean
Cmd + Shift + K

# Open quickly
Cmd + Shift + O
```

### **Basic SwiftUI View:**

```swift
import SwiftUI

struct ContentView: View {
    @State private var count = 0

    var body: some View {
        VStack {
            Text("Count: \(count)")
            Button("Tap") {
                count += 1
            }
        }
    }
}

#Preview {
    ContentView()
}
```

### **Common Shortcuts:**

- `Cmd + B` - Build
- `Cmd + R` - Run
- `Cmd + .` - Stop
- `Cmd + /` - Comment
- `Cmd + [` - Indent left
- `Cmd + ]` - Indent right

---
