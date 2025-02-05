# Python Programming Guide - Part 4: Advanced Concepts

## Table of Contents

### Part 4: Advanced Concepts
- [1. Object-Oriented Programming](#1-object-oriented-programming)
  - [1.1. Classes and Objects](#11-classes-and-objects)
  - [1.2. Inheritance](#12-inheritance)
  - [1.3. Encapsulation](#13-encapsulation)
  - [1.4. Polymorphism](#14-polymorphism)
  - [1.5. Class Methods and Properties](#15-class-methods-and-properties)
- [2. Exception Handling](#2-exception-handling)
  - [2.1. Try-Except Basics](#21-try-except-basics)
  - [2.2. Exception Types](#22-exception-types)
  - [2.3. Custom Exceptions](#23-custom-exceptions)
  - [2.4. Context Managers](#24-context-managers)
- [3. Regular Expressions](#3-regular-expressions)
  - [3.1. Basic Patterns](#31-basic-patterns)
  - [3.2. Pattern Syntax](#32-pattern-syntax)
  - [3.3. RegEx Functions](#33-regex-functions)
  - [3.4. Common Use Cases](#34-common-use-cases)
- [4. Modules and Packages](#4-modules-and-packages)
  - [4.1. Module Basics](#41-module-basics)
  - [4.2. Package Structure](#42-package-structure)
  - [4.3. Package Usage](#43-package-usage)
  - [4.4. Standard Library](#44-standard-library)
- [5. Magic Methods](#5-magic-methods)
  - [5.1. Basic Magic Methods](#51-basic-magic-methods)
  - [5.2. Comparison Methods](#52-comparison-methods)
  - [5.3. Arithmetic Methods](#53-arithmetic-methods)
  - [5.4. Container Methods](#54-container-methods)

## 1. Object-Oriented Programming

### 1.1. Classes and Objects
```python
class Person:
    # Class variable
    species = "Homo Sapiens"
    
    # Constructor
    def __init__(self, name, age):
        # Instance variables
        self.name = name
        self.age = age
    
    # Instance method
    def introduce(self):
        return f"Hi, I'm {self.name}"
    
    # Class method
    @classmethod
    def create_anonymous(cls):
        return cls("Anonymous", 0)

# Creating objects
person1 = Person("Alice", 25)
person2 = Person("Bob", 30)
```

### 1.2. Inheritance
```python
class Employee(Person):
    def __init__(self, name, age, employee_id):
        # Call parent constructor
        super().__init__(name, age)
        self.employee_id = employee_id
    
    # Override method
    def introduce(self):
        return f"Hi, I'm {self.name}, employee {self.employee_id}"

# Multiple inheritance
class Student:
    def study(self):
        return "Studying..."

class WorkingStudent(Employee, Student):
    pass
```

### 1.3. Encapsulation
```python
class BankAccount:
    def __init__(self):
        self.__balance = 0  # Private variable
        self._type = "Savings"  # Protected variable
    
    # Getter method
    @property
    def balance(self):
        return self.__balance
    
    # Setter method
    @balance.setter
    def balance(self, amount):
        if amount >= 0:
            self.__balance = amount
        else:
            raise ValueError("Balance cannot be negative")
```

### 1.4. Polymorphism
```python
class Animal:
    def speak(self):
        pass

class Cat(Animal):
    def speak(self):
        return "Meow!"

class Dog(Animal):
    def speak(self):
        return "Woof!"

# Polymorphic function
def animal_sound(animal):
    return animal.speak()

# Using polymorphism
cat = Cat()
dog = Dog()
print(animal_sound(cat))  # Meow!
print(animal_sound(dog))  # Woof!
```

### 1.5. Class Methods and Properties
```python
class Temperature:
    def __init__(self, celsius):
        self._celsius = celsius
    
    @property
    def fahrenheit(self):
        return (self._celsius * 9/5) + 32
    
    @classmethod
    def from_fahrenheit(cls, fahrenheit):
        celsius = (fahrenheit - 32) * 5/9
        return cls(celsius)
    
    @staticmethod
    def is_valid_temperature(temp):
        return temp >= -273.15
```

## 2. Exception Handling

### 2.1. Try-Except Basics
```python
# Basic try-except
try:
    x = int("not a number")
except ValueError:
    print("That's not a valid number!")

# Multiple exceptions
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero!")
except Exception as e:
    print(f"Other error occurred: {e}")

# Try-except-else-finally
try:
    number = int(input("Enter a number: "))
except ValueError:
    print("Invalid input")
else:
    print(f"You entered {number}")
finally:
    print("Execution completed")
```

### 2.2. Exception Types
```python
# Common exception types
exceptions = {
    ValueError: "Invalid value",
    TypeError: "Invalid type",
    IndexError: "Invalid index",
    KeyError: "Invalid key",
    FileNotFoundError: "File not found",
    IOError: "Input/Output error",
    ZeroDivisionError: "Division by zero",
    AttributeError: "Invalid attribute"
}

# Handling multiple exceptions
try:
    # Some risky code
    pass
except (TypeError, ValueError) as e:
    print(f"Handling multiple exceptions: {e}")
```

### 2.3. Custom Exceptions
```python
# Custom exception class
class CustomError(Exception):
    def __init__(self, message):
        self.message = message
        super().__init__(self.message)

# Using custom exception
def validate_age(age):
    if age < 0:
        raise CustomError("Age cannot be negative")
    if age > 150:
        raise CustomError("Age is too high")
    return age

# Handling custom exception
try:
    validate_age(-5)
except CustomError as e:
    print(f"Custom error: {e}")
```

### 2.4. Context Managers
```python
# Using with statement
with open("file.txt") as f:
    content = f.read()

# Custom context manager
class DatabaseConnection:
    def __enter__(self):
        print("Opening database connection")
        return self
    
    def __exit__(self, exc_type, exc_val, exc_tb):
        print("Closing database connection")
        return False

# Using context manager decorator
from contextlib import contextmanager

@contextmanager
def timer():
    import time
    start = time.time()
    yield
    end = time.time()
    print(f"Elapsed time: {end - start}")
```

## 3. Regular Expressions

### 3.1. Basic Patterns
```python
import re

# Simple pattern matching
text = "Hello, World!"
pattern = r"Hello"
match = re.search(pattern, text)

# Match object methods
if match:
    print(match.group())  # Matched text
    print(match.start())  # Start position
    print(match.end())    # End position
    print(match.span())   # Start and end positions
```

### 3.2. Pattern Syntax
```python
# Common patterns
patterns = {
    r"\d": "Any digit",
    r"\w": "Any word character",
    r"\s": "Any whitespace",
    r".": "Any character except newline",
    r"^": "Start of string",
    r"$": "End of string",
    r"\b": "Word boundary"
}

# Quantifiers
quantifiers = {
    r"*": "0 or more",
    r"+": "1 or more",
    r"?": "0 or 1",
    r"{n}": "Exactly n",
    r"{n,}": "n or more",
    r"{n,m}": "Between n and m"
}
```

### 3.3. RegEx Functions
```python
# Different regex functions
text = "Python programming is fun"

re.search(r"fun", text)    # Search anywhere
re.match(r"Python", text)  # Match at beginning
re.findall(r"\w+", text)   # Find all matches
re.split(r"\s+", text)     # Split string
re.sub(r"fun", "great", text)  # Substitute

# Compile pattern for reuse
pattern = re.compile(r"\d+")
pattern.findall("123 456 789")
```

### 3.4. Common Use Cases
```python
# Email validation
email_pattern = r"^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$"

# Phone number format
phone_pattern = r"\d{3}[-.]?\d{3}[-.]?\d{4}"

# URL matching
url_pattern = r"https?://(?:[\w-]+\.)+[\w-]+(?:/[\w-./?%&=]*)?"

# Password validation
password_pattern = r"^(?=.*[A-Za-z])(?=.*\d)[A-Za-z\d]{8,}$"
```

## 4. Modules and Packages

### 4.1. Module Basics
```python
# Creating a module (math_operations.py)
def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

# Importing module
import math_operations
result = math_operations.add(5, 3)

# Import specific functions
from math_operations import add, subtract

# Import with alias
import math_operations as math
```

### 4.2. Package Structure
```python
mypackage/
    __init__.py
    module1.py
    module2.py
    subpackage/
        __init__.py
        module3.py

# __init__.py content
from .module1 import func1
from .module2 import func2
```

### 4.3. Package Usage
```python
# Different import styles
import mypackage
from mypackage import module1
from mypackage.subpackage import module3
from mypackage import func1, func2

# Relative imports (inside package)
from . import module1
from .. import module2
from .subpackage import module3
```

### 4.4. Standard Library
```python
# Common standard modules
import os           # Operating system interface
import sys          # System-specific parameters
import datetime     # Date and time functions
import json         # JSON encoder and decoder
import random       # Random number generation
import math         # Mathematical functions
import collections  # Container datatypes
import itertools    # Iterator functions
```

## 5. Magic Methods

### 5.1. Basic Magic Methods
```python
class Number:
    def __init__(self, value):
        self.value = value
    
    def __str__(self):
        return str(self.value)
    
    def __repr__(self):
        return f"Number({self.value})"
    
    def __bool__(self):
        return bool(self.value)
    
    def __len__(self):
        return len(str(self.value))
```

### 5.2. Comparison Methods
```python
class Temperature:
    def __init__(self, celsius):
        self.celsius = celsius
    
    def __eq__(self, other):
        return self.celsius == other.celsius
    
    def __lt__(self, other):
        return self.celsius < other.celsius
    
    def __le__(self, other):
        return self.celsius <= other.celsius
    
    def __gt__(self, other):
        return self.celsius > other.celsius
```

### 5.3. Arithmetic Methods
```python
class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    
    def __add__(self, other):
        return Vector(self.x + other.x, self.y + other.y)
    
    def __sub__(self, other):
        return Vector(self.x - other.x, self.y - other.y)
    
    def __mul__(self, scalar):
        return Vector(self.x * scalar, self.y * scalar)
    
    def __truediv__(self, scalar):
        return Vector(self.x / scalar, self.y / scalar)
```

### 5.4. Container Methods
```python
class Deck:
    def __init__(self):
        self.cards = []
    
    def __len__(self):
        return len(self.cards)
    
    def __getitem__(self, position):
        return self.cards[position]
    
    def __setitem__(self, position, value):
        self.cards[position] = value
    
    def __delitem__(self, position):
        del self.cards[position]
    
    def __iter__(self):
        return iter(self.cards)
    
    def __contains__(self, card):
        return card in self.cards
