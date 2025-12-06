Avoiding Code Duplication (#14)
1. What is code duplication?
Code duplication happens when the same logic is written in multiple places instead of reusing a single function.

Example of duplication:

Copy-pasting the same calculation in different files

Writing the same validation in many functions

Repeating the same loops, conditions, or formatting logic

2. Why duplicated code is bad
Harder to maintain

If you fix a bug in one place, you must fix it everywhere

Easy to forget one copy → creates new bugs

Makes the code longer and confusing

New team members struggle to understand which version is correct

3. Example of duplicated code (bad example)
python
Copy code
# calculating discount in two places
price = qty * 100
if qty > 5:
    price = price * 0.9

# later in the code, same logic again
discounted_price = quantity * 100
if quantity > 5:
    discounted_price = discounted_price * 0.9
This is the same code repeated twice.

4. Refactored version (good example)
python
Copy code
def apply_discount(qty):
    price = qty * 100
    if qty > 5:
        price = price * 0.9
    return price

# reuse the function anywhere
price = apply_discount(qty)
discounted_price = apply_discount(quantity)
Now we only write the logic once and reuse it.

5. How refactoring improved the code
No repeated logic → easier to update

If discount rules change, update one function only

Code is shorter and easier to read

Less chance of inconsistent behavior

Makes the project easier for teammates

6. Reflection
Before refactoring, the code was repetitive and hard to manage.

After removing duplication, everything became cleaner and more reliable.

I learned that avoiding duplication saves time and prevents many bugs.

Following the DRY rule (“Don’t Repeat Yourself”) is important for clean code.

