+++
title = "Understanding Identifiers"
+++

Identifiers are the names you give to variables, methods, classes, annotations
and enumerations. Unlike literals, identifiers only help you reference to something.

The program shown in the hello world example shown in the previous section
uses three identifiers.
    * `main`
    * `arguments`
    * `print`

* Identifiers are case sensitive. For example, `ArrayList` with uppercase `A`
and `arrayList` with lowercase `a` are two different identifiers.
* Identifiers may contain uppercase or lowercase letters, numerals,
  underscore characters `_`, and dollar symbols `$`.
* Identifiers must begin with a letter or an underscore. For example, `f07` is a valid
  identifier, but `7feb` is not because it begins with a numeral.
* You cannot use a *keyword* as an identifier. For example, `function` is not a
  valid identifier.
* You have to avoid using dollar symbols in identifiers. It is reserved for tools
  that generate code.

Here are a few examples of valid identifiers.
```
helloWorld
__student
Object
STRING
invoke123
$person
i
x1010
```

Here are a few examples of invalid identifiers.
```
function /* function is a keyword. You cannot use a keyword as an identifier. */
hello world /* An identifier cannot have spaces. */
3dCube /* An identifier cannot begin with a numeral. */
a*a /* An identifier cannot have symbols. */
```
