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