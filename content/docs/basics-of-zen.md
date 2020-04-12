+++
title = "Basics of Zen"
chapter = true
weight = 3
+++

### Chapter 3

# Basics of Zen

In this chapter, you will learn the basics of writing simple Zen programs. The
programs in this chapter are simple and are capable of only printing messages on
the console. These examples will help you to understand the basic structure of Zen
programs.



+++
title = "The Hello World Program"
+++

In this section, you will learn to write the *Hello World* program.

Many programming courses begin with a simple example program that prints the text,
"Hello, world!" on the console.

```
function main(...arguments)
    print('Hello, world!')
```

* Copy the source code from here.
* Paste the source code into a text editor, such as Notepad or Notepad++.
* Save it in a file named *Hello.zen*.
* You need to remember where you save your file. For the sake of demonstration,
  let us assume the path `C:\examples\hello-world`.
* Open a console window.
* Change the current working directory to the directory where your file is
   saved. In our example, it is `C:\examples\hello-world`.
* To change the current working directory use the `cd` command. For example,
```
cd C:\examples\hello-world
```
* Compile it with `zen Hello.zen` in the console window.
* Run your program with `zvm Hello` in the console window.

## Opening Console Window on Windows

### Method 1

1. Press the `Windows + R` keys.
2. A dialog with the title `Run` will appear on the screen.
3. Type `cmd` in the text field.
4. Press enter.

### Method 2

1. Click on the Windows logo in the bottom left corner of your screen.
2. Search `cmd.exe` in the search field.
3. Click on `cmd.exe`.

In Zen, every compilation unit is translated to a class, even if you do not
explicitly declare one. When you do not explicitly declare a class, the compiler
automatically generates a class for you. The name for this class is derived from
the name of the source file. Therefore, you must always save your source code
inside a file whose name adheres to the rules of identifiers. In our first
example, the compiler automatically generated a class named `Hello` because our
source code was saved in the file `Hello.zen`

> You will learn more about classes in a later chapter.

Unlike other programming languages, Zen does not require braces to indicate
the body of a function. A block is indicated by indentation. Whatever you *declare*
within a block belongs to the function below which the block appears.

```
function main(...arguments)
```

Here you created a *function* called `main`. You do not have to know what this
means for now, so do not worry. You will learn more about functions later in
the manual.

The `main` function is the **entry point** of your program. In other words,
your program always starts at `main`.

`(...arguments)` is too advanced to explain just yet. It is called a
*parameter list*. You can use it to pass data to a function.

When the `main` function is invoked by the virtual machine, it receives a single
parameter: an *array* of string objects. If you do not know what a parameter, a
string, or an array is, do not worry. You will learn more about these concepts
later in the manual.

```
    print('Hello, world!')
```

The `print` function allows you to write data to the console window.



+++
title = "Understanding Identifiers"
+++

Identifiers are the names you give to variables, methods, classes, annotations
and enumerations. Unlike literals, identifiers only help you reference to something.

The program shown in the hello world example shown in the previous section
uses three identifiers.
    * `main`
    * `arguments`
    * `print`

* Identifiers are case sensitive. For example, `ArrayList` with uppercase `A`
and `arrayList` with lowercase `a` are two different identifiers.
* Identifiers may contain uppercase or lowercase letters, numerals,
  underscore characters `_`, and dollar symbols `$`.
* Identifiers must begin with a letter or an underscore. For example, `f07` is a valid
  identifier, but `7feb` is not because it begins with a numeral.
* You cannot use a *keyword* as an identifier. For example, `function` is not a
  valid identifier.
* You have to avoid using dollar symbols in identifiers. It is reserved for tools
  that generate code.

Here are a few examples of valid identifiers.
```
helloWorld
__student
Object
STRING
invoke123
$person
i
x1010
```

Here are a few examples of invalid identifiers.
```
function /* function is a keyword. You cannot use a keyword as an identifier. */
hello world /* An identifier cannot have spaces. */
3dCube /* An identifier cannot begin with a numeral. */
a*a /* An identifier cannot have symbols. */
```

+++
title = "Working with Statements"
+++

Statements are similar to sentences in the English language. A statement tells
Zen to perform an action. It can include one or more *expressions*.

There are two types of statements in Zen:
    * Simple Statement
    * Compound Statement

