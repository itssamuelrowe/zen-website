+++
title = "Arrays"
weight = 16
+++

In this module, you will learn about arrays and multdimensional arrays.

So far in this documentation, you have written programs which work with few
variables. For example, consider a program which stores the details of a student
and prints it out. You would create a class to represent the student. Each instance
of this class stores the details of a student, therefore, you would create a variable
which references a student object. What if there were four students? You would create
four variables which reference four student objects. What if there were a hundred
students, or even thousand? In such cases creating hundreds of variables is
absurd.

A better solution would be to use an array which keeps track of the students.
Arrays in Zen are implemented by the `Array` class. As of this writing, arrays
are not a fundamental type is Zen.

An array is an object which stores a fixed number of values of the same type.
It is a linear data structure, which means the values are stored in a sequence.
Each value stored in an array is known as an element, item, or value.
You can store any type of value that you can store in a variable. However, you
can store only one type of value once you create it. For example, if you
have an array of integers, you cannot store strings in it. The type of values
an array can store is known as its component type.

> Zen actually includes classes which implement the full fledged
> behavior of lists, which can grow dynamically. A particular list known as
> array list, which internally stores the values using arrays, is a fundamental
> type, i.e., it is treated specially.

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
you can store any object in Zen. Further, an array itself is an object, which
means you can store an array inside another array. You will learn more about this
later in this module.

## Working with Arrays

In order to work with arrays you need follow these steps.

 * Declare a variable to reference the array object.
 * Create a new array object.
 * Assign the reference of the array object to the variable.
 * Store information in the newly created array.

Before you start working with an array, you need to create a variable that
can store a reference to the array object. You have already learnt how to create
variables. Therefore, we will not waste any time revisiting the topic. You just
need to know that arrays are objects, which means their reference can be stored
in variables like any other object.

After you declare the array variable, you need to create an array object and
assign its reference to the variable. You can create arrays in two different ways.
The first technique is to use the `array()` function and the other is to use one
of the many constructors defined in the `Array` class.

An array has a fixed size that is set when your create it. You cannot change
the size of an array after you create it. You can determine the size of an
array by using the `size` property of an array object.

The `array()` function accepts a list of expressions separated by commas. The
list of expressions is enclosed within parentheses. The commas separate the values
of the array elements. The array will large enough to hold the number of elements
you specify in the array initializer. With this technique, you do not have to use
the new operator. The main advantage of this technique is, when you know the
initial values of your array you do not have to write multiple statements for
allocating and initializing your array.

For example, to store the days of the week you would create an array like this.
```
// Days.zen

function main(... arguments)
    var days = array(
        'Sunday',
        'Monday',
        'Tuesday',
        'Wednesday',
        'Thursday',
        'Friday',
        'Saturday')
    print('The second day of the week is ' + days[1])
```

In this example, you create an array that consists of the days in a
week. A print statement prints the second day of the week. Notice that we used
`1` as the index to access `'Monday'`. This is because array indexes start from
zero.

You can use the `makeArray()` function to create an array without specifying
the initial values.

Here is the general syntax of the `makeArray()` function.
```
makeArray(size)
```

Here, `size` indicates the capacity of the array, that is, the number of
elements it can store.

Here is an example of allocating an array capable of storing 7 object references.
```
var objects = makeArray(7)
```

In this example, the declaration and allocation is combined in the same statement.
It allocates an array with 7 slots, where you can store seven references.

When you create an array object using `makeArray()`, you are basically
creating empty slots where you can store references to objects. You should
remember that allocating an array does not allocate objects in the slots. You
must manually allocate objects and store their references in the array later.
In fact, when you create an array, Zen automatically initializes the slots to
null reference. The keyword `null` refers to a null object and can be used
stored in any reference variable. Unlike C and C++, the null reference is not
equivalent to 0 or the null character (`\0`).

An array size can be zero or more. If you specify a negative size, Zen throws
the `NegativeArraySizeException`.

Here is an example of allocating a negative sized array.
```
// NegativeArraySizeExample.zen

function main(...arguments)
    var daysOfWeek = makeArray(-1)
```

When you run this example, Zen throws an exception.

## Initializing Arrays

When you create an array using `makeArray()`, each slot in an array contains
a default value, which is `null`. Therefore, you must assign a value to each slot
before using it. There are two ways in which you can accomplish this, that is,
manually initialize each slot or specify a default value to `makeArray()` function.

