# Pandas Methods Reference

Pandas is a Python library for data manipulation and analysis. This reference organizes commonly used pandas functions, methods, and attributes by category, with practical examples and links to official documentation.

## 1\. Official Documentation

| Resource | Documentation |
| --- | --- |
| General Functions | [General Functions](<https://pandas.pydata.org/pandas-docs/stable/reference/general_functions.html>) |
| Official Documentation | [Pandas Docs](<https://pandas.pydata.org/docs/>) |
| Complete API Reference | [API Reference](<https://pandas.pydata.org/docs/reference/index.html>) |
| DataFrame Reference | [DataFrame Methods and Attributes](<https://pandas.pydata.org/docs/reference/frame.html>) |
| Series Reference | [Series Methods and Attributes](<https://pandas.pydata.org/docs/reference/series.html>) |
| Input/Output Functions | [Input/Output](<https://pandas.pydata.org/docs/reference/io.html>) |
| User Guide | [Pandas User Guide](<https://pandas.pydata.org/docs/user_guide/index.html>) |
| Release Notes | [What's New](<https://pandas.pydata.org/docs/whatsnew/index.html>) |

## 2\. Common Pandas Methods by Category

| Category | Common Methods | Purpose |
| --- | --- | --- |
| [Import Data](/pandas/inspection_data.md)  | `pd.read_csv()`, `pd.read_excel()`, `pd.read_json()`, `pd.read_sql()` | Load data from files and databases. |
| Inspect Data | `df.head()`, `df.tail()`, `df.sample()`, `df.info()`, `df.describe()`, `df.size`, `df.shape`, `df.columns` | Preview data and examine its structure, size, and column names. |
| Select Data | `loc[]`, `iloc[]`, `query()`, `filter()` | Select specific rows and columns. |
| Data Cleaning | `drop()`, `dropna()`, `fillna()`, `replace()`, `drop_duplicates()` | Remove or correct unwanted data. |
| Data Types | select_dtypes(),`astype()`, `convert_dtypes()`, `pd.to_numeric()`, `pd.to_datetime()` | Convert columns into appropriate data types. |
| [Sort Data](/pandas/sort_data.md)  | `sort_values()`, `sort_index()`, `nlargest()`, `nsmallest()` | Sort records by values or index. |
| Calculate Statistics | `mean()`, `median()`, `mode()`, `sum()`, `min()`, `max()`, `std()`, `var()` | Calculate statistical summaries. |
| Group Data | `groupby()`, `agg()`, `aggregate()`, `transform()` | Group records and calculate summaries. |
| Combine Data | `merge()`, `join()`, `concat()` | Combine datasets using common columns, indexes, or rows. |
| Reshape Data | `pivot()`, `pivot_table()`, `melt()`, `stack()`, `unstack()` | Change the arrangement of rows and columns. |
| [Index Management](/pandas/index_management.md)  | `reset_index()`, `set_index()`, `reindex()` | Set, reset, or reorganize the row index. |
| [Analyze Values](/pandas/value-analysis.md)  | `value_counts()`, `nunique()`, `unique()`, `duplicated()`, `corr()` | Examine frequencies, unique values, duplicates, and relationships. |
| Handle Missing Values | `isna()`, `notna()`, `dropna()`, `fillna()`, `interpolate()` | Find and handle missing data. |
| Work with Strings | `str.lower()`, `str.upper()`, `str.strip()`, `str.replace()`, `str.contains()` | Clean and search text values. |
| Work with Dates | `dt.year`, `dt.month`, `dt.day`, `resample()`, `shift()` | Extract date information and analyze time series. |
| Visualize Data | `plot()`, `hist()`, `boxplot()` | Create charts and visualizations. |
| Export Data | `to_csv()`, `to_excel()`, `to_json()`, `to_sql()`, `to_parquet()`, `to_html()` | Save results in different formats. |

**Important:** `loc` and `iloc` are indexers rather than methods. The `dt` accessor provides access to datetime properties and methods on Series. Functions such as `pd.read_csv()` and `pd.to_datetime()` are top-level pandas functions rather than DataFrame methods.

## 3\. Detailed Examples by Topic

### 3.1. Data Import and Export

Documentation: [Input/Output Functions](<https://pandas.pydata.org/docs/reference/io.html>)

python

```python
import pandas as pd

# Import data
df = pd.read_csv("data.csv")
df = pd.read_excel("data.xlsx")
df = pd.read_json("data.json")

# Export data
df.to_csv("output.csv", index=False)
df.to_excel("output.xlsx", index=False)
```

**Output:**

The import functions create a DataFrame containing the imported data. The export functions save the DataFrame to files and normally do not display output.

Example DataFrame:

| name | age | salary |
| --- | --- | --- |
| John | 25 | 4000 |
| Mary | 30 | 5000 |
| David | 28 | 4500 |

### 3.2. Data Inspection

Documentation: [DataFrame Reference](<https://pandas.pydata.org/docs/reference/frame.html>)

python

```python
# Preview data
df.head()
df.tail()
df.sample(2)

# Inspect DataFrame information
df.info()
df.describe()

# Examine DataFrame attributes
df.shape
df.size
df.columns
df.dtypes
```

Assume the DataFrame contains:

|  | name | age | salary |
| --- | --- | --- | --- |
| 0 | John | 25 | 4000 |
| 1 | Mary | 30 | 5000 |
| 2 | David | 28 | 4500 |
| 3 | Anna | 35 | 6000 |
| 4 | Peter | 22 | 3500 |

**Outputs:**

`df.head(3)` – Displays the first three rows.

text

```text
    name  age  salary
0   John   25    4000
1   Mary   30    5000
2  David   28    4500
```

`df.tail(2)` – Displays the last two rows.

text

```text
    name  age  salary
3   Anna   35    6000
4  Peter   22    3500
```

`df.sample(2)` – Displays two randomly selected rows. The result changes between executions.

text

```text
    name  age  salary
1   Mary   30    5000
4  Peter   22    3500
```

`df.info()` – Displays information about columns, data types, non-null values, and memory usage.

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
```

`df.describe()` – Displays descriptive statistics for numerical columns.

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

`df.shape` – Returns the number of rows and columns.

python

```python
(5, 3)
```

`df.size` – Returns the total number of values (rows × columns).

python

```python
15
```

`df.columns` – Returns the column names.

python

```python
Index(['name', 'age', 'salary'], dtype='object')
```

`df.dtypes` – Returns the data type of each column.

text

```text
name      object
age        int64
salary     int64
dtype: object
```

### 3.3. Data Cleaning

Documentation: [Working with Missing Data](<https://pandas.pydata.org/docs/user_guide/missing_data.html>)

python

```python
# Example DataFrame
df = pd.DataFrame({
    "name": ["John", "Mary", "John"],
    "age": [25, None, 25],
    "salary": [4000, 5000, 4000]
})

# Identify missing values
df.isna().sum()

# Remove missing values
df.dropna()

# Replace missing values
df.fillna(0)

# Remove duplicates
df.drop_duplicates()

# Rename columns
df.rename(columns={"name": "employee"})

# Change data types
df.astype({"age": "float64"})
```

**Outputs:**

`df.isna().sum()` – Counts missing values in each column.

text

```text
name      0
age       1
salary    0
dtype: int64
```

`df.dropna()` – Removes rows containing missing values.

text

```text
   name   age  salary
0  John  25.0    4000
2  John  25.0    4000
```

`df.fillna(0)` – Replaces missing values with zero.

text

```text
   name   age  salary
0  John  25.0    4000
1  Mary   0.0    5000
2  John  25.0    4000
```

`df.drop_duplicates()` – Removes duplicate rows.

text

```text
   name   age  salary
0  John  25.0    4000
1  Mary   NaN    5000
```

`df.rename(columns={"name": "employee"})` – Renames a column.

text

```text
  employee   age  salary
0     John  25.0    4000
1     Mary   NaN    5000
2     John  25.0    4000
```

### 3.4. Data Selection and Filtering

Documentation: [Indexing and Selecting Data](<https://pandas.pydata.org/docs/user_guide/indexing.html>)

python

```python
# Select one column
df["sales"]

# Select multiple columns
df[["sales", "profit"]]

# Select rows and columns
df.loc[0:2, ["sales", "profit"]]
df.iloc[0:2, 0:2]

# Filter records
df.query("sales > 1000")
```

Assume the DataFrame:

|  | sales | profit |
| --- | --- | --- |
| 0 | 500 | 100 |
| 1 | 1500 | 300 |
| 2 | 2000 | 500 |

**Outputs:**

`df["sales"]` – Selects one column.

text

```text
0     500
1    1500
2    2000
Name: sales, dtype: int64
```

`df[["sales", "profit"]]` – Selects two columns.

text

```text
   sales  profit
0    500     100
1   1500     300
2   2000     500
```

`df.loc[0:2, ["sales", "profit"]]` – Selects rows using index labels and specified columns.

text

```text
   sales  profit
0    500     100
1   1500     300
2   2000     500
```

`df.iloc[0:2, 0:2]` – Selects the first two rows and first two columns by position.

text

```text
   sales  profit
0    500     100
1   1500     300
```

`df.query("sales > 1000")` – Returns rows where sales exceed 1000.

text

```text
   sales  profit
1   1500     300
2   2000     500
```

### 3.5. Grouping and Aggregation

Documentation: [GroupBy User Guide](<https://pandas.pydata.org/docs/user_guide/groupby.html>)

python

```python
# Calculate total sales by category
df.groupby("category")["sales"].sum()

# Apply multiple aggregations
df.groupby("category").agg({
    "sales": "sum",
    "profit": "mean"
})
```

Assume the DataFrame:

| category | sales | profit |
| --- | --- | --- |
| A | 100 | 20 |
| A | 200 | 40 |
| B | 300 | 60 |
| B | 400 | 80 |

**Outputs:**

`groupby("category")["sales"].sum()` – Calculates total sales for each category.

text

```text
category
A    300
B    700
Name: sales, dtype: int64
```

`groupby().agg()` – Calculates multiple summaries.

text

```text
          sales  profit
category
A           300    30.0
B           700    70.0
```

### 3.6. Combining and Reshaping Data

Documentation:

- [Merge, Join, and Concatenate](<https://pandas.pydata.org/docs/user_guide/merging.html>)
- [Reshaping and Pivot Tables](<https://pandas.pydata.org/docs/user_guide/reshaping.html>)

python

```python
# Merge datasets
merged_df = pd.merge(df1, df2, on="id")

# Concatenate datasets
combined_df = pd.concat([df1, df2], ignore_index=True)

# Create a pivot table
pivot_df = df.pivot_table(
    index="category",
    values="sales",
    aggfunc="sum"
)
```

**Example: Merge**

python

```python
df1 = pd.DataFrame({
    "id": [1, 2],
    "name": ["John", "Mary"]
})

df2 = pd.DataFrame({
    "id": [1, 2],
    "salary": [4000, 5000]
})

merged_df = pd.merge(df1, df2, on="id")
print(merged_df)
```

Output:

text

```text
   id  name  salary
0   1  John    4000
1   2  Mary    5000
```

**Example: Concat**

python

```python
df1 = pd.DataFrame({
    "name": ["John", "Mary"]
})

df2 = pd.DataFrame({
    "name": ["David", "Anna"]
})

combined_df = pd.concat([df1, df2], ignore_index=True)
print(combined_df)
```

Output:

text

```text
    name
0   John
1   Mary
2  David
3   Anna
```

**Example: Pivot Table**

python

```python
pivot_df = df.pivot_table(
    index="category",
    values="sales",
    aggfunc="sum"
)

print(pivot_df)
```

Output:

text

```text
          sales
category
A           300
B           700
```

### 3.7. Index Management

Documentation: [DataFrame Reference](<https://pandas.pydata.org/docs/reference/frame.html>)

Index management methods allow you to set, reset, and reorganize the index of a DataFrame.

**reset\_index()**

Resets the DataFrame index to the default integer index.

python

```python
df = pd.DataFrame({
    "name": ["John", "Mary", "David"],
    "age": [25, 30, 28]
}, index=[10, 20, 30])

# Creates a new DataFrame
new_df = df.reset_index()

# Creates a new DataFrame and assigns it back to df
df = df.reset_index()

# Modifies the original DataFrame
df.reset_index(inplace=True)
```

Output of `df.reset_index()`:

text

```text
   index   name  age
0     10   John   25
1     20   Mary   30
2     30  David   28
```

By default, the original index becomes a new column.

To discard the original index:

python

```python
new_df = df.reset_index(drop=True)
print(new_df)
```

Output:

text

```text
    name  age
0   John   25
1   Mary   30
2  David   28
```

**set\_index()**

Sets an existing column as the DataFrame index.

python

```python
df = df.set_index("name")
print(df)
```

Output:

text

```text
       age
name
John    25
Mary    30
David   28
```

**reindex()**

Changes the row or column labels to match a specified index.

python

```python
df = pd.DataFrame({
    "name": ["John", "Mary", "David"]
})

new_df = df.reindex([0, 1, 2, 3])
print(new_df)
```

Output:

text

```text
    name
0   John
1   Mary
2  David
3    NaN
```

**Related methods:**

| Method | Purpose |
| --- | --- |
| `df.reset_index()` | Resets the index and preserves the old index as a column. |
| `df.reset_index(drop=True)` | Resets the index and discards the old index. |
| `df.set_index("column")` | Sets a column as the DataFrame index. |
| `df.reindex()` | Changes the row or column labels to a specified index. |
| `df.rename_axis()` | Changes the name of the index or column axis. |

### 3.8. String and Date Operations

Documentation:

- [Working with Text Data](<https://pandas.pydata.org/docs/user_guide/text.html>)
- [Time Series and Date Functionality](<https://pandas.pydata.org/docs/user_guide/timeseries.html>)

python

```python
df = pd.DataFrame({
    "name": [" John ", "MARY", " David "],
    "date": ["2024-01-15", "2024-02-20", "2024-03-10"]
})

# Clean text
df["name"] = df["name"].str.strip().str.lower()

# Convert dates
df["date"] = pd.to_datetime(df["date"])

# Extract date components
df["year"] = df["date"].dt.year
df["month"] = df["date"].dt.month

print(df)
```

Output:

text

```text
    name       date  year  month
0   john 2024-01-15  2024      1
1   mary 2024-02-20  2024      2
2  david 2024-03-10  2024      3
```

### 3.9. Data Visualization

Documentation: [Visualization Guide](<https://pandas.pydata.org/docs/user_guide/visualization.html>)

python

```python
# Histogram
df["sales"].plot(kind="hist")

# Scatter plot
df.plot(x="sales", y="profit", kind="scatter")

# Box plot
df.boxplot(column="sales")
```

**Output:**

These commands generate visualizations rather than text output:

- `hist()` – Displays the distribution of numerical values.
- `scatter` – Displays the relationship between two numerical columns.
- `boxplot()` – Displays the distribution, median, and potential outliers.

## 4\. Important Notes

- The examples assume that `df` is an existing pandas DataFrame unless a new DataFrame is explicitly created.
- Some operations return a new DataFrame or Series rather than modifying the original object.
- Use `inplace=True` when an operation supports it and you want to modify the existing DataFrame directly.
- `reset_index()` is useful after filtering, grouping, or sorting when you want to reorganize the row index.
- `df.shape`, `df.size`, `df.columns`, and `df.dtypes` are attributes, not methods. Do not add parentheses when accessing them.
- Check the official documentation for the parameters, return values, and behavior of each method.
- Available methods and behavior may vary between pandas versions.

Note: The outputs are illustrative. For methods such as `sample()`, the exact results can vary between executions.
