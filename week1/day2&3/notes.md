## Resources

- GeeksforGeeks – Introduction to NumPy
# 1. Introduction to NumPy

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

---
# 2. Creating Arrays

NumPy arrays are created using the `np.array()` function. Arrays can be one-dimensional, two-dimensional, or multi-dimensional depending on the structure of the data provided.

## np.array()

Creates a NumPy array from a Python list or tuple.

```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5])
print(arr)
```

Output:

```text
[1 2 3 4 5]
```

---

## 1D Arrays

A one-dimensional array contains elements arranged in a single row.

```python
arr = np.array([10, 20, 30, 40])
print(arr)
```

Output:

```text
[10 20 30 40]
```

---

## 2D Arrays

A two-dimensional array contains rows and columns, similar to a matrix.

```python
arr = np.array([[1, 2, 3],
                [4, 5, 6]])

print(arr)
```

Output:

```text
[[1 2 3]
 [4 5 6]]
```

---

## 3D Arrays

A three-dimensional array consists of multiple 2D arrays.

```python
arr = np.array([
    [[1, 2], [3, 4]],
    [[5, 6], [7, 8]]
])

print(arr)
```

Output:

```text
[[[1 2]
  [3 4]]

 [[5 6]
  [7 8]]]
```

---

## Array Dimensions (`ndim`)

The `ndim` attribute returns the number of dimensions of an array.

```python
arr1 = np.array([1, 2, 3])
print(arr1.ndim)
```

Output:

```text
1
```

```python
arr2 = np.array([[1, 2], [3, 4]])
print(arr2.ndim)
```

Output:

```text
2
```

---

## Array Shape (`shape`)

The `shape` attribute returns a tuple representing the dimensions of the array.

```python
arr = np.array([[1, 2, 3],
                [4, 5, 6]])

print(arr.shape)
```

Output:

```text
(2, 3)
```

Meaning:

* 2 rows
* 3 columns

---

## Array Data Type (`dtype`)

The `dtype` attribute returns the data type of the array elements.

```python
arr = np.array([1, 2, 3, 4])

print(arr.dtype)
```

Output:

```text
int64
```

Example with floating-point values:

```python
arr = np.array([1.5, 2.5, 3.5])

print(arr.dtype)
```

Output:

```text
float64
```

---

## Summary

| Attribute    | Purpose                                        |
| ------------ | ---------------------------------------------- |
| `np.array()` | Creates a NumPy array                          |
| `ndim`       | Returns number of dimensions                   |
| `shape`      | Returns array dimensions (rows, columns, etc.) |
| `dtype`      | Returns data type of array elements            |

These are the fundamental concepts required before learning array operations, indexing, slicing, and broadcasting in NumPy.

---
# 3. Special Arrays

NumPy provides several built-in functions to quickly create arrays with specific values or patterns.

---

## np.zeros()

Creates an array filled with zeros.

```python
import numpy as np

arr = np.zeros((2, 3))
print(arr)
```

Output:

```text
[[0. 0. 0.]
 [0. 0. 0.]]
```

---

## np.ones()

Creates an array filled with ones.

```python
arr = np.ones((2, 3))
print(arr)
```

Output:

```text
[[1. 1. 1.]
 [1. 1. 1.]]
```

---

## np.empty()

Creates an array without initializing its values. The values depend on the memory location and may appear random.

```python
arr = np.empty((2, 3))
print(arr)
```

Output:

```text
[[6.932e-310 6.932e-310 6.932e-310]
 [6.932e-310 6.932e-310 6.932e-310]]
```

*Output may vary on different systems.*

---

## np.full()

Creates an array filled with a specified value.

```python
arr = np.full((2, 3), 7)
print(arr)
```

Output:

```text
[[7 7 7]
 [7 7 7]]
```

---

## np.eye()

Creates an identity matrix with 1s on the main diagonal and 0s elsewhere.

```python
arr = np.eye(3)
print(arr)
```

Output:

```text
[[1. 0. 0.]
 [0. 1. 0.]
 [0. 0. 1.]]
```

---

## np.arange()

Creates an array with evenly spaced values within a specified range.

```python
arr = np.arange(1, 10)
print(arr)
```

Output:

```text
[1 2 3 4 5 6 7 8 9]
```

Using a step value:

```python
arr = np.arange(0, 20, 2)
print(arr)
```

Output:

```text
[ 0  2  4  6  8 10 12 14 16 18]
```

---

## np.linspace()

Creates an array with a specified number of equally spaced values between a start and end value.

```python
arr = np.linspace(0, 10, 5)
print(arr)
```

Output:

```text
[ 0.   2.5  5.   7.5 10. ]
```

