## Types of values

Values in Python come in different types, and the type determines what you can do with them. The most common ones you'll meet early on are:

- **Integers** (`int`) — whole numbers, like `19` or `-3`
- **Floats** (`float`) — decimal numbers, like `7.8` or `3.14`
- **Strings** (`str`) — text, written between quotes, like `"Sam"` or `"hello"`
- **Booleans** (`bool`) — one of two values, `True` or `False`, often the result of a comparison

You can check what type of object is assigned to a variable using Python's built-in `type ` function. Below are a few examples:
```Python
a = 5
print(type(a))  # returns int

b = 5.1
print(type(b))  # returns float
```
*Strings* are variables represented in between `' '` or `" "`. They are called that way because they are a *string* of characters. We've already dealt with strings last week, you may remember the `"Hello World"` example:
```Python
c = "Hello world!"
print(type(c))  # returns string

```
Boolean variables can only take on two values: `True` or `False`. They are often used to check *conditions* (More on that in the next chapter).
```Python
d = True
print(type(d))  # returns bool
```

## Casting types

Sometimes you want to change the type of a variable. For example, there is no point in arithmetically adding a number to a string. These problems can sometimes be solved with casting. *Casting* is a procedure of changing a variable type. Actually, you create a new variable with the requested data type using the variable you want to alter. You can change a `string` into an `int` for example:
```Python
string_number = '123'
print(string_number, type(string_number))

integer_number = int(string_number)
print(integer_number, type(integer_number))
```
As you can see, both variables look the same in the output but their type now is different. Because of that, the cell below will result in an error.
```Python
string_number + 5
```
But the next cell will run normally.
```Python
integer_number + 5
```