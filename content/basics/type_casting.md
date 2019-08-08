
# Type Casting

## Introduction to Data Types in Python

Users of Python are often drawn-in by its ease of use, one piece of which is dynamic typing. While a statically-typed language like Java or C requires each variable to be explicitly declared, a dynamically-typed language like Python skips this specification. As a simple demonstration:

```java
String a = 'Hello!'
int b = 2
boolean c = true
```

As you can see, each variable needs to explicitly declared a type. In contrast, the equivilant in Python is as follows:

```python
a = 'Hello'
b = 2
c = True
```

In short, data tyes in Java or C are explicitly declared, while in Python the types are dynamically inferred. This means, for example, that we can assign any kind of data to any variable:

```python
x = 4
x = 'four'
```

## Datatype Conversion

Sometimes, we may need to convert a variable from one datatype to another in Python. For instance, say we want to again print out a message with a variable. Normally, the `print` statement expects only `str` inputs, but what if your variable was an `int`?

```python
x = 123
print('My password is ' + x)
```

You can try this out and you will get a `TypeError` as `print` is expecting string inputs. Since x is an `int`, this would not work! To convert `x` to a string, you can simply use the `str()` conversion function.

```python
x = 123
print('My password is ' + str(x))
```

Some common type conversion operations are:

- `int()` converts type to integer
- `float()` converts type to float
- `str()` converts type to string
- `list()` converts  type to list
- `dict()` converts a tuple of order (key, value) into a dictionary

There are many more datatype conversion functions and you may reference them [here](https://www.geeksforgeeks.org/type-conversion-python/).


