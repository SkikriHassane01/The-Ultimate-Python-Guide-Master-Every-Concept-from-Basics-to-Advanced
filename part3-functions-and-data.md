# Python Programming Guide - Part 3: Functions and Advanced Data Types

## Table of Contents

### Part 3: Functions and Advanced Data Types
- [1. Functions](#1-functions)
  - [1.1. Function Basics](#11-function-basics)
  - [1.2. Function Arguments](#12-function-arguments)
  - [1.3. Lambda Functions](#13-lambda-functions)
  - [1.4. Generators](#14-generators)
  - [1.5. Decorators](#15-decorators)
- [2. Sets](#2-sets)
  - [2.1. Set Operations](#21-set-operations)
  - [2.2. Set Methods](#22-set-methods)
  - [2.3. Mathematical Set Operations](#23-mathematical-set-operations)
- [3. Tuples](#3-tuples)
  - [3.1. Tuple Basics](#31-tuple-basics)
  - [3.2. Tuple Operations](#32-tuple-operations)
  - [3.3. Tuple Applications](#33-tuple-applications)
- [4. File Handling](#4-file-handling)
  - [4.1. File Operations](#41-file-operations)
  - [4.2. File Methods](#42-file-methods)
  - [4.3. Working with CSV Files](#43-working-with-csv-files)

## 1. Functions

### 1.1. Function Basics
```python
# Basic function definition
def greet(name):
    """
    Simple greeting function.
    Args:
        name (str): The name to greet
    Returns:
        str: The greeting message
    """
    return f"Hello, {name}!"

# Function with multiple parameters
def calculate_total(price, tax_rate=0.1):
    return price + (price * tax_rate)

# Function with return multiple values
def get_min_max(numbers):
    return min(numbers), max(numbers)
```

### 1.2. Function Arguments
```python
# Positional arguments
def display_info(name, age, city):
    print(f"{name} is {age} years old from {city}")

# Keyword arguments
def create_profile(name, age, city="Unknown"):
    return {"name": name, "age": age, "city": city}

# Variable-length arguments
def sum_all(*args):
    return sum(args)

# Keyword variable-length arguments
def print_kwargs(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")

# Using the functions
display_info("John", 25, "New York")
create_profile(name="Alice", age=30)
sum_all(1, 2, 3, 4, 5)
print_kwargs(name="Bob", age=35, city="London")
```

### 1.3. Lambda Functions
```python
# Simple lambda
square = lambda x: x**2

# Lambda with multiple arguments
multiply = lambda x, y: x * y

# Lambda in sorted function
points = [(1, 2), (3, 1), (2, 4)]
sorted_points = sorted(points, key=lambda p: p[1])

# Lambda with map and filter
numbers = [1, 2, 3, 4, 5]
squares = list(map(lambda x: x**2, numbers))
evens = list(filter(lambda x: x % 2 == 0, numbers))
```

### 1.4. Generators
```python
# Simple generator function
def count_up_to(n):
    i = 1
    while i <= n:
        yield i
        i += 1

# Generator expression
squares_gen = (x**2 for x in range(5))

# Using generators
for num in count_up_to(5):
    print(num)

# Generator with infinite sequence
def fibonacci():
    a, b = 0, 1
    while True:
        yield a
        a, b = b, a + b
```

### 1.5. Decorators
```python
# Simple decorator
def logged(func):
    def wrapper(*args, **kwargs):
        print(f"Calling {func.__name__}")
        result = func(*args, **kwargs)
        print(f"Finished {func.__name__}")
        return result
    return wrapper

# Decorator with parameters
def repeat(times):
    def decorator(func):
        def wrapper(*args, **kwargs):
            for _ in range(times):
                result = func(*args, **kwargs)
            return result
        return wrapper
    return decorator

# Using decorators
@logged
def add(x, y):
    return x + y

@repeat(3)
def greet(name):
    print(f"Hello {name}")
```

## 2. Sets

### 2.1. Set Operations
```python
# Creating sets
empty_set = set()
numbers = {1, 2, 3, 4, 5}
from_list = set([1, 2, 2, 3])  # Duplicates removed

# Basic operations
length = len(numbers)       # Number of elements
exists = 2 in numbers      # Membership test
for num in numbers:        # Iteration
    print(num)
```

### 2.2. Set Methods
```python
# Modifying sets
numbers.add(6)              # Add single element
numbers.update([7, 8, 9])   # Add multiple elements
numbers.remove(1)           # Remove (raises error if not found)
numbers.discard(10)         # Remove (no error if not found)
popped = numbers.pop()      # Remove and return arbitrary element
numbers.clear()             # Remove all elements
```

### 2.3. Mathematical Set Operations
```python
set1 = {1, 2, 3, 4}
set2 = {3, 4, 5, 6}

# Union
union1 = set1 | set2           # Using operator
union2 = set1.union(set2)      # Using method

# Intersection
intersect1 = set1 & set2           # Using operator
intersect2 = set1.intersection(set2)# Using method

# Difference
diff1 = set1 - set2               # Using operator
diff2 = set1.difference(set2)     # Using method

# Symmetric difference
sym_diff1 = set1 ^ set2          # Using operator
sym_diff2 = set1.symmetric_difference(set2)
```

## 3. Tuples

### 3.1. Tuple Basics
```python
# Creating tuples
empty_tuple = ()
single_item = (1,)           # Note the comma
coordinates = (3, 4)
mixed = (1, "hello", 3.14)
nested = ((1, 2), (3, 4))

# Accessing elements
x = coordinates[0]          # First element
y = coordinates[1]          # Second element
first, second = coordinates # Tuple unpacking
```

### 3.2. Tuple Operations
```python
# Basic operations
point = (1, 2)
point + (3, 4)         # Concatenation: (1, 2, 3, 4)
point * 2              # Repetition: (1, 2, 1, 2)
3 in point            # Membership test
len(point)            # Length

# Tuple methods
count = point.count(1)     # Count occurrences
index = point.index(2)     # Find position
```

### 3.3. Tuple Applications
```python
# Multiple assignment
x, y = 10, 20

# Returning multiple values from function
def get_coordinates():
    return (3, 4)

x, y = get_coordinates()

# As dictionary keys (immutable)
locations = {(0, 0): 'origin', (1, 1): 'point'}

# Named tuples
from collections import namedtuple
Point = namedtuple('Point', ['x', 'y'])
p = Point(3, 4)
print(p.x, p.y)
```

## 4. File Handling

### 4.1. File Operations
```python
# Opening files
file = open('example.txt', 'r')  # Read mode
file.close()

# Using with statement (recommended)
with open('example.txt', 'r') as file:
    content = file.read()

# Writing to files
with open('output.txt', 'w') as file:
    file.write('Hello World\n')
    file.writelines(['Line 1\n', 'Line 2\n'])

# Appending to files
with open('log.txt', 'a') as file:
    file.write('New log entry\n')
```

### 4.2. File Methods
```python
with open('example.txt', 'r') as file:
    # Reading methods
    content = file.read()        # Read entire file
    line = file.readline()       # Read one line
    lines = file.readlines()     # Read all lines into list
    
    # File position
    position = file.tell()       # Current position
    file.seek(0)                # Move to position
    
    # File properties
    name = file.name            # File name
    mode = file.mode           # Access mode
    closed = file.closed       # Check if closed
```

### 4.3. Working with CSV Files
```python
import csv

# Reading CSV
with open('data.csv', 'r') as file:
    reader = csv.reader(file)
    for row in reader:
        print(row)

# Writing CSV
with open('output.csv', 'w', newline='') as file:
    writer = csv.writer(file)
    writer.writerow(['Name', 'Age'])
    writer.writerow(['John', 30])

# Using DictReader and DictWriter
with open('data.csv', 'r') as file:
    reader = csv.DictReader(file)
    for row in reader:
        print(row['Name'], row['Age'])

with open('output.csv', 'w', newline='') as file:
    fieldnames = ['Name', 'Age']
    writer = csv.DictWriter(file, fieldnames=fieldnames)
    writer.writeheader()
    writer.writerow({'Name': 'John', 'Age': 30})
