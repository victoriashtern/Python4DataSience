# The nunique() and unique() Methods in Pandas

The nunique() and unique() methods help identify distinct values in a Pandas Series or DataFrame.
- [Pandas Series.unique()](https://pandas.pydata.org/docs/reference/api/pandas.Series.unique.html)
- [Pandas Series.nunique()](https://pandas.pydata.org/docs/reference/api/pandas.Series.nunique.html)
- [Pandas DataFrame.nunique()](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.nunique.html)

## 1. Method Comparison

| Method | Description | Example |
|---|---|---|
| nunique() | Returns the number of unique values in a Series. | df["Department"].nunique() |
| nunique(dropna=False) | Counts unique values, including missing values (NaN). | df["Department"].nunique(dropna=False) |
| unique() | Returns an array of unique values in a Series. | df["Department"].unique() |

**Note:** These methods are typically called on individual DataFrame columns. DataFrame.nunique() counts unique values for each column by default, whereas DataFrame.unique() is not available.

## 2. Example DataFrame

```
import pandas as pd

df = pd.DataFrame({
    "Name": ["Alice", "Bob", "Alice", "Charlie", "Bob"],
    "Department": ["IT", "HR", "IT", "Finance", None],
    "Salary": [65000, 50000, 65000, 60000, 50000]
})

print(df)
```

Output:

| | Name | Department | Salary |
|---:|---|---|---:|
| 0 | Alice | IT | 65000 |
| 1 | Bob | HR | 50000 |
| 2 | Alice | IT | 65000 |
| 3 | Charlie | Finance | 60000 |
| 4 | Bob | None | 50000 |

## 3. Using unique()
```
Returns the distinct values in a column.

python
print(df["Department"].unique())
```

Output:

text
['IT' 'HR' 'Finance' None]


## 4. Using nunique()

Counts distinct values, excluding missing values by default.

```
print(df["Department"].nunique())

```
Output:

text
3


To include missing values in the count:

```
print(df["Department"].nunique(dropna=False))

```
Output:

text
4


## 5. Count Unique Values in Every Column

Use DataFrame.nunique() to count distinct values across all columns.

```
print(df.nunique())
```

Output:

text
Name          3
Department    3
Salary        3
dtype: int64


To include missing values:

```
print(df.nunique(dropna=False))
```

## 6. Practical Applications

- **Identify categories:** Find the distinct departments in a dataset.
- **Check duplicates:** Determine how many distinct values a column contains.
- **Explore data quality:** Identify unexpected categories or missing values.
- **Prepare for analysis:** Understand the number of distinct values before grouping or plotting.
