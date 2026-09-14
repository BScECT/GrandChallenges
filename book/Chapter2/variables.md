# Variables in Python

More information in Think Python (2nd ed.) - Section 2

When you want to compute something, you often need to store a piece of information so you can use it later, for example a number, a name, a result of a calculation. In Python, you do this with a **variable**. Think of a variable as a labeled box: you give it a name, and you put a value inside it.

```python
age = 19
name = "Sam"
gpa = 7.8
```

Here, `age`, `name`, and `gpa` are variables. The `=` sign doesn't mean "equals" like in math, it means "assign this value to this name." So `age = 19` reads as "store 19 in a box called age." You can change what's in the box at any time by assigning it a new value, and Python will always use the most recent one.

Variable names in Python can contain letters, numbers, and underscores, but can't start with a number, and can't contain spaces (use `first_name`, not `first name`). Python is also case-sensitive, so `Age` and `age` are treated as two different variables. It's good practice to give variables names that describe what they hold, so your code stays readable.