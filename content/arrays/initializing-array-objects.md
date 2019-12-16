+++
title = "Initializing Array Objects"
weight = 3
+++

When you create an array using the `Array` class, each slot in an array contains
a default value, which is `null`. Therefore, you must assign a value to each slot
before using it. There are two ways in which you can accomplish this, that is,
manually initialize each slot or specify a default value to the `makeArray` function.
You will learn these techniques in this section.

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
var marks = new Array(3)
marks[0] = 40
marks[1] = 63
marks[2] = 55
```

Here is another version of the days of the week program we saw in the previous
section.
```
// DaysOfWeekManual.zen

function main(...arguments)
    var daysOfWeek = new Array(String, 7)
    daysOfWeek[0] = 'Sunday'
    daysOfWeek[1] = 'Monday'
    daysOfWeek[2] = 'Tuesday'
    daysOfWeek[3] = 'Wednesday'
    daysOfWeek[4] = 'Thursday'
    daysOfWeek[5] = 'Friday'
    daysOfWeek[6] = 'Saturday'
    printf('The fourth day of the week is %s.\n', daysOfWeek[3])
```

In this example, you create an array of String. It consists of the days in a
week. The array is manually initialized by assigning each slot. A print statement
prints the fourth day of the week. Notice that we used `3` as the index to access
`'Wednesday'`. This is because array indexes start from zero.

In some situations, when you create an array using the `Array` class, you may
want each slot in the array to contain a default value other than `null`.
In such cases, you can use the `makeArray()` function
which accepts a default value.

Here is an example an integer array whose slots are initialized to `0`.
```
// DefaultArrayValue.zen

function main(...arguments)
    var marks = makeArray(Integer, 10, 0)
    serialize(marks, System.out)
```