
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

## 7 Parameters for Working with Subplots

| Parameter | Description | Example |
|---|---|---|
| col | Specifies the column whose unique values determine how the data is divided into subplots. | sns.relplot(data=df, x='Age', y='Sales', col='Region') |
| col_wrap | Specifies the maximum number of subplots per row before wrapping to the next row. Used with col in supported figure-level functions. | sns.relplot(data=df, x='Age', y='Sales', col='Region', col_wrap=3) |

## 8  Axes Parameters: Ticks and Limits

# The set() Method Parameters

| Parameter | Description | Example | Graph Example |
|---|---|---|---|
| xticks | Specifies the locations of ticks on the x-axis. | ax.set(xticks=[1910, 1915, 1920, 1925, 1930]) | ↔️ X-axis tick positions |
| yticks | Specifies the locations of ticks on the y-axis. | ax.set(yticks=[0, 500, 1000, 1500]) | ↕️ Y-axis tick positions |
| xlim | Sets the lower and upper limits of the x-axis. | ax.set(xlim=(1910, 1930)) | ↔️ X-axis range |
| ylim | Sets the lower and upper limits of the y-axis. | ax.set(ylim=(0, 1750)) | ↕️ Y-axis range |
| title | Sets the plot title. | ax.set(title='Deaths by Age Group') | 📝 Chart title |
| xlabel | Sets the x-axis label. | ax.set(xlabel='Year') | X → Year |
| ylabel | Sets the y-axis label. | ax.set(ylabel='Deaths per 100,000') | Y → Death rate |

#  The tick_params() Method

| Parameter | Description | Example | Graph Example |
|---|---|---|---|
| axis | Specifies which axis to modify: 'x', 'y', or 'both'. | ax.tick_params(axis='x') | ↔️ X-axis ticks |
| labelrotation | Rotates tick labels by the specified angle in degrees. | ax.tick_params(axis='x', labelrotation=30) | 🔄 Angled labels |
| labelsize | Sets the font size of tick labels. | ax.tick_params(axis='both', labelsize=10) | 🔠 Label size |
| labelcolor | Sets the color of tick labels. | ax.tick_params(axis='x', labelcolor='blue') | 🔵 Label color |
| length | Sets the length of tick marks. | ax.tick_params(axis='both', length=5) | ┬ Tick length |
| width | Sets the width of tick marks. | ax.tick_params(axis='both', width=1.5) | ┃ Tick thickness |
| colors | Sets the color of both tick marks and tick labels. | ax.tick_params(axis='y', colors='red') | 🔴 Tick color |
| direction | Sets the direction of ticks: 'in', 'out', or 'inout'. | ax.tick_params(axis='both', direction='in') | ↘ Tick direction |
| grid_color | Sets the color of gridlines when gridline settings are enabled. | ax.tick_params(axis='y', grid_color='gray') | ▦ Gridline color |
## Official Documentation

- [Seaborn relplot()](https://seaborn.pydata.org/generated/seaborn.relplot.html)
- [Matplotlib Axes.set()](https://matplotlib.org/stable/api/_as_gen/matplotlib.axes.Axes.set.html)
- [Matplotlib Axes.tick_params()](https://matplotlib.org/stable/api/_as_gen/matplotlib.axes.Axes.tick_params.html)