Once you have allocated an array, you can access a specific element in the array
using the index enclosed in square brackets, known as the subscript operator.
An index starts at zero and extend to `n - 1`, where `n` is the size of the array.

Here is the general form of accessing an element in an array using the subscript
operator.
```
identifier[index]
```

The identifier represents the name of the array variable. The index indicates
the element slot which you want to access.

Here is an example which creates an array of three integers and assigns their
respective slots.
```
var marks = makeArray(3)
marks[0] = 40
marks[1] = 63
marks[2] = 55
```

Here is another version of the days of the week program we saw in the previous
section.
```
// DaysOfWeekManual.zen

function main(...arguments)
    var daysOfWeek = makeArray(7)
    daysOfWeek[0] = 'Sunday'
    daysOfWeek[1] = 'Monday'
    daysOfWeek[2] = 'Tuesday'
    daysOfWeek[3] = 'Wednesday'
    daysOfWeek[4] = 'Thursday'
    daysOfWeek[5] = 'Friday'
    daysOfWeek[6] = 'Saturday'
    printf('The fourth day of the week is %s.\n', daysOfWeek[3])
```

In this example, you create an array that consists of the days in a
week. The array is manually initialized by assigning each slot. A print statement
prints the fourth day of the week. Notice that we used `3` as the index to access
`'Wednesday'`. This is because array indexes start from zero.

In some situations, when you create an array using `makeArray`, you may
want each slot in the array to contain a default value other than `null`.
In such cases, you can use the overloaded version of `makeArray()`
that accepts a default value.

Here is an example an array whose slots are initialized to `0`.
```
// DefaultArrayValue.zen

function main(...arguments)
    var marks = makeArray(10, 0)
    for var i in range(0, marks.size)
        print(marks[i])
```

## Accessing Array Elements

After you have an array with initial values, you can read, modify, and test the
values in each slot. The value in a slot is accessed using the subscript operator.
You can write expressions like this using the subscript operator.
```
identifier[index] = value
```

Whenever you try to access an element with an index, Zen makes sure that you
are specifying a valid index. The index should always be greater than or equal
to zero and lesser than the size of the array, known as the arrays boundaries.
Unlike C and C++, in Zen you cannot access a slot outside the array's boundaries.
In case you try to access an element outside the arrays boundaries, Zen will
throw and `InvalidArrayIndexException`.

Here is an example which triggers an `InvalidArrayIndexException`.
```
// InvalidDayOfWeek.zen

function main(...arguments)
    var daysOfWeek = makeArray(7)
    daysOfWeek[0] = 'Sunday'
    daysOfWeek[1] = 'Monday'
    daysOfWeek[2] = 'Tuesday'
    daysOfWeek[3] = 'Wednesday'
    daysOfWeek[4] = 'Thursday'
    daysOfWeek[5] = 'Friday'
    daysOfWeek[6] = 'Saturday'
    printf('The seventh day of the week is ' + daysOfWeek[7])
```

Since the size of the array is `7`, the last valid index is `6`. In this example,
the program tried to access the slot at index `7`, which is invalid index.
This is why Zen throws an `InvalidArrayIndexException`.

Every array object exposes a property called `size`. You can use this to determine
the size of an array. Note that this property is immutable, which means the runtime
will throw an exception if you try to modify it.

## Understanding Multidimensional Arrays

In Zen all arrays are objects, which means you can store an array inside another
array. Such an arrangment of arrays allows you to create multidimensional
arrays.

The two dimensional array is very common compared to other higher dimensional
arrays. A common use of a two dimensional array is to represent data in grids,
such as cartesian planes and matrices.

Here is an example of a two dimensional array.
```
var matrix = new Array(Integer, 5, 10)
```

This example allocates an array with 5 slots in the first dimension. After which,
5 arrays of size 10 are created and assigned in each of those slots. Which means,
there are 50 slots in the array, organized in two dimensions.

Here is an example program, which prints the layout of the two dimensional
array.

```
// TwoDimensionalArrayExample.zen
function main(...arguments)
    var matrix = new Array(Integer, 5, 10)

    var k = 0
    for var i in range(0, matrix.size)
        for var j in range(0, matrix[i].size)
            matrix[i][j] = k
            k += i

    for var i in range(0, matrix.size)
        for var j in range(0, matrix[i].size)
            printf('%d\t', matrix[i][j])
        print()
```

