# Larger equations

The equations we have shown so far don't need a computer to solve, but python comes in handy when equations become more complicated.

Besides making sure that you use the right operators when writing mathematical functions, it is also important that you pay attention to the order of operators. When not done right, this can cause huge changes in the outcome.

When expressions get longer, the order in which Python evaluates them starts to matter a lot, this is called **operator precedence**. Just like in math class, `**` (power) is evaluated before `*` and `/`, which are evaluated before `+` and `-`. When in doubt (or when your equation gets long), use parentheses `()` to group things and make your intentions explicit, this helps reading your own code and whoever reads your code next.


Therefore, when writing out large equations it is easier to use parentheses or split it into multiple variables. e.g.:

$$
y = x\tan\theta - \frac{1}{2v_0^2}\frac{g x^2}{\cos^2\theta} + y_0
$$

You could split this equation into four distinct variables:

1) var_1 $ = x\tan\theta$
2) var_2 $= \frac{1}{2v_0^2}$
3) var_3 $= \frac{g x^2}{\cos^2\theta}$
4) var_4 $= y_0$

And then re-write it as `y = var_1 - (var_2 * var_3) + var_4`