# Python Programming Guide - Part 1: Language Fundamentals

## Table of Contents

### Part 1: Language Fundamentals
- [1. Variables](#1-variables)
- [2. Print Function](#2-print-function)
- [3. Input from User](#3-input-from-user)
- [4. Data Types](#4-data-types)
  - [4.1. Numbers](#41-numbers)
  - [4.2. Strings](#42-strings)
  - [4.3. Lists](#43-lists)
  - [4.4. Dictionaries](#44-dictionaries)
  - [4.5. Tuples](#45-tuples)
  - [4.6. Sets](#46-sets)
  - [4.7. Other Types](#47-other-types)
- [5. Operators](#5-operators)
  - [5.1. Arithmetic Operators](#51-arithmetic-operators)
  - [5.2. Relational Operators](#52-relational-operators)
  - [5.3. Bitwise Operators](#53-bitwise-operators)
  - [5.4. Logical Operators](#54-logical-operators)
- [6. Type Conversion](#6-type-conversion)

## 1. Variables

Variables are containers for storing data values.

```python
name = "John"              # String variable
age = 25                   # Integer variable
height = 5.9              # Float variable
is_student = True         # Boolean variable
```

**Naming Conventions:**
- Must start with a letter or underscore
- Can contain letters, numbers, and underscores
- Case-sensitive
- Cannot use Python keywords

## 2. Print Function

The print() function is used to output text or variables.

```python
print("Hello, World!")                     # Simple string
print("Name:", name)                       # Print with variable
print(f"Age: {age}")                       # F-string (Python 3.6+)
print("Height: %.2f meters" % height)      # Old-style formatting
print("Hi {}, you are {} years old".format(name, age))  # String format
```

## 3. Input from User

The input() function allows user interaction.

```python
name = input("Enter your name: ")          # Returns string
age = int(input("Enter your age: "))       # Convert to integer
height = float(input("Enter height: "))    # Convert to float
```

## 4. Data Types

### 4.1. Numbers
```python
x = 5                  # Integer
y = 3.14              # Float
z = 2 + 3j            # Complex number
```

### 4.2. Strings
```python
text = "Hello World"
# String operations
print(text.upper())                # HELLO WORLD
print(text.lower())                # hello world
print(text[0])                     # H (first character)
print(text[-1])                    # d (last character)
print(text[0:5])                   # Hello (slicing)
print(len(text))                   # 11 (length)
```

### 4.3. Lists
```python
fruits = ["apple", "banana", "orange"]
# List operations
fruits.append("grape")             # Add item
fruits.remove("banana")            # Remove item
fruits.sort()                      # Sort list
print(fruits[0])                   # Access item
print(len(fruits))                # List length
```

### 4.4. Dictionaries
```python
person = {
    "name": "John",
    "age": 25,
    "city": "New York"
}
# Dictionary operations
print(person["name"])              # Access value
person["email"] = "john@email.com" # Add key-value
del person["age"]                  # Remove key-value
print(person.keys())               # Get all keys
print(person.values())             # Get all values
```

### 4.5. Tuples
```python
coordinates = (10, 20)             # Immutable
# Tuple operations
print(coordinates[0])              # Access item
print(len(coordinates))            # Tuple length
x, y = coordinates                 # Tuple unpacking
```

### 4.6. Sets
```python
numbers = {1, 2, 3, 4, 5}
# Set operations
numbers.add(6)                     # Add item
numbers.remove(2)                  # Remove item
print(1 in numbers)                # Check membership
```

### 4.7. Other Types
```python
# None type
empty = None

# Boolean type
is_valid = True
is_active = False
```

## 5. Operators

### 5.1. Arithmetic Operators
```python
x = 10
y = 3

print(x + y)    # 13 (Addition)
print(x - y)    # 7 (Subtraction)
print(x * y)    # 30 (Multiplication)
print(x / y)    # 3.333... (Division)
print(x // y)   # 3 (Floor division)
print(x % y)    # 1 (Modulus)
print(x ** y)   # 1000 (Exponentiation)
```

### 5.2. Relational Operators
```python
print(x > y)    # True (Greater than)
print(x < y)    # False (Less than)
print(x >= y)   # True (Greater than or equal to)
print(x <= y)   # False (Less than or equal to)
print(x == y)   # False (Equal to)
print(x != y)   # True (Not equal to)
```

### 5.3. Bitwise Operators
```python
print(x & y)    # AND
print(x | y)    # OR
print(x ^ y)    # XOR
print(~x)       # NOT
print(x << 2)   # Left shift
print(x >> 2)   # Right shift
```

### 5.4. Logical Operators
```python
a = True
b = False

print(a and b)  # False (Logical AND)
print(a or b)   # True (Logical OR)
print(not a)    # False (Logical NOT)
```

## 6. Type Conversion

```python
# String to Number
x = int("10")           # String to Integer
y = float("3.14")       # String to Float

# Number to String
text = str(10)          # Number to String

# List/Tuple/Set Conversion
my_list = [1, 2, 3]
my_tuple = tuple(my_list)    # List to Tuple
my_set = set(my_list)        # List to Set

# Dictionary Conversion
keys = ["a", "b", "c"]
values = [1, 2, 3]
my_dict = dict(zip(keys, values))  # Lists to Dictionary
