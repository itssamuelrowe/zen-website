+++
title = "Multiple Catch Clauses"
weight = 4
+++

In some cases, more than one type of exception can be thrown by the statements
in your try clause. To handle such situations, you can specify more than one
catch clause, each catching a different type of exception. When an exception is
thrown, each catch clause is checked in order to see if it handles the exception.
The first catch clause whose type matches the thrown exception object is executed.
When one catch statement is finished executing, the other catch clauses are skipped.
The program control transfers to the statement following the try statement.

Here is an example of a try statement which handles multiple types of exceptions.

```
// MultipleCatchClauses.zen

function divide(a, b)
    return a / b

function main(...arguments)
    try
        var a = 10
        var b = 20
        var c = divide(a, b)
        printf('%d / %d = %d\n', a, b, c)

        var object = null
        var string = object.toString()
        print(string)
    catch ArithmeticException exception
        print('Error: You cannot divide an integer by zero.')
    catch NullPointerException exception
        print('Error: You cannot dereference null.')
```

Here is the output produced by this example.
```
0
Error: You cannot dereference null.
```

The statements within the try clause in this program can generate two exceptions.
You cannot divide an integer by zero. In this example, invoking the `divide()`
function may produce an `ArithmeticException`. Since the arguments are positive integers,
this exception does not occur. We nevertheless provide a catch clause to handle
it. The program successfully divides `a` and `b` and prints the result.

You cannot dereference a null reference. Doing so will cause Zen to throw a
`NullPointerException`. Therefore, we provide a catch clause to handle it.

This program was intentionally designed to produce a `NullPointerException`
exception. When the exception is thrown, the catch clause which handles the
`NullPointerException` exception is triggered. Thus, the second print
statement in the try clause is not executed.