## Algebraic Data Types

An **algebraic data type** is a type where we specify the shape of each of the elements. In general, an algebraic data type has one or more *data constructors*, and each data constructor can have zero or more arguments.

```
data AlgDataType = Constr1 Type11 Type12
                 | Constr2 Type21
                 | Constr3 Type31 Type32 Type33
                 | Constr4
```

This specifies that a value of type AlgDataType can be constructed in one of four ways: using ```Constr1```, ```Constr2```, ```Constr3```, or ```Constr4```. Depending on the constructor used, an ```AlgDataType``` value may contain some other values. For example, if it was constructed using ```Constr1```, then it comes along with two values, one of type ```Type11``` and one of type ```Type12```.

## Pattern Matching

Fundamentally, pattern-matching is about taking apart a value by *finding out which constructor* it was built with. This information can be used as the basis for deciding what to do—indeed, in Haskell, this is the *only* way to make a decision.

For example, to decide what to do with a value of type ```AlgDataType``` we would write something like

```
foo (Constr1 a b)   = ...
foo (Constr2 a)     = ...
foo (Constr3 a b c) = ...
foo Constr4         = ...
```

Note how we also get to give names to the values that come along with each constructor. Note also that parentheses are required around patterns consisting of more than just a single constructor.

This is the main idea behind patterns, but there are a few more things to note:
  1. An underscore ```_``` can be used as a “wildcard pattern” which matches anything.
  
  2. A pattern of the form ```x@pat``` can be used to match a value against the pattern ```pat```, but also give the name          ```x``` to the       entire value being matched.
  3. Patterns can be *nested*.
  
