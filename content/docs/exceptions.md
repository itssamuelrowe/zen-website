+++
title = "Exceptions"
weight = 14
chapter = true
+++

### Chapter 14
# Exceptions

No matter how carefully you design and test your program, errors are bound to
happen one or the other. When they do, chances are your program crashes to a halt.

In this chapter you will see what happens when Zen encounters an unexpected
situation. Many techniques have been invented to deal with such errors.
Many languages such as C and Assembly, errors must be manually checked and handled
by using error codes. This technique is very verbose and inelegant. Zen provides
a sophisticated error handling mechanism. Zen implements an object-oriented
approach to handling such situations known as exceptions.

In Zen, an exception is an object which represents an unexpected situation in
your program at runtime. In other words, an exception is an error that occurs
when your program is running. Exceptions allow your programs to recognize errors
and respond to them gracefully. In fact, sometimes your program can resolve the
situation and resume execution normally.


+++
title = "Understanding Exceptions"
weight = 1
+++

In Zen, errors of all types are generalized into a special type of object
known as an exception. An *exception* is an object which represents an unexpected
event. It occurs when your program is running. It disturbs the flow of your program.
Exceptions are used to indicate many types of error conditions.

An exception is represented by an object. It holds the information about the
event such as the condition, the stacktrace, the location, and a message.
The exception object is usually refered to as *exception*. You can *throw and
catch* an exception.

After an exception object is created, it is thrown. The Zen Virtual Machine
attempts to find an exception handler for the exception by backtracking the list
of functions that have been called, known as the call stack. If a handler is found,
the exception is caught.

An exception may occur for many reasons. For example, the programmers did not
anticipate possible problems, or the application is untested, or the program
encounters situations such as corrupt data, corrupt files, network problems,
hardware device failure, and so on.

Here are some common exceptions.

 * `OutOfMemoryError`
 * `StackOverflowError`
 * `InvalidPathException`
 * `IOException`
 * `NullPointerException`
 * `ArrayIndexOutOfBoundsException`

When an unexpected situation occurs, an exception object is created and thrown.
The function which invoked the current function can handle the exception or
let it pass through. At some point, the exception is caught and handled.
Exceptions can be thrown either by your code, or the Zen Virtual Machine, or
any libraries your code uses.

Exceptions thrown by the Zen Virtual Machine indicate errors that violate the
rules of Zen. For example, if you try to access an instance member through a
`null` reference, the virtual machine throws a `NullPointerException`.

Exception handling in Zen uses the following keywords.

 * `try`
 * `catch`
 * `throw`
 * `finally`

In short, when an exception occurs, a new exception object is created.
This object is thrown using a throw statement. Your code can anticipate exceptions
to be thrown from a block of code using the `try` clause. If an exception is
thrown within the `try` block your code is monitoring, your code can handle this
exception using the `catch` clause. Any code that must be executed regardless of
an exception being thrown or not, must be written in the `finally` clause.

Here is the general form of a try statement.
```
try
    // Statements that may trigger an exception
    statement1
    statement2
    ...
    statementN
catch Exception1 exception
    // Handle the exception `Exception1`
    statement1
    statement2
    ...
    statementN
catch Exception2 exception
    // Handle the exception `Exception2`
    statement1
    statement2
    ...
    statementN
finally
    // Statements that must be executed regardless of an exception being thrown
    statement1
    statement2
    ...
    statementN
```

Here, `Exception1` and `Exception2` indicate the type of exception to catch.
You will learn more about the mechanics involved throughout this chapter.

+++
title = "Advantages of Exceptions"
weight = 2
+++

The advantages of exceptions are as follows.

#### You can separate error handling from your algorithm.

With exceptions you can separate the details of what happens when an unexpected
situation occurs. You can separate such logic from the main logic of your program.

In other programming languages, error detection, reporting, and handling often
lead to complex and confusing code.

Exceptions allow you to keep your source code clean and organized.

#### Your functions do not have to forward errors.

Exceptions have the ability to propagate up the stack of functions currently
invoked. For example, assume that a function is the fourth function in a series
of nested function calls. If the first function is the only function interested in
handling the error, and the error occurs in the fourth function, you don't
have to manually forward the error. Throwing an exception does the job
for you. This allows you to generalize error handling in one common place.

#### You can group and differentiate error conditions.

