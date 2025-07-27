---
title: Pandas Crash Course
author: Juma Shafara
date: "2024-01"
date-modified: "2024-08-19"
description: Pandas is a fast, powerful, flexible and easy to use open source data analysis and manipulation tool.
keywords: [Creating Dataframes, Concatenating DataFrames, Sampling values in the DataFrame, Selecting, Boolean Indexing and Setting, Dropping, Retrieving information about DataFrame]
---

<!-- ![Photo by DATAIDEA](../assets/banner4.png) -->

<div class="video-wrapper">
  <iframe
    class="video-iframe"
    src="https://www.youtube.com/embed/BmotKMVgM0M?si=GsTajH65a9AUpYCe"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture;"
    allowfullscreen>
  </iframe>
</div>

Pandas is a fast, powerful, flexible and easy to use open source data analysis and manipulation tool. 

This tutoral will show you the basic and intermediate concepts in Pandas

<!-- Newsletter -->
<div class="newsletter">
<div class="newsletter-heading">
<h4><i class="bi bi-info-circle-fill"></i> Don't Miss Any Updates!</h4>
</div>
<div class="newsletter-body">
<p>
Before we continue, we have a humble request, to be among the first to hear about future updates of the course materials, simply enter your email below, follow us on <a href="https://x.com/dataideaorg"><i class="bi bi-twitter-x"></i>
(formally Twitter)</a>, or subscribe to our <a href="https://www.youtube.com/@dataidea-science"><i class="bi bi-youtube"></i> YouTube channel</a>.
</p>
<iframe class="newsletter-frame" src="https://embeds.beehiiv.com/5fc7c425-9c7e-4e08-a514-ad6c22beee74?slim=true" data-test-id="beehiiv-embed" height="52" frameborder="0" scrolling="no">
</iframe>
</div>
</div>


```python
# Uncomment and run this cell to install pandas
# !pip install pandas
# !pip install openpyxl
```


```python
# import pandas
import pandas as pd
```


```python
# to check python version
print(pd.__version__)
```

    2.2.2


## Creating Dataframes

The reason why data analysts like pandas is because pandas provides them with a very powerful data structure called a dataframe. A dataframe is a 2D structure that offers us rows and columns similar to tables in excel, sql etc

### Creating dataframes from existing files

If you already have some data in maybe an excel, csv, or stata file, you can be able to load it into a dataframe and then perform manipulation.


```python
# loading an excel file into a dataframe
data = pd.read_excel(io='../assets/demo.xlsx')
```

<!-- Alert -->
<div class="alert text-white rounded"><h4><i class="bi bi-info-circle-fill"></i> Note!</h4><p>You must have `openpyxl` installed to be able to read excel files using pandas.</p></div>

The data structure that is returned by the statement is called a `DataFrame`


```python
# checking the datatype of the data object
print(type(data))
```

    <class 'pandas.core.frame.DataFrame'>



```python
# randomly sample some values
data.sample(n=5)
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
      <th>Age</th>
      <th>Gender</th>
      <th>Marital Status</th>
      <th>Address</th>
      <th>Income</th>
      <th>Income Category</th>
      <th>Job Category</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>137</th>
      <td>32</td>
      <td>m</td>
      <td>0</td>
      <td>1</td>
      <td>26</td>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <th>92</th>
      <td>61</td>
      <td>m</td>
      <td>1</td>
      <td>18</td>
      <td>23</td>
      <td>1</td>
      <td>3</td>
    </tr>
    <tr>
      <th>39</th>
      <td>21</td>
      <td>f</td>
      <td>0</td>
      <td>0</td>
      <td>13</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>41</th>
      <td>56</td>
      <td>f</td>
      <td>0</td>
      <td>7</td>
      <td>213</td>
      <td>4</td>
      <td>3</td>
    </tr>
    <tr>
      <th>48</th>
      <td>51</td>
      <td>f</td>
      <td>0</td>
      <td>0</td>
      <td>47</td>
      <td>2</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>



### Creating a DataFrame from a Dictionary

For the previous case, we may be having some data already, but sometimes we may want to create a dataframe from scratch. We can create pandas dataframes using two major ways:

<ul class="cursored-list">
<li><i class="bi bi-cursor"></i> Using a dictionary</li>
<li><i class="bi bi-cursor"></i> Using a 2D list</li>
</ul>

We've met dictionaries and lists in the Containers/Collections module of the Python 3 Beginner Course.

To begin with, we're gonna create a dataframe from a dictionary. The way we create the dictionary is important, keys will be used as column names, and the values will be used as rows. So, you typically want your values to be lists or tuples.

Now you might observe that the values (lists) are of equal length


```python
# create a pandas dataframe using a dictionary
data_dictionary = {
    'age': [65, 51, 45, 38, 40],
    'gender': ['m', 'm', 'm', 'f', 'm'],
    'income': [42, 148, 147, 43, 89]
}

