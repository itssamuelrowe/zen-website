+++
title = "Using If-Else-If Ladders"
+++

A common programming construct based on a sequence if statements is the if-else-if
ladder.

Here is the general form of an if-else-if ladder.
```
if condition1
    statement1
else if condition2
    statement2
else if condition3
    statement3
else
    statement4
```

These ladders are basically a group of nested *if statements*.
The *if statements* are executed from the top to down. As soon
as one of the conditions associated with an if clause is `true`,
then the statement associated with that if clause is executed,
and the rest of the ladder is skipped. If none of the conditions are
`true`, then the final else clause will be executed. In other words,
the final else clause acts as a default condition.

Here is an example program that demonstrates the if-else-if ladder.
```
// SeasonExample.zen
function main(...arguments)
    var month = 2
    var season
    
    if month == 1 
        season = 'Winter'
    else if month == 2 or month == 3 
        season = 'Spring'
    else if month == 4 or month == 5 
        season = 'Summer'
    else if month == 6 or month == 7 or month == 8 or month == 9 
        season = 'Rainy'
    else if month == 10 or month == 11 or month == 12 
        season = 'Winter'
    else 
        season = 'Invalid'
    print('The season experienced in February is ' + season)
```

We suggest you to play around with this program before moving on. As you will find,
no matter what value you assign the `month` variable, only one assignment statement
within the ladder will be executed.