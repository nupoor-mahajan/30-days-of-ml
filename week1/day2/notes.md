# Introduction to NumPy

## Resources

- GeeksforGeeks – Introduction to NumPy

## What is NumPy?

**NumPy (Numerical Python)** is a powerful Python library used for numerical computing and data analysis. It provides efficient multi-dimensional array objects along with a large collection of mathematical functions for performing operations on those arrays.

NumPy is a fundamental library in the Python data science ecosystem and serves as the foundation for libraries such as Pandas, Scikit-Learn, TensorFlow, and PyTorch.

### Key Features

* Fast and efficient multi-dimensional arrays.
* Vectorized mathematical operations.
* Support for linear algebra, statistics, and random number generation.
* Memory-efficient data storage.
* Foundation for many Machine Learning and Data Science libraries.

---

## Installation

Install NumPy using pip:

```bash
pip install numpy
```

---

## Importing NumPy

The standard convention is to import NumPy using the alias `np`:

```python
import numpy as np
```

This allows access to NumPy functions using shorter syntax:

```python
arr = np.array([1, 2, 3, 4, 5])
print(arr)
```

---

## Why is NumPy Fast?

NumPy achieves high performance because its core operations are implemented using highly optimized **C** and **Fortran** libraries rather than pure Python code.

Advantages include:

* Reduced execution time for numerical computations.
* Efficient memory management.
* Vectorized operations that eliminate slow Python loops.
* Optimized low-level implementation for mathematical calculations.

### Example

Python List Addition:

```python
a = [1, 2, 3]
b = [4, 5, 6]

result = []
for i in range(len(a)):
    result.append(a[i] + b[i])
```

NumPy Array Addition:

```python
import numpy as np

a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

result = a + b
print(result)
```

Output:

```text
[5 7 9]
```

The NumPy approach is shorter, cleaner, and significantly faster for large datasets.

---

## Summary

* NumPy stands for Numerical Python.
* It is the core library for numerical computing in Python.
* NumPy provides efficient multi-dimensional arrays and mathematical functions.
* It is widely used in Data Science, Machine Learning, and Artificial Intelligence.
* NumPy is fast because it uses optimized C and Fortran implementations underneath Python.
