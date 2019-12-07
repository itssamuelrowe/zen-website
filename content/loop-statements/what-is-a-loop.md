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