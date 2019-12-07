+++
title = "Understanding Functions That Return Values"
weight = 8
+++

Functions that perform operations without returning any value are useful, but this
is not the case always. In this section you will learn how to return values
from functions.

Imagine that you write a function that accepts your date of birth and calculates
your age. Probably the function can print it on the console. But this is not what
you always want. For example, you would want the calculated age to determine if
you are eligible to vote, or not. In such cases, your function needs to return
a value or store the result in some field. Usually, returning a value is much
easier.

You can use the return statement to return a value to the caller.

Here is the general form of the return statement.

```
return expression
```

The expression must evaluate to a value which will be returned by the function.
You cannot return more than one result at a time. Further, the function terminates
as soon the return statement is executed. Improper use of return statements create
unreachable regions in your function causing bugs. We recommend you to
design your functions to always use a minimum number of return statements. This
way you can easily determine the exit points of your function.

Here is an example of a function that accepts a number and determines if it
is even, or not.
```
// OddOrEven.zen

function isEven(number)
    if number % 2 == 0
        return true
    else
        return false

function main(...arguments)
    var n = 19
    var result = isEven(n) ? 'even' : 'odd'
    printf('%d is %d.\n', n, result)
```

Here, the `isEven()` function accepts an integer value. It then divides it by 2 for
remainder. If the remainder is `0`, it returns `true` indicating an even number.
Otherwise, it returns `false` indicating an odd number.

Here is another version of the `isEven` function.
```
// OddOrEven2.zen

function isEven(number)
    return number % 2 == 0

function main(...arguments)
    var n = 19
    var result = isEven(n) ? 'even' : 'odd'
    printf('%d is %s.\n', n, result)
```

Here is an example of the `isEven()` function, which would generate
an error.

```
function isEven(number)
    if number % 2 == 0
        return true
```

In this example, the function does not return a value in all cases. If the specified
number was odd, the function would not return any value, but the compiler expects
you to return a value in all cases. This is why it would generate errors if you
tried to feed code like this.

You should be careful when you return values from loops and conditional statements.
You need to ensure that a value is returned in all case.

Here is an example of a program that computes the factorial of a number.
```
// Factorial.zen

function factorial(number)
    var result = 1
    for i in range(2, number + 1)
        result *= i
    return result

function main(...arguments)
    var n = promptInteger('Enter an integer: ')
    var result = factorial(n)
    printf("%d! = %d\n", n, result)
```