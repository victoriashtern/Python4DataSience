

# Seaborn Graph Customization

## 1\. Introduction

Graph customization is the process of modifying the appearance and layout of visualizations to make them clearer, more informative, and visually appealing.

Seaborn provides built-in functions for customizing themes, styles, and color palettes. It also integrates with Matplotlib, allowing users to control figure dimensions, titles, axis labels, ticks, annotations, and other visual elements.

Most advanced customization methods are provided by Matplotlib and can be used with Seaborn plots.

## 2\. Graph Customization Methods

The following table summarizes the main methods used to customize Seaborn visualizations.

| Category | Methods | Purpose |
| --- | --- | --- |
| Figure Layout and Size | `plt.subplots()`, `figsize`, `subplots_adjust()` | Control figure dimensions and spacing. |
| Titles and Labels | `set_title()`, `set_xlabel()`, `set_ylabel()` | Add titles and axis labels. |
| Axis Limits | `set_xlim()`, `set_ylim()` | Control the visible ranges of the axes. |
| Ticks | `set_xticks()`, `set_yticks()`, `tick_params()` | Customize tick positions and appearance. |
| Annotations | `annotate()` | Highlight specific data points with text and arrows. |
| Themes and Styles | `sns.set_theme()`, `sns.set_style()` | Change backgrounds, grids, and overall visual appearance. |
| Colors and Palettes | `sns.color_palette()`, `sns.set_palette()` | Select and apply color palettes. |
| Saving Figures | `savefig()` | Export visualizations to image and document formats. |

## 3\. Preparing the Data

Run this setup first. The following examples reuse `df`.

python

```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

df = pd.DataFrame({
    "Age": [22, 25, 30, 35, 40, 45],
    "Sales": [200, 250, 300, 350, 400, 450],
    "Region": ["East", "West", "East", "West", "East", "West"]
})
```

## 4\. Figure Layout and Size

Figure layout controls the dimensions of a graph and the spacing around its elements.

### 4.1 Create a Figure and Axes

**Method:** `plt.subplots()`

**Purpose:** Creates a figure and one or more axes for plotting.

python

```python
fig, ax = plt.subplots(figsize=(8, 5))

sns.scatterplot(
    data=df,
    x="Age",
    y="Sales",
    ax=ax
)

plt.show()
```

- `plt.subplots()` — Creates a figure and an Axes object.
- `figsize=(8, 5)` — Sets the figure width to 8 inches and height to 5 inches.
- `ax=ax` — Draws the Seaborn plot on the specified axes.

### 4.2 Adjust Figure Spacing

**Method:** `fig.subplots_adjust()`

**Purpose:** Controls the margins and spacing around a plot.

python

```python
fig, ax = plt.subplots(figsize=(8, 5))

sns.scatterplot(data=df, x="Age", y="Sales", ax=ax)

fig.subplots_adjust(
    left=0.15,
    right=0.95,
    top=0.85,
    bottom=0.15
)

plt.show()
```

- `left` — Controls the left margin.
- `right` — Controls the right margin.
- `top` — Controls the top margin.
- `bottom` — Controls the bottom margin.

## 5\. Titles and Axis Labels

Titles and axis labels help explain what information a graph displays.

### 5.1 Set the Graph Title

**Method:** `ax.set_title()`

**Purpose:** Adds a title to the graph.

python

```python
fig, ax = plt.subplots()

sns.scatterplot(data=df, x="Age", y="Sales", ax=ax)

ax.set_title("Age vs. Sales")

plt.show()
```

### 5.2 Set Axis Labels

**Methods:** `ax.set_xlabel()` and `ax.set_ylabel()`

**Purpose:** Customize the labels displayed on the x-axis and y-axis.

python

```python
fig, ax = plt.subplots()

sns.scatterplot(data=df, x="Age", y="Sales", ax=ax)

ax.set_xlabel("Customer Age")
ax.set_ylabel("Sales Revenue")

plt.show()
```

### 5.3 Combine Titles and Labels

python

```python
fig, ax = plt.subplots(figsize=(8, 5))

sns.scatterplot(data=df, x="Age", y="Sales", ax=ax)

ax.set_title("Relationship Between Age and Sales")
ax.set_xlabel("Customer Age")
ax.set_ylabel("Sales Revenue")

plt.show()
```

