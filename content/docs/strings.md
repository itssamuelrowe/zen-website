+++
title = "Strings"
chapter = true
weight = 16
+++

### Chapter 16
# Strings

A string is a very common object in Zen. You have used strings throughout
this manual. You have seen how to use string literals, how to concatenate
strings, and how to compare strings. However, strings are much more powerful
and support a wide variety of operations.

In this chapter, you will learn more about strings.


+++
title = "Understanding Strings"
weight = 1
+++

In Zen, strings are not primitive reference types. Strings are implemented by the
`String` class defined in the `zen.core` package. All strings are objects and Zen
treats strings specially.

A string is a sequence of characters. You can create a string by enclosing your
text in single quotes. The character sequence along with the single quotes
form a string literal.

Unlike many other programming languages, string are not arrays of characters.
Internally the `String` class stores the characters in an array, a detail which
you can safely ignore. But you always need to perceive strings as objects and
not arrays.

So far you have seen only one way to create a string object: to use the string
literal. However, the `String` class exposes many constructors, which allow
you to create strings in many ways.

You can perform various operations with strings, such as comparing two strings,
searching for substrings, concatenating two strings, and so on. However, you
cannot modify them because string objects are immutable. In other words, once a
string object is created, you cannot change its characters. You can only derive
a new string which is a modified version of the original string. At first, this
may seem to be a serious restriction. However, immutable strings make your life
easier. You can still perform all types of string operations. Immutable strings
are more efficient than mutable strings.

Zen provides other mechanisms which allow you to derive modified versions of a
string. Each time you derive a new version of the string, you are creating a
new string object. The original string is always left as it is.

If you have to make many changes to a string, deriving a new string for each
change is not efficient. For such situtations, Zen provides the `StringBuilder`
class, which internally represent strings as arrays. So whatever changes you make
will be quick and efficient. Once you are satisfied with the changes, these
classes allow you to derive an immutable string. After which, you can use the
string as usual.

The String and StringBuilder classes are defined in the `zen.core` and `zen.text`
packages, respectively. Therefore, all these classes are available to your programs
automatically. All the three classes extend the `CharacterSequence` abstract class,
which means most operations you find in strings are found in the other class, too.

Before we continue, here is a summary of strings.

 * Strings can include escape sequences. An escape sequence allows you to represent
  a special character which you would not be able to type with your keyboard.
  It is written with a backward slash followed by a letter.

Here is the list of all the escape sequences availablen in Zen.

| Escape Sequence      | Description     |
|----------------------|-----------------|
| \\n                  | Newline         |
| \\t                  | Tab             |
| \\b                  | Backspace       |
| \\r                  | Carriage Return |
| \\f                  | Form feed       |
| \\'                  | Apostrophe      |
| \\"                  | Quotation mark  |
| \\\\                 | Backslash       |

 * Strings are objects. You enclose a string literal in single quotes.
   A string can contain zero or more characters, even if a string contains a single

 * Strings are an important part of programming languages, therefore Zen treats
   strings specially. In fact, strings support many special syntax. For example,
   string objects are created from string literals. However, you can use
   the constructors of the String class for more flexbility. You will learn
   about these constructors in the next lecture.

 * You can combine, or concatenate, strings using the concatenation operator (`+`).
   You can combine strings with other values, in which case Zen automatically
   converts the value to a string for you. In the case of objects, the `toString()`
   function is first invoked to derive a string representation.

   Here is an example of the concatenation operator.

```
var firstPart = 'Hello, '
var secondPart = 'world!'
var message = firstPart + secondPart
```

 * Zen offers a wrapper class for each primitive type defined by the Zen Virtual
   Machine. These wrapper classes allow you to convert a string to a corresponding
   value. You can do this with the `parse()` function these classes expose.

   Here is an example of how you can convert a string to an integer.
```
// StringToInteger.zen

function main(...arguments)
    var text = '2019'
    var year = Integer.parse(text)
    printf('This is the year %d. After 11 years, it will be the year %d.\n', year + 11)
```

   This example converts the string which contains `'2019'` to its equivalent
   integer value, which is `2019`. However, if you specify an invalid text these
   functions throw `NumberFormatException`.

 * Unlike other programming languages, Zen does not support characters inherently.
   However, integer values can be treated as characters and additional support is
   provided through the `Character` class.


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

+++
title = "Comparing Strings"
weight = 4
+++

#### String Equality

You can compare two strings for equality using the equality operator (`==`).
The behavior of the equality operator is overridden in the `equals()` function,
which means you can use it to compare two strings for equality, too.

The declaration of the `equals` function is shown here.
```
function equals(other)
```

It returns `true` if both the strings contain the same characters in the same
order; `false` otherwise. You need to remember that this function is case sensistive.
For example, if you compare `'Batman'` and `'batman'` for equality, it would
return `false`.

Here is an example which demonstrates how you can compare two strings for
equality.

