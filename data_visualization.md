# Data Visualization Libraries
Data visualization, also called data viz or data plotting, is the graphical representation of data to make it easier to interpret, understand  and tell story behind the data

| Library | Description |
|---|---|
| **Matplotlib** | The original plotting library for Python and NumPy. Provides a low-level API that gives you a lot of control over plots. Can be difficult to learn compared with more modern libraries. |
| **Pandas** | Provides a `plot()` method for its DataFrame and Series objects. Uses Matplotlib to generate plots. Is easier to use than Matplotlib but doesn’t provide as much functionality. |
| **Seaborn** | Provides a high-level API for plotting data. Uses Matplotlib to generate plots. Makes it easier to create attractive plots than Matplotlib or Pandas. |
| **Altair** | Provides a high-level, declarative API that lets you create plots with a minimal amount of code. |
| **ggplot** | The Python version of the `ggplot2` package. |

# Pandas methods 
Data Frame is a primary data structure that is provided by Pandas. Commons methods for the data visualization

| Plot option | Description | Example (`kind`) | Example (method) | Semantic graph | Symbol |
|---|---|---|---|---|---|
| line | Displays trends or changes over time. | df.plot(kind='line') | df.plot.line() | Line chart | 📈 |
| bar | Compares values across categories using vertical bars. | df.plot(kind='bar') | df.plot.bar() | Bar chart | 📊 |
| barh | Compares values across categories using horizontal bars. | df.plot(kind='barh') | `df.plot.barh() | Horizontal bar chart | ↔️📊 |
| hist | Displays the distribution of numerical data using bins. | df.plot(kind='hist') | df.plot.hist() | Histogram | ▂▅▇ |
| box | Shows the median, quartiles, and potential outliers. | df.plot(kind='box') | df.plot.box() | Box plot | ─[▬]─ |
| kde | Shows a smoothed estimate of a probability distribution. | df.plot(kind='kde') | df.plot.kde() | Kernel density plot | ∩ |
| density | An alias for `kde`; displays estimated probability density. | df.plot(kind='density') | df.plot.density() | Density plot | ∩ |
| area | Shows quantities as filled areas over a range. | df.plot(kind='area') | df.plot.area() | Area chart | 🏔️ |
| pie | Shows proportions of a whole as slices of a circle. | df.plot(kind='pie', y='Sales') | df.plot.pie(y='Sales') | Pie chart | 🥧 |
| scatter | Shows the relationship between two numerical variables. | df.plot(kind='scatter', x='Age', y='Sales') | df.plot.scatter(x='Age', y='Sales') | Scatter plot | ⁙ |
| hexbin | Groups points into hexagonal bins to show density. | df.plot(kind='hexbin', x='Age', y='Sales') | df.plot.hexbin(x='Age', y='Sales') | Hexbin plot | ⬡ |
