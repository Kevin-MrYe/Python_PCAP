# Exceptions


## Types of errors

- Syntax errors(parsing errors)

Syntax errors occur when the parser comes across a statement that is incorrect.
```python
print("Hello, World!) #output: SyntaxError: EOL while scanning string literal
```
- Exceptions

Exceptions occur even when a statement/expression is syntactically correct; these are the errors that are detected during execution.
```python
# ZeroDivisionError
# perform any operation which provokes division in which the divider is zero
print(1/0) #ZeroDivisionError

# ValueError
# when a function receives an argument of a proper type, but its value is unacceptable.
print(int('hello'))

# IndexError
#when you try to access a non-existent sequence's element
list1 = [1]
print(list1[1])

# KeyError
# Raised when access a collection's non-existent element (e.g., a dictionary's element)
dict1 = {'name':'mike'}
print(dict1['address'])

# TypeError
# Apply a data whose type cannot be accepted in the current context.
short_list = [1]
one_value = short_list[0.5] # TypeError

# AttributeError
# Activate a method which doesn't exist in an item you're dealing with.
short_list = [1]
short_list.append(2)
short_list.depend(3) # AttributeError

# KeyboardInterrupt
# A concrete exception raised when the user uses Ctrl-C terminate a program's execution
from time import sleep

seconds = 0

while True:
    try:
        print(seconds)
        seconds += 1
        sleep(1)
    except KeyboardInterrupt:
        print("Don't do that!")

# ImportErroe
# A concrete exception raised when an import operation fails
try:
    import math
    import time
    import abracadabra

except:
    print('One of your imports has failed.')

# MemoryError 
# a concrete exception raised when an operation cannot be completed due to a lack of free memory.
string = 'x'
try:
    while True:
        string = string + string
        print(len(string))
except MemoryError:
    print('This is not funny!')

# OverflowError
# A concrete exception raised when an operation produces a number too big to be successfully stored
from math import exp
ex = 1

try:
    while True:
        print(exp(ex))
        ex *= 2
except OverflowError:
    print('The number is too big.')

```
## Hierarchy of Exceptions
<p align="left" width="100%">
  <img src ="https://github.com/Kevin-MrYe/Python_PCAP/blob/master/Exceptions/imgs/hierachyofexception.png" width = '700px'>
</p>

The closer to the root an exception is located, the more general (abstract) it is.
```python
try:
    y = 1 / 0
except ArithmeticError:
    print("Arithmetic problem!") #output: Arithmetic problem!
except ZeroDivisionError:
    print("Zero Division!")

print("THE END.")
```

- Don't put more general exceptions before more concrete ones,this will make the latter one unreachable and useless



## try-except
```
while True:
    try:
        number = int(input("Enter an int number: "))
        print(5/number)
        break
    except (ValueError, TypeError):
        print("Wrong value or Wrong type.")
    except ZeroDivisionError:
        print("Sorry. I cannot divide by zero.")
    except: #optinal
        print("I don't know what to do...")
```

**1. Try keyword**

The try keyword begins a block of the code which may or may not be performing correctly

**2. Except keyword**

The except keyword starts a piece of code which will be executed if anything inside the try block goes wrong

**Note:**

- If one of the except branches is executed, the other branches will be skipped.
- Specify a particular built-in exception only once.
- Default (or generic) exception is optional, that is the one with no name specified, should be placed at the bottom of the branch.
- It is possible to handle multiple built-in exceptions within a single except clause.

## Raise an exception

The raise instruction raises the specified exception.

```python
def bad_fun(n):
    raise ZeroDivisionError

try:
    bad_fun(0)
except ArithmeticError:
    print("What happened? An error?") #output:What happened? An error?

print("THE END.")
```
The same statement, but lacking ExceptionName, can be used inside the try branch only, and raises the same exception which is currently being handled. Example as follows:
```python
def bad_fun(n):
    try:
        return n / 0
    except:
        print("I did it again!")
        raise

try:
    bad_fun(0)
except ArithmeticError:
    print("I see!") 

print("THE END.") 

#output:
# I did it again!
# I see!
# THE END.
```

## Assert Keyword
The Python statement assert expression evaluates the expression and raises the AssertError exception when the expression is equal to False, zero, an empty string, or None.
```python
import math

x = float(input("Enter a number: ")) # Enter -1
assert x >= 0.0 #output: AssertionError

x = math.sqrt(x)

print(x)

```

## Try-except-else

Else block is executed when (and only when) no exception has been raised inside the try block.
```python
def reciprocal(n):
    try:
        n = 1 / n
    except ZeroDivisionError:
        print("Division failed")
        return None
    else:
        print("Everything went fine")
        return n

print(reciprocal(2)) 
#output:  Everything went fine
#         0.5
print(reciprocal(0))
# output: Division failed
#         NOne
```

## Try-except-else-finally

The finally block is always executed (it finalizes the try-except block execution, hence its name), no matter what happened earlier, even when raising an exception, no matter whether this has been handled or not.
```python
def reciprocal(n):
    try:
        n = 1 / n
    except ZeroDivisionError:
        print("Division failed")
        n = None
    else:
        print("Everything went fine")
    finally:
        print("It's time to say goodbye")
        return n

print(reciprocal(2))
#output: Everything went fine
#        It's time to say goodbye
#        0.5
print(reciprocal(0))
#output: Division failed
#        It's time to say goodbye
#        None

```

## Create Exception Class










