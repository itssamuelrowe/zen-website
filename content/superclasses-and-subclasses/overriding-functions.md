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