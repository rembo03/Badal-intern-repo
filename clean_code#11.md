Handling Errors & Edge Cases

1. What are edge cases?
Edge cases are unusual or extreme situations that normal code may not handle.
Examples:
Empty input
Negative numbers
Very large values
Missing fields
Null / None values
Wrong data types
Network failure
File not found
These are common sources of bugs.

2. Why handling errors is important
Prevents the program from crashing
Makes the app more reliable
Creates a better user experience
Helps developers understand what went wrong
Ensures your code behaves correctly in all situations

3. Bad example (no error handling)
python
Copy code
def divide(a, b):
    return a / b
Problems:
If b = 0, the app crashes
If inputs are not numbers, it fails
User gets no helpful message

4. Good example (with proper error handling)
python
Copy code
def divide(a, b):
    if b == 0:
        return "Error: Cannot divide by zero"

    try:
        return a / b
    except TypeError:
        return "Error: Inputs must be numbers"
Benefits:
Safe handling of division by zero
Clear message for wrong input types
Prevents the function from crashing

5. More examples of edge case handling
Missing fields

python
Copy code
def get_user_age(user):
    if "age" not in user:
        return "Error: Age is missing"
    return user["age"]
Empty strings

python
Copy code
def greet(name):
    if not name:
        return "Error: Name cannot be empty"
    return "Hello " + name
6. How this improved my code
The code is now safe in unexpected situations
Easier to debug when an error happens
Prevents crashes during real user interactions
More professional and reliable behavior

7. Reflection
I learned that edge cases cause many hidden bugs.
Adding error checks makes the program stronger.
Writing safe code is just as important as writing working code.
Thinking about “what could go wrong?” helps me write cleaner, more stable functions.

