+++
title = "Working with Strings"
+++

In this section, you will learn the basics of strings.

A string is a sequence of characters. String literals are enclosed in single
quotes (`'`).

Here's an example of a string.
```
'Hello, world!'
```

The Zen Virtual Machine does not define string as a primitive type. Further,
the Zen programming language treats strings specially and classifies a string
as primitive reference type. It is implemented by the `zen.core.String` class.

We take an entire chapter to explain strings. Here, we teach you the
basics. It will help you understand the upcoming examples.

### Initializing Strings

Here's an example of initializing a `String` variable.
```
var message
message = 'How are you?'
```

Here, we declared a variable named `message` and initialized it to `'How are you?'`.
Remember that string literals are enclosed in single quotes (`'`), not in double
quotes.

You can combine declaration and initialization like this.
```
var message = 'How are you?'
```

To initialize a local string variable to an empty string, use a statement like
this.
```
var string = ''
```

### Joining Strings

You can join two strings by using the *concatenation operator* (`+`).
*Concatenation* means joining two strings.

Here's an example where two strings are joined.
```
// JoiningStrings.zen

function main(...arguments)
    var hello = 'Hello, '
    var world = 'world!'
    var message = hello + world
    print(message)
```

When you join strings, no extra characters are added by Zen. This includes any
blank spaces between strings. If you want to combine two strings with a space in
between them, you have to do it. In the previous example, the first string ends
with a space.

Here's another example where two strings are joined with and without space in
between them.
```
// JoiningStringsWithSpace.zen

function main(...arguments)
    var hello = 'Hello,'
    var world = 'world!'
    var message1 = hello + ' ' + world
    var message2 = hello + world

    print(message1)
    print(message2)
```

You can join a string with any object, such as `Integer32` and `Decimal32`.
Zen converts the primitive value to a string and then joins it.

Here's an example where a string is joined with a Boolean value.
```
// JoiningStringsWithPrimitiveValues.zen

function main(...arguments)
    var question = 'Are you Batman?'
    var answer = true
    var message = question + ' ' + answer
    print(message)
```

Here we declared a variable named `question` which holds a simple
question. We declared a variable named `answer` which holds `true`.
We joined `question` and `answer` using the concatenation operator (`+`).
The resulting string was stored in `message`. We have added a blank space to
seperate the question and answer. Finally, we printed the string stored in
`message`.

### Converting Strings to Numeric Values

You can convert a string into a numeric value. For example, you can convert the
string `'27'` written with digits into a numeric value. But you cannot convert
the string `'twenty seven'` written in words into an integer, at least not using
the standard API.

You can use one of the following functions to convert a string to a primitive
value.

| Wrapper Class | Function     |
|---------------|--------------|
| Boolean       | parse        |
| Character     | --           |
| Integer8      | parse        |
| Integer16     | parse        |
| Integer32     | parse        |
| Integer64     | parse        |
| Decimal32     | parse        |
| Decimal64     | parse        |

Here's an example of converting strings to primitive values.
```
var value1 = Boolean.parse('true')
var value2 = Integer8.parse('27')
var value3 = Integer16.parse('519')
var value4 = Integer32.parse('2000')
var value5 = Integer64.parse('1999')
var value6 = Decimal32.parse('5.19')
var value7 = Decimal64.parse('9.21')
```