+++
title = "Working with Arrays"
weight = 2
+++

In order to work with arrays you need follow these steps.

 * Declare a variable to reference the array object.
 * Create a new array object.
 * Assign the reference of the array object to the array variable.
 * Store information in the newly created array.

## Declaring Array Variables

Before you start working with an array, you need to create a variable that
can store a reference to the array object. You have already learnt how to create
variables. Therefore, we will not waste any time revisiting the topic. You just
need to know that arrays are objects, which means their reference can be stored
in variables like any other object.

## Creating Array Objects

After you declare the array variable, you need to create an array object and
assign its reference to the variable. You can create arrays in two different ways.
The first technique is to use the `array()` function and the other is to use one
of the many constructors defined in the `Array` class.

An array has a fixed size that is set when your create it. You cannot change
the size of an array after you create it. You can determine the size of an
array by using the `size` property of an array object.

### Using the array() Function

The `array()` function accepts a list of expressions separated by commas. The
list of expressions is enclosed within parentheses. The commas separate the values
of the array elements. The array will large enough to hold the number of elements
you specify in the array initializer. With this technique, you do not have to use
the new operator.

The main advantage of this technique is, when you know the initial values
of your array you do not have to write multiple statements for allocating and
initializing your array.

For example, to store the days of the week you would create an array like this.
```
// DaysOfWeek.zen

function main(... arguments)
    var daysOfWeek = array(
        'Sunday',
        'Monday',
        'Tuesday',
        'Wednesday',
        'Thursday',
        'Friday',
        'Saturday')
    printf('The second day of the week is %s.\n', daysOfWeek[1])
```

In this example, you create an array . It consists of the days in a
week. A print statement prints the second day of the week. Notice that we used
`1` as the index to access `'Monday'`. This is because array indexes start from
zero.

### Using the New Operator to Allocate Array Objects

Arrays are objects in Zen. Therefore, you can use the new operator to create a
new instance of the `Array` class.

Here is the general syntax of the new operator when allocating an array.
```
new Array(size)
```

Here, the `size` indicates the capacity of the array, that is, the number of
elements it can store.

Here is an example of allocating an array capable of storing 7 object references.
```
var objects = new Array(7)
```

In this example, the declaration and allocation is combined in the same statement.
It allocates an array with 7 slots, where you can store seven references.

When you create an array object using the new operator, you are basically
creating empty slots where you can store references to objects. You should
remember that allocating an array does not allocate objects in the slots. You
must manually allocate objects and store their references in the array later.

In fact, when you create an array, Zen automatically initializes the slots to
null reference. The keyword `null` refers to a null object and can be used
stored in any reference variable. Unlike C and C++, the null reference is not
equivalent to 0 or the null character (`\0`).

You can create arrays with specific components like this:
```
new Array(type, size)
```

Here, the type indicates the component type of the array.

Take a look at this example where the allocated array can store only integers.
```
var marks = new Array(Integer, 10)
```

An array size can be zero or more. If you specify a negative size, Zen throws
the `NegativeArraySizeException`.

Here is an example of allocating a negative sized array.
```
// NegativeArraySizeExample.zen

function main(... arguments)
    var daysOfWeek = new Array(-1)
```

When you run this example, Zen throws an exception like this.
```
Exception in thread 'main' zen.core.NegativeArraySizeException: -1
    at NegativeArraySizeExample.main(NegativeArraySizeExample.zen:4)
```