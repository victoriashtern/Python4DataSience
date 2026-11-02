
# Seaborn Plot Types

## 1\. Introduction

Seaborn is a Python visualization library built on Matplotlib. It provides statistical plots that help explore datasets, identify patterns, compare categories, examine distributions, and understand relationships between variables.

Seaborn plotting functions are organized into different categories, each designed for a particular type of data analysis.

python

```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
```

## 2\. Choose the Right Plot

Use this table to select a plot based on what you want to understand about your data.

| Symbol | What do you want to do? | Recommended Plot | Function |
| --- | --- | --- | --- |
| ⁙ | Examine the relationship between two numerical variables. | Scatter plot | `sns.scatterplot()` |
| 📈 | Show changes or trends over time. | Line plot | `sns.lineplot()` |
| 📊 | Compare average values across categories. | Bar plot | `sns.barplot()` |
| ▂▅▇ | Count observations in each category. | Count plot | `sns.countplot()` |
| ─\[▬\]─ | Compare distributions across categories. | Box plot | `sns.boxplot()` |
| 🎻 | Examine distribution shapes across categories. | Violin plot | `sns.violinplot()` |
| ▂▅▇ | Display the frequency distribution of a variable. | Histogram | `sns.histplot()` |
| ∩ | Examine a smooth distribution curve. | KDE plot | `sns.kdeplot()` |
| 🌡️ | Identify correlations between numerical variables. | Heatmap | `sns.heatmap()` |
| ▦ | Examine relationships between several numerical variables. | Pair plot | `sns.pairplot()` |
| ◉ | Examine two variables and their distributions together. | Joint plot | `sns.jointplot()` |
| 📈 | Display a relationship with a regression line. | Regression plot | `sns.regplot()` |

**Note:** Symbols are visual reminders of the graph types, not exact previews.

## 3\. Seaborn Plot Categories

Seaborn provides six main categories of statistical plots.

| Plot Category | General Function | Purpose | Example Functions |
| --- | --- | --- | --- |
| Relational | `relplot()` | Explore relationships between numerical variables. | `scatterplot()`, `lineplot()` |
| Categorical | `catplot()` | Compare values across different categories. | `barplot()`, `boxplot()`, `violinplot()` |
| Distribution | `displot()` | Examine the distribution of numerical data. | `histplot()`, `kdeplot()`, `ecdfplot()` |
| Regression | `lmplot()` | Explore relationships using regression models. | `regplot()`, `residplot()` |
| Matrix | — | Visualize data values using colors and matrices. | `heatmap()`, `clustermap()` |
| Multivariate | — | Explore relationships among multiple variables. | `pairplot()`, `jointplot()` |

### 3.1 Figure-Level and Axes-Level Functions

Seaborn provides two main types of plotting functions.

**Figure-Level Functions**

These functions manage the overall figure layout and can create multiple subplots or facets.

Examples:

- `relplot()`
- `catplot()`
- `displot()`
- `lmplot()`

**Axes-Level Functions**

These functions create individual plots on a Matplotlib Axes object.

Examples:

- `scatterplot()`
- `lineplot()`
- `barplot()`
- `histplot()`
- `regplot()`
- `heatmap()`

**Important Notes:**

- Figure-level functions generally return a `FacetGrid`.
- Axes-level functions generally return a Matplotlib `Axes`.
- Functions such as `pairplot()`, `jointplot()`, and `clustermap()` return specialized objects.

## 4\. Relational Plots

Relational plots help examine relationships between two or more numerical variables.

### 4.1 Scatter Plot

**Function:** `sns.scatterplot()`

**Purpose:** Shows the relationship between two numerical variables using individual data points.

python

```python
sns.scatterplot(data=df, x="Age", y="Sales")
plt.show()
```

### 4.2 Line Plot

**Function:** `sns.lineplot()`

**Purpose:** Displays trends and changes in numerical data, particularly over time.

python

```python
sns.lineplot(data=df, x="Age", y="Sales")
plt.show()
```

### 4.3 Relational Plot

