
# Pandas Series & DataFrame — Reference Guide

**Python · Pandas · Data Structures**

A quick-reference guide to understanding, creating, inspecting, selecting, and converting Pandas Series and DataFrames.

---

## 1. Pandas Series

### Definition

A **Series** is a one-dimensional labelled data structure containing values and an associated index.

Full class name:

```python
pandas.core.series.Series
```

### Create a Series

```python
import pandas as pd

s = pd.Series([9.4, 10.0, 9.5, 11.0])
```

Create a Series with custom index labels:

```python
s = pd.Series(
    [9.4, 10.0, 9.5],
    index=['A', 'B', 'C'],
    name='alcohol'
)
```

### Series Structure

| Index | Value |
|---|---:|
| A | 9.4 |
| B | 10.0 |
| C | 9.5 |

**Dimension:** 1-dimensional

### Series Attributes

| Attribute | Description |
|---|---|
| `s.index` | Returns index labels |
| `s.values` | Returns underlying values |
| `s.dtype` | Returns data type |
| `s.shape` | Returns dimensions |
| `s.size` | Returns number of elements |
| `s.name` | Returns Series name |
| `s.ndim` | Returns number of dimensions |

### Series Methods

| Method | Description |
|---|---|
| `s.head()` | First five observations |
| `s.tail()` | Last five observations |
| `s.describe()` | Descriptive statistics |
| `s.mean()` | Mean |
| `s.median()` | Median |
| `s.std()` | Standard deviation |
| `s.min()` | Minimum |
| `s.max()` | Maximum |
| `s.sum()` | Sum |
| `s.count()` | Number of non-missing values |
| `s.unique()` | Unique values |
| `s.nunique()` | Number of unique values |
| `s.value_counts()` | Frequency of each value |
| `s.isnull()` | Identifies missing values |
| `s.dropna()` | Removes missing values |
| `s.fillna()` | Replaces missing values |
| `s.sort_values()` | Sorts by values |
| `s.sort_index()` | Sorts by index |

### Accessing Series Values

```python
s.iloc[0]       # First value by position
s.iloc[-1]      # Last value by position
s.loc['A']      # Value with index label A
s[0:2]          # Slicing by position
```

---

## 2. Pandas DataFrame

### Definition

A **DataFrame** is a two-dimensional labelled data structure consisting of rows and columns.

Full class name:

```python
pandas.core.frame.DataFrame
```

### Create a DataFrame

```python
data = pd.DataFrame({
    'alcohol': [9.4, 10.0, 9.5],
    'quality': [5, 6, 5],
    'color': ['red', 'white', 'red']
})
```

### DataFrame Structure

| Index | alcohol | quality | color |
|---:|---:|---:|---|
| 0 | 9.4 | 5 | red |
| 1 | 10.0 | 6 | white |
| 2 | 9.5 | 5 | red |

**Dimension:** 2-dimensional

### DataFrame Attributes

| Attribute | Description |
|---|---|
| `data.index` | Row labels |
| `data.columns` | Column names |
| `data.dtypes` | Data types of columns |
| `data.shape` | Number of rows and columns |
| `data.size` | Total number of elements |
| `data.values` | Underlying values |
| `data.ndim` | Number of dimensions |
| `data.T` | Transposed DataFrame |
| `data.empty` | Checks whether DataFrame is empty |

### DataFrame Methods

| Method | Description |
|---|---|
| `data.head()` | First five rows |
| `data.tail()` | Last five rows |
| `data.info()` | Structural information |
| `data.describe()` | Descriptive statistics |
| `data.sample()` | Random observations |
| `data.count()` | Non-missing values per column |
| `data.isnull()` | Identifies missing values |
| `data.dropna()` | Removes missing values |
| `data.fillna()` | Replaces missing values |
| `data.drop()` | Removes rows or columns |
| `data.rename()` | Renames rows or columns |
| `data.sort_values()` | Sorts by column values |
| `data.sort_index()` | Sorts by index |
| `data.duplicated()` | Identifies duplicate rows |
| `data.drop_duplicates()` | Removes duplicate rows |
| `data.corr()` | Calculates correlations |
| `data.groupby()` | Groups observations |
| `data.merge()` | Combines DataFrames |

---

## 3. Series vs DataFrame

| Characteristic | Series | DataFrame |
|---|---|---|
| Dimensions | 1D | 2D |
| Structure | Single sequence | Rows and columns |
| Index | Yes | Yes |
| Column names | No | Yes |
| Data types | One overall dtype | Multiple possible dtypes |
| Class | `pandas.core.series.Series` | `pandas.core.frame.DataFrame` |
| Shape example | `(100,)` | `(100, 5)` |

### Selecting Columns

```python
# Returns a Series
data['alcohol']

# Returns a DataFrame
data[['alcohol']]

# Returns a DataFrame with multiple columns
data[['alcohol', 'quality']]
```

