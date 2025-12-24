<div align="center">

# 🏛️ Design Patterns - Write Better Code! 🏛️

![Patterns](https://img.shields.io/badge/Design_Patterns-Software_Architecture-blue?style=for-the-badge)
![SOLID](https://img.shields.io/badge/SOLID-Principles-green?style=for-the-badge)
![Clean](https://img.shields.io/badge/Clean_Code-Best_Practices-orange?style=for-the-badge)

### _Proven solutions to common problems_ 🎯

**Master the patterns that power great software!** ✨

</div>

---

## 📚 Table of Contents

- [🎯 What are Design Patterns](#-what-are-design-patterns)
- [🔨 Creational Patterns](#-creational-patterns)
- [🏗️ Structural Patterns](#️-structural-patterns)
- [⚡ Behavioral Patterns](#-behavioral-patterns)
- [🎨 Modern Patterns](#-modern-patterns)
- [💎 SOLID Principles](#-solid-principles)
- [🚫 Anti-Patterns](#-anti-patterns)
- [🔗 Pattern Combinations](#-pattern-combinations)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 🎯 What are Design Patterns

</div>

### Understanding Design Patterns 🌟

```

# ═══════════════════════════════════════════

# DESIGN PATTERNS EXPLAINED

# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║ WHAT ARE DESIGN PATTERNS?                                  ║
╚════════════════════════════════════════════════════════════╝

Design Patterns:
─────────────────────────────────────────────────────────────
Reusable solutions to commonly occurring problems in software
design. Templates for solving problems that can be used in
many different situations.

Origin:
─────────────────────────────────────────────────────────────
• "Gang of Four" (GoF) - 1994 book
• Erich Gamma, Richard Helm, Ralph Johnson, John Vlissides
• 23 classic patterns
• Foundation of software design

Key Points:
─────────────────────────────────────────────────────────────
✅ Proven solutions
✅ Language-independent
✅ Reusable templates
✅ Common vocabulary
✅ Best practices
✅ Avoid reinventing the wheel
✅ Improve code quality
✅ Easier maintenance

╔════════════════════════════════════════════════════════════╗
║ WHY USE DESIGN PATTERNS?                                   ║
╚════════════════════════════════════════════════════════════╝

Benefits:
─────────────────────────────────────────────────────────────
✅ Code reusability
✅ Better communication (common language)
✅ Proven solutions
✅ Easier maintenance
✅ Flexibility and scalability
✅ Faster development
✅ Less bugs
✅ Career advancement (understanding patterns)

Problems They Solve:
─────────────────────────────────────────────────────────────
• Tight coupling
• Code duplication
• Hard to extend
• Hard to test
• Difficult to understand
• Fragile code

╔════════════════════════════════════════════════════════════╗
║ PATTERN CATEGORIES                                         ║
╚════════════════════════════════════════════════════════════╝

Three Main Categories:
─────────────────────────────────────────────────────────────

1. Creational Patterns (5)
   • How objects are created
   • Singleton, Factory, Builder, Prototype, Abstract Factory

2. Structural Patterns (7)
   • How objects are composed
   • Adapter, Bridge, Composite, Decorator, Facade, Flyweight, Proxy

3. Behavioral Patterns (11)
   • How objects interact and communicate
   • Chain of Responsibility, Command, Iterator, Mediator,
   Memento, Observer, State, Strategy, Template Method,
   Visitor, Interpreter

╔════════════════════════════════════════════════════════════╗
║ WHEN TO USE PATTERNS                                       ║
╚════════════════════════════════════════════════════════════╝

✅ DO Use Patterns When:
─────────────────────────────────────────────────────────────
• The problem fits the pattern
• It simplifies the solution
• Team understands the pattern
• Long-term maintenance expected
• Code needs to be flexible

❌ DON'T Use Patterns When:
─────────────────────────────────────────────────────────────
• Over-engineering simple problems
• Team doesn't understand patterns
• Forcing a pattern where it doesn't fit
• Adds unnecessary complexity
• Quick prototype/throwaway code

Remember:
─────────────────────────────────────────────────────────────
"Patterns are tools, not rules.
Use them wisely, not religiously."

╔════════════════════════════════════════════════════════════╗
║ LEARNING PATH                                              ║
╚════════════════════════════════════════════════════════════╝

Beginner Level:
─────────────────────────────────────────────────────────────

1. Singleton
2. Factory Method
3. Observer
4. Strategy
5. Decorator

Intermediate Level:
───────────────────────────────────────────────────────────── 6. Builder 7. Adapter 8. Facade 9. Template Method 10. State

Advanced Level:
───────────────────────────────────────────────────────────── 11. Abstract Factory 12. Proxy 13. Composite 14. Chain of Responsibility 15. Command

Expert Level:
───────────────────────────────────────────────────────────── 16. Flyweight 17. Bridge 18. Mediator 19. Memento 20. Visitor 21. Interpreter 22. Prototype

Start simple, master gradually! 📈

```

---

<div align="center">

## 🔨 Creational Patterns

</div>

### How Objects Are Created 🏗️

```

# ═══════════════════════════════════════════

# CREATIONAL PATTERNS

# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║ SINGLETON PATTERN                                          ║
╚════════════════════════════════════════════════════════════╝

Purpose:
─────────────────────────────────────────────────────────────
Ensure a class has only ONE instance and provide a global
point of access to it.

When to Use:
─────────────────────────────────────────────────────────────
• Database connections
• Configuration managers
• Logging
• Cache
• Thread pools
• Device drivers

Pros:
✅ Controlled access to sole instance
✅ Global access point
✅ Lazy initialization possible

Cons:
❌ Global state (can be problematic)
❌ Hard to test (tight coupling)
❌ Thread-safety concerns
❌ Violates Single Responsibility Principle

Implementation:
─────────────────────────────────────────────────────────────

```

Singleton examples:

```javascript
// JavaScript - Modern (ES6+)
class Singleton {
  constructor() {
    if (Singleton.instance) {
      return Singleton.instance;
    }

    this.data = [];
    Singleton.instance = this;
  }

  addData(item) {
    this.data.push(item);
  }

  getData() {
    return this.data;
  }
}

// Usage
const instance1 = new Singleton();
const instance2 = new Singleton();
console.log(instance1 === instance2); // true

// JavaScript - Module Pattern (Better)
const Singleton = (() => {
  let instance;

  function init() {
    // Private variables and methods
    let data = [];

    return {
      // Public methods
      addData(item) {
        data.push(item);
      },
      getData() {
        return data;
      },
    };
  }

  return {
    getInstance() {
      if (!instance) {
        instance = init();
      }
      return instance;
    },
  };
})();

// Usage
const instance = Singleton.getInstance();
```

```python
# Python
class Singleton:
    _instance = None

    def __new__(cls):
        if cls._instance is None:
            cls._instance = super().__new__(cls)
            cls._instance.data = []
        return cls._instance

    def add_data(self, item):
        self.data.append(item)

    def get_data(self):
        return self.data

# Usage
instance1 = Singleton()
instance2 = Singleton()
print(instance1 is instance2)  # True

# Python - Better with decorator
def singleton(cls):
    instances = {}

    def get_instance(*args, **kwargs):
        if cls not in instances:
            instances[cls] = cls(*args, **kwargs)
        return instances[cls]

    return get_instance

@singleton
class Database:
    def __init__(self):
        self.connection = "Connected"

# Usage
db1 = Database()
db2 = Database()
print(db1 is db2)  # True
```

```java
// Java - Thread-safe (Bill Pugh)
public class Singleton {
    private Singleton() {}

    private static class SingletonHolder {
        private static final Singleton INSTANCE = new Singleton();
    }

    public static Singleton getInstance() {
        return SingletonHolder.INSTANCE;
    }
}

// Java - Enum (Best)
public enum Singleton {
    INSTANCE;

    public void doSomething() {
        // Your code here
    }
}

// Usage
Singleton.INSTANCE.doSomething();
```

```
╔════════════════════════════════════════════════════════════╗
║                   FACTORY PATTERN                          ║
╚════════════════════════════════════════════════════════════╝

Purpose:
─────────────────────────────────────────────────────────────
Create objects without specifying the exact class to create.
Defines an interface for creating an object, but lets
subclasses decide which class to instantiate.

When to Use:
─────────────────────────────────────────────────────────────
• Creation logic is complex
• Don't know exact types beforehand
• Want to centralize object creation
• Need to decouple object creation

Pros:
✅ Loose coupling
✅ Single Responsibility (creation separate)
✅ Open/Closed Principle (easy to extend)

Cons:
❌ Can become complex
❌ More classes to manage

Implementation:
─────────────────────────────────────────────────────────────
```

Factory examples:

```javascript
// JavaScript
class Dog {
  speak() {
    return "Woof!";
  }
}

class Cat {
  speak() {
    return "Meow!";
  }
}

class Bird {
  speak() {
    return "Tweet!";
  }
}

// Factory
class AnimalFactory {
  createAnimal(type) {
    switch (type) {
      case "dog":
        return new Dog();
      case "cat":
        return new Cat();
      case "bird":
        return new Bird();
      default:
        throw new Error("Invalid animal type");
    }
  }
}

// Usage
const factory = new AnimalFactory();
const dog = factory.createAnimal("dog");
console.log(dog.speak()); // "Woof!"

// Modern approach with Map
class AnimalFactory2 {
  constructor() {
    this.animals = {
      dog: Dog,
      cat: Cat,
      bird: Bird,
    };
  }

  createAnimal(type) {
    const AnimalClass = this.animals[type];
    if (!AnimalClass) {
      throw new Error("Invalid animal type");
    }
    return new AnimalClass();
  }
}
```

```python
# Python
from abc import ABC, abstractmethod

class Animal(ABC):
    @abstractmethod
    def speak(self):
        pass

class Dog(Animal):
    def speak(self):
        return "Woof!"

class Cat(Animal):
    def speak(self):
        return "Meow!"

class AnimalFactory:
    def create_animal(self, animal_type):
        if animal_type == 'dog':
            return Dog()
        elif animal_type == 'cat':
            return Cat()
        else:
            raise ValueError('Invalid animal type')

# Usage
factory = AnimalFactory()
dog = factory.create_animal('dog')
print(dog.speak())  # "Woof!"

# Python - Better with dictionary
class AnimalFactory2:
    def __init__(self):
        self._animals = {
            'dog': Dog,
            'cat': Cat
        }

    def create_animal(self, animal_type):
        animal_class = self._animals.get(animal_type)
        if not animal_class:
            raise ValueError('Invalid animal type')
        return animal_class()
```

```
╔════════════════════════════════════════════════════════════╗
║                   BUILDER PATTERN                          ║
╚════════════════════════════════════════════════════════════╝

Purpose:
─────────────────────────────────────────────────────────────
Separate the construction of a complex object from its
representation. Build objects step by step.

When to Use:
─────────────────────────────────────────────────────────────
• Object has many parameters (telescoping constructor)
• Want immutable objects
• Step-by-step construction needed
• Different representations of same object

Pros:
✅ Readable code (fluent interface)
✅ Can create different representations
✅ Immutable objects
✅ Single Responsibility

Cons:
❌ More code/classes
❌ Overhead for simple objects

Implementation:
─────────────────────────────────────────────────────────────
```

Builder examples:

```javascript
// JavaScript
class User {
  constructor(builder) {
    this.name = builder.name;
    this.age = builder.age;
    this.email = builder.email;
    this.phone = builder.phone;
    this.address = builder.address;
  }
}

class UserBuilder {
  constructor(name) {
    this.name = name;
  }

  setAge(age) {
    this.age = age;
    return this; // Return this for chaining
  }

  setEmail(email) {
    this.email = email;
    return this;
  }

  setPhone(phone) {
    this.phone = phone;
    return this;
  }

  setAddress(address) {
    this.address = address;
    return this;
  }

  build() {
    return new User(this);
  }
}

// Usage
const user = new UserBuilder("John Doe")
  .setAge(30)
  .setEmail("john@example.com")
  .setPhone("123-456-7890")
  .setAddress("123 Main St")
  .build();

console.log(user);
```

```python
# Python
class User:
    def __init__(self, builder):
        self.name = builder.name
        self.age = builder.age
        self.email = builder.email
        self.phone = builder.phone

class UserBuilder:
    def __init__(self, name):
        self.name = name
        self.age = None
        self.email = None
        self.phone = None

    def set_age(self, age):
        self.age = age
        return self

    def set_email(self, email):
        self.email = email
        return self

    def set_phone(self, phone):
        self.phone = phone
        return self

    def build(self):
        return User(self)

# Usage
user = (UserBuilder('John Doe')
    .set_age(30)
    .set_email('john@example.com')
    .set_phone('123-456-7890')
    .build())
```

```
╔════════════════════════════════════════════════════════════╗
║                   PROTOTYPE PATTERN                        ║
╚════════════════════════════════════════════════════════════╝

Purpose:
─────────────────────────────────────────────────────────────
Create new objects by copying existing objects (prototypes).

When to Use:
─────────────────────────────────────────────────────────────
• Object creation is expensive
• Want to avoid subclasses
• Need to hide creation complexity

Implementation:
─────────────────────────────────────────────────────────────
```

Prototype example:

```javascript
// JavaScript (has built-in prototype)
class Shape {
  constructor() {
    this.type = "";
  }

  clone() {
    return Object.create(this);
  }
}

class Circle extends Shape {
  constructor(radius) {
    super();
    this.type = "Circle";
    this.radius = radius;
  }

  clone() {
    return new Circle(this.radius);
  }
}

// Usage
const circle1 = new Circle(10);
const circle2 = circle1.clone();
console.log(circle2.radius); // 10
```

```python
# Python
import copy

class Prototype:
    def clone(self):
        return copy.deepcopy(self)

class Circle(Prototype):
    def __init__(self, radius):
        self.radius = radius

    def __str__(self):
        return f"Circle(radius={self.radius})"

# Usage
circle1 = Circle(10)
circle2 = circle1.clone()
print(circle2)  # Circle(radius=10)
```

---

<div align="center">

## 🏗️ Structural Patterns

</div>

### How Objects Are Composed 🧱

```
# ═══════════════════════════════════════════
# STRUCTURAL PATTERNS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   ADAPTER PATTERN                          ║
╚════════════════════════════════════════════════════════════╝

Purpose:
─────────────────────────────────────────────────────────────
Convert the interface of a class into another interface that
clients expect. Makes incompatible interfaces work together.

When to Use:
─────────────────────────────────────────────────────────────
• Legacy code integration
• Third-party libraries
• Incompatible interfaces
• Want to use existing class

Analogy:
─────────────────────────────────────────────────────────────
Like a power adapter for different countries.
US plug → Adapter → EU socket

Implementation:
─────────────────────────────────────────────────────────────
```

Adapter examples:

```javascript
// JavaScript
// Old interface
class OldLogger {
  logMessage(message) {
    console.log(`OLD: ${message}`);
  }
}

// New interface expected
class NewLogger {
  log(message, level) {
    console.log(`[${level}] ${message}`);
  }
}

// Adapter
class LoggerAdapter {
  constructor(oldLogger) {
    this.oldLogger = oldLogger;
  }

  log(message, level = "INFO") {
    // Adapt old interface to new
    this.oldLogger.logMessage(`[${level}] ${message}`);
  }
}

// Usage
const oldLogger = new OldLogger();
const adapter = new LoggerAdapter(oldLogger);
adapter.log("Hello", "INFO"); // OLD: [INFO] Hello

// Real-world example: Payment adapters
class PayPalPayment {
  makePayment(amount) {
    console.log(`PayPal payment of $${amount}`);
  }
}

class StripePayment {
  processPayment(amount, currency) {
    console.log(`Stripe payment of ${amount} ${currency}`);
  }
}

// Adapter for Stripe
class StripeAdapter {
  constructor(stripe) {
    this.stripe = stripe;
  }

  makePayment(amount) {
    this.stripe.processPayment(amount, "USD");
  }
}

// Usage
function processPayment(paymentMethod, amount) {
  paymentMethod.makePayment(amount);
}

const paypal = new PayPalPayment();
const stripe = new StripeAdapter(new StripePayment());

processPayment(paypal, 100);
processPayment(stripe, 200);
```

```
╔════════════════════════════════════════════════════════════╗
║                   DECORATOR PATTERN                        ║
╚════════════════════════════════════════════════════════════╝

Purpose:
─────────────────────────────────────────────────────────────
Attach additional responsibilities to an object dynamically.
Flexible alternative to subclassing.

When to Use:
─────────────────────────────────────────────────────────────
• Add features dynamically
• Combine multiple features
• Avoid subclass explosion
• Single Responsibility

Analogy:
─────────────────────────────────────────────────────────────
Like adding toppings to pizza or accessories to a car.

Implementation:
─────────────────────────────────────────────────────────────
```

Decorator examples:

```javascript
// JavaScript
// Base component
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
    return this.coffee.description() + ", Milk";
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
    return this.coffee.description() + ", Sugar";
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
    return this.coffee.description() + ", Whipped Cream";
  }
}

// Usage
let coffee = new Coffee();
console.log(coffee.description(), "$" + coffee.cost());
// Coffee $5

coffee = new MilkDecorator(coffee);
console.log(coffee.description(), "$" + coffee.cost());
// Coffee, Milk $6

coffee = new SugarDecorator(coffee);
console.log(coffee.description(), "$" + coffee.cost());
// Coffee, Milk, Sugar $6.5

coffee = new WhipDecorator(coffee);
console.log(coffee.description(), "$" + coffee.cost());
// Coffee, Milk, Sugar, Whipped Cream $8.5
```

```python
# Python - Using decorators (language feature)
def uppercase_decorator(func):
    def wrapper(*args, **kwargs):
        result = func(*args, **kwargs)
        return result.upper()
    return wrapper

def exclamation_decorator(func):
    def wrapper(*args, **kwargs):
        result = func(*args, **kwargs)
        return result + '!!!'
    return wrapper

@exclamation_decorator
@uppercase_decorator
def greet(name):
    return f'hello {name}'

print(greet('world'))  # HELLO WORLD!!!
```

```
╔════════════════════════════════════════════════════════════╗
║                   FACADE PATTERN                           ║
╚════════════════════════════════════════════════════════════╝

Purpose:
─────────────────────────────────────────────────────────────
Provide a simplified interface to a complex subsystem.

When to Use:
─────────────────────────────────────────────────────────────
• Complex system with many classes
• Want simple interface
• Decouple subsystem from clients
• Layer architecture

Analogy:
─────────────────────────────────────────────────────────────
Like a restaurant waiter - you don't interact with kitchen,
chef, dishwasher directly. Waiter is the facade.

Implementation:
─────────────────────────────────────────────────────────────
```

Facade example:

```javascript
// JavaScript
// Complex subsystem
class CPU {
  freeze() {
    console.log("CPU: Freeze");
  }

  jump(address) {
    console.log(`CPU: Jump to ${address}`);
  }

  execute() {
    console.log("CPU: Execute");
  }
}

class Memory {
  load(address, data) {
    console.log(`Memory: Load ${data} at ${address}`);
  }
}

class HardDrive {
  read(sector, size) {
    console.log(`HardDrive: Read ${size} bytes from sector ${sector}`);
    return "data";
  }
}

// Facade
class ComputerFacade {
  constructor() {
    this.cpu = new CPU();
    this.memory = new Memory();
    this.hardDrive = new HardDrive();
  }

  start() {
    console.log("Starting computer...");
    this.cpu.freeze();
    const data = this.hardDrive.read(0, 1024);
    this.memory.load(0, data);
    this.cpu.jump(0);
    this.cpu.execute();
    console.log("Computer started!");
  }
}

// Usage - Simple interface!
const computer = new ComputerFacade();
computer.start();
```

```
╔════════════════════════════════════════════════════════════╗
║                   PROXY PATTERN                            ║
╚════════════════════════════════════════════════════════════╝

Purpose:
─────────────────────────────────────────────────────────────
Provide a surrogate or placeholder for another object to
control access to it.

Types:
─────────────────────────────────────────────────────────────
• Virtual Proxy: Lazy initialization
• Protection Proxy: Access control
• Remote Proxy: Remote object representation
• Caching Proxy: Cache results

When to Use:
─────────────────────────────────────────────────────────────
• Expensive object creation (lazy loading)
• Access control needed
• Logging/monitoring
• Caching

Implementation:
─────────────────────────────────────────────────────────────
```

Proxy example:

```javascript
// JavaScript
// Real object
class Image {
  constructor(filename) {
    this.filename = filename;
    this.load();
  }

  load() {
    console.log(`Loading image: ${this.filename}`);
  }

  display() {
    console.log(`Displaying image: ${this.filename}`);
  }
}

// Proxy with lazy loading
class ImageProxy {
  constructor(filename) {
    this.filename = filename;
    this.image = null;
  }

  display() {
    if (!this.image) {
      this.image = new Image(this.filename);
    }
    this.image.display();
  }
}

// Usage
const image = new ImageProxy("photo.jpg");
// Image not loaded yet!

image.display(); // Loads and displays
// Loading image: photo.jpg
// Displaying image: photo.jpg

image.display(); // Just displays (already loaded)
// Displaying image: photo.jpg

// Modern JavaScript Proxy
const target = {
  message: "Hello",
};

const handler = {
  get(target, prop) {
    console.log(`Accessing property: ${prop}`);
    return target[prop];
  },
  set(target, prop, value) {
    console.log(`Setting ${prop} to ${value}`);
    target[prop] = value;
    return true;
  },
};

const proxy = new Proxy(target, handler);
console.log(proxy.message); // Logs access then returns value
proxy.message = "World"; // Logs setting
```

---

<div align="center">

## ⚡ Behavioral Patterns

</div>

### How Objects Interact 🤝

```
# ═══════════════════════════════════════════
# BEHAVIORAL PATTERNS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   OBSERVER PATTERN                         ║
╚════════════════════════════════════════════════════════════╝

Purpose:
─────────────────────────────────────────────────────────────
Define a one-to-many dependency between objects so that when
one object changes state, all its dependents are notified.

When to Use:
─────────────────────────────────────────────────────────────
• Event handling
• Real-time updates
• Decoupled communication
• Pub/Sub systems

Analogy:
─────────────────────────────────────────────────────────────
Like subscribing to a YouTube channel - you get notified
when new videos are uploaded.

Implementation:
─────────────────────────────────────────────────────────────
```

Observer examples:

```javascript
// JavaScript
class Subject {
  constructor() {
    this.observers = [];
  }

  subscribe(observer) {
    this.observers.push(observer);
  }

  unsubscribe(observer) {
    this.observers = this.observers.filter((obs) => obs !== observer);
  }

  notify(data) {
    this.observers.forEach((observer) => observer.update(data));
  }
}

class Observer {
  constructor(name) {
    this.name = name;
  }

  update(data) {
    console.log(`${this.name} received: ${data}`);
  }
}

// Usage
const subject = new Subject();

const observer1 = new Observer("Observer 1");
const observer2 = new Observer("Observer 2");

subject.subscribe(observer1);
subject.subscribe(observer2);

subject.notify("Hello!");
// Observer 1 received: Hello!
// Observer 2 received: Hello!

subject.unsubscribe(observer1);
subject.notify("Goodbye!");
// Observer 2 received: Goodbye!

// Real-world: Event Emitter
class EventEmitter {
  constructor() {
    this.events = {};
  }

  on(event, listener) {
    if (!this.events[event]) {
      this.events[event] = [];
    }
    this.events[event].push(listener);
  }

  emit(event, data) {
    if (this.events[event]) {
      this.events[event].forEach((listener) => listener(data));
    }
  }

  off(event, listenerToRemove) {
    if (this.events[event]) {
      this.events[event] = this.events[event].filter(
        (listener) => listener !== listenerToRemove
      );
    }
  }
}

// Usage
const emitter = new EventEmitter();

const handleUserLogin = (data) => {
  console.log(`User logged in: ${data.username}`);
};

emitter.on("userLogin", handleUserLogin);
emitter.on("userLogin", (data) => {
  console.log(`Send welcome email to ${data.email}`);
});

emitter.emit("userLogin", {
  username: "john",
  email: "john@example.com",
});
// User logged in: john
// Send welcome email to john@example.com
```

```
╔════════════════════════════════════════════════════════════╗
║                   STRATEGY PATTERN                         ║
╚════════════════════════════════════════════════════════════╝

Purpose:
─────────────────────────────────────────────────────────────
Define a family of algorithms, encapsulate each one, and make
them interchangeable. Let the algorithm vary independently.

When to Use:
─────────────────────────────────────────────────────────────
• Multiple algorithms for same task
• Want to switch algorithms at runtime
• Avoid conditional statements
• Encapsulate algorithms

Analogy:
─────────────────────────────────────────────────────────────
Like choosing different routes to reach a destination:
highway, scenic route, shortest path.

Implementation:
─────────────────────────────────────────────────────────────
```

Strategy examples:

```javascript
// JavaScript
// Strategies
class CreditCardStrategy {
  pay(amount) {
    console.log(`Paid $${amount} with Credit Card`);
  }
}

class PayPalStrategy {
  pay(amount) {
    console.log(`Paid $${amount} with PayPal`);
  }
}

class CryptoStrategy {
  pay(amount) {
    console.log(`Paid $${amount} with Cryptocurrency`);
  }
}

// Context
class ShoppingCart {
  constructor(paymentStrategy) {
    this.paymentStrategy = paymentStrategy;
  }

  setPaymentStrategy(strategy) {
    this.paymentStrategy = strategy;
  }

  checkout(amount) {
    this.paymentStrategy.pay(amount);
  }
}

// Usage
const cart = new ShoppingCart(new CreditCardStrategy());
cart.checkout(100); // Paid $100 with Credit Card

cart.setPaymentStrategy(new PayPalStrategy());
cart.checkout(200); // Paid $200 with PayPal

cart.setPaymentStrategy(new CryptoStrategy());
cart.checkout(300); // Paid $300 with Cryptocurrency

// Real-world: Sorting strategies
class BubbleSort {
  sort(array) {
    console.log("Sorting with Bubble Sort");
    // Implementation...
    return array.sort((a, b) => a - b);
  }
}

class QuickSort {
  sort(array) {
    console.log("Sorting with Quick Sort");
    // Implementation...
    return array.sort((a, b) => a - b);
  }
}

class Sorter {
  constructor(strategy) {
    this.strategy = strategy;
  }

  sort(array) {
    return this.strategy.sort(array);
  }
}

// Usage
const sorter = new Sorter(new QuickSort());
console.log(sorter.sort([5, 2, 8, 1, 9]));
```

```
╔════════════════════════════════════════════════════════════╗
║                   COMMAND PATTERN                          ║
╚════════════════════════════════════════════════════════════╝

Purpose:
─────────────────────────────────────────────────────────────
Encapsulate a request as an object, allowing you to
parameterize clients with different requests, queue requests,
and support undoable operations.

When to Use:
─────────────────────────────────────────────────────────────
• Undo/Redo functionality
• Transaction systems
• Queue operations
• Macro recording

Analogy:
─────────────────────────────────────────────────────────────
Like a restaurant order - waiter takes order (command),
gives to chef, order can be modified or cancelled.

Implementation:
─────────────────────────────────────────────────────────────
```

Command example:

```javascript
// JavaScript
// Receiver
class Light {
  on() {
    console.log("Light is ON");
  }

  off() {
    console.log("Light is OFF");
  }
}

// Commands
class LightOnCommand {
  constructor(light) {
    this.light = light;
  }

  execute() {
    this.light.on();
  }

  undo() {
    this.light.off();
  }
}

class LightOffCommand {
  constructor(light) {
    this.light = light;
  }

  execute() {
    this.light.off();
  }

  undo() {
    this.light.on();
  }
}

// Invoker
class RemoteControl {
  constructor() {
    this.history = [];
  }

  execute(command) {
    command.execute();
    this.history.push(command);
  }

  undo() {
    const command = this.history.pop();
    if (command) {
      command.undo();
    }
  }
}

// Usage
const light = new Light();
const lightOn = new LightOnCommand(light);
const lightOff = new LightOffCommand(light);

const remote = new RemoteControl();

remote.execute(lightOn); // Light is ON
remote.execute(lightOff); // Light is OFF
remote.undo(); // Light is ON
remote.undo(); // Light is OFF
```

```
╔════════════════════════════════════════════════════════════╗
║                   STATE PATTERN                            ║
╚════════════════════════════════════════════════════════════╝

Purpose:
─────────────────────────────────────────────────────────────
Allow an object to alter its behavior when its internal
state changes. The object will appear to change its class.

When to Use:
─────────────────────────────────────────────────────────────
• Object behavior depends on state
• Large conditional statements based on state
• State-specific behavior

Analogy:
─────────────────────────────────────────────────────────────
Like a vending machine - different behaviors based on
current state (HasMoney, NoMoney, Dispensing).

Implementation:
─────────────────────────────────────────────────────────────
```

State example:

```javascript
// JavaScript
// States
class OrderedState {
  next(order) {
    order.setState(order.shippedState);
  }

  getStatus() {
    return "Ordered";
  }
}

class ShippedState {
  next(order) {
    order.setState(order.deliveredState);
  }

  getStatus() {
    return "Shipped";
  }
}

class DeliveredState {
  next(order) {
    console.log("Order already delivered");
  }

  getStatus() {
    return "Delivered";
  }
}

// Context
class Order {
  constructor() {
    this.orderedState = new OrderedState();
    this.shippedState = new ShippedState();
    this.deliveredState = new DeliveredState();

    this.currentState = this.orderedState;
  }

  setState(state) {
    this.currentState = state;
  }

  next() {
    this.currentState.next(this);
  }

  getStatus() {
    return this.currentState.getStatus();
  }
}

// Usage
const order = new Order();
console.log(order.getStatus()); // Ordered

order.next();
console.log(order.getStatus()); // Shipped

order.next();
console.log(order.getStatus()); // Delivered

order.next(); // Order already delivered
```

```
╔════════════════════════════════════════════════════════════╗
║                   TEMPLATE METHOD PATTERN                  ║
╚════════════════════════════════════════════════════════════╝

Purpose:
─────────────────────────────────────────────────────────────
Define the skeleton of an algorithm in a method, deferring
some steps to subclasses. Let subclasses redefine certain
steps without changing the algorithm's structure.

When to Use:
─────────────────────────────────────────────────────────────
• Common algorithm with varying implementations
• Control extension points
• Avoid code duplication
• Framework design

Implementation:
─────────────────────────────────────────────────────────────
```

Template Method example:

```javascript
// JavaScript
class DataProcessor {
  // Template method
  process() {
    this.readData();
    this.processData();
    this.saveData();
  }

  readData() {
    throw new Error("readData must be implemented");
  }

  processData() {
    throw new Error("processData must be implemented");
  }

  saveData() {
    console.log("Saving data...");
  }
}

class CSVProcessor extends DataProcessor {
  readData() {
    console.log("Reading CSV file");
  }

  processData() {
    console.log("Processing CSV data");
  }
}

class JSONProcessor extends DataProcessor {
  readData() {
    console.log("Reading JSON file");
  }

  processData() {
    console.log("Processing JSON data");
  }
}

// Usage
const csvProcessor = new CSVProcessor();
csvProcessor.process();
// Reading CSV file
// Processing CSV data
// Saving data...

const jsonProcessor = new JSONProcessor();
jsonProcessor.process();
// Reading JSON file
// Processing JSON data
// Saving data...
```

```
╔════════════════════════════════════════════════════════════╗
║                   CHAIN OF RESPONSIBILITY                  ║
╚════════════════════════════════════════════════════════════╝

Purpose:
─────────────────────────────────────────────────────────────
Pass requests along a chain of handlers. Each handler decides
either to process the request or pass it to the next handler.

When to Use:
─────────────────────────────────────────────────────────────
• Multiple objects can handle request
• Handler not known in advance
• Middleware systems
• Event bubbling

Analogy:
─────────────────────────────────────────────────────────────
Like customer support - Level 1 → Level 2 → Manager
Each level tries to solve, or passes to next.

Implementation:
─────────────────────────────────────────────────────────────
```

Chain of Responsibility example:

```javascript
// JavaScript
class Handler {
  constructor() {
    this.nextHandler = null;
  }

  setNext(handler) {
    this.nextHandler = handler;
    return handler; // For chaining
  }

  handle(request) {
    if (this.nextHandler) {
      return this.nextHandler.handle(request);
    }
    return null;
  }
}

class Level1Support extends Handler {
  handle(request) {
    if (request.priority === "low") {
      console.log("Level 1: Handling low priority request");
      return true;
    }
    console.log("Level 1: Passing to next level");
    return super.handle(request);
  }
}

class Level2Support extends Handler {
  handle(request) {
    if (request.priority === "medium") {
      console.log("Level 2: Handling medium priority request");
      return true;
    }
    console.log("Level 2: Passing to next level");
    return super.handle(request);
  }
}

class ManagerSupport extends Handler {
  handle(request) {
    console.log("Manager: Handling high priority request");
    return true;
  }
}

// Setup chain
const level1 = new Level1Support();
const level2 = new Level2Support();
const manager = new ManagerSupport();

level1.setNext(level2).setNext(manager);

// Usage
level1.handle({ priority: "low" });
// Level 1: Handling low priority request

level1.handle({ priority: "medium" });
// Level 1: Passing to next level
// Level 2: Handling medium priority request

level1.handle({ priority: "high" });
// Level 1: Passing to next level
// Level 2: Passing to next level
// Manager: Handling high priority request

// Real-world: Express middleware
class Middleware {
  constructor() {
    this.middlewares = [];
  }

  use(fn) {
    this.middlewares.push(fn);
  }

  execute(context) {
    let index = 0;

    const next = () => {
      if (index < this.middlewares.length) {
        const middleware = this.middlewares[index++];
        middleware(context, next);
      }
    };

    next();
  }
}

// Usage
const app = new Middleware();

app.use((context, next) => {
  console.log("Logging middleware");
  next();
});

app.use((context, next) => {
  console.log("Auth middleware");
  if (context.authenticated) {
    next();
  } else {
    console.log("Not authenticated");
  }
});

app.use((context, next) => {
  console.log("Final handler");
});

app.execute({ authenticated: true });
// Logging middleware
// Auth middleware
// Final handler
```

---

<div align="center">

## 🎨 Modern Patterns

</div>

### Contemporary Design Patterns 🚀

```
# ═══════════════════════════════════════════
# MODERN PATTERNS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   DEPENDENCY INJECTION                     ║
╚════════════════════════════════════════════════════════════╝

Purpose:
─────────────────────────────────────────────────────────────
Provide dependencies from the outside rather than creating
them internally. Inversion of Control (IoC).

Benefits:
─────────────────────────────────────────────────────────────
✅ Loose coupling
✅ Easy testing (mock dependencies)
✅ Flexibility
✅ Single Responsibility

Implementation:
─────────────────────────────────────────────────────────────
```

Dependency Injection examples:

```javascript
// JavaScript

// ❌ BAD - Tight coupling
class UserService {
  constructor() {
    this.database = new Database(); // Hard-coded dependency
  }

  getUser(id) {
    return this.database.query(`SELECT * FROM users WHERE id = ${id}`);
  }
}

// ✅ GOOD - Dependency Injection
class UserService {
  constructor(database) {
    this.database = database; // Injected dependency
  }

  getUser(id) {
    return this.database.query(`SELECT * FROM users WHERE id = ${id}`);
  }
}

// Usage
const database = new Database();
const userService = new UserService(database);

// Easy to mock for testing
const mockDatabase = {
  query: (sql) => ({ id: 1, name: "Test User" }),
};
const testUserService = new UserService(mockDatabase);

// Constructor Injection (shown above)
// Property Injection
class UserService2 {
  setDatabase(database) {
    this.database = database;
  }

  getUser(id) {
    return this.database.query(`SELECT * FROM users WHERE id = ${id}`);
  }
}

const service = new UserService2();
service.setDatabase(new Database());

// Method Injection
class UserService3 {
  getUser(id, database) {
    return database.query(`SELECT * FROM users WHERE id = ${id}`);
  }
}

const service3 = new UserService3();
service3.getUser(1, new Database());
```

```typescript
// TypeScript with interfaces
interface IDatabase {
  query(sql: string): any;
}

interface ILogger {
  log(message: string): void;
}

class UserService {
  constructor(private database: IDatabase, private logger: ILogger) {}

  async getUser(id: number) {
    this.logger.log(`Fetching user ${id}`);
    return this.database.query(`SELECT * FROM users WHERE id = ${id}`);
  }
}

// Different implementations
class MySQLDatabase implements IDatabase {
  query(sql: string) {
    console.log("MySQL query:", sql);
    return { id: 1, name: "John" };
  }
}

class PostgresDatabase implements IDatabase {
  query(sql: string) {
    console.log("Postgres query:", sql);
    return { id: 1, name: "John" };
  }
}

class ConsoleLogger implements ILogger {
  log(message: string) {
    console.log(message);
  }
}

// Usage - Easy to swap implementations
const mysqlService = new UserService(new MySQLDatabase(), new ConsoleLogger());
const postgresService = new UserService(
  new PostgresDatabase(),
  new ConsoleLogger()
);
```

```
╔════════════════════════════════════════════════════════════╗
║                   REPOSITORY PATTERN                       ║
╚════════════════════════════════════════════════════════════╝

Purpose:
─────────────────────────────────────────────────────────────
Separate data access logic from business logic. Mediates
between domain and data mapping layers.

Benefits:
─────────────────────────────────────────────────────────────
✅ Centralized data access
✅ Easy to test
✅ Swap data sources
✅ Single Responsibility

Implementation:
─────────────────────────────────────────────────────────────
```

Repository pattern:

```javascript
// JavaScript
class UserRepository {
  constructor(database) {
    this.database = database;
  }

  async findById(id) {
    return this.database.query("SELECT * FROM users WHERE id = ?", [id]);
  }

  async findByEmail(email) {
    return this.database.query("SELECT * FROM users WHERE email = ?", [email]);
  }

  async findAll() {
    return this.database.query("SELECT * FROM users");
  }

  async create(user) {
    return this.database.query(
      "INSERT INTO users (name, email) VALUES (?, ?)",
      [user.name, user.email]
    );
  }

  async update(id, user) {
    return this.database.query(
      "UPDATE users SET name = ?, email = ? WHERE id = ?",
      [user.name, user.email, id]
    );
  }

  async delete(id) {
    return this.database.query("DELETE FROM users WHERE id = ?", [id]);
  }
}

// Service layer uses repository
class UserService {
  constructor(userRepository) {
    this.userRepository = userRepository;
  }

  async getUser(id) {
    return this.userRepository.findById(id);
  }

  async createUser(userData) {
    // Business logic
    if (!userData.email.includes("@")) {
      throw new Error("Invalid email");
    }

    // Use repository
    return this.userRepository.create(userData);
  }
}

// Usage
const database = new Database();
const userRepository = new UserRepository(database);
const userService = new UserService(userRepository);

await userService.createUser({ name: "John", email: "john@example.com" });
```

```
╔════════════════════════════════════════════════════════════╗
║                   MODULE PATTERN                           ║
╚════════════════════════════════════════════════════════════╝

Purpose:
─────────────────────────────────────────────────────────────
Encapsulate private and public members. JavaScript-specific.

Implementation:
─────────────────────────────────────────────────────────────
```

Module pattern:

```javascript
// JavaScript - IIFE (Immediately Invoked Function Expression)
const UserModule = (function () {
  // Private variables
  let users = [];
  let nextId = 1;

  // Private methods
  function validateUser(user) {
    return user.name && user.email;
  }

  // Public API
  return {
    addUser(user) {
      if (!validateUser(user)) {
        throw new Error("Invalid user");
      }
      user.id = nextId++;
      users.push(user);
      return user;
    },

    getUser(id) {
      return users.find((u) => u.id === id);
    },

    getAllUsers() {
      return [...users]; // Return copy
    },

    removeUser(id) {
      users = users.filter((u) => u.id !== id);
    },
  };
})();

// Usage
UserModule.addUser({ name: "John", email: "john@example.com" });
console.log(UserModule.getAllUsers());

// Can't access private variables
console.log(UserModule.users); // undefined

// ES6 Modules (better approach)
// user-module.js
let users = [];
let nextId = 1;

function validateUser(user) {
  return user.name && user.email;
}

export function addUser(user) {
  if (!validateUser(user)) {
    throw new Error("Invalid user");
  }
  user.id = nextId++;
  users.push(user);
  return user;
}

export function getUser(id) {
  return users.find((u) => u.id === id);
}

// Import in another file
// import { addUser, getUser } from './user-module.js';
```

```
╔════════════════════════════════════════════════════════════╗
║                   FLUX/REDUX PATTERN                       ║
╚════════════════════════════════════════════════════════════╝

Purpose:
─────────────────────────────────────────────────────────────
Unidirectional data flow for state management.
Popular in React applications.

Flow:
─────────────────────────────────────────────────────────────
Action → Dispatcher → Store → View
         ↑                      |
         └──────────────────────┘

Implementation:
─────────────────────────────────────────────────────────────
```

Redux pattern:

```javascript
// JavaScript - Simple Redux implementation
class Store {
  constructor(reducer, initialState = {}) {
    this.reducer = reducer;
    this.state = initialState;
    this.listeners = [];
  }

  getState() {
    return this.state;
  }

  dispatch(action) {
    this.state = this.reducer(this.state, action);
    this.listeners.forEach((listener) => listener());
  }

  subscribe(listener) {
    this.listeners.push(listener);

    // Return unsubscribe function
    return () => {
      this.listeners = this.listeners.filter((l) => l !== listener);
    };
  }
}

// Reducer
function counterReducer(state = { count: 0 }, action) {
  switch (action.type) {
    case "INCREMENT":
      return { count: state.count + 1 };
    case "DECREMENT":
      return { count: state.count - 1 };
    case "ADD":
      return { count: state.count + action.payload };
    default:
      return state;
  }
}

// Usage
const store = new Store(counterReducer, { count: 0 });

store.subscribe(() => {
  console.log("State changed:", store.getState());
});

store.dispatch({ type: "INCREMENT" });
// State changed: { count: 1 }

store.dispatch({ type: "INCREMENT" });
// State changed: { count: 2 }

store.dispatch({ type: "ADD", payload: 5 });
// State changed: { count: 7 }

store.dispatch({ type: "DECREMENT" });
// State changed: { count: 6 }
```

---

<div align="center">

## 💎 SOLID Principles

</div>

### Five Principles of OOP 🎯

```
# ═══════════════════════════════════════════
# SOLID PRINCIPLES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   S - SINGLE RESPONSIBILITY                ║
╚════════════════════════════════════════════════════════════╝

Principle:
─────────────────────────────────────────────────────────────
A class should have only ONE reason to change.
Do one thing and do it well.

Why Important:
─────────────────────────────────────────────────────────────
✅ Easier to understand
✅ Easier to test
✅ Less coupled
✅ Easier to maintain

Examples:
─────────────────────────────────────────────────────────────
```

Single Responsibility examples:

```javascript
// ❌ BAD - Multiple responsibilities
class User {
  constructor(name, email) {
    this.name = name;
    this.email = email;
  }

  // User data management
  getName() {
    return this.name;
  }

  // Database operations
  save() {
    console.log("Saving to database...");
  }

  // Email operations
  sendWelcomeEmail() {
    console.log("Sending welcome email...");
  }

  // Validation
  validateEmail() {
    return this.email.includes("@");
  }
}

// ✅ GOOD - Single responsibility
class User {
  constructor(name, email) {
    this.name = name;
    this.email = email;
  }

  getName() {
    return this.name;
  }

  getEmail() {
    return this.email;
  }
}

class UserRepository {
  save(user) {
    console.log(`Saving ${user.getName()} to database...`);
  }

  findById(id) {
    // Database logic
  }
}

class EmailService {
  sendWelcomeEmail(user) {
    console.log(`Sending welcome email to ${user.getEmail()}...`);
  }
}

class UserValidator {
  validateEmail(email) {
    return email.includes("@");
  }

  validateName(name) {
    return name.length > 0;
  }
}

// Usage
const user = new User("John", "john@example.com");
const repository = new UserRepository();
const emailService = new EmailService();
const validator = new UserValidator();

if (validator.validateEmail(user.getEmail())) {
  repository.save(user);
  emailService.sendWelcomeEmail(user);
}
```

```
╔════════════════════════════════════════════════════════════╗
║                   O - OPEN/CLOSED PRINCIPLE                ║
╚════════════════════════════════════════════════════════════╝

Principle:
─────────────────────────────────────────────────────────────
Open for extension, closed for modification.
Add new functionality without changing existing code.

Why Important:
─────────────────────────────────────────────────────────────
✅ Prevent breaking existing code
✅ Easy to extend
✅ Stable codebase

Examples:
─────────────────────────────────────────────────────────────
```

Open/Closed examples:

```javascript
// ❌ BAD - Need to modify class for new shapes
class AreaCalculator {
  calculate(shapes) {
    let totalArea = 0;

    for (const shape of shapes) {
      if (shape.type === "circle") {
        totalArea += Math.PI * shape.radius ** 2;
      } else if (shape.type === "rectangle") {
        totalArea += shape.width * shape.height;
      }
      // Need to modify this class to add new shapes!
    }

    return totalArea;
  }
}

// ✅ GOOD - Open for extension, closed for modification
class Shape {
  area() {
    throw new Error("area() must be implemented");
  }
}

class Circle extends Shape {
  constructor(radius) {
    super();
    this.radius = radius;
  }

  area() {
    return Math.PI * this.radius ** 2;
  }
}

class Rectangle extends Shape {
  constructor(width, height) {
    super();
    this.width = width;
    this.height = height;
  }

  area() {
    return this.width * this.height;
  }
}

class Triangle extends Shape {
  constructor(base, height) {
    super();
    this.base = base;
    this.height = height;
  }

  area() {
    return (this.base * this.height) / 2;
  }
}

class AreaCalculator {
  calculate(shapes) {
    return shapes.reduce((total, shape) => total + shape.area(), 0);
  }
}

// Usage - Can add new shapes without modifying AreaCalculator!
const shapes = [new Circle(5), new Rectangle(4, 6), new Triangle(3, 4)];

const calculator = new AreaCalculator();
console.log(calculator.calculate(shapes));
```

```
╔════════════════════════════════════════════════════════════╗
║                   L - LISKOV SUBSTITUTION                  ║
╚════════════════════════════════════════════════════════════╝

Principle:
─────────────────────────────────────────────────────────────
Objects of a superclass should be replaceable with objects
of its subclasses without breaking the application.

Why Important:
─────────────────────────────────────────────────────────────
✅ Proper inheritance
✅ Polymorphism works correctly
✅ Predictable behavior

Examples:
─────────────────────────────────────────────────────────────
```

Liskov Substitution examples:

```javascript
// ❌ BAD - Square violates LSP
class Rectangle {
  constructor(width, height) {
    this.width = width;
    this.height = height;
  }

  setWidth(width) {
    this.width = width;
  }

  setHeight(height) {
    this.height = height;
  }

  area() {
    return this.width * this.height;
  }
}

class Square extends Rectangle {
  setWidth(width) {
    this.width = width;
    this.height = width; // Problem!
  }

  setHeight(height) {
    this.width = height; // Problem!
    this.height = height;
  }
}

// This breaks when using Square
function testRectangle(rectangle) {
  rectangle.setWidth(5);
  rectangle.setHeight(4);
  console.log(rectangle.area()); // Expected: 20
}

testRectangle(new Rectangle(0, 0)); // 20 ✓
testRectangle(new Square(0, 0)); // 16 ✗ (Square changed both dimensions!)

// ✅ GOOD - Proper abstraction
class Shape {
  area() {
    throw new Error("area() must be implemented");
  }
}

class Rectangle extends Shape {
  constructor(width, height) {
    super();
    this.width = width;
    this.height = height;
  }

  area() {
    return this.width * this.height;
  }
}

class Square extends Shape {
  constructor(side) {
    super();
    this.side = side;
  }

  area() {
    return this.side ** 2;
  }
}

// Now both work correctly in their own way
```

```
╔════════════════════════════════════════════════════════════╗
║                   I - INTERFACE SEGREGATION                ║
╚════════════════════════════════════════════════════════════╝

Principle:
─────────────────────────────────────────────────────────────
Clients should not be forced to depend on interfaces they
don't use. Many specific interfaces are better than one
general-purpose interface.

Why Important:
─────────────────────────────────────────────────────────────
✅ Smaller, focused interfaces
✅ Less coupling
✅ Easier to implement

Examples:
─────────────────────────────────────────────────────────────
```

Interface Segregation examples:

```typescript
// TypeScript

// ❌ BAD - Fat interface
interface Worker {
  work(): void;
  eat(): void;
  sleep(): void;
}

class HumanWorker implements Worker {
  work() {
    console.log("Working...");
  }

  eat() {
    console.log("Eating...");
  }

  sleep() {
    console.log("Sleeping...");
  }
}

class RobotWorker implements Worker {
  work() {
    console.log("Working...");
  }

  eat() {
    // Robots don't eat! Forced to implement
    throw new Error("Robots don't eat");
  }

  sleep() {
    // Robots don't sleep! Forced to implement
    throw new Error("Robots don't sleep");
  }
}

// ✅ GOOD - Segregated interfaces
interface Workable {
  work(): void;
}

interface Eatable {
  eat(): void;
}

interface Sleepable {
  sleep(): void;
}

class HumanWorker implements Workable, Eatable, Sleepable {
  work() {
    console.log("Working...");
  }

  eat() {
    console.log("Eating...");
  }

  sleep() {
    console.log("Sleeping...");
  }
}

class RobotWorker implements Workable {
  work() {
    console.log("Working...");
  }
  // Only implements what it needs!
}
```

```
╔════════════════════════════════════════════════════════════╗
║                   D - DEPENDENCY INVERSION                 ║
╚════════════════════════════════════════════════════════════╝

Principle:
─────────────────────────────────────────────────────────────
High-level modules should not depend on low-level modules.
Both should depend on abstractions.
Abstractions should not depend on details.

Why Important:
─────────────────────────────────────────────────────────────
✅ Loose coupling
✅ Easy to test
✅ Flexible
✅ Easy to swap implementations

Examples:
─────────────────────────────────────────────────────────────
```

Dependency Inversion examples:

```typescript
// TypeScript

// ❌ BAD - High-level depends on low-level
class MySQLDatabase {
  save(data: string) {
    console.log(`Saving to MySQL: ${data}`);
  }
}

class UserService {
  private database: MySQLDatabase;

  constructor() {
    this.database = new MySQLDatabase(); // Tight coupling!
  }

  saveUser(user: string) {
    this.database.save(user);
  }
}

// Can't easily switch to PostgreSQL or MongoDB!

// ✅ GOOD - Both depend on abstraction
interface IDatabase {
  save(data: string): void;
}

class MySQLDatabase implements IDatabase {
  save(data: string) {
    console.log(`Saving to MySQL: ${data}`);
  }
}

class PostgreSQLDatabase implements IDatabase {
  save(data: string) {
    console.log(`Saving to PostgreSQL: ${data}`);
  }
}

class MongoDBDatabase implements IDatabase {
  save(data: string) {
    console.log(`Saving to MongoDB: ${data}`);
  }
}

class UserService {
  constructor(private database: IDatabase) {}

  saveUser(user: string) {
    this.database.save(user);
  }
}

// Usage - Easy to swap implementations!
const mysqlService = new UserService(new MySQLDatabase());
const postgresService = new UserService(new PostgreSQLDatabase());
const mongoService = new UserService(new MongoDBDatabase());

mysqlService.saveUser("John"); // Saving to MySQL: John
postgresService.saveUser("Jane"); // Saving to PostgreSQL: Jane
mongoService.saveUser("Bob"); // Saving to MongoDB: Bob
```

---

<div align="center">

## 🚫 Anti-Patterns

</div>

### What NOT to Do ⚠️

```
# ═══════════════════════════════════════════
# ANTI-PATTERNS (BAD PRACTICES)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   COMMON ANTI-PATTERNS                     ║
╚════════════════════════════════════════════════════════════╝

God Object:
─────────────────────────────────────────────────────────────
❌ Problem: One object that does everything
❌ Violates: Single Responsibility Principle
✅ Solution: Break into smaller, focused classes

Example:
```

```javascript
// ❌ God Object
class Application {
  // Database operations
  saveToDatabase() {}
  queryDatabase() {}

  // UI operations
  renderUI() {}
  updateUI() {}

  // Network operations
  fetchData() {}
  sendData() {}

  // Business logic
  processOrder() {}
  calculateTotal() {}

  // Authentication
  login() {}
  logout() {}

  // And 50 more methods...
}

// ✅ Better - Separate concerns
class DatabaseService {}
class UIRenderer {}
class NetworkService {}
class OrderService {}
class AuthService {}
```

```
Spaghetti Code:
─────────────────────────────────────────────────────────────
❌ Problem: Tangled, unstructured code
❌ Hard to follow logic
❌ No clear separation
✅ Solution: Use proper structure, design patterns

Singleton Overuse:
─────────────────────────────────────────────────────────────
❌ Problem: Using Singleton for everything
❌ Creates global state
❌ Hard to test
❌ Tight coupling
✅ Solution: Use Dependency Injection instead

Golden Hammer:
─────────────────────────────────────────────────────────────
❌ Problem: "I have a hammer, everything is a nail"
❌ Using same pattern/tool for everything
❌ Forcing patterns where they don't fit
✅ Solution: Choose right tool for the job

Premature Optimization:
─────────────────────────────────────────────────────────────
❌ Problem: Optimizing before knowing if needed
❌ Makes code complex
❌ Wastes time
✅ Solution: Optimize when profiling shows bottleneck

Copy-Paste Programming:
─────────────────────────────────────────────────────────────
❌ Problem: Duplicating code instead of reusing
❌ Hard to maintain
❌ Bugs multiply
✅ Solution: DRY (Don't Repeat Yourself)

Lava Flow:
─────────────────────────────────────────────────────────────
❌ Problem: Dead code that nobody dares to remove
❌ "This was important at some point..."
❌ Clutters codebase
✅ Solution: Remove unused code, use version control

Magic Numbers/Strings:
─────────────────────────────────────────────────────────────
❌ Problem: Hard-coded values without explanation
```

```javascript
// ❌ Magic numbers
if (status === 3) {
  // What is 3?
  processOrder();
}

if (age > 18) {
  // Why 18?
  allowAccess();
}

// ✅ Named constants
const ORDER_STATUS_APPROVED = 3;
const MINIMUM_AGE = 18;

if (status === ORDER_STATUS_APPROVED) {
  processOrder();
}

if (age > MINIMUM_AGE) {
  allowAccess();
}
```

```
Cargo Cult Programming:
─────────────────────────────────────────────────────────────
❌ Problem: Using code without understanding why
❌ "It worked in tutorial, so I'll use it"
❌ Blindly copying from Stack Overflow
✅ Solution: Understand before using

Yo-Yo Problem:
─────────────────────────────────────────────────────────────
❌ Problem: Too many inheritance levels
❌ Hard to trace where method is defined
❌ Deep hierarchies
✅ Solution: Favor composition over inheritance

╔════════════════════════════════════════════════════════════╗
║                   OVER-ENGINEERING                         ║
╚════════════════════════════════════════════════════════════╝

The Pattern Obsession:
─────────────────────────────────────────────────────────────
```

```javascript
// ❌ Over-engineered for simple task
class AbstractFactoryProviderFactory {
  createAbstractFactoryProvider() {
    return new AbstractFactoryProvider();
  }
}

class AbstractFactoryProvider {
  provideFactory() {
    return new ConcreteFactory();
  }
}

class ConcreteFactory {
  createProduct() {
    return new Product();
  }
}

class Product {
  doSomething() {
    return "Hello";
  }
}

// Usage - just to say "Hello"!
const factoryFactory = new AbstractFactoryProviderFactory();
const provider = factoryFactory.createAbstractFactoryProvider();
const factory = provider.provideFactory();
const product = factory.createProduct();
console.log(product.doSomething());

// ✅ Simple solution
function sayHello() {
  return "Hello";
}

console.log(sayHello());

// Remember: KISS (Keep It Simple, Stupid)
```

```
╔════════════════════════════════════════════════════════════╗
║                   WHEN PATTERNS GO WRONG                   ║
╚════════════════════════════════════════════════════════════╝

Warning Signs:
─────────────────────────────────────────────────────────────
⚠️ More patterns than actual code
⚠️ 10+ layers of abstraction
⚠️ Simple task takes 100 lines
⚠️ Nobody understands the code (including you)
⚠️ "Enterprise" everything

Remember:
─────────────────────────────────────────────────────────────
"Patterns are tools to solve problems,
not goals in themselves.

Start simple.
Add patterns when needed.
Don't force them."

- Every senior developer
```

---

<div align="center">

## 🔗 Pattern Combinations

</div>

### Patterns Working Together 🤝

```
# ═══════════════════════════════════════════
# PATTERN COMBINATIONS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   COMMON COMBINATIONS                      ║
╚════════════════════════════════════════════════════════════╝

Factory + Singleton:
─────────────────────────────────────────────────────────────
Create objects using factory, but factory itself is singleton.
```

```javascript
class DatabaseFactory {
  static instance = null;

  static getInstance() {
    if (!DatabaseFactory.instance) {
      DatabaseFactory.instance = new DatabaseFactory();
    }
    return DatabaseFactory.instance;
  }

  createDatabase(type) {
    switch (type) {
      case "mysql":
        return new MySQLDatabase();
      case "postgres":
        return new PostgresDatabase();
      default:
        throw new Error("Unknown database type");
    }
  }
}

// Usage
const factory = DatabaseFactory.getInstance();
const db = factory.createDatabase("mysql");
```

```
Strategy + Factory:
─────────────────────────────────────────────────────────────
Factory creates different strategy implementations.
```

```javascript
// Strategies
class CreditCardPayment {
  pay(amount) {
    console.log(`Paid ${amount} with credit card`);
  }
}

class PayPalPayment {
  pay(amount) {
    console.log(`Paid ${amount} with PayPal`);
  }
}

// Factory
class PaymentFactory {
  static createPayment(type) {
    switch (type) {
      case "card":
        return new CreditCardPayment();
      case "paypal":
        return new PayPalPayment();
      default:
        throw new Error("Unknown payment type");
    }
  }
}

// Context
class ShoppingCart {
  constructor(paymentType) {
    this.payment = PaymentFactory.createPayment(paymentType);
  }

  checkout(amount) {
    this.payment.pay(amount);
  }
}

// Usage
const cart = new ShoppingCart("paypal");
cart.checkout(100);
```

```
Observer + Singleton:
─────────────────────────────────────────────────────────────
Event bus/manager as singleton, multiple observers.
```

```javascript
class EventBus {
  static instance = null;

  constructor() {
    if (EventBus.instance) {
      return EventBus.instance;
    }
    this.events = {};
    EventBus.instance = this;
  }

  on(event, callback) {
    if (!this.events[event]) {
      this.events[event] = [];
    }
    this.events[event].push(callback);
  }

  emit(event, data) {
    if (this.events[event]) {
      this.events[event].forEach((callback) => callback(data));
    }
  }
}

// Usage anywhere in app
const bus = new EventBus();
bus.on("userLogin", (user) => console.log("User logged in:", user));

// Somewhere else in app
const bus2 = new EventBus(); // Same instance!
bus2.emit("userLogin", { name: "John" });
```

```
Decorator + Strategy:
─────────────────────────────────────────────────────────────
Decorate strategies with additional behavior.
```

```javascript
// Base strategy
class BasicEncryption {
  encrypt(data) {
    return btoa(data); // Base64
  }
}

// Decorators
class CompressionDecorator {
  constructor(encryptor) {
    this.encryptor = encryptor;
  }

  encrypt(data) {
    console.log("Compressing...");
    const compressed = data; // Simplified
    return this.encryptor.encrypt(compressed);
  }
}

class LoggingDecorator {
  constructor(encryptor) {
    this.encryptor = encryptor;
  }

  encrypt(data) {
    console.log("Logging encryption...");
    return this.encryptor.encrypt(data);
  }
}

// Usage - Stack decorators
let encryptor = new BasicEncryption();
encryptor = new CompressionDecorator(encryptor);
encryptor = new LoggingDecorator(encryptor);

console.log(encryptor.encrypt("secret"));
// Logging encryption...
// Compressing...
// c2VjcmV0
```

```
╔════════════════════════════════════════════════════════════╗
║                   MVC PATTERN (COMBINATION)                ║
╚════════════════════════════════════════════════════════════╝

Model-View-Controller:
─────────────────────────────────────────────────────────────
Combines multiple patterns:
• Observer (View observes Model)
• Strategy (Controller strategies)
• Composite (View hierarchy)
```

```javascript
// Model (Observable)
class UserModel {
  constructor() {
    this.users = [];
    this.observers = [];
  }

  addUser(user) {
    this.users.push(user);
    this.notify();
  }

  getUsers() {
    return this.users;
  }

  subscribe(observer) {
    this.observers.push(observer);
  }

  notify() {
    this.observers.forEach((observer) => observer.update(this));
  }
}

// View (Observer)
class UserView {
  constructor(model) {
    this.model = model;
    this.model.subscribe(this);
  }

  update(model) {
    console.log("View updated with users:", model.getUsers());
  }

  render() {
    const users = this.model.getUsers();
    return users.map((u) => `<div>${u.name}</div>`).join("");
  }
}

// Controller
class UserController {
  constructor(model) {
    this.model = model;
  }

  addUser(name, email) {
    this.model.addUser({ name, email });
  }
}

// Usage
const model = new UserModel();
const view = new UserView(model);
const controller = new UserController(model);

controller.addUser("John", "john@example.com");
// View updated with users: [{ name: 'John', email: 'john@example.com' }]

console.log(view.render());
// <div>John</div>
```

---

<div align="center">

## 💡 Best Practices

</div>

### Master Design Patterns 🎓

```
# ═══════════════════════════════════════════
# DESIGN PATTERN BEST PRACTICES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   LEARNING PATTERNS                        ║
╚════════════════════════════════════════════════════════════╝

Start Simple:
─────────────────────────────────────────────────────────────
1. Learn one pattern at a time
2. Understand the problem it solves
3. Implement it yourself
4. Use it in real project
5. Move to next pattern

Don't Memorize - Understand:
─────────────────────────────────────────────────────────────
❌ Memorizing code examples
✅ Understanding when and why to use

Practice Order:
─────────────────────────────────────────────────────────────
Beginner:
1. Singleton (easy to understand)
2. Factory Method (very practical)
3. Observer (event-driven apps)
4. Strategy (algorithm switching)
5. Decorator (add features)

Intermediate:
6. Builder (complex objects)
7. Adapter (integrate systems)
8. Facade (simplify interfaces)
9. Template Method (algorithms)
10. State (state machines)

Advanced:
11. Abstract Factory
12. Proxy
13. Composite
14. Chain of Responsibility
15. Command

╔════════════════════════════════════════════════════════════╗
║                   WHEN TO USE PATTERNS                     ║
╚════════════════════════════════════════════════════════════╝

Decision Tree:
─────────────────────────────────────────────────────────────

Need to create objects?
├─ Complex creation logic? → Builder
├─ Don't know exact type? → Factory
├─ Only one instance? → Singleton
└─ Copy existing? → Prototype

Need to structure objects?
├─ Incompatible interfaces? → Adapter
├─ Add features dynamically? → Decorator
├─ Simplify complex system? → Facade
└─ Control access? → Proxy

Need objects to communicate?
├─ Notify multiple objects? → Observer
├─ Switch algorithms? → Strategy
├─ Behavior based on state? → State
├─ Pass request along chain? → Chain of Responsibility
└─ Encapsulate requests? → Command

╔════════════════════════════════════════════════════════════╗
║                   PRACTICAL GUIDELINES                     ║
╚════════════════════════════════════════════════════════════╝

1. Don't Force Patterns:
─────────────────────────────────────────────────────────────
✅ Let them emerge naturally
✅ Refactor into patterns when needed
❌ Don't start with patterns

2. Start Simple, Refactor Later:
─────────────────────────────────────────────────────────────
"Make it work, make it right, make it fast"
- Kent Beck

Step 1: Write simple code that works
Step 2: Identify problems/smells
Step 3: Apply appropriate pattern
Step 4: Optimize if needed

3. Know When NOT to Use:
─────────────────────────────────────────────────────────────
❌ Simple scripts/prototypes
❌ Quick one-off tasks
❌ Team doesn't understand patterns
❌ Adds unnecessary complexity

4. Communicate with Team:
─────────────────────────────────────────────────────────────
✅ Use pattern names (common vocabulary)
✅ Document why pattern was chosen
✅ Ensure team understands
✅ Code reviews discuss patterns

5. Test Your Patterns:
─────────────────────────────────────────────────────────────
✅ Patterns should make testing easier
✅ Mock dependencies
✅ Test each component separately
✅ Integration tests

╔════════════════════════════════════════════════════════════╗
║                   CODE QUALITY CHECKLIST                   ║
╚════════════════════════════════════════════════════════════╝

Before Applying Pattern:
─────────────────────────────────────────────────────────────
☐ Do I understand the problem?
☐ Is there actually a problem?
☐ Is this the right pattern?
☐ Does it simplify or complicate?
☐ Will the team understand it?
☐ Can I test it easily?
☐ Is it maintainable?
☐ Am I over-engineering?

After Applying Pattern:
─────────────────────────────────────────────────────────────
☐ Code is easier to understand?
☐ Easier to extend?
☐ Easier to test?
☐ Less coupled?
☐ Follows SOLID principles?
☐ Team can maintain it?

╔════════════════════════════════════════════════════════════╗
║                   COMMON MISTAKES                          ║
╚════════════════════════════════════════════════════════════╝

1. Pattern for Pattern's Sake:
─────────────────────────────────────────────────────────────
❌ "Let's use Strategy pattern because it's cool"
✅ "We need to switch algorithms, Strategy fits"

2. Premature Patterning:
─────────────────────────────────────────────────────────────
❌ Start with complex pattern structure
✅ Start simple, refactor into pattern when needed

3. Wrong Pattern Choice:
─────────────────────────────────────────────────────────────
❌ Force pattern that doesn't fit
✅ Choose pattern that solves your problem

4. Over-Engineering:
─────────────────────────────────────────────────────────────
❌ 10 patterns for simple app
✅ Patterns only where they add value

5. Ignoring Context:
─────────────────────────────────────────────────────────────
❌ "This pattern worked in Java, use in JavaScript"
✅ Adapt pattern to language/framework

╔════════════════════════════════════════════════════════════╗
║                   LEARNING RESOURCES                       ║
╚════════════════════════════════════════════════════════════╝

Books:
─────────────────────────────────────────────────────────────
📚 "Design Patterns" - Gang of Four (Original)
📚 "Head First Design Patterns" - Freeman (Best for beginners)
📚 "Refactoring" - Martin Fowler
📚 "Clean Code" - Robert Martin
📚 "Design Patterns in JavaScript" - Addy Osmani (Free online)

Websites:
─────────────────────────────────────────────────────────────
🔗 refactoring.guru (Best visual explanations)
🔗 sourcemaking.com (Anti-patterns too)
🔗 patterns.dev (Modern JavaScript patterns)
🔗 github.com/kamranahmedse/design-patterns-for-humans

Practice:
─────────────────────────────────────────────────────────────
💪 Implement each pattern yourself
💪 Use in real projects
💪 Code reviews
💪 Teach others (best way to learn)
💪 Refactor existing code

╔════════════════════════════════════════════════════════════╗
║                   FINAL WISDOM                             ║
╚════════════════════════════════════════════════════════════╝

Remember:
─────────────────────────────────────────────────────────────

"Patterns are tools in your toolbox.
A good carpenter knows when to use a hammer,
when to use a screwdriver,
and when to put tools away and solve problem differently.

Start simple.
Add patterns when they solve real problems.
Refactor fearlessly.
Keep learning.

The goal is not to use all patterns.
The goal is to write maintainable code."

Key Takeaways:
─────────────────────────────────────────────────────────────
✅ Patterns solve common problems
✅ Not all problems need patterns
✅ Understand SOLID principles first
✅ Learn by doing, not reading
✅ Refactor into patterns, don't start with them
✅ Simple is better than complex
✅ Patterns are means, not ends
✅ Team understanding > individual genius

Now go write clean, maintainable code! 🚀
```

---

<div align="center">

## 📊 Quick Reference

</div>

### Pattern Cheat Sheet 📝

| Pattern                     | Category   | Problem                   | Solution               | Use When                 |
| --------------------------- | ---------- | ------------------------- | ---------------------- | ------------------------ |
| **Singleton**               | Creational | Need one instance         | Single global instance | Database, config, logger |
| **Factory**                 | Creational | Don't know exact type     | Create via factory     | Object creation varies   |
| **Builder**                 | Creational | Complex construction      | Build step-by-step     | Many parameters          |
| **Prototype**               | Creational | Expensive creation        | Clone existing         | Performance critical     |
| **Adapter**                 | Structural | Incompatible interfaces   | Convert interface      | Legacy integration       |
| **Decorator**               | Structural | Add features dynamically  | Wrap with features     | Flexible extensions      |
| **Facade**                  | Structural | Complex subsystem         | Simple interface       | Simplify complexity      |
| **Proxy**                   | Structural | Control access            | Surrogate object       | Lazy load, security      |
| **Observer**                | Behavioral | Notify multiple objects   | Subscribe/notify       | Events, data binding     |
| **Strategy**                | Behavioral | Switch algorithms         | Encapsulate algorithm  | Multiple algorithms      |
| **Command**                 | Behavioral | Encapsulate request       | Request as object      | Undo/redo, queues        |
| **State**                   | Behavioral | Behavior changes by state | State objects          | State machines           |
| **Template Method**         | Behavioral | Common algorithm          | Define skeleton        | Framework design         |
| **Chain of Responsibility** | Behavioral | Multiple handlers         | Chain handlers         | Middleware, events       |

### SOLID Quick Reference

| Principle                     | Means                                       | Example                      |
| ----------------------------- | ------------------------------------------- | ---------------------------- |
| **S** - Single Responsibility | One reason to change                        | User class vs UserRepository |
| **O** - Open/Closed           | Open for extension, closed for modification | Shape hierarchy              |
| **L** - Liskov Substitution   | Subclass can replace superclass             | Proper inheritance           |
| **I** - Interface Segregation | Many specific interfaces                    | Worker interfaces            |
| **D** - Dependency Inversion  | Depend on abstractions                      | Inject dependencies          |

---

<div align="center">

**Built with 🏛️ by MrDib, for better software design**

_Remember: "Patterns are solutions, not goals!"_ ✨

**Happy Coding!** 🚀

</div>

---

## 🔗 Related Guides

- [System Design](./System-Design.md)
- [Best Practices](./Best-Practices.md)
- [Clean Code](../Development/Clean-Code.md)
- [Software Architecture](./Microservices.md)

---

## 📖 Further Reading

### Recommended Books:

- 📚 **Head First Design Patterns** - Best for beginners
- 📚 **Design Patterns (GoF)** - The classic
- 📚 **Refactoring** by Martin Fowler
- 📚 **Clean Code** by Robert Martin

### Online Resources:

- 🔗 [Refactoring.Guru](https://refactoring.guru/design-patterns) - Best visual guide
- 🔗 [SourceMaking](https://sourcemaking.com/design_patterns)
- 🔗 [Patterns.dev](https://patterns.dev) - Modern JavaScript patterns
- 🔗 [GitHub: Design Patterns for Humans](https://github.com/kamranahmedse/design-patterns-for-humans)

---
