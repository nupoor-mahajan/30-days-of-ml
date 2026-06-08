# 📝 Day 4 Notes - Pandas Fundamentals

## What is Pandas?

Pandas is a Python library used for:

* Data Analysis
* Data Manipulation
* Data Cleaning
* Working with CSV and Excel files

It provides powerful data structures that make handling data easy.

---

# Why Pandas?

Without Pandas:

* Data handling becomes difficult
* Manual processing takes time

With Pandas:

* Read datasets easily
* Filter data quickly
* Handle missing values
* Perform calculations efficiently

Pandas is one of the most important libraries in Machine Learning.

---

# Importing Pandas

```python
import pandas as pd
```

`pd` is simply an alias for Pandas.

---

# Pandas Data Structures

## 1. Series

A Series is a one-dimensional labeled array.

Example:

```python
import pandas as pd

s = pd.Series([10, 20, 30, 40])
print(s)
```

Output:

```python
0    10
1    20
2    30
3    40
```

Think of a Series as a single column in a table.

---

## 2. DataFrame

A DataFrame is a two-dimensional table.

Example:

```python
data = {
    "Name": ["Nupoor", "Aditi", "Riya"],
    "Age": [19, 20, 18]
}

df = pd.DataFrame(data)
print(df)
```

Output:

```python
     Name  Age
0  Nupoor   19
1   Aditi   20
2    Riya   18
```

A DataFrame is similar to an Excel spreadsheet.

---

# Reading Data

## CSV Files

```python
df = pd.read_csv("students.csv")
```

Loads a CSV file into a DataFrame.

---

# Viewing Data

## First Rows

```python
df.head()
```

Shows first 5 rows.

---

## Last Rows

```python
df.tail()
```

Shows last 5 rows.

---

## Random Rows

```python
df.sample(5)
```

Shows 5 random rows.

---

# Understanding Dataset Structure

## Shape

```python
df.shape
```

Output:

```python
(rows, columns)
```

Example:

```python
(100, 5)
```

Means:

* 100 rows
* 5 columns

---

## Columns

```python
df.columns
```

Displays all column names.

---

## Info

```python
df.info()
```

Shows:

* Number of entries
* Data types
* Missing values

---

## Describe

```python
df.describe()
```

Generates statistical summary:

* Mean
* Standard Deviation
* Minimum
* Maximum
* Quartiles

---

# Selecting Data

## Single Column

```python
df["Name"]
```

Returns a Series.

---

## Multiple Columns

```python
df[["Name", "Age"]]
```

Returns a DataFrame.

---

# Row Selection

## loc

Uses labels.

```python
df.loc[0]
```

Returns first row.

---

## iloc

Uses index position.

```python
df.iloc[0]
```

Returns first row.

---

# Filtering Data

Example:

```python
df[df["Age"] > 18]
```

Returns rows where age is greater than 18.

---

## Multiple Conditions

```python
df[(df["Age"] > 18) & (df["Marks"] > 80)]
```

Both conditions must be true.

---

# Sorting Data

Ascending:

```python
df.sort_values("Age")
```

Descending:

```python
df.sort_values("Age", ascending=False)
```

---

# Aggregation Functions

## Mean

```python
df["Marks"].mean()
```

Average value.

---

## Sum

```python
df["Marks"].sum()
```

Total value.

---

## Maximum

```python
df["Marks"].max()
```

Largest value.

---

## Minimum

```python
df["Marks"].min()
```

Smallest value.

---

## Count

```python
df["Marks"].count()
```

Counts non-null values.

---

# Missing Values

## Check Missing Values

```python
df.isnull()
```

Returns True for missing entries.

---

## Count Missing Values

```python
df.isnull().sum()
```

Shows total missing values per column.

---

## Remove Missing Values

```python
df.dropna()
```

Deletes rows containing missing values.

---

## Fill Missing Values

```python
df.fillna(0)
```

Replaces missing values with 0.

---

# Saving Data

```python
df.to_csv("output.csv", index=False)
```

Exports processed data into a CSV file.

---

# Common Pandas Workflow

```python
import pandas as pd

df = pd.read_csv("data.csv")

print(df.head())

print(df.info())

print(df.describe())

df = df.dropna()

df.to_csv("cleaned_data.csv", index=False)
```

---

# Key Takeaways

* Pandas is the most important library for handling datasets.
* Series = Single Column.
* DataFrame = Table of Data.
* `read_csv()` loads datasets.
* `head()` and `tail()` inspect data.
* `info()` and `describe()` summarize data.
* Filtering helps select useful records.
* Missing values must be handled before ML.
* Pandas is used in almost every Machine Learning project.