dataframe_from_dict = pd.DataFrame(data=data_dictionary)
```


```python
# display the dataframe
dataframe_from_dict
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
      <th>age</th>
      <th>gender</th>
      <th>income</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>65</td>
      <td>m</td>
      <td>42</td>
    </tr>
    <tr>
      <th>1</th>
      <td>51</td>
      <td>m</td>
      <td>148</td>
    </tr>
    <tr>
      <th>2</th>
      <td>45</td>
      <td>m</td>
      <td>147</td>
    </tr>
    <tr>
      <th>3</th>
      <td>38</td>
      <td>f</td>
      <td>43</td>
    </tr>
    <tr>
      <th>4</th>
      <td>40</td>
      <td>m</td>
      <td>89</td>
    </tr>
  </tbody>
</table>
</div>



Next up, we are gonna create a dataframe from a list. For this case, the list be of 2D shape. Again, the way we organize data in our list is important. We should organize that in a format close to rows and columns as showed below. 

It turns out that when creating a dataframe from a list, we need to explicitly define the column names as demonstrated below


```python
# creating a dataframe from a 2D list
data_list = [
    [28, 'm', 24],
    [59, 'm', 841],
    [54, 'm', 741],
    [83, 'f', 34],
    [34, 'm', 98]
]
# let's specify the column names
names = ['age', 'gender', 'income']

dataframe_from_list = pd.DataFrame(data=data_list, 
                                   columns=names)
```


```python
# display the dataframe
dataframe_from_list
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
      <th>age</th>
      <th>gender</th>
      <th>income</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>28</td>
      <td>m</td>
      <td>24</td>
    </tr>
    <tr>
      <th>1</th>
      <td>59</td>
      <td>m</td>
      <td>841</td>
    </tr>
    <tr>
      <th>2</th>
      <td>54</td>
      <td>m</td>
      <td>741</td>
    </tr>
    <tr>
      <th>3</th>
      <td>83</td>
      <td>f</td>
      <td>34</td>
    </tr>
    <tr>
      <th>4</th>
      <td>34</td>
      <td>m</td>
      <td>98</td>
    </tr>
  </tbody>
</table>
</div>



Before we continue, I would like to share some ways you would look for help or more information about pandas methods.

<ul class="cursored-list">
<li><i class="bi bi-cursor"></i> One way is by using the `help()` method.</li> 
<li><i class="bi bi-cursor"></i> Another is by using the query operator `?`</li> 
</ul>



```python
# Finding more information
# help(pd.DataFrame)
```


```python
## Another way to find more information
# ?pd.DataFrame
```

The latter is my favorite because it works in all situations.

## Concatenating DataFrames

<!-- Video -->
<div class="video-wrapper">
  <iframe
    class="video-iframe"
    src="https://www.youtube.com/embed/nDR3rdC7zwI?si=bHbM4iixSF8C_woJ"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture;"
    allowfullscreen
  >
  </iframe>
</div>

Sometimes there's a need to add two or more dataframes. To perform this, for the start, we can use the `pd.concat()`. The `concat()` method takes in a list of dataframes we would like to combine

Remember we created 2 dataframes earlier, one from a dictionary and another from a list, now let's combine them to make one dataframe


```python
concatenated_dataframe = pd.concat(
    objs=[dataframe_from_dict, dataframe_from_list], 
    ignore_index=True
)
```


```python
concatenated_dataframe
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
      <th>age</th>
      <th>gender</th>
      <th>income</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>65</td>
      <td>m</td>
      <td>42</td>
    </tr>
    <tr>
      <th>1</th>
      <td>51</td>
      <td>m</td>
      <td>148</td>
    </tr>
    <tr>
      <th>2</th>
      <td>45</td>
      <td>m</td>
      <td>147</td>
    </tr>
    <tr>
      <th>3</th>
      <td>38</td>
      <td>f</td>
      <td>43</td>
    </tr>
    <tr>
      <th>4</th>
      <td>40</td>
      <td>m</td>
      <td>89</td>
    </tr>
    <tr>
      <th>5</th>
      <td>28</td>
      <td>m</td>
      <td>24</td>
    </tr>
    <tr>
      <th>6</th>
      <td>59</td>
      <td>m</td>
      <td>841</td>
    </tr>
    <tr>
      <th>7</th>
      <td>54</td>
      <td>m</td>
      <td>741</td>
    </tr>
    <tr>
      <th>8</th>
      <td>83</td>
      <td>f</td>
      <td>34</td>
    </tr>
    <tr>
      <th>9</th>
      <td>34</td>
      <td>m</td>
      <td>98</td>
    </tr>
  </tbody>
