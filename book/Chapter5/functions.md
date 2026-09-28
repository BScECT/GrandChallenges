# Write it once, use it forever: Functions

Over the past weeks you have filled up quite a toolbox: **variables**, **operators**, `if` statements, **lists**, **dictionaries** and **loops**. With these tools you can already write surprisingly smart programs. But the longer your programs get, the more often you will catch yourself writing the same few lines of code over and over again. To solve that problem, this chapter teached you how to write functions. For more information, read Think Python (3rd ed.) chapter 3 and 6.

## Example: Regional temperature
Say you have measured the temperature at three weather stations in degrees Celsius. For each station you want to show the temperature in Kelvin, and get a warning when it is freezing:

```Python
temperature_delft = 4.5
kelvin_delft = temperature_delft + 273.15
print("Delft:", kelvin_delft, "K")
if temperature_delft < 0:
    print("It is freezing in Delft")

temperature_utrecht = -1.2
kelvin_utrecht = temperature_utrecht + 273.15
print("Utrecht:", kelvin_utrecht, "K")
if temperature_utrecht < 0:
    print("It is freezing in Utrecht")

temperature_groningen = -3.0
kelvin_groningen = temperature_groningen + 273.15
print("Groningen:", kelvin_groningen, "K")
if temperature_groningen < 0:
    print("It is freezing in Groningen")
```

This contains 15 lines of code that do exactly the same thing three times. Now imagine you made a typo in `273.15`: you would have to fix it in three places. And now imagine you have a hundred weather stations. Your fingers hurt just thinking about it.

Programmers are lazy people (in a good way). If they have to do something twice, they would rather write it once and give it a name. That is exactly what a **function** is: a named block of code that you write once, and then use as often as you like.

## You have been using functions all along
Functions are not completely new to you. You have been using them since the very first week:
- `print()` shows something on your screen
- `input()` asks the user to type something
- `type()` tells you the type of a variable
- `int()` and `bool()` cast a variable to another type
- `range()` gives you a list-like object full of numbers

They all look the same: a **name**, followed by **parentheses** `()`. In between the parentheses you put the things the function needs to do its job. Remember the figure from Chapter 1, where a program takes **input**, does something with it, and gives **output**? A function is exactly that, but then in a small, reusable package.

```Python
string_number = "42"
integer_number = int(string_number)
print(integer_number + 8)  # prints 50
```

Here, `int()` receives the string `"42"` as input, does its magic, and gives the integer `42` back as output. We store that output in the variable `integer_number`, so we can calculate with it.

Somebody else (Python developers) wrote `int()`, `print()` and all the others for you. This week, you will learn to write your own.

## Building your first function
You create, or **define**, a function using the `def` keyword (short for *define*), like so:

```Python
def print_station_header():
    print("==========================")
    print("  Weather station report  ")
    print("==========================")
```

Let's go over it bit by bit:
1. `def` tells Python that you are about to define a function.
2. `print_station_header` is the **name** of the function. The same rules apply as for variable names: letters, numbers and underscores, no spaces, and don't start with a number. Choose a name that describes what the function does.
3. The parentheses `()` come right after the name. They are empty for now, we will fill them in a moment.
4. The colon `:` closes off the first line, just like with `if` statements and loops.
5. All the code that belongs to the function follows at a four-space **indentation**. Back in Chapter 3 we promised you that the indentation rules for `if` statements would come back for **functions**. Here they are!

If you run the code above, you will notice something strange: nothing happens. That's because defining a function is like writing down a recipe. You now have the recipe, but nobody has started cooking yet. To actually run the code inside the function, you have to **call** it. You call a function by writing its name followed by parentheses, just like you do with `print()`:

```Python
print_station_header()
```

And now you will see the header on your screen. The nice thing is that you can call your function as often as you want:

```Python
print_station_header()
print("Delft")
print_station_header()
print("Utrecht")
```
Now copy this code into a python notebook and run the example code yourself.


### Define first, call later
Remember from Chapter 1 that Python reads your code line by line, from top to bottom? That also goes for functions. Python only knows your function after it has read the `def` part. So the example below will give an error, because Python does not know what `print_station_header` is yet when it reaches the first line:

```Python
print_station_header()  # error: Python has never heard of this function

def print_station_header():
    print("==========================")
    print("  Weather station report  ")
    print("==========================")
```

