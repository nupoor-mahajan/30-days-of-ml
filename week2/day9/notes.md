# Day 9 Notes: Linear Regression Theory

# 🎯 What is Regression?

Regression is a **Supervised Learning** technique used to predict **continuous numerical values** by learning relationships between input variables (**features**) and an output variable (**target**).

Examples:

* House Price Prediction
* Temperature Forecasting
* Sales Prediction
* Stock Price Estimation
* Risk Analysis

### Characteristics

* Works with real-valued output variables.
* Identifies relationships between variables.
* Supports both simple and complex predictive models.
* Widely used in forecasting and trend estimation.

---

# Regression vs Classification

| Regression                         | Classification                |
| ---------------------------------- | ----------------------------- |
| Predicts continuous values         | Predicts categories/labels    |
| Output: Price, Temperature, Salary | Output: Spam/Not Spam, Yes/No |
| Example: House price prediction    | Example: Email spam detection |

### Examples

**Regression**

* House Price = ₹50,00,000
* Temperature = 32.5°C
* Sales = 1500 units

**Classification**

* Pass / Fail
* Disease / No Disease
* Fraud / Not Fraud

---

# Linear Regression

Linear Regression predicts output using a straight-line relationship between input and output.

### Prediction Formula

\hat{y}=\beta_1x+\beta_0

Where:

* **ŷ** = Predicted value
* **β₁** = Weight/Coefficient (Slope)
* **x** = Input feature
* **β₀** = Bias/Intercept

The model makes predictions by computing a weighted sum of input features plus a bias term.

---

# Understanding y = mx + b

The simplest linear regression equation is:

Where:

* **y** = Predicted output
* **m** = Slope
* **x** = Input feature
* **b** = Intercept

### Slope (m)

Slope tells how much **y changes when x increases by 1 unit**.

Example:

If

y = 2x + 5

Then:

* x = 1 → y = 7
* x = 2 → y = 9
* x = 3 → y = 11

For every increase of 1 in x, y increases by 2.

### Intercept (b)

Intercept is the value of y when x = 0.

Example:

y = 2x + 5

When x = 0:

y = 5

So intercept = 5.

---

# Best Fit Line

A **Best Fit Line** is a straight line drawn through data points that minimizes prediction errors.

It passes as close as possible to most data points.

Purpose:

* Capture the trend of the data.
* Enable future predictions.

---

# How Model Predictions Work

Suppose the model learns:

y = 3x + 2

Predict for x = 4

y = 3(4) + 2

y = 14

Predicted output = 14

---

# Actual vs Predicted Values

| Actual Value | Predicted Value |
| ------------ | --------------- |
| 15           | 14              |
| 20           | 19              |
| 25           | 27              |

The difference between actual and predicted values is called an **Error** or **Residual**.

### Residual

Residual = Actual − Predicted

Example:

Actual = 15

Predicted = 14

Residual = 1

Smaller residuals indicate better predictions.

---

# Types of Linear Regression

## 1. Simple Linear Regression

Uses only one independent variable.

### Example

Predict house price using only house size.

### Advantages

* Easy to understand.
* Highly interpretable.
* Fast to train.

### Disadvantages

* Cannot model complex patterns.
* Limited prediction power.

---

## 2. Multiple Linear Regression

Uses multiple independent variables.

### Example

Predict house price using:

* Size
* Location
* Age
* Number of rooms

### Advantages

* Captures influence of many factors.
* More realistic than simple regression.

### Disadvantages

* Suffers from multicollinearity.
* More difficult to interpret.

---

## 3. Polynomial Regression

Adds polynomial terms like:

x², x³, x⁴

to model curved relationships.

### Example

Population growth prediction.

### Advantages

* Captures non-linear relationships.
* More flexible than simple regression.

### Disadvantages

* High-degree polynomials can overfit.

---

## 4. Ridge Regression (L2 Regularization)

Adds a penalty for large coefficients.

### Advantages

* Reduces overfitting.
* Works well with many features.

### Disadvantages

* Harder to interpret coefficients.

---

## 5. Lasso Regression (L1 Regularization)

Adds a penalty that can reduce some coefficients to zero.

### Advantages

* Performs feature selection.
* Reduces overfitting.

### Disadvantages

* Can remove useful features if penalty is too strong.

---

## 6. Support Vector Regression (SVR)

Uses Support Vector Machine concepts for regression.

### Advantages

* Handles complex relationships.
* Effective in high-dimensional data.

### Disadvantages

* Computationally expensive.
* Requires parameter tuning.

---

## 7. Decision Tree Regression

Uses decision rules to split data.

### Advantages

* Easy to visualize.
* Captures non-linear patterns.

### Disadvantages

* Easily overfits.

---

## 8. Random Forest Regression

