
# Python Modules and Libraries for Data Analysis

This guide summarizes Python modules and libraries commonly used in data analysis, data cleaning, statistical analysis, data visualization, machine learning, and data engineering.

## 1\. Data Manipulation and Numerical Computing

| Module / Library | Abbreviation | Purpose |
| --- | --- | --- |
| pandas | `pd` | Data manipulation, cleaning, and analysis using DataFrames. |
| NumPy | `np` | Numerical computing, arrays, matrices, and mathematical operations. |
| SciPy | `scipy` | Scientific computing, optimization, and statistical functions. |
| Polars | `pl` | Fast DataFrame operations and data transformation. |
| Dask | `dask` | Parallel and distributed computing for large datasets. |
| xarray | `xr` | Working with labeled multidimensional datasets. |

## 2\. Data Visualization

| Module / Library | Abbreviation | Purpose |
| --- | --- | --- |
| Matplotlib | `plt` | Creating charts, graphs, and customized visualizations. |
| Seaborn | `sns` | Statistical visualizations, including heatmaps and distribution plots. |
| Plotly Express | `px` | Creating interactive charts and graphs. |
| Plotly Graph Objects | `go` | Building detailed interactive visualizations. |
| Bokeh | — | Creating interactive visualizations for web browsers. |
| Altair | `alt` | Declarative statistical visualization based on data columns. |
| missingno | `msno` | Visualizing missing data in datasets. |
| Yellowbrick | — | Visualizing machine learning models and their performance. |

## 3\. Data Cleaning and Preparation

| Module / Library | Abbreviation | Purpose |
| --- | --- | --- |
| pyjanitor | — | Simplifying common DataFrame cleaning operations. |
| Great Expectations | `gx` | Validating data quality and defining data expectations. |
| Pandera | — | Validating DataFrame schemas and data types. |
| chardet | — | Detecting probable text-file encodings. |
| ftfy | — | Fixing common Unicode and text-encoding problems. |
| re | — | Finding, matching, and replacing text using regular expressions. |
| string | — | Working with string constants and text-related utilities. |

## 4\. Statistics and Probability

| Module / Library | Abbreviation | Purpose |
| --- | --- | --- |
| statistics | — | Basic descriptive statistics, averages, and measures of spread. |
| scipy.stats | `stats` | Statistical distributions, hypothesis testing, and probability calculations. |
| statsmodels | `sm` | Statistical modeling, regression, and statistical tests. |
| pingouin | `pg` | Statistical tests, effect sizes, and correlation analysis. |
| researchpy | — | Supporting statistical analysis and summary reporting. |
| SymPy | `sympy` | Symbolic mathematics, algebra, and equation solving. |

## 5\. Machine Learning and Predictive Analysis

| Module / Library | Abbreviation | Purpose |
| --- | --- | --- |
| scikit-learn | `sklearn` | Classification, regression, clustering, and model evaluation. |
| XGBoost | `xgb` | Gradient-boosted decision trees for predictive modeling. |
| LightGBM | `lgb` | Efficient gradient boosting for structured datasets. |
| CatBoost | — | Gradient boosting with support for categorical features. |
| TensorFlow | `tf` | Deep learning and neural network development. |
| Keras | — | Building and training neural networks through a high-level API. |
| PyTorch | `torch` | Deep learning, tensor computation, and neural networks. |
| imbalanced-learn | `imblearn` | Handling imbalanced classification datasets. |
| Optuna | `optuna` | Hyperparameter optimization for machine learning models. |
| SHAP | `shap` | Explaining machine learning model predictions. |
| Prophet | — | Forecasting time series data. |

## 6\. Time Series Analysis

| Module / Library | Abbreviation | Purpose |
| --- | --- | --- |
| datetime | `dt`\* | Working with dates, times, and time intervals. |
| time | — | Working with timestamps, elapsed time, and time-related operations. |
| dateutil | — | Parsing dates and performing flexible date calculations. |
| pandas.tseries | — | Date offsets, business calendars, and time series utilities. |
| statsmodels.tsa | `tsa` | Time series modeling, decomposition, and forecasting. |
| sktime | — | Machine learning for time series forecasting and analysis. |
| ruptures | — | Detecting change points in time series data. |

