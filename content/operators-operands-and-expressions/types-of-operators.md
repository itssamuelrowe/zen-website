+++
title = "Types of Operators"
+++

In this lecture, we'll learn about the types of operators based on the
number of operands they expect.

A common way to categorize Zen’s operators is by the number of operands the
operator expect.

There are three types of operators based on the number of operands they accept.

* Unary Operators  
* Binary Operators  
* Ternary Operators  

## Unary Operators

Unary operators are operators that expect one operand.

A unary operator can be a prefix operator or a postfix operator.

A prefix operator is written before the operand, like this:

```
operator operand
```

A postfix operator is written after the operand, like this:

```
operand operator
```

## Binary Operators

Binary operators are operators that expect two operands.

In Zen, all the binary operators are infix operators, which means they
appear between the operands, like this:

operand1 operator operand2

## Ternary Operators

Ternary operators are operators that expect three operands.

The conditional operator is the only operator in Zen that expects three
operands. It is also an infix operator and written like this:

```
operand1 ? operand1 : operand2
```