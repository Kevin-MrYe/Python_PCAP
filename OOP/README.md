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

## Stack
