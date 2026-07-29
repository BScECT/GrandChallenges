# Loops and iteration
Sometimes, and by sometimes I mean most of the times, you want your code to do something multiple or even many times. Much of the strength of using programming code is using the speed of your computer to do a task a thousand times over. Looping over the same section of code many times is therefore a fundamental skill to learn. In Python, and actually most other programming languages, there are two main types of loops:
- `while` loops
- `for` loops

## While the roses are red, and the sky is blue
`while` loops continuously execute the indented code while their condition is `True`. They are pretty similar to the `if` statements of last week, only they continue to keep running in circles. The simplest `while` loop looks like this:

```Python
while True:
    print("I am stuck")
```

You could execute the above code, and it would start spitting out `I am stuck`, `I am stuck`, `I am stuck`, `I am stuck`, `I am stuck`, `I am stuck`, `I am stuck`, `I am stuck`, `I am stuck`, `I am stuck` until infinity.
It would keep running forever (or until your laptop runs out of power), because `True` will always be `True`. This may be useful in some instances, but in almost all practical cases you will want to exit the loop at some point. For example, like this:

```Python
freed = "no"

while freed != "yes":
    print("I am stuck")
    freed = input("Free me? (yes/no)")

print("Thank you")
```

This code will keep asking you to please free it from its hellish cycle until you benevolently break it free by answering `yes`.


## For every cookie in the jar
While, `while` loops know their uses, there's a second type of loop that you will be using more in practice: the so-called `for` loop. In a `for` loop you cycle, or **iterate**, one by one over the contents of a list or list-like object (**iterator** would be the technical term, but you can forget that).

Okay, difficult to explain, but easy to demonstrate:
```Python
my_list = ["one", "two", "three"]

for item in my_list:
    print(item)
```
I have a list with three items, namely the strings `one`, `two`, and `three`. My `for` loop takes that list and **assigns** each of these strings in turn to the `item` variable. So my program prints first `one`, than `two`, and finally `three`. After that, there are no more items in the list, so the for loop exits.

A `for` loop is also the most common way to make your programming code do something a specific numer of times when combined with the `range()` function. `range()` returns a list-like object containing numbers within a certain range, like so:
```Python
range_of_5 = range(5)
print(list(range_of_5))  # returns [0, 1, 2, 3, 4]
```
If we combine that with a `for` loop, we can make the loop run a specific number of times:
```Python
for i in range(10):
    print("This code will run 10 times")
```

## Breaking the cycle
One last thing to know about loops, is how to break them. Right now you know two ways in which loops end: 
- In a `while` loop, the loop ends when it's condition is no longer `True` but `False`.
- In a `for` loop, the loop ends when the last item in the list-like has been processed.

But there is another, third way, and that's by using the `break` keyword. Whenever Python encounters the `break` keyword in a loop, it will break out of the loop and continue the rest of the code. Like this:
```Python
while True:
    answer = input("Are you a good programmer? (yes/no)")
    if answer == "yes" or answer == "absolutely":
        break
```
This loop will repeatedly ask the question whether you are a good programmer. Unless you answer `yes` or `absolutely`, the program will stay in this loop. If you do answer truthfully, however, the program will `break` and finish.