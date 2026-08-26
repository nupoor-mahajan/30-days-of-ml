# Decision Trees

## 1. Introduction

A **Decision Tree** is a **supervised machine learning algorithm** used for both:

* **Classification** — predicting a categorical target.
* **Regression** — predicting a continuous numerical target.

A decision tree represents decisions in a **hierarchical tree-like structure**. It repeatedly divides the dataset into smaller subsets based on feature values until it reaches a prediction at a **leaf node**.

Decision trees are widely used because they are:

* Easy to understand and interpret
* Capable of handling both numerical and categorical features
* Able to model non-linear relationships
* Require relatively little preprocessing
* Useful for both classification and regression
* Capable of showing the reasoning behind a prediction

---

# 2. Basic Structure of a Decision Tree

A decision tree consists of several important components:

```text
                         Root Node
                       Age < 30?
                      /          \
                    Yes           No
                    /              \
              Income > 40K?       Leaf
                /      \         Buy = No
              Yes       No
               /         \
             Leaf       Leaf
          Buy = Yes   Buy = No
```

### 2.1 Root Node

The **root node** is the first and topmost node of the tree.

It represents the feature and condition used to make the **first split** in the dataset.

The algorithm chooses the split that produces the best separation according to a splitting criterion such as:

* Entropy / Information Gain
* Gini Impurity
* Variance Reduction for regression

---

### 2.2 Internal Node

An **internal node** represents a decision or condition based on a feature.

For example:

```text
Age < 30?
```

Each internal node further divides the dataset into smaller groups.

---

### 2.3 Branch

A **branch** represents the outcome of a decision.

For example:

```text
Age < 30?
   |
   ├── Yes
   └── No
```

---

### 2.4 Leaf Node

A **leaf node** is the final node of a decision tree.

It contains the final prediction.

For classification:

```text
Prediction = Yes
```

For regression:

```text
Prediction = 72.5
```

---

# 3. How Does a Decision Tree Work?

The basic process is:

```text
Dataset
   ↓
Find the best feature and split
   ↓
Split the dataset
   ↓
Evaluate the resulting groups
   ↓
Repeat recursively
   ↓
Stop according to stopping criteria
   ↓
Create leaf nodes
   ↓
Make predictions
```

### Step 1: Start with the complete dataset

The algorithm begins with all training observations at the root node.

### Step 2: Evaluate possible splits

The algorithm considers different features and possible split points.

For example:

```text
Age < 25
Age < 30
Age < 35
Income < 40,000
Income < 50,000
```

### Step 3: Calculate split quality

The algorithm calculates how good each split is using a criterion such as:

* Information Gain
* Gini Impurity
* Variance Reduction

### Step 4: Select the best split

The split that produces the greatest improvement in purity is selected.

### Step 5: Repeat recursively

The same process is applied to each resulting child node.

### Step 6: Stop growing the tree

The algorithm stops when a stopping condition is reached.

Examples:

* Maximum tree depth reached
* Minimum number of samples required for splitting reached
* Node is already pure
* No useful split remains

---

# 4. Why Do We Need Splitting?

Suppose we have a dataset for predicting whether a customer purchases a product.

```text
Customer      Purchased
A             Yes
B             No
C             Yes
D             No
E             Yes
F             No
```

The dataset is mixed:

```text
Yes = 3
No  = 3
```

The tree tries to find a feature that separates these classes.

For example:

```text
Income > ₹50,000?
```

might produce:

```text
Income > ₹50,000
       /       \
     Yes        No
   Mostly      Mostly
   Yes         No
```

A good split makes the resulting nodes more **pure**.

This concept of purity is measured using splitting criteria.

---

# 5. Splitting Criteria

Common splitting criteria include:

### For Classification

1. **Entropy**
2. **Information Gain**
3. **Gini Impurity**

### For Regression

1. **Mean Squared Error (MSE)**
2. **Variance Reduction**
3. **Mean Absolute Error (MAE)** in some implementations

---

# 6. Entropy

**Entropy** is a measure of **randomness, disorder, or uncertainty** in a dataset.

In a decision tree, entropy measures how mixed or impure the classes are within a node.

The basic idea is:

> Higher entropy → greater uncertainty → more mixed classes

> Lower entropy → lower uncertainty → purer node

---

## 6.1 Candy Bowl Analogy

Imagine three bowls containing different types of candy.