This example produces the following output.
```
0       1       2       3       4       5       6       7       8       9
10      11      12      13      14      15      16      17      18      19
20      21      22      23      24      25      26      27      28      29
30      31      32      33      34      35      36      37      38      39
40      41      42      43      44      45      46      47      48      49
```

Zen allows you allocate memory for the first `n` dimensions. You can allocate
other dimensions later.

Here is an example which demonstrates this technique.
```
var array = new Array(Integer, 3)
array[0] = new Array(Integer, 4)
array[1] = new Array(Integer, 8)
array[2] = new Array(Integer, 2)
```

In this example, you allocate memory for the first dimension of the array.
Then you manually allocate the second dimension. The main advantage of this
technique is that it allows you to create different sized arrays in a given
dimension. Arrays with such layout are known as jagged arrays.

Here is a modified version of the earlier program which prints the layout
of an unevenly distributed multidimensional array.

```
// JaggedArrayExample.zen

function main(...arguments)
    var array = new Array(Integer, 3)
    array[0] = new Array(Integer, 4)
    array[1] = new Array(Integer, 8)
    array[2] = new Array(Integer, 2)

    var k = 0
    for var i in range(0, array.size)
        for var j in range(0, array[i].size)
            array[i][j] = k
            k += i

    for var i in range(0, array.size)
        for var j in range(0, array[i].size)
            printf('%d\t', array[i][j])
        print()
```

The output of this program is shown here.

```
0       1       2       3
4       5       6       7       8       9       10      11
12      13
```

Unevenly distributed multidimensional arrays are not very common. This is usually
not how multidimensional arrays are designed. However, irregular arrays are useful
in some cases.

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

+++
title = "Iterating Over Multidimensional Arrays"
weight = 7
+++

You can either use the for statement or the while statement for traversing
multidimensional arrays. You need to remember that multidimensional arrays consist
of arrays of arrays. When you use loops to iterate over multidimensional arrays,
the easiest way is to use nested loop statements. This is important when
iterating over a multidimensional array, because each iteration retrieves the
next array dimensions, until you reach the last dimension.

In general, you will have `k` depth of nested loop statements, to iterate over an
array of `k` dimensions, because you will have `k - 1` array objects, here `1`
represents the last dimension where values are stored.

For example, you will need two for statements nested to iterate over an array of
2 dimensions. You will use the outer loop to retrieve an array object and the
inner loop to retrieve the values.

Similarly, you will need three for statements nested to iterate over an array of
3 dimensions. You will use the outer loops to retrieve the array objects, each
loop statement unwraps a dimension. You will use the inner-most loop to retrieve
the values.

```
// Traversing2DArray.zen

function main(...arguments)
    var matrix = array(
        array(10, 20, 30),
        array(40, 50, 60),
        array(70, 80, 90))

    for var i in range(0, matrix.length)
        var row = matrix[i]
        for var j in range(0, row.length)
            printf('%d\t', row[j])
        print()
```

The output of this example is shown here.
```
10    20    30
40    50    60
70    80    90
```

In this example, a two dimensional array is used to represent a matrix.
The first dimension contains the rows of the matrix. Each row is simply the
second dimension of the array.

Like we said earlier, the outer most loop unwraps a dimension. In this example,
the outer most loop unwraps a dimension which gives us the matrix row.
Then we iterate over the row and print the elements.

Notice how `print()` and `printf()` are used. The `print()` method prints
a newline character whenever it prints something. Whereas, the `printf()` method
does not print any newline character. With this concept in mind, we print a new
line only at the end of a row. Thus, we format the output to represent a matrix.

Here is another example of traversing a two dimensional array using a while
loop.
```
// Traversing2DArray2.zen

function main(...arguments)
    var matrix = array(
        array(10, 20, 30),
        array(40, 50, 60),
        array(70, 80, 90))

    var i = 0
    while i < matrix.length
        var row = matrix[i]
        var j = 0
        while j < row.length
            printf('%d\t', row[j])
            j += 1
        print()
        i += 1
```

The output of this example is shown here.
```
10    20    30
40    50    60
70    80    90
```