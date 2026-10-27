# Handle Missing Values: Numerical Imputation Methods
Numerical imputation is a data preprocessing technique used to replace missing numerical values with estimated values. The goal is to reduce data loss while maintaining the statistical properties and integrity of the dataset.

The three standard methods considered in this step are:

- **Mean:** Use when the numerical distribution is approximately symmetrical and has few significant outliers.
- **Median:** Use when the distribution is skewed or contains significant outliers.
- **Interpolation:** Use when observations have a meaningful order and neighboring values can help estimate missing values.

### Handle Missing Values: Numerical Imputation Methods

| Method | Best For | How It Works | Advantages | Limitations |
|---|---|---|---|---|
| **Mean Imputation** | Symmetrical numerical distributions without significant outliers | Replaces missing values with the arithmetic average of observed values. | Simple to implement; preserves the column mean. | Sensitive to outliers; can reduce variance and distort the distribution. |
| **Median Imputation** | Skewed numerical distributions or datasets with outliers | Replaces missing values with the median of observed values. | Robust to outliers; suitable for skewed data. | Can reduce variability; does not account for relationships between variables. |
| **Interpolation** | Time-series, sequential, or ordered data | Estimates missing values using neighboring observations and a mathematical method, such as linear, polynomial, or spline interpolation. | Preserves sequential patterns; useful for filling gaps in ordered data. | May be unreliable for long gaps, abrupt changes, or irregular patterns. |

### Implementation Checklist

- Identify numerical columns containing missing values.
- Calculate the percentage of missing values in each column.
- Examine distributions, summary statistics, and potential outliers.
- Determine whether the data has a meaningful temporal or sequential order.
- Select the appropriate imputation method for each column.
- Fit imputation parameters using training data only when building a predictive model.
- Apply the fitted transformation consistently to validation, test, and production data.
- Verify that missing values were handled as intended.
- Compare distributions and summary statistics before and after imputation.
- Document the method, assumptions, and any limitations.

### Important Considerations
- Imputed values are estimates, not actual observations.
- Mean and median imputation can reduce variance and weaken relationships between variables.
- Interpolation should only be used when the ordering of observations is meaningful.
- Avoid data leakage by calculating imputation values from training data only in predictive modeling workflows.
- If missingness is substantial or informative, consider more advanced approaches, such as multiple imputation or model-based imputation.

### Expected Outcome

Missing numerical values are handled using a method appropriate to the data distribution and structure. The resulting dataset is ready for subsequent preprocessing, exploratory data analysis, or model development, with the imputation decisions documented for reproducibility.

Recommended workflow: Start by examining the distribution and outliers for each numerical column. Use the mean for approximately symmetrical data, the median for skewed or outlier-prone data, and interpolation for genuinely ordered observations where neighboring values provide useful information.
