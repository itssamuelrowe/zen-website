+++
title = "Understanding Inheritance"
weight = 1
+++

Inheritance is a concept of object-oriented programming. You can derive a class
from another class with inheritance.

A class that you inherit is known as *parent class*, or *base class*, or
*superclass*.

A class which inherits is known as *child class*, or *derived class*, or
*subclass*.

Imagine you have a class that already has behavior and attributes that another
class needs. You do not have to rewrite or copy your code to have the same behavior
and attributes. With inheritance, your class automatically receives the behavior
and attributes from its superclass. Basically, a class becomes a combination of
its own features and all the features it inherits from the classes above it in
the hierarchy.

To inherit a class, you simply specify the class to inherit in the definition
of your class using the extends clause. The general form of the extends clause
is shown here.

```
class A extends B
    ...
```

Here, `A` represents the name of your class. `B` represents the name of the
you want to inherit. In other words, `A` represents the name of the subclass
and `B` represents the name of the superclass.

A class can have one or more superclasses. This type of inheritance is called
multiple inheritance because each class can have one or more superclasses.

In other object-oriented programming languages such as Zen, classes can have
only one superclass. This is called single inheritance. Zen makes inheritance
simpler by allowing only single inheritance.

With inheritance, you can implement *is-a-type-of* relationships. Here are some
examples.
    * Cricket is a type of game.
    * A tiger is a type of animal.
    * A duck is a type of bird.
    * A mango is a type of fruit.

Here is an example that demonstrates the hierarchy of shapes.

```
// ShapeExample.zen

class Shape

    @Property
    var area
    
    @Property
    var perimeter

class Square extends Shape

    @Property
    var side
    
class Rectangle extends Shape

    @Property
    var length

    @Property
    var breadth

class Circle extends Shape

    var radius

function main(...arguments)
    var square = new Square()
    square.setArea(100)
    square.setPerimeter(40)
    square.setSide(10)
    print(serialize(square, 'json'))

    var rectangle = new Rectangle()
    rectangle.setArea(70)
    rectangle.setPerimeter(34)
    rectangle.setLength(7)
    rectangle.setBreadth(10)
    print(serialize(rectangle, 'json'))

    Circle circle = new Circle()
    circle.setArea(314.28)
    circle.setPerimeter(62.85)
    circle.setRadius(10)
    print(serialize(circle, 'json'))
```

In this example, we demonstrate an hierarchy of shapes. Consider three shapes:
squares, rectangles, and circles.

To represent shapes, you can create a class named `Shape`. It describes features
common to all shapes, such as area and perimeter. Being the good citizens of
the Zen world, you make these fields private and thanks to the `@Property` annotation
Zen creates accessors to expose them consistently.

We know that a square is a type of shape. Obviously, it has properties such
as area and perimeter. Instead of rewriting the accessors and fields to implement
these properties, you simply inherit the `Shape` class. Of course, `Square` has
`side`, which describes the length of its sides. Thus, we extend the features of
`Shape` by adding the field and accessors for `side`.

Similarly, a rectangle is a type of shape. It extends the `Shape` class to inherit
the `area` and `perimeter` attributes and their corresponding accessors.
A rectangle has four sides, with equal opposite sides known as length and breadth.
Therefore, we extend the features of `Shape` by adding these two fields and their
corresponding accessors.

In the `main()` function, we create an instance of `Square`, `Rectangle`, and
`Circle`. Although, we did not create accessors for area and perimeter
in these classes, we are still able to invoke their accessors because these
methods were inherited by them.

The `Square`, `Rectangle`, and `Circle` classes have is-a-type-of relationship
with the `Shape` class because they are all a type of shape.

You know that private fields are accessible only within the class they are declared.
Which means, when you inherit a class with private fields, you will not be
able to access them. In other words, private fields are not inherited by classes.
When you create an instance of the subclass, the instance is a combination of
the subclass and all the superclasses. Which goes to say the instance gets its
own copy of all the fields, including private fields declared throughout the
hierarchy. But they are only accessible by the classes in which they were
declared.

In order to access a field declared in a superclass from a subclass, the field
must be either declared as public or secret. If you declare the field as public,
any class can access it. If you want to limit the visibility of the field
only to your class hierarchy, declare it as secret. You must remember that
secret fields are accessible by other classes in the same package even if
they are not a part of your hierarchy.

You can inherit a class that inherits another class. Thus, inheritance forms
an hierarchy. Here is an example.

```
class Vehicle
    
    @Property
    var license
    
    @Property
    var make
    
    @Property
    var model

class Car extends Vehicle

    @Property
    var seats

    @Property
    var wheels

    @Property
    var passengers

class Sedan extends Car
    ...

class Hatchback extends Car
    ...
```