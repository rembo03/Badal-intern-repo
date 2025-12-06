Refactoring Code for Simplicity

1. What is refactoring?
Refactoring means improving the structure of existing code
without changing what the code actually does.
It makes the code:
simpler
cleaner
easier to understand
easier to maintain

2. Why simplicity matters
Simple code is easier to read.
Fewer bugs because the logic is clear.
Future changes become easier.
New developers can understand the project faster.
Reduces stress when debugging.

3. Example of complex code (bad example)
python
Copy code
def get_final_price(qty, price, holiday, discount):
    if holiday == True:
        if discount == True:
            result = (qty * price) - ((qty * price) * 0.25)
        else:
            result = (qty * price) - ((qty * price) * 0.10)
    else:
        if discount == True:
            result = (qty * price) - ((qty * price) * 0.15)
        else:
            result = qty * price
    return result
Problems:
Too many nested if-else conditions
Repeated expressions (qty * price)
Hard to understand at a glance

4. Refactored simple version
python
Copy code
def base_total(qty, price):
    return qty * price

def holiday_discount(total):
    return total * 0.10

def full_discount(total):
    return total * 0.25

def small_discount(total):
    return total * 0.15

def get_final_price(qty, price, holiday, discount):
    total = base_total(qty, price)

    if holiday and discount:
        return total - full_discount(total)

    if holiday:
        return total - holiday_discount(total)

    if discount:
        return total - small_discount(total)

    return total
Benefits:

No repeated code
Very easy to read
Small helper functions make logic clear
Easier to update discounts later

5. How refactoring improved the code
Removed unnecessary complexity
Broke long function into smaller pieces
Logic now looks clean and readable
Each part has a clear responsibility
Much easiyer to test and debug

6. Reflections
I learned that “simple code” doesn’t mean fewer lines — it means clearer logic.
Refactoring makes the code easier for both me and future team members.
It helps avoid bugs because the logic becomes organized.
Clean code = faster development + fewer mistakes.

