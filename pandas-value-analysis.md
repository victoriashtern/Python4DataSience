
# Pandas Value Analysis – Methods and Examples

Pandas provides several methods for analyzing values in a DataFrame or Series. These methods help identify unique values, examine value frequencies, detect duplicate records, and explore relationships between numerical columns.

## 1\. Official Documentation

| Method | Documentation |
| --- | --- |
| `value_counts()` | [Series.value\_counts()](<https://pandas.pydata.org/docs/reference/api/pandas.Series.value_counts.html>) |
| `nunique()` | [DataFrame.nunique()](<https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.nunique.html>) |
| `unique()` | [Series.unique()](<https://pandas.pydata.org/docs/reference/api/pandas.Series.unique.html>) |
| `duplicated()` | [DataFrame.duplicated()](<https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.duplicated.html>) |
| `corr()` | [DataFrame.corr()](<https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.corr.html>) |

## 2\. Quick Reference

| Method | Purpose | Returns |
| --- | --- | --- |
| `value_counts()` | Counts the frequency of each unique value. | Series |
| `nunique()` | Counts the number of unique values. | Integer or Series |
| `unique()` | Returns all unique values. | NumPy array or ExtensionArray |
| `duplicated()` | Identifies duplicate rows or values. | Boolean Series |
| `corr()` | Calculates correlations between numerical columns. | DataFrame |

## 3\. value\_counts() – Count Value Frequencies

The `value_counts()` method counts how many times each unique value appears in a Series.

### Example

python

```python
import pandas as pd

df = pd.DataFrame({
    "department": [
        "Sales", "IT", "HR", "Sales",
        "IT", "Sales", "HR", "IT"
    ]
})

print(df["department"].value_counts())
```

Output:

text

```text
department
Sales    3
IT       3
HR       2
Name: count, dtype: int64
```

### Common Parameters

| Parameter | Description |
| --- | --- |
| `normalize=True` | Returns relative frequencies instead of counts. |
| `sort=True` | Sorts results by frequency (default). |
| `ascending=True` | Sorts frequencies in ascending order. |
| `dropna=False` | Includes missing values in the counts. |
| `bins` | Groups numerical values into intervals. |

### Examples

python

```python
# Count each value
df["department"].value_counts()

# Calculate percentages
df["department"].value_counts(normalize=True) * 100

# Include missing values
df["department"].value_counts(dropna=False)

# Sort from lowest to highest frequency
df["department"].value_counts(ascending=True)
```

## 4\. nunique() – Count Unique Values

The `nunique()` method returns the number of distinct values in a Series or DataFrame.

### Example

python

```python
df = pd.DataFrame({
    "department": ["Sales", "IT", "HR", "Sales", "IT"],
    "city": ["Toronto", "London", "Toronto", "Paris", "London"]
})

# Count unique values in one column
print(df["department"].nunique())

# Count unique values in every column
print(df.nunique())
```

Output:

text

```text
department    3
city          3
dtype: int64
```

### Common Parameters

| Parameter | Description |
| --- | --- |
| `axis=0` | Counts unique values down each column (default for DataFrame). |
| `axis=1` | Counts unique values across each row. |
| `dropna=True` | Excludes missing values (default). |

### Examples

python

```python
# Unique values in one column
df["department"].nunique()

# Unique values in every column
df.nunique()

# Include missing values
df.nunique(dropna=False)
```

## 5\. unique() – Retrieve Unique Values

The `unique()` method returns an array containing the distinct values in a Series.

Unlike `value_counts()`, it does not count the occurrences of each value.

### Example

python

```python
df = pd.DataFrame({
    "department": ["Sales", "IT", "HR", "Sales", "IT"]
})

print(df["department"].unique())
```

Output:

text

```text
['Sales' 'IT' 'HR']
```

### Examples

python

```python
# Get unique department names
df["department"].unique()

# Get unique city names
df["city"].unique()

# Convert unique values into a list
df["department"].unique().tolist()
```

**Important:** `unique()` preserves the order in which values first appear. It is a Series method, not a DataFrame method.

## 6\. duplicated() – Identify Duplicate Records

The `duplicated()` method identifies duplicate rows or values.

It returns Boolean values:

- `True`: The row or value is considered a duplicate.
- `False`: The row or value is not considered a duplicate.

### Example: Identify Duplicate Rows

python

```python
df = pd.DataFrame({
    "name": ["John", "Mary", "John", "David"],
    "age": [25, 30, 25, 28]
})

print(df.duplicated())
```

Output:

text

```text
0    False
1    False
2     True
3    False
dtype: bool
```

### Common Parameters

| Parameter | Description |
| --- | --- |
| `subset` | Specifies which columns to consider when identifying duplicates. |
| `keep='first'` | Marks subsequent duplicates as True (default). |
| `keep='last'` | Marks previous duplicates as True, keeping the last occurrence. |
| `keep=False` | Marks all duplicated occurrences as True. |

### Examples

python

```python
# Identify duplicate rows
df.duplicated()

# Count duplicate rows
df.duplicated().sum()

# Identify duplicates based on one column
df.duplicated(subset=["name"])

# Identify duplicates based on multiple columns
df.duplicated(subset=["name", "age"])

# Mark all duplicate occurrences
df.duplicated(keep=False)

# Display duplicate records
df[df.duplicated(keep=False)]
```

### Remove Duplicate Records

Use `drop_duplicates()` to remove duplicate rows.

python

```python
# Keep the first occurrence
df = df.drop_duplicates()

# Remove duplicates based on selected columns
df = df.drop_duplicates(subset=["name"])

# Keep the last occurrence
df = df.drop_duplicates(keep="last")
```

**Important:** `duplicated()` identifies duplicate records but does not remove them. Use `drop_duplicates()` when you want to remove duplicates.

## 7\. corr() – Calculate Correlations

The `corr()` method calculates the correlation between numerical columns in a DataFrame.

Correlation measures the strength and direction of the relationship between two numerical variables.

### Example

python

```python
df = pd.DataFrame({
    "age": [20, 25, 30, 35, 40],
    "salary": [2000, 2500, 3000, 3500, 4000],
    "expenses": [1500, 1800, 2200, 2100, 2800]
})

correlation = df.corr()

print(correlation)
```

### Understanding Correlation Values

Correlation coefficients range from -1 to +1.

| Correlation | Interpretation |
| --- | --- |
| +1.0 | Perfect positive correlation. |
| +0.7 to +0.9 | Strong positive correlation. |
| +0.3 to +0.6 | Moderate positive correlation. |
| Around 0 | Weak or no linear correlation. |
| -0.3 to -0.6 | Moderate negative correlation. |
| -0.7 to -0.9 | Strong negative correlation. |
| -1.0 | Perfect negative correlation. |

### Common Parameters

| Parameter | Description |
| --- | --- |
| `method='pearson'` | Measures linear correlation (default). |
| `method='kendall'` | Measures rank correlation using Kendall's tau. |
| `method='spearman'` | Measures rank correlation using Spearman's rho. |
| `min_periods` | Minimum number of observations required for a valid result. |
| `numeric_only=True` | Uses numeric columns only (supported in current pandas versions). |

### Examples

python

```python
# Calculate Pearson correlation
df.corr()

# Calculate Spearman correlation
df.corr(method="spearman")

# Calculate Kendall correlation
df.corr(method="kendall")

# Calculate correlation for numeric columns
df.corr(numeric_only=True)

# Calculate correlation between two columns
df["age"].corr(df["salary"])
```

**Important:** Correlation does not establish causation. A strong correlation does not necessarily mean that one variable causes changes in another.

## 8\. Practical Example: Analyze a Dataset

The following example combines the five methods to explore a dataset.

python

```python
import pandas as pd

df = pd.DataFrame({
    "department": [
        "Sales", "IT", "HR", "Sales",
        "IT", "Sales", "HR", "IT"
    ],
    "age": [25, 30, 28, 35, 40, 25, 32, 30],
    "salary": [3000, 4500, 3500, 5000, 6000, 3000, 4000, 4500]
})

# 1. Count department frequencies
print(df["department"].value_counts())

# 2. Count unique departments
print(df["department"].nunique())

# 3. Retrieve unique department names
print(df["department"].unique())

# 4. Identify duplicate rows
print(df.duplicated().sum())

# 5. Calculate numerical correlations
print(df.corr(numeric_only=True))
```

## 9\. When to Use Each Method

| Method | When to Use It |
| --- | --- |
| `value_counts()` | When you want to know how frequently each category or value appears. |
| `nunique()` | When you want to know how many distinct values exist. |
| `unique()` | When you want to retrieve all distinct values. |
| `duplicated()` | When you want to identify repeated records. |
| `corr()` | When you want to investigate relationships between numerical variables. |

## 10\. Important Notes

- `value_counts()` and `unique()` are primarily Series methods.
- `nunique()` and `duplicated()` can be used with both Series and DataFrames.
- `corr()` calculates relationships between numerical variables by default.
- Missing values are generally excluded from these calculations unless the relevant parameters specify otherwise.
- `duplicated()` does not delete records; use `drop_duplicates()` to remove them.
- Correlation measures association, not causation.
- Always investigate unusual frequencies, duplicate records, and unexpected correlations before drawing conclusions.

## Additional Resources

- [Pandas Series API Reference](<https://pandas.pydata.org/docs/reference/series.html>)
- [Pandas DataFrame API Reference](<https://pandas.pydata.org/docs/reference/frame.html>)
- [Pandas Descriptive Statistics](<https://pandas.pydata.org/docs/user_guide/basics.html>)

Add this link to your `pandas-methods-reference.md`:

markdown

```markdown
| [Analyze Values](pandas-value-analysis.md) | `value_counts()`, `nunique()`, `unique()`, `duplicated()`, `corr()` | Examine frequencies, uniqueness, duplicates, and relationships. |
```
