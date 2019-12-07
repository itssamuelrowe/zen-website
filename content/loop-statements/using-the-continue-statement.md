+++
title = "Using the Continue Statement"
+++

Sometimes it is useful to force an early iteration of a loop. In other words,
you might want to continue running the loop but stop processing the remainder
of the code in its body for this particular iteration.

In a while statement, a continue statement causes control to be transferred
directly to the conditional expression that controls the loop. In a for statement,
control first goes to the updation section of the for statement and then to the
conditional expression. For both the loops, any intermediate code is skipped.

The general form of a continue statement is like this.

```
continue label
```

Here, the label is optional. You will learn more about labels in just a moment.

Continue is a simple statement therefore it ends with a newline.

Here is an example program that uses continue to cause two numbers to be printed
on each line:

```
// TwoNumbersPerLine.zen
    
function main(...arguments)
    for var i in range(0, 10)
        write(i + ' ')
        if i % 2 == 0
            continue
        print()
```

This code uses the modulus operator to check if `i` is even. If it is, the loop
continues without printing a newline.

Here is the output from this program.
```
0 1
2 3
4 5
6 7
8 9
```

In the case of nested loops, the loop nearest to the continue statement is affected.
You can override such behaviour using labels.

As with the break statement, continue statements may specify a label to describe
which loop to continue. This is especially useful in nested loop. Without a label,
continue affects the loop nearest to the continue statement. Using continue with
a label enables you to effect a particular loop.

Here is an example program that uses continue statement to print a triangular
multiplication table for 0 through 9.

```
// TriangularMultiplicationTable.zen

function main(...arguments)
    #outer for var i in range(0, 10)
        for var j in range (0, 10)
            if j > i
                print()
                continue outer
            write(' ' + i * j)
    print()
}
```

The continue statement in this example terminates the loop counting `j` and
continues with the next iteration of the loop counting `i`.

Here is the output of this program.

```
0
0 1
0 2 4
0 3 6 9
0 4 8 12 16
0 5 10 15 20 25
0 6 12 18 24 30 36
0 7 14 21 28 35 42 49
0 8 16 24 32 40 48 56 64
0 9 18 27 36 45 54 63 72 81
```

You will rarely come across continue statements. One reason is that Zen provides
loop statements which fit most applications. However, for those special circumstances
in which early iteration is needed, the continue statement provides a structured
way to get your job done.