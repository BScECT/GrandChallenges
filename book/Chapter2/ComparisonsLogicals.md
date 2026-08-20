# Operators in Python


## Comparison operators

# 2.3 Conditions and if statements

In this Section you will learn how to control the flow of your code — process data differently based on some conditions. For that you will learn a construction called the **`if`** statement.

## `if` keyword

The **`if`** statement in Python is similar to how we use it in English. *"If I have apples, I will make an apple pie"* — clearly states that an apple pie will exist under the condition of you having apples. Otherwise, no pie.

Well, it is the same in Python:

````python
amount_of_apples = 0

if amount_of_apples > 0:
    print("You have apples!\nLet's make a pie!")

print('End of the cell block...')
````

As you can see - nothing is printed besides *'End of the cell block...'*.

But we can clearly see that there is another print statement! Why it is not printed? Because we have no apples... thus no pie for you.

Let's acquire some fruit and see whether something will change...

````python
# adding 5 apples to our supply

amount_of_apples += 5

if amount_of_apples > 0:
    print("You have apples!\nLet's make a pie!") 

print('End of the cell block...')
````

Now you can see that the same **`if`** statement prints text. It happened because our statement **`amount_of_apples > 0`** is now **`True`**.

That's how an **`if`** statement works — you type the **`if`** keyword, a statement and a colon. Beneath it, with an indentation of 4 spaces (1 tab), you place any code you want to run in case that **`if`** statement is **`True`**. This indentation is the same as described in Notebook 1 when defining a function.

If the result of the conditional expression is **`False`**, then the code inside of the **`if`** statement block will not run. Here's another example:

````python
my_age = 25

if my_age >= 18 and my_age <= 65:
    print("I'm an adult, I have to work right now :(")

print('End of the cell block...')
````

Slightly different setting but still the same construction. As you can see in this case, the condition of the **`if`** statement is more complicated than the previous one. It combines two smaller conditions by using the keyword **`and`**. Only if both conditions are **`True`** the final result is **`True`** (otherwise it would be **`False`**).

> **⚠️ Attention**
> 
> The condition can be as long and as complicated as you want it to be, just make sure that it is readable.

## `elif` keyword

Now, let's add a bit more logic to our last example:

````python
my_age = 25

if my_age >= 18 and my_age <= 65:
    print("I'm an adult, I have to work right now :(")
elif my_age > 65:
    print("I can finally retire!")

print('End of the cell block...')
````

Still the same output, but what if we change our age...

````python
my_age = 66

if my_age >= 18 and my_age <= 65:
    print("I'm an adult, I have to work right now :(") # msg #1
elif my_age > 65:
    print("I can finally retire!") # msg #2

print('End of the cell block...')
````

See.. we have a different output. Changing the value of our variable **`my_age`** changed the output of the **`if`** statement. Furthermore, the **`elif`** keyword helped us to add more logic to our code.

`elif` is short for *else if*. Now, we have three different output scenarios:

- print message #1 if **`my_age`** is within the [18, 65] range
- print message #2 if **`my_age`** is bigger than 65
- print none of them if **`my_age`** doesn't comply with any of the conditions (as shown below)

````python
my_age = 15

if my_age >= 18 and my_age <= 65:
    print("I'm an adult, I have to work right now :(") # msg #1
elif my_age > 65:
    print("I can finally retire!") # msg #2

print('End of the cell block...')
````

One can also substitute an `elif` block by a different `if` block, however it is preferred to use `elif` instead for two reasons:

- to *"keep the condition together"* and to reduce code size
- in case two or more of the `if`/`elif` statements are met, *only* the first one that is met will run (when using only `if`, *all* statements that are met will run)

It is important to know that there should be only **one** `if` block and **any number of** `elif` blocks within it.

A last example below:

````python
# Setting my_age to run the first elif block
my_age = 88

if my_age >= 18 and my_age <= 65:
    print("I'm an adult, I have to work right now :(")
elif my_age > 65:
    print("I can finally retire!")
elif my_age < 10:
    print("I'm really, really young")

# Setting my_age to run the second elif block
my_age = 7

if my_age >= 18 and my_age <= 65:
    print("I'm an adult, I have to work right now :(")
elif my_age > 65:
    print("I can finally retire!")
elif my_age < 10:
    print("I'm really really young")

print('End of the cell block...')
````

## `else` keyword

We can go even further and add an additional scenario to our **`if`** statement with the **`else`** keyword. It runs the code inside of it **only** when none of the **`if`** and **`elif`** conditions are **`True`**:

````python
my_age = 13

