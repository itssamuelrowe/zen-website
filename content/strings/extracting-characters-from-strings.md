+++
title = 'Extracting Characters From Strings'
weight = 5
+++

You can extract characters from strings in a number of ways. We discuss about
each technique in this section.

Internally, strings store characters in an array. The `String` class overrides
the subscript operator, which allows you to access characters in a string as if
it were an array. Many functions in the `String` class require indexes to operate.
Just like array, string indexes are zero based. So it would help you to understand
strings better if you think of them as arrays.

You can extract a single character from a string using the `getCharacter()` function.
It accepts an index of the character you want to retrieve. You cannot specify
negative values. It throws a `InvalidStringIndexException` if the index is invalid.

Here is the declaration of the `getCharacter()` function.

```
@Operator symbol='[]'
function getCharacter(index)
```

Here is an example.

```
// AccessingCharacter.zen

function main(...arguments)
    var color = 'Neon'
    var c = color.getCharacter(2)
    print(c)
```

This snipet prints the following output.
```
o
```

You can retrieve a range of characters at a time using the `getCharacters()` function.

Here is the declaration of the `getCharacters()` function.
```
function getCharacters(startIndex, stopIndex, destination, destinationIndex)
```

Here, the `startIndex` specifies the index from which the copying begins. It is
inclusive.

The `stopIndex` specifies the index at which the copying ends. This index is exclusive,
which means the character at this index is not copied.

The characters are copied to the `destination` array you specify. The characters
are copied into the destination array beginning at the index specified by
`destinationIndex`. You need to make sure that the destination array is large
enough to store the range of characters.

Here is an example which copies a range of characters.

```
// CharacterExtraction.zen

function main(...arguments)
    var message = 'How you doin?'
    var startIndex = 4
    var stopIndex = 7
    var destination = new Array(Character, 3)
    message.getCharacters(startIndex, stopIndex, destination, 0)

    var message2 = new String(destination)
    print(message2)
```

This example prints the following.
```
you
```

If you want to convert all the characters in your string into a character array,
invoke the `toCharacterArray()` function. It returns an array of characters from
your string.

The declaration of the `toCharacterArray()` function is shown here.
```
function toCharacterArray()
```

You can use the `getCharacters()` function to perform the same operation, except
`getCharacters()` makes you write more code.

## Extracting Substrings

The `substring()` function allows you to extract a region of your string, usually
referred as substring.

The declaration of this function is shown here.
```
function substring(index)
```

Here, the index indicates the index from which the substring is extracted.
The substring begins from the specified index and extends to the end of the
string.

Here is an example of the `substring()` function.
```
// SubstringExtraction.zen

function main(...arguments)
    var lastName = 'Nikola Tesla'.substring(7)
    printf('%s was one of the greatest inventors to ever live!\n', lastName)
```

This example prints the following output.
```
Tesla was one of the greatest inventors to ever live!
```

An overloaded version of the `substring()` function allows you to extract a
range of characters from the string.

Here is the declaration of the `substring()` function.
```
function substring(startIndex, stopIndex)
```

Here the `startIndex` specifies the start index of the substring and the
`stopIndex` specifies the end index of the substring. The `startIndex` is
inclusive, whereas, the `stopIndex` is exclusive.

Here is an example of the overloaded version of the `substring()` function.
```
var substring = 'Nikola Tesla'.substring(2, 6)
println(substring)
```

This example prints the following output.
```
kola
```