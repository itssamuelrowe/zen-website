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