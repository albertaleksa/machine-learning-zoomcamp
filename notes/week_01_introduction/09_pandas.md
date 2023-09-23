>[Back to Week Menu](README.md)
>
>Previous Theme: [Linear Algebra Refresher](08_linear_algebra.md)
>
>Next Theme: [Summary](10_summary.md)

## Introduction to Pandas
_[Video source](https://www.youtube.com/watch?v=0j3XK5PsnxA&list=PL3MmuxUbc_hIhxl5Ji8t4O6lPAOpHaCLR&index=9)_


### Import pandas

```
import pandas as pd
```

### DataFrames

Create dataframe (table) with specific columns:
```
df = pd.DataFrame(data, columns=columns)
```

**data** can be a list of lists or list of dictionaries.

Return n-first rows:
```
df.head(n=2)
```

![head](images/09_pandas_01_head.png)

### Series

Dataframe consists of Series (columns). Every column is a Series.
To get specific Series we can use '.'-notation or put name of Series in brackets:
```
df.Make
df['Make']
```

![series](images/09_pandas_02_series.png)

Add column into Dataframe:
```
df['id'] = [1, 2, 3, 4, 5]
```

![series2](images/09_pandas_03_series2.png)

Delete column from Dataframe:
```
del df['id']
```

### Index

```
df.index
>> RangeIndex(start=0, stop=5, step=1)
```

### Accessing elements

Get rows by index:
```
df.loc[1]
df.loc[[1, 2]]
```
![index](images/09_pandas_04_index.png)
![index2](images/09_pandas_05_index2.png)

Replace index:
```
df.index = ['a', 'b', 'c', 'd', 'e']
```

Get elements by **positional index**:
```
df.iloc[[1, 2]]
```

Reset index and doesn't change Dataframe:
```
df.reset_index()
```

Reset index and drop previous index and doesn't change Dataframe:
```
df.reset_index(drop=True)
```

Rest index and save to Dataframe:
```
df = df.reset_index(drop=True)
```

### Element-wise operations

Opearations with all Series (columns):

![oper](images/09_pandas_06_oper.png)

Logical opeartors:

![logical](images/09_pandas_07_logical.png)

### Filtering

![filtering](images/09_pandas_08_filtering.png)

Combain filtering:
![Combain](images/09_pandas_09_Combain.png)

### String operations

To lower case:
```
'STRr'.lower()
>> 'strr'
```

Replace:
```
'machine learning'.replace(' ', '_')
>> 'machine_learning'
```

![str](images/09_pandas_10_str.png)

### Summarizing operations

Operations min(), max(), mean()

![summarizing](images/09_pandas_11_summarizing.png)

Provide summary statistic about column:

![desc](images/09_pandas_12_desc.png)

Provide summary statistic for all numerical columns in Dataframe:

![desc_table](images/09_pandas_13_desc_table.png)

Count unique values:

![unique](images/09_pandas_14_unique.png)

### Missing values

Find missing values (NaN), return True if the value is Nan:

![missing](images/09_pandas_15_missing.png)

Count the number of missing values (NaN) in each column:

![missing_sum](images/09_pandas_16_missing_sum.png)

### Grouping

![grouping](images/09_pandas_17_grouping.png)

### Getting the NumPy arrays

To get the underlying NumPy array (use .values):

![values](images/09_pandas_18_values.png)

Convert DataFrame to list of dictionaries (per record):

```
df.to_dict(orient='records')
```

![dict](images/09_pandas_19_dict.png)


_[Back to the top](#introduction-to-pandas)_