Parameters:

* Start value = 0
* End value = 10
* Number of values = 5

---

## Random Arrays

NumPy provides functions to generate random numbers.

### Random values between 0 and 1

```python
arr = np.random.rand(2, 3)
print(arr)
```

Example Output:

```text
[[0.42 0.78 0.15]
 [0.63 0.91 0.27]]
```

---

### Random Integers

```python
arr = np.random.randint(1, 10, size=(2, 3))
print(arr)
```

Example Output:

```text
[[4 7 2]
 [9 1 5]]
```

---

### Random Numbers from Standard Normal Distribution

```python
arr = np.random.randn(2, 3)
print(arr)
```

Example Output:

```text
[[ 0.56 -1.23  0.89]
 [-0.34  1.12 -0.76]]
```

---

## Summary

| Function              | Purpose                                       |
| --------------------- | --------------------------------------------- |
| `np.zeros()`          | Creates an array filled with zeros            |
| `np.ones()`           | Creates an array filled with ones             |
| `np.empty()`          | Creates an uninitialized array                |
| `np.full()`           | Creates an array filled with a specific value |
| `np.eye()`            | Creates an identity matrix                    |
| `np.arange()`         | Creates values within a range                 |
| `np.linspace()`       | Creates evenly spaced values                  |
| `np.random.rand()`    | Random values between 0 and 1                 |
| `np.random.randint()` | Random integers in a range                    |
| `np.random.randn()`   | Random values from normal distribution        |

These special array creation functions are widely used in Data Science, Machine Learning, and numerical computing to quickly generate datasets and matrices.

# 5. Indexing & Slicing

Indexing and slicing allow us to access, modify, and extract specific elements from NumPy arrays.

---

## Accessing Elements

Elements can be accessed using their index position.

```python
import numpy as np

arr = np.array([10, 20, 30, 40, 50])

print(arr[0])
print(arr[2])
```

Output:

```text
10
30
```

---

## Negative Indexing

Negative indices access elements from the end of the array.

```python
arr = np.array([10, 20, 30, 40, 50])

print(arr[-1])
print(arr[-2])
```

Output:

```text
50
40
```

---

## Slicing Arrays

Slicing extracts a portion of an array.

Syntax:

```python
array[start:end]
```

```python
arr = np.array([10, 20, 30, 40, 50])

print(arr[1:4])
```

Output:

```text
[20 30 40]
```

Examples:

```python
print(arr[:3])
print(arr[2:])
print(arr[::2])
```

Output:

```text
[10 20 30]
[30 40 50]
[10 30 50]
```

---

## Multi-Dimensional Indexing

Elements in a 2D array are accessed using row and column indices.

```python
arr = np.array([
    [1, 2, 3],
    [4, 5, 6]
])

print(arr[0, 1])
print(arr[1, 2])
```

Output:

```text
2
6
```

---

## Boolean Indexing

Boolean indexing selects elements based on a condition.

```python
arr = np.array([10, 20, 30, 40, 50])

print(arr[arr > 25])
```

Output:

```text
[30 40 50]
```

Example:

```python
print(arr[arr % 2 == 0])
```

Output:

```text
[10 20 30 40 50]
```

---

## Fancy Indexing

Fancy indexing uses a list or array of indices to access multiple elements.

```python
arr = np.array([10, 20, 30, 40, 50])

print(arr[[0, 2, 4]])
```

Output:

```text
[10 30 50]
```

Example:

```python
print(arr[[1, 3]])
```

Output:

```text
[20 40]
```

---

## Summary

| Method           | Purpose                 |
| ---------------- | ----------------------- |
| `arr[index]`     | Access a single element |
| `arr[-1]`        | Access from the end     |
| `arr[start:end]` | Slice an array          |
| `arr[row, col]`  | Access 2D elements      |
| `arr[condition]` | Boolean indexing        |
| `arr[[indices]]` | Fancy indexing          |

---

# 6. Array Operations

NumPy supports element-wise mathematical operations directly on arrays.

```python
import numpy as np

a = np.array([10, 20, 30])
b = np.array([1, 2, 3])
```

---

## Addition

Adds corresponding elements.

```python
print(a + b)
```

Output:

```text
[11 22 33]
```

---

## Subtraction

Subtracts corresponding elements.

```python
print(a - b)
```

Output:

```text
[ 9 18 27]
```

---

## Multiplication

Multiplies corresponding elements.

```python
print(a * b)
```

Output:

```text
[10 40 90]
```

---

## Division

Divides corresponding elements.

```python
print(a / b)
```

Output:

```text
[10. 10. 10.]
```

---

