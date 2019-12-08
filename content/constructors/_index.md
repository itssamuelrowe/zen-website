+++
title = "Constructors"
chapter = true
weight = 11
+++

### Chapter 11
# Constructors: How Your Objects are Initialized

When you create an object using the `new` operator, Zen does several things
for you.

Here is the gist of what happens when you create an object.

 * First, the memory to store the object is allocated.
 * The allocated memory buffer is initialized internally to create the
   object.
 * The object is associated with the class from which it was created.
 * The virtual function tables are generated.
 * Finally, a special function defined in the objects class is invoked.
   This function is called a constructor.

In this chapter, we will learn about constructors. We will see how to work with
constructors, including their declaration and invocation.