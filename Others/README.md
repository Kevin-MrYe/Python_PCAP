# Miscellaneous

## Generator, iterator and closures

**1. Iterator**

An iterator is an object of a class providing at least two methods (not counting the constructor!):
- \_\_iter\_\_() is invoked once when the iterator is created and returns the iterator's object itself;
- \_\_next\_\_() is invoked to provide the next iteration's value and raises the StopIteration exception when the iteration comes to and end.
```python
alist = [0, 1, 2, 3]
gen = iter(alist)
print(next(gen)) #output: 0
print(next(gen)) #output: 1
print(next(gen)) #output: 2
print(next(gen)) #output: 3
print(next(gen)) #output: Error:StopIteration
```


**2. Generator**

A Python generator is a piece of specialized code able to produce a series of values, and to control the iteration process.
```python
def powers_of_2(n):
    power = 1
    for i in range(n):
        yield power
        power *= 2

for v in powers_of_2(8):
    print(v)
# output: 1 2 4 8 16 32 64 128
```

**3. List comprehension**

List comprehension is a simple and very impressive way of creating lists and their contents.

```python
def powers_of_2(n):
    power = 1
    for i in range(n):
        yield power
        power *= 2

t = [x for x in powers_of_2(5)]
print(t) #output: [1,2,4,8,16]
```


**4. Lambda function**

A lambda function is a tool for creating anonymous functions. For example:
```python
def foo(x,f):
    return f(x)

print(foo(9, lambda x: x ** 0.5)) #output: 3.0
```
**5. map() function**

The map() function applies the function passed by its first argument to all its second argument's elements, and returns an iterator delivering all subsequent function results.

 The map(fun, list) function creates a copy of a list argument, and applies the fun function to all of its elements, returning a generator that provides the new list content element by element. For example:
```python
short_list = ['mython', 'python', 'fell', 'on', 'the', 'floor']
new_list = list(map(lambda s: s.title(), short_list))
print(new_list) #output:['Mython', 'Python', 'Fell', 'On', 'The', 'Floor']
```
**6. filter() function**

The filter(fun, list) function creates a copy of those list elements, which cause the fun function to return True. The function's result is a generator providing the new list content element by element. For example:
```python
short_list = [1, "Python", -1, "Monty"]
new_list = list(filter(lambda s: isinstance(s, str), short_list))
print(new_list) #output: ['Python', 'Monty']
```

**7. closure**

A closure is a technique which allows the storing of values in spite of the fact that the context in which they have been created does not exist anymore. For example:
```python
def tag(tg):
    tg2 = tg
    tg2 = tg[0] + '/' + tg[1:]

    def inner(str):
        return tg + str + tg2
    return inner

b_tag = tag('<b>')
print(b_tag('Monty Python')) #output: <b>Monty Python</b>
```

**8. conditional expression**

A conditional expression is an expression built using the if-else operator. For example:
```python
print(True if 0 >=0 else False) #output: True
```
