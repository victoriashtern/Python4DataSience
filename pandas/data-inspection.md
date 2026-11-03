# Pandas Data Inspection – Methods and Attributes

Data inspection is an important step in data analysis. Pandas provides several methods and attributes for examining a DataFrame, understanding its structure, checking missing values, working with columns, and summarizing its contents.

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
| df.axes | Attribute | Returns the row and column axis labels. |
| df.values | Attribute | Returns the underlying data as a NumPy array. |
| df.memory_usage() | Method | Returns memory usage for each column. |
| df.count() | Method | Counts non-missing values in each column. |
| df.nunique() | Method | Counts unique values in each column. |
| df.isna() | Method | Identifies missing values. |
| df.notna() | Method | Identifies non-missing values. |
| df.duplicated() | Method | Identifies duplicate rows. |
| df.keys() | Method | Returns the column labels. |
| df.select_dtypes() | Method | Selects columns based on data types. |
| df.filter() | Method | Filters rows or columns by labels. |

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

text
12624 × 27 = 340848


### 5.3. ndim

Returns the number of dimensions.

```
df.ndim
```

A standard Pandas DataFrame has two dimensions.

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

Count the number of columns:

```
len(df.columns)
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

### 6.5. axes

Returns the row and column axis labels.

```
df.axes
```

### 6.6. values

Returns the underlying DataFrame data as a NumPy array.

```
df.values
```

### 6.7. keys()

Returns the column labels of the DataFrame.

```
df.keys()
```

## 7\. Working with Columns

Pandas provides several methods and techniques for selecting, renaming, reordering, adding, removing, and examining DataFrame columns.

### 7.1. Select One Column

Selects a single column and returns a Series.

```
df["Name"]
```

### 7.2. Select Multiple Columns

Selects multiple columns and returns a DataFrame.

```
df[["Name", "Age", "Salary"]]
```

### 7.3. Select Columns Using a List

You can store column names in a Python list and use that list to select columns.

```
columns = ["Frequency", "Percentage"]
```
new_df = df[columns]


The resulting DataFrame contains only the specified columns, in the order provided.

### 7.4. Rename Columns

Rename specific columns using rename().

```
df.rename(columns={
    "Name": "Employee",
    "Salary": "Annual Salary"
})

```

Rename all columns:

```
df.columns = ["Employee", "Age", "Salary"]
```

### 7.5. Reorder Columns

Change the order of DataFrame columns using a list.

```
columns = ["Name", "Salary", "Age"]

df = df[columns]
```

### 7.6. Add New Columns

Add a new column to the DataFrame.

```
df["Bonus"] = 1000
```

Create a calculated column:

```
df["Total Salary"] = df["Salary"] + df["Bonus"]
```

### 7.7. Insert Columns at a Specific Position

The insert() method adds a new column at a specified position.

**Syntax:**

```
df.insert(loc, column, value)
```

Example:

```
df.insert(1, "Department", ["IT", "HR", "Sales"])
```

The new column is inserted at position 1.

### 7.8. Drop Columns

Remove one column:

```
df.drop(columns=["Age"])
```

Remove multiple columns:

```
df.drop(columns=["Age", "Salary"])
```

### 7.9. Pop Columns

The pop() method removes a column and returns it as a Series.

```
age = df.pop("Age")
```

The Age column is removed from the original DataFrame and stored in the age variable.

### 7.10. Check Whether Columns Exist

Check whether a column exists:

```
"Salary" in df.columns
```

Check whether multiple columns exist:

```
required_columns = ["Name", "Age", "Salary"]
```
all(col in df.columns for col in required_columns)


### 7.11. Select Columns by Data Type

Use select_dtypes() to select columns based on their data types.

```
# Select numerical columns
df.select_dtypes(include="number")

# Select text columns
df.select_dtypes(include="object")

# Select numerical and text columns
df.select_dtypes(include=["number", "object"])

# Exclude numerical columns
df.select_dtypes(exclude="number")
```

### 7.12. Filter Columns by Name

Use filter() to select columns based on their labels.

```
# Select columns containing 'Sale'
df.filter(like="Sale")

# Select columns matching a regular expression
df.filter(regex="^Sale")

# Select columns using specific labels
df.filter(items=["Name", "Salary"])
```

## 8\. Examining Data Types and Unique Values

### 8.1. select\_dtypes()

Selects columns based on their data types.

```
# Numerical columns
df.select_dtypes(include="number")

# Text columns
df.select_dtypes(include="object")

