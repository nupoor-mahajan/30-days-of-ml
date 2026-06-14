# Day 11: Multiple Linear Regression

## Introduction

Multiple Linear Regression (MLR) is an extension of Simple Linear Regression that uses **multiple independent variables (features)** to predict a dependent variable (target).

Instead of predicting an output using only one feature, MLR considers several factors simultaneously, often leading to more accurate predictions.

---

## Why Multiple Linear Regression?

In real-world problems, outcomes usually depend on multiple factors.

### Example

Predicting a house price may depend on:

* Area of the house
* Number of bedrooms
* Age of the house
* Distance from the city
* Number of bathrooms

Using only one feature may not capture the complete relationship.

---

## Mathematical Formula

Multiple Linear Regression is represented as:

[
y = b₀ + b₁x₁ + b₂x₂ + .... + bₙxₙ
]

Where:

* **y** = Predicted value
* **b₀** = Intercept
* **b₁, b₂, ... bₙ** = Coefficients
* **x₁, x₂, ... xₙ** = Input features

---

## Example

Suppose we want to predict house prices.

| Area | Bedrooms | Age | Price |
| ---- | -------- | --- | ----- |
| 1000 | 2        | 10  | 50    |
| 1500 | 3        | 5   | 70    |
| 1800 | 3        | 2   | 90    |
| 2500 | 4        | 1   | 120   |

Features:

```python
X = df[["Area", "Bedrooms", "Age"]]
```

Target:

```python
y = df["Price"]
```

---

## Difference Between Simple and Multiple Linear Regression

| Simple Linear Regression | Multiple Linear Regression |
| ------------------------ | -------------------------- |
| Uses one feature         | Uses multiple features     |
| Simpler model            | More realistic model       |
| Easier to visualize      | Harder to visualize        |
| Lower predictive power   | Usually better predictions |

---

## Steps in Multiple Linear Regression

### 1. Collect Data

Gather data containing input features and target values.

### 2. Split Features and Target

```python
X = df[["Area", "Bedrooms", "Age"]]
y = df["Price"]
```

### 3. Split Training and Testing Data

```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)
```

### 4. Train the Model

```python
from sklearn.linear_model import LinearRegression

model = LinearRegression()

model.fit(X_train, y_train)
```

### 5. Make Predictions

```python
y_pred = model.predict(X_test)
```

### 6. Evaluate the Model

```python
from sklearn.metrics import r2_score

r2 = r2_score(y_test, y_pred)

print(r2)
```

---

## Understanding Coefficients

After training, the model learns coefficients for each feature.

```python
print(model.coef_)
```

Example:

```python
[0.05, 10.2, -1.8]
```

Interpretation:

* Area increases price by 0.05 units per square foot.
* Each additional bedroom increases price by 10.2 units.
* Older houses decrease price by 1.8 units per year.

---

## Model Evaluation

### R² Score

Measures how well the model explains the variance in the target variable.

Range:

* 1 → Perfect prediction
* 0 → Poor prediction

```python
from sklearn.metrics import r2_score

r2_score(y_test, y_pred)
```

---

## Advantages

* Easy to understand and implement
* Works well for linear relationships
* Supports multiple features
* Fast training and prediction

---

## Limitations

* Assumes a linear relationship
* Sensitive to outliers
* Can suffer from multicollinearity
* Performance decreases when assumptions are violated

---

## Real-World Applications

* House price prediction
* Sales forecasting
* Stock trend analysis
* Medical cost estimation
* Business revenue prediction

---

## Key Takeaways

* Multiple Linear Regression uses multiple features to predict a target value.
* It extends Simple Linear Regression.
* Each feature contributes through a coefficient.
* Scikit-Learn provides an easy implementation using `LinearRegression`.
* Model performance can be evaluated using the R² Score.
* MLR is one of the most important foundational algorithms in Machine Learning.

---

## Summary

Multiple Linear Regression is a supervised learning algorithm used for predicting continuous values based on multiple input variables. It is widely used because of its simplicity, interpretability, and effectiveness for many real-world prediction problems.
