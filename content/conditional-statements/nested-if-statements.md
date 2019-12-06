+++
title = "Nested If Statements"
+++

You can write any statement under the *if* and *else* clauses.
In fact, you could write another if statement under them.
This is known as nesting. So, if you write an *if statement* inside
another *if statement*, we call the arrangment as *nested if statements.*

The *if statement* written inside another *if statement* is called the
*inner if statement*.

Similarly, the *if statement* which contains another *if statement* is
called the *outer if statement*. 

*Nested if statements* are very common in programming. When you nest
*if statements*, you must always remember that the *else clause* is
associated with the nearest *if clause*.

You can nest any number of *if statements* to any depth. We recommend you to
keep it as simple as possible. Also, be sure to use indentation to indicate the
structure of the nested statements.

Here is the general form of a nested if statement.

```
if condition1
    if condition2
        statement1
    else
        statement2
else
   if condition3
        statement3
    else
        statement4
```

Remember, you construct a *nested if statement* with regular *if statements*.
So, you don't have to use *if statements* under both the clauses
if you don't have to. Again, all the *else clauses* are optional.