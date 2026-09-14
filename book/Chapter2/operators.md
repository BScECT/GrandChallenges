# Arithmetic operators

Once you have variables, operators let you do things with them. 

Arithmetic operators work on numbers the way you'd expect from math class: `+` for addition, `-` for subtraction, `*` for multiplication, and `/` for division. Python also has a few extras that are useful in programming: `**` for exponents (`2 ** 3` gives `8`), and `//` for division that rounds down to a whole number (`7 // 2` gives `3`).

| Math sign | Python sign | name |
| :-: | :-: |:-:|
| + | + | addition |
| - | - | subtraction |
| * | * | multiplication |
| / | / | division |
| ^ | ** | exponentiation |
|  | // | floor division |

For example:
```python
total = 5 + 3      # returns 8
product = 4 * 2    # returns 8
floor_division = 7 // 2  # returns 3
```

Most of the mathematical symbols stay the same when transforming a piece of mathematics to Python. Note that the exponentiation sign is a double multiplication sign!

Now we can perform operations with this variable. For example, we can add it to itself:

```Python
# Adding variables
b = a + a
print(b)  # returns the value of a and a added together
```

What happens on reassignment? Will Python let us write over it?
```Python
# Reassignment
a = 20
# Check
print(a)  # returns 20 now, instead of the previous value
```

Yes! Python allows you to overwrite assigned variable names. We can also use the variables themselves when doing the reassignment. Since `a = 20` was the last assignment to our variable `a`, you can keep using `a` in place of the number `20`:

```Python
a = a + 5
print(a)  # returns 25 now
```

Try this code in your Jupyter Notebook.