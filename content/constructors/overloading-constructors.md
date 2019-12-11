+++
title = "Overloading Constructors"
+++

A class can have multiple constructors, this is known as constructor overloading.
It is a feature of polymorphism. Constructor overloading is a very useful feature.
It fact, it is similar to method overloading.

Java differentiates constructors using constructor signatures. A constructor
signature is a part of constructor declaration. It is the combination of the
constructor name, which is the class name it lives in, and the parameter list.
The names of the parameters are not included in the signature.

In order to overload a constructor, the constructor signatures should be different.
Which means your constructors need to have different parameter lists. When the

When you invoke an overloaded constructor, Java uses the following conditions to
determine which version of the overloaded constructor you are calling.
    * The type of each argument you are passing.
    * The number of arguments you are passing.

This is the reason why overloaded constructors must have different parameter lists.
Otherwise, Java won't be able to determine which version of the overloaded
constructor you are calling. It goes without saying, no two constructors in a
class can have the same number and type of arguments, because this is the only
way constructors can be differentiated.

Consider the following class.
```
public class Movie {

    private String title;
    private float ratings;
    private float runtime;

    public Movie(String title) {
        this.title = title;
    }

    public Movie(String title, float ratings) {
        this.title = title;
        this.ratings = ratings;
    }

    public Movie(String title, float ratings, float runtime) {
        this.title = title;
        this.ratings = ratings;
        this.runtime = runtime;
    }

    @Override
    public String toString() {
        return "title: " + title + ", ratings = " + ratings + ", runtime = " + runtime;
    }
}
```

In this example, we defined three constructors.

The first constructor accepts a `String` parameter named `title`. It initializes
corresponding `title` field.

The second constructor accepts two paramters named `title` and `ratings` of
the type `String` and `float`, respectively. It initializes the fields with
the corresponding values.

The third constructor accepts three paramters named `title`, `ratings`, and
`runtime` of the type `String`, `float`, and `float`, respectively. It initializes
the fields with the corresponding values.

You can create an instance of `Movie` like this.
```
Movie movie = new Movie("Forrest Gump", 8.8f, 2.22f);
```

## Calling Other Constructors

A constructor can call another constructor in the same class. Java provides
special syntax for this purpose. You must use `this` the keyword with parenthesis.
This is useful when your overloaded constructors have some common behavior of an
existing constructor. You can call the general purpose constructor from your
other constructors.

Here is an example of `Movie` class where the constructors invoke another
general purpose constructor.

```
public class Movie {

    private String title;
    private float ratings;
    private float runtime;

    public Movie() {
        this("Unknown", 0.0f, 0.0f);
    }

    public Movie(String title) {
        this(title, 0.0f, 0.0f);
    }

    public Movie(String title, float ratings) {
        this(title, ratings, 0.0f);
    }

    public Movie(String title, float ratings, float runtime) {
        this.title = title;
        this.ratings = ratings;
        this.runtime = runtime;
    }
}
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
public Movie(String title) {
    int i = 0;
    this(title, 0.0f, 0.0f);
}
```

You can call another constructor only in the first statement. But in the above
example, a declaration statement is the first statement. This results in a
compile-time error.

#### RULE 2 - A constructor can call only one other constructor.

For example, this will not compile.

```
public class Movie {

    private String title;
    private float ratings;
    private float runtime;

    public Movie() {
        this("Unknown", 0.0f, 0.0f);
    }

    public Movie(String title) {
        this();
        this(title, 0.0f, 0.0f);
    }

    public Movie(String title, float ratings) {
        this(title, ratings, 0.0f);
    }

    public Movie(String title, float ratings, float runtime) {
        this.title = title;
        this.ratings = ratings;
        this.runtime = runtime;
    }
}
```

You can call only one constructor. But in this example, the second constructor
invokes two constructors. This results in a compile-time error.

#### RULE 3 - You can chain constructors.

For example, the first constructor can call the second constructor. The
second constructor can call the third constructor.

```
public class Person {

    private String name;
    private int age;
    private String number;

    public Person() {
        this("Unknown");
    }

    public Person(String name) {
        this(name, -1, "Unknown");
    }

    public Person(String name, int age, String number) {
        this.name = name;
        this.age = age;
        this.number = number;
    }
}
```

#### RULE 4 - You cannot call constructors in a cycle.

For example, the first constructor calls the second constructor. The
second constructor calls back the first constructor. Such cases will
generate errors.

```
public class Pet {

    private String name;
    private String species;
    private String owner;
    private int age;

    public Pet() {
        this("Unknown", "Unknown", "Unknown", -1);
    }

    public Pet(String name, String species, String owner, int age) {
        this();
        this.name = name;
        this.species = species;
        this.owner = owner;
        this.age = age;
    }
}
```