Because exceptions are objects, you can group or categorize them using their
class hierarchy. An example of a group of related exception classes are the exception
classes which inherit the `zen.io.IOException` class. The IOException class
represents an input/output error. Its descendants represent more specific errors.
For example, `InvalidPathException` indicates that a path could not be found
on the disk.

All these advantages make exceptions reliable, stable, and secure.

+++
title = "Understanding Exception Types"
weight = 3
+++

An exception object contains the information about the error condition. It
includes information such as stacktrace and message. Perhaps, the most important
information is the cause of the error. It is indicated by the name of the exception
class used to create the exception object. Usually, you will use exception
objects only to figure out the kind of error that occurred.

In order to understand exceptions fully, you need to understand the class
hierarchy of exceptions first. All exception classes are subclasses of the
`Throwable` class. In other words, the `Throwable` is the superclass of all
exceptions in the exception class hierarchy. The `Throwable` class, like any
other class in Zen, inherits the `zen.core.Object` class. You can throw and
catch only the instances of the `Throwable` class.

The exception class hierarchy is further divided into two main subclasses.

 * `Exception`
 * `Error`

The `Exception` class represents conditions that your program should catch and
handle. In order to create your own custom exception classes, you need to inherit
this class. `InvalidPathException` is an example of such an exception. Further,
the class `RuntimeException` is a special subclass of the `Exception` class.
Exceptions which are intended to be unchecked should inherit this class.
`NullPointerException` is an example of such an exception. You will learn more
about checked and unchecked exceptions in the next lecture.

The second subclass of the `Throwable` class is the `Error` class. It defines
exceptions that your program should generally not catch. These exceptions are
usually thrown by the Zen Virtual Machine to indicate errors related to the
environment. `OutOfMemoryError` is an example of such an error which indicates
memory exhaustion.

The following code segement shows the public methods found inside the `Throwable`
class. Please refere the Zen documentation for more reference.

```
class Throwable extends Serializable

    function getMessage()
    function getCause()
    function toString()
    function printStackTrace()
    function printStackTrace(stream)
    function getStackTrace()
    function suppress(exception)
    function getSuppressedExceptions()
```

Here is a list of some typical exceptions.

 * `IllegalArgumentException`
   This exception is thrown to indicate that you passed an incorrect argument
   to a method.

 * `ArithmeticException`
   This exception is thrown to indicate that you tried to perform an illegal
   arithmetic operation, such as dividing an integer by zero.

 * `IOException`
   This exception is thrown to indicate an error that the program encountered
   when you tried to perform an I/O operation.

 * `ClassNotFoundException`
   This exception is thrown to indicate that class coud not be found.

Zen includes hundreds of exceptions. You can learn more about them from the
Zen documentation.

+++
title = "Catching Exceptions"
weight = 4
+++

Before you learn to catch exceptions in your program, you need to see what happens
when you do not catch them. Here is an example which generates an exception.

```
// GenerateException.zen

function main(...arguments)
    var a = 100
    var b = 0
    var c = a / b

    printf('%d / %d = %d\n', a, b, c)
```

When the Zen Virtual Machine tries to evalute `a / b`, it throws an exception
because you tried to divide an integer by zero.

The output of this example is shown here.

```
Exception in thread 'main' zen.core.ArithmeticException: Division by zero
    at GenerateException.main(GenerateException.zen:6)
```

The output contains the type of the exception, an error message and the
stacktrace which points to the location from where the exception occurred.
The stack trace includes the class names, the function names, the file names, and
the line numbers through which the exception propogated.

When an exception is thrown, Zen stops whatever your program is doing and
tries to find an exception handler. In this example, this causes the execution
of the main function to stop. Since we have not provided an exception handler, the
exception propogates outside your function and is caught by the default exception
handler.

Every thread in Zen has a default exception handler which is triggered when an
exception is never caught. In other words, any exception your program fails to
catch is processed by the default exception handler. The default exception handler
prints the exception, the stacktrace from the point where the exception was
thrown, and terminates the current thread. A thread is a component which allows
multiple parts of your program to run simultaneously. In this example, there is
only one thread, hence the program is terminated.

Here is another example which demonstrates how the stacktrace can be useful
to locate the cause of the error.
```
// GenerateException2.zen

function divide(a, b)
    return a / b

function main(...arguments)
    var a = 100
    var b = 0
    var c = divide(a, b)
    printf('%d / %d = %d\n', a, b, c)
```

