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