# Ordering data
Up until now we have been working with a manageable number of variables, a manageable number of datapoints. But the real strength in using programming code is making your computer do something a hundred, a thousand, nay a million times. You don't want to manually input a single datapoint every time you run your code, so we need ways to store more complex data.

You may remember from Week 1 that there are many different variable `types`. We've covered, `strings` and numbers like `integers` and `floats`. Last week we covered `booleans` that can only be either `True` or `False`. This week, we will be looking at two new data types: `lists` and `dictionaries`.

## Everyone loves lists
You must have made a list somewhere this week. Maybe you were going grocery shopping, noting down what homework is coming up, or thinking about all your enemies. Lists are immensely useful to keep track of stuff, and the same goes for data as well. That's why practically any programming language you will ever use has some kind of list implementation, a one-dimensional way of storing data.

First this -> second this -> third this -> then this -> ...

In Python, we would create such a list like this:

```Python
my_list = ["First this", "second this", "third this", "then this", "..."]
```

This is a list of strings. As you can see it has five **items**. Fun to make, but useless if we cannot access the individual items in the list. For this we use the position in the list of the item we want, also called the **index** of the item. Python starts counting at zero (just accept that it does), so if we want the first item of the list we do this:

```Python
first_item = my_list[0]
print(first_item) # returns "First this"
```

And if we want the second, we do this:
```Python
second_item = my_list[1]
print(second_item) # returns "second this"
```

And if we want the third.... I think you got this.

## REASSIGNING
TODO

## Look at all the stuff you can do with lists
When you have lists, the possibilites are endless. Inbuilt functionalities like `len()` or `sort()` will tell you the length of your list or sort your list however you want. You can index your list the other way around using negative numbers, so `list[-1]` gives you it's last item. You can slice a list or stick them together again.

You can even make a lists of lists that functions exactly like a table:
```Python
list_list = [
    ["one", "two", "three"],
    ["four", "five", "six"],
    ["seven", "eight", "nine"],
]
print(list_list[1][1])  # returns "five"
```
*Spoiler: this is how practically any table on a computer actually works*

You don't need to remember all of this, just know that it is possible whenever you face a programming problem that requires it. What you do need to know is what a **loop** is, and how they turn lists from cool, to amazing.