Here is the output generated by this example.
```
Exception in thread 'main' zen.core.ArithmeticException: Division by zero
    at GenerateException2.divide(GenerateException2.zen:4)
    at GenerateException2.main(GenerateException2.zen:9)
```

As you can see, the stacktrace includes the class name, the function name,
the file name, and the line numbers through which the exception propogated.
The exception can occur in any source file, any class, and any function. This
is why each element in the stacktrace contains these information.
In other words, the stack trace will always show the function invocations which
led up to the error.

## Using the Try and Catch Clauses

You cannot always depend on the default exception handler to handle the exceptions.
In some situations, you will want to handle the exception yourself. With a custom
exception handler, you can resolve the error and prevent the program from terminating.
Imagine, you are writing a server side program. How troublesome would it be if your
program terminated whenever an exception occurred?

You need to monitor a block of code for exceptions using the `try` clause.
You can then provide a custom exception handler using a catch clause.
Whenever you write a `try` clause, you are essentially writing the try statement.
It is a compound statement.

Here is the general form of the try clause.
```
try
    statement1
    statement2
    ...
    statementN
```

A try clause should always be followed by a catch clause or a finally
clause. When both the clauses appear, the finally clause should be the last
clause.

Here is the general form of the catch clause.
```
catch ExceptionType identifier
    statement1
    statement2
    ...
    statementN
```

The `ExceptionType` indicates the type of exception the catch clause handles.
When an exception is caught, the variable identified by `identifier` you
specify holds a reference to the exception object. Basically, you declare a
parameter in the parenthesis of the catch clause. The parameter references the
exception object when the exception is caught.

Here is an example which demonstrates how to catch an exception.
```
// GenerateException3.zen

function divide(a, b)
    return a / b

function main(...arguments)
    var a = 100
    var b = 0
    try
        var c = divide(a, b)
        printf('%d / %d = %d\n', a, b, c)
    catch ArithmeticException exception
        print('Error: You cannot divide an integer by zero.')
```

This example generates the following output.
```
Error: You cannot divide an integer by zero.
```

Notice that the print statement inside the try clause is never executed.
When an exception is thrown, the program stops whatever it is doing.
Zen then tries to find the nearest catch clause in the stack trace.
When a catch clause which anticipates the exception which occurred is found
in the stack trace, the program control jumps out of the try clause and is
transferred to the catch clause. A reference to the exception object is stored
in the parameter of the catch clause. Once the catch clause is done executing,
the statement following the catch clause is executed. The control never returns
back to the location where the exception occurred. Because exceptions are not
like functions to return back.

A catch clause can catch an exception only if one of the statements within the
try clause associated with it throws an exception.


+++
title = "Multiple Catch Clauses"
weight = 5
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

+++
title = "Understanding Multiple Catch Clauses and Inheritance"
weight = 6
+++

When you use multiple catch clauses, you need arrange them properly. Imagine
that you have two catch clauses. The first catch clause handles exceptions of
type `A` and the second catch clause handles exceptions of type `B`. The order
in which your catch clauses appear does not matter as long as A and B are not
related. In other words, the order does not matter if `A` is neither the
superclass or subclass of `B`.

However, if `A` and `B` are related, that is, if `A` is either the superclass
or subclass of `B` then the order matters. You always need to write the catch
clause which handles the subclass first because Zen always selects the first
suitable clause without considering other clauses. Zen searches through the
catch clauses in the order in which they appear in your source code. If you
first write a catch clause which handles your superclass, the exception object
even if it is an instance of the subclass is implicitly cast by Zen to match
the superclass. This results in the selection of the catch clause which handles
the superclass, not the subclass.

Consider the following example.

```
// MultipleCatchClauses2.zen

function divide(a, b)
    return a / b

function main(...arguments)
    try
        var a = 10
        var b = 20
        var c = divide(a, b)
        printf('%d / %d = %d\n', a, b, c)
    catch Exception exception
        print('Error: This is a generic message.')
    catch ArithmeticException exception
        print('Error: You cannot divide an integer by zero.')
```

If you try to compile this example, the compiler will generate the following error.
```
MultipleCatchClauses2.zen:14: error: overshadowed exception ArithmeticException
```

