
# Pandas Data Combining

Pandas provides three main methods for combining DataFrames: `merge()`, `join()`, and `concat()`.

## 1\. Official Documentation

| Method | Documentation |
| --- | --- |
| `merge()` | [pandas.merge()](<https://pandas.pydata.org/docs/reference/api/pandas.merge.html>) |
| `join()` | [DataFrame.join()](<https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.join.html>) |
| `concat()` | [pandas.concat()](<https://pandas.pydata.org/docs/reference/api/pandas.concat.html>) |

## 2\. Quick Reference

| Method | Purpose |
| --- | --- |
| `merge()` | Combine DataFrames using common columns. |
| `join()` | Combine DataFrames using indexes. |
| `concat()` | Combine DataFrames by adding rows or columns. |

## 3\. merge() – Combine Using Common Columns

Use `merge()` to combine two DataFrames using a shared column.

### Syntax

python

```python
pd.merge(df1, df2, on="id", how="inner")
```

### Join Types

| Type | Description |
| --- | --- |
| `inner` | Keep matching records from both DataFrames. |
| `left` | Keep all records from the first DataFrame. |
| `right` | Keep all records from the second DataFrame. |
| `outer` | Keep all records from both DataFrames. |

### Example

python

```python
import pandas as pd

df1 = pd.DataFrame({
    "id": [1, 2, 3],
    "name": ["John", "Mary", "David"]
})

df2 = pd.DataFrame({
    "id": [1, 2, 4],
    "salary": [4000, 5000, 6000]
})

result = pd.merge(df1, df2, on="id", how="inner")

print(result)
```

**Output:**

text

```text
   id  name  salary
0   1  John    4000
1   2  Mary    5000
```

Only matching IDs (1 and 2) appear in the result.

### Other Join Types

python

```python
# Keep all records from df1
pd.merge(df1, df2, on="id", how="left")

# Keep all records from df2
pd.merge(df1, df2, on="id", how="right")

# Keep all records from both DataFrames
pd.merge(df1, df2, on="id", how="outer")
```

**Output – Left Join:**

text

```text
   id   name  salary
0   1   John  4000.0
1   2   Mary  5000.0
2   3  David     NaN
```

**Output – Right Join:**

text

```text
   id  name  salary
0   1  John    4000
1   2  Mary    5000
2   4   NaN    6000
```

**Output – Outer Join:**

text

```text
   id   name  salary
0   1   John  4000.0
1   2   Mary  5000.0
2   3  David     NaN
3   4    NaN  6000.0
```

## 4\. join() – Combine Using Indexes

Use `join()` to combine DataFrames based on their indexes.

### Syntax

python

```python
df1.join(df2)
```

### Example

python

```python
df1 = pd.DataFrame({
    "name": ["John", "Mary", "David"]
}, index=[1, 2, 3])

df2 = pd.DataFrame({
    "salary": [4000, 5000, 6000]
}, index=[1, 2, 4])

result = df1.join(df2)

print(result)
```

**Output:**

text

```text
    name  salary
1   John  4000.0
2   Mary  5000.0
3  David     NaN
```

The default join is a left join. All indexes from `df1` are retained.

### Other Join Types

python

```python
# Keep matching indexes
df1.join(df2, how="inner")

# Keep all indexes from both DataFrames
df1.join(df2, how="outer")
```

**Output – Inner Join:**

text

```text
   name  salary
1  John    4000
2  Mary    5000
```

**Output – Outer Join:**

text

```text
    name  salary
1   John  4000.0
2   Mary  5000.0
3  David     NaN
4    NaN  6000.0
```

## 5\. concat() – Combine Rows or Columns

Use `concat()` to combine multiple DataFrames vertically or horizontally.

### A. Vertical – Add Rows

Use `axis=0` (default).

python

```python
df1 = pd.DataFrame({
    "name": ["John", "Mary"]
})

df2 = pd.DataFrame({
    "name": ["David", "Anna"]
})

result = pd.concat([df1, df2], ignore_index=True)

print(result)
```

**Output:**

text

```text
    name
0   John
1   Mary
2  David
3   Anna
```

The rows from `df2` are added below the rows from `df1`.

### B. Horizontal – Add Columns

Use `axis=1`.

python

```python
df1 = pd.DataFrame({
    "name": ["John", "Mary", "David"]
})

df2 = pd.DataFrame({
    "salary": [4000, 5000, 6000]
})

result = pd.concat([df1, df2], axis=1)

print(result)
```

**Output:**

text

```text
    name  salary
0   John    4000
1   Mary    5000
2  David    6000
```

The columns from `df2` are added beside the columns from `df1`.

## 6\. Difference Between the Three Methods

| Method | Combines By | Typical Use |
| --- | --- | --- |
| `merge()` | Common columns | Combine employee and salary data using employee ID. |
| `join()` | Indexes | Combine DataFrames with matching indexes. |
| `concat()` | Rows or columns | Combine monthly datasets or add columns. |

## 7\. Important Notes

- `merge()` and `concat()` are pandas functions.
- `join()` is a DataFrame method.
- These methods return a new DataFrame.
- Use `ignore_index=True` with `concat()` to create a new sequential index.
- `join()` and horizontal `concat()` align data using indexes.
- Check for missing values and duplicate records after combining datasets.

## Additional Resources

- [Pandas Merge, Join, and Concatenate Guide](<https://pandas.pydata.org/docs/user_guide/merging.html>)
- [merge()](<https://pandas.pydata.org/docs/reference/api/pandas.merge.html>)
- [join()](<https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.join.html>)
- [concat()](<https://pandas.pydata.org/docs/reference/api/pandas.concat.html>)

Add this entry to your main `pandas-methods-reference.md`:

markdown

```markdown
| [Combine Data](pandas-data-combining.md) | `merge()`, `join()`, `concat()` | Combine DataFrames using columns, indexes, or rows. |
```
