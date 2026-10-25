
# Seaborn Types

**Seaborn plotting** is the process of creating statistical graphs and visualizations in Python using the Seaborn library. It helps you explore data, identify patterns, compare groups, and understand relationships between variables.
Seaborn is built on top of Matplotlib and works especially well with pandas DataFrames.

## Plotting Methods

| Family | General | Specific | Returns | Purpose | Example | Icon |
|:--|:--|:--|:--|:--|:--|:--:|
| Relational | relplot() | scatterplot() | Axes | Variable relationships | sns.scatterplot(data=df, x="Age", y="Sales") | ⁙ |
| Relational | relplot() | lineplot() | Axes | Trends over time | sns.lineplot(data=df, x="Date", y="Sales") | 📈 |
| Categorical | catplot() | barplot() | Axes | Compare estimates | sns.barplot(data=df, x="Region", y="Sales") | 📊 |
| Categorical | catplot() | countplot() | Axes | Count observations | sns.countplot(data=df, x="Category") | ▂▅▇ |
| Categorical | catplot() | boxplot() | Axes | Quartiles and outliers | sns.boxplot(data=df, x="Region", y="Sales") | ─[▬]─ |
| Categorical | catplot() | violinplot() | Axes | Distribution density | sns.violinplot(data=df, x="Region", y="Sales") | 🎻 |
| Categorical | catplot() | stripplot() | Axes | Individual data points | sns.stripplot(data=df, x="Region", y="Sales") | ⁙ |
| Categorical | catplot() | swarmplot() | Axes | Separated data points | sns.swarmplot(data=df, x="Region", y="Sales") | ⁘ |
| Categorical | catplot() | pointplot() | Axes | Estimates and uncertainty | sns.pointplot(data=df, x="Region", y="Sales") | ─●─ |
| Categorical | catplot() | boxenplot() | Axes | Detailed distribution | sns.boxenplot(data=df, x="Region", y="Sales") | ▣ |
| Distribution | displot() | histplot() | Axes | Frequency distribution | sns.histplot(data=df, x="Sales") | ▂▅▇ |
| Distribution | displot() | kdeplot() | Axes | Smoothed density | sns.kdeplot(data=df, x="Sales") | ∩ |
| Distribution | displot() | ecdfplot() | Axes | Cumulative proportions | sns.ecdfplot(data=df, x="Sales") | ⤴ |
| Regression | lmplot() | regplot() | Axes* | Fitted regression line | sns.regplot(data=df, x="Age", y="Sales") | 📈 |
| Regression | lmplot() | — | FacetGrid | Regression with faceting | sns.lmplot(data=df, x="Age", y="Sales", hue="Region") | 📈 |
| Regression | — | residplot() | Axes | Regression residuals | sns.residplot(data=df, x="Age", y="Sales") | ± |
| Matrix | — | heatmap() | Axes | Values shown by color | sns.heatmap(data=df.corr(numeric_only=True)) | 🌡️ |
| Matrix | clustermap() | — | ClusterGrid | Clustered heatmap | sns.clustermap(df.corr(numeric_only=True)) | ▦ |
| Multivariate | pairplot() | — | PairGrid | Pairwise relationships | sns.pairplot(df, vars=["Age", "Sales"]) | ▦ |
| Multivariate | jointplot() | — | JointGrid | Joint and marginal distributions | sns.jointplot(data=df, x="Age", y="Sales") | ◉ |

### Important Notes

- **Figure-level functions:** Manage the overall plot layout and can create multiple subplots. Examples: relplot(), catplot(), displot(), and lmplot().
- **Axes-level functions:** Draw an individual plot on a Matplotlib Axes object. Examples: scatterplot(), lineplot(), histplot(), and regplot().
- **General methods:** Functions such as relplot(), catplot(), and displot() offer several plot types through the kind parameter.
- **Specific methods:** Create one particular plot type, such as scatterplot() or histplot().
- **Regression:** regplot() draws a regression plot on an Axes; lmplot() supports regression plots with faceting.
- **Returned objects:** The Returns column identifies the object returned by the specific method, or by the general method when the specific method is blank.

## Examples

```
import seaborn as sns
import matplotlib.pyplot as plt
sns.scatterplot(data=df, x="Age", y="Sales")

# Display the plot
plt.show()
```

- import seaborn as sns — Imports the Seaborn library.
- data=df — Specifies the DataFrame containing your data.
- x="Age" and y="Sales" — Specify the variables to visualize.
- plt.show() — Displays the plot.

| Plot Category | Purpose |General Method | Example Function |
| --- | --- | --- |--- |
| Relational | relplot()| Show relationships between variables | sns.scatterplot() |
| Categorical |catplot() | Compare values across categories | sns.barplot() |
| Distribution |  displot() | Understand the distribution of data | sns.histplot() |
| Regression |lmplot() | Show trends and fitted relationships | sns.regplot() |
| Matrix | | Display values using colors | sns.heatmap() |
| Multivariate | | Explore relationships among multiple variables | sns.pairplot() |

### Scatter Plot
```
# Shows the relationship between two numerical variables.
sns.scatterplot(data=df, x="Age", y="Sales")
```

### Bar Plot
```
# Compares estimated values across categories.

sns.barplot(data=df, x="Region", y="Sales")
```

### Histogram
```
# Shows the frequency distribution of numerical data.
sns.histplot(data=df, x="Sales")
```

- **Examples:** The examples assume df is a pandas DataFrame containing the required columns.

