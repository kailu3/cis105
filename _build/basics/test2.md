---
interact_link: content/basics/test2.ipynb
kernel_name: python3
has_widgets: false
title: 'Test2'
prev_page:
  url: /features/notebooks.html
  title: 'Notebook'
next_page:
  url: https://github.com/kailu3/think-data
  title: 'GitHub repository'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---


<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
import numpy as np
import pandas as pd
import json
import os

```
</div>

</div>



## Reads `.json` Files and Combines them into `.csv`



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
df = pd.DataFrame()
for num in np.arange(15, 995, 10):
    lower_bound = str(num)
    upper_bound = str(num + 10)
    filename = lower_bound + "to" + upper_bound + ".json"
    # Check if file is empty
    if os.stat(filename).st_size != 0:    
        some_df = pd.read_json(filename)
        df = pd.concat([df, some_df])

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
len(df)

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
6414
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
df.drop_duplicates(subset='url', keep='first', inplace=True)


```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
len(df)

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
5796
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
df.shape

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
(5796, 37)
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
df.to_csv('cancun_scrape_5.csv', index=False)

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
df[df['url'] == 'https://www.airbnb.com/rooms/10823831']

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
      <th>amt_w_service</th>
      <th>avg_rating</th>
      <th>bathrooms</th>
      <th>bedrooms</th>
      <th>can_instant_book</th>
      <th>checkin</th>
      <th>cleanliness</th>
      <th>communication</th>
      <th>currency</th>
      <th>...</th>
      <th>price</th>
      <th>rate_type</th>
      <th>response_rate</th>
      <th>response_time</th>
      <th>reviews_count</th>
      <th>room_type_category</th>
      <th>star_rating</th>
      <th>url</th>
      <th>value</th>
      <th>weekly_price_factor</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>76</th>
      <td>10</td>
      <td>236</td>
      <td>4.8</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>True</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>CAD</td>
      <td>...</td>
      <td>236</td>
      <td>nightly</td>
      <td>100</td>
      <td>within an hour</td>
      <td>69</td>
      <td>entire_home</td>
      <td>5.0</td>
      <td>https://www.airbnb.com/rooms/10823831</td>
      <td>10</td>
      <td>1.0</td>
    </tr>
  </tbody>
</table>
<p>1 rows × 37 columns</p>
</div>
</div>


</div>
</div>
</div>



## Reads multiple `.csv` Files and Combines them into one `.csv`



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
cancun_df = pd.DataFrame()
growth_list = []
for num in np.arange(1, 6):
    filename = "cancun_scrape_{0}.csv".format(num)
    some_df = pd.read_csv(filename)
    
    # Calculate dataframe size before
    prev_size = len(cancun_df)
    
    # Combine dataframes and drop the duplicates
    cancun_df = pd.concat([cancun_df, some_df])
    cancun_df = cancun_df.drop_duplicates(subset='url', keep='first')

    # Calculate dataframe size after
    after_size = len(cancun_df)
    
    # Calculate growth
    growth = after_size - prev_size
    growth_list.append(growth)
    
    print("On iteration {0}, we added {1} new rows".format(num, growth))

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">
{:.output_stream}
```
On iteration 1, we added 5151 new rows
On iteration 2, we added 144 new rows
On iteration 3, we added 747 new rows
On iteration 4, we added 462 new rows
On iteration 5, we added 169 new rows
```
</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
cancun_df.shape

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
cancun_df.to_csv('cancun_final.csv', index=False)

```
</div>

</div>

