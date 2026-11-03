# Pandas Data Types – Quick Learning Guide

## 1\. Understanding Data Types

Every Pandas column has a data type that identifies the kind of data it contains.

| Data Type | Description | Example |
| --- | --- | --- |
| int64 | Whole numbers | 25 |
| float64 | Decimal numbers | 25.50 |
| object | General objects, often text | John |
| string | Pandas text type | London |
| bool | True/False | True |
| Int64 | Nullable integer | 25, <NA> |
| boolean | Nullable Boolean | True, <NA> |
| datetime64\[ns\] | Date/time | 2025-01-10 |
| timedelta64\[ns\] | Time difference | 5 days |
| category | Categorical values | Male, Female |

## 2\. dtype vs dtypes

These are attributes, not functions. Do not use parentheses.

````
df['Age'].dtype  # Check one column
df.dtypes        # Check all columns
````

Example output:

text

text
Name       object
Age         int64
Salary    float64
dtype: object


| Attribute | Purpose |
| --- | --- |
| dtype | Data type of one column |
| dtypes | Data types of all columns |

---

## 3\. select\_dtypes()

**Purpose:** Select columns based on their data types. Does not change the original DataFrame.

**Syntax:**

````
df.select_dtypes(include=None, exclude=None)
````

### Parameters

| Parameter | Description |
| --- | --- |
| include | Types you want to select |
| exclude | Types you want to leave out |

### Common include values

| Value | Selects |
| --- | --- |
| 'number' | All numeric columns |
| 'integer' | Integer columns |
| 'float' | Decimal columns |
| 'int64' | 64-bit integers |
| 'float64' | 64-bit floats |
| 'object' | Object columns |
| 'string' | Pandas string columns |
| 'bool' | Boolean columns |
| 'datetime' | Date/time columns |
| 'timedelta' | Time differences |
| 'category' | Categorical columns |

You can also use NumPy types such as np.number, np.integer and np.floating.

### Example dataset

````
import pandas as pd

df = pd.DataFrame({
    'Name': ['John', 'Sara', 'Mike'],
    'Age': [25, 30, 35],
    'Salary': [45000.50, 52000.75, 60000.00],
    'Passed': [True, False, True],
    'Joining_Date': pd.to_datetime([
        '2023-01-10', '2022-05-15', '2024-03-20'
    ])
})
````

### Examples and outputs

**1\. Select numeric columns**

````
numeric_cols = df.select_dtypes(include='number')
````

Output: Age, Salary

**2\. Select text columns**

````
text_cols = df.select_dtypes(include='object')
````

Output: Name

**3\. Select Boolean columns**

````
boolean_cols = df.select_dtypes(include='bool')
````

Output: Passed

**4\. Select datetime columns**

````
date_cols = df.select_dtypes(include='datetime')
````

Output: Joining_Date

**5\. Select multiple types**

````

selected = df.select_dtypes(
    include=['int64', 'float64']
)
````

Output: Age, Salary

**6\. Exclude numeric columns**

````
non_numeric = df.select_dtypes(exclude='number')
````

Output: Name, Passed, Joining_Date

**Remember:** include selects; exclude removes. At least one must be specified.

---

## 4\. astype()

**Purpose:** Convert a column into a specific data type.

**Syntax:**

````
df.astype(dtype, copy=None, errors='raise')
````

### Parameters

| Parameter | Description | Possible values |
| --- | --- | --- |
| dtype | Desired data type | int, float, str, bool, string, etc. |
| copy | Copy behaviour | True, False, None |
| errors | Handle conversion errors | 'raise', 'ignore' |

### Examples

````
df['Age'] = df['Age'].astype('int64')

df['Salary'] = df['Salary'].astype('float64')

df['Name'] = df['Name'].astype('string')
````


Convert multiple columns:

````
df = df.astype({
    'Age': 'int64',
    'Salary': 'float64'
})
````


