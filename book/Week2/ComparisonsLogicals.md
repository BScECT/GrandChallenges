# Operators in Python


## Comparison operators

Comparison operators let you compare two values and get a Boolean answer of `True` or `False`: `==` checks if two values are equal (note the double equals sign, since a single `=` is reserved for assignment), `!=` checks if they're not equal, and `<`, `>`, `<=`, `>=` compare size. These are especially useful later on when you start writing conditions and loops, since your program can make decisions based on the result.

| Math sign | Python sign | Meaning |
| :-: | :-: | :-: |
| = | `==` | Equal to |
| > | `>` | Greater than |
| < | `<` | Less than |
| ≥ | `>=` | Greater than or equal to |
| ≤ | `<=` | Less than or equal to |
| ≠ | `!=` | Not equal to |


For example:
```python
is_adult = age >= 18       # True, since age is 19
same_name = name == "Sam"  # True
```

Getting comfortable with variables and operators is the foundation for almost everything else in Python, from calculations to decision-making to working with data. So it's worth experimenting with a few examples yourself before moving on.


<br>Python <b>operators</b> are used to perform operations on variables and values. They are symbols that represent a form of computation; think of addition or multiplication. The value to which this computation is applied to is called the <i>'operand'</i>. Most of the common operators you will recognize from mathematics.

#### Checking if a value corresponds to the set conditions

Check if the the variable **`num`** satisfies the set condition.

```python
num = 6
print(num > 2)
```

If the value does not satisfy the condition the system will return <b><code>False</code></b>

```python
print(num > 7)
```

### Logical & Identity Operators
 
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