+++
title = "Packages: How Your Source Code is Organized"
weight = 15
+++

In this module, you will learn about creating packages and importing
packages.

As new features are implemented, the source code of a project grows in complexity.
It becomes hard to maintain the source code when everything is crammed into a
single source file. Therefore, an intuitive feature of a programming language is
to allow programmers to split their source code into multiple files. The symbols
defined in these source files can be imported and exported outside a given source
file or compilation unit as needed.

Further, imagine you have two classes, one of which represents a component that reads
data from the console. Simiarly, the other class represents a device
which scans papers. Although both the classes are different in functionality,
both the classes can be named `Scanner`. So far, you have learnt that you cannot
declare two classes with the same name. An obvious solution is to name these
classes differently. However, that would not be effective considering software
projects always depend on external code.

In order to address these problems, Zen provides a feature known as package that
allows you to create namespaces.

## Understanding Packages

A package is a group of related classes, annotations and enumerations bundled
together. Packages are like containers that provide your classes a namespace.
For example, a package allows you to create two classes named `Scanner`. You
simply need to store the classes in different packages. However, the class names
should be unique within their respective packages.

A package provides a namespace and visibility control to your classes. You can
tell which classes are available to the world outside your package. As of this
writing, Zen allows only public classes. In the future, the visibility of
classes outside a package may be manipulated by the developer. No promises though.

Packages are organized in a hierarchical fashion. When you want to use a class
from a different package, you need to import it. So far in this course, all the
classes you created were stored in the default package. Which means you had to
provide a unique name for each class to avoid name conflicts. Without packages
you would soon run out of relevant, convenient and descriptive names for your
classes.

Further, without packages you would need to make sure that the name you choose
for your classes are different from the class names chosen by other programmers.
In fact, the Zen API consists of hundreds of classes. It would be impossible
to find a unique name for each of these classes. This is why, the Zen Standard
API is ogranized as packages.

## Creating Packages

If you do not create a package, your classes are stored in the default package,
which is why you were able to create classes so far. The default package has no
name. The default package is usually not used in real life applications. Most of
the time, you will create your own packages.

Zen uses folders, also known as directories, to represent packages. For
example, your `.zen` and `.feb` files for the classes you declare in the
`hello` package should be stored in the `hello` directory. Similarly, your `.zen`
and `.feb` files for the classes you declare in the `com.hello` package should
be stored in the `com/hello` directory. Remember that package names are case
sensitive. Therefore, the directory names must match the package name exactly.

In real-life applications, your source code is spread across many files. Any
number of source files can be a part of a package, as long as they are all stored
in the same directory.

### Understanding Qualified Names

You can create a hierarchy of packages using a qualified name. We mentioned this
term in the previous section without going into its details. A qualified name is
a sequence of identifiers separated by dots.

Here are some examples of qualified names.
```
zen.core
zen.net
zen.io
zen.fs
```

Here is the general form of a qualified name.
```
identifier1.identifier2.identifier3
```

A qualified name can consist of any number of identifiers. Each identifier is
separated by a dot and indicates a node or level in your hierarchy. A package
hierarchy must be reflected in your file system. Which means, if you change the
qualified name, you should change the directory structure, too.

For example, a package `com.example` should be stored in the directory `com/example`.

### Understanding Package Lookup

Your packages should be organized correspondingly in your directories. But how
does the virtual machine determine which directory to look for your packages?
By default Zen looks for packages in the current working directory, the directory
from where you are invoking the virtual machine. Further, the virtual machine
looks for packages in the directories listed in the lookup path of the application.
You can specify the lookup path for an application in two ways.

 * Create the `ZEN_PATH` environment variable and store the directories
   where your packages are stored. You usually need to avoid this technique because
   it applies to all the applications that run on the virtual machine, not
   just one application.

 * Specify the lookup path with the `--path` parameter when you invoke the
   virtual machine. This is the preferred way to specify the lookup path.
   This allows the lookup path to be specific to individual programs, without
   affecting other programs.

The general form of a lookup path is shown here.
```
path1;path2;path3
```

The paths point to the directories where your packages are stored. The semicolon
separates the paths. However, you can use semicolons only on Windows. If you
are using other operating systems such as Unix, Linux and MacOS you need to
use the colon (`:`) symbol to separate the paths.

Consider the following package which declares a class.
```
// example/Message.zen

class Message

    var message

    function new(message)
        this.message = message

    @Override
    function toString()
        return message
```

Now create another class in the default package like this.
```
// PackageExample.zen

function main(...arguments)
    var message = new example.Message('Hello, world!')
    print(message)
```

The `PackageExample` classs is declared in the default package. Whereas, the
`Message` class is declared in the `example` package. The `PackageExample` class
uses the `Message` class, which is declared in another package. Therefore, you
need to specify the fully qualified name of `Message`, which is `example.Message`.
Basically, the fully qualified name of the `Message` class consists of its
containing package and its name.