In a Jupyter Notebook this means: run the cell with your function **before** you run the cell in which you call it.

### Exercise
Write a function called `introduce_myself` that prints your name, your study programme and your favourite grand challenge on three separate lines. Call your function three times.

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

## Functions that make decisions
Everything you have learned so far can be used inside a function. Let's start with `if`, `elif` and `else`. Seismologists put earthquakes in classes based on their magnitude, from *micro* (below magnitude 3) all the way up to *great* (magnitude 8 or higher). We can turn that classification into a function:

```Python
def magnitude_class(magnitude):
    if magnitude >= 8:
        return "great"
    elif magnitude >= 7:
        return "major"
    elif magnitude >= 6:
        return "strong"
    elif magnitude >= 5:
        return "moderate"
    elif magnitude >= 4:
        return "light"
    elif magnitude >= 3:
        return "minor"
    else:
        return "micro"

print(magnitude_class(5.8))  # prints moderate
print(magnitude_class(8.2))  # prints great
```

Notice that we never had to check whether the magnitude is also *smaller* than the next class. Python reads the conditions from top to bottom, just like you learned in Chapter 3. If the magnitude were 8 or higher, the function would already have returned `"great"` and stopped. So by the time Python checks `magnitude >= 7`, we know for sure that the magnitude is lower than 8.

Also notice that there are seven `return` statements in this function, but only one of them will ever run.

## Functions and lists
Functions and lists are a great team. Since a parameter can hold any type of variable, it can also hold a list. Inside the function you can then use a `for` loop to go over all the items. For example, to calculate the average rainfall of a week:

```Python
def average(values):
    total = 0
    count = 0
    for value in values:
        total = total + value
        count = count + 1
    return total / count

rainfall_week = [0.0, 2.4, 11.2, 0.0, 5.1, 0.5, 1.8]  # in mm per day
print(average(rainfall_week))  # prints 3.0
```

The real strength of this function is that it doesn't care *which* list you give it. You can reuse it for any list of numbers you have:

```Python
temperatures_week = [4.5, 6.1, 3.2, -1.2, 0.8, 2.0, 5.3]
print(average(temperatures_week))
```

You can also use a function **inside** a loop. That way, the function is called once for every item in your list:

```Python
magnitudes = [4.2, 6.9, 3.1, 7.4, 2.5]

for magnitude in magnitudes:
    print(magnitude, "is a", magnitude_class(magnitude), "earthquake")
```

And a function can also **build** a new list and return it. Below, the function `freezing_temperatures` creates an empty list, loops over all temperatures, and appends only the temperatures below zero. Note that it uses our own `is_freezing` function to do so: functions can call other functions!

```Python
def freezing_temperatures(temperatures):
    cold = []
    for temperature in temperatures:
        if is_freezing(temperature):
            cold.append(temperature)
    return cold

print(freezing_temperatures(temperatures_week))  # prints [-1.2]
```

This is how larger programs are built: small functions that each do one thing well, stacked on top of each other like LEGO bricks.

## What happens in the function, stays in the function
One last thing that often confuses people. Variables that you create **inside** a function only exist inside that function. As soon as the function is done, they are gone. Try to run the following code in your own Jupyter notebook:

```Python
def celsius_to_kelvin(celsius):
    kelvin = celsius + 273.15
    return kelvin

celsius_to_kelvin(4.5)
print(kelvin)  # error: kelvin only existed inside the function
```

Python gives an error, because outside the function there is no variable called `kelvin`. The same goes for the parameter `celsius`. This is actually a good thing: you can use a function without worrying that it will mess up the variables in the rest of your program. And it is exactly why we need `return`: it is the one way to get a value out of the function. So if you want to keep the result, store it:

```Python
kelvin_delft = celsius_to_kelvin(4.5)
print(kelvin_delft)  # prints 277.65
```

## The anatomy of a function
Let's put it all together. Every function you write will look something like this:

```Python
def function_name(parameter_1, parameter_2):  # def, a name, parameters, and a colon
    # the indented code runs every time the function is called
    result = parameter_1 + parameter_2
    return result  # hand the result back to whoever called the function

answer = function_name(3, 4)  # call the function with arguments, and store what it returns
print(answer)  # prints 7
```
