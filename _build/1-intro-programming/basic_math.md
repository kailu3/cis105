---
redirect_from:
  - "/1-intro-programming/basic-math"
interact_link: content/1-intro-programming/basic_math.ipynb
kernel_name: python3
has_widgets: false
title: 'Basic Math Expressions'
prev_page:
  url: /1-intro-programming/hello-world.html
  title: '1. Introduction to Programming'
next_page:
  url: /1-intro-programming/variables.html
  title: 'Python Variables'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---


# Basic Math Operations

Let's first try some simple commands. In this section, we learn to use Python as a calculator to perform mathematical operations like addition, subtraction, multiplication, and division. The examples so far are basic and I would recommend playing around with some examples on your own.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# Addition
2 + 2

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
4
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# Subtraction
4 - 1

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
3
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# Multiplication
2 * 3

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
6
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# Division
5 / 2

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
2.5
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# Integer Division
5 // 2

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
2
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# Exponents
4 ** 3

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
64
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# Modulo -> remainder computation
123 % 2

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
1
```


</div>
</div>
</div>



*Here is a quick summary of common operations used:*




| Operator	    |          Description                   | Syntax  | Example | Result
|---------------|----------------------------------------|---------|---------|-------
| +             | Addition                               | x + y   | 2 + 2   | 4
| -             | Subtraction                            | x - y   | 5 - 3   | 2
| *             | Multiplication                         | x * y   | 3 * 4   | 12
| /             | Division (float)                       | x / y   | 3 / 4   | 0.75
| //            | Division (floor)                       | x // y  | 3 // 4  | 0
| %             | Modulus (remainder)                    | x % y   | 5 % 3   | 2
| **            | Exponential                            | x ** y  | 2 ** 3  | 8



>Another thing to note is that Python expressions obey the rules of precedence as we are familar with. We can use parentheses to group together expressions that we want to be evaluated in higher priority:



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
2 + 2 * (2 - 2) ** 2 / 4

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
2.0
```


</div>
</div>
</div>

