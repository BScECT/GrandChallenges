## Creating figures

In this notebook we will learn how to make figures in Python, using the `matplotlib.pyplot` module. We start by importing the module.

```python
import matplotlib.pyplot as plt
```

Note that we imported the module ```as plt```. The name **plt** is arbitrary, but commonly used. Remember that in this way you only need to add ```plt.``` in front of the function you want to use from the module, for instance ```plt.plot()`.

### Line plot

```python
# create two lists with the data we want to plot
x = [1, 2, 3, 4, 5]
y = [1, 5, 2, 3, 2]

# and now plot the data
plt.plot(x, y)
```

Your first plot! But... it needs axis-labels, and maybe a title? You can do that as follows.

```python
plt.plot(x, y)
plt.xlabel('Time since start of experiment [days]')
plt.ylabel('Daily apple consumption [-]')
plt.title('Experiment #4')
```

```{admonition} Tip
:class: tip
By the way: annoyed by the 'vague' text output above your plot? Then type ```;``` at then end of the very last line (so in this case ```plt.title('Experiment #4');```).
```


### Scatter plot

Another type of plot we often use is a *scatter* plot. Try this:

```python
x  = [  3.7,   3.9,  6.5,  9.5, 13.1, 15.8, 17.9, 17.8, 14.8, 11.1,  7.2,  4.6]
y  = [  3.8,   4.4,  7.2,  9.2, 13.4, 18.6, 22.2, 22.0, 17.7, 12.3,  6.9,  4.3]
plt.scatter(x, y)
plt.xlabel('Mean monthly temperature in The Netherlands [°C]')
plt.ylabel('Mean monthly temperature in Madrid [°C]')
plt.title('Relation between the temperature in two countries')
```

### Histogram

A third type of plot you will use often is a *histogram*. A histogram does not show the values themselves, but how often values occur: it divides your data into intervals (called *bins*) and counts how many values fall into each bin. This tells you how your data is *distributed*.

As an example, take the exam grades of 30 students:

```python
grades = [6.5, 7.2, 5.8, 8.1, 6.9, 7.5, 4.3, 6.1, 7.8, 9.0,
          5.5, 6.7, 7.0, 8.4, 6.3, 5.1, 7.3, 6.8, 7.9, 6.0,
          8.8, 5.9, 6.6, 7.1, 3.8, 7.6, 6.4, 8.2, 7.4, 6.2]

plt.hist(grades)
plt.xlabel('Grade [-]')
plt.ylabel('Number of students [-]')
plt.title('Distribution of exam grades')
```

Note that you only give one list to `plt.hist()`, not an x and a y: Python counts the values for you, and the counts become the heights of the bars.

You can choose the number of bins yourself with the `bins` argument. Adding `edgecolor='black'` draws a line around each bar, which makes them easier to tell apart:

```python
plt.hist(grades, bins=6, edgecolor='black')
plt.xlabel('Grade [-]')
plt.ylabel('Number of students [-]')
plt.title('Distribution of exam grades')
```

### Bar chart

A *bar chart* shows one bar for each item, where the height of the bar is the value of that item. It is useful when you want to compare values between categories, such as days, cities or measurement stations. The x-values can be strings, so you can directly use the names of the categories:

```python
days = ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
rainfall = [0.0, 2.4, 11.2, 0.0, 5.1, 0.5, 1.8]

plt.bar(days, rainfall)
plt.xlabel('Day')
plt.ylabel('Rainfall [mm]')
plt.title('Rainfall per day')
```

Note the difference with a histogram: in a histogram Python counts the values for you, while in a bar chart you give the height of each bar yourself.

You can give all bars the same colour with, for example, `color='green'`. But you can also give `color` a list with a colour for each bar. Here we make the wettest day stand out:

```python
colors = ['grey', 'grey', 'blue', 'grey', 'grey', 'grey', 'grey']

plt.bar(days, rainfall, color=colors)
plt.xlabel('Day')
plt.ylabel('Rainfall [mm]')
plt.title('Rainfall per day')
```

### Multiple graphs, linestyle, legend

We will now show how you can add multiple graphs in the same figure, using the monthly mean temperatures of three countries:

```python
month=range(1,13) # create sequence of numbers from 1 to 12
T_NL      = [  3.7,   3.9,  6.5,  9.5, 13.1, 15.8, 17.9, 17.8, 14.8, 11.1,  7.2,  4.6]
T_Madrid  = [  3.8,   4.4,  7.2,  9.2, 13.4, 18.6, 22.2, 22.0, 17.7, 12.3,  6.9,  4.3]
T_Lapland = [-12.4, -11.4, -6.6, -0.2,  6.3, 12.3, 15.5, 13.0,  7.8,  0.7, -5.8, -9.6] # Sodankylä, Finland
# mean temperature per month, °C, 1990 - 2019
# Data from https://climatecharts.net/
```

And then we create the graphs as follows. Note that adding the ```label = '...'``` is used to create the labels for the legend, which is created in the last line.

```python
plt.plot(month, T_NL, label='Netherlands')
plt.plot(month, T_Madrid, label='Madrid')
plt.plot(month, T_Lapland, label='Lapland')

plt.xlabel('Month')
plt.ylabel('Temperature (°C)')
plt.title('Monthly mean temperature in 3 countries')
plt.legend()
```

