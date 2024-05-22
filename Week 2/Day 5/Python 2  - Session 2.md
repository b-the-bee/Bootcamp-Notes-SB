#python #data-engineering #data-science 

## For loops

Used when you want to repeat a block of code a **fixed** number of times:

```python
for x in [0, 1, 2]:
		print(f"The current number is {x}")
```

## While loops

We can execute a block of code as long as a condition is true:

```python
i = 0
while i < 5:
	print(i)
	i += 1
```

## Range

```python
for x in range(0,5):
	print(f"Current number is {x}.")
	# Prints the range of numbers from 0-4
```

![[Pasted image 20240513141121.png]]

It will go all the way through fruits before getting to the next item in the first list.


```python
adjectives = ["red", "big", "tasty"]

fruits = ["apple", "banana", "cherry"]

  

for adj in adjectives:

  for fruit in fruits:

    print(adj, fruit)

>red apple
>red banana
>red cherry
>big apple
>big banana
>big cherry
>tasty apple
>tasty banana
>tasty cherry
```

### Break Keyword

With the `break` keyword we can stop the loop before it has looped through all of the items

```python
fruits = ["apple", "banana", "cherry"]

for fruit in fruits:
	print(fruit)
	if fruit == "banana":
		break
```


### Continue Keyword

With the `continue` keyword  we can end the current iteration of the loop early and move to the next

```python
fruits = ["apple", "banana", "cherry"]

for fruit in fruits:
  if fruit == "banana":
    continue
  print(fruit)
```


## Exercise for loops:

```python
"""Loops exercises as part of Python 2"""

  

# 1

  

for i in range(0,11):

    print(i)

# 2

i = 0

while i <= 10:

    print(i)

    i += 1

  
  

nums = [0, 2, 8, 20, 43, 82, 195, 204, 367]

  

# 3

for item in nums:

    print(item)

  

# 4

  

for i in range(0,11):

    print(i)#

else:

    print("Done!")

  

# 5

  

list1 = ["apple", "banana", "cherry", "durian", "elderberry", "fig"]

list2 = ["avocado", "banana", "coconut", "date", "elderberry", "fig"]

  

for item1 in list1:

    for item2 in list2:

        if item1 == item2:

            print(item1)

  
  

import random

while True:

    random_integer = random.randint(1, 100)

    print(random_integer)

    if random_integer % 5 == 0:

        break

    elif random_integer % 3 == 0:

        print("Skipping...")

        continue
```




