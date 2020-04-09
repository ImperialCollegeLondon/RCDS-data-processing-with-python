#### Data Processing with Python

If pandas is installed in your python environment, it's easy to import:


```python
import pandas as pd
```


##### IN CASE OF PROBLEMS WITH PACKAGES:



```python
# SOLUTION A: select this cell and type Shift-Enter to execute the code below.

%conda install pandas

# Now restart the kernel (Menu -> Kernel -> Restart Kernel)
```


```python
# SOLUTION B: select this cell and type Shift-Enter to execute the code below.

%pip install pandas

# Now restart the kernel (Menu -> Kernel -> Restart Kernel)
```

# 1. DataFrames

Pandas is built around a fundamental data object called a `DataFrame`.

Here's how you can create one from a python `dict`:


```python
planets = pd.DataFrame({ 
    "name" : ["Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune"], 
    "type" : ["Terrestrial", "Terrestrial", "Terrestrial", "Terrestrial", "Gas giant", "Gas giant", "Ice giant", "Ice giant"],
    "mass" : [0.0553, 0.815, 1, 0.107, 317.8, 95.2, 14.5, 17.1],
    "diameter" : [0.383, 0.949, 1, 0.532, 11.21, 9.45, 4.01, 3.88],
    "distance from sun" : [0.387, 0.723, 1, 1.52, 5.20, 9.58, 19.2, 30.05],
    "orbital period" : [0.241, 0.615, 1, 1.88, 11.9, 29.4, 83.7, 163.7],
    "rings" : [False, False, False, False, True, True, True, True]
})

planets
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>type</th>
      <th>mass</th>
      <th>diameter</th>
      <th>distance from sun</th>
      <th>orbital period</th>
      <th>rings</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mercury</td>
      <td>Terrestrial</td>
      <td>0.0553</td>
      <td>0.383</td>
      <td>0.387</td>
      <td>0.241</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Venus</td>
      <td>Terrestrial</td>
      <td>0.8150</td>
      <td>0.949</td>
      <td>0.723</td>
      <td>0.615</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Earth</td>
      <td>Terrestrial</td>
      <td>1.0000</td>
      <td>1.000</td>
      <td>1.000</td>
      <td>1.000</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mars</td>
      <td>Terrestrial</td>
      <td>0.1070</td>
      <td>0.532</td>
      <td>1.520</td>
      <td>1.880</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Jupiter</td>
      <td>Gas giant</td>
      <td>317.8000</td>
      <td>11.210</td>
      <td>5.200</td>
      <td>11.900</td>
      <td>True</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Saturn</td>
      <td>Gas giant</td>
      <td>95.2000</td>
      <td>9.450</td>
      <td>9.580</td>
      <td>29.400</td>
      <td>True</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Uranus</td>
      <td>Ice giant</td>
      <td>14.5000</td>
      <td>4.010</td>
      <td>19.200</td>
      <td>83.700</td>
      <td>True</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Neptune</td>
      <td>Ice giant</td>
      <td>17.1000</td>
      <td>3.880</td>
      <td>30.050</td>
      <td>163.700</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>



The variable `planets` now points to a `DataFrame` object containing our data. We can get a quick glimpse of the data using the `head` method, which returns the first five rows:


```python
planets.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>type</th>
      <th>mass</th>
      <th>diameter</th>
      <th>distance from sun</th>
      <th>orbital period</th>
      <th>rings</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mercury</td>
      <td>Terrestrial</td>
      <td>0.0553</td>
      <td>0.383</td>
      <td>0.387</td>
      <td>0.241</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Venus</td>
      <td>Terrestrial</td>
      <td>0.8150</td>
      <td>0.949</td>
      <td>0.723</td>
      <td>0.615</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Earth</td>
      <td>Terrestrial</td>
      <td>1.0000</td>
      <td>1.000</td>
      <td>1.000</td>
      <td>1.000</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mars</td>
      <td>Terrestrial</td>
      <td>0.1070</td>
      <td>0.532</td>
      <td>1.520</td>
      <td>1.880</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Jupiter</td>
      <td>Gas giant</td>
      <td>317.8000</td>
      <td>11.210</td>
      <td>5.200</td>
      <td>11.900</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>



