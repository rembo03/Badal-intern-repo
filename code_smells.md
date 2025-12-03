
## 1. Magic Numbers & Strings

**Smell:** Using hardcoded values.

**Bad example:**

```
if age > 18:
    ticket_price = 250
```

**Refactored:**

```
ADULT_AGE = 18
BASE_TICKET_PRICE = 250

if age > ADULT_AGE:
    ticket_price = BASE_TICKET_PRICE
```

**Why better:** easier to update and understand.

---

## 2. Long Functions

**Smell:** Function doing too many things.

**Bad example:**

```
def process_order(order):
    if not order["item"]: return "Error"
    price = order["qty"] * 100
    print("Order saved")
    return price
```

**Refactored:**

```
def validate(order):
    return order["item"] is not None

def calculate_price(order):
    return order["qty"] * 100

def save_order(order):
    print("Order saved")

def process_order(order):
    if not validate(order):
        return "Error"
    price = calculate_price(order)
    save_order(order)
    return price
```

**Why better:** cleaner and easier to test.

---

## 3. Duplicate Code

**Smell:** Same logic repeated.

**Bad example:**

```
print(user.name + " logged in")
print(user.name + " logged out")
```

**Refactored:**

```
def log_action(user, action):
    print(user.name + " " + action)
```

**Why better:** one function reuse.

---

## 4. Large Class (God Object)

**Smell:** Class doing everything.

**Bad example:**

```
class UserManager:
    def create_user(self): ...
    def delete_user(self): ...
    def process_payment(self): ...
    def generate_report(self): ...
    def send_email(self): ...
```

**Refactored:** split responsibilities:

```
class UserService: ...
class PaymentService: ...
class ReportService: ...
class EmailService: ...
```

---

## 5. Deeply Nested Conditionals

**Smell:** Too many nested if-else.

**Bad example:**

```
if user:
    if user.is_active:
        if user.is_admin:
            print("Welcome Admin")
```

**Refactored:**

```
if not user or not user.is_active:
    return

if user.is_admin:
    print("Welcome Admin")
```

---

## 6. Commented-Out Code

**Smell:** Old unused code left in files.

**Bad example:**

```
# user.login()
# print("debug")
```

**Refactored:** remove it. Git history exists.

---

## 7. Inconsistent Naming

**Smell:** Names not matching purpose.

**Bad example:**

```
a = 10
b = "John"
```

**Refactored:**

```
age = 10
user_name = "John"
```

---

# Reflection

### What code smells did I find?

Magic numbers, long functions, duplicate code, large classes, deep nesting, commented code, inconsistent naming.

### How did refactoring help?

* Code became cleaner.
* Easier to understand.
* Less chance of bugs.
* Functions and classes do one job.

### How does avoiding smells help debugging?

* Mistakes are easier to find.
* Code is organized.
* Less duplicated logic.
* Each part is small and simple.

---

End of file.
# code_smells.md

## 1. Magic Numbers & Strings

**Smell:** Using hardcoded values.

**Bad example:**

```
if age > 18:
    ticket_price = 250
```

**Refactored:**

```
ADULT_AGE = 18
BASE_TICKET_PRICE = 250

if age > ADULT_AGE:
    ticket_price = BASE_TICKET_PRICE
```

**Why better:** easier to update and understand.

---

## 2. Long Functions

**Smell:** Function doing too many things.

**Bad example:**

```
def process_order(order):
    if not order["item"]: return "Error"
    price = order["qty"] * 100
    print("Order saved")
    return price
```

**Refactored:**

```
def validate(order):
    return order["item"] is not None

def calculate_price(order):
    return order["qty"] * 100

def save_order(order):
    print("Order saved")

def process_order(order):
    if not validate(order):
        return "Error"
    price = calculate_price(order)
    save_order(order)
    return price
```

**Why better:** cleaner and easier to test.

---

## 3. Duplicate Code

**Smell:** Same logic repeated.

**Bad example:**

```
print(user.name + " logged in")
print(user.name + " logged out")
```

**Refactored:**

```
def log_action(user, action):
    print(user.name + " " + action)
```

**Why better:** one function reuse.

---

## 4. Large Class (God Object)

**Smell:** Class doing everything.

**Bad example:**

```
class UserManager:
    def create_user(self): ...
    def delete_user(self): ...
    def process_payment(self): ...
    def generate_report(self): ...
    def send_email(self): ...
```

**Refactored:** split responsibilities:

```
class UserService: ...
class PaymentService: ...
class ReportService: ...
class EmailService: ...
```

---

## 5. Deeply Nested Conditionals

**Smell:** Too many nested if-else.

**Bad example:**

```
if user:
    if user.is_active:
        if user.is_admin:
            print("Welcome Admin")
```

**Refactored:**

```
if not user or not user.is_active:
    return

if user.is_admin:
    print("Welcome Admin")
```

---

## 6. Commented-Out Code

**Smell:** Old unused code left in files.

**Bad example:**

```
# user.login()
# print("debug")
```

**Refactored:** remove it. Git history exists.

---

## 7. Inconsistent Naming

**Smell:** Names not matching purpose.

**Bad example:**

```
a = 10
b = "John"
```

**Refactored:**

```
age = 10
user_name = "John"
```

---

# Reflection

### What code smells did I find?

Magic numbers, long functions, duplicate code, large classes, deep nesting, commented code, inconsistent naming.

### How did refactoring help?

* Code became cleaner.
* Easier to understand.
* Less chance of bugs.
* Functions and classes do one job.

### How does avoiding smells help debugging?

* Mistakes are easier to find.
* Code is organized.
* Less duplicated logic.
* Each part is small and simple.

---

End of file.
