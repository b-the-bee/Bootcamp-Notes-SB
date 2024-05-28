#data-engineering #data-science 

# Overview
- Dependency Injection
- Mocking
- Intro to Mock()

## LOs
- To be able to explain what Dependency Injection is
- Use mocking to test dependency injection

![[Pasted image 20240528144559.png]]![[Pasted image 20240528144736.png]]

![[Pasted image 20240528144804.png]]
![[Pasted image 20240528144905.png]]
# Dependency Injection
## What is a dependency?
Our units may depend upon other functions, libraries or external services in order to do their job. We call these **dependencies**.

How do we do it?
Mocking

![[Pasted image 20240528145106.png]]
Dependency injection is injecting a fake (not the real) function to get quicker results, replacing it with something that won't be accurate for the purpose of the program but will be accurate for the purpose of the test.

![[Pasted image 20240528151615.png]]

## Spying on our Mock
Spying allows us to record the behaviour of our mocks and its parameters which we can use later to make better assertions.

### `Mock()`
- `call_count` - returns an integer for how many times the function has been called
- `called` - returns a bool if the mock function has been called or not

## Making Assertions

Mock()
- `assert_called()` - fails if the mock is not called
- `assert_not_called()` - fails if mock is called
- `assert_called_with(*args)` - fails if mock is not called with the specified parms
- `rest_mock()` - resets mock back to initial state. useful if testing one mock under multiple scenarios

### Examples:

![[Pasted image 20240528162438.png]]