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
- set. `basket = {'orange', 'banana', 'pear', 'apple'}`. A set is an unordered collection with no duplicate elements. 

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

### lambda function

In fact, a lambda function is an anonymous function like in JavaScript. A lambda function is an expression which evaluates to a function reference. There is only one expression in a lambda function.

```py
filter(lambda passenger: passenger.age > 35, passengers)
```

This statement is used to select the passenger whose age is greater than 35 years old.

A lambda function is like an arrow function in JavaScript.

```js
var words = ['lei', 'guo', 'yang'];

// Selects the word whose length is greater than 3
var result = words.filter(word => word.length > 3);
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

### `*` & `**` in function definitions and calls

`*` and `**` are used to pack / unpack arguments during function calls. They are often used to pass optional positional or keyword arguments from one function to another. For example, the following is a decorator function.

```py
def f1(func):
    def wrapper(*args, **kwargs):
        print('Start')
        func(*args, **kwargs)
        print('End')
    return wrapper
```

#### `*` in function definitions.

`*` is used to pack an arbitrary number of positional arguments in a tuple. For example,

```py
def greet(*names):
    for name in names:
        print(f'Hello, {name}')
```

This function can receive zero or multiple positional arguments. 

```py
greet()
greet('leiguoyang')
greet('leiguoyang', 'Mary')
```

When calling this function, at first it packs all positional arguments into a tuple called `names`.

#### `**` in function definitions.

`**` is used to pack an arbitray number of keyword arguments into a dictionary. For example,

```py
def print_specs(**specs):
    for key, value in specs.items():
        print(f'key: {key}, value: {value}')
```

This function can receive zero or multiple keyword arguments. 

```py
print_specs()
print_specs(size='large', color='green')
```

When calling this function, at first it packs all the keyword arguments into a dictionary called `specs`.

`*` and `**` can used to unpack arguments during function calls.

#### `*` in function calls

`*` is used to unpack a list or tuple into seperate positional arguments.

```py
def some_args(arg_1, arg_2, arg_3):
    print("arg_1:", arg_1)
    print("arg_2:", arg_2)
    print("arg_3:", arg_3)

args = ("Sammy", "Casey", "Alex")
some_args(*args)
```

#### `**` in function calls

`**` is used to unpack a dictionary into multiple keyword arguments.

```py
def some_kwargs(kwarg_1, kwarg_2, kwarg_3):
    print("kwarg_1:", kwarg_1)
    print("kwarg_2:", kwarg_2)
    print("kwarg_3:", kwarg_3)

kwargs = {"kwarg_1": "Val", "kwarg_2": "Harper", "kwarg_3": "Remy"}
some_kwargs(**kwargs)
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
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def is_suitable(self, candidate):
        return candidate.age <= self.age and candidate.age >= 18
```

Create an instance.

```
leiguoyang= Person('leiguoyang', 32)
Mary = Person('Mary', 37)
```

Call an instance method.

```
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

The official guide on creating and using a virtual environment is here. https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/#creating-a-virtual-environment.

First, in your project direcotry use this command to create a virtual environment.

```
python3 -m venv env
```

where `env` is the location where your virtual environment lives.

Second, use this command to activate your virtual environment.

```
source env/bin/activate
```

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

Use this command to create a `requirements.txt` listing all package dependencies in your current virtual environment.

```
pip freeze > requirements.txt
```

## pip

pip is the package installer for python. You can use it to install any python packages.

```
python3 -m pip install package_name
```

## Error and exception (Jul 19, 2021)

There are two kinds of errors. Syntax and Exceiption.

### Syntax error

For example,

```py
print 'nice to meet you'
```

will raise a SyntaxError.

```
>>> print 'nice to meet you'
  File "<stdin>", line 1
    print 'nice to meet you'
          ^
SyntaxError: Missing parentheses in call to 'print'. Did you mean print('nice to meet you')?
```

### Exception

Errors detected during execution are called exceptions. For example, `ZeroDivisionError` and `TypeError`.

My understanding of exception handling. Some pesudo code here

```py
try:
    to do sth
except some exception:
    to handle the exception
```

```py
try:
    1 / 0
except ZeroDivisionError:
    print('Can\'t divided by 0, please check your statement or expression. Thanks.')
```

output.

```
Can't divided by 0, please check your statement or expression. Thanks.
```

## Falsy & truthy values in python

One of the advantages of using truthy and falsy values is that they can help you make your code more concise and readable. Consider this form snippet I define in Django.

```html
<div class="mb-3">
    <label for="{{ form.title.id_for_label }}" class="form-label">标题</label>
    {% if form.title.errors %}
        <ul class="alert alert-info">
        {% for error in form.title.errors %}
            <li>{{ error }}</li>
        {% endfor %}
        </ul>
    {% endif %}
    {{ form.title }}
</div>
```

It means if there is any errors, output them. In other words, if the `errors` is not an empty list, do something with it.

Falsy values includes:

- Sequences and collections
  - Empty lists `[]`
  - Empty tuples `()`
  - Empty dictionaries `{}`
  - Empty sets `()`
  - Empty strings `''`
  - Empty ranges `range(0)`
- Numbers: Zero of any numeric type
  - Integer: `0`
  - Float: `0.0`
  - Complex: `0j`
- Constants
  - `None`
  - `False`

Truthy values includes:

- Non-empty sequences or collections (lists, tuples, strings, dictionaries, sets).
- Numeric values that are not zero.
- Constant: `True`.

## Decorator

A decorator is a function. It is used to decorate other function in order to extend its functionality. A decorator may like this.

```py
# A decorator
def f1(func):
    def wrapper():
        print('Start')
        func()
        print('End')
    return wrapper

# Decorates a function
@f1
def f():
    print('Hello')

# Call a decorated function
f()
```

`@f1`相当于对`f`这个function进行decorate后又重新assign给一个同样名为`f`的variable。`@f1`这种形式只是一种syntax，上面的代码相当于：

```py
def f1(func):
    def wrapper():
        print('Start')
        func()
        print('End')
    return wrapper

def f():
    print('Hello')

f = f1(f)

f()
```

Decorates a function with parameters.

```py
def f1(func):
    def wrapper(*args, **kwargs):
        print('Start')
        func(*args, **kwargs)
        print('End')
    return wrapper

@f1
def f(a):
    print(a)

f('Hello')
```

这个视频讲解的非常清楚。[Python Decorators in 15 Minutes](https://www.youtube.com/watch?v=r7Dtus7N4pI)
