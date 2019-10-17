
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

## Simple arithmetic

Use a lambda function to create a new column called `'stars_squared'` by squaring the stars column.


```python
# Your code here

```

## Dates
Select the month from the date string using a lambda function.


```python
# Your code here

```

## What is the average number of words for a yelp review?
Do this with a single line of code!


```python
# Your code here

```

## Create a new column for the number of words in the review


```python
# Your code here

```

## Rewrite the following as a lambda function

Create a new column `'Review_Length'` by applying this lambda function to the `'Review_num_words'` column. 


```python
# Rewrite the following function as a lambda function
def rewrite_as_lambda(value):
    if len(value) < 50:
        return 'Short'
    elif len(value) < 80:
        return 'Medium'
    else:
        return 'Long'
# Hint: nest your if, else conditionals

df['Review_length'] = None

```

## Level Up: Dates Advanced!
<img src="images/world_map.png" width="600">  

Print the first five rows of the `'date'` column. 


```python
# Your code here

```

Overwrite the `'date'` column by reordering the month and day from `YYYY-MM-DD` to `DD-MM-YYYY`. Try to do this using a lambda function.


```python
# Your code here

```

## Summary

Great! Hopefully, you're getting the hang of lambda functions now! It's important not to overuse them - it will often make more sense to define a function so that it's reusable elsewhere. But whenever you need to quickly apply some simple processing to a collection of data you have a new technique that will help you to do just that. It'll also be useful if you're reading someone else's code that happens to use lambdas.
