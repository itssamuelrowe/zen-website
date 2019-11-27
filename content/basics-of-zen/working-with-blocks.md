+++
title = "Working with Blocks"
+++

A block is a group of one or more statements. It is also known as a statement suite.
It is a type of statement, a compound statement to be specific. It begins when
the indentation of the first statement of the block is greater than the indentation
of its containing block. Subsequent statements with the same indentation as that
of the first statement are grouped together in the block.

You can write any number of statements, including block statements, in a block.

You cannot write an empty block in Zen. However, you can make use of the empty
statement to represent a dummy block like this.
```
function main()
    ; // Dummy block with an empty statement.
```

For example, this is a block with four statements.
```
    var i = null
    var j = null
    i = 10
    j = 20
```

Here is an example of block statements.

```
function main(...arguments)
    print('This is the outer block.')
    if true
        print('This is the inner block.')
        print('This statement belongs to the inner block as well.')
```