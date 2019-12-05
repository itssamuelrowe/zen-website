+++
title = "Working with Bitwise Operators"
+++

> Please note that the operators described in this section are with respect
> to the `Integer8`, `Integer16`, `Integer32`, `Integer64`, `Decimal32` and `Decimal64`
> data types. For behavior specific to other data types, please refer the documentation.

A computer stores data in binary. In other words, information is encoded as 
a sequence of 1's and 0's. On most computers, the memory is organized into 8-bit
cells known as bytes.

Zen defines several operators that allow you to work at the binary level. These
operators perform bit-by-bit (commonly known as bitwise) operations on bit
patterns and involve manipulation of individual bits. Such operators are known
as bitwise operators. These operators can be applied only to integers.

## The Bitwise AND Operator

The bitwise AND operator combines two bits and returns true
only if both the bits are true. Otherwise, it returns false for 
the given bit pair. When we say true and false, we mean `1` and `0`, respectively.
The operator basically combines all the bits in the given operands.

This operator is called the bitwise AND because the left hand side bit *and* the
right hand side bit must be true for the operator to return true.

Here's the truth table for the bitwise AND operator.

| X | Y | Z |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

Mathematically, it is written as `Z = X . Y` where `.` implies multiplication.

In a bitwise operation, the smaller sized operand is padded with zeroes before the most significant bit
to match the larger sized operand.

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

## The Bitwise OR Operator

The bitwise OR operator combines two bits and returns true if at least one of
the bits is true. Otherwise, it returns false for the given bit pair. Again,
when we say true and alse, we mean `1` and `0`, respectively The operator basically
combines all the bits in the given operands.

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

Mathematically, it is written as `Z = X + Y` where `.` implies addition.

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

## The Bitwise XOR Operator

The bitwise XOR operator combines two bits and returns true only if one of the
bits is true and the other bit is false. Otherwise, it returns false for the
given bit pair. Again, when we say true and false, we mean `1` and `0`, respectively.
The operator basically combines all the bits in the given operands.

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

Mathematically, it is written as `Z = X . ~Y + ~X . Y` where `.` implies multiplication.

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

## The Bitwise Complement Operator

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

## The Left Shift Operator

The left shift operator `<<` shifts all of the bits in the first operand to
the left by a number of times specified by the second operand.

It has the following general form.
```
value << times
```

Where, `times` specifies the number of positions to left-shift the specified value.

For each shift, the most significant bit is shifted out and lost. A zero is brought
in as the least significant bit.

This means that when you left shift a 32-bit integer operand, bits are lost after
32 positions.

## The Right Shift Operator

The right shift operator `>>` shifts all of the bits in the first operand to
the right by a number of times specified by the second operand.

It has the following general form.
```
value >> times
```

Where, `times` specifies the number of positions to right-shift the specified value.

For each shift, the least significant bit is shifted out and lost. A zero is brought
in as the most significant bit.

This means that when you right shift a 32-bit integer operand, bits are lost
after 32 positions.