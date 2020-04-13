+++
title = "Operators, Operands, and Expressions"
weight = 4
+++

In this module, you will learn about operators, operands, and expressions.

An operator is a special symbol or a keyword that performs a mathemtical operation
or a specific operation. Generally, an operator expects one, two, or three values
known as operands. You must always remember, an operator always calculates and
returns a result.

A common way to categorize Zen's operators is by the number of operands the
operator expect. There are three types of operators based on the number of
operands they accept.
 * Unary Operators
 * Binary Operators
 * Ternary Operators

## Unary Operators

Unary operators are operators that expect one operand. A unary operator can be
a prefix operator or a postfix operator.

A prefix operator is written before the operand, like this:
```
operator operand
```

A postfix operator is written after the operand, like this:
```
operand operator
```

## Binary Operators

Binary operators are operators that expect two operands. All the binary operators
are infix operators, which means they appear between the operands, like this:
```
operand1 operator operand2
```

## Ternary Operators

Ternary operators are operators that expect three operands. The conditional
operator is the only operator in Zen that expects three operands. It is also an
infix operator and written like this:
```
operand1 ? operand1 : operand2
```

### Working with Arithmetic Operators

You can perform addition, subtraction, multiplication, and division with the
arithmetic operators. They are similar to operators in basic mathematics.

| Operator | Description                  |
|----------|------------------------------|
| +        | Addition                     |
| -        | Subtraction                  |
| *        | Multiplication               |
| /        | Division (returns quotient)  |
| %        | Division (returns remainder) |

#### Addition

The addition operator, written as plus `+` accepts two operands. It adds both the operands
that you specify and returns their sum as its result. You can add two
constants, a constant and a variable, or two variables.

Here's an example.
```
var age = 10
var ageAfter10Years = age + 10
```

#### Subtraction

The subtraction operator, written as minus `-` accepts two operands. It subtracts the
second operand from the first operand. You can subtract a constant from
another constant, a constant from a variable, or a variable from another
variable.

Here's an example.
```
var age = 10
var ageBefore10Years = age - 10
```

#### Multiplication

The multiplication operator, written as asterisk`*` accepts two operands. It multiplies both the operands
that you specify and returns their product as its result. You can multiply two
constants, a constant and a variable, or two variables.

Here's an example.
```
var increment = 1.2
var salary = 10000
var newSalary = increment * salary
```
In algebra, you can write a number next to a variable and
imply multiplication. For example in algebra, `8y` means eight times y. But this is not the case in Zen. You always
need to write the asterisk to indicate multiplication.

#### Division

The division operator, written as forward slash  `/` accepts two operands. It divides one operand
by another and returns the quotient as its result. You can divide two
constants, a constant and a variable, or two variables.

Here's an example.
```
var favorable = 1
var total = 6
var probability = favorable / total
```

When you add two `int` values, the result is an `int` value, even if you assign the result to a `double` variable.

#### Remainder

In Zen, the modulus `%` operator does not calculate percentage. **It divides
one operand by another and returns the remainder as its result.** This operator is known as the modulus operator.
You can divide two constants, a constant and a variable, or two variables.

```
var a = 21
var b = 2
var c = a % b
```

For example, when you divide 21 by 2 the quotient is 10 and the remainder is 1.
Thus, in this example `c` is equal to 1.

### Working with Comparison Operators

| Operator | Description                  |
|----------|------------------------------|
| <        | Returns `true` if the operand on the left is lesser than the operand on the right.                  |
| >        | Returns `true` if the operand on the left is greater than the operand on the
right. |
| <=       | Returns `true` if the operand on the left is  lesser than or equal to the
operand on the right.
 |
| >=       | Returns `true` if the operand on the left is  greater than or equal to the
operand on the right.
 |

### Working with Equality Operators


| Operator | Description                  |
|----------|------------------------------|
| ==       | Equality                     |
| !=       | Inequality                   |

#### Equality

Returns `true` if the operand on the left is the same as the operand on the
right. Please note that this operator compares the content of the left
operand with the content of the right operand, along with the references.

#### Inequality

Returns `true` if the operand on the left is not the same as the operand on the
right. Plese note that this operator compares the content of the left operand
with the content of the right operand, along with the references.

### Using the Unary Plus and Minus Operators

The unary plus and minus operators let you change the sign of an operand.
Note that the symbol used to represent these operators are the same as the
addition and subtraction operators. The compiler figures out which operation
you mean by examining the expression.

Remember, the unary minus operator does not necessarily make an operand
negative. Actually, it inverts the sign of the operand. For example, assume
`x = -5` then `-x` will give you `5`. Mathematically, this is equivalent to
`-x = x * -1`.

