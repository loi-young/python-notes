# Python notes

## Assignment

```py
name = 'leiguoyang'
age = 32
is_married = False
```

## Data structures

There are four main data structures in python.

- list. `[1, 2, 3, 4]`
- tuple. `(1, 2, 3)`
- dictionary. `{1: 1, 2: 2, 3: 3}`. A dictionary is a key-value pairs.
- set

## Function

### Defining a function

```py
# returns the odd numbers
def odd(numbers):
    return list(filter(lambda x: x % 2 != 0, numbers))

# calling a function
odd(range(10))

# output
>>> [1, 3, 5, 7, 9]
```

### Parameters

Positional parameters and keyword parameters, required parameters or optional parameters.

### List comprehension

A list comprehension follows this format, where the if conditional is optional.

`[expression for element in collection if conditional]`

For example.

Case 1, w/o if conditional.

```py
# returns the squares of numbers
squares = [i ** 2 for i in range(1, 11)]
```

Case 2, w/ if conditional.

```py
# returns the even numbers
even_nums = [num for num in range(1, 11) if num % 2 == 0]
```

## Removing python

Follow this reference to remove a specific version of Python. [How to uninstall Python](https://stackoverflow.com/questions/3819449/how-to-uninstall-python-2-7-on-a-mac-os-x-10-6-4)

