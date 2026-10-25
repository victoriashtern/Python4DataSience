# Pandas DataFrame Methods

## 1. Inspecting and Viewing Data

| Method / Attribute | Description | Example |
|---|---|---|
| `head()` | Returns the first 5 rows by default. | `df.head()` |
| `tail()` | Returns the last 5 rows by default. | `df.tail()` |
| `sample()` | Returns random rows. | `df.sample(5)` |
| `info()` | Displays column names, data types, and non-null counts. | `df.info()` |
| `describe()` | Generates descriptive statistics. | `df.describe()` |
| `shape` | Returns the number of rows and columns. | `df.shape` |
| `size` | Returns the total number of elements. | `df.size` |
| `ndim` | Returns the number of dimensions. | `df.ndim` |
| `columns` | Returns column labels. | `df.columns` |
| `index` | Returns row index labels. | `df.index` |
| `dtypes` | Returns data types of columns. | `df.dtypes` |
| `memory_usage()` | Reports memory usage by column. | `df.memory_usage()` |

## 2. Selecting and Accessing Data

| Method / Attribute | Description | Example |
|---|---|---|
| `loc[]` | Selects rows and columns by labels. | `df.loc[0, 'Age']` |
| `iloc[]` | Selects rows and columns by integer position. | `df.iloc[0, 1]` |
| `at[]` | Accesses a single value using labels. | `df.at[0, 'Age']` |
| `iat[]` | Accesses a single value using integer positions. | `df.iat[0, 1]` |
| `get()` | Retrieves a column or returns a default if missing. | `df.get('Age')` |
| `filter()` | Selects rows or columns by labels or patterns. | `df.filter(items=['Age', 'Sales'])` |
| `query()` | Filters rows using a Boolean expression. | `df.query('Age > 30')` |
| `isin()` | Checks whether values belong to a specified set. | `df['Age'].isin([20, 30])` |
| `where()` | Keeps values where a condition is true. | `df.where(df > 0)` |
| `mask()` | Replaces values where a condition is true. | `df.mask(df < 0)` |

## 3. Adding, Modifying, and Removing Data

| Method | Description | Example |
|---|---|---|
| `assign()` | Adds or modifies columns and returns a DataFrame. | `df.assign(Tax=df['Sales'] * 0.1)` |
| `insert()` | Inserts a column at a specified position. | `df.insert(1, 'Bonus', 100)` |
| `pop()` | Removes and returns a column. | `df.pop('Age')` |
| `drop()` | Removes specified rows or columns. | `df.drop(columns=['Age'])` |
| `rename()` | Renames rows or columns. | `df.rename(columns={'Age': 'Years'})` |
| `set_axis()` | Sets row or column labels. | `df.set_axis(['A', 'B'], axis=1)` |
| `replace()` | Replaces specified values. | `df.replace(0, None)` |
| `update()` | Updates values using another DataFrame. | `df.update(other_df)` |
| `copy()` | Creates a copy of a DataFrame. | `df.copy()` |

## 4. Cleaning Data

| Method | Description | Example |
|---|---|---|
| `isna()` | Identifies missing values. | `df.isna()` |
| `isnull()` | Alias for `isna()`. | `df.isnull()` |
| `notna()` | Identifies non-missing values. | `df.notna()` |
| `dropna()` | Removes rows or columns containing missing values. | `df.dropna()` |
| `fillna()` | Fills missing values. | `df.fillna(0)` |
| `ffill()` | Fills missing values using the previous valid value. | `df.ffill()` |
| `bfill()` | Fills missing values using the next valid value. | `df.bfill()` |
| `drop_duplicates()` | Removes duplicate rows. | `df.drop_duplicates()` |
| `duplicated()` | Identifies duplicate rows. | `df.duplicated()` |
| `convert_dtypes()` | Converts columns to suitable data types. | `df.convert_dtypes()` |
| `astype()` | Converts columns to specified data types. | `df.astype({'Age': 'int64'})` |

## 5. Sorting and Ranking

| Method | Description | Example |
|---|---|---|
| `sort_values()` | Sorts rows by column values. | `df.sort_values('Age')` |
| `sort_index()` | Sorts rows or columns by their labels. | `df.sort_index()` |
| `nlargest()` | Returns rows with the largest values. | `df.nlargest(5, 'Sales')` |
| `nsmallest()` | Returns rows with the smallest values. | `df.nsmallest(5, 'Sales')` |
| `rank()` | Computes numerical ranks. | `df['Sales'].rank()` |

## 6. Statistical and Aggregation Methods

