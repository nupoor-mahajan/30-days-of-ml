# Day 4: Pandas Fundamentals

## 🎯 Goal

Learn how to work with datasets using Pandas, the most important library for data manipulation and analysis in Python.

---

## 📚 Topics to Cover

### 1. Introduction to Pandas

* What is Pandas?
* Why Pandas is used in Data Science and ML
* Series vs DataFrame

---

### 2. Creating Data Structures

#### Series

* Creating a Series from a list
* Creating a Series with custom indices

#### DataFrame

* Creating DataFrames from dictionaries
* Creating DataFrames from lists
* Understanding rows and columns

---

### 3. Reading Data

* `pd.read_csv()`
* `pd.read_excel()`
* Viewing datasets

```python
df.head()
df.tail()
df.sample()
```

---

### 4. Dataset Information

```python
df.shape
df.columns
df.info()
df.describe()
```

Understand:

* Number of rows and columns
* Data types
* Missing values
* Statistical summary

---

### 5. Selecting Data

#### Single Column

```python
df["column"]
```

#### Multiple Columns

```python
df[["col1", "col2"]]
```

#### Rows

```python
df.loc[]
df.iloc[]
```

---

### 6. Filtering Data

Examples:

```python
df[df["Age"] > 25]
df[df["Salary"] > 50000]
```

Combining conditions:

```python
(df["Age"] > 25) & (df["Salary"] > 50000)
```

---

### 7. Sorting Data

```python
df.sort_values()
```

Sort by:

* Single column
* Multiple columns
* Ascending/Descending

---

### 8. Basic Aggregations

```python
df["Salary"].mean()
df["Salary"].sum()
df["Salary"].max()
df["Salary"].min()
df["Salary"].count()
```

---

### 9. Handling Missing Values

```python
df.isnull()
df.isnull().sum()
df.dropna()
df.fillna()
```

---

### 10. Exporting Data

```python
df.to_csv()
```

Save processed datasets.

---

## 📝 Deliverables

* Pandas practice notebook
* Completed exercises
* Mini task implementation
* Notes and observations

---

## ✅ Completion Checklist

* [x] Created Series and DataFrames
* [x] Loaded CSV files
* [x] Explored datasets
* [x] Selected and filtered data
* [x] Performed aggregations
* [x] Handled missing values
* [x] Exported processed data

