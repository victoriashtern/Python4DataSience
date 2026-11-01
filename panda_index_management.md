# Pandas Index Management

Pandas provides three main methods for managing DataFrame indexes: `reset_index()`, `set_index()`, and `reindex()`.

These methods help you change row labels, use columns as indexes, and reorganize rows and columns.

## 1\. Official Documentation

| Method | Documentation |
| --- | --- |
| `reset_index()` | [DataFrame.reset\_index()](<https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.reset_index.html>) |
| `set_index()` | [DataFrame.set\_index()](<https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.set_index.html>) |
| `reindex()` | [DataFrame.reindex()](<https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.reindex.html>) |

## 2\. Quick Reference

| Method | What It Does |
| --- | --- |
| `reset_index()` | Replaces the current row labels with default numbers (0, 1, 2...). |
| `set_index()` | Uses a column, such as `employee_id`, as the row labels instead of default numbers. |
| `reindex()` | Changes the order of rows or columns, or adds new rows or columns with missing values. |

## 3\. reset\_index() – Reset the Index

Use `reset_index()` to replace the current row labels with default numbers starting from 0.

### Example

python

```python
import pandas as pd

df = pd.DataFrame({
    "name": ["John", "Mary", "David"],
    "salary": [4000, 5000, 4500]
}, index=[10, 20, 30])

new_df = df.reset_index()

print(new_df)
```

**Output:**

text

```text
   index   name  salary
0     10   John    4000
1     20   Mary    5000
2     30  David    4500
```

Notice that:

- The old index becomes a regular column.
- Pandas creates new row numbers starting from 0.
- The original DataFrame (`df`) remains unchanged.

### Does reset\_index() Create a New DataFrame?

Yes. By default, `reset_index()` returns a new DataFrame rather than modifying the original.

There are three common ways to use it:

| Code | What Happens |
| --- | --- |
| `new_df = df.reset_index()` | Creates a new DataFrame called `new_df`. The original `df` remains unchanged. |
| `df = df.reset_index()` | Creates a new DataFrame and assigns it back to `df`. |
| `df.reset_index(inplace=True)` | Modifies the original DataFrame directly. No new DataFrame is returned. |

**Important:** When using `inplace=True`, the method returns `None`, so do not assign its result back to the DataFrame.

python

```python
# Correct
df.reset_index(drop=True, inplace=True)

# Avoid
df = df.reset_index(drop=True, inplace=True)
```

### Drop the Old Index

Use `drop=True` when you do not need to keep the old index as a column.

python

```python
new_df = df.reset_index(drop=True)

print(new_df)
```

**Output:**

text

```text
    name  salary
0   John    4000
1   Mary    5000
2  David    4500
```

### Common Parameters

| Parameter | Description |
| --- | --- |
| `drop=True` | Discards the old index instead of keeping it as a column. |
| `inplace=True` | Modifies the original DataFrame instead of returning a new one. |

## 4\. set\_index() – Set a Column as the Index

Use `set_index()` to make an existing column the DataFrame index.

### Example

python

```python
df = pd.DataFrame({
    "employee_id": [101, 102, 103],
    "name": ["John", "Mary", "David"],
    "salary": [4000, 5000, 4500]
})

result = df.set_index("employee_id")

print(result)
```

**Output:**

text

```text
              name  salary
employee_id
101           John    4000
102           Mary    5000
103          David    4500
```

The `employee_id` column becomes the index instead of a regular column.

### Common Parameters

| Parameter | Description |
| --- | --- |
| `drop=True` | Removes the selected column from the DataFrame (default). |
| `inplace=True` | Modifies the original DataFrame. |
| `append=True` | Adds the selected column to the existing index. |

## 5\. reindex() – Reorganize the Index

Use `reindex()` to change the order of rows or columns.

It can also add new row or column labels. Missing values are filled with `NaN` by default.

### Example: Reorder Rows

python

```python
df = pd.DataFrame({
    "name": ["John", "Mary", "David"],
    "salary": [4000, 5000, 4500]
}, index=[1, 2, 3])

result = df.reindex([3, 1, 2])

print(result)
```

**Output:**

text

```text
    name  salary
3  David    4500
1   John    4000
2   Mary    5000
```

The rows are now displayed in the order 3, 1, 2.

### Example: Add a New Index

python

```python
result = df.reindex([1, 2, 3, 4])

print(result)
```

**Output:**

text

```text
    name  salary
1   John  4000.0
2   Mary  5000.0
3  David  4500.0
4    NaN     NaN
```

Index 4 does not exist in the original DataFrame, so pandas adds a new row with missing values.

### Reindex Columns

You can also change the order of columns.

python

```python
result = df.reindex(columns=["salary", "name"])

print(result)
```

**Output:**

text

```text
   salary   name
1    4000   John
2    5000   Mary
3    4500  David
```

## 6\. Difference Between the Three Methods

| Method | What It Does | Example Use |
| --- | --- | --- |
| `reset_index()` | Replaces the current index with default numbers. | Start row numbering from 0. |
| `set_index()` | Uses a column as the row index. | Use employee ID as the index. |
| `reindex()` | Changes the order of rows or columns, or adds new labels. | Reorder rows or add missing rows. |

## 7\. Important Notes

- DataFrame indexes identify rows.
- `reset_index()` creates a new default index.
- `set_index()` uses an existing column as the index.
- `reindex()` changes row or column labels and their order.
- These methods return a new DataFrame by default, except when `inplace=True` is used where supported.
- Use `inplace=True` when you want to modify the original DataFrame directly.
- Always check the resulting DataFrame after changing its index.

## Additional Resources

- [Pandas Indexing and Selecting Data](<https://pandas.pydata.org/docs/user_guide/indexing.html>)
- [reset\_index()](<https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.reset_index.html>)
- [set\_index()](<https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.set_index.html>)
- [reindex()](<https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.reindex.html>)
