<div align="center">

# 🦋 Flutter - Beautiful Native Apps! 🦋

![Flutter](https://img.shields.io/badge/Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white)
![Dart](https://img.shields.io/badge/Dart-0175C2?style=for-the-badge&logo=dart&logoColor=white)
![iOS](https://img.shields.io/badge/iOS-000000?style=for-the-badge&logo=ios&logoColor=white)
![Android](https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white)

### _Beautiful apps in record time_ 🚀

**One codebase for iOS, Android, Web, and Desktop!** ✨

</div>

---

## 📚 Table of Contents

- [🎯 What is Flutter](#-what-is-flutter)
- [🚀 Getting Started](#-getting-started)
- [📝 Dart Language Basics](#-dart-language-basics)
- [🧱 Flutter Widgets](#-flutter-widgets)
- [🎨 Material Design & Cupertino](#-material-design--cupertino)
- [📐 Layouts in Flutter](#-layouts-in-flutter)
- [🧭 Navigation & Routing](#-navigation--routing)
- [💾 State Management](#-state-management)
- [📡 Networking & APIs](#-networking--apis)
- [📦 Popular Packages](#-popular-packages)
- [🎬 Animations](#-animations)
- [🔧 Platform Channels](#-platform-channels)
- [🧪 Testing](#-testing)
- [⚡ Performance](#-performance)
- [📲 Building & Deployment](#-building--deployment)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 🎯 What is Flutter

</div>

### Understanding Flutter 🌟

```

# ═══════════════════════════════════════════

# FLUTTER EXPLAINED

# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║ WHAT IS FLUTTER?                                           ║
╚════════════════════════════════════════════════════════════╝

Flutter:
─────────────────────────────────────────────────────────────
A UI toolkit by Google for building natively compiled
applications from a single codebase.

Key Points:
─────────────────────────────────────────────────────────────
✅ Created by Google (2017)
✅ Uses Dart language
✅ Single codebase → iOS, Android, Web, Desktop
✅ Fast performance (compiled to native)
✅ Beautiful UI out of the box
✅ Hot reload (instant updates)
✅ Rich widget library

How It Works:
─────────────────────────────────────────────────────────────

Your Code (Dart)
↓
Flutter Framework (Widgets, Rendering)
↓
Flutter Engine (Skia Graphics)
↓
Platform (iOS/Android Canvas)
↓
📱 Native App

Key Difference from React Native:
─────────────────────────────────────────────────────────────
✅ No bridge needed
✅ Direct compilation to native
✅ Own rendering engine (Skia)
✅ Consistent UI across platforms
✅ Faster performance

╔════════════════════════════════════════════════════════════╗
║ FLUTTER vs REACT NATIVE                                    ║
╚════════════════════════════════════════════════════════════╝

Flutter:
─────────────────────────────────────────────────────────────
✅ Faster performance (no bridge)
✅ Beautiful UI by default
✅ Single rendering engine
✅ Everything is a widget
✅ Better for complex animations
✅ Hot reload super fast
✅ Backed by Google
❌ Dart language (smaller ecosystem than JS)
❌ Larger app size
❌ Less third-party packages

React Native:
─────────────────────────────────────────────────────────────
✅ JavaScript (huge ecosystem)
✅ React skills transfer
✅ More mature (2015 vs 2017)
✅ More third-party libraries
✅ Larger community
❌ Bridge can be bottleneck
❌ Platform-specific bugs
❌ UI consistency issues

╔════════════════════════════════════════════════════════════╗
║ WHY CHOOSE FLUTTER?                                        ║
╚════════════════════════════════════════════════════════════╝

Perfect For:
─────────────────────────────────────────────────────────────
✅ Beautiful UI apps
✅ Cross-platform (Mobile, Web, Desktop)
✅ Complex animations
✅ Need consistent UI
✅ MVP/prototypes
✅ Starting fresh (no JS legacy)
✅ Fast development

Consider React Native If:
─────────────────────────────────────────────────────────────
• Have React developers
• Need JavaScript ecosystem
• Existing React codebase
• More third-party libraries needed

Success Stories:
─────────────────────────────────────────────────────────────
• Google Ads
• Alibaba
• BMW
• eBay Motors
• Reflectly
• Hamilton Musical
• Nubank

╔════════════════════════════════════════════════════════════╗
║ PLATFORMS SUPPORTED                                        ║
╚════════════════════════════════════════════════════════════╝

Stable:
─────────────────────────────────────────────────────────────
✅ iOS
✅ Android
✅ Web

Beta/Stable:
─────────────────────────────────────────────────────────────
✅ Windows
✅ macOS
✅ Linux

Future:
─────────────────────────────────────────────────────────────
• Embedded devices
• IoT
• Smart displays

One Codebase = All Platforms! 🎉

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
║ INSTALLATION                                               ║
╚════════════════════════════════════════════════════════════╝

Prerequisites:
─────────────────────────────────────────────────────────────
• Git
• Xcode (Mac, for iOS)
• Android Studio
• VS Code or Android Studio

macOS Setup:
─────────────────────────────────────────────────────────────

```

Install Flutter on macOS:

```bash
# Download Flutter SDK
cd ~/development
git clone https://github.com/flutter/flutter.git -b stable

# Add to PATH
export PATH="$PATH:`pwd`/flutter/bin"

# Add to ~/.zshrc or ~/.bash_profile permanently
echo 'export PATH="$PATH:$HOME/development/flutter/bin"' >> ~/.zshrc

# Run flutter doctor
flutter doctor

# Install Xcode (from App Store)
# Install CocoaPods
sudo gem install cocoapods

# Install Android Studio
# Download from: https://developer.android.com/studio

# Accept licenses
flutter doctor --android-licenses

# Check everything is setup
flutter doctor -v
```

Windows Setup:

```bash
# Download Flutter SDK from:
# https://docs.flutter.dev/get-started/install/windows

# Extract to C:\src\flutter

# Add to PATH:
# C:\src\flutter\bin

# Install Android Studio
# Download from: https://developer.android.com/studio

# Run flutter doctor
flutter doctor

# Accept licenses
flutter doctor --android-licenses
```

```
╔════════════════════════════════════════════════════════════╗
║                   IDE SETUP                                ║
╚════════════════════════════════════════════════════════════╝

VS Code (Recommended):
─────────────────────────────────────────────────────────────
1. Install VS Code
2. Install Flutter extension
3. Install Dart extension
4. Cmd/Ctrl + Shift + P → "Flutter: New Project"

Android Studio:
─────────────────────────────────────────────────────────────
1. Install Android Studio
2. Plugins → Flutter
3. Plugins → Dart
4. New Flutter Project

╔════════════════════════════════════════════════════════════╗
║                   CREATE FIRST APP                         ║
╚════════════════════════════════════════════════════════════╝
```

Create Flutter app:

```bash
# Create new app
flutter create my_app

# Navigate to app
cd my_app

# Run on iOS simulator (Mac only)
flutter run -d ios

# Run on Android emulator
flutter run -d android

# Run on Chrome (web)
flutter run -d chrome

# List available devices
flutter devices

# Hot reload: Press 'r' in terminal
# Hot restart: Press 'R'
# Quit: Press 'q'
```

```
╔════════════════════════════════════════════════════════════╗
║                   PROJECT STRUCTURE                        ║
╚════════════════════════════════════════════════════════════╝

Typical Structure:
─────────────────────────────────────────────────────────────
```

```
my_app/
├── android/              # Android native code
├── ios/                  # iOS native code
├── lib/                  # Your Dart code
│   ├── main.dart        # Entry point
│   ├── screens/         # Screen widgets
│   ├── widgets/         # Reusable widgets
│   ├── models/          # Data models
│   ├── services/        # API services
│   └── utils/           # Utilities
├── test/                # Unit tests
├── assets/              # Images, fonts, etc.
├── pubspec.yaml         # Dependencies
└── README.md
```

```
╔════════════════════════════════════════════════════════════╗
║                   FIRST FLUTTER APP                        ║
╚════════════════════════════════════════════════════════════╝
```

Hello World App:

```dart
// lib/main.dart
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: MyHomePage(),
    );
  }
}

class MyHomePage extends StatefulWidget {
  @override
  _MyHomePageState createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  int _counter = 0;

  void _incrementCounter() {
    setState(() {
      _counter++;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Flutter Demo'),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Text(
              'You have pushed the button this many times:',
              style: TextStyle(fontSize: 16),
            ),
            Text(
              '$_counter',
              style: Theme.of(context).textTheme.headlineMedium,
            ),
          ],
        ),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: _incrementCounter,
        tooltip: 'Increment',
        child: Icon(Icons.add),
      ),
    );
  }
}
```

---

<div align="center">

## 📝 Dart Language Basics

</div>

### Learn Dart Essentials 💎

```
# ═══════════════════════════════════════════
# DART LANGUAGE BASICS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   DART FUNDAMENTALS                        ║
╚════════════════════════════════════════════════════════════╝

Variables:
─────────────────────────────────────────────────────────────
```

Dart basics:

```dart
void main() {
  // Variables
  var name = 'John';
  String message = 'Hello';
  int age = 30;
  double height = 5.9;
  bool isActive = true;

  // Type inference
  var count = 10; // int
  var price = 19.99; // double

  // Final and const
  final String city = 'Tokyo'; // Runtime constant
  const double PI = 3.14159; // Compile-time constant

  // Nullable variables
  String? nullableName; // Can be null
  int? nullableAge;

  // Late initialization
  late String description;
  description = 'Hello World';

  // Lists
  List<String> fruits = ['Apple', 'Banana', 'Orange'];
  var numbers = [1, 2, 3, 4, 5];

  // Maps
  Map<String, int> scores = {
    'John': 90,
    'Jane': 95,
  };

  // Sets
  Set<String> colors = {'Red', 'Green', 'Blue'};

  // Functions
  print(add(5, 3)); // 8
  print(greet('World')); // Hello, World!

  // Arrow functions
  int multiply(int a, int b) => a * b;

  // Anonymous functions
  var list = [1, 2, 3];
  list.forEach((item) {
    print(item);
  });

  // String interpolation
  String firstName = 'John';
  String lastName = 'Doe';
  print('Full name: $firstName $lastName');
  print('Length: ${firstName.length}');
}

// Function declarations
int add(int a, int b) {
  return a + b;
}

String greet(String name) {
  return 'Hello, $name!';
}

// Optional parameters
void sayHello(String name, [String? greeting]) {
  print('${greeting ?? 'Hello'}, $name');
}

// Named parameters
void createUser({
  required String name,
  required int age,
  String? email,
}) {
  print('Name: $name, Age: $age');
}

// Usage
sayHello('John');
sayHello('John', 'Hi');
createUser(name: 'John', age: 30);
```

```
Classes:
─────────────────────────────────────────────────────────────
```

Dart classes:

```dart
// Basic class
class Person {
  String name;
  int age;

  // Constructor
  Person(this.name, this.age);

  // Named constructor
  Person.guest() : name = 'Guest', age = 0;

  // Method
  void introduce() {
    print('Hi, I\'m $name and I\'m $age years old.');
  }

  // Getter
  String get description => '$name ($age)';

  // Setter
  set updateAge(int newAge) {
    if (newAge > 0) age = newAge;
  }
}

// Usage
var person = Person('John', 30);
person.introduce();

var guest = Person.guest();

// Inheritance
class Student extends Person {
  String school;

  Student(String name, int age, this.school) : super(name, age);

  @override
  void introduce() {
    print('Hi, I\'m $name, I study at $school.');
  }
}

// Abstract class
abstract class Animal {
  void makeSound(); // Abstract method

  void sleep() {
    print('Sleeping...');
  }
}

class Dog extends Animal {
  @override
  void makeSound() {
    print('Woof!');
  }
}

// Mixins
mixin Swimming {
  void swim() {
    print('Swimming...');
  }
}

class Fish extends Animal with Swimming {
  @override
  void makeSound() {
    print('Blub blub');
  }
}

// Interfaces
class Flyable {
  void fly() {}
}

class Bird extends Animal implements Flyable {
  @override
  void makeSound() {
    print('Chirp!');
  }

  @override
  void fly() {
    print('Flying...');
  }
}
```

```
Async/Await:
─────────────────────────────────────────────────────────────
```

Async programming:

```dart
import 'dart:async';
import 'dart:convert';
import 'package:http/http.dart' as http;

// Future
Future<String> fetchData() async {
  await Future.delayed(Duration(seconds: 2));
  return 'Data loaded';
}

// Usage
void main() async {
  print('Fetching...');
  String data = await fetchData();
  print(data);
}

// HTTP request
Future<Map<String, dynamic>> fetchUser(int id) async {
  final response = await http.get(
    Uri.parse('https://api.example.com/users/$id'),
  );

  if (response.statusCode == 200) {
    return jsonDecode(response.body);
  } else {
    throw Exception('Failed to load user');
  }
}

// Stream
Stream<int> countStream() async* {
  for (int i = 1; i <= 5; i++) {
    await Future.delayed(Duration(seconds: 1));
    yield i;
  }
}

// Listen to stream
void listenToStream() {
  countStream().listen((value) {
    print(value);
  });
}

// StreamBuilder in Flutter
StreamBuilder<int>(
  stream: countStream(),
  builder: (context, snapshot) {
    if (snapshot.hasData) {
      return Text('${snapshot.data}');
    }
    return CircularProgressIndicator();
  },
);
```

---

<div align="center">

## 🧱 Flutter Widgets

</div>

### Everything is a Widget! 📦

```
# ═══════════════════════════════════════════
# FLUTTER WIDGETS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   STATELESS vs STATEFUL                    ║
╚════════════════════════════════════════════════════════════╝

Stateless Widget:
─────────────────────────────────────────────────────────────
Immutable, doesn't change
```

Stateless widget:

```dart
class MyStatelessWidget extends StatelessWidget {
  final String title;

  const MyStatelessWidget({Key? key, required this.title}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Container(
      child: Text(title),
    );
  }
}

// Usage
MyStatelessWidget(title: 'Hello World')
```

Stateful widget:

```dart
class MyStatefulWidget extends StatefulWidget {
  const MyStatefulWidget({Key? key}) : super(key: key);

  @override
  State<MyStatefulWidget> createState() => _MyStatefulWidgetState();
}

class _MyStatefulWidgetState extends State<MyStatefulWidget> {
  int _counter = 0;

  void _incrementCounter() {
    setState(() {
      _counter++;
    });
  }

  @override
  void initState() {
    super.initState();
    // Called when widget is inserted
    print('Widget initialized');
  }

  @override
  void dispose() {
    // Called when widget is removed
    print('Widget disposed');
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        Text('Count: $_counter'),
        ElevatedButton(
          onPressed: _incrementCounter,
          child: Text('Increment'),
        ),
      ],
    );
  }
}
```

```
╔════════════════════════════════════════════════════════════╗
║                   BASIC WIDGETS                            ║
╚════════════════════════════════════════════════════════════╝

Container:
─────────────────────────────────────────────────────────────
```

Common widgets:

```dart
// Container
Container(
  width: 200,
  height: 100,
  padding: EdgeInsets.all(16),
  margin: EdgeInsets.symmetric(horizontal: 20),
  decoration: BoxDecoration(
    color: Colors.blue,
    borderRadius: BorderRadius.circular(8),
    boxShadow: [
      BoxShadow(
        color: Colors.grey.withOpacity(0.5),
        spreadRadius: 2,
        blurRadius: 5,
      ),
    ],
  ),
  child: Text('Hello'),
)

// Text
Text(
  'Hello World',
  style: TextStyle(
    fontSize: 24,
    fontWeight: FontWeight.bold,
    color: Colors.blue,
  ),
)

// Image
Image.network('https://example.com/image.jpg')
Image.asset('assets/images/logo.png')
Image.file(File('/path/to/image.jpg'))

// Icon
Icon(Icons.favorite, color: Colors.red, size: 30)

// Button variants
ElevatedButton(
  onPressed: () => print('Pressed'),
  child: Text('Elevated Button'),
)

TextButton(
  onPressed: () => print('Pressed'),
  child: Text('Text Button'),
)

OutlinedButton(
  onPressed: () => print('Pressed'),
  child: Text('Outlined Button'),
)

IconButton(
  icon: Icon(Icons.add),
  onPressed: () => print('Pressed'),
)

FloatingActionButton(
  onPressed: () => print('Pressed'),
  child: Icon(Icons.add),
)

// TextField
TextField(
  decoration: InputDecoration(
    labelText: 'Name',
    hintText: 'Enter your name',
    border: OutlineInputBorder(),
    prefixIcon: Icon(Icons.person),
  ),
  onChanged: (value) => print(value),
)

// Checkbox
Checkbox(
  value: true,
  onChanged: (bool? value) {},
)

// Radio
Radio<int>(
  value: 1,
  groupValue: selectedValue,
  onChanged: (int? value) {},
)

// Switch
Switch(
  value: true,
  onChanged: (bool value) {},
)

// Slider
Slider(
  value: 50,
  min: 0,
  max: 100,
  onChanged: (double value) {},
)
```

```
╔════════════════════════════════════════════════════════════╗
║                   SCAFFOLD                                 ║
╚════════════════════════════════════════════════════════════╝

Basic Screen Structure:
─────────────────────────────────────────────────────────────
```

Scaffold widget:

```dart
Scaffold(
  appBar: AppBar(
    title: Text('My App'),
    actions: [
      IconButton(
        icon: Icon(Icons.search),
        onPressed: () {},
      ),
      IconButton(
        icon: Icon(Icons.more_vert),
        onPressed: () {},
      ),
    ],
  ),

  body: Center(
    child: Text('Hello World'),
  ),

  floatingActionButton: FloatingActionButton(
    onPressed: () {},
    child: Icon(Icons.add),
  ),

  drawer: Drawer(
    child: ListView(
      children: [
        DrawerHeader(
          decoration: BoxDecoration(color: Colors.blue),
          child: Text('Menu'),
        ),
        ListTile(
          leading: Icon(Icons.home),
          title: Text('Home'),
          onTap: () {},
        ),
        ListTile(
          leading: Icon(Icons.settings),
          title: Text('Settings'),
          onTap: () {},
        ),
      ],
    ),
  ),

  bottomNavigationBar: BottomNavigationBar(
    currentIndex: 0,
    items: [
      BottomNavigationBarItem(
        icon: Icon(Icons.home),
        label: 'Home',
      ),
      BottomNavigationBarItem(
        icon: Icon(Icons.search),
        label: 'Search',
      ),
      BottomNavigationBarItem(
        icon: Icon(Icons.person),
        label: 'Profile',
      ),
    ],
    onTap: (index) {},
  ),
)
```

```
╔════════════════════════════════════════════════════════════╗
║                   LISTVIEW                                 ║
╚════════════════════════════════════════════════════════════╝
```

ListView examples:

```dart
// Simple ListView
ListView(
  children: [
    ListTile(title: Text('Item 1')),
    ListTile(title: Text('Item 2')),
    ListTile(title: Text('Item 3')),
  ],
)

// ListView.builder (for large lists)
ListView.builder(
  itemCount: items.length,
  itemBuilder: (context, index) {
    return ListTile(
      leading: CircleAvatar(
        child: Text('${index + 1}'),
      ),
      title: Text(items[index].title),
      subtitle: Text(items[index].subtitle),
      trailing: Icon(Icons.arrow_forward),
      onTap: () {
        print('Tapped item $index');
      },
    );
  },
)

// ListView.separated (with separators)
ListView.separated(
  itemCount: items.length,
  separatorBuilder: (context, index) => Divider(),
  itemBuilder: (context, index) {
    return ListTile(
      title: Text(items[index]),
    );
  },
)

// Horizontal ListView
ListView(
  scrollDirection: Axis.horizontal,
  children: [
    Container(width: 150, color: Colors.red),
    Container(width: 150, color: Colors.blue),
    Container(width: 150, color: Colors.green),
  ],
)

// GridView
GridView.builder(
  gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
    crossAxisCount: 2,
    crossAxisSpacing: 10,
    mainAxisSpacing: 10,
    childAspectRatio: 1,
  ),
  itemCount: items.length,
  itemBuilder: (context, index) {
    return Card(
      child: Center(
        child: Text(items[index]),
      ),
    );
  },
)
```

---

<div align="center">

## 🎨 Material Design & Cupertino

</div>

### Platform-Specific UI 📱

```
# ═══════════════════════════════════════════
# MATERIAL DESIGN & CUPERTINO
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   MATERIAL DESIGN (ANDROID)                ║
╚════════════════════════════════════════════════════════════╝
```

Material Design:

```dart
import 'package:flutter/material.dart';

MaterialApp(
  theme: ThemeData(
    primarySwatch: Colors.blue,
    brightness: Brightness.light,
    textTheme: TextTheme(
      headlineLarge: TextStyle(fontSize: 32, fontWeight: FontWeight.bold),
    ),
  ),
  home: Scaffold(
    appBar: AppBar(
      title: Text('Material Design'),
    ),
    body: Column(
      children: [
        Card(
          elevation: 4,
          child: Padding(
            padding: EdgeInsets.all(16),
            child: Text('Material Card'),
          ),
        ),
        ElevatedButton(
          onPressed: () {},
          child: Text('Material Button'),
        ),
      ],
    ),
  ),
)
```

```
╔════════════════════════════════════════════════════════════╗
║                   CUPERTINO (iOS)                          ║
╚════════════════════════════════════════════════════════════╝
```

Cupertino design:

```dart
import 'package:flutter/cupertino.dart';

CupertinoApp(
  theme: CupertinoThemeData(
    primaryColor: CupertinoColors.activeBlue,
  ),
  home: CupertinoPageScaffold(
    navigationBar: CupertinoNavigationBar(
      middle: Text('Cupertino Design'),
    ),
    child: Center(
      child: Column(
        mainAxisAlignment: MainAxisAlignment.center,
        children: [
          CupertinoButton(
            color: CupertinoColors.activeBlue,
            onPressed: () {},
            child: Text('iOS Button'),
          ),
          CupertinoSwitch(
            value: true,
            onChanged: (value) {},
          ),
          CupertinoActivityIndicator(),
        ],
      ),
    ),
  ),
)
```

```
╔════════════════════════════════════════════════════════════╗
║                   PLATFORM-ADAPTIVE WIDGETS                ║
╚════════════════════════════════════════════════════════════╝
```

Adaptive widgets:

```dart
import 'dart:io';

Widget buildButton(String text, VoidCallback onPressed) {
  if (Platform.isIOS) {
    return CupertinoButton(
      child: Text(text),
      onPressed: onPressed,
    );
  } else {
    return ElevatedButton(
      child: Text(text),
      onPressed: onPressed,
    );
  }
}

// Or use Platform.select
Widget adaptiveButton() {
  return Platform.isIOS
    ? CupertinoButton(child: Text('iOS'), onPressed: () {})
    : ElevatedButton(child: Text('Android'), onPressed: () {});
}

// Alert Dialog
void showAdaptiveDialog(BuildContext context) {
  if (Platform.isIOS) {
    showCupertinoDialog(
      context: context,
      builder: (context) => CupertinoAlertDialog(
        title: Text('Alert'),
        content: Text('This is an iOS alert'),
        actions: [
          CupertinoDialogAction(
            child: Text('OK'),
            onPressed: () => Navigator.pop(context),
          ),
        ],
      ),
    );
  } else {
    showDialog(
      context: context,
      builder: (context) => AlertDialog(
        title: Text('Alert'),
        content: Text('This is an Android alert'),
        actions: [
          TextButton(
            child: Text('OK'),
            onPressed: () => Navigator.pop(context),
          ),
        ],
      ),
    );
  }
}
```

---

<div align="center">

## 📐 Layouts in Flutter

</div>

### Position Your Widgets 🎯

```
# ═══════════════════════════════════════════
# LAYOUTS IN FLUTTER
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   COLUMN & ROW                             ║
╚════════════════════════════════════════════════════════════╝
```

Column and Row:

```dart
// Column (vertical)
Column(
  mainAxisAlignment: MainAxisAlignment.center, // vertical
  crossAxisAlignment: CrossAxisAlignment.start, // horizontal
  children: [
    Text('Item 1'),
    Text('Item 2'),
    Text('Item 3'),
  ],
)

// Row (horizontal)
Row(
  mainAxisAlignment: MainAxisAlignment.spaceBetween, // horizontal
  crossAxisAlignment: CrossAxisAlignment.center, // vertical
  children: [
    Icon(Icons.star),
    Text('5.0'),
    Text('(123 reviews)'),
  ],
)

// Expanded (take available space)
Row(
  children: [
    Expanded(
      flex: 2,
      child: Container(color: Colors.red),
    ),
    Expanded(
      flex: 1,
      child: Container(color: Colors.blue),
    ),
  ],
)

// Flexible
Row(
  children: [
    Flexible(
      flex: 1,
      child: Container(color: Colors.red),
    ),
    Flexible(
      flex: 2,
      child: Container(color: Colors.blue),
    ),
  ],
)
```

```
╔════════════════════════════════════════════════════════════╗
║                   STACK                                    ║
╚════════════════════════════════════════════════════════════╝
```

Stack (overlay widgets):

```dart
Stack(
  children: [
    // Background
    Container(
      width: 200,
      height: 200,
      color: Colors.blue,
    ),

    // Positioned widget
    Positioned(
      top: 20,
      left: 20,
      child: Text('Top Left'),
    ),

    Positioned(
      bottom: 20,
      right: 20,
      child: Icon(Icons.star),
    ),

    // Centered
    Center(
      child: Text('Centered'),
    ),
  ],
)

// Example: Badge on icon
Stack(
  children: [
    Icon(Icons.shopping_cart, size: 40),
    Positioned(
      right: 0,
      top: 0,
      child: Container(
        padding: EdgeInsets.all(4),
        decoration: BoxDecoration(
          color: Colors.red,
          shape: BoxShape.circle,
        ),
        child: Text('3', style: TextStyle(color: Colors.white)),
      ),
    ),
  ],
)
```

```
╔════════════════════════════════════════════════════════════╗
║                   PADDING & ALIGNMENT                      ║
╚════════════════════════════════════════════════════════════╝
```

Padding and Alignment:

```dart
// Padding
Padding(
  padding: EdgeInsets.all(16),
  child: Text('Padded'),
)

Padding(
  padding: EdgeInsets.symmetric(horizontal: 20, vertical: 10),
  child: Text('Custom padding'),
)

Padding(
  padding: EdgeInsets.only(left: 20, top: 10),
  child: Text('Specific sides'),
)

// Alignment
Align(
  alignment: Alignment.topRight,
  child: Text('Top Right'),
)

Center(
  child: Text('Centered'),
)

// SizedBox (spacing)
Column(
  children: [
    Text('Item 1'),
    SizedBox(height: 20), // Vertical space
    Text('Item 2'),
  ],
)

Row(
  children: [
    Text('Item 1'),
    SizedBox(width: 20), // Horizontal space
    Text('Item 2'),
  ],
)
```

```
╔════════════════════════════════════════════════════════════╗
║                   WRAP                                     ║
╚════════════════════════════════════════════════════════════╝
```

Wrap (flowing layout):

```dart
Wrap(
  spacing: 8, // Horizontal spacing
  runSpacing: 8, // Vertical spacing
  children: [
    Chip(label: Text('Flutter')),
    Chip(label: Text('Dart')),
    Chip(label: Text('Mobile')),
    Chip(label: Text('Development')),
    Chip(label: Text('iOS')),
    Chip(label: Text('Android')),
  ],
)
```

---

<div align="center">

## 🧭 Navigation & Routing

</div>

### Navigate Between Screens 🗺️

```
# ═══════════════════════════════════════════
# NAVIGATION & ROUTING
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   BASIC NAVIGATION                         ║
╚════════════════════════════════════════════════════════════╝
```

Push and pop navigation:

```dart
// Navigate to new screen
Navigator.push(
  context,
  MaterialPageRoute(builder: (context) => SecondScreen()),
);

// Navigate back
Navigator.pop(context);

// Navigate with data
Navigator.push(
  context,
  MaterialPageRoute(
    builder: (context) => DetailScreen(item: selectedItem),
  ),
);

// Pop with result
// In DetailScreen:
Navigator.pop(context, 'Result data');

// In HomeScreen:
final result = await Navigator.push(
  context,
  MaterialPageRoute(builder: (context) => DetailScreen()),
);
print(result); // 'Result data'

// Replace current screen
Navigator.pushReplacement(
  context,
  MaterialPageRoute(builder: (context) => HomeScreen()),
);

// Remove all and push
Navigator.pushAndRemoveUntil(
  context,
  MaterialPageRoute(builder: (context) => LoginScreen()),
  (route) => false, // Remove all previous routes
);
```

```
╔════════════════════════════════════════════════════════════╗
║                   NAMED ROUTES                             ║
╚════════════════════════════════════════════════════════════╝
```

Named routes:

```dart
// Define routes in MaterialApp
MaterialApp(
  initialRoute: '/',
  routes: {
    '/': (context) => HomeScreen(),
    '/details': (context) => DetailsScreen(),
    '/settings': (context) => SettingsScreen(),
  },
)

// Navigate using named routes
Navigator.pushNamed(context, '/details');

// With arguments
Navigator.pushNamed(
  context,
  '/details',
  arguments: {'id': 123, 'title': 'Item'},
);

// Receive arguments
class DetailsScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    final args = ModalRoute.of(context)!.settings.arguments as Map<String, dynamic>;
    final id = args['id'];
    final title = args['title'];

    return Scaffold(
      appBar: AppBar(title: Text(title)),
      body: Text('ID: $id'),
    );
  }
}

// OnGenerateRoute (advanced)
MaterialApp(
  onGenerateRoute: (settings) {
    if (settings.name == '/details') {
      final args = settings.arguments as Map<String, dynamic>;
      return MaterialPageRoute(
        builder: (context) => DetailsScreen(
          id: args['id'],
          title: args['title'],
        ),
      );
    }
    return null;
  },
)
```

```
╔════════════════════════════════════════════════════════════╗
║                   GO_ROUTER (RECOMMENDED)                  ║
╚════════════════════════════════════════════════════════════╝
```

go_router package:

```yaml
# pubspec.yaml
dependencies:
  go_router: ^13.0.0
```

```dart
import 'package:go_router/go_router.dart';

// Define routes
final router = GoRouter(
  routes: [
    GoRoute(
      path: '/',
      builder: (context, state) => HomeScreen(),
    ),
    GoRoute(
      path: '/details/:id',
      builder: (context, state) {
        final id = state.pathParameters['id']!;
        return DetailsScreen(id: id);
      },
    ),
    GoRoute(
      path: '/user/:userId/post/:postId',
      builder: (context, state) {
        final userId = state.pathParameters['userId']!;
        final postId = state.pathParameters['postId']!;
        return PostScreen(userId: userId, postId: postId);
      },
    ),
  ],
);

// Use in MaterialApp
MaterialApp.router(
  routerConfig: router,
)

// Navigate
context.go('/details/123');
context.push('/settings');
context.pop();

// With query parameters
context.go('/search?q=flutter');

// Access query parameters
final query = state.uri.queryParameters['q'];
```

---

<div align="center">

## 💾 State Management

</div>

### Manage Your App State 🗂️

```
# ═══════════════════════════════════════════
# STATE MANAGEMENT
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   PROVIDER (RECOMMENDED)                   ║
╚════════════════════════════════════════════════════════════╝
```

Provider:

```yaml
# pubspec.yaml
dependencies:
  provider: ^6.1.0
```

```dart
import 'package:provider/provider.dart';

// 1. Create a model
class Counter with ChangeNotifier {
  int _count = 0;

  int get count => _count;

  void increment() {
    _count++;
    notifyListeners(); // Notify widgets to rebuild
  }

  void decrement() {
    _count--;
    notifyListeners();
  }
}

// 2. Provide the model
void main() {
  runApp(
    ChangeNotifierProvider(
      create: (context) => Counter(),
      child: MyApp(),
    ),
  );
}

// Multiple providers
void main() {
  runApp(
    MultiProvider(
      providers: [
        ChangeNotifierProvider(create: (context) => Counter()),
        ChangeNotifierProvider(create: (context) => AuthService()),
        Provider(create: (context) => ApiService()),
      ],
      child: MyApp(),
    ),
  );
}

// 3. Consume the model
class HomeScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    // Watch for changes
    final counter = context.watch<Counter>();

    return Scaffold(
      body: Center(
        child: Text('Count: ${counter.count}'),
      ),
      floatingActionButton: FloatingActionButton(
        onPress: () {
          // Read without watching
          context.read<Counter>().increment();
        },
        child: Icon(Icons.add),
      ),
    );
  }
}

// Consumer widget (partial rebuild)
Consumer<Counter>(
  builder: (context, counter, child) {
    return Text('${counter.count}');
  },
)

// Selector (rebuild only when specific value changes)
Selector<Counter, int>(
  selector: (context, counter) => counter.count,
  builder: (context, count, child) {
    return Text('$count');
  },
)
```

```
╔════════════════════════════════════════════════════════════╗
║                   RIVERPOD (MODERN PROVIDER)               ║
╚════════════════════════════════════════════════════════════╝
```

Riverpod:

```yaml
dependencies:
  flutter_riverpod: ^2.4.0
```

```dart
import 'package:flutter_riverpod/flutter_riverpod.dart';

// 1. Create providers
final counterProvider = StateNotifierProvider<CounterNotifier, int>((ref) {
  return CounterNotifier();
});

class CounterNotifier extends StateNotifier<int> {
  CounterNotifier() : super(0);

  void increment() => state++;
  void decrement() => state--;
}

// Simple provider
final helloWorldProvider = Provider((ref) => 'Hello World');

// Future provider
final userProvider = FutureProvider((ref) async {
  final response = await http.get(Uri.parse('api/user'));
  return User.fromJson(jsonDecode(response.body));
});

// 2. Wrap app
void main() {
  runApp(
    ProviderScope(
      child: MyApp(),
    ),
  );
}

// 3. Consume
class HomeScreen extends ConsumerWidget {
  @override
  Widget build(BuildContext context, WidgetRef ref) {
    final counter = ref.watch(counterProvider);

    return Scaffold(
      body: Center(
        child: Text('Count: $counter'),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: () {
          ref.read(counterProvider.notifier).increment();
        },
        child: Icon(Icons.add),
      ),
    );
  }
}

// Or use Consumer
Consumer(
  builder: (context, ref, child) {
    final counter = ref.watch(counterProvider);
    return Text('$counter');
  },
)
```

```
╔════════════════════════════════════════════════════════════╗
║                   BLOC                                     ║
╚════════════════════════════════════════════════════════════╝
```

BLoC pattern:

```yaml
dependencies:
  flutter_bloc: ^8.1.3
```

```dart
import 'package:flutter_bloc/flutter_bloc.dart';

// 1. Define events
abstract class CounterEvent {}

class IncrementEvent extends CounterEvent {}
class DecrementEvent extends CounterEvent {}

// 2. Define states
class CounterState {
  final int count;
  CounterState(this.count);
}

// 3. Create Bloc
class CounterBloc extends Bloc<CounterEvent, CounterState> {
  CounterBloc() : super(CounterState(0)) {
    on<IncrementEvent>((event, emit) {
      emit(CounterState(state.count + 1));
    });

    on<DecrementEvent>((event, emit) {
      emit(CounterState(state.count - 1));
    });
  }
}

// 4. Provide Bloc
BlocProvider(
  create: (context) => CounterBloc(),
  child: HomeScreen(),
)

// 5. Consume
BlocBuilder<CounterBloc, CounterState>(
  builder: (context, state) {
    return Text('${state.count}');
  },
)

// Dispatch events
context.read<CounterBloc>().add(IncrementEvent());
```

```
╔════════════════════════════════════════════════════════════╗
║                   GETX (ALL-IN-ONE)                        ║
╚════════════════════════════════════════════════════════════╝
```

GetX:

```yaml
dependencies:
  get: ^4.6.6
```

```dart
import 'package:get/get.dart';

// 1. Create controller
class CounterController extends GetxController {
  var count = 0.obs; // Observable

  void increment() => count++;
  void decrement() => count--;
}

// 2. Use GetMaterialApp
GetMaterialApp(
  home: HomeScreen(),
)

// 3. Consume
class HomeScreen extends StatelessWidget {
  final CounterController controller = Get.put(CounterController());

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Obx(() => Text('${controller.count}')),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: controller.increment,
        child: Icon(Icons.add),
      ),
    );
  }
}

// Navigation
Get.to(NextScreen());
Get.back();
Get.off(NextScreen()); // Replace
Get.offAll(HomeScreen()); // Clear all

// Snackbar
Get.snackbar('Title', 'Message');

// Dialog
Get.defaultDialog(title: 'Title', middleText: 'Content');
```

---

<div align="center">

## 📡 Networking & APIs

</div>

### Fetch Data from APIs 🌐

```
# ═══════════════════════════════════════════
# NETWORKING & APIs
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   HTTP PACKAGE                             ║
╚════════════════════════════════════════════════════════════╝
```

HTTP requests:

```yaml
dependencies:
  http: ^1.1.0
```

```dart
import 'package:http/http.dart' as http;
import 'dart:convert';

// GET request
Future<List<User>> fetchUsers() async {
  final response = await http.get(
    Uri.parse('https://api.example.com/users'),
  );

  if (response.statusCode == 200) {
    List<dynamic> body = jsonDecode(response.body);
    List<User> users = body.map((json) => User.fromJson(json)).toList();
    return users;
  } else {
    throw Exception('Failed to load users');
  }
}

// POST request
Future<User> createUser(String name, String email) async {
  final response = await http.post(
    Uri.parse('https://api.example.com/users'),
    headers: {'Content-Type': 'application/json'},
    body: jsonEncode({
      'name': name,
      'email': email,
    }),
  );

  if (response.statusCode == 201) {
    return User.fromJson(jsonDecode(response.body));
  } else {
    throw Exception('Failed to create user');
  }
}

// PUT request
Future<User> updateUser(int id, String name) async {
  final response = await http.put(
    Uri.parse('https://api.example.com/users/$id'),
    headers: {'Content-Type': 'application/json'},
    body: jsonEncode({'name': name}),
  );

  return User.fromJson(jsonDecode(response.body));
}

// DELETE request
Future<void> deleteUser(int id) async {
  final response = await http.delete(
    Uri.parse('https://api.example.com/users/$id'),
  );

  if (response.statusCode != 200) {
    throw Exception('Failed to delete user');
  }
}

// With authorization
Future<void> fetchProtectedData(String token) async {
  final response = await http.get(
    Uri.parse('https://api.example.com/protected'),
    headers: {
      'Authorization': 'Bearer $token',
      'Content-Type': 'application/json',
    },
  );
}

// Model class
class User {
  final int id;
  final String name;
  final String email;

  User({required this.id, required this.name, required this.email});

  factory User.fromJson(Map<String, dynamic> json) {
    return User(
      id: json['id'],
      name: json['name'],
      email: json['email'],
    );
  }

  Map<String, dynamic> toJson() {
    return {
      'id': id,
      'name': name,
      'email': email,
    };
  }
}

// Usage in widget
class UsersScreen extends StatefulWidget {
  @override
  _UsersScreenState createState() => _UsersScreenState();
}

class _UsersScreenState extends State<UsersScreen> {
  late Future<List<User>> futureUsers;

  @override
  void initState() {
    super.initState();
    futureUsers = fetchUsers();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Users')),
      body: FutureBuilder<List<User>>(
        future: futureUsers,
        builder: (context, snapshot) {
          if (snapshot.hasData) {
            return ListView.builder(
              itemCount: snapshot.data!.length,
              itemBuilder: (context, index) {
                final user = snapshot.data![index];
                return ListTile(
                  title: Text(user.name),
                  subtitle: Text(user.email),
                );
              },
            );
          } else if (snapshot.hasError) {
            return Center(child: Text('Error: ${snapshot.error}'));
          }

          return Center(child: CircularProgressIndicator());
        },
      ),
    );
  }
}
```

```
╔════════════════════════════════════════════════════════════╗
║                   DIO (ADVANCED HTTP)                      ║
╚════════════════════════════════════════════════════════════╝
```

Dio package:

```yaml
dependencies:
  dio: ^5.4.0
```

```dart
import 'package:dio/dio.dart';

// Create Dio instance
final dio = Dio(BaseOptions(
  baseUrl: 'https://api.example.com',
  connectTimeout: Duration(seconds: 5),
  receiveTimeout: Duration(seconds: 3),
  headers: {
    'Content-Type': 'application/json',
  },
));

// Interceptors
dio.interceptors.add(InterceptorsWrapper(
  onRequest: (options, handler) {
    // Add token
    options.headers['Authorization'] = 'Bearer $token';
    return handler.next(options);
  },
  onResponse: (response, handler) {
    print('Response: ${response.data}');
    return handler.next(response);
  },
  onError: (DioException e, handler) {
    print('Error: ${e.message}');
    return handler.next(e);
  },
));

// GET
Future<List<User>> getUsers() async {
  try {
    final response = await dio.get('/users');
    return (response.data as List)
        .map((json) => User.fromJson(json))
        .toList();
  } on DioException catch (e) {
    throw Exception('Failed: ${e.message}');
  }
}

// POST
Future<User> createUser(User user) async {
  final response = await dio.post('/users', data: user.toJson());
  return User.fromJson(response.data);
}

// Upload file
Future<void> uploadFile(File file) async {
  FormData formData = FormData.fromMap({
    'file': await MultipartFile.fromFile(file.path, filename: 'upload.jpg'),
  });

  await dio.post('/upload', data: formData);
}

// Download file
await dio.download(
  'https://example.com/file.pdf',
  '/path/to/save/file.pdf',
  onReceiveProgress: (received, total) {
    print('${(received / total * 100).toStringAsFixed(0)}%');
  },
);
```

---

<div align="center">

## 📦 Popular Packages

</div>

### Essential Flutter Packages 🎁

```
# ═══════════════════════════════════════════
# POPULAR PACKAGES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   MUST-HAVE PACKAGES                       ║
╚════════════════════════════════════════════════════════════╝
```

| Package                  | Purpose                 | Link                                  |
| ------------------------ | ----------------------- | ------------------------------------- |
| **provider**             | State management        | pub.dev/packages/provider             |
| **riverpod**             | Modern state management | pub.dev/packages/flutter_riverpod     |
| **go_router**            | Routing                 | pub.dev/packages/go_router            |
| **dio**                  | HTTP client             | pub.dev/packages/dio                  |
| **shared_preferences**   | Local storage           | pub.dev/packages/shared_preferences   |
| **sqflite**              | SQLite database         | pub.dev/packages/sqflite              |
| **hive**                 | Fast local database     | pub.dev/packages/hive                 |
| **cached_network_image** | Image caching           | pub.dev/packages/cached_network_image |
| **image_picker**         | Image selection         | pub.dev/packages/image_picker         |
| **google_maps_flutter**  | Maps                    | pub.dev/packages/google_maps_flutter  |
| **firebase_core**        | Firebase                | pub.dev/packages/firebase_core        |
| **fl_chart**             | Charts                  | pub.dev/packages/fl_chart             |
| **intl**                 | Internationalization    | pub.dev/packages/intl                 |
| **url_launcher**         | Open URLs               | pub.dev/packages/url_launcher         |
| **permission_handler**   | Permissions             | pub.dev/packages/permission_handler   |

```
╔════════════════════════════════════════════════════════════╗
║                   SHARED PREFERENCES                       ║
╚════════════════════════════════════════════════════════════╝
```

Local storage:

```yaml
dependencies:
  shared_preferences: ^2.2.2
```

```dart
import 'package:shared_preferences/shared_preferences.dart';

// Save data
Future<void> saveData() async {
  final prefs = await SharedPreferences.getInstance();

  await prefs.setString('username', 'John');
  await prefs.setInt('age', 30);
  await prefs.setBool('isLoggedIn', true);
  await prefs.setStringList('favorites', ['item1', 'item2']);
}

// Read data
Future<String?> getUsername() async {
  final prefs = await SharedPreferences.getInstance();
  return prefs.getString('username');
}

// Remove data
Future<void> removeData() async {
  final prefs = await SharedPreferences.getInstance();
  await prefs.remove('username');
}

// Clear all
Future<void> clearAll() async {
  final prefs = await SharedPreferences.getInstance();
  await prefs.clear();
}
```

```
╔════════════════════════════════════════════════════════════╗
║                   IMAGE PICKER                             ║
╚════════════════════════════════════════════════════════════╝
```

Image picker:

```yaml
dependencies:
  image_picker: ^1.0.5
```

```dart
import 'package:image_picker/image_picker.dart';
import 'dart:io';

final ImagePicker picker = ImagePicker();

// Pick from gallery
Future<File?> pickImageFromGallery() async {
  final XFile? image = await picker.pickImage(source: ImageSource.gallery);

  if (image != null) {
    return File(image.path);
  }
  return null;
}

// Take photo
Future<File?> takePhoto() async {
  final XFile? photo = await picker.pickImage(source: ImageSource.camera);

  if (photo != null) {
    return File(photo.path);
  }
  return null;
}

// Usage in widget
class ImagePickerScreen extends StatefulWidget {
  @override
  _ImagePickerScreenState createState() => _ImagePickerScreenState();
}

class _ImagePickerScreenState extends State<ImagePickerScreen> {
  File? _image;

  Future<void> _pickImage() async {
    final image = await pickImageFromGallery();
    setState(() {
      _image = image;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Column(
          children: [
            if (_image != null)
              Image.file(_image!, width: 200, height: 200),
            ElevatedButton(
              onPressed: _pickImage,
              child: Text('Pick Image'),
            ),
          ],
        ),
      ),
    );
  }
}
```

---

<div align="center">

## 🎬 Animations

</div>

### Bring Your App to Life ✨

```
# ═══════════════════════════════════════════
# ANIMATIONS IN FLUTTER
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╝
║                   IMPLICIT ANIMATIONS                      ║
╚════════════════════════════════════════════════════════════╝

Easy Animations:
─────────────────────────────────────────────────────────────
```

Implicit animations:

```dart
// AnimatedContainer
AnimatedContainer(
  duration: Duration(seconds: 1),
  curve: Curves.easeInOut,
  width: _isExpanded ? 200 : 100,
  height: _isExpanded ? 200 : 100,
  color: _isExpanded ? Colors.blue : Colors.red,
  child: Center(child: Text('Tap me')),
)

// AnimatedOpacity
AnimatedOpacity(
  opacity: _isVisible ? 1.0 : 0.0,
  duration: Duration(milliseconds: 500),
  child: Text('Fading text'),
)

// AnimatedPositioned (inside Stack)
Stack(
  children: [
    AnimatedPositioned(
      duration: Duration(seconds: 1),
      left: _isLeft ? 0 : 200,
      top: 100,
      child: Container(width: 50, height: 50, color: Colors.blue),
    ),
  ],
)

// AnimatedCrossFade
AnimatedCrossFade(
  duration: Duration(milliseconds: 300),
  firstChild: Icon(Icons.favorite_border, size: 50),
  secondChild: Icon(Icons.favorite, size: 50, color: Colors.red),
  crossFadeState: _isFavorite
      ? CrossFadeState.showSecond
      : CrossFadeState.showFirst,
)

// AnimatedSwitcher
AnimatedSwitcher(
  duration: Duration(milliseconds: 300),
  child: Text(
    '$_counter',
    key: ValueKey<int>(_counter),
    style: TextStyle(fontSize: 50),
  ),
)
```

```
╔════════════════════════════════════════════════════════════╗
║                   EXPLICIT ANIMATIONS                      ║
╚════════════════════════════════════════════════════════════╝
```

Explicit animations:

```dart
class MyAnimationScreen extends StatefulWidget {
  @override
  _MyAnimationScreenState createState() => _MyAnimationScreenState();
}

class _MyAnimationScreenState extends State<MyAnimationScreen>
    with SingleTickerProviderStateMixin {
  late AnimationController _controller;
  late Animation<double> _animation;

  @override
  void initState() {
    super.initState();

    _controller = AnimationController(
      duration: Duration(seconds: 2),
      vsync: this,
    );

    _animation = Tween<double>(begin: 0, end: 300).animate(
      CurvedAnimation(
        parent: _controller,
        curve: Curves.easeInOut,
      ),
    );

    _controller.forward();
  }

  @override
  void dispose() {
    _controller.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return AnimatedBuilder(
      animation: _animation,
      builder: (context, child) {
        return Container(
          width: _animation.value,
          height: _animation.value,
          color: Colors.blue,
        );
      },
    );
  }
}

// Rotation animation
late Animation<double> _rotationAnimation;

_rotationAnimation = Tween<double>(begin: 0, end: 2 * 3.14159).animate(_controller);

Transform.rotate(
  angle: _rotationAnimation.value,
  child: Icon(Icons.refresh),
)

// Scale animation
late Animation<double> _scaleAnimation;

_scaleAnimation = Tween<double>(begin: 0.5, end: 1.5).animate(_controller);

Transform.scale(
  scale: _scaleAnimation.value,
  child: Icon(Icons.favorite),
)
```

```
╔════════════════════════════════════════════════════════════╗
║                   HERO ANIMATIONS                          ║
╚════════════════════════════════════════════════════════════╝
```

Hero transitions:

```dart
// First screen
Hero(
  tag: 'hero-image',
  child: Image.network('https://example.com/image.jpg'),
)

// Second screen (same tag!)
Hero(
  tag: 'hero-image',
  child: Image.network('https://example.com/image.jpg'),
)

// Navigation automatically animates!
Navigator.push(
  context,
  MaterialPageRoute(builder: (context) => DetailScreen()),
);
```

---

## 🎯 Summary

```
╔════════════════════════════════════════════════════════════╗
║                   QUICK START CHECKLIST                    ║
╚════════════════════════════════════════════════════════════╝

Getting Started:
─────────────────────────────────────────────────────────────
☐ Install Flutter SDK
☐ Install IDE (VS Code/Android Studio)
☐ Run flutter doctor
☐ Create first app: flutter create my_app
☐ Run app: flutter run
☐ Learn widgets
☐ Build simple app

Essential Concepts:
─────────────────────────────────────────────────────────────
✅ Everything is a widget
✅ Stateless vs Stateful
✅ Dart language basics
✅ Layouts (Column, Row, Stack)
✅ Navigation
✅ State management (Provider)
✅ HTTP requests
✅ Async/await

Recommended Stack:
─────────────────────────────────────────────────────────────
✅ Provider or Riverpod (state)
✅ go_router (navigation)
✅ Dio (networking)
✅ shared_preferences (storage)
✅ Firebase (backend)

Remember:
─────────────────────────────────────────────────────────────
"Learn Dart first.
Master widgets.
Build real apps.
Hot reload is magic!"

Now go build beautiful apps! 🦋
```

---

<div align="center">

**Built with 🦋 by MrDib, for Flutter developers**

_Remember: "Everything is a widget!"_ ✨

**Happy Fluttering!** 🚀

</div>

---

## 🔗 Related Guides

- [Dart Programming](../Development/Languages/Dart.md)
- [Mobile Development](./React-Native.md)
- [UI/UX Design](../Design-Resources/Design-Galleries.md)
- [Firebase Integration](../APIs-Services/Backend-Services.md)

---

## 📊 Quick Reference Card

### **Essential Commands:**

```bash
# Create app
flutter create my_app

# Run app
flutter run
flutter run -d chrome # Web
flutter run -d ios # iOS
flutter run -d android # Android

# Build
flutter build apk # Android
flutter build ios # iOS
flutter build web # Web

# Other
flutter doctor
flutter pub get
flutter clean
```

### **Basic Widget:**

```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(title: Text('Flutter App')),
        body: Center(child: Text('Hello Flutter!')),
      ),
    );
  }
}
```

### **Hot Keys:**

- `r` - Hot reload
- `R` - Hot restart
- `q` - Quit
- `o` - Toggle platform (iOS/Android)

---
