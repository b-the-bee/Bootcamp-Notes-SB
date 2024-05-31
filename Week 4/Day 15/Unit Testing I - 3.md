#data-science #data-engineering 
## Testing frameworks `pytest` & `unittest`
- Provides a framework upon which to write and run our tests
- Includes helper objects and functions for versatile mocking and **spying**
- Provides a test-runner for test detection and verbose results
- Includes additional assertions for diverse testing scenarios


## pytest

pytest works by convention, we an write our tests a certain way and pytest will find them automatically for us
![[Pasted image 20240528135317.png]]

We can also use pytest as a module within code:
![[Pasted image 20240528140801.png]]

![[Pasted image 20240528144312.png]]



![[Pasted image 20240528160029.png]]
![[Pasted image 20240528160306.png]]
## Mock()

- The `unittest` framework has a `Mock` function
- `Mock()` allows us to rcreate a new object we can use to replace dependencies in our code
- We can use it to mock primitive functions or entire modules without having to be fully aware of the underlying architecture of the thing we're trying to mock
- Each method / function call is automagically replaced with another `Mock()` object whenever our unit tries to access it.

![[Pasted image 20240528160843.png]]
```python
mock_function = Mock()
mock_function.return_value = 2
```

![[Pasted image 20240528161613.png]]