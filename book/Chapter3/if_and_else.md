# What if...
One of the main ways to change the flow of you programme is by using **conditions**: executing some code only if something is `True`. We can do that using an **if..else** construction. For this, we will cover the following basic Python **keywords**:
* `if`
* `else`
* `elif`

## If this, then that
You can use the `if` statement followed by a **boolean** as a gatekeeper to some code. Only if the **boolean** is `True` the code that follows the `if` statement will be executed:
```Python
if True:
    print("This will always be printed")
```
We use the keyword `if` to show that we are using an if statement. This is then followed by a **condition** in this case `True` and closed of by a colon `:`. After this the code that will execute if the conditions are met follows at a four-space indentation.

## What else
An `if` statement like this, works perfectly fine on it's own. There will however be cases that you want something to happen in the opposite condition as well. For that, there is the `else` statement:
```Python
number = 10
if number > 20:
    # This happens only when the number is higher than 20
    print("That's a large number!")
else:
    # This happens only when the number is 20 or lower
    print("Look at that tiny *$&*# number")
```

## What if else?
One final `if` statement remains: `elif`. With `elif` (think *else if*) you can chain multiple `if` statements together for more complex conditional operations, like so:
```Python
number = 10
if number > 20:
    # This happens only when the number is higher than 20
    print("That's a large number!")

elif number < 10:
    # This happens only when the number is smaller than 10 and not higher than 20
    print("Look at that tiny *$&*# number")

else:
    # This happens only when the number is between 10 and 20
    print("Just perfect")
```

## Indentation is important
As you can see, all these different codeblocks are indented. This is important because it's how Python knows code belongs together. Any code that doesn't have the four spaces anymore is not part of a block. Learn to read the code like this, because the same principle goes for **loops**, **functions** and **classes**, too (we will get to them later).

```Python
number = input("Pick a number, any number: ")

if number == "5":
    print("Your number is 5!")  # only returned when the number is "5"
    print("I am the best magician")  # still the same block, so also returned when the number is "5"

    print("My life is complete")  # Even with an empty line in between, it's still the same block

print("I quit")  # always returned, because it's not part of the block anymore
```
This would be a lot of work to do manually, so you will notice that your code editor of choice, or Jupyter notebooks, do this for you automatically. If you do get lost, use the tab-key to help you out.