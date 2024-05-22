#python #data-science #data-engineering 

```python
"""The starting code for the mini project"""

  

import sys

  

product_list = ["White Americano","Black Americano", "Cappuccino", "Mocha", "Latte",

                "Cortado", "Macchiato", "Iced Americano", "Iced Cappuccino", "Iced Mocha",

                "Iced Latte", "Iced Cortado", "Iced Macchiato"]

customers_orders = []

  
  

def products_get_user_choice():

    """Get's the user's choice and returns the value to be cached later."""

    user_choice = input("\n\n\n\n\n\nPlease pick an operation:\nReturn to main menu (0).\

                        \nPrint product list (1).\

                        \nAdd Product to list (2).\nUpdate existing product (3).\

                        \nDelete Product(4). \n")

  

    while user_choice not in ["0", "1", "2", "3", "4"]:

        print("Please pick a valid number.")

        user_choice = input("Please pick an operation:\nReturn to main menu (0)."

                            "\nPrint product list (1).\

                            \nAdd Product to list (2).\nUpdate existing product (3).\

                            \nDelete Product(4). \n")

    user_choice = int(user_choice)

    return user_choice

  

def show_products():

    """Generates an indexed list of products."""

    print("Here is the list of the products:")

    for (i, item) in enumerate(product_list, start = 0):

        print(i, item)

  
  
  
  

def products_decision_tree():

    """The decision tree for the products program goes through to provide different end user functions"""

    user_choice_cache = products_get_user_choice()

    if user_choice_cache == 0:

        print("Returning to the main menu.\n\n\n\n\n\n")

    elif user_choice_cache == 1:

        product_list_length = len(product_list)

        show_products()

    elif user_choice_cache == 2:

        user_addition = str(input("What item do you wish to add to the list?\n"))

        product_list.append(user_addition)

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

        show_products()

    elif user_choice_cache == 4:

        product_list_length = len(product_list) - 1

        show_products()

        user_change = int(input(f"Which item do you wish to delete? 0-{product_list_length}: "))

        while user_change < 0 or user_change > product_list_length:

            print("That is not a valid input")

            user_change = int(input(f"Which item do you wish to change? 0-{product_list_length}: "))

        product_list.pop(user_change)

        show_products()

  
  
  
  

def orders_get_user_choice():

    """Get's the user's choice and returns the value to be cached later."""

    user_choice = input("\n\n\n\n\n\nPlease pick an operation:\nReturn to main menu (0).\

                        \nPrint order list (1).\

                        \nAdd Order to list (2).\nUpdate existing order (3).\

                        \nDelete Order(4). \n")

  

    while user_choice not in ["0", "1", "2", "3", "4"]:

        print("Please pick a valid number.")

        user_choice = input("\n\n\n\n\n\nPlease pick an operation:\nReturn to main menu (0).\

                        \nPrint order list (1).\

                        \nAdd Order to list (2).\nUpdate existing order (3).\

                        \nDelete Order(4). \n")

    user_choice = int(user_choice)

    return user_choice

  

def show_orders():

    """Shows a list of saved orders, formatted in dictionaries"""

    print("Here is the list of the orders:")

    for (i, item) in enumerate(customers_orders, start = 0):

        print(f"""Order: \n{i}.

              \nCustomer Name:{[item['customer-name']]}

              \nCustomer Address:{[item['customer-address']]}

              \nCustomer Phone #:{[item['customer-phone']]}

              \nStatus:{[item['status']]} """)

  
  
  

def orders_decision_tree():

    """Decision tree if user chooses o"""

    user_choice_cache = orders_get_user_choice()

    if user_choice_cache == 0:

        print("Returning to the main menu, please select the appropriate inputs.\n\n\n\n\n\n")

    elif user_choice_cache == 1:

        order_list_length = len(customers_orders) - 1

        show_orders()

    elif user_choice_cache == 2:

        customer_name = str(input("What is your name?\n"))

        customer_address = str(input("What is your address?\n"))

        customer_phone = str(input("What is your phone number?\n"))

        statuses = ["preparing", "paid", "completed"]

        status_length = len(statuses) - 1

        for (i, item) in enumerate(statuses, start = 0):

            print(i, item)

        chosen_status_ind = int(input(f"Please pick a status 0-{status_length}: "))

        chosen_status = statuses[chosen_status_ind]

        temp_dict = {

            "customer-name": customer_name,

            "customer-address": customer_address,

            "customer-phone": customer_phone,

            "status": chosen_status,

        }

        customers_orders.append(temp_dict)

        print(customers_orders)

        show_orders()

    elif user_choice_cache == 3 and customers_orders:

        order_list_length = len(customers_orders) - 1

        show_orders()

        user_change = int(input(f"Which order do you wish to change? 0-{order_list_length}: "))

        while user_change < 0 or user_change > order_list_length:

            print("That is not a valid input")

            user_change = int(input(f"Which item do you wish to change? 0-{order_list_length}: "))

        valid_keys = ["customer-name", "customer-address", "customer-phone", "status"]

        key_change = str(input(f"What about the order would you like to update? {valid_keys}\n").lower())

        while key_change not in valid_keys:

            print("That is not a valid input.")

            key_change = str(input(f"What about the order would you like to update? {valid_keys}\n").lower())

        details_change = str(input("What do you wish to change it to?\n"))

        customers_orders[user_change][key_change] = details_change

        show_orders()

    elif user_choice_cache == 4 and customers_orders:

        order_list_length = len(customers_orders) - 1

        show_orders()

        user_change = int(input(f"Which order do you wish to delete? 0-{order_list_length}: "))

        while user_change < 0 or user_change > order_list_length:

            print("That is not a valid input")

            user_change = int(input(f"Which item do you wish to change? 0-{order_list_length}: "))

        customers_orders.pop(user_change)

        show_orders()

    else:

        print("No current orders")

  

if __name__ == "__main__":

    X = "y"

    while X != "n":

        try:

            function_choice = str(input("Please choose whether to access products (p) or access ordering function (o): ").lower())

            while function_choice not in ["o", "p"]:

                print("That is not a valid choice.")

                function_choice = str(input("Please choose whether to access products (p) or access ordering function (o): ").lower())

            if function_choice == "p":

                stay_products = "y"

                while stay_products == "y":

                    products_decision_tree()

                    stay_products = str(input("Would you like to stay on the products program?\

                        y/n: ").lower())

            elif function_choice == "o":

                stay_orders = "y"

                while stay_orders == "y":

                    orders_decision_tree()

                    stay_orders = str(input("Would you like to stay on the orders program? y/n: ").lower())

        except ValueError:

            print("You have inputted the wrong data type, running the program again...")

            continue

        X = str(input("Continue? Return to main menu (y) or exit (n).\n").lower())

        while X not in ["y", "n"]:

            print("Please enter a valid input, y/n")

            X = str(input("Return to main menu? (y) or exit (n)\n").lower())

  

print("Goodbye =)")

sys.exit()
```