+++
title = "Constructors"
chapter = true
weight = 11
+++

### Chapter 11
# Constructors: How Your Objects are Initialized

When you create an object using the `new` operator, Zen does several things
for you.

Here is the gist of what happens when you create an object.

 * First, the memory to store the object is allocated.
 * The allocated memory buffer is initialized internally to create the
   object.
 * The object is associated with the class from which it was created.
 * The virtual function tables are generated.
 * Finally, a special function defined in the objects class is invoked.
   This function is called a constructor.

In this chapter, we will learn about constructors. We will see how to work with
constructors, including their declaration and invocation.


+++
title = "Understanding this Keyword"
weight = 1
+++

In the body of a function, constructor, or initializer block, sometimes you need
to refer to the object that contains the instance member in question.
In other words, sometimes an instance member may want to access the instance
it is contained in. In such cases, you can refer the instance using the `this`
keyword. It always represents the instance within which the instance member is
contained.

To refer to the instance in an instance function, use the `this` keyword where
you normally would refer to an object's reference through a variable. You can use
the `this` keyword as a reference anyway you please. In other words, the
`this` keyword refers to the current object, and you can use it anywhere a
reference to an object might appear.

Here is a some situations where you can use the `this` keyword:
 * with the member access operator
 * as an argument to a function or constructor
 * as the return value for a function, and so on.

In fact, whenever you refer to instance members in functions and constructors
with just their names, an implicit `this` reference is present. Which goes to say,
you can only use the `this` keyword in instance members. You cannot use the
`this` keyword in static contexts, such as static functions and static initializers.

A very common place where the `this` keyword is used is when you have a
local variable and a field with the same name. Yes, this is possible
because fields and local variables have different scopes.

Here is an example function which sets the score of a player.
```
class Player
    ...

    var score

    function setScore(score)
        score = score

    ...
```

In this example, we are trying to assign the parameter `score` to the field
`score`. When you refer `score`, the program looks up for the variable named
`score` from the nearest scope to farthest scope. In this example, the local
scope is the nearest scope, where the parameter `score` is declared. Which means,
the parameter `score` gets assigned to itself leaving the `score` field unchanged.

In order to override this behaviour, we refer to the field by explicitly adding
the `this` keyword to reference the current object.

Here is the modified version of the previous example.

```
class Player

    ...

    var score

    function setScore(score)
        this.score = score

    ...
```

You can skip the `this` reference if the parameter and the field do not have
the same name.

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


+++
title = "Overloading Constructors"
weight = 3
+++

A class can have multiple constructors, this achived through a technique known
as constructor overloading. It is a feature of polymorphism and is a very useful feature.
It is similar to function overloading.

Zen differentiates constructors using constructor signatures. A constructor
signature is a part of constructor declaration. It is the combination of the
new keyword and the parameter count. The names of the parameters are not included
in the signature.

In order to overload a constructor, the constructor signatures should be different.
Which means your constructors need to have different parameter count.

When you invoke an overloaded constructor, Zen uses the following conditions to
determine which version of the overloaded constructor you are calling.
    * The type of each argument you are passing.
    * The number of arguments you are passing.

This is the reason why overloaded constructors must have different parameter counts.
Otherwise, Zen will not be able to determine which version of the overloaded
constructor you are calling. It goes without saying, no two constructors in a
class can have the same number of arguments, because this is the only way
constructors can be differentiated in Zen.

Consider the following class.
```
// MovieExample.zen

class Movie

    var title
    var ratings
    var runtime

    function new(title)
        this.title = title
        this.ratings = 0.0
        this.runtime = 0.0

    function new(title, ratings)
        this.title = title
        this.ratings = ratings
        this.runtime = 0.0

    function new(title, ratings, runtime)
        this.title = title
        this.ratings = ratings
        this.runtime = runtime

    @Override
    function toString()
        return String.format('title: %s, ratings = %f, runtime = %f hours', title, ratings, runtime)

function main(...arguments)
    var forrestGump = new Movie('Forrest Gump')
    var joker = new Movie('Joker', 8.7)
    var interstellar = new Movie('Interstellar', 8.6, 2.49)

    print(forrestGump)
    print(joker)
    print(interstellar)
```

In this example, we defined three constructors.

The first constructor accepts a single parameter named `title`. It initializes
corresponding `title` field.