</table>
</div>



We set `ignore_index=True` to correct the indexing so that we can have unique indexes and hence be able to able to uniquely identify rows by index

**Exercise:** Demonstrate how to concatenate two or more dataframes by column ie if dataframe A has columns a, b, c and dataframe B has columns x, y, z, the resulting dataframe should have columns a, b, c, x, y, z

## Sampling values in the DataFrame

In this section, we are gonna look at how to pick out some sections or parts of the data. We'll look at `head()`, `tail()` and `sample()`.

To demonstrate these, we'll continue with our concatenated dataframe from the previous section

We can use `head()` to look at the top part of the data. Out of the box, it returns the top 5 rows, however modifying the value for `n` can help us pick a specific number of rows from the top.


```python
# We can have look at the top part 
concatenated_dataframe.head(n=3)
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
      <th>age</th>
      <th>gender</th>
      <th>income</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>65</td>
      <td>m</td>
      <td>42</td>
    </tr>
    <tr>
      <th>1</th>
      <td>51</td>
      <td>m</td>
      <td>148</td>
    </tr>
    <tr>
      <th>2</th>
      <td>45</td>
      <td>m</td>
      <td>147</td>
    </tr>
  </tbody>
</table>
</div>



We can use `tail()` to look at the bottom part of the data. Out of the box, it returns the bottom 5 rows, however modifying the value for `n` can help us pick a specific number of rows from the bottom.


```python
# We can look at the bottom part
concatenated_dataframe.tail(n=3)
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
      <th>age</th>
      <th>gender</th>
      <th>income</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>7</th>
      <td>54</td>
      <td>m</td>
      <td>741</td>
    </tr>
    <tr>
      <th>8</th>
      <td>83</td>
      <td>f</td>
      <td>34</td>
    </tr>
    <tr>
      <th>9</th>
      <td>34</td>
      <td>m</td>
      <td>98</td>
    </tr>
  </tbody>
</table>
</div>



We can use `sample()` to look random rows data rows. Out of the box, it returns only 1 row, however modifying the value for `n` can help us pick a specific number of rows at random.