However, classes in the same package can access other classes without their fully
qualified names. Assume two classes, `example.Message` and `example.User`,
both the classes are in the same package. The `User` class can access `Message`
without its fully qualified name, and vice versa.

In order for your program to find the `Message` class, one of following conditions
should be met.

 * The program should be executed from a directory immediately above the `example`
   package.
 * The `ZEN_PATH` environment variable must include the path to `example`.
 * The `--path` parameter must specify the path to `example`.

When you specify a lookup path, the path should not include `com\example` itself.
Instead you need to specify the directory which contains the package directory.
Assume the `com\example` directory is stored in `C:\learning\com\example`.
You need include `C:\learning` in the lookup path, not `C:\learning\com\example`.

We recommend you to run the example programs from their root directories. Which
means you do not have to create the lookup path for now. For example, assume the
`PackageExample` program shown earlier was stored in `C:\learning` and the
`example` package was stored in `C:\learning\example`. To run this program,
you need to execute the following commands in sequence from `C:\learning`.
```
C:\learning>zc PackageExample.zen example/Message.zen
C:\learning>zvm PackageExample
```

The output of the program is shown here.
```
Hello, world!
```

The commands for other operating systems are similar with little tweaks.

## Working with the Import Statement

In Zen, the import statement allows a compilation unit to refer to external
classes. Without the use of the import statement, the only way to refer to a
class outside the current compilation unit is to use a fully qualified name.
Further, all the classes declared in Zen are exported by default. As of this
writing, there is no way to override this behavior.

You have learnt how packages allow you to keep your classes organized. However,
as you have seen accessing classes from different packages require fully qualified
names, which means you have to type so much just to refere a class! For this reason,
Zen provides the import statement.

The general form of the import statement is shown here.
```
import qualifiedName
```

Here, the qualified name refers to the class which you want to import. A qualified
name can consist of any number of identifiers as long as they are separated by
the dot symbol.

The import statement basically allows you to access a class from a different
package without its fully qualified name. Once you import a class, you can refer
it directly, using only its name. The import statement exists to make your life
easier. In the background, the classes are still referred by their fully qualified
names.

Consider the following classes which we saw in the previous section.
```
// com/example/Message.zen

class Message

    var message

    function new(message)
        this.message = message

    @Override
    function toString()
        return message
```

```
// PackageExample.zen

function main(...arguments)
    var message = new com.example.Message('Hello, world!')
    print(message)
```

You could rewrite the `PackageExample` class like this using the import statement.
```
// PackageExampe2.zen

import com.example.Message

function main(...arguments)
    var message = new Message('Hello, world!')
    print(message)
```

You always need to write the import statements at the beginning of your source
file. You cannot write the import statement after or inside components such
as classes and functions.

Sometimes you import many classes from the same package, which means you will
have to write an import statement for each class. This is again cumbersome.
Zen provides a solution to this problem: the wildcard import statement.
In such an import statement, you specify the package name followed by an asterisk.

Here is the general form of such a statement.
```
import level1.level2.*
```

When you specify a package name followed by an asterisk, all the classes in
the package are imported.

Here is an example which demonstrates how you can import all the classes in
the `zen.support` package.
```
import zen.support.*
```

There are two drawbacks with wildcard import statements.

 * It increases the time required to compile your program, especially if your
   source files import large packages. Since the classes are referred by
   their fully qualified names in the background, the bytecode generated
   is the same, with or without the wildcard import statements. In other words,
   wildcard import statements do not affect your runtime performance.

 * It clutters your local namespace, if multiple packages have classes
   with the same names. This forces you to use fully qualified class names.
   When you import multiple packages with a wildcard import, chances are two
   or more classes may have the same name. The import statement does not
   generate an error during such imports. Instead an error is generated when
   you try to refer to either one of them. In such cases, you can resolve
   the conflict by using a fully qualified name to indicate which class
   you are referring to.

For these reasons, we recommed you to use wildcard import statements with care.

All the standard classes in Zen are bundled in the `zen` package, which includes
other sub-packages. It includes a special package called `zen.core`. The classes
in this package are always implicitly imported to your source files. Many classes
such as `Object`, `Integer`, and `String` are defined in this package.

## Naming Conventions for Packages

You can use any identifier you wish to name your packages. However, we recommend
you to follow these naming conventions when you create your packages.

 * Packages are usually named using the name of the project.
   For example, imagine you are working a text editor called Kush. You can
   create a package named `kush` for all your classes. Using your project name
   allows you to create package names which are unique from the packages created
   by other programmers around the world.

 * Package names are usually written in lowercase letters. This helps you to
   avoid conflicts with class names.

 * You can add other subpackages to the package named after your project.
   For example, you can create a subpackage named `workspace` and place all its
   source files under the `kush.workspace` package. It can further contain other
   subpackages. However, we recommend you to work with two levels of packages
   to avoid convolution.