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
    * Primitive Wrapper Types
    * Other Reference Types

The *primitive wrapper types* are the most basic data types available. They are
**defined by Zen** and receive special treatment from the compiler.

The *other reference types* are the data types that are **defined by classes and
enumerations**. They do not receive any special treatment from the compiler.