### Case 1: Zero Entropy

The bowl contains:

```text
100 Snickers
0 Skittles
```

If you pick a candy randomly, you know exactly what you will get.

Therefore:

```text
Entropy = 0
```

The node is completely pure.

---

### Case 2: Maximum Entropy

The bowl contains:

```text
50 Snickers
50 Skittles
```

There is maximum uncertainty.

You have an equal probability of selecting either candy.

For a binary classification problem:

```text
Entropy = 1
```

This is the maximum entropy.

---

### Case 3: Low Entropy

The bowl contains:

```text
90 Snickers
10 Skittles
```

You are highly likely to pick a Snickers, but there is still some uncertainty.

Therefore:

```text
0 < Entropy < 1
```

---

# 7. Entropy Formula

For a dataset containing `c` classes:

$$
H(S) = -\sum_{i=1}^{c}p_i\log_2(p_i)
$$

Where:

* $H(S)$ = entropy of dataset $S$
* $p_i$ = proportion of observations belonging to class $i$
* $c$ = number of classes
* $\log_2$ = logarithm with base 2

### Important rule

If:

$$
p_i = 0
$$

then:

$$
p_i\log_2(p_i) = 0
$$

---

# 8. Entropy Example

Suppose a dataset contains:

```text
10 observations

Class A = 5
Class B = 5
```

Therefore:

$$
p_A = \frac{5}{10}=0.5
$$

$$
p_B = \frac{5}{10}=0.5
$$

Entropy:

$$
H(S)=-(0.5\log_2 0.5 + 0.5\log_2 0.5)
$$

Since:

$$
\log_2(0.5)=-1
$$

we get:

$$
H(S)=-(0.5(-1)+0.5(-1))
$$

$$
H(S)=1
$$

Therefore:

```text
Entropy = 1
```

The node has maximum impurity for a binary classification problem.

---

# 9. Entropy of a Pure Node

Suppose:

```text
Class A = 10
Class B = 0
```

Then:

$$
p_A=1
$$

$$
p_B=0
$$

Therefore:

$$
H(S)=-(1\log_2 1 + 0\log_2 0)
$$

Since:

$$
\log_2(1)=0
$$

and the second term is treated as zero:

$$
H(S)=0
$$

Therefore:

```text
Entropy = 0
```

The node is completely pure.

---

# 10. How Decision Trees Use Entropy

A decision tree attempts to transform a mixed dataset into purer groups.

The process is:

```text
High Entropy
     ↓
Choose a feature
     ↓
Split dataset
     ↓
Calculate child entropies
     ↓
Measure reduction in entropy
     ↓
Choose the best split
```

The reduction in entropy is called **Information Gain**.

---

# 11. Information Gain

**Information Gain** measures how much uncertainty is reduced after splitting a dataset.

The goal is:

> Choose the split that produces the highest Information Gain.

Formula:

$$
IG(S,A)
=======

## H(S)

\sum_{v\in Values(A)}
\frac{|S_v|}{|S|}
H(S_v)
$$

Where:

* $IG(S,A)$ = Information Gain of feature $A$
* $H(S)$ = entropy before splitting
* $S_v$ = subset produced by value $v$
* $|S_v|$ = number of observations in subset $S_v$
* $|S|$ = total number of observations

---

# 12. Information Gain Intuition

Suppose:

```text
Before split:

Yes = 50
No  = 50

Entropy = 1
```

After splitting:

```text
Node 1:
Yes = 45
No  = 5

Node 2:
Yes = 5
No  = 45
```

Both resulting nodes are much purer.

Therefore, the split has a high Information Gain.

In general:

```text
High Information Gain
        ↓
Large reduction in uncertainty
        ↓
Better split
```

---

# 13. Worked Information Gain Example

Consider the following dataset:

| Student | Study Hours | Result |
| ------- | ----------: | ------ |
| A       |           1 | Fail   |
| B       |           2 | Fail   |
| C       |           3 | Pass   |
| D       |           4 | Pass   |
| E       |           5 | Pass   |
| F       |           6 | Pass   |

There are:

```text
Pass = 4
Fail = 2
```

Therefore:

$$
p_{Pass}=\frac{4}{6}
$$

$$
p_{Fail}=\frac{2}{6}
$$

The original entropy is:

$$
H(S)
====

-\left(
\frac{4}{6}\log_2\frac{4}{6}
+
\frac{2}{6}\log_2\frac{2}{6}
\right)
$$

