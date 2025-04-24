# 📚 1D Array

Using NumPy, you can easily convert a Python list into an array and perform fast operations on the array.  
NumPy arrays are optimized for efficient computation and can handle mathematical operations very quickly.

## Example 1: Creating a 1D Array

```python
import numpy as np

data = [1, 2, 3]
arr = np.array(data)
print(arr)
print(type(arr))
```

**Output:**
```
[1 2 3]
<class 'numpy.ndarray'>
```

In the code above, the list `data` is converted into a NumPy array, and then we print the array and check its data type.  
A NumPy array is of the type `numpy.ndarray`.

---

## Example 2: Apply an Operation to All Elements

NumPy allows you to apply operations to all elements in an array without using loops.

```python
import numpy as np

data = [1, 2, 3]
arr = np.array(data)
result = arr * 10
print(result)
```

**Output:**
```
[10 20 30]
```

The code above multiplies each element of the array by 10.  
NumPy performs this efficiently using vectorized operations.

---

# 📚 2D Array

With NumPy, you can create 2D arrays and easily select specific elements.  
NumPy arrays are also very useful for matrix operations.

## Example 1: Creating a 2D Array

```python
import numpy as np

data = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

arr = np.array(data)
print(arr)
```

**Output:**
```
[[1 2 3]
 [4 5 6]
 [7 8 9]]
```

---

## Example 2: Selecting Specific Elements

To access a specific element in a 2D array, use the format `arr[row, column]`.

```python
print(arr[:, 0])
```

**Output:**
```
[1 4 7]
```

In the code above, `:` selects all rows, and `0` refers to the first column.  
This results in the values of the first column being printed.
