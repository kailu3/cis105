---
interact_link: content/1-intro-programming/hello-world.ipynb
kernel_name: python3
has_widgets: false
title: '1. Introduction to Programming'
prev_page:
  url: /0-getting-started/extensions.html
  title: 'Useful Extensions'
next_page:
  url: /1-intro-programming/basic_math.html
  title: 'Basic Math Expressions'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---


# Hello World

In this section, I want to introduce the basics of programming. While the following subsections are relatively straightforward, I guarantee that you will be using everything in here throughout your data science journey!

The most simple function and in my opinion the most useful function is the `print()` statement. This function
is extremely useful for debugging code and checking variable values. To print something in Python 3, just write the following and
run the cell by pressing `Shift+Enter`:



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
print("Hello World")

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



You could use single quotation marks and do:



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



Single quotation marks do pretty much everything double quotation marks do. Double quotation marks are preferred as they can handle apostrophes in strings. For example:



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
print("Hello! I'm a cat!")

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">
{:.output_stream}
```
Hello! I'm a cat!
```
</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
print('Hello! I'm a cat!')

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">
{:.output_traceback_line}
```

      File "<ipython-input-12-5a83290815f4>", line 1
        print('Hello! I'm a cat!')
                        ^
    SyntaxError: invalid syntax



```
</div>
</div>
</div>

