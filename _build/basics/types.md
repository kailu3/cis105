---
title: 'Types'
prev_page:
  url: /basics/hello_world.html
  title: 'Programming in Python'
next_page:
  url: /basics/type_casting.html
  title: 'Type Casting'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---
# Introduction to Types

Every value in Python has a type. First let's have a short discussion of the most common, basic types that are built into Python.
We can check the type of each value by using the Python built-in `type()` function.

## Booleans

A boolean is a data type that almost every programming language has. A Boolean in Python can have two values: `True` or `False`.
These values are constants and can be used to assign or compare boolean values.

```python
In [1]: type(True)
Out[1]: bool

In [2]: type(False)
Out[2]: bool
```

## Numbers

Integers, floating point numbers, and complex numbers fall under Python's number category. They are defined as `int`,
`float`, and `complex`. I personally have not used `complex` yet but have used `int` and `float` almost every day.

```python
In [1]: type(9642)
Out[1]: int

In [2]: type(9642.0)
Out[2]: float

In [3]: type(1+2j)
Out[3]: complex
```

## Strings

As you've seen in the previous section, a sequence of one or more characters enclosed within either single quotes ‘ or double quotes ” is considered as a String in Python. Any letter, number or symbol could be a part of the sting.

```python
In [1]: type('I like cats')
Out[1]: string

In [2]: type("meow")
Out[2]: string

In [3]: type('9642')
Out[3]: string
```

> There are other commonly used data types such as `Lists`, `Tuples`, and `Dictionaries` that can contain Booleans, Numbers, and Strings.
I will be going over them in the next section.

