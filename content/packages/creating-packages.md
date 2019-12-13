+++
title = "Creating Packages"
weight = 2
+++

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