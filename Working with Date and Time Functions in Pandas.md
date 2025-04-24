# 📚 Working with Dates and Times in Pandas: Timestamp, DatetimeIndex, Period

Pandas provides a variety of functions to work with date and time-related data.

Objects such as `Timestamp`, `DatetimeIndex`, and `Period` are especially useful for handling and analyzing time-based data. This post covers the key features of each.

---

## 📚 Timestamp

A `Timestamp` represents a single point in time in Pandas.

It is similar to `datetime64`, but provides more functionality and supports time down to the nanosecond level.

### Example 1: Using a single value to create a Timestamp

```python
import pandas as pd

example1 = pd.Timestamp(1234.5678)  # Default is nanoseconds
example2 = pd.Timestamp(1234.5678, unit='D')  # Days

print(example1)
print(example2)
```

**Output:**

```
1970-01-01 00:00:00.000001234
1973-05-19 13:37:37.920000
```

---

## 📚 DatetimeIndex

`DatetimeIndex` is useful when working with multiple dates.  
It allows you to manage and manipulate a series of dates as an index.

### Example 2: Converting single and multiple dates

```python
import pandas as pd

example1 = pd.to_datetime('2023-11-1 12')  # Single date
example2 = pd.to_datetime(['2023-1-1', '2023-10-31'])  # Multiple dates

print(example1)
print(example2)
```

**Output:**

```
2023-11-01 12:00:00
DatetimeIndex(['2023-01-01', '2023-10-31'], dtype='datetime64[ns]', freq=None)
```

---

### Example 3: Automatically generating a range of dates

You can use `pd.date_range()` to create a range of dates over a given period.

```python
import pandas as pd

example = pd.date_range('2023-1-1', '2023-10-31')
print(example)
```

**Output:**  
Creates 304 dates from January 1 to October 31, 2023, by default on a daily frequency.

---

## 📚 Period and PeriodIndex

`Period` represents a time span (e.g., a month or a year), rather than a single moment.

Use this when you want to work with periods of time instead of timestamps.

### Example 4: Creating Periods

```python
import pandas as pd

example1 = pd.Period('2023-11-1')  # Default is daily
example2 = pd.Period('2023-11-1', freq='M')  # Monthly
example3 = pd.Period('2023-11-1', freq='Y')  # Yearly

print(example1)
print(example2)
print(example3)
print(type(example1))
```

**Output:**

```
2023-11-01
2023-11
2023
<class 'pandas._libs.tslibs.period.Period'>
```

---

### Example 5: Creating a range of periods

`pd.period_range()` can generate multiple period objects across a date range.

```python
import pandas as pd

example1 = pd.period_range('2023-1', '2023-11')  # Default: monthly
example2 = pd.period_range('2023-1', '2023-11', freq='M')  # Monthly
example3 = pd.period_range('2022-1', '2023-11', freq='Y')  # Yearly

print(example1)
print(example2)
print(example3)
print(type(example1))
```

**Output:**

```
PeriodIndex(['2023-01', '2023-02', ..., '2023-11'], dtype='period[M]', freq='M')
PeriodIndex(['2023-01', '2023-02', ..., '2023-11'], dtype='period[M]', freq='M')
PeriodIndex(['2022', '2023'], dtype='period[Y]', freq='Y')
<class 'pandas._libs.tslibs.period.Period'>
```