if my_age >= 18 and my_age <= 65:
    print("I'm an adult, I have to work right now :(")
elif my_age > 65:
    print("I can finally retire!")
elif my_age < 10:
    print("I'm really really young")
else:
    print("I'm just young")

print('End of the cell block...')
````

On the previous example, since **`my_age`** is **not** between [18,65], **nor** bigger than 65, **nor** smaller than 10, the **`else`** block is run.

Below, a final comprehensive example:

````python
# Setting age to run the if block
my_age = 27

if my_age >= 18 and my_age <= 65:
    print("I'm an adult, I have to work right now :(")
elif my_age > 65:
    print("I can finally retire!")
elif my_age < 10:
    print("I'm really really young")
else:
    print("I'm just young")

print('End of the cell block...')
print('------------------------')

# Setting age to run the first elif block
my_age = 71

if my_age >= 18 and my_age <= 65:
    print("I'm an adult, I have to work right now :(")
elif my_age > 65: # first elif block
    print("I can finally retire!")
elif my_age < 10:
    print("I'm really really young")
else:
    print("I'm just young")

print('End of the cell block...')
print('------------------------')

# Setting age to run the second elif block
my_age = 9

if my_age >= 18 and my_age <= 65:
    print("I'm an adult, I have to work right now :(")
elif my_age > 65:
    print("I can finally retire!")
elif my_age < 10: # second elif block
    print("I'm really really young")
else:
    print("I'm just young")

print('End of the cell block...')
print('------------------------')

# Setting age to run the else block
my_age = 13

if my_age >= 18 and my_age <= 65:
    print("I'm an adult, I have to work right now :(")
elif my_age > 65:
    print("I can finally retire!")
elif my_age < 10:
    print("I'm really really young")
else: # else block
    print("I'm just young")

print('End of the cell block...')
print('------------------------')
````

## Key Points About if Statements

That's almost everything you have to know about **`if`** statements! The last two important things are:

### 1. Top-to-Bottom Execution

It goes from top to bottom. When the first condition to be **`True`** runs, it skips all conditions after it:

````python
random_number = 17

if random_number > 35:
    print('Condition #1')
elif random_number > 25:
    print('Condition #2')
elif random_number > 15:
    print('Condition #3')
elif random_number > 5:
    print('Condition #4')
else:
    print('Condition #5')
````

### 2. Nested Conditions and Variable Scope

You can put almost everything inside each condition block and you can define variables within each block:

````python
my_income = 150
my_degree = 'BSc'

if my_degree == 'BSc':
    x = 5
    if my_income > 300:
        b = 2
        print('I am a rich BSc student')
    else:
        print('I am a poor BSc student')

elif my_degree == 'MSc':

    if my_income > 300:
        print('I am a rich MSc student')
    else:
        print('I am a poor MSc student')

print('x =', x)
print('b =', b)
````

As you can see, we can make it as complicated as we want in terms of conditional branching. Additionally, note that only variables within the blocks which run were created, while other variables were not. Thus, we have a *NameError* when we try to access a variable **`(b)`** that was not defined.

## Comparison Operators

For your easy reference, below are the comparison operators used for comparing numbers:

| Operator | Description |
|----------|-------------|
| `a == b` | a is equal to b |
| `a > b` | a is larger than b |
| `a < b` | a is smaller than b |
| `a >= b` | a is larger than or equal to b |
| `a <= b` | a is smaller than or equal to b |
| `a != b` | a is not equal to b |

> **⚠️ Attention**
> 
> There is a major difference between `=` and `==`. `a = 1` assigns the number 1 to variable `a`. `a == 1` tests if the variable `a` is equal to 1, and will return `True` or `False` (for use in `if` statements).

## Additional Resources

- [Official Python Documentation - Control Flow](https://docs.python.org/3/tutorial/controlflow.html)
- Think Python (2nd ed.) - Chapter 5

# Logical & Identity Operators
 
 |sign|description|
 |:-:|:-:|
 |and|returns True if both statements are true|
 |or|return True if at least 1 statements is true|
 |not|reverse of the results; returns False if the statement is True|
 |in|returns True if a sequence with the specified value is present in the object|
 |not in|returns True if a sequence with the specified value is not present in the object|

 #### <b><code>and</code></b> statement

By using the <b><code>and</code></b> statement you can set multiple conditions for the system to return. This can be seen as setting a boundary condition for a mathematical function.

```python
num = 5
print(num > 4 and num < 8)
```



Now download the exercise to your course folder and open the file in python jupyter notebook. Show the exercise to a teaching assistant to check your work.