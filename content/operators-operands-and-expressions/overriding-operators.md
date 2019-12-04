+++
title = "Overriding Operators"
+++

Zen allows operator overriding through a combination of functions and
annotations.

All the operators in Zen are dispatched to a function call.
The `ZenKernel.evaluate(...)` function finds a suitable handler for the
operator defined within the operand object and dispatches it. In other words,
the compiler translates expressions with operators to equivalent
`ZenKernel.evaluate(...)` calls.

For example, in the `HashMap` class the following annotation
overrides the subscript operator.

```
@Operator symbol='[]'
function getValue(key)
    ...
```

With that information, consider the following snippet of code.

```
var emailAddresses = {
    'Samuel Rowe' : 'samuelrowe1999@gmail.com',
    'Joel E. Rego' : 'joelerego@gmail.com'
}
var myEmailAddress = emailAddresses['Samuel Rowe']
```

The above code snippet is equivalent to the following expression statement.

```
var emailAddresses = {
    'Samuel Rowe' : 'samuelrowe1999@gmail.com',
    'Joel E. Rego' : 'joelerego@gmail.com'
}
var myEmailAddress = ZenKernel.evaluate(emailAddresses, 'Samuel Rowe', '[]')
```

In fact, when you compile the former code snippet the compiler generates
instructions as if the code was written in the latter form.