Combines many decision trees and averages predictions.

### Advantages

* High accuracy.
* Less overfitting than a single tree.

### Disadvantages

* Difficult to interpret.
* Requires more computation.

---

# Loss Functions

A Loss Function measures how wrong a model's predictions are.

The goal during training is:

**Minimize Loss**

Smaller loss = Better model.

---

# Regression Evaluation Metrics

## 1. Mean Absolute Error (MAE)

Average absolute difference between actual and predicted values.

Formula:

MAE = Σ|Actual − Predicted| / n

### Interpretation

* Lower MAE = Better model
* Easy to understand
* Less sensitive to outliers

---

## 2. Mean Squared Error (MSE)

Average of squared errors.

Formula:

MSE = Σ(Actual − Predicted)² / n

### Interpretation

* Lower MSE = Better model
* Penalizes large errors heavily
* Sensitive to outliers

---

## 3. Root Mean Squared Error (RMSE)

Square root of MSE.

Formula:

RMSE = √MSE

### Interpretation

* Lower RMSE = Better model
* Same unit as target variable
* Easier to interpret than MSE

---

## 4. Huber Loss

Combination of:

* MAE
* MSE

### Advantages

* Less sensitive to outliers than MSE.
* More stable than MAE.

---

# R² Score (Coefficient of Determination)

R² measures how much variation in the target variable is explained by the model.

### Range

* 1 → Perfect prediction
* 0 → No predictive power
* Negative → Worse than predicting the mean

### General Interpretation

| R² Score    | Interpretation |
| ----------- | -------------- |
| 0.90 - 1.00 | Excellent      |
| 0.70 - 0.89 | Good           |
| 0.50 - 0.69 | Moderate       |
| Below 0.50  | Poor           |

### Limitations

* High R² does not always mean a good model.
* Does not detect overfitting.
* Should be used with MAE/RMSE.

---

# Linear Regression Assumptions

## 1. Linear Relationship

Input and output should have a roughly linear relationship.

---

## 2. Independent Features

Features should not be highly correlated with each other.

---

## 3. Minimal Outliers

Too many outliers can distort the regression line.

---

## 4. Constant Variance (Homoscedasticity)

Variance is a statistical measure that tells us how far data points are spread from their mean (average).

### Understanding Variance

* **Low Variance** → Data points are close to the mean.
* **High Variance** → Data points are spread far from the mean.

### Example

Dataset A:

```text
48, 50, 52, 50, 50
```

Mean = 50

Values are very close to the mean, so variance is low.

Dataset B:

```text
10, 30, 50, 70, 90
```

Mean = 50

Values are widely spread around the mean, so variance is high.

### Formula

Variance = Σ(xᵢ − x̄)² / n

Where:

* xᵢ = each data point
* x̄ = mean of the dataset
* n = number of observations

### Why Square the Differences?

If we directly add differences from the mean, positive and negative values cancel each other out. Squaring:

* Makes all values positive
* Gives more importance to larger deviations

### Variance in Machine Learning

Variance is important in understanding model behavior.

#### High Variance Model

* Learns training data too closely
* Captures noise in the data
* Performs poorly on unseen data
* Leads to **Overfitting**

#### Low Variance Model

* More stable predictions
* Better generalization to new data

### Variance vs Standard Deviation

* Variance measures spread in squared units.
* Standard Deviation is the square root of variance and is easier to interpret because it uses the original units.

### Key Point

Higher variance means data or model predictions are more spread out, while lower variance means they are more concentrated around the average.


Errors should have roughly equal variance across all predictions.

---

# Underfitting vs Overfitting

## Underfitting

* Model is too simple.
* Fails to learn patterns.
* High training error.
* High testing error.

### Example

Using a straight line for highly curved data.

---

## Overfitting

* Model memorizes training data.
* Performs poorly on unseen data.
* Very low training error.
* High testing error.

### Example

Using a very high-degree polynomial.

---

# Quick Revision

✅ Regression predicts continuous values

✅ Classification predicts categories

✅ Linear Regression learns a best-fit line

✅ Slope controls rate of change

✅ Intercept is value when x = 0

✅ Residual = Actual − Predicted

✅ Lower MAE, MSE, RMSE are better

✅ Higher R² is generally better

✅ Watch for overfitting and outliers

✅ Linear relationship is a key assumption

---

# Practice Questions

### Q1

A model learns:

y = 4x + 3

Predict y when x = 5.

Answer:
y = 23

---

### Q2

Actual = 20

Predicted = 17

Find residual.

Answer:
20 − 17 = 3

---

### Q3

Is house price prediction Regression or Classification?

Answer:
Regression

---

### Q4

Which metric squares errors?

Answer:
MSE

---

### Q5

What does R² = 1 mean?

Answer:
Perfect prediction.
