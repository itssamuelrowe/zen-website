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