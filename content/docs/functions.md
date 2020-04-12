+++
title = "Functions"
chapter = true
weight = 10
+++

### Chapter 10
# Functions

In Zen all programs are built with classes, which means there is at least
one class. Further, every program must have at least one function, the `main()`
function. That is it. Beyond that, you do not need to create other functions.
But, without functions, often your code will contain a lot of duplicate instructions.

In this chapter, you will learn how to create your own functions, invoking functions,
accepting parameters, and finally returning values from functions.


+++
title = "What is a Function?"
weight = 1
+++

A function is a block of statements. You can give it a name. When a function is
declared inside a class, it defines an object's behavior, basically whatever an
object is capable of performing.

You can call or invoke a function with its name. When you invoke a function, the
execution of your program branches to the body of that function. When the function
is finished, execution resumes from where the program branched, and the program
continues on to the next statement.

You have already used functions. For example, `print` and `prompt` are
functions declared in the `ZenHelper` class.


+++
title = "Difference Between Functions and Methods"
weight = 2
+++

Function is a sequence of instructions that achieve some result. It may take
arguments and return a result. If a function does not return a result it is
usually called a procedure.

Here are a few examples of functions.
```
function drawLine(x1, y1, x2, y2)
  /* Draws a line using Bresenham's algorithm from (x1, y1) to (x2, y2).
   * It does not return anything.
   */

function add(a, b)
    /* Adds a to b and returns the result as a number. */
    return a + b
```

When you need to draw a polygon of 3 lines as a part of a vector image it is
more convenient to invoke the `drawLine()` function thrice rather than duplicating
the algorithm thrice.

Functions are similar to functions, they belong to classes or objects and usually
express verbs of an object. For example, an object of class `Window` usually
would have methods `resize()` and `setVisible()` which do corresponding operations
to the object they belong.

In Zen, methods are also referred to as functions.


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


+++
title = "Naming Conventions for Functions"
weight = 4
+++

 * Begin function names with a lowercase letter. For example, `print`, `getName`,
  `setTitle` and `buffer`.
 * If the function name consists of more than one word, capitalize every word,
  except the first word. For example, `toString`, `initializeCamera`, `launchRocket`
  and `parseInteger`.
 * Try to begin your function names with verbs. The name of a function should indicate
   an action.

   +++
title = "Advantages of Functions"
weight = 5
+++

The primary advantages of functions are as follows.

 * Functions improve the quality of your code. They make it more readable because
   you break your code into logical chunks.
 * You avoid duplicate code. Imagine you are writing an application that simulates
   an airplane, which requires primitive matrix operations such as addition,
   subtraction and multiplication. Without functions you would have to write these
   operations in several places. So whenever you see yourself writing the same
   code, it is a good idea to write a function.
 * You can implement polymorphism through functions. This is one of the most
   important features of functions.


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


+++
title = "Understanding Functions That Return Values"
weight = 8
+++

Functions that perform operations without returning any value are useful, but this
is not the case always. In this section you will learn how to return values
from functions.

Imagine that you write a function that accepts your date of birth and calculates
your age. Probably the function can print it on the console. But this is not what
you always want. For example, you would want the calculated age to determine if
you are eligible to vote, or not. In such cases, your function needs to return
a value or store the result in some field. Usually, returning a value is much
easier.

You can use the return statement to return a value to the caller.

Here is the general form of the return statement.

```
return expression
```

The expression must evaluate to a value which will be returned by the function.
You cannot return more than one result at a time. Further, the function terminates
as soon the return statement is executed. Improper use of return statements create
unreachable regions in your function causing bugs. We recommend you to
design your functions to always use a minimum number of return statements. This
way you can easily determine the exit points of your function.

Here is an example of a function that accepts a number and determines if it
is even, or not.
```
// OddOrEven.zen

function isEven(number)
    if number % 2 == 0
        return true
    else
        return false

function main(...arguments)
    var n = 19
    var result = isEven(n) ? 'even' : 'odd'
    printf('%d is %d.\n', n, result)
```

Here, the `isEven()` function accepts an integer value. It then divides it by 2 for
remainder. If the remainder is `0`, it returns `true` indicating an even number.
Otherwise, it returns `false` indicating an odd number.

