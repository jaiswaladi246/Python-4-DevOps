# DAY-9 | JSON (JavaScript Object Notation) manipulation in Python

JSON (JavaScript Object Notation) manipulation in Python involves working with JSON data, which is a lightweight data-interchange format. It is easy for humans to read and write and easy for machines to parse and generate.

In Python, you can manipulate JSON data using the `json` module, which provides methods for encoding and decoding JSON data. Here are some common JSON manipulation tasks in Python:

1. **Loading JSON Data:**
   - The `json.loads()` function is used to parse a JSON string and convert it into a Python data structure (usually a dictionary or a list).

   ```python
   import json

   json_string = '{"name": "John Doe", "age": 30, "city": "New York"}'
   data = json.loads(json_string)
   print(data)
   ```

2. **Reading JSON from a File:**
   - The `json.load()` function is used to read JSON data from a file and convert it into a Python data structure.

   ```python
   import json

   with open('data.json', 'r') as file:
       data = json.load(file)
   print(data)
   ```

3. **Dumping JSON Data:**
   - The `json.dumps()` function is used to convert a Python object (usually a dictionary or a list) into a JSON formatted string.

   ```python
   import json

   data = {'name': 'John Doe', 'age': 30, 'city': 'New York'}
   json_string = json.dumps(data)
   print(json_string)
   ```

4. **Writing JSON to a File:**
   - The `json.dump()` function is used to write JSON data to a file.

   ```python
   import json

   data = {'name': 'John Doe', 'age': 30, 'city': 'New York'}
   with open('output.json', 'w') as file:
       json.dump(data, file)
   ```

5. **Accessing JSON Data:**
   - Once you've loaded JSON data, you can access individual elements using dictionary or list indexing.

   ```python
   import json

   json_string = '{"name": "John Doe", "age": 30, "city": "New York"}'
   data = json.loads(json_string)
   print(data['name'])  # Output: John Doe
   print(data['age'])   # Output: 30
   ```

6. **Modifying JSON Data:**
   - After loading JSON data, you can modify it like any other Python data structure.

   ```python
   import json

   json_string = '{"name": "John Doe", "age": 30, "city": "New York"}'
   data = json.loads(json_string)
   
   data['age'] = 31  # Modify the age
   data['city'] = 'San Francisco'  # Modify the city
   
   # Convert the modified data back to JSON string
   modified_json_string = json.dumps(data)
   ```

## More detailed Examples

#### Examples of how to parse and manipulate JSON data in Python, along with explanations and sample outputs.

### Example 1: Parsing JSON Data

```python
import json

# JSON data as a string
json_data = '{"name": "John Doe", "age": 30, "city": "New York"}'

# Parse JSON string to a Python dictionary
data = json.loads(json_data)

# Accessing elements in the dictionary
print(data['name'])  # Output: John Doe
print(data['age'])   # Output: 30
```

**Explanation**: In this example, we have a JSON string `json_data` representing a person's information. We use `json.loads()` to parse this string into a Python dictionary called `data`. We then access individual elements within the dictionary using keys.

**Output**:
```
John Doe
30
```

### Example 2: Modifying JSON Data

```python
import json

# JSON data as a string
json_data = '{"name": "John Doe", "age": 30, "city": "New York"}'

# Parse JSON string to a Python dictionary
data = json.loads(json_data)

# Modify data
data['age'] = 31
data['city'] = 'San Francisco'

# Convert back to JSON
updated_json_data = json.dumps(data)

print(updated_json_data)  # Output: {"name": "John Doe", "age": 31, "city": "San Francisco"}
```

**Explanation**: In this example, we first parse a JSON string into a dictionary. Then, we modify the `age` and `city` values. After the modifications, we convert the updated dictionary back to a JSON string using `json.dumps()`.

**Output**:
```
{"name": "John Doe", "age": 31, "city": "San Francisco"}
```

### Example 3: Adding a New Key-Value Pair

```python
import json

# JSON data as a string
json_data = '{"name": "John Doe", "age": 30, "city": "New York"}'

# Parse JSON string to a Python dictionary
data = json.loads(json_data)

# Add a new key-value pair
data['occupation'] = 'Engineer'

# Convert back to JSON
updated_json_data = json.dumps(data)

print(updated_json_data)
# Output: {"name": "John Doe", "age": 30, "city": "New York", "occupation": "Engineer"}
```

**Explanation**: Here, we parse a JSON string into a dictionary, then add a new key-value pair (`'occupation': 'Engineer'`). We then convert the updated dictionary back to a JSON string.

