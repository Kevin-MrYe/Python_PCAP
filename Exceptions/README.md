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

# TypeError
# Apply a data whose type cannot be accepted in the current context.
short_list = [1]
one_value = short_list[0.5] # TypeError

# AttributeError
# Activate a method which doesn't exist in an item you're dealing with.
short_list = [1]
short_list.append(2)
short_list.depend(3) # AttributeError
```
## Hirerachy of Exceptions


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











