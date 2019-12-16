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