The second constructor accepts two paramters named `title` and `ratings`.
It initializes the fields with the corresponding values.

The third constructor accepts three paramters named `title`, `ratings`, and
`runtime`. It initializes the fields with the corresponding values.

You can create an instance of `Movie` like this.
```
var movie = new Movie('Forrest Gump', 8.8, 2.22)
```

## Calling Other Constructors

A constructor can call another constructor in the same class. Zen provides
special syntax for this purpose. You must use the `this` keyword with parenthesis.
This is useful when your overloaded constructors have some common behavior of an
existing constructor. You can call the general purpose constructor from your
other constructors.

Here is an example of `Movie` class where the constructors invoke another
general purpose constructor.

```
// MovieExample2.zen

class Movie {

    var title
    var ratings
    var runtime

    function new()
        this("Unknown", 0.0, 0.0)

    function new(title)
        this(title, 0.0, 0.0)

    function new(title, ratings)
        this(title, ratings, 0.0)

    function new(title, ratings, runtime)
        this.title = title
        this.ratings = ratings
        this.runtime = runtime

function main(...arguments)
    var forrestGump = new Movie('Forrest Gump')
    var joker = new Movie('Joker', 8.7)
    var interstellar = new Movie('Interstellar', 8.6, 2.49)

    print(forrestGump)
    print(joker)
    print(interstellar)
```

In the above example, we declared four constructors.

The first constructor is the *explicit default constructor*. It accepts
no parameters. It passes default values to the fourth constructor, which is
general purpose constructor.

The second constructor accepts the title of a movie. It passes the
title and default values to the third constructor.

The third constructor accepts the title and ratings of a movie.
It initializes the corresponding fields.

The fourth constructor, the general purpose constructor which is invoked by
all the other constructors, accepts three parameters `length`, `ratings`
and  `runtime`. It initializes the corresponding fields.

You need to follow these rules when calling another constructor.

#### RULE 1 - You can call another constructor only in the very first statement of your constructor.

For example, this will not compile.

```
function new(title)
    int i = 0
    this(title, 0.0, 0.0)
```

You can call another constructor only in the first statement. But in the above
example, a declaration statement is the first statement. This results in a
compile-time error.

#### RULE 2 - A constructor can call only one other constructor.

For example, this will not compile.

```
class Movie {

    var title
    var ratings
    var runtime

    function new()
        this('Unknown', 0.0, 0.0)

    function new(title)
        this()
        this(title, 0.0, 0.0)

    function new(title, ratings)
        this(title, ratings, 0.0)

    function new(title, ratings, runtime)
        this.title = title
        this.ratings = ratings
        this.runtime = runtime
```

You can call only one constructor. But in this example, the second constructor
invokes two constructors. This results in a compile-time error.

#### RULE 3 - You can chain constructors.

For example, the first constructor can call the second constructor. The
second constructor can call the third constructor.

```
class Person

    var name
    var age
    var number

    function new()
        this('Unknown')

    function new(name)
        this(name, -1, 'Unknown')

    function new(name, age, number)
        this.name = name
        this.age = age
        this.number = number
```

#### RULE 4 - You cannot call constructors in a cycle.

For example, the first constructor calls the second constructor. The
second constructor calls back the first constructor. Such cases will
generate errors.

```
class Pet

    var name
    var species
    var owner
    var age

    function new()
        this('Unknown', 'Unknown', 'Unknown', -1)

    function new(name, species, owner, age)
        this()
        this.name = name
        this.species = species
        this.owner = owner
        this.age = age
```

+++
title = "Working with the Static Initializer"
weight = 4
+++

Sometimes you may want to initialize your static fields after computing a value.
A static initializer is a special block of code which initializes a class.
It is written inside a class and outside function and constructors. You cannot
assign a name or invoke a static initializer, at least directly.

It is executed whenever the class is loaded. The Zen Virtual Machine may
unload a class when the class is unused to save memory. Since you cannot control
when a class is loaded in all cases, we recommend you to design your static
initializers to be unaware of the context in which it is executed.

The general form of a static initializer is shown here.
```
function static()
    statement1
    statement2
    ...
    statementN
```

As you can see, a static initializer is similar to a constructor, except it
is identified by the `static` keyword. You cannot have more than one static
initializer in your class.