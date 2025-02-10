# Python-Interview-Prep

# Introduction to Python Programming Language 
Python was invented by ___Guido van Rossum___, and it was named after the show ___Monty Python's Flying Circus___. Python is a high-level ___interpreted programming language___, meaning the source code is first compiled into intermediate bytecode, which is then executed by the Python Virtual Machine (PVM), implemented in CPython. This process makes Python flexible but comes at the cost of speed. In contrast, other compiled languages directly compile the source code into machine code for execution. Such languages typically run faster because their machine code executes directly on the hardware, eliminating the need for an intermediate virtual machine. Python is a ___dynamically typed language___, meaning the type of a variable is determined at runtime. Unlike statically typed languages, Python does not require you to explicitly specify the type of a variable when declaring it. An ___interpreter___ is a layer of software that translates your code into machine-readable instructions at runtime, allowing the computer to execute it.

__Advantages of Python:__
- Python is an easy-to-code, high-level programming language that emphasizes readability and simplicity.
- Python uses clear and readable syntax, making it more accessible.
- Python is portable and works on multiple platforms and operating systems such as Windows, macOS, and Linux without requiring modifications to the code.
- Python has extensive support libraries that assist with tasks like automation, web scraping, machine learning, data analysis, and more.
- Python supports graphical user interface (GUI) development through Tkinter, PyQt, and other libraries. It also has web frameworks such as Django and Flask for web development.

__Disadvantages of Python:__
- Python is slower than compiled languages like C or C++ because it is interpreted, which can affect performance for certain applications.
- Python's memory consumption is higher compared to languages like C, making it less suitable for memory-constrained environments.
- Python’s dynamic typing can lead to runtime errors that may be harder to debug, as type-related issues are only detected when the code is executed.

## Memory Allocation in Python
- In languages like C, the programmer must manually allocate and free memory using functions like `malloc` or `calloc`, and deallocate it using `free`, which can lead to errors if not done properly. In contrast, Python handles memory management automatically through garbage collection, which tracks references to objects and frees up memory when an object is no longer needed. This reduces the risk of memory leaks by automatically deallocating memory that is no longer in use.

## Garbage collection in Python
- Garbage collection in Python is the process of automatically identifying and freeing memory that is no longer in use, helping to manage memory more efficiently and prevent memory leaks.
- Python uses a ___reference counting mechanism___ as its primary method of garbage collection. Every object in Python has a reference count that tracks how many references are pointing to it. When the reference count of an object drops to zero (i.e., no references are pointing to it), the object is considered unreachable, and its memory can be deallocated.

## Types of memory in Python
__A) Stack Memory:__ 
- Stack memory is used to store local variables and function call information during the program's execution. It operates on a Last-In-First-Out (LIFO) basis, meaning the most recently called function is the first one to be completed and removed. When a function is called, a new stack frame is created to hold its local variables and return information. Once the function execution is complete, its stack frame is removed, and the memory is freed automatically. Stack memory is limited in size, making it ideal for small, short-lived data.
  
__B) Heap Memory:__ 
- Heap memory is used to store objects and dynamic data structures like lists, dictionaries, and instances of user-defined classes. This memory is managed by the Python memory manager, which allocates memory when an object is created. Python's garbage collector automatically deallocates heap memory when objects are no longer in use, i.e., when their reference count drops to zero.

__C) Global Memory:__ 
- Global memory is used to store global variables, which are variables that are accessible throughout the entire program. Global variables are stored in the `global namespace` and are typically managed by the global scope. These variables remain in memory as long as the program is running.

## PyObject Concept in Python 
- PyObject is a fundamental concept in Python's memory model. Every Python object, regardless of its type, is represented internally as a PyObject. This includes both built-in objects (like integers, strings, and dictionaries) and user-defined objects (like instances of custom classes).
- A PyObject consists of two main components: the ___reference count___, which tracks how many references are pointing to the object, and the ___type information___, which defines the object's data type (e.g., integer, string, list, etc.).
- In Python, when you assign the same value to multiple variables, like `var = 10` and `temp = 10`, both variables will have the same object identity or ID. This happens because Python reuses the same memory location for immutable objects, like small integers, so both var and temp will point to the same memory address. However, when you assign a new value to a variable, such as `var = 10` and then `var = 20`, Python creates a new object for 20, and as a result, var will point to a different memory address.
- In contrast, in languages like C or Java, assigning values to variables like `var = 10` and `temp = 10` would typically result in different memory allocations for each variable, even if the values are the same.

## Threading and Multiprocessing in Python
__A) Threading:__ 
- Threading in Python allows you to run multiple threads (smaller units of code) concurrently in the same program. Each thread runs in the same memory space, sharing the same data and resources, which makes it lightweight and efficient for certain tasks.
- Threads are often used to handle I/O-bound tasks, such as reading/writing files or interacting with databases. These tasks can run concurrently because they spend a lot of time waiting for external events (e.g., I/O operations), allowing other threads to run during that time. While the tasks may not run simultaneously (due to the Global Interpreter Lock or GIL), the CPU switches between them so quickly that it appears as if they are running in parallel.

__B) Multiprcessing:__
- Multiprocessing allows you to run multiple processes, each with its own memory space and Python interpreter, on different CPU cores. Unlike threads, processes run independently and do not share memory. This allows processes to execute truly in parallel, unaffected by the GIL.
- Multiprocessing is ideal for CPU-bound tasks, such as heavy computations or data processing, where parallel execution is required to fully utilize multiple CPU cores.
- Python provides the multiprocessing module, which allows you to create and manage processes. Each process has its own memory and resources, making multiprocessing more robust but also more memory-intensive compared to threading.

# Basics of Python Programming Language
## Variables in Python
- Variables in Python are named references to objects in memory that store data. When defining a variable, you don't need to explicitly declare its type because the type is determined based on the value assigned to the variable. However, you need to be careful when naming variables, as Python is a case-sensitive programming language.

### Rules for Naming Variables
- Variable names must start with a letter `(a-z, A-Z)` or an underscore `(_)`.
- The rest of the name can include letters, numbers `(0-9)`, and underscores.
- Variable names cannot be a Python keyword `(like if, else, for, etc.)`.
- Variable names should be descriptive to improve code readability.

### Predefined Keywords in Python
- Keywords in Python are reserved words that have predefined meanings and purposes. They cannot be used as variable names, function names, or any other identifiers in Python programs.
- The predefined keywords in Python are: `False, None, True, and, as, assert, async, await, break, class, continue, def, del, elif, else, except, finally, for, from, global, if, import, in, is, lambda, nonlocal, not, or, pass, raise, return, try, while, with, yield`.

### Types of variables in Python
__A) Local Varibale:__ 
- These variables are defined inside a function and are accessible only within that function.
  ```python
  def greet():
      message = "Hello, World!"  # Local variable
      print(message)

  greet()
  # print(message)  # This will raise an error: NameError: name 'message' is not defined
  ```
__B) Global Variable:__
- These variables are defined outside of all functions or classes and can be accessed and modified throughout the program.
  ```python
  name = "Python"  # Global variable

  def show_name():
      print(name)

  show_name()  # Output: Python
  ```
__C) Nonlocal Variable:__
- These variables are defined inside a nested function and are not local to the inner function but belong to the enclosing function.
  ```python
  def outer_function():
      message = "Hello"

      def inner_function():
          nonlocal message
          message = "Hi"
          print(message)

      inner_function()
      print(message)

  outer_function()
  # Output:
  # Hi
  # Hi
  ```
__D) Instance Variable:__
- These variables are defined inside a class within an instance method (using `self`) and are associated with an instance of the class. They are used to store data specific to each instance.
  ```python
  class Person:
      def __init__(self, name, age):
          self.name = name  # Instance variable
          self.age = age    # Instance variable

  person1 = Person("Alice", 25)
  person2 = Person("Bob", 30)

  print(person1.name)  # Output: Alice
  print(person2.age)   # Output: 30
  ```
__E) Class Variable:__
- These variables are shared across all instances of a class. They are defined within the class, but outside of all instance methods. Their value is common to all instances of the class.
  ```python
  class Animal:
      species = "Mammal"  # Class variable

  cat = Animal()
  dog = Animal()

  print(cat.species)  # Output: Mammal
  print(dog.species)  # Output: Mammal
  ```
__F) Constant Variable:__
- Python does not have built-in constant support, but variables declared in all uppercase letters (by convention) are treated as constants. Their values should not be modified, though this is not enforced by the language.
  ```python
  import math
  import numpy as np

  print(np.pi)

  from scipy.constants import g

  print(g)
  ```

## Data Types in Python
__A) Numeric Datatype (`int`, `float`, `complex`):__
- Numeric datatype stores numeric values.
  ```python
  age = 25
  print(type(age))  # Output: <class 'int'>

  pi = 3.14159
  print(type(pi))  # Output: <class 'float'>

  z = 3 + 4j
  print(type(z))  # Output: <class 'complex'>
  ```
__B) Sequential Datatype (`str`, `list`, `tuple`):__ 
- Sequential datatype stores ordered collections of items.
  ```python
  name = "Python"
  print(type(name))  # Output: <class 'str'>
  
  fruits = ["apple", "banana", "cherry"]
  print(type(fruits))  # Output: <class 'list'>

  colors = ("red", "green", "blue")
  print(type(colors))  # Output: <class 'tuple'>
  ```
__C) Mapping Datatype (`dict`):__
- Mapping datatype represents a collection of key-value pairs.
  ```python
  person = {"name": "Alice", "age": 30}
  print(type(person))  # Output: <class 'dict'>
  ```
__D) Set Datatype:__
- Set datatype is used to store unordered collections of unique items.
  ```python
  numbers = {1, 2, 3}
  print(type(numbers))  # Output: <class 'set'>

  frozen_numbers = frozenset([1, 2, 3])
  print(type(frozen_numbers))  # Output: <class 'frozenset'>
  ```
__E) Boolean Datatype:__
- Boolean datatype Represents one of two values: `True` or `False`.
  ```python
  is_active = True
  print(type(is_active))  # Output: <class 'bool'>
  ```
__F) None Datatype:__
- None datatype represents the absence of a value or a null value.
  ```python
  value = None
  print(type(value))  # Output: <class 'NoneType'>
  ```

### Ducktyping in Python
- Duck typing is a concept in dynamic typing where the type of an object is determined by its behavior (methods or attributes) rather than its explicit type. The name comes from the phrase: ___"If it looks like a duck, swims like a duck, and quacks like a duck, then it probably is a duck."___

### Typecasting in Python
- Type casting refers to converting the data type of a variable from one data type to another. Since Python is dynamically typed, variables can change their type at runtime. Python also provides built-in functions to perform explicit type conversions.

__A) Implicit Type Casting:__
- Python automatically converts one data type to another to prevent data loss during operations.
  ```python
  a = 10   # int
  b = 3.5  # float
  result = a + b  # int + float = float
  print(result)       # Output: 13.5
  print(type(result))  # Output: <class 'float'>
  ```
__B) Explicit Type Casting:__
- Performed manually using type conversion functions like `int()`, `float()`, `str()`, `list()`, `tuple()`, `set()`, `bool()`
  ```python
  a = "123"   # str
  b = int(a)  # Convert str to int
  print(b)       # Output: 123
  print(type(b))  # Output: <class 'int'>
  ```

## Operators in Python
- Operators in Python are special symbols or keywords that perform specific operations on one or more operands.

__A) Arithmetic Operators:__ Used to perform mathematical operations.

| Operator | Description    |
|----------|----------------|
| +        | Addition       |
| -        | Substraction   |
| *        | Multiplication |
| /        | Division       |
| //       | Floor Division |
| %        | Modulus        |
| **       | Exponentiation |

__B) Comparison Operators:__ Used to compare two values, returning `True` or `False`.

