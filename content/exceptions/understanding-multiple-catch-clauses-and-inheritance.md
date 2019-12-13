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