+++
title = "Using the Compound Assignment Operators"
+++

A compound assignment operator is an operator that performs both an implicit
calculation and an assignment.

Here's a list of all the compound arithmetic assignment operators in Zen.

> Please note that the operators described in the table below are with respect
> to the `Integer8`, `Integer16`, `Integer32`, `Integer64`, `Decimal32` and `Decimal64`
> data types. For behavior specific to other data types, please refer the documentation.

| Operator | Description                              |
|----------|------------------------------------------|
| +=       | Addition and assignment                  |
| -=       | Subtraction and assignment               |
| *=       | Multiplication and assignment            |
| /=       | Division (for quotient) and assignment   |
| %=       | Division (for remainder) and assignment  |

For example, the expression `a = a + 10` can be written as `a += 10`.

Here's another exampe. The expression `b = b * 100` can be written as `b *= 100`.

> Please note that the operators described in the table below are with respect
> to the `Integer8`, `Integer16`, `Integer32`, and `Integer64` data types.
> For behavior specific to other data types, please refer the documentation.

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