| Operator | Description           |
|----------|-----------------------|
| ==       | Equal to              |
| !=       | Not equal to          |
| >        | Greater than          |
| <        | Less than             |
| >=       | Greater than or equal |
| <=       | Less than or equal    |

__C) Logical Operators:__ Used to perform logical operations.

| Operator | Description                            |
|----------|----------------------------------------|
| and      | Logical AND (`True and False → False`) |
| or       | Logical OR (`True or False → True`)    |
| not      | Logical NOT (`not True → False`)       |

__D) Assignment Operators:__ Used to assign values to variables.

| Operator | Description               |
|----------|---------------------------|
| =        | Assign                    |
| +=       | Add and assign            |
| -=       | Subtract and assign       |
| *=       | Multiply and assign       |
| /=       | Divide and assign         |
| //=      | Floor divide and assign   |
| %=       | Modulus and assign        |
| **=      | Exponentiation and assign |

__E) Bitwise Operators:__ Used for binary operations on bits.

| Operator | Description |
|----------|-------------|
| &        | AND         |
| `        | OR          |
| ^        | XOR         |
| <<       | Left shift  |
| >>       | Right shift |

__F) Membership Operators:__ Used to check if a value exists in a sequence (like strings, lists, or tuples).

| Operator | Description                                               |
|----------|-----------------------------------------------------------|
| in       | `True` if value exists (`'a' in 'apple' → True`)          |
| not in   | `True` if value does not exist (`'b' in 'apple' → False`) |

__G) Identity Operators:__ Used to compare memory addresses (ID) of two objects.

| Operator | Description                                       |
|----------|---------------------------------------------------|
| is       | `True` if objects are the same (`x is y`)         |
| is not   | `True` if objects are not the same (`x is not y`) |

__H) Ternary Operators:__ Allows conditional expressions in a single line.
```python
result = "Positive" if x > 0 else "Non-positive"
```

## Printing Methods in Python
__A) `print()` Function:__
- The most commonly used function to display output in Python.
  ```python
  # Simple print statement
  print("Hello, World!")  # Output: Hello, World!

  # Printing variables
  name = "Alice"
  age = 25
  print("Name:", name, "Age:", age)  # Output: Name: Alice Age: 25
  ```  
__B) String Concatenation in print():__
- You can concatenate strings with `+` while using `print()`.
  ```python
  # Concatenation example
  greeting = "Hello"
  name = "Bob"
  print(greeting + ", " + name + "!")  # Output: Hello, Bob!
  ```  
__C) `format()` Method:__
- This method allows inserting variables into placeholders `{}` within a string.
  ```python
  # Using .format()
  name = "Diana"
  city = "Paris"
  print("Hello, my name is {} and I live in {}.".format(name, city))  
  # Output: Hello, my name is Diana and I live in Paris.
  
  # You can also use index numbers in placeholders
  print("I am {0} years old, and I live in {1}.".format(25, "New York"))  
  # Output: I am 25 years old, and I live in New York.
  ```  
__D) `f-string` Method:__
- Introduced in Python 3.6, f-strings provide an easy way to format strings. Variables can be embedded directly within curly braces `{}`.
  ```python
  name = "Charlie"
  age = 30
  print(f"My name is {name}, and I am {age} years old.")  
  # Output: My name is Charlie, and I am 30 years old.
  ```  
__E) Printing with Custom Separators:__
- The `sep` argument in `print()` specifies the separator between multiple items.
  ```python
  # Using a custom separator
  print("Python", "is", "fun", sep="-")  # Output: Python-is-fun
  ```  
__F) Printing without a Newline:__
- By default, `print()` adds a newline after each statement. You can change this behaviour using the `end` argument.
  ```python
  # Printing on the same line
  print("Hello", end=" ")
  print("World!")  # Output: Hello World!
  ```  
__G) Escape Characters in Printing:__
- Python supports escape characters for special formatting in strings.
  ```python
  print("Line 1\nLine 2")  # Newline
  # Output:
  # Line 1
  # Line 2

  print("This is a tab:\tIndented")  # Tab
  # Output: This is a tab:	Indented

  print("Quotes: \"Double\" and \'Single\'")  # Quotation marks
  # Output: Quotes: "Double" and 'Single'
  ```  

### Comments
- Comments are lines in Python code that are ignored by the Python interpreter. They are used to add explanations, notes, or information about the code to make it easier for developers to understand and maintain. There are two types of comments in Python: ___Single-Line Comments___, ___Multi-Line Comments___.
  ```python
  # Single line comment
  # This is a single line comment

  # Multiple line comment
  '''The old lighthouse keeper, eyes like weathered glass,
  Climbed the spiral stairs, a lonely, rhythmic lass.
  The fog horn wailed, a mournful, distant cry,
  As another ship, unseen, sailed silently by.'''

  """The old lighthouse keeper, eyes like weathered glass,
  Climbed the spiral stairs, a lonely, rhythmic lass.
  The fog horn wailed, a mournful, distant cry,
  As another ship, unseen, sailed silently by."""
  ```

## Conditional Statements in Python
- Conditional statements in Python allow you to execute specific blocks of code based on whether a condition is `True` or `False`. The primary conditional statements in Python are `if`, `elif`, and `else`.

__A) `if`:__
- The `if` statement checks a condition. If the condition evaluates to `True`, the associated block of code is executed.
  ```python
  # Syntax
  if condition:
      # code to execute if the condition is True

  # Example
  age = 18
  if age >= 18:
      print("You are eligible to vote.")
  ```
__B) `if-else`:__
- The `else` block executes if the condition in the if statement is `False`.
  ```python
  # Syntax
  if condition:
      # code to execute if the condition is True
  else:
      # code to execute if the condition is False

  # Example
  age = 16
  if age >= 18:
      print("You are eligible to vote.")
  else:
      print("You are not eligible to vote.")
  ```
__C) `if-elif-else`:__
- The `elif` allows you to check multiple conditions. The `else` block executes if none of the conditions are `True`.
  ```python
  # Syntax
  if condition1:
      # code to execute if condition1 is True
  elif condition2:
      # code to execute if condition2 is True
  else:
      # code to execute if all conditions are False

  # Example
  marks = 85
  if marks >= 90:
      print("Grade: A")
  elif marks >= 80:
      print("Grade: B")
  elif marks >= 70:
      print("Grade: C")
  else:
      print("Grade: F")
  ```
__D) nested `if`:__
- You can place one `if` statement inside another to check for more specific conditions.
  ```python
  # Syntax
  if condition1:
      if condition2:
          # code to execute if both conditions are True

  # Example
  age = 20
  if age > 18:
      if age < 25:
          print("You are a young adult.")
  ```
__E) Conditional Expressions (Ternary Operator):__
- Python provides a concise way to write `if-else` statements in a single line.
  ```python
  # Syntax
  value = true_expression if condition else false_expression

  # Example
  age = 20
  status = "Adult" if age >= 18 else "Minor"
  print(status)
  ```
__F) Using Logical Operators with Conditions:__
- It combines multiple conditions using logical operators like `and`, `or`, and `not`.
  ```python
  # Example with `and`
  age = 20
  if age > 18 and age < 25:
      print("You are a young adult.")

  # Example with `or`
  age = 16
  if age < 18 or age > 65:
      print("You are not in the working-age group.")

  # Example with `not`
  is_raining = False
  if not is_raining:
      print("You can go outside.")
  ```

## Loops in Python
- Loops are control flow statements that execute a block of code repeatedly until a specific condition is met. Python provides two primary types of loops: `for` and `while`.

__A) `for` Loop:__
- The `for` loop is used to iterate over a sequence (like a `list`, `tuple`, `string`, or `range`). It executes the block of code for each element in the sequence.
  ```python
  # Syntax
  for variable in sequence:
      # code to execute

  # Example
  fruits = ["apple", "banana", "cherry"]
  for fruit in fruits:
      print(fruit)
  ```
__B) `while` Loop:__
- The `while` loop continues to execute as long as the specified condition is `True`. It is commonly used when the number of iterations is not known in advance.
  ```python
  # Syntax
  while condition:
      # code to execute
  # Example
  count = 0
  while count < 5:
      print(count)
      count += 1
  ```

### Loop Control Statements
__A) `break`:__
- Terminates the loop prematurely when a condition is met.
  ```python
  for number in range(10):
      if number == 5:
          break
      print(number)
  ```
__B) `continue`:__
- Skips the current iteration and moves to the next one.
  ```python
  for number in range(5):
      if number == 2:
          continue
      print(number)
  ```
__C) `pass`:__
- Does nothing and acts as a placeholder in loops or functions where no action is required.
  ```python
  for number in range(5):
      if number == 2:
          pass  # Placeholder
      print(number)
  ```
__D) Nested Loops:__
- A loop inside another loop.
  ```python
  for i in range(3):
      for j in range(2):
          print(f"i={i}, j={j}")
  ```
__E) Else with Loops:__
- The `else` block in loops executes after the loop finishes, but not if the loop is terminated with `break`.
  ```python
  for number in range(5):
      print(number)
  else:
      print("Loop finished")
  ```

# String
In Python, a string is a sequence of characters enclosed in single `' '`, double `" "` or triple quotes`''' '''`. Strings are ___immutable___. Strings cannot be changed after creation. Any operation that modifies a string creates a new string.

### String Indexing
- Indexing is used to access individual characters using indices ___(indexing starts from 0 whereas length starts from 1)___.
  ```python
  s = "Python"
  print(s[0])   # Output: P (first character)
  print(s[-1])  # Output: n (last character)
  ```

### String Slicing
- String slicing extract substrings using the colon `:` operator.
  ```python
  s = "Python"
  print(s[0:3])   # Output: Pyt (characters from index 0 to 2)
  print(s[:3])    # Output: Pyt (start is optional)
  print(s[3:])    # Output: hon (end is optional)
  print(s[::-1])  # Output: nohtyP (reverse string)
  ```

### Common String Operations
__A) Concatenation:__
```python
s1 = "Hello"
s2 = "World"
print(s1 + " " + s2)  # Output: Hello World
```
__B) Repetition:__
```python
s = "Hi! "
print(s * 3)  # Output: Hi! Hi! Hi!
```
__C) Length:__
```python
s = "Python"
print(len(s))  # Output: 6
```
__D) Membership Testing:__
```python
s = "Python"
print("Py" in s)  # Output: True
print("Java" not in s)  # Output: True
```
__E) Reversing a String:__
```python
s = "Python"
print(s[::-1])  # Output: nohtyP
```
__F) Parsing Data:__
```python
data = "name=Omkar;age=25;location=Pune"
pairs = data.split(";")
for pair in pairs:
    key, value = pair.split("=")
    print(f"{key}: {value}")