## 6\. Axis Limits

Axis limits control the visible range of values displayed on a graph.

### 6.1 Set X-Axis Limits

**Method:** `ax.set_xlim()`

**Purpose:** Controls the minimum and maximum values displayed on the x-axis.

python

```python
fig, ax = plt.subplots()

sns.scatterplot(data=df, x="Age", y="Sales", ax=ax)

ax.set_xlim(20, 50)

plt.show()
```

### 6.2 Set Y-Axis Limits

**Method:** `ax.set_ylim()`

**Purpose:** Controls the minimum and maximum values displayed on the y-axis.

python

```python
fig, ax = plt.subplots()

sns.scatterplot(data=df, x="Age", y="Sales", ax=ax)

ax.set_ylim(150, 500)

plt.show()
```

### 6.3 Set Both Axis Limits

python

```python
fig, ax = plt.subplots()

sns.scatterplot(data=df, x="Age", y="Sales", ax=ax)

ax.set_xlim(20, 50)
ax.set_ylim(150, 500)

plt.show()
```

## 7\. Axis Ticks

Ticks are the marks and numerical labels displayed along the axes. They help readers interpret values on a graph.

### 7.1 Set X-Axis Ticks

**Method:** `ax.set_xticks()`

**Purpose:** Specifies the positions of the ticks on the x-axis.

python

```python
fig, ax = plt.subplots()

sns.scatterplot(data=df, x="Age", y="Sales", ax=ax)

ax.set_xticks([20, 30, 40, 50])

plt.show()
```

### 7.2 Set Y-Axis Ticks

**Method:** `ax.set_yticks()`

**Purpose:** Specifies the positions of the ticks on the y-axis.

python

```python
fig, ax = plt.subplots()

sns.scatterplot(data=df, x="Age", y="Sales", ax=ax)

ax.set_yticks([200, 300, 400, 500])

plt.show()
```

### 7.3 Customize Tick Appearance

**Method:** `ax.tick_params()`

**Purpose:** Changes the appearance of tick marks and their labels.

python

```python
fig, ax = plt.subplots()

sns.scatterplot(data=df, x="Age", y="Sales", ax=ax)

ax.tick_params(
    axis="both",
    labelsize=10,
    colors="blue"
)

plt.show()
```

- `axis="both"` — Applies the settings to both axes.
- `labelsize=10` — Sets the tick-label font size.
- `colors="blue"` — Changes the tick marks and labels to blue.

## 8\. Annotations

Annotations add explanatory text, arrows, or other visual information to highlight important points on a graph.

### 8.1 Add an Annotation

**Method:** `ax.annotate()`

**Purpose:** Highlights a particular data point with text and an optional arrow.

python

```python
fig, ax = plt.subplots()

sns.scatterplot(data=df, x="Age", y="Sales", ax=ax)

ax.annotate(
    "Highest Sales",
    xy=(45, 450),
    xytext=(32, 430),
    arrowprops={"arrowstyle": "->", "color": "red"}
)

plt.show()
```

- `xy=(45, 450)` — Specifies the data point to highlight.
- `xytext=(32, 430)` — Specifies the position of the annotation text.
- `arrowprops` — Controls the appearance of the arrow.

## 9\. Themes and Styles

Themes and styles control the overall appearance of Seaborn visualizations, including backgrounds, gridlines, and other visual elements.

### 9.1 Set a Theme

**Method:** `sns.set_theme()`

**Purpose:** Sets the overall visual theme for Seaborn plots.

python

```python
sns.set_theme(style="whitegrid")

sns.scatterplot(data=df, x="Age", y="Sales")

plt.show()
```

### 9.2 Set a Plot Style

**Method:** `sns.set_style()`

**Purpose:** Changes the background and grid appearance of Seaborn plots.

python

```python
sns.set_style("darkgrid")

sns.scatterplot(data=df, x="Age", y="Sales")

plt.show()
```

### Common Seaborn Styles

