---
redirect_from:
  - "/basics/hello-world"
interact_link: content/basics/hello_world.ipynb
kernel_name: python3
has_widgets: false
title: 'Hello World'
prev_page:
  url: /getting-started/extensions.html
  title: 'Useful Extensions'
next_page:
  url: /basics/math.html
  title: 'Basic Math'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---


# Hello World

In this section, I want to introduce the basics of using Python for data analysis. While the following subsections are relatively straightforward, I guarantee that you will be using everything in here throughout your data science journey!

The most simple function and in my opinion one the most useful functions is the `print()` statement. This function
is extremely useful for debugging code and checking variable values. To print something in Python 3, just write the following and
run the cell by pressing `Shift+Enter`:



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
print('Hello World')

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">
{:.output_stream}
```
Hello World
```
</div>
</div>
</div>



## Assigning Values to Variables

Sometimes you may want to print a variable to see its contents. Variables are essentially reserved memory locations to store values. When you **assign** some value to a variable using `=`, the operand to the left of `=` is the name of the variable and the operand
to the right of the `=` operator is the value stored in the variable. For instance,



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
apple = 100
banana = 'hello'
kiwi = True
print(apple, banana, kiwi)

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">
{:.output_stream}
```
100 hello True
```
</div>
</div>
</div>



## Passing Variables to Strings

You may want to print a sentence with a variable at times. Some ways to do this are



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

