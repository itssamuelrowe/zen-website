+++
title = "Introduction to Object Oriented Programming"
chapter = true
weight = 8
+++

### Chapter 8
# Introduction to Object Oriented Programming

Zen is a pure object-oriented programming language. When you work with Zen, you
primarily use objects to get things done. You create objects, modify them,
change their attributes, call their methods, and combine them with other objects.

This chapter is a simple introduction to object-oriented programming. It
introduces some of the basic concepts and terms you need to know before
moving to the following chapters.

Some concepts in this chapter are confusing. Do not worry, if you do not get
them right away. By the end of this manual you will be comfortable with these
concepts.

+++
title = "Understanding Object Oriented Programming"
weight = 1
+++

Object-oriented programming is a programming language paradigm or model.
In this model, programs are organized around data, also known as objects.
Zen is unlike languages such as C, a Procedural Oriented Language (POL), in which
the programs are organized around functions and logic.

An object is simply data that has attributes and behavior.

An example of an object is a human being. A human being has properties like
name, date of birth, and gender.

Another example of an object is a button that you see on your computer. It has
properties such width, height, background color, foreground color, and text.

In other words, objects — both in the real world and in the world of programming —
are entities that have certain basic characteristics.

The basic characteristics of objects are as follows.
 * Identity
 * State
 * Behaviour

We will discuss each of them briefly in this section.

## Identity

Every object has an identity, both in the real world and the programming world.

Imagine you own a Lamborghini Aventador and you parked it before you went shopping.
When you returned after shopping, you find two Lamborghini Aventadors
parked next to each other. It so happens both the cars have the same color and
are identical. Obviously, you own one of them and somebody else owns the other
Aventador.

How do you recognize your car? Of course, there are a number of ways you can
*identify* your car. For one, you could take a peek at your number plate.
Since a number is unique to every instance of car in your region, you can
easily identify your car.

Similarly, in the programming world each instance of an object can be identified
by its reference. A reference is usually an address where the instance resides
in memory.

We mentioned the term instance a couple of times. So what exactly does it mean?

An instance is simply an existence or occurrence of an object.

The process where you create an instance of an object is known as instantiation.

For example, the Lamborghini you own is an instance of Lamborghini Aventador,
the object. Similarly, the Lamborghini parked next to yours is yet another
instance, where Lamborghini Aventador is again the object.

Think of it this way, an object is simply an idea, an instance is the
idea brought to life, and the process of bringing the idea to life is
instantiation.

## State

The state determines the attributes of an object. For example, a car can have
the attributes such as speed, RPM, gear, fuel level, and engine temperature.

The type of an object determines what attributes the object has. Thus, all
instances of a particular object have the same attributes. But there is no
guarantee that all the instances have the same attributes.

When we say type, we actually mean a class. We will learn more about classes
in the next chapter.

From the parking lot example, your Lamborghini may have a different fuel
level than the Lamborghini parked next to yours.

The combination of the values assigned to all the attributes of an object is
called the object's state. Unlike an objects identity, the state can change over
its lifetime.

For example, the engine temperature of your Lamborghini may heat up and cool
down during its lifetime. Similarly, the fuel level can increase and decrease.

## Behavior

The behavior of an object is simply the capabilities of an object. Like state,
the behavior of an object depends on its type.

Unlike state, behavior is not different for each instance of an object.

For example, a car is capable of moving, which is a behavior. All cars
are capable of moving. Which goes to say, behavior is not different from instance
to instance.

+++
title = "Advantages of Object-Oriented Programming"
weight = 3
+++

In this section, we will learn about the advantages of Object Oriented Programming (OOP).

## Reusability

Reusability allows us to reuse available facilities rather building it again
and again. This is done with the use of a class. You can use it any number of
times. Thus, your productivity is improved.

## Maintenance

Code maintainance is a necessity for any programming languages. Object Oriented
Programming allows programmers to refactor code in many ways.

## Security

With the use of data hiding and abstraction mechanism, you limit data exposure
to the world outside your class. This reduces accidental modification of your
data.

## Problem Solving

Decomposing a complex problem into smaller components is a good practice.
Object Oriented Programming is specialized in this style, as it breaks down
your problem into objects.

In fact, these objects can be reused in creating solutions to different problems.

+++
title = "Principles of Object Oriented Programming"
weight = 2
+++

Object oriented programming is based on the following principles.

 * Class
 * Object
 * Inheritance
 * Abstraction
 * Encapsulation
 * Polymorphism

We will briefly discuss each of these principles in this section. In the next
few chapters we will learn about them in detail with their applications in Zen.

## Understanding Classes

A class is a collection of objects of similar type. Once a class is defined,
any number of instances can be created which belong to that class.

The class is at the core of Zen. It defines the shape and nature of an object.
Any concept you wish to implement in a Zen program must be encapsulated within
a class. In fact, the next few chapters are dedicated to classes and the components
that go with it.

## Understanding Objects

Objects are the basic runtime entities in an object-oriented system.
Programming problem is analyzed in terms of objects and nature of communication
between them. When a program is executed, objects interact with each other by
sending messages. Different objects can also interact with each other without
knowing the details of their data or code.

## Understanding Inheritance

Inheritance allows a class to derive features of another class. The existing
class is called the *base class*, *superclass*, or *parent class*. The new
class is called the *derived class*, *subclass*, or *child class*.

When a class inherits, the members of the parent class are derived. You can
change their behavior, or just use them as is it is. You can extend the behaviour of
the parent class.

## Understanding Abstraction

Abstraction refers to representing essential features without including the
details or explanations.

For example, both a Lamborghini and Ferrari have steering wheel and accelerator.
Internally, the mechanisms for steering and acceleration are different but
anybody who knows to drive a car can drive both the cars without having to
worry about the internal details.

## Understanding Encapsulation

## Understanding Polymorphism

Polymorphism refers to the ability to take more than one form.

Here is a real life example of polymorphism, where a person can have different
characteristics based on the viewers perspective. Consider a woman who is a
mother, an actress, and owns a bank account. As you can see, the same person
posses different behavior from different perspectives. This is called polymorphism.

Polymorphism is an important feature of Object Oriented Programming (OOP).