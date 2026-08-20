# Lists, but with names
There is one last type of basic variable type that we haven't yet covered in this course: `dictionaries`. They are similar to lists, in the sense that they store other variables in them, but fundamentally different in the way that they do. As said earlier, a list stores data in a certain order, and you can retrieve that data using its `index`, its number of appearance in the list, like so:
```Python
shopping_list = ["flour", "eggs", "sugar", "butter", "baking powder", "salt"]
print(stuff[2])  # returns sugar
```
A `dictionary`, however, doesn't store values using a numerical `index`, a `dictionary` uses names, or `keys`, instead. You can define a dictionary using curly brackets and colons, like this:
```Python
cake_recipe = {
    "flour": "250 g",
    "eggs": "2 large",
    "sugar": "200 g",
    "butter": "115 g",
    "baking powder": "8 g",
    "salt": "a pinch",
}
print(cake_recipe["eggs"])  # returns 2 large
```
This is a dictionary with `strings` for both the `keys` and `values`. It contains all the ingredients, and amounts for a basic cake. As you can see we don't use a numerical `index` like `0` or `2` to get the values out again. We can use the `keys` we defined when creating the dictionary.

## Dictionaries and loops
Just like lists, we can use dictionaries very effectively in a `for` loop. However, there are two things we could loop over: either the `keys`, or, the `values`. For example, doing it like this, loops over the keys:
```Python
for ingredient in cake_recipe:
    print(ingredient)  # returns flour, eggs, sugar, butter, baking powder, salt. One after the other
```
If you want to loop over the values, however, you can do this like so, using the `values()` method:
```Python
for amount in cake_recipe.values():
    print(amount)  # returns 250 g, 2 large, 200 g, 115 g, 8 g, a pinch. One after the other
```
Or, if you want both you can use the `items()` method of a `dictionary`, which returns both the `key` and `value` as a a pair.
```Python
for ingredient, amount in cake_recipe.items():
    print(ingredient + ": " + amount)  # returns flour: 250 g, eggs: 2 large... etc etc one after the other.
```
Take note on how these three differ slightly from eachother. The devil is in the details when it comes to programming code, the better you get at spotting small differences, the better you will get at programming.