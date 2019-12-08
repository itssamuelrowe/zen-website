+++
title = "Function Overloading"
weight = 9
+++

Unlike variables, multiple functions in the same scope can have the same
name. This technique is known as function overloading. It is a feature of
polymorphism. Function overloading is a very useful feature.

Zen differentiates functions using pseudo function signatures. A pseudo function
signature is a part of function declaration. It is the combination of the function
name and the parameter count. The names of the parameters are not included in the
pseudo function signature.

In order to overload a function, the pseudo function signatures should be different.
Which means even if your function names are the same, you need to have different
parameter counts. When the functions have the same name but different parameter
counts, the functions are said to be overloaded.

When you invoke an overloaded function, Zen uses the following conditions to
determine which version of the overloaded function you are calling.

 * The type of each argument you are passing.
 * The number of arguments you are passing.

This is the reason why overloaded functions must have different parameter counts.
Otherwise, Zen will not be able to determine which version of the overloaded
function to call.

Here is a simple example that computes area of squares and rectangles using
function overloading.

```
// AreaComputer.zen

/**
 * Compute the area of a square.
 */
function computeArea(side)
    return side * side

/**
 * Compute the area of a rectangle.
 */
function computeArea(length, breadth)
    return length * breadth

function main(...arguments)
    var side = 10
    var areaOfSquare = computeArea(side)
    printf('The area of square with side %d is %d.\n', side, areaOfSquare)

    var length = 10
    var breadth = 5
    var areaOfRectangle = computeArea(length, breadth)
    printf('The area of rectangle with length %d and breadth %d is %d.\n', length, breadth, areaOfRectangle)
```

The output of this program is shown here.

```
The area of square with side 10 is 100.
The area of rectangle with length 10 and breadth 5 is 50.
```

As you can see, `computeArea()` is overloaded two times. The first version accepts
a single parameter named `side`. The second version accepts two parameters
named `length` and `breadth`, respectively. When you invoke a function, Zen
looks for a match between the arguments passed and the function parameters
declared.

When `computeArea` is called the first time with a single integer argument,
the function which computes the area of a square is invoked. Similarly, when
`computeArea` is called the second time with two integer arguments, the function
which computes the area of a rectangle is invoked. The results are respectively
stored in variables before printing.

Overloading is useful because it allows you to declare and invoke related functions
with the same name.

For example, you could implement an operation such as `computeVelocity`, which
obviously evalutes the velocity of an object, say a bike. The name `computeVelocity`
represents the general action that is being performed. You could implement
two different versions of calculations using different formulas. Assume
one version accepts distance and time, whereas another version accepts force,
mass and time. With function overloading you could easily implement this. Otherwise,
you would have to come up with different names for each function.

When you overload a function, each version can implement anything. You do not
have to relate the functions to one another. We recommend you to always overload
functions that perform the same operation but in different ways.