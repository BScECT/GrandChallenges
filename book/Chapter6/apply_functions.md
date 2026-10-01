## Giving a function something to work with
A function that always prints the same header is nice, but not very useful. Just like `int()` needs something to cast, most functions need some input to work with. You can give a function input using **parameters**. You write them in between the parentheses:

```Python
def print_kelvin(celsius):
    kelvin = celsius + 273.15
    print(kelvin, "K")

print_kelvin(20)  # prints 293.15 K
print_kelvin(-5)  # prints 268.15 K
```

Here `celsius` is a **parameter**. It is a variable that only gets its value when the function is called. The value that you put in between the parentheses when calling the function is called the **argument**.

So when you call `print_kelvin(20)`, Python does two things:
1. it **assigns** the argument to the parameter, so `celsius = 20`
2. it runs the indented code of the function, using that value

Does that sound familiar? It is very similar to how a `for` loop **assigns** each item of a list, one by one, to the `item` variable.

You can also use a variable as an argument. The name of that variable does not have to match the name of the parameter. Python simply takes the value that is stored in it:

```Python
temperature_delft = 4.5
print_kelvin(temperature_delft)  # prints 277.65 K
```

### More than one parameter
A function can have as many parameters as you like. You separate them with commas, just like the items in a list:

```Python
def print_station_report(station, celsius):
    kelvin = celsius + 273.15
    print(station + ":", kelvin, "K")
    if celsius < 0:
        print("It is freezing in " + station)
```

And now take a look at what happens to the fifteen lines of code we started this chapter with:

```Python
print_station_report("Delft", 4.5)
print_station_report("Utrecht", -1.2)
print_station_report("Groningen", -3.0)
```

Three lines! And if you find a typo in `273.15`, you only have to fix it in one place. Copy the function above and call it in your own python notebook.

Note that the **order** of the arguments matters. Python assigns the first argument to the first parameter, the second argument to the second parameter, and so on. So in the call `print_station_report("Delft", 4.5)`, `station` becomes `"Delft"` and `celsius` becomes `4.5`.

### Exercise
What happens when you call `print_station_report(-1.2, "Utrecht")`? Try it out and explain the error that Python gives you. *Hint: think back to what you learned about variable types in Chapter 2.*

## Getting something back
So far, our functions **print** their result. That is fine if you only want to look at the result, but you cannot calculate any further with something that is printed on your screen. Think of `int()`: it would be quite useless if it only printed the integer, instead of giving it back to you so you can store it in a variable.

To give something back from a function, you use the `return` keyword:

```Python
def celsius_to_kelvin(celsius):
    kelvin = celsius + 273.15
    return kelvin

kelvin_delft = celsius_to_kelvin(4.5)
print(kelvin_delft)  # prints 277.65
```

The function calculates the temperature in Kelvin and hands it back to the line of code that called it. There, we store it in the variable `kelvin_delft`, and we can do with it whatever we want.

:::{admonition} Printing is not the same as returning
:class: warning
In the previous chapters we used the word *return* quite loosely, as in "`print(1 + 1)` returns `2`". From now on we need to be a bit more precise. **Printing** means: showing something on the screen, for a human to read. **Returning** means: handing a value back to your code, so the program can keep working with it. That is why, from this chapter on, the comments in the code examples say *prints* whenever something is shown on your screen.
:::

You can see the difference when you try to store the "result" of a function that only prints:

```Python
result = print_kelvin(20)  # prints 293.15 K
print(result)              # prints None
```

`print_kelvin` shows the answer on the screen, but it doesn't hand anything back. So there is nothing to store in `result`, and Python tells you so with `None`, its way of saying "nothing".

### Using what a function returns
Because a function call is replaced by the value it returns, you can use it anywhere you would otherwise use a variable. In a calculation:

```Python
difference = celsius_to_kelvin(25) - celsius_to_kelvin(15)
print(difference)  # prints 10.0
```

Or as a condition in an `if` statement:

```Python
measurement = -300
if celsius_to_kelvin(measurement) < 0:
    print("That is colder than absolute zero. Check your thermometer!")
```

A function can return any type of variable: a number, a string, a list, a dictionary, and also a **boolean**. Remember that a comparison always results in either `True` or `False`? That means we can return a comparison directly:

```Python
def is_freezing(celsius):
    return celsius < 0

print(is_freezing(-3.0))  # prints True
print(is_freezing(4.5))   # prints False

if is_freezing(-1.2):
    print("Watch out for slippery roads")
```

Read that last `if` statement out loud: *if is freezing, print watch out for slippery roads*. That is almost English! Good function names make your code easy to read.

### Return means: stop
One more thing to know about `return`: as soon as Python reaches a `return`, the function stops, and any code below it inside the function is skipped. It works a bit like `break` in a loop.

```Python
def celsius_to_kelvin(celsius):
    kelvin = celsius + 273.15
    return kelvin
    print("You will never see this")  # never runs, the function already stopped
```

### Exercise
Write a function `celsius_to_fahrenheit` that takes a temperature in degrees Celsius and **returns** the temperature in degrees Fahrenheit, using $F = C \cdot \frac{9}{5} + 32$. Check your function: `celsius_to_fahrenheit(100)` should give `212.0`, and `celsius_to_fahrenheit(-40)` should give `-40.0`.