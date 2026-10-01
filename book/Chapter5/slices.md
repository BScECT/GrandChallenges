## Just a slice, please
For more information, read Think Python (3rd ed.) section 9.3 (list slices) and 8.2 (string slices).

Often you don't need a whole list, but only a part of it. Take this list with the temperature of every month of a year, from January to December:

```Python
temperatures_c = [-1, -1.2, 1.3, 6.4, 11.2, 14.8, 17.8, 17.7, 13.7, 8.5, 4.1, 0.9]
```

Say you only want the summer months: June, July and August. With what you know so far, you could pick them one by one using their index:

```Python
summer = [temperatures_c[5], temperatures_c[6], temperatures_c[7]]
```

That works fine for three months. But imagine you have a year of daily measurements and you want the 92 days of summer. That's what a **slice** is for: it takes a whole piece of a list in one go.

### Slicing a list
You write a slice with square brackets, just like an index, but now with two numbers separated by a colon `:`. The first number is where the slice starts, the second where it stops:

```Python
summer = temperatures_c[5:8]
print(summer)  # prints [14.8, 17.8, 17.7]
```

To see which index belongs to which month, it helps to write them out:

```
index:   0     1     2     3     4     5     6     7     8     9    10    11
month:  Jan   Feb   Mar   Apr   May   Jun   Jul   Aug   Sep   Oct   Nov   Dec
```

Wait a minute. Index `8` is September, and September is not in our slice! That's because a slice stops just **before** the stop index. This is the same rule as for `range()`: `range(5, 8)` also gives you `5`, `6` and `7`, but not `8`. A handy trick: stop minus start is the number of items you get. So `8 - 5 = 3` months.

### Leaving out the start or the stop
If you leave out the start, the slice starts at the beginning of the list. If you leave out the stop, the slice continues to the end of the list:

```Python
first_half = temperatures_c[:6]   # January up to and including June
second_half = temperatures_c[6:]  # July up to and including December
```

And just like with a normal index, you can count from the end using negative numbers:

```Python
last_three = temperatures_c[-3:]
print(last_three)  # prints [8.5, 4.1, 0.9]
```

### Taking steps
You can add a third number to a slice: the step. The slice then takes every so-many items:

```Python
every_other_month = temperatures_c[::2]
print(every_other_month)  # prints [-1, 1.3, 11.2, 17.8, 13.7, 4.1]
```

### A slice is a new list
A slice gives you a **new** list, the original list stays exactly the same. That means you can do anything with a slice that you can do with a list: store it in a variable, loop over it, or give it to a function. For example, to the `mean()` function from the built-in NumPy module:

```Python
import numpy as np

print(np.mean(temperatures_c[:6]))  # prints 5.25
print(np.mean(temperatures_c[6:]))  # prints about 10.45
```

So the second half of the year was quite a bit warmer than the first half.

Note that by adding `as np` in the import statement, we can just use `np.` to call functions from this module, and don't need to type out `numpy.` every time.

What about winter? December, January and February are at the end *and* at the beginning of the list, so one slice won't do. But just like strings, you can glue lists together using `+`:

```Python
winter = temperatures_c[-1:] + temperatures_c[:2]
print(winter)  # prints [0.9, -1, -1.2]
```

### Slicing strings
A string is a *string of characters*, remember? That means you can slice strings too, which comes in handy when you work with dates:

```Python
date = "2026-09-29"
year = date[:4]
month = date[5:7]
print(year, month)  # prints 2026 09
```