**Function:** `sns.relplot()`

**Purpose:** Provides a figure-level interface for creating scatter plots and line plots.

python

```python
# Scatter plot
sns.relplot(data=df, x="Age", y="Sales", kind="scatter")

# Line plot
sns.relplot(data=df, x="Age", y="Sales", kind="line")

plt.show()
```

## 5\. Categorical Plots

Categorical plots help compare numerical values across different groups or categories.

### 5.1 Bar Plot

**Function:** `sns.barplot()`

**Purpose:** Compares statistical estimates, usually the mean, across categories.

python

```python
sns.barplot(data=df, x="Region", y="Sales")
plt.show()
```

### 5.2 Count Plot

**Function:** `sns.countplot()`

**Purpose:** Displays the number of observations in each category.

python

```python
sns.countplot(data=df, x="Region")
plt.show()
```

### 5.3 Box Plot

**Function:** `sns.boxplot()`

**Purpose:** Displays the distribution of numerical data using quartiles, median, and potential outliers.

python

```python
sns.boxplot(data=df, x="Region", y="Sales")
plt.show()
```

### 5.4 Violin Plot

**Function:** `sns.violinplot()`

**Purpose:** Combines a box-plot-like summary with a density representation to show the distribution of data across categories.

python

```python
sns.violinplot(data=df, x="Region", y="Sales")
plt.show()
```

### 5.5 Strip Plot

**Function:** `sns.stripplot()`

**Purpose:** Displays individual observations as points across different categories.

python

```python
sns.stripplot(data=df, x="Region", y="Sales")
plt.show()
```

### 5.6 Swarm Plot

**Function:** `sns.swarmplot()`

**Purpose:** Displays individual observations while adjusting their positions to reduce overlapping.

python

```python
sns.swarmplot(data=df, x="Region", y="Sales")
plt.show()
```

### 5.7 Point Plot

**Function:** `sns.pointplot()`

**Purpose:** Displays statistical estimates and uncertainty intervals across categories.

python

```python
sns.pointplot(data=df, x="Region", y="Sales")
plt.show()
```

### 5.8 Boxen Plot

**Function:** `sns.boxenplot()`

**Purpose:** Provides a detailed representation of distributions, particularly useful for larger datasets.

python

```python
sns.boxenplot(data=df, x="Region", y="Sales")
plt.show()
```

### 5.9 Categorical Plot

**Function:** `sns.catplot()`

**Purpose:** Provides a figure-level interface for creating different categorical plots.

python

```python
sns.catplot(
    data=df,
    x="Region",
    y="Sales",
    kind="box"
)

plt.show()
```

## 6\. Distribution Plots

Distribution plots help understand how numerical values are spread across a dataset.

### 6.1 Histogram

**Function:** `sns.histplot()`

**Purpose:** Displays the frequency distribution of numerical data using bars.

python

```python
sns.histplot(data=df, x="Sales")
plt.show()
```

### 6.2 Kernel Density Estimate (KDE) Plot

**Function:** `sns.kdeplot()`

**Purpose:** Displays a smoothed estimate of the probability density distribution.

python

```python
sns.kdeplot(data=df, x="Sales")
plt.show()
```

### 6.3 Empirical Cumulative Distribution Function (ECDF) Plot

**Function:** `sns.ecdfplot()`

**Purpose:** Shows the proportion of observations that are less than or equal to a particular value.

python

```python
sns.ecdfplot(data=df, x="Sales")
plt.show()
```

### 6.4 Distribution Plot

**Function:** `sns.displot()`

**Purpose:** Provides a figure-level interface for creating distribution visualizations.

python

```python
sns.displot(
    data=df,
    x="Sales",
    kind="hist"
)

plt.show()
```

## 7\. Regression Plots

Regression plots help examine relationships between variables and identify trends using fitted statistical models.

### 7.1 Regression Plot

**Function:** `sns.regplot()`

**Purpose:** Displays a scatter plot with a fitted regression line.

python

```python
sns.regplot(data=df, x="Age", y="Sales")
plt.show()
```

