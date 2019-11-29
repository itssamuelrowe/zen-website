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