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
| [import_data](import) | [pd.read_csv()](import/file.md)  ,  [pd.read_excel()](import/file.md) , [pd.read_json()](import/file.md), [pd.read_sql()](import/database.md)   | Load data from files and databases. |
| Inspect data | head(), tail(), sample(), info(), describe() | Preview and summarize data. |
| Select data | loc[], iloc[], query(), filter() | Select rows and columns. |
| Clean data | drop(), dropna(), fillna(), replace(), drop_duplicates() | Remove or correct unwanted data. |
| Data types | astype(), convert_dtypes(), pd.to_numeric(), pd.to_datetime() | Convert data into appropriate types. |
| Sort data | sort_values(), sort_index(), nlargest(), nsmallest() | Order and rank records. |
| Calculate statistics | mean(), median(), mode(), sum(), min(), max(), std(), var() | Calculate descriptive statistics. |
| Group data | groupby(), agg(), aggregate(), transform() | Summarize and transform groups. |
| Combine data | merge(), join(), concat() | Combine datasets. |
| Reshape data | pivot(), pivot_table(), melt(), stack(), unstack() | Change the layout of datasets. |
| Analyze values | value_counts(), nunique(), unique(), duplicated(), corr() | Examine frequencies, uniqueness, and relationships. |
| Handle missing values | isna(), notna(), dropna(), fillna(), interpolate() | Identify and handle missing data. |
| Work with strings | str.lower(), str.upper(), str.strip(), str.replace(), str.contains() | Clean and search text. |
| Work with dates | dt.year, dt.month, dt.day, resample(), shift() | Extract date components and analyze time series. |
| Visualize data | plot(), hist(), boxplot() | Create basic charts. |
| Export data | to_csv(), to_excel(), to_json(), to_sql(), to_parquet() | Save results in different formats. |

**Important:** loc and iloc are indexers rather than methods. The dt accessor provides access to datetime properties and methods on Series. Functions such as pd.read_csv() and pd.to_datetime() are top-level pandas functions rather than DataFrame methods.

## 3\. Detailed Examples by Topic

### 3.1. Data Import and Export

Documentation: [Input/Output Functions](<https://pandas.pydata.org/docs/reference/io.html>)

```
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

### 3.3. Data Cleaning

Documentation: [Working with Missing Data](<https://pandas.pydata.org/docs/user_guide/missing_data.html>)

```
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

```
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

```
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

```
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

### 3.7. String and Date Operations

Documentation:

- [Working with Text Data](<https://pandas.pydata.org/docs/user_guide/text.html>)
- [Time Series and Date Functionality](<https://pandas.pydata.org/docs/user_guide/timeseries.html>)

```
# Clean text
df["name"] = df["name"].str.strip().str.lower()

# Convert dates
df["date"] = pd.to_datetime(df["date"])

# Extract date components
df["year"] = df["date"].dt.year
df["month"] = df["date"].dt.month
```

### 3.8. Data Visualization

Documentation: [Visualization Guide](<https://pandas.pydata.org/docs/user_guide/visualization.html>)

```
# Histogram
df["sales"].plot(kind="hist")

# Scatter plot
df.plot(x="sales", y="profit", kind="scatter")

# Box plot
df.boxplot(column="sales")
```

## 4\. Important Notes

- The examples assume that df is an existing pandas DataFrame.
- Some operations return a new DataFrame or Series rather than modifying the original object.
- Check the official documentation for the parameters, return values, and behavior of each method.
- Available methods and behavior may vary between pandas versions.
