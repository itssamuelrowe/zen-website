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
called the object’s state. Unlike an objects identity, the state can change over
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