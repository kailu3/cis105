# Hello World

The most simple function and in my opinion one the most useful functions is the `print()` statement. This function
is extremely useful for debugging code and checking variable values. To print something in Python 3, just write the following and
run the cell by pressing `Shift+Enter`:

```python
In [1]: print('Hello World!')
Out[1]: Hello World!
```

## Assigning Values to Variables

Sometimes you may want to print a variable to see its contents. Variables are essentially reserved memory locations to store values. When you **assign** some value to a variable using `=`, the operand to the left of `=` is the name of the variable and the operand
to the right of the `=` operator is the value stored in the variable. For instance,

```python
In [1]: apple = 100
        banana = 'hello'
        kiwi = True
        print(apple, banana, kiwi)
Out[1]: 100 hello True
```

## Passing Variables to Strings

You may want to print a sentence with a variable at times. Some ways to do this are

```python
In [1]: apple = 12
        print('Apples are', apple, 'dollars a dozen')
Out[1]: apples are 12 dollars a dozen

In [2]: print('Apples are ' + str(12) + 'dollars a dozen.')
Out[2]: apples are 12 dollars a dozen
```

**Note:** When you concatenate Strings (text enclosed in '') together, all components must be of String Type. Here, I used
the `str()` function to cast the integer 12 into the String `12`. More on types and casting later.


*My usual way of passing variables into a String is to use formatting:*

```python
In [1]: print('apples are {} dollars a dozen'.format(apple))
Out[1]: apples are 12 dollars a dozen
```

In Python 3.6, there was an added string formatting approach called `f-strings`. This is another way of formatting
strings that I am still getting used to using more of. Here's a simple example

```python
In [1]: print(f'apples are {apple} dollars a dozen')
Out[1]: apples are 12 dollars a dozen
```

You can also do inline arithmetic with this formatting approach!

```python
In [1]: a = 5
        b = 10
        print(f'Five plus ten is {a + b} and not {2 * (a + b)}.')
Out[1]: Five plus ten is 15 and not 30.
```

> As you can see, there are multiple ways to pass variables to a String in Python. Similarly, there are many, many ways
to do most things in Python. These snippets in this book are just how I approach Python. You should not be limited by
them!
