+++
title = "The Zen Programming Language"
+++

# The Zen Programming Language

Zen is a general purpose programming language designed to build simple, reliable and efficient programs.

## Example 1

```
function factorial(n)
    return n <= 1 ? 1 : n * factorial(n - 1)

function main(...arguments)
    printf('Enter an integer: ')
    var n = scanInteger()
    var result = factorial(n)
    print('%d! = %d', n, result)
```

The above example generates the following output:

```
Enter an integer: 5
5! = 120
```

## Example 2
```
function main(...arguments)
    printf('What is your name? ')
    var name = scanLine()
    if name.isBlank()
        print('The specified name is blank.')
    else if name == 'Samuel Rowe'
        print('Hey! That is my name, too!')
    else
        print('Hi, %s!', name)
```

The above example generates the following output:

```
What is your name? Samuel Rowe
Hey! That is my name, too!
```

## Example 3

```
function main(...arguments)
    var names = [
        'Samuel Rowe',
        'Joel E. Rego',
        'Bill Gates',
        'Linus Trovalds',
        'Abraham Lincoln',
        'Isaac Newton',
        'Albert Einstein',
        'Richard Feynman',
        'Christopher Nolan',
        'Benedict Cumberbatch'
    ]
    var key = 'Marshall Mathers'
    var result = null
    for var i in range(0, names.size)
        if key == names[i]
            result = i
            break

    if result != null
        print('Found the key "%s" at index %d.', key, result)
    else
        print('Could not find the key "%s" in the list.', key)
```

The above example generates the following output:

```
Could not find the key "Marshall Mathers" in the list.
```