**Important distinction:**

- `data['alcohol']` → Series
- `data[['alcohol']]` → DataFrame

---

## 4. Converting Series to DataFrame

### Method 1: `.to_frame()`

```python
s = data['alcohol']

df = s.to_frame()
```

### Method 2: `.to_frame()` with Column Name

```python
df = s.to_frame(name='alcohol')
```

### Method 3: Double Square Brackets

```python
df = data[['alcohol']]
```

### Method 4: `pd.DataFrame()`

```python
df = pd.DataFrame(s)
```

### Verify Conversion

```python
type(s)
# pandas.core.series.Series

type(df)
# pandas.core.frame.DataFrame
```

### Compare Dimensions

```python
s.shape
# (100,)

df.shape
# (100, 1)
```

| Structure | Shape | Meaning |
|---|---|---|
| Series | `(100,)` | 100 values, one-dimensional |
| DataFrame | `(100, 1)` | 100 rows and one column |

**Important:** Conversion changes the structure, not the underlying values.

---

## 5. Converting DataFrame to Series

Select a single column using one pair of square brackets.

```python
s = data['alcohol']
```

Alternatively:

```python
s = data[['alcohol']].squeeze()
```

The `.squeeze()` method removes dimensions of length one, returning a Series when the DataFrame has one column.

---

## 6. When to Use Series vs DataFrame

| Situation | Recommended Structure |
|---|---|
| Analysing one variable | Series |
| Calculating one column's mean | Series |
| Calculating missing values in one column | Series |
| Selecting multiple features | DataFrame |
| Combining multiple columns | DataFrame |
| Merging datasets | DataFrame |
| Preparing ML input features (`X`) | DataFrame |
| Preparing a single ML target (`y`) | Series (commonly) |

### Machine Learning Example

```python
# Independent variables
X = data[['alcohol', 'fixed_acidity', 'sulphates']]

# Target variable
y = data['quality']
```

- `X` is a DataFrame (2D).
- `y` is a Series (1D).

---

## 7. Working with Your Wine Dataset

### Load the Dataset

```python
data = pd.read_csv('wine_red.csv')
```

### Inspect the Dataset

```python
data.head()
data.shape
data.info()
data.describe()
data.dtypes
```

### Select a Series

```python
alcohol = data['alcohol']
```

### Select a DataFrame

```python
features = data[['alcohol', 'fixed_acidity', 'density']]
```

### Calculate Statistics

```python
alcohol.mean()
alcohol.median()
alcohol.std()
alcohol.min()
alcohol.max()
```

### Select Features and Target

```python
X = data.drop(columns='quality')
y = data['quality']
```

---

## 8. Important Terminology

| Term | Meaning |
|---|---|
| Series | One-dimensional labelled data structure |
| DataFrame | Two-dimensional labelled data structure |
| Index | Labels identifying rows or observations |
| Columns | Variables in a DataFrame |
| Values | Actual data stored |
| `dtype` | Data type of a Series |
| `dtypes` | Data types of DataFrame columns |
| `shape` | Dimensions of an object |
| `ndim` | Number of dimensions |
| Attribute | Information associated with an object |
| Method | Function associated with an object |
| Class | Blueprint for creating objects |
| Object | Instance of a class |

---

## 9. Quick Syntax Reference

| Operation | Syntax |
|---|---|
| Create Series | `pd.Series([...])` |
| Create DataFrame | `pd.DataFrame({...})` |
| Select Series | `data['column']` |
| Select DataFrame | `data[['column']]` |
| Convert Series to DataFrame | `s.to_frame()` |
| Convert DataFrame to Series | `data['column']` |
| Check object type | `type(data)` |
| Check dimensions | `data.shape` |
| Check data types | `data.dtypes` |
| Get column names | `data.columns` |
| Get index | `data.index` |
| First five rows | `data.head()` |
| Summary statistics | `data.describe()` |

---

## 10. Key Takeaways

1. A Series is a one-dimensional labelled data structure.
2. A DataFrame is a two-dimensional labelled data structure.
3. `pandas.core.series.Series` is the full class name of a Series.
4. `pandas.core.frame.DataFrame` is the full class name of a DataFrame.
5. Use one pair of square brackets to select a Series.
6. Use double square brackets to select a DataFrame.
7. Use `.to_frame()` to convert a Series into a DataFrame.
8. Use `.squeeze()` to remove single-dimensional axes where appropriate.
9. Use Series for individual variables and DataFrames for multiple variables.
10. In machine learning, `X` is generally two-dimensional, while a single target `y` is generally one-dimensional.

---

**Reference scope:** Pandas data structures, selection, attributes, methods, conversion, and machine learning preparation.

**Examples:** Standard Pandas syntax.
````

Suggested filename: `pandas_series_dataframe.md`
