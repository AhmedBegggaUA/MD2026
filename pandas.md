#  Pandas


In this section, we will learn how use Pandas library. Pandas is the most commonly used library for data structures and data analysis in Python. It is built on top of NumPy, which is a library for numerical computation. Pandas is a powerful library that provides a wide range of methods for data manipulation and analysis. It is widely used in data science, machine learning, and other fields that require data analysis. So, let's get started with Pandas!

## Creating DataFrames

A DataFrame is a two-dimensional labeled data structure with columns of potentially different types. You can think of it like a spreadsheet or SQL table, or a dictionary of Series objects. DataFrames are the most commonly used data structures in Pandas. You can create a DataFrame from a dictionary, a list of dictionaries, a list of lists, or a NumPy array. Let's see some examples of creating DataFrames.

### Creating a DataFrame from a dictionary

You can create a DataFrame from a dictionary using the `pd.DataFrame()` function. The keys of the dictionary will be the column names, and the values will be the column values. Let's see an example.

```python
import pandas as pd

# Create a dictionary
data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Emily'],
    'Age': [25, 30, 35, 40, 45],
    'City': ['New York', 'Los Angeles', 'Chicago', 'Houston', 'Phoenix']
}

# Create a DataFrame from the dictionary
df = pd.DataFrame(data)

# Display the DataFrame
print(df)
```

Output:
```
      Name  Age         City
0    Alice   25     New York
1      Bob   30  Los Angeles
2  Charlie   35      Chicago
3    David   40      Houston
4    Emily   45      Phoenix
```

In this example, we created a DataFrame from a dictionary with three columns: `Name`, `Age`, and `City`. The keys of the dictionary became the column names, and the values became the column values.

### Creating a DataFrame from a list of dictionaries

You can also create a DataFrame from a list of dictionaries. Each dictionary in the list will become a row in the DataFrame. Let's see an example.

```python
import pandas as pd

# Create a list of dictionaries
data = [
    {'Name': 'Alice', 'Age': 25, 'City': 'New York'},
    {'Name': 'Bob', 'Age': 30, 'City': 'Los Angeles'},
    {'Name': 'Charlie', 'Age': 35, 'City': 'Chicago'},
    {'Name': 'David', 'Age': 40, 'City': 'Houston'},
    {'Name': 'Emily', 'Age': 45, 'City': 'Phoenix'}
]

# Create a DataFrame from the list of dictionaries
df = pd.DataFrame(data)

# Display the DataFrame
print(df)
```

Output:
```
      Name  Age         City
0    Alice   25     New York
1      Bob   30  Los Angeles
2  Charlie   35      Chicago
3    David   40      Houston
4    Emily   45      Phoenix
```

In this example, we created a DataFrame from a list of dictionaries with three columns: `Name`, `Age`, and `City`. Each dictionary in the list became a row in the DataFrame.

### Creating a DataFrame from a list of lists

You can also create a DataFrame from a list of lists. Each list in the list will become a row in the DataFrame. Let's see an example.

```python
import pandas as pd

# Create a list of lists

data = [
    ['Alice', 25, 'New York'],
    ['Bob', 30, 'Los Angeles'],
    ['Charlie', 35, 'Chicago'],
    ['David', 40, 'Houston'],
    ['Emily', 45, 'Phoenix']
]

# Create a DataFrame from the list of lists
df = pd.DataFrame(data, columns=['Name', 'Age', 'City'])

# Display the DataFrame
print(df)
```

Output:
```
      Name  Age         City
0    Alice   25     New York
1      Bob   30  Los Angeles
2  Charlie   35      Chicago
3    David   40      Houston
4    Emily   45      Phoenix
```

In this example, we created a DataFrame from a list of lists with three columns: `Name`, `Age`, and `City`. Each list in the list became a row in the DataFrame.

### Creating a DataFrame from a NumPy array

You can also create a DataFrame from a NumPy array. Let's see an example.

```python
import pandas as pd
import numpy as np

# Create a NumPy array
data = np.array([
    ['Alice', 25, 'New York'],
    ['Bob', 30, 'Los Angeles'],
    ['Charlie', 35, 'Chicago'],
    ['David', 40, 'Houston'],
    ['Emily', 45, 'Phoenix']
])

# Create a DataFrame from the NumPy array
df = pd.DataFrame(data, columns=['Name', 'Age', 'City'])

# Display the DataFrame
print(df)
```

