+++
title = "Superclasses and Subclasses"
weight = 11
chapter = true
+++

### Chapter 11
# Superclasses and Subclasses

Inheritance is a very important feature of object-oriented programming,
a mechanism which allows one class to inherit the behaviors and attributes
from another class. Inheritance allows you to create a hierarchy of classes.
Thus, it has a direct impact on the design of your programs.

To represent a hierarchy, you can create a class that defines characteristics
common to a group of objects. Using inheritance, this class can then be inherited
by other classes which are more specific.

In this chapter, we will learn about inheritance, its mechanisms, and applications.
We will see how to extend superclasses, the behavior of constructors in class hierarchies,
their invocation, and much more.




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


+++
title = "The Object Class"
weight = 2
+++

Inheritance is comparable to how you inherited traits such as your height,
eyes, hair, DNA, and allergies from your parents. They in turn inherited
some of their traits from their parents, that is, your grandparents. Inheritance
of such tratis basically keeps going backwards in time till the very first people
who populated Earth, say Adam and Eve, the root of your ancestorial hierarchy.

Similarly, every class hierarchy has a root class. All the class hierarchies in
Zen have the same class as their root class: the `Object` class. When the extends
clause is absent, an implicit extends clause inheriting the `Object` class is
provided by Zen.

In Zen, the `Object` class is the root of class hierarchy. In other words,
the `Object` class is the superclass of all classes in Zen.

The `Object` class is special because it is the only class in Zen that does not
inherit any other class.

The `Object` class defines the following functions, which means that they are
available in every object.

  * The `clone()` function creates a clone of the object is being invoked against.

  * The `equals()` function determines whether one object is equal to another object.
    It compares two objects and returns `true` if both are same, otherwise it
    returns `false`.

  * The `finalize()` function is invoked by the Zen Virtual Machine (ZVM) before
    the object is destroyed.

  * The `getClass()` returns an object which represents the class of an object
    at runtime. This function is part of the reflection API, which allows you to
    dynamically load classes, create instances, and invoke functions. It is a
    final function and cannot be overridden.

  * The `hash()` function returns the hash code of the object.

  * You have already seen the `toString()` function. It returns a string that
    describes the object.

    +++
title = "Overriding Functions"
weight = 3
+++

A subclass inherits all the behavior and attributes of its superclass. It can then
extend the behavior and attributes of its superclass. In fact, a subclass can
change the behavior provided by its superclass. This is known as *overriding*.
Overriding functions is a feature of polymorphism. In this section, you will learn
about overriding functions.

When you call an instance function, Zen looks for the definition of the function
in the object's class. If it does not find it, Zen looks up for the function
in its superclasses, all the way to the `Object` class, until the function definition
is found. If the definition is not found, the function is considered as non-existent
and the virtual machine throws an exception. You will learn more about exceptions
in the upcoming chapters.

Inheritance allows you to define functions in superclasses and use them in
instances of your subclasses. This helps you avoid rewriting the code in your
subclasses. However, sometimes you may want to invoke a function but change its
behavior which was defined in a superclass. In such cases, you can alter it. This is
known as function overriding.

To override a function in a subclass you simply need to define the function
in your subclass with the same signature and return type. Zen determines if
a function is overridden by comparing the signature of your function in the subclass
and the superclass. If the signatures match, then that function is considered as
overridden. When you invoke that function, the overridden version is executed instead
of the one in the superclass.

Consider the following example which prints the popular lines of the characters
from Friends.

