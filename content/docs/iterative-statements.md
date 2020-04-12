+++
title = "Loop Statements"
chapter = true
weight = 7
+++

### Chapter 7
# Loop Statements: How Your Programs Repeat Things

One thing computers enjoy doing more than anything else is repeating themselves.
Imagine your teacher asked you to write "I love Game of Thrones!" a hundred
times. Although you may love the show, you would find this a cruel punishment.
Computers on the other hand, do not mind this. In fact, a computer could easily
write this a thousand times in milliseconds.

You need to understand conditional statements to properly understand the concepts
of loops, the if statement in particular.

In this chapter you will learn the three loop statements in Zen.

+++
title = "What is a Loop?"
+++

Repeating things over and over is referred to as looping. The iteration statements
in Zen help you create loops in your programs. These statements allow a segment
of your code to repeat a given number of times.

As an example of a loop, consider yourself watching a series like Breaking Bad.
 * Find the next episode to watch.
 * Watch the episode.
 * Repeat.

This simple example contains a loop. The loop is based on the "Repeat" instruction,
which tells you that the entire sequence of steps repeats itself.

Unfortunately, the steps in the previous example do not contain any
stopping condition. Which means you will never stop watching the series!
Such a loop is known as an endless loop.

Most looping statements in computer programming languages have some sort of condition —
like an if statement — that tells the program when to stop repeating.

A simple modification to the previous example can fix the endless loop situation:
 * Repeat while you're not bored and you have more episodes to watch.

Now, the example has a stopping condition for the loop.

In conclusion, loops have four parts:
 * Initialization
 * Condition
 * Action
 * Updation

During initialization, you instruct your program to setup things for the loop.
In our previous example, starting the Netflix app can be considered as
initialization.

The condition determines whether the loop has to execute or terminate.
"Repeat while not bored and you have more episodes to watch" was the condition
in our earlier example.

The action consists of instructions that are repeated over and over. Finally,
the updation part prepares the program for the next iteration. Usually, the
updation brings the program closer to termination.

In the previous example, "Find the next episode to watch." was the updation part
and "Watch the episode." was the action.

The action and the updation parts are sometimes considered together.

All the loop statements in Java include these four parts. They differ in the way
they are expressed.

After the loop has completed, the program continues as usual. But during looping
the same part of the program runs over and over.

+++
title = "Working with the While Statement"
+++

When it comes to loops, Zen gives you two choices. You can go with the
while loop, which provides enough flexbility to make most programmers
happy, or you can choose the simpler for loop for your programs.

The for statement is clearer and lays out all its plans in one place.
Whereas, the while statement gives you more flexbility. The important thing to
remember is that you can convert a for loop into a while loop, and vice versa.

The while loop is the simplest loop in Zen. It simply executes a loop continuously
as long as a condition is true. While loops are useful in many situations, so
you use them a lot.

Generally in a while loop we say "while this condition is true, keep repeating
this action."

Here is a simple example that shows a while loop in real life. You eat from your
lunch box while there is food in it. Easy enough.

The general form of the while statement is like this.
```
while condition
    body
```

The while statement begins by evaluating the conditional expression. If the
expression is `true`, the body is executed. Then, the conditional expression
is evaluated again, and the whole process repeats. If the expression is `false`,
the body is not executed, and the while loop ends.

Here's a simple program that uses a while loop to print the even numbers
from 2 through 10 on the console.

```
// EvenNumbers.zen

function main(...arguments)
    var number = 2
    while number <= 10
        print(number)
        number += 2
```

If you run this program, the following output is displayed on your console.
```
2
4
6
8
10
```

The conditional expression you used in the while loop shown in the previous
example is `number <= 10` (number is less than or equal to 10).
That means the loop repeats as long as the value of number is less
than or equal to `10`.

The body of the loop consists of two statements. The first statement prints the
value of `number`. Then, the second statement adds `2` to `number`.

Notice that we have idented the statements below the while clause. This forms a
statement suite. You can write more than one statement under the while clause.

Here's a flowchart for this program. It can help you visualize the basic decision
making process of a loop.

> TODO: Insert an image here.

+++
title = "Using the Break Statement"
+++

All loops end when a test condition fails. There might be situations where
something occurs during the execution of a loop, and you want to exit the loop
early. In such cases, you can use the break statement.

The general form of a break statement is like this.

```
break label
```

Here, the label is optional. You will learn more about labels in just a moment.

Break is a simple statement therefore it ends with a newline.

The `break` keyword, when used inside a loop, does the same thing, that is, it
immediately halts execution of the loop.

In the case of nested loops, the loop nearest to the break statement is terminated.
You can override such behaviour using labels.

A break statement accepts an optional label that indicates which loop to terminate.
This is especially useful in nested loop. Without a label, break jumps outside
loop nearest to the break statement. Using break with a label enables you to
terminate a particular loop.

The general form of a label is shown here.

```
#label // loop statement
```

To use a labeled loop, add the label before the initial part of the loop with a
octothorpe (the hash sign) before the label. Then, when you can use the break
statement add the name of the label after the `break` keyword.

Labels can be used with any type of loop available in Zen, that is, for and while
loops.

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