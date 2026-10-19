
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


## Notes

- Some entries are built-in Python modules, such as `csv`, `json`, `statistics`, and `datetime`.
- Other libraries are third-party packages that must be installed separately.
- Import aliases are conventions rather than fixed names.
- Not every library is necessary for every project. Choose tools according to your data sources, analytical questions, and project requirements.
