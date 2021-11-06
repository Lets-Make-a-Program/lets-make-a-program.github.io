# C# - Hello World
## Overview
By the end of this series, you'll have a simple console program that takes some input and displays it on the screen.

If you've never programmed before, this is the ideal place to start.  We'll jump right in, make a simple program together
and learn about a ton of programming concepts along the way.  The end result won't be very useful, but we'll use the
context of a silly little program to learn the ins and outs of C#.

## Getting Set Up
First thing's first, you've got to get the tools to write code.  The code you write can't be run by the computer - it's
just text - so you need a program that *compiles* your human-readable code into a form that can be executed by the computer.

Luckily, Microsoft *really* wants people to use their tools, so there is a free-to-use version of their flagship code 
editor, Visual Studio.  Before we do anything else, go download [Visual Studio Community Edition](https://visualstudio.microsoft.com/vs/community/)
and run the installer.  Visual Studio can let you write code in many different languages, so make sure that you pick the
C# development tools when you run the installer.  The rest can be added later as the need arises, so don't worry too much
about the other components available in the installer.

## Creating a Project
Open your freshly-installed Visual Studio and you'll be presented a screen with several options.  If you didn't already 
guess it, you want to click *Create a new project*.  Depending on what you selected during the installation, you may have
a ton of available project types.  Look for the one called *Console Application* and make sure it has the C# label below it.
***HINT***: Use the search bar at the top, or click "Console" from the **Project Types** dropdown.  Name your project
**HelloWorld** and leave the rest of the defaults the same.

## Making sure it runs
At this point, Visual Studio should have created a new project with a few files in it and opened up to a screen with some
code that looks something like this:

```csharp
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
```

If you're new to programming, this probably looks like gibberish, so let's see what it does!  Run the program by either

* Hitting F5 on your keyboard
* Going to *Debug -> Start Debugging* in top menu
* Clicking the play icon with the words `HelloWorld` (or whatever you named your project) next to it

So what happened?  You should have seen a console window pop up with the phrase "Hello World!" in it.  Let's play with 
what's going on and make it say a few other things.  Copy the line that says `Console.WriteLine` and paste it a few more
times but change what's in the quotes.  Let's make our program countdown from 3 before saying hello.  You should end up
with something like this:

```csharp
static void Main(string[] args)
{
    Console.WriteLine("3!");
    Console.WriteLine("2!");
    Console.WriteLine("1!");
    Console.WriteLine("Hello World!");
}
```

Hit F5 again and watch what happens this time.  Now that console should show all those `WriteLine` messages, one at a time,
in your console window.  This is essentially what all programs are - a series of instructions that the computer executes,
one at a time.  The `static void Main(string[] args)` part of that code file tells the computer where to start, and it 
goes from top to bottom at that point, doing whatever you tell it to.

## Variables

A program that does the same thing every time is boring.  Let's add some user interactivity by saying hello to the user
instead of the entire world.  First, let's make a variable where we will store our user's name.  Above your `WriteLine`
statements, put `string name = "Your Name";`.  What this does is:
- Sets the type of the variable to `string` (i.e.: a **string** of letters/characters, like a word or sentence)
- Gives the variable the name `name`.  You can name your variables whatever you want, but you should try to use names
that make sense.  I called this `name` because it will store somebody's name.  Makes sense, right?
- Sets the value of the variable to `Your Name`.  Because it's a `string`, you have to wrap that text in quotes so VS
knows where it starts and stops.
- Ends the line with a `;`.

A fun note about that last part: starting a new line isn't what lets C# know that a command is done.  The `;` is what
does that.  This means you can put multiple commands on one line, such as 
`Console.WriteLine("Hello"); Console.WriteLine("Hello again")` or you can do something awful like this:

```csharp
string
    name
        =
            "Your Name"
                ;
```

and it's perfectly valid.  Ugly and terrible, but valid.  On that note, be mindful to include a semicolon at the end
of your lines.  Tons of early programming mistakes stem from accidentally deleting some punction.  To see what happens,
remove the semicolon at the end of one of your `Console.WriteLine` statements and hit F5 to see what happens.

You should see a few things:
- A window popped up saying `There were build errors`.  You can click *No* to go back to your code
- The line after the semicolon you removed should have a red squiggly line to alert you that something is wrong
- By default, VS includes an *Error List* window at the bottom of the screen.  You should see an error there saying
`; expected`.  Put that semicolon back to resolve the error.

Alright, now that we have our name variable, let's use it.  Change the `"Hello World"` message to just say hello and 
add yet another `WriteLine` command that gives your variable name.  Hit F5 and see what happens.

Did it write `name` to the console, or did it write `Your Name` (or whatever you put for the variable)?  If you see
`name` instead of the variable's value, that's because you put the variable's name in quotes.  Your commands should look
like this:

```csharp
Console.WriteLine("Hello");
Console.WriteLine(name);
Console.WriteLine("!");
```

The quotes around `"Hello"` let VS know it's a string, so the contents are not treated like code.  `name` is a code 
reference to the variable you defined further up in the code, so it does not need quotes.  Now, in your console you
probably saw that the output is a little bit clunky.  We don't want the name on a new line, we want it together with
the word *Hello*, right?

Great news, because if you "add" strings together, C# combines them.  So try doing this:

```csharp
Console.WriteLine("Hello " + name + "!");
```

Hit F5 and watch it go.  Now you've got your name on the same line as *Hello World* and the exclamation mark.

## User Input

Our program still requires a programmer to change the variable to change the message.  Let's face it - most end users
aren't going to alter your code, so we need a better way to take a user's name.  We've already used a command that
writes to the console, now let's use a command that *reads* from the console.  Where you defined name, change that
line to:

```csharp
string name = Console.ReadLine();
```

This line does the same thing as before, but now it takes whatever input a user entered and assigns that to the variable
`name`.  Run the program and see what happens.  Keep in mind, it'll expect you to type something in and hit enter.

It's a little strange that it doesn't display a prompt, isn't it?  Let's add one in by adding a new `WriteLine` command
above out `ReadLine` command, so we have something like the following:

```csharp
Console.WriteLine("Enter your name");
string name = Console.ReadLine();
```

Hit F5 and check it out.  Wouldn't it be great if the prompt was on the same line as the user input, though?  Try changing
the `WriteLine` command to `Write` instead and add a space at the end of the prompt.  Hit F5 and see - it looks better,
doesn't it?

## Loops

Right now, our program counts down from 3.  What if we wanted it to count down from 5?  Easy, right?  Just cook up some
copy pasta and you wind up with:

```csharp
static void Main(string[] args)
{
    Console.Write("Enter your name: ");
    string name = Console.ReadLine();

    Console.WriteLine("5!");
    Console.WriteLine("4!");
    Console.WriteLine("3!");
    Console.WriteLine("2!");
    Console.WriteLine("1!");
    Console.WriteLine("Hello " + name + "!");
}
```

But what if we wanted to count down from 10?  What about 100?  Suddenly copy/paste doesn't seem like a good idea.
Instead, we'll use a *loop*.

Earlier, I said that a program is just a series of commands.  Sometimes, we want to make the same (or almost the same)
command repeatedly.  A *loop* tells the program to keep running until a certain condition is reached.  So if we want to
count down from 10, we could replace all those `WriteLine` statements with this:

```csharp
for (int t = 5; t > 0; t--)
{
    Console.WriteLine(t);
}
```

There's a lot going on in this `for` loop, so let's break it down:

- The `for` keyword says you're declaring a loop.  The particulars of that `for` loop are within the parentheses `()`.
- `int t = 5;` is defining a variable just like `string name = "Your Name"`.  This time, it's an `int`, short for integer
(i.e.: a whole number, could be positive, negative, or 0).  This variable `t` is what we'll use to determine how many
times we loop.
- `t > 0;` is the condition our loop is checking for.  The body of the `for` loop will keep going as long as `t` is 
greater than 0.
- `t--` is something that's run at the end of every loop to change out counter variable, `t`.  Any sort of statement
could be written here, but it will often be either a `++` (which adds 1 to a number variable) or `--` (which subtracts
1)
- The curly brackets `{ }` define the body of the `for` loop.  Everything within these brackets is what will get repeated.
- The body, another `WriteLine` statement, displays the current value of `t` each time the loop runs.
- Note the multiple semicolons `;` that break up each statement.  As I said above, you could separate things onto one
line each, but a `for` loop is usually written on a single line like this.

Hit F5 and watch it go.  Try changing the initial value of `t` to something larger and see how it changes.  Suddenly it's
very easy to write the same line 100 times with a single `WriteLine` command, isn't it?

## User Input Part 2

What if the number of loops was another piece of user interaction?  Instead of defining the value of `t` ourselves, let's
ask the user.  After we ask for name, add these lines:

```csharp
Console.Write("How many loops?  ");
var userT = Console.ReadLine();
```

Note that I used the word `var`.  This is the *inferred* type keyboard and lets C# determine the type from context without
you having to spell the type out.  This is especially useful if you have variable types with really long names.  Starting
out, I advise against using it because it's helpful to know what type a variable is.

Now let's use our new user input in our `for` loop by changing it to the following:

```csharp
for (int t = userT; t > 0; t--)
```

Uh-oh - a red squiggly line appeared!  Check the error window or mouse over it to see the details.  You should see the 
message:

> Cannot implicitly convert type 'string' to 'int'

As the error explains, `t` is an int - a number - and `userT` is a string.  Why did C# assume `userT` is a string when
we used the `var` keyword?  To explain, mouse over the `ReadLine()` command and see what pops up.  You should see it pop
up the command's definition as follows: `string? Console.ReadLine()`.  That first word tells you what type of variable
the command is giving you.  In this case, it assumes that the user input is going to be a string.  After all, a user could
type in whatever they want, right?  So how do we tell C# that we want an `int` and not a `string`?

## Casting / Parsing

Luckily, C# has done the hard work for us with the `int.Parse()` command.  It can be used like this:

```csharp
var rawInput = Console.ReadLine();
var userT = int.Parse(rawInput);
```

You can mouse over the pieces of this to see the types for the variables and commands.  You'll see that `rawInput` is a
`string` because that's what `ReadLine()` assumes all user input is.  You'll also see that `Parse()` can take a `string`
and give you an `int` in return.  You'll also notice that the red squiggly line in your `for` loop has disappeared!  Try
hitting F5 and seeing what happens now.

If you enter a number, your program will loop that many times.  But what happens if you give it something that is NOT a
number?  Try it out and see!

## Accounting for User Error

So your user decides to be a wise guy and enter "five" instead of "5" and your whole program blows up.  Will they admit
the error of their ways and apologize to you?  **Of course not**!  When programs break, users get mad - even if they are
the ones who broke it - so we have to account for things a user could do wrong.

If you've been typing your code instead of copying/pasting my samples, you may have noticed that VS pops up suggestions
as you type.  When you typed `int.Parse` you may have noticed that it also suggest `int.TryParse`.  Any time VS does this,
you can use the arrow keys to select a suggestion and read the built-in documentation.  `TryParse` says it will give you
a value to indicate if the parsing was successful - that's *exactly* what we need!  Here's how it's used:

```csharp
var rawInput = Console.ReadLine();
if (int.TryParse(rawInput, out int parsedInput))
{
    Console.WriteLine(parsedInput);
}
```

There's a few new things going on here, so let's break it down:
- We're getting `rawInput` the same way as before
- The `if` command takes a boolean value (i.e.: true or false) and runs code only if the value given to it is true.  This
is similar to the `for` loop from before, except the code is executed only once.
- Similar to the `for` loop, the curly braces `{ }` define the body of the `if`.  Things within the curly braces will run
if the condition is true.
- The parentheses `( )` surround the condition of the `if` statement.  In this case, the condition is the result of the
`TryParse` command.
- `TryParse` takes 2 pieces of data, called *arguments*.
    - The first is your `rawInput`, just like `Parse` took.
    - The second is a newly-defined variable that will store the parsed result, if there is one.  The `out` keyword here
    indicates that the newly-created variable will be set by the `TryParse` function.
    - If you hover over `TryParse`, you'll see it returns a `bool` (short for boolean, a true/false value), which is the
    value our `if` is looking for.  If `TryParse` is successful, it returns the value `true` and what's in the `if` will
    run.  If `TryParse` fails, the contents of the `if` will not run.

So what do we do with this?  Well, our `for` loop will only work if the user provides an `int`, so we move all that code
inside of the curly braces of the `if` command.  Be mindful of the punctuation when you're doing this!  This is where a 
ton of mistakes can happen.  The final result should look like this:

```csharp
static void Main(string[] args)
{
    Console.Write("Enter your name: ");
    string name = Console.ReadLine();

    Console.Write("How many loops?  ");
    var rawInput = Console.ReadLine();
    if (int.TryParse(rawInput, out int userT))
    {
        for (int t = userT; t > 0; t--)
        {
            Console.WriteLine(t);
        }
    }
    Console.WriteLine("Hello " + name + "!");
}
```

Hit F5 and run your code.  Try giving it a few different values and see how it behaves differently.

## Give me a number - or **else**!

While trying out your code, you may have noticed that nothing happens if you give bad input - the `for` loop gets skipped
and ther user isn't given any sort of feedback that their input was bad.

We already know that `if` will only run things if a condition is `true`, but what if we want to do something when the 
condition is `false`?  That's where the `else` command comes in.  When paired with an `if`, the `else` can define what to
do instead when the `if` condition is `false`.  It's used like this:

```csharp
bool chocolateIsDelicious = false;
if (chocolateIsDelicious)
{
    Console.WriteLine("I love chocolate!");
}
else
{
    Console.WriteLine("Chocolate is GROSS!");
}
```

If the value of the variable `chocolateIsDelicious` will control which statement runs.  `if` and `else` are very basic 
tools to a programmer, but they are the decision-makers behind much of the programs you use on a daily basis.

***SIDE NOTE***: Remember when I said variables could be anything?  Notice how names of variables can make code easy to
read?  If you show the above snippet to a non-programmer, they could probably figure out what's happening.  If all your 
variable names are non-descriptive things like `x` and `y`, it makes code much harder to read.

Let's use an `else` statement to write a special message if somebody didn't give us a number for the countdown.  You can
put whatever you want as your message, but your final code should look about like this:

```csharp
static void Main(string[] args)
{
    Console.Write("Enter your name: ");
    string name = Console.ReadLine();

    Console.Write("How many loops?  ");
    var rawInput = Console.ReadLine();
    if (int.TryParse(rawInput, out int userT))
    {
        for (int t = userT; t > 0; t--)
        {
            Console.WriteLine(t);
        }
    }
    else
    {
        Console.WriteLine("No number given.  Countdown is CANCELLED!");
    }

    Console.WriteLine("Hello " + name + "!");
}
```

*Reminder*: be careful with punctuation!  `if` and `else` both have their own curly braces, plus the `main` method that
you're in.  It can be very easy to add or remove a curly brace and cause the whole thing to blow up - so be careful!

Hit F5 and run your code again to see your friendly (or not so friendly) error message.

## Keep asking until they get it right

But what if we want to *demand* that the user gives us a number?  After all, it's *our* program, so we're the boss!
Instead of `if` and `else`, let's use a different kind of loop that will keep pestering the user until they cave and
give us a valid number.  That loop is called a `while` loop, and it can be used like this:

```csharp
int x = 5;
while (x > 0)
{
    Console.WriteLine(x);
    x--;
}
```

This is doing the same thing as our original `for` loop, but the syntax is a little different.  Essentially, a `while`
loop is like an `if` statement that repeats itself.  If the condition in parentheses `( )` is true, the body of the 
`while` loop (i.e.: the code inside the curly braces `{ }`) gets run.  In this case, we'll display the value of `x` and
decrease it by 1.

But in our case we don't want our `while` loop to keep going when something is `true`, we want to keep going while 
something is `false` (i.e.: the user didn't give us a valid number).  To do that, we can use a `bool` operator, `!`.
The exlamation mark `!` flips the `bool` value after it.  For example:

```csharp
bool someBoolValue = false;
if (!someBoolValue)
{
    Console.WriteLine("someBoolValue is false!");
}
```

Reading this out, you're asking "if NOT someBoolValue" - the `!` essentially acts like a negative sign in math, by
flipping any `true` values to `false` and vice versa.  We can use this along with `TryParse` to do the following:

```csharp
while (!int.TryParse(Console.ReadLine(), out int userT))
{
    Console.WriteLine("You must enter a number!  Try again.");
}    
```

We're doing a lot on one line, so let's break it down:

- `while` is checking if what's in its parentheses is `true`
- `int.TryParse` is taking a string to try parsing and is giving back a `true` or `false` value
- `Console.ReadLine()` is nested within `TryParse` directly, rather than being put in a variable
- `out int userT` is where the parse value will go, just as before
- The body of the `while` loop contains a `WriteLine` message that instructs the user to try again.

Try hitting F5 and running to see how it works - except it won't work.  Why?  Let's read the error VS is telling you about
inside the `for` loop you created earlier.  You likely see the following message:

> The name 'userT' does not exist in the current context

This is our first time seeing the implications of *scope*.  When you create a variable, that variable only exists in the
place you created it.  Imagine if you had to worry about every name of every variable used by any code ever written.
There's no way you could account for that.  Instead, your variable only exists within the curly braces in which it lives.
To quickly demonstrate, let's add some curly braces for no reason and see what happens:

```csharp
{
    int x = 5;
}
Console.WriteLine(x);
```

You should get the same error telling you that `x` doesn't exist.  You can see it just above the `WriteLine` statement,
but the code can't see it because it's within those curly braces.  You can alter things slightly, though, and see how to
make it work:

```csharp
int x;
{
    x = 5;
}
Console.WriteLine(x);
```

By defining `x` outside of those curly braces, `x` lives in the same place as the `WriteLine` statement below.  Setting
the value of `x` inside the curly braces works because those curly braces *also* live in the same place as `x`.  But this
is why our code from earlier is having an error.  All we have to do is move the place where we create our `userT` variable
so that it is in the same *scope* as where we need to do it.  Your final result should look like this:

```csharp
static void Main(string[] args)
{
    Console.Write("Enter your name: ");
    string name = Console.ReadLine();

    Console.Write("How many loops?  ");
    int userT;
    while (!int.TryParse(Console.ReadLine(), out userT))
    {
        Console.WriteLine("You must enter a number!  Try again.");
    }    
    for (int t = userT; t > 0; t--)
    {
        Console.WriteLine(t);
    }

    Console.WriteLine("Hello " + name + "!");
}
```

Note that the word `int` was removed on the line with the `while` loop.  We only specify the type when we first create a
variable.  Since `int userT` is defined just above that line, we don't need to specify the type over again.  In fact, if
you try, VS will assume you've made a mistake and throw an error.

## *Stay Tuned!*
I will return to add to this page later and include more concepts, such as:
- `foreach` loops
- Data structures such as:
    - Arrays
    - Lists
    - Dictionaries
- Methods
- Classes