
# Pandas Data Inspection

Pandas provides several methods and attributes to inspect a DataFrame. They help you preview records, understand the dataset structure, examine data types, calculate summary statistics, and identify the number of rows and columns.

## 1\. Official Documentation

| Method / Attribute | Documentation |
| --- | --- |
| `head()` | [DataFrame.head()](<https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.head.html>) |
| `tail()` | [DataFrame.tail()](<https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.tail.html>) |
| `sample()` | [DataFrame.sample()](<https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.sample.html>) |
| `info()` | [DataFrame.info()](<https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.info.html>) |
| `describe()` | [DataFrame.describe()](<https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.describe.html>) |
| `shape` | [DataFrame Reference](<https://pandas.pydata.org/docs/reference/frame.html>) |

## 2\. Quick Reference

| Method / Attribute | Purpose |
| --- | --- |
| `df.head()` | Displays the first 5 rows. |
| `df.tail()` | Displays the last 5 rows. |
| `df.sample()` | Displays randomly selected rows. |
| `df.info()` | Shows column names, data types, non-null counts, and memory usage. |
| `df.describe()` | Calculates summary statistics for numerical columns. |
| `df.shape` | Returns the number of rows and columns. |
| `df.shape[0]` | Returns the number of rows. |
| `df.shape[1]` | Returns the number of columns. |
| `df.size` | Returns the total number of values. |
| `df.columns` | Returns the names of all columns. |
| `df.dtypes` | Returns the data type of each column. |
| `len(df)` | Returns the number of rows. |

## 3\. Example DataFrame

The following examples use this DataFrame:

python

```python
import pandas as pd

df = pd.DataFrame({
    "name": ["John", "Mary", "David", "Anna", "Peter"],
    "age": [25, 30, 28, 35, 22],
    "salary": [4000, 5000, 4500, 6000, 3500]
})

print(df)
```

Output:

text

```text
    name  age  salary
0   John   25    4000
1   Mary   30    5000
2  David   28    4500
3   Anna   35    6000
4  Peter   22    3500
```

## 4\. Preview Data

### head()

Displays the first rows of a DataFrame.

python

```python
df.head()
```

Output:

text

```text
    name  age  salary
0   John   25    4000
1   Mary   30    5000
2  David   28    4500
3   Anna   35    6000
4  Peter   22    3500
```

Display a specific number of rows:

python

```python
df.head(3)
```

Output:

text

```text
    name  age  salary
0   John   25    4000
1   Mary   30    5000
2  David   28    4500
```

### tail()

Displays the last rows of a DataFrame.

python

```python
df.tail()
```

Output:

text

```text
    name  age  salary
0   John   25    4000
1   Mary   30    5000
2  David   28    4500
3   Anna   35    6000
4  Peter   22    3500
```

Display the last two rows:

python

```python
df.tail(2)
```

Output:

text

```text
    name  age  salary
3   Anna   35    6000
4  Peter   22    3500
```

### sample()

Displays randomly selected rows from a DataFrame.

python

```python
df.sample(2)
```

Example output:

text

```text
    name  age  salary
1   Mary   30    5000
4  Peter   22    3500
```

**Note:** The selected rows may change each time you execute the command.

To get reproducible random results, use `random_state`:

python

```python
df.sample(2, random_state=42)
```

## 5\. Examine DataFrame Information

### info()

Displays a summary of the DataFrame, including column names, data types, non-null counts, and memory usage.

python

```python
df.info()
```

Output:

text

```text
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 5 entries, 0 to 4
Data columns (total 3 columns):
 #   Column  Non-Null Count  Dtype
---  ------  --------------  -----
 0   name    5 non-null      object
 1   age     5 non-null      int64
 2   salary  5 non-null      int64
dtypes: int64(2), object(1)
```

**Understanding the output:**

| Output | Meaning |
| --- | --- |
| `RangeIndex: 5 entries` | The DataFrame contains 5 rows. |
| `Data columns (total 3 columns)` | The DataFrame contains 3 columns. |
| `5 non-null` | The column contains 5 non-missing values. |
| `int64` | The column contains integers. |
| `object` | The column contains objects, often strings. |

### describe()

Calculates descriptive statistics for numerical columns.

python

```python
df.describe()
```

Output:

text

```text
             age       salary
count   5.000000      5.000000
mean   28.000000   4600.000000
std     5.099020    962.910050
min    22.000000   3500.000000
25%    25.000000   4000.000000
50%    28.000000   4500.000000
75%    30.000000   5000.000000
max    35.000000   6000.000000
```

**Understanding the output:**

| Statistic | Meaning |
| --- | --- |
| `count` | Number of non-missing values. |
| `mean` | Average value. |
| `std` | Standard deviation. |
| `min` | Smallest value. |
| `25%` | First quartile. |
| `50%` | Median. |
| `75%` | Third quartile. |
| `max` | Largest value. |

To include categorical columns:

python

```python
df.describe(include="all")
```

## 6\. DataFrame Size and Dimensions

Pandas provides several attributes and functions to understand the size and structure of a DataFrame.

### Difference Between These Attributes

| Attribute / Function | Meaning | Example |
| --- | --- | --- |
| `df.shape` | Number of rows and columns. | `(100, 5)` |
| `df.shape[0]` | Number of rows. | `100` |
| `df.shape[1]` | Number of columns. | `5` |
| `df.size` | Total number of values (rows × columns). | `500` |
| `df.columns` | Names of all columns. | `name, age, salary` |
| `len(df)` | Number of rows. | `100` |

### shape

Returns a tuple containing the number of rows and columns.

python

```python
df.shape
```

Output:

text

```text
(5, 3)
```

The result means:

- 5 rows
- 3 columns

### Get the Number of Rows

Use `df.shape[0]` to get the number of rows.

python

```python
df.shape[0]
```

Output:

text

```text
5
```

You can also use:

python

```python
len(df)
```

Output:

text

```text
5
```

Both return the number of rows.

### Get the Number of Columns

Use `df.shape[1]` to get the number of columns.

python

```python
df.shape[1]
```

Output:

text

```text
3
```

### size

Returns the total number of values in the DataFrame.

python

```python
df.size
```

Output:

text

```text
15
```

Calculation:

text

```text
5 rows × 3 columns = 15 values
```

### columns

Returns the names of all columns.

python

```python
df.columns
```

Output:

text

```text
Index(['name', 'age', 'salary'], dtype='object')
```

### dtypes

Returns the data type of each column.

python

```python
df.dtypes
```

Output:

text

```text
name      object
age        int64
salary     int64
dtype: object
```

## 7\. Practical Example: Inspect a Dataset

You can combine these methods to quickly understand a newly imported dataset.

python

```python
import pandas as pd

df = pd.read_csv("data.csv")

# Preview the dataset
print(df.head())

# Examine the structure
df.info()

# Calculate summary statistics
print(df.describe())

# Get the number of rows and columns
print("Rows:", df.shape[0])
print("Columns:", df.shape[1])

# Get the total number of values
print("Total values:", df.size)

# Display column names
print("Column names:", df.columns.tolist())

# Display data types
print(df.dtypes)
```

Example output:

text

```text
Rows: 100
Columns: 5
Total values: 500

Column names:
['name', 'age', 'salary', 'department', 'city']
```

## 8\. Important Notes

- `head()` and `tail()` display 5 rows by default.
- `sample()` selects random rows.
- `info()` is useful for checking missing values and data types.
- `describe()` provides statistical summaries.
- `shape` returns a tuple in the order `(rows, columns)`.
- `shape[0]` returns the number of rows.
- `shape[1]` returns the number of columns.
- `size` returns the total number of values, not the number of rows.
- `columns` returns column names.
- `df.shape`, `df.size`, `df.columns`, and `df.dtypes` are attributes, not methods. Do not add parentheses.
- `len(df)` is another way to get the number of rows.

## Additional Resources

- [Pandas DataFrame Reference](<https://pandas.pydata.org/docs/reference/frame.html>)
- [Pandas Getting Started Guide](<https://pandas.pydata.org/docs/getting_started/intro_tutorials/index.html>)
- [Pandas User Guide](<https://pandas.pydata.org/docs/user_guide/index.html>)

