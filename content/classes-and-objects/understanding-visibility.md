+++
title = "Understanding Visibility"
weight = 3
+++

You can control whether the world outside your class can access its members.
This is known as visibility of the member. In other words, you can expose only
certain members to public, that is the world outside your class, while keep other
members private or secret. Thus, you can control the access of your members.
The visibility modifiers are a form of encapsulation in Zen.

You will use visibility modifiers very often. There are three visibility levels
in Zen.

 * Public
 * Private
 * Secret

The visibility modifiers determine which members of your class are visible
to other classes. With access control, you can tell the compiler how your class
can be used by other classes. You can use only one visibility modifier at a time.

## Private Access

You can use the private modifier to hide a class member from all the other classes.
In other words, a private member is accessible only within its class.

Some members of a class are useful only within the class. There is no point in
such members being accessed from other classes. In such cases, you should always
use the private modifier. 

In fact, fields are marked as private by default. You will learn more about this
later in this chapter.

## Secret Access

A secret member is accessible to the following two groups.
    * Subclasses of a class
    * Other classes in the same package

You will learn more about subclasses and packages later in this manual.

## Public Access

In some cases, you want your class members to be completely visible to the
outside world. In other words, any class can access the member.

You can use the public modifier to make a member completely visible to all
the classes. Unlike fields, functions are `public` by default.

In fact, you have already used the public modifier from the beginning of this
course implicitly.

The `main()` function of an application has to be public. Otherwise, it cannot
not be invoked by the Zen Virtual Machine (ZVM).