Approximately:

$$
H(S)\approx0.918
$$

Now suppose we split at:

```text
Study Hours < 3
```

This produces:

### Left node

```text
Fail = 2
Pass = 0
```

Therefore:

$$
H(S_{left})=0
$$

### Right node

```text
Fail = 0
Pass = 4
```

Therefore:

$$
H(S_{right})=0
$$

Weighted entropy after splitting:

$$
0
$$

Therefore:

$$
IG=0.918-0
$$

$$
IG=0.918
$$

This is a perfect split because the resulting nodes are completely pure.

---

# 14. Gini Impurity

The **Gini Index**, also called **Gini Impurity**, measures the impurity of a node.

It represents the probability that a randomly selected observation would be incorrectly classified if it were assigned a class according to the class distribution of that node.

Formula:

$$
Gini(S)=1-\sum_{i=1}^{n}p_i^2
$$

Where:

* $p_i$ = proportion of observations belonging to class $i$
* $n$ = number of classes

---

# 15. Gini Index Example

Suppose a dataset contains 8 observations:

```text
Class A = 3
Class B = 5
```

Calculate the class probabilities:

$$
p_A=\frac{3}{8}=0.375
$$

$$
p_B=\frac{5}{8}=0.625
$$

Square the probabilities:

$$
p_A^2=(0.375)^2=0.140625
$$

$$
p_B^2=(0.625)^2=0.390625
$$

Now:

$$
Gini(S)=1-(0.140625+0.390625)
$$

$$
Gini(S)=1-0.53125
$$

$$
\boxed{Gini(S)=0.46875}
$$

---

# 16. Interpreting Gini Values

### Gini = 0

The node is completely pure.

Example:

```text
Class A = 100%
Class B = 0%
```

Therefore:

$$
Gini=0
$$

---

### Gini = 0.5

For binary classification, Gini reaches its maximum when the classes are equally distributed.

Example:

```text
Class A = 50%
Class B = 50%
```

Therefore:

$$
Gini=1-(0.5^2+0.5^2)
$$

$$
Gini=1-0.5
$$

$$
Gini=0.5
$$

---

### General Maximum Gini

For $n$ classes:

$$
Gini_{max}=1-\frac{1}{n}
$$

Therefore:

* 2 classes → maximum Gini = 0.5
* 3 classes → maximum Gini = 0.667
* 4 classes → maximum Gini = 0.75

---

# 17. Entropy vs Gini Impurity

| Feature                         | Gini Impurity     | Entropy                   |
| ------------------------------- | ----------------- | ------------------------- |
| Formula                         | $1-\sum p_i^2$    | $-\sum p_i\log_2(p_i)$    |
| Measures                        | Impurity          | Uncertainty               |
| Range for binary classification | 0 to 0.5          | 0 to 1                    |
| Best value                      | 0                 | 0                         |
| Worst value                     | 0.5               | 1                         |
| Logarithmic calculation         | No                | Yes                       |
| Computationally                 | Generally faster  | Generally slower          |
| Common algorithm                | CART              | ID3 / C4.5                |
| Main goal                       | Minimize impurity | Maximize Information Gain |

### Important

Both criteria generally produce similar trees.

The main difference is how they measure impurity and how the split is selected.

---

# 18. Gini vs Entropy — Which One Should You Use?

In practice, the difference in model performance is often small.

### Gini is useful when:

* You want faster computation.
* You are using CART-style trees.
* You want a commonly used default criterion.

### Entropy is useful when:

* You want an information-theoretic interpretation.
* You specifically want to work with Information Gain.
* You are studying algorithms such as ID3.

In `scikit-learn`, the classification `DecisionTreeClassifier` supports criteria including:

```python
criterion="gini"
```

and:

```python
criterion="entropy"
```

Modern versions also provide:

```python
criterion="log_loss"
```

---

# 19. Classification Trees

A **classification tree** predicts a categorical target.

Examples:

```text
Spam / Not Spam
Disease / No Disease
Buy / Don't Buy
Pass / Fail
```

The leaf node contains the predicted class.

Example:

```text
                 Income > 50K?
                    /      \
                  Yes       No
                  /          \
            Buy Product    Don't Buy
```

---

# 20. Regression Trees

A **regression tree** predicts a continuous numerical value.

Examples:

