+++
title = "Determining the Size of Strings"
weight = 3
+++

You can determine the size of a string using the immutable `size` property.
The size of a string is basically the number of code points it contains.

Here is an example which prints the size of a string.

```
// StringSize.zen

function main(...arguments)
    var name = 'Shazam'
    printf('The size of "%s" is %d.\n', name.size)
```

The example above produces the following output:
```
The size of "Shazam" is 6.
```

The size of a string is an important value when you want to manipulate strings.