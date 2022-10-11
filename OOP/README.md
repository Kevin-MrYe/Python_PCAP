# Object Oriented Programming

## Class

A class is an idea (more or less abstract) which can be used to create a number of incarnations.

**1. Terminology**

- Inheritance:When a class is derived from another class, their relation is named inheritance.

- Encapsulation: The ability to hide (protect) selected values against unauthorized access.

- Subclass: The class which derives from the other class is named a subclass.
- Superclass:  The second side of this relation is named superclass
```
- Superclasses are always presented above their subclasses;
- Relations between classes are shown as arrows directed from the subclass toward its superclass.
```

**2. Object**

An object is an incarnation of a class.Objects are equipped with:

- a name which identifies them and allows us to distinguish between them(UpperCamelCase).
- a set of properties (the set can be empty)
- a set of methods (can be empty, too)

**3. Class definition**
```python
class This_Is_A_Class:
     pass
```

**4. Object Creating**
```python
this_is_an_object = This_Is_A_Class()
```

**5. Constructor**
```
class Stack:
    def __init__(self):
        print("Hi!")

stack_object = Stack()
```

**Note:**

- The constructor's name is always \_\_init\_\_
- The obligatory parameter is usually named self,

**6. Self parameter**

A method is obligated to have at least one parameter, which is used by Python itself. It allows the method to access entities (properties and activities/methods) carried out by the actual object. 


So, harry.greet() translates into Person.greet(harry).

**7. Private attributes(__name)**

Using OOP in Python, we can restrict access to methods and variables. This prevents data from direct modification which is called encapsulation.

When any class component has a name starting with two underscores (__), it becomes private. As dir() shows, If we identify the variable with prefix __, then its name will change to __Classname__variable. That why there will raising an error when access it using instance.__variable
```python
class Stack:
    def __init__(self):
        self.__stack_list = []

stack_object = Stack()
print(dir(stack_object)) # output: ['_Stack__stack_list',...]
print(len(stack_object.__stack_list)) #output: AttributeError: 'Stack' object has no attribute '__stack_list'

```
**Note:**

- Private variable must have at least two leading underscores
- There is one more requirement - the name must have no more than one trailing underscore






