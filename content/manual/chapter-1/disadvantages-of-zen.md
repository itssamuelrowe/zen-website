# Disadvantages of Zen

Like any programming language, Zen is not perfect.

## Performance

Zen programs are converted to bytecodes when compiled. During execution, these
byte codes are interpreted by the virtual machine. Thus, Zen programs take
longer time to run compared to programs written in C and C++. But this problem
will soon be overcome with a Just-in-time Compiler (JIT).

## Consumes More Memory

This is one of the biggest problems in Zen. Zen takes more memory space than the
other native programming languages like C and C++. The Zen Virtual Machine,
stores metadata about classes and other objects in the background. This causes
your programs to consume more memory.

## Garbage Collection

You have no control over garbage collection in Zen. The Zen Virtual Machine
takes care of everything for you. Sometimes this is not what you want.