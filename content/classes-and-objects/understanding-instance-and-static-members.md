+++
title = "Understanding Instance and Static Members"
weight = 4
+++

## Instance Members

Instance variables are variables that you declare inside a class body and
without the `static` keyword. They are declared outside functions, constructors,
and initializers. These variables are initialized when you create an instance
of the class. Further, each instance of the class gets a copy of these variables.

In fact, when any member of a class, except constructors, is declared
without the `static` keyword you are essentially declaring an instance member.
An instance member can be accessed only with a reference to an instance.

When you create an instance of a class, the instance gets its own copy of the
instance variables in memory. Zen treats other instance members specially.
In fact, each instance of class does not contain its own copy of instance members
such as functions, constructors, and initializers. Because multiple copies of
such members will exhaust the memory. Instead Zen keeps only one copy of
such instance members and simulates as if each instance gets its own copy.
Actually, if memory were not a concern, each instance would get its own copy
of such members to improve performance.

## Static Members

Class variables are variables that you declare within a class with the `static`
keyword. They are outside functions, constructors, and initializers. Remember,
you declare class variables with the `static` keyword.

Unlike instance variables, each instance of a class does not get a copy of class
variables. A class member can be accessed without a reference to an instance.

Static members belong to the class instead of a specific instance. Which means
if you make a member static, you can access it without an instance.
You should always remember that whenever you create an instance of a class,
the instance does not get its own copy of the static members.

You have already used the `static` modifier from the beginning of this manual.
The `main()` function is declared outside a class, an implicit static modifier
is added by the compiler. However, you must explicitly add the static modifier
when you declare the `main()` function inside a class. The Zen Virtual Machine
(ZVM) does not create an instance of your main class before invoking the main
function. This is why you should always declare the main function as static.

Here is an example of a class variable.

```
// Circle.zen

class Circle
    static var PI = 3.14159265f
```

You can access a class member without a reference to an instance. You
can access a class member using the class name followed by the member access
operator (`.`) and the name of the member.

Here is an example that calculates the area of a cirlce. It demonstrates
accessing the class variable from the previous example.
```
// CircleArea.zen
function main(...arguments)
    var radius = promptFloat('Enter the radius: ')
    var area = Circle.PI * radius * radius
    printf('The area of the circle with radius %f is %f.\n', radius, area)
```

You cannot use an instance of a class to access its class members. This design
choice was made to improve code clarity.