# Exclude numerical columns
df.select_dtypes(exclude="number")
```

### 8.2. count()

Returns the number of non-missing values in each column.

```
df.count()
```

Example output:

text

text
name      5
age       4
salary    5
dtype: int64


### 8.3. nunique()

Returns the number of unique values in each column.

```
df.nunique()
```

By default, missing values are excluded.

To include missing values:

```
df.nunique(dropna=False)
```

### 8.4. unique()

Returns the unique values in a Series.

```
df["Name"].unique()
```

### 8.5. duplicated()

Identifies duplicate rows.

```
df.duplicated()
```

Count duplicate rows:

```
df.duplicated().sum()
```

## 9\. Checking Missing Values

### 9.1. isna()

Identifies missing values in a DataFrame.

```
df.isna()
```

Count missing values in each column:

```
df.isna().sum()
```

Calculate total missing values:

```
df.isna().sum().sum()
```

### 9.2. notna()

Identifies non-missing values.

```
df.notna()
```

Count non-missing values:

```
df.notna().sum()
```

### 9.3. any()

Checks whether at least one missing value exists in each column.

```
df.isna().any()
```

Check whether any missing values exist in the entire DataFrame:

```
df.isna().any().any()
```

## 10\. Checking Memory Usage

### 10.1. memory\_usage()

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

## 11\. Quick Reference

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
| Row and column axes | axes | df.axes |
| Underlying data array | values | df.values |
| Column labels | keys() | df.keys() |
| Select one column | Column selection | df["Name"] |
| Select multiple columns | Column selection | df[["Name", "Age"]] |
| Select columns using a list | Column selection | df[columns] |
| Rename columns | rename() | df.rename(columns={}) |
| Reorder columns | Column selection | df[columns] |
| Add a column | Assignment | df["Bonus"] = 1000 |
| Insert a column | insert() | df.insert(1, "Bonus", 1000) |
| Drop columns | drop() | df.drop(columns=["Age"]) |
| Remove and return a column | pop() | df.pop("Age") |
| Select by data type | select_dtypes() | df.select_dtypes(include="number") |
| Filter columns | filter() | df.filter(like="Sale") |
| Count non-missing values | count() | df.count() |
| Count unique values | nunique() | df.nunique() |
| Get unique values | unique() | df["Name"].unique() |
| Identify duplicates | duplicated() | df.duplicated() |
| Identify missing values | isna() | df.isna() |
| Identify non-missing values | notna() | df.notna() |
| Column memory usage | memory_usage() | df.memory_usage() |

## 12\. Recommended Data Inspection Workflow

A useful starting workflow when importing a new dataset is:

```
import pandas as pd

# Import data
df = pd.read_csv("data.csv")

# 1. Preview the dataset
df.head()

# 2. Examine the last rows
df.tail()

# 3. Check the DataFrame dimensions
print("Shape:", df.shape)

# 4. Check total elements
print("Size:", df.size)

# 5. Examine column names
print(df.columns.tolist())

# 6. Examine data types
print(df.dtypes)

# 7. Inspect DataFrame information
df.info(show_counts=True, memory_usage="deep")

# 8. Generate descriptive statistics
df.describe()

# 9. Check missing values
print(df.isna().sum())

# 10. Check duplicate records
print(df.duplicated().sum())

# 11. Examine unique values
print(df.nunique())

# 12. Examine memory usage
print(df.memory_usage(deep=True))

# 13. Select specific columns
columns = ["Name", "Age", "Salary"]
new_df = df[columns]

# 14. Examine a random sample
df.sample(5, random_state=42)
```

## 13\. Important Notes

- Methods use parentheses, such as df.head() and df.info().
- Attributes do not use parentheses, such as df.shape, df.size, and df.columns.
- head() and tail() return five rows by default.
- sample() selects random rows; use random_state for reproducible results.
- describe() summarizes numerical columns by default.
- info() is particularly useful for identifying missing values and checking data types.
- shape returns rows and columns, whereas size returns the total number of elements.
- df["Name"] returns a Series, whereas df[["Name"]] returns a DataFrame.
- df[columns] selects columns in the order specified by the list.
- rename() returns a new DataFrame by default unless inplace=True is specified.
- drop() returns a new DataFrame by default unless inplace=True is specified.
- pop() removes the selected column from the original DataFrame and returns it as a Series.
- insert() modifies the original DataFrame.
- select_dtypes() is useful when working with datasets containing many columns and different data types.
- memory_usage(deep=True) provides a more detailed estimate of memory consumption.
- values returns a NumPy array; for many applications, to_numpy() is the more explicit alternative.

## 14\. Official Documentation

- [Pandas DataFrame API Reference](<https://pandas.pydata.org/docs/reference/frame.html>)
- [Pandas DataFrame Attributes](<https://pandas.pydata.org/docs/reference/frame.html>)
- Pandas Descriptive Statistics
- [Pandas Indexing and Selecting Data](<https://pandas.pydata.org/docs/user_guide/indexing.html>)
- [Pandas Options and Settings](<https://pandas.pydata.org/docs/user_guide/options.html>)
