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