The error basically means that your second catch clause will never be executed
because the first catch clause handles it. You need to change the order of
the catch clauses to fix this problem.

## Handling all Exceptions in One Place

You can create a general catch clause such that all the exceptions are handled
by a single catch clause. You have learnt how implicit casting works with exceptions.
Using this concept, we can create a general catch clause.

You know that the `Throwable` class is the superclass of all exceptions. Which
means, if you write a catch clause which handles `Throwable`, then all types
of exceptions are handled by it.

Here is the general form of such a catch clause.
```
try
    statement1
    statement2
    ...
    statementN
catch Throwable exception
    ...
```

Since, exceptions which inherit `Error` should not be caught, it is better to
write a catch clause that handles the `Exception` class. This way, you can
catch only the exceptions that are meant to be caught.

Here is the general form of such a catch clause.
```
try
    statement1
    statement2
    ...
    statementN
catch Exception exception
    ...
```

+++
title = "Throwing Exceptions"
weight = 7
+++

So far, you have only learnt to catch exceptions. In particular, the exceptions
that were thrown by Zen. However, you can throw an exception manually, using
the throw statement.

The general form of throw statement is shown here.
```
throw expression
```

The throw statement is a simple statement. Therefore, it is terminated by a
semicolon.

Here, the `expression` must evaluates to an object whose type inherits `Throwable`.
It can be an instance of the `Throwable` class itself.

Unlike C++, you cannot throw primitive values such as integer or floating-point
decimals. In fact, you cannot throw an instance of a class which does not inherit
the `Throwable` class. Which means, you cannot throw objects such as strings
and arrays.

The flow of execution stops immediately after you throw an exception. Any
statements following the throw statement are skipped. The nearest enclosing try
block is checked to see if it has a catch clause that handles the exception.
If it finds a suitable catch clause, then the control is transferred to that
clause. Otherwise, the next enclosing try statement is checked, and this process
repeats until no try statements are found. In such a case, the default exception
handler is triggered. It will print the stack trace and the error message.
After which, the thread in which the exception occurred is terminated.
So far you have learnt to write single threaded programs. Therefore, if your
main thread terminates, your program itself will terminate.

Here is an example program which throws an exception.
````
// ThrowExample.zen
function printGreetings(name)
    if name == 'Chikka Chikka Slim Shady'
        throw new IllegalArgumentException('That hardly sounds like a name.')
    printf('Hi, %s!\n', name)

function main(...arguments)
    try
        printGreetings('Chikka Chikka Slim Shady')
    catch IllegalArgumentException exception
        print('Error: ' + exception.message)
```

This program generates the following output.
```
Error: That hardly sounds like a name.
```

The `printGreetings()` function validates the name before printing it. It considers
`'Chikka Chikka Slim Shady'` an invalid name. Therefore, when you specify this name
it throws an exception. The `IllegalArgumentException` class is an in-built Zen
class. It is thrown to indicate an illegal argument passed to a function.
You can pass a message to its constructor.

In the `main()` function, we invoke the `printGreetings()` function with `"Chikka
Chikka Slim Shady"` as the name. This causes it to throw an exception. The
main function catches this exception. You can retrieve the message that you
specified to the constructor of the `IllegalArgumentException` with the `message`
property. The catch clause retrieves the message and prints it on the console.

+++
title = "Understanding Checked and Unchecked Exceptions"
weight = 8
+++

The concepts of checked and unchecked exceptions were inspired from Java. These
concepts are simplified in Zen and are observed only as design principles,
meaning the compiler does not enforce these rules. However, the compiler
marks each function with the exceptions it may throw. This information can be
used outside Zen by other tools.

An *unchecked exception* is an exception which you can handle if you want.
Any exception class which inherits the `RuntimeException` class is an unchecked
exception. The compiler does not force you to handle it. It is assumed that the
application cannot do anything to recover from such exceptions at runtime.
So far, all the exceptions you have used are unchecked exceptions.

A *checked exception* is an exception which you need to handle. However, the
compiler does not force you to handle it. Any exception class which inherits the
*Exception* class is a checked exception. An example of a checked exception is the
`IOException` class.

Unchecked exceptions allow you to ignore exceptions that you cannot recover
from, and only handle the ones you can. This leads to less clutter. However,
many programmers simply ignore unchecked exceptions. Turning all exceptions
into unchecked exceptions would lead to complicated error handling.

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