Interestingly, the unary plus operator does not actually do anything. For example,
assume `x = -5` and `y = 7` then `+x` and `+y` will give you `-5` and `7`, respectively.
Mathematically, this is equivalent to `+x = x * 1`.

### Using the Logical Operators

You can combine two or more conditions or constraints or complement with logical
operators. The result of the operation of a logical operator is a Boolean value,
either `true` or `false`.

#### Logical AND Operator

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

#### Logical OR Operator

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

#### The Logical NOT Operator

The simplest of the logical operators is the logical NOT operator. It is a unary
prefix operator, which means you can use it with only one operand and you write it
immediately before its operand.

This operator is also called as the complement operator.

The logical NOT operator reverses the value of a Boolean expression. Thus, if the
expression is `true`, the operator changes it to `false`. If the expression is `false`,
the operator changes it to `true`.

Here's an example.

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

### Using the Assignment Operators

The assignment operator helps you assign a value to a variable. You have
already seen many examples of this operator. It assigns the value on its
right to the operand on its left.

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

Your expression on the left hand side, known as the lvalue or left-value, should
be capable of storing a value.

For example, the following statement does not compile because the expression on
the left hand side evaluates to a value. A value simply cannot store another value.

```
a + b = c * d
```

Before we continue with the other concepts of the assignment operator, you need
to understand that an assignment in Zen is simply an expression and not a statement.
For example, `a = 7` is an expression. It becomes an expression statement only
when you add a newline to the end like this.

```
a = 7

```

An operator always returns a result. In that case, what does the assignment
operator return? It returns the value that it assigned to a variable.
For example, the result of `s = 7` evaluates to `7`. Similarly, the expression
`r = (a * a) - (b * b)` returns the result of the expression `(a * a) - (b * b)`.
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

### Using the Compound Assignment Operators

A compound assignment operator is an operator that performs both an implicit
calculation and an assignment.

Here's a list of all the compound arithmetic assignment operators in Zen.

| Operator | Description                              |
|----------|------------------------------------------|
| +=       | Addition and assignment                  |
| -=       | Subtraction and assignment               |
| *=       | Multiplication and assignment            |
| /=       | Division (for quotient) and assignment   |
| %=       | Division (for remainder) and assignment  |

For example, the expression `a = a + 10` can be written as `a += 10`.
Here's another exampe. The expression `b = b * 100` can be written as `b *= 100`.

Here's a list of all the compound bitwise assignment operators in Zen.

| Operator | Description                                 |
|----------|---------------------------------------------|
| \|=       | Bitwise OR and assignment                   |
| &=       | Bitwise AND and assignment                  |
| ^=       | Bitwise XOR and assignment                  |
| <<=      | Bitwise Left Shift and Assignment           |
| >>=      | Bitwise Right Shift and Assignment          |
| >>>=     | Unsigned Bitwise Right Shift and Assignment |

Compound assignment operators can be confusing when used in complex expressions.
Therefore, we recommend you to always compound assignment operators by themselves.

### Using the Conditional Operator

The conditional operator is the only ternary operator in Zen.
It is used to replace certain types of if-then-else statements.
The conditional operator is represented by a question mark (?).
It can seem somewhat confusing at first, but the conditional operator
can be used very effectively once understood.

The conditional operator has the following general form.
```
expression1 ? expression2 : expression3
```

Here, `expression1` can be any expression that evaluates to a boolean value.
If expression1 is true, then expression2 is evaluated; otherwise, expression3
is evaluated. The result of the conditional operator is that of the expression
evaluated.

In Zen, you cannot use 0 as denominator in integer division. Here, is an example
which prevents division by 0 using the conditional operator.
```
result = (denominator == 0) ? 0 : numerator / denominator
```

When Zen evaluates this assignment expression, it first evaluates the expression
in the parenthesis, which is not really necessary. In other words, the expression
to the left of the question mark is first evaluated. If the denominator equals
to zero, then the expression between the question mark and
the colon is evaluated and used as the value of the entire conditional
expression. If denominator is not equal to zero, then the expression after the colon
is evaluated and used for the value of the entire conditional expression. The result
produced by the conditional operator is then assigned to result.

Here is a program that demonstrates the conditional operator. It uses it to obtain the
absolute value of a variable.

```
// ConditionalOperatorExample.zen

function main(...arguments)
    var i = 10
    var k = i < 0? -i : i
    print('Absolute value of i is ' + k)

    i = -7
    k = i < 0 ? -i : i
    print('Absolute value of i is ' + k)
```

The output generated by the program is shown here.
```
Absolute value of 10 is 10
Absolute value of -7 is 7
```

### Working with Bitwise Operators

A computer stores data in binary. In other words, information is encoded as
a sequence of 1's and 0's. On most computers, the memory is organized into 8-bit
cells known as bytes.

