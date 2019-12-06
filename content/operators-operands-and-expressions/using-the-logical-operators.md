+++
title = "Using the Logical Operators"
+++

You can combine two or more conditions or constraints or complement with logical
operators. The result of the operation of a logical operator is a Boolean value,
either `true` or `false`.

## Logical AND Operator

The logical AND operator combines two Boolean expressions and returns `true`
if both the expressions evaluate to `true`. Otherwise, it returns `false` for
the given expressions.

The general form of the logical AND operator is shown here.
```
expression1 && expression2
```

Here, `expression1` and `expression2` must evaluate to Boolean values. The
result of the above operation `expression1 && expression2` will be
 * `true` if both the operands are `true`
 * `false` if any of the operands is `false` or both the operands are `false`.

For example, consider the following statements.

```
var value1 = 10
var value2 = 20
var value3 = 30
var result = value2 > value1 && value2 < value3
```

Can you guess the value stored in `result`? It will be equal to `true`, because
`value2` is greater than `value1` and `value2` is lesser than `value3`.

The logical AND operator is similar to the bitwise AND operator. In fact, you
could use the bitwise AND to combine Boolean conditions. However, the logical
AND leverages your knowledge of logic.

We know that both expressions compared by the logical AND operator must be `true`
for the entire expression to be `true`. There is no reason to evaluate the
second expression if the first one returns `false`. The logical AND leverages
this idea and skips the evaluation of the second expression, if the first expression
evalutes to `false`. On the other hand, the bitwise AND operator is not aware of
this fact, so it blindly evaluates both expressions before determining the results.
The logical AND operator is smart enough to stop when it knows what the result is.

Programmers almost always use logical AND instead of bitwise AND for combining
conditions. In fact, you should do the same. Because sometimes the expressions
have significant side effects.

For example, the second expression may delete a file. But what if the file
was supposed to be deleted only if the first condition was true? The bitwise
AND does not stop when the first condition is `false`, deleting the
file. With a logical AND, the operator does the work for as expected.

Relying on the side effects of expressions can be risky. In fact, you can almost
always find a better way to write your code without side effects.

## Logical OR Operator

The OR operator combines two Boolean expressions and returns `true`
if at least one of the expressions evaluates to `true`. Otherwise, it returns
`false` for the given expressions.

The general form of the logical OR operator is shown here.
```
expression1 || expression2
```

Here, `expression1` and `expression2` must evaluate to Boolean values. The
result of the operation `expression1 || expression2` will be
 * `true`if at least one of the operands is `true`
 * `false` if both the operands are `false`

For example, consider the following statements.

```
var value1 = 10
var value2 = 20
var value3 = 30
var result = value2 < value1 || value2 < value3
```

Can you guess the value stored in `result`? It will be equal to `true`. Since
`value2` is greater than `value1`, it evaluates to false. Then `value2` is lesser
than `value3` evaluates to `true`. Thus, `result1` evaluates to `true`.

The logical OR operator is similar to the bitwise OR operator. In fact, you could use
the bitwise OR to combine Boolean conditions. However, the logical OR leverages your
knowledge of logic.

We know that at least one of the expressions compared by the logical OR operator must be
true for the entire expression to be `true`, there is no reason to evaluate the
second expression if the first one returns `true`. Whereas, the bitwise OR operator
is not aware of this fact, so it blindly evaluates both expressions before determining
the results. The logical OR operator is smart enough to stop when it knows what the
result is.

Therefore, programmers almost always use logical OR instead of bitwise OR
for combining conditions. In fact, you should do the same.
Because sometimes the expressions have significant side effects.

For example, the second expression may delete a file. But what if the file
was supposed to be deleted only if the first condition was false? The bitwise
OR does not stop when the first condition is `true`, deleting the
file. With a logical OR, the operator does the work for as expected.

Again, relying on the side effects of expressions can be risky.
In fact, you can almost always find a better way to write your code without
side effects.

# The Logical NOT Operator

The simplest of the logical operators is the logical NOT operator. It is a unary
prefix operator, which means you can use it with only one operand and you write it
immediately before its operand.

This operator is also called as the complement operator.

The logical NOT operator reverses the value of a Boolean expression. Thus, if the
expression is `true`, the operator changes it to `false`. If the expression is `false`,
the operator changes it to `true`.

Here’s an example.

`!(day == 7)`

This expression evaluates to `true` if `day` is any value other than `7`.
If `day` is `7`, it evaluates to `false`. It works by first evaluating the
expression `(day == 4)`, after which it reverses the result of the evaluation.
Do not confuse the logical NOT operator `!` with the NOT equals relational
operator `!=`.

The preceding example could have be written like this, too. The result will be
the same.
```
day != 4
```

The logical NOT operator is more general. It can be applied to any expression
that returns a Boolean result, not just an equality expression.

You must almost always enclose the expression that the logical NOT `!` operator is
applied to in parentheses.

Consider the following expression.
```
!i == 6
```

Assume that `i` is a variable holding an integer value. The compiler does not
generate any error about this expression. However, during runtime an exception
will be thrown because it looks like you are trying to apply the logical NOT
operator to the variable, not to the result of the comparison. Enclosig the
comparison with parentheses solves the problem.
```
!(i == 6)
```