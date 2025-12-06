Writing Small, Focused Functions (#15)

1. Why small, single-purpose functions are important
They do only one job, so they are easy to understand.
They reduce bugs because the logic is clear and simple.
They make the code easier to test — each function can be checked alone.
They make debugging faster — you immediately know where things went wrong.
They allow code reuse in other parts of the program.
They make the whole file cleaner and easier for teammates to read.

2. Example of a long, complex function (bad example)
python
Copy code
def process_order(order):
    # validation
    if not order["item"]:
        return "Error"

    # price calculation
    price = order["qty"] * 100

    # discount logic
    if order["qty"] > 5:
        price *= 0.9

    # tax calculation
    price = price + (price * 0.05)

    # save order
    print("Order saved to database")

    # send confirmation
    print("Email sent to customer")

    return price
This one function is doing way too many things:
validation
price calculation
discount
tax
saving
sending email
This is a “God function” — hard to read, test, or fix.

3. Refactored into small, clear functions
python
Copy code
def validate(order):
    return order["item"] is not None

def calculate_price(order):
    price = order["qty"] * 100
    if order["qty"] > 5:
        price *= 0.9
    return price

def add_tax(price):
    return price + (price * 0.05)

def save_order(order):
    print("Order saved to database")

def send_confirmation():
    print("Email sent to customer")

def process_order(order):
    if not validate(order):
        return "Error"

    price = calculate_price(order)
    final_price = add_tax(price)
    save_order(order)
    send_confirmation()

    return final_price
Now each function does ONE job.

4. How refactoring improved the structure
Code is easier to read because the logic is separated into small parts.
Each function has a clear purpose (validation, price, tax, saving, emailing).
If something breaks, it is easy to find which function caused the problem.
Testing becomes simpler — you can test calculate_price() or add_tax() alone.
The code looks cleaner and is easier for teammates to understand.

5. Reflection
Large functions grow messy quickly and are hard to maintain.
After refactoring, the code became much more organized and readable.
I learned that writing small, focused functions improves quality and makes debugging faster.
This style also follows the Single Responsibility Principle (SRP) — a key clean code rule.

