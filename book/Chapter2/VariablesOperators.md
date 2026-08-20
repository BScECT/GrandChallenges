# Variables and operators
In this chapter you will learn about variables, operators and conditions. All the information about these topics van be found in Think Python (2nd ed.) - Section 2 and 5. 

Once you have gone through the chapter, right-click and select "Save Link As" to download the exercise: [Download the exercise notebook](https://raw.githubusercontent.com/BScECT/GrandChallenges/main/Exercises/Exercise_chapter2.ipynb). Then open the exercise in Jupyter notebook that you can access via anaconda and do the exercise.

## Creating a variable

When you want to compute something, you often need to store a piece of information so you can use it later, for example a number, a name, a result of a calculation. In Python, you do this with a **variable**. Think of a variable as a labeled box: you give it a name, and you put a value inside it.

```python
age = 19
name = "Sam"
gpa = 7.8
```

Here, `age`, `name`, and `gpa` are variables. The `=` sign doesn't mean "equals" like in math, it means "assign this value to this name." So `age = 19` reads as "store 19 in a box called age." You can change what's in the box at any time by assigning it a new value, and Python will always use the most recent one.

Variable names in Python can contain letters, numbers, and underscores, but can't start with a number, and can't contain spaces (use `first_name`, not `first name`). Python is also case-sensitive, so `Age` and `age` are treated as two different variables. It's good practice to give variables names that describe what they hold, so your code stays readable.

Now let's create a variable called "a" and assign it the number 5

```python
a = 5
```

No output will be printed to the screen when you clicked on 'Run', because there was no print statement. The print statement will be added later.

Now if I use `a` in my Python scripts below, Python will treat it as the number $5$.

## Arithmetic operators

Once you have variables, operators let you do things with them. 

Arithmetic operators work on numbers the way you'd expect from math class: `+` for addition, `-` for subtraction, `*` for multiplication, and `/` for division. Python also has a few extras that are useful in programming: `**` for exponents (`2 ** 3` gives `8`), `%` for the remainder after division (`7 % 2` gives `1`), and `//` for division that rounds down to a whole number (`7 // 2` gives `3`).

| Math sign | Python sign | name |
| :-: | :-: |:-:|
| + | + | addition |
| - | - | subtraction |
| * | * | multiplication |
| / | / | division |
| ^ | ** | exponentiation |

For example:
```python
total = 5 + 3      # 8
product = 4 * 2    # 8
remainder = 7 % 2  # 1
```

<br>Most of the mathematical symbols stay the same when transforming a piece of mathematics to Python. Note that the exponentiation sign is a double multiplication sign!<br><br>

Now we can perform operations with this variable. For example, we can add it to itself:
```python
# Adding variables
b = a + a
```

You can now check the value of "b" by printing it:
```python
# Check b
print(b)
```

What happens on reassignment? Will Python let us write over it and compute b with the new value of a?
```python
# Reassignment
a = 20
print(b)
```

Yes! Python allows you to overwrite assigned variable names. We can also use the variables themselves when doing the reassignment. Since <b><code>a = 20</code></b> was the last assignment to our variable <b><code>a</code></b>, you can keep using <b><code>a</code></b> in place of the number <b><code>20</code></b>:

```python
a = a + 5
print(a)
```


## Larger equations
Besides making sure that you use the right operators when writing mathematical functions, it is also important that you pay attention to the order of operators. When not done right, this can cause huge changes in the outcome. Therefore, when writing out large equations it is easier to use parentheses or split it into multiple variables. e.g.:

$$
y = x\tan\theta - \frac{1}{2v_0^2}\frac{g x^2}{\cos^2\theta} + y_0
$$

You could split this equation into four distinct variables:


1) var_1 $ = x\tan\theta$

2) var_2 $= \frac{1}{2v_0^2}$

3) var_3 $= \frac{g x^2}{\cos^2\theta}$

4) var_4 $= y_0$

And then re-write it as <code>y = var_1 - (var_2 * var_3) + var_4</code>