Here is another version of the `isEven` function.
```
// OddOrEven2.zen

function isEven(number)
    return number % 2 == 0

function main(...arguments)
    var n = 19
    var result = isEven(n) ? 'even' : 'odd'
    printf('%d is %s.\n', n, result)
```

Here is an example of the `isEven()` function, which would generate
an error.

```
function isEven(number)
    if number % 2 == 0
        return true
```

In this example, the function does not return a value in all cases. If the specified
number was odd, the function would not return any value, but the compiler expects
you to return a value in all cases. This is why it would generate errors if you
tried to feed code like this.

You should be careful when you return values from loops and conditional statements.
You need to ensure that a value is returned in all case.

Here is an example of a program that computes the factorial of a number.
```
// Factorial.zen

function factorial(number)
    var result = 1
    for i in range(2, number + 1)
        result *= i
    return result

function main(...arguments)
    var n = promptInteger('Enter an integer: ')
    var result = factorial(n)
    printf("%d! = %d\n", n, result)
```

+++
title = "Function Overloading"
weight = 9
+++

Unlike variables, multiple functions in the same scope can have the same
name. This technique is known as function overloading. It is a feature of
polymorphism. Function overloading is a very useful feature.

Zen differentiates functions using pseudo function signatures. A pseudo function
signature is a part of function declaration. It is the combination of the function
name and the parameter count. The names of the parameters are not included in the
pseudo function signature.

In order to overload a function, the pseudo function signatures should be different.
Which means even if your function names are the same, you need to have different
parameter counts. When the functions have the same name but different parameter
counts, the functions are said to be overloaded.

When you invoke an overloaded function, Zen uses the following conditions to
determine which version of the overloaded function you are calling.

 * The type of each argument you are passing.
 * The number of arguments you are passing.

This is the reason why overloaded functions must have different parameter counts.
Otherwise, Zen will not be able to determine which version of the overloaded
function to call.

Here is a simple example that computes area of squares and rectangles using
function overloading.

```
// AreaComputer.zen

/**
 * Compute the area of a square.
 */
function computeArea(side)
    return side * side

/**
 * Compute the area of a rectangle.
 */
function computeArea(length, breadth)
    return length * breadth

function main(...arguments)
    var side = 10
    var areaOfSquare = computeArea(side)
    printf('The area of square with side %d is %d.\n', side, areaOfSquare)

    var length = 10
    var breadth = 5
    var areaOfRectangle = computeArea(length, breadth)
    printf('The area of rectangle with length %d and breadth %d is %d.\n', length, breadth, areaOfRectangle)
```

The output of this program is shown here.

```
The area of square with side 10 is 100.
The area of rectangle with length 10 and breadth 5 is 50.
```

As you can see, `computeArea()` is overloaded two times. The first version accepts
a single parameter named `side`. The second version accepts two parameters
named `length` and `breadth`, respectively. When you invoke a function, Zen
looks for a match between the arguments passed and the function parameters
declared.

When `computeArea` is called the first time with a single integer argument,
the function which computes the area of a square is invoked. Similarly, when
`computeArea` is called the second time with two integer arguments, the function
which computes the area of a rectangle is invoked. The results are respectively
stored in variables before printing.

Overloading is useful because it allows you to declare and invoke related functions
with the same name.

For example, you could implement an operation such as `computeVelocity`, which
obviously evalutes the velocity of an object, say a bike. The name `computeVelocity`
represents the general action that is being performed. You could implement
two different versions of calculations using different formulas. Assume
one version accepts distance and time, whereas another version accepts force,
mass and time. With function overloading you could easily implement this. Otherwise,
you would have to come up with different names for each function.

When you overload a function, each version can implement anything. You do not
have to relate the functions to one another. We recommend you to always overload
functions that perform the same operation but in different ways.


+++
title = "Working with Getters and Setters"
weight = 10
+++

Object-oriented programming helps you hide the details of a class. You can
expose certain parts of your class to others.

You should generally avoid creating public fields. You can make all your
fields private. You can give access to the values in these fields with
*accessors*. Accessors are functions which access fields on the behalf of the
world outside your class.

