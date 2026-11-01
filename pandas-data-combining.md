

# Pandas Data Combining – merge(), join(), and concat()

Pandas provides several methods for combining multiple DataFrames into a single dataset. The three commonly used methods are `merge()`, `join()`, and `concat()`.

These methods allow you to combine datasets based on common columns, indexes, or by stacking DataFrames vertically or horizontally.

## 1\. Official Documentation

| Method | Documentation |
| --- | --- |
| `pd.merge()` | [pandas.merge()](<https://pandas.pydata.org/docs/reference/api/pandas.merge.html>) |
| `DataFrame.join()` | [DataFrame.join()](<https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.join.html>) |
| `pd.concat()` | [pandas.concat()](<https://pandas.pydata.org/docs/reference/api/pandas.concat.html>) |

## 2\. Quick Reference

| Method | Purpose | How It Combines Data |
| --- | --- | --- |
| `merge()` | Combines DataFrames using common columns or indexes. | Database-style joins. |
| `join()` | Combines DataFrames primarily using their indexes. | Index-based joining. |
| `concat()` | Combines multiple DataFrames along rows or columns. | Vertical or horizontal stacking. |

## 3\. merge() – Combine DataFrames Using Common Columns

The `merge()` function combines two DataFrames using one or more common columns or indexes.

It works similarly to SQL JOIN operations.

### Basic Syntax

python

```python
pd.merge(
    left,
    right,
    how="inner",
    on=None,
    left_on=None,
    right_on=None
)
```

### Common Parameters

| Parameter | Description |
| --- | --- |
| `left` | First DataFrame. |
| `right` | Second DataFrame. |
| `how` | Type of join: inner, left, right, or outer. |
| `on` | Column name used to match both DataFrames. |
| `left_on` | Column name in the left DataFrame. |
| `right_on` | Column name in the right DataFrame. |
| `left_index` | Uses the left DataFrame index as the join key. |
| `right_index` | Uses the right DataFrame index as the join key. |
| `suffixes` | Adds suffixes to overlapping column names. |
| `indicator` | Adds a column identifying the source of each row. |
| `validate` | Checks the expected relationship between join keys. |

### Example: Create Two DataFrames

python

```python
import pandas as pd

employees = pd.DataFrame({
    "employee_id": [1, 2, 3, 4],
    "name": ["John", "Mary", "David", "Anna"]
})

salaries = pd.DataFrame({
    "employee_id": [1, 2, 3, 5],
    "salary": [4000, 5000, 4500, 6000]
})
```

### Inner Join

Returns only records with matching keys in both DataFrames.

python

```python
result = pd.merge(
    employees,
    salaries,
    on="employee_id",
    how="inner"
)
```

Result:

| employee\_id | name | salary |
| --- | --- | --- |
| 1 | John | 4000 |
| 2 | Mary | 5000 |
| 3 | David | 4500 |

### Left Join

Returns all records from the left DataFrame and matching records from the right DataFrame.

python

```python
result = pd.merge(
    employees,
    salaries,
    on="employee_id",
    how="left"
)
```

Result:

| employee\_id | name | salary |
| --- | --- | --- |
| 1 | John | 4000 |
| 2 | Mary | 5000 |
| 3 | David | 4500 |
| 4 | Anna | NaN |

### Right Join

Returns all records from the right DataFrame and matching records from the left DataFrame.

python

```python
result = pd.merge(
    employees,
    salaries,
    on="employee_id",
    how="right"
)
```

Result:

| employee\_id | name | salary |
| --- | --- | --- |
| 1 | John | 4000 |
| 2 | Mary | 5000 |
| 3 | David | 4500 |
| 5 | NaN | 6000 |

### Outer Join

Returns all records from both DataFrames, matching records where possible.

python

```python
result = pd.merge(
    employees,
    salaries,
    on="employee_id",
    how="outer"
)
```

Result:

| employee\_id | name | salary |
| --- | --- | --- |
| 1 | John | 4000 |
| 2 | Mary | 5000 |
| 3 | David | 4500 |
| 4 | Anna | NaN |
| 5 | NaN | 6000 |

### Merge Using Different Column Names

Use `left_on` and `right_on` when the matching columns have different names.

python

```python
employees = pd.DataFrame({
    "employee_id": [1, 2, 3],
    "name": ["John", "Mary", "David"]
})

salaries = pd.DataFrame({
    "id": [1, 2, 3],
    "salary": [4000, 5000, 4500]
})

result = pd.merge(
    employees,
    salaries,
    left_on="employee_id",
    right_on="id"
)
```

### Merge Using Multiple Columns

You can use multiple columns as matching keys.

python

```python
result = pd.merge(
    df1,
    df2,
    on=["employee_id", "department"],
    how="inner"
)
```

### Additional Merge Options

python

```python
# Add suffixes to overlapping column names
result = pd.merge(
    df1,
    df2,
    on="employee_id",
    suffixes=("_left", "_right")
)

# Identify the source of each record
result = pd.merge(
    df1,
    df2,
    on="employee_id",
    how="outer",
    indicator=True
)

# Validate a one-to-one relationship
result = pd.merge(
    df1,
    df2,
    on="employee_id",
    validate="one_to_one"
)
```

## 4\. join() – Combine DataFrames Using Indexes

The `join()` method combines DataFrames primarily using their indexes.

It is especially useful when the matching information is already stored in the DataFrame index.

### Basic Syntax

python

```python
df1.join(
    other,
    how="left",
    on=None,
    lsuffix="",
    rsuffix=""
)
```

### Common Parameters

| Parameter | Description |
| --- | --- |
| `other` | DataFrame or Series to join. |
| `on` | Column in the calling DataFrame used to match the other DataFrame's index. |
| `how` | Type of join: left, right, inner, or outer. |
| `lsuffix` | Suffix for overlapping column names in the left DataFrame. |
| `rsuffix` | Suffix for overlapping column names in the right DataFrame. |
| `sort` | Sorts the resulting index. |

### Example

python

```python
employees = pd.DataFrame({
    "name": ["John", "Mary", "David"]
}, index=[1, 2, 3])

salaries = pd.DataFrame({
    "salary": [4000, 5000, 4500]
}, index=[1, 2, 4])
```

### Left Join

python

```python
result = employees.join(
    salaries,
    how="left"
)
```

Result:

| Index | name | salary |
| --- | --- | --- |
| 1 | John | 4000 |
| 2 | Mary | 5000 |
| 3 | David | NaN |

### Outer Join

python

```python
result = employees.join(
    salaries,
    how="outer"
)
```

Result:

| Index | name | salary |
| --- | --- | --- |
| 1 | John | 4000 |
| 2 | Mary | 5000 |
| 3 | David | NaN |
| 4 | NaN | 4500 |

### Join Using a Column and an Index

Use `on` when the left DataFrame has a matching column and the right DataFrame uses its index.

python

```python
employees = pd.DataFrame({
    "employee_id": [1, 2, 3],
    "name": ["John", "Mary", "David"]
})

salaries = pd.DataFrame({
    "salary": [4000, 5000, 4500]
}, index=[1, 2, 3])

result = employees.join(
    salaries,
    on="employee_id"
)
```

## 5\. concat() – Stack DataFrames Vertically or Horizontally

The `concat()` function combines multiple DataFrames along a particular axis.

It is useful when you want to append rows or add columns from different datasets.

### Basic Syntax

python

```python
pd.concat(
    objs,
    axis=0,
    join="outer",
    ignore_index=False
)
```

### Common Parameters

| Parameter | Description |
| --- | --- |
| `objs` | List or dictionary of DataFrames or Series to combine. |
| `axis=0` | Combines DataFrames vertically (rows). |
| `axis=1` | Combines DataFrames horizontally (columns). |
| `join="outer"` | Keeps the union of columns or indexes (default). |
| `join="inner"` | Keeps only common columns or indexes. |
| `ignore_index=True` | Creates a new default integer index along the concatenation axis. |
| `keys` | Adds an additional index level identifying the source. |
| `verify_integrity=True` | Checks for duplicate labels along the concatenation axis. |

### Example: Vertical Concatenation

Combine DataFrames by adding rows.

python

```python
df1 = pd.DataFrame({
    "name": ["John", "Mary"],
    "age": [25, 30]
})

df2 = pd.DataFrame({
    "name": ["David", "Anna"],
    "age": [28, 22]
})

result = pd.concat(
    [df1, df2],
    ignore_index=True
)
```

Result:

| Index | name | age |
| --- | --- | --- |
| 0 | John | 25 |
| 1 | Mary | 30 |
| 2 | David | 28 |
| 3 | Anna | 22 |

### Example: Horizontal Concatenation

Combine DataFrames by adding columns.

python

```python
df1 = pd.DataFrame({
    "name": ["John", "Mary", "David"]
})

df2 = pd.DataFrame({
    "salary": [4000, 5000, 4500]
})

result = pd.concat(
    [df1, df2],
    axis=1
)
```

Result:

| Index | name | salary |
| --- | --- | --- |
| 0 | John | 4000 |
| 1 | Mary | 5000 |
| 2 | David | 4500 |

### Concatenate Using Common Columns

Use `join="inner"` to keep only columns shared by all DataFrames.

python

```python
result = pd.concat(
    [df1, df2],
    axis=0,
    join="inner",
    ignore_index=True
)
```

### Keep Source Information Using keys

python

```python
result = pd.concat(
    [df1, df2],
    keys=["January", "February"]
)
```

This creates a hierarchical index that identifies the source DataFrame.

## 6\. Differences Between merge(), join(), and concat()

| Feature | merge() | join() | concat() |
| --- | --- | --- | --- |
| Main purpose | Combine using matching keys. | Combine primarily using indexes. | Stack or combine DataFrames. |
| Matching columns | Yes | Possible using `on` | No key matching |
| Index matching | Yes | Yes | Aligns indexes when combining columns |
| Multiple DataFrames | Usually two at a time | One or multiple | Yes |
| SQL-style joins | Yes | Yes | No |
| Vertical stacking | Not its primary purpose | Not its primary purpose | Yes |
| Horizontal stacking | Possible through keys | Yes | Yes |

## 7\. Practical Example: Combining Business Datasets

Consider three datasets containing employee information, department details, and salaries.

python

```python
import pandas as pd

employees = pd.DataFrame({
    "employee_id": [1, 2, 3],
    "name": ["John", "Mary", "David"],
    "department_id": [10, 20, 10]
})

departments = pd.DataFrame({
    "department_id": [10, 20],
    "department": ["Sales", "IT"]
})

salaries = pd.DataFrame({
    "employee_id": [1, 2, 3],
    "salary": [4000, 5000, 4500]
})

# Combine employees and departments
df = pd.merge(
    employees,
    departments,
    on="department_id",
    how="left"
)

# Combine the result with salaries
df = pd.merge(
    df,
    salaries,
    on="employee_id",
    how="left"
)

print(df)
```

Result:

| employee\_id | name | department\_id | department | salary |
| --- | --- | --- | --- | --- |
| 1 | John | 10 | Sales | 4000 |
| 2 | Mary | 20 | IT | 5000 |
| 3 | David | 10 | Sales | 4500 |

## 8\. Common Mistakes and Recommendations

- **Unexpected duplicate rows:** Check whether the matching columns contain duplicate keys. A many-to-many merge can produce multiple rows for one key.
- **Missing values after merging:** Check whether matching keys exist in both DataFrames.
- **Different column names:** Use `left_on` and `right_on` with `merge()`.
- **Incorrect index alignment:** Remember that `join()` and horizontal `concat()` align data using indexes.
- **Repeated indexes after concatenation:** Use `ignore_index=True` when you want a new sequential index.
- **Overlapping column names:** Use `suffixes` in `merge()` or `lsuffix` and `rsuffix` in `join()`.

## 9\. When to Use Each Method

| Situation | Recommended Method |
| --- | --- |
| Combine two datasets using a common ID column. | `merge()` |
| Combine DataFrames using their indexes. | `join()` |
| Append rows from multiple files. | `concat()` |
| Add columns from DataFrames with matching indexes. | `concat(axis=1)` or `join()` |
| Perform SQL-style inner, left, right, or outer joins. | `merge()` |
| Combine multiple monthly or yearly datasets. | `concat()` |

## 10\. Important Notes

- `merge()` and `concat()` are top-level pandas functions.
- `join()` is a DataFrame method.
- These operations generally return a new DataFrame rather than modifying the original DataFrame.
- Always check the resulting row count and missing values after combining datasets.
- Use `validate` in `merge()` when you want to check expected key relationships.
- Use `ignore_index=True` with `concat()` when you want a new sequential index.

## Additional Resources

- [Pandas Merge, Join, and Concatenate Guide](<https://pandas.pydata.org/docs/user_guide/merging.html>)
- [pandas.merge() API](<https://pandas.pydata.org/docs/reference/api/pandas.merge.html>)
- [DataFrame.join() API](<https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.join.html>)
- [pandas.concat() API](<https://pandas.pydata.org/docs/reference/api/pandas.concat.html>)



```markdown
| [Combine Data](pandas-data-combining.md) | `merge()`, `join()`, `concat()` | Combine datasets using common columns, indexes, or rows. |
```
