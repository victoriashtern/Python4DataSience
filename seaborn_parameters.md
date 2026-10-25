##  Seaborn Parameters — Reference Table

| Parameter | Purpose | Example |
|---|---|---|
| data | DataFrame or other data source | data=df |
| x, y | Variables assigned to the axes | x="Age", y="Sales" |
| hue | Groups data by color | hue="Region" |
| palette | Controls category colors | palette="colorblind" |
| size | Maps a variable to marker size | size="Population" |
| sizes | Sets the marker-size range | sizes=(20, 200) |
| kind | Selects a plot type in figure-level functions | kind="scatter" |
| errorbar | Controls uncertainty intervals where supported | errorbar=("ci", 95) |
| height | Sets the height of each facet, in inches | height=5 |
| aspect | Sets the width-to-height ratio of each facet | aspect=1.25 |
| col | Creates subplots for distinct column values | col="Region" |
| col_wrap | Wraps facets into multiple rows | col_wrap=3 |
| legend | Controls legend display for supported functions | legend="auto" |

### Important Notes

- **Common parameters:** data, x, y, hue, and palette are widely used across Seaborn plotting functions.
- **Marker parameters:** size maps a variable to marker size, while sizes controls the range of marker sizes in supported functions.
- **Plot-type parameter:** kind selects the plot type in supported figure-level functions, such as relplot(), catplot(), and displot().
- **Faceting parameters:** height, aspect, col, and col_wrap control the size and arrangement of subplots in supported figure-level functions.
- **Uncertainty intervals:** errorbar controls how uncertainty is displayed in functions that support it, such as barplot() and lineplot().
- **Legend parameter:** legend controls legend display in supported functions.

**Important:** These parameters are not universal. Their availability and behavior depend on the specific Seaborn function being used.


# Seaborn Parameters — Examples

### 1. Create Sample Data
Run this first; the examples below reuse df.

```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

df = pd.DataFrame({
    "Age": [22, 25, 30, 35, 40, 45, 28, 38],
    "Sales": [200, 250, 300, 350, 400, 450, 280, 390],
    "Region": ["East", "West", "East", "West",
               "East", "West", "East", "West"],
    "Population": [100, 200, 150, 300, 250, 400, 180, 350],
    "Gender": ["F", "M", "F", "M", "F", "M", "F", "M"]
})
```


### 2. Basic Data and Axis Parameters
Parameters: data, x, y, hue, palette

```
sns.scatterplot(
    data=df,
    x="Age",
    y="Sales",
    hue="Region",
    palette="colorblind"
)
plt.show()
```
- data=df — Uses the DataFrame.
- x="Age" — Places Age on the x-axis.
- y="Sales" — Places Sales on the y-axis.
- hue="Region" — Colors points according to region.
- palette="colorblind" — Selects a colorblind-friendly palette.

### 3. Marker Size Parameters
Parameters: size, sizes
```
sns.scatterplot(
    data=df,
    x="Age",
    y="Sales",
    size="Population",
    sizes=(20, 200)
)
plt.show()
```

- size="Population" — Maps Population values to marker sizes.
- sizes=(20, 200) — Sets the minimum and maximum marker sizes.
  
### 4. Choose a Plot Type with kind
The kind parameter works with supported figure-level functions such as relplot().

```
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

### 5. Control Plot Size with height and aspect

```
sns.relplot(
    data=df,
    x="Age",
    y="Sales",
    height=5,
    aspect=1.5
)
plt.show()
```

- height=5 — Sets each facet's height to 5 inches.
- aspect=1.5 — Makes each facet's width 1.5 times its height.

### 6. Create Subplots with col and col_wrap
```
sns.relplot(
    data=df,
    x="Age",
    y="Sales",
    hue="Region",
    col="Gender",
    col_wrap=2
)
plt.show()
```


### 7. Control Uncertainty Intervals with errorbar
```
sns.barplot(
    data=df,
    x="Region",
    y="Sales",
    errorbar=("ci", 95)
)
plt.show()
```

- errorbar=("ci", 95) — Displays a 95% confidence interval around the estimated mean.
- This parameter is supported by functions such as barplot() and lineplot().

 ### 8. Control the Legend with legend
```
sns.relplot(
    data=df,
    x="Age",
    y="Sales",
    hue="Region",
    legend="auto"
)
plt.show()
```
- legend="auto" — Lets Seaborn choose an appropriate legend display.
- Other supported options include "brief", "full", and False.
```
