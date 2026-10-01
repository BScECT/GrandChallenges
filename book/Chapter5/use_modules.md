## Python Modules

Python only has a couple of built-in functions that can be useful for you, such as <b><code>abs()</code></b>, <b><code>int()</code></b> and <b><code>print()</code></b>. The input of the function always needs to be specified between the `()`.

However, there are way more functions that can be useful, and fortunately are available via so-called Python *modules*. A module is a code library, with a set of functions for a specific purpose. Some examples we will use in this chapter are:

* the **math** module which has many mathematical functions and constants,
* the **numpy** module for numerical computing, and which can handle arrays and matrices,
* the **matplotlib** module for plotting.

We will demonstrate how you can import and use the functions in a module below.

### math

The <code>math</code> module is one of the most popular modules since it contains all implementations of basic math functions ($\sin$, $\cos$, $\log_{10}$ (as log10), factorial, etc — the full list can be found <a href="https://docs.python.org/3/library/math.html">here</a>). 

In order to access it, you just have to import it into your code with an <b><code>import</code></b> statement.

Then you can use its functions as shown below for the square root.

```Python
# importing all contents of the module math
import math

print(f'Square root of 16 is equal to {math.sqrt(16)}')
```

Note that in order to access the function, you first need to type the module's name (in this case <b><code>math</code></b>) and a <b><code>.</code></b> followed by the name of the function (in this case <b><code>sqrt</code></b>).

You can also use the constants defined within the module, such as **`math.pi`**:

```Python
print(f'π is equal to {math.pi}')

print(f"and Euler's number e is {math.e}")
```

We are able to do this since we have loaded all contents of the module by using the <b><code>import</code></b> keyword. If we try to use these functions somehow differently — we will get an error:

```Python
print('Square root of 16 is equal to')
print(sqrt(16))
```

You could, however, directly specify the functionality of the module you want to access. Then, the above cell would work.

This is done by typing: <code>from <b>module_name</b> import <b>the_function_I_need</b></code>, as shown below:

```Python
from math import sqrt

print(f'Square root of 16 is equal to {sqrt(16)}.')

from math import pi

print(f'π is equal to {pi}.')
```

This can be convenient if you know you only need this specific function or constant from the module, but otherwise, it is easier to import the complete module to avoid you have to type in the `from math import ...` everytime. The price to pay is that you have to use the prefix `math.` every time you call a function or constant.

### Listing all functions of a module and documentation

Sometimes, when you use a module for the first time, you may have no clue about the functions inside of it. In order to unveil all the potential a module has to offer, you can either access the documentation on the corresponding web resource or you can use some Python code, as shown below:

```Python
import math

# listing all contents of a module
print('contents of math:', dir(math))
```

If you want to know what a function is for, you can read the documentation as follows:

```Python
math.exp?
```

```{admonition} Additional study material
:class: tip
* Official Python Documentation - https://docs.python.org/3/tutorial/modules.html
* Think Python (3rd ed.) - Chapters 3 and 14 
+++
```

