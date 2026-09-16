Creating large sequences is a common task in data processing. This page compares the time taken to create sequences of equal length using native Python versus NumPy. In each case we will create the sequence a large number of times so we can measure the performance more accurately.

# Native Python

The following code creates a list of zeros in Python. If you're not familiar with the exact syntax used don't worry - the important feature is that it is an efficient way to create a large sequence of zeros.

```py-cell
import time
import numpy as np

repetitions = 1000

start_time = time.time()
for i in range(repetitions):
  a = [0] * 100000
print('Non-NumPy zeroes:', time.time() - start_time)
```

# NumPy

The following code creates an array of zeros using NumPy. 

```py-cell
start_time = time.time()
for i in range(repetitions):
  a = np.zeros(100000)
print('NumPy zeroes:', time.time() - start_time)
```

# Observations

The NumPy Version should run a lot faster, by a factor of around X.

## Why is NumPy Faster?

NumPy's array creation functions like `np.zeros()` and `np.arange()` are implemented in optimised compiled code, not in Python. This allows them to create large arrays much faster than native Python list operations. 