```
// Friends.zen

class Friend

    function getPopularLine()
        return 'F.R.I.E.N.D.S is the best show ever, isn\'t it?!'

class JoeyTribbiani extends Friend

    @Override
    function getPopularLine()
        return 'How you doin\'?'

class ChandlerBing extends Friend

    @Override
    function getPopularLine() {
        // PS: Could Chandler be more funny?
        // This is the only program I have ever written laughing.
        return 'Until I was 25, I thought that the only response to "I love you" was "Oh crap!"'

class PhoebeBuffay extends Friend

    @Override
    function getPopularLine()
        // That's it. I'm off to watch Friends.
        return 'They don\'t know that we know they know we know.'

function main(...arguments)
    var joey = new JoeyTribbiani()
    print('Joey: ' + joey.getPopularLine())

    var chandler = new ChandlerBing()
    print('Chandler: ' + chandler.getPopularLine())

    var phoebe = new PhoebeBuffay()
    print('Phoebe: ' + phoebe.getPopularLine())
```

When you compile this example, the compiler produces fives files, one for each
class. The output of the program is shown here.

```
Joey: How you doin'?
Chandler: Until I was 25, I thought that the only response to "I love you" was "Oh crap!"
Phoebe: They don't know that we know they know we know.
```

The `Friend` class defines a function called `getPopularLine()`. It always
returns the string `'F.R.I.E.N.D.S is the best show ever, isn\'t it?!'`.

To demonstrate function overriding, we created three other classes called
`JoeyTribbiani`, `ChandlerBing` and `PheobeBuffay` which inherit the `Friend`
class. Each of these classes define the `getPopularLine()` function with the same
signature. Thus, they override the `getPopularLine()` function in their respective
classes.

Sometimes you may misspell a function name or change the signature by accident in
your subclass. Since Zen does not force your subclass to override the definition
of a function, you may end up creating a new function instead of overriding a function
that exists in your superclass.

You always need to make sure that you have correctly overridden a function. Zen
provides an annotation called `Override`. With this annotation you can tell the
compiler to check if you have correctly overridden a function.

An annotation is a special class that provides supplemental information
about your source code. They are similar to comments, except they are not ignored
by the compiler. Annotations start with `@`. They provide information about your
source code to tools such compilers. You will learn more about annotations in the
upcoming chapters.

In the `main()` function we create an instance of each of the subclasses of `Friend`.
We assign the instances to their respective variables.

You can prevent a subclass from overriding a function. You simply need to add
the `final` keyword in the function declaration. When a subclass tries to override
a final function, the compiler generates errors.

Here is an example of a final function.
```
final function printStatistics()
    ...
```

Zen provides a special operator called as `is` operator. It allows you
to determine whether an object is an instance of the specified class.

Here is the general form the instance of operator.
```
object.class is Class
```

Here, the `object` represents the object you want to test. The `is` operator
is a keyword. The `Class` represents the class the object should
be an instance of.

Here is an example.
```
if friend.class is ChandlerBing
    print('It is Chandler!')
else
    print('I don\'t know who this is. Is it Monica?')
```


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

+++
title = "Understanding the Extended Self Reference"
weight = 5
+++

You have already seen how the `this` reference works. It provides a reference to
the current instance. You can use it distinguish between a local variable and an
instance variable with the same name.

Sometimes you may want to distinguish between a subclass instance member and
a superclass instance member. In such cases, you can use the extended form of the
`this` keyword known as the extended self reference. You can reference a superclass
directly above the current subclass in the hierarchy.

A very common place where the extended form of the `this` keyword is used is
when you override a function and you want to invoke the function defined in the
superclass.

Here is an example, where the superclass reference is used.
```
class A

    function printMessage()
        print('This is the function defined in the superclass.')

class B extends A

    @Override
    function printMessage()
        A.this.printMessage()
        print('This is the function defined the subclass.')
```

In Zen, you cannot shadow fields, that is, a subclass cannot declare a public
field with the same signature as another public field that is already present
in a superclass. This design choice was made because it shadowing fields makes
your code less readable. Although this does not matter, if the fields are private
in the first place, because private fields are not inherited.

The compiler generates errors if you try to compile the following example.
```
class A

    public var message = 'This is the superclass message.'

class B extends A

    public var message = 'This is the subclass message.'
```