```text
House Price
Temperature
Sales
Salary
Demand
```

Example:

```text
                  Area > 1000 sq.ft?
                    /           \
                  Yes            No
                  /               \
          Price = ₹80L        Price = ₹45L
```

Instead of class purity, regression trees generally use a measure such as **Mean Squared Error (MSE)** or variance reduction to determine good splits.

---

# 21. Mean Squared Error in Regression Trees

For regression:

$$
MSE=\frac{1}{n}\sum_{i=1}^{n}(y_i-\hat{y})^2
$$

Where:

* $y_i$ = actual value
* $\hat{y}$ = predicted value
* $n$ = number of observations

The tree attempts to create groups where the target values are as similar as possible.

The prediction at a typical regression leaf is the **mean target value** of the observations reaching that leaf.

---

# 22. Continuous Features

Decision trees can handle numerical features by finding appropriate split points.

Suppose:

```text
Age:
18
22
25
31
40
45
```

Possible splits could include:

```text
Age < 20
Age < 23.5
Age < 28
Age < 35.5
Age < 42.5
```

The algorithm evaluates the possible splits and selects the one that gives the best improvement according to the chosen criterion.

---

# 23. Categorical Features

Decision trees can also work with categorical variables, depending on the implementation.

Example:

```text
City:
Mumbai
Pune
Delhi
Bangalore
```

A tree may use category-based conditions to divide observations.

However, in many machine learning libraries such as traditional `scikit-learn` workflows, categorical variables need to be converted into a numerical representation such as **one-hot encoding** before training.

---

# 24. Does a Decision Tree Need Feature Scaling?

Generally, **no**.

Decision trees are not distance-based algorithms.

For example, if a feature contains:

```text
Age = 20, 30, 40
```

and another contains:

```text
Income = 20,000, 50,000, 100,000
```

the difference in scale does not cause the same problems that it would in algorithms such as:

* K-Nearest Neighbors
* K-Means
* SVM
* Neural Networks

Therefore:

```text
Decision Tree → Feature scaling usually NOT required
```

---

# 25. Missing Values

Handling missing values depends on the implementation.

A common preprocessing approach is to:

* Impute missing numerical values using mean/median.
* Impute missing categorical values using mode.
* Use a model/implementation that explicitly supports missing values.

It is important to check the behavior of the specific library being used.

---

# 26. Recursive Partitioning

Decision trees are built using a process called **recursive partitioning**.

The basic idea is:

```text
Dataset
   ↓
Best split
   ↓
Dataset 1       Dataset 2
   ↓               ↓
Best split      Best split
   ↓               ↓
Subsets          Subsets
   ↓               ↓
Continue recursively
```

Each child node is treated as a new smaller dataset.

The process continues until a stopping condition is reached.

---

# 27. Stopping Criteria

A decision tree should not necessarily grow until every leaf contains a single observation.

Common stopping conditions include:

### 1. Maximum Depth

Controls the maximum number of levels.

```python
max_depth=5
```

A smaller value produces a simpler tree.

---

### 2. Minimum Samples Split

Minimum number of observations required to split a node.

```python
min_samples_split=10
```

A node containing fewer than 10 observations will not be split.

---

### 3. Minimum Samples Leaf

Minimum number of observations that must be present in a leaf.

```python
min_samples_leaf=5
```

---

### 4. Maximum Number of Leaf Nodes

Limits the total number of leaf nodes.

```python
max_leaf_nodes=20
```

---

# 28. Overfitting in Decision Trees

Decision trees are highly capable of learning complex patterns.

However, an unrestricted tree can become too complex.

For example:

```text
Training Data
      ↓
Very Deep Tree
      ↓
Learns noise + patterns
      ↓
Very high training accuracy
      ↓
Poor performance on unseen data
```

This is called **overfitting**.

A typical sign is:

```text
Training Accuracy = 99%
Validation Accuracy = 75%
```

The model has learned the training data too closely.

---

# 29. Underfitting

Underfitting occurs when the tree is too simple to capture important patterns.

Example:

```text
Training Accuracy = 65%
Validation Accuracy = 63%
```

Possible reasons include:

* Tree depth is too small.
* Too many restrictions are applied.
* Important features are missing.

---

# 30. Controlling Overfitting

Overfitting can be reduced using:

### Pre-pruning

Stop the tree from growing too much.

Common parameters:

