---
interact_link: content/1-intro-programming/variables.ipynb
kernel_name: python3
has_widgets: false
title: 'Python Variables'
prev_page:
  url: /1-intro-programming/basic_math.html
  title: 'Basic Math Expressions'
next_page:
  url: /1-intro-programming/call-expressions.html
  title: 'Call Expressions'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---


# Python Variables



Using variables is essential to all programming languages. I like to think of a variable as a nametag attached to an object. Variables are essentially reserved memory locations to store values. In Python, variables do not need to be declared or defined in advance like other programming languages such as Java. To create a variable, we just assign it a value and then can start using it. Assignment is done with a single equals sign `=`



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
colour_of_car = "red"

```
</div>

</div>



> This is read as `colour_of_car` is assigned the value 'red'. Once this is done, `colour_of_car` can be used in any statement or expression, and its value will be substituted.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
print(colour_of_car)

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">
{:.output_stream}
```
red
```
</div>
</div>
</div>



Python also supports multiple assignment, which allows you to assign values to multiple variables in one line.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
x, y, z = 1, 2, 3
print(x + y + z)

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">
{:.output_stream}
```
6
```
</div>
</div>
</div>



You can also assign the same value to multiple variables in one line. I don't use this one often though!



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
x = y = z = "cat"
print(x)
print(y)
print(z)

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">
{:.output_stream}
```
cat
cat
cat
```
</div>
</div>
</div>



## Variable Names



Here are some rules for naming your variables:
- A variable name must start with a letter or the `_` character
- A variable name cannot start with a number
- A variable name can only contain alpha-numeric characters and underscores (A-z, 0-9, and `_` )
- Variable names are case-sensitive (cat, Cat, and caT are three different variables)



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
cat = 2
print(Cat) # mistyping variable names is a very common error!

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">
{:.output_traceback_line}
```

    -----------------------------------------------------------------------

    NameError                             Traceback (most recent call last)

    <ipython-input-6-c8a2b97be72a> in <module>
          1 cat = 2
    ----> 2 print(Cat) # mistyping variable names is a very common error!
    

    NameError: name 'Cat' is not defined


```
</div>
</div>
</div>



> As a quick tip, when typing your variable you can press `TAB` to bring up a drop down or autocomplete your variable name.



## Passing Variables to Strings

You may want to print a message with a variable at times to help with debugging. Some ways to do this are



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
apple = 12
print('Apples are', apple, 'dollars a dozen')

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">
{:.output_stream}
```
Apples are 12 dollars a dozen
```
</div>
</div>
</div>



**Note:** When you concatenate Strings (text enclosed in '') together, all components must be of String Type. Here, I used
the `str()` function to cast the integer 12 into the String `12`. More on types and casting later.


*My usual way of passing variables into a String is to use formatting:*



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
print('apples are {} dollars a dozen'.format(apple))

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">
{:.output_stream}
```
apples are 12 dollars a dozen
```
</div>
</div>
</div>



In Python 3.6, there was an added string formatting approach called `f-strings`. This is another way of formatting
strings that I am still getting used to using more of. Here's a simple example



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
print(f'apples are {apple} dollars a dozen')

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">
{:.output_stream}
```
apples are 12 dollars a dozen
```
</div>
</div>
</div>



You can also do inline arithmetic with this formatting approach!



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
a = 5
b = 10
print(f'Five plus ten is {a + b} and not {2 * (a + b)}.')

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">
{:.output_stream}
```
Five plus ten is 15 and not 30.
```
</div>
</div>
</div>



> As you can see, there are multiple ways to pass variables to a String in Python. Similarly, there are many, many ways
to do most things in Python. These snippets in this book are just how I approach Python. You should not be limited by
them!