## Understanding Simple Statements

Simple statements are the actions your program performs.

 * Assertion Statement
 * Break Statement
 * Continue Statement
 * Empty Statement
 * Expression Statement
 * Return Statement and
 * Throw Statement

A simple statement always ends with a newline. Most programming languages
such as C, C++, and Java expect a simple statement to be terminated with a
semicolon. In languages such as JavaScript and Python, the semicolon is
optional.

The example shown here is an expression statement. Therefore, it is
*terminated* with a newline.

```
print('Hello, world!')
```

## Understanding Compound Statements

Compound statements help you group simple statements and control them. They
are always associated with blocks.

 * Block Statement
 * For Statement
 * If Statement
 * Synchronize Statement
 * Try Statement
 * While Statement

+++
title = "Understanding Keywords"
+++

A *keyword* is a special word whose meaning is defined by the Zen programming
language specification. **You cannot use these words as identifiers**.
All keywords are in lowercase.

Like everything else in Zen, keywords are case sensitive. For example, if you
use `For` with uppercase `F` instead of `for` with lowercase `f` it is an error.

The hello world program shown in the beginning of this chapter use one keyword:
`function`.

In Zen there are 36 keywords. They are listed below in alphabetical order.

| Keywords | | | | |
|----------|-----------|-----------|-------------|----------|
| abstract | and       | assert    | break       | catch    |
| class    | continue  | else      | enum        | extends  |
| false    | final     | finally   | for         | function |
| if       | import    | is        | native      | new      |
| null     | or        | private   | public      | return   |
| secret   | static    | super     | synchronize | this     |
| throw    | true      | try       | var         | while    |
| with     |


+++
title = "Working with Blocks"
+++

A block is a group of one or more statements. It is also known as a statement suite.
It is a type of statement, a compound statement to be specific. It begins when
the indentation of the first statement of the block is greater than the indentation
of its containing block. Subsequent statements with the same indentation as that
of the first statement are grouped together in the block.

You can write any number of statements, including block statements, in a block.

You cannot write an empty block in Zen. However, you can make use of the empty
statement to represent a dummy block like this.
```
function main()
    ; // Dummy block with an empty statement.
```

For example, this is a block with four statements.
```
    var i = null
    var j = null
    i = 10
    j = 20
```

Here is an example of block statements.

```
function main(...arguments)
    print('This is the outer block.')
    if true
        print('This is the inner block.')
        print('This statement belongs to the inner block as well.')
```

+++
title = "Working with Comments"
+++

Comments are texts that are ignored by the compiler. They help you write
information or explanation about your code. You can use comments to hide a part
of your code.

We recommend you to use plenty of comments in your source code.

## Types of Comments

There are 3 types of comments in Zen.

 * Single Line Comment
 * Multi-Line Comment
 * Documentation Comment

### Single Line Comments

A single line comment begins with `//` and ends at the end of the line.
Everything you type after `//` is ignored by the compiler.

Here's an example.
```
perimeter = 2 * (width + breadth) // Calculate the perimeter of the rectangle.
```

If you want, you can move the comment on a separate line.
```
// Calculate the perimeter of the rectangle.
perimeter = 2 * (width + breadth)
```

### Multi-Line Comments

A multi-line comment begins with `/*` and ends with `*/`. It can span
over multiple lines.

Here is an example.
```
/*
Calculate the perimeter of the rectangle.
Then subtract 100 from it.
*/
perimeter = 2 * (width + breadth) - 100
```

Here is another example.
```
/* Calculate the perimeter of the rectangle.
Then subtract 100 from it. */
perimeter = 2 * (width + breadth) - 100
```

A multi-line comment can begin and end anywhere on a line.

Here is an example where the comment is placed in the expression.

```
perimeter = 2 * (width + breadth) /* Calculate the perimeter of the rectangle.*/ - 100 /* Then subtract 100 from it. */
```

Usually, multi-line comments appear on separate lines.

Multi-line comments cannot be nested. Here is an example which results in error
when you try to compile.

```
/*
 This is a comment.
 /* This is a nested comment. */
 */
```

### Documentation Comments

A documentation comment begins with `/**` and ends with `*/`. It can span
over multiple lines. It is similar to multi-line comments.