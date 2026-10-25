# Data Visualization Libraries
Data visualization, also called data viz or data plotting, is the graphical representation of data to make it easier to interpret, understand  and tell story behind the data
- [Chart Visualisation](data_visualization_phases.md](https://pandas.pydata.org/pandas-docs/stable/user_guide/visualization.html)
- [Series Visualization](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.plot.html)

| Library | Description |
|---|---|
| **Matplotlib** | The original plotting library for Python and NumPy. Provides a low-level API that gives you a lot of control over plots. Can be difficult to learn compared with more modern libraries. |
| **Pandas** | Provides a plot() method for its DataFrame and Series objects. Uses Matplotlib to generate plots. Is easier to use than Matplotlib but doesn’t provide as much functionality. |
| **Seaborn** | Provides a high-level API for plotting data. Uses Matplotlib to generate plots. Makes it easier to create attractive plots than Matplotlib or Pandas. |
| **Altair** | Provides a high-level, declarative API that lets you create plots with a minimal amount of code. |
| **ggplot** | The Python version of the ggplot2 package. |

# Pandas methods 
Data Frame is a primary data structure that is provided by Pandas. Commons methods for the data visualization

| Plot option | Description | Example (kind) | Example (method) | Semantic graph | Symbol |
|---|---|---|---|---|---|
| line | Displays trends or changes over time. | df.plot(kind='line') | df.plot.line() | Line chart | 📈 |
| bar | Compares values across categories using vertical bars. | df.plot(kind='bar') | df.plot.bar() | Bar chart | 📊 |
| barh | Compares values across categories using horizontal bars. | df.plot(kind='barh') | df.plot.barh() | Horizontal bar chart | ↔️📊 |
| hist | Displays the distribution of numerical data using bins. | df.plot(kind='hist') | df.plot.hist() | Histogram | ▂▅▇ |
| box | Shows the median, quartiles, and potential outliers. | df.plot(kind='box') | df.plot.box() | Box plot | ─[▬]─ |
| kde | Shows a smoothed estimate of a probability distribution. | df.plot(kind='kde') | df.plot.kde() | Kernel density plot | ∩ |
| density | An alias for kde; displays estimated probability density. | df.plot(kind='density') | df.plot.density() | Density plot | ∩ |
| area | Shows quantities as filled areas over a range. | df.plot(kind='area') | df.plot.area() | Area chart | 🏔️ |
| pie | Shows proportions of a whole as slices of a circle. | df.plot(kind='pie', y='Sales') | df.plot.pie(y='Sales') | Pie chart | 🥧 |
| scatter | Shows the relationship between two numerical variables. | df.plot(kind='scatter', x='Age', y='Sales') | df.plot.scatter(x='Age', y='Sales') | Scatter plot | ⁙ |
| hexbin | Groups points into hexagonal bins to show density. | df.plot(kind='hexbin', x='Age', y='Sales') | df.plot.hexbin(x='Age', y='Sales') | Hexbin plot | ⬡ |


# Pandas plot() Method Parameters

| Parameter | Description | Example | Graph Example |
|---|---|---|---|
| x | Specifies the column to use for the x-axis. | df.plot(x='Age') | 📈 X-axis values |
| y | Specifies the column or columns to plot on the y-axis. | df.plot(y='Sales') | 📊 Y-axis values |
| kind | Specifies the type of plot to create. | df.plot(kind='bar') | 📊 Bar chart |
| ax | Uses an existing Matplotlib Axes object. | df.plot(ax=ax) | 🖼️ Existing plot |
| subplots | Creates a separate subplot for each column. | df.plot(subplots=True) | ▦ Multiple plots |
| sharex | Shares the x-axis among subplots. | df.plot(subplots=True, sharex=True) | ↔️ Shared x-axis |
| sharey | Shares the y-axis among subplots. | df.plot(subplots=True, sharey=True) | ↕️ Shared y-axis |
| layout | Sets the arrangement of subplots as (rows, columns). | df.plot(subplots=True, layout=(2, 2)) | ▦ 2 × 2 grid |
| figsize | Sets the figure size in inches. | df.plot(figsize=(10, 6)) | ↔️ Wide figure |
| use_index | Uses the DataFrame index for x-axis labels. | df.plot(use_index=True) | 🏷️ Index labels |
| title | Sets the plot title. | df.plot(title='Sales Report') | 📝 Chart title |
| grid | Controls gridline visibility. | df.plot(grid=True) | # Gridlines |
| legend | Displays or hides the legend. | df.plot(legend=False) | 🗂️ Legend |
| style | Specifies line styles. | df.plot(style='--') | ╌╌ Dashed line |
| logx | Uses a logarithmic x-axis. | df.plot(logx=True) | ↔️ Log scale |
| logy | Uses a logarithmic y-axis. | df.plot(logy=True) | ↕️ Log scale |
| loglog | Uses logarithmic scales on both axes. | df.plot(loglog=True) | 📈 Log-log plot |
| xticks | Specifies x-axis tick positions. | df.plot(xticks=[0, 1, 2, 3]) | ┬ X-axis ticks |
| yticks | Specifies y-axis tick positions. | df.plot(yticks=[0, 100, 200]) | ├ Y-axis ticks |
| xlim | Sets the x-axis display range. | df.plot(xlim=(0, 100)) | ↔️ Axis limits |
| ylim | Sets the y-axis display range. | df.plot(ylim=(0, 500)) | ↕️ Axis limits |
| xlabel | Sets the x-axis label. | df.plot(xlabel='Age') | X → Age |
| ylabel | Sets the y-axis label. | df.plot(ylabel='Sales') | Y → Sales |
| rot | Rotates tick labels by a specified angle. | df.plot(rot=45) | 🔄 Rotated labels |
| fontsize | Sets tick-label font size. | df.plot(fontsize=12) | 🔠 Text size |
| colormap | Specifies the color palette. | df.plot(colormap='viridis') | 🎨 Colors |
| colorbar | Displays a color scale for supported plots. | df.plot(kind='hexbin', x='Age', y='Sales', colorbar=True) | 🌈 Color scale |
| position | Controls bar alignment within available space. | df.plot(kind='bar', position=0.5) | 📊 Bar alignment |
| table | Adds a data table to the plot. | df.plot(table=True) | ▤ Data table |
| yerr | Specifies y-axis error bars. | df.plot(yerr=5) | ↕️ Error bars |
| xerr | Specifies x-axis error bars. | df.plot(xerr=2) | ↔️ Error bars |
| secondary_y | Plots specified columns on a secondary y-axis. | df.plot(secondary_y=True) | 📈 Dual y-axis |
| stacked | Stacks values in supported plot types. | df.plot(kind='bar', stacked=True) | 📚 Stacked bars |
| **kwargs| Passes additional parameters to the plotting backend, usually Matplotlib. | df.plot(alpha=0.7) | 🎨 Transparency |
