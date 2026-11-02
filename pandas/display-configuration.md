# Pandas – Display and Configuration Options

Pandas provides built-in configuration functions that allow you to customize how DataFrames and Series are displayed and manage global Pandas settings.

These functions are particularly useful when working with large datasets in Jupyter Notebook because they allow you to control the number of displayed rows, columns, column widths, and other display settings.

## 1\. List of Display and Configuration Methods

| Method | Description |
| --- | --- |
| pd.set_option() | Sets or changes a Pandas configuration option. |
| pd.get_option() | Retrieves the current value of a configuration option. |
| pd.reset_option() | Resets a configuration option to its default value. |
| pd.describe_option() | Displays documentation about available configuration options. |

## 2\. Syntax and Examples

### 2.1. pd.set\_option() – Set Configuration Options

Sets or changes a global Pandas configuration option.

**Syntax:**

```
pd.set_option(pat, value)
```

**Examples:**

```
import pandas as pd

# Display all rows
pd.set_option('display.max_rows', None)

# Display all columns
pd.set_option('display.max_columns', None)

# Display full column content
pd.set_option('display.max_colwidth', None)

# Set the maximum number of displayed rows to 20
pd.set_option('display.max_rows', 20)

# Set display width
pd.set_option('display.width', 1000)
```

**Common display options:**

| Option | Description |
| --- | --- |
| display.max_rows | Maximum number of displayed rows. |
| display.max_columns | Maximum number of displayed columns. |
| display.max_colwidth | Maximum width of column content. |
| display.width | Target display width in characters. |
| display.precision | Number of decimal places displayed for floating-point values. |
| display.expand_frame_repr | Controls whether wide DataFrames are printed across multiple lines. |
| display.show_dimensions | Controls whether DataFrame dimensions are shown in truncated output. |

### 2.2. pd.get\_option() – Get Configuration Options

Returns the current value of a specified Pandas configuration option.

**Syntax:**

```
pd.get_option(pat)
```

**Examples:**

```
# Get maximum displayed rows
pd.get_option('display.max_rows')

# Get maximum displayed columns
pd.get_option('display.max_columns')

# Get maximum column width
pd.get_option('display.max_colwidth')

# Get display precision
pd.get_option('display.precision')
```

**Example Output:**

```
pd.get_option('display.max_rows')
```

60


_Note: The output depends on your Pandas version and configuration._

### 2.3. pd.reset\_option() – Reset Configuration Options

Resets a specified configuration option to its default value.

**Syntax:**

```
pd.reset_option(pat)
```

**Examples:**

```

# Reset maximum rows
pd.reset_option('display.max_rows')

# Reset maximum columns
pd.reset_option('display.max_columns')

# Reset maximum column width
pd.reset_option('display.max_colwidth')

# Reset all display options
pd.reset_option('display')
```

_Note: Resetting an option restores its default value rather than removing the option._

### 2.4. pd.describe\_option() – Describe Configuration Options

Displays information about available Pandas configuration options, including their descriptions and default values.

**Syntax:**

```
pd.describe_option(pat=None)
```

**Examples:**

```
# Display information about all options
pd.describe_option()

# Display information about maximum rows
pd.describe_option('display.max_rows')

# Display information about display options
pd.describe_option('display')
```

## 3\. Practical Example: Configure DataFrame Display

Assume you have a DataFrame containing 100 rows and 10 columns.

```
import pandas as pd

# Create a sample DataFrame
data = {
    'Name': ['John', 'Mary', 'David', 'Anna', 'Peter'],
    'Age': [25, 30, 28, 35, 22],
    'Salary': [4000, 5000, 4500, 6000, 3500]
}

df = pd.DataFrame(data)

# Configure Pandas display settings
pd.set_option('display.max_rows', None)
pd.set_option('display.max_columns', None)

# Display DataFrame
display(df)
```

**Output:**

text

text
    Name  Age  Salary
0   John   25    4000
1   Mary   30    5000
2  David   28    4500
3   Anna   35    6000
4  Peter   22    3500


_Note: The example contains five records. With these settings, Pandas will display all rows and columns rather than truncating them._

## 4\. Practical Example: Manage Configuration Settings

```

import pandas as pd

# Set display options
pd.set_option('display.max_rows', 20)
pd.set_option('display.max_columns', 10)

# Retrieve current settings
print(pd.get_option('display.max_rows'))
print(pd.get_option('display.max_columns'))

# Reset settings to defaults
pd.reset_option('display.max_rows')
pd.reset_option('display.max_columns')

# Display configuration information
pd.describe_option('display.max_rows')
```

**Output:**

text

text
20
10


The remaining output provides documentation about the display.max_rows configuration option.

## 5\. Quick Reference

| Requirement | Function |
| --- | --- |
| Display all rows | pd.set_option('display.max_rows', None) |
| Display all columns | pd.set_option('display.max_columns', None) |
| Display full column content | pd.set_option('display.max_colwidth', None) |
| Check current row setting | pd.get_option('display.max_rows') |
| Reset row display setting | pd.reset_option('display.max_rows') |
| Reset all display settings | pd.reset_option('display') |
| View all configuration options | pd.describe_option() |
| View specific configuration details | pd.describe_option('display.max_rows') |

## 6\. Important Notes

- Configuration functions are top-level Pandas functions, not DataFrame methods.
- pd.set_option() changes the configuration for the current Python session.
- Display settings affect how DataFrames and Series are presented, not the underlying dataset.
- None can be used for certain display options, such as display.max_rows, to disable the corresponding display limit.
- pd.reset_option() restores the selected option to its default value.
- Displaying very large DataFrames may consume significant memory and make Jupyter Notebook slower.
- Configuration options and their default values may vary between Pandas versions.

## 7\. Official Documentation

- [Pandas Options and Settings](<https://pandas.pydata.org/docs/user_guide/options.html>)
- [Pandas General Functions](<https://pandas.pydata.org/pandas-docs/stable/reference/general_functions.html>)
- [Pandas API Reference](<https://pandas.pydata.org/docs/reference/index.html>)
