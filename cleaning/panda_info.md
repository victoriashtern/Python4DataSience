# The info() Method in Pandas

The info() method provides a summary of a DataFrame, including column names, data types, non-null counts, and memory usage.

### Parameters of the info() Method

| Parameter | Description |
|---|---|
| verbose=True | Displays detailed information for all columns. |
| memory_usage='deep' | Calculates memory usage more accurately, including the memory used by object values. |
| show_counts=True | Displays the number of non-null values in each column. |

### Example: Using info()

```
polls.info(
    verbose=True,
    memory_usage='deep',
    show_counts=True
)
```

 Output
```
text
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 12624 entries, 0 to 12623

Data columns (total 27 columns):
forecastdate          12624 non-null object
startdate             12624 non-null object
enddate               12624 non-null object
samplesize            12621 non-null float64
rawpoll_mcmullin         90 non-null float64
adjpoll_mcmullin         90 non-null float64


dtypes: float64(10), int64(3), object(14)
memory usage: 12.9 MB
```

*Note: The output above is abbreviated for illustration. Actual output depends on the DataFrame.*

#### Understanding the Output

| Output | Meaning |
|---|---|
| RangeIndex: 12624 entries | The DataFrame contains 12,624 rows. |
| Data columns (total 27 columns) | The DataFrame contains 27 columns. |
| 12624 non-null | The column contains 12,624 non-missing values. |
| 90 non-null | The column contains 90 non-missing values, so many values may be missing. |
| float64 | The column contains floating-point numbers. |
| int64 | The column contains integers. |
| object | The column contains objects, often strings or mixed values. |
| memory usage: 12.9 MB | The estimated memory occupied by the DataFrame. |

####  Why Use info() When Cleaning Data?

The info() method helps you:

- Identify columns with missing values.
- Check whether columns have appropriate data types.
- Understand the size and structure of a dataset.
- Estimate the memory used by a DataFrame.
- Identify columns that may require further investigation.

**Example:** If a column has 12,624 rows but only 90 non-null values, investigate whether the missing values should be retained, replaced, or removed before analysis.
