+++
title = "Classes and Objects"
weight = 8
+++

In this chapter, you discover the basics of creating classes in Zen.

You have been using classes since the beginning of this manual. However, until
now, you have barely scratched the surface, because the classes in the previous
chapters simply wrapped the `main()` function implicitly. As you will see,
classes are very powerful and important in Zen.

## Working with Classes

In the real world, you wll find many objects of the same kind. There are
thousands of bikes with the same make and model. Each of these bikes was built
with the same blueprint.

A class is a blueprint from which you create objects. The most important thing
to understand about a class is that it defines a new data type. Once defined,
this new type can be used to create instances. In other words, a class is a
blueprint or a template for an object, and an object is an instance of a class,
Given an object is an instance of a class, you will often see the two words
object and instance used interchangeably.

You should declare a class with a name and a body. Here is the general form of
a class declaration.

```
class Name

    /* Fields */
    /* Constructors */
    /* Functions */
```

A class body can contain the following elements.

 * Constructors
   A constructor is a block of code that runs whenever you create an instance.
   It initializes new instances.

 * Fields
   A field is a variable declared inside a class body and outside a method body.
   A field provides the state of the class and its instances.
   There are two types of fields, instance variables and static variables.
   When you declare a field inside a class, outside a method, and without
   the `static` keyword it is an instance variable. Similarly, when you declare
   a field inside a class, outside a method, and
   with the `static` keyword it is a static variable. You will learn about static
   variables later in this chapter.

 * Functions
   A function is a block of code. It defines a behavior of the class and its
   instances.

The order in which you write your class members does not matter. We recommend
you to follow a uniform order. So you will know where to find your members.
Further, the fields and functions, that is, the entities that you declare
inside your class are known as its members.

### Working with Fields

The general form of a field is shown here.

```
modifiers var identifier
```

You can declare fields like any other variable. You can optionally specify
modifiers. The modifiers tell the compiler additional characteristics of the
field such as visibility, mutability, etc.

Basically, there are four modifiers you can use when you declare a field.

 * private
 * public
 * secret
 * static

Each modifier is a keyword. We will be learning about all the modifiers
in this chapter.

Here is an example of a class called `Superhero`.

```
// Superhero.zen

class Superhero

    var name

    var gender

    var strength

    var speed

    var intelligence
```

This class definition contains five variables. Given these variables are not
defined inside a method without the `static` keyword, they are instance variables.

In this example, the `name` field holds the name of the superhero.
For example, `Batman`. The `gender` field holds the gender of the superhero.
For example, it could be `'female'` for Wonder Woman. The `strength` field represents
the muscular strength of the superhero, ranging from 1 to 10. For example, The
Presence would have a perfect 10. The `speed` field represents the speed of the
superhero, ranging from 1 to 10. For example, you guessed it, The Flash would
have a perfect 10. The `intelligence` fields represents the intellect of the
superhero. For example, Batman would be considered `very intelligent`, just
behind Lex Luthor, a supervillan.

It is important to remember that a class declaration only creates a blueprint.
It does not create an actual object. Thus, the previous example does not create
any object. To actually create a `Superhero` object, you should use the `new`
keyword, which is an operator.

## Working with the New Operator

The general form of the `new` operator to create an instance of a class is
shown here.

```
new Class()
```

Here the `Class` represents the name of the class whose instance you want to
create. You will learn the significance of the parenthesis when you learn
about constructors.

To create an instance of the `Superhero` class, you would write something like this.
```
var superman = new Superhero()
```

In this example, we created a variable called `superman`. Then we created an
instance of `Superhero` and assigned its reference to the variable `superman`.
A reference is important to write and read the values stored in an object.

You should always remember that each instance contains its own copy of
instance variables. Thus, every Superhero object will contain its own copies of
name, gender, strength, speed and intelligence. This is a very important concept
you need to remember.

Here is an example where two Superhero objects are created.

```
var superman = new Superhero()
var batman = new Superhero()
```

In this example, `superman` object has its own copies of name, gender, strength,
speed, and intelligence. If you modified any of these fields it would not affect
the values stored in the `batman` object, because each `Superhero` object contains
its own copies of the `Superhero` fields.

To access an instance variable, you can use the member access operator (`.`).
The dot operator (synonym for the member access operator) links the reference
of the object with the instance variable. For example, to assign `'Batman'` to
the `name` instance variable contained in the `batman` object, you can write the
following statement.

```
batman.name = 'Batman'
```

Here, the `batman` variable contains the reference to a `Superhero` object.
`name` indicates the instance variable to modify.

The member access operator is a binary operator. Obviously, the member access operator
always returns a value. Accessing instance variables with it is an expression.
In fact, both the operands of the member access operator are expressions.
This means that you can chain instance variable access. You will see chaining
instance variable access later in the course.

Here is the complete Superhero program.

```
// Superhero.zen

class Superhero

    var name

    var gender

    var strength

    var speed

    var intelligence

    static function main(...arguments)
        // Create the Superhero objects.

        var superman = new Superhero()
        superman.name = 'Superman'
        superman.gender = 'Male'
        superman.strength = 9
        superman.speed = 9
        superman.intelligence = 'Very Intelligent'

        var batman = new Superhero()
        batman.name = 'Batman'
        batman.gender = 'Male'
        batman.strength = 6
        batman.speed = 6
        batman.intelligence = 'Very Intelligent'

        // Print the values contained in the instance variables.
        print(serialize(batman, 'json'))
        print(serialize(superman, 'json'))
}
```

