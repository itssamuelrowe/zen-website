+++
title = "The Zen Programming Language"
+++

# The Zen Programming Language

Zen is a general purpose programming language designed to build simple, reliable
and efficient programs.

## Example 1

```
function factorial(n)
    return n <= 1? 1 : n * factorial(n - 1)

function main(...arguments)
    var n = promptInteger('Enter an integer: ')
    var result = factorial(n)
    printf('%d! = %d', n, result)
```

## Example 2

```
function main(...arguments)
    var name = prompt('What\'s your name? ')
    if name.isBlank()
        print('The specified name is blank.')
    else if name == 'Samuel Rowe'
        print('Hey! That\'s my name, too!')
    else
        print('Hi, %s!', name)
```