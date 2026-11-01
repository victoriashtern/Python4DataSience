
# Pandas Data Sorting

Pandas provides several methods for sorting DataFrame data. You can sort rows by column values, sort by the index, or find the largest and smallest values in a dataset.

## 1\. Official Documentation

| Method | Documentation |
| --- | --- |
| `sort_values()` | [DataFrame.sort\_values()](<https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.sort_values.html>) |
| `sort_index()` | [DataFrame.sort\_index()](<https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.sort_index.html>) |
| `nlargest()` | [DataFrame.nlargest()](<https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.nlargest.html>) |
| `nsmallest()` | [DataFrame.nsmallest()](<https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.nsmallest.html>) |

## 2\. Quick Reference

| Method | Purpose |
| --- | --- |
| `df.sort_values()` | Sort rows according to column values. |
| `df.sort_index()` | Sort rows according to their index labels. |
| `df.nlargest()` | Return the rows with the largest values. |
| `df.nsmallest()` | Return the rows with the smallest values. |

## 3\. Example DataFrame

python

```python
import pandas as pd

df = pd.DataFrame({
    "name": ["John", "Mary", "David", "Anna"],
    "age": [25, 30, 22, 28],
    "salary": [4000, 6000, 3500, 5000]
})

print(df)
```

Output:

|  | name | age | salary |
| --- | --- | --- | --- |
| 0 | John | 25 | 4000 |
| 1 | Mary | 30 | 6000 |
| 2 | David | 22 | 3500 |
| 3 | Anna | 28 | 5000 |

## 4\. sort\_values() – Sort by Column Values

Sorts rows based on the values of one or more columns.

### Ascending Order (Smallest to Largest)

python

```python
df.sort_values(by="salary")
```

Output:

|  | name | age | salary |
| --- | --- | --- | --- |
| 2 | David | 22 | 3500 |
| 0 | John | 25 | 4000 |
| 3 | Anna | 28 | 5000 |
| 1 | Mary | 30 | 6000 |

### Descending Order (Largest to Smallest)

python

```python
df.sort_values(by="salary", ascending=False)
```

Output:

|  | name | age | salary |
| --- | --- | --- | --- |
| 1 | Mary | 30 | 6000 |
| 3 | Anna | 28 | 5000 |
| 0 | John | 25 | 4000 |
| 2 | David | 22 | 3500 |

### Sort by Multiple Columns

python

```python
df.sort_values(
    by=["age", "salary"],
    ascending=[True, False]
)
```

Sorts by age first. If two people have the same age, salary determines their order.

## 5\. sort\_index() – Sort by Index

Sorts rows according to their index labels rather than their column values.

python

```python
df.sort_index(ascending=False)
```

Output:

|  | name | age | salary |
| --- | --- | --- | --- |
| 3 | Anna | 28 | 5000 |
| 2 | David | 22 | 3500 |
| 1 | Mary | 30 | 6000 |
| 0 | John | 25 | 4000 |

### Sort in Ascending Order

python

```python
df.sort_index()
```

Returns the rows in index order: 0, 1, 2, 3.

## 6\. nlargest() – Get the Largest Values

Returns the rows with the largest values in a specified column.

python

```python
df.nlargest(2, "salary")
```

Output:

|  | name | age | salary |
| --- | --- | --- | --- |
| 1 | Mary | 30 | 6000 |
| 3 | Anna | 28 | 5000 |

The number `2` specifies how many rows to return.

## 7\. nsmallest() – Get the Smallest Values

Returns the rows with the smallest values in a specified column.

python

```python
df.nsmallest(2, "salary")
```

Output:

|  | name | age | salary |
| --- | --- | --- | --- |
| 2 | David | 22 | 3500 |
| 0 | John | 25 | 4000 |

## 8\. Important Parameters

| Parameter | Description |
| --- | --- |
| `by` | Column name or list of column names used for sorting. |
| `ascending=True` | Sort from smallest to largest. |
| `ascending=False` | Sort from largest to smallest. |
| `inplace=True` | Modify the original DataFrame instead of returning a new one. |
| `na_position="last"` | Place missing values at the end. |

## 9\. Important Notes

- `sort_values()` sorts by column values.
- `sort_index()` sorts by row or column index labels.
- `nlargest()` and `nsmallest()` return a specified number of rows.
- By default, these methods return a new DataFrame and leave the original unchanged.
- Use `inplace=True` when you want to modify the original DataFrame.

## 10\. When to Use Each Method

| Situation | Recommended Method |
| --- | --- |
| Sort salaries from highest to lowest. | `sort_values()` |
| Sort rows by their index numbers. | `sort_index()` |
| Find the five highest salaries. | `nlargest(5, "salary")` |
| Find the five lowest salaries. | `nsmallest(5, "salary")` |

Add this row to your main Pandas Methods Reference:

markdown

```markdown
| [Sort Data](pandas-data-sorting.md) | `sort_values()`, `sort_index()`, `nlargest()`, `nsmallest()` | Sort rows by column values or index and find the highest or lowest values. |
```
