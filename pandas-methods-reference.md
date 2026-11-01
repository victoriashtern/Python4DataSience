

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
| Import Data | `pd.read_csv()`, `pd.read_excel()`, `pd.read_json()`, `pd.read_sql()` | Load data from files and databases. |
| Inspect Data | `df.head()`, `df.tail()`, `df.sample()`, `df.info()`, `df.describe()`, `df.size`, `df.shape` | Preview and summarize data. |
| Select Data | `loc[]`, `iloc[]`, `query()`, `filter()` | Select rows and columns. |
| Data Cleaning | `drop()`, `dropna()`, `fillna()`, `replace()`, `drop_duplicates()` | Remove or correct unwanted data. |
| Data Types | `astype()`, `convert_dtypes()`, `pd.to_numeric()`, `pd.to_datetime()` | Convert data into appropriate types. |
| Sort Data | `sort_values()`, `sort_index()`, `nlargest()`, `nsmallest()` | Order and rank records. |
| Calculate Statistics | `mean()`, `median()`, `mode()`, `sum()`, `min()`, `max()`, `std()`, `var()` | Calculate descriptive statistics. |
| Group Data | `groupby()`, `agg()`, `aggregate()`, `transform()` | Summarize and transform groups. |
| Combine Data | `merge()`, `join()`, `concat()` | Combine datasets. |
| Reshape Data | `pivot()`, `pivot_table()`, `melt()`, `stack()`, `unstack()` | Change the layout of datasets. |
| Index Management | `reset_index()`, `set_index()`, `reindex()` | Set, reset, and reorganize DataFrame indexes. |
| Analyze Values | `value_counts()`, `nunique()`, `unique()`, `duplicated()`, `corr()` | Examine frequencies, uniqueness, and relationships. |
| Handle Missing Values | `isna()`, `notna()`, `dropna()`, `fillna()`, `interpolate()` | Identify and handle missing data. |
| Work with Strings | `str.lower()`, `str.upper()`, `str.strip()`, `str.replace()`, `str.contains()` | Clean and search text. |
| Work with Dates | `dt.year`, `dt.month`, `dt.day`, `resample()`, `shift()` | Extract date components and analyze time series. |
| Visualize Data | `plot()`, `hist()`, `boxplot()` | Create basic charts. |
| Export Data | `to_csv()`, `to_excel()`, `to_json()`, `to_sql()`, `to_parquet()` | Save results in different formats. |

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

### 3.2. Data Inspection

Documentation: [DataFrame Reference](<https://pandas.pydata.org/docs/reference/frame.html>)

python

```python
# Preview data
df.head()
df.tail()
df.sample(5)

# Inspect DataFrame information
df.info()
df.describe()

# Examine DataFrame attributes
df.shape
df.size
df.columns
df.dtypes
```

### 3.3. Data Cleaning

Documentation: [Working with Missing Data](<https://pandas.pydata.org/docs/user_guide/missing_data.html>)

python

```python
# Identify missing values
df.isna()
df.isna().sum()

# Remove missing values
df.dropna()

# Replace missing values
df.fillna(0)

# Remove duplicates
df.drop_duplicates()

# Rename columns
df.rename(columns={"old_name": "new_name"})

# Change data types
df.astype({"age": "int64"})
```

### 3.4. Data Selection and Filtering

Documentation: [Indexing and Selecting Data](<https://pandas.pydata.org/docs/user_guide/indexing.html>)

python

```python
# Select columns
df["sales"]
df[["sales", "profit"]]

# Select rows and columns
df.loc[0:5, ["sales", "profit"]]
df.iloc[0:5, 0:2]

# Filter records
df.query("sales > 1000")
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

### 3.7. Index Management

Documentation: [DataFrame Reference](<https://pandas.pydata.org/docs/reference/frame.html>)

Index management methods allow you to set, reset, and reorganize the index of a DataFrame.

#### reset\_index()

Resets the DataFrame index to the default integer index.

python

```python
df.reset_index()
```

By default, the original index is added as a new column.

**Discard the original index:**

python

```python
df.reset_index(drop=True)
```

**Modify the original DataFrame:**

python

```python
df.reset_index(drop=True, inplace=True)
```

**Example:**

python

```python
import pandas as pd

df = pd.DataFrame({
    "name": ["John", "Mary", "David"],
    "age": [25, 30, 28]
}, index=[10, 20, 30])

# Reset index and discard the original index
df = df.reset_index(drop=True)

print(df)
```

Output:

text

```text
    name  age
0   John   25
1   Mary   30
2  David   28
```

#### Related Index Management Methods

| Method | Purpose |
| --- | --- |
| `df.reset_index()` | Resets the index and preserves the old index as a column. |
| `df.reset_index(drop=True)` | Resets the index and discards the old index. |
| `df.set_index("column")` | Sets a column as the DataFrame index. |
| `df.reindex()` | Conforms the DataFrame to a new index. |
| `df.rename_axis()` | Changes the name of the index or column axis. |

### 3.8. String and Date Operations

Documentation:

- [Working with Text Data](<https://pandas.pydata.org/docs/user_guide/text.html>)
- [Time Series and Date Functionality](<https://pandas.pydata.org/docs/user_guide/timeseries.html>)

python

```python
# Clean text
df["name"] = df["name"].str.strip().str.lower()

# Convert dates
df["date"] = pd.to_datetime(df["date"])

# Extract date components
df["year"] = df["date"].dt.year
df["month"] = df["date"].dt.month
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

## 4\. Important Notes

- The examples assume that `df` is an existing pandas DataFrame.
- Some operations return a new DataFrame or Series rather than modifying the original object.
- Use `inplace=True` when an operation supports it and you want to modify the existing DataFrame directly.
- `reset_index()` is useful after filtering, grouping, or sorting when you want to reorganize the row index.
- Check the official documentation for the parameters, return values, and behavior of each method.
- Available methods and behavior may vary between pandas versions.
