# Day 8: Train-Test Split & Data Preparation

## 🎯 Goal

Learn how to prepare datasets for Machine Learning by selecting features, target variables, splitting data into training and testing sets, and understanding the ML workflow.

---

## 📚 Topics to Cover

### 1. Machine Learning Workflow

Understand the complete pipeline:

```text
Data Collection
      ↓
Data Cleaning
      ↓
Feature Selection
      ↓
Train-Test Split
      ↓
Model Training
      ↓
Prediction
      ↓
Evaluation
```

---

## 2. Features and Target Variables

### Features (X)

Input variables used to make predictions.

Examples:

* age
* bmi
* cholesterol
* heart_rate

```python
X = df[["age", "bmi", "cholesterol_total"]]
```

---

### Target (y)

The value we want to predict.

Example:

```python
y = df["diagnosed_diabetes"]
```

---

## 3. Understanding Train-Test Split

Why split data?

If we train and test on the same data:

* Model memorizes data
* Results become unrealistic

Solution:

Split dataset into:

* Training Set
* Testing Set

---

## 4. Training Data

Used to teach the model.

Typical size:

```text
80%
```

---

## 5. Testing Data

Used to evaluate model performance.

Typical size:

```text
20%
```

---

## 6. Using train_test_split()

Import:

```python
from sklearn.model_selection import train_test_split
```

Basic usage:

```python
X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)
```

---

## 7. Understanding Parameters

### test_size

Percentage reserved for testing.

Example:

```python
test_size=0.2
```

Means:

```text
80% Train
20% Test
```

---

### random_state

Ensures reproducible results.

Example:

```python
random_state=42
```

Using the same value gives the same split every time.

---

## 8. Checking Split Sizes

```python
print(X_train.shape)
print(X_test.shape)

print(y_train.shape)
print(y_test.shape)
```

Verify data was split correctly.

---

## 9. Feature Scaling (Introduction)

Why scale features?

Example:

```text
Age = 20

Salary = 500000
```

Large values can dominate smaller values.

---

### StandardScaler

Import:

```python
from sklearn.preprocessing import StandardScaler
```

Usage:

```python
scaler = StandardScaler()

X_train = scaler.fit_transform(X_train)

X_test = scaler.transform(X_test)
```

---

## 10. Understanding Data Leakage

Wrong:

```python
scaler.fit_transform(X)
```

Correct:

```python
scaler.fit_transform(X_train)

scaler.transform(X_test)
```

Never learn from test data.

---

### Features

```python
[
    "age",
    "bmi",
    "cholesterol_total",
    "heart_rate"
]
```

### Target

```python
diagnosed_diabetes
```

Tasks:

* Load data
* Select features
* Select target
* Split data
* Scale features
* Print results

---

## 📦 Libraries Required

```bash
pip install scikit-learn
```

---

## 📁 Deliverables

* day8.ipynb
* notes.md
* practice.py

---

## 🎓 Learning Outcomes

By the end of Day 8 you should be able to:

* Identify features and targets
* Understand ML workflow
* Split data correctly
* Use train_test_split()
* Understand training vs testing data
* Apply StandardScaler
* Avoid data leakage

---

## ✅ Completion Checklist

* [ ] Dataset loaded
* [ ] Features selected
* [ ] Target selected
* [ ] Train-test split completed
* [ ] Shapes verified
* [ ] Feature scaling applied
* [ ] Data leakage understood
* [ ] Practice exercises completed