Zen defines several operators that allow you to work at the binary level. These
operators perform bit-by-bit (commonly known as bitwise) operations on bit
patterns and involve manipulation of individual bits. Such operators are known
as bitwise operators. These operators can be applied only to integers.

#### The Bitwise AND Operator

The bitwise AND operator combines two bits and returns true
only if both the bits are true. Otherwise, it returns false for
the given bit pair. When we say true and false, we mean `1` and `0`, respectively.
The operator basically combines all the bits in the given operands.
Mathematically, it is written as `Z = X . Y` where `.` implies multiplication.

This operator is called the bitwise AND because the left hand side bit *and* the
right hand side bit must be true for the operator to return true.

Here's the truth table for the bitwise AND operator.

| X | Y | Z |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

In a bitwise operation, the smaller sized operand is padded with zeroes before
the most significant bit to match the larger sized operand.

Consider the following example.

```
// BitwiseAndExample.zen

function main(...arguments)
    var a = 10
    var b = 255
    var c = a & b
    print(c)
```

We know that integers occupy 32 bits. To evaluate the last expression, each bit
of the operands is combined to produce 0 or 1 if the corresponding bits are 1 or
otherwise, respectively.

#### The Bitwise OR Operator

The bitwise OR operator combines two bits and returns true if at least one of
the bits is true. Otherwise, it returns false for the given bit pair. Again,
when we say true and alse, we mean `1` and `0`, respectively The operator basically
combines all the bits in the given operands. Mathematically, it is written as
`Z = X + Y` where `.` implies addition.

This operator is called the bitwise OR because the left hand side bit *or* the
right hande side bit must be true for the operator to return true. Further, by
definition it returns true if both the bits are true and returns false if both
the bits are false.

Here's the truth table for the bitwise OR operator.

| X | Y | Z |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 1 |

Consider the following example.

```
// BitwiseOrExample.zen

function main(...arguments)
    var a = 19
    var b = 7
    var c = a | b
    print(c)
```

We know that integers occupy 32 bits. To evaluate the last expression, each bit
is combined to produce 1 or 0 if at least one of the corresponding bits is 1 or
otherwise, respectively.

#### The Bitwise XOR Operator

The bitwise XOR operator combines two bits and returns true only if one of the
bits is true and the other bit is false. Otherwise, it returns false for the
given bit pair. Again, when we say true and false, we mean `1` and `0`, respectively.
The operator basically combines all the bits in the given operands.
Mathematically, it is written as `Z = X . ~Y + ~X . Y` where `.` implies multiplication.

This operator is called the bitwise XOR because the left hand side bit must be
*exclusive* of the right hande side bit for the operator to return true.
Further, by definition it returns false if both the bits are true or false.

Here's the truth table for the bitwise XOR operator.

| X | Y | Z |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

As metioned previously, in a bitwise operation, the smaller sized operand is
padded with zeroes before the most significant bit to match the larger sized
operand.

Consider the following example.

```
// BitwiseXorExample.zen

function main(...arguments)
    var a = 25
    var b = 25
    var c = a ^ b
    print(c)
```

To evaluate the last expression, each bit is combined to produce 1 or 0 if the
corresponding bits are exclusive or otherwise, respectively.

#### The Bitwise Complement Operator

The bitwise complement operator is a unary operator. It flips every bit in the
operand.

Here's the truth table for the bitwise complement operator.

| X | Y |
|---|---|
| 0 | 1 |
| 1 | 0 |

Mathematically, it is written as `Y = ~X`, where `~` implies negation.

Consider the following example.

```
// BitwiseNotExample.zen

function main(...arguments)
    var a = 255
    var b = ~a
    print(b)
```

Here, each bit is flipped to produce 1 or 0 if the corresponding bit is 0 or 1,
respectively.

#### The Left Shift Operator

The left shift operator `<<` shifts all of the bits in the first operand to
the left by a number of times specified by the second operand.

It has the following general form.
```
value << times
```

Where, `times` specifies the number of positions to left-shift the specified value.
For each shift, the most significant bit is shifted out and lost. A zero is brought
in as the least significant bit. This means that when you left shift a 32-bit
integer operand, bits are lost after 32 positions.

## The Right Shift Operator

The right shift operator `>>` shifts all of the bits in the first operand to
the right by a number of times specified by the second operand.

It has the following general form.
```
value >> times
```

Where, `times` specifies the number of positions to right-shift the specified value.
For each shift, the least significant bit is shifted out and lost. A zero is brought
in as the most significant bit. This means that when you right shift a 32-bit integer
operand, bits are lost after 32 positions.


## Overriding Operators

