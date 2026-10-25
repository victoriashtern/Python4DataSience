
# Seaborn Plotting Functions
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
| lmplot() | FacetGrid | Regression plot with faceting | sns.lmplot() | 📈 |
| residplot() | Axes | Residual plot | sns.residplot() | ± |


**Note:** Symbols are illustrative Unicode characters or emoji, not actual rendered graph previews.
