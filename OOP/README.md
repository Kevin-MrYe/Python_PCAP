# Object Oriented Programming

## Class Overview

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
The part of the Python class responsible for creating new objects is called the constructor.It's implemented as a method of the name \_\_init\_\_.

```
class Stack:
    def __init__(self):
        print("Hi!")

stack_object = Stack()
```

**Note:**

- The constructor's name is always \_\_init\_\_
- The obligatory parameter is usually named self
- Can not return a value, as it is designed to return a newly created object and nothing else

**6. Self parameter**

A method is obligated to have at least one parameter, which is used by Python itself. It allows the method to access entities (properties and activities/methods) carried out by the actual object. 

stack_object_1.pop() = Stack.pop(stack_object_1)

```python
class Stack:
    def __init__(self):
        self.__stack_list = []

    def push(self, val):
        self.__stack_list.append(val)

    def pop(self):
        val = self.__stack_list[-1]
        del self.__stack_list[-1]
        return val
        
stack_object_1 = Stack()
stack_object_2 = Stack()

stack_object_1.push(3)
stack_object_2.push(stack_object_1.pop())

print(stack_object_2.pop()) #output: 3
```

**Note:**

- invoking any method (including constructors) from outside the class never requires you to put the self argument at the argument's list 

- invoking a method from within the class demands explicit usage of the self argument, and it has to be put first on the list.

**7. Private attributes(__name)**

Using OOP in Python, we can restrict access to methods and variables. This prevents data from direct modification which is called encapsulation.

When any class component has a name starting with two underscores (__), it becomes private.But don't forget that such a property is still accessible from outside the class using a mangled name constructed as \_ClassName\_\_PrivatePropertyName. That why there will raising an error when access it using instance.__variable



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

The mangling won't work if you add a private instance variable outside the class code.
```python
class ExampleClass:
    def __init__(self, val = 1):
        self.__first = val

    def set_second(self, val = 2):
        self.__second = val

example_object_3 = ExampleClass(4)
example_object_3.__third = 5

print(example_object_3.__dict__) #output: {'_ExampleClass__first': 4, '__third': 5}
```
## Discovery class structure

**1. \_\_dict\_\_**

