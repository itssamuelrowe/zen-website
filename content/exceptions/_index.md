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