# Linear Regression Implementation using Scikit-Learn

## Step 1: Import Libraries

```python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error, mean_absolute_error, r2_score
```

---

## Step 2: Create Dataset

```python
data = {
    "Size": [1000, 1200, 1500, 1800, 2000],
    "Price": [200000, 250000, 300000, 350000, 400000]
}

df = pd.DataFrame(data)

print(df)
```

Output:

```text
   Size   Price
0  1000  200000
1  1200  250000
2  1500  300000
3  1800  350000
4  2000  400000
```

---

## Step 3: Separate Features and Target

Features (X) are input variables.

Target (y) is the output variable.

```python
X = df[["Size"]]
y = df["Price"]
```

---

## Step 4: Split Dataset

Training data is used to train the model.

Testing data is used to evaluate the model.

```python
X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)
```

---

## Step 5: Create Linear Regression Model

```python
model = LinearRegression()
```

---

## Step 6: Train the Model

```python
model.fit(X_train, y_train)
```

The model learns:

* Slope (coefficient)
* Intercept (bias)

---

## Step 7: View Learned Equation

```python
print("Slope:", model.coef_[0])
print("Intercept:", model.intercept_)
```

Example Output:

```text
Slope: 200
Intercept: 0
```

Equation:

Price = 200 × Size + 0

---

## Step 8: Make Predictions

```python
y_pred = model.predict(X_test)

print(y_pred)
```

Predict a new house:

```python
new_house = [[1600]]

predicted_price = model.predict(new_house)

print(predicted_price)
```

---

## Step 9: Evaluate the Model

### Mean Absolute Error (MAE)

```python
mae = mean_absolute_error(y_test, y_pred)
print("MAE:", mae)
```

### Mean Squared Error (MSE)

```python
mse = mean_squared_error(y_test, y_pred)
print("MSE:", mse)
```

### Root Mean Squared Error (RMSE)

```python
rmse = mean_squared_error(
    y_test,
    y_pred,
    squared=False
)

print("RMSE:", rmse)
```

### R² Score

```python
r2 = r2_score(y_test, y_pred)

print("R² Score:", r2)
```

---

## Step 10: Visualize Regression Line

```python
import matplotlib.pyplot as plt

plt.scatter(X, y)

plt.plot(
    X,
    model.predict(X)
)

plt.xlabel("House Size")
plt.ylabel("House Price")
plt.title("Linear Regression")

plt.show()
```

### Graph Interpretation

* Dots = Actual data points
* Line = Best Fit Line
* Smaller distance between points and line = Better predictions

---

# Complete Workflow

1. Import libraries
2. Load/Create dataset
3. Separate features and target
4. Split dataset
5. Create model
6. Train model using `fit()`
7. Predict using `predict()`
8. Evaluate using MAE, MSE, RMSE, and R²
9. Visualize results

---

# Important Scikit-Learn Functions

| Function                | Purpose             |
| ----------------------- | ------------------- |
| `LinearRegression()`    | Creates model       |
| `fit()`                 | Trains model        |
| `predict()`             | Makes predictions   |
| `train_test_split()`    | Splits data         |
| `mean_absolute_error()` | Calculates MAE      |
| `mean_squared_error()`  | Calculates MSE/RMSE |
| `r2_score()`            | Calculates R² Score |

---

# Interview Questions

### What does `fit()` do?

It trains the model by learning the relationship between features and target values.

### What does `predict()` do?

It generates output values using the learned equation.

### Why use `train_test_split()`?

To evaluate how well the model performs on unseen data.

### What is the output of Linear Regression?

A continuous numerical value.

### Which metrics are commonly used?

* MAE
* MSE
* RMSE
* R² Score