```python
max_depth
min_samples_split
min_samples_leaf
max_leaf_nodes
```

---

### Post-pruning

First grow a larger tree and then remove branches that do not contribute sufficiently to generalization.

One common approach is **Cost Complexity Pruning**.

In `scikit-learn`, this can be controlled using:

```python
ccp_alpha
```

Higher pruning strength generally produces a simpler tree.

---

# 31. Cost Complexity Pruning

The idea is to balance:

```text
Model complexity
       +
Prediction error
```

A simplified objective is:

$$
R_\alpha(T)=R(T)+\alpha|T|
$$

Where:

* $T$ = tree
* $R(T)$ = prediction error
* $|T|$ = complexity of the tree, often represented by number of leaves
* $\alpha$ = complexity penalty

Higher $\alpha$ encourages simpler trees.

---

# 32. Advantages of Decision Trees

### 1. Easy to Interpret

The decision process can be visualized and explained.

### 2. Little Preprocessing

Feature scaling is generally unnecessary.

### 3. Handles Non-Linear Relationships

Decision trees can model complex decision boundaries.

### 4. Works for Classification and Regression

The same basic concept can be applied to both problems.

### 5. Feature Selection

The tree naturally selects features that are useful for making splits.

### 6. Human-Readable Rules

A trained tree can produce rules such as:

```text
IF income > 50K
AND age < 30
THEN purchase = Yes
```

---

# 33. Disadvantages of Decision Trees

### 1. Can Overfit Easily

Deep trees can memorize training data.

### 2. Unstable

Small changes in the training data can produce a significantly different tree.

### 3. Greedy Algorithm

Most decision tree algorithms choose the best split at the current node rather than searching for the globally optimal tree.

### 4. Can Create Complex Trees

Without restrictions or pruning, the tree can become very large.

### 5. Axis-Aligned Splits

Traditional decision trees typically make splits based on one feature at a time.

For example:

```text
Age < 30
```

rather than a complex combination such as:

```text
2 × Age + Income > threshold
```

---

# 34. Greedy Nature of Decision Trees

Decision tree construction is generally **greedy**.

At each node, the algorithm chooses the split that looks best **at that moment**.

It does not usually examine every possible complete tree and choose the globally optimal one.

Example:

```text
Root
 ↓
Choose best current split
 ↓
Child nodes
 ↓
Choose best split for each child
 ↓
Continue
```

This makes tree construction practical but does not guarantee the globally optimal tree.

---

# 35. Decision Tree Algorithm Families

Several important decision tree algorithms exist.

| Algorithm | Main Criterion / Idea                                 |
| --------- | ----------------------------------------------------- |
| ID3       | Information Gain / Entropy                            |
| C4.5      | Gain Ratio                                            |
| CART      | Gini for classification, squared error for regression |
| CHAID     | Chi-square based splitting                            |

---

# 36. ID3

**ID3 (Iterative Dichotomiser 3)** was one of the early decision tree algorithms.

It primarily uses:

```text
Entropy
      ↓
Information Gain
      ↓
Choose highest-gain feature
```

It was mainly designed for classification problems.

---

# 37. C4.5

C4.5 is an extension of ID3.

It introduced improvements such as:

* Handling continuous attributes
* Handling missing values
* Pruning
* Gain Ratio

### Gain Ratio

Information Gain can sometimes favor features with many distinct values.

Gain Ratio attempts to compensate for this.

$$
Gain\ Ratio=
\frac{Information\ Gain}{Split\ Information}
$$

---

# 38. CART

**CART** stands for:

> Classification and Regression Trees

CART can be used for both:

* Classification
* Regression

Typical criteria include:

```text
Classification → Gini Impurity
Regression     → Squared Error / MSE
```

CART generally creates **binary splits**.

Example:

```text
Age < 30?
   /   \
 Yes    No
```

---

# 39. Decision Tree Prediction

## Classification

For a classification tree, a leaf predicts a class.

For example:

```text
Leaf:

Class A = 80%
Class B = 20%
```

The predicted class is generally:

```text
Class A
```

The class probabilities can also be estimated from the distribution of training samples in the leaf.

---

## Regression

For regression, a leaf generally predicts the average target value of the observations reaching that leaf.

Example:

```text
Target values:

40
50
60
70
```

Prediction:

$$
\frac{40+50+60+70}{4}=55
$$

Therefore:

```text
Prediction = 55
```

