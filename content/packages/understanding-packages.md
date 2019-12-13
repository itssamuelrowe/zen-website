+++
title = "Understanding Packages"
weight = 1
+++

A package is a group of related classes, annotations and enumerations bundled
together. Henceforth, when we refer to classes in this chapter we mean to include
other components such as annotations and enumerations, unless stated otherwise.

Packages are like containers that provide your classes a namespace. For example,
a package allows you to create two classes named `Scanner`. You simply need to
store the classes in different packages. However, the class names should be
unique within their respective packages.

A package provides a namespace and visibility control to your classes. You can
tell which classes are available to the world outside your package.

> As of now, Zen allows only public classes. In the future, the visibility of
> classes outside a package can be manipulated by the developer.

Packages are organized in a hierarchical fashion. When you want to use a class
from a different package, you need to import it. So far in this course, all the
classes you created were stored in the default package. Which means you had to
provide a unique name for each class to avoid name conflicts. Without packages
you would soon run out of relevant, convenient and descriptive names for your
classes.

Further, without packages you would need to make sure that the name you choose
for your classes are different from the class names chosen by other programmers.
In fact, the Zen API consists of hundreds of classes. It would be impossible
to find a unique name for each of these classes. This is why, the Zen API is
ogranized as packages.