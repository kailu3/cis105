---
interact_link: content/2-python-types/booleans.ipynb
kernel_name: python3
has_widgets: false
title: 'Booleans'
prev_page:
  url: /2-python-types/strings.html
  title: 'Strings'
next_page:
  url: /2-python-types/tuples_lists_dicts.html
  title: 'Tuples, Lists, and Dictionaries'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---


# Booleans



Boolean values only come in two flavours: `True` and `False`. There's not much for me to talk about right now but these are going to be super useful later when we encounter pandas boolean indexing in further chapters as we try to slice our data. More on that later~



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
True

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
True
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
False

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
False
```


</div>
</div>
</div>



### Comparisons

Booleans are always the result of any comparison between two objects. Comparison operators come in five flavours. Here's a quick summary:


| Operator	    |          Description                   | Syntax     | Example | Result
|---------------|----------------------------------------|------------|---------|-------
| ==            | Equals                                 | x == y     | 2 == 2  | True
| >             | Strictly Greater than                  | x > y      | 5 > 3   | True
| <             | Strictly Less than                     | x < y      | 5 < 3   | False
| >=            | Greater than or Equal to               | x >= y     | 4 >= 4  | True
| <=            | Less than or Equal to                  | x <= y     | 4 <= 4  | True





We typically use Boolean values to make comparisons between two objects. While this may seem trivial at this point, it is in fact very powerful in supporting quick and effective data analysis tasks. Here's a quick sneak peak at what we'll be learning later on this semester:



### A Quick Case Study



**Scenario:** Let's say you are looking for an Airbnb home to stay in for an upcoming trip. Now, you can't just pick any Airbnb listing as you would most likely need to filter the possibilities down to the listings that most satisfy your personal requirements. Now, suppose you had a dataset containing all of the listings in the location you are looking at. However, there are some contraints that you need to consider:
- You need to look for listings less than 100 usd to be able to reimburse your trip
- Since you are travelling with a classmate, you would prefer two beds in your Airbnb home
- You want a listing that you can book instantly since your flight leaves tomorrow



> `.head()` shows the first few rows of a dataset. You can also specify how many rows you want to return! On the other hand, `.tail()` returns the last few rows of a dataset



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
import pandas as pd

# Importing Data
url = "https://raw.githubusercontent.com/kailu3/think-data/master/content/data/airbnb.csv"
dataset = pd.read_csv(url)
dataset.head(5)

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">



<div markdown="0" class="output output_html">
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
      <th>bathrooms</th>
      <th>bedrooms</th>
      <th>num_beds</th>
      <th>can_instant_book</th>
      <th>price</th>
      <th>listing_id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.0</td>
      <td>1</td>
      <td>1</td>
      <td>True</td>
      <td>22</td>
      <td>20776319</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1.0</td>
      <td>1</td>
      <td>1</td>
      <td>False</td>
      <td>28</td>
      <td>16492050</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1.5</td>
      <td>1</td>
      <td>1</td>
      <td>True</td>
      <td>30</td>
      <td>14266451</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1.0</td>
      <td>2</td>
      <td>2</td>
      <td>True</td>
      <td>24</td>
      <td>17625889</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1.0</td>
      <td>1</td>
      <td>2</td>
      <td>True</td>
      <td>21</td>
      <td>18543147</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



>To satisfy these contraints, we will need to use `boolean indexing` which makes uses of `Comparisons` and `Booleans`!



This is the syntax to get listings less than 100 usd from the `dataset`. You'll learn the syntax later in class but pay attention to `dataset['price'] < 100`. The whole expression means that I only want rows where the `price` column is `<` 100.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
dataset.loc[dataset['price'] < 100]

```
</div>

</div>



To get listings that have two beds, the process is similar. Here pay attention to `dataset['num_beds']`. The whole expression means that I only want rows where the number of beds is at least 2.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
dataset.loc[dataset['num_beds'] >= 2]

```
</div>

</div>



Finally, we want to be able to instantly book the listing which refers to the `can_instant_book` column. The datatype of this column is Boolean so we keep rows where the value is `True`. This again is similar:



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
dataset.loc[dataset['can_instant_book'] == True]

```
</div>

</div>



#### Combining the 3 statements

Now let's combine the 3 statements and select all the listings where all three conditions satisfy:



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
(
    dataset
    .loc[dataset['price'] < 100]
    .loc[dataset['num_beds'] >= 2]
    .loc[dataset['can_instant_book'] == True]
    .shape
)

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
(1363, 6)
```


</div>
</div>
</div>



> `.shape` returns the dimensions of the dataframe after we applied the 3 filters on it. It looks like there are 1363 listings that satisfy all three constraints. I guess we can filter down even more to get the perfect listing! :)

