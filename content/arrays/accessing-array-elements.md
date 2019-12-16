+++
title = "Accessing Array Elements"
weight = 4
+++

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
    var daysOfWeek = new Array(String, 7)
    daysOfWeek[0] = 'Sunday'
    daysOfWeek[1] = 'Monday'
    daysOfWeek[2] = 'Tuesday'
    daysOfWeek[3] = 'Wednesday'
    daysOfWeek[4] = 'Thursday'
    daysOfWeek[5] = 'Friday'
    daysOfWeek[6] = 'Saturday'
    printf('The seventh day of the week is %s.\n', daysOfWeek[7])
```

This example produces the following output.

```
Exception in thread 'main' zen.core.InvalidArrayIndexException: The specified index 7 is invalid for an array of size 7.
    at InvalidDayOfWeek.main(InvalidDayOfWeek.zen:12)
```

Since the size of the array is `7`, the last valid index is `6`. In this example,
the program tried to access the slot at index `7`, which is invalid index. 
This is why Zen throws an `InvalidArrayIndexException`.

Every array object exposes a property called `size`. You can use this to determine
the size of an array. Note that this property is immutable, which means the runtime
will throw an exception if you try to modify it.