**Remember:** Use astype() when you know exactly which data type you need. Invalid values can cause errors.

---

## 5\. convert\_dtypes()

**Purpose:** Automatically improve column data types, particularly when missing values are present.

**Syntax:**

````
df.convert_dtypes(
    infer_objects=True,
    convert_string=True,
    convert_integer=True,
    convert_boolean=True,
    convert_floating=True,
    dtype_backend='numpy_nullable'
)
````


### Parameters

| Parameter | Description |
| --- | --- |
| infer_objects | Infer better types for object columns |
| convert_string | Convert suitable text columns |
| convert_integer | Convert to nullable integers |
| convert_boolean | Convert to nullable Boolean |
| convert_floating | Convert to nullable floats |
| dtype_backend | Choose nullable data type backend |

### Possible dtype\_backend values

- 'numpy_nullable' – Pandas nullable types (default).
- 'pyarrow' – PyArrow-backed types (requires PyArrow).

### Example

````
df = pd.DataFrame({
    'Age': [25, 30, None, 35],
    'Name': ['John', 'Sara', 'Mike', 'Emma']
})

df = df.convert_dtypes()

print(df.dtypes)
````


Expected output:

text

text
Age              Int64
Name            string
dtype: object


**Remember:** Int64 supports missing values. convert_dtypes() improves types but does not generally parse arbitrary numeric text.

---

## 6\. pd.to\_numeric()

**Purpose:** Convert values stored as text into numeric values.

**Syntax:**

````
pd.to_numeric(arg, errors='raise', downcast=None)
````


### Parameters

| Parameter | Description | Possible values |
| --- | --- | --- |
| arg | Data to convert | Series, list, scalar |
| errors | Handle invalid values | 'raise', 'coerce', 'ignore' (deprecated) |
| downcast | Reduce numeric type size | 'integer', 'signed', 'unsigned', 'float' |

### Example

````
df = pd.DataFrame({
    'Marks': ['85', '90', 'ABC', '75']
})

df['Marks'] = pd.to_numeric(
    df['Marks'],
    errors='coerce'
)

print(df)
````


Output:

text

text
   Marks
0   85.0
1   90.0
2    NaN
3   75.0


### Important options

- errors='raise' – Raises an error for invalid values.
- errors='coerce' – Invalid values become NaN.
- downcast='integer' – Attempts to use a smaller integer type.
- downcast='float' – Attempts to use a smaller floating-point type.

**Remember:** Use this when numbers are stored as text.

---

## 7\. pd.to\_datetime()

**Purpose:** Convert text or numeric values into date/time format.

**Syntax:**

````
pd.to_datetime(
    arg,
    errors='raise',
    dayfirst=False,
    yearfirst=False,
    utc=False,
    format=None,
    exact=True,
    unit=None,
    origin='unix',
    cache=True
)
````


### Parameters

| Parameter | Description | Common values |
| --- | --- | --- |
| arg | Data to convert | Series, list, scalar |
| errors | Handle invalid dates | 'raise', 'coerce' |
| dayfirst | Day before month | True, False |
| yearfirst | Year before month/day | True, False |
| utc | Convert/localise to UTC | True, False |
| format | Specify date format | '%d-%m-%Y' |
| exact | Exact format matching | True, False |
| unit | Numeric timestamp unit | D, h, m, s, ms, us, ns |
| origin | Reference date | 'unix' or specified date |
| cache | Cache repeated dates | True, False |

### Example 1: Convert text to dates

````
df['Date'] = pd.to_datetime(
    df['Date'],
    errors='coerce'
)
````


Invalid dates become NaT (Not a Time).

### Example 2: Specify date format

````
dates = pd.to_datetime(
    ['15-02-2025', '20-03-2025'],
    format='%d-%m-%Y'
)
````


### Common date format codes

| Code | Meaning |
| --- | --- |
| %Y | Four-digit year |
| %y | Two-digit year |
| %m | Month |
| %d | Day |
| %H | Hour |
| %M | Minute |
| %S | Second |

