+++
title = "Understanding Unicode"
+++

> This section describes Unicode and how Zen deals with it. It is a difficult
> concept to grasp. You can safely skip this section for now. You can come back
> when you are comfortable with Zen.

To work with characters in a computer, you need the following:  
 * Character Repertoire  
 * Character Set  
 * Character Encoding  

### Understanding Characters Repertoire

A *character repertoire* is a collection of characters your computer can
work with. For example, a character repertoire may include letters, digits,
and symbols from Kannada, English, Tamil, Hindi, and Telugu.

### Understanding Character Set

Computers understand only numbers. So they store letters and other characters
by assigning a number for each one. These numbers are known as *codepoints*.

When a computer stores a character, it doesn't really know the difference
between `A` and `B`. However, it knows the difference between `65` and `66`.
Internally, computers use the number `65` as the *codepoint* to represent `A`
and `66` for `B`.

In fact, all letters, digits, and symbols have codepoints. The codepoints given
to characters are collectively known as *character set* or *charset*.

When you store `'A'` in a `char` variable, you actually store the value `65` in
it. Which means, the `char` type is really an integer type.

Here's an example which prints the codepoints of A, B, C, D, E, and F.
```
// CodePointsExample.zen

function main(...arguments)
    print('A'.getCodepoint(0))
    print('B'.getCodepoint(0))
    print('C'.getCodepoint(0))
    print('D'.getCodepoint(0))
    print('E'.getCodepoint(0))
    print('F'.getCodepoint(0))
```

### Understanding Character Encoding

Finally, your computer stores your codepoints in a sequence of 1s and 0s.
This binary representation is called as *character encoding*.

## History of Unicode

There were hundreds of different character encodings before Unicode was
invented. The other character encodings were limited. They did not cover
all the languages of the world.

The *Unicode Standard* provides a codepoint for every character, no matter
what platform, device, application or language. It is used in all modern
software.

Unicode is a very popular character encoding standard. Many well known companies
such as Microsoft, Google and Oracle use Unicode. In fact, you are using Unicode
already.

Unicode was actually designed to *encode* characters in 2 bytes. This is why
`char` defined by the Zen Virtual Machine uses 2 bytes.

Only 65,536 characters can be encoded with 16 bits. You cannot represent all
the characters in the world with just 16 bits. So Unicode was extended to use
21 bits. Now over one million characters can be encoded (1,114,111 to be exact).
You can use the characters outside U+FFFF with *supplementary characters*.

## Using Unicode in Zen

A supplementary character is any character within the range U+10000 and U+10FFFF.
You need to use a pair of character values to represent them. The pair of codepoints
which represent a supplementary character are known as surrogates.

The first codepoint is known as the high surrogate. It is in the range of U+D800
to U+DBFF.

The second codepoint is known as the low surrogate. It is in the range of U+DC00
to U+DFFF.

For example, the **DESERET CAPITAL LETTER LONG I** (U+10400), is represented with
U+D801 and U+DC00 surrogate pair.
```
var letter = '\uD801\uDC00'
```