There are two types of accessors.

 * Get Accessor
 * Set Accessor

A get accessor is also known as **getter**. It is a function which gets the value
of a field.

A set accessor is also known as **setter**. It is a function that sets the value
of a field.

Accessors are usually named `getField` and `setField`. For example, for a
field named `age`, the accessors are named `getAge` and `setAge`.

Here is an example.

```
class Rocket

    var mass
    var velocity
    var acceleration

    function setMass(m)
        mass = m

    function getMass()
        return mass

    function setVelocity(v)
        velocity = v

    function getVelocity()
        return velocity

    function setAcceleration(a)
        acceleration = a

    function getAcceleration()
        return acceleration
```

In the above example, `mass`, `velocity, and `acceleration` are private fields.
You cannot access them directly outside the class. You need to use their accessors
instead.

Accessors have the following advantages over public fields.

 * You can create read-only properties. You can provide only the getter but not
   a setter. Which means other classes can only read the property, but cannot
   write.
 * You can avoid storing the value in a field. A getter can calculate the value.

Here is an example of a rectangle, where an accessor evaluates the value.

```
class Rectangle

    var width
    var height

    function setWidth(w)
        width = w

    function getWidth()
        return width

    function setHeight(h)
        height = h

    function getHeight()
        return height

    function getArea()
        return width * height
```

A setter can check if an invalid value is passed. It can *throw an exception*
or provide a default value. You will learn more about exceptions later in
this course.

For example, imagine you have a class `Adult`. It has an integer property
named `age`. Its value can be 18 or greater. You can write a setter which
ignores invalid values like this.

```
class Adult

    ...

    var age

    function setAge(a)
        if a >= 18
            age = a

    function getAge()
        return age

    ...
```

In fact, using accessors is actually a design pattern known as the Accessor Pattern.
It is designed to provide a consistent way to read and write values of class
fields while hiding the fields from the outside world. This pattern is very
common because fields are usually private.

+++
title = "Using the Property Annotation"
weight = 11
+++

```
class Rocket

    @Property
    var mass

    @Property
    var velocity

    @Property
    var acceleration
```

```
class Rectangle

    @Property
    var width

    @Property
    var height

    function getArea()
        return width * height
```

+++
title = "Understanding Pass-By-Reference"
weight = 12
+++

When you pass a reference value, such as objects and arrays, as an argument to
a function, the function receives a copy of the reference. In other words, the object
itself is not copied when you pass it as an argument, only its reference is copied.

Similarly, when you pass a variable that contains a reference to an object as an
argument to a function, the function receives a copy of the reference, not the the
variable itself.

This technique is called pass-by-reference. It is applied when you pass reference
values, such as objects and arrays.

Therefore, if a function changes the reference it received through the parameter,
it is not reflected in the original variable that was passed to the function.

However, if the object is modified through the reference, then the change is
reflected in the object. Because both the argument and the parameter refer to
the same object, and not separate copies of the object.

Consider the following example.

```
// PassByReferenceDemo.zen

class Square

    var side

function main(...arguments)
    var square = new Square()
    square.side = 5

    printf('[before] square in main contains side = %d\n", square.side)
    changeValue(square)
    printf("[after] square in main contains side %d\n", square.side)

function changeValue(square)
    square.side = 7
    printf('square in changeValue contains side = %d\n", square.side)
```

The output of this example is shown here.

```
[before] square in main contains side = 5
square in changeValue contains side = 7
[after] square in main contains side = 7
```

In this example, a variable named `square` is assigned an instance of the `Square`
class. The value of the `side` field contained in the `square` object is assigned
`5`. It is then printed on the console. After which, Tthe `changeValue()` function
is invoked with `square` as its argument. Remember, the reference to the `square`
object is copied, not the object itself.

`changeValue()` receives the reference as the parameter named `square`.
It modifies the value of `side` contained in the `Square` object to `7`. After
which it prints out the value stored in it.

When the `changeValue()` function terminates, the control is again transferred to
`main()`, where the current value of `side` is printed. Since the
`changeValue()` was invoked with a copy of the reference, the `square` object
has been changed.