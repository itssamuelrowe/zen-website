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