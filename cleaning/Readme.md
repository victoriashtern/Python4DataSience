
# A Structured Plan for Data Cleaning

Data cleaning is the process of identifying, investigating, and correcting data quality issues to make a dataset reliable and suitable for analysis. The process combines Exploratory Data Analysis (EDA), data cleaning, and validation.

The data analyst or data scientist is generally responsible for assessing data quality, deciding which cleaning actions are appropriate, and documenting the decisions. These decisions should be guided by the project objectives, business requirements, available documentation, and evidence from the dataset. When the meaning or importance of a variable is unclear, the analyst should consult relevant stakeholders or domain experts. In this phase Data visualization is heavily integrated into the broader exploration phase—specifically  such as using tools like histograms, box plots, and scatter plots are used to identify patterns, outliers, and data quality issues (Seaborn, MathLib and Plot methods are used)

## Phase 1: Understand and Explore the Data (EDA)

The goal is to understand the dataset, explore its characteristics, and identify potential data quality issues before making changes.
This initial step focuses primarily on reviewing documentation, data dictionaries, schema definitions, and business requirements rather than looking at charts.

### 1\. Understand the Dataset and Project Objectives
- Review the dataset's source, documentation, and data dictionary.
- Understand what each row represents and what each column measures.
- Clarify the project's objectives and the questions the analysis must answer.
- Identify important variables, identifiers, and expected relationships between columns.
- Consult business stakeholders or domain experts when the meaning or relevance of a variable is unclear.

**Outcome:** A clear understanding of the dataset, its purpose, and the requirements it must satisfy.


### 2\. Inspect the Data Structure
- Examine the number of rows and columns.
- Review column names and data types.
- Inspect sample records to understand how values are represented.
- Check for unexpected columns, malformed records, or structural inconsistencies.
- Identify columns that may require renaming, conversion, or further investigation.

**Outcome:** An understanding of the dataset's structure and potential structural problems.
**Solution:**  - 
- [panda.info()](panda_info.md) 
- When to use: Immediately after loading the dataset.
- What it does: Prints a concise summary of the DataFrame, including the total number of rows and columns, column names, non-null counts, and data types (int64, float64, object, etc.). It gives you a quick snapshot of potential data type errors and missing data.

### 3\. Explore Data Quality and Distributions
- Calculate summary statistics for numerical variables.
- Examine the frequency and distribution of categorical variables.
- Measure missing values and identify duplicate records.
- Investigate unusual values, inconsistent categories, and potential outliers.
- Use visualizations, such as histograms and box plots, to identify unexpected patterns.
- Compare observed values against documented business rules and expected ranges.

**Outcome:** A list of potential data quality issues that require investigation.
**Solution:**  - 
- [df.isnull() (or isna())](panda_info.md) 
- When to use: When checking for missing values.
- What it does: Returns a boolean DataFrame indicating whether values are missing. Combined with .sum() (df.isnull().sum()), it gives you the exact count of missing values per column.
- [panda.count()](panda_count.md) 
- When to use: To check non-missing data volume.
- What it does: Counts the number of non-null (valid) entries for each column, which helps you quickly compare total rows against valid rows.
- [panda.nunique()](panda_nuniqe.md) 
- When to use: When analyzing categorical columns, identifiers, or low-cardinality numerical columns.
- What it does: Counts the number of unique values in each column. This helps identify columns with only one unique value (useless for analysis) or unique IDs that shouldn't have duplicates.

## Phase 2: Decide What Needs Cleaning

Before modifying the DataFrame, the data analyst or data scientist should evaluate the identified issues and determine which actions are justified.

### 4\. Evaluate Columns and Records
- Identify irrelevant columns that do not contribute to the project's objectives.
- Identify redundant columns that duplicate information or provide no additional useful information.
- Identify rows that fall outside the scope of the analysis.
- Determine whether apparently unnecessary columns or records are required for auditing, validation, or future use.
- Consult stakeholders or domain experts when the meaning or importance of a column is uncertain.
- Document the reason for each proposed removal or modification.

