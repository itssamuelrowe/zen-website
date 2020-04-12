+++
title = "Variables, Values, and Data Types"
chapter = true
weight = 4
+++

### Chapter 4

# Variables, Values, and Data Types

In this chapter, you will learn the basics of working with variables in Java.
Variables are fundamental in making general purpose programs.
In the Hello World program that we studied in the previous chapter
always prints "Hello, world!". With a variable, you can
make it more general. For example, you could personalize the greeting to wish
the user with their name.


+++
title = "Understanding Data Types"
+++

Zen is a *dynamically typed* programming language. What this means is, the
compiler does not know the type of every variable. Once you declare a variable,
it can hold values of any type. For example, a variable referencing an integer
may be updated to reference a string without making the compiler complain.

The advantage of dynamically typed languages is that programs can be written
quickly. On the other hand, the primary disadvantage of a dynamically typed
language is that many bugs cannot be caught during compilation.

As a Zen programmer, you are not required to specify the type of each variable.
The compiler does not check if you assigned the wrong type of data to variables.

Here's an example where a string value is assigned to a variable holding an
integer value. Do you think it will compile?
```
function main(...arguments)
    var age = 20
    age = 'twenty'
    print(age)
```

The compiler generates no errors if you try to compile this, because `age` is
a variable and can hold any type of value.

### Different Categories of Data Types

In Zen, a data type is always a reference type, which is divided into two
categories.
    * Primitive Reference Types
    * Non-Primitive Reference Types

The *primitive reference types* are the most basic data types available. They are
**defined by Zen** and receive special treatment from the compiler.

The *non-primitive reference types* are the data types that are **defined by classes and
enumerations**. They do not receive any special treatment from the compiler.



+++
title = "Understanding Variables"
+++

In this section, you will learn about variables.

A variable is a place holder. A variable's value can change when your program
is running.

For exampe, you can store a value like 100 in a variable. After you store a value,
you can store a different value in the variable whenever you want. When you store
a new value in a variable, the old value is no longer there. In other words, the
old value is replaced by the new value.

The value you can store in a variable is not necessarily a number. In fact, Zen
is dynamically typed. What this means is, you can store any type of value in a
variable. For example, consider a variable called `i` which currently holds a
string. You can later store an integer in `i`.

You can refer the value stored in a variable using a variable's name.



+++
title = "Declaring Variables"
+++

In this lecture, you will learn how to declare variables.

You must *declare* a variable before using it. The compiler will display
errors otherwise.

The basic form of a variable declaration statement is shown below.
```
var name
```

A variable name is an identifier. You can refer the value stored in the
variable with its name.

Unlike other statically typed programming languages, you don't have to write
the type of values that can be stored in a variable.

A variable declaration is a simple statement. It must end with a newline.

Here's an example where two variables are declared.
```
var name
var age
```

In this example, you *declared* variables named `name` and `age`. The variable
`name` can hold any types of values.

### Declaring Two or More Variables in One Statement

You can declare two or more variables in a single statement. You must separate
the variable names with commas.

Here's an example where four variables are declared.
```..
var a, b, c, d
```

Although this is easier, we suggest you to avoid this. Because it makes your
code less easier to read.

### Understanding Local Variables

A local variable is a variable that you declare within the body of a function.
You can use a local variable only within that function. You can't use it outside
the function.

For example, the variable `k` exists only with the body of the `main` function.
```
function main(...arguments)
    var k
    /* You can refer 'k' only within the body of this function. */
```

The region in which your variable exists is known as *scope*. You will learn
more about scopes later in the manual.

The place where you declare a local variable is important. You must declare
a variable before you use it.

For example, the compiler generates an error if you try to compile this example
**because the program declares the variable after using it.**

```
function main(...arguments)
    i = 10
    var i
```

Don't worry if you don't understand what `i = 10` means. You'll learn about it
in the next section.

### Initializing Variables

When you refer the value *stored in a local variable*, the compiler checks if
you assigned a value previously.

For example, the compiler generates an error if you try to compile this
example **because the program uses a variable without assigning a value.**
```
function main(...arguments)
    var name
    print(name)
```

To avoid such errors, you must initialize local variables before you use them.
You can assign a variable with an *expression statement*. In particular, you use
the *assignment expression* to assign a variable. You will learn more about
expressions later in the manual.

The basic form of an assignment expression is shown here.
```
variable = expression
```

Here, `expression` can be any expression that evaluates to a value.

For example, this is the correct version of the previous example.
```
function main(...arguments)
    var name
    name = 'Samuel Rowe'
    print(name)
```

In this example, the variable is assigned a value of 'Samuel Rowe' before
printing it.

### Initializing Variables with Initializers

You can initialize a variable when you declare it. You use an *initializer* to
do this. The general form of an initializer is shown here.
```
type name = expression
```

The initializer allows you to combine declaration and initialization.

