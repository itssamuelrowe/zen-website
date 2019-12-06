+++
title = "Combing Operators"
+++

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