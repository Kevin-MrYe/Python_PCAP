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






