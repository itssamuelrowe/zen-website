+++
title = "Arrays"
chapter = true
weight = 16
+++

### Chapter 16
# Arrays

So far in this manual, you have written programs which work with few variables.
For example, consider a program which stores the details of a student and prints
it out. You would create a class to represent the student. Each instance of this
class stores the details of a student, therefore, you would create a variable which
references a student object. What if there were four students? You would create
four variables which reference four student objects. What if there were a hundred
students, or even thousand? In such cases creating hundreds of variables is
absurd.

A better solution would be to use a list which keeps track of the students.
Zen provides a class known as an array which is similar to lists. Arrays are not
a fundamental type is Zen. In this chapter you will learn about arrays, their
declaration and initialization. Finally, we will learn a variation of arrays
known as multdimensional arrays.

Interestingly, Zen actually includes classes which implement the full fledged
behavior of lists. A particular list known as array list, which internally stores
the values using arrays, is a fundamental type. It is treated specially by Zen.