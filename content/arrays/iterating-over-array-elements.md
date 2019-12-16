+++
title = "Iterating Over Array Elements"
weight = 6
+++

So far, you have learnt how to access array elements manually. In most cases,
you will automate this process with a loop. You will often encounter code which
iterates over the elements of an array. You will learn about this technique
in this section.

### Traversing with While Loop

Here is an example of iterating through the elements of an array using
a while loop.

```
// ArrayTraversing.zen

function main(...arguments)
    var daysOfWeek = array(
        'Sunday',
        'Monday',
        'Tuesday',
        'Wednesday',
        'Thursday',
        'Friday',
        'Saturday')
    var i = 0
    while i < daysOfWeek.size
        print(daysOfWeek[i])
        i += 1
```

Here, the loop control variable `i` serves two purposes here. One, it is used to
control the repetition of the loop and the other is to automate the generation of
indexes. As you can see, i varies from zero to `daysOfWeek.length - 1`, which is
indicated by `i < daysOfWeek.length`. Since array indexes start from zero and
end at `n - 1`, where n is the length of the array, this allows you to use the
variable `i` as an array index. Thus, the elements of the array are read in a
strictly linear fashion, from the start to end.

Here is an example program which shows how `i` varies in the while loop.
```
// IndexGenerationExample.zen

function main(...arguments)
    var daysOfWeek = array(
        'Sunday',
        'Monday',
        'Tuesday',
        'Wednesday',
        'Thursday',
        'Friday',
        'Saturday')
    var i = 0
    while i < daysOfWeek.size
        print(i)
        i += 1
```

This program generates the following output.
```
0
1
2
3
4
5
6
```

### Traversing with For Loop

The for loop is designed to iterate through a collection of objects, such as
arrays and lists.

The general form of the enhanced for statement is shown here.
```
for var identifier in iterable
    statement
```

Here, `var` is optional and its inclusion indicates an inline declaration of a
variable. The variable identified by the specified `identifier` is referred to
as the iteration variable. Its importance is explained shortly. The `iterable`
part represents an expression that must evaluate to an object whose type extends
the `Iterable` class or at least implements the `getIterator()` function.

The for statement first evaluates the expression specified by the iterable part
and retreives an iterator for the given iterable. In other words, the iterable
specifies a the iterator source whose elements are supposed to be processed.
In each iteration, an element from the iterable is retrieved through the iterator
and stored in the iteration variable. The loop repeats until all elements in the
collection have been processed. Further, you can force the loop to stop with break,
throw, and return statements as usual.

An iterable is an object that returns an iterator. Iterable objects can be seamlessly
traversed with for statements. Interestingly, iterators are iterable objects, too!
Iterators return a reference to themselves in their respective `getIterator()`
functions. Which means iterators can be used directly in for loops without being
wrapped with decorator objects.

In fact, the `range()` function returns an instance of the `IntegerRangeIterator`
class. To the state the obvious, this class extends the `Iterator` class which
makes its instances iterators. If iterators were not iterables, you would not be
able to use the `range()` function with for loops directly.

There are various types of objects in Zen that can be used with the for statement.
In this section, we will show you to loop through an array. Please refer the
Zen API documentation for more information.

Here is an example of iterating through the elements of an array
using the for loop.

```
// TraversingArray2.zen

function main(...arguments)
    var daysOfWeek = array(
        'Sunday',
        'Monday',
        'Tuesday',
        'Wednesday',
        'Thursday',
        'Friday',
        'Saturday')
    for var dayOfWeek in daysOfWeek
        print(dayOfWeek)
```

This example is simpler than the example shown earlier, which used an index.
You can always use the for loop whenever you do not need an index or your
iteration is always strictly linear. In all other cases, you need to
use the while statement.

Here is another example of iterating through the elements of an array using the
for statement.

```
// ArrayTraversing3.zen

function main(...arguments)
    var daysOfWeek = array(
        'Sunday',
        'Monday',
        'Tuesday',
        'Wednesday',
        'Thursday',
        'Friday',
        'Saturday')
    for var i in range(0, daysOfWeek.length)
        print(daysOfWeek[i])
```

This example produces the following output.
```
Sunday
Monday
Tuesday
Wednesday
Thursday
Friday
Saturday
```

In this example, we created an array of strings, which stores the days of a week.
We use a combination of the for loop and `range()` function to iterate over the
array elements and print them on the console.