Take a look at some examples given below.

```
var name = 'Samuel Rowe'
var age = 19
var gravity = 9.8f
var pi = 3.142857142857143
```

In each of these statements, a variable is declared and initialized.

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


+++
title = "Working with Non-Primitive Reference Types"
+++

In this section, you will learn about the basics of non-primitive reference types.
You learn to create variables that work with objects.

The rules that apply to these types also apply to primitive reference types.

> You will learn more about classes and objects later in the course.

Zen programs are built with classes. You can use classes to create objects.
A class can either be a part of the Zen standard API or a class that you create.

When you create an object, you allocate memory to store the object. Here's an
example of how you can create an object.
```
new Object()
```

When you store the object in a variable, you assign a *reference* to the object.
You don't store the object itself.

A reference is the location of an object in memory. References are similar to
pointers in C or C++. Unlike pointers, references are simple and easy to use.

For example, think that you are writing a program which involves cars.
You have a class named `Car` which defines the behavior of a car.
You can declare a variable that stores a reference to a `Car` object like
this.
```
var car
```

Here, the variable `car` can hold any type of object, including `Car` objects.

To create a new *instance* of a class, you can use the `new` keyword. You have
to provide `new` keyword the name of the class, whose instance you want to create.
When you create an instance of a class, you actually call a *constructor*.
The constructor initializes the new object.

> You do not have to understand these concepts right away. You will understand
> them when you learn about them in detail.

Here's an example where we create an instance of the class `Car`.
```
new Car()
```

You can assign a reference to the new object as shown below.
```
var car
car = new Car()
```

You can combine both these statements like this.
```
var car = new Car()
```

Remember that a reference variable does not actually store an object.
It stores only the reference to an object in memory. As a result, two or more
variables can refer to the same object.

Here's an example where two variables refer to the same `Car` object.
```
var carX = new Car()
var carY = carX
```

Here, we have declared two variables, named `carX` and `carY`. But we have
created only one `Car` object.

We first created a `Car` object and assigned its reference to `carX`. Then
the same reference is assigned to `carY`. This way, both `carX` and `carY`
refer to the same object.


+++
title = 'Declaring Final Variables or Constants'
+++

In this section, you will learn how to declare final variables or constants.

A final variable is variable that you cannot change after initializing.
The compiler will generate errors if you try to change it. It is also
called as a *constant*.

The basic form of a constant declaration statement is shown here.
```
final name = expression
```

The primary difference between declaring a variable and a constant is the
use of `final` keyword. Further, you must provide the value of the constant
when you declare it.

Take a look at this example where two constants are declared.
```
final NUMBER_OF_MONTHS = 12
final PI = 3.142857142857143
```

We suggest you to use only capital letters for naming constants. It helps you
easily spot constants in your programs.

### Declaring Two or More Constants in One Statement

You can declare two or more constants in a single statement, just like variables.
You must separate the constant names with commas.

Here's an example where three constants are declared.
```
final NUMBER_OF_DAYS = 7, FIRST_DAY = 'Sunday', LAST_DAY = 'Saturday'
```

Although declaring two or more costants in a single statement is easier, we
suggest you to avoid this because it makes your code less easier to read.

### Advantages of Using Constants

Using constants has the following advantages:
 * If you later decide to change its value, you must change in just one place,
   that is, the initializer. In case of using a literal, you would have to change
   everywhere, which is error prone.
 * Constants make your programs easier to read.




+++
title = "Working with Strings"
+++

In this section, you will learn the basics of strings.

A string is a sequence of characters. String literals are enclosed in single
quotes (`'`).

Here's an example of a string.
```
'Hello, world!'
```

The Zen Virtual Machine does not define string as a primitive type. Further,
the Zen programming language treats strings specially and classifies a string
as primitive reference type. It is implemented by the `zen.core.String` class.

We take an entire chapter to explain strings. Here, we teach you the
basics. It will help you understand the upcoming examples.

### Initializing Strings

Here's an example of initializing a `String` variable.
```
var message
message = 'How are you?'
```

Here, we declared a variable named `message` and initialized it to `'How are you?'`.
Remember that string literals are enclosed in single quotes (`'`), not in double
quotes.

You can combine declaration and initialization like this.
```
var message = 'How are you?'
```

To initialize a local string variable to an empty string, use a statement like
this.
```
var string = ''
```

### Joining Strings

You can join two strings by using the *concatenation operator* (`+`).
*Concatenation* means joining two strings.

Here's an example where two strings are joined.
```
// JoiningStrings.zen

function main(...arguments)
    var hello = 'Hello, '
    var world = 'world!'
    var message = hello + world
    print(message)
```

When you join strings, no extra characters are added by Zen. This includes any
blank spaces between strings. If you want to combine two strings with a space in
between them, you have to do it. In the previous example, the first string ends
with a space.

