---
redirect_from:
  - "/2-python-types/tuples-lists-dicts"
interact_link: content/2-python-types/tuples_lists_dicts.ipynb
kernel_name: python3
has_widgets: false
title: 'Tuples, Lists, and Dictionaries'
prev_page:
  url: /2-python-types/booleans.html
  title: 'Booleans'
next_page:
  url: /2-python-types/type_casting.html
  title: 'Type Casting'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---


# Tuples, Lists, and Dictionaries

As an interactive way to learn about these collection data types, first consider these three problems:

1. Let's say we wanted to store a long list of information in a variable that doesn't change over time? For example, the names of the days of the week don't change at all.

2. Let's say we also wanted to store a long list of information in a variable that changes over time? For instance, the names of all your cats. You might get new kittens and some cats might unfortunately die. You will need to make updates to your list each time something happens.

3. Let's say we wanted to create a phonebook with every CIS105 student's name and phone number. You would need a list of names and a list of phone numbers and some way to find the student's phone number when only given his or her name.




## The Solution -> Tuples, Lists, and Dictionaries

For each of these three problems, there are built-in data types in Python to solve them.

## Tuples

Using Tuples would solve the first problem. Tuples are immutable which means that their value cannot be changed. This
is the perfect data type is store something like the `the days of the week` as they do not change ever. Tuples are quite 
easy to make:



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
days_of_week = ('Monday', 'Tuesday', 'Wednesday', \
                'Thursday', 'Friday', 'Saturday', 'Sunday')

```
</div>

</div>



> **Quick Tip:** The backslash key `\` allows you to continue your statement on the next line! 



which Python then organizes into something that looks like this:

| Index |  Value   |
|-------|----------|
| 0     | Monday   |
| 1     | Tuesday  |
| 2     | Wednesday|
| 3     | Thursday |
| 4     | Friday   |
| 5     | Saturday |
| 6     | Sunday   |



To access a `Value` in our tuple, we do so by indexing! This is exactly the same as what we learned in the `Strings` section.

We can demonstrate with an example: Let's say we want to access `Monday` from the `days_of_week` tuple which in the first position. To do that, we can simply access with:



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
days_of_week[0]

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
'Monday'
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
days_of_week[-1]

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
'Sunday'
```


</div>
</div>
</div>



You can learn about Tuples [here](https://www.w3schools.com/python/python_tuples.asp).



## Lists

Using Lists would solve the second problem. A List is essentially a list of values and are mutable, which means that they can be modified. Lists can also contain different datatypes.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
some_cat_list = ['haku', 'nagi', 'poki', 20, 40]

```
</div>

</div>



Now suppose we were looking through our `some_cat_list` and we realized we wanted to remove `20` as it might've been a happy little accident. To do that, we simply can type




<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
some_cat_list.remove(20)

```
</div>

</div>



Suppose we didn't know the item we wanted to remove but knew its **index**. If we wanted to remove an item in `40`'s location, we can type




<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# Note that since we removed 20, 40's position shifts forward by 1!
del some_cat_list[3] 

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
some_cat_list

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
['haku', 'nagi', 'poki']
```


</div>
</div>
</div>



Now maybe you adopted another cat called kiki and would like to add her to the list. To do that, we could type



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
some_cat_list.append('kiki')

```
</div>

</div>



which would append kiki onto the end of the list. Or if we want to change kiki's name to mei instead given a change of mind, we could do so easily by changing the item at the last index.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
some_cat_list[-1] = 'mei'

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
some_cat_list

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
['haku', 'nagi', 'poki', 'mei']
```


</div>
</div>
</div>



You can learn more about Lists [here](https://www.w3schools.com/python/python_lists.asp).



## Dictionaries

Likewise, we can solve the third problem with using a dictionary. Python dictionaries are conceptually the same as the 
dictionaries we use to look up words! For instance, we typically use a dictionary to look up some word we do not know.
It might be trivial but every `word` in the dictionary maps to some `definition`. Similarly in Python dictionaries, we
have `keys` and `values` where a `key` can map to some `value`. Here we make a dictionary of CIS105 student names and
their phone numbers:



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
some_dict = {
    'Kai': 1231231231,
    'Lin': 3213213213,
    'Racheal': 964296429
}

```
</div>

</div>



Now, say we want to access `Racheal's` phone number from the dictionary. We can simply do so get *getting* her number using her name as the `key`. You can do so in two ways:



### Method 1



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
some_dict.get('Racheal')

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
964296429
```


</div>
</div>
</div>



### Method 2



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
some_dict['Racheal']

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
964296429
```


</div>
</div>
</div>



**However**, this only works when the `key` is present and I would **NOT** recommend using this method. 

Suppose we wanted to find Bob's phone number. However, Bob unfortunately had not been recorded in `some_dict` yet.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
some_dict['Bob']

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">
{:.output_traceback_line}
```

    -------------------------------------------------------------------------

    KeyError                                Traceback (most recent call last)

    <ipython-input-17-0a6d42b2d742> in <module>()
    ----> 1 some_dict['Bob']
    

    KeyError: 'Bob'


```
</div>
</div>
</div>



If the `key` 'Bob' does not exist in the dictionary, this would throw a KeyError which is uninformative and not good.

Now suppose we use the `.get` method to try and get Bob's phone number:



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
some_dict.get('Bob')

```
</div>

</div>



This returns nothing when we run it. If we try and store and then print the output, we will get `None`. However, what's good about using this method is that we can specify an an informative message when the `key` does
not exist .



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
some_dict.get('Bob', 'Key does not exist!')

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
'Key does not exist!'
```


</div>
</div>
</div>



>This is much more informative when debugging!



You may also learn more about Dictionaries [here](https://www.w3schools.com/python/python_dictionaries.asp).