---

# 40. Feature Importance

Decision trees can provide a measure of **feature importance**.

A feature is considered important when it contributes significantly to reducing impurity across the tree.

Example:

```text
Feature            Importance

Income               0.42
Age                  0.31
Education            0.18
Location             0.09
```

This tells us that `Income` contributed the most according to the model's feature-importance calculation.

### Important limitation

Tree-based impurity importance can be biased in some situations, particularly toward features with many possible split points or high cardinality.

Therefore, alternatives such as **permutation importance** or **SHAP** can sometimes provide more useful explanations.

---

# 41. Decision Tree vs Other Algorithms

| Property                 | Decision Tree        | Logistic Regression             | KNN      | Neural Network |
| ------------------------ | -------------------- | ------------------------------- | -------- | -------------- |
| Interpretability         | High                 | High                            | Medium   | Low            |
| Feature Scaling          | Usually not required | Often useful                    | Required | Often useful   |
| Non-linear relationships | Yes                  | Limited without transformations | Yes      | Yes            |
| Classification           | Yes                  | Yes                             | Yes      | Yes            |
| Regression               | Yes                  | Yes                             | Yes      | Yes            |
| Overfitting risk         | High                 | Lower                           | Medium   | High           |
| Easy visualization       | Yes                  | No tree structure               | No       | No             |

---

# 42. Decision Tree Example — Customer Purchase

Suppose we want to predict whether a customer will purchase a product.

Features:

```text
Age
Income
Previous Purchases
Website Visits
```

Target:

```text
Purchase = Yes / No
```

The tree might learn:

```text
                       Income > ₹50K?
                         /          \
                       Yes           No
                       /              \
              Previous Visits > 3?    No
                 /       \
               Yes        No
               /           \
             Yes            No
```

The prediction process is:

```text
New Customer
     ↓
Income > ₹50K?
     ↓
Previous Visits > 3?
     ↓
Purchase = Yes
```

This is one reason decision trees are highly interpretable.

---

# 43. Complete Decision Tree Workflow

A typical machine learning workflow is:

```text
1. Collect dataset
        ↓
2. Explore the data
        ↓
3. Clean the data
        ↓
4. Separate features and target
        ↓
5. Train-test split
        ↓
6. Handle missing/categorical values if required
        ↓
7. Train Decision Tree
        ↓
8. Tune hyperparameters
        ↓
9. Evaluate model
        ↓
10. Prune/control complexity
        ↓
11. Interpret results
        ↓
12. Deploy model
```

---

# 44. Python Implementation

Using `scikit-learn`:

```python
from sklearn.tree import DecisionTreeClassifier
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score, classification_report

# Features
X = df.drop("target", axis=1)

# Target
y = df["target"]

# Train-test split
X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)

# Create model
model = DecisionTreeClassifier(
    criterion="gini",
    max_depth=5,
    random_state=42
)

# Train
model.fit(X_train, y_train)

# Predict
y_pred = model.predict(X_test)

# Evaluate
print("Accuracy:", accuracy_score(y_test, y_pred))
print(classification_report(y_test, y_pred))
```

---

# 45. Using Entropy Instead of Gini

To use entropy:

```python
model = DecisionTreeClassifier(
    criterion="entropy",
    max_depth=5,
    random_state=42
)
```

The important difference is:

```python
criterion="gini"
```

versus:

```python
criterion="entropy"
```

---

# 46. Regression Tree in Python

```python
from sklearn.tree import DecisionTreeRegressor
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_squared_error

X = df.drop("target", axis=1)
y = df["target"]

X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)

model = DecisionTreeRegressor(
    max_depth=5,
    random_state=42
)

model.fit(X_train, y_train)

y_pred = model.predict(X_test)

mse = mean_squared_error(y_test, y_pred)

print("MSE:", mse)
```

---

# 47. Visualizing a Decision Tree

A trained tree can be visualized using:

```python
from sklearn.tree import plot_tree
import matplotlib.pyplot as plt

plt.figure(figsize=(20, 10))

plot_tree(
    model,
    feature_names=X.columns,
    filled=True
)

plt.show()
```

Visualization can show:

* Feature used for splitting
* Threshold
* Impurity
* Number of samples
* Class distribution
* Prediction

---

# 48. Important Hyperparameters

Some important decision tree hyperparameters are:

