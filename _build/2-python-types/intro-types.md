---
interact_link: content/2-python-types/intro-types.ipynb
kernel_name: python3
has_widgets: false
title: '2. Python Data Types'
prev_page:
  url: /1-intro-programming/call-expressions.html
  title: 'Call Expressions'
next_page:
  url: /2-python-types/numbers.html
  title: 'Numbers'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---


# Introduction to Types

Every value in Python has a type. In this section I will introduce the most common, basic types that are built into Python. To check the type of a value, we can use the Python built-in `type()` function.



## Numbers

The first category of types I will go through in detail is Numbers. Integers, floating point numbers, and complex numbers fall under Python's number category. They are defined as `int`,
`float`, and `complex`. I personally have not used `complex` yet but have used `int` and `float` almost every day.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
type(9642)

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
int
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
type(9642.0)

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
float
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
type(1+2j)

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
complex
```


</div>
</div>
</div>



## Strings

Next we have strings. As you've seen in the previous section, a sequence of one or more characters enclosed within single quotes ‘, double quotes ", or even triple quotes ''' is considered as a String in Python. Any letter, number or symbol could be a part of the sting.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
type('I like cats')

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
str
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
type("meow")

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
str
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
type('''meoooooow''')

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
str
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
type('9642')

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
str
```


</div>
</div>
</div>



## Booleans



Last but not least, we introduce booleans. A boolean is a data type that almost every programming language has. A Boolean in Python can have two values: `True` or `False`. These values are constants and can be used to assign or compare boolean values.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
type(True)

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
bool
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
type(False)

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
bool
```


</div>
</div>
</div>



> Note that there are many other Python data types that you will encounter in our Pythonic journey! Don't be intimidated as there are many data types that even I haven't heard of. Besides `Numbers`, `Strings`, and `Booleans`, I will also going over container data types like `Lists`, `Tuples`, and `Dictionaries` that can contain `Booleans`, `Numbers`, and `Strings` soon.

