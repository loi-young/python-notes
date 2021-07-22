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

#### Positional parameter and keyword parameter

When defining a function, parameters can either be positional or keywords.

```py
def say(message):
    return message
```

Here `message` is a positional parameter or a keyword parameter.

A function can be called using positional arguments or keyword arguments. 

Call with positional argument.

```py
say('Nice to meet you')
```

Call with keyword argument.

```py
say(message='Good night')
```

#### Required parameter and optional parameter

The `message` parameter is a required parameter. A function can also defined with parameter with default value. For example,

```py
def say(message='hi'):
    return message
```

Call with default value.

```py
say()
```

### Return statement

If there is no `return` statement in a function, the default returned value is `None`. For example,

```py
def add(a, b):
    result = a + b
```


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

## Class

```py
class Person(object):
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def is_suitable(self, candidate):
        if candidate.age <= self.age and candidate.age >= 18:
            return True
        else:
            return False

leiguoyang= Person('leiguoyang', 32)
Mary = Person('Mary', 37)

result = leiguoyang.is_suitable(Mary)
```

## Import a module

A module is a file containing Python definitions and statements. The code below is to import a module.

```py
import module_name
```

Say you have a file called `person.py` and there is a class `Person` in it. Now if you want to access the `Person` class to create in instance from it, the code looks like this.

```py
import person

person.Person('leiguoyang', 32)
```

More details about module, please refer to [Module](https://docs.python.org/3/tutorial/modules.html) doc.

## Virtual environment (Jul 17, 2021)

Create a virtual environment before you start a python project please. With a virtual env, you can easily manage your package installation and dependencies. 

The official guide on creating and using a virtual environment is here. https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/#creating-a-virtual-environment. Please follow it.

Usually at first you may create a `requirements.txt` to specify the versions of packages you want to install and then use `pip` to install them. A `requirements.txt` file may look like this.

```
certifi==2021.5.30
charset-normalizer==2.0.3
idna==3.2
requests==2.26.0
urllib3==1.26.6
```

Install with `pip`.

```
python3 -m pip install -r requirements.txt
```

## pip

pip is the package installer for python. You can use it to install any python packages.

```
python3 -m pip install package_name
```

## Error and exception (Jul 19, 2021)

There are two kinds of errors.

- Syntax error.
- Exception. Errors detected during execution are called exceptions.

## Keywords arguments (Jul 22, 2021)

Please read this article, very clear on calling and defining function with keywords. https://www.geeksforgeeks.org/args-kwargs-python/
