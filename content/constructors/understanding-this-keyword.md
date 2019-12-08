+++
title = "Understanding this Keyword"
weight = 1
+++

In the body of a function, constructor, or initializer block, sometimes you need
to refer to the object that contains the instance member in question.
In other words, sometimes an instance member may want to access the instance
it is contained in. In such cases, you can refer the instance using the `this`
keyword. It always represents the instance within which the instance member is
contained.

To refer to the instance in an instance function, use the `this` keyword where
you normally would refer to an object's reference through a variable. You can use
the `this` keyword as a reference anyway you please. In other words, the
`this` keyword refers to the current object, and you can use it anywhere a
reference to an object might appear.

Here is a some situations where you can use the `this` keyword:
 * with the member access operator
 * as an argument to a function or constructor
 * as the return value for a function, and so on.

In fact, whenever you refer to instance members in functions and constructors
with just their names, an implicit `this` reference is present. Which goes to say,
you can only use the `this` keyword in instance members. You cannot use the
`this` keyword in static contexts, such as static functions and static initializers.

A very common place where the `this` keyword is used is when you have a
local variable and a field with the same name. Yes, this is possible
because fields and local variables have different scopes.

Here is an example function which sets the score of a player.
```
class Player
    ...

    var score

    function setScore(score)
        score = score

    ...
```

In this example, we are trying to assign the parameter `score` to the field
`score`. When you refer `score`, the program looks up for the variable named
`score` from the nearest scope to farthest scope. In this example, the local
scope is the nearest scope, where the parameter `score` is declared. Which means,
the parameter `score` gets assigned to itself leaving the `score` field unchanged.

In order to override this behaviour, we refer to the field by explicitly adding
the `this` keyword to reference the current object.

Here is the modified version of the previous example.

```
class Player

    ...

    var score

    function setScore(score)
        this.score = score

    ...
```

You can skip the `this` reference if the parameter and the field do not have
the same name.