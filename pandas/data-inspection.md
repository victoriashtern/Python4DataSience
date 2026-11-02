
# Pandas Data Inspection – Methods and Attributes

Data inspection is an important step in data analysis. Pandas provides several methods and attributes for examining a DataFrame, understanding its structure, checking missing values, and summarizing its contents.

## 1\. Data Inspection Methods and Attributes

| Method / Attribute | Type | Purpose |
| --- | --- | --- |
| df.head() | Method | Displays the first five rows by default. |
| df.tail() | Method | Displays the last five rows by default. |
| df.sample() | Method | Returns a random sample of rows. |
| df.info() | Method | Displays column names, data types, non-null counts, and memory usage. |
| df.describe() | Method | Generates descriptive statistics for numerical columns by default. |
| df.shape | Attribute | Returns the number of rows and columns. |
| df.size | Attribute | Returns the total number of elements. |
| df.ndim | Attribute | Returns the number of dimensions. |
| df.columns | Attribute | Returns the column names. |
| df.index | Attribute | Returns the row index. |
| df.dtypes | Attribute | Returns the data type of each column. |
| df.empty | Attribute | Checks whether the DataFrame is empty. |
| df.memory_usage() | Method | Returns memory usage for each column. |

## 2\. Previewing Data

### 2.1. head()

Displays the first five rows of a DataFrame by default.

```
df.head()
```

To display a specific number of rows:

```
df.head(10)
```

### 2.2. tail()

Displays the last five rows of a DataFrame by default.
```
df.tail()
```

To display the last ten rows:

```
df.tail(10)
```

### 2.3. sample()

Returns a random sample of rows from a DataFrame.

```
df.sample()
```

To return five random rows:

```
df.sample(5)
```

To make the random selection reproducible:

```
df.sample(5, random_state=42)
```

## 3\. Examining DataFrame Information

### 3.1. info()

Displays a summary of the DataFrame, including column names, data types, non-null counts, and memory usage.

```
df.info()
```

Common parameters:

| Parameter | Description |
| --- | --- |
| verbose=True | Displays detailed information for all columns. |
| memory_usage="deep" | Estimates memory usage more accurately, including object values. |
| show_counts=True | Displays the number of non-null values in each column. |

Example:

```
df.info(
    verbose=True,
    memory_usage="deep",
    show_counts=True
)
```

### Understanding the Output

| Output | Meaning |
| --- | --- |
| RangeIndex: 12624 entries | The DataFrame contains 12,624 rows. |
| Data columns (total 27 columns) | The DataFrame contains 27 columns. |
| 12624 non-null | The column contains 12,624 non-missing values. |
| 90 non-null | The column contains 90 non-missing values. |
| float64 | Floating-point numerical data. |
| int64 | Integer numerical data. |
| object | Objects, often strings or mixed values. |
| memory usage: 12.9 MB | Estimated DataFrame memory usage. |

## 4\. Descriptive Statistics

### 4.1. describe()

Generates descriptive statistics for numerical columns by default.

```
df.describe()
```

Common statistics include:

| Statistic | Meaning |
| --- | --- |
| count | Number of non-missing values. |
| mean | Average value. |
| std | Standard deviation. |
| min | Minimum value. |
| 25% | First quartile. |
| 50% | Median. |
| 75% | Third quartile. |
| max | Maximum value. |

To include all columns:

```
df.describe(include="all")
```

To summarize categorical columns:

```
df.describe(include=["object"])
```

## 5\. Examining DataFrame Dimensions

### 5.1. shape

Returns the number of rows and columns as a tuple.
```
df.shape
```

Example output:

text
(12624, 27)


Access the dimensions separately:

```
rows = df.shape[0]
columns = df.shape[1]

print("Rows:", rows)
print("Columns:", columns)
```

### 5.2. size

Returns the total number of elements in the DataFrame.

```
df.size
```

Calculation:

```
total_elements = df.shape[0] * df.shape[1]
```

For a DataFrame with 12,624 rows and 27 columns:

text
12624 × 27 = 340848


### 5.3. ndim

Returns the number of dimensions.

```
df.ndim
```

A standard pandas DataFrame has two dimensions.

## 6\. Examining Columns and Indexes

### 6.1. columns

Returns the names of all DataFrame columns.

```
df.columns
```

Convert column names into a list:

```
df.columns.tolist()
```

### 6.2. index

Returns the row index.

```
df.index
```

### 6.3. dtypes

Returns the data type of each column.

```
df.dtypes
```

### 6.4. empty

Checks whether the DataFrame is empty.

```
df.empty
```

Returns True if the DataFrame has no rows or columns.

## 7\. Checking Memory Usage

### 7.1. memory\_usage()

Returns the memory usage of each column.

```
df.memory_usage()
```

For a more detailed estimate:

```
df.memory_usage(deep=True)
```

Calculate the total memory usage:

```
df.memory_usage(deep=True).sum()
```

## 8\. Quick Reference

| Task | Method / Attribute | Example |
| --- | --- | --- |
| Preview first rows | head() | df.head() |
| Preview last rows | tail() | df.tail() |
| Random sample | sample() | df.sample(5) |
| DataFrame information | info() | df.info() |
| Descriptive statistics | describe() | df.describe() |
| Number of rows and columns | shape | df.shape |
| Total number of elements | size | df.size |
| Number of dimensions | ndim | df.ndim |
| Column names | columns | df.columns |
| Row index | index | df.index |
| Column data types | dtypes | df.dtypes |
| Check empty DataFrame | empty | df.empty |
| Column memory usage | memory_usage() | df.memory_usage() |

## 9\. Recommended Data Inspection Workflow

A useful starting workflow when importing a new dataset is:

```
import pandas as pd

# Import data
df = pd.read_csv("data.csv")

# Preview the dataset
print(df.head())

# Examine the last rows
print(df.tail())

# Check the DataFrame dimensions
print("Shape:", df.shape)

# Check total elements
print("Size:", df.size)

# Examine column names and data types
print(df.dtypes)

# Inspect missing values and memory usage
df.info(show_counts=True, memory_usage="deep")

# Generate descriptive statistics
print(df.describe())

# Examine random records
print(df.sample(5, random_state=42))
```

## 10\. Important Notes

- Methods use parentheses, such as df.head() and df.info().
- Attributes do not use parentheses, such as df.shape, df.size, and df.columns.
- head() and tail() return five rows by default.
- sample() selects random rows; use random_state for reproducible results.
- describe() summarizes numerical columns by default.
- info() is particularly useful for identifying missing values and checking data types.
- shape returns rows and columns, whereas size returns the total number of elements.


