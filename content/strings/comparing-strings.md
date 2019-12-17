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