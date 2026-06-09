# Train-Test Split & Data Preparation

# Introduction

Before training any model, data must be prepared correctly.

This preparation process is called **Data Preparation**.

---

# Machine Learning Workflow

A typical Machine Learning project follows this sequence:

```text
Collect Data
      ↓
Clean Data
      ↓
Explore Data
      ↓
Select Features
      ↓
Train-Test Split
      ↓
Train Model
      ↓
Predict
      ↓
Evaluate Model
```

---

# Features and Target

Machine Learning learns relationships between inputs and outputs.

## Features (X)

Features are the input variables used to make predictions.

Example:

| Age | BMI  | Cholesterol |
| --- | ---- | ----------- |
| 25  | 22.5 | 180         |
| 40  | 31.2 | 240         |

These columns are features.

```python
X = df[
    [
        "age",
        "bmi",
        "cholesterol_total"
    ]
]
```

---

## Target (y)

Target is the output variable we want to predict.

Example:

| Diabetes |
| -------- |
| 0        |
| 1        |

```python
y = df["diagnosed_diabetes"]
```

Where:

```text
0 = No Diabetes
1 = Diabetes
```

---

# Why Separate X and y?

Machine Learning learns:

```text
Features → Target
```

Example:

```text
Age
BMI
Cholesterol
      ↓
Diabetes Prediction
```

The model studies the features and learns patterns that predict the target.

---

# Train-Test Split

One of the most important concepts in Machine Learning.

Suppose we have:

```text
1000 rows
```

If we train and test on the same data:

```text
Model memorizes answers
```

This leads to:

```text
Unrealistically high accuracy
```

The model performs well on known data but fails on new data.

This problem is called:

**Overfitting**

---
## Underfitting

Underfitting occurs when a model is too simple to learn the patterns in the data.

### Characteristics

* Performs poorly on training data
* Performs poorly on testing data
* High bias
* Model fails to capture important relationships

### Example

Trying to fit a straight line to data that follows a curved pattern.

### Solution

* Use a more complex model
* Add more relevant features
* Train for longer
* Reduce regularization

---

## Overfitting

Overfitting occurs when a model learns the training data too well, including noise and unnecessary details.

### Characteristics

* Very high training accuracy
* Poor testing accuracy
* High variance
* Cannot generalize to new data

### Example

A student memorizes all practice questions instead of understanding concepts.

### Solution

* Use more training data
* Reduce model complexity
* Apply regularization
* Use cross-validation
* Remove irrelevant features

---

## Comparison

| Feature           | Underfitting | Overfitting |
| ----------------- | ------------ | ----------- |
| Training Accuracy | Low          | Very High   |
| Testing Accuracy  | Low          | Low         |
| Bias              | High         | Low         |
| Variance          | Low          | High        |
| Learns Patterns   | Poorly       | Too Much    |
| Generalization    | Poor         | Poor        |

---

## Ideal Model

A good model should:

* Learn important patterns from training data
* Ignore random noise
* Perform well on unseen data

This state is called **Good Fit** or **Balanced Model**.
---

# Solution: Train-Test Split

Divide data into two parts:

```text
Training Data
+
Testing Data
```

Example:

```text
80% Training
20% Testing
```

For 1000 rows:

```text
800 rows → Train

200 rows → Test
```

---

# Training Data

Training data is used to teach the model.

The model learns patterns from this data.

Example:

```text
Age
BMI
Cholesterol
      ↓
Diabetes
```

The model tries to understand how features influence the target.

---

# Testing Data

Testing data is never shown during training.

After training:

```text
Model predicts on test data
```

compare predictions with actual answers.

This tells us how well the model performs on unseen data.

---

# train_test_split()

Scikit-Learn provides a function for splitting datasets.

Import:

```python
from sklearn.model_selection import train_test_split
```

Basic Usage:

```python
X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)
```

---

# Understanding Parameters

## test_size

Determines how much data goes to testing.

Example:

