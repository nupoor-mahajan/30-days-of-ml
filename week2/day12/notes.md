# Day 12: Logistic Regression Theory

## Introduction

Logistic Regression is a **supervised machine learning algorithm** used for **classification problems**.
Unlike Linear Regression, which predicts continuous values, Logistic Regression predicts the **probability of a data point belonging to a class**.

It is mainly used for **binary classification**, where the output has only two possible classes such as:

* 0 or 1
* Yes or No
* Spam or Not Spam
* Pass or Fail

Although the name contains the word *Regression*, Logistic Regression is actually used for **classification tasks**.

---

## Understanding Classification Problems

Classification is a type of supervised learning where the goal is to predict a **category or label** instead of a continuous value.

### Examples of Classification

* Spam vs Not Spam
* Disease vs No Disease
* Pass vs Fail
* Fraud vs Legitimate Transaction

In classification, the model decides **which class the input belongs to**.

---

## Classification vs Regression

| Regression                           | Classification                     |
| ------------------------------------ | ---------------------------------- |
| Predicts continuous numerical values | Predicts categories / class labels |
| Output can be any real number        | Output belongs to a class          |
| Example: House price prediction      | Example: Spam email detection      |
| Algorithms: Linear Regression        | Algorithms: Logistic Regression    |

### Example

* Predicting **house price** → Regression
* Predicting **whether a student passes or fails** → Classification

---

## Why Linear Regression Fails for Classification

Linear Regression predicts outputs using a straight-line equation and can produce values like:

* -2.5
* 0.7
* 1.8
* 5.3

This becomes a problem in classification because we need outputs that can represent **probabilities**, and probabilities must always lie between **0 and 1**.

### Problems with Linear Regression for Classification

* It can predict values less than 0
* It can predict values greater than 1
* It does not naturally represent probability
* It is designed for continuous target values, not class labels

### Example

If we want to predict whether a student passes or fails:

* 0 = Fail
* 1 = Pass

Linear Regression may predict:

* -0.4
* 0.3
* 1.6

These values do not make sense as probabilities.

---

## Why Logistic Regression is Needed

For classification, we want outputs such as:

* 0.10 → very low chance of belonging to Class 1
* 0.85 → high chance of belonging to Class 1

So instead of predicting unrestricted numerical values, we need a model that predicts **probabilities between 0 and 1**.

Logistic Regression solves this problem by using the **Sigmoid Function**.

---

## What is Logistic Regression?

Logistic Regression is used to predict the **probability** that a data point belongs to a particular class.

For binary classification:

* **Class 0** → Negative class
* **Class 1** → Positive class

The model predicts:

$P(y = 1)$

which means the probability that the output belongs to **Class 1**.

---

## Binary Classification

Binary classification means there are only **two possible output classes**.

### Examples

* Pass / Fail
* Spam / Not Spam
* Disease / No Disease
* Fraud / Legit

Logistic Regression is most commonly used for such binary classification tasks.

---

## Sigmoid Function

The Sigmoid Function is the core of Logistic Regression.
It converts any real value into a number between **0 and 1**.

### Formula

$$
f(x) = \frac{1}{1 + e^{-x}}
$$

It is also written as:

$$
\sigma(z) = \frac{1}{1 + e^{-z}}
$$

where **z** is the linear output of the model.

---

## Why Sigmoid Function is Used

The sigmoid function is used because:

* It converts large negative values close to **0**
* It converts large positive values close to **1**
* It gives an output that can be interpreted as a **probability**

### Example Values

| Input (z) | Sigmoid Output |
| --------- | -------------- |
| -5        | 0.0067         |
| -2        | 0.119          |
| 0         | 0.5            |
| 2         | 0.881          |
| 5         | 0.993          |

So sigmoid transforms the model’s raw output into a probability.

---

## Logistic Regression Formula

Logistic Regression first calculates a linear combination of the input features:

$$
z = b_0 + b_1x_1 + b_2x_2 + \dots + b_nx_n
$$

Then this value is passed through the sigmoid function:

$$
p = \frac{1}{1 + e^{-z}}
$$

So the full Logistic Regression equation becomes:

$$
p = \frac{1}{1 + e^{-(b_0 + b_1x_1 + b_2x_2 + \dots + b_nx_n)}}
$$

Where:

* **p** = Predicted probability
* **b₀** = Intercept
* **b₁, b₂, ... bₙ** = Coefficients
* **x₁, x₂, ... xₙ** = Input features

---

## Probability Predictions

Logistic Regression predicts a probability between **0 and 1**.

### Example

Suppose the model predicts the following probabilities:

* 0.10
* 0.35
* 0.75
* 0.95

These values represent the probability of belonging to **Class 1**.

---

## Decision Boundary

A **Decision Boundary** is the threshold used to convert probability into a final class label.

The default threshold is usually:

$0.5$

### Rule

* If probability **≥ 0.5** → predict **Class 1**
* If probability **< 0.5** → predict **Class 0**

### Example

| Predicted Probability | Predicted Class |
| --------------------- | --------------- |
| 0.10                  | 0               |
| 0.35                  | 0               |
| 0.75                  | 1               |
| 0.95                  | 1               |

---

## Logistic Regression Workflow

### 1. Input Features

Take the independent variables from the dataset.

Example:

```python
X = df[["Hours_Studied", "Attendance", "Internal_Marks"]]
```

### 2. Compute Linear Combination

The model calculates:

[
z = b_0 + b_1x_1 + b_2x_2 + \dots + b_nx_n
]

### 3. Apply Sigmoid Function