| Hyperparameter      | Purpose                                     |
| ------------------- | ------------------------------------------- |
| `criterion`         | Defines splitting criterion                 |
| `max_depth`         | Maximum depth of tree                       |
| `min_samples_split` | Minimum samples required to split           |
| `min_samples_leaf`  | Minimum samples in a leaf                   |
| `max_leaf_nodes`    | Maximum number of leaves                    |
| `max_features`      | Number of features considered for splitting |
| `ccp_alpha`         | Controls cost-complexity pruning            |
| `random_state`      | Controls reproducibility                    |

---

# 49. Hyperparameter Tuning

Instead of manually choosing hyperparameters, techniques such as:

* Grid Search
* Randomized Search
* Cross-validation

can be used.

Example:

```python
from sklearn.model_selection import GridSearchCV

params = {
    "max_depth": [3, 5, 7, 10],
    "min_samples_split": [2, 5, 10],
    "min_samples_leaf": [1, 2, 5]
}

grid = GridSearchCV(
    DecisionTreeClassifier(random_state=42),
    params,
    cv=5,
    scoring="accuracy"
)

grid.fit(X_train, y_train)

print(grid.best_params_)
```

---

# 50. Important Concepts to Remember

### Purity

How homogeneous the observations in a node are.

```text
Pure node → mostly one class
Impure node → mixture of classes
```

### Entropy

Measures uncertainty.

```text
Low entropy → low uncertainty
High entropy → high uncertainty
```

### Information Gain

Measures the reduction in entropy after a split.

```text
Higher Information Gain → better split
```

### Gini Impurity

Measures impurity based on class probabilities.

```text
Lower Gini → purer node
```

### Pruning

Removes unnecessary tree branches to reduce overfitting.

---

# 51. Quick Comparison of Purity Measures

```text
                 Node Purity
                     │
          ┌──────────┴──────────┐
          │                     │
       Entropy                Gini
          │                     │
       Uncertainty            Impurity
          │                     │
     Lower is better        Lower is better
          │                     │
        0 = Pure             0 = Pure
```

For binary classification:

```text
                 Maximum
                    │
        ┌───────────┴───────────┐
        │                       │
     Entropy                  Gini
        │                       │
        1                      0.5
        │                       │
     50/50                   50/50
```

---
# Types of Decision Tree-Based Models

A **Decision Tree** can be used as a single model, or multiple trees can be combined using **ensemble learning** to improve performance.

## 1. Bagging

**Bagging = Bootstrap Aggregating**

* Creates multiple training datasets using **random sampling with replacement**.
* Trains multiple decision trees **independently/in parallel**.
* Combines predictions using:

  * **Majority voting** → Classification
  * **Averaging** → Regression
* Main purpose: **Reduce variance and overfitting**.

```text
Dataset → Bootstrap Samples → Multiple Trees → Voting/Average → Prediction
```

---

## 2. Random Forest

**Random Forest = Bagging + Random Feature Selection**

* Builds many decision trees using different **bootstrap samples**.
* At each split, only a **random subset of features** is considered.
* Combines all tree predictions.
* Main purpose: **Reduce variance and improve generalization**.

```text
Random Data + Random Features → Many Trees → Voting/Average → Prediction
```

**Key point:** Random Forest is a specific **bagging-based ensemble of decision trees**.

---

## 3. Boosting

Boosting builds multiple trees **sequentially**, where each new tree focuses on correcting the errors of previous trees.

* Trees are dependent on previous trees.
* Usually uses **weak learners** (small trees).
* Main purpose: **Improve predictive performance and reduce bias**.

```text
Tree 1 → Errors → Tree 2 → Errors → Tree 3 → Final Prediction
```

### Examples

* AdaBoost
* Gradient Boosting
* XGBoost
* LightGBM
* CatBoost

---

## Bagging vs Random Forest vs Boosting

|           | Bagging         | Random Forest                        | Boosting                |
| --------- | --------------- | ------------------------------------ | ----------------------- |
| Training  | Parallel        | Parallel                             | Sequential              |
| Trees     | Independent     | Independent + randomized features    | Dependent               |
| Main idea | Reduce variance | Reduce variance + increase diversity | Correct previous errors |
| Example   | Bagged Trees    | Random Forest                        | XGBoost                 |

### Easy way to remember

**Bagging → Parallel**

**Random Forest → Bagging + Random Features**

**Boosting → Sequential Error Correction**
