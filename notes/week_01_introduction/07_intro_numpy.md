>[Back to Week Menu](README.md)
>
>Previous Theme: [Setting up the Environment](06_environment.md)
>
>Next Theme: [Linear Algebra Refresher](08_linear_algebra.md)

## Introduction to NumPy
_[Video source](https://www.youtube.com/watch?v=Qa0-jYtRdbY&list=PL3MmuxUbc_hIhxl5Ji8t4O6lPAOpHaCLR&index=7
)_

**NumPy** (Numerical Python) is a fundamental package for scientific computing in Python. It provides a high-performance multidimensional array object, as well as tools for working with these arrays. NumPy is essential for conducting numerical computations and serves as the foundational package for many other scientific computing libraries in the Python ecosystem.

### Import numpy
```
import numpy as np
```


### Creating arrays

```
np.zeros(5) # array size of 5 with zeros
>> array([0., 0., 0., 0., 0.])

np.ones(10) # array size of 10 with ones
>> array([1., 1., 1., 1., 1., 1., 1., 1., 1., 1.])

np.full(10, 2.5)    # array size of 10 with some arbitrary number (2.5)
>> array([2.5, 2.5, 2.5, 2.5, 2.5, 2.5, 2.5, 2.5, 2.5, 2.5])

# convert a python list to array
np.arange(3, 10)
>> array([3, 4, 5, 6, 7, 8, 9])

# create a range
np.arange(10)
>> array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])

# create an array and fills with numbers between first and second parameter:
np.linspace(0, 1, 11)
>> array([0. , 0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9, 1. ])
```

### Multi-dimensional arrays

```
# create an array with 5 rows and 2 columns and fill it with '0':
np.zeros((5, 2))

>> array([[0., 0.],
       [0., 0.],
       [0., 0.],
       [0., 0.],
       [0., 0.]])

# Create an array from python list:
np.array([
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
])

>> array([[1, 2, 3],
       [4, 5, 6],
       [7, 8, 9]])
```


```
n[0]    # Get the first row from the array
>> array([1, 2, 3])


n[:, 0] # Get the first column from the array
>> array([1, 4, 7])
```

### Randomly generated arrays

Random numbers from Standard uniform distribution (matrix 5x2):

```
np.random.seed(2)   # for reproducibility
np.random.rand(5, 2)    # Generates random numbers between 0 and 1

array([[0.4359949 , 0.02592623],
       [0.54966248, 0.43532239],
       [0.4203678 , 0.33033482],
       [0.20464863, 0.61927097],
       [0.29965467, 0.26682728]])
```

Random numbers from Standard normal distribution:
```
np.random.seed(2)   # for reproducibility
np.random.randn(5, 2)    # Generates random numbers from Standard normal distribution

array([[-0.41675785, -0.05626683],
       [-2.1361961 ,  1.64027081],
       [-1.79343559, -0.84174737],
       [ 0.50288142, -1.24528809],
       [-1.05795222, -0.90900761]])
```

Generate random integers:
```
np.random.seed(2)
np.random.randint(low=0, high=100, size=(5, 2))

array([[40, 15],
       [72, 22],
       [43, 82],
       [75,  7],
       [34, 49]])
```

### Element-wise operations

Perform different operations with every element from array:
```
a =np.arange(5)
a
>> array([0, 1, 2, 3, 4])

a + 1
>> array([1, 2, 3, 4, 5])

a * 2
>> array([0, 2, 4, 6, 8])

```

Perform different operations with 2 arrays of the same shape (element by element):
```
b =np.arange(2, 7)
b
>> array([2, 3, 4, 5, 6])

a + b
>> array([ 2,  4,  6,  8, 10])
```

### Comparison operations

Compare every element from array to number or other array's element
```
a >= 2
>> array([False, False,  True,  True,  True])

a > b
>> array([False, False, False, False, False])
```

Select elements of array based on certain condition:
```
a[a >= 2]
>> array([2, 3, 4])

a[a > b]
>> array([], dtype=int64)
```

### Summarizing operations

Return a single number instead of a new array
```
a
>> array([0, 1, 2, 3, 4])

a.min()
>> 0
a.max()
>> 4
a.sum()
>> 10
a.mean()    # average (mean) value
>> 2.0
a.std()     # Standard deviation
>> 1.4142135623730951
```


_[Back to the top](#introduction-to-numpy)_