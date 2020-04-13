+++
title = "Introduction: Yet Another Programming Language"
weight = 1
+++

This module is a gentle introduction to the world of Zen. You will learn what
Zen is, its history, and where it is going. You will also also learn about
its advantages and disadvantages. Finally, we will try to compare Zen with
other popular programming languages.

> You can download all the examples shown throughout the manual from the following
> link.
> https://github.com/itssamuelrowe/zen-examples

## What is Zen?

Zen is a general purpose programming language designed to build simple, reliable
and efficient programs. It was created by Samuel Rowe. The initial development
began in 2017.

Zen was designed to develop applications that are capable of running across
multiple platforms. As of now, Zen is officially supported on all major platforms,
in particular, Linux, Windows, and MacOS. In the future, programs written in Zen
will able to run on browsers via WebAssembly.

Zen is similar to Java, Python, and C. So, if you have any experience with these
languages, you will find Zen easy to learn. It should be noted that Zen is
different in many significant ways.


## Advantages of Zen

#### Zen is Simple

Zen has a clear syntax which makes it easy to learn and use. With a combination of libraries, it makes tasks such as string manipulation, mathematical calculations, networking and other mundane tasks extremely simple.

Zen provides high-level collections such as lists, maps, sets, bags, queues,
stacks, and so on. You do not need external libraries or hours of coding to
use these collections.

#### Zen is Platform Independent

The platform independence of Zen allows your programs to run on many types of
computers. In other words, applications written on one platform can be easily
ported to another platform.

Specifically, a Zen program runs on any computer with the Zen Virtual Machine.
The programs you write in Zen are compiled to a special binary format known as
the Binary Entity Format (FEB). The virtual machine is responsible for the
interpretation of your program. As of this writing, Zen is available for all
major platforms, in particular, Linux, Windows, and MacOS. In the future, programs
written in Zen will able to run on browsers via WebAssembly.

#### Zen is Purely Object Oriented

Zen is a purely object-oriented programming language, which means your programs
are built with *objects*. Objects are programming entities that represent real-world
objects.

#### Zen Includes Automatic Memory Management

In programming, you can take a portion of your computers memory. This is known
as memory allocation. You can then store data there.

You can safely ignore the mechanisms of allocating the memory. But in many
programming languages, you need to safely tell *what happens to the memory
when you no longer need it*.

For example, in C and C++ you have to write code that will release the memory
your program allocated. If you forget this, your program will cause a *memory leak*.
Which means your program will soon run out of memory.

However, in Zen you do not have to release memory. The Zen Virtual Machine does
it for you! It has a special component called the garbage collector. It automatically
releases memory that is no longer in use.

> As of this writing, the garbage collector is not available. It is currently
> under development.

#### Zen is Concurrent

Zen allows two or more parts of your program to run simultaneously. This allows
your program to use multiple CPU cores efficiently.

> As of this writing, concurrency is not available. It is currently
> under development.

## Zen is Secure

Zen is a secure programming language.

 * You do not have to deal with pointers.
 * You cannot access arrays with illegal indexes.

Thus, several security flaws like stack corruption or buffer overflow are
impossible to exploit.

### Disadvantages of Zen

Like any programming language, Zen is not perfect.

#### Performance

Zen programs are converted to bytecodes when compiled. During execution, these
byte codes are interpreted by the virtual machine. Thus, Zen programs take
longer time to run compared to programs written in C and C++. But this problem
will soon be overcome with a Just-in-time Compiler (JIT).

#### Consumes More Memory

This is one of the biggest problems in Zen. Zen takes more memory space than the
other native programming languages like C and C++. The Zen Virtual Machine,
stores metadata about classes and other objects in the background. This causes
your programs to consume more memory.

#### Garbage Collection

You have no control over garbage collection in Zen. The Zen Virtual Machine
takes care of everything for you. Sometimes this is not what you want.

## Comparing Zen to Other Programming Languages

In this lecture, we will compare Zen, Java, C and C++.

#### Paradigm

Zen, Java and C++ are object-oriented programming languages. Whereas, C is
procedural oriented programming (POP) language.

#### Memory Management

All programming languages let you handle data. When you create a variable,
you can assign a portion of the computer's memory to store the data.
The allocation of memory is a detail that you can usually ignore.
But you need to know what happens to that memory when you no longer need
the data that was stored in it.

In C, C++ and other similar languages, you have to manually release the memory
so that other programs can use it. If you don't, your program develops a memory leak,
which means that your program slowly runs out of memory.

In languages such as Zen, Python, JavaScript and Java, you do not have to manually
release memory when you are done with it. Instead, memory is released automatically
when it is no longer needed.

The virtual machine includes a garbage collector that scans the memory,
determines when data is no longer needed, and automatically releases it.

#### Exceptions

No matter how carefully you design and test your programs, errors happen.
When they do, chances are your program crashes to a halt.

In Zen, errors of all types are generalized into a special type of object
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
| Creator              | Dennis Ritchie                 | Bjarne Stroustrup           | James Gosling               | Samuel Rowe                 |
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