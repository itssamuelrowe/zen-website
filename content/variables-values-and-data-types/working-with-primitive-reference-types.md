+++
title = 'Working with Primitive Reference Types'
+++

The *primitive types* are the most basic data types available in the Zen Virtual
Machine.

There are eight primitive data types defined by the Zen Virtual Machine.  
 * `boolean`  
 * `char`  
 * `integer8`  
 * `integer16`  
 * `integer32`  
 * `integer64`  
 * `decimal32`  
 * `decimal64`  

The primitive types are not reference types. Since the Zen programming language
supports only primitive types, it adds wrappers around these primitive types
through *wrapper classes*.

There are eight wrapper classes defined by the Zen programming language.  
 * `Boolean`  
 * `Character`  
 * `Integer8`  
 * `Integer16`  
 * `Integer32`  
 * `Integer64`  
 * `Decimal32`  
 * `Decimal64`  

| Type      | Default  | Size    | Range                                                   | Example                                        |
|-----------|----------|---------|---------------------------------------------------------|------------------------------------------------|
| boolean   | false    | 1 byte  | true or false                                           | true, false                                    |
| char      | \u0000 | 2 bytes | 0 to 65,536 (unsigned)                                  | 's', 'M', 'a', 'o', 'H', '7', 'L'              |
| integer8  | 0        | 1 byte  | -128 to 127                                             | 5, 2, 7, 19, 100                               |
| integer16 | 0        | 2 bytes | -32,768 to 32,767                                       | 2000, 2, 7, 19, 5, 1999                        |
| integer32 | 0        | 4 bytes | -2,147,483,648 to 2,147,483,647                         | 1, 88234, -9991, 22234                         |
| integer64 | 0        | 8 bytes | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 | 922337203685477L, -72202593477L, 882200333466L |
| decimal32 | 0.0      | 4 bytes |                                                         | 123.4f, 3.14_15f                               |
| decimal64 | 0.0      | 8 bytes |                                                         | 3.141592653589793d, 1.23456e300d               |

### Working with Boolean

The `boolean` type has two values: `true` or `false`. You can perform *logical
operations* with boolean values. You will learn more about logical operations later
in the manual.

Here is an example of the `boolean` type.
```
var initialized = true
var valid = false
```

In the above example, we declared a variable named `initialized` and
assigned it `true`. We declared another variable named `valid` and assigned
it `false`.

In C and C++, integer values can be used as boolean values, with `0` as `false`
and any other value as `true`. Remember that in Zen integers cannot be used as
boolean values without explicitly converting.

### Working with Integer Types

An *integer* is a number without any fractional or decimal portion.

There are four integer types you can use.
 * `Integer8`
 * `Integer16`
 * `Integer32`
 * `Integer64`

You can store different *range* of integer values in each of these types because
they differ in size.

The most commonly used integer type is `Integer32`. It uses four bytes (32 bits) to
store an integer value.

If you have read the previous chapters, you have already seen `Integer32` in some
examples. Let's take a look at another example.

```
function main(...arguments)
    var cars = 100
    print(cars)
```

If you want to store numbers greater than 2 billion, you can use `Integer64`.
It uses eight bytes (64 bits) to store an integer value.

All integer literals are of type `Integer32` by default. What would you do if you
wanted to assign a huge number like this `1234567890987` to a variable? You must
add the integer suffix `L` like this `1234567890987L`.

Here's an example.
```
function main(...arguments)
    var number = 2720001951999
    print(number)
```

If you try to compile it, the compiler will generate errors.
```
[error] HugeNumber.zen:2-2:18-31: 32-bit integer number too large
```

This is the correct version of the previous example. This program will compile
without any errors.
```
function main(...arguments)
    var number = 2720001951999L
    print(number)
```

You can either use uppercase`L` or lowercase `l`. We suggest you to use uppercase
`L` because lowercase `l` is usually confused with `1`.

The `Integer16` and `Integer8` types use less memory than `Integer32` and
`Integer64` types. They are not used commonly, because saving a few bytes here
and there does not make any difference in performance. You will learn more about
saving memory with `Integer8` and `Integer16` when you learn about arrays.

In C and C++, the size of an integer data type depends on your compiler and
environment. For example, the size of `int` may be four bytes in your computer.
But it may be two bytes in your friends computer. This causes many problems.

This problem is solved in Zen because the virtual machine specification decides
the sizes of the integer data types. They do not depend on your compiler or
environment. This way, the sizes remain same on all computers.

### Working with Decimal Types

Decimal numbers are numbers that have fractional parts.

A decimal number is stored in *exponential notation*, also known as
scientific notation. It has two parts: a base value and an exponent. The base
value is also known as mantissa.

The actual value of a decimal number is calculated by multiplying its mantissa
by two raised to its exponent. Here's the mathematical formula.
```
mantissa × (2 ^ exponent)
```

There are two decimal types you can use.
    * `Decimal32`
    * `Decimal64`

The most commonly used decimal type is `Decimal64`. It uses eight bytes (64 bits)
to store decimal values. *It implements the IEEE 754 double-precision format.*
For `Decimal64`, the exponent ranges from -1023 to +1024.

The `Decimal32` type uses four bytes (32 bits) to store decimal values. *It implements
the IEEE 754 single-precision format.* For `Decimal32`, the exponent ranges from
–127 to +128.

You must add a suffix `D` or `d` to indicate that the literal is of `Decimal64` type.
It is optional, because all decimal literals are of type `Decimal64` by default.

What would you do if you wanted to treat the literal `2.7` as `Decimal32`? You must add
a suffix `F` or `f` to indicate that the literal is of `Decimal32` type.

Here's an example.
```
// AreaOfCircle.zen
function main(...arguments)
    var r = 2.7f
    var pi = 22.0 / 7.0
    print(pi * r * r)
```

We suggest you to never use `Decimal32` and `Decimal64` for precise values, such
as currency.

### Exponents in Decimal Numbers

You can write decimal numbers in scientific notation. Here's a small example.
```
function main(...arguments)
    var n1 = 2.10e+6
    var n2 = 2100000D
    print("n1 = " + n1)
    print("n2 = " + n2)
```

In the above example, both `n1` and `n2` store the same value.

The exponent part either begins with `E` or `e`. You can skip the sign if the
exponent is positive.

You could have written `2.10e6` instead of `2.10e+6` in the previous example.