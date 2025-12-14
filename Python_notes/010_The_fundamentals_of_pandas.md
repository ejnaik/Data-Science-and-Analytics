# Pandas: Data Structures and Selection

## Primary Data Structures
Pandas has two primary data structures: **Series** and **DataFrame**.

* **Series:** A Series is a one-dimensional labeled array that can hold any data type. It’s similar to a column in a spreadsheet or a one-dimensional NumPy array. Each element in a series has an associated label called an *index*. The index allows for more efficient and intuitive data manipulation by making it easier to reference specific elements of your data.
* **DataFrame:** A dataframe is a two-dimensional labeled data structure—essentially a table or spreadsheet—where each column and row is represented by a Series.

## Create a DataFrame
To use pandas in your notebook, first import it. Similar to NumPy, pandas has its own standard alias, `pd`, that’s used by data professionals around the world:

```python
import pandas as pd
import numpy as np

data = {'Column A': [1, 2], 'Column B': [3, 4]}
df_dict = pd.DataFrame(data)
print(df_dict)
```
```
   col1  col2
0     1     3
1     2     4
```
From a numpy array:
```python

df2 = pd.DataFrame(np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]]),
                  columns=['a', 'b', 'c'])
df2
```
```
Output:
   a  b  c
0  1  2  3
1  4  5  6
2  7  8  9
```

**From a comma-separated values (csv) file:**
```python
df3 = pd.read_csv('/file_path/file_name.csv'
```
**Attributes and methods**

The ```DataFrame``` class is powerful and convenient because it comes with a suite of built-in features that simplify common data analysis tasks. These features are known as attributes and methods. An attribute is a value associated with an object or class that is referenced by name using dotted expressions. A method is a function that is defined inside a class body and typically performs an action. A simpler way of thinking about the distinction between attributes and methods is to remember that attributes are characteristics of the object, while methods are actions or operations. 

**Common DataFrame attributes**

Data professionals use attributes and methods constantly. Some of the most-used DataFrame attributes include:

### Common DataFrame Attributes

| Attribute | Description |
|-----------|-------------|
| `columns` | Returns column labels |
| `dtypes` | Returns data types of columns |
| `iloc` | Integer-based row/column selection |
| `loc` | Label-based row/column selection |
| `shape` | Returns dimensions of the dataframe |
| `values` | Returns NumPy array representation |

### Common DataFrame Methods

| Method | Description |
|--------|-------------|
| `apply()` | Applies a function across an axis |
| `copy()` | Creates a copy of the dataframe |
| `describe()` | Summary statistics |
| `drop()` | Removes rows or columns |
| `groupby()` | Groups data for aggregation |
| `head()` | Returns first n rows |
| `info()` | Displays dataframe summary |
| `isna()` | Detects missing values |
| `sort_values()` | Sorts values |
| `value_counts()` | Counts unique values |
| `where()` | Conditional replacement |

### Selection Statements

### Row Selection

Rows can be selected using index labels (`loc[]`) or integer positions (`iloc[]`).

#### Using `loc[]` (Label-Based)

```python
import pandas as pd

df = pd.DataFrame({
    'A': ['alpha', 'apple', 'arsenic', 'angel', 'android'],
    'B': [1, 2, 3, 4, 5],
    'C': ['coconut', 'curse', 'cassava', 'cuckoo', 'clarinet'],
    'D': [6, 7, 8, 9, 10]
}, index=['row_0', 'row_1', 'row_2', 'row_3', 'row_4'])
```
### Select a single row
```python
df.loc['row_1']
```
### Select multiple rows
```python
df.loc[['row_2', 'row_4']]
```
### Select a range (inclusive)
```python
df.loc['row_0':'row_3']
```
### Using iloc[] (Integer-Based)

```python
# Select single row
df.iloc[1]

# Select multiple rows
```python
df.iloc[[0, 2, 4]]

# Select a range (exclusive end)
```python
df.iloc[0:3]
```
Column Selection
Bracket Notation (Preferred)
```python
# Single column
df['C']
```
### Multiple columns
```python
df[['A', 'C']]
Dot Notation
```python
df.A  # Not recommended for clarity and reliability
```
Column Selection with loc[]
```python
df.loc[:, ['B', 'D']]
```
Column Selection with iloc[]
```python
df.iloc[:, [1, 3]]
Selecting Rows and Columns Together
Using loc[]
```python
df.loc['row_0':'row_2', ['A', 'C']]
Using iloc[]
```python
df.iloc[[2, 4], 0:3]
```
Important Considerations
### Mixing Index Types
Mixing numeric and named indices is not allowed:

### This will raise an error with named indices
df.loc[0:3, ['D']]  # Error: "cannot do slice indexing on <class 'pandas.core.indexes.base.Index'> with these indexers [0] of <class 'int'>"
Correct approaches:

```python
# For viewing
df.iloc[0:3][['D']]
```
### Best practice for manipulation
```python
df.loc[df.index[0:3], 'D']
```
DataFrames with Numeric Indices
When using default numeric indices:

```python
df_numeric = pd.DataFrame({
    'A': ['alpha', 'apple', 'arsenic', 'angel', 'android'],
    'B': [1, 2, 3, 4, 5],
    'C': ['coconut', 'curse', 'cassava', 'cuckoo', 'clarinet'],
    'D': [6, 7, 8, 9, 10]
})
```
### This works with numeric indices
```python
df_numeric.loc[0:3, ['D']]
```
Practical Examples
Example DataFrame Creation
```python
import pandas as pd
import numpy as np
```
#### Create sample DataFrame
```python
data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Eva'],
    'Age': [25, 30, 35, 28, 32],
    'Salary': [50000, 60000, 75000, 52000, 68000],
    'Department': ['HR', 'IT', 'IT', 'HR', 'Finance']
}

df_example = pd.DataFrame(data)
df_example.set_index('Name', inplace=True)
print(df_example)
```
### Using DataFrame Methods
```python
# Get summary statistics

```python
df_example.describe()
```
### Get data types
```python
df_example.dtypes
```
### Get shape
```python
df_example.shape
```
### Check for missing values
```python
df_example.isna()
```
### Sort values
```python
df_example.sort_values('Salary', ascending=False)
```
### Apply a function
```python
df_example['Salary_in_k'] = df_example['Salary'].apply(lambda x: x/1000)
```
Complex Selections
python
### Select IT department employees
```python
it_employees = df_example.loc[df_example['Department'] == 'IT']
```
### Select employees aged 30-35
```python
young_employees = df_example.loc[(df_example['Age'] >= 30) & (df_example['Age'] <= 35)]
```
### Select specific columns for HR department
```python
hr_data = df_example.loc[df_example['Department'] == 'HR', ['Age', 'Salary']]
```
###  Using iloc for numeric selection
```python
first_two_employees = df_example.iloc[0:2]
```
### Key Takeaways
- Pandas DataFrames are ideal for tabular data manipulation

- Rows and columns are pandas Series objects when selected individually

- DataFrames provide rich attributes and methods for data analysis

- loc[] and iloc[] are essential tools for data selection

- Consistent practice leads to mastery of pandas operations

### Best Practices
- Use bracket notation over dot notation for column selection

- Choose loc[] for label-based indexing and iloc[] for integer-based indexing

- Be mindful of index types when performing selections

- Create copies of DataFrames when needed to avoid modifying original data

- Use descriptive index names for better code readability
