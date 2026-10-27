
# Handle Missing Values: Numerical Imputation Methods

Numerical imputation is a data preprocessing technique used to replace missing numerical values with estimated values. The goal is to reduce data loss while maintaining the statistical properties and integrity of the dataset.

The three standard methods considered in this step are:

- **Mean:** Use when the numerical distribution is approximately symmetrical and has few significant outliers.
- **Median:** Use when the distribution is skewed or contains significant outliers.
- **Interpolation:** Use when observations have a meaningful order and neighboring values can help estimate missing values.

### Numerical Imputation Methods

| Method | Best For | How It Works | Pandas Method | Advantages | Limitations |
|---|---|---|---|---|---|
| **Mean Imputation** | Symmetrical numerical distributions without significant outliers | Replaces missing values with the arithmetic average of observed values. | df[column].fillna(df[column].mean()) | Simple to implement; preserves the column mean. | Sensitive to outliers; can reduce variance and distort the distribution. |
| **Median Imputation** | Skewed numerical distributions or datasets with outliers | Replaces missing values with the median of observed values. | df[column].fillna(df[column].median()) | Robust to outliers; suitable for skewed data. | Can reduce variability; does not account for relationships between variables. |
| **Interpolation** | Time-series, sequential, or ordered data | Estimates missing values using neighboring observations and a mathematical method. | df[column].interpolate(method="linear") | Preserves sequential patterns; useful for filling gaps in ordered data. | May be unreliable for long gaps, abrupt changes, or irregular patterns. |

### Pandas Implementation

**Mean Imputation:** fillna() with mean()

```python
import pandas as pd

# Replace missing values with the column mean
df["column"] = df["column"].fillna(df["column"].mean())
```

**Example:**

```python
df = pd.DataFrame({"age": [20, 30, None, 40]})

df["age"] = df["age"].fillna(df["age"].mean())
```

The missing value is replaced with `30.0`.

**Median Imputation::** fillna() with median()

```python
# Replace missing values with the column median
df["column"] = df["column"].fillna(df["column"].median())
```

**Example:**

```python
df = pd.DataFrame({"income": [2000, 3000, None, 10000]})

df["income"] = df["income"].fillna(df["income"].median())
```

The missing value is replaced with 3000.0.

**Interpolation:** interpolate()

```python
# Linear interpolation
df["column"] = df["column"].interpolate(method="linear")
```

**Example:**

```python
df = pd.DataFrame({"sales": [100, None, 300]})

df["sales"] = df["sales"].interpolate(method="linear")
```

The missing value is estimated as 200.0.

**Common interpolation options:**

| Method | Description | Typical Use |
|---|---|---|
| linear | Assumes a straight-line relationship between observations. | General numerical sequences |
| polynomial | Fits a polynomial of a specified order. | Data following a suitable polynomial trend |
| spline | Fits a piecewise polynomial curve of a specified order. | Smoothly varying data |

Example with polynomial interpolation:

```python
df["column"] = df["column"].interpolate(
    method="polynomial",
    order=2
)
```

Note: Polynomial and spline interpolation require an appropriate order. Some interpolation methods also require SciPy. For time-series data, sort by timestamp before interpolation and choose the method according to the time intervals and data structure.

####  Applying Imputation to Multiple Columns

### Mean Imputation

```python
numeric_cols = df.select_dtypes(include="number").columns

df[numeric_cols] = df[numeric_cols].fillna(
    df[numeric_cols].mean()
)
```

### Median Imputation

```python
numeric_cols = df.select_dtypes(include="number").columns

df[numeric_cols] = df[numeric_cols].fillna(
    df[numeric_cols].median()
)
```

### Interpolation

```python
numeric_cols = df.select_dtypes(include="number").columns

df[numeric_cols] = df[numeric_cols].interpolate(
    method="linear"
)
```

**Important:** These examples apply the selected method to all numerical columns. In practice, choose the method separately for each column based on its distribution and meaning. Interpolation is most appropriate for ordered data, not arbitrary numerical columns.

## 4. Implementation Checklist

- [ ] Identify numerical columns containing missing values.
- [ ] Calculate the percentage of missing values in each column.
- [ ] Examine distributions, summary statistics, and potential outliers.
- [ ] Determine whether the data has a meaningful temporal or sequential order.
- [ ] Select the appropriate imputation method for each column.
- [ ] Fit imputation parameters using training data only when building a predictive model.
- [ ] Apply the fitted transformation consistently to validation, test, and production data.
- [ ] Verify that missing values were handled as intended.
- [ ] Compare distributions and summary statistics before and after imputation.
- [ ] Document the method, assumptions, and any limitations.

## 5. Important Considerations

- Imputed values are estimates, not actual observations.
- Mean and median imputation can reduce variance and weaken relationships between variables.
- Interpolation should only be used when the ordering of observations is meaningful.
- By default, linear interpolation uses the row positions between known observations; it does not automatically account for irregular time intervals.
- Avoid data leakage by calculating imputation values from training data only in predictive modeling workflows.
- For model pipelines, consider `sklearn.impute.SimpleImputer` for mean and median imputation.
- If missingness is substantial or informative, consider more advanced approaches, such as multiple imputation or model-based imputation.

## 6. Validation After Imputation

Check whether missing values remain:

```python
df.isna().sum()
```

Review numerical summaries:

```python
df.describe()
```

Compare the data before and after imputation to assess whether distributions and variability have changed substantially.

## 7. Expected Outcome

Missing numerical values are handled using a method appropriate to the data distribution and structure. The resulting dataset is ready for subsequent preprocessing, exploratory data analysis, or model development, with the imputation decisions documented for reproducibility.

**Recommended workflow:** Examine the distribution and outliers for each numerical column. Use mean imputation for approximately symmetrical data, median imputation for skewed or outlier-prone data, and interpolation for genuinely ordered observations where neighboring values provide useful information.
