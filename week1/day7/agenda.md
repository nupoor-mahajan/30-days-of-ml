# Day 7: Mini Project - Heart Disease Data Analysis

## 🎯 Goal

Apply NumPy, Pandas, Data Cleaning, and Data Visualization skills to perform a complete Exploratory Data Analysis (EDA) on a real-world dataset.

---

## 📚 Project Overview

You will analyze a Heart Disease dataset and generate insights using:

* Data Exploration
* Data Cleaning
* Statistical Analysis
* Data Visualization
* Feature Engineering

This project simulates a real Data Science workflow.

---

## 🛠 Skills Covered

### NumPy

* Mean
* Median
* Standard Deviation
* Variance

### Pandas

* Data Loading
* Data Inspection
* Filtering
* Aggregation
* Grouping

### Data Cleaning

* Missing Values
* Duplicate Records
* Outlier Detection
* Data Validation

### Visualization

* Histograms
* Bar Charts
* Scatter Plots
* Box Plots
* Correlation Heatmaps

---

# Project Tasks

## Step 1: Load Dataset

### Objectives

* Import dataset
* Verify successful loading

Commands:

```python
pd.read_csv()
df.head()
```

---

## Step 2: Dataset Exploration

### Objectives

Understand:

* Number of rows
* Number of columns
* Data types
* Missing values

Commands:

```python
df.shape
df.info()
df.describe()
df.columns
```

---

## Step 3: Data Cleaning

### Objectives

* Detect missing values
* Handle missing values
* Remove duplicates
* Identify outliers

Commands:

```python
df.isnull().sum()
df.drop_duplicates()
df.fillna()
```

---

## Step 4: Feature Engineering

### Objectives

Create a new feature:

```python
bp_difference =
systolic_bp - diastolic_bp
```

Learn:

* Creating columns
* Deriving useful information

---

## Step 5: Statistical Analysis

### Find

* Average Age
* Average BMI
* Maximum Cholesterol
* Minimum Heart Rate
* Diabetes Count

Commands:

```python
mean()
median()
max()
min()
value_counts()
```

---

## Step 6: Group-Based Analysis

### Analyze

Average BMI by Gender

```python
df.groupby("gender")["bmi"].mean()
```

Average Age by Diabetes Status

```python
df.groupby(
    "diagnosed_diabetes"
)["age"].mean()
```

---

## Step 7: Data Visualization

### Histogram

Age Distribution

---

### Bar Chart

Gender Distribution

---

### Scatter Plot

Age vs BMI

---

### Box Plot

BMI Outlier Detection

---

### Heatmap

Feature Correlation Analysis

---

## Step 8: Insight Generation

Answer Questions:

### Dataset Questions

1. What is the average age?
2. What is the average BMI?
3. Which gender appears most frequently?
4. How many diabetic patients exist?
5. Which smoking category is most common?

### Visualization Questions

6. Is BMI normally distributed?
7. Are there visible outliers?
8. Which features have strong correlations?

---

## Step 9: Export Processed Data

Save cleaned dataset:

```python
df.to_csv(
    "cleaned_heart_disease.csv",
    index=False
)
```

---

## Step 10: Project Report

Create:

```text
report.md
```

Include:

* Dataset Summary
* Cleaning Steps
* Statistical Findings
* Visual Insights
* Final Conclusions

---

## 📁 Deliverables

```text
Day-07-Mini-Project/
│
├── dataset/
│   └── heart_disease.csv
│
├── notebook.ipynb
├── cleaned_heart_disease.csv
├── report.md
├── README.md
└── visualizations/
```

---

## ✅ Completion Checklist

* [x] Dataset loaded successfully
* [x] Data explored
* [x] Missing values handled
* [x] Duplicates removed
* [x] Outliers identified
* [x] Feature engineering completed
* [x] Statistical analysis performed
* [x] Visualizations created
* [x] Insights documented
* [x] Cleaned dataset exported
* [x] Report completed
* [x] Project pushed to GitHub
