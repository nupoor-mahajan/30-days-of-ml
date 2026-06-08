# Resources

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

# 8. Mathematical Functions

NumPy provides a wide range of mathematical functions for performing statistical and numerical operations on arrays.

```python
import numpy as np

arr = np.array([10, 20, 30, 40, 50])
```

## np.sum()

Returns the sum of all elements.

```python
np.sum(arr)
```

Output:

```text
150
```

## np.mean()

Returns the average of array elements.

```python
np.mean(arr)
```

Output:

```text
30.0
```

## np.median()

Returns the middle value after sorting.

```python
np.median(arr)
```

Output:

```text
30.0
```

## np.std()

Returns the standard deviation.

```python
np.std(arr)
```

Output:

```text
14.1421356237
```

## np.var()

Returns the variance.

```python
np.var(arr)
```

Output:

```text
200.0
```

## np.min()

Returns the minimum value.

```python
np.min(arr)
```

Output:

```text
10
```

## np.max()

Returns the maximum value.

```python
np.max(arr)
```

Output:

```text
50
```

## np.argmin()

Returns the index of the minimum value.

```python
np.argmin(arr)
```

Output:

```text
0
```

## np.argmax()

Returns the index of the maximum value.

```python
np.argmax(arr)
```

Output:

```text
4
```

---

# 9. Array Manipulation

Array manipulation functions help modify the structure and layout of arrays.

## reshape()

Changes the shape of an array without changing its data.

```python
arr = np.array([1, 2, 3, 4, 5, 6])

print(arr.reshape(2, 3))
```

Output:

```text
[[1 2 3]
 [4 5 6]]
```

## flatten()

Converts a multi-dimensional array into a 1D array and returns a copy.

```python
arr = np.array([[1, 2], [3, 4]])

print(arr.flatten())
```

Output:

```text
[1 2 3 4]
```

## ravel()

Converts a multi-dimensional array into a 1D array and returns a view whenever possible.

```python
arr.ravel()
```

Output:

```text
[1 2 3 4]
```

## transpose()

Swaps rows and columns.

```python
arr = np.array([[1, 2, 3],
                [4, 5, 6]])

print(arr.transpose())
```

Output:

```text
[[1 4]
 [2 5]
 [3 6]]
```

## swapaxes()

Interchanges specified axes.

```python
arr = np.array([
    [[1, 2],
     [3, 4]]
])

print(np.swapaxes(arr, 1, 2))
```

---

# 10. Joining Arrays

NumPy provides functions to combine multiple arrays.

## concatenate()

Joins arrays along an existing axis.

```python
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

print(np.concatenate((a, b)))
```

Output:

```text
[1 2 3 4 5 6]
```

## stack()

Stacks arrays along a new axis.

```python
print(np.stack((a, b)))
```

Output:

```text
[[1 2 3]
 [4 5 6]]
```

## hstack()

Stacks arrays horizontally.

```python
print(np.hstack((a, b)))
```

Output:

```text
[1 2 3 4 5 6]
```

## vstack()

Stacks arrays vertically.

```python
print(np.vstack((a, b)))
```

Output:

```text
[[1 2 3]
 [4 5 6]]
```

---

# 11. Splitting Arrays

Splitting functions divide arrays into smaller parts.

## split()

Splits an array into equal sections.

```python
arr = np.array([1, 2, 3, 4, 5, 6])

print(np.split(arr, 3))
```

Output:

```text
[array([1, 2]), array([3, 4]), array([5, 6])]
```

## hsplit()

Splits arrays horizontally.

```python
arr = np.array([[1, 2, 3, 4]])

print(np.hsplit(arr, 2))
```

Output:

```text
[array([[1, 2]]), array([[3, 4]])]
```

## vsplit()

Splits arrays vertically.

```python
arr = np.array([
    [1, 2],
    [3, 4],
    [5, 6],
    [7, 8]
])

print(np.vsplit(arr, 2))
```

Output:

```text
[array([[1, 2],
       [3, 4]]),
 array([[5, 6],
       [7, 8]])]
```

---

# 12. Searching & Sorting

## where()

Returns indices where a condition is true.

```python
arr = np.array([10, 20, 30, 40])

print(np.where(arr > 20))
```

Output:

```text
(array([2, 3]),)
```

## sort()

Returns a sorted copy of the array.

```python
arr = np.array([5, 2, 8, 1])

print(np.sort(arr))
```

Output:

```text
[1 2 5 8]
```

## argsort()

Returns indices that would sort the array.

```python
arr = np.array([50, 20, 80, 10])

print(np.argsort(arr))
```

Output:

```text
[3 1 0 2]
```

## unique()

Returns unique values.

```python
arr = np.array([1, 2, 2, 3, 3, 4])

print(np.unique(arr))
```

Output:

```text
[1 2 3 4]
```

---

# 13. Filtering Arrays

Filtering allows selection of elements based on conditions.

## Boolean Masks

A Boolean mask is an array containing True and False values.

```python
arr = np.array([10, 20, 30, 40, 50])

mask = arr > 25

print(mask)
```

Output:

```text
[False False True True True]
```

## Conditional Filtering