### Example 3: Convert numeric timestamps

````
dates = pd.to_datetime(
    [0, 86400, 172800],
    unit='s'
)
````


**Remember:** Use pd.to_datetime() when dates are stored as text or numeric timestamps.

---

## 8\. Datetime .dt Accessor

After converting a column to datetime, use .dt to extract date information.

````
df['Date'] = pd.to_datetime(df['Date'])

df['Year'] = df['Date'].dt.year
df['Month'] = df['Date'].dt.month
df['Day'] = df['Date'].dt.day
df['Day_Name'] = df['Date'].dt.day_name()
````


### Common .dt attributes and methods

| Attribute/Method | Purpose |
| --- | --- |
| .dt.year | Extract year |
| .dt.month | Extract month |
| .dt.day | Extract day |
| .dt.hour | Extract hour |
| .dt.minute | Extract minute |
| .dt.dayofweek | Day number (Monday = 0) |
| .dt.day_name() | Weekday name |
| .dt.month_name() | Month name |
| .dt.quarter | Quarter |
| .dt.is_month_start | Check first day of month |
| .dt.is_month_end | Check last day of month |

---

## 9\. Practical Example – Cleaning a Dataset

Combine the functions in a real-world example.

````
import pandas as pd

df = pd.DataFrame({
    'Name': ['John', 'Sara', 'Mike', 'Emma'],
    'Age': ['25', '30', 'ABC', '35'],
    'Salary': ['45000', '52000', '48000', '60000'],
    'Joining_Date': [
        '2023-01-10',
        '2022-05-15',
        'Invalid',
        '2021-11-01'
    ]
})
````

# 1. Check original data types
print(df.dtypes)

# 2. Convert Age to numeric
df['Age'] = pd.to_numeric(
    df['Age'], errors='coerce'
)

# 3. Convert Salary to numeric
df['Salary'] = pd.to_numeric(df['Salary'])

# 4. Convert date column
df['Joining_Date'] = pd.to_datetime(
    df['Joining_Date'], errors='coerce'
)

# 5. Improve nullable types
df = df.convert_dtypes()

# 6. Select numeric columns
numeric_cols = df.select_dtypes(include='number')

# 7. Check final data types
print(df.dtypes)
print(df)

````


Expected final data types:

text

text
Name                    string
Age                      Int64
Salary                   Int64
Joining_Date    datetime64[ns]
dtype: object


The invalid Age value becomes <NA>, and the invalid date becomes NaT.

---

## 10\. Quick Revision

| Function / Attribute | Purpose | Example |
| --- | --- | --- |
| dtype | Check one column's type | df['Age'].dtype |
| dtypes | Check all column types | df.dtypes |
| select_dtypes() | Select columns by type | include='number' |
| astype() | Change data type | .astype(int) |
| convert_dtypes() | Improve data types | df.convert_dtypes() |
| pd.to_numeric() | Convert to numbers | errors='coerce' |
| pd.to_datetime() | Convert to dates | format='%Y-%m-%d' |
| .dt | Extract date components | .dt.year |

### Important terms

- NaN – Missing numeric value.
- NaT – Missing datetime value.
- <NA> – Missing value in nullable Pandas types.
- coerce – Replace invalid values with missing values.
- downcast – Attempt to reduce numeric storage size.
- nullable – Data type that supports missing values.

### Official Documentation

- [select\_dtypes()](<https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.select_dtypes.html>)
- [astype()](<https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.astype.html>)
- [convert\_dtypes()](<https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.convert_dtypes.html>)
- [to\_numeric()](<https://pandas.pydata.org/docs/reference/api/pandas.to_numeric.html>)
- [to\_datetime()](<https://pandas.pydata.org/docs/reference/api/pandas.to_datetime.html>)

---

**Study tip:** Focus on understanding when to use each function, what its parameters do, and how the output changes. You do not need to memorise every parameter immediately.
