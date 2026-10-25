## 2. Seaborn Plotting Methods — Master Table

| Plot Family | General Method | Specific Method | Object Returned | Purpose | Example | Symbol |
|---|---|---|---|---|---|---|
| Relational |relplot()` |scatterplot()` |Axes` | Relationship between two variables |sns.scatterplot(data=df, x="Age", y="Sales")` | ⁙ |
| Relational |relplot()` |lineplot()` |Axes` | Trends and changes |sns.lineplot(data=df, x="Date", y="Sales")` | 📈 |
| Categorical |catplot()` |barplot()` |Axes` | Compare estimated values |sns.barplot(data=df, x="Region", y="Sales")` | 📊 |
| Categorical |catplot()` |countplot()` |Axes` | Count observations |sns.countplot(data=df, x="Category")` | ▂▅▇ |
| Categorical |catplot()` |boxplot()` |Axes` | Median, quartiles, and outliers |sns.boxplot(data=df, x="Region", y="Sales")` | ─[▬]─ |
| Categorical |catplot()` |violinplot()` |Axes` | Distribution and density |sns.violinplot(data=df, x="Region", y="Sales")` | 🎻 |
| Categorical |catplot()` |stripplot()` |Axes` | Individual observations |sns.stripplot(data=df, x="Region", y="Sales")` | ⁙ |
| Categorical |catplot()` |swarmplot()` |Axes` | Non-overlapping observations where possible |sns.swarmplot(data=df, x="Region", y="Sales")` | ⁘ |
| Categorical |catplot()` |pointplot()` |Axes` | Estimates and uncertainty |sns.pointplot(data=df, x="Region", y="Sales")` | ─●─ |
| Categorical |catplot()` |boxenplot()` |Axes` | Detailed distribution |sns.boxenplot(data=df, x="Region", y="Sales")` | ▣ |
| Distribution |displot()` |histplot()` |Axes` | Frequency distribution |sns.histplot(data=df, x="Sales")` | ▂▅▇ |
| Distribution |displot()` |kdeplot()` |Axes` | Smoothed density |sns.kdeplot(data=df, x="Sales")` | ∩ |
| Distribution |displot()` |ecdfplot()` |Axes` | Cumulative proportions |sns.ecdfplot(data=df, x="Sales")` | ⤴ |
| Regression |lmplot()` |regplot()` |Axes`* | Relationship with fitted regression |sns.regplot(data=df, x="Age", y="Sales")` | 📈 |
| Regression |lmplot()` | — |FacetGrid` | Regression with optional faceting |sns.lmplot(data=df, x="Age", y="Sales", hue="Region")` | 📈 |
| Regression | — |residplot()` |Axes` | Regression residuals |sns.residplot(data=df, x="Age", y="Sales")` | ± |
| Matrix | — |heatmap()` |Axes` | Values represented by color |sns.heatmap(data=df.corr(numeric_only=True), annot=True)` | 🌡️ |
| Matrix |clustermap()` | — |ClusterGrid` | Clustered heatmap |sns.clustermap(df.corr(numeric_only=True))` | ▦ |
| Multivariate |pairplot()` | — |PairGrid` | Pairwise relationships |sns.pairplot(df, vars=["Age", "Sales"])` | ▦ |
| Multivariate |jointplot()` | — |JointGrid` | Joint and marginal distributions |sns.jointplot(data=df, x="Age", y="Sales")` | ◉ |

### Important Notes

### Important Notes

- **Figure-level functions:** These create and manage the overall plot layout. They can arrange data into multiple subplots when needed. Examples:relplot()`,catplot()`,displot()`,lmplot()`,pairplot()`,jointplot()`, andclustermap()`.
- **Axes-level functions:** These create a specific plot on a single set of axes. Examples:scatterplot()`,lineplot()`,barplot()`,histplot()`, andregplot()`.
- **General methods:** Functions such asrelplot()`,catplot()`, anddisplot()` let you choose between several related plot types using thekind` parameter. They also support creating multiple subplots based on categories.
- **Specific methods:** These create one particular type of plot. For example,scatterplot()` creates a scatter plot, whilehistplot()` creates a histogram.
- **Regression methods:**lmplot()` creates a regression plot and supports multiple subplots.regplot()` creates a regression plot on a single set of axes.
- **Returned objects:** Figure-level functions return grid objects, such asFacetGrid` orPairGrid`. Axes-level functions return a MatplotlibAxes` object. This tells you what kind of object you can use to customize the plot afterward.
- **Examples:** All code examples assume thatdf` is a pandas DataFrame containing the columns used in the example. Theheatmap()` andclustermap()` examples use numeric data suitable for a matrix visualization.

*Correction:* TheObject Returned` column describes the object returned by the specific method. When the specific method is blank, it describes the general method.