Output:
```
      Name Age         City
0    Alice  25     New York
1      Bob  30  Los Angeles
2  Charlie  35      Chicago
3    David  40      Houston
4    Emily  45      Phoenix
```

In this example, we created a DataFrame from a NumPy array with three columns: `Name`, `Age`, and `City`. Each row in the NumPy array became a row in the DataFrame.

## Accessing DataFrames

Once you have created a DataFrame, you can access its data using various methods. You can access individual columns, rows, or cells of the DataFrame. Let's see some examples of accessing DataFrames.

### Accessing individual columns

You can access individual columns of a DataFrame using the column name. Let's see an example.

```python
import pandas as pd

# Create a DataFrame
data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Emily'],
    'Age': [25, 30, 35, 40, 45],
    'City': ['New York', 'Los Angeles', 'Chicago', 'Houston', 'Phoenix']
}
df = pd.DataFrame(data)

# Access the 'Name' column
print(df['Name'])
```

Output:
```
0      Alice
1        Bob
2    Charlie
3      David
4      Emily
Name: Name, dtype: object
```

In this example, we accessed the `Name` column of the DataFrame using the column name.

### Accessing individual rows

You can access individual rows of a DataFrame using the `iloc[]` method. Let's see an example.

```python
import pandas as pd

# Create a DataFrame
data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Emily'],
    'Age': [25, 30, 35, 40, 45],
    'City': ['New York', 'Los Angeles', 'Chicago', 'Houston', 'Phoenix']
}
df = pd.DataFrame(data)

# Access the first row
print(df.iloc[0])
```

Output:
```
Name        Alice
Age            25
City     New York
Name: 0, dtype: object
```

In this example, we accessed the first row of the DataFrame using the `iloc[]` method.

### Accessing individual cells

You can access individual cells of a DataFrame using the `iloc[]` method. Let's see an example.

```python
import pandas as pd

# Create a DataFrame
data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Emily'],
    'Age': [25, 30, 35, 40, 45],
    'City': ['New York', 'Los Angeles', 'Chicago', 'Houston', 'Phoenix']
}
df = pd.DataFrame(data)

# Access the cell at row 0 and column 'Name'
print(df.iloc[0]['Name'])
```

Output:
```
Alice
```

In this example, we accessed the cell at row 0 and column `Name` of the DataFrame using the `iloc[]` method.


## Operations on DataFrames

Once you have created a DataFrame, you can perform various operations on it. You can perform operations like filtering, sorting, grouping, and aggregating on the DataFrame. Let's see some examples of operations on DataFrames.

### Filtering DataFrames

You can filter a DataFrame to select rows that satisfy a certain condition. Let's see an example.

```python
import pandas as pd

# Create a DataFrame
data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Emily'],
    'Age': [25, 30, 35, 40, 45],
    'City': ['New York', 'Los Angeles', 'Chicago', 'Houston', 'Phoenix']
}
df = pd.DataFrame(data)

# Filter the DataFrame to select rows where Age is greater than 30
filtered_df = df[df['Age'] > 30]

# Display the filtered DataFrame
print(filtered_df)
```

Output:
```
    Name  Age     City
2  Charlie   35  Chicago
3    David   40  Houston
4    Emily   45  Phoenix
```

In this example, we filtered the DataFrame to select rows where `Age` is greater than 30.

### Sorting DataFrames

You can sort a DataFrame by one or more columns. Let's see an example.

```python
import pandas as pd

# Create a DataFrame

data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Emily'],
    'Age': [25, 30, 35, 40, 45],
    'City': ['New York', 'Los Angeles', 'Chicago', 'Houston', 'Phoenix']
}
df = pd.DataFrame(data)

# Sort the DataFrame by Age in descending order
sorted_df = df.sort_values(by='Age', ascending=False)

# Display the sorted DataFrame
print(sorted_df)
```

Output:
```
      Name  Age         City
4    Emily   45      Phoenix
3    David   40      Houston
2  Charlie   35      Chicago
1      Bob   30  Los Angeles
0    Alice   25     New York
```

In this example, we sorted the DataFrame by `Age` in descending order.

### Statistics on DataFrames

You can perform various statistical operations on a DataFrame, such as mean, median, sum, min, max, etc. Let's see an example.

