## 5. Saving Figures

| Method or Parameter | Description | Example |
|---|---|---|
| savefig() | Saves a figure to a file | fig.savefig("plot.png") |
| .png | Raster image format | fig.savefig("plot.png", dpi=300) |
| .svg | Scalable vector image format | fig.savefig("plot.svg") |
| .pdf | Document format suitable for printing | fig.savefig("plot.pdf") |
| get_figure()| Retrieves the Figure associated with an Axes object | fig = ax.get_figure() |
| bbox_inches="tight" | Helps prevent labels and titles from being clipped | fig.savefig("plot.png", bbox_inches="tight") |


### 1. Prepare a plot
Create a plot first, then use the same figure for the saving examples.
```
import seaborn as sns
import matplotlib.pyplot as plt
import pandas as pd

df = pd.DataFrame({
    "Age": [22, 25, 30, 35, 40, 45],
    "Sales": [200, 250, 300, 350, 400, 450]
})

fig, ax = plt.subplots(figsize=(8, 5))

sns.scatterplot(data=df, x="Age", y="Sales", ax=ax)

ax.set_title("Age vs. Sales")
ax.set_xlabel("Age")
ax.set_ylabel("Sales")
```

### 2. Save a figure using savefig()
Saves the plot to a file.
```
fig.savefig("plot.png")
```
The file plot.png is saved in your current working directory.

### 3 Save as PNG
PNG is a raster image format, useful for sharing plots in documents and presentations.
```
fig.savefig("plot.png", dpi=300)
```
- dpi=300 sets the image resolution to 300 dots per inch.
- Higher DPI generally produces a sharper image.

### 4 Save as SVG
SVG is a vector format that can be enlarged without losing sharpness.
```
fig.savefig("plot.svg")
```
Useful for websites, diagrams, and graphics that need to be resized.

### 5. Save as PDF
PDF is useful for reports, academic papers, and printing.
```
fig.savefig("plot.pdf")
```

### 6. Retrieve the figure using get_figure()
If you already have an Axes object (ax), you can retrieve the Figure associated with it.
```
fig = ax.get_figure()
fig.savefig("sales_chart.png")
```
Here, ax is the plotting area, while fig is the complete figure containing the plot.

### 7. Prevent labels from being clipped
Use bbox_inches="tight" to reduce the chance of titles, labels, or other content being cut off.
```
fig.savefig(
    "plot_tight.png",
    dpi=300,
    bbox_inches="tight"
)
```
