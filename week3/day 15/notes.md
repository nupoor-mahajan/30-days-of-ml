# Day 15 — K-Nearest Neighbors (KNN)

## 1. What is KNN?

**K-Nearest Neighbors (KNN)** is a **supervised machine learning algorithm** used for:

- **Classification** — predicts a class/category.
- **Regression** — predicts a numerical value.

KNN makes predictions based on the **nearest data points** in the training dataset.

### Why is KNN called a Lazy Learner?

KNN is called a **lazy learning algorithm** because it does not build an explicit model during the training phase.

Instead, it:

1. Stores the training data.
2. Waits until a prediction is required.
3. Calculates distances between the new point and training points.
4. Finds the nearest neighbors.
5. Uses those neighbors to make the prediction.

> **Key idea:** KNN does most of its computation at prediction time rather than during training.

---

## 2. What does 'K' mean?

**K** is the number of nearest neighbors considered when making a prediction.

For example:

- `K = 1` → consider the closest 1 point.
- `K = 3` → consider the closest 3 points.
- `K = 5` → consider the closest 5 points.

For classification, the predicted class is generally determined by **majority voting** among the K neighbors.

For regression, the prediction is generally the **average** of the target values of the K neighbors.

---

## 3. How KNN Works

The basic KNN algorithm can be understood in four steps.

### Step 1: Select the value of K

Choose how many nearest neighbors should be considered.

### Step 2: Calculate distance

Calculate the distance between the new/test point and every training point.

### Step 3: Find the K nearest neighbors

Sort the points according to their distance and select the **K points with the smallest distances**.

### Step 4: Make the prediction

**Classification:**
- Count the class labels of the K neighbors.
- Choose the class with the majority vote.

**Regression:**
- Take the average of the target values of the K neighbors.

### Example

Suppose `K = 5` and the five nearest neighbors contain:

- 3 points from Class 1
- 2 points from Class 2

The new point is classified as **Class 1** because Class 1 has the majority vote.

---

## 4. Choosing the Value of K

The value of K has a major effect on KNN performance.

### Small K

Example: `K = 1`

- Very sensitive to noise and outliers.
- Can create complex decision boundaries.
- May **overfit** the training data.

### Large K

- Predictions become more stable.
- Individual noisy points have less influence.
- But if K becomes too large, the model may become too simple.
- This can lead to **underfitting**.

### Bias-Variance Intuition

| K | Typical behavior |
|---|---|
| Very small K | Low bias, high variance |
| Moderate K | Often a good balance |
| Very large K | High bias, low variance |

The best K depends on the dataset and should generally be selected using validation or cross-validation.

---

## 5. Methods for Selecting K

### 5.1 Cross-Validation

**Cross-validation** is a reliable way to compare different K values.

For example, in **5-fold cross-validation**:

1. Divide the training data into 5 parts.
2. Train using 4 parts.
3. Validate on the remaining part.
4. Repeat until every part has been used as the validation set.
5. Calculate the average validation performance.
6. Repeat for different K values.
7. Select the K that gives the best validation performance.

> **Important:** The `K` in KNN and the `K` in K-fold cross-validation are two different concepts.

### 5.2 Validation/Error vs K Plot

You can evaluate KNN for several K values and plot validation error (or another evaluation metric) against K.

Choose a K that gives strong validation performance rather than simply choosing a value based on the shape of the curve.

### 5.3 Odd Values of K

For binary classification, an odd K can reduce the chance of a voting tie.

For example:

- `K = 3` → usually avoids a 1-vs-1 tie.
- `K = 5` → usually avoids a 2-vs-2 tie.

However, **odd K is not a strict requirement**. Cross-validation should ultimately guide the choice.

---

## 6. Distance Metrics in KNN

KNN depends heavily on the distance metric used to determine which points are "nearest."

### 6.1 Euclidean Distance

Euclidean distance is the straight-line distance between two points.

$$
d(x,X_i) =
\sqrt{
\sum_{j=1}^{n}
(x_j-X_{ij})^2
}
$$

For two dimensions:

$$
d =
\sqrt{(x_1-y_1)^2+(x_2-y_2)^2}
$$

It is commonly used when features are continuous and the geometry of the feature space makes Euclidean distance meaningful.

---

### 6.2 Manhattan Distance

Manhattan distance measures the total absolute difference between coordinates.

$$
d(x,y)=
\sum_{i=1}^{n}|x_i-y_i|
$$

It is also called **taxicab distance** because it resembles movement along a city grid.

---

### 6.3 Minkowski Distance

Minkowski distance is a generalized distance metric:

$$
d(x,y)=
\left(
\sum_{i=1}^{n}|x_i-y_i|^p
\right)^{1/p}
$$

Special cases:

