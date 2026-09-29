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



