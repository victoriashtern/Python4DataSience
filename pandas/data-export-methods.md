# Pandas – Export Data

Pandas provides several built-in methods to export or save DataFrame data into different file formats and databases. These methods allow you to store, share, and use your processed data in other applications.

## 1\. List of Pandas Export Methods

| Method | Description | File Format |
| --- | --- | --- |
| to_csv() | Exports data into a CSV file. | .csv |
| to_excel() | Exports data into an Excel spreadsheet. | .xlsx |
| to_json() | Exports data into JSON format. | .json |
| to_sql() | Saves DataFrame data into a SQL database table. | Database |
| to_parquet() | Exports data into Parquet format. | .parquet |
| to_html() | Exports data into an HTML table. | .html |

## 2\. Syntax and Examples

### 1\. to\_csv() – Export to CSV

Saves a DataFrame into a comma-separated values (CSV) file.

```
df.to_csv('output.csv', index=False)
```

### 2\. to\_excel() – Export to Excel

Saves a DataFrame into an Excel spreadsheet.

```
df.to_excel('output.xlsx', index=False)
```

### 3\. to\_json() – Export to JSON

Saves a DataFrame into JavaScript Object Notation (JSON) format.

```
df.to_json('output.json', orient='records')
```

### 4\. to\_sql() – Export to SQL Database

Writes DataFrame records into a table in a SQL database.

```
from sqlalchemy import create_engine

engine = create_engine('sqlite:///database.db')

df.to_sql('employees', engine, if_exists='replace', index=False)
```

### 5\. to\_parquet() – Export to Parquet

Saves a DataFrame into Parquet, a column-oriented file format commonly used for analytical workloads.

```
df.to_parquet('output.parquet', index=False)
```

### 6\. to\_html() – Export to HTML

Converts a DataFrame into an HTML table and saves it as an HTML file.

```
df.to_html('output.html', index=False)
```

## 3\. Common Export Parameters

| Parameter | Description |
| --- | --- |
| path_or_buf | File path or output destination. |
| index | Whether to include DataFrame index. |
| columns | Select specific columns to export. |
| header | Include column names. |
| encoding | Specify file encoding. |
| sep | Specify the CSV delimiter. |
| mode | File writing mode. |
| na_rep | Representation for missing values. |
| if_exists | SQL table behavior if it already exists. |
| orient | Define JSON output structure. |

_Note: Parameters differ depending on the export method._

## 4\. Practical Example: Exporting a DataFrame

```
import pandas as pd

data = {
    'Name': ['John', 'Sarah', 'David'],
    'Age': [25, 30, 35],
    'Salary': [40000, 50000, 60000]
}

df = pd.DataFrame(data)

# Export data
df.to_csv('employees.csv', index=False)
df.to_excel('employees.xlsx', index=False)
df.to_json('employees.json', orient='records')
df.to_parquet('employees.parquet', index=False)
df.to_html('employees.html', index=False)
```

## 5\. Quick Reference: When to Use Each Method

| Export Method | Best Use Case |
| --- | --- |
| to_csv() | Sharing data between applications |
| to_excel() | Business reports and spreadsheets |
| to_json() | APIs and web applications |
| to_sql() | Storing data in relational databases |
| to_parquet() | Big data analytics and data pipelines |
| to_html() | Displaying data on websites |

## 6\. Important Takeaway

- **CSV:** Simple and widely supported data storage.
- **Excel:** Suitable for business users and reporting.
- **JSON:** Useful for web applications and APIs.
- **SQL:** Useful for storing and querying structured data.
- **Parquet:** Efficient for large analytical datasets.
- **HTML:** Useful for displaying tabular data in web pages.

## Official Documentation

[Pandas – Input and Output Documentation](<https://pandas.pydata.org/docs/user_guide/io.html>)
