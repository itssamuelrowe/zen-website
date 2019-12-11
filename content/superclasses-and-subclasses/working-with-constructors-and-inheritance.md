+++
title = "Working with Constructors and Inheritance"
weight = 4
+++

When you inherit a class, the constructors are not inherited because cnostructors
are not instance members. Which means each class should create its own constructors.
However, sometimes you may want to invoke the constructor of a superclass from
your subclass.

For example, to initialize the fields in a superclass you either need access to
them or invoke the constructor. The former technique is verbose and not recommended
because it violates the principles of encapsulation. Instead you can invoke the
superclass constructor.

## Invoking Superclass Constructors

A constructor can call the superclass constructor from a subclass. Zen provides
special syntax for this purpose. You must use the `super` keyword with parenthesis.
This is useful when your subclass constructor requires some behavior which already
exists in superclass constructor. Whenever you want invoke a supeclass constructor
you can use the super keyword.

Here is the general form invoke a superclass constructor.

```
Class.super(arguments)
```

Here, the Class indicates the superclass whose constructor you want to invoke.
It is optional if your class inherits only one superclass. The arguments are the
values you want to pass to your superclass constructor.

You need to follow these rules when calling a superclass constructor.

You can call a superclass constructor only in the first statement. But in the above
example, a declaration statement is the first statement. This results in a
compile-time error.

#### RULE 1 - A constructor can call one or more superclass constructor.

For example, this will compile.

```
function new(title)
    UACertifiedMovie.super(null)
    Movie.super(title, 0.0, 0.0)
}
```

You can call one or more superclass constructor. However, you can invoke only
one constructor per superclass. Otherwise, the compiler generates error.

#### RULE 2 - You can call superclass constructors only if their invocations occur before any other statement.

For example, this will not compile.

```
function new(title)
    var i = 0
    super(title, 0.0, 0.0)
```

#### RULE 3 - You can either invoke another constructor or a superclass constructor, not both.

For example, the first constructor can call the second constructor. The
second constructor can call the third constructor.

```
function new(title)
    super(title, 0.0, 0.0)
    this('Christopher Nolan')
```

You can call a superclass constructor or another constructor in your class.
But the constructor show above invokes both the constructors. This results in
a compile-time error.

This rule applies only when you explicitly invoke a superclass constructor. 
Because when you do not invoke the superclass constructor, Zen automatically
invokes the default superclass constructor.