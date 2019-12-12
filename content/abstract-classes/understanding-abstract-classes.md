+++
title = "Understanding Abstract Classes"
weight = 1
+++

In a class hierarchy, the classes at the top are abstract in their definitions
because these classes can define behavior and attributes common to all the
classes below them. Classes with specific behavior and attributes are usually
at the bottom of the hierarchy.

When you design a class hirerarchy, your first step is to factor out the common
behavior and attributes common to all the classes. In some situations you may
find yourself with a very abstract behavior, which prevents you from providing
a general implementation. Classes with such behavior are known as abstract classes.

Consider the following class which represents a shape.
```
class Shape

    @Property
    var color

    function getArea()
        return 0.0

    function getPerimeter()
        return 0.0
```

Imagine the shape is a graphical component. Thus, every shape has area, perimeter,
and say a color. The color attribute has corresponding accessors, thanks to the
`@Property` annotation. Given area and perimeter depend on variables defined by
the subclasses, we cannot implement their accessors.

At this level in the class hierarchy, you cannot provide general functions that
can calculate both area and perimeter for all shapes. Because each shape has
different formulas for area and perimeter. Even if you manage to find a work
around for a few shapes, you cannot keep all the shapes happy. This is why you
create dummy functions that always return zero. In the sense, these functions are
examples of abstract behavior.

However, the `Shape` class should never be instantiated directly because
some of its functions are dummies incapable of calculating anything. It makes no
sense to instantiate a class that is incomplete.

In order to tell the compiler that this class is incomplete and should not
be allowed to instantiate, we need to mark it as abstract. You can add the
`abstract` modifier to the class declaration to mark it as an abstract class.

In order to declare an abstract function, you need to add the `abstract` modifier
to all the abstract functions. You do not have to provide a body to abstract
functions. Instead terminate the declaration with a newline.

Here is the general form of an abstract function.

```
modifiers abstract function name(parameters)
```

Here, the valid modifiers are `public` and `secret`. You cannot declare an abstract
function as `private`, `final`, `native`, or `static`. You cannot mark private
functions as abstract because the subclasses cannot implement private functions
because they would be inaccessible to begin with. Similarly, you cannot mark
abstract functions as final because final functions cannot be overridden.

Abstraction is a concept associated with instance members of a class.
When an instance member is invoked, Zen uses a mechanism known as dynamic
function dispatch, which means Zen determines which instance function you are invoking
at runtime. Zen determines which static function you are invoking at compile time.
Which means, invocation of static functions works differently. Therefore, you
cannot mark a `static` function as abstract.

An abstract function constitutes of the function signature with no implementation.
It serves as a placeholder so the subclasses can implement it. You cannot declare
an abstract function inside a class that is not abstract.

Here is an abstract version of the `Shape` class.
```
abstract class Shape

    @Property
    var color

    abstract function getArea()

    abstract function getPerimeter()
```

In this example, the `getArea()` and `getPerimeter()` functions are abstract.
Which means, you will not be able instantiate the `Shape` class. If you try
to instantiate it with the `new` operator, the compiler generates errors.

Abstract classes can contain anything a normal class can contain, including
constructors, static initializers, and functions. Subclasses which extend abstract
classes inherit superclass members as usual.

You do not have to declare all the functions in an abstract class as abstract.
A class can provide implementation for some of its functions. In fact,
you can declare a class as abstract even when it has no abstract functions.
In which case, the class cannot be instantiated unless it is extended.

Here is an example of a `Rectangle` class which extends the `Shape` class.
```
class Rectangle extends Shape

    @Property
    var length

    @Property
    var breadth

    @Override
    function getArea()
        return length * breadth

    @Override
    function getPerimeter()
        return 2 * (length + breadth)
```

When you inherit an abstract class, you need to implement the abstract functions.
If your subclass is also incapable of implementing general behavior for its
subclasses, you can declare it as abstract. In which case, you do not have to
implement the abstract functions you inherited. Further, you can add other abstract
functions.

In fact, an abstract class can appear at any level in a class hierarchy. When
you want to instantiate it, you need to extend it and implement the abstract
functions.