```
__G) Generating Dynamic Text:__
```python
template = "Hello, {name}! Welcome to {platform}."
print(template.format(name="Omkar", platform="Python Programming"))
```

### Common String Functions

| Function       | Description                                                                                         | Example                                               |
|----------------|-----------------------------------------------------------------------------------------------------|-------------------------------------------------------|
| `upper()`      | Converts all characters in the string to uppercase.                                                 | `"hello".upper()` → `HELLO`                           |
| `lower()`      | Converts all characters in the string to lowercase.                                                 | `"HELLO".lower()` → `hello`                           |
| `capitalize()` | Converts the first character to uppercase and the rest to lowercase.                                | `"hello world".capitalize()` → `Hello world`          |
| `title()`      | Converts the first character of each word to uppercase.                                             | `"hello world".title()` → `Hello World`               |
| `casefold()`   | Converts string to lowercase for caseless matching (more aggressive than `lower()`).                | `"ß".casefold()` → `ss`                               |
| `swapcase()`   | Swaps the case of all characters in the string.                                                     | `"Hello".swapcase()` → `hELLO`                        |
| `lstrip()`     | Removes leading whitespace (or specified characters).                                               | `"   hello".lstrip()` → `hello`                       |
| `strip()`      | Removes leading and trailing whitespace (or specified characters).                                  | `"   hello   ".strip()` → `hello`                     |
| `rstrip()`     | Removes trailing whitespace (or specified characters).                                              | `"hello   ".rstrip()` → `hello`                       |
| `center()`     | Centers the string within a specified width, padding with spaces (or specified character).          | `"hello".center(10)` → `"  hello   "`                 |
| `ljust()`      | Left-justifies the string within a specified width.                                                 | `"hello".ljust(10)` → `"hello     "`                  |
| `rjust()`      | Right-justifies the string within a specified width.                                                | `"hello".rjust(10)` → `"     hello"`                  |
| `zfill()`      | Pads the string with zeros on the left, making it the specified width.                              | `"42".zfill(5)` → `00042`                             |
| `replace()`    | Replaces occurrences of a substring with another substring.                                         | `"hello".replace("l", "w")` → `hewwo`                 |
| `split()`      | Splits the string into a list of substrings based on a delimiter.                                   | `"a,b,c".split(",")` → `['a', 'b', 'c']`              |
| `join()`       | Joins a list of strings into one string, separated by a specified delimiter.                        | `",".join(['a', 'b', 'c'])` → `a,b,c`                 |
| `count()`      | Counts the occurrences of a substring in the string.                                                | `"banana".count("a")` → `3`                           |
| `expandtabs()` | Replaces tab characters (`\t`) with spaces (default is 8 spaces).                                   | `"a\tb".expandtabs(4)` → `a   b`                      |
| `index()`      | Finds the index of the first occurrence of a substring (raises `ValueError` if not found).          | `"hello".index("e")` → `1`                            |
| `find()`       | Finds the index of the first occurrence of a substring (returns `-1` if not found).                 | `"hello".find("e")` → `1`, `"hello".find("z")` → `-1` |
| `endswith()`   | Returns `True` if the string ends with the specified substring.                                     | `"hello".endswith("o")` → `True`                      |
| `startswith()` | Returns `True` if the string starts with the specified substring.                                   | `"hello".startswith("h")` → `True`                    |
| `isspace()`    | Returns `True` if the string contains only whitespace characters.                                   | `"   ".isspace()` → `True`                            |
| `istitle()`    | Returns `True` if the string follows title case conventions.                                        | `"Hello World".istitle()` → `True`                    |
| `isupper()`    | Returns `True` if all alphabetic characters in the string are uppercase.                            | `"HELLO".isupper()` → `True`                          |
| `islower()`    | Returns `True` if all alphabetic characters in the string are lowercase.                            | `"hello".islower()` → `True`                          |
| `isalnum()`    | Returns `True` if the string contains only alphanumeric characters (no spaces or special chars).    | `"abc123".isalnum()` → `True`                         |
| `isalpha()`    | Returns `True` if the string contains only alphabetic characters.                                   | `"abc".isalpha()` → `True`                            |
| `isdecimal()`  | Returns `True` if the string contains only decimal characters.                                      | `"123".isdecimal()` → `True`                          |
| `isdigit()`    | Returns `True` if the string contains only digit characters.                                        | `"123".isdigit()` → `True`                            |
| `isnumeric()`  | Returns `True` if the string contains numeric characters (including fractions, superscripts, etc.). | `"½".isnumeric()` → `True`                            |


# List
A list is a mutable, ordered, heterogeneous collection of elements enclosed by square brackets `[]`. ___Mutable___ means that lists can be changed after they are created. You can modify, add, or remove items. ___Ordered___ means that the items in a list maintain the order in which they are added. You can access the elements using their index. ___Heterogeneous___ means that lists can hold elements of different data types (integers, strings, floats, objects, etc.).
  ```python
  # Creating a list
  my_list = [1, 2, 3, "hello", 4.5]

  # Accessing elements using indexing
  my_list = [1, 2, 3, "hello"]
  print(my_list[0])  # Output: 1
  print(my_list[3])  # Output: hello

  # Negative indexing
  print(my_list[-1])  # Output: hello

  # SLicing a list
  my_list = [1, 2, 3, 4, 5]
  sublist = my_list[1:3]  # Output: [2, 3]

  # Nested list
  matrix = [[1, 2], [3, 4], [5, 6]]
  print(matrix[0])  # Output: [1, 2]
  ```

### List Comprehension
- List comprehension provides a concise way to create lists based on existing lists.
  ```python
  squared_numbers = [x**2 for x in range(5)]
  print(squared_numbers)  # Output: [0, 1, 4, 9, 16]
  ```

### Common List Functions:

| Function     | Description                                                                            | Example                                              |
|--------------|----------------------------------------------------------------------------------------|------------------------------------------------------|
| `len()`      | Returns the number of elements in the list.                                            | `len([1, 2, 3])` → `3`                               |
| `type()`     | Returns the type of the object.                                                        | `type([1, 2, 3])` → `<class 'list'>`                 |
| `sum()`      | Returns the sum of all numeric elements in the list.                                   | `sum([1, 2, 3])` → `6`                               |
| `min()`      | Returns the smallest element in the list.                                              | `min([1, 2, 3])` → `1`                               |
| `max()`      | Returns the largest element in the list.                                               | `max([1, 2, 3])` → `3`                               |
| `append()`   | Adds an element to the end of the list.                                                | `lst = [1, 2]; lst.append(3)` → `[1, 2, 3]`          |
| `insert()`   | Inserts an element at a specific index.                                                | `lst = [1, 2]; lst.insert(1, 10)` → `[1, 10, 2]`     |
| `extend()`   | Extends the list by appending elements from another list or iterable.                  | `lst = [1, 2]; lst.extend([3, 4])` → `[1, 2, 3, 4]`  |
| `remove()`   | Removes the first occurrence of a specified value.                                     | `lst = [1, 2, 3]; lst.remove(2)` → `[1, 3]`          |
| `pop()`      | Removes and returns an element at the specified index (default: last).                 | `lst = [1, 2, 3]; lst.pop()` → `3`, `lst` → `[1, 2]` |
| `del`        | Deletes an element, slice, or the entire list.                                         | `lst = [1, 2, 3]; del lst[1]` → `[1, 3]`             |
| `clear()`    | Removes all elements from the list.                                                    | `lst = [1, 2, 3]; lst.clear()` → `[]`                |
| `sort()`     | Sorts the list in place, in ascending or descending order.                             | `lst = [3, 1, 2]; lst.sort()` → `[1, 2, 3]`          |
| `sorted()`   | Returns a new sorted list without modifying the original list.                         | `lst = [3, 1, 2]; sorted(lst)` → `[1, 2, 3]`         |
| `reverse()`  | Reverses the elements of the list in place.                                            | `lst = [1, 2, 3]; lst.reverse()` → `[3, 2, 1]`       |
| `reversed()` | Returns an iterator to access elements in reverse without modifying the original list. | `lst = [1, 2, 3]; list(reversed(lst))` → `[3, 2, 1]` |

# Tuple
A tuple is an immutable, ordered, heterogeneous, and hashable collection of elements enclosed by parentheses `()`. ___Immutable___ means that once a tuple is created, its contents cannot be changed, meaning you cannot add, remove, or modify elements. ___Ordered___ means that the items in a tuple maintain the order in which they are added. You can access the elements using their index. ___Heterogeneous___ means that tuples can hold elements of different data types (integers, strings, floats, objects, etc.). ___Hashable___ means that since tuples are immutable, they can be used as keys in dictionaries, unlike lists, which are mutable and cannot be used as dictionary keys. ___Tuples are faster than lists in Python___ mainly because they are immutable. This immutability allows Python to optimize memory usage, iteration speed, and internal management of the data structure. In contrast, lists, being mutable, come with extra overhead to handle dynamic resizing and changes to the data, which makes them slightly slower than tuples for read-only operations.
  ```python
  # Creating a tuple
  my_tuple = (1, 2, 3, "hello", 4.5)

  # Accessing elements using indexing
  my_tuple = (1, 2, 3, "hello")
  print(my_tuple[0])  # Output: 1
  print(my_tuple[3])  # Output: hello

  # Negative indexing
  print(my_tuple[-1])  # Output: hello

  # Slicing a tuple
  my_tuple = (1, 2, 3, 4, 5)
  sub_tuple = my_tuple[1:3]  # Output: (2, 3)

  # Nested tuple
  nested_tuple = ((1, 2), (3, 4), (5, 6))
  print(nested_tuple[0])  # Output: (1, 2)
  ```

### Tuple Packing
- Tuplpe packing is a way to create a tuple by grouping values together.
  ```python
  # Tuple packing
  my_tuple = 1, 2, 3  # Tuple packing

  # Tuple unpacking
  a, b, c = my_tuple  # Unpacking the tuple
  print(a, b, c)  # Output: 1 2 3
  ```

### Common Tuple Functions

| Function                     | Description                                                                                   | Example                                                       |
|------------------------------|-----------------------------------------------------------------------------------------------|---------------------------------------------------------------|
| `count()`                     | Returns the number of occurrences of a specified element in the tuple.                        | `t = (1, 2, 2, 3); t.count(2)` → `2`                         |
| `index()`                     | Returns the index of the first occurrence of the specified element in the tuple.              | `t = (1, 2, 3, 4); t.index(3)` → `2`                          |


# Set
A set is a mutable, unordered, heterogeneous, and unique collection of elements enclosed by curly brackets `{}`. ___Mutable___ means you can add or remove elements from a set, but once created, the order of elements in the set is not guaranteed to stay the same. ___Unordered___ means the elements in a set do not maintain any specific order. You cannot access elements by an index like you can with lists or tuples. ___Heterogeneous___ means sets can hold elements of different data types, such as integers, strings, and floats. However, elements must be hashable (e.g., you cannot include a list inside a set). ___Unique___ means sets automatically eliminate duplicate elements. If you try to add a duplicate value to a set, it will not be added.
  ```python
  # Creating a set
  my_set = {1, 2, 3, "hello", 4.5}

  # Alternatively, you can create an empty set using set()
  empty_set = set()

  # Adding elements
  my_set = {1, 2, 3}
  my_set.add(4)  # Adds 4 to the set
  print(my_set)  # Output: {1, 2, 3, 4}

  # Removing duplicate elements
  my_list = [1, 2, 3, 3, 4, 5, 5]
  unique_elements = set(my_list)
  print(unique_elements)  # Output: {1, 2, 3, 4, 5}
  ```

### Set Comprehension:
- You can create sets using set comprehension, similar to list comprehension.
  ```python
  squared_set = {x**2 for x in range(5)}  # Output: {0, 1, 4, 9, 16}
  ```

### Common Set Functions

| Function                        | Description                                                                                      | Example                                                                   |
|---------------------------------|--------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------|
| `add()`                         | Adds an element to the set (if it is not already present).                                       | `s = {1, 2}; s.add(3)` → `{1, 2, 3}`                                      |
| `update()`                      | Updates the set with elements from another set or iterable (adds elements to the set).           | `s = {1, 2}; s.update([3, 4])` → `{1, 2, 3, 4}`                           |
| `union()`                       | Returns a new set with all elements from both sets (union of sets).                              | `s1 = {1, 2}; s2 = {2, 3}; s1.union(s2)` → `{1, 2, 3}`                    |
| `remove()`                      | Removes the specified element from the set (raises `KeyError` if not found).                     | `s = {1, 2, 3}; s.remove(2)` → `{1, 3}`                                   |
| `discard()`                     | Removes the specified element from the set (does nothing if element is not found).               | `s = {1, 2, 3}; s.discard(2)` → `{1, 3}`                                  |
| `pop()`                         | Removes and returns an arbitrary element from the set (raises `KeyError` if set is empty).       | `s = {1, 2, 3}; s.pop()` → `1` (or any arbitrary element)                 |
| `clear()`                       | Removes all elements from the set.                                                               | `s = {1, 2, 3}; s.clear()` → `set()`                                      |
| `intersection()`                | Returns a new set with elements common to both sets (intersection of sets).                      | `s1 = {1, 2}; s2 = {2, 3}; s1.intersection(s2)` → `{2}`                   |
| `intersection_update()`         | Updates the set to keep only the elements found in both sets (intersection).                     | `s1 = {1, 2}; s2 = {2, 3}; s1.intersection_update(s2)` → `{2}`            |
| `difference()`                  | Returns a new set with elements in the first set but not in the second (set difference).         | `s1 = {1, 2, 3}; s2 = {2, 3}; s1.difference(s2)` → `{1}`                  |
| `difference_update()`           | Updates the set to remove elements found in the second set (difference).                         | `s1 = {1, 2, 3}; s2 = {2, 3}; s1.difference_update(s2)` → `{1}`           |
| `symmetric_difference()`        | Returns a new set with elements in either set, but not both (symmetric difference).              | `s1 = {1, 2}; s2 = {2, 3}; s1.symmetric_difference(s2)` → `{1, 3}`        |
| `symmetric_difference_update()` | Updates the set to keep elements that are in either set, but not both (symmetric difference).    | `s1 = {1, 2}; s2 = {2, 3}; s1.symmetric_difference_update(s2)` → `{1, 3}` |
| `issubset()`                    | Returns `True` if the set is a subset of another set (all elements are in the other set).        | `s1 = {1, 2}; s2 = {1, 2, 3}; s1.issubset(s2)` → `True`                   |
| `isuperset()`                   | Returns `True` if the set is a superset of another set (contains all elements of the other set). | `s1 = {1, 2, 3}; s2 = {2}; s1.isuperset(s2)` → `True`                     |
| `isdisjoint()`                  | Returns `True` if the set has no elements in common with another set.                            | `s1 = {1, 2}; s2 = {3, 4}; s1.isdisjoint(s2)` → `True`                    |

## FrozenSet
- A frozenset in Python is an immutable version of a set. ___Immutable___ means once a frozenset is created, you cannot add, remove, or modify its elements. This immutability is the primary distinction between a frozenset and a regular set. Because frozensets are immutable, they are hashable and can be used as dictionary keys or added to other sets.
  ```python
  # Creating a frozenset from a set or list
  frozen_set = frozenset([1, 2, 3, 4, 5])
  print(frozen_set)  # Output: frozenset({1, 2, 3, 4, 5})

  # Using as dictionary keys
  frozen_set = frozenset([1, 2, 3])
  my_dict = {frozen_set: "value"}
  print(my_dict)  # Output: {frozenset({1, 2, 3}): 'value'}
  ```

### Common FrozenSet Functions

| Function                 | Description                                                                                                        | Example                                                                                                 |
|--------------------------|--------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| `add()`                  | Not supported for `frozenset` (raises `AttributeError`).                                                           | `fs = frozenset([1, 2]); fs.add(3)` → `AttributeError`                                                  |
| `remove()`               | Removes the specified element from the frozenset (raises `KeyError` if not found).                                 | `fs = frozenset([1, 2, 3]); fs.remove(2)` → `frozenset([1, 3])`                                         |
| `discard()`              | Removes the specified element from the frozenset (does nothing if element is not found).                           | `fs = frozenset([1, 2, 3]); fs.discard(2)` → `frozenset([1, 3])`                                        |
| `pop()`                  | Removes and returns an arbitrary element from the frozenset (raises `KeyError` if empty).                          | `fs = frozenset([1, 2, 3]); fs.pop()` → `1` (or any arbitrary element)                                  |
| `clear()`                | Not supported for `frozenset` (raises `AttributeError`).                                                           | `fs = frozenset([1, 2]); fs.clear()` → `AttributeError`                                                 |
| `union()`                | Returns a new frozenset with all elements from both sets (union of frozensets).                                    | `fs1 = frozenset([1, 2]); fs2 = frozenset([2, 3]); fs1.union(fs2)` → `frozenset([1, 2, 3])`             |
| `intersection()`         | Returns a new frozenset with elements common to both sets (intersection of frozensets).                            | `fs1 = frozenset([1, 2]); fs2 = frozenset([2, 3]); fs1.intersection(fs2)` → `frozenset([2])`            |
| `difference()`           | Returns a new frozenset with elements in the first set but not in the second (difference).                         | `fs1 = frozenset([1, 2, 3]); fs2 = frozenset([2, 3]); fs1.difference(fs2)` → `frozenset([1])`           |
| `symmetric_difference()` | Returns a new frozenset with elements in either set, but not both (symmetric difference).                          | `fs1 = frozenset([1, 2]); fs2 = frozenset([2, 3]); fs1.symmetric_difference(fs2)` → `frozenset([1, 3])` |
| `issubset()`             | Returns `True` if the frozenset is a subset of another frozenset (all elements are in the other frozenset).        | `fs1 = frozenset([1, 2]); fs2 = frozenset([1, 2, 3]); fs1.issubset(fs2)` → `True`                       |
| `isuperset()`            | Returns `True` if the frozenset is a superset of another frozenset (contains all elements of the other frozenset). | `fs1 = frozenset([1, 2, 3]); fs2 = frozenset([2]); fs1.isuperset(fs2)` → `True`                         |
| `isdisjoint()`           | Returns `True` if the frozenset has no elements in common with another frozenset.                                  | `fs1 = frozenset([1, 2]); fs2 = frozenset([3, 4]); fs1.isdisjoint(fs2)` → `True`                        |

# Dictionary
A dictionary in Python is a mutable, unordered, heterogeneous, and indexed collection of key-value pairs, where each key is unique, enclosed by curly brackets `{}`, and each key-value pair is separated by a colon `:`. Dictionaries are used to store data values like a map, where each key maps to a specific value. ___Mutable___ means you can add, modify, or remove key-value pairs after the dictionary is created. ___Unordered___ means dictionaries do not maintain any specific order for the key-value pairs. However, ___as of Python 3.7+, dictionaries preserve the insertion order of items___ (i.e., the order in which the key-value pairs were added). ___Heterogeneous___ means a dictionary can store values of any data type (integers, strings, lists, etc.), and different data types can be used for keys and values. ___Indexed___ means the values in a dictionary are accessed using keys (instead of indexes, like lists or tuples). ___Each key in a dictionary must be unique___. If you try to add a duplicate key, the old value associated with that key will be replaced with the new one. ___The keys in a dictionary must be hashable___ (i.e., they must be immutable types like strings, numbers, or tuples).
  ```python
  # Creating a dictionary with key-value pairs
  my_dict = {"name": "John", "age": 30, "city": "New York"}
  print(my_dict)  # Output: {'name': 'John', 'age': 30, 'city': 'New York'}

  # Accessing a value using its key; If a key is not found, it raises a KeyError
  print(my_dict["name"])  # Output: John

  # Using get() to avoid KeyError
  print(my_dict.get("name"))  # Output: John
  print(my_dict.get("address", "Not Found"))  # Output: Not Found

  # Modifying a value
  my_dict["age"] = 35

  # Adding a new key-value pair
  my_dict["address"] = "123 Main St"

  print(my_dict)  # Output: {'name': 'John', 'age': 35, 'city': 'New York', 'address': '123 Main St'}

  # Using del to remove a key-value pair
  del my_dict["city"]
  ```

### Dictionary Comprehension
- Like list comprehension, you can also create dictionaries using dictionary comprehension.
  ```python
  # Dictionary comprehension to square numbers
  squared_dict = {x: x**2 for x in range(5)}
  print(squared_dict)  # Output: {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}
  ```

### Common Dictionary Functions

| Function       | Description                                                                                                 | Example                                                                |
|----------------|-------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| `get()`        | Returns the value for the specified key, or a default value if the key doesn't exist.                       | `d = {'a': 1, 'b': 2}; d.get('a')` → `1`, `d.get('c', 3)` → `3`        |
| `update()`     | Updates the dictionary with elements from another dictionary or iterable of key-value pairs.                | `d = {'a': 1}; d.update({'b': 2})` → `{'a': 1, 'b': 2}`                |
| `keys()`       | Returns a view object that displays a list of all the keys in the dictionary.                               | `d = {'a': 1, 'b': 2}; d.keys()` → `dict_keys(['a', 'b'])`             |
| `values()`     | Returns a view object that displays a list of all the values in the dictionary.                             | `d = {'a': 1, 'b': 2}; d.values()` → `dict_values([1, 2])`             |
| `items()`      | Returns a view object that displays a list of tuples, where each tuple is a key-value pair.                 | `d = {'a': 1, 'b': 2}; d.items()` → `dict_items([('a', 1), ('b', 2)])` |
| `pop()`        | Removes and returns the value for the specified key (raises `KeyError` if key is not found).                | `d = {'a': 1, 'b': 2}; d.pop('a')` → `1`                               |
| `popitem()`    | Removes and returns the last key-value pair from the dictionary (raises `KeyError` if empty).               | `d = {'a': 1, 'b': 2}; d.popitem()` → `('b', 2)`                       |
| `fromkeys()`   | Returns a new dictionary with keys from a given sequence and values set to a specified value.               | `keys = ['a', 'b']; dict.fromkeys(keys, 0)` → `{'a': 0, 'b': 0}`       |
| `setdefault()` | Returns the value of the specified key (if the key exists), otherwise inserts the key with a default value. | `d = {'a': 1}; d.setdefault('b', 2)` → `2`, `d` → `{'a': 1, 'b': 2}`   |

# Shallow Copy & Deep Copy
In Python, shallow copy and deep copy refer to ways of copying data structures, particularly when dealing with mutable objects like lists, dictionaries, etc. They determine how the objects and their contents are copied and whether changes to one affect the other.

__A) Shallow Copy:__
- A shallow copy creates a new object, but it does not recursively copy the nested objects. Instead, it copies references to the nested objects contained in the original object. This means that changes to the new object itself will not affect the original object, but changes made to its nested objects will affect the original object.
  ```python
  import copy

  original = [1, [2, 3], [4, 5, 6]]
  shallow_copy = copy.copy(original)

  # Modifying a nested element in the shallow copy
  shallow_copy[0] = 10
  shallow_copy[1][0] = 20

  print("Original:", original)         # Output: [1, [20, 3], [4, 5, 6]]
  print("Shallow Copy:", shallow_copy)  # Output: [10, [20, 3], [4, 5, 6]]
  ```
__B) Deep Copy:__
- A deep copy creates a new object and recursively copies all objects found in the original, including the nested objects. This means that changes to the new object or its nested objects will not affect the original object.
  ```python
  import copy

  original = [1, [2, 3], [4, 5, 6]]
  deep_copy = copy.deepcopy(original)

  # Modifying a nested element in the deep copy
  deep_copy[0] = 10
  deep_copy[1][0] = 20

  print("Original:", original)         # Output: [1, [2, 3], [4, 5, 6]]
  print("Deep Copy:", deep_copy)       # Output: [10, [20, 3], [4, 5, 6]]
  ```

# Functions
A function in Python is a reusable block of code that performs a specific task, takes input (optional), processes it, and returns an output (optional). Functions help organize code, avoid repetition, and make programs easier to read and maintain.

## User Defined Functions
- A user-defined function is a custom function created by the user to perform a specific task. These functions are defined using the `def` keyword, followed by the function name, parentheses `()`, and a colon `:`. The name you give to your function should follow naming conventions.
  ```python
  # User-defined function to calculate the square of a number
  def square(num):
      return num * num

  # Calling the function
  result = square(4)
  print(result)  # Output: 16
  ```

### Parameters in User Defined Functions
- Parameters are placeholders defined in the function that specify the input values a function can accept.
  ```python
  def greet(name):  # `name` is a parameter
      print(f"Hello, {name}!")
  ```
__Types of Parameters:__
- __A) Positional Parameters:__ Parameters that match with arguments based on their position.
  ```python
  def greet(name, age):
      print(f"Hello, {name}. You are {age} years old.")

  greet("Alice", 25)  # Positional arguments matched to parameters
  ```
- __B) Default Parameters:__ Parameters that have default values. If an argument is not provided, the default value is used.
  ```python
  def greet(name, age=18):
      print(f"Hello, {name}. You are {age} years old.")

  greet("Alice", 25)  # Overrides default value
  greet("Bob")        # Uses default value (age=18)
  ```
- __C) Keyword Parameters:__ Parameters specified by their names during the function call, allowing arguments to be passed in any order.
  ```python
  def greet(name, age):
      print(f"Hello, {name}. You are {age} years old.")

  greet(age=25, name="Alice")  # Arguments provided out of order
  ```
- __D) Variable-Length Parameters:__ Used to accept an arbitrary number of arguments (`**args`, `**kwargs`).
  > __**args:__ Captures any number of positional arguments as a tuple.
  
  > __**kwargs:__ Captures any number of keyword arguments as a dictionary.
  ```python
  # **args
  def sum_numbers(*args):
      return sum(args)

  print(sum_numbers(1, 2, 3, 4))  # Output: 10

  # **kwargs
  def display_info(**kwargs):
      for key, value in kwargs.items():
          print(f"{key}: {value}")

  display_info(name="Alice", age=25, city="New York")
  # Output:
  # name: Alice
  # age: 25
  # city: New York
  ```

### Arguments in User Defined Functions
- Arguments are the actual values passed to a function when it is called.
  ```python
  def introduce(name, age=18):  # `name` is required, `age` has a default value
      print(f"My name is {name}, and I am {age} years old.")

  introduce("Alice", 25)       # "Alice" and 25 are arguments
  introduce("Bob")             # "Bob" is an argument; `age` uses its default value
  ```

## Lambda Functions
- A lambda function in Python is a small, anonymous function defined using the `lambda` keyword. It can have any number of arguments but only one expression. Lambda functions do not have a name and are typically used where a function is required temporarily, which is why they are called anonymous. They are often used with higher-order functions (functions that either take one or more functions as arguments, or return another function as its result) such as `map()`, `filter()`, and `reduce()`.
  ```python
  # Syntax
  lambda arguments: expression
  
  # map(); applies a function to each item in an iterable
  numbers = [1, 2, 3, 4]
  squared = list(map(lambda x: x**2, numbers))
  print(squared)  # Output: [1, 4, 9, 16]

  #filter(); filters items in an iterable based on a condition.
  numbers = [1, 2, 3, 4]
  even = list(filter(lambda x: x % 2 == 0, numbers))
  print(even)  # Output: [2, 4]

  # reduce(); reduces an iterable to a single value using a function
  from functools import reduce
  numbers = [1, 2, 3, 4]
  product = reduce(lambda x, y: x * y, numbers)
  print(product)  # Output: 24
  ```

## Recursive Functions
- A recursive function is a function that calls itself in order to solve a problem. The function typically breaks down the problem into smaller, more manageable subproblems, solves them, and then combines the results. Recursive functions consist of two cases: a ___recursive case___ (where the function calls itself with modified arguments to reduce the problem size) and a ___base case___ (a condition that terminates the recursion, preventing an infinite loop). When the function is called, it performs a calculation and then calls itself with modified parameters. This continues until it reaches the base case, at which point the recursion stops, and the final result is returned.
  ```python
  # Syntax
  def recursive_function(parameters):
      if base_case_condition:
          return result  # base case
      else:
          return recursive_function(modified_parameters)  # recursive case

  # Example: Recursive function to calculate factorial
  def factorial(n):
      # Base case
      if n == 0:
          return 1
      # Recursive case
      else:
          return n * factorial(n - 1)

  # Example usage
  print(factorial(5))  # Output: 120

  # The recursive calls look like this:
  # factorial(5) → 5 * factorial(4) 
  # factorial(4) → 4 * factorial(3)
  # factorial(3) → 3 * factorial(2)
  # factorial(2) → 2 * factorial(1)
  # factorial(1) → 1 * factorial(0)
  # factorial(0) → 1  (base case)
  ```

## Built-in Functions
- In Python, built-in functions are pre-defined functions that are available for use without requiring the user to import any additional libraries or modules.

| Function   | Description                                                                                                                      | Example                                                                     |
|------------|----------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------|
| `ord()`    | Returns the Unicode code point for a given character.                                                                            | `ord('a')` → `97`                                                           |
| `chr()`    | Returns the character for a given Unicode code point.                                                                            | `chr(97)` → `'a'`                                                           |
| `bin()`    | Converts an integer to its binary representation (as a string).                                                                  | `bin(5)` → `'0b101'`                                                        |
| `id()`     | Returns the identity of an object (unique integer for each object).                                                              | `a = 5; id(a)` → Unique identifier like `140715705256064`                   |
| `zip()`    | Combines two or more iterables element-wise into an iterator of tuples.                                                          | `zip([1, 2], ['a', 'b'])` → `[(1, 'a'), (2, 'b')]`                          |
| `filter()` | Filters elements from an iterable based on a function that returns a boolean value.                                              | `filter(lambda x: x > 2, [1, 2, 3, 4])` → `[3, 4]`                          |
| `map()`    | Applies a function to all items in an iterable (or iterables) and returns an iterator of the results.                            | `map(lambda x: x**2, [1, 2, 3])` → `[1, 4, 9]`                              |
| `all()`    | Returns `True` if all elements of an iterable are true (or if the iterable is empty).                                            | `all([True, True, False])` → `False`                                        |
| `any()`    | Returns `True` if any element of an iterable is true (or if the iterable is empty).                                              | `any([True, False, False])` → `True`                                        |
| `abs()`    | Returns the absolute value of a number.                                                                                          | `abs(-5)` → `5`                                                             |
| `dir()`    | Returns a list of the attributes and methods of an object, or the current local scope if no object is provided.                  | `dir([1, 2, 3])` → `['__add__', '__class__', '__delattr__', ...]`           |
| `eval()`   | Executes a string expression and returns the result.                                                                             | `eval('3 + 2')` → `5`                                                       |
| `divmod()` | Returns a tuple containing the quotient and remainder when dividing two numbers.                                                 | `divmod(10, 3)` → `(3, 1)`                                                  |
| `reduce()` | Applies a function cumulatively to the items of an iterable, from left to right, so as to reduce the iterable to a single value. | `from functools import reduce; reduce(lambda x, y: x + y, [1, 2, 3])` → `6` |

# Namespace
In Python, a namespace refers to a container or a space where names (identifiers such as variable names, function names, class names, etc.) are mapped to objects. Essentially, it is a way of keeping track of all the objects in a program, ensuring that names are unique within a specific context. It is a dictionary-like structure where the key is the name (identifier), and the value is the object it refers to. For example, in the statement `x = 10`, the name `x` is mapped to the object `10` in the namespace.

## Types of Namespaces
__A) Built-in Namespace:__
- Contains names of built-in functions and exceptions in Python (e.g., print(), len(), Exception, etc.).
  
__B) Global Namespace:__
- This is the namespace for variables defined at the top-level of a script or module. These variables can be accessed anywhere within the module.
  
__C) Local Namespace:__ 
- Refers to namespaces created within functions or methods. Variables inside a function are part of its local namespace.
  
__D) Enclosing Namespace:__
- Refers to the namespaces of enclosing functions, especially in cases of nested functions. For example, in a function within a function, the enclosing function's namespace will contain names that the inner function can access.

> __LEGB Rule (Local, Enclosing, Global, Built-in)__: Python uses a specific order to search for a name when it is referenced. Python looks for a name in the local namespace first, then in the enclosing namespaces, then in the global namespace, and finally in the built-in namespace. This is called the LEGB rule.

> __Namespace Isolation:__ Namespaces provide isolation between different parts of a program. Variables in different namespaces don't conflict with each other. For example, a variable named x in a function won't overwrite the global variable x.

> __Modifying and Accessing Namespaces:__ The global namespace can be accessed and modified using the `global` keyword inside a function.

> __Scope and Lifetime of Namespaces:__ The scope of a namespace refers to where a name can be accessed in the program. The lifetime refers to how long the namespace exists. For example, a local namespaces are created when a function is called and destroyed when the function returns. In contrast, A global namespaces are created when the module is loaded and exist as long as the program is running.
```python
# Global namespace
x = 10

