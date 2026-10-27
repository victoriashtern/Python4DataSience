Here’s a Markdown (`.md`) form you can use to document and support the Handle Missing Values step in a data preprocessing workflow. It includes the purpose, selection criteria, method descriptions, and a checklist for choosing the appropriate numerical imputation technique.

Writing

# Handle Missing Values: Numerical Imputation Methods

## 1\. Objective

Numerical imputation is a data preprocessing technique used to replace missing numerical values with estimated values. The goal is to reduce data loss while maintaining the statistical properties and integrity of the dataset.

The three standard methods considered in this step are:

- **Mean Imputation**
- **Median Imputation**
- **Interpolation**

## 2\. Imputation Methods

### 2.1 Mean Imputation

**Best for:** Symmetrical numerical distributions without significant outliers.

**How it works:** Replaces each missing value with the arithmetic mean of the available values in the column.

**Formula:**

Mean = Sum of observed values / Number of observed values

**Advantages:**

- Simple to implement and understand.
- Preserves the column's overall average.

**Limitations:**

- Sensitive to extreme values and outliers.
- Can reduce variance and distort the original distribution.
- May be inappropriate for highly skewed data.

**Example:** For observed values `10, 20, 30`, the mean is `20`. A missing value is replaced with `20`.

### 2.2 Median Imputation

**Best for:** Skewed numerical distributions or datasets containing outliers.

**How it works:** Replaces each missing value with the median, or middle value, of the available observations.

**Advantages:**

- Robust to extreme values and outliers.
- Suitable for skewed numerical distributions.
- Less affected by unusually high or low observations than the mean.

**Limitations:**

- Can reduce variability in the dataset.
- Does not account for relationships between variables.
- May distort the distribution when many values are missing.

**Example:** For observed values `10, 20, 100`, the median is `20`. A missing value is replaced with `20`.

### 2.3 Interpolation

**Best for:** Time-series, sequential, or ordered data, such as daily sales, sensor readings, and stock prices.

**How it works:** Estimates missing values using known observations before and after the missing position, based on an assumed mathematical relationship.

**Common methods:**

- **Linear interpolation:** Assumes a straight-line relationship between known observations.
- **Polynomial interpolation:** Uses a polynomial function to estimate intermediate values.
- **Spline interpolation:** Uses piecewise polynomial functions to produce a smooth curve.

**Advantages:**

- Preserves the order and continuity of sequential data.
- Can provide realistic estimates when neighboring observations are informative.
- Useful for filling short gaps in time-series data.

**Limitations:**

- May be unreliable for long gaps or abrupt changes.
- Results depend on the interpolation method and underlying data pattern.
- Requires appropriate ordering and, typically, known observations around the missing value.

**Example:** If a daily sensor reading is `10` on Monday and `20` on Wednesday, linear interpolation estimates Tuesday's missing reading as `15`, assuming equal time intervals.

## 3\. Method Selection Guide

| Data characteristics | Recommended method |
| --- | --- |
| Approximately symmetrical distribution, few significant outliers | Mean imputation |
| Skewed distribution or significant outliers | Median imputation |
| Time-series or ordered observations | Interpolation |
| Long missing sequences or substantial missingness | Investigate the missingness pattern and consider more advanced methods |

## 4\. Implementation Checklist

- [ ]Identify numerical columns containing missing values.
- [ ]Calculate the percentage of missing values in each column.
- [ ]Examine distributions, summary statistics, and potential outliers.
- [ ]Determine whether the data has a meaningful temporal or sequential order.
- [ ]Select the appropriate imputation method for each column.
- [ ]Fit imputation parameters using training data only when building a predictive model.
- [ ]Apply the fitted transformation consistently to validation, test, and production data.
- [ ]Verify that missing values were handled as intended.
- [ ]Compare distributions and summary statistics before and after imputation.
- [ ]Document the method, assumptions, and any limitations.

## 5\. Important Considerations

- Imputed values are estimates, not actual observations.
- Mean and median imputation can reduce variance and weaken relationships between variables.
- Interpolation should only be used when the ordering of observations is meaningful.
- Avoid data leakage by calculating imputation values from training data only in predictive modeling workflows.
- If missingness is substantial or informative, consider more advanced approaches, such as multiple imputation or model-based imputation.

## 6\. Documentation Record

| Field | Details |
| --- | --- |
| Dataset / table | _Specify dataset name_ |
| Numerical column | _Specify column name_ |
| Missing value count | _Specify count_ |
| Missing value percentage | _Specify percentage_ |
| Selected method | _Mean / Median / Interpolation_ |
| Reason for selection | _Describe distribution or data structure_ |
| Validation performed | _Describe checks_ |
| Outcome | _Summarize results_ |

## 7\. Expected Outcome

Missing numerical values are handled using a method appropriate to the data distribution and structure. The resulting dataset is ready for subsequent preprocessing, exploratory data analysis, or model development, with the imputation decisions documented for reproducibility.

Recommended workflow: Start by examining the distribution and outliers for each numerical column. Use the mean for approximately symmetrical data, the median for skewed or outlier-prone data, and interpolation for genuinely ordered observations where neighboring values provide useful information.
