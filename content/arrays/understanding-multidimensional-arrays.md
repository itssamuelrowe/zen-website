+++
title = "Understanding Multidimensional Arrays"
weight = 5
+++

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