+++
title = "Working with Comments"
+++

Comments are texts that are ignored by the compiler. They help you write
information or explanation about your code. You can use comments to hide a part
of your code.

We recommend you to use plenty of comments in your source code.

## Types of Comments

There are 3 types of comments in Zen.

 * Single Line Comment
 * Multi-Line Comment
 * Documentation Comment

### Single Line Comments

A single line comment begins with `//` and ends at the end of the line.
Everything you type after `//` is ignored by the compiler.

Here's an example.
```
perimeter = 2 * (width + breadth) // Calculate the perimeter of the rectangle.
```

If you want, you can move the comment on a separate line.
```
// Calculate the perimeter of the rectangle.
perimeter = 2 * (width + breadth)
```

### Multi-Line Comments

A multi-line comment begins with `/*` and ends with `*/`. It can span
over multiple lines.

Here is an example.
```
/*
Calculate the perimeter of the rectangle.
Then subtract 100 from it.
*/
perimeter = 2 * (width + breadth) - 100
```

Here is another example.
```
/* Calculate the perimeter of the rectangle.
Then subtract 100 from it. */
perimeter = 2 * (width + breadth) - 100
```

A multi-line comment can begin and end anywhere on a line.

Here is an example where the comment is placed in the expression.

```
perimeter = 2 * (width + breadth) /* Calculate the perimeter of the rectangle.*/ - 100 /* Then subtract 100 from it. */
```

Usually, multi-line comments appear on separate lines.

Multi-line comments cannot be nested. Here is an example which results in error
when you try to compile.

```
/*
 This is a comment.
 /* This is a nested comment. */
 */
```

### Documentation Comments

A documentation comment begins with `/**` and ends with `*/`. It can span
over multiple lines. It is similar to multi-line comments.