Decisions should be based on the project objectives, business requirements, and evidence from the dataset, rather than assumptions based solely on column names or initial observations.

**Outcome:** A documented set of cleaning decisions and rules.

## Phase 3: Clean and Transform the Data

The goal is to apply the approved cleaning rules while preserving valid and useful information.

### 5\. Fix Structural Issues

- Rename columns to make them clear and consistent.
- Standardize column naming conventions.
- Remove irrelevant or redundant columns when their removal is justified.
- Remove records that fall outside the scope of the analysis.
- Correct structural problems, such as repeated headers or malformed rows.

### 6\. Handle Missing Values

- Identify missing values and measure their frequency.
- Detect placeholders such as empty strings, `"N/A"`, or `"Unknown"` where appropriate.
- Investigate why values are missing and whether their absence is meaningful.
- Drop rows or columns when justified by the analysis requirements.
- Impute missing values using an appropriate method when necessary.
- Preserve meaningful categories, such as `"Not applicable"`, when they represent valid information.

  **Solution:**  - 
- [Handling Missing Values](panda_missing_values.md) 

### 7\. Correct Data Types and Formats

- Convert columns to appropriate data types.
- Parse dates and timestamps consistently.
- Convert numerical values stored as strings.
- Standardize units of measurement and numerical formats.
- Investigate values that cannot be converted successfully.

### 8\. Standardize and Correct Values

- Remove unnecessary whitespace and unwanted characters.
- Standardize capitalization, spelling, and category labels.
- Correct known data-entry errors using documented rules or authoritative reference data.
- Normalize units, currencies, and other comparable measurements.
- Ensure equivalent values are represented consistently without changing their meaning.

### 9\. Resolve Duplicates and Invalid Values

- Identify exact duplicate rows.
- Investigate duplicates based on identifiers or combinations of columns.
- Remove or reconcile duplicate records according to documented rules.
- Detect values outside valid ranges or permitted categories.
- Investigate logical inconsistencies between columns.
- Assess potential outliers and decide whether to retain, correct, flag, or exclude them based on evidence and analytical requirements.

**Outcome of Phase 3:** A cleaned DataFrame with consistent structure, formats, and values, with problematic records handled according to documented rules.

## Phase 4: Validate and Document the Results

The goal is to verify that cleaning improved data quality without introducing errors or unnecessarily losing information.

### 10\. Validate the Cleaned Data

The data analyst or data scientist should:

- Recheck row counts, column counts, and data types.
- Reassess missing values and duplicates.
- Confirm that invalid values and inconsistencies have been addressed.
- Verify business rules, valid ranges, and relationships between variables.
- Compare summary statistics and distributions before and after cleaning.
- Investigate unexpected changes or remaining data quality issues.
- Repeat relevant cleaning steps if validation reveals new problems.

### 11\. Document and Preserve the Process

The data analyst or data scientist should:

- Record the problems identified and the actions taken.
- Document assumptions, exclusion criteria, and imputation methods.
- Explain why columns or records were removed or retained.
- Preserve the original dataset and apply changes to a working copy.
- Keep the cleaning steps reproducible in a script or notebook.
- Record how many rows were removed or modified.
- Save the cleaned dataset and document any remaining limitations.

**Outcome:** A validated, reproducible dataset ready for analysis or modeling, with documented decisions and known limitations.

## Summary of the Workflow

1. **Understand the data and objectives** — establish what the dataset represents and what the project requires.
2. **Explore the data (EDA)** — identify patterns and potential data quality issues.
3. **Evaluate and decide** — determine which issues need correction and justify each cleaning decision.
4. **Clean and transform** — apply appropriate changes while preserving valid information.
5. **Validate** — confirm that the cleaned dataset meets the required quality standards.
6. **Document** — record decisions, assumptions, and results to ensure reproducibility.

The data analyst or data scientist leads this process, using technical evidence and project requirements to make informed decisions and consulting stakeholders when necessary. Data cleaning is iterative: validation may reveal issues that require further investigation and cleaning.

To save it, copy the content into a text editor and save the file as `data_cleaning_plan.md`.
