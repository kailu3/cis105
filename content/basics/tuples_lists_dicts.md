# Tuples, Lists, and Dictionaries

As an interactive way to learn about these collection data types, first consider these three problems:

1. Let's say we wanted to store a long list of information in a variable that doesn't change over time? For example, the names of the days of the week don't change at all.

2. Let's say we also wanted to store a long list of information in a variable that changes over time? For instance, the names of all your cats. You might get new kittens and some cats might unfortunately die. You will need to make updates to your list each time something happens.

3. Let's say we wanted to create a phonebook with every CIS105 student's name and phone number. You would need a list of names and a list of phone numbers and some way to find the student's phone number when only given his or her name.

## The Solution - Tuples, Lists, and Dictionaries

For each of these three problems, there are built-in data types in Python to solve them.

## Tuples

Using Tuples would solve the first problem. Tuples are immutable which means that their value cannot be changed. This
is the perfect data type is store something like the `the days of the week` as they do not change ever. Tuples are quite 
easy to make:

```python
days_of_week = ('Monday', 'Tuesday', 'Wednesday', \
                'Thursday', 'Friday', 'Saturday', 'Sunday')
```

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

>`Index` might be new to those haven't programmed before! Put simply, an index refers to a position within a sequence. In Python and most programming languages, we start at position `0`.

We can demonstrate with an example: Let's say we want to access `Monday` from the `days_of_week` tuple which in the first position. To do that, we can simply access with:

```python
In [1]: days_of_week[0]
Out[1]: Monday
```

You can learn about Tuples [here](https://www.w3schools.com/python/python_tuples.asp).

## Lists

Using Lists would solve the second problem. A List is essentially a list of values and are mutable, which means that they can be modified. Lists can also contain different datatypes.

```python
some_cat_list = ['haku', 'nagi', 'poki', 20]

```
Now suppose we were looking through our `some_cat_list` and we realized we wanted to remove `20` as it might've been a happy little accident. To do that, we simply can type

```python
some_cat_list.remove(20)
```
Suppose we didn't know the item we wanted to remove but knew its **index**. If we wanted to remove an item in `20`'s location, we can type

```python
del some_cat_list[3]
```

Now maybe you adopted another cat called kiki and would like to add her to the list. To do that, we could type

```python
some_cat_list.append('kiki')

```

which would append kiki onto the end of the list. Or if we want to change kiki's name to mei instead given a change of mind, we could do so easily by changing the item at the last index.

```python
some_cat_list[-1] = 'mei'

```

> While `0` refers to the position of the first item in the list, `-1` refers to the last item in the list. Moreover, `-2`
would be the second last item in the list.

You can learn more about Lists [here](https://www.w3schools.com/python/python_lists.asp).

## Dictionaries

Likewise, we can solve the third problem with using a dictionary. Python dictionaries are conceptually the same as the 
dictionaries we use to look up words! For instance, we typically use a dictionary to look up some word we do not know.
It might be trivial but every `word` in the dictionary maps to some `definition`. Similarly in Python dictionaries, we
have `keys` and `values` where a `key` can map to some `value`. Here we make a dictionary of CIS105 student names and
their phone numbers:

```python
some_dict = {
    'Kai': 1231231231,
    'Lin': 3213213213,
    'Racheal': 964296429
}
```

Now, say we want to access `Racheal's` phone number from the dictionary. We can simply do so get *getting* her number
using her name as the `key`.

### Method 1 (Recommended)

```python
In [1]: some_dict.get('Racheal')
Out[1]: 964296429
```

### Method 2

Some people might remember that you can also access the `value` by doing:

```python
In [1]: some_dict['Racheal']
Out[1]: 964296429
```
This does work when the `key` is present but I would **NOT** recommend it. Suppose we wanted to find Bob's phone number. However,
Bob unfortunately had not been recorded in `some_dict` yet.

```python
In [1]: some_dict['Bob']
Out[1]: KeyError
```
If the `key` 'Bob' does not exist in the dictionary, this would throw a KeyError which is uninformative and not good.
> Now suppose we use the `.get` method to try and get Bob's phone number:

```python
In [1]: bobs_number = some_dict.get('Bob')
        print(bobs_number)
Out[1]: None
```

As you can see, the `.get` method defaults to `None`. You are also able to specify an informative message when the `key` does
not exist which is much better than causing a `KeyError`. For example:

```python
In [1]: bobs_number = some_dict.get('Bob', 'The key You are looking for does not exist!')
        print(bobs_number)
Out[1]: 'The key You are looking for does not exist!'

```

>This is much more informative when debugging!

You may also learn more about Dictionaries [here](https://www.w3schools.com/python/python_dictionaries.asp).
