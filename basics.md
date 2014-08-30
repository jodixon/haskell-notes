## Overview

Haskell is a **lazy**, **pure**, **functional** programming language. It is called *lazy* because expressions which are not needed to determine the answer to a problem are not evaluated. The opposite of lazy is *strict*, which is the evaluation strategy of most common programming languages (C, C++, Java, even ML). A strict language is one in which every expression is evaluated, regardless of whether the result of the computation is important or not.

It is called *pure* because it does not allow side effects. (A side effect is something that affects the “state” of the program. For instance, a function that prints something to the screen is said to be side-effecting, as is a function which affects the
value of a global variable). Calling the same function with the same arguments always produces the same output. Haskell uses a system of *monads* to isolate all impure computations and perform them in a safe way.

Haskell is called a *functional* language because the evaluation of a program is equivalent to evaluating a function in the pure mathematical sense. This also differs from standard languages (like C and Java) which evaluate a sequence of statements,
one after the other (this is termed an imperative langauge). The difference boils down to: *evaluating expressions* versus *executing instructions*.


