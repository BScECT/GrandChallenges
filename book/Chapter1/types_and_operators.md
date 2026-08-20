# Doing stuff
Great. Now you've got the basics for input, you've got the basics for output. But a program that only ever spits out the same thing that you feed it is not very useful. A useful program needs to take that data and do stuff. Preferably the stuff that you want it to do.

However, before we get into the *doing stuff* part, there is one last piece of vital basic programming knowledge you will need. You will need to understand why:

```Python
"one" + "one" != "two"
```

## Variable types
In the last section we already quickly touched on variables as a way to name certain datapoints. What I forgot to mention however, is that each variable has a certain `type` associated with it as well, which tells what kind of data is stored within the variable.

When we created the `Hello World` variable a few sections back, Python gave it the **string** type, which means it stores text (or a *string of characters*). We can always check what type a certain variable is in Python by using the `type()` function.

```Python
string_variable = "This is a string because I use quotation marks around text"
type(string_variable)
```
Try it out yourself, and it will return `<class 'str'>`, where `str` is shorthand for string.

String is only one of many types that Python has out of the box. There are many others and you can even create your own. The following, however, are the most important ones:
- String or `str`: a line of text, like `"Hello World"`
- Integer or `int`: a number without decimal point, like `12`
- Floating-point number or `float`: a number with a decimal point, like `7.3`
- Boolean or `bool`: a value that is either true or false, like `True`
- List or `list`: a list of other variables, like `[1, 2, 3]`
- Dictionary or `dict`: a collection where the values have names, like `{"one": 1, "two", 2}`

Don't worry if some of these seem complex now, by the end of this course you will have no problem understanding what they are, and what they do.

## Types show what you can do with a variable
Now, what's the point of all of this? We specify variable types because each type of variable can do different things. We can use integers and floats for calculations, while we use strings to build texts.

```Python
result = 1 + 1
print(result)  # Returns 2
```