**Output**:
```
{"name": "John Doe", "age": 30, "city": "New York", "occupation": "Engineer"}
```

### Example 4: Removing a Key-Value Pair

```python
import json

# JSON data as a string
json_data = '{"name": "John Doe", "age": 30, "city": "New York"}'

# Parse JSON string to a Python dictionary
data = json.loads(json_data)

# Remove a key-value pair
del data['age']

# Convert back to JSON
updated_json_data = json.dumps(data)

print(updated_json_data)  # Output: {"name": "John Doe", "city": "New York"}
```

**Explanation**: In this example, we parse a JSON string into a dictionary and then remove the key `'age'`. We then convert the modified dictionary back to a JSON string.

**Output**:
```
{"name": "John Doe", "city": "New York"}
```

### Example 5: Working with Nested JSON

```python
import json

# JSON data as a string with nested structure
json_data = '{"person": {"name": "John Doe", "age": 30, "city": "New York"}}'

# Parse JSON string to a Python dictionary
data = json.loads(json_data)

# Accessing nested elements
print(data['person']['name'])  # Output: John Doe
print(data['person']['age'])   # Output: 30
```

**Explanation**: Here, we have a JSON string with a nested structure. We parse it into a dictionary and then access elements within the nested structure using multiple keys.

**Output**:
```
John Doe
30
```

### Example 6: Handling JSON Arrays

```python
import json

# JSON data as a string with an array
json_data = '{"fruits": ["apple", "banana", "cherry"]}'

# Parse JSON string to a Python dictionary
data = json.loads(json_data)

# Accessing elements in the array
print(data['fruits'][0])  # Output: apple
print(data['fruits'][2])  # Output: cherry
```

**Explanation**: In this example, we have a JSON string with an array of fruits. We parse it into a dictionary and then access elements in the array using indices.

**Output**:
```
apple
cherry
```

### Example 7: Working with JSON Objects in a List

```python
import json

# JSON data as a string with a list of objects
json_data = '[{"name": "John Doe", "age": 30}, {"name": "Jane Doe", "age": 25}]'

# Parse JSON string to a Python list of dictionaries
data = json.loads(json_data)

# Accessing elements in the list of objects
print(data[0]['name'])  # Output: John Doe
print(data[1]['age'])   # Output: 25
```

**Explanation**: Here, we have a JSON string with a list of objects representing people. We parse it into a list of dictionaries and then access elements within each dictionary.

**Output**:
```
John Doe
25
```

### Example 8: Handling JSON with Dates

```python
import json
from datetime import datetime

# Python dictionary with a date
data = {'date': datetime(2023, 11, 1).isoformat()}

# Convert to JSON
json_data = json.dumps(data)

print(json_data)  # Output: {"date": "2023-11-01T00:00:00"}
```

**Explanation**: In this example, we have a Python dictionary with a date (represented as a `datetime` object). We convert it to a JSON string using `json.dumps()`.

**Output**:
```
{"date": "2023-11-01T00:00:00"}
```

### Example 9: Error Handling for Invalid JSON

```python
import json

# Invalid JSON data
invalid_json = '{"name": "John Doe", "age": 30, "city": "New York"'

try:
    data = json.loads(invalid_json)
    print(data)
except json.JSONDecodeError as e:
    print(f"Error: {e}")
```

**Explanation**: This example demonstrates error handling for cases where the provided string is not valid JSON. The `json.loads()` function can raise a `JSONDecodeError`, which we catch and print.

**Output**:
```
Error: Expecting ',' delimiter: line 1 column 35 (char 34)
```



### Example 10: Reading and Writing from/to JSON Files

```python
import json

# Writing to a JSON file
data_to_write = {'name': 'John Doe', 'age': 30, 'city': 'New York'}

with open('output.json', 'w') as file:
    json.dump(data_to_write, file)

# Reading from a JSON file
with open('output.json', 'r') as file:
    data_read = json.load(file)

print(data_read)  # Output: {'name': 'John Doe', 'age': 30, 'city': 'New York'}
```

**Explanation**: In this example, we first write a Python dictionary to a JSON file using `json.dump()`. Then, we read the contents of the JSON file back into a Python dictionary using `json.load()`.

**Output**: None (file created) / `{'name': 'John Doe', 'age': 30, 'city': 'New York'}` (printed content)

These examples cover a range of scenarios for parsing and manipulating JSON data in Python. They demonstrate common operations like reading from files, handling nested structures, and working with both dictionaries and lists in JSON format.