Here's another example where two strings are joined with and without space in
between them.
```
// JoiningStringsWithSpace.zen

function main(...arguments)
    var hello = 'Hello,'
    var world = 'world!'
    var message1 = hello + ' ' + world
    var message2 = hello + world

    print(message1)
    print(message2)
```

You can join a string with any object, such as `Integer32` and `Decimal32`.
Zen converts the primitive value to a string and then joins it.

Here's an example where a string is joined with a Boolean value.
```
// JoiningStringsWithPrimitiveValues.zen

function main(...arguments)
    var question = 'Are you Batman?'
    var answer = true
    var message = question + ' ' + answer
    print(message)
```

Here we declared a variable named `question` which holds a simple
question. We declared a variable named `answer` which holds `true`.
We joined `question` and `answer` using the concatenation operator (`+`).
The resulting string was stored in `message`. We have added a blank space to
seperate the question and answer. Finally, we printed the string stored in
`message`.

### Converting Strings to Numeric Values

You can convert a string into a numeric value. For example, you can convert the
string `'27'` written with digits into a numeric value. But you cannot convert
the string `'twenty seven'` written in words into an integer, at least not using
the standard API.

You can use one of the following functions to convert a string to a primitive
value.

| Wrapper Class | Function     |
|---------------|--------------|
| Boolean       | parse        |
| Character     | --           |
| Integer8      | parse        |
| Integer16     | parse        |
| Integer32     | parse        |
| Integer64     | parse        |
| Decimal32     | parse        |
| Decimal64     | parse        |

Here's an example of converting strings to primitive values.
```
var value1 = Boolean.parse('true')
var value2 = Integer8.parse('27')
var value3 = Integer16.parse('519')
var value4 = Integer32.parse('2000')
var value5 = Integer64.parse('1999')
var value6 = Decimal32.parse('5.19')
var value7 = Decimal64.parse('9.21')
```




+++
title = "Understanding Unicode"
+++

> This section describes Unicode and how Zen deals with it. It is a difficult
> concept to grasp. You can safely skip this section for now. You can come back
> when you are comfortable with Zen.

To work with characters in a computer, you need the following:
 * Character Repertoire
 * Character Set
 * Character Encoding

### Understanding Characters Repertoire

A *character repertoire* is a collection of characters your computer can
work with. For example, a character repertoire may include letters, digits,
and symbols from Kannada, English, Tamil, Hindi, and Telugu.

### Understanding Character Set

Computers understand only numbers. So they store letters and other characters
by assigning a number for each one. These numbers are known as *codepoints*.

When a computer stores a character, it doesn't really know the difference
between `A` and `B`. However, it knows the difference between `65` and `66`.
Internally, computers use the number `65` as the *codepoint* to represent `A`
and `66` for `B`.

In fact, all letters, digits, and symbols have codepoints. The codepoints given
to characters are collectively known as *character set* or *charset*.

When you store `'A'` in a `char` variable, you actually store the value `65` in
it. Which means, the `char` type is really an integer type.

Here's an example which prints the codepoints of A, B, C, D, E, and F.
```
// CodePointsExample.zen

function main(...arguments)
    print('A'.getCodepoint(0))
    print('B'.getCodepoint(0))
    print('C'.getCodepoint(0))
    print('D'.getCodepoint(0))
    print('E'.getCodepoint(0))
    print('F'.getCodepoint(0))
```

### Understanding Character Encoding

Finally, your computer stores your codepoints in a sequence of 1s and 0s.
This binary representation is called as *character encoding*.

## History of Unicode

There were hundreds of different character encodings before Unicode was
invented. The other character encodings were limited. They did not cover
all the languages of the world.

The *Unicode Standard* provides a codepoint for every character, no matter
what platform, device, application or language. It is used in all modern
software.

Unicode is a very popular character encoding standard. Many well known companies
such as Microsoft, Google and Oracle use Unicode. In fact, you are using Unicode
already.

Unicode was actually designed to *encode* characters in 2 bytes. This is why
`char` defined by the Zen Virtual Machine uses 2 bytes.

Only 65,536 characters can be encoded with 16 bits. You cannot represent all
the characters in the world with just 16 bits. So Unicode was extended to use
21 bits. Now over one million characters can be encoded (1,114,111 to be exact).
You can use the characters outside U+FFFF with *supplementary characters*.

## Using Unicode in Zen

A supplementary character is any character within the range U+10000 and U+10FFFF.
You need to use a pair of character values to represent them. The pair of codepoints
which represent a supplementary character are known as surrogates.

The first codepoint is known as the high surrogate. It is in the range of U+D800
to U+DBFF.

The second codepoint is known as the low surrogate. It is in the range of U+DC00
to U+DFFF.

For example, the **DESERET CAPITAL LETTER LONG I** (U+10400), is represented with
U+D801 and U+DC00 surrogate pair.
```
var letter = '\uD801\uDC00'
```