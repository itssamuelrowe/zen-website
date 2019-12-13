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