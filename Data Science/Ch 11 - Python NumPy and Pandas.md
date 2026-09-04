# Chapter 11: Python, NumPy, and Pandas

## Python Fundamentals for Data Science

Python is a high-level, interpreted programming language that is widely used in data science. It provides a rich set of libraries and tools for data analysis, visualization, and machine learning.

### Python Basics

Python basics include variables, data types, operators, control structures, and functions. These are the building blocks of Python programming.

```python
# Variables
x = 10
y = 20

# Data types
int, float, str, bool, list, tuple, dict, set

# Operators
+, -, *, /, //, %, **

# Control structures
if, else, elif, for, while, break, continue

# Functions
def function_name(parameters):
    # Function body
    return value
```

### Python Libraries for Data Science

Python libraries for data science include NumPy, Pandas, Matplotlib, Seaborn, and Scikit-learn. These libraries provide a rich set of tools for data analysis, visualization, and machine learning.

## NumPy

NumPy is a library for numerical computing in Python. It provides support for large, multi-dimensional arrays and matrices, along with a large collection of mathematical functions to operate on these arrays.

### NumPy Arrays

NumPy arrays are multi-dimensional arrays that are used to store numerical data. They are created using the `numpy.array()` function.

```python
import numpy as np

# Create a NumPy array
arr = np.array([1, 2, 3, 4, 5])

# Create a multi-dimensional NumPy array
arr_2d = np.array([[1, 2, 3], [4, 5, 6]])
```

### NumPy Functions

NumPy functions include mathematical functions, statistical functions, and array manipulation functions. These functions are used to perform operations on NumPy arrays.

```python
# Mathematical functions
np.sin(arr), np.cos(arr), np.exp(arr), np.log(arr)

# Statistical functions
np.mean(arr), np.median(arr), np.std(arr), np.var(arr)

# Array manipulation functions
np.reshape(arr, (2, 3)), np.transpose(arr), np.concatenate((arr1, arr2))
```

## Pandas

Pandas is a library for data manipulation and analysis in Python. It provides data structures and functions designed to work with structured (tabular, multidimensional, potentially heterogeneous) and time series data.

### Pandas DataFrames

Pandas DataFrames are two-dimensional, size-mutable, and heterogeneous tabular data structures with labeled axes. They are created using the `pandas.DataFrame()` function.

```python
import pandas as pd

# Create a Pandas DataFrame
df = pd.DataFrame({'A': [1, 2, 3], 'B': [4, 5, 6]})
```

### Pandas Series

Pandas Series are one-dimensional labeled arrays capable of holding data of any type. They are created using the `pandas.Series()` function.

```python
# Create a Pandas Series
s = pd.Series([1, 2, 3, 4, 5])
```

### Data Manipulation

Data manipulation involves performing operations on Pandas DataFrames and Series to clean, transform, and analyze data. It includes selecting data, filtering data, sorting data, and aggregating data.

```python
# Select data
df['A'], df[['A', 'B']], df.loc[0], df.iloc[0]

# Filter data
df[df['A'] > 1], df.query('A > 1')

# Sort data
df.sort_values('A'), df.sort_index()

# Aggregate data
df.groupby('A').mean(), df.groupby('A').sum(), df.pivot_table(values='A', index='B')
```

## Conclusion

Python, NumPy, and Pandas are essential tools for data science. By understanding Python fundamentals, NumPy arrays and functions, and Pandas DataFrames and Series, we can perform data analysis, visualization, and machine learning effectively. This ensures the accuracy and reliability of our analysis and insights.