+++
title = "Working with Parameters"
weight = 6
+++

A *parameter* is a value that you can send to a function. Parameters allow a
function to be generalized. In other words, such functions can operate on a
variety of data and work differently based on different arguments.

It is important to understand the difference between parameters and arguments.
A parameter is a variable defined by a function that receives a value when the
function is invoked. Whereas, an argument is the value that is passed to a function
when it is invoked.

## Declaring Parameters

You must list your parameters when you declare your function. The parameters are
listed in the parentheses after your functions name. Every parameter should
have a name.

You can pass values to your function when you call it. List your values in the
parentheses after your functions name.

Consider the following example.

```
function square()
    print(7 * 7)
```

The `square()` function prints the square of `7`. Although this function works
perfectly, it is very limited. However, if you modify the function to accept a
parameter, you can make it more useful and flexible.

```
function square(number)
    var result = number * number
    print(result)
```

You can use a parameter like any other local variable. Its value is initialized
with the value you pass.

For example, you can call `square` like this.
```
square(5)
```

If you need more than one parameter, you must separate them with commas.

Here is an example.
```
void createUser(name, age)
    ...
```

You can call `createUser` like this:
```
createUser('Sherlock Holmes', 24)
```

If your function needs no parameters, leave the parentheses empty.

Here is an example.
```
function collect()
    ...
```

You can call `collect` like this:
```
collect()
```

## Understanding Scope of Parameters

The parameters of your function exists only within the function. You cannot access
it outside your function.

```
// Calculator.zen

class Calculator

    static function main(...arguments)
        var x = 10
        var y = 20
        var result = add(x, y)

        printf('%d + %d = %d\n', x, y, result)

    static function add(x, y)
        return x + y
}
```

In 'main`, we declared three variables named `x`, `y` and `result`. We call
`add()` to compute the sum of `x` and `y`. The `add()` function accepts two
parameters named `x` and `y`.

The local variables in `main` and the parameters in `add` have the same names.
Compile this program. The compiler does not complain. But why? The compiler
generate errors if we declare variables with the same name, right? As we told
earlier, parameters exist only within the function they are declared. Local
variables exist only within the block they are declared. This is why the compiler
does not generate any error. In other words, the local variables `x` and `y`
declared in the `main()` function and the parameters `x` and `y` declared in the
`add()` function exist in different scopes.