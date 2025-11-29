# Files, Directories, and Paths in Python

This lesson covers:
- Handling **files** for reading and writing  
- Working with **directories and paths**  
- Using Python's **`os`** and **`pathlib`** modules  

---

## 1. Working with Files

Python allows you to **read from and write to files** using built-in functions.

### 1.1 Opening a File

```python
# Open a file in read mode
file = open("example.txt", "r")

# Open a file in write mode
file = open("example.txt", "w")

# Open a file in append mode
file = open("example.txt", "a")
```

- `"r"` → read  
- `"w"` → write (overwrites existing file)  
- `"a"` → append (adds to the file)  

---

### 1.2 Reading from a File

```python
with open("example.txt", "r") as file:
    content = file.read()
    print(content)
```

- `with` ensures the file is **automatically closed**  
- Other options:
  - `readline()` → reads one line at a time  
  - `readlines()` → reads all lines into a list  

---

### 1.3 Writing to a File

```python
with open("example.txt", "w") as file:
    file.write("Hello, Python!\n")
    file.write("Working with files is easy.")
```

- Writing **overwrites existing content**  
- Use `"a"` mode to **add content** instead  

---

## 2. Working with Directories

### 2.1 Using `os` Module

```python
import os

# Current working directory
print(os.getcwd())

# Create a new directory
os.mkdir("new_folder")

# List files and directories
print(os.listdir())

# Remove a directory
os.rmdir("new_folder")
```

---

### 2.2 Using `pathlib` Module

```python
from pathlib import Path

# Create a Path object
path = Path("example.txt")

# Check if file exists
print(path.exists())

# Get parent directory
print(path.parent)

# Join paths
new_path = path.parent / "new_file.txt"
print(new_path)
```

- `pathlib` provides **an object-oriented approach** to paths  
- Safer and more readable than `os.path`  

---

## 3. File Paths

- **Absolute path**: full path from root (e.g., `C:/Users/Name/Documents/file.txt`)  
- **Relative path**: path relative to current working directory (e.g., `file.txt` or `folder/file.txt`)  

```python
# Absolute path
abs_path = Path("/Users/username/Documents/example.txt")

# Relative path
rel_path = Path("example.txt")
```

---

## 4. Common File Operations

| Operation | Example |
|-----------|---------|
| Rename file | `os.rename("old.txt", "new.txt")` |
| Delete file | `os.remove("example.txt")` |
| Check if file | `Path("example.txt").is_file()` |
| Check if directory | `Path("folder").is_dir()` |

---

## 5. Reading/Writing CSV or JSON

### CSV Example

```python
import csv

with open("data.csv", "w", newline="") as file:
    writer = csv.writer(file)
    writer.writerow(["Name", "Age"])
    writer.writerow(["Alice", 25])
```

### JSON Example

```python
import json

data = {"name": "Alice", "age": 25}

with open("data.json", "w") as file:
    json.dump(data, file)
```

- Useful for **structured data storage**  

---

## 6. Key Takeaways

- Use **`open()`** or **`with open()`** to read/write files  
- `os` and `pathlib` help manage **directories and file paths**  
- Always **close files** or use `with` to avoid errors  
- File handling is essential for **data storage, configuration, and project management**  

Files, directories, and paths are **core Python skills** for managing data and organizing projects efficiently.
