## Overview

Haskell is a **lazy**, **pure**, **functional** programming language. It is called *lazy* because expressions which are not needed to determine the answer to a problem are not evaluated. The opposite of lazy is *strict*, which is the evaluation strategy of most common programming languages (C, C++, Java, even ML). A strict language is one in which every expression is evaluated, regardless of whether the result of the computation is important or not.

It is called *pure* because it does not allow side effects. (A side effect is something that affects the “state” of the program. For instance, a function that prints something to the screen is said to be side-effecting, as is a function which affects the
value of a global variable). Calling the same function with the same arguments always produces the same output. Haskell uses a system of *monads* to isolate all impure computations and perform them in a safe way.

Haskell is called a *functional* language because the evaluation of a program is equivalent to evaluating a function in the pure mathematical sense. This also differs from standard languages (like C and Java) which evaluate a sequence of statements,
one after the other (this is termed an imperative langauge). The difference boils down to: *evaluating expressions* versus *executing instructions*.

## Declarations and Variables

In Haskell, variables are *not mutable boxes*, they are simply names for values. Put another way, ```=``` does *not* denote 'assignment' like in many other languages. Instead, ```=``` denotes 'definiton' like it does in mathematics.

```
x :: Int
x = 3
```

The above code declares a variable ```x``` of type ```Int``` and declares the value of ```x``` to be ```3```. It is important to note that once the value of ```x```has been declared, it *cannot* be changed later.

## Tuples and Lists

A **tuple** is an ordered set of heterogeneous elements whose length is predefined. For instance, we can create a pair like so:

```
p :: (Int, Char)
p = (5, 'c')
```

A **list** is an ordered set of homogeneous elements whose length is allowed to vary.

```
nums :: [Int]
nums = [1, 2, 3, 4]
```
The simplest list is the *empty list* ```[]```. Other lists are built up from the empty list using the ```cons``` operator (```:```):

```
msg :: [Char]
msg = 'h' : 'e' : 'l' : 'l' : 'o' : []
```
It is important to note that in Haskell, lists are actually *singly linked lists* and *not* arrays.

## Basic Functions

We can write functions on integers by cases:

```
factorial :: Integer -> Integer
factorial 0 = 1
factorial n = n * factorial (n-1)
```
Each clause is checked in order from top to bottom, and the first matching clause is chosen. Choices can also be made based on arbitrary Boolean expressions using **guards**. For example:

```
hailstone :: Integer -> Integer
hailstone n
  | n `mod` 2 == 0 = n `div` 2
  | otherwise      = 3*n + 1
```
Any number of guards can be associated with each clause of a function definition, each of which is a Boolean expression. If the clause’s patterns match, the guards are evaluated in order from top to bottom, and the first one which evaluates to True is chosen. If none of the guards evaluate to True, matching continues with the next clause.



