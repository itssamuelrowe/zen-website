+++
title = "Conditional Statements: How Your Programs Make Choices"
weight = 6
+++

In this module, you will learn about the if statement.

So far in this documentation, all the programs have run in a linear fashion. In
other words, your programs simply ran from start to finish with each
statement being executed one after the other. However, in most real-life
situations, your programs will need to make decisions whether to skip a
few statements, repeat things multiple times, or even jump from one
part of your code to another part. Such actions are performed using
control statements. You will learn about these statements in this module
and the next module.

A programming language provides control statements that allow your
programs to alter the flow of execution. Zen's control statements are
divided into the following categories: selection, iteration, and jump.

##### Selection Statement

Selection statements allow your program to choose different paths of
execution based on a Boolean expression. They are also known as
conditional statements. They are the focus of this chapter.

##### Iteration Statement

Iteration statements enable your program to repeat one or more
statements in your code. They are also known as loop statements. You
will learn more about these statements in the next chapter.

##### Jump Statements

By far, jump statements are the simplest control statements. As the
name suggests, they allow your program to jump from one location to
another location. Given their simplicity, they don't get their own
module. However, we explain them in detail whenever their usage is
required or when a concept is closely associated with them.

In this module, we will learn about the if statement which allows you to
execute a statement or a block of statements based on a Boolean condition.
The if statement relies heavily on the use of Boolean expressions. In
general, these expressions produce true or false. You have already learnt
the various logical and comparison operators, which produce Boolean values. You
can always go back to the previous module to jog your memory.

## Using If Statements

The if statement is one of the most important statements in any
programming language. The following sections describe the various
forms of the if statement in Zen. Basically, the if statement allows your
program to branch conditionally. It is a compound statement.

Here is the general form of the *if statement*.

```
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
        print('You are eligible to vote!')
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
```
Sorry, kid. You cannot vote.
```

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

## Nested If Statements

You can write any statement under the if and else clauses.
In fact, you could write another if statement under them.
This is known as nesting. So, if you write an if statement inside
another if statement, we call the arrangment as nested if statements.
The if statement written inside another if statement is called the
inner if statement. Similarly, the if statement which contains another if statement is
called the outer if statement.

Nested if statements are very common in programming. When you nest
if statements, you must always remember that the else clause is
associated with the nearest if clause. You can nest any number of if statements
to any depth. We recommend you to keep it as simple as possible. Also, be sure
to use indentation to indicate the structure of the nested statements.

Here is the general form of a nested if statement.

```
if condition1
    if condition2
        statement1
    else
        statement2
else
   if condition3
        statement3
    else
        statement4
```

Remember, you construct a nested if statement with regular if statements.
So, you do not have to use if statements under both the clauses
if you do not have to. Again, all the else clauses are optional.

## Using If-Else-If Ladders

A common programming construct based on a sequence if statements is the if-else-if
ladder.

Here is the general form of an if-else-if ladder.
```
if condition1
    statement1
else if condition2
    statement2
else if condition3
    statement3
else
    statement4
```

The if statements are executed from the top to down. As soon
as one of the conditions associated with an if clause is `true`,
then the statement associated with that if clause is executed,
and the rest of the ladder is skipped. If none of the conditions are
`true`, then the final else clause will be executed. In other words,
the final else clause acts as a default condition.

Here is an example program that demonstrates the if-else-if ladder.
```
// SeasonExample.zen
function main(...arguments)
    var month = 2
    var season

    if month == 1
        season = 'Winter'
    else if month == 2 or month == 3
        season = 'Spring'
    else if month == 4 or month == 5
        season = 'Summer'
    else if month == 6 or month == 7 or month == 8 or month == 9
        season = 'Rainy'
    else if month == 10 or month == 11 or month == 12
        season = 'Winter'
    else
        season = 'Invalid'
    print('The season experienced in February is ' + season)
```

We suggest you to play around with this program before moving on. As you will find,
no matter what value you assign the `month` variable, only one assignment statement
within the ladder will be executed.