# Day 5: Data Cleaning

## 🎯 Goal

Learn how to identify and fix common data quality issues before training Machine Learning models.

---

## 📚 Topics to Cover

### 1. Why Data Cleaning Matters

* Real-world datasets contain errors
* Missing values affect model performance
* Duplicate records create bias
* Incorrect data types cause issues
* Outliers can distort predictions

---

## 2. Understanding Missing Values

Check missing values:

```python
df.isnull()

df.isnull().sum()
```

Find columns containing missing data.

---

## 3. Handling Missing Values

### Remove Missing Values

```python
df.dropna()
```

### Fill Missing Values

Fill with constant value:

```python
df.fillna(0)
```

Fill numerical columns using mean:

```python
df["age"].fillna(df["age"].mean())
```

Fill categorical columns using mode:

```python
df["gender"].fillna(df["gender"].mode()[0])
```

---

## 4. Detecting Duplicates

Check duplicates:

```python
df.duplicated()
```

Count duplicates:

```python
df.duplicated().sum()
```

Remove duplicates:

```python
df.drop_duplicates()
```

---

## 5. Fixing Data Types

View data types:

```python
df.dtypes
```

Convert data types:

```python
df["age"] = df["age"].astype(int)
```

```python
df["salary"] = df["salary"].astype(float)
```

---

## 6. Renaming Columns

```python
df.rename(columns={"old_name":"new_name"})
```

Example:

```python
df.rename(columns={"cholesterol_total":"cholesterol"})
```

---

## 7. Removing Unnecessary Columns

```python
df.drop("column_name", axis=1)
```

Multiple columns:

```python
df.drop(["col1","col2"], axis=1)
```

---

## 8. Detecting Outliers

### Statistical Summary

```python
df.describe()
```

### Box Plot

```python
import matplotlib.pyplot as plt

df.boxplot(column="bmi")
plt.show()
```

---

## 9. Handling Outliers

Using IQR Method

```python
Q1 = df["bmi"].quantile(0.25)
Q3 = df["bmi"].quantile(0.75)

IQR = Q3 - Q1

lower = Q1 - 1.5 * IQR
upper = Q3 + 1.5 * IQR

df = df[(df["bmi"] >= lower) & (df["bmi"] <= upper)]
```

---

## 10. String Cleaning

Remove extra spaces:

```python
df["name"] = df["name"].str.strip()
```

Convert to lowercase:

```python
df["gender"] = df["gender"].str.lower()
```

Convert to uppercase:

```python
df["gender"] = df["gender"].str.upper()
```

---

## 11. Finding Unique Values

```python
df["gender"].unique()
```

```python
df["gender"].value_counts()
```

Useful for spotting inconsistent entries.

---

## 12. Final Data Validation

Check dataset after cleaning:

```python
df.info()

df.describe()

df.isnull().sum()
```

---

## 📝 Deliverables

* Data cleaning notebook
* Cleaned dataset
* Summary of issues found
* Notes.md updated

---

## ✅ Completion Checklist

* [x] Checked missing values
* [x] Filled missing values
* [x] Removed duplicates
* [x] Fixed data types
* [x] Cleaned string data
* [x] Detected outliers
* [x] Removed outliers
* [x] Exported cleaned dataset

