+++
title = "Working with the Import Statement"
weight = 5
+++

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
as classes, functions, enumerations, and annotations.

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