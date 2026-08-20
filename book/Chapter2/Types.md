## Types of variables

Variables in Python come in different types, and the type determines what you can do with them. The most common ones you'll meet early on are:

- **Integers** (`int`) — whole numbers, like `19` or `-3`
- **Floats** (`float`) — decimal numbers, like `7.8` or `3.14`
- **Strings** (`str`) — text, written between quotes, like `"Sam"` or `"hello"`
- **Booleans** (`bool`) — one of two values, `True` or `False`, often the result of a comparison

You can check what type of object is assigned to a variable using Python's built-in <b><code>type()</code></b> function.

```{admonition} Attention
:class: danger
Always check the type of your variables as this is important to determine how the variables can be used in equations.
+++
```

### Floating point numbers and integers


```python
type(a)

float_var = 3.1415
type(float_var)
```
```python
a = 0.3
b = 0.2
c = a - b
print(c)
```
You probably noticed that Python wrote $0.09999999999999998$ instead of $0.1$ when calculating $0.3 - 0.2$. 

Integers are whole numbers and floats are real numbers (with a decimal point).
On computers, these are called floating point numbers (where 'point' refers to the decimal point) or 'float' for short. 

An important thing to remember with floating point numbers is that doing mathematical operations with them is not exact, small rounding errors will appear. Even in simple calculations such as 0.3 - 0.1. Try to run the cell below and see the result.

```python
0.3 - 0.1
```

### Booleans

```python
type(1 < 2)
```

Boolean variables can only take on two values: <b><code>True</code></b> or <b><code>False</code></b>. They are often used to check conditions.

```python
1 < 2
```

### Strings
message = 'Hello world!'
type(message)


## Casting types

Sometimes you want to change the type of a variable. For example, there is no point in arithmetically adding a number to a string. These problems can sometimes be solved with casting. <b>Casting</b> is a procedure of changing variable type. Actually, you create a new variable with the requested data type using the variable you want to alter.

For example: 
```python
string_number = '123'
print(string_number, type(string_number))

integer_number = int(string_number)
print(integer_number, type(integer_number))    
```

As you can see, both variables look the same in the output but their type now is different. Because of that, the cell below will result in an error.
```python
string_number + 5
```
But the next cell will run normally.

```python
integer_number + 5
```

