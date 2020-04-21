---
title: "Why I Created Zen: Yet Another Programming Language"
description: "Zen is a general-purpose programming language designed to build simple, reliable and efficient programs."
image: "images/blog/why-i-created-zen.jpg"
author: "Samuel Rowe"
---

Zen is a general-purpose programming language designed to build simple, reliable and efficient programs. When I say simple, reliable, and efficient I mean it. The syntax of Zen is designed to be clear, which means the code you write speaks for itself. Further, the architecture of the runtime is designed to run your programs reliably, regardless of the platform, with efficiency. You can develop Zen applications in nearly any environment and deploy with little to no performance loss irrespective of the platform.

As of this writing, Zen is currently under development. The alpha version of the compiler and virtual machine will be available shortly. Meanwhile, you can browse the source code at https://github.com/itssamuelrowe/zen.

I decided to create my own programming language because of my interest in compiler design since 9th grade. Also, I did not find any existing language that met all of my needs. In this article, I will explain the concepts that I feel are necessary for a dynamically typed programming language that is both enjoyable and efficient. My goal is not to build a toy language but to create a full-blown programming language. Why? Because I think it is really cool to create a programming language that everybody loves.

## Simple

The syntax of Zen was intentionally designed to restrict the number of ways a certain task can be achieved. For example, unlike other dynamically typed programming languages methods and attributes cannot be introduced to an object at runtime. As a Zen programmer, you will focus more on the logic of your program rather than dealing with the convoluted state of your objects.
The tokens required to write your code are minimal. With this in mind, tokens such as semicolons to terminate simple statements, braces to enclose blocks, etc. which are common in C-like programming languages were removed.

Zen offers good readability and clear syntax with an emphasis on natural language. At first glance, code written in Zen looks almost like pseudo-code. You can write code and execute it quickly to test your ideas.

For newcomers and beginners, Zen is incredibly easy to learn and use. Given the learning curve is simple, you do not have to be an expert to apply Zen in your everyday life. Zen automatically takes care of things like garbage collection, releasing resources, etc. for you.

Are you still not convinced Zen is simple? In that case, here is an example of the binary search algorithm written in Zen.

```javascript
function search(values, key)
    var start = 0
    var end = values.size - 1
    var result = null
    for var i in range(0, end)
        var middle = (end - start) / 2
        if values[i] == key
             result = i
             break
        else if values[i] > key
            end = middle - 1
        else
            end = middle + 1
    return result

function main(...arguments)
    var values = array(53, 118, 519, 1216)
    var result = search(values, 27)
    if result != null
        print('Found key 27 at index ' + result + '.\n')
    else
        print('Could not find key 27.')
```

## Dynamically Typed

Zen is dynamically typed, which helps you avoid writing support code. However, it was designed to detect many programming errors at compile-time, where other dynamically typed languages report these errors at runtime. This provides the compiler with opportunities for optimizations. Thus, you can enjoy both the increased runtime efficiency and the developer experience.

In fact, the premise on which I started Zen was to create a programming language that was inspired by both Python and Java. The simple and clear syntax from Python was adopted to improve the developer experience. Similarly, the runtime architecture was inspired by Java to increase the runtime efficiency.

The hypothesis is that with certain restrictions on the language, both productivity and efficiency can be achieved. The restrictions imposed by the language allows the compiler to take advantage of static information available in the source code. For example, in Zen attributes and methods cannot be introduced dynamically to objects. Further, if static methods cannot be invoked via objects (like C#), the compiler can emit a single instruction to invoke static functions. Similarly, when methods invoke other methods in the same class, the compiler can simply emit an instruction to invoke the target method via the virtual method table. The same technique can be applied to attributes. Do you see what I am trying to say?

## Portable: Write Once, Run Anywhere

The programs you write in Zen are compiled to bytecodes that are encoded in a special binary format known as Binary Entity Format (FEB). When you run your program, the virtual machine interprets these bytecodes. For each platform, a specific implementation of the virtual machine is required. However, once the implementation is done, your programs can run on the virtual machine seamlessly.

## Lack of Implicit Idioms
Undefined values, truthy/falsy values, and many other implicit idioms are unavailable in Zen. The idea is to limit the number of ways you can express something. For example, Boolean values are always derived from relational and equality expressions. There is no implicit conversion of objects to Boolean values. This design choice, inspired by Java and C#, allows you to write readable and safe code.
Personally, I believe that more bugs arise from implicit idioms than other types of errors. Additionally, such bugs are hard to track down. For example, when a programming language treats dissimilar objects as if they were the same, it leads to unexpected behaviors when the programmer attempts to use them.

Here is an example from JavaScript. Given, JavaScript did not allow default parameters before ES6 was released, it was a common pattern to simulate default parameters as shown below.
```javascript
function example(value) {
    value = value || 1;
}
```

In this example, the function updates `value` to 1 when no argument is passed. However, if you tried to pass 0 as an argument, the truthy test in JavaScript would fail causing your variable to hold 1 instead of 0. Obviously, there is a better way of writing this. But we would not have this problem, to begin with, if the language did not have truthy/falsy values.

## Concurrency

In CPython and MRuby, the reference implementations of Python and Ruby, respectively, a global interpreter lock (GIL) exists. The GIL protects the internals of the interpreters from race conditions that could corrupt data. In a multithreaded context, this lock allows only one thread to execute code at any given time. For example, if you have 4 threads working on a 4-core machine, only one thread and one core will be active at any given time.

In Zen, the virtual machine implements threads as first-class citizens. The various internal components (including garbage collector, JIT compiler, class loader) are thread-safe. Therefore, the global interpreter lock does not exist. This means your programs can take complete advantage of multicore systems.

## Fast Compile Time

The simplistic design of Zen, both in terms of syntax and semantics, allows you to compile your source codes quickly. This stands true even though the compiler makes multiple passes.
Further, the dependency management in Zen is elegant. The compiler processes only classes that are directly imported. The programs you write in Zen are compiled to a compact binary format known as Binary Entity Format (FEB). When the compiled classes are imported from your source code, the compiler makes use of a simple symbol loader which discards unnecessary information and loads only the required symbols.

## Conclusion

I understand that this post was rather long. However, it presents a broad overview of some of the most important features of the Zen programming language. Many of the features discussed here are not available in Zen right now. However, this article describes the overall vision for Zen.

I believe creating Zen was worth giving a shot. At worst, I would have enjoyed three years learning to write a compiler and a virtual machine. On the other end, I would have created a programming language others appreciate. Finally, my deepest hope is that after reading this article, you will be motivated to explore Zen and find out how it might help with your own projects.

It should be noted that I am not a compiler design expert. I understand that the arguments I put forward in this post are easily beatable. In fact, I may be wrong about a few things that I mentioned. If you feel like getting in touch or would like to contribute, here is my email address: samuelrowe1999@gmail.com.

Thank you for reading.