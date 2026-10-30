# Connecting to Databases in Python

Python provides several packages for connecting to databases. The appropriate package depends on the database system you want to use.
- [Python sqlite3](https://docs.python.org/3/library/sqlite3.html)
- [PyMySQL](https://pymysql.readthedocs.io/)
- [Psycopg](https://www.psycopg.org/)
- [python-oracledb](https://python-oracledb.readthedocs.io/)
- [pymssql](https://pymssql.readthedocs.io/)
- [Pandas SQL Queries](https://pandas.pydata.org/docs/reference/api/pandas.read_sql_query.html)

## 1. Python Packages for Database Connections

| Package | Database | Availability | Description |
|---|---|---|---|
| sqlite3 | SQLite | Built-in | Connects to SQLite databases without installing an additional package. |
| pymysql | MySQL | Needs to be installed | Provides a Python interface for MySQL databases. |
| psycopg2 | PostgreSQL | Needs to be installed | Connects Python applications to PostgreSQL databases. |
| oracledb | Oracle Database | Needs to be installed | Connects Python applications to Oracle databases. |
| pymssql | Microsoft SQL Server | Needs to be installed | Provides a Python interface for SQL Server. |

**Note:** oracledb is the modern Oracle Python driver; cx_Oracle is its predecessor. Package installation and additional client requirements vary by driver.

### Installation

Install the packages you need using pip:

bash
pip install pymysql psycopg2-binary oracledb pymssql


The sqlite3 module is included with Python, so it normally does not need to be installed separately.

## 2. Connecting to a SQLite Database

### The connect() Method

| Method | Description | Example |
|---|---|---|
| sqlite3.connect(path) | Returns a database connection object for the database identified by the path. | conn = sqlite3.connect("sales.db") |

Example:

python
import sqlite3

# Connect to a database (creates the file if it does not exist)
```
conn = sqlite3.connect("sales.db")
print("Connected to the database")
```

### The cursor() Method

| Method | Description | Example |
|---|---|---|
| cursor() | Returns a cursor object used to execute SQL statements and retrieve results. | cursor = conn.cursor() |

Example:

```
cursor = conn.cursor()
```

### Common Cursor Methods

| Method | Description | Example |
|---|---|---|
| execute(sql) | Executes a SQL statement. | cursor.execute("SELECT * FROM sales") |
| fetchall() | Returns all remaining rows from the executed query as a list of tuples. | rows = cursor.fetchall() |
| fetchone() | Returns the next row, or None if no rows remain. | row = cursor.fetchone() |
| fetchmany(size) | Returns up to the specified number of rows. | rows = cursor.fetchmany(5) |

## 3. Example: Querying a SQLite Database

```
import sqlite3

# Connect to the database
conn = sqlite3.connect("sales.db")

# Create a cursor
cursor = conn.cursor()

# Execute a SQL query
cursor.execute("SELECT * FROM sales")

# Retrieve all results
rows = cursor.fetchall()

# Display the results
for row in rows:
    print(row)

# Close the connection
conn.close()
```

**Important:** The sales table must exist in sales.db for this query to work.

## 4. Using Pandas with a Database

Pandas can execute SQL queries and load their results into a DataFrame.

```
import sqlite3
import pandas as pd

with sqlite3.connect("sales.db") as conn:
    df = pd.read_sql_query(
        "SELECT * FROM sales",
        conn
    )

print(df.head())
```

This is useful when you want to analyze database data using Pandas.

## 5. Database Connection Workflow

1. Import the appropriate database package.
2. Establish a connection using the database's connection method.
3. Create a cursor if needed.
4. Execute SQL statements.
5. Retrieve query results.
6. Close the connection when finished.
