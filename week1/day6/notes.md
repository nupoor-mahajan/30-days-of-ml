# 📝 Day 6 Notes - Data Visualization

# What is Data Visualization?

Data Visualization is the graphical representation of data using charts, graphs, and plots.

Instead of reading thousands of rows, we can quickly understand data through visuals.

Example:

Instead of:

```python
Age:
18
20
21
22
25
30
35
```

A graph immediately shows the distribution and trends.

---

# Why is Data Visualization Important?

Visualization helps us:

* Understand data quickly
* Identify patterns
* Detect outliers
* Find relationships between variables
* Make better decisions

In Machine Learning, visualization is often performed before model training.

---

# Matplotlib

Matplotlib is the most popular Python library for creating graphs and plots.

Import:

```python
import matplotlib.pyplot as plt
```

The alias `plt` is commonly used.

---

# Line Plot

A Line Plot connects data points using lines.

Used for:

* Trends over time
* Continuous data

Example:

```python
import matplotlib.pyplot as plt

x = [1,2,3,4,5]
y = [10,20,30,40,50]

plt.plot(x,y)
plt.show()
```

Output:

A line joining all points.

---

## Adding Labels

```python
plt.plot(x,y)

plt.title("Sales Trend")
plt.xlabel("Month")
plt.ylabel("Sales")

plt.show()
```

Benefits:

* Better readability
* Professional appearance

---

# Bar Chart

A Bar Chart compares categories.

Example:

```python
cities = ["Mumbai","Delhi","Pune"]
population = [20,18,7]

plt.bar(cities,population)

plt.show()
```

Used for:

* Comparing groups
* Category frequencies

---

# Histogram

A Histogram shows data distribution.

Example:

```python
plt.hist(df["age"])

plt.show()
```

Used for:

* Frequency analysis
* Distribution analysis

---

## Understanding Bins

Bins divide data into intervals.

Example:

```python
plt.hist(
    df["age"],
    bins=10
)
```

More bins:

* More detail

Fewer bins:

* Simpler view

---

# Pie Chart

Pie charts show percentages.

Example:

```python
gender_counts = df["gender"].value_counts()

plt.pie(
    gender_counts,
    labels=gender_counts.index
)

plt.show()
```

Used for:

* Proportion analysis

---

# Scatter Plot

A Scatter Plot shows relationships between two variables.

Example:

```python
plt.scatter(
    df["age"],
    df["bmi"]
)

plt.show()
```

Each point represents one observation.

---

# Correlation

Scatter plots help identify correlation.

## Positive Correlation

As X increases, Y increases.

Example:

```text
Age ↑
BMI ↑
```

---

## Negative Correlation

As X increases, Y decreases.

Example:

```text
Exercise ↑
Weight ↓
```

---

## No Correlation

No clear pattern exists.

---

# Box Plot

A Box Plot helps detect outliers.

Example:

```python
plt.boxplot(df["bmi"])

plt.show()
```

Shows:

* Minimum
* Maximum
* Median
* Quartiles
* Outliers

---

# Understanding Box Plot Components

## Median

Middle value.

Represented by the line inside the box.

---

## Quartiles

Q1 = 25th percentile

Q3 = 75th percentile

---

## IQR

Interquartile Range:

```python
IQR = Q3 - Q1
```

Used for outlier detection.

---

# Seaborn

Seaborn is built on top of Matplotlib.

Import:

```python
import seaborn as sns
```

Advantages:

* Better aesthetics
* Less code
* Statistical visualizations

---

# Count Plot

Displays category frequencies.

Example:

```python
sns.countplot(
    x="gender",
    data=df
)

plt.show()
```

Useful for:

* Class balance checking
* Category comparison

---

# Histogram with KDE

```python
sns.histplot(
    df["bmi"],
    kde=True
)

plt.show()
```

KDE = Kernel Density Estimate

Provides a smooth distribution curve.

---

# Correlation Matrix

Correlation measures relationships between variables.

Range:

```text
+1 = Strong Positive Correlation

0 = No Correlation

-1 = Strong Negative Correlation
```

---

# Creating Correlation Matrix

```python
corr = df.corr(
    numeric_only=True
)

print(corr)
```

---

# Heatmap

A Heatmap visualizes correlations.

Example:

```python
sns.heatmap(
    corr,
    annot=True
)

plt.show()
```

---

## Interpreting Heatmaps

### Strong Positive Correlation

```text
0.8 to 1.0
```

Variables move together.

---

### Strong Negative Correlation

```text
-0.8 to -1.0
```

Variables move in opposite directions.

---

### Weak Correlation

```text
Near 0
```

Little relationship.

---

# Pair Plot

Displays relationships among multiple variables.

Example:

```python
sns.pairplot(
    df[
        ["age",
         "bmi",
         "heart_rate"]
    ]
)

plt.show()
```

Useful for:

* Exploratory Data Analysis (EDA)
* Detecting trends

---

# Common Visualization Workflow

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv("data.csv")

plt.hist(df["age"])
plt.show()

sns.countplot(
    x="gender",
    data=df
)

plt.show()

corr = df.corr(
    numeric_only=True
)

sns.heatmap(
    corr,
    annot=True
)

plt.show()
```

---

# Choosing the Right Chart

| Chart        | Use Case               |
| ------------ | ---------------------- |
| Line Plot    | Trends over time       |
| Bar Chart    | Compare categories     |
| Histogram    | Distribution           |
| Pie Chart    | Percentages            |
| Scatter Plot | Relationships          |
| Box Plot     | Outliers               |
| Heatmap      | Correlations           |
| Pair Plot    | Multiple relationships |

---

# Data Visualization in ML

Visualization is used before training models to:

* Understand data
* Detect missing values
* Identify outliers
* Study feature relationships
* Find useful patterns

This process is called:

**Exploratory Data Analysis (EDA)**

---

# Key Takeaways

* Visualization converts raw data into understandable charts.
* Matplotlib is the foundation of plotting in Python.
* Seaborn provides more advanced and attractive visualizations.
* Histograms show distributions.
* Scatter plots show relationships.
* Box plots detect outliers.
* Heatmaps reveal feature correlations.
* Visualization is a crucial step in Machine Learning workflows.