def outer_function():
    # Enclosing namespace
    y = 20
    
    def inner_function():
        # Local namespace
        z = 30
        print(x, y, z)  # Accesses x (global), y (enclosing), z (local)
    
    inner_function()

outer_function()

```

# Decorator
A decorator is a function that takes another function as an argument, adds some functionality to it, and returns a new function that enhances or modifies the original function's behaviour without changing its code. Decorators are commonly used for measuring execution time, modifying or validating input and output, logging, caching results, access control, and authentication. Multiple decorators can be applied to a single function, and they are applied from top to bottom. Decorators can also be used with methods in classes, often in combination with `@staticmethod`, `@classmethod`, or `@property`. Additionally, decorators can take arguments if you need to pass extra data to them.

## Types of Decorators
- __A) Built-in Decorators:__ `@staticmethod` (defines a static method in a class), `@classmethod` (defines a class method), `@property` (defines a property for a class).
- __B) User-defined Decorators__
```python
def my_decorator(func):
    def wrapper():
        print("Something before the function runs")
        func()
        print("Something after the function runs")
    return wrapper

@my_decorator
def say_hello():
    print("Hello!")

say_hello()
# Output:
# Something before the function runs
# Hello!
# Something after the function runs

# Decorators with arguments
def repeat(n):
    def decorator(func):
        def wrapper(*args, **kwargs):
            for _ in range(n):
                func(*args, **kwargs)
        return wrapper
    return decorator