```python
import pandas as pd

# Create a DataFrame
data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Emily'],
    'Age': [25, 30, 35, 40, 45],
    'City': ['New York', 'Los Angeles', 'Chicago', 'Houston', 'Phoenix']
}
df = pd.DataFrame(data)

# Calculate the mean of Age
mean_age = df['Age'].mean()

# Display the mean of Age
print(mean_age)
```

Output:
```
35.0
```

In this example, we calculated the mean of `Age` in the DataFrame.


## Adding and Removing Columns

You can add and remove columns from a DataFrame. Let's see some examples of adding and removing columns from DataFrames.

### Adding a column


You can add a new column to a DataFrame using the `[]` operator. Let's see an example.

```python
import pandas as pd

# Create a DataFrame
data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Emily'],
    'Age': [25, 30, 35, 40, 45],
    'City': ['New York', 'Los Angeles', 'Chicago', 'Houston', 'Phoenix']
}
df = pd.DataFrame(data)

# Add a new 
column df['Country'] = ['USA', 'USA', 'USA', 'USA', 'USA']

# Display the DataFrame
print(df)
```

Output:
```
      Name  Age         City Country
0    Alice   25     New York     USA
1      Bob   30  Los Angeles     USA
2  Charlie   35      Chicago     USA
3    David   40      Houston     USA
4    Emily   45      Phoenix     USA
```

In this example, we added a new column `Country` to the DataFrame.

### Removing a column

You can remove a column from a DataFrame using the `drop()` method. Let's see an example.

```python
import pandas as pd

# Create a DataFrame
data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Emily'],
    'Age': [25, 30, 35, 40, 45],
    'City': ['New York', 'Los Angeles', 'Chicago', 'Houston', 'Phoenix']
}
df = pd.DataFrame(data)

# Remove the 'City' column

df = df.drop('City', axis=1)

# Display the DataFrame
print(df)
```

Output:
```
      Name  Age
0    Alice   25
1      Bob   30
2  Charlie   35
3    David   40
4    Emily   45
```

In this example, we removed the `City` column from the DataFrame.

## Adding and Removing Rows

You can add and remove rows from a DataFrame. Let's see some examples of adding and removing rows from DataFrames.

### Adding a row

You can add a new row to a DataFrame using the `loc[]` method. Let's see an example.

```python
import pandas as pd

# Create a DataFrame
data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Emily'],
    'Age': [25, 30, 35, 40, 45],
    'City': ['New York', 'Los Angeles', 'Chicago', 'Houston', 'Phoenix']
}
df = pd.DataFrame(data)

# Add a new row
df.loc[5] = ['Frank', 50, 'Las Vegas']

# Display the DataFrame
print(df)
```

Output:
```
      Name  Age         City
0    Alice   25     New York
1      Bob   30  Los Angeles
2  Charlie   35      Chicago
3    David   40      Houston
4    Emily   45      Phoenix
5    Frank   50    Las Vegas
```

In this example, we added a new row to the DataFrame.

### Removing a row

You can remove a row from a DataFrame using the `drop()` method. Let's see an example.

```python
import pandas as pd

# Create a DataFrame
data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Emily'],
    'Age': [25, 30, 35, 40, 45],
    'City': ['New York', 'Los Angeles', 'Chicago', 'Houston', 'Phoenix']
}
df = pd.DataFrame(data)

# Remove the row at index 2
df = df.drop(2)

# Display the DataFrame
print(df)
```

Output:
```
    Name  Age         City
0  Alice   25     New York
1    Bob   30  Los Angeles
3  David   40      Houston
4  Emily   45      Phoenix
```

In this example, we removed the row at index 2 from the DataFrame.
## Iterating over DataFrames

You can iterate over a DataFrame to access its rows and columns. Let's see some examples of iterating over DataFrames.

### Iterating over rows

You can iterate over the rows of a DataFrame using the `iterrows()` method. Let's see an example.

```python
import pandas as pd

# Create a DataFrame
data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Emily'],
    'Age': [25, 30, 35, 40, 45],
    'City': ['New York', 'Los Angeles', 'Chicago', 'Houston', 'Phoenix']
}
df = pd.DataFrame(data)

# Iterate over the rows of the DataFrame
for index, row in df.iterrows():
    print(index, row['Name'], row['Age'], row['City'])
```

Output:
```
0 Alice 25 New York
1 Bob 30 Los Angeles
2 Charlie 35 Chicago
3 David 40 Houston
4 Emily 45 Phoenix
```