Convert the linear output into probability:

$$
p = \frac{1}{1 + e^{-z}}
$$

### 4. Get Probability Output

The output is a probability value between **0 and 1**.

### 5. Convert Probability into Class Label

Use a threshold (usually 0.5) to decide whether the prediction belongs to Class 0 or Class 1.

---

## Example

Suppose we want to predict whether a student will pass or fail.

| Hours Studied | Attendance | Result |
| ------------- | ---------- | ------ |
| 2             | 60         | 0      |
| 4             | 75         | 0      |
| 6             | 85         | 1      |
| 8             | 92         | 1      |

Features:

```python
X = df[["Hours_Studied", "Attendance"]]
```

Target:

```python
y = df["Result"]
```

If the model predicts:

[
p = 0.82
]

then:

* Probability of Class 1 = 82%
* Since 0.82 > 0.5, final predicted class = **1**

---

## Evaluation Metrics for Classification

To evaluate a classification model, we use metrics such as:

* Accuracy
* Precision
* Recall
* F1 Score

These metrics are based on the predictions made by the model.

---

## Accuracy

Accuracy measures how many predictions were correct out of the total predictions.

### Formula

$$
\text{Accuracy} = \frac{\text{Correct Predictions}}{\text{Total Predictions}}
$$

### Example

If the model makes 10 predictions and 8 are correct:

$$
\text{Accuracy} = \frac{8}{10} = 0.8 = 80%
$$

---

## Confusion Matrix

A Confusion Matrix is used to compare **actual values** and **predicted values** in a classification problem.

For binary classification, it contains four important terms:

* True Positive (TP)
* True Negative (TN)
* False Positive (FP)
* False Negative (FN)

### Confusion Matrix Structure

| Actual \ Predicted | Positive (1) | Negative (0) |
| ------------------ | ------------ | ------------ |
| Positive (1)       | TP           | FN           |
| Negative (0)       | FP           | TN           |

---

## Understanding TP, TN, FP, FN

### True Positive (TP)

Model predicted **Positive**, and the actual class was also **Positive**.

Example:

* Model predicts “Disease”
* Patient actually has the disease

### True Negative (TN)

Model predicted **Negative**, and the actual class was also **Negative**.

Example:

* Model predicts “No Disease”
* Patient actually does not have the disease

### False Positive (FP)

Model predicted **Positive**, but the actual class was **Negative**.

Example:

* Model predicts “Fraud”
* Transaction was actually legitimate

### False Negative (FN)

Model predicted **Negative**, but the actual class was **Positive**.

Example:

* Model predicts “No Disease”
* Patient actually has the disease

---

## Precision

Precision tells us:

**Out of all the samples predicted as positive, how many were actually positive?**

### Formula

$$
\text{Precision} = \frac{TP}{TP + FP}
$$

Precision becomes important when **false positives** are costly.

---

## Recall

Recall tells us:

**Out of all actual positive samples, how many were correctly identified by the model?**

### Formula

$$
\text{Recall} = \frac{TP}{TP + FN}
$$

Recall becomes important when **missing positive cases** is costly.

---

## F1 Score

F1 Score is the harmonic mean of Precision and Recall.

### Formula

$$
F1 = 2 \cdot \frac{\text{Precision} \cdot \text{Recall}}{\text{Precision} + \text{Recall}}
$$

It is useful when both Precision and Recall are important.

---

## Small Confusion Matrix Example

Suppose:

Actual values:

[
[1, 0, 1, 1, 0, 0, 1, 0]
]

Predicted values:

[
[1, 0, 1, 0, 0, 1, 1, 0]
]

Now the counts are:

* **TP = 3**
* **TN = 3**
* **FP = 1**
* **FN = 1**

This gives a clear picture of model performance.

---

## Visual Understanding

### Sigmoid Curve

The sigmoid curve is an **S-shaped curve**:

* Very negative input → output near 0
* Input = 0 → output = 0.5
* Very positive input → output near 1

### Decision Boundary

For binary classification, the probability line can be viewed as:

```text
0 ------------------ 0.5 ------------------ 1
      Class 0            Boundary            Class 1
```

---

## Advantages

* Works well for binary classification problems
* Predicts probabilities between 0 and 1
* Easy to understand and implement
* Computationally efficient
* Widely used as a baseline classification model

---

## Limitations

* Mainly suitable for linear decision boundaries
* Performance decreases if the relationship is highly non-linear
* Sensitive to outliers in some cases
* Not ideal for very complex classification tasks without feature engineering

---

## Real-World Applications

* Spam email detection
* Disease prediction
* Fraud detection
* Customer churn prediction
* Loan approval prediction
* Student pass/fail prediction

---

## Key Takeaways

* Logistic Regression is a supervised learning algorithm used for **classification**.
* It is mainly used for **binary classification problems**.
* Unlike Linear Regression, it predicts **probabilities** instead of continuous values.
* The **Sigmoid Function** converts the linear output into a value between 0 and 1.
* A **decision boundary** is used to convert probability into a class label.
* Classification models are evaluated using **Accuracy, Precision, Recall, F1 Score, and Confusion Matrix**.
* Logistic Regression is one of the most important foundational classification algorithms in Machine Learning.

---

## Summary

Logistic Regression is a supervised machine learning algorithm used for classification tasks, especially binary classification. It predicts the probability that a data point belongs to a particular class and then converts that probability into a final class label using a threshold. Because of its simplicity, interpretability, and effectiveness, Logistic Regression is one of the most widely used classification algorithms in machine learning.
