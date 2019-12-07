+++
title = "Declaring Functions"
weight = 1
+++

A function is a block of statements. You can give it a name. When a function is
declared inside a class, it defines an object's behavior, basically whatever an
object is capable of performing.

You can call or invoke a function with its name. When you invoke a function, the
execution of your program branches to the body of that function. When the function
is finished, execution resumes from where the program branched, and the program
continues on to the next statement.

You have already used functions. For example, `print` and `prompt` are
functions declared in the `ZenHelper` class.

## Difference Between Functions and Functions

Function is a sequence of instructions that achieve some result. It may take
arguments and return a result. If a function does not return a result it is
usually called a procedure.

Here are a few examples of functions.
```
function drawLine(x1, y1, x2, y2)
  /* Draws a line using Bresenham's algorithm from (x1, y1) to (x2, y2).
   * It does not return anything.
   */

function add(a, b)
    /* Adds a to b and returns the result as a number. */
    return a + b
```

When you need to draw a polygon of 3 lines as a part of a vector image it is
more convenient to invoke the `drawLine()` function thrice rather than duplicating
the algorithm thrice.

Functions are similar to functions, they belong to classes or objects and usually
express verbs of an object. For example, an object of class `Window` usually
would have methods `resize()` and `setVisible()` which do corresponding operations
to the object they belong.

In Zen, methods are also referred to as functions.

## Advantages of Function

The primary advantages of functions are as follows.
 * Functions improve the quality of your code. They make it more readable because
   you break your code into logical chunks.
 * You avoid duplicate code. Imagine you are writing an application that simulates
   an airplane, which requires primitive matrix operations such as addition,
   subtraction and multiplication. Without functions you would have to write these
   operations in several places. So whenever you see yourself writing the same
   code, it is a good idea to write a function.
 * You can implement polymorphism through functions. This is one of the most
   important features of functions.

## Creating Functions

Here is the general form of a function declaration.

```
function name(parameters)
    statement1
    statement2
    ...
    statementN
```

The name of your function helps you call it.

Here is an example of a program which has redundant statements. Apparently,
Harry and Hermione are on an adventure, trying to break into a mysterious tower.
The following program prints the dialogue between them.

```
// MysteryTower.zen

function main(...arguments)
    print('Harry Potter: Can you open this door?')
    print('Hermione Granger: Alohomora!')

    print('Harry Potter: Can you open this door?')
    print('Hermione Granger: Alohomora!')

    print('Harry Potter: Can you open this door?')
    print('Hermione Granger: Alohomora!')

    print('The door opens!')
``

In this example, your program prints the same messages three times. But then
you end up writing the same statements over and over. Of course, you could
rewrite this program with a loop. Alternatively, you could use a function.

Here is another version of the previous example using a function.

```
// MysteryTower2.zen

function openDoor()
    print('Harry Potter: Can you open this door?')
    print('Hermione Granger: Alohomora!')

function main(...arguments)
    openDoor()
    openDoor()
    openDoor()

    print('The door opens!')
```

The order in which you declare your functions does not matter. So in this example,
you could write the `openDoor()` function after the `main()` function, it would
not matter. Your program will execute the same.

```
// MysteryTower2.zen

function main(...arguments)
    openDoor()
    openDoor()
    openDoor()

    print('The door opens!')

function openDoor()
    print('Harry Potter: Can you open this door?')
    print('Hermione Granger: Alohomora!')
```

When you invoke openDoor(), the two print statements in the `openDoor()` function
are executed sequentially. After which the control returns back to where the
function was called.