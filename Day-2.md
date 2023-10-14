# Day-2 | Python syntax, data types, and variables

## Python Syntax:

Python is known for its clean and readable syntax. Here are some fundamental syntax rules:

1. **Statements and Indentation**:
   - Python uses indentation (whitespace) to define blocks of code, rather than curly braces `{}`. This is a unique feature of Python and helps in maintaining a clean and consistent code structure.

   Example:

   ```python
   if condition:
       # This block is indented, it belongs to the if statement
       print("This is indented")
   else:
       print("This is also indented")
   ```

2. **Comments**:
   - Comments start with a `#` character and are ignored by the Python interpreter. They are used to add explanations or notes within the code.

   Example:

   ```python
   # This is a comment
   ```

3. **Variables and Identifiers**:
   - Variables are used to store data. In Python, you can assign a value to a variable using `=`. Identifiers are names given to variables, functions, classes, etc.

   Example:

   ```python
   # Variable assignment
   x = 10
   name = "John"

   # Identifiers
   my_variable = 5
   ```

4. **Data Types**:
   - Python has several built-in data types, including integers, floats, strings, booleans, lists, tuples, dictionaries, etc. We'll discuss them in more detail below.

## Data Types:

### 1. Numeric Types:
   - **int**: Integer numbers (e.g., -5, 0, 100)
   - **float**: Floating-point numbers (e.g., 3.14, -0.5)

   Examples:

   ```python
   num_int = 42
   num_float = 3.14
   ```

### 2. String:
   - A sequence of characters enclosed in single (' '), double (" "), or triple (''' ''' or """ """) quotes.

   Examples:

   ```python
   name = "Alice"
   message = 'Hello, world!'
   ```

### 3. Boolean:
   - Represents truth values `True` or `False`.

   Examples:

   ```python
   is_valid = True
   has_permission = False
   ```

### 4. List:
   - Ordered collection of items, which can be of different types.

   Example:

   ```python
   my_list = [1, 2, 3, "hello", True]
   ```

### 5. Tuple:
   - Similar to lists but immutable (cannot be changed after creation).

   Example:

   ```python
   my_tuple = (1, 2, 3, "world")
   ```

### 6. Dictionary:
   - Collection of key-value pairs.

   Example:

   ```python
   my_dict = {'name': 'John', 'age': 30, 'city': 'New York'}
   ```

### 7. Set:
   - Unordered collection of unique items.

   Example:

   ```python
   my_set = {1, 2, 3, 4, 4, 4}  # Only contains 1, 2, 3, 4
   ```

## Examples:

Let's combine these concepts in some examples:

### Example 1: Variables and Basic Operations

```python
# Variables and basic operations
x = 5
y = 3

# Arithmetic operations
sum_result = x + y
difference_result = x - y
product_result = x * y
division_result = x / y

print(sum_result, difference_result, product_result, division_result)
```



### Lists:

#### Example 1 - Creating and Manipulating Lists:

```python
# Creating a list
my_list = [1, 2, 3, 4, 5]

# Accessing elements
print("First element:", my_list[0])
print("Last element:", my_list[-1])

# Modifying elements
my_list[2] = 10
print("Modified list:", my_list)

# Appending and removing elements
my_list.append(6)
my_list.remove(4)
print("Updated list:", my_list)
```

### Tuples:

#### Example 2 - Creating and Accessing Tuples:

```python
# Creating a tuple
my_tuple = (1, 2, 3, 4, 5)

# Accessing elements
print("First element:", my_tuple[0])
print("Last element:", my_tuple[-1])
```

### Dictionaries:

#### Example 3 - Creating and Manipulating Dictionaries:

```python
# Creating a dictionary
my_dict = {'name': 'John', 'age': 30, 'city': 'New York'}

# Accessing values
print("Name:", my_dict['name'])
print("Age:", my_dict['age'])

# Adding a new key-value pair
my_dict['email'] = 'john@example.com'
print("Updated dictionary:", my_dict)

# Iterating through keys and values
for key, value in my_dict.items():
    print(f"{key}: {value}")
```

### Sets:

#### Example 4 - Creating and Operating on Sets:

```python
# Creating a set
my_set = {1, 2, 3, 4, 4, 4}

# Adding and removing elements
my_set.add(5)
my_set.remove(2)
print("Updated set:", my_set)
```
### Sample Program for all data types

```python
# Integer
integer_var = 42
print("Integer Variable:", integer_var)

# Float
float_var = 3.14
print("Float Variable:", float_var)

# String
string_var = "Hello, World!"
print("String Variable:", string_var)

# List
list_var = [1, 2, 3, 4, 5]
print("List Variable:", list_var)

# Tuple
tuple_var = (10, 20, 30, 40, 50)
print("Tuple Variable:", tuple_var)

# Dictionary
dict_var = {'a': 1, 'b': 2, 'c': 3}
print("Dictionary Variable:", dict_var)

# Set
set_var = {1, 2, 3, 4, 5}
print("Set Variable:", set_var)

# Basic tasks

# Integer and Float operations
result = integer_var + float_var
print("Integer + Float:", result)

# String concatenation
new_string = string_var + " Have a nice day!"
print("Concatenated String:", new_string)

# List manipulation
list_var.append(6)
list_var.remove(2)
print("Modified List:", list_var)



# Dictionary operations
dict_var['d'] = 4
del dict_var['a']
print("Modified Dictionary:", dict_var)

# Set operations
set_var.add(6)
set_var.remove(3)
print("Modified Set:", set_var)
```
