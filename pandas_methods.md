# Pandas Methods Documentation

Pandas is a Python library for data manipulation and analysis. Its methods help you import data, inspect datasets, clean missing values, transform columns, combine tables, perform calculations, and prepare data for visualization.

## Official Documentation

- [General Functions](<https://pandas.pydata.org/pandas-docs/stable/reference/general_functions.html>)
- [Official pandas documentation](<https://pandas.pydata.org/docs/>)
- [Complete API reference](<https://pandas.pydata.org/docs/reference/index.html>)
- [DataFrame methods and attributes](<https://pandas.pydata.org/docs/reference/frame.html>)
- [Series methods and attributes](<https://pandas.pydata.org/docs/reference/series.html>)
- [Input/output functions](<https://pandas.pydata.org/docs/reference/io.html>)

## Common Pandas Methods by Category

| Category | Common Methods | Purpose |
| --- | --- | --- |
| Import data | `pd.read_csv()`, `pd.read_excel()`, `pd.read_json()`, `pd.read_sql()` | Load data from files and databases. |
| Inspect data | `head()`, `tail()`, `sample()`, `info()`, `describe()` | Preview and summarize data. |
| Select data | `loc[]`, `iloc[]`, `query()`, `filter()` | Select rows and columns. |
| Clean data | `drop()`, `dropna()`, `fillna()`, `replace()`, `drop_duplicates()` | Remove or correct unwanted data. |
| Data types | `astype()`, `convert_dtypes()`, `pd.to_numeric()`, `pd.to_datetime()` | Convert data into appropriate types. |
| Sort data | `sort_values()`, `sort_index()`, `nlargest()`, `nsmallest()` | Order and rank records. |
| Calculate statistics | `mean()`, `median()`, `mode()`, `sum()`, `min()`, `max()`, `std()`, `var()` | Calculate descriptive statistics. |
| Group data | `groupby()`, `agg()`, `aggregate()`, `transform()` | Summarize and transform groups. |
| Combine data | `merge()`, `join()`, `concat()` | Combine datasets. |
| Reshape data | `pivot()`, `pivot_table()`, `melt()`, `stack()`, `unstack()` | Change the layout of datasets. |
| Analyze values | `value_counts()`, `nunique()`, `unique()`, `duplicated()`, `corr()` | Examine frequencies, uniqueness, and relationships. |
| Handle missing values | `isna()`, `notna()`, `dropna()`, `fillna()`, `interpolate()` | Identify and handle missing data. |
| Work with strings | `str.lower()`, `str.upper()`, `str.strip()`, `str.replace()`, `str.contains()` | Clean and search text. |
| Work with dates | `dt.year`, `dt.month`, `dt.day`, `resample()`, `shift()` | Extract date components and analyze time series. |
| Visualize data | `plot()`, `hist()`, `boxplot()` | Create basic charts. |
| Export data | `to_csv()`, `to_excel()`, `to_json()`, `to_sql()`, `to_parquet()` | Save results in different formats. |

**Note:** `loc` and `iloc` are indexers rather than methods. The `dt` accessor provides access to datetime properties and methods on Series. Functions such as `pd.read_csv()` and `pd.to_datetime()` are top-level pandas functions rather than DataFrame methods.

## Detailed Documentation by Topic

### 1\. Data Import and Export

- [Input/output functions](<https://pandas.pydata.org/docs/reference/io.html>)

Common functions and methods:

```
import pandas as pd

df = pd.read_csv("data.csv")
df = pd.read_excel("data.xlsx")
df = pd.read_json("data.json")

df.to_csv("output.csv", index=False)
df.to_excel("output.xlsx", index=False)
```

### 2\. Data Inspection

- [DataFrame reference](<https://pandas.pydata.org/docs/reference/frame.html>)

```
df.head()
df.tail()
df.sample(5)
df.info()
df.describe()
df.shape
df.columns
df.dtypes
```

### 3\. Data Cleaning

- [Working with missing data](<https://pandas.pydata.org/docs/user_guide/missing_data.html>)

```
df.isna()
df.isna().sum()
df.dropna()
df.fillna(0)
df.drop_duplicates()
df.rename(columns={"old_name": "new_name"})
df.astype({"age": "int64"})
```

### 4\. Data Selection and Filtering

- [Indexing and selecting data](<https://pandas.pydata.org/docs/user_guide/indexing.html>)

```
df["sales"]
df[["sales", "profit"]]
df.loc[0:5, ["sales", "profit"]]
df.iloc[0:5, 0:2]
df.query("sales > 1000")
```

### 5\. Grouping and Aggregation

- [GroupBy user guide](<https://pandas.pydata.org/docs/user_guide/groupby.html>)

```
df.groupby("category")["sales"].sum()

df.groupby("category").agg({
    "sales": "sum",
    "profit": "mean"
})
```

### 6\. Combining and Reshaping Data

- [Merge, join, and concatenate](<https://pandas.pydata.org/docs/user_guide/merging.html>)
- [Reshaping and pivot tables](<https://pandas.pydata.org/docs/user_guide/reshaping.html>)

```
merged_df = pd.merge(df1, df2, on="id")
combined_df = pd.concat([df1, df2], ignore_index=True)

pivot_df = df.pivot_table(
    index="category",
    values="sales",
    aggfunc="sum"
)
```

### 7\. String and Date Operations

- [Working with text data](<https://pandas.pydata.org/docs/user_guide/text.html>)
- [Time series and date functionality](<https://pandas.pydata.org/docs/user_guide/timeseries.html>)

```
df["name"] = df["name"].str.strip().str.lower()

df["date"] = pd.to_datetime(df["date"])
df["year"] = df["date"].dt.year
df["month"] = df["date"].dt.month
```

### 8\. Data Visualization

- [Visualization guide](<https://pandas.pydata.org/docs/user_guide/visualization.html>)

```
df["sales"].plot(kind="hist")
df.plot(x="sales", y="profit", kind="scatter")
df.boxplot(column="sales")
```

## Additional Official Resources

- [Pandas user guide](<https://pandas.pydata.org/docs/user_guide/index.html>)
- [Pandas API reference](<https://pandas.pydata.org/docs/reference/index.html>)
- [What's new in pandas](<https://pandas.pydata.org/docs/whatsnew/index.html>)

## Important Notes

- The examples assume that `df` is an existing pandas DataFrame.
- Some operations return a new DataFrame or Series rather than modifying the original object.
- Check the official documentation for the parameters, return values, and behavior of each method.
- The available methods and behavior may vary between pandas versions.

- [Pandas Methods Documentation](data-analysis/pandas-methods.md)
```
