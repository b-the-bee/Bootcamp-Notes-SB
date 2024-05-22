#python #data-science #data-engineering 
## More on Lists

Constant is a variable that does not change, Python does not have any built in support for an unchanging variable.  
Integers that are typed in are known as literals, not taken from anywhere else.
Heterogenous lists contain multiple data types, Homogenous lists contain only one data type.

![[Pasted image 20240509135303.png]]

```python
cool_list = ["Bob", "People", 3, 2, [1, 2, 3], "Bananas"] 

print(cool_list[0])
print(cool_list[2:])
print(cool_list[:3])
print(cool_list[4][1])
print(cool_list[3:])
```

## Inputs and Outputs

### Standard input

Standard input is done using the `input()` method


```python
user_num = int(input("Enter a number: "))
print(f"The square value of this value is {user_num * user_num}")
```

```python
"""Create a variable which will store your first name. Print out the variable.

Create a second variable which will store your last name. Concatenate the two variables and print out the result.

Extend the above to print the following using an f-string: Hi, my name is {first_name} {last_name}."""

  

first_name = input("What is your first name?")

last_name = input("What is your last name?")

  

print(f"Hi my name is {first_name} {last_name}.")
```

We then did the exercises below:

```python
# Create a variable which will store your first name. Print out the variable.

# Create a second variable which will store your last name.

# Concatenate the two variables and print out the result.

# Extend the above to print the following using an f-string:

# Hi, my name is {first_name} {last_name}.

  

first_name = "Sam"

last_name = "Brunkard"

  

print(f"Hi my name is {first_name} {last_name}.")

  
  

# Create two variables that store integer values. Calculate the product (the number you get by multiplying two or more other numbers together) of the two integers and store it in a third variable. Print the value of this variable.

# Extend the above to print out the following: The product of {x} and {y} is {product}, replacing x, y, product with the values for the above.

  
  

first_integer = 23

second_integer = 32

product_of_two = first_integer * second_integer

  

# Extend the above to print out the following: The product of {x} and {y} is {product}, replacing x, y, product with the values for the above.

  

print(f"The product of {first_integer} and {second_integer} is {product_of_two}.")

  
  

# For this section, we will be operating on the below list of names.

# Please copy this line and paste it into your code file. Remember that list indexes start at zero!

  

# people = ["John", "Sally", "Mark", "Lisa", "Joe", "Barry", "Jane"]

# Retrieve the third element (the second-indexed element) and store it in its own variable.

# Print the variable.

# Retrieve the element third from the back of the list and store it in its own variable.

# Print the variable.

# Split the list into a new list with just the names Mark, Lisa, Joe and Barry.

# Print whether or not the first and last element in the list are equal to one another.

  

people = ["John", "Sally", "Mark", "Lisa", "Joe", "Barry", "Jane"]

print(people[2])

print(people[-2])

new_people = people[2:6]

print(people[0] == people[-1])

  
  

# Hint: You can use input() as many times as you like. For instance,

# you can ask for someone's first name on one line, and their last name on another line.

  

# Accept input from the user for their name. Print their name out.

# Accept two integer inputs from the user and calculate the product. Print out the product.

# Accept two integer inputs from the user. Use the comparison operator to print out

# if the two values are equal (True), or if they're not (False).

  

user_name = input("What is your name please")

print(f"Your name is {user_name}.")

user_integer_one = int(input("What is your first integer?"))

user_integer_two = int(input("What is your second integer?"))

user_integer_product = user_integer_one * user_integer_two

print(f"The product of your two integers is {user_integer_product}")

  

check_if_same = bool(user_integer_one == user_integer_two)

print(f"It is {check_if_same} that your integers are the same.")
```


## Making Decisions
or conditional logic

In programming, often we want to make certain decisions based on a **condition**.

We looked at comparison operators before. They are also known as conditionals.
Conditionals are expressions which return **True** or **False**.
These help us make decisions in our programs.

![[Pasted image 20240509155036.png]]

```python
a=3

if a > 5:
	print("a is greater than 5")
```

![[Pasted image 20240509155514.png]]

![[Pasted image 20240509160831.png]]

## Exercises Part 2

### Input and Numbers

1. Accept an integer input from the user. If the number is even, print out an appropriate message, and vice versa if it is odd.
    1. **Hint**: Using modulus may help you here.
2. Extend the above to print a different message if the number is a multiple of four.
3. Accept an integer input from the user. If the number is a multiple of three, print the word `fizz`. If the number is a multiple of five, print `buzz`. If it is neither then do not print anything.

### Temperature Conversion

1. Write a program that will convert celsius to fahrenheit, and vice versa. Accept two inputs from the user. The first will be a letter which is either `c`, which means you should convert from fahrenheit to celsius, or `f` which is vice versa. For the second input, accept an integer value representing the temperature. Print out the converted value, along with the correct temperature type.

2. Expected input: `f` and `100`

3. Expected output: `100c is 212.0f`
- Converting from a temperature in fahrenheit (`F`) to celsius, use: `(F - 32) * (5/9)`
- Converting from a temperature in celsius (`C`) to fahrenheit, use: `(C * 1.8) + 32`