@repeat(3)
def greet():
    print("Hello!")

greet()
# Output:
# Hello!
# Hello!
# Hello!

# Chaining decorators (multiple decorators to a single function)
@decorator1
@decorator2
def my_function():
    pass

# Decorating methods in class
class MyClass:
    @staticmethod
    def static_method():
        print("This is a static method.")
```

# Iterator
In Python, an iterator is an object that allows you to iterate through a collection of items, such as a list or tuple, one item at a time. An iterator implements two methods `__iter__()` method (which returns the iterator object) and `__next__()` method (which returns the next element in the sequence). If there are no more items, it raises a `StopIteration` exception. Iterators compute the next value only when required, saving memory. Once an iterator is exhausted (all elements have been iterated over), it cannot be reset or reused. You must create a new iterator to start over.
```python
# Creating an iterator from a list
my_list = [1, 2, 3, 4]
iterator = iter(my_list)

print(next(iterator))  # Output: 1
print(next(iterator))  # Output: 2
# Continue calling next() to access more elements
```
> __Iterable__ is an object capable of returning its elements one at a time like lists, tuples, strings and can implement the `__iter__()` method but not necessarily the `__next__()` method.

> __Iterator__ is an object that implements both `__iter__()` and `__next__()` methods. Every iterator is also an iterable, but not every iterable is an iterator.

# Generator
In Python, a generator is a special type of iterator that generates values as needed, rather than generating all the values at once and storing them in memory. It is defined using a function with the `yield` keyword instead of `return`, which pauses the function's execution and returns a value to the caller. When the function is called again, execution resumes from where it was paused.
```python
def count_up_to(n):
    count = 1
    while count <= n:
        yield count
        count += 1

