+++
title = "Constructors of the String Class"
weight = 2
+++

The `String` class exposes many constructors. You will learn about a few of
these constructors in this section. Please refer the Zen API documentation for
more information.

#### Creating Empty Strings

You can create an empty string by calling the default constructor.
An empty string basically contains no characters.

Here is an example.
```
var emtpyString = new String()
```

#### Creating Strings From Array of Characters

The `String` class implements a constructor which accepts an array of characters.
This allows you to create a string from an array of characters. 
```
function new(sequence)
```

Here is an example which demonstrates how you can create strings using arrays.
```
var sequence = arrayEx(String, 'F', 'e', 'b', 'r', 'u', 'a', 'r', 'y' )
var string = new String(sequence)
```

This creates a string that holds the text `'February'`.

You can further specify a range within the array you want the
constructor to copy using this constructor.

```
function new(sequence, startIndex, count)
```

Here, the `startIndex` indicates the index from where the characters should be
copied. It is inclusive, which means the string at the start index is also
included. The count parameter indicates the number of characters to copy,
beginning the copy at the start index.

The following example demonstrates this constructor.

```
var sequence = arrayEx(String, 'F', 'e', 'b', 'r', 'u', 'a', 'r', 'y')
var string = new String(sequence, 3, 2)
```

This creates a string which represents `'ru'`. Remember indexes in Zen always
begin at `0`, therefore, `3` indicates the fourth character.

#### Cloning Strings

You can create a copy of the string object using the `clone()` function.

Here is an example.
```
// StringCopy.zen

function main(...arguments)
    var string1 = 'Hello'
    var string2 = string1.clone()
    print(string1 is string2)
    print(string1 == string2)
```

The first string contains the text `'Hello'`. We create another copy of this string.

Since the `is` operator tests if both the variables contain the same reference,
the first print statement prints false. In other words, the variables `string1`
and `string2` hold two different references. However, they hold logically equal
objects because they both contain the same text. To prove that they contain the
same text, we use the `==` operator, which invokes the `equals()` function. This
is why the second print statement prints `true`.

There are many other constructors implemented in the `String` class. We encourage
you to learn more about these constructors from the Zen API documentation.