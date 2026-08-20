# More than one thing can be true
We know now that, in Python, booleans come in many shapes and sizes, though in the end they are always either `True` or `False`. We can create booleans by comparing parameters, or by using logical operators. I would like to wrap up by showing that many other **types** of **variables** can be **cast** to a boolean as well.

For example: an integer of `0` will be `False`, while any other integer value will be `True`:
```Python
print(bool(0))  # returns False
```

An empty string `""` will be `False`, while any string with characters `"hello"` will be `True`:
```Python
print(bool("False"))  # returns True
```

Lists and dictionaries (we will cover them next week), will also be either `False` or `True` depending on whether they have values in them.

## Our advantage
We can use these variables directly in conditional statements, for example like so:
```Python
name = input("What's your name? ")
if not name:
    print("You forgot to answer the question, dummkopf")
else:
    print("Hi! " + name)
```
Personally, I find that nicer to read than `if name == ""`, which sounds more computery. However, it is a good idea to always check whether a certain **value** actually is `True` or `False` for your specific **type**. Use `bool()` to find out what's what.