Zen allows operator overriding through a combination of functions and
annotations. All the operators in Zen are dispatched to a function call.
The `ZenKernel.evaluate(...)` function finds a suitable handler for the
operator defined within the operand object and dispatches it. In other words,
the compiler translates expressions with operators to equivalent
`ZenKernel.evaluate(...)` calls.

For example, in the `HashMap` class the following annotation
overrides the subscript operator.

```
@Operator symbol='[]'
function getValue(key)
    ...
```

With that information, consider the following snippet of code.

```
var emailAddresses = {
    'Samuel Rowe' : 'samuelrowe1999@gmail.com',
    'Joel E. Rego' : 'joelerego@gmail.com'
}
var myEmailAddress = emailAddresses['Samuel Rowe']
```

The above code snippet is equivalent to the following expression statement.

```
var emailAddresses = {
    'Samuel Rowe' : 'samuelrowe1999@gmail.com',
    'Joel E. Rego' : 'joelerego@gmail.com'
}
var myEmailAddress = ZenKernel.evaluate(emailAddresses, 'Samuel Rowe', '[]')
```

In fact, when you compile the former code snippet the compiler generates
instructions as if the code was written in the latter form.


## Combing Operators

The concepts explained in this section are very important. Do not worry if you
find the concepts confusing. You can always come back and read the section later.

You can combine operators to form complex expessions. The order in which the
operations are evaluated is determined by the precedence of the operators involved
in the expression. For example, multiplication and division have a higher
precedence than addition and subtraction.

Always remember, precedence rules can be overridden by explicit parentheses.
They raise the precedence of the operations that are inside them. This is
often necessary to obtain the result you desire. We recommend you to use
parentheses whenever possible for clarity.

When two operators share an operand the operator with the higher precedence goes
first. For example, `1 + 2 * 3` is treated as `1 + (2 * 3)`, whereas `1 * 2 + 3`
is treated as `(1 * 2) + 3` since multiplication has a higher precedence than addition.
But what happens when two operators with the same precedence
occur in the same expression? In such cases, the expression is evaluated
according to the associativity of the operators involved.

For example, the expression `x = y = z = 7` is equivalent to `x = (y = (z = 7))`,
because the assignment operator has right-to-left associativity which means the
operators are evaluated from right to left.
Here's another example. The expression `10 / 20 / 30` is equivalent to `(10 / 20) / 30`
because the `/` division operator has left-to-right associativity.

Further, some operators are non-associative. For example, the expression `x <= y <= z`
is invalid.

The following table shows all operators in Zen from highest to lowest precedence,
along with their associativity. You do not have to memorize them all. You will
learn their properties eventually with practise.


| Precedence | Operator | Type                                     | Associativity |
|------------|----------|------------------------------------------|---------------|
| 14         | ()       | Parentheses                              | left-to-right |
|            | []       | Subscript                                |               |
|            | ·	    | Member selection                         |               |
| 13         | +        | Unary plus                               | right-to-left |
|            | -        | Unary minus                              |               |
|            | !        | Logical NOT                              |               |
|            | ~        | Bitwise NOT                              |               |
| 12	     | *        | Multiplication                           | left-to-right |
|            | /        | Division (quotient)                      |               |
|            | %	    | Division (remainder)                     |               |
| 11         | +        | Addition                                 | left-to-right |
|            | -        | Subtraction                              |               |
| 10         | <<       | Bitwise left shift                       | left-to-right |
|            | >>       | Bitwise right shift with sign extension  |               |
|            | >>>      | Bitwise right shift with zero extension  |               |
| 9	         | <        | Lesser than                              | left-to-right |
|            | <=       | Lesser than or equal                     |               |
|            | >        | Greater than                             |               |
|            | >=       | Greater than or equal                    |               |
|            | is       | Reference comparison                     |               |
| 8	         | ==       | Equality                                 | left-to-right |
|            | !=       | Inequality                               |               |
| 7          | &        | Bitwise AND                              | left-to-right |
| 6          | ^        | Bitwise Exclusive OR                     | left-to-right |
| 5          | \|       | Bitwise Inclusive OR                     | left-to-right |
| 4          | &&       | Logical AND                              | left-to-right |
| 3          | \|\|	    | Logical OR                               | left-to-right |
| 2          | ? :      | Conditional                              | right-to-left |
| 1          | =        | Assignment                               |               |
|            | +=       | Addition and assignment                  |               |
|            | -=       | Subtraction and assignment               |               |
|            | *=       | Multiplication and assignment            |               |
|            | /=       | Division (quotient) and assignment       |               |
|            | &=       | Bitwise AND and assignment               |               |
|            | ^=       | Bitwise XOR and assignment               |               |
|            | \|=      | Bitwise OR and assignment                |               |
|            | ~=       | Bitwise NOT and assignment               |               |