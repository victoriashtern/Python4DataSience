
# Seaborn Plotting Functions
Seaborn is a Python data visualization library used to create attractive, informative statistical graphs. It is built on top of Matplotlib and works particularly well with Pandas DataFrame
- [Seaborn API Reference](https://seaborn.pydata.org/api.html)
- [Relational Plots](https://seaborn.pydata.org/tutorial/relational.html)
- [Categorical Plots](https://seaborn.pydata.org/tutorial/categorical.html)
- [Distribution Plots](https://seaborn.pydata.org/tutorial/distributions.html)
- [Matrix Plots](https://seaborn.pydata.org/tutorial/matrix.html)
- [Regression Plots](https://seaborn.pydata.org/tutorial/regression.html)

## 1. Relational Plots

Relational plots show relationships between variables.

### General Method

| General Method | Object Returned | Plot Type | Seaborn Primary Method | Symbol |
|---|---|---|---|---|
| relplot() | FacetGrid | Relational plots | sns.relplot() | 📈 |

### Specific Methods

| Specific Method | Object Returned | Plot Type | Seaborn Primary Method | Symbol |
|---|---|---|---|---|
| scatterplot() | Axes | Scatter plot | sns.scatterplot() | ⁙ |
| lineplot() | Axes | Line plot | sns.lineplot() | 📈 |

## 2. Categorical Plots

Categorical plots compare values or show distributions across categories.

### General Method

| General Method | Object Returned | Plot Type | Seaborn Primary Method | Symbol |
|---|---|---|---|---|
| catplot() | FacetGrid | Categorical plots | sns.catplot() | 📊 |

### Specific Methods

| Specific Method | Object Returned | Plot Type | Seaborn Primary Method | Symbol |
|---|---|---|---|---|
| barplot() | Axes | Bar plot | sns.barplot() | 📊 |
| countplot() | Axes | Count plot | sns.countplot() | ▂▅▇ |
| boxplot() | Axes | Box plot | sns.boxplot() | ─[▬]─ |
| violinplot() | Axes | Violin plot | sns.violinplot() | 🎻 |
| stripplot() | Axes | Strip plot | sns.stripplot() | ⁙ |
| swarmplot() | Axes | Swarm plot | sns.swarmplot() | ⁘ |
| pointplot() | Axes | Point plot | sns.pointplot() | ─●─ |
| boxenplot() | Axes | Boxen plot | sns.boxenplot() | ▣ |

## 3. Distribution Plots

Distribution plots visualize the distribution, frequency, and density of data.

### General Method

| General Method | Object Returned | Plot Type | Seaborn Primary Method | Symbol |
|---|---|---|---|---|
| displot() | FacetGrid | Distribution plots | sns.displot() | 📊 |

### Specific Methods

| Specific Method | Object Returned | Plot Type | Seaborn Primary Method | Symbol |
|---|---|---|---|---|
| histplot() | Axes | Histogram | sns.histplot() | ▂▅▇ |
| kdeplot() | Axes | Kernel density estimate (KDE) | sns.kdeplot() | ∩ |
| ecdfplot() | Axes | Empirical cumulative distribution function (ECDF) | sns.ecdfplot() | ⤴ |

## 4. Other Important Seaborn Plotting Methods

| Method | Object Returned | Plot Type | Seaborn Primary Method | Symbol |
|---|---|---|---|---|
| heatmap() | Axes | Heatmap | sns.heatmap() | 🌡️ |
| clustermap() | ClusterGrid | Clustered heatmap | sns.clustermap() | ▦ |
| pairplot() | PairGrid | Pairwise relationships | sns.pairplot() | ▦ |
| jointplot() | JointGrid | Joint and marginal distributions | sns.jointplot() | ◉ |
| regplot() | Axes | Regression plot | sns.regplot() | 📈 |

## 5. Basic Seaborn Parameters

| Parameter | Description |
|---|---|
| data | The DataFrame or other data source that provides the data for the plot. |
| kind | Specifies the type of plot to create. |
| x, y | Specify the columns to use for the x-axis and y-axis, respectively. |
| hue | Specifies the column used to group data by category, assigning a different color to each category. |
| palette | Specifies the color palette for the plot, such as colorblind, pastel, flare, or bright. The default is None. |
| height | Sets the height of the plot in inches. The default is 5. Available for general plotting functions. |
| aspect | Sets the ratio of the plot's width to its height. The width is calculated as aspect * height. Available for general plotting functions. |
| legend | Controls how the legend is displayed. Options include 'auto' (default), 'brief', 'full', and False. Available for general plotting functions. |
| lmplot() | FacetGrid | Regression plot with faceting | sns.lmplot() | 📈 |
| residplot() | Axes | Residual plot | sns.residplot() | ± |


