+++
title = "Difference Between Functions and Methods"
weight = 2
+++

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