## 7\. File Handling and Data Import

| Module / Library | Abbreviation | Purpose |
| --- | --- | --- |
| pathlib | — | Managing file paths and directories. |
| os | — | Interacting with the operating system and file system. |
| glob | — | Finding files using wildcard patterns. |
| shutil | — | Copying, moving, and managing files and directories. |
| csv | — | Reading and writing CSV files. |
| json | — | Reading and writing JSON data. |
| pickle | — | Serializing and deserializing Python objects. |
| zipfile | — | Creating, reading, and extracting ZIP archives. |
| gzip | — | Reading and writing gzip-compressed files. |
| io | — | Working with in-memory streams and file-like objects. |
| openpyxl | — | Reading and writing Excel `.xlsx` files. |
| XlsxWriter | — | Creating and formatting Excel `.xlsx` files. |
| pyreadstat | — | Reading and writing statistical files, including SAS, SPSS, and Stata formats. |
| pyarrow | `pa` | Working with Apache Arrow and columnar data formats. |
| fastparquet | — | Reading and writing Parquet files. |

## 8\. Databases and Data Access

| Module / Library | Abbreviation | Purpose |
| --- | --- | --- |
| sqlite3 | — | Connecting to and querying SQLite databases. |
| SQLAlchemy | `sa` | Connecting to databases and working with SQL through a Python toolkit. |
| psycopg | — | Connecting to PostgreSQL databases. |
| pymysql | — | Connecting to MySQL databases. |
| duckdb | — | Running analytical SQL queries on local files and datasets. |
| pymongo | — | Working with MongoDB databases. |
| requests | — | Sending HTTP requests to web services and APIs. |
| urllib | — | Working with URLs and retrieving web resources. |
| httpx | — | Making synchronous and asynchronous HTTP requests. |
| Beautiful Soup (`bs4`) | `bs4` | Parsing HTML and extracting information from web pages. |
| lxml | — | Parsing and processing XML and HTML documents. |

## 9\. Geographic and Spatial Analysis

| Module / Library | Abbreviation | Purpose |
| --- | --- | --- |
| GeoPandas | `gpd` | Analyzing geographic data using spatial DataFrames. |
| Shapely | — | Creating and manipulating geometric objects. |
| Fiona | — | Reading and writing geographic vector data formats. |
| Rasterio | — | Reading and processing raster and geospatial image data. |
| PyProj | — | Working with coordinate reference systems and map projections. |
| Folium | — | Creating interactive maps using Leaflet. |
| contextily | — | Adding web map tiles as basemaps to geographic plots. |

## 10\. Data Quality, Profiling, and Exploration

| Module / Library | Abbreviation | Purpose |
| --- | --- | --- |
| ydata-profiling | — | Generating automated exploratory data analysis reports. |
| skimpy | — | Producing concise summaries of DataFrames. |
| Sweetviz | — | Generating visual data analysis and comparison reports. |
| fugue | — | Supporting distributed data processing across compatible execution engines. |

## 11\. Data Engineering and Big Data

| Module / Library | Abbreviation | Purpose |
| --- | --- | --- |
| PySpark | `pyspark` | Distributed data processing using Apache Spark. |
| Apache Beam | — | Building batch and streaming data processing pipelines. |
| Prefect | — | Orchestrating and monitoring data workflows. |
| Airflow | — | Scheduling and managing data pipelines. |
| dlt | — | Loading data from sources into destination systems. |

## 12\. Utilities and Programming Support

| Module / Library | Abbreviation | Purpose |
| --- | --- | --- |
| collections | — | Specialized data structures such as counters and default dictionaries. |
| itertools | — | Efficient iteration and combinatorial operations. |
| functools | — | Higher-order functions and function caching utilities. |
| math | — | Basic mathematical functions and constants. |
| decimal | — | Decimal arithmetic with controlled precision. |
| logging | — | Recording application events, warnings, and errors. |
| warnings | — | Displaying and controlling warning messages. |
| typing | — | Type hints for documenting and checking Python code. |
| tqdm | — | Displaying progress bars for loops and data-processing tasks. |
| joblib | — | Parallel computing and caching computational results. |
| concurrent.futures | — | Running tasks concurrently using threads or processes. |
| multiprocessing | — | Running computations across multiple processes. |
| pytest | — | Testing data-processing functions and Python code. |

