# Lambda Functions - Lab

## Introduction

In this lab, you'll get some hands-on practice creating and using lambda functions.

## Objectives

In this lab you will:

* Create lambda functions to use as arguments of other functions   
* Use the `.map()` or `.apply()` method to apply a function to a pandas series or DataFrame

## Lambda Functions


```python
import pandas as pd
df = pd.read_csv('Yelp_Reviews.csv', index_col=0)
df.head(2)
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
      <th>business_id</th>
      <th>cool</th>
      <th>date</th>
      <th>funny</th>
      <th>review_id</th>
      <th>stars</th>
      <th>text</th>
      <th>useful</th>
      <th>user_id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>pomGBqfbxcqPv14c3XH-ZQ</td>
      <td>0</td>
      <td>2012-11-13</td>
      <td>0</td>
      <td>dDl8zu1vWPdKGihJrwQbpw</td>
      <td>5</td>
      <td>I love this place! My fiance And I go here atl...</td>
      <td>0</td>
      <td>msQe1u7Z_XuqjGoqhB0J5g</td>
    </tr>
    <tr>
      <th>2</th>
      <td>jtQARsP6P-LbkyjbO1qNGg</td>
      <td>1</td>
      <td>2014-10-23</td>
      <td>1</td>
      <td>LZp4UX5zK3e-c5ZGSeo3kA</td>
      <td>1</td>
      <td>Terrible. Dry corn bread. Rib tips were all fa...</td>
      <td>3</td>
      <td>msQe1u7Z_XuqjGoqhB0J5g</td>
    </tr>
  </tbody>
</table>
</div>



## Simple arithmetic

Use a lambda function to create a new column called `'stars_squared'` by squaring the stars column.


```python
df['stars_squared'] = df['stars'].map(lambda x: x**2)
df.head(2)
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
      <th>business_id</th>
      <th>cool</th>
      <th>date</th>
      <th>funny</th>
      <th>review_id</th>
      <th>stars</th>
      <th>text</th>
      <th>useful</th>
      <th>user_id</th>
      <th>stars_squared</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>pomGBqfbxcqPv14c3XH-ZQ</td>
      <td>0</td>
      <td>2012-11-13</td>
      <td>0</td>
      <td>dDl8zu1vWPdKGihJrwQbpw</td>
      <td>5</td>
      <td>I love this place! My fiance And I go here atl...</td>
      <td>0</td>
      <td>msQe1u7Z_XuqjGoqhB0J5g</td>
      <td>25</td>
    </tr>
    <tr>
      <th>2</th>
      <td>jtQARsP6P-LbkyjbO1qNGg</td>
      <td>1</td>
      <td>2014-10-23</td>
      <td>1</td>
      <td>LZp4UX5zK3e-c5ZGSeo3kA</td>
      <td>1</td>
      <td>Terrible. Dry corn bread. Rib tips were all fa...</td>
      <td>3</td>
      <td>msQe1u7Z_XuqjGoqhB0J5g</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>



## Dates
Select the month from the date string using a lambda function.


```python
df['date'].map(lambda x: x[5:7]).head()
```




    1     11
    2     10
    4     09
    5     02
    10    06
    Name: date, dtype: object



## What is the average number of words for a yelp review?
Do this with a single line of code!


```python
df['text'].map(lambda x: len(x.split())).mean()
```




    77.06551724137931



## Create a new column for the number of words in the review


```python
df['Review_num_words'] = df['text'].map(lambda x: len(x.split()))
df.head(2)
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
      <th>business_id</th>
      <th>cool</th>
      <th>date</th>
      <th>funny</th>
      <th>review_id</th>
      <th>stars</th>
      <th>text</th>
      <th>useful</th>
      <th>user_id</th>
      <th>stars_squared</th>
      <th>Review_num_words</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>pomGBqfbxcqPv14c3XH-ZQ</td>
      <td>0</td>
      <td>2012-11-13</td>
      <td>0</td>
      <td>dDl8zu1vWPdKGihJrwQbpw</td>
      <td>5</td>
      <td>I love this place! My fiance And I go here atl...</td>
      <td>0</td>
      <td>msQe1u7Z_XuqjGoqhB0J5g</td>
      <td>25</td>
      <td>58</td>
    </tr>
    <tr>
      <th>2</th>
      <td>jtQARsP6P-LbkyjbO1qNGg</td>
      <td>1</td>
      <td>2014-10-23</td>
      <td>1</td>
      <td>LZp4UX5zK3e-c5ZGSeo3kA</td>
      <td>1</td>
      <td>Terrible. Dry corn bread. Rib tips were all fa...</td>
      <td>3</td>
      <td>msQe1u7Z_XuqjGoqhB0J5g</td>
      <td>1</td>
      <td>30</td>
    </tr>
  </tbody>
</table>
</div>



## Rewrite the following as a lambda function

Create a new column `'Review_Length'` by applying this lambda function to the `'Review_num_words'` column. 


```python
# Rewrite the following function as a lambda function
def rewrite_as_lambda(value):
    if len(value) > 50:
        return 'Short'
    elif len(value) < 80:
        return 'Medium'
    else:
        return 'Long'
# Hint: nest your if, else conditionals

df['Review_length'] = df['Review_num_words'].map(lambda x: 'Short' if x < 50 else ('Medium' if x < 80 else 'Long'))
df['Review_length'].value_counts(normalize=True)
```




    Short     0.493103
    Long      0.294636
    Medium    0.212261
    Name: Review_length, dtype: float64



## Level Up: Dates Advanced!
<img src="images/world_map.png" width="600">  

Print the first five rows of the `'date'` column. 


```python
df['date'].head()
```




    1     2012-11-13
    2     2014-10-23
    4     2014-09-05
    5     2011-02-25
    10    2016-06-15
    Name: date, dtype: object



Overwrite the `'date'` column by reordering the month and day from `YYYY-MM-DD` to `DD-MM-YYYY`. Try to do this using a lambda function.


```python
df['date'] = df['date'].map(lambda x: '{}-{}-{}'.format(x[-2:], x[5:7], x[:4]))
df['date'].head()
```




    1     13-11-2012
    2     23-10-2014
    4     05-09-2014
    5     25-02-2011
    10    15-06-2016
    Name: date, dtype: object



## Summary

Great! Hopefully, you're getting the hang of lambda functions now! It's important not to overuse them - it will often make more sense to define a function so that it's reusable elsewhere. But whenever you need to quickly apply some simple processing to a collection of data you have a new technique that will help you to do just that. It'll also be useful if you're reading someone else's code that happens to use lambdas.
