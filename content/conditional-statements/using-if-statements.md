+++
title = "Using If Statements"
+++

The if statement is one of the most important statements in any
programming language. The following sections describe the various
forms of the if statement in Zen.
Basically, the if statement allows your program to branch conditionally.
It is a compound statement.

Here is the general form of the *if statement*.

```java
if condition
    statement
else
    statement
```

Here, a statement may be either a simple statement or a compound
statement. The condition is any expression that evaluates to a Boolean
value.

The if statement is divided into two clauses: if clause and else clause.
The if clause begins with the if keyword. It accepts a condition,
enclosed in parenthesis. Similarly, the else clause begins with the else
keyword. It is optional. In other words, if you do not write the else clause
in your if statement, the compiler will not complain.

If the condition specified to the if clause evaluates to `true`, then the
statement under the if clause is executed. Otherwise, the statement
under the else clause is executed.

Here is a simple example of the if statement.

```
// VoteEligibility.zen

function main(...arguments)
    var age = 18
    if age >= 18
        println('You are eligible to vote!')
```

In this example, a variable named age is initialized to 18. Using the if
statement your program checks if the user is `18` or above. If the
condition evaluates to `true`, the user is allowed to vote. Which we
indicate by printing the message `'You are eligible to vote!'`

The output of this program is shown below.
```
You are eligible to vote!
```

As you can see, the else clause was not written in this example. By now
if you compiled and ran this program, you wold know that the compiler
did not generate any errors. This is because the else clause is optional.

Can you guess what would have happened if the Boolean expression
evaluated to false in this example? The entire if statement would have
been skipped because the else clause is absent.

Notice that we have indented the print statement. This forms a block statement,
or statement suite. Thanks to the statement suite, you can write more than one
statement under a clause.

Now, let's extend the program to print a message when the user is not
eligible to vote.

```
// VoteEligibility2.zen {

function main(...arguments)
    var age = 14
    if age >= 18
        print('You are eligible to vote!')
    else
        print('Sorry, kid. You cannot vote.')
```

The if clause is exactly the same as the previous example. The only
changes here are the else clause and the age variable initialized to 14.
Since the condition evaluates to `false`, the if clause is skipped and the
else clause is executed. The output of this program is shown below.

*Sorry, kid. You cannot vote.*

Notice that the statements inside the blocks are indented. Indentation
refers to the space and tab characters that you write before you write any
visible characters. Zen was designed around indentation to indicate blocks,
because indentation makes the structure of your code more obvious.
Unlike most programming language, Zen may ignore or may not ignore white space
depending on the context. It is always a good practice to indent your code with
4 space characters. Usually, text editors and IDEs take care of indentation for
you.

You can write a block statement inside another block statement, provided that
the inner block statement is part of a compound statement. You can think of the
outer block statement as level 1 and the inner block statement as level 2.
We recommend you to increment your indentation by four space characters for each
level.

Here is a modified version of the previous example which includes
comments that indicate the block level.

```
// VoteEligibility3.zen

// level 1, 0 spaces
function main(...arguments)
    var age = 14
    // Level 2, 4 spaces
    if age >= 18
        // Level 3, 8 spaces
        print('You are eligible to vote!')
    else
        // Level 3, 8 spaces
        print('Sorry, kid. You cannot vote.')
```