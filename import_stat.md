# Reading Stata Files with pyreadstat

The read_dta() method from the pyreadstat package reads Stata (.dta) files and returns two objects: a DataFrame containing the data and a metadata object containing information about the dataset.
- [pyreadstat Documentation](https://github.com/Roche/pyreadstat)
- [pyreadstat on PyPI](https://pypi.org/project/pyreadstat/)

## 1. The read_dta() Method

| Method | Parameter | Description |
|---|---|---|
| pyreadstat.read_dta() | filename | The path to the Stata file to read. |
| pyreadstat.read_dta() | columns | Optional list of column names to read. |
| pyreadstat.read_dta() | metadataonly | If True, reads metadata without loading the dataset's data rows. |

### Example: Read a Stata File

```
import pyreadstat
df, meta = pyreadstat.read_dta("data.dta")

print(df.head())
print(meta.column_names)
```

## 2. Metadata Container Attributes

The metadata object provides information about the dataset without requiring you to inspect every row.

| Attribute | Description | Example |
|---|---|---|
| column_names | Names of the columns in the dataset. | meta.column_names |
| column_labels | Descriptive labels associated with the columns. | meta.column_labels |
| number_columns | Number of columns in the dataset. | meta.number_columns |
| number_rows | Number of rows in the dataset. | meta.number_rows |

### Example: Inspect Dataset Metadata

```
import pyreadstat

df, meta = pyreadstat.read_dta("data.dta")

print("Column names:", meta.column_names)
print("Column labels:", meta.column_labels)
print("Number of columns:", meta.number_columns)
print("Number of rows:", meta.number_rows)
```

## 3. Read Selected Columns

Use the columns parameter to load only the columns you need.

```
df, meta = pyreadstat.read_dta(
    "data.dta",
    columns=["age", "income"]
)

print(df.head())
```

## 4. Read Metadata Only

Use metadataonly=True when you need information about the dataset without loading its data rows.

```
df, meta = pyreadstat.read_dta(
    "data.dta",
    metadataonly=True
)

print(meta.column_names)
print(meta.number_rows)
```
