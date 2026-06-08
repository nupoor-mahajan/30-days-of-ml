# Day 6: Data Visualization

## 🎯 Goal

Learn how to visualize data using Matplotlib and Seaborn to identify patterns, trends, distributions, and relationships in datasets.

---

## 📚 Topics to Cover

### 1. Introduction to Data Visualization

* What is Data Visualization?
* Why visualization is important in Data Science and ML
* Understanding patterns through graphs

Benefits:

* Better understanding of data
* Easier identification of trends
* Detect anomalies and outliers
* Improve decision making

---

## 2. Matplotlib Basics

Import library:

```python
import matplotlib.pyplot as plt
```

Create a simple plot:

```python
x = [1,2,3,4,5]
y = [10,20,30,40,50]

plt.plot(x,y)
plt.show()
```

---

## 3. Line Plot

Used for:

* Trends over time
* Continuous data

Example:

```python
plt.plot(df["age"])
plt.show()
```

Learn:

* Title
* X-axis label
* Y-axis label
* Grid

---

## 4. Bar Chart

Used for:

* Comparing categories

Example:

```python
df["gender"].value_counts().plot(kind="bar")
plt.show()
```

---

## 5. Histogram

Used for:

* Data distribution
* Frequency analysis

Example:

```python
plt.hist(df["age"])
plt.show()
```

Understand:

* Bins
* Distribution shape
* Skewness

---

## 6. Pie Chart

Used for:

* Percentage contribution

Example:

```python
df["gender"].value_counts().plot(kind="pie")
plt.show()
```

---

## 7. Scatter Plot

Used for:

* Relationship between two variables

Example:

```python
plt.scatter(
    df["age"],
    df["bmi"]
)
plt.show()
```

Understand:

* Positive correlation
* Negative correlation
* No correlation

---

## 8. Box Plot

Used for:

* Outlier detection

Example:

```python
plt.boxplot(df["bmi"])
plt.show()
```

Observe:

* Median
* Quartiles
* Outliers

---

## 9. Seaborn Basics

Import:

```python
import seaborn as sns
```

Why Seaborn?

* Better looking plots
* Statistical visualizations
* Easier syntax

---

## 10. Count Plot

```python
sns.countplot(
    x="gender",
    data=df
)
plt.show()
```

---

## 11. Distribution Plot

```python
sns.histplot(
    df["bmi"],
    kde=True
)
plt.show()
```

---

## 12. Correlation Heatmap

Most important visualization in ML.

```python
corr = df.corr(numeric_only=True)

sns.heatmap(
    corr,
    annot=True
)

plt.show()
```

Learn:

* Positive correlation
* Negative correlation
* Feature relationships

---

## 13. Pair Plot

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

Shows relationships between multiple variables.

---

## 📝 Deliverables

* Visualization notebook
* Generated charts
* Observations document
* Updated Notes.md

---

## 📊 Key Learning Outcomes

By the end of Day 6 you should be able to:

* Create line charts
* Create bar charts
* Create histograms
* Create pie charts
* Create scatter plots
* Create box plots
* Use Seaborn effectively
* Interpret visual patterns
* Analyze feature relationships

---

## ✅ Completion Checklist

* [x] Created line plot
* [x] Created bar chart
* [x] Created histogram
* [x] Created pie chart
* [x] Created scatter plot
* [x] Created box plot
* [x] Used Seaborn
* [x] Created heatmap