| Method | Description | Example |
|---|---|---|
| `sum()` | Calculates the sum. | `df.sum()` |
| `mean()` | Calculates the arithmetic mean. | `df.mean(numeric_only=True)` |
| `median()` | Calculates the median. | `df.median(numeric_only=True)` |
| `mode()` | Returns the most frequent value or values. | `df['Age'].mode()` |
| `min()` | Returns the minimum value. | `df.min(numeric_only=True)` |
| `max()` | Returns the maximum value. | `df.max(numeric_only=True)` |
| `count()` | Counts non-missing values. | `df.count()` |
| `std()` | Calculates standard deviation. | `df.std(numeric_only=True)` |
| `var()` | Calculates variance. | `df.var(numeric_only=True)` |
| `quantile()` | Calculates specified quantiles. | `df.quantile(0.5, numeric_only=True)` |
| `nunique()` | Counts unique values. | `df.nunique()` |
| `value_counts()` | Counts the frequency of distinct values in a Series. | `df['Age'].value_counts()` |
| `corr()` | Calculates pairwise correlations. | `df.corr(numeric_only=True)` |
| `cov()` | Calculates pairwise covariance. | `df.cov(numeric_only=True)` |
| `agg()` | Applies one or more aggregation functions. | `df.agg(['min', 'max'])` |

## 7. Applying Functions and Grouping

| Method | Description | Example |
|---|---|---|
| `apply()` | Applies a function along rows or columns. | `df.apply(sum, axis=0)` |
| `map()` | Applies a function elementwise to DataFrame values. | `df.map(lambda x: x)` |
| `transform()` | Applies a function while preserving the DataFrame's shape. | `df.transform(lambda x: x * 2)` |
| `pipe()` | Passes the DataFrame to a function. | `df.pipe(my_function)` |
| `groupby()` | Groups rows for aggregation or analysis. | `df.groupby('Department')['Sales'].sum()` |
| `resample()` | Groups time-series data into time intervals. | `df.resample('ME').sum()` |

## 8. Combining DataFrames

| Method / Function | Description | Example |
|---|---|---|
| `merge()` | Combines DataFrames using database-style joins. | `pd.merge(df1, df2, on='ID')` |
| `join()` | Joins DataFrames, usually by index. | `df1.join(df2)` |
| `concat()` | Concatenates DataFrames along rows or columns. | `pd.concat([df1, df2])` |
| `combine_first()` | Fills missing values using another DataFrame. | `df1.combine_first(df2)` |
| `compare()` | Shows differences between similarly labeled DataFrames. | `df1.compare(df2)` |
| `align()` | Aligns row and column labels between objects. | `df1.align(df2)` |

## 9. Reshaping Data

| Method / Attribute | Description | Example |
|---|---|---|
| `pivot()` | Reshapes data using unique index-column combinations. | `df.pivot(index='Date', columns='City', values='Sales')` |
| `pivot_table()` | Creates a summarized pivot table. | `df.pivot_table(values='Sales', index='City', aggfunc='sum')` |
| `melt()` | Converts wide-format data into long-format data. | `df.melt(id_vars=['ID'])` |
| `transpose()` | Swaps rows and columns. | `df.transpose()` |
| `T` | Returns the transpose of a DataFrame. | `df.T` |
| `explode()` | Converts list-like elements into separate rows. | `df.explode('Items')` |
| `stack()` | Moves column levels into the row index. | `df.stack()` |
| `unstack()` | Moves index levels into columns. | `df.unstack()` |
| `reset_index()` | Moves index labels into columns and resets the index. | `df.reset_index()` |
| `set_index()` | Sets one or more columns as the index. | `df.set_index('ID')` |

## 10. Importing and Exporting Data

| Function / Method | Description | Example |
|---|---|---|
| `pd.read_csv()` | Reads a CSV file into a DataFrame. | `pd.read_csv('data.csv')` |
| `pd.read_excel()` | Reads an Excel file. | `pd.read_excel('data.xlsx')` |
| `pd.read_json()` | Reads JSON data. | `pd.read_json('data.json')` |
| `to_csv()` | Exports a DataFrame to CSV. | `df.to_csv('output.csv', index=False)` |
| `to_excel()` | Exports a DataFrame to Excel. | `df.to_excel('output.xlsx', index=False)` |
| `to_json()` | Exports a DataFrame to JSON. | `df.to_json('output.json')` |
| `to_dict()` | Converts a DataFrame to a dictionary. | `df.to_dict()` |
| `to_numpy()` | Converts DataFrame values to a NumPy array. | `df.to_numpy()` |

## 11. Plotting

| Method | Description | Example |
|---|---|---|
| `plot()` | Creates a plot of the DataFrame. | `df.plot()` |
| `hist()` | Creates histograms for numerical columns. | `df.hist()` |
| `boxplot()` | Creates box plots for selected columns. | `df.boxplot()` |

## Official Documentation

- [Pandas DataFrame API Reference](https://pandas.pydata.org/pandas-docs/stable/reference/frame.html)
- [Pandas User Guide](https://pandas.pydata.org/pandas-docs/stable/user_guide/index.html)
- [Pandas Visualization Guide](https://pandas.pydata.org/pandas-docs/stable/user_guide/visualization.html)

**Note:** Some examples assume that the referenced columns exist in your DataFrame. Functions such as `pd.concat()`, `pd.merge()`, and `pd.read_csv()` are top-level pandas functions rather than DataFrame instance methods.
