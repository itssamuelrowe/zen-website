+++
title = "Declaring Functions"
weight = 3
+++

Here is the general form of a function declaration.

```
function name(parameters)
    statement1
    statement2
    ...
    statementN
```

The name of your function helps you call it.

Here is an example of a program which has redundant statements. Apparently,
Harry and Hermione are on an adventure, trying to break into a mysterious tower.
The following program prints the dialogue between them.

```
// MysteryTower.zen

function main(...arguments)
    print('Harry Potter: Can you open this door?')
    print('Hermione Granger: Alohomora!')

    print('Harry Potter: Can you open this door?')
    print('Hermione Granger: Alohomora!')

    print('Harry Potter: Can you open this door?')
    print('Hermione Granger: Alohomora!')

    print('The door opens!')
```

In this example, your program prints the same messages three times. But then
you end up writing the same statements over and over. Of course, you could
rewrite this program with a loop. Alternatively, you could use a function.

Here is another version of the previous example using a function.

```
// MysteryTower2.zen

function openDoor()
    print('Harry Potter: Can you open this door?')
    print('Hermione Granger: Alohomora!')

function main(...arguments)
    openDoor()
    openDoor()
    openDoor()

    print('The door opens!')
```

The order in which you declare your functions does not matter. So in this example,
you could write the `openDoor()` function after the `main()` function, it would
not matter. Your program will execute the same.

```
// MysteryTower3.zen

function main(...arguments)
    openDoor()
    openDoor()
    openDoor()

    print('The door opens!')

function openDoor()
    print('Harry Potter: Can you open this door?')
    print('Hermione Granger: Alohomora!')
```

When you invoke openDoor(), the two print statements in the `openDoor()` function
are executed sequentially. After which the control returns back to where the
function was called.