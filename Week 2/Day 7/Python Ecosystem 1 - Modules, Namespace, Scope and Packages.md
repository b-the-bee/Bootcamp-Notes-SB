#python #data-science #data-engineering 

## Modules

A piece of python code act as a container to classes, methods, functions and variables.
main.py:
```python
"""Introduction to modules and classes - OOP"""

import module_1

  

if __name__ == "__main__":

    module_1.print_name("Bob")
```

module_1.py:
```python
"""Document of modules to import"""

def print_name(name):

    print(f"Hi {name}")
```

We can also do:
```python
from module_1 import print_name
print_name("Jane")
```

Bringing the function into scope

![[Pasted image 20240515113924.png]]
![[Pasted image 20240515114054.png]]

## Namespace && Scope
![[Pasted image 20240515120625.png]]

```python
def add_numbers(a, b):
	c = a + b
	return c
print(add_numbers(1,2))
```

The local scope of the function `add_numbers` includes `a` and `b` and `c`. 

![[Pasted image 20240515121724.png]]
**Local Namespace**: Includes local names inside of a function. Created when the function is called and is destroyed when it returns.
**Global Namespace**: Includes names from various imported modules. Created when the module starts and destroyed when the module ends.
**Built-In Namespace**: Includes built-in functions and exception names.

# Packages

A collection of modules under one directory that are made available under a parent namespace
![[Pasted image 20240515122555.png]]


# Exercises:
main.py:
```python
# 1

import math

  

print(math.factorial(9))

  

# 2

  

from math import factorial

  

print(factorial(10))

  

# 3

from module_one import factorial_func

  

print(factorial_func(12))

  

"""

Variable Scope:

1. a and b are local to the function my_function,

c and d are global (d is only defined in the case of the

if statement being true)

2.

"""
```
module_one.py:
```python
from math import factorial

def factorial_func(number):

    calculation = factorial(number)

	    return calculation
```