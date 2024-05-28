#data-engineering #data-science 

![[Pasted image 20240528093844.png]]# What is a Unit?
A "unit" of code is considerred to be the smallest **testable** chunk of software which performs a very specific job/task
e.g. a pure function:

```python
def add_two_numbers(a,b):
	return a + b
```

This function has referential transparency, the same 2 inputs gives the same output hence it being a pure function.

## What is Unit Testing?
Unit Testing is then the process of executing this unit of code in isolation under certain conditions or scenarios to test its behaviour.

![[Pasted image 20240528094708.png]]

### Happy Path
Testing expected successful scenarios.

### Unhappy Path
Testing expected unsuccessful scenarios.

![[Pasted image 20240528095009.png]]
This happens more when devs test their own work.

## Test Cases
We can define certain test cases when we test:
- Common Case - Normal Input Output
- Edge Case - Uncommon  Input Output
- Corner case - Abnormal input

## Why do we care?
- A good testing strategy outlines the operational envelope of our software
- Failing tests indicate where we need to improve our software.
- Passing tests are an indicator of software quality and robustness
```
robust_software == happy_users == happy_employer
```

![[Pasted image 20240528100106.png]]
Assert is built-in to many programming languages, if it's True, nothing will happen if False, it'd "blow up".

![[Pasted image 20240528100513.png]]

## Non Test Driven Development (non TDD)
1. Read, understand, and process the feature or bug request.
2. Implement the code that fulfils the requirement.
3. Test the code works by writing a unit test.
4. Clean up code by refactoring.
5. Rinse, lather and repeat.
## Test Driven Development (TDD)
1. Read, understand, and process the feature or bug request.
2. Translate the requirement by writing a unit test.
3. Write the minimum amount of code to get the test to pass.
4. Rinse, lather and repeat.

![[Pasted image 20240528100919.png]]