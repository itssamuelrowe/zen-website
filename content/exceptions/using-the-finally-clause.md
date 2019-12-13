+++
title = "Using the Finally Clause"
+++

When an exception is thrown, the execution of your code jumps abruptly, possibly
from one function to another function. This means some important segment of your
code may be skipped. This could be a problem in some functions.

For example, if a function opens a file in the beginning and closes it before
returning, then you will not want the code that closes the file to be skipped
by an exception. The finally clause is designed to control such situations.

You can create a finally clause in a try statement. The finally clause is
basically a block of code that will always be executed, regardless of an exception
being thrown or not. If an exception is thrown, the finally block will execute
even if no catch clause matches.

If a function is returns to the caller from inside a try/catch clauses, via an
uncaught exception or a return statement, the finally clause is executed just
before the function returns. The finally clause is optional. However, a try clause
requires at least one catch or a finally clause to follow it.

```
// FinallyExample.zen

function divide(a, b)
    return a / b

function main(...arguments)
    try
        var a = 10
        var b = 0
        var c = divide(a, b)
        printf('%d / %d = %d\n', a, b, c)
    finally
        print('This statement was executed.')
```

This example generates the following output.

```
This statement was executed.
Exception in thread 'main' zen.core.ArithmeticException: Division by zero
    at FinallyExample.divide(FinallyExample.zen:4)
    at FinallyExample.main(FinallyExample.zen:10)
```

As you can see, the print statement inside the finally clause was executed
even when an exception was thrown. Without the finally clause the exception
would have prevented the print statement from being executed.