gen = count_up_to(3)
print(next(gen))  # Output: 1
print(next(gen))  # Output: 2
print(next(gen))  # Output: 3
```

# Object-Oriented Programming (OOP)
Object-oriented programming (OOP) in Python is a programming paradigm and a way of organizing and writing code in a more structured and modular manner, reducing the need to write the same code repeatedly.

__Terminology in OOP:__
- __A) Class:__ A class is a blueprint or template for an object. In simple terms, it defines a set of rules, including methods (functions) and attributes (variables), that the objects created from the class will possess.
  ```python
  class Dog: # Dog is a class
      def __init__(self, name, breed):
          self.name = name
          self.breed = breed
      def bark(self):
          return f"{self.name} says woof!"
  ```
- __B) Object:__ An object is an instance of a class. It represents a specific example of the class with real data.
  ```python
  my_dog = Dog("Buddy", "Golden Retriever") # my_dog is an object of class Dog
  print(my_dog.bark())  # Output: Buddy says woof!
  ```
- __C) Instance Variables:__ Instance variables are the variables that are defined inside a class and are specific to each instance (or object) of that class. These variables are initialized in the `__init__` method of the class using the `self` keyword. The `self` keyword is used to refer to the current object, ensuring the variable belongs to that specific instance. Instance variables can be accessed or modified using the self keyword inside the class or using the object reference outside the class. Changes made to instance variables of one object do not affect those of another object.
  ```python
  class Person:
      def __init__(self, name, age):
          self.name = name  # Instance variable
          self.age = age    # Instance variable

  # Creating two objects
  person1 = Person("Alice", 30)
  person2 = Person("Bob", 25)

  # Accessing instance variables
  print(person1.name)  # Output: Alice
  print(person2.age)   # Output: 25

  # Modifying instance variables
  person1.age = 31
  print(person1.age)   # Output: 31
  ```
- __D) Static variables:__ Static variables, also called class variables, are shared by all instances (objects) of a class. They are not tied to any particular instance. Static variables are defined directly inside the class and outside any instance methods. Statics variables can be accessed using the class name.
  ```python
  class Car:
      wheels = 4  # Static variable (shared by all instances)    

      def __init__(self, brand, model):
          self.brand = brand    # Instance variable
          self.model = model    # Instance variable

  # Creating two instances of the Car class
  car1 = Car("Toyota", "Corolla")
  car2 = Car("Honda", "Civic")

  # Accessing static variable
  print(car1.wheels)  # Output: 4
  print(car2.wheels)  # Output: 4

  # Modifying the static variable
  Car.wheels = 5

  # Accessing static variable after modification
  print(car1.wheels)  # Output: 5
  print(car2.wheels)  # Output: 5
  ```
- __E) Static Methods:__ Static methods are methods that belong to the class rather than any instance of the class. Static methods can be called both by the class name or an instance. They are usually used for utility functions that don’t need to access or modify the object’s state or class state.
  ```python
  class Calculator:
      @staticmethod
      def add(a, b):
          return a + b

      @staticmethod
      def multiply(a, b):
          return a * b

  # Calling static methods via class name
  print(Calculator.add(5, 10))         # Output: 15
  print(Calculator.multiply(2, 3))     # Output: 6

  # Calling static methods via instance
  calc = Calculator()
  print(calc.add(10, 20))              # Output: 30
  print(calc.multiply(3, 4))           # Output: 12
  ```

### Magic Methods
- Magic methods, also called dunder methods (short for "double underscore"), are special methods in Python that are predefined in Python and are used to define the behaviour of objects in specific situations. Magic methods allow you to customize how objects behave for common operations.
  ```python
  class Point:
      def __init__(self, x, y):
          self.x = x
          self.y = y

      def __add__(self, other):
          return Point(self.x + other.x, self.y + other.y)

      def __str__(self):
          return f"Point({self.x}, {self.y})"

  p1 = Point(2, 3)
  p2 = Point(4, 5)

  p3 = p1 + p2  # Calls __add__
  print(p3)     # Calls __str__: Output: Point(6, 8)
  ```
__Some examples of Magic Methods:__
- __`__init__`:__ Initializes a new object (constructor).
- __`__str__`:__ Defines the string representation of an object.
- __`__add__`:__ Customizes the behavior of the `+` operator.
- __`__len__`:__ Defines behavior for the `len()` function.

### Constructors in OOP
- A constructor is a special magic method (`__init__`) in Python that is automatically called when a new object of a class is created.  The constructor is used to assign values to instance variables or to perform any setup required for the object. Python classes can have only one constructor.
  ```python
  class Person:
      def __init__(self, name, age):
          self.name = name
          self.age = age

      def greet(self):
          print(f"Hello, my name is {self.name} and I am {self.age} years old.")

  # Creating an object
  person1 = Person("Alice", 30)
  person1.greet()  # Output: Hello, my name is Alice and I am 30 years old.
  ```
  
## Concepts of OOP
### Encapsulation
- Encapsulation is a concept in object-oriented programming (OOP) that keeps the data (attributes or variables) and methods (functions) of a class together in one place. In simple terms, encapsulation is like putting data and methods in a box (class) and locking it.
- It controls how the data (attributes/variables and methods) inside a class can be accessed or modified, ensuring it is protected from accidental or improper use.
- Encapsulation hides the internal details of a class by restricting direct access to its attributes (variables) and methods. To safely access or modify private data, you use special methods called ___getters___ (to read the value) and ___setters___ (to update the value).
  ```python
  # Private attribute
  class BankAccount:
      def __init__(self, owner, balance):
          self.owner = owner  # Public attribute
          self.__balance = balance  # Private attribute (hidden)

      def deposit(self, amount):
          if amount > 0:
              self.__balance += amount
              print(f"Deposited {amount}. New balance: {self.__balance}")
          else:
              print("Deposit amount must be positive.")

      def withdraw(self, amount):
          if 0 < amount <= self.__balance:
              self.__balance -= amount
              print(f"Withdrew {amount}. New balance: {self.__balance}")
          else:
              print("Invalid withdrawal amount or insufficient funds.")

      def get_balance(self):  # Getter method to access private data
          return self.__balance

  # Using the class
  account = BankAccount("Alice", 1000)

  # Accessing public data
  print(account.owner)  # Output: Alice

  # Trying to access private data directly (will cause an error)
  # print(account.__balance)  # AttributeError

  # Using methods to work with private data
  account.deposit(500)  # Output: Deposited 500. New balance: 1500
  account.withdraw(200)  # Output: Withdrew 200. New balance: 1300
  print(account.get_balance())  # Output: 1300
  ```
  ```python
  # Private method
  class BankAccount:
      def __init__(self, owner, balance):
          self.owner = owner
          self.__balance = balance  # Private attribute

      def __private_method(self):  # Private method
          print("This is a private method.")

      def public_method(self):
          print("This is a public method.")
          self.__private_method()  # Accessing the private method within the class

  # Creating an instance
  account = BankAccount("Alice", 1000)

  # Accessing public method
  account.public_method()  # Works fine, prints the public and private method outputs

  # Trying to access private method directly will cause an error
  # account.__private_method()  # AttributeError: 'BankAccount' object has no attribute '__private_method'
  ```
__Access Levels in Python:__
- __A) Public:__ Attributes and methods can accessed directly by anyone.
- __B) Protected:__ Marked with a single underscore `_`. Can be accessed by the class and its subclasses.
- __C) Private:__ Marked with double underscores `__`. Can only be accessed inside the class.
  ```python
  class Person:
      def __init__(self, name, age):
          self.name = name           # Public attribute
          self._address = "Unknown"  # Protected attribute
          self.__age = age           # Private attribute
    
      # Public method
      def greet(self):
          print(f"Hello, my name is {self.name}")
    
      # Protected method
      def _get_address(self):
          return self._address
    
      # Private method
      def __get_age(self):
          return self.__age

  # Creating an object of the Person class
  person = Person("Alice", 25)

  # Accessing public attribute and method
  print(person.name)  # Output: Alice
  person.greet()      # Output: Hello, my name is Alice

  # Accessing protected attribute and method
  print(person._address)      # Output: Unknown
  print(person._get_address())  # Output: Unknown

  # Accessing private attribute and method (Not recommended)
  # Direct access to private variables and methods will raise an error
  # print(person.__age)  # AttributeError: 'Person' object has no attribute '__age'
  # print(person.__get_age())  # AttributeError: 'Person' object has no attribute '__get_age'

  # Accessing private attributes/methods using name mangling (Not recommended)
  print(person._Person__age)      # Output: 25
  print(person._Person__get_age())  # Output: 25
  ```
  
__Gettter & Setter Method:__
- To safely access or modify private data, you use special methods called getters (to read the value) and setters (to update the value).
  ```python
  class Person:
      def __init__(self, name, age):
          self.__name = name  # Private attribute
          self.__age = age    # Private attribute
    
      # Getter method for name
      def get_name(self):
          return self.__name
    
      # Setter method for name
      def set_name(self, name):
          self.__name = name
    
      # Getter method for age
      def get_age(self):
          return self.__age
    
      # Setter method for age
      def set_age(self, age):
          if age > 0:
              self.__age = age
          else:
              print("Age cannot be negative or zero")

  # Creating an object of Person class
  person = Person("Alice", 25)

  # Using getter methods to access private attributes
  print(person.get_name())  # Output: Alice
  print(person.get_age())   # Output: 25

  # Using setter methods to modify private attributes
  person.set_name("Bob")
  person.set_age(30)

  # Using getter methods to access updated attributes
  print(person.get_name())  # Output: Bob
  print(person.get_age())   # Output: 30
  ```

### Inheritance
- Inheritance is a concept in object-oriented programming (OOP) where a new class (called a child class or subclass) is based on an existing class (called a parent class or superclass). The child class inherits constructors, attributes, static attributes, methods and static methods from the parent class and can also add or modify them to make the child class more specialized, using the `super()` function. ___The child class can override (redefine) the methods of the parent class___ to provide specific functionality. Inheritance allows you to reuse code from the parent class. You don’t have to rewrite common functionality in every class which helps to organize code in a hierarchical way.

__Method Overriding:__
- The child class can override the methods of the parent class to provide a more specific or customized implementation.
  ```python
  class Animal:
      def sound(self):
          print("Some generic sound")

  class Dog(Animal):
      def sound(self):
          print("Bark")

  dog = Dog()
  dog.sound()  # Output: Bark (overridden method)

  # The child class can override the methods of the parent class to provide a more specific or customized implementation.
  ```
  
__Types of Inheritance:__
- __A) Single Inheritance:__ A subclass inherits from a single parent class.
  ```python
  class Parent:
      pass

  class Child(Parent):
      pass
  ```
- __B) Multiple Inheritance:__ A subclass inherits from more than one parent class.
  ```python
  class Mother:
      pass

  class Father:
      pass

  class Child(Mother, Father):
      pass
  ```
- __C) Multilevel Inheritance:__ A class derives from a subclass, creating a chain of inheritance.
  ```python
  class Grandparent:
      pass

  class Parent(Grandparent):
      pass

  class Child(Parent):
      pass
  ```
- __D) Hierarchical Inheritance:__ Multiple subclasses inherit from a single parent class.
  ```python
  class Parent:
      pass

  class Child1(Parent):
      pass

  class Child2(Parent):
      pass
  ```
- __E) Hybrid Inheritance:__ A combination of multiple inheritance types.
  ```python
  class ClassA:
      pass

  class ClassB:
      pass

  class ClassC(ClassA, ClassB):
      pass
  ```

__`super()` Function:__
- The `super()` function is used to call methods from the parent class inside the child class.
  ```python
  class Animal:
      def __init__(self, name):
          self.name = name

  class Dog(Animal):
      def __init__(self, name, breed):
          super().__init__(name)  # Calling the parent class constructor
          self.breed = breed

  dog = Dog("Buddy", "Golden Retriever")
  print(dog.name)  # Output: Buddy (from parent class)
  print(dog.breed)  # Output: Golden Retriever (from child class)
  ```

### Polymorphism
- Polymorphism is a concept in object-oriented programming (OOP) where different classes can have methods with the same name, but each method behaves differently depending on the object that is calling it. In simple terms, polymorphism allows you to use the same method name for different types of objects, but the method’s behaviour can change based on the type of object.
  ```python
  class Animal:
      def sound(self):
          print("Animal makes a sound")

  class Dog(Animal):
      def sound(self):
          print("Dog barks")

  class Cat(Animal):
      def sound(self):
          print("Cat meows")

  # Using polymorphism
  animal = Animal()
  dog = Dog()
  cat = Cat()

  animal.sound()  # Animal makes a sound
  dog.sound()     # Dog barks
  cat.sound()     # Cat meows
  ```

### Abstraction
- Abstraction is a concept in object-oriented programming (OOP) that focuses on hiding the implementation details of a class and only exposing the essential functionalities to the user to reduce complexity. It uses abstract classes and abstract methods. An ___abstract class___ cannot be instantiated directly; it serves as a blueprint for other classes. An ___abstract method___ is a method declared in an abstract class that must be implemented by any subclass that inherits the abstract class. Python provides abstraction using the `ABC` module from the `abc` package. An abstract class act as a contract: ___"If you want to inherit from me, you must define these methods!"___
  ```python
  from abc import ABC, abstractmethod

  # Abstract Base Class
  class Vehicle(ABC):
      @abstractmethod
      def start_engine(self):
          raise NotImplementedError("Subclass must implement start_engine method")

      @abstractmethod
      def stop_engine(self):
          raise NotImplementedError("Subclass must implement stop_engine method")

      def describe(self):
          """Concrete method to describe the vehicle"""
          print("This is a vehicle.")

  # Concrete Subclass
  class Car(Vehicle):
      def start_engine(self):
          print("The car's engine starts with a key or a button.")

      def stop_engine(self):
          print("The car's engine stops when you turn off the key or press the button.")

  # Another Concrete Subclass
  class Motorcycle(Vehicle):
      def start_engine(self):
          print("The motorcycle's engine starts with a kick or an electric button.")

      def stop_engine(self):
          print("The motorcycle's engine stops when you turn off the key or press the kill switch.")

  # Usage
  car = Car()
  car.describe()              # Output: This is a vehicle.
  car.start_engine()          # Output: The car's engine starts with a key or a button.
  car.stop_engine()           # Output: The car's engine stops when you turn off the key or press the button.

  bike = Motorcycle()
  bike.describe()             # Output: This is a vehicle.
  bike.start_engine()         # Output: The motorcycle's engine starts with a kick or an electric button.
  bike.stop_engine()          # Output: The motorcycle's engine stops when you turn off the key or press the kill switch.
  ```

# Exception Handling
Exception handling is a mechanism in Python used to handle runtime exceptions (errors) in a program without crashing it. It ensures that a program can respond to unexpected conditions gracefully instead of abruptly terminating. Python uses `try` (contains code that might throw an exception), `except` (catches and handles the exception), `else` (executes if no exceptions are raised in the `try` block), and `finally` (Always executes, whether an exception occurred or not) blocks to handle exceptions. 
```python
try:
    # Code that may raise an exception
    risky_operation()
