# What We Will Do

In this tutorial we are looking at how to build and email using regex expressions. Looking at the expression step by step will help the developed understand how to properly build and what it is telling you to do. 

The expression that we will be looking at is `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` and together we will disect each component of the expression to fully understand how it will build out a proper email. 


## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)


## Regex Components
Provided below is the breakdown of the expression for an email.

Matching an Email – `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

First Part: `([a-z0-9_\.-]+)@`

a-z or 0-9 or _
and it must be followed by a  "@"

qualified emailmatch: test@

Second Part:`([\da-z\.-]+)\.` qualified emailmatch: gmail.com

`\d` says it needs to have digit spacing from 0-9
the characters allowed need to be from a-z
`\.` it must be followed by a `.`
valid example: test@gmail.

Third Part: `([a-z\.]{2,6})$/`

a-z{2,6}  matches a string that has user's letters followed by 2 up to 6 of the letters

qualified emailmatch: test@gmail.com


### Anchors
Anchors are the first part of writing an expression. They will start with `^` and end with `$`. 

The `^` expression shows where you will be starting with a string. For example if I write `^Hello` and I am trying to pull it from "Hello there how is your day?" it will only highlight Hello. 

The `$` is the oppositie, it is where the expression will be ending. If I continue with that example and not search for `^Hello there$` it will only pull hello there from my example. 

### Quantifiers
Quantifiers consist of four different symbols, they are, `*`, `+`, `?`, and `{}`. 

The first expression, `*`, can be referred to as a wild card. I'll keep withmy first example and write `hello*`. The reason this is a wild card is becuase this string could pick up just hello or it could pick up helooooo. As along as there is an "o" that is touching the origiional string then the expression will be picked up.

The symbol `+` will pick up the string that you put and it will look at the last character and pick that one or more up. 

//The symbol `?` will match the string and then pick up only one more that matches the last character. 

The last symbol is `{}` and this will work by the string picking up a certain abount that is determined by the number that you put within the bracket. For example if you write hello{3} then the this expression will match hello followed by three "o" if they are there. You are abel to set a specific number that it will start picking up and a number that it should stop picking up. An example of this would be `hello {4, }` if you write the expression like this then it will pick up the string and at least 4 "o" followed up to an undefinable number. 

### OR Operator
a(side1|side2) 
you will need a and side1 OR a and side2 to be true
side1 OR side2 can be true and will also need to have a

it can be notated with "()" and followed by a "|" or "[]"

### Character Classes
There are four different types of character classes. They are `\d`, `\w`, `\s`, and `.`. Let's break these four down;

To start, `\d` is telling the expression to pick up a single digit. However, if you see `\D` then it will do the opposite. This si for all the expressions that are under the character classes. 
\d = 0-9 spacing
\D = cannot be 0-9 digit spacing (-value which is not possible or greater than 9)

!(0-9)
!0-9

The next class is `\w` and this will pick a single word character. Like the one above it has the inverse option of `\W` and it will do the opposite. 
!a-z &&!A-Z&&!0-9

The phrase `\s` will pick up any whitespace that is in the text. Note that this also has an inverse option and would be written as `\S`. 
/s = includes  return linefeed tab(vertical and hor) formfeed
/S cannot be any of the above

The final character class is `.` and this is any character that you would like to pick up. 

### Flags
When starting an expression you will use `\` at the beginning and the end. This is done so that we can see the value that we are trying to find. 

There are three types of values that we can put within the flags, they are `g`, `m`, and  `i`. 

`g` stands for global which restarts the string that you are looking for. `m` stands for multi-line which will make our anchors `^` and `$` work. The last one, `i` makes our string pay attention to the case size, meaning if a letter is upper case and lower case. 

### Grouping and Capturing

This part of the expression is used with `()` and when they are used it is pulling specific informaiton within them. For example if I have an expression `1(23)` then it will capture the `23`

We can write this is different ways so that we are grabbing specific expressions within it. For example we can have the same example as before but write it as `1(?:23)` then the expression will pull just the `1` and not the `23`. 

The last add on that we can have is adding `?<foo>`. To keep going with our example `1(?<foo>23)`, then it will pull the `23`. All this is doing is putting a name to the expression. 

### Bracket Expressions
The bracket expressions will be using `[]` and just like the grouping and capturing section we are able to have different forms of this. 

## Author

If you have any questions or comments please contact me at smazurek44@gmail.com or check out my github at https://github.com/sophiamazurek 
