---
interact_link: content/basics/kl-cancun-initial-exploration.ipynb
kernel_name: python3
has_widgets: false
title: 'Notebook Testing'
prev_page:
  url: /getting-started/extensions.html
  title: 'Useful Extensions'
next_page:
  url: /basics/kl-cancun-data-cleaning.html
  title: 'Data Cleaning'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---


<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
%matplotlib inline
import numpy as np
import pandas as pd
import pandas_profiling
import matplotlib.pyplot as plt
import seaborn as sns
import re

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
cancun = pd.read_csv('../data/interim/cancun_unclean.csv')

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# Initial report for exploratory
# profile = cancun.profile_report(title='Pandas Profiling Report')
# profile.to_file(output_file="cancun_unclean.html")

```
</div>

</div>



# Inital Exploration



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
cancun.shape

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
(6673, 37)
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
cancun.isnull().sum().sort_values(ascending=False).head(7)

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
localized_neighborhood    6673
star_rating               3044
response_time             1217
listing_name                 7
bathrooms                    2
bedrooms                     2
currency                     0
dtype: int64
```


</div>
</div>
</div>



## Dealing with Missing Values



Spider scraped 37 fields for around 6673 listings in Cancún but not all fields are important or have no missing values. That said, there is some manual selection to be done. Since there are only 37 fields, this is doable. If there were more (e.g. 100+ columns), manual selection would not be possible and we would have to adopt some rule system to remove low variance/high correlation/high NA columns.

`localized_neighborhood`, `star_rating`, and `response time` have a large number of NaN/NA values. `localized neighborhood` is instantly dropped as it's missing all its values; `star_rating` is substitutable with `avg_rating` and `response time` is not super crucial to our analysis and will also be dropped. There are 2 NAs for both `bedrooms` and `bathrooms` but we can simply drop those rows since there aren't a lot of them.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
COLUMNS_TO_DROP = ['is_business_travel_ready', # Constant Column
                   'localized_neighborhood', # Not Important field
                   'amt_w_service', # Duplicate with price
                   'rate_type', # Constant Column
                   'star_rating', # 45% missing
                   'listing_name', # Not Important field
                   'response_time', # 18% missing + Not descriptive enough
                   'localized_city',
                   'host_id'] # Same with localized_neighborhood

```
</div>

</div>



We also need to separate the `VARIABLES` from the `FILTERS`. We want to create two DataFrames that are joinable by key.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
FILTERS_WITH_URL = ['bathrooms', 'bedrooms', 'num_beds', 'can_instant_book',
                    'is_fully_refundable', 'is_superhost', 'is_new_listing',
                    'room_type_category', 'person_capacity', 'lat', 'lng', 
                     'url']

FILTERS = ['bathrooms', 'bedrooms', 'num_beds', 'can_instant_book',
           'is_fully_refundable', 'is_superhost', 'is_new_listing',
           'room_type_category', 'person_capacity', 'lat', 'lng']

```
</div>

</div>



## Filters



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
cancun_filters = (cancun
                  .drop(columns=COLUMNS_TO_DROP)
                  .dropna(how='any') 
                  .loc[:,FILTERS_WITH_URL] 
                 )                                            

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
cancun_filters.shape

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
(6669, 12)
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
cancun_filters.head(5)

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
      <th>url</th>
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
      <td>https://www.airbnb.com/rooms/20776319</td>
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
      <td>https://www.airbnb.com/rooms/16492050</td>
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
      <td>https://www.airbnb.com/rooms/14266451</td>
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
      <td>https://www.airbnb.com/rooms/17625889</td>
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
      <td>https://www.airbnb.com/rooms/18543147</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
cancun_filters.columns

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
Index(['bathrooms', 'bedrooms', 'num_beds', 'can_instant_book',
       'is_fully_refundable', 'is_superhost', 'is_new_listing',
       'room_type_category', 'person_capacity', 'lat', 'lng', 'url'],
      dtype='object')
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
def exclude_columns(df, columns):
    """
    Exludes specified columns [List] from the DataFrame
    """
    return df[df.columns[~df.columns.isin(columns)]]