Python objects, when created, are gifted with a small set of predefined properties and methods. One of them is a variable named \_\_dict\_\_ (it's a dictionary).The variable contains the names and values of all the properties (variables or methods) the object is currently carrying. 

```python
class Classy:
    varia = 1
    def __init__(self):
        self.var = 2

    def method(self):
        pass

    def __hidden(self):
        pass
obj = Classy()

print(obj.__dict__) #output: {'var': 2}
print(Classy.__dict__) #output: {'__module__': '__main__', 'varia': 1, '__init__': <function Classy.__init__ at 0x7fb5f1340320>, 'method': <function Classy.method at 0x7fb5f13403b0>, '_Classy__hidden': <function Classy.__hidden at 0x7fb5f1340440>, '__dict__': <attribute '__dict__' of 'Classy' objects>, '__weakref__': <attribute '__weakref__' of 'Classy' objects>, '__doc__': None}
```

**2. hasattr()**

A function named hasattr() can be used to determine if any object/class contains a specified property.

```python
class ExampleClass:
    a = 1
    def __init__(self):
        self.b = 2
example_object = ExampleClass()

print(hasattr(example_object, 'b')) #output: True
print(hasattr(example_object, 'a')) #output: True
print(hasattr(ExampleClass, 'b')) #output: False
print(hasattr(ExampleClass, 'a')) #output: True
```
**3. \_\_name\_\_**

The property contains the name of the class.
```python
class Classy:
    pass

print(Classy.__name__) #output:Classy
obj = Classy()
print(type(obj).__name__) #output:Classy
```

**Note:**
- The \_\_name\_\_ attribute is absent from the object - it exists only inside classes.
- If you want to find the class of a particular object, you can use a function named type()

**4. \_\_module\_\_**

 It stores the name of the module which contains the definition of the class.
 ```python
 class Classy:
    pass

print(Classy.__module__) #output: __main__
obj = Classy()
print(obj.__module__) #output: __main__
 ```
- Any module named \_\_main\_\_ is actually not a module, but the file currently being run.

**5. \_\_bases\_\_**

\_\_bases\_\_ is a tuple. The tuple contains classes (not class names) which are direct superclasses for the class.
```python
class SuperOne:
    pass

class SuperTwo:
    pass

class Sub(SuperOne, SuperTwo):
    pass

def printBases(cls):
    print('( ', end='')

    for x in cls.__bases__:
        print(x.__name__, end=' ')
    print(')')

printBases(SuperOne) #output: ( object )
printBases(SuperTwo) #output: ( object )
printBases(Sub) #output: ( SuperOne SuperTwo )
```
**Note:**

- Only classes have this attribute - objects don't.
- A class without explicit superclasses points to object (a predefined Python class) as its direct ancestor.

## Class Variable

A class variable is a property which exists in just one copy and is stored outside any object.
```python
class ExampleClass:
    counter = 0
    def __init__(self, val = 1):
        self.__first = val
        ExampleClass.counter += 1


example_object_1 = ExampleClass()
example_object_2 = ExampleClass(2)
example_object_3 = ExampleClass(4)

print(example_object_1.__dict__, example_object_1.counter) #output: {'_ExampleClass__first': 1} 3
print(example_object_2.__dict__, example_object_2.counter) #output: {'_ExampleClass__first': 2} 3
print(example_object_3.__dict__, example_object_3.counter) #output: {'_ExampleClass__first': 4} 3
```

**Note:**

- class variables aren't shown in an object's \_\_dict\_\_
- a class variable always presents the same value in all class instances (objects)

## Instance Variable

The word instance suggests that they are closely connected to the objects (which are class instances), not to the classes themselves.

```python
class ExampleClass:
    def __init__(self, val = 1):
        self.first = val

    def set_second(self, val):
        self.second = val


example_object_1 = ExampleClass()
example_object_2 = ExampleClass(2)

example_object_2.set_second(3)

example_object_3 = ExampleClass(4)
example_object_3.third = 5

print(example_object_1.__dict__) #output: {'first': 1}
print(example_object_2.__dict__) #output: {'second': 3, 'first': 2}
print(example_object_3.__dict__) #output: {'third': 5, 'first': 4}
```

**Note:**

- Modifying an instance variable of any object has no impact on all the remaining objects.
- Adding or deleting instance variable can be done in any moment of the object's life. 


## Methods

A method is a function embedded inside a class and a method is obliged to have at least one parameter:

- A method may be invoked without an argument, but not declared without parameters.
- The parameter 'self' identifies the object for which the method is invoked.

If you want the method to accept parameters other than self, you should:

- place them after self in the method's definition;
- deliver them during invocation without specifying self (as previously)
```python
class Classy:
    def method(self, par):
        print("method:", par)

obj = Classy()
obj.method(1) #output: method: 1
obj.method(2) #output: method: 2
obj.method(3) #output: method: 3
```

## Class inheritance
```python
class Stack:
    def __init__(self):
        self.__stack_list = []

    def push(self, val):
        self.__stack_list.append(val)

    def pop(self):
        val = self.__stack_list[-1]
        del self.__stack_list[-1]
        return val

class AddingStack(Stack):
    def __init__(self):
        Stack.__init__(self)
        self.__sum = 0

```
**Note:**

- Python forces you to explicitly invoke a superclass's constructor. 
- Omitting this point will have harmful effects - the object will be deprived of the __stack_list list.
- it's generally a recommended practice to invoke the superclass's constructor before any other initializations you want to perform inside the subclass.

## Inheritance

Inheritance is a common practice (in object programming) of passing attributes and methods from the superclass (defined and existing) to a newly created class, called the subclass.

**1. issubclass()**

issubclass() can check if a particular class is a subclass of any other class.

```python
class Vehicle:
    pass

class LandVehicle(Vehicle):
    pass

class TrackedVehicle(LandVehicle):
    pass

for cls1 in [Vehicle, LandVehicle, TrackedVehicle]:
    for cls2 in [Vehicle, LandVehicle, TrackedVehicle]:
        print(issubclass(cls1, cls2), end="\t")
    print()
#output: True False False
#        True True  False
#        True True  True
```

**Note:**

- Each class is considered to be a subclass of itself.

**2. isinstance()**

isinstance() can check whether it is an object of a certain class or not.
```python
class Vehicle:
    pass

class LandVehicle(Vehicle):
    pass

class TrackedVehicle(LandVehicle):
    pass

my_vehicle = Vehicle()
my_land_vehicle = LandVehicle()
my_tracked_vehicle = TrackedVehicle()

for obj in [my_vehicle, my_land_vehicle, my_tracked_vehicle]:
    for cls in [Vehicle, LandVehicle, TrackedVehicle]:
        print(isinstance(obj, cls), end="\t")
    print()
#output: True False Fasle
#        True True  True
#        True True  True
```

**Note:**

- Being an instance of a class means that the object (the cake) has been prepared using a recipe contained in either the class or one of its superclasses.

**3. is operator**

The is operator checks whether two variables (object_one and object_two here) refer to the same object.
```python
class SampleClass:
    def __init__(self, val):
        self.val = val

object_1 = SampleClass(0)
object_2 = SampleClass(2)
object_3 = object_1
object_3.val += 1

print(object_1 is object_2) #output: False
print(object_2 is object_3) #output: False
print(object_3 is object_1) #output: True
print(object_1.val, object_2.val, object_3.val) #output: 1 2 1

string_1 = "Mary had a little "
string_2 = "Mary had a little lamb"
string_1 += "lamb"

print(string_1 == string_2, string_1 is string_2) #output: True False
```

**Note:**

- Variables don't store the objects themselves, but only the handles pointing to the internal Python memory.

**4. Inheriting methods**
```python
# First way: superclass_name.__init__(self,args)
class SuperClass:
    def __init__(self, name):
        self.name = name

    def __str__(self):
        return "My name is " + self.name + "."


class Sub(SuperClass):
    def __init__(self, name):
        SuperClass.__init__(self, name)
    
obj = Sub("Andy")
print(obj) #output: My name is Andy.
```

**Note:**

- The Sub class defines its own constructor, which invokes the one from the superclass. It explicitly named the superclass, and pointed to the method to invoke __init__(), providing all needed arguments.

```python
class Super:
    def __init__(self, name):
        self.name = name

    def __str__(self):
        return "My name is " + self.name + "."


class Sub(Super):
    def __init__(self, name):
        super().__init__(name)

obj = Sub("Andy")
print(obj) #output: My name is Andy.
```

**Note:**

- The super() function creates a context in which you don't have to (moreover, you mustn't) pass the self argument to the method being invoked.
- superclass_name.\_\_init\_\_(self,args) == super().\_\_init\_\_(args)
## Magic methods


