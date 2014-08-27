## Overview

Haskell is a **lazy**, **pure**, **functional** programming language. It is called *lazy* because expressions which are not needed to determine the answer to a problem are not evaluated. The opposite of lazy is *strict*, which is the evaluation strategy of most common programming languages (C, C++, Java, even ML). A strict language is one in which every expression is evaluated, regardless of whether the result of the computation is important or not.

It is called *pure* because it does not allow side effects. (A side effect is something that affects the “state” of the program. For instance, a function that prints something to the screen is said to be side-effecting, as is a function which affects the
value of a global variable.) Instead, Haskell uses a system of *monads* to isolate all impure computations and perform them in a safe way.

Haskell is called a *functional* language because the evaluation of a program is equivalent to evaluating a function in the pure mathematical sense. This also differs from standard languages (like C and Java) which evaluate a sequence of statements,
one after the other (this is termed an imperative langauge).

## Expressions and Tuples

An **expression** is something that has a value. For instance, the number ```5``` is an expression (its value is 5). Expressions can in turn be built up from other expressions; for instance, ```5 + 6``` is an expression (its value is 11).

In addition to single values, we also want a way to represent multiple values. For instance, we might want to refer to a position by its *x/y* coordinate, which is a pair of integers. To make a pair of integers, you enclose the pair in parenthesis and separate them with a comma:

```
Prelude> (5, 3)
(5, 3)
```
The first element of a pair need not be of the same type as the second element: that is, pairs are allowed to be heterogeneous. We can also have triples, quadruples, etc. In general, pairs, triples, and so on are called **tuples** and can store fixed amounts of heterogeneous data.

## Lists

A data structure that can hold an arbitrary number of homogeneous elements is a **list**. Lists are assembled in a very similar fashion to tuples, except that they use square brackets instead of parentheses.

```
Prelude> [1, 2, 3]
[1, 2, 3]
```
Lists don't need to have any elements. The empty list is simply ```[]```.

Unlike tuples, we can very easily add an element on to the beginning of the list using the colon operator. The colon is called the ```cons``` operator; the process of adding an element is called *consing*. The etymology of this is that we are *constructing* a new list from an element and an old list.

```
Prelude> 0: [1, 2]
[0, 1, 2]
```

There are two basic list functions: ```head``` and ```tail```. The ```head``` function returns the first element of a (non-empty) list, and the ```tail``` function returns all but the first element of a (non-empty) list:

```
Prelude> head [1, 2, 3]
1

Prelude> tail [1, 2, 3]
[2, 3]
```

## Simple List Functions

Much of the computation in Haskell programs is done by processing lists. There are three primary list-processing functions: ```map```, ```filter``` and ```foldr``` (also ```foldl```).

The ```map``` function takes as arguments a list of values and a function that should be applied to each of the values. For instance, there is a built-in function ```Char.toUpper``` that takes as input a ```Char``` and produces a ```Char``` that is the upper-case version of the original argument. So, to covert an entire string (which is simply a list of characters) to upper case, we can map the ```toUpper``` function across the entire list:

```
Prelude> map Char.toUpper "Hello World"
"HELLO WORLD"
```

To remove elements from the list, you can use the ```filter``` function. This function allows you to remove certain elements from a list depending on their value, but not on their context. For instance, the function ```Char.isLower``` tells you whether a given character is lower case. We can filter out all non-lowercase characters using this:

```
Prelude> filter Char.isLower "Hello World"
"elloorld"
```
The function ```foldr``` takes a little more getting used to. foldr takes three arguments: a function, an initial value and a list. The best way to think about foldr is that it replaces occurences of the list cons operator (:) with the function parameter and replaces the empty list constructor (```[]```) with the initial value. Thus, if we have a list ```3 : 8 : 12 : 5 : []``` and we apply ```foldr (+) 0``` to it, we get ```3 + 8 + 12 + 5 + 0```:

```
Prelude> foldr (+) 0 [3, 8, 12, 5]
28
```

We can perform the same sort of operation to calculate the product of all the elements of the list:

```
Prelude> foldr (*) 1 [4, 8, 5]
160
```

## Functions

Functions are central to Haskell, as it is a *functional* programming language. This means that the evaluation of a program is simply the evaluation of a function.

We can write a simple function to square a number, which we define as follows:

```
square x = x * x
```
Here we are defining a function ```square``` that takes one argument which we call x. We say that the *value* of ```square x``` is equal to ```x * x```.
