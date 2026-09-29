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
