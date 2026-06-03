# 30 Days of Machine Learning 🚀

## Day 01: Machine Learning Landscape

### Topics Covered
- AI vs ML vs DL
- Types of Machine Learning
- Supervised Learning
- Unsupervised Learning
- Semi-Supervised Learning
- Reinforcement Learning
- Batch vs Online Learning
- Instance-Based vs Model-Based Learning

### Resources
- Hands-On Machine Learning with Scikit-Learn, Keras & TensorFlow
- Official Scikit-Learn Documentation

# Day 01 - Machine Learning Landscape

## AI → ML → DL

```text
Artificial Intelligence (AI)
        ↓
Machine Learning (ML)
        ↓
Deep Learning (DL)
```

### Artificial Intelligence (AI)

Artificial Intelligence is the broad field of computer science focused on building systems capable of performing tasks that normally require human intelligence, such as reasoning, problem-solving, decision-making, and understanding language.

### Machine Learning (ML)

Machine Learning is a subset of AI where computers learn patterns from data and improve their performance without being explicitly programmed for every task.

### Deep Learning (DL)

Deep Learning is a specialized subset of Machine Learning that uses multi-layered Artificial Neural Networks inspired by the human brain to solve complex problems such as image recognition, speech processing, and natural language understanding.

---

# Why Machine Learning?

Machine Learning is useful when:

* Traditional rule-based systems become too complex.
* There is no clear algorithmic solution.
* Data changes frequently and systems need to adapt.
* Hidden patterns need to be discovered from large datasets.

Examples:

* Spam detection
* Recommendation systems
* Stock price prediction
* Fraud detection

---

# Types of Machine Learning

```text
Machine Learning
│
├── Supervised Learning
├── Unsupervised Learning
├── Semi-Supervised Learning
└── Reinforcement Learning
```

## 1. Supervised Learning

Training data contains input features and corresponding labels.

### Common Tasks

#### Classification

Predicts categories.

Examples:

* Spam / Not Spam
* Disease Detection
* Pass / Fail

#### Regression

Predicts continuous numerical values.

Examples:

* House Price Prediction
* Sales Forecasting

### Popular Algorithms

* K-Nearest Neighbors (KNN)
* Linear Regression
* Logistic Regression
* Support Vector Machines (SVM)
* Decision Trees
* Random Forests
* Neural Networks

---

## 2. Unsupervised Learning

Training data contains no labels.

The algorithm discovers hidden structures and patterns on its own.

### Clustering

Groups similar data points together.

Algorithms:

* K-Means
* DBSCAN
* Hierarchical Cluster Analysis (HCA)

Example:

* Customer Segmentation

### Anomaly Detection

Identifies unusual or suspicious observations.

Algorithms:

* Isolation Forest
* One-Class SVM

Example:

* Credit Card Fraud Detection

### Dimensionality Reduction

Reduces the number of features while preserving important information.

Algorithms:

* PCA
* Kernel PCA
* LLE
* t-SNE

Benefits:

* Faster Training
* Better Visualization

### Association Rule Learning

Finds relationships between items.

Algorithms:

* Apriori
* Eclat

Example:

```text
Customers who buy Bread
often buy Butter
```

---

## 3. Semi-Supervised Learning

Uses:

* Small amount of labeled data
* Large amount of unlabeled data

Combines ideas from supervised and unsupervised learning.

Example:

* Image Classification with limited labeled images.

---

## 4. Reinforcement Learning

An agent learns by interacting with an environment.

```text
Agent → Action
Environment → Reward / Penalty
```

### Important Terms

* Agent: Learner
* Environment: Surroundings where actions occur
* Reward: Positive feedback
* Penalty: Negative feedback
* Policy: Strategy followed by the agent

Example:

* Self-driving Cars
* Game Playing AI

---

# Batch Learning vs Online Learning

| Feature                   | Batch Learning | Online Learning |
| ------------------------- | -------------- | --------------- |
| Training                  | Entire Dataset | Incremental     |
| Learning After Deployment | No             | Yes             |
| Adaptation Speed          | Slow           | Fast            |
| Resource Requirement      | High           | Lower           |
| Best For                  | Stable Data    | Streaming Data  |

### Batch Learning

* Trained using the complete dataset.
* Also called Offline Learning.
* Requires retraining from scratch when new data arrives.

### Online Learning

* Learns continuously from incoming data.
* Suitable for real-time applications.
* Can process data in small batches called mini-batches.

---

# Out-of-Core Learning

Used when datasets are too large to fit into memory.

Process:

```text
Load Data Chunk
      ↓
Train
      ↓
Load Next Chunk
      ↓
Train
```

Often implemented using online learning techniques.

---

# Instance-Based Learning

The model memorizes training examples and compares new instances to previously seen data.

Example:

* K-Nearest Neighbors (KNN)

Workflow:

```text
Store Examples
      ↓
Find Similar Examples
      ↓
Make Prediction
```

---

# Model-Based Learning

Instead of memorizing data, the model learns a mathematical representation of the data.

Examples:

* Linear Regression
* Logistic Regression
* Neural Networks

Workflow:

```text
Training Data
      ↓
Build Model
      ↓
Make Predictions
```

---

# Quick Revision

| Learning Type   | Uses Labels? | Example                    |
| --------------- | ------------ | -------------------------- |
| Supervised      | Yes          | Classification, Regression |
| Unsupervised    | No           | Clustering                 |
| Semi-Supervised | Partial      | Image Tagging              |
| Reinforcement   | Rewards      | Self-Driving Cars          |

| Learning Approach | Description                  |
| ----------------- | ---------------------------- |
| Batch Learning    | Train once using full data   |
| Online Learning   | Learn continuously           |
| Instance-Based    | Compare with stored examples |
| Model-Based       | Build predictive model       |

---

## Key Takeaways

* AI is the broad field, ML is a subset of AI, and DL is a subset of ML.
* Supervised Learning uses labeled data.
* Unsupervised Learning finds patterns in unlabeled data.
* Semi-Supervised Learning combines labeled and unlabeled data.
* Reinforcement Learning learns through rewards and penalties.
* Batch Learning trains on complete datasets, while Online Learning updates incrementally.
* Instance-Based Learning memorizes examples, whereas Model-Based Learning builds predictive models.

