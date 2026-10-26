# JSON File Example

## 1. What Is a JSON File?

**JSON (JavaScript Object Notation)** is a text-based format used to store and exchange structured data. JSON supports objects, arrays, strings, numbers, Booleans, and null values.

File extension: .json
- [Pandas read_json()](https://pandas.pydata.org/docs/reference/api/pandas.read_json.html)
- [Python JSON Module](https://docs.python.org/3/library/json.html)

## 2. Example of a JSON File

Create a file named employees.json:
```
json
[
  {
    "id": 1,
    "name": "Alice",
    "department": "IT",
    "salary": 65000
  },
  {
    "id": 2,
    "name": "Bob",
    "department": "Finance",
    "salary": 70000
  },
  {
    "id": 3,
    "name": "Charlie",
    "department": "HR",
    "salary": 60000
  }
]
```
view json 
```
JSON Array
│
├── Object 1
│   ├── id: 1
│   ├── name: "Alice"
│   ├── department: "IT"
│   └── salary: 65000
│
├── Object 2
│   ├── id: 2
│   ├── name: "Bob"
│   ├── department: "Finance"
│   └── salary: 70000
│
└── Object 3
    ├── id: 3
    ├── name: "Charlie"
    ├── department: "HR"
    └── salary: 60000
```
This JSON file contains an array of three employee objects.

## 3. Read a JSON File Using Pandas

```
import pandas as pd

df = pd.read_json("employees.json")

print(df)
```

Output:

| id | name | department | salary |
|---:|---|---|---:|
| 1 | Alice | IT | 65000 |
| 2 | Bob | Finance | 70000 |
| 3 | Charlie | HR | 60000 |

Pandas converts the JSON records into a DataFrame.

## 4. Read JSON Directly from a String

```
import pandas as pd
from io import StringIO

json_data = """
[
  {"name": "Alice", "age": 25},
  {"name": "Bob", "age": 30}
]
"""


df = pd.read_json(StringIO(json_data))

print(df)
```

## 5. Common JSON Structures

| Structure | Example | Description |
|---|---|---|
| Object | {"name": "Alice", "age": 25} | Stores key-value pairs. |
| Array | [10, 20, 30] | Stores an ordered list of values. |
| String | "Alice" | Stores text. |
| Number | 25 | Stores a number. |
| Boolean | true or false | Stores a logical value. |
| Null | null | Represents an empty or missing value. |

## 6. JSON Import Method

| Method | Description | Example |
|---|---|---|
| pd.read_json() | Reads JSON data into a DataFrame when its structure is supported. | pd.read_json("employees.json") |
| json.load() | Loads JSON from an open file into Python objects. | json.load(file) |
| json.loads() | Parses a JSON string into Python objects. | json.loads(json_string) |

## Official Documentation


