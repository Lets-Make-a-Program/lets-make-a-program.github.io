# Python - Hello World
## Overview
By the end of this series, you'll have a simple Python script that takes some input and displays it on the screen.

If you've never programmed before, this is the ideal place to start.  We'll jump right in, make a simple program together
and learn about a ton of programming concepts along the way.  The end result won't be very useful, but we'll use the
context of a silly little program to learn the ins and outs of Python.

## Getting Set Up
One of the beauties of Python is that it's a lightweight language that can run without a lot of overhead.  As a result,
you have a few options when it comes to writing Python.  The two basic options are to either A) download and install a
code editor or B) use a website that will interpret your Python code directly in the browser.  There are many possible
options, but the two I would recommend are:

- Use [CodeSkulptor](https://py3.codeskulptor.org/) and write Python in your browser.  You can save your code to a URL
in order to come back to it later or share with others, which is very handy.
- Download and install [Visual Studio Community Edition](https://visualstudio.microsoft.com/vs/community/) from Microsoft.
I program primarily in C#, but VS is free, powerful, and can be used to program in many languages, including Python.
- For a smaller, lighter editor, you could use [Visual Studio Code](https://code.visualstudio.com/).  Like its older,
bigger brother, VS Code can be used to program many different languages.  If you get used to using it for Python, you
can easily add components to program in other languages as well.

## Saying Hello
Once you've got your editor opened and a new Python file opened, clear anything the editor put there by default and type
the following:

```python
print("Hello World!")
```

Congrats - you've just written your first Python script!  Run your code (F5 if you're using Visual Studio, otherwise
look for a big **Run** button) and see what it does.  Easy peasy, right?  Let's see what else we can print.

```python
print("Hello World!")
print("Hi Moon")
print("Hey Sun")
print(1)
print(2.0)
print(3 + 4)
print("3 + 4")
```

Before you run the code above, take a guess at what will happen.  Pay particular attention to the lines with `3 + 4` with
and without quotation marks.  Now run it and see what happens - any surprises?

## Data Types
So why does `print(3 + 4)` show `7` but `print("3 + 4")` displays `3 + 4`?  As you can guess, it's because of the quotes,
but why?  The quotes tell the Python what sort of data to expect.  The same goes for using `2` vs `2.0` - if we include a
decimal, it means we want to treat the number as a `float`, or *floating point decimal* number.  If we include quotes, we
want to treat things as a `string`, or *string of characters* - a word, basically.

Now you may wonder, what happens if we start to mix data types?  Well, let's try it!

```python
print(1 + 2)
print("1" + "2")
print(1 + "2")
```

Run the above and see what happens.  Your output should be `3`, `12`, and an error.  Let's explain each of those.

- `print(1 + 2)` shows `3` because `1` and `2` have no quotes, so Python treats them as numbers.  As you might expect,
putting a `+` between numbers will add them together.
- `print("1" + "2")` shows `12` because it is treating `"1"` and `"2"` as strings.  Try putting something else in the
quotes if you'd like, but *adding* words in Python simply smashes them together.  For example, `"cat" + "dog" = "catdog"`.
- `print(1 + "2")` has an error because you have mixed data types.  Python isn't sure what you want to do.  Do you want
to treat `1` as a string and combine strings together, or do you want to treat `"2"` as a number and add the values?

We can specify what to do for Python by using either the `str()` or `int()` command.  These commands convert whatever value
you feed them (the stuff in the parentheses) to either a string (for `str()`) or an integer (for `int()`).  Try this:

```python
print(str(1) + "2")
print(1 + int("2"))
```

Run this code and see what happens now.  The `str()` and `int()` functions convert the values so that both of the items
are the same data type.  Now Python knows what to do, and no errors happen.

**NOTE**: These functions have their limits.  For example, try putting something like `int("three")` - Python doesn't know
everything, so it won't know that the word `three` has a numeric value.

## Variables
You may be wondering - why would we use `str()` instead of simply putting something in quotes?  Well, quotes work for raw
values, but often we will be dealing with *variables* instead of raw values.  If you've taken algebra, you've seen a
variable before.  In short, a variable takes a value and assigns it a name so you can refer to it later.  For example:

```python
x = 5
print("x")
print(x)
```

Here's what's happening on these 3 lines:

- The first line assigns the value `5` to a new variable named `x`
- The second line has `"x"`, which Python interprets as a string because of the quotes.
- The third line, without the quotes, references the variable `x` you created above.  Rather than printing the letter x,
Python prints the *value* of `x` as defined above - in this case, it prints `5`.

Anywhere you would use raw values like `"cat"` or `4.0` or `100`, you can use a variable instead.  Some examples:

```python
x = 1
y = 2
z = x + y
print(z)
print(10 + z)

dog = "Sparky"
print(dog + " is a good boy!")
```

As you can see, you can create many variables and use them all over the place.  You can use variables to assign values to
other variables (as you can see we did with `z` above), you can mix variables and raw values (like `10 + z`), and you can
pass variables to functions like `print()`.

## Converting Variables

This brings us back around to the idea of changing data types.  Remember that things like `"1" + 2` will break because
Python doesn't know how you want to handle addition of a `string` with an `int`.  The same thing is true with variables.
For example:

```python
x = 1
dog = "Sparky"
print(x + dog)
```

When we get to the `print()` command, we try to add the int variable `x` with the string variable `dog` and Python blows
up.  Before, we fixed this by using `str()` to convert a number to a string, so try that here, like so:

```python
print(str(x) + dog)
```

Now the value of `x` is treated as a string and it can be combined with the value of `dog`.  But what happened to `x`?
Did giving it to the `str()` function change it?  Let's do an experiment:

```python
x = 1
str(x)
print(x + x)
```
Before you run it, think about what will happen.  Will you see the value of `x` added together (i.e.: `2`) or will you see
`x` treated like a string and see it combined (i.e.: `11`)?  The short answer is that - in general - variables only change




## *Stay Tuned!*
I will return to add to this page later and include more concepts, such as:
- Variables
- Conditionals
- Loops
- Lists
- Using and creating functions
- Using and creating classes
- Importing packages