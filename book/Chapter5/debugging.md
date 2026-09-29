## When things go wrong: Debugging

By now you have written quite a few lines of code yourself. And chances are that a good number of them did not work the first time. Don't worry: that happens to everyone, also to programmers who have been doing this for 30 years. A mistake in a program is called a **bug**, and finding and fixing bugs is called **debugging**. For more information, read Think Python (3rd ed.) section 2.9.

The word *bug* is older than computers, but it got famous in 1947. Engineers at Harvard University found a moth stuck inside their Mark II computer. They taped it into their logbook with the note "first actual case of bug being found". That logbook is now in a museum. Your bugs will usually be less literal.

## Three kinds of errors
There are three kinds of errors you will run into. It helps to recognise them, because each kind asks for a different approach.

### 1. Syntax errors: Python doesn't understand you
Just like a language has grammar, Python has rules for how code should be written. This is called **syntax**. Break one of those rules, and Python doesn't understand what you mean. Think of a missing colon `:` after an `if` statement, a parenthesis `(` that is never closed, or an operator that doesn't exist:

```Python
print("Message before")
result = 2 *** 3
print("Message after")
```

Run this, and Python gives you a `SyntaxError`. Note that *nothing* gets printed, not even `Message before`. Python first checks the grammar of all your code, and if there is a syntax error anywhere, it doesn't run a single line.

Luckily, Python usually tells you quite precisely what is wrong. Forget the colon, like this:

```Python
temperature = -3.0
if temperature < 0
    print("It is freezing")
```

and Python tells you `SyntaxError: expected ':'` and points at the line where the colon is missing.

Remember from Chapter 3 that indentation is important in Python? Put the colon back, but now forget the four spaces in front of `print()`, and you get an `IndentationError`. That is a special kind of syntax error: Python can't tell which lines belong to the `if` statement.

### 2. Runtime errors: Python understands you, but can't do it
A runtime error only shows up while your code is running. The grammar is fine, but at some point Python is asked to do something that is impossible. At that point, Python stops and gives you an error message. Everything before that line has already been executed:

```Python
temperatures = [4.5, 6.1, 3.2]
print("First temperature:", temperatures[0])
print("Fourth temperature:", temperatures[3])
print("Done")
```

This prints `First temperature: 4.5`, and then stops with `IndexError: list index out of range`. The list only has three items (index `0`, `1` and `2`), so there is no index `3`. The last line, `print("Done")`, is never reached.

You have actually seen a few runtime errors already in this course. Here are the ones you will meet most often:

| Error | What it means | Example |
| :-- | :-- | :-- |
| `NameError` | Python doesn't know this name | A typo in a variable name, calling a function before you defined it, or using a variable that only existed inside a function |
| `TypeError` | This action doesn't work for this type | `"5" + 5`: adding a string and an integer (remember casting from Chapter 2?) |
| `IndexError` | This index doesn't exist in the list | `temperatures[3]` in a list with three items |
| `KeyError` | This key doesn't exist in the dictionary | `cake_recipe["milk"]` when there is no milk in the recipe |
| `ZeroDivisionError` | You divided by zero | `average([])`: an empty list has zero items, so `total / count` divides by zero |

:::{admonition} The line that breaks is not always the line with the mistake
:class: tip
Python tells you on which line it got stuck. But that is not always the line where you made the mistake. Take `average([])` from the table above: Python will point at `return total / count` inside the function. There is nothing wrong with that line, though. The real mistake is that somebody gave the function an empty list. So if the line Python points at looks perfectly fine, ask yourself where the values on that line came from.
:::

### 3. Semantic errors: Python does what you wrote, not what you meant
The sneakiest errors are the ones where Python doesn't complain at all. Your code runs, but the answer is wrong. These are called **semantic errors**, because the *meaning* of your code is not what you intended. For example:

```Python
power = 2^3
print("2 to the power 3 is", power)  # prints 2 to the power 3 is 1
```

In math class you may write $2^3$, but in Python the power operator is `**` (remember the table in Chapter 2?). The `^` sign exists in Python, but it does something completely different. So Python happily calculates something, just not what you wanted. Nobody tells you that the answer is wrong: you have to notice it yourself. That's why it is always a good idea to check whether your results make sense.

## Reading an error message
Error messages can look scary, with lots of red text. But they are trying to help you. Read them like this:
1. **Start at the bottom.** The last line tells you the type of error (like `IndexError`) and a short description of what went wrong.
2. **Then look for the line.** Above that, Python shows the line of code where things went wrong, often with an arrow or `^` markers pointing at the exact spot.
3. **Still no idea?** Copy the last line of the error message and search for it online. You are guaranteed not to be the first person with this error.

## Hunting for bugs
Syntax errors and runtime errors come with an error message that tells you where to look. Semantic errors don't, so you have to go hunting yourself. Take a look at this function, that should calculate the total rainfall of a week:

```Python
def total_rainfall(rainfall):
    total = 0
    for amount in rainfall:
        total = amount
    return total

rainfall_week = [0.0, 2.4, 11.2, 0.0, 5.1, 0.5, 1.8]  # in mm per day
print(total_rainfall(rainfall_week))  # prints 1.8
```

No error message, but `1.8` mm can't be right: on the third day alone it already rained 11.2 mm. Time to go hunting.

### Print what is happening
The simplest and most used debugging trick is to add `print()` statements, so you can see what your code is doing step by step. Let's print the value of `amount` and `total` every time the loop runs:

```Python
def total_rainfall(rainfall):
    total = 0
    for amount in rainfall:
        total = amount
        print("amount:", amount, "total:", total)
    return total
```

Calling the function again now shows:

```
amount: 0.0 total: 0.0
amount: 2.4 total: 2.4
amount: 11.2 total: 11.2
amount: 0.0 total: 0.0
amount: 5.1 total: 5.1
amount: 0.5 total: 0.5
amount: 1.8 total: 1.8
```

Now we can see the problem: `total` is not adding anything up, it just becomes the same as `amount` every time. We forgot to add the new amount to the total we already had:

```Python
def total_rainfall(rainfall):
    total = 0
    for amount in rainfall:
        total = total + amount
    return total

print(total_rainfall(rainfall_week))  # prints 21.0
```

Once your bug is fixed, don't forget to remove the extra `print()` statements again.

### Test with something simple
To notice a semantic error, you need to know what the right answer should be. So test your code with an input that is so simple that you can calculate the answer in your head:

```Python
print(total_rainfall([1, 2, 3]))  # should be 6
```

If that doesn't give `6`, you know for sure something is wrong, and you know exactly what the right answer should have been.

### Explain it to a duck
It sounds silly, but it works surprisingly well: explain your code, line by line, out loud, to somebody else. That can be your neighbour, a TA, or a rubber duck on your desk (programmers really do this, it is called *rubber duck debugging*). Remember from Chapter 1 that Python reads your code one line at a time? When you force yourself to do the same, and say out loud what each line does, you will often hear yourself say something like "and here it adds the amount to the total... oh wait, it doesn't."

:::{admonition} Change one thing at a time
:class: tip
When you are trying to fix a bug, change only one thing, and then run your code again. If you change five things at once and it suddenly works (or breaks even more), you have no idea which change did it.
:::
