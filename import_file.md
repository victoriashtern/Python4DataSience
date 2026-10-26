# Importing Data with Pandas

Pandas provides functions for importing data from different file formats, websites, and databases into a DataFrame.
- [Pandas Input/Output Guide](<https://pandas.pydata.org/docs/user_guide/io.html>)
- [Pandas](<https://pandas.pydata.org/docs/reference/api/pandas.read_csv.html>)[read_csv()](<https://pandas.pydata.org/docs/reference/api/pandas.read_csv.html>)
- [Pandas](<https://pandas.pydata.org/docs/reference/api/pandas.read_excel.html>)[read_excel()](<https://pandas.pydata.org/docs/reference/api/pandas.read_excel.html>)
- [Pandas](<https://pandas.pydata.org/docs/reference/api/pandas.read_json.html>)[read_json()](<https://pandas.pydata.org/docs/reference/api/pandas.read_json.html>)

## 1\. Common Data File Formats

| File Format | Extension | Description | Typical Contents |
| --- | --- | --- | --- |
| CSV | .csv | Comma-separated values | One table |
| TSV | .tsv | Tab-separated values | One table |
| Excel | .xlsx, .xls | Excel spreadsheet | One or more sheets |
| Stata | .dta | Stata statistical data file | Structured statistical data |
| JSON | .json | JavaScript Object Notation | Nested or tabular data |
| XML | .xml | Extensible Markup Language | Hierarchical data |
| SAS | .sas7bdat, .xpt | SAS statistical data files | Structured statistical data |
| SPSS | .sav | SPSS statistical data file | Structured statistical data |
| HDF5 | .h5, .hdf5 | Hierarchical Data Format | Large or complex datasets |
| ZIP | .zip | Compressed archive | One or more files |

## 2\. Pandas Data Import Methods

| Data Format | Pandas Method | Description |
| --- | --- | --- |
| CSV | pd.read_csv(file) | Reads a CSV file into a DataFrame. |
| TSV | pd.read_csv(file, sep='\t') | Reads a tab-separated file. |
| Excel | pd.read_excel(file) | Reads an Excel worksheet. |
| Stata | pd.read_stata(file, columns=...) | Reads a Stata dataset. |
| JSON | pd.read_json(file) | Reads JSON data. |
| HDF5 | pd.read_hdf(file, key=...) | Reads data from an HDF5 file. |
| SAS | pd.read_sas(file) | Reads a SAS dataset. |
| SPSS | pd.read_spss(file) | Reads an SPSS dataset. |
| SQL database | pd.read_sql_query(query, con) | Executes a SQL query and returns its results as a DataFrame. |

**Note:** The exact parameters depend on the method and file format. For example, read_hdf() generally requires a key identifying the stored dataset.

## 3\. Importing a CSV File from a Website

Use pd.read_csv() with the URL of the CSV file.


```
import pandas as pd

mortality_url = "https://www.murach.com/python_analysis/mortality.csv"
mortality_data = pd.read_csv(mortality_url)
print(mortality_data.head())
```

**Explanation:**

- mortality_url stores the web address of the CSV file.
- pd.read_csv() downloads and reads the CSV data.
- mortality_data stores the result as a DataFrame.
- head() displays the first five rows by default.

## 4\. Importing an Excel File

Use pd.read_excel() to read an Excel file stored on your computer.

```
import pandas as pd
jobs = pd.read_excel("oesm18all/all_data_M_2018.xlsx")
print(jobs.head())
```

By default, read_excel() reads the first worksheet.

To select a specific worksheet:

```
jobs = pd.read_excel(
    "oesm18all/all_data_M_2018.xlsx",
    sheet_name="Sheet1"
)
```

Replace "Sheet1" with the actual worksheet name.

## 5\. General Rules for Importing Data

- **Tabular data:** Pandas can usually import data directly into a DataFrame when the source has a compatible table structure.
- **Website files:** Pass the file URL to the relevant read function.
- **Local files:** Pass the file path to the relevant read function.
- **File paths:** Use the correct directory and filename.
- **Complex data:** Nested JSON, XML, or hierarchical files may require additional processing after importing.
- **Missing or invalid data:** Check the imported DataFrame for missing values, incorrect data types, and unexpected column names.

## 6\. Quick Reference

| Task | Example |
| --- | --- |
| Read a CSV file | pd.read_csv("data.csv") |
| Read a TSV file | pd.read_csv("data.tsv", sep="\t") |
| Read an Excel file | pd.read_excel("data.xlsx") |
| Read a JSON file | pd.read_json("data.json") |
| Read a Stata file | pd.read_stata("data.dta") |
| Read an HDF5 file | pd.read_hdf("data.h5", key="data") |
| Read a SAS file | pd.read_sas("data.sas7bdat") |
| Read an SPSS file | pd.read_spss("data.sav") |
| Run a SQL query | pd.read_sql_query("SELECT * FROM table_name", connection) |