```python
# We can also randomly sample out some values in a DataFrame
concatenated_dataframe.sample(n=3)
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
      <th>age</th>
      <th>gender</th>
      <th>income</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>65</td>
      <td>m</td>
      <td>42</td>
    </tr>
    <tr>
      <th>2</th>
      <td>45</td>
      <td>m</td>
      <td>147</td>
    </tr>
    <tr>
      <th>8</th>
      <td>83</td>
      <td>f</td>
      <td>34</td>
    </tr>
  </tbody>
</table>
</div>



## Selection

In this section we are gonna look at some tricks and techniques we can use to pick some really specific values from the dataframe

#### Selecting, Boolean Indexing and Setting

To demonstrate these, we're creating a little countries dataframe. As you may observe we use `pd.DataFrame()` to create our dataframe and notice we're passing in a dictionary for the value of data.


```python
country_data = pd.DataFrame(data={
    'Country': ['Uganda', 'Kenya', 'Tanzania'],
    'Capital': ['Kampala', 'Nairobi', 'Dodoma'],
    'Population': [11190846, 1303171035, 207847528]
    })
country_data
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
      <th>Country</th>
      <th>Capital</th>
      <th>Population</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Uganda</td>
      <td>Kampala</td>
      <td>11190846</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Kenya</td>
      <td>Nairobi</td>
      <td>1303171035</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Tanzania</td>
      <td>Dodoma</td>
      <td>207847528</td>
    </tr>
  </tbody>
</table>
</div>



We can pick a specific value (or values) from a dataframe by indexing usin the `iloc` and `iat` methods. We insert the row number and the column number of an item that we want to pick from the dataframe in the square brackets. 

We can also use these techniques to replace values in a dataframe.


```python
# position 1
print(country_data.iloc[0, 0])
print(country_data.iloc[2, 1])
```

    Uganda
    Dodoma



```python
# position 2
print(country_data.iat[0, 0])
print(country_data.iat[2, 1])
```

    Uganda
    Dodoma


Ponder:

<i class="bi bi-cursor"></i> How can you use the `pd.DataFrame.iat` method to replace (or modify) a specific value in a dataframe

We can access any value(s) by their row index and column name with the help of the `loc[]` and `at[]` methods.

As you may observe the difference now is that we are using row index and column name instead of row index and column index for `iloc[]` and `iat[]`


```python
# using label
print(country_data.loc[0, 'Capital'])
print(country_data.loc[1, 'Population'])
```

    Kampala
    1303171035



```python
# using label
print(country_data.at[2, 'Population'])
print(country_data.at[1, 'Capital'])
```

    207847528
    Nairobi


We can be able to pick out an entire column by either using the `.` operator or `[]`.

<ul class="cursored-list">
<li><i class="bi bi-cursor"></i> We use the `.` operator when a column name is one single word</li> 
<li><i class="bi bi-cursor"></i> We can use the `[]` when the column name is containing more that one word</li> 
<li><i class="bi bi-cursor"></i> We can also use the `[]` when creating or assigning values to columns in a dataframe</li> 
</ul>


```python
# picking out data from a specific column
country_data.Country
```




    0      Uganda
    1       Kenya
    2    Tanzania
    Name: Country, dtype: object




```python
# another way to pick data from a specific column
country_data['Country']
```




    0      Uganda
    1       Kenya
    2    Tanzania
    Name: Country, dtype: object



The data structure that is returned by the statement is called a `Series`


```python
lakes = ['Albert', 'Turkana', 'Tanganyika']
country_data['Lake'] = lakes

# lets display the updated data
country_data
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
      <th>Country</th>
      <th>Capital</th>
      <th>Population</th>
      <th>Lake</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Uganda</td>
      <td>Kampala</td>
      <td>11190846</td>
      <td>Albert</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Kenya</td>
      <td>Nairobi</td>
      <td>1303171035</td>
      <td>Turkana</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Tanzania</td>
      <td>Dodoma</td>
      <td>207847528</td>
      <td>Tanganyika</td>
    </tr>
  </tbody>
</table>
</div>




```python
# lets check it
type(country_data['Capital'])
```




    pandas.core.series.Series




```python
# Get specific row data (using indexing)
country_data.iloc[0]
```




    Country         Uganda
    Capital        Kampala
    Population    11190846
    Lake            Albert
    Name: 0, dtype: object



We can get a range of rows by passing into `iloc[]` a range of indexes. The demonstration below returns rows of indexes 0 until but not including 2 ie 0 for Uganda and 1 for Kenya


```python
# Get specific rows (using subsetting)
country_data.iloc[0:2]
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
      <th>Country</th>
      <th>Capital</th>
      <th>Population</th>
      <th>Lake</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Uganda</td>
      <td>Kampala</td>
      <td>11190846</td>
      <td>Albert</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Kenya</td>
      <td>Nairobi</td>
      <td>1303171035</td>
      <td>Turkana</td>
    </tr>
  </tbody>