\* `dt` is a user-defined alias sometimes used for `datetime`; it is not a standard import abbreviation.

## Recommended Starting Libraries

If you are learning practical data analysis, start with these libraries before moving into specialized areas:

1. **pandas and NumPy** — Data manipulation and numerical computing.
2. **Matplotlib and Seaborn** — Data visualization.
3. **SciPy and statsmodels** — Statistical analysis.
4. **openpyxl and requests** — Importing Excel data and accessing web resources.
5. **scikit-learn** — Predictive analysis and machine learning.
6. **SQLAlchemy and sqlite3** — Database access.
7. **ydata-profiling and Pandera** — Data exploration and data quality checks.


# Installing and Importing Python Modules

## 1\. Two Ways to Install a Python Module

You can install Python modules using `pip`, Python's package installer.

-**Method 1:** Install the Latest Available Version

Use the `pip install` command to install the latest version available from the configured package index.

```
pip install pyreadstat
```

-**Method 2:** Install a Specific Version

Use `==` to specify the exact package version you want to install.

```
pip install geopandas==0.14.3
```

**Note:** Installing a specific version can help maintain compatibility and reproducibility across projects.

## 2\. How to Import Python Modules

After installing a module, import it into your Python script or notebook to use its functionality.

### Method 1: Import a Module Using an Alias

Use the `as` keyword to assign a shorter name to a module.

```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

In this example:

- `pandas` is imported as `pd`.
- `numpy` is imported as `np`.
- `matplotlib.pyplot` is imported as `plt`.

### Method 2: Import a Specific Function or Object

Use `from ... import ...` to import a specific function, class, or object from a module.

```
from datetime import datetime
from math import sqrt
```

You can then use the imported objects directly:

```
current_time = datetime.now()
result = sqrt(25)

print(current_time)
print(result)
```

### Method 3: Import a Submodule

You can import a submodule from a larger package.

```
import matplotlib.pyplot as plt
import scipy.stats as stats
```

Here, `pyplot` is a submodule of `matplotlib`, and `stats` is a submodule of `scipy`.

### Method 4: Import Multiple Objects from a Module

You can import multiple functions or objects in one statement.

```
from math import sqrt, pi, ceil
```

Example:

```
print(sqrt(16))
print(pi)
print(ceil(4.2))
```

### Method 5: Import All Objects from a Module

Python also allows importing all public names from a module using `*`.

```
from math import *
```

However, this approach is generally **not recommended** because it can make it harder to identify where names come from and may cause naming conflicts.

## 3\. Summary

| Operation | Syntax | Purpose |
| --- | --- | --- |
| Install the latest version | `pip install package_name` | Install a package. |
| Install a specific version | `pip install package_name==version` | Install a particular version. |
| Import a module | `import pandas` | Import a complete module. |
| Import with an alias | `import pandas as pd` | Use a shorter module name. |
| Import a specific object | `from math import sqrt` | Import an individual function or object. |
| Import a submodule | `import matplotlib.pyplot as plt` | Import a module within a package. |
| Import multiple objects | `from math import sqrt, pi` | Import several selected objects. |

## 4\. Best Practices

- Install packages in the correct Python environment or virtual environment.
- Use common aliases, such as `pd` for pandas and `np` for NumPy.
- Pin package versions when reproducibility is important.
- Prefer explicit imports over `from module import *`.
- Restart your Jupyter kernel if necessary after installing a package that was previously unavailable.

## 5\. Installing Packages in Jupyter Notebook

If you are using Jupyter Notebook, you can install a package directly from a notebook cell using `%pip`.

```
%pip install pyreadstat
```

Using `%pip` helps install the package into the Python environment associated with the active notebook kernel.

## Notes

- Some entries are built-in Python modules, such as `csv`, `json`, `statistics`, and `datetime`.
- Other libraries are third-party packages that must be installed separately.
- Import aliases are conventions rather than fixed names.
- Not every library is necessary for every project. Choose tools according to your data sources, analytical questions, and project requirements.
