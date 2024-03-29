Jetpack Compose internals Jorge Castillo
6/10 - interesting, but compose is hard to comprehend in a text form (still waiting for 2nd half of
book)
Memoization is remember(input){ res }

@Composable should be idempodent

@Composable and suspend are COLORED functions

Metaprogramming is a programming technique in which computer programs have the ability to treat
other programs as their data.

Arity - num of argument is function

Comparison propagation - the same as passing the composer to every child, but it regards state
changes

Use key() inside Column, Row

Currently, a @Composable function that returns a value will never be skipped, even if it has
immutable inputs and returns an immutable value. Thus use remember for any @Composable with return
value
