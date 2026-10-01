## Creating figures

In this notebook we will learn how to make figures in Python, using the `matplotlib.pyplot` module. We start by importing the module.

```python
import matplotlib.pyplot as plt
```

Note that we imported the module ```as plt```. The name **plt** is arbitrary, but commonly used. Remember that in this way you only need to add ```plt.``` in front of the function you want to use from the module, for instance ```plt.plot()`.

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

By the way: annoyed by the 'vague' text output above your plot? Then type ```;``` at then end of the very last line (so in this case ```plt.title('Experiment #4');```).

### Multiple plots, linestyle, legend

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