</table>
</div>



We can be able to pickout only rows whose values satisfy a specific condition, this trick is called *boolean indexing*. In the example below, we find all rows whose contry is Uganda


```python
# get all rows that have a column-value matching a specific value
# eg where country is Belgium
country_data[country_data['Country'] == 'Uganda']
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
      <th>Country</th>
      <th>Capital</th>
      <th>Population</th>
      <th>Lake</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Uganda</td>
      <td>Kampala</td>
      <td>11190846</td>
      <td>Albert</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Think about this
country_data['Country'] == 'Tanzania'
```




    0    False
    1    False
    2     True
    Name: Country, dtype: bool



You donot have to submit that 

## Dropping 

In this part we will learn some tricks and techniques to drop or remove some data from a dataframe.


```python
country_data
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
      <th>Country</th>
      <th>Capital</th>
      <th>Population</th>
      <th>Lake</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Uganda</td>
      <td>Kampala</td>
      <td>11190846</td>
      <td>Albert</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Kenya</td>
      <td>Nairobi</td>
      <td>1303171035</td>
      <td>Turkana</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Tanzania</td>
      <td>Dodoma</td>
      <td>207847528</td>
      <td>Tanganyika</td>
    </tr>
  </tbody>
</table>
</div>



We may realize that all our population values are terribly wrong and may choose the entire column. we can do this by using the `drop()` method. We specify the column name and `axis=1` to drop a column. 


```python
# drop a column from a dataframe
country_data.drop(
    labels='Population', 
    axis=1
)
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
      <th>Country</th>
      <th>Capital</th>
      <th>Lake</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Uganda</td>
      <td>Kampala</td>
      <td>Albert</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Kenya</td>
      <td>Nairobi</td>
      <td>Turkana</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Tanzania</td>
      <td>Dodoma</td>
      <td>Tanganyika</td>
    </tr>
  </tbody>
</table>
</div>



To drop many columns, we can pass all the columns to the `drop()` method as a list or tuple, and again specify the `axis=1`.


```python
country_data.drop(
    labels=['Lake', 'Population'], 
    axis=1
)
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
      <th>Country</th>
      <th>Capital</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Uganda</td>
      <td>Kampala</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Kenya</td>
      <td>Nairobi</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Tanzania</td>
      <td>Dodoma</td>
    </tr>
  </tbody>
</table>
</div>



Another way to drop many columns is by passing them to the `drop()` method as a list value to the `columns` parameter. In this case we don't need to specify the `axis`.


```python
# You can drop many columns by passing in a columns list
country_data.drop(columns=['Country', 'Population'])
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
      <th>Capital</th>
      <th>Lake</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Kampala</td>
      <td>Albert</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Nairobi</td>
      <td>Turkana</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Dodoma</td>
      <td>Tanganyika</td>
    </tr>
  </tbody>
</table>
</div>



To drop a row or many rows, we shall pass the index(es) as labels to the `drop` method method and optionally set `axis=0`. It turns out that the default value for `axis` is actually 0. Below, we have some two examples.


```python
# how to drop 1 row
country_data.drop(labels=0) # drops out Uganda
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
      <th>Country</th>
      <th>Capital</th>
      <th>Population</th>
      <th>Lake</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>Kenya</td>
      <td>Nairobi</td>
      <td>1303171035</td>
      <td>Turkana</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Tanzania</td>
      <td>Dodoma</td>
      <td>207847528</td>
      <td>Tanganyika</td>
    </tr>
  </tbody>
</table>
</div>




```python
# how to drop row data
country_data.drop(labels=[0, 2], axis=0)
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
      <th>Country</th>
      <th>Capital</th>
      <th>Population</th>
      <th>Lake</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>Kenya</td>
      <td>Nairobi</td>
      <td>1303171035</td>
      <td>Turkana</td>
    </tr>
  </tbody>
