## Seaborn Plot Customization Methods
These methods are mainly Matplotlib functions used to customize plots created with Seaborn.

| Category | Methods | Purpose |
|---|---|---|
| Figure layout |plt.subplots(),figsize,subplots_adjust() | Control figure size and spacing |
| Titles and labels |set_title(),set_xlabel(),set_ylabel() | Add titles and axis labels |
| Axis limits |set_xlim(),set_ylim() | Control visible ranges |
| Ticks |set_xticks(),set_yticks(),tick_params() | Customize tick positions and appearance |
| Annotations |annotate() | Highlight specific data points |
| Style |sns.set_style() | Change backgrounds and grid appearance |
| Colors |sns.color_palette(),sns.set_palette() | Choose color palettes |
| Saving |savefig() | Export a figure to a file |


## Examples

These methods are mainly Matplotlib functions used to customize plots created with Seaborn.

### 1. Prepare the Data

Run this setup first. The following examples reusedf.

```
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

df = pd.DataFrame({
    "Age": [22, 25, 30, 35, 40, 45],
    "Sales": [200, 250, 300, 350, 400, 450],
    "Region": ["East", "West", "East", "West", "East", "West"]
})
```

### 2. Figure Layout
Use plt.subplots() to create a figure and axes, figsize to set the figure size, and subplots_adjust() to control spacing.
```
fig, ax = plt.subplots(figsize=(8, 5))
sns.scatterplot(data=df, x="Age", y="Sales", ax=ax)
fig.subplots_adjust(left=0.15, right=0.95, top=0.85)
plt.show()
```
- figsize=(8, 5) — Sets the figure width to 8 inches and height to 5 inches.
- subplots_adjust() — Changes the margins around the plot.

### 3. Titles and Labels
Use set_title(), set_xlabel(), and set_ylabel() to add a title and axis labels.
```
fig, ax = plt.subplots()
sns.scatterplot(data=df, x="Age", y="Sales", ax=ax)

ax.set_title("Age vs. Sales")
ax.set_xlabel("Customer Age")
ax.set_ylabel("Sales Revenue")

plt.show()
```

### 4. Axis Limits
Use set_xlim() and set_ylim() to control the visible ranges of the axes.
```
fig, ax = plt.subplots()
sns.scatterplot(data=df, x="Age", y="Sales", ax=ax)

ax.set_xlim(20, 50)
ax.set_ylim(150, 500)

plt.show()
```

- set_xlim(20, 50) — Displays x-axis values from 20 to 50.
- set_ylim(150, 500) — Displays y-axis values from 150 to 500.

### 5. Ticks
Use set_xticks(), set_yticks(), and tick_params() to customize axis tick positions and appearance.
```
fig, ax = plt.subplots()
sns.scatterplot(data=df, x="Age", y="Sales", ax=ax)

ax.set_xticks([20, 30, 40, 50])
ax.set_yticks([200, 300, 400, 500])
ax.tick_params(axis="both", labelsize=10, colors="blue")

plt.show()
```
- set_xticks() — Sets the x-axis tick positions.
- set_yticks() — Sets the y-axis tick positions.
- tick_params() — Changes the appearance of tick marks and labels.

### 6. Annotations
Use annotate() to highlight a particular data point with text and an arrow.
```
fig, ax = plt.subplots()
sns.scatterplot(data=df, x="Age", y="Sales", ax=ax)

ax.annotate(
    "Highest sales",
    xy=(45, 450),
    xytext=(32, 430),
    arrowprops={"arrowstyle": "->", "color": "red"}
)

plt.show()
```

- xy=(45, 450) — Specifies the point to highlight.
- xytext=(32, 430) — Specifies where the annotation text appears.
- arrowprops — Controls the arrow's appearance.


### 7.Style
Use sns.set_style() to change the background and grid appearance.
```
sns.set_style("whitegrid")
sns.scatterplot(data=df, x="Age", y="Sales")

plt.show()
```
Common styles:
- "whitegrid" — White background with grid lines.
- "darkgrid" — Gray background with grid lines.
- "white" — White background without grid lines.
- "dark" — Gray background without grid lines.
- "ticks" — Clean background with axis tick marks.

### 8 Colors
Use sns.color_palette() to retrieve a palette and sns.set_palette() to set the default palette for subsequent Seaborn plots.
```
sns.set_palette("Set2")
sns.scatterplot(
    data=df,
    x="Age",
    y="Sales",
    hue="Region"
)

plt.show()
```

To inspect a palette
```
sns.color_palette("Set2")
```
- Common palettes include "Set2", "pastel", "muted", and "colorblind".

### 9. Saving a Figure
Use savefig() to save a plot to an image file.
```
fig, ax = plt.subplots(figsize=(8, 5))
sns.scatterplot(data=df, x="Age", y="Sales", ax=ax)
ax.set_title("Age vs. Sales")
fig.savefig("sales_plot.png", dpi=300, bbox_inches="tight")

plt.show()
```
- "sales_plot.png" — The output filename.
- dpi=300 — Sets the image resolution.
- bbox_inches="tight" — Helps prevent labels from being cut off.
