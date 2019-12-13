+++
title = "Understanding Qualified Names"
weight = 3
+++

You can create a hierarchy of packages using a qualified name. We mentioned this
term in the previous section without going into its details.

A qualified name is a sequence of identifiers separated by dots.
Here are some examples of qualified names.

```
zen.core
zen.support
zen.io
com.onecube
com.onecube.model
com.onecube.storage
```

Here is the general form of a qualified name.
```
identifier1.identifier2.identifier3
```

Each identifier in a qualified name, separated by a dot, creates a node or level
in your hierarchy. A package hierarchy must be reflected in your file system.
Which means, if you change the name of your package, you should change the
directory structure, too.

For example, a package `com.example` should be stored in the directory `com/example`.