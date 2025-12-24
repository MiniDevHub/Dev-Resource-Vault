<div align="center">

# 🐍 Python Data Science - Complete Practical Guide

![Python](https://img.shields.io/badge/Python-Data_Science-blue?style=for-the-badge&logo=python)
![NumPy](https://img.shields.io/badge/NumPy-Pandas-green?style=for-the-badge)
![Level](https://img.shields.io/badge/Level-Beginner_to_Advanced-orange?style=for-the-badge)

### _Turn raw data into actionable insights_ 📊

**Data is the new oil, but insights are the new gold** 💰

</div>

---

## 📚 Table of Contents

- [🎯 Data Science Fundamentals](#-data-science-fundamentals)
- [🔢 NumPy - Numerical Computing](#-numpy---numerical-computing)
- [🐼 Pandas - Data Manipulation](#-pandas---data-manipulation)
- [🧹 Data Cleaning](#-data-cleaning)
- [🔍 Exploratory Data Analysis](#-exploratory-data-analysis)
- [📊 Data Visualization](#-data-visualization)
- [📈 Statistical Analysis](#-statistical-analysis)
- [🔧 Feature Engineering](#-feature-engineering)
- [⚡ Performance Optimization](#-performance-optimization)
- [🚀 Real-World Projects](#-real-world-projects)
- [✅ Best Practices](#-best-practices)

---

<div align="center">

## 🎯 Data Science Fundamentals

</div>

### Understanding Data Science 📖

```bash
# ═══════════════════════════════════════════
# WHAT IS DATA SCIENCE?
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   DATA SCIENCE WORKFLOW                    ║
╚════════════════════════════════════════════════════════════╝

The Data Science Process:
─────────────────────────────────────────────────────────────

1. Ask Questions 🤔
   ↓
2. Get Data 📊
   ↓
3. Clean Data 🧹
   ↓
4. Explore Data 🔍
   ↓
5. Model Data 🤖
   ↓
6. Communicate Results 📢
   ↓
7. Deploy & Monitor 🚀

Key Skills:
─────────────────────────────────────────────────────────────
• Programming (Python, R)
• Statistics & Mathematics
• Data Wrangling
• Data Visualization
• Machine Learning
• Domain Knowledge
• Communication

Python Data Science Stack:
─────────────────────────────────────────────────────────────
┌─────────────────────────────────────────┐
│  Machine Learning                       │
│  scikit-learn, TensorFlow, PyTorch     │
└─────────────────────────────────────────┘
          ↑
┌─────────────────────────────────────────┐
│  Visualization                          │
│  Matplotlib, Seaborn, Plotly           │
└─────────────────────────────────────────┘
          ↑
┌─────────────────────────────────────────┐
│  Data Manipulation                      │
│  Pandas, Polars                         │
└─────────────────────────────────────────┘
          ↑
┌─────────────────────────────────────────┐
│  Numerical Computing                    │
│  NumPy, SciPy                          │
└─────────────────────────────────────────┘
          ↑
┌─────────────────────────────────────────┐
│  Python                                 │
└─────────────────────────────────────────┘

# ═══════════════════════════════════════════
# SETUP ENVIRONMENT
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   INSTALLATION                             ║
╚════════════════════════════════════════════════════════════╝

Install Core Libraries:
─────────────────────────────────────────────────────────────
# Using pip
pip install numpy pandas matplotlib seaborn scipy scikit-learn jupyter

# Using conda (recommended for data science)
conda create -n data-science python=3.11
conda activate data-science
conda install numpy pandas matplotlib seaborn scipy scikit-learn jupyter

# Or install Anaconda (all-in-one)
# Download from: https://www.anaconda.com/download

Essential Libraries:
─────────────────────────────────────────────────────────────
numpy         # Numerical computing
pandas        # Data manipulation
matplotlib    # Basic plotting
seaborn       # Statistical visualization
plotly        # Interactive plots
scipy         # Scientific computing
scikit-learn  # Machine learning
jupyter       # Interactive notebooks
statsmodels   # Statistical modeling

Jupyter Notebook:
─────────────────────────────────────────────────────────────
# Start Jupyter
jupyter notebook

# Or JupyterLab (better interface)
pip install jupyterlab
jupyter lab

# Access: http://localhost:8888

Standard Imports:
─────────────────────────────────────────────────────────────
# Data manipulation
import numpy as np
import pandas as pd

# Visualization
import matplotlib.pyplot as plt
import seaborn as sns

# Statistics
from scipy import stats

# Machine Learning
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler

# Settings
%matplotlib inline  # For Jupyter
pd.set_option('display.max_columns', None)
pd.set_option('display.max_rows', 100)
plt.style.use('seaborn-v0_8')
sns.set_palette("husl")

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🔢 NumPy - Numerical Computing

</div>

### Array Operations & Linear Algebra 🧮

```python
# ═══════════════════════════════════════════
# NUMPY FUNDAMENTALS
# ═══════════════════════════════════════════

"""
NumPy (Numerical Python)
- Foundation of Python data science
- Fast operations on arrays
- Written in C (much faster than pure Python)
- Broadcasting capabilities
"""

import numpy as np

# ═══════════════════════════════════════════
# CREATING ARRAYS
# ═══════════════════════════════════════════

# From list
arr = np.array([1, 2, 3, 4, 5])
print(arr)              # [1 2 3 4 5]
print(type(arr))        # <class 'numpy.ndarray'>

# 2D array (matrix)
matrix = np.array([[1, 2, 3],
                   [4, 5, 6],
                   [7, 8, 9]])

print(matrix)
# [[1 2 3]
#  [4 5 6]
#  [7 8 9]]

# Array attributes
print(arr.shape)        # (5,)
print(matrix.shape)     # (3, 3)
print(arr.ndim)         # 1 (dimensions)
print(matrix.ndim)      # 2
print(arr.size)         # 5 (total elements)
print(arr.dtype)        # int64

# Special arrays
zeros = np.zeros((3, 4))        # 3x4 array of zeros
ones = np.ones((2, 3))          # 2x3 array of ones
empty = np.empty((2, 2))        # Uninitialized 2x2 array
eye = np.eye(4)                 # 4x4 identity matrix
full = np.full((3, 3), 7)       # 3x3 array filled with 7

# Ranges
arange = np.arange(0, 10, 2)    # [0, 2, 4, 6, 8]
linspace = np.linspace(0, 1, 5) # [0. 0.25 0.5 0.75 1.]

# Random arrays
np.random.seed(42)  # For reproducibility
random = np.random.random((3, 3))       # Uniform [0, 1)
randn = np.random.randn(3, 3)           # Standard normal
randint = np.random.randint(0, 10, (3, 3))  # Random integers

# ═══════════════════════════════════════════
# ARRAY INDEXING & SLICING
# ═══════════════════════════════════════════

arr = np.array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])

# Indexing
print(arr[0])           # 0 (first element)
print(arr[-1])          # 9 (last element)

# Slicing
print(arr[2:5])         # [2 3 4]
print(arr[:5])          # [0 1 2 3 4]
print(arr[5:])          # [5 6 7 8 9]
print(arr[::2])         # [0 2 4 6 8] (every other)
print(arr[::-1])        # [9 8 7 6 5 4 3 2 1 0] (reverse)

# 2D indexing
matrix = np.array([[1, 2, 3],
                   [4, 5, 6],
                   [7, 8, 9]])

print(matrix[0, 0])     # 1 (row 0, col 0)
print(matrix[1, :])     # [4 5 6] (row 1, all columns)
print(matrix[:, 1])     # [2 5 8] (all rows, col 1)
print(matrix[0:2, 1:3]) # [[2 3]
                        #  [5 6]]

# Boolean indexing
arr = np.array([1, 2, 3, 4, 5])
mask = arr > 3
print(mask)             # [False False False  True  True]
print(arr[mask])        # [4 5]
print(arr[arr > 3])     # [4 5] (shorthand)

# Fancy indexing
arr = np.array([10, 20, 30, 40, 50])
indices = [0, 2, 4]
print(arr[indices])     # [10 30 50]

# ═══════════════════════════════════════════
# ARRAY OPERATIONS
# ═══════════════════════════════════════════

arr = np.array([1, 2, 3, 4, 5])

# Arithmetic (element-wise)
print(arr + 10)         # [11 12 13 14 15]
print(arr * 2)          # [ 2  4  6  8 10]
print(arr ** 2)         # [ 1  4  9 16 25]
print(1 / arr)          # [1.   0.5  0.33 0.25 0.2]

# Array operations
arr1 = np.array([1, 2, 3])
arr2 = np.array([4, 5, 6])

print(arr1 + arr2)      # [5 7 9]
print(arr1 * arr2)      # [ 4 10 18]
print(arr1 @ arr2)      # 32 (dot product)
print(np.dot(arr1, arr2))  # 32 (same)

# Universal functions (ufuncs)
arr = np.array([1, 4, 9, 16, 25])

print(np.sqrt(arr))     # [1. 2. 3. 4. 5.]
print(np.exp(arr))      # Exponential
print(np.log(arr))      # Natural log
print(np.sin(arr))      # Sine
print(np.abs(arr))      # Absolute value

# Aggregations
arr = np.array([1, 2, 3, 4, 5])

print(arr.sum())        # 15
print(arr.mean())       # 3.0
print(arr.std())        # 1.414... (standard deviation)
print(arr.var())        # 2.0 (variance)
print(arr.min())        # 1
print(arr.max())        # 5
print(arr.argmin())     # 0 (index of min)
print(arr.argmax())     # 4 (index of max)

# Axis operations
matrix = np.array([[1, 2, 3],
                   [4, 5, 6]])

print(matrix.sum())           # 21 (total)
print(matrix.sum(axis=0))     # [5 7 9] (sum each column)
print(matrix.sum(axis=1))     # [ 6 15] (sum each row)

# ═══════════════════════════════════════════
# BROADCASTING
# ═══════════════════════════════════════════

"""
Broadcasting: NumPy's way of performing operations on
arrays of different shapes
"""

# Scalar broadcasting
arr = np.array([1, 2, 3])
print(arr + 10)         # [11 12 13]

# Array broadcasting
arr1 = np.array([[1, 2, 3],
                 [4, 5, 6]])  # Shape: (2, 3)
arr2 = np.array([10, 20, 30]) # Shape: (3,)

print(arr1 + arr2)
# [[11 22 33]
#  [14 25 36]]

# Column vector broadcasting
arr1 = np.array([[1, 2, 3],
                 [4, 5, 6]])          # (2, 3)
arr2 = np.array([[10], [20]])         # (2, 1)

print(arr1 + arr2)
# [[11 12 13]
#  [24 25 26]]

# ═══════════════════════════════════════════
# RESHAPING & TRANSFORMING
# ═══════════════════════════════════════════

arr = np.arange(12)     # [0 1 2 3 4 5 6 7 8 9 10 11]

# Reshape
reshaped = arr.reshape(3, 4)
print(reshaped)
# [[ 0  1  2  3]
#  [ 4  5  6  7]
#  [ 8  9 10 11]]

# Flatten
flat = reshaped.flatten()
print(flat)             # [0 1 2 3 4 5 6 7 8 9 10 11]

# Transpose
matrix = np.array([[1, 2, 3],
                   [4, 5, 6]])
print(matrix.T)
# [[1 4]
#  [2 5]
#  [3 6]]

# Concatenate
arr1 = np.array([1, 2, 3])
arr2 = np.array([4, 5, 6])

# Vertical stack (row-wise)
vstack = np.vstack([arr1, arr2])
print(vstack)
# [[1 2 3]
#  [4 5 6]]

# Horizontal stack (column-wise)
hstack = np.hstack([arr1, arr2])
print(hstack)           # [1 2 3 4 5 6]

# Concatenate
concat = np.concatenate([arr1, arr2])
print(concat)           # [1 2 3 4 5 6]

# Split
arr = np.arange(10)
split = np.split(arr, 5)  # Split into 5 equal parts
print(split)            # [array([0, 1]), array([2, 3]), ...]

# ═══════════════════════════════════════════
# LINEAR ALGEBRA
# ═══════════════════════════════════════════

# Matrix multiplication
A = np.array([[1, 2],
              [3, 4]])
B = np.array([[5, 6],
              [7, 8]])

# Dot product
C = np.dot(A, B)        # or A @ B
print(C)
# [[19 22]
#  [43 50]]

# Matrix operations
print(A.T)              # Transpose
print(np.linalg.inv(A)) # Inverse
print(np.linalg.det(A)) # Determinant: -2.0

# Eigenvalues & eigenvectors
eigenvalues, eigenvectors = np.linalg.eig(A)
print("Eigenvalues:", eigenvalues)
print("Eigenvectors:\n", eigenvectors)

# Solve linear equations (Ax = b)
# 2x + 3y = 8
# 3x + 5y = 14
A = np.array([[2, 3],
              [3, 5]])
b = np.array([8, 14])
x = np.linalg.solve(A, b)
print(x)                # [1. 2.]

# ═══════════════════════════════════════════
# STATISTICAL FUNCTIONS
# ═══════════════════════════════════════════

data = np.random.randn(1000)  # 1000 random numbers

# Descriptive statistics
print("Mean:", data.mean())
print("Median:", np.median(data))
print("Std:", data.std())
print("Var:", data.var())
print("Min:", data.min())
print("Max:", data.max())

# Percentiles
print("25th percentile:", np.percentile(data, 25))
print("50th percentile:", np.percentile(data, 50))  # median
print("75th percentile:", np.percentile(data, 75))

# Correlation
x = np.random.randn(100)
y = 2 * x + np.random.randn(100) * 0.5

correlation = np.corrcoef(x, y)[0, 1]
print(f"Correlation: {correlation:.3f}")

# ═══════════════════════════════════════════
# PRACTICAL EXAMPLE: DATA NORMALIZATION
# ═══════════════════════════════════════════

# Sample data
data = np.array([[100, 200, 300],
                 [150, 250, 350],
                 [200, 300, 400]])

# Min-Max Normalization (0-1 scale)
def min_max_normalize(data):
    min_val = data.min(axis=0)
    max_val = data.max(axis=0)
    return (data - min_val) / (max_val - min_val)

normalized = min_max_normalize(data)
print("Min-Max Normalized:")
print(normalized)

# Z-Score Normalization (standardization)
def standardize(data):
    mean = data.mean(axis=0)
    std = data.std(axis=0)
    return (data - mean) / std

standardized = standardize(data)
print("\nStandardized:")
print(standardized)

# ═══════════════════════════════════════════
# PERFORMANCE TIPS
# ═══════════════════════════════════════════

import time

# Vectorization vs loops
n = 1000000

# ❌ Slow: Python loop
start = time.time()
result = []
for i in range(n):
    result.append(i ** 2)
print(f"Loop time: {time.time() - start:.3f}s")

# ✅ Fast: NumPy vectorization
start = time.time()
arr = np.arange(n)
result = arr ** 2
print(f"NumPy time: {time.time() - start:.3f}s")

# NumPy is 10-100x faster!

# Memory views (avoid copies)
arr = np.arange(10)
view = arr[2:5]         # View (no copy)
copy = arr[2:5].copy()  # Copy

view[0] = 999           # Modifies original!
print(arr)              # [0 1 999 3 4 5 6 7 8 9]

copy[0] = 888           # Doesn't modify original
```

---

<div align="center">

## 🐼 Pandas - Data Manipulation

</div>

### DataFrames & Series Mastery 📊

```python
# ═══════════════════════════════════════════
# PANDAS FUNDAMENTALS
# ═══════════════════════════════════════════

"""
Pandas: Python Data Analysis Library
- Built on NumPy
- Two main data structures: Series & DataFrame
- SQL-like operations
- Time series functionality
"""

import pandas as pd
import numpy as np

# ═══════════════════════════════════════════
# SERIES (1D)
# ═══════════════════════════════════════════

# Create Series
s = pd.Series([1, 2, 3, 4, 5])
print(s)
# 0    1
# 1    2
# 2    3
# 3    4
# 4    5
# dtype: int64

# Series with custom index
s = pd.Series([10, 20, 30], index=['a', 'b', 'c'])
print(s)
# a    10
# b    20
# c    30
# dtype: int64

# From dictionary
data = {'a': 10, 'b': 20, 'c': 30}
s = pd.Series(data)

# Series operations
print(s + 5)            # Add 5 to all elements
print(s * 2)            # Multiply all by 2
print(s[s > 15])        # Filter

# ═══════════════════════════════════════════
# DATAFRAME (2D)
# ═══════════════════════════════════════════

# Create DataFrame from dictionary
data = {
    'name': ['Alice', 'Bob', 'Charlie', 'David'],
    'age': [25, 30, 35, 28],
    'city': ['New York', 'Paris', 'London', 'Tokyo'],
    'salary': [50000, 60000, 55000, 52000]
}

df = pd.DataFrame(data)
print(df)
#       name  age      city  salary
# 0    Alice   25  New York   50000
# 1      Bob   30     Paris   60000
# 2  Charlie   35    London   55000
# 3    David   28     Tokyo   52000

# DataFrame attributes
print(df.shape)         # (4, 4) - (rows, columns)
print(df.columns)       # Index(['name', 'age', 'city', 'salary'])
print(df.index)         # RangeIndex(start=0, stop=4, step=1)
print(df.dtypes)        # Data types of each column
print(df.info())        # Summary information
print(df.describe())    # Statistical summary

# ═══════════════════════════════════════════
# READING DATA
# ═══════════════════════════════════════════

# Read CSV
df = pd.read_csv('data.csv')
df = pd.read_csv('data.csv', sep=';')           # Custom separator
df = pd.read_csv('data.csv', encoding='utf-8') # Encoding
df = pd.read_csv('data.csv', nrows=1000)       # Read first 1000 rows

# Read Excel
df = pd.read_excel('data.xlsx')
df = pd.read_excel('data.xlsx', sheet_name='Sheet1')

# Read JSON
df = pd.read_json('data.json')
df = pd.read_json('data.json', orient='records')

# Read SQL
import sqlite3
conn = sqlite3.connect('database.db')
df = pd.read_sql('SELECT * FROM users', conn)

# Read from URL
url = 'https://example.com/data.csv'
df = pd.read_csv(url)

# Read HTML tables
url = 'https://en.wikipedia.org/wiki/List_of_countries_by_GDP_(nominal)'
tables = pd.read_html(url)
df = tables[0]  # First table

# ═══════════════════════════════════════════
# SELECTING DATA
# ═══════════════════════════════════════════

# Sample DataFrame
df = pd.DataFrame({
    'A': [1, 2, 3, 4, 5],
    'B': [10, 20, 30, 40, 50],
    'C': ['a', 'b', 'c', 'd', 'e']
})

# Select column (returns Series)
print(df['A'])
print(df.A)             # Same (if column name is valid identifier)

# Select multiple columns (returns DataFrame)
print(df[['A', 'C']])

# Select rows by index (.iloc - integer location)
print(df.iloc[0])       # First row
print(df.iloc[0:3])     # First 3 rows
print(df.iloc[[0, 2, 4]])  # Rows 0, 2, 4

# Select rows by label (.loc - label location)
print(df.loc[0])        # Row with index 0
print(df.loc[0:2])      # Rows 0 to 2 (inclusive!)

# Select specific cell
print(df.iloc[0, 1])    # Row 0, Column 1
print(df.loc[0, 'B'])   # Row 0, Column 'B'

# Boolean indexing
print(df[df['A'] > 2])
print(df[(df['A'] > 2) & (df['B'] < 50)])

# ═══════════════════════════════════════════
# MODIFYING DATA
# ═══════════════════════════════════════════

# Add column
df['D'] = df['A'] + df['B']
df['E'] = [100, 200, 300, 400, 500]

# Modify column
df['A'] = df['A'] * 2

# Rename columns
df = df.rename(columns={'A': 'Column_A', 'B': 'Column_B'})

# Drop columns
df = df.drop('E', axis=1)           # Single column
df = df.drop(['D', 'E'], axis=1)    # Multiple columns

# Drop rows
df = df.drop(0, axis=0)             # Row 0
df = df.drop([0, 2], axis=0)        # Rows 0 and 2

# Reset index
df = df.reset_index(drop=True)

# Set index
df = df.set_index('name')

# ═══════════════════════════════════════════
# SORTING
# ═══════════════════════════════════════════

# Sort by column
df_sorted = df.sort_values('age')
df_sorted = df.sort_values('age', ascending=False)

# Sort by multiple columns
df_sorted = df.sort_values(['city', 'age'])

# Sort by index
df_sorted = df.sort_index()

# ═══════════════════════════════════════════
# FILTERING
# ═══════════════════════════════════════════

# Simple filter
young = df[df['age'] < 30]

# Multiple conditions
filtered = df[(df['age'] > 25) & (df['salary'] > 50000)]

# Filter by list
cities = ['New York', 'Tokyo']
filtered = df[df['city'].isin(cities)]

# String operations
filtered = df[df['name'].str.startswith('A')]
filtered = df[df['city'].str.contains('York')]

# ═══════════════════════════════════════════
# AGGREGATIONS & GROUPING
# ═══════════════════════════════════════════

# Sample data
df = pd.DataFrame({
    'department': ['Sales', 'Sales', 'IT', 'IT', 'HR'],
    'employee': ['Alice', 'Bob', 'Charlie', 'David', 'Eve'],
    'salary': [50000, 55000, 60000, 65000, 45000],
    'years': [2, 3, 5, 4, 1]
})

# Aggregation functions
print(df['salary'].sum())
print(df['salary'].mean())
print(df['salary'].median())
print(df['salary'].std())
print(df['salary'].min())
print(df['salary'].max())
print(df['salary'].count())

# GroupBy
grouped = df.groupby('department')['salary'].mean()
print(grouped)
# department
# HR        45000.0
# IT        62500.0
# Sales     52500.0
# Name: salary, dtype: float64

# Multiple aggregations
agg_result = df.groupby('department').agg({
    'salary': ['mean', 'sum', 'count'],
    'years': ['mean', 'max']
})
print(agg_result)

# GroupBy with multiple columns
grouped = df.groupby(['department', 'years'])['salary'].mean()

# Apply custom function
def salary_category(salary):
    if salary < 50000:
        return 'Low'
    elif salary < 60000:
        return 'Medium'
    else:
        return 'High'

df['salary_category'] = df['salary'].apply(salary_category)

# ═══════════════════════════════════════════
# MERGING & JOINING
# ═══════════════════════════════════════════

# Sample DataFrames
employees = pd.DataFrame({
    'id': [1, 2, 3, 4],
    'name': ['Alice', 'Bob', 'Charlie', 'David'],
    'dept_id': [10, 20, 10, 30]
})

departments = pd.DataFrame({
    'dept_id': [10, 20, 30],
    'dept_name': ['Sales', 'IT', 'HR']
})

# Inner join (SQL JOIN)
merged = pd.merge(employees, departments, on='dept_id')
print(merged)
#    id     name  dept_id dept_name
# 0   1    Alice       10     Sales
# 1   3  Charlie       10     Sales
# 2   2      Bob       20        IT
# 3   4    David       30        HR

# Left join
merged = pd.merge(employees, departments, on='dept_id', how='left')

# Right join
merged = pd.merge(employees, departments, on='dept_id', how='right')

# Outer join
merged = pd.merge(employees, departments, on='dept_id', how='outer')

# Concatenate (stack vertically)
df1 = pd.DataFrame({'A': [1, 2], 'B': [3, 4]})
df2 = pd.DataFrame({'A': [5, 6], 'B': [7, 8]})
combined = pd.concat([df1, df2], ignore_index=True)

# Concatenate horizontally
combined = pd.concat([df1, df2], axis=1)

# ═══════════════════════════════════════════
# PIVOT TABLES
# ═══════════════════════════════════════════

# Sample data
sales = pd.DataFrame({
    'date': ['2024-01', '2024-01', '2024-02', '2024-02'],
    'product': ['A', 'B', 'A', 'B'],
    'region': ['East', 'West', 'East', 'West'],
    'sales': [100, 150, 120, 180]
})

# Pivot table
pivot = sales.pivot_table(
    values='sales',
    index='product',
    columns='region',
    aggfunc='sum'
)
print(pivot)
# region    East  West
# product
# A          220   NaN
# B          NaN   330

# Melt (unpivot)
melted = pivot.reset_index().melt(
    id_vars='product',
    var_name='region',
    value_name='sales'
)
```

---

<div align="center">

## 🧹 Data Cleaning

</div>

### Handling Missing Data & Outliers 🔧

```python
# ═══════════════════════════════════════════
# MISSING DATA HANDLING
# ═══════════════════════════════════════════

import pandas as pd
import numpy as np

# Sample data with missing values
df = pd.DataFrame({
    'name': ['Alice', 'Bob', None, 'David', 'Eve'],
    'age': [25, None, 35, 28, None],
    'city': ['NYC', 'Paris', 'London', None, 'Tokyo'],
    'salary': [50000, 60000, None, 52000, 48000]
})

print(df)
#      name   age    city   salary
# 0   Alice  25.0     NYC  50000.0
# 1     Bob   NaN   Paris  60000.0
# 2    None  35.0  London      NaN
# 3   David  28.0    None  52000.0
# 4     Eve   NaN   Tokyo  48000.0

# ═══════════════════════════════════════════
# DETECTING MISSING VALUES
# ═══════════════════════════════════════════

# Check for missing values
print(df.isnull())
print(df.isna())        # Same as isnull()

# Count missing values
print(df.isnull().sum())
# name       1
# age        2
# city       1
# salary     1
# dtype: int64

# Percentage of missing values
print(df.isnull().sum() / len(df) * 100)
# name       20.0
# age        40.0
# city       20.0
# salary     20.0
# dtype: float64

# Visualize missing data
import missingno as msno
import matplotlib.pyplot as plt

msno.matrix(df)
plt.show()

# Check rows with any missing values
print(df[df.isnull().any(axis=1)])

# Check rows with all values present
print(df[df.notnull().all(axis=1)])

# ═══════════════════════════════════════════
# HANDLING MISSING VALUES
# ═══════════════════════════════════════════

# 1. Drop rows with missing values
df_dropped_rows = df.dropna()
print(df_dropped_rows)  # No rows remain!

# Drop rows with any missing value
df_dropped = df.dropna(how='any')

# Drop rows only if all values are missing
df_dropped = df.dropna(how='all')

# Drop rows with missing values in specific columns
df_dropped = df.dropna(subset=['age', 'salary'])

# 2. Drop columns with missing values
df_dropped_cols = df.dropna(axis=1)

# 3. Fill missing values with specific value
df_filled = df.fillna(0)
df_filled = df.fillna('Unknown')

# Fill with different values per column
df_filled = df.fillna({
    'name': 'Unknown',
    'age': df['age'].mean(),
    'city': 'Unknown',
    'salary': df['salary'].median()
})

# 4. Forward fill (use previous value)
df_ffill = df.fillna(method='ffill')

# 5. Backward fill (use next value)
df_bfill = df.fillna(method='bfill')

# 6. Interpolate (for numeric data)
df['age'] = df['age'].interpolate()

# Linear interpolation
df['salary'] = df['salary'].interpolate(method='linear')

# ═══════════════════════════════════════════
# IMPUTATION STRATEGIES
# ═══════════════════════════════════════════

from sklearn.impute import SimpleImputer, KNNImputer

# Mean imputation
imputer = SimpleImputer(strategy='mean')
df[['age', 'salary']] = imputer.fit_transform(df[['age', 'salary']])

# Median imputation
imputer = SimpleImputer(strategy='median')
df[['age']] = imputer.fit_transform(df[['age']])

# Most frequent (mode) imputation
imputer = SimpleImputer(strategy='most_frequent')
df[['city']] = imputer.fit_transform(df[['city']])

# KNN Imputation (more sophisticated)
imputer = KNNImputer(n_neighbors=3)
df_numeric = df.select_dtypes(include=[np.number])
df[df_numeric.columns] = imputer.fit_transform(df_numeric)

# ═══════════════════════════════════════════
# OUTLIER DETECTION & HANDLING
# ═══════════════════════════════════════════

# Sample data with outliers
np.random.seed(42)
data = np.random.randn(1000) * 10 + 50
data = np.append(data, [150, 160, -50, -60])  # Add outliers

df = pd.DataFrame({'value': data})

# 1. Z-Score Method
from scipy import stats

z_scores = np.abs(stats.zscore(df['value']))
threshold = 3
outliers = df[z_scores > threshold]
print(f"Outliers (Z-score): {len(outliers)}")

# Remove outliers
df_no_outliers = df[z_scores <= threshold]

# 2. IQR Method (Interquartile Range)
Q1 = df['value'].quantile(0.25)
Q3 = df['value'].quantile(0.75)
IQR = Q3 - Q1

lower_bound = Q1 - 1.5 * IQR
upper_bound = Q3 + 1.5 * IQR

outliers = df[(df['value'] < lower_bound) | (df['value'] > upper_bound)]
print(f"Outliers (IQR): {len(outliers)}")

# Remove outliers
df_no_outliers = df[(df['value'] >= lower_bound) & (df['value'] <= upper_bound)]

# 3. Isolation Forest (ML-based)
from sklearn.ensemble import IsolationForest

iso_forest = IsolationForest(contamination=0.01, random_state=42)
outlier_labels = iso_forest.fit_predict(df[['value']])

df['outlier'] = outlier_labels
outliers = df[df['outlier'] == -1]
print(f"Outliers (Isolation Forest): {len(outliers)}")

# 4. Visualization
import matplotlib.pyplot as plt
import seaborn as sns

# Box plot (shows outliers)
plt.figure(figsize=(10, 6))
sns.boxplot(x=df['value'])
plt.title('Box Plot - Outlier Detection')
plt.show()

# ═══════════════════════════════════════════
# DATA TYPE CONVERSION
# ═══════════════════════════════════════════

df = pd.DataFrame({
    'int_col': ['1', '2', '3', '4'],
    'float_col': ['1.5', '2.5', '3.5', '4.5'],
    'date_col': ['2024-01-01', '2024-01-02', '2024-01-03', '2024-01-04'],
    'bool_col': ['True', 'False', 'True', 'False']
})

# Convert to numeric
df['int_col'] = pd.to_numeric(df['int_col'])
df['float_col'] = df['float_col'].astype(float)

# Convert to datetime
df['date_col'] = pd.to_datetime(df['date_col'])

# Convert to boolean
df['bool_col'] = df['bool_col'].map({'True': True, 'False': False})

# Handle errors in conversion
df['int_col'] = pd.to_numeric(df['int_col'], errors='coerce')  # Invalid → NaN

print(df.dtypes)

# ═══════════════════════════════════════════
# DUPLICATE HANDLING
# ═══════════════════════════════════════════

df = pd.DataFrame({
    'name': ['Alice', 'Bob', 'Alice', 'Charlie', 'Bob'],
    'age': [25, 30, 25, 35, 30],
    'city': ['NYC', 'Paris', 'NYC', 'London', 'Paris']
})

# Check for duplicates
print(df.duplicated())
# 0    False
# 1    False
# 2     True
# 3    False
# 4     True

# Count duplicates
print(df.duplicated().sum())  # 2

# Find duplicate rows
duplicates = df[df.duplicated()]
print(duplicates)

# Remove duplicates
df_unique = df.drop_duplicates()

# Remove duplicates based on specific columns
df_unique = df.drop_duplicates(subset=['name', 'age'])

# Keep first occurrence (default)
df_unique = df.drop_duplicates(keep='first')

# Keep last occurrence
df_unique = df.drop_duplicates(keep='last')

# Remove all duplicates
df_unique = df.drop_duplicates(keep=False)

# ═══════════════════════════════════════════
# STRING CLEANING
# ═══════════════════════════════════════════

df = pd.DataFrame({
    'text': [
        '  Hello World  ',
        'UPPERCASE',
        'Mixed Case Text',
        'email@example.com',
        '123-456-7890'
    ]
})

# Strip whitespace
df['text_clean'] = df['text'].str.strip()

# Lowercase
df['text_lower'] = df['text'].str.lower()

# Uppercase
df['text_upper'] = df['text'].str.upper()

# Title case
df['text_title'] = df['text'].str.title()

# Remove specific characters
df['text_clean'] = df['text'].str.replace('-', '')

# Extract patterns
df['has_email'] = df['text'].str.contains('@')

# Extract numbers
df['numbers'] = df['text'].str.extract(r'(\d+)')

# Split strings
df['words'] = df['text'].str.split()

# ═══════════════════════════════════════════
# COMPLETE CLEANING PIPELINE
# ═══════════════════════════════════════════

def clean_dataframe(df):
    """
    Complete data cleaning pipeline
    """
    # 1. Remove duplicate rows
    df = df.drop_duplicates()

    # 2. Handle missing values
    # For numeric columns: fill with median
    numeric_cols = df.select_dtypes(include=[np.number]).columns
    for col in numeric_cols:
        df[col].fillna(df[col].median(), inplace=True)

    # For categorical columns: fill with mode
    categorical_cols = df.select_dtypes(include=['object']).columns
    for col in categorical_cols:
        df[col].fillna(df[col].mode()[0], inplace=True)

    # 3. Remove outliers (IQR method for numeric columns)
    for col in numeric_cols:
        Q1 = df[col].quantile(0.25)
        Q3 = df[col].quantile(0.75)
        IQR = Q3 - Q1
        lower_bound = Q1 - 1.5 * IQR
        upper_bound = Q3 + 1.5 * IQR
        df = df[(df[col] >= lower_bound) & (df[col] <= upper_bound)]

    # 4. Clean string columns
    for col in categorical_cols:
        df[col] = df[col].str.strip()
        df[col] = df[col].str.lower()

    # 5. Reset index
    df = df.reset_index(drop=True)

    return df

# Usage
# df_clean = clean_dataframe(df)
```

---

<div align="center">

## 🔍 Exploratory Data Analysis

</div>

### Understanding Your Data 📈

```python
# ═══════════════════════════════════════════
# EDA WORKFLOW
# ═══════════════════════════════════════════

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Load sample dataset (Titanic)
df = pd.read_csv('https://raw.githubusercontent.com/datasciencedojo/datasets/master/titanic.csv')

# ═══════════════════════════════════════════
# INITIAL DATA EXPLORATION
# ═══════════════════════════════════════════

# First look
print(df.head())        # First 5 rows
print(df.tail())        # Last 5 rows
print(df.sample(10))    # Random 10 rows

# Dataset shape
print(f"Rows: {df.shape[0]}, Columns: {df.shape[1]}")

# Column names
print(df.columns.tolist())

# Data types
print(df.dtypes)

# Detailed info
print(df.info())

# Memory usage
print(df.memory_usage(deep=True))

# ═══════════════════════════════════════════
# STATISTICAL SUMMARY
# ═══════════════════════════════════════════

# Describe numeric columns
print(df.describe())
#        PassengerId    Survived      Pclass         Age       SibSp       Parch        Fare
# count   891.000000  891.000000  891.000000  714.000000  891.000000  891.000000  891.000000
# mean    446.000000    0.383838    2.308642   29.699118    0.523008    0.381594   32.204208
# std     257.353842    0.486592    0.836071   14.526497    1.102743    0.806057   49.693429
# min       1.000000    0.000000    1.000000    0.420000    0.000000    0.000000    0.000000
# 25%     223.500000    0.000000    2.000000   20.125000    0.000000    0.000000    7.910400
# 50%     446.000000    0.000000    3.000000   28.000000    0.000000    0.000000   14.454200
# 75%     668.500000    1.000000    3.000000   38.000000    1.000000    0.000000   31.000000
# max     891.000000    1.000000    3.000000   80.000000    8.000000    6.000000  512.329200

# Describe all columns (including categorical)
print(df.describe(include='all'))

# Custom percentiles
print(df.describe(percentiles=[0.1, 0.5, 0.9]))

# Specific column statistics
print(df['Age'].mean())
print(df['Age'].median())
print(df['Age'].mode())
print(df['Age'].std())
print(df['Age'].var())
print(df['Age'].min())
print(df['Age'].max())
print(df['Age'].quantile([0.25, 0.5, 0.75]))

# ═══════════════════════════════════════════
# UNIVARIATE ANALYSIS
# ═══════════════════════════════════════════

# Numeric variable - Age
plt.figure(figsize=(15, 5))

# Histogram
plt.subplot(1, 3, 1)
plt.hist(df['Age'].dropna(), bins=30, edgecolor='black')
plt.title('Age Distribution')
plt.xlabel('Age')
plt.ylabel('Frequency')

# Box plot
plt.subplot(1, 3, 2)
plt.boxplot(df['Age'].dropna())
plt.title('Age Box Plot')
plt.ylabel('Age')

# Density plot
plt.subplot(1, 3, 3)
df['Age'].plot(kind='density')
plt.title('Age Density Plot')
plt.xlabel('Age')

plt.tight_layout()
plt.show()

# Categorical variable - Survived
print(df['Survived'].value_counts())
# 0    549
# 1    342
# Name: Survived, dtype: int64

print(df['Survived'].value_counts(normalize=True))
# 0    0.616162
# 1    0.383838
# Name: Survived, dtype: float64

# Visualize
plt.figure(figsize=(12, 4))

# Bar plot
plt.subplot(1, 2, 1)
df['Survived'].value_counts().plot(kind='bar')
plt.title('Survival Count')
plt.xlabel('Survived')
plt.ylabel('Count')

# Pie chart
plt.subplot(1, 2, 2)
df['Survived'].value_counts().plot(kind='pie', autopct='%1.1f%%')
plt.title('Survival Percentage')
plt.ylabel('')

plt.tight_layout()
plt.show()

# ═══════════════════════════════════════════
# BIVARIATE ANALYSIS
# ═══════════════════════════════════════════

# Numeric vs Numeric - Correlation
correlation = df[['Age', 'Fare']].corr()
print(correlation)

# Scatter plot
plt.figure(figsize=(8, 6))
plt.scatter(df['Age'], df['Fare'], alpha=0.5)
plt.title('Age vs Fare')
plt.xlabel('Age')
plt.ylabel('Fare')
plt.show()

# Categorical vs Numeric
# Survival by Age
plt.figure(figsize=(10, 6))
df.boxplot(column='Age', by='Survived')
plt.title('Age Distribution by Survival')
plt.suptitle('')  # Remove default title
plt.show()

# Group statistics
print(df.groupby('Survived')['Age'].describe())

# Categorical vs Categorical
# Cross-tabulation
ct = pd.crosstab(df['Pclass'], df['Survived'])
print(ct)
#          0    1
# Pclass
# 1       80  136
# 2       97   87
# 3      372  119

# Normalized
ct_norm = pd.crosstab(df['Pclass'], df['Survived'], normalize='index')
print(ct_norm)

# Visualize
ct.plot(kind='bar', stacked=True)
plt.title('Survival by Passenger Class')
plt.xlabel('Passenger Class')
plt.ylabel('Count')
plt.legend(['Died', 'Survived'])
plt.show()

# ═══════════════════════════════════════════
# MULTIVARIATE ANALYSIS
# ═══════════════════════════════════════════

# Correlation matrix
numeric_df = df.select_dtypes(include=[np.number])
correlation_matrix = numeric_df.corr()

# Heatmap
plt.figure(figsize=(10, 8))
sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm', center=0)
plt.title('Correlation Heatmap')
plt.show()

# Pairplot (scatter matrix)
sns.pairplot(df[['Survived', 'Pclass', 'Age', 'Fare']], hue='Survived')
plt.show()

# ═══════════════════════════════════════════
# ADVANCED EDA TECHNIQUES
# ═══════════════════════════════════════════

# 1. Distribution Analysis
from scipy import stats

# Check normality
statistic, p_value = stats.normaltest(df['Age'].dropna())
print(f"Normality test p-value: {p_value}")
if p_value < 0.05:
    print("Data is NOT normally distributed")
else:
    print("Data is normally distributed")

# Q-Q plot for normality
stats.probplot(df['Age'].dropna(), dist="norm", plot=plt)
plt.title('Q-Q Plot - Age')
plt.show()

# 2. Skewness and Kurtosis
print(f"Skewness: {df['Fare'].skew()}")
print(f"Kurtosis: {df['Fare'].kurtosis()}")

# 3. Value Counts with Percentage
def value_counts_with_percentage(df, column):
    counts = df[column].value_counts()
    percentages = df[column].value_counts(normalize=True) * 100
    result = pd.DataFrame({
        'Count': counts,
        'Percentage': percentages
    })
    return result

print(value_counts_with_percentage(df, 'Pclass'))

# 4. Unique Values Analysis
def analyze_unique_values(df):
    result = pd.DataFrame({
        'Column': df.columns,
        'Unique_Count': [df[col].nunique() for col in df.columns],
        'Unique_Percentage': [df[col].nunique() / len(df) * 100 for col in df.columns],
        'Missing_Count': [df[col].isnull().sum() for col in df.columns],
        'Missing_Percentage': [df[col].isnull().sum() / len(df) * 100 for col in df.columns]
    })
    return result.sort_values('Unique_Count', ascending=False)

print(analyze_unique_values(df))

# ═══════════════════════════════════════════
# COMPLETE EDA REPORT FUNCTION
# ═══════════════════════════════════════════

def generate_eda_report(df, target=None):
    """
    Generate comprehensive EDA report
    """
    print("=" * 80)
    print("EXPLORATORY DATA ANALYSIS REPORT")
    print("=" * 80)

    # 1. Dataset Overview
    print("\n📊 DATASET OVERVIEW")
    print("-" * 80)
    print(f"Rows: {df.shape[0]}")
    print(f"Columns: {df.shape[1]}")
    print(f"Memory Usage: {df.memory_usage(deep=True).sum() / 1024**2:.2f} MB")

    # 2. Data Types
    print("\n📋 DATA TYPES")
    print("-" * 80)
    print(df.dtypes.value_counts())

    # 3. Missing Values
    print("\n❌ MISSING VALUES")
    print("-" * 80)
    missing = df.isnull().sum()
    missing_pct = (missing / len(df)) * 100
    missing_df = pd.DataFrame({
        'Missing_Count': missing,
        'Percentage': missing_pct
    })
    print(missing_df[missing_df['Missing_Count'] > 0].sort_values('Missing_Count', ascending=False))

    # 4. Duplicate Rows
    print("\n🔄 DUPLICATE ROWS")
    print("-" * 80)
    duplicates = df.duplicated().sum()
    print(f"Duplicate rows: {duplicates} ({duplicates/len(df)*100:.2f}%)")

    # 5. Numeric Columns Summary
    print("\n🔢 NUMERIC COLUMNS SUMMARY")
    print("-" * 80)
    numeric_cols = df.select_dtypes(include=[np.number]).columns
    print(df[numeric_cols].describe())

    # 6. Categorical Columns Summary
    print("\n📝 CATEGORICAL COLUMNS SUMMARY")
    print("-" * 80)
    categorical_cols = df.select_dtypes(include=['object']).columns
    for col in categorical_cols:
        print(f"\n{col}:")
        print(df[col].value_counts().head())

    # 7. Correlation Analysis (if target specified)
    if target and target in df.columns:
        print(f"\n🎯 CORRELATION WITH TARGET ({target})")
        print("-" * 80)
        correlations = df[numeric_cols].corr()[target].sort_values(ascending=False)
        print(correlations)

    # 8. Outliers Detection
    print("\n⚠️  OUTLIERS (IQR METHOD)")
    print("-" * 80)
    for col in numeric_cols:
        Q1 = df[col].quantile(0.25)
        Q3 = df[col].quantile(0.75)
        IQR = Q3 - Q1
        outliers = df[(df[col] < (Q1 - 1.5 * IQR)) | (df[col] > (Q3 + 1.5 * IQR))][col]
        if len(outliers) > 0:
            print(f"{col}: {len(outliers)} outliers ({len(outliers)/len(df)*100:.2f}%)")

    print("\n" + "=" * 80)
    print("END OF REPORT")
    print("=" * 80)

# Usage
# generate_eda_report(df, target='Survived')
```

---

<div align="center">

## 📊 Data Visualization

</div>

### Creating Insightful Visualizations 📈

```python
# ═══════════════════════════════════════════
# MATPLOTLIB BASICS
# ═══════════════════════════════════════════

import matplotlib.pyplot as plt
import numpy as np

# Basic plot
x = np.linspace(0, 10, 100)
y = np.sin(x)

plt.figure(figsize=(10, 6))
plt.plot(x, y)
plt.title('Sine Wave')
plt.xlabel('X axis')
plt.ylabel('Y axis')
plt.grid(True)
plt.show()

# Multiple plots
plt.figure(figsize=(12, 5))

plt.subplot(1, 2, 1)
plt.plot(x, np.sin(x), label='sin(x)')
plt.plot(x, np.cos(x), label='cos(x)')
plt.title('Trigonometric Functions')
plt.legend()

plt.subplot(1, 2, 2)
plt.plot(x, x**2, 'r--', label='x²')
plt.plot(x, x**3, 'g:', label='x³')
plt.title('Polynomial Functions')
plt.legend()

plt.tight_layout()
plt.show()

# ═══════════════════════════════════════════
# COMMON PLOT TYPES
# ═══════════════════════════════════════════

# Sample data
np.random.seed(42)
data1 = np.random.randn(1000)
data2 = np.random.randn(1000) * 2 + 1

fig, axes = plt.subplots(2, 3, figsize=(15, 10))

# 1. Histogram
axes[0, 0].hist(data1, bins=30, edgecolor='black', alpha=0.7)
axes[0, 0].set_title('Histogram')

# 2. Scatter Plot
x = np.random.randn(100)
y = 2*x + np.random.randn(100)
axes[0, 1].scatter(x, y, alpha=0.5)
axes[0, 1].set_title('Scatter Plot')

# 3. Line Plot
x = np.linspace(0, 10, 50)
axes[0, 2].plot(x, np.sin(x), marker='o')
axes[0, 2].set_title('Line Plot')

# 4. Bar Chart
categories = ['A', 'B', 'C', 'D']
values = [23, 45, 56, 78]
axes[1, 0].bar(categories, values)
axes[1, 0].set_title('Bar Chart')

# 5. Box Plot
axes[1, 1].boxplot([data1, data2], labels=['Group 1', 'Group 2'])
axes[1, 1].set_title('Box Plot')

# 6. Pie Chart
sizes = [30, 25, 20, 25]
axes[1, 2].pie(sizes, labels=categories, autopct='%1.1f%%')
axes[1, 2].set_title('Pie Chart')

plt.tight_layout()
plt.show()

# ═══════════════════════════════════════════
# SEABORN - STATISTICAL VISUALIZATION
# ═══════════════════════════════════════════

import seaborn as sns
import pandas as pd

# Load sample dataset
tips = sns.load_dataset('tips')

# Set style
sns.set_style('whitegrid')
sns.set_palette('husl')

# Distribution plots
fig, axes = plt.subplots(2, 2, figsize=(14, 10))

# 1. Histogram with KDE
sns.histplot(data=tips, x='total_bill', kde=True, ax=axes[0, 0])
axes[0, 0].set_title('Distribution of Total Bill')

# 2. Box plot by category
sns.boxplot(data=tips, x='day', y='total_bill', ax=axes[0, 1])
axes[0, 1].set_title('Total Bill by Day')

# 3. Violin plot
sns.violinplot(data=tips, x='day', y='total_bill', ax=axes[1, 0])
axes[1, 0].set_title('Total Bill Distribution by Day')

# 4. Strip plot
sns.stripplot(data=tips, x='day', y='total_bill', ax=axes[1, 1])
axes[1, 1].set_title('Individual Points by Day')

plt.tight_layout()
plt.show()

# Relationship plots
fig, axes = plt.subplots(1, 3, figsize=(18, 5))

# 1. Scatter plot with regression
sns.regplot(data=tips, x='total_bill', y='tip', ax=axes[0])
axes[0].set_title('Bill vs Tip (with regression)')

# 2. Scatter plot with hue
sns.scatterplot(data=tips, x='total_bill', y='tip', hue='time', ax=axes[1])
axes[1].set_title('Bill vs Tip by Time')

# 3. Line plot with confidence interval
flights = sns.load_dataset('flights')
sns.lineplot(data=flights, x='year', y='passengers', ax=axes[2])
axes[2].set_title('Passengers Over Time')

plt.tight_layout()
plt.show()

# Categorical plots
fig, axes = plt.subplots(1, 3, figsize=(18, 5))

# 1. Count plot
sns.countplot(data=tips, x='day', ax=axes[0])
axes[0].set_title('Count by Day')

# 2. Bar plot (with aggregation)
sns.barplot(data=tips, x='day', y='total_bill', estimator=np.mean, ax=axes[1])
axes[1].set_title('Average Bill by Day')

# 3. Point plot
sns.pointplot(data=tips, x='day', y='total_bill', hue='sex', ax=axes[2])
axes[2].set_title('Bill by Day and Gender')

plt.tight_layout()
plt.show()

# Heatmap
# Correlation matrix
df = tips.select_dtypes(include=[np.number])
correlation = df.corr()

plt.figure(figsize=(8, 6))
sns.heatmap(correlation, annot=True, cmap='coolwarm', center=0,
            square=True, linewidths=1)
plt.title('Correlation Heatmap')
plt.show()

# Pairplot
sns.pairplot(tips, hue='time', corner=True)
plt.show()

# ═══════════════════════════════════════════
# PLOTLY - INTERACTIVE VISUALIZATIONS
# ═══════════════════════════════════════════

import plotly.express as px
import plotly.graph_objects as go

# Sample data
df = px.data.gapminder()

# 1. Interactive scatter plot
fig = px.scatter(df, x='gdpPercap', y='lifeExp',
                 animation_frame='year',
                 animation_group='country',
                 size='pop', color='continent',
                 hover_name='country',
                 log_x=True, size_max=55,
                 range_x=[100, 100000], range_y=[25, 90])
fig.update_layout(title='Life Expectancy vs GDP per Capita')
# fig.show()

# 2. Interactive line plot
df_filtered = df[df['country'].isin(['United States', 'China', 'India'])]
fig = px.line(df_filtered, x='year', y='lifeExp', color='country',
              title='Life Expectancy Over Time')
# fig.show()

# 3. Interactive bar chart
df_2007 = df[df['year'] == 2007].nlargest(10, 'pop')
fig = px.bar(df_2007, x='country', y='pop',
             title='Top 10 Countries by Population (2007)')
# fig.show()

# 4. Choropleth map
fig = px.choropleth(df, locations='iso_alpha', color='lifeExp',
                    hover_name='country', animation_frame='year',
                    color_continuous_scale=px.colors.sequential.Plasma,
                    title='Life Expectancy Around the World')
# fig.show()

# 5. 3D Scatter plot
iris = px.data.iris()
fig = px.scatter_3d(iris, x='sepal_length', y='sepal_width', z='petal_width',
                    color='species', size='petal_length',
                    title='Iris Dataset - 3D Visualization')
# fig.show()

# ═══════════════════════════════════════════
# ADVANCED VISUALIZATION TECHNIQUES
# ═══════════════════════════════════════════

# 1. Subplots with Matplotlib
fig = plt.figure(figsize=(15, 10))
gs = fig.add_gridspec(3, 3, hspace=0.3, wspace=0.3)

# Large plot
ax1 = fig.add_subplot(gs[0:2, 0:2])
x = np.linspace(0, 10, 1000)
ax1.plot(x, np.sin(x))
ax1.set_title('Large Plot')

# Small plots
ax2 = fig.add_subplot(gs[0, 2])
ax2.hist(np.random.randn(1000), bins=30)
ax2.set_title('Histogram')

ax3 = fig.add_subplot(gs[1, 2])
ax3.scatter(np.random.rand(100), np.random.rand(100))
ax3.set_title('Scatter')

ax4 = fig.add_subplot(gs[2, :])
ax4.plot(x, np.cos(x))
ax4.set_title('Bottom Plot')

plt.show()

# 2. Dual axis plot
fig, ax1 = plt.subplots(figsize=(10, 6))

x = np.arange(10)
y1 = np.random.randint(10, 100, 10)
y2 = np.random.randint(1000, 5000, 10)

# First y-axis
ax1.plot(x, y1, 'b-', marker='o', label='Y1')
ax1.set_xlabel('X axis')
ax1.set_ylabel('Y1 (blue)', color='b')
ax1.tick_params(axis='y', labelcolor='b')

# Second y-axis
ax2 = ax1.twinx()
ax2.plot(x, y2, 'r-', marker='s', label='Y2')
ax2.set_ylabel('Y2 (red)', color='r')
ax2.tick_params(axis='y', labelcolor='r')

plt.title('Dual Axis Plot')
fig.tight_layout()
plt.show()

# 3. Annotated plot
fig, ax = plt.subplots(figsize=(10, 6))

x = np.linspace(0, 10, 100)
y = np.sin(x)

ax.plot(x, y)
ax.set_title('Annotated Sine Wave')

# Add annotations
ax.annotate('Maximum', xy=(np.pi/2, 1), xytext=(np.pi/2 + 1, 1.2),
            arrowprops=dict(facecolor='red', shrink=0.05),
            fontsize=12)

ax.annotate('Minimum', xy=(3*np.pi/2, -1), xytext=(3*np.pi/2 + 1, -1.2),
            arrowprops=dict(facecolor='blue', shrink=0.05),
            fontsize=12)

ax.axhline(y=0, color='k', linestyle='--', alpha=0.3)
ax.grid(True, alpha=0.3)
plt.show()

# ═══════════════════════════════════════════
# STYLING & CUSTOMIZATION
# ═══════════════════════════════════════════

# Available styles
print(plt.style.available)

# Use a style
plt.style.use('seaborn-v0_8-darkgrid')

# Custom colors
colors = ['#FF6B6B', '#4ECDC4', '#45B7D1', '#FFA07A', '#98D8C8']

# Custom plot
fig, ax = plt.subplots(figsize=(10, 6))

for i, color in enumerate(colors):
    x = np.linspace(0, 10, 100)
    y = np.sin(x + i)
    ax.plot(x, y, color=color, linewidth=2, label=f'Wave {i+1}')

ax.set_title('Custom Styled Plot', fontsize=16, fontweight='bold')
ax.set_xlabel('X axis', fontsize=12)
ax.set_ylabel('Y axis', fontsize=12)
ax.legend(loc='upper right', frameon=True, shadow=True)
ax.grid(True, alpha=0.3, linestyle='--')

plt.tight_layout()
plt.show()

# Save figure
plt.savefig('plot.png', dpi=300, bbox_inches='tight')
plt.savefig('plot.pdf', dpi=300, bbox_inches='tight')
```

---

<div align="center">

## 📈 Statistical Analysis

</div>

### Hypothesis Testing & Statistical Methods 📊

```python
# ═══════════════════════════════════════════
# DESCRIPTIVE STATISTICS
# ═══════════════════════════════════════════

import numpy as np
import pandas as pd
from scipy import stats
import seaborn as sns
import matplotlib.pyplot as plt

# Sample data
np.random.seed(42)
data = np.random.randn(1000) * 15 + 100

# Measures of central tendency
mean = np.mean(data)
median = np.median(data)
mode_result = stats.mode(data, keepdims=True)
mode = mode_result.mode[0]

print(f"Mean: {mean:.2f}")
print(f"Median: {median:.2f}")
print(f"Mode: {mode:.2f}")

# Measures of dispersion
variance = np.var(data)
std_dev = np.std(data)
range_val = np.ptp(data)
iqr = stats.iqr(data)

print(f"\nVariance: {variance:.2f}")
print(f"Standard Deviation: {std_dev:.2f}")
print(f"Range: {range_val:.2f}")
print(f"IQR: {iqr:.2f}")

# Measures of shape
skewness = stats.skew(data)
kurtosis = stats.kurtosis(data)

print(f"\nSkewness: {skewness:.2f}")
print(f"Kurtosis: {kurtosis:.2f}")

# Percentiles
percentiles = [25, 50, 75, 90, 95, 99]
for p in percentiles:
    value = np.percentile(data, p)
    print(f"{p}th percentile: {value:.2f}")

# ═══════════════════════════════════════════
# PROBABILITY DISTRIBUTIONS
# ═══════════════════════════════════════════

# 1. Normal Distribution
mean, std = 0, 1
x = np.linspace(-4, 4, 100)
pdf = stats.norm.pdf(x, mean, std)
cdf = stats.norm.cdf(x, mean, std)

fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(14, 5))

ax1.plot(x, pdf)
ax1.set_title('Normal Distribution - PDF')
ax1.set_xlabel('Value')
ax1.set_ylabel('Probability Density')

ax2.plot(x, cdf)
ax2.set_title('Normal Distribution - CDF')
ax2.set_xlabel('Value')
ax2.set_ylabel('Cumulative Probability')

plt.tight_layout()
plt.show()

# Generate random samples
samples = stats.norm.rvs(loc=100, scale=15, size=1000)

# 2. Other common distributions
fig, axes = plt.subplots(2, 3, figsize=(15, 10))

# Binomial
n, p = 20, 0.5
x = np.arange(0, n+1)
axes[0, 0].bar(x, stats.binom.pmf(x, n, p))
axes[0, 0].set_title('Binomial Distribution')

# Poisson
mu = 5
x = np.arange(0, 20)
axes[0, 1].bar(x, stats.poisson.pmf(x, mu))
axes[0, 1].set_title('Poisson Distribution')

# Exponential
x = np.linspace(0, 5, 100)
axes[0, 2].plot(x, stats.expon.pdf(x))
axes[0, 2].set_title('Exponential Distribution')

# Uniform
x = np.linspace(0, 1, 100)
axes[1, 0].plot(x, stats.uniform.pdf(x))
axes[1, 0].set_title('Uniform Distribution')

# Chi-square
x = np.linspace(0, 20, 100)
for df in [1, 2, 5, 10]:
    axes[1, 1].plot(x, stats.chi2.pdf(x, df), label=f'df={df}')
axes[1, 1].set_title('Chi-Square Distribution')
axes[1, 1].legend()

# Student's t
x = np.linspace(-4, 4, 100)
for df in [1, 5, 30]:
    axes[1, 2].plot(x, stats.t.pdf(x, df), label=f'df={df}')
axes[1, 2].plot(x, stats.norm.pdf(x), 'k--', label='Normal')
axes[1, 2].set_title("Student's t Distribution")
axes[1, 2].legend()

plt.tight_layout()
plt.show()

# ═══════════════════════════════════════════
# HYPOTHESIS TESTING
# ═══════════════════════════════════════════

# 1. One-Sample t-test
# H0: population mean = 100
# H1: population mean ≠ 100
data = np.random.randn(30) * 10 + 105

t_statistic, p_value = stats.ttest_1samp(data, 100)
print(f"One-sample t-test:")
print(f"t-statistic: {t_statistic:.4f}")
print(f"p-value: {p_value:.4f}")

alpha = 0.05
if p_value < alpha:
    print(f"Reject H0: Mean is significantly different from 100")
else:
    print(f"Fail to reject H0: Mean is not significantly different from 100")

# 2. Two-Sample t-test (Independent)
# Compare two groups
group1 = np.random.randn(30) * 10 + 100
group2 = np.random.randn(30) * 10 + 105

t_statistic, p_value = stats.ttest_ind(group1, group2)
print(f"\nTwo-sample t-test (independent):")
print(f"t-statistic: {t_statistic:.4f}")
print(f"p-value: {p_value:.4f}")

# 3. Paired t-test
# Before-after comparison
before = np.random.randn(30) * 10 + 100
after = before + np.random.randn(30) * 5 + 5

t_statistic, p_value = stats.ttest_rel(before, after)
print(f"\nPaired t-test:")
print(f"t-statistic: {t_statistic:.4f}")
print(f"p-value: {p_value:.4f}")

# 4. Chi-Square Test (Independence)
# Contingency table
observed = np.array([[10, 15, 20],
                     [20, 25, 15]])

chi2, p_value, dof, expected = stats.chi2_contingency(observed)
print(f"\nChi-Square test:")
print(f"Chi-square statistic: {chi2:.4f}")
print(f"p-value: {p_value:.4f}")
print(f"Degrees of freedom: {dof}")

# 5. ANOVA (Analysis of Variance)
# Compare multiple groups
group1 = np.random.randn(30) * 10 + 100
group2 = np.random.randn(30) * 10 + 105
group3 = np.random.randn(30) * 10 + 110

f_statistic, p_value = stats.f_oneway(group1, group2, group3)
print(f"\nOne-way ANOVA:")
print(f"F-statistic: {f_statistic:.4f}")
print(f"p-value: {p_value:.4f}")

# 6. Mann-Whitney U test (Non-parametric)
# When data is not normally distributed
group1 = np.random.exponential(2, 30)
group2 = np.random.exponential(3, 30)

u_statistic, p_value = stats.mannwhitneyu(group1, group2)
print(f"\nMann-Whitney U test:")
print(f"U-statistic: {u_statistic:.4f}")
print(f"p-value: {p_value:.4f}")

# 7. Shapiro-Wilk test (Normality)
data = np.random.randn(100)
statistic, p_value = stats.shapiro(data)
print(f"\nShapiro-Wilk test (Normality):")
print(f"Statistic: {statistic:.4f}")
print(f"p-value: {p_value:.4f}")

if p_value > 0.05:
    print("Data appears to be normally distributed")
else:
    print("Data does not appear to be normally distributed")

# ═══════════════════════════════════════════
# CORRELATION & REGRESSION
# ═══════════════════════════════════════════

# Generate correlated data
np.random.seed(42)
x = np.random.randn(100)
y = 2 * x + np.random.randn(100) * 0.5

# 1. Pearson correlation
r, p_value = stats.pearsonr(x, y)
print(f"\nPearson correlation:")
print(f"r = {r:.4f}")
print(f"p-value = {p_value:.4f}")

# 2. Spearman correlation (rank-based)
rho, p_value = stats.spearmanr(x, y)
print(f"\nSpearman correlation:")
print(f"rho = {rho:.4f}")
print(f"p-value = {p_value:.4f}")

# 3. Simple Linear Regression
from scipy.stats import linregress

slope, intercept, r_value, p_value, std_err = linregress(x, y)
print(f"\nLinear Regression:")
print(f"Slope: {slope:.4f}")
print(f"Intercept: {intercept:.4f}")
print(f"R-squared: {r_value**2:.4f}")
print(f"p-value: {p_value:.4f}")

# Plot
plt.figure(figsize=(10, 6))
plt.scatter(x, y, alpha=0.5, label='Data')
plt.plot(x, slope*x + intercept, 'r-', label=f'y = {slope:.2f}x + {intercept:.2f}')
plt.xlabel('X')
plt.ylabel('Y')
plt.title(f'Linear Regression (R² = {r_value**2:.4f})')
plt.legend()
plt.grid(True, alpha=0.3)
plt.show()

# ═══════════════════════════════════════════
# CONFIDENCE INTERVALS
# ═══════════════════════════════════════════

def confidence_interval(data, confidence=0.95):
    """
    Calculate confidence interval for mean
    """
    n = len(data)
    mean = np.mean(data)
    sem = stats.sem(data)  # Standard error of mean
    margin = sem * stats.t.ppf((1 + confidence) / 2, n - 1)
    return mean - margin, mean + margin

data = np.random.randn(100) * 10 + 100
lower, upper = confidence_interval(data, 0.95)

print(f"\n95% Confidence Interval:")
print(f"Mean: {np.mean(data):.2f}")
print(f"CI: [{lower:.2f}, {upper:.2f}]")

# ═══════════════════════════════════════════
# BOOTSTRAP SAMPLING
# ═══════════════════════════════════════════

def bootstrap_confidence_interval(data, num_bootstrap=10000, confidence=0.95):
    """
    Bootstrap confidence interval for median
    """
    bootstrap_medians = []

    for _ in range(num_bootstrap):
        sample = np.random.choice(data, size=len(data), replace=True)
        bootstrap_medians.append(np.median(sample))

    alpha = 1 - confidence
    lower = np.percentile(bootstrap_medians, alpha/2 * 100)
    upper = np.percentile(bootstrap_medians, (1 - alpha/2) * 100)

    return lower, upper

data = np.random.exponential(2, 100)
lower, upper = bootstrap_confidence_interval(data)

print(f"\nBootstrap 95% CI for Median:")
print(f"Median: {np.median(data):.2f}")
print(f"CI: [{lower:.2f}, {upper:.2f}]")
```

---

<div align="center">

## 🔧 Feature Engineering

</div>

### Creating Better Features 🛠️

```python
# ═══════════════════════════════════════════
# FEATURE ENGINEERING TECHNIQUES
# ═══════════════════════════════════════════

import pandas as pd
import numpy as np
from sklearn.preprocessing import (StandardScaler, MinMaxScaler,
                                   LabelEncoder, OneHotEncoder)
from sklearn.feature_selection import SelectKBest, chi2, f_classif

# Sample dataset
df = pd.DataFrame({
    'age': [25, 30, 35, 40, 45, 50, 55, 60],
    'income': [30000, 50000, 60000, 80000, 90000, 100000, 110000, 120000],
    'city': ['NYC', 'LA', 'NYC', 'SF', 'LA', 'NYC', 'SF', 'LA'],
    'education': ['Bachelor', 'Master', 'PhD', 'Bachelor', 'Master',
                  'PhD', 'Bachelor', 'Master'],
    'experience': [2, 5, 10, 15, 20, 25, 30, 35],
    'purchased': [0, 0, 1, 1, 1, 1, 1, 1]
})

# ═══════════════════════════════════════════
# 1. NUMERICAL TRANSFORMATIONS
# ═══════════════════════════════════════════

# Binning (Discretization)
df['age_group'] = pd.cut(df['age'], bins=[0, 30, 50, 100],
                         labels=['Young', 'Middle', 'Senior'])

# Log transformation (for skewed data)
df['log_income'] = np.log1p(df['income'])

# Square root transformation
df['sqrt_experience'] = np.sqrt(df['experience'])

# Polynomial features
df['age_squared'] = df['age'] ** 2
df['age_cubed'] = df['age'] ** 3

# Interaction features
df['age_income_interaction'] = df['age'] * df['income']

# Ratio features
df['income_per_year_exp'] = df['income'] / (df['experience'] + 1)

print(df[['age', 'age_group', 'log_income', 'age_income_interaction']].head())

# ═══════════════════════════════════════════
# 2. SCALING & NORMALIZATION
# ═══════════════════════════════════════════

# StandardScaler (z-score normalization)
scaler = StandardScaler()
df['age_scaled'] = scaler.fit_transform(df[['age']])
df['income_scaled'] = scaler.fit_transform(df[['income']])

# MinMaxScaler (0-1 normalization)
min_max_scaler = MinMaxScaler()
df['age_normalized'] = min_max_scaler.fit_transform(df[['age']])

# Robust Scaler (resistant to outliers)
from sklearn.preprocessing import RobustScaler
robust_scaler = RobustScaler()
df['income_robust'] = robust_scaler.fit_transform(df[['income']])

print(f"Original age: {df['age'].values}")
print(f"Scaled age: {df['age_scaled'].values}")
print(f"Normalized age: {df['age_normalized'].values}")

# ═══════════════════════════════════════════
# 3. ENCODING CATEGORICAL VARIABLES
# ═══════════════════════════════════════════

# Label Encoding (ordinal)
label_encoder = LabelEncoder()
df['education_encoded'] = label_encoder.fit_transform(df['education'])

print("Education mapping:")
for i, label in enumerate(label_encoder.classes_):
    print(f"{label}: {i}")

# One-Hot Encoding (nominal)
df_onehot = pd.get_dummies(df, columns=['city'], prefix='city')
print("\nOne-hot encoded cities:")
print(df_onehot[['city_LA', 'city_NYC', 'city_SF']].head())

# Manual one-hot encoding (more control)
for city in df['city'].unique():
    df[f'is_{city}'] = (df['city'] == city).astype(int)

# Ordinal Encoding (with custom order)
from sklearn.preprocessing import OrdinalEncoder

education_order = ['Bachelor', 'Master', 'PhD']
ordinal_encoder = OrdinalEncoder(categories=[education_order])
df['education_ordinal'] = ordinal_encoder.fit_transform(df[['education']])

# Target Encoding (mean encoding)
def target_encode(df, column, target):
    """
    Encode categorical variable with target mean
    """
    means = df.groupby(column)[target].mean()
    df[f'{column}_target_enc'] = df[column].map(means)
    return df

df = target_encode(df, 'city', 'purchased')
print("\nTarget encoding for city:")
print(df[['city', 'city_target_enc', 'purchased']].head())

# ═══════════════════════════════════════════
# 4. DATETIME FEATURES
# ═══════════════════════════════════════════

# Sample datetime data
df_dates = pd.DataFrame({
    'date': pd.date_range('2024-01-01', periods=100, freq='D'),
    'sales': np.random.randint(100, 1000, 100)
})

# Extract datetime components
df_dates['year'] = df_dates['date'].dt.year
df_dates['month'] = df_dates['date'].dt.month
df_dates['day'] = df_dates['date'].dt.day
df_dates['day_of_week'] = df_dates['date'].dt.dayofweek
df_dates['day_name'] = df_dates['date'].dt.day_name()
df_dates['is_weekend'] = df_dates['day_of_week'].isin([5, 6]).astype(int)
df_dates['quarter'] = df_dates['date'].dt.quarter
df_dates['week_of_year'] = df_dates['date'].dt.isocalendar().week

# Cyclical encoding (for periodic features)
df_dates['month_sin'] = np.sin(2 * np.pi * df_dates['month'] / 12)
df_dates['month_cos'] = np.cos(2 * np.pi * df_dates['month'] / 12)

df_dates['day_sin'] = np.sin(2 * np.pi * df_dates['day_of_week'] / 7)
df_dates['day_cos'] = np.cos(2 * np.pi * df_dates['day_of_week'] / 7)

print(df_dates[['date', 'year', 'month', 'day_name', 'is_weekend']].head())

# ═══════════════════════════════════════════
# 5. TEXT FEATURES
# ═══════════════════════════════════════════

df_text = pd.DataFrame({
    'text': [
        'This is great!',
        'Bad product',
        'Excellent quality and fast shipping',
        'Terrible experience',
        'Love it!'
    ]
})

# Length features
df_text['text_length'] = df_text['text'].str.len()
df_text['word_count'] = df_text['text'].str.split().str.len()

# Count specific patterns
df_text['exclamation_count'] = df_text['text'].str.count('!')
df_text['uppercase_ratio'] = (df_text['text'].str.count(r'[A-Z]') /
                               df_text['text_length'])

# TF-IDF vectorization
from sklearn.feature_extraction.text import TfidfVectorizer

tfidf = TfidfVectorizer(max_features=10)
tfidf_matrix = tfidf.fit_transform(df_text['text'])

# Convert to DataFrame
tfidf_df = pd.DataFrame(
    tfidf_matrix.toarray(),
    columns=tfidf.get_feature_names_out()
)

print("\nTF-IDF features:")
print(tfidf_df)

# ═══════════════════════════════════════════
# 6. AGGREGATION FEATURES
# ═══════════════════════════════════════════

# Sample transactional data
transactions = pd.DataFrame({
    'user_id': [1, 1, 1, 2, 2, 3, 3, 3, 3],
    'amount': [10, 20, 15, 30, 25, 5, 10, 15, 20],
    'category': ['A', 'B', 'A', 'A', 'C', 'B', 'A', 'B', 'C']
})

# Aggregate by user
user_features = transactions.groupby('user_id').agg({
    'amount': ['sum', 'mean', 'median', 'std', 'min', 'max', 'count'],
    'category': lambda x: x.nunique()  # Number of unique categories
}).reset_index()

# Flatten column names
user_features.columns = ['_'.join(col).strip('_') for col in user_features.columns]

print("\nAggregated features:")
print(user_features)

# Rolling window features
df_series = pd.DataFrame({
    'value': np.random.randn(100).cumsum()
})

df_series['rolling_mean_7'] = df_series['value'].rolling(window=7).mean()
df_series['rolling_std_7'] = df_series['value'].rolling(window=7).std()
df_series['rolling_max_7'] = df_series['value'].rolling(window=7).max()

# Lag features
df_series['lag_1'] = df_series['value'].shift(1)
df_series['lag_7'] = df_series['value'].shift(7)

# Difference features
df_series['diff_1'] = df_series['value'].diff(1)

print(df_series.tail())

# ═══════════════════════════════════════════
# 7. FEATURE SELECTION
# ═══════════════════════════════════════════

# Sample data
from sklearn.datasets import make_classification

X, y = make_classification(n_samples=1000, n_features=20,
                          n_informative=10, n_redundant=5,
                          random_state=42)

X_df = pd.DataFrame(X, columns=[f'feature_{i}' for i in range(20)])

# 1. Univariate Feature Selection
selector = SelectKBest(score_func=f_classif, k=10)
X_selected = selector.fit_transform(X_df, y)

# Get selected feature names
selected_features = X_df.columns[selector.get_support()]
print(f"\nSelected features: {list(selected_features)}")

# 2. Correlation-based selection
correlation_matrix = X_df.corr().abs()

# Find highly correlated features
upper_tri = correlation_matrix.where(
    np.triu(np.ones(correlation_matrix.shape), k=1).astype(bool)
)

to_drop = [column for column in upper_tri.columns
           if any(upper_tri[column] > 0.95)]

print(f"Highly correlated features to drop: {to_drop}")

# 3. Feature importance (with tree-based model)
from sklearn.ensemble import RandomForestClassifier

rf = RandomForestClassifier(n_estimators=100, random_state=42)
rf.fit(X_df, y)

# Get feature importances
feature_importance = pd.DataFrame({
    'feature': X_df.columns,
    'importance': rf.feature_importances_
}).sort_values('importance', ascending=False)

print("\nTop 10 important features:")
print(feature_importance.head(10))

# ═══════════════════════════════════════════
# COMPLETE FEATURE ENGINEERING PIPELINE
# ═══════════════════════════════════════════

from sklearn.pipeline import Pipeline
from sklearn.compose import ColumnTransformer
from sklearn.preprocessing import StandardScaler, OneHotEncoder

def create_feature_pipeline(numeric_features, categorical_features):
    """
    Create a complete feature engineering pipeline
    """
    # Numeric pipeline
    numeric_transformer = Pipeline(steps=[
        ('scaler', StandardScaler())
    ])

    # Categorical pipeline
    categorical_transformer = Pipeline(steps=[
        ('onehot', OneHotEncoder(handle_unknown='ignore'))
    ])

    # Combine
    preprocessor = ColumnTransformer(
        transformers=[
            ('num', numeric_transformer, numeric_features),
            ('cat', categorical_transformer, categorical_features)
        ])

    return preprocessor

# Usage
numeric_features = ['age', 'income', 'experience']
categorical_features = ['city', 'education']

preprocessor = create_feature_pipeline(numeric_features, categorical_features)

# Fit and transform
X_transformed = preprocessor.fit_transform(df)

print(f"\nOriginal shape: {df[numeric_features + categorical_features].shape}")
print(f"Transformed shape: {X_transformed.shape}")
```

---

<div align="center">

## ⚡ Performance Optimization

</div>

### Making Your Code Faster 🚀

```python
# ═══════════════════════════════════════════
# PERFORMANCE OPTIMIZATION TECHNIQUES
# ═══════════════════════════════════════════

import pandas as pd
import numpy as np
import time

# ═══════════════════════════════════════════
# 1. VECTORIZATION vs LOOPS
# ═══════════════════════════════════════════

# Sample data
n = 1000000
data = pd.DataFrame({
    'A': np.random.randn(n),
    'B': np.random.randn(n)
})

# ❌ BAD: Python loop
start = time.time()
result = []
for i in range(len(data)):
    result.append(data.iloc[i]['A'] + data.iloc[i]['B'])
loop_time = time.time() - start
print(f"Loop time: {loop_time:.3f}s")

# ✅ GOOD: Vectorized operation
start = time.time()
result = data['A'] + data['B']
vectorized_time = time.time() - start
print(f"Vectorized time: {vectorized_time:.3f}s")
print(f"Speedup: {loop_time/vectorized_time:.1f}x faster")

# ═══════════════════════════════════════════
# 2. EFFICIENT DATA LOADING
# ═══════════════════════════════════════════

# Read only needed columns
columns_to_read = ['col1', 'col2', 'col3']
# df = pd.read_csv('large_file.csv', usecols=columns_to_read)

# Read in chunks (for very large files)
def process_in_chunks(filename, chunksize=10000):
    """
    Process large CSV file in chunks
    """
    results = []
    for chunk in pd.read_csv(filename, chunksize=chunksize):
        # Process chunk
        processed = chunk[chunk['value'] > 0]
        results.append(processed)

    return pd.concat(results, ignore_index=True)

# Optimize data types
def optimize_dtypes(df):
    """
    Reduce memory usage by optimizing data types
    """
    # Convert object to category for low-cardinality columns
    for col in df.select_dtypes(include=['object']).columns:
        num_unique = df[col].nunique()
        num_total = len(df[col])

        if num_unique / num_total < 0.5:  # Less than 50% unique
            df[col] = df[col].astype('category')

    # Downcast numeric types
    for col in df.select_dtypes(include=['int']).columns:
        df[col] = pd.to_numeric(df[col], downcast='integer')

    for col in df.select_dtypes(include=['float']).columns:
        df[col] = pd.to_numeric(df[col], downcast='float')

    return df

# Example
df = pd.DataFrame({
    'category': ['A', 'B', 'A', 'C'] * 250000,
    'value': np.random.randint(0, 100, 1000000),
    'price': np.random.random(1000000)
})

print(f"Original memory: {df.memory_usage(deep=True).sum() / 1024**2:.2f} MB")
df_optimized = optimize_dtypes(df)
print(f"Optimized memory: {df_optimized.memory_usage(deep=True).sum() / 1024**2:.2f} MB")

# Use Parquet instead of CSV (much faster)
# df.to_parquet('data.parquet', compression='snappy')
# df = pd.read_parquet('data.parquet')

# ═══════════════════════════════════════════
# 3. EFFICIENT PANDAS OPERATIONS
# ═══════════════════════════════════════════

# Use built-in methods instead of apply
df = pd.DataFrame({
    'A': np.random.randn(100000),
    'B': np.random.randn(100000)
})

# ❌ SLOW: apply
start = time.time()
result = df['A'].apply(lambda x: x ** 2)
apply_time = time.time() - start

# ✅ FAST: vectorized
start = time.time()
result = df['A'] ** 2
vectorized_time = time.time() - start

print(f"\nApply time: {apply_time:.3f}s")
print(f"Vectorized time: {vectorized_time:.3f}s")
print(f"Speedup: {apply_time/vectorized_time:.1f}x")

# Use query() for filtering
# ❌ SLOW
result = df[(df['A'] > 0) & (df['B'] < 0)]

# ✅ FAST
result = df.query('A > 0 and B < 0')

# Use eval() for complex expressions
# ❌ SLOW
df['C'] = df['A'] + df['B'] * 2 - df['A'] / 3

# ✅ FAST
df.eval('C = A + B * 2 - A / 3', inplace=True)

# ═══════════════════════════════════════════
# 4. PARALLEL PROCESSING
# ═══════════════════════════════════════════

from multiprocessing import Pool
import numpy as np

def expensive_function(x):
    """Simulate expensive computation"""
    return np.sum(np.sin(np.arange(10000)) * x)

data = np.random.rand(1000)

# ❌ Serial processing
start = time.time()
results = [expensive_function(x) for x in data]
serial_time = time.time() - start
print(f"\nSerial time: {serial_time:.3f}s")

# ✅ Parallel processing
start = time.time()
with Pool(processes=4) as pool:
    results = pool.map(expensive_function, data)
parallel_time = time.time() - start
print(f"Parallel time: {parallel_time:.3f}s")
print(f"Speedup: {serial_time/parallel_time:.1f}x")

# Pandas parallel apply (using swifter)
# pip install swifter
# import swifter
# df['result'] = df['column'].swifter.apply(expensive_function)

# ═══════════════════════════════════════════
# 5. NUMBA - JIT COMPILATION
# ═══════════════════════════════════════════

from numba import jit, prange

# Without JIT
def monte_carlo_pi(n):
    """Estimate Pi using Monte Carlo method"""
    inside = 0
    for _ in range(n):
        x = np.random.random()
        y = np.random.random()
        if x*x + y*y <= 1.0:
            inside += 1
    return 4.0 * inside / n

# With JIT
@jit(nopython=True)
def monte_carlo_pi_jit(n):
    """Estimate Pi using Monte Carlo method (JIT compiled)"""
    inside = 0
    for _ in range(n):
        x = np.random.random()
        y = np.random.random()
        if x*x + y*y <= 1.0:
            inside += 1
    return 4.0 * inside / n

# Compare
n = 10000000

start = time.time()
result1 = monte_carlo_pi(n)
normal_time = time.time() - start

start = time.time()
result2 = monte_carlo_pi_jit(n)
jit_time = time.time() - start

print(f"\nNormal time: {normal_time:.3f}s")
print(f"JIT time: {jit_time:.3f}s")
print(f"Speedup: {normal_time/jit_time:.1f}x")

# Parallel JIT
@jit(nopython=True, parallel=True)
def sum_parallel(arr):
    """Parallel sum with Numba"""
    total = 0
    for i in prange(len(arr)):
        total += arr[i]
    return total

# ═══════════════════════════════════════════
# 6. MEMORY-EFFICIENT OPERATIONS
# ═══════════════════════════════════════════

# Use generators instead of lists
# ❌ Memory-heavy
big_list = [x**2 for x in range(10000000)]

# ✅ Memory-efficient
big_generator = (x**2 for x in range(10000000))

# Process in chunks
def process_large_dataframe(df, func, chunksize=10000):
    """
    Process large DataFrame in chunks
    """
    for i in range(0, len(df), chunksize):
        chunk = df.iloc[i:i+chunksize]
        yield func(chunk)

# Use inplace operations where possible
df = pd.DataFrame({'A': range(1000000)})

# ❌ Creates copy
df_new = df.drop('A', axis=1)

# ✅ Modifies in place (saves memory)
df.drop('A', axis=1, inplace=True)

# ═══════════════════════════════════════════
# 7. PROFILING CODE
# ═══════════════════════════════════════════

import cProfile
import pstats

def slow_function():
    """Function to profile"""
    df = pd.DataFrame(np.random.randn(10000, 10))
    for col in df.columns:
        df[col] = df[col].apply(lambda x: x ** 2)
    return df

# Profile with cProfile
profiler = cProfile.Profile()
profiler.enable()
result = slow_function()
profiler.disable()

# Print stats
stats = pstats.Stats(profiler)
stats.sort_stats('cumulative')
stats.print_stats(10)  # Top 10 slowest functions

# Line profiler (install: pip install line_profiler)
# @profile decorator and run: kernprof -l -v script.py

# Memory profiler
# from memory_profiler import profile
# @profile
# def memory_heavy_function():
#     ...

# ═══════════════════════════════════════════
# 8. PERFORMANCE BEST PRACTICES
# ═══════════════════════════════════════════

# ✅ DO:
# • Use vectorized operations instead of loops
# • Use NumPy/Pandas built-in functions
# • Optimize data types (category, downcasting)
# • Use query() and eval() for complex operations
# • Read only necessary columns
# • Use Parquet/Feather instead of CSV
# • Process large files in chunks
# • Use parallel processing for independent operations
# • Profile code to find bottlenecks
# • Cache expensive computations

# ❌ DON'T:
# • Use iterrows() or loops when vectorization is possible
# • Chain multiple copies of DataFrames
# • Use apply() when built-in functions exist
# • Load entire file if you only need subset
# • Keep unused columns in memory
# • Convert between data types unnecessarily
```

---

<div align="center">

## 🚀 Real-World Projects

</div>

### Complete Data Science Workflows 💼

```python
# ═══════════════════════════════════════════
# PROJECT 1: SALES ANALYSIS DASHBOARD
# ═══════════════════════════════════════════

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Generate sample sales data
np.random.seed(42)
dates = pd.date_range('2023-01-01', '2024-12-31', freq='D')
n_products = 5
products = [f'Product_{chr(65+i)}' for i in range(n_products)]
regions = ['North', 'South', 'East', 'West']

data = []
for date in dates:
    for _ in range(np.random.randint(5, 20)):
        data.append({
            'date': date,
            'product': np.random.choice(products),
            'region': np.random.choice(regions),
            'quantity': np.random.randint(1, 10),
            'price': np.random.uniform(10, 100),
            'customer_id': np.random.randint(1000, 2000)
        })

df = pd.DataFrame(data)
df['revenue'] = df['quantity'] * df['price']

print("Sales Data Shape:", df.shape)
print("\nFirst rows:")
print(df.head())

# ═══════════════════════════════════════════
# DATA CLEANING & PREPARATION
# ═══════════════════════════════════════════

# Check for missing values
print("\nMissing values:")
print(df.isnull().sum())

# Add time-based features
df['year'] = df['date'].dt.year
df['month'] = df['date'].dt.month
df['quarter'] = df['date'].dt.quarter
df['day_of_week'] = df['date'].dt.day_name()
df['is_weekend'] = df['date'].dt.dayofweek.isin([5, 6]).astype(int)

# ═══════════════════════════════════════════
# EXPLORATORY ANALYSIS
# ═══════════════════════════════════════════

# 1. Overall metrics
total_revenue = df['revenue'].sum()
total_transactions = len(df)
avg_order_value = df['revenue'].mean()

print(f"\n📊 OVERALL METRICS")
print(f"Total Revenue: ${total_revenue:,.2f}")
print(f"Total Transactions: {total_transactions:,}")
print(f"Average Order Value: ${avg_order_value:.2f}")

# 2. Revenue by product
revenue_by_product = df.groupby('product')['revenue'].sum().sort_values(ascending=False)
print(f"\n💰 Revenue by Product:")
print(revenue_by_product)

# 3. Monthly trend
monthly_revenue = df.groupby(['year', 'month'])['revenue'].sum().reset_index()

# Visualize
fig, axes = plt.subplots(2, 2, figsize=(15, 10))

# Revenue by product
axes[0, 0].bar(revenue_by_product.index, revenue_by_product.values)
axes[0, 0].set_title('Revenue by Product')
axes[0, 0].set_ylabel('Revenue ($)')
axes[0, 0].tick_params(axis='x', rotation=45)

# Revenue trend
monthly_revenue['date'] = pd.to_datetime(monthly_revenue[['year', 'month']].assign(day=1))
axes[0, 1].plot(monthly_revenue['date'], monthly_revenue['revenue'])
axes[0, 1].set_title('Monthly Revenue Trend')
axes[0, 1].set_ylabel('Revenue ($)')
axes[0, 1].tick_params(axis='x', rotation=45)

# Revenue by region
region_revenue = df.groupby('region')['revenue'].sum()
axes[1, 0].pie(region_revenue.values, labels=region_revenue.index, autopct='%1.1f%%')
axes[1, 0].set_title('Revenue by Region')

# Revenue by day of week
dow_revenue = df.groupby('day_of_week')['revenue'].mean()
dow_order = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday']
dow_revenue = dow_revenue.reindex(dow_order)
axes[1, 1].bar(range(7), dow_revenue.values)
axes[1, 1].set_xticks(range(7))
axes[1, 1].set_xticklabels(dow_order, rotation=45)
axes[1, 1].set_title('Average Revenue by Day of Week')
axes[1, 1].set_ylabel('Revenue ($)')

plt.tight_layout()
plt.savefig('sales_analysis.png', dpi=300, bbox_inches='tight')
print("\n✅ Analysis visualizations saved to 'sales_analysis.png'")

# ═══════════════════════════════════════════
# CUSTOMER ANALYSIS
# ═══════════════════════════════════════════

# RFM Analysis (Recency, Frequency, Monetary)
reference_date = df['date'].max()

rfm = df.groupby('customer_id').agg({
    'date': lambda x: (reference_date - x.max()).days,  # Recency
    'customer_id': 'count',  # Frequency
    'revenue': 'sum'  # Monetary
}).reset_index()

rfm.columns = ['customer_id', 'recency', 'frequency', 'monetary']

# Create RFM scores (1-5)
rfm['r_score'] = pd.qcut(rfm['recency'], 5, labels=[5, 4, 3, 2, 1])
rfm['f_score'] = pd.qcut(rfm['frequency'].rank(method='first'), 5, labels=[1, 2, 3, 4, 5])
rfm['m_score'] = pd.qcut(rfm['monetary'], 5, labels=[1, 2, 3, 4, 5])

rfm['rfm_score'] = rfm['r_score'].astype(str) + rfm['f_score'].astype(str) + rfm['m_score'].astype(str)

# Segment customers
def segment_customer(row):
    if row['r_score'] >= 4 and row['f_score'] >= 4 and row['m_score'] >= 4:
        return 'Champions'
    elif row['r_score'] >= 3 and row['f_score'] >= 3 and row['m_score'] >= 3:
        return 'Loyal Customers'
    elif row['r_score'] >= 4:
        return 'Recent Customers'
    elif row['f_score'] >= 4:
        return 'Frequent Buyers'
    elif row['m_score'] >= 4:
        return 'Big Spenders'
    else:
        return 'At Risk'

rfm['segment'] = rfm.apply(segment_customer, axis=1)

print(f"\n👥 Customer Segments:")
print(rfm['segment'].value_counts())

# ═══════════════════════════════════════════
# FORECAST (SIMPLE TIME SERIES)
# ═══════════════════════════════════════════

# Aggregate daily revenue
daily_revenue = df.groupby('date')['revenue'].sum().reset_index()

# Simple moving average forecast
daily_revenue['MA_7'] = daily_revenue['revenue'].rolling(window=7).mean()
daily_revenue['MA_30'] = daily_revenue['revenue'].rolling(window=30).mean()

# Plot
plt.figure(figsize=(15, 6))
plt.plot(daily_revenue['date'], daily_revenue['revenue'], alpha=0.3, label='Actual')
plt.plot(daily_revenue['date'], daily_revenue['MA_7'], label='7-day MA')
plt.plot(daily_revenue['date'], daily_revenue['MA_30'], label='30-day MA')
plt.title('Daily Revenue with Moving Averages')
plt.xlabel('Date')
plt.ylabel('Revenue ($)')
plt.legend()
plt.xticks(rotation=45)
plt.tight_layout()
plt.savefig('revenue_forecast.png', dpi=300, bbox_inches='tight')
print("✅ Forecast plot saved to 'revenue_forecast.png'")

# ═══════════════════════════════════════════
# GENERATE INSIGHTS REPORT
# ═══════════════════════════════════════════

def generate_insights_report(df, rfm):
    """
    Generate automated insights report
    """
    report = []

    report.append("=" * 80)
    report.append("SALES ANALYSIS INSIGHTS REPORT")
    report.append("=" * 80)

    # Top performers
    top_product = df.groupby('product')['revenue'].sum().idxmax()
    top_product_revenue = df.groupby('product')['revenue'].sum().max()
    report.append(f"\n🏆 TOP PERFORMING PRODUCT: {top_product}")
    report.append(f"   Revenue: ${top_product_revenue:,.2f}")

    top_region = df.groupby('region')['revenue'].sum().idxmax()
    report.append(f"\n🌍 TOP PERFORMING REGION: {top_region}")

    # Growth trends
    current_month_revenue = df[df['month'] == df['month'].max()]['revenue'].sum()
    prev_month_revenue = df[df['month'] == df['month'].max() - 1]['revenue'].sum()
    growth = ((current_month_revenue - prev_month_revenue) / prev_month_revenue) * 100

    report.append(f"\n📈 MONTH-OVER-MONTH GROWTH: {growth:+.2f}%")

    # Customer insights
    total_customers = df['customer_id'].nunique()
    report.append(f"\n👥 TOTAL CUSTOMERS: {total_customers:,}")
    report.append(f"   Champions: {len(rfm[rfm['segment'] == 'Champions'])} ({len(rfm[rfm['segment'] == 'Champions'])/len(rfm)*100:.1f}%)")
    report.append(f"   At Risk: {len(rfm[rfm['segment'] == 'At Risk'])} ({len(rfm[rfm['segment'] == 'At Risk'])/len(rfm)*100:.1f}%)")

    # Recommendations
    report.append("\n💡 RECOMMENDATIONS:")
    if growth < 0:
        report.append("   • Focus on customer retention campaigns")
        report.append("   • Analyze reasons for revenue decline")

    at_risk_pct = len(rfm[rfm['segment'] == 'At Risk']) / len(rfm) * 100
    if at_risk_pct > 20:
        report.append(f"   • {at_risk_pct:.1f}% customers at risk - implement win-back campaigns")

    report.append("\n" + "=" * 80)

    return "\n".join(report)

# Generate and print report
report = generate_insights_report(df, rfm)
print(report)

# Save report to file
with open('insights_report.txt', 'w') as f:
    f.write(report)

print("\n✅ Report saved to 'insights_report.txt'")

# ═══════════════════════════════════════════
# PROJECT 2: CUSTOMER CHURN PREDICTION
# ═══════════════════════════════════════════

from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import classification_report, confusion_matrix, roc_auc_score

# Generate sample churn data
np.random.seed(42)
n_customers = 5000

churn_data = pd.DataFrame({
    'customer_id': range(n_customers),
    'tenure_months': np.random.randint(1, 72, n_customers),
    'monthly_charges': np.random.uniform(20, 150, n_customers),
    'total_charges': np.random.uniform(100, 8000, n_customers),
    'contract_type': np.random.choice(['Month-to-month', 'One year', 'Two year'], n_customers),
    'payment_method': np.random.choice(['Electronic check', 'Mailed check', 'Bank transfer', 'Credit card'], n_customers),
    'tech_support': np.random.choice(['Yes', 'No'], n_customers),
    'num_services': np.random.randint(0, 10, n_customers),
    'support_tickets': np.random.randint(0, 20, n_customers),
})

# Create target variable (churn) - biased by features
churn_probability = (
    (churn_data['tenure_months'] < 12) * 0.3 +
    (churn_data['monthly_charges'] > 100) * 0.2 +
    (churn_data['contract_type'] == 'Month-to-month') * 0.3 +
    (churn_data['support_tickets'] > 10) * 0.2 +
    np.random.uniform(0, 0.2, n_customers)
)

churn_data['churned'] = (churn_probability > 0.5).astype(int)

print("\n📊 CHURN PREDICTION PROJECT")
print(f"Total Customers: {len(churn_data)}")
print(f"Churn Rate: {churn_data['churned'].mean()*100:.2f}%")

# Feature engineering
churn_data['avg_monthly_spend'] = churn_data['total_charges'] / churn_data['tenure_months']
churn_data['charges_per_service'] = churn_data['monthly_charges'] / (churn_data['num_services'] + 1)

# Encode categorical variables
churn_encoded = pd.get_dummies(churn_data, columns=['contract_type', 'payment_method', 'tech_support'],
                                drop_first=True)

# Prepare features and target
X = churn_encoded.drop(['customer_id', 'churned'], axis=1)
y = churn_encoded['churned']

# Split data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42, stratify=y)

# Scale features
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)

# Train model
model = RandomForestClassifier(n_estimators=100, random_state=42, max_depth=10)
model.fit(X_train_scaled, y_train)

# Predictions
y_pred = model.predict(X_test_scaled)
y_pred_proba = model.predict_proba(X_test_scaled)[:, 1]

# Evaluation
print("\n📊 MODEL PERFORMANCE:")
print(classification_report(y_test, y_pred))
print(f"\nROC-AUC Score: {roc_auc_score(y_test, y_pred_proba):.4f}")

# Feature importance
feature_importance = pd.DataFrame({
    'feature': X.columns,
    'importance': model.feature_importances_
}).sort_values('importance', ascending=False)

print("\n🎯 TOP 10 CHURN PREDICTORS:")
print(feature_importance.head(10))

# Visualize confusion matrix
cm = confusion_matrix(y_test, y_pred)
plt.figure(figsize=(8, 6))
sns.heatmap(cm, annot=True, fmt='d', cmap='Blues')
plt.title('Confusion Matrix - Churn Prediction')
plt.ylabel('Actual')
plt.xlabel('Predicted')
plt.savefig('churn_confusion_matrix.png', dpi=300, bbox_inches='tight')
print("\n✅ Confusion matrix saved to 'churn_confusion_matrix.png'")

# Identify high-risk customers
high_risk_customers = churn_data.copy()
high_risk_customers['churn_probability'] = model.predict_proba(
    scaler.transform(churn_encoded.drop(['customer_id', 'churned'], axis=1))
)[:, 1]

high_risk = high_risk_customers[high_risk_customers['churn_probability'] > 0.7].sort_values(
    'churn_probability', ascending=False
)

print(f"\n⚠️  HIGH RISK CUSTOMERS (>70% churn probability): {len(high_risk)}")
print("\nTop 5 at-risk customers:")
print(high_risk[['customer_id', 'tenure_months', 'monthly_charges', 'support_tickets', 'churn_probability']].head())

# Save high-risk customer list
high_risk.to_csv('high_risk_customers.csv', index=False)
print("\n✅ High-risk customer list saved to 'high_risk_customers.csv'")

# ═══════════════════════════════════════════
# PROJECT 3: A/B TEST ANALYSIS
# ═══════════════════════════════════════════

from scipy import stats

# Generate A/B test data
np.random.seed(42)

# Control group (A)
n_control = 1000
control_conversions = np.random.binomial(1, 0.10, n_control)  # 10% conversion rate

# Treatment group (B)
n_treatment = 1000
treatment_conversions = np.random.binomial(1, 0.12, n_treatment)  # 12% conversion rate

ab_test = pd.DataFrame({
    'group': ['A'] * n_control + ['B'] * n_treatment,
    'converted': np.concatenate([control_conversions, treatment_conversions])
})

print("\n🔬 A/B TEST ANALYSIS")
print("=" * 60)

# Calculate conversion rates
conversion_rates = ab_test.groupby('group')['converted'].agg(['sum', 'count', 'mean'])
conversion_rates['conversion_rate'] = conversion_rates['mean'] * 100

print("\n📊 Conversion Rates:")
print(conversion_rates[['sum', 'count', 'conversion_rate']])

# Statistical test (Chi-square test)
contingency_table = pd.crosstab(ab_test['group'], ab_test['converted'])
chi2, p_value, dof, expected = stats.chi2_contingency(contingency_table)

print(f"\n📈 Chi-Square Test:")
print(f"Chi-square statistic: {chi2:.4f}")
print(f"p-value: {p_value:.4f}")

alpha = 0.05
if p_value < alpha:
    print(f"✅ Result is statistically significant (p < {alpha})")
    print("   Reject null hypothesis: There is a significant difference between groups")
else:
    print(f"❌ Result is NOT statistically significant (p >= {alpha})")
    print("   Fail to reject null hypothesis: No significant difference between groups")

# Calculate lift
control_rate = conversion_rates.loc['A', 'mean']
treatment_rate = conversion_rates.loc['B', 'mean']
lift = ((treatment_rate - control_rate) / control_rate) * 100

print(f"\n📈 Lift: {lift:+.2f}%")

# Confidence interval for difference
def proportion_confint(count, nobs, alpha=0.05):
    """Calculate confidence interval for proportion"""
    from statsmodels.stats.proportion import proportion_confint
    return proportion_confint(count, nobs, alpha=alpha, method='normal')

ci_control = proportion_confint(
    conversion_rates.loc['A', 'sum'],
    conversion_rates.loc['A', 'count']
)

ci_treatment = proportion_confint(
    conversion_rates.loc['B', 'sum'],
    conversion_rates.loc['B', 'count']
)

print(f"\n95% Confidence Intervals:")
print(f"Control (A):   [{ci_control[0]*100:.2f}%, {ci_control[1]*100:.2f}%]")
print(f"Treatment (B): [{ci_treatment[0]*100:.2f}%, {ci_treatment[1]*100:.2f}%]")

# Visualize results
fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(14, 5))

# Bar chart
groups = ['Control (A)', 'Treatment (B)']
rates = [control_rate * 100, treatment_rate * 100]
colors = ['#3498db', '#2ecc71']

ax1.bar(groups, rates, color=colors)
ax1.set_ylabel('Conversion Rate (%)')
ax1.set_title('A/B Test Results')
ax1.set_ylim(0, max(rates) * 1.2)

for i, (group, rate) in enumerate(zip(groups, rates)):
    ax1.text(i, rate + 0.5, f'{rate:.2f}%', ha='center', fontsize=12, fontweight='bold')

# Confidence intervals
ax2.errorbar([0, 1], [control_rate * 100, treatment_rate * 100],
             yerr=[(control_rate - ci_control[0]) * 100, (treatment_rate - ci_treatment[0]) * 100],
             fmt='o', markersize=10, capsize=5, capthick=2, color=colors)
ax2.set_xticks([0, 1])
ax2.set_xticklabels(groups)
ax2.set_ylabel('Conversion Rate (%)')
ax2.set_title('A/B Test with 95% Confidence Intervals')
ax2.grid(True, alpha=0.3)

plt.tight_layout()
plt.savefig('ab_test_results.png', dpi=300, bbox_inches='tight')
print("\n✅ A/B test visualization saved to 'ab_test_results.png'")

# Recommendation
print("\n💡 RECOMMENDATION:")
if p_value < alpha and lift > 0:
    print(f"   ✅ Implement variant B - Expected lift: {lift:.2f}%")

    # Calculate expected impact
    total_visitors = 100000  # Example
    expected_additional_conversions = total_visitors * (treatment_rate - control_rate)
    print(f"   📊 Expected additional conversions per 100K visitors: {expected_additional_conversions:.0f}")
else:
    print("   ⚠️  Continue testing or try different variant")
```

---

<div align="center">

## ✅ Best Practices

</div>

### Professional Data Science Standards 📋

```bash
# ═══════════════════════════════════════════
# PROJECT ORGANIZATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   RECOMMENDED FOLDER STRUCTURE             ║
╚════════════════════════════════════════════════════════════╝

project/
├── data/
│   ├── raw/                    # Original, immutable data
│   ├── processed/              # Cleaned, processed data
│   └── external/               # External data sources
│
├── notebooks/
│   ├── 01_exploration.ipynb    # EDA notebooks
│   ├── 02_modeling.ipynb       # Model development
│   └── 03_evaluation.ipynb     # Model evaluation
│
├── src/
│   ├── __init__.py
│   ├── data/                   # Data processing modules
│   │   ├── __init__.py
│   │   └── preprocessing.py
│   ├── features/               # Feature engineering
│   │   ├── __init__.py
│   │   └── build_features.py
│   ├── models/                 # Model code
│   │   ├── __init__.py
│   │   ├── train.py
│   │   └── predict.py
│   └── visualization/          # Visualization code
│       ├── __init__.py
│       └── visualize.py
│
├── models/                     # Trained models (.pkl, .h5)
├── reports/                    # Generated reports
│   └── figures/                # Plots and figures
├── tests/                      # Unit tests
│   ├── __init__.py
│   └── test_preprocessing.py
│
├── requirements.txt            # Dependencies
├── setup.py                    # Package setup
├── README.md                   # Project documentation
├── .gitignore                  # Git ignore rules
└── config.yaml                 # Configuration
```

---

### Code Quality Standards 📝

```python
# ═══════════════════════════════════════════
# 1. MEANINGFUL VARIABLE NAMES
# ═══════════════════════════════════════════

import pandas as pd

# ❌ BAD: Cryptic, unclear names
df1 = pd.read_csv('data.csv')
x = df1[['a', 'b', 'c']]
y = df1['d']

# ✅ GOOD: Clear, descriptive names
customer_data = pd.read_csv('customer_data.csv')
features = customer_data[['age', 'income', 'tenure']]
target = customer_data['churned']

# ═══════════════════════════════════════════
# 2. WRITE COMPREHENSIVE DOCSTRINGS
# ═══════════════════════════════════════════

def calculate_churn_probability(customer_features, model):
    """
    Calculate churn probability for customers.

    Parameters
    ----------
    customer_features : pd.DataFrame
        DataFrame containing customer features (age, income, tenure)
    model : sklearn model
        Trained classification model

    Returns
    -------
    np.ndarray
        Array of churn probabilities for each customer

    Examples
    --------
    >>> features = pd.DataFrame({'age': [25, 30], 'income': [50000, 60000]})
    >>> probs = calculate_churn_probability(features, trained_model)
    >>> probs
    array([0.15, 0.23])
    """
    return model.predict_proba(customer_features)[:, 1]

# ═══════════════════════════════════════════
# 3. USE TYPE HINTS
# ═══════════════════════════════════════════

from typing import List, Dict, Tuple, Optional
import pandas as pd
import numpy as np

def preprocess_data(
    data: pd.DataFrame,
    columns: List[str],
    fill_value: Optional[float] = None
) -> Tuple[pd.DataFrame, Dict[str, float]]:
    """
    Preprocess data by handling missing values.

    Parameters
    ----------
    data : pd.DataFrame
        Input data
    columns : List[str]
        Columns to process
    fill_value : Optional[float]
        Value to fill missing data (None = use mean)

    Returns
    -------
    Tuple[pd.DataFrame, Dict[str, float]]
        Processed data and dictionary of fill values used
    """
    processed = data.copy()
    fill_values = {}

    for col in columns:
        if fill_value is None:
            fill_val = processed[col].mean()
        else:
            fill_val = fill_value

        processed[col].fillna(fill_val, inplace=True)
        fill_values[col] = fill_val

    return processed, fill_values

# ═══════════════════════════════════════════
# 4. PROPER ERROR HANDLING
# ═══════════════════════════════════════════

def load_and_validate_data(filepath: str) -> pd.DataFrame:
    """
    Load data with comprehensive error handling.
    """
    try:
        df = pd.read_csv(filepath)
    except FileNotFoundError:
        raise FileNotFoundError(f"Data file not found: {filepath}")
    except pd.errors.EmptyDataError:
        raise ValueError(f"Data file is empty: {filepath}")
    except Exception as e:
        raise Exception(f"Error loading data: {str(e)}")

    # Validate data
    if df.empty:
        raise ValueError("Loaded DataFrame is empty")

    required_columns = ['customer_id', 'age', 'income']
    missing_columns = set(required_columns) - set(df.columns)
    if missing_columns:
        raise ValueError(f"Missing required columns: {missing_columns}")

    return df

# ═══════════════════════════════════════════
# 5. IMPLEMENT LOGGING
# ═══════════════════════════════════════════

import logging

# Configure logging
logging.basicConfig(
    level=logging.INFO,
    format='%(asctime)s - %(name)s - %(levelname)s - %(message)s',
    handlers=[
        logging.FileHandler('data_processing.log'),
        logging.StreamHandler()
    ]
)

logger = logging.getLogger(__name__)

def process_customer_data(df: pd.DataFrame) -> pd.DataFrame:
    """Process customer data with logging."""
    logger.info(f"Starting data processing. Input shape: {df.shape}")

    # Remove duplicates
    initial_rows = len(df)
    df = df.drop_duplicates()
    logger.info(f"Removed {initial_rows - len(df)} duplicate rows")

    # Handle missing values
    missing_before = df.isnull().sum().sum()
    df = df.fillna(df.mean(numeric_only=True))
    logger.info(f"Filled {missing_before} missing values")

    # Remove outliers (assuming function exists)
    initial_rows = len(df)
    df = remove_outliers(df)
    logger.info(f"Removed {initial_rows - len(df)} outlier rows")

    logger.info(f"Processing complete. Output shape: {df.shape}")
    return df
```

---

### Configuration Management ⚙️

```python
# ═══════════════════════════════════════════
# EXTERNALIZE CONFIGURATION
# ═══════════════════════════════════════════

import yaml
from pathlib import Path

class Config:
    """Configuration management class."""

    def __init__(self, config_path: str = 'config.yaml'):
        with open(config_path, 'r') as f:
            self.config = yaml.safe_load(f)

    def get(self, key: str, default=None):
        """
        Get configuration value using dot notation.

        Example:
            config.get('data.raw_path')
            config.get('model.n_estimators', 100)
        """
        keys = key.split('.')
        value = self.config

        for k in keys:
            if isinstance(value, dict) and k in value:
                value = value[k]
            else:
                return default

        return value

# Usage
config = Config('config.yaml')
raw_data_path = config.get('data.raw_path')
n_estimators = config.get('model.n_estimators', 100)
```

**config.yaml** example:

```yaml
data:
  raw_path: data/raw/
  processed_path: data/processed/

preprocessing:
  missing_value_strategy: mean
  outlier_threshold: 3

model:
  algorithm: random_forest
  n_estimators: 100
  max_depth: 10

output:
  model_path: models/
  report_path: reports/
```

---

### Data Quality Validation ✅

```python
# ═══════════════════════════════════════════
# DATA QUALITY CHECKS
# ═══════════════════════════════════════════

from typing import Dict, Callable

def validate_dataframe(
    df: pd.DataFrame,
    checks: Dict[str, Callable]
) -> Dict[str, bool]:
    """
    Run data quality checks on DataFrame.

    Parameters
    ----------
    df : pd.DataFrame
        DataFrame to validate
    checks : Dict[str, Callable]
        Dictionary mapping check names to check functions

    Returns
    -------
    Dict[str, bool]
        Results of each check (True = passed)
    """
    results = {}

    for check_name, check_func in checks.items():
        try:
            results[check_name] = check_func(df)
        except Exception as e:
            logger.error(f"Error in check '{check_name}': {str(e)}")
            results[check_name] = False

    return results

# Define validation checks
checks = {
    'no_nulls_in_id': lambda df: df['customer_id'].isnull().sum() == 0,
    'positive_values': lambda df: (df['age'] > 0).all() and (df['income'] > 0).all(),
    'valid_dates': lambda df: df['signup_date'].dtype == 'datetime64[ns]',
    'reasonable_age': lambda df: (df['age'] >= 18).all() and (df['age'] <= 120).all(),
}

# Run checks
results = validate_dataframe(customer_data, checks)

print("Data Quality Check Results:")
for check, passed in results.items():
    status = "✅ PASS" if passed else "❌ FAIL"
    print(f"{check}: {status}")
```

---

### Reproducibility 🔄

```python
# ═══════════════════════════════════════════
# ENSURE REPRODUCIBLE RESULTS
# ═══════════════════════════════════════════

import numpy as np
import pandas as pd
import random

def set_seeds(seed: int = 42):
    """
    Set random seeds for reproducibility across libraries.
    """
    np.random.seed(seed)
    random.seed(seed)

    # For PyTorch (if used)
    # import torch
    # torch.manual_seed(seed)
    # torch.cuda.manual_seed_all(seed)

    # For TensorFlow (if used)
    # import tensorflow as tf
    # tf.random.set_seed(seed)

# Set seeds at start of script
set_seeds(42)
```

**requirements.txt** (always specify versions!):

```
numpy==1.24.3
pandas==2.0.3
scikit-learn==1.3.0
matplotlib==3.7.2
seaborn==0.12.2
scipy==1.11.1
jupyter==1.0.0
```

---

### Testing 🧪

```python
# ═══════════════════════════════════════════
# UNIT TESTS
# ═══════════════════════════════════════════

import unittest
import pandas as pd

class TestPreprocessing(unittest.TestCase):
    """Test preprocessing functions."""

    def setUp(self):
        """Set up test data before each test."""
        self.test_data = pd.DataFrame({
            'age': [25, 30, None, 40],
            'income': [50000, 60000, 70000, 80000]
        })

    def test_missing_value_imputation(self):
        """Test that missing values are filled correctly."""
        result, fill_values = preprocess_data(
            self.test_data,
            columns=['age'],
            fill_value=None
        )

        # Check no missing values remain
        self.assertEqual(result['age'].isnull().sum(), 0)

        # Check fill value is mean
        expected_mean = self.test_data['age'].mean()
        self.assertAlmostEqual(fill_values['age'], expected_mean)

    def test_invalid_column(self):
        """Test handling of invalid column names."""
        with self.assertRaises(KeyError):
            preprocess_data(self.test_data, columns=['invalid_column'])

    def test_output_shape(self):
        """Test that output shape matches input shape."""
        result, _ = preprocess_data(self.test_data, columns=['age'])
        self.assertEqual(result.shape, self.test_data.shape)

# Run tests
if __name__ == '__main__':
    unittest.main()

# Or run from command line:
# python -m unittest test_preprocessing.py
# python -m pytest tests/  (if using pytest)
```

---

### Code Review Checklist 📋

```bash
# ═══════════════════════════════════════════
# DATA SCIENCE CODE REVIEW CHECKLIST
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   DATA QUALITY                             ║
╚════════════════════════════════════════════════════════════╝

☐ Data source documented
☐ Data loaded correctly
☐ Missing values handled appropriately
☐ Outliers detected and addressed
☐ Data types correct
☐ Duplicates removed
☐ Data validation checks implemented

╔════════════════════════════════════════════════════════════╗
║                   CODE QUALITY                             ║
╚════════════════════════════════════════════════════════════╝

☐ Meaningful variable names
☐ Functions have comprehensive docstrings
☐ Type hints used
☐ Error handling implemented
☐ Logging added for important operations
☐ Code follows PEP 8 style guide
☐ No hardcoded values (use config)
☐ DRY principle applied (Don't Repeat Yourself)
☐ Functions are modular and reusable
☐ Code is readable and maintainable

╔════════════════════════════════════════════════════════════╗
║                   REPRODUCIBILITY                          ║
╚════════════════════════════════════════════════════════════╝

☐ Random seeds set
☐ Dependencies listed with exact versions
☐ Configuration externalized (not hardcoded)
☐ README.md updated with instructions
☐ Comments explain "why" not "what"
☐ Environment documented (Python version, OS)
☐ Data versioning strategy in place

╔════════════════════════════════════════════════════════════╗
║                   ANALYSIS                                 ║
╚════════════════════════════════════════════════════════════╝

☐ Exploratory Data Analysis (EDA) performed
☐ Assumptions validated
☐ Multiple approaches tried and compared
☐ Results interpreted correctly
☐ Visualizations clear and properly labeled
☐ Statistical tests appropriate
☐ Causal vs correlation understood

╔════════════════════════════════════════════════════════════╗
║                   MODELING                                 ║
╚════════════════════════════════════════════════════════════╝

☐ Train/test split implemented
☐ Cross-validation used
☐ Hyperparameters tuned systematically
☐ Model evaluated with multiple metrics
☐ Feature importance analyzed
☐ Predictions validated on holdout set
☐ Model performance baseline established
☐ Overfitting checked
☐ Model assumptions verified

╔════════════════════════════════════════════════════════════╗
║                   DOCUMENTATION                            ║
╚════════════════════════════════════════════════════════════╝

☐ Process documented in notebooks
☐ Findings summarized in report
☐ Limitations clearly noted
☐ Next steps outlined
☐ Business impact quantified
☐ Visualizations saved with descriptive names
☐ Model card created (if deploying)

╔════════════════════════════════════════════════════════════╗
║                   DEPLOYMENT                               ║
╚════════════════════════════════════════════════════════════╝

☐ Model serialized properly
☐ API created (if needed)
☐ Monitoring plan established
☐ Rollback strategy defined
☐ Performance benchmarks set
☐ Error handling for production
☐ Documentation for end users

═══════════════════════════════════════════════════════════
```

---

### Documentation Standards 📄

```markdown
# ═══════════════════════════════════════════

# README.md TEMPLATE

# ═══════════════════════════════════════════

# Customer Churn Prediction

## 📊 Project Overview

Predict customer churn using machine learning to identify at-risk customers
and enable proactive retention strategies.

## 🎯 Business Problem

High customer churn rate (25%) leading to revenue loss. Need to identify
customers likely to churn in the next 30 days.

## 📁 Project Structure

project/
├── data/ # Data files
├── notebooks/ # Jupyter notebooks
├── src/ # Source code
├── models/ # Trained models
├── reports/ # Analysis reports
└── tests/ # Unit tests
```

## 🚀 Setup

### Prerequisites

- Python 3.9+
- pip or conda

### Installation

```bash
# Clone repository
git clone https://github.com/username/churn-prediction.git
cd churn-prediction

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

## 💻 Usage

### Data Preprocessing

```bash
python src/data/preprocessing.py --input data/raw/customers.csv --output data/processed/
```

### Train Model

```bash
python src/models/train.py --data data/processed/ --model-output models/
```

### Make Predictions

```bash
python src/models/predict.py --model models/churn_model.pkl --input data/new_customers.csv
```

## 📈 Results

| Metric    | Value |
| --------- | ----- |
| Accuracy  | 85.3% |
| Precision | 82.1% |
| Recall    | 78.9% |
| ROC-AUC   | 0.89  |

### Key Findings

- Top churn indicators: contract type, tenure, support tickets
- Monthly contract customers 3x more likely to churn
- Customers with >5 support tickets have 60% churn probability

## 📊 Model Performance

![ROC Curve](reports/figures/roc_curve.png)
![Feature Importance](reports/figures/feature_importance.png)

## 🔄 Model Updates

To retrain the model with new data:

```bash
python src/models/train.py --data data/new/ --retrain
```

## 🧪 Testing

```bash
# Run all tests
python -m pytest tests/

# Run with coverage
python -m pytest --cov=src tests/
```

## 📝 License

MIT License - see LICENSE file

## 👥 Authors

- Your Name - [email@example.com](mailto:email@example.com)
- Contributor Name

## 🙏 Acknowledgments

- Dataset source: [Link]
- Inspiration: [Papers/Projects]

---

### Naming Conventions 📛

```python
# ═══════════════════════════════════════════
# PYTHON NAMING CONVENTIONS
# ═══════════════════════════════════════════

# ✅ GOOD NAMING EXAMPLES

# Variables: lowercase_with_underscores
customer_age = 25
total_revenue = 10000
is_premium_customer = True

# Constants: UPPERCASE_WITH_UNDERSCORES
MAX_ITERATIONS = 1000
DEFAULT_BATCH_SIZE = 32
API_KEY = "your-api-key"

# Functions: lowercase_with_underscores
def calculate_customer_lifetime_value(customer_data):
    pass

def preprocess_data(df):
    pass

# Classes: CapitalizedWords (PascalCase)
class CustomerSegmentation:
    pass

class DataProcessor:
    pass

# Private methods/attributes: _leading_underscore
class Model:
    def _internal_method(self):
        pass

    def __init__(self):
        self._private_attribute = None

# Protected: __double_underscore (name mangling)
class BaseModel:
    def __private_method(self):
        pass

# ❌ BAD NAMING EXAMPLES

# Too short/cryptic
x = df[['a', 'b']]
fn = lambda x: x * 2
d = {}

# Inconsistent style
customerAge = 25      # camelCase (use snake_case)
TotalRevenue = 1000   # PascalCase for variable (use snake_case)

# Non-descriptive
data1, data2, data3
temp, tmp
foo, bar

# ═══════════════════════════════════════════
# FILE NAMING CONVENTIONS
# ═══════════════════════════════════════════

# Scripts: lowercase_with_underscores.py
data_preprocessing.py
model_training.py
customer_segmentation.py

# Notebooks: numbered_descriptive_name.ipynb
01_data_exploration.ipynb
02_feature_engineering.ipynb
03_model_development.ipynb

# Data files: descriptive_versioned.csv
customer_data_2024_01.csv
sales_data_raw.csv
sales_data_processed.csv

# Model files: model_version_date.pkl
churn_model_v1_20240101.pkl
recommendation_model_v2.pkl

# Config files: lowercase.yaml
config.yaml
database.yaml
model_config.yaml
```

---

### Performance Best Practices ⚡

```python
# ═══════════════════════════════════════════
# PERFORMANCE DO'S AND DON'TS
# ═══════════════════════════════════════════

import pandas as pd
import numpy as np

# ✅ DO: Use vectorized operations
df['new_col'] = df['col1'] * df['col2']

# ❌ DON'T: Use loops
result = []
for i in range(len(df)):
    result.append(df.iloc[i]['col1'] * df.iloc[i]['col2'])

# ✅ DO: Use built-in pandas methods
df['col'].str.contains('pattern')

# ❌ DON'T: Use apply with lambda for simple operations
df['col'].apply(lambda x: 'pattern' in x)

# ✅ DO: Use query() for complex filters
filtered = df.query('age > 25 and income > 50000')

# ❌ DON'T: Chain multiple boolean operations inefficiently
filtered = df[(df['age'] > 25) & (df['income'] > 50000)]

# ✅ DO: Use category dtype for low-cardinality columns
df['category'] = df['category'].astype('category')

# ❌ DON'T: Keep high-cardinality columns as object
# (wastes memory)

# ✅ DO: Read only needed columns
df = pd.read_csv('file.csv', usecols=['col1', 'col2', 'col3'])

# ❌ DON'T: Load entire file if you only need subset
df = pd.read_csv('file.csv')
df = df[['col1', 'col2', 'col3']]

# ✅ DO: Use chaining with assign()
result = (df
    .assign(new_col=lambda x: x['col1'] * 2)
    .query('new_col > 10')
    .sort_values('new_col')
)

# ✅ DO: Profile your code to find bottlenecks
import cProfile
cProfile.run('slow_function()')

# ✅ DO: Use appropriate data structures
# - list: ordered, mutable, allows duplicates
# - tuple: ordered, immutable
# - set: unordered, no duplicates, fast lookup
# - dict: key-value pairs, fast lookup
```

---

### Version Control Best Practices 🔀

```bash
# ═══════════════════════════════════════════
# GIT BEST PRACTICES FOR DATA SCIENCE
# ═══════════════════════════════════════════

# .gitignore for data science projects
─────────────────────────────────────────────────────────────

# Python
__pycache__/
*.py[cod]
*$py.class
*.so
.Python
venv/
env/
*.egg-info/

# Jupyter Notebook
.ipynb_checkpoints
*/.ipynb_checkpoints/*

# Data (don't commit large datasets)
data/raw/*
data/processed/*
!data/raw/.gitkeep
!data/processed/.gitkeep

# Models (don't commit large model files)
models/*.pkl
models/*.h5
*.joblib

# IDE
.vscode/
.idea/
*.swp
*.swo

# OS
.DS_Store
Thumbs.db

# Logs
*.log
logs/

# Environment
.env
.env.local

# Reports (optional - depending on project)
reports/*.html
reports/*.pdf

═══════════════════════════════════════════════════════════

# Commit Message Format
─────────────────────────────────────────────────────────────

<type>: <subject>

<body>

<footer>

Types:
• feat: New feature
• fix: Bug fix
• docs: Documentation changes
• style: Code style changes (formatting)
• refactor: Code refactoring
• test: Adding tests
• chore: Maintenance tasks

Examples:
─────────────────────────────────────────────────────────────

✅ GOOD:
feat: add customer segmentation model

Implemented K-means clustering for customer segmentation.
- Added preprocessing pipeline
- Tuned number of clusters using elbow method
- Achieved silhouette score of 0.68

Closes #123

✅ GOOD:
fix: correct date parsing in data loader

Fixed bug where dates were parsed as strings instead of datetime.
This was causing errors in time-series analysis.

❌ BAD:
updated stuff

❌ BAD:
fix bug

═══════════════════════════════════════════════════════════
```

---

### Security Best Practices 🔒

```python
# ═══════════════════════════════════════════
# SECURITY IN DATA SCIENCE
# ═══════════════════════════════════════════

# ✅ DO: Use environment variables for secrets
import os
from dotenv import load_dotenv

load_dotenv()
API_KEY = os.getenv('API_KEY')
DATABASE_PASSWORD = os.getenv('DATABASE_PASSWORD')

# ❌ DON'T: Hardcode credentials
API_KEY = 'sk-1234567890abcdef'  # NEVER DO THIS!

# ✅ DO: Use .env file (and add to .gitignore)
"""
# .env file
API_KEY=your-api-key-here
DATABASE_URL=postgresql://user:password@localhost/db
AWS_ACCESS_KEY=your-aws-key
"""

# ✅ DO: Validate and sanitize user inputs
def load_user_data(filepath: str) -> pd.DataFrame:
    # Validate file path
    if not filepath.endswith('.csv'):
        raise ValueError("Only CSV files allowed")

    # Check file exists
    if not os.path.exists(filepath):
        raise FileNotFoundError(f"File not found: {filepath}")

    # Limit file size
    max_size = 100 * 1024 * 1024  # 100MB
    if os.path.getsize(filepath) > max_size:
        raise ValueError("File too large")

    return pd.read_csv(filepath)

# ✅ DO: Anonymize sensitive data
def anonymize_customer_data(df: pd.DataFrame) -> pd.DataFrame:
    """Remove or hash PII (Personally Identifiable Information)."""
    import hashlib

    df = df.copy()

    # Hash email addresses
    df['email_hash'] = df['email'].apply(
        lambda x: hashlib.sha256(x.encode()).hexdigest()
    )

    # Remove direct identifiers
    df = df.drop(['email', 'phone', 'ssn'], axis=1)

    return df

# ✅ DO: Use secure pickle alternatives for models
import joblib

# Save model
joblib.dump(model, 'model.joblib', compress=3)

# Load model
model = joblib.load('model.joblib')

# ❌ DON'T: Use pickle with untrusted data (security risk!)
```

---

### Collaboration Guidelines 🤝

```bash
# ═══════════════════════════════════════════
# TEAM COLLABORATION BEST PRACTICES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   CODE REVIEW ETIQUETTE                    ║
╚════════════════════════════════════════════════════════════╝

As a Reviewer:
─────────────────────────────────────────────────────────────
✅ Be constructive, not critical
✅ Ask questions, don't make demands
✅ Praise good solutions
✅ Provide specific suggestions
✅ Focus on code, not person
✅ Review promptly (within 24 hours)

Examples:
• "What do you think about using vectorization here for better performance?"
• "Nice solution! Have you considered edge case X?"
• "Could you add a docstring to explain the logic?"

As an Author:
─────────────────────────────────────────────────────────────
✅ Keep PRs small and focused
✅ Write clear PR descriptions
✅ Respond to all comments
✅ Don't take feedback personally
✅ Ask for clarification if unsure
✅ Thank reviewers for their time

╔════════════════════════════════════════════════════════════╗
║                   DOCUMENTATION STANDARDS                  ║
╚════════════════════════════════════════════════════════════╝

Every Analysis Should Include:
─────────────────────────────────────────────────────────────
1. Business Context
   • What problem are we solving?
   • Why is this important?
   • What's the expected impact?

2. Data Description
   • Data source and collection method
   • Time period covered
   • Number of records
   • Key variables

3. Methodology
   • Approach taken
   • Assumptions made
   • Models/techniques used
   • Why these choices?

4. Results
   • Key findings
   • Metrics and performance
   • Visualizations
   • Statistical significance

5. Conclusions & Recommendations
   • What did we learn?
   • What should we do?
   • What are the limitations?
   • What are next steps?

6. Appendix
   • Detailed technical notes
   • Code snippets
   • Additional charts
   • References

╔════════════════════════════════════════════════════════════╗
║                   MEETING BEST PRACTICES                   ║
╚════════════════════════════════════════════════════════════╝

Data Science Standups:
─────────────────────────────────────────────────────────────
• What did I accomplish yesterday?
• What will I work on today?
• What blockers do I have?
• What insights did I discover?

Model Review Meetings:
─────────────────────────────────────────────────────────────
• Present problem and approach
• Show EDA findings
• Explain model choice and hyperparameters
• Demonstrate performance metrics
• Discuss limitations and next steps
• Get feedback and approval
```

---

<div align="center">

## 🎓 Final Thoughts

</div>

### Remember These Principles 💡

```bash
╔════════════════════════════════════════════════════════════╗
║                   THE DATA SCIENCE MINDSET                 ║
╚════════════════════════════════════════════════════════════╝

1. Question Everything
   • Validate assumptions
   • Check data quality
   • Test edge cases
   • Verify results

2. Iterate Quickly
   • Start simple
   • Test hypotheses fast
   • Learn from failures
   • Refine continuously

3. Communicate Clearly
   • Explain to non-technical stakeholders
   • Visualize insights
   • Document your work
   • Tell a story with data

4. Stay Curious
   • Keep learning new techniques
   • Read research papers
   • Experiment with new tools
   • Share knowledge

5. Focus on Impact
   • Solve business problems
   • Measure outcomes
   • Deliver value
   • Think beyond accuracy

╔════════════════════════════════════════════════════════════╗
║                   QUALITY OVER SPEED                       ║
╚════════════════════════════════════════════════════════════╝

✅ Take time to understand the data
✅ Validate thoroughly
✅ Write clean, maintainable code
✅ Document your process
✅ Test your assumptions
✅ Consider ethical implications

"It's better to deliver a well-validated, explainable model
 later than a black-box model quickly."
```

---

<div align="center">

## 🎓 Learning Resources

</div>

### Essential Python Data Science Resources 📚

```
📘 Books
• Python for Data Analysis (Wes McKinney)
• Hands-On Machine Learning (Aurélien Géron)
• Python Data Science Handbook (Jake VanderPlas)
• Data Science from Scratch (Joel Grus)

📗 Online Courses
• DataCamp: Data Scientist with Python
• Coursera: Applied Data Science with Python
• Kaggle Learn: Python courses
• Fast.ai: Practical Deep Learning

📙 Documentation
• NumPy: https://numpy.org/doc/
• Pandas: https://pandas.pydata.org/docs/
• Matplotlib: https://matplotlib.org/stable/contents.html
• Seaborn: https://seaborn.pydata.org/
• Scikit-learn: https://scikit-learn.org/

🎥 YouTube Channels
• Corey Schafer (Python & Pandas)
• Keith Galli (Data Science)
• StatQuest (Statistics)
• 3Blue1Brown (Math visualization)
• sentdex (Python programming)

💻 Practice Platforms
• Kaggle: https://www.kaggle.com/
• DataCamp: https://www.datacamp.com/
• LeetCode: https://leetcode.com/
• HackerRank: https://www.hackerrank.com/

📊 Datasets
• Kaggle Datasets: https://www.kaggle.com/datasets
• UCI ML Repository: https://archive.ics.uci.edu/ml/
• Data.gov: https://data.gov/
• Google Dataset Search: https://datasetsearch.research.google.com/
• Awesome Public Datasets: https://github.com/awesomedata/awesome-public-datasets

🛠️ Tools
• Jupyter: https://jupyter.org/
• Google Colab: https://colab.research.google.com/
• VS Code: https://code.visualstudio.com/
• Anaconda: https://www.anaconda.com/

💬 Communities
• r/datascience: https://reddit.com/r/datascience
• r/learnpython: https://reddit.com/r/learnpython
• Stack Overflow: https://stackoverflow.com/questions/tagged/pandas
• Kaggle Forums: https://www.kaggle.com/discussion
• Data Science Discord servers
```

---

<div align="center">

## 📝 Quick Reference

</div>

### Common Operations Cheat Sheet 🚀

```python
# ═══════════════════════════════════════════
# PANDAS CHEAT SHEET
# ═══════════════════════════════════════════

import pandas as pd
import numpy as np

# Read data
df = pd.read_csv('file.csv')
df = pd.read_excel('file.xlsx')
df = pd.read_json('file.json')

# Quick look
df.head()                    # First 5 rows
df.tail()                    # Last 5 rows
df.info()                    # Data types and info
df.describe()                # Statistical summary
df.shape                     # (rows, columns)

# Selection
df['column']                 # Select column
df[['col1', 'col2']]        # Multiple columns
df.iloc[0]                   # First row
df.loc[0, 'column']         # Specific cell

# Filtering
df[df['age'] > 25]          # Simple filter
df[(df['age'] > 25) & (df['city'] == 'NYC')]  # Multiple conditions

# Aggregation
df['column'].sum()
df['column'].mean()
df['column'].median()
df.groupby('category')['value'].sum()

# Missing data
df.isnull().sum()           # Count missing
df.dropna()                 # Drop missing
df.fillna(0)                # Fill missing

# Sorting
df.sort_values('column')    # Sort by column
df.sort_values(['col1', 'col2'], ascending=[True, False])

# Apply function
df['new_col'] = df['old_col'].apply(lambda x: x * 2)

# Merge/Join
pd.merge(df1, df2, on='key')

# Pivot
df.pivot_table(values='value', index='row', columns='col', aggfunc='sum')

# ═══════════════════════════════════════════
# NUMPY CHEAT SHEET
# ═══════════════════════════════════════════

import numpy as np

# Create arrays
np.array([1, 2, 3])         # From list
np.zeros((3, 4))            # Zeros
np.ones((2, 3))             # Ones
np.arange(0, 10, 2)         # Range
np.linspace(0, 1, 5)        # Linear space
np.random.random((3, 3))    # Random

# Array operations
arr + 10                     # Add scalar
arr * 2                      # Multiply
arr ** 2                     # Power
arr1 + arr2                  # Element-wise

# Aggregations
arr.sum()
arr.mean()
arr.std()
arr.min()
arr.max()

# Reshaping
arr.reshape(3, 4)
arr.flatten()
arr.T                        # Transpose

# Indexing
arr[0]                       # First element
arr[1:3]                     # Slice
arr[arr > 5]                 # Boolean indexing

# ═══════════════════════════════════════════
# MATPLOTLIB CHEAT SHEET
# ═══════════════════════════════════════════

import matplotlib.pyplot as plt

# Basic plot
plt.plot(x, y)
plt.xlabel('X label')
plt.ylabel('Y label')
plt.title('Title')
plt.legend()
plt.show()

# Scatter
plt.scatter(x, y)

# Bar
plt.bar(categories, values)

# Histogram
plt.hist(data, bins=30)

# Subplots
fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(12, 5))
ax1.plot(x, y)
ax2.scatter(x, y)

# Save
plt.savefig('plot.png', dpi=300, bbox_inches='tight')
```

---

<div align="center">

## 🎯 Summary

</div>

### Key Takeaways 💡

```bash
╔════════════════════════════════════════════════════════════╗
║                   ESSENTIAL SKILLS                         ║
╚════════════════════════════════════════════════════════════╝

1. NumPy - Foundation
   • Fast numerical operations
   • Array manipulation
   • Linear algebra
   • Broadcasting

2. Pandas - Data Manipulation
   • DataFrames and Series
   • Data loading and cleaning
   • Aggregation and grouping
   • Merging and joining

3. Visualization
   • Matplotlib for basic plots
   • Seaborn for statistical viz
   • Plotly for interactivity

4. Statistics
   • Descriptive statistics
   • Hypothesis testing
   • Correlation and regression

5. Feature Engineering
   • Creating meaningful features
   • Encoding categorical variables
   • Scaling and normalization

6. Best Practices
   • Clean, documented code
   • Reproducibility
   • Version control
   • Testing

╔════════════════════════════════════════════════════════════╗
║                   WORKFLOW CHECKLIST                       ║
╚════════════════════════════════════════════════════════════╝

Every Data Science Project:
☐ 1. Define problem clearly
☐ 2. Collect and load data
☐ 3. Explore data (EDA)
☐ 4. Clean and preprocess
☐ 5. Engineer features
☐ 6. Build and train model
☐ 7. Evaluate performance
☐ 8. Communicate results
☐ 9. Deploy and monitor
☐ 10. Iterate and improve

Remember:
─────────────────────────────────────────────────────────────
📊 Data quality matters more than model complexity
🧹 Spend 80% time on data cleaning, 20% on modeling
📈 Visualize everything - EDA is crucial
🔄 Always validate assumptions
✅ Document your process
🧪 Test your code
🚀 Focus on business impact
```

---

<div align="center">

**Built with 🐍 by MrDib, for data enthusiasts**

_Remember: "Data is the new oil, but insights are the new gold"_ 💰

**Happy Analyzing!** 📊

</div>
