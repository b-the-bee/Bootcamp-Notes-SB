#python #data-science #data-engineering 

## Dictionaries

Properties of a dictionary are:
- Mutable
- Doesn't have an order

So to index the dictionary you can index the key like:

```python
data = {
		"key": "value",
		"fruits": ["Apples", "Bananas", "Oranges"],
}

data["fruits"]
```

Values can be pretty much anything, even another dictionary or a list.

```python
print(data[0])
```

Would get KeyError as it does not exist.

![[Pasted image 20240513152800.png]]
With data there is **CRUD**:


**C** - Create 
**R** - Remove
**U** - Update
**D** - Delete


```python
car1_owners = [

    {"location": "NE", "age" : 25},

    {"location": "NW", "age": 30}

    ]

  

car1 = {

    "mileage": 50000,

    "owners": car1_owners,

    "MOT": True

}

  

car2 = {

    "mileage": 0,

    "owners": [],

    "MOT": False

}
```
