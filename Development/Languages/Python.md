<div align="center">

# 🐍 Python - Powerful, Elegant, Simple

### _Write code that works, reads well, and scales_ ✨

![Python](https://img.shields.io/badge/Python-3.9+-blue?style=for-the-badge&logo=python)
![Versatile](https://img.shields.io/badge/Use_Cases-Everything-green?style=for-the-badge)

</div>

---

## 📚 Table of Contents

- [🎯 Python Fundamentals](#-python-fundamentals)
- [📊 Data Types & Structures](#-data-types--structures)
- [🔄 Control Flow](#-control-flow)
- [🔧 Functions & Modules](#-functions--modules)
- [🏗️ Object-Oriented Programming](#️-object-oriented-programming)
- [📂 File Operations](#-file-operations)
- [⚠️ Error Handling](#️-error-handling)
- [📦 Virtual Environments](#-virtual-environments)
- [🌐 Web Development](#-web-development)
- [📊 Data Science](#-data-science)
- [🧪 Testing](#-testing)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 🎯 Python Fundamentals

</div>

### Getting Started 🚀

```bash
# ═══════════════════════════════════════════
# Installation & Setup
# ═══════════════════════════════════════════

# Check Python version
python3 --version

# macOS
brew install python3

# Linux (Ubuntu/Debian)
sudo apt update
sudo apt install python3 python3-pip

# Windows
# Download from: https://python.org/downloads/

# Verify installation
python3 --version
pip3 --version

# ═══════════════════════════════════════════
# Running Python Code
# ═══════════════════════════════════════════

# Interactive mode (REPL)
python3

# Run script
python3 script.py

# Run with arguments
python3 script.py arg1 arg2

# Execute one-liner
python3 -c "print('Hello, World!')"

# Run module as script
python3 -m http.server 8000
```

---

### Basic Syntax 📝

```python
# ═══════════════════════════════════════════
# Hello World & Comments
# ═══════════════════════════════════════════

print("Hello, World!")  # Single-line comment

"""
Multi-line comment
or docstring
"""

'''
Also a multi-line comment
'''

# ═══════════════════════════════════════════
# Variables & Constants
# ═══════════════════════════════════════════

# Variables (dynamic typing)
name = "MrDib"          # str
age = 25                # int
height = 5.9            # float
is_active = True        # bool
nothing = None          # NoneType

# Multiple assignment
x, y, z = 1, 2, 3
a = b = c = 0

# Unpacking
first, *rest, last = [1, 2, 3, 4, 5]
# first = 1, rest = [2, 3, 4], last = 5

# Constants (convention: UPPERCASE)
MAX_SIZE = 100
API_KEY = "secret_key"

# ═══════════════════════════════════════════
# Type Hints (Python 3.5+)
# ═══════════════════════════════════════════

def greet(name: str) -> str:
    return f"Hello, {name}!"

age: int = 25
names: list[str] = ["Alice", "Bob"]
data: dict[str, int] = {"a": 1, "b": 2}

# Optional types
from typing import Optional, Union, List, Dict

def get_user(user_id: int) -> Optional[dict]:
    return None  # or return user dict

# ═══════════════════════════════════════════
# String Operations
# ═══════════════════════════════════════════

# String creation
single = 'Hello'
double = "World"
multi = """
Multiple
lines
"""

# String formatting
name = "MrDib"
age = 25

# f-strings (Python 3.6+) - RECOMMENDED
message = f"My name is {name} and I'm {age} years old"
calculation = f"2 + 2 = {2 + 2}"

# format method
message = "My name is {} and I'm {} years old".format(name, age)
message = "My name is {n} and I'm {a} years old".format(n=name, a=age)

# % formatting (old style)
message = "My name is %s and I'm %d years old" % (name, age)

# String methods
text = "  Hello World  "
text.upper()          # "  HELLO WORLD  "
text.lower()          # "  hello world  "
text.strip()          # "Hello World"
text.replace("World", "Python")  # "  Hello Python  "
text.split()          # ["Hello", "World"]

# String checking
text.startswith("Hello")  # False (has spaces)
text.strip().startswith("Hello")  # True
text.endswith("World")
"123".isdigit()       # True
"abc".isalpha()       # True

# ═══════════════════════════════════════════
# Input & Output
# ═══════════════════════════════════════════

# Input
name = input("Enter your name: ")
age = int(input("Enter your age: "))  # Convert to int

# Output
print("Hello, World!")
print("Name:", name, "Age:", age)
print(f"Name: {name}, Age: {age}")

# Print without newline
print("Loading", end="...")

# Print to file
with open("output.txt", "w") as f:
    print("Hello", file=f)
```

---

<div align="center">

## 📊 Data Types & Structures

</div>

### Built-in Data Types 📦

```python
# ═══════════════════════════════════════════
# Numbers
# ═══════════════════════════════════════════

# Integer
x = 42
x = 0b1010      # Binary: 10
x = 0o12        # Octal: 10
x = 0xA         # Hexadecimal: 10

# Float
pi = 3.14159
scientific = 1.5e-3  # 0.0015

# Complex
z = 3 + 4j
z.real          # 3.0
z.imag          # 4.0

# Arithmetic
a + b           # Addition
a - b           # Subtraction
a * b           # Multiplication
a / b           # Division (float)
a // b          # Floor division
a % b           # Modulo
a ** b          # Exponentiation

# Built-in functions
abs(-5)         # 5
round(3.7)      # 4
pow(2, 3)       # 8
max(1, 2, 3)    # 3
min(1, 2, 3)    # 1

# ═══════════════════════════════════════════
# Lists (Mutable)
# ═══════════════════════════════════════════

# Create list
fruits = ["apple", "banana", "cherry"]
numbers = [1, 2, 3, 4, 5]
mixed = [1, "hello", 3.14, True]
empty = []

# Access elements
fruits[0]           # "apple" (first)
fruits[-1]          # "cherry" (last)
fruits[1:3]         # ["banana", "cherry"] (slice)
fruits[:2]          # ["apple", "banana"]
fruits[2:]          # ["cherry"]
fruits[::2]         # ["apple", "cherry"] (step)

# Modify list
fruits[0] = "orange"        # Change element
fruits.append("grape")      # Add to end
fruits.insert(1, "mango")   # Insert at index
fruits.extend(["kiwi", "melon"])  # Add multiple
fruits.remove("banana")     # Remove by value
del fruits[0]               # Remove by index
popped = fruits.pop()       # Remove and return last
fruits.clear()              # Remove all

# List operations
len(fruits)         # Length
fruits.count("apple")   # Count occurrences
fruits.index("banana")  # Find index
fruits.sort()       # Sort in-place
sorted(fruits)      # Return sorted copy
fruits.reverse()    # Reverse in-place
fruits.copy()       # Shallow copy

# List comprehension
squares = [x**2 for x in range(10)]
# [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

evens = [x for x in range(20) if x % 2 == 0]
# [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]

# Nested comprehension
matrix = [[i*j for j in range(3)] for i in range(3)]
# [[0, 0, 0], [0, 1, 2], [0, 2, 4]]

# ═══════════════════════════════════════════
# Tuples (Immutable)
# ═══════════════════════════════════════════

# Create tuple
point = (3, 4)
single = (1,)       # Comma needed for single element
empty = ()
mixed = (1, "hello", 3.14)

# Access (same as list)
x, y = point        # Unpacking
first, *rest = (1, 2, 3, 4)  # first=1, rest=[2,3,4]

# Tuple operations
len(point)
point.count(3)
point.index(4)

# Named tuples
from collections import namedtuple

Point = namedtuple('Point', ['x', 'y'])
p = Point(3, 4)
p.x, p.y            # 3, 4

# ═══════════════════════════════════════════
# Sets (Unique, Unordered)
# ═══════════════════════════════════════════

# Create set
fruits = {"apple", "banana", "cherry"}
numbers = {1, 2, 3, 4, 5}
empty = set()       # {} creates empty dict!

# Set from list (removes duplicates)
unique = set([1, 2, 2, 3, 3, 3])  # {1, 2, 3}

# Add/remove
fruits.add("orange")
fruits.remove("banana")     # Error if not exists
fruits.discard("banana")    # No error
fruits.pop()                # Remove random
fruits.clear()

# Set operations
a = {1, 2, 3, 4}
b = {3, 4, 5, 6}

a | b               # Union: {1, 2, 3, 4, 5, 6}
a & b               # Intersection: {3, 4}
a - b               # Difference: {1, 2}
a ^ b               # Symmetric difference: {1, 2, 5, 6}

a.issubset(b)       # False
a.issuperset(b)     # False
a.isdisjoint(b)     # False

# Set comprehension
squares = {x**2 for x in range(10)}

# ═══════════════════════════════════════════
# Dictionaries (Key-Value Pairs)
# ═══════════════════════════════════════════

# Create dictionary
person = {
    "name": "MrDib",
    "age": 25,
    "city": "Tokyo"
}

# Alternative creation
person = dict(name="MrDib", age=25, city="Tokyo")

# Access elements
person["name"]              # "MrDib"
person.get("age")           # 25
person.get("country", "Unknown")  # Default value

# Modify
person["age"] = 26          # Update
person["email"] = "email@example.com"  # Add
del person["city"]          # Delete
person.pop("age")           # Remove and return

# Dictionary methods
person.keys()               # Keys view
person.values()             # Values view
person.items()              # (key, value) pairs

person.update({"age": 27, "country": "Japan"})
person.clear()

# Dictionary comprehension
squares = {x: x**2 for x in range(5)}
# {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}

# Nested dictionaries
users = {
    "user1": {"name": "Alice", "age": 25},
    "user2": {"name": "Bob", "age": 30}
}

# Default dict
from collections import defaultdict

counts = defaultdict(int)  # Default value: 0
counts["a"] += 1           # No KeyError

# ═══════════════════════════════════════════
# Type Conversion
# ═══════════════════════════════════════════

# To integer
int("42")           # 42
int(3.14)           # 3
int("1010", 2)      # 10 (binary)

# To float
float("3.14")       # 3.14
float(42)           # 42.0

# To string
str(42)             # "42"
str(3.14)           # "3.14"

# To list
list("hello")       # ['h', 'e', 'l', 'l', 'o']
list((1, 2, 3))     # [1, 2, 3]

# To tuple
tuple([1, 2, 3])    # (1, 2, 3)

# To set
set([1, 2, 2, 3])   # {1, 2, 3}

# To dict
dict([("a", 1), ("b", 2)])  # {'a': 1, 'b': 2}
```

---

<div align="center">

## 🔄 Control Flow

</div>

### Conditionals & Loops 🔀

```python
# ═══════════════════════════════════════════
# If/Elif/Else
# ═══════════════════════════════════════════

age = 25

if age < 18:
    print("Minor")
elif age < 65:
    print("Adult")
else:
    print("Senior")

# Ternary operator
status = "adult" if age >= 18 else "minor"

# Multiple conditions
if age >= 18 and age < 65:
    print("Working age")

if age < 18 or age > 65:
    print("Not working age")

# Checking existence
if "key" in my_dict:
    print("Key exists")

if item not in my_list:
    print("Item not found")

# Truthiness
if my_list:         # True if not empty
    print("List has items")

if not my_string:   # True if empty
    print("String is empty")

# ═══════════════════════════════════════════
# For Loops
# ═══════════════════════════════════════════

# Iterate over sequence
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)

# Range
for i in range(5):          # 0 to 4
    print(i)

for i in range(1, 6):       # 1 to 5
    print(i)

for i in range(0, 10, 2):   # 0, 2, 4, 6, 8
    print(i)

# Enumerate (index + value)
for index, fruit in enumerate(fruits):
    print(f"{index}: {fruit}")

# Start index at 1
for index, fruit in enumerate(fruits, start=1):
    print(f"{index}. {fruit}")

# Dictionary iteration
person = {"name": "MrDib", "age": 25}

for key in person:
    print(key, person[key])

for key, value in person.items():
    print(f"{key}: {value}")

# Zip (parallel iteration)
names = ["Alice", "Bob", "Charlie"]
ages = [25, 30, 35]

for name, age in zip(names, ages):
    print(f"{name} is {age} years old")

# ═══════════════════════════════════════════
# While Loops
# ═══════════════════════════════════════════

count = 0
while count < 5:
    print(count)
    count += 1

# Infinite loop
while True:
    response = input("Continue? (y/n): ")
    if response == "n":
        break

# ═══════════════════════════════════════════
# Loop Control
# ═══════════════════════════════════════════

# Break - exit loop
for i in range(10):
    if i == 5:
        break
    print(i)

# Continue - skip iteration
for i in range(10):
    if i % 2 == 0:
        continue
    print(i)  # Only odd numbers

# Else clause (executes if no break)
for i in range(5):
    print(i)
else:
    print("Loop completed normally")

# Pass - do nothing
for i in range(5):
    if i == 3:
        pass  # Placeholder
    print(i)

# ═══════════════════════════════════════════
# Match/Case (Python 3.10+)
# ═══════════════════════════════════════════

command = "start"

match command:
    case "start":
        print("Starting...")
    case "stop":
        print("Stopping...")
    case "pause" | "hold":
        print("Pausing...")
    case _:  # Default
        print("Unknown command")

# Pattern matching with values
point = (0, 0)

match point:
    case (0, 0):
        print("Origin")
    case (0, y):
        print(f"Y-axis at {y}")
    case (x, 0):
        print(f"X-axis at {x}")
    case (x, y):
        print(f"Point at ({x}, {y})")

# ═══════════════════════════════════════════
# Comprehensions (Elegant Loops)
# ═══════════════════════════════════════════

# List comprehension
squares = [x**2 for x in range(10)]

# With condition
evens = [x for x in range(20) if x % 2 == 0]

# Nested
matrix = [[i*j for j in range(3)] for i in range(3)]

# Dict comprehension
square_dict = {x: x**2 for x in range(5)}

# Set comprehension
unique_lengths = {len(word) for word in ["hello", "world", "hi"]}

# Generator expression (memory efficient)
sum_of_squares = sum(x**2 for x in range(1000000))
```

---

<div align="center">

## 🔧 Functions & Modules

</div>

### Functions 📦

```python
# ═══════════════════════════════════════════
# Basic Functions
# ═══════════════════════════════════════════

def greet(name):
    """Greet someone by name."""
    return f"Hello, {name}!"

result = greet("MrDib")

# Multiple returns
def get_user():
    return "MrDib", 25, "Tokyo"

name, age, city = get_user()

# Default parameters
def greet(name, greeting="Hello"):
    return f"{greeting}, {name}!"

greet("MrDib")                  # "Hello, MrDib!"
greet("MrDib", "Hi")           # "Hi, MrDib!"

# Keyword arguments
def create_user(name, age, city="Unknown"):
    return {"name": name, "age": age, "city": city}

user = create_user(name="MrDib", age=25, city="Tokyo")
user = create_user("MrDib", 25)  # city="Unknown"

# ═══════════════════════════════════════════
# Variable Arguments
# ═══════════════════════════════════════════

# *args (positional arguments)
def sum_all(*numbers):
    return sum(numbers)

total = sum_all(1, 2, 3, 4, 5)  # 15

# **kwargs (keyword arguments)
def print_info(**info):
    for key, value in info.items():
        print(f"{key}: {value}")

print_info(name="MrDib", age=25, city="Tokyo")

# Combined
def process(*args, **kwargs):
    print("Args:", args)
    print("Kwargs:", kwargs)

process(1, 2, 3, name="MrDib", age=25)

# ═══════════════════════════════════════════
# Lambda Functions (Anonymous)
# ═══════════════════════════════════════════

# Basic lambda
square = lambda x: x**2
square(5)  # 25

# Multiple arguments
add = lambda x, y: x + y
add(3, 4)  # 7

# Common with map, filter, sorted
numbers = [1, 2, 3, 4, 5]

# Map
squared = list(map(lambda x: x**2, numbers))

# Filter
evens = list(filter(lambda x: x % 2 == 0, numbers))

# Sorted
people = [{"name": "Alice", "age": 25}, {"name": "Bob", "age": 30}]
sorted_people = sorted(people, key=lambda x: x["age"])

# ═══════════════════════════════════════════
# Decorators
# ═══════════════════════════════════════════

# Simple decorator
def timer(func):
    import time
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        end = time.time()
        print(f"{func.__name__} took {end - start:.4f} seconds")
        return result
    return wrapper

@timer
def slow_function():
    import time
    time.sleep(1)
    return "Done"

# Decorator with arguments
def repeat(times):
    def decorator(func):
        def wrapper(*args, **kwargs):
            for _ in range(times):
                result = func(*args, **kwargs)
            return result
        return wrapper
    return decorator

@repeat(3)
def say_hello():
    print("Hello!")

# Common decorators
@staticmethod       # No self parameter
@classmethod        # Receives class as first parameter
@property          # Make method accessible like attribute

# ═══════════════════════════════════════════
# Generators
# ═══════════════════════════════════════════

def count_up_to(n):
    count = 1
    while count <= n:
        yield count
        count += 1

# Use generator
for num in count_up_to(5):
    print(num)

# Generator expression
squares_gen = (x**2 for x in range(1000000))  # Memory efficient

# ═══════════════════════════════════════════
# Type Hints (Python 3.5+)
# ═══════════════════════════════════════════

from typing import List, Dict, Tuple, Optional, Union

def process_names(names: List[str]) -> Dict[str, int]:
    return {name: len(name) for name in names}

def get_user(user_id: int) -> Optional[Dict[str, Union[str, int]]]:
    if user_id > 0:
        return {"name": "MrDib", "age": 25}
    return None

# Multiple return types
def divide(a: float, b: float) -> Tuple[float, str]:
    return a / b, "success"

# ═══════════════════════════════════════════
# Docstrings
# ═══════════════════════════════════════════

def calculate_area(radius: float) -> float:
    """
    Calculate the area of a circle.

    Args:
        radius: The radius of the circle

    Returns:
        The area of the circle

    Raises:
        ValueError: If radius is negative

    Examples:
        >>> calculate_area(5)
        78.53981633974483
    """
    if radius < 0:
        raise ValueError("Radius cannot be negative")
    return 3.14159 * radius ** 2
```

---

### Modules & Packages 📚

```python
# ═══════════════════════════════════════════
# Importing Modules
# ═══════════════════════════════════════════

# Import entire module
import math
result = math.sqrt(16)

# Import specific items
from math import sqrt, pi
result = sqrt(16)

# Import with alias
import numpy as np
array = np.array([1, 2, 3])

# Import all (not recommended)
from math import *

# Relative imports (in packages)
from . import module          # Same directory
from .. import module         # Parent directory
from ..sibling import module  # Sibling directory

# ═══════════════════════════════════════════
# Creating Modules
# ═══════════════════════════════════════════

# mymodule.py
def greet(name):
    return f"Hello, {name}!"

PI = 3.14159

class Calculator:
    @staticmethod
    def add(a, b):
        return a + b

# Use in another file
import mymodule

message = mymodule.greet("MrDib")
result = mymodule.Calculator.add(5, 3)

# ═══════════════════════════════════════════
# Package Structure
# ═══════════════════════════════════════════

'''
mypackage/
├── __init__.py
├── module1.py
├── module2.py
└── subpackage/
    ├── __init__.py
    └── module3.py
'''

# __init__.py
from .module1 import function1
from .module2 import function2

__all__ = ['function1', 'function2']

# Usage
from mypackage import function1
from mypackage.subpackage import module3

# ═══════════════════════════════════════════
# Useful Standard Library Modules
# ═══════════════════════════════════════════

# os - Operating system interface
import os
os.getcwd()                 # Current directory
os.listdir('.')             # List directory
os.path.join('dir', 'file') # Path joining
os.makedirs('path/to/dir', exist_ok=True)

# sys - System-specific parameters
import sys
sys.argv                    # Command-line arguments
sys.exit(0)                 # Exit program
sys.path                    # Module search path

# datetime - Date and time
from datetime import datetime, timedelta
now = datetime.now()
tomorrow = now + timedelta(days=1)
formatted = now.strftime("%Y-%m-%d %H:%M:%S")

# json - JSON encoding/decoding
import json
data = {"name": "MrDib", "age": 25}
json_str = json.dumps(data)
parsed = json.loads(json_str)

# pathlib - Object-oriented filesystem paths
from pathlib import Path
path = Path('myfile.txt')
path.exists()
path.read_text()
path.write_text("content")

# collections - Specialized containers
from collections import Counter, defaultdict, OrderedDict
counts = Counter(['a', 'b', 'a', 'c', 'b', 'a'])
# Counter({'a': 3, 'b': 2, 'c': 1})

# itertools - Iteration tools
from itertools import chain, cycle, combinations
combined = chain([1, 2], [3, 4])  # Combine iterables
pairs = combinations([1, 2, 3, 4], 2)  # All 2-item combinations

# functools - Higher-order functions
from functools import lru_cache, partial

@lru_cache(maxsize=None)
def fibonacci(n):
    if n < 2:
        return n
    return fibonacci(n-1) + fibonacci(n-2)

# random - Random number generation
import random
random.randint(1, 10)       # Random integer
random.choice(['a', 'b', 'c'])  # Random choice
random.shuffle(my_list)      # Shuffle in-place
random.sample(my_list, 3)   # Random sample

# re - Regular expressions
import re
pattern = r'\d+'
matches = re.findall(pattern, "abc123def456")  # ['123', '456']
text = re.sub(r'\d+', 'X', "abc123def")  # "abcXdef"
```

---

<div align="center">

## 🏗️ Object-Oriented Programming

</div>

### Classes & Objects 🎯

```python
# ═══════════════════════════════════════════
# Basic Class
# ═══════════════════════════════════════════

class Dog:
    # Class attribute
    species = "Canis familiaris"

    # Constructor
    def __init__(self, name, age):
        # Instance attributes
        self.name = name
        self.age = age

    # Instance method
    def bark(self):
        return f"{self.name} says woof!"

    # String representation
    def __str__(self):
        return f"{self.name} is {self.age} years old"

# Create instance
dog = Dog("Buddy", 3)
print(dog.bark())    # "Buddy says woof!"
print(dog)           # "Buddy is 3 years old"

# ═══════════════════════════════════════════
# Inheritance
# ═══════════════════════════════════════════

class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        raise NotImplementedError("Subclass must implement")

class Dog(Animal):
    def speak(self):
        return f"{self.name} says Woof!"

class Cat(Animal):
    def speak(self):
        return f"{self.name} says Meow!"

# Multiple inheritance
class Robot:
    def charge(self):
        return "Charging..."

class RobotDog(Dog, Robot):
    pass

# ═══════════════════════════════════════════
# Special Methods (Magic/Dunder Methods)
# ═══════════════════════════════════════════

class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    # String representation
    def __str__(self):
        return f"Vector({self.x}, {self.y})"

    def __repr__(self):
        return f"Vector(x={self.x}, y={self.y})"

    # Arithmetic operations
    def __add__(self, other):
        return Vector(self.x + other.x, self.y + other.y)

    def __sub__(self, other):
        return Vector(self.x - other.x, self.y - other.y)

    # Comparison
    def __eq__(self, other):
        return self.x == other.x and self.y == other.y

    # Length
    def __len__(self):
        return int((self.x**2 + self.y**2)**0.5)

    # Indexing
    def __getitem__(self, index):
        return [self.x, self.y][index]

v1 = Vector(1, 2)
v2 = Vector(3, 4)
v3 = v1 + v2  # Vector(4, 6)

# ═══════════════════════════════════════════
# Properties & Decorators
# ═══════════════════════════════════════════

class User:
    def __init__(self, name, email):
        self._name = name
        self._email = email

    # Getter
    @property
    def name(self):
        return self._name

    # Setter
    @name.setter
    def name(self, value):
        if not value:
            raise ValueError("Name cannot be empty")
        self._name = value

    # Deleter
    @name.deleter
    def name(self):
        del self._name

    # Read-only property
    @property
    def display_name(self):
        return f"User: {self._name}"

user = User("MrDib", "email@example.com")
user.name = "NewName"  # Uses setter
print(user.display_name)  # Uses getter

# ═══════════════════════════════════════════
# Class Methods & Static Methods
# ═══════════════════════════════════════════

class MyClass:
    count = 0

    def __init__(self, name):
        self.name = name
        MyClass.count += 1

    # Instance method (has access to instance)
    def instance_method(self):
        return f"Instance: {self.name}"

    # Class method (has access to class)
    @classmethod
    def class_method(cls):
        return f"Class has {cls.count} instances"

    # Static method (no access to instance or class)
    @staticmethod
    def static_method():
        return "This is a static method"

    # Alternative constructor
    @classmethod
    def from_string(cls, string):
        name = string.split(',')[0]
        return cls(name)

obj1 = MyClass("Object1")
obj2 = MyClass.from_string("Object2,extra")
print(MyClass.class_method())  # "Class has 2 instances"

# ═══════════════════════════════════════════
# Dataclasses (Python 3.7+)
# ═══════════════════════════════════════════

from dataclasses import dataclass, field
from typing import List

@dataclass
class Person:
    name: str
    age: int
    email: str = "unknown"
    hobbies: List[str] = field(default_factory=list)

    def greet(self):
        return f"Hello, I'm {self.name}"

person = Person("MrDib", 25, hobbies=["coding", "gaming"])
print(person)  # Person(name='MrDib', age=25, ...)

# ═══════════════════════════════════════════
# Abstract Base Classes
# ═══════════════════════════════════════════

from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

    @abstractmethod
    def perimeter(self):
        pass

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

    def perimeter(self):
        return 2 * (self.width + self.height)

# ═══════════════════════════════════════════
# Context Managers
# ═══════════════════════════════════════════

class FileManager:
    def __init__(self, filename, mode):
        self.filename = filename
        self.mode = mode
        self.file = None

    def __enter__(self):
        self.file = open(self.filename, self.mode)
        return self.file

    def __exit__(self, exc_type, exc_val, exc_tb):
        if self.file:
            self.file.close()

# Usage
with FileManager('test.txt', 'w') as f:
    f.write('Hello, World!')

# Simpler with contextlib
from contextlib import contextmanager

@contextmanager
def file_manager(filename, mode):
    f = open(filename, mode)
    try:
        yield f
    finally:
        f.close()
```

---

<div align="center">

## 📂 File Operations

</div>

### Reading & Writing Files 📄

```python
# ═══════════════════════════════════════════
# Reading Files
# ═══════════════════════════════════════════

# Read entire file
with open('file.txt', 'r') as f:
    content = f.read()

# Read lines as list
with open('file.txt', 'r') as f:
    lines = f.readlines()

# Read line by line
with open('file.txt', 'r') as f:
    for line in f:
        print(line.strip())

# Read with specific encoding
with open('file.txt', 'r', encoding='utf-8') as f:
    content = f.read()

# ═══════════════════════════════════════════
# Writing Files
# ═══════════════════════════════════════════

# Write (overwrite)
with open('file.txt', 'w') as f:
    f.write('Hello, World!\n')
    f.write('Second line\n')

# Write lines from list
lines = ['Line 1\n', 'Line 2\n', 'Line 3\n']
with open('file.txt', 'w') as f:
    f.writelines(lines)

# Append
with open('file.txt', 'a') as f:
    f.write('Appended line\n')

# ═══════════════════════════════════════════
# Working with Paths
# ═══════════════════════════════════════════

from pathlib import Path

# Create Path object
path = Path('myfile.txt')

# Check existence
if path.exists():
    print("File exists")

# Read/write with Path
content = path.read_text()
path.write_text('Hello, World!')

# File info
path.stat().st_size  # File size
path.suffix          # File extension
path.stem            # Filename without extension
path.parent          # Parent directory

# Directory operations
dir_path = Path('mydir')
dir_path.mkdir(exist_ok=True)  # Create directory

# List files
for file in dir_path.glob('*.txt'):
    print(file)

# ═══════════════════════════════════════════
# JSON Files
# ═══════════════════════════════════════════

import json

# Write JSON
data = {"name": "MrDib", "age": 25, "hobbies": ["coding", "gaming"]}
with open('data.json', 'w') as f:
    json.dump(data, f, indent=2)

# Read JSON
with open('data.json', 'r') as f:
    data = json.load(f)

# ═══════════════════════════════════════════
# CSV Files
# ═══════════════════════════════════════════

import csv

# Write CSV
data = [
    ['Name', 'Age', 'City'],
    ['Alice', '25', 'Tokyo'],
    ['Bob', '30', 'NYC']
]

with open('data.csv', 'w', newline='') as f:
    writer = csv.writer(f)
    writer.writerows(data)

# Read CSV
with open('data.csv', 'r') as f:
    reader = csv.reader(f)
    for row in reader:
        print(row)

# CSV with dictionaries
with open('data.csv', 'w', newline='') as f:
    fieldnames = ['name', 'age', 'city']
    writer = csv.DictWriter(f, fieldnames=fieldnames)
    writer.writeheader()
    writer.writerow({'name': 'Alice', 'age': 25, 'city': 'Tokyo'})

# ═══════════════════════════════════════════
# Binary Files
# ═══════════════════════════════════════════

# Write binary
data = b'\x00\x01\x02\x03'
with open('binary.dat', 'wb') as f:
    f.write(data)

# Read binary
with open('binary.dat', 'rb') as f:
    data = f.read()

# ═══════════════════════════════════════════
# Temporary Files
# ═══════════════════════════════════════════

import tempfile

# Temporary file
with tempfile.NamedTemporaryFile(mode='w', delete=False) as f:
    f.write('Temporary content')
    temp_path = f.name

# Temporary directory
with tempfile.TemporaryDirectory() as tmpdir:
    print(f'Created temporary directory: {tmpdir}')
    # Directory is automatically deleted
```

---

<div align="center">

## ⚠️ Error Handling

</div>

### Exceptions & Error Handling 🛡️

```python
# ═══════════════════════════════════════════
# Try/Except/Finally
# ═══════════════════════════════════════════

# Basic exception handling
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero!")

# Multiple exceptions
try:
    value = int("not a number")
except (ValueError, TypeError) as e:
    print(f"Error: {e}")

# Catch all exceptions (not recommended)
try:
    # risky code
    pass
except Exception as e:
    print(f"An error occurred: {e}")

# Else clause (runs if no exception)
try:
    result = 10 / 2
except ZeroDivisionError:
    print("Error")
else:
    print(f"Result: {result}")

# Finally clause (always runs)
try:
    file = open('file.txt', 'r')
    content = file.read()
except FileNotFoundError:
    print("File not found")
finally:
    if 'file' in locals():
        file.close()

# ═══════════════════════════════════════════
# Raising Exceptions
# ═══════════════════════════════════════════

def divide(a, b):
    if b == 0:
        raise ValueError("Cannot divide by zero")
    return a / b

# Re-raise exception
try:
    result = divide(10, 0)
except ValueError:
    print("Handling error")
    raise  # Re-raise the same exception

# ═══════════════════════════════════════════
# Custom Exceptions
# ═══════════════════════════════════════════

class InvalidAgeError(Exception):
    """Custom exception for invalid age."""
    pass

class User:
    def __init__(self, name, age):
        if age < 0:
            raise InvalidAgeError(f"Age cannot be negative: {age}")
        self.name = name
        self.age = age

try:
    user = User("MrDib", -5)
except InvalidAgeError as e:
    print(e)

# ═══════════════════════════════════════════
# Common Built-in Exceptions
# ═══════════════════════════════════════════

'''
ValueError      - Invalid value
TypeError       - Invalid type
KeyError        - Invalid dictionary key
IndexError      - Invalid sequence index
AttributeError  - Invalid attribute access
FileNotFoundError - File doesn't exist
IOError         - I/O operation failed
ImportError     - Import failed
ZeroDivisionError - Division by zero
RuntimeError    - Generic runtime error
'''

# ═══════════════════════════════════════════
# Context Managers for Resource Management
# ═══════════════════════════════════════════

# Automatic cleanup
with open('file.txt', 'r') as f:
    content = f.read()
# File automatically closed

# Multiple context managers
with open('input.txt', 'r') as infile, \
     open('output.txt', 'w') as outfile:
    content = infile.read()
    outfile.write(content)

# ═══════════════════════════════════════════
# Assertions
# ═══════════════════════════════════════════

def calculate_average(numbers):
    assert len(numbers) > 0, "List cannot be empty"
    return sum(numbers) / len(numbers)

# Assertions can be disabled with -O flag
# python -O script.py
```

---

<div align="center">

## 📦 Virtual Environments

</div>

### Environment Management 🔒

```bash
# ═══════════════════════════════════════════
# venv (Built-in, Python 3.3+)
# ═══════════════════════════════════════════

# Create virtual environment
python3 -m venv myenv

# Activate (macOS/Linux)
source myenv/bin/activate

# Activate (Windows)
myenv\Scripts\activate

# Deactivate
deactivate

# Delete environment
rm -rf myenv

# ═══════════════════════════════════════════
# pip - Package Management
# ═══════════════════════════════════════════

# Install package
pip install requests

# Install specific version
pip install requests==2.28.0

# Install minimum version
pip install 'requests>=2.28.0'

# Upgrade package
pip install --upgrade requests

# Uninstall
pip uninstall requests

# List installed packages
pip list

# List outdated packages
pip list --outdated

# Show package info
pip show requests

# ═══════════════════════════════════════════
# Requirements Files
# ═══════════════════════════════════════════

# Generate requirements
pip freeze > requirements.txt

# Install from requirements
pip install -r requirements.txt

# Upgrade all packages
pip list --outdated --format=freeze | cut -d = -f 1 | xargs -n1 pip install -U

# ═══════════════════════════════════════════
# pipenv (Advanced Dependency Management)
# ═══════════════════════════════════════════

# Install pipenv
pip install pipenv

# Create environment and install packages
pipenv install requests

# Install dev dependencies
pipenv install --dev pytest

# Activate shell
pipenv shell

# Run command in venv
pipenv run python script.py

# Generate requirements
pipenv lock -r > requirements.txt

# ═══════════════════════════════════════════
# Poetry (Modern Dependency Management)
# ═══════════════════════════════════════════

# Install poetry
curl -sSL https://install.python-poetry.org | python3 -

# Create new project
poetry new myproject

# Install dependencies
poetry install

# Add package
poetry add requests

# Add dev dependency
poetry add --dev pytest

# Update packages
poetry update

# Run command
poetry run python script.py

# ═══════════════════════════════════════════
# conda (Data Science Focused)
# ═══════════════════════════════════════════

# Create environment
conda create -n myenv python=3.9

# Activate
conda activate myenv

# Deactivate
conda deactivate

# Install package
conda install numpy

# List environments
conda env list

# Export environment
conda env export > environment.yml

# Create from file
conda env create -f environment.yml
```

---

<div align="center">

## 🌐 Web Development

</div>

### Flask - Lightweight Web Framework 🌶️

```python
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

# pip install flask

# ═══════════════════════════════════════════
# Basic Flask App
# ═══════════════════════════════════════════

from flask import Flask, request, jsonify, render_template

app = Flask(__name__)

@app.route('/')
def home():
    return 'Hello, Flask!'

@app.route('/user/<name>')
def user(name):
    return f'Hello, {name}!'

# HTTP methods
@app.route('/api/data', methods=['GET', 'POST'])
def data():
    if request.method == 'POST':
        data = request.json
        return jsonify({"received": data}), 201
    return jsonify({"message": "GET request"})

# Query parameters
@app.route('/search')
def search():
    query = request.args.get('q', '')
    return f'Searching for: {query}'

# Templates
@app.route('/profile/<username>')
def profile(username):
    return render_template('profile.html', username=username)

if __name__ == '__main__':
    app.run(debug=True)

# ═══════════════════════════════════════════
# Flask with Database
# ═══════════════════════════════════════════

from flask_sqlalchemy import SQLAlchemy

app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///database.db'
db = SQLAlchemy(app)

class User(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    username = db.Column(db.String(80), unique=True, nullable=False)
    email = db.Column(db.String(120), unique=True, nullable=False)

    def to_dict(self):
        return {
            'id': self.id,
            'username': self.username,
            'email': self.email
        }

# Create tables
with app.app_context():
    db.create_all()

@app.route('/users', methods=['POST'])
def create_user():
    data = request.json
    user = User(username=data['username'], email=data['email'])
    db.session.add(user)
    db.session.commit()
    return jsonify(user.to_dict()), 201

@app.route('/users/<int:user_id>')
def get_user(user_id):
    user = User.query.get_or_404(user_id)
    return jsonify(user.to_dict())
```

---

### Django - Full-Featured Web Framework 🎯

```bash
# ═══════════════════════════════════════════
# Installation & Setup
# ═══════════════════════════════════════════

# Install Django
pip install django

# Create project
django-admin startproject myproject
cd myproject

# Create app
python manage.py startapp myapp

# Run development server
python manage.py runserver

# ═══════════════════════════════════════════
# Database Migrations
# ═══════════════════════════════════════════

# Create migrations
python manage.py makemigrations

# Apply migrations
python manage.py migrate

# Create superuser
python manage.py createsuperuser

# ═══════════════════════════════════════════
# Django Shell
# ═══════════════════════════════════════════

python manage.py shell
```

```python
# ═══════════════════════════════════════════
# Django Models (myapp/models.py)
# ═══════════════════════════════════════════

from django.db import models
from django.contrib.auth.models import User

class Post(models.Model):
    title = models.CharField(max_length=200)
    content = models.TextField()
    author = models.ForeignKey(User, on_delete=models.CASCADE)
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)

    class Meta:
        ordering = ['-created_at']

    def __str__(self):
        return self.title

# ═══════════════════════════════════════════
# Django Views (myapp/views.py)
# ═══════════════════════════════════════════

from django.shortcuts import render, get_object_or_404
from django.http import JsonResponse
from .models import Post

def post_list(request):
    posts = Post.objects.all()
    return render(request, 'post_list.html', {'posts': posts})

def post_detail(request, pk):
    post = get_object_or_404(Post, pk=pk)
    return render(request, 'post_detail.html', {'post': post})

# API View
from django.views.decorators.csrf import csrf_exempt
import json

@csrf_exempt
def api_posts(request):
    if request.method == 'GET':
        posts = Post.objects.all()
        data = [{'id': p.id, 'title': p.title} for p in posts]
        return JsonResponse(data, safe=False)

    elif request.method == 'POST':
        data = json.loads(request.body)
        post = Post.objects.create(**data)
        return JsonResponse({'id': post.id, 'title': post.title})

# ═══════════════════════════════════════════
# Django URLs (myapp/urls.py)
# ═══════════════════════════════════════════

from django.urls import path
from . import views

urlpatterns = [
    path('', views.post_list, name='post_list'),
    path('post/<int:pk>/', views.post_detail, name='post_detail'),
    path('api/posts/', views.api_posts, name='api_posts'),
]
```

---

### FastAPI - Modern API Framework ⚡

```python
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

# pip install fastapi uvicorn[standard]

# ═══════════════════════════════════════════
# Basic FastAPI App
# ═══════════════════════════════════════════

from fastapi import FastAPI, HTTPException
from pydantic import BaseModel
from typing import List, Optional

app = FastAPI()

# Pydantic models for request/response
class User(BaseModel):
    id: Optional[int] = None
    name: str
    email: str
    age: int

# In-memory database
users_db = []

@app.get("/")
def read_root():
    return {"message": "Welcome to FastAPI"}

@app.get("/users", response_model=List[User])
def get_users():
    return users_db

@app.get("/users/{user_id}", response_model=User)
def get_user(user_id: int):
    user = next((u for u in users_db if u.id == user_id), None)
    if not user:
        raise HTTPException(status_code=404, detail="User not found")
    return user

@app.post("/users", response_model=User, status_code=201)
def create_user(user: User):
    user.id = len(users_db) + 1
    users_db.append(user)
    return user

@app.put("/users/{user_id}", response_model=User)
def update_user(user_id: int, user: User):
    index = next((i for i, u in enumerate(users_db) if u.id == user_id), None)
    if index is None:
        raise HTTPException(status_code=404, detail="User not found")
    user.id = user_id
    users_db[index] = user
    return user

@app.delete("/users/{user_id}")
def delete_user(user_id: int):
    global users_db
    users_db = [u for u in users_db if u.id != user_id]
    return {"message": "User deleted"}

# Query parameters
@app.get("/search")
def search(q: str, limit: int = 10):
    return {"query": q, "limit": limit}

# Run with: uvicorn main:app --reload
# Docs at: http://localhost:8000/docs
```

---

<div align="center">

## 📊 Data Science

</div>

### NumPy - Numerical Computing 🔢

```python
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

# pip install numpy

import numpy as np

# ═══════════════════════════════════════════
# Creating Arrays
# ═══════════════════════════════════════════

# From list
arr = np.array([1, 2, 3, 4, 5])

# 2D array
matrix = np.array([[1, 2, 3], [4, 5, 6]])

# Special arrays
zeros = np.zeros((3, 4))        # 3x4 array of zeros
ones = np.ones((2, 3))          # 2x3 array of ones
empty = np.empty((2, 2))        # Uninitialized
identity = np.eye(3)            # 3x3 identity matrix

# Range
arange = np.arange(0, 10, 2)    # [0, 2, 4, 6, 8]
linspace = np.linspace(0, 1, 5) # 5 values from 0 to 1

# Random
random = np.random.random((3, 3))
randint = np.random.randint(0, 10, (3, 3))

# ═══════════════════════════════════════════
# Array Operations
# ═══════════════════════════════════════════

arr = np.array([1, 2, 3, 4, 5])

# Basic operations
arr + 10            # Add 10 to all elements
arr * 2             # Multiply all by 2
arr ** 2            # Square all elements
np.sqrt(arr)        # Square root

# Array operations
arr1 + arr2         # Element-wise addition
arr1 * arr2         # Element-wise multiplication
np.dot(arr1, arr2)  # Dot product

# Aggregations
arr.sum()           # Sum of all elements
arr.mean()          # Mean
arr.std()           # Standard deviation
arr.min()           # Minimum
arr.max()           # Maximum
arr.argmin()        # Index of minimum
arr.argmax()        # Index of maximum

# ═══════════════════════════════════════════
# Indexing & Slicing
# ═══════════════════════════════════════════

arr = np.array([1, 2, 3, 4, 5])
arr[0]              # First element
arr[-1]             # Last element
arr[1:4]            # Slice [2, 3, 4]

matrix = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
matrix[0, 0]        # Element at (0, 0)
matrix[0, :]        # First row
matrix[:, 0]        # First column

# Boolean indexing
arr[arr > 3]        # Elements greater than 3

# ═══════════════════════════════════════════
# Reshaping
# ═══════════════════════════════════════════

arr = np.arange(12)
arr.reshape(3, 4)   # 3x4 matrix
arr.reshape(2, 6)   # 2x6 matrix
arr.reshape(-1, 1)  # Column vector

matrix.flatten()    # 1D array
matrix.T            # Transpose
```

---

### Pandas - Data Analysis 🐼

```python
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

# pip install pandas

import pandas as pd

# ═══════════════════════════════════════════
# Creating DataFrames
# ═══════════════════════════════════════════

# From dictionary
data = {
    'name': ['Alice', 'Bob', 'Charlie'],
    'age': [25, 30, 35],
    'city': ['Tokyo', 'NYC', 'London']
}
df = pd.DataFrame(data)

# From CSV
df = pd.read_csv('data.csv')

# From Excel
df = pd.read_excel('data.xlsx')

# From JSON
df = pd.read_json('data.json')

# ═══════════════════════════════════════════
# Data Inspection
# ═══════════════════════════════════════════

df.head()           # First 5 rows
df.tail(10)         # Last 10 rows
df.info()           # DataFrame info
df.describe()       # Statistical summary
df.shape            # (rows, columns)
df.columns          # Column names
df.dtypes           # Data types

# ═══════════════════════════════════════════
# Selecting Data
# ═══════════════════════════════════════════

# Single column
df['name']
df.name

# Multiple columns
df[['name', 'age']]

# Rows by index
df.iloc[0]          # First row
df.iloc[0:5]        # First 5 rows
df.iloc[0, 0]       # Specific cell

# Rows by label
df.loc[0, 'name']

# Conditional selection
df[df['age'] > 25]
df[(df['age'] > 25) & (df['city'] == 'Tokyo')]

# ═══════════════════════════════════════════
# Data Manipulation
# ═══════════════════════════════════════════

# Add column
df['salary'] = [50000, 60000, 70000]

# Drop column
df.drop('salary', axis=1, inplace=True)

# Rename columns
df.rename(columns={'name': 'full_name'}, inplace=True)

# Sort
df.sort_values('age', ascending=False)
df.sort_values(['city', 'age'])

# Filter
filtered = df[df['age'] > 25]

# Grouping
df.groupby('city')['age'].mean()
df.groupby('city').agg({'age': ['mean', 'max', 'min']})

# ═══════════════════════════════════════════
# Missing Data
# ═══════════════════════════════════════════

# Check for missing
df.isnull()
df.isnull().sum()

# Drop missing
df.dropna()                 # Drop rows with any NaN
df.dropna(axis=1)           # Drop columns with any NaN

# Fill missing
df.fillna(0)                # Fill with 0
df.fillna(df.mean())        # Fill with mean

# ═══════════════════════════════════════════
# Data Aggregation
# ═══════════════════════════════════════════

df['age'].sum()
df['age'].mean()
df['age'].median()
df['age'].std()
df['age'].min()
df['age'].max()
df['age'].count()

# ═══════════════════════════════════════════
# Exporting Data
# ═══════════════════════════════════════════

df.to_csv('output.csv', index=False)
df.to_excel('output.xlsx', index=False)
df.to_json('output.json', orient='records')
```

---

### Matplotlib - Visualization 📊

```python
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

# pip install matplotlib

import matplotlib.pyplot as plt
import numpy as np

# ═══════════════════════════════════════════
# Line Plot
# ═══════════════════════════════════════════

x = np.linspace(0, 10, 100)
y = np.sin(x)

plt.figure(figsize=(10, 6))
plt.plot(x, y, label='sin(x)')
plt.plot(x, np.cos(x), label='cos(x)')
plt.title('Trigonometric Functions')
plt.xlabel('x')
plt.ylabel('y')
plt.legend()
plt.grid(True)
plt.savefig('plot.png', dpi=300, bbox_inches='tight')
plt.show()

# ═══════════════════════════════════════════
# Scatter Plot
# ═══════════════════════════════════════════

x = np.random.rand(50)
y = np.random.rand(50)
colors = np.random.rand(50)
sizes = 1000 * np.random.rand(50)

plt.scatter(x, y, c=colors, s=sizes, alpha=0.5, cmap='viridis')
plt.colorbar()
plt.show()

# ═══════════════════════════════════════════
# Bar Chart
# ═══════════════════════════════════════════

categories = ['A', 'B', 'C', 'D']
values = [23, 45, 56, 78]

plt.bar(categories, values)
plt.title('Bar Chart')
plt.xlabel('Category')
plt.ylabel('Value')
plt.show()

# ═══════════════════════════════════════════
# Histogram
# ═══════════════════════════════════════════

data = np.random.randn(1000)

plt.hist(data, bins=30, edgecolor='black', alpha=0.7)
plt.title('Histogram')
plt.xlabel('Value')
plt.ylabel('Frequency')
plt.show()

# ═══════════════════════════════════════════
# Subplots
# ═══════════════════════════════════════════

fig, axes = plt.subplots(2, 2, figsize=(12, 8))

# Top left
axes[0, 0].plot([1, 2, 3, 4], [1, 4, 2, 3])
axes[0, 0].set_title('Plot 1')

# Top right
axes[0, 1].scatter([1, 2, 3, 4], [1, 4, 2, 3])
axes[0, 1].set_title('Plot 2')

# Bottom left
axes[1, 0].bar([1, 2, 3, 4], [1, 4, 2, 3])
axes[1, 0].set_title('Plot 3')

# Bottom right
axes[1, 1].hist(np.random.randn(100), bins=20)
axes[1, 1].set_title('Plot 4')

plt.tight_layout()
plt.show()
```

---

<div align="center">

## 🧪 Testing

</div>

### Unit Testing 🔬

```python
# ═══════════════════════════════════════════
# unittest (Built-in)
# ═══════════════════════════════════════════

import unittest

# File: calculator.py
class Calculator:
    def add(self, a, b):
        return a + b

    def divide(self, a, b):
        if b == 0:
            raise ValueError("Cannot divide by zero")
        return a / b

# File: test_calculator.py
class TestCalculator(unittest.TestCase):
    def setUp(self):
        """Run before each test"""
        self.calc = Calculator()

    def tearDown(self):
        """Run after each test"""
        pass

    def test_add(self):
        result = self.calc.add(2, 3)
        self.assertEqual(result, 5)

    def test_divide(self):
        result = self.calc.divide(10, 2)
        self.assertEqual(result, 5)

    def test_divide_by_zero(self):
        with self.assertRaises(ValueError):
            self.calc.divide(10, 0)

if __name__ == '__main__':
    unittest.main()

# Run tests
# python -m unittest test_calculator.py
# python -m unittest discover  # Auto-discover tests

# ═══════════════════════════════════════════
# pytest (Popular Framework)
# ═══════════════════════════════════════════

# pip install pytest

# File: test_calculator_pytest.py
import pytest
from calculator import Calculator

@pytest.fixture
def calc():
    return Calculator()

def test_add(calc):
    assert calc.add(2, 3) == 5

def test_divide(calc):
    assert calc.divide(10, 2) == 5

def test_divide_by_zero(calc):
    with pytest.raises(ValueError):
        calc.divide(10, 0)

# Parametrized tests
@pytest.mark.parametrize("a,b,expected", [
    (2, 3, 5),
    (5, 5, 10),
    (-1, 1, 0),
])
def test_add_parametrized(calc, a, b, expected):
    assert calc.add(a, b) == expected

# Run tests
# pytest
# pytest -v  # Verbose
# pytest test_calculator_pytest.py  # Specific file
# pytest -k "add"  # Tests matching pattern

# ═══════════════════════════════════════════
# Test Coverage
# ═══════════════════════════════════════════

# pip install pytest-cov

# pytest --cov=calculator --cov-report=html
# Open htmlcov/index.html

# ═══════════════════════════════════════════
# Mocking
# ═══════════════════════════════════════════

from unittest.mock import Mock, patch

def test_with_mock():
    # Create mock object
    mock_api = Mock()
    mock_api.get_user.return_value = {"name": "MrDib", "age": 25}

    result = mock_api.get_user(123)
    assert result["name"] == "MrDib"

    # Verify method was called
    mock_api.get_user.assert_called_once_with(123)

# Patch external dependencies
@patch('module.external_api')
def test_with_patch(mock_api):
    mock_api.get_data.return_value = {"status": "success"}
    # Test code that uses external_api
```

---

<div align="center">

## 💡 Best Practices

</div>

### Python Best Practices ⭐

```python
# ═══════════════════════════════════════════
# PEP 8 - Style Guide
# ═══════════════════════════════════════════

# Naming conventions
variable_name = "lowercase_with_underscores"
CONSTANT_NAME = "UPPERCASE_WITH_UNDERSCORES"

def function_name():
    pass

class ClassName:
    pass

# Indentation: 4 spaces
# Line length: 79 characters (or 88 with Black)
# Imports at top of file

# ═══════════════════════════════════════════
# The Zen of Python
# ═══════════════════════════════════════════

import this

'''
Beautiful is better than ugly.
Explicit is better than implicit.
Simple is better than complex.
Complex is better than complicated.
...
'''

# ═══════════════════════════════════════════
# Common Idioms
# ═══════════════════════════════════════════

# ✅ DO: Use enumerate
for index, value in enumerate(my_list):
    print(f"{index}: {value}")

# ❌ DON'T:
for i in range(len(my_list)):
    print(f"{i}: {my_list[i]}")

# ✅ DO: Use zip
for name, age in zip(names, ages):
    print(f"{name} is {age}")

# ❌ DON'T:
for i in range(len(names)):
    print(f"{names[i]} is {ages[i]}")

# ✅ DO: Use with statement
with open('file.txt') as f:
    content = f.read()

# ❌ DON'T:
f = open('file.txt')
content = f.read()
f.close()

# ✅ DO: Use list comprehensions
squares = [x**2 for x in range(10)]

# ❌ DON'T:
squares = []
for x in range(10):
    squares.append(x**2)

# ═══════════════════════════════════════════
# Avoid Common Pitfalls
# ═══════════════════════════════════════════

# ❌ Mutable default arguments
def bad_function(items=[]):  # DON'T DO THIS
    items.append(1)
    return items

# ✅ Correct way
def good_function(items=None):
    if items is None:
        items = []
    items.append(1)
    return items

# ❌ Modifying list while iterating
for item in my_list:
    if condition:
        my_list.remove(item)  # DON'T DO THIS

# ✅ Correct way
my_list = [item for item in my_list if not condition]

# ═══════════════════════════════════════════
# Performance Tips
# ═══════════════════════════════════════════

# Use sets for membership testing
my_set = set(my_list)
if item in my_set:  # O(1) vs O(n) for list
    pass

# Use generators for large data
# Instead of:
data = [process(x) for x in range(1000000)]

# Do:
data = (process(x) for x in range(1000000))

# String concatenation
# Instead of:
result = ""
for s in strings:
    result += s  # Slow for many strings

# Do:
result = "".join(strings)

# ═══════════════════════════════════════════
# Type Hints
# ═══════════════════════════════════════════

from typing import List, Dict, Tuple, Optional

def process_data(
    items: List[str],
    mapping: Dict[str, int],
    flag: Optional[bool] = None
) -> Tuple[int, str]:
    """Process data and return results."""
    return len(items), "done"

# ═══════════════════════════════════════════
# Documentation
# ═══════════════════════════════════════════

def calculate_area(radius: float) -> float:
    """
    Calculate the area of a circle.

    Args:
        radius: The radius of the circle

    Returns:
        The area of the circle

    Raises:
        ValueError: If radius is negative

    Examples:
        >>> calculate_area(5)
        78.53981633974483
    """
    if radius < 0:
        raise ValueError("Radius cannot be negative")
    return 3.14159 * radius ** 2
```

---

### Project Structure 📁

```bash
# ═══════════════════════════════════════════
# Recommended Project Structure
# ═══════════════════════════════════════════

myproject/
├── .github/
│   └── workflows/          # GitHub Actions
├── docs/                   # Documentation
├── src/
│   └── myproject/
│       ├── __init__.py
│       ├── main.py
│       ├── models.py
│       ├── utils.py
│       └── tests/
│           ├── __init__.py
│           ├── test_main.py
│           └── test_utils.py
├── .gitignore
├── .env.example            # Environment variables template
├── README.md
├── requirements.txt        # Production dependencies
├── requirements-dev.txt    # Development dependencies
├── setup.py               # Package setup
├── pyproject.toml         # Modern Python project config
└── LICENSE

# ═══════════════════════════════════════════
# .gitignore (Python)
# ═══════════════════════════════════════════

# Byte-compiled / optimized
__pycache__/
*.py[cod]
*$py.class

# Virtual environment
venv/
env/
ENV/

# IDEs
.vscode/
.idea/
*.swp

# Distribution
dist/
build/
*.egg-info/

# Environment
.env
.env.local

# Testing
.pytest_cache/
.coverage
htmlcov/

# OS
.DS_Store
Thumbs.db

# ═══════════════════════════════════════════
# requirements.txt
# ═══════════════════════════════════════════

requests==2.28.0
flask==2.3.0
python-dotenv==1.0.0

# ═══════════════════════════════════════════
# pyproject.toml (Modern Config)
# ═══════════════════════════════════════════

[build-system]
requires = ["setuptools>=45", "wheel"]
build-backend = "setuptools.build_meta"

[project]
name = "myproject"
version = "0.1.0"
description = "A sample Python project"
authors = [{name = "MrDib"}]
dependencies = [
    "requests>=2.28.0",
]

[project.optional-dependencies]
dev = [
    "pytest>=7.0",
    "black>=23.0",
    "flake8>=6.0",
]
```

---

<div align="center">

**Built with 🐍 by MrDib, for Pythonistas**

_Remember: "There should be one-- and preferably only one --obvious way to do it."_ ✨

**Happy Coding!** 🚀

</div>
