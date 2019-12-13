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