### 7.2 Linear Model Plot

**Function:** `sns.lmplot()`

**Purpose:** Creates regression visualizations with additional grouping and faceting capabilities.

python

```python
sns.lmplot(
    data=df,
    x="Age",
    y="Sales",
    hue="Region"
)

plt.show()
```

### 7.3 Residual Plot

**Function:** `sns.residplot()`

**Purpose:** Displays regression residuals to help evaluate how well a regression model fits the data.

python

```python
sns.residplot(data=df, x="Age", y="Sales")
plt.show()
```

## 8\. Matrix Plots

Matrix plots represent numerical values in a matrix format, often using colors to highlight patterns and relationships.

### 8.1 Heatmap

**Function:** `sns.heatmap()`

**Purpose:** Uses color intensity to represent numerical values in a matrix, commonly for correlation analysis.

python

```python
sns.heatmap(
    df.corr(numeric_only=True),
    annot=True,
    cmap="coolwarm"
)

plt.show()
```

### 8.2 Cluster Map

**Function:** `sns.clustermap()`

**Purpose:** Creates a heatmap with hierarchical clustering to group similar rows and columns.

python

```python
sns.clustermap(
    df.corr(numeric_only=True),
    annot=True,
    cmap="coolwarm"
)

plt.show()
```

## 9\. Multivariate Plots

Multivariate plots help explore relationships among multiple variables simultaneously.

### 9.1 Pair Plot

**Function:** `sns.pairplot()`

**Purpose:** Creates a collection of plots showing pairwise relationships between numerical variables.

python

```python
sns.pairplot(
    df,
    vars=["Age", "Sales", "Population"],
    hue="Region"
)

plt.show()
```

### 9.2 Joint Plot

**Function:** `sns.jointplot()`

**Purpose:** Combines a plot showing the relationship between two variables with their individual distributions.

python

```python
sns.jointplot(
    data=df,
    x="Age",
    y="Sales",
    kind="scatter"
)

plt.show()
```

## 10\. Summary of Seaborn Plot Types

| Plot Category | Function | Main Application |
| --- | --- | --- |
| Relational | `scatterplot()` | Shows relationships between numerical variables. |
| Relational | `lineplot()` | Shows trends and changes. |
| Categorical | `barplot()` | Compares statistical estimates across categories. |
| Categorical | `countplot()` | Displays the number of observations in each category. |
| Categorical | `boxplot()` | Shows distributions, quartiles, and potential outliers. |
| Categorical | `violinplot()` | Shows distribution shapes and density across categories. |
| Categorical | `stripplot()` | Displays individual observations as points. |
| Categorical | `swarmplot()` | Displays individual points while reducing overlap. |
| Categorical | `pointplot()` | Compares statistical estimates and uncertainty intervals. |
| Categorical | `boxenplot()` | Shows detailed distributions, especially for larger datasets. |
| Distribution | `histplot()` | Shows the frequency distribution of numerical data. |
| Distribution | `kdeplot()` | Shows a smoothed probability density distribution. |
| Distribution | `ecdfplot()` | Shows cumulative proportions of observations. |
| Regression | `regplot()` | Shows relationships with a fitted regression line. |
| Regression | `lmplot()` | Displays regression relationships with grouping and faceting. |
| Regression | `residplot()` | Displays regression residuals. |
| Matrix | `heatmap()` | Represents numerical values using color intensity. |
| Matrix | `clustermap()` | Displays clustered data using a heatmap. |
| Multivariate | `pairplot()` | Explores pairwise relationships between multiple variables. |
| Multivariate | `jointplot()` | Shows relationships and marginal distributions. |

## 11\. Additional Resources

- [Seaborn Official Documentation](<https://seaborn.pydata.org/>)
- [Seaborn Tutorial](<https://seaborn.pydata.org/tutorial.html>)
- [Seaborn API Reference](<https://seaborn.pydata.org/api.html>)
- [Seaborn Example Gallery](<https://seaborn.pydata.org/examples/index.html>)