| Style | Appearance |
| --- | --- |
| `"whitegrid"` | White background with gridlines. |
| `"darkgrid"` | Gray background with gridlines. |
| `"white"` | White background without gridlines. |
| `"dark"` | Gray background without gridlines. |
| `"ticks"` | Clean background with axis tick marks. |

## 10\. Colors and Palettes

Color palettes control the colors used to represent categories and data in visualizations.

### 10.1 Set a Color Palette

**Method:** `sns.set_palette()`

**Purpose:** Sets the default color palette for subsequent Seaborn plots.

python

```python
sns.set_palette("Set2")

sns.scatterplot(
    data=df,
    x="Age",
    y="Sales",
    hue="Region"
)

plt.show()
```

### 10.2 Retrieve a Color Palette

**Method:** `sns.color_palette()`

**Purpose:** Retrieves a collection of colors for visualization.

python

```python
palette = sns.color_palette("Set2")

print(palette)
```

### 10.3 Display a Color Palette

python

```python
sns.color_palette("Set2")
```

### Common Seaborn Palettes

| Palette | Purpose |
| --- | --- |
| `"Set2"` | Provides distinct categorical colors. |
| `"pastel"` | Provides soft and light colors. |
| `"muted"` | Provides less saturated colors. |
| `"colorblind"` | Provides colors designed to improve accessibility for color-vision deficiencies. |
| `"deep"` | Provides a collection of moderately saturated colors. |
| `"bright"` | Provides bright and vivid colors. |

**Important:** A color palette can be applied globally using `sns.set_palette()` or individually through the `palette` parameter of supported plotting functions.

## 11\. Saving Figures

Saving figures allows you to export visualizations for reports, presentations, websites, and research documents.

### 11.1 Save a Figure

**Method:** `fig.savefig()`

**Purpose:** Exports a graph to a file.

python

```python
fig, ax = plt.subplots(figsize=(8, 5))

sns.scatterplot(data=df, x="Age", y="Sales", ax=ax)

ax.set_title("Age vs. Sales")

fig.savefig(
    "sales_plot.png",
    dpi=300,
    bbox_inches="tight"
)

plt.show()
```

- `"sales_plot.png"` — Specifies the output filename.
- `dpi=300` — Sets the image resolution to 300 dots per inch.
- `bbox_inches="tight"` — Helps prevent labels and other graph elements from being cut off.

### 11.2 Common File Formats

| Format | Extension | Common Application |
| --- | --- | --- |
| PNG | `.png` | General-purpose images and web graphics. |
| JPEG | `.jpg` | Compressed images. |
| PDF | `.pdf` | Reports and documents. |
| SVG | `.svg` | Scalable vector graphics for websites and design applications. |

Example:

python

```python
fig.savefig("sales_plot.png", dpi=300)
fig.savefig("sales_plot.pdf")
fig.savefig("sales_plot.svg")
```

## 12\. Summary of Graph Customization Methods

| Category | Method | Main Application |
| --- | --- | --- |
| Figure Layout | `plt.subplots()` | Creates a figure and axes. |
| Figure Size | `figsize` | Controls figure dimensions. |
| Figure Spacing | `subplots_adjust()` | Adjusts figure margins and spacing. |
| Titles | `set_title()` | Adds a graph title. |
| Axis Labels | `set_xlabel()`, `set_ylabel()` | Adds descriptive axis labels. |
| Axis Limits | `set_xlim()`, `set_ylim()` | Controls visible axis ranges. |
| Ticks | `set_xticks()`, `set_yticks()` | Controls tick positions. |
| Tick Appearance | `tick_params()` | Customizes tick marks and labels. |
| Annotations | `annotate()` | Highlights important data points. |
| Themes | `sns.set_theme()` | Sets the overall visualization theme. |
| Styles | `sns.set_style()` | Changes backgrounds and grid appearance. |
| Colors | `sns.set_palette()` | Sets the default color palette. |
| Color Palettes | `sns.color_palette()` | Retrieves a collection of colors. |
| Saving | `fig.savefig()` | Exports graphs to files. |

**Important Note:** Seaborn provides high-level visualization features, while Matplotlib provides additional control over figure layout and graph formatting. Combining both libraries allows you to create customized and publication-ready visualizations.