There is a lot of documentation on the project homepage https://matplotlib.org. The detailed function description can be quite hard to read, but the examples are helpful.

A good starting point in the matplotlib documentation is the [getting started guide](https://matplotlib.org/stable/users/getting_started/).
Another good resource is the [gallery of plot types](https://matplotlib.org/stable/plot_types/index.html) with example code to create them.

The plot function has additional *optional* arguments, which you can use to choose different line styles, markers, colors, etcetera:

```python
plt.plot(month, T_NL, label='Netherlands', linestyle='--', marker='o', color='blue')
plt.plot(month, T_Madrid, label='Madrid', linestyle=':', marker='s', color='red')
plt.plot(month, T_Lapland, label='Lapland', linestyle='-', marker='^', color='green')

plt.xlabel('Month')
plt.ylabel('Temperature (°C)')
plt.title('Monthly mean temperature')
plt.legend()
```

## Creating a figure with multiple plots

### Subplots

So far we have put all graphs in one figure. Sometimes it is clearer to show each graph in its own panel, next to each other. These panels are called *subplots*. We make them with `plt.subplots()`:

```python
fig, axes = plt.subplots(1, 3, figsize=(12, 4))
```

The first two numbers are the number of rows and columns of subplots, so here we get 1 row with 3 subplots. `figsize` sets the width and height of the whole figure (in inches).

The function gives back two things, and it helps to know the difference:

* `fig` is the **figure**: the whole image, everything you would save as one picture or put in a report as "Figure 1".
* `axes` contains the **plots**: the separate panels inside the figure, each with its own x-axis, y-axis, labels and title. Matplotlib calls each panel an *Axes* (not to be confused with the x- and y-axis lines themselves).

Inside each plot you can then draw one or more **graphs**: the actual lines or points showing your data. So a figure contains plots, and a plot contains graphs.

Because `axes` is a list-like object, you pick a plot by its index: `axes[0]` is the first (left) subplot, `axes[1]` the second, and `axes[2]` the third.

Instead of `plt.plot()`, you now plot *on a specific subplot*, with `axes[0].plot()`. Labels and titles work almost the same, but the function names get `set_` in front: `plt.xlabel()` becomes `axes[0].set_xlabel()`, and `plt.title()` becomes `axes[0].set_title()`.

Let's plot the temperatures of the three countries, each in its own subplot:

```python
fig, axes = plt.subplots(1, 3, figsize=(12, 4))

# first subplot: the Netherlands
axes[0].plot(month, T_NL, color='blue')
axes[0].set_title('Netherlands')
axes[0].set_xlabel('Month')
axes[0].set_ylabel('Temperature (°C)')

# second subplot: Madrid
axes[1].plot(month, T_Madrid, color='red')
axes[1].set_title('Madrid')
axes[1].set_xlabel('Month')
axes[1].set_ylabel('Temperature (°C)')

# third subplot: Lapland
axes[2].plot(month, T_Lapland, color='green')
axes[2].set_title('Lapland')
axes[2].set_xlabel('Month')
axes[2].set_ylabel('Temperature (°C)')

fig.suptitle('Monthly mean temperature')  # title above the whole figure
plt.tight_layout()                        # prevents labels from overlapping
```

Notice the two kinds of titles: `axes[0].set_title()` gives a title to one plot, while `fig.suptitle()` gives a title to the whole figure.

This works, but notice how often we wrote (almost) the same lines! Only the index (`0`, `1`, `2`), the data, the name and the colour change. Imagine doing this for 10 countries... This is exactly what the `for` loop from Chapter 4 is for.

#### Subplots with a `for` loop

First we put everything that changes per subplot in lists. Then we loop over the indices `0`, `1` and `2` with `range()`, and use that index `i` both to pick the subplot and to pick the right item from each list:

```python
temperatures = [T_NL, T_Madrid, T_Lapland]
names  = ['Netherlands', 'Madrid', 'Lapland']
colors = ['blue', 'red', 'green']

fig, axes = plt.subplots(1, 3, figsize=(12, 4))

for i in range(len(names)):   # i becomes 0, 1 and 2
    axes[i].plot(month, temperatures[i], color=colors[i])
    axes[i].set_title(names[i])
    axes[i].set_xlabel('Month')
    axes[i].set_ylabel('Temperature (°C)')

fig.suptitle('Monthly mean temperature')
plt.tight_layout()
```

The result is exactly the same figure, but the code is much shorter. And if you want to add a fourth country, you only add it to the three lists and change the `3` in `plt.subplots(1, 4, ...)`: the loop takes care of the rest.

Note that `temperatures` is a *list of lists*: `temperatures[0]` is the whole list `T_NL`. And `len(names)` is 3, so `range(len(names))` gives us `0, 1, 2`, exactly the indices of our subplots.

```{admonition} Tip: compare subplots fairly
:class: tip
Each subplot gets its own y-axis range by default, which makes it hard to compare the panels. Add `sharey=True` to give all subplots the same y-axis: `plt.subplots(1, 3, figsize=(12, 4), sharey=True)`.
```

```{admonition} Subplots in multiple rows
:class: note
With more than one row, e.g. `plt.subplots(2, 2)`, `axes` becomes a *grid*. You then need two indices, row first and column second: `axes[0, 0]` is the top-left subplot and `axes[1, 0]` the bottom-left one.
```