The attribute `shape` holds the dimensions of the DataFrame as (#rows, #columns) :


```python
planets.shape
```




    (8, 7)



## 1.1 Methods and Attributes

To make use of a DataFrame, we need to understand some basic concepts in object-oriented python.

A *method* is a function that is bound to an object. We show that we want to call the method `head` of the object `planets` using a dot: `planets.head()`.

In a similar way, objects can have associated variables called *attributes*, such as `planets.shape`

A pandas `DataFrame` has many other useful [methods](https://pandas.pydata.org/pandas-docs/stable/reference/frame.html#computations-descriptive-stats) and [attributes](https://pandas.pydata.org/pandas-docs/stable/reference/frame.html#attributes-and-underlying-data).

##### *Exercise*

1. What do the following methods do?

`tail`,
`sample`,
`describe`,
`copy`
?



```python
planets.tail() # selects the last 5 rows
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>type</th>
      <th>mass</th>
      <th>diameter</th>
      <th>distance from sun</th>
      <th>orbital period</th>
      <th>rings</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3</th>
      <td>Mars</td>
      <td>Terrestrial</td>
      <td>0.107</td>
      <td>0.532</td>
      <td>1.52</td>
      <td>1.88</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Jupiter</td>
      <td>Gas giant</td>
      <td>317.800</td>
      <td>11.210</td>
      <td>5.20</td>
      <td>11.90</td>
      <td>True</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Saturn</td>
      <td>Gas giant</td>
      <td>95.200</td>
      <td>9.450</td>
      <td>9.58</td>
      <td>29.40</td>
      <td>True</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Uranus</td>
      <td>Ice giant</td>
      <td>14.500</td>
      <td>4.010</td>
      <td>19.20</td>
      <td>83.70</td>
      <td>True</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Neptune</td>
      <td>Ice giant</td>
      <td>17.100</td>
      <td>3.880</td>
      <td>30.05</td>
      <td>163.70</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>




```python
planets.sample() # selects one row at random
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>type</th>
      <th>mass</th>
      <th>diameter</th>
      <th>distance from sun</th>
      <th>orbital period</th>
      <th>rings</th>
      <th>density</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>7</th>
      <td>Neptune</td>
      <td>Ice giant</td>
      <td>17.1</td>
      <td>3.88</td>
      <td>30.05</td>
      <td>163.7</td>
      <td>True</td>
      <td>0.292753</td>
    </tr>
  </tbody>
</table>
</div>




```python
planets.describe() # calculates summary statistics
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>mass</th>
      <th>diameter</th>
      <th>distance from sun</th>
      <th>orbital period</th>
      <th>density</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>8.000000</td>
      <td>8.000000</td>
      <td>8.000000</td>
      <td>8.000000</td>
      <td>8.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>55.822163</td>
      <td>3.926750</td>
      <td>8.457500</td>
      <td>36.554500</td>
      <td>0.563070</td>
    </tr>
    <tr>
      <th>std</th>
      <td>110.605675</td>
      <td>4.227064</td>
      <td>10.837813</td>
      <td>58.705645</td>
      <td>0.386688</td>
    </tr>
    <tr>
      <th>min</th>
      <td>0.055300</td>
      <td>0.383000</td>
      <td>0.387000</td>
      <td>0.241000</td>
      <td>0.112808</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>0.638000</td>
      <td>0.844750</td>
      <td>0.930750</td>
      <td>0.903750</td>
      <td>0.225417</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>7.750000</td>
      <td>2.440000</td>
      <td>3.360000</td>
      <td>6.890000</td>
      <td>0.501696</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>36.625000</td>
      <td>5.370000</td>
      <td>11.985000</td>
      <td>42.975000</td>
      <td>0.961264</td>
    </tr>
    <tr>
      <th>max</th>
      <td>317.800000</td>
      <td>11.210000</td>
      <td>30.050000</td>
      <td>163.700000</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
planets.copy() # returns a copy of the DataFrame
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>type</th>
      <th>mass</th>
      <th>diameter</th>
      <th>distance from sun</th>
      <th>orbital period</th>
      <th>rings</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mercury</td>
      <td>Terrestrial</td>
      <td>0.0553</td>
      <td>0.383</td>
      <td>0.387</td>
      <td>0.241</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Venus</td>
      <td>Terrestrial</td>
      <td>0.8150</td>
      <td>0.949</td>
      <td>0.723</td>
      <td>0.615</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Earth</td>
      <td>Terrestrial</td>
      <td>1.0000</td>
      <td>1.000</td>
      <td>1.000</td>
      <td>1.000</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mars</td>
      <td>Terrestrial</td>
      <td>0.1070</td>
      <td>0.532</td>
      <td>1.520</td>
      <td>1.880</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Jupiter</td>
      <td>Gas giant</td>
      <td>317.8000</td>
      <td>11.210</td>
      <td>5.200</td>
      <td>11.900</td>
      <td>True</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Saturn</td>
      <td>Gas giant</td>
      <td>95.2000</td>
      <td>9.450</td>
      <td>9.580</td>
      <td>29.400</td>
      <td>True</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Uranus</td>
      <td>Ice giant</td>
      <td>14.5000</td>
      <td>4.010</td>
      <td>19.200</td>
      <td>83.700</td>
      <td>True</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Neptune</td>
      <td>Ice giant</td>
      <td>17.1000</td>
      <td>3.880</td>
      <td>30.050</td>
      <td>163.700</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>



2. To what do the following attributes refer?

`size`,
`dtypes`,
`columns`,
`values`


```python
planets.size # the total number of data values (cells)
```




    56




```python
planets.dtypes # the data type for each column
```




    name                  object
    type                  object
    mass                 float64
    diameter             float64
    distance from sun    float64
    orbital period       float64
    rings                   bool
    dtype: object




```python
planets.columns # the column labels
```




    Index(['name', 'type', 'mass', 'diameter', 'distance from sun',
           'orbital period', 'rings'],
          dtype='object')




```python
planets.values # the data values as an array
```




    array([['Mercury', 'Terrestrial', 0.0553, 0.383, 0.387, 0.241, False],
           ['Venus', 'Terrestrial', 0.815, 0.949, 0.723, 0.615, False],
           ['Earth', 'Terrestrial', 1.0, 1.0, 1.0, 1.0, False],
           ['Mars', 'Terrestrial', 0.107, 0.532, 1.52, 1.88, False],
           ['Jupiter', 'Gas giant', 317.8, 11.21, 5.2, 11.9, True],
           ['Saturn', 'Gas giant', 95.2, 9.45, 9.58, 29.4, True],
           ['Uranus', 'Ice giant', 14.5, 4.01, 19.2, 83.7, True],
           ['Neptune', 'Ice giant', 17.1, 3.88, 30.05, 163.7, True]],
          dtype=object)



## 1.2 Accessing Data

Pandas provides several different ways to get data out of the DataFrame.



### Accessing single values

A single value can be accessed using `iat[]`. 

We can think of it as meaning "the value **at** an **i**nteger position". 

It treats the `DataFrame` like an array with two *axes*.

The row coordinate is the first axis; the column coordinate is second.



```python
planets.iat[1,2]
```




    0.815



### Accessing rows and columns

`iloc[]` means "**loc**ate data by **i**nteger position". 

It is used to access subsets of rows and columns, using the same coordinate system as `iat[]`.

#### Selecting rows

We can use `iloc[]` with a slice to get a subset of rows:


```python
planets.iloc[2:4]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>type</th>
      <th>mass</th>
      <th>diameter</th>
      <th>distance from sun</th>
      <th>orbital period</th>
      <th>rings</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2</th>
      <td>Earth</td>
      <td>Terrestrial</td>
      <td>1.000</td>
      <td>1.000</td>
      <td>1.00</td>
      <td>1.00</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mars</td>
      <td>Terrestrial</td>
      <td>0.107</td>
      <td>0.532</td>
      <td>1.52</td>
      <td>1.88</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
</div>



Because *slicing rows* is such a common operation, pandas also provides a shortcut:


```python
planets[2:4]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>type</th>
      <th>mass</th>
      <th>diameter</th>
      <th>distance from sun</th>
      <th>orbital period</th>
      <th>rings</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2</th>
      <td>Earth</td>
      <td>Terrestrial</td>
      <td>1.000</td>
      <td>1.000</td>
      <td>1.00</td>
      <td>1.00</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mars</td>
      <td>Terrestrial</td>
      <td>0.107</td>
      <td>0.532</td>
      <td>1.52</td>
      <td>1.88</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
</div>



Alternatively, we can provide `iloc` with a list of the indices to select:


```python
planets.iloc[[1,3,5]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>type</th>
      <th>mass</th>
      <th>diameter</th>
      <th>distance from sun</th>
      <th>orbital period</th>
      <th>rings</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>Venus</td>
      <td>Terrestrial</td>
      <td>0.815</td>
      <td>0.949</td>
      <td>0.723</td>
      <td>0.615</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mars</td>
      <td>Terrestrial</td>
      <td>0.107</td>
      <td>0.532</td>
      <td>1.520</td>
      <td>1.880</td>
      <td>False</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Saturn</td>
      <td>Gas giant</td>
      <td>95.200</td>
      <td>9.450</td>
      <td>9.580</td>
      <td>29.400</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>



##### *Exercise*

1. Select the last three rows.


```python
planets[-3:]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>type</th>
      <th>mass</th>
      <th>diameter</th>
      <th>distance from sun</th>
      <th>orbital period</th>
      <th>rings</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>5</th>
      <td>Saturn</td>
      <td>Gas giant</td>
      <td>95.2</td>
      <td>9.45</td>
      <td>9.58</td>
      <td>29.4</td>
      <td>True</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Uranus</td>
      <td>Ice giant</td>
      <td>14.5</td>
      <td>4.01</td>
      <td>19.20</td>
      <td>83.7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Neptune</td>
      <td>Ice giant</td>
      <td>17.1</td>
      <td>3.88</td>
      <td>30.05</td>
      <td>163.7</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>



2. Select three rows at random.


```python
planets.sample(3)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>type</th>
      <th>mass</th>
      <th>diameter</th>
      <th>distance from sun</th>
      <th>orbital period</th>
      <th>rings</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3</th>
      <td>Mars</td>
      <td>Terrestrial</td>
      <td>0.107</td>
      <td>0.532</td>
      <td>1.52</td>
      <td>1.88</td>
      <td>False</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Saturn</td>
      <td>Gas giant</td>
      <td>95.200</td>
      <td>9.450</td>
      <td>9.58</td>
      <td>29.40</td>
      <td>True</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Earth</td>
      <td>Terrestrial</td>
      <td>1.000</td>
      <td>1.000</td>
      <td>1.00</td>
      <td>1.00</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
</div>



3. Make a DataFrame containing only the first row.


```python
planets[:1]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>type</th>
      <th>mass</th>
      <th>diameter</th>
      <th>distance from sun</th>
      <th>orbital period</th>
      <th>rings</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mercury</td>
      <td>Terrestrial</td>
      <td>0.0553</td>
      <td>0.383</td>
      <td>0.387</td>
      <td>0.241</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
</div>



4. Make a DataFrame containing the first, second and last rows.


```python
planets.iloc[[0,1,-1]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>type</th>
      <th>mass</th>
      <th>diameter</th>
      <th>distance from sun</th>
      <th>orbital period</th>
      <th>rings</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mercury</td>
      <td>Terrestrial</td>
      <td>0.0553</td>
      <td>0.383</td>
      <td>0.387</td>
      <td>0.241</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Venus</td>
      <td>Terrestrial</td>
      <td>0.8150</td>
      <td>0.949</td>
      <td>0.723</td>
      <td>0.615</td>
      <td>False</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Neptune</td>
      <td>Ice giant</td>
      <td>17.1000</td>
      <td>3.880</td>
      <td>30.050</td>
      <td>163.700</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>



#### Selecting columns

We can access columns by integer using the second axis of `iloc[]`:



```python
planets.iloc[:,2]
```




    0      0.0553
    1      0.8150
    2      1.0000
    3      0.1070
    4    317.8000
    5     95.2000
    6     14.5000
    7     17.1000
    Name: mass, dtype: float64



Using an integer index (e.g. `2` above), this returns the column values in the form of a pandas `Series` object.

Notice that we still need to provide a placeholder `:` before the comma, to indicate "all of the rows".

Using a slice in place of an integer returns a subset of columns as a new DataFrame:


```python
planets.iloc[:,2:4]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>mass</th>
      <th>diameter</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.0553</td>
      <td>0.383</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0.8150</td>
      <td>0.949</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1.0000</td>
      <td>1.000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.1070</td>
      <td>0.532</td>
    </tr>
    <tr>
      <th>4</th>
      <td>317.8000</td>
      <td>11.210</td>
    </tr>
    <tr>
      <th>5</th>
      <td>95.2000</td>
      <td>9.450</td>
    </tr>
    <tr>
      <th>6</th>
      <td>14.5000</td>
      <td>4.010</td>
    </tr>
    <tr>
      <th>7</th>
      <td>17.1000</td>
      <td>3.880</td>
    </tr>
  </tbody>
</table>
</div>



However, accessing columns by position is not usually very useful. We need to be able to refer to the columns by their *labels*.

### Accessing by label
`loc[]` means "locate by label". Our columns are labelled with strings.



```python
planets.loc[:,"name"]
```




    0    Mercury
    1      Venus
    2      Earth
    3       Mars
    4    Jupiter
    5     Saturn
    6     Uranus
    7    Neptune
    Name: name, dtype: object



This returns a pandas `Series` object, which represents the data from a single column. The numbers shown next to the values are the *row labels*.

As a shortcut, we can also use `[]` with the *column labels* to select specified columns:


```python
planets["name"]
```




    0    Mercury
    1      Venus
    2      Earth
    3       Mars
    4    Jupiter
    5     Saturn
    6     Uranus
    7    Neptune
    Name: name, dtype: object



A list can be used to select multiple columns.


```python
planets[["name","mass"]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>mass</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mercury</td>
      <td>0.0553</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Venus</td>
      <td>0.8150</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Earth</td>
      <td>1.0000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mars</td>
      <td>0.1070</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Jupiter</td>
      <td>317.8000</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Saturn</td>
      <td>95.2000</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Uranus</td>
      <td>14.5000</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Neptune</td>
      <td>17.1000</td>
    </tr>
  </tbody>
</table>
</div>



##### *Exercise*

1. Select the first three rows, but only the **name** and **diameter** columns.


```python
planets[:3][["name","diameter"]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>diameter</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mercury</td>
      <td>0.383</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Venus</td>
      <td>0.949</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Earth</td>
      <td>1.000</td>
    </tr>
  </tbody>
</table>
</div>



2. Select the first two columns for rows 4 and 6


```python
planets.iloc[[4,6],:2]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>4</th>
      <td>Jupiter</td>
      <td>Gas giant</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Uranus</td>
      <td>Ice giant</td>
    </tr>
  </tbody>
</table>
</div>



3. Select all columns from **type** to **diameter** inclusive.


```python
planets.loc[:,"type":"diameter"]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>type</th>
      <th>mass</th>
      <th>diameter</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Terrestrial</td>
      <td>0.0553</td>
      <td>0.383</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Terrestrial</td>
      <td>0.8150</td>
      <td>0.949</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Terrestrial</td>
      <td>1.0000</td>
      <td>1.000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Terrestrial</td>
      <td>0.1070</td>
      <td>0.532</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Gas giant</td>
      <td>317.8000</td>
      <td>11.210</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Gas giant</td>
      <td>95.2000</td>
      <td>9.450</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Ice giant</td>
      <td>14.5000</td>
      <td>4.010</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Ice giant</td>
      <td>17.1000</td>
      <td>3.880</td>
    </tr>
  </tbody>
</table>
</div>



## 1.3 Querying, filtering and sorting data

Of course, we are not just limited to accessing data by its position or labels.

Here are some useful DataFrame methods for basic data manipulation:

### `query`
selects rows according to whatever conditions we specify, e.g.:


```python
planets.query("name == 'Earth'")
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>type</th>
      <th>mass</th>
      <th>diameter</th>
      <th>distance from sun</th>
      <th>orbital period</th>
      <th>rings</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2</th>
      <td>Earth</td>
      <td>Terrestrial</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
</div>




```python
planets.query("diameter > 2")
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>type</th>
      <th>mass</th>
      <th>diameter</th>
      <th>distance from sun</th>
      <th>orbital period</th>
      <th>rings</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>4</th>
      <td>Jupiter</td>
      <td>Gas giant</td>
      <td>317.8</td>
      <td>11.21</td>
      <td>5.20</td>
      <td>11.9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Saturn</td>
      <td>Gas giant</td>
      <td>95.2</td>
      <td>9.45</td>
      <td>9.58</td>
      <td>29.4</td>
      <td>True</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Uranus</td>
      <td>Ice giant</td>
      <td>14.5</td>
      <td>4.01</td>
      <td>19.20</td>
      <td>83.7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Neptune</td>
      <td>Ice giant</td>
      <td>17.1</td>
      <td>3.88</td>
      <td>30.05</td>
      <td>163.7</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>



Note that the query is a Boolean expression, provided as a string `""`. 

Inside the query, column names are unquoted and string values are quoted using `''`.

We can refer to columns containing spaces by enclosing them in backticks ` `` `.

We can also refer to variables in the environment using the `@` prefix.


```python
max_period = 30
planets.query("rings & `orbital period` < @max_period")
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>type</th>
      <th>mass</th>
      <th>diameter</th>
      <th>distance from sun</th>
      <th>orbital period</th>
      <th>rings</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>4</th>
      <td>Jupiter</td>
      <td>Gas giant</td>
      <td>317.8</td>
      <td>11.21</td>
      <td>5.20</td>
      <td>11.9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Saturn</td>
      <td>Gas giant</td>
      <td>95.2</td>
      <td>9.45</td>
      <td>9.58</td>
      <td>29.4</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>



### `filter`

extracts a subset of columns by examining their **labels**, e.g.:


```python
planets.filter(["name","mass"])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>mass</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mercury</td>
      <td>0.0553</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Venus</td>
      <td>0.8150</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Earth</td>
      <td>1.0000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mars</td>
      <td>0.1070</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Jupiter</td>
      <td>317.8000</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Saturn</td>
      <td>95.2000</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Uranus</td>
      <td>14.5000</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Neptune</td>
      <td>17.1000</td>
    </tr>
  </tbody>
</table>
</div>



This is similar to `loc[]` but has some extra pattern-matching powers:


```python
planets.filter(like="am")
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>diameter</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mercury</td>
      <td>0.383</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Venus</td>
      <td>0.949</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Earth</td>
      <td>1.000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mars</td>
      <td>0.532</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Jupiter</td>
      <td>11.210</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Saturn</td>
      <td>9.450</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Uranus</td>
      <td>4.010</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Neptune</td>
      <td>3.880</td>
    </tr>
  </tbody>
</table>
</div>




```python
planets.filter(regex="^t")
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Terrestrial</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Terrestrial</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Terrestrial</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Terrestrial</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Gas giant</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Gas giant</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Ice giant</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Ice giant</td>
    </tr>
  </tbody>
</table>
</div>



### `sort_values`

returns a copy of the DataFrame, sorted by ascending column value:


```python
planets.sort_values("diameter")
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>type</th>
      <th>mass</th>
      <th>diameter</th>
      <th>distance from sun</th>
      <th>orbital period</th>
      <th>rings</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mercury</td>
      <td>Terrestrial</td>
      <td>0.0553</td>
      <td>0.383</td>
      <td>0.387</td>
      <td>0.241</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mars</td>
      <td>Terrestrial</td>
      <td>0.1070</td>
      <td>0.532</td>
      <td>1.520</td>
      <td>1.880</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Venus</td>
      <td>Terrestrial</td>
      <td>0.8150</td>
      <td>0.949</td>
      <td>0.723</td>
      <td>0.615</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Earth</td>
      <td>Terrestrial</td>
      <td>1.0000</td>
      <td>1.000</td>
      <td>1.000</td>
      <td>1.000</td>
      <td>False</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Neptune</td>
      <td>Ice giant</td>
      <td>17.1000</td>
      <td>3.880</td>
      <td>30.050</td>
      <td>163.700</td>
      <td>True</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Uranus</td>
      <td>Ice giant</td>
      <td>14.5000</td>
      <td>4.010</td>
      <td>19.200</td>
      <td>83.700</td>
      <td>True</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Saturn</td>
      <td>Gas giant</td>
      <td>95.2000</td>
      <td>9.450</td>
      <td>9.580</td>
      <td>29.400</td>
      <td>True</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Jupiter</td>
      <td>Gas giant</td>
      <td>317.8000</td>
      <td>11.210</td>
      <td>5.200</td>
      <td>11.900</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>



...or by descending value using `ascending=False`:


```python
planets.sort_values("diameter", ascending=False)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>type</th>
      <th>mass</th>
      <th>diameter</th>
      <th>distance from sun</th>
      <th>orbital period</th>
      <th>rings</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>4</th>
      <td>Jupiter</td>
      <td>Gas giant</td>
      <td>317.8000</td>
      <td>11.210</td>
      <td>5.200</td>
      <td>11.900</td>
      <td>True</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Saturn</td>
      <td>Gas giant</td>
      <td>95.2000</td>
      <td>9.450</td>
      <td>9.580</td>
      <td>29.400</td>
      <td>True</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Uranus</td>
      <td>Ice giant</td>
      <td>14.5000</td>
      <td>4.010</td>
      <td>19.200</td>
      <td>83.700</td>
      <td>True</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Neptune</td>
      <td>Ice giant</td>
      <td>17.1000</td>
      <td>3.880</td>
      <td>30.050</td>
      <td>163.700</td>
      <td>True</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Earth</td>
      <td>Terrestrial</td>
      <td>1.0000</td>
      <td>1.000</td>
      <td>1.000</td>
      <td>1.000</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Venus</td>
      <td>Terrestrial</td>
      <td>0.8150</td>
      <td>0.949</td>
      <td>0.723</td>
      <td>0.615</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mars</td>
      <td>Terrestrial</td>
      <td>0.1070</td>
      <td>0.532</td>
      <td>1.520</td>
      <td>1.880</td>
      <td>False</td>
    </tr>
    <tr>
      <th>0</th>
      <td>Mercury</td>
      <td>Terrestrial</td>
      <td>0.0553</td>
      <td>0.383</td>
      <td>0.387</td>
      <td>0.241</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
</div>




```python
planets
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>type</th>
      <th>mass</th>
      <th>diameter</th>
      <th>distance from sun</th>
      <th>orbital period</th>
      <th>rings</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mercury</td>
      <td>Terrestrial</td>
      <td>0.0553</td>
      <td>0.383</td>
      <td>0.387</td>
      <td>0.241</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Venus</td>
      <td>Terrestrial</td>
      <td>0.8150</td>
      <td>0.949</td>
      <td>0.723</td>
      <td>0.615</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Earth</td>
      <td>Terrestrial</td>
      <td>1.0000</td>
      <td>1.000</td>
      <td>1.000</td>
      <td>1.000</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mars</td>
      <td>Terrestrial</td>
      <td>0.1070</td>
      <td>0.532</td>
      <td>1.520</td>
      <td>1.880</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Jupiter</td>
      <td>Gas giant</td>
      <td>317.8000</td>
      <td>11.210</td>
      <td>5.200</td>
      <td>11.900</td>
      <td>True</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Saturn</td>
      <td>Gas giant</td>
      <td>95.2000</td>
      <td>9.450</td>
      <td>9.580</td>
      <td>29.400</td>
      <td>True</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Uranus</td>
      <td>Ice giant</td>
      <td>14.5000</td>
      <td>4.010</td>
      <td>19.200</td>
      <td>83.700</td>
      <td>True</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Neptune</td>
      <td>Ice giant</td>
      <td>17.1000</td>
      <td>3.880</td>
      <td>30.050</td>
      <td>163.700</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>



##### *Exercise*

Use manipulations of `planets` to make DataFrames containing the following:

1. the terrestrial planets, ordered by increasing orbital period.


```python
df = planets.query("type == 'Terrestrial'")
df.sort_values("orbital period")
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>type</th>
      <th>mass</th>
      <th>diameter</th>
      <th>distance from sun</th>
      <th>orbital period</th>
      <th>rings</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mercury</td>
      <td>Terrestrial</td>
      <td>0.0553</td>
      <td>0.383</td>
      <td>0.387</td>
      <td>0.241</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Venus</td>
      <td>Terrestrial</td>
      <td>0.8150</td>
      <td>0.949</td>
      <td>0.723</td>
      <td>0.615</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Earth</td>
      <td>Terrestrial</td>
      <td>1.0000</td>
      <td>1.000</td>
      <td>1.000</td>
      <td>1.000</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mars</td>
      <td>Terrestrial</td>
      <td>0.1070</td>
      <td>0.532</td>
      <td>1.520</td>
      <td>1.880</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
</div>



2. the giant planets, ordered from largest to smallest.


```python
df = planets.query("type in ['Gas giant','Ice giant']")
df.sort_values("diameter",ascending=False)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>type</th>
      <th>mass</th>
      <th>diameter</th>
      <th>distance from sun</th>
      <th>orbital period</th>
      <th>rings</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>4</th>
      <td>Jupiter</td>
      <td>Gas giant</td>
      <td>317.8</td>
      <td>11.21</td>
      <td>5.20</td>
      <td>11.9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Saturn</td>
      <td>Gas giant</td>
      <td>95.2</td>
      <td>9.45</td>
      <td>9.58</td>
      <td>29.4</td>
      <td>True</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Uranus</td>
      <td>Ice giant</td>
      <td>14.5</td>
      <td>4.01</td>
      <td>19.20</td>
      <td>83.7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Neptune</td>
      <td>Ice giant</td>
      <td>17.1</td>
      <td>3.88</td>
      <td>30.05</td>
      <td>163.7</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>



3. the planets that are more massive than Neptune.


```python
m_neptune = planets.query("name == 'Neptune'")["mass"].values[0]
planets.query("mass > @m_neptune")
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>type</th>
      <th>mass</th>
      <th>diameter</th>
      <th>distance from sun</th>
      <th>orbital period</th>
      <th>rings</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>4</th>
      <td>Jupiter</td>
      <td>Gas giant</td>
      <td>317.8</td>
      <td>11.21</td>
      <td>5.20</td>
      <td>11.9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Saturn</td>
      <td>Gas giant</td>
      <td>95.2</td>
      <td>9.45</td>
      <td>9.58</td>
      <td>29.4</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>



## 1.4 Making new columns from existing ones

It's easy to add a new column to a `DataFrame`. 

We just use `[]=` to assign a `Series` to the new column:


```python
df = planets.copy()
df["radius"] = df["diameter"] / 2
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>type</th>
      <th>mass</th>
      <th>diameter</th>
      <th>distance from sun</th>
      <th>orbital period</th>
      <th>rings</th>
      <th>radius</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mercury</td>
      <td>Terrestrial</td>
      <td>0.0553</td>
      <td>0.383</td>
      <td>0.387</td>
      <td>0.241</td>
      <td>False</td>
      <td>0.1915</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Venus</td>
      <td>Terrestrial</td>
      <td>0.8150</td>
      <td>0.949</td>
      <td>0.723</td>
      <td>0.615</td>
      <td>False</td>
      <td>0.4745</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Earth</td>
      <td>Terrestrial</td>
      <td>1.0000</td>
      <td>1.000</td>
      <td>1.000</td>
      <td>1.000</td>
      <td>False</td>
      <td>0.5000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mars</td>
      <td>Terrestrial</td>
      <td>0.1070</td>
      <td>0.532</td>
      <td>1.520</td>
      <td>1.880</td>
      <td>False</td>
      <td>0.2660</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Jupiter</td>
      <td>Gas giant</td>
      <td>317.8000</td>
      <td>11.210</td>
      <td>5.200</td>
      <td>11.900</td>
      <td>True</td>
      <td>5.6050</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Saturn</td>
      <td>Gas giant</td>
      <td>95.2000</td>
      <td>9.450</td>
      <td>9.580</td>
      <td>29.400</td>
      <td>True</td>
      <td>4.7250</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Uranus</td>
      <td>Ice giant</td>
      <td>14.5000</td>
      <td>4.010</td>
      <td>19.200</td>
      <td>83.700</td>
      <td>True</td>
      <td>2.0050</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Neptune</td>
      <td>Ice giant</td>
      <td>17.1000</td>
      <td>3.880</td>
      <td>30.050</td>
      <td>163.700</td>
      <td>True</td>
      <td>1.9400</td>
    </tr>
  </tbody>
</table>
</div>



Note that `Series` objects can be combined in a row-wise manner, similar to numpy arrays, e.g.:


```python
planets["name"] + " -- " + planets["type"]
```




    0    Mercury -- Terrestrial
    1      Venus -- Terrestrial
    2      Earth -- Terrestrial
    3       Mars -- Terrestrial
    4      Jupiter -- Gas giant
    5       Saturn -- Gas giant
    6       Uranus -- Ice giant
    7      Neptune -- Ice giant
    dtype: object



##### *Exercise*

Add a new column to `planets` to show the density of each planet relative to Earth.



```python
# First we compute the density in arbitrary units and add the new column

radius = planets["diameter"] / 2
vol = 4/3 * 3.14 * radius**3

mass = planets["mass"]
density = mass/vol

planets["density"] = density
```


```python
# Now we have to normalise by the density of Earth

d_E = planets.query("name == 'Earth'")["density"].values[0]
planets["density"] = planets["density"] / d_E
```


```python
planets
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>type</th>
      <th>mass</th>
      <th>diameter</th>
      <th>distance from sun</th>
      <th>orbital period</th>
      <th>rings</th>
      <th>density</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mercury</td>
      <td>Terrestrial</td>
      <td>0.0553</td>
      <td>0.383</td>
      <td>0.387</td>
      <td>0.241</td>
      <td>False</td>
      <td>0.984303</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Venus</td>
      <td>Terrestrial</td>
      <td>0.8150</td>
      <td>0.949</td>
      <td>0.723</td>
      <td>0.615</td>
      <td>False</td>
      <td>0.953584</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Earth</td>
      <td>Terrestrial</td>
      <td>1.0000</td>
      <td>1.000</td>
      <td>1.000</td>
      <td>1.000</td>
      <td>False</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mars</td>
      <td>Terrestrial</td>
      <td>0.1070</td>
      <td>0.532</td>
      <td>1.520</td>
      <td>1.880</td>
      <td>False</td>
      <td>0.710639</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Jupiter</td>
      <td>Gas giant</td>
      <td>317.8000</td>
      <td>11.210</td>
      <td>5.200</td>
      <td>11.900</td>
      <td>True</td>
      <td>0.225599</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Saturn</td>
      <td>Gas giant</td>
      <td>95.2000</td>
      <td>9.450</td>
      <td>9.580</td>
      <td>29.400</td>
      <td>True</td>
      <td>0.112808</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Uranus</td>
      <td>Ice giant</td>
      <td>14.5000</td>
      <td>4.010</td>
      <td>19.200</td>
      <td>83.700</td>
      <td>True</td>
      <td>0.224872</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Neptune</td>
      <td>Ice giant</td>
      <td>17.1000</td>
      <td>3.880</td>
      <td>30.050</td>
      <td>163.700</td>
      <td>True</td>
      <td>0.292753</td>
    </tr>
  </tbody>
</table>
</div>


