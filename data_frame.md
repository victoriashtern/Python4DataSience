
# Pandas DataFrame Methods (Latest Reference)

Pandas DataFrame methods provide functionality for inspecting, selecting, cleaning, transforming, analyzing, combining, and reshaping tabular data.

This reference covers commonly used DataFrame methods, attributes, indexers, and related pandas functions, based on the official **pandas 3.1.0 API documentation**.

- Official DataFrame API Reference
- [DataFrame Class Documentation](<https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.html>)
- [Complete pandas API Reference](<https://pandas.pydata.org/docs/reference/index.html>)

## 1\. Creating DataFrames

| Function / Attribute | Description | Example |
| --- | --- | --- |
| `pd.DataFrame()` | Creates a DataFrame. | `pd.DataFrame(data)` |
| `pd.Series()` | Creates a Series. | `pd.Series([10, 20, 30])` |
| `from_dict()` | Creates a DataFrame from a dictionary. | `pd.DataFrame.from_dict(data)` |
| `from_records()` | Creates a DataFrame from records. | `pd.DataFrame.from_records(records)` |
| `copy()` | Creates a copy of a DataFrame. | `df.copy()` |

Example:

python

```python
import pandas as pd

df = pd.DataFrame({
    "Name": ["Alice", "Bob", "Charlie"],
    "Age": [25, 30, 35],
    "Salary": [40000, 50000, 60000]
})
```

## 2\. Inspecting and Viewing Data

| Method / Attribute | Description | Example |
| --- | --- | --- |
| `head()` | Returns the first 5 rows by default. | `df.head()` |
| `head(n)` | Returns the first n rows. | `df.head(10)` |
| `tail()` | Returns the last 5 rows by default. | `df.tail()` |
| `tail(n)` | Returns the last n rows. | `df.tail(10)` |
| `sample()` | Returns randomly selected rows. | `df.sample(5)` |
| `info()` | Displays column names, data types, and non-null counts. | `df.info()` |
| `describe()` | Generates descriptive statistics. | `df.describe()` |
| `shape` | Returns the number of rows and columns. | `df.shape` |
| `size` | Returns the total number of elements. | `df.size` |
| `ndim` | Returns the number of dimensions. | `df.ndim` |
| `empty` | Checks whether the DataFrame has any elements. | `df.empty` |
| `axes` | Returns row and column axis labels. | `df.axes` |
| `columns` | Returns column labels. | `df.columns` |
| `index` | Returns row index labels. | `df.index` |
| `dtypes` | Returns column data types. | `df.dtypes` |
| `memory_usage()` | Reports memory usage by column. | `df.memory_usage(deep=True)` |
| `select_dtypes()` | Selects columns based on data types. | `df.select_dtypes(include="number")` |
| `first_valid_index()` | Returns the first index containing a non-missing value. | `df.first_valid_index()` |
| `last_valid_index()` | Returns the last index containing a non-missing value. | `df.last_valid_index()` |

## 3\. Selecting and Accessing Data

| Method / Indexer | Description | Example |
| --- | --- | --- |
| `loc[]` | Selects rows and columns by labels. | `df.loc[0, "Age"]` |
| `iloc[]` | Selects rows and columns by integer positions. | `df.iloc[0, 1]` |
| `at[]` | Accesses a single value using labels. | `df.at[0, "Age"]` |
| `iat[]` | Accesses a single value using integer positions. | `df.iat[0, 1]` |
| `get()` | Retrieves a column or returns a default if missing. | `df.get("Age")` |
| `filter()` | Selects rows or columns by labels or patterns. | `df.filter(items=["Age", "Salary"])` |
| `query()` | Filters rows using a Boolean expression. | `df.query("Age > 30")` |
| `isin()` | Checks whether values belong to a specified set. | `df["Age"].isin([20, 30])` |
| `where()` | Replaces values where a condition is false. | `df.where(df > 0)` |
| `mask()` | Replaces values where a condition is true. | `df.mask(df < 0)` |
| `xs()` | Selects a cross-section from a DataFrame. | `df.xs("A", level="Category")` |
| `take()` | Selects rows or columns by integer positions. | `df.take([0, 2])` |
| `select_dtypes()` | Selects columns with specified data types. | `df.select_dtypes(include="number")` |

**Note:** `loc`, `iloc`, `at`, and `iat` are indexers rather than methods.

## 4\. Adding, Modifying, and Removing Data

| Method | Description | Example |
| --- | --- | --- |
| `assign()` | Adds or modifies columns and returns a DataFrame. | `df.assign(Tax=df["Salary"] * 0.1)` |
| `insert()` | Inserts a column at a specified position. | `df.insert(1, "Bonus", 100)` |
| `pop()` | Removes and returns a column. | `df.pop("Age")` |
| `drop()` | Removes specified rows or columns. | `df.drop(columns=["Age"])` |
| `rename()` | Renames rows or columns. | `df.rename(columns={"Age": "Years"})` |
| `set_axis()` | Sets row or column labels. | `df.set_axis(["A", "B", "C"], axis=1)` |
| `replace()` | Replaces specified values. | `df.replace(0, pd.NA)` |
| `update()` | Updates values using another DataFrame. | `df.update(other_df)` |
| `eval()` | Evaluates expressions involving DataFrame columns. | `df.eval("Profit = Sales - Cost")` |
| `set_flags()` | Changes DataFrame behavior flags. | `df.set_flags(allows_duplicate_labels=False)` |
| `isetitem()` | Sets a column using its integer position. | `df.isetitem(0, [10, 20, 30])` |
| `add_prefix()` | Adds a prefix to row or column labels. | `df.add_prefix("col_")` |
| `add_suffix()` | Adds a suffix to row or column labels. | `df.add_suffix("_data")` |

## 5\. Cleaning Data and Handling Missing Values

| Method | Description | Example |
| --- | --- | --- |
| `isna()` | Identifies missing values. | `df.isna()` |
| `isnull()` | Alias for `isna()`. | `df.isnull()` |
| `notna()` | Identifies non-missing values. | `df.notna()` |
| `notnull()` | Alias for `notna()`. | `df.notnull()` |
| `dropna()` | Removes rows or columns containing missing values. | `df.dropna()` |
| `fillna()` | Fills missing values. | `df.fillna(0)` |
| `ffill()` | Fills missing values using previous valid values. | `df.ffill()` |
| `bfill()` | Fills missing values using subsequent valid values. | `df.bfill()` |
| `interpolate()` | Estimates missing values using interpolation. | `df.interpolate()` |
| `drop_duplicates()` | Removes duplicate rows. | `df.drop_duplicates()` |
| `duplicated()` | Identifies duplicate rows. | `df.duplicated()` |
| `convert_dtypes()` | Converts columns to suitable nullable data types. | `df.convert_dtypes()` |
| `astype()` | Converts columns to specified data types. | `df.astype({"Age": "int64"})` |

## 6\. Sorting and Ranking

| Method | Description | Example |
| --- | --- | --- |
| `sort_values()` | Sorts rows by column values. | `df.sort_values("Age")` |
| `sort_index()` | Sorts rows or columns by labels. | `df.sort_index()` |
| `nlargest()` | Returns rows with the largest values. | `df.nlargest(5, "Salary")` |
| `nsmallest()` | Returns rows with the smallest values. | `df.nsmallest(5, "Salary")` |
| `rank()` | Computes numerical ranks. | `df["Salary"].rank()` |

Additional examples:

python

```python
df.sort_values("Salary", ascending=False)

df.sort_values(
    ["Department", "Salary"],
    ascending=[True, False]
)

df["Salary_Rank"] = df["Salary"].rank(
    ascending=False
)
```

## 7\. Statistical and Aggregation Methods

| Method | Description | Example |
| --- | --- | --- |
| `sum()` | Calculates the sum. | `df.sum(numeric_only=True)` |
| `prod()` | Calculates the product. | `df.prod(numeric_only=True)` |
| `mean()` | Calculates the arithmetic mean. | `df.mean(numeric_only=True)` |
| `median()` | Calculates the median. | `df.median(numeric_only=True)` |
| `mode()` | Returns the most frequent value or values. | `df["Age"].mode()` |
| `min()` | Returns minimum values. | `df.min(numeric_only=True)` |
| `max()` | Returns maximum values. | `df.max(numeric_only=True)` |
| `count()` | Counts non-missing values. | `df.count()` |
| `std()` | Calculates standard deviation. | `df.std(numeric_only=True)` |
| `var()` | Calculates variance. | `df.var(numeric_only=True)` |
| `sem()` | Calculates standard error of the mean. | `df.sem(numeric_only=True)` |
| `quantile()` | Calculates specified quantiles. | `df.quantile(0.5, numeric_only=True)` |
| `nunique()` | Counts unique values per column. | `df.nunique()` |
| `value_counts()` | Counts distinct row combinations. | `df.value_counts()` |
| `corr()` | Calculates pairwise correlations. | `df.corr(numeric_only=True)` |
| `corrwith()` | Calculates correlations with another object. | `df.corrwith(other_df)` |
| `cov()` | Calculates pairwise covariance. | `df.cov(numeric_only=True)` |
| `skew()` | Measures distribution asymmetry. | `df.skew(numeric_only=True)` |
| `kurt()` | Calculates distribution kurtosis. | `df.kurt(numeric_only=True)` |
| `agg()` | Applies one or more aggregation functions. | `df.agg(["min", "max"])` |
| `aggregate()` | Alias for `agg()`. | `df.aggregate(["mean", "sum"])` |
| `all()` | Checks whether all values satisfy a condition. | `df.all()` |
| `any()` | Checks whether any values satisfy a condition. | `df.any()` |
| `round()` | Rounds numerical values. | `df.round(2)` |

**Note:** `Series.value_counts()` counts distinct values in a Series, whereas `DataFrame.value_counts()` counts distinct row combinations.

## 8\. Applying Functions and Grouping

| Method | Description | Example |
| --- | --- | --- |
| `apply()` | Applies a function along rows or columns. | `df.apply(sum, axis=0)` |
| `map()` | Applies a function elementwise to DataFrame values. | `df.map(lambda x: x)` |
| `transform()` | Applies a function while preserving the shape of the DataFrame. | `df.transform(lambda x: x * 2)` |
| `pipe()` | Passes the DataFrame to a function. | `df.pipe(my_function)` |
| `groupby()` | Groups rows for aggregation and analysis. | `df.groupby("Department")["Salary"].mean()` |
| `groupby().agg()` | Aggregates grouped data. | `df.groupby("Department").agg({"Salary": "mean"})` |
| `groupby().transform()` | Calculates group-based values aligned with original rows. | `df.groupby("Department")["Salary"].transform("mean")` |
| `groupby().filter()` | Filters groups based on a condition. | `df.groupby("Department").filter(lambda x: len(x) > 5)` |
| `groupby().size()` | Counts rows in each group. | `df.groupby("Department").size()` |
| `resample()` | Groups time-series data into time intervals. | `df.resample("ME").sum()` |

Example:

python

```python
df.groupby("Department").agg({
    "Salary": ["mean", "max", "min"],
    "Age": "mean"
})
```

## 9\. Combining DataFrames

| Method / Function | Description | Example |
| --- | --- | --- |
| `merge()` | Combines DataFrames using database-style joins. | `pd.merge(df1, df2, on="ID")` |
| `join()` | Joins DataFrames, usually by index. | `df1.join(df2)` |
| `concat()` | Concatenates DataFrames along rows or columns. | `pd.concat([df1, df2])` |
| `combine()` | Combines DataFrames using a specified function. | `df1.combine(df2, max)` |
| `combine_first()` | Fills missing values using another DataFrame. | `df1.combine_first(df2)` |
| `compare()` | Shows differences between similarly labeled DataFrames. | `df1.compare(df2)` |
| `align()` | Aligns row and column labels between objects. | `df1.align(df2)` |

## 10\. Reshaping DataFrames

| Method / Attribute | Description | Example |
| --- | --- | --- |
| `pivot()` | Reshapes data using unique index-column combinations. | `df.pivot(index="Date", columns="City", values="Sales")` |
| `pivot_table()` | Creates a summarized pivot table. | `df.pivot_table(values="Sales", index="City", aggfunc="sum")` |
| `melt()` | Converts wide-format data into long-format data. | `df.melt(id_vars=["ID"])` |
| `transpose()` | Swaps rows and columns. | `df.transpose()` |
| `T` | Returns the transpose of a DataFrame. | `df.T` |
| `explode()` | Converts list-like elements into separate rows. | `df.explode("Items")` |
| `stack()` | Moves column levels into the row index. | `df.stack()` |
| `unstack()` | Moves index levels into columns. | `df.unstack()` |
| `reset_index()` | Moves index labels into columns and resets the index. | `df.reset_index()` |
| `set_index()` | Sets one or more columns as the index. | `df.set_index("ID")` |
| `swaplevel()` | Swaps MultiIndex levels. | `df.swaplevel()` |
| `squeeze()` | Converts single-dimensional objects into a Series or scalar where possible. | `df.squeeze()` |

## 11\. Window and Time-Series Calculations

| Method | Description | Example |
| --- | --- | --- |
| `rolling()` | Performs rolling-window calculations. | `df["Sales"].rolling(3).mean()` |
| `expanding()` | Performs calculations over expanding windows. | `df["Sales"].expanding().mean()` |
| `ewm()` | Performs exponentially weighted calculations. | `df["Sales"].ewm(span=3).mean()` |
| `shift()` | Shifts values by a specified number of periods. | `df["Sales"].shift(1)` |
| `diff()` | Calculates differences between consecutive values. | `df["Sales"].diff()` |
| `pct_change()` | Calculates fractional changes between periods. | `df["Sales"].pct_change()` |
| `cumsum()` | Calculates cumulative sums. | `df.cumsum(numeric_only=True)` |
| `cumprod()` | Calculates cumulative products. | `df.cumprod(numeric_only=True)` |
| `cummax()` | Calculates cumulative maximums. | `df.cummax(numeric_only=True)` |
| `cummin()` | Calculates cumulative minimums. | `df.cummin(numeric_only=True)` |
| `resample()` | Changes the frequency of time-series data. | `df.resample("ME").sum()` |
| `asfreq()` | Converts time-series data to a specified frequency. | `df.asfreq("D")` |
| `asof()` | Retrieves the last non-missing observation before a specified time. | `df.asof("2026-01-01")` |
| `at_time()` | Selects observations at a particular time of day. | `df.at_time("09:30")` |
| `between_time()` | Selects observations within a time range. | `df.between_time("09:00", "17:00")` |
| `to_period()` | Converts a DatetimeIndex to a PeriodIndex. | `df.to_period("M")` |
| `to_timestamp()` | Converts a PeriodIndex to a DatetimeIndex. | `df.to_timestamp()` |
| `tz_localize()` | Assigns a time zone to timezone-naive datetime values. | `df.tz_localize("UTC")` |
| `tz_convert()` | Converts timezone-aware values to another time zone. | `df.tz_convert("America/Toronto")` |

**Note:** Time-series examples assume an appropriate datetime index. Methods such as `resample()`, `asfreq()`, and `at_time()` require suitable time-based indexing.

## 12\. Importing and Exporting Data

The following are top-level pandas functions or DataFrame conversion and export methods.

| Function / Method | Description | Example |
| --- | --- | --- |
| `pd.read_csv()` | Reads CSV files. | `pd.read_csv("data.csv")` |
| `pd.read_excel()` | Reads Excel files. | `pd.read_excel("data.xlsx")` |
| `pd.read_json()` | Reads JSON data. | `pd.read_json("data.json")` |
| `pd.read_sql()` | Reads data from SQL databases. | `pd.read_sql("SELECT * FROM sales", con)` |
| `pd.read_parquet()` | Reads Parquet files. | `pd.read_parquet("data.parquet")` |
| `pd.read_feather()` | Reads Feather files. | `pd.read_feather("data.feather")` |
| `pd.read_html()` | Reads HTML tables. | `pd.read_html("page.html")` |
| `pd.read_xml()` | Reads XML data. | `pd.read_xml("data.xml")` |
| `to_csv()` | Exports to CSV. | `df.to_csv("output.csv", index=False)` |
| `to_excel()` | Exports to Excel. | `df.to_excel("output.xlsx", index=False)` |
| `to_json()` | Exports to JSON. | `df.to_json("output.json")` |
| `to_sql()` | Writes data to a SQL database. | `df.to_sql("sales", con)` |
| `to_parquet()` | Exports to Parquet. | `df.to_parquet("output.parquet")` |
| `to_feather()` | Exports to Feather. | `df.to_feather("output.feather")` |
| `to_pickle()` | Serializes a DataFrame using pickle. | `df.to_pickle("output.pkl")` |
| `to_html()` | Converts a DataFrame to HTML. | `df.to_html("output.html")` |
| `to_xml()` | Converts a DataFrame to XML. | `df.to_xml("output.xml")` |
| `to_dict()` | Converts a DataFrame to a dictionary. | `df.to_dict()` |
| `to_numpy()` | Converts DataFrame values to a NumPy array. | `df.to_numpy()` |
| `to_records()` | Converts a DataFrame to a NumPy record array. | `df.to_records()` |
| `to_string()` | Formats a DataFrame as a string. | `df.to_string()` |
| `to_markdown()` | Formats a DataFrame as a Markdown table. | `df.to_markdown()` |
| `to_clipboard()` | Copies a DataFrame to the clipboard. | `df.to_clipboard()` |
| `to_latex()` | Converts a DataFrame to LaTeX format. | `df.to_latex()` |
| `to_orc()` | Exports data to ORC format. | `df.to_orc("output.orc")` |
| `to_iceberg()` | Writes data to an Apache Iceberg table. | `df.to_iceberg("db.table")` |

## 13\. Plotting and Visualization

| Method | Description | Example |
| --- | --- | --- |
| `plot()` | Creates a plot of the DataFrame. | `df.plot()` |
| `hist()` | Creates histograms for numerical columns. | `df.hist()` |
| `boxplot()` | Creates box plots for selected columns. | `df.boxplot()` |

Examples:

python

```python
# Line chart
df.plot(x="Date", y="Sales")

# Bar chart
df.plot(x="Department", y="Sales", kind="bar")

# Histogram
df["Sales"].plot(kind="hist")

# Scatter plot
df.plot(x="Sales", y="Profit", kind="scatter")

# Box plot
df.boxplot(column="Sales")
```

Pandas visualization uses Matplotlib as its default plotting backend.

## 14\. Iterating Over DataFrames

| Method | Description | Example |
| --- | --- | --- |
| `items()` | Iterates over column labels and Series. | `for name, col in df.items():` |
| `iterrows()` | Iterates over rows as index and Series pairs. | `for index, row in df.iterrows():` |
| `itertuples()` | Iterates over rows as named tuples. | `for row in df.itertuples():` |

Example:

python

```python
for row in df.itertuples(index=False):
    print(row)
```

**Note:** Prefer vectorized operations over row iteration when possible. `itertuples()` is generally preferable to `iterrows()` when iteration is necessary.

## 15\. Useful DataFrame Attributes and Properties

| Attribute | Description | Example |
| --- | --- | --- |
| `columns` | Returns column labels. | `df.columns` |
| `index` | Returns row index labels. | `df.index` |
| `dtypes` | Returns column data types. | `df.dtypes` |
| `shape` | Returns DataFrame dimensions. | `df.shape` |
| `size` | Returns total number of elements. | `df.size` |
| `ndim` | Returns number of dimensions. | `df.ndim` |
| `empty` | Checks whether the DataFrame is empty. | `df.empty` |
| `T` | Returns transposed DataFrame. | `df.T` |
| `values` | Returns underlying values as an array. | `df.values` |
| `attrs` | Stores user-defined metadata. | `df.attrs` |
| `flags` | Returns object flags. | `df.flags` |

**Note:** Prefer `to_numpy()` over `.values` when explicitly converting a DataFrame to a NumPy array.

## Important Technical Notes

1. This document covers commonly used public APIs, not every method in the complete DataFrame API.
2. `loc`, `iloc`, `at`, and `iat` are indexers, not methods.
3. `str` and `dt` are Series accessors, not DataFrame methods.
4. Functions such as `pd.read_csv()`, `pd.merge()`, and `pd.concat()` are top-level pandas functions.
5. Some operations return new DataFrames or Series instead of modifying the original object.
6. Methods that support `inplace=True` should be used carefully; returning and assigning the result is often easier to understand.
7. Statistical operations may require numeric columns or an appropriate `numeric_only` setting.
8. Time-series methods require suitable datetime-based indexes or columns, depending on the operation.
9. Some examples assume that referenced columns, indexes, and variables already exist.
10. Always check the official documentation for parameters, return values, and version-specific behavior.

## Official Pandas Resources

- Pandas DataFrame API Reference
- [Pandas DataFrame Class](<https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.html>)
- [Complete Pandas API Reference](<https://pandas.pydata.org/docs/reference/index.html>)
- Pandas User Guide
- Pandas Windowing Operations
- Pandas GroupBy Guide
- Pandas Time-Series Guide
- Pandas Visualization Guide
- Pandas Release Notes

---

**Documentation version:** pandas 3.1.0\
**Last updated:** October 2026\
**Reference type:** DataFrame methods, attributes, indexers, and related functions.

## A final recommendation

I would use this document alongside two separate references:

1. Pandas Series Methods — for Series-specific operations and accessors.
2. Pandas General Functions — for `pd.read_csv()`, `pd.to_datetime()`, `pd.concat()`, `pd.merge()`, and other top-level functions.

This gives you a well-organized pandas documentation collection without unnecessarily repeating content.
