+++
title = "Working with Constructors"
weight = 2
+++

A constructor is a special function which initializes your variables and performs
any other additional operations when you create an object. It is called whenever
you create an object.

Here is the general form of a constructor.

```
function new(parameters)
    statement1
    statement2
    ...
    statementN
```

Here, the `new` keyword indicates that the function is a constructor. Constructors
usually initialize values of fields.

You have already learnt about parameters in the previous chapter. A parameter
is a value that you can send to your constructor. Parameters allow a constructor
to be generalized. In other words, such constructors can operate on a
variety of data and work differently based on different arguments.

Here is an example of a constructor.

```
class Example

    function new()
        ;
```

The constructor is public by default. Which means, other classes can access it.
You can even make constructors private or secret. You can prevent a class
from being instantiated by other classes, by making the constructor private.
You will learn more about secret constructors in the next chapter.

Finally, the constructor shown here does not accept any parameters, making it
a default constructor.

As you can see, constructors are similar to functions, with the following differences.
    * A constructor canntat return any value.
    * Constructors are not considered as members of a class.

Unlike functions, a constructor cannot be called directly. You need to use the
`new` operator to invoke a constructor.

Every class has at least one constructor. In the examples shown so far, we have
not defined any constructor. But how were we able to create instances? That is
because Zen automatically provided your classes with constructors. In other words,
if you do not define a constructor in your class, Zen automatically creates an
empty constructor known as the default constructor. A default constructor accepts
no arguments. It does nothing. But it allows you to create objects of your class.
This is why you were able to create objects of the classes you created so far.

Here is an example where we declare an empty class.

```
class BlackHole
    var mass
```

Here is another way of writing the `BlackHole` class.

```
class BlackHole

    var mass

    function new()
        ;
```

Both the classes we declared are exactly the same.

In the first example, Zen provides you a default constructor. In the second
example, you declared a constructor that does not accept parameters and does
nothing. Such a constructor is known as *explicit default constructor*.

Here is an example of three classes. Each class demonstrates initialization using
different techniques.

```
// Pizza.zen

class Pizza

    public var name
    public var size
    public var price

    @Override
    function toString()
        return format('[Pizza] name: %s, size: %d, price: $%f', name, size, price)

// Burger.zen

class Burger
    var name
    var size
    var price

    function initialize(n, s, p)
        name = n
        size = s
        price = p

    @Override
    function toString()
        return format('[Burger] name: %s, size: %d, price: $%f', name, size, price)

// Roll.zen

class Roll
    var name
    var size
    var price

    function new(n, s, p)
        name = n
        size = s
        price = p

    @Override
    function toString()
        return format('[Roll] name: %s, size: %d, price: $%f', name, size, price)

// FastFoodJoint.zen

function main(...arguments)
    var pizza = new Pizza()
    pizza.name = 'Farm House Pizza'
    pizza.size = 'Large'
    pizza.price = 12.5
    print(pizza)

    var burger = new Burger()
    burger.initialize('Double Cheeseburger', 'Medium', 8.0)
    print(burger)

    var roll = new Roll('Chilli Chicken Roll', 'Large', 10.0)
    print(roll)
```

The output of this program is shown here.

```
[Pizza] name: Farm House Pizza, size: Large, price: $12.5
[Burger] name: Double Cheeseburger, size: Medium, price: $8.0
[Roll] name: Chilli Chicken Roll, size: Large, price: $10.0
```

This example demonstrates three ways you can initialize your objects. You
create three classes which include three fields `name`, `size`, and `price`.

The first technique is the simplest. You simply declare the fields in your class
and expose them, that is, make them public. You create an instance of the `Pizza`
class and initialize its fields by assigning each field in the `main()` function.
Although, this technique is simple you will end up repeating yourself very often.
Imagine you create twenty instances of the `Pizza` class in twenty different
places. You may forget to initialize a field. Imagine what happens when you
add or remove a field? You will have to find every place where you initialize
the object and edit your code.

The second technique is efficient. You declare the fields as private but expose
a function which initializes the object. After you create an instance of the
`Burger` class, to initialize its fields you invoke the `initialize` function
from the `main()` function. You pass the values of the fields as arguments to the
function, which in turn assigns to the fields. This is efficient, but you still
need to write two statements: one to create the object and another to initialize
the object. In case you add or remove a field, you simply need to change the
`initialize()` function.

For the final technique, we take inspiration from the previous technique and
combine creation and initialization of the object in the same statement. When
you create an instance of the `Roll` class, to initialize its fields you pass
the values of the fields to the constructor of `Roll` class. The constructor
assigns the fields the values it receives through its parameters.

Constructors are both efficient and simple. We recommend you to always initialize
your objects using constructors. After all, that is their primary purpose.

You need to remember that, when you create a parameterized constructor, Zen
does not provide a default constructor. In which case, you need to explicitly
define a default constructor if you need it.

Try to compile this example. The compiler will generate errors.
```
class Sitcom

    var title
    var ratings
    var length

    function new(t, r, l)
        title = t
        ratings = r
        length = l

// SitcomExample.zen
function main(...arguments)
    var sitcom = new Sitcom()
```

In this example, you try to invoke the default constructor of the `Sitcom` class.
The compiler generates errors obediently.

Zen does not provide a default constructor for the `Sitcom` class because we
declared a constructor which accepts parameters. We did not provide an explicit
default constructor either. Because you defined a parameterized constructor in
the `Sitcom` class, Zen will not provide a default constructor.
Which means, we are calling a constructor that does not exist. This is why
the compiler generates errors. This is basically the gist of the compiler error
you will see when you try to compile this example.