```
</div>

</div>



## Variables



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
cancun_variables = (cancun
                    .drop(columns=COLUMNS_TO_DROP)
                    .dropna(how='any') 
                    .pipe(exclude_columns, columns=FILTERS)
                   )

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
cancun_variables.shape

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
(6669, 17)
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
cancun_variables.head(5)

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
      <th>accuracy</th>
      <th>avg_rating</th>
      <th>checkin</th>
      <th>cleanliness</th>
      <th>communication</th>
      <th>currency</th>
      <th>guest_satisfication</th>
      <th>host_reviews</th>
      <th>location</th>
      <th>monthly_price_factor</th>
      <th>picture_count</th>
      <th>price</th>
      <th>response_rate</th>
      <th>reviews_count</th>
      <th>url</th>
      <th>value</th>
      <th>weekly_price_factor</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>10</td>
      <td>4.74</td>
      <td>10</td>
      <td>9</td>
      <td>10</td>
      <td>CAD</td>
      <td>95</td>
      <td>311</td>
      <td>10</td>
      <td>0.88</td>
      <td>19</td>
      <td>22</td>
      <td>100</td>
      <td>50</td>
      <td>https://www.airbnb.com/rooms/20776319</td>
      <td>10</td>
      <td>0.88</td>
    </tr>
    <tr>
      <th>1</th>
      <td>10</td>
      <td>4.93</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>CAD</td>
      <td>99</td>
      <td>147</td>
      <td>10</td>
      <td>0.85</td>
      <td>22</td>
      <td>28</td>
      <td>100</td>
      <td>108</td>
      <td>https://www.airbnb.com/rooms/16492050</td>
      <td>10</td>
      <td>0.90</td>
    </tr>
    <tr>
      <th>2</th>
      <td>10</td>
      <td>4.72</td>
      <td>10</td>
      <td>9</td>
      <td>10</td>
      <td>CAD</td>
      <td>94</td>
      <td>1376</td>
      <td>9</td>
      <td>1.00</td>
      <td>14</td>
      <td>30</td>
      <td>100</td>
      <td>243</td>
      <td>https://www.airbnb.com/rooms/14266451</td>
      <td>9</td>
      <td>1.00</td>
    </tr>
    <tr>
      <th>3</th>
      <td>10</td>
      <td>4.75</td>
      <td>10</td>
      <td>9</td>
      <td>10</td>
      <td>CAD</td>
      <td>95</td>
      <td>179</td>
      <td>10</td>
      <td>0.79</td>
      <td>27</td>
      <td>24</td>
      <td>97</td>
      <td>177</td>
      <td>https://www.airbnb.com/rooms/17625889</td>
      <td>10</td>
      <td>0.93</td>
    </tr>
    <tr>
      <th>4</th>
      <td>10</td>
      <td>4.65</td>
      <td>10</td>
      <td>9</td>
      <td>10</td>
      <td>CAD</td>
      <td>93</td>
      <td>631</td>
      <td>9</td>
      <td>0.80</td>
      <td>18</td>
      <td>21</td>
      <td>100</td>
      <td>194</td>
      <td>https://www.airbnb.com/rooms/18543147</td>
      <td>9</td>
      <td>0.95</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
cancun_variables.columns

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
Index(['accuracy', 'avg_rating', 'checkin', 'cleanliness', 'communication',
       'currency', 'guest_satisfication', 'host_reviews', 'location',
       'monthly_price_factor', 'picture_count', 'price', 'response_rate',
       'reviews_count', 'url', 'value', 'weekly_price_factor'],
      dtype='object')
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
def extract_id(url):
    '''
    Helper funciton that extracts the listing id
    '''
    return re.search('/rooms/(.*)', url).group(1)

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# Create new column listing_key
cancun_variables['listing_key'] = cancun_variables['url'].apply(extract_id)

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# Do the same for cancun_filters
cancun_filters['listing_key'] = cancun_filters['url'].apply(extract_id)

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
cancun_filters.head()

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
      <th>url</th>
      <th>listing_key</th>
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
      <td>https://www.airbnb.com/rooms/20776319</td>
      <td>20776319</td>
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
      <td>https://www.airbnb.com/rooms/16492050</td>
      <td>16492050</td>
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
      <td>https://www.airbnb.com/rooms/14266451</td>
      <td>14266451</td>
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
      <td>https://www.airbnb.com/rooms/17625889</td>
      <td>17625889</td>
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
      <td>https://www.airbnb.com/rooms/18543147</td>
      <td>18543147</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# Export variables and filters

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
cancun_variables.to_csv('cancun_variables.csv', index=False)
cancun_filters.to_csv('cancun_filters.csv', index=False)

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# profile = cancun_variables.profile_report(title='Pandas Profiling Report')
# profile.to_file(output_file="cancun_variables.html")


```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# IDEA: We currently have the issue where we cannot benchmark our model. Perhaps to prove that it is better than random selection,
# scrape the 1st page of each price_range and see how much of our TOP 50 listings overlap with the 1st page Airbnb Listing Rankings,
# compare to a random selection of listings, bootstrap the proportion/median/difference and see whether we have a significance difference.

# Null Hypothesis: Our model will have the same overlap proportion with Airbnb Ranking (1st page) as a random selection
# Alternative Hypothesis: Our model will have more first page listings than a random selection

# This all depends on Airbnb's ranking algorithm. I wonder how it works! 

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# TODO: Variable section within variables. Try to filter down to ~10 to work with

```
</div>

</div>