```
// StringEquality.zen

function main(...arguments)
    var string1 = 'Joker'
    var string2 = 'Harley Quinn'
    if string1.equals(string2)
        printf('"%s" is equal to "%s"!\n', string1, string2)
    else
        printf('"%s" is not equal to "%s"!\n', string1, string2)
```

You can compare two strings for equality without considering case. For this,
you need to invoke the overloaded version of the equals() function.

```
function equals(other, ignoreCase)
```

It returns `true` if both the strings contain the same characters in the same
order; `false` otherwise. You need to remember that this function is case
insensistive. For example, if you compare `'Camel'` and `'camel'` for equality,
it would return `true`.

Here is an example which demonstrates how you can compare two strings for
equality.

```
// StringEquality2.zen

function main(...arguments)
    var string1 = 'Poison Ivy'
    var string2 = 'poison ivy'
    if string1.equals(string2, true)
        printf('"%s" is equal to "%s"!\n', string1, string2)
    else
        printf('"%s" is not equal to "%s"!\n', string1, string2)
```

#### Comparing String Regions

You can compare a region inside your string with the region of another string.
You need to invoke the `regionMatches()` function for this.

Here is the declaration of the `regionMatches()` function.
```
function regionMatches(startIndex, other, otherStartIndex, count)
```

The `startIndex` specifies the index at which the region begins for the string
object against which the function is invoked.

`other` represents the other string to compare. The `otherIndex` indicates the
index at which the region begins for the other string.

The `count` parameter indicates the number of characters in both the regions.
You need to carefully specify this parameter.

You can force `regionMatches()` function to ignore case. For this invoke the
overloaded version of the `regionMatches()`.
```
function regionMatches(startIndex, other, otherStartIndex, count, ignoreCase)
```

The `ignoreCase` boolean parameter indicates whether the function should ignore
case when comparing, or not.

#### Prefixes and Suffixes

You can determine if a string starts with a substring using the `startsWith()`
function. It returns `true` if a string starts with the specified substring;
`false` otherwise.

Here is the declaration of the `startsWith()` function.

```
function startsWith(sequence)
```

Further, you can specify from which index `startsWith()` begins comparing.
An overloaded version of the `startsWith()` function accepts the starting index.
Here is the declaration of this function.
```
function startsWith(sequence, startIndex)
```

Here, the `startIndex` specifies the index applies to the string object against
which the function is invoked. It indicates the index from where the comparison is
started.

Similarly, you can determine if a string ends with a substring using the endsWith()
function. It returns `false` if a string ends with the specified substring; `false`
otherwise.

Here is the declaration of the `endsWith()` function.
```
function endsWith(sequence)
```

Here is an example which demonstrates these functions.
```
function main(...arguments)
    var superhero = 'Swamp Thing'
    var r1 = superhero.startsWith('Swam')
    var r2 = superhero.endsWith('ing')
    var r3 = superhero.startsWith('Thing', 5)
    printf('"%s" starts with "Swam": %z\n', superhero, r1)
    printf('"%s" ends with "ing": %z\n', superhero, r2)
    printf('"%s" starts with "Thing" after 5 characters: %z\n', superhero, r3)
```

This example produces the following output.
```
"Swamp Thing" starts with "Swam": true
"Swamp Thing" ends with "ing": true
"Swamp Thing" starts with "Thing" after 5 characters: true
```

#### Comparing Strings

Imagine you are sorting an array of strings. How can you determine whether one
string is greater than the other? So far you have learnt about functions that only
help you determine whether they are identical. In order to compare strings
for relativity, you need to use the `compare()` function.

The `compare()` function compares two strings lexicographically, which means
a A is lesser B, B is lesser than C and so on. For example, A is lesser than Z
and Y is greater than M. In this logic, lowercase letters are always greater
than uppercase letters.

The declaration of the `compare()` function is shown here.
```
function compare(other)
```

 * It returns a negative number if the current string object is lesser than the
   specified string.

 * It returns a positive number if the current string object is greater than the
  specified string.

 * It returns zero when both the strings are equal.

Here is an example, which determines if a string is greater than the other.
```
// YatchVsDragon.zen

function main(...arguments)
    var yatch = 'Yatch'
    var dragon = 'Dragon'
    if yatch.compare(dragon) > 0
        print('Yatch is greater than Dragon.')
    else if yatch.compare(dragon) < 0
        print('Yatch is lesser than Dragon.')
    else
        print('Yatch is equal to Dragon.')
```

This program generate the following output.
```
Yatch is greater than Dragon.
```

As mentioned previously, the `compare()` function is case sensitive. For case
insensistive comparison you need to invoke the overloaded version of the `compare()`
function which accepts a Boolean flag indicating whether the function has to
ignore case or not.

The declaration of the overloaded version of the `compare()` function is shown
below.
```
function compare(other, ignoreCase)
```

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