# Python Programming Guide - Part 2: Control Flow and Data Structures

## Table of Contents

### Part 2: Control Flow and Data Structures
- [1. Control Statements](#1-control-statements)
  - [1.1. If-Else Statements](#11-if-else-statements)
  - [1.2. While Loops](#12-while-loops)
  - [1.3. For Loops](#13-for-loops)
- [2. Lists in Detail](#2-lists-in-detail)
  - [2.1. List Operations](#21-list-operations)
  - [2.2. List Methods](#22-list-methods)
  - [2.3. List Comprehensions](#23-list-comprehensions)
- [3. Dictionaries in Detail](#3-dictionaries-in-detail)
  - [3.1. Dictionary Operations](#31-dictionary-operations)
  - [3.2. Dictionary Methods](#32-dictionary-methods)
  - [3.3. Dictionary Comprehensions](#33-dictionary-comprehensions)
- [4. Strings in Detail](#4-strings-in-detail)
  - [4.1. String Operations](#41-string-operations)
  - [4.2. String Methods](#42-string-methods)
  - [4.3. String Formatting](#43-string-formatting)

## 1. Control Statements

### 1.1. If-Else Statements

#### Basic If Statement
```python
# Simple if statement
age = 18
if age >= 18:
    print("You are an adult")

# If-else statement
temperature = 25
if temperature > 30:
    print("It's hot!")
else:
    print("It's not too hot")

# If-elif-else statement
score = 75
if score >= 90:
    print("Grade: A")
elif score >= 80:
    print("Grade: B")
elif score >= 70:
    print("Grade: C")
else:
    print("Grade: D")

# Ternary operator
status = "Adult" if age >= 18 else "Minor"
```

### 1.2. While Loops

#### Basic While Loop
```python
# Simple counter
count = 0
while count < 5:
    print(count)
    count += 1

# While loop with break
counter = 0
while True:
    print(counter)
    counter += 1
    if counter >= 5:
        break

# While loop with continue
counter = 0
while counter < 5:
    counter += 1
    if counter % 2 == 0:
        continue
    print(counter)  # Only prints odd numbers

# While loop with else
count = 0
while count < 3:
    print(count)
    count += 1
else:
    print("Loop completed successfully")
```

### 1.3. For Loops

#### Basic For Loop
```python
# Looping through range
for i in range(5):
    print(i)

# Looping through list
fruits = ["apple", "banana", "orange"]
for fruit in fruits:
    print(fruit)

# Enumerate for index and value
for index, fruit in enumerate(fruits):
    print(f"{index}: {fruit}")

# Nested for loops
for i in range(2):
    for j in range(2):
        print(f"({i}, {j})")

# For loop with break and continue
for i in range(5):
    if i == 2:
        continue  # Skip 2
    if i == 4:
        break    # Stop at 4
    print(i)
```

## 2. Lists in Detail

### 2.1. List Operations
```python
# Creating and accessing lists
numbers = [1, 2, 3, 4, 5]
first = numbers[0]      # First element
last = numbers[-1]      # Last element
subset = numbers[1:4]   # Slicing [2, 3, 4]

# Basic operations
combined = numbers + [6, 7]  # Concatenation
doubled = numbers * 2        # Repetition
length = len(numbers)       # Length
exists = 3 in numbers      # Membership test

# Modifying lists
numbers[0] = 10            # Change element
numbers.extend([6, 7])     # Add multiple elements
numbers.insert(1, 15)      # Insert at position
```

### 2.2. List Methods
```python
numbers = [1, 2, 3, 4, 5]

# Adding elements
numbers.append(6)       # Add to end
numbers.insert(0, 0)   # Insert at position
numbers.extend([7, 8]) # Add multiple items

# Removing elements
numbers.remove(3)      # Remove first occurrence of 3
popped = numbers.pop() # Remove and return last item
numbers.clear()        # Remove all items

# Other methods
numbers.reverse()      # Reverse in place
numbers.sort()        # Sort in place
index = numbers.index(4)  # Find position
count = numbers.count(2)  # Count occurrences
```

### 2.3. List Comprehensions
```python
# Simple comprehension
squares = [x**2 for x in range(5)]
# [0, 1, 4, 9, 16]

# Comprehension with condition
evens = [x for x in range(10) if x % 2 == 0]
# [0, 2, 4, 6, 8]

# Nested comprehension
matrix = [[i+j for j in range(3)] for i in range(3)]
# [[0,1,2], [1,2,3], [2,3,4]]
```

## 3. Dictionaries in Detail

### 3.1. Dictionary Operations
```python
# Creating dictionaries
person = {
    "name": "John",
    "age": 30,
    "city": "New York"
}

# Accessing elements
name = person["name"]           # Using key
age = person.get("age")        # Using get method
city = person.get("address", "Unknown")  # With default

# Modifying dictionaries
person["email"] = "john@example.com"  # Add/update
del person["age"]                     # Remove key-value
person.update({"age": 31, "phone": "123"})  # Update multiple
```

### 3.2. Dictionary Methods
```python
# Common methods
keys = person.keys()           # Get all keys
values = person.values()       # Get all values
items = person.items()         # Get key-value pairs

# Advanced methods
person.pop("age")             # Remove and return value
last = person.popitem()       # Remove last item
person.clear()               # Remove all items

# Helpful methods
copy_dict = person.copy()    # Shallow copy
person.setdefault("age", 25) # Get or set default
```

### 3.3. Dictionary Comprehensions
```python
# Simple comprehension
squares = {x: x**2 for x in range(5)}
# {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}

# Conditional comprehension
evens = {x: x**2 for x in range(5) if x % 2 == 0}
# {0: 0, 2: 4, 4: 16}

# Dictionary from two lists
keys = ['a', 'b', 'c']
values = [1, 2, 3]
dict_comp = {k: v for k, v in zip(keys, values)}
# {'a': 1, 'b': 2, 'c': 3}
```

## 4. Strings in Detail

### 4.1. String Operations
```python
# String creation and access
text = "Hello World"
first = text[0]         # First character
last = text[-1]        # Last character
slice = text[1:5]      # Substring

# Basic operations
combined = "Hello" + " " + "World"  # Concatenation
repeated = "Hi" * 3                 # Repetition
length = len(text)                  # Length
exists = "o" in text               # Membership test
```

### 4.2. String Methods
```python
text = "  Hello, World!  "

# Case methods
upper = text.upper()           # Convert to uppercase
lower = text.lower()           # Convert to lowercase
title = text.title()           # Title case

# Cleaning methods
stripped = text.strip()        # Remove whitespace
replaced = text.replace('o', 'x')  # Replace characters
split_text = text.split(',')   # Split into list

# Search methods
found = text.find('World')     # Find substring
count = text.count('l')        # Count occurrences
starts = text.startswith('H')  # Check prefix
ends = text.endswith('!')      # Check suffix
```

### 4.3. String Formatting
```python
name = "John"
age = 25

# F-strings (Python 3.6+)
print(f"Name: {name}, Age: {age}")

# Format method
print("Name: {}, Age: {}".format(name, age))
print("Name: {n}, Age: {a}".format(n=name, a=age))

# % operator (old style)
print("Name: %s, Age: %d" % (name, age))

# Format specifications
pi = 3.14159
print(f"Pi: {pi:.2f}")  # Two decimal places
print(f"Age: {age:03d}")  # Zero-padded number