In this example, we iterated over the rows of the DataFrame to access the `Name`, `Age`, and `City` columns of each row.

### Iterating over columns

You can iterate over the columns of a DataFrame using the `iteritems()` method. Let's see an example.

```python
import pandas as pd

# Create a DataFrame
data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Emily'],
    'Age': [25, 30, 35, 40, 45],
    'City': ['New York', 'Los Angeles', 'Chicago', 'Houston', 'Phoenix']
}
df = pd.DataFrame(data)

# Iterate over the columns of the DataFrame
for column, values in df.iteritems():
    print(column, values.values)
```

Output:
```
Name ['Alice' 'Bob' 'Charlie' 'David' 'Emily']
Age [25 30 35 40 45]
City ['New York' 'Los Angeles' 'Chicago' 'Houston' 'Phoenix']
```

In this example, we iterated over the columns of the DataFrame to access the values of each column.

## Merging DataFrames

You can merge two or more DataFrames into a single DataFrame. Let's see some examples of merging DataFrames.

### Merging two DataFrames

You can merge two DataFrames into a single DataFrame using the `merge()` method. Let's see an example.

```python
import pandas as pd

# Create the first DataFrame

data1 = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Emily'],
    'Age': [25, 30, 35, 40, 45]
}
df1 = pd.DataFrame(data1)

# Create the second DataFrame

data2 = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Emily'],
    'City': ['New York', 'Los Angeles', 'Chicago', 'Houston', 'Phoenix']
}
df2 = pd.DataFrame(data2)

# Merge the two DataFrames
df = pd.merge(df1, df2, on='Name')

# Display the merged DataFrame
print(df)
```

Output:
```
      Name  Age         City
0    Alice   25     New York
1      Bob   30  Los Angeles
2  Charlie   35      Chicago
3    David   40      Houston
4    Emily   45      Phoenix
```

In this example, we merged two DataFrames `df1` and `df2` into a single DataFrame `df` using the `merge()` method.

### Merging multiple DataFrames

You can merge multiple DataFrames into a single DataFrame using the `merge()` method. Let's see an example.

```python
import pandas as pd

# Create the first DataFrame

data1 = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Emily'],
    'Age': [25, 30, 35, 40, 45]
}
df1 = pd.DataFrame(data1)

# Create the second DataFrame

data2 = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Emily'],
    'City': ['New York', 'Los Angeles', 'Chicago', 'Houston', 'Phoenix']
}
df2 = pd.DataFrame(data2)

# Create the third DataFrame

data3 = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Emily'],
    'Country': ['USA', 'USA', 'USA', 'USA', 'USA']
}
df3 = pd.DataFrame(data3)

# Merge the three DataFrames
df = pd.merge(df1, df2, on='Name')
df = pd.merge(df, df3, on='Name')

# Display the merged DataFrame
print(df)
```

Output:
```
      Name  Age         City Country
0    Alice   25     New York     USA
1      Bob   30  Los Angeles     USA
2  Charlie   35      Chicago     USA
3    David   40      Houston     USA
4    Emily   45      Phoenix     USA
```

In this example, we merged three DataFrames `df1`, `df2`, and `df3` into a single DataFrame `df` using the `merge()` method.

## Grouping and Aggregating DataFrames

You can group a DataFrame by one or more columns and perform aggregations on the groups. Let's see some examples of grouping and aggregating DataFrames.

### Grouping and aggregating by one column

You can group a DataFrame by one column and perform aggregations on the groups using the `groupby()` method. Let's see an example.

```python
import pandas as pd

# Create a DataFrame

data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Emily'],
    'Age': [25, 30, 35, 40, 45],
    'City': ['New York', 'Los Angeles', 'Chicago', 'Houston', 'Phoenix']
}
df = pd.DataFrame(data)

# Group the DataFrame by City and calculate the mean of Age for each group
grouped_df = df.groupby('City').agg({'Age': 'mean'})

# Display the grouped and aggregated DataFrame
print(grouped_df)
```

Output:
```
             Age
City
Chicago       35
Houston       40
Los Angeles   30
New York      25
Phoenix       45
```

In this example, we grouped the DataFrame by `City` and calculated the mean of `Age` for each group.

### Grouping and aggregating by multiple columns

