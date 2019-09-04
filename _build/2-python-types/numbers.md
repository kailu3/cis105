---
interact_link: content/2-python-types/numbers.ipynb
kernel_name: python3
has_widgets: false
title: 'Numbers'
prev_page:
  url: /2-python-types/intro-types.html
  title: '2. Python Data Types'
next_page:
  url: /2-python-types/strings.html
  title: 'Strings'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---


<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
import sys

```
</div>

</div>



# Numbers



As we've seen in the `Basic Math` section, we can use numbers to perform calculations. In this section, I will explain in detail the differences between the different types of numbers: `int`, `float`, and `complex` as well as some common methods we can use with them.



## Integers



Integers refer to `int` values in Python. They represent whole numbers (negative, zero, positive) and do not have a decimal component



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
1

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



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
0

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
0
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
-1

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
-1
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# Python3 ints can be some pretty large values

123812093819012381290380129830192830912312312313123712983719823719237

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
123812093819012381290380129830192830912312312313123712983719823719237
```


</div>
</div>
</div>



## Floats



Real numbers are called `float` values in Python. They can represent whole and fractional numbers but have limitations that I will discuss as you scroll down.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
3.0

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
3.0
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
3.76

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
3.76
```


</div>
</div>
</div>



When an operation (e.g. addition) is performed on a `float` and a `int` value, the result will always be a `float` value. For operations with only `int` values, you typically get an `int` value as a result but division of two `int` values will always return a `float`.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
3.0 + 3

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
6.0
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
3 / 3

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
1.0
```


</div>
</div>
</div>



### Limitations for Floats



>These limitation most likely won't affect any work done in CIS105 but I think they are good to know :)

1. There is an upperbound and lowerbound to a `float`'s number. You will rarely encounter this problem however
2. A `float` has limited precision (up to around 15 or 16 significant digits)
3. Combining `float` values with arithmetic operations can lead to small rounding errors



#### Limitation 1



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# the maximum a float's value is ..
sys.float_info.max

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
1.7976931348623157e+308
```


</div>
</div>
</div>



> `e+308` means e^308 in mathematical terms.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
1.797e+308

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
1.797e+308
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
1.797e+309

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
inf
```


</div>
</div>
</div>



If we go past this value, we will run into the value `inf` which is positive infinity. 

On the other hand, we could also have a very small number that is extremely close to 0. At a certain point, the number is going to be represented as `0.0`.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
5e-324

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
5e-324
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
5e-325

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
0.0
```


</div>
</div>
</div>



#### Limitation 2



If we do operations on floats with a large number of decimal places, the resulting `float` can be a tiny bit inprecise.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
0.111111111111111111111111111119 - 0.111111111111111111111111111118

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
0.0
```


</div>
</div>
</div>



#### Limitation 3



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# square root of 5
5 ** 0.5

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
2.23606797749979
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
(5**0.5) * (5**0.5)

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
5.000000000000001
```


</div>
</div>
</div>



>The product of two square roots of 5 should be 5 as well but it's not!



## Complex Numbers



Complex numbers are not used as much (in my opinion) so I won't go over them in much detail. In Python, you can make a number imaginary by putting `j` or `J` after it.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
1j

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
1j
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
1J

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
1j
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
2j * 3j

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
(-6+0j)
```


</div>
</div>
</div>



If you ever need to deal with complex numbers, the standard module `cmath` has many functions that handle them nicely.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# e.g.
import cmath

x = complex(1,2)
y = complex(3,4)

x, y

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
((1+2j), (3+4j))
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
x.real, x.imag

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
(1.0, 2.0)
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
y.real, y.imag

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
(3.0, 4.0)
```


</div>
</div>
</div>



## Numerical Methods



There are some basic numerical methods/functions that are built into Python without any imports. Here are some examples:



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# minimum value
min(3, 3.14, 3.1415, 3.141596)

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
# maximum value
max(3, 3.14, 3.1415, 3.141596)

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
3.141596
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# absolute value
abs(-2)

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
# round
round(3.5), round(3.49)

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
(4, 3)
```


</div>
</div>
</div>



There are also many methods/functions the `math` library that help you do mathematical calculations. Here are some more examples:



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
import math

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# ceil (smallest integer greater than x)
math.ceil(1.2)

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
# floor (biggest integer smaller than x)
math.ceil(1.2)

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
# natural log & e
math.log(math.e)

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
1.0
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# log base 10
math.log10(10)

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
1.0
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# exponential e^x
math.exp(2)

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
7.38905609893065
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# square root
math.sqrt(4)

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



For more useful functions in the `math` library, you can check them out [here](https://www.programiz.com/python-programming/modules/math)!

