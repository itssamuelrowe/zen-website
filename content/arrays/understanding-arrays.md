+++
title = "Understanding Arrays"
weight = 1
+++

An array is an object which stores a fixed number of values of the same type.
It is a linear data structure, which means the values are stored in a sequence.
Each value stored in an array is known as an element, item, or value.

You can store any type of value that you can store in a variable. However, you
can store only one type of value once you create it. For example, if you
have an array of integers, you cannot store strings in it. The type of values
an array can store is known as its component type.

You can store a list of items of the same reference type in an array. Each
element in an array is stored in a slot. Each slot in an array is assigned a
number known as index. You can access an element with its index. An index is
always positive and lesser than the size of the array.

Assume your array can store ten elements. The index number begins at 0 and ends
at 9. The first element is at index 0, the second at index 1, and so on. In any
given array, the minimum valid index is always 0 and the maximum valid index
is always `n - 1`, where `n` is the size of the array. 

If you are new to programming, you may think in an array of ten elements, the
5th index would refer to the fifth element. This is wrong. An index numbers
starts at zero, the first element is at zeroth index, the first element is at the
second index, and so on. Which means the fifth index actually refers to the sixth
element. Most beginners find this concept very confusing. You need to learn and
practiceto grasp this concept well. In fact, most experienced programmers make
mistakes with indexes, too.

Since indexes start from zero in Zen, they are also known as zero based indexes.
Most programming languages use zero based indexes. Therefore, we recommend
you to get used to counting from zero instead of one. If you notice the loops
we designed in the earlier chapters, most of the loop control variables start
from 0. With enough practice, counting from 0 becomes a habit.

When it comes to class types, an array can hold instances of the class or any
of its subclasses. Which goes to say, if you have an array of the `Object` class,
you can store any object in Zen.

Further, an array itself is an object, which means you can store an array inside
another array. You will learn more about this later in this chapter.