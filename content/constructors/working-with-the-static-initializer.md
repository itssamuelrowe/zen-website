+++
title = "Working with the Static Initializer"
weight = 4
+++

Sometimes you may want to initialize your static fields after computing a value.
A static initializer is a special block of code which initializes a class.
It is written inside a class and outside function and constructors. You cannot
assign a name or invoke a static initializer, at least directly.

It is executed whenever the class is loaded. The Zen Virtual Machine may
unload a class when the class is unused to save memory. Since you cannot control
when a class is loaded in all cases, we recommend you to design your static
initializers to be unaware of the context in which it is executed.

The general form of a static initializer is shown here.
```
function static()
    statement1
    statement2
    ...
    statementN
```

As you can see, a static initializer is similar to a constructor, except it
is identified by the `static` keyword. You cannot have more than one static
initializer in your class.