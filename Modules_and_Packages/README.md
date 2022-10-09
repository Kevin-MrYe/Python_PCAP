# Modules and Packages

## Import

**1. Import module**

```python
import my_module
import mod1, mod2, mod3

# If a module is imported in the above manner, access entry need to prefix with module name.
result = my_module.my_function(my_module.my_data)
```
**Note :** None of the imported entity names conflicts with the identical names existing in code's namespace.


**2. From module import methods**
```python
from module import my_function, my_data

# In this case, the imported entities must not be prefixed when used
result = my_function(my_data)
```

**Note :** The way is not recommended because of the danger of causing conflicts with names derived from importing the code's namespace.



**3. From module import \***
```python
from my_module import *

# import all entities offered by a module, the imported entities must not be prefixed when used
result = my_function(my_data)
```

**Note :** This import's variant is not recommended due to the danger of causing conflicts with names derived from importing the code's namespace.(The threat of a naming conflict is even more dangerous here).

**4. Import alias**
```python
from module1 import my_function as fun, my_data as dat
import module2 as alias

result = fun(dat)
alias.method()
```

## Modules

Module is designed to couple together some related entities (functions, variables, constants, etc.),

**1. dir()**

- dir() returns an alphabetically sorted list containing all entities' names available in the module.
- if the module's name has been aliased, you must use the alias, not the original name. 

**2. Math**

The math module couples more than 50 symbols (functions and constants) that perform mathematical operations (like sine(), pow(), factorial()) or providing important values (like π and the Euler symbol e).

**3. Random**

The random module groups more than 60 entities designed to help you use pseudo-random numbers. Don't forget the prefix "pseudo", as there is no such thing as a real random number when it comes to generating them using the computer's algorithms.

**4. Platform**

The platform module contains about 70 functions which let you dive into the underlaying layers of the OS and hardware. Using them allows you to get to know more about the environment in which your code is executed.( i.e., hardware, operating system, and interpreter version information.)

- platform() is a function that can show you all the underlying layers in one glance.
- machine()  tells the generic name of the processor which runs your OS together with Python and your code.
- processor() function returns a string filled with the real processor name (if possible). 
- system() returns the generic OS name as a string.
- version() returns the OS version is provided as a string.
- python_implementation() returns a string denoting the Python implementation.
- python_version_tuple() returns a three-element tuple filled with:
    - the major part of Python's version;
    - the minor part;
    - the patch level number.

**5. private entity**

If you want to instruct your module's user that a particular entity should be treated as private (i.e. not to be explicitly used outside the module) you can mark its name with either the _ or __ prefix.
```python
# module.py
__counter = 0


def suml(the_list):
    global __counter
    __counter += 1
    the_sum = 0
    for element in the_list:
        the_sum += element
    return the_sum


def prodl(the_list):
    global __counter    
    __counter += 1
    prod = 1
    for element in the_list:
        prod *= element
    return prod


if __name__ == "__main__":
    print("I prefer to be a module, but I can do some tests for you.")
    my_list = [i+1 for i in range(5)]
    print(suml(my_list) == 15)
    print(prodl(my_list) == 120)
    
#  main.py
import module
print(module.counter) # AttributeError: module 'module' has no attribute 'counter'
```

**Note:**

- Don't forget that this is only a recommendation, not an order.



## Packages

Package is a container which enables the coupling of several related modules under one common name

**1. __init__.py**

A Python file named __init__.py is implicitly run when a package containing it is subject to import, and is used to initialize a package and/or its sub-packages (if any). The file may be empty, but must not be absent.

**2. import a package**

If you want convince Python that it should take into account a non-standard package's directory, its name needs to be inserted/appended into/to the import directory list stored in the path variable contained in the sys module.

```python
from sys import path

path.append('..\\modules')

import module

zeroes = [0 for i in range(5)]
ones = [1 for i in range(5)]
print(module.suml(zeroes))
print(module.prodl(ones))
```





