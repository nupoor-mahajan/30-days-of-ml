# 📝 Day 5 Notes - Data Cleaning

## What is Data Cleaning?

Data Cleaning is the process of detecting and correcting errors, inconsistencies, and missing information in a dataset.

Raw data is often:

* Incomplete
* Incorrect
* Duplicated
* Inconsistent

Machine Learning models perform better when trained on clean data.

---

# Why Data Cleaning is Important

Imagine a student dataset:

| Name   | Age | Marks |
| ------ | --- | ----- |
| Nupoor | 19  | 85    |
| Aditi  | NaN | 78    |
| Riya   | 18  | NaN   |

Problems:

* Missing age
* Missing marks

If these issues are ignored:

* Analysis becomes inaccurate
* ML models learn incorrect patterns

Therefore, cleaning data is a critical preprocessing step.

---

# Missing Values

Missing values occur when information is unavailable.

Examples:

```python
Age = NaN
Salary = NaN
City = NaN
```

---

## Detect Missing Values

```python
df.isnull()
```

Returns:

```python
True
False
```

where:

* True → Missing value exists
* False → Value is present

---

## Count Missing Values

```python
df.isnull().sum()
```

Example Output:

```python
Age       5
Salary    2
City      0
```

This shows the number of missing values in each column.

---

# Handling Missing Values

## Method 1: Remove Missing Data

```python
df.dropna()
```

Removes rows containing missing values.

Use when:

* Very few records are missing.

---

## Method 2: Fill Missing Values

Replace with a constant value:

```python
df.fillna(0)
```

Example:

```python
Age = NaN
```

becomes

```python
Age = 0
```

---

## Fill with Mean

Best for numerical columns.

```python
df["Age"].fillna(df["Age"].mean())
```

Example:

```python
Age values:
20, 25, 30
```

Mean:

```python
25
```

Missing values become:

```python
25
```

---

## Fill with Median

Useful when outliers exist.

```python
df["Salary"].fillna(df["Salary"].median())
```

---

## Fill with Mode

Best for categorical data.

```python
df["Gender"].fillna(df["Gender"].mode()[0])
```

Example:

```python
Male
Female
Male
Male
NaN
```

Missing value becomes:

```python
Male
```

because it occurs most frequently.

---

# Duplicate Records

Duplicates occur when the same record appears multiple times.

Example:

| Name   | Age |
| ------ | --- |
| Nupoor | 19  |
| Nupoor | 19  |

---

## Detect Duplicates

```python
df.duplicated()
```

Returns:

```python
True
False
```

---

## Count Duplicates

```python
df.duplicated().sum()
```

---

## Remove Duplicates

```python
df.drop_duplicates()
```

Removes repeated rows.

---

# Data Types

Every column has a data type.

Common Types:

| Type   | Meaning    |
| ------ | ---------- |
| int    | Integer    |
| float  | Decimal    |
| object | String     |
| bool   | True/False |

---

## Check Data Types

```python
df.dtypes
```

---

## Convert Data Types

Convert to integer:

```python
df["Age"] = df["Age"].astype(int)
```

Convert to float:

```python
df["Salary"] = df["Salary"].astype(float)
```

---

# Renaming Columns

Sometimes column names are too long.

Example:

```python
cholesterol_total
```

Rename it:

```python
df.rename(
    columns={
        "cholesterol_total": "cholesterol"
    }
)
```

Benefits:

* Easier coding
* Better readability

---

# Removing Unnecessary Columns

Not every column is useful.

Remove one column:

```python
df.drop("column_name", axis=1)
```

Remove multiple columns:

```python
df.drop(
    ["col1", "col2"],
    axis=1
)
```

---

# Outliers

Outliers are values that are unusually high or low.

Example:

```python
18
20
19
22
500
```

Here:

```python
500
```

is an outlier.

---

# Why Outliers Matter

Outliers can:

* Distort averages
* Affect model performance
* Produce misleading results

---

# Detecting Outliers

## Statistical Summary

```python
df.describe()
```

Check:

* Min
* Max
* Mean
* Quartiles

---

## Box Plot

```python
import matplotlib.pyplot as plt

df.boxplot(column="bmi")

plt.show()
```

Box plots visually identify extreme values.

---

# IQR Method

A common technique for detecting outliers.

Steps:

1. Calculate Q1
2. Calculate Q3
3. Compute IQR

```python
IQR = Q3 - Q1
```

4. Determine boundaries

```python
Lower = Q1 - 1.5 * IQR

Upper = Q3 + 1.5 * IQR
```

5. Values outside boundaries are outliers.

---

# String Cleaning

Real-world text often contains errors.

Example:

```python
" Male "
"male"
"MALE"
```

These should represent the same value.

---

## Remove Extra Spaces

```python
df["Gender"] = df["Gender"].str.strip()
```

---

## Convert to Lowercase

```python
df["Gender"] = df["Gender"].str.lower()
```

Output:

```python
male
female
```

---

## Convert to Uppercase

```python
df["Gender"] = df["Gender"].str.upper()
```

Output:

```python
MALE
FEMALE
```

---

# Unique Values

Find distinct values:

```python
df["Gender"].unique()
```

Output:

```python
['Male', 'Female']
```

---

# Frequency Counts

```python
df["Gender"].value_counts()
```

Output:

```python
Male      600
Female    400
```

Useful for spotting inconsistent entries.

---

# Final Dataset Validation

Before moving to Machine Learning:

Check:

```python
df.info()
```

Verify:

* Correct data types
* No unexpected missing values

---

Check:

```python
df.isnull().sum()
```

Verify:

* Missing values handled

---

Check:

```python
df.describe()
```

Verify:

* Reasonable statistics
* Outliers addressed

---

# Exporting Cleaned Data

Save processed dataset:

```python
df.to_csv(
    "cleaned_data.csv",
    index=False
)
```

This creates a new clean dataset ready for Machine Learning.

---

# Typical Data Cleaning Workflow

```python
import pandas as pd

df = pd.read_csv("data.csv")

df = df.drop_duplicates()

df["Age"] = df["Age"].fillna(
    df["Age"].mean()
)

df["Gender"] = df["Gender"].fillna(
    df["Gender"].mode()[0]
)

df.to_csv(
    "cleaned_data.csv",
    index=False
)
```

---

# Key Takeaways

* Data Cleaning improves data quality.
* Missing values must be handled.
* Duplicate records should be removed.
* Data types should be correct.
* Outliers can affect model performance.
* String values should be standardized.
* Always validate data before training ML models.
* Clean data leads to better Machine Learning results.
