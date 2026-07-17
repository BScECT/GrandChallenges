# From input to output 
So now we now what this does:
```Python
print("Hello World")
```
Printing "Hello World" is the start of almost every programmer's journey. It is a staple in the programming community. It is also, **very boring**.

In essence, this program does nothing. It runs, outputs something, and then exits. If you want to do something interesting, we have to give a program something to work with. We have to give it some **input**.

## What is input
Input is the stuff you want your program to react to, to do something with. On your phone you provide input to an app by clicking on a button, writing some text using the keyboard. Even scrolling down a screan is input.

In **Python** we mostly work with data input:
- Text that was put in by the user
- A file that has a million different numbers
- An image of your favourite teacher

A typical program takes this input, does what you want, and then returns the output.

![Demo hello world](../figures/Week1/input_output_image.png)

## Variables
The whole point of input, is that it may be different every time you run your program. We need a place to store it so we can refer to it at a later time. This is what **variables** are for.

**Variables** are named datapoints that may be different every time. In Python you can create, or **assign**, a variable using the `=` sign, like so:

```Python
hello = "Hello World"
print(hello)
```
This code has created a **variable** called `hello` and assigned the value `"Hello World"` to it. Afterwards I can use that **variable** to return "Hello World" using `print()`.

## Simple input
Now that we know how to store input, we can ask for input in our program. Instead of the boring "Hello World", we can now create a program that says Hello, followed by your name.

```Python
name = input("What is your name? ")
print("Hello")
print(name)
```
`input()` asks the user to put in their name using their keyboard, and then stores the answer in the **variable** called `name`. After that we can return "Hello" and their name back to the user!