</table>
</div>



This drops rows in indexes 0 and 2, ie Uganda and Tanzania

#### Research on:
<i class="bi bi-cursor"></i> sort and rank data

## Retrieving information about DataFrame

Pandas offers us some quick way with which we can find some quick information about our dataset (or dataframe)

#### Basic Information


```python
country_data = pd.DataFrame({
    'Country': ['Uganda', 'Kenya', 'Tanzania'],
    'Capital': ['Kampala', None, None],
    'Population': [11190846, 1303171035, 207847528]
    })

country_data
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
      <th>Country</th>
      <th>Capital</th>
      <th>Population</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Uganda</td>
      <td>Kampala</td>
      <td>11190846</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Kenya</td>
      <td>None</td>
      <td>1303171035</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Tanzania</td>
      <td>None</td>
      <td>207847528</td>
    </tr>
  </tbody>
</table>
</div>



We can use the `shape` attribute to obtain the number of rows and columns available in our dataset as illustrated.


```python
# shape of a dataframe (ie rows, columns)
country_data.shape
```




    (3, 3)



If you're only interested in the number of rows you can use the `len()` method to find that eg


```python
# len of a dataframe (ie no of rows)
len(country_data)
```




    3



If you are interested in looking at the columns (column names), you can use the `columns` attribute to obtain the `Index` object of column names


```python
# Get all columns in a dataframe
country_data.columns
```




    Index(['Country', 'Capital', 'Population'], dtype='object')



We can also use the `len()` method on this `Index` object to obtain the number of columns


```python
len(country_data.columns)
```




    3



We can use the `info()` method to find some information on our dataframe ie:

<ul class="cursored-list">
<li><i class="bi bi-cursor"></i> Columns (All columns in the dataframe)</li> 
<li><i class="bi bi-cursor"></i> Non-Null Count (Number of non null values per column)</li> 
<li><i class="bi bi-cursor"></i> Dtype (Data type each column)</li> 
<li><i class="bi bi-cursor"></i> Total number of entries (rows)</li> 
</ul>


```python
# get some basic info about the dataframe
country_data.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 3 entries, 0 to 2
    Data columns (total 3 columns):
     #   Column      Non-Null Count  Dtype 
    ---  ------      --------------  ----- 
     0   Country     3 non-null      object
     1   Capital     1 non-null      object
     2   Population  3 non-null      int64 
    dtypes: int64(1), object(2)
    memory usage: 204.0+ bytes


By using the `count()` method on the dataframe, we can obtain the number of non-null values per a column


```python
# Count non-null values in each column
country_data.count()
```




    Country       3
    Capital       1
    Population    3
    dtype: int64



#### Summary

Finally, we can use the `describe()` to obtain some quick summary (descriptive) statistics about our data eg count, mean, standard deviation, minimum and maximum values, percentile


```python
# summary statistics
country_data.describe()
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
      <th>Population</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>3.000000e+00</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>5.074031e+08</td>
    </tr>
    <tr>
      <th>std</th>
      <td>6.961346e+08</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.119085e+07</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>1.095192e+08</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>2.078475e+08</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>7.555093e+08</td>
    </tr>
    <tr>
      <th>max</th>
      <td>1.303171e+09</td>
    </tr>
  </tbody>
</table>
</div>



#### Research
Find out how to get for specific columns:

<ul class="cursored-list">
<li><i class="bi bi-cursor"></i> mean</li> 
<li><i class="bi bi-cursor"></i> median</li> 
<li><i class="bi bi-cursor"></i> cummulative sum</li> 
<li><i class="bi bi-cursor"></i> minimum</li> 
<li><i class="bi bi-cursor"></i> maximum</li> 
</ul>

<h2>What's on your mind? Put it in the comments!</h2>
<script src="https://utteranc.es/client.js"
        repo="dataideaorg/dataidea-science"
        issue-term="pathname"
        theme="github-light"
        crossorigin="anonymous"
        async>
</script>