except SpecificException as e:
    # Code to handle the exception
    print(f"An error occurred: {e}")
else:
    # Code that runs if no exception occurs
    print("Operation succeeded!")
finally:
    # Code that runs no matter what (optional)
    print("Cleaning up resources.")
```

__Common Exceptions:__
- __A) `ZeroDivisionError`:__ Dividing by zero.
- __B) `FileNotFoundError`:__ Trying to access a file that doesn't exist.
- __C) `ValueError`:__ Passing invalid values to a function.

## Creating Custom Exceptions
- You can create a custom exception in Python and name it anything you want. Custom exceptions are user-defined exceptions that can make your code more descriptive and easier to understand. To create a custom exception, you typically define a new class that inherits from Python's built-in `Exception` class.
  ```python
  class TimesUpError(Exception):
      """Custom exception to indicate that time is up."""
      pass

  # Using the custom exception
  def countdown_timer(seconds):
      if seconds <= 0:
          raise TimesUpError("Time's up!")
      else:
          print(f"{seconds} seconds remaining.")

  try:
      countdown_timer(0)
  except TimesUpError as e:
      print(e) # Output: Time's up!
  ```

# Module, Package & Library, Framework
- __A) Module:__ A module is a single file containing Python functions, classes and variables. It organizes code into reusable components.
  ```python
  # Here a file named `math_utils.py` with functions like `add(a, b)` and `multiply(a, b)` is a module
  import math_utils
  result = math_utils.add(2, 3)
  ```
- __B) Package:__ A package is a collection of modules organized in a directory with a special `__init__.py` file.
  ```python
  # Directory structure
  # my_package/
    # __init__.py
    # module1.py
    # module2.py

  from my_package import module1
  module1.function()
  ```
- __C) Library:__ A library is a collection of pre-written modules or packages that provide specific functionality to simplify coding tasks.
  ```python
  import numpy as np
  arr = np.array([1, 2, 3])
  ```
- __D) Framework:__ A framework is a structured foundation that provides tools, functions, and conventions to help developers build applications efficiently and systematically.
  ```python
  import tensorflow as tf

  # Define a simple sequential model
  model = tf.keras.Sequential([
      tf.keras.layers.Dense(128, activation='relu'),
      tf.keras.layers.Dense(10, activation='softmax')
  ])

  # Compile the model
  model.compile(optimizer='adam',
                loss='sparse_categorical_crossentropy',
                metrics=['accuracy'])

  # Display the model's architecture
  model.summary()
  ```
### Boilerplate
- In Python, boilerplate code refers to standard or repetitive code that is commonly included in Python scripts or projects to set up the basic structure. It is often used as a starting point to streamline development, ensuring that certain conventions or requirements are met. The `if __name__ == "__main__":` constructor is commonly used in Python scripts to ensure that code inside the main block won't run if the script is imported as a module.
  ```python
  from flask import Flask

  app = Flask(__name__)

  @app.route('/')
  def home():
      return "Welcome to Flask Boilerplate!"

  if __name__ == "__main__":
      app.run(debug=True)
  ```

# `os` Module
The `os` module provides functions for interacting with the operating system, such as file and directory management, environment variables, and process management.

### Common `os` Module Functions

| Function                | Description                                                                                              | Example                                                                          |
|-------------------------|----------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------|
| `os.getcwd()`           | Returns the current working directory.                                                                   | `os.getcwd()` → `'/home/user/projects'`                                          |
| `os.chdir(path)`        | Changes the current working directory to the specified path.                                             | `os.chdir('/home/user')` → Changes directory to `/home/user`.                    |
| `os.listdir(path)`      | Returns a list of files and directories in the specified directory.                                      | `os.listdir('.')` → `['file1.txt', 'folder1']`                                   |
| `os.mkdir(path)`        | Creates a new directory at the specified path.                                                           | `os.mkdir('new_folder')` → Creates a directory named `new_folder`.               |
| `os.makedirs(path)`     | Creates intermediate directories for the specified path if they don’t already exist.                     | `os.makedirs('folder/subfolder')` → Creates `folder` and `subfolder`.            |
| `os.stat(path)`         | Returns a `stat_result` object containing details like size, modification time, etc., of the given file. | `os.stat('file.txt')` → `os.stat_result(st_size=1024, st_mtime=1681234567, ...)` |
| `os.remove(path)`       | Deletes the specified file.                                                                              | `os.remove('file.txt')` → Deletes `file.txt`.                                    |
| `os.rmdir(path)`        | Removes an empty directory.                                                                              | `os.rmdir('empty_folder')` → Deletes `empty_folder`.                             |
| `os.path.exists(path)`  | Checks if the specified path exists.                                                                     | `os.path.exists('file.txt')` → `True` or `False`.                                |
| `os.rename(src, dst)`   | Renames a file or directory from `src` to `dst`.                                                         | `os.rename('old.txt', 'new.txt')` → Renames `old.txt` to `new.txt`.              |
| `os.path.getsize(path)` | Returns the size of the specified file in bytes.                                                         | `os.path.getsize('file.txt')` → `1024` (size in bytes).                          |

# File Handling 
File handling in Python allows for performing ___CRUD operations (Create, Read, Update, and Delete)___ on files. 

__CRUD Operations in File Handling:__
- __A) Create:__ Open or create a file for writing or appending (`w`, `x`, `a`).
- __B) Read:__ Read the content of a file (`r` or `r+`).
- __C) Update:__ Modify the content of a file (`w+`, `a+`).
- __D) Delete__

### File Modes in Python
- __A) Read Mode (`r`):__
  ```python
  with open('example.txt', 'r') as f:
      content = f.read()
      print(content)
  ```
- __B) Write Mode (`w`):__
  ```python
  with open('example.txt', 'w') as f:
      f.write("Writing to the file. Previous content is erased.")
  ```
- __C) Append Mode (`a`):__
  ```python
  with open('example.txt', 'a') as f:
      f.write("\nAppending this line to the file.")
  ```
- __D) Creat Mode (`x`):__
  ```python
  with open('newfile.txt', 'x') as f:
      f.write("This file is created and written exclusively.")
  ```
- __E) Binary Mode (`b`):__
  ```python
  # Writing binary data
  with open('example.bin', 'wb') as f:
      f.write(b"Binary data here")

  # Reading binary data
  with open('example.bin', 'rb') as f:
      content = f.read()
      print(content)
  ```
- __F) Read and Write Mode (`r+`):__
  ```python
  with open('example.txt', 'r+') as f:
      content = f.read()
      f.write("\nAdding this line after reading the content.")
  ```
- __G) Write and Read Mode (`w+`):__
  ```python
  with open('example.txt', 'w+') as f:
      f.write("This is new content. Previous content is erased.")
      f.seek(0)
      print(f.read())
  ```
- __H) Append and Read Mode (`a+`):__
  ```python
  with open('example.txt', 'a+') as f:
      f.write("\nThis line is appended.")
      f.seek(0)
      print(f.read())
  ```
| Mode | Description                                                                                        | Example                             |
|------|----------------------------------------------------------------------------------------------------|-------------------------------------|
| `r`  | Open a file for reading. File must exist.                                                          | `with open('file.txt', 'r') as f:`  |
| `w`  | Open a file for writing. Creates a new file if it doesn’t exist or truncates the existing file.    | `with open('file.txt', 'w') as f:`  |
| `a`  | Open a file for appending. Creates a new file if it doesn’t exist.                                 | `with open('file.txt', 'a') as f:`  |
| `x`  | Open a file for exclusive creation. Fails if the file already exists.                              | `with open('file.txt', 'x') as f:`  |
| `t`  | Open a file in text mode (default).                                                                | `with open('file.txt', 'rt') as f:` |
| `b`  | Open a file in binary mode.                                                                        | `with open('file.bin', 'rb') as f:` |
| `r+` | Open a file for reading and writing. File must exist.                                              | `with open('file.txt', 'r+') as f:` |
| `w+` | Open a file for writing and reading. Creates a new file if it doesn’t exist or truncates the file. | `with open('file.txt', 'w+') as f:` |
| `a+` | Open a file for appending and reading. Creates a new file if it doesn’t exist.                     | `with open('file.txt', 'a+') as f:` |

### `with` Statement
- The with statement ensures that files are properly closed after their operations, even in case of exceptions.
  ```python
  with open('example.txt', 'r') as f:
      data = f.read()
      print(data)  # File is automatically closed after the block.
  ```
__Best Practices:__
- Always use `with` statement to close the file automatically.
- Use `os.path.exists()` to check file existence and avoid errors.
- Use `try-except` to catch and manage errors.

# `glob` Module
The `glob` module is used in Python for file pattern matching. It utilizes wildcards to list files and directories that match a specified pattern.

__Wildcards:__
- __A) `*`:__ Matches zero or more characters in a filename or directory name.
- __B) `?`:__ Matches a single character in a filename or directory name.
- __C) `[]`:__ Matches any character inside the brackets.

### Common `glob` Module Functions

| Function              | Description                                                                                           | Example                                                     |
|-----------------------|-------------------------------------------------------------------------------------------------------|-------------------------------------------------------------|
| `glob.glob(pattern)`  | Returns a list of file paths that match the specified pattern.                                        | `glob.glob('*.txt')` → `['file1.txt', 'file2.txt']`         |
| `glob.iglob(pattern)` | Returns an iterator that yields file paths matching the specified pattern (useful for large results). | `list(glob.iglob('*.py'))` → `['script1.py', 'script2.py']` |

# `shutil` Module
The `shutil` module provides high-level operations for file copying, removal, and directory management. 

### Common `shutil` Module Functions

| Function               | Description                                                                             | Example                                                                                          |
|------------------------|-----------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|
| `shutil.copyfileobj()` | Copies the contents of one file-like object to another.                                 | `with open('src.txt', 'r') as src, open('dest.txt', 'w') as dest: shutil.copyfileobj(src, dest)` |
| `shutil.copy()`        | Copies a file to another location. Preserves the file's permissions but not metadata.   | `shutil.copy('src.txt', 'dest.txt')`                                                             |
| `shutil.copy2()`       | Copies a file to another location, preserving metadata (timestamps, permissions, etc.). | `shutil.copy2('src.txt', 'dest.txt')`                                                            |
| `shutil.copyfile()`    | Copies the content of a file to another file. Destination must be writable.             | `shutil.copyfile('src.txt', 'dest.txt')`                                                         |
| `shutil.move()`        | Moves a file or directory to another location.                                          | `shutil.move('src_folder', 'dest_folder')`                                                       |
| `shutil.copytree()`    | Recursively copies an entire directory tree to a new location.                          | `shutil.copytree('src_folder', 'dest_folder')`                                                   |
| `shutil.rmtree()`      | Recursively deletes a directory tree, including all files and subdirectories.           | `shutil.rmtree('folder_to_delete')`                                                              |

# `time` Module
The `time` module provides various time-related functions to handle time-related tasks such as measuring execution time or delaying execution.

### Common `time` Module Functions

| Function                | Description                                                                               | Example                                                                                |
|-------------------------|-------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| `time.time()`           | Returns the current time in seconds since the epoch (Unix timestamp).                     | `time.time()` → `1652201225.331`                                                       |
| `time.sleep(seconds)`   | Suspends execution for the given number of seconds.                                       | `time.sleep(2)` → Sleeps for 2 seconds                                                 |
| `time.ctime()`          | Converts a time expressed in seconds since the epoch to a string representing local time. | `time.ctime()` → `'Thu May 18 10:03:45 2023'`                                          |
| `time.gmtime()`         | Converts seconds since the epoch to a `struct_time` in UTC.                               | `time.gmtime(1652201225)` → `struct_time(tm_year=2023, tm_mon=5, ...)`                 |
| `time.localtime()`      | Converts seconds since the epoch to a `struct_time` in local time.                        | `time.localtime(1652201225)` → `struct_time(tm_year=2023, tm_mon=5, ...)`              |
| `time.strftime(format)` | Converts a `struct_time` or current time to a string based on the provided format.        | `time.strftime('%Y-%m-%d')` → `'2023-05-18'`                                           |
| `time.strptime(string)` | Parses a string into a `struct_time` based on the given format.                           | `time.strptime('2023-05-18', '%Y-%m-%d')` → `struct_time(tm_year=2023, tm_mon=5, ...)` |

# `datetime` Module
The `datetime` module provides classes for manipulating dates and times, like creating, formatting, and manipulating datetime objects.

### Common `datetime` Module Functions

| Function                    | Description                                                                                                      | Example                                                                 |
|-----------------------------|------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
| `datetime.now()`            | Returns the current local date and time as a `datetime` object.                                                  | `datetime.now()` → `2023-05-18 10:12:33.331`                            |
| `datetime.today()`          | Returns the current local date as a `datetime` object (similar to `datetime.now()` without time).                | `datetime.today()` → `2023-05-18 10:12:33.331`                          |
| `datetime.today().date()`   | Returns the current date (year, month, day) from the current `datetime` object.                                  | `datetime.today().date()` → `2023-05-18`                                |
| `datetime.today().time()`   | Returns the current time (hour, minute, second, microsecond) from the current `datetime` object.                 | `datetime.today().time()` → `10:12:33.331`                              |
| `datetime.strftime(format)` | Converts a `datetime` object to a string based on the given format.                                              | `datetime.now().strftime('%Y-%m-%d')` → `'2023-05-18'`                  |
| `datetime.strptime(string)` | Parses a string into a `datetime` object based on the given format.                                              | `datetime.strptime('2023-05-18', '%Y-%m-%d')` → `datetime(2023, 5, 18)` |
| `datetime.timedelta()`      | Represents a time duration (difference between two `datetime` objects).                                          | `datetime.timedelta(days=5)` → `datetime.timedelta(days=5)`             |
| `datetime.replace()`        | Returns a new `datetime` object with specific attributes (year, month, day, hour, minute, second, etc.) changed. | `datetime.now().replace(year=2025)` → `2025-05-18 10:12:33.331`         |

# `re` Module
The `re` module in Python provides support for working with regular expressions, which are patterns used to match sequences of characters in strings. It is widely used for string searching and manipulation.

### Common `re` Module Functions

| Function                        | Description                                                                                                                          | Example                                                                                                             |
|---------------------------------|--------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| `re.match(pattern, string)`     | Tries to match a pattern at the beginning of the string and returns a match object if a match is found, otherwise returns `None`.    | result = re.match(r'hello', 'hello world') → <re.Match object; span=(0, 5), match='hello'>                          |
| `re.search(pattern, string)`    | Searches for the first occurrence of the pattern anywhere in the string and returns a match object if found, otherwise returns None. | result = re.search(r'world', 'hello world') → <re.Match object; span=(6, 11), match='world'>                        |
| `re.findall(pattern, string)`   | Returns a list of all non-overlapping matches of the pattern in the string.                                                          | result = re.findall(r'\d+', 'There are 15 apples and 20 bananas.') → ['15', '20']                                   |
| `re.finditer(pattern, string)`  | Returns an iterator of match objects for all non-overlapping matches in the string.                                                  | result = re.finditer(r'\d+', 'There are 15 apples and 20 bananas.') → 15, 20                                        |
| `re.sub(pattern, repl, string)` | Replaces occurrences of the pattern in the string with the specified replacement.                                                    | result = re.sub(r'apples', 'oranges', 'There are 15 apples and 20 bananas.') → There are 15 oranges and 20 bananas. |
| `re.split(pattern, string)`     | Splits the string at each match of the pattern.                                                                                      | result = re.split(r'\s+', 'This is a test') → ['This', 'is', 'a', 'test']                                           |

### `re.compile(pattern, flags=0)`
- It compiles a regular expression pattern into a regex object, which can be reused for pattern matching.
  ```python
  import re

  pattern = re.compile(r'\d+')
  text = "There are 42 apples and 19 bananas."

  # Using the compiled pattern for multiple matches
  match = pattern.search(text)
  print(match.group())  # Output: 42

  all_matches = pattern.findall(text)
  print(all_matches)  # Output: ['42', '19']
  ```

__Flags:__
- __A) `re.IGNORECASE` or `re.I`:__ Used for case-insensitive matching.
  ```python
  import re

  text = "Hello World"
  result = re.search(r'hello', text, re.IGNORECASE)
  print(result)  # <re.Match object; span=(0, 5), match='Hello'>
  ```
- __B) `re.MULTILINE` or `re.M`:__ It allows `^` and `$` to match the beginning and end of each line.
  ```python
  import re

  text = """Hello World
  This is a test
  Another line"""
  result = re.findall(r'^This', text, re.MULTILINE)
  print(result)  # ['This']
  ```
- __C) `re.DOTALL` or `re.S`:__ It allows `.` to match newline characters.
  ```python
  import re

  text = """Hello World
  This is a test
  Another line"""
  result = re.search(r'Hello.*test', text, re.DOTALL)
  print(result.group())  # 'Hello World\nThis is a test'
  ```
- __D) `re.VERBOSE` or `re.X`:__ It allows you to write regular expressions that span multiple lines and include comments for better readability.
  ```python
  import re

  pattern = re.compile(r"""
      \d{3}     # Match three digits
      -         # Match a hyphen
      \d{2}     # Match two digits
      -         # Match another hyphen
      \d{4}     # Match four digits
  """, re.VERBOSE)

  text = "123-45-6789"
  result = pattern.match(text)
  print(result.group())  # '123-45-6789'
  ```

### Special Characters for Regular Expression Pattern

| Special Character | Description                                                             | Example                                                   |
|-------------------|-------------------------------------------------------------------------|-----------------------------------------------------------|
| `[]`              | Used to match any one of the characters inside the brackets.            | `[a-c]` matches `'a'`, `'b'`, or `'c'`.                   |
| `{m,n}`           | Matches between m and n repetitions of the preceding pattern.           | `a{2,4}` matches `'aa'`, `'aaa'`, or `'aaaa'`.            |
| `()`              | Groups patterns together. Captures the matched text for reference.      | `(ab)+` matches `'ab'`, `'abab'`.                         |
| `.`               | Matches any single character except newline.                            | `a.b` matches `'acb'`, `'a1b'`, but not `'ab'`.           |
| `+`               | Matches 1 or more repetitions of the preceding pattern.                 | `a+` matches `'a'`, `'aa'`, `'aaa'`.                      |
| `*`               | Matches 0 or more repetitions of the preceding pattern.                 | `a*` matches `''`, `'a'`, `'aa'`.                         |
| `?`               | Matches 0 or 1 repetition of the preceding pattern.                     | `colou?r` matches `'color'` and `'colour'`.               |
| `^`               | Matches the start of the string.                                        | `^hello` matches `'hello world'` but not `'world hello'`. |
| `$`               | Matches the end of the string.                                          | `world$` matches `'hello world'` but not `'world hello'`. |
| `\d`              | Matches any digit `[0-9]`.                                              | `\d+` matches `'123'`, `'42'`.                            |
| `\D`              | Matches any non-digit `[^0-9]`.                                         | `\D+` matches `'abc'`, `'hello'`.                         |
| `\w`              | Matches any alphanumeric character `[a-z, A-Z, 0-9, _]`.                | `\w+` matches `'word'`, `'variable1'`.                    |
| `\W`              | Matches any non-alphanumeric character `[^a-z, A-Z, 0-9, _]`.           | `\W+` matches `'!'`, `'#'`, `'@'`.                        |
| `\s`              | Matches any whitespace character `[\t\n\r\f\v]`.                        | `\s+` matches spaces, tabs, or newlines.                  |
| `\S`              | Matches any non-whitespace character.                                   | `\S+` matches `'word'`, `'1234'`.                         |
| `\b`              | Matches a word boundary (position between word and non-word character). | `\bword\b` matches `'word'` but not `'wording'`.          |
| `\B`              | Matches non-word boundary (position inside a word).                     | `\Bing` matches `'ringing'`, but not `'ing'`.             |

__Important Links:__
- https://pythontutor.com/