You can group a DataFrame by multiple columns and perform aggregations on the groups using the `groupby()` method. Let's see an example.

```python
import pandas as pd

# Create a DataFrame

data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Emily'],
    'Age': [25, 30, 35, 40, 45],
    'City': ['New York', 'Los Angeles', 'Chicago', 'Houston', 'Phoenix']
}
df = pd.DataFrame(data)

# Group the DataFrame by City and Age and calculate the mean of Age for each group
grouped_df = df.groupby(['City', 'Age']).agg({'Age': 'mean'})

# Display the grouped and aggregated DataFrame
print(grouped_df)
```

Output:
```
                    Age
City        Age
Chicago     35       35
Houston     40       40
Los Angeles 30       30
New York    25       25
Phoenix     45       45
```

In this example, we grouped the DataFrame by `City` and `Age` and calculated the mean of `Age` for each group.

## Reading and Writing DataFrames

You can read data from various file formats into a DataFrame, and you can write a DataFrame to various file formats. Let's see some examples of reading and writing DataFrames.

### Reading a DataFrame from a CSV file

You can read a DataFrame from a CSV file using the `read_csv()` method. Let's see an example.

```python
import pandas as pd

# Read a DataFrame from a CSV file
df = pd.read_csv('data.csv')

# Display the DataFrame
print(df)
```

In this example, we read a DataFrame from a CSV file called `data.csv`.

### Writing a DataFrame to a CSV file

You can write a DataFrame to a CSV file using the `to_csv()` method. Let's see an example.

```python
import pandas as pd

# Create a DataFrame

data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Emily'],
    'Age': [25, 30, 35, 40, 45],
    'City': ['New York', 'Los Angeles', 'Chicago', 'Houston', 'Phoenix']
}
df = pd.DataFrame(data)

# Write the DataFrame to a CSV file
df.to_csv('data.csv', index=False)
```

In this example, we wrote a DataFrame to a CSV file called `data.csv`.

### Reading a DataFrame from an Excel file

You can read a DataFrame from an Excel file using the `read_excel()` method. Let's see an example.

```python
import pandas as pd

# Read a DataFrame from an Excel file
df = pd.read_excel('data.xlsx')

# Display the DataFrame
print(df)
```

In this example, we read a DataFrame from an Excel file called `data.xlsx`.

### Writing a DataFrame to an Excel file

You can write a DataFrame to an Excel file using the `to_excel()` method. Let's see an example.

```python
import pandas as pd

# Create a DataFrame

data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Emily'],
    'Age': [25, 30, 35, 40, 45],
    'City': ['New York', 'Los Angeles', 'Chicago', 'Houston', 'Phoenix']
}

df = pd.DataFrame(data)

# Write the DataFrame to an Excel file
df.to_excel('data.xlsx', index=False)
```

In this example, we wrote a DataFrame to an Excel file called `data.xlsx`.

## Conclusion

In this section, we learned how to use Pandas library. We learned how to create DataFrames, access DataFrames, perform operations on DataFrames, add and remove columns from DataFrames, add and remove rows from DataFrames, and read and write DataFrames to various file formats. We also saw some examples of creating DataFrames from dictionaries, lists of dictionaries, lists of lists, and NumPy arrays. We saw some examples of accessing individual columns, rows, and cells of DataFrames. We saw some examples of filtering, sorting, and performing statistics on DataFrames. We saw some examples of adding and removing columns and rows from DataFrames. We saw some examples of reading and writing DataFrames to various file formats. We hope you found this section helpful and that you are now comfortable using Pandas for data manipulation and analysis.

## Exercises


After reading the previous section, you should be able to create your first Jupyter-Notebook and write a report about all the things you have learned in this section. In order to have a good structure, we recommend you to follow exactly the same structure as in this notebook. 


But this time it would be different, since you will have to create your own data. Your dataframe must have at least 6 columns and 12 rows. You can use any data you want, but we recommend you to use data that you are familiar with. For example, you can use data from your work, your studies, your hobbies, etc. After you create your dataframe, you will have to recreate all the examples from the previous section using your dataframe and write a report about it. 

```{Note}
Your dataframe must have at least 6 columns and 12 rows. And it is very important to include a column named "Conections" in your dataframe, that will symbolize the connections between the rows. So, you will end up with a dataframe that has at least 6 columns and 12 rows, and one of the columns must be named "Connections" 6+1.
```