1. What makes a good variable or function name?
Clear and easy to understand.
Describes what the value or function actually does.
Uses full words, not confusing short forms.
Consistent style (camelCase, snake_case, etc.).
Not too long, not too short.
Avoids generic names like data, temp, a, x, func1.

2. Examples of unclear names (bad examples)
a = 10
b = "John"
tmp = 45
fn(x): return x * 2

3. Refactored clear names (good examples)
age = 10
user_name = "John"
retry_count = 45
def double_value(number):
    return number * 2

4. Why poor variable names cause issues
Hard to understand what the code does.
New developers get confused.
Bugs become harder to find.
You may forget what the variable was for.
Code takes longer to maintain.

5. How refactoring improved readability
Code became easier to understand at a glance.
I didn’t need comments to explain variable names.
Each name now clearly explains its purpose.
Functions describe exactly what they do.
Cleaner code helps avoid mistakes in the future.
End of file.