```python
test_size=0.2
```

Means:

```text
20% Test

80% Train
```

Another example:

```python
test_size=0.3
```

Means:

```text
30% Test

70% Train
```

---

## random_state

Controls randomness.

Example:

```python
random_state=42
```

Using the same value:

```text
Same split every run
```

This ensures reproducible results.

42 is commonly used but any integer works.

---

# Understanding Output Variables

After splitting:

```python
X_train
```

Training features

---

```python
X_test
```

Testing features

---

```python
y_train
```

Training labels

---

```python
y_test
```

Testing labels

---

# Checking Shapes

Always verify dataset sizes.

```python
print(X_train.shape)

print(X_test.shape)

print(y_train.shape)

print(y_test.shape)
```

Example Output:

```text
(800, 4)

(200, 4)

(800,)

(200,)
```

Meaning:

```text
800 training rows

200 testing rows
```

---

# Feature Scaling

Features often have different ranges.

Example:

```text
Age = 25

Salary = 500000
```

Salary dominates because it is much larger.

This can negatively affect some ML algorithms.

Solution:

**Feature Scaling**

---

# StandardScaler

One of the most common scaling techniques.

Import:

```python
from sklearn.preprocessing import StandardScaler
```

Create scaler:

```python
scaler = StandardScaler()
```

---

# Scaling Training Data

```python
X_train = scaler.fit_transform(
    X_train
)
```

What happens?

1. Calculate mean
2. Calculate standard deviation
3. Transform data

---

# Scaling Testing Data

```python
X_test = scaler.transform(
    X_test
)
```

Notice:

```python
transform()
```

NOT

```python
fit_transform()
```

---

# Why Not fit_transform() on Test Data?

Wrong:

```python
X_test = scaler.fit_transform(
    X_test
)
```

This learns information from test data.

The model indirectly sees test information.

This creates:

**Data Leakage**

---

# Data Leakage

Data leakage occurs when information from testing data is used during training.

Example:

```python
scaler.fit_transform(X)
```

Entire dataset is scaled before splitting.

This is incorrect.

---

# Correct Workflow

```python
Split Data

↓

Fit Scaler on Training Data

↓

Transform Training Data

↓

Transform Testing Data
```

Example:

```python
scaler = StandardScaler()

X_train = scaler.fit_transform(
    X_train
)

X_test = scaler.transform(
    X_test
)
```

---

# Common Split Ratios

| Train | Test |
| ----- | ---- |
| 80%   | 20%  |
| 75%   | 25%  |
| 70%   | 30%  |
| 90%   | 10%  |

Most projects use:

```text
80% Train

20% Test
```

---

# Complete Example

```python
import pandas as pd

from sklearn.model_selection import train_test_split

from sklearn.preprocessing import StandardScaler

df = pd.read_csv(
    "heart_disease.csv"
)

X = df[
    [
        "age",
        "bmi",
        "cholesterol_total",
        "heart_rate"
    ]
]

y = df["diagnosed_diabetes"]

X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)

scaler = StandardScaler()

X_train = scaler.fit_transform(
    X_train
)

X_test = scaler.transform(
    X_test
)

print(X_train.shape)
print(X_test.shape)
```

---

# Common Mistakes

## Mistake 1

Training and testing on same dataset.

Wrong:

```python
model.fit(X, y)

model.predict(X)
```

---

## Mistake 2

Forgetting random_state.

This causes different splits every run.

---

## Mistake 3

Scaling before splitting.

Wrong:

```python
scaler.fit_transform(X)
```

---

## Mistake 4

Using fit_transform() on test data.

Wrong:

```python
scaler.fit_transform(X_test)
```

---

# Key Takeaways

* Features are stored in X.
* Target is stored in y.
* Train-test split prevents overfitting.
* Training data teaches the model.
* Testing data evaluates performance.
* StandardScaler standardizes feature values.
* Fit scaler only on training data.
* Never allow data leakage.
* Proper data preparation is essential before model training.