## Power Operations

Raises elements to a specified power.

```python
print(a ** 2)
```

Output:

```text
[100 400 900]
```

Example:

```python
print(b ** 3)
```

Output:

```text
[ 1  8 27]
```

---

## Modulus

Returns the remainder after division.

```python
print(a % b)
```

Output:

```text
[0 0 0]
```

Example:

```python
arr = np.array([11, 12, 13, 14])

print(arr % 2)
```

Output:

```text
[1 0 1 0]
```

---

## Operations with Scalars

A scalar operation is applied to every element in the array.

```python
arr = np.array([1, 2, 3])

print(arr + 5)
print(arr * 2)
```

Output:

```text
[6 7 8]
[2 4 6]
```

---

## Summary

| Operation      | Example  |
| -------------- | -------- |
| Addition       | `a + b`  |
| Subtraction    | `a - b`  |
| Multiplication | `a * b`  |
| Division       | `a / b`  |
| Power          | `a ** 2` |
| Modulus        | `a % b`  |

NumPy performs these operations element-wise, making numerical computations faster and more efficient than traditional Python loops.

---
# 7. Broadcasting

Broadcasting is a powerful NumPy feature that allows arrays of different shapes to perform arithmetic operations without explicitly reshaping them.

Instead of creating copies of data, NumPy automatically expands smaller arrays to match the shape of larger arrays whenever possible.

---

## Broadcasting Concept

Normally, mathematical operations are performed between arrays of the same shape.

```python
import numpy as np

a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

print(a + b)
```

Output:

```text
[5 7 9]
```

With broadcasting, NumPy can also perform operations between an array and a scalar.

```python
a = np.array([1, 2, 3])

print(a + 10)
```

Output:

```text
[11 12 13]
```

NumPy automatically treats the scalar `10` as:

```text
[10 10 10]
```

and performs element-wise addition.

---

## Broadcasting Rules

NumPy compares array shapes starting from the rightmost dimension.

Two dimensions are compatible when:

1. They are equal.
2. One of them is 1.

If neither condition is satisfied, broadcasting fails and NumPy raises an error.

---

### Rule 1: Same Shape

```python
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

print(a + b)
```

Shapes:

```text
(3,) and (3,)
```

Broadcasting is not needed because shapes already match.

---

### Rule 2: One Dimension is 1

```python
a = np.array([[1], [2], [3]])
b = np.array([10, 20, 30])

print(a + b)
```

Shapes:

```text
(3,1) and (3,)
```

Output:

```text
[[11 21 31]
 [12 22 32]
 [13 23 33]]
```

NumPy automatically expands the smaller dimension.

---

### Rule 3: Incompatible Shapes

```python
a = np.array([1, 2, 3])
b = np.array([1, 2])

print(a + b)
```

Shapes:

```text
(3,) and (2,)
```

Output:

```text
ValueError: operands could not be broadcast together
```

The dimensions are neither equal nor 1.

---

## Broadcasting Examples

### Example 1: Scalar Broadcasting

```python
arr = np.array([1, 2, 3, 4])

print(arr * 5)
```

Output:

```text
[ 5 10 15 20]
```

---

### Example 2: Adding a Row Vector

```python
arr = np.array([
    [1, 2, 3],
    [4, 5, 6]
])

row = np.array([10, 20, 30])

print(arr + row)
```

Output:

```text
[[11 22 33]
 [14 25 36]]
```

The row vector is automatically applied to each row.

---

### Example 3: Adding a Column Vector

```python
arr = np.array([
    [1, 2, 3],
    [4, 5, 6]
])

col = np.array([[10],
                [20]])

print(arr + col)
```

Output:

```text
[[11 12 13]
 [24 25 26]]
```

The column vector is automatically applied to each row.

---

### Example 4: Multiplying a Matrix by a Scalar

```python
arr = np.array([
    [1, 2],
    [3, 4]
])

print(arr * 2)
```

Output:

```text
[[2 4]
 [6 8]]
```

---

## Advantages of Broadcasting

* Reduces the need for loops.
* Improves performance.
* Saves memory.
* Makes code shorter and easier to read.

---

## Summary

| Concept      | Description                                          |
| ------------ | ---------------------------------------------------- |
| Broadcasting | Allows operations between arrays of different shapes |
| Rule 1       | Dimensions are equal                                 |
| Rule 2       | One dimension is 1                                   |
| Rule 3       | Otherwise broadcasting fails                         |
| Benefit      | Faster and more memory-efficient computations        |

Broadcasting is one of the most important NumPy features and is heavily used in Data Science, Machine Learning, and Deep Learning for efficient mathematical computations.
