+++
title = "Understanding Package Lookup"
weight = 4
+++

Your packages should be organized correspondingly in your directories. But how
does the Zen Virtual Machine determine which directory to look for your packages?

By default Zen looks for packages in the current working directory, the directory
from where you are invoking the virtual machine. Further, the Zen Virtual Machine
looks for packages in the directories listed in the search path of the application.
You can specify the search path for an application in two ways.

 * Create the `ZEN_SEARCH_PATH` environment variable and store the directories
   where your packages are stored. You usually need to avoid this technique because
   it applies to all the applications that run on the Zen Virtual Machine, not
   just one application.

 * Specify the search path with the `--search` parameter when you invoke the
   Zen Virtual Machine. This is the preferred way to specify the search path.
   This allows the search path to be specific to individual programs, without
   affecting other programs.

The general form of a search path is shown here.
```
path1;path2;path3
```

The paths point to the directories where your packages are stored. The semicolon
separates the paths. However, you can use semicolons only on Windows. If you
are using other operating systems such as Unix, Linux and MacOS you need to
use the colon (`:`) symbol to separate the paths.

Consider the following package which declares a class.
```
// com/example/Message.zen

class Message

    var message
    
    function new(message)
        this.message = message

    function toString()
        return message
```

Now create another class in the default package like this.
```
// PackageExample.zen

function main(...arguments)
    var message = new com.example.Message('Hello, world!')
    print(message)
```

The `PackageExample` classs is declared in the default package. Whereas, the
`Message` class is declared in the `com.example` package. The `PackageExample` class
uses the `Message` class, which is declared in another package. Therefore, you
need to specify the fully qualified name of `Message`, which is `com.example.Message`.
Basically, the fully qualified name of the `Message` class consists of its
containing package and its name.

However, classes in the same package can access other classes without their fully
qualified names. Assume two classes, `com.example.Message` and `com.example.User`,
both the classes are in the same package. The `User` class can access `Message`
without its fully qualified name, and vice versa.

In order for your program to find the `Message` class, one of following conditions
should be met.
    
 * The program should be executed from a directory immediately above the `com.example`
   package.
 * The `ZEN_SEARCH_PATH` environment variable must include the path to `com\example`.
 * The `--search` parameter must specify the path to `com\example`.

When you specify a search path, the path should not include `com\example` itself.
Instead you need to specify the directory which contains the package directory.
Assume the `com\example` directory is stored in `C:\learning\com\example`.
You need include `C:\learning` in the search path, not `C:\learning\com\example`.

We recommend you to run the example programs from their root directories. Which
means you do not have to create the search path for now. For example, assume the
`PackageExample` program shown earlier was stored in `C:\learning` and the
`com.example` package was stored in `C:\learning\com\example`. To run this program,
you need to execute the following commands in sequence from `C:\learning`.
```
C:\learning>zen PackageExample.zen com/example/Message.zen
C:\learning>zvm PackageExample
```

The output of the program is shown here.
```
Hello, world!
```

The commands for other operating systems are similar with little tweaks.