The output produced by the Superhero program is shown here.

```
{
    "name" : "Superman",
    "gender" :  "Male",
    "strength" : 9,
    "speed" : 9,
    "intelligence" : "Very Intelligent"
}
{
    "name" : "Batman",
    "gender" :  "Male",
    "strength" : 6,
    "speed" : 6,
    "intelligence" : "Very Intelligent"
}
```

### Understanding Object References

When you declare a variable, you are basically creating a reference variable.

For example, what do you think the following code segment performs?
```
var shazamKid = new Superhero()
var darlaDudley = shazamKid
```

If you are new to programming, you might think that `darlaDudley` is being
assigned a copy of new Superhero object. In other words, you might think that
`shazamKid` and `darlaDudley` refer to two separate and distinct objects.
However, this is not true.

If you ran this code, `shazamKid` and `darlaDudley` will both refer to the same
object. The assignment of `shazamKid` to `darlaDudley` did not create any new
copy of the original object. It simply makes `darlaDudley` refer to the same
object that `shazamKid` references. Thus, any changes made to the object through
`darlaDudley` will affect the original object and the changes will reflect through
`shazamKid`.

### Conventions for Class Names

Your class name is an identifier. You can use any identifier you want. But we
suggest you to follow these guidelines.

 * Begin the class name with a capital letter. For example, `Bike`, `Car`,
  `Planet` and `Person`.
 * If the class name consists of more than one word, capitalize each word.
  For example, `BikeRace`, `CarGame`, `CollegeLibrary` and `StringBuilder`.
 * Try to use nouns for your class names. We know that classes represent real
  life objects. In the real word, you identify objects with nouns. Hence,
  we recommend you to use nouns for naming your classes.

### Understanding Visibility

You can control whether the world outside your class can access its members.
This is known as visibility of the member. In other words, you can expose only
certain members to public, that is the world outside your class, while keep other
members private or secret. Thus, you can control the access of your members.
The visibility modifiers are a form of encapsulation in Zen.

You will use visibility modifiers very often. There are three visibility levels
in Zen.

 * Public
 * Private
 * Secret

The visibility modifiers determine which members of your class are visible
to other classes. With access control, you can tell the compiler how your class
can be used by other classes. You can use only one visibility modifier at a time.

#### Private Access

You can use the private modifier to hide a class member from all the other classes.
In other words, a private member is accessible only within its class.

Some members of a class are useful only within the class. There is no point in
such members being accessed from other classes. In such cases, you should always
use the private modifier.

In fact, fields are marked as private by default. You will learn more about this
later in this chapter.

#### Secret Access

A secret member is accessible to the following two groups.
    * Subclasses of a class
    * Other classes in the same package

You will learn more about subclasses and packages later in this manual.

#### Public Access

In some cases, you want your class members to be completely visible to the
outside world. In other words, any class can access the member.

You can use the public modifier to make a member completely visible to all
the classes. Unlike fields, functions are `public` by default.

In fact, you have already used the public modifier from the beginning of this
course implicitly.

The `main()` function of an application has to be public. Otherwise, it cannot
not be invoked by the Zen Virtual Machine (ZVM).

## Understanding Instance and Static Members

#### Instance Members

Instance variables are variables that you declare inside a class body and
without the `static` keyword. They are declared outside functions, constructors,
and initializers. These variables are initialized when you create an instance
of the class. Further, each instance of the class gets a copy of these variables.
In fact, when any member of a class, except constructors, is declared
without the `static` keyword you are essentially declaring an instance member.
An instance member can be accessed only with a reference to an instance.

When you create an instance of a class, the instance gets its own copy of the
instance variables in memory. Zen treats other instance members specially.
In fact, each instance of class does not contain its own copy of instance members
such as functions, constructors, and initializers. Because multiple copies of
such members will exhaust the memory. Instead Zen keeps only one copy of
such instance members and simulates as if each instance gets its own copy.
Actually, if memory were not a concern, each instance would get its own copy
of such members to improve performance.

#### Static Members

Class variables are variables that you declare within a class with the `static`
keyword. They are outside functions, constructors, and initializers. Remember,
you declare class variables with the `static` keyword. Unlike instance variables,
each instance of a class does not get a copy of class variables. A class member
can be accessed without a reference to an instance.

Static members belong to the class instead of a specific instance. Which means
if you make a member static, you can access it without an instance.
You should always remember that whenever you create an instance of a class,
the instance does not get its own copy of the static members.

You have already used the `static` modifier from the beginning of this manual.
The `main()` function is declared outside a class, an implicit static modifier
is added by the compiler. However, you must explicitly add the static modifier
when you declare the `main()` function inside a class. The Zen Virtual Machine
(ZVM) does not create an instance of your main class before invoking the main
function. This is why you should always declare the main function as static.

Here is an example of a class variable.

```
// Circle.zen

class Circle
    static final PI = 3.14159265
```

You can access a class member without a reference to an instance. You
can access a class member using the class name followed by the member access
operator (`.`) and the name of the member.

Here is an example that calculates the area of a cirlce. It demonstrates
accessing the class variable from the previous example.
```
// CircleArea.zen
function main(...arguments)
    var radius = promptFloat('Enter the radius: ')
    var area = Circle.PI * radius * radius
    printf('The area of the circle with radius %f is %f.\n', radius, area)
```

You cannot use an instance of a class to access its class members. This design
choice was made to improve code clarity.