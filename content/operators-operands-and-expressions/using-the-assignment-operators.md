+++
title = "Using the Assignment Operators"
+++

The assignment operator helps you assign a value to a variable. You have
already seen many examples of this operator. **It assigns the value on its
right to the operand on its left.**

For example, here's an example of the assignment operator in use.
```
var vehicles
var cars = 100
vehicles = cars
```

In the above example, we created a variable named `vehicles`. Think that
it stores the number of vehicles you own. We also created another variable
named `cars`. Think that it stores the number of cars you own.

When we say `vehicles = cars`, we are storing the value stored in `cars`
to `vehicles`, because the assignment operator assigns the value on its
right to the operand on its left.

Your expression on the left hand side, known as the lvalue, should be capable
of storing a value.

For example, the following statement does not compile.
```
a + b = c * d
```

Because the expression on the left hand side evaluates to a value.
A value simply cannot store another value.

Before we continue with the other concepts of the assignment operator, you need
to understand that an assignment in Zen is simply an expression and not a statement.

For example, `a = 7` is an expression. It becomes an expression statement only
when you add a newline to the end like this.

```
a = 7

```

An operator always returns a result. In that case, what does the assignment
operator return? It returns the value that it assigned to a variable.

For example, the result of `s = 7` evaluates to `7`.

Similarly, the expression `r = (a * a) - (b * b)` returns the result of the
expression `(a * a) - (b * b)`.

So, what is the use of the assignment operator returning a result?
Well, this allows us to use multiple assignments in the same expression.

Consider the following code snippet.
```
a = 10
b = a
c = b
```

You could rewrite the above code snippet like this:
```
a = b = c = 10
```

Given, the associativity of the assignment operator is right-to-left, first
`c = 10` is evaluated. It returns `10`, which is assigned to `b`. Again, `b = c`
returns `10` which is assigned to `a`. Thus, all the variables are assigned to `10`.

Now, consider another complicated case.

```
b = 7
a = (b = 9) + 10
```

As in any expression, the expression inside the parenthesis is evaluated first.
Here, `b` is assigned to `9`. Since an assignment returns whatever was assigned,
in this case `9` is returned. The `9` is then added to `10`. The result, that is
`19`, is then stored in `a`.