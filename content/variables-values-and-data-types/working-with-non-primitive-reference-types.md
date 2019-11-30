+++
title = "Working with Non-Primitive Reference Types"
+++

In this section, you will learn about the basics of non-primitive reference types.
You learn to create variables that work with objects.

The rules that apply to these types also apply to primitive reference types.

> You will learn more about classes and objects later in the course.

Zen programs are built with classes. You can use classes to create objects.
A reference type is a type which references an object. The class can be any class.
It can either be a part of the Zen standard API or a class that you create.

When you create an object, you allocate memory to store the object. Here's an
example of how you can create an object.
```
new Object()
```

When you store the object in a variable, you assign a *reference* to the object.
You don't store the object itself.

A reference is the location of an object in memory. References are similar to
pointers in C or C++. Unlike pointers, references are simple and easy to use.

For example, think that you are writing a program which involves cars.
You have a class named `Car` which defines the behavior of a car.
You can declare a variable that stores a reference to a `Car` object like
this.
```
var car
```

Here, the variable `car` can hold any type of object, including `Car` objects.

To create a new *instance* of a class, you can use the `new` keyword. You have
to tell `new` the class whose instance you want. When you create an instance of
a class, you actually call a *constructor*. The constructor initializes the new
object.

> You do not have to understand these concepts right away. You will understand
> them when you learn about them in detail.

Here's an example where we create an instance of the class `Car`.
```
new Car()
```

You can assign a reference to the new object as shown below.
```
var car
car = new Car()
```

You can combine both these statements like this.
```
var car = new Car()
```

Remember that a reference variable does not actually store an object.
It stores only the reference to an object in memory. As a result, two or more
variables can refer to the same object.

Here's an example where two variables refer to the same `Car` object.
```
var carX = new Car()
var carY = carX
```

Here, we have declared two variables, named `carX` and `carY`. But we have
created only one `Car` object.

We first created a `Car` object and assigned its reference to `carX`. Then
the same reference is assigned to `carY`. This way, both `carX` and `carY`
refer to the same object.