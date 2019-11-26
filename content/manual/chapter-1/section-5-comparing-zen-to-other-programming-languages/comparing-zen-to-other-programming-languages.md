# Comparing Zen to Other Programming Languages

In this lecture, we will compare Zen, Java, C and C++.

## Paradigm

Zen, Java and C++ are object-oriented programming languages. Whereas, C is
procedural oriented programming (POP) language.

## Memory Management

All programming languages let you handle data. When you create a variable,
you can assign a portion of the computer’s memory to store the data.
The allocation of memory is a detail that you can usually ignore.
But you need to know what happens to that memory when you no longer need
the data that was stored in it.

In C, C++ and other similar languages, you have to manually release the memory
so that other programs can use it. If you don't, your program develops a memory leak,
which means that your program slowly runs out of memory.

In Zen and Java, you do not have to manually release memory when you are done
with it. Instead, memory is released automatically when it is no longer needed.

The virtual machine includes a garbage collector that scans the memory,
determines when data is no longer needed, and automatically releases it.

## Exceptions

No matter how carefully you design and test your programs, errors happen.
When they do, chances are your program crashes to a halt.

In Zen and Java, errors of all types are generalized into a special type of object
known as an exception. Your program must anticipate errors that can happen while
your program is running. This helps your programs be more reliable. Java requires
any statements that can potentially raise an exception to be handled. However,
this is not the case with Zen.

C++ has a similar approach to handling exceptions. But then, it is not as
sophisticated as the exception handling mechanism found in either Zen or Java.

In the case of C, there is no concept of exceptions. Alternatively, you can
use jump buffers. This mechanism is usually frowned upon and most programmers
tend to stay away from it.

These are some of the major differences between Zen, Java, C, and C++.

Here is a list of many other differences. Unfortunately, we will not be discussing
all of them in this lecture.

|                      | C                              | C++                         | Java                        | Zen                         |
|----------------------|--------------------------------|-----------------------------|-----------------------------|-----------------------------|
| Founder              | Dennis Ritchie                 | Bjarne Stroustrup           | James Gosling               | Samuel Rowe                 |
| Year                 | 1972                           | 1979                        | 1995                        | 2020                        |
| Compiled             | Yes                            | Yes                         | Yes                         | Yes                         |
| Interpreted          | No                             | No                          | Yes                         | Yes                         |
| Paradigm             | Procedure Oriented Programming | Object Oriented Programming | Object Oriented Programming | Object Oriented Programming |
| Pointers             | Yes                            | Yes                         | No                          | No                          |
| Memory Management    | Manual                         | Manual                      | Automatic                   | Automatic                   |
| Statically Typed     | Yes                            | Yes                         | Yes                         | No                          |
| Preprocessor         | Yes                            | Yes                         | No                          | No                          |
| Exceptions           | No                             | Yes                         | Yes                         | Yes                         |
| Function Overloading | No                             | Yes                         | Yes                         | Yes                         |
| Operator Overloading | No                             | Yes                         | No                          | Yes                         |