- `p = 1` → **Manhattan distance**
- `p = 2` → **Euclidean distance**

Therefore, Minkowski distance can be viewed as a general family that includes both Euclidean and Manhattan distance.

---

## 7. Why Feature Scaling Matters in KNN

KNN is a **distance-based algorithm**, so feature scales can strongly affect the result.

Suppose we have:

- Age: `18–60`
- Salary: `20,000–2,00,000`

Salary has much larger numerical values and can dominate the distance calculation.

Therefore, numerical features are often scaled before applying KNN.

Common techniques:

### Standardization

Transforms features so they have approximately:

- Mean = 0
- Standard deviation = 1

```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)
```

### Min-Max Scaling

Transforms values to a specified range, commonly `[0, 1]`.

```python
from sklearn.preprocessing import MinMaxScaler

scaler = MinMaxScaler()
X_scaled = scaler.fit_transform(X)
```

> **Rule of thumb:** Always consider feature scaling before using KNN, especially when features have different units or ranges.

---

## 8. KNN Classification vs Regression

### Classification

KNN predicts a **category** using majority voting.

Example:

```text
Neighbor 1 → Class A
Neighbor 2 → Class A
Neighbor 3 → Class B
Neighbor 4 → Class A
Neighbor 5 → Class B

Prediction → Class A
```

### Regression

KNN predicts a **continuous numerical value** using the neighbors' target values.

Example:

```text
Neighbor values → 20, 24, 25, 27, 29

Prediction → average of the values
```

---

## 9. Advantages of KNN

- Simple and easy to understand.
- Easy to implement.
- No complex training procedure.
- Can be used for both classification and regression.
- Can model non-linear decision boundaries.
- Useful as a baseline model.

---

## 10. Disadvantages of KNN

- Prediction can be computationally expensive for large datasets.
- Requires storing the training dataset.
- Sensitive to feature scaling.
- Sensitive to irrelevant features.
- Sensitive to noise and outliers, especially with small K.
- Performance can degrade in high-dimensional spaces due to the **curse of dimensionality**.
- Choosing the right K and distance metric is important.

---

## 11. KNN Decision-Making — Visual Intuition

The provided diagram shows a target point surrounded by observations from two classes.

The process is:

1. Start with the target/test point.
2. Measure its distance from training points.
3. Identify the nearest K points.
4. Consider their class labels.
5. Use majority voting to assign the target point to a class.

For example, with `K = 5`, if the five nearest points contain more Class 1 observations than Class 2 observations, the target point is classified as **Class 1**.

---

## 12. KNN in Scikit-learn

### Classification

```python
from sklearn.neighbors import KNeighborsClassifier

model = KNeighborsClassifier(n_neighbors=5)
model.fit(X_train, y_train)

y_pred = model.predict(X_test)
```

### Regression

```python
from sklearn.neighbors import KNeighborsRegressor

model = KNeighborsRegressor(n_neighbors=5)
model.fit(X_train, y_train)

y_pred = model.predict(X_test)
```

---

## 13. KNN with Scaling

A typical KNN pipeline looks like this:

```python
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler
from sklearn.neighbors import KNeighborsClassifier

model = Pipeline([
    ("scaler", StandardScaler()),
    ("knn", KNeighborsClassifier(n_neighbors=5))
])

model.fit(X_train, y_train)
y_pred = model.predict(X_test)
```

Using a pipeline is useful because the scaler is fitted only on the training data and then applied to the validation/test data without data leakage.

---

## 14. Important Terms to Remember

| Term | Meaning |
|---|---|
| **K** | Number of neighbors considered |
| **Neighbor** | A nearby training observation |
| **Distance metric** | Method used to measure closeness |
| **Majority voting** | Most common class among neighbors |
| **Lazy learner** | Performs most computation at prediction time |
| **Feature scaling** | Putting features on comparable scales |
| **Overfitting** | Model is too sensitive to training data |
| **Underfitting** | Model is too simple to capture patterns |
| **Cross-validation** | Method for estimating validation performance |
| **Curse of dimensionality** | Distance-based methods become less effective as dimensionality increases |

---

## 15. KNN — Quick Revision

> **KNN = Find the nearest K points → use them to make the prediction.**

### Classification

**Nearest neighbors → Majority vote → Class**

### Regression

**Nearest neighbors → Average target values → Numerical prediction**

### Most important points

- KNN is a **supervised, distance-based, lazy learning algorithm**.
- K controls how many neighbors influence a prediction.
- Small K can overfit; very large K can underfit.
- Select K using validation/cross-validation.
- Feature scaling is important.
- Common distance metrics: **Euclidean, Manhattan, Minkowski**.
- Classification uses **majority voting**.
- Regression commonly uses the **average** of neighboring target values.
