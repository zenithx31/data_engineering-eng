# 📚 Series

A Series is a one-dimensional array with labeled indices.

```python
import pandas as pd

# Create a Series
sr = pd.Series([10000, 20000, 30000], index=['Hamburger', 'Chicken', 'Pizza'])

# Print Series
print(sr)

# Print values and index info
print('Value : {}'.format(sr.values))
print('Index : {}'.format(sr.index))
```

**Output:**
```
Hamburger    10000
Chicken      20000
Pizza        30000
dtype: int64

Value : [10000 20000 30000]
Index : Index(['Hamburger', 'Chicken', 'Pizza'], dtype='object')
```

- `sr.values`: Prints the values of the Series.
- `sr.index`: Prints the index labels of the Series.

---

# 📚 DataFrame

A DataFrame is a two-dimensional array made of rows and columns, similar to a table in Excel.

```python
import pandas as pd

# Create DataFrame from a 2D list
values = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
index = ['one', 'two', 'three']
columns = ['A', 'B', 'C']

df = pd.DataFrame(values, index=index, columns=columns)

# Print DataFrame
print(df)

# Print values, index, and columns
print('Value : {}'.format(df.values))
print('Index : {}'.format(df.index))
print('Columns : {}'.format(df.columns))
```

**Output:**
```
       A  B  C
one    1  2  3
two    4  5  6
three  7  8  9

Value : [[1 2 3]
 [4 5 6]
 [7 8 9]]
Index : Index(['one', 'two', 'three'], dtype='object')
Columns : Index(['A', 'B', 'C'], dtype='object')
```

---

# 📚 Creating DataFrames

## 1) Creating a DataFrame from a list

```python
import pandas as pd

# Create DataFrame from a list
data = [
    ['1000', 'A', 10],
    ['2000', 'B', 20],
    ['3000', 'C', 30]
]

df = pd.DataFrame(data)
print(df)
```

**Output:**
```
      0  1   2
0  1000  A  10
1  2000  B  20
2  3000  C  30
```

Use the `columns` parameter to name the columns.

```python
df = pd.DataFrame(data, columns=['Price', 'Name', 'Age'])
print(df)
```

**Output:**
```
  Price Name  Age
0  1000    A   10
1  2000    B   20
2  3000    C   30
```

## 2) Creating a DataFrame from a dictionary

```python
import pandas as pd

# Create DataFrame from a dictionary
data = {
    'Price': ['1000', '2000', '3000'],
    'Name': ['A', 'B', 'C'],
    'Age': [10, 20, 30]
}

df = pd.DataFrame(data)
print(df)
```

**Output:**
```
  Price Name  Age
0  1000    A   10
1  2000    B   20
2  3000    C   30
```

---

# 📚 Viewing a DataFrame

```python
# View first n rows
print(df.head(2))  # First 2 rows

# View last n rows
print(df.tail(2))  # Last 2 rows

# View a specific column
print(df['Price'])  # 'Price' column
```

---

# 📚 Reading External Data

Pandas can easily read external files (e.g., CSV) into a DataFrame.

```python
# Read a CSV file
df = pd.read_csv('example.csv')
print(df)
```
