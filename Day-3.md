# DAY-3 | File handling in Python

Handling files and directories is a common task in programming. Python provides a rich set of modules in its standard library to work with files and directories. 

### Working with Files

#### 1. Opening and Closing Files

To work with a file in Python, you first need to open it. You can open a file using the built-in `open()` function. It takes two arguments - the file path and the mode in which you want to open the file (read, write, append, etc.).

```python
# Opening a file in read mode
file = open('myfile.txt', 'r')

# Opening a file in write mode
file = open('myfile.txt', 'w')

# Opening a file in append mode
file = open('myfile.txt', 'a')

# Always close the file after you're done with it
file.close()
```

#### 2. Reading from Files

After opening a file in read mode, you can read its contents using methods like `read()`, `readline()`, or `readlines()`.

```python
# Reading the entire file
content = file.read()

# Reading one line at a time
line = file.readline()

# Reading all lines into a list
lines = file.readlines()
```

#### 3. Writing to Files

After opening a file in write mode, you can write to it using the `write()` method.

```python
file.write("Hello, World!\n")
```

#### 4. Appending to Files

Opening a file in append mode allows you to add content to the end of the file.

```python
file = open('myfile.txt', 'a')
file.write("New content\n")
```

### Working with Directories

#### 1. Creating Directories

You can use the `os` module to create directories.

```python
import os

# Create a directory
os.mkdir('mydir')
```

#### 2. Listing Files and Directories

The `os` module also allows you to list the contents of a directory.

```python
import os

# List all files and directories in the current directory
contents = os.listdir('.')
```

#### 3. Checking if a File or Directory Exists

You can use the `os.path` module to check if a file or directory exists.

```python
import os.path

# Check if a file exists
os.path.exists('myfile.txt')

# Check if a directory exists
os.path.exists('mydir')
```

#### 4. Deleting Files and Directories

To delete files, you can use `os.remove()` and to delete directories, you can use `os.rmdir()`.

```python
import os

# Delete a file
os.remove('myfile.txt')

# Delete an empty directory
os.rmdir('mydir')
```

#### 5. Recursive Directory Deletion

To delete a directory and its contents recursively, you can use the `shutil.rmtree()` function.

```python
import shutil

# Recursively delete a directory
shutil.rmtree('mydir')
```

These are the basics of working with files and directories in Python. Remember to always handle files carefully, and make sure to close them after you're done to free up system resources. Additionally, when working with directories, be cautious about deleting files, as it's a permanent action.
