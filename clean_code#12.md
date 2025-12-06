Commenting & Documentation
1. Why comments are important
They explain why the code exists, not just what it does.
Help future developers understand your thinking.
Useful for complex logic or tricky parts of the code.
Make onboarding easier for new team members.

2. What makes a good comment?
Short and clear
Explains why, not obvious things
Updated when code changes
Written in simple language
Good example:
python
# Calculate overtime only if user worked more than 8 hours
overtime = hours_worked - 8 if hours_worked > 8 else 0
Bad example:
python
Copy code
# subtract
x = a - b
(Anyone can Already SEE that without a comment.)

3. What should NOT be commented
Obvious code
Commenting every line
Old commented-out code (remove it—Git saves history)
Comments that restate code exactly

4. Documentation good practices
Add a short description at the top of files or functions.
Describe inputs, outputs, and purpose.
Use docstrings (Python), JSDoc (JavaScript), or comments above functions.

5. How refactoring improved readability
Removed unnecessary comments
Added clear explanations where needed
Code became easier to understand without reading deep logic
Future changes will be easier and faster

