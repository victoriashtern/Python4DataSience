

# Seaborn Plot Types

## 1\. Introduction

Seaborn is a Python visualization library built on Matplotlib. It helps explore data, identify patterns, compare categories, examine distributions, and understand relationships between variables.

python

```python
import seaborn as sns
import matplotlib.pyplot as plt
import pandas as pd
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

## 3\. Understanding Horizontal and Vertical Plots

You can change the orientation of a graph by switching the `x` and `y` variables.

- **Vertical:** Categories on the X-axis and values on the Y-axis.
- **Horizontal:** Values on the X-axis and categories on the Y-axis.

### Vertical Bar Plot

python

```python
sns.barplot(data=df, x="Region", y="Sales")
plt.show()
```

### Horizontal Bar Plot

python

```python
sns.barplot(data=df, x="Sales", y="Region")
plt.show()
```

### Quick Reference

| Plot | Vertical | Horizontal |
| --- | --- | --- |
| Bar | `x="Region", y="Sales"` | `x="Sales", y="Region"` |
| Count | `x="Region"` | `y="Region"` |
| Box | `x="Region", y="Sales"` | `x="Sales", y="Region"` |
| Violin | `x="Region", y="Sales"` | `x="Sales", y="Region"` |

**Tip:** Horizontal graphs are particularly useful when category names are long or there are many categories.

## 4\. Relational Plots

Used to examine relationships between numerical variables.

### 4.1 Scatter Plot – `sns.scatterplot()`

Shows the relationship between two numerical variables using individual points.

python

```python
sns.scatterplot(data=df, x="Age", y="Sales")
plt.show()
```

### 4.2 Line Plot – `sns.lineplot()`

Shows trends and changes, especially over time.

python

```python
sns.lineplot(data=df, x="Date", y="Sales")
plt.show()
```

### 4.3 Relational Plot – `sns.relplot()`

A figure-level function for scatter and line plots.

python

```python
# Scatter plot
sns.relplot(
    data=df,
    x="Age",
    y="Sales",
    kind="scatter"
)

# Line plot
sns.relplot(
    data=df,
    x="Age",
    y="Sales",
    kind="line"
)

plt.show()
```

## 5\. Categorical Plots

Used to compare numerical values across different groups or categories.

### 5.1 Bar Plot – `sns.barplot()`

Compares statistical estimates, usually the mean, across categories.

python

```python
sns.barplot(data=df, x="Region", y="Sales")
plt.show()
```

### 5.2 Count Plot – `sns.countplot()`

Displays the number of observations in each category.

python

```python
sns.countplot(data=df, x="Region")
plt.show()
```

### 5.3 Box Plot – `sns.boxplot()`

Shows the median, quartiles, spread, and potential outliers.

python

```python
sns.boxplot(data=df, x="Region", y="Sales")
plt.show()
```

### 5.4 Violin Plot – `sns.violinplot()`

Shows the shape and density of a numerical distribution across categories.

python

```python
sns.violinplot(data=df, x="Region", y="Sales")
plt.show()
```

### 5.5 Other Categorical Plots

| Function | Purpose |
| --- | --- |
| `sns.stripplot()` | Shows individual observations as points. |
| `sns.swarmplot()` | Shows individual points while reducing overlap. |
| `sns.pointplot()` | Compares statistical estimates and uncertainty intervals. |
| `sns.boxenplot()` | Shows detailed distributions, particularly for larger datasets. |
| `sns.catplot()` | Creates different categorical plots using a figure-level interface. |

Example:

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

Used to understand how numerical values are spread across a dataset.

### 6.1 Histogram – `sns.histplot()`

Displays the frequency distribution using bars.

python

```python
sns.histplot(data=df, x="Sales", bins=20)
plt.show()
```

### 6.2 KDE Plot – `sns.kdeplot()`

Displays a smooth curve representing the estimated distribution.

python

```python
sns.kdeplot(data=df, x="Sales")
plt.show()
```

### 6.3 ECDF Plot – `sns.ecdfplot()`

Shows the proportion of observations less than or equal to each value.

python

```python
sns.ecdfplot(data=df, x="Sales")
plt.show()
```

### 6.4 Distribution Plot – `sns.displot()`

A figure-level function for creating histograms, KDE, and ECDF plots.

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

Used to examine relationships and identify trends using regression models.

### 7.1 Regression Plot – `sns.regplot()`

Shows individual data points with a fitted regression line.

python

```python
sns.regplot(data=df, x="Age", y="Sales")
plt.show()
```

### 7.2 Linear Model Plot – `sns.lmplot()`

Creates regression plots with additional grouping and faceting capabilities.

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

### 7.3 Residual Plot – `sns.residplot()`

Displays regression residuals to help evaluate model fit.

python

```python
sns.residplot(data=df, x="Age", y="Sales")
plt.show()
```

## 8\. Matrix Plots

Used to represent numerical values in a matrix, often using colors to highlight patterns.

### 8.1 Heatmap – `sns.heatmap()`

Uses colors to represent numerical values. Commonly used to visualize correlations.

python

```python
sns.heatmap(
    df.corr(numeric_only=True),
    annot=True,
    cmap="coolwarm"
)

plt.show()
```

### 8.2 Cluster Map – `sns.clustermap()`

Creates a heatmap with hierarchical clustering to group similar rows and columns.

python

```python
sns.clustermap(
    df.corr(numeric_only=True),
    cmap="coolwarm"
)

plt.show()
```

## 9\. Multivariate Plots

Used to explore relationships among multiple variables simultaneously.

### 9.1 Pair Plot – `sns.pairplot()`

Creates multiple plots showing pairwise relationships between numerical variables.

python

```python
sns.pairplot(
    df,
    vars=["Age", "Sales", "Population"],
    hue="Region"
)

plt.show()
```

### 9.2 Joint Plot – `sns.jointplot()`

Combines the relationship between two variables with their individual distributions.

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

## 10\. Quick Reference – All Plot Functions

| Category | Function | Main Purpose |
| --- | --- | --- |
| Relational | `scatterplot()` | Examine relationships. |
| Relational | `lineplot()` | Show trends over time. |
| Categorical | `barplot()` | Compare average values. |
| Categorical | `countplot()` | Count observations. |
| Categorical | `boxplot()` | Compare distributions. |
| Categorical | `violinplot()` | Examine distribution shapes. |
| Categorical | `stripplot()` | Display individual points. |
| Categorical | `swarmplot()` | Display non-overlapping points. |
| Categorical | `pointplot()` | Compare estimates. |
| Categorical | `boxenplot()` | Examine detailed distributions. |
| Distribution | `histplot()` | Show frequencies. |
| Distribution | `kdeplot()` | Show smooth distributions. |
| Distribution | `ecdfplot()` | Show cumulative proportions. |
| Regression | `regplot()` | Show regression lines. |
| Regression | `lmplot()` | Explore grouped regression. |
| Regression | `residplot()` | Examine residuals. |
| Matrix | `heatmap()` | Visualize numerical matrices. |
| Matrix | `clustermap()` | Group similar observations. |
| Multivariate | `pairplot()` | Examine multiple relationships. |
| Multivariate | `jointplot()` | Examine two variables and distributions. |

## 11\. Additional Resources

- [Seaborn Official Documentation](<https://seaborn.pydata.org/>)
- [Seaborn Tutorial](<https://seaborn.pydata.org/tutorial.html>)
- [Seaborn API Reference](<https://seaborn.pydata.org/api.html>)
- [Seaborn Example Gallery](<https://seaborn.pydata.org/examples/index.html>)
