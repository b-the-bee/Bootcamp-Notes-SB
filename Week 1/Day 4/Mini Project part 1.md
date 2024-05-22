#data-science #data-engineering #python 

Pseudo code is used to outline what the program will be doing, it gives structure 

### Pseudo-code:
`Create list and save as variable`
`GET user input for product menu option 

    IF user input is 0: 

        RETURN to main menu 

    ELSE IF user input is 1: 

        PRINT products list 

    ELSE IF user input is 2: 

        # CREATE new product 

        GET user input for product name 

        APPEND product name to products list 

    ELSE IF user input is 3: 

        # STRETCH GOAL - UPDATE existing product 

        PRINT product names with its index value 

        GET user input for product index value 

        GET user input for new product name 

        UPDATE product name at index in products list 

    ELSE IF user input is 4: 

        # STRETCH GOAL - DELETE product 

        PRINT products list 

        GET user input for product index value 

        DELETE product at index in products list

I completed the first part of the project as shown here, I believe the code is self explanatory enough:

```python
"""The starting code for the mini project"""

  

import sys

  

product_list = ["White Americano","Black Americano", "Cappuccino", "Mocha", "Latte",

                "Cortado", "Macchiato", "Iced Americano", "Iced Cappuccino", "Iced Mocha",

                "Iced Latte", "Iced Cortado", "Iced Macchiato"]

  
  

def get_user_choice():

    """Get's the user's choice and returns the value to be cached later."""

    user_choice = int(input("\n\n\n\n\n\nPlease pick an operation:\nReturn to main menu (0).\n"

                        "Print product list (1)."

                        "\nAdd Product to list (2).\nUpdate existing product (3)."

                        "\nDelete Product(4).\n"))

  

    while user_choice not in [0, 1, 2, 3, 4]:

        print("Please pick a valid number.")

        user_choice = int(input("Please pick an operation:\nReturn to main menu (0)."

                                "\n Print product list (1)."

                                "\nAdd Product to list (2).\nUpdate existing product (3)."

                                "\nDelete Product(4).\n"))

    return user_choice

  
  

def show_products():

    """Generates an indexed list of products."""

    print("Here is a list of products")

    for (i, item) in enumerate(product_list, start = 0):

        print(i, item)

  

def iterable_decision_tree():

    """The decision tree the program goes through to provide functionality"""

    user_choice_cache = get_user_choice()

    if user_choice_cache == 0:

        print("Returning to the main menu.\n\n\n\n\n\n")

    elif user_choice_cache == 1:

        product_list_length = len(product_list)

        show_products()

    elif user_choice_cache == 2:

        user_addition = str(input("What item do you wish to add to the list?\n"))

        product_list.append(user_addition)

        print("The new list is:")

        show_products()

    elif user_choice_cache == 3:

        product_list_length = len(product_list) - 1

        show_products()

        user_change = int(input(f"Which item do you wish to change? 0-{product_list_length}: "))

        while user_change < 0 or user_change > product_list_length:

            print("That is not a valid input")

            user_change = int(input(f"Which item do you wish to change? 0-{product_list_length}: "))

        item_change = str(input("What do you wish to change it to?\n"))

        product_list[user_change] = item_change

    elif user_choice_cache == 4:

        product_list_length = len(product_list) - 1

        show_products()

        user_change = int(input(f"Which item do you wish to delete? 0-{product_list_length}: "))

        while user_change < 0 or user_change > product_list_length:

            print("That is not a valid input")

            user_change = int(input(f"Which item do you wish to change? 0-{product_list_length}: "))

        product_list.pop(user_change)

  

if __name__ == "__main__":

    X = "y"

    while X == "y":

        iterable_decision_tree()

        X = str(input("Continue? (y/n)\n").lower())

        while X not in ["y", "n"]:

            print("Please enter a valid input, y/n")

            X = str(input("Continue? (y/n)\n").lower())

        if X == "n":

            print("Goodbye =)")

            sys.exit()
```