# The value_counts() Method in Pandas

The value_counts() method returns the frequency of each unique value in a Pandas Series. It is useful for understanding category distributions and identifying frequently occurring values.
- [Pandas Series.value_counts()](https://pandas.pydata.org/docs/reference/api/pandas.Series.value_counts.html)
- [Pandas DataFrame.value_counts()](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.value_counts.html)

## 1. Method and Parameters

| Method / Parameter | Description | Example |
|---|---|---|
| value_counts() | Returns the count of each unique value in a Series. | df["Department"].value_counts() |
| normalize=True | Returns relative frequencies as proportions instead of actual counts. | df["Department"].value_counts(normalize=True) |
| dropna=True | Excludes missing values from the results. This is the default. | df["Department"].value_counts(dropna=True) |
| dropna=False | Includes missing values in the results. | df["Department"].value_counts(dropna=False) |

**Note:** The normalize and dropna parameters apply to Series.value_counts(). The method can also be used with DataFrames, but its behavior and available parameters differ.

## 2. Example DataFrame

```
import pandas as pd

df = pd.DataFrame({
    "Name": ["Alice", "Bob", "Alice", "Charlie", "Bob"],
    "Department": ["IT", "HR", "IT", "Finance", None]
})

print(df)
```

Output:

| | Name | Department |
|---:|---|---|
| 0 | Alice | IT |
| 1 | Bob | HR |
| 2 | Alice | IT |
| 3 | Charlie | Finance |
| 4 | Bob | None |

## 3. Count Unique Values

```
print(df["Department"].value_counts())
```

Output:

text
Department
IT         2
HR         1
Finance    1
Name: count, dtype: int64


Missing values are excluded by default.

## 4. Calculate Relative Frequencies

Set normalize=True to return proportions instead of counts.

```
print(df["Department"].value_counts(normalize=True))
```

Output:

text
Department
IT         0.50
HR         0.25
Finance    0.25
Name: proportion, dtype: float64


To display percentages:

```
print(df["Department"].value_counts(normalize=True) * 100)
```

Output:

text
Department
IT         50.0
HR         25.0
Finance    25.0
Name: proportion, dtype: float64


## 5. Include Missing Values

Use dropna=False to count missing values as a category.

```
print(df["Department"].value_counts(dropna=False))
```

Output:

text
Department
IT         2
HR         1
Finance    1
NaN        1
Name: count, dtype: int64


## 6. Practical Applications

- **Frequency analysis:** Determine which categories occur most often.
- **Data quality checks:** Identify unexpected values and missing data.
- **Percentage calculations:** Compare category proportions.
- **Exploratory data analysis:** Understand categorical variables before visualization.



