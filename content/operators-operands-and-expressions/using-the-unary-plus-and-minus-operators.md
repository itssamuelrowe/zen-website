+++
title = "Using the Unary Plus and Minus Operators"
+++

> Please note that the operators described in this section are with respect
> to the `Integer8`, `Integer16`, `Integer32`, `Integer64`, `Decimal32` and `Decimal64`
> data types. For behavior specific to other data types, please refer the documentation.

The unary plus and minus operators let you change the sign of an operand.

Note that the symbol used to represent these operators are the same as the
addition and subtraction operators. The compiler figures out which operation
you mean by examining the expression.

Remember, the unary minus operator does not necessarily make an operand
negative. Actually, it inverts the sign of the operand. For example, assume
`x = -5` then `-x` will give you `5`.

Mathematically, this is equivalent to `-x = x * -1`.

Interestingly, the unary plus operator does not actually
do anything. For example, assume `x = -5` and `y = 7` then
`+x` and `+y` will give you `-5` and `7`, respectively.

Mathematically, this is equivalent to `+x = x * 1`.