Use Boolean masks to filter elements.

```python
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

# 14. Random Module

## np.random.rand()

Generates random values between 0 and 1.

```python
np.random.rand(2, 3)
```

## np.random.randint()

Generates random integers.

```python
np.random.randint(1, 10, size=(2, 3))
```

## np.random.randn()

Generates values from a standard normal distribution.

```python
np.random.randn(2, 3)
```

## Random Seed

Produces reproducible random results.

```python
np.random.seed(42)

print(np.random.randint(1, 10, 5))
```

Output:

```text
[7 4 8 5 7]
```

---

# 15. Linear Algebra

Linear Algebra is one of the most important mathematical foundations of Machine Learning. NumPy provides a dedicated module, `numpy.linalg`, for performing linear algebra operations.

```python
import numpy as np
```

---

## Dot Product

The dot product multiplies corresponding elements and then sums the results.

```python
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

print(np.dot(a, b))
```

Output:

```text
32
```

Calculation:

```text
(1×4) + (2×5) + (3×6)
= 4 + 10 + 18
= 32
```

---

## Matrix Multiplication

Used to multiply matrices.

```python
a = np.array([
    [1, 2],
    [3, 4]
])

b = np.array([
    [5, 6],
    [7, 8]
])

print(np.matmul(a, b))
```

Output:

```text
[[19 22]
 [43 50]]
```

Alternative:

```python
print(a @ b)
```

---

## Transpose

Swaps rows and columns.

```python
a = np.array([
    [1, 2, 3],
    [4, 5, 6]
])

print(a.T)
```

Output:

```text
[[1 4]
 [2 5]
 [3 6]]
```

---

## Determinant

A determinant is a special value calculated from a square matrix.

```python
a = np.array([
    [1, 2],
    [3, 4]
])

print(np.linalg.det(a))
```

Output:

```text
-2.0
```

---

## Inverse

The inverse of a matrix is similar to reciprocal for numbers.

```python
a = np.array([
    [1, 2],
    [3, 4]
])

print(np.linalg.inv(a))
```

Output:

```text
[[-2.   1. ]
 [ 1.5 -0.5]]
```

---

## Eigenvalues & Eigenvectors

Widely used in PCA and dimensionality reduction.

```python
a = np.array([
    [4, 2],
    [1, 3]
])

values, vectors = np.linalg.eig(a)

print(values)
print(vectors)
```

Example Output:

```text
[5. 2.]
```

---

# 16. Useful Functions

These functions are commonly used while preprocessing and manipulating data.

---

## copy()

Creates a completely independent copy of an array.

```python
arr = np.array([1, 2, 3])

new_arr = arr.copy()

arr[0] = 100

print(arr)
print(new_arr)
```

Output:

```text
[100   2   3]
[1 2 3]
```

Changes in the original array do not affect the copied array.

---

## view()

Creates a view that shares memory with the original array.

```python
arr = np.array([1, 2, 3])

new_arr = arr.view()

arr[0] = 100

print(arr)
print(new_arr)
```

Output:

```text
[100   2   3]
[100   2   3]
```

Changes in one array affect the other.

---

## astype()

Converts array elements to another data type.

```python
arr = np.array([1.1, 2.2, 3.3])

print(arr.astype(int))
```

Output:

```text
[1 2 3]
```

---

## clip()

Limits values within a specified range.

```python
arr = np.array([5, 10, 15, 20, 25])

print(np.clip(arr, 10, 20))
```

Output:

```text
[10 10 15 20 20]
```

Values below 10 become 10 and values above 20 become 20.

---

# 17. NumPy for Machine Learning

NumPy is the backbone of most Machine Learning workflows.

---

## Feature Matrix

A Feature Matrix contains input features used for training a model.

```python
X = np.array([
    [22, 50000],
    [25, 60000],
    [30, 80000]
])

print(X)
```

Output:

```text
[[   22 50000]
 [   25 60000]
 [   30 80000]]
```

Here:

* Column 1 = Age
* Column 2 = Salary

Shape:

```python
print(X.shape)
```

Output:

```text
(3, 2)
```

Meaning:

* 3 samples
* 2 features

---

## Label Vector

A Label Vector contains the target values.

```python
y = np.array([0, 1, 1])

print(y)
```

Output:

```text
[0 1 1]
```

Here:

* 0 = No
* 1 = Yes

Shape:

```python
print(y.shape)
```

Output:

```text
(3,)
```

---

## Vectorization

Vectorization means performing operations on entire arrays without loops.

Traditional Python:

```python
numbers = [1, 2, 3, 4]

result = []

for num in numbers:
    result.append(num * 2)
```

NumPy:

```python
arr = np.array([1, 2, 3, 4])

result = arr * 2

print(result)
```

Output:

```text
[2 4 6 8]
```

Vectorized operations are faster and cleaner.

---

## Performance Optimization

NumPy is optimized because:

* Core operations are written in C and Fortran.
* Uses contiguous memory storage.
* Reduces Python loops.
* Supports vectorized computations.

Example:

```python
arr = np.arange(1000000)

result = arr * 2
```

This operation is significantly faster than using Python loops.

---

