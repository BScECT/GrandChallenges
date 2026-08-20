# Nothing but the truth
Last week we recapped on **variables**, different **types** of variables and how to manipulate those variables using **operators**. This week we will be diving into, maybe, the most important variable type that we have: `boolean`s. In essence, they are very simple: they can only be either `True` or `False`:

## Creating booleans
The simplest way you can create a `bool` is by using the built-in `True` and `False` parameters (**literals**, technically) that are always available:
```Python
print(type(True))  # returns bool
print(type(False))  # returns bool
```

But just on it's own that's not very useful at all. The more interesting way to create `booleans` is by using either **comparison operators** or **logical operators**.

### Comparison operators
There are six different comparison operators, and you will probably remember them from mathematics:
* `==` equals
* `!=` does not equal
* `<` smaller than
* `>` greather than
* `<=` smaller than or equal to
* `>=` greater than or equal to

If we use these to compare different variables, you may imagine that the result is either `True` or `False`. For example:
```Python
print(1 == 2)  # returns False
print(1 + 1 == 2)  # returns True
print(type(1 + 1 == 2))  # returns bool
```

### Logical operators
There are three different logical operators, and they are quite simple:
* `and` or `&&`
* `or` or `||`
* `not` or `!`

Logical operators are used to compare `booleans` with each other! The ways in which they do looks like this:
```Python
print(True and True)  # returns True
print(True and False)  # returns False
print(False and False) # returns False

print(True or True)  # returns True
print(True or False)  # returns True
print(False or False)  # returns False

print(not True)  # returns False
print(not False)  # returns True
```
It may take some time to fully get the grasp of this, but practice makes perfect! Before you know it you will be reading this code as if it where English.

Note that each also has a symbol notation. I don't necessarily recommend using them as they make your code harder to read, but you need to know they exist, because you will encounter them.

## Combining operators
As you may imagine, you can combine these operators to your heart's desire. For example:

```Python
age = 21
have_drivers_license = True

allowed_to_drive = have_drivers_license and age >= 18
print(allowed_to_drive)  # returns True
```

Although for the Dutch case we will have to add some parentheses `()`, which will tell Python what to evaluate first (just like in math):
```Python
age = 21
have_drivers_license = True
has_co_driver = False

allowed_to_drive = (have_drivers_license and age >= 18) or (have_drivers_license and age >= 17 and has_co_driver)
print(allowed_to_drive)  # returns True
```
If you can figure out what the Dutch law on driving age restrictions is based on this code, you are well on your way to becoming a programmer!

## What makes booleans so important?
`booleans` are used to control the **flow** of a computer programme. As we discussed in chapter 1, Python works by **interpreting** your lines of code one by one, one after the other. Totally fine if your code only has to do one thing once and then stop. Most code, however, is a little (or much) smarter than that: it can do certain things only when you want it to. Only `if` a certain **condition** is `True`, for example.