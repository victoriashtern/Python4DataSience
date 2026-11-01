
# Pandas Data Import – Documentation and Reference

This documentation provides a structured reference for importing data into Python using pandas and related libraries.

It covers importing data from different file formats, websites, and databases, as well as reading specialized statistical files such as Stata datasets using `pyreadstat`.

The goal is to provide an overview of available import methods and link to detailed documentation, examples, and official resources.

## 1\. Documentation Overview

| File | Description |
| --- | --- |
| Pandas Data Import | Importing data from CSV, TSV, Excel, JSON, Stata, SAS, SPSS, HDF5, and SQL databases using pandas. |
| Python Database Connections | Connecting Python to SQLite, MySQL, PostgreSQL, Oracle, and Microsoft SQL Server databases. |
| Pyreadstat – Stata Reference | Reading Stata `.dta` files, selecting columns, and inspecting dataset metadata using pyreadstat. |
| Pandas Methods Reference | Common pandas functions, methods, attributes, and data manipulation examples. |
| Python Data Analysis Libraries | Overview of Python libraries used in data analysis, visualization, statistics, and machine learning. |

## 2\. Pandas Data Import Methods

Pandas provides several functions for importing data from different sources into a DataFrame.

| Data Source | Pandas Function | Description |
| --- | --- | --- |
| CSV | [pd.read_csv()](file.md)  | Reads comma-separated files. |
| TSV | `pd.read_csv(sep="\t")` | Reads tab-separated files. |
| Excel |  [pd.read_excel()](file.md)  | Reads Excel worksheets. |
| JSON |  [pd.read_json()](file.md)  | Reads JSON data. |
| HTML | `pd.read_html()` | Extracts tables from HTML pages. |
| XML | `pd.read_xml()` | Reads XML data. |
| Stata | [pd.read_stata()](stat.md) | Reads Stata `.dta` files. |
| SAS | `pd.read_sas()` | Reads SAS datasets. |
| SPSS | `pd.read_spss()` | Reads SPSS datasets. |
| HDF5 | `pd.read_hdf()` | Reads HDF5 datasets. |
| SQL | [pd.read_sql()](database.md) | Reads data from SQL queries or tables. |
| SQL Query | [pd.read_sql_query()](database.md)  | Executes a SQL query and returns the results as a DataFrame. |
| SQL Table | [pd.read_sql_table()](database.md)  | Reads an entire SQL database table into a DataFrame. |
| Parquet | `pd.read_parquet()` | Reads Parquet files. |
| Feather | `pd.read_feather()` | Reads Feather files. |
| Pickle | `pd.read_pickle()` | Reads serialized pandas objects. |

**Note:** Some import functions require optional dependencies. For example, Excel, database, and specialized statistical file readers may require additional packages.

## 3\. Specialized Data Import Libraries

Some file formats benefit from specialized Python libraries that provide additional functionality beyond pandas.

| Library | File Format / Database | Main Function | Purpose |
| --- | --- | --- | --- |
| pyreadstat | Stata, SAS, SPSS | `pyreadstat.read_dta()` | Reads statistical datasets and provides metadata. |
| openpyxl | Excel | `load_workbook()` | Reads and modifies Excel workbooks. |
| SQLAlchemy | SQL databases | `create_engine()` | Creates database connections and supports SQL operations. |
| sqlite3 | SQLite | `connect()` | Establishes connections to SQLite databases. |
| PyMySQL | MySQL | `connect()` | Connects Python applications to MySQL databases. |
| Psycopg | PostgreSQL | `connect()` | Connects Python applications to PostgreSQL databases. |
| python-oracledb | Oracle | `connect()` | Connects Python applications to Oracle databases. |

## 4\. Common Import Examples

### 4.1. Import a CSV File

python

```python
import pandas as pd

df = pd.read_csv("data.csv")
```

### 4.2. Import an Excel File

python

```python
import pandas as pd

df = pd.read_excel("data.xlsx")
```

### 4.3. Import a CSV File from a Website

python

```python
import pandas as pd

url = "https://example.com/data.csv"

df = pd.read_csv(url)
```

### 4.4. Import Data from a SQL Database

python

```python
import pandas as pd
import sqlite3

with sqlite3.connect("sales.db") as conn:
    df = pd.read_sql_query(
        "SELECT * FROM sales",
        conn
    )
```

### 4.5. Import a Stata File with pyreadstat

python

```python
import pyreadstat

df, meta = pyreadstat.read_dta("data.dta")
```

## 5\. Recommended Learning Sequence

For a structured learning approach, follow this order:

1. **Pandas Data Import** – Learn how to import common file formats.
2. **Python Database Connections** – Learn how to connect Python to database systems.
3. **Pyreadstat – Stata Reference** – Learn how to import Stata datasets and inspect metadata.
4. **Pandas Methods Reference** – Learn how to inspect, clean, transform, and analyze imported data.
5. **Python Data Analysis Libraries** – Explore additional libraries for more advanced analytical tasks.

## 6\. Official Documentation

- [Pandas Input/Output Guide](<https://pandas.pydata.org/docs/user_guide/io.html>)
- [Pandas Input/Output API Reference](<https://pandas.pydata.org/docs/reference/io.html>)
- [Pandas Documentation](<https://pandas.pydata.org/docs/>)
- [Pyreadstat Documentation](<https://github.com/Roche/pyreadstat>)
- [Python sqlite3 Documentation](<https://docs.python.org/3/library/sqlite3.html>)
- [SQLAlchemy Documentation](<https://docs.sqlalchemy.org/>)


**Purpose of this documentation:** To provide a central reference for importing data into Python, understanding available import functions, connecting to external data sources, and accessing detailed examples for each supported format.

Filename: `README.md`

Suggested location: Place it in the root directory of your `pandas-data-import/` folder so it serves as the main entry point for your documentation.
