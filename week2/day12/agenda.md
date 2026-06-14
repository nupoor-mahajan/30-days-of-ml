# Day 12: Logistic Regression Theory

## 🎯 Goal

Understand how Logistic Regression works and why it is used for classification problems.

---

## 📚 Study Plan

### 1. Understand Classification Problems

* What is Classification?
* Classification vs Regression
* Real-world classification examples

Examples:

* Spam vs Not Spam
* Disease vs No Disease
* Pass vs Fail
* Fraud vs Legitimate Transaction

---

### 2. Why Linear Regression Fails for Classification

* Review Linear Regression outputs
* Problem of predictions outside 0–1 range
* Need for probability-based predictions

Understand why classification requires a different approach.

---

### 3. Learn Logistic Regression Basics

* What is Logistic Regression?
* Supervised Learning Algorithm
* Binary Classification

Key idea:

* Predicts probability instead of continuous values

---

### 4. Understand the Sigmoid Function

* What is a Sigmoid Curve?
* Output range (0 to 1)
* Converting values into probabilities

Formula:

$$f(x) = \frac{1}{1+e^{-x}}$$

Observe how inputs are transformed into probabilities.

---

### 5. Understand Probability Predictions

Examples:

* 0.10 → Class 0
* 0.35 → Class 0
* 0.75 → Class 1
* 0.95 → Class 1

Learn how probabilities become class labels.

---

### 6. Learn Decision Boundary

* What is a Decision Boundary?
* Threshold concept
* Default threshold = 0.5

Examples:

* Probability > 0.5 → Positive Class
* Probability < 0.5 → Negative Class

---

### 7. Understand Logistic Regression Workflow

1. Input Features
2. Linear Combination
3. Sigmoid Function
4. Probability Output
5. Class Prediction

---

### 8. Learn Evaluation Metrics for Classification

Introduction only:

* Accuracy
* Precision
* Recall
* F1 Score

(No need to calculate manually yet.)

---

### 9. Understand Confusion Matrix

Basic concepts:

* True Positive (TP)
* True Negative (TN)
* False Positive (FP)
* False Negative (FN)

Learn what each term means.

---

### 10. Visual Understanding

* Sigmoid Curve
* Decision Boundary
* Probability Output
* Classification Regions

---

## 🛠 Practice

* Classify 5 sample probabilities into Class 0 or Class 1
* Draw a simple Sigmoid Curve
* Create a small Confusion Matrix example
* Identify TP, TN, FP, and FN manually

---

## 📖 Resources

* Scikit-learn Logistic Regression Documentation
* GeeksforGeeks Logistic Regression Tutorial
* StatQuest Logistic Regression (YouTube)

---

## ✅ Checklist

* [ ] Classification understood
* [ ] Regression vs Classification understood
* [ ] Logistic Regression purpose understood
* [ ] Sigmoid Function understood
* [ ] Probability concept understood
* [ ] Decision Boundary understood
* [ ] Classification workflow understood
* [ ] Accuracy understood
* [ ] Precision understood
* [ ] Recall understood
* [ ] F1 Score understood
* [ ] Confusion Matrix understood
* [ ] Practice questions solved

---

## 🚀 Tomorrow (Day 13)

Implement Logistic Regression using Scikit-Learn:

* Load classification dataset
* Train Logistic Regression model
* Predict classes
* Predict probabilities
* Generate Confusion Matrix
* Calculate Accuracy Score
* Evaluate model performance
