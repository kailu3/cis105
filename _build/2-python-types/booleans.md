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



### Example



**Scenario:** Let's say you are looking for an Airbnb home to stay in for an upcoming trip. Now, you can't just pick any Airbnb listing as you would most likely need to filter the possibilities down to the listings that most satisfy your personal requirements. Now, suppose you had a dataset containing all of the listings in the location you are looking at. However, there are some contraints that you need to consider:
- You need to look for listings <100 usd to be able to reimburse your trip
- Since you are travelling with a classmate, you would prefer two beds in your Airbnb home
- You want a listing that you can book instantly since your flight leaves tomorrow



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
import pandas as pd

# Importing Data
url = "https://raw.githubusercontent.com/kailu3/think-data/master/content/data/airbnb.csv"
dataset = pandas.read_csv(url)
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
      <th>is_fully_refundable</th>
      <th>is_superhost</th>
      <th>is_new_listing</th>
      <th>room_type_category</th>
      <th>person_capacity</th>
      <th>lat</th>
      <th>lng</th>
      <th>price</th>
      <th>url</th>
      <th>listing_key</th>
      <th>price_in_usd</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.0</td>
      <td>1.0</td>
      <td>1</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>False</td>
      <td>private_room</td>
      <td>2</td>
      <td>21.13566</td>
      <td>-86.76741</td>
      <td>22</td>
      <td>https://www.airbnb.com/rooms/20776319</td>
      <td>20776319</td>
      <td>16.541353</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1.0</td>
      <td>1.0</td>
      <td>1</td>
      <td>False</td>
      <td>True</td>
      <td>True</td>
      <td>False</td>
      <td>private_room</td>
      <td>2</td>
      <td>21.14571</td>
      <td>-86.84190</td>
      <td>28</td>
      <td>https://www.airbnb.com/rooms/16492050</td>
      <td>16492050</td>
      <td>21.052632</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1.5</td>
      <td>1.0</td>
      <td>1</td>
      <td>True</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>private_room</td>
      <td>2</td>
      <td>21.13119</td>
      <td>-86.76394</td>
      <td>30</td>
      <td>https://www.airbnb.com/rooms/14266451</td>
      <td>14266451</td>
      <td>22.556391</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1.0</td>
      <td>2.0</td>
      <td>2</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>False</td>
      <td>entire_home</td>
      <td>5</td>
      <td>21.15737</td>
      <td>-86.83975</td>
      <td>24</td>
      <td>https://www.airbnb.com/rooms/17625889</td>
      <td>17625889</td>
      <td>18.045113</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1.0</td>
      <td>1.0</td>
      <td>2</td>
      <td>True</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>entire_home</td>
      <td>3</td>
      <td>21.15327</td>
      <td>-86.85548</td>
      <td>21</td>
      <td>https://www.airbnb.com/rooms/18543147</td>
      <td>18543147</td>
      <td>15.789474</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>

