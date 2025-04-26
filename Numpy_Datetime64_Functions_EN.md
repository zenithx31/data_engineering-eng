# Working with datetime64 in NumPy

## 📚 What is datetime64?

`datetime64` is a data type in NumPy designed for handling dates and times with high precision.

It allows representing and calculating dates and times in various units (e.g., year, month, day, second, millisecond, etc.).  
While Python's standard `datetime` module supports up to microseconds (10^-6 seconds), NumPy's `datetime64` can handle down to attoseconds (10^-18 seconds).

---

## 📚 Creating Dates Using NumPy Objects

You can create dates or times using `datetime64` objects in NumPy.

Different units such as day, second, or nanosecond can be specified.

```python
import numpy as np

example1 = np.datetime64('2023-11-08')  # Create date '2023-11-08'
example2 = np.datetime64(100000, 'ns')  # 100,000 nanoseconds
example3 = np.datetime64(100000, 's')   # 100,000 seconds
example4 = np.datetime64(100000, 'D')   # 100,000 days

print(example1)
print(example2)
print(example3)
print(example4)
```

- `example1`: Creates the date 2023-11-08.
- `example2`: 100,000 nanoseconds from the epoch (1970-01-01).
- `example3`: 100,000 seconds corresponds to 1970-01-02 03:46:40.
- `example4`: 100,000 days corresponds to approximately 2243-10-17.

---

## 📚 Creating Dates Using NumPy's array() Function

You can create arrays with `datetime64` type.

Different units such as year, month, and day can be specified.

```python
import numpy as np

example1 = np.array('2023-11-08', dtype='datetime64')     # Default date
example2 = np.array('2023-11-08', dtype='datetime64[D]')   # Day precision
example3 = np.array('2023-11-08', dtype='datetime64[M]')   # Month precision
example4 = np.array('2023-11-08', dtype='datetime64[Y]')   # Year precision

print(example1)
print(example2)
print(example3)
print(example4)
```

- `example1`: Basic full date format.
- `example2`: Day unit; displays full date.
- `example3`: Month unit; displays year and month only.
- `example4`: Year unit; displays year only.

---

## 📚 Creating Date Ranges Using arange()

Using `np.arange()`, you can create a range of dates at a specified interval.

```python
import numpy as np

example1 = np.arange('2023-10', '2023-11', dtype='datetime64[D]')  # Daily
example2 = np.arange('2023-10', '2023-11', dtype='datetime64[W]')  # Weekly
example3 = np.arange('2023-10', '2023-11', dtype='datetime64[M]')  # Monthly
example4 = np.arange('2022-10', '2023-11', dtype='datetime64[Y]')  # Yearly
example5 = np.arange('2023-11-07', '2023-11-08', dtype='datetime64[h]')  # Hourly
example6 = np.arange('2023-11-07', '2023-11-08', dtype='datetime64[m]')  # Minutely
example7 = np.arange('2023-11-07', '2023-11-08', dtype='datetime64[s]')  # Secondly

print(example1)
print(example2)
print(example3)
print(example4)
print(example5)
print(example6)
print(example7)
```

- `example1`: Dates from Oct 1 to Oct 31, 2023 (daily).
- `example2`: Dates at weekly intervals from Sep 28 to Oct 19, 2023.
- `example3`: Monthly range for October 2023.
- `example4`: Yearly range from 2022 to 2023.
- `example5`: Hourly timestamps between Nov 7 and Nov 8, 2023.
- `example6`: Minute-level timestamps between Nov 7 and Nov 8, 2023.
- `example7`: Second-level timestamps between Nov 7 and Nov 8, 2023.

---

## 📚 Calculating Differences Between Dates

You can subtract two `datetime64` objects to find the difference between them.

```python
import numpy as np

example = np.datetime64('2023-11') - np.datetime64('2023-01')
print(example)  # Output: 10 months
```

The result shows the difference between two dates in months.  
NumPy can calculate differences in terms of years, months, days, and so on.
