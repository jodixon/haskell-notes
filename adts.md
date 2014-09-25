## Algebraic Data Types

An **algebraic data type** is a type where we specify the shape of each of the elements. In general, an algebraic data type has one or more *data constructors*, and each data constructor can have zero or more arguments.

```
data AlgDataType = Constr1 Type11 Type12
                 | Constr2 Type 21
                 | Constr3 Type31 Type32 Type33
                 | Constr4
```

This specifies that a value of type AlgDataType can be constructed in one of four ways: using ```Constr1```, ```Constr2```, ```Constr3```, or ```Constr4```. Depending on the constructor used, an ```AlgDataType``` value may contain some other values. For example, if it was constructed using ```Constr1```, then it comes along with two values, one of type ```Type11``` and one of type ```Type12```.


